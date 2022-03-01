---
title: 'Odnajdowanie urządzeń : często zadawane pytania'
description: Znajdowanie odpowiedzi na często zadawane pytania (często zadawane pytania) dotyczące odnajdowania urządzeń
keywords: odnajdowanie urządzeń, odnajdowanie, pasywne, aktywne, sieci, widoczność, serwer, stacja robocza, urządzenia w trybie onboard, urządzenia nieza zarządzania
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
ms.openlocfilehash: e364a2cffcd1c18c3d220e0747010a855fafed2a
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013817"
---
# <a name="device-discovery-frequently-asked-questions"></a>Odnajdowanie urządzeń : często zadawane pytania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- - [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Znajdź odpowiedzi na często zadawane pytania (często zadawane pytania) dotyczące odnajdowania urządzeń.

## <a name="what-is-basic-discovery-mode"></a>Co to jest podstawowy tryb odnajdowania?

Ten tryb umożliwia zbieranie danych sieciowych i wykrywanie sąsiadujących urządzeń we wszystkich urządzeniach w onboardyce programu Microsoft Defender dla punktu końcowego. W onboarded endpoints passively collect events in the network and extract device information from them. Ruch sieciowy nie zostanie zainicjowany. W onboarded endpoints will simply extract data from every network traffic that is seen by an onboarded device. Te dane służą do rozsyłania listy urządzeń niezawiązyanych w Twojej sieci.

## <a name="can-i-disable-basic-discovery"></a>Czy mogę wyłączyć odnajdowanie podstawowe?

Możesz wyłączyć odnajdowanie urządzeń za pośrednictwem strony [Funkcje](advanced-features.md) zaawansowane. Jednak utracisz widoczność na niezamenuanych urządzeniach w Twojej sieci. Pamiętaj, SenseNDR.exe nadal będzie działać na urządzeniach włączonych, niezależnie od tego, czy odnajdowanie jest wyłączone. 

## <a name="what-is-standard-discovery-mode"></a>Co to jest standardowy tryb odnajdowania?

W tym trybie punkty końcowe, które zostały podłączone do programu Microsoft Defender for Endpoint, mogą aktywnie oznaczać obserwowane urządzenia w sieci w celu wzbogacenia zbieranych danych (z dużą ilością ruchu sieciowego). Tylko urządzenia obserwowane przez podstawowy tryb odnajdowania będą aktywnie aktywne w trybie standardowym. Ten tryb jest zdecydowanie zalecany w celu tworzenia niezawodnego i spójnego spisu urządzeń. Jeśli wyłączysz ten tryb i wybierzesz pozycję Podstawowy tryb odnajdowania, prawdopodobnie uzyskasz tylko ograniczoną widoczność nieza zarządzania punktami końcowymi w Twojej sieci.

 Tryb standardowy korzysta również z typowych protokołów odnajdowania, które korzystają z zapytań wielowymiarowych w sieci, aby znaleźć jeszcze więcej urządzeń, oprócz tych, które zostały zarezerwowane przy użyciu metody pasywnej.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Czy mogę kontrolować, które urządzenia wykonują odnajdowanie standardowe?

Możesz dostosować listę urządzeń używanych do odnajdowania standardowego. Możesz włączyć odnajdowanie standardowe na wszystkich urządzeniach wewnych, które również obsługują tę funkcję (obecnie jest Windows 10 lub nowszym i tylko na urządzeniach z programem Windows Server 2019 lub nowszym) lub wybrać podzbiór lub podzbiór urządzeń, określając ich tagi urządzeń. W takim przypadku wszystkie inne urządzenia będą skonfigurowane do uruchamiania tylko odnajdowania podstawowego. Konfiguracja jest dostępna na stronie ustawień odnajdowania urządzeń.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Czy mogę wykluczyć nieza zarządzanie urządzeniami z listy zasobów w spisie urządzeń?

Tak, możesz zastosować filtry, aby wykluczyć nieza zarządzanie urządzeniami z listy zasobów w spisie urządzeń. Możesz również użyć kolumny stanu dołączania w zapytaniach interfejsu API, aby odfiltrować urządzenia nieza zarządzanie.

## <a name="which-onboarded-devices-can-perform-discovery"></a>Na jakich urządzeniach podłączonych można odnajdowania?

Odnajdowanie można przeprowadzać na urządzeniach Windows 10 działających w wersji 1809 lub nowszej, Windows 11, Windows Server 2019 lub Windows Server 2022.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Co się stanie, jeśli urządzenia połączone z moją siecią domową lub publicznym punktem dostępu będą połączone?

Aparat odnajdowania rozróżnia zdarzenia sieciowe odbierane w sieci firmowej, a nie poza siecią firmową. Skorelowanie identyfikatorów sieci dla wszystkich klientów dzierżawy odróżnia wydarzenia od tych, które otrzymano z sieci prywatnych i firmowych. Jeśli na przykład większość urządzeń w organizacji zgłasza, że są połączone z tą samą nazwą sieciową, z tą samą domyślną bramą i adresem serwera FTP, można założyć, że ta sieć prawdopodobnie jest siecią firmową. Urządzenia z siecią prywatną nie będą wymienione w spisie i nie będą aktywnie badane.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Jakie protokoły przechwytuje się i analizuje?

Domyślnie wszystkie urządzenia włączone uruchomione w Windows 10 wersji 1809 lub nowszej, Program Windows 11, Windows Server 2019 lub Windows Server 2022 przechwytuje i analizuje następujące protokoły: ARP, CDP, DHCPv6, IP (nagłówki), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (nagłówki SYN), UDP (nagłówki), WSD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Jakich protokołów używasz do aktywnego uwierzytelniania w odnajdowania standardowego?
Jeśli urządzenie jest skonfigurowane do uruchamiania odnajdowania standardowego, usługi dostępne są w przypadku uwierzytelniania przy użyciu następujących protokołów: ARP, FTP, HTTP, HTTPS, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL, RPC, mDNS,FP, AFP, CrestonCIP, IphoneSync, WinRM, VNC, SLP, LDAP


## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Jak mogę wykluczyć cele z standardowych odnajdowania?

Jeśli w Twojej sieci są urządzenia, które nie powinny być aktywnie skanowane, możesz również zdefiniować listę wykluczeń, aby uniemożliwić ich skanowanie. Konfiguracja jest dostępna na stronie ustawień odnajdowania urządzeń.

> [!NOTE]
> Urządzenia mogą nadal odpowiadać na próby odnajdowania wielu danych w sieci. Te urządzenia zostaną wykryte, ale nie będą aktywnie wykryte. 

## <a name="can-i-exclude-devices-from-being-discovered"></a>Czy mogę wykluczyć urządzenia z wykrytych urządzeń?

Odkrywanie urządzeń w sieci przy użyciu metod pasywnych oznacza, że wszystkie urządzenia komunikują się z Twoimi urządzeniami w sieci firmowej, mogą zostać odkryte i wymienione w spisie. Urządzenia można wykluczać tylko z aktywnego  probowania.

## <a name="how-frequent-is-the-active-probing"></a>Jak częste jest aktywne prawdopodobieństwo?

Urządzenia będą aktywnie wstrzemiędne w przypadku obserwowania zmian w cechach urządzeń w celu upewninia się, że istniejące informacje są aktualne (zwykle urządzenia mają nie więcej niż jeden raz w okresie trzech tygodni)

## <a name="my-security-tool-raised-alert-on-unicastscannerps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Co mam zrobić, gdy w narzędziu zabezpieczeń UnicastScanner.ps1 powiadomienia dotyczące skanowania portów lub skanowania portów zainicjowane przez to narzędzie?

Aktywne skrypty  probowania są podpisane przez firmę Microsoft i bezpieczne. Do listy wykluczeń możesz dodać następującą ścieżkę: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps1`

## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Jaka jest wielkość ruchu generowanego przez aktywną usługę odnajdowania standardowego?

Aktywne  probowanie może wygenerować do 50 KB ruchu między urządzeniem wsadowym a urządzeniem, przy każdej próbie  probowania

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Dlaczego istnieje rozbieżność między urządzeniami "mogą być naniesiene" w spisie urządzeń a liczbą "urządzeń donia" na kafelku pulpitu nawigacyjnego?

Można zauważyć różnice między liczbą urządzeń wymienionych w obszarze "można dodać" w spisie urządzeń, zaleceniem zabezpieczeń "board to Microsoft Defender for Endpoint" i widżetem pulpitu nawigacyjnego "urządzenia do do urządzenia".

 Zalecenia dotyczące zabezpieczeń i widżet pulpitu nawigacyjnego są dla urządzeń, które są stabilne w sieci; z wyjątkiem urządzeń zewnętrznych, urządzeń gościnnych i innych. Chodzi o to, aby polecić urządzenia trwałe, które również wskazują ogólną ocenę bezpieczeństwa organizacji.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Czy można wychowywano urządzenia niezamanektowane?

Tak. Możesz ręcznie włączyć urządzenia niezakierowane. Nieza zarządzania punktami końcowymi w Twojej sieci są związane luki w zabezpieczeniach i zagrożenia związane z siecią. Możliwość dochowania ich do usługi może zwiększyć poziom widoczności zabezpieczeń na tych usługach.

## <a name="ive-noticed-that-unmanaged-device-health-state-is-always-active-why-is-that"></a>Zda mi się zauważyć, że stan kondycji niezakierowane urządzenia jest zawsze "Aktywny", dlaczego tak jest?

Tymczasowo stan kondycji nieza zarządzania urządzeniami będzie miał wartość "Aktywne" w standardowym okresie przechowywania spisu urządzeń, niezależnie od ich rzeczywistego stanu.

## <a name="does-standard-discovery-look-like-malicious-network-activity"></a>Czy standardowe odnajdowanie wygląda jak złośliwa aktywność w sieci?

Rozważając odnajdowanie standardowe, możesz zastanawiać się nad konsekwencjami  probowania, a w szczególności tego, czy narzędzia zabezpieczające mogą podejrzewać takie działania, jak złośliwe. W poniższej podsekcji wyjaśniono, dlaczego niemal we wszystkich przypadkach organizacje nie powinny mieć obaw o włączenie odnajdowania standardowego.  

### <a name="probing-is-distributed-across-all-windows-devices-on-the-network"></a>Probing is distributed across all Windows devices on the network

W odróżnieniu od złośliwych działań, które zwykle skanują całą sieć z niewielkiej liczby naruszonych urządzeń, odnajdowanie standardu programu Microsoft Defender dla punktu końcowego jest inicjowane ze wszystkich urządzeń Windows onboarding, co czyni działanie 99-9999- i nieujemną. Probowanie jest centralnie zarządzane z chmury, aby zrównoważyć próby  probowania między wszystkimi obsługiwanymi urządzeniami w sieci.  

### <a name="active-probing-generates-negligible-amount-of-extra-traffic"></a>Aktywne prawdopodobieństwo wygenerowania dużej ilości dodatkowego ruchu

Urządzenia niezalecane zwykle będą miały nie więcej niż raz w ciągu trzech tygodni i generują mniej niż 50 KB ruchu. Złośliwa aktywność obejmuje zwykle wiele powtarzających się prób  probowania, a w niektórych przypadkach także dane, które generują znaczną ilość ruchu sieciowego, który można zidentyfikować jako anomaly za pomocą narzędzi do monitorowania sieci.

### <a name="your-windows-device-already-runs-active-discovery"></a>Twoje Windows już działa aktywne odnajdowanie

Aktywne funkcje odnajdowania są zawsze osadzone w systemie operacyjnym Windows, co ułatwia znajdowanie pobliskich urządzeń, punktów końcowych i drukarek w celu ułatwienia "podłączania i odtwarzania" oraz udostępniania plików między punktami końcowymi w sieci. Podobne funkcje są zaimplementowane w przypadku urządzeń przenośnych, sprzętu sieciowego i aplikacji do spisu.  

Standardowe odnajdowanie używa tych samych metod odnajdowania w celu identyfikowania urządzeń i zapewniania ujednoliconej widoczności dla wszystkich urządzeń w Twojej sieci w spisie Microsoft 365 Defender urządzenia. Na przykład — funkcja odnajdowania standardowego identyfikuje pobliskie punkty końcowe w sieci tak samo Windows listach dostępnych drukarek w sieci. 

Narzędzia do monitorowania i zabezpieczeń sieci są różne na takie działania wykonywane przez urządzenia w sieci. 

### <a name="only-unmanaged-devices-are-being-probed"></a>Jest wyeksprawowane tylko urządzenia niezamanektowane

Funkcje odnajdowania urządzeń zostały stworzone, aby wykrywać i identyfikować tylko urządzenia nieza zarządzania w Twojej sieci. Oznacza to, że poprzednio wykryte urządzenia, które są już podłączone do programu Microsoft Defender for Endpoint, nie będą wsadowe.

### <a name="you-can-exclude-network-lures-from-active-probing"></a>Możesz wykluczyć luresy sieci z aktywnego  probowania

Odnajdowanie standardowe obsługuje wykluczenie urządzeń lub zakresów (podsieci) z aktywnego  probowania. Jeśli wdrożono luresy sieci, możesz użyć ustawień Odnajdowanie urządzeń w celu zdefiniowania wykluczeń na podstawie adresów IP lub podsieci (zakres adresów IP). Zdefiniowanie tych wykluczeń spowoduje, że te urządzenia nie będą aktywnie wykluczone i nie będą powiadamiane o nich alerty. Te urządzenia zostaną wykryte wyłącznie przy użyciu metod pasywnych (podobnych do podstawowego trybu odnajdowania).
