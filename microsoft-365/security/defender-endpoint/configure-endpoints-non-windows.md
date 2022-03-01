---
title: Dołączanie urządzeń innych niż Windows do usługi Microsoft Defender for Endpoint
description: Skonfiguruj urządzenia Windows, aby wysyłały dane czujnika do usługi Microsoft Defender for Endpoint.
keywords: onboard non-Windows devices, macos, linux, device management, configure Microsoft Defender for Endpoint devices
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4573e7002454e9e72648df42352104abaa4c22d6
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019242"
---
# <a name="onboard-non-windows-devices"></a>Urządzenia Windows urządzeniach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platformy**
- macOS
- Linux

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-nonwindows-abovefoldlink)

Program Defender for Endpoint udostępnia scentralizowane środowisko operacji zabezpieczeń dla Windows i innych Windows platform. W programie Microsoft 365 Defender będziesz widzieć alerty z różnych obsługiwanych systemów operacyjnych i lepiej chronić sieć organizacji.

Aby integracja działała, musisz znać dokładne wersje systemu Linux i macOS zgodne z programem Defender for Endpoint. Więcej informacji można znaleźć w następujących artykułach:

- [Wymagania systemowe programu Microsoft Defender dla punktu końcowego systemu Linux](microsoft-defender-endpoint-linux.md#system-requirements)
- [Program Microsoft Defender for Endpoint w wymaganiach systemowych systemu macOS](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>Wniesienie urządzeń Windows inne niż urządzenia

Aby na urządzeniach innych niż Windows, należy wykonać Windows czynności:

1. Wybierz preferowaną metodę dołączania:

   - W przypadku urządzeń z systemem macOS możesz wybrać opcję doniania się w programie Microsoft Defender for Endpoint lub za pośrednictwem rozwiązania innej firmy. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint na komputerze Mac](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac).

   - W przypadku innych urządzeń Windows wybierz opcję **Na urządzeniach Windows przez integrację z innymi firmami**.
    1. W okienku nawigacji wybierz pozycję **Partnerzy i aplikacje partnerów interfejsów** \> **API** . Upewnij się, że na liście znajduje się rozwiązanie innej firmy.
    2. Na stronie **Aplikacje partnerskie** wybierz partnera, który obsługuje Twoje urządzenia Windows inne niż.
    3. Kliknij **pozycję** Wyświetl, aby otworzyć stronę partnera. Postępuj zgodnie z instrukcjami wyświetlanymi na stronie.
    4. Po utworzeniu konta lub zas subskrybowania rozwiązania partnera musisz rozpocząć etap, w którym administrator globalny dzierżawy w Twojej organizacji jest proszony o zaakceptowanie żądania uprawnień z aplikacji partnera. Uważnie przeczytaj żądanie uprawnień, aby upewnić się, że jest ono zgodne z wymaganą usługą.

2. Uruchom test wykrywania, korzystając z instrukcji rozwiązania innej firmy.

## <a name="offboard-non-windows-devices"></a>Urządzenia niezwiązy Windows od urządzenia

W przypadku urządzeń z systemami macOS i Linux możesz wybrać, czy chcesz wystartować z programu Microsoft Defender for Endpoint. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Wybierz** \> **system operacyjny, aby rozpocząć proces wywę owania**.

Wyłączenie integracji z urządzeniami innych firm Windows wyłączanie urządzeń innych firm. Włączenie ochrony dla urządzeń, które nie Windows platform, [integrując rozwiązania innych firm](https://security.microsoft.com/interoperability/partners).

## <a name="related-topics"></a>Tematy pokrewne
- [Urządzenia Windows urządzeniach](configure-endpoints.md)
- [Serwery wsadowe](configure-server-endpoints.md)
- [Konfigurowanie ustawień serwera proxy i łączności internetowej](configure-proxy-internet.md)
- [Rozwiązywanie problemów z dołączaniem do programu Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
