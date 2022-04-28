---
title: Dołączanie serwerów Windows do usługi Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dołącz serwery Windows, aby mogły wysyłać dane czujnika do czujnika Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: dołączanie serwera, serwera, 2012r2, 2016, 2019, dołączanie serwera, zarządzanie urządzeniami, konfigurowanie serwerów Ochrona punktu końcowego w usłudze Microsoft Defender, dołączanie serwerów Ochrona punktu końcowego w usłudze Microsoft Defender, dołączanie serwery Ochrona punktu końcowego w usłudze Microsoft Defender
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
ms.openlocfilehash: 14ec731eebe21f6b399e03d445fef248b8675026
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098763"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>Dołączanie serwerów Windows do usługi Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- Windows Server 2012 R2
- System Windows Server 2016
- Kanał Semi-Annual Enterprise serwera Windows
- Windows Server 2019 i nowsze
- wersja podstawowa Windows Server 2019
- Windows Server 2022
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configserver-abovefoldlink)

Usługa Defender for Endpoint rozszerza obsługę o system operacyjny Windows Server. Ta obsługa zapewnia zaawansowane funkcje wykrywania i badania ataków bezproblemowo za pośrednictwem konsoli Microsoft 365 Defender. Obsługa serwera Windows zapewnia dokładniejszy wgląd w działania serwera, pokrycie wykrywania ataków jądra i pamięci oraz włącza akcje reagowania.

W tym temacie opisano sposób dołączania określonych serwerów Windows do Ochrona punktu końcowego w usłudze Microsoft Defender.

Aby uzyskać wskazówki dotyczące pobierania i używania Zabezpieczenia Windows planów bazowych dla serwerów Windows, zobacz [Zabezpieczenia Windows Baselines (Punkty odniesienia Zabezpieczenia Windows](/windows/device-security/windows-security-baselines)).

## <a name="windows-server-onboarding-overview"></a>Omówienie dołączania serwera Windows

Aby pomyślnie dołączyć serwery, należy wykonać następujące ogólne kroki.

:::image type="content" source="images/server-onboarding-tools-methods.png" alt-text="Ilustracja przedstawiająca przepływ dołączania dla serwerów Windows i urządzeń Windows 10" lightbox="images/server-onboarding-tools-methods.png":::

**Windows Server 2012 R2 i Windows Server 2016**

- Pobieranie pakietów instalacyjnych i dołączanych
- Stosowanie pakietu instalacyjnego
- Wykonaj kroki dołączania odpowiedniego narzędzia

**Windows Server Semi-Annual Enterprise Channel i Windows Server 2019**

- Pobieranie pakietu dołączania
- Wykonaj kroki dołączania odpowiedniego narzędzia

>[!IMPORTANT]
>Aby kwalifikować się do zakupu jednostki SKU serwera Ochrona punktu końcowego w usłudze Microsoft Defender, musisz już kupić łączne minimum spośród następujących, Windows E5/A5, Microsoft 365 E5/A5 lub Zabezpieczenia platformy Microsoft 365 E5 licencji subskrypcji.  Aby uzyskać więcej informacji na temat licencjonowania, zobacz [Warunki produktu](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  



### <a name="new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution"></a>Nowe funkcje Windows Server 2012 R2 i 2016 w nowoczesnym ujednoliconym rozwiązaniu

Poprzednia implementacja dołączania Windows Server 2012 R2 i Windows Server 2016 wymagała użycia Microsoft Monitoring Agent (MMA).

Nowy ujednolicony pakiet rozwiązań ułatwia dołączanie serwerów przez usunięcie zależności i kroków instalacji. Ponadto ten ujednolicony pakiet rozwiązań zawiera następujące istotne ulepszenia:

- [Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) z [ochroną nowej generacji](/microsoft-365/security/defender-endpoint/next-generation-protection) dla Windows Server 2012 R2
- [Reguły zmniejszania obszaru ataków (ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- [Ochrona sieci](/microsoft-365/security/defender-endpoint/network-protection)
- [Kontrolowany dostęp do folderów](/microsoft-365/security/defender-endpoint/controlled-folders)
- [Blokowanie potencjalnie niechcianej aplikacji (PUA)](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Ulepszone możliwości wykrywania](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
- [Rozszerzone możliwości reagowania](/microsoft-365/security/defender-endpoint/respond-machine-alerts) na urządzeniach i [plikach](/microsoft-365/security/defender-endpoint/respond-file-alerts)
- [EDR w trybie bloku](/microsoft-365/security/defender-endpoint/edr-in-block-mode)
- [Odpowiedź na żywo](/microsoft-365/security/defender-endpoint/live-response)
- [Zautomatyzowane badanie i reagowanie (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations)
- [Ochrona przed naruszeniami](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection)

W zależności od serwera, który dołączasz, ujednolicone rozwiązanie instaluje Program antywirusowy Microsoft Defender i/lub czujnik EDR. Poniższa tabela wskazuje, który składnik jest zainstalowany i co jest wbudowane domyślnie.

|Wersja serwera|AV|EDR|
|----|----|----|
|Windows Server 2012 R2 SP1|![Tak.](images/svg/check-yes.svg)|![Tak.](images/svg/check-yes.svg)|
|System Windows Server 2016|Wbudowane|![Tak.](images/svg/check-yes.svg)|
|Windows Server 2019 lub nowszy|Wbudowane|Wbudowane|

Jeśli serwery zostały wcześniej dołączone przy użyciu programu MMA, postępuj zgodnie ze wskazówkami podanymi w temacie [Migracja serwera](server-migration.md) , aby przeprowadzić migrację do nowego rozwiązania.

#### <a name="known-issues-and-limitations-in-the-new-unified-solution-package-for-windows-server-2012-r2-and-2016"></a>Znane problemy i ograniczenia w nowym, ujednoliconym pakiecie rozwiązań dla Windows Server 2012 R2 i 2016

Następujące szczegółowe informacje dotyczą nowego ujednoliconego pakietu rozwiązań dla Windows Server 2012 R2 i 2016:

- Upewnij się, że są spełnione wymagania dotyczące łączności określone w temacie [Włączanie dostępu do adresów URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender na serwerze proxy](/microsoft-365/security/defender-endpoint/configure-proxy-internet?enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Są one równoważne tym dla programu Windows Server 2019. 
- Zidentyfikowaliśmy problem z łącznością Windows Server 2012 R2 z chmurą, gdy jest używany statyczny serwer TelemetryProxyServer **, a** adresy URL listy odwołania certyfikatów (CRL) nie są osiągalne z kontekstu konta SYSTEMU. Natychmiastowe ograniczenie ryzyka polega na użyciu alternatywnej opcji serwera proxy ("ogólnosystemowej"), która zapewnia taką łączność, lub skonfigurowaniu tego samego serwera proxy za pośrednictwem ustawienia WinInet w kontekście konta SYSTEMU.
Alternatywnie użyj instrukcji podanych w artykule [Obejście znanego problemu z serwerem TelemetryProxyServer na odłączonych maszynach](#workaround-for-a-known-issue-with-telemetryproxyserver-on-disconnected-machines) , aby zainstalować certyfikat jako obejście.
- Wcześniej użycie Microsoft Monitoring Agent (MMA) na Windows Server 2016 i poniżej pozwoliło bramie OMS/Log Analytics zapewnić łączność z usługami w chmurze Defender. Nowe rozwiązanie, takie jak Ochrona punktu końcowego w usłudze Microsoft Defender na serwerze Windows Server 2019, Windows Server 2022 i Windows 10, nie obsługuje tej bramy.
- Na Windows Server 2016 sprawdź, czy Program antywirusowy Microsoft Defender jest zainstalowany, jest aktywny i aktualny. Najnowszą wersję platformy można pobrać i zainstalować przy użyciu Windows Update. Alternatywnie pobierz pakiet aktualizacji ręcznie z [katalogu microsoft update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) lub z [programu MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).  
- W Windows Server 2012 R2 nie ma interfejsu użytkownika dla Program antywirusowy Microsoft Defender. Ponadto interfejs użytkownika w Windows Server 2016 zezwala tylko na operacje podstawowe. Aby wykonywać operacje na urządzeniu lokalnie, zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu programu PowerShell, usługi WMI i MPCmdRun.exe](/microsoft-365/security/defender-endpoint/manage-mde-post-migration-other-tools). W związku z tym funkcje, które w szczególności polegają na interakcji użytkownika, takie jak monit o podjęcie decyzji lub wykonanie określonego zadania, mogą nie działać zgodnie z oczekiwaniami. Zaleca się wyłączenie lub niewłączenie interfejsu użytkownika ani wymaganie interakcji użytkownika na dowolnym zarządzanym serwerze, ponieważ może to mieć wpływ na możliwość ochrony.
- Nie wszystkie reguły zmniejszania obszaru podatnego na ataki są dostępne we wszystkich systemach operacyjnych. Zobacz [Reguły zmniejszania obszaru podatnego na ataki (ASR](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)).
- Aby włączyć [ochronę sieci](/microsoft-365/security/defender-endpoint/network-protection), wymagana jest dodatkowa konfiguracja:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

  Ponadto na maszynach o dużym natężeniu ruchu sieciowego zaleca się przeprowadzenie testów wydajnościowych w środowisku przed szerokim włączeniem tej możliwości. Może być konieczne uwzględnienie dodatkowego użycia zasobów.
- W Windows Server 2012 R2 zdarzenia sieciowe mogą nie być wypełniane na osi czasu. Ten problem wymaga wydania Windows Update w ramach [miesięcznego pakietu zbiorczego z 12 października 2021 r. (KB5006714).](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e)
- Uaktualnienia systemu operacyjnego nie są obsługiwane. Następnie odinstaluj przed uaktualnieniem.
- Automatyczne wykluczenia dla **ról serwera** nie są obsługiwane w Windows Server 2012 R2. Jednak wbudowane wykluczenia dla plików systemu operacyjnego są. Aby uzyskać więcej informacji na temat dodawania wykluczeń, zobacz [Zalecenia dotyczące skanowania wirusów dla Enterprise komputerów z aktualnie obsługiwanymi wersjami Windows](https://support.microsoft.com/topic/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows-kb822158-c067a732-f24a-9079-d240-3733e39b40bc).
- Na maszynach, które zostały uaktualnione z poprzedniego rozwiązania mma i czujnika EDR jest (wersja zapoznawcza) starsza niż 10.8047.22439.1056, odinstalowywanie i powrót do rozwiązania opartego na mma może prowadzić do awarii. Jeśli korzystasz z takiej wersji zapoznawczej, zaktualizuj je przy użyciu kb5005292.
- Aby wdrożyć i dołączyć nowe rozwiązanie przy użyciu Microsoft Endpoint Manager, obecnie wymaga to utworzenia pakietu. Aby uzyskać więcej informacji na temat wdrażania programów i skryptów w Configuration Manager, zobacz [Pakiety i programy w Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs). Program MECM 2107 z pakietem zbiorczym poprawek lub nowszym jest wymagany do obsługi zarządzania konfiguracją zasad przy użyciu węzła Endpoint Protection.

## <a name="workaround-for-a-known-issue-with-telemetryproxyserver-on-disconnected-machines"></a>Obejście znanego problemu z serwerem TelemetryProxyServer na odłączonych maszynach

Opis problemu: W przypadku używania ustawienia TelemetryProxyServer do określenia serwera proxy, który ma być używany przez składnik EDR Ochrona punktu końcowego w usłudze Microsoft Defender, na maszynach, które nie mają innego sposobu uzyskiwania dostępu do adresu URL listy odwołania certyfikatów (CRL), brak certyfikatu pośredniego spowoduje EDR  czujnika, aby nie nawiązać pomyślnego połączenia z usługą w chmurze.

Scenariusz, którego dotyczy problem: -Ochrona punktu końcowego w usłudze Microsoft Defender z wersją sense 10.8048.22439.1065 lub starszą wersją zapoznawczą uruchomioną w Windows Server 2012 R2 — przy użyciu konfiguracji serwera proxy TelemetryProxyServer; inne metody nie mają wpływu na

Obejście:
1. Upewnij się, że na maszynie działa sense w wersji 10.8048.22439.1065 lub nowszej, instalując przy użyciu najnowszego pakietu dostępnego na stronie dołączania lub stosując kb5005292.
2. Pobieranie i rozpakowywania certyfikatu https://github.com/microsoft/mdefordownlevelserver/blob/main/InterCA.zip
3. Zaimportuj certyfikat do zaufanego magazynu "Pośrednie urzędy certyfikacji" komputera lokalnego.
Możesz użyć polecenia programu PowerShell: Import-Certificate -FilePath .\InterCA.cer -CertStoreLocation Cert:\LocalMachine\Ca

## <a name="integration-with-microsoft-defender-for-cloud"></a>Integracja z Microsoft Defender dla Chmury

Ochrona punktu końcowego w usłudze Microsoft Defender bezproblemowo integruje się z Microsoft Defender dla Chmury. Serwery można dołączać automatycznie, serwery monitorowane przez usługę Azure Defender są wyświetlane w usłudze Defender for Endpoint i przeprowadzać szczegółowe badania jako klient Microsoft Defender dla Chmury.

Aby uzyskać więcej informacji, zobacz [Integracja z Microsoft Defender dla Chmury](azure-server-integration.md).

> [!NOTE]
> W przypadku Windows Server 2012 R2 i 2016 r. z uruchomionym nowoczesnym ujednoliconym rozwiązaniem integracja z Microsoft Defender dla Chmury /Microsoft Defender dla serwerów na potrzeby zautomatyzowanego wdrażania lub uaktualniania nie jest jeszcze dostępna dla wszystkich planów. Nowe rozwiązanie można zainstalować ręcznie na tych maszynach lub użyć usługi Microsoft Defender dla serwera P1, aby przetestować nowe rozwiązanie. Więcej informacji można znaleźć w [tematach New Defender for servers plans (Plany nowej usługi Defender dla serwerów](/azure/defender-for-cloud/release-notes#new-defender-for-servers-plans)).

> [!NOTE]
> - Integracja między usługą Microsoft Defender dla serwerów i Ochrona punktu końcowego w usłudze Microsoft Defender została rozszerzona o obsługę Windows Server 2022, [Windows Server 2019 i Windows Virtual Desktop (WVD)](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview).
> - Monitorowanie punktu końcowego serwera korzystające z tej integracji zostało wyłączone dla Office 365 GCC klientów.

## <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 i Windows Server 2016

### <a name="prerequisites"></a>Wymagania wstępne

**Wymagania wstępne dotyczące Windows Server 2012 R2**

Jeśli maszyny zostały w pełni zaktualizowane przy użyciu najnowszego [miesięcznego pakietu zbiorczego](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e) , **nie** ma żadnych dodatkowych wymagań wstępnych.

Pakiet instalatora sprawdzi, czy następujące składniki zostały już zainstalowane za pośrednictwem aktualizacji:

- [Aktualizacja środowiska klienta i danych telemetrycznych diagnostycznych](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [Aktualizacja środowiska uniwersalnego języka C w Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

**Wymagania wstępne dotyczące Windows Server 2016** 

- Należy zainstalować aktualizację stosu obsługi (SSU) z 14 września 2021 r. lub nowszą.  
- Należy zainstalować najnowszą aktualizację zbiorczą (LCU) z 20 września 2018 r. lub nowszą.  Zaleca się zainstalowanie najnowszej dostępnej jednostki SSU i LCU na serwerze.  — Funkcja Program antywirusowy Microsoft Defender musi być włączona/zainstalowana i aktualna. Najnowszą wersję platformy można pobrać i zainstalować przy użyciu Windows Update. Alternatywnie pobierz pakiet aktualizacji ręcznie z [katalogu microsoft update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) lub z [programu MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).

**Wymagania wstępne dotyczące uruchamiania z rozwiązaniami zabezpieczeń innych firm**

Jeśli zamierzasz używać rozwiązania chroniącego przed złośliwym kodem innej firmy, musisz uruchomić Program antywirusowy Microsoft Defender w trybie pasywnym. Należy pamiętać o ustawieniu trybu pasywnego podczas procesu instalacji i dołączania.

> [!NOTE]
> Jeśli instalujesz Ochrona punktu końcowego w usłudze Microsoft Defender na serwerach z programem McAfee Endpoint Security (ENS) lub VirusScan Enterprise (VSE), może być konieczne zaktualizowanie wersji platformy McAfee w celu zapewnienia, że Program antywirusowy Microsoft Defender nie jest usuwana ani wyłączana. Aby uzyskać więcej informacji, w tym wymagane numery wersji, zobacz [artykuł McAfee Knowledge Center](https://kc.mcafee.com/corporate/index?page=content&id=KB88214).

**Aktualizowanie pakietu dla Ochrona punktu końcowego w usłudze Microsoft Defender w Windows Server 2012 R2 i 2016**

Aby otrzymywać regularne ulepszenia i poprawki produktu dla składnika czujnika EDR, upewnij się, Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) zostanie zastosowana lub zatwierdzona. Ponadto aby aktualizować składniki ochrony, zobacz [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie punktów odniesienia](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).


Jeśli używasz Windows Server Update Services (WSUS) i/lub Microsoft Endpoint Configuration Manager, ta nowa "aktualizacja Ochrona punktu końcowego w usłudze Microsoft Defender dla EDR  Czujnik" jest dostępny w kategorii "Ochrona punktu końcowego w usłudze Microsoft Defender".



### <a name="onboarding-steps-summary"></a>Podsumowanie kroków dołączania

- KROK 1. [Pobieranie pakietów instalacyjnych i dołączających](#step-1-download-installation-and-onboarding-packages)
- KROK 2. [Stosowanie pakietu instalacyjnego i dołączania](#step-2-apply-the-installation-and-onboarding-package)
- KROK 3. [Wykonaj kroki dołączania](#step-3-complete-the-onboarding-steps) 

### <a name="step-1-download-installation-and-onboarding-packages"></a>KROK 1. Pobieranie pakietów instalacyjnych i dołączanych

Należy pobrać zarówno **pakiety instalacyjne** , jak i **dołączane** z portalu.

> [!div class="mx-imgBorder"]
> ![Obraz przedstawiający pulpit nawigacyjny dołączania](images/install-agent-onboard.png)


   > [!NOTE]
   > Na serwerze Windows Server 2012R2 Program antywirusowy Microsoft Defender zostanie zainstalowany przez pakiet instalacyjny i będzie aktywny, chyba że zostanie ustawiony na tryb pasywny. Na Windows Server 2016 należy najpierw zainstalować Program antywirusowy Microsoft Defender jako funkcję (zobacz [Przełączanie do rozwiązania MDE](/microsoft-365/security/defender-endpoint/switch-to-mde-phase-2#re-enable-microsoft-defender-antivirus-on-windows-server-2016)) przed kontynuowaniem instalacji.
   > 
   > Jeśli korzystasz z rozwiązania chroniącego przed złośliwym kodem firmy innej niż Microsoft, przed instalacją upewnij się, że dodano wykluczenia dla Program antywirusowy Microsoft Defender ([z tej listy procesów usługi Microsoft Defender na karcie Procesy usługi Defender](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)) do rozwiązania spoza firmy Microsoft.  Zaleca się również dodanie rozwiązań zabezpieczeń innych niż Microsoft do listy wykluczeń programu antywirusowego Defender.


**Pakiet instalacyjny** zawiera plik MSI, który instaluje agenta Ochrona punktu końcowego w usłudze Microsoft Defender.

**Pakiet dołączania** zawiera następujące pliki:

- `OptionalParamsPolicy` — zawiera ustawienie, które włącza zbieranie przykładów
- `WindowsDefenderATPOnboardingScript.cmd` — zawiera skrypt dołączania

Aby pobrać pakiety, wykonaj następujące kroki: 

1. W Microsoft 365 Defender przejdź do **Ustawienia > Zarządzanie urządzeniami > dołączania**.

2. Wybierz **pozycję Windows Server 2012 R2 i 2016**.

3. Wybierz pozycję **Pobierz pakiet instalacyjny** i zapisz plik .msi. 
 
4. Wybierz pozycję **Pobierz pakiet dołączania** i zapisz plik .zip.

5. Zainstaluj pakiet instalacyjny przy użyciu dowolnej z opcji instalacji Program antywirusowy Microsoft Defender. Instalacja wymaga uprawnień administracyjnych.



### <a name="step-2-apply-the-installation-and-onboarding-package"></a>KROK 2. Stosowanie pakietu instalacyjnego i dołączania
W tym kroku zainstalujesz składniki zapobiegania i wykrywania wymagane przed dołączeniem urządzenia do środowiska chmury Ochrona punktu końcowego w usłudze Microsoft Defender, aby przygotować maszynę do dołączenia. Upewnij się, że zostały spełnione wszystkie [wymagania wstępne](#prerequisites) . 

   > [!NOTE]
   > Program antywirusowy Microsoft Defender zostanie zainstalowana i będzie aktywna, chyba że zostanie ustawiona na tryb pasywny. 

#### <a name="options-to-install-the-microsoft-defender-for-endpoint-packages"></a>Opcje instalowania pakietów Ochrona punktu końcowego w usłudze Microsoft Defender

W poprzedniej sekcji pobrano pakiet instalacyjny. Pakiet instalacyjny zawiera instalator dla wszystkich składników Ochrona punktu końcowego w usłudze Microsoft Defender. 

Aby zainstalować agenta, możesz użyć dowolnej z następujących opcji:
- [Instalowanie przy użyciu wiersza polecenia](#install-microsoft-defender-for-endpoint-using-the-command-line)
- [Instalowanie przy użyciu skryptu](#install-microsoft-defender-for-endpoint-using-a-script)
- [Stosowanie pakietów instalacyjnych i dołączających przy użyciu zasady grupy](#apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy)

##### <a name="install-microsoft-defender-for-endpoint-using-the-command-line"></a>Instalowanie usługi Microsoft Defender dla punktu końcowego przy użyciu wiersza polecenia
Użyj pakietu instalacyjnego z poprzedniego kroku, aby zainstalować Ochrona punktu końcowego w usłudze Microsoft Defender. 


Uruchom następujące polecenie, aby zainstalować Ochrona punktu końcowego w usłudze Microsoft Defender:

```console
Msiexec /i md4ws.msi /quiet
```

Aby odinstalować, upewnij się, że maszyna została najpierw odłączona przy użyciu odpowiedniego skryptu odłączania. Następnie użyj programu Panel sterowania \> Programy \> i funkcje, aby przeprowadzić odinstalowywanie.

Alternatywnie uruchom następujące polecenie dezinstalacji, aby odinstalować Ochrona punktu końcowego w usłudze Microsoft Defender:

```console
Msiexec /x md4ws.msi /quiet
```

Aby powyższe polecenie zakończyło się pomyślnie, należy użyć tego samego pakietu, którego użyto do instalacji.

Przełącznik `/quiet` pomija wszystkie powiadomienia.

> [!NOTE]
> Program antywirusowy Microsoft Defender nie przechodzi automatycznie w tryb pasywny. Jeśli korzystasz z rozwiązania antywirusowego/chroniącego przed złośliwym kodem firmy Microsoft, możesz ustawić Program antywirusowy Microsoft Defender w trybie pasywnym. W przypadku instalacji wiersza polecenia opcjonalny `FORCEPASSIVEMODE=1` natychmiast ustawia składnik Program antywirusowy Microsoft Defender na tryb pasywny, aby uniknąć zakłóceń. Następnie, aby upewnić się, że program antywirusowy Defender pozostaje w trybie pasywnym po dołączeniu do obsługi funkcji, takich jak EDR Block, ustaw klucz rejestru "ForceDefenderPassiveMode".

Obsługa serwera Windows zapewnia dokładniejszy wgląd w działania serwera, pokrycie wykrywania ataków jądra i pamięci oraz włącza akcje reagowania.

##### <a name="install-microsoft-defender-for-endpoint-using-a-script"></a>Instalowanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu skryptu

Skrypt [instalatora](server-migration.md#installer-script) ułatwia automatyzację instalacji, odinstalowywania i dołączania. Aby uzyskać więcej informacji, zobacz instrukcje w poniższej sekcji dotyczące używania skryptu z zasady grupy.

##### <a name="apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy"></a>Stosowanie Ochrona punktu końcowego w usłudze Microsoft Defender instalacji i dołączania pakietów przy użyciu zasad grupy

1. Tworzenie zasad grupy: <br> Otwórz [konsolę zarządzania zasady grupy](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), kliknij prawym przyciskiem myszy **pozycję zasady grupy Obiekty**, które chcesz skonfigurować, i kliknij przycisk **Nowy**. Wprowadź nazwę nowego obiektu zasad grupy w wyświetlonym oknie dialogowym i kliknij przycisk **OK**.

2. Otwórz [konsolę zarządzania zasady grupy](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), kliknij prawym przyciskiem myszy obiekt zasady grupy , który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**, **preferencje**, a następnie **ustawienia panelu sterowania**.

4. Kliknij prawym przyciskiem myszy pozycję **Zaplanowane zadania**, wskaż pozycję **Nowe**, a następnie kliknij pozycję **Zadanie natychmiastowe (co najmniej Windows 7)**.

5. W **wyświetlonym oknie Zadanie** przejdź do karty **Ogólne** . W obszarze **Opcje zabezpieczeń** kliknij pozycję **Zmień użytkownika lub grupę** i wpisz SYSTEM, a następnie kliknij pozycję **Sprawdź nazwy** , a następnie **przycisk OK**. NT AUTHORITY\SYSTEM jest wyświetlany jako konto użytkownika, które będzie uruchamiane jako zadanie.

6. Wybierz pozycję **Uruchom, czy użytkownik jest zalogowany, czy nie** , i zaznacz pole wyboru **Uruchom z najwyższymi uprawnieniami** .

7. W polu Nazwa wpisz odpowiednią nazwę zaplanowanego zadania (na przykład Defender for Endpoint Deployment).

8. Przejdź do karty **Akcje** i wybierz pozycję **Nowy...** Upewnij się, że w polu **Akcja** wybrano **opcję Uruchom program**. [Skrypt instalatora](server-migration.md#installer-script) obsługuje instalację i natychmiast wykonuje krok dołączania po zakończeniu instalacji. Wybierz *pozycjęC:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe* a następnie podaj argumenty:

    ```console
     -ExecutionPolicy RemoteSigned \\servername-or-dfs-space\share-name\install.ps1 -OnboardingScript \\servername-or-dfs-space\share-name\windowsdefenderatponboardingscript.cmd
    ```  

     >[!NOTE]
    >Jeśli chcesz rozwiązać problemy z instalacją agenta, dodaj polecenie "-etl -log" do parametrów skryptu install.ps1.
    >
    >Zalecane ustawienie zasad wykonywania to `Allsigned`. Wymaga to zaimportowania certyfikatu podpisywania skryptu do magazynu zaufanych wydawców komputera lokalnego, jeśli skrypt jest uruchomiony jako SYSTEM w punkcie końcowym.

    Zastąp \\ciąg servername-or-dfs-space\share-name ścieżką UNC przy użyciu w pełni kwalifikowanej nazwy domeny serwera plików (FQDN) udostępnionego pliku *install.ps1* . Pakiet instalatora md4ws.msi należy umieścić w tym samym katalogu.  Upewnij się również, że uprawnienia ścieżki UNC zezwalają na dostęp do odczytu do konta komputera, które instaluje platformę.

   

    W przypadku scenariuszy, w których chcesz Program antywirusowy Microsoft Defender współistnieć z rozwiązaniami ochrony przed złośliwym kodem innych niż Microsoft, dodaj parametr $Passive, aby ustawić tryb pasywny podczas instalacji.

9. Wybierz przycisk **OK** i zamknij wszystkie otwarte okna kontrolera GPMC.

10. Aby połączyć obiekt zasad grupy z jednostką organizacyjną (OU), kliknij prawym przyciskiem myszy i wybierz pozycję **Połącz istniejący obiekt zasad grupy**. W wyświetlonym oknie dialogowym wybierz obiekt zasady grupy, który chcesz połączyć. Kliknij przycisk **OK**.

Aby uzyskać dodatkowe ustawienia konfiguracji, zobacz [Konfigurowanie ustawień przykładowej kolekcji](configure-endpoints-gp.md#configure-sample-collection-settings) i [Inne zalecane ustawienia konfiguracji](configure-endpoints-gp.md#other-recommended-configuration-settings).

### <a name="step-3-complete-the-onboarding-steps"></a>KROK 3. Wykonaj kroki dołączania

Poniższe kroki mają zastosowanie tylko w przypadku korzystania z rozwiązania chroniącego przed złośliwym oprogramowaniem innych firm. Należy zastosować następujące ustawienie trybu pasywnego Program antywirusowy Microsoft Defender. Sprawdź, czy został poprawnie skonfigurowany:

1. Ustaw następujący wpis rejestru:
    - Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
    - Nazwa: `ForceDefenderPassiveMode`
    - Typu: `REG_DWORD`
    - Wartość: `1`

       :::image type="content" source="images/atp-verify-passive-mode.png" alt-text="Wynik weryfikacji trybu pasywnego" lightbox="images/atp-verify-passive-mode.png":::
> [!IMPORTANT]
>
> - Gdy używasz Microsoft Defender dla Chmury do monitorowania serwerów, dzierżawa usługi Defender for Endpoint jest tworzona automatycznie (w Stanach Zjednoczonych dla użytkowników z USA, w UE dla użytkowników europejskich i w Wielkiej Brytanii dla użytkowników z Wielkiej Brytanii).
Dane zbierane przez usługę Defender for Endpoint są przechowywane w lokalizacji geograficznej dzierżawy zgodnie z opisem podczas aprowizacji.
> - Jeśli używasz usługi Defender for Endpoint przed użyciem Microsoft Defender dla Chmury, dane będą przechowywane w lokalizacji określonej podczas tworzenia dzierżawy, nawet jeśli zostaną one zintegrowane z Microsoft Defender dla Chmury w późniejszym czasie.
> - Po skonfigurowaniu nie można zmienić lokalizacji przechowywania danych. Jeśli musisz przenieść dane do innej lokalizacji, musisz skontaktować się z pomoc techniczna firmy Microsoft, aby zresetować dzierżawę.
> - Pakiet dołączania dla Windows Server 2019 i Windows Server 2022 do Microsoft Endpoint Manager obecnie dostarcza skrypt. Aby uzyskać więcej informacji na temat wdrażania skryptów w Configuration Manager, zobacz [Pakiety i programy w Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs).
> - Skrypt lokalny jest odpowiedni do weryfikacji koncepcji, ale nie powinien być używany do wdrożenia produkcyjnego. W przypadku wdrożenia produkcyjnego zalecamy używanie zasady grupy lub Microsoft Endpoint Configuration Manager.



## <a name="windows-server-semi-annual-enterprise-channel-sac-windows-server-2019-and-windows-server-2022"></a>Windows Server Semi-Annual Enterprise Channel (SAC), Windows Server 2019 i Windows Server 2022

### <a name="download-package"></a>Pobieranie pakietu

1. W Microsoft 365 Defender przejdź do **Ustawienia > Zarządzanie urządzeniami > dołączania**.

2. Wybierz **pozycję Windows Server 1803 i 2019**.

3. Wybierz pozycję **Pobierz pakiet**. Zapisz go jako WindowsDefenderATPOnboardingPackage.zip.

4. Wykonaj kroki opisane w sekcji [Zakończ kroki dołączania](#step-3-complete-the-onboarding-steps) .


## <a name="verify-the-onboarding-and-installation"></a>Weryfikowanie dołączania i instalacji

Sprawdź, czy Program antywirusowy Microsoft Defender i Ochrona punktu końcowego w usłudze Microsoft Defender są uruchomione.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Uruchamianie testu wykrywania w celu zweryfikowania dołączania

Po dołączeniu urządzenia można uruchomić test wykrywania, aby sprawdzić, czy urządzenie jest prawidłowo dołączone do usługi. Aby uzyskać więcej informacji, zobacz [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](run-detection-test.md).

> [!NOTE]
> Uruchamianie Program antywirusowy Microsoft Defender nie jest wymagane, ale jest zalecane. Jeśli inny produkt dostawcy oprogramowania antywirusowego jest podstawowym rozwiązaniem ochrony punktu końcowego, możesz uruchomić program antywirusowy Defender w trybie pasywnym. Możesz tylko potwierdzić, że tryb pasywny jest włączony po sprawdzeniu, czy czujnik Ochrona punktu końcowego w usłudze Microsoft Defender (SENSE) jest uruchomiony.

1. Uruchom następujące polecenie, aby sprawdzić, czy Program antywirusowy Microsoft Defender jest zainstalowana:

    >[!NOTE]
    >Ten krok weryfikacji jest wymagany tylko wtedy, gdy używasz Program antywirusowy Microsoft Defender jako aktywnego rozwiązania chroniącego przed złośliwym kodem.

    `sc.exe query Windefend`


    Jeśli wynik to "Określona usługa nie istnieje jako zainstalowana usługa", musisz zainstalować Program antywirusowy Microsoft Defender. 


    Aby uzyskać informacje na temat sposobu używania zasady grupy do konfigurowania Program antywirusowy Microsoft Defender na serwerach Windows i zarządzania nimi, zobacz [Konfigurowanie i zarządzanie nimi za pomocą ustawień zasady grupy Program antywirusowy Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md).

2. Uruchom następujące polecenie, aby sprawdzić, czy Ochrona punktu końcowego w usłudze Microsoft Defender jest uruchomiona:

    `sc.exe query sense`

    Wynik powinien pokazywać, że jest uruchomiony. Jeśli wystąpią problemy z dołączaniem, zobacz [Rozwiązywanie problemów z dołączaniem](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Uruchamianie testu wykrywania

Wykonaj kroki opisane w [temacie Uruchamianie testu wykrywania na nowo dołączonym urządzeniu](run-detection-test.md) , aby sprawdzić, czy serwer raportuje do usługi Defender dla usługi Endpoint.

## <a name="next-steps"></a>Następne kroki

Po pomyślnym dołączeniu urządzeń do usługi należy skonfigurować poszczególne składniki Ochrona punktu końcowego w usłudze Microsoft Defender. Postępuj zgodnie z [kolejnością wdrażania](prepare-deployment.md#adoption-order) , aby kierować się włączaniem różnych składników.

## <a name="offboard-windows-servers"></a>Odłączanie serwerów Windows

Możesz odłączyć Windows Server 2012 R2, Windows Server 2016, Windows Server (SAC), Windows Server 2019 i Windows Server 2019 Core w tej samej metodzie dostępnej dla Windows 10 urządzeń klienckich.

- [Odłączanie urządzeń przy użyciu zasady grupy](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Odłączanie urządzeń przy użyciu Configuration Manager](configure-endpoints-sccm.md#offboard-devices-using-configuration-manager)
- [Odłączanie i monitorowanie urządzeń przy użyciu narzędzi mobile Zarządzanie urządzeniami](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)
- [Odłączanie urządzeń przy użyciu skryptu lokalnego](configure-endpoints-script.md#offboard-devices-using-a-local-script)

Po odłączeniu można odinstalować pakiet ujednoliconego rozwiązania w Windows Server 2012 R2 i Windows Server 2016.

W przypadku innych wersji serwera Windows dostępne są dwie opcje odłączania serwerów Windows z usługi:

- Odinstalowywanie agenta MMA
- Usuwanie konfiguracji obszaru roboczego usługi Defender for Endpoint

> [!NOTE]
> Te instrukcje dotyczące odłączania dla innych wersji serwera Windows mają zastosowanie również w przypadku uruchamiania poprzednich Ochrona punktu końcowego w usłudze Microsoft Defender dla Windows Server 2016 i Windows Server 2012 R2, które wymagają MMA. Instrukcje migracji do nowego ujednoliconego rozwiązania znajdują się [w scenariuszach migracji serwera w Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>Tematy pokrewne

- [Dołącz poprzednią wersję systemu Windows](onboard-downlevel.md)
- [Dołączanie urządzeń Windows 10](configure-endpoints.md)
- [Dołącz urządzenia z system operacyjnym innym niż Windows](configure-endpoints-non-windows.md)
- [Konfiguruj ustawienia serwera proxy i połączenia internetowego](configure-proxy-internet.md)
- [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu usługi Defender for Endpoint](run-detection-test.md)
- [Rozwiązywanie problemów z dołączaniem Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-onboarding.md)
