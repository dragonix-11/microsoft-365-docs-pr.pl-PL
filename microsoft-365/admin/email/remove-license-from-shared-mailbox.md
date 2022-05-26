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
- commerce_licensing
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: 'Usuń licencję ze udostępnionej skrzynki pocztowej, aby przypisać ją innemu użytkownikowi lub zwrócić licencję, aby nie płacić za nią. '
ms.date: 04/22/2022
ms.openlocfilehash: 5248c7fdb807a91ab2a9a7dfd44bdb375eb7d0f0
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65678925"
---
# <a name="remove-a-license-from-a-shared-mailbox"></a>Usuwanie licencji z udostępnionej skrzynki pocztowej

Udostępnione skrzynki pocztowe zwykle nie wymagają licencji. Postępuj zgodnie z tymi instrukcjami, aby usunąć licencję ze udostępnionej skrzynki pocztowej, aby można było przypisać ją do użytkownika lub zwrócić licencję, aby nie płacić za licencję, której nie potrzebujesz.

> [!NOTE]
>
> Licencja Exchange Online Plan 2 jest wymagana w następujących scenariuszach:
>
> - Udostępniona skrzynka pocztowa ma ponad 50 GB magazynu w użyciu.
> - Udostępniona skrzynka pocztowa używa archiwizacji w miejscu.
> - Udostępniona skrzynka pocztowa jest umieszczana w blokadzie sądowej.
> 
> Aby uzyskać instrukcje krok po kroku dotyczące przypisywania licencji, zobacz [Przypisywanie licencji do użytkowników](/microsoft-365/admin/manage/assign-licenses-to-users). 


## <a name="remove-the-license"></a>Usuwanie licencji

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>.

::: moniker-end

   > [!NOTE]
   > Musisz usunąć licencję ze strony Aktywni użytkownicy. Nie można usunąć licencji ze strony Udostępniona skrzynka pocztowa, ponieważ licencje są ustawieniami użytkownika.
  
2. Wybierz udostępnioną skrzynkę pocztową.

3. Na **karcie Licencje i aplikacje** rozwiń węzeł **Licencje** i usuń zaznaczenie pola wyboru licencji, którą chcesz usunąć.

4. Wybierz pozycję **Zapisz zmiany**.

5. Po powrocie do strony **Aktywni użytkownicy** stan udostępnionej skrzynki pocztowej będzie **nielicencjonowany**.

6. Nadal płacisz za licencję. Aby przestać za to płacić, [usuń licencję z subskrypcji](../../commerce/licenses/buy-licenses.md).

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi](resolve-issues-with-shared-mailboxes.md) (artykuł)
