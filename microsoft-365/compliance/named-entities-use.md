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
ms.openlocfilehash: 0cdf544eddf873f3bbf761bd613641433dd2da6b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623717"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies"></a>Używaj nazwanych obiektów w zasadach zapobiegania utracie danych

Przed rozpoczęciem korzystania z nich zapoznaj się z artykułem [Dowiedz się więcej o nazwanych jednostkach](named-entities-learn.md) .

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie jednostek SKU/subskrypcji

Aby uzyskać szczegółowe informacje o licencjonowaniu, zobacz [opis usługi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Uprawnienia

Konto używane do tworzenia i edytowania zasad ochrony przed utratą danych (DLP) musi mieć uprawnienia roli **DLP Compliance Management** . Aby uzyskać więcej informacji, zobacz [Udzielanie użytkownikom dostępu do Centrum zgodności Office 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Obsługiwane lokalizacje

Do wykrywania i ochrony poufnych elementów w tych lokalizacjach można używać nazwanych interfejsów SIC jednostek i rozszerzonych zasad:

- Witryny programu SharePoint
- Konta usługi OneDrive
- Wiadomości na czacie i kanale w usłudze Teams
- Urządzenia (urządzenia Windows 10 i 11 urządzeń punktu końcowego)
- Skrzynki pocztowe programu Exchange
- Microsoft Defender for Cloud Apps

Nazwane jednostki SIC i rozszerzone zasady nie są obsługiwane w następujących celach:

- Repozytoria lokalne
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Tworzenie i edytowanie rozszerzonych zasad

Aby utworzyć lub edytować zasady DLP, użyj procedur w [sekcji Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Obciążenia i usługi obsługujące nazwane jednostki

- **Usługa Microsoft 365 eDiscovery** obsługuje korzystanie z nazwanych jednostek w usługach Substrate.
- **Microsoft Defender for Cloud Apps** obsługuje używanie nazwanych jednostek w zasadach usługi Defender for Cloud Apps w portalu aplikacji usługi Defender for Cloud.
- **Usługa Insider Risk Management** obsługuje korzystanie z nazwanych jednostek w usługach Substrate.
- **Usługa Records Management** obsługuje używanie nazwanych jednostek.
- **Dokładne typy informacji poufnych dopasowania danych** obsługuje użycie nazwanych jednostek.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>Ujednolicony DLP

|Obciążenie/usługi  |Obsługa jednostek nazwanych  |
|---------|---------|
|Porada dotycząca zasad klientów usługi Office Win32    |Nieobsługiwane  |
|Porada dotycząca zasad klienta funkcji Office WAC    |Obsługiwane         |
|Porada dotycząca zasad OWA     |Nieobsługiwane         |
|Porada dotycząca zasad programu Outlook     |Nieobsługiwane |
|Punkty końcowe (Windows 10 i 11 urządzeń)     |Obsługiwane  |
|Reguły transportu exchange     |Obsługiwane |
|OneDrive dla Firm danych magazynowanych     |Obsługiwane         |
|Magazyn danych usługi SharePoint Online     |Obsługiwane         |
|Dane w spoczynku usługi Teams     |Obsługiwane         |
|Dane w spoczynku wiadomości e-mail     |Obsługiwane w przypadku dzierżaw z planem usługi ochrony prywatności         |
|Microsoft Defender for Cloud Apps     |Obsługiwane         |

### <a name="autolabeling"></a>Automatyczne etykietowanie

|Obciążenie/usługi |Obsługa jednostek nazwanych  |
|---------|---------|
|Klienci usługi Office Win32 w trybie offline   |Obsługiwane, użytkownik musi wybrać etykietę i ręcznie zastosować |
|Online klienci usługi Office Win32 w trybie online|Obsługiwane przy użyciu starego schematu ufności |
|Outlook online   |Obsługiwane przy użyciu starego schematu ufności  |
|Klient WAC pakietu Office     |Obsługiwane |
|OWA     |Obsługiwane |
|Transport wymiany     |Obsługiwane |
|OneDrive dla Firm danych magazynowanych     |Obsługiwane |
|Magazyn danych usługi SharePoint Online|Obsługiwane|
|Skaner usługi Azure Information Protection (AIP)|Nieobsługiwane|

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

- Jeśli używasz nazwanej jednostki SIT, takiej jak Wszystkie imiona i nazwiska, aby pomóc w znalezieniu numerów ubezpieczenia społecznego USA, użyj większej liczby wystąpień, takiej jak 10 lub 50. Następnie, gdy zarówno nazwiska osób, jak i nazwy SSN są wykrywane razem, bardziej prawdopodobne jest uzyskanie prawdziwych wyników dodatnich.

- Za pomocą [symulacji automatycznego etykietowania](apply-sensitivity-label-automatically.md#learn-about-simulation-mode) można przetestować dokładność nazwanych jednostek SIC. Uruchom symulację przy użyciu nazwanej jednostki SIT, aby zobaczyć, które elementy są zgodne z zasadami. Dzięki tym informacjom można dostosować dokładność, dostosowując liczbę wystąpień i poziomy ufności w zasadach niestandardowych lub rozszerzonych warunkach szablonu. Przed wdrożeniem zasad DLP lub automatycznego etykietowania zawierających nazwane jednostki w środowisku produkcyjnym można iterować symulacje do momentu, gdy dokładność będzie odpowiednia. Oto omówienie przepływu:

1. Zidentyfikuj interfejs SIT lub kombinację interfejsów SIC, które chcesz przetestować w trybie symulacji, niestandardowe lub sklonowane i edytowane.
1. Zidentyfikuj lub utwórz etykietę poufności do zastosowania, gdy zasady automatycznego etykietowania wyszukują dopasowanie na kontach programu Exchange, witryn programu SharePoint lub kontach usługi OneDrive.
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
