---
title: Zarządzanie dostępem do aplikacji poczty e-mail w Centrum administracyjne platformy Microsoft 365
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
description: Dowiedz się, jak wybrać aplikacje mobilne, których użytkownicy mogą używać do uzyskiwania dostępu do poczty e-mail, kalendarza i kontaktów.
ms.openlocfilehash: 5f5a96a0ac44757cfe168db87deb494019759c36
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780242"
---
# <a name="manage-email-app-access-in-the-microsoft-365-admin-center"></a>Zarządzanie dostępem do aplikacji poczty e-mail w Centrum administracyjne platformy Microsoft 365

Użyj ustawień dostępu do mobilnej poczty e-mail, aby wybrać aplikacje mobilne, których użytkownicy w organizacji mogą używać do uzyskiwania dostępu do konta służbowego w celu uzyskania dostępu do poczty e-mail, kalendarza i kontaktów.
  
> [!IMPORTANT]
> Twoja organizacja będzie miała dostęp do tego ustawienia, chyba że używasz Microsoft Intune lub skonfigurowano ustawienia zarządzania urządzeniami przenośnymi w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>.
  
## <a name="manage-email-app-options"></a>Zarządzanie opcjami aplikacji poczty e-mail

> [!IMPORTANT]
> Jeśli nie używasz tej funkcji, nie będzie żadnych zmian w środowisku użytkowników. Będą oni mogli korzystać z dowolnej mobilnej aplikacji poczty e-mail w celu uzyskania dostępu do konta służbowego na potrzeby poczty e-mail, kalendarza i kontaktów z urządzenia przenośnego.

1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Usługi &amp; Dodatki</a>.

2. Na stronie **Opcje dostępu do poczty e-mail dla urządzeń przenośnych** zaznacz pole wyboru, a następnie wybierz sposób, w jaki użytkownicy w organizacji używają aplikacji poczty e-mail na swoich urządzeniach:
  
Wybierz opcję ustawiania sposobu, w jaki użytkownicy w organizacji uzyskują dostęp do konta służbowego z urządzeń przenośnych
  
- **tylko Outlook** — użytkownicy w organizacji będą musieli korzystać z Outlook dla aplikacji systemu Android lub Outlook dla systemu iOS na urządzeniu przenośnym.

- **Dowolna aplikacja poczty e-mail** — wszyscy użytkownicy w organizacji będą monitować o użycie Outlook, ale mogą oni wybrać użycie dowolnej aplikacji poczty e-mail.

- **Dowolna aplikacja poczty e-mail** — nowi użytkownicy lub urządzenia w organizacji będą monitowane raz o użycie Outlook, ale mogą oni wybrać użycie dowolnej aplikacji poczty e-mail.

Aby uzyskać więcej informacji, zobacz [Opcje uzyskiwania dostępu do poczty e-mail z urządzenia przenośnego](access-email-from-a-mobile-device.md).
  
## <a name="new-user-or-device-is-activated-in-your-organization"></a>Nowy użytkownik lub urządzenie jest aktywowane w organizacji

Gdy tylko użytkownik w organizacji doda służbową wiadomość e-mail do aplikacji poczty e-mail innej firmy lub do nowego urządzenia, otrzyma wiadomość e-mail od firmy **Microsoft w imieniu Twojej organizacji**. Wiadomość e-mail poinformuje ich o zaletach korzystania z aplikacji mobilnej Outlook i udostępni link do lokalizacji pobierania. Użytkownicy mogą następnie wybrać, czy nadal korzystać z aplikacji innej firmy, czy też korzystać z aplikacji mobilnej Outlook. W ciągu 24 godzin po otrzymaniu tej wiadomości e-mail przez użytkownika urządzenie zostanie poddane kwarantannie, a adres e-mail, kalendarz i dane kontaktowe nie zostaną zaktualizowane. Jeśli zdecydują się korzystać z aplikacji mobilnej Outlook, aplikacja innej firmy pozostanie poddana kwarantannie, a dane będą synchronizowane tylko z aplikacją mobilną Outlook. Jeśli zdecydują się kontynuować korzystanie z aplikacji innej firmy, dane zaczną się natychmiast synchronizować. Jeśli w ciągu pierwszych 24 godzin nie zostaną podjęte żadne działania, wiadomość e-mail zostanie usunięta ze skrzynki odbiorczej, a dane zaczną być automatycznie synchronizowane z serwera.
  
## <a name="previously-configured-users-in-your-organization"></a>Wcześniej skonfigurowani użytkownicy w organizacji

Jeśli zdecydujesz się zalecić Outlook wszystkim w organizacji, oprócz środowiska opisanego powyżej dla nowych użytkowników, użytkownicy, którzy wcześniej połączyli swoje służbowe konto e-mail z aplikacją innej firmy, otrzymają wiadomość e-mail od firmy **Microsoft w imieniu organizacji** w ciągu 48 godzin od włączenia tego ustawienia. Wiadomość e-mail poinformuje ich o zaletach korzystania z aplikacji mobilnej Outlook i udostępni link do lokalizacji pobierania. Użytkownicy mogą następnie wybrać, czy nadal korzystać z aplikacji innej firmy, czy też korzystać z aplikacji mobilnej Outlook. W ciągu 24 godzin po otrzymaniu tej wiadomości e-mail przez użytkownika urządzenie zostanie poddane kwarantannie, a adres e-mail, kalendarz i dane kontaktowe nie zostaną zaktualizowane. Jeśli zdecydują się korzystać z aplikacji mobilnej Outlook, aplikacja innej firmy pozostanie poddana kwarantannie, a dane będą synchronizowane tylko z aplikacją mobilną Outlook. Jeśli zdecydują się kontynuować korzystanie z aplikacji innej firmy, dane zaczną się natychmiast synchronizować. Jeśli w ciągu pierwszych 24 godzin nie zostaną podjęte żadne działania, wiadomość e-mail zostanie usunięta ze skrzynki odbiorczej, a dane zaczną być automatycznie synchronizowane z serwera.
