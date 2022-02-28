---
title: Informacje o funkcjach dotyczące wyszukiwania zawartości
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Ten artykuł zawiera informacje referencyjne dotyczące narzędzia zbierania elektronicznych materiałów dowodowych przeszukiwania zawartości w p Centrum zgodności platformy Microsoft 365, które ułatwiają poznanie wielu szczegółowych informacji na temat wyszukiwania zawartości.
ms.openlocfilehash: 0688f3119b500f8e11675aa101d92942a3063e8b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984612"
---
# <a name="feature-reference-for-content-search"></a>Informacje o funkcjach dotyczące wyszukiwania zawartości

W tym artykule opisano funkcje wyszukiwania zawartości.

## <a name="content-search-limits"></a>Limity wyszukiwania zawartości

Aby uzyskać opis limitów, które są stosowane do przeszukiwania zawartości, zobacz [Limity wyszukiwania zawartości](limits-for-content-search.md).

## <a name="building-a-search-query"></a>Tworzenie zapytania wyszukiwania

Aby uzyskać szczegółowe informacje na temat tworzenia zapytania wyszukiwania, używania logicznych operatorów wyszukiwania i warunków wyszukiwania oraz wyszukiwania typów informacji poufnych i zawartości udostępnianej użytkownikom spoza organizacji, zobacz Zapytania słów kluczowych i warunki wyszukiwania dotyczące wyszukiwania [zawartości.](keyword-queries-and-search-conditions.md)

Używając listy słów kluczowych do utworzenia zapytania wyszukiwania, pamiętaj o następujących kwestiach.

- Należy zaznaczyć pole wyboru  Pokaż listę słów kluczowych, a następnie wpisać każde słowo kluczowe w osobnym wierszu w celu utworzenia zapytania wyszukiwania, w którym słowa kluczowe (lub frazy słów kluczowych) w każdym wierszu są połączone **operatorem LUB**. Jeśli wkleisz listę słów kluczowych w polu słowa kluczowego lub naciśniesz klawisz **Enter** po wpisaniu słowa kluczowego, nie zostaną one połączone przez operator **OR** . Poniżej przedstawiono niepoprawne i poprawne przykłady dodawania listy słów kluczowych.

    **Niepoprawne**

    ![Niepoprawny sposób formatowania listy słów kluczowych (przez wklejenie listy w polu słowa kluczowego).](../media/fb54e3df-232a-439a-b3d7-27a60ec76a4c.png)

    **Popraw**

    ![Prawidłowy sposób formatowania listy słów kluczowych (przez zaznaczenie pola wyboru, a następnie wklejenie listy).](../media/5d511a7b-c1f9-499c-bffe-e075bfc9adec.png)

- Możesz również przygotować listę słów kluczowych lub fraz słów kluczowych w pliku Excel lub pliku w formacie zwykłego tekstu, a następnie skopiować i wkleić listę słów kluczowych. W tym celu należy zaznaczyć pole **wyboru Pokaż listę słów** kluczowych. Następnie kliknij pierwszy wiersz na liście słów kluczowych i wklej listę. Każdy wiersz z pliku Excel lub tekstowego jest wklejony do oddzielnego wiersza na liście słów kluczowych.

- Po utworzeniu zapytania za pomocą listy słów kluczowych warto sprawdzić, czy składnia zapytania wyszukiwania jest zamierzeniu. W zapytaniu wyszukiwania wyświetlanym w obszarze Zapytanie  w okienku szczegółów słowa kluczowe są oddzielone tekstem **(c:s).** Oznacza to, że słowa kluczowe są połączone operatorem logicznym podobnym do funkcji operatora **LUB** . Podobnie, jeśli zapytanie wyszukiwania zawiera warunki, słowa kluczowe i warunki są rozdzielane tekstem **(c:c)**. Oznacza to, że słowa kluczowe są połączone z warunkami za pomocą operatora logicznego podobnego do funkcji operatora **AND** . Oto przykład zapytania wyszukiwania (wyświetlanego w okienku Szczegóły), które zwraca wyniki w przypadku użycia listy słów kluczowych i warunku.

    ![Przykład zapytania utworzonego przy użyciu listy słów kluczowych i warunku.](../media/b463750c-57fa-4602-9fed-0d5a420db3ad.png)

- Po uruchomieniu wyszukiwania zawartości program Microsoft 365 automatycznie wyszukuje nieobsługiwane znaki i operatory logiczne, które mogą nie być zapisywane za pomocą automatycznych liter. Nieobsługiwane znaki są często ukryte i zwykle powodują błąd wyszukiwania lub zwracają niezamierzone wyniki. Aby uzyskać więcej informacji o sprawdzanych nieobsługiwanych znakach, zobacz Sprawdzanie błędów [w zapytaniu wyszukiwania zawartości](check-your-content-search-query-for-errors.md).

- Jeśli masz zapytanie wyszukiwania zawierające słowa kluczowe zawierające znaki w języku innym niż angielski (na przykład znaki chińskie), możesz kliknąć pozycję Query **language-country/regionQuery**![ language-country/region w obszarze Przeszukiwanie zawartości.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) i wybierz wartość kodu kultury kraju w języku dla wyszukiwania. Domyślny język/region jest neutralny. Jak możesz stwierdzić, czy chcesz zmienić ustawienie języka wyszukiwania zawartości? Jeśli masz określone lokalizacje zawartości zawierające wyszukiwane znaki w języku nieanglojęzycznym, ale wyszukiwanie nie zwraca żadnych wyników, przyczyną może być ustawienie języka.

## <a name="partially-indexed-items"></a>Elementy częściowo indeksowane

- Częściowo indeksowane elementy skrzynek pocztowych są uwzględniane w szacowanych wynikach wyszukiwania. Częściowo indeksowane elementy SharePoint i OneDrive nie są uwzględniane w szacowanych wynikach wyszukiwania. Aby uzyskać więcej informacji, zobacz [Częściowo indeksowane elementy podczas zbierania elektronicznych materiałów dowodowych](partially-indexed-items-in-content-search.md).

## <a name="searching-onedrive-accounts"></a>Wyszukiwanie OneDrive kontach

- Aby uzyskać listę adresów URL witryn OneDrive w organizacji, zobacz Tworzenie listy wszystkich OneDrive [lokalizacji w organizacji](/onedrive/list-onedrive-urls). Ten skrypt w tym artykule tworzy plik tekstowy zawierający listę wszystkich OneDrive internetowych. Aby uruchomić ten skrypt, musisz zainstalować powłokę zarządzania SharePoint online i używać jej. Pamiętaj, aby dołączyć adres URL domeny Moja witryna organizacji do każdej witryny OneDrive, którą chcesz przeszukać. Jest to domena zawierająca wszystkie twoje OneDrive, na przykład `https://contoso-my.sharepoint.com`. Oto przykładowy adres URL witryny sieci OneDrive użytkownika: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

    W rzadkich przypadkach zmiany głównej nazwy użytkownika (UPN) osoby adres URL jego lokalizacji OneDrive w celu uwzględnienia nowej głównej nazwy użytkownika. W takim przypadku musisz zmodyfikować wyszukiwanie zawartości, dodając nowy adres URL OneDrive URL i usuwając stary adres URL. Aby uzyskać więcej informacji, zobacz [Jak zmiany głównej sieci użytkowników wpływają na OneDrive URL](/onedrive/upn-changes).

## <a name="searching-microsoft-teams-and-microsoft-365-groups"></a>Wyszukiwanie Microsoft Teams grup Microsoft 365 grup

Możesz przeszukać skrzynkę pocztową skojarzoną z zespołem Microsoft Team Microsoft 365 grupy. Ponieważ Microsoft Teams jest wbudowana w Microsoft 365 grupy, jej przeszukiwanie jest podobne. W obu przypadkach przeszukiwana jest tylko skrzynka pocztowa grupy lub zespołu. Skrzynki pocztowe członków grupy lub zespołu nie są przeszukiwane. Aby je wyszukać, musisz je dodać do wyszukiwania.

Wyszukując zawartość w grupach zawartości w grupach, Microsoft Teams i Microsoft 365 należy pamiętać o następujących kwestiach.

- Aby wyszukać zawartość w grupach Teams i Microsoft 365, musisz określić skrzynkę pocztową i witrynę SharePoint skojarzonej z zespołem lub grupą.

- Zawartość z kanałów prywatnych jest przechowywana w skrzynce pocztowej każdego użytkownika, a nie w skrzynce pocztowej zespołu. Aby wyszukać zawartość w kanałach prywatnych, zobacz [Zbierania elektronicznych materiałów dowodowych w kanałach prywatnych](/microsoftteams/ediscovery-investigation#ediscovery-of-private-channels).

- Uruchom polecenie **cmdlet Get-UnifiedGroup** w programie Exchange Online, aby wyświetlić właściwości zespołu lub grupy Microsoft 365 grupy. Jest to dobry sposób na uzyskania adresu URL witryny skojarzonej z zespołem lub grupą. Na przykład następujące polecenie wyświetla wybrane właściwości grupy kierownictwa Microsoft 365 o nazwie Starszy zespół kierownictwa:

  ```text
  Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
  DisplayName            : Senior Leadership Team
  Alias                  : seniorleadershipteam
  PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
  SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
  ```

    > [!NOTE]
    > Aby uruchomić polecenie **cmdlet Get-UnifiedGroup**, musisz mieć przypisaną rolę adresatów View-Only w programie Exchange Online lub być członkiem grupy ról z przypisaną rolą adresatów View-Only.

- Podczas przeszukiwania skrzynki pocztowej użytkownika nie będą przeszukiwane żadne grupy zespołu Microsoft 365, do których należy użytkownik. Podobnie podczas przeszukiwania zespołu lub grupy Microsoft 365 przeszukiwana jest tylko skrzynka pocztowa grupy i witryna grupy określone przez Ciebie. Skrzynki pocztowe i OneDrive dla Firm członków grupy nie są przeszukiwane, chyba że jawnie dodasz ich do wyszukiwania.

- Aby uzyskać listę członków zespołu lub grupy Microsoft 365,  \> możesz wyświetlić właściwości na stronie Grupy macierzyste w centrum administracyjne platformy Microsoft 365.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a> Możesz również uruchomić następujące polecenie w programie Exchange Online PowerShell:

  ```powershell
  Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
  ```

    > [!NOTE]
    > Aby uruchomić polecenie **cmdlet Get-UnifiedGroupLinks**, musisz mieć przypisaną rolę adresatów View-Only w programie Exchange Online lub być członkiem grupy ról z przypisaną rolą adresatów View-Only.

- Konwersacje w ramach kanału Teams są przechowywane w skrzynce pocztowej skojarzonej z zespołem. Podobnie pliki, które członkowie zespołu mają udział w kanale, są przechowywane w SharePoint zespołu. Dlatego w celu przeszukiwania konwersacji i plików w kanale należy dodać skrzynkę pocztową zespołu SharePoint witrynę jako lokalizację zawartości.

- Konwersacje, które są częścią listy czatów w programie Teams, są również przechowywane w skrzynce Exchange Online użytkowników, którzy uczestniczą w czacie. Pliki, które użytkownik udostępnia w konwersacjach za pomocą czatu, są przechowywane OneDrive dla Firm konta użytkownika, który udostępnia plik. Dlatego musisz dodać poszczególne skrzynki pocztowe użytkowników i konta OneDrive dla Firm jako lokalizacje zawartości do wyszukiwania konwersacji i plików na liście czatów.

    > [!NOTE]
    > W Exchange hybrydowego użytkownicy z lokalną skrzynką pocztową mogą uczestniczyć w konwersacjach  ramach listy czatów w programie Teams. W tym przypadku zawartość tych konwersacji można również przeszukiwać, ponieważ jest zapisywana w opartym na chmurze obszarze magazynu (nazywanym skrzynką pocztową w chmurze dla użytkowników *lokalnych) dla* użytkowników, którzy mają lokalną skrzynkę pocztową. Aby uzyskać więcej informacji, [zobacz Wyszukiwanie Teams danych czatu dla użytkowników lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

- Każdy zespół lub kanał zespołu zawiera stronę typu wiki do sporządzania notacji i współpracy. Zawartość typu wiki jest automatycznie zapisywana w pliku w formacie mht. Ten plik jest przechowywany w bibliotece Teams danych typu wiki w witrynie zespołu SharePoint wiki. Za pomocą narzędzia Przeszukiwanie zawartości możesz przeszukiwać witrynę typu wiki, określając witrynę zespołu, SharePoint jako lokalizację zawartości do przeszukania.

    > [!NOTE]
    > 22 czerwca 2017 r. opublikowano funkcję wyszukiwania na wiki zespołu lub kanału (podczas wyszukiwania SharePoint zespołu). Strony typu wiki, które zostały zapisane lub zaktualizowane w tym dniu lub później, są dostępne do przeszukania. Strony typu wiki zapisane lub zaktualizowane przed datą nie są dostępne do wyszukiwania.

- Podsumowanie informacji dotyczących spotkań i połączeń w kanale Teams są również przechowywane w skrzynkach pocztowych użytkowników, którzy nacięli się do spotkania lub połączenia telefonicznego. Oznacza to, że za pomocą wyszukiwania zawartości można przeszukiwać te rekordy podsumowania. Podsumowanie zawiera:

  - Data, godzina rozpoczęcia, godzina zakończenia i czas trwania spotkania lub połączenia

  - Data i godzina dołączenia do spotkania lub połączenia przez poszczególnych uczestników

  - Połączenia wysłane do poczty głosowej

  - Nieodebrane lub nieodebrane połączenia

  - Transfery połączeń, które są reprezentowane przez dwie osobne rozmowy

  Wyszukiwanie rekordów spotkań i podsumowań połączeń może potrwać do 8 godzin.

  W wynikach wyszukiwania podsumowania spotkań są identyfikowane jako "Spotkanie" w polu **Typ, a** podsumowania połączeń są identyfikowane jako **Połączenie**. Ponadto konwersacje, które są częścią kanału Teams i czaty 1xN, są identyfikowane jako wiadomości  błyskawiczne w **polu Typ**.

  ![Teams, połączenia i czaty 1xN są oznaczone w polu Typ.](../media/O365-ContentSearch-Teams-MessageKind.png)

   Aby uzyskać więcej informacji, [zobacz Microsoft Teams dotyczące uruchamiania zbierania elektronicznych materiałów dowodowych dla połączeń i spotkań](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-launches-ediscovery-for-calling-and-meetings/ba-p/210947).

- Treści na kartach wygenerowane przez aplikacje Teams kanałach komunikacji głosowej, czatach jeden na jeden i czatach 1xN są przechowywane w skrzynkach pocztowych i można je przeszukiwać. Karta *to* kontener interfejsu użytkownika na krótkie fragmenty zawartości. Karty mogą mieć wiele właściwości i załączników oraz zawierać przyciski służące do wyzwalania akcji kart. Aby uzyskać więcej informacji, zobacz [Karty.](/microsoftteams/platform/task-modules-and-cards/what-are-cards)

  Podobnie jak Teams, gdzie zawartość kart jest przechowywana na podstawie miejsca jej użytego. Zawartość kart używanych w kanale Teams jest przechowywana w skrzynce Teams pocztowej grupy. Zawartość kart do czatów 1:1 i 1xN jest przechowywana w skrzynkach pocztowych uczestników czatu.

  Aby wyszukać zawartość karty, możesz użyć tych warunków `kind:microsoftteams` lub `itemclass:IPM.SkypeTeams.Message` warunków wyszukiwania. Podczas przeglądania wyników wyszukiwania zawartość kart generowana przez boty w kanale Teams ma właściwość poczty e-mail Nadawca **/**`<appname>@teams.microsoft.com`Autor jako , `appname` gdzie znajduje się nazwa aplikacji, która wygenerowała zawartość karty. Jeśli zawartość karty została wygenerowana przez użytkownika, wartość nadawcy **/** autora identyfikuje użytkownika.

  Podczas wyświetlania zawartości karty w wynikach przeszukiwania zawartości jest wyświetlana jako załącznik do wiadomości. Nazwa załącznika to `appname.html`, gdzie `appname` jest nazwa aplikacji, która wygenerowała zawartość karty. Na poniższych zrzutach ekranu pokazano, jak zawartość kart (w przypadku aplikacji o nazwie Asana) pojawia się Teams w wynikach wyszukiwania.

  **Zawartość karty w Teams**

  ![Zawartość karty w Teams kanału.](../media/CardContentTeams.png)

  **Zawartość karty w wynikach wyszukiwania**

  ![Ta sama zawartość kart w wynikach wyszukiwania zawartości.](../media/CardContentEdiscoverySearchResults.png)

  > [!NOTE]
  > Aby w tej chwili wyświetlać obrazy z zawartości kart w wynikach wyszukiwania (takich jak znacznik wyboru na poprzednim zrzucie ekranu), musisz zalogować się do przeglądarki Teams (https://teams.microsoft.com)na innej karcie w tej samej sesji przeglądarki, która jest następnie wyświetlana w celu wyświetlenia wyników wyszukiwania). W przeciwnym razie są wyświetlane symbole zastępcze obrazów.

- Za pomocą właściwości **E-mail** typu **lub warunku wyszukiwania** Typu wiadomości możesz wyszukiwać zawartość w programie Teams.

  - Aby użyć **właściwości Rodzaj** jako części zapytania wyszukiwania słów kluczowych, w polu Słowa **kluczowe** zapytania wyszukiwania wpisz `kind:microsoftteams`.

    ![Użyj funkcji kind:microsoftteams w polu Słowa kluczowe.](../media/O365-ContentSearch-Teams-Keywords.png)

  - Aby użyć warunku wyszukiwania, dodaj **warunek typu wiadomości** i użyj wartości `microsoftteams`.

    ![Użyj warunku typu wiadomości z wartością microsoftteams.](../media/O365-ContentSearch-Teams-MessageKindCondition.png)

   Warunki są logicznie połączone z zapytaniem słowa kluczowego przez **operator AND** . Oznacza to, że element musi odpowiadać zarówno zapytaniu słów kluczowych, jak i warunekowi wyszukiwania, który ma zostać zwrócony w wynikach wyszukiwania. Aby uzyskać więcej informacji, zobacz sekcję "Wskazówki dotyczące używania warunków" w sekcji Zapytania słów kluczowych [i warunki wyszukiwania wyszukiwania zawartości.](keyword-queries-and-search-conditions.md#guidelines-for-using-conditions)

## <a name="searching-yammer-groups"></a>Wyszukiwanie Yammer grup

Możesz użyć właściwości poczty e-mail **ItemClass** lub **warunku** wyszukiwania Typ, aby wyszukać elementy konwersacji w Yammer grupy.

  - Aby użyć właściwości **ItemClass** jako części zapytania wyszukiwania słów kluczowych, w polu Słowa kluczowe  zapytania wyszukiwania możesz wpisać jedną (lub wszystkie) z następujących par property:value:

     - ItemClass:IPM.Yammer.message
     - ItemClass:IPM.Yammer.poll
     - ItemClass:IPM.Yammer.praise
     - ItemClass:IPM.Yammer.question

    Możesz na przykład użyć następującego zapytania wyszukiwania, aby zwrócić wiadomości Yammer i Yammer elementów pochwał:

    ![Właściwość ItemClass (Klasy Elementów) jest Yammer elementów.](../media/YammerContentSearch1.png)

  - Możesz również użyć warunku Wpisz wiadomość **e-mail** i wybrać pozycję wiadomości **e-Yammer,** aby Yammer elementy. Na przykład poniższe zapytanie wyszukiwania zwróci wszystkie Yammer konwersacji zawierające słowo kluczowe "poufne".

    ![Użyj karty warunku Typ, aby wyszukać Yammer konwersacji.](../media/YammerContentSearch2.png)

## <a name="searching-inactive-mailboxes"></a>Wyszukiwanie nieaktywnych skrzynek pocztowych

Podczas przeszukiwania zawartości możesz wyszukiwać nieaktywne skrzynki pocztowe. Aby uzyskać listę nieaktywnych skrzynek pocztowych w organizacji, uruchom polecenie `Get-Mailbox -InactiveMailboxOnly` w programie Exchange Online PowerShell. Możesz również przejść do sekcji  \> Zarządzanie informacjami **Przechowywanie w Centrum** & zabezpieczeń i zgodności, ![a następnie kliknąć wielokropek paska nawigacji.](../media/9723029d-e5cd-4740-b5b1-2806e4f28208.gif) \>**Nieaktywne skrzynki pocztowe**.

Oto kilka rzeczy, o których należy pamiętać podczas wyszukiwania nieaktywnych skrzynek pocztowych.

- Jeśli istniejące przeszukiwanie zawartości obejmuje skrzynkę pocztową użytkownika i ta skrzynka pocztowa zostanie nieaktywny, przeszukiwanie zawartości będzie nadal przeszukiwać nieaktywną skrzynkę pocztową po jego ponownie uruchomić, gdy zostanie ono nieaktywne.

- Czasami użytkownik może mieć aktywną skrzynkę pocztową i nieaktywną skrzynkę pocztową o tym samym adresie SMTP. W takim przypadku przeszukana zostanie tylko skrzynka pocztowa, która została wybrane jako lokalizacja wyszukiwania zawartości. Innymi słowy, jeśli dodasz skrzynkę pocztową użytkownika do wyszukiwania, nie możesz zakładać, że są przeszukiwane zarówno aktywne, jak i nieaktywne skrzynki pocztowe. Przeszukiwana jest tylko skrzynka pocztowa, która została jawnie dodaniu do wyszukiwania.

- Za pomocą programu PowerShell & zabezpieczeń i zgodności można utworzyć przeszukiwanie zawartości w celu przeszukiwania nieaktywnej skrzynki pocztowej. W tym celu musisz wstępnie dołączyć okres ( . ) na adres e-mail nieaktywnej skrzynki pocztowej. Na przykład poniższe polecenie tworzy przeszukiwanie zawartości w celu przeszukiwania nieaktywnej skrzynki pocztowej przy użyciu adresu e-mail pavelb@contoso.onmicrosoft.com:

   ```powershell
   New-ComplianceSearch -Name InactiveMailboxSearch -ExchangeLocation .pavelb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true
   ```

- Zdecydowanie zalecamy, aby nie mieć aktywnej i nieaktywnej skrzynki pocztowej z tym samym adresem SMTP. Jeśli chcesz ponownie użyć adresu SMTP przypisanego do nieaktywnej skrzynki pocztowej, zalecamy odzyskanie nieaktywnej skrzynki pocztowej lub przywrócenie zawartości nieaktywnej skrzynki pocztowej do aktywnej skrzynki pocztowej (lub archiwum aktywnej skrzynki pocztowej), a następnie usunięcie nieaktywnej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

  - [Odzyskiwanie nieaktywnej skrzynki pocztowej w Office 365](recover-an-inactive-mailbox.md)

  - [Przywracanie nieaktywnej skrzynki pocztowej w Office 365](restore-an-inactive-mailbox.md)

  - [Usuwanie nieaktywnej skrzynki pocztowej z Office 365](delete-an-inactive-mailbox.md)

## <a name="searching-disconnected-or-de-licensed-mailboxes"></a>Wyszukiwanie odłączone lub dez licencjonowane skrzynki pocztowe

Jeśli licencja usługi Exchange Online (lub cała licencja usługi Microsoft 365) została usunięta z konta użytkownika lub w programie Azure Active Directory, skrzynka pocztowa użytkownika staje się odłączoną *skrzynką pocztową*. Oznacza to, że skrzynka pocztowa nie jest już skojarzona z kontem użytkownika. Oto co się dzieje w przypadku wyszukiwania z odłączonych skrzynek pocztowych:

- Po usunięciu licencji ze skrzynki pocztowej nie będzie już można jej przeszukiwać.

- Jeśli istniejące przeszukiwanie zawartości obejmuje skrzynkę pocztową, w której usunięto licencję, po ponownego uruchomić wyszukiwanie zawartości nie zostaną zwrócone żadne wyniki wyszukiwania z odłączonych skrzynek pocztowych.

- Jeśli za pomocą polecenia cmdlet **New-ComplianceSearch** utworzysz przeszukiwanie zawartości i określisz rozłączona skrzynkę pocztową jako lokalizację zawartości Exchange do przeszukania, wyszukiwanie zawartości nie zwróci żadnych wyników wyszukiwania z odłączonych skrzynek pocztowych.

Jeśli chcesz zachować dane w odłączanej skrzynce pocztowej w celu ich przeszukiwania, przed usunięciem licencji musisz umieścić w skrzynce pocztowej hold. Dzięki temu dane zostaną zachowywane i nie będzie można przeszukiwać odłączonych skrzynek pocztowych do momentu usunięcia zawieszonego połączenia. Aby uzyskać więcej informacji o blokadych, zobacz [Jak zidentyfikować typ blokady umieszczany w skrzynce Exchange Online pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="searching-for-content-in-a-sharepoint-multi-geo-environment"></a>Wyszukiwanie zawartości w środowisku SharePoint Multi-Geo zawartości

Jeśli menedżer zbierania elektronicznych materiałów dowodowych musi wyszukać zawartość w programach SharePoint i OneDrive w różnych regionach w środowisku wielolokalowym programu [SharePoint](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md), aby to zrobić, należy wykonać następujące czynności:

1. Utwórz osobne konto użytkownika dla każdej lokalizacji geograficznej satelitarnej, która musi zostać przeszukana przez menedżera zbierania elektronicznych materiałów dowodowych. Aby wyszukać zawartość w witrynach w tej lokalizacji geograficznej, menedżer zbierania elektronicznych materiałów dowodowych musi zalogować się do konta utworzonego dla tej lokalizacji, a następnie uruchomić wyszukiwanie zawartości.

2. Utwórz filtr uprawnień wyszukiwania dla każdej lokalizacji geograficznej satelitarnej (i odpowiadającego mu konta użytkownika), który musi przeszukać menedżer zbierania elektronicznych materiałów dowodowych. Każdy z tych filtrów uprawnień wyszukiwania ogranicza zakres wyszukiwania zawartości do określonej lokalizacji geograficznej, gdy menedżer zbierania elektronicznych materiałów dowodowych jest zalogowany do konta użytkownika skojarzonego z tą lokalizacją.

> [!TIP]
> Tej strategii nie trzeba stosować podczas korzystania z narzędzia wyszukiwania w [programie Advanced eDiscovery](overview-ediscovery-20.md). Wynika to z tego, że podczas wyszukiwania w witrynach sieci SharePoint i kontach OneDrive w programie Advanced eDiscovery. Tej strategii należy używać w przypadku kont użytkowników specyficznych dla regionu i filtrów uprawnień wyszukiwania tylko w przypadku korzystania z narzędzia Przeszukiwanie zawartości i uruchamiania wyszukiwań skojarzonych ze sprawami [zbierania elektronicznych materiałów dowodowych](./get-started-core-ediscovery.md).

Załóżmy na przykład, że menedżer zbierania elektronicznych materiałów dowodowych musi wyszukać zawartość SharePoint i OneDrive w lokalizacjach satelitarnych w Ameryce Północnej, Europie i Azji Pacyfiku. Pierwszym krokiem jest utworzenie trzech kont użytkowników, po jednym dla każdej lokalizacji. Następnym krokiem jest utworzenie trzech filtrów uprawnień wyszukiwania: jednego dla każdej lokalizacji *i odpowiadającego* mu konta użytkownika. Oto przykłady trzech filtrów uprawnień wyszukiwania dla tego scenariusza. W każdym z tych przykładów **region** określa lokalizację centrum danych SharePoint dla tej lokalizacji geograficznej, a parametr **Użytkownicy** określa odpowiednie konto użytkownika.

**Ameryka Północna**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-NAM" -Users ediscovery-nam@contoso.com -Region NAM -Action ALL
```

**Europa**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-EUR" -Users ediscovery-eur@contoso.com -Region EUR -Action ALL
```

**Azja i Pacyfik**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-APC" -Users ediscovery-apc@contoso.com -Region APC -Action ALL
```

Używając filtrów uprawnień wyszukiwania do wyszukiwania zawartości w środowiskach wielolokalizacji, należy pamiętać o następujących kwestiach:

- Parametr **Region** kieruje wyszukiwania do określonej lokalizacji satelitarnej. Jeśli menedżer zbierania elektronicznych materiałów dowodowych przeszukuje tylko witryny SharePoint i OneDrive poza regionem określonym w filtrze uprawnień wyszukiwania, nie są zwracane żadne wyniki wyszukiwania.

- Parametr **Region** nie kontroluje przeszukiwania skrzynek Exchange pocztowych. Podczas przeszukiwania skrzynek pocztowych przeszukiwane są wszystkie centra danych.

Aby uzyskać więcej informacji na temat używania filtrów uprawnień wyszukiwania w środowisku wielolokalowym, zobacz sekcję "Wyszukiwanie i eksportowanie zawartości w środowiskach wielowymiarowych" w tece Konfigurowanie granic zgodności dla badań zbierania elektronicznych materiałów [dowodowych](set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).
