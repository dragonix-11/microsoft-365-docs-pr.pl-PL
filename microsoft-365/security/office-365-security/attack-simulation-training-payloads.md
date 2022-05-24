---
title: Tworzenie niestandardowych ładunków na potrzeby szkolenia z symulacji ataków
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
description: Administratorzy mogą dowiedzieć się, jak tworzyć niestandardowe ładunki do trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2.
ms.technology: mdo
ms.openlocfilehash: f0f91eb3936d1dc4ed6c028552b37fecb5df2ff6
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648310"
---
# <a name="create-custom-payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Tworzenie niestandardowych ładunków na potrzeby trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

W trenowaniu symulacji ataków _ładunek_ to wiadomość e-mail wyłudzająca informacje i strony internetowe, które są prezentowane użytkownikom w symulacjach. Szkolenie z symulacji ataków w Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2 oferuje niezawodny wbudowany katalog ładunków dla dostępnych technik inżynierii społecznej. Można jednak utworzyć niestandardowe ładunki, które będą działać lepiej dla Twojej organizacji.

W tym artykule opisano sposób tworzenia własnych ładunków podczas trenowania symulacji ataków. Ładunki niestandardowe można tworzyć w następujących lokalizacjach:

- Karta **Ładunki**: w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do karty **Ładunki trenowania** \> symulacji **ataków** & **współpracy pocztą** \> e-mail. Aby przejść bezpośrednio do karty **Ładunki**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=payload>.
- Podczas tworzenia symulacji: niestandardowe ładunki można tworzyć na stronie **Wybieranie ładunku** (trzecia strona) kreatora tworzenia symulacji. Aby uzyskać więcej informacji, zobacz [Symulowanie ataku wyłudzania informacji w Ochrona usługi Office 365 w usłudze Defender](attack-simulation-training.md).

Aby uzyskać informacje o rozpoczęciu trenowania symulacji ataków, zobacz [Wprowadzenie korzystanie z trenowania symulacji ataków](attack-simulation-training-get-started.md).

> [!NOTE]
> Niektóre znaki towarowe, logo, symbole, insygnia i inne identyfikatory źródłowe otrzymują zwiększoną ochronę zgodnie z lokalnymi, stanowymi i federalnymi ustawami i przepisami. Nieautoryzowane użycie takich wskaźników może naliczać użytkownikom kary, w tym grzywny karne. Choć nie jest to obszerna lista, obejmuje to prezydenckich, wiceprezydenta i Kongresu pieczęci, CIA, FBI, Social Security, Medicare i Medicaid, Stany Zjednoczone Internal Revenue Service i Olimpiady. Poza tymi kategoriami znaków towarowych użycie i modyfikacja jakiegokolwiek znaku towarowego innych firm niesie ze sobą nieodłączne ryzyko. Korzystanie z własnych znaków towarowych i logo w ładunku byłoby mniej ryzykowne, szczególnie w przypadku, gdy organizacja zezwala na korzystanie. Jeśli masz jakiekolwiek dalsze pytania dotyczące tego, co jest lub nie jest odpowiednie do użycia podczas tworzenia lub konfigurowania ładunku, skontaktuj się ze swoimi doradcami prawnymi.

## <a name="create-a-payload"></a>Tworzenie ładunku

Po kliknięciu przycisku ![Utwórz ikonę ładunku.](../../media/m365-cc-sc-create-icon.png) **Utwórz ładunek** na **karcie Ładunki** szkolenia symulacji ataku lub na stronie **[Wybieranie ładunku](attack-simulation-training.md#select-a-payload)** kreatora tworzenia symulacji zostanie uruchomiony kreator tworzenia ładunku i zostanie opisany w tej sekcji.

### <a name="select-a-payload-type"></a>Wybieranie typu ładunku

Na stronie **Wybierz typ** jedyną wartością, którą można obecnie wybrać, jest **wiadomość e-mail**.

Kliknij **Dalej**.

### <a name="select-a-social-engineering-technique"></a>Wybieranie techniki inżynierii społecznej

Na stronie **Wybieranie techniki** dostępne opcje są takie same jak na stronie [Wybieranie techniki](attack-simulation-training.md#select-a-social-engineering-technique) w kreatorze tworzenia symulacji:

- **Zbieranie poświadczeń**
- **Załącznik złośliwego oprogramowania**
- **Link w załączniku**
- **Link do złośliwego oprogramowania**
- **Drive-by URL**

Po zakończeniu kliknij przycisk **Dalej**.

### <a name="name-and-describe-the-payload"></a>Nazwij i opisz ładunek

Na stronie **Nazwa ładunku** skonfiguruj następujące ustawienia:

- **Nazwa**: wprowadź unikatową, opisową nazwę ładunku.
- **Opis**: wprowadź opcjonalny szczegółowy opis ładunku.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="configure-the-payload"></a>Konfigurowanie ładunku

Na stronie **Konfigurowanie ładunku** nadszedł czas na utworzenie ładunku. Wiele dostępnych ustawień zależy od wyboru dokonanego na stronie **Wybieranie techniki** (na przykład linki a załączniki).

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

- Typowe ustawienia:
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
      - **Wstaw nazwę**: wartość dodana w treści komunikatu to `${userName}`.
      - **Wstaw wiadomość e-mail**: wartość dodana w treści wiadomości to `${emailAddress}`.

      :::image type="content" source="../../media/attack-sim-training-payloads-configure-payload-email-message.png" alt-text="Sekcja Wiadomość e-mail na stronie Konfigurowanie ładunku w kreatorze tworzenia ładunku w trenowaniu symulacji ataków w Ochrona usługi Office 365 w usłudze Microsoft Defender" lightbox="../../media/attack-sim-training-payloads-configure-payload-email-message.png":::

      Kontrola **linku wyłudzania informacji**: ta kontrolka jest dostępna tylko wtedy, gdy wybrano opcję **Zbiory poświadczeń**, **Link w załączniku** lub **Adres URL drive-by** na stronie **Wybieranie techniki**. Użyj tej kontrolki, aby wstawić wcześniej wybrany adres URL w sekcji **Link do wyłudzania informacji** .

      Kontrola **linku załącznika złośliwego oprogramowania**: ta kontrolka jest dostępna tylko wtedy, gdy **wybrano pozycję Połącz ze złośliwym oprogramowaniem** na stronie **Wybieranie techniki**. Użyj tej kontrolki, aby wstawić wcześniej wybrany adres URL w sekcji **Link do załącznika** .

      Jeśli klikniesz **link wyłudzający informacje** lub **link załącznika złośliwego oprogramowania**, zostanie otwarte okno dialogowe z monitem o nadenie mu nazwy. Po zakończeniu kliknij przycisk **Potwierdź**.

      Wartość dodana w treści komunikatu (widoczna na karcie **Kod** ) to `<a href="${phishingUrl}" target="_blank">Name value you specified</a>`.

  - Na karcie **Kod** można bezpośrednio wyświetlać i modyfikować kod HTML. Formatowanie i inne kontrolki, takie jak **tag dynamiczny** i **link do wyłudzania informacji** lub **link załącznika złośliwego oprogramowania** , nie są dostępne.

  - Przełącznik **Zastąp wszystkie linki w wiadomości e-mail linkiem wyłudzających informacje** jest dostępny tylko wtedy, gdy wybrano opcję **Zbieranie poświadczeń**, **Link do złośliwego oprogramowania** lub **Adres URL typu Dysk według** na stronie **Wybieranie techniki** . Ten przełącznik może zaoszczędzić czas, zastępując wszystkie linki w wiadomości wcześniej wybranym **linkiem wyłudzającym informacje** lub **linkiem dla adresu URL załącznika** . W tym celu przełącz ustawienie na pozycję ![Przełącz na ikonę.](../../media/scc-toggle-on.png).

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="add-indicators-to-phishing-clues"></a>Dodawanie wskaźników do wskazówek dotyczących wyłudzania informacji

> [!NOTE]
> Wskaźniki nie są dostępne w przypadku **wybrania załącznika złośliwego oprogramowania** lub **linku do złośliwego oprogramowania** na stronie **Wybieranie techniki** .

Wskaźniki pomagają pracownikom przechodzącym przez symulację ataku zidentyfikować znaki ostrzegawcze wiadomości wyłudzających informacje.

Na stronie **Dodawanie wskaźników** kliknij pozycję **Dodaj wskaźnik**. Na wyświetlonym wysuwie skonfiguruj następujące ustawienia:

- **Nazwa wskaźnika** i **lokalizacja wskaźnika**: te wartości są ze sobą powiązane. Miejsce, w którym można umieścić wskaźnik, zależy od samego wskaźnika. Dostępne wartości opisano w poniższej tabeli:

  |Nazwa wskaźnika|Lokalizacja wskaźnika|
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

  Jeśli jako lokalizację wskaźnika wybierzesz temat wiadomości e-mail lub treść wiadomości, dostępny jest przycisk **Wybierz tekst** . Kliknij ten przycisk, aby wybrać tekst w treści wiadomości lub tematu wiadomości, w którym ma zostać wyświetlony wskaźnik. Po zakończeniu kliknij pozycję **Wybierz**.

  :::image type="content" source="../../media/attack-sim-training-payloads-add-indicators-select-location.png" alt-text="Wybrana lokalizacja tekstowa w treści wiadomości, która ma zostać dodana do wskaźnika w kreatorze tworzenia ładunku w szkoleniu symulacji ataków" lightbox="../../media/attack-sim-training-payloads-add-indicators-select-location.png":::

  - **Opis wskaźnika**: Możesz zaakceptować domyślny opis wskaźnika lub dostosować go.

  - **Podgląd wskaźnika**: aby zobaczyć, jak wygląda bieżący wskaźnik, kliknij w tej sekcji.

  Po zakończeniu kliknij pozycję **Dodaj**

Powtórz kroki opisane w tej sekcji, aby dodać wiele wskaźników.

Aby edytować istniejący wskaźnik, wybierz go z listy, a następnie kliknij pozycję ![Edytuj ikonę wskaźnika.](../../media/m365-cc-sc-edit-icon.png) **Edytuj ładunek**.

Aby usunąć istniejący wskaźnik, wybierz go z listy, a następnie kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="review-payload"></a>Przejrzyj ładunek

Na stronie **Przejrzyj ładunek** możesz przejrzeć szczegóły ładunku.

Kliknij ikonę ![Wyślij test.](../../media/m365-cc-sc-send-icon.png) **Wyślij przycisk testu,** aby wysłać kopię wiadomości e-mail ładunku do siebie (obecnie zalogowanego użytkownika) w celu przeprowadzenia inspekcji.

Kliknij ikonę wskaźnika podglądu ![.](../../media/m365-cc-sc-open-icon.png) **Przycisk wskaźnika podglądu** umożliwia otwarcie ładunku w wysuwanej wersji zapoznawczej. Wersja zapoznawcza zawiera wszystkie utworzone wskaźniki ładunku.

Na **głównej stronie Przejrzyj ładunek** możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

Po zakończeniu kliknij pozycję **Prześlij**. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

:::image type="content" source="../../media/attack-sim-training-payloads-review-payload.png" alt-text="Strona Przeglądanie ładunku w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-payloads-review-payload.png":::

> [!IMPORTANT]
> Utworzone ładunki będą miały wartość **Dzierżawa** dla właściwości **Source** . Podczas tworzenia symulacji i wybierania ładunków upewnij się, że nie filtrujesz **dzierżawy** wartości **źródłowej**.

## <a name="related-links"></a>Linki pokrewne

[Wprowadzenie do szkolenia z symulacji ataku](attack-simulation-training-get-started.md)

[Tworzenie symulacji ataku wyłudzania informacji](attack-simulation-training.md)

[Uzyskuj szczegółowe informacje dzięki szkoleniu związanemu z symulacją ataku](attack-simulation-training-insights.md)
