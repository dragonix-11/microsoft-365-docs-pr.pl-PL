---
title: Zarządzanie przekazywaniem plików automatyzacji
description: Włączanie analizy zawartości i konfigurowanie rozszerzeń plików i rozszerzeń załączników wiadomości e-mail, które będą przesyłane do analizy
keywords: automatyzacja, plik, przekazywanie, zawartość, analiza, plik, rozszerzenie, wiadomość e-mail, załącznik
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 21e7eb17759ff6127f3d91137023c058abe2715e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998088"
---
# <a name="manage-automation-file-uploads"></a>Zarządzanie przekazywaniem plików automatyzacji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationefileuploads-abovefoldlink)

Włącz funkcję analizy zawartości, aby określone pliki i załączniki wiadomości e-mail można było automatycznie przekazać do chmury w celu dodatkowej inspekcji w automatycznym śledztwie.

Zidentyfikuj pliki i załączniki wiadomości e-mail, określając nazwy rozszerzeń plików i nazwy rozszerzeń załączników wiadomości e-mail.

Jeśli na przykład dodasz exe  i *bat* jako nazwy rozszerzeń plików lub załączników, wszystkie pliki lub załączniki z tymi rozszerzeniami zostaną automatycznie wysłane do chmury w celu dodatkowej inspekcji podczas automatycznego badania.

## <a name="add-file-extension-names-and-attachment-extension-names"></a>Dodaj nazwy rozszerzeń plików i nazwy rozszerzeń załączników.

1. W okienku nawigacji **wybierz pozycję Ustawienia** \> **automatyzacji** \> **reguł** \> punktów **końcowych**.

2. Włącz lub wyłącz ustawienie analizy **zawartości**.

3. Skonfiguruj następujące nazwy rozszerzeń i osobne nazwy rozszerzeń przecinkami:
   - **Nazwy rozszerzeń plików — podejrzane** pliki z wyjątkiem załączników wiadomości e-mail zostaną przesłane do dodatkowej inspekcji

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie wykluczeniami folderów automatyzacji](manage-automation-folder-exclusions.md)
