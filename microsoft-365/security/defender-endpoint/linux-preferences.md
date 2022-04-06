---
title: Ustawianie preferencji dotyczących programu Ochrona punktu końcowego w usłudze Microsoft Defender Linux
ms.reviewer: ''
description: W tym artykule opisano, jak Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux w przedsiębiorstwach.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, installation, deploy, dezinstalacja, 8, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.openlocfilehash: 19e107e500f3c90f00edb81d67e0da05b5e579d4
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634190"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-linux"></a>Ustawianie preferencji dotyczących programu Ochrona punktu końcowego w usłudze Microsoft Defender Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!IMPORTANT]
> Ten temat zawiera instrukcje dotyczące sposobu ustawienia preferencji programu Defender dla punktu końcowego w systemie Linux w środowiskach przedsiębiorstwa. Jeśli chcesz skonfigurować produkt na urządzeniu za pomocą wiersza polecenia, zobacz [Zasoby](linux-resources.md#configure-from-the-command-line).

W środowiskach przedsiębiorstwa usługą Defender for Endpoint dla systemu Linux można zarządzać za pomocą profilu konfiguracji. Ten profil jest wdrażany za pomocą wybranego narzędzia do zarządzania. Preferencje zarządzane przez przedsiębiorstwo mają pierwszeństwo przed preferencjami ustawionymi lokalnie na urządzeniu. Innymi słowy, użytkownicy w przedsiębiorstwie nie mogą zmieniać preferencji ustawionych za pomocą tego profilu konfiguracji.

W tym artykule opisano strukturę tego profilu (w tym zalecany profil, który umożliwia rozpoczynanie pracy) oraz instrukcje dotyczące wdrażania profilu.

## <a name="configuration-profile-structure"></a>Struktura profilu konfiguracji

Profil konfiguracji to plik json składający się z wpisów oznaczonych przez klucz (co oznacza nazwę preferencji), a następnie wartość, która zależy od rodzaju preferencji. Wartości mogą być proste, na przykład wartości liczbowe, lub złożone, na przykład lista zagnieżdżona listy preferencji.

Zazwyczaj za pomocą narzędzia ```mdatp_managed.json``` do zarządzania konfiguracją można wypychać plik z nazwą w lokalizacji ```/etc/opt/microsoft/mdatp/managed/```.

Górny poziom profilu konfiguracji obejmuje preferencje dotyczące całego produktu oraz wpisy dotyczące podobszarów produktu, które szczegółowo opisano w następnych sekcjach.

### <a name="antivirus-engine-preferences"></a>Preferencje aparatu antywirusowego

Sekcja *oprogramowania antywirusowego* w profilu konfiguracji służy do zarządzania preferencjami składnika oprogramowania antywirusowego produktu.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|antivirusEngine|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

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

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|enforcementLevel|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|real_time (domyślnie) <p> on_demand <p> pasywne|
|**Komentarze**|Dostępny w programie Defender dla punktu końcowego w wersji 101.10.72 lub wyższej.|
|


#### <a name="enabledisable-behavior-monitoring"></a>Włączanie/wyłączanie monitorowania zachowania 

Określa, czy funkcja monitorowania zachowania i blokowania jest włączona na urządzeniu. Aby zwiększyć skuteczność ochrony zabezpieczeń, zalecamy, aby ta funkcja była włączona.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|behaviorMonitoring|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|wyłączone (domyślnie) <p> włączony (domyślnie)|
|**Komentarze**|Dostępny w programie Defender dla punktu końcowego w wersji 101.45.00 lub wyższej.|
  
#### <a name="run-a-scan-after-definitions-are-updated"></a>Uruchamianie skanowania po zaktualizowaniu definicji

Określa, czy po pobraniu na urządzenie nowych aktualizacji analizy zabezpieczeń ma być rozpoczynane skanowanie procesu. Włączenie tego ustawienia spowoduje uruchomienie skanowania antywirusowego w uruchomionych procesach urządzenia.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|scanAfterDefinitionUpdate|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|**Komentarze**|Dostępny w programie Defender dla punktu końcowego w wersji 101.45.00 lub wyższej.|
|

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Skanowanie archiwów (tylko skanowanie na żądanie)

Określa, czy podczas skanowania antywirusowego na żądanie mają być skanowane archiwa.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|scanArchives|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|**Komentarze**|Dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender wersji 101.45.00 lub wyższej.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Stopień równoległości skanów na żądanie

Określa stopień równoległości w skanach na żądanie. Odpowiada ona liczbie wątków używanych do skanowania i wpływa na użycie procesora, a także na czas trwania skanowania na żądanie.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|maximumOnDemandKanThreads|
|**Typ danych**|Liczba całkowita|
|**Dopuszczalne wartości**|2 (domyślnie). Dozwolone wartości to liczby całkowite z od 1 do 64.|
|**Komentarze**|Dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender wersji 101.45.00 lub wyższej.|
|||
  

#### <a name="exclusion-merge-policy"></a>Zasady scalania wykluczeń

Określa zasady scalania dla wyjątków. Może to być połączenie wykluczeń zdefiniowanych przez administratora i zdefiniowanych przez użytkownika (`merge`) lub tylko zdefiniowanych przez administratora (`admin_only`). To ustawienie może być używane do ograniczania użytkownikom lokalnym definiowania własnych wykluczeń.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|exclusionsMergePolicy|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|scalanie (domyślnie) <p> admin_only|
|**Komentarze**|Dostępny w programie Defender dla punktu końcowego w wersji 100.83.73 lub wyższej.|
|

#### <a name="scan-exclusions"></a>Wykluczenia skanowania

Jednostki, które zostały wykluczone z skanowania. Wykluczenia można określić za pomocą pełnych ścieżek, rozszerzeń lub nazw plików.
(Wykluczenia są określone jako tablica elementów, administrator może określić dowolną liczbę elementów w dowolnej kolejności).

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|wykluczenia|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

##### <a name="type-of-exclusion"></a>Typ wykluczenia

Określa typ zawartości wykluczanych z skanowania.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|$type|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|excludedPath <p> excludedFileExtension (Wykluczanie pliku) <p> excludedFileName|
|

##### <a name="path-to-excluded-content"></a>Ścieżka do wykluczanej zawartości

Umożliwia wykluczenie zawartości ze skanowania przez pełną ścieżkę pliku.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|ścieżka|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|prawidłowe ścieżki|
|**Komentarze**|Ma zastosowanie tylko w *$type* *wykluczonych danychPath*|
|

##### <a name="path-type-file--directory"></a>Typ ścieżki (plik/katalog)

Wskazuje, czy właściwość *ścieżki* odwołuje się do pliku lub katalogu.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|isDirectory|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|false (domyślnie) <p> true|
|**Komentarze**|Ma zastosowanie tylko w *$type* *wykluczonych danychPath*|
|

##### <a name="file-extension-excluded-from-the-scan"></a>Rozszerzenie pliku wykluczonych podczas skanowania

Umożliwia wykluczenie zawartości ze skanowania według rozszerzenia pliku.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|rozszerzenie|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|prawidłowe rozszerzenia plików|
|**Komentarze**|Ma zastosowanie tylko w *$type* *excludedFileExtension*|
|

##### <a name="process-excluded-from-the-scan"></a>Proces wykluczony w skanie*

Określa proces, dla którego wszystkie działania na plikach są wyłączane z skanowania. Proces można określić za pomocą nazwy ( `cat`na przykład ) lub pełnej ścieżki (na przykład `/bin/cat`).

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|nazwa|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|dowolny ciąg|
|**Komentarze**|Dotyczy tylko, *jeśli $type* jest *wykluczonaNazwa_pliku*|
|

#### <a name="allowed-threats"></a>Dozwolone zagrożenia

Lista zagrożeń (oznaczonych przez ich nazwy), które nie są blokowane przez produkt i można je uruchamiać.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|allowedThreats|
|**Typ danych**|Tablica ciągów|
|

#### <a name="disallowed-threat-actions"></a>Niedozwolone działania związane z zagrożeniami

Ogranicza akcje, które lokalny użytkownik urządzenia może podjąć w przypadku wykrycia zagrożeń. Akcje zawarte na tej liście nie są wyświetlane w interfejsie użytkownika.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|disallowedThreatActions|
|**Typ danych**|Tablica ciągów|
|**Dopuszczalne wartości**|zezwalaj (ogranicza możliwość zezwalania użytkownikom na zagrożenia) <p> przywracanie (ogranicza możliwość przywracania zagrożeń z kwarantanny przez użytkowników)|
|**Komentarze**|Dostępny w programie Defender dla punktu końcowego w wersji 100.83.73 lub wyższej.|
|

#### <a name="threat-type-settings"></a>Ustawienia typu zagrożeń

*Preferencja threatTypeSettings* w a aparatie antywirusowym jest używana do sterowania obsługą określonych typów zagrożeń przez produkt.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|threatTypeSettings|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

##### <a name="threat-type"></a>Typ zagrożenia

Typ zagrożeń, dla których skonfigurowano zachowanie.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|klawisz|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|potentially_unwanted_application <p> archive_bomb|
|

##### <a name="action-to-take"></a>Czynność do podjęcia

Akcja do podjęcia w przypadku zagrożenia typu określonego w poprzedniej sekcji. Mogą być:

- **Inspekcja**: Urządzenie nie jest chronione przed zagrożeniami tego typu, ale jest rejestrowane wpis o zagrożeń.
- **Zablokuj**: Urządzenie jest chronione przed tego typu zagrożeniami i w konsoli zabezpieczeń jest powiadamiane o tym użytkowniku.
- **Wyłączone**: Urządzenie nie jest chronione przed tego typu zagrożeniami i nic nie jest rejestrowane.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|wartość|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|inspekcja (domyślna) <p> blok <p> wyłączone|
|

#### <a name="threat-type-settings-merge-policy"></a>Zasady scalania ustawień typu zagrożeń

Określa zasady scalania dla ustawień typów zagrożeń. Może to być połączenie ustawień zdefiniowanych przez administratora i zdefiniowanych przez użytkownika (`merge`) lub tylko ustawień zdefiniowanych przez administratora (`admin_only`). To ustawienie może być używane do ograniczania użytkownikom lokalnym definiowania własnych ustawień dla różnych typów zagrożeń.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|threatTypeSettingsMergePolicy|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|scalanie (domyślnie) <p> admin_only|
|**Komentarze**|Dostępny w programie Defender dla punktu końcowego w wersji 100.83.73 lub wyższej.|
|

#### <a name="antivirus-scan-history-retention-in-days"></a>Przechowywanie historii skanowania antywirusowego (w dniach)

Określ liczbę dni, przez które wyniki są zachowywane w historii skanowania na urządzeniu. Stare wyniki skanowania zostaną usunięte z historii. Stare pliki poddane kwarantannie, które są również usuwane z dysku.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|scanResultsRetentionDays|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|90 (domyślnie). Dozwolone wartości to od 1 dnia do 180 dni.|
|**Komentarze**|Dostępny w programie Defender dla punktu końcowego w wersji 101.04.76 lub wyższej.|
|

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Maksymalna liczba elementów w historii skanowania oprogramowania antywirusowego

Określ maksymalną liczbę wpisów do historii skanowania. Wpisy obejmują wszystkie skany na żądanie wykonane w przeszłości oraz wszystkie wykrywanie oprogramowania antywirusowego.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|scanHistoryMaximumItems|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|10000 (domyślnie). Dozwolone wartości to od 5000 elementów do 15000 elementów.|
|**Komentarze**|Dostępny w programie Defender dla punktu końcowego w wersji 101.04.76 lub wyższej.|
|

### <a name="cloud-delivered-protection-preferences"></a>Preferencje ochrony w chmurze

Wpis *cloudService* w profilu konfiguracji służy do konfigurowania funkcji ochrony opartej na chmurze produktu.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|cloudService|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

#### <a name="enable--disable-cloud-delivered-protection"></a>Włączanie/wyłączanie ochrony dostarczonej w chmurze

Określa, czy na urządzeniu włączono ochronę w chmurze. Aby poprawić bezpieczeństwo usług, zalecamy, aby ta funkcja była włączona.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|włączone|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|

#### <a name="diagnostic-collection-level"></a>Poziom kolekcji diagnostycznej

Dane diagnostyczne są używane w celu zapewnienia, że program Defender for Endpoint jest bezpieczny i aktualny, wykrywa, diagnozuje i naprawia problemy, a także ulepsza produkty. To ustawienie określa poziom diagnostyki wysyłanej przez produkt do firmy Microsoft.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|diagnosticLevel|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|opcjonalne (domyślne) <p> Wymagane|
|

#### <a name="enable--disable-automatic-sample-submissions"></a>Włączanie/wyłączanie automatycznych przesyłania próbek

Ustala, czy podejrzane próbki (które mogą zawierać zagrożenia) są wysyłane do firmy Microsoft. Istnieją trzy poziomy kontroli przesłania przykładowego:

- **Brak**: żadne podejrzane próbki nie są przesyłane do firmy Microsoft.
- **Sejf**: automatycznie przesyłane są tylko podejrzane próbki, które nie zawierają danych umożliwiających identyfikację użytkownika. Jest to wartość domyślna dla tego ustawienia.
- **Wszystko**: wszystkie podejrzane próbki są przesyłane do firmy Microsoft.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|automaticSampleSubmissionConsent|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|brak <p> bezpieczne (domyślne) <p> wszystkie|
|

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Włączanie/wyłączanie aktualizacji automatycznej analizy zabezpieczeń

Określenie, czy aktualizacje analizy zabezpieczeń są instalowane automatycznie:

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|automaticDefinitionUpdateEnabled|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (domyślnie) <p> fałsz|
|

## <a name="recommended-configuration-profile"></a>Zalecany profil konfiguracji

Aby rozpocząć, zalecamy skorzystanie ze wszystkich funkcji ochrony zapewnianych przez usługę Defender for Endpoint w poniższym profilu konfiguracji przedsiębiorstwa.

Następujący profil konfiguracji:

- Włączanie ochrony w czasie rzeczywistym (RTP)
- Określ sposób obsługi następujących typów zagrożeń:
  - **Potencjalnie niepożądane aplikacje (PUA)** są blokowane
  - **Archiwalne bomby** (pliki o wysokim poziomie kompresji) są rejestrowane w dziennikach produktów
- Włączanie aktualizacji automatycznej analizy zabezpieczeń
- Włączanie ochrony w chmurze
- Włączanie automatycznego przesyłania próbek na `safe` poziomie
- Włączanie monitorowania zachowania

### <a name="sample-profile"></a>Przykładowy profil

```JSON
{
   "antivirusEngine":{
      "behaviorMonitoring":"enabled",
      "enforcementLevel":"real_time",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "automaticDefinitionUpdateEnabled":true,
      "automaticSampleSubmissionConsent":"safe",
      "enabled":true,
      "proxy": "<EXAMPLE DO NOT USE> http://proxy.server:port/"
   }
}
```

## <a name="full-configuration-profile-example"></a>Przykład profilu pełnej konfiguracji

Poniższy profil konfiguracji zawiera wpisy dotyczące wszystkich ustawień opisanych w tym dokumencie i może być używany w bardziej zaawansowanych scenariuszach, w których potrzebujesz większej kontroli nad produktem.

### <a name="full-profile"></a>Pełny profil

```JSON
{
   "antivirusEngine":{
      "behaviorMonitoring":"enabled",
      "enforcementLevel":"real_time",
      "scanAfterDefinitionUpdate":true,
      "scanArchives":true,
      "maximumOnDemandScanThreads":2,
      "exclusionsMergePolicy":"merge",
      "exclusions":[
         {
            "$type":"excludedPath",
            "isDirectory":false,
            "path":"/var/log/system.log"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/run"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/home/*/git"
         },
         {
            "$type":"excludedFileExtension",
            "extension":".pdf"
         },
         {
            "$type":"excludedFileName",
            "name":"cat"
         }
      ],
      "allowedThreats":[
         "<EXAMPLE DO NOT USE>EICAR-Test-File (not a virus)"
      ],
      "disallowedThreatActions":[
         "allow",
         "restore"
      ],
      "threatTypeSettingsMergePolicy":"merge",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "enabled":true,
      "diagnosticLevel":"optional",
      "automaticSampleSubmissionConsent":"safe",
      "automaticDefinitionUpdateEnabled":true,
      "proxy": "<EXAMPLE DO NOT USE> http://proxy.server:port/"
   }
}
```

## <a name="add-tag-or-group-id-to-the-configuration-profile"></a>Dodawanie identyfikatora grupy lub tagu do profilu konfiguracji

Po uruchomieniu tego `mdatp health` polecenia po raz pierwszy wartość tagu i identyfikatora grupy będzie pusta. Aby dodać identyfikator tagu lub grupy do `mdatp_managed.json` pliku, wykonaj następujące czynności:
  
  1. Otwórz profil konfiguracji ze ścieżki `/etc/opt/microsoft/mdatp/managed/mdatp_managed.json`.
  2. Przejdź do dołu pliku, w którym znajduje `cloudService` się blok.
  3. Dodaj wymagany tag lub identyfikator grupy, jak po poniższym przykładzie na końcu zamykającego nawiasu klamrowego .`cloudService`

  ```JSON
    },
    "cloudService": {
      "enabled": true,
      "diagnosticLevel": "optional",
      "automaticSampleSubmissionConsent": "safe",
      "automaticDefinitionUpdateEnabled": true,
      "proxy": "http://proxy.server:port/"
  },
  "edr": {
    "groupIds":"GroupIdExample",
    "tags": [
              {
              "key": "GROUP",
              "value": "Tag"
              }
            ]
        }
  }
  ```

  > [!NOTE]
  > Nie zapomnij dodać przecinka po zamykającym nawiasie klamrowym na końcu bloku `cloudService` . Ponadto upewnij się, że po dodaniu bloku Identyfikator tagu lub Identyfikatora grupy istnieją dwa zamykające nawiasy klamrowe (zobacz powyższy przykład). Obecnie jedyną obsługiwaną nazwą klucza tagów jest `GROUP`. 
  
## <a name="configuration-profile-validation"></a>Sprawdzanie poprawności profilu konfiguracji

Profil konfiguracji musi być prawidłowym plikiem w formacie JSON. Istnieje wiele narzędzi, których można użyć w celu zweryfikowania tego. Jeśli na przykład zainstalowano `python` na urządzeniu:

```bash
python -m json.tool mdatp_managed.json
```

Jeśli JSON jest dobrze formowany, powyższe polecenie zwraca go z powrotem do terminalu i zwraca kod wyjścia `0`. W przeciwnym razie zostanie wyświetlony błąd opisujący problem, a polecenie zwróci kod wyjścia `1`.

## <a name="verifying-that-the-mdatp_managedjson-file-is-working-as-expected"></a>Sprawdzanie, czy plik mdatp_managed.json działa zgodnie z oczekiwaniami

Aby sprawdzić, czy Twój /etc/opt/microsoft/mdatp/managed/mdatp_managed.json działa poprawnie, obok tych ustawień powinien być wyświetlony "[managed]":

- cloud_enabled
- cloud_automatic_sample_submission_consent
- passive_mode_enabled
- real_time_protection_enabled
- automatic_definition_update_enabled

> [!NOTE]
> Aby deamon mdatp_managed.json, `mdatp` nie jest wymagane ponowne uruchomienie tego deamon.

## <a name="configuration-profile-deployment"></a>Wdrożenie profilu konfiguracji

Profil konfiguracji dla przedsiębiorstwa można wdrożyć za pomocą narzędzia do zarządzania, które jest stosowane w przedsiębiorstwie. Program Defender for Endpoint w systemie Linux odczytuje zarządzaną konfigurację z pliku */etc/opt/microsoft/mdatp/managed/mdatp_managed.json* .
