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
description: Jeśli jesteś administratorem globalnym lub administratorem zarządzania użytkownikami subskrypcji Microsoft 365 dla firm, możesz użyć filtrów do tworzenia, edytowania lub usuwania niestandardowego widoku użytkownika.
ms.openlocfilehash: d90d324690d153fa708dbe7c36a9f41d349f8588
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436740"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Tworzenie, edytowanie i usuwanie niestandardowego widoku użytkownika

Jeśli jesteś administratorem globalnym lub administratorem zarządzania użytkownikami subskrypcji Microsoft 365 dla firm, możesz utworzyć niestandardowe widoki użytkowników, aby wyświetlić określony podzbiór użytkowników. Widoki te są dodatkiem do standardowego zestawu widoków. Możesz tworzyć, edytować lub usuwać niestandardowe widoki użytkowników, a utworzone widoki niestandardowe są dostępne dla wszystkich administratorów.
  
## <a name="custom-user-views-in-the-admin-center"></a>Niestandardowe widoki użytkowników w centrum administracyjnym

Podczas tworzenia, edytowania lub usuwania niestandardowego widoku użytkownika zmiany zostaną wyświetlone na liście **Filtr** , którą wszyscy administratorzy w firmie widzą po przejściu do strony **Użytkownicy** . Możesz utworzyć maksymalnie 50 widoków niestandardowych. 

> [!TIP]
>  Standardowe widoki użytkowników są domyślnie wyświetlane na liście rozwijanej **Filtry**. Standardowe filtry obejmują **wszystkich użytkowników**, **licencjonowanych użytkowników,** **użytkowników-gości**,  **dozwolonych logowań**, **zablokowanych logowań**, **użytkowników nielicencjonowanych**, **użytkowników z błędami**, **administratorów rozliczeń**, **administratorów globalnych**, **administratorów pomocy technicznej**, **administratorów usług** i **administratorów zarządzania użytkownikami**. Nie można edytować ani usuwać widoków standardowych. 

Kilka kwestii do zapamiętania na temat widoków standardowych: 

- Niektóre widoki standardowe wyświetlają listę niesortowaną, jeśli na liście znajduje się ponad 2000 użytkowników. Aby zlokalizować określonych użytkowników na tej liście, użyj pola wyszukiwania. 
- Jeśli nie zakupiono Microsoft 365 od firmy Microsoft, **administratorzy rozliczeń nie są widoczni na liście widoków** standardowych. Aby uzyskać więcej informacji, zobacz [Przypisywanie ról administratora](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Wybieranie filtrów dla niestandardowego widoku użytkownika

Widoki niestandardowe można tworzyć i edytować w okienku **Filtr niestandardowy** . Jeśli wybierzesz wiele opcji filtru, uzyskasz wyniki zawierające użytkowników spełniających wszystkie wybrane kryteria. W poniższym przykładzie pokazano, jak utworzyć widok niestandardowy o nazwie "Użytkownicy kanadyjscy", który pokazuje wszystkich użytkowników w określonej domenie, którzy znajdują się w Kanadzie. 

  
 **A — domena** Jeśli masz wiele domen dla swojej organizacji, możesz wybrać z listy rozwijanej dostępnych domen. 
  
 **B — stan logowania** Wybierz użytkowników, którzy są dozwolone lub zablokowane. 
  
 **C — lokalizacja** Wybierz lokalizację z listy rozwijanej krajów. 
  
 **D — przypisana licencja produktu** Wybierz z listy rozwijanej licencji dostępnych w organizacji. Użyj tego filtru, aby wyświetlić użytkowników, którzy mają przypisaną licencję. Użytkownicy mogą również mieć dodatkowe licencje. 
  
Możesz również filtrować według dodatkowych szczegółów profilu użytkownika używanych w organizacji, takich jak dział, miasto, stan lub prowincja, kraj lub region albo stanowisko.
  
 **Inne warunki:**
  
- **Tylko zsynchronizowanych użytkowników** Zaznacz to pole, aby wyświetlić wszystkich użytkowników, którzy zostali zsynchronizowani z lokalną usługą Active Directory, niezależnie od tego, czy użytkownicy zostali aktywowani. 
    
- **Użytkownicy z błędami** Zaznacz to pole, aby wyświetlić użytkowników, którzy mogą mieć błędy aprowizacji. 
    
- **Użytkownicy bez licencji** Zaznacz to pole, aby znaleźć wszystkich użytkowników, którzy nie otrzymali licencji. Wyniki dla tego widoku mogą również obejmować użytkowników, którzy mają Exchange skrzynkę pocztową, ale nie mają licencji. Aby śledzić tych użytkowników, użyj filtru **Nielicencjonowani użytkownicy z Exchange skrzynek pocztowych lub archiwów**. Wyniki dla tego widoku mogą również obejmować użytkowników, którzy mają Exchange archiwum, ale nie mają licencji.
    
- **Nielicencjonowani użytkownicy z Exchange skrzynkami pocztowymi lub archiwami** Wybierz to pole, aby wyświetlić konta użytkowników utworzone w Exchange Online i mają Exchange skrzynkę pocztową, ale nie przypisano jej do licencji Microsoft 365. Wyniki tego filtru obejmują użytkowników, którzy mają lub którzy zostali przypisani do archiwum Exchange. 

> [!NOTE]
> Filtr **Nielicencjonowani użytkownicy z Exchange skrzynkami pocztowymi** działa, gdy:
1. Skrzynka pocztowa została niedawno przekonwertowana z **udostępnionej** na **użytkownika** i nie ma licencji.
2. Skrzynka pocztowa została niedawno zmigrowana do Microsoft 365 ale licencja nie została przypisana.
3. Skrzynka pocztowa została utworzona przy użyciu programu PowerShell i licencja nie została przypisana.
4. Dla użytkownika jest aprowizowana nowa skrzynka pocztowa utworzona lokalnie za pomocą polecenia cmdlet New-RemoteMailbox.
    
> [!TIP]
> Jeśli utworzysz widok niestandardowy, który zwróci więcej niż 2000 użytkowników, lista użytkowników wynikowych nie zostanie posortowana. W takim przypadku użyj pola wyszukiwania, aby znaleźć użytkowników lub edytować widok niestandardowy, aby uściślić wyszukiwanie. 
  
## <a name="create-a-custom-user-view"></a>Tworzenie niestandardowego widoku użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do pozycji **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">aktywni użytkownicy</a>.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do pozycji **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">aktywni użytkownicy</a>.  

::: moniker-end
    
2. Na stronie **Aktywni użytkownicy** wybierz pozycję **Filtry** i wybierz pozycję **Nowy filtr**.
  
3. Na stronie **Filtr niestandardowy** wprowadź nazwę filtru, wybierz warunki filtru niestandardowego, a następnie wybierz pozycję **Dodaj**. Widok niestandardowy znajduje się teraz na liście rozwijanej filtrów.

## <a name="edit-or-delete-a-custom-user-view"></a>Edytowanie lub usuwanie niestandardowego widoku użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do pozycji **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do pozycji **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">aktywni użytkownicy</a>. 

::: moniker-end 
    
2. Na stronie **Aktywni użytkownicy** wybierz pozycję **Filtruj**, wybierz filtr, który chcesz zmienić, a następnie wybierz pozycję **Edytuj filtr**. 
    
    > [!TIP]
    > Można edytować tylko widoki niestandardowe. 
  
3. Na stronie **Filtr niestandardowy** edytuj informacje zgodnie z potrzebami, a następnie wybierz pozycję **Zapisz**. Aby usunąć filtr, w dolnej części strony wybierz pozycję **Usuń**. 

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie Centrum administracyjne platformy Microsoft 365](../admin-overview/admin-center-overview.md) (wideo)\
[Informacje o rolach administratora](../add-users/about-admin-roles.md) (wideo)\
[Dostosowywanie motywu Microsoft 365 dla organizacji](../setup/customize-your-organization-theme.md) (artykuł)


     
