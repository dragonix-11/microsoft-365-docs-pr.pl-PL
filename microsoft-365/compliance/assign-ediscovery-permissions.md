---
title: Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 5b9a067b-9d2e-4aa5-bb33-99d8c0d0b5d7
description: Przypisz uprawnienia wymagane do wykonywania zadań związanych z zbierania elektronicznych materiałów dowodowych przy użyciu Centrum zgodności platformy Microsoft 365.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 129363fe614bafef653fe65b39fa15d50a3b1c8a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033756"
---
# <a name="assign-ediscovery-permissions-in-the-microsoft-365-compliance-center"></a>Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365

Jeśli chcesz, aby inne osoby korzystały z [](ediscovery.md) jakichkolwiek narzędzi związanych z zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365, musisz im przypisać odpowiednie uprawnienia. Najłatwiej to zrobić przez dodanie odpowiedniej grupy ról na stronie Uprawnienia w Centrum zgodności. W tym temacie opisano uprawnienia wymagane do wykonywania zadań zbierania elektronicznych materiałów dowodowych.
  
Podstawowa grupa ról związanych z zbierania elektronicznych materiałów dowodowych w programie Centrum zgodności platformy Microsoft 365 nosi nazwę **Menedżer zbierania elektronicznych materiałów dowodowych**. W tej grupie ról występują dwie podgrupy.
  
- **Menedżer zbierania** elektronicznych materiałów dowodowych — Menedżer zbierania elektronicznych materiałów dowodowych może używać narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych do przeszukiwania lokalizacji zawartości w organizacji i wykonywać różne akcje związane z wyszukiwaniem, takie jak wyświetlanie podglądu i eksportowanie wyników wyszukiwania. Członkowie mogą również tworzyć sprawy i zarządzać nimi w podstawowych zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery, dodawać i usuwać członków do sprawy, tworzyć blokady sprawy, uruchamiać wyszukiwania skojarzone ze sprawą i uzyskać dostęp do danych sprawy. Menedżerowie zbierania elektronicznych materiałów dowodowych mogą tylko uzyskać dostęp do tworzyć sprawy i zarządzać nimi. Nie mogą oni uzyskać dostępu do spraw utworzonych przez innych menedżerów zbierania elektronicznych materiałów dowodowych ani zarządzać nimi.
  
- **Administrator** zbierania elektronicznych materiałów dowodowych — administrator zbierania elektronicznych materiałów dowodowych jest członkiem grupy ról Menedżera zbierania elektronicznych materiałów dowodowych i może wykonywać te same zadania związane z wyszukiwaniem zawartości i zarządzaniem sprawą, które może wykonywać Menedżer zbierania elektronicznych materiałów dowodowych. Ponadto administrator zbierania elektronicznych materiałów dowodowych może:
  
  - Dostęp do wszystkich spraw wymienionych **na stronach** podstawowych zbierania elektronicznych materiałów dowodowych **i** Advanced eDiscovery w Centrum zgodności platformy Microsoft 365.

  - Dostęp do danych Advanced eDiscovery przypadku dowolnej sprawy w organizacji.
  
  - Zarządzanie każdą sprawą zbierania elektronicznych materiałów dowodowych po dodaniu siebie jako członka do sprawy.
  
  - Usuwanie członków ze sprawy zbierania elektronicznych materiałów dowodowych. Tylko administrator zbierania elektronicznych materiałów dowodowych może usuwać członków ze sprawy. Użytkownicy, którzy są członkami podgrupy Menedżer zbierania elektronicznych materiałów dowodowych, nie mogą usuwać członków ze sprawy, nawet jeśli użytkownik utworzył sprawę.
  
  Aby dowiedzieć się, dlaczego warto mieć administratorów zbierania elektronicznych materiałów dowodowych w organizacji, zobacz [Więcej informacji](#more-information).

> [!NOTE]
> Aby można było analizować dane użytkownika przy użyciu Advanced eDiscovery, użytkownikowi (inicjując dane) musi zostać przypisana licencja usługi Office 365 E5 lub Microsoft 365 E5 administratora. Ewentualnie użytkownikom z licencją Office 365 E1 albo licencją programu Office 365 lub Microsoft 365 E3 można przypisać licencję na usługę Zgodność platformy Microsoft 365 E5 lub Microsoft 365 zbierania elektronicznych materiałów dowodowych i licencję na dodatek Inspekcja. Administratorzy, służby zgodności lub pracownicy prawni, którzy są przypisani do spraw jako członkowie i używają usługi Advanced eDiscovery do zbierania, wyświetlania i analizowania danych, nie potrzebują licencji usługi E5. Aby uzyskać więcej informacji na Advanced eDiscovery, zobacz [Subskrypcje i licencjonowanie w programie Advanced eDiscovery](overview-ediscovery-20.md#subscriptions-and-licensing).
  
## <a name="before-you-assign-permissions"></a>Zanim przypiszesz uprawnienia

- Musisz być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę Zarządzanie rolami, aby przypisać uprawnienia zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365.

- Możesz użyć polecenia cmdlet [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) w programie PowerShell centrum zabezpieczeń & zgodności, aby dodać grupę zabezpieczeń z obsługą poczty jako członka podgrupy Menedżerowie zbierania elektronicznych materiałów dowodowych w grupie ról Menedżer zbierania elektronicznych materiałów dowodowych. Do podgrupy Administratorzy zbierania elektronicznych materiałów dowodowych nie można jednak dodać grupy zabezpieczeń z obsługą poczty. Aby uzyskać szczegółowe informacje, zobacz [Więcej informacji](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych

1. Przejdź do tego <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się przy użyciu konta, które może przypisywać uprawnienia.
  
2. W okienku po lewej stronie wybierz pozycję **Uprawnienia**.

3. Na stronie **Uprawnienia & w** obszarze **Centrum zgodności** kliknij pozycję **Role**.

4. Na stronie **Role w Centrum zgodności** wybierz pozycję **Menedżer zbierania elektronicznych materiałów dowodowych**.
  
5. Na stronie **wysuwu Menedżera** zbierania elektronicznych materiałów dowodowych wykonaj jedną z następujących czynności na podstawie uprawnień zbierania elektronicznych materiałów dowodowych, które chcesz przypisać.
  
    **Aby uczynić użytkownika menedżerem zbierania elektronicznych materiałów dowodowych:** Obok **przycisku Menedżer zbierania elektronicznych materiałów dowodowych** wybierz pozycję **Edytuj**. Na stronie **kreatora Wybieranie menedżera zbierania elektronicznych materiałów** dowodowych kliknij pozycję ![Dodaj ikonę.](../media/ITPro-EAC-AddIcon.gif) **Dodaj**. Wybierz użytkownika (lub użytkowników), których chcesz dodać jako menedżera zbierania elektronicznych materiałów dowodowych, a następnie wybierz pozycję **Dodaj**. Po zakończeniu dodawania użytkowników wybierz pozycję **Gotowe**. Następnie na stronie kreatora **Wybieranie** zbierania elektronicznych materiałów dowodowych wybierz pozycję Zapisz,  aby zapisać zmiany członkostwa Menedżera zbierania elektronicznych materiałów dowodowych.
  
    **Aby uczynić użytkownika administratorem zbierania elektronicznych materiałów dowodowych:** Obok **przycisku Administrator zbierania elektronicznych materiałów dowodowych** wybierz pozycję **Edytuj**. Na stronie **Wybieranie administratora zbierania elektronicznych materiałów dowodowych** kliknij pozycję ![Dodaj ikonę.](../media/ITPro-EAC-AddIcon.gif) **Dodaj**. Wybierz użytkownika (lub użytkowników), którego chcesz dodać jako administratora **zbierania elektronicznych materiałów dowodowych**, a następnie wybierz pozycję  **Dodaj**. Po zakończeniu dodawania użytkowników wybierz pozycję **Gotowe**. Następnie na stronie **Kreatora wybierania edycji** zbierania elektronicznych materiałów dowodowych wybierz pozycję  Zapisz, aby zapisać zmiany w członkostwie administratora zbierania elektronicznych materiałów dowodowych.
  
> [!NOTE]
> Możesz również użyć polecenia cmdlet **Add-eDiscoveryCaseAdmin** , aby uczynić użytkownika administratorem zbierania elektronicznych materiałów dowodowych. Jednak aby można było użyć tego polecenia cmdlet, użytkownik musi mieć przypisaną rolę Zarządzanie sprawami. Aby uzyskać więcej informacji, [zobacz Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin). 
  
Na stronie **Uprawnienia** w Centrum zgodności platformy Microsoft 365 możesz także przypisywać użytkownikom uprawnienia związane z zbierania elektronicznych materiałów dowodowych, dodając ich do grup ról Administrator zgodności, Zarządzanie organizacją i Recenzent. Aby uzyskać opis ról RBAC związanych z zbierania elektronicznych materiałów dowodowych przypisanych do każdej z tych grup ról, zobacz Role [RBAC dotyczące zbierania elektronicznych materiałów dowodowych](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>Role RBAC związane z zbierania elektronicznych materiałów dowodowych

W poniższej tabeli wymieniono role RBAC powiązane z zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365 oraz wbudowane grupy ról, do których są domyślnie przypisane poszczególne role.
  
| Rola | Administrator zgodności | Menedżer zbierania elektronicznych materiałów dowodowych & administratorem | Zarządzanie organizacją | Recenzent |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Zarządzanie sprawą <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> |
|Komunikacja <br/> | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Wyszukiwanie zgodności <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> |
|Szybki <br/> | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Eksportowanie <br/> | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Wstrzymaj <br/>  |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> |
|Wersja zapoznawcza <br/>  | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Recenzja <br/>  | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> |![Znacznik wyboru](../media/checkmark.png) <br/> |
|Odszyfrowywanie usługi RMS <br/>  ||![Znacznik wyboru](../media/checkmark.png) <br/> |||
|Wyszukiwanie i przeczyszczanie <br/> | <br/> | <br/> |![Znacznik wyboru](../media/checkmark.png)           <br/> | <br/> |
||||
  
W poniższych sekcjach opisano wszystkie role RBAC związane z zbierania elektronicznych materiałów dowodowych wymienione w poprzedniej tabeli.

### <a name="case-management"></a>Zarządzanie sprawą

Ta rola umożliwia użytkownikom tworzenie, edytowanie, usuwanie i kontrolowanie dostępu do podstawowych zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery spraw Centrum zgodności platformy Microsoft 365. Jak wyjaśniono wcześniej, użytkownik musi mieć przypisaną rolę zarządzania sprawami, aby można było użyć polecenia cmdlet **Add-eDiscoveryCaseAdmin** w celu nadawania mu uprawnień administratora zbierania elektronicznych materiałów dowodowych.

Więcej informacji można znaleźć w następujących artykułach:

- [Wprowadzenie do zbierania elektronicznych materiałów dowodowych w podstawowym programie](get-started-core-ediscovery.md)

- [Wprowadzenie do Advanced eDiscovery](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Komunikacja

Ta rola umożliwia użytkownikom zarządzanie całą komunikacją z użytkownikami- elementami przechowawczymi wskazanymi w Advanced eDiscovery przypadku. Obejmuje to tworzenie powiadomień o wstrzymaniu, przypomnień o wstrzymaniu i eskalacji do zarządzania. Użytkownik może również śledzić potwierdzenia przechowywania powiadomień wstrzymywania i zarządzać dostępem do portalu do obsługi wiadów używanego przez każdego opiekuna do śledzenia komunikacji w przypadkach, gdy zostali zidentyfikowani jako opiekunzy.

Aby uzyskać więcej informacji, zobacz [Praca z komunikacją w programie Advanced eDiscovery](managing-custodian-communications.md).

### <a name="compliance-search"></a>Wyszukiwanie zgodności

Ta rola umożliwia użytkownikom uruchamianie narzędzia Przeszukiwanie zawartości w programie Centrum zgodności platformy Microsoft 365 w celu przeszukiwania skrzynek pocztowych i folderów publicznych, SharePoint witryn online, OneDrive dla Firm witryn i Skype dla firm konwersacji. Microsoft 365 grupy, grupy Microsoft Teams i Yammer grupy. Ta rola umożliwia użytkownikowi oszacowanie wyników wyszukiwania i tworzenie raportów eksportu, ale inne role są niezbędne do inicjowania akcji wyszukiwania zawartości, takich jak wyświetlanie podglądu, eksportowanie lub usuwanie wyników wyszukiwania.

W przypadku funkcji Przeszukiwanie zawartości i Podstawowe zbierania elektronicznych materiałów dowodowych użytkownicy z przypisaną rolą Wyszukiwanie zgodności, ale bez roli Podgląd, mogą wyświetlać podgląd wyników wyszukiwania, w którym akcja podglądu została zainicjowana przez użytkownika z przypisaną rolą Podgląd. Użytkownik bez roli Podgląd może wyświetlać podgląd wyników przez maksymalnie dwa tygodnie od utworzenia początkowej akcji podglądu.

Podobnie użytkownicy w przeszukiwaniu zawartości i podstawowym zbierania elektronicznych materiałów dowodowych, którzy mają przypisaną rolę Wyszukiwanie zgodności, ale nie mają roli Eksportowanie, mogą pobierać wyniki wyszukiwania, w którym akcja eksportowania została zainicjowana przez użytkownika z przypisaną rolą Eksportowanie. Użytkownik bez roli eksportowania może pobrać wyniki wyszukiwania z maksymalnie dwóch tygodni po utworzeniu początkowej akcji eksportowania. Następnie nie może pobrać wyników, chyba że ktoś z rolą eksportowania ponownie uruchomi eksport.

Dwutygodniowy okres prolongaty na potrzeby wyświetlania podglądu i eksportowania wyników wyszukiwania (bez odpowiednich ról wyszukiwania i eksportu) nie ma zastosowania do Advanced eDiscovery. Aby można było wyświetlać podgląd i eksportować zawartość w aplikacji, należy przypisać do użytkowników role podglądu i eksportu Advanced eDiscovery.

### <a name="custodian"></a>Szybki

Ta rola pozwala użytkownikom identyfikować urządzenia do spraw Advanced eDiscovery i zarządzać nimi, a także korzystać z informacji  z Azure Active Directory i innych źródeł w celu znalezienia źródeł danych skojarzonych z nimi. Użytkownik może skojarzyć inne źródła danych, takie jak skrzynki pocztowe, witryny SharePoint i Teams z odbiorcami w przypadku sprawy. Użytkownik może także umieścić w prawnych źródłach danych skojarzonych z przechowywaniami, aby zachować zawartość w kontekście sprawy.

Aby uzyskać więcej informacji, zobacz [Praca z opiekunami w Advanced eDiscovery](managing-custodians.md).

### <a name="export"></a>Eksportowanie

Ta rola umożliwia użytkownikom eksportowanie wyników przeszukiwania zawartości na komputer lokalny. Pozwala także przygotować wyniki wyszukiwania do analizy w programie Advanced eDiscovery.

Aby uzyskać więcej informacji na temat eksportowania wyników wyszukiwania, zobacz [Eksportowanie wyników wyszukiwania z Centrum zgodności platformy Microsoft 365](export-search-results.md).

### <a name="hold"></a>Wstrzymaj

Ta rola pozwala użytkownikom umieszczać zawartość w hold w skrzynkach pocztowych, folderach publicznych, witrynach, Skype dla firm konwersacjach i Microsoft 365 grupach. Po wstrzymaniu zawartości właściciele zawartości nadal mogą modyfikować lub usuwać oryginalną zawartość, ale zawartość jest zachowywana do momentu usunięcia lub wygaśnięcia czasu trwania zawieszonego przechowywania.

Aby uzyskać więcej informacji na temat blokady, zobacz:

- [Tworzenie zbierania elektronicznych materiałów dowodowych w celu utworzenia wstrzymywania](create-ediscovery-holds.md) 

- [Tworzenie wstrzymywania w Advanced eDiscovery](add-custodians-to-case.md)

### <a name="preview"></a>Wersja zapoznawcza

Ta rola umożliwia użytkownikom wyświetlanie listy elementów zwróconych z przeszukiwania zawartości. Mogą także otwierać i wyświetlać poszczególne element listy w celu wyświetlenia jego zawartości.

### <a name="review"></a>Recenzja

Ta rola umożliwia użytkownikom dostęp do zestawów [recenzji w Advanced eDiscovery](overview-ediscovery-20.md). Użytkownicy przypisani do tej roli mogą widzieć i otwierać listę spraw na stronie Zaawansowane zbierania elektronicznych materiałów dowodowych **>** w Centrum zgodności platformy Microsoft 365 których są członkami. Gdy użytkownik uzyskuje dostęp do sprawy Advanced eDiscovery, może wybrać pozycję **Przejrzyj zestawy**, aby uzyskać dostęp do danych dotyczących sprawy. Ta rola nie umożliwia użytkownikowi wyświetlania podglądu wyników przeszukiwania kolekcji skojarzonego ze sprawą ani wykonywania innych zadań związanych z wyszukiwaniem lub zarządzaniem sprawą. Użytkownicy z tą rolą mogą uzyskać dostęp do danych tylko w zestawie recenzji.

### <a name="rms-decrypt"></a>Odszyfrowywanie usługi RMS

Ta rola umożliwia użytkownikom wyświetlanie wiadomości e-mail chronionych prawami podczas wyświetlania podglądu wyników wyszukiwania oraz eksportowanie odszyfrowanych wiadomości e-mail chronionych prawami. Ta rola umożliwia również użytkownikom wyświetlanie (i eksportowanie) pliku zaszyfrowanego za pomocą technologii szyfrowania [firmy Microsoft](encryption.md) , gdy zaszyfrowany plik zostanie dołączony do wiadomości e-mail dołączonej do wyników wyszukiwania zbierania elektronicznych materiałów dowodowych. Ponadto ta rola umożliwia użytkownikom przeglądanie zaszyfrowanych załączników wiadomości e-mail i tworzenie zapytań, które są dodawane do zestawu recenzji w aplikacji Advanced eDiscovery. Aby uzyskać więcej informacji na temat odszyfrowywania przy użyciu zbierania elektronicznych materiałów dowodowych, zobacz Odszyfrowywanie w Microsoft 365 [zbierania elektronicznych materiałów dowodowych](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Wyszukiwanie i przeczyszczanie

Ta rola umożliwia użytkownikom zbiorcze usuwanie danych spełniających kryteria wyszukiwania zawartości. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i usuwanie wiadomości e-mail w organizacji](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>Dodawanie grup ról jako członków spraw zbierania elektronicznych materiałów dowodowych

Grupy ról można dodawać jako członków podstawowych zbierania elektronicznych materiałów dowodowych i w Advanced eDiscovery, dzięki czemu członkowie grup ról mogą uzyskać dostęp do przydzielonych spraw i wykonywać zadania. Role przypisane do grupy ról określają, co mogą robić członkowie grupy ról. Następnie dodanie grupy ról jako członka sprawy umożliwia członkom uzyskiwanie dostępu do tych zadań i wykonywanie ich w określonym przypadku. Aby uzyskać więcej informacji na temat dodawania grup ról jako członków spraw, zobacz:

- [Wprowadzenie do zbierania elektronicznych materiałów dowodowych w podstawowym programie](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-core-ediscovery-case)

- [Dodawanie lub usuwanie członków w przypadku Advanced eDiscovery sprawy](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

W związku z tym należy pamiętać, że jeśli rola zostanie dodana lub usunięta z grupy ról, ta grupa ról zostanie automatycznie usunięta jako członek dowolnej sprawy, do których należy grupa ról. Przyczyną tego jest ochrona organizacji przed nieumyślnie udostępnieniem dodatkowych uprawnień członkom sprawy. Podobnie, jeśli grupa ról zostanie usunięta, zostanie usunięta ze wszystkich spraw, do których była członkiem.

Przed dodaniem lub usunięciem ról do grupy ról, która może być członkiem sprawy zbierania elektronicznych materiałów dowodowych, można uruchomić następujące polecenia w programie [PowerShell zabezpieczeń &](/powershell/exchange/connect-to-scc-powershell) zgodności, aby uzyskać listę spraw, do których należy grupa ról. Po zaktualizowaniu grupy ról można ją z powrotem dodać jako członka takich spraw.

### <a name="get-a-list-of-core-ediscovery-cases-a-role-group-is-assigned-to"></a>Uzyskiwanie listy podstawowych spraw zbierania elektronicznych materiałów dowodowych, do których przypisano grupę ról

```powershell
Get-ComplianceCase -RoleGroup "Name of role group"
```

### <a name="get-a-list-of-advanced-ediscovery-cases-a-role-group-is-assigned-to"></a>Uzyskiwanie listy spraw Advanced eDiscovery do których przypisano grupę ról

```powershell
Get-ComplianceCase -RoleGroup "Name of role group" -CaseType AdvancedEdiscovery
```

## <a name="more-information"></a>Więcej informacji

- **Dlaczego warto utworzyć administratora zbierania elektronicznych materiałów dowodowych?** Jak wyjaśniono wcześniej, administrator zbierania elektronicznych materiałów dowodowych jest członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych, która może wyświetlać wszystkie sprawy zbierania elektronicznych materiałów dowodowych i uzyskać do nich dostęp w organizacji. Ta możliwość uzyskiwania dostępu do wszystkich spraw zbierania elektronicznych materiałów dowodowych ma dwa ważne cele:

  - Jeśli osoba, która jest jedynym członkiem sprawy zbierania elektronicznych materiałów dowodowych, odejdzie z organizacji, nikt (w tym członkowie grupy ról Zarządzanie organizacją lub inny członek grupy ról Menedżer zbierania elektronicznych materiałów dowodowych) nie będzie miał dostępu do tej sprawy zbierania elektronicznych materiałów dowodowych, ponieważ nie jest jej członkiem. W takiej sytuacji nie będzie możliwości uzyskania dostępu do danych w takim przypadku. Jednak ponieważ administrator zbierania elektronicznych materiałów dowodowych może uzyskać dostęp do wszystkich spraw zbierania elektronicznych materiałów dowodowych w organizacji, może wyświetlić sprawę i dodać siebie lub innego menedżera zbierania elektronicznych materiałów dowodowych jako członka tej sprawy.

  - Ze względu na to, że administrator zbierania elektronicznych materiałów dowodowych może wyświetlać wszystkie podstawowe sprawy zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery zbierania elektronicznych materiałów dowodowych i nadzorować wszystkie sprawy i skojarzone z nimi wyszukiwania zgodności. Może to pomóc w zapobieganiu wszelkim błędom podczas przeszukiwania zgodności lub spraw zbierania elektronicznych materiałów dowodowych. A ponieważ administratorzy zbierania elektronicznych materiałów dowodowych mogą uzyskać dostęp do potencjalnie poufnych informacji w wynikach wyszukiwania zgodności, należy ograniczyć liczbę osób, które są administratorami zbierania elektronicznych materiałów dowodowych.

- **Czy mogę dodać grupę jako członka grupy ról Menedżer zbierania elektronicznych materiałów dowodowych?** Jak wyjaśniono wcześniej, możesz dodać grupę zabezpieczeń z obsługą poczty jako członka podgrupy Menedżerowie zbierania elektronicznych materiałów dowodowych w grupie ról Menedżer zbierania elektronicznych materiałów dowodowych, używając polecenia cmdlet **Add-RoleGroupMember** w programie PowerShell centrum zabezpieczeń & zgodności. Możesz na przykład uruchomić następujące polecenie, aby dodać grupę zabezpieczeń z obsługą poczty do grupy ról Menedżer zbierania elektronicznych materiałów dowodowych. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange i grupy Microsoft 365 nie są obsługiwane. Należy użyć grupy zabezpieczeń z obsługą poczty, którą można utworzyć w programie Exchange Online PowerShell, uruchamiając program `New-DistributionGroup -Type Security`. Możesz również utworzyć grupę zabezpieczeń z obsługą poczty (i dodać członków) w centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange lub</a> na [stronie centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339). Może upłynieć do 60 minut od utworzenia grupy zabezpieczeń z włączoną obsługą poczty w celu dodania jej do grupy ról Menedżerowie zbierania elektronicznych materiałów dowodowych.

    Jak wspomniano wcześniej, administrator zbierania elektronicznych materiałów dowodowych nie może być grupą zabezpieczeń z obsługą poczty przy użyciu polecenia cmdlet **Add-eDiscoveryCaseAdmin** w programie PowerShell w centrum zabezpieczeń & zgodności. Jako administratorów zbierania elektronicznych materiałów dowodowych możesz dodawać tylko pojedynczych użytkowników.

    Nie można też dodać grupy zabezpieczeń z obsługą poczty jako członka sprawy.
