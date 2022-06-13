---
title: (Fałszywie pozytywne) Jak obsługiwać wiarygodne wiadomości e-mail blokowane przed dostarczaniem przy użyciu usługi Microsoft Defender dla Office 365
description: Kroki obsługi legalnych wiadomości e-mail są blokowane (fałszywie dodatnie) przez Ochrona usługi Office 365 w usłudze Microsoft Defender, aby zapobiec utracie działalności.
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
ms.openlocfilehash: abf348fd4de02f521dfa9c5f8d7c16346753c5de
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043651"
---
# <a name="how-to-handle-legitimate-emails-getting-blocked-false-positive-using-microsoft-defender-for-office-365"></a>Jak obsługiwać zablokowane uzasadnione wiadomości e-mail (fałszywie dodatnie) przy użyciu Ochrona usługi Office 365 w usłudze Microsoft Defender

Ochrona usługi Office 365 w usłudze Microsoft Defender pomaga radzić sobie z ważnymi legalnymi wiadomościami e-mail biznesowymi, które są omyłkowo blokowane jako zagrożenia (wyniki fałszywie dodatnie). Ochrona usługi Office 365 w usłudze Defender może pomóc administratorom zrozumieć, *dlaczego* uzasadnione wiadomości e-mail są blokowane, jak szybko rozwiązać sytuację i zapobiec podobnym sytuacjom w przyszłości.

## <a name="what-youll-need"></a>Co będzie potrzebne

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 lub 2 (uwzględniony w ramach E5). Exchange Online klienci mogą również korzystać z tej funkcji.
- Wystarczające uprawnienia (rola administratora zabezpieczeń).
- 5–10 minut na wykonanie poniższych kroków.

## <a name="handling-legitimate-emails-in-to-junk-folder-of-end-users"></a>Obsługa legalnych wiadomości e-mail w folderze Junk użytkowników końcowych

1. Poproś użytkowników końcowych o zgłaszanie wiadomości e-mail jako **wiadomości-śmieci** przy użyciu dodatku microsoft message lub przycisków Outlook.
2. Użytkownicy końcowi mogą również dodać nadawcę do [**listy bezpiecznych nadawców**](https://support.microsoft.com/en-us/office/safe-senders-in-outlook-com-470d4ee6-e3b6-402b-8cd9-a6f00eda7339) w Outlook, aby zapobiec trafieniu wiadomości e-mail od tych nadawców w folderze Wiadomości-śmieci.
3. Administratorzy mogą klasyfikować komunikaty zgłaszane przez użytkownika z portalu [zawartości zgłoszonego przez użytkownika](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
4. Z tych zgłoszonych wiadomości administratorzy mogą przesyłać do [**firmy Microsoft w celu analizy**](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) i zrozumieć, dlaczego ta wiadomość e-mail została w pierwszej kolejności zablokowana.
5. W razie potrzeby podczas przesyłania do firmy Microsoft w celu analizy administratorzy mogą rozsądnie utworzyć [**zezwolenie** nadawcy na](/microsoft-365/security/office-365-security/manage-tenant-allows?view=o365-worldwide#add-sender-allows-using-the-submissions-portal&preserve-view=true) rozwiązanie problemu.
6. Po udostępnieniu wyników przesyłania przez administratora przeczytaj je, aby zrozumieć, dlaczego wiadomości e-mail zostały zablokowane i jak można ulepszyć konfigurację dzierżawy, aby *zapobiec* podobnym sytuacjom w przyszłości.

## <a name="handling-legitimate-emails-that-are-in-quarantine-folder-of-end-users"></a>Obsługa legalnych wiadomości e-mail znajdujących się w folderze kwarantanny użytkowników końcowych

1. Użytkownik końcowy otrzymuje [wiadomość e-mail dotyczącą](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide&preserve-view=true) komunikatów poddanych kwarantannie zgodnie z ustawieniami włączonymi przez administratorów zabezpieczeń.
2. Użytkownicy końcowi mogą wyświetlać podgląd komunikatów w kwarantannie, blokować nadawcę, zwalniać komunikaty, przesyłać te wiadomości do firmy Microsoft w celu analizy i żądać wydania tych wiadomości e-mail od administratorów.

## <a name="handling-legitimate-emails-in-quarantine-folder-of-an-admin"></a>Obsługa legalnych wiadomości e-mail w folderze kwarantanny administratora

1. Administratorzy mogą wyświetlać wiadomości e-mail poddane kwarantannie (w tym te z prośbą o uprawnienie do żądania wydania) [na stronie przeglądu](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide&preserve-view=true).
2. Administratorzy mogą zwolnić komunikat z kwarantanny podczas przesyłania go do firmy Microsoft w celu analizy i utworzyć zezwolenie na złagodzenie sytuacji.
3. Po udostępnieniu wyników przesyłania administratorzy powinni przeczytać werdykt, aby zrozumieć, dlaczego wiadomości e-mail zostały zablokowane i jak można ulepszyć konfigurację dzierżawy, aby zapobiec podobnym sytuacjom w przyszłości.
