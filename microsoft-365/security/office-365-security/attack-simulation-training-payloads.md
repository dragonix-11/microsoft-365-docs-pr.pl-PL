---
title: Tworzenie niestandardowych ładów na szkolenia symulacyjne z atakami
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
description: Administratorzy mogą dowiedzieć się, jak tworzyć niestandardowe łady dla szkolenia symulacyjnego w programie Microsoft Defender dla programu Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: d670236aa81f4b5086263a75bbeceb8ca7e1e25f
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679769"
---
# <a name="create-custom-payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Tworzenie niestandardowych ładów na platformie Defender for Office 365

**Dotyczy programu** [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)

W szkoleniu symulacyjnych ataków _ładład jest_ wiadomością e-mail wyłudzającą informacje i stronami sieci Web przedstawionymi użytkownikom w symulacyjnych. Szkolenie symulacyjne dotyczące ataków w programie Microsoft 365 E5 lub programie Microsoft Defender dla programu Office 365 Plan 2 oferuje niezawodny wbudowany katalog ładowania dla dostępnych technik społecznościowych. Można jednak utworzyć niestandardowe łady, które będą lepiej działać w Twojej organizacji.

W tym artykule opisano, jak tworzyć własne łady w szkoleniu z symezyjną ataków. Niestandardowe łady można tworzyć w następujących lokalizacjach:

- Karta **Ładowania**: W <https://security.microsoft.com>portalu Microsoft 365 Defender pod adresem przejdź  \> do szkolenia & e-mail **do szkolenia** z symulacjami \> ataków w ramach współpracy **.** Aby przejść bezpośrednio do karty **Łady**, użyj klawisza <https://security.microsoft.com/attacksimulator?viewid=payload>.
- Podczas tworzenia symulacyjnego: Niestandardowe łady można tworzyć na stronie  Wybieranie ładownika (trzecia strona) kreatora tworzenia symulacyjnej. Aby uzyskać więcej informacji, zobacz [Symulowanie ataku służącego do wyłudzania informacji w programie Defender dla Office 365](attack-simulation-training.md).

Aby uzyskać informacje na temat szkolenia z symezyjną ataków, zobacz Wprowadzenie do szkolenia z użyciem [symezyjny](attack-simulation-training-get-started.md) ataków.

> [!NOTE]
> Niektóre znaki towarowe, znaki logo, symbole, insignias i inne identyfikatory źródłowe są chronione na mocy ustaw i ustaw lokalnych, stanowych i federalnych. Nieuprawnione użycie takich wskaźników może nachylić użytkowników do odpowiedzialności, w tym także karnej. Choć nie jest to rozbudowana lista, obejmuje to: Szomówienie, Wicedyrecja i Kopercie, CIA, FBI, Ubezpieczenia społecznego, Opieki medycznej i Anny, Amerykańskiej Administracji Skarbowej i Igrzysk Olimpijskich. Oprócz korzystania z tych kategorii znaków towarowych, korzystanie z znaku towarowego innej firmy i modyfikowanie go wiąże się z ryzykiem. Używanie znaków towarowych i logo w ładowarce byłoby mniej ryzykowne, szczególnie w przypadku, gdy organizacja zezwala na użycie tych znaków. Jeśli masz jakiekolwiek dodatkowe pytania dotyczące tego, co jest lub czego nie należy używać podczas tworzenia lub konfigurowania ładowania, skonsultuj się z doradcami  prawne.

## <a name="create-a-payload"></a>Tworzenie ładu

Po kliknięciu ![ikony Utwórz ład.](../../media/m365-cc-sc-create-icon.png) **Utwórz ład na** karcie Ładowania  na stronie Szkolenia symulacyjne w czasie ataków lub na **[](attack-simulation-training.md#select-a-payload)** stronie Wybierz ładuj kreatora tworzenia symulacyjnego zostanie uruchomiony kreator tworzeniaładowania, który jest opisany w tej sekcji.

### <a name="select-a-payload-type"></a>Wybierz typ ładu

Na **stronie Wybierz typ** jedyną wartością, która można obecnie wybrać, jest Wiadomość **e-mail**.

Kliknij **Dalej**.

### <a name="select-a-social-engineering-technique"></a>Wybieranie techniki społecznościowej

Na **stronie Wybierz technikę** dostępne opcje są takie same jak na stronie [Wybierz](attack-simulation-training.md#select-a-social-engineering-technique) technikę w kreatorze tworzenia symulacji:

- **Zbiór poświadczeń**
- **Załącznik z złośliwym oprogramowaniem**
- **Łącze w załączniku**
- **Link do złośliwego oprogramowania**
- **Adres URL dla dysków**

Po zakończeniu kliknij przycisk **Dalej**.

### <a name="name-and-describe-the-payload"></a>Nazwa i opisz ład

Na stronie **Nazwa usługi Payload** skonfiguruj następujące ustawienia:

- **Nazwa**: Wprowadź unikatową nazwę opisową dla ładu.
- **Opis**: Wprowadź opcjonalny szczegółowy opis ładu.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="configure-the-payload"></a>Konfigurowanie ładu

Na **stronie Konfigurowanie** ładu to czas na tworzenie ładu. Wiele dostępnych ustawień zależy od wyboru dokonanego na stronie **Techniki** wybierania (na przykład łącza a załączniki).

- **Sekcja Szczegóły nadawcy** : Skonfiguruj następujące ustawienia:
  - **Od nazwy**
  - **Użyj imienia jako nazwy wyświetlanej**: Domyślnie to ustawienie nie jest zaznaczone.
  - **Z poczty** e-mail: Jeśli wybierzesz wewnętrzny adres e-mail nadawcy ładu, ład będzie wyświetlany od współpracownika. Ten adres e-mail nadawcy zwiększa ryzyko wrażliwości użytkownika na ład i pomaga w edukacji pracowników w związku z zagrożeniami wewnętrznymi.
  - **Temat wiadomości e-mail**

- **Sekcja szczegółów załącznika**: Ta sekcja jest dostępna tylko w przypadku wybrania załącznika złośliwego **oprogramowania,** linku w załączniku lub **linku** do złośliwego oprogramowania na **stronie Wybierz technikę**. Skonfiguruj następujące ustawienia:
  - **Nadaj nazwę załącznikowi**
  - **Wybierz typ załącznika**: Obecnie jedyną dostępną wartością jest **docx**.

- **Link do sekcji załącznika**: Ta sekcja jest dostępna tylko wtedy, gdy na stronie **Select technique (Wybierz technikę**) wybrano pozycję **Link do** złośliwego oprogramowania. W polu **Wybierz adres URL** , który ma być linkiem do załącznika złośliwego **oprogramowania wybierz** jeden z dostępnych adresów URL (te same adresy URL, które opisano w sekcji Link do wyłudzania informacji).

  Później osadzisz adres URL w treści wiadomości.

- **Sekcja linku Wyłudzanie** informacji: Ta sekcja jest dostępna tylko w przypadku wybrania opcji Poświadczenie **zbiorów**, **Link** w załączniku lub Adres **URL dysków** według na **stronie Wybierz technikę** .

  W **przypadku poświadczeń lub** **adresu URL dysków** nazwa pola to Wybierz adres URL, który ma **być linkiem do wyłudzania informacji**. Później osadzisz adres URL w treści wiadomości.

  W **przypadku linku w** załączniku nazwa pola to Wybierz adres URL w tym załączniku, **który ma być linkiem** do wyłudzania informacji. Później osadzisz adres URL w załączniku.

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
  > Usługa reputacji adresu URL może zidentyfikować co najmniej jeden z tych adresów URL jako niebezpieczne. Sprawdź dostępność adresu URL w obsługiwanych przeglądarkach internetowych przed użyciem go w czasie symulacyjnej. Aby uzyskać więcej informacji, zobacz [Adresy URL symulowania wyłudzania informacji zablokowane przez przeglądanie Sejf Google](attack-simulation-training-faq.md#phishing-simulation-urls-blocked-by-google-safe-browsing).

- **Sekcja zawartości** załącznika: Ta sekcja jest dostępna tylko wtedy, gdy na **stronie Wybierz technikę** wybrano **link** w załączniku.

  Dostępny jest edytor tekstów sformatowanych do tworzenia zawartości w ładowanych załącznikach plików.

  Użyj kontrolki **Link wyłudzania** informacji, aby dodać do załącznika wcześniej wybrany adres URL wyłudzających informacje.

- Typowe ustawienia:
  - **Dodawanie tagów**
  - **Motyw**: Dostępne **wartości to:** Aktywacja **konta, Weryfikacja** **konta, Rozliczenia****,** Oczyszczanie **poczty,** Odebrano **dokument, Koszt**, **Faks****, Raport** **finansowy, Przychodzące** **wiadomości, Faktura****,** Otrzymano element, **Alert logowania****,** Otrzymano pocztę **, Inne****, Hasło****, Płatności**, **Płace**, **Spersonalizowana** oferta, **Kwarantanna** , **Praca zdalna**, **Przejrzenie wiadomości**, **Aktualizacja zabezpieczeń****,** Wstrzymana usługa, Podpis **wymagany**, Uaktualnij skrzynkę **pocztową Storage**, Zweryfikuj skrzynkę **pocztową** lub **Pocztę głosową**.
  - **Marka**: Dostępne wartości to: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** lub **Inne**.
  - **Branża**: Dostępne **wartości** **to:** Bankowość **, Usługi** **biznesowe, Usługi** dla klientów **indywidualnych, Edukacja****, Energy****,** Konsygnacja, **Consulting**, Usługi finansowe, **Rząd****,** Dorównanie, **Ubezpieczenia, Prawne****,** **Courier services**, **IT****, Opieka** zdrowotna **, Produkcja**, **Sprzedaż** detaliczna, **Telecom**, **Nieruchomości** lub **Inne**.
  - **Bieżące zdarzenie**: Dostępne wartości to **Tak** lub **Nie**.
  - **Wymierne**: Dostępne wartości to **Tak** lub **Nie**.

- **Sekcja** Język: Wybierz język ładu. Dostępne **wartości to:** angielski, hiszpański, niemiecki, **japoński, francuski****,** **portugalski****, holenderski****, włoski****, szwedzki**, chiński **(****uproszczony), norweski (bokmål**), polski, rosyjski **, fiński,** **koreański,** **turecki,** węgierski, **hebrajski**, **tajski****, arabski**, **wietnamski****, słowacki**, **grecki**, **indonezyjski**, **rumuński**, **słoweński**, **chorwacki****,** kataloński lub **inny**.

- **Sekcja wiadomości e-mail** :

  - Możesz kliknąć pozycję **Importuj pocztę e-mail** , a następnie **pozycję Wybierz plik** , aby zaimportować istniejący plik wiadomości w formacie zwykłego tekstu.

  - Na **karcie Tekst** dostępny jest edytor tekstów sformatowanych, który umożliwia tworzenie ładu wiadomości e-mail.

    - Użyj **kontrolki tagu dynamicznego** , aby spersonalizować wiadomość e-mail dla każdego użytkownika, wstawiając dostępne tagi:
      - **Wstaw nazwę**: Wartość dodana w treści wiadomości to `${userName}`.
      - **Wstaw wiadomość** e-mail: Wartość dodana w treści wiadomości to `${emailAddress}`.

      ![Sekcja Wiadomość e-mail na stronie Konfigurowanie obciążenia w kreatorze tworzenia przepływu pracy w sekcji Szkolenia symulacyjne dotyczące ataków w programie Microsoft Defender dla systemu Office 365.](../../media/attack-sim-training-payloads-configure-payload-email-message.png)

      **Kontrolka łączenia wyłudzania** informacji: Ta kontrolka jest dostępna tylko w przypadku wybrania opcji Poświadczenie **zbiorów**, **Link** w załączniku lub Adres **URL dysków** na **stronie Techniki wybierania** . Użyj tej kontrolki, aby wstawić wcześniej wybrany adres URL w sekcji **Link wyłudzania** informacji.

      **Kontrolka linku załącznika** złośliwego oprogramowania: Ta kontrolka jest dostępna tylko wtedy, gdy na **stronie Wybierz technikę** wybrano **pozycję Połącz** z złośliwym oprogramowaniem. Użyj tej kontrolki, aby wstawić wcześniej wybrany adres URL w **sekcji Link do załącznika** .

      Jeśli klikniesz link **wyłudzania informacji** lub **link** do załącznika złośliwego oprogramowania, zostanie otwarte okno dialogowe z prośbą o nadanie linku nazwę. Po zakończeniu kliknij pozycję **Potwierdź**.

      Wartość dodana w treści wiadomości (widoczna na **karcie** Kod) to `<a href="${phishingUrl}" target="_blank">Name value you specified</a>`.

  - Na **karcie** Kod możesz bezpośrednio wyświetlać i modyfikować kod HTML. Formatowanie i inne kontrolki, takie jak **link tagu dynamicznego** i **link wyłudzania** informacji lub **link** do załącznika złośliwego oprogramowania, nie są dostępne.

  - Przełącznik **Zamień** wszystkie linki w wiadomości **e-mail** na link wyłudzania informacji jest dostępny tylko **wtedy, gdy** wybrano opcję Zbioru poświadczeń **, Link** do złośliwego oprogramowania lub Adres URL dysków na **stronie Techniki** wybierania. Ten przełącznik pozwala zaoszczędzić czas, zastępując wszystkie linki w wiadomości wcześniej wybranym linkiem wyłudzaniem informacji lub **łączem dla adresu URL załącznika**. W tym celu włącz ![](../../media/scc-toggle-on.png)ikonę Włącz.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="add-indicators-to-phishing-clues"></a>Dodawanie wskaźników do wskazówek wyłudzających informacje

> [!NOTE]
> Wskaźniki są niedostępne, jeśli na stronie Wybierz technikę wybrano załącznik **złośliwego** oprogramowania lub link do **złośliwego** oprogramowania.

Wskaźniki pomagają pracownikom w czasie symkusyjną ataków w celu zidentyfikowania znaków odsuwu wiadomości wyłudzających informacje.

Na **stronie Dodawanie wskaźników** kliknij pozycję **Dodaj wskaźnik**. W wyświetlonym wysuwanych menu skonfiguruj następujące ustawienia:

- **Nazwa wskaźnika** i **lokalizacja wskaźnika**: Te wartości są powiązane. Miejsce, w którym można umieścić wskaźnik, zależy od samego wskaźnika. Dostępne wartości opisano w poniższej tabeli:

  |Nazwa wskaźnika|Lokalizacja wskaźnika|
  |---|---|
  |**Typ załącznika**|Treść wiadomości|
  |**Szczegół rozpraszający**|Treść wiadomości|
  |**Spoofing domeny**|Treść wiadomości <p> Z adresu e-mail|
  |**Ogólne powitanie**|Treść wiadomości|
  |**Atrakcyjność wytłaczy**|Treść wiadomości|
  |**Niespójność**|Treść wiadomości|
  |**Brak szczegółów nadawcy**|Treść wiadomości|
  |**Język prawni**|Treść wiadomości|
  |**Oferta ograniczony czas**|Treść wiadomości|
  |**Imitacja logo lub znakowanie dat**|Treść wiadomości|
  |**Naśladuje proces służbowy lub biznesowy**|Treść wiadomości|
  |**Nie/minimalne znakowanie**|Treść wiadomości|
  |**Poses as friend, colleague, supervisor, or authority figure**|Treść wiadomości|
  |**Żądanie informacji poufnych**|Treść wiadomości|
  |**Wskaźniki i ikony zabezpieczeń**|Treść wiadomości <p> Temat wiadomości|
  |**Nazwa wyświetlana nadawcy i adres e-mail**|Od nazwy <p> Z adresu e-mail|
  |**Nieciekawość**|Treść wiadomości <p> Temat wiadomości|
  |**Błędy pisowni i gramatyki**|Treść wiadomości <p> Temat wiadomości|
  |**Język językowy**|Treść wiadomości <p> Temat wiadomości|
  |**Oferty są zbyt dobre, aby można było je znaleźć**|Treść wiadomości|
  |**Nieprofejny wygląd projektu lub formatowania**|Treść wiadomości|
  |**Hiperłącze adresu URL**|Treść wiadomości|
  |**Jesteś szczególnym użytkownikom**|Treść wiadomości|
  
  Ta lista jest wyświetlana w taki sposób, aby zawierała najczęstsze wskazówki, które pojawiają się w wiadomościach wyłudzających informacje.

  Jeśli jako lokalizację wskaźnika wybierzesz temat wiadomości e-mail lub treść wiadomości, dostępny jest przycisk  Zaznacz tekst. Kliknij ten przycisk, aby zaznaczyć tekst w temacie wiadomości lub w treści wiadomości, w którym ma się pojawić wskaźnik. Po zakończeniu kliknij pozycję **Wybierz**.

  ![Zaznaczona lokalizacja tekstu w treści wiadomości, aby dodać ją do wskaźnika w kreatorze tworzenia przepływu pracy w szkoleniu symezyjny ataków.](../../media/attack-sim-training-payloads-add-indicators-select-location.png)

  - **Opis wskaźnika**: możesz zaakceptować domyślny opis wskaźnika lub dostosować go.

  - **Podgląd wskaźnika**: aby zobaczyć, jak wygląda bieżący wskaźnik, kliknij w tej sekcji.

  Po zakończeniu kliknij pozycję **Dodaj**

Powtórz czynności opisane w tej sekcji, aby dodać wiele wskaźników.

Aby edytować istniejący wskaźnik, wybierz go z listy, a następnie kliknij ikonę ![Edytuj wskaźnik.](../../media/m365-cc-sc-edit-icon.png) **Edytuj ład.**

Aby usunąć istniejący wskaźnik, zaznacz go na liście, a następnie kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="review-payload"></a>Przejrzyj ład

Na **stronie Przeglądanie ładu** możesz przejrzeć szczegóły ładu.

Kliknij ikonę ![Wyślij test.](../../media/m365-cc-sc-send-icon.png) **Wyślij przycisk testu** , aby wysłać kopię wiadomości e-mail z obciążeniem do siebie (obecnie zalogowanego użytkownika) do inspekcji.

Kliknij ikonę ![wskaźnika Podgląd.](../../media/m365-cc-sc-open-icon.png) **Przycisk wskaźnika** podglądu umożliwia otwarcie ładowania w wysuwanych oknach podglądu. Podgląd zawiera wszystkie utworzone wskaźniki obciążenia.

Na głównej **stronie Przeglądanie ładu** możesz wybrać pozycję **Edytuj w każdej** sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

Po zakończeniu kliknij pozycję **Prześlij**. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

![Przejrzyj stronę szkoleń z symezyjną ataku w portalu Microsoft 365 Defender sieci Web.](../../media/attack-sim-training-payloads-review-payload.png)

> [!IMPORTANT]
> Utworzone łady będą mieć wartość **Dzierżawa** dla **właściwości Źródło** . Podczas tworzenia symulowań i wybierania ładowań upewnij się, że nie odfiltrowywuje się **wartości źródłowej** **dzierżawy**.

## <a name="related-links"></a>Linki pokrewne

[Wprowadzenie do korzystania ze szkolenia symulacyjnego w zakresie ataków](attack-simulation-training-get-started.md)

[Tworzenie symulacyjnej próby wyłudzania informacji](attack-simulation-training.md)

[Uzyskaj szczegółowe informacje dzięki szkoleniom symulacyjnych ataków](attack-simulation-training-insights.md)
