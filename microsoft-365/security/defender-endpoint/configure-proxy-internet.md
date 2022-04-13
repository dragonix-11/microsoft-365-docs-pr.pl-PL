---
title: Konfigurowanie ustawień serwera proxy urządzenia i połączenia internetowego
description: Skonfiguruj ustawienia serwera proxy Ochrona punktu końcowego w usłudze Microsoft Defender i Internetu, aby umożliwić komunikację z usługą w chmurze.
keywords: konfigurowanie, serwer proxy, Internet, łączność z Internetem, ustawienia, ustawienia serwera proxy, netsh, winhttp, serwer proxy
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
ms.openlocfilehash: 787da143bdbbc2d21610ba14d0fe7c955e4e976d
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823405"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Czujnik usługi Defender for Endpoint wymaga, aby usługa Microsoft Windows HTTP (WinHTTP) zgłaszała dane czujników i komunikowała się z usługą Defender for Endpoint. Osadzony czujnik usługi Defender for Endpoint działa w kontekście systemu przy użyciu konta LocalSystem. Czujnik korzysta z usług Http Services firmy Microsoft Windows (WinHTTP), aby umożliwić komunikację z usługą w chmurze Defender for Endpoint.

> [!TIP]
> W przypadku organizacji korzystających z serwerów proxy przesyłania dalej jako bramy do Internetu można użyć ochrony sieci w celu [zbadania zdarzeń połączenia występujących za serwerami proxy.](investigate-behind-proxy.md)

Ustawienie konfiguracji WinHTTP jest niezależne od ustawień serwera proxy przeglądania Windows Internet (WinINet) (zobacz [WinINet a WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). Serwer proxy można odnajdywać tylko przy użyciu następujących metod odnajdywania:

- Metody wykrywania automatycznego:

  - Przezroczysty serwer proxy
  
  - Protokół automatycznego odnajdywania serwera proxy sieci Web (WPAD)

    > [!NOTE]
    > Jeśli używasz przezroczystego serwera proxy lub WPAD w topologii sieci, nie potrzebujesz specjalnych ustawień konfiguracji. Aby uzyskać więcej informacji na temat wykluczeń adresu URL punktu końcowego usługi Defender na serwerze proxy, zobacz [Włączanie dostępu do adresów URL usługi Defender for Endpoint na serwerze proxy](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- Ręczna konfiguracja statycznego serwera proxy:

  - Konfiguracja oparta na rejestrze
  
  - WinHTTP skonfigurowany przy użyciu polecenia netsh: nadaje się tylko dla komputerów stacjonarnych w stabilnej topologii (na przykład: pulpit w sieci firmowej za tym samym serwerem proxy)

> [!NOTE]
> Oprogramowanie antywirusowe Defender i serwery proxy EDR można ustawić niezależnie.  W poniższych sekcjach należy pamiętać o tych różnicach.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Ręczne konfigurowanie serwera proxy przy użyciu statycznego serwera proxy opartego na rejestrze

Skonfiguruj oparty na rejestrze statyczny serwer proxy dla czujnika wykrywania i reagowania punktu końcowego usługi Defender (EDR), aby raportować dane diagnostyczne i komunikować się z usługą Defender for Endpoint, jeśli komputer nie może łączyć się z Internetem.

> [!NOTE]
> W przypadku korzystania z tej opcji na Windows 10, Windows 11 lub Windows Server 2019 lub Windows Server 2022 zaleca się utworzenie następującego (lub nowszego) zbiorczego zestawienia aktualizacji:
>
> - Windows 11
> - Windows 10, wersja 1809 lub Windows Server 2019 lub Windows Server 2022 —<https://support.microsoft.com/kb/5001384>
> - Windows 10, wersja 1909 —<https://support.microsoft.com/kb/4601380>
> - Windows 10, wersja 2004 —<https://support.microsoft.com/kb/4601382>
> - Windows 10, wersja 20H2 —<https://support.microsoft.com/kb/4601382>
>
> Te aktualizacje zwiększają łączność i niezawodność kanału CnC (Command and Control).

Statyczny serwer proxy można skonfigurować za pomocą zasad grupy (GP), oba ustawienia w obszarze wartości zasad grupy powinny być skonfigurowane na serwerze proxy na potrzeby korzystania z EDR. Zasady grupy są dostępne w szablonach administracyjnych.

- **Szablony administracyjne > Windows składniki > zbieranie danych i kompilacje w wersji zapoznawczej > konfigurowania uwierzytelnionego użycia serwera proxy dla połączonego środowiska użytkownika i usługi telemetrii**.

  Ustaw ją na **wartość Włączone** i wybierz pozycję **Wyłącz użycie uwierzytelnionego serwera proxy**.

  :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Okienko stanu ustawienia zasady grupy 1" lightbox="images/atp-gpo-proxy1.png":::

- **Szablony administracyjne > Windows składniki > zbieranie danych i kompilacje wersji zapoznawczej > Konfigurowanie środowisk i telemetrii połączonych użytkowników**:

  Skonfiguruj serwer proxy.

  :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Okienko stanu zasady grupy setting2" lightbox="images/atp-gpo-proxy2.png":::


| Zasady grupy | Klucz rejestru | Wpis rejestru | Value |
|:---|:---|:---|:---|
| Konfigurowanie uwierzytelnionego użycia serwera proxy dla środowiska połączonego użytkownika i usługi telemetrii | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| Konfigurowanie środowisk i danych telemetrycznych połączonych użytkowników | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> Na przykład: ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>Konfigurowanie statycznego serwera proxy dla Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender [ochrona dostarczana przez chmurę](cloud-protection-microsoft-defender-antivirus.md) zapewnia niemal natychmiastową, zautomatyzowaną ochronę przed nowymi i pojawiającym się zagrożeniami. Uwaga: łączność jest wymagana dla [niestandardowych wskaźników](manage-indicators.md) , gdy program antywirusowy Defender jest aktywnym rozwiązaniem chroniącym przed złośliwym oprogramowaniem. W przypadku [EDR w trybie bloku](edr-in-block-mode.md) jest używane podstawowe rozwiązanie chroniące przed złośliwym oprogramowaniem w przypadku korzystania z rozwiązania innego niż Microsoft.

Skonfiguruj statyczny serwer proxy przy użyciu zasady grupy dostępnych w szablonach administracyjnych:

1. **Szablony administracyjne > Windows Składniki > Program antywirusowy Microsoft Defender > Definiowanie serwera proxy na potrzeby nawiązywania połączenia z siecią**. 

2. Ustaw ją na **wartość Włączone** i zdefiniuj serwer proxy. Należy pamiętać, że adres URL musi mieć http:// lub https://. Aby uzyskać informacje o obsługiwanych wersjach https://, zobacz [Manage Program antywirusowy Microsoft Defender updates (Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md)).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="Serwer proxy dla Program antywirusowy Microsoft Defender" lightbox="images/proxy-server-mdav.png":::

3. W kluczu rejestru `HKLM\Software\Policies\Microsoft\Windows Defender`zasady ustawiają wartość `ProxyServer` rejestru jako REG_SZ. 

   Wartość `ProxyServer` rejestru przyjmuje następujący format ciągu:

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> W celu zapewnienia odporności i w czasie rzeczywistym ochrony dostarczanej przez chmurę Program antywirusowy Microsoft Defender będzie buforować ostatni znany działający serwer proxy. Upewnij się, że rozwiązanie serwera proxy nie przeprowadza inspekcji protokołu SSL. Spowoduje to przerwanie bezpiecznego połączenia w chmurze. 
>
> Program antywirusowy Microsoft Defender nie będzie używać statycznego serwera proxy do nawiązywania połączenia z usługą Windows Update lub Microsoft Update w celu pobierania aktualizacji. Zamiast tego będzie używać serwera proxy dla całego systemu, jeśli zostanie skonfigurowany do używania Windows Update lub skonfigurowanego wewnętrznego źródła aktualizacji zgodnie ze [skonfigurowaną kolejnością rezerwową](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> W razie potrzeby możesz użyć **szablonów administracyjnych > Windows Components > Program antywirusowy Microsoft Defender > Define proxy auto-config (.pac)** do nawiązywania połączenia z siecią. Jeśli musisz skonfigurować zaawansowane konfiguracje z wieloma serwerami proxy, użyj **szablonów administracyjnych > Windows components > Program antywirusowy Microsoft Defender > Define addresses (Definiowanie adresów**), aby pominąć serwer proxy i zapobiec Program antywirusowy Microsoft Defender  z użyciem serwera proxy dla tych miejsc docelowych. 
>
> Aby skonfigurować następujące opcje, możesz użyć programu PowerShell z `Set-MpPreference` poleceniem cmdlet: 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - Serwer proxy 

> [!NOTE]
> Aby prawidłowo używać serwera proxy, skonfiguruj te trzy różne ustawienia serwera proxy:
>  - Ochrona punktu końcowego w usłudze Microsoft Defender (MDE)
>  - AV (oprogramowanie antywirusowe)
>  - Wykrywanie i reagowanie na punkty końcowe (EDR)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Ręczne konfigurowanie serwera proxy przy użyciu polecenia netsh

Za pomocą programu netsh skonfiguruj statyczny serwer proxy w całym systemie.

> [!NOTE]
>
> - Będzie to miało wpływ na wszystkie aplikacje, w tym usługi Windows korzystające z usługi WinHTTP z domyślnym serwerem proxy.</br>
> - Laptopy zmieniające topologię (na przykład z biura do domu) będą działać nieprawidłowo za pomocą polecenia netsh. Użyj konfiguracji statycznego serwera proxy opartego na rejestrze.

1. Otwórz wiersz polecenia z podwyższonym poziomem poziomu:
   1. Przejdź do **pozycji Start** i wpisz **cmd**.
   1. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij **klawisz Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Na przykład: `netsh winhttp set proxy 10.0.0.6:8080`

Aby zresetować serwer proxy winhttp, wprowadź następujące polecenie i naciśnij **klawisz Enter**:

```PowerShell
netsh winhttp reset proxy
```

Aby dowiedzieć się więcej [, zobacz Składnia poleceń netsh, konteksty i formatowanie](/windows-server/networking/technologies/netsh/netsh-contexts) .

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>Włączanie dostępu do adresów URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender na serwerze proxy

Domyślnie, jeśli serwer proxy lub zapora domyślnie blokuje cały ruch i zezwala tylko na określone domeny, dodaj domeny wymienione w arkuszu do pobrania do listy dozwolonych domen.

W poniższym arkuszu kalkulacyjnym do pobrania wymieniono usługi i skojarzone z nimi adresy URL, z którymi sieć musi być w stanie nawiązać połączenie. Upewnij się, że nie ma reguł filtrowania zapory ani sieci, aby odmówić dostępu dla tych adresów URL. Opcjonalnie może być konieczne utworzenie reguły *zezwalania* specjalnie dla nich.

<br>

|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów komercyjnych| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender gov/GCC/doD | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów Gov/GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Jeśli serwer proxy lub zapora ma włączoną funkcję skanowania HTTPS (inspekcja SSL), wyklucz domeny wymienione w powyższej tabeli ze skanowania HTTPS.
W zaporze otwórz wszystkie adresy URL, w których kolumna geografii to WW. W przypadku wierszy, w których kolumna geografii nie jest WW, otwórz adresy URL w określonej lokalizacji danych. Aby zweryfikować ustawienie lokalizacji danych, zobacz [Weryfikowanie lokalizacji magazynu danych i aktualizowanie ustawień przechowywania danych dla Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows urządzeń z wersją 1803 lub starszą wymaga .`settings-win.data.microsoft.com`  <br>
>
> Adresy URL, które zawierają w nich wersję 20, są potrzebne tylko wtedy, gdy masz Windows urządzenia w wersji 1803 lub nowszej. Na przykład `us-v20.events.data.microsoft.com` jest to wymagane dla urządzenia Windows w wersji 1803 lub nowszej i dołączone do regionu us Data Storage.
>

Jeśli serwer proxy lub zapora blokuje ruch anonimowy jako czujnik usługi Defender for Endpoint i nawiązuje połączenie z kontekstu systemu, aby upewnić się, że ruch anonimowy jest dozwolony we wcześniej wymienionych adresach URL.

> [!NOTE]
> Firma Microsoft nie udostępnia serwera proxy. Te adresy URL są dostępne za pośrednictwem skonfigurowanego serwera proxy.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) — wymagania dotyczące serwera proxy i zapory dla starszych wersji klienta Windows lub serwera Windows

Informacje na liście informacji o konfiguracji serwera proxy i zapory są wymagane do komunikowania się z agentem usługi Log Analytics (często nazywanym Microsoft Monitoring Agent) dla poprzednich wersji Windows, takich jak Windows 7 z dodatkiem SP1, Windows 8.1 i Windows Server 2008 R2*.

<br>

****

|Zasoby agenta|Porty|Kierunek|Pomijanie inspekcji HTTPS|
|---|---|---|---|
|*.ods.opinsights.azure.com|Port 443|Wychodzące|Tak|
|*.oms.opinsights.azure.com|Port 443|Wychodzące|Tak|
|*.blob.core.windows.net|Port 443|Wychodzące|Tak|
|*.azure-automation.net|Port 443|Wychodzące|Tak|

> [!NOTE]
> *Te wymagania dotyczące łączności dotyczą poprzednich Ochrona punktu końcowego w usłudze Microsoft Defender Windows Server 2016 i Windows Server 2012 R2, które wymagają mma. Instrukcje dotyczące dołączania tych systemów operacyjnych do nowego ujednoliconego rozwiązania znajdują się na [stronie Dołączanie serwerów Windows](configure-server-endpoints.md) lub migrowanie do nowego ujednoliconego rozwiązania w [scenariuszach migracji serwera w Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Jako rozwiązanie oparte na chmurze zakres adresów IP może ulec zmianie. Zalecane jest przejście do ustawienia rozpoznawania dns.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Potwierdzanie wymagań dotyczących adresu URL usługi Microsoft Monitoring Agent (MMA) 

 Zapoznaj się z poniższymi wskazówkami, aby wyeliminować wymaganie dotyczące symboli wieloznacznych (*) dla określonego środowiska podczas korzystania z Microsoft Monitoring Agent (MMA) dla poprzednich wersji Windows.

1. Dołącz poprzedni system operacyjny z Microsoft Monitoring Agent (MMA) do usługi Defender for Endpoint (aby uzyskać więcej informacji, zobacz [Dołączanie poprzednich wersji Windows w usłudze Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2010326) i [Dołączanie serwerów Windows](configure-server-endpoints.md)).

2. Upewnij się, że maszyna pomyślnie zgłasza się do portalu Microsoft 365 Defender.

3. Uruchom narzędzie TestCloudConnection.exe z folderu "C:\Program Files\Microsoft Monitoring Agent\Agent", aby zweryfikować łączność i uzyskać wymagane adresy URL dla określonego obszaru roboczego.

4. Sprawdź listę adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać pełną listę wymagań dotyczących danego regionu (zapoznaj się z [arkuszem kalkulacyjnym](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx) adresów URL usługi).

   :::image type="content" source="images/admin-powershell.png" alt-text="Administrator w Windows PowerShell" lightbox="images/admin-powershell.png":::

Symbole wieloznaczne (\*) używane w \*punktach końcowych .ods.opinsights.azure.com, \*.oms.opinsights.azure.com i \*.agentsvc.azure-automation.net URL można zastąpić określonym identyfikatorem obszaru roboczego. Identyfikator obszaru roboczego jest specyficzny dla środowiska i obszaru roboczego. Można go znaleźć w sekcji Dołączanie dzierżawy w portalu Microsoft 365 Defender.

\*Punkt końcowy adresu URL blob.core.windows.net można zastąpić adresami URL wyświetlanymi w sekcji "Reguła zapory: \*.blob.core.windows.net" wyników testu.

> [!NOTE]
> W przypadku dołączania za pośrednictwem Microsoft Defender dla Chmury można użyć wielu obszarów roboczych. Należy wykonać procedurę TestCloudConnection.exe na dołączonym komputerze z każdego obszaru roboczego (aby ustalić, czy istnieją jakiekolwiek zmiany adresów URL *.blob.core.windows.net między obszarami roboczymi).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Weryfikowanie łączności klienta z adresami URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender

Sprawdź, czy konfiguracja serwera proxy została pomyślnie ukończona. Następnie usługa WinHTTP może odnajdywać i komunikować się za pośrednictwem serwera proxy w danym środowisku, a następnie serwer proxy zezwoli na ruch do adresów URL usługi Defender for Endpoint.

1. Pobierz [narzędzie Ochrona punktu końcowego w usłudze Microsoft Defender Client Analyzer](https://aka.ms/mdeanalyzer) na komputer, na którym działa czujnik usługi Defender for Endpoint. W przypadku serwerów o niskiej wydajności użyj najnowszej wersji zapoznawczej, która jest dostępna do pobrania [Ochrona punktu końcowego w usłudze Microsoft Defender narzędzia Client Analyzer w wersji beta](https://aka.ms/BetaMDEAnalyzer).

2. Wyodrębnij zawartość MDEClientAnalyzer.zip na urządzeniu.

3. Otwórz wiersz polecenia z podwyższonym poziomem poziomu:
   1. Przejdź do **pozycji Start** i wpisz **cmd**.
   1. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

4. Wprowadź następujące polecenie i naciśnij **klawisz Enter**:

    ```PowerShell
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    Zastąp ciąg *HardDrivePath* ścieżką, w której pobrano narzędzie MDEClientAnalyzer. Przykład:

    ```PowerShell
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. Narzędzie tworzy i wyodrębnia plik *MDEClientAnalyzerResult.zip* w folderze do użycia w programie *HardDrivePath*.

6. Otwórz *MDEClientAnalyzerResult.txt* i sprawdź, czy wykonano kroki konfiguracji serwera proxy, aby umożliwić odnajdywanie serwerów i dostęp do adresów URL usługi.

   Narzędzie sprawdza łączność adresów URL usługi Defender for Endpoint. Upewnij się, że klient usługi Defender for Endpoint jest skonfigurowany do interakcji. Narzędzie wyświetli wyniki w pliku *MDEClientAnalyzerResult.txt* dla każdego adresu URL, który może być potencjalnie używany do komunikowania się z usługami Defender for Endpoint. Przykład:

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Jeśli którakolwiek z opcji łączności zwraca stan (200), klient usługi Defender for Endpoint może prawidłowo komunikować się z przetestowanym adresem URL przy użyciu tej metody łączności.

Jeśli jednak wyniki sprawdzania łączności wskazują na błąd, zostanie wyświetlony błąd HTTP (zobacz Kody stanu HTTP). Następnie możesz użyć adresów URL w tabeli przedstawionej w temacie [Enable access to Defender for Endpoint service URLLs in the proxy server (Włącz dostęp do adresów URL usługi Defender for Endpoint service na serwerze proxy](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)). Adresy URL dostępne do użycia zależą od regionu wybranego podczas procedury dołączania.

> [!NOTE]
> Testy łączności narzędzia Analizator łączności w chmurze nie są zgodne z tworzeniem procesów bloku reguły zmniejszania obszaru podatnego na ataki [pochodzącymi z poleceń PSExec i WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands). Aby uruchomić narzędzie łączności, należy tymczasowo wyłączyć tę regułę. Alternatywnie można tymczasowo dodać [wykluczenia usługi ASR](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) podczas uruchamiania analizatora.
>
> Gdy parametr TelemetryProxyServer jest ustawiony w rejestrze lub za pośrednictwem zasady grupy, usługa Defender dla punktu końcowego powróci, nie będzie uzyskiwać dostępu do zdefiniowanego serwera proxy.

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfigurowanie Program antywirusowy Microsoft Defender i zarządzanie nimi przy użyciu ustawień zasady grupy](use-group-policy-microsoft-defender-antivirus.md)
- [Dołączanie urządzeń Windows](configure-endpoints.md)
- [Rozwiązywanie problemów z dołączaniem Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-onboarding.md)
