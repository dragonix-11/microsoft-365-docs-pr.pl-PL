---
title: Konfigurowanie ustawień serwera proxy urządzenia i połączenia internetowego w celu ochrony informacji
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Konfigurowanie ustawień serwera proxy urządzenia i połączenia internetowego w celu ochrony informacji
ms.openlocfilehash: 2d0bc6484636cffb479ccb96b3458fddf0697cd7
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013809"
---
# <a name="configure-device-proxy-and-internet-connection-settings-for-information-protection"></a>Konfigurowanie ustawień serwera proxy urządzenia i połączenia internetowego w celu ochrony informacji

Technologie punktu końcowego firmy Microsoft Windows http (WinHTTP) firmy Microsoft do zgłaszania danych i komunikowania się z usługą w chmurze punktu końcowego firmy Microsoft. Usługa osadzona działa w kontekście systemowym przy użyciu konta LocalSystem.

> [!TIP]
> W przypadku organizacji, które używają serwerów proxy przesyłania dalej jako bramy do Internetu, można użyć ochrony sieci w celu zbadania za serwerem proxy. Aby uzyskać więcej informacji, [zobacz Badanie zdarzeń połączenia, które występują za forward proxy](/windows/security/threat-protection/microsoft-defender-atp/investigate-behind-proxy).

Ustawienie konfiguracji WinHTTP jest niezależne od ustawień serwera proxy przeglądania Internetu Windows (WinINet) i może wykrywać tylko serwer proxy przy użyciu następujących metod wykrywania automatycznego:

- Przezroczysty serwer proxy
- WPAD (Web Proxy Auto-discovery Protocol)

> [!NOTE]
> Jeśli używasz przezroczystego serwera proxy lub tabletu WPAD w topologii sieci, nie potrzebujesz specjalnych ustawień konfiguracji. Aby uzyskać więcej informacji na temat wykluczeń adresu URL punktu końcowego w programie proxy, zobacz Włączanie dostępu do adresów URL usługi w chmurze [DLP na serwerze proxy](#enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server).

- Ręczna statyczna konfiguracja serwera proxy:
  - Konfiguracja oparta na rejestrze
  - WinHTTP skonfigurowane przy użyciu polecenia netsh — odpowiednie tylko dla komputerów stacjonarnych w stabilnej topologii (na przykład: komputer stacjonarny w sieci firmowej z tym samym serwerem proxy)

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Ręczne konfigurowanie serwera proxy przy użyciu statycznego serwera proxy opartego na rejestrze

W przypadku urządzeń końcowych, które nie są dozwolone do łączenia się z Internetem, musisz skonfigurować statyczny serwer proxy oparty na rejestrze. Musisz skonfigurować to tak, aby umożliwić raportom danych diagnostycznych i komunikowanie się z usługą w chmurze punktu końcowego firmy Microsoft tylko w przypadku punktów końcowych firmy Microsoft.

Statyczny serwer proxy można skonfigurować za pośrednictwem zasady grupy (GP). Zasady grupy można znaleźć w obszarze:

1. Otwieranie **szablonów administracyjnych > Windows składników > i** kompilacji zbierania i podglądu danych > Konfigurowanie uwierzytelnionego użycia serwera proxy dla połączonego interfejsu użytkownika i usługi telemetrii

2. Ustaw dla ustawienia **Włączone i** wybierz **pozycję Wyłącz uwierzytelniony serwer proxy**:

   ![Obraz ustawień zasad grupy 1.](../media/atp-gpo-proxy1.png)

3. Otwieranie szablonów administracyjnych > Windows składników > kompilacji zbierania i podglądu danych > Konfigurowanie połączonych **funkcji użytkownika i telemetrii**:

   Konfigurowanie serwera proxy

   ![Obraz ustawień zasad grupy 2.](../media/atp-gpo-proxy2.png)

   Zasady ustawiają dwie wartości `TelemetryProxyServer` rejestru jako REG_SZ i jako `DisableEnterpriseAuthProxy` REG_DWORD w ramach klucza rejestru `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

   Wartość rejestru TelemetryProxyServer jest w tym formacie \<server name or ip\>:\<port\>. Na przykład: **10.0.0.6:8080**

   Wartość rejestru powinna `DisableEnterpriseAuthProxy` być ustawiona na 1.

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Ręczne konfigurowanie serwera proxy przy użyciu polecenia "netsh"

Za pomocą metody netsh skonfiguruj statyczny serwer proxy dla całego systemu.

> [!NOTE]
> Dotyczy to wszystkich aplikacji, w tym usług Windows, które korzystają z winHTTP z domyślnym serwerem proxy. - Komputery przenośne, które zmieniają topologię (na przykład: z biura do domu) zostaną niepoprawnie niepoprawne przy użyciu oprogramowania Netsh. Użyj statycznej konfiguracji serwera proxy opartej na rejestrze.

1. Otwieranie wiersza polecenia z podwyższonym poziomem uprawnień:
    1. Przejdź do **przycisku Start** i wpisz **cmd**
    2. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   `netsh winhttp set proxy <proxy>:<port>`

   Na przykład: **netsh winhttp set proxy 10.0.0.6:8080**

3. Aby zresetować serwer proxyhttp win, wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   `netsh winhttp reset proxy`

Aby [dowiedzieć się więcej, zobacz Składnia poleceń Netsh, konteksty](/windows-server/networking/technologies/netsh/netsh-contexts) i formatowanie.

## <a name="enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server"></a>Włączanie dostępu do adresów URL usługi w chmurze DLP punktu końcowego na serwerze proxy

Jeśli serwer proxy lub zapora domyślnie blokuje cały ruch i zezwala na dostęp tylko do określonych domen, dodaj domeny wymienione w arkuszu do pobrania do listy dozwolonych domen.

Ten [arkusz kalkulacyjny do pobrania](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) zawiera listę usług i skojarzonych z nimi adresów URL, z których sieć musi być w stanie nawiązać połączenie. Należy upewnić się, że nie ma żadnych reguł zapory lub filtrowania sieci, które odmówią dostępu do tych adresów URL, lub może być konieczne utworzenie reguły zezwalania przeznaczonej specjalnie dla tych adresów URL.

Jeśli serwer proxy lub zapora ma włączoną funkcję skanowania HTTPS (inspekcji SSL), wyklucz z funkcji skanowania HTTPS domeny wymienione w powyższej tabeli.
Jeśli serwer proxy lub zapora blokuje ruch anonimowy, ponieważ ochrona DLP punktu końcowego łączy się z kontekstu systemowego, upewnij się, że ruch anonimowy jest dozwolony we wcześniej wymienionych adresach URL.

## <a name="verify-client-connectivity-to-microsoft-cloud-service-urls"></a>Weryfikowanie łączności klienta z adresami URL usług firmy Microsoft w chmurze

Sprawdź pomyślnie ukończoną konfigurację serwera proxy, czy usługa WinHTTP może wykrywać i komunikować się za pośrednictwem serwera proxy w Twoim środowisku oraz czy serwer proxy zezwala na ruch do adresów URL usługi Defender for Endpoint Service.

1. Pobierz narzędzie [analizatora klienta MDATP na](https://aka.ms/mdatpanalyzer) komputer, na którym jest uruchomiony program DLP punktu końcowego.
2. Wyodrębnianie zawartości MDATPClientAnalyzer.zip na urządzeniu.
3. Otwieranie wiersza polecenia z podwyższonym poziomem uprawnień:
    1. Przejdź do **przycisku Start** i wpisz **cmd**.
    1. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.
4. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   `HardDrivePath\MDATPClientAnalyzer.cmd`

   *Zamień narzędzie HardDrivePath* na ścieżkę, do której pobrano narzędzie MDATPClientAnalyzer, na przykład

   **C:\Work\tools\MDATPClientAnalyzer\MDATPClientAnalyzer.cmd**

5. Wyodrębnij **MDATPClientAnalyzerResult.zip** _ utworzony przez narzędzie w folderze używanym w folderze _HardDrivePath*.

6. Otwórz **MDATPClientAnalyzerResult.txt** i upewnij się, że wykonano kroki konfiguracji serwera proxy w celu umożliwienia odnajdowania serwera i uzyskiwania dostępu do adresów URL usługi.  Narzędzie sprawdza łączność usługi Defender pod adresami URL usługi Endpoint, z których usługa Defender dla klienta punktu końcowego jest skonfigurowana do interakcji. Następnie drukuje wyniki do pliku **MDATPClientAnalyzerResult.txt** każdego adresu URL, który potencjalnie może zostać użyty do komunikacji z usługami Defender for Endpoint. Przykład:

   ```DOS
   Testing URL: https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command-line proxy: Doesn't exist
   ```

Jeśli co najmniej jedna z opcji łączności zwróci stan (200), wówczas klient programu Defender dla punktu końcowego może poprawnie komunikować się z testowym adresem URL przy użyciu tej metody łączności.

Jeśli jednak wyniki kontroli łączności wskazują na awarię, zostanie wyświetlony błąd HTTP (zobacz Kody stanu PROTOKOŁU HTTP). Następnie możesz użyć adresów URL z tabeli przedstawionej w tece Włączanie dostępu do adresów URL usługi W [chmurze DLP na serwerze proxy](#enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server). Adresy URL, których będziesz używać, zależą od regionu wybranego podczas procedury dołączania.

> [!NOTE]
>
> Narzędzie Analizator łączności nie jest zgodne z regułą zmniejszania powierzchni ataków Tworzenie procesu blokowania pochodzące z poleceń [PSExec i WMI](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#block-process-creations-originating-from-psexec-and-wmi-commands). Aby uruchomić narzędzie łączności, musisz tymczasowo wyłączyć tę regułę.
>
> Po skonfigurowaniu telemetrycznego serwera proxy w rejestrze lub za pośrednictwem serwera zasady grupy usługa Defender for Endpoint powraca do kierowania, jeśli nie może uzyskać dostępu do zdefiniowanego serwera proxy. Tematy pokrewne:
>
> - Urządzenia Windows 10 urządzeniach
> - Rozwiązywanie problemów z dołączaniem do punktów końcowych firmy Microsoft

## <a name="see-also"></a>Zobacz też

- [Informacje na temat ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-learn-about.md)
- [Korzystanie z ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-using.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Narzędzia i metody dołączania do Windows 10 komputerów](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 subskrypcji](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Urządzenia przyłączone do usługi Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Pobierz nowy Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
