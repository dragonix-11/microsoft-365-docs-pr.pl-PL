---
title: Stos ochrony przed zagrożeniami krok po kroku w programie Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
ms.reviewer: gigarrub
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
description: Postępuj zgodnie ze ścieżką wiadomości przychodzącej w stosie filtrowania zagrożeń w Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e7be5c66e0ca3841a8bc4fd76555feaeafb1bd17
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469036"
---
# <a name="step-by-step-threat-protection-in-microsoft-defender-for-office-365"></a>Ochrona przed zagrożeniami krok po kroku w programie Ochrona usługi Office 365 w usłudze Microsoft Defender

Sposób Ochrona usługi Office 365 w usłudze Microsoft Defender ochrony lub filtrowania można podzielić na 4 fazy, tak jak w tym artykule. Ogólnie rzecz biorąc, wiadomości przychodzące przechodzą przez wszystkie te etapy przed dostarczeniem, ale rzeczywista ścieżka wiadomości e-mail zależy od konfiguracji Ochrona usługi Office 365 w usłudze Defender organizacji.

> [!TIP]
> Bądź na bieżąco do końca tego artykułu *, aby uzyskać* ujednoliconą grafikę ze wszystkich 4 faz Ochrona usługi Office 365 w usłudze Defender ochrony!

## <a name="phase-1---edge-protection"></a>Faza 1 — Ochrona krawędzi

Niestety, bloki programu Edge, które kiedyś  miały krytyczne znaczenie, są teraz stosunkowo proste do rozwiązania przez złe 8 8 800 bloków. Z czasem ruch będzie blokowany w tym miejscu, ale nadal stanowi istotny element stosu.  

Bloki edge są zaprojektowane tak, aby zostały automatycznie. W przypadku wyników fałszywie dodatnich nadawcy zostaną powiadomieni i powiadomieni o tym, jak rozwiązać swój problem. Łączniki od zaufanych partnerów o ograniczonej reputacji mogą zapewnić zapewnianie dostawy lub tymczasowe zastępowanie można wprowadzić podczas dołączania nowych punktów końcowych.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png" alt-text="Filtrowanie faz 1 w programie Ochrona usługi Office 365 w usłudze Defender" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png":::

1. **Ograniczanie sieci** chroni Office 365 i klientów przed atakami typu "odmowa usługi" (DOS, Denial of Service) przez ograniczenie liczby wiadomości, które mogą być przesyłane przez określony zestaw infrastruktury.

2. **Reputacja i ograniczanie adresów IP** zablokuje możliwość wysłania wiadomości ze znanych, źle połączonych adresów IP. Jeśli określony adres IP wyśle wiele wiadomości w krótkim czasie, zostaną one ograniczone.

3. **Reputacja domeny** blokuje wszystkie wiadomości wysyłane z znanej złej domeny.

4. **Filtrowanie brzegowe oparte na katalogu** blokuje próby zbierania informacji katalogowych organizacji za pomocą protokołu SMTP.

5. **Wykrywanie typu backscatter zapobiega** atakom organizacji za pośrednictwem nieprawidłowych raportów o niedo dostarczenia.

6. **Ulepszone filtrowanie łączników** zachowuje informacje o uwierzytelnianiu nawet wtedy, gdy ruch przechodzi przez inne urządzenie, zanim dotrze do Office 365. Zwiększa to dokładność filtrowania stosów, w tym heuristic clustering, anti-spoofing i modele uczenia maszynowego ochrony przed wyłudzaniem informacji, nawet w złożonych lub hybrydowych scenariuszach routingu.

## <a name="phase-2---sender-intelligence"></a>Etap 2. Analizy nadawców

Funkcje analizy nadawców są niezbędne do wychwytywania spamu, zbiorczego, personifikacji i nieautoryzowanych wiadomości spoofof, a także do wykrywania wyłudzeń informacji. Większość tych funkcji można konfigurować osobno.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png" alt-text="Etap 2 filtrowania w programie Ochrona usługi Office 365 w usłudze Defender to Inteligencja nadawców" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png":::

1. **Wyzwalacze wykrywania** naruszenia zabezpieczeń konta i alerty są wywoływane, gdy konto ma anomalne zachowanie, zgodne z naruszoniem. W niektórych przypadkach konto użytkownika jest zablokowane i nie może wysyłać kolejnych wiadomości e-mail, dopóki nie zostanie rozwiązany przez zespół operacyjny zabezpieczeń organizacji.

2. **Uwierzytelnianie poczty** e-mail obejmuje zarówno metody skonfigurowane przez klienta, jak i metody skonfigurowane w chmurze, których celem jest upewnienie się, że nadawcy są autoryzowani, autentyczni nadawcy. Te metody opierają się na spoofingu.
    - **Rekord SPF** może odrzucać wiadomości na podstawie rekordów DNS TXT, które listują adresy IP i serwery, które mogą wysyłać pocztę w imieniu organizacji.
    - **DKIM** udostępnia zaszyfrowany podpis uwierzytelniacy nadawcę.
    - **Funkcja DMARC** umożliwia administratorom oznaczanie spf i DKIM jako wymaganego w domenie oraz wymusza wyrównywanie wyników tych dwóch technologii.
    - **Usługa ARC** nie jest skonfigurowana przez klienta, ale jest kompilowana na funkcji DMARC w celu pracy z przesyłaniem dalej na listach wysyłkowych podczas rejestrowania łańcucha uwierzytelniania.

3.  Sfałszowana inteligencja umożliwia filtrowanie osób, którym wolno podszyć się (czyli osobom wysyłającym pocztę w imieniu innego konta lub przesyłać dalej wiadomości na listę adresową) przed złośliwymi nadawcami, którzy imitują dane organizacji lub znane domeny zewnętrzne. Oddziela on legalną pocztę "w imieniu" od nadawców, którzy podszywają się pod nadawców, którzy podszywają się pod spam i wiadomości wyłudzają informacje.

    **Spoof intelligence wewnątrz organizacji** wykrywa i blokuje próby spoof przez domenę w organizacji.

4. **Funkcje analizy fałszowania** między domenami wykrywają i blokowały próby spoofofs z domeny spoza organizacji.

5. **Filtrowanie zbiorcze umożliwia** administratorom skonfigurowanie poziomu ufności zbiorczej wskazującego, czy wiadomość została wysłana od nadawcy zbiorczego. Administratorzy mogą używać suwaka zbiorczego w zasadach ochrony przed spamem, aby określić, jaki poziom poczty masowej należy traktować jako spam.

6. **Funkcje analizy skrzynek** pocztowych uczy się na temat standardowych zachowań poczty e-mail użytkowników. Korzysta on z wykresu komunikacji użytkownika do wykrywania, gdy nadawca wygląda na kogoś, z którym zwykle się komunikuje, ale w rzeczywistości jest złośliwy. Ta metoda wykrywa personifikację.

7. **Personifikacja skrzynki pocztowej** włącza lub wyłącza rozszerzone wyniki personifikacji na podstawie mapy poszczególnych nadawców poszczególnych użytkowników. Po włączeniu ta funkcja ułatwia identyfikowanie personifikacji.

8. **Personifikacja użytkownika** umożliwia administratorowi utworzenie listy celów o wysokiej wartości, które mogą zostać personifikowane. Jeśli dotrze do nas wiadomość e-mail, na której nadawca wygląda tak samo jak chronione konto o wysokiej wartości, jest ona oznaczana lub otagowana. (Na przykład *trα cye@contoso.com* dla *tracye@contoso.com*).

9. **Personifikacja domeny** wykrywa domeny, które są podobne do domeny adresata, i ta próba wygląda jak domena wewnętrzna. Na przykład ta personifikacja *tracye@liw α re.com* *dla tracye@litware.com*.

## <a name="phase-3---content-filtering"></a>Etap 3. Filtrowanie zawartości

W tej fazie stos filtrowania zacznie obsługiwać konkretną zawartość wiadomości, w tym jej hiperlinki i załączniki.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png" alt-text="Filtrowanie faz 3 w mdo to filtrowanie zawartości" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png":::

1. **Reguły transportu** (nazywane także regułami przepływu poczty e-mail Exchange regułami transportu) umożliwiają administratorowi szeroki zakres działań w przypadku, gdy dla wiadomości jest spełniony tak samo szeroki zakres warunków. Wszystkie wiadomości, które przepływają przez Twoją organizację, są oceniane pod względem włączonych reguł przepływu poczty/reguł transportu.

2. **Program antywirusowy Microsoft Defender** załącznikach są wykrywane  wszystkie znane złośliwe oprogramowanie za pomocą dwóch aparatów antywirusowych innych firm.

3. Aparaty antywirusowe są również używane do oznaczania wszystkich załączników jako prawda, dzięki czemu blokowanie typu może  blokować wszystkie załączniki typów określonych przez administratora.

4. Gdy Ochrona usługi Office 365 w usłudze Microsoft Defender złośliwy załącznik, do reputacji usługi Exchange Online Protection (EOP) jest dodawany skrót pliku i skrót jego zawartości aktywnej. **Blokowanie reputacji załączników** blokuje ten plik we wszystkich Office 365 i na punktach końcowych, za pośrednictwem połączeń w chmurze MSAV.

5. **Grupowanie heuristyczne pozwala** stwierdzić, że plik jest podejrzany na podstawie heuristicsów dostarczania. W przypadku wykrycia podejrzanego załącznika cała kampania zostanie wstrzymana i plik zostanie w trybie piaskownicy. Jeśli plik zostanie znaleziony jako złośliwy, cała kampania zostanie zablokowana.

6. **Modele uczenia maszynowego** działają na nagłówku, treści i adresach URL wiadomości w celu wykrywania prób wyłudzania informacji.

7. Firma Microsoft używa wyznaczania reputacji z trybu piaskownicy url oraz reputacji adresu URL z kanałów informacyjnych innych firm w blokowania reputacji **adresu URL**, aby blokować wszystkie wiadomości przy użyciu znanego złośliwego adresu URL.

8. **Heuristics zawartości mogą** wykrywać podejrzane wiadomości na podstawie struktury i częstotliwości wyrazów w treści wiadomości przy użyciu modeli uczenia maszynowego.

9. **Sejf w trybie** piaskownicy załączniki są Ochrona usługi Office 365 w usłudze Defender dla klientów korzystających z analizy dynamicznej w celu wykrywania nigdy wcześniej widocznych zagrożeń.

10. **Detonacja połączonej** zawartości traktuje każdy adres URL, który zawiera link do pliku w wiadomości e-mail, jako załącznik, asynchronicznie w trybie piaskownicy w czasie dostarczania.

11. **Detonacja adresu URL** jest dzieje, gdy upstream anti-phishing technology znajduje wiadomość lub adres URL jako podejrzany. Detonacja adresu URL detonuje adresy URL w wiadomości w momencie dostarczania.

## <a name="phase-4---post-delivery-protection"></a>Etap 4. Ochrona po dostarczeniu

Ostatni etap odbywa się po dostarczeniu poczty lub pliku, czyli w przypadku poczty z różnych skrzynek pocztowych, plików i linków wyświetlanych w klientach, takich jak Microsoft Teams.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png" alt-text="Filtrowanie faz 4 w programie Ochrona usługi Office 365 w usłudze Defender jest ochrona po dostarczeniu" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png":::

1. **Sejf linki** Ochrona usługi Office 365 w usłudze Defender czasu kliknięcia. Każdy adres URL w każdej wiadomości jest zawijany w celu wskazania serwerów usługi Microsoft Sejf Links. Po kliknięciu adresu URL jest on sprawdzany pod kątem najnowszej reputacji, zanim użytkownik zostanie przekierowany do witryny docelowej. Adres URL jest asynchronicznie w trybie piaskownicy w celu zaktualizowania jego reputacji.

2. **Automatyczne przeczyszczanie** zerowej godziny w celu wyłudzania informacji wykrywa i wykrywa złośliwe wiadomości służące do wyłudzania informacji, które już zostały dostarczone do Exchange Online pocztowych.

3. **Zap dla złośliwego** oprogramowania wykrywa i wykrywa i wykrywa złośliwe złośliwe oprogramowanie, które już dostarczono do Exchange Online skrzynkach pocztowych.

4. **Zap dla spamu**, który wykrywa i wykrywa złośliwe wiadomości,które już zostały dostarczone do Exchange Online pocztowych.

5. **Widoki kampanii** pozwalają administratorom lepiej widzieć atak szybciej i bardziej całkowicie, niż jakikolwiek zespół mógł bez automatyzacji. Firma Microsoft wykorzystuje ogromną ilość danych chroniących przed wyłudzaniem informacji, spamem i złośliwym oprogramowaniem w całej usłudze, aby ułatwić identyfikowanie kampanii, a następnie umożliwia administratorom od początku do końca ich badanie, w tym cele, skutki i przepływy, które są również dostępne w ramach pisania kampanii do pobrania.

6. Dodatki do wiadomości raportów umożliwiają firmie Microsoft łatwe zgłaszanie wyników fałszywie dodatnich (dobra wiadomość **e-mail**, błędnie oznaczonych jako *złe) lub* ujemnych (oznaczanych jako *złe) do* firmy Microsoft w celu dalszej analizy.

7. **Sejf** Linki dla klientów usługi Office oferują tę samą ochronę po kliknięciu linków usługi Sejf natywnie wewnątrz klientów usługi Office, takich jak word, PowerPoint i Excel.

8. **Ochrona dla OneDrive,** SharePoint i Teams zapewnia tę samą ochronę załączników Sejf przed złośliwymi plikami, natywnie, wewnątrz witryn OneDrive, SharePoint i Microsoft Teams.

9. Gdy adres URL, który wskazuje plik, jest wybrany po dostarczeniu, **detonacja** połączonej zawartości wyświetla stronę z ostrzeżeniem do momentu ukończenia trybu piaskownicy pliku i gdy adres URL zostanie odnaleziony jako bezpieczny.

## <a name="the-filtering-stack-diagram"></a>Diagram stosu filtrowania

Końcowy diagram (tak jak wszystkie części diagramu redagowania go) może ulec zmianie w miarę rozwoju *i rozwoju produktu*. Dodaj zakładkę do tej strony  i użyj opcji opinii, która jest dostępna u dołu, jeśli chcesz poprosić o aktualizacje po aktualizacji. W przypadku rekordów jest to stos ze wszystkimi fazami w kolejności:

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png" alt-text="Wszystkie fazy filtrowania w Ochrona usługi Office 365 w usłudze Defender kolejności, od 1 do 4" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png":::

## <a name="more-information"></a>Więcej informacji

Czy musisz teraz skonfigurować Ochrona usługi Office 365 w usłudze Microsoft Defender ***?** Użyj tego stosu, _now*, z [tym](protect-against-threats.md) krokiem krok po kroku w celu rozpoczęcia ochrony organizacji.

*Specjalnie dziękujemy zespołowi MSFTTracyP i zespołowi piszącemu dokumenty do Giudora Garruba za tę zawartość*.
