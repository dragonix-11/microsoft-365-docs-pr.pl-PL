---
title: Zarządzanie grupą w centrum administracyjnym
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 74a1ef8b-3844-4d08-9980-9f8f7a36000f
description: Dowiedz się, Microsoft 365 grupy grupy, w tym dodawanie usuwania członków grupy, edytowanie adresu e-mail, nazwy grupy lub opisu oraz dostosowywanie sposobu działania grupy.
ms.openlocfilehash: e04d91219f1bfd51b609b9be749bd98c2798a52a
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63015972"
---
# <a name="manage-a-group-in-the-microsoft-365-admin-center"></a>Zarządzanie grupą w centrum administracyjne platformy Microsoft 365

Po [utworzeniu grupy Microsoft 365 i](create-groups.md) dodaniu jej członków możesz ją skonfigurować. Możesz edytować nazwę lub opis grupy, zarządzać właścicielami lub członkami grupy oraz określać, czy nadawcy zewnętrzni mogą wysyłać wiadomości e-mail do grupy i czy wysyłać kopie konwersacji grupowych do członków.

Przejdź do centrum administracyjne platformy Microsoft 365 stronie [https://admin.microsoft.com](https://admin.microsoft.com).

## <a name="edit-the-group-name-or-description"></a>Edytowanie nazwy lub opisu grupy

1. W centrum administracyjnym rozwiń pozycję **Grupy**, a następnie kliknij pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a>.

2. Zaznacz grupę, którą chcesz edytować, a następnie kliknij pozycję **Edytuj nazwę i opis**.

3. Zaktualizuj nazwę i opis, a następnie wybierz pozycję **Zapisz**.

## <a name="manage-group-owners-and-members"></a>Zarządzanie właścicielami i członkami grupy

1. W centrum administracyjnym rozwiń pozycję **Grupy**, a następnie kliknij pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a>.

2. Kliknij nazwę grupy, którą chcesz zarządzać, aby otworzyć okienko ustawień.

3. Na karcie **Członkowie** wybierz, czy chcesz zarządzać właścicielami, czy członkami.

4. Wybierz **pozycję Dodaj** , aby dodać osobę, lub **kliknij pozycję X** , aby ją usunąć.

5. Kliknij przycisk **Zamknij**.

## <a name="send-copies-of-conversations-to-group-members-inboxes"></a>Wysyłanie kopii konwersacji do skrzynek pocztowych członków grupy
  
Podczas tworzenia grupy przy użyciu centrum administracyjnego użytkownicy domyślnie nie są otrzymywać kopii wiadomości e-mail grupy wysyłanych do ich skrzynek pocztowych, ale użytkownicy są otrzymywać kopie zaproszeń na spotkania grupy wysyłanych do swoich skrzynek pocztowych. Aby wyświetlić konwersacje, musi przejść do grupy. To ustawienie można zmienić w centrum administracyjnym.

Po włączeniu tego ustawienia członkowie grupy będą otrzymywać kopie wiadomości e-mail i zaproszeń na spotkania grupy wysyłane do ich Outlook Odbiorczej. Mogą oni odczytać i usunąć tę kopię wiadomości e-mail, ponieważ nie ma to wpływu na inne osoby. Kopia wiadomości e-mail nadal istnieje w skrzynce odbiorczej grupy.

Członkowie grupy mogą zrezygnować z otrzymywania tych wiadomości e-mail, wybierając opcję zatrzymania trzymywania grupę w Outlook.

1. W centrum administracyjnym rozwiń pozycję **Grupy**, a następnie kliknij pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a>.

2. Kliknij nazwę grupy, którą chcesz zarządzać, aby otworzyć okienko ustawień.

3. Na karcie **Ustawienia** wybierz pozycję Wysyłaj kopie konwersacji i zdarzeń grupowych do członków grupy, jeśli chcesz, aby członkowie o różnych kopiach wiadomości i elementów kalendarza grupy o różnych skrzynkach odbiorczych os.

4. Wybierz **Zapisz**.

## <a name="let-people-outside-the-organization-email-the-group"></a>Umożliwianie osobom spoza organizacji wysyłanie wiadomości e-mail do grupy

Ta opcja jest bardzo doskonała, jeśli chcesz mieć firmowy adres e-mail, taki jak adres e-mail info@contoso.com.
 
1. W centrum administracyjnym rozwiń pozycję **Grupy**, a następnie kliknij pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a>.

2. Kliknij nazwę grupy, którą chcesz zarządzać, aby otworzyć okienko ustawień.

3. Na liście grup w centrum administracyjnym wybierz nazwę grupy, którą chcesz zmienić, a następnie na karcie Grupy **Ustawienia** wybierz pozycję Zezwalaj nadawcom zewnętrznym na wysyłanie wiadomości e-mail **do tej grupy**.
    
4. Wybierz **Zapisz**.

> [!NOTE]
> Wysyłanie wiadomości e-mail do grupy przez użytkowników spoza organizacji może potrwać do 30 minut.

## <a name="permanently-delete-a-microsoft-365-group"></a>Trwałe usuwanie grupy Microsoft 365 grupy

Czasami może być chcieć trwale usunąć grupę, nie czekając na wygaśnięcie 30-dniowego okresu "miękkiego usunięcia". W tym celu uruchom program PowerShell i uruchom następujące polecenie, aby uzyskać identyfikator obiektu grupy:
 
 ```powershell
Get-AzureADMSDeletedGroup
```

Zanotuj identyfikator obiektu grup, które chcesz trwale usunąć.
  
> [!CAUTION]
> Trwałe usunięcie grupy spowoduje usunięcie grupy i jej danych na zawsze. 
  
Aby trwale usunąć grupę, uruchom następujące polecenie w programie PowerShell:

```powershell
Remove-AzureADMSDeletedDirectoryObject -Id <objectId>
```

Aby sprawdzić, czy grupa została pomyślnie usunięta, uruchom ponownie polecenie  *Get-AzureADMSDeletedGroup*  i upewnij się, że grupa nie jest już widoczna na liście grup poddanych „miękkiemu usunięciu". W niektórych przypadkach trwałe usunięcie grupy i wszystkich jej danych może potrwać nawet 24 godziny. 
  
## <a name="related-articles"></a>Artykuły pokrewne

[Tworzenie grupy Microsoft 365 grupy](create-groups.md)

[Zarządzanie dostępem gości do grup Microsoft 365 grupy](https://support.microsoft.com/office/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Wybieranie domeny do użycia podczas tworzenia grup Microsoft 365 grupy](../../solutions/choose-domain-to-create-groups.md)

[Zezwalanie członkom na wysyłanie jako grupa lub w imieniu Microsoft 365 grupy](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md)

[Uaktualnianie list dystrybucyjnych do Microsoft 365 grup](../manage/upgrade-distribution-lists.md)

[Zarządzanie grupami Microsoft 365 za pomocą programu PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md)
