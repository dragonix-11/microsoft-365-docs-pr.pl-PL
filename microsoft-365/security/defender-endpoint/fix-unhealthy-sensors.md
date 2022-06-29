---
title: Naprawianie czujników w złej kondycji w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Napraw czujniki urządzeń, które są raportowane jako nieprawidłowo skonfigurowane lub nieaktywne, tak aby usługa odbierała dane z urządzenia.
keywords: nieprawidłowa konfiguracja, nieaktywność, napraw czujnik, kondycja czujnika, brak danych czujnika, dane czujnika, komunikacja z zaburzeniami
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
ms.openlocfilehash: cc88fa877c0c284555f1702a5fa3190a06e7e47e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490880"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>Naprawianie czujników w złej kondycji w Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

Urządzenia można sklasyfikować jako nieprawidłowo skonfigurowane lub nieaktywne, które są oflagowane z różnych przyczyn. Ta sekcja zawiera kilka wyjaśnień, co mogło spowodować, że urządzenie zostało sklasyfikowane jako nieaktywne lub nieprawidłowo skonfigurowane.

## <a name="inactive-devices"></a>Nieaktywne urządzenia

Nieaktywne urządzenie nie musi być oflagowane z powodu problemu. Następujące akcje wykonywane na urządzeniu mogą spowodować sklasyfikowanie urządzenia jako nieaktywnego:

- Urządzenie nie jest używane
- Urządzenie zostało ponownie zainstalowane lub zmieniono jego nazwę
- Urządzenie zostało odłączone
- Urządzenie nie wysyła sygnałów


### <a name="device-isnt-in-use"></a>Urządzenie nie jest używane

Każde urządzenie, które nie jest używane przez więcej niż siedem dni, zachowa stan "Nieaktywne" w portalu.

### <a name="device-was-reinstalled-or-renamed"></a>Urządzenie zostało ponownie zainstalowane lub zmieniono jego nazwę
Nowa jednostka urządzenia jest generowana w Microsoft 365 Defender dla ponownie zainstalowanych lub zmienionych nazw urządzeń. Poprzednia jednostka urządzenia pozostaje ze stanem "Nieaktywne" w portalu. Jeśli ponownie zainstalowano urządzenie i wdrożono pakiet usługi Defender for Endpoint, wyszukaj nową nazwę urządzenia, aby sprawdzić, czy urządzenie jest raportowane normalnie.

### <a name="device-was-offboarded"></a>Urządzenie zostało odłączone
Jeśli urządzenie zostało odłączone, nadal będzie wyświetlane na liście urządzeń. Po siedmiu dniach stan kondycji urządzenia powinien ulec zmianie na nieaktywny.

### <a name="device-isnt-sending-signals"></a>Urządzenie nie wysyła sygnałów
Jeśli urządzenie nie wysyła żadnych sygnałów do żadnych kanałów Ochrona punktu końcowego w usłudze Microsoft Defender przez więcej niż siedem dni z jakiegokolwiek powodu, urządzenie może zostać uznane za nieaktywne; obejmuje to warunki objęte błędną klasyfikacją urządzeń.

Czy oczekujesz, że urządzenie będzie w stanie "Aktywne"? [Otwórz bilet pomocy technicznej](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>Nieprawidłowo skonfigurowane urządzenia
Błędnie skonfigurowane urządzenia można dalej klasyfikować do:
- Komunikacja z upośledzoną łącznością
- Brak danych czujnika

### <a name="impaired-communications"></a>Komunikacja z upośledzoną łącznością
Ten stan wskazuje, że komunikacja między urządzeniem a usługą jest ograniczona.

Następujące sugerowane akcje mogą pomóc rozwiązać problemy związane z błędnie skonfigurowanym urządzeniem z ograniczoną komunikacją:

- [Upewnij się, że urządzenie ma połączenie z Internetem](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Czujnik Ochrona punktu końcowego w usłudze Microsoft Defender wymaga protokołu HTTP (WinHTTP) systemu Microsoft Windows do raportowania danych czujnika i komunikowania się z usługą Ochrona punktu końcowego w usłudze Microsoft Defender.

- [Weryfikowanie łączności klienta z adresami URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Sprawdź, czy konfiguracja serwera proxy została ukończona pomyślnie, czy usługa WinHTTP może odnajdywać i komunikować się za pośrednictwem serwera proxy w danym środowisku oraz czy serwer proxy zezwala na ruch do adresów URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender.

Jeśli akcje naprawcze zostały wykonywane, a stan urządzenia jest nadal nieprawidłowo skonfigurowany, [otwórz bilet pomocy technicznej](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>Brak danych czujnika
Nieprawidłowo skonfigurowane urządzenie o stanie "Brak danych czujnika" ma komunikację z usługą, ale może zgłaszać tylko częściowe dane czujnika.

Wykonaj następujące czynności, aby rozwiązać znane problemy związane z błędnie skonfigurowanym urządzeniem o stanie "Brak danych czujnika":

- [Upewnij się, że urządzenie ma połączenie z Internetem](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Czujnik Ochrona punktu końcowego w usłudze Microsoft Defender wymaga protokołu HTTP (WinHTTP) systemu Microsoft Windows do raportowania danych czujnika i komunikowania się z usługą Ochrona punktu końcowego w usłudze Microsoft Defender.

- [Weryfikowanie łączności klienta z adresami URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Sprawdź, czy konfiguracja serwera proxy została ukończona pomyślnie, czy usługa WinHTTP może odnajdywać i komunikować się za pośrednictwem serwera proxy w danym środowisku oraz czy serwer proxy zezwala na ruch do adresów URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender.

- [Upewnij się, że usługa danych diagnostycznych jest włączona](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
Jeśli urządzenia nie są prawidłowo raportowania, należy sprawdzić, czy usługa danych diagnostycznych systemu Windows jest ustawiona na automatyczne uruchamianie. Sprawdź również, czy usługa danych diagnostycznych systemu Windows jest uruchomiona w punkcie końcowym.

- [Upewnij się, że program antywirusowy Microsoft Defender nie jest wyłączony przez zasady](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
Jeśli na urządzeniach działa klient ochrony przed złośliwym kodem innej firmy, agent usługi Defender for Endpoint wymaga włączenia sterownika ochrony przed złośliwym oprogramowaniem antywirusowym Microsoft Defender (ELAM).

Jeśli akcje naprawcze zostały wykonywane, a stan urządzenia jest nadal nieprawidłowo skonfigurowany, [otwórz bilet pomocy technicznej](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>Zobacz też
- [Sprawdzanie stanu kondycji czujnika w Ochrona punktu końcowego w usłudze Microsoft Defender](check-sensor-status.md)
- [Omówienie funkcji analizatora klienta](overview-client-analyzer.md)
- [Pobierz i uruchom analizator klienta](download-client-analyzer.md)
- [Uruchom analizator klienta w systemie Windows](run-analyzer-windows.md)
- [Uruchom analizator klienta w systemie macOS lub Linux](run-analyzer-macos-linux.md)
- [ Zbieranie danych na potrzeby zaawansowanego rozwiązywania problemów w systemie Windows](data-collection-analyzer.md)

