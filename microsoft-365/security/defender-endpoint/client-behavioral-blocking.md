---
title: Blokowanie behawioralne klienta
description: Blokowanie zachowań klientów jest częścią funkcji blokowania i powstrzymywania zachowań w Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: blokowanie zachowań, szybka ochrona, zachowanie klienta, Ochrona punktu końcowego w usłudze Microsoft Defender
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: f19e354a23af03abd905591993197ff8f484ceff
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788397"
---
# <a name="client-behavioral-blocking"></a>Blokowanie behawioralne klienta

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platforma**
- System Windows

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Omówienie

Blokowanie zachowania klienta jest składnikiem [funkcji blokowania i powstrzymywania zachowań](behavioral-blocking-containment.md) w usłudze Defender for Endpoint. Ponieważ podejrzane zachowania są wykrywane na urządzeniach (nazywanych również klientami lub punktami końcowymi), artefakty (takie jak pliki lub aplikacje) są blokowane, sprawdzane i korygowane automatycznie.

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="Ochrona chmury i klienta" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

Ochrona antywirusowa działa najlepiej w połączeniu z ochroną w chmurze.

## <a name="how-client-behavioral-blocking-works"></a>Jak działa blokowanie zachowania klienta

[Program antywirusowy Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) może wykrywać podejrzane zachowanie, złośliwy kod, ataki bez plików i ataków w pamięci i nie tylko na urządzeniu. Po wykryciu podejrzanych zachowań Program antywirusowy Microsoft Defender monitoruje i wysyła te podejrzane zachowania i drzewa procesów do usługi ochrony chmury. Uczenie maszynowe rozróżnia złośliwe aplikacje i dobre zachowania w milisekundach i klasyfikuje każdy artefakt. Niemal w czasie rzeczywistym, gdy tylko artefakt zostanie uznany za złośliwy, zostanie zablokowany na urządzeniu.

Za każdym razem, gdy zostanie wykryte podejrzane zachowanie, [alert](alerts-queue.md) jest generowany i widoczny, gdy atak został wykryty i zatrzymany; alerty, takie jak "alert dostępu początkowego", są wyzwalane i wyświetlane w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) (dawniej Microsoft 365 Defender).

Blokowanie zachowania klienta jest skuteczne, ponieważ nie tylko pomaga zapobiec rozpoczęciu ataku, ale może pomóc zatrzymać atak, który rozpoczął się. Ponadto w przypadku [blokowania pętli sprzężenia zwrotnego](feedback-loop-blocking.md) (innej możliwości blokowania i powstrzymywania zachowań) ataki są blokowane na innych urządzeniach w organizacji.

## <a name="behavior-based-detections"></a>Wykrywanie oparte na zachowaniu

Wykrywanie oparte na zachowaniu jest określane zgodnie z [macierzą&CK MITRE ATT dla Enterprise](https://attack.mitre.org/matrices/enterprise). Konwencja nazewnictwa pomaga zidentyfikować etap ataku, w którym zaobserwowano złośliwe zachowanie:

|Taktyka|Nazwa zagrożenia wykrywania|
|---|---|
|Dostęp początkowy|`Behavior:Win32/InitialAccess.*!ml`|
|Wykonanie|`Behavior:Win32/Execution.*!ml`|
|Trwałości|`Behavior:Win32/Persistence.*!ml`|
|Eskalacja uprawnień|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|Uchylanie się od obrony|`Behavior:Win32/DefenseEvasion.*!ml`|
|Dostęp poświadczeń|`Behavior:Win32/CredentialAccess.*!ml`|
|Odnajdywania|`Behavior:Win32/Discovery.*!ml`|
|Ruch boczny|`Behavior:Win32/LateralMovement.*!ml`|
|Kolekcji|`Behavior:Win32/Collection.*!ml`|
|Polecenie i kontrolka|`Behavior:Win32/CommandAndControl.*!ml`|
|Eksfiltracja|`Behavior:Win32/Exfiltration.*!ml`|
|Wpływ|`Behavior:Win32/Impact.*!ml`|
|Uncategorized|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> Aby dowiedzieć się więcej na temat konkretnych zagrożeń, zobacz **[ostatnie działania związane z globalnymi zagrożeniami](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>Konfigurowanie blokowania behawioralnego klienta

Jeśli Twoja organizacja używa usługi Defender for Endpoint, blokowanie zachowań klientów jest domyślnie włączone. Jednak aby skorzystać ze wszystkich możliwości usługi Defender for Endpoint, w tym [blokowania behawioralnego i powstrzymywania](behavioral-blocking-containment.md), upewnij się, że następujące funkcje i możliwości usługi Defender for Endpoint są włączone i skonfigurowane:

- [Punkty odniesienia usługi Defender dla punktów końcowych](configure-machines-security-baseline.md)
- [Urządzenia dołączone do usługi Defender for Endpoint](onboard-configure.md)
- [Funkcja EDR w trybie blokowania](edr-in-block-mode.md)
- [Zmniejszanie obszaru podatnego na ataki](attack-surface-reduction.md)
- [Ochrona nowej generacji](configure-microsoft-defender-antivirus-features.md) (oprogramowanie antywirusowe, oprogramowanie chroniące przed złośliwym kodem i inne możliwości ochrony przed zagrożeniami)

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)
