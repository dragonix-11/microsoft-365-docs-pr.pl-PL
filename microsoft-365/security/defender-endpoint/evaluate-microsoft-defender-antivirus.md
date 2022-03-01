---
title: Szacowanie Program antywirusowy Microsoft Defender
description: Firmy o wszystkich rozmiarach mogą skorzystać z tego przewodnika w celu oceny i przetestowania ochrony oferowanej przez firmę Program antywirusowy Microsoft Defender w Windows.
keywords: Program antywirusowy Microsoft Defender, ochrona chmury, chmura, ochrona przed złośliwym kodem, zabezpieczenia, defender, ocenianie, testowanie, ochrona, porównanie, ochrona w czasie rzeczywistym
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 4dd25a599f144a60bfd2ebeb3e9bb8b1876bd3c6
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014710"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Szacowanie Program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Skorzystaj z tego przewodnika, aby ustalić, Program antywirusowy Microsoft Defender chroni Cię przed wirusami, złośliwym oprogramowaniem i potencjalnie niechcianymi aplikacjami.

> [!TIP]
>Możesz również odwiedzić witrynę pokazu programu Microsoft Defender for Endpoint w witrynie [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) , aby sprawdzić, czy działają następujące funkcje i jak działają:
>
> - Ochrona w chmurze
> - Szybkie uczenie się (w tym blokowanie od pierwszego rzutu)
> - Potencjalnie niechciane blokowanie aplikacji

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

Opisano w nim istotne funkcje ochrony nowej generacji w p Program antywirusowy Microsoft Defender są dostępne zarówno dla małych, jak i dużych przedsiębiorstw, oraz wyjaśniono, jak zwiększają one wykrywanie złośliwego oprogramowania i ochronę w sieci.

Możesz skonfigurować i ocenić poszczególne ustawienia niezależnie lub wszystkie naraz. Pogrupowane zostały podobne ustawienia w oparciu o typowe scenariusze oceny i pogrupowane zostały instrukcje dotyczące włączania tych ustawień przy użyciu programu PowerShell.

Przewodnik jest dostępny w formacie PDF do wyświetlania w trybie offline:

- [Pobierz przewodnik w formacie PDF](https://www.microsoft.com/download/details.aspx?id=54795)

Możesz również pobrać program PowerShell, który automatycznie włączy wszystkie ustawienia opisane w tym przewodniku. Skrypt można uzyskać obok powyższego pliku PDF lub pojedynczo z galerii programu PowerShell:

- [Pobieranie skryptu programu PowerShell w celu automatycznego skonfigurowania ustawień](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Ten przewodnik jest obecnie przeznaczony do oceny wyników oceny wyników Program antywirusowy Microsoft Defender. Włączenie wszystkich ustawień w tym przewodniku może nie być odpowiednie do wdrożenia w świecie rzeczywistym.
>
> Aby uzyskać najnowsze zalecenia dotyczące wdrażania i monitorowania Program antywirusowy Microsoft Defender w sieci, zobacz [Wdrażanie](deploy-manage-report-microsoft-defender-antivirus.md) Program antywirusowy Microsoft Defender.

## <a name="related-topics"></a>Tematy pokrewne

- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)