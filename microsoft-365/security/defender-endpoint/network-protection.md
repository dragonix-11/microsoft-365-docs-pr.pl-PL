---
title: Używanie ochrony sieci w celu zapobiegania połączeniom z nieprawidłowymi lokacjami
description: Ochrona sieci przez uniemożliwienie użytkownikom uzyskiwania dostępu do znanych złośliwych i podejrzanych adresów sieciowych
keywords: Ochrona sieci, luki w zabezpieczeniach, złośliwa witryna internetowa, adres IP, domena, domeny
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: f58c7afe9c6f532f7f6420d58bcd681778483680
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789343"
---
# <a name="protect-your-network"></a>Chroń sieć

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Omówienie ochrony sieci

Ochrona sieci pomaga chronić urządzenia przed zdarzeniami internetowymi. Ochrona sieci to możliwość zmniejszania obszaru podatnego na ataki. Pomaga to uniemożliwić pracownikom dostęp do niebezpiecznych domen za pośrednictwem aplikacji. Domeny hostujące wyłudzanie informacji, luki w zabezpieczeniach i inne złośliwe treści w Internecie są uważane za niebezpieczne. Ochrona sieci rozszerza zakres [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview), aby zablokować cały wychodzący ruch HTTP(ów), który próbuje nawiązać połączenie ze źródłami o niskiej reputacji (na podstawie domeny lub nazwy hosta).

Ochrona sieci rozszerza ochronę w [sieci Web](web-protection-overview.md) na poziom systemu operacyjnego. Zapewnia ona funkcje ochrony sieci Web w przeglądarce Edge dla innych obsługiwanych przeglądarek i aplikacji innych niż przeglądarki. Ponadto ochrona sieci zapewnia widoczność i blokowanie wskaźników naruszenia zabezpieczeń (IOCs) w przypadku użycia z [wykrywaniem i reagowaniem na punkty końcowe](overview-endpoint-detection-response.md). Na przykład ochrona sieci działa z [niestandardowymi wskaźnikami](manage-indicators.md) , których można użyć do blokowania określonych domen lub nazw hostów.

> [!TIP]
> Zobacz witrynę Ochrona punktu końcowego w usłudze Microsoft Defender testground w [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground), aby zobaczyć, jak działa ochrona sieci.

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="requirements-for-network-protection"></a>Wymagania dotyczące ochrony sieci

Ochrona sieci wymaga Windows 10 Pro lub Enterprise i Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym.

<br>

****

|Wersje systemu Windows|Program antywirusowy Microsoft Defender|
|---|---|
|Windows 10 wersji 1709 lub nowszej <p> Windows 11 <p> Windows Server 1803 lub nowszy|[Program antywirusowy Microsoft Defender należy włączyć ochronę w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md) i [ochronę dostarczaną przez chmurę](enable-cloud-protection-microsoft-defender-antivirus.md)|
|

Po włączeniu usług może być konieczne skonfigurowanie sieci lub zapory w celu zezwolenia na połączenia między usługami i urządzeniami (nazywane również punktami końcowymi).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>Konfigurowanie ochrony sieci

Aby uzyskać więcej informacji na temat włączania ochrony sieci, zobacz **[Włączanie ochrony sieci](enable-network-protection.md)**. Użyj zasady grupy, programu PowerShell lub dostawców CSP mdm, aby włączyć ochronę sieci w sieci i zarządzać nią.

## <a name="viewing-network-protection-events"></a>Wyświetlanie zdarzeń ochrony sieci

Ochrona sieci działa najlepiej z [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md), co zapewnia szczegółowe raportowanie zdarzeń i bloków ochrony przed lukami w zabezpieczeniach w ramach [scenariuszy badania alertów](investigate-alerts.md).

Gdy ochrona sieci blokuje połączenie, z Centrum akcji jest wyświetlane powiadomienie. Twój zespół ds. operacji zabezpieczeń może [dostosować powiadomienie](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) przy użyciu szczegółów i informacji kontaktowych organizacji. Ponadto można włączyć i dostosować poszczególne reguły zmniejszania obszaru podatnego na ataki, aby dostosować je do określonych technik monitorowania.

Możesz również użyć [trybu inspekcji](audit-windows-defender.md) , aby ocenić, w jaki sposób ochrona sieci wpłynie na organizację, jeśli zostałaby włączona.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Przeglądanie zdarzeń ochrony sieci w portalu Microsoft 365 Defender

Ochrona punktu końcowego w usłudze Microsoft Defender udostępnia szczegółowe raporty dotyczące zdarzeń i bloków w ramach [scenariuszy badania alertów](investigate-alerts.md). Te szczegóły można wyświetlić w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w [kolejce alertów](review-alerts.md) lub przy użyciu [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md). Jeśli używasz [trybu inspekcji](audit-windows-defender.md), możesz użyć zaawansowanego wyszukiwania zagrożeń, aby zobaczyć, jak ustawienia ochrony sieci wpłyną na środowisko, jeśli zostaną włączone.

Oto przykładowe zapytanie dotyczące zaawansowanego wyszukiwania zagrożeń:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Przejrzyj zdarzenia ochrony sieci w Windows Podgląd zdarzeń

Możesz przejrzeć dziennik zdarzeń Windows, aby wyświetlić zdarzenia, które są tworzone, gdy ochrona sieci blokuje (lub przeprowadza inspekcje) dostępu do złośliwego adresu IP lub domeny:

1. [Skopiuj plik XML bezpośrednio](event-views.md).

2. Wybierz przycisk **OK**.

Ta procedura tworzy widok niestandardowy, który filtruje tylko następujące zdarzenia związane z ochroną sieci:

<br>

****

|Identyfikator zdarzenia|Opis|
|---|---|
|5007|Zdarzenie po zmianie ustawień|
|1125|Zdarzenie, gdy ochrona sieci jest uruchamiana w trybie inspekcji|
|1126|Zdarzenie, gdy ochrona sieci jest uruchamiana w trybie bloku|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Ochrona sieci i trójstopnie uzgadnianie protokołu TCP

W przypadku ochrony sieci określenie, czy zezwolić na dostęp do lokacji lub zablokować go, jest wykonywane po zakończeniu [uzgadniania trójstopnienego za pośrednictwem protokołu TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). W związku z tym, gdy lokacja jest zablokowana przez ochronę sieci, w portalu Microsoft 365 Defender może zostać wyświetlony typ `ConnectionSuccess` `NetworkConnectionEvents` akcji poniżej, mimo że witryna została faktycznie zablokowana. `NetworkConnectionEvents` są zgłaszane z warstwy TCP, a nie z ochrony sieci. Po zakończeniu uzgadniania trójstopnienia dostęp do witryny jest dozwolony lub blokowany przez ochronę sieci.

Oto przykład tego, jak to działa:

1. Załóżmy, że użytkownik próbuje uzyskać dostęp do witryny internetowej na swoim urządzeniu. Lokacja jest hostowana w niebezpiecznej domenie i powinna zostać zablokowana przez ochronę sieci.  

2. Rozpoczyna się uzgadnianie trójstopnie za pośrednictwem protokołu TCP/IP. Przed zakończeniem `NetworkConnectionEvents` jest rejestrowana akcja, a jej `ActionType` nazwa jest wyświetlana jako `ConnectionSuccess`. Jednak po zakończeniu trójstopnienego procesu uzgadniania ochrona sieci blokuje dostęp do lokacji. Wszystko to dzieje się bardzo szybko. Podobny proces ma miejsce w [przypadku Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)— wtedy trójstopnie uzgadnianie kończy się, gdy jest wykonywane ustalanie, a dostęp do witryny jest zablokowany lub dozwolony.

3. W portalu Microsoft 365 Defender alert jest wyświetlany w [kolejce alertów](alerts-queue.md). Szczegóły tego alertu obejmują zarówno `NetworkConnectionEvents` i `AlertEvents`. Widać, że witryna została zablokowana, mimo że masz `NetworkConnectionEvents` również element o typie ActionType .`ConnectionSuccess`

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Zagadnienia dotyczące Windows pulpitu wirtualnego uruchomionego Windows 10 Enterprise wielu sesjach

Ze względu na charakter wielu użytkowników Windows 10 Enterprise należy pamiętać o następujących kwestiach:

1. Ochrona sieci jest funkcją dla całego urządzenia i nie może być przeznaczona dla określonych sesji użytkowników.

2. Zasady filtrowania zawartości sieci Web są również na całym urządzeniu.

3. Jeśli musisz rozróżnić grupy użytkowników, rozważ utworzenie oddzielnych Windows pul hostów i przypisań hostów usługi Virtual Desktop.

4. Przetestuj ochronę sieci w trybie inspekcji, aby ocenić jej zachowanie przed wdrożeniem.

5. Rozważ zmiany rozmiaru wdrożenia, jeśli masz dużą liczbę użytkowników lub dużą liczbę sesji z wieloma użytkownikami.

### <a name="alternative-option-for-network-protection"></a>Alternatywna opcja ochrony sieci

W przypadku Windows 10 Enterprise z wieloma sesjami 1909 i nowszymi, używanymi w Windows Virtual Desktop na platformie Azure, ochronę sieci dla Microsoft Edge można włączyć przy użyciu następującej metody:

1. Użyj opcji [Włącz ochronę sieci](enable-network-protection.md) i postępuj zgodnie z instrukcjami, aby zastosować zasady.

2. Wykonaj następujące polecenia programu PowerShell:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Rozwiązywanie problemów z ochroną sieci

Ze względu na środowisko, w którym działa ochrona sieci, firma Microsoft może nie być w stanie wykryć ustawień serwera proxy systemu operacyjnego. W niektórych przypadkach klienci ochrony sieci nie mogą nawiązać połączenia z usługą w chmurze. Aby rozwiązać problem z łącznością, klienci z licencjami E5 powinni skonfigurować jeden z następujących kluczy rejestru:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Zobacz też

- [Ocena | ochrony sieci](evaluate-network-protection.md) Podejmij się szybkiego scenariusza, który pokazuje, jak działa funkcja i jakie zdarzenia są zwykle tworzone.
- [Włączanie | ochrony sieci](enable-network-protection.md) Użyj zasady grupy, programu PowerShell lub dostawców CSP mdm, aby włączyć ochronę sieci w sieci i zarządzać nią.
- [Konfigurowanie możliwości zmniejszania obszaru ataków w Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
