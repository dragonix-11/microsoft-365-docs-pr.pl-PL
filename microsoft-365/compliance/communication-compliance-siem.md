---
title: Zgodność komunikacji z rozwiązaniami SIEM
description: Dowiedz się więcej o integracji zgodności komunikacji z rozwiązaniami SIEM.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: d957b5fec4341cd7335f5c5a49b6654ffaf51f68
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006535"
---
# <a name="communication-compliance-with-siem-solutions"></a>Zgodność komunikacji z rozwiązaniami SIEM

[Zgodność komunikacji to](communication-compliance.md) rozwiązanie ryzyka niejawnego programu testów w programie Microsoft 365 które pomaga zminimalizować ryzyko związane z komunikacją, pomagając wykrywać i przechwytywać nieodpowiednie wiadomości w organizacji oraz działać na nie. Rozwiązania do zarządzania informacjami o zabezpieczeniach i zdarzeniami, takie jak [Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel) czy [Splunk](https://www.splunk.com/) , są często używane do agregowania i śledzenia zagrożeń w organizacji.

Często spotykaną potrzebą organizacji jest integracja alertów zgodności komunikacji i tych rozwiązań SIEM. Dzięki tej integracji organizacje mogą wyświetlać alerty zgodności komunikacji w swoich rozwiązaniach SIEM, a następnie rekultywować alerty w ramach przepływu pracy zgodności komunikacji i środowiska użytkownika. Na przykład pracownik wysyła obraźliwą wiadomość do innego pracownika i jest wykrywana przez monitorowanie zasad zgodności komunikacji dla nieodpowiedniej zawartości. Te zdarzenia są śledzone w ramach Microsoft 365 inspekcji (nazywanej także "ujednoliconym dziennikem inspekcji") przez rozwiązanie do zapewnienia zgodności komunikacji i importowane do rozwiązania SIEM. W rozwiązaniu SIEM organizacji jest następnie wyzwolony alert z wynikami zdarzeń monitorowanych Microsoft 365 inspekcji skojarzonej z alertami zgodności komunikacji. Wschowy są powiadamiane o alertach w rozwiązaniach SIEM, a następnie badają i zaradają nad alertem w rozwiązaniu do zapewnienia zgodności komunikacji.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>Alerty zgodności komunikacji w Microsoft 365 inspekcji komunikacji

Wszystkie dopasowania zasad zgodności komunikacji są przechwytywane w Microsoft 365 inspekcji. W poniższych przykładach podano szczegóły dostępne dla wybranych działań dopasowania zasad zgodności komunikacji:

**Przykład wpisu dziennika inspekcji dla szablonu zasad Nieodpowiednia zawartość jest zgodne:**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/7/2021 5:30:11 AM
UserIds: user1@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-07T05:30:11","Id":"44e98a7e-57fd-4f89-79b8-08d941084a35","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<HE1P190MB04600526C0524C75E5750C5AC61A9@HE1P190MB0460.EURP190.PROD.OUTLOOK.COM\>","UserId":"user1@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"53be0bf4-75ee-4315-b65d-17d63bdd53ae","SRPolicyName":"Adult images","SRRuleMatchDetails":\[\]}}
ResultIndex: 24
ResultCount: 48
Identity: 44e98a7e-57fd-4f89-79b8-08d941084a35
IsValid: True
ObjectState: Unchanged
```

**Przykład wpisu dziennika inspekcji Microsoft 365 dla zasad z niestandardowym dopasowaniem słów kluczowych (niestandardowy typ informacji poufnych):**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/6/2021 9:50:12 PM
UserIds: user2@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-06T21:50:12","Id":"5c61aae5-26fc-4c8e-0791-08d940c8086f","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"public\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<20210706174831.24375086.807067@sailthru.com\>","UserId":"user2@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"a97cf128-c0fc-42a1-88e3-fd3b88af9941","SRPolicyName":"Insiders","SRRuleMatchDetails":\[{"SRCategoryName":"New insiders lexicon"}\]}}
ResultIndex: 46
ResultCount: 48
Identity: 5c61aae5-26fc-4c8e-0791-08d940c8086f
IsValid: True
ObjectState: Unchanged
```

> [!NOTE]
> Obecnie między zarejestrowanym dopasowaniem zasad w inspekcji w programie Microsoft 365 a czasem, w którym można badać dopasowania zasad w ramach zgodności komunikacji, może upłynie do 24 godzin.

## <a name="configure-communication-compliance-and-microsoft-sentinel-integration"></a>Konfigurowanie zgodności komunikacji i integracji z usługą Microsoft Sentinel

Jeśli używasz programu Microsoft Sentinel do agregowania dopasowania zasad zgodności komunikacji, usługa Sentinel używa Microsoft 365 Inspekcji jako źródła danych. Aby zintegrować alerty zgodności komunikacji z kanałem Sentinel, wykonaj następujące czynności:

1. [Wnosz do programu Microsoft Sentinel](/azure/sentinel/quickstart-onboard). W ramach procesu dołączania skonfigurujesz źródła danych.
2. Skonfiguruj łącznik danych programu Microsoft Sentinel [Microsoft Office 365 w](/azure/sentinel/data-connectors-reference#microsoft-office-365) obszarze Konfiguracja łącznika *wybierz pozycję Exchange*.
3. Skonfiguruj zapytanie wyszukiwania, aby pobierało alerty zgodności komunikacji. Przykład:

    *| Pakiet OfficeActivity | where OfficeWorkload == "Exchange" and Operation == "SupervisionRuleMatch" | Sortuj według TimeGenerated*

    Aby przefiltrować dane określonego użytkownika, należy użyć następującego formatu zapytania:

    *| Pakiet OfficeActivity | where OfficeWorkload == "Exchange" and Operation == "SupervisionRuleMatch" and UserId == "User1@Contoso.com" | Sortuj według TimeGenerated*

Aby uzyskać więcej informacji o dziennikach Microsoft 365 inspekcji dla Office 365 zbieranych przez program Microsoft Sentinel, zobacz Informacje dotyczące dzienników programu [Azure Monitor](/azure/azure-monitor/reference/tables/OfficeActivity).

## <a name="configure-communication-compliance-and-splunk-integration"></a>Konfigurowanie zgodności komunikacji i integracji z usługą Splunk

Aby zintegrować alerty zgodności komunikacji z programem Splunk, wykonaj następujące czynności:

1. Instalowanie [dodatku Splunk dla Microsoft Office 365](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI)
2. Konfigurowanie aplikacji integracji w usłudze Azure AD dla dodatku Splunk dla programu Microsoft Office 365
3. Skonfiguruj zapytania wyszukiwania w swoim rozwiązaniu Splunk. Użyj następującego przykładu wyszukiwania, aby zidentyfikować wszystkie alerty zgodności komunikacji:

    *index=\* sourcetype="o365:management:activity" Workload=Exchange Operation=SupervisionRuleMatch*

W celu filtrowania wyników określonych zasad zgodności komunikacji możesz użyć *parametru SRPolicyMatchDetails.SRPolicyName* .

Na przykład w poniższym przykładzie wyszukiwania byłyby zwracane alerty dotyczące dopasowania do zasad zgodności komunikacji o nazwie *Nieodpowiednia zawartość*:

  *index=\* sourcetype='o365:management:activity' Workload=Exchange Operation=SupervisionRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Inappropriate content\>*

W poniższej tabeli przedstawiono przykładowe wyniki wyszukiwania dla różnych typów zasad:

| Typy zasad | Przykładowe wyniki wyszukiwania |
| :------------------ | :--------------------------------------- |
| Zasady wykrywania niestandardowej listy słów kluczowych o typie informacji poufnych | { <br> CreationTime: 2021-09-17T16:29:57 <br> Identyfikator: 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicy Należy: true <br> ObjectId: <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> Operacja: SupervisionRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM. Uwaga","CcsiResults":"leak"} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.OnMicrosoft.com <br> UserKey: SupervisionStoreDeliveryAgent <br> UserType: 0 <br> Wersja: 1 <br> Obciążenie pracą: Exchange <br> } |
| Zasady wykrywania nieodpowiedniego języka | { <br> CreationTime: 2021-09-17T23:44:35 <br> IDENTYFIKATOR: e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicy Należy: true <br> ObjectId: <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> Operacja: SupervisionRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM.Yammer. Wiadomość","CcsiResults":""} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.com <br> UserKey: SupervisionStoreDeliveryAgent <br> UserType: 0 <br> Wersja: 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>Konfigurowanie zgodności komunikacji z innymi rozwiązaniami SIEM

Aby pobierać dopasowania zasad zgodności komunikacji z Microsoft 365 inspekcji, możesz użyć programu PowerShell lub interfejsu [API Office 365 zarządzania](/office/office-365-management-api/office-365-management-activity-api-reference).

Podczas korzystania z programu PowerShell możesz użyć jednego z tych parametrów z poleceniem cmdlet **Search-UnifiedAuditLog** w celu filtrowania zdarzeń dziennika inspekcji pod celu zapewnienia zgodności komunikacji.

| Parametr dziennika inspekcji | Wartość parametru zgodności komunikacji |
| :------------------ | :--------------------------------------- |
| Operacje          | SupervisionRuleMatch                     |
| RecordType (Typ rekordu)          | ComplianceSupervisionExchange            |

Na przykład poniżej przedstawiono przykładowe wyszukiwanie z użyciem **parametru Operations** i wartości *SupervisionRuleMatch* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
Poniżej przedstawiono przykładowe wyszukiwanie przy użyciu **parametru RecordsType** i *wartości ComplianceSupervisionExchange* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>Zasoby

- [Inspekcja zgodności komunikacji](communication-compliance-reports-audits.md#audit)
- [Advanced Audit in Microsoft 365](advanced-audit.md)
- [Office 365 interfejsu API działań zarządzania](/office/office-365-management-api/office-365-management-activity-api-reference)
