---
title: Zgodność w komunikacji z rozwiązaniami SIEM
description: Dowiedz się więcej o integracji zgodności komunikacji z rozwiązaniami SIEM.
keywords: Microsoft 365, Microsoft Purview, zgodność, zgodność z komunikacją
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
ms.openlocfilehash: f111fbd831f36cd8f1647e4b99565a24372387b8
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953875"
---
# <a name="communication-compliance-with-siem-solutions"></a>Zgodność w komunikacji z rozwiązaniami SIEM

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[Zgodność z komunikacją](communication-compliance.md) to rozwiązanie ryzyka związanego z informacjami poufnymi w usłudze Microsoft Purview, które pomaga zminimalizować ryzyko komunikacji, pomagając wykrywać, przechwytywać i działać na nieodpowiednich komunikatach w organizacji. Rozwiązania do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM), takie jak [Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel) lub [Splunk](https://www.splunk.com/) , są często używane do agregowania i śledzenia zagrożeń w organizacji.

Typowym zapotrzebowaniem organizacji jest zintegrowanie alertów zgodności z komunikacją i tych rozwiązań SIEM. Dzięki tej integracji organizacje mogą wyświetlać alerty zgodności komunikacji w rozwiązaniu SIEM, a następnie korygować alerty w ramach przepływu pracy zgodności komunikacji i środowiska użytkownika. Na przykład pracownik wysyła obraźliwy komunikat do innego pracownika i ten komunikat jest wykrywany przez monitorowanie zasad zgodności komunikacji pod kątem nieodpowiedniej zawartości. Te zdarzenia są śledzone w usłudze Microsoft 365 Audit (znanej również jako "ujednolicony dziennik inspekcji") przez rozwiązanie zgodności z komunikacją i importowane do rozwiązania SIEM. Alert jest następnie wyzwalany w rozwiązaniu SIEM dla organizacji na podstawie zdarzeń monitorowanych w Microsoft 365 Inspekcja, które są skojarzone z alertami zgodności komunikacji. Śledczy są powiadamiani o alercie w rozwiązaniach SIEM, a następnie badają i korygują alert w rozwiązaniu zgodności z komunikacją.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>Alerty zgodności komunikacji w usłudze Microsoft 365 Audit

Wszystkie dopasowania zasad zgodności komunikacji są przechwytywane w Microsoft 365 Audit. W poniższych przykładach przedstawiono szczegóły dotyczące wybranych działań dopasowania zasad zgodności komunikacji:

**Przykład wpisu dziennika inspekcji dla dopasowania szablonu zasad nieodpowiedniej zawartości:**

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
> Obecnie może wystąpić do 24-godzinne opóźnienie między czasem rejestrowania dopasowania zasad w Microsoft 365 Audit a czasem, w którym można badać dopasowania zasad w zgodności z komunikacją.

## <a name="configure-communication-compliance-and-microsoft-sentinel-integration"></a>Konfigurowanie zgodności komunikacji i integracji z usługą Microsoft Sentinel

Jeśli używasz usługi Microsoft Sentinel do agregowania dopasowań zasad zgodności komunikacji, usługa Sentinel używa Microsoft 365 Audit jako źródła danych. Aby zintegrować alerty zgodności komunikacji z usługą Sentinel, wykonaj następujące kroki:

1. [Dołącz do usługi Microsoft Sentinel](/azure/sentinel/quickstart-onboard). W ramach procesu dołączania skonfigurujesz źródła danych.
2. Skonfiguruj [łącznik danych Microsoft Office 365](/azure/sentinel/data-connectors-reference#microsoft-office-365) usługi Microsoft Sentinel i w obszarze konfiguracji łącznika wybierz pozycję *Exchange*.
3. Skonfiguruj zapytanie wyszukiwania, aby pobierać alerty zgodności komunikacji. Przykład:

    *| OfficeActivity | where OfficeWorkload == "Exchange" and Operation == "SupervisionRuleMatch" | sortuj według timegenerated*

    Aby odfiltrować określonego użytkownika, należy użyć następującego formatu zapytania:

    *| OfficeActivity | where OfficeWorkload == "Exchange" and Operation == "SupervisionRuleMatch" and UserId == "User1@Contoso.com" | sortuj według timegenerated*

Aby uzyskać więcej informacji na temat dzienników inspekcji Microsoft 365 dla Office 365 zebranych przez usługę Microsoft Sentinel, zobacz [Dokumentacja dzienników usługi Azure Monitor](/azure/azure-monitor/reference/tables/OfficeActivity).

## <a name="configure-communication-compliance-and-splunk-integration"></a>Konfigurowanie zgodności komunikacji i integracji splunk

Aby zintegrować alerty zgodności komunikacji z rozwiązaniem Splunk, wykonaj następujące kroki:

1. Instalowanie [dodatku Splunk dla Microsoft Office 365](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI)
2. Konfigurowanie aplikacji integracji w usłudze Azure AD dla dodatku Splunk dla Microsoft Office 365
3. Skonfiguruj zapytania wyszukiwania w rozwiązaniu Splunk. Użyj następującego przykładu wyszukiwania, aby zidentyfikować wszystkie alerty zgodności komunikacji:

    *index=\* sourcetype="o365:management:activity" Workload=Exchange Operation=SupervisionRuleMatch*

Aby filtrować wyniki dla określonych zasad zgodności komunikacji, można użyć parametru *SRPolicyMatchDetails.SRPolicyName* .

Na przykład poniższy przykład wyszukiwania zwraca alerty dotyczące dopasowań do zasad zgodności komunikacji o nazwie *Nieodpowiednia zawartość*:

  *index=\* sourcetype='o365:management:activity' Workload=Exchange Operation=SupervisionRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Inappropriate content\>*

W poniższej tabeli przedstawiono przykładowe wyniki wyszukiwania dla różnych typów zasad:

| Typy zasad | Przykładowe wyniki wyszukiwania |
| :------------------ | :--------------------------------------- |
| Zasady wykrywające niestandardową listę słów kluczowych typu informacji poufnych | { <br> CreationTime: 2021-09-17T16:29:57 <br> Identyfikator: 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicyHit: prawda <br> Objectid: <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> Operacja: SupervisionRuleMatch <br> Identyfikator organizacji: d6a06676-95e8-4632-b949-44bc00f0793f <br> Typ rekordu: 68 <br> ResultStatus: {"ItemClass":"IPM. Uwaga","CcsiResults":"leak"} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.OnMicrosoft.com <br> UserKey: SupervisionStoreDeliveryAgent <br> Typ użytkownika: 0 <br> Wersja: 1 <br> Obciążenie: Exchange <br> } |
| Zasady wykrywające nieodpowiedni język | { <br> CreationTime: 2021-09-17T23:44:35 <br> Identyfikator: e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicyHit: prawda <br> Objectid: <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> Operacja: SupervisionRuleMatch <br> Identyfikator organizacji: d6a06676-95e8-4632-b949-44bc00f0793f <br> Typ rekordu: 68 <br> ResultStatus: {"ItemClass":"IPM.Yammer. Wiadomość","CcsiResults":""} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.com <br> UserKey: SupervisionStoreDeliveryAgent <br> Typ użytkownika: 0 <br> Wersja: 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>Konfigurowanie zgodności komunikacji z innymi rozwiązaniami SIEM

Aby pobrać dopasowania zasad zgodności komunikacji z Microsoft 365 Audit, możesz użyć programu PowerShell lub [interfejsu API zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

W przypadku korzystania z programu PowerShell można użyć jednego z tych parametrów z poleceniem cmdlet **Search-UnifiedAuditLog** do filtrowania zdarzeń dziennika inspekcji pod kątem działań związanych ze zgodnością komunikacji.

| Parametr dziennika inspekcji | Wartość parametru zgodności komunikacji |
| :------------------ | :--------------------------------------- |
| Operacje          | NadzórRuleMatch                     |
| Typ rekordu          | ComplianceSupervisionExchange            |

Na przykład poniżej przedstawiono przykładowe wyszukiwanie przy użyciu parametru **Operations** i wartości *SupervisionRuleMatch* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
Poniżej przedstawiono przykładowe wyszukiwanie przy użyciu parametru **RecordsType** i wartości *ComplianceSupervisionExchange* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>Zasoby

- [Inspekcja zgodności komunikacji](communication-compliance-reports-audits.md#audit)
- [Microsoft Purview Audit (Premium)](advanced-audit.md)
- [Dokumentacja dotycząca interfejsu API działań związanych z zarządzaniem w usłudze Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)
