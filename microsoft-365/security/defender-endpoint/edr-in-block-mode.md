---
title: Wykrywanie punktu końcowego i odpowiedź w trybie blokowania
description: Informacje o wykrywanie i reagowanie w punktach końcowych w trybie blokowania
keywords: Microsoft Defender for Endpoint, mde, EDR in block mode, passive mode blocking
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
- admindeeplinkDEFENDER
ms.date: 03/16/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 6c3df0efe5c565497803ecdd84716ec70e590afd
ms.sourcegitcommit: b67385243fb56ad20f2a6f1c40be46f5691c1c2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63527830"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Wykrywanie punktu końcowego i odpowiedź (EDR) w trybie blokowania

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Co to EDR tryb blokowania?

[Wykrywanie punktu końcowego](overview-endpoint-detection-response.md) i odpowiedź (EDR) w trybie blokowania zapewnia dodatkową ochronę przed złośliwymi artefaktami, gdy Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym i działa w trybie pasywnym. EDR trybie blokowania działa w tle w celu korygowania złośliwych artefaktów wykrytych przez EDR. Tego rodzaju artefakty mogły zostać pominięte przez podstawowy produkt antywirusowy firmy Microsoft. W przypadku urządzeń Program antywirusowy Microsoft Defender jako podstawowych programów antywirusowych EDR tryb blokowania zapewnia dodatkową warstwę obrony, umożliwiając Program antywirusowy Microsoft Defender automatyczne działanie w przypadku po naruszeniu zabezpieczeń, zachowań i EDR wykrywania.

> [!IMPORTANT]
> EDR trybie blokowania nie zapewnia całej ochrony dostępnej po włączeniu Program antywirusowy Microsoft Defender w czasie rzeczywistym. Nie wszystkie funkcje, które zależą Program antywirusowy Microsoft Defender aktywne rozwiązanie antywirusowe, nie będą działać, w tym następujące kluczowe przykłady:
>
> - Ochrona w czasie rzeczywistym, w tym skanowanie przy dostępie, nie jest dostępna, gdy Program antywirusowy Microsoft Defender w trybie pasywnym. Aby dowiedzieć się więcej o ustawieniach zasad ochrony w czasie rzeczywistym, zobacz Włączanie i konfigurowanie **[Program antywirusowy Microsoft Defender zawsze włączoną ochronę](configure-real-time-protection-microsoft-defender-antivirus.md)**.
> - Funkcje takie **[jak ochrona sieci](network-protection.md)** i **[reguły zmniejszania powierzchni](attack-surface-reduction.md)** ataków są dostępne tylko wtedy, Program antywirusowy Microsoft Defender są uruchomione w trybie aktywnym.
>
> Te funkcje powinny być dostępne w rozwiązaniu antywirusowym innych niż firmy Microsoft.

EDR trybie blokowania jest zintegrowana z [zagrożeniami, które & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md). Zespół zabezpieczeń Twojej organizacji otrzyma zalecenie o zabezpieczeniach[](tvm-security-recommendation.md), aby włączyć EDR tryb blokowania, jeśli nie jest jeszcze włączony.

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="zalecenie, aby włączyć EDR trybie blokowania.":::

> [!TIP]
> Aby uzyskać najlepszą ochronę, upewnij się, że wdrożono program **[Microsoft Defender dla punktów bazowych punktów końcowych](configure-machines-security-baseline.md)**.

## <a name="what-happens-when-something-is-detected"></a>Co się dzieje, gdy coś zostanie wykryte?

W EDR w trybie blokowania i wykryciu złośliwego artefaktu program Microsoft Defender dla punktu końcowego blokuje i rekultywuje ten artefakt. Zespół operacyjny zabezpieczeń zobaczy w Centrum akcji stan  wykrywania Zablokowany  lub [Prevented (Zablokowane](respond-machine-alerts.md#check-activity-details-in-action-center)) jako Ukończone akcje.

Na poniższej ilustracji przedstawiono wystąpienie niechcianego oprogramowania wykrytego i zablokowanego przez inne EDR w trybie blokowania:

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="EDR w trybie blokowania coś wykryło.":::


## <a name="enable-edr-in-block-mode"></a>Włączanie EDR w trybie blokowania

> [!IMPORTANT]
> Począwszy od wersji platformy 4.18.2202.X, możesz teraz skonfigurować EDR w trybie blokowania, aby kierować określone grupy urządzeń za pomocą tych grup usługi Intune. W portalu EDR można nadal ustawiać ustawienia trybu Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">dzierżawy</a>. Należy pamiętać, że EDR trybie blokowania jest zalecane przede wszystkim dla urządzeń z kodem MDAV w trybie pasywnym (aktywna jest funkcja audio/wideo innej firmy). 

> [!TIP]
> Przed [włączeniem trybu blokowania](#requirements-for-edr-in-block-mode) upewnij się, że są EDR w trybie blokowania.

### <a name="security-portal"></a>Portal zabezpieczeń 

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com/](https://security.microsoft.com/)) i zaloguj się.
2. Wybierz **Ustawienia** \> **Punkty końcowe Ogólne** \>  \> **funkcje zaawansowane**.
3. Przewiń w dół, a następnie włącz **opcję Włącz EDR w trybie blokowania**.

### <a name="intune"></a>Intune

Aby utworzyć zasady niestandardowe w usłudze Intune, zobacz Wdrażanie OMA-URIs csp w usłudze Intune i porównanie z lokalnym [środowiskem](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune).

Aby uzyskać więcej informacji na temat programu CSP usługi Defender używanego do EDR w trybie blokowania, zobacz "Konfiguracja/strona biernaRemediation" w programie [Defender CSP](/windows/client-management/mdm/defender-csp).


## <a name="requirements-for-edr-in-block-mode"></a>Wymagania dotyczące EDR w trybie blokowania

|Wymaganie|Szczegóły|
|---|---|
|Uprawnienia|Administrator globalny lub administrator zabezpieczeń musi mieć przypisaną rolę administratora globalnego [lub administratora zabezpieczeń](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal) w Azure Active Directory. Aby uzyskać więcej informacji, zobacz [Uprawnienia podstawowe](basic-permissions.md).|
|System operacyjny|Na urządzeniach musi być uruchomiona jedna z następujących wersji programu Windows: <br/>- Windows 10 (wszystkie wersje)<br/>- Windows Server, wersja 1803 lub nowsza<br/>- Windows Server 2019<br/>- Windows Server 2022<br/>— Windows Server 2016 (tylko wtedy, Program antywirusowy Microsoft Defender jest w trybie aktywnym)|
|Ochrona punktu końcowego w usłudze Microsoft Defender|Urządzenia muszą być podłączone do usługi Defender for Endpoint. Zobacz [Minimalne wymagania programu Microsoft Defender dla punktu końcowego](minimum-requirements.md).|
|Program antywirusowy Microsoft Defender|Urządzenia muszą Program antywirusowy Microsoft Defender zainstalowane i uruchomione w trybie aktywnym lub pasywnym. [Upewnij Program antywirusowy Microsoft Defender, że aktywny lub pasywny jest aktywny](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|Ochrona w chmurze|Program antywirusowy Microsoft Defender musi być tak skonfigurowany, aby włączono [ochronę w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md).|
|Program antywirusowy Microsoft Defender platformę|Urządzenia muszą być aktualne. Aby potwierdzić, używając programu PowerShell, uruchom [polecenie cmdlet Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) jako administrator. W **wierszu AMProductVersion** powinien być wyświetlony ciąg **4.18.2001.10** lub wyżej. <p> Aby dowiedzieć się więcej, zobacz [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md).|
|Program antywirusowy Microsoft Defender aparat|Urządzenia muszą być aktualne. Aby potwierdzić, używając programu PowerShell, uruchom [polecenie cmdlet Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) jako administrator. W **wierszu AMEngineVersion** powinien być wyświetlony wiersz **1.1.16700.2** lub więcej. <p> Aby dowiedzieć się więcej, zobacz [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md).|

> [!IMPORTANT]
> Aby uzyskać najlepszą wartość ochrony, upewnij się, że twoje rozwiązanie antywirusowe jest skonfigurowane do odbierania regularnych aktualizacji i podstawowych funkcji oraz że twoje wykluczenia [są skonfigurowane](configure-exclusions-microsoft-defender-antivirus.md). EDR trybie blokowania szanuje wykluczenia zdefiniowane dla programu Program antywirusowy Microsoft Defender, ale nie wskaźniki, które są zdefiniowane dla programu [](manage-indicators.md) Microsoft Defender dla punktu końcowego.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Czy muszę włączać tryb EDR blokowania, jeśli mam Program antywirusowy Microsoft Defender na urządzeniach?

Podstawowym celem usuwania EDR w trybie blokowania jest korygowanie problemów z wykrywaniem naruszeń, które zostały nieodebrane przez produkt antywirusowy innych niż firmy Microsoft. Zalecamy jednak, aby w trybie EDR włączona, niezależnie od tego, Program antywirusowy Microsoft Defender działa w trybie pasywnym, czy w trybie aktywnym.

- Gdy Program antywirusowy Microsoft Defender jest w trybie pasywnym, tryb EDR trybie blokowania zapewnia kolejną warstwę obrony wraz z usługą Microsoft Defender for Endpoint.
- Gdy program Program antywirusowy Microsoft Defender jest w trybie aktywnym, tryb EDR tryb blokowania nie umożliwia dodatkowego skanowania, ale umożliwia programowi Program antywirusowy Microsoft Defender automatyczne akcje dotyczące po naruszeniu zabezpieczeń i zachowań EDR wykrywania.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>Czy EDR w trybie blokowania będzie miało wpływ na ochronę antywirusową użytkownika?

EDR trybie blokowania nie wpływa na ochronę antywirusową uruchamianą na urządzeniach użytkowników przez inne firmy. EDR trybie blokowania działa w przypadku, gdy podstawowe rozwiązanie antywirusowe czegoś przeobrabi lub jeśli wykrycie naruszenia zostanie naruszyne. EDR trybie blokowania działa tak samo Program antywirusowy Microsoft Defender w trybie pasywnym, z tym że tryb EDR w trybie blokowania blokuje i rekultywuje złośliwe artefakty lub zachowania, które są wykrywane.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Dlaczego muszę być na bieżąco Program antywirusowy Microsoft Defender?

Ponieważ Program antywirusowy Microsoft Defender wykrywa i rekultywuje złośliwe elementy, należy zadbać o jego aktualny dostęp. Aby EDR tryb blokowy, używa ona najnowszych modeli nauki urządzeń, wykrywania zachowań i heuristics. Stos [funkcji programu Defender for Endpoint](microsoft-defender-endpoint.md) działa w zintegrowany sposób. Aby uzyskać najlepszą wartość ochrony, pamiętaj Program antywirusowy Microsoft Defender na bieżąco. Zobacz [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Dlaczego jest potrzebna ochrona chmury (MAPS) w usłudze?

Aby włączyć tę funkcję na urządzeniu, ochrona chmury jest potrzebna. Ochrona w chmurze umożliwia usłudze [Defender dla](microsoft-defender-endpoint.md) punktu końcowego dostarczanie najnowszej i najwspanialszej ochrony w oparciu o nasze strony i głębie analizy zabezpieczeń, a także modeli nauki zachowań i urządzeń.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Jaka jest różnica między trybem aktywnym i pasywnym?

W przypadku punktów końcowych z systemem Windows 10, Windows 11, Windows Server w wersji 1803 lub nowszej, Windows Server 2019 lub Windows Server 2022, gdy program Program antywirusowy Microsoft Defender jest w trybie aktywnym, jest on używany jako podstawowe oprogramowanie antywirusowe na . Jeśli pracujesz w trybie pasywnym, Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym. W takim przypadku zagrożenia nie są korygowane przez Program antywirusowy Microsoft Defender w czasie rzeczywistym.

> [!NOTE]
> Program antywirusowy Microsoft Defender działać w trybie pasywnym tylko wtedy, gdy urządzenie jest włoowane do programu Microsoft Defender for Endpoint.

Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender zgodności](microsoft-defender-antivirus-compatibility.md).

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Jak potwierdzić, Program antywirusowy Microsoft Defender jest aktywny lub pasywny?

Aby sprawdzić, czy Program antywirusowy Microsoft Defender działa w trybie aktywnym, czy pasywnym, możesz użyć wiersza polecenia lub programu PowerShell na urządzeniu z uruchomionym Windows.

<br/><br/>

|Metoda|Procedura|
|---|---|
|PowerShell|1. Zaznacz menu Start, zacznij pisać `PowerShell`, a następnie otwórz Windows PowerShell w wynikach.<br/><br/>2. Wpisz `Get-MpComputerStatus`.<br/><br/>3. Na liście wyników w wierszu **AMRunningMode** poszukaj jednej z następujących wartości:<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>Aby dowiedzieć się więcej, [zobacz Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|Wiersz polecenia|1. Wybierz wiersz menu Start, zacznij pisać `Command Prompt`, a następnie Windows w wynikach wiersza polecenia.<br/><br/>2. Wpisz `sc query windefend`.<br/><br/>3. Na liście wyników w wierszu **WOJEWÓDZTWO** potwierdź, że usługa jest uruchomiona. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Jak sprawdzić, czy tryb EDR jest włączony w trybie Program antywirusowy Microsoft Defender w trybie pasywnym?

Za pomocą programu PowerShell można sprawdzić, EDR tryb blokowania jest włączony w trybie Program antywirusowy Microsoft Defender w trybie pasywnym.

1. Zaznacz menu Start, zacznij pisać `PowerShell`, a następnie otwórz Windows PowerShell w wynikach.

2. Typ: `Get-MPComputerStatus|select AMRunningMode`.

3. Potwierdź, że zostanie wyświetlony wynik ( `EDR Block Mode`.

   > [!TIP]
   > Jeśli Program antywirusowy Microsoft Defender jest w trybie aktywnym, będzie wyświetlony zamiast `Normal` .`EDR Block Mode` Aby dowiedzieć się więcej, [zobacz Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016"></a>Czy EDR tryb blokowania jest obsługiwany na Windows Server 2016?

Jeśli Program antywirusowy Microsoft Defender działa w trybie aktywnym lub pasywnym, EDR trybie blokowania jest obsługiwane w następujących wersjach programu Windows:

- Windows 10 (wszystkie wersje)
- Windows Server w wersji 1803 lub nowszej 
- Windows Server 2022
- Windows Server 2019 
- System Windows Server 2016
- Windows Server 2012 R2
- Windows 11

>[!NOTE]
>Windows Server 2016 i Windows Server 2012 R2 muszą zostać naniesone zgodnie z instrukcjami podanymi w te sposób: Windows [onboard](configure-server-endpoints.md), aby ta funkcja działała. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Ile czasu trwa wyłączenie EDR w trybie blokowania?

Jeśli wyłączysz funkcję EDR trybie blokowania, wyłączenie tej funkcji przez system może potrwać do 30 minut.

## <a name="see-also"></a>Zobacz też

- [Blog Community tech:Introducing EDR in block mode: Stopping attacks in their tracks](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)
- [Blokowanie i blokowanie zachowań](behavioral-blocking-containment.md)
