---
title: Określanie poziomu ochrony w chmurze dla Program antywirusowy Microsoft Defender
description: Ustaw poziom ochrony chmury dla Program antywirusowy Microsoft Defender.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, obrońca, chmura, agresywność, poziom ochrony
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.date: 08/26/2021
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 6e24be40b4ff9e57d896cf53769b578c482a2c6e
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787539"
---
# <a name="specify-the-cloud-protection-level"></a>Określ poziom ochrony w chmurze

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Ochrona w chmurze współpracuje z Program antywirusowy Microsoft Defender, aby zapewnić ochronę punktów końcowych znacznie szybciej niż w przypadku tradycyjnych aktualizacji analizy zabezpieczeń. Poziom ochrony w chmurze można skonfigurować przy użyciu Microsoft Endpoint Manager (zalecane) lub zasady grupy.

> [!NOTE]
> Wybranie pozycji **Wysoka**, **Wysoka +** lub **Zero tolerancji** może spowodować wykrycie niektórych legalnych plików. W takim przypadku możesz odblokować wykryty plik lub zakwestionować to wykrycie w portalu Microsoft 365 Defender.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>Użyj Microsoft Endpoint Manager, aby określić poziom ochrony w chmurze

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz pozycję **Program antywirusowy** zabezpieczeń \> **punktu końcowego**.

3. Wybierz profil antywirusowy. (Jeśli jeszcze go nie masz lub chcesz utworzyć nowy profil, zobacz [Konfigurowanie ustawień ograniczeń urządzenia w Microsoft Intune](/intune/device-restrictions-configure).

4. Wybierz polecenie **Właściwości**. Następnie obok pozycji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

5. Rozwiń węzeł **Ochrona w chmurze**, a następnie na liście **poziomów ochrony dostarczanej w chmurze** wybierz jedną z następujących opcji:

    - **Nie skonfigurowano: stan domyślny**.
    - **Wysoki**: stosuje silny poziom wykrywania.
    - **Wysoki plus**: używa **wysokiego** poziomu i stosuje dodatkowe środki ochrony (może mieć wpływ na wydajność klienta).
    - **Zero tolerancji**: blokuje wszystkie nieznane pliki wykonywalne.

6. Wybierz **pozycję Przeglądanie i zapisywanie**, a następnie wybierz pozycję **Zapisz**.

> [!TIP]
> Potrzebujesz pomocy? Zobacz następujące zasoby:
>
> - [Konfigurowanie Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Dodawanie ustawień ochrony punktu końcowego w Intune](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>Użyj zasady grupy, aby określić poziom ochrony chmury

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja** \> komputera **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows Components** \> **Program antywirusowy Microsoft Defender** \> **MpEngine**.

5. Kliknij dwukrotnie ustawienie **Wybierz poziom ochrony w chmurze** i ustaw go na **wartość Włączone**. Wybierz poziom ochrony:

    - **Nie skonfigurowano: stan domyślny**.
    - **Domyślny poziom blokowania** zapewnia silne wykrywanie bez zwiększania ryzyka wykrycia legalnych plików.
    - **Umiarkowany poziom blokowania** zapewnia średni poziom tylko w przypadku wykrywania wysokiego poziomu ufności
    - **Wysoki poziom blokowania** stosuje silny poziom wykrywania przy jednoczesnej optymalizacji wydajności klienta (ale może również dać większą szansę na wyniki fałszywie dodatnie).
    - **Wysoki + poziom blokowania** stosuje dodatkowe środki ochrony (może mieć wpływ na wydajność klienta i zwiększyć prawdopodobieństwo wyników fałszywie dodatnich).
    - **Poziom blokowania zerowej tolerancji** blokuje wszystkie nieznane pliki wykonywalne.

6. Wybierz przycisk **OK**.

7. Wdróż zaktualizowany obiekt zasady grupy. Zobacz [konsolę zarządzania zasady grupy](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Czy używasz obiektów zasady grupy w środowisku lokalnym? Zobacz, jak tłumaczą się w chmurze. [Analizowanie lokalnych obiektów zasad grupy przy użyciu analizy zasady grupy w Microsoft Endpoint Manager — wersja zapoznawcza](/mem/intune/configuration/group-policy-analytics).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)
  
## <a name="see-also"></a>Zobacz też

[Dlaczego ochrona w chmurze powinna być włączona dla Program antywirusowy Microsoft Defender](why-cloud-protection-should-be-on-mdav.md)
