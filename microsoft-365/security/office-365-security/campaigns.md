---
title: Widoki kampanii w planie Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: mcostea
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Dowiedz się więcej o widokach kampanii w Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5308770e4ddb72ead5e4d5dac7506c507aa407f6
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739632"
---
# <a name="campaign-views-in-microsoft-defender-for-office-365"></a>Widoki kampanii w ochronie usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)

Widoki kampanii to funkcja w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2 (na przykład Microsoft 365 E5 lub organizacje z dodatkiem Ochrona usługi Office 365 w usłudze Defender plan 2). Widoki kampanii w portalu Microsoft 365 Defender identyfikuje i kategoryzuje ataki phishingowe w usłudze. Widoki kampanii mogą pomóc w:

- Efektywne badanie ataków wyłudzania informacji i reagowanie na nie.
- Lepiej zrozumieć zakres ataku.
- Pokaż wartość decydentom.

Widoki kampanii pozwalają zobaczyć ogólny obraz ataku szybciej i bardziej kompletnie niż jakikolwiek człowiek.

Obejrzyj ten krótki film wideo, w jaki sposób widoki kampanii w Ochrona usługi Office 365 w usłudze Microsoft Defender pomagają zrozumieć kampanie ataków wymierzone w organizację.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGBL8]

## <a name="what-is-a-campaign"></a>Co to jest kampania?

Kampania to skoordynowany atak e-mail na jedną lub wiele organizacji. Ataki e-mail, które kradną poświadczenia i dane firmowe, to duża i lukratywna branża. Wraz ze wzrostem liczby technologii w celu powstrzymania ataków osoby atakujące modyfikują swoje metody w celu zapewnienia ciągłego sukcesu.

Firma Microsoft korzysta z ogromnych ilości danych chroniących przed wyłudzaniem informacji, ochrony przed spamem i złośliwym oprogramowaniem w całej usłudze, aby ułatwić identyfikowanie kampanii. Analizujemy i klasyfikujemy informacje o ataku według kilku czynników. Przykład:

- **Źródło ataku**: źródłowe adresy IP i domeny wiadomości e-mail nadawcy.
- **Właściwości komunikatu**: zawartość, styl i ton komunikatów.
- **Adresaci wiadomości**: jak adresaci są powiązani. Na przykład domeny adresatów, funkcje zadań adresatów (administratorzy, kadra kierownicza itp.), typy firm (duże, małe, publiczne, prywatne itp.) i branże.
- **Ładunek ataku**: złośliwe linki, załączniki lub inne ładunki w komunikatach.

Kampania może być krótkotrwała lub może obejmować kilka dni, tygodni lub miesięcy z aktywnymi i nieaktywnymi okresami. Może zostać uruchomiona kampania przeciwko określonej organizacji lub twoja organizacja może być częścią większej kampanii w wielu firmach.

## <a name="campaign-views-in-the-microsoft-365-defender-portal"></a>Widoki kampanii w portalu Microsoft 365 Defender

Wyświetlenia kampanii są dostępne w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com> **Email & collaboration** \> **Campaigns** lub bezpośrednio pod adresem <https://security.microsoft.com/campaigns>.

:::image type="content" source="../../media/campaigns-overview.png" alt-text="Omówienie kampanii w portalu Microsoft 365 Defender" lightbox="../../media/campaigns-overview.png":::

Możesz również uzyskać dostęp do widoków kampanii z:

- Współpraca \> **& poczty e-mail** **Explorer** \> **Widok** \> **Kampanie**
- Współpraca \> **& poczty e-mail** **Explorer** \> **Widok** \> **Wszystkie wiadomości e-mail** \> Karta **Kampania**
- Współpraca \> **& poczty e-mail** **Explorer** \> **Widok** \> **Phish** \> Karta **Kampania**
- Współpraca \> **& poczty e-mail** **Explorer** \> **Widok** \> **Złośliwego oprogramowania** \> Karta **Kampania**

Aby uzyskać dostęp do widoków kampanii, musisz być członkiem grup ról **Zarządzanie organizacją**, **Administrator zabezpieczeń** lub **Czytelnik zabezpieczeń** w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="campaigns-overview"></a>Omówienie kampanii

Strona przeglądu zawiera informacje o wszystkich kampaniach.

Na domyślnej karcie **Kampania** obszar **Typ kampanii** zawiera wykres słupkowy pokazujący liczbę adresatów dziennie. Domyślnie na wykresie są wyświetlane zarówno dane **języka Phish** , jak i **złośliwego oprogramowania** .

> [!TIP]
> Jeśli nie widzisz żadnych danych kampanii, spróbuj zmienić zakres dat lub [filtry](#filters-and-settings).

Tabela poniżej wykresu na stronie przeglądu zawiera następujące informacje na karcie **Kampania** :

- **Nazwa**

- **Przykładowy temat**: wiersz tematu jednego z komunikatów w kampanii. Pamiętaj, że wszystkie komunikaty w kampanii nie muszą mieć tego samego tematu.

- **Docelowe**: wartość procentowa obliczona przez: (liczba adresatów kampanii w organizacji) / (całkowita liczba adresatów w kampanii we wszystkich organizacjach w usłudze). Ta wartość wskazuje stopień, w jakim kampania jest kierowana tylko do organizacji (wyższa wartość) a także skierowana do innych organizacji w usłudze (niższa wartość).

- **Typ**: Ta wartość to **Phish** lub **Malware**.

- **Podtyp**: ta wartość zawiera więcej szczegółów na temat kampanii. Przykład:
  - **Phish**: Jeśli jest dostępna, marka, która jest phished przez tę kampanię. Na przykład , `Microsoft`, `365`, `Unknown`, `Outlook`lub `DocuSign`.
  - **Złośliwe oprogramowanie**: na przykład `HTML/PHISH` lub `HTML/<MalwareFamilyName>`.

  Jeśli jest dostępna, marka, która jest phished przez tę kampanię. Gdy wykrywanie jest sterowane przez technologię Ochrona usługi Office 365 w usłudze Defender, prefiks **ATP —** jest dodawany do wartości podtypu.

- **Adresaci**: liczba użytkowników objętych tą kampanią.

- **Skrzynka odbiorcza**: liczba użytkowników, którzy odebrali wiadomości z tej kampanii w skrzynce odbiorczej (nie są dostarczane do folderu Wiadomości-śmieci).

- **Kliknięto**: liczba użytkowników, którzy klikną adres URL lub otworzyli załącznik w wiadomości wyłudzającej informacje.

- **Współczynnik kliknięć**: procent obliczony przez "**Klikniętą** / **skrzynkę odbiorczą**". Ta wartość jest wskaźnikiem skuteczności kampanii. Innymi słowy, jeśli adresaci byli w stanie zidentyfikować wiadomość jako wyłudzającą informacje i jeśli nie kliknęli adresu URL ładunku.

  Pamiętaj, że **współczynnik kliknięć** nie jest używany w kampaniach złośliwego oprogramowania.

- **Odwiedzone**: Ilu użytkowników faktycznie dotarło do witryny sieci Web ładunku. Jeśli istnieją **wartości klikniętych**, ale Sejf Łącza zablokowały dostęp do witryny internetowej, ta wartość będzie równa zero.

Na karcie **Źródło kampanii** są wyświetlane źródła komunikatów na mapie świata.

### <a name="filters-and-settings"></a>Filtry i ustawienia

W górnej części strony **Kampania** istnieje kilka ustawień filtru i zapytań, które ułatwiają znajdowanie i izolowanie określonych kampanii.

:::image type="content" source="../../media/campaign-filters-and-settings.png" alt-text="Filtry kampanii" lightbox="../../media/campaign-filters-and-settings.png":::

Najbardziej podstawowym filtrowaniem, jakie można wykonać, jest data/godzina rozpoczęcia oraz data/godzina zakończenia.

Aby jeszcze bardziej filtrować widok, możesz wykonać pojedynczą właściwość z filtrowaniem wielu wartości, klikając przycisk **Typ kampanii** , wybierając opcję, a następnie klikając przycisk **Odśwież**.

Właściwości kampanii z możliwością filtrowania, które są dostępne na przycisku **Typ kampanii** , zostały opisane na następującej liście:

- **Podstawowe**:
  - **Typ kampanii**: wybierz pozycję **Złośliwe oprogramowanie** lub **Phish**. Wyczyszczenie zaznaczeń ma taki sam wynik jak wybranie obu tych opcji.
  - **Nazwa kampanii**
  - **Podtyp kampanii**
  - **Nadawcy**
  - **Adresatów**
  - **Domena nadawcy**
  - **Temat**
  - **Nazwa pliku załącznika**
  - **Rodzina złośliwego oprogramowania**
  - **Tagi**: użytkownicy lub grupy, dla których zastosowano określony tag użytkownika (w tym konta priorytetowe). Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).
  - **Akcja dostarczania**
  - **Dodatkowa akcja**
  - **Kierunkowość**
  - **Technologia wykrywania**
  - **Oryginalna lokalizacja dostarczania**
  - **Najnowsza lokalizacja dostarczania**
  - **Przesłonięcia systemu**

- **Zaawansowane**:
  - **Identyfikator komunikatu internetowego**: dostępny w polu **nagłówka Message-ID** w nagłówku wiadomości. Przykładowa wartość to `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (zwróć uwagę na nawiasy kątowe).
  - **Identyfikator komunikatu sieciowego**: wartość identyfikatora GUID dostępna w polu nagłówka **X-MS-Exchange-Organization-Network-Message-Id** w nagłówku komunikatu.
  - **Adres IP nadawcy**
  - **Załącznik SHA256**: Aby znaleźć wartość skrótu SHA256 pliku w Windows, uruchom następujące polecenie w wierszu polecenia: `certutil.exe -hashfile "<Path>\<Filename>" SHA256`.
  - **Identyfikator klastra**
  - **Identyfikator alertu**
  - **Identyfikator zasad alertu**
  - **Identyfikator kampanii**
  - **Sygnał adresu URL zap**

- **Adresy URL**:
  - **Domena adresu URL**
  - **Domena i ścieżka adresu URL**
  - **ADRES URL**
  - **Ścieżka adresu URL**
  - **Kliknij werdykt**

Aby uzyskać bardziej zaawansowane filtrowanie, w tym filtrowanie według wielu właściwości, możesz kliknąć przycisk **Filtr zaawansowany** , aby utworzyć zapytanie. Dostępne są te same właściwości kampanii, ale z następującymi ulepszeniami:

- Możesz kliknąć **pozycję Dodaj warunek,** aby wybrać wiele warunków.
- Między warunkami można wybrać operator **And** lub **Or** .
- Możesz wybrać element **grupy Warunek** w dolnej części listy warunków, aby utworzyć złożone warunki złożone.

Po zakończeniu kliknij przycisk **Zapytanie** .

Po utworzeniu filtru podstawowego lub zaawansowanego możesz go zapisać przy użyciu polecenia **Zapisz zapytanie** lub **Zapisz zapytanie jako**. Później, po powrocie do strony **Kampanie** , możesz załadować zapisany filtr, klikając pozycję **Zapisane ustawienia zapytania**.

Aby wyeksportować wykres lub listę kampanii, kliknij pozycję **Eksportuj** i wybierz pozycję **Eksportuj dane wykresu** lub **Eksportuj listę kampanii**.

Jeśli masz subskrypcję Ochrona punktu końcowego w usłudze Microsoft Defender, możesz kliknąć pozycję **MDE Ustawienia**, aby połączyć lub rozłączyć informacje o kampaniach z Ochrona punktu końcowego w usłudze Microsoft Defender. Aby uzyskać więcej informacji, zobacz [Integrowanie Ochrona usługi Office 365 w usłudze Microsoft Defender z Ochrona punktu końcowego w usłudze Microsoft Defender](integrate-office-365-ti-with-mde.md).

## <a name="campaign-details"></a>Szczegóły kampanii

Po kliknięciu nazwy kampanii szczegóły kampanii są wyświetlane w wysuwnym oknie.

### <a name="campaign-information"></a>Informacje o kampanii

W górnej części widoku szczegółów kampanii dostępne są następujące informacje o kampanii:

- **Identyfikator kampanii**: unikatowy identyfikator kampanii.
- **Działanie**: czas trwania i aktywność kampanii.
- Następujące dane dla wybranego filtru zakresu dat (lub wybrane na osi czasu):
- **Wpływ**
- **Komunikaty**: całkowita liczba adresatów.
- **Skrzynka odbiorcza**: liczba wiadomości dostarczonych do skrzynki odbiorczej, a nie do folderu Wiadomości-śmieci.
- **Kliknięto link**: Ilu użytkowników kliknął ładunek adresu URL w wiadomości wyłudzającej informacje.
- **Odwiedzone łącze**: Ilu użytkowników odwiedziło adres URL.
- **Targeted(%)**: procent obliczony przez: (liczbę adresatów kampanii w organizacji) / (całkowita liczba adresatów w kampanii we wszystkich organizacjach w usłudze). Należy pamiętać, że ta wartość jest obliczana przez cały okres istnienia kampanii i nie zmienia się na podstawie filtrów dat.
- Filtry daty/godziny rozpoczęcia i zakończenia danych/godziny dla przepływu kampanii zgodnie z opisem w następnej sekcji.
- Interaktywna oś czasu działania kampanii: oś czasu pokazuje aktywność w całym okresie istnienia kampanii. Możesz zatrzymać kursor nad punktami danych na grafie, aby wyświetlić liczbę wykrytych komunikatów.

:::image type="content" source="../../media/campaign-details-campaign-info.png" alt-text="Informacje o kampanii" lightbox="../../media/campaign-details-campaign-info.png":::

### <a name="campaign-flow"></a>Przepływ kampanii

W widoku szczegółów kampanii ważne szczegóły dotyczące kampanii są prezentowane na diagramie przepływu poziomego (znanym jako diagram _Sankeya_ ). Te szczegóły pomogą Ci zrozumieć elementy kampanii i potencjalny wpływ w organizacji.

> [!TIP]
> Informacje wyświetlane na diagramie przepływu są kontrolowane przez filtr zakresu dat na osi czasu zgodnie z opisem w poprzedniej sekcji.

:::image type="content" source="../../media/campaign-details-no-recipient-actions.png" alt-text="Szczegóły kampanii, które nie zawierają kliknięć adresu URL użytkownika" lightbox="../../media/campaign-details-no-recipient-actions.png":::

Po umieszczeniu wskaźnika myszy na pasmie poziomym na diagramie zobaczysz liczbę powiązanych komunikatów (na przykład komunikatów z określonego źródłowego adresu IP, komunikatów ze źródłowego adresu IP przy użyciu określonej domeny nadawcy itp.).

Diagram zawiera następujące informacje:

- **Adresy IP nadawcy**
- **Domeny nadawcy**
- **Werdykty filtru**: Wartości werdyktów są związane z dostępnymi werdyktami dotyczącymi wyłudzania informacji i filtrowania spamu zgodnie z opisem w [nagłówkach wiadomości antyspamowych](anti-spam-message-headers.md). Dostępne wartości opisano w poniższej tabeli:

  |Value|Werdykt filtru spamu|Opis|
  |---|---|---|
  |**Dozwolone**|`SFV:SKN` <p> `SFV:SKI`|Wiadomość została oznaczona jako niespamowana i/lub pominięta, zanim została oceniona przez filtrowanie spamu. Na przykład wiadomość została oznaczona jako niespamowanie przez regułę przepływu poczty (znaną również jako reguła transportu). <p> Wiadomość pominąła filtrowanie spamu z innych powodów. Na przykład nadawca i adresat są w tej samej organizacji.|
  |**Zablokowany**|`SFV:SKS`|Wiadomość została oznaczona jako spam, zanim została oceniona przez filtrowanie spamu. Na przykład przez regułę przepływu poczty.|
  |**Wykryte**|`SFV:SPM`|Wiadomość została oznaczona jako spam przez filtrowanie spamu.|
  |**Nie wykryto**|`SFV:NSPM`|Wiadomość została oznaczona jako niespamowana przez filtrowanie spamu.|
  |**Wydany**|`SFV:SKQ`|Wiadomość pominąła filtrowanie spamu, ponieważ została zwolniona z kwarantanny.|
  |**Zezwalaj na dzierżawę**<sup>\*</sup>|`SFV:SKA`|Komunikat pominął filtrowanie spamu z powodu ustawień w zasadach ochrony przed spamem. Na przykład nadawca znajdował się na liście dozwolonych nadawców lub na liście dozwolonych domen.|
  |**Blok dzierżawy**<sup>\*\*</sup>|`SFV:SKA`|Wiadomość została zablokowana przez filtrowanie spamu ze względu na ustawienia zasad ochrony przed spamem. Na przykład nadawca znajdował się na liście dozwolonych nadawców lub na liście dozwolonych domen.|
  |**Zezwalaj użytkownikowi**<sup>\*</sup>|`SFV:SFE`|Wiadomość pominąła filtrowanie spamu, ponieważ nadawca znajdował się na liście nadawców Sejf użytkownika.|
  |**Blok użytkownika**<sup>\*\*</sup>|`SFV:BLK`|Wiadomość została zablokowana przez filtrowanie spamu, ponieważ nadawca znajdował się na liście zablokowanych nadawców użytkownika.|
  |**ZAP**|nie dotyczy|[Automatyczne przeczyszczanie bez godziny (ZAP)](zero-hour-auto-purge.md) przeniosło dostarczoną wiadomość do folderu wiadomości-śmieci lub kwarantanny. Akcję można skonfigurować w [zasadach ochrony przed spamem](configure-your-spam-filter-policies.md).|

  <sup>\*</sup> Przejrzyj zasady ochrony przed spamem, ponieważ dozwolona wiadomość prawdopodobnie zostałaby zablokowana przez usługę.

  <sup>\*\*</sup> Przejrzyj zasady ochrony przed spamem, ponieważ te wiadomości powinny zostać poddane kwarantannie, a nie dostarczone.

- **Miejsca docelowe wiadomości**: prawdopodobnie będziesz chciał zbadać komunikaty, które zostały dostarczone do adresatów (do skrzynki odbiorczej lub folderu Wiadomości-śmieci), nawet jeśli użytkownicy nie klikną adresu URL ładunku w wiadomości. Można również usunąć komunikaty poddane kwarantannie z kwarantanny. Aby uzyskać więcej informacji, zobacz [Kwarantanna wiadomości e-mail w EOP](quarantine-email-messages.md).
  - **Usunięty folder**
  - **Spadła**
  - **Zewnętrzne**: adresat znajduje się w lokalnej organizacji poczty e-mail w środowiskach hybrydowych.
  - **Zakończone niepowodzeniem**
  - **Przekazywane**
  - **Skrzynki odbiorczej**
  - **Folder śmieci**
  - **Kwarantanna**
  - **Unknown**

- **Kliknięcia adresu URL**: te wartości zostały opisane w następnej sekcji.

> [!NOTE]
> We wszystkich warstwach zawierających więcej niż 10 elementów jest wyświetlanych 10 pierwszych elementów, a pozostałe są powiązane w **innych**.

#### <a name="url-clicks"></a>Kliknięcia adresu URL

Gdy wiadomość wyłudzająca informacje zostanie dostarczona do folderu Skrzynka odbiorcza lub Wiadomość-śmieci, zawsze istnieje szansa, że użytkownik kliknie adres URL ładunku. Nie kliknięcie adresu URL jest niewielką miarą powodzenia, ale musisz określić, dlaczego wiadomość wyłudzająca informacje została nawet dostarczona do skrzynki pocztowej.

Jeśli użytkownik kliknie adres URL ładunku w wiadomości wyłudzającej informacje, **akcje zostaną wyświetlone w obszarze kliknięć adresu URL** diagramu w widoku szczegółów kampanii.

- **Dozwolone**
- **BlockPage**: adresat kliknął adres URL ładunku, ale dostęp do złośliwej witryny internetowej został zablokowany przez zasady [Sejf Linki](safe-links.md) w organizacji.
- **BlockPageOverride**: adresat kliknął adres URL ładunku w wiadomości, Sejf Łącza próbowały je zatrzymać, ale pozwolono im zastąpić blok. Sprawdź [zasady linków Sejf](set-up-safe-links-policies.md), aby sprawdzić, dlaczego użytkownicy mogą zastąpić werdykt Sejf Links i przejść do złośliwej witryny internetowej.
- **PendingDetonationPage**: Sejf Załączniki w Ochrona usługi Office 365 w usłudze Microsoft Defender jest w trakcie otwierania i badania adresu URL ładunku w środowisku komputera wirtualnego.
- **PendingDetonationPageOverride**: Adresat mógł zastąpić proces detonacji ładunku i otworzyć adres URL bez oczekiwania na wyniki.

### <a name="tabs"></a>Karty

Karty w widoku szczegółów kampanii umożliwiają dalsze badanie kampanii.

> [!TIP]
> Informacje wyświetlane na kartach są kontrolowane przez filtr zakresu dat na osi czasu zgodnie z opisem w sekcji [Informacje o kampanii](#campaign-information) .

- **Kliknięcia adresu URL**: jeśli użytkownicy nie kliknieli adresu URL ładunku w wiadomości, ta sekcja będzie pusta. Jeśli użytkownik mógł kliknąć adres URL, zostaną wypełnione następujące wartości:
  - **Użytkownika**<sup>\*</sup>
  - **ADRES URL**<sup>\*</sup>
  - **Godzina kliknięcia**
  - **Kliknij werdykt**

- **Adresy IP nadawcy**
  - **Adres IP nadawcy**<sup>\*</sup>
  - **Łączna liczba**
  - **Skrzynka odbiorcza**
  - **Nie skrzynka odbiorcza**
  - **Przekazano protokół SPF**: nadawca został uwierzytelniony przez [platformę zasad nadawcy (SPF).](how-office-365-uses-spf-to-prevent-spoofing.md) Nadawca, który nie przechodzi weryfikacji SPF, wskazuje nieuwierzytelnionego nadawcę lub wiadomość podszywa się pod uprawnionego nadawcę.

- **Nadawców**
  - **Nadawca**: jest to rzeczywisty adres nadawcy w poleceniu SMTP MAIL FROM, który niekoniecznie jest adresem e-mail Od: widocznym przez użytkowników na klientach poczty e-mail.
  - **Łączna liczba**
  - **Skrzynka odbiorcza**
  - **Nie skrzynka odbiorcza**
  - **Przekazano moduł DKIM**: nadawca został uwierzytelniony przez wiadomość [e-mail z identyfikatorem kluczy domeny (DKIM).](support-for-validation-of-dkim-signed-messages.md) Nadawca, który nie przechodzi weryfikacji DKIM wskazuje nieuwierzytelnionego nadawcę lub komunikat podszywa się pod uprawnionego nadawcę.
  - **Przekazano DMARC**: nadawca został uwierzytelniony przez [uwierzytelnianie komunikatów oparte na domenie, raportowanie i zgodność (DMARC).](use-dmarc-to-validate-email.md) Nadawca, który nie przejdzie weryfikacji DMARC, wskazuje nieuwierzytelnionego nadawcę lub wiadomość podszywa się pod uprawnionego nadawcę.

- **Załączniki**
  - **Pod nazwą**
  - **SHA256**
  - **Rodzina złośliwego oprogramowania**
  - **Łączna liczba**

- **ADRES URL**
  - **ADRES URL**<sup>\*</sup>
  - **Łączna liczba**

<sup>\*</sup> Kliknięcie tej wartości powoduje otwarcie nowego wysuwanego elementu, który zawiera więcej szczegółów na temat określonego elementu (użytkownika, adresu URL itp.) w widoku szczegółów kampanii. Aby powrócić do widoku szczegółów kampanii, kliknij pozycję **Gotowe** w nowym wysuwu.

### <a name="buttons"></a>Przyciski

Przyciski w dolnej części widoku szczegółów kampanii umożliwiają badanie i rejestrowanie szczegółów kampanii:

- **Eksplorowanie komunikatów**: użyj możliwości Eksploratora zagrożeń, aby dokładniej zbadać kampanię:
  - **Wszystkie komunikaty**: otwiera nową kartę wyszukiwania Eksploratora zagrożeń, używając wartości **Identyfikator kampanii** jako filtru wyszukiwania.
  - **Komunikaty skrzynki odbiorczej**: otwiera nową kartę wyszukiwania Eksploratora zagrożeń przy użyciu **identyfikatora kampanii** i **lokalizacji dostarczania: Skrzynka odbiorcza** jako filtr wyszukiwania.
  - **Komunikaty wewnętrzne**: otwiera nową kartę wyszukiwania Eksploratora zagrożeń przy użyciu **identyfikatora kampanii** i **kierunkowości: wewnątrz organizacji** jako filtru wyszukiwania.

- **Pobierz raport o zagrożeniach**: pobierz szczegóły kampanii do dokumentu programu Word (domyślnie o nazwie CampaignReport.docx). Należy pamiętać, że pobieranie zawiera szczegółowe informacje z całego okresu istnienia kampanii (nie tylko wybrane daty filtru).
