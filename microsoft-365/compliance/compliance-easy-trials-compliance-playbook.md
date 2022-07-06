---
title: Podręcznik wersji próbnej rozwiązań Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: Podręcznik wersji próbnej rozwiązań Microsoft Purview.
ms.custom: trial-playbook
ms.openlocfilehash: 2b84a3e5636edad78a9d221a0d088b84392cf49e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633790"
---
# <a name="trial-playbook-microsoft-purview-solutions"></a>Podręcznik wersji próbnej: rozwiązania Usługi Microsoft Purview

Witamy w podręczniku wersji próbnej rozwiązań Microsoft Purview. Ten podręcznik pomoże Ci w maksymalnym użyciu 90-dniowej bezpłatnej wersji próbnej, pomagając odkryć niezawodne i kompleksowe możliwości usługi Microsoft Purview i produktów zabezpieczających.

Wypróbowanie każdego rozwiązania pomoże Ci podjąć świadome decyzje w celu spełnienia wymagań organizacji w zakresie zgodności.

Funkcje:

- [Inspekcja (wersja Premium)](#audit-premium)
- [Zgodność z komunikacją](#communication-compliance)
- [Menedżer zgodności](#compliance-manager)
- [Zarządzanie cyklem życia danych](#data-lifecycle-management)
- [Ochrona przed utratą danych w Microsoft Purview](#data-loss-prevention)
- [Zbierania elektronicznych materiałów dowodowych](#ediscovery)
- [Information Protection](#information-protection)
- [Zarządzanie ryzykiem wewnętrznym](#insider-risk-management)
- [Zarządzanie rekordami](#records-management)

Opcjonalne dodatki:

- [Oceny premium programu Compliance Manager](#compliance-manager-premium-assessments)
- [zarządzanie ryzykiem prywatności Microsoft Priva i żądania praw podmiotów Microsoft Priva](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-purview"></a>Akcje zgodności w usłudze Microsoft Purview

Łatwo i szybko zacznij próbować rozwiązań firmy Microsoft w zakresie zgodności bez zmieniania metadanych organizacji. W zależności od priorytetów możesz zacząć od dowolnego z tych obszarów rozwiązania, aby zobaczyć natychmiastową wartość. Poniżej przedstawiono pięć najważniejszych problemów organizacyjnych przekazywanych przez naszych klientów i zalecane rozwiązania na początek.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="Akcje zgodności z platformą Microsoft 365":::

## <a name="audit-premium"></a>Inspekcja (wersja Premium)

**Prowadzenie dochodzeń**:

Inspekcja w Microsoft Purview (Premium) pomaga organizacjom przeprowadzać badania kryminalistyczne i badania zgodności poprzez zwiększenie przechowywania dzienników inspekcji wymaganych do przeprowadzenia badania, zapewnienie dostępu do kluczowych zdarzeń, które pomagają określić zakres naruszenia zabezpieczeń, oraz zapewnienie szybszego dostępu do interfejsu API działania zarządzania Office 365.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>Krok 1. [Stosowanie licencji E5 do każdego użytkownika, dla którego chcesz wygenerować zdarzenia E5](set-up-advanced-audit.md#step-1-set-up-audit-premium-for-users)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Funkcje inspekcji (Premium), takie jak możliwość rejestrowania kluczowych zdarzeń, takich jak MailItemsAccessed i Send, wymagają odpowiedniej licencji E5 przypisanej do użytkowników. Ponadto dla tych użytkowników należy włączyć plan aplikacji/usługi inspekcji zaawansowanej.

Skonfiguruj usługę Audit (Premium) dla użytkowników — aby sprawdzić, czy aplikacja Zaawansowana inspekcja jest przypisana do użytkowników, [wykonaj następujące kroki dla każdego użytkownika](set-up-advanced-audit.md#step-1-set-up-audit-premium-for-users).

1. Włącz zdarzenia inspekcji (Premium) — włącz inspekcję [zapytań SearchQueryInitiatedExchange i SearchQueryInitiatedSharePoint](set-up-advanced-audit.md#step-2-enable-audit-premium-events) dla każdego użytkownika w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
1. Konfigurowanie zasad przechowywania inspekcji — [utwórz dodatkowe zasady przechowywania dzienników inspekcji](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) , aby spełnić wymagania zespołów ds. operacji zabezpieczeń, it i zgodności w organizacji.
1. Wyszukaj zdarzenia inspekcji (Premium) — [wyszukaj kluczowe zdarzenia inspekcji (Premium)](set-up-advanced-audit.md#step-4-search-for-audit-premium-events) i inne działania podczas prowadzenia dochodzeń kryminalistycznych.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>Krok 2. [Tworzenie nowych zasad dziennika inspekcji w celu określenia czasu przechowywania dzienników inspekcji w organizacji dla działań wykonywanych przez użytkowników i definiowania poziomów priorytetów dla zasad](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: tworzenie w ciągu pierwszych 30 dni

Zasady przechowywania dzienników inspekcji są częścią nowych funkcji inspekcji (Premium) w usłudze Microsoft Purview. Zasady przechowywania dzienników inspekcji umożliwiają określenie czasu przechowywania dzienników inspekcji w organizacji.

1. Przed utworzeniem zasad przechowywania dziennika inspekcji — [najważniejsze informacje przed](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) utworzeniem zasad.
1. [Tworzenie zasad przechowywania dziennika inspekcji](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [Zarządzanie zasadami przechowywania dzienników inspekcji w portal zgodności Microsoft Purview](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-compliance-portal) — zasady przechowywania dzienników inspekcji są wyświetlane na karcie Zasady przechowywania inspekcji (nazywanej również pulpitem nawigacyjnym). Pulpit nawigacyjny umożliwia wyświetlanie, edytowanie i usuwanie zasad przechowywania inspekcji.
1. Tworzenie zasad przechowywania dzienników inspekcji i zarządzanie nimi w programie PowerShell — do [tworzenia zasad przechowywania dzienników inspekcji i zarządzania nimi](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell) można również użyć programu PowerShell & Zgodności z zabezpieczeniami. Jednym z powodów używania programu PowerShell jest utworzenie zasad dla typu rekordu lub działania, które nie są dostępne w interfejsie użytkownika.

## <a name="communication-compliance"></a>Zgodność z komunikacją

**Identyfikowanie naruszeń zasad kodeksu postępowania i ich działanie**:

Zgodność w komunikacji w Microsoft Purview pomaga inteligentnie identyfikować naruszenia komunikacji w celu obsługi zgodnego i zdrowego środowiska pracy, pomagając wykrywać nieodpowiednie komunikaty, badać możliwe naruszenia zasad i podejmować kroki w celu skorygowania problemu.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>Krok 1. [Włączanie uprawnień do zgodności komunikacji](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

[Przypisz wszystkich użytkowników zgodności do grupy ról Zgodność z komunikacją](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).

### <a name="step-2-enable-the-audit-log"></a>Krok 2. [Włączanie dziennika inspekcji](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Konfiguracja w ciągu pierwszych 30 dni

Aby użyć tej funkcji, włącz inspekcję, aby organizacja mogła rozpocząć rejestrowanie aktywności użytkowników i administratorów w organizacji. Po włączeniu tej opcji działanie zostanie zarejestrowane w dzienniku inspekcji i będzie dostępne do wyświetlenia w raporcie. Aby dowiedzieć się więcej, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>Krok 3. [Tworzenie zasad zgodności komunikacji](communication-compliance-policies.md)

[Tworzenie zasad zgodności komunikacji przy użyciu istniejących szablonów](communication-compliance-policies.md): 1 — nieodpowiednia zawartość; 2 — informacje poufne; 3 — Zgodność z przepisami; 4 — Konflikt interesów.

### <a name="step-4-investigate-and-remediate-alerts"></a>Krok 4. [Badanie i korygowanie alertów](communication-compliance-investigate-remediate.md)

[Zbadaj i skoryguj](communication-compliance-investigate-remediate.md) alerty zgodności komunikacji.

## <a name="compliance-manager"></a>Menedżer zgodności

**Łatwo zarządzaj zgodnością organizacji**:

Program Microsoft Purview Compliance Manager może pomóc w całej procesie zapewniania zgodności, od tworzenia spisu zagrożeń związanych z ochroną danych po zarządzanie złożonością wdrażania mechanizmów kontroli, aktualizowanie przepisów i certyfikatów oraz raportowanie do audytorów.

### <a name="step-1-get-to-know-compliance-manager"></a>Krok 1. [Zapoznanie się z Menedżerem zgodności](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Nasza strona przeglądu programu Compliance Manager jest najlepszym pierwszym przystankiem w celu kompleksowego przeglądu tego, czym jest Menedżer zgodności i jak działa. Możesz również przejść bezpośrednio do kluczowych sekcji naszej dokumentacji, korzystając z poniższych linków:

- [Omówienie oceny zgodności](compliance-manager.md#understanding-your-compliance-score)
- [Omówienie kluczowych elementów: kontrolek, ocen, szablonów i akcji poprawy](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [Omówienie pulpitu nawigacyjnego programu Compliance Manager](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [Filtrowanie widoku pulpitu nawigacyjnego](compliance-manager-setup.md#filtering-your-dashboard-view)
- [Dowiedz się więcej o akcjach ulepszania](compliance-manager-setup.md#improvement-actions-page)
- [Omówienie ocen](compliance-manager.md#assessments)
- [Wykonaj szybkie skanowanie środowiska przy użyciu Configuration Manager zgodności firmy Microsoft](compliance-manager-mcca.md)

![Menedżer zgodności — pulpit nawigacyjny.](../media/compliance-manager-dashboard.png "Pulpit nawigacyjny programu Compliance Manager")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>Krok 2. [Konfigurowanie Menedżera zgodności w celu zarządzania działaniami dotyczącymi zgodności](compliance-manager-assessments.md)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: inspekcja w ciągu pierwszych 30 dni

Rozpocznij pracę z ocenami i podejmij działania ulepszeń, aby zaimplementować mechanizmy kontroli i poprawić wskaźnik zgodności.

1. [Wybierz wstępnie utworzony szablon, aby utworzyć pierwszą ocenę i zarządzać nią](compliance-manager-assessments.md).
1. [Dowiedz się, jak używać szablonów do tworzenia ocen](compliance-manager-templates.md).
1. [Wykonaj prace nad implementacją i testowaniem akcji poprawy, aby ukończyć kontrole w ocenach](compliance-manager-improvement-actions.md).
1. [Lepiej zrozumieć, jak różne akcje wpływają na wynik zgodności](compliance-score-calculation.md).

> [!NOTE]
> Subskrypcja platformy Microsoft 365 lub Office 365 E1/E3 obejmuje szablon punktu odniesienia usługi Microsoft Data Protection. Microsoft 365 lub Office 365 E5, zgodność E5 zawiera szablony dla:
>
> - Punkt odniesienia usługi Microsoft Data Protection
> - RODO Unii Europejskiej  
> - ISO/IEC 27001,
> - NIST 800-53
>
> Menedżer zgodności zawiera ponad 300 szablonów regulacyjnych lub premium, które można kupić jako dodatek. Zobacz listę tutaj. W przypadku szablonów w warstwie Premium (dołączonych do subskrypcji lub zakupionych jako dodatek) otrzymasz uniwersalną wersję tych szablonów, umożliwiając zarządzanie zgodnością z dowolnym produktem lub usługą

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>Krok 3. [Skalowanie w górę: korzystanie z zaawansowanych funkcji w celu spełnienia niestandardowych potrzeb](compliance-manager-templates-create.md)

Niestandardowe oceny są przydatne w:

- Zarządzanie zgodnością dla produktów innych niż Microsoft 365, takich jak aplikacje i usługi innych firm, aplikacje lokalne i inne zasoby
- Zarządzanie własnymi niestandardowymi lub specyficznymi dla firmy kontrolami zgodności

1. [Rozszerzanie szablonu programu Compliance Manager przez dodawanie własnych kontrolek i akcji ulepszania](compliance-manager-templates-extend.md)
1. [Tworzenie własnego szablonu niestandardowego](compliance-manager-templates-create.md)
1. [Modyfikowanie istniejącego szablonu w celu dodawania lub usuwania kontrolek i akcji](compliance-manager-templates-modify.md)
1. [Konfigurowanie zautomatyzowanego testowania akcji poprawy](compliance-manager-setup.md#set-up-automated-testing)
1. [Ponowne przypisywanie akcji poprawy do innego użytkownika](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-lifecycle-management"></a>Zarządzanie cyklem życia danych

**Zarządzanie na dużą skalę za pomocą automatyzacji**:

Zwiększ możliwość dostosowywania się do zmian w organizacji za pomocą zakresów zasad, które są automatycznie aktualizowane. Automatyzowanie etykietowania zawartości w celu zmniejszenia nakładów pracy ręcznej i poprawy stanu zgodności.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>Krok 1. Dynamiczne określanie docelowych zasad przechowywania przy użyciu zakresów zasad adaptacyjnych

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Zakresy zasad adaptacyjnych umożliwiają dynamiczne kierowanie zasad do niektórych użytkowników, grup lub witryn na podstawie ich atrybutów usługi AD.  Atrybuty zakresów można wybrać z listy lub dostosować przy użyciu zaawansowanego konstruktora zapytań.

Zasady korzystające z zakresów zasad adaptacyjnych pozostają aktualne, gdy organizacja zmienia się wraz z dołączeniem lub odejściem nowych pracowników. Ponadto nie podlegają one poprzednim limitom 100/1000 lokalizacji uwzględnionych w zasadach.

- Tworzenie zakresu zasad adaptacyjnych i używanie go z zasadami przechowywania

### <a name="step-2-automate-labeling-to-apply-a-label-to-all-items-by-default"></a>Krok 2. Automatyzowanie etykietowania w celu domyślnego zastosowania etykiety do wszystkich elementów

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Konfiguracja w ciągu pierwszych 30 dni

Etykiety domyślne umożliwiają automatyczne stosowanie etykiety przechowywania do wszystkich elementów w określonej bibliotece, folderze lub dokumencie ustawionym w programie SharePoint.

- Publikowanie etykiety i stosowanie jej jako domyślnej w programie SharePoint

## <a name="data-loss-prevention"></a>Zapobieganie utracie danych

**Ochrona poufnych danych**:

Aby zapewnić zgodność ze standardami biznesowymi i przepisami branżowymi, organizacje muszą chronić poufne informacje, aby zapobiec ich nieumyślnemu ujawnieniu. Skonfiguruj zasady Ochrona przed utratą danych w Microsoft Purview, aby identyfikować, monitorować i automatycznie chronić poufne informacje na platformie Microsoft 365.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>Krok 1. [Ochrona utraty danych w lokalizacjach usługi Teams](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Jeśli Twoja organizacja ma profilaktykę utraty danych (DLP), możesz zdefiniować zasady, które uniemożliwiają użytkownikom udostępnianie poufnych informacji w kanale usługi Microsoft Teams lub sesji czatu.

1. Dowiedz się więcej na temat [licencjonowania DLP dla usługi Microsoft Teams i zakresu ochrony DLP](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)
1. [Dodawanie aplikacji Microsoft Teams jako lokalizacji do istniejących zasad DLP](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [Skonfiguruj nasze domyślne zasady DLP dla usługi Teams](mip-easy-trials.md) lub [zdefiniuj nowe zasady DLP dla usługi Microsoft Teams](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>Krok 2. [Ochrona utraty danych w lokalizacjach urządzeń](endpoint-dlp-getting-started.md)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Konfiguracja w ciągu pierwszych 30 dni

Program DLP punktu końcowego firmy Microsoft umożliwia monitorowanie urządzeń Windows 10 i wykrywanie, kiedy są używane i udostępniane poufne elementy.

1. Przygotowywanie punktów końcowych — upewnij się, że urządzenia z systemem Windows 10 i macOS, które planujesz wdrożyć w celu [spełnienia tych wymagań](endpoint-dlp-getting-started.md),
1. [Dołączanie urządzeń do zarządzania urządzeniami](endpoint-dlp-getting-started.md)  — należy włączyć monitorowanie i dołączanie punktów końcowych przed monitorowaniem i ochroną poufnych elementów na urządzeniu. Obie te akcje są wykonywane w portal zgodności Microsoft Purview.
   - Scenariusz 1 — [dołączanie urządzeń](endpoint-dlp-getting-started.md) , które nie zostały jeszcze dołączone.
   - Scenariusz 2 — [Ochrona punktu końcowego w usłudze Microsoft Defender jest już wdrożony i w programie są raporty punktów końcowych](endpoint-dlp-getting-started.md). Wszystkie te punkty końcowe zostaną wyświetlone na liście urządzeń zarządzanych.
1. [Skonfiguruj nasze domyślne zasady DLP dla urządzeń](mip-easy-trials.md#dlp-for-devices) lub [zdefiniuj nowe zasady DLP dla urządzeń](endpoint-dlp-learn-about.md).
1. [Wyświetl alerty DLP punktu końcowego na pulpicie](dlp-configure-view-alerts-policies.md) nawigacyjnym zarządzania alertami DLP.
1. [Wyświetlanie danych DLP punktu końcowego](data-classification-activity-explorer.md) w Eksploratorze działań.

### <a name="step-3-expand-policies-in-scope-or-protection"></a>Krok 3. [Rozwijanie zasad w zakresie lub ochronie](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

Możesz elastycznie konfigurować zasady DLP. Możesz zacząć od naszych domyślnych zasad DLP dla aplikacji Teams i urządzeń i rozszerzyć te zasady, aby chronić dodatkowe lokalizacje, typy informacji poufnych lub etykiety. Ponadto możesz rozwinąć akcje zasad i dostosować alerty.

1. Dodawanie lokalizacji
1. Dodawanie poufnych typów informacji lub etykiet w celu ochrony
1. Dodawanie akcji
   - Zespołów:
      - [Zapobieganie dostępowi zewnętrznemu do poufnych dokumentów](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [Uzyskiwanie wskazówek dotyczących zasad ułatwiających edukowanie użytkowników i instrukcje dotyczące dostosowywania wskazówek dotyczących zasad](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - Urządzenia: przełącz się tylko z inspekcji, aby zablokować
1. [Konfigurowanie i wyświetlanie alertów dotyczących zasad ochrony przed utratą danych — Microsoft Purview | Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>Zbierania elektronicznych materiałów dowodowych

**Dowiedz się więcej za pomocą kompleksowego przepływu pracy**:

Korzystaj z kompleksowego przepływu pracy w celu zachowania, zbierania, analizowania i eksportowania zawartości, która odpowiada na wewnętrzne i zewnętrzne badania organizacji. Zespoły prawne mogą również zarządzać całym procesem powiadamiania o blokadzie prawnej, komunikując się z opiekunami zaangażowanymi w sprawę.

### <a name="step-1-required-permissions"></a>Krok 1 (wymagany): [uprawnienia](https://aka.ms/ediscoveryninja)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Aby uzyskać dostęp do zbierania elektronicznych materiałów dowodowych (Premium) lub zostać dodanym jako członek sprawy zbierania elektronicznych materiałów dowodowych (Premium), użytkownik musi mieć przypisane odpowiednie uprawnienia.

1. [Konfigurowanie zbierania elektronicznych materiałów dowodowych (Premium) — przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [Dodaj członków do sprawy lub ich usuń](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>Krok 2 (wymagany): Tworzenie sprawy

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: tworzenie w ciągu pierwszych 30 dni

Więcej organizacji korzysta z rozwiązania eDiscovery (Premium) w usłudze Microsoft Purview na potrzeby krytycznych procesów zbierania elektronicznych materiałów dowodowych. Obejmuje to odpowiadanie na żądania regulacyjne, dochodzenia i spory sądowe.

1. Zarządzaniebierania elektronicznych materiałów dowodowych (Premium) — [dowiedz się, jak skonfigurować wykrywanie elektroniczne (Premium), zarządzać przypadkami, zarządzać przepływem pracy w środowisku zbierania elektronicznych materiałów dowodowych (Premium) i analizować wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych (Premium](/learn/modules/manage-advanced-ediscovery)).
1. [Tworzenie sprawy zbierania elektronicznych materiałów dowodowych przy użyciu nowego formatu sprawy advance eDiscovery](advanced-ediscovery-new-case-format.md)
1. [Zamknij lub usuń sprawę](close-or-delete-case.md) — po zakończeniu sprawy prawnej lub dochodzenia możesz zamknąć lub usunąć. Możesz również ponownie otworzyć zamkniętą sprawę.

### <a name="step-3-optional-settings"></a>Krok 3 (opcjonalnie): Ustawienia

Aby umożliwić osobom w organizacji rozpoczęcie tworzenia i używania przypadków, należy skonfigurować ustawienia globalne, które mają zastosowanie do wszystkich przypadków w organizacji. Obecnie jedynym ustawieniem globalnym jest **wykrywanie uprawnień klienta-adwokata** (więcej ustawień globalnych będzie dostępnych w przyszłości).

1. [Konfigurowanie zbierania elektronicznych materiałów dowodowych (Premium) — ustawienia globalne](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-ediscovery-premium)
1. [Konfiguruj ustawienia wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [Zarządzanie zadaniami w środowisku zbierania elektronicznych materiałów dowodowych (Premium)](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>Krok 4 (opcjonalnie): [Granice zgodności](set-up-compliance-boundaries.md)

Granice zgodności tworzą granice logiczne w organizacji kontrolujące lokalizacje zawartości użytkownika (takie jak skrzynki pocztowe, konta usługi OneDrive i witryny programu SharePoint), które mogą przeszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych. Kontrolują również, kto może uzyskiwać dostęp do spraw zbierania elektronicznych materiałów dowodowych używanych do zarządzania badaniami prawnymi, ludzkimi lub innymi badaniami w organizacji.

![Granice zgodności składają się z filtrów uprawnień wyszukiwania, które kontrolują dostęp do agencji i grup ról administratora, które kontrolują dostęp do przypadków zbierania elektronicznych materiałów dowodowych.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

Skonfiguruj granice zgodności dla badań zbierania elektronicznych materiałów dowodowych:

1. [Identyfikowanie atrybutu użytkownika do definiowania agencji](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [Tworzenie grupy ról dla każdej agencji](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [Tworzenie filtru uprawnień wyszukiwania w celu wymuszenia granicy zgodności](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [Tworzenie sprawy zbierania elektronicznych materiałów dowodowych dla dochodzenia wewnątrzagencyjnego](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>Krok 5 (opcjonalnie): [informacje o narzędziu do wyszukiwania zawartości](search-for-content.md)

Użyj narzędzia do wyszukiwania zawartości w portal zgodności Microsoft Purview, aby szybko znaleźć wiadomości e-mail w skrzynkach pocztowych programu Exchange, dokumentach w witrynach programu SharePoint i lokalizacjach usługi OneDrive oraz konwersacjach wiadomości błyskawicznych w Skype dla firm. Narzędzie do wyszukiwania zawartości umożliwia wyszukiwanie wiadomości e-mail, dokumentów i konwersacji wiadomości błyskawicznych w narzędziach do współpracy, takich jak Microsoft Teams i Grupy Microsoft 365.

- [Dowiedz się więcej o wyszukiwaniu zbierania elektronicznych materiałów dowodowych (Premium)](search-for-content.md#search-for-content)

## <a name="information-protection"></a>Information Protection

**Odnajdywanie, klasyfikowanie i ochrona poufnych informacji**:

Zaimplementuj etykiety Microsoft Purview Information Protection i poufności, aby ułatwić odnajdywanie, klasyfikowanie i ochronę poufnych treści wszędzie tam, gdzie się znajduje lub podróżuje.

### <a name="step-1-start-your-information-protection-trial"></a>Krok 1. [Rozpoczynanie wersji próbnej ochrony informacji](mip-easy-trials.md)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Uprawnieni klienci mogą aktywować domyślne etykiety i zasady dla Microsoft Purview Information Protection. Po włączeniu konfiguracji domyślnej w wersji próbnej skonfigurowanie wszystkich zasad dla dzierżawy potrwa około 2 minut, a wyświetlenie wyników tych domyślnych zasad może potrwać do 24 godzin.

Wybranie konfiguracji domyślnej przy użyciu 1 kliknięcia powoduje automatyczne skonfigurowanie następujących elementów:

- Etykiety poufności i zasady etykiet poufności
- Automatyczne etykietowanie po stronie klienta
- Automatyczne etykietowanie po stronie usługi
- Zasady ochrony przed utratą danych (DLP) dla aplikacji Teams i urządzeń

[Aktywuj domyślne etykiety i zasady](mip-easy-trials.md#activate-the-default-labels-and-policies). W razie potrzeby można edytować ręcznie po zakończeniu konfiguracji.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>Krok 2. [Automatyczne stosowanie etykiet poufności do dokumentów](apply-sensitivity-label-automatically.md)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Konfiguracja w ciągu pierwszych 30 dni

Podczas tworzenia etykiety poufności można automatycznie przypisywać tę etykietę do plików i wiadomości e-mail, gdy jest ona zgodna z określonymi warunkami.

1. [Tworzenie i konfigurowanie etykiet poufności](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [Publikowanie zasad etykiet poufności dla wszystkich użytkowników](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [Tworzenie zasad automatycznego etykietowania](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - Wybieranie informacji, do których ma zostać zastosowana etykieta
   - Definiowanie lokalizacji do zastosowania etykiety
   - Wybierz etykietę do zastosowania
   - [Uruchamianie zasad w trybie symulacji](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![Nowa konfiguracja zasad automatycznego etykietowania.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>Krok 3. [Przeglądanie i włączanie zasad automatycznego etykietowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

Teraz na stronie **Automatyczne etykietowanie** **ochrony** >  informacji zobaczysz zasady automatycznego **etykietowania w sekcji Symulacja**.

Wybierz zasady, aby wyświetlić szczegóły konfiguracji i stanu. Po zakończeniu symulacji wybierz kartę Elementy do przejrzenia, aby zobaczyć, które wiadomości e-mail lub dokumenty pasują do określonych reguł.

Gdy wszystko będzie gotowe do uruchomienia zasad bez symulacji, wybierz opcję **Włącz zasady** .

## <a name="insider-risk-management"></a>Zarządzanie ryzykiem wewnętrznym

**Wykrywanie i korygowanie ryzyka związanego z informacjami poufnymi**:

Korzystaj ze sztucznej inteligencji, aby ułatwić szybkie identyfikowanie, klasyfikowanie i korygowanie ryzyka wewnętrznego. Korzystając z dzienników z platformy Microsoft 365 i usług platformy Azure, można zdefiniować zasady, które monitorują sygnały o ryzyku wewnętrznym, a następnie podejmować działania korygujące, takie jak promowanie edukacji użytkowników lub inicjowanie badania.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Krok 1 (wymagane): [Włączanie uprawnień do zarządzania ryzykiem wewnętrznym](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Istnieją cztery grupy ról używane do konfigurowania uprawnień do zarządzania funkcjami zarządzania ryzykiem wewnętrznym.

[Dodaj użytkowników do grupy ról zarządzania ryzykiem wewnętrznym.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

Jeśli nie widzisz uprawnień, skontaktuj się z administratorem dzierżawy, aby przypisać odpowiednie role.

### <a name="step-2-start-with-user-quick-start-guide"></a>Krok 2. [Rozpoczynanie pracy z przewodnikiem Szybki start dla użytkowników](insider-risk-management-configure.md#recommended-actions-preview)

Szybko rozpocznij pracę i jak najlepiej wykorzystać możliwości zarządzania ryzykiem wewnętrznym za pomocą zalecanych akcji. Zalecane akcje zawarte na stronie Przegląd ułatwiają wykonanie kroków konfigurowania i wdrażania zasad oraz podejmowania akcji badania akcji użytkownika, które generują alerty na podstawie dopasowań zasad.

[Wybierz zalecenie z listy,](insider-risk-management-configure.md#recommended-actions-preview) aby rozpocząć konfigurowanie zarządzania ryzykiem wewnętrznym.

![Zalecane akcje dotyczące zarządzania ryzykiem wewnętrznym.](../media/insider-risk-recommended-actions.png)

Każda zalecana akcja przeprowadzi Cię przez wymagane działania dla zalecenia, w tym wszelkie wymagania, oczekiwane wymagania i wpływ konfigurowania funkcji w organizacji.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>Krok 3 (wymagane): [Włączanie dziennika inspekcji platformy Microsoft 365](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

Inspekcja jest domyślnie włączona dla organizacji platformy Microsoft 365. Niektóre organizacje mogły wyłączyć inspekcję z określonych powodów. Jeśli inspekcja jest wyłączona dla Twojej organizacji, może to być spowodowane tym, że inny administrator wyłączył tę inspekcję. Zalecamy potwierdzenie, że podczas wykonywania tego kroku można ponownie włączyć inspekcję.

Aby uzyskać instrukcje krok po kroku dotyczące włączania inspekcji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](turn-audit-log-search-on-or-off.md). Po włączeniu inspekcji zostanie wyświetlony komunikat informujący, że dziennik inspekcji jest przygotowywany i że wyszukiwanie można uruchomić w ciągu kilku godzin po zakończeniu przygotowywania. Tę akcję trzeba wykonać tylko raz. Aby uzyskać więcej informacji na temat korzystania z dziennika inspekcji platformy Microsoft 365, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>Krok 4 (wymagany): [Włączanie i wyświetlanie szczegółowych informacji dotyczących analizy ryzyka dla osób poufnych](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

Analiza zarządzania ryzykiem wewnętrznym umożliwia przeprowadzenie oceny potencjalnych zagrożeń wewnętrznych w organizacji bez konfigurowania żadnych zasad ryzyka wewnętrznego. Wyniki skanowania analizy mogą potrwać do 48 godzin, zanim szczegółowe informacje będą dostępne jako raporty do przeglądu. Aby dowiedzieć się więcej na temat szczegółowych informacji analitycznych, zobacz [Ustawienia zarządzania ryzykiem wewnętrznym: Analiza (wersja zapoznawcza)](insider-risk-management-settings.md) i zapoznaj się z [wideo Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) , aby ułatwić zrozumienie stanu ryzyka związanego z wewnętrznymi informacjami i pomóc w podjęciu działań przez skonfigurowanie odpowiednich zasad w celu zidentyfikowania ryzykownych użytkowników.

Aby włączyć analizę ryzyka wewnętrznego, musisz być członkiem Administracja Insider Risk Management lub Insider Risk Management. [Wykonaj te kroki, aby włączyć analizę ryzyka wewnętrznego](insider-risk-management-configure.md).

## <a name="records-management"></a>Zarządzanie rekordami

**Zarządzanie elementami o wysokiej wartości dla wymagań biznesowych, prawnych lub regulacyjnych dotyczących prowadzenia dokumentacji**:

Użyj funkcji Zarządzanie rekordami w Microsoft Purview, aby zautomatyzować harmonogram przechowywania dla rekordów prawnych, prawnych i krytycznych dla działania firmy. Wykorzystaj możliwości automatyzacji od utworzenia poprzez współpracę, aby zadeklarować rekordy, zachować zawartość i usunąć je na końcu.

### <a name="step-1-mark-contents-as-records"></a>Krok 1. Oznaczanie zawartości jako rekordów  

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Gdy zawartość jest zadeklarowana jako rekord, ograniczenia są nakładane na element pod względem tego, jakie akcje są dozwolone lub blokowane, dodatkowe działania dotyczące elementów są rejestrowane i masz dowód dyspozycji, jeśli elementy zostaną usunięte po zakończeniu okresu przechowywania.

- Tworzenie etykiety przechowywania, która deklaruje zawartość jako rekord lub rekord regulacyjny

### <a name="step-2-review-content-to-approve-before-its-permanently-deleted"></a>Krok 2. Przeglądanie zawartości do zatwierdzenia przed jej trwałym usunięciem

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Dzień 1

Po zakończeniu okresu przechowywania użytkownicy określeni ("recenzenci") mogą zostać powiadomieni o przejrzeniu zawartości i zatwierdzeniu trwałej akcji usuwania. Jest to obsługiwane, jeśli bardziej odpowiednia jest inna akcja niż usunięcie, na przykład przypisanie innego okresu przechowywania do zawartości lub wstrzymanie usuwania na potrzeby inspekcji.

- Tworzenie etykiety przechowywania używającej przeglądu dyspozycji

### <a name="step-3-apply-labels-automatically-to-content-that-matches-specific-conditions"></a>Krok 3. Automatyczne stosowanie etykiet do zawartości zgodnej z określonymi warunkami

> [!TIP]
> Najlepsze rozwiązanie dotyczące wersji próbnej: Konfiguracja w ciągu pierwszych 30 dni

Automatyczne stosowanie etykiet eliminuje konieczność ręcznego wykonywania działań związanych z etykietowaniem przez użytkowników. Etykiety przechowywania można stosować do zawartości automatycznie, gdy ta zawartość nie ma jeszcze zastosowanej etykiety przechowywania i zawiera informacje poufne, słowa kluczowe lub właściwości z możliwością wyszukiwania albo dopasowanie do klasyfikatorów klasyfikujących.

- Automatyczne stosowanie etykiet przechowywania do zawartości z określonymi typami informacji poufnych
- Automatyczne stosowanie etykiet przechowywania do zawartości przy użyciu klasyfikatorów z możliwością trenowania
- Automatyczne stosowanie etykiet przechowywania ze słowami kluczowymi lub właściwościami z możliwością wyszukiwania

## <a name="additional-trials-and-add-ons"></a>Dodatkowe wersje próbne i dodatki

### <a name="compliance-manager-premium-assessments"></a>Oceny premium programu Compliance Manager

**Ocena ryzyka i efektywne reagowanie**:

Pomóż swojej organizacji ocenić ryzyko i efektywnie reagować na kraje, wymagania regionalne i branżowe regulujące zbieranie i wykorzystywanie danych.

[Więcej informacji na temat wersji próbnej ocen premium programu Compliance Manager](compliance-easy-trials-compliance-manager-assessments.md).

[Podręcznik wersji próbnej: oceny premium programu Microsoft Purview Compliance Manager](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>zarządzanie ryzykiem prywatności Microsoft Priva i żądania praw podmiotów Microsoft Priva

**Identyfikowanie & zapobiegania zagrożeniom związanym z prywatnością**:

Proaktywne identyfikowanie i ochrona przed zagrożeniami prywatności, takimi jak gromadzenie danych, transfery danych i nadmierne dzielenie danych, oraz ułatwianie organizacji automatyzowania żądań podmiotów i zarządzania nimi na dużą skalę.

[Dowiedz się więcej o Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management).

[Podręcznik wersji próbnej: Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>Dodatkowe materiały

**Co zawiera**: Aby uzyskać pełną listę rozwiązań i funkcji usługi Microsoft Purview wymienionych w warstwie produktu, zobacz [Macierz funkcji](https://go.microsoft.com/fwlink/?linkid=2139145).

**Biblioteka zawartości technicznej zabezpieczeń firmy Microsoft**: zapoznaj się z tą biblioteką, aby znaleźć interaktywne przewodniki i inną zawartość szkoleniową odpowiadającą Twoim potrzebom. [Odwiedź stronę Biblioteka](/security).

**Zasoby zabezpieczeń firmy Microsoft**: od oprogramowania chroniącego przed złośliwym kodem po Zero Trust uzyskaj wszystkie odpowiednie zasoby dla potrzeb organizacji w zakresie zabezpieczeń.
