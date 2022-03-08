---
title: Tworzenie tagów urządzeń i zarządzanie nimi
description: Grupowanie urządzeń za pomocą tagów urządzeń w celu przechwytywania kontekstu i umożliwienia dynamicznego tworzenia list w ramach zdarzenia
keywords: tags, device tags, device groups, groups, remediation, level, rules, aad group, role, assign, rank
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
ms.openlocfilehash: 65df8553f5ee3b7dd7876557398e0d4aa22c7bd5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323531"
---
# <a name="create-and-manage-device-tags"></a>Tworzenie tagów urządzeń i zarządzanie nimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dodaj tagi na urządzeniach, aby utworzyć logiczną przynależność do grupy. Tagi urządzeń obsługują prawidłowe mapowanie sieci, pozwalając na dołączanie różnych tagów w celu przechwycenia kontekstu i umożliwienia dynamicznego tworzenia listy w ramach zdarzenia. Tagi mogą być używane jako filtr **w widoku Spis** urządzeń lub do grupowania urządzeń. Aby uzyskać więcej informacji na temat grupowania urządzeń, zobacz [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md).

Tagi na urządzeniach można dodawać w następujący sposób:

- Używanie portalu
- Ustawianie wartości klucza rejestru

> [!NOTE]
> Między dodaniem tagu do urządzenia a jego dostępnością na liście urządzeń i na stronie urządzenia może wystąpić pewne opóźnienie.

Aby dodać tagi urządzeń przy użyciu interfejsu API, zobacz [Dodawanie lub usuwanie tagów urządzeń interfejsu API](add-or-remove-machine-tags.md).

## <a name="add-and-manage-device-tags-using-the-portal"></a>Dodawanie tagów urządzeń i zarządzanie nimi przy użyciu portalu

1. Wybierz urządzenie, na którym chcesz zarządzać tagami. Możesz wybrać lub wyszukać urządzenie z dowolnego z następujących widoków:

   - **Pulpit nawigacyjny operacji zabezpieczeń** — wybierz nazwę urządzenia w sekcji Naj górne urządzenia z aktywnymi alertami.
   - **Kolejka alertów** - z kolejki alertów wybierz nazwę urządzenia obok ikony urządzenia.
   - **Spis urządzeń** — wybierz nazwę urządzenia z listy urządzeń.
   - **Pole wyszukiwania** - wybierz pozycję Urządzenie z menu rozwijanego i wprowadź nazwę urządzenia.

     Możesz również przejść do strony alertu za pośrednictwem widoków plików i adresów IP.

2. Wybierz **pozycję Zarządzaj tagami** w wierszu Akcje odpowiedzi.

    :::image type="content" alt-text="Obraz przycisku Zarządzaj tagami." source="images/manage-tags-option.png":::

3. Wpisywanie w celu znalezienia lub utworzenia tagów

    :::image type="content" alt-text="Obraz dodawania tagów na urządzeniu1." source="images/create-new-tag.png":::

Tagi są dodawane do widoku urządzenia i będą również odzwierciedlane w widoku **zapasów** Urządzeń. Następnie możesz użyć **filtru Tagi** , aby wyświetlić odpowiednią listę urządzeń.

> [!NOTE]
> Filtrowanie może nie działać w przypadku nazw tagów zawierających nawiasy.
>
> Po utworzeniu nowego tagu zostanie wyświetlona lista istniejących tagów. Na liście są jedynie znaczniki utworzone za pośrednictwem portalu. Istniejące tagi utworzone na urządzeniach klienckich nie będą wyświetlane.

W tym widoku możesz również usuwać tagi.

:::image type="content" alt-text="Obraz dodawania tagów na urządzeniu2." source="images/new-tag-label-display.png":::

## <a name="add-device-tags-by-setting-a-registry-key-value"></a>Dodawanie tagów urządzeń przez ustawienie wartości klucza rejestru

> [!NOTE]
> Dotyczy tylko następujących urządzeń:
>
> - Windows 11
> - Windows 10, wersja 1709 lub nowsza
> - Windows Server w wersji 1803 lub nowszej
> - System Windows Server 2016
> - Windows Server 2012 R2
> - Windows Server 2008 R2 z dodatkiem SP1
> - Windows 8.1
> - Windows 7 z dodatkiem SP1

> [!NOTE]
> Maksymalna liczba znaków, które można ustawić w znaczniku, to 200.

Urządzenia z podobnymi tagami mogą być przydatne, gdy musisz zastosować akcję kontekstową na określonej liście urządzeń.

Aby dodać tag na urządzeniu, użyj następującego wpisu klucza rejestru:

- Klucz rejestru: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging\`
- Wartość klucza rejestru (REG_SZ): `Group`
- Dane klucza rejestru: `Name of the tag you want to set`

> [!NOTE]
> Tag urządzenia jest częścią raportu informacji o urządzeniu generowanego raz dziennie. Alternatywnie możesz ponownie uruchomić punkt końcowy, który transferuje nowy raport informacji o urządzeniu.
>
> Jeśli chcesz usunąć tag dodany przy użyciu powyższego klucza rejestru, wyczyść zawartość danych klucza rejestru, zamiast usuwać klucz grupy.
