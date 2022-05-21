---
title: Wykrywanie punktów końcowych i reagowanie w trybie bloku
description: Dowiedz się więcej o wykrywanie i reagowanie w punktach końcowych w trybie bloku
keywords: Ochrona punktu końcowego w usłudze Microsoft Defender, mde, EDR w trybie bloku, blokowanie trybu pasywnego
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
ms.date: 04/04/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: c8b3016517393b473bcae664a6044098e04ebf6d
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623596"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Wykrywanie i reagowanie na punkty końcowe (EDR) w trybie bloku

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Co to jest EDR w trybie bloku?

[Wykrywanie i reagowanie punktów końcowych](overview-endpoint-detection-response.md) (EDR) w trybie bloku zapewnia dodatkową ochronę przed złośliwymi artefaktami, gdy Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym i działa w trybie pasywnym. EDR w trybie bloku działa w tle, aby korygować złośliwe artefakty, które zostały wykryte przez EDR możliwości. Takie artefakty mogły zostać pominięte przez podstawowy produkt antywirusowy spoza firmy Microsoft. W przypadku urządzeń z systemem Program antywirusowy Microsoft Defender jako podstawowym programem antywirusowym EDR w trybie bloku zapewnia dodatkową warstwę ochrony, umożliwiając Program antywirusowy Microsoft Defender wykonywanie automatycznych działań w przypadku wykrywania EDR behawioralnych po naruszeniu zabezpieczeń.

> [!IMPORTANT]
> EDR w trybie bloku nie zapewnia całej ochrony dostępnej po włączeniu Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym. Wszystkie funkcje, które zależą od Program antywirusowy Microsoft Defender jako aktywnego rozwiązania antywirusowego, nie będą działać, w tym następujące kluczowe przykłady:
>
> - Ochrona w czasie rzeczywistym, w tym skanowanie przy dostępie, nie jest dostępna, gdy Program antywirusowy Microsoft Defender jest w trybie pasywnym. Aby dowiedzieć się więcej na temat ustawień zasad ochrony w czasie rzeczywistym, zobacz **[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony](configure-real-time-protection-microsoft-defender-antivirus.md)**.
>
> - Funkcje, takie jak **[reguły ochrony sieci](network-protection.md)** i **[zmniejszania obszaru ataków](attack-surface-reduction.md)**, są dostępne tylko wtedy, gdy Program antywirusowy Microsoft Defender działa w trybie aktywnym.
>
> Oczekuje się, że rozwiązanie antywirusowe firmy innej niż Microsoft zapewnia te możliwości.

EDR w trybie bloku jest zintegrowana z [& zarządzanie lukami w zabezpieczeniach zagrożeń](next-gen-threat-and-vuln-mgt.md). Zespół ds. zabezpieczeń organizacji otrzyma [zalecenie dotyczące zabezpieczeń](tvm-security-recommendation.md), aby włączyć EDR w trybie bloku, jeśli nie jest jeszcze włączona.

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="Zalecenie włączenia EDR w trybie bloku" lightbox="images/edrblockmode-TVMrecommendation.png":::

> [!TIP]
> Aby uzyskać najlepszą ochronę, należy **[wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender punktów odniesienia](configure-machines-security-baseline.md)**.

Obejrzyj ten film wideo, aby dowiedzieć się, dlaczego i jak włączyć wykrywanie i reagowanie w punktach końcowych (EDR) w trybie bloku, włączyć blokowanie zachowań i ograniczanie na każdym etapie od wstępnego naruszenia do po naruszeniu zabezpieczeń. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4HjW2]

## <a name="what-happens-when-something-is-detected"></a>Co się stanie, gdy coś zostanie wykryte?

Po włączeniu EDR w trybie bloku i wykryciu złośliwego artefaktu Ochrona punktu końcowego w usłudze Microsoft Defender blokuje i koryguje ten artefakt. Twój zespół ds. operacji zabezpieczeń będzie widzieć stan wykrywania **jako Zablokowany** lub **Zablokowany** w [centrum akcji](respond-machine-alerts.md#check-activity-details-in-action-center), wymieniony jako ukończone akcje.

Na poniższej ilustracji przedstawiono wystąpienie niechcianego oprogramowania, które zostało wykryte i zablokowane przez EDR w trybie bloku:

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="Wykrywanie przez EDR w trybie bloku" lightbox="images/edr-in-block-mode-detection.png":::


## <a name="enable-edr-in-block-mode"></a>Włączanie EDR w trybie bloku

> [!IMPORTANT]
> Począwszy od platformy w wersji 4.18.2202.X, możesz teraz ustawić EDR w trybie bloku, tak aby była przeznaczona dla określonych grup urządzeń przy użyciu Intune dostawców CSP. Możesz nadal ustawiać EDR w trybie bloku dla całej dzierżawy w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>. EDR w trybie bloku jest zalecane przede wszystkim w przypadku urządzeń, które działają Program antywirusowy Microsoft Defender w trybie pasywnym (na urządzeniu jest zainstalowane i aktywne rozwiązanie antywirusowe innej firmy niż Microsoft). 

> [!TIP]
> Przed włączeniem EDR w trybie bloku upewnij się, że [wymagania](#requirements-for-edr-in-block-mode) zostały spełnione.

### <a name="security-portal"></a>Portal zabezpieczeń 

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) i zaloguj się.

2. Wybierz **pozycję Ustawienia** \> Ogólne **funkcje zaawansowane** **punktów końcowych** \>  \>.

3. Przewiń w dół, a następnie włącz opcję **Włącz EDR w trybie bloku**.

### <a name="intune"></a>Intune

Aby utworzyć zasady niestandardowe w Intune, zobacz [Deploy OMA-URIs to target a CSP through Intune (Wdrażanie OMA-URIs do docelowego dostawcy CSP za pośrednictwem Intune) oraz porównanie z lokalnymi](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune).

Aby uzyskać więcej informacji na temat dostawcy CSP usługi Defender używanego do EDR w trybie bloku, zobacz "Configuration/PassiveRemediation" (Konfiguracja/PasywneRemediacja) w obszarze [Dostawca CSP usługi Defender](/windows/client-management/mdm/defender-csp).


## <a name="requirements-for-edr-in-block-mode"></a>Wymagania dotyczące EDR w trybie bloku

W poniższej tabeli wymieniono wymagania dotyczące EDR w trybie bloku:

|Wymóg|Szczegóły|
|---|---|
|Uprawnienia|Musisz mieć przypisaną rolę administratora globalnego lub administratora zabezpieczeń w [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Aby uzyskać więcej informacji, zobacz [Podstawowe uprawnienia](basic-permissions.md).|
|System operacyjny|Urządzenia muszą mieć uruchomioną jedną z następujących wersji Windows: <br/>- Windows 11 <br/>- Windows 10 (wszystkie wersje)<br/>- Windows Server 2022 <br/>- Windows Server 2019<br/>— serwer Windows, wersja 1803 lub nowsza<br/>- Windows Server 2016 i Windows Server 2012 R2 (z [nowym ujednoliconym rozwiązaniem klienta](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))<sup>[[1](#fn1)]</sup>  |
|Ochrona punktu końcowego w usłudze Microsoft Defender|Urządzenia muszą być dołączone do usługi Defender for Endpoint. Zobacz następujące artykuły: <br/>- [Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender](minimum-requirements.md)<br/>- [Dołączanie urządzeń i konfigurowanie możliwości Ochrona punktu końcowego w usłudze Microsoft Defender](onboard-configure.md)<br/>- [Dołączanie serwerów Windows do usługi Defender for Endpoint](configure-server-endpoints.md)<br/>- [Nowe funkcje Windows Server 2012 R2 i 2016 w nowoczesnym ujednoliconym rozwiązaniu (wersja zapoznawcza)](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) |
|Program antywirusowy Microsoft Defender|Urządzenia muszą mieć Program antywirusowy Microsoft Defender zainstalowane i uruchomione w trybie aktywnym lub pasywnym. [Upewnij się, Program antywirusowy Microsoft Defender jest w trybie aktywnym lub pasywnym](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|Ochrona dostarczana przez chmurę|Program antywirusowy Microsoft Defender należy skonfigurować w taki sposób, aby [włączono ochronę dostarczaną przez chmurę](enable-cloud-protection-microsoft-defender-antivirus.md).|
|platforma Program antywirusowy Microsoft Defender|Urządzenia muszą być aktualne. Aby potwierdzić, używając programu PowerShell, uruchom polecenie cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) jako administrator. W **wierszu AMProductVersion** powinna być widoczna wersja **4.18.2001.10 lub nowsza** . <p> Aby dowiedzieć się więcej, zobacz [Zarządzanie aktualizacji programu antywirusowego Microsoft Defender i stosowanie punktów odniesienia](manage-updates-baselines-microsoft-defender-antivirus.md).|
|aparat Program antywirusowy Microsoft Defender|Urządzenia muszą być aktualne. Aby potwierdzić, używając programu PowerShell, uruchom polecenie cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) jako administrator. W wierszu **AMEngineVersion** powinna zostać wyświetlona wartość **1.1.16700.2** lub nowsza. <p> Aby dowiedzieć się więcej, zobacz [Zarządzanie aktualizacji programu antywirusowego Microsoft Defender i stosowanie punktów odniesienia](manage-updates-baselines-microsoft-defender-antivirus.md).|

(<a id="fn1">1</a>) Czy [EDR jest obsługiwany w trybie bloku w Windows Server 2016 i Windows Server 2012 R2?](#is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2)

> [!IMPORTANT]
> Aby uzyskać najlepszą wartość ochrony, upewnij się, że rozwiązanie antywirusowe jest skonfigurowane do otrzymywania regularnych aktualizacji i podstawowych funkcji oraz że [wykluczenia są skonfigurowane](configure-exclusions-microsoft-defender-antivirus.md). EDR w trybie bloku uwzględnia wykluczenia zdefiniowane dla Program antywirusowy Microsoft Defender, ale nie [wskaźniki](manage-indicators.md) zdefiniowane dla Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="can-i-specify-exclusions-for-edr-in-block-mode"></a>Czy mogę określić wykluczenia dla EDR w trybie bloku?

Po uzyskaniu wyniku fałszywie dodatniego możesz przesłać plik do analizy w [witrynie przesyłania Microsoft Security Intelligence](https://www.microsoft.com/en-us/wdsi/filesubmission).

Można również zdefiniować wykluczenie dla Program antywirusowy Microsoft Defender. Zobacz [Konfigurowanie i weryfikowanie wykluczeń dla skanowania Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Czy muszę włączyć EDR w trybie bloku, jeśli mam Program antywirusowy Microsoft Defender uruchomione na urządzeniach?

Głównym celem EDR w trybie bloku jest korygowanie wykryć po naruszeniu zabezpieczeń, które zostały pominięte przez produkt antywirusowy firmy innej niż Microsoft. Włączenie EDR w trybie bloku przy Program antywirusowy Microsoft Defender jest w trybie aktywnym, ponieważ ochrona w czasie rzeczywistym powinna najpierw przechwytywać i korygować wykrycia. Zalecamy włączenie EDR w trybie bloku w punktach końcowych, w których program antywirusowy Microsoft Defender for Antivirus działa w trybie pasywnym. EDR wykrywanie może być automatycznie korygowane przez [ochronę pua](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) lub [przez zautomatyzowane badanie & możliwości korygowania](automated-investigations.md) w trybie bloku.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>Czy EDR w trybie bloku wpłynie na ochronę antywirusową użytkownika?

EDR w trybie bloku nie ma wpływu na ochronę antywirusową innych firm działającą na urządzeniach użytkowników. EDR w trybie bloku działa, jeśli podstawowe rozwiązanie antywirusowe coś przegapi lub w przypadku wykrycia po naruszeniu zabezpieczeń. EDR w trybie bloku działa podobnie jak Program antywirusowy Microsoft Defender w trybie pasywnym, z tą różnicą, że EDR w trybie bloku blokuje i koryguje wykryte złośliwe artefakty lub zachowania.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Dlaczego muszę być na bieżąco Program antywirusowy Microsoft Defender?

Ponieważ Program antywirusowy Microsoft Defender wykrywa i koryguje złośliwe elementy, ważne jest, aby być na bieżąco. Aby EDR w trybie bloku były skuteczne, używa najnowszych modeli uczenia urządzenia, wykrywania zachowań i heurystyki. Stos możliwości [usługi Defender for Endpoint](microsoft-defender-endpoint.md) działa w sposób zintegrowany. Aby uzyskać najlepszą wartość ochrony, należy zachować aktualną Program antywirusowy Microsoft Defender. Zobacz [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie punktów odniesienia](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Dlaczego potrzebujemy ochrony w chmurze (MAPS)?

Ochrona w chmurze jest potrzebna do włączenia funkcji na urządzeniu. Ochrona w chmurze umożliwia [usłudze Defender for Endpoint](microsoft-defender-endpoint.md) zapewnienie najnowszej i największej ochrony w oparciu o naszą rozległość i głębię analizy zabezpieczeń, a także modele uczenia behawioralnego i urządzenia.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Jaka jest różnica między trybem aktywnym i pasywnym?

W przypadku punktów końcowych z systemem Windows 10, Windows 11, Windows Server w wersji 1803 lub nowszej, Windows Server 2019 lub Windows Server 2022, gdy Program antywirusowy Microsoft Defender jest w trybie aktywnym, jest on używany jako podstawowy program antywirusowy na urządzeniu. W trybie pasywnym Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym. W takim przypadku zagrożenia nie są korygowane przez Program antywirusowy Microsoft Defender w czasie rzeczywistym.

> [!NOTE]
> Program antywirusowy Microsoft Defender może działać w trybie pasywnym tylko wtedy, gdy urządzenie jest dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender.

Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender zgodność](microsoft-defender-antivirus-compatibility.md).

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Jak mogę potwierdzić, Program antywirusowy Microsoft Defender jest w trybie aktywnym lub pasywnym?

Aby potwierdzić, czy Program antywirusowy Microsoft Defender działa w trybie aktywnym, czy pasywnym, możesz użyć wiersza polecenia lub programu PowerShell na urządzeniu z uruchomionym Windows.

|Metoda|Procedura|
|---|---|
|PowerShell|1. Wybierz menu Start, rozpocznij wpisywanie `PowerShell`, a następnie otwórz Windows PowerShell w wynikach.<br/><br/>2. Wpisz `Get-MpComputerStatus`.<br/><br/>3. Na liście wyników w wierszu **AMRunningMode** poszukaj jednej z następujących wartości:<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>Aby dowiedzieć się więcej, zobacz [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|Wiersz polecenia|1. Wybierz menu Start, rozpocznij wpisywanie `Command Prompt`, a następnie otwórz Windows wiersza polecenia w wynikach.<br/><br/>2. Wpisz `sc query windefend`.<br/><br/>3. Na liście wyników w wierszu **STATE** upewnij się, że usługa jest uruchomiona. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Jak mogę potwierdzić, że EDR w trybie bloku jest włączona z Program antywirusowy Microsoft Defender w trybie pasywnym?

Za pomocą programu PowerShell możesz potwierdzić, że EDR w trybie bloku jest włączony, a Program antywirusowy Microsoft Defender działa w trybie pasywnym.

1. Wybierz menu Start, rozpocznij wpisywanie `PowerShell`, a następnie otwórz Windows PowerShell w wynikach.

2. Typ: `Get-MPComputerStatus|select AMRunningMode`.

3. Upewnij się, `EDR Block Mode`że jest wyświetlany wynik , .

   > [!TIP]
   > Jeśli Program antywirusowy Microsoft Defender jest w trybie aktywnym, zobaczysz `Normal` zamiast `EDR Block Mode`. Aby dowiedzieć się więcej, zobacz [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2"></a>Czy EDR w trybie bloku jest obsługiwane w Windows Server 2016 i Windows Server 2012 R2?

Jeśli Program antywirusowy Microsoft Defender działa w trybie aktywnym lub pasywnym, EDR w trybie bloku są obsługiwane następujące wersje Windows:

- Windows 11
- Windows 10 (wszystkie wersje)
- Windows Server, wersja 1803 lub nowsza 
- Windows Server 2022
- Windows Server 2019 
- Windows Server 2016 i Windows Server 2012 R2 (z [nowym ujednoliconym rozwiązaniem klienckim](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))

Dzięki [nowemu ujednoliconemu rozwiązaniu klienckiemu](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) dla Windows Server 2016 i Windows Server 2012 R2 można uruchamiać EDR w trybie bloku w trybie pasywnym lub aktywnym.

> [!NOTE]
> Windows Server 2016 i Windows Server 2012 R2 muszą zostać dołączone przy użyciu instrukcji zawartych w temacie [Dołączanie serwerów Windows](configure-server-endpoints.md), aby ta funkcja działała. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Ile czasu zajmuje wyłączenie EDR w trybie bloku?

Jeśli zdecydujesz się wyłączyć EDR w trybie bloku, wyłączenie tej możliwości przez system może potrwać do 30 minut.

## <a name="see-also"></a>Zobacz też

- [Blog tech Community: wprowadzenie EDR w trybie bloku: zatrzymywanie ataków na swoich torach](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)

- [Blokowanie i ograniczanie behawioralne](behavioral-blocking-containment.md)
