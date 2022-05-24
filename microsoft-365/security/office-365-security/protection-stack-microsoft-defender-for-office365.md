---
title: Stos ochrony przed zagrożeniami krok po kroku w Ochrona usługi Office 365 w usłudze Microsoft Defender
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
description: Postępuj zgodnie ze ścieżką komunikatu przychodzącego za pośrednictwem stosu filtrowania zagrożeń w Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 4548beaf8d3071006114a65fd95c16b06e8a875d
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648178"
---
# <a name="step-by-step-threat-protection-in-microsoft-defender-for-office-365"></a>Krok po kroku ochrona przed zagrożeniami w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy:**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Stos ochrony Ochrona usługi Office 365 w usłudze Microsoft Defender lub filtrowania można podzielić na 4 fazy, jak w tym artykule. Ogólnie rzecz biorąc, poczta przychodząca przechodzi przez wszystkie te fazy przed dostarczeniem, ale rzeczywista ścieżka, którą przyjmuje wiadomość e-mail, podlega konfiguracji Ochrona usługi Office 365 w usłudze Defender organizacji.

> [!TIP]
> Bądź na bieżąco do końca tego artykułu, aby uzyskać *ujednoliconą* grafikę ze wszystkimi 4 fazami ochrony Ochrona usługi Office 365 w usłudze Defender!

## <a name="phase-1---edge-protection"></a>Faza 1 — ochrona krawędzi

Niestety, bloki krawędzi, które kiedyś były *krytyczne* , są teraz stosunkowo proste do pokonania dla złych aktorów. Z biegiem czasu mniejszy ruch jest blokowany, ale pozostaje ważną częścią stosu.  

Bloki krawędzi są zaprojektowane tak, aby były automatyczne. W przypadku fałszywie dodatniego wyniku nadawcy zostaną powiadomieni i poinformowani, jak rozwiązać swój problem. Łączniki od zaufanych partnerów o ograniczonej reputacji mogą zapewnić możliwość dostarczania lub tymczasowe przesłonięcia podczas dołączania nowych punktów końcowych.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png" alt-text="Filtrowanie fazy 1 w Ochrona usługi Office 365 w usłudze Defender" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png":::

1. **Ograniczanie przepustowości sieci** chroni infrastrukturę Office 365 i klientów przed atakami typu "odmowa usługi" (DOS), ograniczając liczbę komunikatów, które mogą być przesyłane przez określony zestaw infrastruktury.

2. **Reputacja adresów IP i ograniczanie przepustowości** zablokują wysyłanie komunikatów ze znanych nieprawidłowych adresów IP. Jeśli określony adres IP wyśle wiele komunikatów w krótkim czasie, zostaną one ograniczone.

3. **Reputacja domeny** zablokuje wysyłanie komunikatów ze znanej złej domeny.

4. **Bloki filtrowania krawędzi oparte na katalogach** próbują zbierać informacje o katalogu organizacji za pośrednictwem protokołu SMTP.

5. **Wykrywanie backscatter** zapobiega atakom organizacji za pośrednictwem nieprawidłowych raportów o braku dostarczania (NDR).

6. **Ulepszone filtrowanie łączników** zachowuje informacje o uwierzytelnianiu nawet wtedy, gdy ruch przechodzi przez inne urządzenie, zanim dotrze do Office 365. Poprawia to dokładność stosu filtrowania, w tym klastrowanie heurystyczne, modele uczenia maszynowego chroniącego przed fałszowaniem i wyłudzaniem informacji, nawet w przypadku złożonych lub hybrydowych scenariuszy routingu.

## <a name="phase-2---sender-intelligence"></a>Faza 2 — analiza nadawcy

Funkcje analizy nadawców mają kluczowe znaczenie dla wykrywania spamu, zbiorczego, personifikacji i nieautoryzowanego fałszowania wiadomości, a także uwzględniają wykrywanie phish. Większość z tych funkcji można konfigurować indywidualnie.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png" alt-text="Faza 2 filtrowania w Ochrona usługi Office 365 w usłudze Defender to analiza nadawcy" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png":::

1. Wyzwalacze i alerty **wykrywania naruszenia zabezpieczeń konta** są zgłaszane, gdy konto ma nietypowe zachowanie, spójne z naruszeniem zabezpieczeń. W niektórych przypadkach konto użytkownika jest zablokowane i nie może wysyłać żadnych dalszych wiadomości e-mail, dopóki problem nie zostanie rozwiązany przez zespół ds. operacji zabezpieczeń organizacji.

2. **Uwierzytelnianie poczty e-mail** obejmuje zarówno metody skonfigurowane przez klienta, jak i metody skonfigurowane w chmurze, mające na celu zapewnienie, że nadawcy są autoryzowanymi, autentycznymi nadawcami. Metody te opierają się fałszowaniu.
    - **SPF** może odrzucać wiadomości e-mail na podstawie rekordów TXT DNS, które wyświetlają listę adresów IP i serwerów, które mogą wysyłać wiadomości e-mail w imieniu organizacji.
    - **Program DKIM** udostępnia zaszyfrowany podpis, który uwierzytelnia nadawcę.
    - **Funkcja DMARC** umożliwia administratorom oznaczanie SPF i DKIM jako wymaganych w ich domenie i wymusza wyrównanie wyników tych dwóch technologii.
    - **Usługa ARC** nie jest skonfigurowana przez klienta, ale bazuje na narzędziu DMARC do pracy z przekazywaniem na listach wysyłkowych podczas rejestrowania łańcucha uwierzytelniania.

3. **Analiza fałszowania** umożliwia filtrowanie osób, które mogą "podszywać się" (czyli osób wysyłających pocztę w imieniu innego konta lub przekazujących listę adresową) od złośliwych nadawców, którzy imitują domeny organizacyjne lub znane domeny zewnętrzne. Oddziela ona legalną pocztę "w imieniu" od nadawców, którzy podszywają się pod nadawców w celu dostarczania wiadomości spamu i wyłudzania informacji.

    **Analiza fałszowania wewnątrz organizacji** wykrywa i blokuje próby fałszowania z domeny w organizacji.

4. **Analiza fałszowania między domenami** wykrywa i blokuje próby fałszowania z domeny spoza organizacji.

5. **Filtrowanie zbiorcze** umożliwia administratorom skonfigurowanie poziomu ufności zbiorczej (BCL) wskazującego, czy komunikat został wysłany z nadawcy zbiorczego. Administratorzy mogą używać suwaka zbiorczego w zasadach ochrony przed spamem, aby zdecydować, jaki poziom poczty zbiorczej należy traktować jako spam.

6. **Analiza skrzynek pocztowych** uczy się na podstawie standardowych zachowań poczty e-mail użytkownika. Wykorzystuje on wykres komunikacji użytkownika do wykrywania, kiedy nadawcą jest tylko osoba, z kim użytkownik zwykle komunikuje się, ale jest w rzeczywistości złośliwy. Ta metoda wykrywa personifikację.

7. **Personifikacja analizy skrzynki pocztowej** umożliwia lub wyłącza rozszerzone wyniki personifikacji na podstawie mapy poszczególnych nadawców poszczególnych użytkowników. Po włączeniu tej funkcji można zidentyfikować personifikację.

8. **Personifikacja użytkownika** umożliwia administratorowi utworzenie listy obiektów docelowych o wysokiej wartości, które mogą być personifikowane. Jeśli nadejdzie wiadomość e-mail, w której nadawca ma tylko taką samą nazwę i adres jak chronione konto o wysokiej wartości, wiadomość zostanie oznaczona lub oznaczona tagiem. (Na przykład *trα cye@contoso.com* dla *tracye@contoso.com*).

9. **Personifikacja domeny** wykrywa domeny podobne do domeny adresata, które próbują wyglądać jak domena wewnętrzna. Na przykład ta personifikacja *tracye@liw α re.com* dla *tracye@litware.com*.

## <a name="phase-3---content-filtering"></a>Faza 3 — filtrowanie zawartości

W tej fazie stos filtrowania zaczyna obsługiwać określoną zawartość wiadomości e-mail, w tym jej hiperłącza i załączniki.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png" alt-text="Filtrowanie fazy 3 w usłudze MDO to filtrowanie zawartości" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png":::

1. **Reguły transportu** (znane również jako reguły przepływu poczty lub reguły transportu Exchange) umożliwiają administratorowi wykonywanie szerokiego zakresu akcji, gdy zostanie spełniony równie szeroki zakres warunków dla wiadomości. Wszystkie komunikaty przepływane przez organizację są oceniane pod kątem włączonych reguł przepływu poczty/reguł transportu.

2. **Program antywirusowy Microsoft Defender** i dwa *aparaty antywirusowe innych firm* są używane do wykrywania całego znanego złośliwego oprogramowania w załącznikach.

3. Aparaty antywirusowe (AV) są również używane do typu true wszystkich załączników, dzięki czemu **blokowanie typów** może blokować wszystkie załączniki typów określonych przez administratora.

4. Za każdym razem, gdy Ochrona usługi Office 365 w usłudze Microsoft Defender wykrywa złośliwy załącznik, skrót pliku i skrót jego aktywnej zawartości są dodawane do reputacji Exchange Online Protection (EOP). **Blokowanie reputacji załączników** zablokuje ten plik we wszystkich Office 365 i w punktach końcowych za pośrednictwem wywołań w chmurze MSAV.

5. **Klastrowanie heurystyczne** może ustalić, że plik jest podejrzany na podstawie heurystyki dostarczania. Po znalezieniu podejrzanego załącznika cała kampania zostaje wstrzymana, a plik jest w trybie piaskownicy. Jeśli plik zostanie uznany za złośliwy, cała kampania zostanie zablokowana.

6. **Modele uczenia maszynowego** działają na nagłówku, treści i adresach URL komunikatu w celu wykrywania prób wyłudzania informacji.

7. Firma Microsoft używa określenia reputacji z piaskownicy adresów URL, a także reputacji adresów URL z kanałów informacyjnych innych firm w **blokowania reputacji adresów URL**, aby zablokować wszelkie wiadomości ze znanym złośliwym adresem URL.

8. **Heurystyka zawartości** może wykrywać podejrzane komunikaty na podstawie struktury i częstotliwości słów w treści wiadomości przy użyciu modeli uczenia maszynowego.

9. **Sejf załączniki piaskownice** każdego załącznika dla Ochrona usługi Office 365 w usłudze Defender klientów przy użyciu analizy dynamicznej w celu wykrywania nigdy wcześniej nie widzianych zagrożeń.

10. **Detonacja połączonej zawartości** traktuje każdy adres URL łączący się z plikiem w wiadomości e-mail jako załącznik, asynchronicznie piaskownicę pliku w momencie dostarczenia.

11. **Detonacja adresu URL** ma miejsce, gdy nadrzędna technologia ochrony przed wyłudzaniem informacji znajdzie komunikat lub adres URL jako podejrzany. Piaskownica detonacji adresu URL określa adresy URL w komunikacie w momencie dostarczenia.

## <a name="phase-4---post-delivery-protection"></a>Faza 4 — ochrona po dostarczeniu

Ostatni etap odbywa się po dostarczeniu wiadomości e-mail lub pliku, działając na pocztę w różnych skrzynkach pocztowych, plikach i łączach, które pojawiają się w klientach, takich jak Microsoft Teams.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png" alt-text="Filtrowanie fazy 4 w Ochrona usługi Office 365 w usłudze Defender jest ochroną po dostarczeniu" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png":::

1. **Sejf Linki** to ochrona Ochrona usługi Office 365 w usłudze Defender czasu kliknięcia. Każdy adres URL w każdej wiadomości jest opakowane w celu wskazywania serwerów microsoft Sejf Links. Po kliknięciu adresu URL jest on sprawdzany pod kątem najnowszej reputacji, zanim użytkownik zostanie przekierowany do witryny docelowej. Adres URL jest asynchronicznie w trybie piaskownicy, aby zaktualizować swoją reputację.

2. **Automatyczne przeczyszczanie o wartości zero godzin (ZAP) w przypadku wyłudzania informacji** z mocą wsteczną wykrywa i neutralizuje złośliwe wiadomości wyłudzające informacje, które zostały już dostarczone do Exchange Online skrzynek pocztowych.

3. **Zap dla złośliwego oprogramowania** z mocą wsteczną wykrywa i neutralizuje złośliwe złośliwe oprogramowanie wiadomości, które zostały już dostarczone do Exchange Online skrzynek pocztowych.

4. **Zap dla spamu** z mocą wsteczną wykrywa i neutralizuje złośliwe wiadomości spamu, które zostały już dostarczone do Exchange Online skrzynek pocztowych.

5. **Widoki kampanii** pozwalają administratorom zobaczyć ogólny obraz ataku, szybciej i bardziej całkowicie, niż jakikolwiek zespół mógłby bez automatyzacji. Firma Microsoft korzysta z ogromnych ilości danych chroniących przed wyłudzaniem informacji, ochrony przed spamem i złośliwym oprogramowaniem w całej usłudze, aby ułatwić identyfikowanie kampanii, a następnie umożliwia administratorom badanie ich od początku do końca, w tym celów, wpływów i przepływów, które są również dostępne w zapisie kampanii do pobrania.

6. **Dodatki wiadomości raportu** umożliwiają użytkownikom łatwe zgłaszanie fałszywych alarmów (dobra wiadomość e-mail, omyłkowo oznaczona jako *zła*) lub fałszywych negatywów (zła wiadomość e-mail oznaczona jako *dobra*) firmie Microsoft w celu dalszej analizy.

7. **Sejf Linki dla klientów Office** oferuje taką samą ochronę przed kliknięciem Sejf Łącza, natywnie, wewnątrz klientów Office, takich jak Word, PowerPoint i Excel.

8. **Ochrona OneDrive, SharePoint i Teams** zapewnia taką samą ochronę załączników Sejf przed złośliwymi plikami, natywnie, wewnątrz OneDrive, SharePoint i Microsoft Teams.

9. Gdy adres URL wskazujący plik jest zaznaczony po dostarczeniu, **detonacja połączonej zawartości** wyświetla stronę ostrzeżenia do czasu zakończenia piaskownicy pliku, a adres URL zostanie uznany za bezpieczny.

## <a name="the-filtering-stack-diagram"></a>Diagram stosu filtrowania

Końcowy diagram (podobnie jak w przypadku wszystkich części diagramu, który go komponuje) *może ulec zmianie w miarę rozwoju i rozwoju produktu*. Dodaj do zakładek tę stronę i użyj opcji **opinii** , którą znajdziesz u dołu, jeśli musisz zapytać po aktualizacji. W przypadku rekordów jest to stos ze wszystkimi fazami w kolejności:

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png" alt-text="Wszystkie fazy filtrowania w Ochrona usługi Office 365 w usłudze Defender w kolejności od 1 do 4" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png":::

## <a name="more-information"></a>Więcej informacji

Czy musisz skonfigurować Ochrona usługi Office 365 w usłudze Microsoft Defender ***right now** _? Użyj tego stosu, _now*, z [tym krokiem](protect-against-threats.md) , aby rozpocząć ochronę organizacji.

*Specjalne podziękowania od MSFTTracyP i zespołu piszącego dokumenty do Giulian Garruba za tę zawartość*.
