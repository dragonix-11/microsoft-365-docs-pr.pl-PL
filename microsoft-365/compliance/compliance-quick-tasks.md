---
title: Szybkie zadania dotyczące rozpoczynania pracy z Microsoft 365 zgodnością
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365-security-compliance
- m365initiative-compliance
ms.custom:
- admindeeplinkDEFENDER
- intro-get-started
ms.localizationpriority: medium
description: Dowiedz się więcej o zadaniach, które ułatwiają szybkie rozpoczynanie pracy ze zgodnością w Microsoft 365.
ms.openlocfilehash: 1fb1a94e41550e10288bc42b3900cb10e76362bc
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010625"
---
# <a name="quick-tasks-for-getting-started-with-microsoft-365-compliance"></a>Szybkie zadania dotyczące rozpoczynania pracy z Microsoft 365 zgodnością

Jeśli nie masz pomysłu Microsoft 365 zgodności z przepisami i zastanawiasz się, od czego zacząć, ten artykuł zawiera wskazówki dotyczące podstaw i priorytetów ważnych zadań związanych ze zgodnością. Ten artykuł pomoże Ci szybko rozpocząć zarządzanie danymi i monitorowanie ich, ochronę informacji i zminimalizowanie ryzyka w niejawnym programie testów.

Ten artykuł jest również przydatny, jeśli wiesz, jak najlepiej zarządzać ryzykiem, chronić dane i zachować zgodność z przepisami i standardami u nowo zatrudnionych zdalnie. Pracownicy współpracują i kontaktują się ze sobą na nowe sposoby, co oznacza, że istniejące procesy i mechanizmy kontroli zgodności mogą wymagać dostosowania istniejących procesów i kontroli zgodności. Identyfikowanie tych nowych zagrożeń związanych ze zgodnością i zarządzanie nimi w organizacji ma kluczowe znaczenie dla zabezpieczania danych i minimalizowania zagrożeń i zagrożeń.

Po ukończeniu tych podstawowych zadań dotyczących zgodności rozważ rozszerzenie zakresu zgodności w organizacji, implementując dodatkowe rozwiązania Microsoft 365 zgodności.

## <a name="task-1-configure-compliance-permissions"></a>Zadanie 1. Konfigurowanie uprawnień dotyczących zgodności

Ważne jest zarządzanie tym, kto w organizacji ma dostęp do witryny, Centrum zgodności platformy Microsoft 365 wyświetlać zawartość i wykonywać zadania zarządzania. Microsoft 365 zapewnia role administracyjne specyficzne dla zgodności i korzystania z narzędzi zawartych w Centrum zgodności platformy Microsoft 365.

Zacznij od przypisania uprawnień do zgodności osobom w organizacji, aby one mogą wykonywać te zadania i aby uniemożliwić nieautoryzowanym osobom dostęp do obszarów spoza zakresu obowiązków. Przed rozpoczęciem konfigurowania i wdrażania rozwiązań zgodności dołączonych do programu Microsoft 365 należy upewnić się,  że odpowiednie osoby zostały przypisane  do administratora danych zgodności i ról administratora Microsoft 365. Musisz również przypisać użytkowników do roli globalnego Azure Active Directory, aby wyświetlać dane w Menedżerze zgodności.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania uprawnień i przypisywania osób do ról administratora, zobacz Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

## <a name="task-2-know-your-state-of-compliance"></a>Zadanie 2. Poznaw swój stan zgodności

Trudno jest wiedzieć, gdzie się udać, jeśli nie wiesz, gdzie się znajdujesz. Spełnienie Wymagań dotyczących zgodności obejmuje zrozumienie bieżącego poziomu ryzyka i tego, jakie aktualizacje mogą być potrzebne w tych zmieniających się czasach. Niezależnie od tego, czy Twoja organizacja nie jest nowym użytkownikiem wymagań dotyczących zgodności z przepisami, czy ma doświadczenie w standardach i regulacjach, które określają branżę, najlepszą rzeczą, jaką możesz zrobić, aby poprawić zgodność z przepisami, jest zrozumienie, gdzie znajduje się Twoja organizacja.

[Menedżer zgodności firmy Microsoft](compliance-manager.md) może pomóc Ci w zrozumieniu stanu zgodności Twojej organizacji i wyróżnienia obszarów, które mogą wymagać poprawy. Menedżer zgodności używa scentralizowanego pulpitu nawigacyjnego do obliczania wyników opartych na czynnikach ryzyka, pomiaru postępu w realizacji działań, które ułatwiają zmniejszenie ryzyka związanego z ochroną danych i standardami regulacyjną. Menedżera zgodności można także użyć jako narzędzia do śledzenia wszystkich ocen ryzyka. Udostępnia on funkcje przepływów pracy, które ułatwiają wydajne przeprowadzanie oceny ryzyka za pomocą wspólnego narzędzia.

Aby uzyskać szczegółowe instrukcje dotyczące rozpoczynania pracy z Menedżerem zgodności, zobacz [Wprowadzenie do Menedżera zgodności](compliance-manager-setup.md).

> [!IMPORTANT]
> Zabezpieczenia i zgodność z przepisami są ściśle zintegrowane dla większości organizacji. Ważne jest, aby Twoja organizacja uwzględniała podstawowe obszary zabezpieczeń, ochrony przed zagrożeniami, tożsamości i zarządzania dostępem, aby zapewnić szczegółową obronę zarówno w zakresie zabezpieczeń, jak i zgodności.
>
> Sprawdź swój [Microsoft 365 bezpieczeństwa](../security/defender/microsoft-secure-score.md) w portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> wykonanie zadań opisanych w następujących artykułach:
>
> - [Plan zabezpieczeń — najważniejsze priorytety pierwszych 30 dni, 90 dni i później](../security/office-365-security/security-roadmap.md)
> - [12 najlepszych zadań dla zespołów ds. zabezpieczeń na rzecz obsługi pracy z domu](../security/top-security-tasks-for-remote-work.md)

## <a name="task-3-enable-auditing-for-your-organization"></a>Zadanie 3. Włączanie inspekcji dla organizacji

Teraz, gdy ustalisz bieżący stan organizacji i kto może zarządzać funkcjami zgodności, następnym krokiem jest upewninie się, że masz dane do przeprowadzenia badania zgodności i wygenerowania raportów dotyczących aktywności sieci i użytkowników w organizacji. Włączenie inspekcji jest również ważnym wymaganiem wstępnym dla rozwiązań zgodności ważnych dla zgodności ważnych w dalszej części tego artykułu.

Szczegółowe informacje zapewniane przez dziennik inspekcji to cenne narzędzie pomagające dopasować Wymagania dotyczące zgodności do rozwiązań ułatwiających zarządzanie obszarami zgodności i monitorowanie ich, które wymagają doskonalenia. Rejestrowanie inspekcji musi być włączone, zanim zostaną zarejestrowane działania i będzie można przeszukiwać dziennik inspekcji. Po włączeniu działania użytkowników i administratorów z Twojej organizacji są rejestrowane w dzienniku inspekcji i przechowywane przez 90 dni, a do jednego roku w zależności od licencji przypisanej do użytkowników.

Aby uzyskać instrukcje krok po kroku dotyczące dotyczące włączanie inspekcji, zobacz Włączanie lub wyłączanie przeszukiwania [dziennika inspekcji](turn-audit-log-search-on-or-off.md).

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>Zadanie 4. Tworzenie zasad w celu powiadamiania Cię o potencjalnych problemach ze zgodnością

Firma Microsoft udostępnia kilka wbudowanych zasad alertów, które ułatwiają identyfikowanie nadużyć dotyczących uprawnień administratora, działań złośliwego oprogramowania, potencjalnych zagrożeń zewnętrznych i wewnętrznych oraz zagrożeń związanych z zarządzaniem informacjami. Te zasady są domyślnie włączone, ale może być konieczne skonfigurowanie alertów niestandardowych w celu zarządzania wymaganiami zgodności specyficznymi dla Organizacji.

Za pomocą zasad alertów i narzędzi pulpitu nawigacyjnego alertów można tworzyć niestandardowe zasady alertów i wyświetlać alerty generowane, gdy użytkownicy wykonują działania zgodne z warunkami zasad. Niektóre przykłady mogą dotyczyć śledzenia działań użytkowników i administratorów dotyczących zgodności z przepisami, uprawnień i zdarzeń dotyczących utraty danych w organizacji za pomocą zasad alertów.

Aby uzyskać szczegółowe instrukcje dotyczące tworzenia niestandardowych zasad alertów, zobacz [Alerty dotyczące zasad w Centrum zabezpieczeń i zgodności](alert-policies.md).

## <a name="task-5-classify-and-protect-sensitive-data"></a>Zadanie 5. Klasyfikowanie i ochrona danych poufnych

Aby wykonać pracę, osoby w Twojej organizacji współpracują z innymi osobami z organizacji i spoza tej organizacji. Oznacza to, że zawartość nie pozostaje już za zaporą — może być przesyłana wszędzie, na różnych urządzeniach, w aplikacjach i usługach. W celu zapewnienia bezpieczeństwa i ochrony w sposób zgodny z zasadami firmy i zgodnością organizacja może się w ten sposób dzieje.

[Etykiety](sensitivity-labels.md) wrażliwości pozwalają klasyfikować i chronić dane organizacji, a jednocześnie zapewnić, że produktywność użytkowników i ich współpraca nie są utrudnione. Użyj etykiet wrażliwości, aby wymusić szyfrowanie i ograniczenia dotyczące użycia, aby zastosować oznaczenia wizualne i chronić informacje na różnych platformach i urządzeniach, lokalnie i w chmurze.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania i używania etykiet wrażliwości, zobacz Wprowadzenie [do etykiet wrażliwości](get-started-with-sensitivity-labels.md).

## <a name="task-6-configure-retention-policies"></a>Zadanie 6. Konfigurowanie zasad przechowywania

Zasady [przechowywania](retention.md) pozwalają aktywnie zdecydować, czy zachować zawartość, usunąć zawartość, czy obie te wartości — zachować, a następnie usunąć tę zawartość na koniec określonego okresu przechowywania. Te działania mogą być potrzebne w celu zachowania zgodności z przepisami branżowymi i zasadami wewnętrznymi, a także zmniejszenia ryzyka w przypadku sporu sądowego lub naruszenia zabezpieczeń.

Gdy zawartość podlega zasadom przechowywania, inne osoby będą nadal mogą ją edytować i pracować nad zawartością tak, jakby nic się nie zmieniło. Zawartość jest zachowywana w miejscu, w jego pierwotnej lokalizacji. Jeśli jednak ktoś edytuje lub usuwa zawartość podlega zasadom przechowywania, kopia oryginalnej zawartości jest zapisywana w bezpiecznym miejscu, w którym jest zachowywana, podczas gdy zasady przechowywania dla tej zawartości są obowiązywać.

W środowisku usługi Microsoft 365 można szybko utworzyć zasady przechowywania dla wielu usług, takich jak wiadomości Teams i Yammer, poczta Exchange, witryny SharePoint i konta OneDrive firm. Nie ma żadnych ograniczeń liczby użytkowników, skrzynek pocztowych lub witryn, które mogą automatycznie uwzględniać zasady przechowywania. Jeśli jednak chcesz uzyskać bardziej selektywny dostęp, możesz to zrobić, konfigurując adaptacyjny zakres oparty na kwerendach w celu dynamicznego kierowania określonych wystąpień lub statyczny zakres określający określone wystąpienia, które mają być zawsze dołączane lub wykluczane.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad przechowywania, zobacz [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md). Ponieważ zasady przechowywania stanowią podstawowy element strategii zarządzania informacjami Microsoft 365, zobacz Wprowadzenie [do zarządzania informacjami](get-started-with-information-governance.md).

## <a name="task-7-configure-sensitive-information-and-offensive-language-policies"></a>Zadanie 7. Konfigurowanie informacji poufnych i obraźliwych zasad dotyczących języka

Ochrona informacji poufnych oraz wykrywanie incydentów nękania w miejscu pracy i działanie na nich to istotny element zgodności z wewnętrznymi zasadami i standardami. [Zgodność komunikacji w](communication-compliance.md) programie Microsoft 365 pozwala zminimalizować te zagrożenia, pomagając szybko wykrywać, przechwytywać i podjąć działania naprawcze dotyczące poczty e-mail Microsoft Teams komunikacji. Należą do nich nieodpowiednia komunikacja zawierająca wulgarne, zagrożenia, molestowanie i komunikacja, w których są przekazywane poufne informacje w organizacji i poza nią.

Wstępnie zdefiniowany szablon zasad *Obraźliwy* język i zasady ochrony przed molestowaniem umożliwia skanowanie komunikacji wewnętrznej i zewnętrznej w poszukiwaniu dopasowania zasad w celu sprawdzenia ich przez wyznaczonych recenzentów. Recenzentzy mogą badać zeskanowane wiadomości e-mail, wiadomości e-Microsoft Teams, Yammer lub inne firmy w organizacji i podjąć odpowiednie działania naprawcze, aby upewnić się, że są one zgodne ze standardami Twojej organizacji.

Wstępnie zdefiniowany szablon zasad  dotyczących informacji poufnych ułatwia szybkie tworzenie zasad do skanowania wiadomości e-mail i komunikacji programu Microsoft Teams zawierającej zdefiniowane typy informacji poufnych lub słowa kluczowe w celu upewnień się, że ważne dane nie są udostępniane osobom, które nie powinny mieć do nich dostępu. Działania te mogą obejmować nieautoryzowaną komunikację na temat poufnych projektów lub reguł branżowych dotyczących notowania niejawnego programu testów lub innych działań z zakresu współpracy.

Aby uzyskać szczegółowe instrukcje dotyczące planowania i konfigurowania zgodności komunikacji, zobacz [Planowanie](communication-compliance-plan.md) zgodności komunikacji i Wprowadzenie [do zgodności komunikacji](communication-compliance-configure.md). Aby uzyskać informacje dotyczące licencjonowania zgodności komunikacji, [zobacz Microsoft 365 licencjonowania w celu zapewnienia zgodności & komunikacji](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

## <a name="task-8-see-whats-happening-with-your-sensitive-items"></a>Zadanie 8. Zobacz, co się dzieje z poufnymi elementami

Etykiety wrażliwości, typy informacji poufnych, etykiety przechowywania i zasady oraz przeszkolne klasyfikatory mogą być używane do klasyfikowania i oznaczania poufnych elementów w elementach Exchange, SharePoint i OneDrive tak jak w poprzednich zadaniach. Ostatnim krokiem szybkiej podróży po zadaniach jest zobaczenie, które elementy zostały oznaczone etykietą i jakie akcje użytkownicy będą podejmowane w przypadku tych poufnych elementów. [Eksplorator zawartości i](data-classification-content-explorer.md) [Eksplorator aktywności](data-classification-activity-explorer.md) zapewniają tę widoczność.

### <a name="content-explorer"></a>Eksplorator zawartości
Eksplorator zawartości umożliwia wyświetlanie w natywnym formacie wszystkich elementów sklasyfikowanych jako typ informacji poufnych lub należących do określonej klasyfikacji przez przeszkolny klasyfikatora, a także wszystkich elementów, które mają etykietę wrażliwości lub przechowywania.

Aby uzyskać szczegółowe wskazówki dotyczące korzystania z Eksploratora zawartości, zobacz [Poznanie danych —](data-classification-overview.md) omówienie klasyfikacji danych i Wprowadzenie [do Eksploratora zawartości](data-classification-content-explorer.md).

### <a name="activity-explorer"></a>Eksplorator aktywności
W Eksploratorze aktywności można monitorować, co jest wykonywane wraz z klasyfikowanym i oznaczonym poufnymi elementami w różnych krajach:
- SharePoint
- Exchange
- OneDrive

Dostępnych jest ponad 30 różnych filtrów, niektóre są dostępne:

- zakres dat
- typ działania
- lokalizacja
- użytkownik
- etykieta wrażliwości
- etykieta przechowywania
- ścieżka pliku
- Zasady DLP

Aby uzyskać szczegółowe instrukcje dotyczące korzystania z Eksploratora aktywności, zobacz [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md).

## <a name="next-steps"></a>Następne kroki

Po skonfigurowaniu podstaw zarządzania zgodnością w organizacji warto rozważyć następujące rozwiązania dotyczące zgodności w programie Microsoft 365, aby ułatwić ochronę poufnych informacji oraz wykrywanie dodatkowych czynników ryzyka w zakresie niejawnego programu testów i działanie na ich podstawie.

### <a name="configure-retention-labels"></a>Konfigurowanie etykiet przechowywania

Zasady przechowywania są automatycznie stosowane do wszystkich elementów na poziomie kontenera (takich jak witryny programu SharePoint, skrzynki pocztowe użytkowników itp[.), natomiast](retention.md#retention-labels) etykiety przechowywania mają zastosowanie do poszczególnych elementów, takich jak dokument programu SharePoint lub wiadomość e-mail. Etykiety te można stosować ręcznie lub automatycznie.

Etykiety przechowywania mogą być używane w ramach strategii dotyczącej informacji zarządzania zachowaniem tego, czego potrzebujesz, i usuwaniem tego, co nie jest potrzebne. Etykiet tych należy używać, gdy są potrzebne wyjątki od zasad przechowywania, gdy określone dokumenty lub wiadomości e-mail wymagają różnych ustawień przechowywania lub usuwania. Na przykład twoje SharePoint będą zachowywać wszystkie dokumenty przez trzy lata, ale określone dokumenty biznesowe muszą być przechowywane przez pięć lat. Aby uzyskać więcej informacji, zobacz [Tworzenie etykiet przechowywania dla wyjątków od zasad przechowywania](create-retention-labels-information-governance.md).

Jednak etykiety przechowywania w przypadku korzystania z zarządzania [rekordami](records-management.md) zapewniają o wiele więcej opcji zarządzania w celu obsługi pełnego cyklu życia dokumentów i wiadomości e-mail. Ten poziom zarządzania danymi jest odpowiedni do wymogów przechowywania dokumentacji biznesowej, prawnych lub prawnych o wysokim poziomie wartości. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do zarządzania rekordami](get-started-with-records-management.md).

### <a name="identify-and-define-sensitive-information-types"></a>Identyfikowanie i definiowanie typów informacji poufnych

Definiowanie typów informacji poufnych na podstawie wzorca zawartego w informacjach w danych organizacji. Wbudowane [typy informacji poufnych](./sensitive-information-type-entity-definitions.md) ułatwiają identyfikowanie i ochronę numerów kart kredytowych, numerów kont bankowych, paszportów i nie tylko. Możesz też utworzyć własne [niestandardowe typy informacji poufnej](create-a-custom-sensitive-information-type.md) specyficzne dla Twojej organizacji.

Aby uzyskać szczegółowe instrukcje dotyczące definiowania niestandardowych typów informacji poufnych, zobacz Tworzenie niestandardowego typu informacji poufnych w Centrum & [zabezpieczeń](./create-a-custom-sensitive-information-type.md).

### <a name="prevent-data-loss"></a>Zapobieganie utracie danych

[Zasady ochrony przed utratą danych (DLP, Data loss prevention)](dlp-learn-about-dlp.md) umożliwiają identyfikowanie, monitorowanie i automatyczne chroninie poufnych informacji w całej organizacji Microsoft 365 organizacji. Zasady DLP pomagają identyfikować poufne elementy usługi firmy Microsoft, zapobiegać przypadkowemu udostępnianiu poufnych elementów i pomagać użytkownikom nauczyć się, jak zachować zgodność bez przerywania przepływu pracy.

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad DLP, tworzenia [, testowania i dostosowania zasad DLP](create-test-tune-dlp-policy.md). Aby uzyskać informacje dotyczące licencjonowania zarządzania utratą danych, Microsoft 365 [wskazówki dotyczące licencjonowania w celu zapewnienia & zgodnością](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="detect-and-act-on-insider-risks"></a>Wykrywanie czynników ryzyka w niejawnym programie testów i działanie na ich podstawie

Coraz więcej pracowników ma coraz większy dostęp do tworzenia i udostępniania danych oraz zarządzania nimi w różnych platformach i usługach. W większości przypadków organizacje mają ograniczone zasoby i narzędzia do identyfikowania zagrożeń dla całej organizacji i ich ograniczania, a także spełniają wymagania dotyczące zgodności z przepisami i standardy ochrony prywatności pracowników. Te zagrożenia mogą obejmować kradzież danych przez odchodzące pracowników i wycieki danych spoza organizacji w przypadku przypadkowego oversharingu lub złośliwych intencji.

[Zarządzanie ryzykiem](insider-risk-management-policies.md) niejawnego programu testów w programie Microsoft 365 korzysta z pełnej szerokości usługi i wskaźników innych firm, aby ułatwić szybkie identyfikowanie i trygorzy oraz działanie na ryzykownych działaniach użytkowników. Za pomocą dzienników firmy Microsoft 365 i usługi Microsoft Graph zarządzanie ryzykiem w ramach niejawnego programu testów umożliwia definiowanie konkretnych zasad w celu identyfikowania wskaźników ryzyka i podjęcia działań w celu ich zmniejszenia.

Aby uzyskać szczegółowe instrukcje dotyczące planowania i konfigurowania zasad zarządzania ryzykiem w niejawnym programie testów, zobacz [Planowanie](insider-risk-management-plan.md) zarządzania ryzykiem w niejawnym programie testów i Rozpoczynanie pracy z zarządzaniem [ryzykiem w niejawnym programie testów](insider-risk-management-configure.md). Aby uzyskać informacje dotyczące licencjonowania zarządzania ryzykiem w niejawnym programie testów, Microsoft 365 wskazówki dotyczące [licencjonowania w celu zapewnienia & zgodnością](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management).
