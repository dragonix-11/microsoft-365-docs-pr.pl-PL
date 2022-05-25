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
ms.openlocfilehash: 355fc0f367c415ae679259195e18ff3920812f4a
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670163"
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
> - Dowiedz się więcej o najnowszych ulepszeniach usługi Defender for Endpoint: [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - Usługa Defender for Endpoint zademonstrowała wiodącą w branży optykę i możliwości wykrywania w ostatniej ocenie MITRE. Przeczytaj: [Szczegółowe informacje z oceny opartej na&MITRE ATT](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania
Aby uzyskać informacje o wymaganiach licencyjnych dotyczących Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender informacje o licencjonowaniu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).


Aby uzyskać szczegółowe informacje o licencjonowaniu, zobacz [witrynę Warunki produktu](https://www.microsoft.com/licensing/terms/) i skontaktuj się z zespołem ds. konta, aby dowiedzieć się więcej na temat warunków i postanowień.

Aby uzyskać więcej informacji na temat tablicy funkcji w wersjach Windows, zobacz [Porównanie wersji Windows](https://www.microsoft.com/windowsforbusiness/compare).

## <a name="browser-requirements"></a>Wymagania przeglądarki

Dostęp do usługi Defender for Endpoint odbywa się za pośrednictwem przeglądarki obsługującej następujące przeglądarki:

- Microsoft Edge
- Google Chrome

> [!NOTE]
> Chociaż inne przeglądarki mogą działać, wymienione przeglądarki są obsługiwane.

## <a name="hardware-and-software-requirements"></a>Wymagania dotyczące sprzętu i oprogramowania

### <a name="supported-windows-versions"></a>Obsługiwane wersje Windows

- Windows 7 Enterprise SP1 ([wymaga ESU do obsługi](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows 7 Pro SP1 ([wymaga ESU do obsługi](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows 8.1 Enterprise
- Windows 8.1 Pro
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
- serwer Windows
  - Windows Server 2008 R2 SP1 ([wymaga ESU do obsługi](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - Windows Server 2016
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
> Maszyny z mobilnymi wersjami Windows (na przykład Windows CE i Windows 10 Mobile) nie są obsługiwane.
>
> Maszyny wirtualne z systemem Windows 10 Enterprise 2016 LTSB mogą napotkać problemy z wydajnością, jeśli są uruchamiane na platformach wirtualizacji innych niż Microsoft.
>
> W przypadku środowisk wirtualnych zalecamy używanie Windows 10 Enterprise LTSC 2019 lub nowszych.

Gdy składniki są aktualne w systemach operacyjnych microsoft Windows, Ochrona punktu końcowego w usłudze Microsoft Defender pomoc techniczna będzie zgodna z cyklem życia odpowiedniego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Często zadawane pytania dotyczące cyklu życia](/lifecycle/faq/general-lifecycle). Nowe funkcje lub możliwości są zwykle udostępniane tylko w systemach operacyjnych, które nie osiągnęły jeszcze końca ich cyklu życia. Aktualizacje analizy zabezpieczeń (aktualizacje definicji i aparatu) i logika wykrywania będą udostępniane co najmniej do:

- [Data zakończenia wsparcia](/lifecycle/products/) (dla systemów operacyjnych, które nie mają programu rozszerzonych aktualizacji zabezpieczeń (ESU).
- [Koniec daty ESU](/lifecycle/faq/extended-security-updates) (dla systemów operacyjnych z programem ESU).



### <a name="other-supported-operating-systems"></a>Inne obsługiwane systemy operacyjne

- [Android](microsoft-defender-endpoint-android.md)
- [iOS](microsoft-defender-endpoint-ios.md)
- [Linux](microsoft-defender-endpoint-linux.md)
- [macOS](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Aby integracja działała, musisz potwierdzić, że dystrybucje i wersje systemu Linux Android, iOS i macOS są zgodne z usługą Defender for Endpoint.

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

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>Użyj wiersza polecenia, aby sprawdzić typ uruchamiania usługi danych diagnostycznych Windows

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

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>Użyj wiersza polecenia, aby ustawić automatyczne uruchamianie usługi danych diagnostycznych Windows

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

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>Program antywirusowy Microsoft Defender wymagania dotyczące konfiguracji

Agent usługi Defender for Endpoint zależy od możliwości Program antywirusowy Microsoft Defender skanowania plików i dostarczania informacji o nich.

Skonfiguruj aktualizacje analizy zabezpieczeń na urządzeniach usługi Defender for Endpoint, niezależnie od tego, czy Program antywirusowy Microsoft Defender jest aktywnym oprogramowaniem chroniącym przed złośliwym kodem. Aby uzyskać więcej informacji, zobacz [Manage Program antywirusowy Microsoft Defender updates and apply baselines (Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie punktów odniesienia](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus)).

Jeśli Program antywirusowy Microsoft Defender nie jest aktywnym oprogramowaniem chroniącym przed złośliwym kodem w organizacji i używasz usługi Defender for Endpoint, Program antywirusowy Microsoft Defender przechodzi w tryb pasywny.

Jeśli twoja organizacja wyłączyła Program antywirusowy Microsoft Defender za pomocą zasad grupy lub innych metod, dołączone urządzenia muszą zostać wykluczone z tych zasad grupy.

Jeśli dołączasz serwery i Program antywirusowy Microsoft Defender nie jest aktywnym oprogramowaniem chroniącym przed złośliwym kodem na serwerach, Program antywirusowy Microsoft Defender należy skonfigurować tryb pasywny lub odinstalować. Konfiguracja zależy od wersji serwera. Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender zgodność](microsoft-defender-antivirus-compatibility.md).

> [!NOTE]
> Zwykłe zasady grupy nie mają zastosowania do ochrony przed naruszeniami, a zmiany ustawień Program antywirusowy Microsoft Defender zostaną zignorowane, gdy ochrona przed naruszeniami jest włączona.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>Program antywirusowy Microsoft Defender włączono sterownik wczesnego uruchamiania oprogramowania chroniącego przed złośliwym kodem (ELAM)

Jeśli używasz Program antywirusowy Microsoft Defender jako podstawowego produktu chroniącego przed złośliwym kodem na urządzeniach, agent usługi Defender for Endpoint zostanie pomyślnie dołączone.

Jeśli korzystasz z klienta ochrony przed złośliwym kodem innej firmy i używasz rozwiązań mobile Zarządzanie urządzeniami lub Microsoft Endpoint Manager (bieżąca gałąź), musisz upewnić się, że sterownik Program antywirusowy Microsoft Defender ELAM jest włączony. Aby uzyskać więcej informacji, zobacz [Upewnij się, że Program antywirusowy Microsoft Defender nie jest wyłączona przez zasady](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="related-topics"></a>Tematy pokrewne

- [Konfigurowanie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender](production-deployment.md)
- [Dołączanie urządzeń](onboard-configure.md)
