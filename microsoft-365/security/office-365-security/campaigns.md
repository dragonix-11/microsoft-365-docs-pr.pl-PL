---
title: Widoki kampanii w programie Microsoft Defender dla Office 365 plan
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
description: Dowiedz się więcej o widokach kampanii w programie Microsoft Defender dla Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 479963323dad613f3a17a527f94bbd5963487f76
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021365"
---
# <a name="campaign-views-in-microsoft-defender-for-office-365"></a>Widoki kampanii w programie Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)

Widoki kampanii to funkcja programu Microsoft Defender dla systemu Office 365 (plan 2) (na przykład Microsoft 365 E5 lub organizacji z dodatku Defender for Office 365 Plan 2). Widoki kampanii w portalu Microsoft 365 Defender identyfikują i kategoryzują ataki służące do wyłudzania informacji w usłudze. Widoki kampanii mogą ułatwić:

- Efektywne badanie i reagowanie na ataki służące do wyłudzania informacji.
- Lepsze zrozumienie zakresu ataków.
- Pokazanie wartości dla osób decyzyjnych.

Widoki kampanii pozwalają szybciej i pełniej ominić ataki niż użytkownicy.

## <a name="what-is-a-campaign"></a>Co to jest kampania?

Kampania to skoordynowany atak poczty e-mail wobec jednej lub wielu organizacji. Ataki poczty e-mail, które ukraść poświadczenia i dane firmowe to duża i dochodowa branża. W związku z zwiększaniem się technologii w celu zatrzymania ataków atakujący modyfikują swoje metody w celu zapewnienia sukcesu.

Firma Microsoft wykorzystuje ogromną ilość danych ochrony przed wyłudzaniem informacji, spamem i złośliwym oprogramowaniem w całej usłudze, aby ułatwić identyfikowanie kampanii. Dane dotyczące ataków są analizowane i klasyfikowane według kilku czynników. Przykład:

- **Źródło ataków**: źródłowe adresy IP i domeny poczty e-mail nadawcy.
- **Właściwości wiadomości**: zawartość, styl i ton wiadomości.
- **Adresaci wiadomości**: w jaki sposób są powiązani adresaci. Mogą to być na przykład domeny adresatów, funkcje pracy adresata (administratorzy,  kierownictwo itp.), typy firm (duże, małe, publiczne, prywatne itd.) oraz branże.
- **Ład ataku**: złośliwe linki, załączniki lub inne łady w wiadomościach.

Kampania może być krótka lub może obejmować kilka dni, tygodni lub miesięcy z okresami aktywnymi i nieaktywnymi. Kampania może zostać rozpoczęta wobec konkretnej organizacji lub może stanowić część większej kampanii w wielu firmach.

## <a name="campaign-views-in-the-microsoft-365-defender-portal"></a>Widoki kampanii w portalu Microsoft 365 Defender kampanii

Widoki kampanii są dostępne w portalu Microsoft 365 Defender pod <https://security.microsoft.com> adresem Poczta **& kampanie** \> dotyczące współpracy lub bezpośrednio pod adresem .<https://security.microsoft.com/campaigns>

![Omówienie kampanii w portalu Microsoft 365 Defender sieci.](../../media/campaigns-overview.png)

Do widoków kampanii możesz również uzyskać dostęp w:

- **Współpraca za & e-mail** \> **Eksplorator** \> **Widok** \> **Kampanie**
- **Współpraca za & e-mail** \> **Eksplorator** \> **Widok** \> **Wszystkie wiadomości e-mail** \> **Karta Kampanii**
- **Współpraca za & e-mail** \> **Eksplorator** \> **Widok** \> **Phish** \> **Karta Kampanii**
- **Współpraca za & e-mail** \> **Eksplorator** \> **Widok** \> **Złośliwe oprogramowanie** \> **Karta Kampanii**

Aby uzyskać dostęp do widoków kampanii, musisz być członkiem grup ról Zarządzanie **organizacją,** **Administrator** zabezpieczeń lub  Czytnik zabezpieczeń w portalu Microsoft 365 Defender zabezpieczeń. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).

## <a name="campaigns-overview"></a>Omówienie kampanii

Strona przeglądu zawiera informacje na temat wszystkich kampanii.

Na domyślnej **karcie Kampania** obszar **Typ** kampanii zawiera wykres słupkowy przedstawiający liczbę adresatów dziennie. Domyślnie na wykresie są zarówno dane **typu Phish** , jak i **Malware** .

> [!TIP]
> Jeśli nie widzisz żadnych danych dotyczących kampanii, spróbuj zmienić zakres dat lub [filtry](#filters-and-settings).

Tabela poniżej wykresu na stronie przeglądu zawiera następujące informacje na karcie **Kampania** :

- **Nazwa**

- **Przykładowy temat**: wiersz tematu jednej z wiadomości w kampanii. Pamiętaj, że wszystkie wiadomości w kampanii niekoniecznie będą mieć ten sam temat.

- **Kierowane**: Wartość procentowa obliczona przez: (liczba adresatów kampanii w organizacji) / (łączna liczba adresatów w kampanii we wszystkich organizacjach w ramach usługi). Ta wartość wskazuje stopień, w jakim kampania jest kierowana tylko do Twojej organizacji (wyższa wartość) i do innych organizacji w usłudze (niższa wartość).

- **Typ**: Ta wartość to **Phish** lub **Malware**.

- **Podtyp**: ta wartość zawiera więcej szczegółów dotyczących kampanii. Przykład:
  - **Phish**: Jeśli jest dostępny, markę, która jest wyłuddawana w tej kampanii. Na przykład `Microsoft`, `365`, `Unknown``Outlook`, lub `DocuSign`.
  - **Złośliwe** oprogramowanie: Na przykład lub `HTML/PHISH` `HTML/<MalwareFamilyName>`.

  Tam, gdzie jest to możliwe, markę, która jest wyłuddawana w ramach tej kampanii. Gdy wykrywanie jest sterowane przez program Defender Office 365 technologii, do wartości podtypu jest dodawany prefiks **ATP**-.

- **Adresaci**: liczba użytkowników, do których kierowano w ramach tej kampanii.

- **Skrzynka odbiorcza**: liczba użytkowników, którzy otrzymywali wiadomości z tej kampanii w swoich skrzynkach odbiorczych (nie jest dostarczana do folderu wiadomości-śmieci).

- **Kliknął**: liczba użytkowników, którzy kliknął adres URL lub otworzyli załącznik w wiadomości służącej do wyłudzania informacji.

- **Szybkość klikania**: Wartość procentowa obliczona przez wartość "**KlikedInboxed** / ". Wartość ta jest wskaźnikiem skuteczności kampanii. Innymi słowy, jeśli adresaci mogli zidentyfikować wiadomość jako wyłudzającą informacje, a także jeśli nie kliknął adresu URL ładowania.

  Należy pamiętać **, że w kampaniach** złośliwego oprogramowania nie jest używana szybkość klikania.

- **Odwiedzone**: ilu użytkowników rzeczywiście przesu chodziło o witrynę sieci Web z opłatami. Jeśli istnieją wartości **Klikone**, ale Sejf dostęp do witryny sieci Web został zablokowany, ta wartość będzie równa zero.

Karta **Pochodzenie kampanii** pokazuje źródła wiadomości na mapie świata.

### <a name="filters-and-settings"></a>Filtry i ustawienia

W górnej części strony **Kampanii znajduje** się kilka ustawień filtrów i zapytań, które ułatwiają znajdowanie i odizolowanie określonych kampanii.

![Filtry kampanii.](../../media/campaign-filters-and-settings.png)

Najbardziej podstawowym filtrowaniem, które można wykonać, jest data/godzina rozpoczęcia i data/godzina zakończenia.

Aby dodatkowo filtrować widok, możesz wykonać jedną właściwość z wieloma filtrami wartości, klikając przycisk Typ  kampanii, zaznaczając odpowiednie opcje, a następnie klikając pozycję **Odśwież**.

Właściwości kampanii z filtrowaniem dostępne w przycisku **Typ** kampanii opisano na poniższej liście:

- **Podstawowe**:
  - **Typ kampanii**: Wybierz pozycję **Złośliwe oprogramowanie** lub **Wyłudzy**. Wyczyszczenie zaznaczeń ma taki sam wynik, jak zaznaczenie obu.
  - **Nazwa kampanii**
  - **Podtyp kampanii**
  - **Nadawca**
  - **Adresaci**
  - **Domena nadawcy**
  - **Temat**
  - **Nazwa pliku załącznika**
  - **Rodzina złośliwego oprogramowania**
  - **Tagi**: użytkownicy lub grupy, do których zastosowano określony tag użytkownika (w tym konta priorytetowe). Aby uzyskać więcej informacji o tagach użytkowników, zobacz [Tagi użytkowników](user-tags.md).
  - **Akcja dostarczenia**
  - **Dodatkowa akcja**
  - **Kierunkowość**
  - **Technologia wykrywania**
  - **Oryginalna lokalizacja dostarczania**
  - **Najnowsza lokalizacja dostarczania**
  - **Zastępowanie systemu**

- **Zaawansowane**:
  - **Identyfikator wiadomości internetowej**: dostępny w polu **nagłówka identyfikatora** wiadomości w nagłówku wiadomości. Przykładowa wartość to `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (zwróć uwagę na nawiasy kątowe).
  - **Identyfikator wiadomości sieciowej**: wartość GUID, która jest dostępna w polu **nagłówka X-MS-Exchange-Organization-Network-Message-Id** w nagłówku wiadomości.
  - **Adres IP nadawcy**
  - **Załącznik SHA256**: Aby znaleźć wartość skrótu SHA256 pliku w programie Windows, uruchom następujące polecenie w wierszu polecenia: `certutil.exe -hashfile "<Path>\<Filename>" SHA256`.
  - **Identyfikator klastrów**
  - **Identyfikator alertu**
  - **Identyfikator zasad alertu**
  - **Identyfikator kampanii**
  - **Sygnał adresu URL zap**

- **Adresy URL**:
  - **Domena adresu URL**
  - **Ścieżka i domena adresu URL**
  - **ADRES URL**
  - **Ścieżka adresu URL**
  - **Kliknij werdykt**

Aby utworzyć bardziej zaawansowane filtrowanie, w tym filtrowanie według wielu właściwości, możesz kliknąć przycisk **Filtr** zaawansowany, aby utworzyć zapytanie. Dostępne są te same właściwości kampanii, ale z następującymi ulepszeniami:

- Możesz kliknąć pozycję **Dodaj warunek,** aby wybrać wiele warunków.
- Możesz wybrać operator **And** (Oraz **) lub Or (** Lub) między warunkami.
- Możesz wybrać element **grupy Warunek** u dołu listy warunków, aby utworzyć złożone warunki złożone.

Po zakończeniu kliknij **przycisk Zapytanie.**

Po utworzeniu filtru podstawowego lub zaawansowanego można go zapisać przy **użyciu opcji Zapisz** zapytanie lub **Zapisz zapytanie jako**. Później, po powrocie do strony **Kampanie** , możesz załadować zapisany filtr, klikając pozycję **Zapisane ustawienia zapytania**.

Aby wyeksportować wykres lub listę kampanii, kliknij pozycję Eksportuj i wybierz pozycję **Eksportuj dane wykresu** lub **Eksportuj listę kampanii**.

Jeśli masz subskrypcję programu Microsoft Defender for Endpoint, możesz kliknąć pozycję **MDE Ustawienia**, aby połączyć lub odłączyć informacje dotyczące kampanii za pomocą usługi Microsoft Defender for Endpoint. Aby uzyskać więcej informacji, zobacz [Integracja programu Microsoft Defender w celu Office 365 z programem Microsoft Defender for Endpoint](integrate-office-365-ti-with-mde.md).

## <a name="campaign-details"></a>Szczegóły kampanii

Po kliknięciu nazwy kampanii jej szczegóły są wyświetlane w wysuwanych informacjach.

### <a name="campaign-information"></a>Informacje dotyczące kampanii

U góry widoku szczegółów kampanii dostępne są następujące informacje o kampanii:

- **Identyfikator kampanii**: unikatowy identyfikator kampanii.
- **Działanie**: Czas trwania i działanie kampanii.
- Następujące dane wybranego filtru zakresu dat (lub wybranego na osi czasu):
- **Wpływ**
- **Wiadomości**: Całkowita liczba adresatów.
- **Skrzynka odbiorcza**: liczba wiadomości dostarczonych do skrzynki odbiorczej, a nie do folderu Wiadomości-śmieci.
- **Kliknął link**: Ilu użytkowników kliknął ład w adresie URL w wiadomości służącej do wyłudzania informacji.
- **Odwiedzony link**: ilu użytkowników odwiedziło adres URL.
- **Targeted(%)**: Wartość procentowa obliczona przez: (liczba adresatów kampanii w organizacji) / (łączna liczba adresatów w kampanii we wszystkich organizacjach w ramach usługi). Należy zauważyć, że ta wartość jest obliczana przez cały okres trwania kampanii i nie zmienia się na podstawie filtrów dat.
- Data/godzina rozpoczęcia oraz filtry danych/godzin zakończenia dla przepływu kampanii zgodnie z opisem w następnej sekcji.
- Interakcyjna oś czasu działań kampanii: Oś czasu pokazuje aktywność w całym okresie trwania kampanii. Możesz zatrzymać wskaźnik myszy na punktach danych na wykresie, aby wyświetlić liczbę wykrytych wiadomości.

![Informacje dotyczące kampanii.](../../media/campaign-details-campaign-info.png)

### <a name="campaign-flow"></a>Przepływ kampanii

W środku widoku szczegółów kampanii ważne szczegóły dotyczące kampanii przedstawiono na poziomym diagramie przepływu (nazywanym diagramem _Sankey_ ). Te szczegóły pomogą zrozumieć elementy kampanii i jej potencjalny wpływ na organizację.

> [!TIP]
> Informacja wyświetlana na diagramie przepływu jest kontrolowana przez filtr zakresu dat na osi czasu zgodnie z opisem w poprzedniej sekcji.

![Szczegóły kampanii, które nie zawierają kliknięć adresu URL użytkownika.](../../media/campaign-details-no-recipient-actions.png)

Gdy najedziesz kursorem na poziomy pasek na diagramie, zobaczysz liczbę powiązanych wiadomości (na przykład wiadomości z określonego źródłowego adresu IP, wiadomości ze źródłowego adresu IP, używając określonej domeny nadawcy itp.).

Diagram zawiera następujące informacje:

- **Sender IPs**
- **Domeny nadawcy**
- **Werdykty filtrów**: wartości werdyktów są związane z dostępnymi werdyktami filtrowania spamu i wyłudzania informacji, zgodnie z opisem w nagłówkach wiadomości ochrony przed [spamem](anti-spam-message-headers.md). Dostępne wartości opisano w poniższej tabeli:

  <br>

  ****

  |Value|Werdykt filtru spamu|Opis|
  |---|---|---|
  |**Dozwolone**|`SFV:SKN` <p> `SFV:SKI`|Wiadomość została oznaczona jako niebędąca spamem i(lub pominięta) filtrowaniem przed rozpoczęciem oceny przez filtrowanie spamu. Na przykład wiadomość została oznaczona przez regułę przepływu poczty jako niebędąc spamem (znana również jako reguła transportu). <p> W wiadomości pominięto filtrowanie spamu z innych przyczyn. Na przykład nadawca i adresat mogą być w tej samej organizacji.|
  |**Zablokowane**|`SFV:SKS`|Wiadomość została oznaczona jako spam przed rozpoczęciem oceny przez filtrowanie spamu. Na przykład za pomocą reguły przepływu poczty e-mail.|
  |**Wykryty**|`SFV:SPM`|Wiadomość została oznaczona jako spam przez filtrowanie spamu.|
  |**Nie wykryto**|`SFV:NSPM`|Wiadomość została oznaczona jako niebędąca spamem przez filtrowanie spamu.|
  |**Wydano**|`SFV:SKQ`|Wiadomość pominięta w filtrowaniu spamu, ponieważ została zwolniona z kwarantanny.|
  |**Zezwalaj na dzierżawę**<sup>\*</sup>|`SFV:SKA`|Wiadomość pominięto filtrowanie spamu z powodu ustawień w zasadach ochrony przed spamem. Na przykład nadawca został na liście dozwolonych nadawców lub na liście domen dozwolonych.|
  |**Blok dzierżawy**<sup>\*\*</sup>|`SFV:SKA`|Wiadomość została zablokowana przez filtrowanie spamu ze względu na ustawienia w zasadach ochrony przed spamem. Na przykład nadawca został na liście dozwolonych nadawców lub na liście domen dozwolonych.|
  |**Zezwalaj użytkownikom**<sup>\*</sup>|`SFV:SFE`|Wiadomość pominięta w filtrowaniu spamu, ponieważ nadawca był na liście Sejf nadawców.|
  |**Blokowanie użytkowników**<sup>\*\*</sup>|`SFV:BLK`|Wiadomość została zablokowana przez filtrowanie spamu, ponieważ nadawca był na liście zablokowanych nadawców użytkownika.|
  |**ZAP**|n/a|[Automatyczne czyszczenie zerowe (ZAP)](zero-hour-auto-purge.md) przeniesiono dostarczoną wiadomość do folderu wiadomości-śmieci lub kwarantanny. Działanie konfiguruje się w zasadach [ochrony przed spamem](configure-your-spam-filter-policies.md).|
  |

  <sup>\*</sup> Przejrzyj zasady ochrony przed spamem, ponieważ dozwolona wiadomość prawdopodobnie zostałaby zablokowana przez usługę.

  <sup>\*\*</sup> Przejrzyj zasady ochrony przed spamem, ponieważ te wiadomości powinny być poddawane kwarantannie, a nie dostarczane.

- Miejsca **docelowe** wiadomości: Prawdopodobnie chcesz zbadać wiadomości, które zostały dostarczone do adresatów (do skrzynki odbiorczej lub folderu Wiadomości-śmieci), nawet jeśli użytkownicy nie klikną adresu URL ładowania w wiadomości. Możesz również usunąć poddaną kwarantannie wiadomości z kwarantanny. Aby uzyskać więcej informacji, zobacz [Poddaj wiadomościom w kwarantannie usługi EOP](quarantine-email-messages.md).
  - **Usunięto folder**
  - **Wrzucono**
  - **Zewnętrzne**: Adresat znajduje się w lokalnej organizacji poczty e-mail w środowiskach hybrydowych.
  - **Zakończone niepowodzeniem**
  - **Przekazane**
  - **Skrzynka odbiorcza**
  - **Folder wiadomości-śmieci**
  - **Kwarantanna**
  - **Unknown**

- **Kliknięcia adresu URL**: Te wartości są opisane w następnej sekcji.

> [!NOTE]
> Na wszystkich warstwach zawierających więcej niż 10 elementów jest wyświetlanych 10 najwyższych elementów, a pozostałe są powiązane ze sobą w obszarze **Inne**.

#### <a name="url-clicks"></a>Kliknięcia adresu URL

Gdy wiadomość wyłudzająca informacje zostanie dostarczona do folderu Skrzynka odbiorcza lub Wiadomości-śmieci adresata, istnieje możliwość, że użytkownik kliknie adres URL ładowania. Nie klikanie adresu URL jest małą miarą sukcesu, ale musisz ustalić, dlaczego wiadomość wyłudzająca informacje została nawet dostarczona do skrzynki pocztowej.

Jeśli użytkownik kliknął adres URL ładowania w wiadomości służącej do wyłudzania informacji, akcje są wyświetlane w obszarze kliknięć adresu **URL** diagramu w widoku szczegółów kampanii.

- **Dozwolone**
- **BlockPage**: Adresat kliknął adres URL ładowania, ale jego dostęp do złośliwej witryny sieci Web został zablokowany przez zasady usługi [Sejf Linki](safe-links.md) w Twojej organizacji.
- **BlockPageOverride**: Adresat kliknął adres URL ładowania w wiadomości, ale Sejf Linki próbowały je zatrzymać, ale mógł zastąpić blok. Sprawdź zasady [Sejf sieci Web](set-up-safe-links-policies.md), aby zobaczyć, dlaczego użytkownicy mogą zastępować werdykt linków Sejf i kontynuować pracę ze złośliwą witryną sieci Web.
- **PendingDetonationPage**: Sejf Załączniki w programie Microsoft Defender Office 365 są w trakcie otwierania i badanie adresu URL ładowania w środowisku komputera wirtualnego.
- **PendingDetonationPageOverride**: Adresat mógł zastąpić proces detonacji ładowania i otworzyć adres URL bez oczekiwania na wyniki.

### <a name="tabs"></a>Karty

Karty w widoku szczegółów kampanii umożliwiają dalsze badanie kampanii.

> [!TIP]
> Informacja wyświetlana na kartach jest kontrolowana przez filtr zakresu dat na osi czasu zgodnie z opisem w [sekcji Informacje o kampanii](#campaign-information) .

- **Klikanie adresu URL**: Jeśli użytkownicy nie klikną adresu URL ładowania w wiadomości, ta sekcja będzie pusta. Jeśli użytkownik mógł kliknąć adres URL, zostaną wypełnione następujące wartości:
  - **Użytkownik**<sup>\*</sup>
  - **ADRES URL**<sup>\*</sup>
  - **Godzina kliknięcia**
  - **Kliknij werdykt**

- **Sender IPs**
  - **Adres IP nadawcy**<sup>\*</sup>
  - **Łączna liczba**
  - **Skrzynka odbiorcza**
  - **Bez skrzynki odbiorczej**
  - **Spf passed**: The sender was authenticated by the [Sender Policy Framework (SPF)](how-office-365-uses-spf-to-prevent-spoofing.md). Nadawca, który nie przejdzie weryfikacji SPF, wskazuje nieuwierzytanego nadawcę lub wiadomość podszywa się pod wiarygodnego nadawcę.

- **Nadawcy**
  - **Nadawca**: Jest to rzeczywisty adres nadawcy w poleceniu SMTP MAIL FROM, który nie musi być adresem e-mail Od: widzianych przez użytkowników w klientach poczty e-mail.
  - **Łączna liczba**
  - **Skrzynka odbiorcza**
  - **Bez skrzynki odbiorczej**
  - **Pomyślnie przekazano DKIM**: Nadawca został uwierzytelniony za pomocą [dKIM (Domain Keys Identified Mail) (DKIM](support-for-validation-of-dkim-signed-messages.md)). Nadawca, który nie przejdzie weryfikacji DKIM, wskazuje nieuwierzytanego nadawcę lub wiadomość podszywa się pod wiarygodnego nadawcę.
  - **Przekazano DMARC**: Nadawca został uwierzytelniony za pomocą [DMARC (Domain-based Message Authentication, Reporting, and Conformance).](use-dmarc-to-validate-email.md) Nadawca, który nie przejdzie weryfikacji DMARC, wskazuje nieuwierzytanego nadawcę lub wiadomość podszywa się pod prawdziwego nadawcę.

- **Załączniki**
  - **Nazwa pliku**
  - **SHA256**
  - **Rodzina złośliwego oprogramowania**
  - **Łączna liczba**

- **ADRES URL**
  - **ADRES URL**<sup>\*</sup>
  - **Łączna liczba**

<sup>\*</sup> Kliknięcie tej wartości spowoduje otwarcie nowego menu wysuwu zawierającego więcej szczegółowych informacji na temat określonego elementu (użytkownik, adres URL itp.) u góry widoku szczegółów kampanii. Aby wrócić do widoku szczegółów kampanii, w nowym  wysuwanych menu kliknij pozycję Gotowe.

### <a name="buttons"></a>Przyciski

Przyciski w dolnej części widoku szczegółów kampanii umożliwiają badanie i rejestrowanie szczegółów kampanii:

- **Eksplorowanie** wiadomości: Korzystaj z eksploratora zagrożeń, aby dokładniej zbadać kampanię:
  - **Wszystkie wiadomości**: Otwiera nową kartę wyszukiwania Eksploratora zagrożeń, używając wartości **Identyfikator** kampanii jako filtru wyszukiwania.
  - **Wiadomości w skrzynce odbiorczej**: Otwiera nową kartę wyszukiwania Eksploratora zagrożeń przy użyciu filtru Identyfikator kampanii i Lokalizacja dostarczania **:** Skrzynka odbiorcza.
  - **Wiadomości wewnętrzne**. Otwiera nową kartę wyszukiwania Eksploratora zagrożeń, używając jako filtru wyszukiwania Identyfikatora kampanii i **kierunkowości:** Wewnątrz organizacji.

- **Pobierz raport zagrożeń**: pobierz szczegóły kampanii do dokumentu programu Word (domyślnie o nazwie CampaignReport.docx). Pamiętaj, że plik do pobrania zawiera szczegółowe informacje przez cały okres trwania kampanii (nie tylko wybrane daty filtrowania).
