---
title: Określanie poziomu ochrony w chmurze dla Program antywirusowy Microsoft Defender
description: Ustaw poziom ochrony przed Program antywirusowy Microsoft Defender.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, defender, chmura, agresywność, poziom ochrony
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
ms.openlocfilehash: 4723b84e285e508e33ca4b54a1897bbed036a897
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996275"
---
# <a name="specify-the-cloud-protection-level"></a>Określanie poziomu ochrony w chmurze

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Program antywirusowy Microsoft Defender

Ochrona chmury współpracuje z usługą Program antywirusowy Microsoft Defender dostarczania ochrony do punktów końcowych znacznie szybciej niż za pośrednictwem tradycyjnych aktualizacji analizy zabezpieczeń. Poziom ochrony chmury można skonfigurować przy użyciu Microsoft Endpoint Manager (zalecane) lub zasady grupy.

> [!NOTE]
> Wybranie **opcji** **Tolerancja wysoka, Wysoka +** lub **Zero** może spowodować wykrycie niektórych legalnych plików. W takim przypadku możesz odblokować wykryty plik lub spór, który został wykryty w portalu Microsoft 365 Defender sieci.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>Określanie Microsoft Endpoint Manager w chmurze za pomocą funkcji

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz pozycję **Endpoint security Antivirus (Zabezpieczenia punktu końcowego**\>).

3. Wybierz profil antywirusowy. (Jeśli nie masz jeszcze profilu lub chcesz utworzyć nowy profil, zobacz Konfigurowanie ustawień ograniczeń urządzeń w aplikacji [Microsoft Intune](/intune/device-restrictions-configure).

4. Wybierz **pozycję Właściwości**. Następnie obok ustawień **konfiguracji wybierz** pozycję **Edytuj**.

5. **Rozwiń pozycję Ochrona** w chmurze, a następnie na liście **Poziom ochrony w** chmurze wybierz jedną z następujących opcji:

    - **Nieskonfigurowane**: Stan domyślny.
    - **Wysoka**: stosuje wysoki poziom wykrywania.
    - **Wysoka plus**: korzysta **z najwyższego** poziomu i stosuje dodatkowe środki ochrony (może to wpłynąć na wydajność klienta).
    - **Zero tolerancji**: Blokuje wszystkie nieznane pliki wykonywalne.

6. Wybierz **pozycję Recenzja + zapisywanie**, a następnie wybierz **pozycję Zapisz**.

> [!TIP]
> Potrzebujesz pomocy? Zobacz następujące zasoby:
>
> - [Konfigurowanie Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Dodawanie ustawień ochrony punktu końcowego w usłudze Intune](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>Określanie zasady grupy w chmurze za pomocą zasady grupy

1. Na komputerze zasady grupy zarządzania usługami otwórz [konsolę zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **administracyjnym zasady grupy zarządzania przejdź** do **strony Szablony administracyjne konfiguracji** \> **komputera**.

4. Rozwiń drzewo, **aby Windows Składniki Program antywirusowy Microsoft Defender** \>  \> **MpEngine**.

5. Kliknij dwukrotnie ustawienie **Wybierz poziom ochrony w** chmurze i ustaw je jako **Włączone**. Wybierz poziom ochrony:

    - **Nieskonfigurowane**: Stan domyślny.
    - **Domyślny poziom blokowania zapewnia** silne wykrywanie bez zwiększania ryzyka wykrycia legalnych plików.
    - **Moderate blocking level** provides moderate only for high confidence detections
    - **Wysoki poziom blokowania** powoduje zastosowanie silnego poziomu wykrywania przy jednoczesnym optymalizacji wydajności klienta (ale zwiększa też prawdopodobieństwo wyników fałszywie dodatnich).
    - **Wysoki poziom + blokowanie powoduje** zastosowanie dodatkowych środków ochrony (może to wpłynąć na wydajność klienta i zwiększyć prawdopodobieństwo wyników fałszywie dodatnich).
    - **Zero tolerancji blokujące poziom** blokuje wszystkie nieznane pliki wykonywalne.

6. Wybierz przycisk **OK**.

7. Wdeksuj zaktualizowany obiekt zasady grupy obiekt. Zobacz [zasady grupy zarządzania](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Czy używasz lokalnego zasady grupy? Zobacz, jak tłumaczą się w chmurze. [Analizuj lokalne obiekty zasad grupy przy użyciu analizy zasady grupy w aplikacji Microsoft Endpoint Manager Podgląd](/mem/intune/configuration/group-policy-analytics).
  
## <a name="see-also"></a>Zobacz też

[Dlaczego ochrona chmury powinna być włączona dla Program antywirusowy Microsoft Defender](why-cloud-protection-should-be-on-mdav.md)
