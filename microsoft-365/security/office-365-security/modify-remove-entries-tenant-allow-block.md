---
title: Modyfikowanie i usuwanie wpisów na liście dozwolonych/zablokowanych dzierżaw
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak modyfikować i usuwać wpisy na liście dozwolonych/zablokowanych dzierżaw w portalu zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7da986c42421c797f2d01b1e61d50c06933e373f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64970936"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>Modyfikowanie i usuwanie wpisów na liście dozwolonych/zablokowanych dzierżaw

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Za pomocą portalu Microsoft 365 Defender lub programu PowerShell można modyfikować i usuwać wpisy na liście dozwolonych/zablokowanych dzierżaw.

## <a name="use-the-microsoft-365-defender-portal"></a>Korzystanie z portalu Microsoft 365 Defender

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>Modyfikowanie wpisów na liście dozwolonych/zablokowanych dzierżaw

1. W portalu Microsoft 365 Defender przejdź **do sekcji** **Zasady & reguły zasad** \> **zagrożeń** \> w sekcji \> **Zezwalaj/blokuj listy dzierżawy**.

2. Wybierz kartę zawierającą typ wpisu, który chcesz zmodyfikować:
   - **Nadawców**
   - **Fałszowanie**
   - **Adresy url**
   - **Pliki**

3. Wybierz wpis, który chcesz zmodyfikować, a następnie kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**. Wartości, które można zmodyfikować w wyświetlonym wysuwie, zależą od karty wybranej w poprzednim kroku:
   - **Nadawców**
     - **Nigdy nie wygasaj** i/lub nie wygasaj.
     - **Uwaga opcjonalna**
   - **Fałszowanie**
     - **Akcja**: możesz zmienić wartość **na Zezwalaj** lub **Blokuj**.
   - **Adresy url**
     - **Nigdy nie wygasaj** i/lub nie wygasaj.
     - **Uwaga opcjonalna**
   - **Pliki**
     - **Nigdy nie wygasaj** i/lub nie wygasaj.
     - **Uwaga opcjonalna**

4. Po zakończeniu kliknij przycisk **Zapisz**.

> [!NOTE]
> Można rozszerzyć zezwala tylko na maksymalnie 30 dni od daty utworzenia. Bloki można przedłużyć o maksymalnie 90 dni, ale w przeciwieństwie do opcji zezwalania można je również ustawić na wartość Nigdy nie wygasają.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>Usuwanie wpisów z listy dozwolonych/zablokowanych dzierżaw

1. W portalu Microsoft 365 Defender przejdź **do sekcji** **Zasady & reguły zasad** \> **zagrożeń** \> w sekcji \> **Zezwalaj/blokuj listy dzierżawy**.

2. Wybierz kartę zawierającą typ wpisu, który chcesz usunąć:
   - **Nadawców**
   - **Fałszowanie**
   - **Adresy url**
   - **Pliki**

3. Wybierz wpis, który chcesz usunąć, a następnie kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

4. W wyświetlonym oknie dialogowym ostrzeżenia kliknij pozycję **Usuń**.

## <a name="use-powershell"></a>Korzystanie z programu PowerShell

### <a name="modify-allow-or-block-sender-file-and-url-entries-in-the-tenant-allowblock-list"></a>Modyfikowanie pozycji zezwalania lub blokowania nadawcy, pliku i adresu URL na liście zezwalania/blokowania dzierżawy

Aby zmodyfikować wpisy zezwalania, pliku i adresu URL nadawcy, pliku i adresu URL na liście dozwolonych/zablokowanych dzierżaw, użyj następującej składni:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Ten przykład zmienia datę wygaśnięcia określonego wpisu adresu URL bloku.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-allow-or-block-sender-url-or-file-entries-from-the-tenant-allowblock-list"></a>Usuwanie dozwolonych lub zablokowanych wpisów nadawcy, adresu URL lub pliku z listy dozwolonych/zablokowanych dzierżaw

Aby usunąć wpisy zezwalania, pliku i adresu URL nadawcy, pliku i adresu URL z listy dozwolonych/zablokowanych dzierżaw, użyj następującej składni:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

W tym przykładzie usunięto określony wpis adresu URL bloku z listy dozwolonych/zablokowanych dzierżaw.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Modyfikowanie pozycji dozwolonych lub zablokowanych fałszywych nadawców z listy dozwolonych/zablokowanych dzierżaw

Aby zmodyfikować wpisy nadawcy dozwolonych lub zablokowanych na liście dozwolonych/zablokowanych dzierżawców, użyj następującej składni:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

Ten przykład zmienia sfałszowany wpis nadawcy z opcji zezwalania na blokowanie.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Usuń wpisy nadawcy zezwalającego na fałszowanie lub blokuj je z listy dozwolonych/zablokowanych dzierżaw

Aby usunąć wpisy nadawcy zezwalania na fałszowanie lub blokować je z listy dozwolonych/zablokowanych dzierżaw, użyj następującej składni:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
