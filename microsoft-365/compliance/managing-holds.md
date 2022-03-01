---
title: Zarządzanie rekordami w Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Dowiedz się, jak ująć w treści treści i ich źródła danych, aby zachować odpowiednią zawartość Advanced eDiscovery przypadku.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkMAC
ms.openlocfilehash: 2c19b608f01f30df83e914bbe34d29aa85bd5af3
ms.sourcegitcommit: 2e05865beeb2051fd9ece212a46179310b946a46
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2021
ms.locfileid: "63007503"
---
# <a name="manage-holds-in-advanced-ediscovery"></a>Zarządzanie rekordami w Advanced eDiscovery

Przy użyciu sprawy Advanced eDiscovery można utworzyć blokady w celu zachowania zawartości, która może być istotny dla danej sprawy. Przy użyciu Advanced eDiscovery przechowywania można umieścić blokady na przechwytników i ich źródłach danych. Ponadto możesz umieścić w skrzynkach pocztowych i witrynach internetowych niezabędące grupy OneDrive dla Firm. Możesz także umieścić wstrzymaj skrzynkę pocztową grupy, witrynę SharePoint, a OneDrive dla Firm witrynie grupy Microsoft 365 grupy. Podobnie możesz umieścić wstrzymaj skrzynkę pocztową i witrynę skojarzoną z Microsoft Teams. Po umieszczenie lokalizacji zawartości w miejscu przechowywania zawartość jest umieszczana do czasu zwolnienia przechowywania, usunięcia określonej lokalizacji danych lub usunięcia całkowicie zasad przechowywania.

## <a name="manage-custodian-based-holds"></a>Zarządzanie blokadymi opartymi na u użytkownikach

W niektórych przypadkach może zostać wskazany zestaw opiekunów i zdecydowano się na zachowanie danych podczas tej sprawy. Po Advanced eDiscovery przechowywania tych elementy uruchamiacze są automatycznie dodawane do zasad przechowywania w czacie użytkownika i wybranych przez nich źródeł danych.

Aby wyświetlić zasady przechowywania dla osób, które nie mają prawa do przechowywania:

1. W Centrum zgodności platformy Microsoft 365 wiadomości kliknij pozycję **zbierania elektronicznych** materiałów dowodowych > Zaawansowane, aby wyświetlić listę spraw w Twojej organizacji.

2. Przejdź do karty **Źródła** , aby dodać opiekunów w obrębie sprawy. Aby dowiedzieć się, jak dodawać i umieszczać przechowywać przechowywać w Advanced eDiscovery przypadku, zobacz Dodawanie osób do [sprawy](add-custodians-to-case.md). Jeśli zostały już dodane i umieszczone w agorze, przejdź do kroku 3.

3. Przejdź na kartę **Zachowaje** i kliknij **pozycjęHoldianHold\<HoldId>** ..

4. Na wysuwanych stronie możesz zobaczyć statystykę blokowania dla zasad. Można również wykonywać akcje, takie jak zastosowanie zapytania do holdsu opartego na danych do przechowywania. Aby uzyskać więcej informacji na temat tworzenia zapytania wstrzymywania i używania warunków, zobacz Zapytania słów kluczowych [i warunki wyszukiwania dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Zarządzanie blokadym typu non-ialial holdsial

Po utworzeniu wstrzymywania dostępne są następujące opcje zakresu zawartości przechowywanej w określonych lokalizacjach zawartości:

- Tworzysz nieskończoną liczbę miejsc, w których cała zawartość jest umieszczana w hold. Można również utworzyć hold oparty na kwerendzie, w którym wstrzymywana jest tylko zawartość, która jest dosyć do kwerendy wyszukiwania.
  
- Zakres dat można określić, aby była w tym zakresie tylko ta zawartość, która została wysłana, odebrana lub utworzona w tym zakresie. Ewentualnie możesz przechowywać całą zawartość niezależnie od tego, kiedy została wysłana, odebrana lub utworzona.

Aby utworzyć zbędną przechowywania danych dla sprawy Advanced eDiscovery przypadku:

1. Na liście <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> pozycję Zbierania elektronicznych materiałów dowodowych **> zaawansowane**, aby wyświetlić listę spraw w Organizacji.
  
2. Kliknij **przycisk** Otwórz obok sprawy, w której chcesz utworzyć blokady.
  
3. Na stronie głównej sprawy kliknij kartę **Z blokady** .
  
4. Na karcie **Blokady** kliknij pozycję **Utwórz**.
  
5. Na stronie **Nadaj nazwę** hold (Nadaj nazwę holdowi). Nazwa hold musi być unikatowa w Twojej organizacji.

6. (Opcjonalnie) W **polu** Opis dodaj opis hold.
  
7. Kliknij **Dalej**.
  
8. Wybierz lokalizacje zawartości, które mają zostać zawieszone. Możesz umieścić skrzynki pocztowe, witryny i foldery publiczne w miejscu przechowywania.

   1. **Exchange-mail** — kliknij pozycję Wybierz użytkowników, grupy lub zespoły **,** a następnie ponownie kliknij pozycję Wybierz użytkowników, grupy lub **zespoły,** aby określić skrzynki pocztowe do przechowywania. Użyj pola wyszukiwania, aby znaleźć skrzynki pocztowe użytkowników i grupy dystrybucyjne (aby umieścić je w miejscu przechowywania w skrzynkach pocztowych członków grupy), aby umieścić je w a hold. Możesz także umieścić wstrzymaj skojarzoną skrzynkę pocztową dla grupy Microsoft 365 lub zespołu Microsoft. Zaznacz pole wyboru użytkownik, grupa, zespół, kliknij pozycję **Wybierz**, a następnie kliknij pozycję **Gotowe**.

      > [!NOTE]
      > Po kliknięciu **przycisku Wybierz użytkowników, grupy lub zespoły** w celu określenia skrzynek pocztowych, które mają być zawieszone, wyświetlany s picker skrzynki pocztowej jest pusty. Jest to zaprojektowany w celu zwiększenia wydajności. Aby dodać osoby do tej listy, wpisz nazwę (co najmniej 3 znaki) w polu wyszukiwania.

   1. **SharePoint witryny —** kliknij pozycję Wybierz witryny, a następnie ponownie kliknij  pozycję Wybierz witryny, aby określić SharePoint, OneDrive dla Firm, które mają być zawieszone. Wpisz adres URL każdej witryny, którą chcesz umieścić w miejscu przechowywania. Możesz również dodać adres URL witryny SharePoint grupy Microsoft 365 lub zespołu Microsoft. Kliknij **pozycję** Wybierz, a następnie kliknij pozycję **Gotowe**.

      > [!NOTE]
      > Adres URL konta użytkownika OneDrive zawiera jego główną nazwę użytkownika (GŁÓWNĄ nazwę użytkownika), na przykład `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). W rzadkich przypadkach, w której głównej nazwa sieci OneDrive głównej osoby, adres URL tej osoby również zostanie zmieniony, aby włączyć nową nazwę UPN. Jeśli konto użytkownika OneDrive jest częścią niebędące przechowywania danych i jego głównej nazwy użytkownika zostanie zmieniona, należy zaktualizować to hold i wskazać nowy adres URL OneDrive URL. Aby uzyskać więcej informacji, zobacz [Jak zmiany głównej sieci użytkowników wpływają na OneDrive URL](/onedrive/upn-changes).

   1. **Exchange foldery** publiczne — przesuń przełącznik do pozycji Wszystkie, aby umieścić wszystkie foldery publiczne w Exchange Online wstrzymaj. Nie można wybrać konkretnych folderów publicznych, które mają zostać zawieszone. Jeśli nie chcesz przechowywać folderów publicznych, pozostaw przełącznik ustawiony jako Brak.

9. Po dodaniu lokalizacji zawartości do hold kliknij przycisk **Dalej**.
  
10. Aby utworzyć hold oparty na kwerendzie z warunkami, wykonaj następujące czynności. W przeciwnym razie po prostu kliknij **przycisk Dalej**.

    - W polu w obszarze **Słowa** kluczowe wpisz w polu zapytanie wyszukiwania, aby wstrzymywać tylko zawartość spełniająca kryteria wyszukiwania. Możesz określić słowa kluczowe, właściwości wiadomości lub właściwości dokumentu, takie jak nazwy plików. Można także używać bardziej złożonych zapytań, które używają operatora logicznych, takiego jak AND, OR lub NOT. Jeśli pozostawisz pole słowa kluczowego puste, cała zawartość znajdująca się w określonych lokalizacjach zawartości zostanie umieszczona w wstrzymaniu.

    - Kliknij  **pozycję** Dodaj warunki, aby dodać jeden lub więcej warunków, aby zawęzić kwerendę wyszukiwania dla wstrzymywania. Każdy warunek powoduje dodanie klauzuli do zapytania wyszukiwania WKQL, które jest tworzone i uruchamiane podczas tworzenia holdu. Można na przykład określić zakres dat, aby wiadomości e-mail lub dokumenty witryny utworzone w zakresie dat umieszczać w miejscu wstrzymywania. Warunek jest logicznie połączony z zapytaniem słowa kluczowego (określonym w polu słowa kluczowego) przez operator AND. Oznacza to, że elementy muszą spełniać zarówno zapytanie słów kluczowych, jak i warunek, który ma zostać umieszczony w hold.

     Aby uzyskać więcej informacji na temat tworzenia zapytania wyszukiwania i używania warunków, zobacz Zapytania [słów kluczowych i warunki wyszukiwania dotyczące wyszukiwania zawartości](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Po skonfigurowaniu hold'a opartego na kwerendzie kliknij przycisk **Dalej**.

12. Przejrzyj ustawienia, a następnie kliknij pozycję **Utwórz to hold**.

> [!NOTE]
> Jeśli adres SMTP użytkownika zmieni się po zatrzymaniu skrzynki pocztowej użytkownika, pozostanie ona w tym miejscu. Aby użyć nowego adresu SMTP do stosowania wstrzymywania, utwórz nowe hold.

## <a name="view-hold-statistics"></a>Wyświetl statystykę zawieszonego widoku

Po pewnym czasie informacje o nowym ztrzymaniu zostaną wyświetlone w okienku szczegółów na karcie  Blokady dla wybranego blokady. Te informacje obejmują liczbę skrzynek pocztowych i witryn umieszczonych w hold' oraz statystyki dotyczące zawartości, która została umieszczona w hold, na przykład całkowita liczba i rozmiar elementów umieszczonych w a holdie oraz czas ostatniego obliczania statystyki dotyczącej blokowania. Statystyki te ułatwiają ustalenie, ile zawartości związanej ze sprawą zbierania elektronicznych materiałów dowodowych jest przechowywane.

W statystyce dotyczącej zawieszonego przechowywania należy pamiętać o następujących kwestiach:

- Całkowita liczba elementów wstrzymywanych wskazuje liczbę elementów ze wszystkich źródeł zawartości, które są umieszczone w hold. Jeśli utworzono hold oparte na kwerendzie, ta statystyka wskazuje liczbę elementów, które pasują do zapytania.
  
- Liczba elementów w hold obejmuje również elementy nieindeksowane odnalezione w lokalizacjach zawartości. Jeśli utworzysz hold oparte na kwerendzie, wszystkie elementy nieindeksowane w lokalizacjach zawartości zostaną umieszczone w hold. Dotyczy to elementów nieindeksowanych, które nie są zgodne z kryteriami wyszukiwania opartymi na kwerendzie i elementów nieindeksowanych, które mogą być spoza warunku zakresu dat. Jest to inne niż to, co dzieje się po uruchomieniu wyszukiwania zawartości, w którym elementy nieindeksowane, które nie są zgodne z zapytaniem wyszukiwania lub są wykluczane przez warunek zakresu dat, nie są uwzględniane w wynikach wyszukiwania. Aby uzyskać więcej informacji na temat elementów nieindeksowanych, zobacz [Częściowo indeksowane elementy w przeszukiwaniu zawartości w programie Office 365](partially-indexed-items-in-content-search.md).

- Możesz uzyskać najnowsze statystyki dotyczące blokowania, klikając pozycję Aktualizuj statystykę, aby ponownie uruchomić oszacowanie wyszukiwania, które oblicza bieżącą liczbę elementów w wstrzymaniu.

- W razie potrzeby kliknij pozycję Odśwież na pasku narzędzi, aby zaktualizować statystykę blokowania w okienku szczegółów.

- Zazwyczaj liczba wstrzymanych elementów zwiększa się w czasie, ponieważ użytkownicy, których skrzynka pocztowa lub witryna znajdują się w miejscu, zazwyczaj wysyłają lub otrzymują nową wiadomość e-mail oraz tworzą nowe dokumenty SharePoint i OneDrive dla Firm e-mail.

- Jeśli konto SharePoint lub konta OneDrive zostanie przeniesione do innego regionu w środowisku wielolokalowym, statystyki dotyczące tej witryny nie będą uwzględniane w statystykach dotyczących blokowania. Zawartość witryny będzie jednak nadal wstrzymywana. Ponadto, jeśli witryna zostanie przeniesiona do innego regionu, adres URL wyświetlany w witrynie nie zostanie zaktualizowany. Musisz edytować wstrzymywanie i zaktualizować adres URL.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Hold on Microsoft Teams and Office 365 Groups

Microsoft Teams jest wbudowana w Office 365 grupy. Dlatego umieszczenie ich w Advanced eDiscovery jest podobne.

- **Jak zamapować dodatkową witrynę sieci Microsoft 365 lub witryny Microsoft Teams na witrynę iniekcyjną? A co z umieszczaniem w grupach danych i Microsoft 365 grupach danych bez Microsoft Teams?** Microsoft Teams jest wbudowana w Microsoft 365 grupy. Dlatego umieszczenie ich w posiadaniu sprawy zbierania elektronicznych materiałów dowodowych jest podobne. Podczas umieszczania grup Microsoft 365 i umieszczania ich w Microsoft Teams należy pamiętać o następujących kwestiach.

  - Aby umieścić zawartość w grupach Microsoft 365 i umieścić Microsoft Teams w stanie przechowywania, musisz określić skrzynkę pocztową i SharePoint skojarzoną z grupą lub zespołem.
  
  - Uruchom polecenie **cmdlet Get-UnifiedGroup** w programie Exchange Online, aby wyświetlić właściwości grupy Microsoft 365 lub zespołu Microsoft. Jest to dobry sposób na uzyskania adresu URL witryny skojarzonej z grupą Microsoft 365 lub zespołem Microsoft. Na przykład następujące polecenie wyświetla wybrane właściwości grupy kierownictwa Microsoft 365 o nazwie Starszy zespół kierownictwa:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Aby uruchomić polecenie cmdlet Get-UnifiedGroup, musisz mieć przypisaną rolę adresatów View-Only w programie Exchange Online lub być członkiem grupy ról z przypisaną rolą adresatów View-Only adresatów.

  - Podczas przeszukiwania skrzynki pocztowej użytkownika nie będą Microsoft 365 grupy ani zespołu Microsoft, do których należy użytkownik. Podobnie po umieszczeniu grupy Microsoft 365 lub witryny zespołu firmy Microsoft wstrzymywana jest tylko skrzynka pocztowa grupy i witryna grupy; skrzynki pocztowe i witryny grupy OneDrive dla Firm nie są umieszczane w a holdie, chyba że jawnie dodasz je jako osoby przechwycące lub umieścisz ich źródła danych. Jeśli w związku z tym musisz umieścić grupę Microsoft 365 lub zespół Microsoft Team w miejscu określonego adresata, rozważ zamapowanie witryny grupy i skrzynki pocztowej grupy na skrzynkę odbiorczy (zobacz Zarządzanie odbiorcami w systemie Advanced eDiscovery). Jeśli grupa Microsoft 365 lub zespół Firmy Microsoft nie zostanie przypisana do jednego opiekuna, rozważ dodanie źródła do aresztu niebędącego plikiem źródłowym.
  - Aby uzyskać listę członków grupy Microsoft 365 lub zespołu Microsoft,  >  można wyświetlić właściwości na stronie Grupy domowe w centrum administracyjne platformy Microsoft 365.[](https://go.microsoft.com/fwlink/p/?linkid=2052855) Możesz również uruchomić następujące polecenie w programie Exchange Online PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Aby uruchomić polecenie **cmdlet Get-UnifiedGroupLinks**, musisz mieć przypisaną rolę adresatów View-Only w programie Exchange Online lub być członkiem grupy ról z przypisaną rolą adresatów View-Only.

  - Konwersacje w kanale, które są częścią Microsoft Teams są przechowywane w skrzynce pocztowej skojarzonej z zespołem. Podobnie pliki, które członkowie zespołu mają udział w kanale, są przechowywane w SharePoint zespołu. Dlatego, aby zachować konwersacje i pliki w kanale, SharePoint przechowywać konwersacje i pliki w kanale, należy umieścić skrzynkę pocztową usługi Microsoft Team i umieścić witrynę w awitrynie.
  
  - Konwersacje, które są częścią listy czatów w programie Microsoft Teams są przechowywane w skrzynce pocztowej użytkownika, który uczestniczy w czacie.  Pliki, które użytkownik udostępnia w konwersacjach na czacie, są przechowywane OneDrive dla Firm witryny użytkownika, który udostępnia plik. Dlatego, aby zachować konwersacje i pliki na liście czatów, należy umieścić skrzynki pocztowe poszczególnych użytkowników i OneDrive dla Firm witryn.
  
  - Każdy kanał zespołu lub zespołu firmy Microsoft zawiera stronę typu wiki do sporządzania notacji i współpracy. Zawartość typu wiki jest automatycznie zapisywana w pliku w formacie mht. Ten plik jest przechowywany w bibliotece Teams danych typu wiki w witrynie zespołu SharePoint wiki. Zawartość witryny typu wiki można umieścić w a hold, umieszczając witrynę zespołu w SharePoint wstrzymywanie.

    > [!NOTE]
    > 22 czerwca 2017 r. opublikowano funkcję przechowywania zawartości typu wiki dla zespołu lub kanału zespołu (po SharePoint zespołu w witrynie zespołu). Jeśli witryna zespołu znajduje się w wstrzymaniu, jej zawartość będzie zachowywana od tego dnia. Jednak jeśli witryna zespołu znajduje się w miejscu, a zawartość typu wiki została usunięta przed 22 czerwca 2017 r., zawartość witryny typu wiki nie została zachowana.
