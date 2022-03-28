---
title: Wypróbuj Microsoft 365 Defender reagowania na zdarzenia w środowisku pilotażowym
description: Wypróbuj funkcje reagowania na incydenty Microsoft 365 Defender w celu ustalania priorytetów zdarzeń i zarządzania nimi, automatyzowania badań i używania zaawansowanego wyszukiwania w celu wykrywania zagrożeń.
keywords: Microsoft 365 Defender próbny, spróbuj Microsoft 365 Defender, oceń Microsoft 365 Defender, Microsoft 365 Defender laboratorium oceniania, Microsoft 365 Defender  pilot, zabezpieczenia cyberzabłędu, zaawansowane zagrożenia trwałe, zabezpieczenia przedsiębiorstwa, urządzenia, urządzenia, tożsamość, użytkownicy, dane, aplikacje, zdarzenia, zautomatyzowane badania i działania naprawcze, szukanie zaawansowane
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 0ad2fc9a1566e7816b3ff806b7d07ac29347cc89
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754779"
---
# <a name="try-microsoft-365-defender-incident-response-capabilities-in-a-pilot-environment"></a>Wypróbuj Microsoft 365 Defender reagowania na zdarzenia w środowisku pilotażowym

**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł jest [krokiem 2 z 2](eval-defender-investigate-respond.md) w procesie wykonywania badania i reakcji w przypadku zdarzenia w Microsoft 365 Defender przy użyciu środowiska pilotażowego. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-investigate-respond.md) .

Po wykonaniu reakcji dotyczącej zdarzenia [w przypadku symulowanego](eval-defender-investigate-respond-simulate-attack.md) ataków warto poznać Microsoft 365 Defender czynności:

|Funkcja |Opis |
|:-------|:-----|
| [Określanie priorytetu zdarzeń](#prioritize-incidents) | Użyj filtrowania i sortowania kolejki zdarzeń, aby określić, które zdarzenia należy w następnej kolejności rozwiązać. |
| [Zarządzanie zdarzeniami](#manage-incidents) | Modyfikowanie właściwości zdarzenia w celu zapewnienia poprawnego przypisywania, dodawania znaczników i komentarzy oraz rozwiązywania problemów. |
| [Zautomatyzowane badanie i odpowiedź](#examine-automated-investigation-and-response-with-the-action-center) | Użyj funkcji automatycznego badania i odpowiedzi (AIR), aby ułatwić zespołowi ds. bezpieczeństwa wydajniejsze i skuteczniejsze reagowanie na zagrożenia. Centrum akcji to "pojedyncze okienko zeszyt" dla zadań alertów i zdarzeń, takich jak zatwierdzanie oczekujących działań naprawczych. |
| [Zaawansowane wyszukiwanie zagrożeń](#use-advanced-hunting) | Za pomocą zapytań możesz proaktywnie przeprowadzać inspekcje zdarzeń w sieci oraz znajdować wskaźniki zagrożeń i jednostki. Korzystasz również z zaawansowanego wyszukiwania podczas badania i rozwiązywania problemów. |


## <a name="prioritize-incidents"></a>Określanie priorytetów zdarzeń

Do kolejki zdarzeń możesz uzyskać dostęp z menu **Zdarzenia & alerty > zdarzenia** na pasku Szybkie uruchamianie portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender zdarzenia.</a> Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Sekcja Alerty o & zdarzeniach w portalu Microsoft 365 Defender w programie" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::


Sekcja **Najnowsze zdarzenia i** alerty zawiera wykres liczby otrzymywanych alertów i zdarzeń utworzonych w ciągu ostatnich 24 godzin.

Aby zbadać listę zdarzeń i ustalić priorytet ich ważności dla zadania i badania, możesz: 

- Skonfiguruj dostosowywalne kolumny (wybierz **pozycję Wybierz** kolumny), aby zapewnić Ci wgląd w różne cechy zdarzenia lub jednostek, których to wpływ. Ułatwia to podejmowanie przejętnych decyzji dotyczących priorytetów zdarzeń w analizie.

- Filtrowanie umożliwia skoncentrowanie się na konkretnym scenariuszu lub zagrożeń. Stosowanie filtrów w kolejce zdarzeń może ułatwić ustalenie, które zdarzenia wymagają natychmiastowej uwagi. 

W domyślnej kolejce zdarzeń wybierz pozycję **Filtry** , aby wyświetlić okienko **Filtry** , w którym możesz określić określony zestaw zdarzeń. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Okienko Filtry w sekcji Alerty o & zdarzeniach w portalu Microsoft 365 Defender wiadomości" lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Aby uzyskać więcej informacji, zobacz [Określanie priorytetów zdarzeń](incident-queue.md).

## <a name="manage-incidents"></a>Zarządzanie zdarzeniami

Możesz zarządzać zdarzeniami z **okienka Zarządzanie zdarzeniami** w przypadku zdarzenia. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Okienko Zarządzanie zdarzeniami w sekcji Alerty o & zdarzeniach w portalu Microsoft 365 Defender zdarzenia" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

To okienko można wyświetlić za pomocą **linku Zarządzaj incydentem** na stronie:

- Okienko Właściwości zdarzenia w kolejce zdarzenia.
- **Strona** podsumowania zdarzenia.

Oto sposoby zarządzania zdarzeniami:

- Edytowanie nazwy zdarzenia

  Zmień automatycznie przypisaną nazwę na podstawie najlepszych rozwiązań dla zespołu zabezpieczeń.
  
- Dodawanie tagów zdarzeń

  Dodaj tagi używane przez Twój zespół zabezpieczeń do klasyfikowania zdarzeń, które można później filtrować.
  
- Przypisywanie zdarzenia

  Przypisz ją do nazwy konta użytkownika, którą można później filtrować.
  
- Rozwiązywanie zdarzenia

  Po zakończeniu rozwiązywania problemów zamknij zdarzenie.
  
- Ustawianie klasyfikacji i wyznaczania jej

  Klasyfikowanie i wybieranie typu zagrożenia podczas rozwiązywania zdarzenia.
  
- Dodawanie komentarzy

  Używaj komentarzy do postępu, notatek lub innych informacji na podstawie najlepszych rozwiązań dotyczących zespołu zabezpieczeń. Pełna historia komentarzy jest dostępna w opcji **Komentarze i historia** na stronie szczegółów zdarzenia.

Aby uzyskać więcej informacji, zobacz [Zarządzanie zdarzeniami](manage-incidents.md).

## <a name="examine-automated-investigation-and-response-with-the-action-center"></a>Sprawdzaj automatyczne badania i odpowiedzi przy użyciu Centrum akcji

W zależności od tego, jak są skonfigurowane funkcje automatycznego badania i reakcji dla organizacji, działania naprawcze są podejmowane automatycznie lub tylko po zatwierdzeniu ich przez zespół operacyjny ds. zabezpieczeń. Wszystkie akcje, zarówno oczekujące, jak i ukończone, są wyświetlane w Centrum [akcji, które](m365d-action-center.md) zawiera listę oczekujących i ukończonych akcji naprawczych dla Twoich urządzeń, wiadomości e-mail & zawartości współpracy i tożsamości w jednym miejscu.

Oto przykład.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Ujednolicone Centrum akcji w portalu Microsoft 365 Defender akcji" lightbox="../../media/m3d-action-center-unified.png":::

W Centrum akcji możesz wybrać oczekujące akcje, a następnie zatwierdzić je lub odrzucić w okienku wysuwanych. Oto przykład.

:::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Okienko z opcjami zatwierdzania lub odrzucania akcji w portalu Microsoft 365 Defender zadań" lightbox="../../media/air-actioncenter-itemselected.png":::


Zatwierdź (lub odrzuć) oczekujące akcje jak najszybciej, aby zautomatyzowane badania były w stanie wykonać w terminie.

Aby uzyskać więcej informacji, zobacz [Automatyczne badanie i odpowiedzi](m365d-autoir.md) [oraz Centrum akcji](m365d-action-center.md).

## <a name="use-advanced-hunting"></a>Użyj zaawansowanego wyszukiwania

> [!NOTE]
> Przed rozpoczęciem zaawansowanej symulacyjnej pracy myśliwskiej obejrzyj poniższy klip wideo, aby poznać zaawansowane koncepcje myśliwskie, dowiedzieć się, gdzie można je znaleźć w portalu i jak może pomóc Ci w operacjach zabezpieczających.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]


Jeśli opcjonalna symulacja ataków bez użycia plików programu [PowerShell](eval-defender-investigate-respond-simulate-attack.md#simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional) była prawdziwym atakiem, który już przeszedł etap dostępu poświadczeń, możesz użyć zaawansowanego wyszukiwania w dowolnym momencie w śledztwie, aby aktywnie przeszukiwać zdarzenia i rekordy w sieci przy użyciu tego, co już znasz z wygenerowanych alertów i jednostek, których to dotyczy. 

Na przykład na podstawie informacji z alertu rozpoznawczego użytkownika i adresu [IP (SMB, User and IP address reconnaissance)](eval-defender-investigate-respond-simulate-attack.md#alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity) możesz użyć tabeli, `IdentityDirectoryEvents` aby znaleźć wszystkie zdarzenia wyliczania sesji SMB lub znaleźć więcej działań odnajdowania w różnych innych protokołach w programie Microsoft Defender dla `IdentityQueryEvents` danych tożsamości przy użyciu tabeli.


### <a name="hunting-environment-requirements"></a>Wymagania dotyczące środowiska łowego

Do tej symulacji jest wymagana pojedyncza wewnętrzna skrzynka pocztowa i urządzenie. Do wysłania wiadomości testowej potrzebne jest również zewnętrzne konto e-mail.

1. Sprawdź, czy w dzierżawie [włączono Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. Zidentyfikuj docelową skrzynkę pocztową, która ma być używana do odbierania wiadomości e-mail.

   - Ta skrzynka pocztowa musi być monitorowana przez program Microsoft Defender dla Office 365

   - Urządzenie z wymagania 3 musi mieć dostęp do tej skrzynki pocztowej

3. Konfigurowanie urządzenia testowego:

    a. Upewnij się, że korzystasz z Windows 10 1903 lub nowszej.

    b. Dołącz urządzenie testowe do domeny testowej.

    c. [Włącz Program antywirusowy Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). Jeśli masz problem z włączeniem Program antywirusowy Windows Defender, zobacz [ten temat rozwiązywania problemów](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

    d. [Wdowy do programu Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="run-the-simulation"></a>Uruchamianie symulacyjnej

1. Z zewnętrznego konta e-mail wyślij wiadomość e-mail do skrzynki pocztowej zidentyfikowaną w kroku 2 sekcji wymagań dotyczących środowiska pracy myśliwskiej. Dołącz załącznik, który będzie dozwolony za pośrednictwem wszelkich istniejących zasad filtrowania wiadomości e-mail. Ten plik nie musi być złośliwy ani wykonywalny. Sugerowane typy plików <i> to.pdf</i>, <i>.exe</i> (jeśli są dozwolone) lub Office typu dokumentu, na przykład plik programu Word.

2. Otwórz wysłaną wiadomość e-mail z urządzenia skonfigurowanego jako zdefiniowane w kroku 3 sekcji wymagań środowiska pracy. Otwórz załącznik lub zapisz plik na urządzeniu.

#### <a name="go-hunting"></a>Idź na pochody

1. Otwórz Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">witryny</a>.

2. W okienku nawigacji wybierz pozycję **Czas na > zaawansowanego chowania**.

3. Tworzenie zapytania, które rozpocznie się od zbierania zdarzeń wiadomości e-mail.

   1. Wybierz **pozycję Zapytanie > Nowy**.

   1. W **grupach Poczty** e-mail w **obszarze Zaawansowane** szukanie kliknij **dwukrotnie pozycję EmailEvents**. Powinien on być wyświetlony w oknie zapytania.

      ```console
      EmailEvents
      ```

   1. Zmień ramy czasowe zapytania na ostatnie 24 godziny. Zakładając, że wiadomość e-mail wysłana po czasie działania powyższej symulacyjnej przebiegła w ciągu ostatnich 24 godzin, w przeciwnym razie zmień ramy czasowe zgodnie z potrzebami.

   1. Wybierz **pozycję Uruchom zapytanie**. Wyniki mogą się różnić w zależności od środowiska pilotażowego.

      > [!NOTE]
      > Zobacz następny krok, aby uzyskać informacje na temat opcji filtrowania w celu ograniczenia możliwości zwracania danych.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-1.png" alt-text="Strona zaawansowanego wyszukiwania w Microsoft 365 Defender wyszukiwania" lightbox="../../media/advanced-hunting-incident-response-try-1.png":::

        > [!NOTE]
        > Funkcja wyszukiwania zaawansowanego wyświetla wyniki zapytania jako dane tabelarowe. Możesz również wyświetlić dane w innych typach formatów, takich jak wykresy.

   1. Zapoznaj się z wynikami i sprawdź, czy możesz zidentyfikować otwartą wiadomość e-mail. Może upłynieć do dwóch godzin, aż wiadomość pojawi się w zaawansowanym chłonie. Aby zawęzić wyniki, możesz dodać  do zapytania warunek gdzie, aby szukać tylko wiadomości e-mail z yahoo.com jako senderMailFromDomain. Oto przykład.

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. Kliknij wiersze wynikowe z zapytania, aby sprawdzić rekord.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-2.png" alt-text="Sekcja Inspekcja rekordu na stronie zaawansowanego wyszukiwania w portalu Microsoft 365 Defender zaawansowanego" lightbox="../../media/advanced-hunting-incident-response-try-2.png":::

4. Po sprawdzeniu, że wiadomości e-mail są już dostępne, dodaj filtr załączników. Skoncentruj się na wszystkich wiadomościach e-mail z załącznikami w środowisku. W przypadku tej symulacyjnej pracy należy się skupić na przychodzących wiadomościach e-mail, a nie na tych, które są wysyłane ze środowiska. Usuń wszelkie filtry dodane w celu zlokalizowania wiadomości i dodaj "| gdzie **AttachmentCount > 0** i **EmailDirection** == **"Inbound""**

   Poniższe zapytanie spowoduje wyświetlanie wyników z krótszą listą niż zapytanie początkowe dla wszystkich zdarzeń wiadomości e-mail:

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. Następnie dołącz do zestawu wyników informacje o załączniku (takie jak: nazwa pliku czy skróty). Aby to zrobić, dołącz do **tabeli EmailAttachmentInfo** . Pola wspólne, których należy użyć w celu dołączenia, w tym przypadku to **NetworkMessageId** i **RecipientObjectId**.

   Poniższe zapytanie zawiera również dodatkowy wiersz "| **project-rename EmailTimestamp=Timestamp"**, ułatwiający określenie, który sygnatura czasowa była powiązana z pocztą e-mail, a sygnatury czasowe związane z akcjami pliku, które dodasz w następnym kroku.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. Następnie użyj wartości **SHA256** z tabeli **EmailAttachmentInfo** , aby znaleźć zdarzenia **DeviceFileEvents** (akcje pliku, które wydarzyły się w punkcie końcowym) dla tego skrótu. Najczęściej spotykane w tym miejscu będzie skrót SHA256 załącznika.

   W tabeli wynikowej znajdują się teraz szczegóły z punktu końcowego (Microsoft Defender for Endpoint), takie jak nazwa urządzenia, co zostało wykonane (w tym przypadku odfiltrowane tak, aby uwzględniały tylko zdarzenia FileCreated) i gdzie plik był przechowywany. Zostanie również uwzględniona nazwa konta skojarzona z tym procesem.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   Zostało utworzone zapytanie identyfikujące wszystkie przychodzące wiadomości e-mail, w których użytkownik otwierał lub zapisywał załącznik. Możesz również uściślić to zapytanie, aby filtrować według konkretnych domen nadawcy, rozmiarów plików, typów plików i tak dalej.

7. Funkcje to specjalny rodzaj sprzężenia, który pozwala na przyciągnięcie kolejnych danych TI na temat pliku, np. informacje o jego adresacie, podpiszeniu i wystawcy itp. Aby uzyskać więcej szczegółowych informacji na temat pliku, wzbogać funkcję **FileProfile(** ):

    ```console
    EmailEvents
    | where AttachmentCount > 0 and EmailDirection == "Inbound"
    | project-rename EmailTimestamp=Timestamp
    | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
    | join DeviceFileEvents on SHA256
    | where ActionType == "FileCreated"
    | distinct SHA1
    | invoke FileProfile()
    ```

#### <a name="create-a-detection"></a>Tworzenie wykrywania

Po utworzeniu zapytania identyfikującego informacje, o których chcesz w przyszłości otrzymać **alerty** , możesz utworzyć wykrywanie niestandardowe na podstawie zapytania.

Wykrywanie niestandardowe będzie uruchamiać zapytanie zgodnie z ustawioną częstotliwością, a wyniki zapytań będą tworzyć alerty zabezpieczeń na podstawie wyboru zasobów. Alerty te będą skorelowane z zdarzeniami i mogą być triagedowane jako wszelkie inne alerty zabezpieczeń wygenerowane przez jeden z produktów.

1. Na stronie zapytania usuń wiersze 7 i 8, które zostały dodane w kroku 7 instrukcji go wyszukiwania, i kliknij pozycję **Utwórz regułę wykrywania**.

   :::image type="content" source="../../media/advanced-hunting-incident-response-try-3.png" alt-text="Sekcja edytowania zapytania na stronie zaawansowanego wyszukiwania w portalu Microsoft 365 Defender zaawansowanego" lightbox="../../media/advanced-hunting-incident-response-try-3.png":::

   > [!NOTE]
   > Jeśli klikniesz **pozycję Utwórz regułę wykrywania** i w zapytaniu będą wystąpiły błędy składni, reguła wykrywania nie zostanie zapisana. Sprawdź dwukrotnie zapytanie, aby upewnić się, że nie wystąpiły żadne błędy.

2. Wypełnij wymagane pola informacjami, które umożliwią zespołowi zabezpieczeń zrozumienie alertu, przyczyny jego wygenerowania i czynności, które mogą być podejmowane przez zespół zabezpieczeń.

   :::image type="content" source="../../media/mtp/fig23.png" alt-text="Strona Szczegóły alertu w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/mtp/fig23.png":::

   Zadbaj o czytelność pól, aby ułatwić następnej użytkownikowi podejmowanie decyzji dotyczącej alertu z regułą wykrywania.

3. Wybierz encje, których dotyczy ten alert. W tym przypadku wybierz pozycję **Urządzenie i skrzynka** **pocztowa**.

   :::image type="content" source="../../media/mtp/fig24.png" alt-text="Strona szczegółów jednostek wpływanych na w Microsoft 365 Defender sieci Web" lightbox="../../media/mtp/fig24.png":::

4. Określ, jakie działania należy podjąć w przypadku uruchomienia alertu. W takim przypadku uruchom skanowanie antywirusowe, chociaż można podjąć inne działania.

   :::image type="content" source="../../media/mtp/fig25.png" alt-text="Strona Akcje w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/mtp/fig25.png":::

5. Wybierz zakres reguły alertu. Ponieważ to zapytanie obejmuje urządzenia, grupy urządzeń są istotne w tym niestandardowym wykrywaniu zgodnie z kontekstem programu Microsoft Defender for Endpoint. Podczas tworzenia wykrywania niestandardowego, które nie uwzględnia urządzeń jako jednostek, których to dotyczy, zakres nie ma zastosowania.

   :::image type="content" source="../../media/mtp/fig26.png" alt-text="Strona Zakres w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/mtp/fig26.png":::


   W ramach tego programu pilotażowego można ograniczyć tę regułę do podzbioru urządzeń testowych w środowisku produkcyjnym.

6. Wybierz pozycję **Utwórz**. Następnie wybierz pozycję **Niestandardowe reguły wykrywania** w panelu nawigacji.

   :::image type="content" source="../../media/mtp/fig27a.png" alt-text="Opcja Reguły wykrywania niestandardowego w portalu Microsoft 365 Defender automatycznego" lightbox="../../media/mtp/fig27a.png":::

   :::image type="content" source="../../media/mtp/fig27b.png" alt-text="Strona z regułami wykrywania i szczegółami wykonywania w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/mtp/fig27b.png":::

   Na tej stronie możesz wybrać regułę wykrywania, co spowoduje otwarcie strony szczegółów.

   :::image type="content" source="../../media/mtp/fig28.png" alt-text="Strona z wyświetlonymi szczegółami alertów wyzwalanych w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/mtp/fig28.png":::


### <a name="expert-training-on-advanced-hunting"></a>Szkolenia ekspertów dotyczące zaawansowanego wyszukiwania

**Śledzenie obiektu adversary** to seria webcastów dla nowych analityków zabezpieczeń i zaprawianych w ogromów zagrożeń. Prowadzi Cię ona przez podstawy zaawansowanego wyszukiwania po wszystko, aby tworzyć własne, zaawansowane zapytania. 

Zobacz [Szkolenia ekspertów dotyczące zaawansowanego wyszukiwania](advanced-hunting-expert-training.md) w celu rozpoczęcia pracy.

### <a name="navigation-you-may-need"></a>Nawigacja, która może być potrzebna

[Tworzenie środowiska Microsoft 365 Defender oceny](eval-create-eval-environment.md)
