---
title: Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi
description: Dowiedz się więcej o Program antywirusowy Microsoft Defender z innymi produktami zabezpieczeń i systemami operacyjnymi.
keywords: windows defender, defender for endpoint, next-generation, antivirus, compatibility, passive mode
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.technology: mde
ms.date: 04/19/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 3bae6326fca5cefc921cb24b1a16180da2a2f52f
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415134"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi

**Dotyczy:**

- Program antywirusowy Microsoft Defender
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

**Platformy**
- System Windows

[!include[Prerelease information](../../includes/prerelease.md)]

Program antywirusowy Microsoft Defender jest automatycznie instalowana w punktach końcowych z następującymi wersjami Windows:

- Windows 10 lub nowsze
- Windows Server 2022
- Windows Server 2019
- Windows Server, wersja 1803 lub nowsza
- System Windows Server 2016

Co się stanie, gdy zostanie użyte inne rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft? Czy można uruchomić Program antywirusowy Microsoft Defender obok innego produktu antywirusowego? Odpowiedzi zależą od kilku czynników, takich jak system operacyjny i czy używasz [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md) razem z ochroną antywirusową.

W tym artykule opisano, co dzieje się z Program antywirusowy Microsoft Defender i rozwiązaniem antywirusowym/chroniącym przed złośliwym kodem firmy Microsoft, z usługą Defender for Endpoint i bez jej użycia.

> [!IMPORTANT]
> - Program antywirusowy Microsoft Defender jest dostępna na urządzeniach z systemem Windows 10 i 11, Windows Server 2022, Windows Server 2019, Windows Server, wersja 1803 lub nowsza i Windows Server 2016. 
> - Program antywirusowy Microsoft Defender jest również dostępna w Windows Server 2012 R2 po dołączeniu przy użyciu [nowoczesnego, ujednoliconego rozwiązania](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - W Windows 8.1 ochrona antywirusowa punktu końcowego na poziomie przedsiębiorstwa jest oferowana jako [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10), który jest zarządzany za pośrednictwem Microsoft Endpoint Configuration Manager.
> - Windows Defender jest również oferowana dla [urządzeń konsumenckich w Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), chociaż Windows Defender nie zapewnia zarządzania na poziomie przedsiębiorstwa.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Ochrona antywirusowa bez usługi Defender dla punktu końcowego

W tej sekcji opisano, co się dzieje, gdy używasz Program antywirusowy Microsoft Defender obok produktów antywirusowych/chroniących przed złośliwym kodem firmy Microsoft w punktach końcowych, które nie są dołączone do usługi Defender for Endpoint. 

> [!NOTE]
> Ogólnie rzecz biorąc, Program antywirusowy Microsoft Defender nie działa w trybie pasywnym na urządzeniach, które nie są dołączone do usługi Defender for Endpoint.

Poniższa tabela zawiera podsumowanie oczekiwań:

|Wersje systemu Windows|Podstawowe rozwiązanie antywirusowe/chroniące przed złośliwym kodem|stan Program antywirusowy Microsoft Defender|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Program antywirusowy Microsoft Defender|Tryb aktywny|
|Windows 10 <br/> Windows 11|Rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft|Tryb wyłączony (odbywa się automatycznie)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, wersja 1803 lub nowsza <br/> System Windows Server 2016 |Program antywirusowy Microsoft Defender|Tryb aktywny|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, wersja 1803 lub nowsza <br/> System Windows Server 2016  |Rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft|Wyłączone (ustaw ręcznie) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Na serwerze Windows, jeśli korzystasz z oprogramowania antywirusowego innego niż Microsoft, możesz odinstalować Program antywirusowy Microsoft Defender, aby zapobiec konfliktom. Jeśli urządzenie jest dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender, możesz użyć Program antywirusowy Microsoft Defender w trybie pasywnym (patrz poniżej).

> [!TIP]
> Na Windows Server 2016 może pojawić *się Program antywirusowy Windows Defender* zamiast *Program antywirusowy Microsoft Defender*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Program antywirusowy Microsoft Defender i rozwiązania antywirusowe/chroniące przed złośliwym kodem firmy Microsoft

> [!NOTE]
> Ogólnie rzecz biorąc, Program antywirusowy Microsoft Defender można ustawić na tryb pasywny tylko w punktach końcowych dołączonych do usługi Defender for Endpoint.

To, czy Program antywirusowy Microsoft Defender działa w trybie aktywnym, trybie pasywnym, czy jest wyłączone, zależy od kilku czynników, takich jak:

- Która wersja Windows jest zainstalowana w punkcie końcowym
- Czy Program antywirusowy Microsoft Defender jest podstawowym rozwiązaniem antywirusowym/chroniącym przed złośliwym kodem w punkcie końcowym
- Czy punkt końcowy jest dołączony do usługi Defender for Endpoint

W poniższej tabeli podsumowano stan Program antywirusowy Microsoft Defender w kilku scenariuszach. 

| Wersje systemu Windows   | Rozwiązanie antywirusowe/chroniące przed złośliwym kodem  | Dołączone do <br/> Defender dla punktu końcowego? | stan Program antywirusowy Microsoft Defender     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Program antywirusowy Microsoft Defender | Tak  | Tryb aktywny | 
| Windows 10 <br/> Windows 11 | Program antywirusowy Microsoft Defender | Nie   | Tryb aktywny |
| Windows 10 <br/> Windows 11  | Rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft | Tak  | Tryb pasywny (automatycznie) |
| Windows 10 <br/> Windows 11  | Rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft | Nie   | Tryb wyłączony (automatycznie)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server, wersja 1803 lub nowsza  | Program antywirusowy Microsoft Defender  | Tak |         Tryb aktywny  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server, wersja 1803 lub nowsza   | Program antywirusowy Microsoft Defender | Nie  | Tryb aktywny |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, wersja 1803 lub nowsza  | Rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft | Tak  | Program antywirusowy Microsoft Defender należy ustawić na tryb pasywny (ręcznie) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, wersja 1803 lub nowsza  | Rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft | Nie  | Program antywirusowy Microsoft Defender należy wyłączyć (ręcznie) <sup>[[3](#fn3)]<sup></sup>  |
| System Windows Server 2016 <br/> Windows Server 2012 R2   | Program antywirusowy Microsoft Defender | Tak | Tryb aktywny |
|System Windows Server 2016 <br/> Windows Server 2012 R2  | Program antywirusowy Microsoft Defender | Nie | Tryb aktywny |
| System Windows Server 2016 <br/> Windows Server 2012 R2  | Rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft | Tak | Program antywirusowy Microsoft Defender należy ustawić na tryb pasywny (ręcznie) <sup>[[2](#fn2)]<sup> |
|System Windows Server 2016 <br/> Windows Server 2012 R2  | Rozwiązanie antywirusowe/chroniące przed złośliwym kodem firmy Microsoft | Nie | Program antywirusowy Microsoft Defender należy wyłączyć (ręcznie) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) Na Windows Server 2019, Windows Server, wersja 1803 lub nowsza, Windows Server 2016 lub Windows Server 2012 R2, Program antywirusowy Microsoft Defender  program antywirusowy innej firmy nie przechodzi automatycznie w tryb pasywny. W takich przypadkach ustaw Program antywirusowy Microsoft Defender na tryb pasywny, aby zapobiec problemom spowodowanym przez zainstalowanie wielu produktów antywirusowych na serwerze. Możesz ustawić Program antywirusowy Microsoft Defender na tryb pasywny przy użyciu programu PowerShell, zasady grupy lub klucza rejestru. 

  Możesz ustawić Program antywirusowy Microsoft Defender na tryb pasywny, ustawiając następujący klucz rejestru:
- Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nazwa: `ForceDefenderPassiveMode`
- Typu: `REG_DWORD`
- Wartość: `1`

 > [!NOTE]
 > Aby tryb pasywny działał w punktach końcowych z uruchomionymi Windows Server 2016 i Windows Server 2012 R2, te punkty końcowe muszą być dołączone do nowoczesnego, ujednoliconego rozwiązania opisanego w [temacie Dołączanie serwerów Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) W Windows Server 2016, Windows Server 2012 R2, Windows Server w wersji 1803 lub nowszej, Windows Server 2019 i Windows Server 2022, jeśli używasz produktu antywirusowego innego niż Microsoft w punkcie końcowym, który *nie* jest dołączony do Ochrona punktu końcowego w usłudze Microsoft Defender, wyłącz/odinstaluj Program antywirusowy Microsoft Defender ręcznie, aby zapobiec problemom spowodowanym przez zainstalowanie wielu produktów antywirusowych na serwerze.

> [!TIP]
> Na Windows Server 2016 może pojawić *się Program antywirusowy Windows Defender* zamiast *Program antywirusowy Microsoft Defender*.

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender jest dostępna tylko na urządzeniach z systemem Windows 10 i 11, Windows Server 2022, Windows Server 2019, Windows Server, wersja 1803 lub nowsza, Windows Server 2016 i Windows Server 2012 R2.
>
> W Windows 8.1 ochrona antywirusowa punktu końcowego na poziomie przedsiębiorstwa jest oferowana jako [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), która jest zarządzana za pośrednictwem Microsoft Endpoint Configuration Manager.
>
> Windows Defender jest również oferowana dla [urządzeń konsumenckich w Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), chociaż Windows Defender nie zapewnia zarządzania na poziomie przedsiębiorstwa.

Usługa Defender for Endpoint oferuje możliwości, które dodatkowo rozszerzają ochronę antywirusową zainstalowaną w punkcie końcowym. Możesz skorzystać z uruchamiania Program antywirusowy Microsoft Defender wraz z innym rozwiązaniem antywirusowym.

Na przykład [wykrywanie i reagowanie punktów końcowych (EDR) w trybie bloku](edr-in-block-mode.md) zapewnia dodatkową ochronę przed złośliwymi artefaktami, nawet jeśli Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym. Takie możliwości wymagają zainstalowania i uruchomienia Program antywirusowy Microsoft Defender w trybie pasywnym lub aktywnym.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Wymagania dotyczące uruchamiania Program antywirusowy Microsoft Defender w trybie pasywnym

Aby Program antywirusowy Microsoft Defender działała w trybie pasywnym, punkty końcowe muszą spełniać następujące wymagania:

- System operacyjny: Windows 10 lub nowszy; Windows Server 2022, Windows Server 2019 lub Windows Server, wersja 1803 lub nowsza
- Program antywirusowy Microsoft Defender należy zainstalować
- Inny produkt antywirusowy/chroniący przed złośliwym kodem firmy Microsoft musi być zainstalowany i używany jako podstawowe rozwiązanie antywirusowe
- Punkty końcowe muszą zostać dołączone do usługi Defender for Endpoint

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Jak Program antywirusowy Microsoft Defender wpływa na funkcjonalność usługi Defender for Endpoint

Usługa Defender dla punktu końcowego ma wpływ na to, czy Program antywirusowy Microsoft Defender może działać w trybie pasywnym. Program antywirusowy Microsoft Defender może również wpływać na niektóre możliwości w usłudze Defender for Endpoint. Na przykład ochrona w czasie rzeczywistym działa, gdy Program antywirusowy Microsoft Defender jest w trybie aktywnym lub pasywnym, ale nie wtedy, gdy Program antywirusowy Microsoft Defender jest wyłączona lub odinstalowana.

Tabela w tej sekcji zawiera podsumowanie funkcji i możliwości, które aktywnie działają, w zależności od tego, czy Program antywirusowy Microsoft Defender jest w trybie aktywnym, pasywnym, czy wyłączonym/odinstalowanym.

> [!IMPORTANT]
> Poniższa tabela została zaprojektowana tak, aby była tylko informacyjna. **Nie wyłączaj możliwości**, takich jak ochrona w czasie rzeczywistym, ochrona dostarczana w chmurze lub ograniczone okresowe skanowanie, jeśli używasz Program antywirusowy Microsoft Defender w trybie pasywnym lub jeśli używasz [EDR w trybie bloku](edr-in-block-mode.md), który działa w tle w celu wykrywania i korygowania złośliwych artefaktów, które zostały wykryte po naruszeniu zabezpieczeń.

| Ochrony | Program antywirusowy Microsoft Defender <br/>(*Tryb aktywny*) | Program antywirusowy Microsoft Defender <br/>(*Tryb pasywny*) | Program antywirusowy Microsoft Defender <br/>(*Wyłączone lub odinstalowane*) | [Funkcja EDR w trybie blokowania](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [Ochrona w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md) | Tak | Zobacz notatkę <sup>[[4](#fn4)]</sup> | Nie | Nie | 
| [Ochrona dostarczana przez chmurę](enable-cloud-protection-microsoft-defender-antivirus.md) | Tak | Nie  | Nie | Nie | 
| [Ochrona sieci](network-protection.md)  | Tak | Nie | Nie | Nie | 
| [Reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction.md)  | Tak | Nie | Nie  | Nie | 
| [Ograniczona okresowa dostępność skanowania](limited-periodic-scanning-microsoft-defender-antivirus.md) | Nie | Nie | Tak | Nie | 
| [Informacje o skanowaniu i wykrywaniu plików](review-scan-results-microsoft-defender-antivirus.md) | Tak | Tak<sup>[[5](#fn5)]</sup> | Nie | Tak | 
| [Korygowanie zagrożeń](configure-remediation-microsoft-defender-antivirus.md) | Tak | Zobacz notatkę <sup>[[6](#fn6)]</sup> | Nie | Tak | 
| [Aktualizacje analizy zabezpieczeń](manage-updates-baselines-microsoft-defender-antivirus.md) | Tak | Tak <sup>[[7](#fn7)]</sup> | Nie | Tak <sup>[[7](#fn7)]</sup> | 
| [Zapobieganie utracie danych](../../compliance/endpoint-dlp-learn-about.md) | Tak | Tak | Nie | Nie |
| [Kontrolowany dostęp do folderu](controlled-folders.md) | Tak |Nie | Nie | Nie |
| [Filtrowanie zawartości sieci Web](web-content-filtering.md) | Tak | Zobacz notatkę <sup>[[8](#fn8)]</sup> | Nie | Nie |
| [Sterowanie urządzeniem](device-control-report.md) | Tak | Tak | Nie | Nie |
| [Ochrona pua](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | Tak | Nie | Nie | Nie |

(<a id="fn4">4</a>) Ogólnie rzecz biorąc, gdy Program antywirusowy Microsoft Defender jest w trybie pasywnym, ochrona w czasie rzeczywistym nie zapewnia blokowania ani wymuszania, nawet jeśli jest włączona i w trybie pasywnym.

(<a id="fn5">5</a>) Jeśli Program antywirusowy Microsoft Defender jest w trybie pasywnym, skanowanie nie jest zaplanowane.

(<a id="fn6">6</a>) Gdy Program antywirusowy Microsoft Defender jest w trybie pasywnym, nie koryguje zagrożeń. Jednak zagrożenia mogą być korygowane przez [wykrywanie i reagowanie punktów końcowych (EDR) w trybie bloku](edr-in-block-mode.md). W takim przypadku mogą zostać wyświetlone alerty pokazujące Program antywirusowy Microsoft Defender jako źródło, nawet jeśli Program antywirusowy Microsoft Defender jest w trybie pasywnym.

(<a id="fn7">7</a>) Cykl aktualizacji analizy zabezpieczeń jest kontrolowany tylko przez ustawienia Windows Update. Ustawienia harmonogramów aktualizacji specyficznych dla usługi Defender (codziennie/co tydzień o określonej godzinie, na podstawie interwałów) działają tylko wtedy, gdy Program antywirusowy Microsoft Defender jest w trybie aktywnym. Są one ignorowane w trybie pasywnym.

(<a id="fn8">8</a>) Gdy Program antywirusowy Microsoft Defender jest w trybie pasywnym, filtrowanie zawartości internetowej działa tylko z przeglądarką Microsoft Edge. 

> [!NOTE]
> [Ochrona przed utratą danych punktu końcowego](/microsoft-365/compliance/endpoint-dlp-learn-about) nadal działa normalnie, gdy Program antywirusowy Microsoft Defender jest w trybie aktywnym lub pasywnym.

## <a name="important-notes"></a>Ważne uwagi

- Nie wyłączaj, nie zatrzymuj ani nie modyfikuj żadnych skojarzonych usług używanych przez Program antywirusowy Microsoft Defender, usługę Defender dla punktu końcowego ani aplikację Zabezpieczenia Windows. To zalecenie obejmuje usługi *i procesy wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* lub *MsMpEng* . Ręczne zmodyfikowanie tych usług może spowodować poważną niestabilność na urządzeniach i spowodować, że sieć będzie podatna na zagrożenia. Wyłączanie, zatrzymywanie lub modyfikowanie tych usług może również powodować problemy podczas korzystania z rozwiązań antywirusowych innych niż Microsoft i sposobu wyświetlania ich informacji w [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

- W usłudze Defender for Endpoint włącz EDR w trybie bloku, nawet jeśli Program antywirusowy Microsoft Defender nie jest podstawowym rozwiązaniem antywirusowym. EDR w trybie bloku wykrywa i koryguje złośliwe elementy znalezione na urządzeniu (po naruszeniu zabezpieczeń). Aby dowiedzieć się więcej, zobacz [EDR w trybie bloku](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Jak potwierdzić stan Program antywirusowy Microsoft Defender

Aby potwierdzić stan Program antywirusowy Microsoft Defender, można użyć jednej z kilku metod, zgodnie z opisem w poniższej tabeli:

 | Metoda | Procedura | 
 |:---|:---| 
 | aplikacja Zabezpieczenia Windows |  1. Na urządzeniu Windows otwórz aplikację Zabezpieczenia Windows.<br/>2. Wybierz pozycję **Ochrona przed zagrożeniami & wirusów**.<br/>3. W obszarze **ochrona KtoTo?** wybierz pozycję **Zarządzaj dostawcami**.<br/>4. Na stronie **Dostawcy zabezpieczeń** w obszarze **Program antywirusowy** powinna zostać wyświetlona Program antywirusowy Microsoft Defender **jest włączona**. | 
 | Menedżer zadań |  1. Na urządzeniu Windows otwórz aplikację Menedżer zadań.<br/>2. Wybierz kartę **Szczegóły** .<br/>3. Wyszukaj **MsMpEng.exe** na liście. | 
 | Windows PowerShell <br/> (Aby potwierdzić, że Program antywirusowy Microsoft Defender jest uruchomiona) |  1. Na urządzeniu Windows otwórz Windows PowerShell. <br/>2. Uruchom następujące polecenie cmdlet programu PowerShell: `Get-Process`.<br/>3. Przejrzyj wyniki. Jeśli Program antywirusowy Microsoft Defender jest włączona, powinna zostać wyświetlona **MsMpEng.exe**. | 
 | Windows PowerShell <br/>(Aby potwierdzić, że ochrona antywirusowa jest w miejscu) |  Możesz użyć [polecenia cmdlet Get-MpComputerStatus programu PowerShell](/powershell/module/defender/get-mpcomputerstatus).<br/>1. Na urządzeniu Windows otwórz Windows PowerShell.<br/>2. Uruchom następujące polecenie cmdlet programu PowerShell:<br/> \|Get-MpComputerStatus wybierz pozycję AMRunningMode <br/>3. Przejrzyj wyniki. Jeśli Program antywirusowy Microsoft Defender jest włączony w punkcie końcowym, powinien zostać wyświetlony tryb **normalny**, **pasywny** lub **EDR bloku**.  | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Więcej szczegółów na temat stanów Program antywirusowy Microsoft Defender

W tabeli w tej sekcji opisano różne stany, które mogą być widoczne w Program antywirusowy Microsoft Defender.

 |  Stan  |  Efekt  | 
 |:---|:---| 
 |  Tryb aktywny  |  W trybie aktywnym Program antywirusowy Microsoft Defender jest używana jako aplikacja antywirusowa na komputerze. Ustawienia skonfigurowane przy użyciu Configuration Manager, zasady grupy, Microsoft Intune lub innych produktów do zarządzania. Pliki są skanowane, zagrożenia są korygowane, a informacje o wykrywaniu są zgłaszane w narzędziu konfiguracji (takim jak Configuration Manager lub aplikacja Program antywirusowy Microsoft Defender w samym punkcie końcowym).  | 
 |  Tryb pasywny <br/><br/> lub <br/><br/> tryb bloku EDR |  W trybie pasywnym Program antywirusowy Microsoft Defender nie jest używana jako aplikacja antywirusowa, a zagrożenia *nie* są korygowane przez Program antywirusowy Microsoft Defender. <br/><br/>Zagrożenia mogą być korygowane przez [wykrywanie punktów końcowych i reagowanie (EDR) w trybie bloku](edr-in-block-mode.md) podczas uruchamiania w trybie bloku EDR. <br/><br/> Pliki są skanowane przez EDR, a raporty są udostępniane pod kątem wykrywania zagrożeń, które są udostępniane usłudze Defender for Endpoint. Alerty pokazujące Program antywirusowy Microsoft Defender jako źródło, nawet jeśli Program antywirusowy Microsoft Defender jest w trybie pasywnym. <br/><br/> Gdy Program antywirusowy Microsoft Defender jest w trybie pasywnym, nadal można [zarządzać aktualizacjami dla Program antywirusowy Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md); nie można jednak przenosić Program antywirusowy Microsoft Defender  w trybie aktywnym, jeśli urządzenia mają produkt antywirusowy firmy innej niż Microsoft, który zapewnia ochronę przed złośliwym oprogramowaniem w czasie rzeczywistym. <br/><br/> Aby uzyskać optymalną ochronę warstwową i skuteczność wykrywania, upewnij się, że oprogramowanie antywirusowe i oprogramowanie chroniące przed złośliwym kodem są aktualizowane, nawet jeśli Program antywirusowy Microsoft Defender działa w trybie pasywnym. Zobacz [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie punktów odniesienia](manage-updates-baselines-microsoft-defender-antivirus.md). <br/><br/> Należy pamiętać, że tryb pasywny jest obsługiwany tylko w Windows Server 2012 R2 & 2016 r., gdy maszyna jest dołączana przy użyciu [nowoczesnego, ujednoliconego rozwiązania](/microsoft-365/security/defender-endpoint/configure-server-endpoints).  | 
 |  Wyłączona <br/><br/> lub <br/><br/> Odinstalować  |  Po wyłączeniu lub odinstalowaniu Program antywirusowy Microsoft Defender nie jest używana jako aplikacja antywirusowa. Pliki nie są skanowane, a zagrożenia nie są korygowane. <br/><br/> Wyłączenie lub odinstalowanie Program antywirusowy Microsoft Defender nie jest zalecane ogólnie; jeśli to możliwe, zachowaj Program antywirusowy Microsoft Defender w trybie pasywnym, jeśli używasz rozwiązania chroniącego przed złośliwym kodem lub oprogramowania antywirusowego firmy innej niż Microsoft. <br/><br/> W przypadkach, gdy Program antywirusowy Microsoft Defender jest automatycznie wyłączona, można ją ponownie włączyć automatycznie, jeśli produkt antywirusowy/chroniący przed złośliwym kodem firmy microsoft wygaśnie lub w inny sposób przestanie zapewniać ochronę przed wirusami, złośliwym oprogramowaniem lub innymi zagrożeniami w czasie rzeczywistym. Automatyczne ponowne włączanie Program antywirusowy Microsoft Defender pomaga zapewnić utrzymanie ochrony antywirusowej w punktach końcowych. <br/><br/> Możesz również używać [ograniczonego okresowego skanowania](limited-periodic-scanning-microsoft-defender-antivirus.md), które współpracuje z aparatem Program antywirusowy Microsoft Defender, aby okresowo sprawdzać zagrożenia, jeśli używasz aplikacji antywirusowej innej niż Microsoft.  | 

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender na klientach Windows](microsoft-defender-antivirus-in-windows-10.md)
- [Program antywirusowy Microsoft Defender na serwerze Windows](microsoft-defender-antivirus-on-windows-server.md)
- [Funkcja EDR w trybie blokowania](edr-in-block-mode.md)
- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](/microsoft-365/compliance/endpoint-dlp-learn-about)
