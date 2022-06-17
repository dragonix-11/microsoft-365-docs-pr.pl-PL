---
title: Dlaczego musisz używać programu PowerShell do Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: admindeeplinkEXCHANGE
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Podsumowanie: Dowiedz się, dlaczego należy używać programu PowerShell do zarządzania Microsoft 365, w niektórych przypadkach bardziej wydajnie, a w innych przypadkach z konieczności.'
ms.openlocfilehash: 0da00ffe3c492b3bac3da9f435ece89219b4113f
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139368"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Dlaczego musisz używać programu PowerShell do Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Za pomocą Centrum administracyjne platformy Microsoft 365 możesz zarządzać Microsoft 365 kontami użytkowników i licencjami. Możesz również zarządzać usługami Microsoft 365, takimi jak Exchange Online, Teams i SharePoint Online. Jeśli zamiast tego używasz programu PowerShell do zarządzania tymi usługami, możesz skorzystać ze środowiska języka wiersza polecenia i skryptów w celu zapewnienia szybkości, automatyzacji i dodatkowych możliwości.

W tym artykule pokazano, jak zarządzać Microsoft 365 za pomocą programu PowerShell:

- Ujawnij dodatkowe informacje, których nie widać w Centrum administracyjne platformy Microsoft 365

- Konfigurowanie funkcji i ustawień jest możliwe tylko za pomocą programu PowerShell

- Wykonywanie operacji zbiorczych

- Filtrowanie danych

- Drukowanie lub zapisywanie danych

- Zarządzanie między usługami

Należy pamiętać, że program PowerShell dla Microsoft 365 to zestaw modułów dla Windows PowerShell, który jest środowiskiem wiersza polecenia dla usług i platform opartych na Windows. To środowisko tworzy język powłoki poleceń, który można rozszerzyć o dodatkowe moduły. Umożliwia wykonywanie prostych lub złożonych poleceń lub skryptów. Na przykład po zainstalowaniu programu PowerShell dla modułów Microsoft 365 i nawiązaniu połączenia z subskrypcją Microsoft 365 można uruchomić następujące polecenie, aby wyświetlić listę wszystkich skrzynek pocztowych użytkownika dla Microsoft Exchange Online:

```powershell
Get-Mailbox
```

Możesz również uzyskać listę skrzynek pocztowych przy użyciu Centrum administracyjne platformy Microsoft 365 ale zliczanie elementów na wszystkich listach dla wszystkich witryn dla wszystkich aplikacji internetowych nie jest łatwe.

Program PowerShell dla Microsoft 365 ma na celu ułatwienie zarządzania Microsoft 365, a nie zastępowanie Centrum administracyjne platformy Microsoft 365. Administratorzy muszą mieć możliwość używania programu PowerShell dla Microsoft 365, ponieważ istnieją pewne procedury konfiguracji, które można wykonać tylko za pośrednictwem programu PowerShell dla poleceń Microsoft 365. W takich przypadkach musisz wiedzieć, jak:

- Zainstaluj program PowerShell dla modułów Microsoft 365 (wykonanych tylko raz dla każdego komputera administratora).

- Połączenie do subskrypcji Microsoft 365 (raz dla każdej sesji programu PowerShell).

- Zbierz informacje potrzebne do uruchomienia wymaganego programu PowerShell dla poleceń Microsoft 365.

- Uruchom program PowerShell dla poleceń Microsoft 365.

Po zapoznaniu się z tymi podstawowymi umiejętnościami nie musisz wyświetlać listy użytkowników skrzynek pocztowych przy użyciu polecenia **Get-Mailbox** . Nie musisz również rozumieć, jak utworzyć nowe polecenie, takie jak cytowane wcześniej polecenie, aby zliczyć wszystkie elementy na wszystkich listach dla wszystkich witryn dla wszystkich aplikacji internetowych. Firma Microsoft i społeczność administratorów mogą ci pomóc w wykonywaniu takich zadań w razie potrzeby.

## <a name="powershell-for-microsoft-365-can-reveal-information-that-you-cant-see-with-the-microsoft-365-admin-center"></a>Program PowerShell dla Microsoft 365 może ujawnić informacje, których nie widać w Centrum administracyjne platformy Microsoft 365

W Centrum administracyjne platformy Microsoft 365 jest wyświetlanych wiele przydatnych informacji. Ale nie wyświetla wszystkich możliwych informacji, które Microsoft 365 przechowuje o użytkownikach, licencjach, skrzynkach pocztowych i witrynach. Oto przykład dla *użytkowników i grup* w Centrum administracyjne platformy Microsoft 365:

![Przykład wyświetlania użytkowników i grup w Centrum administracyjne platformy Microsoft 365.](../media/o365-powershell-users-and-groups.png)

Ten widok zawiera informacje, które są potrzebne w wielu przypadkach. Jednak są chwile, kiedy potrzebujesz więcej. Na przykład Microsoft 365 licencjonowanie (i funkcje Microsoft 365 dostępne dla użytkownika) zależy częściowo od lokalizacji geograficznej użytkownika. Zasady i funkcje, które można rozszerzyć na użytkownika, który mieszka w Stany Zjednoczone, mogą nie być takie same jak te, które można rozszerzyć na użytkownika w Indiach lub Belgii. Wykonaj następujące kroki w Centrum administracyjne platformy Microsoft 365, aby określić lokalizację geograficzną użytkownika:

1. Kliknij dwukrotnie **nazwę wyświetlaną** użytkownika.

2. W okienku wyświetlania właściwości użytkownika wybierz **szczegóły**.

3. Na ekranie szczegółów wybierz **dodatkowe szczegóły**.

4. Przewiń, aż znajdziesz nagłówek **Kraj lub region**:

     ![Przykład informacji o regionie użytkownika w Centrum administracyjne platformy Microsoft 365.](../media/o365-powershell-usage-location.png)

5. Zapisz nazwę wyświetlaną użytkownika i lokalizację na kartce papieru lub skopiuj ją i wklej do Notatnik.

Należy powtórzyć tę procedurę dla każdego użytkownika. Jeśli masz wielu użytkowników, ten proces może być żmudny. Za pomocą programu PowerShell dla Microsoft 365 możesz wyświetlić te informacje dla wszystkich użytkowników przy użyciu następującego polecenia:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet, które mają nazwę *msol*. Musisz uruchomić te polecenia cmdlet z Windows PowerShell.
>

Oto przykład wyników:

```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

Interpretacja tego polecenia programu PowerShell to: Pobierz wszystkich użytkowników w bieżącej subskrypcji Microsoft 365 (**Get-AzureADUser**), ale wyświetlaj tylko nazwę i lokalizację dla każdego użytkownika (**wybierz pozycję DisplayName, UsageLocation**).

Ponieważ program PowerShell for Microsoft 365 obsługuje język powłoki poleceń, możesz dalej manipulować informacjami uzyskanymi za pomocą polecenia **Get-AzureADUser**. Na przykład możesz posortować tych użytkowników według ich lokalizacji, grupując wszystkich brazylijskich użytkowników razem, wszystkie Stany Zjednoczone użytkowników i tak dalej. Oto polecenie:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Oto przykład wyników:

```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

Interpretacja tego polecenia programu PowerShell jest następująca: Pobierz wszystkich użytkowników w bieżącej subskrypcji Microsoft 365, ale wyświetl tylko nazwę i lokalizację dla każdego użytkownika i posortuj ich najpierw według lokalizacji, a następnie nazwy (**Sort UsageLocation, DisplayName**).

Można również użyć dodatkowego filtrowania. Jeśli na przykład chcesz wyświetlić tylko informacje o użytkownikach z brazylii, użyj tego polecenia:

```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation
```

Oto przykład wyników:

```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

Interpretacja tego polecenia programu PowerShell to: Pobierz wszystkich użytkowników w bieżącej subskrypcji Microsoft 365, której lokalizacja to Brazylia (**gdzie {$\_). UsageLocation -eq "BR"}**), a następnie wyświetl nazwę i lokalizację dla każdego użytkownika.

 **Uwaga dotycząca dużych domen**

Jeśli masz dużą domenę z dziesiątkami tysięcy użytkowników, wypróbowanie niektórych przykładów, które przedstawiono w tym artykule, może prowadzić do ograniczania przepustowości. W oparciu o takie czynniki, jak moc obliczeniowa i dostępna przepustowość sieci, możesz próbować zrobić zbyt wiele jednocześnie. Duże organizacje mogą chcieć podzielić niektóre z tych operacji programu PowerShell na dwa polecenia.

Na przykład następujące polecenie zwraca wszystkie konta użytkowników i pokazuje nazwę i lokalizację dla każdego z nich:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

To działa świetnie w przypadku mniejszych domen. Jednak w dużej organizacji warto podzielić tę operację na dwa polecenia: jedno polecenie do przechowywania informacji o koncie użytkownika w zmiennej, a drugie w celu wyświetlenia potrzebnych informacji. Oto przykład:

```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

Interpretacja tego zestawu poleceń programu PowerShell to:
1. Pobierz wszystkich użytkowników w bieżącej subskrypcji Microsoft 365 i zapisz informacje w zmiennej o nazwie $x (**$x = Get-AzureADUser**).
1.  Wyświetl zawartość *zmiennej $x*, ale uwzględnij tylko nazwę i lokalizację dla każdego użytkownika (**$x | Wybierz pozycję DisplayName, UsageLocation**).

## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 ma funkcje, które można skonfigurować tylko za pomocą programu PowerShell dla Microsoft 365

Centrum administracyjne platformy Microsoft 365 ma na celu zapewnienie dostępu do typowych, przydatnych zadań administracyjnych, które mają zastosowanie do większości środowisk. Innymi słowy, Centrum administracyjne platformy Microsoft 365 została zaprojektowana tak, aby typowy administrator mógł wykonywać najczęstsze zadania zarządzania. Istnieją jednak pewne zadania, których nie można wykonać w centrum administracyjnym.

Na przykład centrum administracyjne usługi Skype dla firm Online oferuje kilka opcji tworzenia niestandardowych zaproszeń na spotkania:

![Przykład wyświetlania niestandardowych zaproszeń na spotkania w centrum Administracja Skype dla firm Online.](../media/o365-powershell-meeting-invitation.png)

Za pomocą tych ustawień możesz dodać odrobinę personalizacji i profesjonalizmu do zaproszeń na spotkania. Jednak ustawienia konfiguracji spotkania to coś więcej niż tylko tworzenie niestandardowych zaproszeń na spotkania. Na przykład domyślnie spotkania zezwalają na:

- Anonimowi użytkownicy uzyskują automatyczne wejście do każdego spotkania.

- Uczestnicy nagrywania spotkania.

- Podczas dołączania do spotkania wszyscy użytkownicy z organizacji mają zostać wyznaczeni jako prezenterzy.

Te ustawienia nie są dostępne w centrum administracyjnym usługi Skype dla firm Online. Możesz kontrolować je za pomocą programu PowerShell dla Microsoft 365. Oto polecenie, które wyłącza te trzy ustawienia:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Aby uruchomić to polecenie, należy zainstalować [moduł Skype dla firm Online programu PowerShell](/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-the-skype-for-business-online-connector).

Interpretacja tego polecenia programu PowerShell to:

1. W ustawieniach nowych spotkań Skype dla firm Online (**Set-CsMeetingConfiguration**) wyłącz zezwalanie anonimowym użytkownikom na automatyczne wejście na spotkania (**-AdmitAnonymousUsersByDefault $False**).
2.  Wyłącz możliwość rejestrowania spotkań przez uczestników (**-AllowConferenceRecording $False**).
3. Nie wyznaczaj wszystkich użytkowników z organizacji jako prezenterów (**-DesignateAsPresenter "None"**).

Aby przywrócić te ustawienia domyślne (włącz opcje), uruchom następujące polecenie:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Istnieją również inne podobne scenariusze, dlatego administratorzy powinni wiedzieć, jak uruchamiać program PowerShell dla poleceń Microsoft 365.

## <a name="powershell-for-microsoft-365-is-great-for-bulk-operations"></a>Program PowerShell dla Microsoft 365 doskonale nadaje się do operacji zbiorczych

Interfejsy wizualne, takie jak Centrum administracyjne platformy Microsoft 365, są najbardziej wartościowe, gdy masz jedną operację do wykonania. Jeśli na przykład musisz wyłączyć jedno konto użytkownika, możesz użyć centrum administracyjnego, aby szybko zlokalizować i wyczyścić pole wyboru. Może to być łatwiejsze niż wykonanie podobnej operacji w programie PowerShell.

Ale jeśli musisz zmienić wiele rzeczy lub niektóre wybrane rzeczy w ramach dużego zestawu innych rzeczy, Centrum administracyjne platformy Microsoft 365 może nie być najlepszym narzędziem. Załóżmy na przykład, że musisz zmienić prefiks na tysiącach numerów telefonów lub usunąć określonego użytkownika *Kena Myera* ze wszystkich witryn SharePoint Online. Jak to zrobić w Centrum administracyjne platformy Microsoft 365?

W ostatnim przykładzie załóżmy, że masz kilkaset SharePoint witryn online i nie wiesz, do których z nich należy Ken Meyer. Należy zacząć od Centrum administracyjne platformy Microsoft 365, a następnie wykonać tę procedurę dla każdej lokacji:

1. Wybierz **adres URL** witryny.

2. W polu **właściwości zbioru witryn** wybierz link **Adres witryny sieci Web** , aby otworzyć witrynę.

3. W witrynie wybierz pozycję **Udostępnij**.

4. W oknie dialogowym **Udostępnianie** wybierz link pokazujący wszystkich użytkowników, którzy mają uprawnienia do witryny:

     ![Przykład wyświetlania elementów członkowskich witryny SharePoint Online w centrum Administracja SharePoint Online.](../media/o365-powershell-view-permissions.png)

5. W oknie dialogowym **Udostępnianie** wybierz pozycję **Zaawansowane**.

6. Przewiń w dół listę użytkowników, znajdź i wybierz pozycję Ken Myer (zakładając, że ma uprawnienia do witryny), a następnie wybierz pozycję **Usuń uprawnienia użytkownika**.

Zajęłoby to *dużo* czasu dla kilkuset witryn.

Alternatywą jest uruchomienie następującego polecenia w programie PowerShell dla Microsoft 365, aby usunąć Kena Myera ze wszystkich witryn:

```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> To polecenie wymaga zainstalowania [modułu SharePoint Online programu PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Interpretacja tego polecenia programu PowerShell: Pobierz wszystkie witryny SharePoint w bieżącej subskrypcji Microsoft 365 (**Get-SPOSite**) i dla każdej witryny usuń Kena Meyera z listy użytkowników, którzy mogą uzyskać do niej dostęp (**ForEach {Remove-SPOUser -Site $\_. Url -LoginName "kenmyer\@litwareinc.com"}**).

Mówimy Microsoft 365, aby usunąć Ken Meyer z każdej strony, w tym tych, że nie ma dostępu do. Wyniki będą więc pokazywać błędy dla tych witryn, do których nie ma dostępu. Możemy użyć dodatkowego warunku dla tego polecenia, aby usunąć Ken Meyer tylko z witryn, które mają go na liście logowania. Ale zwrócone błędy nie powodują szkody dla samych witryn. Uruchomienie tego polecenia może potrwać kilka minut względem setek witryn, a nie godzin pracy za pośrednictwem Centrum administracyjne platformy Microsoft 365.

Oto kolejny przykład operacji zbiorczej. Użyj tego polecenia, aby dodać *bonnie Kearney*, nowy administrator SharePoint, do wszystkich witryn w organizacji:

```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

Interpretacja tego polecenia programu PowerShell jest następująca: Pobierz wszystkie witryny SharePoint w bieżącej subskrypcji Microsoft 365 i dla każdej witryny zezwalaj na dostęp Bonnie Kearney, dodając jej nazwę logowania do grupy **Członkowie witryny (ForEach {Add-SPOUser -Site $\_. Url -LoginName "bkearney\@litwareinc.com" -Group "Members"}**).

## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>Program PowerShell dla Microsoft 365 doskonale nadaje się do filtrowania danych

Centrum administracyjne platformy Microsoft 365 udostępnia kilka sposobów filtrowania danych w celu łatwego zlokalizowania docelowego podzestawu informacji. Na przykład Exchange ułatwia filtrowanie praktycznie dowolnej właściwości skrzynki pocztowej użytkownika. Oto lista skrzynek pocztowych dla wszystkich użytkowników mieszkających w mieście Bloomington:

![Przykład zaawansowanego wyszukiwania w Centrum administracyjne platformy Microsoft 365 listy skrzynek pocztowych dla wszystkich użytkowników mieszkających w mieście Bloomington.](../media/o365-powershell-advanced-search.png)

<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centrum administracyjne Exchange</a> umożliwia również łączenie kryteriów filtrowania. Na przykład możesz znaleźć skrzynki pocztowe dla wszystkich osób mieszkających w Bloomington i działających w dziale finansów.

Istnieją jednak ograniczenia dotyczące tego, co można zrobić w centrum Exchange Administracja. Na przykład nie można tak łatwo znaleźć skrzynek pocztowych osób mieszkających w Bloomington *lub* San Diego, ani skrzynek pocztowych dla wszystkich osób, które nie mieszkają w Bloomington.

Aby uzyskać listę skrzynek pocztowych dla wszystkich osób mieszkających w Bloomington lub San Diego, możesz użyć następującego polecenia programu PowerShell dla Microsoft 365:

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

Oto przykład wyników:

```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

Interpretacja tego polecenia programu PowerShell to: Pobierz wszystkich użytkowników w bieżącej subskrypcji Microsoft 365, którzy mają skrzynkę pocztową w mieście San Diego lub Bloomington (**gdzie {$\_). RecipientTypeDetails -eq "UserMailbox" -i ($\_. Miasto -eq "San Diego" -lub $\_. City -eq "Bloomington")}**), a następnie wyświetl nazwę i miasto dla każdego (**Wybierz nazwę wyświetlaną, miasto**).

A oto polecenie, aby wyświetlić listę wszystkich skrzynek pocztowych dla osób, które mieszkają w dowolnym miejscu z wyjątkiem Bloomington:

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Oto przykład wyników:

```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

Interpretacja tego polecenia programu PowerShell to: Pobierz wszystkich użytkowników w bieżącej subskrypcji Microsoft 365, którzy mają skrzynkę pocztową, która nie znajduje się w mieście Bloomington (**gdzie {$\_). RecipientTypeDetails -eq "UserMailbox" -i $\_. City -ne "Bloomington"}**), a następnie wyświetl nazwę i miasto dla każdego.

### <a name="use-wildcards"></a>Używanie symboli wieloznacznych

Możesz również użyć symboli wieloznacznych w filtrach programu PowerShell, aby dopasować część nazwy. Załóżmy na przykład, że szukasz konta użytkownika. Pamiętaj tylko, że nazwisko użytkownika to *Anderson* , a może *Henderson* lub *Jorgenson*.

Możesz śledzić tego użytkownika w Centrum administracyjne platformy Microsoft 365 za pomocą narzędzia wyszukiwania i przeprowadzając trzy różne wyszukiwania:

- Jeden dla  *Andersona*

- Jeden dla  *Hendersona*

- Jeden dla  *Jorgensona*

Ponieważ wszystkie trzy z tych nazw kończą się ciągiem "son", można powiedzieć programowi PowerShell, aby wyświetlił wszystkich użytkowników, których nazwa kończy się ciągiem "son". Oto polecenie:

```powershell
Get-User -Filter '{LastName -like "*son"}'
```

Interpretacja tego polecenia programu PowerShell to: Pobierz wszystkich użytkowników w bieżącej subskrypcji Microsoft 365, ale użyj filtru, który wyświetla tylko listę użytkowników, których nazwiska kończą się ciągiem "son" (**-Filter {LastName -like "\*son"}).** Oznacza \* dowolny zestaw znaków, które są literami w nazwisku użytkownika.

## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>Program PowerShell dla Microsoft 365 ułatwia drukowanie lub zapisywanie danych

Centrum administracyjne platformy Microsoft 365 umożliwia wyświetlanie list danych. Oto przykład centrum administracyjnego usługi Skype dla firm Online z listą użytkowników, którzy zostali włączeni dla usługi Skype dla firm Online:

![Przykład centrum Administracja Skype dla firm Online z listą użytkowników, dla których włączono Skype dla firm Online.](../media/o365-powershell-lync-users.png)

Aby zapisać te informacje w pliku, należy wkleić je do dokumentu lub Microsoft Excel arkuszu. Każdy przypadek może wymagać dodatkowego formatowania. Ponadto Centrum administracyjne platformy Microsoft 365 nie umożliwia bezpośredniego drukowania wyświetlonej listy.

Na szczęście możesz użyć programu PowerShell, aby nie tylko wyświetlić listę, ale także zapisać ją w pliku, który można łatwo zaimportować do Excel. Oto przykładowe polecenie umożliwiające zapisanie danych użytkownika usługi Skype dla firm Online w pliku wartości rozdzielanych przecinkami (CSV), który można łatwo zaimportować jako tabelę w arkuszu Excel:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Oto przykład wyników:

![Przykład tabeli zaimportowanych do arkusza Excel dla Skype dla firm danych użytkownika usługi Online, które zostały zapisane w pliku wartości rozdzielanych przecinkami.](../media/o365-powershell-data-in-excel.png)

Interpretacja tego polecenia programu PowerShell: pobierz wszystkich użytkowników usługi Skype dla firm Online w bieżącej subskrypcji Microsoft 365 (**Get-CsOnlineUser**); uzyskaj tylko nazwę użytkownika, nazwę UPN i **lokalizację (wybierz pozycję DisplayName, UserPrincipalName, UsageLocation**), a następnie zapisz te informacje w pliku CSV o nazwie C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**).

Możesz również użyć opcji, aby zapisać tę listę jako plik XML lub stronę HTML. W rzeczywistości za pomocą dodatkowych poleceń programu PowerShell można zapisać go bezpośrednio jako plik Excel przy użyciu dowolnego niestandardowego formatowania.

Możesz również wysłać dane wyjściowe polecenia programu PowerShell, które wyświetla listę bezpośrednio do drukarki domyślnej w Windows. Oto przykładowe polecenie:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Oto jak będzie wyglądał drukowany dokument:

![Przykład drukowanego dokumentu, który był wynikiem polecenia programu PowerShell wysłanego bezpośrednio do drukarki domyślnej w Windows.](../media/o365-powershell-printed-data.png)

Interpretacja tego polecenia programu PowerShell jest następująca: Pobierz wszystkich użytkowników usługi Skype dla firm Online w bieżącej subskrypcji Microsoft 365; uzyskaj tylko nazwę użytkownika, nazwę UPN i lokalizację, a następnie wyślij te informacje do domyślnej drukarki Windows (**drukarki out-printer**).

Drukowany dokument ma takie samo proste formatowanie jak w oknie poleceń programu PowerShell. Aby uzyskać kopię na stałe, wystarczy dodać **| Out-Printer** na końcu polecenia.

## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>Program PowerShell dla Microsoft 365 umożliwia zarządzanie między produktami serwera

Składniki, które tworzą Microsoft 365, zostały zaprojektowane do współpracy. Załóżmy na przykład, że dodajesz nowego użytkownika do Microsoft 365 i określasz takie informacje jak dział użytkownika i numer telefonu. Te informacje będą następnie dostępne, jeśli uzyskasz dostęp do informacji użytkownika w dowolnej z usług Microsoft 365: Skype dla firm Online, Exchange lub SharePoint.

Ale to dla typowych informacji, które obejmują zestaw produktów. Informacje specyficzne dla produktu, takie jak informacje o Exchange skrzynce pocztowej użytkownika, zwykle nie są dostępne w całym pakiecie. Na przykład informacje o tym, czy skrzynka pocztowa użytkownika jest włączona, czy nie, są dostępne tylko w centrum administracyjnym Exchange.

Załóżmy, że chcesz utworzyć raport zawierający następujące informacje dla wszystkich użytkowników:

- Nazwa wyświetlana użytkownika

- Czy użytkownik ma licencję na Microsoft 365

- Czy skrzynka pocztowa Exchange użytkownika została włączona

- Czy użytkownik jest włączony dla usługi Skype dla firm Online

Nie można łatwo utworzyć takiego raportu w Centrum administracyjne platformy Microsoft 365. Zamiast tego należy utworzyć oddzielny dokument do przechowywania informacji, takich jak arkusz Excel. Następnie pobierz wszystkie nazwy użytkowników i informacje o licencjonowaniu z Centrum administracyjne platformy Microsoft 365, pobierz informacje o skrzynce pocztowej z <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange</a>, uzyskaj informacje Skype dla firm Online z usługi Skype dla firm Online Administracja w centrum, a następnie połącz te informacje.

Alternatywą jest użycie skryptu programu PowerShell do skompilowania raportu.

Poniższy przykładowy skrypt jest bardziej skomplikowany niż polecenia widoczne do tej pory w tym artykule. Pokazuje jednak potencjał używania programu PowerShell do tworzenia widoków informacji, które są trudne do uzyskania w przeciwnym razie. Oto skrypt do skompilowania i wyświetlenia potrzebnej listy:

```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

Oto przykład wyników:

```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

Interpretacja tego skryptu programu PowerShell to:

1. Pobierz wszystkich użytkowników w bieżącej subskrypcji Microsoft 365 i zapisz informacje w zmiennej o nazwie *$x* (**$x = Get-AzureADUser**).
1. Uruchom pętlę, która uruchamia wszystkich użytkowników w zmiennej $x (**foreach ($i w $x)**).
1. Zdefiniuj zmienną o nazwie *$y* i zapisz w niej informacje o skrzynce pocztowej użytkownika (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
1. Dodaj nową właściwość do informacji użytkownika o nazwie *IsMailBoxEnabled*. Ustaw wartość właściwości IsMailBoxEnabled skrzynki pocztowej użytkownika (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
1. Zdefiniuj zmienną o nazwie *$y* i zapisz w niej informacje Skype dla firm Online użytkownika (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
1. Dodaj nową właściwość do informacji użytkownika o nazwie *EnabledForSfB*. Ustaw ją na wartość właściwości Włączone informacji użytkownika Skype dla firm Online (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
1. Wyświetl listę użytkowników, ale podaj tylko ich nazwę, czy są licencjonowani, oraz dwie nowe właściwości wskazujące, czy ich skrzynka pocztowa jest włączona i czy są one włączone dla usługi Skype dla firm Online (**$x | Wybierz pozycje DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).

## <a name="see-also"></a>Zobacz też

[Wprowadzenie za pomocą programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Tworzenie raportów w Microsoft 365 przy użyciu Windows PowerShell](use-windows-powershell-to-create-reports-in-microsoft-365.md)
