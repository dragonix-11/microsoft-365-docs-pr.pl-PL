---
title: Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Przypisz uprawnienia wymagane do wykonywania zadań związanych zbierania elektronicznych materiałów dowodowych przy użyciu portalu zgodności usługi Microsoft Purview.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: e764aae4313a8e5d4dfc402e4c1f87eb8c1a5bbb
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090522"
---
# <a name="assign-ediscovery-permissions-in-the-compliance-portal"></a>Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w portalu zgodności

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Jeśli chcesz, aby użytkownicy korzystali z dowolnego [narzędzia związanego zbierania elektronicznych materiałów dowodowych](ediscovery.md) w portalu zgodności usługi Microsoft Purview, musisz przypisać im odpowiednie uprawnienia. Najprostszym sposobem na to jest dodanie odpowiedniej grupy ról na stronie **Uprawnienia** w Centrum zgodności. W tym temacie opisano uprawnienia wymagane do wykonywania zadań zbierania elektronicznych materiałów dowodowych.
  
Podstawowa grupa ról związana zbierania elektronicznych materiałów dowodowych w portalu zgodności nosi nazwę **eDiscovery Manager**. W tej grupie ról znajdują się dwie podgrupy.
  
- **eDiscovery Manager** — menedżer zbierania elektronicznych materiałów dowodowych może używać narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych do wyszukiwania lokalizacji zawartości w organizacji i wykonywania różnych akcji związanych z wyszukiwaniem, takich jak podgląd i eksport wyników wyszukiwania. Członkowie mogą również tworzyć przypadki i zarządzać nimi w usługach Microsoft Purview eDiscovery (Standard) i Microsoft Purview eDiscovery (Premium), dodawać i usuwać członków do sprawy, tworzyć blokady spraw, uruchamiać wyszukiwania skojarzone ze sprawą i uzyskiwać dostęp do danych przypadków. Menedżerowie zbierania elektronicznych materiałów dowodowych mogą uzyskiwać dostęp tylko do utworzonych przypadków i zarządzać nimi. Nie mogą uzyskiwać dostępu do spraw utworzonych przez innych menedżerów zbierania elektronicznych materiałów dowodowych ani zarządzać nimi.
  
- **Administrator zbierania** elektronicznych materiałów dowodowych — administrator zbierania elektronicznych materiałów dowodowych jest członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych i może wykonywać te same zadania związane z wyszukiwaniem zawartości i zarządzaniem sprawami, które może wykonywać menedżer zbierania elektronicznych materiałów dowodowych. Ponadto administrator zbierania elektronicznych materiałów dowodowych może:
  
  - Uzyskaj dostęp do wszystkich przypadków wymienionych na stronach **eDiscovery (Standard)** i **eDiscovery (Premium)** w portalu zgodności.

  - Dane przypadków dostępu zbierania elektronicznych materiałów dowodowych (Premium) w dowolnym przypadku w organizacji.
  
  - Zarządzaj dowolnym przypadkiem zbierania elektronicznych materiałów dowodowych po dodaniu się jako członek sprawy.
  
  - Usuń elementy członkowskie ze sprawy zbierania elektronicznych materiałów dowodowych. Tylko administrator zbierania elektronicznych materiałów dowodowych może usunąć członków ze sprawy. Użytkownicy, którzy są członkami podgrupy Menedżera zbierania elektronicznych materiałów dowodowych, nie mogą usuwać członków ze sprawy, nawet jeśli użytkownik utworzył przypadek.
  
  Aby uzyskać więcej informacji, zobacz [Więcej informacji](#more-information) z powodów, dla których mogą być potrzebne administratorzy zbierania elektronicznych materiałów dowodowych w organizacji.

> [!NOTE]
> Aby analizować dane użytkownika przy użyciu eDiscovery (Premium), użytkownik (opiekun danych) musi mieć przypisaną licencję Office 365 E5 lub Microsoft 365 E5. Alternatywnie użytkownicy z licencją Office 365 E1 lub licencją Office 365 lub Microsoft 365 E3 mogą mieć przypisaną licencję dodatku Zgodność platformy Microsoft 365 E5 lub Microsoft 365 zbierania elektronicznych materiałów dowodowych i inspekcji. Administratorzy, urzędnicy ds. zgodności lub pracownicy prawni, którzy są przypisani do spraw jako członkowie i używają eDiscovery (Premium) do zbierania, wyświetlania i analizowania danych, nie potrzebują licencji E5. Aby uzyskać więcej informacji na temat licencjonowania zbierania elektronicznych materiałów dowodowych (Premium), zobacz [Subskrypcje i licencjonowanie w usłudze eDiscovery (Premium)](overview-ediscovery-20.md#subscriptions-and-licensing).
  
## <a name="before-you-assign-permissions"></a>Przed przypisaniem uprawnień

- Musisz być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę Zarządzanie rolami, aby przypisać uprawnienia zbierania elektronicznych materiałów dowodowych w portalu zgodności.

- Aby dodać grupę zabezpieczeń z obsługą poczty eDiscovery Manager, możesz użyć polecenia cmdlet [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) w programie PowerShell Security & Compliance Center. Nie można jednak dodać grupy zabezpieczeń z obsługą poczty do podgrupy Administratorzy zbierania elektronicznych materiałów dowodowych. Aby uzyskać szczegółowe informacje, zobacz [Więcej informacji](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>Przypisz uprawnienia zbierania elektronicznych materiałów dowodowych

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności</a> i zaloguj się przy użyciu konta, które może przypisywać uprawnienia.
  
2. W okienku po lewej stronie wybierz pozycję **Uprawnienia**.

3. Na stronie **Uprawnienia & role** w **obszarze Centrum zgodności** kliknij pozycję **Role**.

4. Na stronie **Role Centrum zgodności** wybierz pozycję **Menedżer zbierania elektronicznych materiałów dowodowych**.
  
5. Na stronie wysuwanego **Menedżera zbierania** elektronicznych materiałów dowodowych wykonaj jedną z następujących czynności na podstawie uprawnień zbierania elektronicznych materiałów dowodowych, które chcesz przypisać.
  
    **Aby uczynić użytkownika menedżerem zbierania elektronicznych materiałów dowodowych:** Obok pozycji **Menedżer zbierania elektronicznych materiałów dowodowych** wybierz pozycję **Edytuj**. Na stronie **Kreator wybierania menedżera zbierania elektronicznych materiałów dowodowych** kliknij pozycję Dodaj ikonę ![.](../media/ITPro-EAC-AddIcon.gif) **Dodaj**. Wybierz użytkownika (lub użytkowników), który chcesz dodać jako menedżera zbierania elektronicznych materiałów dowodowych, a następnie wybierz pozycję **Dodaj**. Po zakończeniu dodawania użytkowników wybierz pozycję **Gotowe**. Następnie na stronie Kreator **edytowania wybierz menedżera zbierania elektronicznych** materiałów dowodowych wybierz pozycję **Zapisz** , aby zapisać zmiany w członkostwie w menedżerze zbierania elektronicznych materiałów dowodowych.
  
    **Aby użytkownik był administratorem zbierania elektronicznych materiałów dowodowych:** Obok pozycji **Administrator zbierania elektronicznych materiałów dowodowych** wybierz pozycję **Edytuj**. Na stronie **Wybieranie administratora zbierania elektronicznych materiałów dowodowych** kliknij pozycję Dodaj ikonę ![.](../media/ITPro-EAC-AddIcon.gif) **Dodaj**. Wybierz użytkownika (lub użytkowników), który chcesz dodać jako **administratora zbierania elektronicznych materiałów dowodowych**, a następnie  **dodaj**. Po zakończeniu dodawania użytkowników wybierz pozycję **Gotowe**. Następnie na stronie Kreator **edytowania wybierz administratora zbierania elektronicznych** materiałów dowodowych wybierz pozycję **Zapisz** , aby zapisać zmiany w członkostwie administratora zbierania elektronicznych materiałów dowodowych.
  
> [!NOTE]
> Możesz również użyć polecenia cmdlet **Add-eDiscoveryCaseAdmin** , aby uczynić użytkownika administratorem zbierania elektronicznych materiałów dowodowych. Jednak użytkownik musi mieć przypisaną rolę Zarządzanie przypadkami, zanim będzie można użyć tego polecenia cmdlet, aby uczynić go administratorem zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin).
  
Na stronie **Uprawnienia** w portalu zgodności można również przypisać użytkownikom uprawnienia związane zbierania elektronicznych materiałów dowodowych, dodając je do grup ról Administrator zgodności, Zarządzanie organizacją i Recenzent. Aby zapoznać się z opisem ról RBAC związanych zbierania elektronicznych materiałów dowodowych przypisanych do każdej z tych grup ról, zobacz [Role RBAC związane zbierania elektronicznych materiałów dowodowych](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>Role RBAC związane zbierania elektronicznych materiałów dowodowych

Poniższa tabela zawiera listę ról RBAC związanych zbierania elektronicznych materiałów dowodowych w portalu zgodności i wskazuje wbudowane grupy ról, do których domyślnie przypisano każdą rolę.
  
| Rola | Administrator zgodności | eDiscovery Manager & Administrator | Zarządzanie organizacją | Recenzent |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Zarządzanie przypadkami <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> |
|Komunikacja <br/> | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Wyszukiwanie zgodności <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> |
|Opiekun <br/> | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Eksportowanie <br/> | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Przytrzymaj <br/>  |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> |
|Wersja zapoznawcza <br/>  | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Przegląd <br/>  | <br/> |![Znacznik wyboru.](../media/checkmark.png) <br/> | <br/> |![Znacznik wyboru](../media/checkmark.png) <br/> |
|Odszyfrowywanie usługi RMS <br/>  ||![Znacznik wyboru](../media/checkmark.png) <br/> |||
|Wyszukiwanie i przeczyszczanie <br/> | <br/> | <br/> |![Znacznik wyboru](../media/checkmark.png)<br/> | <br/> |
||||||
  
W poniższych sekcjach opisano każdą z ról RBAC związanych zbierania elektronicznych materiałów dowodowych wymienionych w poprzedniej tabeli.

### <a name="case-management"></a>Zarządzanie przypadkami

Ta rola umożliwia użytkownikom tworzenie, edytowanie, usuwanie i kontrolowanie dostępu do przypadków zbierania elektronicznych materiałów dowodowych (Standard) i eDiscovery (Premium) w portalu zgodności. Jak wyjaśniono wcześniej, użytkownikowi należy przypisać rolę Zarządzanie przypadkami, aby można było użyć polecenia cmdlet **Add-eDiscoveryCaseAdmin** , aby uczynić go administratorem zbierania elektronicznych materiałów dowodowych.

Więcej informacji można znaleźć w następujących artykułach:

- [Zacznij od zbierania elektronicznych materiałów dowodowych (wersja standardowa)](get-started-core-ediscovery.md)

- [Wprowadzenie zbierania elektronicznych materiałów dowodowych (Premium)](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Komunikacja

Ta rola umożliwia użytkownikom zarządzanie całą komunikacją z opiekunami zidentyfikowanymi w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Obejmuje to tworzenie powiadomień o blokadzie, przypomnienia o blokadzie i eskalacje do zarządzania. Użytkownik może również śledzić potwierdzenie blokady powiadomień i zarządzać dostępem do portalu opiekuna, który jest używany przez każdego opiekuna do śledzenia komunikacji w przypadkach, w których zostały zidentyfikowane jako opiekun.

Aby uzyskać więcej informacji, zobacz [Praca z komunikacją w usłudze eDiscovery (Premium)](managing-custodian-communications.md).

### <a name="compliance-search"></a>Wyszukiwanie zgodności

Ta rola umożliwia użytkownikom uruchamianie narzędzia do wyszukiwania zawartości w portalu zgodności w celu wyszukiwania skrzynek pocztowych i folderów publicznych, witryn SharePoint Online, witryn OneDrive dla Firm, konwersacji Skype dla firm, grup Microsoft 365 i Microsoft Teams oraz Yammer grup. Ta rola umożliwia użytkownikowi uzyskanie oszacowania wyników wyszukiwania i utworzenie raportów eksportu, ale inne role są potrzebne do zainicjowania akcji wyszukiwania zawartości, takich jak podgląd, eksportowanie lub usuwanie wyników wyszukiwania.

W obszarze Wyszukiwanie zawartości i eDiscovery (Standard) użytkownicy, którym przypisano rolę wyszukiwania zgodności, ale nie mają roli Podgląd, mogą wyświetlić podgląd wyników wyszukiwania, w którym akcja w wersji zapoznawczej została zainicjowana przez użytkownika, któremu przypisano rolę podglądu. Użytkownik bez roli podglądu może wyświetlać podgląd wyników przez maksymalnie dwa tygodnie po utworzeniu początkowej akcji w wersji zapoznawczej.

Podobnie użytkownicy wyszukiwania zawartości i eDiscovery (Standardowa), którym przypisano rolę Wyszukiwania zgodności, ale nie mają roli Eksportuj, mogą pobrać wyniki wyszukiwania, w którym akcja eksportu została zainicjowana przez użytkownika, któremu przypisano rolę Eksportuj. Użytkownik bez roli Eksportuj może pobrać wyniki wyszukiwania przez maksymalnie dwa tygodnie po utworzeniu początkowej akcji eksportu. Następnie nie mogą pobrać wyników, chyba że ktoś z rolą Eksportuj ponownie uruchomi eksport.

Dwutygodniowy okres prolongaty na potrzeby podglądu i eksportowania wyników wyszukiwania (bez odpowiednich ról wyszukiwania i eksportu) nie ma zastosowania do zbierania elektronicznych materiałów dowodowych (Premium). Użytkownikom należy przypisać role podglądu i eksportu, aby wyświetlać podgląd i eksportować zawartość zbierania elektronicznych materiałów dowodowych (Premium).

### <a name="custodian"></a>Opiekun

Ta rola umożliwia użytkownikom identyfikowanie opiekunów w sprawach zbierania elektronicznych materiałów dowodowych (Premium) i zarządzanie nimi oraz korzystanie z informacji z Azure Active Directory i innych źródeł w celu znalezienia źródeł danych skojarzonych z opiekunami. Użytkownik może skojarzyć inne źródła danych, takie jak skrzynki pocztowe, witryny SharePoint i Teams z opiekunami w danym przypadku. Użytkownik może również wstrzymać prawne źródła danych skojarzone z opiekunami, aby zachować zawartość w kontekście sprawy.

Aby uzyskać więcej informacji, zobacz [Praca z opiekunami w zakresie zbierania elektronicznych materiałów dowodowych (Premium)](managing-custodians.md).

### <a name="export"></a>Eksportowanie

Rola umożliwia użytkownikom eksportowanie wyników wyszukiwania zawartości na komputer lokalny. Umożliwia również przygotowanie wyników wyszukiwania do analizy w obszarze zbierania elektronicznych materiałów dowodowych (Premium).

Aby uzyskać więcej informacji na temat eksportowania wyników wyszukiwania, zobacz [Eksportowanie wyników wyszukiwania z portalu zgodności usługi Microsoft Purview](export-search-results.md).

### <a name="hold"></a>Przytrzymaj

Ta rola umożliwia użytkownikom umieszczanie zawartości w skrzynkach pocztowych, folderach publicznych, witrynach, Skype dla firm konwersacjach i grupach Microsoft 365. Gdy zawartość jest wstrzymana, właściciele zawartości mogą nadal modyfikować lub usuwać oryginalną zawartość, ale zawartość zostanie zachowana do momentu usunięcia blokady lub do czasu wygaśnięcia czasu przechowywania.

Aby uzyskać więcej informacji na temat blokad, zobacz:

- [Tworzenie blokady w usłudze eDiscovery (Standard)](create-ediscovery-holds.md) 

- [Tworzenie blokady w usłudze eDiscovery (Premium)](add-custodians-to-case.md)

### <a name="preview"></a>Wersja zapoznawcza

Ta rola umożliwia użytkownikom wyświetlanie listy elementów zwróconych z wyszukiwania zawartości. Mogą również otwierać i wyświetlać każdy element z listy, aby wyświetlić jego zawartość.

### <a name="review"></a>Przegląd

Ta rola umożliwia użytkownikom dostęp do zestawów przeglądów w [usłudze eDiscovery (Premium)](overview-ediscovery-20.md). Użytkownicy, którym przypisano tę rolę, mogą wyświetlać i otwierać listę przypadków na stronie **eDiscovery > Advanced** w portalu zgodności, do których należą. Gdy użytkownik uzyskuje dostęp do sprawy zbierania elektronicznych materiałów dowodowych (Premium), może wybrać pozycję **Zestawy przeglądów**, aby uzyskać dostęp do danych przypadków. Ta rola nie zezwala użytkownikowi na wyświetlanie podglądu wyników wyszukiwania kolekcji skojarzonego ze sprawą ani wykonywanie innych zadań wyszukiwania lub zarządzania sprawami. Użytkownicy z tą rolą mogą uzyskiwać dostęp tylko do danych w zestawie przeglądów.

### <a name="rms-decrypt"></a>Odszyfrowywanie usługi RMS

Ta rola umożliwia użytkownikom wyświetlanie wiadomości e-mail chronionych prawami podczas podglądu wyników wyszukiwania i eksportowania odszyfrowanych wiadomości e-mail chronionych prawami. Ta rola umożliwia również użytkownikom wyświetlanie (i eksportowanie) pliku zaszyfrowanego za pomocą [technologii szyfrowania firmy Microsoft](encryption.md) , gdy zaszyfrowany plik jest dołączony do wiadomości e-mail dołączonej do wyników wyszukiwania zbierania elektronicznych materiałów dowodowych. Ponadto ta rola umożliwia użytkownikom przeglądanie zaszyfrowanych załączników wiadomości e-mail i wykonywanie zapytań o nie, które są dodawane do zestawu przeglądów w usłudze eDiscovery (Premium). Aby uzyskać więcej informacji na temat odszyfrowywania w usłudze eDiscovery, zobacz [Odszyfrowywanie w narzędziach do zbierania elektronicznych materiałów dowodowych Microsoft 365](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Wyszukiwanie i przeczyszczanie

Ta rola umożliwia użytkownikom zbiorcze usuwanie danych zgodnych z kryteriami wyszukiwania zawartości. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i usuwanie wiadomości e-mail w organizacji](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>Dodawanie grup ról jako członków spraw zbierania elektronicznych materiałów dowodowych

Grupy ról można dodawać jako członków przypadków zbierania elektronicznych materiałów dowodowych (standard) i eDiscovery (Premium), aby członkowie grup ról mogli uzyskiwać dostęp do zadań i wykonywać je w przypisanych przypadkach. Role przypisane do grupy ról definiują, co mogą robić członkowie grupy ról. Następnie dodanie grupy ról jako członka sprawy umożliwia członkom dostęp do tych zadań i wykonywanie ich w określonym przypadku. Aby uzyskać więcej informacji na temat dodawania grup ról jako członków przypadków, zobacz:

- [Zacznij od zbierania elektronicznych materiałów dowodowych (wersja standardowa)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

- [Dodawanie lub usuwanie członków ze sprawy zbierania elektronicznych materiałów dowodowych (Premium)](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

Mając to na uwadze, należy pamiętać, że jeśli rola zostanie dodana lub usunięta z grupy ról, ta grupa ról zostanie automatycznie usunięta jako członek każdej grupy ról. Powodem jest ochrona organizacji przed nieumyślnym udzieleniem dodatkowych uprawnień członkom sprawy. Podobnie, jeśli grupa ról zostanie usunięta, zostanie usunięta ze wszystkich przypadków, do które należała.

Przed dodaniem lub usunięciem ról do grupy ról, która może być członkiem sprawy zbierania elektronicznych materiałów dowodowych, możesz uruchomić następujące polecenia w programie [PowerShell Security & Compliance](/powershell/exchange/connect-to-scc-powershell) , aby uzyskać listę przypadków, do których należy grupa ról. Po zaktualizowaniu grupy ról należy dodać grupę ról z powrotem jako element członkowski tych przypadków.

### <a name="get-a-list-of-ediscovery-standard-cases-a-role-group-is-assigned-to"></a>Pobieranie listy przypadków zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) przypisanych do grupy ról

```powershell
Get-ComplianceCase -RoleGroup "Name of role group"
```

### <a name="get-a-list-of-ediscovery-premium-cases-a-role-group-is-assigned-to"></a>Pobieranie listy przypadków zbierania elektronicznych materiałów dowodowych (Premium) przypisanych do grupy ról

```powershell
Get-ComplianceCase -RoleGroup "Name of role group" -CaseType AdvancedEdiscovery
```

## <a name="more-information"></a>Więcej informacji

- **Dlaczego warto utworzyć administratora zbierania elektronicznych materiałów dowodowych?** Jak wyjaśniono wcześniej, administrator zbierania elektronicznych materiałów dowodowych jest członkiem grupy ról menedżera zbierania elektronicznych materiałów dowodowych, która może wyświetlać wszystkie przypadki zbierania elektronicznych materiałów dowodowych i uzyskiwać do nich dostęp w organizacji. Ta możliwość dostępu do wszystkich przypadków zbierania elektronicznych materiałów dowodowych ma dwa ważne cele:

  - Jeśli osoba, która jest jedynym członkiem sprawy zbierania elektronicznych materiałów dowodowych, opuszcza organizację, nikt (w tym członkowie grupy ról zarządzania organizacją lub inny członek grupy ról menedżera zbierania elektronicznych materiałów dowodowych) nie może uzyskać dostępu do tego przypadku zbierania elektronicznych materiałów dowodowych, ponieważ nie jest członkiem sprawy. W takiej sytuacji nie będzie możliwości uzyskania dostępu do danych w tym przypadku. Ponieważ jednak administrator zbierania elektronicznych materiałów dowodowych może uzyskać dostęp do wszystkich przypadków zbierania elektronicznych materiałów dowodowych w organizacji, może wyświetlić sprawę i dodać siebie lub innego menedżera zbierania elektronicznych materiałów dowodowych jako członka sprawy.

  - Ponieważ administrator zbierania elektronicznych materiałów dowodowych może wyświetlać i uzyskiwać dostęp do wszystkich przypadków zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) i zbierania elektronicznych materiałów dowodowych (Premium), może przeprowadzać inspekcję i nadzorować wszystkie przypadki oraz skojarzone wyszukiwania zgodności. Może to pomóc w zapobieganiu wszelkim niewłaściwym użyciu wyszukiwań zgodności lub przypadków zbierania elektronicznych materiałów dowodowych. Ponieważ administratorzy zbierania elektronicznych materiałów dowodowych mogą uzyskiwać dostęp do potencjalnie poufnych informacji w wynikach wyszukiwania zgodności, należy ograniczyć liczbę osób, które są administratorami zbierania elektronicznych materiałów dowodowych.

- **Czy mogę dodać grupę jako członka grupy ról menedżera zbierania elektronicznych materiałów dowodowych?** Jak wyjaśniono wcześniej, można dodać grupę zabezpieczeń z obsługą poczty jako członka podgrupy menedżerów zbierania elektronicznych materiałów dowodowych w grupie ról menedżera zbierania elektronicznych materiałów dowodowych przy użyciu polecenia cmdlet **Add-RoleGroupMember** w programie PowerShell Centrum zgodności & zabezpieczeń. Na przykład możesz uruchomić następujące polecenie, aby dodać grupę zabezpieczeń obsługującą pocztę do grupy ról menedżera zbierania elektronicznych materiałów dowodowych. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange grupy dystrybucyjne i Grupy Microsoft 365 nie są obsługiwane. Należy użyć grupy zabezpieczeń z obsługą poczty, którą można utworzyć w programie Exchange Online programie PowerShell, uruchamiając polecenie `New-DistributionGroup -Type Security`. Możesz również utworzyć grupę zabezpieczeń obsługującą pocztę (i dodać członków) w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a> lub w [Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339). Po utworzeniu nowej grupy zabezpieczeń z obsługą poczty może upłynąć do 60 minut, aby dodać ją do grupy ról Menedżerowie zbierania elektronicznych materiałów dowodowych.

    Ponadto, jak wspomniano wcześniej, nie można utworzyć grupy zabezpieczeń obsługującej pocztę jako administratora zbierania elektronicznych materiałów dowodowych przy użyciu polecenia cmdlet **Add-eDiscoveryCaseAdmin** w programie PowerShell Security & Compliance Center. Jako administratorów zbierania elektronicznych materiałów dowodowych można dodawać tylko poszczególnych użytkowników.

    Nie można również dodać grupy zabezpieczeń z obsługą poczty jako członka sprawy.
