---
title: Blokowanie zachowania klienta
description: Blokowanie zachowania klienta jest częścią funkcji blokowania zachowania i blokowania jej na stronie Ochrona punktu końcowego w usłudze Microsoft Defender
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
ms.openlocfilehash: 8da3f04af66568bbe79dd6a74c38b30a8a1ab891
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470224"
---
# <a name="client-behavioral-blocking"></a>Blokowanie zachowania klienta

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Omówienie

Blokowanie zachowania klienta jest składnikiem funkcji blokowania [zachowania i blokowania w](behavioral-blocking-containment.md) programie Defender for Endpoint. W przypadku wykrycia podejrzanych zachowań na urządzeniach (nazywanych również klientami lub punktami końcowymi) artefakty (takie jak pliki lub aplikacje) są automatycznie blokowane, sprawdzane i naprawiane.

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="Ochrona chmury i klienta" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

Ochrona antywirusowa działa najlepiej w połączeniu z ochroną chmury.

## <a name="how-client-behavioral-blocking-works"></a>Jak działa blokowanie zachowania klienta

[Program antywirusowy Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) wykrywać podejrzane zachowanie, złośliwy kod, ataki bez plików i w pamięci i nie tylko na urządzeniu. W przypadku wykrycia podejrzanych zachowań monitoruje Program antywirusowy Microsoft Defender i wysyła te podejrzane zachowania oraz ich drzewa procesu do usługi ochrony chmury. Uczenie maszynowe rozróżnia złośliwe aplikacje i dobre zachowania w milisekundach, a także klasyfikuje poszczególne artefakty. Niemal w czasie rzeczywistym, gdy tylko artefakt zostanie znaleziony jako złośliwy, zostanie on zablokowany na urządzeniu.

W przypadku wykrycia podejrzanego zachowania jest generowany [alert](alerts-queue.md) widoczny w informacjach Podczas wykrycia i zatrzymania ataków alerty, takie jak "alert dostępu początkowego", były wyzwalane i pojawiały się w portalu programu [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) (dawniej Microsoft 365 Defender).

Blokowanie zachowań klientów obowiązuje, ponieważ pomaga nie tylko zapobiegać rozpoczęciu ataków, ale także zatrzymywać rozpoczęty przez niego atak. Ponadto w przypadku blokowania [pętli opinii](feedback-loop-blocking.md) (kolejna funkcja blokowania zachowań i blokowania treści) ataki są blokowane na innych urządzeniach w organizacji.

## <a name="behavior-based-detections"></a>Wykrywanie oparte na zachowaniu

Wykrywanie oparte na zachowaniu jest nazwane zgodnie z [miTRE ATT i&CK Matrix for Enterprise](https://attack.mitre.org/matrices/enterprise). Konwencja nazewnictwa pomaga zidentyfikować etap ataków, w którym zostało obserwowane złośliwe zachowanie:

|Emotikon|Nazwa zagrożenia wykrywania|
|---|---|
|Dostęp wstępny|`Behavior:Win32/InitialAccess.*!ml`|
|Wykonywanie|`Behavior:Win32/Execution.*!ml`|
|Persistence|`Behavior:Win32/Persistence.*!ml`|
|Eskalacji uprawnień|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|Obrona|`Behavior:Win32/DefenseEvasion.*!ml`|
|Dostęp poświadczeń|`Behavior:Win32/CredentialAccess.*!ml`|
|Odnajdowanie|`Behavior:Win32/Discovery.*!ml`|
|Ruch lateralny|`Behavior:Win32/LateralMovement.*!ml`|
|Kolekcja|`Behavior:Win32/Collection.*!ml`|
|Command and Control|`Behavior:Win32/CommandAndControl.*!ml`|
|Ex przeocły|`Behavior:Win32/Exfiltration.*!ml`|
|Wpływ|`Behavior:Win32/Impact.*!ml`|
|Bez kategorii|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> Aby dowiedzieć się więcej o konkretnych zagrożeniach, zobacz **[Ostatnia globalna aktywność zagrożeń](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>Konfigurowanie blokowania zachowania klienta

Jeśli Twoja organizacja używa programu Defender for Endpoint, blokowanie zachowania klienta jest domyślnie włączone. Jednak aby korzystać ze wszystkich funkcji programu Defender dla punktu końcowego, w tym blokowania i blokowania [zachowań, upewnij](behavioral-blocking-containment.md) się, że włączono i skonfigurowano następujące funkcje i możliwości usługi Defender for Endpoint:

- [Defender for Endpoint baselines](configure-machines-security-baseline.md)
- [Urządzenia podłączone do usługi Defender for Endpoint](onboard-configure.md)
- [EDR w trybie blokowania](edr-in-block-mode.md)
- [Zmniejszanie obszaru podatnego na ataki](attack-surface-reduction.md)
- [Ochrona następnej generacji](configure-microsoft-defender-antivirus-features.md) (funkcje ochrony przed złośliwym oprogramowaniem i oprogramowanie antywirusowe oraz inne funkcje ochrony przed zagrożeniami)
