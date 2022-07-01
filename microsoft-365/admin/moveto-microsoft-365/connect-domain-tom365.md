---
title: Łączenie domeny z platformą Microsoft 365
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
description: Dowiedz się, jak połączyć domenę z platformą Microsoft 365.
ms.openlocfilehash: 2b02687e8d62a40272ffa5dad8ccabec4fbde368
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603885"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Łączenie domeny z usługą Microsoft 365 dla firm

Zapoznaj się z [pomocą dla małych firm platformy Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) w serwisie YouTube.

## <a name="watch-connect-your-domain-to-microsoft-365"></a>Obejrzyj: Łączenie domeny z platformą Microsoft 365

Zapoznaj się z tym filmem i innymi osobami na naszym [kanale YouTube](https://go.microsoft.com/fwlink/?linkid=2198216).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Po skonfigurowaniu platformy Microsoft 365 i przeniesieniu danych poczty e-mail z obszaru roboczego Google możesz połączyć domenę z platformą Microsoft 365. 

Najpierw należy usunąć istniejące rekordy DNS z firmy Google, a następnie możemy dodać nowe rekordy DNS z platformy Microsoft 365.

1. Zaloguj się do konsoli administracyjnej obszaru roboczego Google w [admin.google.com](https://admin.google.com).
1. Wybierz pozycję **Domeny**, **Zarządzaj domenami**, **Wyświetl szczegóły**, **Zarządzaj domeną**, a następnie **DNS** w lewej nawigacji.
1. Przewiń w dół do **pozycji Rekordy syntetyczne**, otwórz **obszar roboczy Google**, wybierz pozycję **Usuń**, a następnie ponownie **usuń** .
1. Przewiń w dół do **pozycji Niestandardowe rekordy zasobów** i usuń wszystkie istniejące rekordy DNS, w tym wszystkie utworzone wcześniej dla platformy Microsoft 365.
1. Przejdź do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com).
1. W lewej nawigacji wybierz pozycję **Pokaż wszystkie** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domeny ustawień**</a> > .
1. Następnie wybierz domenę domyślną.
1. Wybierz pozycję **Kontynuuj konfigurację**, a następnie, aby połączyć domenę, wybierz pozycję  **Kontynuuj**.
1. Przewiń w dół, aby wyświetlić rekordy DNS, które należy skopiować do firmy Google.
1. Otwórz **rekordy MX** i w obszarze **Punkty do adresu lub wartości** skopiuj rekord.
1. Wróć do firmy Google, a następnie w sekcji **Niestandardowe rekordy zasobów** otwórz listę rozwijaną typu rekordu i wybierz pozycję **MX**.
1. W polu **Dane** wklej skopiowany rekord.
1. Następnie wybierz pozycję **Dodaj**.
1. Powtórz proces dla rekordów CNAME i TXT i dodaj wartości na stronie zarządzania google DNS.
1. Wróć do Centrum administracyjne platformy Microsoft 365 i wybierz pozycję **Kontynuuj**.

    Konfiguracja domeny została ukończona.