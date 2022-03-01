---
title: Wniesienie poprzednich wersji programu Windows programu Microsoft Defender dla punktu końcowego
description: Urządzenia typu Onboard obsługiły poprzednie wersje Windows, dzięki czemu mogą przesyłać dane czujnika do czujnika programu Microsoft Defender for Endpoint
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
ms.openlocfilehash: 60fd10024be0b214aed4cbc7ae89d7129df99e79
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63020862"
---
# <a name="onboard-previous-versions-of-windows"></a>Wniesienie poprzednich wersji Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platformy**

- Windows 7 z dodatkiem SP1 Enterprise
- Windows 7 z dodatkiem SP1 Pro
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows Server 2008 R2 z dodatkiem SP1

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Program Defender for Endpoint rozszerza obsługę, zapewniając zaawansowane funkcje wykrywania ataków i badania na obsługiwanych Windows wersjach.

Aby do usługi Defender for Endpoint Windows punktów końcowych klienta, musisz:

- [Konfigurowanie i aktualizowanie System Center Endpoint Protection klienta](#configure-and-update-system-center-endpoint-protection-clients)
- [Instalowanie i konfigurowanie Microsoft Monitoring Agent MMA w celu zgłaszania danych czujnika](#install-and-configure-microsoft-monitoring-agent-mma)

W Windows Server 2008 R2 z dodatkiem SP1 masz możliwość do rozwiązania rozwiązania [Microsoft Defender for Cloud](#onboard-windows-servers-through-microsoft-defender-for-cloud).

> [!NOTE]
> Aby serwer programu Defender dla punktu końcowego był w trybie Microsoft Monitoring Agent w węźle, wymagana jest Windows serwera poczty e-mail (opcja 1). Ewentualnie wymagana jest licencja microsoft Defender for servers na każdy węzeł, aby móc wboardować serwer programu Windows za pośrednictwem programu Microsoft Defender dla chmury (opcja 2), zobacz Obsługiwane funkcje dostępne w programie [Microsoft Defender dla chmury](/azure/security-center/security-center-services).

> [!TIP]
> Po włoceniu urządzenia możesz uruchomić test wykrywania w celu sprawdzenia, czy zostało ono poprawnie podłączone do usługi. Aby uzyskać więcej informacji, zobacz Uruchamianie testu wykrywania dla nowo [dodanego punktu końcowego programu Defender](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>Konfigurowanie i aktualizowanie System Center Endpoint Protection klienta

> [!IMPORTANT]
> Ten krok jest wymagany tylko w przypadku, gdy Twoja organizacja System Center Endpoint Protection (SCEP).

Program Defender for Endpoint jest zintegrowany z programem System Center Endpoint Protection w celu zapewnienia widoczności wykrywaniu złośliwego oprogramowania i zatrzymania propagacji ataków w organizacji przez zablokowanie potencjalnie złośliwych plików lub potencjalnego złośliwego oprogramowania.

Aby włączyć tę integrację, wymagane są następujące kroki:

- Instalowanie aktualizacji [platformy chroniącej przed złośliwym oprogramowaniem ze stycznia 2017 r. dla Endpoint Protection klientów](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- Konfigurowanie członkostwa klienta SCEP w usłudze Cloud Protection na poziomie **ustawienia Zaawansowane**
- Skonfiguruj sieć, aby zezwalać na połączenia z chmurą Program antywirusowy Microsoft Defender sieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i sprawdzanie poprawności Program antywirusowy Microsoft Defender sieciowych.](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>Instalowanie i konfigurowanie Microsoft Monitoring Agent (MMA)

### <a name="before-you-begin"></a>Przed rozpoczęciem

Przejrzyj poniższe informacje, aby sprawdzić minimalne wymagania systemowe:

- Instalowanie pakietu zb. aktualizacji miesięcznej z lutego [2018 r.](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

  > [!NOTE]
  > Dotyczy tylko Windows Server 2008 R2, Windows 7 SP1 Enterprise i Windows 7 SP1 Pro.

- Instalowanie aktualizacji [w celu obsługi klienta i telemetrii diagnostycznej](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- Instalowanie programu [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (lub nowszego) albo [aktualizacji KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > Dotyczy tylko Windows Server 2008 R2, Windows 7 SP1 Enterprise i Windows 7 SP1 Pro.
    >
    > Nie instaluj .NET Framework 4.0.x, ponieważ spowoduje to negatywę powyższej instalacji.
    >
    > Instalacja programu .NET 4.5 może wymagać ponownego uruchomienia komputera po instalacji.

- Spełnia minimalne wymagania systemowe agenta usługi Azure Log Analytics. Aby uzyskać więcej informacji, zobacz [Zbieranie danych z komputerów w środowisku za pomocą analizy dziennika](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites).

### <a name="installation-steps"></a>Kroki instalacji

1. Pobierz plik konfiguracji agenta: [Windows 64-bitowy](https://go.microsoft.com/fwlink/?LinkId=828603) lub Windows [32-bitowy agent](https://go.microsoft.com/fwlink/?LinkId=828604).

2. Uzyskaj identyfikator obszaru roboczego:
   - W okienku nawigacji programu Defender for Endpoint wybierz pozycję Ustawienia > **Zarządzanie urządzeniami > dołączanie**
   - Wybieranie systemu operacyjnego
   - Kopiowanie identyfikatora obszaru roboczego i klawisza obszaru roboczego

3. Za pomocą klawiszy Identyfikator obszaru roboczego i Obszar roboczy wybierz dowolną z następujących metod instalacji, aby zainstalować agenta:
    - [Ręcznie zainstaluj agenta przy użyciu konfiguracji](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      Na stronie **Opcje konfiguracji agenta** wybierz pozycję **Połączenie do usługi Azure Log Analytics (OMS)**

    - [Zainstaluj agenta za pomocą wiersza polecenia](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [Skonfiguruj agenta przy użyciu skryptu](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation).

   > [!NOTE]
   > Jeśli jesteś klientem administracji państwowej Stanów [Zjednoczonych, w](gov.md) obszarze "Azure Cloud" musisz wybrać pozycję "Azure US Government" (Platforma Azure dla instytucji rządowych Stanów Zjednoczonych) w przypadku korzystania z kreatora konfiguracji, a jeśli używasz wiersza polecenia lub skryptu — ustaw parametr "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" na 1.

4. Jeśli łączysz się z Internetem za pomocą serwera proxy, zobacz sekcję Konfigurowanie ustawień serwera proxy i łączności internetowej.

Po ukończeniu w ciągu godziny w portalu powinny zostać zobaczyć punktu końcowe wnosone.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>Konfigurowanie ustawień serwera proxy i łączności internetowej
Jeśli serwery muszą korzystać z serwera proxy do komunikacji z usługą Defender for Endpoint, użyj jednej z następujących metod, aby skonfigurować mma do używania serwera proxy:

- [Konfigurowanie usługi MMA do używania serwera proxy](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [Konfigurowanie Windows używania serwera proxy dla wszystkich połączeń](configure-proxy-internet.md)

Jeśli serwer proxy lub zapora są w użyciu, upewnij się, że serwery mogą uzyskać bezpośredni dostęp do wszystkich adresów URL usługi Microsoft Defender dla punktu końcowego bez przecięcia z protokołem SSL. Aby uzyskać więcej informacji, zobacz [Włączanie dostępu do usługi Defender dla adresów URL usługi punktu końcowego](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Użycie punktu przecięcia SSL uniemożliwia systemowi komunikowanie się z usługą Defender for Endpoint.

Po zakończeniu w portalu powinny być Windows w portalu w ciągu godziny.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>Wnosz Windows serwerach za pośrednictwem programu Microsoft Defender dla chmury

1. W okienku Microsoft 365 Defender nawigacji wybierz pozycję **Ustawienia** >  **Device** **managementOnboarding** >  (Zarządzanie urządzeniami).

2. Wybierz **Windows Windows Server 2008 R2 z dodatkiem SP1** jako system operacyjny.

3. Kliknij **pozycję Serwery onboard w usłudze Microsoft Defender dla chmury**.

4. Postępuj zgodnie z instrukcjami dotyczącymi dołączania do programu Microsoft Defender dla punktu końcowego w programie [Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) i Jeśli korzystasz z funkcji Azure ARC, postępuj zgodnie z instrukcjami dotyczącymi dołączania do programu [Microsoft Defender for Endpoint](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

Po wykonaniu kroków dołączania musisz skonfigurować i zaktualizować System Center Endpoint Protection [klientów](#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
>
> - Aby zapewnić przewidywaną pracę podczas dołączania serwerów za pośrednictwem programu Microsoft Defender, serwer musi mieć skonfigurowany odpowiedni obszar roboczy i klucz w ustawieniach programu Microsoft Monitoring Agent (MMA).
> - Po skonfigurowaniu na komputerze wdrożony zostanie odpowiedni pakiet administracyjny w chmurze, a proces czujnika (MsSenseS.exe) zostanie wdrożony i uruchomiony.
> - Jest to również wymagane, jeśli serwer jest skonfigurowany do używania serwera bramy OMS jako serwera proxy.



## <a name="verify-onboarding"></a>Weryfikuj dołączanie

Upewnij się, że program Microsoft Defender AV i Microsoft Defender for Endpoint są uruchomione. 

> [!NOTE]
> Uruchomienie programu Microsoft Defender AV nie jest wymagane, ale jest zalecane. Jeśli głównym rozwiązaniem ochrony punktu końcowego jest inny produkt dostawcy oprogramowania antywirusowego, możesz uruchomić program antywirusowy Defender w trybie pasywnym. Można sprawdzić, czy tryb pasywny jest uruchomiony tylko po sprawdzeniu, czy czujnik programu Microsoft Defender for Endpoint (SENSE) jest uruchomiony. 

1. Uruchom następujące polecenie, aby sprawdzić, czy program Microsoft Defender AV jest zainstalowany:

   ```sc.exe query Windefend```

    Jeśli wynikiem jest to, że "Określona usługa nie istnieje jako zainstalowana usługa", musisz zainstalować program Microsoft Defender AV. Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-windows.md).

    Aby uzyskać informacje na temat konfigurowania zasady grupy sieci Program antywirusowy Microsoft Defender na serwerach Windows i zarządzania nimi, zobacz Konfigurowanie i zarządzanie usługą zasady grupy przy użyciu [ustawień Program antywirusowy Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md).


2. Uruchom następujące polecenie, aby sprawdzić, czy usługa Microsoft Defender dla punktu końcowego jest uruchomiona:

    ```sc.exe query sense```
    
    Wynik powinien być pokazywany, że jest uruchomiony. Jeśli wystąpią problemy z dołączaniem, zobacz [Rozwiązywanie problemów z dołączaniem](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Uruchamianie testu wykrywania
Postępuj zgodnie z instrukcjami w teście uruchamiania wykrywania na nowo [wnosiowym](run-detection-test.md) urządzeniu, aby sprawdzić, czy serwer raportuje usługę Defender dla punktu końcowego.





## <a name="onboarding-endpoints-with-no-management-solution"></a>Punkty końcowe dołączania bez rozwiązania do zarządzania 

### <a name="using-group-policy"></a>Korzystanie z zasady grupy

**Krok 1. Pobieranie odpowiedniej witryny udpate dla punktu końcowego.**

1. Przejdź do folderu c:\windows\sysvol\domain\scripts (kontrolka zmiany może być potrzebna w jednym z kontrolerów domeny).
1. Utwórz folder o nazwie MMA.
1. Pobierz następujące elementy i umieść je w folderze MMA:
   
    - Aktualizacja do obsługi klienta i telemetrii diagnostycznej:
      - [Dla Windows Server 2008 R2 x64](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    W Windows Server 2008 R2 z dodatkiem SP1 są również wymagane następujące aktualizacje:

    Aktualizacja miesięczna z lutego 2018 r. — KB4074598 (Windows Server 2008 R2)

    [Wykaz usługi Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    Pobieranie aktualizacji dla Windows Server 2008 R2 x64
    
    .NET Framework 3.5.1 (KB315418)<br>
    [Dla Windows Server 2008 R2 x64](https://download.microsoft.com/download/6/8/0/680ee424-358c-4fdf-a0de-b45dee07b711/windows6.1-kb3154518-x64.msu)
    
    >[!NOTE]
    > W tym artykule założono, że używasz serwerów opartych na standardzie x64 (agent MMA .exe wersji zgodnej z sha-2 x64).


**Krok 2. Tworzenie nazwy pliku DeployMMA.cmd (przy użyciu notatnika)** Dodaj następujące wiersze do pliku cmd. Pamiętaj, że potrzebujesz identyfikatora OBSZARU ROBOCZEGO i KLUCZA.

Poniżej przedstawiono przykładowe polecenie. Zamień następujące wartości:
- KB — użyj odpowiedniej bazy wiedzy dotyczącej punktu końcowego, który dołączasz
- Identyfikator obszaru roboczego i klucz — używanie identyfikatora i klucza


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





### <a name="group-policy-configuration"></a>zasady grupy konfiguracji

Utwórz nowe zasady grupy przeznaczone specjalnie dla urządzeń dołączających, takie jak "Microsoft Defender for Endpoint Onboarding".

- Tworzenie folderu zasady grupy o nazwie "c:\windows\MMA"

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="foldery":::

    **Spowoduje to dodanie nowego folderu na każdym serwerze, na którym będzie zastosowany serwer GPO o nazwie MMA, i będzie przechowywany w folderze c:\windows. Będzie to dotyczyć plików instalacyjnych do obsługi wiadomości MMA, wymagań wstępnych i skryptu instalacji.**

- Utwórz preferencję zasady grupy plików dla każdego pliku przechowywanego w logiie sieci.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="obraz zasad grupy1":::

Kopiuje ona pliki z domeny\NETLOGON\MMA\nazwa_pliku do C:\windows\MMA\nazwa_pliku, więc pliki instalacyjne są lokalne **na serwerze**:

:::image type="content" source="images/deploymma.png" alt-text="wdrażanie polecenia cmd mma":::

Powtórz ten proces, ale utwórz element docelowy na karcie COMMON, więc plik zostanie skopiowany tylko do odpowiedniej platformy/systemu operacyjnego w zakresie:

:::image type="content" source="images/targeteditor.png" alt-text="edytor docelowy":::

W Windows Server 2008 R2 potrzebujesz (a następnie skopiuje tylko) następujące elementy:
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


Gdy to zrobisz, musisz utworzyć zasady skryptu uruchamiania:

:::image type="content" source="images/startupprops.png" alt-text="właściwości uruchamiania":::

Nazwa pliku, który ma zostać uruchomiony w tym miejscu, to c:\windows\MMA\DeployMMA.cmd.
Po ponownym uruchomieniu serwera w ramach procesu uruchamiania zainstaluje aktualizację kb do obsługi klienta i telemetrii diagnostycznej, a następnie zainstaluje agenta MMA, ustawiając identyfikator obszaru roboczego i klucz, a serwer zostanie uruchomiony.

Jeśli nie chcesz **ponownie uruchamiać** wszystkich serwerów, możesz także użyć natychmiastowego zadania w celu uruchomienia wdrożenia poleceniaMMA.cmd.

Można to zrobić w dwóch fazach. Najpierw utwórz **pliki i folder** w zakładzie zasad grupy — uślij czas systemowy na zastosowanie zasad grupy, a wszystkie serwery mają pliki instalacji. Następnie dodaj natychmiastowe zadanie. Dzięki temu taki sam wynik będzie taki sam bez konieczności ponownego rozruchu.

Ponieważ skrypt ma metodę wyjścia i nie można go ponownie uruchomić, jeśli program MMA jest zainstalowany, ten sam wynik możesz także uzyskać za pomocą zaplanowanego dziennego zadania. Podobnie jak w Menedżer konfiguracji zgodności sprawdza ona codziennie w celu zapewnienia, że mma jest obecne.

:::image type="content" source="images/schtask.png" alt-text="zaplanuj zadanie":::

:::image type="content" source="images/newtaskprops.png" alt-text="nowe właściwości zadania":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="wdrażanie wiadomości mma do pobrania":::

:::image type="content" source="images/tasksch.png" alt-text="harmonogram zadań":::

Jak wspomniano w dokumentacji dotyczącej dołączania do programu Server konkretnie wokół programu Server 2008 R2, zobacz poniżej: W przypadku programu Windows Server 2008 R2 z dodatkiem SP1 upewnij się, że spełniasz następujące wymagania:

- Instalowanie pakietu zb. aktualizacji miesięcznej z lutego [2018 r.](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- Instalowanie programu [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (lub nowszego) albo [aktualizacji KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

Sprawdź, czy kb/s są obecne przed rozpoczęciem Windows Server 2008 R2. Ten proces umożliwia ci włocie wszystkich serwerów, jeśli nie masz dostępu do zarządzania Menedżer konfiguracji Serwerami.


## <a name="offboard-endpoints"></a>Punkty końcowe aplikacji Offboard

Dostępne są dwie opcje Windows punktów końcowych z usługi:

- Odinstalowywanie agenta MMA
- Usuwanie konfiguracji obszaru roboczego programu Defender for Endpoint

> [!NOTE]
> Wynoszenie powoduje, Windows punkt końcowy przestaje wysyłać dane czujnika do portalu, ale dane z tego punktu końcowego, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie 6 miesięcy.

### <a name="uninstall-the-mma-agent"></a>Odinstalowywanie agenta MMA

Aby usunąć punkt Windows punkt końcowy, możesz odinstalować agenta MMA lub odłączyć go od raportowania w obszarze roboczym programu Defender for Endpoint. Po wy dostępie do agenta punkt końcowy nie będzie już przesyłał danych czujnika do usługi Defender for Endpoint.
Aby uzyskać więcej informacji, zobacz [Aby wyłączyć agenta](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>Usuwanie konfiguracji obszaru roboczego programu Defender for Endpoint

Możesz użyć jednej z następujących metod:

- Usuwanie konfiguracji obszaru roboczego programu Defender for Endpoint z agenta MMA
- Uruchamianie polecenia programu PowerShell w celu usunięcia konfiguracji

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>Usuwanie konfiguracji obszaru roboczego programu Defender for Endpoint z agenta MMA

1. W **oknie Microsoft Monitoring Agent** wybierz **kartę Azure Log Analytics (OMS**).

2. Wybierz obszar roboczy Defender for Endpoint i kliknij pozycję **Usuń**.

    ![Obraz Microsoft Monitoring Agent właściwości](images/atp-mma.png)

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>Uruchamianie polecenia programu PowerShell w celu usunięcia konfiguracji

1. Uzyskaj identyfikator obszaru roboczego:

   1. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Onboarding**.

   1. Wybierz odpowiedni system operacyjny i uzyskaj identyfikator obszaru roboczego.

    
2. Otwórz program PowerShell o podwyższonym poziomie uprawnień i uruchom następujące polecenie. Użyj uzyskanego identyfikatora obszaru roboczego i zastąpienia go `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
