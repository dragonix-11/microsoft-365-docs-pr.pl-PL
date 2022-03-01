---
title: Program Microsoft Defender dla punktu końcowego w zasobach systemu Linux
ms.reviewer: ''
description: W tym artykule opisano zasoby dotyczące programu Microsoft Defender for Endpoint w systemie Linux, w tym informacje o tym, jak go odinstalować, jak zbierać dzienniki diagnostyczne, polecenia cli i znane problemy dotyczące produktu.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, installation, deploy, dezinstalacja, 8, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e20b993d577f144e80c99479bac7bf70e484f785
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997422"
---
# <a name="resources"></a>Zasoby

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="collect-diagnostic-information"></a>Zbieranie informacji diagnostycznych

Jeśli możesz odtworzyć problem, najpierw zwiększ poziom rejestrowania, uruchom system przez pewien czas, a następnie przywróć domyślny poziom rejestrowania.

1. Zwiększanie poziomu rejestrowania:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Odtprodukuj problem.

3. Uruchom następujące polecenie, aby uzyskać kopię zapasową dzienników usługi Defender dla punktu końcowego. Pliki będą przechowywane w archiwum .zip archiwum.

   ```bash
   sudo mdatp diagnostic create
   ```

    Po zakończeniu operacji to polecenie wydrukuje również ścieżkę do pliku kopii zapasowej:

   ```Output
   Diagnostic file created: <path to file>
   ```

4. Przywracanie poziomu rejestrowania:

   ```bash
   mdatp log level set --level info
   ```

   ```Output
   Log level configured successfully
   ```

## <a name="log-installation-issues"></a>Problemy z instalacją dziennika

Jeśli podczas instalacji wystąpi błąd, instalator będzie zgłaszał tylko błąd ogólny.

Szczegółowy dziennik zostanie zapisany w .`/var/log/microsoft/mdatp/install.log`
Jeśli podczas instalacji wystąpią problemy, wyślij nam ten plik, abyśmy pomogli zdiagnozować przyczynę.

## <a name="uninstall"></a>Odinstalowanie

Istnieje kilka sposobów odinstalowania programu Defender dla punktu końcowego w systemie Linux. Jeśli korzystasz z narzędzia konfiguracyjne, takiego jak Schowek, postępuj zgodnie z instrukcjami odinstalowywania pakietu dla tego narzędzia konfiguracyjne.

### <a name="manual-uninstallation"></a>Ręczne odinstalowywanie

- `sudo yum remove mdatp` dla RNOG i wariantów(CentOS i Oracle Linux).
- `sudo zypper remove mdatp` dla SLES i wariantów.
- `sudo apt-get purge mdatp` dla systemów Ubuntu i Debian.

## <a name="configure-from-the-command-line"></a>Konfigurowanie z wiersza polecenia

Z poziomu wiersza polecenia można wykonywać ważne zadania, takie jak kontrolowanie ustawień produktu i wyzwalanie skanów na żądanie.

### <a name="global-options"></a>Opcje globalne

Domyślnie narzędzie wiersza polecenia wyprowadza wynik w formacie czytelnym dla człowieka. Ponadto narzędzie obsługuje również wyprowadzanie wyników jako JSON, co jest przydatne w przypadku scenariuszy automatyzacji. Aby zmienić wynik na JSON, należy przejść `--output json` do dowolnego z poniższych poleceń.

### <a name="supported-commands"></a>Obsługiwane polecenia

W poniższej tabeli wymieniono polecenia najbardziej typowych scenariuszy. Uruchom `mdatp help` program Terminal, aby wyświetlić pełną listę obsługiwanych poleceń.

<br>

****

|Grupa|Scenariusz|Polecenie|
|---|---|---|
|Konfiguracja|Włączanie/wyłączanie ochrony w czasie rzeczywistym|`mdatp config real-time-protection --value [enabled\|disabled]`|
|Konfiguracja|Włączanie/wyłączanie monitorowania zachowania|`mdatp config behavior-monitoring --value [enabled\|disabled]`
|Konfiguracja|Włączanie/wyłączanie ochrony w chmurze|`mdatp config cloud --value [enabled\|disabled]`|
|Konfiguracja|Włączanie/wyłączanie diagnostyki produktów|`mdatp config cloud-diagnostic --value [enabled\|disabled]`|
|Konfiguracja|Włączanie/wyłączanie automatycznego przesyłania próbek|`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`|
|Konfiguracja|Włączanie/wyłączanie trybu pasywnego audio/wideo|`mdatp config passive-mode --value [enabled\|disabled]`|
|Konfiguracja|Dodawanie/usuwanie wykluczeń oprogramowania antywirusowego dla rozszerzenia pliku|`mdatp exclusion extension [add\|remove] --name [extension]`|
|Konfiguracja|Dodawanie/usuwanie wykluczeń oprogramowania antywirusowego dla pliku|`mdatp exclusion file [add\|remove] --path [path-to-file]`|
|Konfiguracja|Dodawanie/usuwanie wykluczeń oprogramowania antywirusowego dla katalogu|`mdatp exclusion folder [add\|remove] --path [path-to-directory]`|
|Konfiguracja|Dodawanie/usuwanie wykluczenia oprogramowania antywirusowego dla procesu|`mdatp exclusion process [add\|remove] --path [path-to-process]` <p> `mdatp exclusion process [add\|remove] --name [process-name]`|
|Konfiguracja|Lista wszystkich wykluczeń oprogramowania antywirusowego|`mdatp exclusion list`|
|Konfiguracja|Dodawanie nazwy zagrożenia do listy dozwolonych|`mdatp threat allowed add --name [threat-name]`|
|Konfiguracja|Usuwanie nazwy zagrożenia z listy dozwolonych|`mdatp threat allowed remove --name [threat-name]`|
|Konfiguracja|Lista wszystkich dozwolonych nazw zagrożeń|`mdatp threat allowed list`|
|Konfiguracja|Włączanie ochrony przed zabłądem pua|`mdatp threat policy set --type potentially_unwanted_application --action block`|
|Konfiguracja|Wyłączanie ochrony przed pua|`mdatp threat policy set --type potentially_unwanted_application --action off`|
|Konfiguracja|Włączanie trybu inspekcji w celu ochrony przed pua|`mdatp threat policy set --type potentially_unwanted_application --action audit`|
|Konfiguracja|Konfigurowanie stopnia równoległości w skanach na żądanie|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Konfiguracja|Włączanie/wyłączanie skanów po aktualizacjach analizy zabezpieczeń|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Konfiguracja|Włączanie/wyłączanie skanowania archiwum (tylko skanowanie na żądanie)|`mdatp config scan-archives --value [enabled/disabled]`|
|Diagnostyka|Zmienianie poziomu dziennika|`mdatp log level set --level verbose [error|warning|info|verbose]`|
|Diagnostyka|Generowanie dzienników diagnostycznych|`mdatp diagnostic create --path [directory]`|
|Kondycja|Sprawdzanie kondycji produktu|`mdatp health`|
|Ochrona|Skanowanie ścieżki|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Ochrona|Szybkie skanowanie|`mdatp scan quick`|
|Ochrona|Wykonaj pełne skanowanie|`mdatp scan full`|
|Ochrona|Anulowanie trwającego skanowania na żądanie|`mdatp scan cancel`|
|Ochrona|Żądanie aktualizacji analizy zabezpieczeń|`mdatp definitions update`|
|Historia ochrony|Drukowanie pełnej historii ochrony|`mdatp threat list`|
|Historia ochrony|Uzyskiwanie szczegółów zagrożeń|`mdatp threat get --id [threat-id]`|
|Zarządzanie kwarantanną|Lista wszystkich plików poddanych kwarantannie|`mdatp threat quarantine list`|
|Zarządzanie kwarantanną|Usuwanie wszystkich plików z kwarantanny|`mdatp threat quarantine remove-all`|
|Zarządzanie kwarantanną|Dodawanie pliku wykrytego jako zagrożenie do kwarantanny|`mdatp threat quarantine add --id [threat-id]`|
|Zarządzanie kwarantanną|Usuwanie pliku wykrytego jako zagrożenie z kwarantanny|`mdatp threat quarantine remove --id [threat-id]`|
|Zarządzanie kwarantanną|Przywracanie pliku z kwarantanny|`mdatp threat quarantine restore --id [threat-id]`|
|Wykrywanie punktu końcowego i odpowiedź|Ustawianie wczesnego podglądu (nieużywane)|`mdatp edr early-preview [enable|disable]`|
|Wykrywanie punktu końcowego i odpowiedź|Ustaw identyfikator grupy|`mdatp edr group-ids --group-id [group-id]`|
|Wykrywanie punktu końcowego i odpowiedź|Ustawianie/usuwanie tagu, obsługiwane tylko `GROUP`|`mdatp edr tag set --name GROUP --value [tag]`|
|Wykrywanie punktu końcowego i odpowiedź|Wykluczenia listy (główne)|`mdatp edr exclusion list [processes|paths|extensions|all]`|
|
