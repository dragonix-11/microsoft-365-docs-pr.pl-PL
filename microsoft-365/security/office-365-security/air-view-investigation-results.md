---
title: Wyświetlanie wyników zautomatyzowanego badania w Microsoft 365
keywords: AIR, autoIR, Ochrona punktu końcowego w usłudze Microsoft Defender, zautomatyzowane, badanie, korygowanie, akcje
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Podczas i po zautomatyzowanym badaniu w Microsoft 365 można wyświetlić wyniki i kluczowe wyniki.
ms.date: 01/29/2021
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6e3234168383a0dad6d8a9de3fb680b27b7ce6cb
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139700"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Szczegóły i wyniki zautomatyzowanego badania w Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)

W przypadku [zautomatyzowanego badania](office-365-air.md) w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) szczegółowe informacje o tym dochodzeniu są dostępne w trakcie i po zautomatyzowanym procesie badania. Jeśli masz niezbędne uprawnienia, możesz wyświetlić te szczegóły w portalu Microsoft 365 Defender. Szczegóły badania zapewniają aktualny stan i możliwość zatwierdzania wszelkich oczekujących akcji.

> [!TIP]
> Zapoznaj się z nową, ujednoliconą stroną badania w portalu Microsoft 365 Defender. Aby dowiedzieć się więcej, zobacz [(NOWY!) Ujednolicona strona badania](../defender/m365d-autoir-results.md#new-unified-investigation-page).

## <a name="investigation-status"></a>Stan badania

Stan badania wskazuje postęp analizy i akcji. Po uruchomieniu badania stan zmienia się, aby wskazać, czy wykryto zagrożenia i czy akcje zostały zatwierdzone.

|Stan|Opis|
|---|---|
|**Rozpoczynanie**|Badanie zostało wyzwolone i czeka na uruchomienie.|
|**Uruchomienie**|Proces dochodzeniowy rozpoczął się i jest w toku. Ten stan występuje również wtedy, gdy [oczekujące akcje](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) zostaną zatwierdzone.|
|**Nie znaleziono zagrożeń**|Badanie zostało zakończone i nie zidentyfikowano żadnych zagrożeń (konta użytkownika, wiadomości e-mail, adresu URL lub pliku). <p> **PORADA**: Jeśli podejrzewasz, że coś zostało pominięte (na przykład fałszywie ujemne), możesz podjąć działania za pomocą [Eksploratora zagrożeń](threat-explorer.md).|
|**Częściowo zbadane**|Zautomatyzowane badanie wykryło problemy, ale nie ma konkretnych akcji korygowania w celu rozwiązania tych problemów. <p> Stan **Częściowo zbadane** może wystąpić, gdy określono jakiś typ działania użytkownika, ale nie są dostępne żadne akcje oczyszczania. Przykłady obejmują dowolne z następujących działań użytkownika: <ul><li>Zdarzenie [zapobiegania utracie danych](../../compliance/dlp-learn-about-dlp.md)</li><li>Anomalia wysyłania wiadomości e-mail</li><li>Wysłane złośliwe oprogramowanie</li><li>Wysłane phish</li></ul> <p> **Uwaga**: ten **częściowo zbadany** stan był oznaczony jako **Znaleziono zagrożenia**. <p> W badaniu nie znaleziono złośliwych adresów URL, plików ani wiadomości e-mail do skorygowania i nie znaleziono działań skrzynki pocztowej do naprawienia, takich jak wyłączenie reguł przekazywania lub delegowanie. <p> **PORADA**: Jeśli podejrzewasz, że coś zostało pominięte (na przykład fałszywie ujemne), możesz zbadać i podjąć działania przy użyciu [Eksploratora zagrożeń](threat-explorer.md)|
|**Zakończone przez system**|Dochodzenie zostało zatrzymane. Dochodzenie można zatrzymać z kilku powodów: <ul><li>Oczekujące akcje badania wygasły. Limit czasu oczekujących akcji po oczekiwaniu na zatwierdzenie na tydzień</li><li>Istnieje zbyt wiele akcji. Jeśli na przykład zbyt wielu użytkowników klika złośliwe adresy URL, może przekroczyć możliwość uruchomienia wszystkich analizatorów przez badanie, więc badanie zostanie wstrzymane</li></ul> <p> **PORADA**: Jeśli badanie zostanie wstrzymane przed podjęciem akcji, spróbuj użyć [Eksploratora zagrożeń](threat-explorer.md) , aby znaleźć zagrożenia i rozwiązać je.|
|**Akcja oczekująca**|Badanie wykryło zagrożenie, takie jak złośliwa wiadomość e-mail, złośliwy adres URL lub ryzykowne ustawienie skrzynki pocztowej, oraz akcja korygowania tego zagrożenia [oczekuje na zatwierdzenie](air-review-approve-pending-completed-actions.md). <p> Stan **Oczekująca akcja** jest wyzwalany, gdy zostanie znalezione jakiekolwiek zagrożenie z odpowiednią akcją. Jednak lista oczekujących akcji może wzrosnąć w miarę uruchamiania badania. Wyświetl szczegóły badania, aby sprawdzić, czy inne elementy nadal oczekują na ukończenie.|
|**Skorygowano**|Dochodzenie zostało zakończone i wszystkie akcje korygowania zostały zatwierdzone (zanotowane jako w pełni skorygowane). <p> **UWAGA**: Zatwierdzone akcje korygowania mogą mieć błędy, które uniemożliwiają wykonanie akcji. Niezależnie od tego, czy akcje korygowania zostały pomyślnie zakończone, stan badania nie ulega zmianie. Wyświetl szczegóły badania.|
|**Częściowo skorygowane**|Badanie spowodowało akcje korygowania, a niektóre zostały zatwierdzone i zakończone. Inne akcje nadal [oczekują](air-review-approve-pending-completed-actions.md).|
|**Zakończone niepowodzeniem**|Co najmniej jeden analizator badania napotkał problem polegający na tym, że nie mógł prawidłowo ukończyć. <p> **UWAGA** Jeśli badanie zakończy się niepowodzeniem po zatwierdzeniu akcji korygowania, akcje korygowania mogły zakończyć się pomyślnie. Wyświetl szczegóły badania.|
|**W kolejce według ograniczania przepustowości**|Dochodzenie jest przechowywane w kolejce. Po zakończeniu innych badań rozpoczną się badania w kolejce. Ograniczanie przepustowości pomaga uniknąć niskiej wydajności usługi.  <p> **PORADA**: Oczekujące akcje mogą ograniczyć liczbę nowych badań. Pamiętaj, aby [zatwierdzić (lub odrzucić) oczekujące akcje](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions).|
|**Zakończone przez ograniczanie przepustowości**|Jeśli badanie jest przechowywane w kolejce zbyt długo, zatrzymuje się. <p> **PORADA**: Możesz [rozpocząć badanie z poziomu Eksploratora zagrożeń](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|

## <a name="view-details-of-an-investigation"></a>Wyświetlanie szczegółów badania

1. Przejdź do portalu Microsoft 365 Defender (<https://security.microsoft.com>) i zaloguj się.
2. W okienku nawigacji wybierz pozycję **Centrum akcji**.
3. Na kartach **Oczekujące** lub **Historia** wybierz akcję. Zostanie otwarte okienko wysuwane.
4. W okienku wysuwanym wybierz pozycję **Otwórz stronę badania**. 
5. Użyj różnych kart, aby dowiedzieć się więcej o badaniu.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Wyświetlanie szczegółów dotyczących alertu związanego z badaniem

Niektóre rodzaje alertów wyzwalają automatyczne badanie w Microsoft 365. Aby dowiedzieć się więcej, zobacz [zasady alertów, które wyzwalają zautomatyzowane badania](office-365-air.md#which-alert-policies-trigger-automated-investigations).

1. Przejdź do portalu Microsoft 365 Defender (<https://security.microsoft.com>) i zaloguj się.
2. W okienku nawigacji wybierz pozycję **Centrum akcji**.
3. Na kartach **Oczekujące** lub **Historia** wybierz akcję. Zostanie otwarte okienko wysuwane.
4. W okienku wysuwanym wybierz pozycję **Otwórz stronę badania**.
5. Wybierz kartę **Alerty** , aby wyświetlić listę wszystkich alertów skojarzonych z tym badaniem.
6. Wybierz element z listy, aby otworzyć okienko wysuwane. W tym miejscu możesz wyświetlić więcej informacji na temat alertu.

## <a name="keep-the-following-points-in-mind"></a>Należy pamiętać o następujących kwestiach

- Liczba wiadomości e-mail jest obliczana w czasie badania, a niektóre liczby są ponownie obliczane podczas otwierania wysuwanych badań (na podstawie zapytania bazowego).

- Liczba wiadomości e-mail wyświetlanych dla klastrów poczty e-mail na karcie **Poczta e-mail** i wartość ilości wiadomości e-mail wyświetlana w wysuwie klastra są obliczane w czasie badania i nie ulegają zmianie.

- Liczba wiadomości e-mail wyświetlanych w dolnej części karty **Poczta e-mail** wysuwanego klastra poczty e-mail oraz liczba wiadomości e-mail wyświetlanych w Eksploratorze odzwierciedlają wiadomości e-mail odebrane po wstępnej analizie badania.

  W związku z tym klaster poczty e-mail, który pokazuje oryginalną ilość 10 wiadomości e-mail, pokazuje listę wiadomości e-mail łącznie 15, gdy pojawi się jeszcze pięć wiadomości e-mail między fazą analizy badania a przeglądem badania przez administratora. Podobnie stare badania mogą zacząć pokazywać większą liczbę niż pokazują zapytania Eksploratora, ponieważ dane w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2 wygasają po siedmiu dniach prób i po 30 dniach dla płatnych licencji.

  Wyświetlanie zarówno liczby historycznych, jak i bieżących liczb w różnych widokach jest wykonywane w celu wskazania wpływu wiadomości e-mail w czasie badania i bieżącego wpływu aż do czasu uruchomienia korygowania.

- W kontekście wiadomości e-mail w ramach badania może zostać wyświetlona powierzchnia zagrożenia anomalią woluminu. Anomalia woluminu wskazuje na wzrost liczby podobnych wiadomości e-mail w czasie zdarzenia badania w porównaniu do wcześniejszych ram czasowych. Wzrost ruchu poczty e-mail wraz z pewnymi cechami (na przykład domeną podmiotu i nadawcy, podobieństwem treści i adresem IP nadawcy) jest typowym początkiem kampanii e-mail lub ataków. Jednak zbiorcze, spamowe i uzasadnione kampanie e-mail często mają te cechy.

- Anomalie woluminów stanowią potencjalne zagrożenie i w związku z tym mogą być mniej poważne w porównaniu do złośliwego oprogramowania lub zagrożeń phish, które są identyfikowane przy użyciu aparatów antywirusowych, detonacji lub złośliwej reputacji.

- Nie musisz zatwierdzać każdej akcji. Jeśli nie zgadzasz się z zalecaną akcją lub twoja organizacja nie wybiera niektórych typów akcji, możesz wybrać opcję **Odrzuć** akcje lub po prostu je zignorować i nie podejmować żadnych działań.

- Zatwierdzenie i/lub odrzucenie wszystkich akcji pozwala na całkowite zamknięcie badania (stan staje się korygowany), a pozostawienie niektórych akcji niekompletnych powoduje zmianę stanu badania na częściowo skorygowany stan.

## <a name="next-steps"></a>Następne kroki

- [Przeglądanie i zatwierdzanie oczekujących akcji](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
