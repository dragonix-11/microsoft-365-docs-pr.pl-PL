---
title: Konfigurowanie wykluczeń dla skanowania Program antywirusowy Microsoft Defender
description: Można wykluczyć pliki (w tym pliki zmodyfikowane przez określone procesy) i foldery ze skanowania przez Program antywirusowy Microsoft Defender. Weryfikowanie wykluczeń za pomocą programu PowerShell.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.technology: mde
ms.audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: c9796f4e5154fd46d1479f0cbfa25f2afaf4e9bb
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787517"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Konfigurowanie i weryfikowanie wykluczeń dla skanowania Program antywirusowy Microsoft Defender

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Niektóre pliki, foldery, procesy i pliki otwierane przez proces można wykluczyć ze skanowania Program antywirusowy Microsoft Defender. Takie wykluczenia mają zastosowanie do [zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [skanów na żądanie](run-scan-microsoft-defender-antivirus.md) oraz [zawsze włączonej ochrony i monitorowania w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md). Wykluczenia dla plików otwartych przez proces mają zastosowanie tylko do ochrony w czasie rzeczywistym.

## <a name="configure-and-validate-exclusions"></a>Konfiguruj i weryfikuj wykluczenia

Aby skonfigurować i zweryfikować wykluczenia, zobacz następujące kwestie:

- [Skonfiguruj i zweryfikuj wykluczenia na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Pliki ze skanowania Program antywirusowy Microsoft Defender można wykluczyć na podstawie ich rozszerzenia pliku, nazwy pliku lub lokalizacji.

- [Konfigurowanie i weryfikowanie wykluczeń dla plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Można wykluczyć pliki ze skanów, które zostały otwarte przez określony proces.

## <a name="recommendations-for-defining-exclusions"></a>Rekomendacje definiowania wykluczeń

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender obejmuje wiele automatycznych wykluczeń opartych na znanych zachowaniach systemu operacyjnego i typowych plikach zarządzania, takich jak te używane w zarządzaniu przedsiębiorstwem, zarządzaniu bazami danych i innych scenariuszach i sytuacjach przedsiębiorstwa.
>
> Definiowanie wykluczeń obniża ochronę oferowaną przez Program antywirusowy Microsoft Defender. Należy zawsze oceniać ryzyko związane z implementowaniem wykluczeń i należy wykluczać tylko pliki, które są pewne, że nie są złośliwe.

Podczas definiowania wykluczeń należy pamiętać o następujących kwestiach:

- Wykluczenia są technicznie luką w ochronie. Podczas definiowania wykluczeń rozważ wszystkie opcje. Inne opcje mogą być tak proste, jak upewnienie się, że wykluczona lokalizacja ma odpowiednie listy kontroli dostępu (ACL) lub ustawienie zasad trybu inspekcji na początku.

- Okresowo przeglądaj wykluczenia. Ponowne sprawdzanie i ponowne wymuszanie środków zaradczych w ramach procesu przeglądu.

- Najlepiej unikać definiowania wykluczeń w celu proaktywnego działania. Na przykład nie wykluczaj czegoś tylko dlatego, że uważasz, że może to być problem w przyszłości. Wykluczeń należy używać tylko w przypadku określonych problemów, takich jak problemy dotyczące wydajności lub zgodności aplikacji, które mogą uniknąć wykluczeń.

- Przejrzyj i przeprowadź inspekcję zmian na liście wykluczeń. Twój zespół ds. zabezpieczeń powinien zachować kontekst dotyczący przyczyn dodania określonego wykluczenia, aby uniknąć pomyłek w dalszej części. Twój zespół ds. zabezpieczeń powinien mieć możliwość udzielenia konkretnych odpowiedzi na pytania dotyczące przyczyn istnienia wykluczeń.

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

- [Program antywirusowy Microsoft Defender wykluczeń dotyczących Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Typowe błędy, których należy unikać podczas definiowania wykluczeń](common-exclusion-mistakes-microsoft-defender-antivirus.md)
