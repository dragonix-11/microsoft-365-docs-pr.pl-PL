---
title: Symulowanie ataku polegającego na wyłudzaniu informacji dzięki szkoleniu z symulacji ataku
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
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak symulować ataki wyłudzania informacji i szkolić swoich użytkowników w zakresie zapobiegania wyłudzaniu informacji przy użyciu trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2.
ms.technology: mdo
ms.openlocfilehash: 55810d65c33796a617421f0796191335821bde98
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648894"
---
# <a name="simulate-a-phishing-attack-with-attack-simulation-training-in-defender-for-office-365"></a>Symulowanie ataku wyłudzającego informacje przy użyciu trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

Trenowanie symulacji ataków w Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2 lub Microsoft 365 E5 umożliwia uruchamianie niegroźnych symulacji cyberataków w organizacji. Te symulacje testują zasady i praktyki dotyczące zabezpieczeń, a także szkolą pracowników, aby zwiększyli ich świadomość i zmniejszyli podatność na ataki. W tym artykule przedstawiono proces tworzenia symulowanego ataku wyłudzania informacji przy użyciu trenowania symulacji ataków.

Aby uzyskać informacje o rozpoczęciu trenowania symulacji ataków, zobacz [Wprowadzenie korzystanie z trenowania symulacji ataków](attack-simulation-training-get-started.md).

Aby uruchomić symulowany atak wyłudzający informacje, wykonaj następujące czynności:

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do karty Symulacje **symulacji** \> **ataków** **& współpracy** \> e-mail.

   Aby przejść bezpośrednio do karty **Symulacje** , użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=simulations>.

2. Na **karcie Symulacje** wybierz pozycję ![Uruchom ikonę symulacji.](../../media/m365-cc-sc-create-icon.png) **Uruchom symulację**.

   :::image type="content" source="../../media/attack-sim-training-simulations-launch.png" alt-text="Przycisk Uruchom symulację na karcie Symulacje w trenowaniu symulacji ataku w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-launch.png":::

3. Zostanie otwarty kreator tworzenia symulacji. W pozostałej części tego artykułu opisano strony i ustawienia, które zawierają.

> [!NOTE]
> W dowolnym momencie kreatora tworzenia symulacji możesz kliknąć pozycję **Zapisz i zamknij** , aby zapisać postęp i kontynuować konfigurowanie symulacji później. Niekompletna symulacja ma wartość **Stan** **— wersja robocza** na **karcie Symulacje** . Możesz wybrać miejsce, w którym zostało przerwane, wybierając symulację i klikając ikonę ![Edytuj symulację.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** symulację.

## <a name="select-a-social-engineering-technique"></a>Wybieranie techniki inżynierii społecznej

Na stronie **Wybieranie techniki** wybierz dostępną technikę inżynierii społecznej, która została wyselekcjonowana w [ramach programu MITRE ATT&CK®](https://attack.mitre.org/techniques/enterprise/). Różne ładunki są dostępne dla różnych technik. Dostępne są następujące techniki inżynierii społecznej:

- **Zbieranie poświadczeń**: próbuje zebrać poświadczenia, zabierając użytkowników do dobrze znanej witryny internetowej z polami wejściowymi w celu przesłania nazwy użytkownika i hasła.
- **Załącznik złośliwego oprogramowania**: dodaje złośliwy załącznik do wiadomości. Gdy użytkownik otworzy załącznik, zostanie uruchomiony dowolny kod, który pomoże atakującemu naruszyć bezpieczeństwo urządzenia docelowego.
- **Link w załączniku**: typ hybrydowego zbioru poświadczeń. Osoba atakująca wstawia adres URL do załącznika wiadomości e-mail. Adres URL w załączniku jest zgodny z tą samą techniką co zbieranie poświadczeń.
- **Link do złośliwego oprogramowania**: uruchamia dowolny kod z pliku hostowanego w dobrze znanej usłudze udostępniania plików. Wiadomość wysłana do użytkownika będzie zawierać link do tego złośliwego pliku. Otwarcie pliku pomoże atakującemu naruszyć bezpieczeństwo urządzenia docelowego.
- **Adres URL usługi Drive-by**: złośliwy adres URL w komunikacie przenosi użytkownika do znanej witryny internetowej, która w trybie dyskretnym uruchamia i/lub instaluje kod na urządzeniu użytkownika.

Po kliknięciu linku **Wyświetl szczegóły** w opisie zostanie otwarte okno wysuwane szczegóły opisujące technikę i kroki symulacji wynikające z tej techniki.

:::image type="content" source="../../media/attack-sim-training-simulations-select-technique-sim-steps.png" alt-text="Okno wysuwane Szczegóły dla techniki zbioru poświadczeń na stronie Wybieranie techniki" lightbox="../../media/attack-sim-training-simulations-select-technique-sim-steps.png":::

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="name-and-describe-the-simulation"></a>Nazwa i opisanie symulacji

Na stronie **Symulacja nazw** skonfiguruj następujące ustawienia:

- **Nazwa**: wprowadź unikatową, opisową nazwę symulacji.
- **Opis**: wprowadź opcjonalny szczegółowy opis symulacji.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="select-a-payload"></a>Wybieranie ładunku

Na stronie **Wybierz ładunek** musisz wybrać istniejący ładunek z listy lub utworzyć nowy ładunek.

Poniższe szczegóły są wyświetlane na liście ładunków, które pomogą Ci wybrać:

- **Nazwa ładunku**
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

- **Język**: Dostępne wartości to: **chiński (uproszczony),** **chiński (tradycyjny),** **angielski**, **francuski**, **niemiecki**, **włoski**, **japoński**, **koreański**, **portugalski**, **rosyjski**, **hiszpański** i **holenderski**.

- **Dodawanie tagów**

- **Filtruj według motywu**: Dostępne wartości to: **Aktywacja konta**, **Weryfikacja konta**, **Rozliczenia**, **Oczyszczanie poczty**, **Odebrane dokumenty**, **Wydatki**, **Faks**, **Raport finansowy**, **Wiadomości przychodzące**, **Faktura**, **Odebrane elementy**, **Alert logowania**, **Odebrana poczta**, **Hasło**, **Płatność**, **Lista płac**, **Spersonalizowana oferta**, **Kwarantanna**, **Praca zdalna**, **przejrzyj komunikat**, **aktualizację zabezpieczeń**, **wstrzymanie usługi**, **wymagany podpis**, **uaktualnienie magazynu skrzynki pocztowej Sprawdź skrzynkę pocztową**, **pocztę głosową** i **inne**.

- **Filtruj według marki**: Dostępne wartości to: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** i **Inne**.

- **Filtruj według branży**: Dostępne wartości to: **Bankowość**, **Usługi biznesowe**, **Usługi konsumenckie**, **Edukacja**, **Energia**, **Budownictwo**, **Doradztwo**, **Usługi finansowe**, **Rząd**, **Gościnność**, **Ubezpieczenia**, **Prawne**, **Usługi kurierskie**, **IT**, **Healthcare**, **Produkcja**, **Handel detaliczny**, **Telekomunikacja**, **Nieruchomości**, i **inne**.

- **Bieżące zdarzenie**: Dostępne wartości to **Tak** lub **Nie**.

- **Kontrowersyjne**: Dostępne wartości to **Tak** lub **Nie**.

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload.png" alt-text="Strona Wybieranie ładunku w szkoleniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-select-payload.png":::

Jeśli wybierzesz ładunek z listy, szczegóły dotyczące ładunku są wyświetlane w wysuwnym oknie:

- Karta **Przegląd** zawiera przykład i inne szczegóły dotyczące ładunku.
- Karta **Symulacje uruchomione** zawiera **nazwę symulacji**, **szybkość kliknięć**, **wskaźnik naruszonych** zabezpieczeń i **akcję**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details.png" alt-text="Wysuwane szczegóły ładunku w szkoleniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-select-payload-details.png":::

Jeśli wybierzesz ładunek z listy, klikając nazwę, ikona ![Wyślij ładunek testowy.](../../media/m365-cc-sc-create-icon.png) Na stronie głównej zostanie wyświetlony przycisk **Wyślij test**, na którym można wysłać kopię wiadomości e-mail ładunku do siebie (obecnie zalogowanego użytkownika) w celu przeprowadzenia inspekcji.

Aby utworzyć własny ładunek, kliknij pozycję ![Utwórz ikonę ładunku.](../../media/m365-cc-sc-create-icon.png) **Utwórz ładunek**. Aby uzyskać więcej informacji, zobacz [Create custom payloads for Attack simulation training (Tworzenie niestandardowych ładunków na potrzeby trenowania symulacji ataków](attack-simulation-training-payloads.md)).

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="target-users"></a>Użytkownicy docelowi

Na stronie **Użytkownicy docelowi** wybierz, kto otrzyma symulację. Skonfiguruj jedno z następujących ustawień:

- **Uwzględnij wszystkich użytkowników w organizacji**: użytkownicy, których dotyczy problem, są pokazywani na listach po 10. Aby przewijać listę, możesz użyć przycisków **Dalej** i **Poprzednie** bezpośrednio poniżej listy użytkowników. Możesz również użyć ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Ikona wyszukiwania** na stronie w celu znalezienia użytkowników, których dotyczy problem.

- **Uwzględnij tylko określonych użytkowników i grupy**: wybierz jedną z następujących opcji:
  - ![Ikona Dodaj użytkowników.](../../media/m365-cc-sc-create-icon.png) **Dodaj użytkowników**: w wyświetlonym menu wysuwowym **Dodawanie użytkowników** można znaleźć użytkowników i grupy na podstawie następujących kryteriów:

    - **Wyszukaj użytkowników lub grupy**: w polu możesz wpisać część **nazwy** lub **adresu e-mail** użytkownika lub grupy, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki. Po zakończeniu kliknij pozycję **Dodaj użytkowników x**.

      > [!NOTE]
      > Kliknięcie przycisku **Dodaj filtry** w celu powrotu do opcji **Filtruj użytkowników według kategorii** spowoduje usunięcie wszystkich użytkowników lub grup wybranych w wynikach wyszukiwania.

    - **Filtruj użytkowników według kategorii**: wybierz opcję brak, niektóre lub wszystkie z następujących opcji:

      - **Sugerowane grupy użytkowników**: wybierz spośród następujących wartości:
        - **Wszystkie sugerowane grupy użytkowników**
        - **Użytkownicy, którzy nie są objęci symulacją w ciągu ostatnich trzech miesięcy**
        - **Recydywistów**

      - **Tagi użytkowników**: tagi użytkowników są identyfikatorami określonych grup użytkowników (na przykład kont priorytetowych). Aby uzyskać więcej informacji, zobacz [Tagi użytkowników w Ochrona usługi Office 365 w usłudze Microsoft Defender](user-tags.md).

          Użyj następujących opcji:

        - **Wyszukiwanie**: w ![obszarze Wyszukaj według ikony tagów użytkownika.](../../media/m365-cc-sc-search-icon.png) **Wyszukaj według tagów użytkownika**, możesz wpisać część tagu użytkownika, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki.
        - Wybierz pozycję **Wszystkie tagi użytkowników**
        - Wybierz istniejące tagi użytkowników.

      - **Dział**: Użyj następujących opcji:
        - **Wyszukaj**: w ![obszarze Wyszukaj według działu ikona.](../../media/m365-cc-sc-search-icon.png) **Wyszukaj według działu**, możesz wpisać część wartości Dział, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki.
        - Wybierz **pozycję Wszystkie działy**
        - Wybierz istniejące wartości działu.

      - **Tytuł**: Użyj następujących opcji:
        - **Wyszukiwanie**: w ![obszarze Wyszukaj według tytułu ikona.](../../media/m365-cc-sc-search-icon.png) **Wyszukaj według tytułu**, możesz wpisać część wartości Tytuł, a następnie nacisnąć klawisz Enter. Możesz wybrać niektóre lub wszystkie wyniki.
        - Wybierz **pozycję Wszystkie tytuły**
        - Wybierz istniejące wartości tytułu.

      :::image type="content" source="../../media/attack-sim-training-simulations-target-users-filter-by-category.png" alt-text="Filtrowanie użytkownika na stronie Użytkownicy docelowi w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-target-users-filter-by-category.png":::

      Po zidentyfikowaniu kryteriów użytkownicy, których dotyczy problem, są wyświetlani w wyświetlonej sekcji **Lista użytkowników** , w której można wybrać niektórych lub wszystkich odnalezionych adresatów.

      Po zakończeniu kliknij pozycję **Zastosuj(x),** a następnie kliknij pozycję **Dodaj użytkowników x**.

  Po powrocie do głównej strony **Użytkownicy docelowi** możesz użyć ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu znalezienia użytkowników, których dotyczy problem. Możesz również kliknąć ikonę ![Usuń użytkowników.](../../media/m365-cc-sc-search-icon.png) **Usuń** , aby usunąć określonych użytkowników.

- ![Ikona importu.](../../media/m365-cc-sc-create-icon.png) **Importuj**: W otwieranym oknie dialogowym określ plik CSV zawierający jeden adres e-mail na wiersz.

  Po znalezieniu wybranego pliku CSV lista użytkowników zostanie zaimportowana i **wyświetlona na stronie Użytkownicy docelowi** . Możesz użyć ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu znalezienia użytkowników, których dotyczy problem. Możesz również kliknąć ikonę ![Usuń użytkowników docelowych.](../../media/m365-cc-sc-delete-icon.png) **Usuń** , aby usunąć określonych użytkowników.

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

Dla każdego szkolenia na liście musisz wybrać, kto pobiera szkolenie, wybierając wartości w kolumnie **Przypisz do** :

- **Wszyscy użytkownicy**

  lub jedną lub obie z następujących wartości:

- **Klikniętego ładunku**
- **Zagrożone**

Jeśli nie chcesz używać pokazanego szkolenia, kliknij pozycję Usuń ikonę ![trenowania.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

:::image type="content" source="../../media/attack-sim-training-training-assignment.png" alt-text="Strona Trenowanie przypisania w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-training-assignment.png":::

Po zakończeniu kliknij przycisk **Dalej**.

### <a name="landing-page"></a>Strona docelowa

Na **stronie Docelowa** skonfigurujesz stronę internetową, do którą użytkownik jest pobierany, jeśli otworzy ładunek w symulacji.

Strony docelowe nadzorowane przez firmę Microsoft są dostępne w 12 językach: chińskim (uproszczonym), chińskim (tradycyjnym), angielskim, francuskim, niemieckim, włoskim, japońskim, koreańskim, portugalskim, rosyjskim, hiszpańskim i holenderskim.

- **Wybierz preferencję strony docelowej**: Dostępne wartości to:
  - **Użyj domyślnej strony docelowej firmy Microsoft**: jest to wartość domyślna, która ma następujące skojarzone opcje konfigurowania:
    - **Wybierz układ strony docelowej**: wybierz jeden z dostępnych szablonów.
    - **Dodaj logo**: kliknij przycisk **Przeglądaj** , aby znaleźć i wybrać plik .png, jpeg lub .gif. Aby uniknąć zniekształceń, rozmiar logo powinien wynosić maksymalnie 210 x 70. Aby usunąć logo, kliknij przycisk **Usuń**.
    - **Dodawanie wskaźników ładunku do poczty e-mail**: to ustawienie jest niedostępne, jeśli wcześniej **wybrano pozycję Załącznik złośliwego oprogramowania** lub **Link do złośliwego oprogramowania** na stronie [Wybieranie techniki](#select-a-social-engineering-technique) .

    Możesz wyświetlić podgląd wyników, klikając przycisk **Otwórz panel podglądu** w dolnej części strony.

  - **Użyj niestandardowego adresu URL**: to ustawienie nie jest dostępne, jeśli wcześniej **wybrano pozycję Załącznik złośliwego oprogramowania** lub **Link do złośliwego oprogramowania** na stronie [Wybieranie techniki](#select-a-social-engineering-technique) .

    Jeśli wybierzesz **pozycję Użyj niestandardowego adresu URL**, musisz dodać adres URL w wyświetlonym polu **Wprowadź niestandardowy adres URL strony docelowej** . Na stronie nie są dostępne żadne inne opcje.

  - **Utwórz własną stronę docelową**: Ta wartość ma następujące skojarzone opcje do skonfigurowania:
    - **Dodawanie wskaźników ładunku do wiadomości e-mail**: to ustawienie jest dostępne do wybrania tylko wtedy, gdy spełnione są oba następujące warunki:
      - Wcześniej wybrano pozycje **Zbieranie poświadczeń**, **Link w załączniku** lub **Adres URL typu Dysk według** na stronie [Wybieranie techniki](#select-a-social-engineering-technique) .
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
        - **Użyj domyślnie**: wybierz dostępny szablon, od którego chcesz zacząć. Możesz zmodyfikować tekst i układ w obszarze edycji. Aby zresetować stronę docelową z powrotem do domyślnego tekstu i układu szablonu, kliknij przycisk **Resetuj do wartości domyślnej**.
    - **Kod**: kod HTML można wyświetlać i modyfikować bezpośrednio.

    Możesz wyświetlić podgląd wyników, klikając przycisk **Otwórz panel podglądu** w środku strony.

Po zakończeniu kliknij przycisk **Dalej**.

> [!NOTE]
> Niektóre znaki towarowe, logo, symbole, insygnia i inne identyfikatory źródłowe otrzymują zwiększoną ochronę zgodnie z lokalnymi, stanowymi i federalnymi ustawami i przepisami. Nieautoryzowane użycie takich wskaźników może naliczać użytkownikom kary, w tym grzywny karne. Choć nie jest to obszerna lista, obejmuje to prezydenckich, wiceprezydenta i Kongresu pieczęci, CIA, FBI, Social Security, Medicare i Medicaid, Stany Zjednoczone Internal Revenue Service i Olimpiady. Poza tymi kategoriami znaków towarowych użycie i modyfikacja jakiegokolwiek znaku towarowego innych firm niesie ze sobą nieodłączne ryzyko. Korzystanie z własnych znaków towarowych i logo w ładunku byłoby mniej ryzykowne, szczególnie w przypadku, gdy organizacja zezwala na korzystanie. Jeśli masz jakiekolwiek dalsze pytania dotyczące tego, co jest lub nie jest odpowiednie do użycia podczas tworzenia lub konfigurowania ładunku, skontaktuj się ze swoimi doradcami prawnymi.

## <a name="select-end-user-notification"></a>Wybieranie powiadomienia użytkownika końcowego

Na stronie **Wybieranie powiadomienia użytkownika końcowego** wybierz jedną z następujących opcji powiadomień:

- **Nie dostarczaj powiadomień**: kliknij przycisk **Kontynuuj** w wyświetlonym oknie dialogowym alertu. Jeśli wybierzesz tę opcję, po kliknięciu przycisku **Dalej** zostanie wyświetlona strona [Szczegóły uruchamiania](#launch-details).

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
      - Karta **Podgląd**: wyświetl komunikat powiadomienia.
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

  Po kliknięciu przycisku **Dalej** zostanie wyświetlona strona [Szczegóły uruchamiania](#launch-details).

- **Dostosowane powiadomienia użytkowników końcowych**: po kliknięciu **przycisku Dalej** zostanie wyświetlona strona **powiadomienia o przypisaniu trenowania** zgodnie z opisem w następnych sekcjach.

### <a name="training-assignment-notification"></a>Powiadomienie o przypisaniu szkolenia

Strona **powiadomienia o przypisaniu trenowania** jest dostępna tylko wtedy, gdy **wybrano opcję Dostosowane powiadomienia użytkownika końcowego** na stronie **[Powiadomienia wybierz użytkownika końcowego](#select-end-user-notification)** .

Na tej stronie przedstawiono następujące powiadomienia i ich skonfigurowane języki:

- **Domyślne powiadomienie o przypisaniu szkolenia firmy Microsoft**
- Wszystkie utworzone wcześniej niestandardowe powiadomienia dotyczące przypisania trenowania.

  Te powiadomienia są również dostępne na karcie **Powiadomienia użytkowników końcowych** w szkoleniu symulacji ataku pod adresem <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>. **Domyślne powiadomienie o przypisaniu szkolenia firmy Microsoft** jest dostępne na karcie **Powiadomienia globalne** . Niestandardowe powiadomienia dotyczące przypisań szkoleniowych są dostępne na karcie **Powiadomienia dzierżawy** . Aby uzyskać więcej informacji, zobacz [Powiadomienia użytkowników końcowych dotyczące trenowania symulacji ataków](attack-simulation-training-end-user-notifications.md).

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

    Te powiadomienia są również dostępne na karcie **Powiadomienia użytkowników końcowych** w szkoleniu symulacji ataku pod adresem <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>. **Domyślne powiadomienie o przypomnieniu szkoleniowym firmy Microsoft** jest dostępne na karcie **Powiadomienia globalne** . Powiadomienia o przypomnieniu o trenowaniu niestandardowym są dostępne na karcie **Powiadomienia dzierżawy** . Aby uzyskać więcej informacji, zobacz [Powiadomienia użytkowników końcowych dotyczące trenowania symulacji ataków](attack-simulation-training-end-user-notifications.md).

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

  - **Nie dostarczaj**: jeśli wybierzesz tę opcję, po kliknięciu przycisku Dalej zostanie wyświetlona strona [Szczegóły uruchamiania](#launch-details).

  - **Dostarczanie po wyświetleniu przez użytkownika informacji o zakończeniu kampanii i zakończeniu kampanii** lub dostarczeniu **natychmiast po zgłoszeniu phish przez użytkownika**: W poniższych sekcjach przedstawiono następujące powiadomienia i ich skonfigurowane języki w **wyświetlonej sekcji Wybierz powiadomienie o pozytywnym wzmocnieniu** :

  - **Domyślne powiadomienie o wzmacnianiu dodatnim firmy Microsoft**
  - Wszystkie utworzone wcześniej niestandardowe powiadomienia o pozytywnym wzmocnieniu.

    Te powiadomienia są również dostępne na karcie **Powiadomienia użytkowników końcowych** w szkoleniu symulacji ataku pod adresem <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>. **Domyślne powiadomienie o pozytywnym wzmocnieniu firmy Microsoft** jest dostępne na karcie **Powiadomienia globalne** . Niestandardowe powiadomienia o pozytywnym wzmacnianiu są dostępne na karcie **Powiadomienia dzierżawy** . Aby uzyskać więcej informacji, zobacz [Powiadomienia użytkowników końcowych dotyczące trenowania symulacji ataków](attack-simulation-training-end-user-notifications.md).

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

## <a name="launch-details"></a>Szczegóły uruchamiania

Na stronie **Szczegóły uruchamiania** wybierz, kiedy uruchomić symulację i kiedy zakończyć symulację. Zatrzymamy przechwytywanie interakcji z tą symulacją po podanej dacie zakończenia.

Dostępne są następujące ustawienia:

- Wybierz jedną z następujących wartości:
  - **Uruchom tę symulację natychmiast po zakończeniu**
  - **Zaplanuj uruchomienie tej symulacji później**: Ta wartość ma następujące skojarzone opcje konfigurowania:
    - **Wybierz datę uruchomienia**
    - **Wybierz godzinę uruchamiania**
- **Skonfiguruj liczbę dni do zakończenia symulacji po**: wartość domyślna to 2.
- **Włączanie dostarczania stref czasowych z obsługą regionu**: dostarczaj pracownikom symulowane komunikaty o atakach w godzinach pracy na podstawie ich regionu.
- **Wyświetl stronę z zebranymi danymi śródmiąższowymi techniką drive-by**: możesz pokazać nakładkę, która pojawia się w przypadku ataków związanych z techniką drive-bu URL. Aby ukryć nakładkę i przejść bezpośrednio do strony docelowej, usuń zaznaczenie tej opcji.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="review-simulation"></a>Przegląd symulacji

Na stronie **Przeglądanie symulacji** możesz przejrzeć szczegóły symulacji.

Kliknij ikonę ![Wyślij test.](../../media/m365-cc-sc-send-icon.png) **Wyślij przycisk testu,** aby wysłać kopię wiadomości e-mail ładunku do siebie (obecnie zalogowanego użytkownika) w celu przeprowadzenia inspekcji.

W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

Po zakończeniu kliknij pozycję **Prześlij**.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Strona Przeglądanie symulacji w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::
