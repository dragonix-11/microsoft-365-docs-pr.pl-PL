---
title: laboratorium ewaluacji Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się więcej o Ochrona punktu końcowego w usłudze Microsoft Defender możliwościach, uruchamianiu symulacji ataków i zobacz, jak zapobiega ono zagrożeniom, wykrywa je i koryguje.
keywords: ocena Ochrona punktu końcowego w usłudze Microsoft Defender, ocena, laboratorium, symulacja, Windows 10, Windows Server 2019, laboratorium ewaluacyjne
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.prod: m365-security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3d13c3b126f4aae75ff775ac3170049dfc9c0a2e
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65679445"
---
# <a name="microsoft-defender-for-endpoint-evaluation-lab"></a>laboratorium ewaluacji Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Przeprowadzenie kompleksowej oceny produktu w zakresie zabezpieczeń może być złożonym procesem wymagającym skomplikowanego środowiska i konfiguracji urządzenia, zanim będzie można faktycznie przeprowadzić kompleksową symulację ataku. Zwiększenie złożoności to wyzwanie związane ze śledzeniem sytuacji, w której działania symulacji, alerty i wyniki są odzwierciedlane podczas oceny.

Laboratorium oceny Ochrona punktu końcowego w usłudze Microsoft Defender ma na celu wyeliminowanie złożoności konfiguracji urządzenia i środowiska, dzięki czemu można skoncentrować się na ocenie możliwości platformy, uruchamianiu symulacji oraz wyświetlaniu funkcji zapobiegania, wykrywania i korygowania w działaniu.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUM]

Dzięki uproszczonemu środowisku konfiguracji możesz skupić się na uruchamianiu własnych scenariuszy testowych i wstępnie utworzonych symulacji, aby zobaczyć, jak działa usługa Defender for Endpoint.

Będziesz mieć pełny dostęp do zaawansowanych możliwości platformy, takich jak zautomatyzowane badania, zaawansowane wyszukiwanie zagrożeń i analiza zagrożeń, co pozwala przetestować kompleksowy stos ochrony, który oferuje usługa Defender for Endpoint.

Możesz dodać urządzenia Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 i Linux (Ubuntu), które są wstępnie skonfigurowane, aby mieć zainstalowane najnowsze wersje systemu operacyjnego i odpowiednie składniki zabezpieczeń, a także Office 2019 Standard.

Można również zainstalować symulatory zagrożeń. Usługa Defender for Endpoint nawiązała współpracę z wiodącymi w branży platformami symulacji zagrożeń, które ułatwiają testowanie możliwości usługi Defender for Endpoint bez konieczności opuszczania portalu.

Zainstaluj preferowany symulator, uruchom scenariusze w laboratorium ewaluacyjnym i natychmiast zobacz, jak działa platforma — wszystko to jest wygodnie dostępne bez dodatkowych kosztów. Będziesz mieć również wygodny dostęp do szerokiej gamy symulacji, do których można uzyskiwać dostęp i uruchamiać z katalogu symulacji.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby uzyskać dostęp do laboratorium oceny, musisz spełnić [wymagania licencyjne](minimum-requirements.md#licensing-requirements) lub mieć dostęp próbny do Ochrona punktu końcowego w usłudze Microsoft Defender.

Musisz mieć uprawnienia **Do zarządzania ustawieniami zabezpieczeń** :

- Tworzenie laboratorium
- Tworzenie urządzeń
- Resetuj hasło
- Tworzenie symulacji

Jeśli włączono kontrolę dostępu opartą na rolach (RBAC) i utworzono co najmniej jedną grupę maszyn, użytkownicy muszą mieć dostęp do wszystkich grup maszyn.

Aby uzyskać więcej informacji, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink)

## <a name="get-started-with-the-lab"></a>Wprowadzenie z laboratorium

Dostęp do laboratorium można uzyskać z menu. W menu nawigacji wybierz pozycję **Ocena i samouczki > laboratorium ewaluacji**.

> [!NOTE]
>
> - W zależności od wybranego typu struktury środowiska urządzenia będą dostępne przez określoną liczbę godzin od dnia aktywacji.
> - Każde środowisko jest aprowizowane z ograniczonym zestawem urządzeń testowych. Po użyciu aprowizowanych urządzeń i usunięciu ich można zażądać większej liczby urządzeń.
> - Zasoby laboratorium można żądać raz w miesiącu.

Masz już laboratorium? Pamiętaj, aby włączyć nowe symulatory zagrożeń i mieć aktywne urządzenia.

## <a name="setup-the-evaluation-lab"></a>Konfigurowanie laboratorium ewaluacyjnego

1. W okienku nawigacji wybierz pozycję **Ocena & samouczków** \> **Laboratorium ewaluacji**, a następnie wybierz pozycję **Laboratorium konfiguracji**.

   :::image type="content" source="../../media/evaluationtutormenu.png" alt-text="Strona powitalna laboratorium ewaluacji" lightbox="../../media/evaluationtutormenu.png":::

2. W zależności od potrzeb ewaluacyjnych można skonfigurować środowisko z mniejszą liczbą urządzeń przez dłuższy okres lub więcej urządzeń przez krótszy okres. Wybierz preferowaną konfigurację laboratorium, a następnie wybierz pozycję **Dalej**.

    :::image type="content" source="images/lab-creation-page.png" alt-text="Opcje konfiguracji laboratorium" lightbox="images/lab-creation-page.png":::

3. (Opcjonalnie) W laboratorium można zainstalować symulatory zagrożeń.

    :::image type="content" source="images/install-agent.png" alt-text="Strona agenta symulatorów instalacji" lightbox="images/install-agent.png":::

   > [!IMPORTANT]
   > Najpierw musisz zaakceptować i wyrazić zgodę na postanowienia i instrukcje dotyczące udostępniania informacji.

4. Wybierz agenta symulacji zagrożeń, którego chcesz użyć, i wprowadź swoje szczegóły. Możesz również zainstalować symulatory zagrożeń w późniejszym czasie. Jeśli zdecydujesz się zainstalować agentów symulacji zagrożeń podczas instalacji laboratorium, skorzystasz z zalet ich wygodnej instalacji na dodanych urządzeniach.

   :::image type="content" source="images/lab-setup-summary.png" alt-text="Strona podsumowania" lightbox="images/lab-setup-summary.png":::

5. Przejrzyj podsumowanie i wybierz pozycję **Laboratorium konfiguracji**.

Po zakończeniu procesu konfiguracji laboratorium można dodawać urządzenia i uruchamiać symulacje.

## <a name="add-devices"></a>Dodawanie urządzeń

Po dodaniu urządzenia do środowiska usługa Defender for Endpoint konfiguruje dobrze skonfigurowane urządzenie ze szczegółami połączenia. Możesz dodać Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 i Linux (Ubuntu).

Urządzenie zostanie skonfigurowane z najbardziej aktualną wersją systemu operacyjnego i Office 2019 Standard, a także innymi aplikacjami, takimi jak Java, Python i SysIntenals.

Jeśli podczas instalacji laboratorium wybrano opcję dodania symulatora zagrożeń, na dodanych urządzeniach na wszystkich urządzeniach zostanie zainstalowany agent symulatora zagrożeń.

Urządzenie zostanie automatycznie dołączone do dzierżawy z zalecanymi Windows składników zabezpieczeń włączonych i w trybie inspekcji — bez wysiłku po twojej stronie.

Następujące składniki zabezpieczeń są wstępnie skonfigurowane na urządzeniach testowych:

- [Zmniejszanie obszaru podatnego na ataki](attack-surface-reduction.md)
- [Blokuj od pierwszego wejrzenia](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Kontrolowany dostęp do folderu](controlled-folders.md)
- [Ochrona przed wykorzystywaniem](enable-exploit-protection.md)
- [Ochrona sieci](network-protection.md)
- [Potencjalnie niechciane wykrywanie aplikacji](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Ochrona dostarczana przez chmurę](cloud-protection-microsoft-defender-antivirus.md)
- [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

> [!NOTE]
> Program antywirusowy Microsoft Defender będzie włączone (nie w trybie inspekcji). Jeśli Program antywirusowy Microsoft Defender uniemożliwia uruchamianie symulacji, możesz wyłączyć ochronę urządzenia w czasie rzeczywistym za pośrednictwem Zabezpieczenia Windows. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zawsze włączonej ochrony](configure-real-time-protection-microsoft-defender-antivirus.md).

Ustawienia zautomatyzowanego badania będą zależeć od ustawień dzierżawy. Zostanie on domyślnie skonfigurowany jako półautomatyczny. Aby uzyskać więcej informacji, zobacz [Omówienie zautomatyzowanych badań](automated-investigations.md).

> [!NOTE]
> Połączenie z urządzeniami testowymi odbywa się przy użyciu protokołu RDP. Upewnij się, że ustawienia zapory zezwalają na połączenia RDP.

1. Na pulpicie nawigacyjnym wybierz pozycję **Dodaj urządzenie**.

2. Wybierz typ urządzenia do dodania. Możesz dodać Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 i Linux (Ubuntu).

   :::image type="content" source="../../media/add-machine-optionsnew.png" alt-text="Konfiguracja laboratorium z opcjami urządzenia" lightbox="../../media/add-machine-optionsnew.png":::

   > [!NOTE]
   > Jeśli coś pójdzie nie tak z procesem tworzenia urządzenia, otrzymasz powiadomienie i będziesz musiał przesłać nowe żądanie. Jeśli tworzenie urządzenia zakończy się niepowodzeniem, nie zostanie ono zliczone do ogólnego dozwolonego limitu przydziału.

3. Zostaną wyświetlone szczegóły połączenia. Wybierz pozycję **Kopiuj** , aby zapisać hasło dla urządzenia.

   > [!NOTE]
   > Hasło jest wyświetlane tylko raz. Pamiętaj, aby zapisać go do późniejszego użycia.

    :::image type="content" source="../../media/add-machine-eval-lab-new.png" alt-text="Urządzenie dodane ze szczegółami połączenia" lightbox="../../media/add-machine-eval-lab-new.png":::

4. Rozpoczyna się konfigurowanie urządzenia. Może to potrwać do około 30 minut.

5. Zobacz stan urządzeń testowych, poziomy ryzyka i narażenia oraz stan instalacji symulatora, wybierając kartę **Urządzenia** .

   :::image type="content" source="images/machines-tab.png" alt-text="Karta Urządzenia" lightbox="images/machines-tab.png":::
    

   > [!TIP]
   > W kolumnie **Stan symulatora** możesz zatrzymać kursor na ikonie informacji, aby poznać stan instalacji agenta.


## <a name="add-a-domain-controller-preview"></a>Dodawanie kontrolera domeny (wersja zapoznawcza)

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Dodaj kontroler domeny do uruchamiania złożonych scenariuszy, takich jak przenoszenie boczne i ataki wieloetapowe na wielu urządzeniach.


>[!NOTE]
>Obsługa domeny jest dostępna tylko w portalu Microsoft 365 Defender (security.microsoft.com).

1. Na pulpicie nawigacyjnym wybierz pozycję **Dodaj urządzenie**.

2. Wybierz **pozycję Windows Server 2019**, a następnie wybierz pozycję **Ustaw jako kontroler domeny**. 

3. Po aprowizowaniu kontrolera domeny będzie można tworzyć urządzenia przyłączone do domeny, klikając pozycję **Dodaj urządzenie**. Następnie wybierz pozycję Windows 10/Windows 11 i wybierz pozycję **Dołącz do domeny**. 

>[!NOTE]
>Jednocześnie może istnieć tylko jeden kontroler domeny. Urządzenie kontrolera domeny pozostanie aktywne tak długo, jak długo będzie z nim połączone urządzenie na żywo.



## <a name="request-for-more-devices"></a>Żądanie większej liczby urządzeń

Gdy wszystkie istniejące urządzenia są używane i usuwane, możesz poprosić o więcej urządzeń. Zasoby laboratorium można żądać raz w miesiącu.

1. Na pulpicie nawigacyjnym laboratorium ewaluacyjnego wybierz pozycję **Zażądaj większej liczby urządzeń**.

   :::image type="content" source="images/request-more-devices.png" alt-text="Opcja żądania większej liczby urządzeń" lightbox="images/request-more-devices.png":::

2. Wybierz konfigurację.
3. Prześlij żądanie.

Po pomyślnym przesłaniu żądania zobaczysz zielony baner potwierdzający i datę ostatniego przesłania.

Stan żądania można znaleźć na karcie **Akcje użytkownika** , która zostanie zatwierdzona w ciągu kilku godzin.

Po zatwierdzeniu żądane urządzenia zostaną dodane do konfiguracji laboratorium i będzie można utworzyć więcej urządzeń.

> [!TIP]
> Aby uzyskać więcej informacji z laboratorium, nie zapomnij zapoznać się z naszą biblioteką symulacji.

## <a name="simulate-attack-scenarios"></a>Symulowanie scenariuszy ataków

Użyj urządzeń testowych, aby uruchamiać własne symulacje ataków, łącząc się z nimi.

Scenariusze ataków można symulować przy użyciu:

- [Scenariusze ataku "Zrób to sam"](https://security.microsoft.com/tutorials/all)
- Symulatory zagrożeń

Zaawansowane [wyszukiwanie zagrożeń](advanced-hunting-overview.md) umożliwia również wykonywanie zapytań dotyczących danych i [analizy zagrożeń](threat-analytics.md) w celu wyświetlania raportów dotyczących pojawiających się zagrożeń.

### <a name="do-it-yourself-attack-scenarios"></a>Scenariusze ataków typu "zrób to sam"

Jeśli szukasz wstępnie wykonanej symulacji, możesz użyć [scenariuszy ataku "Zrób to sam"](https://security.microsoft.com/tutorials/all). Te skrypty są bezpieczne, udokumentowane i łatwe w użyciu. Te scenariusze będą odzwierciedlać możliwości usługi Defender for Endpoint i przeprowadzą Cię przez środowisko badania.

> [!NOTE]
> Połączenie z urządzeniami testowymi odbywa się przy użyciu protokołu RDP. Upewnij się, że ustawienia zapory zezwalają na połączenia RDP.

1. Połączenie do urządzenia i uruchom symulację ataku, wybierając **pozycję Połączenie**.

    :::image type="content" source="images/test-machine-table.png" alt-text="Przycisk Połączenie dla urządzeń testowych" lightbox="images/test-machine-table.png":::


   :::image type="content" source="images/remote-connection.png" alt-text="Ekran połączenia pulpitu zdalnego" lightbox="images/remote-connection.png":::

    W przypadku **urządzeń z systemem Linux**: należy użyć lokalnego klienta SSH i dostarczonego polecenia. 


    > [!NOTE]
    > Jeśli nie masz kopii hasła zapisanej podczas początkowej konfiguracji, możesz zresetować hasło, wybierając pozycję **Resetuj hasło** z menu:
    >
    > :::image type="content" source="images/reset-password-test-machine.png" alt-text="Opcja Resetuj hasło" lightbox="images/reset-password-test-machine.png":::
    >
    > Urządzenie zmieni jego stan na "Wykonywanie resetowania hasła", a następnie za kilka minut zostanie wyświetlone nowe hasło.

3. Wprowadź hasło, które zostało wyświetlone podczas kroku tworzenia urządzenia.

   :::image type="content" source="images/enter-password.png" alt-text="Ekran, na którym wprowadzasz poświadczenia" lightbox="images/enter-password.png":::

4. Uruchom symulacje ataków samodzielnych na urządzeniu.

### <a name="threat-simulator-scenarios"></a>Scenariusze symulatora zagrożeń

Jeśli podczas instalacji laboratorium wybrano instalację dowolnego z obsługiwanych symulatorów zagrożeń, możesz uruchomić wbudowane symulacje na urządzeniach laboratorium ewaluacyjnego.

Uruchamianie symulacji zagrożeń przy użyciu platform innych firm to dobry sposób oceny Ochrona punktu końcowego w usłudze Microsoft Defender możliwości w granicach środowiska laboratoryjnego.

> [!NOTE]
>
> Przed uruchomieniem symulacji upewnij się, że zostały spełnione następujące wymagania:
>
> - Urządzenia muszą zostać dodane do laboratorium ewaluacji
> - Symulatory zagrożeń muszą być zainstalowane w laboratorium ewaluacyjnym

1. W portalu wybierz pozycję **Utwórz symulację**.

2. Wybierz symulator zagrożeń.

   :::image type="content" source="images/select-simulator.png" alt-text="Wybór symulatora zagrożeń" lightbox="images/select-simulator.png":::

3. Wybierz symulację lub przejrzyj galerię symulacji, aby przejrzeć dostępne symulacje.

    Możesz przejść do galerii symulacji z:
    - Główny pulpit nawigacyjny oceny na kafelku **Omówienie symulacji** lub
    - Przechodząc z okienka nawigacji **Ewaluacja i samouczki** \> **symulacji & samouczków**, wybierz pozycję **Wykaz symulacji**.

4. Wybierz urządzenia, na których chcesz uruchomić symulację.

5. Wybierz pozycję **Utwórz symulację**.

6. Wyświetl postęp symulacji, wybierając kartę **Symulacje** . Wyświetl stan symulacji, aktywne alerty i inne szczegóły.

   :::image type="content" source="images/simulations-tab.png" alt-text="Karta Symulacje" lightbox="images/simulations-tab.png":::

Po uruchomieniu symulacji zachęcamy do przejścia przez pasek postępu laboratorium i zbadania **, Ochrona punktu końcowego w usłudze Microsoft Defender wyzwoliły zautomatyzowane badanie i korygowanie**. Zapoznaj się z dowodami zebranymi i przeanalizowanymi przez funkcję.

Wyszukiwanie dowodów ataków dzięki zaawansowanemu wyszukiwaniu przy użyciu zaawansowanego języka zapytań i nieprzetworzonych danych telemetrycznych oraz zapoznanie się z niektórymi zagrożeniami na całym świecie udokumentowane w analizie zagrożeń.

## <a name="simulation-gallery"></a>Galeria symulacji

Ochrona punktu końcowego w usłudze Microsoft Defender nawiązała współpracę z różnymi platformami symulacji zagrożeń, aby zapewnić wygodny dostęp do testowania możliwości platformy bezpośrednio z poziomu portalu.

Wyświetl wszystkie dostępne symulacje, przechodząc do **katalogu Symulacje** **i samouczki Symulacje** \> z menu.

Lista obsługiwanych agentów symulacji zagrożeń innych firm jest wyświetlana, a w wykazie znajdują się określone typy symulacji wraz ze szczegółowymi opisami.

Możesz wygodnie uruchomić dowolną dostępną symulację bezpośrednio z katalogu.

:::image type="content" source="images/simulations-catalog.png" alt-text="Wykaz symulacji" lightbox="images/simulations-catalog.png":::

Każda symulacja zawiera szczegółowy opis scenariusza ataku i odwołania, takie jak używane techniki ataków MITRE i przykładowe uruchamiane zaawansowane zapytania wyszukiwania zagrożeń.

**Przykłady:**

:::image type="content" source="images/simulation-details-aiq.png" alt-text="Przykład okienka szczegółów opisu symulacji dla metod trwałości" lightbox="images/simulation-details-aiq.png":::

:::image type="content" source="images/simulation-details-sb.png" alt-text="Szczegóły opisu symulacji dla APT29" lightbox="images/simulation-details-sb.png":::

## <a name="evaluation-report"></a>Raport ewaluacji

Raporty laboratorium podsumowują wyniki symulacji przeprowadzonych na urządzeniach.

:::image type="content" source="images/eval-report.png" alt-text="Raport ewaluacji" lightbox="images/eval-report.png":::

Szybko zobaczysz następujące elementy:

- Zdarzenia, które zostały wyzwolone
- Wygenerowane alerty
- Oceny na poziomie narażenia
- Zaobserwowano kategorie zagrożeń
- Źródła wykrywania
- Zautomatyzowane badania

## <a name="provide-feedback"></a>Przekazywanie opinii

Twoja opinia pomaga nam lepiej chronić środowisko przed zaawansowanymi atakami. Podziel się swoim doświadczeniem i wrażeniami z możliwości produktu i wyników oceny.

Daj nam znać, co myślisz, wybierając pozycję **Przekaż opinię**.

:::image type="content" source="images/send-us-feedback-eval-lab.png" alt-text="Strona opinii" lightbox="images/send-us-feedback-eval-lab.png":::
