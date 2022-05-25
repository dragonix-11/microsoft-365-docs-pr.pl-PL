---
title: Wykonaj akcje odpowiedzi dla pliku w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Wykonaj akcje reagowania na alerty związane z plikami, zatrzymując i kłócąc plik lub blokując plik i sprawdzając szczegóły działania.
keywords: odpowiadanie, zatrzymywanie i kwarantanna, blok plik, głęboka analiza
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
ms.openlocfilehash: a70602f9b482196ee949a8f9922f2979b04b3ff4
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669303"
---
# <a name="take-response-actions-on-a-file"></a>Wykonaj akcje odpowiedzi na pliku

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-responddile-abovefoldlink)

Szybkie reagowanie na wykryte ataki przez zatrzymywanie i kwazarowanie plików lub blokowanie pliku. Po wykonaniu akcji na plikach możesz sprawdzić szczegóły działania w Centrum akcji.

Akcje odpowiedzi są dostępne na szczegółowej stronie profilu pliku. Po przejściu na tę stronę możesz przełączać się między nowymi i starymi układami stron, przełączając **nową stronę Plik**. W pozostałej części tego artykułu opisano nowszy układ strony.

Akcje odpowiedzi są uruchamiane w górnej części strony pliku i obejmują:

- Plik zatrzymania i kwarantanny
- Dodaj wskaźnik
- Pobieranie pliku
- Konsultuj się z ekspertem ds. zagrożeń
- Centrum akcji

Możesz również przesłać pliki do głębokiej analizy, aby uruchomić plik w bezpiecznej piaskownicy w chmurze. Po zakończeniu analizy otrzymasz szczegółowy raport zawierający informacje o zachowaniu pliku. Możesz przesyłać pliki do głębokiej analizy i odczytywać wcześniejsze raporty, wybierając kartę **Analiza szczegółowa** . Znajduje się poniżej kart informacji o pliku.

Niektóre akcje wymagają pewnych uprawnień. W poniższej tabeli opisano akcję, jaką niektóre uprawnienia mogą wykonać w przypadku przenośnych plików wykonywalnych (PE) i innych niż PE:

|Uprawnienia|Pliki PE|Pliki inne niż PE|
|---|:---:|:---:|
|Wyświetlanie danych|X|X|
|Badanie alertów|&#x2611;|X|
|Podstawowa odpowiedź na żywo|X|X|
|Zaawansowana odpowiedź na żywo|&#x2611;|&#x2611;|

Aby uzyskać więcej informacji na temat ról, zobacz [Tworzenie ról i zarządzanie nimi na potrzeby kontroli dostępu opartej na rolach](user-roles.md).

## <a name="stop-and-quarantine-files-in-your-network"></a>Zatrzymaj i poddaj kwarantannie pliki w sieci

Możesz powstrzymać atak w organizacji, zatrzymując złośliwy proces i kłócąc plik, w którym był obserwowany.

> [!IMPORTANT]
> Tę akcję można wykonać tylko wtedy, gdy:
>
> - Na urządzeniu, na którym jest wykonywana akcja, działa Windows 10, wersja 1703 lub nowsza oraz Windows 11
> - Plik nie należy do zaufanych wydawców innych firm lub nie jest podpisany przez firmę Microsoft
> - Program antywirusowy Microsoft Defender musi co najmniej działać w trybie pasywnym. Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender zgodność](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

Akcja **Zatrzymywanie i kwarantanna pliku** obejmuje zatrzymywanie uruchomionych procesów, quarantining plików i usuwanie trwałych danych, takich jak klucze rejestru.

Ta akcja ma wpływ na urządzenia z Windows 10 w wersji 1703 lub nowszej i Windows 11, gdzie plik był obserwowany w ciągu ostatnich 30 dni.

> [!NOTE]
> W dowolnym momencie będzie można przywrócić plik z kwarantanny.

### <a name="stop-and-quarantine-files"></a>Zatrzymywanie i kwarantanna plików

1. Wybierz plik, który chcesz zatrzymać i poddać kwarantannie. Możesz wybrać plik z dowolnego z następujących widoków lub użyć pola Wyszukiwania:

   - **Alerty** — kliknij odpowiednie linki z opisu lub szczegółów na osi czasu scenariusza alertu
   - **Pole wyszukiwania** — wybierz pozycję **Plik** z menu rozwijanego i wprowadź nazwę pliku

   > [!NOTE]
   > Akcja pliku zatrzymania i kwarantanny jest ograniczona do maksymalnie 1000 urządzeń. Aby zatrzymać plik na większej liczbie urządzeń, zobacz [Dodawanie wskaźnika w celu zablokowania lub zezwolenia na plik](#add-indicator-to-block-or-allow-a-file).

2. Przejdź do górnego paska i wybierz pozycję **Zatrzymaj i Kwarantanna**.

   :::image type="content" source="images/atp-stop-quarantine-file.png" alt-text="Akcja pliku zatrzymania i kwarantanny" lightbox="images/atp-stop-quarantine-file.png":::

3. Określ przyczynę, a następnie wybierz pozycję **Potwierdź**.

   :::image type="content" source="images/atp-stop-quarantine.png" alt-text="Strona pliku zatrzymania i kwarantanny" lightbox="images/atp-stop-quarantine.png":::

   Centrum akcji pokazuje informacje o przesłaniu:

   :::image type="content" source="images/atp-stopnquarantine-file.png" alt-text="Centrum akcji pliku zatrzymania i kwarantanny" lightbox="images/atp-stopnquarantine-file.png":::

   - **Czas przesyłania** — pokazuje, kiedy akcja została przesłana.
   - **Powodzenie** — pokazuje liczbę urządzeń, na których plik został zatrzymany i poddany kwarantannie.
   - **Niepowodzenie** — pokazuje liczbę urządzeń, na których akcja nie powiodła się, oraz szczegóły dotyczące błędu.
   - **Oczekujące** — pokazuje liczbę urządzeń, z których plik nie został jeszcze zatrzymany i poddany kwarantannie. Może to zająć trochę czasu w przypadku, gdy urządzenie jest w trybie offline lub nie jest połączone z siecią.

4. Wybierz dowolny ze wskaźników stanu, aby wyświetlić więcej informacji o akcji. Na przykład wybierz pozycję **Nie można** zobaczyć, gdzie akcja nie powiodła się.

#### <a name="notification-on-device-userf"></a>Powiadomienie na urządzeniu userf

Po usunięciu pliku z urządzenia zostanie wyświetlone następujące powiadomienie:

:::image type="content" source="images/atp-notification-file.png" alt-text="Powiadomienie użytkownika urządzenia" lightbox="images/atp-notification-file.png":::

Na osi czasu urządzenia jest dodawane nowe zdarzenie dla każdego urządzenia, na którym plik został zatrzymany i poddany kwarantannie.

Ostrzeżenie jest wyświetlane przed zaimplementowaniem akcji dla plików powszechnie używanych w całej organizacji. Ma to na celu sprawdzenie, czy operacja jest zamierzona.

## <a name="restore-file-from-quarantine"></a>Przywróć plik z kwarantanny

Możesz wycofać i usunąć plik z kwarantanny, jeśli ustalono, że jest on czysty po badaniu. Uruchom następujące polecenie na każdym urządzeniu, na którym plik został poddany kwarantannie.

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu:

   1. Przejdź do **pozycji Start** i wpisz _cmd_.

   1. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij **klawisz Enter**:

   ```dos
   "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
   ```

   > [!NOTE]
   > W niektórych scenariuszach **nazwa zagrożenia** może wyglądać następująco: EUS:Win32/CustomEnterpriseBlock!cl.
   >
   > Usługa Defender for Endpoint przywróci wszystkie niestandardowe zablokowane pliki, które zostały poddane kwarantannie na tym urządzeniu w ciągu ostatnich 30 dni.

> [!IMPORTANT]
> Plik, który został poddany kwarantannie jako potencjalne zagrożenie sieciowe, może nie być możliwy do odzyskania. Jeśli użytkownik spróbuje przywrócić plik po kwarantannie, ten plik może być niedostępny. Może to być spowodowane tym, że system nie ma już poświadczeń sieciowych umożliwiających dostęp do pliku. Zazwyczaj jest to wynikiem tymczasowego logowania do systemu lub folderu udostępnionego, a tokeny dostępu wygasły.

## <a name="download-or-collect-file"></a>Pobierz lub zbierz plik

Wybranie pozycji **Pobierz plik** z akcji odpowiedzi umożliwia pobranie lokalnego archiwum .zip chronionego hasłem zawierającego plik. Zostanie wyświetlone okno wysuwane, w którym można zarejestrować przyczynę pobrania pliku i ustawić hasło.

Domyślnie powinno być możliwe pobieranie plików znajdujących się w kwarantannie.

:::image type="content" source="images/atp-download-file-action.png" alt-text="Akcja pobierania pliku" lightbox="images/atp-download-file-action.png":::

### <a name="download-quarantined-files"></a>Pobieranie plików poddanych kwarantannie

Pliki poddane kwarantannie przez Program antywirusowy Microsoft Defender lub twój zespół ds. zabezpieczeń zostaną zapisane w zgodny sposób zgodnie z [konfiguracjami przykładowego przesyłania](enable-cloud-protection-microsoft-defender-antivirus.md). Twój zespół ds. zabezpieczeń może pobrać pliki bezpośrednio ze strony szczegółów pliku za pośrednictwem przycisku "Pobierz plik". **Ta funkcja jest domyślnie włączona**.

Lokalizacja zależy od ustawień geograficznych organizacji (UE, Wielka Brytania lub USA). Plik poddany kwarantannie będzie zbierany tylko raz dla organizacji. Dowiedz się więcej o ochronie danych firmy Microsoft w portalu zaufania usługi pod adresem https://aka.ms/STP.

Włączenie tego ustawienia może pomóc zespołom ds. zabezpieczeń zbadać potencjalnie złe pliki i szybko i w mniej ryzykowny sposób zbadać zdarzenia. Jeśli jednak chcesz wyłączyć to ustawienie, przejdź do **Ustawienia** \> **Funkcje** \> zaawansowane **punktów końcowych** \> **Pobierz pliki poddane kwarantannie**, aby dostosować ustawienie. [Dowiedz się więcej o zaawansowanych funkcjach](advanced-features.md)

#### <a name="backing-up-quarantined-files"></a>Tworzenie kopii zapasowych plików poddanych kwarantannie

Użytkownicy mogą zostać poproszeni o wyrażenie jawnej zgody przed utworzeniem kopii zapasowej pliku poddanego kwarantannie, w zależności od [konfiguracji przykładowego przesyłania](enable-cloud-protection-microsoft-defender-antivirus.md#use-group-policy-to-turn-on-cloud-protection).

Ta funkcja nie będzie działać, jeśli przesyłanie przykładowe jest wyłączone. Jeśli automatyczne przesyłanie przykładów jest ustawione na żądanie uprawnień od użytkownika, będą zbierane tylko przykłady, które użytkownik zgadza się wysłać.

> [!IMPORTANT]
> Pobieranie wymagań dotyczących plików poddanych kwarantannie:
>
> - Twoja organizacja używa Program antywirusowy Microsoft Defender w trybie aktywnym
> - Wersja aparatu antywirusowego to 1.1.17300.4 lub nowszy. Zobacz [Miesięczne wersje platformy i aparatu](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)
> - Włączono ochronę opartą na chmurze. Zobacz [Włączanie ochrony dostarczanej w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)
> - Przesyłanie przykładu jest włączone
> - Urządzenia mają Windows 10 wersję 1703 lub nowszą albo serwer Windows 2016 lub 2019 lub Windows Server 2022 lub Windows 11

### <a name="collect-files"></a>Zbieranie plików

Jeśli plik nie jest jeszcze przechowywany przez Ochrona punktu końcowego w usłudze Microsoft Defender, nie możesz go pobrać. Zamiast tego w tej samej lokalizacji zostanie wyświetlony przycisk **Zbierz plik** . Jeśli plik nie był widoczny w organizacji w ciągu ostatnich 30 dni, **plik Collect** zostanie wyłączony.
> [!Important]
> Plik, który został poddany kwarantannie jako potencjalne zagrożenie sieciowe, może nie być możliwy do odzyskania. Jeśli użytkownik spróbuje przywrócić plik po kwarantannie, ten plik może być niedostępny. Może to być spowodowane tym, że system nie ma już poświadczeń sieciowych umożliwiających dostęp do pliku. Zazwyczaj jest to wynikiem tymczasowego logowania do systemu lub folderu udostępnionego, a tokeny dostępu wygasły.

## <a name="add-indicator-to-block-or-allow-a-file"></a>Dodawanie wskaźnika w celu zablokowania lub zezwolenia na plik

Zapobiegaj dalszej propagacji ataku w organizacji, zakazując potencjalnie złośliwych plików lub podejrzewanego złośliwego oprogramowania. Jeśli znasz potencjalnie złośliwy przenośny plik wykonywalny (PE), możesz go zablokować. Ta operacja uniemożliwi jej odczytywanie, zapisywanie lub wykonywanie na urządzeniach w organizacji.

> [!IMPORTANT]
>
> - Ta funkcja jest dostępna, jeśli organizacja korzysta z Program antywirusowy Microsoft Defender i włączono ochronę dostarczaną przez chmurę. Aby uzyskać więcej informacji, zobacz [Zarządzanie ochroną dostarczaną przez chmurę](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
>
> - Wersja klienta ochrony przed złośliwym kodem musi mieć wersję 4.18.1901.x lub nowszą.
> - Ta funkcja ma na celu zapobieganie pobieraniu z Sieci Web podejrzanego złośliwego oprogramowania (lub potencjalnie złośliwych plików). Obecnie obsługuje przenośne pliki wykonywalne (PE), w tym _pliki.exe_ i _.dll_ . Pokrycie zostanie przedłużone w czasie.
> - Ta akcja odpowiedzi jest dostępna dla urządzeń w Windows 10, wersji 1703 lub nowszej i Windows 11.
> - Nie można wykonać funkcji zezwalania lub blokowania dla plików, jeśli klasyfikacja pliku istnieje w pamięci podręcznej urządzenia przed akcją zezwalania lub blokowania.

> [!NOTE]
> Aby można było wykonać tę akcję, plik PE musi znajdować się na osi czasu urządzenia.
>
> Może wystąpić kilka minut opóźnienia między wykonaniem akcji a zablokowaniem rzeczywistego pliku.

### <a name="enable-the-block-file-feature"></a>Włączanie funkcji pliku blokowego

Aby rozpocząć blokowanie plików, należy najpierw [włączyć funkcję **Blokuj lub zezwalaj** w](advanced-features.md) Ustawienia.

### <a name="allow-or-block-file"></a>Zezwalaj lub blokuj plik

Po dodaniu skrótu wskaźnika dla pliku możesz zgłosić alert i zablokować plik za każdym razem, gdy urządzenie w organizacji podejmie próbę jego uruchomienia.

Pliki automatycznie blokowane przez wskaźnik nie będą wyświetlane w centrum akcji pliku, ale alerty będą nadal widoczne w kolejce alertów.

Zobacz [zarządzanie wskaźnikami](manage-indicators.md) , aby uzyskać więcej informacji na temat blokowania i zgłaszania alertów dotyczących plików.

Aby zatrzymać blokowanie pliku, usuń wskaźnik. Można to zrobić za pomocą akcji **Edytuj wskaźnik** na stronie profilu pliku. Ta akcja będzie widoczna w tej samej pozycji co akcja **Dodaj wskaźnik** przed dodaniem wskaźnika.

Wskaźniki można również edytować na stronie **Ustawienia** w obszarze **Wskaźniki reguł**\>. Wskaźniki są wyświetlane w tym obszarze przez skrót pliku.

## <a name="consult-a-threat-expert"></a>Konsultuj się z ekspertem ds. zagrożeń

Skontaktuj się z ekspertem ds. zagrożeń firmy Microsoft, aby uzyskać więcej szczegółowych informacji na temat urządzeń, których bezpieczeństwo zostało potencjalnie naruszone lub które zostały już naruszone. Microsoft Threat Experts są zaangażowani bezpośrednio z poziomu portalu Microsoft 365 Defender w celu terminowego i dokładnego reagowania. Eksperci udostępniają szczegółowe informacje na temat potencjalnie zagrożonego urządzenia i pomagają zrozumieć złożone zagrożenia i ukierunkowane powiadomienia o atakach. Mogą również udostępniać informacje o alertach lub kontekście analizy zagrożeń widocznym na pulpicie nawigacyjnym portalu.

Szczegółowe informacje [można znaleźć w temacie Consult a Microsoft Threat Expert (Zapoznaj się z ekspertem ds. zagrożeń firmy Microsoft](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) ).

## <a name="check-activity-details-in-action-center"></a>Sprawdź szczegóły aktywności w Centrum akcji

**Centrum akcji** zawiera informacje o akcjach wykonywanych na urządzeniu lub pliku. Możesz wyświetlić następujące szczegóły:

- Badanie kolekcji pakietów
- Skanowanie antywirusowe
- Ograniczenie aplikacji
- Izolacja urządzenia

Wyświetlane są również wszystkie inne powiązane szczegóły, takie jak data/godzina przesłania, przesyłanie użytkownika oraz czy akcja zakończyła się pomyślnie lub nie powiodła się.

:::image type="content" source="images/action-center-details.png" alt-text="Centrum akcji z informacjami" lightbox="images/action-center-details.png":::

## <a name="deep-analysis"></a>Głęboka analiza

Badania zabezpieczeń cybernetycznych są zwykle wyzwalane przez alert. Alerty są powiązane z co najmniej jednym zaobserwowanym plikiem, które często są nowe lub nieznane. Wybranie pliku spowoduje przejście do widoku pliku, w którym można wyświetlić metadane pliku. Aby wzbogacić dane związane z plikiem, możesz przesłać plik do głębokiej analizy.

Funkcja analizy głębokiej wykonuje plik w bezpiecznym, w pełni instrumentowanym środowisku chmury. Wyniki szczegółowej analizy pokazują działania pliku, obserwowane zachowania i skojarzone artefakty, takie jak porzucone pliki, modyfikacje rejestru i komunikacja z adresami IP.
Głęboka analiza obsługuje obecnie obszerną analizę przenośnych plików wykonywalnych (PE), w tym _plików.exe_ i _.dll_ ).

Szczegółowa analiza pliku trwa kilka minut. Po zakończeniu analizy plików karta Analiza szczegółowa zostanie zaktualizowana w celu wyświetlenia podsumowania oraz daty i godziny najnowszych dostępnych wyników.

Podsumowanie analizy głębokiej zawiera listę *obserwowanych zachowań*, z których niektóre mogą wskazywać na złośliwe działanie i *obserwowane* działania, w tym kontaktowane adresy IP i pliki utworzone na dysku. Jeśli nic nie zostało znalezione, w tych sekcjach zostanie wyświetlony krótki komunikat.

Wyniki głębokiej analizy są dopasowywane do analizy zagrożeń, a wszystkie dopasowania wygenerują odpowiednie alerty.

Użyj funkcji analizy głębokiej, aby zbadać szczegóły dowolnego pliku, zwykle podczas badania alertu lub z innego powodu, w którym podejrzewasz złośliwe zachowanie. Ta funkcja jest dostępna na karcie **Analiza szczegółowa** na stronie profilu pliku.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4aAYy?rel=0]

**Funkcja Prześlij do analizy głębokiej** jest włączona, gdy plik jest dostępny w przykładowej kolekcji zaplecza usługi Defender for Endpoint lub jeśli zaobserwowano go na urządzeniu Windows 10, które obsługuje przesyłanie do głębokiej analizy.

> [!NOTE]
> Tylko pliki z Windows 10 i Windows 11 mogą być zbierane automatycznie.

Możesz również przesłać przykład za pośrednictwem [portalu Microsoft 365 Defender,](https://www.microsoft.com/security/portal/submission/submit.aspx) jeśli plik nie był obserwowany na urządzeniu Windows 10 (lub Windows 11) i poczekać na udostępnienie przycisku **Prześlij do analizy głębokiej**.

> [!NOTE]
> Ze względu na przepływy przetwarzania zaplecza w portalu Microsoft 365 Defender może wystąpić do 10 minut opóźnienia między przesłaniem pliku a dostępnością funkcji analizy głębokiej w usłudze Defender for Endpoint.

### <a name="submit-files-for-deep-analysis"></a>Przesyłanie plików do głębokiej analizy

1. Wybierz plik, który chcesz przesłać do głębokiej analizy. Możesz wybrać lub wyszukać plik z dowolnego z następujących widoków:

    - **Alerty** — wybierz linki do plików na osi czasu **Opis** lub **Szczegóły** na osi czasu wątku alertu
    - **Lista urządzeń** — wybierz linki do plików w sekcji **Opis** lub **Szczegóły** **w sekcji Urządzenie w organizacji**
    - **Pole wyszukiwania** — wybierz pozycję **Plik** z menu rozwijanego i wprowadź nazwę pliku

2. Na karcie **Analiza szczegółowa** widoku pliku wybierz pozycję **Prześlij**.

   :::image type="content" source="images/submit-file.png" alt-text="Przycisk Prześlij pliki PE" lightbox="images/submit-file.png":::

   > [!NOTE]
   > Obsługiwane są tylko pliki PE, w tym _pliki.exe_ i _.dll_ .

   Zostanie wyświetlony pasek postępu, który zawiera informacje o różnych etapach analizy. Następnie możesz wyświetlić raport po zakończeniu analizy.

> [!NOTE]
> W zależności od dostępności urządzenia czas zbierania przykładów może się różnić. Istnieje 3-godzinny limit czasu dla przykładowej kolekcji. Kolekcja zakończy się niepowodzeniem, a operacja zostanie przerwana, jeśli w tym czasie nie będzie żadnych raportów dotyczących urządzeń Windows 10 online (lub Windows 11). Możesz ponownie przesłać pliki do głębokiej analizy, aby uzyskać nowe dane w pliku.

### <a name="view-deep-analysis-reports"></a>Wyświetlanie raportów analizy głębokiej

Wyświetl udostępniony raport analizy szczegółowej, aby wyświetlić bardziej szczegółowe szczegółowe informacje na temat przesłanego pliku. Ta funkcja jest dostępna w kontekście widoku plików.

Możesz wyświetlić kompleksowy raport zawierający szczegółowe informacje na temat następujących sekcji:

- Zachowania
- Obserwowane elementy

Podane szczegóły mogą pomóc w zbadaniu, czy istnieją oznaki potencjalnego ataku.

1. Wybierz przesłany plik do głębokiej analizy.
2. Wybierz kartę **Analiza szczegółowa** . Jeśli istnieją jakieś poprzednie raporty, podsumowanie raportu zostanie wyświetlone na tej karcie.

   :::image type="content" source="images/analysis-results-nothing500.png" alt-text="Raport analizy głębokiej przedstawiający szczegółowe informacje w wielu kategoriach" lightbox="images/analysis-results-nothing500.png":::

#### <a name="troubleshoot-deep-analysis"></a>Rozwiązywanie problemów z głęboką analizą

Jeśli podczas próby przesłania pliku wystąpi problem, spróbuj wykonać każdy z poniższych kroków rozwiązywania problemów.

1. Upewnij się, że dany plik jest plikiem PE. Pliki PE zwykle mają _rozszerzenia.exe_ lub _.dll_ (programy wykonywalne lub aplikacje).

2. Upewnij się, że usługa ma dostęp do pliku, że nadal istnieje i nie została uszkodzona ani zmodyfikowana.

3. Poczekaj chwilę i spróbuj ponownie przesłać plik. Kolejka może być pełna lub wystąpił tymczasowy błąd połączenia lub komunikacji.

4. Jeśli przykładowe zasady zbierania nie są skonfigurowane, domyślnym zachowaniem jest zezwolenie na zbieranie przykładów. Jeśli jest skonfigurowany, sprawdź, czy ustawienie zasad zezwala na zbieranie przykładów przed ponownym przesłaniem pliku. Po skonfigurowaniu przykładowej kolekcji sprawdź następującą wartość rejestru:

    ```text
    Path: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
    Name: AllowSampleCollection
    Type: DWORD
    Hexadecimal value :
      Value = 0 - block sample collection
      Value = 1 - allow sample collection
    ```

5. Zmień jednostkę organizacyjną za pośrednictwem zasady grupy. Aby uzyskać więcej informacji, zobacz [Konfigurowanie za pomocą zasady grupy](configure-endpoints-gp.md).

6. Jeśli te kroki nie rozwiążą problemu, skontaktuj się z pomocą techniczną.

## <a name="related-topics"></a>Tematy pokrewne

- [Wykonaj akcje odpowiedzi na urządzeniu](respond-machine-alerts.md)
- [Badaj pliki](investigate-files.md)
- [Ręczne akcje reagowania w planie Ochrona punktu końcowego w usłudze Microsoft Defender 1](defender-endpoint-plan-1.md#manual-response-actions)
