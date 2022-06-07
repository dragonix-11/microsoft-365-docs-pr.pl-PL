---
title: Szybkie zadania umożliwiające rozpoczęcie pracy ze zgodnością w usłudze Microsoft Purview
description: Dowiedz się więcej o zadaniach, które pomogą Ci szybko rozpocząć pracę ze zgodnością w usłudze Microsoft Purview.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
f1.keywords:
- NOCSH
ms.collection:
- m365-security-compliance
- m365initiative-compliance
ms.custom:
- admindeeplinkDEFENDER
- intro-get-started
ms.localizationpriority: medium
ms.openlocfilehash: cb8471ffea418ac47921777a0ee9594fa73fe4ac
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930224"
---
# <a name="quick-tasks-for-getting-started-with-compliance-in-microsoft-purview"></a>Szybkie zadania umożliwiające rozpoczęcie pracy ze zgodnością w usłudze Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Jeśli dopiero zaczynasz pracę w usłudze Microsoft Purview i zastanawiasz się, od czego zacząć, ten artykuł zawiera wskazówki dotyczące podstaw i priorytetyzuje ważne zadania związane z zgodnością. Ten artykuł pomoże Ci szybko rozpocząć pracę z zarządzaniem danymi i ich monitorowaniem, ochroną informacji oraz minimalizowaniem ryzyka związanego z wewnętrznymi informacjami.

Ten artykuł jest również przydatny, jeśli zastanawiasz się, jak najlepiej zarządzać ryzykiem, chronić dane i zachować zgodność z przepisami i standardami dotyczącymi nowo zdalnej siły roboczej. Pracownicy współpracują teraz ze sobą i łączą się ze sobą w nowy sposób, a ta zmiana oznacza, że istniejące procesy i mechanizmy kontroli zgodności mogą wymagać dostosowania. Identyfikowanie nowych zagrożeń związanych ze zgodnością i zarządzanie nimi w organizacji ma kluczowe znaczenie dla ochrony danych oraz minimalizowania zagrożeń i zagrożeń.

Po wykonaniu tych podstawowych zadań dotyczących zgodności rozważ rozszerzenie zakresu zgodności w organizacji, implementując dodatkowe rozwiązania usługi Microsoft Purview.

## <a name="task-1-configure-compliance-permissions"></a>Zadanie 1. Konfigurowanie uprawnień zgodności

Ważne jest, aby zarządzać tym, kto w organizacji ma dostęp do portalu zgodności usługi Microsoft Purview, aby wyświetlać zawartość i wykonywać zadania zarządzania. Platforma Microsoft 365 udostępnia role administracyjne specyficzne dla zgodności i korzystania z narzędzi dostępnych w portalu zgodności usługi Microsoft Purview.

Zacznij od przypisania uprawnień zgodności do osób w organizacji, aby mogły wykonywać te zadania i aby uniemożliwić nieautoryzowanym osobom dostęp do obszarów spoza ich obowiązków. Przed rozpoczęciem konfigurowania i implementowania rozwiązań zgodności dołączonych do platformy Microsoft 365 należy upewnić się, że przypisano odpowiednie osoby do **administratora danych zgodności** i **administratora zgodności** . Musisz również przypisać użytkowników do roli czytelnika globalnego usługi Azure Active Directory, aby wyświetlić dane w Menedżerze zgodności.

Aby uzyskać szczegółowe wskazówki dotyczące konfigurowania uprawnień i przypisywania osób do ról administratora, zobacz [Uprawnienia w Centrum zgodności & zabezpieczeń](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

## <a name="task-2-know-your-state-of-compliance"></a>Zadanie 2. Znajomość stanu zgodności

Trudno jest wiedzieć, gdzie iść, jeśli nie wiesz, gdzie jesteś. Spełnienie wymagań dotyczących zgodności obejmuje zrozumienie bieżącego poziomu ryzyka i tego, jakie aktualizacje mogą być potrzebne w tych stale zmieniających się czasach. Niezależnie od tego, czy Twoja organizacja jest nowa w zakresie wymagań dotyczących zgodności, czy ma głębokie doświadczenie w zakresie standardów i przepisów regulujących twoją branżę, najlepszą rzeczą, jaką możesz zrobić, aby poprawić zgodność, jest zrozumienie, na czym polega twoja organizacja.

[Menedżer zgodności usługi Microsoft Purview](/microsoft-365/compliance/compliance-manager) może pomóc zrozumieć stan zgodności organizacji i wyróżnić obszary, które mogą wymagać poprawy. Menedżer zgodności używa scentralizowanego pulpitu nawigacyjnego do obliczania oceny opartej na ryzyku, mierząc postęp w wykonywaniu akcji, które pomagają zmniejszyć ryzyko związane z ochroną danych i standardami regulacyjnymi. Możesz również użyć Menedżera zgodności jako narzędzia do śledzenia wszystkich ocen ryzyka. Zapewnia możliwości przepływu pracy, które ułatwiają efektywne wykonywanie ocen ryzyka za pomocą wspólnego narzędzia.

Aby uzyskać szczegółowe wskazówki dotyczące rozpoczynania pracy z Menedżerem zgodności, zobacz [Wprowadzenie do Menedżera zgodności](/microsoft-365/compliance/compliance-manager-setup).

> [!IMPORTANT]
> Zabezpieczenia i zgodność są ściśle zintegrowane w większości organizacji. Ważne jest, aby twoja organizacja zajmuje się podstawowymi obszarami zabezpieczeń, ochrony przed zagrożeniami oraz zarządzania tożsamościami i dostępem, aby ułatwić zapewnienie dogłębnego podejścia do zabezpieczeń i zgodności.
>
> Sprawdź wskaźnik [bezpieczeństwa platformy Microsoft 365](/microsoft-365/security/defender/microsoft-secure-score) w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu usługi Microsoft 365 Defender</a> i wykonaj zadania opisane w następujących artykułach:
>
> - [Plan bezpieczeństwa — najważniejsze priorytety dla pierwszych 30 dni, 90 dni i nie tylko](/microsoft-365/security/office-365-security/security-roadmap)
> - [12 najważniejszych zadań dla zespołów zabezpieczeń do obsługi pracy z domu](/microsoft-365/security/top-security-tasks-for-remote-work)

## <a name="task-3-enable-auditing-for-your-organization"></a>Zadanie 3. Włączanie inspekcji dla organizacji

Po określeniu bieżącego stanu organizacji i możliwości zarządzania funkcjami zgodności następnym krokiem jest upewnienie się, że masz dane do przeprowadzania badań zgodności i generowania raportów dotyczących działań sieciowych i użytkowników w organizacji. Włączenie inspekcji jest również ważnym wymaganiem wstępnym dla rozwiązań zgodności opisanych w dalszej części tego artykułu.

Szczegółowe informacje udostępniane przez dziennik inspekcji są cennym narzędziem, które pomaga dopasować wymagania dotyczące zgodności do rozwiązań, które ułatwiają zarządzanie obszarami zgodności i monitorowanie ich wymagających ulepszeń. Rejestrowanie inspekcji musi być włączone przed zarejestrowaniem działań i przed przeszukaniem dziennika inspekcji. Po włączeniu działania użytkownika i administratora w organizacji są rejestrowane w dzienniku inspekcji i przechowywane przez 90 dni i do jednego roku w zależności od licencji przypisanej do użytkowników.

Aby uzyskać instrukcje krok po kroku dotyczące włączania inspekcji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](/microsoft-365/compliance/turn-audit-log-search-on-or-off).

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>Zadanie 4. Tworzenie zasad w celu powiadamiania o potencjalnych problemach ze zgodnością

Firma Microsoft udostępnia kilka wbudowanych zasad alertów, które ułatwiają identyfikowanie zagrożeń związanych z uprawnieniami administratora, działaniami złośliwego oprogramowania, potencjalnymi zagrożeniami zewnętrznymi i wewnętrznymi oraz zagrożeniami związanymi z zarządzaniem cyklem życia danych. Te zasady są domyślnie włączone, ale może być konieczne skonfigurowanie alertów niestandardowych, aby ułatwić zarządzanie wymaganiami dotyczącymi zgodności specyficznymi dla organizacji.

Użyj zasad alertów i narzędzi pulpitu nawigacyjnego alertów, aby utworzyć niestandardowe zasady alertów i wyświetlić alerty wygenerowane, gdy użytkownicy wykonują działania zgodne z warunkami zasad. Przykładem może być użycie zasad alertów do śledzenia działań użytkowników i administratorów wpływających na wymagania dotyczące zgodności, uprawnienia i zdarzenia utraty danych w organizacji.

Aby uzyskać szczegółowe wskazówki dotyczące tworzenia niestandardowych zasad alertów, zobacz [Zasady alertów w centrum zabezpieczeń i zgodności](/microsoft-365/compliance/alert-policies).

## <a name="task-5-classify-and-protect-sensitive-data"></a>Zadanie 5. Klasyfikowanie i ochrona poufnych danych

Aby wykonać swoją pracę, osoby w organizacji współpracują z innymi osobami zarówno w organizacji, jak i poza nią. Oznacza to, że zawartość nie pozostaje już za zaporą — może poruszać się wszędzie, na urządzeniach, w aplikacjach i usługach. A gdy będzie się poruszać, chcesz, aby odbywało się to w bezpieczny, chroniony sposób, który spełnia zasady biznesowe i zgodności organizacji.

[Etykiety poufności](/microsoft-365/compliance/sensitivity-labels) umożliwiają klasyfikowanie i ochronę danych organizacji, jednocześnie upewniając się, że produktywność użytkowników i możliwość współpracy nie są utrudnione. Używanie etykiet poufności do wymuszania ograniczeń szyfrowania i użycia stosuje oznaczenia wizualne oraz chroni informacje na różnych platformach i urządzeniach, lokalnie i w chmurze.

Aby uzyskać szczegółowe wskazówki dotyczące konfigurowania i używania etykiet poufności, zobacz Wprowadzenie do [etykiet poufności](/microsoft-365/compliance/get-started-with-sensitivity-labels).

## <a name="task-6-configure-retention-policies"></a>Zadanie 6. Konfigurowanie zasad przechowywania

[Zasady przechowywania](/microsoft-365/compliance/retention) pozwalają proaktywnie decydować, czy zachować zawartość, usunąć zawartość, czy obie te wartości — zachować, a następnie usunąć zawartość na końcu określonego okresu przechowywania. Te działania mogą być konieczne w celu zachowania zgodności z przepisami branżowymi i zasadami wewnętrznymi oraz zmniejszenia ryzyka w przypadku sporów sądowych lub naruszenia bezpieczeństwa.

Jeśli zawartość podlega zasadom przechowywania, użytkownicy mogą nadal edytować zawartość i pracować z nią tak, jakby nic się nie zmieniło. Zawartość jest przechowywana w miejscu, w oryginalnej lokalizacji. Jeśli jednak ktoś edytuje lub usunie zawartość podlegającą zasadom przechowywania, kopia oryginalnej zawartości zostanie zapisana w bezpiecznej lokalizacji, w której jest przechowywana, gdy obowiązują zasady przechowywania tej zawartości.

Zasady przechowywania można szybko wprowadzić dla wielu usług w środowisku platformy Microsoft 365, które obejmują wiadomości usługi Teams i Yammer, pocztę programu Exchange, witryny programu SharePoint i konta usługi OneDrive. Nie ma żadnych ograniczeń dotyczących liczby użytkowników, skrzynek pocztowych lub witryn, które zasady przechowywania mogą być automatycznie uwzględniane. Jeśli jednak chcesz uzyskać bardziej selektywne dane, możesz to zrobić, konfigurując zakres adaptacyjny oparty na zapytaniach w celu dynamicznego określania konkretnych wystąpień lub zakres statyczny, który określa określone wystąpienia, które mają być zawsze uwzględniane lub zawsze wykluczane.

Aby uzyskać szczegółowe wskazówki dotyczące konfigurowania zasad przechowywania, zobacz [Tworzenie i konfigurowanie zasad przechowywania](/microsoft-365/compliance/create-retention-policies). Ponieważ zasady przechowywania stanowią podstawę strategii zarządzania cyklem życia danych dla aplikacji i usług platformy Microsoft 365, zobacz również [Wprowadzenie do zarządzania cyklem życia danych](/microsoft-365/compliance/get-started-with-data-lifecycle-management).

## <a name="task-7-configure-sensitive-information-and-inappropriate-language-policies"></a>Zadanie 7. Konfigurowanie informacji poufnych i nieodpowiednich zasad języka

Ochrona poufnych informacji oraz wykrywanie i działanie w przypadku przypadków molestowania w miejscu pracy jest ważnym elementem zgodności z wewnętrznymi zasadami i standardami. [Zgodność komunikacji](/microsoft-365/compliance/communication-compliance) w usłudze Microsoft Purview pomaga zminimalizować te zagrożenia, pomagając szybko wykrywać, przechwytywać i podejmować działania korygowania dotyczące poczty e-mail i komunikacji w usłudze Microsoft Teams. Obejmują one niewłaściwą komunikację zawierającą wulgaryzmy, groźby oraz nękanie i komunikację, które udostępniają poufne informacje wewnątrz organizacji i poza nią.

Wstępnie zdefiniowany szablon zasad *Wykrywanie nieodpowiedniego tekstu* umożliwia skanowanie komunikacji wewnętrznej i zewnętrznej pod kątem dopasowań zasad, aby można było je zbadać przez wyznaczonych recenzentów. Recenzenci mogą badać zeskanowaną pocztę e-mail, usługę Microsoft Teams, usługę Yammer lub komunikację innych firm w organizacji i podejmować odpowiednie działania korygujące, aby upewnić się, że są one zgodne ze standardami organizacji.

Wstępnie zdefiniowany szablon zasad *wykrywania informacji poufnych* pomaga szybko utworzyć zasady skanowania wiadomości e-mail i komunikacji w usłudze Microsoft Teams zawierające zdefiniowane typy informacji poufnych lub słowa kluczowe, aby upewnić się, że ważne dane nie są udostępniane osobom, które nie powinny mieć dostępu. Działania te mogą obejmować nieautoryzowaną komunikację na temat poufnych projektów lub specyficznych dla branży przepisów dotyczących wykorzystywania informacji poufnych lub innych działań związanych z zmową.

Aby uzyskać szczegółowe wskazówki dotyczące planowania i konfigurowania zgodności z komunikacją, zobacz [Planowanie zgodności z komunikacją](/microsoft-365/compliance/communication-compliance-plan) i [Wprowadzenie do zgodności z komunikacją](/microsoft-365/compliance/communication-compliance-configure). Aby uzyskać informacje o licencjonowaniu zgodności komunikacji, zobacz [Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

## <a name="task-8-see-whats-happening-with-your-sensitive-items"></a>Zadanie 8. Zobacz, co się dzieje z poufnymi elementami

Etykiety poufności, poufne typy informacji, etykiety przechowywania i zasady oraz klasyfikatory z możliwością trenowania mogą służyć do klasyfikowania i etykietowania poufnych elementów w programach Exchange, SharePoint i OneDrive, jak pokazano w poprzednich zadaniach. Ostatnim krokiem w szybkiej podróży po zadaniu jest sprawdzenie, które elementy zostały oznaczone etykietą i jakie akcje użytkownicy podejmują w przypadku tych poufnych elementów. [Eksplorator zawartości](/microsoft-365/compliance/data-classification-content-explorer) i [eksplorator działań](/microsoft-365/compliance/data-classification-activity-explorer) zapewniają ten wgląd.

### <a name="content-explorer"></a>Eksplorator zawartości

Eksplorator zawartości umożliwia wyświetlanie w ich formacie natywnym wszystkich elementów, które zostały sklasyfikowane jako typ informacji poufnych lub należących do określonej klasyfikacji przez klasyfikator trenowalny, oraz wszystkich elementów, które mają zastosowaną etykietę poufności lub przechowywania.

Aby uzyskać szczegółowe wskazówki dotyczące korzystania z Eksploratora zawartości, zobacz [Know your data - data classification overview (Poznanie danych — omówienie klasyfikacji danych](/microsoft-365/compliance/data-classification-overview)) i [Get started with content explorer (Rozpoczynanie pracy z Eksploratorem zawartości](/microsoft-365/compliance/data-classification-content-explorer)).

### <a name="activity-explorer"></a>Eksplorator działań

Eksplorator działań ułatwia monitorowanie czynności wykonywanych za pomocą elementów poufnych sklasyfikowanych i oznaczonych etykietami:

- SharePoint
- Exchange
- OneDrive

Dostępnych jest ponad 30 różnych filtrów, niektóre z nich to:

- zakres dat
- typ działania
- Lokalizacji
- Użytkownika
- etykieta poufności
- etykieta przechowywania
- ścieżka pliku
- Zasady DLP

Aby uzyskać szczegółowe wskazówki dotyczące korzystania z Eksploratora działań, zobacz [Wprowadzenie do Eksploratora działań](/microsoft-365/compliance/data-classification-activity-explorer).

## <a name="next-steps"></a>Następne kroki

Teraz, po skonfigurowaniu podstaw zarządzania zgodnością dla organizacji, rozważ następujące rozwiązania zgodności w usłudze Microsoft Purview, aby ułatwić ochronę poufnych informacji oraz wykrywanie dodatkowych zagrożeń wewnętrznych i reagowanie na nie.

### <a name="configure-retention-labels"></a>Konfigurowanie etykiet przechowywania

Zasady przechowywania są automatycznie stosowane do wszystkich elementów na poziomie kontenera (takich jak witryny programu SharePoint, skrzynki pocztowe użytkowników itd.), [etykiety przechowywania](/microsoft-365/compliance/retention#retention-labels) mają zastosowanie do poszczególnych elementów, takich jak dokument programu SharePoint lub wiadomość e-mail. Te etykiety można zastosować ręcznie lub automatycznie.

Etykiety przechowywania mogą być używane jako część strategii utrzymania ładu danych, aby zachować to, czego potrzebujesz, i usunąć to, czego nie potrzebujesz. Użyj tych etykiet, gdy potrzebujesz wyjątków od zasad przechowywania, gdy określone dokumenty lub wiadomości e-mail wymagają różnych ustawień przechowywania lub usuwania. Na przykład zasady programu SharePoint przechowują wszystkie dokumenty przez trzy lata, ale określone dokumenty biznesowe muszą być przechowywane przez pięć lat. Aby uzyskać więcej informacji, zobacz [Tworzenie etykiet przechowywania dla wyjątków od zasad przechowywania](/microsoft-365/compliance/create-retention-labels-data-lifecycle-management).

Jednak etykiety przechowywania używane w [przypadku zarządzania rekordami](/microsoft-365/compliance/records-management) udostępniają o wiele więcej opcji zarządzania do obsługi dokumentów i wiadomości e-mail na poziomie elementu. Ten poziom zarządzania danymi jest odpowiedni dla elementów o wysokiej wartości dla wymagań dotyczących prowadzenia rejestrów biznesowych, prawnych lub regulacyjnych. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do zarządzania rekordami](/microsoft-365/compliance/get-started-with-records-management).

### <a name="identify-and-define-sensitive-information-types"></a>Identyfikowanie i definiowanie typów informacji poufnych

Definiowanie typów informacji poufnych na podstawie wzorca zawartego w informacjach w danych organizacji. [Wbudowane typy informacji poufnych](./sensitive-information-type-entity-definitions.md) pomagają identyfikować i chronić numery kart kredytowych, numery kont bankowych, numery paszportów i inne. Możesz też utworzyć własne [niestandardowe typy informacji o poufności](/microsoft-365/compliance/create-a-custom-sensitive-information-type) specyficzne dla twojej organizacji.

Aby uzyskać szczegółowe wskazówki dotyczące definiowania niestandardowych typów informacji poufnych, zobacz [Create a custom sensitive information type in the Security & Compliance Center (Tworzenie niestandardowego typu informacji poufnych w Centrum zgodności & zabezpieczeń](./create-a-custom-sensitive-information-type.md)).

### <a name="prevent-data-loss"></a>Zapobieganie utracie danych

[Zasady ochrony przed utratą danych (DLP) w usłudze Microsoft Purview](/microsoft-365/compliance/dlp-learn-about-dlp) umożliwiają identyfikowanie, monitorowanie i automatyczne ochronę poufnych informacji w organizacji platformy Microsoft 365. Użyj zasad DLP, aby identyfikować poufne elementy w usługach firmy Microsoft, zapobiegać przypadkowemu udostępnianiu poufnych elementów i pomagać użytkownikom dowiedzieć się, jak zachować zgodność bez przerywania przepływu pracy.

Aby uzyskać szczegółowe wskazówki dotyczące konfigurowania zasad DLP, [utwórz, przetestuj i dostosuj zasady DLP](/microsoft-365/compliance/create-test-tune-dlp-policy). Aby uzyskać informacje o licencjonowaniu zarządzania utratą danych, zobacz [Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="detect-and-act-on-insider-risks"></a>Wykrywanie zagrożeń wewnętrznych i reagowanie na nie

Coraz więcej pracowników ma coraz większy dostęp do tworzenia i udostępniania danych oraz zarządzania nimi na wielu platformach i usługach. W większości przypadków organizacje mają ograniczone zasoby i narzędzia do identyfikowania i ograniczania ryzyka w całej organizacji, jednocześnie spełniając wymagania dotyczące zgodności i standardy prywatności pracowników. Te zagrożenia mogą obejmować kradzież danych przez odchodzących pracowników i wycieki danych informacji spoza organizacji przez przypadkowe nadmierne dzielenie lub złośliwe zamiary.

[Zarządzanie ryzykiem wewnętrznym](/microsoft-365/compliance/insider-risk-management-policies) korzysta z pełnego zakresu wskaźników usług i innych firm, aby ułatwić szybkie identyfikowanie, klasyfikowanie i działanie na ryzykownych działaniach użytkowników. Dzięki użyciu dzienników z platformy Microsoft 365 i programu Microsoft Graph zarządzanie ryzykiem wewnętrznym umożliwia definiowanie określonych zasad w celu identyfikowania wskaźników ryzyka i podejmowania działań w celu ograniczenia tych zagrożeń.

Aby uzyskać szczegółowe wskazówki dotyczące planowania i konfigurowania zasad zarządzania ryzykiem wewnętrznym, zobacz [Planowanie zarządzania ryzykiem wewnętrznym](/microsoft-365/compliance/insider-risk-management-plan) i [Wprowadzenie do zarządzania ryzykiem wewnętrznym](/microsoft-365/compliance/insider-risk-management-configure). Aby uzyskać informacje o licencjonowaniu zarządzania ryzykiem wewnętrznym, zobacz [Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management).
