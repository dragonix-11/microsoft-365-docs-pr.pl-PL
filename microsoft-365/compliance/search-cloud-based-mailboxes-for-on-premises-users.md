---
title: Wyszukiwanie Teams czatów dla użytkowników lokalnych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MST160
- MET150
ms.assetid: 3f7dde1a-a8ea-4366-86da-8ee6777f357c
description: Administratorzy mogą używać narzędzi zbierania elektronicznych materiałów dowodowych Microsoft 365 w celu wyszukiwania i eksportowania danych Teams czatów dla użytkowników lokalnych w Exchange hybrydowym.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fdd142783313418c8c65c04f9b5e344ff325ec2c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021165"
---
# <a name="search-for-teams-chat-data-for-on-premises-users"></a>Wyszukiwanie Teams czatów dla użytkowników lokalnych

Jeśli Organizacja ma wdrożenie hybrydowe programu Exchange (lub organizacja synchronizuje lokalną organizację programu Exchange z programem Office 365) i włączyła usługę Microsoft Teams, użytkownicy lokalni mogą używać aplikacji czatu Teams do obsługi wiadomości błyskawicznych. W przypadku użytkownika opartego na chmurze Teams danych czatu (nazywanych również czatami *1x1 lub 1xN*) są zapisywane w ich podstawowej skrzynce pocztowej w chmurze. Gdy użytkownik korzysta z aplikacji czatu Teams czatów, jego wiadomości na czacie nie mogą być przechowywane w podstawowej skrzynce pocztowej, która znajduje się lokalnie. W celu rozwiązania tego ograniczenia firma Microsoft wydała nową funkcję, w której jest tworzony obszar magazynu w chmurze, za pomocą narzędzi zbierania elektronicznych materiałów dowodowych do wyszukiwania i eksportowania danych Teams czatów dla użytkowników lokalnych.
  
Oto wymagania i ograniczenia dotyczące włączania magazynu lokalnego w chmurze:
  
- Konta użytkowników w lokalnej usłudze katalogowej (na przykład Active Directory) muszą być zsynchronizowane z usługą Azure Active Directory, usługą katalogową w usłudze Microsoft 365. Oznacza to, że w programie Microsoft 365 utworzono konto użytkownika poczty i jest skojarzone z użytkownikiem, którego podstawowa skrzynka pocztowa znajduje się w organizacji lokalnej.

- Użytkownik, którego podstawowa skrzynka pocztowa znajduje się w organizacji lokalnej, musi mieć przypisaną licencję usługi Microsoft Teams oraz co najmniej licencję Exchange Online Plan 1.

- Jeśli Twoja organizacja nie ma hybrydowego Exchange hybrydowego, musisz zsynchronizować lokalną Exchange schemat, aby Azure Active Directory. Jeśli tego nie zrobisz, istnieje ryzyko utworzenia zduplikowanych chmurowych skrzynek pocztowych w programie Exchange Online dla użytkowników, którzy mają skrzynkę pocztową w lokalnej Exchange organizacji.

- Tylko Teams czatów skojarzone z lokalnym użytkownikiem są przechowywane w opartym na chmurze obszarze przechowywania. Użytkownik lokalnie nie może w żaden sposób uzyskać dostępu do tego obszaru magazynu.

> [!NOTE]
> Teams konwersacji w kanale są zawsze przechowywane w chmurowej skrzynce pocztowej skojarzonej z zespołem, co oznacza, że możesz wyszukiwać konwersacje w kanale. Aby uzyskać więcej informacji na temat Teams konwersacji w kanale, zobacz Wyszukiwanie Microsoft Teams [i Microsoft 365 grup](content-search-reference.md#searching-microsoft-teams-and-microsoft-365-groups).
  
## <a name="how-it-works"></a>Jak to działa

Jeśli użytkownik z włączoną obsługą usługi Microsoft Teams ma lokalną skrzynkę pocztową, a jego konto/tożsamość użytkownika zostało zsynchronizowane z chmurą, firma Microsoft tworzy magazyn w chmurze w celu skojarzenia danych czatu z 1xN użytkownika lokalnego Teams z. Teams czatów dla użytkowników lokalnych są indeksowane w celu wyszukiwania. Dzięki temu możesz wyszukiwać i eksportować dane Teams użytkowników lokalnych przy użyciu wyszukiwania zawartości (i Advanced eDiscovery powiązanych z podstawowymi sprawami zbierania elektronicznych materiałów dowodowych i zbierania elektronicznych materiałów dowodowych). Możesz również użyć poleceń **\*cmdlet funkcji ComplianceSearch** w centrum zabezpieczeń & zgodności programu PowerShell, aby Teams danych czatu dla użytkowników lokalnych.
  
Na poniższej ilustracji przedstawiono przepływ pracy, w jaki Teams wiadomości czatu dla użytkowników lokalnych są dostępne do wyszukiwania i wyświetlania podglądu oraz eksportowania.
  
![Przechowywanie danych w chmurze dla użytkowników lokalnych w Microsoft Teams.](../media/EHAMShard1.png)
  
Oprócz tej funkcji możesz również używać narzędzi zbierania elektronicznych materiałów dowodowych w celu przeszukiwania i wyświetlania podglądu zawartości programu Teams oraz eksportowania jej w chmurze w witrynie programu SharePoint i skrzynce pocztowej usługi Exchange skojarzonej z każdym zespołem Microsoft Team oraz danymi rozmów 1xN Teams w skrzynce pocztowej usługi Exchange Online dla użytkowników korzystających z chmury.

## <a name="searching-for-teams-chat-content-for-on-premises-users"></a>Wyszukiwanie Teams czatu dla użytkowników lokalnych

Poniżej opisano, jak za pomocą funkcji wyszukiwanie zawartości Centrum zgodności platformy Microsoft 365 wyszukiwania Teams czatów dla użytkowników lokalnych. Możesz również użyć narzędzia wyszukiwania w core eDiscovery, aby wyszukać dane czatu dla użytkowników lokalnych.
  
1. W Centrum zgodności platformy Microsoft 365 przejdź do **pola Wyszukiwanie zawartości**.

2. Na **karcie Wyszukiwania** kliknij pozycję **Nowe wyszukiwanie** i nadaj nazwę nowem wyszukiwaniu.

3. Na **stronie Lokalizacje** ustaw przełącznik w pozycji Wł **. dla Exchange** pocztowych.

4. Aby wyszukać Teams zawartości dla określonych użytkowników (w tym użytkowników lokalnych), wybierz pozycję Wybierz użytkownika **,** grupy lub zespoły i wybierz konkretnych użytkowników do uwzględnienia w wyszukiwaniu. Jeśli nie zostanie wyświetlona lista konkretnych użytkowników, wyszukiwanie obejmie wszystkich użytkowników, w tym użytkowników lokalnych.

5. Upewnij się **, że** jest zaznaczone pole wyboru Dodaj zawartość aplikacji dla użytkowników lokalnych. Dzięki temu będzie przeszukiwane magazyn w bazie danych w chmurze dla użytkowników lokalnych.

    ![Zaznacz pole wyboru "Aplikacja pakietu Office zawartości dla użytkowników lokalnych" na stronie kreatora Lokalizacje.](../media/EHAMShardCheckBox.png)

6. Na stronie **Definiowanie warunków wyszukiwania** utwórz zapytanie słów kluczowych i w razie potrzeby dodaj warunki do zapytania wyszukiwania. Aby wyszukać tylko dane czatów zespołu, możesz dodać następujące zapytanie w polu **Słowa kluczowe** :

    ```text
    kind:im AND kind:microsoftteams
    ```

6. Prześlij i uruchom wyszukiwanie. Wszelkie wyniki wyszukiwania użytkowników lokalnych można wyświetlać w podglądzie tak samo jak inne wyniki wyszukiwania. Możesz również wyeksportować wyniki wyszukiwania (w tym Teams danych czatu) do pliku PST. Więcej informacji można znaleźć w następujących artykułach:

    - [Tworzenie wyszukiwania](content-search.md)

    - [Podgląd wyników wyszukiwania](preview-ediscovery-search-results.md)

    - [Eksportowanie wyników wyszukiwania](export-search-results.md)

## <a name="using-powershell-to-search-for-teams-chat-data-for-on-premises-users"></a>Wyszukiwanie danych czatu Teams użytkowników lokalnych za pomocą programu PowerShell

Za pomocą poleceń cmdlet **New-ComplianceSearch** w Centrum & zgodności w programie PowerShell możesz Teams danych czatu dla użytkowników lokalnych. Jak wyjaśniono wcześniej, nie musisz przesyłać wniosku o pomoc techniczną, aby użyć programu PowerShell do wyszukiwania Teams danych czatu dla użytkowników lokalnych.
  
1. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom następujące polecenie programu PowerShell, aby utworzyć wyszukiwanie zawartości, które wyszukuje Teams danych czatu dla użytkowników lokalnych.

    ```powershell
    New-ComplianceSearch <name of new search> -ContentMatchQuery <search query> -ExchangeLocation <on-premises user> -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

    Parametr *IncludeUserAppContent*  służy do określania opartego na chmurze magazynu dla użytkownika lub użytkowników określonych przez  *parametr ExchangeLocation*  . Funkcja *AllowNotFoundExchangeLocationsEnabled*  umożliwia wyszukiwanie użytkowników lokalnych w magazynie opartym na chmurze. W przypadku użycia wartości `$true` dla tego parametru wyszukiwanie nie próbuje sprawdzić, czy skrzynka pocztowa istnieje przed jej rozpoczęciem. Jest to wymagane do przeszukiwania magazynu lokalnego w chmurze dla użytkowników, ponieważ ten magazyn oparty na chmurze nie jest rozpoznawalny jako zwykła skrzynka pocztowa w chmurze.

    Poniższy przykład wyszukuje Teams, które zawierają słowo kluczowe "redstone" w opartym na chmurze magazynie dla Anny Ciesomej, która jest użytkownikiem lokalnym w organizacji Contoso.
  
    ```powershell
    New-ComplianceSearch "Redstone_Search" -ContentMatchQuery "redstone AND (kind:im AND kind:microsoftteams)" -ExchangeLocation sarad@contoso.com -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

   Po utworzeniu wyszukiwania użyj polecenia cmdlet **Start-ComplianceSearch** , aby uruchomić wyszukiwanie.
  
Aby uzyskać więcej informacji dotyczących korzystania z tych funkcji cmdlet, zobacz:
  
- [Wyszukiwanie nowych zgodności](/powershell/module/exchange/new-compliancesearch)

- [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

## <a name="known-issues"></a>Znane problemy

- Obecnie możesz wyszukiwać, wyświetlać podgląd i eksportować Teams czatów dla użytkowników lokalnych. Możesz także umieścić dane czatu Teams użytkownika lokalnego w czacie skojarzonym ze sprawą podstawową lub Advanced eDiscovery i zastosować zasady przechowywania dla czatów Teams lub wiadomości kanałów dla użytkowników lokalnych. Jednak obecnie nie można stosować zasad przechowywania dla innych lokalizacji zawartości (takich jak skrzynki pocztowe Exchange i witryny SharePoint) dla użytkowników lokalnych.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Czy muszę wysyłać wnioski o pomoc techniczną w celu wyszukania wiadomości czatu dla użytkowników lokalnych?**

L.p. Ta funkcja jest domyślnie włączona dla wszystkich organizacji. W pewnym momencie trzeba było skontaktować się z pomocą techniczną firmy Microsoft, ale już nie tak jest.
  
 **Czy narzędzia zbierania elektronicznych materiałów dowodowych mogą znaleźć starsze dane Teams czatów dla użytkowników lokalnych przed czasem, w jaki ta funkcja była domyślnie włączona dla wszystkich organizacji?**
  
Firma Microsoft rozpoczęła przechowywanie Teams danych czatu dla użytkowników lokalnych 31 stycznia 2018 r. Jeśli od tej daty tożsamość użytkownika lokalnego programu Teams została zsynchronizowana między lokalną usługą Active Directory i usługą Azure Active Directory w usłudze Microsoft 365, dane rozmów Teams są przechowywane w chmurze i można je przeszukiwać przy użyciu narzędzi zbierania elektronicznych materiałów dowodowych.

 **Czy użytkownicy lokalni muszą mieć licencję, aby przechowywać swoje Teams czatów w chmurze?**
  
Tak. Aby przechowywać Teams czatu dla użytkownika lokalnego w magazynie w chmurze, musi on mieć przypisaną licencję Microsoft Teams i licencję planu usługi Exchange Online w systemie Office 365 (lub Microsoft 365).

**Gdzie znajduje się magazyn w chmurze dla użytkowników lokalnych?**
  
Teams czatów są przechowywane w preferowanej lokalizacji danych (PDL) dla użytkownika lokalnego. Plik PDL jest honorowany zarówno w środowisku Single-Geo jak i w środowisku wielolokalowym. Aby uzyskać więcej informacji, zobacz [Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md).

**Czy istnieje ryzyko utraty danych Teams czatu, jeśli lokalna skrzynka pocztowa użytkownika jest migrowana do chmury?**
  
L.p. Podczas migracji podstawowej skrzynki pocztowej użytkownika lokalnego do chmury dane rozmów Teams tego użytkownika zostaną zmigrowane do jego nowej podstawowej skrzynki pocztowej w chmurze.
  
 **Czy można zastosować zasady przechowywania lub zbierania elektronicznych materiałów dowodowych do użytkowników lokalnych?**
  
Tak. Możesz stosować blokady zbierania elektronicznych materiałów dowodowych lub zasady przechowywania Teams czatach i wiadomościach kanałów użytkowników lokalnych. Jednak w celu zachowania Teams zawartości dla użytkowników lokalnych użytkownikowi lokalnego należy przypisać licencję Exchange Online Plan 2.
