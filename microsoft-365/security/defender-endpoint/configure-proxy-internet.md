---
title: Konfigurowanie ustawień serwera proxy i połączenia internetowego urządzenia
description: Skonfiguruj ustawienia serwera proxy i Internetu programu Microsoft Defender dla punktu końcowego, aby umożliwić komunikację z usługą w chmurze.
keywords: configure, proxy, internet, łączność z Internetem, ustawienia, ustawienia serwera proxy, netsh, winhttp, serwer proxy
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d687273a3029f3de080f06f328d4d40853142353
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014884"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Czujnik Defender for Endpoint wymaga, aby program Microsoft Windows HTTP (WinHTTP) do zgłaszania danych czujnika i komunikowania się z usługą Defender for Endpoint. Osadzony czujnik programu Defender for Endpoint działa w kontekście systemowym przy użyciu konta LocalSystem. Czujnik korzysta z usług Microsoft Windows HTTP (WinHTTP) w celu umożliwienia komunikacji z usługą w chmurze Defender for Endpoint.

> [!TIP]
> W organizacjach, które używają serwerów proxy przesyłania dalej jako bramy do Internetu, możesz użyć ochrony sieci w celu zbadania zdarzeń połączenia, które występują za serwerami [proxy przesyłania dalej](investigate-behind-proxy.md).

Ustawienie konfiguracji WinHTTP jest niezależne od ustawień serwera proxy przeglądania sieci Windows Internet (WinINet) (zobacz: [WinINet vs. WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). Serwer proxy można odnajdywać tylko przy użyciu następujących metod odnajdowania:

- Metody wykrywania automatycznego:

  - Przezroczysty serwer proxy
  
  - WPAD (Web Proxy Auto-discovery Protocol)

    > [!NOTE]
    > Jeśli używasz przezroczystego serwera proxy lub tabletu WPAD w topologii sieci, nie potrzebujesz specjalnych ustawień konfiguracji. Aby uzyskać więcej informacji na temat usługi Defender dla wykluczeń adresu URL punktu końcowego w serwerze proxy, zobacz Włączanie dostępu do usługi Defender dla adresów URL usługi punktu końcowego [na serwerze proxy.](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- Ręczna statyczna konfiguracja serwera proxy:

  - Konfiguracja oparta na rejestrze
  
  - WinHTTP configured using netsh command: Suitable only for desktops in a stable topology (example: a desktop in a corporate network behind the same proxy)

> [!NOTE]
> Oprogramowanie antywirusowe Defender i EDR można ustawić niezależnie.  W kolejnych sekcjach należy pamiętać o różnicach.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Ręczne konfigurowanie serwera proxy przy użyciu statycznego serwera proxy opartego na rejestrze

Skonfiguruj statyczny serwer proxy oparty na rejestrze dla czujnika wykrywania i reakcji punktu końcowego (EDR) oparty na rejestrze, aby raportować dane diagnostyczne i komunikować się z usługą Defender for Endpoint, jeśli komputer nie jest dozwolony do łączenia się z Internetem.

> [!NOTE]
> W przypadku używania tej opcji w programie Windows 10, Windows 11 lub Windows Server 2019 albo Windows Server 2022 zaleca się używanie następującej (lub nowszej) kompilacji i zbiorczego rzutu aktualizacji:
>
> - Windows 11
> - Windows 10, wersja 1809 lub Windows Server 2019 lub Windows Server 2022 —<https://support.microsoft.com/kb/5001384>
> - Windows 10, wersja 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10, wersja 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10, wersja 20H2 -<https://support.microsoft.com/kb/4601382>
>
> Te aktualizacje poprawiają łączność i niezawodność kanału CnC (Command and Control).

Statyczny serwer proxy można skonfigurować za pośrednictwem zasad grupy (GP), oba ustawienia w obszarze wartości zasad grupy należy skonfigurować na serwerze proxy do używania EDR. Zasady grupy są dostępne w szablonach administracyjnych.

- **Szablony administracyjne > Windows składniki >** i kompilacje zbierania danych w wersji Preview > Konfigurowanie uwierzytelnionego użycia serwera proxy dla połączonego interfejsu użytkownika i usługi telemetrii.

  Ustaw dla ustawienia **Włączone i** wybierz **pozycję Wyłącz uwierzytelniony serwer proxy**.

  ![Obraz zasady grupy ustawienie1.](images/atp-gpo-proxy1.png)

- **Szablony administracyjne > Windows składników > kompilacji** zbierania i podglądu danych oraz > konfigurowanie połączonych funkcji użytkownika i telemetrii:

  Skonfiguruj serwer proxy.

  ![Obraz zasady grupy ustawienie2.](images/atp-gpo-proxy2.png)


| zasady grupy | Klucz rejestru | Wpis rejestru | Value |
|:---|:---|:---|:---|
| Konfigurowanie uwierzytelnionego użycia serwera proxy dla połączonego interfejsu użytkownika i usługi telemetrii | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| Konfigurowanie połączonych usług użytkownika i telemetrii | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> Na przykład: ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>Konfigurowanie statycznego serwera proxy dla Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender [dostarczana w](cloud-protection-microsoft-defender-antivirus.md) chmurze ochrona zapewnia natychmiastową, automatyczną ochronę przed nowymi i wyłaniających się zagrożeniami. Pamiętaj, że łączność jest wymagana dla [wskaźników niestandardowych,](manage-indicators.md) gdy program antywirusowy Defender jest aktywnym rozwiązaniem chroniącym przed złośliwym oprogramowaniem. Na [EDR trybie blokowania ma](edr-in-block-mode.md) podstawowe rozwiązanie chroniące przed złośliwym oprogramowaniem w przypadku używania rozwiązania innych niż firmy Microsoft.

Skonfiguruj statyczny serwer proxy przy użyciu zasady grupy dostępnych w szablonach administracyjnych:

1. **Szablony administracyjne > Windows składniki > Program antywirusowy Microsoft Defender > definiować serwer proxy do łączenia się z siecią**. 

2. Ustaw dla ustawienia **Włączone i** zdefiniuj serwer proxy. Adres URL musi być http:// lub https://. Aby uzyskać informacje o obsługiwanych https://, [zobacz Zarządzanie Program antywirusowy Microsoft Defender aktualizacjami](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="Serwer proxy dla Program antywirusowy Microsoft Defender.":::

3. W obszarze klucza rejestru `HKLM\Software\Policies\Microsoft\Windows Defender`zasady ustawiają wartość rejestru `ProxyServer` jako REG_SZ. 

   Wartość rejestru przyjmuje `ProxyServer` następujący format ciągu:

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> Ze względu na odporność i ze względu na charakter ochrony w chmurze w czasie rzeczywistym Program antywirusowy Microsoft Defender buforuje ostatni znany roboczy serwer proxy. Upewnij się, że rozwiązanie serwera proxy nie przeprowadza inspekcji SSL. Spowoduje to zerwanie bezpiecznego połączenia z chmurą. 
>
> Program antywirusowy Microsoft Defender nie będzie używać statycznego serwera proxy do łączenia się z usługą Windows Update ani usługą Microsoft Update w celu pobrania aktualizacji. Zamiast tego będzie używać serwera proxy dla całego systemu( jeśli skonfigurowano go do korzystania z usługi Windows Update) lub skonfigurowanego wewnętrznego źródła aktualizacji zgodnie ze skonfigurowaną kolejnością [rezerwową](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> Jeśli jest to wymagane, możesz użyć szablonów **administracyjnych > Windows składników > Program antywirusowy Microsoft Defender > definiowania automatycznej konfiguracji serwera proxy (pac)** na potrzeby łączenia się z siecią. Jeśli musisz skonfigurować zaawansowane konfiguracje z wieloma serwerami proxy, użyj szablonów **administracyjnych > Windows składniki > Program antywirusowy Microsoft Defender > Definiuj** adresy, aby pominąć serwer proxy i zapobiec Program antywirusowy Microsoft Defender  z używania serwera proxy dla tych miejsc docelowych. 
>
> Za pomocą programu PowerShell i polecenia `Set-MpPreference` cmdlet możesz skonfigurować następujące opcje: 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - ProxyServer (Serwer proxy) 

> [!NOTE]
> Aby prawidłowo korzystać z serwera proxy, skonfiguruj następujące trzy różne ustawienia serwera proxy:
>  - Microsoft Defender for Endpoint (MDE)
>  - AUDIO/wideo (oprogramowanie antywirusowe)
>  - Wykrywanie i odpowiedź punktu końcowego (EDR)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Ręczne konfigurowanie serwera proxy przy użyciu polecenia netsh

Za pomocą metody netsh skonfiguruj statyczny serwer proxy dla całego systemu.

> [!NOTE]
>
> - Dotyczy to wszystkich aplikacji, w tym usług Windows, które korzystają z winHTTP z domyślnym serwerem proxy.</br>
> - Komputery przenośne, które zmieniają topologię (na przykład: z biura do domu) zostaną niepoprawnie niepoprawne przy użyciu polecenia Netsh. Użyj statycznej konfiguracji serwera proxy opartej na rejestrze.

1. Otwieranie wiersza polecenia z podwyższonym poziomem uprawnień:
   1. Przejdź do **przycisku Start** i wpisz **cmd**.
   1. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Na przykład: `netsh winhttp set proxy 10.0.0.6:8080`

Aby zresetować serwer proxyhttp win, wprowadź następujące polecenie i naciśnij klawisz **Enter**:

```PowerShell
netsh winhttp reset proxy
```

Aby [dowiedzieć się więcej, zobacz Składnia poleceń Netsh, konteksty](/windows-server/networking/technologies/netsh/netsh-contexts) i formatowanie.

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>Włączanie dostępu do programu Microsoft Defender dla adresów URL usługi punktu końcowego na serwerze proxy

Jeśli domyślnie cały ruch jest blokowany przez serwer proxy lub zaporę i dopuszcza tylko określone domeny, dodaj domeny wymienione w arkuszu do pobrania do listy dozwolonych domen.

Poniższy arkusz kalkulacyjny zawiera listę usług i skojarzonych z nimi adresów URL, które sieć musi połączyć. Upewnij się, że nie ma żadnych reguł zapory ani filtrowania sieci, aby uniemożliwić dostęp do tych adresów URL. Opcjonalnie może być konieczne utworzenie reguły *zezwalania* specjalnie dla nich.

<br>

**** 
|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|Lista adresów URL punktu końcowego programu Microsoft Defender dla klientów komercyjnych| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Lista adresów URL programu Microsoft Defender dla punktów końcowych dla klientów GCC/DoD | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Jeśli serwer proxy lub zapora ma włączoną funkcję skanowania HTTPS (inspekcji SSL), wyklucz z funkcji skanowania HTTPS domeny wymienione w powyższej tabeli.
W zaporze otwórz wszystkie adresy URL, których kolumna geografii to WW. W przypadku wierszy, w których kolumna geografii nie jest kolumną WW, otwórz adresy URL do konkretnej lokalizacji danych. Aby zweryfikować ustawienie lokalizacji danych, zobacz Weryfikowanie lokalizacji przechowywania danych i aktualizowanie ustawień przechowywania danych dla programu [Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows urządzeń z wersjami 1803 lub wcześniejszymi`settings-win.data.microsoft.com`.  <br>
>
> Adresy URL, które zawierają wersję 20, są potrzebne tylko, jeśli masz Windows z wersją 1803 lub nowszą. Jest ona potrzebna na przykład `us-v20.events.data.microsoft.com` w przypadku urządzenia Windows z wersją 1803 lub nowszą, które jest dołączane do Storage danych w USA.
>

Jeśli serwer proxy lub zapora blokuje ruch anonimowy jako czujnik programu Defender for Endpoint i łączy się on z kontekstu systemowego w celu upewnienia się, że ruch anonimowy jest dozwolony we wcześniej wymienionych adresach URL.

> [!NOTE]
> Firma Microsoft nie zapewnia serwera proxy. Te adresy URL są dostępne za pośrednictwem skonfigurowanego serwera proxy.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) — wymagania dotyczące serwera proxy i zapory dla starszych wersji Windows lub Windows Server

Informacje zawarte na liście informacji o konfiguracji serwera proxy i zapory są wymagane do komunikacji z agentem analizy dziennika (często określanej mianem Microsoft Monitoring Agent) poprzednich wersji programu Windows, takich jak Windows 7 SP1, Windows 8.1 i Windows Server 2008 R2*.

<br>

****

|Zasoby agenta|Porty|Kierunek|Pomijanie inspekcji HTTPS|
|---|---|---|---|
|*.ods.opinsights.azure.com|Port 443|Wychodzące|Tak|
|*.oms.opinsights.azure.com|Port 443|Wychodzące|Tak|
|*.blob.core.windows.net|Port 443|Wychodzące|Tak|
|*.azure-automation.net|Port 443|Wychodzące|Tak|

> [!NOTE]
> *Te wymagania dotyczące łączności mają zastosowanie do poprzedniej wersji programu Microsoft Defender dla punktu Windows Server 2016 i Windows Server 2012 R2, która wymaga programu MMA. Instrukcje dotyczące dołączania tych systemów operacyjnych do nowego, ujednoliconego rozwiązania znajdują się w witrynie [Onboard Windows servers (Wewnecie serwerów Windows](configure-server-endpoints.md)) lub migracji do nowego, ujednoliconego rozwiązania w scenariuszach migracji serwera w programie [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Jako rozwiązanie oparte na chmurze zakres adresów IP może się zmienić. Zalecane jest przejście do ustawienia rozpoznawania dns.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Potwierdź Microsoft Monitoring Agent adresu URL usługi MMA 

 Zobacz poniższe wskazówki, aby wyeliminować wymaganie używania symboli wieloznacznych (*) w określonym środowisku podczas korzystania Microsoft Monitoring Agent (MMA) dla poprzednich wersji Windows.

1. Wduń poprzedni system operacyjny z programem Microsoft Monitoring Agent (MMA) do programu Defender for Endpoint (aby uzyskać więcej informacji, zobacz Wdowe poprzednie wersje programu Windows na temat programu [Defender](https://go.microsoft.com/fwlink/p/?linkid=2010326) dla punktów końcowych i na nowych serwerach Windows [końcowych](configure-server-endpoints.md)).

2. Upewnij się, że komputer pomyślnie zgłasza się do Microsoft 365 Defender urządzenia.

3. Uruchom narzędzie TestCloudConnection.exe z folderu "C:\Program Files\Microsoft Monitoring Agent\Agent", aby zweryfikować łączność i uzyskać wymagane adresy URL dla określonego obszaru roboczego.

4. Na liście adresów URL punktów końcowych programu Microsoft Defender można znaleźć pełną listę wymagań dotyczących swojego regionu (zobacz Arkusz kalkulacyjny adresów URL [usługi](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)).

    ![Obraz administratora w programie Windows PowerShell.](images/admin-powershell.png)

Symbole wieloznaczne używane\*\* w punktach końcowych adresów URL ods.opinsights.azure.com, \*oms.opinsights.azure.com \*i agentsvc.azure-automation.net można zastąpić określonym identyfikatorem obszaru roboczego. Identyfikator obszaru roboczego jest określony dla danego środowiska i obszaru roboczego. Można go znaleźć w sekcji Dołączanie dzierżawy w portalu Microsoft 365 Defender sieci.

Punkt \*końcowy blob.core.windows.net URL można zastąpić adresami URL przedstawionymi w sekcji "Reguła zapory: \*blob.core.windows.net" wyników testu.

> [!NOTE]
> W przypadku dorównania za pomocą programu Microsoft Defender dla chmury można korzystać z wielu obszarów roboczych. Konieczne będzie wykonanie procedury TestCloudConnection.exe na wewnecie komputera z każdego obszaru roboczego (aby ustalić, czy między obszarami roboczymi występują jakieś zmiany w adresach URL *.blob.core.windows.net).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Weryfikowanie łączności klienta z adresami URL usługi Programu Microsoft Defender dla punktu końcowego

Sprawdź, czy konfiguracja serwera proxy została ukończona pomyślnie. WinHTTP może następnie wykrywać i komunikować się za pośrednictwem serwera proxy w Twoim środowisku, a następnie serwer proxy zezwala na ruch do adresów URL usługi Defender for Endpoint.

1. Pobierz narzędzie [Microsoft Defender for Endpoint Client Analyzer na](https://aka.ms/mdeanalyzer) komputer, na którym działa czujnik programu Defender for Endpoint. W przypadku serwerów o funkcjach serwerach o goniące niżej można pobrać program [Microsoft Defender for Endpoint Client Analyzer w wersji Beta, która jest dostępna do pobrania najnowszej wersji Preview](https://aka.ms/BetaMDEAnalyzer).

2. Wyodrębnianie zawartości MDEClientAnalyzer.zip na urządzeniu.

3. Otwieranie wiersza polecenia z podwyższonym poziomem uprawnień:
   1. Przejdź do **przycisku Start** i wpisz **cmd**.
   1. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

4. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

    ```PowerShell
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    Zastąp *ścieżkę HardDrivePath* ścieżką, do której pobrano narzędzie MDEClientAnalyzer. Przykład:

    ```PowerShell
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. Narzędzie tworzy i wyodrębnia plik *MDEClientAnalyzerResult.zip* w folderze do użycia w *programie HardDrivePath*.

6. Otwórz *MDEClientAnalyzerResult.txt* i upewnij się, że wykonano kroki konfiguracji serwera proxy w celu umożliwienia odnajdowania serwera i uzyskiwania dostępu do adresów URL usługi.

   Narzędzie sprawdza łączność usługi Defender pod adresami URL usługi punktu końcowego. Upewnij się, że klient usługi Defender for Endpoint jest skonfigurowany do interakcji. Narzędzie wydrukuje wyniki w pliku *MDEClientAnalyzerResult.txt* każdego adresu URL, który potencjalnie może zostać użyty do komunikacji z usługami Defender for Endpoint. Przykład:

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Jeśli którakolwiek z opcji łączności zwróci stan (200), wówczas klient programu Defender dla punktu końcowego może prawidłowo komunikować się z testowym adresem URL przy użyciu tej metody łączności.

Jeśli jednak wyniki kontroli łączności wskazują na awarię, zostanie wyświetlony błąd HTTP (zobacz Kody stanu PROTOKOŁU HTTP). Następnie możesz użyć adresów URL z tabeli przedstawionej w tece Włączanie dostępu do usługi Defender dla adresów URL usługi punktu końcowego [na serwerze proxy](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Adresy URL dostępne do użycia zależą od regionu wybranego podczas procedury dołączania.

> [!NOTE]
> Testy łączności narzędzia Analizator łączności z chmurą nie są zgodne z tworzeniem procesu blokowania zmniejszania powierzchni w przypadku ataków na produkty pochodzące z poleceń [PSExec i WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands). Aby uruchomić narzędzie łączności, należy tymczasowo wyłączyć tę regułę. Możesz również tymczasowo dodać wykluczenia [asr podczas](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) uruchamiania analizatora.
>
> Gdy telemetryczny serwer proxy zostanie ustawiony w rejestrze lub za pośrednictwem serwera zasady grupy, usługa Defender dla punktu końcowego zakończy się niepowodzeniem dostępu do zdefiniowanego serwera proxy.

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfigurowanie zasady grupy zarządzanie plikami Program antywirusowy Microsoft Defender i zarządzanie nimi zasady grupy](use-group-policy-microsoft-defender-antivirus.md)
- [Urządzenia Windows urządzeniach](configure-endpoints.md)
- [Rozwiązywanie problemów z dołączaniem do programu Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
