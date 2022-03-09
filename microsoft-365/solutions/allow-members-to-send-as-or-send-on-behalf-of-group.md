---
title: Zezwalanie członkom na wysyłanie jako grupa lub w jej imieniu
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
- m365solution-collabgovernance
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MET150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
recommendations: false
description: Dowiedz się, jak zezwolić członkom grupy na wysyłanie wiadomości e-mail Microsoft 365 grupy grupowej lub wysyłanie wiadomości e-mail w imieniu Microsoft 365 grupy.
ms.openlocfilehash: 588008669359629f5b59498bb7dbf776112d5408
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401010"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Zezwalanie członkom na wysyłanie jako grupa lub w jej imieniu

Członek grupy grupy Microsoft 365, który otrzymał uprawnienia Wyślij jako lub Wyślij  w imieniu może  wysyłać wiadomości e-mail jako grupa lub w imieniu tej grupy. (Gościom w grupie nie można przyznać tych uprawnień).

W tym artykule wyjaśniono, jak administrator globalny Exchange może ustawić te uprawnienia.
  
Jeśli na przykład Megan Bowen należy do grupy **Szkolenie Microsoft 365 i** ma uprawnienia Wyślij jako do grupy, jeśli  wyśle wiadomość e-mail jako grupa, będzie ona wyglądać tak, jakby grupa Szkolenie wysłała wiadomość e-mail. 
  
Uprawnienie **Wyślij w imieniu** umożliwia użytkownikowi wysyłanie wiadomości e-mail w imieniu Microsoft 365 grupy. Jeśli na przykład Alex Wilber należy do grupy **Marketing** Microsoft 365 i ma uprawnienia Wyślij w imieniu oraz wysyła wiadomość e-mail jako grupa, wygląda na to, że została wysłana przez **Alexa Wilbera** w imieniu marketingowym.

> [!IMPORTANT]
> Dla danego użytkownika **możesz** skonfigurować opcje  Wyślij jako lub Wyślij w imieniu danego użytkownika, ale nie oba te opcje. Jeśli skonfigurujesz oba te ustawienia, domyślnie będzie to **opcja Wyślij jako**.

> [!NOTE]
> **W konfiguracjach** **hybrydowych usługi** Wyślij jako i Wyślij w imieniu nie Outlook dla komputerów Mac w Exchange hybrydowych.
    
## <a name="allow-members-to-send-email-as-a-group"></a>Zezwalanie członkom na wysyłanie wiadomości e-mail jako grupa

W tej sekcji wyjaśniono, jak umożliwić użytkownikom wysyłanie wiadomości e-mail jako grupy w centrum administracyjnym usługi Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">w</a> programie Exchange Online.
  
1. W centrum Exchange przejdź do **pozycji Grupy adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. Wybierz grupę, jako której chcesz zezwolić użytkownikom na wysyłanie. 
    
3. Wybierz **Ustawienia** >  **Edytuj zarządzanie pełnomocnikami**.
    
4. W **sekcji Dodaj pełnomocnika** wprowadź adres e-mail użytkownika, który ma mieć dostęp **Wyślij jako** .
  
5. Z **listy rozwijanej** wybierz pozycję Typ uprawnień **jako** Wyślij jako.

6.  Wybierz **pozycję Zapisz zmiany**.
    
    
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Zezwalanie członkom na wysyłanie wiadomości e-mail w imieniu grupy

W tej sekcji wyjaśniono, jak zezwolić użytkownikom na wysyłanie wiadomości e-mail w imieniu grupy w centrum administracyjnym programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange w</a> programie Exchange Online.
  
1. W centrum Exchange przejdź do **pozycji Grupy adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. Wybierz grupę, w imieniu której chcesz zezwolić użytkownikom na wysyłanie wiadomości. 
    
3. Wybierz **Ustawienia** >  **Edytuj zarządzanie pełnomocnikami**.
    
4. W **sekcji Dodaj pełnomocnika** wprowadź adres e-mail użytkownika, który ma mieć dostęp **Wyślij jako** .
  
5. Z **listy rozwijanej** wybierz pozycję Typ uprawnień **jako** Wyślij w imieniu.

6.  Wybierz **pozycję Zapisz zmiany**.

## <a name="related-articles"></a>Artykuły pokrewne

[Wysyłanie wiadomości e-mail z grupy Microsoft 365 lub w jej imieniu](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Dowiedz się więcej o Microsoft 365 grup](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission)

[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup)
