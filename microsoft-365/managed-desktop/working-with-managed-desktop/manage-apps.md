---
title: Zarządzanie aplikacjami w aplikacji Microsoft Managed Desktop
description: Informacje o aktualizowaniu aplikacji biznesowych wdrożonych na Microsoft Managed Desktop urządzeniach
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 01/18/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: a51be2521924164a8c90a51fcf99328ecf511877
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63013785"
---
# <a name="manage-line-of-business-apps-in-microsoft-managed-desktop"></a>Zarządzanie aplikacjami biznesowymi w aplikacji Microsoft Managed Desktop

<!--Application management -->

Istnieje kilka sposobów zarządzania aktualizacjami aplikacji i wdrażania ich na swoich Microsoft Managed Desktop urządzeniach. Możesz dokonać aktualizacji aplikacji w Microsoft Managed Desktop lub Intune.

<span id="update-app-mmd" />

## <a name="update-line-of-business-apps-in-microsoft-managed-desktop"></a>Aktualizowanie aplikacji biznesowych w aplikacji Microsoft Managed Desktop

**Aby zaktualizować aplikacje firmowe w portalu Microsoft Managed Desktop firmowego:**

1. Zaloguj się do [Microsoft Managed Desktop administratora](https://aka.ms/mmdportal).
1. W **obszarze Spis** wybierz pozycję **Aplikacje**.  
1. Wybierz aplikację, którą chcesz zmienić, a następnie wybierz pozycję **Edytuj**.
1. W **obszarze Zarządzanie** wybierz pozycję **Właściwości**.
1. Wybierz **plik pakietu aplikacji**, a następnie przejdź do przekazywania nowego pliku pakietu aplikacji.
1. Wybierz **plik pakietu aplikacji**.
1. Wybierz ikonę folderu i przejdź do lokalizacji zaktualizowanego pliku aplikacji. Wybierz opcję **Otwórz**. Informacje o aplikacji zostaną zaktualizowane przy użyciu informacji o pakiecie.
1. Sprawdź, **czy wersja aplikacji** odzwierciedla zaktualizowany pakiet aplikacji.

Zaktualizowana aplikacja zostanie wdrożona na urządzeniach użytkowników.

<span id="update-app-intune" />

## <a name="update-line-of-business-apps-in-intune"></a>Aktualizowanie aplikacji biznesowych w usłudze Intune

**Aby zaktualizować aplikacje biznesowe w usłudze Intune:**

1. Zaloguj się do [portalu Azure Portal](https://portal.azure.com).
2. Wybierz **pozycję Wszystkie** **usługiIntune** > . Usługa Intune znajduje się w **sekcji Monitorowanie +** zarządzanie.
3. Wybierz **pozycję Aplikacje > aplikacje**.
4. Znajdź i wybierz aplikację na liście aplikacji.
5. W sekcji **Przegląd** wybierz pozycję **Właściwości**.
6. Wybierz **plik pakietu aplikacji**.
7. Wybierz ikonę folderu i przejdź do lokalizacji zaktualizowanego pliku aplikacji. Wybierz opcję **Otwórz**. Informacje o aplikacji zostaną zaktualizowane przy użyciu informacji o pakiecie.
8. Sprawdź, **czy wersja aplikacji** odzwierciedla zaktualizowany pakiet aplikacji.

<span id="roll-back-app-mmd" />

## <a name="roll-back-an-app-to-a-previous-version"></a>Wycofywanie aplikacji do poprzedniej wersji

Gdy zostanie wdrożona nowa wersja aplikacji i zostanie odnaleziony błąd, możesz wrócić do poprzedniej wersji. Poniższy proces przedstawia aplikacje, w których typ jest wymieniony jako aplikacja biznesowa **WINDOWS MSI** lub aplikacja Windows **(Win 32)** — wersja Preview

**Aby wycofać aplikację biznesową do poprzedniej wersji:**

1. Zaloguj się do [Microsoft Managed Desktop administratora](https://aka.ms/mmdportal).
2. W **obszarze Spis** wybierz pozycję **Aplikacje**.  
3. Wybierz aplikację, która ma być wycofana, a następnie wybierz pozycję **Edytuj**.
4. W **obszarze Zarządzanie** wybierz pozycję **Właściwości**.
    - Aby **Windows aplikacji biznesowych MSI**, wybierz pozycję Informacje o **aplikacji, a** następnie w obszarze Ignoruj **wersję** aplikacji wybierz pozycję **Tak**.
    - W **Windows aplikacji (Win 32) —** wyświetl podgląd aplikacji, wybierz pozycję Informacje o **aplikacji, wybierz** pozycję **Wykrywanie** reguł, a następnie wybierz pozycję **Dodaj**.
    Jeśli istnieje reguła MSI, sprawdź, czy dla ustawienia Sprawdzanie wersji produktu **MSI** ustawiono wartość **Nie**.
5. [Upload poprzednią wersję pliku źródłowego aplikacji do](../get-started/deploy-apps.md) portalu Microsoft Managed Desktop administracyjnego.  
