---
title: Automatyzacje symulacji na potrzeby trenowania symulacji ataków
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorzy mogą dowiedzieć się, jak tworzyć zautomatyzowane symulacje zawierające określone techniki i ładunki uruchamiane po spełnieniu określonych warunków w Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2.
ms.technology: mdo
ms.openlocfilehash: 32730dfa36b0140bda246137b4cf6706b3472da7
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739676"
---
# <a name="simulation-automations-for-attack-simulation-training"></a>Automatyzacje symulacji na potrzeby trenowania symulacji ataków

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

Aby uzyskać informacje o rozpoczęciu trenowania symulacji ataków, zobacz [Wprowadzenie korzystanie z trenowania symulacji ataków](attack-simulation-training-get-started.md).

Aby utworzyć automatyzację symulacji, wykonaj następujące kroki:

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/>przejdź do obszaru Email & collaboration Attack simulation training **Automations** tab \> **Simulation automations (Automatyzacje symulacji** za pomocą **funkcji e-mail & współpracy** \> w **zakresie** \> symulacji ataków).

   Aby przejść bezpośrednio do karty **Automatyzacje** , na której można wybrać **pozycję Automatyzacje symulacji**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=automations>.

2. W obszarze **Automatyzacje symulacji** wybierz pozycję Utwórz ikonę ![automatyzacji.](../../media/m365-cc-sc-create-icon.png) **Tworzenie automatyzacji**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Przycisk Utwórz symulację na karcie Automatyzacje symulacji w trenowaniu symulacji ataku w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. Zostanie otwarty kreator tworzenia. W pozostałej części tego artykułu opisano strony i ustawienia, które zawierają.

> [!NOTE]
> W dowolnym momencie kreatora tworzenia symulacji możesz kliknąć pozycję **Zapisz i zamknij** , aby zapisać postęp i kontynuować konfigurowanie symulacji później. Niekompletna symulacja ma wartość **Stan** **— wersja robocza** na **karcie Symulacje** . Możesz wybrać miejsce, w którym zostało przerwane, wybierając symulację i klikając ikonę ![Edytuj symulację.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** symulację.## Nazwij i opisz symulację.

## <a name="name-and-describe-the-simulation-automation"></a>Nazwa i opisanie automatyzacji symulacji

Na stronie **Nazwa usługi Automation** skonfiguruj następujące ustawienia:

- **Nazwa**: wprowadź unikatową, opisową nazwę symulacji.
- **Opis**: wprowadź opcjonalny szczegółowy opis symulacji.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="select-one-or-more-social-engineering-techniques"></a>Wybierz co najmniej jedną technikę inżynierii społecznej

Na stronie **Wybieranie technik inżynierii społecznej** wybierz co najmniej jedną z dostępnych technik inżynierii społecznej, które zostały wyselekcjonowane w [ramach programu MITRE ATT&CK®](https://attack.mitre.org/techniques/enterprise/). Różne ładunki są dostępne dla różnych technik. Dostępne są następujące techniki inżynierii społecznej:

- **Zbieranie poświadczeń**: próbuje zebrać poświadczenia, zabierając użytkowników do dobrze znanej witryny internetowej z polami wejściowymi w celu przesłania nazwy użytkownika i hasła.
- **Załącznik złośliwego oprogramowania**: dodaje złośliwy załącznik do wiadomości. Gdy użytkownik otworzy załącznik, zostanie uruchomiony dowolny kod, który pomoże atakującemu naruszyć bezpieczeństwo urządzenia docelowego.
- **Link w załączniku**: typ hybrydowego zbioru poświadczeń. Osoba atakująca wstawia adres URL do załącznika wiadomości e-mail. Adres URL w załączniku jest zgodny z tą samą techniką co zbieranie poświadczeń.
- **Link do złośliwego oprogramowania**: uruchamia dowolny kod z pliku hostowanego w dobrze znanej usłudze udostępniania plików. Wiadomość wysłana do użytkownika będzie zawierać link do tego złośliwego pliku. Otwarcie pliku i ułatwić atakującemu naruszenie zabezpieczeń urządzenia docelowego.
- **Adres URL usługi Drive-by**: złośliwy adres URL w komunikacie przenosi użytkownika do znanej witryny internetowej, która w trybie dyskretnym uruchamia i/lub instaluje kod na urządzeniu użytkownika.

Po kliknięciu linku **Wyświetl szczegóły** w opisie zostanie otwarte okno wysuwane szczegóły opisujące technikę i kroki symulacji wynikające z tej techniki.

:::image type="content" source="../../media/attack-sim-training-simulations-select-technique-sim-steps.png" alt-text="Okno wysuwane Szczegóły dla techniki zbioru poświadczeń na stronie Wybieranie technik inżynierii społecznej" lightbox="../../media/attack-sim-training-simulations-select-technique-sim-steps.png":::

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="select-payloads"></a>Wybieranie ładunków

Na stronie **Wybieranie ładunków** wybierz jedną z następujących opcji:

- **Ręczne wybieranie**
- **Losowo**

Jeśli wybierzesz pozycję **Randomize**, nie ma nic do skonfigurowania na tej stronie, więc kliknij przycisk **Dalej** , aby kontynuować.

Jeśli **wybierzesz pozycję Ręcznie**, musisz wybrać jeden lub więcej ładunków z listy. Zostaną wyświetlone następujące szczegóły, które pomogą Ci wybrać:

- **Nazwa ładunku**
- **Technika**: musisz wybrać co najmniej jeden ładunek na technikę wybraną na poprzedniej stronie.
- **Język**: język zawartości ładunku. Katalog ładunków firmy Microsoft (globalny) udostępnia ładunki w ponad 10 językach, które można również filtrować.
- **Współczynnik kliknięć**: ile osób kliknąło ten ładunek.
- **Przewidywany wskaźnik kompromisu**: dane historyczne dotyczące ładunku w Microsoft 365, które przewidują odsetek osób, które zostaną naruszone przez ten ładunek.
- **Uruchomione symulacje** liczą, ile razy ten ładunek był używany w innych symulacjach.

W ikonie ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** umożliwia wpisanie części nazwy ładunku i naciśnięcie klawisza Enter w celu filtrowania wyników.

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Źródło**: wskazuje, czy ładunek został utworzony w organizacji, czy jest częścią wcześniej istniejącego wykazu ładunków firmy Microsoft. Prawidłowe wartości to:
  - **Globalny** (wbudowany)
  - **Dzierżawa** (niestandardowa)
  - **Wszystkie**

- **Złożoność**: obliczana na podstawie liczby wskaźników w ładunku, które wskazują na możliwy atak (błędy pisowni, pilność itp.). Więcej wskaźników można łatwiej zidentyfikować jako atak i wskazać mniejszą złożoność. Dostępne wartości to:
  - **Niskie**
  - **Średni**
  - **High (Wysoki)**

- **Język**: Dostępne wartości to: **angielski**, **hiszpański**, **niemiecki**, **japoński**, **francuski**, **portugalski**, **holenderski**, **włoski**, **szwedzki**, **chiński (uproszczony),** **norweski Bokmål**, **polski**, **rosyjski**, **fiński**, **koreański**, **turecki**, **węgierski**, **hebrajski**, **tajski**, **arabski**, **wietnamski**, **słowacki**, **grecki**, **indonezyjski**, **rumuński**, **słoweński**, **chorwacki**, **kataloński** i **inne**.

- **Dodawanie tagów**

- **Filtruj według motywu**: Dostępne wartości to: **Aktywacja konta**, **Weryfikacja konta**, **Rozliczenia**, **Oczyszczanie poczty**, **Odebrane dokumenty**, **Wydatki**, **Faks**, **Raport finansowy**, **Wiadomości przychodzące**, **Faktura**, **Odebrane elementy**, **Alert logowania**, **Odebrana poczta**, **Hasło**, **Płatność**, **Lista płac**, **Spersonalizowana oferta**, **Kwarantanna**, **Praca zdalna**, **przejrzyj komunikat**, **aktualizację zabezpieczeń**, **wstrzymanie usługi**, **wymagany podpis**, **uaktualnienie magazynu skrzynki pocztowej Sprawdź skrzynkę pocztową**, **pocztę głosową** i **inne**.

- **Filtruj według marki**: Dostępne wartości to: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** i **Inne**.

- **Filtruj według branży**: Dostępne wartości to: **Bankowość**, **Usługi biznesowe**, **Usługi konsumenckie**, **Edukacja**, **Energia**, **Budownictwo**, **Doradztwo**, **Usługi finansowe**, **Rząd**, **Gościnność**, **Ubezpieczenia**, **Prawne**, **Usługi kurierskie**, **IT**, **Healthcare**, **Produkcja**, **Handel detaliczny**, **Telekomunikacja**, **Nieruchomości**, i **inne**.

- **Bieżące zdarzenie**: Dostępne wartości to **Tak** lub **Nie**.

- **Kontrowersyjne**: Dostępne wartości to **Tak** lub **Nie**.

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Jeśli wybierzesz ładunek z listy, klikając nazwę, szczegółowe informacje o ładunku są wyświetlane w wysuwnym:

- Karta **Przegląd** zawiera przykład i inne szczegóły dotyczące ładunku.
- Karta **Symulacje uruchomione** zawiera **nazwę symulacji**, **szybkość kliknięć**, **wskaźnik naruszonych** zabezpieczeń i **akcję**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details.png" alt-text="Wysuwane szczegóły ładunku w szkoleniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-select-payload-details.png":::

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="target-users"></a>Użytkownicy docelowi

Na stronie **Użytkownicy docelowi** wybierz, kto otrzyma symulację. Skonfiguruj jedno z następujących ustawień:

- **Uwzględnij wszystkich użytkowników w organizacji**: użytkownicy, których dotyczy problem, są pokazywani na listach po 10. Aby przewijać listę, możesz użyć przycisków **Dalej** i **Poprzednie** bezpośrednio poniżej listy użytkowników. Możesz również użyć ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Ikona wyszukiwania** na stronie w celu znalezienia użytkowników, których dotyczy problem.
- **Uwzględnij tylko określonych użytkowników i grupy**: wybierz jedną z następujących opcji:
  - ![Ikona Dodaj użytkowników.](../../media/m365-cc-sc-create-icon.png) **Dodaj użytkowników**: w wyświetlonym menu wysuwowym **Dodawanie użytkowników** można znaleźć użytkowników i grupy na podstawie następujących kryteriów:
    - **Użytkownicy lub grupy**: w ikonie ![Wyszukaj użytkowników i grupy.](../../media/m365-cc-sc-search-icon.png) **Wyszukaj pola użytkownicy i grupy** , możesz wpisać część **nazwy** lub **adresu e-mail** użytkownika lub grupy, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki. Po zakończeniu kliknij pozycję **Dodaj użytkowników x**.

      > [!NOTE]
      > Kliknięcie przycisku **Dodaj filtry** w celu powrotu do opcji **Filtruj użytkowników według kategorii** spowoduje usunięcie wszystkich użytkowników lub grup wybranych w wynikach wyszukiwania.

    - **Filtruj użytkowników według kategorii**: wybierz opcję brak, niektóre lub wszystkie z następujących opcji:
      - **Sugerowane grupy użytkowników**: wybierz spośród następujących wartości:
        - **Wszystkie sugerowane grupy użytkowników**
        - **Użytkownicy, którzy nie są objęci symulacją w ciągu ostatnich trzech miesięcy**
        - **Recydywistów**
      - **Dział**: Użyj następujących opcji:
        - **Wyszukaj**: na ikonie ![Wyszukaj według działu.](../../media/m365-cc-sc-search-icon.png) **Wyszukaj według pola Dział** , możesz wpisać część wartości Dział, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki.
        - Wybierz **pozycję Wszystkie działy**
        - Wybierz istniejące wartości działu.
      - **Tytuł**: Użyj następujących opcji:
        - **Wyszukaj**: na ikonie ![Wyszukaj według tytułu.](../../media/m365-cc-sc-search-icon.png) **Wyszukaj według pola Tytuł** , możesz wpisać część wartości Tytuł, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki.
        - Wybierz **pozycję Wszystkie tytuły**
        - Wybierz istniejące wartości tytułu.

      :::image type="content" source="../../media/attack-sim-training-simulations-target-users-filter-by-category.png" alt-text="Użytkownik filtrujący na stronie Użytkownicy docelowi w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-target-users-filter-by-category.png":::

      Po zidentyfikowaniu kryteriów użytkownicy, których dotyczy problem, są wyświetlani w wyświetlonej sekcji **Lista użytkowników** , w której można wybrać niektórych lub wszystkich odnalezionych adresatów.

      Po zakończeniu kliknij pozycję **Zastosuj(x),** a następnie kliknij pozycję **Dodaj użytkowników x**.

  Po powrocie do głównej strony **Użytkownicy docelowi** możesz użyć ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu znalezienia użytkowników, których dotyczy problem. Możesz również kliknąć ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń** , aby usunąć określonych użytkowników.

- ![Ikona importu.](../../media/m365-cc-sc-create-icon.png) **Importuj**: W otwieranym oknie dialogowym określ plik CSV zawierający jeden adres e-mail na wiersz.

  Po znalezieniu wybranego pliku CSV lista użytkowników zostanie zaimportowana i **wyświetlona na stronie Użytkownicy docelowi** . Możesz użyć ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu znalezienia użytkowników, których dotyczy problem. Możesz również kliknąć ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń** , aby usunąć określonych użytkowników.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="assign-training"></a>Przypisywanie szkolenia

Na stronie **Przypisywanie szkolenia** można przypisać szkolenia dla symulacji. Zalecamy przypisanie szkoleń dla każdej symulacji, ponieważ pracownicy, którzy przechodzą szkolenie, są mniej podatni na podobne ataki. Dostępne są następujące ustawienia:

- **Wybierz preferencje dotyczące zawartości szkoleniowej**: Wybierz jedną z następujących opcji:
  - **Środowisko szkoleniowe firmy Microsoft**: jest to wartość domyślna, która ma następujące skojarzone opcje konfigurowania:
    - Wybierz jedną z następujących opcji:
      - **Przypisz dla mnie szkolenie**: jest to wartość domyślna i zalecana. Przypisujemy szkolenia na podstawie poprzednich wyników symulacji i trenowania użytkownika, a wybrane opcje można przejrzeć w kolejnych krokach kreatora.
      - **Wybierz samodzielnie kursy i moduły szkoleniowe**: jeśli wybierzesz tę wartość, w następnym kroku kreatora nadal będzie można wyświetlić zalecaną zawartość, a także wszystkie dostępne kursy i moduły.
    - **Data ukończenia**: Wybierz jedną z następujących wartości:
      - **30 dni po zakończeniu symulacji**: jest to wartość domyślna.
      - **15 dni po zakończeniu symulacji**
      - **7 dni po zakończeniu symulacji**
  - **Przekierowanie do niestandardowego adresu URL**: Ta wartość ma następujące skojarzone opcje do skonfigurowania:
    - **Niestandardowy adres URL trenowania** (wymagany)
    - **Niestandardowa nazwa trenowania** (wymagana)
    - **Niestandardowy opis trenowania**
    - **Niestandardowy czas trwania trenowania (w minutach)**: wartość domyślna to 0, co oznacza, że nie ma określonego czasu trwania trenowania.
    - **Data ukończenia**: Wybierz jedną z następujących wartości:
      - **30 dni po zakończeniu symulacji**: jest to wartość domyślna.
      - **15 dni po zakończeniu symulacji**
      - **7 dni po zakończeniu symulacji**
  - **Brak trenowania**: jeśli wybierzesz tę wartość, jedyną opcją na stronie jest przycisk **Dalej** , który przeniesie Cię na stronę [**docelową**](#landing-page) .

:::image type="content" source="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png" alt-text="Opcja dodania zalecanego szkolenia na stronie Przypisania trenowania w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png":::

### <a name="training-assignment"></a>Przypisanie szkoleniowe

> [!NOTE]
> Strona **Przypisywanie szkolenia** jest dostępna tylko wtedy, gdy wybrano **środowisko** \> **szkoleniowe firmy Microsoft Wybierz kursy szkoleniowe i moduły samodzielnie** na poprzedniej stronie.

Na stronie **Przypisanie trenowania** wybierz szkolenia, które chcesz dodać do symulacji, klikając ![ikonę Dodaj szkolenia.](../../media/m365-cc-sc-create-icon.png) **Dodaj szkolenia**.

Na wyświetlonym menu wysuwowym **Dodawanie trenowania** możesz wybrać szkolenia do użycia na następujących dostępnych kartach:

- **Zalecana** karta: przedstawia zalecane wbudowane szkolenia oparte na konfiguracji symulacji. Są to te same szkolenia, które zostałyby przypisane, gdyby wybrano pozycję **Przypisz szkolenie dla mnie** na poprzedniej stronie.
- **Karta Wszystkie szkolenia** : pokazuje wszystkie dostępne wbudowane szkolenia.

  Dla każdego szkolenia są wyświetlane następujące informacje:

  - **Nazwa szkolenia**
  - **Źródło**: Wartość jest **globalna**.
  - **Czas trwania (min)**
  - **Wersja zapoznawcza**: kliknij przycisk **Podgląd** , aby wyświetlić szkolenie.

  W ikonie ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **W polu wyszukiwania** możesz wpisać część nazwy trenowania i nacisnąć klawisz Enter, aby filtrować wyniki na bieżącej karcie.

  Wybierz wszystkie szkolenia, które chcesz uwzględnić na bieżącej karcie, a następnie kliknij przycisk **Dodaj**.

Po powrocie do głównej strony **Przypisania trenowania** zostaną wyświetlone wybrane szkolenia. Dla każdego szkolenia są wyświetlane następujące informacje:

- **Nazwa szkolenia**
- **Źródło**
- **Czas trwania (min)**

Dla każdego szkolenia na liście wybierz co najmniej jedną z następujących wartości w kolumnie **Przypisz do** , aby skonfigurować, kto pobiera szkolenie:

- **Wszyscy użytkownicy**
- **Klikniętego ładunku**
- **Zagrożone**

Jeśli nie chcesz używać pokazanego szkolenia, kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

:::image type="content" source="../../media/attack-sim-training-training-assignment.png" alt-text="Strona Trenowanie przypisania w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-training-assignment.png":::

Po zakończeniu kliknij przycisk **Dalej**.

### <a name="landing-page"></a>Strona docelowa

Na **stronie Docelowa** skonfigurujesz stronę internetową, do którą użytkownik jest pobierany, jeśli otworzy ładunek w symulacji.

- **Wybierz preferencję strony docelowej**: dostępne wartości zależą od poprzednich wyborów na stronie [Wybieranie ładunków](#select-payloads) zgodnie z opisem w poniższej tabeli:

  |Wybór na stronie Wybieranie ładunków|Dostępne wartości dla preferencji Wybieranie strony docelowej|
  |---|---|
  |Ręczne wybieranie|Używanie domyślnej strony docelowej firmy Microsoft <p> Tworzenie własnej strony docelowej <p> Używanie niestandardowego adresu URL <p> **Uwaga**: wartość **Użyj niestandardowego adresu URL** jest niedostępna, jeśli wcześniej **wybrano pozycję Załącznik złośliwego oprogramowania** lub **Link do złośliwego oprogramowania** na stronie [Wybieranie technik inżynierii społecznej](#select-one-or-more-social-engineering-techniques) .|
  |Losowo|Używanie domyślnej strony docelowej firmy Microsoft|

  Dostępne wartości **preferencji Wybierz stronę docelową** i skojarzone z nimi ustawienia są opisane na następującej liście:

  - **Użyj domyślnej strony docelowej firmy Microsoft**. Jest to wartość domyślna i powoduje wykonanie jednej domyślnej akcji szablonu, logo i wskaźnika ładunku firmy Microsoft, która ma zastosowanie do wszystkich ładunków.

    Na **stronie docelowej** należy skonfigurować następujące dodatkowe ustawienia:

    - **Wybierz układ strony docelowej**: wybierz jeden z 5 dostępnych szablonów stron docelowych.
    - **Dodaj logo**: kliknij przycisk **Przeglądaj** , aby znaleźć i wybrać plik .png, jpeg lub .gif, aby dodać do wszystkich ładunków wybranych przez firmę Microsoft. Aby uniknąć zniekształceń, rozmiar logo powinien wynosić maksymalnie 210 x 70. Aby usunąć logo, kliknij przycisk **Usuń**.
    - **Wskaźniki ładunku**: to ustawienie nie jest dostępne, jeśli wcześniej **wybrano pozycję Załącznik złośliwego oprogramowania** lub **Link do złośliwego oprogramowania** na stronie [Wybieranie technik inżynierii społecznej](#select-one-or-more-social-engineering-techniques) .

      Wybierz pozycję **Dodaj wskaźniki ładunku do wiadomości e-mail** , aby pomóc użytkownikom dowiedzieć się, jak identyfikować wiadomości wyłudzające informacje.

    Możesz wyświetlić podgląd wyników, klikając przycisk **Otwórz panel podglądu** w środku strony. W wyświetlonym okienku wysuwowym podglądu możesz użyć opcji **Wybierz ładunek w celu wyświetlenia podglądu** , aby zobaczyć, jak wygląda każdy ładunek.

  - **Utwórz własną stronę docelową**: ta wartość powoduje wykonanie pojedynczej akcji wskaźnika ładunku, która jest stosowana do wybranych ładunków.

    Na **stronie docelowej** należy skonfigurować następujące dodatkowe ustawienia:

    - **Wskaźniki ładunku**: to ustawienie jest dostępne do wybrania tylko wtedy, gdy oba z następujących warunków są spełnione:
      - Wcześniej wybrano **pozycje Zbiory poświadczeń**, **Link w załączniku** lub **Adres URL usługi Drive-by** na stronie [Wybieranie technik inżynierii społecznej](#select-one-or-more-social-engineering-techniques) .
      - Po dodaniu **tagu dynamicznego** o nazwie **Wstaw zawartość wiadomości e-mail** do zawartości strony.

    - Zawartość strony: Dostępne są dwie karty:

      - **Tekst**: Do utworzenia strony docelowej jest dostępny edytor tekstów sformatowanych. Oprócz typowych ustawień czcionki i formatowania dostępne są następujące ustawienia:
        - **Tag dynamiczny**: wybierz spośród następujących tagów:
          - **Wstaw nazwę**
          - **Wstaw nazwę nadawcy**
          - **Wstawianie wiadomości e-mail nadawcy**
          - **Wstawianie tematu wiadomości e-mail**
          - **Wstawianie zawartości wiadomości e-mail**
          - **Wstaw datę**
        - **Użyj od wartości domyślnej**: wybierz jeden z 5 dostępnych szablonów stron docelowych, od których chcesz zacząć. Możesz zmodyfikować tekst i układ w obszarze edycji. Aby zresetować stronę docelową z powrotem do domyślnego tekstu i układu szablonu, kliknij przycisk **Resetuj do wartości domyślnej**.
        - **Łącze szkoleniowe**: W wyświetlonym oknie dialogowym **Adres URL trenowania Nazwy** wprowadź tytuł linku do linku szkoleniowego, a następnie kliknij przycisk **Potwierdź** , aby dodać link do strony docelowej.
      - **Kod**: kod HTML można wyświetlać i modyfikować bezpośrednio.

      Możesz wyświetlić podgląd wyników, klikając przycisk **Otwórz panel podglądu** w środku strony. W wyświetlonym okienku wysuwowym podglądu możesz użyć opcji **Wybierz ładunek w celu wyświetlenia podglądu** , aby zobaczyć, jak wygląda każdy ładunek.

  - **Użyj niestandardowego adresu URL**: dodaj adres URL w wyświetlonym polu **Wprowadź niestandardowy adres URL strony docelowej** . Na stronie nie są dostępne żadne inne opcje.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="select-end-user-notification"></a>Wybieranie powiadomienia użytkownika końcowego

Na stronie **Wybieranie powiadomienia użytkownika końcowego** wybierz jedną z następujących opcji powiadomień:

- **Nie dostarczaj powiadomień**: kliknij przycisk **Kontynuuj** w wyświetlonym oknie dialogowym alertu. Jeśli wybierzesz tę opcję, po kliknięciu przycisku **Dalej** zostanie wyświetlona strona [Harmonogram symulacji](#simulation-schedule).

- **Domyślne powiadomienie firmy Microsoft (zalecane)**: Na stronie są dostępne następujące dodatkowe ustawienia:

  - **Wybierz język domyślny**: Dostępne wartości to: **chiński (uproszczony),** **chiński (tradycyjny),** **angielski**, **francuski**, **niemiecki**, **włoski**, **japoński**, **koreański**, **portugalski**, **rosyjski**, **hiszpański** i **holenderski**.

  - Domyślnie są uwzględniane następujące powiadomienia:
    - **Powiadomienie o pozytywnym wzmocnieniu firmy Microsoft**
    - **Domyślne powiadomienie o przypisaniu szkolenia firmy Microsoft**
    - **Domyślne powiadomienie o przypomnieniu szkoleniowym firmy Microsoft**

    Dla każdego powiadomienia są dostępne następujące informacje:
    - **Powiadomienia**: nazwa powiadomienia.
    - **Język**: jeśli powiadomienie zawiera wiele tłumaczeń, dwa pierwsze języki są wyświetlane bezpośrednio. Aby wyświetlić pozostałe języki, umieść kursor nad ikoną liczbową (na przykład **+10**).
    - **Typ**: Jedna z następujących wartości:
      - **Powiadomienie o pozytywnym wzmocnieniu**
      - **Powiadomienie o przypisaniu szkolenia**
      - **Powiadomienie dotyczące przypomnienia o trenowaniu**
    - **Preferencje dostarczania**: W przypadku **powiadomień o pozytywnym wzmocnieniu** i typów **powiadomień dotyczących przypomnień szkoleniowych** dostępne są następujące wartości
      - **Nie dostarczaj**
      - **Dostarczanie po zakończeniu kampanii**
      - **Dostarczanie podczas kampanii**
    - **Akcje**: jeśli klikniesz ikonę ![Widok.](../../media/m365-cc-sc-view-icon.png) **Wyświetl** ikonę, zostanie wyświetlona strona **Przejrzyj powiadomienie** z następującymi informacjami:
      - Karta **Podgląd**: wyświetl komunikat powiadomienia, gdy użytkownicy będą go widzieć.
        - Aby wyświetlić komunikat w różnych językach, użyj pola **Wybierz język** .
        - Użyj pola **Wybierz ładunek do wersji zapoznawczej** , aby wybrać komunikat powiadomienia dla symulacji zawierających wiele ładunków.
      - Karta **Szczegóły**: wyświetl szczegóły dotyczące powiadomienia:
        - **Opis powiadomienia**
        - **Źródło**: W przypadku wbudowanych powiadomień wartość to **Globalne**. W przypadku powiadomień niestandardowych wartość to **Dzierżawa**.
        - **Typ powiadomienia**: Jeden z następujących typów bazuje na pierwotnie wybranym powiadomieniu:
          - **Powiadomienie o pozytywnym wzmocnieniu**
          - **Powiadomienie o przypisaniu szkolenia**
          - **Powiadomienie dotyczące przypomnienia o trenowaniu**
        - **Zmodyfikowane przez**
        - **Ostatnia modyfikacja**

        Po wprowadzeniu wszystkich zmian kliknij przycisk **Zamknij**.

  Po kliknięciu przycisku **Dalej** zostanie wyświetlona strona [Harmonogram symulacji](#simulation-schedule).

- **Dostosowane powiadomienia użytkowników końcowych**: po kliknięciu **przycisku Dalej** zostanie wyświetlona strona **powiadomienia o przypisaniu trenowania** zgodnie z opisem w następnych sekcjach.

### <a name="training-assignment-notification"></a>Powiadomienie o przypisaniu szkolenia

Strona **powiadomienia o przypisaniu trenowania** jest dostępna tylko wtedy, gdy **wybrano opcję Dostosowane powiadomienia użytkownika końcowego** na stronie **[Powiadomienia wybierz użytkownika końcowego](#select-end-user-notification)** .

Na tej stronie przedstawiono następujące powiadomienia i ich skonfigurowane języki:

- **Domyślne powiadomienie o przypisaniu szkolenia firmy Microsoft**
- Wszystkie utworzone wcześniej niestandardowe powiadomienia dotyczące przypisania trenowania.

  Te powiadomienia są również dostępne w **powiadomieniach użytkowników końcowych** na karcie **Biblioteka zawartości symulacji** w trenowaniu symulacji ataków pod adresem <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. **Domyślne powiadomienie o przypisaniu szkolenia firmy Microsoft** jest dostępne na karcie **Powiadomienia globalne** . Niestandardowe powiadomienia dotyczące przypisań szkoleniowych są dostępne na karcie **Powiadomienia dzierżawy** . Aby uzyskać więcej informacji, zobacz [Powiadomienia użytkowników końcowych dotyczące trenowania symulacji ataków](attack-simulation-training-end-user-notifications.md).

Możesz wybrać istniejące powiadomienie o przypisaniu szkolenia lub utworzyć nowe powiadomienie do użycia:

- Aby wybrać istniejące powiadomienie, kliknij pusty obszar obok nazwy powiadomienia. Jeśli klikniesz nazwę powiadomienia, powiadomienie zostanie wybrane i zostanie wyświetlone okno wysuwane w wersji zapoznawczej. Aby usunąć zaznaczenie powiadomienia, wyczyść pole wyboru obok powiadomienia.
- Aby wyszukać istniejące powiadomienie, użyj ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu wyszukania nazwy.

  Wybierz powiadomienie, którego chcesz użyć, a następnie kliknij przycisk **Dalej**.

- Aby utworzyć nowe powiadomienie i użyć go, kliknij pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nową**.

#### <a name="create-new-training-assignment-notification-wizard"></a>Kreator tworzenia nowego powiadomienia o przypisaniu trenowania

Jeśli klikniesz pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nową** na stronie **powiadomienia o przypisaniu trenowania** , zostanie otwarty kreator tworzenia powiadomień.

Kroki tworzenia są identyczne, jak opisano w artykule [Tworzenie powiadomień użytkowników końcowych](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> Na stronie **Definiowanie szczegółów** wybierz wartość **Powiadomienie o przypisaniu trenowania** dla **pozycji Wybierz typ powiadomienia**.

Po zakończeniu wrócisz do strony **powiadomień o przypisaniu trenowania** , na której na liście zostanie wyświetlone właśnie utworzone powiadomienie.

Wybierz powiadomienie, którego chcesz użyć, a następnie kliknij przycisk **Dalej**.

### <a name="training-reminder-notification"></a>Powiadomienie dotyczące przypomnienia o trenowaniu

Strona **powiadomienia Przypomnienie o trenowaniu** jest dostępna tylko wtedy, gdy **wybrano opcję Dostosowane powiadomienia użytkownika końcowego** na stronie **[Powiadomienia wybierz użytkownika końcowego](#select-end-user-notification)** .

- **Ustaw częstotliwość powiadamiania o przypomnieniu**: wybierz pozycję **Co tydzień** (wartość **domyślna) lub Dwa razy w tygodniu**.

- **Wybierz powiadomienie o przypomnieniu**: W tej sekcji przedstawiono następujące powiadomienia i ich skonfigurowane języki:

  - **Domyślne powiadomienie o przypomnieniu szkoleniowym firmy Microsoft**
  - Wszystkie utworzone wcześniej powiadomienia o przypomnieniu o trenowaniu niestandardowym.

    Te powiadomienia są również dostępne w **powiadomieniach użytkowników końcowych** na karcie **Biblioteka zawartości symulacji** w trenowaniu symulacji ataków pod adresem <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. **Domyślne powiadomienie o przypomnieniu szkoleniowym firmy Microsoft** jest dostępne na karcie **Powiadomienia globalne** . Powiadomienia o przypomnieniu o trenowaniu niestandardowym są dostępne na karcie **Powiadomienia dzierżawy** . Aby uzyskać więcej informacji, zobacz [Powiadomienia użytkowników końcowych dotyczące trenowania symulacji ataków](attack-simulation-training-end-user-notifications.md).

  Możesz wybrać istniejące powiadomienie dotyczące przypomnienia szkoleniowego lub utworzyć nowe powiadomienie do użycia:

  - Aby wybrać istniejące powiadomienie, kliknij pusty obszar obok nazwy powiadomienia. Jeśli klikniesz nazwę powiadomienia, powiadomienie zostanie wybrane i zostanie wyświetlone okno wysuwane w wersji zapoznawczej. Aby usunąć zaznaczenie powiadomienia, wyczyść pole wyboru obok powiadomienia.
  - Aby wyszukać istniejące powiadomienie, użyj ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu wyszukania nazwy.

    Wybierz powiadomienie, którego chcesz użyć, a następnie kliknij przycisk **Dalej**.

  - Aby utworzyć nowe powiadomienie i użyć go, kliknij pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nową**.

#### <a name="create-new-training-reminder-notification-wizard"></a>Kreator tworzenia nowego powiadomienia o przypomnieniu szkoleniowym

Jeśli klikniesz pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nową** na stronie **powiadomienia Przypomnienie szkoleniowe** , zostanie otwarty kreator tworzenia powiadomień.

Kroki tworzenia są identyczne, jak opisano w artykule [Tworzenie powiadomień użytkowników końcowych](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> Na stronie **Definiowanie szczegółów** wybierz wartość **Powiadomienie o przypomnieniu trenowania** dla **pozycji Wybierz typ powiadomienia**.

Po zakończeniu zostaniesz przekierowany z powrotem na stronę **powiadomienia Przypomnienie o trenowaniu** , na której zostanie wyświetlone właśnie utworzone powiadomienie na liście.

Wybierz powiadomienie, którego chcesz użyć, a następnie kliknij przycisk **Dalej**.

### <a name="positive-reinforcement-notification"></a>Powiadomienie o pozytywnym wzmocnieniu

Strona **Powiadomienia o pozytywnym wzmocnieniu** jest dostępna tylko wtedy, gdy **wybrano opcję Dostosowane powiadomienia użytkownika końcowego** na stronie **[Powiadomienia wybierz użytkownika końcowego](#select-end-user-notification)** .

- **Preferencje dostarczania**: wybierz jedną z następujących wartości:

  - **Nie dostarczaj**: po wybraniu tej opcji zostanie wyświetlona strona [Harmonogram symulacji](#simulation-schedule) po kliknięciu przycisku **Dalej**.

  - **Dostarczanie po wyświetleniu przez użytkownika informacji o zakończeniu kampanii i zakończeniu kampanii** lub dostarczeniu **natychmiast po zgłoszeniu phish przez użytkownika**: W poniższych sekcjach przedstawiono następujące powiadomienia i ich skonfigurowane języki w **wyświetlonej sekcji Wybierz powiadomienie o pozytywnym wzmocnieniu** :

  - **Domyślne powiadomienie o wzmacnianiu dodatnim firmy Microsoft**
  - Wszystkie utworzone wcześniej niestandardowe powiadomienia o pozytywnym wzmocnieniu.

    Te powiadomienia są również dostępne w **powiadomieniach użytkowników końcowych** na karcie **Biblioteka zawartości symulacji** w trenowaniu symulacji ataków pod adresem <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. **Domyślne powiadomienie o pozytywnym wzmocnieniu firmy Microsoft** jest dostępne na karcie **Powiadomienia globalne** . Niestandardowe powiadomienia o pozytywnym wzmacnianiu są dostępne na karcie **Powiadomienia dzierżawy** . Aby uzyskać więcej informacji, zobacz [Powiadomienia użytkowników końcowych dotyczące trenowania symulacji ataków](attack-simulation-training-end-user-notifications.md).

  Możesz wybrać istniejące powiadomienie o pozytywnym wzmocnieniu lub utworzyć nowe powiadomienie do użycia:

  - Aby wybrać istniejące powiadomienie, kliknij pusty obszar obok nazwy powiadomienia. Jeśli klikniesz nazwę powiadomienia, powiadomienie zostanie wybrane i zostanie wyświetlone okno wysuwane w wersji zapoznawczej. Aby usunąć zaznaczenie powiadomienia, wyczyść pole wyboru obok powiadomienia.
  - Aby wyszukać istniejące powiadomienie, użyj ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu wyszukania nazwy.

    Wybierz powiadomienie, którego chcesz użyć, a następnie kliknij przycisk **Dalej**.

  - Aby utworzyć nowe powiadomienie i użyć go, kliknij pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nową**.

#### <a name="create-new-positive-reinforcement-notification-wizard"></a>Kreator tworzenia nowego pozytywnego powiadomienia wzmacniania

Jeśli klikniesz pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nową** na stronie **Powiadomienia o pozytywnym wzmocnieniu** , zostanie otwarty kreator tworzenia powiadomień.

Kroki tworzenia są identyczne, jak opisano w artykule [Tworzenie powiadomień użytkowników końcowych](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> Na stronie **Definiowanie szczegółów** wybierz wartość **Powiadomienie o pozytywnym wzmocnieniu** dla **opcji Wybierz typ powiadomienia**.

Po zakończeniu wrócisz do strony **powiadomienia o pozytywnym wzmocnieniu** , na której zostanie wyświetlone właśnie utworzone powiadomienie na liście.

Wybierz powiadomienie, którego chcesz użyć, a następnie kliknij przycisk **Dalej**.

## <a name="simulation-schedule"></a>Harmonogram symulacji

Na stronie **Harmonogram symulacji** wybierz jedną z następujących wartości:

- **Randomizowane**: nadal musisz wybrać harmonogram na następnej stronie, ale symulacje będą uruchamiane losowo z harmonogramem.
- **Stałe**

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="schedule-details"></a>Szczegóły harmonogramu

To, co widzisz na stronie **Szczegóły harmonogramu**, zależy od tego, czy **wybrano** opcję **Randomized** czy Fixed na poprzedniej stronie.

- **Randomizowane**: Dostępne są następujące ustawienia:
  - Sekcja **uruchamiania symulacji**: Skonfiguruj następujące ustawienie:
    - **Wybierz datę rozpoczęcia symulacji**
  - Sekcja **określania zakresu symulacji**: Skonfiguruj następujące ustawienia:
    - **Wybierz dni tygodnia, od których mogą rozpoczynać się symulacje**: wybierz co najmniej jeden dzień tygodnia.
    - **Wprowadź maksymalną liczbę symulacji, które można uruchomić między datami rozpoczęcia i zakończenia**: wprowadź wartość z zakresu od 1 do 10.
    - **Losowe czasy wysyłania**: wybierz to ustawienie, aby losowo określić czas wysyłania.
  - Sekcja **końcowa symulacji**: Skonfiguruj następujące ustawienie:
    - **Wybierz datę zakończenia symulacji**

- **Naprawiono**: Dostępne są następujące ustawienia:
  - Sekcja **uruchamiania symulacji**: Skonfiguruj następujące ustawienie:
    - **Wybierz datę rozpoczęcia symulacji**
  - Sekcja **Cykl symulacji**: Skonfiguruj następujące ustawienia:
    - **Wybierz, czy chcesz, aby symulacje były uruchamiane co tydzień lub co miesiąc**: Wybierz jedną z następujących wartości:
      - **Co tydzień**: jest to wartość domyślna.
      - **Miesięczne**
    - **Wprowadź częstotliwość powtarzania symulacji w tygodniach**: wprowadź wartość z zakresu od 1 do 99 tygodni.
    - **Wybierz dzień tygodnia, od których mają rozpoczynać się symulacje**
  - Sekcja **końcowa symulacji**: Zaznacz jedną z następujących wartości:
    - **Wybierz datę zakończenia symulacji**
    - **Wprowadź liczbę wystąpień symulacji do uruchomienia przed zakończeniem**: wprowadź wartość z zakresu od 1 do 10.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="launch-details"></a>Szczegóły uruchamiania

Na stronie **Szczegóły uruchamiania** skonfiguruj następujące dodatkowe ustawienia automatyzacji:

- **Używaj unikatowych ładunków w symulacjach w ramach automatyzacji**: domyślnie to ustawienie nie jest zaznaczone.
- **Cel recydywistów**: domyślnie to ustawienie nie jest zaznaczone. Jeśli ją wybierzesz, skonfiguruj następujące wyświetlone ustawienie:
  - **Wprowadź maksymalną liczbę elementów docelowych użytkownika w ramach tej automatyzacji**: wprowadź wartość z zakresu od 1 do 10.
- **Wyślij wiadomość e-mail symulacji na podstawie bieżącego ustawienia strefy czasowej użytkownika z Outlook aplikacji internetowej**: domyślnie to ustawienie nie jest zaznaczone.
- **Wyświetl stronę z zebranymi danymi śródmiąższowymi techniką drive-by**: to ustawienie jest dostępne tylko wtedy, gdy wybrano pozycję **Dysk po adresie URL** na stronie **[Wybieranie technik inżynierii społecznej](#select-one-or-more-social-engineering-techniques)** . Domyślnie ustawienie jest włączone (![przełącz na ikonę).](../../media/scc-toggle-on.png)

## <a name="review-simulation-automation"></a>Przegląd automatyzacji symulacji

Na stronie **Przegląd automatyzacji symulacji** możesz przejrzeć szczegóły automatyzacji symulacji.

W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

Po zakończeniu kliknij pozycję **Prześlij**.
