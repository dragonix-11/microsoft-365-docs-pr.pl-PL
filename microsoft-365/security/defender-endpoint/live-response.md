---
title: Badanie jednostek na urządzeniach przy użyciu funkcji live response w programie Ochrona punktu końcowego w usłudze Microsoft Defender
description: Uzyskaj dostęp do urządzenia przy użyciu bezpiecznego połączenia powłoki zdalnej w celu pracy badania i natychmiastowego reagowania na urządzenie w czasie rzeczywistym.
keywords: zdalna, powłoka, połączenie, na żywo, odpowiedź, w czasie rzeczywistym, polecenie, skrypt, remediate, hunt, export, log, drop, download, file,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8987c5642ea48e4c7887735cc0fce0e5bfccc119
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470400"
---
# <a name="investigate-entities-on-devices-using-live-response"></a>Badanie jednostek na urządzeniach przy użyciu funkcji odpowiedzi na żywo

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Funkcja odpowiedzi na żywo zapewnia zespołom operacji zabezpieczeń błyskawiczny dostęp do urządzenia (nazywanego także maszyną) przy użyciu połączenia powłoki zdalnej. Umożliwia to użytkownikom szczegółową pracę w ramach badania i natychmiastowe działania w celu natychmiastowego reagowania na określone zagrożenia w czasie rzeczywistym.

Działanie na żywo ma na celu usprawnianie analiz, umożliwiając zespołowi ds. bezpieczeństwa zbieranie danych forensycznych, uruchamianie skryptów, wysyłanie podejrzanych jednostek na analizy, korygowanie zagrożeń oraz aktywne wyszukiwanie wyłaniających się zagrożeń.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUW]

W odpowiedzi na żywo analitycy mogą wykonywać wszystkie następujące zadania:

- Uruchamianie podstawowych i zaawansowanych poleceń w celu szukania informacji na urządzeniu.
- Pobierz pliki, takie jak próbki złośliwego oprogramowania i wyniki skryptów programu PowerShell.
- Pobieranie plików w tle (nowe!).
- Upload skrypt programu PowerShell lub plik wykonywalny biblioteki i uruchom go na urządzeniu z poziomu dzierżawy.
- Działania naprawcze można podjąć lub cofnąć.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Zanim zainicjujesz sesję na urządzeniu, upewnij się, że spełniasz następujące wymagania:

- **Sprawdź, czy używasz obsługiwanej wersji pakietu Windows**.

  Na urządzeniach musi być uruchomiona jedna z następujących wersji Windows

  - **Windows 10 & 11**
    - [Wersja 1909 lub](/windows/whats-new/whats-new-windows-10-version-1909) nowsza
    - [Wersja 1903](/windows/whats-new/whats-new-windows-10-version-1903) z [kb4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Wersja 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) z [kb4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Wersja 1803 (RS 4) z](/windows/whats-new/whats-new-windows-10-version-1803) [kb4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Wersja 1709 (RS 3) z](/windows/whats-new/whats-new-windows-10-version-1709) [kb4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **macOS** — dotyczy tylko wersji Public Preview, minimalna wymagana wersja: 101.43.84 
  
   > [!NOTE]
   > Obecnie obsługiwane są tylko systemy macOS firmy Intel.
    

  - **Linux** — dotyczy tylko publicznej wersji Zapoznawczej, minimalna wymagana wersja: 101.45.13 
    
  - **Windows Server 2012 R2 —** z [kb5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)
  
  - **Windows Server 2016** — z [kb5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2019**
    - Wersja 1903 lub (z [kb4515384) później](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - Wersja 1809 (z [kb4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

       

- **Włącz odpowiedź na żywo na stronie ustawień zaawansowanych**.

  Musisz włączyć funkcję odpowiedzi na żywo na stronie [Ustawień funkcji zaawansowanych](advanced-features.md) .

  > [!NOTE]
  > Tylko użytkownicy z rolami administratora globalnego lub zabezpieczeń mogą edytować te ustawienia.
  > 
  > Funkcja Automated Investigation musi być włączona w [ustawieniach funkcji zaawansowanych przed](advanced-features.md) włączeniem funkcji odpowiedzi na żywo.

- **Włącz odpowiedź na żywo dla serwerów z zaawansowanej strony ustawień** (zalecane).

  > [!NOTE]
  > Tylko użytkownicy z rolami administratora globalnego lub zabezpieczeń mogą edytować te ustawienia.

- **Upewnij się, że do urządzenia jest przypisany poziom rozwiązywania problemów automatyzacji**.

  Konieczne będzie co najmniej włączenie minimalnego poziomu środków zaradczych dla danej grupy urządzeń. W przeciwnym razie nie będzie można ustanowić sesji na żywo odpowiedzi do członka tej grupy.

  Zostanie wyświetlony następujący komunikat o błędzie:

  :::image type="content" source="images/live-response-error.png" alt-text="Komunikat o błędzie" lightbox="images/live-response-error.png":::

- **Włączanie niepodpisanych skryptów wykonywania odpowiedzi na żywo** (opcjonalnie).

  >[!IMPORTANT]
  >Weryfikacja podpisu dotyczy tylko skryptów programu PowerShell. 

  > [!WARNING]
  > Zezwolenie na używanie niepodpisanych skryptów może zwiększyć twoją ekspozycję na zagrożenia.

  Uruchamianie niepodpisanych skryptów nie jest zalecane, ponieważ może zwiększyć twoją ekspozycję na zagrożenia. Jeśli jednak musisz ich używać, musisz włączyć to ustawienie na [stronie Ustawienia funkcji zaawansowanych](advanced-features.md) .

- **Upewnij się, że masz odpowiednie uprawnienia**.

  Tylko użytkownicy z odpowiednimi uprawnieniami mogą zainicjować sesję. Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

  > [!IMPORTANT]
  > Opcja przekazania pliku do biblioteki jest dostępna tylko dla użytkowników z uprawnieniem "Zarządzanie zabezpieczeniami Ustawienia".
  > Przycisk jest zaszerowany w przypadku użytkowników z uprawnieniami delegowanymi.

  W zależności od roli, która została Ci nadana, możesz uruchamiać podstawowe lub zaawansowane polecenia odpowiedzi na żywo. Uprawnienia użytkowników są kontrolowane przez niestandardową rolę RBAC.

## <a name="live-response-dashboard-overview"></a>Pulpit nawigacyjny odpowiedzi na żywo — omówienie

Zainicjowanie sesji odpowiedzi na żywo na urządzeniu powoduje otwarcie pulpitu nawigacyjnego. Pulpit nawigacyjny zawiera informacje o sesji, takie jak:

- KtoTo utworzono sesję
- Po rozpoczętej sesji
- Czas trwania sesji

Pulpit nawigacyjny zapewnia również dostęp do:

- Odłączanie sesji
- Upload plików do biblioteki
- Konsola poleceń
- Dziennik poleceń

## <a name="initiate-a-live-response-session-on-a-device"></a>Inicjowanie sesji odpowiedzi na żywo na urządzeniu

1. Zaloguj się do Microsoft 365 Defender konta.

2. Przejdź do **punktu końcowego > Spis** urządzeń i wybierz urządzenie do zbadania. Zostanie otwarta strona urządzenia.

3. Uruchom sesję odpowiedzi na żywo, wybierając pozycję **Zainicjuj sesję odpowiedzi na żywo**. Zostanie wyświetlona konsola poleceń. Poczekaj, aż sesja połączy się z urządzeniem.

4. Za pomocą wbudowanych poleceń można badać jego pracę. Aby uzyskać więcej informacji, zobacz [Polecenia odpowiedzi na żywo](#live-response-commands).

5. Po zakończeniu badania wybierz pozycję **Rozłącz sesję**, a następnie wybierz pozycję **Potwierdź**.

## <a name="live-response-commands"></a>Polecenia odpowiedzi na żywo

W zależności od roli, która została Ci nadana, możesz uruchamiać podstawowe lub zaawansowane polecenia odpowiedzi na żywo. Uprawnienia użytkowników są kontrolowane przez role niestandardowe RBAC. Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

> [!NOTE]
> Odpowiedź na żywo to interakcyjna powłoka oparta na chmurze, w związku z tym konkretne środowisko poleceń może różnić się w czasie odpowiedzi w zależności od jakości sieci i obciążenia systemu między użytkownikiem docelowym a urządzeniem docelowym.

### <a name="basic-commands"></a>Podstawowe polecenia

Następujące polecenia są dostępne dla ról użytkowników, które mają możliwość uruchamiania podstawowych **poleceń** odpowiedzi na żywo. Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

<br>

****
| Polecenie  | Opis  | Windows i Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| cd  | Zmienia bieżący katalog.  | T  | T  | T  |
| cls  | Wyczyści ekran konsoli.  | T  | T  | T  |
| łączenie  | Inicjuje sesję odpowiedzi na żywo na urządzeniu.  | T  | T  | T  |
| połączenia  | Pokazuje wszystkie aktywne połączenia.  | T  | N  | N  |
| dir  | Lista plików i podkategorie w katalogu.  | T  | T  | T  |
| sterowniki  | Pokazuje wszystkie sterowniki zainstalowane na urządzeniu.  | T  | N  | N  |
| fg `<command ID>`  | Umieść określone zadanie na pierwszym planie na pierwszym planie, przygotowawc je jako bieżące zadanie.  UWAGA: fg pobiera identyfikator polecenia dostępny w zadaniach, a nie identyfikator PID  | T  | T  | T  |
| fileinfo  | Uzyskaj informacje o pliku.  | T  | T  | T  |
| findfile  | Znajduje na urządzeniu pliki pod podaną nazwą.  | T  | T  | T  |
| getfile <file_path>  | Pobiera plik.  | T  | T  | T  |
| Pomoc  | Udostępnia informacje pomocy dla poleceń odpowiedzi na żywo.  | T  | T  | T  |
| praca  | Pokazuje obecnie uruchomione zadania, ich identyfikator i stan.  | T  | T  | T  |
| persistence  | Pokazuje wszystkie znane metody utrwalania na urządzeniu.  | T  | N  | N  |
| procesy  | Pokazuje wszystkie procesy uruchomione na urządzeniu.  | T  | T  | T  |
| rejestr  | Wyświetla wartości rejestru.  | T  | N  | N  |
| zadania zaplanowane  | Pokazuje wszystkie zaplanowane zadania na urządzeniu.  | T  | N  | N  |
| usługi  | Pokazuje wszystkie usługi na urządzeniu.  | T  | N  | N  |
| autostartfolders  | Pokazuje wszystkie znane pliki w folderach startowych na urządzeniu.  | T  | N  | N  |
| stan  | Wyświetla stan i dane wyjściowe określonego polecenia.  | T  | N  | N  |
| śledzenie  | Ustawia tryb rejestrowania terminalu w celu debugowania.  | T  | T  | T  |

### <a name="advanced-commands"></a>Polecenia zaawansowane

Następujące polecenia są dostępne dla ról użytkowników, które mają możliwość **uruchamiania zaawansowanych poleceń** odpowiedzi na żywo. Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

<br>

****

| Polecenie  | Opis  | Windows i Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| analizowanie  | Analizowanie jednostki za pomocą różnych aparatów incrimination w celu osiągnięcia werdyktu.  | T  | N  | N  |
| zbieranie  | Zbiera pakiet forensics z komputera  | N  | T  | T  |
| wyizoluj  | Odłącza urządzenie od sieci, zachowując łączność z usługą Defender for Endpoint  | N  | T  | N  |
| wersja  | Zwalnia urządzenie z izolacji sieci  | N  | T  | N  |
| uruchamianie  | Uruchamia skrypt programu PowerShell z biblioteki na urządzeniu.  | T  | T  | T  |
| biblioteka  | Wyświetla listę plików, które zostały przekazane do biblioteki odpowiedzi na żywo.  | T  | T  | T  |
| putfile  | Umieszcza plik z biblioteki na urządzeniu. Pliki są zapisywane w folderze roboczym i są usuwane po domyślnym ponownym uruchomieniu urządzenia.  | T  | T  | T  |
| remediate  | Remediates an entity on the device. Działania naprawcze będą się różnić w zależności od typu encji: Plik: usuń Proces: zatrzymaj, usuń usługę pliku obrazu: stop, delete image file Registry entry: delete Scheduled task: remove Startup folder item: delete file NOTE: This command has a prerequisite command. Możesz użyć polecenia -auto w połączeniu z poleceniem remediate, aby automatycznie uruchomić wstępnie wymagane polecenie.  | T  | T  | T  |
| skanowanie | Uruchamia skanowanie antywirusowe, aby pomóc w zidentyfikowaniu i naprawiniu złośliwego oprogramowania. | N | T | T |
| cofanie  | Przywraca jednostkę, która została rozwiązana.  | T  | T  | T  |


## <a name="use-live-response-commands"></a>Używanie poleceń odpowiedzi na żywo

Polecenia, których można używać w konsoli, są zgodne z podobnymi zasadami, [jak w Windows polecenia](/windows-server/administration/windows-commands/windows-commands#BKMK_c).

Zaawansowane polecenia oferują bardziej zaawansowany zestaw akcji, które pozwalają na bardziej zaawansowane akcje, takie jak pobieranie i przekazywanie pliku, uruchamianie skryptów na urządzeniu i uruchamianie działań naprawczych w encji.

### <a name="get-a-file-from-the-device"></a>Pobierz plik z urządzenia

W scenariuszach, w których chcesz uzyskać plik z urządzenia, które badasz, możesz użyć tego `getfile` polecenia. Umożliwia to zapisanie pliku z urządzenia w celu dalszego badania.

> [!NOTE]
> Obowiązują następujące limity rozmiarów plików:
>
> - `getfile` limit: 3 GB
> - `fileinfo` limit: 30 GB
> - `library` Limit: 250 MB

### <a name="download-a-file-in-the-background"></a>Pobieranie pliku w tle

Aby umożliwić zespołowi ds. bezpieczeństwa kontynuowanie badania urządzenia, na które wpływa to zagrożenie, teraz można pobierać pliki w tle.

- Aby pobrać plik w tle, w konsoli poleceń live response wpisz `download <file_path> &`.
- W przypadku oczekiwania na pobranie pliku możesz przenieść go do tła, naciskając klawisze Ctrl +Z.
- Aby pobrać plik na pierwszy plan, w konsoli poleceń na żywo wpisz `fg <command_id>`.

Oto kilka przykładów:

<br>

****

|Polecenie|Jakie są jego|
|---|---|
|`getfile "C:\windows\some_file.exe" &`|Rozpoczyna się pobieranie pliku o *some_file.exe* w tle.|
|`fg 1234`|Zwraca plik do pobrania z identyfikatorem *polecenia 1234* na pierwszy plan.|
|

### <a name="put-a-file-in-the-library"></a>Umieść plik w bibliotece

Odpowiedź na żywo zawiera bibliotekę, w której można umieszczać pliki. W bibliotece są przechowywane pliki (na przykład skrypty), które można uruchamiać w sesji odpowiedzi na żywo na poziomie dzierżawy.

Funkcja odpowiedzi na żywo umożliwia uruchamianie skryptów programu PowerShell, jednak przed uruchomieniem plików należy je umieścić w bibliotece.

Możesz mieć kolekcję skryptów programu PowerShell, które można uruchamiać na urządzeniach, za pomocą których inicjuje się sesje odpowiedzi na żywo.

#### <a name="to-upload-a-file-in-the-library"></a>Aby przekazać plik w bibliotece

1. Kliknij **Upload plik do biblioteki**.

2. Kliknij **przycisk** Przeglądaj i wybierz plik.

3. Podaj krótki opis.

4. Określ, czy chcesz zastąpić plik o tej samej nazwie.

5. Jeśli chcesz się dowiedzieć, jakie parametry są potrzebne dla skryptu, zaznacz pole wyboru parametry skryptu. W polu tekstowym wprowadź przykład i opis.

6. Kliknij **przycisk Potwierdź**.

7. (Opcjonalnie) Aby sprawdzić, czy plik został przekazany do biblioteki, uruchom to `library` polecenie.

### <a name="cancel-a-command"></a>Anulowanie polecenia

W dowolnym momencie sesji możesz anulować polecenie, naciskając klawisze CTRL+C.

> [!WARNING]
> Użycie tego skrótu nie zatrzyma polecenia po stronie agenta. Polecenie w portalu zostanie anulowane tylko. Dlatego zmiany takie jak "działania naprawcze" mogą być kontynuowane po anulowaniu polecenia.

## <a name="run-a-script"></a>Uruchom skrypt

Przed uruchomieniem skryptu PowerShell/Bash należy najpierw przekazać go do biblioteki.

Po przesłaniu skryptu do biblioteki `run` użyj tego polecenia, aby go uruchomić.

Jeśli planujesz użyć niepodpisanych skryptów programu PowerShell w sesji, musisz włączyć to ustawienie na [stronie Ustawienia funkcji zaawansowanych](advanced-features.md) .

> [!WARNING]
> Zezwolenie na używanie niepodpisanych skryptów może zwiększyć twoją ekspozycję na zagrożenia.

## <a name="apply-command-parameters"></a>Stosowanie parametrów polecenia

- Wyświetl pomoc konsoli, aby dowiedzieć się więcej o parametrach poleceń. Aby uzyskać informacje na temat pojedynczego polecenia, uruchom polecenie:

  ```powershell
  help <command name>
  ```

- Podczas stosowania parametrów do poleceń należy pamiętać, że parametry są obsługiwane w ustalonej kolejności:

  ```powershell
  <command name> param1 param2
  ```

- Podczas określania parametrów poza stałą kolejnością określ nazwę parametru za pomocą łącznika przed podaniem wartości:

  ```powershell
  <command name> -param2_name param2
  ```

- W przypadku korzystania z poleceń, które mają wstępnie wymagane polecenia, można używać flag:

  ```powershell
  <command name> -type file -id <file path> - auto
  ```

  lub

  ```powershell
  remediate file <file path> - auto`
  ```

## <a name="supported-output-types"></a>Obsługiwane typy danych wyjściowych

Odpowiedzi na żywo obsługują typy danych wyjściowych w formacie tabeli i formatu JSON. Dla każdego polecenia istnieje domyślne zachowanie wyjściowe. Możesz zmodyfikować dane wyjściowe w preferowanym formacie wyjściowym, korzystając z następujących poleceń:

- `-output json`
- `-output table`

> [!NOTE]
> Ze względu na ograniczoną ilość miejsca w tabeli jest wyświetlanych mniej pól. Aby wyświetlić więcej szczegółów w wynikach, możesz użyć polecenia wyjściowego JSON, aby wyświetlić więcej szczegółów.

## <a name="supported-output-pipes"></a>Potoki wyjściowe obsługiwane

Funkcja odpowiedzi na żywo obsługuje rure wyjściowe do pliku i interfejsu wideo. Interfejsu wideo jest domyślnym zachowaniem wyjściowym. Dane wyjściowe można dodać potokami do pliku, używając następującego polecenia: [command] > [nazwa_pliku].txt.

Przykład:

```console
processes > output.txt
```

## <a name="view-the-command-log"></a>Wyświetlanie dziennika poleceń

Wybierz **kartę Dziennik poleceń** , aby wyświetlić polecenia używane na urządzeniu w trakcie sesji. Każde polecenie jest śledzone ze pełnymi szczegółami, takimi jak:

- ID
- Wiersz polecenia
- Czas trwania
- Pasek boczny stanu i danych wejściowych lub wyjściowych

## <a name="limitations"></a>Ograniczenia

- Sesje odpowiedzi na żywo są ograniczone do 25 sesji odpowiedzi na żywo jednocześnie.
- Nieaktywny limit czasu sesji na żywo wynosi 30 minut.
- Poszczególne polecenia odpowiedzi na żywo mają limit czasu 10 minut, `getfile`z wyjątkiem , `findfile`i `run`, które mają limit 30 minut.
- Użytkownik może zainicjować do 10 jednoczesnych sesji.
- Urządzenie może być w jednej sesji na raz.
- Obowiązują następujące limity rozmiarów plików:
  - `getfile` limit: 3 GB
  - `fileinfo` limit: 10 GB
  - `library` Limit: 250 MB

## <a name="related-article"></a>Artykuł pokrewny

- [Przykłady poleceń odpowiedzi na żywo](live-response-command-examples.md)
