---
title: Rozwiązywanie problemów dotyczących kondycji czujnika przy użyciu programu Microsoft Defender for Endpoint Client Analyzer
description: Rozwiązywanie problemów dotyczących kondycji czujnika na urządzeniach w celu zidentyfikowania potencjalnej konfiguracji, środowiska, łączności lub telemetrii wpływających na dane lub możliwości czujnika.
keywords: czujnik, kondycja czujnika, nieprawidłowo skonfigurowane, nieaktywne, bez danych czujnika, dane czujnika, zakłócona komunikacja, komunikacja
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 9b4363b529ce9087e640c9bfaa32c8d21f410710
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017900"
---
# <a name="troubleshoot-sensor-health-using-microsoft-defender-for-endpoint-client-analyzer"></a>Rozwiązywanie problemów dotyczących kondycji czujnika przy użyciu programu Microsoft Defender for Endpoint Client Analyzer

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Program Microsoft Defender for Endpoint Client Analyzer (MDECA) może być przydatny w przypadku diagnozowania problemów z kondycją i niezawodnością czujnika [](/microsoft-365/security/defender-endpoint/onboard-configure) na urządzeniach we wnoszach z systemem Windows, Linux lub macOS. Na przykład możesz chcieć uruchomić analizatora na komputerze, który wydaje się nie działać zgodnie ze stanem kondycji wyświetlanego [czujnika (](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors) Nieaktywny, Bez danych czujnika lub Ograniczona komunikacja) w portalu zabezpieczeń.

Oprócz oczywistej kondycji czujnika MDECA może zbierać inne śledzenia, dzienniki i informacje diagnostyczne na potrzeby rozwiązywania złożonych scenariuszy, takich jak:

- Zgodność aplikacji (AppCompat), wydajność, łączność sieciowa lub
- Nieoczekiwane zachowanie związane z [zapobieganiem utracie danych w punkcie końcowym](/microsoft-365/compliance/endpoint-dlp-learn-about).

## <a name="privacy-notice"></a>Zasady zachowania poufności informacji

- Narzędzie Microsoft Defender for Endpoint Client Analyzer jest regularnie używane przez usługi obsługi klienta firmy Microsoft (CSS) do zbierania informacji pomocnych w rozwiązywaniu problemów, które mogą wystąpić w programie Microsoft Defender for Endpoint.

- Zbierane dane mogą zawierać dane umożliwiające identyfikację użytkownika i/lub dane poufne, takie jak (ale nie wyłącznie) adresy IP, nazwy komputerów i nazwy użytkowników.

- Po zakończeniu zbierania danych narzędzie zapisuje dane lokalnie na komputerze w podfolderze i skompresowanym pliku zip.

- Żadne dane nie są automatycznie wysyłane do firmy Microsoft. Jeśli korzystasz z tego narzędzia podczas współpracy nad problemem z pomocą techniczną, może zostaćsz poproszony o wysłanie skompresowanych danych do arkusza Microsoft CSS za pomocą bezpiecznego pliku Exchange w celu ułatwienia badania problemu.

Aby uzyskać więcej informacji na temat bezpiecznego Exchange pliku, zobacz Jak używać bezpiecznego pliku i Exchange do wymiany plików za [pomocą pomocy technicznej firmy Microsoft.](/troubleshoot/azure/general/secure-file-exchange-transfer-files)

Aby uzyskać więcej informacji na temat zasad zachowania poufności informacji, zobacz [Oświadczenie o ochronie prywatności firmy Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="requirements"></a>Wymagania

- Przed uruchomieniem analizatora zalecamy zapewnienie, że konfiguracja serwera proxy lub zapory umożliwia dostęp do usługi Microsoft Defender pod adresami [URL usługi punktu końcowego](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- Analizator może działać na obsługiwanych wersjach systemu [Windows](minimum-requirements.md#supported-windows-versions), [Linux](microsoft-defender-endpoint-linux.md#system-requirements) lub [macOS](microsoft-defender-endpoint-mac.md#system-requirements) przed dodaniem do usługi Microsoft Defender for Endpoint.

- W Windows urządzeniach, jeśli analizator jest uruchomiony bezpośrednio na określonych komputerach, a nie zdalnie za pośrednictwem funkcji [Live Response](/microsoft-365/security/defender-endpoint/troubleshoot-collect-support-log), wówczas uruchamianie narzędzia SysInternals [PsExec.exe](/sysinternals/downloads/psexec) powinno być dozwolone (przynajmniej tymczasowo). Analizator dzwoni do narzędzia PsExec.exe do uruchamiania testów łączności w chmurze jako systemu lokalnego i emulowania zachowania usługi SENSE.

    > [!NOTE]
    > Jeśli na urządzeniach z systemem Windows użyjesz reguły zmniejszania powierzchni (ASR, Attack Surface Reduction) Blokowanie procesów pochodzących z poleceń [PSExec i WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands), możesz tymczasowo wyłączyć regułę lub skonfigurować regułę wykluczania od reguły [asR](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules), aby umożliwić analizatorowi uruchomienie testów łączności z chmurą zgodnie z oczekiwaniami.
