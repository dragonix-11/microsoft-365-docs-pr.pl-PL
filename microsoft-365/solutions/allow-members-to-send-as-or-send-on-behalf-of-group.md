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
description: Dowiedz się, jak zezwolić członkom grupy na wysyłanie wiadomości e-mail Microsoft 365 grupy lub wysyłanie wiadomości e-mail w imieniu Microsoft 365 grupy.
ms.openlocfilehash: e3742b645d1efb2acb4bd14d109314947d781246
ms.sourcegitcommit: b6676f2dd7c42b0b5eb3ca2790b13e10177a5758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2022
ms.locfileid: "62974003"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Zezwalanie członkom na wysyłanie jako grupa lub w jej imieniu

Członek grupy grupy usługi Microsoft 365, który otrzymał uprawnienia Wyślij jako lub Wyślij  w imieniu,  może wysyłać wiadomości e-mail jako grupa lub w imieniu tej grupy. (Gościom w grupie nie można przyznać tych uprawnień).

W tym artykule wyjaśniono, jak administrator globalny Exchange może ustawić te uprawnienia.
  
Jeśli na przykład Megan Bowen należy do grupy **Szkolenie Microsoft 365 i** ma uprawnienia Wyślij jako do grupy,  jeśli wyśle wiadomość e-mail jako grupa, będzie ona wyglądać tak, jakby grupa Szkolenie wysłała wiadomość e-mail. 
  
Uprawnienie **Wyślij w imieniu** umożliwia użytkownikowi wysyłanie wiadomości e-mail w imieniu Microsoft 365 grupy. Jeśli na przykład Alex Wilber należy do grupy **Marketing** Microsoft 365 i ma uprawnienia Wyślij w imieniu oraz wysyła wiadomość e-mail jako grupa, wygląda na to, że została wysłana przez **Alexa Wilbera** w imieniu marketingowym.

> [!IMPORTANT]
> Dla danego użytkownika **możesz** skonfigurować opcje  Wyślij jako lub Wyślij w imieniu danego użytkownika, ale nie oba te opcje. Jeśli skonfigurujesz oba te ustawienia, domyślnie będzie to **opcja Wyślij jako**.

> [!NOTE]
> **W przypadku** usługi **Wyślij jako i Wyślij w imieniu** nie Outlook dla komputerów Mac w hybrydowych Exchange hybrydowych.
    
## <a name="allow-members-to-send-email-as-a-group"></a>Zezwalanie członkom na wysyłanie wiadomości e-mail jako grupa

W tej sekcji wyjaśniono, jak umożliwić użytkownikom wysyłanie wiadomości e-mail jako<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a> grupy w centrum administracyjnym usługi Exchange w programie Exchange Online.
  
1. W centrum Exchange przejdź do pozycji **Grupy adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. Wybierz **ikonę grupy EditEdit**  ![.](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) w grupie, jako której użytkownicy mają być wysyłani. 
    
3. Wybierz **delegowanie grupy**.
    
4. W **sekcji Wyślij jako** wybierz znak **+** , aby dodać użytkowników, których chcesz wysłać jako grupę. 
    
    ![Zrzut ekranu przedstawiający okno dialogowe Wyślij jako.](../media/1df167f6-1eff-4f98-9ecd-4230fab46557.png)
  
5. Wpisz tekst, aby wyszukać użytkownika lub wybrać użytkownika z listy. Wybierz **przycisk OK** i **pozycję Zapisz**.
    
    ![Wpisz tekst, aby wyszukać użytkownika lub wybrać użytkownika z listy.](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)
  
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Zezwalanie członkom na wysyłanie wiadomości e-mail w imieniu grupy

W tej sekcji wyjaśniono, jak zezwolić użytkownikom na wysyłanie wiadomości e-mail w imieniu grupy w centrum administracyjnym programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange w</a> programie Exchange Online.
  
1. W centrum Exchange przejdź do pozycji **Grupy adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. Wybierz **ikonę** ![Edytuj grupę.](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) w grupie, jako której użytkownicy mają być wysyłani. 
    
3. Wybierz **delegowanie grupy**.
    
4. W sekcji Wyślij w imieniu wybierz znak **+** , aby dodać użytkowników, których chcesz wysłać jako grupę. 
    
    ![Zrzut ekranu przedstawiający wysyłanie w imieniu okna dialogowego.](../media/2bae0579-8907-4d6b-8920-ddd6555897b4.png)
  
5. Wpisz tekst, aby wyszukać użytkownika lub wybrać użytkownika z listy. Wybierz **przycisk OK** i **pozycję Zapisz**.
    
    ![Wpisz tekst, aby wyszukać użytkownika lub wybrać użytkownika z listy.](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)

## <a name="related-articles"></a>Artykuły pokrewne

[Wysyłanie wiadomości e-mail w imieniu Microsoft 365 grupy](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Dowiedz się więcej o Microsoft 365 grup](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission)

[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup)
