---
title: (Fałszywie negatywne) Jak obsługiwać złośliwe wiadomości e-mail dostarczane do adresatów przy użyciu usługi Microsoft Defender dla Office 365
description: Kroki obsługi złośliwych wiadomości e-mail przesyłanych do użytkowników końcowych i skrzynek odbiorczych (jako fałszywych negatywów) z Ochrona usługi Office 365 w usłudze Microsoft Defender, aby zapobiec utracie działalności.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: jarogers
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: decbece049ea4f91deb529d2fd640816bf3f1d0c
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042154"
---
# <a name="how-to-handle-malicious-emails-that-are-delivered-to-recipients-false-negatives-using-microsoft-defender-for-office-365"></a>Jak obsługiwać złośliwe wiadomości e-mail dostarczane do adresatów (fałszywie ujemne) przy użyciu Ochrona usługi Office 365 w usłudze Microsoft Defender

Ochrona usługi Office 365 w usłudze Microsoft Defender pomaga radzić sobie ze złośliwymi wiadomościami e-mail (fałszywie ujemnymi), które są dostarczane do adresatów i które narażają produktywność organizacji na niebezpieczeństwo.
Ochrona usługi Office 365 w usłudze Defender może pomóc zrozumieć, dlaczego wiadomości e-mail są dostarczane, jak szybko rozwiązać sytuację i jak zapobiegać podobnym sytuacjom w przyszłości.

## <a name="what-youll-need"></a>Co będzie potrzebne

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i 2 (uwzględniony w ramach E5). Exchange Online klienci mogą również skorzystać z tej możliwości.
- Wystarczające uprawnienia (rola administratora zabezpieczeń).
- 5–10 minut na wykonanie poniższych kroków.

## <a name="handling-malicious-emails-in-the-inbox-folder-of-end-users"></a>Obsługa złośliwych wiadomości e-mail w folderze Skrzynka odbiorcza użytkowników końcowych

1. Poproś użytkowników końcowych o zgłaszanie wiadomości e-mail jako wiadomości **wyłudzających informacje** lub **wiadomości-śmieci** przy użyciu dodatku microsoft message, dodatku Microsoft Phish lub przycisków Outlook.
2. Użytkownicy końcowi mogą również dodać nadawcę do [listy zablokowanych nadawców](https://support.microsoft.com/en-us/office/block-a-mail-sender-b29fd867-cac9-40d8-aed1-659e06a706e4#:~:text=1%20On%20the%20Home%20tab%2C%20in%20the%20Delete,4%20Click%20OK%20in%20both%20open%20dialog%20boxes..) w Outlook, aby zapobiec dostarczaniu wiadomości e-mail od tego nadawcy do skrzynki odbiorczej.
3. Administratorzy mogą klasyfikować komunikaty zgłaszane przez użytkownika z portalu [zawartości zgłoszonej przez użytkownika](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
4. Z tych zgłoszonych wiadomości administratorzy mogą **przesyłać do firmy Microsoft w celu** [analizy](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) , aby dowiedzieć się, dlaczego ta wiadomość e-mail była dozwolona.
5. W razie potrzeby podczas przesyłania do firmy Microsoft w celu analizy administratorzy mogą utworzyć [blok dla nadawcy](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide&preserve-view=true) w celu rozwiązania problemu.
6. Po udostępnieniu wyników przesyłania przeczytaj werdykt, aby zrozumieć, dlaczego wiadomości e-mail były dozwolone, oraz jak można ulepszyć konfigurację dzierżawy, aby zapobiec podobnym sytuacjom w przyszłości.

## <a name="handling-malicious-emails-in-junk-folder-of-end-users"></a>Obsługa złośliwych wiadomości e-mail w folderze śmieci użytkowników końcowych

1. Poproś użytkowników końcowych, aby zgłaszali wiadomość e-mail jako **wyłudzanie informacji** przy użyciu dodatku microsoft message, dodatku Microsoft Phish lub przycisków Outlook.
2. Administratorzy mogą klasyfikować komunikaty zgłaszane przez użytkownika z portalu [zawartości zgłoszonej przez użytkownika](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
3. Z tych zgłoszonych wiadomości administratorzy mogą **przesyłać do firmy Microsoft w celu** [analizy](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) i dowiedzieć się, dlaczego ta wiadomość e-mail została w pierwszej kolejności dozwolona.
4. W razie potrzeby podczas przesyłania do firmy Microsoft w celu analizy administratorzy mogą utworzyć [blok dla nadawcy](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide&preserve-view=true) w celu rozwiązania problemu.
5. Po udostępnieniu wyników przesyłania przeczytaj werdykt, aby zrozumieć, dlaczego wiadomości e-mail były dozwolone, oraz jak można ulepszyć konfigurację dzierżawy, aby zapobiec podobnym sytuacjom w przyszłości.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-end-users"></a>Obsługa złośliwych wiadomości e-mail w folderze kwarantanny użytkowników końcowych

1. Użytkownicy końcowi otrzymują [wiadomość e-mail dotyczącą](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide&preserve-view=true) komunikatów poddanych kwarantannie zgodnie z ustawieniami włączonymi przez administratorów.
2. Użytkownicy końcowi mogą wyświetlać podgląd komunikatów w kwarantannie, blokować nadawcę i przesyłać te komunikaty do firmy Microsoft w celu analizy.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-admins"></a>Obsługa złośliwych wiadomości e-mail w folderze kwarantanny administratorów

1. Administratorzy mogą wyświetlać wiadomości e-mail poddane kwarantannie (w tym te z prośbą o uprawnienie do żądania wydania) [na stronie przeglądu](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide&preserve-view=true).
2. Administratorzy mogą przesyłać do firmy Microsoft wszelkie złośliwe lub podejrzane wiadomości do analizy i tworzyć blok w celu złagodzenia sytuacji podczas oczekiwania na werdykt.
3. Po udostępnieniu wyników przesyłania przeczytaj werdykt, aby dowiedzieć się, dlaczego wiadomości e-mail były dozwolone i jak można ulepszyć konfigurację dzierżawy, aby zapobiec podobnym sytuacjom w przyszłości.
