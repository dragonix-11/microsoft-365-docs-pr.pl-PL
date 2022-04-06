---
title: Często zadawane pytania dotyczące odnajdywania urządzeń
description: Znajdowanie odpowiedzi na często zadawane pytania dotyczące odnajdywania urządzeń
keywords: odnajdywanie, odnajdywanie, pasywne, proaktywne, sieć, widoczność, serwer, stacja robocza, dołączanie, urządzenia niezarządzane
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
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 54a1b816f3d1322cab5558e5bd09d5d9b4285ae8
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665013"
---
# <a name="device-discovery-frequently-asked-questions"></a>Często zadawane pytania dotyczące odnajdywania urządzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- - [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Znajdź odpowiedzi na często zadawane pytania dotyczące odnajdywania urządzeń.

## <a name="what-is-basic-discovery-mode"></a>Co to jest tryb odnajdywania podstawowego?

Ten tryb umożliwia każdemu Ochrona punktu końcowego w usłudze Microsoft Defender dołączonemu urządzeniu zbieranie danych sieciowych i odnajdywanie sąsiednich urządzeń. Dołączone punkty końcowe pasywnie zbierają zdarzenia w sieci i wyodrębniają z nich informacje o urządzeniu. Nie zostanie zainicjowany żaden ruch sieciowy. Dołączone punkty końcowe po prostu wyodrębnią dane z każdego ruchu sieciowego, który jest widoczny dla dołączonego urządzenia. Te dane służą do wyświetlania listy niezarządzanych urządzeń w sieci.

## <a name="can-i-disable-basic-discovery"></a>Czy mogę wyłączyć odnajdywanie podstawowe?

Możesz wyłączyć odnajdywanie urządzeń za pośrednictwem strony [Funkcje zaawansowane](advanced-features.md) . Utracisz jednak widoczność na urządzeniach niezarządzanych w sieci. Należy pamiętać, że SenseNDR.exe nadal będą działać na dołączonych urządzeniach, niezależnie od tego, czy odnajdywanie jest wyłączone. 

## <a name="what-is-standard-discovery-mode"></a>Co to jest tryb odnajdywania w warstwie Standardowa?

W tym trybie punkty końcowe dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender mogą aktywnie sondować obserwowane urządzenia w sieci w celu wzbogacenia zebranych danych (z nieznaczną ilością ruchu sieciowego). Tylko urządzenia, które zostały zaobserwowane w trybie odnajdywania podstawowego, będą aktywnie sondowane w trybie standardowym. Ten tryb jest zdecydowanie zalecany do tworzenia niezawodnego i spójnego spisu urządzeń. Jeśli wybierzesz opcję wyłączenia tego trybu i wybierzesz tryb odnajdywania podstawowego, prawdopodobnie uzyskasz tylko ograniczoną widoczność niezarządzanych punktów końcowych w sieci.

 Tryb standardowy wykorzystuje również typowe protokoły odnajdywania korzystające z zapytań multiemisji w sieci w celu znalezienia jeszcze większej liczby urządzeń, oprócz tych, które zaobserwowano przy użyciu metody pasywnej.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Czy mogę kontrolować, które urządzenia wykonują odnajdywanie w warstwie Standardowa?

Listę urządzeń używanych do odnajdywania w warstwie Standardowa można dostosować. Możesz włączyć odnajdywanie w warstwie Standardowa na wszystkich dołączonych urządzeniach, które również obsługują tę funkcję (obecnie Windows 10 lub nowszym i tylko na urządzeniach z serwerem Windows Server 2019 lub nowszym), albo wybrać podzestaw lub podzestaw urządzeń, określając tagi urządzeń. W takim przypadku wszystkie inne urządzenia zostaną skonfigurowane do uruchamiania tylko podstawowego odnajdywania. Konfiguracja jest dostępna na stronie ustawień odnajdywania urządzeń.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Czy można wykluczyć urządzenia niezarządzane z listy spisu urządzeń?

Tak, można zastosować filtry, aby wykluczyć urządzenia niezarządzane z listy spisu urządzeń. Możesz również użyć kolumny stanu dołączania w zapytaniach interfejsu API, aby odfiltrować urządzenia niezarządzane.

## <a name="which-onboarded-devices-can-perform-discovery"></a>Które urządzenia dołączone mogą przeprowadzać odnajdywanie?

Odnajdywanie można wykonywać na urządzeniach z systemem Windows 10 wersji 1809 lub nowszej, Windows 11, Windows Server 2019 lub Windows Server 2022.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Co się stanie, jeśli moje dołączone urządzenia są połączone z siecią domową lub publicznym punktem dostępu?

Aparat odnajdywania rozróżnia zdarzenia sieciowe odbierane w sieci firmowej i poza siecią firmową. Dzięki korelacji identyfikatorów sieci we wszystkich klientach dzierżawy zdarzenia są rozróżniane między tymi, które zostały odebrane z sieci prywatnych i firmowych. Jeśli na przykład większość urządzeń w organizacji zgłasza, że są podłączone do tej samej nazwy sieci, z tą samą bramą domyślną i adresem serwera DHCP, można założyć, że ta sieć jest prawdopodobnie siecią firmową. Urządzenia sieci prywatnej nie zostaną wymienione w spisie i nie będą aktywnie sondowane.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Jakie protokoły są przechwytywane i analizowane?

Domyślnie wszystkie dołączone urządzenia działające w Windows 10 wersji 1809 lub nowszej, Windows 11, Windows Server 2019 lub Windows Server 2022 przechwytują i analizują następujące protokoły: ARP, CDP, DHCP, DHCPv6, IP (nagłówki), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (nagłówki SYN), UDP (nagłówki), WSDD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Których protokołów używasz do aktywnego sondowania w odnajdywaniem w warstwie Standardowa?
Gdy urządzenie jest skonfigurowane do uruchamiania odnajdywania standardowego, uwidocznione usługi są sondowane przy użyciu następujących protokołów: ARP, FTP, HTTP, HTTPS, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL, RPC, mDNS, DHCP, AFP, CrestonCIP, IphoneSync, WinRM, VNC, SLP, LDAP


## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Jak wykluczyć obiekty docelowe z sondowania przy użyciu odnajdywania standardowego?

Jeśli w sieci znajdują się urządzenia, które nie powinny być aktywnie sondowane, możesz również zdefiniować listę wykluczeń, aby zapobiec ich skanowaniu. Konfiguracja jest dostępna na stronie ustawień odnajdywania urządzeń.

> [!NOTE]
> Urządzenia mogą nadal odpowiadać na próby odnajdywania multiemisji w sieci. Te urządzenia zostaną odnalezione, ale nie będą aktywnie badane. 

## <a name="can-i-exclude-devices-from-being-discovered"></a>Czy można wykluczyć urządzenia z odnajdywania?

Ponieważ odnajdywanie urządzeń używa metod pasywnych do odnajdywania urządzeń w sieci, wszystkie urządzenia komunikujące się z dołączonymi urządzeniami w sieci firmowej można odnaleźć i wyświetlić w spisie. Urządzenia można wykluczyć tylko z aktywnego sondowania.

## <a name="how-frequent-is-the-active-probing"></a>Jak częste jest aktywne sondowanie?

Urządzenia będą aktywnie sondowane, gdy zostaną zaobserwowane zmiany w charakterystykach urządzeń, aby upewnić się, że istniejące informacje są aktualne (zazwyczaj urządzenia sondowane nie częściej niż raz w okresie trzech tygodni)

## <a name="my-security-tool-raised-alert-on-unicastscannerps1--psscript_guidps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Moje narzędzie zabezpieczeń zgłosiło alert dotyczący UnicastScanner.ps1 /PSScript_{GUID}.ps1 lub zainicjowanego przez niego działania skanowania portów, co mam zrobić?

Aktywne skrypty sondowania są podpisane przez firmę Microsoft i są bezpieczne. Do listy wykluczeń możesz dodać następującą ścieżkę: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps1`

## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Jaka jest ilość ruchu generowanego przez aktywną sondę odnajdywania w warstwie Standardowa?

Aktywne sondowanie może wygenerować do 50 KB ruchu między dołączonym urządzeniem a sondowanym urządzeniem, przy każdej próbie sondowania

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Dlaczego występuje rozbieżność między urządzeniami "można dołączyć" do spisu urządzeń i liczbą "urządzeń do dołączenia" na kafelku pulpitu nawigacyjnego?

W spisie urządzeń można zauważyć różnice między liczbą wymienionych urządzeń w obszarze "można dołączyć" do spisu urządzeń, zaleceniem dotyczącym zabezpieczeń "dołączanie do Ochrona punktu końcowego w usłudze Microsoft Defender" a widżetem pulpitu nawigacyjnego "urządzenia do dołączenia".

 Zalecenia dotyczące zabezpieczeń i widżet pulpitu nawigacyjnego są przeznaczone dla urządzeń, które są stabilne w sieci; z wyłączeniem urządzeń efemeryczne, urządzeń gościa i innych. Chodzi o to, aby zalecić na urządzeniach trwałych, co również oznacza ogólny wynik bezpieczeństwa organizacji.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Czy mogę dołączyć odnalezione niezarządzane urządzenia?

Tak. Urządzenia niezarządzane można dołączyć ręcznie. Niezarządzane punkty końcowe w sieci wprowadzają luki w zabezpieczeniach i zagrożenia dla sieci. Dołączenie ich do usługi może zwiększyć widoczność zabezpieczeń.

## <a name="ive-noticed-that-unmanaged-device-health-state-is-always-active-why-is-that"></a>Zauważyłem, że stan kondycji urządzenia niezarządzanego jest zawsze "Aktywny", dlaczego tak jest?

Tymczasowo stan kondycji urządzenia niezarządzanego będzie "Aktywny" w standardowym okresie przechowywania spisu urządzeń, niezależnie od ich rzeczywistego stanu.

## <a name="does-standard-discovery-look-like-malicious-network-activity"></a>Czy odnajdywanie standardowe wygląda jak złośliwa aktywność sieciowa?

Rozważając odnajdywanie w warstwie Standardowa, możesz się zastanawiać nad konsekwencjami sondowania, a w szczególności o tym, czy narzędzia zabezpieczeń mogą podejrzewać taką aktywność jako złośliwą. W poniższej podsekcji wyjaśniono, dlaczego w prawie wszystkich przypadkach organizacje nie powinny mieć żadnych obaw dotyczących włączania odnajdywania w warstwie Standardowa.  

### <a name="probing-is-distributed-across-all-windows-devices-on-the-network"></a>Sondowanie jest dystrybuowane na wszystkich urządzeniach Windows w sieci

W przeciwieństwie do złośliwych działań, które zazwyczaj skanują całą sieć z niewielkiej liczby urządzeń, których zabezpieczenia zostały naruszone, sondowanie odnajdywania standardowego Ochrona punktu końcowego w usłudze Microsoft Defender jest inicjowane ze wszystkich dołączonych urządzeń Windows, co sprawia, że działanie jest łagodne i nietypowe. Sondowanie jest centralnie zarządzane z chmury w celu zrównoważenia próby sondowania między wszystkimi obsługiwanymi urządzeniami dołączonymi w sieci.  

### <a name="active-probing-generates-negligible-amount-of-extra-traffic"></a>Aktywne sondowanie generuje znikomą ilość dodatkowego ruchu

Urządzenia niezarządzane zwykle są sondowane nie częściej niż raz w ciągu trzech tygodni i generują mniej niż 50 KB ruchu. Złośliwe działanie zwykle obejmuje duże powtarzające się próby sondowania, a w niektórych przypadkach eksfiltrację danych, która generuje znaczną ilość ruchu sieciowego, który można zidentyfikować jako anomalię za pomocą narzędzi do monitorowania sieci.

### <a name="your-windows-device-already-runs-active-discovery"></a>Urządzenie Windows już uruchamia aktywne odnajdywanie

Funkcje aktywnego odnajdywania zawsze były osadzone w systemie operacyjnym Windows, aby znaleźć pobliskie urządzenia, punkty końcowe i drukarki, aby ułatwić środowisko "plug and play" i udostępnianie plików między punktami końcowymi w sieci. Podobne funkcje są implementowane w urządzeniach przenośnych, sprzęcie sieciowym i aplikacjach spisu tylko po to, aby wymienić tylko kilka.  

Odnajdywanie standardowe używa tych samych metod odnajdywania do identyfikowania urządzeń i zapewniania ujednoliconej widoczności dla wszystkich urządzeń w sieci w spisie urządzeń Microsoft 365 Defender. Na przykład — odnajdywanie standardowe identyfikuje pobliskie punkty końcowe w sieci w taki sam sposób, Windows wyświetla listę dostępnych drukarek w sieci. 

Narzędzia do zabezpieczeń sieci i monitorowania są obojętne na takie działania wykonywane przez urządzenia w sieci. 

### <a name="only-unmanaged-devices-are-being-probed"></a>Sondowane są tylko urządzenia niezarządzane

Możliwości odnajdywania urządzeń zostały skompilowane w celu odnajdywania i identyfikowania urządzeń niezarządzanych w sieci. Oznacza to, że wcześniej odnalezione urządzenia, które są już dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender, nie będą sondowane.

### <a name="you-can-exclude-network-lures-from-active-probing"></a>Możesz wykluczyć przynęty sieciowe z aktywnego sondowania

Odnajdywanie standardowe obsługuje wykluczanie urządzeń lub zakresów (podsieci) z aktywnego sondowania. Jeśli masz wdrożone przynęty sieciowe, możesz użyć ustawień odnajdywania urządzeń, aby zdefiniować wykluczenia na podstawie adresów IP lub podsieci (zakres adresów IP). Zdefiniowanie tych wykluczeń zapewni, że te urządzenia nie będą aktywnie sondowane i nie będą otrzymywać alertów. Te urządzenia zostaną odnalezione tylko przy użyciu metod pasywnych (podobnie jak w trybie odnajdywania podstawowego).
