---
title: Tagowanie obrazów w programie SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.custom: admindeeplinkMAC
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Informacje o tagowaniu obrazów w programie SharePoint Syntex
ms.openlocfilehash: 79df10f80dd02930dc49f56274b00664c6f1d3d2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988337"
---
# <a name="image-tagging-in-sharepoint-syntex"></a>Tagowanie obrazów w programie SharePoint Syntex

(Już wkrótce)

Dzięki tagom obrazów w SharePoint Syntex użytkownicy mogą wyszukiwać obrazy, wyszukując tagi obrazów i tworząc przepływy pracy na podstawie tagów obrazów. Domyślnie dla znakowania obrazów jest włączone podstawowe SharePoint obrazów OneDrive. Obrazy przekazane do jednej z tych lokalizacji są automatycznie skanowane, a odpowiednie tagi są stosowane , jeśli są dostępne, z listy 37 tagów podstawowych. Użytkownicy mogą znaleźć obrazy za pomocą funkcji wyszukiwania, wyszukując tagi obrazów.

Gdy użytkownik przekaże obraz, proces znakowania jest uruchamiany automatycznie. Jeśli obraz jest edytowany, proces znakowania jest ponownie uruchamiany w celu zaktualizowania tagów.

Użytkownicy z uprawnieniami do pliku obrazu mogą zobaczyć i edytować tagi w panelu informacji o pliku lub na stronie wyników wyszukiwania. Gdy użytkownik edytuje tagi obrazu, system nie automatycznie taguje tego obrazu, nawet jeśli jest edytowany.

Jeśli wyłączysz otagowanie, obrazy nie będą już automatycznie tagowane. Istniejące tagi nie zostaną usunięte.

> [!NOTE]
> Tagi wygenerowane przez system mogą ulec zmianie wraz z aktualizacjami obrazu lub naszej technologii tagów.


## <a name="configure-image-tagging"></a>Konfigurowanie otagowania obrazów

Po [skonfigurowaniu SharePoint Syntex](set-up-content-understanding.md) możesz skonfigurować otagowanie obrazów w centrum administracyjne platformy Microsoft 365.  

Aby włączyć lub wyłączyć otagowanie obrazów

1. W centrum administracyjne platformy Microsoft 365 wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Konfiguracja**</a>.

2. W **obszarze Znajomość organizacji** kliknij pozycję **Zautomatyzuj zrozumienie zawartości**.

3. Kliknij **pozycję Zarządzaj**.

4. Na karcie **Otagowanie obrazów** kliknij pozycję **Edytuj**.

5. Wybierz, czy **zezwolić na znakowanie podstawowe** , czy wyłączyć **otagowanie Wyłączone**.

6. Kliknij **Zapisz**.

    ![Zrzut ekranu przedstawiający kontrolkę tagowania obrazów.](../media/content-understanding/sharepoint-syntex-image-tagging-control.png)
