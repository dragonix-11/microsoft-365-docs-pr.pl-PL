---
title: Zasady zgodności komunikacji
description: Dowiedz się więcej o zasadach zgodności komunikacji.
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
ms.openlocfilehash: 33961088105e838add3634024bb85807a6550eb7
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450734"
---
# <a name="communication-compliance-policies"></a>Zasady zgodności komunikacji

## <a name="policies"></a>Policies (zasady)

> [!IMPORTANT]
> Tworzenie zasad zgodności komunikacji i zarządzanie nimi za pomocą programu PowerShell nie jest obsługiwane. Aby utworzyć te zasady i zarządzać nimi, musisz użyć kontrolek zarządzania zasadami w Microsoft 365 [rozwiązania do zgodności komunikacji](https://compliance.microsoft.com/supervisoryreview).

Tworzysz zasady zgodności komunikacji dla Microsoft 365 organizacji w Centrum zgodności platformy Microsoft 365. Zasady zgodności komunikacji określają, które informacje i użytkownicy będą podlegać kontroli w organizacji, określają niestandardowe warunki, które ta komunikacja musi spełnić, oraz określają, kto powinien być przeglądany. Użytkownicy z *przypisaną rolą* Administratora zgodności komunikacji mogą skonfigurować zasady, a każda osoba z przypisaną rolą Communication (Zgodność komunikacji)  może uzyskać dostęp do strony zgodności komunikacji i ustawień globalnych w Centrum zgodności platformy Microsoft 365. W razie potrzeby można wyeksportować historię zmian zasad do pliku programu .csv (wartości rozdzielane przecinkami), który zawiera również stan alertów oczekujących na przejrzenie, eskalacji elementów i elementów rozwiązanych. Zasad nie można zmienić ani usunąć, gdy nie są już potrzebne.

## <a name="policy-templates"></a>Szablony zasad

Szablony zasad to wstępnie zdefiniowane ustawienia zasad, za pomocą których można szybko tworzyć zasady dotyczące typowych scenariuszy zgodności. Każdy z tych szablonów ma różnice w warunkach i zakresie, a wszystkie szablony używają tych samych typów sygnałów skanowania. Do wyboru są następujące szablony zasad:

|**Obszar**|**Szablon zasad**|**Szczegóły**|
|:-----|:-----|:-----|
| **Nieodpowiedni tekst** | Wykrywanie nieodpowiedniego tekstu | — Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> — Kierunek: przychodzący, wychodzący, wewnętrzny <br> - Przeglądanie wartości procentowej: 100% <br> — Warunki: Klasyfikatorzy podszywki, podszycie się i molestowania |
| **Nieodpowiednie obrazy** | Wykrywanie nieodpowiednich obrazów | — Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> — Kierunek: przychodzący, wychodzący, wewnętrzny <br> - Przeglądanie wartości procentowej: 100% <br> - Warunki: Klasyfikatory obrazu dla dorosłych i osoby dorosłej |
| **Informacje poufne** | Monitorowanie w celu odszukiwnia informacji poufnych | — Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> — Kierunek: przychodzący, wychodzący, wewnętrzny <br> - Przejrzyj procent: 10% <br> — Warunki: Informacje poufne, niestandardowe wzorce zawartości i typy, opcja słownika niestandardowego, załączniki większe niż 1 MB |
| **Zgodność z przepisami** | Monitorowanie zgodności z przepisami | — Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> — Kierunek: przychodzący, wychodzący <br> - Przejrzyj procent: 10% <br> — Warunki: opcja słownika niestandardowego, załączniki o rozmiarze większym niż 1 MB |
| **Konflikt interesów** | Monitorowanie pod celu monitorowania konfliktu zainteresowań | — Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> — Kierunek: Wewnętrzny <br> - Przeglądanie wartości procentowej: 100% <br> — Warunki: Brak |

Korespondencja jest skanowana co 24 godziny od chwili utworzenia zasad czasu. Jeśli na przykład utworzysz nieodpowiednie zasady dotyczące zawartości o godzinie 11:00, zasady będą zbierać sygnały dotyczące zgodności komunikacji co 24 godziny o 11:00 dziennie. Edytowanie zasad nie zmieni się tym razem. Aby wyświetlić datę i czas ostatniego skanowania zasad, przejdź do kolumny Ostatnie  skanowanie zasad na **stronie** Zasady. Po utworzeniu nowych zasad wyświetlenie daty i godziny pierwszego skanowania zasad może potrwać do 24 godzin. Data i godzina ostatniego skanowania są konwertowane na strefę czasową systemu lokalnego.

## <a name="pause-a-policy-preview"></a>Wstrzymywanie zasad (wersja Preview)

Po utworzeniu zasad zgodności komunikacji w razie potrzeby mogą zostać tymczasowo wstrzymane. Wsłuchiwanie zasad może być używane do testowania lub rozwiązywania problemów ze dopasowaniami zasad lub do optymalizowania warunków zasad. Zamiast usuwać zasady w tej sytuacji, wstyczanie zasad zachowuje także istniejące alerty zasad i wiadomości dla trwających badań i przeglądów. Wstrzymywanie zasad uniemożliwia generowanie inspekcji i alertów dla wszystkich warunków wiadomości użytkownika zdefiniowanych w zasadach na czas wstrzymania zasad. Aby wstrzymać lub ponownie uruchomić zasady, użytkownicy muszą być członkami grupy ról *Administrator zgodności* komunikacji.

Aby wstrzymać zasady, przejdź do strony **Zasady** , wybierz zasady, a następnie wybierz pozycję Wstrzymaj **zasady** na pasku narzędzi akcji. W **okienku Wstrzymaj** zasady potwierdź, że chcesz wstrzymać zasady, wybierając pozycję **Wstrzymaj**. W niektórych przypadkach może upłynie do 24 godzin, aż zasady zostaną wstrzymane. Po wstrzymaniu zasad alerty dotyczące wiadomości spełniających te zasady nie są tworzone. Jednak wiadomości skojarzone z alertami, które zostały utworzone przed wstrzymaniem zasad, pozostają dostępne do badania, przeglądu i rozwiązywania problemów.

Stan zasad dla wstrzymanych zasad może wskazywać kilka stanów:

- **Aktywne**: zasady są aktywne
- **Wstrzymane**: zasady są w pełni wstrzymane.
- **Wstrzymywanie**: Zasady są w trakcie wstrzymywania.
- **Wznawianie**: Zasady w procesie wznawiania.
- **Błąd podczas wznawiania**: Podczas wznawiania zasad wystąpił błąd. Aby sprawdzić śledzenie stosu błędów, umieść wskaźnik myszy na kolumnie  Błąd w kolumnie Stan na stronie Zasady.
- **Błąd w wstrzymaniu**: Podczas wsłuchiania zasad wystąpił błąd. Aby sprawdzić śledzenie stosu błędów, umieść wskaźnik myszy na kolumnie Błąd wsadu *w* kolumnie Stan na stronie Zasady.

Aby wznowić działanie zasad, przejdź do strony **Zasady** , wybierz zasady, a następnie wybierz pozycję Wznów **zasady** na pasku narzędzi akcje. W **okienku Wznów** zasady potwierdź, że chcesz wznowić działanie zasad, wybierając pozycję **Wznów**. W niektórych przypadkach może upłynie do 24 godzin, aż zasady zostaną wznowione. Po wznowieniu zasad zostaną utworzone alerty o wiadomościach zgodnych z zasadami, które będą dostępne do badania, przeglądu i rozwiązywania problemów.

## <a name="copy-a-policy-preview"></a>Kopiowanie zasad (wersja zapoznawcza)

W przypadku organizacji z istniejącymi zasadami zgodności komunikacji przydatne mogą być scenariusze podczas tworzenia nowych zasad na pomocą istniejących zasad. Skopiowanie zasad powoduje utworzenie dokładnego duplikatu istniejących zasad, łącznie z wszystkimi użytkownikami o zakresie, wszystkimi przydzielonymi recenzentami i wszystkimi warunkami zasad. Niektóre scenariusze mogą obejmować:

- **Osiągnięto limit magazynowania zasad**: Zasady aktywnej zgodności komunikacji mają limity magazynowania wiadomości. Po osiągnięciu limitu magazynowania dla zasad zasady są automatycznie dezaktywowane. Organizacje, które muszą nadal wykrywać, przechwytywać i działać na nieodpowiednich wiadomościach objętych dezaktywowanymi zasadami, mogą szybko utworzyć nowe zasady o identycznej konfiguracji.
- **Wykrywanie i przeglądanie nieodpowiednich** wiadomości dla różnych grup użytkowników: Niektóre organizacje mogą preferować tworzenie wielu zasad z taką samą konfiguracją, ale także uwzględniać różnych użytkowników w zakresie i różnych recenzentów poszczególnych zasad.
- **Podobne zasady z niewielkimi** zmianami: W przypadku zasad ze złożonymi konfiguracjami lub warunkami utworzenie nowych zasad na ich pomocą może zaoszczędzić czas.

Aby skopiować zasady, użytkownicy muszą być członkami grup ról Zgodność *komunikacji* lub *Administrator* zgodności komunikacji. Po utworzeniu nowych zasad na podstawie istniejących zasad wyświetlanie wiadomości, które są zgodne z nową konfiguracją zasad, może potrwać do 24 godzin.

Aby skopiować zasady i utworzyć nowe zasady, wykonaj następujące czynności:

1. Wybierz zasady, które chcesz skopiować.
2. Wybierz **przycisk kopiuj** pasek poleceń zasad na pasku poleceń lub wybierz polecenie Kopiuj **zasady** z menu akcji zasad.
3. W **okienku Kopiowanie** zasad możesz zaakceptować domyślną nazwę zasad w polu **Nazwa** zasad lub zmienić nazwę zasad. Nazwa zasad dla nowych zasad nie może być taka sama jak istniejąca, aktywna lub dezaktywowana zasada. Wypełnij pole **Opis** zgodnie z potrzebami.
4. Jeśli nie potrzebujesz dalszego dostosowywania zasad, wybierz pozycję Kopiuj **zasady** , aby ukończyć proces. Jeśli chcesz zaktualizować konfigurację nowych zasad, wybierz pozycję **Dostosuj zasady**. Zostanie uruchomiony kreator zasad ułatwiający aktualizowanie i dostosowywanie nowych zasad.

## <a name="storage-limit-notification-preview"></a>Storage powiadomienia o limitach (wersja zapoznawcza)

Każda zasada zgodności komunikacji ma rozmiar limitu magazynowania 100 GB lub 1 milion wiadomości, w zależności od tego, co zostanie osiągnięte najpierw. Gdy zasady będą zbliżać się do tych limitów, powiadomienia e-mail będą automatycznie wysyłane  do użytkowników przypisanych do grup ról Zgodność z komunikacją lub *Administrator zgodności* komunikacji. Powiadomienia są wysyłane, gdy rozmiar przestrzeni dyskowej lub liczba wiadomości osiągnie 80, 90 i 95 procent limitu. Po osiągnięciu limitu zasad zasady są automatycznie dezaktywowane i zasady wstrzymuje przetwarzanie komunikatów alertów.

>[!IMPORTANT]
>Jeśli zasady zostaną zdezaktywowane ze względu na osiągnięcie limitów magazynowania i wiadomości, oceń sposób zarządzania dezaktywowanych zasad. Jeśli usuniesz zasady, wszystkie wiadomości, skojarzone załączniki i alerty wiadomości zostaną trwale usunięte. Jeśli chcesz zachować te elementy do użytku w przyszłości, nie usuwaj dezaktywowanych zasad.

Aby zarządzać zasadami zbliżających się do limitów magazynowania i wiadomości, rozważ skopiowanie zasad w celu zachowania ciągłości obsługi lub wykonanie następujących działań w celu zminimalizowania bieżącego rozmiaru magazynu zasad i liczby wiadomości:

- Rozważ zmniejszenie liczby użytkowników przypisanych do zasad. Usunięcie użytkowników z zasad lub utworzenie różnych zasad dla różnych grup użytkowników może spowolnić wzrost rozmiaru zasad i łączną liczbę wiadomości.
- Przeanalij zasady pod aby sprawdzić nadmiarowe alerty fałszywie dodatnie. Rozważ dodanie wyjątków lub zmian w warunkach zasad w celu ignorowania typowych alertów fałszywie dodatnich.
- Jeśli zasady osiągną limity magazynowania lub wiadomości i zostały zdezaktywowane, skopiuj zasady, aby nadal wykrywać i podjąć działania dotyczące tych samych warunków i użytkowników.

## <a name="policy-settings"></a>Ustawienia zasad

### <a name="users"></a>Użytkownicy

Możesz wybrać opcję Wszyscy użytkownicy **lub** zdefiniować konkretnych użytkowników w zasadach zgodności komunikacji. Zaznaczenie **opcji Wszyscy** użytkownicy powoduje zastosowanie zasad do wszystkich użytkowników i wszystkich grup, do których każdy użytkownik jest członkiem. Zdefiniowanie konkretnych użytkowników powoduje zastosowanie tych zasad do zdefiniowanych użytkowników, a wszelkie grupy, do których są dołączona zdefiniowanych użytkowników, są uwzględniane jako ich członka.

### <a name="direction"></a>Kierunek

Domyślnie wyświetlany jest **warunek** Kierunek i nie można go usunąć. Ustawienia kierunku komunikacji w zasadach są wybierane osobno lub razem:

- **Przychodzący:** Wykrywa komunikację przesyłaną  do nadzorowanych użytkowników od nadawców zewnętrznych i wewnętrznych, w tym innych użytkowników nadzorowanych w zasadach.
- **Ruch wychodzący**: Wykrywa komunikację  przesyłaną przez nadzorowanych użytkowników do adresatów zewnętrznych i wewnętrznych, w tym innych użytkowników nadzorowanych w zasadach.
- **Wewnętrznie**: Wykrywa komunikację **między** nadzorowanych użytkownikami lub grupami w zasadach.

### <a name="sensitive-information-types"></a>Typy informacji poufnych

W ramach zasad zgodności komunikacji możesz w swoich zasadach zgodności do uwzględnienia typów informacji poufnych. Typy informacji poufnych to wstępnie zdefiniowane lub niestandardowe typy danych, które pomagają identyfikować i chronić numery kart kredytowych, numery kont bankowych, numery paszportów i nie tylko. W ramach tego dowiesz się, jak zapobiegać utracie [danych, w](dlp-learn-about-dlp.md) konfiguracji informacji poufnych można używać wzorców, odległości znaków, poziomów ufności, a nawet niestandardowych typów danych w celu identyfikowania i oflagowania zawartości, która może być podejściowa. Domyślne typy informacji poufnych to:

- Finanse
- Medyczne i medyczne
- Prywatność
- Niestandardowy typ informacji

> [!IMPORTANT]
> Typy SIT mają dwa różne sposoby definiowania parametrów maksymalnej liczby unikatowych wystąpień. Aby dowiedzieć się więcej, zobacz [Obsługiwane wartości liczby wystąpień dla usługi SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Aby dowiedzieć się więcej o szczegółach dotyczących informacji poufnych i wzorcach zawartych w typach domyślnych, zobacz Definicje encji [typu informacji poufnych](sensitive-information-type-entity-definitions.md).

### <a name="custom-keyword-dictionaries"></a>Niestandardowe słowniki słów kluczowych

Skonfiguruj słowniki niestandardowych słów kluczowych (lub lexicons), aby zapewnić proste zarządzanie słowami kluczowymi specyficznymi dla organizacji lub branży. Słowniki słów kluczowych obsługują do 100 KB terminów (po kompresji) w słowniku i obsługują dowolny język. Limit dzierżawy po kompresji również wynosi 100 KB. W razie potrzeby możesz zastosować wiele niestandardowych słowników słów kluczowych do jednej zasady lub zastosować jeden słownik słów kluczowych do jednej zasady. Te słowniki są przypisywane do zasad zgodności komunikacji i mogą być źródłową z pliku (na przykład listy .csv lub .txt) albo z listy, która można zaimportować w Centrum [zgodności](create-a-keyword-dictionary.md). Jeśli potrzebujesz obsługi terminów lub języków specyficznych dla organizacji i zasad, użyj słowników niestandardowych.

### <a name="classifiers"></a>Klasyfikatory

Wbudowana klasyfikatorzy klasyfikatorzy globalni i przeszkolni w zakresie zgodności skanują wysłane lub odebrane wiadomości ze wszystkich kanałów komunikacji w organizacji w poszukiwaniu różnych typów problemów ze zgodnością. Klasyfikatory używają kombinacji sztucznej inteligencji i słów kluczowych do identyfikowania języka w wiadomościach, które mogą naruszać zasady ochrony przed molestowaniem. Wbudowane klasyfikatory obecnie obsługują identyfikację słów kluczowych wiadomości w kilku językach:

- Chiński (uproszczony)
- English
- French
- German
- Italian
- Japanese
- Portugalski
- Spanish

Wbudowana w komunikację, wytłaczalna i globalna klasyfikatorzy skanują komunikację pod kątem terminów, obrazów i sentymentów dla następujących typów języka i zawartości:

- **Obrazy dorosłych**: skanuje w poszukiwaniu obrazów erogarnych w przyrodzie.
- **Dotyczy** dyskryminacyjnego języka dyskryminacyjnego, który jest szczególnie poufny dla dyskryminacyjnego języka dla społeczności afrykańskich/czarnych w porównaniu z innymi społecznościami.
- **Obrazy wąsów**: skanuje obrazy przedstawiające sceny przemocy i wąsy.
- **Profanity**: skanuje w poszukiwaniu wulgarnych wyrażeń, które kłopotliwe dla większości osób.
- **Mniej treściwe obrazy**: skanuje w poszukiwaniu obrazów, które erotycyjnie sugerują w przywróceniu natury, ale zawierają mniej jawną zawartość niż obrazy uważane za dorosłe.
- **Molestowanie kierowane**: skanuje w poszukiwaniu obraźliwych działań dotyczących rasy, koloru, religii, pochodzenia państwowego.
- **Zagrożenie**: Skanuje w poszukiwaniu zagrożeń w celu zatwierdzenia przemocy lub wyszkodowania fizycznego osoby lub mienia.

*Klasyfikatory obrazu* Dla dorosłych, *Ania* i *Gory* skanują pliki w formatach jpeg, jpeg, .png, .gif i .bmp formatach. Rozmiar plików obrazów musi być mniejszy niż 4 megabajty (MB), a wymiary obrazów muszą być większe niż 50x50 pikseli i większe niż 50 kilobajtów (KB), aby obraz był kwalifikuje się do oceny. Identyfikacja obrazów jest obsługiwana w Exchange Online e-mail i Microsoft Teams kanałach i czatach.

Wbudowane klasyfikatory przeszkolne i globalne nie zawierają pełnej listy terminów i obrazów dla tych obszarów. Ponadto standardy językowe i kulturowe stale się zmieniają, a w związku z tymi uwarunkowaniami firma Microsoft zastrzega sobie prawo do według własnego uznania do aktualizowania klasyfikatorów. Klasyfikatorzy mogą pomóc Twojej organizacji w monitorowaniu tych obszarów, natomiast klasyfikatory nie są przeznaczone wyłącznie do monitorowania lub adresowania takiego języka czy obrazów. Twoja organizacja, a nie firma Microsoft, ponosi odpowiedzialność za wszystkie decyzje związane z monitorowaniem, skanowaniem i blokowaniem języków i obrazów w tych obszarach, w tym zgodność z lokalnymi przepisami prawnymi i prywatnością. Firma Microsoft zachęca do konsultowania się z doradcą prawnym przed wdrożeniem i użyciem.

> [!NOTE]
> Zasady używające klasyfikatorów sprawdzają i oceniają wiadomości, których liczba wyrazów jest większa niż sześć. Wiadomości zawierające mniej niż sześć wyrazów nie są oceniane w zasadach przy użyciu klasyfikatorów. Aby identyfikować i podjąć działania na krótszych wiadomościach zawierających nieodpowiednią zawartość, zalecamy użycie niestandardowego słownika słów kluczowych do monitorowania zasad zgodności komunikacji dla tego typu zawartości.

Aby uzyskać informacje na temat przeszkolnych klasyfikatorów w Microsoft 365, zobacz Wprowadzenie do przeszkolnych [klasyfikatorów](classifier-get-started-with.md).

### <a name="optical-character-recognition-ocr"></a>Optyczne rozpoznawanie znaków (OCR)

Skonfiguruj wbudowane lub niestandardowe zasady zgodności komunikacji w celu skanowania i identyfikowania drukowanego lub napisanego ręcznie tekstu na obrazach, które mogą być nieodpowiednie w Twojej organizacji. Zintegrowane usługi [Azure Cognitive Services](/azure/cognitive-services/computer-vision/overview-ocr) i optyczne skanowanie tekstu w obrazach ułatwiają analitykom i chłonie wykrywanie i działanie w przypadkach, w których nieodpowiednie postępowanie może zostać pominięte w komunikacji, która przede wszystkim nie jest tekstowa.

Możesz włączyć optyczne rozpoznawanie znaków (OCR) w nowych zasadach na podstawie szablonów, zasad niestandardowych lub zaktualizować istniejące zasady, aby rozszerzyć obsługę przetwarzania osadzonych obrazów i załączników. Po włączeniu w zasadach utworzonych na podstawie szablonu zasad automatyczne skanowanie jest obsługiwane dla osadzonych lub dołączonych obrazów w wiadomościach e-mail i Microsoft Teams wiadomościach czatu. W przypadku obrazów osadzonych w plikach dokumentów skanowanie OCR nie jest obsługiwane. W przypadku zasad niestandardowych w zasadach należy skonfigurować co najmniej jedno lub więcej ustawień warunkowych skojarzonych ze słowami kluczowymi, wbudowanymi klasyfikatorami lub typami informacji poufnych, aby umożliwić wybór funkcji skanowania OCR.

Obrazy o rozmiarze od 50 KB do 4 MB w następujących formatach obrazów są skanowane i przetwarzane:

- .jpg/.jpeg (grupa joint photographic experts group)
- .png (przenośna grafika sieciowa)
- .bmp (mapa bitowa)
- tiff (format pliku obrazu tagu)
- .pdf (portable document format)

> [!NOTE]
> Skanowanie i wyodrębnianie osadzonych i dołączonych obrazów .pdf jest obecnie obsługiwane tylko w przypadku wiadomości e-mail.

Podczas przeglądania oczekujących alertów dotyczących zasad z włączoną obsługą funkcji OCR obrazy zidentyfikowane i dopasowane do warunków zasad są wyświetlane jako elementy podrzędne dla skojarzonych alertów. Oryginalny obraz można wyświetlić, aby ocenić zidentyfikowany tekst w kontekście oryginalnej wiadomości. Może upłynieć do 48 godzin, aż wykryte obrazy będą dostępne z alertami.

### <a name="conditional-settings"></a>Ustawienia warunkowe
<a name="ConditionalSettings"> </a>

Warunki, jakie wybierzesz dla tych zasad, mają zastosowanie do komunikacji z pocztą e-mail i źródłami innych firm w organizacji (na przykład z błyskawicznego bloomberga).

W poniższej tabeli wyjaśniono więcej na temat poszczególnych warunków.

|**Warunek**|**Jak używać tego warunku**|
|:-----|:-----|
| **Zawartość odpowiada dowolnej z tych klasyfikatorów.** | Zastosuj do zasad, gdy wszystkie klasyfikatory są uwzględniane lub wykluczane w wiadomości. Niektóre klasyfikatory są wstępnie zdefiniowane w dzierżawie, a niestandardowe klasyfikatory muszą być skonfigurowane oddzielnie, zanim będą dostępne dla tego warunku. Tylko jeden klasyfikator można zdefiniować jako warunek w zasadach. Aby uzyskać więcej informacji na temat konfigurowania klasyfikatorów, zobacz Informacje na temat przeszkolnych [klasyfikatorów (wersja zapoznawcza).](classifier-learn-about.md) |
| **Zawartość zawiera dowolny z tych typów informacji poufnych** | Zastosuj do zasad, gdy wszystkie typy informacji poufnych zostaną uwzględnione lub wykluczone w wiadomości. Niektóre klasyfikatory są wstępnie zdefiniowane w dzierżawie, a niestandardowe klasyfikatory można skonfigurować oddzielnie lub w ramach procesu przypisywania warunku. Każdy wybierany typ informacji poufnych jest stosowany osobno i tylko jeden z tych typów informacji poufnych musi być stosowany do wiadomości przez zasady. Aby uzyskać więcej informacji o niestandardowych typach informacji poufnych, zobacz [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md). |
| **Wiadomość jest odbierana z dowolnej z tych domen**  <br><br> **Wiadomość nie jest odbierana z żadnej z tych domen** | Zastosuj zasady, aby uwzględnić lub wykluczyć określone domeny lub adresy e-mail w odebranych wiadomościach. Wprowadź każdy adres domeny lub adresu e-mail i oddziel wiele domen lub adresów e-mail przecinkami. Każda wprowadzona domena lub adres e-mail jest stosowana osobno, tylko jedna domena lub adres e-mail musi mieć zastosowanie do zasad stosowania do wiadomości. <br><br> Jeśli chcesz przeskanować wszystkie wiadomości e-mail z określonej domeny, ale chcesz wykluczyć wiadomości, które nie muszą być przeglądane (biuletyny, ogłoszenia i tak dalej), musisz skonfigurować  wiadomość, która nie jest odbierana z żadnego z tych warunków domen, wykluczających adres e-mail (na przykład "newsletter@contoso.com"). |
| **Wiadomość jest wysyłana do dowolnej z tych domen**  <br><br> **Wiadomość nie jest wysyłana do żadnej z tych domen** | Zastosuj zasady, aby uwzględnić lub wykluczyć określone domeny w wysłanych wiadomościach. Wprowadź każdą domenę i oddziel wiele domen przecinkami. Każda domena jest stosowana osobno, tylko jedna domena musi mieć zastosowanie do zasad, które mają być stosowane do wiadomości. <br><br> Jeśli chcesz wykluczyć wszystkie wiadomości e-mail wysyłane do dwóch konkretnych domen, musisz skonfigurować,  że wiadomość nie jest wysyłana do żadnego z tych warunków domen z tymi dwiema domenami (na przykład "contoso.com,wingtiptoys.com"). |
| **Wiadomości są klasyfikowane przy użyciu dowolnych z tych etykiet**  <br><br> **Wiadomość nie jest klasyfikowana przy użyciu żadnej z tych etykiet** | Zasady mają być stosowane, gdy określone etykiety przechowywania są uwzględniane lub wykluczane w wiadomości. Etykiety przechowywania należy skonfigurować oddzielnie, a w ramach tego warunku wybierane są skonfigurowane etykiety. Każda etykieta, która zostanie przez Ciebie wybrać, jest stosowana osobno (tylko jedna z tych etykiet musi mieć zastosowanie do zasad, które będą stosowane do wiadomości). Aby uzyskać więcej informacji na temat etykiet przechowywania, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).|
| **Wiadomość zawiera dowolny z tych wyrazów**  <br><br> **Wiadomość nie zawiera żadnego z tych wyrazów** | Aby zastosować zasady, gdy określone wyrazy lub frazy zostaną uwzględnione lub wykluczone w wiadomości, wprowadź poszczególne wyrazy rozdzielone przecinkami. W przypadku fraz o dwóch lub więcej wyrazach ujmij je w cudzysłów. Każdy wprowadzany wyraz lub każda w wprowadzana fraza jest stosowana osobno (tylko jeden wyraz musi być stosowany do zasad do wiadomości). Aby uzyskać więcej informacji na temat wprowadzania wyrazów lub fraz, zobacz następną sekcję Dopasowywanie wyrazów i fraz do wiadomości e-mail [lub załączników](communication-compliance-policies.md#Matchwords).|
| **Załącznik zawiera dowolny z tych wyrazów**  <br><br> **Załącznik nie zawiera żadnego z tych wyrazów** | Aby zastosować zasady, gdy określone wyrazy lub frazy zostaną uwzględnione lub wykluczone w załączniku wiadomości (na przykład w dokumencie programu Word), wprowadź poszczególne wyrazy rozdzielone przecinkami. W przypadku fraz o dwóch lub więcej wyrazach ujmij je w cudzysłów. Każdy wprowadzany wyraz lub każda w wprowadzana fraza jest stosowana osobno (tylko jeden wyraz musi być stosowany do zasad do załącznika). Aby uzyskać więcej informacji na temat wprowadzania wyrazów lub fraz, zobacz następną sekcję Dopasowywanie wyrazów i fraz do wiadomości e-mail [lub załączników](communication-compliance-policies.md#Matchwords).|
| **Załącznik jest dowolnym z tych typów plików**  <br><br> **Załącznik nie jest jednym z tych typów plików** | Aby nadzorować komunikację z określonymi typami załączników lub wykluczać z nich, wprowadź rozszerzenia plików (takie jak .exe lub .pdf). Jeśli chcesz uwzględnić lub wykluczyć wiele rozszerzeń plików, wprowadź je w oddzielnych wierszach. Aby zastosować zasady, tylko jedno rozszerzenie załącznika musi być zgodne.|
| **Rozmiar wiadomości jest większy niż**  <br><br> **Rozmiar wiadomości nie jest większy niż** | Aby przejrzeć wiadomości na podstawie określonego rozmiaru, należy użyć tych warunków do określenia maksymalnego lub minimalnego rozmiaru wiadomości, która może być zanim zostanie zweryfikowana. Jeśli na przykład określisz, że rozmiar wiadomości jest większy **niż** \> **1,0 MB**, wszystkie wiadomości o rozmiarze 1,01 MB i większym będą podlegać recenzji. Dla tego warunku możesz wybrać bajty, kilobajty, megabajty lub gigabajty.|
| **Rozmiar załącznika jest większy niż**  <br><br> **Rozmiar załącznika nie jest większy niż** | Aby przejrzeć wiadomości na podstawie rozmiaru załączników, określ maksymalny lub minimalny rozmiar załącznika przed przejrzeniem wiadomości i jej załączników. Jeśli na przykład określisz  \>, że rozmiar załącznika jest większy niż **2,0 MB**, wszystkie wiadomości z załącznikami o rozmiarze 2,01 MB lub więcej będą podlegać recenzji. Dla tego warunku możesz wybrać bajty, kilobajty, megabajty lub gigabajty.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Dopasowywanie wyrazów i fraz do wiadomości e-mail lub załączników
<a name="Matchwords"> </a>

Każdy wprowadzany wyraz oddzielony przecinkiem jest stosowany osobno (tylko jeden wyraz musi być stosowany do warunku zasad stosowanego do wiadomości e-mail lub załącznika). Na przykład użyjmy warunku Wiadomość zawiera dowolny z tych **słów, ze** słowami kluczowymi "banker", "poufne" i "niejawny program handlowy" oddzielone przecinkiem (banker, poufne,"niejawny program handlowych"). Zasady dotyczą wszystkich wiadomości, które zawierają wyraz "banker", "poufne" lub frazę "insider trading". Aby zastosować ten warunek zasad, musi występować tylko jeden z tych wyrazów lub fraz. Wyrazy w wiadomości lub załączniku muszą dokładnie odpowiadać wprowadzeniu.

> [!IMPORTANT]
>
> Podczas importowania pliku słownika niestandardowego każdy wyraz lub frazę należy oddzielić za pomocą powrotu karetki i w osobnym wierszu. Przykład:
>
> *banker* <br>
> *poufne* <br>
> *niejawny program handlowy*

Aby przeskanować zarówno wiadomości e-mail, jak i załączniki w poszukiwaniu tych samych słów kluczowych, utwórz niestandardowy słownik słów kluczowych dla terminów, które chcesz przeskanować w wiadomościach.[](create-a-keyword-dictionary.md) Ta konfiguracja zasad identyfikuje zdefiniowane słowa kluczowe wyświetlane w wiadomości e-mail **LUB** w załączniku wiadomości e-mail. Używanie standardowych ustawień zasad warunkowych *(wiadomość* zawiera dowolny z tych wyrazów, a załącznik zawiera dowolny z tych wyrazów *) do* identyfikowania terminów w wiadomościach i załącznikach wymaga, aby  terminy były obecne zarówno w wiadomości, jak i w załączniku.

#### <a name="enter-multiple-conditions"></a>Wprowadź wiele warunków

W przypadku wprowadzenia wielu warunków Microsoft 365 wszystkie warunki razem określają, kiedy stosować zasady zgodności komunikacji do elementów do komunikacji. W przypadku skonfigurowania wielu warunków wszystkie warunki muszą być spełnione, aby zasady były stosowane, o ile nie wprowadzeniu wyjątku. Zasady są potrzebne na przykład wtedy, gdy wiadomość zawiera wyraz "transakcje" i ma rozmiar większy niż 2 MB. Jeśli jednak wiadomość zawiera również wyrazy "Zatwierdzone przez firmę Contoso — finansowe", zasady nie powinny być stosowane. W tym przykładzie te trzy warunki zostałyby zdefiniowane w następujący sposób:

- **Wiadomość zawiera dowolny z tych słów** i słowo kluczowe "handlowe".
- **Rozmiar wiadomości jest większy niż** i ma wartość 2 MB
- **Wiadomość nie zawiera żadnego z tych słów ze** słowami kluczowymi "Zatwierdzone przez zespół finansowy Contoso"

### <a name="review-percentage"></a>Przeglądanie wartości procentowej

Jeśli chcesz zmniejszyć ilość zawartości do przejrzenia, możesz określić procent całej komunikacji objętej zasadami zgodności komunikacji. W czasie rzeczywistym wybierana jest losowa próbka zawartości spośród całkowitego procentu zawartości, która jest taka, jaka jest do warunków wybranych zasad. Jeśli chcesz, aby recenzentzy przeglądali wszystkie elementy, możesz skonfigurować **100%** w zasadach zgodności komunikacji.

## <a name="alert-policies"></a>Zasady alertów

Po skonfigurowaniu zasad automatycznie są tworzone odpowiadające im zasady alertów i są generowane alerty dla wiadomości, które są zgodne z warunkami zdefiniowanymi w zasadach. Po utworzeniu zasad otrzymywanie alertów ze wskaźników aktywności może potrwać do 24 godzin. Domyślnie do wszystkich wyzwalaczy alertów są przypisywane średnie poziomy ważności w skojarzonych zasadach alertów. Alerty są generowane dla zasad zgodności komunikacji, gdy poziom progu wyzwalacza agregacji zostanie spełniony w skojarzonych zasadach alertów. Alerty są wysyłane jednorazowo co 24 godziny, niezależnie od liczby poszczególnych wiadomości, które są zgodne z warunkami zasad. Na przykład w firmie Contoso włączono nieodpowiednie zasady zawartości, a dla 1 stycznia było 100 dopasowania zasad, które wygenerowały sześć alertów. Na koniec 1 stycznia zostanie wysłane pojedyncze powiadomienie e-mail dla tych sześciu alertów.

W przypadku zasad zgodności komunikacji następujące wartości zasad alertów są konfigurowane domyślnie:

|**Wyzwalacz zasad alertu**|**Wartość domyślna**|
|:-----|:-----|
| Agregacja | Prosta agregacja |
| Próg | Domyślne: 4 działania <br> Minimum: 3 działania <br> Wartość maksymalna: 2 147 483 647 działań |
| Okno | Domyślne: 60 minut <br> Minimum: 60 minut <br> Wartość maksymalna: 10 000 minut |

> [!NOTE]
> Ustawienia wyzwalacza progów zasad alertów dla działań obsługują co najmniej 3 wartości minimalne w przypadku zasad zgodności komunikacji.

Możesz zmienić domyślne ustawienia wyzwalaczy liczby działań, okresu działań i poszczególnych użytkowników w zasadach alertów na stronie Zasady **alertów** w Centrum zgodności platformy Microsoft 365.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Zmienianie poziomu ważności zasad alertów

Jeśli chcesz zmienić poziom ważności przypisany w zasadach alertów dla określonych zasad zgodności komunikacji, wykonaj następujące czynności:

1. Zaloguj się [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu poświadczeń dla konta administratora w Twojej Microsoft 365 organizacji.

2. W Centrum zgodności platformy Microsoft 365 przejdź do **tematu Zasady**.

3. Wybierz **Office 365 alert** na **stronie Zasady**, aby otworzyć stronę **Zasady alertów**.

4. Zaznacz pole wyboru zasad zgodności komunikacji, które chcesz zaktualizować, a następnie wybierz **pozycję Edytuj zasady**.

5. Na karcie **Opis** wybierz menu rozwijane **Ważność** , aby skonfigurować poziom alertów zasad.

6. Wybierz **pozycję Zapisz** , aby zastosować do zasad nowy poziom ważności.

7. Wybierz **pozycję Zamknij** , aby zamknąć stronę szczegółów zasad alertu.
