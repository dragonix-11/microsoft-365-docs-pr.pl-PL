---
title: Wysyłanie wiadomości e-mail jako listy dystrybucyjnej
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
- Adm_O365
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a7c98273-067e-4162-b3a1-4ba081796012
description: Wyślij wiadomość e-mail jako listę dystrybucyjną w Microsoft 365, aby gdy członek odpowiada na wiadomość, wydaje się, że pochodzi z listy dystrybucyjnej.
ms.openlocfilehash: dd6e1f906481fe1c04bfa7cd275bd108ab558d59
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468465"
---
# <a name="send-microsoft-365-email-as-a-distribution-list"></a>Wysyłanie Microsoft 365 wiadomości e-mail jako listy dystrybucyjnej

W Microsoft 365 możesz wysłać wiadomość e-mail jako listę dystrybucyjną. Gdy osoba będąca członkiem listy dystrybucyjnej odpowiada na wiadomość wysłaną do listy dystrybucyjnej, wiadomość e-mail wydaje się pochodzić z listy dystrybucyjnej, a nie od pojedynczego użytkownika. W tym temacie pokazano, jak to zrobić.
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed wykonaniem tych kroków upewnij się, że dodano Cię do Microsoft 365 listy dystrybucyjnej i masz przyznane uprawnienie Wyślij jako uprawnienie do tej listy.
  
 **Administratorzy**: upewnij się, że wykonaliśmy kroki opisane w temacie [Dodawanie Microsoft 365 użytkownika lub kontaktu do listy](../email/add-user-or-contact-to-distribution-list.md) i [Zezwalaj członkom na wysyłanie wiadomości e-mail jako tematów grupy Microsoft 365](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md#allow-members-to-send-email-as-a-group) i dodają odpowiednie osoby do listy dystrybucyjnej.
  
## <a name="outlook-on-the-web"></a>Outlook on the web

1. Otwórz Outlook w sieci Web i przejdź do skrzynki odbiorczej. 
    
2. Otwórz komunikat, który został wysłany do listy dystrybucyjnej. 
    
3. Wybierz pozycję **Odpowiedz**. 
    
4. W dolnej części wiadomości wybierz pozycję **Więcej** \> **pokaż.**<br/> ![Wybierz pozycję Więcej, a następnie wybierz pozycję Pokaż z.](../../media/534f13b7-9f15-48ea-8835-ea2ed1863ece.png)
  
5. Kliknij prawym przyciskiem myszy pozycję Z adresu — na przykład `Ina@weewalter.me` — i wybierz pozycję **Usuń**.<br/> ![Remove the FROM alias.](../../media/9b8d8e8f-dc46-499c-89bd-0a480603bf1f.png)
  
6. Następnie wpisz adres listy dystrybucyjnej, taki jak support@contoso.com, i wyślij wiadomość. Gdy następnym razem odpowiesz z listy dystrybucyjnej, jej adres będzie wyświetlany jako opcja na liście **Od** .<br/>![Zostanie wyświetlony alias udostępnionej skrzynki pocztowej.](../../media/f7632a9a-9cab-446c-9e37-23ef50c5b975.png)

## <a name="outlook"></a>Outlook

1. Otwórz klienta Outlook desktop.

2. Utwórz nową wiadomość e-mail. Kliknij pole **Od** i wybierz pozycję **Inny adres e-mail**. Jeśli nie widzisz pola Od, przejdź do pozycji **Opcje** i wybierz pozycję **Od** w sekcji Pokaż pola.

3. Wybierz adres **listy dystrybucyjnej** z globalnej listy adresów.

4. Wyślij wiadomość e-mail.

## <a name="related-content"></a>Zawartość pokrewna

[Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń w Centrum administracyjne platformy Microsoft 365](../email/create-edit-or-delete-a-security-group.md) (artykuł)\
[Współpraca w wiadomościach e-mail](../email/email-collaboration.md) (artykuł)\
[Dodawanie użytkownika lub kontaktu do grupy dystrybucyjnej](../email/add-user-or-contact-to-distribution-list.md) (artykuł)