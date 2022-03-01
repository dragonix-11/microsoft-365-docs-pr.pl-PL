---
title: Usuwanie licencji z udostępnionej skrzynki pocztowej
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
ms.reviewer: sinakassaw, nicholak
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
- AdminSurgePortfolio
- commerce_licensing
search.appverid:
- BCS160
- MET150
- MOE150
description: 'Usuń licencję z udostępnionej skrzynki pocztowej, aby przypisać ją do innego użytkownika lub zwrócić licencję, aby za nie nie płacić. '
ms.date: 05/11/2021
ms.openlocfilehash: 89e5e3023121bb4633d7c8c1e2f92fbecc5f3e18
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995924"
---
# <a name="remove-a-license-from-a-shared-mailbox"></a>Usuwanie licencji z udostępnionej skrzynki pocztowej

Udostępnione skrzynki pocztowe zazwyczaj nie wymagają licencji. Wykonaj poniższe instrukcje, aby usunąć licencję z udostępnionej skrzynki pocztowej, tak aby można było przypisać ją do użytkownika lub zwrócić licencję, aby nie płacić za licencję, która nie jest potrzebna.

> [!NOTE]
>
> Licencja Exchange Online Plan 2 jest wymagana w następujących scenariuszach:
>
> - W udostępnionej skrzynce pocztowej jest ponad 50 GB miejsca do magazynowania.
> - Udostępniona skrzynka pocztowa używa archiwizacji w miejscu.
> - Udostępniona skrzynka pocztowa jest umieszczana w postępowaniem sądowym.
> - Do udostępnionej skrzynki pocztowej jest Microsoft 365 Defender przypisana licencja.
> 
> Aby uzyskać instrukcje krok po kroku dotyczące przypisywania licencji, zobacz [Przypisywanie licencji użytkownikom](/microsoft-365/admin/manage/assign-licenses-to-users). 


## <a name="remove-the-license"></a>Odejmij licencję

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

   > [!NOTE]
   > Należy usunąć licencję ze strony Aktywni użytkownicy. Nie można usunąć licencji ze strony Udostępniona skrzynka pocztowa, ponieważ licencje są ustawieniami użytkownika.
  
2. Wybierz udostępnioną skrzynkę pocztową.

3. Na karcie **Licencje i aplikacje** rozwiń **pozycję** Licencje i wyczyść pole wyboru licencji, którą chcesz usunąć.

4. Wybierz **pozycję Zapisz zmiany**.

5. Po powrocie do strony **Aktywni użytkownicy** stan udostępnionej skrzynki pocztowej będzie miał stan **Nielicencjonowany**.

6. Nadal płacisz za licencję. Aby przestać za niego płacić, [usuń licencję z subskrypcji](../../commerce/licenses/buy-licenses.md).

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)
