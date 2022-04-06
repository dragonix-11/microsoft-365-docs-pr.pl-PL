---
title: Używaj nazwanych jednostek w zasadach ochrony przed utratą danych (wersja zapoznawcza)
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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Te procedury umożliwiają korzystanie z nazwanych jednostek w zasadach ochrony przed utratą danych
ms.openlocfilehash: 9b3a8899ef4b64c682289e29df19648a00d4f048
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665167"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>Używaj nazwanych jednostek w zasadach ochrony przed utratą danych (wersja zapoznawcza)

> [!IMPORTANT]
> Funkcja nazwanych jednostek jest wdrażana i będzie wyświetlana w dzierżawie, gdy będzie dostępna dla Ciebie. Sprawdź je w Eksploratorze zawartości i w przepływie tworzenia zasad ochrony przed utratą danych (DLP). 

Przeczytaj artykuł [Dowiedz się więcej o nazwanych jednostkach (wersja zapoznawcza)](named-entities-learn.md) przed rozpoczęciem ich używania.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie jednostek SKU/subskrypcji

Musisz mieć jedną z tych subskrypcji

- Information Protection i ład
- Zgodność platformy Microsoft 365 E5
- Office 365 E5
- Microsoft 365 E5

Aby uzyskać szczegółowe informacje o licencjonowaniu, zobacz [opis usługi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Uprawnienia

Konto używane do tworzenia i edytowania zasad ochrony przed utratą danych (DLP) musi mieć uprawnienia roli **DLP Compliance Management** . Aby uzyskać więcej informacji, zobacz [Udzielanie użytkownikom dostępu do Centrum zgodności Office 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Obsługiwane lokalizacje

Do wykrywania i ochrony poufnych elementów w tych lokalizacjach można używać nazwanych interfejsów SIC jednostek i rozszerzonych zasad:

- witryny SharePoint
- konta OneDrive
- Teams wiadomości czatu i kanału
- Urządzenia (Windows 10 urządzenia punktu końcowego)

Nazwane jednostki SIC i rozszerzone zasady nie są obsługiwane w następujących celach:


- Repozytoria lokalne
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Tworzenie i edytowanie rozszerzonych zasad

Aby utworzyć lub edytować zasady DLP, użyj procedur w [sekcji Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Obciążenia i usługi obsługujące nazwane jednostki


- **Usługa Microsoft 3655 eDiscovery** obsługuje korzystanie z nazwanych jednostek w usługach Substrate.
- **Microsoft Defender for Cloud Apps** obsługuje używanie nazwanych jednostek w zasadach Defender dla Chmury Apps.
- **Usługa Insider Risk Management** obsługuje korzystanie z nazwanych jednostek w usługach Substrate.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>Ujednolicony DLP

|Obciążenie/usługi  |Publiczna obsługa wersji zapoznawczej dla jednostek nazwanych  |
|---------|---------|
|porada dotycząca zasad klientów Office Win32    |nieobsługiwane  |
|porada dotycząca zasad klientów Office WAC    |Obsługiwane         |
|Porada dotycząca zasad OWA     |nieobsługiwane         |
|Porada dotycząca zasad Outlook     |nieobsługiwane |
|Punkty końcowe (urządzenia Windows 10)     |Obsługiwane  |
|reguły transportu Exchange     |nieobsługiwane |
|OneDrive dla Firm danych magazynowanych     |Obsługiwane         |
|SharePoint Dane w trybie online magazynowane     |Obsługiwane         |
|Teams danych magazynowanych     |Obsługiwane         |
|Dane w spoczynku wiadomości e-mail     |nieobsługiwane         |
|Microsoft Defender for Cloud Apps     |Obsługiwane         |

### <a name="autolabeling"></a>Automatyczne etykietowanie

|Obciążenie/usługi |Publiczna obsługa wersji zapoznawczej dla jednostek nazwanych  |
|---------|---------|
|Office klientów Win32 w trybie offline   |obsługiwane, użytkownik musi wybrać etykietę i ręcznie zastosować |
|Klienci online Office Win32 online|obsługiwane za pomocą starego schematu ufności |
|Outlook online   |obsługiwane za pomocą starego schematu ufności  |
|klient Office WAC     |Obsługiwane |
|OWA     |Obsługiwane |
|transport Exchange     |nieobsługiwane |
|OneDrive dla Firm danych magazynowanych     |Obsługiwane |
|SharePoint Dane w trybie online magazynowane|Obsługiwane|
|Skaner usługi Azure Information Protection (AIP)|nieobsługiwane|

## <a name="known-issues"></a>Znane problemy

|Problem  |Wpływ  |
|---------|---------|
|Porady dotyczące zasad DLP (klienci OWA, Outlook, Office Win32)     |   Porady dotyczące zasad dotyczące warunku jednostki spowodują "brak dopasowania"      |
| Obsługa języka azjatyckiego dla nazwy osoby (chiński, japoński, koreański)    | Jednostki nazwane obsługiwane tylko dla zestawu znaków opartych na języku łacińskim (czyli kanji nie jest obsługiwane) dla nazwy osoby        |
|Repozytoria lokalne    | Nieobsługiwane jako obciążenie|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>Aby uzyskać więcej informacji
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Dowiedz się więcej o nazwanych jednostkach (wersja zapoznawcza).](named-entities-learn.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
