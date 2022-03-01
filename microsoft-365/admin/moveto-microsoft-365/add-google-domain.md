---
title: Dodawanie domeny obszaru roboczego usługi Google
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
description: Dowiedz się, jak przenieść domenę z usługi Google Workspace do usługi Microsoft 365 dla firm.
ms.openlocfilehash: b41fdf304d0f0b9680f87f40a4564573593d6e75
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014768"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a>Dodawanie domeny obszaru roboczego usługi Google Workspace do Microsoft 365

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

Dodaj domenę obszaru roboczego Google Microsoft 365 dla firm, aby nadal korzystać z firmowego adresu e-mail.

## <a name="try-it"></a>Spróbuj!

1. Przejdź do [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com).
1. Na pasku centrum administracyjne platformy Microsoft 365 w lewym okienku narracji wybierz pozycję **Pokaż wszystkie** >  **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.
1. Wybierz **pozycję Dodaj domenę**, wprowadź nazwę domeny, a następnie wybierz **pozycję Użyj tej domeny**. 
1. Wybierz pozycję **Add a TXT record to the domains DNS records** (Dodaj rekord TXT) do rekordów DNS domen, **wybierz pozycję Continue (Kontynuuj**) i skopiuj wartość TXT. 
1. Wróć do konsoli [administracyjnej usługi Google](https://admin.google.com), wybierz pozycję **Domeny, Zarządzanie** **domenami****, Wyświetl** **szczegóły, Zarządzaj** domeną i **systemem DNS**, a następnie przewiń w dół do **pozycji Niestandardowe rekordy zasobów**. 
1. Otwórz menu rozwijane typu rekordu, wybierz pozycję **TXT**, wklej skopiowaną wartość TXT, a następnie wybierz pozycję **Dodaj**. 

    Aktualizacja zwykle trwa kilka minut, ale może potrwać do 48 godzin. 
1. Wróć do centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">administracyjnego</a>, wybierz pozycję **Weryfikuj**, a następnie **zamknij**. 
1. Aby ustawić domenę jako podstawową pocztę e-mail dla użytkowników, w lewym okienku narracji wybierz pozycję [**UżytkownicyAktywowanie**](https://go.microsoft.com/fwlink/p/?linkid=834822) >  użytkowników. 
1. Wybierz użytkownika, wybierz pozycję **Zarządzaj nazwą użytkownika i pocztą** e-mail, **Edytuj**, wybierz domenę z listy rozwijanej, a następnie wybierz **pozycję Gotowe** i **Zapisz zmiany**. 
1. Powtórz tę procedurę dla każdego użytkownika. 

    Po zakończeniu możesz zainstalować aplikacje pakietu Office i przeprowadzić migrację poczty e-mail oraz elementów kalendarza do usługi Microsoft 365. 