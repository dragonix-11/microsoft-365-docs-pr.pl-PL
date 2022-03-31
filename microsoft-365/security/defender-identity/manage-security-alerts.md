---
title: Microsoft Defender for Identity zabezpieczeń w programie Microsoft 365 Defender
description: Dowiedz się, jak zarządzać alertami zabezpieczeń wydanymi przez inne Microsoft Defender for Identity i je przeglądać w programie Microsoft 365 Defender
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 3023dc05550aeee5a9d47bb7561eb221c6d1c588
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465822"
---
# <a name="defender-for-identity-security-alerts-in-microsoft-365-defender"></a>Alerty zabezpieczeń usługi Defender dla tożsamości w aplikacji Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono podstawowe informacje na temat pracy z alertami zabezpieczeń [Microsoft Defender for Identity w](/defender-for-identity) [programie Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Alerty usługi Defender dla tożsamości są natywnie zintegrowane <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> z dedykowanym formatem strony alertów tożsamości. Jest to pierwszy krok w kierunku wprowadzenia wszystkich nowych [Microsoft Defender for Identity w Microsoft 365 Defender](/defender-for-identity/defender-for-identity-in-microsoft-365-defender).

Strona nowego alertu tożsamości udostępnia Microsoft Defender for Identity lepsze wzbogacenie sygnału między domenami oraz nowe automatyczne funkcje odpowiedzi tożsamości. Zapewnia bezpieczeństwo i pomaga zwiększyć wydajność operacji zabezpieczających.

Jedną z zalet badania alertów za pośrednictwem aplikacji [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) jest skorelowanie alertów Microsoft Defender for Identity z informacjami uzyskanymi z każdego z pozostałych produktów w pakiecie. Te rozszerzone alerty są spójne z innymi formatami alertów Microsoft 365 Defender alertów pochodzącymi [z Ochrona usługi Office 365 w usłudze Microsoft Defender](/microsoft-365/security/office-365-security) i [ Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint). Nowa strona w praktyce eliminuje konieczność przechodzenia do innego portalu produktu w celu zbadania alertów skojarzonych z tożsamością.

Alerty pochodzące z usługi Defender dla tożsamości mogą teraz uruchamiać funkcje automatycznego badania i odpowiedzi [(AIR) programu Microsoft 365 Defender, w](/microsoft-365/security/defender/m365d-autoir) tym automatyczne korygowanie alertów oraz ograniczanie narzędzi i procesów, które mogą przyczyniać się do podejrzanych działań.

> [!IMPORTANT]
> W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

## <a name="review-security-alerts"></a>Przeglądanie alertów zabezpieczeń

Dostęp do alertów można uzyskiwać z wielu lokalizacji, w tym ze strony  Alerty, ze strony Zdarzenia, ze stron poszczególnych urządzeń oraz ze  strony zaawansowanego wyszukiwania. W tym przykładzie przejdę stronę **Alerty**.

W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> przejdź do alertów w & **zdarzeniach**, a następnie do **alertów**.

:::image type="content" source="../../media/defender-identity/incidents-alerts.png" alt-text="Element menu Alerty" lightbox="../../media/defender-identity/incidents-alerts.png":::

Aby wyświetlić alerty z usługi Defender dla tożsamości, w prawym górnym rogu wybierz pozycję **Filtr**, a  następnie w obszarze Źródła usług **wybierz** pozycję Microsoft Defender for Identity i wybierz pozycję **Zastosuj**:

:::image type="content" source="../../media/defender-identity/filter-defender-for-identity.png" alt-text="Filtr dla zdarzeń tożsamości usługi Defender" lightbox="../../media/defender-identity/filter-defender-for-identity.png":::

Alerty są wyświetlane z informacjami w następujących kolumnach: Nazwa **alertu****, Tagi****,** Ważność **, Stan** badania, **Stan****, Kategoria****, Źródło** wykrywania **, Zasoby****, Pierwsze** działanie i **Ostatnie działanie**.

:::image type="content" source="../../media/defender-identity/filtered-alerts.png" alt-text="Zdarzenia usługi Defender for Identity" lightbox="../../media/defender-identity/filtered-alerts.png":::

## <a name="manage-alerts"></a>Zarządzanie alertami

Jeśli klikniesz **nazwę alertu** dla jednego z alertów, zostaniesz na stronie ze szczegółami alertu. W okienku po lewej stronie zobaczysz podsumowanie Co się **stało**:

:::image type="content" source="../../media/defender-identity/what-happened.png" alt-text="Okienko Co się stało" lightbox="../../media/defender-identity/what-happened.png":::

Powyżej pola **Co się stało** znajdują przyciski **Konta**, **Host docelowy** **i Host** źródłowy alertu. W przypadku innych alertów mogą być dostępne przyciski służące do szczegółowych informacji o dodatkowych hostach, kontach, adresach IP, domenach i grupach zabezpieczeń. Wybierz dowolną z nich, aby uzyskać więcej szczegółowych informacji na temat zaangażowanych jednostek.

W prawym okienku zobaczysz szczegóły **alertu**. W tym miejscu można wyświetlić więcej szczegółów i wykonać kilka zadań:

- **Klasyfikowanie tego alertu** — w tym miejscu możesz określić ten alert jako **alert Prawda lub** Jako **fałszywy**

    :::image type="content" source="../../media/defender-identity/classify-alert.png" alt-text="Strona, na której można klasyfikować alerty" lightbox="../../media/defender-identity/classify-alert.png":::

- **Stan alertu** — w **koncentracji klasyfikacji** możesz sklasyfikować alert jako **Prawda** lub **Fałsz**. W **onecie** Przypisano możesz przypisać alert do siebie lub go nieprzydzielić.

    :::image type="content" source="../../media/defender-identity/alert-state.png" alt-text="Okienko Stan alertu" lightbox="../../media/defender-identity/alert-state.png":::

-  Szczegóły alertu — w obszarze Szczegóły alertu możesz znaleźć więcej informacji na temat konkretnego alertu, śledzić link do dokumentacji dotyczącej typu alertu, sprawdzać, z którym zdarzeniem jest skojarzony alert, przeglądać wszystkie zautomatyzowane badania połączone z tym typem alertu, a także sprawdzać urządzenia i użytkowników, których to dotyczy.

   :::image type="content" source="../../media/defender-identity/alert-details.png" alt-text="Strona Szczegóły alertu" lightbox="../../media/defender-identity/alert-details.png":::

- **Komentarze & —** tutaj możesz dodawać komentarze do alertu i wyświetlić historię wszystkich akcji skojarzonych z alertem.

    :::image type="content" source="../../media/defender-identity/comments-history.png" alt-text="Strona & komentarze" lightbox="../../media/defender-identity/comments-history.png":::

- **Zarządzanie alertami** — jeśli wybierzesz pozycję **Zarządzaj alertem**, przejdź do okienka umożliwiającego edytowanie:
  - **Stan** — możesz wybrać pozycję **Nowy**, **Rozwiązany** **lub W toku**.
  - **Klasyfikacja** — możesz wybrać pozycję **Prawda alertu** **lub Alert o wartości Fałsz**.
  - **Komentarz** — możesz dodać komentarz na temat alertu.

    Jeśli wybierzesz trzy kropki obok przycisku Zarządzaj **alertem**, możesz skorzystać z opcji Skonsultuj się z ekspertem ds.  **zagrożeń,** Wyeksportuj alert do pliku Excel pliku lub **Link do innego zdarzenia**.

    :::image type="content" source="../../media/defender-identity/manage-alert.png" alt-text="Opcja Zarządzaj alertami" lightbox="../../media/defender-identity/manage-alert.png":::

    > [!NOTE]
    > W tym Excel dostępne są dwa linki: Wyświetl w programie **Microsoft Defender for Identity** **i Wyświetl w** Microsoft 365 Defender. Każdy link prowadzi do odpowiedniego portalu i zawiera informacje o alercie.

## <a name="see-also"></a>Zobacz też

- [Badanie alertów w programie Microsoft 365 Defender](../defender/investigate-alerts.md)
