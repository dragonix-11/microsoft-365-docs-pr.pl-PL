---
title: Zarządzanie wykluczeniami folderów automatyzacji
description: Dodawanie wykluczeń folderów automatyzacji w celu kontrolowania plików wykluczonych z automatycznego badania.
keywords: zarządzanie, automatyzacja, wykluczenie, blokowanie, czyszczenie, złośliwe
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
ms.openlocfilehash: 54c0f7f67b62216eae4264c8e7a55c0e34c82fb0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998087"
---
# <a name="manage-automation-folder-exclusions"></a>Zarządzanie wykluczeniami folderów automatyzacji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationexclusionfolder-abovefoldlink)

Wykluczenia folderów automatyzacji umożliwiają określenie folderów, które będą pomijane w automatycznym śledzeniu.

Możesz kontrolować następujące atrybuty dotyczące folderu, który ma zostać pominięty:

- **Foldery**: Możesz określić folder i jego podfoldery do pomijania.

  > [!NOTE]
  > Obecnie korzystanie z symboli wieloznaczych w celu wykluczenia plików w katalogu nie jest jeszcze obsługiwane.

- **Rozszerzenia plików**: Możesz określić rozszerzenia, które chcesz wykluczyć w określonym katalogu. Rozszerzenia te mogą zapobiegać używaniu przez atakującego folderu wykluczonych w celu ukrycia luk. Rozszerzenia jawnie określają, które pliki mają być ignorowane.

- **Nazwy plików**: Możesz określić nazwy plików, które mają być wykluczone w określonym katalogu. Nazwy te mogą zapobiegać używaniu przez atakującego folderu wykluczonych w celu ukrycia luk. Nazwy jawnie określają, które pliki mają być ignorowane.

## <a name="add-an-automation-folder-exclusion"></a>Dodawanie wykluczenia folderu automatyzacji

1. W okienku nawigacji wybierz **pozycję Ustawienia** \> **wykluczeń** \>  \> folderu **automatyzacji reguł punktów końcowych**.

2. Kliknij **pozycję Wykluczenie nowego folderu**.

3. Wprowadź szczegóły folderu:

    - Folder
    - Rozszerzenia
    - Nazwy plików
    - Opis

4. Kliknij **Zapisz**.

> [!NOTE]
> Polecenia funkcji Live Response umożliwiające zbieranie lub badanie wykluczonych plików zakończyły się niepowodzeniem i błędem: "Plik jest wykluczony". Dodatkowo elementy wykluczonych będą ignorowane w przypadku zautomatyzowanego badania.

## <a name="edit-an-automation-folder-exclusion"></a>Edytowanie wykluczenia folderu automatyzacji

1. W okienku nawigacji wybierz **pozycję Ustawienia** \> **wykluczeń** \>  \> folderu **automatyzacji reguł punktów końcowych**.
2. Kliknij **pozycję Edytuj** na wykluczeniu folderu.
3. Zaktualizuj szczegóły reguły i kliknij przycisk **Zapisz**.

## <a name="remove-an-automation-folder-exclusion"></a>Usuwanie wykluczeń folderów automatyzacji

1. W okienku nawigacji wybierz **pozycję Ustawienia** \> **wykluczeń** \>  \> folderu **automatyzacji reguł punktów końcowych**.
2. Kliknij **pozycję Usuń wykluczenie**.

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie listami dozwolonymi/zablokowanymi automatyzacją](manage-indicators.md)
- [Zarządzanie przekazywaniem plików automatyzacji](manage-automation-file-uploads.md)
