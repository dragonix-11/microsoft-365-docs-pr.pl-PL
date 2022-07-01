---
title: Dodawanie domeny obszaru roboczego Google
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Dowiedz się, jak przenieść domenę z obszaru roboczego Google na platformę Microsoft 365 dla firm.
ms.openlocfilehash: 06129811ea1d97b0ffb770843c58373427228559
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601141"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a>Dodawanie domeny obszaru roboczego Google do platformy Microsoft 365

Zapoznaj się z [pomocą dla małych firm platformy Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) w serwisie YouTube.

## <a name="watch-add-google-workspace-domain"></a>Obejrzyj: Dodawanie domeny obszaru roboczego Google

Zapoznaj się z tym filmem i innymi osobami na naszym [kanale YouTube](https://go.microsoft.com/fwlink/?linkid=2198105).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

Dodaj domenę obszaru roboczego Google do usługi Microsoft 365 dla firm, aby nadal korzystać z firmowego adresu e-mail.

1. Przejdź do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com).
1. W Centrum administracyjne platformy Microsoft 365 w lewym pasku nawigacyjnym wybierz pozycję **Pokaż wszystkie** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domeny ustawień**</a> > .
1. Wybierz **pozycję Dodaj domenę**, wprowadź nazwę domeny, a następnie wybierz pozycję **Użyj tej domeny**. 
1. Wybierz **pozycję Dodaj rekord TXT do rekordów DNS domen**, wybierz pozycję **Kontynuuj** i skopiuj wartość TXT. 
1. Wstecz do [konsoli usługi Google Administracja](https://admin.google.com), wybierz pozycję **Domeny**, **Zarządzaj domenami**, **Wyświetl szczegóły**, **Zarządzaj domeną**, **SYSTEMEM DNS**, a następnie przewiń w dół do **pozycji Niestandardowe rekordy zasobów**. 
1. Otwórz listę rozwijaną typ rekordu, wybierz pozycję **TXT**, wklej skopiowaną wartość TXT, a następnie wybierz pozycję **Dodaj**. 

    Aktualizacja zwykle trwa kilka minut, ale może potrwać do 48 godzin. 
1. Wróć do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnego</a>, wybierz pozycję **Weryfikuj**, a następnie **zamknij**. 
1. Aby ustawić domenę jako podstawową wiadomość e-mail dla użytkowników, w lewym okienku nawigacji wybierz pozycję **Użytkownicy** > [**aktywni użytkownicy**](https://go.microsoft.com/fwlink/p/?linkid=834822). 
1. Wybierz użytkownika, wybierz pozycję **Zarządzaj nazwą użytkownika i wiadomością e-mail**, **Edytuj**, wybierz domenę z listy rozwijanej, a następnie wybierz pozycję **Gotowe** i **Zapisz zmiany**. 
1. Powtórz ten proces dla każdego użytkownika. 

    Po zakończeniu będziesz gotowy do zainstalowania aplikacji pakietu Office i migracji elementów poczty e-mail i kalendarza na platformę Microsoft 365. 