---
title: Tworzenie, edytowanie i usuwanie niestandardowego widoku użytkownika
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 4fe7f6ac-be8e-4b57-9e13-24ff889a4b28
description: Dowiedz się, jak używać filtrów do tworzenia, edytowania i usuwania niestandardowego widoku użytkownika w Microsoft 365.
ms.openlocfilehash: 479f6c566cea407e75c6fb14f76db418c127aeb4
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017857"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Tworzenie, edytowanie i usuwanie niestandardowego widoku użytkownika

Jeśli jesteś administratorem globalnym lub administratorem zarządzającym użytkownikami subskrypcji usługi Microsoft 365 dla firm, możesz tworzyć niestandardowe widoki użytkowników w celu wyświetlania określonego podzbioru użytkowników. Widoki te są dodatkiem do standardowego zestawu widoków. Możesz tworzyć, edytować lub usuwać niestandardowe widoki użytkowników, a tworzyć własne widoki niestandardowe, które są dostępne dla wszystkich administratorów.
  
## <a name="custom-user-views-in-the-admin-center"></a>Niestandardowe widoki użytkownika w centrum administracyjnym

Gdy tworzysz, edytujesz lub usuwasz niestandardowy widok użytkownika, zmiany będą wyświetlane na liście Filtr widocznej dla wszystkich administratorów w firmie, gdy przejdą do **strony** Użytkownicy. Możesz utworzyć do 50 widoków niestandardowych. 

> [!TIP]
>  Standardowe widoki użytkownika są domyślnie wyświetlane na **liście rozwijanej** Filtry. Standardowe filtry obejmują: Wszyscy **użytkownicy, Licencjonowani** **użytkownicy, Użytkownicy** **goście, Logowanie**  **dozwolone, Logowanie** jest **zablokowane, Użytkownicy** bez **licencji, Użytkownicy** z błędami **,** Administratorzy **rozliczeń,** **Administratorzy** globalni **,** administratorzy działu pomocy **technicznej,** administratorzy usługi i administratorzy zarządzający **użytkownikami**. Nie można edytować ani usuwać widoków standardowych. 

Kilka standardowych widoków, na które należy zwrócić uwagę: 

- W niektórych widokach standardowych jest wyświetlana nieposortowana lista, jeśli lista zawiera więcej niż 2000 użytkowników. Aby zlokalizować konkretnych użytkowników na tej liście, użyj pola wyszukiwania. 
- W przypadku nieuzysłania Microsoft 365 od firmy **Microsoft administratorzy** rozliczeń nie są wyświetleni na liście standardowych widoków. Aby uzyskać więcej informacji, zobacz [Przypisywanie ról administratora](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Wybieranie filtrów dla niestandardowego widoku użytkownika

Widoki niestandardowe można tworzyć i edytować w **okienku Filtr** niestandardowy. Jeśli wybierzesz wiele opcji filtru, zostaną uzyskane wyniki zawierające użytkowników, którzy spełniają wszystkie wybrane kryteria. W poniższym przykładzie pokazano, jak utworzyć widok niestandardowy o nazwie "Użytkownicy w Kanadzie", który przedstawia wszystkich użytkowników w określonej domenie, którzy znajdują się w Kanadzie. 

  
 **A — domena** Jeśli masz wiele domen dla swojej organizacji, możesz wybrać domenę z listy rozwijanej dostępnych domen. 
  
 **B — Stan logowania** Wybierz użytkowników, którzy są dozwoloni lub zablokowani. 
  
 **C — Lokalizacja** Wybierz lokalizację z listy rozwijanej krajów. 
  
 **D — Przypisana licencja produktu** Wybierz licencję z listy rozwijanej dostępnej w Twojej organizacji. Ten filtr umożliwia wyświetlanie użytkowników, do których przypisano wybraną licencję. Użytkownicy mogą również mieć dodatkowe licencje. 
  
Możesz również filtrować według dodatkowych szczegółów profilu użytkownika używanych w organizacji, takich jak dział, miasto, województwo, kraj lub region lub stanowisko.
  
 **Inne warunki:**
  
- **Tylko zsynchronizowani użytkownicy** Zaznacz to pole wyboru, aby wyświetlić wszystkich użytkowników, którzy zostały zsynchronizowani z lokalną usługą Active Directory, niezależnie od tego, czy użytkownicy zostały aktywowane. 
    
- **Użytkownicy z błędami** Zaznacz to pole, aby wyświetlić użytkowników, którzy mogą mieć błędy inicjowania obsługi administracyjnej. 
    
- **Nielicencjonowani użytkownicy** Zaznacz to pole, aby znaleźć wszystkich użytkowników, którym nie przypisano licencji. Wyniki dla tego widoku mogą również obejmować użytkowników, którzy mają skrzynkę pocztową usługi Exchange ale nie mają licencji. Aby śledzić tych użytkowników, użyj filtru **Nielicencjonowani użytkownicy Exchange skrzynki pocztowe lub archiwa**. Wyniki dla tego widoku mogą również obejmować użytkowników, którzy mają Exchange archiwum wiadomości, ale nie mają licencji.
    
- **Nielicencjonowani** użytkownicy ze skrzynkami pocztowymi lub archiwami programu Exchange Zaznacz to pole, aby wyświetlić konta użytkowników, które zostały utworzone w programie Exchange Online i mają skrzynkę pocztową programu Exchange, ale do których nie przypisano licencji usługi Microsoft 365. Ten filtr jest również filtrem użytkowników, którym przypisano archiwum Exchange archiwum. 

> [!NOTE]
> Filtr **Nielicencjonowani użytkownicy z Exchange pocztowych** działa w następującej sytuacji:
1. Skrzynka pocztowa została ostatnio przekonwertowana z **udostępnionego** na **użytkownika i nie** ma licencji.
2. Skrzynka pocztowa została ostatnio zmigrowana do usługi Microsoft 365 ale licencja nie została przypisana.
3. Skrzynka pocztowa została utworzona przy użyciu programu PowerShell i licencja nie została przypisana.
4. Dla użytkownika jest aprowowana nowa skrzynka pocztowa, która została utworzona lokalnie New-RemoteMailbox poleceniem cmdlet.
    
> [!TIP]
> Jeśli utworzysz widok niestandardowy, który zwraca więcej niż 2000 użytkowników, wynikowa lista użytkowników nie zostanie posortowana. W takim przypadku użyj pola wyszukiwania, aby znaleźć użytkowników, lub edytuj widok niestandardowy, aby uściślić wyszukiwanie. 
  
## <a name="create-a-custom-user-view"></a>Tworzenie niestandardowego widoku użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do pozycji **Aktywni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">użytkownicy użytkownicy</a>.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do pozycji **Aktywni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">użytkownicy użytkownicy</a>.  

::: moniker-end
    
2. Na stronie **Aktywni użytkownicy** wybierz pozycję **Filtry** i wybierz pozycję **Nowy filtr**.
  
3. Na **stronie Filtr niestandardowy** wprowadź nazwę filtru, wybierz warunki filtru niestandardowego, a następnie wybierz pozycję **Dodaj**. Widok niestandardowy zostanie uwzględniony na liście rozwijanej filtrów.

## <a name="edit-or-delete-a-custom-user-view"></a>Edytowanie lub usuwanie niestandardowego widoku użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do pozycji **Aktywni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">użytkownicy użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do pozycji **Aktywni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">użytkownicy użytkownicy</a>. 

::: moniker-end 
    
2. Na stronie **Aktywni użytkownicy** wybierz pozycję **Filtruj**, wybierz filtr, który chcesz zmienić, a następnie wybierz pozycję **Edytuj filtr**. 
    
    > [!TIP]
    > Możesz edytować tylko widoki niestandardowe. 
  
3. Na stronie **Filtr niestandardowy** edytuj informacje zgodnie z potrzebami, a następnie wybierz pozycję **Zapisz**. Aby usunąć filtr, u dołu strony wybierz pozycję **Usuń**. 

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie centrum administracyjne platformy Microsoft 365](Omówienie centrum administracyjne platformy Microsoft 365](.. /admin-overview/admin-center-overview.md) (wideo)\
[Role administratorów](../add-users/about-admin-roles.md) (klip wideo)\ Informacje
[Dostosowywanie Microsoft 365 organizacji](../setup/customize-your-organization-theme.md) (artykuł)


     