---
title: Przypisywanie ról administratora w centrum administracyjne platformy Microsoft 365
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
- Adm_TOC
ms.custom:
- MSStore_Link
- okr_smb
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: eac4d046-1afd-4f1a-85fc-8219c79e1504
description: Dowiedz się, jak przypisać role administratora do użytkownika lub wielu użytkowników w firmie, aby mógł wykonywać określone zadania w centrum administracyjnym.
ms.openlocfilehash: fd38bb9ed378e6b3ffc20a79ca71eb2943599dcc
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995930"
---
# <a name="assign-admin-roles"></a>Przypisywanie ról administratora

Jeśli jesteś osobą, która kupiła Twoją subskrypcję firmy Microsoft dla firm, jesteś administratorem globalnym. Oznacza to, że masz nieograniczoną kontrolę nad produktami w subskrypcjach i możesz uzyskać dostęp do większości danych.

Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](about-admin-roles.md).

Jeśli nie przypiszesz im roli administratora podczas dodawania nowych użytkowników, pełnią oni tę rolę i nie  mają uprawnień administratora w żadnym z centrów aadministracyjnym firmy Microsoft. Jeśli jednak potrzebujesz pomocy w sprawach, możesz przypisać rolę administratora do użytkownika. Jeśli na przykład chcesz, aby ktoś pomógł Ci w resetowaniu haseł, nie przypisz mu roli administratora globalnego, przypisz mu rolę administratora haseł. Zbyt duża liczba administratorów globalnych bez ograniczeń dostępu do danych i firm online stanowi zagrożenie bezpieczeństwa.

## <a name="watch-add-an-admin"></a>Obejrzyj: Dodawanie administratora

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfO] 

1. Gdy tworzysz konto w Microsoft 365 Business, automatycznie stajesz się administratorem globalnym. Aby ułatwić zarządzanie firmą, możesz również określić innych administratorów. 
1. W centrum administracyjne platformy Microsoft 365 wybierz pozycję **Użytkownicy** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktywuj użytkowników**</a>.
1. Wybierz użytkownika, którego chcesz pełnić rolę administratora, a następnie wybierz pozycję **Zarządzaj rolami**.

Jeśli ten klip wideo okazał się przydatny, poznaj [kompletną serię szkoleń dla małych firm i nowych użytkowników usługi Microsoft 365](../../business-video/index.yml).

## <a name="assign-admin-roles"></a>Przypisywanie ról administratora 

Do roli można przypisać użytkowników na dwa różne sposoby:

- Możesz przejść do szczegółów użytkownika i wybrać zarządzanie rolami  w celu przypisania roli do użytkownika.
- Możesz również przejść do role **i** wybrać tę rolę, a następnie dodać do niego wielu użytkowników.

### <a name="assign-admin-roles-to-users-using-roles"></a>Przypisywanie ról administratora użytkownikom za pomocą ról

1. W centrum administracyjnym przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**pozycji Przypisania ról**</a>. Wybierz karty **Azure AD** lub **Intune** , aby wyświetlić role administratorów dostępne dla Twojej organizacji.
2. Wybierz rolę administratora, do której chcesz przypisać użytkownika.
3. Wybierz **pozycję Przypisani** **administratorzyDad** > .
4. Wpisz nazwę **wyświetlaną lub** nazwę **użytkownika, a** następnie wybierz użytkownika z listy sugestii.
5. Dodaj wielu użytkowników, dopóki nie zostanie to zrobione.
6. Wybierz **pozycję** Zapisz, a następnie użytkownik zostanie dodany do listy przypisanych administratorów.

### <a name="assign-a-user-to-an-admin-role-from-active-users"></a>Przypisywanie użytkownika do roli administratora z usługi Aktywni użytkownicy

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do **strony Aktywni** > [użytkownicy użytkownicy](https://go.microsoft.com/fwlink/p/?linkid=834822) .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** > <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Na stronie **Aktywni** użytkownicy wybierz użytkownika, którego rolę administratora chcesz zmienić. W wysuwanych okienkach w obszarze **Role** wybierz pozycję **Zarządzaj rolami**.

3. Wybierz rolę administratora, którą chcesz przypisać do użytkownika. Jeśli nie widzisz roli, których szukasz, wybierz pozycję Pokaż wszystko u dołu listy.

## <a name="assign-admin-roles-to-multiple-users"></a>Przypisywanie ról administratora wielu użytkownikom

Jeśli znasz program PowerShell, zobacz [Przypisywanie ról do kont użytkowników za pomocą programu PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md). To doskonały sposób przypisywania ról kilkuset użytkownikom.
  
Aby przypisać role dziesiątkom użytkowników, skorzystaj z poniższych instrukcji.

## <a name="check-admin-roles-in-your-organization"></a>Sprawdzanie ról administratora w organizacji

Możesz nie mieć odpowiednich uprawnień do przypisywania ról administratorów innym użytkownikom. Sprawdź, czy masz odpowiednie uprawnienia, lub poproś innego administratora o przypisanie ról.

Uprawnienia roli administratora można sprawdzać na dwa różne sposoby:

- Możesz przejść do szczegółów użytkownika i sprawdzić go w obszarze **Role** na **stronie** Konto.
- Możesz również przejść do pozycji **Role i** wybrać rolę administratora, a następnie wybrać przypisani administratorzy, aby sprawdzić, którzy użytkownicy są przypisani.

## <a name="related-content"></a>Zawartość pokrewna

[Informacje Microsoft 365 administratora](about-admin-roles.md) (artykuł)\
[Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference) (artykuł)\
[Przypisywanie ról do kont użytkowników za pomocą programu PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md) (artykuł)\
[Autoryzuj lub usuwaj relacje partnerów](../misc/add-partner.md) (artykuł)