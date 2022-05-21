---
title: Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender
description: Zmień stan alertów, utwórz reguły pomijania, aby ukryć alerty, przesłać komentarze i przejrzeć historię zmian dla poszczególnych alertów za pomocą menu Zarządzanie alertami.
keywords: zarządzanie alertami, zarządzanie, alerty, stan, nowy, w toku, rozwiązany, rozwiązywanie alertów, pomijanie, supression, reguły, kontekst, historia, komentarze, zmiany
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
ms.openlocfilehash: c14447301cfa6abf83c231361c020d261eeb87a9
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623444"
---
# <a name="manage-microsoft-defender-for-endpoint-alerts"></a>Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Usługa Defender for Endpoint powiadamia o możliwych złośliwych zdarzeniach, atrybutach i informacjach kontekstowych za pośrednictwem alertów. Podsumowanie nowych alertów jest wyświetlane na **pulpicie nawigacyjnym Operacje zabezpieczeń** i można uzyskać dostęp do wszystkich alertów w **kolejce alertów**.

Alertami można zarządzać, wybierając alert w **kolejce Alerty** lub kartę **Alerty** na stronie Urządzenie dla pojedynczego urządzenia.

Wybranie alertu w każdym z tych miejsc powoduje utworzenie **okienka zarządzania alertami**.

:::image type="content" source="images/atp-alerts-selected.png" alt-text="Okienko zarządzania alertami i kolejka alertów" lightbox="images/atp-alerts-selected.png":::

Obejrzyj ten film wideo, aby dowiedzieć się, jak używać nowej strony alertów Ochrona punktu końcowego w usłudze Microsoft Defender.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4yiO5]

## <a name="link-to-another-incident"></a>Link do innego incydentu

Możesz utworzyć nowe zdarzenie z poziomu alertu lub utworzyć link do istniejącego incydentu.

## <a name="assign-alerts"></a>Przypisywanie alertów

Jeśli alert nie został jeszcze przypisany, możesz wybrać pozycję **Przypisz do mnie** , aby przypisać alert do siebie.

## <a name="suppress-alerts"></a>Pomijanie alertów

Mogą istnieć scenariusze, w których należy pominąć wyświetlanie alertów w Microsoft 365 Defender. Usługa Defender for Endpoint umożliwia tworzenie reguł pomijania dla określonych alertów, o których wiadomo, że są nieszkodliwe, takich jak znane narzędzia lub procesy w organizacji.

Reguły pomijania można utworzyć na podstawie istniejącego alertu. W razie potrzeby można je wyłączyć i przywrócić.

Gdy zostanie utworzona reguła pomijania, zacznie obowiązywać od momentu utworzenia reguły. Reguła nie wpłynie na istniejące alerty już w kolejce przed utworzeniem reguły. Reguła będzie stosowana tylko w przypadku alertów spełniających warunki ustawione po utworzeniu reguły.

Istnieją dwa konteksty reguły pomijania, z których można wybrać:

- **Pomijanie alertu na tym urządzeniu**
- **Pomijanie alertu w mojej organizacji**

Kontekst reguły umożliwia dostosowanie tego, co zostanie wyświetlone w portalu, i upewnienie się, że w portalu zostaną wyświetlone tylko prawdziwe alerty zabezpieczeń.

Przykłady z poniższej tabeli ułatwiają wybranie kontekstu reguły pomijania:

|Kontekście|Definicja|Przykładowe scenariusze|
|---|---|---|
|**Pomijanie alertu na tym urządzeniu**|Alerty o tym samym tytule alertu i tylko na tym urządzeniu zostaną pominięte. <p> Wszystkie inne alerty na tym urządzeniu nie zostaną pominięte.|<ul><li>Badacz zabezpieczeń bada złośliwy skrypt, który został użyty do ataku na inne urządzenia w organizacji.</li><li>Deweloper regularnie tworzy skrypty programu PowerShell dla swojego zespołu.</li></ul>|
|**Pomijanie alertu w mojej organizacji**|Alerty o tym samym tytule alertu na dowolnym urządzeniu zostaną pominięte.|<ul><li>Niegroźne narzędzie administracyjne jest używane przez wszystkich użytkowników w organizacji.</li></ul>|

### <a name="suppress-an-alert-and-create-a-new-suppression-rule"></a>Pomijanie alertu i tworzenie nowej reguły pomijania

Utwórz reguły niestandardowe, aby kontrolować, kiedy alerty są pomijane lub rozwiązywane. Kontekst można kontrolować, gdy alert jest pomijany, określając tytuł alertu, wskaźnik naruszenia zabezpieczeń i warunki. Po określeniu kontekstu będzie można skonfigurować akcję i zakres alertu.

1. Wybierz alert, który chcesz pominąć. Spowoduje to utworzenie **okienka zarządzania alertami** .

2. Wybierz **pozycję Utwórz regułę pomijania**.

    Warunek pomijania można utworzyć przy użyciu tych atrybutów. Operator AND jest stosowany między każdym warunkiem, więc pomijanie występuje tylko wtedy, gdy wszystkie warunki są spełnione.

    - Plik SHA1
    - Nazwa pliku — obsługiwane symbole wieloznaczne
    - Ścieżka folderu — obsługiwane symbole wieloznaczne
    - Adres IP
    - Adres URL — obsługiwane symbole wieloznaczne
    - Wiersz polecenia — obsługiwane symbole wieloznaczne

3. Wybierz **wyzwalający mkol**.

4. Określ akcję i zakres alertu.

   Alert można automatycznie rozpoznać lub ukryć w portalu. Alerty, które są automatycznie rozwiązywane, będą wyświetlane w rozwiązanej sekcji kolejki alertów, strony alertów i osi czasu urządzenia i będą wyświetlane jako rozwiązane w interfejsach API punktu końcowego usługi Defender.

   Alerty oznaczone jako ukryte zostaną pominięte w całym systemie, zarówno na skojarzonych alertach urządzenia, jak i na pulpicie nawigacyjnym i nie będą przesyłane strumieniowo przez interfejsy API punktu końcowego usługi Defender.

5. Wprowadź nazwę reguły i komentarz.

6. Kliknij **Zapisz**.

#### <a name="view-the-list-of-suppression-rules"></a>Wyświetlanie listy reguł pomijania

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Pomijanie alertów**.

2. Lista reguł pomijania zawiera wszystkie reguły utworzone przez użytkowników w organizacji.

Aby uzyskać więcej informacji na temat zarządzania regułami pomijania, zobacz [Zarządzanie regułami pomijania](manage-suppression-rules.md)

## <a name="change-the-status-of-an-alert"></a>Zmienianie stanu alertu

Alerty (jako **nowe**, **w toku** lub **rozwiązane**) można kategoryzować, zmieniając ich stan w miarę postępu badania. Ułatwia to organizowanie i zarządzanie sposobem reagowania zespołu na alerty.

Na przykład lider zespołu może przejrzeć wszystkie **nowe** alerty i podjąć decyzję o przypisaniu ich do kolejki **W toku w** celu dalszej analizy.

Alternatywnie lider zespołu może przypisać alert do **rozwiązanej** kolejki, jeśli wie, że alert jest niegroźny, pochodzący z urządzenia, które nie ma znaczenia (na przykład należącego do administratora zabezpieczeń) lub jest rozpatrywany za pośrednictwem wcześniejszego alertu.

## <a name="alert-classification"></a>Klasyfikacja alertów

Możesz nie ustawiać klasyfikacji ani określać, czy alert jest prawdziwym alertem, czy fałszywym alertem. Ważne jest, aby zapewnić klasyfikację prawdziwie dodatnich/fałszywie dodatnich. Ta klasyfikacja służy do monitorowania jakości alertów i zwiększenia dokładności alertów. Pole "determinacja" definiuje dodatkową wierność dla klasyfikacji "prawdziwie dodatniej".

## <a name="add-comments-and-view-the-history-of-an-alert"></a>Dodawanie komentarzy i wyświetlanie historii alertu

Możesz dodawać komentarze i wyświetlać zdarzenia historyczne dotyczące alertu, aby zobaczyć poprzednie zmiany wprowadzone w alercie.

Za każdym razem, gdy zostanie wprowadzona zmiana lub komentarz do alertu, jest on rejestrowany w sekcji **Komentarze i historia** .

Dodane komentarze natychmiast pojawiają się w okienku.

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzaj regułami pomijania](manage-suppression-rules.md)
- [Wyświetlanie i organizowanie kolejki alertów Ochrona punktu końcowego w usłudze Microsoft Defender](alerts-queue.md)
- [Badanie alertów Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-alerts.md)
- [Badanie pliku skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-files.md)
- [Badanie urządzeń na liście urządzeń Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-domain.md)
- [Badanie konta użytkownika w Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-user.md)
