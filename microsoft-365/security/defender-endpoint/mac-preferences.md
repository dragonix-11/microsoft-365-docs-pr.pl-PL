---
title: Ustawianie preferencji programu Microsoft Defender dla punktu końcowego na komputerze Mac
description: Konfigurowanie programu Microsoft Defender dla punktu końcowego na komputerze Mac w organizacjach przedsiębiorstw.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, management, preferences, enterprise, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: cb3f38b861f85849165be330e03fe1d96a9c708c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326709"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>Ustawianie preferencji programu Microsoft Defender dla punktu końcowego w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Program Microsoft Defender for Endpoint w systemie macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> Ten artykuł zawiera instrukcje dotyczące sposobu ustawienia preferencji programu Microsoft Defender dla punktu końcowego w systemie macOS w przedsiębiorstwach. Aby skonfigurować program Microsoft Defender dla punktu końcowego w systemie macOS za pomocą interfejsu wiersza polecenia, zobacz [Zasoby](mac-resources.md#configuring-from-the-command-line).

## <a name="summary"></a>Podsumowanie

W przedsiębiorstwach program Microsoft Defender for Endpoint w systemie macOS można zarządzać za pomocą profilu konfiguracji wdrożonego przy użyciu jednego z kilku narzędzi do zarządzania. Preferencje zarządzane przez zespół operacyjny ds. zabezpieczeń mają pierwszeństwo przed preferencjami ustawionymi lokalnie na urządzeniu. Zmiana preferencji ustawianych za pomocą profilu konfiguracji wymaga eskalacji uprawnień i nie jest dostępna dla użytkowników bez uprawnień administracyjnych.

W tym artykule opisano strukturę profilu konfiguracji, przedstawiono zalecany profil, który umożliwia rozpoczynanie pracy, oraz przedstawiono instrukcje dotyczące wdrażania profilu.

## <a name="configuration-profile-structure"></a>Struktura profilu konfiguracji

Profil konfiguracji to plik *plist* składający się z wpisów oznaczonych kluczem (co oznacza nazwę preferencji), a następnie wartością, która zależy od rodzaju preferencji. Wartości mogą być proste (na przykład wartości liczbowe) lub złożone, na przykład lista zagnieżdżona preferencji.

> [!CAUTION]
>Układ profilu konfiguracji zależy od konsoli zarządzania, z których korzystasz. Poniższe sekcje zawierają przykłady profilów konfiguracji dla usługi JAMF i Intune.

Górny poziom profilu konfiguracji obejmuje preferencje dotyczące całego produktu oraz wpisy dotyczące podobszarów usługi Microsoft Defender for Endpoint, które szczegółowo opisano w następnych sekcjach.

### <a name="antivirus-engine-preferences"></a>Preferencje aparatu antywirusowego

Sekcja *antivirusEngine* profilu konfiguracji służy do zarządzania preferencjami składnika antywirusowego programu Microsoft Defender for Endpoint.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|antivirusEngine|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|||

#### <a name="enforcement-level-for-antivirus-engine"></a>Poziom wymuszania dla aparatu antywirusowego

Określa preferencje wymuszania aparatu antywirusowego. Istnieją trzy wartości ustawień poziomu wymuszania:

- W czasie rzeczywistym (`real_time`): funkcja ochrony w czasie rzeczywistym (skanuj pliki w momencie, gdy są dostępne) jest włączona.
- Pliki na żądanie (`on_demand`): Pliki są skanowane tylko na żądanie. W tym:
  - Ochrona w czasie rzeczywistym jest wyłączona.
- Pasywne (`passive`): działa aparat antywirusowy w trybie pasywnym. W tym:
  - Ochrona w czasie rzeczywistym jest wyłączona.
  - Skanowanie na żądanie jest włączone.
  - Automatyczne rozwiązywanie problemów ze zagrożeniami jest wyłączone.
  - Aktualizacje analizy zabezpieczeń są włączone.
  - Ikona menu statusu jest ukryta.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|enforcementLevel|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|real_time (domyślnie) <p> on_demand <p> pasywne|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 101.10.72 lub wyższej.|
|||

#### <a name="run-a-scan-after-definitions-are-updated"></a>Uruchamianie skanowania po zaktualizowaniu definicji

Określa, czy po pobraniu na urządzenie nowych aktualizacji analizy zabezpieczeń ma być rozpoczynane skanowanie procesu. Włączenie tego ustawienia spowoduje uruchomienie skanowania antywirusowego w uruchomionych procesach urządzenia.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|scanAfterDefinitionUpdate|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 101.41.10 lub wyższej.|
|||

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Skanowanie archiwów (tylko skanowanie na żądanie)

Określa, czy podczas skanowania antywirusowego na żądanie mają być skanowane archiwa.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|scanArchives|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 101.41.10 lub wyższej.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Stopień równoległości skanów na żądanie

Określa stopień równoległości w skanach na żądanie. Odpowiada ona liczbie wątków używanych do skanowania i wpływa na użycie procesora, a także na czas trwania skanowania na żądanie.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|maximumOnDemandKanThreads|
|**Typ danych**|Liczba całkowita|
|**Dopuszczalne wartości**|2 (domyślnie). Dozwolone wartości to liczby całkowite z od 1 do 64.|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 101.41.10 lub wyższej.|
|||

#### <a name="exclusion-merge-policy"></a>Zasady scalania wykluczeń

Określanie zasad scalania dla wyjątków. Może to być połączenie wykluczeń zdefiniowanych przez administratora i zdefiniowanych przez użytkownika (`merge`) lub tylko zdefiniowanych przez administratora (`admin_only`). To ustawienie może być używane do ograniczania użytkownikom lokalnym definiowania własnych wykluczeń.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|exclusionsMergePolicy|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|scalanie (domyślnie) <p> admin_only|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 100.83.73 lub wyższej.|
|||

#### <a name="scan-exclusions"></a>Wykluczenia skanowania

Określ jednostki wykluczone przed skanowaniem. Wykluczenia można określić za pomocą pełnych ścieżek, rozszerzeń lub nazw plików.
(Wykluczenia są określone jako tablica elementów, administrator może określić dowolną liczbę elementów w dowolnej kolejności).

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|wykluczenia|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|||

##### <a name="type-of-exclusion"></a>Typ wykluczenia

Określ zawartość wykluczaną z skanowania według typu.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|$type|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|excludedPath <p> excludedFileExtension (Wykluczanie pliku) <p> excludedFileName|
|||

##### <a name="path-to-excluded-content"></a>Ścieżka do wykluczanej zawartości

Określ zawartość wykluczaną z skanowania przez pełną ścieżkę pliku.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|ścieżka|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|prawidłowe ścieżki|
|**Komentarze**|Ma zastosowanie tylko w *$type* *wykluczonych danychPath*|
|||

## <a name="supported-exclusion-types"></a>Obsługiwane typy wykluczeń

W poniższej tabeli przedstawiono typy wykluczeń obsługiwane przez program Defender for Endpoint na komputerze Mac.

<br>

****

|Wykluczenie|Definicja|Przykłady|
|---|---|---|
|Rozszerzenie pliku|Wszystkie pliki z rozszerzeniem w dowolnym miejscu na urządzeniu|`.test`|
|Plik|Określony plik oznaczony pełną ścieżką|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`|
|Folder|Wszystkie pliki w określonym folderze (cyklicznie)|`/var/log/` <p> `/var/*/`|
|Proces|Określony proces (określony przez pełną ścieżkę lub nazwę pliku) i wszystkie otwarte przez niego pliki|`/bin/cat` <p> `cat` <p> `c?t`|
||||

> [!IMPORTANT]
> Powyższe ścieżki muszą być twardymi linkami, a nie łączami symbolicznymi, aby można było je pomyślnie wykluczyć. Możesz sprawdzić, czy ścieżka jest linkiem symbolicznym, uruchamiając .`file <path-name>`

Wykluczenia plików, folderów i procesów obsługują następujące symbole wieloznaczne:

<br>

****

|Symbol wieloznaczny|Opis|Przykład|Dopasowania|Nie jest zgodne|
|---|---|---|---|---|
|\*|Zastępuje dowolną liczbę dowolnych znaków z uwzględnieniem znaków brak (zwróć uwagę, że jeśli ta symbol wieloznaczny zostanie użyty w ścieżce, zastąpi tylko jeden folder)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`|
|?|Dopasowuje dowolny pojedynczy znak.|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`|
||||||

### <a name="path-type-file--directory"></a>Typ ścieżki (plik/katalog)

Wskaż, czy *właściwość ścieżki* odwołuje się do pliku lub katalogu.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|isDirectory|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|false (domyślnie) <p> true|
|**Komentarze**|Ma zastosowanie tylko w *$type* *wykluczonych danychPath*|
|||

### <a name="file-extension-excluded-from-the-scan"></a>Rozszerzenie pliku wykluczonych podczas skanowania

Określ zawartość wykluczaną z skanowania za pomocą rozszerzenia pliku.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|rozszerzenie|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|prawidłowe rozszerzenia plików|
|**Komentarze**|Ma zastosowanie tylko w *$type* *excludedFileExtension*|
|||

### <a name="process-excluded-from-the-scan"></a>Proces wykluczony podczas skanowania

Określ proces, w przypadku którego wszystkie działania na plikach są wykluczane z skanowania. Proces można określić za pomocą nazwy ( `cat`na przykład ) lub pełnej ścieżki (na przykład `/bin/cat`).

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|nazwa|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|dowolny ciąg|
|**Komentarze**|Dotyczy tylko, *jeśli $type* jest *wykluczonaNazwa_pliku*|
|||

#### <a name="allowed-threats"></a>Dozwolone zagrożenia

Określ zagrożenia według nazwy, które nie są blokowane przez program Defender dla punktu końcowego na komputerze Mac. Te zagrożenia będą mogły działać.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|allowedThreats|
|**Typ danych**|Tablica ciągów|
|||

#### <a name="disallowed-threat-actions"></a>Niedozwolone działania związane z zagrożeniami

Ogranicza akcje, które lokalny użytkownik urządzenia może podjąć w przypadku wykrycia zagrożeń. Akcje zawarte na tej liście nie są wyświetlane w interfejsie użytkownika.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|disallowedThreatActions|
|**Typ danych**|Tablica ciągów|
|**Dopuszczalne wartości**|zezwalaj (ogranicza możliwość zezwalania użytkownikom na zagrożenia) <p> przywracanie (ogranicza możliwość przywracania zagrożeń z kwarantanny przez użytkowników)|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 100.83.73 lub wyższej.|
|||

#### <a name="threat-type-settings"></a>Ustawienia typu zagrożeń

Określ obsługę określonych typów zagrożeń przez usługę Microsoft Defender for Endpoint w systemie macOS.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|threatTypeSettings|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|||

##### <a name="threat-type"></a>Typ zagrożenia

Określ typy zagrożeń.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|klawisz|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|potentially_unwanted_application <p> archive_bomb|
|||

##### <a name="action-to-take"></a>Czynność do podjęcia

Określ, jakie działania będą podjąć w przypadku wykrycia zagrożenia typu określonego w poprzedniej sekcji. Wybierz jedną z następujących opcji:

- **Inspekcja**: urządzenie nie jest chronione przed tego typu zagrożeniami, ale jest rejestrowane zgłoszenie zagrożenia.
- **Blokowanie**: urządzenie jest chronione przed tego typu zagrożeniami i w interfejsie użytkownika i na konsoli zabezpieczeń jest powiadamiane o tym użytkowniku.
- **Wyłączone**: urządzenie nie jest chronione przed tego typu zagrożeniami i nic nie jest rejestrowane.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|wartość|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|inspekcja (domyślna) <p> blok <p> wyłączone|
|||

#### <a name="threat-type-settings-merge-policy"></a>Zasady scalania ustawień typu zagrożeń

Określ zasady scalania dla ustawień typu zagrożeń. Może to być połączenie ustawień zdefiniowanych przez administratora i zdefiniowanych przez użytkownika (`merge`) lub tylko ustawień zdefiniowanych przez administratora (`admin_only`). To ustawienie może być używane do ograniczania użytkownikom lokalnym definiowania własnych ustawień dla różnych typów zagrożeń.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|threatTypeSettingsMergePolicy|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|scalanie (domyślnie) <p> admin_only|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 100.83.73 lub wyższej.|
|||

#### <a name="antivirus-scan-history-retention-in-days"></a>Przechowywanie historii skanowania antywirusowego (w dniach)

Określ liczbę dni, przez które wyniki są zachowywane w historii skanowania na urządzeniu. Stare wyniki skanowania zostaną usunięte z historii. Stare pliki poddane kwarantannie, które są również usuwane z dysku.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|scanResultsRetentionDays|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|90 (domyślnie). Dozwolone wartości to od 1 dnia do 180 dni.|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 101.07.23 lub wyższej.|
|||

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Maksymalna liczba elementów w historii skanowania oprogramowania antywirusowego

Określ maksymalną liczbę wpisów do historii skanowania. Wpisy obejmują wszystkie skany na żądanie wykonane w przeszłości oraz wszystkie wykrywanie oprogramowania antywirusowego.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|scanHistoryMaximumItems|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|10000 (domyślnie). Dozwolone wartości to od 5000 elementów do 15000 elementów.|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 101.07.23 lub wyższej.|
|||

### <a name="cloud-delivered-protection-preferences"></a>Preferencje ochrony w chmurze

Skonfiguruj funkcje ochrony oparte na chmurze programu Microsoft Defender dla punktu końcowego w systemie macOS.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|cloudService|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|||

#### <a name="enable--disable-cloud-delivered-protection"></a>Włączanie/wyłączanie ochrony w chmurze

Określ, czy chcesz włączyć ochronę w chmurze dla urządzenia. Aby poprawić bezpieczeństwo usług, zalecamy, aby ta funkcja była włączona.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|włączone|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|||

#### <a name="diagnostic-collection-level"></a>Poziom kolekcji diagnostycznej

Dane diagnostyczne służą do zabezpieczania i aktualnego działania programu Microsoft Defender for Endpoint, wykrywania, diagnozowania i rozwiązywania problemów oraz do ulepszeń produktu. To ustawienie określa poziom diagnostyki wysyłanej przez usługę Microsoft Defender dla punktu końcowego do firmy Microsoft.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|diagnosticLevel|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|opcjonalne (domyślne) <p> Wymagane|
|||

#### <a name="enable--disable-automatic-sample-submissions"></a>Włączanie/wyłączanie automatycznych przesyłania próbek

Ustala, czy podejrzane próbki (które mogą zawierać zagrożenia) są wysyłane do firmy Microsoft. Zostanie wyświetlony monit, jeśli przesłany plik prawdopodobnie zawiera informacje osobiste.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|automaticSampleSubmission|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|||

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Włączanie/wyłączanie aktualizacji automatycznej analizy zabezpieczeń

Określenie, czy aktualizacje analizy zabezpieczeń są instalowane automatycznie:

<br>

****

|Sekcja|Value|
|---|---|
|**Klucz**|automaticDefinitionUpdateEnabled|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|||

### <a name="user-interface-preferences"></a>Preferencje interfejsu użytkownika

Zarządzaj preferencjami interfejsu użytkownika programu Microsoft Defender for Endpoint w systemie macOS.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|userInterface|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|||

#### <a name="show--hide-status-menu-icon"></a>Show/hide status menu icon

Określ, czy pokazać lub ukryć ikonę menu statusu w prawym górnym rogu ekranu.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|hideStatusMenuIcon|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|false (domyślnie) <p> true|
|||

#### <a name="show--hide-option-to-send-feedback"></a>Opcja Pokazywanie/ukrywanie w celu wysłania opinii

Określ, czy użytkownicy mogą przesyłać opinie do firmy Microsoft, przechodząc do .`Help` > `Send Feedback`

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|userInitiatedFeedback|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|włączony (domyślnie) <p> wyłączona|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 101.19.61 lub wyższej.|
|||



#### <a name="control-sign-in-to-consumer-version-of-microsoft-defender"></a>Sterowanie logowaniem się do wersji programu Microsoft Defender dla klientów konsumenckich

Określ, czy użytkownicy mogą logować się do wersji programu Microsoft Defender dla klientów indywidualnych.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|consumerExperience|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|włączony (domyślnie) <p> wyłączona|
|**Komentarze**|Dostępny w programie Microsoft Defender dla punktu końcowego w wersji 101.60.18 lub wyższej.|
|||


### <a name="endpoint-detection-and-response-preferences"></a>Wykrywanie punktu końcowego i preferencje odpowiedzi

Zarządzaj preferencjami składnika wykrywanie i reagowanie w punktach końcowych (EDR) programu Microsoft Defender for Endpoint w systemie macOS.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|edr|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|||

#### <a name="device-tags"></a>Tagi urządzeń

Określ nazwę tagu i jego wartość.

- Tag GROUP oznacza urządzenie określoną wartością. Tag jest odzwierciedlany w portalu pod stroną urządzenia i może być używany do filtrowania i grupowania urządzeń.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|tagi|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|||

##### <a name="type-of-tag"></a>Typ tagu

Określa typ tagu

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|klawisz|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|`GROUP`|
|||

##### <a name="value-of-tag"></a>Wartość tagu

Określa wartość tagu

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.wdav`|
|**Klucz**|wartość|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|dowolny ciąg|
|||

> [!IMPORTANT]
>
> - Można ustawić tylko jedną wartość dla każdego typu tagu.
> - Typ tagów jest unikatowy i nie należy go powtarzać w tym samym profilu konfiguracji.

## <a name="recommended-configuration-profile"></a>Zalecany profil konfiguracji

Aby rozpocząć, zalecamy w przedsiębiorstwie następującą konfigurację, aby korzystać ze wszystkich funkcji ochrony zapewnianych przez program Microsoft Defender for Endpoint.

Następujący profil konfiguracji (lub, w przypadku usługi JAMF, lista właściwości, która może zostać przesłana do profilu konfiguracji ustawień niestandardowych) będzie:

- Włączanie ochrony w czasie rzeczywistym (RTP)
- Określ sposób obsługi następujących typów zagrożeń:
  - **Potencjalnie niepożądane aplikacje (PUA)** są blokowane
  - **Archiwalne bomby** (plik o wysokiej stopie kompresji) są podejrzliwnie podejrzliwą do programu Microsoft Defender for Endpoint logs
- Włączanie aktualizacji automatycznej analizy zabezpieczeń
- Włączanie ochrony w chmurze
- Włączanie automatycznego przesyłania próbek

### <a name="property-list-for-jamf-recommended-configuration-profile"></a>Lista właściwości profilu konfiguracji zalecanego przez program JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
</dict>
</plist>
```

### <a name="intune-recommended-profile"></a>Profil zalecany w usłudze Intune

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="full-configuration-profile-example"></a>Przykład profilu pełnej konfiguracji

Poniższe szablony zawierają wpisy wszystkich ustawień opisanych w tym dokumencie i mogą być używane w bardziej zaawansowanych scenariuszach, w których potrzebujesz większej kontroli nad programem Microsoft Defender for Endpoint w systemie macOS.

### <a name="property-list-for-jamf-full-configuration-profile"></a>Lista właściwości dla pełnego profilu konfiguracji usługi JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>scanAfterDefinitionUpdate</key>
        <true/>
        <key>scanArchives</key>
        <true/>
        <key>maximumOnDemandScanThreads</key>
        <integer>2</integer>
        <key>exclusions</key>
        <array>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <false/>
                <key>path</key>
                <string>/var/log/system.log</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/home</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/Users/*/git</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileExtension</string>
                <key>extension</key>
                <string>pdf</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileName</string>
                <key>name</key>
                <string>cat</string>
            </dict>
        </array>
        <key>exclusionsMergePolicy</key>
        <string>merge</string>
        <key>allowedThreats</key>
        <array>
            <string>EICAR-Test-File (not a virus)</string>
        </array>
        <key>disallowedThreatActions</key>
        <array>
            <string>allow</string>
            <string>restore</string>
        </array>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
        <key>threatTypeSettingsMergePolicy</key>
        <string>merge</string>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>diagnosticLevel</key>
        <string>optional</string>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
    <key>edr</key>
    <dict>
        <key>tags</key>
        <array>
            <dict>
                <key>key</key>
                <string>GROUP</string>
                <key>value</key>
                <string>ExampleTag</string>
            </dict>
        </array>
    </dict>
    <key>userInterface</key>
    <dict>
        <key>hideStatusMenuIcon</key>
        <false/>
        <key>userInitiatedFeedback</key>
        <string>enabled</string>
    </dict>
</dict>
</plist>
```

### <a name="intune-full-profile"></a>Intune full profile

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>scanAfterDefinitionUpdate</key>
                    <true/>
                    <key>scanArchives</key>
                    <true/>
                    <key>maximumOnDemandScanThreads</key>
                    <integer>1</integer>
                    <key>exclusions</key>
                    <array>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <false/>
                            <key>path</key>
                            <string>/var/log/system.log</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/home</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/Users/*/git</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileExtension</string>
                            <key>extension</key>
                            <string>pdf</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileName</string>
                            <key>name</key>
                            <string>cat</string>
                        </dict>
                    </array>
                    <key>exclusionsMergePolicy</key>
                    <string>merge</string>
                    <key>allowedThreats</key>
                    <array>
                        <string>EICAR-Test-File (not a virus)</string>
                    </array>
                    <key>disallowedThreatActions</key>
                    <array>
                        <string>allow</string>
                        <string>restore</string>
                    </array>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                    <key>threatTypeSettingsMergePolicy</key>
                    <string>merge</string>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>diagnosticLevel</key>
                    <string>optional</string>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
                <key>edr</key>
                <dict>
                    <key>tags</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>GROUP</string>
                            <key>value</key>
                            <string>ExampleTag</string>
                        </dict>
                    </array>
                </dict>
                <key>userInterface</key>
                <dict>
                    <key>hideStatusMenuIcon</key>
                    <false/>
                    <key>userInitiatedFeedback</key>
                    <string>enabled</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="property-list-validation"></a>Sprawdzanie poprawności listy właściwości

Lista właściwości musi być prawidłowym *plikiem plist* . Można to sprawdzić, wykonując:

```bash
plutil -lint com.microsoft.wdav.plist
```

```Output
com.microsoft.wdav.plist: OK
```

Jeśli plik jest dobrze formowany, `OK` powyższe polecenia są wyprowadzone i zwraca kod wyjścia `0`. W przeciwnym razie zostanie wyświetlony błąd opisujący problem, a polecenie zwróci kod wyjścia `1`.

## <a name="configuration-profile-deployment"></a>Wdrożenie profilu konfiguracji

Profil konfiguracji dla przedsiębiorstwa można wdrożyć za pośrednictwem konsoli zarządzania, z których korzysta przedsiębiorstwo. Poniższe sekcje zawierają instrukcje dotyczące wdrażania tego profilu za pomocą usługi JAMF i Intune.

### <a name="jamf-deployment"></a>Wdrożenie usługi JAMF

W konsoli JAMF otwórz pozycję **Profile** \> konfiguracji **komputerów, przejdź** do profilu konfiguracji, który chcesz użyć, a następnie wybierz pozycję Ustawienia **Ustawienia**. Utwórz wpis, jako `com.microsoft.wdav` domenę preferencji, i przekaż *plik .plist* , który został wcześniej przezNawisły.

> [!CAUTION]
> Należy wprowadzić prawidłową domenę preferencji (). W`com.microsoft.wdav` przeciwnym razie preferencje nie będą rozpoznawane przez usługę Microsoft Defender for Endpoint.

### <a name="intune-deployment"></a>Wdrożenie usługi Intune

1. Otwórz **okno Zarządzanie** \> **konfiguracją urządzenia**. Wybierz **pozycję Zarządzaj profilami** \>  \> **Utwórz profil**.

2. Wybierz nazwę profilu. Zmień **platformę=macOS** na **Profile type=Custom**. Wybierz pozycję Konfiguruj.

3. Zapisz plik plist, który został powstały wcześniej jako `com.microsoft.wdav.xml`.

4. Wprowadź `com.microsoft.wdav` nazwę profilu **konfiguracji niestandardowej**.

5. Otwórz profil konfiguracji i przekaż `com.microsoft.wdav.xml` plik. (Ten plik został utworzony w kroku 3).

6. Wybierz przycisk **OK**.

7. Wybierz **pozycję Zarządzaj** \> **zadaniami**. Na karcie **Dołączanie** wybierz pozycję **Przypisz do wszystkich użytkowników & wszystkich urządzeń**.

> [!CAUTION]
> Należy wprowadzić prawidłową nazwę profilu konfiguracji niestandardowej. w przeciwnym razie te preferencje nie będą rozpoznawane przez usługę Microsoft Defender for Endpoint.

## <a name="resources"></a>Zasoby

- [Dokumentacja dotycząca profilu konfiguracji (Dokumentacja dla deweloperów firmy Apple)](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
