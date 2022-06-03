---
title: Zasady zgodności komunikacji
description: Dowiedz się więcej o zasadach zgodności komunikacji.
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
ms.openlocfilehash: 44b177d0215acaa2e637aacda22db3eb16ee7168
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65864523"
---
# <a name="communication-compliance-policies"></a>Zasady zgodności komunikacji

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="policies"></a>Policies (zasady)

> [!IMPORTANT]
> Używanie programu PowerShell do tworzenia zasad zgodności komunikacji i zarządzania nimi nie jest obsługiwane. Aby utworzyć te zasady i zarządzać nimi, należy użyć mechanizmów kontroli zarządzania zasadami w [rozwiązaniu zgodności z komunikacją](https://compliance.microsoft.com/supervisoryreview).

Zasady zgodności komunikacji są tworzone dla organizacji Microsoft 365 w portal zgodności Microsoft Purview. Zasady zgodności komunikacji określają, które komunikaty i użytkownicy podlegają przeglądowi w organizacji, definiują niestandardowe warunki, które muszą spełniać komunikacja, i określają, kto powinien wykonywać przeglądy. Użytkownicy przypisani do roli *Administracja zgodności z komunikacją* mogą konfigurować zasady, a każdy, kto ma przypisaną tę rolę, może uzyskać dostęp do strony **Zgodność komunikacji** i ustawień globalnych w portal zgodności Microsoft Purview. W razie potrzeby można wyeksportować historię modyfikacji zasad do pliku .csv (wartości rozdzielane przecinkami), który zawiera również stan alertów oczekujących na przegląd, elementy eskalowane i rozwiązane elementy. Nie można zmienić nazwy zasad i można je usunąć, gdy nie będą już potrzebne.

## <a name="policy-templates"></a>Szablony zasad

Szablony zasad to wstępnie zdefiniowane ustawienia zasad, których można użyć do szybkiego tworzenia zasad w celu rozwiązania typowych scenariuszy zgodności. Każdy z tych szablonów ma różnice w warunkach i zakresie, a wszystkie szablony używają tych samych typów sygnałów skanowania. Możesz wybrać spośród następujących szablonów zasad:

|**Obszar**|**Szablon zasad**|**Szczegóły**|
|:-----|:-----|:-----|
| **Nieodpowiedni tekst** | Wykrywanie nieodpowiedniego tekstu | - Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> - Kierunek: przychodzący, wychodzący, wewnętrzny <br> - Procent przeglądu: 100% <br> - Warunki: Klasyfikatory zagrożeń, dyskryminacji i ukierunkowanego nękania |
| **Nieodpowiednie obrazy** | Wykrywanie nieodpowiednich obrazów | - Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> - Kierunek: przychodzący, wychodzący, wewnętrzny <br> - Procent przeglądu: 100% <br> - Warunki: klasyfikatory obrazów dla dorosłych i racy |
| **Informacje poufne** | Monitorowanie pod kątem informacji poufnych | - Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> - Kierunek: przychodzący, wychodzący, wewnętrzny <br> - Procent przeglądu: 10% <br> - Warunki: informacje poufne, wbudowane wzorce zawartości i typy, opcja słownika niestandardowego, załączniki większe niż 1 MB |
| **Zgodność** | Monitorowanie pod kątem zgodności z przepisami | - Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> - Kierunek: przychodzący, wychodzący <br> - Procent przeglądu: 10% <br> - Warunki: opcja słownika niestandardowego, załączniki większe niż 1 MB |
| **Konflikt interesów** | Monitorowanie pod kątem konfliktu interesów | - Lokalizacje: Exchange Online, Microsoft Teams, Yammer, Skype dla firm <br> - Kierunek: wewnętrzny <br> - Procent przeglądu: 100% <br> - Warunki: Brak |

Komunikacja jest skanowana co 24 godziny od momentu utworzenia zasad. Jeśli na przykład utworzysz nieodpowiednie zasady zawartości o godzinie 11:00, zasady będą zbierać sygnały zgodności komunikacji co 24 godziny codziennie o godzinie 11:00. Edytowanie zasad nie zmienia się tym razem. Aby wyświetlić datę i godzinę ostatniego skanowania zasad, przejdź do kolumny *Ostatnie skanowanie zasad* na stronie **Zasady** . Po utworzeniu nowych zasad wyświetlenie daty i godziny pierwszego skanowania zasad może potrwać do 24 godzin. Data i godzina ostatniego skanowania są konwertowane na strefę czasową systemu lokalnego.

## <a name="pause-a-policy-preview"></a>Wstrzymywanie zasad (wersja zapoznawcza)

Po utworzeniu zasad zgodności komunikacji zasady mogą zostać tymczasowo wstrzymane w razie potrzeby. Wstrzymywanie zasad może służyć do testowania lub rozwiązywania problemów z dopasowaniami zasad lub do optymalizacji warunków zasad. Zamiast usuwać zasady w tych okolicznościach, wstrzymywanie zasad zachowuje również istniejące alerty zasad i komunikaty dla trwających badań i przeglądów. Wstrzymanie zasad uniemożliwia przeprowadzanie inspekcji i generowanie alertów dla wszystkich warunków komunikatów użytkownika zdefiniowanych w zasadach na czas wstrzymania zasad. Aby wstrzymać lub ponownie uruchomić zasady, użytkownicy muszą być członkami grupy ról *Administracja zgodności z komunikacją*.

Aby wstrzymać zasady, przejdź do strony **Zasady** , wybierz zasady, a następnie wybierz pozycję **Wstrzymaj zasady** na pasku narzędzi akcji. W okienku **Wstrzymaj zasady** potwierdź, że chcesz wstrzymać zasady, wybierając pozycję **Wstrzymaj**. W niektórych przypadkach wstrzymanie zasad może potrwać do 24 godzin. Po wstrzymaniu zasad alerty dotyczące komunikatów pasujących do zasad nie są tworzone. Jednak komunikaty skojarzone z alertami, które zostały utworzone przed wstrzymaniem zasad, pozostają dostępne do badania, przeglądania i korygowania.

Stan zasad wstrzymania zasad może wskazywać kilka stanów:

- **Aktywne**: zasady są aktywne
- **Wstrzymano**: zasady są w pełni wstrzymane.
- **Wstrzymywanie**: zasady są w trakcie wstrzymywania.
- **Wznowienie**: zasady w trakcie wznawiania.
- **Błąd podczas wznawiania**: wystąpił błąd podczas wznawiania zasad. W przypadku śledzenia stosu błędów umieść wskaźnik myszy nad pozycją *Błąd podczas wznawiania* stanu w kolumnie Stan na stronie Zasady.
- **Błąd podczas wstrzymywania**: wystąpił błąd podczas wstrzymywania zasad. W przypadku śledzenia stosu błędów umieść wskaźnik myszy nad pozycją *Błąd w stanie wstrzymania* w kolumnie Stan na stronie Zasady.

Aby wznowić zasady, przejdź do strony **Zasady** , wybierz zasady, a następnie wybierz pozycję **Wznów zasady** na pasku narzędzi akcji. W okienku **Wznów zasady** potwierdź, że chcesz wznowić zasady, wybierając pozycję **Wznów**. W niektórych przypadkach wznowienie zasad może potrwać do 24 godzin. Po wznowieniu zasad alerty dotyczące komunikatów pasujących do zasad zostaną utworzone i będą dostępne do badania, przeglądania i korygowania.

## <a name="copy-a-policy-preview"></a>Kopiowanie zasad (wersja zapoznawcza)

W przypadku organizacji z istniejącymi zasadami zgodności z komunikacją mogą być przydatne scenariusze tworzenia nowych zasad na podstawie istniejących zasad. Kopiowanie zasad powoduje utworzenie dokładnego duplikatu istniejących zasad, w tym wszystkich użytkowników w zakresie, wszystkich przypisanych recenzentów i wszystkich warunków zasad. Niektóre scenariusze mogą obejmować:

- **Osiągnięto limit magazynu zasad**: zasady zgodności aktywnej komunikacji mają limity magazynu komunikatów. Po osiągnięciu limitu magazynu dla zasad zasady są automatycznie dezaktywowane. Organizacje, które muszą nadal wykrywać, przechwytywać i działać na nieodpowiednich komunikatach objętych dezaktywowanymi zasadami, mogą szybko utworzyć nowe zasady z identyczną konfiguracją.
- **Wykrywanie i przeglądanie nieodpowiednich komunikatów dla różnych grup użytkowników**: niektóre organizacje mogą preferować tworzenie wielu zasad o tej samej konfiguracji, ale obejmują różnych użytkowników w zakresie i różnych recenzentów dla poszczególnych zasad.
- **Podobne zasady z niewielkimi zmianami**: w przypadku zasad ze złożonymi konfiguracjami lub warunkami może to zaoszczędzić czas na utworzenie nowych zasad na podstawie podobnych zasad.

Aby skopiować zasady, użytkownicy muszą być członkami grup ról *Zgodność z komunikacją* lub *Zgodność z komunikacją Administracja*. Po utworzeniu nowych zasad na podstawie istniejących zasad wyświetlenie komunikatów zgodnych z nową konfiguracją zasad może potrwać do 24 godzin.

Aby skopiować zasady i utworzyć nowe zasady, wykonaj następujące kroki:

1. Wybierz zasady, które chcesz skopiować.
2. Wybierz przycisk **Kopiuj** pasek poleceń zasad na pasku poleceń lub wybierz pozycję **Kopiuj zasady** z menu akcji dla zasad.
3. W okienku **Kopiowanie zasad** możesz zaakceptować domyślną nazwę zasad w polu **Nazwa zasad** lub zmienić nazwę zasad. Nazwa zasad dla nowych zasad nie może być taka sama jak istniejące aktywne lub dezaktywowane zasady. Wypełnij pole **Opis** zgodnie z potrzebami.
4. Jeśli nie potrzebujesz dalszego dostosowywania zasad, wybierz pozycję **Kopiuj zasady** , aby ukończyć proces. Jeśli chcesz zaktualizować konfigurację nowych zasad, wybierz pozycję **Dostosuj zasady**. Spowoduje to uruchomienie kreatora zasad ułatwiającego aktualizowanie i dostosowywanie nowych zasad.

## <a name="user-reported-messages-policy"></a>Zasady komunikatów zgłaszanych przez użytkowników

>[!NOTE]
>Komunikaty zgłaszane przez użytkowników zaczną być dostępne dla organizacji licencjonowanych na [potrzeby zgodności z komunikacją](/microsoft-365/compliance/communication-compliance-configure#subscriptions-and-licensing) i Microsoft Teams począwszy od maja 2022 r. Ta funkcja powinna być dostępna dla wszystkich licencjonowanych organizacji do 31 sierpnia 2022 r.

W ramach ochrony warstwowej w celu wykrywania i korygowania nieodpowiednich komunikatów w organizacji można uzupełnić zasady zgodności komunikacji o komunikaty zgłaszane przez użytkowników w Microsoft Teams. Ta funkcja umożliwia użytkownikom w organizacji samodzielne zgłaszanie nieodpowiednich wiadomości, takich jak nękanie lub grożenie językiem, udostępnianie treści dla dorosłych oraz udostępnianie poufnych lub poufnych informacji w celu wspierania bezpiecznego i zgodnego środowiska pracy.

Domyślnie włączona w [centrum administracyjnym Teams](/microsoftteams/manage-teams-in-modern-portal) opcja *Zgłoś problem* w Teams komunikatach umożliwia użytkownikom w organizacji przesyłanie nieodpowiednich komunikatów do przeglądu przez recenzentów zgodności komunikacji dla zasad. Te komunikaty są obsługiwane przez domyślne zasady systemowe, które obsługują raportowanie komunikatów w Teams kanałach, grupach i czatach prywatnych.

![Zgodność z komunikacją Zgłoś problem.](../media/communication-compliance-report-a-concern-full-menu.png)

Gdy użytkownik prześle wiadomość Teams czatu do przeglądu, wiadomość zostanie skopiowana do zasad wiadomości zgłoszonych przez użytkownika. Zgłoszone wiadomości początkowo pozostają widoczne dla wszystkich członków czatu i nie ma żadnego powiadomienia dla członków czatu lub osoby przesyłającego, że wiadomość została zgłoszona w kanałach, prywatnych ani czatach grupowych. Użytkownik nie może zgłosić tego samego komunikatu więcej niż raz, a wiadomość pozostaje widoczna dla wszystkich użytkowników uwzględnionych w sesji czatu podczas procesu przeglądu zasad. 

Podczas procesu przeglądu recenzenci zgodności komunikacji mogą wykonywać wszystkie standardowe [akcje korygowania](/microsoft-365/compliance/communication-compliance-investigate-remediate#step-3-decide-on-a-remediation-action) komunikatu, w tym usuwać komunikat z czatu Teams. W zależności od sposobu korygowania wiadomości nadawca i adresaci wiadomości będą widzieć różne [komunikaty powiadomień](/microsoftteams/communication-compliance#act-on-inappropriate-messages-in-microsoft-teams) w Teams czatach po przeglądzie.

![Zasady komunikatów zgłoszonych przez użytkownika dotyczące zgodności z komunikacją.](../media/communication-compliance-user-reported-messages-policy.png)

Komunikaty zgłaszane przez użytkownika z czatów Teams są jedynymi komunikatami przetworzonymi przez zasady komunikatów zgłaszane przez użytkownika i można modyfikować tylko przypisanych recenzentów zasad. Nie można edytować wszystkich innych właściwości zasad. Po utworzeniu zasad początkowi recenzenci przypisani do zasad są członkami grupy ról *Administratorzy zgodności komunikacji* (jeśli są wypełniani co najmniej jednym użytkownikiem) lub wszyscy członkowie globalnej grupy ról *Administracja* organizacji. Twórca zasad jest losowo wybranym użytkownikiem z grupy ról *Administratorzy zgodności komunikacji* (jeśli zostanie wypełniony co najmniej jednym użytkownikiem) lub losowo wybranym użytkownikiem z globalnej grupy ról *Administracja* organizacji.  

Administratorzy powinni natychmiast przypisywać niestandardowych recenzentów do tych zasad odpowiednio do twojej organizacji. Mogą to być recenzenci, tacy jak Oficer zgodności, Oficer ds. ryzyka lub członkowie działu zasobów ludzkich. Aby dostosować recenzentów wiadomości czatu przesłanych jako komunikaty zgłaszane przez użytkownika, wykonaj następujące kroki:

1. Zaloguj się [do portal zgodności Microsoft Purview](https://compliance.microsoft.com/) przy użyciu poświadczeń konta administratora w organizacji Microsoft 365.
2. W portalu zgodności przejdź do pozycji **Zgodność z komunikacją**.
3. Na karcie **Zasady** wybierz zasady *Komunikaty zgłaszane przez użytkownika* i wybierz pozycję **Edytuj**.
4. W okienku **Monitorowanie komunikatów zgłaszanych przez użytkownika** przypisz recenzentów do zasad. Recenzenci muszą mieć skrzynki pocztowe hostowane na Exchange Online. Gdy recenzenci są dodawani do zasad, automatycznie otrzymują wiadomość e-mail z powiadomieniem o przypisaniu do zasad i udostępniają linki do informacji o procesie przeglądu.
5. Wybierz **Zapisz**.

Opcja *Zgłoś problem* jest domyślnie włączona i może być kontrolowana za pośrednictwem zasad obsługi komunikatów Teams w [centrum Teams Administracja](/microsoftteams/manage-teams-in-modern-portal). Użytkownicy w organizacji automatycznie otrzymają zasady globalne, chyba że utworzysz i przypiszesz zasady niestandardowe. Edytuj ustawienia w zasadach globalnych lub utwórz i przypisz co najmniej jedną zasadę niestandardową, aby włączyć lub wyłączyć *opcję Zgłoś problem* . Aby dowiedzieć się więcej, zobacz [Zarządzanie zasadami obsługi komunikatów w Teams](/microsoftteams/messaging-policies-in-teams).  

>[!IMPORTANT]
>Jeśli używasz programu PowerShell do **włączania lub wyłączania opcji Raportowanie użytkowników końcowych** w centrum Teams Administracja, musisz użyć [modułu Microsoft Teams poleceń cmdlet w wersji 4.2.0 lub nowszej](/MicrosoftTeams/teams-powershell-release-notes).

## <a name="storage-limit-notification-preview"></a>powiadomienie o ograniczeniu Storage (wersja zapoznawcza)

Każda zasada zgodności z komunikacją ma rozmiar limitu magazynu wynoszący 100 GB lub 1 milion komunikatów, w zależności od tego, która z tych wartości zostanie osiągnięta jako pierwsza. W miarę zbliżania się zasad do tych limitów wiadomości e-mail z powiadomieniami są automatycznie wysyłane do użytkowników przypisanych do grup ról *Zgodność komunikacji* lub *Zgodność z komunikacją Administracja*. Komunikaty powiadomień są wysyłane, gdy rozmiar magazynu lub liczba komunikatów osiągnie 80, 90 i 95 procent limitu. Po osiągnięciu limitu zasad zasady są automatycznie dezaktywowane, a zasady przestają przetwarzać komunikaty dla alertów.

>[!IMPORTANT]
>Jeśli zasady są dezaktywowane z powodu osiągnięcia limitów magazynu i komunikatów, należy ocenić sposób zarządzania dezaktywowanymi zasadami. Jeśli usuniesz zasady, wszystkie komunikaty, skojarzone załączniki i alerty komunikatów zostaną trwale usunięte. Jeśli chcesz zachować te elementy do użytku w przyszłości, nie usuwaj dezaktywowanych zasad.

Aby zarządzać zasadami zbliżającym się do limitów magazynu i komunikatów, rozważ utworzenie kopii zasad w celu zachowania ciągłości pokrycia lub podjęcie następujących działań w celu zminimalizowania bieżącego rozmiaru magazynu zasad i liczby komunikatów:

- Rozważ zmniejszenie liczby użytkowników przypisanych do zasad. Usunięcie użytkowników z zasad lub utworzenie różnych zasad dla różnych grup użytkowników może pomóc spowolnić wzrost rozmiaru zasad i łącznej liczby komunikatów.
- Sprawdź zasady pod kątem nadmiernych alertów fałszywie dodatnich. Rozważ dodanie wyjątków lub zmian w warunkach zasad, aby zignorować typowe alerty fałszywie dodatnie.
- Jeśli zasady osiągnęły limity magazynu lub komunikatów i zostały dezaktywowane, utwórz kopię zasad, aby nadal wykrywać i podejmować działania dla tych samych warunków i użytkowników.

## <a name="policy-settings"></a>Ustawienia zasad

### <a name="users"></a>Użytkownicy

Możesz wybrać opcję **Wszyscy użytkownicy** lub zdefiniować określonych użytkowników w zasadach zgodności komunikacji. Wybranie pozycji **Wszyscy użytkownicy** stosuje zasady do wszystkich użytkowników i wszystkich grup, w których każdy użytkownik jest uwzględniony jako członek. Definiowanie określonych użytkowników stosuje zasady do zdefiniowanych użytkowników, a wszystkie grupy zdefiniowanych użytkowników są uwzględniane jako element członkowski.

### <a name="direction"></a>Kierunek

Domyślnie jest wyświetlany warunek **Kierunek** i nie można go usunąć. Ustawienia kierunku komunikacji w zasadach są wybierane indywidualnie lub razem:

- **Przychodzące**: wykrywa komunikaty wysyłane **do** nadzorowanych użytkowników od nadawców zewnętrznych i wewnętrznych, w tym innych nadzorowanych użytkowników w zasadach.
- **Wychodzące**: wykrywa komunikaty wysyłane **od** nadzorowanych użytkowników do adresatów zewnętrznych i wewnętrznych, w tym innych nadzorowanych użytkowników w zasadach.
- **Wewnętrzne**: wykrywa komunikację **między** nadzorowanym użytkownikiem lub grupami w zasadach.

### <a name="sensitive-information-types"></a>Typy informacji poufnych

W ramach zasad zgodności komunikacji można włączyć typy informacji poufnych. Typy informacji poufnych to wstępnie zdefiniowane lub niestandardowe typy danych, które mogą pomóc w identyfikowaniu i ochronie numerów kart kredytowych, numerów kont bankowych, numerów paszportów i innych. W ramach funkcji [Dowiedz się więcej o Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md) konfiguracja informacji poufnych może używać wzorców, bliskości znaków, poziomów ufności, a nawet niestandardowych typów danych, aby ułatwić identyfikowanie i oznaczanie zawartości, która może być wrażliwa. Domyślne typy informacji poufnych to:

- Finansowych
- Medycyna i zdrowie
- Prywatność
- Typ informacji niestandardowych

> [!IMPORTANT]
> Interfejsy SIC mają dwa różne sposoby definiowania maksymalnej liczby unikatowych parametrów liczby wystąpień. Aby dowiedzieć się więcej, zobacz [Liczba obsługiwanych wartości wystąpień dla usługi SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Aby dowiedzieć się więcej o szczegółach informacji poufnych i wzorcach uwzględnionych w typach domyślnych, zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md).

### <a name="custom-keyword-dictionaries"></a>Niestandardowe słowniki słów kluczowych

Skonfiguruj niestandardowe słowniki słów kluczowych (lub leksykony), aby zapewnić proste zarządzanie słowami kluczowymi specyficznymi dla organizacji lub branży. Słowniki słów kluczowych obsługują do 100 KB terminów (po kompresji) w słowniku i obsługują dowolny język. Limit dzierżawy wynosi również 100 KB po kompresji. W razie potrzeby można zastosować wiele niestandardowych słowników słów kluczowych do jednej zasady lub mieć jeden słownik słów kluczowych dla zasad. Te słowniki są przypisane w zasadach zgodności komunikacji i mogą być pozyskiwane z pliku (takiego jak lista .csv lub .txt) lub z listy, którą można [zaimportować w Centrum zgodności](create-a-keyword-dictionary.md). Używaj słowników niestandardowych, gdy musisz obsługiwać terminy lub języki specyficzne dla organizacji i zasad.

### <a name="classifiers"></a>Klasyfikatorów

[Wbudowane klasyfikatory trenujące i globalne](/microsoft-365/compliance/classifier-learn-about) skanują wysyłane lub odbierane komunikaty we wszystkich kanałach komunikacyjnych w organizacji w celu uzyskania różnych typów problemów ze zgodnością. Klasyfikatory używają kombinacji sztucznej inteligencji i słów kluczowych do identyfikowania języka w komunikatach, które mogą naruszać zasady ochrony przed molestowaniem. Wbudowane klasyfikatory obsługują obecnie identyfikację słów kluczowych komunikatów w kilku językach:

- Arabski
- Chiński (uproszczony)
- Chiński (tradycyjny)
- Dutch
- English
- French
- German
- Italian
- Korean
- Japanese
- Portugalski
- Spanish

Wbudowane klasyfikatory trenujące i globalne zgodności z komunikacją skanują komunikację pod kątem terminów, obrazów i tonacji dla następujących typów języka i zawartości:

- **Obrazy dla dorosłych**: skanuje obrazy o charakterze jednoznacznie seksualnym.
- **Skargi klientów**: skanuje opinie i skargi dotyczące produktów lub usług organizacji.
- **Dyskryminacja**: Skanuje w poszukiwaniu jawnego dyskryminującego języka i jest szczególnie wrażliwa na dyskryminujący język wobec społeczności Afroamerykańskich/Czarnych w porównaniu z innymi społecznościami.
- **Gory images**: Skanuje obrazy, które przedstawiają przemoc i gore.
- **Molestowanie**: Skanuje pod kątem obraźliwych zachowań wymierzonych w ludzi w odniesieniu do rasy, koloru, religii, pochodzenia narodowego.
- **Wulgaryzmy**: Skanuje w poszukiwaniu wulgarnych wyrażeń, które zawstydzają większość ludzi.
- **Obrazy erotyczne**: Skanuje obrazy, które mają charakter seksualnie sugestywny, ale zawierają mniej jawną zawartość niż obrazy uważane za dorosłe.
- **Zagrożenie**: Skanuje pod kątem gróźb popełnienia przemocy lub fizycznej szkody dla osoby lub mienia.

Klasyfikatory obrazów *Adult*, *Racy* i *Gory* skanują pliki w formatach jpeg, .png, .gif i .bmp. Rozmiar plików obrazów musi być mniejszy niż 4 megabajty (MB), a wymiary obrazów muszą być większe niż 50x50 pikseli i większe niż 50 kilobajtów (KB), aby obraz kwalifikował się do oceny. Identyfikacja obrazów jest obsługiwana w przypadku Exchange Online wiadomości e-mail oraz Microsoft Teams kanałów i czatów.

Wbudowane klasyfikatory trenowalne i globalne nie zawierają wyczerpującej listy terminów ani obrazów w tych obszarach. Ponadto standardy językowe i kulturowe stale się zmieniają, a w świetle tych realiów firma Microsoft zastrzega sobie prawo do aktualizowania klasyfikatorów według własnego uznania. Klasyfikatory mogą pomóc twojej organizacji w monitorowaniu tych obszarów, ale klasyfikatory nie są przeznaczone do zapewniania organizacji jedynego sposobu monitorowania lub rozwiązywania problemów z takim językiem lub obrazami. Twoja organizacja, a nie firma Microsoft, pozostaje odpowiedzialna za wszystkie decyzje związane z monitorowaniem, skanowaniem i blokowaniem języka i obrazów w tych obszarach, w tym za zgodność z lokalną prywatnością i innymi obowiązującymi przepisami. Firma Microsoft zachęca do konsultacji z radcą prawnym przed wdrożeniem i użyciem.

> [!NOTE]
> Zasady używające klasyfikatorów będą sprawdzać i oceniać komunikaty z liczbą wyrazów wynoszącą sześć lub więcej. Komunikaty zawierające mniej niż sześć wyrazów nie są oceniane w zasadach przy użyciu klasyfikatorów. Aby zidentyfikować i podjąć działania w przypadku krótszych komunikatów zawierających nieodpowiednią zawartość, zalecamy dołączenie niestandardowego słownika słów kluczowych do monitorowania zasad zgodności komunikacji dla tego typu zawartości.

### <a name="optical-character-recognition-ocr"></a>Optyczne rozpoznawanie znaków (OCR)

Skonfiguruj wbudowane lub niestandardowe zasady zgodności komunikacji, aby skanować i identyfikować drukowany lub odręczny tekst z obrazów, które mogą być nieodpowiednie w organizacji. Zintegrowane [usługi Azure Cognitive Services i obsługa skanowania optycznego](/azure/cognitive-services/computer-vision/overview-ocr) na potrzeby identyfikowania tekstu na obrazach ułatwiają analitykom i badaczom wykrywanie wystąpień, w których w komunikacji, która jest przede wszystkim nietekstowa, można pominąć niewłaściwe zachowanie.

Możesz włączyć optyczne rozpoznawanie znaków (OCR) w nowych zasadach z szablonów, zasad niestandardowych lub zaktualizować istniejące zasady, aby rozszerzyć obsługę przetwarzania osadzonych obrazów i załączników. Po włączeniu zasad utworzonych na podstawie szablonu zasad automatyczne skanowanie jest obsługiwane w przypadku obrazów osadzonych lub dołączonych w wiadomościach e-mail i Microsoft Teams wiadomościach czatu. W przypadku obrazów osadzonych w plikach dokumentów skanowanie OCR nie jest obsługiwane. W przypadku zasad niestandardowych w zasadach należy skonfigurować co najmniej jedno ustawienie warunkowe skojarzone ze słowami kluczowymi, wbudowane klasyfikatory lub typy informacji poufnych, aby umożliwić wybór skanowania OCR.

Obrazy z zakresu od 50 KB do 4 MB w następujących formatach obrazów są skanowane i przetwarzane:

- .jpg/.jpeg (wspólna grupa ekspertów fotograficznych)
- .png (przenośna grafika sieciowa)
- .bmp (mapa bitowa)
- .tiff (format pliku obrazu tagu)
- .pdf (przenośny format dokumentu)

> [!NOTE]
> Skanowanie i wyodrębnianie osadzonych i dołączonych obrazów .pdf jest obecnie obsługiwane tylko w przypadku wiadomości e-mail.

Podczas przeglądania oczekujących alertów dla zasad z włączoną funkcją OCR obrazy zidentyfikowane i dopasowane do warunków zasad są wyświetlane jako elementy podrzędne skojarzonych alertów. Oryginalny obraz można wyświetlić, aby ocenić zidentyfikowany tekst w kontekście z oryginalną wiadomością. Może upłynąć do 48 godzin, aż wykryte obrazy będą dostępne z alertami.

### <a name="conditional-settings"></a>Ustawienia warunkowe
<a name="ConditionalSettings"> </a>

Warunki, które wybierzesz dla zasad, dotyczą komunikacji zarówno ze źródeł poczty e-mail, jak i innych firm w organizacji (na przykład z witryny Instant Bloomberg).

W poniższej tabeli wyjaśniono więcej na temat każdego warunku.

|**Warunek**|**Jak używać tego warunku**|
|:-----|:-----|
| **Zawartość pasuje do dowolnego z tych klasyfikatorów** | Zastosuj do zasad, gdy wszystkie klasyfikatory zostaną uwzględnione lub wykluczone w komunikacie. Niektóre klasyfikatory są wstępnie zdefiniowane w dzierżawie, a klasyfikatory niestandardowe muszą być skonfigurowane oddzielnie, zanim będą dostępne dla tego warunku. Tylko jeden klasyfikator można zdefiniować jako warunek w zasadach. Aby uzyskać więcej informacji na temat konfigurowania klasyfikatorów, zobacz [Learn about trainable classifiers (wersja zapoznawcza)](classifier-learn-about.md). |
| **Zawartość zawiera dowolny z tych poufnych typów informacji** | Zastosuj do zasad, gdy wszystkie typy informacji poufnych zostaną uwzględnione lub wykluczone w komunikacie. Niektóre klasyfikatory są wstępnie zdefiniowane w dzierżawie, a klasyfikatory niestandardowe można skonfigurować oddzielnie lub w ramach procesu przypisywania warunku. Każdy wybrany typ informacji poufnych jest stosowany oddzielnie i tylko jeden z tych typów informacji poufnych musi mieć zastosowanie do zasad, które mają zostać zastosowane do komunikatu. Aby uzyskać więcej informacji na temat niestandardowych typów informacji poufnych, zobacz [Dowiedz się więcej o typach informacji poufnych](sensitive-information-type-learn-about.md). |
| **Komunikat jest odbierany z dowolnej z tych domen**  <br><br> **Komunikat nie jest odbierany z żadnej z tych domen** | Zastosuj zasady, aby uwzględnić lub wykluczyć określone domeny lub adresy e-mail w odebranych wiadomościach. Wprowadź każdą domenę lub adres e-mail i rozdziel wiele domen lub adresów e-mail przecinkami. Każda wprowadzona domena lub adres e-mail jest stosowana oddzielnie. Tylko jedna domena lub adres e-mail musi mieć zastosowanie do tej wiadomości. <br><br> Jeśli chcesz zeskanować wszystkie wiadomości e-mail z określonej domeny, ale chcesz wykluczyć wiadomości, które nie wymagają przeglądu (biuletyny, anonsy itd.), musisz skonfigurować, że **wiadomość nie jest odbierana z żadnego z tych warunków domeny** , który wyklucza adres e-mail (na przykład "newsletter@contoso.com"). |
| **Wiadomość jest wysyłana do dowolnej z tych domen**  <br><br> **Komunikat nie jest wysyłany do żadnej z tych domen** | Zastosuj zasady, aby uwzględnić lub wykluczyć określone domeny w wysłanych komunikatach. Wprowadź każdą domenę i oddziel wiele domen przecinkiem. Każda domena jest stosowana oddzielnie, tylko jedna domena musi mieć zastosowanie do zasad, które mają zostać zastosowane do komunikatu. <br><br> Jeśli chcesz wykluczyć wszystkie wiadomości e-mail wysyłane do dwóch określonych domen, skonfiguruj, aby **komunikat nie był wysyłany do żadnej z tych domen** z dwiema domenami (na przykład "contoso.com,wingtiptoys.com"). |
| **Komunikat jest klasyfikowany przy użyciu dowolnej z tych etykiet**  <br><br> **Komunikat nie jest klasyfikowany przy użyciu żadnej z tych etykiet** | Aby zastosować zasady, gdy niektóre etykiety przechowywania zostaną uwzględnione lub wykluczone w komunikacie. Etykiety przechowywania muszą być skonfigurowane oddzielnie i skonfigurowane etykiety są wybierane jako część tego warunku. Każda wybrana etykieta jest stosowana oddzielnie (tylko jedna z tych etykiet musi być stosowana w celu zastosowania zasad do komunikatu). Aby uzyskać więcej informacji na temat etykiet przechowywania, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).|
| **Komunikat zawiera dowolne z tych słów**  <br><br> **Komunikat nie zawiera żadnego z tych słów** | Aby zastosować zasady, gdy niektóre wyrazy lub frazy zostaną uwzględnione lub wykluczone w komunikacie, wprowadź każde słowo oddzielone przecinkiem. W przypadku fraz z co najmniej dwoma wyrazami użyj cudzysłowów wokół frazy. Każdy wprowadzony wyraz lub fraza jest stosowana oddzielnie (tylko jeden wyraz musi mieć zastosowanie do zasad, które mają zostać zastosowane do wiadomości). Aby uzyskać więcej informacji na temat wprowadzania słów lub fraz, zobacz następną sekcję [Dopasowywanie wyrazów i fraz do wiadomości e-mail lub załączników](communication-compliance-policies.md#Matchwords).|
| **Załącznik zawiera dowolne z tych wyrazów**  <br><br> **Załącznik nie zawiera żadnego z tych słów** | Aby zastosować zasady, gdy niektóre wyrazy lub frazy są dołączone lub wykluczone w załączniku wiadomości (na przykład w dokumencie programu Word), wprowadź każde słowo oddzielone przecinkiem. W przypadku fraz z co najmniej dwoma wyrazami użyj cudzysłowów wokół frazy. Każde wprowadzone wyrazy lub frazy są stosowane oddzielnie (tylko jeden wyraz musi mieć zastosowanie do zasad, które mają zostać zastosowane do załącznika). Aby uzyskać więcej informacji na temat wprowadzania słów lub fraz, zobacz następną sekcję [Dopasowywanie wyrazów i fraz do wiadomości e-mail lub załączników](communication-compliance-policies.md#Matchwords).|
| **Załącznik to dowolny z tych typów plików**  <br><br> **Załącznik nie jest żadnym z tych typów plików** | Aby nadzorować komunikację, która zawiera lub wyklucza określone typy załączników, wprowadź rozszerzenia plików (takie jak .exe lub .pdf). Jeśli chcesz dołączyć lub wykluczyć wiele rozszerzeń plików, wprowadź typy plików oddzielone przecinkami (na przykład *.exe,.pdf,.zip*). Aby zasady zostały zastosowane, musi być zgodne tylko jedno rozszerzenie załącznika.|
| **Rozmiar komunikatu jest większy niż**  <br><br> **Rozmiar komunikatu nie jest większy niż** | Aby przejrzeć komunikaty na podstawie określonego rozmiaru, użyj tych warunków, aby określić maksymalny lub minimalny rozmiar komunikatu, zanim będzie podlegał przeglądowi. Na przykład jeśli określisz **rozmiar komunikatu jest większy niż** \> **1,0 MB**, wszystkie komunikaty o rozmiarze 1,01 MB i większym podlegają przeglądowi. Dla tego warunku możesz wybrać bajty, kilobajty, megabajty lub gigabajty.|
| **Załącznik jest większy niż**  <br><br> **Załącznik nie jest większy niż** | Aby przejrzeć komunikaty na podstawie rozmiaru ich załączników, określ maksymalny lub minimalny rozmiar załącznika przed przesłaniem wiadomości i jej załącznikami. Jeśli na przykład określisz, że **załącznik jest większy niż** \> **2,0 MB**, wszystkie komunikaty z załącznikami 2,01 MB i nowszymi będą podlegać przeglądowi. Dla tego warunku możesz wybrać bajty, kilobajty, megabajty lub gigabajty.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Dopasowywanie wyrazów i fraz do wiadomości e-mail lub załączników
<a name="Matchwords"> </a>

Każde słowo wprowadzone i oddzielone przecinkiem jest stosowane oddzielnie (tylko jeden wyraz musi mieć zastosowanie do warunku zasad, który ma zostać zastosowany do wiadomości e-mail lub załącznika). Na przykład użyjemy tego warunku, **komunikat zawiera dowolne z tych słów**, ze słowami kluczowymi "bankier", "poufne" i "insider trading" oddzielone przecinkiem (bankier, poufne,"insider trading"). Zasady te mają zastosowanie do wszelkich komunikatów zawierających słowo "bankier", "poufne" lub frazę "insider trading". Aby ten warunek zasad został zastosowany, musi wystąpić tylko jeden z tych słów lub fraz. Słowa w wiadomości lub załączniku muszą dokładnie odpowiadać wprowadzaniu.

> [!IMPORTANT]
>
> Podczas importowania pliku słownika niestandardowego każde słowo lub fraza muszą być oddzielone powrotem karetki i w osobnym wierszu. Przykład:
>
> *Bankier* <br>
> *Poufne* <br>
> *insider trading*

Aby skanować wiadomości e-mail i załączniki dla tych samych słów kluczowych, utwórz [niestandardowy słownik słów kluczowych](create-a-keyword-dictionary.md) dla terminów, które chcesz skanować w wiadomościach. Ta konfiguracja zasad identyfikuje zdefiniowane słowa kluczowe, które są wyświetlane w wiadomości e-mail **lub** w załączniku wiadomości e-mail. Używanie standardowych ustawień zasad warunkowych (*komunikat zawiera dowolne z tych słów* , a *załącznik zawiera dowolne z tych słów*) do identyfikowania terminów w komunikatach i w załącznikach wymaga, aby terminy były obecne **ZARÓWNO** w wiadomości, jak i w załączniku.

#### <a name="enter-multiple-conditions"></a>Wprowadź wiele warunków

Jeśli wprowadzisz wiele warunków, Microsoft 365 użyje wszystkich warunków razem, aby określić, kiedy zastosować zasady zgodności komunikacji do elementów komunikacji. Podczas konfigurowania wielu warunków wszystkie warunki muszą być spełnione, aby zasady zostały zastosowane, chyba że wprowadzisz wyjątek. Na przykład potrzebne są zasady, które mają zastosowanie, jeśli komunikat zawiera słowo "trade" i jest większy niż 2 MB. Jeśli jednak komunikat zawiera również wyrazy "Approved by Contoso financial", zasady nie powinny mieć zastosowania. W tym przykładzie trzy warunki zostałyby zdefiniowane w następujący sposób:

- **Komunikat zawiera dowolne z tych słów** ze słowem kluczowym "trade"
- **Rozmiar komunikatu jest większy niż** o wartości 2 MB
- **Komunikat nie zawiera żadnego z tych słów** ze słowami kluczowymi "Approved by Contoso financial team" (Zatwierdzone przez zespół finansowy firmy Contoso)

### <a name="review-percentage"></a>Przejrzyj procent

Jeśli chcesz zmniejszyć ilość zawartości do przejrzenia, możesz określić procent wszystkich komunikacji podlegających zasadom zgodności komunikacji. Losowa próbka zawartości w czasie rzeczywistym jest wybierana z łącznej wartości procentowej zawartości zgodnej z wybranymi warunkami zasad. Jeśli chcesz, aby recenzenci przeglądali wszystkie elementy, możesz skonfigurować **100%** w zasadach zgodności komunikacji.

## <a name="alert-policies"></a>Zasady alertów

Po skonfigurowaniu zasad odpowiednie zasady alertów są tworzone automatycznie i są generowane alerty dla komunikatów zgodnych z warunkami zdefiniowanymi w zasadach. Może upłynąć do 24 godzin od rozpoczęcia tworzenia zasad, aby otrzymywać alerty ze wskaźników aktywności. Domyślnie wszystkie zasady zgodne z wyzwalaczami alertów mają przypisany poziom ważności średniej w skojarzonych zasadach alertów. Alerty są generowane dla zasad zgodności komunikacji po osiągnięciu poziomu progu wyzwalacza agregacji w skojarzonych zasadach alertów. Pojedyncze powiadomienie e-mail jest wysyłane raz na 24 godziny dla wszystkich alertów, niezależnie od liczby pojedynczych komunikatów zgodnych z warunkami zasad. Na przykład firma Contoso ma włączone zasady nieodpowiedniej zawartości i od 1 stycznia było 100 dopasowań zasad, które wygenerowały sześć alertów. Pojedyncze powiadomienie e-mail dotyczące sześciu alertów jest wysyłane pod koniec 1 stycznia.

W przypadku zasad zgodności z komunikacją domyślnie skonfigurowano następujące wartości zasad alertów:

|**Wyzwalacz zasad alertów**|**Wartość domyślna**|
|:-----|:-----|
| Agregacja | Agregacja prosta |
| Próg | Domyślne: 4 działania <br> Minimum: 3 działania <br> Maksymalna liczba działań: 2 147 483 647 |
| Okno | Wartość domyślna: 60 minut <br> Minimum: 60 minut <br> Maksymalnie: 10 000 minut |

> [!NOTE]
> Ustawienia wyzwalacza progu zasad alertów dla działań obsługują minimalną wartość co najmniej 3 dla zasad zgodności komunikacji.

Możesz zmienić domyślne ustawienia wyzwalaczy dla liczby działań, okresu dla działań i dla określonych użytkowników w zasadach alertów na stronie **Zasady alertów** w portal zgodności Microsoft Purview.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Zmienianie poziomu ważności dla zasad alertów

Jeśli chcesz zmienić poziom ważności przypisany w zasadach alertów dla określonych zasad zgodności komunikacji, wykonaj następujące kroki:

1. Zaloguj się [do portal zgodności Microsoft Purview](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji Microsoft 365.

2. W portal zgodności Microsoft Purview przejdź do pozycji **Zasady**.

3. Wybierz **pozycję Office 365 alert** na stronie **Zasady**, aby otworzyć stronę **Zasady alertów**.

4. Zaznacz pole wyboru dla zasad zgodności komunikacji, które chcesz zaktualizować, a następnie wybierz pozycję **Edytuj zasady**.

5. Na karcie **Opis** wybierz listę **rozwijaną Ważność** , aby skonfigurować poziom alertu zasad.

6. Wybierz pozycję **Zapisz** , aby zastosować nowy poziom ważności do zasad.

7. Wybierz pozycję **Zamknij** , aby zamknąć stronę szczegółów zasad alertów.
