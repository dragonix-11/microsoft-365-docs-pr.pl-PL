---
title: Używanie nazwanych obiektów w zasadach ochrony przed utratą danych (wersja zapoznawcza)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: Skorzystaj z tych procedur, aby korzystać z nazwanych obiektów w zasadach ochrony przed utratą danych.
ms.openlocfilehash: f3dac4efa1b0cf84971ac4d07f78144b438d1161
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009685"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>Używanie nazwanych obiektów w zasadach ochrony przed utratą danych (wersja zapoznawcza)

> [!IMPORTANT]
> Funkcja nazwanych jednostek jest obecnie wprowadzana i będzie wyświetlana w dzierżawie, gdy będzie dla Ciebie dostępna. Sprawdź je w Eksploratorze zawartości i w przepływie tworzenia zasad ochrony przed utratą danych (DLP). 

Przeczytaj Informacje [o nazwanych jednostkach (wersja zapoznawcza)](named-entities-learn.md) przed rozpoczęciem ich używania.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie subskrypcji/licencji na subskrypcje sKU

Musisz mieć jedną z tych subskrypcji

- Ochrona informacji i zarządzanie
- Zgodność platformy Microsoft 365 E5
- Office 365 E5
- Microsoft 365 E5

Aby uzyskać szczegółowe informacje o licencjonowaniu, [zobacz opis usługi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Uprawnienia

Konto, za pomocą których tworzysz i edytujesz zasady ochrony przed utratą danych (DLP), musi mieć uprawnienia roli zarządzanie zgodnością **DLP** . Aby uzyskać więcej informacji, zobacz [Zapewnianie użytkownikom dostępu do Centrum Office 365 zgodności](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).


## <a name="supported-locations"></a>Obsługiwane lokalizacje

Aby wykrywać i chronić poufne elementy w tych lokalizacjach, można używać nazwanych identyfikatorów SIT encji i rozszerzonych zasad:

- SharePoint witryn
- OneDrive konta
- Teams wiadomości czatu i kanałów
- Urządzenia (Windows 10 punktów końcowych)

Nazwane jednostki SIT i rozszerzone zasady nie są obsługiwane w przypadku:


- Repozytoria lokalne
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Tworzenie i edytowanie rozszerzonych zasad

Aby utworzyć lub edytować zasady DLP, skorzystaj z procedur zobacz Tworzenie [, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Obciążenia pracą i usługi, które obsługują nazwane jednostki


- **Usługa zbierania elektronicznych materiałów dowodowych platformy Microsoft 3655** obsługuje użycie nazwanych jednostek w usługach obsługi wiadomości e-mail.
- **Program Microsoft Defender for Cloud Apps** obsługuje korzystanie z nazwanych jednostek w zasadach usługi Defender for Cloud Apps.
- **Zarządzanie ryzykiem w niejawnym** programie testów obsługuje użycie nazwanych jednostek w usługach arytmie.
- **Zgodność komunikacji** nie obsługuje używania nazwanych jednostek w Exchange transportu i danych w miejscu.
- **Microsoft Information Governance** (MIG) nie obsługuje używania nazwanych jednostek w Exchange reguł transportu i danych w miejscu.
 
### <a name="unified-dlp"></a>Ujednolicony system DLP

|Obciążenie pracą/usługi  |Publiczna obsługa podglądu dla nazwanych obiektów  |
|---------|---------|
|porada Office klientów win32    |nie jest obsługiwane  |
|Office klientów usługi WAC    |obsługiwane         |
|Porada w zakresie zasad OWA     |nie jest obsługiwane         |
|Outlook zasad     |nie jest obsługiwane |
|Punkty końcowe (Windows 10 urządzenia)     |obsługiwane  |
|Exchange reguły transportu     |nie jest obsługiwane |
|OneDrive dla Firm danych w spoczynku     |obsługiwane         |
|SharePoint danych online w spoczynku     |obsługiwane         |
|Teams danych w spoczynku     |obsługiwane         |
|Dane w spoczynku wiadomości e-mail     |nie jest obsługiwane         |
|Usługa Microsoft Defender dla aplikacji w chmurze     |obsługiwane         |

### <a name="autolabeling"></a>Autolabelowanie

|Obciążenie pracą/usługi |Publiczna obsługa podglądu dla nazwanych obiektów  |
|---------|---------|
|Office klientów win32 w trybie offline   |obsługiwane, użytkownik musi wybrać etykietę i ręcznie zastosować |
|Online Office klientów win32 w trybie online|obsługiwane ze starym schematem ufności |
|Outlook online   |obsługiwane ze starym schematem ufności  |
|Office klienta aplikacji WAC     |obsługiwane |
|OWA     |obsługiwane |
|Exchange transport     |nie jest obsługiwane |
|OneDrive dla Firm danych w spoczynku     |obsługiwane |
|SharePoint danych online w spoczynku|obsługiwane|
|Skaner usługi Azure Information Protection (AIP)|nie jest obsługiwane|

## <a name="known-issues"></a>Znane problemy

|Problem  |Wpływ  |
|---------|---------|
|Porady dotyczące zasad DLP (OWA, Outlook i Office Win32)     |   Porady dotyczące zasad z warunkiem jednostki będą powodować "brak dopasowania"      |
| Obsługa azjatyckich języków dla imienia i nazwiska osoby (chiński, japoński, koreański)    | Nazwane jednostki obsługiwane tylko dla zestawu znaków opartych na alfabetu łacińskim (czyli nazwa kanji nie jest obsługiwana) dla imienia i nazwiska osoby        |
|Repozytoria lokalne    | Nie obsługiwane jako obciążenie pracą|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>Więcej informacji
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Dowiedz się więcej o nazwanych jednostkach (wersja zapoznawcza)](named-entities-learn.md).
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
