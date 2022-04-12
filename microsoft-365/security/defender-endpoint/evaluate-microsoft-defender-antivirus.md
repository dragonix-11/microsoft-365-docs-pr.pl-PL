---
title: Oceń program antywirusowy Microsoft Defender
description: Firmy każdej wielkości mogą korzystać z tego przewodnika, aby ocenić i przetestować ochronę oferowaną przez Program antywirusowy Microsoft Defender w Windows.
keywords: Program antywirusowy Microsoft Defender, ochrona w chmurze, chmura, oprogramowanie chroniące przed złośliwym kodem, zabezpieczenia, ochrona, ocena, testowanie, ochrona, porównanie, ochrona w czasie rzeczywistym
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
ms.openlocfilehash: 8c7ced9c85ec7c6075b44970d25e34ba5594404e
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787643"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Oceń program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- Program antywirusowy Microsoft Defender
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 

**Platformy**
- System Windows

Skorzystaj z tego przewodnika, aby określić, jak dobrze Program antywirusowy Microsoft Defender chroni przed wirusami, złośliwym oprogramowaniem i potencjalnie niepożądanymi aplikacjami.

> [!TIP]
>Możesz również odwiedzić witrynę internetową Ochrona punktu końcowego w usłudze Microsoft Defender demo pod adresem [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground), aby potwierdzić, że działają następujące funkcje i zobaczyć, jak działają:
>
> - Ochrona dostarczana przez chmurę
> - Szybkie uczenie się (w tym Blok od pierwszego wejrzenia)
> - Potencjalnie niepożądane blokowanie aplikacji

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

Wyjaśniono w nim ważne funkcje ochrony nowej generacji Program antywirusowy Microsoft Defender dostępne zarówno dla małych, jak i dużych przedsiębiorstw oraz jak zwiększają one wykrywanie złośliwego oprogramowania i ochronę w sieci.

Możesz skonfigurować i ocenić każde ustawienie niezależnie lub wszystkie jednocześnie. Pogrupowaliśmy podobne ustawienia na podstawie typowych scenariuszy oceny i uwzględniliśmy instrukcje dotyczące korzystania z programu PowerShell w celu włączenia ustawień.

Przewodnik jest dostępny w formacie PDF do wyświetlania w trybie offline:

- [Pobierz przewodnik w formacie PDF](https://www.microsoft.com/download/details.aspx?id=54795)

Możesz również pobrać program PowerShell, który automatycznie włączy wszystkie ustawienia opisane w przewodniku. Skrypt można uzyskać razem z powyższym plikiem PDF lub osobno z Galeria programu PowerShell:

- [Pobierz skrypt programu PowerShell, aby automatycznie skonfigurować ustawienia](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Przewodnik jest obecnie przeznaczony do oceny Program antywirusowy Microsoft Defender na jednej maszynie. Włączenie wszystkich ustawień w tym przewodniku może nie być odpowiednie do wdrożenia w świecie rzeczywistym.
>
> Aby uzyskać najnowsze zalecenia dotyczące rzeczywistego wdrażania i monitorowania Program antywirusowy Microsoft Defender w sieci, zobacz [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="related-topics"></a>Tematy pokrewne

- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)