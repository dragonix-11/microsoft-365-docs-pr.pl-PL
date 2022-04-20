---
title: Używanie nazwanych jednostek w zasadach DLP
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
ms.openlocfilehash: 108b21e7c5a6708a01a712dcd44788f489df0e73
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971588"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies"></a>Używanie nazwanych jednostek w zasadach ochrony przed utratą danych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Przed rozpoczęciem korzystania z nich zapoznaj się z artykułem [Dowiedz się więcej o nazwanych jednostkach](named-entities-learn.md) .

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie jednostek SKU/subskrypcji

Aby uzyskać szczegółowe informacje o licencjonowaniu, zobacz [opis usługi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Uprawnienia

Konto używane do tworzenia i edytowania zasad ochrony przed utratą danych (DLP) musi mieć uprawnienia roli **DLP Compliance Management** . Aby uzyskać więcej informacji, zobacz [Udzielanie użytkownikom dostępu do Centrum zgodności Office 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Obsługiwane lokalizacje

Do wykrywania i ochrony poufnych elementów w tych lokalizacjach można używać nazwanych interfejsów SIC jednostek i rozszerzonych zasad:

- witryny SharePoint
- konta OneDrive
- Teams wiadomości czatu i kanału
- Urządzenia (urządzenia Windows 10 i 11 urządzeń punktu końcowego)
- skrzynki pocztowe Exchange

Nazwane jednostki SIC i rozszerzone zasady nie są obsługiwane w następujących celach:

- Repozytoria lokalne
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Tworzenie i edytowanie rozszerzonych zasad

Aby utworzyć lub edytować zasady DLP, użyj procedur w [sekcji Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Obciążenia i usługi obsługujące nazwane jednostki

- **Microsoft 365 eDiscovery** obsługuje używanie nazwanych jednostek w usługach Substrate.
- **Microsoft Defender for Cloud Apps** obsługuje używanie nazwanych jednostek w zasadach Defender dla Chmury Apps w portalu aplikacji Defender dla Chmury.
- **Usługa Insider Risk Management** obsługuje korzystanie z nazwanych jednostek w usługach Substrate.
- **Usługa Records Management** obsługuje używanie nazwanych jednostek.
- **Dokładne typy informacji poufnych dopasowania danych** obsługuje użycie nazwanych jednostek.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>Ujednolicony DLP

|Obciążenie/usługi  |Obsługa jednostek nazwanych  |
|---------|---------|
|porada dotycząca zasad klientów Office Win32    |Nieobsługiwane  |
|porada dotycząca zasad klientów Office WAC    |Obsługiwane         |
|Porada dotycząca zasad OWA     |Nieobsługiwane         |
|Porada dotycząca zasad Outlook     |Nieobsługiwane |
|Punkty końcowe (Windows 10 i 11 urządzeń)     |Obsługiwane  |
|reguły transportu Exchange     |Obsługiwane |
|OneDrive dla Firm danych magazynowanych     |Obsługiwane         |
|SharePoint Dane w trybie online magazynowane     |Obsługiwane         |
|Teams danych magazynowanych     |Obsługiwane         |
|Dane w spoczynku wiadomości e-mail     |Obsługiwane w przypadku dzierżaw z planem usługi ochrony prywatności         |
|Microsoft Defender for Cloud Apps     |Obsługiwane         |

### <a name="autolabeling"></a>Automatyczne etykietowanie

|Obciążenie/usługi |Obsługa jednostek nazwanych  |
|---------|---------|
|Office klientów Win32 w trybie offline   |Obsługiwane, użytkownik musi wybrać etykietę i ręcznie zastosować |
|Klienci online Office Win32 online|Obsługiwane przy użyciu starego schematu ufności |
|Outlook online   |Obsługiwane przy użyciu starego schematu ufności  |
|klient Office WAC     |Obsługiwane |
|OWA     |Obsługiwane |
|transport Exchange     |Obsługiwane |
|OneDrive dla Firm danych magazynowanych     |Obsługiwane |
|SharePoint Dane w trybie online magazynowane|Obsługiwane|
|Skaner usługi Azure Information Protection (AIP)|nieobsługiwane|

## <a name="known-issues"></a>Znane problemy

|Problem  |Wpływ  |
|---------|---------|
|Porady dotyczące zasad DLP (klienci OWA, Outlook, Office Win32)     |   Porady dotyczące zasad dotyczące warunku jednostki spowodują "brak dopasowania"      |
| Obsługa języka azjatyckiego dla nazwy osoby (chiński, japoński, koreański)    | Jednostki nazwane obsługiwane tylko dla zestawu znaków opartych na języku łacińskim (czyli kanji nie jest obsługiwane) dla nazwy osoby        |
|Repozytoria lokalne    | Nieobsługiwane jako obciążenie|
|Power BI (wersja zapoznawcza) | Nieobsługiwane

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="best-practices-for-using-named-entity-sits"></a>Najlepsze rozwiązania dotyczące używania nazwanych SIC jednostek

Poniżej przedstawiono niektóre rozwiązania, których można użyć podczas tworzenia lub edytowania zasad używających nazwanej jednostki SIT.

- Użyj niskiej liczby wystąpień (od trzech do pięciu), gdy szukasz danych w arkuszu kalkulacyjnym, a słowo kluczowe wymagane przez sit dla tych danych znajduje się tylko w nagłówku kolumny. Załóżmy na przykład, że szukasz numerów ubezpieczenia społecznego w USA, a słowo kluczowe `Social Security Number` występuje tylko w nagłówku kolumny. Ponieważ wartości (dowody potwierdzające) znajdują się w poniższych komórkach, prawdopodobnie tylko kilka pierwszych wystąpień znajduje się w pobliżu słowa kluczowego, które ma zostać wykryte.  

- Jeśli używasz nazwanej jednostki SIT, takiej jak Wszystkie imiona i nazwiska, aby pomóc w znalezieniu numerów ubezpieczenia społecznego USA, użyj większej liczby wystąpień, takiej jak 10 lub 50. Następnie, gdy zarówno nazwy osób, jak i nazwy SSN są wykrywane razem, bardziej prawdopodobne jest uzyskanie prawdziwych wyników dodatnich.

- Za pomocą [symulacji automatycznego etykietowania](apply-sensitivity-label-automatically.md#learn-about-simulation-mode) można przetestować dokładność nazwanych jednostek SIC. Uruchom symulację przy użyciu nazwanej jednostki SIT, aby zobaczyć, które elementy są zgodne z zasadami. Dzięki tym informacjom można dostosować dokładność, dostosowując liczbę wystąpień i poziomy ufności w zasadach niestandardowych lub rozszerzonych warunkach szablonu. Przed wdrożeniem zasad DLP lub automatycznego etykietowania zawierających nazwane jednostki w środowisku produkcyjnym można iterować symulacje do momentu, gdy dokładność będzie odpowiednia. Oto omówienie przepływu:

1. Zidentyfikuj interfejs SIT lub kombinację interfejsów SIC, które chcesz przetestować w trybie symulacji, niestandardowe lub sklonowane i edytowane.
1. Zidentyfikuj lub utwórz etykietę poufności, która ma zostać zastosowana, gdy zasady automatycznego etykietowania wyszukują dopasowanie w Exchange, SharePoint witrynach lub kontach OneDrive.
1. Utwórz zasady automatycznego etykietowania poufności korzystające z interfejsu SIT z kroku 1 i z tymi samymi warunkami i wyjątkami, które będą używane w zasadach DLP
1. Uruchamianie symulacji zasad
1. Wyświetlanie wyników
1. Dostosuj zasady sit lub oraz liczbę wystąpień i poziomy ufności, aby zmniejszyć liczbę wyników fałszywie dodatnich.
1. Powtarzaj, aż uzyskasz żądane wyniki dokładności.


## <a name="for-further-information"></a>Aby uzyskać więcej informacji
- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Dowiedz się więcej o nazwanych jednostkach](named-entities-learn.md).
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
