---
title: Dołączanie poprzednich wersji Windows na Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dołączanie obsługiwało poprzednie wersje urządzeń Windows, dzięki czemu mogą wysyłać dane czujnika do czujnika Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: onboard, windows, 7, 81, oms, sp1, enterprise, pro, down level
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
ms.technology: mde
ms.openlocfilehash: 8ca88340ae90889c0e45c5905863373d930949b2
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872967"
---
# <a name="onboard-previous-versions-of-windows"></a>Dołącz poprzednią wersję systemu Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platformy**

- Windows 7 Enterprise SP1
- Windows 7 Pro SP1
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows Server 2008 R2 z dodatkiem SP1

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Usługa Defender for Endpoint rozszerza obsługę o systemy operacyjne niższego poziomu, zapewniając zaawansowane funkcje wykrywania ataków i badania w obsługiwanych wersjach Windows.

Aby dołączyć punkty końcowe klienta Windows niższego poziomu do usługi Defender for Endpoint, należy wykonać następujące czynności:

- [Konfigurowanie i aktualizowanie klientów System Center Endpoint Protection](#configure-and-update-system-center-endpoint-protection-clients)
- [Instalowanie i konfigurowanie Microsoft Monitoring Agent (MMA) do raportowania danych czujnika](#install-and-configure-microsoft-monitoring-agent-mma)

W przypadku Windows Server 2008 R2 z dodatkiem SP1 można [dołączyć do Microsoft Defender dla Chmury](#onboard-windows-servers-through-microsoft-defender-for-cloud).

> [!NOTE]
> Aby dołączyć serwer Windows za pośrednictwem Microsoft Monitoring Agent (opcja 1) wymagana jest licencja autonomicznego serwera usługi Defender for Endpoint dla każdego węzła. Alternatywnie wymagana jest licencja usługi Microsoft Defender dla serwerów dla każdego węzła, aby dołączyć serwer Windows za pośrednictwem Microsoft Defender dla Chmury (opcja 2), zobacz [Obsługiwane funkcje dostępne w Microsoft Defender dla Chmury](/azure/defender-for-cloud/supported-machines-endpoint-solutions-clouds-servers).

> [!TIP]
> Po dołączeniu urządzenia można uruchomić test wykrywania, aby sprawdzić, czy jest ono prawidłowo dołączone do usługi. Aby uzyskać więcej informacji, zobacz [Uruchamianie testu wykrywania w nowo dołączonym punkcie końcowym usługi Defender for Endpoint](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>Konfigurowanie i aktualizowanie klientów System Center Endpoint Protection

> [!IMPORTANT]
> Ten krok jest wymagany tylko wtedy, gdy organizacja używa System Center Endpoint Protection (SCEP).

Usługa Defender for Endpoint integruje się z System Center Endpoint Protection, aby zapewnić wgląd w wykrywanie złośliwego oprogramowania i zatrzymać propagację ataku w organizacji, zakazując potencjalnie złośliwych plików lub podejrzewanego złośliwego oprogramowania.

Aby włączyć tę integrację, wymagane są następujące kroki:

- Instalowanie [aktualizacji platformy chroniącej przed złośliwym oprogramowaniem ze stycznia 2017 r. dla klientów Endpoint Protection](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- Konfigurowanie członkostwa klienta SCEP w usłudze Cloud Protection w ustawieniu **Zaawansowanym**
- Skonfiguruj sieć tak, aby zezwalała na połączenia z chmurą Program antywirusowy Microsoft Defender. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i weryfikowanie połączeń sieciowych Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>Instalowanie i konfigurowanie Microsoft Monitoring Agent (MMA)

### <a name="before-you-begin"></a>Przed rozpoczęciem

Przejrzyj następujące szczegóły, aby sprawdzić minimalne wymagania systemowe:

- Instalowanie [miesięcznego pakietu zbiorczego aktualizacji z lutego 2018 r.](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

  > [!NOTE]
  > Dotyczy tylko Windows Server 2008 R2, Windows 7 z dodatkiem SP1 Enterprise i Windows 7 Pro SP1.

- Instalowanie [aktualizacji środowiska klienta i danych telemetrycznych diagnostycznych](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- Zainstaluj program [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (lub nowszy) lub [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > Dotyczy tylko Windows Server 2008 R2, Windows 7 z dodatkiem SP1 Enterprise i Windows 7 Pro SP1.
    >
    > Nie instaluj .NET Framework 4.0.x, ponieważ spowoduje to zanegonie powyższej instalacji.
    >
    > Instalacja platformy .NET 4.5 może wymagać ponownego uruchomienia komputera po instalacji.

- Spełnianie minimalnych wymagań systemowych agenta usługi Azure Log Analytics. Aby uzyskać więcej informacji, zobacz [Zbieranie danych z komputerów w środowisku za pomocą usługi Log Analytics](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)

### <a name="installation-steps"></a>Kroki instalacji

1. Pobierz plik konfiguracji agenta: [Windows agenta 64-bitowego](https://go.microsoft.com/fwlink/?LinkId=828603) lub [agenta 32-bitowego Windows](https://go.microsoft.com/fwlink/?LinkId=828604).

    >[!NOTE]
    >Z powodu [wycofania obsługi SHA-1 przez agenta MMA](/azure/azure-monitor/agents/agent-windows#sha-2-code-signing-support-requirement) agent mma musi mieć wersję 10.20.18029 lub nowszą.
    

2. Uzyskaj identyfikator obszaru roboczego:
   - W okienku nawigacji usługi Defender for Endpoint wybierz pozycję **Ustawienia > Zarządzanie urządzeniami > dołączanie**
   - Wybieranie systemu operacyjnego
   - Kopiowanie identyfikatora obszaru roboczego i klucza obszaru roboczego

3. Korzystając z identyfikatora obszaru roboczego i klucza obszaru roboczego, wybierz dowolną z następujących metod instalacji, aby zainstalować agenta:
    - [Ręcznie zainstaluj agenta przy użyciu instalatora](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      Na stronie **Opcje instalacji agenta** wybierz **pozycję Połączenie agenta do usługi Azure Log Analytics (OMS)**

    - [Zainstaluj agenta przy użyciu wiersza polecenia](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [Skonfiguruj agenta przy użyciu skryptu](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation).

   > [!NOTE]
   > Jeśli jesteś [klientem rządowym USA](gov.md), w obszarze "Azure Cloud" musisz wybrać opcję "Azure US Government", jeśli używasz kreatora konfiguracji lub jeśli używasz wiersza polecenia lub skryptu — ustaw parametr "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" na 1.

4. Jeśli używasz serwera proxy do nawiązywania połączenia z Internetem, zobacz sekcję Konfigurowanie ustawień serwera proxy i łączności z Internetem.

Po zakończeniu powinny zostać wyświetlone dołączone punkty końcowe w portalu w ciągu godziny.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>Konfiguruj ustawienia serwera proxy i połączenia internetowego
Jeśli serwery muszą używać serwera proxy do komunikowania się z usługą Defender for Endpoint, użyj jednej z następujących metod, aby skonfigurować mma do korzystania z serwera proxy:

- [Konfigurowanie mma do korzystania z serwera proxy](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [Konfigurowanie Windows do używania serwera proxy dla wszystkich połączeń](configure-proxy-internet.md)

Jeśli serwer proxy lub zapora są używane, upewnij się, że serwery mogą uzyskiwać dostęp do wszystkich adresów URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender bezpośrednio i bez przechwytywania protokołu SSL. Aby uzyskać więcej informacji, zobacz [Włączanie dostępu do adresów URL usługi Defender for Endpoint](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Użycie przechwytywania protokołu SSL uniemożliwi systemowi komunikowanie się z usługą Defender for Endpoint.

Po zakończeniu w ciągu godziny powinny zostać wyświetlone dołączone serwery Windows w portalu.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>Dołączanie serwerów Windows za pośrednictwem Microsoft Defender dla Chmury

1. W okienku nawigacji Microsoft 365 Defender wybierz pozycję **Ustawienia** >  Device management **Onboarding (Dołączanie** **do zarządzania urządzeniami** > ).

2. Wybierz **pozycję Windows Server 2008 R2 SP1** jako system operacyjny.

3. Kliknij **pozycję Dołączanie serwerów w Microsoft Defender dla Chmury**.

4. Postępuj zgodnie z instrukcjami dołączania w [Ochrona punktu końcowego w usłudze Microsoft Defender z Microsoft Defender dla Chmury](/azure/security-center/security-center-wdatp) i Jeśli używasz usługi Azure ARC, postępuj zgodnie z instrukcjami dotyczącymi [dołączania w temacie Włączanie integracja Ochrona punktu końcowego w usłudze Microsoft Defender](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

Po wykonaniu kroków dołączania należy [skonfigurować i zaktualizować System Center Endpoint Protection klientów](#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
>
> - Aby dołączanie za pośrednictwem usługi Microsoft Defender dla serwerów działało zgodnie z oczekiwaniami, serwer musi mieć odpowiedni obszar roboczy i klucz skonfigurowany w ustawieniach Microsoft Monitoring Agent (MMA).
> - Po skonfigurowaniu na maszynie zostanie wdrożony odpowiedni pakiet administracyjny w chmurze, a proces czujnika (MsSenseS.exe) zostanie wdrożony i uruchomiony.
> - Jest to również wymagane, jeśli serwer jest skonfigurowany do używania serwera bramy OMS jako serwera proxy.



## <a name="verify-onboarding"></a>Weryfikowanie dołączania

Sprawdź, czy usługa Microsoft Defender AV i Ochrona punktu końcowego w usłudze Microsoft Defender są uruchomione. 

> [!NOTE]
> Uruchamianie usługi Microsoft Defender AV nie jest wymagane, ale jest zalecane. Jeśli inny produkt dostawcy oprogramowania antywirusowego jest podstawowym rozwiązaniem ochrony punktu końcowego, możesz uruchomić program antywirusowy Defender w trybie pasywnym. Możesz tylko potwierdzić, że tryb pasywny jest włączony po sprawdzeniu, czy czujnik Ochrona punktu końcowego w usłudze Microsoft Defender (SENSE) jest uruchomiony. 

1. Uruchom następujące polecenie, aby sprawdzić, czy zainstalowano usługę Microsoft Defender AV:

   ```sc.exe query Windefend```

    Jeśli wynik to "Określona usługa nie istnieje jako zainstalowana usługa", musisz zainstalować usługę Microsoft Defender AV. Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-windows.md).

    Aby uzyskać informacje na temat sposobu używania zasady grupy do konfigurowania Program antywirusowy Microsoft Defender na serwerach Windows i zarządzania nimi, zobacz [Konfigurowanie i zarządzanie nimi za pomocą ustawień zasady grupy Program antywirusowy Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md).


2. Uruchom następujące polecenie, aby sprawdzić, czy Ochrona punktu końcowego w usłudze Microsoft Defender jest uruchomiona:

    ```sc.exe query sense```
    
    Wynik powinien pokazywać, że jest uruchomiony. Jeśli wystąpią problemy z dołączaniem, zobacz [Rozwiązywanie problemów z dołączaniem](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Uruchamianie testu wykrywania
Wykonaj kroki opisane w [temacie Uruchamianie testu wykrywania na nowo dołączonym urządzeniu](run-detection-test.md) , aby sprawdzić, czy serwer raportuje do usługi Defender dla usługi Endpoint.





## <a name="onboarding-endpoints-with-no-management-solution"></a>Dołączanie punktów końcowych bez rozwiązania do zarządzania 

### <a name="using-group-policy"></a>Korzystanie z zasady grupy

**Krok 1. Pobieranie odpowiedniego interfejsu użytkownika dla punktu końcowego.**

1. Przejdź do folderu c:\windows\sysvol\domain\scripts (może być wymagana kontrola zmiany na jednym z kontrolerów domeny).
1. Utwórz folder o nazwie MMA.
1. Pobierz następujące elementy i umieść je w folderze MMA:
   
    - Aktualizacja środowiska klienta i danych telemetrycznych diagnostycznych:
      - [Dla Windows Server 2008 R2 x64](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    W przypadku Windows Server 2008 R2 z dodatkiem SP1 wymagane są również następujące aktualizacje:

    Zestawienie miesięczne z lutego 2018 r. — KB4074598 (Windows Server 2008 R2)

    [Wykaz usługi Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    Pobieranie aktualizacji dla Windows Server 2008 R2 x64
    
    .NET Framework 3.5.1 (KB315418)<br>
    [Dla Windows Server 2008 R2 x64](/iis/install/installing-iis-7/install-windows-server-2008-and-windows-server-2008-r2)
    
    >[!NOTE]
    > W tym artykule przyjęto założenie, że używasz serwerów opartych na systemie x64 (agent MMA .exe x64 Nowa wersja zgodna ze standardem SHA-2).


**Krok 2. Tworzenie nazwy pliku DeployMMA.cmd (przy użyciu Notatnika)** Dodaj następujące wiersze do pliku cmd. Należy pamiętać, że będziesz potrzebować identyfikatora obszaru roboczego i klucza.

Poniższe polecenie jest przykładem. Zastąp następujące wartości:
- KB — użyj odpowiedniej bazy wiedzy odpowiedniej dla dołączanego punktu końcowego
- Identyfikator obszaru roboczego i klucz — użyj identyfikatora i klucza


```dos
@echo off 
cd "C:"
IF EXIST "C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe" ( 
exit
) ELSE (

wusa.exe C:\Windows\MMA\Windows6.1-KB3080149-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows6.1-KB4074598-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows6.1-KB3154518-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows8.1-KB3080149-x64.msu /quiet /norestart
"c:\windows\MMA\MMASetup-AMD64.exe" /c /t: "C:\Windows\MMA"c:\windows\MMA\ setup.exe /qn NOAPM=1 ADD_OPINSIGHTS_WORKSPACE=1
OPINSIGHTS_WORKSPACE_ID="<your workspace ID>"
OPINSIGHTS_WORKSPACE_KEY="<your workspace key>" AcceptEndUserLicenseAgreement=1
)

)
```





### <a name="group-policy-configuration"></a>konfiguracja zasady grupy

Utwórz nowe zasady grupy przeznaczone specjalnie do dołączania urządzeń, takich jak "Ochrona punktu końcowego w usłudze Microsoft Defender dołączanie".

- Tworzenie folderu zasady grupy o nazwie "c:\windows\MMA"

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="Lokalizacja folderów" lightbox="images/grppolicyconfig1.png":::

    **Spowoduje to dodanie nowego folderu na każdym serwerze, który pobiera zastosowany obiekt zasad grupy o nazwie MMA i będzie przechowywany w c:\windows. Będzie on zawierać pliki instalacyjne programu MMA, wymagania wstępne i skrypt instalacji.**

- Utwórz preferencję zasady grupy Files dla każdego z plików przechowywanych w logowaniu do sieci.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="Zasady grupy — 1" lightbox="images/grppolicyconfig2.png":::

Kopiuje pliki z DOMENY\NETLOGON\MMA\filename do C:\windows\MMA\filename - **więc pliki instalacyjne są lokalne na serwerze**:

:::image type="content" source="images/deploymma.png" alt-text="Deploy mma cmd properties (Wdrażanie właściwości cmd mma)" lightbox="images/deploymma.png":::

Powtórz proces, ale utwórz określanie wartości docelowej na poziomie elementu na karcie COMMON, więc plik zostanie skopiowany tylko do odpowiedniej wersji platformy/systemu operacyjnego w zakresie:

:::image type="content" source="images/targeteditor.png" alt-text="Edytor docelowy" lightbox="images/targeteditor.png":::

W przypadku Windows Server 2008 R2 będziesz potrzebować (i będzie on kopiować tylko w dół) następujące elementy:
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


Po zakończeniu należy utworzyć zasady skryptu uruchamiania:

:::image type="content" source="images/startupprops.png" alt-text="Właściwości uruchamiania" lightbox="images/startupprops.png":::

Nazwa pliku do uruchomienia w tym miejscu to c:\windows\MMA\DeployMMA.cmd.
Po ponownym uruchomieniu serwera w ramach procesu uruchamiania zainstaluje on aktualizację środowiska klienta i telemetrię diagnostyczną KB, a następnie zainstaluje agenta MMA podczas ustawiania identyfikatora obszaru roboczego i klucza, a serwer zostanie dołączony.

Możesz również użyć **natychmiastowego zadania** , aby uruchomić plik deployMMA.cmd, jeśli nie chcesz ponownie uruchamiać wszystkich serwerów.

Można to zrobić w dwóch fazach. Najpierw utwórz **pliki i folder w obiekcie** zasad grupy — daj systemowi czas na upewnienie się, że obiekt zasad grupy został zastosowany, a wszystkie serwery mają pliki instalacyjne. Następnie dodaj zadanie natychmiastowe. Spowoduje to osiągnięcie tego samego wyniku bez konieczności ponownego uruchamiania.

Ponieważ skrypt ma metodę zakończenia i nie będzie uruchamiany ponownie, jeśli jest zainstalowany program MMA, możesz również użyć zaplanowanego zadania codziennego, aby osiągnąć ten sam wynik. Podobnie jak w przypadku zasad zgodności Configuration Manager będzie codziennie sprawdzana, aby upewnić się, że mma jest obecny.

:::image type="content" source="images/schtask.png" alt-text="zaplanuj zadanie" lightbox="images/schtask.png":::

:::image type="content" source="images/newtaskprops.png" alt-text="Właściwości nowego zadania" lightbox="images/newtaskprops.png":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="Wdrażanie właściwości pobierania mma" lightbox="images/deploymmadowmload.png":::

:::image type="content" source="images/tasksch.png" alt-text="Harmonogram zadań" lightbox="images/tasksch.png":::

Jak wspomniano w dokumentacji dołączania do serwera w szczególności wokół serwera 2008 R2, zobacz poniżej: Aby uzyskać Windows Server 2008 R2 SP1, upewnij się, że spełniasz następujące wymagania:

- Instalowanie [miesięcznego pakietu zbiorczego aktualizacji z lutego 2018 r.](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- Zainstaluj program [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (lub nowszy) lub [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

Sprawdź, czy bazy danych są obecne przed dołączeniem Windows Server 2008 R2. Ten proces umożliwia dołączenie wszystkich serwerów, jeśli nie masz Configuration Manager zarządzania serwerami.


## <a name="offboard-endpoints"></a>Odłączanie punktów końcowych

Dostępne są dwie opcje odłączania punktów końcowych Windows z usługi:

- Odinstalowywanie agenta MMA
- Usuwanie konfiguracji obszaru roboczego usługi Defender for Endpoint

> [!NOTE]
> Odłączanie powoduje, że punkt końcowy Windows przestaje wysyłać dane czujników do portalu, ale dane z punktu końcowego, w tym odwołania do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie 6 miesięcy.

### <a name="uninstall-the-mma-agent"></a>Odinstalowywanie agenta MMA

Aby odłączyć punkt końcowy Windows, możesz odinstalować agenta MMA lub odłączyć go od raportowania do obszaru roboczego usługi Defender for Endpoint. Po odłączeniu agenta punkt końcowy nie będzie już wysyłać danych czujnika do usługi Defender for Endpoint.
Aby uzyskać więcej informacji, zobacz [Aby wyłączyć agenta](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>Usuwanie konfiguracji obszaru roboczego usługi Defender for Endpoint

Możesz użyć jednej z następujących metod:

- Usuwanie konfiguracji obszaru roboczego usługi Defender for Endpoint z agenta MMA
- Uruchom polecenie programu PowerShell, aby usunąć konfigurację

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>Usuwanie konfiguracji obszaru roboczego usługi Defender for Endpoint z agenta MMA

1. Na **Microsoft Monitoring Agent Właściwości** wybierz kartę **Azure Log Analytics (OMS**).

2. Wybierz obszar roboczy Defender for Endpoint i kliknij pozycję **Usuń**.

    :::image type="content" source="images/atp-mma.png" alt-text="Okienko Obszary robocze" lightbox="images/atp-mma.png":::

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>Uruchom polecenie programu PowerShell, aby usunąć konfigurację

1. Pobierz identyfikator obszaru roboczego:

   1. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Onboarding**.

   1. Wybierz odpowiedni system operacyjny i uzyskaj identyfikator obszaru roboczego.

    
2. Otwórz program PowerShell z podwyższonym poziomem uprawnień i uruchom następujące polecenie. Użyj uzyskanego identyfikatora obszaru roboczego i zastąp element `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
