---
title: Badanie jednostek na urządzeniach przy użyciu odpowiedzi na żywo w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Uzyskiwanie dostępu do urządzenia przy użyciu bezpiecznego zdalnego połączenia powłoki w celu wykonywania zadań dochodzeniowych i wykonywania natychmiastowych działań reagowania na urządzeniu w czasie rzeczywistym.
keywords: remote, shell, connection, live, response, real-time, command, script, remediate, hunt, export, log, drop, download, file,
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
ms.openlocfilehash: 1f387696797d52805495777be0850ebe135fd38a
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173116"
---
# <a name="investigate-entities-on-devices-using-live-response"></a>Badanie jednostek na urządzeniach przy użyciu odpowiedzi na żywo

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Reagowanie na żywo zapewnia zespołom operacji zabezpieczeń natychmiastowy dostęp do urządzenia (nazywanego również maszyną) przy użyciu zdalnego połączenia powłoki. Daje to możliwość wykonywania szczegółowych działań dochodzeniowych i podejmowania natychmiastowych działań reagowania w celu szybkiego powstrzymania zidentyfikowanych zagrożeń w czasie rzeczywistym.

Reagowanie na żywo ma na celu usprawnienie badań dzięki umożliwieniu zespołowi ds. operacji zabezpieczeń zbierania danych kryminalistycznych, uruchamiania skryptów, wysyłania podejrzanych jednostek do analizy, korygowania zagrożeń i proaktywnego wyszukiwania pojawiających się zagrożeń.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUW]

Dzięki odpowiedzi na żywo analitycy mogą wykonywać wszystkie następujące zadania:

- Uruchom podstawowe i zaawansowane polecenia, aby wykonać czynności śledcze na urządzeniu.
- Pobierz pliki, takie jak przykłady złośliwego oprogramowania i wyniki skryptów programu PowerShell.
- Pobierz pliki w tle (nowe!).
- Upload skrypt programu PowerShell lub plik wykonywalny do biblioteki i uruchom go na urządzeniu z poziomu dzierżawy.
- Wykonaj lub cofnij akcje korygowania.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed zainicjowaniem sesji na urządzeniu upewnij się, że spełniasz następujące wymagania:

- **Sprawdź, czy używasz obsługiwanej wersji Windows**.

  Na urządzeniach musi działać jedna z następujących wersji Windows

  - **Windows 10 & 11**
    - [Wersja 1909 lub nowsza](/windows/whats-new/whats-new-windows-10-version-1909)
    - [Wersja 1903](/windows/whats-new/whats-new-windows-10-version-1903) z [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Wersja 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) [z kb4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Wersja 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803) z [kb4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Wersja 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709) z [kb4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **macOS** — dotyczy tylko publicznej wersji zapoznawczej, minimalnej wymaganej wersji: 101.43.84

   > [!NOTE]
   > Obecnie obsługiwane są tylko systemy macOS oparte na technologii Intel.

  - **Linux** — dotyczy tylko publicznej wersji zapoznawczej, minimalna wymagana wersja: 101.45.13

  - **Windows Server 2012 R2** — z [kb5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2016** — z [kb5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2019**
    - Wersja 1903 lub (z [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)) później
    - Wersja 1809 (z [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))

  - **Windows Server 2022**

- **Włącz odpowiedź na żywo na stronie ustawień zaawansowanych**.

  Musisz włączyć funkcję odpowiedzi na żywo na stronie [Ustawienia funkcji zaawansowanych](advanced-features.md) .

  > [!NOTE]
  > Te ustawienia mogą edytować tylko użytkownicy z rolami zarządzania zabezpieczeniami lub administratorami globalnymi.
  >
  > Przed włączeniem odpowiedzi na żywo należy włączyć automatyczne badanie w [ustawieniach funkcji zaawansowanych](advanced-features.md) .

- **Włącz odpowiedź na żywo dla serwerów na stronie ustawień zaawansowanych** (zalecane).

  > [!NOTE]
  > Te ustawienia mogą edytować tylko użytkownicy z rolami zarządzania zabezpieczeniami lub administratorami globalnymi.

- **Upewnij się, że urządzenie ma przypisany poziom korygowania usługi Automation**.

  Musisz włączyć co najmniej minimalny poziom korygowania dla danej grupy urządzeń. W przeciwnym razie nie będzie można ustanowić sesji odpowiedzi na żywo dla członka tej grupy.

  Zostanie wyświetlony następujący błąd:

  :::image type="content" source="images/live-response-error.png" alt-text="Komunikat o błędzie" lightbox="images/live-response-error.png":::

- **Włącz wykonywanie skryptu bez znaku odpowiedzi na żywo** (opcjonalnie).

  >[!IMPORTANT]
  >Weryfikacja podpisu dotyczy tylko skryptów programu PowerShell.

  > [!WARNING]
  > Zezwolenie na używanie niepodpisanych skryptów może zwiększyć narażenie na zagrożenia.

  Uruchamianie niepodpisanych skryptów nie jest zalecane, ponieważ może zwiększyć narażenie na zagrożenia. Jeśli jednak musisz ich używać, musisz włączyć to ustawienie na stronie [Ustawienia funkcji zaawansowanych](advanced-features.md) .

- **Upewnij się, że masz odpowiednie uprawnienia**.

  Sesję mogą zainicjować tylko użytkownicy, którzy zostali aprowizowane z odpowiednimi uprawnieniami. Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

  > [!IMPORTANT]
  > Opcja przekazania pliku do biblioteki jest dostępna tylko dla użytkowników z uprawnieniem "Zarządzanie Ustawienia zabezpieczeń".
  > Przycisk jest wyszarzony dla użytkowników z uprawnieniami delegowanymi.

  W zależności od roli, która została Ci przyznana, można uruchamiać podstawowe lub zaawansowane polecenia odpowiedzi na żywo. Uprawnienia użytkowników są kontrolowane przez rolę niestandardową RBAC.

## <a name="live-response-dashboard-overview"></a>Omówienie pulpitu nawigacyjnego odpowiedzi na żywo

Po zainicjowaniu sesji odpowiedzi na żywo na urządzeniu zostanie otwarty pulpit nawigacyjny. Pulpit nawigacyjny zawiera informacje o sesji, takie jak:

- KtoTo utworzono sesję
- Po rozpoczęciu sesji
- Czas trwania sesji

Pulpit nawigacyjny zapewnia również dostęp do następujących elementów:

- Rozłącz sesję
- Upload pliki do biblioteki
- Konsola poleceń
- Dziennik poleceń

## <a name="initiate-a-live-response-session-on-a-device"></a>Inicjowanie sesji odpowiedzi na żywo na urządzeniu

1. Zaloguj się do portalu Microsoft 365 Defender.

2. Przejdź do **obszaru Punkty końcowe > Spis urządzeń** i wybierz urządzenie do zbadania. Zostanie otwarta strona urządzenia.

3. Uruchom sesję odpowiedzi na żywo, wybierając pozycję **Inicjuj sesję odpowiedzi na żywo**. Zostanie wyświetlona konsola poleceń. Poczekaj, aż sesja nawiąże połączenie z urządzeniem.

4. Użyj wbudowanych poleceń, aby wykonać czynności śledcze. Aby uzyskać więcej informacji, zobacz [Polecenia odpowiedzi na żywo](#live-response-commands).

5. Po zakończeniu badania wybierz pozycję **Rozłącz sesję**, a następnie wybierz pozycję **Potwierdź**.

## <a name="live-response-commands"></a>Polecenia odpowiedzi na żywo

W zależności od roli, która została Ci przyznana, można uruchamiać podstawowe lub zaawansowane polecenia odpowiedzi na żywo. Uprawnienia użytkownika są kontrolowane przez role niestandardowe RBAC. Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

> [!NOTE]
> Odpowiedź na żywo to interaktywna powłoka oparta na chmurze, w związku z tym określone środowisko poleceń może się różnić w czasie odpowiedzi w zależności od jakości sieci i obciążenia systemu między użytkownikiem końcowym a urządzeniem docelowym.

### <a name="basic-commands"></a>Podstawowe polecenia

Następujące polecenia są dostępne dla ról użytkowników, którym przyznano możliwość uruchamiania **podstawowych** poleceń odpowiedzi na żywo. Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

| Polecenia  | Opis  | Windows i serwer Windows  | macOS  | Linux  |
|---|---|---|---|---|
| Cd  | Zmienia bieżący katalog.  | T  | T  | T  |
| Cls  | Czyści ekran konsoli.  | T  | T  | T  |
| Połączyć  | Inicjuje sesję odpowiedzi na żywo na urządzeniu.  | T  | T  | T  |
| Połączenia  | Pokazuje wszystkie aktywne połączenia.  | T  | N  | N  |
| Dir  | Pokazuje listę plików i podkatalogów w katalogu.  | T  | T  | T  |
| Sterowniki  | Pokazuje wszystkie sterowniki zainstalowane na urządzeniu.  | T  | N  | N  |
| Fg `<command ID>`  | Umieść określone zadanie na pierwszym planie, co czyni go bieżącym zadaniem.  UWAGA: usługa fg pobiera identyfikator polecenia dostępny z zadań, a nie z identyfikatora PID  | T  | T  | T  |
| Fileinfo  | Uzyskaj informacje o pliku.  | T  | T  | T  |
| Findfile  | Lokalizuje pliki według danej nazwy na urządzeniu.  | T  | T  | T  |
| getfile <file_path>  | Pobiera plik.  | T  | T  | T  |
| Pomoc  | Zawiera informacje o pomocy dotyczące poleceń odpowiedzi na żywo.  | T  | T  | T  |
| Zadania  | Pokazuje aktualnie uruchomione zadania, ich identyfikator i stan.  | T  | T  | T  |
| Trwałości  | Pokazuje wszystkie znane metody trwałości na urządzeniu.  | T  | N  | N  |
| Procesów  | Pokazuje wszystkie procesy uruchomione na urządzeniu.  | T  | T  | T  |
| Rejestrze  | Pokazuje wartości rejestru.  | T  | N  | N  |
| scheduledtasks  | Pokazuje wszystkie zaplanowane zadania na urządzeniu.  | T  | N  | N  |
| Usług  | Pokazuje wszystkie usługi na urządzeniu.  | T  | N  | N  |
| startupfolders  | Pokazuje wszystkie znane pliki w folderach startowych na urządzeniu.  | T  | N  | N  |
| Stan  | Pokazuje stan i dane wyjściowe określonego polecenia.  | T  | N  | N  |
| Śledzenia  | Ustawia tryb rejestrowania terminalu na debugowanie.  | T  | T  | T  |

### <a name="advanced-commands"></a>Polecenia zaawansowane

Następujące polecenia są dostępne dla ról użytkownika, którym przyznano możliwość uruchamiania **zaawansowanych** poleceń odpowiedzi na żywo. Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

| Polecenia  | Opis  | Windows i serwer Windows  | macOS  | Linux  |
|---|---|---|---|---|
| Analizować  | Analizuje jednostkę za pomocą różnych aparatów oskarżenia, aby osiągnąć werdykt.  | T  | N  | N  |
| Zbierać  | Zbiera pakiet kryminalistyki z maszyny  | N  | T  | T  |
| Wyizolować  | Odłącza urządzenie od sieci przy zachowaniu łączności z usługą Defender for Endpoint  | N  | T  | N  |
| Wydania  | Zwalnia urządzenie z izolacji sieci  | N  | T  | N  |
| Uruchomić  | Uruchamia skrypt programu PowerShell z biblioteki na urządzeniu.  | T  | T  | T  |
| Biblioteki  | Wyświetla listę plików przekazanych do biblioteki odpowiedzi na żywo.  | T  | T  | T  |
| putfile  | Umieszcza plik z biblioteki na urządzeniu. Pliki są zapisywane w folderze roboczym i są usuwane po domyślnym ponownym uruchomieniu urządzenia.  | T  | T  | T  |
| Koryguj  | Koryguje jednostkę na urządzeniu. Akcja korygowania będzie się różnić w zależności od typu jednostki: Plik: usuń Proces: zatrzymaj, usuń plik obrazu Usługa: zatrzymaj, usuń wpis rejestru pliku obrazu: usuń zaplanowane zadanie: usuń element folderu uruchamiania: usuń plik UWAGA: To polecenie ma polecenie wymagań wstępnych. Możesz użyć polecenia -auto w połączeniu z korygowaniem, aby automatycznie uruchomić polecenie wymagań wstępnych.  | T  | T  | T  |
| Skanowania | Uruchamia skanowanie antywirusowe, aby ułatwić identyfikowanie i korygowanie złośliwego oprogramowania. | N | T | T |
| Cofnij  | Przywraca jednostkę, która została skorygowana.  | T  | T  | T  |

## <a name="use-live-response-commands"></a>Używanie poleceń odpowiedzi na żywo

Polecenia, których można użyć w konsoli programu, są zgodne z podobnymi zasadami jak [polecenia Windows](/windows-server/administration/windows-commands/windows-commands#BKMK_c).

Zaawansowane polecenia oferują bardziej niezawodny zestaw akcji, które umożliwiają wykonywanie bardziej zaawansowanych akcji, takich jak pobieranie i przekazywanie pliku, uruchamianie skryptów na urządzeniu i wykonywanie akcji korygowania jednostki.

### <a name="get-a-file-from-the-device"></a>Pobieranie pliku z urządzenia

W przypadku scenariuszy, w których chcesz pobrać plik z badanego urządzenia, możesz użyć `getfile` polecenia . Dzięki temu można zapisać plik z urządzenia w celu dalszego zbadania.

> [!NOTE]
> Obowiązują następujące limity rozmiaru plików:
>
> - `getfile` limit: 3 GB
> - `fileinfo` limit: 30 GB
> - `library` limit: 250 MB

### <a name="download-a-file-in-the-background"></a>Pobieranie pliku w tle

Aby umożliwić zespołowi ds. operacji zabezpieczeń kontynuowanie badania urządzenia, na które ma to wpływ, pliki można teraz pobrać w tle.

- Aby pobrać plik w tle, w konsoli poleceń odpowiedzi na żywo wpisz `download <file_path> &`.
- Jeśli czekasz na pobranie pliku, możesz przenieść go do tła przy użyciu klawiszy Ctrl + Z.
- Aby przenieść plik do pobrania na pierwszy plan, w konsoli poleceń odpowiedzi na żywo wpisz `fg <command_id>`.

Oto kilka przykładów:

<br>

****

|Polecenia|Co robi|
|---|---|
|`getfile "C:\windows\some_file.exe" &`|Rozpoczyna pobieranie pliku o nazwie *some_file.exe* w tle.|
|`fg 1234`|Zwraca pobranie z identyfikatorem polecenia *1234* na pierwszy plan.|
|

### <a name="put-a-file-in-the-library"></a>Umieszczanie pliku w bibliotece

Odpowiedź na żywo zawiera bibliotekę, w której można umieszczać pliki. Biblioteka przechowuje pliki (takie jak skrypty), które można uruchomić w sesji odpowiedzi na żywo na poziomie dzierżawy.

Odpowiedź na żywo umożliwia uruchamianie skryptów programu PowerShell, jednak przed ich uruchomieniem należy najpierw umieścić pliki w bibliotece.

Możesz mieć kolekcję skryptów programu PowerShell, które mogą być uruchamiane na urządzeniach, za pomocą których inicjujesz sesje odpowiedzi na żywo.

#### <a name="to-upload-a-file-in-the-library"></a>Aby przekazać plik w bibliotece

1. Kliknij **Upload plik do biblioteki**.

2. Kliknij przycisk **Przeglądaj** i wybierz plik.

3. Podaj krótki opis.

4. Określ, czy chcesz zastąpić plik o tej samej nazwie.

5. Jeśli chcesz być, dowiedz się, jakie parametry są potrzebne dla skryptu, zaznacz pole wyboru Parametry skryptu. W polu tekstowym wprowadź przykład i opis.

6. Kliknij **przycisk Potwierdź**.

7. (Opcjonalnie) Aby sprawdzić, czy plik został przekazany do biblioteki, uruchom `library` polecenie .

### <a name="cancel-a-command"></a>Anulowanie polecenia

W dowolnym momencie sesji możesz anulować polecenie, naciskając klawisze CTRL + C.

> [!WARNING]
> Użycie tego skrótu nie spowoduje zatrzymania polecenia po stronie agenta. Spowoduje to anulowanie tylko polecenia w portalu. Dlatego zmiana operacji, takich jak "korygowanie", może być kontynuowana, gdy polecenie zostanie anulowane.

## <a name="run-a-script"></a>Uruchom skrypt

Przed uruchomieniem skryptu programu PowerShell/powłoki Bash należy najpierw przekazać go do biblioteki.

Po przekazaniu skryptu do biblioteki użyj `run` polecenia , aby uruchomić skrypt.

Jeśli planujesz używać niepodpisanego skryptu programu PowerShell w sesji, musisz włączyć to ustawienie na stronie [Ustawienia funkcji zaawansowanych](advanced-features.md) .

> [!WARNING]
> Zezwolenie na używanie niepodpisanych skryptów może zwiększyć narażenie na zagrożenia.

## <a name="apply-command-parameters"></a>Stosowanie parametrów polecenia

- Wyświetl pomoc dotyczącą konsoli, aby dowiedzieć się więcej o parametrach polecenia. Aby dowiedzieć się więcej o pojedynczym poleceniu, uruchom polecenie:

  ```powershell
  help <command name>
  ```

- Podczas stosowania parametrów do poleceń należy pamiętać, że parametry są obsługiwane w oparciu o stałą kolejność:

  ```powershell
  <command name> param1 param2
  ```

- Podczas określania parametrów poza stałą kolejnością określ nazwę parametru za pomocą łącznika przed podaniem wartości:

  ```powershell
  <command name> -param2_name param2
  ```

- W przypadku korzystania z poleceń, które mają polecenia wymagań wstępnych, można użyć flag:

  ```powershell
  <command name> -type file -id <file path> - auto
  ```

  lub

  ```powershell
  remediate file <file path> - auto`
  ```

## <a name="supported-output-types"></a>Obsługiwane typy danych wyjściowych

Odpowiedź na żywo obsługuje typy danych wyjściowych w formacie tabeli i JSON. Dla każdego polecenia istnieje domyślne zachowanie danych wyjściowych. Dane wyjściowe można modyfikować w preferowanym formacie danych wyjściowych przy użyciu następujących poleceń:

- `-output json`
- `-output table`

> [!NOTE]
> Mniej pól jest wyświetlanych w formacie tabeli ze względu na ograniczoną ilość miejsca. Aby wyświetlić więcej szczegółów w danych wyjściowych, możesz użyć polecenia danych wyjściowych JSON, aby wyświetlić więcej szczegółów.

## <a name="supported-output-pipes"></a>Obsługiwane potoki wyjściowe

Odpowiedź na żywo obsługuje potoki wyjściowe do interfejsu wiersza polecenia i pliku. Domyślnym zachowaniem danych wyjściowych jest interfejs wiersza polecenia. Dane wyjściowe można przekazać do pliku za pomocą następującego polecenia: [command] > [nazwa_pliku].txt.

Przykład:

```console
processes > output.txt
```

## <a name="view-the-command-log"></a>Wyświetlanie dziennika poleceń

Wybierz kartę **Dziennik poleceń** , aby wyświetlić polecenia używane na urządzeniu podczas sesji. Każde polecenie jest śledzone z pełnymi szczegółami, takimi jak:

- ID
- Wiersz polecenia
- Długość
- Pasek boczny stanu i danych wejściowych lub wyjściowych

## <a name="limitations"></a>Ograniczenia

- Sesje odpowiedzi na żywo są ograniczone do 25 sesji odpowiedzi na żywo jednocześnie.
- Wartość limitu czasu nieaktywnej sesji odpowiedzi na żywo wynosi 30 minut.
- Poszczególne polecenia odpowiedzi na żywo mają limit czasu wynoszący 10 minut, z wyjątkiem `getfile`, `findfile`i `run`, które mają limit 30 minut.
- Użytkownik może zainicjować maksymalnie 10 współbieżnych sesji.
- Urządzenie może być jednocześnie tylko w jednej sesji.
- Obowiązują następujące limity rozmiaru plików:
  - `getfile` limit: 3 GB
  - `fileinfo` limit: 30 GB
  - `library` limit: 250 MB

## <a name="related-article"></a>Powiązany artykuł

- [Przykłady poleceń reagowania w czasie rzeczywistym](live-response-command-examples.md)
