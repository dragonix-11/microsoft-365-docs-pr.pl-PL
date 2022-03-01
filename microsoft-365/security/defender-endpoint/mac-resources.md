---
title: Zasoby dotyczące programu Microsoft Defender dla punktu końcowego na komputerze Mac
description: Zasoby dotyczące programu Microsoft Defender dla punktu końcowego na komputerze Mac, w tym informacje o tym, jak go odinstalować, jak zbierać dzienniki diagnostyczne, polecenia cli i znane problemy dotyczące produktu.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 5c8580e1bc0869f28da1b23a813bba9d2f3c612e
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011932"
---
# <a name="resources-for-microsoft-defender-for-endpoint-on-macos"></a>Zasoby dotyczące programu Microsoft Defender dla punktu końcowego w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="collecting-diagnostic-information"></a>Zbieranie informacji diagnostycznych

Jeśli możesz odtworzyć problem, zwiększ poziom rejestrowania, uruchom system przez pewien czas i przywróć domyślny poziom rejestrowania.

1. Zwiększanie poziomu rejestrowania:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Odtprodukuj problem

3. Uruchom kopię `sudo mdatp diagnostic create` zapasową dzienników programu Microsoft Defender for Endpoint. Pliki będą przechowywane w archiwum .zip archiwum. Po zakończeniu operacji to polecenie wydrukuje również ścieżkę do pliku kopii zapasowej.

   > [!TIP]
   > Domyślnie dzienniki diagnostyczne są zapisywane w `/Library/Application Support/Microsoft/Defender/wdavdiag/`. Aby zmienić katalog, w którym są zapisywane dzienniki diagnostyczne, należy przejść `--path [directory]` do poniższego polecenia i zastąpić `[directory]` go odpowiednim katalogiem.

   ```bash
   sudo mdatp diagnostic create
   ```

   ```console
   Diagnostic file created: "/Library/Application Support/Microsoft/Defender/wdavdiag/932e68a8-8f2e-4ad0-a7f2-65eb97c0de01.zip"
   ```

4. Przywracanie poziomu rejestrowania:

   ```bash
   mdatp log level set --level info
   ```

   ```console
   Log level configured successfully
   ```

## <a name="logging-installation-issues"></a>Problemy z instalacją rejestrowania

Jeśli podczas instalacji wystąpi błąd, instalator będzie zgłaszał tylko błąd ogólny.

Szczegółowy dziennik zostanie zapisany w .`/Library/Logs/Microsoft/mdatp/install.log` Jeśli podczas instalacji wystąpią problemy, wyślij nam ten plik, abyśmy pomogli zdiagnozować przyczynę.

## <a name="uninstalling"></a>Odinstalowywanie

Istnieje kilka sposobów odinstalowania programu Microsoft Defender for Endpoint w systemie macOS. Należy pamiętać, że centralnie zarządzane odinstalowywanie jest dostępne w układzie JAMF, ale nie jest jeszcze dostępne dla Microsoft Intune.

### <a name="interactive-uninstallation"></a>Interakcyjna dezinstalacja

- Otwórz **program Finder > Applications**. Kliknij prawym przyciskiem myszy **pozycję Microsoft Defender for Endpoint > Przenieś do Kosza**.

### <a name="supported-output-types"></a>Obsługiwane typy danych wyjściowych

Obsługuje typy danych wyjściowych w formacie tabeli i format JSON. Dla każdego polecenia istnieje domyślne zachowanie wyjściowe. Możesz zmodyfikować dane wyjściowe w preferowanym formacie wyjściowym, korzystając z następujących poleceń:

`-output json`

`-output table`

### <a name="from-the-command-line"></a>Z wiersza polecenia

- `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`

## <a name="configuring-from-the-command-line"></a>Konfigurowanie z wiersza polecenia

Ważne zadania, takie jak kontrolowanie ustawień produktu i wyzwalanie skanów na żądanie, można wykonać z poziomu wiersza polecenia:

|Grupa|Scenariusz|Polecenie|
|---|---|---|
|Konfiguracja|Włączanie/wyłączanie ochrony w czasie rzeczywistym|`mdatp config real-time-protection --value [enabled/disabled]`|
|Konfiguracja|Włączanie/wyłączanie ochrony w chmurze|`mdatp config cloud --value [enabled/disabled]`|
|Konfiguracja|Włączanie/wyłączanie diagnostyki produktów|`mdatp config cloud-diagnostic --value [enabled/disabled]`|
|Konfiguracja|Włączanie/wyłączanie automatycznego przesyłania próbek|`mdatp config cloud-automatic-sample-submission --value [enabled/disabled]`|
|Konfiguracja|Dodawanie nazwy zagrożenia do listy dozwolonych|`mdatp threat allowed add --name [threat-name]`|
|Konfiguracja|Usuwanie nazwy zagrożenia z listy dozwolonych|`mdatp threat allowed remove --name [threat-name]`|
|Konfiguracja|Lista wszystkich dozwolonych nazw zagrożeń|`mdatp threat allowed list`|
|Konfiguracja|Włączanie ochrony przed zabłądem pua|`mdatp threat policy set --type potentially_unwanted_application -- action block`|
|Konfiguracja|Wyłączanie ochrony przed pua|`mdatp threat policy set --type potentially_unwanted_application -- action off`|
|Konfiguracja|Włączanie trybu inspekcji w celu ochrony przed pua|`mdatp threat policy set --type potentially_unwanted_application -- action audit`|
|Konfiguracja|Włączanie/wyłączanie trybu pasywnego oprogramowania antywirusowego|`mdatp config passive-mode --value [enabled/disabled]`|
|Konfiguracja|Konfigurowanie stopnia równoległości w skanach na żądanie|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Konfiguracja|Włączanie/wyłączanie skanów po aktualizacjach analizy zabezpieczeń|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Konfiguracja|Włączanie/wyłączanie skanowania archiwum (tylko skanowanie na żądanie)|`mdatp config scan-archives --value [enabled/disabled]`|
|Diagnostyka|Zmienianie poziomu dziennika|`mdatp log level set --level [error/warning/info/verbose]`|
|Diagnostyka|Generowanie dzienników diagnostycznych|`mdatp diagnostic create --path [directory]`|
|Kondycja|Sprawdzanie kondycji produktu|`mdatp health`|
|Kondycja|Sprawdzanie, czy atrybut produktu jest fikcyjny|`mdatp health --field [attribute: healthy/licensed/engine_version...]`|
|Ochrona|Skanowanie ścieżki|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Ochrona|Szybkie skanowanie|`mdatp scan quick`|
|Ochrona|Wykonaj pełne skanowanie|`mdatp scan full`|
|Ochrona|Anulowanie trwającego skanowania na żądanie|`mdatp scan cancel`|
|Ochrona|Żądanie aktualizacji analizy zabezpieczeń|`mdatp definitions update`|
|EDR|Set/Remove tag, only GROUP supported|`mdatp edr tag set --name GROUP --value [name]`|
|EDR|Usuwanie tagu grupy z urządzenia|`mdatp edr tag remove --tag-name [name]`|
|EDR|Dodawanie identyfikatora grupy|`mdatp edr group-ids --group-id [group]`|

### <a name="how-to-enable-autocompletion"></a>Jak włączyć autouzupełnianie

Aby włączyć autouzupełnianie w powłoce Bash, uruchom następujące polecenie i uruchom ponownie sesję terminalu:

```bash
echo "source /Applications/Microsoft\ Defender.app/Contents/Resources/Tools/mdatp_completion.bash" >> ~/.bash_profile
```

Aby włączyć autouzupełnianie w programie zsh:

- Sprawdź, czy na Twoim urządzeniu jest włączone autouzupełnianie:

   ```zsh
   cat ~/.zshrc | grep autoload
   ```

- Jeśli poprzednie polecenie nie powoduje uzyskania żadnych danych wyjściowych, możesz włączyć autouzupełnianie przy użyciu następującego polecenia:

   ```zsh
   echo "autoload -Uz compinit && compinit" >> ~/.zshrc
   ```

- Uruchom następujące polecenia, aby włączyć autouzupełnianie programu Microsoft Defender dla punktu końcowego w systemie macOS i ponownie uruchomić sesję terminalu:

   ```zsh
   sudo mkdir -p /usr/local/share/zsh/site-functions

   sudo ln -svf "/Applications/Microsoft Defender.app/Contents/Resources/Tools/mdatp_completion.zsh" /usr/local/share/zsh/site-functions/_mdatp
   ```

## <a name="client-microsoft-defender-for-endpoint-quarantine-directory"></a>Katalog kwarantanny klienta programu Microsoft Defender dla punktów końcowych

`/Library/Application Support/Microsoft/Defender/quarantine/` zawiera pliki poddane kwarantannie przez `mdatp`. Nazwy plików są takie, jak w przypadkuidu śledzenia zagrożeń. Bieżąceidy śledzenia są wyświetlane wraz z .`mdatp threat list`

## <a name="microsoft-defender-for-endpoint-portal-information"></a>Informacje dotyczące portalu programu Microsoft Defender for Endpoint

EDR funkcje dla [systemu macOS](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/edr-capabilities-for-macos-have-now-arrived/ba-p/1047801) zostały teraz dostępne w blogu Microsoft Defender for Endpoint, który zawiera szczegółowe wskazówki na temat tego, czego można oczekiwać w programie Microsoft Defender for Endpoint Security Center.
