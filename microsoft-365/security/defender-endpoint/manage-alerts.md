---
title: Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender wiadomości
description: Za pomocą menu Zarządzaj alertami można zmieniać stan alertów, tworzyć reguły ostrzeżeń w celu ukrywania alertów, przesyłania komentarzy i przeglądania historii zmian dla poszczególnych alertów.
keywords: zarządzanie alertami, zarządzanie, alerty, stan, nowy, w toku, rozwiązywanie, rozwiązywanie alertów, pomijanie, kompresja, reguły, kontekst, historia, komentarze, zmiany
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
ms.openlocfilehash: 83e7bd2cc46469cb6a5a6bc8c29a8d21dba20b7f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466196"
---
# <a name="manage-microsoft-defender-for-endpoint-alerts"></a>Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender wiadomości

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Program Defender for Endpoint powiadamia Cię o możliwych złośliwych zdarzeniach, atrybutach i informacjach kontekstowych za pośrednictwem alertów. Podsumowanie nowych alertów jest wyświetlane na pulpicie nawigacyjnym Operacje **zabezpieczeń, a** także umożliwia dostęp do wszystkich alertów w **kolejce alertów**.

Alertami można zarządzać, wybierając je w kolejce **Alerty** lub na  karcie Alerty na stronie Urządzenie dla poszczególnych urządzeń.

Wybranie alertu w jednym z tych miejsc prowadzi do **okienka Zarządzanie alertami**.

:::image type="content" source="images/atp-alerts-selected.png" alt-text="Okienko zarządzania alertami i kolejka alertów" lightbox="images/atp-alerts-selected.png":::

## <a name="link-to-another-incident"></a>Link do innego zdarzenia

Możesz utworzyć nowe zdarzenie z alertu lub linku do istniejącego zdarzenia.

## <a name="assign-alerts"></a>Przypisywanie alertów

Jeśli alert nie został jeszcze przypisany, możesz wybrać pozycję **Przypisz** do mnie, aby przypisać alert do siebie.

## <a name="suppress-alerts"></a>Pomiń alerty

W niektórych sytuacjach może być konieczne pominięcie pojawiania się alertów w Microsoft 365 Defender. Program Defender for Endpoint umożliwia tworzenie reguł obowiązujących dla określonych alertów, o których wiadomo, że są one niezbędne, takie jak znane narzędzia lub procesy w organizacji.

Reguły można tworzyć na podstawie istniejącego alertu. W razie potrzeby można je wyłączyć i w razie potrzeby ponownie wywoływali.

Podczas tworzenia reguły reguła będzie obowiązywać od momentu jej utworzenia. Reguła nie będzie mieć wpływu na istniejące alerty już w kolejce przed utworzeniem reguły. Reguła zostanie zastosowana tylko do alertów spełniających warunki określone po jej utworzeniu.

Istnieją dwa konteksty reguły, do wyboru:

- **Pomiń alerty na tym urządzeniu**
- **Pomiń alert w mojej organizacji**

Kontekst reguły pozwala dostosować to, co jest dostępne w portalu, oraz zagwarantować, że w portalu będą publikowane tylko rzeczywiste alerty zabezpieczeń.

Możesz użyć przykładów z poniższej tabeli, aby ułatwić ci wybranie kontekstu reguły reguły eksowej:

|Kontekst|Definicja|Przykładowe scenariusze|
|---|---|---|
|**Pomiń alerty na tym urządzeniu**|Alerty z tym samym tytułem alertu i tylko na tym konkretnym urządzeniu zostaną pominięte. <p> Wszystkie inne alerty na tym urządzeniu nie będą pomijane.|<ul><li>Badacz zabezpieczeń bada złośliwy skrypt, który został użyty do ataków na inne urządzenia w organizacji.</li><li>Deweloper regularnie tworzy skrypty programu PowerShell dla swojego zespołu.</li></ul>|
|**Pomiń alert w mojej organizacji**|Alerty z tym samym tytułem alertu na dowolnym urządzeniu będą pomijane.|<ul><li>Wszystkie osoby w organizacji będą korzystać z administracyjnych narzędzi administracyjnych, które mogą być w tym celu używane.</li></ul>|

### <a name="suppress-an-alert-and-create-a-new-suppression-rule"></a>Pomijanie alertu i tworzenie nowej reguły reguły odc.

Tworzenie reguł niestandardowych w celu kontrolowania, kiedy alerty są pomijane lub rozwiązywane. Można sterować kontekstem, w którym alert jest pomijany, przez podanie tytułu alertu, wskaźnika naruszenia i warunków. Po określeniu kontekstu będzie można skonfigurować akcję i zakres w alercie.

1. Wybierz alert, który chcesz pominąć. Zostanie w ten sposób wyz **zawartość okienka Zarządzanie alertami** .

2. Wybierz **pozycję Utwórz regułę reguły.**

    Można utworzyć warunek podkresu przy użyciu tych atrybutów. Między poszczególnymi warunkami jest stosowany operator AND, więc tylko wtedy, gdy są spełnione wszystkie warunki.

    - Plik SHA1
    - Nazwa pliku — obsługiwana jest symbol wieloznaczny
    - Ścieżka folderu — obsługiwana jest symbol wieloznaczny
    - Adres IP
    - Adres URL — obsługiwany jest symbol wieloznaczny
    - Wiersz polecenia — obsługiwany jest symbol wieloznaczny

3. Wybierz pozycję **Wyzwalanie IOC**.

4. Określ akcję i zakres alertu.

   Alert można automatycznie rozstrzygnieć lub ukryć przed portalem. Alerty, które są automatycznie rozwiązywane, będą wyświetlane w rozwiązanych sekcjach kolejki alertów, strony alertów i osi czasu urządzenia oraz będą wyświetlane jako rozpoznane w interfejsach API punktów końcowych usługi Defender.

   Alerty oznaczone jako ukryte zostaną pominięte w całym systemie, zarówno na skojarzonych z urządzeniem alertach, jak i na pulpicie nawigacyjnym, i nie będą przesyłane strumieniowo przez interfejsy API punktów końcowych usługi Defender.

5. Wprowadź nazwę reguły i komentarz.

6. Kliknij **Zapisz**.

#### <a name="view-the-list-of-suppression-rules"></a>Wyświetlanie listy reguł ekbrydów

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **alertu**.

2. Lista reguł reguł utworzonych przez użytkowników w organizacji.

Aby uzyskać więcej informacji na temat zarządzania regułami [](manage-suppression-rules.md) reguł

## <a name="change-the-status-of-an-alert"></a>Zmienianie stanu alertu

Alerty można kategoryzować **(jako Nowe**, **W toku** lub Rozwiązane **), zmieniając** ich status w trakcie badania. Ułatwia to organizowanie alertów i zarządzanie tym, jak zespół może odpowiadać na alerty.

Na przykład kierownik zespołu może przejrzeć wszystkie nowe  alerty i przypisać go do kolejki W **toku w celu** dalszej analizy.

Ewentualnie kierownik zespołu może przypisać alert do kolejki Rozwiązany, jeśli  wie, że alert jest nieodpowiedni, pochodzących z urządzenia, które nie ma znaczenia (na przykład należącego do administratora zabezpieczeń) lub które jest zajęte za pomocą wcześniejszego alertu.

## <a name="alert-classification"></a>Klasyfikacja alertu

Możesz nie ustawiać klasyfikacji lub określać, czy alert jest alertem prawdziwym, czy alertem fałszywym. Ważne jest podanie klasyfikacji wyników dodatnich/fałszywie dodatnich. Ta klasyfikacja jest używana do monitorowania jakości alertów i zapewnia większą dokładność alertów. Pole "określenie" definiuje dodatkową wierność klasyfikacji "prawdziwego dodatniego".

## <a name="add-comments-and-view-the-history-of-an-alert"></a>Dodawanie komentarzy i wyświetlanie historii alertów

Możesz dodawać komentarze i wyświetlać historyczne zdarzenia dotyczące alertu, aby zobaczyć wcześniejsze zmiany wprowadzone w alercie.

Każda zmiana lub komentarz w alercie jest rejestrowany w sekcji **Komentarze i** historia.

Dodane komentarze natychmiast pojawiają się w okienku.

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie regułami zarządzania regułami](manage-suppression-rules.md)
- [Wyświetlanie i organizowanie kolejki Ochrona punktu końcowego w usłudze Microsoft Defender alertów](alerts-queue.md)
- [Badanie Ochrona punktu końcowego w usłudze Microsoft Defender alertów](investigate-alerts.md)
- [Badanie pliku skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender pliku](investigate-files.md)
- [Badanie urządzeń na liście Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender adresu IP](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem Ochrona punktu końcowego w usłudze Microsoft Defender domeny](investigate-domain.md)
- [Badanie konta użytkownika w programie Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-user.md)
