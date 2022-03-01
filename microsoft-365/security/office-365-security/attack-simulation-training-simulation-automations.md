---
title: Automatyzacje symezyjne dla szkolenia z symezyjną ataków
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorzy mogą dowiedzieć się, jak tworzyć zautomatyzowane symulacje zawierające określone techniki i łady uruchamiane po spełnionych określonych warunkach w programie Microsoft Defender Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: a7b49baf23734bccf42df8215e384593ad48d30a
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014856"
---
# <a name="simulation-automations-for-attack-simulation-training"></a>Automatyzacje symezyjne dla szkolenia z symezyjną ataków

**Dotyczy programu** [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)

Aby uzyskać informacje na temat szkolenia z symezyjną ataków, zobacz Wprowadzenie do szkolenia z użyciem [symezyjny](attack-simulation-training-get-started.md) ataków.

Aby utworzyć automatyzację symulacyjna, wykonaj następujące czynności:

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com/>adresem ,  \>  \> przejdź do karty & szkolenia symulacyjnego z atakami **i** symezyjną.

   Aby przejść bezpośrednio do karty **Automatyzacje symulacyjne** , użyj klawisza <https://security.microsoft.com/attacksimulator?viewid=simulationautomation>.

2. Na karcie **Automatyzacje symulacyjne** wybierz pozycję Utwórz ![ikonę automatyzacji.](../../media/m365-cc-sc-create-icon.png) **Tworzenie automatyzacji**.

   ![Przycisk automatyzacji utwórz na karcie Automatyzacja symulacyjna w szkoleniu symezyjny ataków w portalu Microsoft 365 Defender zaawansowanej.](../../media/attack-sim-training-sim-automations-create.png)

3. Zostanie otwarty kreator tworzenia. W dalszej części tego artykułu opisano strony i ustawienia, które zawierają.

> [!NOTE]
> W dowolnym momencie kreatora tworzenia symulacyjnej możesz kliknąć przycisk **Zapisz** i zamknij, aby zapisać postęp i kontynuować konfigurowanie symulacyjnej później. W czasie nieukończonej **symulacyjnej wartości stanowej** **na** **karcie Symulatory** . Możesz wybrać miejsce, w którym zostało to pozostawione, wybierając symululę i klikając ikonę ![Edytuj symululę.](../../media/m365-cc-sc-edit-icon.png) **Symulacja** edycji.## Nazwa i opisz symulowanie.

## <a name="name-and-describe-the-simulation-automation"></a>Nazywanie i opisywanie automatyzacji symulacyjnej

Na stronie **Nazwa automatyzacji** skonfiguruj następujące ustawienia:

- **Nazwa**: Wprowadź unikatową nazwę opisową dla symulacyjnej.
- **Opis**. Wprowadź opcjonalny szczegółowy opis symulowania.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="select-one-or-more-social-engineering-techniques"></a>Wybieranie jednej lub większej liczby technik społecznościowych

Na stronie **Wybieranie technik społecznościowych** wybierz jedną lub więcej z dostępnych technik socjograficznych, które zostały przejmowane na podstawie struktury [MITRE ATT&CK®](https://attack.mitre.org/techniques/enterprise/). Różne łady są dostępne dla różnych technik. Dostępne są następujące techniki społecznościowe:

- **Zbieranie poświadczeń**. Próbuje zbierać poświadczenia przez wprowadzenie nazwy użytkownika i hasła do dobrze znanej witryny internetowej z polami wprowadzania.
- **Załącznik w złośliwym** oprogramowaniu: powoduje dodanie złośliwego załącznika do wiadomości. Gdy użytkownik otworzy załącznik, zostanie uruchomiony dowolny kod, który pomoże intruzowi naruszyć urządzenie docelowe.
- **Link w załączniku**: typ środowiska hybrydowego zbierania poświadczeń. Atakujący wstawia adres URL do załącznika wiadomości e-mail. Adres URL w załączniku jest zgodny z techniką zbioru poświadczeń.
- **Link do złośliwego oprogramowania**: uruchamia dowolny kod z pliku hostowanej w dobrze znanej usłudze udostępniania plików. Wiadomość wysłana do użytkownika będzie zawierać link do tego złośliwego pliku. Otwarcie pliku i pomoc osobie atakującej w naruszoniu urządzenia docelowego.
- **Adres URL** dysku: złośliwy adres URL w wiadomości przenosi użytkownika do znanej witryny sieci Web, która po cichu uruchamia i/lub instaluje kod na urządzeniu użytkownika.

Kliknięcie linku **Wyświetl szczegóły** w opisie spowoduje otwarcie wysuwu szczegółów, opisujące technikę i kroki symulacyjne wynikające z tej techniki.

![Wysuwające szczegółowe informacje dotyczące techniki poświadczeń chyłej na stronie Wybieranie technik społecznościowych.](../../media/attack-sim-training-simulations-select-technique-sim-steps.png)

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="select-payloads"></a>Wybierz łady

Na **stronie Wybierz ładowania** wybierz jedną z następujących opcji:

- **Wybierz ręcznie**
- **Randomizuj**

Jeśli wybierzesz **pozycję Losowo**, na tej stronie nie ma nic do skonfigurowania, więc kliknij przycisk **Dalej** , aby kontynuować.

Jeśli **wybierzesz pozycję Ręcznie**, musisz wybrać jeden lub więcej ładów z listy. Wyświetlane są następujące informacje, które pomogą Ci wybrać:

- **Nazwaładuj**
- **Technika**: Należy wybrać co najmniej jeden ład według techniki wybranej na poprzedniej stronie.
- **Język**: język zawartości ładu. Katalog ładów firmy Microsoft (globalna) udostępnia  payloads w ponad 10 językach, które można również filtrować.
- **Szybkość klikania**: ile osób kliknąło ten ład.
- **Przewidywana szybkość naruszenia**: dane historyczne obciążenia na poziomie Microsoft 365, które przewiduje procent osób, które zostaną naruszone przez ten ład.
- **Uruchomiono symeony** i zlicza, ile razy ten ład został użyty w innych symulacyjnych.

Na ikonie ![wyszukiwania.](../../media/m365-cc-sc-search-icon.png) **Pole** wyszukiwania, możesz wpisać część nazwy ładowania i nacisnąć klawisz Enter, aby przefiltrować wyniki.

Jeśli klikniesz **pozycję Filtruj**, dostępne są następujące filtry:

- **Złożoność**: Obliczona na podstawie liczby wskaźników w zbędnych wynikach możliwych ataków (błędy pisowni, pilność itp.). Więcej wskaźników jest łatwiejsze do zidentyfikowania jako atak i wskazuje niższą złożoność. Dostępne wartości:
  - **Niska**
  - **Średni**
  - **High (Wysoki)**
- **Źródło**: wskazuje, czy ład został utworzony w organizacji, czy jest częścią istniejącego katalogu ładów firmy Microsoft. Prawidłowe wartości to:
  - **Globalna**
  - **Dzierżawca**
  - **Wszystkie**
- Język **: Dostępne** **wartości: angielski**, **hiszpański, niemiecki****, japoński,** **francuski,** **portugalski****, holenderski****, włoski****, szwedzki**, **chiński (****uproszczony), norweski bokmål****, polski****, rosyjski,** **fiński,** **koreański,** **turecki,** węgierski, **hebrajski**, **tajski**, **arabski**, **wietnamski****, słowacki**, **grecki**, **indonezyjski**, **rumuński**, **słoweński**, **chorwacki**, **kataloński** **i inny**.
- **Dodawanie tagów**
- **Filtruj** według motywu **: Dostępne** wartości: Aktywacja **konta, Weryfikacja** **konta, Rozliczenia****,** Oczyszczanie **poczty,** Odebrano dokument, **Koszt**, **Faks****, Raport** **finansowy, Wiadomości** przychodzące, Faktura **,** Odebrane **elementy,** **Alert logowania****,** Otrzymano **pocztę**, Hasło, **Płatność**, **Płace**, **Spersonalizowana oferta****,** Kwarantanna, **Praca zdalna**, **Przejrzenie wiadomości**, **Aktualizacja** **zabezpieczeń, Usługa** zawieszona, Podpis **wymagany**, Uaktualnij magazyn skrzynki pocztowej **Weryfikowanie** skrzynki pocztowej, **Poczta głosowa** i **Inne**.
- Filtruj według **marki: Dostępne** wartości to: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid, Title** Title, **Tesco**, **Wells Fargo**, **Syrinx Cloud** i **inne**.
- **Filtruj** według branży: Dostępne **wartości to:** Bankowość **, Usługi** **biznesowe, Usługi** dla klientów **indywidualnych, Edukacja****, Energy****,** Konsygnacja, **Consulting**, Usługi **finansowe**, **Rząd**, **Jednak**, **Ubezpieczenia**, **Prawne**, **Courier services**, **IT****, Opieka** zdrowotna **, Produkcja**, **Sprzedaż** detaliczna, **Telecom**, **Nieruchomości**, i **Inne**.
- **Bieżące zdarzenie**: Dostępne wartości to **Tak** lub **Nie**.
- **Wymierne**: Dostępne wartości to **Tak** lub **Nie**.

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj,** **Anuluj** lub **Wyczyść filtry**.

W przypadku wybrania ładu z listy przez kliknięcie nazwy szczegóły dotyczące ładów są wyświetlane w wysuwanych informacjach:

- Karta **Przegląd** zawiera przykład i inne szczegóły dotyczące ładu.
- Karta **Uruchomiono symulatory** zawiera nazwę **symulacyjnej**, **szybkość** klikania, **naruszone tempo** i **działanie**.

![Wysuwowe informacje o szczegółach ładowania w szkoleniu symulacyjnych ataków w Microsoft 365 Defender sieci Microsoft 365 Defender sieci.](../../media/attack-sim-training-simulations-select-payload-details.png)

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="target-users"></a>Użytkownicy docelowi

Na stronie **Użytkownicy docelowi** wybierz osoby, które otrzymają symulowanie. Skonfiguruj jedno z następujących ustawień:

- **Uwzględnij wszystkich użytkowników w organizacji**: użytkownicy, których dotyczy problem, są pokazywani na listach z 10. Do przewijania **listy możesz** **użyć** przycisków Następny i Poprzedni bezpośrednio poniżej listy użytkowników. Możesz również użyć ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Ikona** wyszukiwania na stronie w celu znalezienia użytkowników, których dotyczy problem.
- **Uwzględnij tylko określonych użytkowników i grupy**: Wybierz jedną z następujących opcji:
  - ![Ikona Dodaj użytkowników.](../../media/m365-cc-sc-create-icon.png) **Dodawanie użytkowników**: **W wyświetlonym** wysuwanych czacie Dodawanie użytkowników możesz znaleźć użytkowników i grupy na podstawie następujących kryteriów:
    - **Użytkownicy lub grupy**: W ![ikony Wyszukaj użytkowników i grupy.](../../media/m365-cc-sc-search-icon.png) **Pole Wyszukaj użytkowników i** grupy umożliwia wpisanie części Nazwa lub Adres e-mail  użytkownika lub grupy, a następnie naciśnięcie klawisza Enter. Możesz wybrać niektóre lub wszystkie wyniki. Po zakończeniu kliknij pozycję **Dodaj x użytkowników**.

      > [!NOTE]
      > Kliknięcie **przycisku Dodaj filtry** w celu powrotu  do opcji Filtruj użytkowników według kategorii spowoduje wyczyszczenie wszystkich użytkowników lub grup wybranych w wynikach wyszukiwania.

    - **Filtrowanie użytkowników według kategorii**: Wybierz jedną z następujących opcji:
      - **Sugerowane grupy użytkowników**: Wybierz jedną z następujących wartości:
        - **Wszystkie sugerowane grupy użytkowników**
        - **Użytkownicy, którzy nie są docelowi w czasie symulacyjnej pracy w ciągu ostatnich trzech miesięcy**
        - **Powtarzanie czynności przez offenders**
      - **Dział**: Użyj następujących opcji:
        - **Wyszukiwanie**: Na ikonie ![Wyszukaj według działu.](../../media/m365-cc-sc-search-icon.png) **Pole Wyszukaj według** działu można wpisać część wartości Dział, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki.
        - Wybierz **pozycję Cały dział**
        - Wybierz istniejące wartości department (Dział).
      - **Tytuł**. Użyj następujących opcji:
        - **Wyszukiwanie**: Na ikonie ![Wyszukaj według tytułu.](../../media/m365-cc-sc-search-icon.png) **Pole Wyszukaj według** tytułu można wpisać część wartości Tytuł, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki.
        - **Zaznaczanie całego tytułu**
        - Wybierz istniejące wartości Title.

      ![Filtrowanie użytkowników na stronie Użytkownicy docelowi w szkoleniu z symezyjną ataków w portalu Microsoft 365 Defender sieci Web.](../../media/attack-sim-training-simulations-target-users-filter-by-category.png)

      Po zidentyfikowaniu kryteriów użytkownicy, których dotyczy problem, są pokazywani  w wyświetlonej sekcji Lista użytkowników, w której można wybrać niektórych lub wszystkich wykrytych adresatów.

      Po zakończeniu kliknij pozycję **Zastosuj(x),** a następnie kliknij pozycję **Dodaj użytkowników x**.

  Z powrotem na **stronie głównej Użytkownicy** docelowi możesz użyć ikony ![Wyszukiwania.](../../media/m365-cc-sc-search-icon.png) **Pole** wyszukiwania, aby znaleźć użytkowników, których dotyczy problem. Możesz również kliknąć ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń,** aby usunąć określonych użytkowników.

- ![Ikona Importuj.](../../media/m365-cc-sc-create-icon.png) **Importowanie**: W oknie dialogowym, które zostanie otwarte, określ plik CSV zawierający jeden adres e-mail w wierszu.

  Po odnalezieniu pliku CSV lista użytkowników zostanie zaimportowana i wyświetlona na stronie Użytkownicy **docelowi** . Możesz użyć ikony ![Wyszukiwania.](../../media/m365-cc-sc-search-icon.png) **Pole** wyszukiwania, aby znaleźć użytkowników, których dotyczy problem. Możesz również kliknąć ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń,** aby usunąć określonych użytkowników.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="assign-training"></a>Przypisywanie szkolenia

Na stronie **Przypisywanie** szkolenia możesz przypisać szkolenia dla symulacyjnej. Zaleca się przypisywanie szkoleń do każdej symulacyjnej sytuacji, ponieważ pracownicy, którzy przejdą szkolenie, są mniej podatni na podobne ataki. Dostępne są następujące ustawienia:

- **Wybierz preferencje dotyczące zawartości szkoleń**: Wybierz jedną z następujących opcji:
  - **Środowisko szkoleniowe firmy Microsoft**: Jest to wartość domyślna, która ma następujące skojarzone opcje konfigurowania:
    - Wybierz jedną z następujących opcji:
      - **Przypisz do mnie szkolenie**: jest to wartość domyślna i zalecana. Przypisujemy szkolenie na podstawie poprzedniej symulacyjnej oraz wyników szkolenia użytkownika. Możesz przejrzeć opcje w następnych krokach kreatora.
      - **Wybierz pozycję kursy** szkoleniowe i moduły samodzielnie. Jeśli wybierzesz tę wartość, w następnym kroku kreatora nadal będzie można wyświetlić zalecaną zawartość, a także wszystkie dostępne kursy i moduły.
    - **Termin realizacji**: Wybierz jedną z następujących wartości:
      - **30 dni po zakończeniu symulowania**: jest to wartość domyślna.
      - **15 dni po zakończeniu symulowania**
      - **7 dni po zakończeniu symulacyjnej pracy**
  - **Przekierowywanie do niestandardowego adresu URL**: Ta wartość ma następujące skojarzone opcje konfigurowania:
    - **Niestandardowy adres URL szkolenia** (wymagany)
    - **Niestandardowa nazwa szkolenia** (wymagane)
    - **Niestandardowy opis szkolenia**
    - **Niestandardowy czas trwania szkolenia (w** minutach): Wartość domyślna to 0, co oznacza, że nie ma określonego czasu trwania szkolenia.
    - **Termin realizacji**: Wybierz jedną z następujących wartości:
      - **30 dni po zakończeniu symulowania**: jest to wartość domyślna.
      - **15 dni po zakończeniu symulowania**
      - **7 dni po zakończeniu symulacyjnej pracy**
  - **Brak szkolenia**: Jeśli wybierzesz tę wartość, jedyną opcją na stronie jest przycisk **Dalej, który** przenosi Cię do [**strony docelowej**](#landing-page) .

![Dodaj zalecane szkolenie na stronie Szkolenie dotyczące zadań do wykonania w trybie szkolenia symendacyjnego w portalu Microsoft 365 Defender ataków.](../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png)

### <a name="training-assignment"></a>Zadanie szkoleniowe

> [!NOTE]
> Strona **Zadania szkoleniowe jest** dostępna tylko w przypadku wybrania na poprzedniej stronie opcji Wybierz kursy szkoleniowe i moduły szkoleniowe firmy **Microsoft**\>.

Na stronie **Zadanie szkoleniowe** wybierz szkolenia, które chcesz dodać do symulacyjnej pracy, klikając ![ikonę Dodaj szkolenia.](../../media/m365-cc-sc-create-icon.png) **Dodaj szkolenia**.

W **wyświetlonym wysuwam** menu Dodaj szkolenie możesz wybrać szkolenia, których chcesz użyć, na następujących dostępnych kartach:

- **Karta** Zalecane: przedstawia zalecane wbudowane szkolenia na podstawie konfiguracji symulacyjnej. Są to te same szkolenia, które zostałyby przypisane, jeśli na poprzedniej stronie wybrano opcję **Przypisz** do mnie szkolenie.
- **Karta Wszystkie szkolenia** : Wyświetla wszystkie dostępne wbudowane szkolenia.

  Dla każdego szkolenia są wyświetlane następujące informacje:

  - **Nazwa szkolenia**
  - **Źródło**: wartość to **Global**.
  - **Czas trwania (miny)**
  - **Podgląd**: Kliknij przycisk **Podgląd** , aby wyświetlić szkolenie.

  Na ikonie ![wyszukiwania.](../../media/m365-cc-sc-search-icon.png) **Pole** wyszukiwania, możesz wpisać część nazwy szkolenia i nacisnąć klawisz Enter, aby przefiltrować wyniki na bieżącej karcie.

  Z bieżącej karty zaznacz wszystkie szkolenia, które chcesz uwzględnić, a następnie kliknij przycisk **Dodaj**.

Na głównej **stronie zadania szkoleniowego** są wyświetlane wybrane szkolenia. Dla każdego szkolenia są wyświetlane następujące informacje:

- **Nazwa szkolenia**
- **Źródło**
- **Czas trwania (miny)**

Dla każdego szkolenia z listy musisz wybrać, kto otrzymuje szkolenie, wybierając wartości w kolumnie **Przypisz do** :

- **Wszyscy użytkownicy**

  lub co najmniej jedną z następujących wartości:

- **Kliknął ład**
- **Naruszone**

Jeśli nie chcesz używać wyświetlonego szkolenia, kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

![Strona przydzielania szkoleń w szkoleniu z symezyjną ataków w portalu Microsoft 365 Defender sieci Web.](../../media/attack-sim-training-training-assignment.png)

Po zakończeniu kliknij przycisk **Dalej**.

### <a name="landing-page"></a>Strona docelowa

Na stronie **docelowej** możesz skonfigurować stronę sieci Web, do których użytkownik jest przekierowywowywny w przypadku otwarcia przez nich ładu w czasie symulacyjnej.

- **Wybieranie preferencji strony docelowej**: Dostępne wartości zależą od wcześniejszych wyborów na stronie Wybieranie ładowań zgodnie z opisem w poniższej tabeli:[](#select-payloads)

  <br>

  ****

  |Zaznaczenie na stronie Wybierz łady|Dostępne wartości dla preferencji Wybierz stronę docelową|
  |---|---|
  |Wybierz ręcznie|Użyj domyślnej strony startowej firmy Microsoft <p> Tworzenie własnej strony docelowej <p> Używanie niestandardowego adresu URL <p> **Uwaga**: wartość **Użyj niestandardowego adresu URL** nie jest dostępna, jeśli na stronie  Wybieranie technik społecznościowych wcześniej wybrano pozycję Załącznik złośliwego [oprogramowania lub](#select-one-or-more-social-engineering-techniques) **Link** do złośliwego oprogramowania.|
  |Randomizuj|Użyj domyślnej strony startowej firmy Microsoft|
  |

  Dostępne wartości **preferencji wybierz stronę docelową** i skojarzone z nimi ustawienia są opisane na poniższej liście:

  - **Użyj domyślnej strony startowej firmy Microsoft**. Jest to wartość domyślna, co powoduje, że do wszystkich ładów jest stosowana jedna domyślna akcja wskaźnika, logo i ładu firmy Microsoft.

    Na stronie docelowej musisz skonfigurować następujące **ustawienia** dodatkowe:

    - **Wybieranie układu strony docelowej**: wybierz jeden z 5 dostępnych szablonów stron startowych.
    - **Dodać logo**: Kliknij przycisk **Przeglądaj** , aby znaleźć i wybrać plik .png, jpeg lub .gif, aby dodać go do wszystkich ładów wybranych przez firmę Microsoft. Aby usunąć logo, kliknij przycisk **Usuń**.
    - **Wskaźniki ładowania**: To ustawienie jest niedostępne, jeśli na stronie Wybieranie technik społecznościowych wcześniej wybrano załącznik  złośliwego [oprogramowania lub](#select-one-or-more-social-engineering-techniques) link do złośliwego oprogramowania.

      Wybierz **pozycję Dodaj wskaźniki opłaty do wiadomości e-mail** , aby ułatwić użytkownikom identyfikowanie wiadomości wyłudzających informacje.

    Możesz wyświetlić podgląd wyników, klikając przycisk Otwórz **panel podglądu** na środku strony. W wyświetlonym wysuwanych oknie podglądu możesz użyć  opcji Wybierz ład, aby wyświetlić podgląd poszczególnych ładów.

  - **Utwórz własną stronę docelową**: Ta wartość powoduje utworzenie jednej akcji wskaźnika obciążenia, która zostanie zastosowana do wybranych ładowań.

    Na stronie docelowej musisz skonfigurować następujące **ustawienia** dodatkowe:

    - **Wskaźniki ładowania**: To ustawienie jest niedostępne, jeśli na stronie Wybieranie technik społecznościowych wcześniej wybrano załącznik  złośliwego [oprogramowania lub](#select-one-or-more-social-engineering-techniques) link do złośliwego oprogramowania.

      Wybierz **pozycję Dodaj wskaźniki opłaty do wiadomości e-mail** , aby ułatwić użytkownikom identyfikowanie wiadomości wyłudzających informacje.

    - Zawartość strony: Dostępne są dwie karty:

      - **Funkcje** tekstowe: Do utworzenia strony docelowej jest dostępny edytor tekstów sformatowanych. Oprócz typowych ustawień czcionki i formatowania dostępne są następujące ustawienia:
        - **Tag dynamiczny**: Wybierz z następujących tagów:
          - **Nazwa użytkownika**
          - **Nazwa nadawcy wiadomości e-mail**
          - **Adres e-mail nadawcy**
          - **Temat wiadomości e-mail**
          - **Zawartość wiadomości e-mail**
        - **Użyj z domyślnego**: Wybierz jeden z 5 dostępnych szablonów stron startowych, od których chcesz rozpocząć. Tekst i układ można zmodyfikować w obszarze edytowania. Aby przywrócić domyślny tekst i układ szablonu strony docelowej, kliknij pozycję **Resetuj do domyślnego.**
        - **Link do szkolenia**: W wyświetlonym oknie dialogowym Nazywanie adresu **URL** szkolenia wprowadź tytuł linku do szkolenia, a następnie kliknij  pozycję Potwierdź, aby dodać link do strony docelowej.
      - **Kod**: Możesz bezpośrednio wyświetlać i modyfikować kod HTML.

      Możesz wyświetlić podgląd wyników, klikając przycisk Otwórz **panel podglądu** na środku strony. W wyświetlonym wysuwanych oknie podglądu możesz użyć  opcji Wybierz ład, aby wyświetlić podgląd poszczególnych ładów.

  - **Użyj niestandardowego adresu URL**: Dodaj adres URL w **wyświetlonym polu Wprowadź adres URL** niestandardowej strony docelowej. Na stronie nie są dostępne żadne inne opcje.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="select-end-user-notification"></a>Wybierz powiadomienie użytkownika końcowego

Na stronie **Wybieranie powiadomienia użytkownika końcowego** wybierz jedną z następujących opcji powiadomień:

- **Nie dostarczaj powiadomień**: Kliknij **przycisk Kontynuuj** w wyświetlonym oknie dialogowym alertu. Jeśli wybierzesz tę opcję, kliknięcie przycisku Dalej spowoduje wybranie strony Harmonogram [symulowania](#simulation-schedule).

- **Powiadomienie domyślne firmy Microsoft (zalecane)**: Na stronie są dostępne następujące dodatkowe ustawienia:
  - **Wybierz język domyślny**: Dostępne wartości to: chiński **(** uproszczony), chiński (tradycyjny **),****angielski,** **francuski****, niemiecki****, włoski****, japoński**, **koreański**, **portugalski****, rosyjski****, hiszpański** i **holenderski**.
  - Domyślnie jedynym dostępnym powiadomieniem do wyboru jest powiadomienie **o dodatnich wiadomościach od firmy Microsoft**. W przypadku tego powiadomienia dostępne są następujące informacje:
    - **Powiadomienia** (nazwa): wartość to powiadomienie o dodatnich **wiadomościach po stronie dodatniej firmy Microsoft**.
    - **Język**: Jeśli powiadomienie zawiera wiele tłumaczeń, dwa pierwsze języki są wyświetlane bezpośrednio. Aby wyświetlić pozostałe języki, umieść wskaźnik myszy na ikonie numerycznej (na przykład **+10**).
    - **Typ**: Wartość jest **dodatnia**.
    - **Preferencje dostarczania**: Wybierz jedną z następujących wartości:
      - **Nie dostarczaj**
      - **Dostarczanie po zakończeniu kampanii**
      - **Dostarczanie w trakcie kampanii**
    - **Dostarczanie do**: Wartość nie **ma zastosowania**.
    - **Akcje**: Kliknięcie ikony ![Widok.](../../media/m365-cc-sc-view-icon.png) **Ikona** Widok; zostanie **wyświetlona strona z** powiadomieniem Recenzja z następującymi informacjami:
      - **Karta** Podgląd: Wyświetlanie komunikat z powiadomieniem. Aby wyświetlić wiadomość w różnych językach, użyj **pola Wybierz** język.
      - **Karta** Szczegóły: Wyświetl szczegóły powiadomienia:
        - **Opis powiadomienia**
        - **Źródło**: W przypadku wbudowanych powiadomień wartość to **Global**. W przypadku powiadomień niestandardowych wartość to **Dzierżawa**.
        - **Typ powiadomienia**
        - **Zmodyfikowane przez**
        - **Ostatnia modyfikacja**

        Po zakończeniu kliknij przycisk **Zamknij**.

  Jeśli wybierzesz tę opcję, kliknięcie przycisku Dalej spowoduje wybranie strony Harmonogram [symulowania](#simulation-schedule).

- **Dostosowane powiadomienia dla użytkowników** końcowych: Po kliknięciu przycisku **Dalej** jest przekierowywana strona powiadomień o dodatnich wiadomościach **,** zgodnie z opisem w następnej sekcji, w której można wybrać istniejące powiadomienia lub utworzyć nowe powiadomienia.

Po zakończeniu kliknij przycisk **Dalej**.

### <a name="positive-reinforcement-notification"></a>Powiadomienie o dodatnich wiadomościach dodatnich

Strona **powiadomień o dodatnich wiadomościach** jest dostępna tylko w przypadku, **gdy na** poprzedniej stronie wybrano opcję Niestandardowe powiadomienia dla użytkowników końcowych.

- **Preferencje dostarczania**: Wybierz jedną z następujących wartości:
  - **Nie dostarczaj**
  - **Dostarczanie po zrzucie przez użytkownika informacji o wyłudzeniu informacji i zakończeniu kampanii**
  - **Dostarczanie natychmiast po zgłosce użytkownika o wyłudzeniu informacji**

- **Wybierz powiadomienie dodatnie powiadomienie z powiadomieniem**: Możesz wybrać istniejące powiadomienie lub utworzyć nowe powiadomienie o typie Powiadomienie dodatnie **przesłone do** użycia:
  - Aby wybrać istniejące powiadomienie, kliknij pusty obszar obok nazwy powiadomienia. Jeśli klikniesz nazwę powiadomienia, zostanie zaznaczone powiadomienie i zostanie wyświetlone wysuwne okno podglądu. Aby usunąć zaznaczenie powiadomienia, wyczyść pole wyboru obok powiadomienia.
  - Aby wyszukać istniejące powiadomienie, użyj ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole** wyszukiwania, aby wyszukać nazwę.
  - Aby utworzyć nowe powiadomienie, kliknij pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nowy**.
  - Aby zmodyfikować istniejące powiadomienie niestandardowe, zaznacz je, a następnie kliknij pozycję ![Edytuj ikonę powiadomienia.](../../media/m365-cc-sc-edit-icon.png) **Edytuj powiadomienie**.

#### <a name="create-new-notification-wizard"></a>Tworzenie nowego kreatora powiadomień

Jeśli kliknąłem pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nowe** na stronie **powiadomień Po dodatnich wiadomościach** , zostanie otwarty kreator tworzenia powiadomień.

Czynności tworzenia są identyczne, jak opisano w [tece Tworzenie powiadomień dla użytkowników końcowych](attack-simulation-traning-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> Na stronie **Definiowanie szczegółów** upewnij się, że dla opcji Wybierz typ powiadomień wybierz wartość Powiadomienie o dodatnim **przesłoceniu**. Nie zaznaczaj powiadomień **symulacyjnych**.

Po zakończeniu wracasz do strony powiadomień o dodatnich przechowach, gdzie właśnie utworzone powiadomienie jest wyświetlane na liście powiadomień Wybierz dodatnią  przechłodę.

- Aby utworzyć nowe powiadomienie, kliknij pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png).
- Aby zmodyfikować powiadomienie lub dodać dodatkowe tłumaczenia, wybierz powiadomienie z listy, a następnie kliknij ikonę ![Edytuj powiadomienie.](../../media/m365-cc-sc-edit-icon.png) **Edytuj powiadomienie,** aby uruchomić kreatora powiadomień w sposób opisany wcześniej (gdy większość wartości jest już wypełniona). Jeśli powiadomienie zawiera już tłumaczenia dla 12 obsługiwanych języków, nie możesz dodać więcej tłumaczeń.

Wybierz powiadomienie, którego chcesz użyć, a następnie kliknij przycisk **Dalej**.

## <a name="simulation-schedule"></a>Harmonogram symulowania

Na stronie **Harmonogram symulowania** wybierz jedną z następujących wartości:

- **Losowo**: nadal trzeba wybrać harmonogram na następnej stronie, ale wraz z harmonogramem będą one rozpoczynane w losowych godzinach.
- **Naprawione**

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="schedule-details"></a>Szczegóły harmonogramu

Informacje na stronie Szczegóły harmonogramu  zależą od tego, czy wybrano opcję **Randomized** (Losowo), czy **Fixed** (Stała) na poprzedniej stronie.

- **Losowo**: Dostępne są następujące ustawienia:
  - **Sekcja rozpoczęcia symulowania** : Konfigurowanie następującego ustawienia:
    - **Wybierz datę, od której mają się zaczynać symulowania**
  - **Sekcja zakresu symulacyjnego** : Konfigurowanie następujących ustawień:
    - **Wybierz dni tygodnia, od których** mogą rozpoczynać się symulowania: Wybierz jeden lub więcej dni tygodnia.
    - **Wprowadź maksymalną liczbę symulowań, które mogą być** rozpoczęte między datą rozpoczęcia i zakończenia: Wprowadź wartość z od 1 do 10.
    - **Randomize czasu wysyłania**: zaznacz to ustawienie, aby losowo określać czas wysyłania.
  - **Sekcja zakończenia symulowania** : Konfigurowanie następującego ustawienia:
    - **Wybierz datę, do której mają się zakończyć symulowania**

- **Rozwiązano**: Dostępne są następujące ustawienia:
  - **Sekcja rozpoczęcia symulowania** : Konfigurowanie następującego ustawienia:
    - **Wybierz datę, od której mają się zaczynać symulowania**
  - **Sekcja cyklu** symezyjnego: Konfigurowanie następujących ustawień:
    - **Wybierz, czy mają być uruchamiane cotygodniowe** czy miesięczne czasy symulacyjne: Wybierz jedną z następujących wartości:
      - **Co tydzień**: jest to wartość domyślna.
      - **Co miesiąc**
    - **Wprowadź, jak często mają** się powtarzać czasy symulacyjne w tygodniach: Wprowadź wartość z od 1 do 99 tygodni.
    - **Wybierz dzień tygodnia, od którego mają się rozpoczynać symulowania**
  - **Sekcja zakończenia symulowania** : Wybór jednej z następujących wartości:
    - **Wybierz datę, do której mają się zakończyć symulowania**
    - **Wprowadź liczbę wystąpień symulowań**, które mają być uruchamiane przed zakończeniem: Wprowadź wartość z od 1 do 10.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="launch-details"></a>Szczegóły uruchamiania

Na stronie **Szczegóły uruchamiania** skonfiguruj następujące dodatkowe ustawienia automatyzacji:

- **Korzystanie z unikatowych ładowań w ramach automatyzacji**: domyślnie to ustawienie nie jest zaznaczone.
- **Ustawiać docelowych użytkowników powtarzających** się: to ustawienie nie jest domyślnie zaznaczone. Jeśli ją wybierzesz, skonfiguruj następujące ustawienie, które zostanie wyświetlone:
  - **Wprowadź maksymalną liczbę zadań, na które** użytkownik może być skierowany w ramach tej automatyzacji: Wprowadź wartość z zakresu od 1 do 10.
- **Wysyłaj symezyjną** pocztę e-mail na podstawie bieżącego ustawienia strefy czasowej użytkownika z aplikacji Outlook sieci Web: Domyślnie to ustawienie nie jest zaznaczone.
- **Wyświetl stronę** pochyłana danych w programie **Drive-by** technique: To ustawienie jest dostępne tylko wtedy, gdy wybrano pozycję Adres URL Według dysku na stronie Wybieranie technik **[społecznościowych](#select-one-or-more-social-engineering-techniques)** . Domyślnie to ustawienie jest włączone (![ikona Włącz](../../media/scc-toggle-on.png)).

## <a name="review-simulation-automation"></a>Automatyzacja przeglądania symezyjna

Na stronie **Automatyzacja symezyjna** przeglądu można przejrzeć szczegóły automatyzacji symulacyjnej.

Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

Po zakończeniu kliknij pozycję **Prześlij**.
