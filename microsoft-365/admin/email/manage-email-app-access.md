---
title: Zarządzanie dostępem do aplikacji poczty e-mail w aplikacji centrum administracyjne platformy Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
ms.assetid: d00b6b83-1f14-4e9c-a2c5-dbd9a92816f4
ROBOTS: NOINDEX, NOFOLLOW
description: Dowiedz się, jak wybrać aplikacje mobilne, za pomocą których inne osoby mogą uzyskać dostęp do poczty e-mail, kalendarza i kontaktów.
ms.openlocfilehash: e3a7999900e85bde1bee7bf220b46a74a1151f57
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017754"
---
# <a name="manage-email-app-access-in-the-microsoft-365-admin-center"></a>Zarządzanie dostępem do aplikacji poczty e-mail w centrum administracyjne platformy Microsoft 365

Za pomocą ustawień dostępu mobilnego do poczty e-mail możesz wybrać, które aplikacje mobilne osoby w Twojej organizacji mogą używać do uzyskiwania dostępu do konta służbowego w celu uzyskiwania dostępu do poczty e-mail, kalendarza i kontaktów.
  
> [!IMPORTANT]
> Twoja organizacja będzie mieć dostęp do tego ustawienia, chyba że używasz programu Microsoft Intune lub ustawienia zarządzania urządzeniami przenośnymi zostały skonfigurowane w centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange.</a> 
  
## <a name="manage-email-app-options"></a>Zarządzanie opcjami aplikacji poczty e-mail

> [!IMPORTANT]
>  Jeśli nie będziesz korzystać z tej funkcji, zmiany w obsłudze użytkowników nie będą się zmieniać. Za pomocą dowolnej aplikacji mobilnej do poczty e-mail będzie mógł uzyskać dostęp do swojego konta służbowego do poczty e-mail, kalendarza i kontaktów z urządzenia przenośnego. 
    
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Usługi &amp; Dodatki</a>. 

2. Na stronie **Opcji dostępu do poczty e-mail** na urządzeniach przenośnych zaznacz pole wyboru, a następnie wybierz sposób używania aplikacji poczty e-mail przez użytkowników w organizacji na swoich urządzeniach:
  
Wybieranie opcji ustawienia sposobu, w jaki użytkownicy w organizacji uzyskają dostęp do swoich kont służbowych za pomocą urządzeń przenośnych
  
- **Outlook —** użytkownicy w Twojej organizacji będą zobowiązani do korzystania z aplikacji Outlook dla systemu Android lub aplikacji Outlook dla systemu iOS na swoich urządzeniach przenośnych. 
    
- **Dowolna aplikacja poczty** e-mail — wszyscy użytkownicy w organizacji będą monitować o korzystanie z usługi Outlook, ale mogą używać dowolnej aplikacji poczty e-mail. 
    
- **Dowolna aplikacja poczty** e-mail — nowi użytkownicy lub urządzenia w Twojej organizacji zostaną raz wyświetleniu monitu o korzystanie z usługi Outlook, ale mogą oni używać dowolnej aplikacji poczty e-mail. 
    
Aby uzyskać więcej szczegółowych informacji, zobacz [Opcje uzyskiwania dostępu do poczty e-mail z urządzenia przenośnego](access-email-from-a-mobile-device.md).
  
## <a name="new-user-or-device-is-activated-in-your-organization"></a>W Twojej organizacji aktywowano nowego użytkownika lub urządzenie

Gdy tylko użytkownik w Twojej organizacji doda służbowy lub szkolny adres e-mail do aplikacji poczty e-mail innej firmy lub do nowego urządzenia, otrzyma wiadomość e-mail od firmy Microsoft w imieniu **Twojej organizacji**. Wiadomość e-mail zawiera informacje o zaletach korzystania z aplikacji mobilnej Outlook i będzie zawierała link do lokalizacji pobierania. Użytkownicy mogą wówczas zdecydować, czy nadal korzystać z aplikacji innej firmy, czy z aplikacji Outlook mobilnej. W ciągu 24 godzin od otrzymania tej wiadomości e-mail przez użytkownika urządzenie zostanie poddane kwarantannie, a wiadomości e-mail, kalendarz i dane kontaktowe nie będą aktualizowane. Jeśli zdecyduje się na korzystanie z Outlook mobilnej, aplikacja innej firmy pozostanie pod kwarantanną, a dane będą synchronizowane tylko z aplikacją mobilną Outlook przenośnych. Jeśli zaczną oni nadal korzystać z aplikacji innej firmy, dane zaczną być synchronizowane natychmiast. Jeśli w ciągu tych pierwszych 24 godzin nie zostanie wykonane żadne działanie, wiadomość e-mail zostanie usunięta ze skrzynki odbiorczej tej osoby i dane z serwera zaczną być synchronizowane automatycznie.
  
## <a name="previously-configured-users-in-your-organization"></a>Wcześniej skonfigurowani użytkownicy w organizacji

Jeśli zdecydujesz się polecić usługę Outlook wszystkim osobom w organizacji, oprócz opisanej powyżej funkcji dla nowych użytkowników użytkownicy, którzy wcześniej połączyli swoje służbowe konto e-mail z aplikacją innej firmy, otrzymają wiadomość e-mail od firmy **Microsoft** w imieniu Twojej organizacji w ciągu 48 godzin od włączeniu tego ustawienia. Wiadomość e-mail zawiera informacje o zaletach korzystania z aplikacji mobilnej Outlook i będzie zawierała link do lokalizacji pobierania. Użytkownicy mogą wówczas zdecydować, czy nadal korzystać z aplikacji innej firmy, czy z aplikacji Outlook mobilnej. W ciągu 24 godzin od otrzymania tej wiadomości e-mail przez użytkownika urządzenie zostanie poddane kwarantannie, a wiadomości e-mail, kalendarz i dane kontaktowe nie będą aktualizowane. Jeśli zdecyduje się na korzystanie z Outlook mobilnej, aplikacja innej firmy pozostanie pod kwarantanną, a dane będą synchronizowane tylko z aplikacją mobilną Outlook przenośnych. Jeśli zaczną oni nadal korzystać z aplikacji innej firmy, dane zaczną być synchronizowane natychmiast. Jeśli w ciągu tych pierwszych 24 godzin nie zostanie wykonane żadne działanie, wiadomość e-mail zostanie usunięta ze skrzynki odbiorczej tej osoby i dane z serwera zaczną być synchronizowane automatycznie. 
  

