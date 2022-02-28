---
title: Modyfikowanie i usuwanie wpisów na liście zezwalania/blokowania dzierżawy
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
description: Administratorzy mogą dowiedzieć się, jak modyfikować i usuwać wpisy na liście zezwalania/blokowania dzierżawy w portalu zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f2662ac41e5df5cf2eb36413d8a58568ff336841
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988436"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>Modyfikowanie i usuwanie wpisów na liście zezwalania/blokowania dzierżawy

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Za pomocą portalu Microsoft 365 Defender lub programu PowerShell można modyfikować i usuwać wpisy na liście zezwalania/blokowania dzierżawy.

## <a name="use-the-microsoft-365-defender-portal"></a>Korzystanie z Microsoft 365 Defender a

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>Modyfikowanie wpisów na liście zezwalania/blokowania dzierżawy

1. W portalu Microsoft 365 Defender przejdź do **sekcji Zasady i reguły &** \>  \> reguły **zagrożeń w sekcji** \> Listy zezwalania **i blokowania** dzierżaw.

2. Wybierz kartę zawierającą typ wpisu, który chcesz zmodyfikować:
   - **Nadawcy)
   - **Adresy URL**
   - **Pliki**
   - **Fałszowanie**

3. Zaznacz wpis, który chcesz zmodyfikować, a następnie kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**. Wartości, które można modyfikować w wysuwanych menu wysuwanych, zależą od karty wybranej w poprzednim kroku:
   - **Nadawcy**
     - **Nigdy nie wygasają** ani nie wygasają.
     - **Uwaga opcjonalna**
   - **Adresy URL**
     - **Nigdy nie wygasają** ani nie wygasają.
     - **Uwaga opcjonalna**
   - **Pliki**
     - **Nigdy nie wygasają** ani nie wygasają.
     - **Uwaga opcjonalna**
   - **Fałszowanie**
     - **Akcja**: Możesz zmienić wartość na **Zezwalaj lub** **Zablokuj**.
4. Po zakończeniu kliknij przycisk **Zapisz**.

> [!NOTE]
> Okres ważności można wydłużyć tylko do 30 dni od daty utworzenia. Okres ważności bloków może zostać wydłużony do 90 dni, ale w przeciwieństwie do zezwalania, można dla nich również ustawić opcję Nigdy nie wygasają.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>Usuwanie wpisów z listy zezwalania/blokowania dzierżawy

1. W portalu Microsoft 365 Defender przejdź do **sekcji Zasady i reguły &** \>  \> reguły **zagrożeń w sekcji** \> Listy zezwalania **i blokowania** dzierżaw.

2. Wybierz kartę zawierającą typ wpisu, który chcesz usunąć:
   - **Nadawcy**
   - **Adresy URL**
   - **Pliki**
   - **Fałszowanie**

3. Zaznacz wpis, który chcesz usunąć, a następnie kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń**.

4. W wyświetlonym oknie dialogowym z ostrzeżeniem kliknij pozycję **Usuń**.

## <a name="use-powershell"></a>Używanie programu PowerShell

### <a name="modify-block-file-and-url-entries-in-the-tenant-allowblock-list"></a>Modyfikowanie wpisów pliku blokowego i adresu URL na liście zezwalania/blokowania dzierżawy

Aby zmodyfikować wpisy zablokowanych nadawców, plików i adresów URL na liście zezwalania/blokowania dzierżawy, użyj następującej składni:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

W tym przykładzie jest zmieniana data wygaśnięcia określonego wpisu w adresie URL bloku.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-url-or-file-entries-from-the-tenant-allowblock-list"></a>Usuwanie adresu URL lub wpisów plików z listy zablokowanych/zezwalanych dzierżaw

Aby usunąć wpisy nadawcy, pliku i adresu URL z listy zablokowanych/zezwalanych na dzierżawę, użyj następującej składni:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

W tym przykładzie usuwany jest określony wpis adresu URL bloku z listy adresów zezwalania/blokowania dzierżawy.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries"></a>Modyfikowanie zezwalania lub blokowania fałszywych wpisów nadawców

Aby zmodyfikować pozycje zezwalania lub blokowania fałszywych nadawców na liście zezwalania/blokowania dzierżawy, użyj następującej składni:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

W tym przykładzie zmienia się sfałszowany wpis nadawcy z zezwalania na zablokowanie.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries"></a>Usuwanie zezwalania lub blokowania fałszywych wpisów nadawców

Aby usunąć zezwalanie lub blokowanie wpisów nadawców podszywające się pod nadawców z listy zablokowanych/zezwalanych na dzierżawę, użyj następującej składni:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
