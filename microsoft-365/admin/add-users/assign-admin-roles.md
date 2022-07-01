---
title: Przypisywanie ról administratora Centrum administracyjne platformy Microsoft 365
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
description: Dowiedz się, jak przypisać role administratora do użytkownika lub wielu użytkowników w firmie, aby mogli oni wykonywać określone zadania w centrum administracyjnym.
ms.openlocfilehash: 62a860fd90104e475763494f84ca1b4546774757
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601526"
---
# <a name="assign-admin-roles-in-the-microsoft-365-admin-center"></a>Przypisywanie ról administratora w Centrum administracyjne platformy Microsoft 365

Zapoznaj się z [pomocą dla małych firm platformy Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) w serwisie YouTube.

Jeśli jesteś osobą, która kupiła Subskrypcję biznesową firmy Microsoft, jesteś administratorem globalnym. Oznacza to, że masz nieograniczoną kontrolę nad produktami w subskrypcjach i masz dostęp do większości danych.

Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](about-admin-roles.md).

Jeśli dodasz nowych użytkowników, jeśli nie przypiszesz im roli administratora, będą oni pełnić *rolę użytkownika* i nie mają uprawnień administratora do żadnego z centrów administracyjnych firmy Microsoft. Jeśli jednak potrzebujesz pomocy w wykonywaniu zadań, możesz przypisać rolę administratora do użytkownika. Jeśli na przykład potrzebujesz kogoś, kto pomoże zresetować hasła, nie powinieneś przypisywać mu roli administratora globalnego, musisz przypisać mu rolę administratora haseł. Posiadanie zbyt wielu administratorów globalnych z nieograniczonym dostępem do danych i działalności online stanowi zagrożenie dla bezpieczeństwa.

## <a name="watch-add-an-admin"></a>Obejrzyj: Dodawanie administratora

Zapoznaj się z tym filmem i innymi osobami na naszym [kanale YouTube](https://go.microsoft.com/fwlink/?linkid=2198030).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfO] 

1. Po utworzeniu konta w usłudze Microsoft 365 Business automatycznie stajesz się administratorem globalnym. Aby ułatwić zarządzanie firmą, możesz również tworzyć administratorów innych osób. 
1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Użytkownicy** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**aktywni użytkownicy**</a>.
1. Wybierz użytkownika, który chcesz utworzyć administratora, a następnie wybierz pozycję **Zarządzaj rolami**.

Jeśli ten klip wideo okazał się przydatny, poznaj [kompletną serię szkoleń dla małych firm i nowych użytkowników usługi Microsoft 365](../../business-video/index.yml).

## <a name="assign-admin-roles"></a>Przypisywanie ról administratora 

Możesz przypisać użytkowników do roli na dwa różne sposoby:

- Możesz przejść do szczegółów użytkownika i **zarządzać rolami** , aby przypisać rolę do użytkownika.
- Możesz też przejść do pozycji **Role** i wybrać rolę, a następnie dodać do niej wielu użytkowników.

### <a name="assign-admin-roles-to-users-using-roles"></a>Przypisywanie ról administratora do użytkowników przy użyciu ról

1. W centrum administracyjnym przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**Przypisania ról**</a>. Wybierz karty **Azure AD** lub **Intune**, aby wyświetlić role administratora dostępne dla Organizacji.
2. Wybierz rolę administratora, do którą chcesz przypisać użytkownika.
3. Wybierz pozycję **Przypisani administratorzy** > **Dodaj**.
4. Wpisz **nazwę wyświetlaną** użytkownika lub **nazwę użytkownika**, a następnie wybierz użytkownika z listy sugestii.
5. Dodaj wielu użytkowników, dopóki nie skończysz.
6. Wybierz pozycję **Zapisz**, a następnie użytkownik zostanie dodany do listy przypisanych administratorów.

### <a name="assign-a-user-to-an-admin-role-from-active-users"></a>Przypisywanie użytkownika do roli administratora od aktywnych użytkowników

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** > [aktywni użytkownicy](https://go.microsoft.com/fwlink/p/?linkid=834822) .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** > <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

2. Na stronie **Aktywni użytkownicy** wybierz użytkownika, którego rolę administratora chcesz zmienić. W okienku wysuwanym w obszarze **Role** wybierz pozycję **Zarządzaj rolami**.

3. Wybierz rolę administratora, którą chcesz przypisać użytkownikowi. Jeśli nie widzisz roli, której szukasz, wybierz pozycję **Pokaż wszystko** w dolnej części listy.

## <a name="assign-admin-roles-to-multiple-users"></a>Przypisywanie ról administratora wielu użytkownikom

Jeśli znasz program PowerShell, zobacz [Przypisywanie ról do kont użytkowników przy użyciu programu PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md). To doskonały sposób przypisywania ról kilkuset użytkownikom.
  
Aby przypisać role dziesiątkom użytkowników, skorzystaj z poniższych instrukcji.

## <a name="check-admin-roles-in-your-organization"></a>Sprawdzanie ról administratora w organizacji

Możesz nie mieć odpowiednich uprawnień do przypisywania ról administratora innym użytkownikom. Upewnij się, że masz odpowiednie uprawnienia, lub poproś innego administratora o przypisanie ról.

Uprawnienia roli administratora można sprawdzić na 2 różne sposoby:

- Możesz przejść do szczegółów użytkownika i wyszukać w obszarze **Role** na stronie **Konto** .
- Możesz też przejść do pozycji **Role** i wybrać rolę administratora, a następnie wybrać przypisanych administratorów, aby zobaczyć, którzy użytkownicy są przypisani.

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o rolach administratora platformy Microsoft 365](about-admin-roles.md) (artykuł)\
[Azure AD wbudowanych ról](/azure/active-directory/roles/permissions-reference) (artykuł)\
[Przypisywanie ról do kont użytkowników przy użyciu programu PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md) (artykuł)\
[Autoryzowanie lub usuwanie relacji z partnerami](../misc/add-partner.md) (artykuł)