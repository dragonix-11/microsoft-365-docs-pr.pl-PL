---
title: podręcznik Microsoft 365 wersji próbnej rozwiązań zgodności
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: Microsoft 365 dotyczące wersji próbnej rozwiązań zgodności.
ms.openlocfilehash: fc04e5d745997e31799511d4a9edb7e7207f4088
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63015969"
---
# <a name="trial-playbook-microsoft-365-compliance-solutions"></a>Podręcznik wersji próbnej: Microsoft 365 rozwiązania do zgodności

Witamy w podręczniku Microsoft 365 rozwiązania zgodności z przepisami. Ten podręcznik pomoże Ci w pełnej 90-dniowej bezpłatnej wersji próbnej, pomagając Ci w odkrywaniu niezawodnych i kompleksowych funkcji produktów firmy Microsoft 365 dotyczących zgodności z przepisami i zabezpieczeń.

Wypróbowanie każdego rozwiązania pomoże w podejmowania przeszłych decyzji dotyczących zgodności z przepisami organizacji.

Funkcje:

- [Inspekcja zaawansowana](#advanced-audit)
- [Zgodność komunikacji](#communication-compliance)
- [Menedżer zgodności](#compliance-manager)
- [Ochrona przed utratą danych](#data-loss-prevention)
- [zbierania elektronicznych materiałów dowodowych](#ediscovery)
- [Ochrona informacji](#information-protection)
- [Zarządzanie ryzykiem w niejawnym programie testów](#insider-risk-management)
- [Zarządzanie rekordami](#records-management)

Opcjonalne dodatki:

- [Oceny premium w Menedżerze zgodności](#compliance-manager-premium-assessments)
- [Żądania praw osób trzecich dotyczące zarządzania ryzykiem prywatności w firmie Microsoft Priva i Microsoft Priva](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-365"></a>Akcje dotyczące zgodności z Microsoft 365

Łatwo i szybko rozpocznij wypróbowanie rozwiązań firmy Microsoft dotyczących zgodności bez zmieniania danych meta Twojej organizacji. W zależności od priorytetów możesz zacząć od dowolnego z tych obszarów rozwiązania, aby zobaczyć natychmiastową wartość. Poniżej znajduje się pięć najogorętszych problemów dotyczących organizacji, z których skomunikowali się nasi klienci, oraz zalecane rozwiązania na początek.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="Akcje dotyczące zgodności z Microsoft 365":::

## <a name="advanced-audit"></a>Inspekcja zaawansowana

**Przeprowadzanie badań**

Zaawansowana inspekcja ułatwia organizacjom przeprowadzanie analiz prawnych i zgodności, zwiększając liczbę działań w dzienniku inspekcji wymaganym do przeprowadzenia badania, zapewniając dostęp do ważnych zdarzeń pomocnych w określeniu zakresu naruszenia bezpieczeństwa oraz zapewniając szybszy dostęp do interfejsu API działań zarządzania Office 365 zarządzaniem.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>Krok 1. [Zastosuj licencję E5](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users) do każdego użytkownika, dla którego chcesz wygenerować zdarzenia E5

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Zaawansowane funkcje inspekcji, takie jak możliwość rejestrować ważne zdarzenia, takie jak MailItemsAccessed i Send, wymagają odpowiedniej licencji usługi E5 przypisanej do użytkowników. Ponadto dla tych użytkowników musi być włączony plan usługi/aplikacji zaawansowanej inspekcji.

Konfigurowanie inspekcji zaawansowanej dla użytkowników — aby sprawdzić, czy aplikacja inspekcji zaawansowanej została przypisana do użytkowników, wykonaj następujące czynności [dla każdego użytkownika](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users).

1. Włącz zdarzenia inspekcji zaawansowanej — [włącz inspekcję SearchQueryInitiatedExchange i SearchQueryInitiatedSharePoint](set-up-advanced-audit.md#step-2-enable-advanced-audit-events) w celu umożliwienia każdemu użytkownikowi inspekcji w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
1. Konfigurowanie zasad przechowywania [inspekcji — tworzenie](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) dodatkowych zasad przechowywania dziennika inspekcji w celu spełnienia wymagań zespołów ds. zabezpieczeń organizacji, it i zgodności.
1. Wyszukiwanie zdarzeń inspekcji zaawansowanej — [wyszukaj istotne](set-up-advanced-audit.md#step-4-search-for-advanced-audit-events) zdarzenia inspekcji zaawansowanej i inne działania podczas prowadzenia dochodzenia sądowego.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>Krok 2. Tworzenie nowych zasad dziennika inspekcji w celu określenia, jak długo mają być zachowywane dzienniki inspekcji w organizacji w przypadku działań wykonywanych przez użytkowników i [zdefiniowanie](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) poziomów priorytetów zasad

> [!TIP]
> Najlepsze rozwiązanie w wersji próbnej: tworzenie w ciągu pierwszych 30 dni

Zasady przechowywania dziennika inspekcji są częścią nowych funkcji zaawansowanej inspekcji w programie Microsoft 365. Zasady przechowywania dziennika inspekcji pozwalają określić, jak długo mają być zachowywane dzienniki inspekcji w organizacji.

1. Przed utworzeniem zasad przechowywania dziennika [inspekcji— kluczowych](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) informacji przed utworzeniem zasad.
1. [Tworzenie zasad przechowywania dziennika inspekcji](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [Zarządzanie zasadami przechowywania dziennika inspekcji w aplikacji usługi Centrum zgodności platformy Microsoft 365](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center) — zasady przechowywania dziennika inspekcji znajdują się na karcie Zasady przechowywania inspekcji (nazywanej również pulpitem nawigacyjnym). Za pomocą pulpitu nawigacyjnego można wyświetlać, edytować i usuwać zasady przechowywania inspekcji.
1. Tworzenie zasad przechowywania dziennika inspekcji i zarządzanie nimi w programie PowerShell — za pomocą programu PowerShell & Centrum zabezpieczeń i zgodności możesz także tworzyć zasady przechowywania dziennika inspekcji i zarządzać [nimi](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell). Jednym z powodów korzystania z programu PowerShell jest utworzenie zasad dla typu rekordu lub działania, które nie jest dostępne w interfejsie użytkownika.

## <a name="communication-compliance"></a>Zgodność komunikacji

**Identyfikowanie i działanie na podstawie kodeksu postępowania naruszeń zasad**

Zgodność komunikacji ułatwia inteligentne identyfikowanie naruszeń komunikacji w celu obsługi zgodnego i zdrowego środowiska pracy, pomagając wykrywać nieodpowiednie wiadomości, badać możliwe naruszenia zasad i podjąć działania naprawcze.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>Krok 1. [Włączanie uprawnień do zgodności komunikacji](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

[Przypisz wszystkich użytkowników zgodności do grupy ról Zgodność komunikacji](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).
### <a name="step-2-enable-the-audit-log"></a>Krok 2. [Włączanie dziennika inspekcji](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> Najlepsze rozwiązanie w wersji próbnej: Konfigurowanie w ciągu pierwszych 30 dni

Aby skorzystać z tej funkcji, włącz inspekcję, aby twoja organizacja rozpoczynała rejestrowanie aktywności użytkowników i administratorów w organizacji. Po włączeniu tej czynności działania będą rejestrowane w dzienniku inspekcji i dostępne do wyświetlania w raporcie. Aby dowiedzieć się więcej, zobacz [Włączanie lub wyłączanie wyszukiwania w dzienniku inspekcji](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>Krok 3. [Tworzenie zasad zgodności komunikacji](communication-compliance-policies.md)

[Tworzenie zasad zgodności komunikacji przy użyciu istniejących szablonów](communication-compliance-policies.md): 1- Nieodpowiednia zawartość; 2- Informacje poufne; 3. Zgodność z przepisami; 4. Konflikt zainteresowania.

### <a name="step-4-investigate-and-remediate-alerts"></a>Krok 4. [Badanie i rozwiązywanie problemów z alertami](communication-compliance-investigate-remediate.md)

[Badanie i rozwiązywanie problemów dotyczących alertów](communication-compliance-investigate-remediate.md) zgodności komunikacji.

## <a name="compliance-manager"></a>Menedżer zgodności

**Łatwe zarządzanie zgodnością w organizacji**

Menedżer zgodności może ułatwić Ci pozostawanie na drodze do zapewnienia zgodności z przepisami, od sporządzania spisu informacji o ryzyku związanym z ochroną danych, przez zarządzanie skomplikowaniem wdrażania kontroli, pozostawanie na czasie dzięki regulacjom i certyfikatom, a także raportowanie audytorom.

### <a name="step-1-get-to-know-compliance-manager"></a>Krok 1. [Poznaj Menedżera zgodności](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Strona przeglądu Menedżera zgodności jest najlepszym pierwszym etapem kompleksowego przeglądu tego, czym jest Menedżer zgodności i jak to działa. Możesz również przejść bezpośrednio do kluczowych sekcji naszej dokumentacji, korzystając z poniższych linków:

- [Opis wyniku w zakresie zgodności](compliance-manager.md#understanding-your-compliance-score)
- [Omówienie kluczowych elementów: kontrolek, ocen, szablonów i działań usprawnień](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [Opis pulpitu nawigacyjnego Menedżera zgodności](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [Filtrowanie widoku pulpitu nawigacyjnego](compliance-manager-setup.md#filtering-your-dashboard-view)
- [Dowiedz się więcej o działaniach usprawnień](compliance-manager-setup.md#improvement-actions-page)
- [Opis ocen](compliance-manager.md#assessments)
- [Wykonaj szybkie skanowanie środowiska za pomocą centrum zgodności firmy Microsoft Menedżer konfiguracji](compliance-manager-mcca.md)

![Menedżer zgodności — pulpit nawigacyjny.](../media/compliance-manager-dashboard.png "Pulpit nawigacyjny Menedżera zgodności")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>Krok 2. Konfigurowanie [Menedżera zgodności w celu zarządzania działaniami zgodności](compliance-manager-assessments.md)

> [!TIP]
> Najlepsze rozwiązanie w wersji próbnej: Inspekcja w ciągu pierwszych 30 dni

Rozpoczynanie pracy z ocenami i podejmowanie działań udoskonalania w celu wdrożenia kontroli i poprawienia wyniku zgodności.

1. [Wybierz wstępnie wbudowany szablon, aby utworzyć pierwszą ocenę i zarządzać jej](compliance-manager-assessments.md).
1. [Dowiedz się, jak używać szablonów do tworzenia ocen](compliance-manager-templates.md).
1. [Przekonuj prace implementacji i testowania nad działaniami udoskonalania, aby ukończyć kontrolę w testach](compliance-manager-improvement-actions.md).
1. [Lepiej zrozumieć, jak różne akcje wpływają na ocenę zgodności](compliance-score-calculation.md).

> [!NOTE]
> Microsoft 365 lub Office 365 E1/E3 zawiera szablon Planu bazowego ochrony danych firmy Microsoft. Microsoft 365 lub Office 365 E5 zgodności E5 zawiera szablony dla:
>
> - Plan bazowy ochrony danych firmy Microsoft
> - RODO Unii Europejskiej  
> - ISO/IEC 27001,
> - NIST 800-53
>
> Menedżer zgodności zawiera ponad 300 szablonów prawnych lub premium, które można kupić jako dodatek. Lista jest tutaj. Wszystkie szablony klasy premium (dołączone do Twojej subskrypcji lub kupione jako dodatek) będą zawierały uniwersalną wersję tych szablonów, co pozwoli Ci zarządzać zgodnością z każdym produktem lub usługą.

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>Krok 3. [Skalowanie: korzystanie z zaawansowanych funkcji w celu zaspokojenia potrzeb niestandardowych](compliance-manager-templates-create.md)

Oceny niestandardowe są przydatne w przypadku:

- Zarządzanie zgodnością dla produktów Microsoft 365 innych firm, takich jak usługi i aplikacje innych firm, aplikacje lokalne i inne zasoby
- Zarządzanie własnymi niestandardowymi lub firmowych mechanizmami kontroli zgodności

1. [Rozszerzanie szablonu Menedżera zgodności przez dodanie własnych kontrolek i działań udoskonalania](compliance-manager-templates-extend.md)
1. [Tworzenie własnego szablonu niestandardowego](compliance-manager-templates-create.md)
1. [Modyfikowanie istniejącego szablonu w celu dodania lub usunięcia kontrolek i akcji](compliance-manager-templates-modify.md)
1. [Konfigurowanie automatycznego testowania działań udoskonalania](compliance-manager-setup.md#set-up-automated-testing)
1. [Ponowne przypisanie akcji udoskonalania do innego użytkownika](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-loss-prevention"></a>Ochrona przed utratą danych

**Ochrona danych poufnych**

Aby zapewnić zgodność ze standardami biznesowymi i przepisami branżowymi, organizacje muszą chronić informacje poufne, aby zapobiec ich niezamierzonemu ujawnianiu. Skonfiguruj zasady ochrony przed utratą danych, aby identyfikować, monitorować i automatycznie chronić poufne informacje na różnych Microsoft 365.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>Krok 1. [Ochrona przed utratą danych w Teams lokalizacji](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Jeśli Twoja organizacja korzysta z ochrony przed utratą danych (DLP, data loss prevention), możesz zdefiniować zasady uniemożliwiające innym osobom udostępnianie poufnych informacji w Microsoft Teams kanale lub sesji czatu.

1. Informacje o [licencjonowaniu ochrony przed Microsoft Teams DLP i zakresie ochrony przed DLP](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)
1. [Dodawanie Microsoft Teams jako lokalizacji do istniejących zasad DLP](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [Skonfiguruj nasze domyślne zasady DLP](mip-easy-trials.md) Teams [lub Definiuj nowe zasady DLP dla Microsoft Teams](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>Krok 2. [Ochrona utraty danych w lokalizacjach urządzeń](endpoint-dlp-getting-started.md)

> [!TIP]
> Najlepsze rozwiązanie w wersji próbnej: Konfigurowanie w ciągu pierwszych 30 dni

Funkcja DLP punktu końcowego firmy Microsoft pozwala monitorować, Windows 10 urządzenia i wykrywać, kiedy są używane i udostępniane poufne elementy.

1. Przygotowywanie punktów końcowych — upewnij się, że urządzenia Windows 10 i macOS, które planujesz wdrożyć zasady DLP punktu końcowego, aby spełnić [te wymagania](endpoint-dlp-getting-started.md)
1. [Urządzenia na urządzeniach do zarządzania urządzeniami](endpoint-dlp-getting-started.md)  — aby monitorować i chronić poufne elementy na urządzeniu, należy włączyć monitorowanie urządzeń i włączyć ich punkty końcowe. Obie te czynności są wykonywane w portalu Microsoft 365 zgodności.
   - Scenariusz 1 [. Urządzenia dołączające](endpoint-dlp-getting-started.md) , które nie zostały jeszcze wnoszone.
   - Scenariusz 2. [Usługa Microsoft Defender for Endpoint jest już wdrożona i istnieją punkty końcowe raportowania](endpoint-dlp-getting-started.md). Wszystkie te punkty końcowe zostaną wyświetlone na liście urządzeń zarządzanych.
1. [Skonfiguruj nasze domyślne zasady DLP dla urządzeń](mip-easy-trials.md#dlp-for-devices) lub [Definiuj nowe zasady DLP dla urządzeń](endpoint-dlp-learn-about.md).
1. [Wyświetlanie alertów DLP dla punktów końcowych na](dlp-configure-view-alerts-policies.md) pulpicie nawigacyjnym zarządzania alertami DLP.
1. [Wyświetl dane DLP punktu końcowego w](data-classification-activity-explorer.md) Eksploratorze aktywności.

### <a name="step-3-expand-policies-in-scope-or-protection"></a>Krok 3. [Rozwijanie zasad w zakresie lub ochronie](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

Masz elastyczność w zakresie konfigurowania zasad DLP. Możesz zacząć od naszych domyślnych zasad DLP dla Teams i urządzeń i rozwinąć je, aby chronić dodatkowe lokalizacje, typy informacji poufnych lub etykiety. Ponadto można rozwinąć po działaniach zasad i dostosować alerty.

1. Dodawanie lokalizacji
1. Dodawanie typów informacji poufnych lub etykiet w celu ochrony
1. Dodawanie akcji
   - Teams:
      - [Uniemożliwianie dostępu zewnętrznego do poufnych dokumentów](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [Uzyskaj porady dotyczące zasad, które ułatwiają pomaganie użytkownikom w edukacji, oraz instrukcje dotyczące dostosowywania porad dotyczących zasad](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - Urządzenia: przełączanie z inspekcji tylko do blokowania
1. [Konfigurowanie i wyświetlanie alertów dotyczących zasad ochrony przed utratą danych — informacje Microsoft 365 dotyczące zgodności | Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>zbierania elektronicznych materiałów dowodowych

**Odkryj więcej dzięki end-to-endowi przepływu pracy**

Przy zachowaniu, zbieraniu, analizowaniu i eksportowaniu zawartości, która odpowiada wewnętrznym i zewnętrznym analizom Twojej organizacji, skorzystaj z zalet końcowego przepływu pracy. Zespoły prawne mogą również zarządzać całym procesem powiadamiania o zerowaniu ze strony prawnej, komunikując się z opiekunami zaangażowanymi w sprawę.

### <a name="step-1-required-permissions"></a>Krok 1 (wymagany): [Uprawnienia](https://aka.ms/ediscoveryninja)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Aby uzyskać Advanced eDiscovery lub dodać go jako członka do sprawy Advanced eDiscovery, użytkownikowi muszą zostać przypisane odpowiednie uprawnienia.

1. [Konfigurowanie usługi Advanced eDiscovery — przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [Dodawanie lub usuwanie członków w sprawie](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>Krok 2 (wymagany): Tworzenie sprawy

> [!TIP]
> Najlepsze rozwiązanie w wersji próbnej: tworzenie w ciągu pierwszych 30 dni

Więcej organizacji korzysta z Advanced eDiscovery w programie Microsoft 365 w krytycznych procesach zbierania elektronicznych materiałów dowodowych. Obejmuje to odpowiadanie na żądania prawne, dochodzenia i procesy.

1. Zarządzanie Advanced eDiscovery — dowiedz się, jak skonfigurować usługę Advanced eDiscovery, zarządzać sprawami przy użyciu Centrum zgodności usługi [&,](/learn/modules/manage-advanced-ediscovery) zarządzać przepływem pracy w programie Advanced eDiscovery i analizować wyniki Advanced eDiscovery wyszukiwania.
1. [Tworzenie sprawy zbierania elektronicznych materiałów dowodowych przy użyciu nowego formatu sprawy zbierania elektronicznych materiałów dowodowych](advanced-ediscovery-new-case-format.md)
1. [Zamknięcie lub usunięcie sprawy —](close-or-delete-case.md) po zakończeniu postępowania sądowego lub śledztwa można zamknąć lub usunąć sprawę. Możesz także ponownie otworzyć zamkniętą sprawę.

### <a name="step-3-optional-settings"></a>Krok 3 (opcjonalny): Ustawienia

Aby zezwolić osobom w twojej organizacji na rozpoczynanie tworzenia i używania spraw, musisz skonfigurować ustawienia globalne, które będą stosowane do wszystkich spraw w organizacji. Obecnie jedynym ustawieniem globalnym jest wykrywanie uprawnień klienta-klienta **(w** przyszłości będzie dostępnych więcej ustawień globalnych).

1. [Konfigurowanie Advanced eDiscovery — ustawienia globalne Ustawienia](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-advanced-ediscovery)
1. [Konfigurowanie ustawień wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [Zarządzanie zadaniami w u Advanced eDiscovery](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>Krok 4 (opcjonalnie): [Granice zgodności](set-up-compliance-boundaries.md)

Granice zgodności tworzą logiczne granice w organizacji, które kontrolują lokalizacje zawartości użytkowników (takie jak skrzynki pocztowe, konta OneDrive i witryny SharePoint), które menedżerowie zbierania elektronicznych materiałów dowodowych mogą wyszukiwać. Ponadto kontrolują one, kto może uzyskać dostęp do spraw zbierania elektronicznych materiałów dowodowych używanych do zarządzania sprawami prawnie, zasobami kadrami lub innymi badaniami w organizacji.

![Granice zgodności składają się z filtrów uprawnień wyszukiwania, które sterują dostępem do instytucji i grup ról administratorów, które kontrolują dostęp do spraw zbierania elektronicznych materiałów dowodowych.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

Konfigurowanie granic zgodności dla badań zbierania elektronicznych materiałów dowodowych:

1. [Identyfikowanie atrybutu użytkownika w celu zdefiniowania agencji](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [Tworzenie grupy ról dla każdej agencji](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [Tworzenie filtru uprawnień wyszukiwania w celu wymuszenia granicy zgodności](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [Tworzenie sprawy zbierania elektronicznych materiałów dowodowych dla dochodzenia wewnątrz agencji](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>Krok 5 (opcjonalnie): [Informacje o narzędziu przeszukiwania zawartości](search-for-content.md)

Za pomocą narzędzia Przeszukiwanie zawartości w aplikacji Centrum zgodności platformy Microsoft 365 możesz szybko znaleźć wiadomości e-mail w skrzynkach pocztowych programu Exchange, dokumentach w witrynach SharePoint i lokalizacjach usługi OneDrive oraz w konwersacjach za pomocą wiadomości błyskawicznych w Skype dla firm. Za pomocą narzędzia do wyszukiwania zawartości możesz wyszukiwać wiadomości e-mail, dokumenty i konwersacje za pomocą wiadomości błyskawicznych w narzędziach do współpracy, takich Microsoft Teams i Microsoft 365 Grupy.

- [Dowiedz się więcej o Advanced eDiscovery wyszukiwania](search-for-content.md#search-for-content)

## <a name="information-protection"></a>Ochrona informacji

**Odnajdowanie, klasyfikowanie i ochrona informacji poufnych**

Implementuj Microsoft Information Protection etykiety wrażliwości, aby ułatwić odnajdowanie, klasyfikowanie i ochronę poufnej zawartości niezależnie od miejsca, w którym mieszka lub podróżujesz.

### <a name="step-1-start-your-information-protection-trial"></a>Krok 1. [Rozpoczynanie okresu próbnego ochrony informacji](mip-easy-trials.md)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Uprawnieni klienci mogą aktywować etykiety i zasady domyślne dla Microsoft Information Protection. Po włączeniu konfiguracji domyślnej w wersji próbnej skonfigurowanie wszystkich zasad dla dzierżawy i do 24 godzin w celu zobaczenia wyników tych zasad domyślnych potrwa około 2 minut.

Wybranie konfiguracji domyślnej jednym kliknięciem spowoduje automatyczne skonfigurowanie następujących ustawień:

- Etykiety wrażliwości i zasady wrażliwości
- Automatyczne etykiety po stronie klienta
- Automatyczne etykiety po stronie serwisowej
- Zasady ochrony przed utratą danych (DLP) dotyczące Teams i urządzeń

[Uaktywnienie domyślnych etykiet i zasad](mip-easy-trials.md#activate-the-default-labels-and-policies). W razie potrzeby można edytować ręcznie po zakończeniu konfiguracji.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>Krok 2. [Automatyczne stosowanie etykiet wrażliwości do dokumentów](apply-sensitivity-label-automatically.md)

> [!TIP]
> Najlepsze rozwiązanie w wersji próbnej: Konfigurowanie w ciągu pierwszych 30 dni

Po utworzeniu etykiety wrażliwości możesz ją automatycznie przypisać do plików i wiadomości e-mail, jeśli jest ona taka, jaka jest do warunków określonych przez Ciebie.

1. [Tworzenie i konfigurowanie etykiet wrażliwości](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [Publikowanie zasad etykiet wrażliwości dla wszystkich użytkowników](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [Tworzenie zasad automatycznego oznaczania etykiet](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - Wybierz informacje, do których chcesz zastosować etykietę
   - Definiowanie lokalizacji do zastosowania etykiety
   - Wybierz etykietę do zastosowania
   - [Zasady uruchamiania w trybie symulacyjnej](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![Konfiguracja nowych zasad do automatycznego oznaczania etykiet.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>Krok 3. [Przeglądanie i włączanie zasad automatycznego oznaczania etykiet](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

Teraz na **stronie Ochrona** **informacjiAutomatyczne** >  etykiety są dostępne w sekcji **Symulacja** w zasadach auto etykiet.

Wybierz zasady, aby wyświetlić szczegóły konfiguracji i stanu. Po zakończeniu symulacyjnej wybierz kartę Elementy do przejrzenia, aby sprawdzić, które wiadomości e-mail lub dokumenty są zgodne z określonymi regułami.

Gdy wszystko będzie gotowe do uruchomienia zasad bez symulowania, wybierz opcję **Włącz zasady** .

## <a name="insider-risk-management"></a>Zarządzanie ryzykiem w niejawnym programie testów

**Wykrywanie i rozwiązywanie problemów z niejawnym programem testów**

Skorzystaj ze sztucznej inteligencji, aby ułatwić szybkie identyfikowanie, określanie i rozwiązywanie problemów wewnętrznych. Za pomocą dzienników z usługi Microsoft 365 i usług Azure możesz zdefiniować zasady monitorujące sygnały ryzyka niejawnego programu testów, a następnie podjąć działania naprawcze, takie jak promowanie edukacji użytkowników lub inicjowanie badania.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Krok 1 (wymagany): Włączanie [uprawnień do zarządzania ryzykiem w niejawnym programie testów](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Do konfigurowania uprawnień do zarządzania funkcjami zarządzania ryzykiem w niejawnym programie testów są używane cztery grupy ról.

[Dodawanie użytkowników do grupy ról zarządzania ryzykiem w niejawnym programie testów.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

Jeśli nie widzisz uprawnień, skontaktuj się z administratorem dzierżawy, aby przypisać odpowiednie role.

### <a name="step-2-start-with-user-quick-start-guide"></a>Krok 2. [Rozpoczynanie pracy z przewodnikiem Szybki start dla użytkownika](insider-risk-management-configure.md#recommended-actions-preview)

Szybko rozpoczynaj pracę i wyeksymlij możliwości zarządzania ryzykiem w ramach niejawnego programu testów dzięki zalecanym działaniom. Na stronie Przegląd zalecane akcje ułatwiają konfigurowanie i wdrażanie zasad oraz akcje badania dotyczące akcji użytkownika generujące alerty na podstawie dopasowania zasad.

[Wybierz z listy zalecenie, aby](insider-risk-management-configure.md#recommended-actions-preview) rozpocząć konfigurowanie zarządzania ryzykiem w niejawnym programie testów.

![Zalecane działania w ramach zarządzania ryzykiem w ramach niejawnego programu testów.](../media/insider-risk-recommended-actions.png)

Każda zalecana akcja przeprowadzi Cię przez działania wymagane do zalecenia, w tym wymagania, czego można oczekiwać i jaki wpływ ma skonfigurowanie tej funkcji w organizacji.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>Krok 3 (wymagany): [włączanie dziennika Microsoft 365 inspekcji](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

Inspekcja jest domyślnie włączona Microsoft 365 organizacji. Niektóre organizacje mogą wyłączyć inspekcję z określonych powodów. Jeśli w Twojej organizacji inspekcja jest wyłączona, może to być spowodowane tym, że inny administrator wyłączył ją. Zalecamy potwierdzenie, że po wykonaniu tego kroku można ponownie włączyć inspekcję.

Aby uzyskać instrukcje krok po kroku dotyczące dotyczące włączanie inspekcji, zobacz Włączanie lub wyłączanie przeszukiwania [dziennika inspekcji](turn-audit-log-search-on-or-off.md). Po włączeniu inspekcji jest wyświetlany komunikat informujący, że dziennik inspekcji jest przygotowywany i że po upływie kilku godzin od zakończenia przygotowywania można uruchomić wyszukiwanie. Wystarczy wykonać tę czynność tylko raz. Aby uzyskać więcej informacji na temat korzystania z Microsoft 365 inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>Krok 4 (wymagany): Włączanie i wyświetlanie szczegółowych informacji z analizy ryzyka [w niejawnym programie testów](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

Analiza ryzyka w niejawnym programie testów umożliwia przeprowadzenie oceny potencjalnych czynników ryzyka niejawnego programu testów w organizacji bez konfigurowania żadnych zasad ryzyka niejawnego programu testów. Wyniki analizy mogą zająć do 48 godzin, zanim szczegółowe informacje będą dostępne jako raporty do przejrzenia. Aby dowiedzieć się więcej o szczegółowych informacjach z analiz, zobacz Ustawienia zarządzania ryzykiem w ramach niejawnego programu testów [: Analiza (wersja zapoznawcza)](insider-risk-management-settings.md) i obejrzyj klip wideo z analizą ryzyka w ramach niejawnego programu testów( [Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) ), który pomaga zrozumieć stan ryzyka niejawnego programu testów i pomóc Ci w podjęciu działań przez skonfigurowanie odpowiednich zasad w celu identyfikowania ryzykownych użytkowników.

Aby włączyć analizę ryzyka niejawnego programu testów, musisz być członkiem grupy Insider Risk Management lub administratora zarządzania ryzykiem w niejawnym programie testów. Wykonaj poniższe czynności, aby włączyć analizę [ryzyka niejawnego programu testów](insider-risk-management-configure.md).

## <a name="records-management"></a>Zarządzanie rekordami

**Automatyzowanie harmonogramu przechowywania rekordów o krytycznym znaczeniu dla firmy**

Zintegrowane funkcje zarządzania rekordami pozwalają zautomatyzować harmonogram przechowywania rekordów dotyczących wymogów prawnych, prawnych i biznesowych organizacji. Uzyskaj pełną obsługę cyklu życia zawartości, od tworzenia do współpracy, deklaracji rekordu, przechowywania i operacji ich przechowywania.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>Krok 1. Dynamiczne kierowanie zasad przechowywania za pomocą adaptacyjnych zakresów zasad

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Zakresy adaptacyjnych zasad umożliwiają dynamiczne kierowanie zasad do określonych użytkowników, grup lub witryn na podstawie ich atrybutów USŁUGI AD.

Atrybuty zakresów można wybierać z listy lub dostosowywać przy użyciu zaawansowanego konstruktora zapytań.

Zasady korzystające z zakresów adaptacyjnych zasad pozostają aktualne w przypadku zmiany organizacji wraz z dołączanie do nich lub opuszczanie nowych pracowników. Ponadto nie podlegają one poprzednim limitom 100/1000 lokalizacji uwzględnionych w zasadach.

- Tworzenie [adaptacyjnego zakresu zasad](retention.md#adaptive-or-static-policy-scopes-for-retention) i korzystanie z niego przy użyciu zasad przechowywania

### <a name="step-2-automate-labeling-of-sensitive-information-with-the-ability-to-review-before-disposal"></a>Krok 2. Automatyzowanie oznaczania poufnych informacji etykietami z możliwością przejrzenia przed ich usunięciem

> [!TIP]
> Najlepsze rozwiązanie w wersji próbnej: Konfigurowanie w ciągu pierwszych 30 dni

Etykiety przechowywania można skonfigurować w taki sposób, aby stosowane automatycznie do zawartości po wykryciu informacji poufnych, takich jak numer karty kredytowej. Dzięki temu użytkownicy nie muszą ręcznie wykonywać czynności z etykietami.

Po zakończeniu okresu przechowywania użytkownicy określeni przez Użytkownika ("recenzentzy") zostaną powiadomieni o przejrzeniu zawartości i zatwierdzeniu akcji trwałego usuwania. Dzięki temu jeśli dane dane muszą zostać zachowane na dłuższy czas, może tak być.

Zarówno działania aplikacji etykiet, jak i działania przeglądu ich zawartości można wyświetlić na ekranie Omówienie zarządzania rekordami.

1. [Automatyczne stosowanie etykiet przechowywania do zawartości zawierającej informacje poufne](retention.md#retention-labels)
1. Tworzenie i stosowanie etykiety przechowywania z [recenzją rozsyłania](disposition.md#disposition-reviews) na końcu okresu przechowywania

### <a name="step-3-label-content-as-records-automatically-using-trainable-classifiers"></a>Krok 3. Etykieta zawartości jako rekordów automatycznie przy użyciu przeszkolnych klasyfikatorów

Gdy zawartość jest deklarowana jako rekord, na element są nakładane ograniczenia dotyczące akcji dozwolonych lub zablokowanych, rejestrowane są dodatkowe działania dotyczące tych elementów oraz dowód usunięcia elementów po zakończeniu okresu przechowywania.

Klasyfikatorzy przeszkoli to narzędzia, które rozpoznają różne typy zawartości na podstawie pobranych próbek. Do wyboru są różne wbudowane opcje lub niestandardowy klasyfikator dostosowany do określonych potrzeb.

1. Tworzenie etykiety przechowywania [deklarowania zawartości jako rekordu lub rekordu prawnego](records-management.md#records)
1. [Automatyczne stosowanie etykiet przechowywania do zawartości przy użyciu przeszkolnych klasyfikatorów](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

### <a name="more-information-auto-apply-retention-labels--disposition-review"></a>Więcej informacji: Automatyczne stosowanie etykiet przechowywania + przegląd rozsyłania

**Zastosuj etykiety automatycznie, aby zachować to, czego potrzebujesz...**
Etykiety przechowywania można automatycznie stosować do zawartości, jeśli zawierają:

- [Określone typy informacji poufnych](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)
- [Określone słowa kluczowe lub właściwości, które można wyszukiwać, zgodne z tworzyć zapytania](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties)
- [Dopasowanie dla klasyfikatorów przeszkolnych](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

**... a następnie zlikwiduj ją bezpiecznie na końcu.**

Gdy na koniec okresu przechowywania zostanie wyzwolona recenzja rozsyłania, wybieranie recenzentów powoduje otrzymywanie wiadomości e-mail z powiadomieniem, że mają zawartość do przejrzenia.

Zawartość oczekująca na recenzję usuwania jest trwale usuwana dopiero po ostatecznym etapie usuwania recenzenta zdecyduje o trwałym usunięciu zawartości.

## <a name="additional-trials-and-add-ons"></a>Dodatkowe wersje próbne i dodatki

### <a name="compliance-manager-premium-assessments"></a>Oceny premium w Menedżerze zgodności

**Ocenianie ryzyka i efektywne odpowiadanie**

Pomóż organizacji oceniać zagrożenia i wydajnie reagować na kraje, wymagania regionalne i branżowe dotyczące gromadzenia i używania danych.

[Więcej informacji na temat wersji próbnej testów premium menedżera zgodności](compliance-easy-trials-compliance-manager-assessments.md).

[Podręcznik wersji próbnej: Testy premium w menedżerze zgodności firmy Microsoft](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>Żądania praw osób trzecich dotyczące zarządzania ryzykiem prywatności w firmie Microsoft Priva i Microsoft Priva

**Identyfikowanie & ochrony prywatności**

Aktywne identyfikowanie i ochrona przed zagrożeniami prywatności, takimi jak przetwarzanie danych, przesyłanie danych i przekazywanie danych, oraz pomagaj organizacji automatyzować żądania dotyczące tematu i zarządzać nimi na skalę.

[Dowiedz się więcej o microsoft Priva](/privacy/solutions/privacymanagement/privacy-management).

[Podręcznik wersji próbnej: Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>Dodatkowe materiały

**Dostępne funkcje**: Aby uzyskać pełną listę rozwiązań i funkcji zgodności Microsoft 365 warstwie produktu, wyświetl [Macierz funkcji](https://go.microsoft.com/fwlink/?linkid=2139145).

**Biblioteka zawartości technicznej zabezpieczeń firmy Microsoft**. Zapoznaj się z tą biblioteką, aby znaleźć interakcyjne przewodniki i inną zawartość edukacyjną odpowiednią do Twoich potrzeb. [Odwiedź bibliotekę](/security/content-library).

**Zasoby zabezpieczeń firmy Microsoft**: od ochrony przed złośliwym oprogramowaniem do zerowego zaufania uzyskaj wszystkie istotne zasoby na potrzeby organizacji dotyczące zabezpieczeń. [Odwiedź stronę Resources (Zasoby](/security/business/resources)).
