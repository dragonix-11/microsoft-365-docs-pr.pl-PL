---
title: przechowywanie danych Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Ochrona usługi Office 365 w usłudze Microsoft Defender informacje o przechowywaniu danychWykrycie Eksploratora/Real-Time
ms.openlocfilehash: 9cab47358890b47796a42e48b690818d65e20527
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772799"
---
# <a name="data-retention-information-for-microsoft-defender-for-office-365"></a>Informacje o przechowywaniu danych dla Ochrona usługi Office 365 w usłudze Microsoft Defender

Domyślnie dane różnych funkcji są przechowywane przez maksymalnie 30 dni. Jednak w przypadku niektórych funkcji można określić okres przechowywania na podstawie zasad. Zapoznaj się z poniższą tabelą, aby zapoznać się z różnymi okresami przechowywania dla każdej funkcji.

> [!NOTE]
> Ochrona usługi Office 365 w usłudze Microsoft Defender jest dostępny w dwóch różnych typach planów. Jeśli masz Eksploratora zagrożeń, możesz sprawdzić, czy masz **plan 1** , czy masz "wykrywanie w czasie rzeczywistym" i **plan 2**. Plan, który masz, ma wpływ na narzędzia, które zobaczysz, więc upewnij się, że masz świadomość swojego planu w miarę nauki.

## <a name="defender-for-office-365-plan-1"></a>Ochrona usługi Office 365 w usłudze Defender plan 1

|Funkcja|Okres przechowywania|
|---|---|
|Szczegóły metadanych alertów (usługa Microsoft Defender dla alertów Office) | 90 dni |
|Szczegóły metadanych jednostki (wiadomości e-mail) | 30 dni |
|Szczegóły alertu aktywności (dzienniki inspekcji) | 7 dni |
|Strona jednostki poczty e-mail | 30 dni |
|Kwarantanna | 30 dni (można skonfigurować maksymalnie do 30 dni) |
|Raporty | 90 dni (dla wszystkich zagregowanych danych) <br>30 dni (dla wszystkich szczegółowych informacji z wyjątkiem poniższych) <br> 10 dni (w przypadku szczegółów raportu o stanie ochrony przed zagrożeniami i fałszywych raportów pocztowych) <br> 7 dni (w przypadku szczegółów raportu ochrony adresu URL) <br>
|Zgłoszenia | 30 dni |
|Eksplorator zagrożeń/ wykrywanie Real-Time | 30 dni |

## <a name="defender-for-office-365-plan-2"></a>Ochrona usługi Office 365 w usłudze Defender plan 2

Ochrona usługi Office 365 w usłudze Defender możliwości planu 1 oraz:

|Funkcja|Okres przechowywania|
|---|---|
|Centrum akcji | 180 dni, 30 dni (Office Centrum akcji)   |
|Zaawansowane wyszukiwanie zagrożeń | 30 dni |
|AIR (zautomatyzowane badanie i reagowanie) | 60 dni (w przypadku metadanych badań)<br> 30 dni (dla metadane wiadomości e-mail)  |
|Dane symulacji ataków | 18 miesięcy |
|Kampanie | 30 dni |
|Zdarzenia | 30 dni|
|Korygowania | 30 dni |
|Analiza zagrożeń | 30 dni |
|Moduły śledzące zagrożenia | 30 dni |
