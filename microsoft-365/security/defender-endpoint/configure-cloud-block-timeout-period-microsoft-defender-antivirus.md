---
title: Konfigurowanie limitu czasu Program antywirusowy Microsoft Defender blokowania chmury
description: Można określić, jak długo Program antywirusowy Microsoft Defender będzie blokować uruchamianie pliku podczas oczekiwania na określenie chmury.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, defender, chmura, limit czasu, blok, okres, sekundy
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 1acd1a95ddc3aa679f0e5f1295e14cf33b4f97a0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997360"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Konfigurowanie limitu czasu blokowania chmury

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Jeśli Program antywirusowy Microsoft Defender znajduje podejrzany plik, może zapobiec jego uruchamianiu podczas zapytania Program antywirusowy Microsoft Defender [w chmurze](cloud-protection-microsoft-defender-antivirus.md).

Domyślny czas blokowania [pliku to](configure-block-at-first-sight-microsoft-defender-antivirus.md) 10 sekund. Jeśli jesteś administratorem zabezpieczeń, możesz określić więcej czasu na uruchomienie pliku. Wydłużenie limitu czasu blokowania chmury może zapewnić wystarczającą ilość czasu na otrzymanie właściwej wyznaczania czasu na Program antywirusowy Microsoft Defender chmurze.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Wymagania wstępne dotyczące używania limitu czasu rozszerzonego blokowania chmury

[Blokuj na pierwszy rzut](configure-block-at-first-sight-microsoft-defender-antivirus.md) oka i jego wymagania wstępne muszą być włączone, aby można było określić dłuższy limit czasu.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>Określanie rozszerzonego limitu czasu przy Microsoft Endpoint Manager

Możesz określić okres limitu czasu blokowania chmury przy użyciu zasad zabezpieczeń [punktu końcowego w Microsoft Endpoint Manager](/mem/intune/protect/endpoint-security-policy).

1. Przejdź do Endpoint Manager administracyjnego ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)) i zaloguj się.

2. Wybierz **pozycję Zabezpieczenia punktu końcowego**, a następnie w **obszarze Zarządzanie** wybierz pozycję **Oprogramowanie antywirusowe**.

3. Wybierz (lub utwórz) zasady antywirusowe.

4. W sekcji **Ustawienia konfiguracji** rozwiń pozycję **Ochrona w chmurze**. Następnie w polu **Program antywirusowy Microsoft Defender Limit** czasu w sekundach określ czas (w sekundach) z 1 sekundy do 50 sekund. Domyślną wartość 10 sekund zostanie dodana do wartości domyślnej 10 sekund.

5. (Ten krok jest opcjonalny) W tym celu należy wprowadzić inne zmiany w zasadach oprogramowania antywirusowego. (Potrzebujesz pomocy? Zobacz [Ustawienia, Program antywirusowy Microsoft Defender w Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)).

6. Wybierz **pozycję** Dalej i zakończ konfigurowanie zasad.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>Określanie rozszerzonego limitu czasu przy zasady grupy

Możesz użyć zasady grupy, aby określić rozszerzony limit czasu dla testów w chmurze.

1. Na komputerze zasady grupy zarządzania usługami otwórz [konsolę zasady grupy zarządzania](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **administracyjnym zasady grupy zarządzania** przejdź do **strony Konfiguracja komputera**, a następnie wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **MpEngine**.

4. Kliknij dwukrotnie pozycję **Konfiguruj rozszerzone sprawdzanie w chmurze** i upewnij się, że ta opcja jest włączona. 

   Określenie dodatkowego czasu uniemożliwiającego uruchamianie pliku podczas oczekiwania na określenie chmury. Określ dodatkowy czas (w sekundach) z 1 sekundy do 50 sekund. Domyślną wartość 10 sekund zostanie dodana do wartości domyślnej 10 sekund.

5. Wybierz przycisk **OK**.

 
