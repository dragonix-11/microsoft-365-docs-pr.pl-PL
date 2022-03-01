---
title: Połączenie domenę do Microsoft 365
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
description: Dowiedz się, jak połączyć domenę z Microsoft 365.
ms.openlocfilehash: d54b3bbf00dd0cf37006924e2884f2861c345d3e
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014760"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Połączenie domenę do Microsoft 365 dla firm

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Po skonfigurowaniu usługi Microsoft 365 i przesunięcie danych poczty e-mail z usługi Google Workspace możesz połączyć domenę z usługą Microsoft 365. 

Najpierw musisz usunąć istniejące rekordy DNS z usługi Google, a następnie dodać nowe rekordy DNS z usługi Microsoft 365.

## <a name="try-it"></a>Spróbuj!

1. Zaloguj się do konsoli administracyjnej programu Google Workspace w oknie [admin.google.com](https://admin.google.com).
1. Wybierz **domeny**, **Zarządzaj domenami**, **Wyświetl szczegóły**, **Zarządzaj domeną**, **a następnie DNS** w lewym pasku narracji.
1. Przewiń w dół do **obszaru Rekordy domen** domenowych, otwórz **obszar roboczy Google**, wybierz pozycję **Usuń**, a następnie **ponownie pozycję Usuń** .
1. Przewiń w dół **do opcji Niestandardowe** rekordy zasobów i usuń wszelkie istniejące rekordy DNS, w tym wszelkie utworzone wcześniej przez Ciebie Microsoft 365.
1. Przejdź do [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com).
1. W lewym okienku narracji wybierz pozycję **Pokaż wszystkie** >  **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.
1. Następnie wybierz domenę domyślną.
1. Wybierz **pozycję Kontynuuj konfigurowanie**, a następnie wybierz pozycję Kontynuuj, aby połączyć  **domenę**.
1. Przewiń w dół, aby wyświetlić rekordy DNS, które muszą zostać skopiowane do usługi Google.
1. Otwórz **rekordy MX** i w **obszarze Points to address or value (Wskazuje adres lub wartość)** skopiuj rekord.
1. Wróć do usługi Google i w sekcji **Custom resource records (** Niestandardowe rekordy zasobów) otwórz menu rozwijane record type (Typ rekordu) i wybierz pozycję **MX**.
1. W **polu Dane** wklej skopiowany rekord.
1. Następnie wybierz **pozycję Dodaj**.
1. Powtórz tę procedurę dla rekordów CNAME i TXT i dodaj wartości na stronie zarządzania usługą DNS Google.
1. Wróć do centrum administracyjne platformy Microsoft 365 i wybierz **pozycję Kontynuuj**.

    Konfiguracja domeny jest ukończona.