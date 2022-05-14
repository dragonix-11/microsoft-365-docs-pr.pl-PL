---
title: Włączanie ograniczonej funkcji skanowania Program antywirusowy Microsoft Defender okresowych
description: Ograniczone okresowe skanowanie umożliwia korzystanie z Program antywirusowy Microsoft Defender oprócz innych zainstalowanych dostawców av
keywords: lps, limited, periodic, scan, scan, compatibility, 3rd party, other av, disable
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 2b9320c5d7086d41be363fd01b786c98ffbc52d5
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417913"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>Użyj ograniczonego, okresowego skanowania w programie antywirusowym Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Ograniczone skanowanie okresowe to specjalny typ wykrywania zagrożeń i korygowania, który można włączyć po zainstalowaniu innego produktu antywirusowego na urządzeniu Windows 10 lub Windows 11.

Można ją włączyć tylko w pewnych sytuacjach. Aby uzyskać więcej informacji na temat ograniczonego okresowego skanowania i sposobu działania Program antywirusowy Microsoft Defender z innymi produktami antywirusowymi, zobacz [Program antywirusowy Microsoft Defender zgodność](microsoft-defender-antivirus-compatibility.md).

**Firma Microsoft nie zaleca używania tej funkcji w środowiskach przedsiębiorstwa. Jest to funkcja przeznaczona głównie dla użytkowników.** Ta funkcja używa tylko ograniczonego podzestawu Program antywirusowy Microsoft Defender możliwości wykrywania złośliwego oprogramowania i nie będzie w stanie wykryć większości złośliwego oprogramowania i potencjalnie niechcianego oprogramowania. Ponadto możliwości zarządzania i raportowania będą ograniczone. Firma Microsoft zaleca przedsiębiorstwom wybór podstawowego rozwiązania antywirusowego i używanie go wyłącznie.

## <a name="how-to-enable-limited-periodic-scanning"></a>Jak włączyć ograniczone okresowe skanowanie

Domyślnie Program antywirusowy Microsoft Defender włączy się na urządzeniu Windows 10 lub Windows 11, jeśli nie zainstalowano innego produktu antywirusowego lub jeśli inny produkt jest nieaktualny, wygasł lub nie działa poprawnie.

Jeśli Program antywirusowy Microsoft Defender jest włączona, zostaną wyświetlone zwykłe opcje konfigurowania go na tym urządzeniu:

:::image type="content" source="images/vtp-wdav.png" alt-text="Aplikacja Zabezpieczenia Windows z opcjami av usługi Microsoft Defender, w tym opcjami skanowania, ustawieniami i opcjami aktualizacji" lightbox="images/vtp-wdav.png":::

Jeśli inny produkt antywirusowy jest zainstalowany i działa poprawnie, Program antywirusowy Microsoft Defender wyłączy się. Aplikacja Zabezpieczenia Windows zmieni sekcję **Ochrona przed zagrożeniami & wirusów**, aby wyświetlić stan produktu AV i udostępni link do opcji konfiguracji produktu.

Pod dowolnymi produktami av innych firm zostanie wyświetlony nowy link **Program antywirusowy Microsoft Defender opcji**. Kliknięcie tego linku spowoduje rozwinięcie, aby wyświetlić przełącznik, który umożliwia ograniczone okresowe skanowanie. Należy pamiętać, że ograniczona opcja okresowa to przełącznik umożliwiający włączanie lub wyłączanie skanowania okresowego. 

Przesunięcie przełącznika do pozycji **Włączone** spowoduje wyświetlenie standardowych opcji usługi Microsoft Defender AV poniżej produktu AV innej firmy. Ograniczona opcja skanowania okresowego pojawi się w dolnej części strony.

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfiguruj ochronę behawioralną, heurystyczną i w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)