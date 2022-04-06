---
title: Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux
ms.reviewer: ''
description: Opis sposobu konfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux w przedsiębiorstwach.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.openlocfilehash: 1a579944fa0f7578fa2afcf66472cebbb6f07037
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663781"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-linux"></a>Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!IMPORTANT]
> Ten temat zawiera instrukcje dotyczące ustawiania preferencji dla usługi Defender dla punktu końcowego w systemie Linux w środowiskach przedsiębiorstwa. Jeśli chcesz skonfigurować produkt na urządzeniu z poziomu wiersza polecenia, zobacz [Zasoby](linux-resources.md#configure-from-the-command-line).

W środowiskach przedsiębiorstwa usługą Defender for Endpoint w systemie Linux można zarządzać za pośrednictwem profilu konfiguracji. Ten profil jest wdrażany z wybranego narzędzia do zarządzania. Preferencje zarządzane przez przedsiębiorstwo mają pierwszeństwo przed preferencjami ustawionymi lokalnie na urządzeniu. Innymi słowy, użytkownicy w przedsiębiorstwie nie mogą zmieniać preferencji ustawionych za pomocą tego profilu konfiguracji.

W tym artykule opisano strukturę tego profilu (w tym zalecany profil, którego można użyć do rozpoczęcia pracy) oraz instrukcje dotyczące sposobu wdrażania profilu.

## <a name="configuration-profile-structure"></a>Struktura profilu konfiguracji

Profil konfiguracji to plik json, który składa się z wpisów zidentyfikowanych przez klucz (co oznacza nazwę preferencji), po którym następuje wartość, która zależy od charakteru preferencji. Wartości mogą być proste, takie jak wartość liczbowa lub złożone, takie jak zagnieżdżona lista preferencji.

Zazwyczaj należy użyć narzędzia do zarządzania konfiguracją, aby wypchnąć plik o nazwie ```mdatp_managed.json``` w lokalizacji ```/etc/opt/microsoft/mdatp/managed/```.

Najwyższy poziom profilu konfiguracji zawiera preferencje dla całego produktu i wpisy dla obszarów podrzędnych produktu, co opisano bardziej szczegółowo w następnych sekcjach.

### <a name="antivirus-engine-preferences"></a>Preferencje aparatu antywirusowego

Sekcja *antivirusEngine* profilu konfiguracji służy do zarządzania preferencjami składnika antywirusowego produktu.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|antivirusEngine|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

#### <a name="enforcement-level-for-antivirus-engine"></a>Poziom wymuszania dla aparatu antywirusowego

Określa preferencje wymuszania aparatu antywirusowego. Istnieją trzy wartości dotyczące ustawiania poziomu wymuszania:

- W czasie rzeczywistym (`real_time`): włączono ochronę w czasie rzeczywistym (skanuj pliki w miarę uzyskiwania dostępu).
- Na żądanie (`on_demand`): pliki są skanowane tylko na żądanie. W tym:
  - Ochrona w czasie rzeczywistym jest wyłączona.
- Pasywne (`passive`): uruchamia aparat antywirusowy w trybie pasywnym. W tym:
  - Ochrona w czasie rzeczywistym jest wyłączona.
  - Skanowanie na żądanie jest włączone.
  - Automatyczne korygowanie zagrożeń jest wyłączone.
  - Aktualizacje analizy zabezpieczeń są włączone.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|enforcementLevel|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|real_time (wartość domyślna) <p> on_demand <p> Pasywne|
|**Komentarze**|Dostępne w usłudze Defender for Endpoint w wersji 101.10.72 lub nowszej.|
|


#### <a name="enabledisable-behavior-monitoring"></a>Włączanie/wyłączanie monitorowania zachowania 

Określa, czy funkcja monitorowania i blokowania zachowania jest włączona na urządzeniu, czy nie. Aby zwiększyć skuteczność ochrony przed zabezpieczeniami, zalecamy włączenie tej funkcji.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|behaviorMonitoring|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|wyłączone (ustawienie domyślne) <p> włączone (ustawienie domyślne)|
|**Komentarze**|Dostępne w usłudze Defender for Endpoint w wersji 101.45.00 lub nowszej.|
  
#### <a name="run-a-scan-after-definitions-are-updated"></a>Uruchamianie skanowania po zaktualizowaniu definicji

Określa, czy należy rozpocząć skanowanie procesu po pobraniu nowych aktualizacji analizy zabezpieczeń na urządzeniu. Włączenie tego ustawienia spowoduje wyzwolenie skanowania antywirusowego w uruchomionych procesach urządzenia.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|scanAfterDefinitionUpdate|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (wartość domyślna) <p> False|
|**Komentarze**|Dostępne w usłudze Defender for Endpoint w wersji 101.45.00 lub nowszej.|
|

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Skanuj archiwa (tylko skanowanie antywirusowe na żądanie)

Określa, czy skanować archiwa podczas skanowania antywirusowego na żądanie.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|scanArchives|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (wartość domyślna) <p> False|
|**Komentarze**|Dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender wersji 101.45.00 lub nowszej.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Stopień równoległości skanowania na żądanie

Określa stopień równoległości skanowania na żądanie. Odpowiada to liczbie wątków używanych do skanowania i wpływa na użycie procesora CPU, a także czas trwania skanowania na żądanie.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|maximumOnDemandScanThreads|
|**Typ danych**|Liczba całkowita|
|**Dopuszczalne wartości**|2 (wartość domyślna). Dozwolone wartości to liczby całkowite z zakresu od 1 do 64.|
|**Komentarze**|Dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender wersji 101.45.00 lub nowszej.|
|||
  

#### <a name="exclusion-merge-policy"></a>Zasady scalania wykluczeń

Określa zasady scalania dla wykluczeń. Może to być kombinacja wykluczeń zdefiniowanych przez administratora i zdefiniowanych przez użytkownika (`merge`) lub tylko wykluczeń zdefiniowanych przez administratora (`admin_only`). To ustawienie może służyć do ograniczania użytkownikom lokalnym definiowania własnych wykluczeń.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|exclusionsMergePolicy|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|scalanie (domyślne) <p> admin_only|
|**Komentarze**|Dostępne w usłudze Defender for Endpoint w wersji 100.83.73 lub nowszej.|
|

#### <a name="scan-exclusions"></a>Wykluczeń skanowania

Jednostki, które zostały wykluczone ze skanowania. Wykluczenia można określić za pomocą pełnych ścieżek, rozszerzeń lub nazw plików.
(Wykluczenia są określane jako tablica elementów, administrator może określić dowolną liczbę elementów w dowolnej kolejności).

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|Wykluczenia|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

##### <a name="type-of-exclusion"></a>Typ wykluczenia

Określa typ zawartości wykluczonej ze skanowania.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|$type|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|

##### <a name="path-to-excluded-content"></a>Ścieżka do wykluczonej zawartości

Służy do wykluczania zawartości ze skanowania za pomocą pełnej ścieżki pliku.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|Ścieżka|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|prawidłowe ścieżki|
|**Komentarze**|Dotyczy tylko wtedy, gdy *$type* jest *excludedPath*|
|

##### <a name="path-type-file--directory"></a>Typ ścieżki (plik/katalog)

Wskazuje, czy właściwość *path* odwołuje się do pliku lub katalogu.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|isDirectory|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|false (wartość domyślna) <p> True|
|**Komentarze**|Dotyczy tylko wtedy, gdy *$type* jest *excludedPath*|
|

##### <a name="file-extension-excluded-from-the-scan"></a>Rozszerzenie pliku wykluczone ze skanowania

Służy do wykluczania zawartości ze skanowania według rozszerzenia pliku.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|Rozszerzenie|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|prawidłowe rozszerzenia plików|
|**Komentarze**|Dotyczy tylko wtedy, *gdy $type* jest *wykluczoneFileExtension*|
|

##### <a name="process-excluded-from-the-scan"></a>Proces wykluczony ze skanowania*

Określa proces, dla którego wszystkie działania plików są wykluczone ze skanowania. Proces można określić za pomocą jego nazwy (na przykład `cat`) lub pełnej ścieżki (na przykład `/bin/cat`).

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|Nazwa|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|dowolny ciąg|
|**Komentarze**|Dotyczy tylko wtedy, *gdy $type* jest *wykluczoneFileName*|
|

#### <a name="allowed-threats"></a>Dozwolone zagrożenia

Lista zagrożeń (identyfikowanych według ich nazwy), które nie są blokowane przez produkt i zamiast tego mogą być uruchamiane.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|allowedThreats|
|**Typ danych**|Tablica ciągów|
|

#### <a name="disallowed-threat-actions"></a>Niedozwolone akcje zagrożeń

Ogranicza akcje, które może wykonać lokalny użytkownik urządzenia po wykryciu zagrożeń. Akcje zawarte na tej liście nie są wyświetlane w interfejsie użytkownika.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|disallowedThreatActions|
|**Typ danych**|Tablica ciągów|
|**Dopuszczalne wartości**|zezwalaj (ogranicza użytkownikom możliwość zezwalania na zagrożenia) <p> przywracanie (ogranicza użytkownikom możliwość przywracania zagrożeń z kwarantanny)|
|**Komentarze**|Dostępne w usłudze Defender for Endpoint w wersji 100.83.73 lub nowszej.|
|

#### <a name="threat-type-settings"></a>Ustawienia typu zagrożenia

Preferencja *threatTypeSettings* w aparacie antywirusowym służy do kontrolowania sposobu obsługi określonych typów zagrożeń przez produkt.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|threatTypeSettings|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

##### <a name="threat-type"></a>Typ zagrożenia

Typ zagrożenia, dla którego skonfigurowano zachowanie.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|Klucz|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|potentially_unwanted_application <p> archive_bomb|
|

##### <a name="action-to-take"></a>Akcja do wykonania

Akcja do wykonania w przypadku wystąpienia zagrożenia typu określonego w poprzedniej sekcji. Może to być:

- **Inspekcja**: urządzenie nie jest chronione przed tego typu zagrożeniem, ale rejestrowany jest wpis dotyczący zagrożenia.
- **Blokuj**: urządzenie jest chronione przed tego typu zagrożeniem i otrzymujesz powiadomienie w konsoli zabezpieczeń.
- **Wyłączone**: urządzenie nie jest chronione przed tego typu zagrożeniem i nic nie jest rejestrowane.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|Wartość|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|audit (wartość domyślna) <p> Bloku <p> wyłączone|
|

#### <a name="threat-type-settings-merge-policy"></a>Zasady scalania ustawień typu zagrożenia

Określa zasady scalania dla ustawień typu zagrożenia. Może to być kombinacja ustawień zdefiniowanych przez administratora i zdefiniowanych przez użytkownika (`merge`) lub tylko ustawień zdefiniowanych przez administratora (`admin_only`). To ustawienie może służyć do ograniczania użytkownikom lokalnym możliwości definiowania własnych ustawień dla różnych typów zagrożeń.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|threatTypeSettingsMergePolicy|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|scalanie (domyślne) <p> admin_only|
|**Komentarze**|Dostępne w usłudze Defender for Endpoint w wersji 100.83.73 lub nowszej.|
|

#### <a name="antivirus-scan-history-retention-in-days"></a>Przechowywanie historii skanowania antywirusowego (w dniach)

Określ liczbę dni przechowywania wyników w historii skanowania na urządzeniu. Stare wyniki skanowania są usuwane z historii. Stare pliki poddane kwarantannie, które również są usuwane z dysku.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|scanResultsRetentionDays|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|90 (wartość domyślna). Dozwolone wartości to od 1 dnia do 180 dni.|
|**Komentarze**|Dostępne w usłudze Defender for Endpoint w wersji 101.04.76 lub nowszej.|
|

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Maksymalna liczba elementów w historii skanowania antywirusowego

Określ maksymalną liczbę wpisów do zachowania w historii skanowania. Wpisy obejmują wszystkie skany na żądanie wykonywane w przeszłości i wszystkie wykrycia antywirusowe.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|scanHistoryMaximumItems|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|10000 (wartość domyślna). Dozwolone wartości to od 5000 do 15000 elementów.|
|**Komentarze**|Dostępne w usłudze Defender for Endpoint w wersji 101.04.76 lub nowszej.|
|

### <a name="cloud-delivered-protection-preferences"></a>Preferencje ochrony dostarczanej w chmurze

Wpis *cloudService* w profilu konfiguracji służy do konfigurowania funkcji ochrony opartej na chmurze produktu.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|cloudService|
|**Typ danych**|Słownik (preferencja zagnieżdżona)|
|**Komentarze**|Opis zawartości słownika można znaleźć w poniższych sekcjach.|
|

#### <a name="enable--disable-cloud-delivered-protection"></a>Włączanie/wyłączanie ochrony dostarczanej w chmurze

Określa, czy ochrona dostarczana w chmurze jest włączona na urządzeniu, czy nie. Aby zwiększyć bezpieczeństwo usług, zalecamy włączenie tej funkcji.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|Włączone|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (wartość domyślna) <p> False|
|

#### <a name="diagnostic-collection-level"></a>Poziom kolekcji diagnostycznej

Dane diagnostyczne służą do zapewnienia bezpieczeństwa i aktualności usługi Defender for Endpoint, wykrywania, diagnozowania i rozwiązywania problemów, a także wprowadzania ulepszeń produktu. To ustawienie określa poziom diagnostyki wysyłanej przez produkt do firmy Microsoft.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|diagnosticLevel|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|opcjonalne (domyślne) <p> Wymagane|
|

#### <a name="enable--disable-automatic-sample-submissions"></a>Włączanie/wyłączanie automatycznych przesyłania przykładów

Określa, czy podejrzane próbki (które mogą zawierać zagrożenia) są wysyłane do firmy Microsoft. Istnieją trzy poziomy kontroli przesyłania przykładów:

- **Brak**: firma Microsoft nie przesyła żadnych podejrzanych przykładów.
- **Sejf**: automatycznie przesyłane są tylko podejrzane przykłady, które nie zawierają danych osobowych. Jest to wartość domyślna dla tego ustawienia.
- **Wszystkie**: wszystkie podejrzane przykłady są przesyłane do firmy Microsoft.

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|automaticSampleSubmissionConsent|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|Brak <p> safe (wartość domyślna) <p> Wszystkie|
|

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Włączanie/wyłączanie automatycznych aktualizacji analizy zabezpieczeń

Określa, czy aktualizacje analizy zabezpieczeń są instalowane automatycznie:

<br>

****

|Opis|Value|
|---|---|
|**Klucz**|automaticDefinitionUpdateEnabled|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|true (wartość domyślna) <p> False|
|

## <a name="recommended-configuration-profile"></a>Zalecany profil konfiguracji

Aby rozpocząć pracę, zalecamy korzystanie ze wszystkich funkcji ochrony udostępnianych przez usługę Defender for Endpoint w następującym profilu konfiguracji dla przedsiębiorstwa.

Następujący profil konfiguracji:

- Włączanie ochrony w czasie rzeczywistym (RTP)
- Określ sposób obsługi następujących typów zagrożeń:
  - **Potencjalnie niechciane aplikacje (PUA)** są blokowane
  - **Bomby archiwalne** (plik o wysokiej szybkości kompresji) są poddawane inspekcji w dziennikach produktów
- Włączanie automatycznych aktualizacji analizy zabezpieczeń
- Włączanie ochrony dostarczanej w chmurze
- Włączanie automatycznego przesyłania przykładów na `safe` poziomie
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

## <a name="full-configuration-profile-example"></a>Przykład pełnego profilu konfiguracji

Poniższy profil konfiguracji zawiera wpisy dla wszystkich ustawień opisanych w tym dokumencie i może służyć do bardziej zaawansowanych scenariuszy, w których chcesz mieć większą kontrolę nad produktem.

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

## <a name="add-tag-or-group-id-to-the-configuration-profile"></a>Dodawanie tagu lub identyfikatora grupy do profilu konfiguracji

Po pierwszym uruchomieniu `mdatp health` polecenia wartość tagu i identyfikatora grupy będzie pusta. Aby dodać tag lub identyfikator grupy do `mdatp_managed.json` pliku, wykonaj poniższe kroki:
  
  1. Otwórz profil konfiguracji ze ścieżki `/etc/opt/microsoft/mdatp/managed/mdatp_managed.json`.
  2. Przejdź do dolnej części pliku, gdzie `cloudService` znajduje się blok.
  3. Dodaj wymagany tag lub identyfikator grupy jako poniższy przykład na końcu zamykającego nawiasu klamrowego `cloudService`dla elementu .

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
  > Nie zapomnij dodać przecinka po zamykającym nawiasie klamrowym na końcu `cloudService` bloku. Upewnij się również, że istnieją dwa zamykające nawiasy klamrowe po dodaniu bloku Tag lub Identyfikator grupy (zobacz powyższy przykład). Obecnie jedyną obsługiwaną nazwą klucza tagów jest `GROUP`. 
  
## <a name="configuration-profile-validation"></a>Sprawdzanie poprawności profilu konfiguracji

Profil konfiguracji musi być prawidłowym plikiem w formacie JSON. Istnieje wiele narzędzi, których można użyć do zweryfikowania tego. Jeśli na przykład `python` zainstalowano na urządzeniu:

```bash
python -m json.tool mdatp_managed.json
```

Jeśli kod JSON jest dobrze sformułowany, powyższe polecenie wyprowadza go z powrotem do terminalu i zwraca kod zakończenia .`0` W przeciwnym razie zostanie wyświetlony błąd opisujący problem, a polecenie zwróci kod zakończenia .`1`

## <a name="verifying-that-the-mdatp_managedjson-file-is-working-as-expected"></a>Sprawdzanie, czy plik mdatp_managed.json działa zgodnie z oczekiwaniami

Aby sprawdzić, czy plik /etc/opt/microsoft/mdatp/managed/mdatp_managed.json działa prawidłowo, obok następujących ustawień powinien zostać wyświetlony komunikat "[managed]":

- cloud_enabled
- cloud_automatic_sample_submission_consent
- passive_mode_enabled
- real_time_protection_enabled
- automatic_definition_update_enabled

> [!NOTE]
> Aby plik mdatp_managed.json został uruchomiony, nie jest wymagane ponowne uruchomienie deamonu `mdatp` .

## <a name="configuration-profile-deployment"></a>Wdrażanie profilu konfiguracji

Po utworzeniu profilu konfiguracji dla przedsiębiorstwa można go wdrożyć za pośrednictwem narzędzia do zarządzania używanego przez przedsiębiorstwo. Usługa Defender dla punktu końcowego w systemie Linux odczytuje konfigurację zarządzana z pliku */etc/opt/microsoft/mdatp/managed/mdatp_managed.json* .
