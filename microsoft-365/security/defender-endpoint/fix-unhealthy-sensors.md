---
title: Naprawianie czujników o złej kondycji w programie Microsoft Defender dla punktu końcowego
description: Napraw czujniki urządzenia, które zgłaszają się jako nieprawidłowo skonfigurowane lub nieaktywne, aby usługa odbierała dane z urządzenia.
keywords: nieprawidłowo skonfigurowane, nieaktywne, naprawianie czujnika, kondycja czujnika, bez danych czujnika, dane czujnika, zakłócona komunikacja, komunikacja
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/23/2020
ms.technology: mde
ms.openlocfilehash: e801776001b79bf1ae3e6e8a220c5e4c395896db
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033740"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>Naprawianie czujników o złej kondycji w programie Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

Urządzenia można kategoryzować jako nieprawidłowo skonfigurowane lub nieaktywne, z różnych przyczyn. W tej sekcji przedstawiono niektóre objaśnienia przyczyn, które mogły spowodować kategoryzowanie urządzenia jako nieaktywnego lub nieprawidłowo skonfigurowanego.

## <a name="inactive-devices"></a>Nieaktywne urządzenia

Nieaktywne urządzenie nie musi być oflagowane z powodu problemu. Następujące akcje wykonane na urządzeniu mogą powodować kategoryzowanie urządzenia jako nieaktywnego:

### <a name="device-is-not-in-use"></a>Urządzenie nie jest w użyciu

Każde urządzenie, które nie jest w użyciu dłużej niż siedem dni, zachowa w portalu status "Nieaktywny".

### <a name="device-was-reinstalled-or-renamed"></a>Urządzenie zostało ponownie zainstalowane lub jego nazwa została zmieniona
W aplikacji jest generowana nowa jednostka Microsoft 365 Defender dla urządzeń ponownie zainstalowanych lub o zmienionych nazwach. Poprzednia jednostka urządzenia pozostaje ze stanem "Nieaktywny" w portalu. Jeśli ponownie zainstalowano urządzenie i wdrożono pakiet Defender for Endpoint, wyszukaj nową nazwę urządzenia, aby sprawdzić, czy urządzenie raportuje normalnie.

### <a name="device-was-offboarded"></a>Urządzenie zostało wyłączone
Jeśli urządzenie zostało wyłączone, nadal będzie wyświetlane na liście urządzeń. Po upływie siedmiu dni stan kondycji urządzenia powinien zmienić się na nieaktywny.

### <a name="device-is-not-sending-signals"></a>Urządzenie nie wysyła sygnałów
Jeśli urządzenie z jakiegokolwiek powodu nie wysyła żadnych sygnałów do żadnego kanału programu Microsoft Defender for Endpoint przez ponad siedem dni, urządzenie można uznać za nieaktywne. obejmuje to warunki, które mogą podlegać nieprawidłowo skonfigurowanej klasyfikacji urządzeń.

Czy oczekujesz, że urządzenie będzie w stanie "Aktywne"? [Otwórz bilet pomocy technicznej](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>Nieprawidłowo skonfigurowane urządzenia
Nieprawidłowo skonfigurowane urządzenia można dodatkowo sklasyfikować jako:
- Komunikacja z ograniczoną komunikacją
- Brak danych czujnika

### <a name="impaired-communications"></a>Komunikacja z ograniczoną komunikacją
Ten stan oznacza, że między urządzeniem a usługą jest ograniczona komunikacja.

Następujące sugerowane działania mogą ułatwić rozwiązywanie problemów związanych z nieprawidłowo skonfigurowanym urządzeniem z ograniczoną komunikacją:

- [Upewnij się, że urządzenie ma połączenie internetowe](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Czujnik programu Microsoft Defender for Endpoint wymaga, Windows Http (WinHTTP) firmy Microsoft do zgłaszania danych czujnika i komunikowania się z usługą Microsoft Defender for Endpoint.

- [Weryfikowanie łączności klienta z adresami URL usługi Programu Microsoft Defender dla punktu końcowego](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Sprawdź pomyślnie ukończoną konfigurację serwera proxy, czy system WinHTTP może wykrywać i komunikować się za pośrednictwem serwera proxy w Twoim środowisku oraz czy serwer proxy zezwala na ruch do adresów URL usługi Programu Microsoft Defender dla punktów końcowych.

Jeśli poczynisz działania korygacyjne, a stan urządzenia nadal jest nieprawidłowo skonfigurowany, [otwórz zgłoszenie do pomocy technicznej](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>Brak danych czujnika
Nieprawidłowo skonfigurowane urządzenie ze stanem "Brak danych czujnika" ma komunikację z usługą, ale może zgłaszać tylko dane częściowego czujnika.

Wykonaj poniższe czynności, aby rozwiązać znane problemy związane z nieprawidłowo skonfigurowanym urządzeniem ze stanem "Brak danych czujnika":

- [Upewnij się, że urządzenie ma połączenie internetowe](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Czujnik programu Microsoft Defender for Endpoint wymaga, Windows Http (WinHTTP) firmy Microsoft do zgłaszania danych czujnika i komunikowania się z usługą Microsoft Defender for Endpoint.

- [Weryfikowanie łączności klienta z adresami URL usługi Programu Microsoft Defender dla punktu końcowego](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Sprawdź pomyślnie ukończoną konfigurację serwera proxy, czy system WinHTTP może wykrywać i komunikować się za pośrednictwem serwera proxy w Twoim środowisku oraz czy serwer proxy zezwala na ruch do adresów URL usługi Programu Microsoft Defender dla punktów końcowych.

- [Upewnij się, że usługa danych diagnostycznych jest włączona](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
Jeśli urządzenia nie zgłaszają się poprawnie, upewnij się, że usługa Windows jest ustawiona na automatyczne uruchamianie. Sprawdź również, czy Windows danych diagnostycznych jest uruchomiona w punkcie końcowym.

- [Zapewnianie, Program antywirusowy Microsoft Defender nie jest wyłączone przez zasady](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
Jeśli na Twoich urządzeniach jest uruchomiony klient ochrony przed złośliwym oprogramowaniem innej firmy, agent programu Defender for Endpoint wymaga, aby Program antywirusowy Microsoft Defender włączono sterownik ELAM (Early Launch Antimalware).

Jeśli poczynisz działania korygacyjne, a stan urządzenia nadal jest nieprawidłowo skonfigurowany, [otwórz zgłoszenie do pomocy technicznej](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>Zobacz też
- [Sprawdzanie stanu kondycji czujnika w programie Microsoft Defender dla punktu końcowego](check-sensor-status.md)
- [Omówienie analizatora klientów](overview-client-analyzer.md)
- [Pobieranie i uruchamianie analizatora klienta](download-client-analyzer.md)
- [Uruchamianie analizatora klienta na Windows](run-analyzer-windows.md)
- [Uruchamianie analizatora klienta w systemie macOS lub Linux](run-analyzer-macos-linux.md)
- [Zbieranie danych na potrzeby zaawansowanego rozwiązywania problemów na Windows](data-collection-analyzer.md)

