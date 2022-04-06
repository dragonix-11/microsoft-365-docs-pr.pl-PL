---
title: Badanie alertów Ochrona punktu końcowego w usłudze Microsoft Defender
description: Użyj opcji badania, aby uzyskać szczegółowe informacje na temat alertów wpływających na sieć, ich znaczenie i sposób ich rozwiązywania.
keywords: badanie, badanie, urządzenia, urządzenie, kolejka alertów, pulpit nawigacyjny, adres IP, plik, przesyłanie, przesyłanie, analiza szczegółowa, oś czasu, wyszukiwanie, domena, adres URL, ADRES IP
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
ms.openlocfilehash: e4d379ee476276d24b683878bc4978addf220ced
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665805"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Badanie alertów w Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

Zbadaj alerty wpływające na sieć, dowiedz się, co one oznaczają i jak je rozwiązać.

Wybierz alert z kolejki alertów, aby przejść do strony alertów. Ten widok zawiera tytuł alertu, zasoby, których dotyczy problem, okienko po stronie szczegółów i historię alertu.

Na stronie alertu rozpocznij badanie, wybierając zasoby, których dotyczy problem, lub dowolne jednostki w widoku drzewa historii alertów. Okienko szczegółów zostanie automatycznie wypełnione dalszymi informacjami o wybranych elementach. Aby zobaczyć, jakiego rodzaju informacje można wyświetlić tutaj, przeczytaj [artykuł Przejrzyj alerty w Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/review-alerts).

## <a name="investigate-using-the-alert-story"></a>Badanie przy użyciu scenariusza alertu

Historia alertu zawiera szczegółowe informacje o przyczynach wyzwolenia alertu, powiązanych zdarzeniach, które wystąpiły przed i po, a także innych powiązanych jednostkach.

Jednostki można klikać, a każda jednostka, która nie jest alertem, jest rozwijana przy użyciu ikony rozwijania po prawej stronie karty tej jednostki. Jednostka w centrum uwagi zostanie oznaczona niebieskim paskiem po lewej stronie karty tej jednostki, a alert w tytule będzie początkowo w centrum uwagi.

Rozwiń jednostki, aby szybko wyświetlić szczegóły. Wybranie jednostki spowoduje przełączenie kontekstu okienka szczegółów na tę jednostkę i umożliwi przeglądanie dalszych informacji, a także zarządzanie tą jednostką. Wybranie *pozycji ...* z prawej strony karty jednostki spowoduje wyświetlenie wszystkich akcji dostępnych dla tej jednostki. Te same akcje są wyświetlane w okienku szczegółów, gdy ta jednostka jest w centrum uwagi.

> [!NOTE]
> Sekcja dotycząca alertów może zawierać więcej niż jeden alert z dodatkowymi alertami dotyczącymi tego samego drzewa wykonywania wyświetlanymi przed wybranym alertem lub po nim.

:::image type="content" source="images/alert-story-tree.png" alt-text="scenariusz alertu z alertem w centrum uwagi i kilkoma rozwiniętymi kartami" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>Wykonaj akcję z okienka szczegółów

Po wybraniu interesującej jednostki okienko szczegółów zmieni się, aby wyświetlić informacje o wybranym typie jednostki, informacje historyczne, gdy są dostępne, i zaoferować kontrolki do **podjęcia akcji** na tej jednostce bezpośrednio ze strony alertu.

Po zakończeniu badania wróć do alertu, który został uruchomiony, oznacz stan alertu jako **rozwiązany** i zaklasyfikuj go jako **alert False** lub **True**. Klasyfikowanie alertów pomaga dostroić tę funkcję, aby zapewnić więcej prawdziwych alertów i mniej fałszywych alertów.

Jeśli zaklasyfikujesz go jako prawdziwy alert, możesz również wybrać określenie, jak pokazano na poniższej ilustracji.

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="Okienko szczegółów z rozwiązanym alertem i rozwiniętą listą rozwijaną określania" lightbox="images/alert-details-resolved-true.png":::

Jeśli występuje fałszywy alert z aplikacją biznesową, utwórz regułę pomijania, aby uniknąć tego typu alertów w przyszłości.

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="Akcje i klasyfikacja w okienku szczegółów z wyróżnioną regułą pomijania" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> Jeśli występują jakiekolwiek problemy, które nie zostały opisane powyżej, użyj przycisku 🙂 , aby przekazać opinię lub otworzyć bilet pomocy technicznej.

## <a name="related-topics"></a>Tematy pokrewne

- [Wyświetlanie i organizowanie kolejki alertów Ochrona punktu końcowego w usłudze Microsoft Defender](alerts-queue.md)
- [Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender](manage-alerts.md)
- [Badanie pliku skojarzonego z alertem usługi Defender for Endpoint](investigate-files.md)
- [Badanie urządzeń na liście Defender for Endpoint Devices](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem usługi Defender for Endpoint](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem usługi Defender for Endpoint](investigate-domain.md)
- [Badanie konta użytkownika w usłudze Defender for Endpoint](investigate-user.md)
