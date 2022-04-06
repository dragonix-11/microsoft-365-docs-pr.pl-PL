---
title: Badanie Ochrona punktu końcowego w usłudze Microsoft Defender alertów
description: Za pomocą opcji badania możesz uzyskać szczegółowe informacje na temat alertów mających wpływ na Twoją sieć, ich znaczenie i sposób ich rozwiązywania.
keywords: badanie, analiza, urządzenia, urządzenie, kolejka alertów, pulpit nawigacyjny, adres IP, plik, przesyłanie, przesyłanie, deep analysis, oś czasu, wyszukiwanie, domena, adres URL, ADRES IP
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: e2ebdffa171266fdc0ec77047c9fecc5be9e56ba
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471170"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Badanie alertów w programie Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

Badanie alertów mających wpływ na sieć, zrozumienie ich znaczenie i sposób ich rozwiązywania.

Wybierz alert z kolejki alertów, aby przejść do strony alertów. Ten widok zawiera tytuł alertu, zasoby, okienko boczne szczegółów i historię alertu.

Na stronie alertu rozpocznij badanie, wybierając odpowiednie zasoby lub dowolne jednostki w widoku drzewa alertów. Okienko szczegółów zostanie automatycznie wypełnione  szczegółami na temat wybranej treści. Aby sprawdzić, jakiego rodzaju informacje można wyświetlić w tym miejscu, przeczytaj przeglądanie [alertów](/microsoft-365/security/defender-endpoint/review-alerts) w Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="investigate-using-the-alert-story"></a>Badanie za pomocą historii alertów

Historia alertu ze szczegółami przyczyny wyzwolenia alertu, powiązanymi zdarzeniami, które miały miejsce przed i po, a także innymi jednostkami pokrewnymi.

Encje można klikać, a każdą jednostkę, która nie jest alertem, można rozwinąć przy użyciu ikony rozwijania po prawej stronie karty tej jednostki. Encję, w która ma fokus, zostanie oznaczony niebieskim paskiem po lewej stronie karty tej jednostki, a alert w tytule będzie najpierw w centrum uwagi.

Rozwijaj encje, aby wyświetlać szczegóły jednym rzutem oka. Wybranie encji spowoduje przełączenie kontekstu okienka szczegółów do tej jednostki i umożliwi przeglądanie dodatkowych informacji, a także zarządzanie tą jednostką. Wybranie *przycisku ...* po prawej stronie karty jednostki spowoduje odsłonięcie wszystkich akcji dostępnych dla tej jednostki. Te same akcje są wyświetlane w okienku szczegółów, gdy ta jednostka ma fokus.

> [!NOTE]
> Sekcja artykułu alertu może zawierać więcej niż jeden alert, a dodatkowe alerty dotyczące tego samego drzewa wykonywania pojawiają się przed wybranym alertem lub po nim.

:::image type="content" source="images/alert-story-tree.png" alt-text="Alert z alertem w centrum uwagi i rozwiniętymi kartami" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>Działanie z okienka szczegółów

Po wybraniu encji zainteresowań okienko szczegółów zmieni się, aby wyświetlić informacje o wybranym typie encji, informacje historyczne, gdy jest dostępna, oraz oferować kontrolki do działania w tej encji bezpośrednio  ze strony alertu.

Po zakończeniu badania wróć do rozpoczętego alertu, oznacz stan alertu jako Rozwiązany i sklasyfikuj go  jako fałszywy **alert** lub **alert Prawda**. Alerty klasyfikowania pomagają dostosować tę funkcję w celu zapewnienia bardziej prawdziwych alertów i mniej fałszywych alertów.

Aby sklasyfikować ją jako prawdziwy alert, można także wybrać wyznaczanie, jak pokazano na poniższej ilustracji.

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="Okienko szczegółów z rozstrzygniętym alertem i rozwiniętą menu rozwijanego wyznaczania" lightbox="images/alert-details-resolved-true.png":::

W przypadku wystąpienia fałszywych alertów alertów z aplikacja LOB utwórz regułę częściowego alertu, aby uniknąć tego typu alertu w przyszłości.

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="Akcje i klasyfikacja w okienku szczegółów z wyróżniona regułą reguły ekgresu" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> Jeśli występują problemy, które nie zostały opisane powyżej, 🙂 użyj przycisku, aby przekazać opinię lub otworzyć zgłoszenie do pomocy technicznej.


## <a name="related-topics"></a>Tematy pokrewne
- [Wyświetlanie i organizowanie kolejki Ochrona punktu końcowego w usłudze Microsoft Defender alertów](alerts-queue.md)
- [Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender wiadomości](manage-alerts.md)
- [Badanie pliku skojarzonego z alertem programu Defender dla punktu końcowego](investigate-files.md)
- [Badanie urządzeń na liście Usługi Defender dla urządzeń końcowych](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem programu Defender dla punktu końcowego](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem programu Defender dla punktu końcowego](investigate-domain.md)
- [Badanie konta użytkownika w programie Defender dla punktu końcowego](investigate-user.md)


