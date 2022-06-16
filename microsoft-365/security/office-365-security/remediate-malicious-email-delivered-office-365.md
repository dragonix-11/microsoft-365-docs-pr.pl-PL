---
title: Korygowanie złośliwych wiadomości e-mail dostarczonych w Office 365
author: msfttracyp
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.collection: M365-security-compliance
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: ''
search.appverid: MET150
description: Korygowanie zagrożeń
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6102d1e7d3b7e39787c3787b8bc0851eedbdcefb
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115548"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Korygowanie złośliwych wiadomości e-mail dostarczanych w usłudze Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)

Korygowanie oznacza podjęcie określonego działania przeciwko zagrożeniu. Złośliwe wiadomości e-mail wysyłane do organizacji mogą być czyszczone przez system, przez automatyczne przeczyszczanie bez godziny (ZAP) lub przez zespoły zabezpieczeń poprzez akcje korygowania, takie jak *przejście do skrzynki odbiorczej*, *przejście na śmieci*, *przejście do usuniętych elementów*, *usuwanie nietrwałe* lub *usuwanie twarde*. Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2/E5 umożliwia zespołom ds. zabezpieczeń korygowanie zagrożeń za pomocą poczty e-mail i funkcji współpracy za pomocą ręcznego i zautomatyzowanego badania.

> [!NOTE]
> Aby korygować złośliwe wiadomości e-mail, zespoły ds. zabezpieczeń potrzebują przypisanej roli *Wyszukiwanie i przeczyszczanie* . Przypisywanie roli odbywa się za pośrednictwem [uprawnień w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="what-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem

Administratorzy mogą podejmować wymagane działania w wiadomościach e-mail, ale aby te akcje zostały zatwierdzone, muszą mieć przypisaną rolę *Wyszukiwania i przeczyszczania* w uprawnieniach **do współpracy & poczty e-mail** w portalu Microsoft 365 Defender. Bez roli *Wyszukaj i przeczyszczanie* dodanej do jednej z grup ról nie będą mogli wykonać akcji.

Ponieważ akcje poczty e-mail tworzą zautomatyzowane badania w zapleczu, należy włączyć *automatyczne badanie*. Przejdź do **obszaru Ustawienia** \> **Funkcje zaawansowane** **punktów końcowych** \> i włącz funkcję **Zautomatyzowane badanie**.

## <a name="manual-and-automated-remediation"></a>Ręczne i zautomatyzowane korygowanie

*Ręczne wyszukiwanie zagrożeń* występuje, gdy zespoły zabezpieczeń ręcznie identyfikują zagrożenia przy użyciu funkcji wyszukiwania i filtrowania w Eksploratorze. Ręczne korygowanie poczty e-mail może być wyzwalane za pośrednictwem dowolnego widoku poczty e-mail (*złośliwego oprogramowania*, *języka Phish* lub *wszystkich wiadomości e-mail*) po zidentyfikowaniu zestawu wiadomości e-mail, które muszą zostać skorygowane.

:::image type="content" source="../../media/microsoft-365-defender-threat-explorer-manual-remediation.png" alt-text="Zrzut ekranu przedstawiający ręczne wyszukiwanie zagrożeń w Eksploratorze Office 365 według daty.":::

Zespoły zabezpieczeń mogą używać Eksploratora do wybierania wiadomości e-mail na kilka sposobów:

- Wybierz wiadomości e-mail ręcznie: użyj filtrów w różnych widokach. Wybierz maksymalnie 100 wiadomości e-mail do skorygowania.

- Wybór zapytania: wybierz całe zapytanie, używając górnego przycisku **wybierz wszystko** . To samo zapytanie jest również wyświetlane w szczegółach przesyłania poczty centrum akcji. Klienci mogą przesyłać maksymalnie 200 000 wiadomości e-mail z Eksploratora zagrożeń.  

- Wybór zapytania z wykluczeniem: Czasami zespoły operacji zabezpieczeń mogą chcieć korygować wiadomości e-mail, wybierając całe zapytanie i wykluczając niektóre wiadomości e-mail z zapytania ręcznie. W tym celu administrator może użyć pola wyboru **Zaznacz wszystko** i przewiń w dół, aby ręcznie wykluczyć wiadomości e-mail. Zapytanie może zawierać maksymalnie 1000 wiadomości e-mail. Maksymalna liczba wykluczeń wynosi 100.

Po wybraniu wiadomości e-mail za pośrednictwem Eksploratora możesz rozpocząć korygowanie, podejmując akcję bezpośrednią lub kolejkując wiadomości e-mail w celu wykonania akcji:

- Bezpośrednie zatwierdzenie: Gdy akcje, takie jak *przenoszenie do skrzynki odbiorczej*, *przenoszenie do wiadomości-śmieci*, *przenoszenie do usuniętych elementów*, *usuwanie nietrwałe* lub *usuwanie twarde* , są wybierane przez pracowników ochrony, którzy mają odpowiednie uprawnienia, a następnie są wykonywane kolejne kroki korygowania, proces korygowania rozpoczyna wykonywanie wybranej akcji.
> [!NOTE]
> Gdy korygowanie zostanie uruchomione, generuje alert i badanie równolegle. Alert jest wyświetlany w kolejce alertów o nazwie "Akcja administracyjna przesłana przez administratora" sugerująca, że pracownicy ochrony podjęli akcję korygowania jednostki. Przedstawia szczegóły, takie jak imię i nazwisko osoby, która wykonała akcję, link do badania pomocniczego, czas itp. To działa naprawdę dobrze wiedzieć za każdym razem, gdy trudne działania, takie jak korygowanie jest wykonywana na jednostkach. Wszystkie te akcje można śledzić na **karcie Historia** **centrum**  ->  akcji **& Przesłania** \> (publiczna wersja zapoznawcza).

- Zatwierdzanie dwuetapowe: akcję "dodaj do korygowania" mogą wykonać administratorzy, którzy nie mają odpowiednich uprawnień lub muszą poczekać na wykonanie akcji. W takim przypadku docelowe wiadomości e-mail są dodawane do kontenera korygowania. Zatwierdzenie jest wymagane przed wykonaniem korygowania.

**Zautomatyzowane akcje badania i reagowania** są wyzwalane przez alerty lub zespoły operacji zabezpieczeń z Eksploratora. Mogą one obejmować zalecane akcje korygowania, które muszą zostać zatwierdzone przez zespół ds. operacji zabezpieczeń. Te akcje są uwzględniane na karcie **Akcja** w zautomatyzowanym badaniu.

> [!div class="mx-imgBorder"]
> [![Poczta ze złośliwym oprogramowaniem na stronie "Zapped" z czasem wykonywania zap.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Wszystkie korygowanie (zatwierdzenia bezpośrednie) utworzone w Eksploratorze, Zaawansowane wyszukiwanie zagrożeń lub za pośrednictwem zautomatyzowanego badania są wyświetlane w Centrum akcji. Uzyskaj do nich dostęp za pośrednictwem panelu nawigacyjnego po lewej stronie w obszarze **Akcje** \> &**Karta Historia** **centrum**  ->  akcji przesyłania.

Wszystkie korygowania (zatwierdzenia bezpośrednie), które zostały utworzone w Eksploratorze lub Zaawansowane wyszukiwanie zagrożeń lub za pośrednictwem zautomatyzowanego badania są wyświetlane w Centrum akcji. Uzyskaj do nich dostęp za pośrednictwem panelu nawigacyjnego po lewej stronie w obszarze **Akcje** \> &**Karta Historia** **centrum**  ->  akcji przesyłania. 

Akcje ręczne oczekujące na zatwierdzenie przy użyciu dwuetapowego procesu zatwierdzania (1. dodaj do korygowania przez jednego członka zespołu operacji zabezpieczeń, 2. przeglądane i zatwierdzane przez innego członka zespołu operacji zabezpieczeń) są widoczne tylko w starszej Ochrona usługi Office 365 w usłudze Defender centrum akcji **Review** \> **Action Center**, a nie w zdarzeniach/badaniach i Centrum ujednoliconej akcji.

> [!NOTE]
> Zatwierdzanie dwuetapowe: akcje dostępne tylko w centrum akcji pakietu Office  **Review** \> **Action Center**

:::image type="content" source="../../media/microsoft-365-defender-action-center-history.png" alt-text="Ujednolicone Centrum akcji pokazuje 30 dni akcji korygowania.":::

Ujednolicone centrum akcji pokazuje akcje korygowania z ostatnich 30 dni. Akcje wykonywane za pośrednictwem Eksploratora są wyświetlane według nazwy, którą zespół ds. operacji zabezpieczeń podał podczas tworzenia korygowania, a także identyfikator zatwierdzenia, Identyfikator badania. Akcje wykonywane w ramach zautomatyzowanych badań mają tytuły rozpoczynające się od powiązanego alertu, który wyzwolił badanie, takiego jak *klaster poczty e-mail Zap*.

Otwórz dowolny element korygowania, aby wyświetlić szczegółowe informacje na jego temat, w tym jego nazwę korygowania, identyfikator zatwierdzenia, identyfikator badania, datę utworzenia, opis, stan, źródło akcji, typ akcji, o którym decyduje stan. Zostanie również otwarte okienko boczne ze szczegółami akcji, szczegółami klastra poczty e-mail, alertem i szczegółami zdarzenia.

- *Otwórz stronę Badanie* , aby otworzyć badanie administratora, które zawiera mniej szczegółów i kart. Wyświetlane są szczegółowe informacje, takie jak: alert pokrewny, jednostka wybrana do korygowania, podjęta akcja, stan korygowania, liczba jednostek, dzienniki, osoba zatwierdzająca akcję. To badanie śledzi badanie wykonywane ręcznie przez administratora i zawiera szczegółowe informacje dotyczące wyborów dokonanych przez administratora, dlatego jest nazywane badaniem akcji administratora. Nie ma potrzeby podejmowania działań w sprawie dochodzenia i powiadamiania o tym, że jest ono już w stanie zatwierdzonym.
- *Liczba wiadomości e-mail* Wyświetla liczbę wiadomości e-mail przesłanych za pośrednictwem Eksploratora zagrożeń. Te wiadomości e-mail mogą być możliwe do wykonania lub nie umożliwiają wykonania akcji.
- *Dzienniki akcji* Pokaż szczegóły stanu korygowania, takie jak pomyślne, zakończone niepowodzeniem i już w miejscu docelowym.

:::image type="content" source="../../media/microsoft-365-defender-action-center-history-panel.png" alt-text="Centrum akcji z otwartą opcją Przenieś do skrzynki odbiorczej.":::

  - **Możliwość wykonania akcji**: Wiadomości e-mail w następujących lokalizacjach skrzynek pocztowych w chmurze można wykonywać i przenosić:
    - Skrzynki odbiorczej
    - Śmieci
    - Usunięty folder
    - Folder usunięty nietrwale

      > [!NOTE]
      > Obecnie tylko użytkownik z dostępem do skrzynki pocztowej może odzyskać elementy z folderu usuniętego nietrwale.

  - **Nie można wykonać akcji**: Wiadomości e-mail w następujących lokalizacjach nie mogą być realizowane ani przenoszone w akcjach korygowania:
    - Kwarantanna
    - Folder o twardym usunięciu
    - Lokalnie/zewnętrznie
    - Niepowodzenie/upuszczenie

  Podejrzane komunikaty są kategoryzowane jako korygowanie lub niezobowiązujące. W większości przypadków komunikaty korygowania i niezobowiązywalne łączą się z łączną liczbą przesłanych komunikatów. Ale w rzadkich przypadkach może to nie być prawdą. Może się to zdarzyć z powodu opóźnień systemu, przekroczenia limitu czasu lub wygasłych komunikatów. Komunikaty wygasają na podstawie okresu przechowywania Eksploratora dla Organizacji.

  Jeśli nie korygujesz starych komunikatów po okresie przechowywania Eksploratora organizacji, zaleca się ponowienie próby skorygowania elementów, jeśli wystąpią niespójności liczbowe. W przypadku opóźnień systemu aktualizacje korygowania są zwykle odświeżane w ciągu kilku godzin.

  Jeśli okres przechowywania poczty e-mail w Eksploratorze w organizacji wynosi 30 dni, a korygujesz wiadomości e-mail w ciągu 29–30 dni, liczba przesłanych wiadomości e-mail nie zawsze może się sumować. Wiadomości e-mail mogły już zacząć się przenosić z okresu przechowywania.

  Jeśli korygowania są zablokowane w stanie "W toku" na chwilę, jest to prawdopodobnie spowodowane opóźnieniami systemu. Korygowanie może potrwać do kilku godzin. Mogą wystąpić zmiany liczby przesłanych wiadomości e-mail, ponieważ niektóre wiadomości e-mail mogły nie zostać dołączone do zapytania na początku korygowania z powodu opóźnień w systemie. Dobrym pomysłem jest ponowienie próby skorygowania w takich przypadkach.

  > [!NOTE]
  > Aby uzyskać najlepsze wyniki, korygowanie powinno odbywać się w partiach o wartości 50 000 lub mniejszej.

  Podczas korygowania działają tylko skorygowane wiadomości e-mail. Niezbywalne wiadomości e-mail nie mogą być korygowane przez Office 365 system poczty e-mail, ponieważ nie są one przechowywane w skrzynkach pocztowych w chmurze.

  Administratorzy mogą w razie potrzeby podejmować działania dotyczące wiadomości e-mail w kwarantannie, ale te wiadomości e-mail wygasną z kwarantanny, jeśli nie zostaną ręcznie wyczyszczone. Domyślnie wiadomości e-mail poddane kwarantannie z powodu złośliwej zawartości nie są dostępne dla użytkowników, więc pracownicy ochrony nie muszą podejmować żadnych działań, aby pozbyć się zagrożeń w kwarantannie. Jeśli wiadomości e-mail są lokalne lub zewnętrzne, można skontaktować się z użytkownikiem w celu wysłania podejrzanej wiadomości e-mail. Administratorzy mogą też użyć oddzielnych narzędzi do usuwania serwera poczty e-mail/zabezpieczeń. Te wiadomości e-mail można zidentyfikować, stosując *lokalizację dostarczania =* lokalny filtr zewnętrzny w Eksploratorze. W przypadku wiadomości e-mail zakończonych niepowodzeniem lub wiadomości e-mail, które nie są dostępne dla użytkowników, nie będzie żadnych wiadomości e-mail w celu ich ograniczenia, ponieważ te wiadomości nie docierają do skrzynki pocztowej.

 
- **Dzienniki akcji: pokazuje komunikaty** skorygowane, zakończone pomyślnie, zakończone niepowodzeniem, już w miejscu docelowym.

  Stan może być:

  - **Rozpoczęto**: wyzwalane jest korygowanie.
    - **W kolejce**: Korygowanie jest umieszczane w kolejce w celu ograniczenia ryzyka wiadomości e-mail.
    - **W toku**: Środki zaradcze są w toku.
    - **Ukończono**: Ograniczenie ryzyka dla wszystkich skorygowanych wiadomości e-mail zostało ukończone pomyślnie lub z pewnymi błędami.
    - **Niepowodzenie**: żadne korygowanie nie powiodło się.

  Ponieważ można wykonywać tylko naprawcze wiadomości e-mail, oczyszczanie każdej wiadomości e-mail jest wyświetlane jako pomyślne lub zakończone niepowodzeniem. Z łącznej liczby skorygowanych wiadomości e-mail są zgłaszane pomyślne i nieudane środki zaradcze.

  - **Powodzenie**: Żądana akcja dotycząca skorygowanych wiadomości e-mail została wykonana. Na przykład: administrator chce usunąć wiadomości e-mail ze skrzynek pocztowych, więc administrator podejmuje akcję usuwania nietrwałych wiadomości e-mail. Jeśli po wykonaniu akcji w oryginalnym folderze nie odnaleziono adresu e-mail korygowania, stan zostanie wyświetlony jako pomyślny.

  - **Niepowodzenie**: Żądana akcja dotycząca skorygowanych wiadomości e-mail nie powiodła się. Na przykład: administrator chce usunąć wiadomości e-mail ze skrzynek pocztowych, więc administrator podejmuje akcję usuwania nietrwałych wiadomości e-mail. Jeśli po wykonaniu akcji w skrzynce pocztowej nadal znajduje się adres e-mail korygowania, stan będzie wyświetlany jako zakończony niepowodzeniem.
  
  - **Już w miejscu docelowym**: żądana akcja została już podjęta w wiadomości e-mail LUB wiadomość e-mail już istniała w lokalizacji docelowej. Na przykład: wiadomość e-mail została usunięta nietrwale przez administratora za pośrednictwem Eksploratora pierwszego dnia. Następnie podobne wiadomości e-mail są wyświetlane w dniu 2, które są ponownie nietrwale usuwane przez administratora. Podczas wybierania tych wiadomości e-mail administrator odbiera wiadomości e-mail od pierwszego dnia, które zostały już usunięte nietrwale. Teraz te wiadomości e-mail nie zostaną ponownie podjęte, po prostu będą wyświetlane jako "już w miejscu docelowym", ponieważ nie podjęto żadnych działań na nich, ponieważ istniały w lokalizacji docelowej.

  - **Nowość**: w dzienniku akcji dodano kolumnę *Już w miejscu docelowym* . Ta funkcja używa najnowszej lokalizacji dostarczania w Eksploratorze zagrożeń do sygnalizowania, czy poczta została już skorygowana. *Już w miejscu docelowym* pomoże zespołom zabezpieczeń zrozumieć całkowitą liczbę komunikatów, które nadal wymagają rozwiązania.

Akcje można wykonywać tylko w przypadku komunikatów w folderach Skrzynka odbiorcza, Śmieci, Usunięte i Usunięte nietrwale w Eksploratorze zagrożeń. Oto przykład działania nowej kolumny. Akcja *usuwania nietrwałego* jest wykonywana w komunikacie znajdującym się w skrzynce odbiorczej, a następnie komunikat zostanie obsłużony zgodnie z zasadami. Następnym razem, gdy zostanie wykonane usuwanie nietrwałe, ten komunikat będzie wyświetlany w kolumnie "Już w miejscu docelowym", sygnalizując, że nie trzeba go ponownie rozwiązywać.

Wybierz dowolny element w dzienniku akcji, aby wyświetlić szczegóły korygowania. Jeśli szczegóły mówią "pomyślne" lub "nie znaleziono w skrzynce pocztowej", ten element został już usunięty ze skrzynki pocztowej. Czasami występuje błąd systemu podczas korygowania. W takich przypadkach warto ponowić próbę wykonania akcji korygowania.

W przypadku korygowania dużych partii wiadomości e-mail wyeksportuj wiadomości wysyłane do korygowania za pośrednictwem przesyłania poczty oraz wiadomości skorygowane za pośrednictwem dzienników akcji. Limit eksportu zostanie zwiększony do 100 000 rekordów.

 Administratorzy mogą podejmować akcje korygowania, takie jak przenoszenie wiadomości e-mail do folderu Wiadomości-śmieci, Skrzynka odbiorcza lub Usunięte elementy, oraz usuwać akcje, takie jak usuwanie nietrwałe lub twarde ze stron zaawansowanego wyszukiwania zagrożeń.

:::image type="content" source="../../media/microsoft-365-defender-advanced-hunting-actions-pane.png" alt-text="Panel Zaawansowane wyszukiwanie zagrożeń i akcji z wybranymi akcjami.":::

Korygowanie ogranicza zagrożenia, usuwa podejrzane wiadomości e-mail i pomaga zapewnić bezpieczeństwo organizacji.
