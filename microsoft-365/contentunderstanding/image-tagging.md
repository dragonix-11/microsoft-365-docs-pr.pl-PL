---
title: Tagowanie obrazów w SharePoint Syntex
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
description: Dowiedz się więcej o tagowaniu obrazów w SharePoint Syntex
ms.openlocfilehash: e0b9b1669efb069942b81aaad7fb5e7e3aa57c1c
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415887"
---
# <a name="image-tagging-in-sharepoint-syntex"></a>Tagowanie obrazów w SharePoint Syntex

(Wkrótce)

Dzięki tagowaniu obrazów w SharePoint Syntex użytkownicy mogą wyszukiwać obrazy, wyszukując tagi obrazów i tworząc przepływy pracy na podstawie tagów obrazów. Domyślnie dla SharePoint i OneDrive jest włączone podstawowe tagowanie obrazów. Obrazy przekazane do dowolnej lokalizacji są automatycznie skanowane, a odpowiednie tagi są stosowane, jeśli są dostępne, z listy 37 podstawowych tagów. Użytkownicy mogą znaleźć obrazy za pośrednictwem wyszukiwania, wyszukując tagi obrazów.

Gdy użytkownik przekaże obraz, proces tagowania jest uruchamiany automatycznie. Jeśli obraz jest edytowany, proces tagowania zostanie uruchomiony ponownie, aby zaktualizować tagi.

Użytkownicy z uprawnieniami do pliku obrazu mogą wyświetlać i edytować tagi w panelu informacji o pliku lub na stronie wyników wyszukiwania. Gdy użytkownik edytuje tagi obrazu, system nie będzie już automatycznie tagował tego obrazu, nawet jeśli jest edytowany.

Jeśli wyłączysz tagowanie, obrazy nie będą już automatycznie oznaczane. Istniejące tagi nie zostaną usunięte.

> [!NOTE]
> Tagi generowane przez system mogą ulec zmianie wraz z aktualizacjami obrazu lub technologii tagów.

## <a name="configure-image-tagging"></a>Konfigurowanie tagowania obrazów

Po [skonfigurowaniu SharePoint Syntex](set-up-content-understanding.md) można skonfigurować tagowanie obrazów w Centrum administracyjne platformy Microsoft 365.

Aby włączyć lub wyłączyć tagowanie obrazów

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Konfiguracja**</a>.

2. W obszarze **Wiedza organizacyjna** kliknij pozycję **Automatyzuj zrozumienie zawartości**.

3. Kliknij pozycję **Zarządzaj**.

4. Na **karcie Tagowanie obrazów** kliknij pozycję **Edytuj**.

5. Wybierz opcję **zezwalania na tagowanie podstawowe** lub wyłącz **tagowanie.**

6. Kliknij **Zapisz**.

    ![Zrzut ekranu przedstawiający kontrolkę tagowania obrazów.](../media/content-understanding/sharepoint-syntex-image-tagging-control.png)
