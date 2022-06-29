---
title: Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender
description: Omówienie wymagań i wymagań dotyczących licencjonowania dołączania urządzeń do usługi
keywords: minimalne wymagania, licencjonowanie, tabela porównawcza
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
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b2b1303fc9ab0841643536ccf5a85470243fe74e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490580"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-minreqs-abovefoldlink)

Istnieją pewne minimalne wymagania dotyczące dołączania urządzeń do usługi. Dowiedz się więcej o wymaganiach dotyczących licencjonowania, sprzętu i oprogramowania oraz innych ustawieniach konfiguracji w celu dołączania urządzeń do usługi.

> [!TIP]
>
> - W tym artykule opisano minimalne wymagania dotyczące planu Ochrona punktu końcowego w usłudze Microsoft Defender 2. Jeśli szukasz informacji o usłudze Defender for Endpoint Plan 1, zobacz [Wymagania dotyczące usługi Defender for Endpoint Plan 1](mde-p1-setup-configuration.md#review-the-requirements).
> - Dowiedz się więcej o najnowszych ulepszeniach w usłudze Defender for Endpoint: [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - Usługa Defender for Endpoint zademonstrowała wiodącą w branży optykę i możliwości wykrywania w ostatniej ocenie MITRE. Przeczytaj: [Szczegółowe informacje z oceny opartej na programie MITRE ATT&CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Aby uzyskać informacje o wymaganiach licencyjnych dotyczących Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender informacje o licencjonowaniu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).

Aby uzyskać szczegółowe informacje o licencjonowaniu, zobacz [witrynę Warunki produktu](https://www.microsoft.com/licensing/terms/) i skontaktuj się z zespołem ds. konta, aby dowiedzieć się więcej na temat warunków i postanowień.

Aby uzyskać więcej informacji na temat tablicy funkcji w wersjach systemu Windows, zobacz [Porównanie wersji systemu Windows](https://www.microsoft.com/windowsforbusiness/compare).

## <a name="browser-requirements"></a>Wymagania przeglądarki

Dostęp do usługi Defender for Endpoint odbywa się za pośrednictwem przeglądarki obsługującej następujące przeglądarki:

- Microsoft Edge
- Google Chrome

> [!NOTE]
> Chociaż inne przeglądarki mogą działać, wymienione przeglądarki są obsługiwane.

## <a name="hardware-and-software-requirements"></a>Wymagania dotyczące sprzętu i oprogramowania

### <a name="supported-windows-versions"></a>Obsługiwane wersje systemu Windows

- System Windows 11 dla firm
- System Windows 11 dla edukacji
- System Windows 11 Pro
- System Windows 11 Pro dla edukacji
- System Windows10 dla firm
- [Windows 10 Enterprise LTSC 2016 (lub nowszy)](/windows/whats-new/ltsc/)
- Windows 10 Enterprise IoT

    >[!NOTE]
    >Chociaż Windows 10 IoT Enterprise jest obsługiwanym systemem operacyjnym w Ochrona punktu końcowego w usłudze Microsoft Defender i umożliwia maszynom OEM/ODM dystrybucję go w ramach produktu lub rozwiązania, klienci powinni postępować zgodnie ze wskazówkami producenta OEM/ODM dotyczącymi zainstalowanego oprogramowania i możliwości obsługi hosta.

- Windows 10 Education
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 8.1 Enterprise
- Windows 8.1 Pro
- Windows 7 SP1 Enterprise ([wymaga ESU do obsługi](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows 7 SP1 Pro ([wymaga ESU do obsługi](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows Server
  - Windows Server 2008 R2 SP1 ([wymaga ESU do obsługi](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - System Windows Server 2016
  - Windows Server, wersja 1803 lub nowsza
  - Windows Server 2019
  - Windows Server 2022
- Windows Virtual Desktop
- Windows 365

Na urządzeniach w sieci musi być uruchomiona jedna z tych wersji.

Wymagania sprzętowe usługi Defender dla punktu końcowego na urządzeniach są takie same w przypadku obsługiwanych wersji.

> Rdzenie: 2 minimum, 4 preferowane pamięci: minimum 1 GB, 4 preferowane

Aby uzyskać więcej informacji na temat obsługiwanych wersji Windows 10, zobacz (/windows/release-health/release-information).

> [!NOTE]
> - Punkty końcowe z mobilnymi wersjami systemu Windows (takimi jak Windows CE i Windows 10 Mobile) nie są obsługiwane.
>
> - Virtual Machines uruchomione Windows 10 Enterprise 2016 LTSB mogą napotkać problemy z wydajnością, jeśli są uruchamiane na platformach wirtualizacji innych niż Microsoft.
>
> - W przypadku środowisk wirtualnych zalecamy używanie Windows 10 Enterprise LTSC 2019 lub nowszych.
>
> - Autonomiczne wersje [usług Defender for Endpoint Plan 1 i Plan 2](defender-endpoint-plan-1-2.md) nie obejmują licencji serwera. Aby dołączyć serwery do tych planów, musisz mieć usługę Defender for Servers Plan 1 lub Plan 2 w ramach [oferty usługi Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . Aby dowiedzieć się więcej. zobacz [Omówienie usługi Microsoft Defender dla serwerów](/azure/defender-for-cloud/defender-for-servers-introduction).

Gdy składniki są aktualne w systemach operacyjnych Microsoft Windows, obsługa Ochrona punktu końcowego w usłudze Microsoft Defender będzie zgodna z cyklem życia odpowiedniego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Często zadawane pytania dotyczące cyklu życia](/lifecycle/faq/general-lifecycle). Nowe funkcje lub możliwości są zwykle udostępniane tylko w systemach operacyjnych, które nie osiągnęły jeszcze końca ich cyklu życia. Aktualizacje analizy zabezpieczeń (aktualizacje definicji i aparatu) i logika wykrywania będą udostępniane co najmniej do:

- [Data zakończenia wsparcia](/lifecycle/products/) (dla systemów operacyjnych, które nie mają programu Extended Security Aktualizacje (ESU).
- [Koniec daty ESU](/lifecycle/faq/extended-security-updates) (dla systemów operacyjnych z programem ESU).

### <a name="other-supported-operating-systems"></a>Inne obsługiwane systemy operacyjne

- [Android](microsoft-defender-endpoint-android.md)
- [iOS](microsoft-defender-endpoint-ios.md)
- [Linux](microsoft-defender-endpoint-linux.md)
- [macOS](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Aby integracja działała, musisz potwierdzić, że dystrybucje systemu Linux i wersje systemów Android, iOS i macOS są zgodne z usługą Defender for Endpoint.

### <a name="network-and-data-storage-and-configuration-requirements"></a>Wymagania dotyczące sieci i magazynu danych oraz konfiguracji

Po pierwszym uruchomieniu kreatora dołączania należy wybrać miejsce przechowywania informacji związanych z Ochrona punktu końcowego w usłudze Microsoft Defender: w Unii Europejskiej, Wielkiej Brytanii lub Stany Zjednoczone centrum danych.

> [!NOTE]
>
> - Nie można zmienić lokalizacji magazynu danych po pierwszej konfiguracji.
> - Przejrzyj [Ochrona punktu końcowego w usłudze Microsoft Defender magazyn danych i prywatność](data-storage-privacy.md), aby uzyskać więcej informacji na temat tego, gdzie i jak firma Microsoft przechowuje Twoje dane.

### <a name="diagnostic-data-settings"></a>Ustawienia danych diagnostycznych

> [!NOTE]
> Ochrona punktu końcowego w usłudze Microsoft Defender nie wymaga żadnego określonego poziomu diagnostyki, o ile jest włączona.

Upewnij się, że usługa danych diagnostycznych jest włączona na wszystkich urządzeniach w organizacji.
Domyślnie ta usługa jest włączona. Dobrym rozwiązaniem jest sprawdzenie, czy otrzymasz od nich dane z czujników.

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>Użyj wiersza polecenia, aby sprawdzić typ uruchamiania usługi danych diagnostycznych systemu Windows

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu:
   1. Przejdź do **pozycji Start** i wpisz **cmd**.
   2. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij **klawisz Enter**:

   ```console
   sc qc diagtrack
   ```

   Jeśli usługa jest włączona, wynik powinien wyglądać podobnie do następującego zrzutu ekranu:

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="Wynik polecenia sc query dla narzędzia diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

Musisz ustawić usługę tak, aby była uruchamiana automatycznie, jeśli **START_TYPE** nie jest ustawiona na **AUTO_START**.

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>Użyj wiersza polecenia, aby ustawić automatyczne uruchamianie usługi danych diagnostycznych systemu Windows

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień w punkcie końcowym:
    1. Przejdź do **pozycji Start** i wpisz **cmd**.
    2. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij **klawisz Enter**:

    ```console
    sc config diagtrack start=auto
    ```

3. Zostanie wyświetlony komunikat o powodzeniu. Sprawdź zmianę, wprowadzając następujące polecenie i naciśnij **klawisz Enter**:

    ```console
    sc qc diagtrack
    ```

#### <a name="internet-connectivity"></a>Łączność z Internetem

Łączność z Internetem na urządzeniach jest wymagana bezpośrednio lub za pośrednictwem serwera proxy.

Czujnik usługi Defender for Endpoint może używać średniej dziennej przepustowości wynoszącej 5 MB do komunikowania się z usługą Defender for Endpoint w chmurze i raportowania danych cybernetycznych. Działania jednorazowe, takie jak przekazywanie plików i zbieranie pakietów badania, nie są uwzględniane w tej średniej dziennej przepustowości.

Aby uzyskać więcej informacji na temat dodatkowych ustawień konfiguracji serwera proxy, zobacz [Konfigurowanie ustawień serwera proxy urządzenia i łączności z Internetem](configure-proxy-internet.md).

Przed dołączeniem urządzeń należy włączyć usługę danych diagnostycznych. Usługa jest domyślnie włączona w Windows 10 i Windows 11.

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>Wymaganie konfiguracji programu antywirusowego Microsoft Defender

Agent usługi Defender for Endpoint zależy od możliwości skanowania plików i dostarczania informacji o nich przez program antywirusowy Microsoft Defender.

Skonfiguruj aktualizacje analizy zabezpieczeń na urządzeniach usługi Defender for Endpoint, niezależnie od tego, czy program antywirusowy Microsoft Defender jest aktywnym oprogramowaniem chroniącym przed złośliwym kodem. Aby uzyskać więcej informacji, zobacz [Zarządzanie aktualizacjami programu antywirusowego Microsoft Defender i stosowanie punktów odniesienia](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus).

Gdy program antywirusowy Microsoft Defender nie jest aktywnym oprogramowaniem chroniącym przed złośliwym kodem w organizacji i używasz usługi Defender for Endpoint, program antywirusowy Microsoft Defender przechodzi w tryb pasywny.

Jeśli Twoja organizacja wyłączyła program antywirusowy Microsoft Defender za pomocą zasad grupy lub innych metod, dołączone urządzenia muszą zostać wykluczone z tych zasad grupy.

Jeśli dołączasz serwery, a program antywirusowy Microsoft Defender nie jest aktywnym oprogramowaniem chroniącym przed złośliwym kodem na serwerach, program antywirusowy Microsoft Defender musi zostać skonfigurowany tak, aby działał w trybie pasywnym lub był odinstalowany. Konfiguracja zależy od wersji serwera. Aby uzyskać więcej informacji, zobacz [Zgodność programu antywirusowego Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

> [!NOTE]
> Regularne zasady grupy nie mają zastosowania do ochrony przed naruszeniami, a zmiany ustawień programu antywirusowego Microsoft Defender zostaną zignorowane, gdy ochrona przed naruszeniami jest włączona.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>Sterownik ochrony przed złośliwym oprogramowaniem antywirusowym Microsoft Defender (ELAM) jest włączony

Jeśli używasz programu antywirusowego Microsoft Defender jako podstawowego produktu chroniącego przed złośliwym kodem na urządzeniach, agent usługi Defender for Endpoint zostanie pomyślnie dołączone.

Jeśli używasz klienta ochrony przed złośliwym kodem innej firmy i używasz rozwiązań mobile Zarządzanie urządzeniami lub microsoft Endpoint Manager (bieżąca gałąź), musisz upewnić się, że sterownik ELAM programu antywirusowego Microsoft Defender jest włączony. Aby uzyskać więcej informacji, zobacz [Upewnij się, że program antywirusowy Microsoft Defender nie jest wyłączony przez zasady](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="related-topics"></a>Tematy pokrewne

- [Konfigurowanie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender](production-deployment.md)
- [Dołączanie urządzeń](onboard-configure.md)
