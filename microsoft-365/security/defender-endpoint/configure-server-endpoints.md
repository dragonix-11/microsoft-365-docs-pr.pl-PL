---
title: Wdowa Windows usługi Microsoft Defender dla punktu końcowego
description: Na tych Windows, aby wysyłać dane czujnika do czujnika programu Microsoft Defender for Endpoint.
keywords: serwer onboard, serwer, 2012r2, 2016, 2019, dołączanie do serwera, zarządzanie urządzeniami, konfigurowanie programu Microsoft Defender dla serwerów punktów końcowych, dołączanie programu Microsoft Defender do serwerów punktów końcowych, dołączanie programu Microsoft Defender dla serwerów punktów końcowych
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2979216cb87982210ac33dd8e273702f8bc18bf0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328095"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>Wdowa Windows usługi Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- Windows Server 2012 R2
- System Windows Server 2016
- Windows Server Semi-Annual Enterprise Channel
- Windows Server 2019 lub nowszy
- Windows Server 2019 Core Edition
- Windows Server 2022
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configserver-abovefoldlink)

Program Defender for Endpoint obsługuje również system operacyjny Windows Server. Ta obsługa bezproblemowo udostępnia zaawansowane funkcje wykrywania ataków i badania za pośrednictwem Microsoft 365 Defender zaawansowanej. Obsługa serwera Windows zapewnia bardziej szczegółowe informacje o działaniach serwera, zasięgu wykrywania ataku kernelu i pamięci oraz umożliwia akcje odpowiedzi.

W tym temacie opisano, jak w programie Microsoft Defender for Endpoint Windows poszczególnych serwerów.

Aby uzyskać wskazówki dotyczące pobierania i używania planu bazowego Zabezpieczenia Windows dla Windows, zobacz Zabezpieczenia Windows [bazowe](/windows/device-security/windows-security-baselines).

## <a name="windows-server-onboarding-overview"></a>Windows dotyczące dołączania do serwera

Aby pomyślnie wdować się na serwerach, należy wykonać poniższe ogólne czynności.

![Ilustracja przepływu dołączania do Windows Serwerami i Windows 10 urządzeniami](images/server-onboarding-tools-methods.png)

**Windows Server 2012 R2 i Windows Server 2016 (wersja Preview)**

>[!IMPORTANT]
> Aby korzystać z tej funkcji, musisz włączyć funkcje wersji Preview w sekcji Microsoft 365 Defender punkty końcowe. Przejdź do [Microsoft 365 Defender > Ustawienia > punktów końcowych > zaawansowanych i](https://security.microsoft.com/preferences2/integration) włącz funkcje wersji Preview.

- Pobieranie pakietów instalacyjnych i pakietów dołączania
- Stosowanie pakietu instalacyjnego
- Postępuj zgodnie z instrukcjami dołączania dla odpowiedniego narzędzia

**Windows Server Semi-Annual Enterprise Channel and Windows Server 2019**

- Pobierz pakiet dołączający
- Postępuj zgodnie z instrukcjami dołączania dla odpowiedniego narzędzia

>[!IMPORTANT]
>Aby można było zakupić usługę Microsoft Defender for Endpoint Server SKU, musisz już zakupić co najmniej dowolną z następujących subskrypcji: Windows E5/A5, Microsoft 365 E5/A5 lub Zabezpieczenia platformy Microsoft 365 E5 subskrypcji.  Aby uzyskać więcej informacji na temat licencjonowania, zobacz [Postanowienia dotyczące produktu](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  



### <a name="new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview"></a>Nowe Windows Server 2012 R2 i 2016 w nowoczesnym, ujednoliconym rozwiązaniu (wersja Preview)

Wcześniejsza implementacja wdrożenia Windows Server 2012 R2 i Windows Server 2016 wymagała użycia Microsoft Monitoring Agent MMA.

Nowy ujednolicony pakiet rozwiązań ułatwia pracę na serwerach przez usunięcie zależności i kroków instalacji. Ponadto ten ujednolicony pakiet rozwiązań zawiera następujące główne ulepszenia:

- [Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) z ochroną [następnej generacji dla](/microsoft-365/security/defender-endpoint/next-generation-protection) Windows Server 2012 R2
- [Reguły ograniczania powierzchni ataków (ASR, Attack Surface Reduction)](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- [Ochrona sieci](/microsoft-365/security/defender-endpoint/network-protection)
- [Kontrolowany dostęp do folderu](/microsoft-365/security/defender-endpoint/controlled-folders)
- [Blokowanie potencjalnie niechcianej aplikacji (PUA)](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Ulepszone funkcje wykrywania](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
- [Rozszerzone funkcje odpowiedzi na](/microsoft-365/security/defender-endpoint/respond-machine-alerts) urządzeniach i [plikach](/microsoft-365/security/defender-endpoint/respond-file-alerts)
- [EDR trybie blokowania](/microsoft-365/security/defender-endpoint/edr-in-block-mode)
- [Odpowiedź na żywo](/microsoft-365/security/defender-endpoint/live-response)
- [Zautomatyzowane badania i odpowiedzi (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations)
- [Ochrona przed naruszeniami](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection)

W zależności od serwera, na którym jest wnoszony, ujednolicone rozwiązanie instaluje Program antywirusowy Microsoft Defender i/lub czujnik EDR rozwiązania. W poniższej tabeli przedstawiono, jaki składnik jest zainstalowany i co jest domyślnie wbudowane.

|Wersja na serwerze|AV|EDR|
|----|----|----|
|Windows Server 2012 R2 z dodatkiem SP1|![Tak.](images/svg/check-yes.svg)|![Tak.](images/svg/check-yes.svg)|
|System Windows Server 2016|Wbudowane|![Tak.](images/svg/check-yes.svg)|
|Windows Server 2019 lub nowszy|Wbudowane|Wbudowane|

Jeśli serwery były wcześniej wnoszone za pomocą usługi MMA, postępuj zgodnie ze wskazówkami w tece Migracja serwera, aby przeprowadzić migrację do nowego rozwiązania.[](server-migration.md)

>[!NOTE]
>Podczas gdy ta metoda dołączania do Windows Server 2012 R2 i Windows Server 2016 jest w wersji preview, możesz wybrać, czy chcesz nadal używać poprzedniej metody dołączania przy użyciu Microsoft Monitoring Agent (MMA). Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie punktów końcowych przy użyciu usługi MMA](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma).

#### <a name="known-issues-and-limitations-on-the-new-unified-solution-package-for-windows-server-2012-r2-and-2016"></a>Znane problemy i ograniczenia nowego, ujednoliconego pakietu rozwiązań dla nowych Windows Server 2012 R2 i 2016

Następujące informacje szczegółowe dotyczą nowego pakietu rozwiązań ujednoliconych dla pakietów Windows Server 2012 R2 i 2016:

- Upewnij się, że są spełnione wymagania dotyczące łączności określone w punkcie Umożliwianie dostępu do usługi Microsoft Defender dla adresów URL usługi punktu końcowego [na serwerze proxy](/microsoft-365/security/defender-endpoint/configure-proxy-internet?enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) . Są one równoważne tym, które są Windows Server 2019. 
- Pracujemy nad badaniem problemu z łącznością serwera Windows Server 2012 R2 z chmurą, gdy jest używany statyczny serwer telemetryczny telemetryczny, a adresy URL odwołań certyfikatów (CRL) nie są osiągalne z poziomu kontekstu konta systemowego. Natychmiastowym ograniczeniem jest użycie alternatywnej opcji serwera proxy, która zapewnia taką łączność, lub skonfigurowanie tego samego serwera proxy za pośrednictwem ustawienia WinInet w kontekście konta SYSTEMowego.
- Wcześniej korzystanie z programu Microsoft Monitoring Agent (MMA) w programie Windows Server 2016 i innych dozwolonych dla bramy OMS / Log Analytics do świadczenia łączności z usługami w chmurze Defender. Nowe rozwiązanie, takie jak program Microsoft Defender for Endpoint w systemach Windows Server 2019, Windows Server 2022 i Windows 10, nie obsługuje tej bramy.

- Na Windows Server 2016 upewnij się, że Program antywirusowy Microsoft Defender zainstalowany, jest aktywny i aktualny. Najnowszą wersję platformy można pobrać i zainstalować przy użyciu usługi Windows Update. Możesz również ręcznie pobrać pakiet aktualizacji z wykazu [usługi Microsoft Update lub](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) [z usługi MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).  
- W Windows Server 2012 R2 nie ma interfejsu użytkownika dla Program antywirusowy Microsoft Defender. Ponadto interfejs użytkownika na platformie Windows Server 2016 umożliwia tylko podstawowe operacje. Aby wykonać operacje na urządzeniu lokalnie, zobacz Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą programu [PowerShell, usługi WMI i MPCmdRun.exe](/microsoft-365/security/defender-endpoint/manage-mde-post-migration-other-tools). W wyniku tego funkcje, które w szczególności są zależne od interakcji użytkownika, takie jak miejsce, w którym użytkownik jest monitowany o podjęcie decyzji lub wykonanie określonego zadania, mogą nie działać zgodnie z oczekiwaniami. Zalecane jest wyłączenie lub wyłączenie interfejsu użytkownika ani nie wymaganie interakcji użytkownika na dowolnym serwerze zarządzanym, ponieważ może to wpłynąć na funkcję ochrony.
- Nie wszystkie reguły zmniejszania powierzchni ataków są dostępne dla wszystkich systemów operacyjnych. Zobacz [Reguły ograniczania powierzchni ataków (ASR](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)).
- Aby [włączyć ochronę sieci](/microsoft-365/security/defender-endpoint/network-protection), wymagana jest dodatkowa konfiguracja:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

  Ponadto na komputerach o dużej ilości ruchu sieciowego zdecydowanie zalecane jest testowanie wydajności w Środowisku przed włączeniem tej funkcji. Może być konieczne uwzględnianie dodatkowego zużycia zasobów.
- W Windows Server 2012 R2 zdarzenia sieciowe mogą nie zostać wypełnione osią czasu. Ten problem wymaga aktualizacji Windows wydanej w ramach [comiesięcznego wydania z 12 października 2021 r. (KB5006714)](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e).
- Uaktualnienia systemu operacyjnego nie są obsługiwane. Przed uaktualnieniem odinstaluj aplikację Offboard.
- Automatyczne wykluczenia *dla ról serwera* nie są obsługiwane na Windows Server 2012 R2, jednak wbudowane wykluczenia dotyczące plików systemu operacyjnego są takie. Aby uzyskać więcej informacji na temat dodawania wykluczeń, zobacz Zalecenia dotyczące skanowania wirusów [dla Enterprise komputerów z](https://support.microsoft.com/topic/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows-kb822158-c067a732-f24a-9079-d240-3733e39b40bc) obecnie obsługiwanymi wersjami Windows.
- Jeśli zdecydujesz się na wynosz i odinstalujesz nowoczesne, ujednolicone rozwiązanie i ponownie włożysz poprzedni czujnik EDR MMA, `MsSenseS.exe` mogą wystąpić powtarzające się awarie. 

Aby obejść ten problem, usuń następujące klucze rejestru, jeśli istnieją:
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security\fdedb2b8-61e4-4a7e-8b15-abf214a08fcc`
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security\c60418cc-7e07-400f-ae3b-d521c5dbd96f`

Można używać następujących poleceń:

```cmd
reg delete HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security /v fdedb2b8-61e4-4a7e-8b15-abf214a08fcc /f
reg delete HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security /v c60418cc-7e07-400f-ae3b-d521c5dbd96f /f
```
Ponowne uruchomienie nie jest wymagane.


<a name="integration-with-azure-defender"></a>

## <a name="integration-with-microsoft-defender-for-cloud"></a>Integracja z usługą Microsoft Defender dla chmury

Program Microsoft Defender for Endpoint bezproblemowo integruje się z programem Microsoft Defender dla chmury. Możesz automatycznie włączać serwery, monitorować je przez usługę Azure Defender w programie Defender for Endpoint i przeprowadzać szczegółowe badania jako klient usługi Microsoft Defender dla chmury.

Aby uzyskać więcej informacji, zobacz [Integracja z programem Microsoft Defender dla chmury](azure-server-integration.md).

> [!NOTE]
> W Windows Server 2012 R2 i 2016 z systemem nowoczesnego, ujednoliconego rozwiązania w wersji Zapoznawczej integracja z usługą Microsoft Defender dla chmury/ programem Microsoft Defender dla serwerów w celu alertowania i automatycznego wdrażania nie jest jeszcze dostępna. Mimo że możesz ręcznie zainstalować nowe rozwiązanie na tych komputerach, w programie Microsoft Defender dla chmury nie będą wyświetlane alerty.

> [!NOTE]
> - Integracja między programem Microsoft Defender dla serwerów i programem Microsoft Defender for Endpoint została rozwinięta w celu obsługi programu Windows Server 2022, [Windows Server 2019 i Windows Virtual Desktop (WVD)](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview) .
> - Monitorowanie punktu końcowego serwera korzystające z tej integracji zostało wyłączone dla Office 365 GCC klientów.

## <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 i Windows Server 2016

> [!NOTE]
> Podczas gdy ta metoda dołączania do Windows Server 2012 R2 i Windows Server 2016 jest w wersji preview, możesz wybrać, czy chcesz nadal używać poprzedniej metody dołączania przy użyciu Microsoft Monitoring Agent (MMA). Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie punktów końcowych przy użyciu usługi MMA](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma).

### <a name="prerequisites"></a>Wymagania wstępne

**Wymagania wstępne dotyczące Windows Server 2012 R2**

Jeśli Twoje komputery zostały w pełni zaktualizowane za pomocą najnowszego miesięcznego pakietu zb. pakietu zb. **nie ma żadnych** dodatkowych wymagań wstępnych.[](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e)

Pakiet instalatora sprawdzi, czy następujące składniki zostały już zainstalowane za pośrednictwem aktualizacji:

- [Aktualizacja do obsługi klienta i telemetrii diagnostycznej](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [Aktualizacja uniwersalnego środowiska C Runtime w Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

**Wymagania wstępne dotyczące Windows Server 2016** 

Poza pełną aktualizacją komputera za pomocą najnowszej aktualizacji skumulowanej (LCU), upewnij się, Program antywirusowy Microsoft Defender jest zainstalowana, jest aktywna i zaktualizowana. Najnowszą wersję platformy można pobrać i zainstalować przy użyciu usługi Windows Update. Możesz również ręcznie pobrać pakiet aktualizacji z wykazu [usługi Microsoft Update lub](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) [z usługi MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64). 

> [!NOTE]
> Aby pomyślnie zaktualizować wbudowaną wersję programu Windows Defender, której numer wersji zaczyna się od wersji 4.10, do najnowszej dostępnej platformy, należy zastosować aktualizację stosu obsługi, a także najnowszą aktualizację skumulowaną (LCU) równą lub późniejszą niż 20 września 2018 r. — KB4457127 (kompilacja systemu operacyjnego 14393.2515).

**Wymagania wstępne dotyczące uruchamiania z rozwiązaniami zabezpieczeń innych firm**

Jeśli zamierzasz używać rozwiązania ochrony przed złośliwym oprogramowaniem innej firmy, musisz uruchomić Program antywirusowy Microsoft Defender w trybie pasywnym. Należy pamiętać o ustawianiu trybu pasywnego podczas instalacji i procesu dołączania.

**Nowy pakiet aktualizacji programu Microsoft Defender dla punktu końcowego w systemach Windows Server 2012 R2 i 2016**

Aby otrzymywać regularne ulepszenia i poprawki dotyczące składnika czujnika EDR, upewnij się, Windows, że jest stosowana lub zatwierdzona aktualizacja [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277). Aby dodatkowo aktualizować składniki ochrony, zobacz Zarządzanie [Program antywirusowy Microsoft Defender i stosowanie linii bazowych](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

### <a name="onboarding-steps-summary"></a>Podsumowanie kroków dołączania

- KROK 1. [Pobieranie pakietów instalacyjnych i pakietów dołączania](#step-1-download-installation-and-onboarding-packages)
- KROK 2. [Stosowanie pakietu instalacyjnego i dołączania](#step-2-apply-the-installation-and-onboarding-package)
- KROK 3. [Wykonaj kroki dotyczące dołączania](#step-3-complete-the-onboarding-steps) 


### <a name="step-1-download-installation-and-onboarding-packages"></a>KROK 1. Pobieranie pakietów instalacyjnych i pakietów dołączania

Musisz pobrać z portalu zarówno pakiety instalacyjne **,** jak  i pakiety dołączania.

> [!div class="mx-imgBorder"]
> ![Obraz pulpitu nawigacyjnego dołączania](images/install-agent-onboard.png)


   > [!NOTE]
   > Na Windows Server 2012R2 pakiet instalacyjny zostanie Program antywirusowy Microsoft Defender zainstalowany i będzie aktywny, o ile nie ustawiono trybu pasywnego. Na Windows Server 2016 musisz Program antywirusowy Microsoft Defender jako funkcję (zobacz Przełączanie do [usługi MDE](/microsoft-365/security/defender-endpoint/switch-to-mde-phase-2#re-enable-microsoft-defender-antivirus-on-windows-server-2016)) przed przejściem do instalacji w pełni zaktualizowany (zobacz Przełączanie do usługi MDE).
   > 
   > Jeśli używasz rozwiązania ochrony przed złośliwym oprogramowaniem firmy microsoft, przed rozpoczęciem instalacji dodaj wykluczenia dla programu Program antywirusowy Microsoft Defender (z tej listy procesów programu [Microsoft Defender](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) na karcie Procesy programu Defender) do rozwiązania firmy innych niż Microsoft.  Zalecane jest również dodanie rozwiązań zabezpieczeń innych niż firmy Microsoft do listy wykluczeń programu antywirusowego Defender.


Pakiet **instalacyjny zawiera** plik MSI, który instaluje agenta programu Microsoft Defender for Endpoint.

Pakiet **dołączający zawiera** następujące pliki:

- `OptionalParamsPolicy` — zawiera ustawienie umożliwiające zbieranie przykładowych
- `WindowsDefenderATPOnboardingScript.cmd` — zawiera skrypt dołączania

Aby pobrać pakiety, należy wykonać następujące czynności: 

1. W Microsoft 365 Defender przejdź do Ustawienia > **Zarządzanie urządzeniami > dołączanie**.

2. Wybierz **Windows Server 2012 R2 i 2016**.

3. Wybierz **pozycję Pobierz pakiet instalacyjny** i zapisz .msi pliku. 
 
4. Wybierz **pozycję Pobierz pakiet dołączający** i zapisz .zip pliku.

5. Zainstaluj pakiet instalacyjny przy użyciu dowolnej z opcji instalowania pakietu Program antywirusowy Microsoft Defender. Instalacja wymaga uprawnień administracyjnych.



### <a name="step-2-apply-the-installation-and-onboarding-package"></a>KROK 2. Stosowanie pakietu instalacyjnego i dołączania
W tym kroku zainstalujesz składniki zapobiegania i wykrywania wymagane przed dodaniem urządzenia do środowiska chmury programu Microsoft Defender for Endpoint, aby przygotować komputer doinstalowania. Upewnij się [, że zostały spełnione](#prerequisites) wszystkie wymagania wstępne. 

   > [!NOTE]
   > Program antywirusowy Microsoft Defender zainstalowany i będzie aktywny, jeśli nie ustawiono trybu pasywnego. 

#### <a name="options-to-install-the-microsoft-defender-for-endpoint-packages"></a>Opcje instalowania pakietów programu Microsoft Defender for Endpoint

W poprzedniej sekcji pobrano pakiet instalacyjny. Pakiet instalacyjny zawiera instalatora wszystkich składników programu Microsoft Defender for Endpoint. 

Aby zainstalować agenta, możesz użyć dowolnej z następujących opcji:
- [Instalowanie przy użyciu wiersza polecenia](#install-microsoft-defender-for-endpoint-using-the-command-line)
- [Instalowanie przy użyciu skryptu](#install-microsoft-defender-for-endpoint-using-a-script)
- [Stosowanie pakietów instalacyjnych i pakietów dołączania przy użyciu zasady grupy](#apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy)

##### <a name="install-microsoft-defender-for-endpoint-using-the-command-line"></a>Instalowanie programu Microsoft Defender For Endpoint przy użyciu wiersza polecenia
Użyj pakietu instalacyjnego z poprzedniego kroku, aby zainstalować program Microsoft Defender for Endpoint. 


Uruchom następujące polecenie, aby zainstalować program Microsoft Defender dla punktu końcowego:

```console
Msiexec /i md4ws.msi /quiet
```

Aby odinstalować, upewnij się, że komputer został wyłączony, używając odpowiedniego skryptu wynoszania. Następnie wykonaj odinstalowanie za pomocą programów \> i funkcji w Panelu \> sterowania Programy i funkcje.

Ewentualnie uruchom następujące polecenie odinstalowywania, aby odinstalować program Microsoft Defender for Endpoint:

```console
Msiexec /x md4ws.msi /quiet
```

Aby instalacja powyższego polecenia powiodła się, należy użyć tego samego pakietu, który został użyty do instalacji.

Przełącznik `/quiet` pominie wszystkie powiadomienia.

> [!NOTE]
> Program antywirusowy Microsoft Defender nie włącza automatycznie trybu pasywnego. Jeśli używasz rozwiązania antywirusowego/ochrony przed złośliwym oprogramowaniem firmy Microsoft, możesz skonfigurować go Program antywirusowy Microsoft Defender w trybie pasywnym. W przypadku instalacji wiersza polecenia opcjonalne pole `FORCEPASSIVEMODE=1` wyboru natychmiast ustawia dla składnika Program antywirusowy Microsoft Defender tryb pasywny, aby uniknąć zakłócenia. Następnie, aby zapewnić, że program antywirusowy Defender pozostaje w trybie pasywnym po dojściu do obsługi funkcji, takich jak blokowanie usługi EDR, ustaw klucz rejestru "ForceDefenderPassiveMode".

Obsługa serwera Windows zapewnia bardziej szczegółowe informacje o działaniach serwera, zasięgu wykrywania ataku kernelu i pamięci oraz umożliwia akcje odpowiedzi.

##### <a name="install-microsoft-defender-for-endpoint-using-a-script"></a>Instalowanie programu Microsoft Defender dla punktu końcowego przy użyciu skryptu

Za pomocą skryptu [instalatora można](server-migration.md#installer-script) zautomatyzować instalację, dezinstalację i dołączanie. Aby uzyskać więcej informacji, zapoznaj się z instrukcjami w poniższej sekcji dotyczącymi używania skryptu w zasady grupy.

##### <a name="apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy"></a>Stosowanie pakietów instalacji i dołączania programu Microsoft Defender dla punktów końcowych przy użyciu zasad grupy

1. Tworzenie zasad grupy: <br> Otwórz [konsolę zasady grupy zarządzania](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), kliknij prawym przyciskiem **myszy zasady grupy obiekty,** które chcesz skonfigurować, a następnie kliknij pozycję **Nowy**. Wprowadź nazwę nowego serwera zasad grupy w wyświetlonym oknie dialogowym i kliknij przycisk **OK**.

2. Otwórz [konsolę zasady grupy zarządzania](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), kliknij prawym przyciskiem myszy obiekt zasady grupy obiekt (GPO), który chcesz skonfigurować, a następnie kliknij polecenie **Edytuj**.

3. W **edytorze zasady grupy zarządzaniem** przejdź do opcji Konfiguracja **komputera,** Preferencje **, a** następnie **Ustawienia Panelu sterowania**.

4. Kliknij prawym przyciskiem **myszy pozycję Zaplanowane zadania**, wskaż pozycję **Nowe**, a następnie kliknij pozycję **Zadanie natychmiastowe (co najmniej Windows 7).**

5. W **oknie** Zadanie, które zostanie otwarte, przejdź do **karty** Ogólne. W **obszarze Opcje zabezpieczeń** kliknij **pozycję Zmień użytkownika lub grupę** i wpisz SYSTEM, a następnie kliknij pozycję **Sprawdź nazwy** , a następnie kliknij **przycisk OK**. Nt AUTHORITY\SYSTEM pojawi się jako konto użytkownika, jako które będzie działać zadanie.

6. Zaznacz **pole wyboru Uruchom** niezależnie od tego, czy użytkownik jest zalogowany, i zaznacz **pole wyboru Uruchom z najwyższymi uprawnieniami** .

7. W polu Nazwa wpisz odpowiednią nazwę dla zaplanowanego zadania (na przykład Defender do wdrożenia punktu końcowego).

8. Przejdź do karty **Akcje** i wybierz pozycję **Nowy...** Upewnij się **, że w** polu Akcja jest wybrana opcja **Uruchom program.** Skrypt [instalatora obsługuje](server-migration.md#installer-script) instalację i natychmiast wykonuje kroki dołączania po zakończeniu instalacji. Wybierz *C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe* a następnie podaj argumenty:

    ```console
     -ExecutionPolicy RemoteSigned \\servername-or-dfs-space\share-name\install.ps1 -OnboardingScript \\servername-or-dfs-space\share-name\windowsdefenderatponboardingscript.cmd
    ```  

     >[!NOTE]
    >Zalecane ustawienie zasad wykonywania to `Allsigned`. Wymaga to zaimportowania certyfikatu podpisywania skryptu do magazynu zaufani wydawcy na komputerze lokalnym, jeśli skrypt jest uruchomiony jako SYSTEM w punkcie końcowym.

    Zastąp \\nazwę serwera -lub-dfs-space\share-name ścieżką UNC, używając w pełni kwalifikowanej nazwy domeny (FQDN) serwera plików udostępnionych w *install.ps1pliku.* Pakiet instalatora md4ws.msi musi znajdować się w tym samym katalogu.  Upewnij się również, że uprawnienia ścieżki UNC umożliwiają dostęp do odczytu konta komputera, które instaluje platformę.

   

    W scenariuszach, w Program antywirusowy Microsoft Defender z rozwiązaniami innych niż firmy Microsoft w celu ochrony przed złośliwym oprogramowaniem, dodaj parametr $Passive, aby ustawić tryb pasywny podczas instalacji.

9. Wybierz **przycisk OK** i zamknij wszystkie otwarte okna GPMC.

10. Aby połączyć element zasad grupy z jednostką jednostki organizacyjnej, kliknij prawym przyciskiem myszy i wybierz polecenie **Połącz istniejący element zasad grupy**. W wyświetlonym oknie dialogowym wybierz obiekt, zasady grupy, który chcesz połączyć. Kliknij przycisk **OK**.

Aby uzyskać dodatkowe ustawienia konfiguracji, zobacz [Konfigurowanie przykładowych ustawień kolekcji i](configure-endpoints-gp.md#configure-sample-collection-settings) [Inne zalecane ustawienia konfiguracji](configure-endpoints-gp.md#other-recommended-configuration-settings).

### <a name="step-3-complete-the-onboarding-steps"></a>KROK 3. Wykonaj kroki dotyczące dołączania

Poniższe kroki mają zastosowanie tylko w przypadku korzystania z rozwiązania innej firmy chroniącego przed złośliwym oprogramowaniem. Należy zastosować następujące ustawienie trybu Program antywirusowy Microsoft Defender pasywnego. Sprawdź, czy konfiguracja została prawidłowo skonfigurowana:

1. Ustaw następujący wpis rejestru:
    - Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
    - Nazwa: `ForceDefenderPassiveMode`
    - Typ: `REG_DWORD`
    - Wartość: `1`

2. Uruchom następujące polecenie programu PowerShell, aby sprawdzić, czy tryb pasywny został skonfigurowany:

    ```powershell
    Get-WinEvent -FilterHashtable @{ProviderName="Microsoft-Windows-Sense" ;ID=84}
    ```

3. Upewnij się, że odnaleziono ostatnie zdarzenie zawierające zdarzenie pasywne:

    ![Obraz wyniku weryfikacji w trybie pasywnym](images/atp-verify-passive-mode.png)

> [!IMPORTANT]
>
> - Podczas monitorowania serwerów za pomocą programu Microsoft Defender for Cloud jest automatycznie tworzona dzierżawa usługi Defender dla punktu końcowego (w Stanach Zjednoczonych dla użytkowników w Stanach Zjednoczonych, w Unii Europejskiej dla użytkowników w Unii Europejskiej i w Wielkiej Brytanii dla użytkowników Ze Zjednoczonego Królestwa).
Dane zbierane przez usługę Defender for Endpoint są przechowywane w lokalizacji geograficznej dzierżawy zidentyfikowana podczas inicjowania obsługi administracyjnej.
> - Jeśli używasz usługi Defender for Endpoint przed użyciem programu Microsoft Defender dla chmury, Twoje dane będą przechowywane w lokalizacji określonej podczas tworzenia dzierżawy, nawet jeśli w późniejszym czasie zintegrowasz ją z programem Microsoft Defender dla chmury.
> - Po skonfigurowaniu tej konfiguracji nie można zmienić lokalizacji przechowywania danych. Jeśli chcesz przenieść dane do innej lokalizacji, skontaktuj się z pomocą techniczną firmy Microsoft, aby zresetować dzierżawę.
> - Pakiet onboardingowy dla Windows Server 2019 i Windows Server 2022–Microsoft Endpoint Manager obecnie wysyła skrypt. Aby uzyskać więcej informacji na temat wdrażania skryptów w programie Menedżer konfiguracji, zobacz Pakiety [i programy w Menedżer konfiguracji](/configmgr/apps/deploy-use/packages-and-programs).
> - Skrypt lokalny nadaje się do dowodu koncepcji, ale nie powinien być używany do wdrożenia produkcyjnego. W przypadku wdrożenia produkcyjnego zalecamy używanie aplikacji zasady grupy lub Microsoft Endpoint Configuration Manager.



## <a name="windows-server-semi-annual-enterprise-channel-and-windows-server-2019-and-windows-server-2022"></a>Windows Server Semi-Annual Enterprise Channel and Windows Server 2019 oraz Windows Server 2022

Pakiet dołączający do programu Windows Server 2019 i Windows Server 2022 do Microsoft Endpoint Manager obecnie wysyła skrypt. Aby uzyskać więcej informacji na temat wdrażania skryptów w programie Menedżer konfiguracji, zobacz Pakiety [i programy w Menedżer konfiguracji](/configmgr/apps/deploy-use/packages-and-programs).

### <a name="download-package"></a>Pobierz pakiet

1. W Microsoft 365 Defender przejdź do Ustawienia > **Zarządzanie urządzeniami > dołączanie**.

2. Wybierz **Windows Server 1803 i 2019**.

3. Wybierz **pozycję Pobierz pakiet**. Zapisz jako WindowsDefenderATPOnboardingPackage.zip.

4. Postępuj zgodnie z instrukcjami w [sekcji Wykonaj kroki dołączania](#step-3-complete-the-onboarding-steps) .


## <a name="verify-the-onboarding-and-installation"></a>Weryfikowanie procesu dołączania i instalowania

Sprawdź, czy Program antywirusowy Microsoft Defender i Program Microsoft Defender for Endpoint są uruchomione.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Uruchamianie testu wykrywania w celu zweryfikowania do uruchomienia

Po włoceniu urządzenia możesz uruchomić test wykrywania w celu sprawdzenia, czy urządzenie jest prawidłowo podłączone do usługi. Aby uzyskać więcej informacji, zobacz Uruchamianie testu wykrywania na nowo włodarzony [program Microsoft Defender dla urządzenia końcowego](run-detection-test.md).

> [!NOTE]
> Uruchamianie Program antywirusowy Microsoft Defender nie jest wymagane, ale jest zalecane. Jeśli głównym rozwiązaniem ochrony punktu końcowego jest inny produkt dostawcy oprogramowania antywirusowego, możesz uruchomić program antywirusowy Defender w trybie pasywnym. Można sprawdzić, czy tryb pasywny jest uruchomiony tylko po sprawdzeniu, czy czujnik programu Microsoft Defender for Endpoint (SENSE) jest uruchomiony.

1. Uruchom następujące polecenie, aby sprawdzić, czy Program antywirusowy Microsoft Defender zainstalowano oprogramowanie:

    >[!NOTE]
    >Ten krok zawrót głowy jest wymagany tylko w przypadku Program antywirusowy Microsoft Defender jako aktywnego rozwiązania zapobiegającego złośliwym oprogramowaniem.

    `sc.exe query Windefend`


    Jeśli wynikiem jest błąd "Określona usługa nie istnieje jako zainstalowana usługa", musisz zainstalować usługę w Program antywirusowy Microsoft Defender. 


    Aby uzyskać informacje na temat konfigurowania zasady grupy sieci Program antywirusowy Microsoft Defender na serwerach Windows i zarządzania nimi, zobacz Konfigurowanie i zarządzanie usługą zasady grupy przy użyciu [ustawień Program antywirusowy Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md).

2. Uruchom następujące polecenie, aby sprawdzić, czy usługa Microsoft Defender dla punktu końcowego jest uruchomiona:

    `sc.exe query sense`

    Wynik powinien być pokazywany, że jest uruchomiony. Jeśli wystąpią problemy z dołączaniem, zobacz [Rozwiązywanie problemów z dołączaniem](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Uruchamianie testu wykrywania

Postępuj zgodnie z instrukcjami w teście uruchamiania wykrywania na nowo [wnosiowym](run-detection-test.md) urządzeniu, aby sprawdzić, czy serwer raportuje usługę Defender dla punktu końcowego.

## <a name="next-steps"></a>Następne kroki

Po pomyślnym doniu urządzeń do usługi konieczne będzie skonfigurowanie poszczególnych składników programu Microsoft Defender dla punktu końcowego. Postępuj zgodnie z [porządek](prepare-deployment.md#adoption-order) przyjęcia, aby zostać przewodnikiem po włączaniu poszczególnych składników.

## <a name="offboard-windows-servers"></a>Odsuń Windows serwerach

Wersje Windows Server 2012 R2, Windows Server 2016, Windows Server (KW), Windows Server 2019 i Windows Server 2019 Core można wystartować w taki sam sposób, jak w przypadku urządzeń klienckich firmy Windows 10.

- [Urządzenia wye korzystające z zasady grupy](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Urządzenia wye korzystające z Menedżer konfiguracji](configure-endpoints-sccm.md#offboard-devices-using-configuration-manager)
- [Urządzenia wyełowywne i monitorują je przy użyciu narzędzi do zarządzania urządzeniami przenośnymi](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)
- [Urządzenia wye korzystające ze skryptu lokalnego](configure-endpoints-script.md#offboard-devices-using-a-local-script)

W przypadku Windows wersji serwera dostępne są dwie opcje Windows z usługi:

- Odinstalowywanie agenta MMA
- Usuwanie konfiguracji obszaru roboczego programu Defender for Endpoint

>[!NOTE]
>*Poniższe instrukcje dotyczące wywrzeniania na inne Windows serwera mają zastosowanie również w przypadku, gdy używasz poprzedniej wersji programu Microsoft Defender for Endpoint dla systemu Windows Server 2016 i Windows Server 2012 R2, która wymaga programu MMA. Instrukcje migrowania do nowego nieprawionego rozwiązania znajdują się w scenariuszach migracji z serwera [w programie Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>Tematy pokrewne

- [Wniesienie poprzednich wersji Windows](onboard-downlevel.md)
- [Urządzenia Windows 10 urządzeniach](configure-endpoints.md)
- [Urządzenia Windows urządzeniach](configure-endpoints-non-windows.md)
- [Konfigurowanie ustawień serwera proxy i łączności internetowej](configure-proxy-internet.md)
- [Uruchamianie testu wykrywania na nowo w urządzeniu z uruchomionym programem Defender dla punktu końcowego](run-detection-test.md)
- [Rozwiązywanie problemów z dołączaniem do programu Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
