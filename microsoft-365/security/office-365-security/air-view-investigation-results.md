---
title: Wyświetlanie wyników automatycznego badania w programie Microsoft 365
keywords: AIR, autoIR, Microsoft Defender for Endpoint, automated, investigation, remediation, actions
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
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
description: W trakcie automatycznego badania Microsoft 365 i po jego zakończeniu możesz wyświetlić wyniki i najważniejsze wyniki.
ms.date: 01/29/2021
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 80c58c0e4c084199537dcfbb9097541a0cba71a0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984958"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Szczegóły i wyniki automatycznego badania Microsoft 365

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Gdy w [programie](office-365-air.md) [Microsoft Defender for Office 365](defender-for-office-365.md) odbywa się zautomatyzowane badanie, dostępne są szczegółowe informacje dotyczące tego badania w trakcie i po nim. Jeśli masz odpowiednie uprawnienia, możesz wyświetlić te szczegóły w portalu Microsoft 365 Defender portal. Szczegóły badania zapewniają aktualny stan oraz możliwość zatwierdzania wszystkich oczekujących akcji.

> [!TIP]
> Zapoznaj się z nową, ujednoliconą stroną badania w portalu Microsoft 365 Defender użytkowników. Aby dowiedzieć się więcej, zobacz [(NOWY!) Ujednolicona strona badania](../defender/m365d-autoir-results.md#new-unified-investigation-page).

## <a name="investigation-status"></a>Stan badania

Stan badania wskazuje postęp analizy i akcji. Po prowadzonym śledztwie stan zmienia się w celu wskazania, czy znaleziono zagrożenia i czy zatwierdzono działania.

<br>

****

|Stan|Opis|
|---|---|
|**Rozpoczynanie**|Badanie zostało wyzwolone i może rozpocząć się uruchamianie.|
|**Uruchomione**|Proces badania rozpoczął się i jest w toku. Ten stan występuje również w przypadku [zatwierdzenia oczekujących](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) akcji.|
|**Nie znaleziono zagrożeń**|Badanie zakończyło się i nie zostały zidentyfikowane żadne zagrożenia (konto użytkownika, wiadomość e-mail, adres URL lub plik). <p> **PORADA**: Jeśli podejrzewasz, że coś zostało nieodebrane (na przykład fałszywie ujemne), możesz podjąć działania przy użyciu [Eksploratora zagrożeń](threat-explorer.md).|
|**Znalezione zagrożenia**|Zautomatyzowane badanie znaleziono problemy, ale nie ma konkretnych działań naprawczych w celu ich rozwiązania. <p> Stan **Znaleziono zagrożenia** może występować, gdy zidentyfikowano jakiś typ aktywności użytkownika, ale nie są dostępne żadne akcje oczyszczania. Przykłady obejmują dowolne z następujących działań użytkownika: <ul><li>Zdarzenie [ochrony przed utratą](../../compliance/dlp-learn-about-dlp.md) danych</li><li>Anomaly w wiadomości e-mail</li><li>Wysłane złośliwe oprogramowanie</li><li>Wysłane wiadomości wyłudzy</li></ul> <p> W śledztwie nie znaleziono złośliwych adresów URL, plików ani wiadomości e-mail do rozwiązania ani nie usunięto działań dotyczących skrzynki pocztowej, takich jak wyłączenie reguł przesyłania dalej lub delegowania. <p> **PORADA**: Jeśli podejrzewasz, że coś zostało nieodebrane (na przykład wynik fałszywie ujemny), możesz go zbadać i podjąć działania przy użyciu [Eksploratora zagrożeń](threat-explorer.md)|
|**Zakończone przez system**|Badanie zostało zatrzymane. Badanie może zostać zatrzymane z kilku powodów: <ul><li>Oczekujące działania badania wygasły. Oczekiwanie na czekanie na zatwierdzenie przez tydzień</li><li>Jest zbyt wiele akcji. Jeśli na przykład jest zbyt wielu użytkowników klikających złośliwe adresy URL, może to przekroczyć możliwość uruchomienia wszystkich analizatorów w celu zatrzymania badania</li></ul> <p> **PORADA**: Jeśli śledztwo zostanie zatrzymane przed podjęciem akcji, spróbuj użyć Eksploratora zagrożeń [, aby znaleźć](threat-explorer.md) zagrożenia i rozwiązać je.|
|**Oczekiwanie na akcję**|W ramach badania znaleziono zagrożenie, takie jak złośliwa wiadomość e-mail, złośliwy adres URL lub ustawienie ryzykownych skrzynek pocztowych, oraz akcja mająca na celu naprawienie tego zagrożenia, które oczekuje [na zatwierdzenie](air-review-approve-pending-completed-actions.md). <p> Stan **Akcji oczekującej** jest wyzwalany w przypadku, gdy zostanie znalezione zagrożenie, w którym znajduje się odpowiednia akcja. Jednak lista oczekujących akcji może rosnąć w trakcie prowadzenia badania. Wyświetl szczegóły badania, aby sprawdzić, czy inne elementy nadal oczekują na ukończenie.|
|**Działania naprawcze**|Po zakończeniu badania i wszystkich działań naprawczych zostały zatwierdzone (zaznaczono, że zostały one w pełni rozwiązane). <p> **UWAGA**: Zatwierdzone działania naprawcze mogą mieć błędy uniemożliwiające ich akcje. Stan badania nie zmienia się bez względu na to, czy działania naprawcze zostały zakończone pomyślnie. Wyświetl szczegóły badania.|
|**Częściowo naprawiony**|Badanie zakończyło się działaniami naprawczymi, a niektóre zostały zatwierdzone i ukończone. Inne akcje nadal oczekują[.](air-review-approve-pending-completed-actions.md)|
|**Zakończone niepowodzeniem**|Co najmniej jeden analizator analizy mógł mieć problem, który nie mógł zostać poprawnie ukończony. <p> **UWAGA** Jeśli po zatwierdzeniu działań naprawczych nie powiedzie się badanie, działania naprawcze nadal mogą się powieść. Wyświetl szczegóły badania.|
|**W kolejce przez ograniczanie**|Trwa badanie w kolejce. Po zakończeniu innych badań rozpoczyna się w kolejce. Ograniczanie pozwala uniknąć niskiej wydajności usługi.  <p> **PORADA**: Oczekujące akcje mogą ograniczyć liczbę nowych czynności do uruchomienia. Pamiętaj, aby [zatwierdzić (lub odrzucić) oczekujące akcje](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions).|
|**Zakończone przez ograniczanie**|Jeśli badanie jest przechowywane w kolejce zbyt długo, jest ono zatrzymane. <p> **PORADA**: Możesz [rozpocząć badanie z eksploratora zagrożeń](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|
|

## <a name="view-details-of-an-investigation"></a>Wyświetlanie szczegółów badania

1. Przejdź do Microsoft 365 Defender konta (<https://security.microsoft.com>) i zaloguj się.
2. W okienku nawigacji wybierz pozycję **Centrum akcji**.
3. Wybierz **akcję** na **karcie Oczekujące** lub Historia. Zostanie otwarte okienko wysuwu.
4. W wysuwanych okienkach wybierz pozycję **Otwórz stronę badania**. 
5. Korzystaj z różnych kart, aby dowiedzieć się więcej o śledztwie.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Wyświetlanie szczegółów alertu związanego z badaniem

Niektóre typy alertów powodują automatyczne badanie Microsoft 365. Aby dowiedzieć się więcej, zobacz [zasady alertów wyzwalace automatyczne badania](office-365-air.md#which-alert-policies-trigger-automated-investigations).

1. Przejdź do Microsoft 365 Defender konta (<https://security.microsoft.com>) i zaloguj się.
2. W okienku nawigacji wybierz pozycję **Centrum akcji**.
3. Wybierz **akcję** na **karcie Oczekujące** lub Historia. Zostanie otwarte okienko wysuwu.
4. W wysuwanych okienkach wybierz pozycję **Otwórz stronę badania**.
5. Wybierz **kartę Alerty** , aby wyświetlić listę wszystkich alertów skojarzonych z tym badaniem.
6. Zaznacz element na liście, aby otworzyć jego okienko wysuwu. Tam możesz wyświetlić więcej informacji na temat alertu.

## <a name="keep-the-following-points-in-mind"></a>Należy pamiętać o następujących kwestiach

- Liczby wiadomości e-mail są obliczane w czasie badania, a niektóre z nich są ponownie obliczane po otwarciu wysuwu badania (na podstawie zapytania źródłowego).

- Liczby wiadomości e-mail wyświetlane dla grup poczty e-mail  na karcie Poczta e-mail oraz wartość liczby wiadomości e-mail wyświetlana w wysuwanych wiadomościach grupowych są obliczane w czasie badania i nie zmieniają się.

- Liczba wiadomości e-mail wyświetlana u dołu  karty Poczta e-mail w wysuwanej grupie wiadomości e-mail oraz liczba wiadomości e-mail wyświetlanych w Eksploratorze odzwierciedla wiadomości e-mail odebrane po początkowej analizie badania.

  Z tego względu klaster poczty e-mail, w którym jest pokazywana oryginalna liczba 10 wiadomości e-mail, będzie zawierał łącznie 15 wiadomości e-mail, gdy między fazą analizy badania a przeglądem badania przez administratora nadejść więcej niż pięć wiadomości e-mail. Podobnie stare badania mogą zacząć pokazywać większą liczbę danych niż w przypadku zapytań w Eksploratorze, ponieważ dane w programie Microsoft Defender dla systemu Office 365 Plan 2 wygasają po siedmiu dniach dla wersji próbnych i po 30 dniach dla płatnych licencji.

  Pokazywanie zarówno licznika historycznego, jak i bieżącego licznika w różnych widokach jest wykonywane w celu wskazania wpływu wiadomości e-mail w czasie badania i bieżącego wpływu aż do czasu uruchomienia działania naprawczego.

- W kontekście wiadomości e-mail w ramach badania może zostać wyświetlony poziom zagrożenia anomaly. Anomaly głośności oznacza kolekcję podobnych wiadomości e-mail w czasie zdarzenia badania w porównaniu z wcześniejszymi okresami. Kolekcję ruchu poczty e-mail wraz z określonymi cechami (na przykład domeną tematu i nadawcy, podobieństwem do treści oraz adresem IP nadawcy) jest typowy początek kampanii lub ataków e-mail. Jednak zbiorcze, spam i legalne kampanie e-mail mają często te cechy.

- Anomalie oznaczają potencjalne zagrożenie, a zatem mogą być mniej poważne w porównaniu z złośliwym oprogramowaniem lub wyłudzeniami, które zidentyfikowano przy użyciu aparatów antywirusowych, detonacji lub złośliwej reputacji.

- Nie trzeba zatwierdzać wszystkich działań. Jeśli nie zgadzasz się z zalecaną akcją lub Twoja organizacja nie wybiera niektórych typów akcji, możesz wybrać opcję Odrzuć akcje lub po prostu je zignorować i nie podjąć żadnych działań.

- Zatwierdzanie i/lub odrzucanie wszystkich akcji umożliwia pełne zamknięcie badania (działania naprawcze mogą zostać rozwiązane), natomiast niektóre akcje są niepełne, a stan badania zmienia się na częściowo zaradczy.

## <a name="next-steps"></a>Następne kroki

- [Przeglądanie i zatwierdzanie oczekujących akcji](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
