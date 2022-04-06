---
title: Zapobieganie połączeniam ze złymi witrynami za pomocą ochrony sieci
description: Ochrona sieci przez uniemożliwienie użytkownikom dostępu do znanych złośliwych i podejrzanych adresów sieciowych
keywords: Ochrona sieci, wykorzystywanie, złośliwa witryna internetowa, adres IP, domena, domeny
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
ms.openlocfilehash: 7b9443cac6543ac14f6d94bd2809b5263be0a860
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681837"
---
# <a name="protect-your-network"></a>Ochrona sieci

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Omówienie ochrony sieci

Ochrona sieci pomaga chronić urządzenia przed zdarzeniami internetowymi. Ochrona sieci to funkcja ograniczania powierzchni ataków. Pomaga to zapobiegać uzyskiwaniu przez pracowników dostępu do niebezpiecznych domen za pośrednictwem aplikacji. Domeny hostują wyłudzanie informacji, oszustwa i inną złośliwą zawartość w Internecie są uznawane za niebezpieczne. Ochrona sieci rozszerza zakres protokołu [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) blokowania całego ruchu wychodzącego HTTP, który próbuje nawiązać połączenie ze źródłami o niskiej reputacji (na podstawie nazwy domeny lub hosta).

Ochrona sieci rozszerza ochronę sieci [Web na](web-protection-overview.md) poziom systemu operacyjnego. Zapewnia on funkcje ochrony sieci Web w przeglądarce Microsoft Edge innym obsługiwanym przeglądarkom i aplikacjom niebędący przeglądarkami. Ponadto ochrona sieci zapewnia widoczność i blokowanie wskaźników naruszenia zabezpieczeń (IOCs) w przypadku korzystania z wykrywania punktu [końcowego i odpowiedzi](overview-endpoint-detection-response.md). Na przykład ochrona sieci działa ze [wskaźnikami](manage-indicators.md) niestandardowymi, które mogą być służące do blokowania określonych domen lub nazw hostów.

> [!TIP]
> Zobacz witrynę testową programu Microsoft Defender for Endpoint [w demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) , aby dowiedzieć się, jak działa ochrona sieci.

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="requirements-for-network-protection"></a>Wymagania dotyczące ochrony sieci

Ochrona sieci wymaga Windows 10 Pro lub Enterprise i Program antywirusowy Microsoft Defender w czasie rzeczywistym.

<br>

****

|Wersje systemu Windows|Program antywirusowy Microsoft Defender|
|---|---|
|Windows 10 1709 lub nowsza <p> Windows 11 <p> Windows Server 1803 lub nowszy|[Program antywirusowy Microsoft Defender w czasie rzeczywistym i](configure-real-time-protection-microsoft-defender-antivirus.md) [musi być włączona ochrona w](enable-cloud-protection-microsoft-defender-antivirus.md) chmurze|
|

Po włączeniu usług może być konieczne skonfigurowanie sieci lub zapory w celu umożliwienia połączeń między usługami i Twoimi urządzeniami (nazywanych również punktami końcowymi).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>Konfigurowanie ochrony sieci

Aby uzyskać więcej informacji na temat włączania ochrony sieci, zobacz **[Włączanie ochrony sieci](enable-network-protection.md)**. Za zasady grupy sieci, programu PowerShell lub usługi MDM możesz włączyć ochronę sieci i zarządzać nimi.

## <a name="viewing-network-protection-events"></a>Wyświetlanie zdarzeń ochrony sieci

Ochrona sieci działa najlepiej z [programem Microsoft Defender for Endpoint](microsoft-defender-endpoint.md), który udostępnia szczegółowe raporty dotyczące zdarzeń ochrony przed wykorzystywaniem luk i bloków w ramach [scenariuszy analizy alertów](investigate-alerts.md).

Gdy ochrona sieci blokuje połączenie, w Centrum akcji jest wyświetlane powiadomienie. Zespół operacyjny ds. zabezpieczeń [może dostosować powiadomienie](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) , dostosowując je do szczegółów i informacji kontaktowych organizacji. Ponadto można włączać i dostosowywać indywidualne reguły ograniczania powierzchni ataków, aby odpowiadały określonym technikom do monitorowania.

Za pomocą trybu [inspekcji można również](audit-windows-defender.md) ocenić wpływ ochrony sieci na organizację, jeśli ją włączono.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Przeglądanie zdarzeń ochrony sieci w portalu Microsoft 365 Defender sieci

Program Microsoft Defender for Endpoint udostępnia szczegółowe raportowanie zdarzeń i bloków w ramach scenariuszy analizy [alertów](investigate-alerts.md). Możesz wyświetlić te szczegóły w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w kolejce [alertów](review-alerts.md) lub przy użyciu [zaawansowanego wyszukiwania](advanced-hunting-overview.md). Jeśli korzystasz [z trybu inspekcji](audit-windows-defender.md), możesz użyć zaawansowanego wyszukiwania, aby zobaczyć, jak ustawienia ochrony sieci wywrze wpływ na Twoje środowisko, jeśli zostały włączone.

Oto przykładowa kwerenda dla zaawansowanego wyszukiwania:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Przeglądanie zdarzeń ochrony sieci w przeglądarce Windows zdarzeń

Możesz przejrzeć dziennik Windows zdarzeń, aby zobaczyć zdarzenia utworzone w przypadku bloków dostępu do złośliwego adresu IP lub domeny (inspekcji lub ochrony sieci):

1. [Skopiuj kod XML bezpośrednio](event-views.md).

2. Wybierz przycisk **OK**.

Ta procedura umożliwia utworzenie widoku niestandardowego, który filtruje w celu pokazania tylko następujących zdarzeń związanych z ochroną sieci:

<br>

****

|Identyfikator zdarzenia|Opis|
|---|---|
|5007|Zdarzenie w przypadku zmiany ustawień|
|1125|Zdarzenie, gdy ochrona sieci jest w trybie inspekcji|
|1126|Zdarzenie, gdy ochrona sieci jest w trybie blokowania|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Ochrona sieci i trójkierunkowy uścisk dłoni protokołu TCP

W ramach ochrony sieci określenie, czy zezwolić na dostęp do witryny, czy zablokować go, jest dokonywane po zakończeniu trójkierunkowego połączenia praktycznego za pośrednictwem [protokołu TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). Dlatego w przypadku `ConnectionSuccess` `NetworkConnectionEvents` zablokowania witryny przez ochronę sieci w portalu usługi Microsoft 365 Defender może zostać wyświetlony typ akcji, mimo że witryna została faktycznie zablokowana. `NetworkConnectionEvents` są raporty z warstwy TCP, a nie z ochrony sieci. Po zakończeniu trójkierunkowego połączenia dostęp do witryny jest dozwolony lub zablokowany przez ochronę sieci.

Oto przykład działania:

1. Załóżmy, że użytkownik próbuje uzyskać dostęp do witryny internetowej na swoim urządzeniu. Witryna jest hostowana w niebezpiecznej domenie i powinna zostać zablokowana przez ochronę sieci.  

2. Rozpocznie się trójkierunkowy handshake za pośrednictwem protokołu TCP/IP. Zanim zostanie ukończona, akcja `NetworkConnectionEvents` zostanie zarejestrowana i będzie wymieniona `ActionType` jako `ConnectionSuccess`. Jednak po zakończeniu tego trzykierunkowego procesu głośnomówiące ochrona sieci blokuje dostęp do witryny. To wszystko dzieje się bardzo szybko. Podobny proces występuje [w przypadku](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) Microsoft Defender SmartScreen; oznacza to, że dokonano wyznaczania trzech sposobów; dostęp do witryny jest zablokowany lub dozwolony.

3. W portalu Microsoft 365 Defender alert jest wymieniony w [kolejce alertów](alerts-queue.md). Szczegóły tego alertu obejmują zarówno alert, jak `NetworkConnectionEvents` i `AlertEvents`. Jak widać, witryna została zablokowana, `NetworkConnectionEvents` nawet jeśli masz element z elementem ActionType (Typ akcji) z `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Zagadnienia dotyczące Windows pulpitu wirtualnego z Windows 10 Enterprise z wieloma sesjami

Ze względu na charakter wielu użytkowników Windows 10 Enterprise należy pamiętać o następujących kwestiach:

1. Ochrona sieci to funkcja dostępna na całym urządzeniu, która nie może być kierowana do konkretnych sesji użytkowników.

2. Zasady filtrowania zawartości sieci Web również są dostępne na urządzeniach.

3. Jeśli chcesz rozróżnić grupy użytkowników, rozważ utworzenie oddzielnych pul hosta Windows i przydziałów dla hosta pulpitu wirtualnego.

4. Przetestuj ochronę sieci w trybie inspekcji, aby ocenić jej działanie przed jej rozpoczęciem.

5. Rozważ zmienianie rozmiaru wdrożenia, jeśli masz dużą liczbę użytkowników lub dużą liczbę sesji z wieloma użytkownikami.

### <a name="alternative-option-for-network-protection"></a>Opcja alternatywna ochrony sieci

W Windows 10 Enterprise wersji 1909 dla wielu sesji (i więcej) używanej w programie Windows Virtual Desktop na platformie Azure ochronę sieci dla komputerów Microsoft Edge można włączyć przy użyciu następującej metody:

1. Aby [zastosować zasady,](enable-network-protection.md) użyj polecenia Włącz ochronę sieci i postępuj zgodnie z instrukcjami.

2. Wykonaj następujące polecenie programu PowerShell: `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Rozwiązywanie problemów z ochroną sieci

Ze względu na środowisko, w którym jest uruchomiona ochrona sieci, firma Microsoft może nie być w stanie wykryć ustawień serwera proxy systemu operacyjnego. W niektórych przypadkach klienci ochrony sieci nie mogą uzyskać dostępu do usługi w chmurze. Aby rozwiązać problem z łącznością, klienci z licencjami E5 powinni skonfigurować jeden z następujących kluczy rejestru:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Zobacz też

- [Ocenianie ochrony sieci](evaluate-network-protection.md) | Podejmij krótki scenariusz, który pokazuje, jak działa ta funkcja i jakie zdarzenia zazwyczaj można by utworzyć.
- [Włączanie ochrony sieci |](enable-network-protection.md) Za zasady grupy sieci, programu PowerShell lub usługi MDM możesz włączyć ochronę sieci i zarządzać nimi.
- [Konfigurowanie funkcji zmniejszania powierzchni ataków w programie Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
