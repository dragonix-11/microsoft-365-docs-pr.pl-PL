---
title: Ładunki do trenowania symulacji ataków
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
description: Administratorzy mogą dowiedzieć się, jak tworzyć ładunki do trenowania symulacji ataków i zarządzać nimi w Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2.
ms.technology: mdo
ms.openlocfilehash: a21e3e72e435e9aaa53fb5fab825be6c490017fe
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840238"
---
# <a name="payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Ładunki do trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

Podczas trenowania symulacji _ataków ładunek_ to wiadomość e-mail wyłudzająca informacje oraz linki lub zawartość załączników, które są prezentowane użytkownikom w symulacjach. Szkolenie z symulacji ataków w Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2 oferuje niezawodny wbudowany katalog ładunków dla dostępnych technik inżynierii społecznej. Można jednak utworzyć niestandardowe ładunki, które będą działać lepiej dla Twojej organizacji.

Aby wyświetlić dostępne ładunki, otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do karty \> Biblioteka **zawartości** **symulacji** \> ataków & **wiadomości e-mail**\>, a następnie wybierz pozycję **Ładunki**. Aby przejść bezpośrednio do karty **Biblioteka zawartości symulacji** , na której można wybrać pozycję **Ładunki**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Ładunki** na karcie **Biblioteka zawartości symulacji** mają dwie karty:

- **Ładunki globalne**: zawiera wbudowane, nie modyfikowalne ładunki.
- **Ładunki dzierżawy**: zawiera utworzone ładunki niestandardowe.

Dla każdego ładunku są wyświetlane następujące informacje:

- **Nazwa ładunku**
- **Typ**: Obecnie ta wartość to zawsze **inżynieria społeczna**.
- **Język**: jeśli ładunek zawiera wiele tłumaczeń, dwa pierwsze języki są wyświetlane bezpośrednio. Aby wyświetlić pozostałe języki, umieść kursor nad ikoną liczbową (na przykład **+10**).
- **Źródło**: W przypadku wbudowanych ładunków wartość to **Globalna**. W przypadku ładunków niestandardowych wartość to **Dzierżawa**.
- **Uruchomiono symulacje**: liczba uruchomionych symulacji korzystających z ładunku.
- **Wskaźnik naruszeń (%)**: w przypadku wbudowanych ładunków ta wartość jest przewidywanym średnim współczynnikiem kompromisu dla symulacji symulacji ataków, które używają tego samego typu ładunku we wszystkich innych organizacjach Microsoft 365.
- **Utworzone przez**: w przypadku wbudowanych ładunków wartość to **Microsoft**. W przypadku ładunków niestandardowych wartość to nazwa UPN użytkownika, który utworzył ładunek.
- **Ostatnia modyfikacja**
- **Technika**: Jedna z dostępnych [technik inżynierii społecznej](attack-simulation-training.md#select-a-social-engineering-technique):
  - **Zbieranie poświadczeń**
  - **Załącznik złośliwego oprogramowania**
  - **Link w załączniku**
  - **Link do złośliwego oprogramowania**
  - **Drive-by URL**
- **Stan**: Wartość to **Gotowe** lub **Wersja robocza**. Na karcie **Globalne ładunki** wartość jest zawsze **gotowa**.

Aby znaleźć ładunek na liście, użyj ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole wyszukiwania** w celu znalezienia nazwy ładunku.

Kliknij ![Ikona filtru.](../../media/m365-cc-sc-filter-icon.png) aby filtrować ładunki według jednej lub z następujących wartości:

- **Złożoność**: **wysoka**, **średnia** i **niska**.
- **Język**
- **Dodawanie tagów**
- **Tematu**
- **Marki**
- **Przemysłu**
- **Bieżące zdarzenie**: **Tak** lub **Nie**.
- **Kontrowersyjne**: **Tak** lub **Nie**.

Aby usunąć co najmniej jedną wyświetlaną kolumnę, kliknij pozycję Dostosuj ikonę ![kolumn.](../../media/m365-cc-sc-customize-icon.png) **Dostosowywanie kolumn**. Domyślnie jedyną kolumną, która nie jest wyświetlana, jest **Platforma**, a ta wartość to obecnie zawsze **wiadomość e-mail**.

Po wybraniu ładunku z listy zostanie wyświetlony wysuwany szczegół z następującymi informacjami:

- **Karta Przegląd** : wyświetl ładunek, gdy użytkownicy go zobaczą. Widoczne są również właściwości ładunku:
  - **Opis ładunku**
  - **Z nazwy**
  - **Z poczty e-mail**
  - **Temat wiadomości e-mail**
  - **Źródło**: W przypadku wbudowanych ładunków wartość to **Globalna**. W przypadku ładunków niestandardowych wartość to **Dzierżawa**.
  - **Tematu**
  - **Marki**
  - **Przemysłu**
  - **Kontrowersyjne**
  - **Bieżące zdarzenie**
  - **Tagi**

- Karta **Symulacje uruchomione**:
  - **Nazwa symulacji**
  - **Częstotliwość klikania**
  - **Wskaźnik naruszona**
  - **Akcja**

## <a name="create-payloads"></a>Tworzenie ładunków

> [!NOTE]
> Niektóre znaki towarowe, logo, symbole, insygnia i inne identyfikatory źródłowe otrzymują zwiększoną ochronę zgodnie z lokalnymi, stanowymi i federalnymi ustawami i przepisami. Nieautoryzowane użycie takich wskaźników może naliczać użytkownikom kary, w tym grzywny karne. Choć nie jest to obszerna lista, obejmuje to prezydenckich, wiceprezydenta i Kongresu pieczęci, CIA, FBI, Social Security, Medicare i Medicaid, Stany Zjednoczone Internal Revenue Service i Olimpiady. Poza tymi kategoriami znaków towarowych użycie i modyfikacja jakiegokolwiek znaku towarowego innych firm niesie ze sobą nieodłączne ryzyko. Korzystanie z własnych znaków towarowych i logo w ładunku byłoby mniej ryzykowne, szczególnie w przypadku, gdy organizacja zezwala na korzystanie. Jeśli masz jakiekolwiek dalsze pytania dotyczące tego, co jest lub nie jest odpowiednie do użycia podczas tworzenia lub konfigurowania ładunku, skontaktuj się ze swoimi doradcami prawnymi.

1. W portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com>przejdź do strony **Email & collaboration** \> **Attack simulation training** \> **Simulation content library** tab Payloads Tenant payloads tab (Karta \> **Ładunki dzierżawy ładunków** usługi **Payloads**\>). Aby przejść bezpośrednio do karty **Biblioteka zawartości symulacji**, na której można wybrać pozycję **Ładunki** i kartę **Ładunki dzierżawy**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

   Kliknij pozycję ![Utwórz ikonę ładunku.](../../media/m365-cc-sc-create-icon.png) **Utwórz ładunek** na **karcie Ładunki dzierżawy** w **obszarze Ładunki** , aby uruchomić kreatora tworzenia ładunku.

   ![Utwórz ładunek na karcie Ładunki dzierżawy w obszarze Ładunki w trenowaniu symulacji ataków w portalu Microsoft 365 Defender.](../../media/attack-sim-training-payload-create.png)

   > [!NOTE]
   > ![Utwórz ikonę ładunku.](../../media/m365-cc-sc-create-icon.png) **Tworzenie ładunku** jest również dostępne na stronie **Wybierz ładunek** kreatora tworzenia symulacji. Aby uzyskać więcej informacji, zobacz [Symulowanie ataku wyłudzania informacji w Ochrona usługi Office 365 w usłudze Defender](attack-simulation-training.md).
   >
   > W dowolnym momencie kreatora tworzenia możesz kliknąć przycisk **Zapisz i zamknąć** , aby zapisać postęp i kontynuować konfigurowanie ładunku później. Możesz wybrać miejsce, w którym zostało przerwane, wybierając powiadomienie na karcie **Ładunki dzierżawy** w **obszarze Ładunki**, a następnie klikając ikonę ![Edytuj ładunek.](../../media/m365-cc-sc-edit-icon.png) **Edytuj ładunek**. Częściowo ukończony ładunek będzie miał wartość **Stan** **— wersja robocza**.

2. Na stronie **Wybierz typ** jedyną wartością, którą można obecnie wybrać, jest **wiadomość e-mail**.

   Kliknij **Dalej**.

3. Na stronie **Wybieranie techniki** dostępne opcje są takie same jak na stronie **Wybieranie techniki** w kreatorze tworzenia symulacji:

   - **Zbieranie poświadczeń**
   - **Załącznik złośliwego oprogramowania**
   - **Link w załączniku**
   - **Link do złośliwego oprogramowania**
   - **Drive-by URL**

   Aby uzyskać więcej informacji, zobacz [Simulate a phishing attack with Attack simulation training in Ochrona usługi Office 365 w usłudze Defender (Symulowanie ataku wyłudzania informacji przy użyciu trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Defender](attack-simulation-training.md)).

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Nazwa ładunku** skonfiguruj następujące ustawienia:

   - **Nazwa**: wprowadź unikatową, opisową nazwę ładunku.
   - **Opis**: wprowadź opcjonalny szczegółowy opis ładunku.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Konfigurowanie ładunku** nadszedł czas na utworzenie ładunku. Wiele dostępnych ustawień zależy od wyboru dokonanego na stronie **Wybieranie techniki** (na przykład linki a załączniki).

   - Sekcja **szczegółów nadawcy**: Skonfiguruj następujące ustawienia:
     - **Z nazwy**
     - **Użyj imienia jako nazwy wyświetlanej**: domyślnie to ustawienie nie jest zaznaczone.
     - **Z adresu e-mail**: jeśli wybierzesz wewnętrzny adres e-mail nadawcy ładunku, ładunek będzie prawdopodobnie pochodzić od innego pracownika. Ten adres e-mail nadawcy zwiększy podatność użytkownika na ładunek i pomoże edukować pracowników na temat ryzyka zagrożeń wewnętrznych.
     - **Temat wiadomości e-mail**

   - Sekcja **Szczegóły załącznika**: Ta sekcja jest dostępna tylko wtedy, gdy **wybrano pozycję Załącznik złośliwego oprogramowania**, **Link w załączniku** lub **Link do złośliwego oprogramowania** na stronie **Wybieranie techniki**. Skonfiguruj następujące ustawienia:
     - **Nadaj załącznikowi nazwę**
     - **Wybierz typ załącznika: Obecnie jedyną** dostępną wartością jest **Docx**.

   - **Link do sekcji załącznika** : ta sekcja jest dostępna tylko wtedy, gdy **wybrano pozycję Połącz ze złośliwym oprogramowaniem** na stronie **Wybieranie techniki** . W polu **Wybierz adres URL, który ma być linkiem do załącznika złośliwego oprogramowania** wybierz jeden z dostępnych adresów URL (te same adresy URL, które zostały opisane w sekcji **Link wyłudzania informacji** ).

     Później osadzisz adres URL w treści wiadomości.

   - Sekcja **linku do wyłudzania informacji**: ta sekcja jest dostępna tylko wtedy, gdy wybrano opcję **Zbieranie poświadczeń**, **Link w załączniku** lub **Adres URL dysku po** stronie **Wybierz technikę**.

     W przypadku **zbioru poświadczeń** lub **adresu URL usługi Drive-by** nazwa pola to **Wybierz adres URL, który ma być linkiem do wyłudzania informacji**. Później osadzisz adres URL w treści wiadomości.

     W polu **Link w załączniku** nazwa pola to **Wybierz adres URL w tym załączniku, który ma być linkiem do wyłudzania informacji**. Później osadzisz adres URL w załączniku.

     Wybierz jedną z dostępnych wartości adresu URL:
  
     - <https://www.mcsharepoint.com>
     - <https://www.attemplate.com>
     - <https://www.doctricant.com>
     - <https://www.mesharepoint.com>
     - <https://www.officence.com>
     - <https://www.officenced.com>
     - <https://www.officences.com>
     - <https://www.officentry.com>
     - <https://www.officested.com>
     - <https://www.prizegives.com>
     - <https://www.prizemons.com>
     - <https://www.prizewel.com>
     - <https://www.prizewings.com>
     - <https://www.shareholds.com>
     - <https://www.sharepointen.com>
     - <https://www.sharepointin.com>
     - <https://www.sharepointle.com>
     - <https://www.sharesbyte.com>
     - <https://www.sharession.com>
     - <https://www.sharestion.com>
     - <https://www.templateau.com>
     - <https://www.templatent.com>
     - <https://www.templatern.com>
     - <https://www.windocyte.com>

     > [!NOTE]
     > Usługa reputacji adresu URL może zidentyfikować co najmniej jeden z tych adresów URL jako niebezpieczny. Przed użyciem adresu URL w symulacji sprawdź dostępność adresu URL w obsługiwanych przeglądarkach internetowych. Aby uzyskać więcej informacji, zobacz [Adresy URL symulacji wyłudzania informacji zablokowane przez usługę Google Sejf Browsing](attack-simulation-training-faq.md#phishing-simulation-urls-blocked-by-google-safe-browsing).

   - Sekcja **zawartości załącznika**: ta sekcja jest dostępna tylko **wtedy, gdy wybrano pozycję Link w załączniku** na stronie **Wybieranie techniki**.

     Edytor tekstów sformatowanych jest dostępny do utworzenia zawartości w ładunku załącznika pliku.

     Użyj kontrolki **Link wyłudzania informacji** , aby dodać wcześniej wybrany adres URL wyłudzania informacji do załącznika.

   - Typowe ustawienia na stronie **Konfigurowanie ładunku** :

     - **Dodawanie tagów**
  
     - **Motyw**: Dostępne wartości to: **Aktywacja konta**, **Weryfikacja konta**, **Rozliczenia**, **Oczyszczanie poczty**, **Odebrane dokumenty**, **Wydatki**, **Faks**, **Raport finansowy**, **Wiadomości przychodzące**, **Faktura**, **Odebrany element**, **Alert logowania**, **Odebrana poczta**, **Inne**, **Hasło**, **Płatność**, **Lista płac**, **Spersonalizowana oferta**, **Kwarantanna** , **praca zdalna**, **przejrzyj komunikat**, **aktualizację zabezpieczeń**, **wstrzymanie usługi**, **wymagany podpis**, **uaktualnienie skrzynki pocztowej Storage**, **weryfikowanie skrzynki pocztowej** lub **poczty głosowej**.
  
     - **Marka**: Dostępne wartości to: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** lub **Inne**.
  
     - **Branża**: Dostępne wartości to: **Bankowość**, **Usługi biznesowe**, **Usługi konsumenckie**, **Edukacja**, **Energia**, **Budownictwo**, **Doradztwo**, **Usługi finansowe**, **Rząd**, **Gościnność**, **Ubezpieczenia**, **Prawne**, **Usługi kurierskie**, **IT**, **Healthcare**, **Produkcja**, **Handel detaliczny**, **Telekomunikacja**, **Nieruchomości** lub **Inne**.

     - **Bieżące zdarzenie**: Dostępne wartości to **Tak** lub **Nie**.

     - **Kontrowersyjne**: Dostępne wartości to **Tak** lub **Nie**.

   - Sekcja **Język**: wybierz język ładunku. Dostępne wartości to: **angielski**, **hiszpański**, **niemiecki**, **japoński**, **francuski**, **portugalski**, **holenderski**, **włoski**, **szwedzki**, **chiński (uproszczony),** **norweski Bokmål**, **polski**, **rosyjski**, **fiński**, **koreański**, **turecki**, **węgierski**, **hebrajski**, **tajski**, **arabski**, **wietnamski**, **słowacki**, **grecki**, **indonezyjski**, **rumuński**, **słoweński**, **chorwacki**, **kataloński** lub **inny**.

   - Sekcja **wiadomości e-mail**:

     - Możesz kliknąć pozycję **Importuj wiadomość e-mail** , a następnie **wybrać plik** , aby zaimportować istniejący plik wiadomości zwykłego tekstu.

     - Na karcie **Tekst** możesz utworzyć ładunek wiadomości e-mail w edytorze tekstu sformatowany.

       - Użyj kontrolki **Tag dynamiczny** , aby spersonalizować wiadomość e-mail dla każdego użytkownika, wstawiając dostępne tagi:
         - **Wstaw nazwę użytkownika**: wartość dodana w treści komunikatu to `${userName}`.
         - **Wstaw imię**: wartość dodana w treści komunikatu to `${firstName}`.
         - **Wstaw nazwisko**: wartość dodana w treści komunikatu to `${lastName}`.
         - **Wstaw nazwę UPN**: wartość dodana w treści komunikatu to `${upn}`.
         - **Wstaw wiadomość e-mail**: wartość dodana w treści wiadomości to `${emailAddress}`.
         - **Wstaw dział**: wartość dodana w treści komunikatu to `${department}`.
         - **Wstaw menedżera**: wartość dodana w treści komunikatu to `${manager}`.
         - **Wstaw telefon komórkowy**: wartość dodana w treści wiadomości to `${mobilePhone}`.
         - **Wstaw miasto**: wartość dodana w treści komunikatu to `${city}`.
         - **Wstaw datę**: wartość dodana w treści komunikatu to `${date|MM/dd/yyyy|offset}`.

         :::image type="content" source="../../media/attack-sim-training-payloads-configure-payload-email-message.png" alt-text="Sekcja Wiadomość e-mail na stronie Konfigurowanie ładunku w kreatorze tworzenia ładunku w trenowaniu symulacji ataków w Ochrona usługi Office 365 w usłudze Microsoft Defender" lightbox="../../media/attack-sim-training-payloads-configure-payload-email-message.png":::

       - Kontrola **linku wyłudzania informacji**: ta kontrolka jest dostępna tylko wtedy, gdy wybrano opcję **Zbiory poświadczeń**, **Link w załączniku** lub **Adres URL drive-by** na stronie **Wybieranie techniki**. Użyj tej kontrolki, aby nadać nazwę i wstawić wcześniej wybrany adres URL w sekcji **Link do wyłudzania informacji** .

       - Kontrola **linku załącznika złośliwego oprogramowania**: ta kontrolka jest dostępna tylko wtedy, gdy **wybrano pozycję Połącz ze złośliwym oprogramowaniem** na stronie **Wybieranie techniki**. Użyj tej kontrolki, aby nadać nazwę i wstawić wcześniej wybrany adres URL w sekcji **Link do załącznika** .

       Po kliknięciu **linku wyłudzania informacji** lub **linku załącznika złośliwego oprogramowania** zostanie otwarte okno dialogowe z monitem o nadenie mu nazwy. Po zakończeniu kliknij przycisk **Potwierdź**.

       Wartość dodana w treści komunikatu (widoczna na karcie **Kod** ) to `<a href="${phishingUrl}" target="_blank">Name value you specified</a>`.

     - Na karcie **Kod** można bezpośrednio wyświetlać i modyfikować kod HTML. Formatowanie i inne kontrolki, takie jak **tag dynamiczny** i **link do wyłudzania informacji** lub **link załącznika złośliwego oprogramowania** , nie są dostępne.

     - Przełącznik **Zastąp wszystkie linki w wiadomości e-mail linkiem wyłudzających informacje** jest dostępny tylko wtedy, gdy wybrano opcję **Zbieranie poświadczeń**, **Link do złośliwego oprogramowania** lub **Adres URL typu Dysk według** na stronie **Wybieranie techniki** . Ten przełącznik może zaoszczędzić czas, zastępując wszystkie linki w wiadomości wcześniej wybranym **linkiem wyłudzającym informacje** lub **linkiem dla adresu URL załącznika** . W tym celu przełącz ustawienie na pozycję ![Przełącz na ikonę.](../../media/scc-toggle-on.png).

   Po zakończeniu kliknij przycisk **Dalej**.

6. Strona **Dodawanie wskaźników** jest dostępna tylko wtedy, gdy wybrano opcję **Zbiory poświadczeń**, **Link w załączniku** lub **Adres URL drive-by** na stronie **Wybieranie techniki** .

   Wskaźniki ułatwiają pracownikom identyfikowanie oznak wyłudzania informacji.

   Na stronie **Dodawanie wskaźników** kliknij pozycję **Dodaj wskaźnik**. W wyświetlonym wysuwie skonfiguruj następujące ustawienia:

   - **Wybierz i wskaźnik, którego chcesz użyć** , i **Gdzie chcesz umieścić ten wskaźnik w ładunku?**:

     Te wartości są ze sobą powiązane. Miejsce, w którym można umieścić wskaźnik, zależy od typu wskaźnika. Dostępne wartości opisano w poniższej tabeli:

     |Typ wskaźnika|Lokalizacja wskaźnika|
     |---|---|
     |**Typ załącznika**|Treść komunikatu|
     |**Rozpraszające szczegóły**|Treść komunikatu|
     |**Fałszowanie domeny**|Treść komunikatu <p> Z adresu e-mail|
     |**Ogólne pozdrowienie**|Treść komunikatu|
     |**Apele humanitarne**|Treść komunikatu|
     |**Niespójność**|Treść komunikatu|
     |**Brak szczegółów nadawcy**|Treść komunikatu|
     |**Język prawny**|Treść komunikatu|
     |**Oferta ograniczona czasowo**|Treść komunikatu|
     |**Imitacja logo lub znakowanie z datą**|Treść komunikatu|
     |**Naśladuje proces służbowy lub biznesowy**|Treść komunikatu|
     |**Bez/minimalne znakowanie**|Treść komunikatu|
     |**Pozuje jako znajomy, współpracownik, przełożony lub urząd**|Treść komunikatu|
     |**Żądanie informacji poufnych**|Treść komunikatu|
     |**Wskaźniki i ikony zabezpieczeń**|Treść komunikatu <p> Temat wiadomości|
     |**Nazwa wyświetlana nadawcy i adres e-mail**|Z nazwy <p> Z adresu e-mail|
     |**Poczucie pilności**|Treść komunikatu <p> Temat wiadomości|
     |**Błędy pisowni i gramatyki**|Treść komunikatu <p> Temat wiadomości|
     |**Język zagrażający**|Treść komunikatu <p> Temat wiadomości|
     |**Zbyt dobre, aby były prawdziwe oferty**|Treść komunikatu|
     |**Nieprofesjonalny wygląd projektu lub formatowania**|Treść komunikatu|
     |**Hiperlinkowanie adresu URL**|Treść komunikatu|
     |**Jesteś wyjątkowy**|Treść komunikatu|
  
     Ta lista jest wyselekcjonowana tak, aby zawierała najczęstsze wskazówki, które pojawiają się w wiadomościach wyłudzających informacje.

     Jeśli jako lokalizację wskaźnika wybierzesz temat wiadomości e-mail lub treść wiadomości, zostanie wyświetlony przycisk **Wybierz tekst** . Kliknij ten przycisk, aby wybrać tekst w treści wiadomości lub tematu wiadomości, w którym ma zostać wyświetlony wskaźnik. Po zakończeniu kliknij pozycję **Wybierz**.

     :::image type="content" source="../../media/attack-sim-training-payloads-add-indicators-select-location.png" alt-text="Wybrana lokalizacja tekstowa w treści wiadomości, która ma zostać dodana do wskaźnika w kreatorze tworzenia ładunku w szkoleniu symulacji ataków" lightbox="../../media/attack-sim-training-payloads-add-indicators-select-location.png":::

     - **Opis wskaźnika**: Możesz zaakceptować domyślny opis wskaźnika lub dostosować go.

     - **Podgląd wskaźnika**: aby zobaczyć, jak wygląda bieżący wskaźnik, kliknij dowolne miejsce w sekcji.

     Po zakończeniu kliknij pozycję **Dodaj**

   Powtórz te kroki, aby dodać wiele wskaźników.

   Na stronie **Dodawanie wskaźników** możesz przejrzeć wybrane wskaźniki:

   - Aby edytować istniejący wskaźnik, wybierz go z listy, a następnie kliknij pozycję ![Edytuj ikonę wskaźnika.](../../media/m365-cc-sc-edit-icon.png) **Edytuj wskaźnik**.

   - Aby usunąć istniejący wskaźnik, wybierz go z listy, a następnie kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

   - Aby przenieść wskaźniki w górę lub w dół na liście, wybierz wskaźnik z listy, a następnie kliknij ikonę ![Przenieś w górę.](../../media/m365-cc-sc-increase-icon.png) **Ikona Przenieś w górę** lub ![Przenieś w dół.](../../media/m365-cc-sc-decrease-icon.png) **Przenieś w dół**.

   Po zakończeniu kliknij przycisk **Dalej**.

7. Na stronie **Przejrzyj ładunek** możesz przejrzeć szczegóły ładunku.

   Kliknij ikonę ![Wyślij test.](../../media/m365-cc-sc-send-icon.png) **Wyślij przycisk testu,** aby wysłać kopię wiadomości e-mail ładunku do siebie (obecnie zalogowanego użytkownika) w celu przeprowadzenia inspekcji.

   Kliknij ikonę wskaźnika podglądu ![.](../../media/m365-cc-sc-open-icon.png) **Przycisk wskaźnika podglądu** umożliwia otwarcie ładunku w wysuwanej wersji zapoznawczej. Wersja zapoznawcza zawiera wszystkie utworzone wskaźniki ładunku.

   Na **głównej stronie Przejrzyj ładunek** możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

   :::image type="content" source="../../media/attack-sim-training-payloads-review-payload.png" alt-text="Strona Przeglądanie ładunku w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-payloads-review-payload.png":::

## <a name="modify-payloads"></a>Modyfikowanie ładunków

Nie można modyfikować wbudowanych ładunków na karcie **Ładunki globalne** . Ładunki niestandardowe można modyfikować tylko na karcie **Ładunki dzierżawy** .

Aby zmodyfikować istniejący ładunek na **karcie Ładunki dzierżawy** , wykonaj jedną z następujących czynności:

- Wybierz ładunek z listy, klikając pole wyboru. Kliknij ikonę Edytuj ![ładunek.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** wyświetloną ikonę ładunku.
- Wybierz ładunek z listy, klikając dowolne miejsce w wierszu z wyjątkiem pola wyboru. W wyświetlonym wysuwu szczegółów kliknij pozycję **Edytuj ładunek**.

Zostanie otwarty kreator ładunku z ustawieniami i wartościami wybranego ładunku. Kroki są takie same, jak opisano w sekcji [Tworzenie ładunków](#create-payloads) .

## <a name="copy-payloads"></a>Kopiowanie ładunków

Aby skopiować istniejący ładunek na **kartach Ładunki dzierżawy** lub **Globalne ładunki** , wybierz ładunek z listy, klikając pole wyboru, a następnie kliknij ikonę Kopiuj ![ładunek.](../../media/m365-cc-sc-edit-icon.png) **Wyświetlona ikona kopiowania ładunku** .

Zostanie otwarty kreator tworzenia ładunku z ustawieniami i wartościami wybranego ładunku. Kroki są takie same, jak opisano w sekcji [Tworzenie ładunków](#create-payloads) .

> [!NOTE]
> Podczas kopiowania wbudowanego ładunku na karcie **Globalne ładunki** należy zmienić wartość **Nazwa** . Jeśli tego nie zrobisz, ładunek pojawi się na stronie **Ładunki dzierżawy** o takiej samej nazwie jak wbudowany ładunek.

## <a name="send-a-test"></a>Wysyłanie testu

Na **kartach Ładunki dzierżawy** lub **Ładunki globalne** możesz wysłać kopię wiadomości e-mail ładunku do siebie (obecnie zalogowanego użytkownika) w celu przeprowadzenia inspekcji.

Wybierz ładunek z listy, klikając pole wyboru, a następnie kliknij ![ikonę Wyślij test.](../../media/m365-cc-sc-send-icon.png) **Wyślij wyświetlony przycisk testu** .

## <a name="related-links"></a>Linki pokrewne

[Wprowadzenie do szkolenia z symulacji ataku](attack-simulation-training-get-started.md)

[Tworzenie symulacji ataku wyłudzania informacji](attack-simulation-training.md)

[Uzyskuj szczegółowe informacje dzięki szkoleniu związanemu z symulacją ataku](attack-simulation-training-insights.md)
