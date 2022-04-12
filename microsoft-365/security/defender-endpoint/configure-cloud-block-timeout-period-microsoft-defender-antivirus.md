---
title: Konfigurowanie okresu limitu czasu blokady chmury Program antywirusowy Microsoft Defender
description: Możesz skonfigurować, jak długo Program antywirusowy Microsoft Defender zablokuje uruchamianie pliku podczas oczekiwania na określenie chmury.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, defender, chmura, przekroczenie limitu czasu, blok, kropka, sekundy
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
ms.openlocfilehash: 9669bb17b8e970427fb9c35c5f24d35e247b720b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790575"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Skonfiguruj limit czasu blokady chmury

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Gdy Program antywirusowy Microsoft Defender znajdzie podejrzany plik, może uniemożliwić uruchomienie pliku podczas wykonywania zapytań w [usłudze Program antywirusowy Microsoft Defender w chmurze](cloud-protection-microsoft-defender-antivirus.md).

Domyślny okres, przez który plik jest [blokowany](configure-block-at-first-sight-microsoft-defender-antivirus.md) , wynosi 10 sekund. Jeśli jesteś administratorem zabezpieczeń, możesz określić więcej czasu oczekiwania, zanim plik będzie mógł zostać uruchomiony. Wydłużenie okresu przekroczenia limitu czasu bloku chmury może pomóc w zapewnieniu wystarczającej ilości czasu na otrzymanie odpowiedniego określenia z usługi w chmurze Program antywirusowy Microsoft Defender.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Wymagania wstępne dotyczące korzystania z rozszerzonego limitu czasu blokady chmury

Aby można było określić dłuższy limit czasu, należy włączyć ustawienie [Blokuj od pierwszego wejrzenia](configure-block-at-first-sight-microsoft-defender-antivirus.md) i jego wymagania wstępne.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>Określ rozszerzony okres limitu czasu przy użyciu Microsoft Endpoint Manager

Okres limitu czasu bloku chmury można określić przy użyciu [zasad zabezpieczeń punktu końcowego w Microsoft Endpoint Manager](/mem/intune/protect/endpoint-security-policy).

1. Przejdź do centrum administracyjnego Endpoint Manager ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)) i zaloguj się.

2. Wybierz pozycję **Zabezpieczenia punktu końcowego**, a następnie w obszarze **Zarządzanie** wybierz pozycję **Oprogramowanie antywirusowe**.

3. Wybierz (lub utwórz) zasady ochrony antywirusowej.

4. W sekcji **Ustawienia konfiguracji** rozwiń węzeł **Ochrona w chmurze**. Następnie w **polu Program antywirusowy Microsoft Defender Extended Timeout In Seconds (Rozszerzony limit czasu w sekundach**) określ więcej czasu w sekundach od 1 sekundy do 50 sekund. Cokolwiek określisz, zostanie dodane do domyślnych 10 sekund.

5. (Ten krok jest opcjonalny) Wprowadź inne zmiany w zasadach ochrony antywirusowej. (Potrzebujesz pomocy? Zobacz [Ustawienia, aby uzyskać informacje o zasadach Program antywirusowy Microsoft Defender w Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)).

6. Wybierz pozycję **Dalej** i zakończ konfigurowanie zasad.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>Określ rozszerzony okres limitu czasu przy użyciu zasady grupy

Możesz użyć zasady grupy, aby określić rozszerzony limit czasu na kontrole w chmurze.

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**, a następnie wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **MpEngine**.

4. Kliknij **dwukrotnie pozycję Konfiguruj rozszerzone sprawdzanie chmury** i upewnij się, że opcja jest włączona. 

   Określ dodatkową ilość czasu, aby zapobiec uruchomieniu pliku podczas oczekiwania na określenie chmury. Określ dodatkowy czas w sekundach od 1 sekundy do 50 sekund. Cokolwiek określisz, zostanie dodane do domyślnych 10 sekund.

5. Wybierz przycisk **OK**.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md) 
