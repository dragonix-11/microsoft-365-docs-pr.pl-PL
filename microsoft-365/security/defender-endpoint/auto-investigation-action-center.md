---
title: Odwiedź centrum akcji, aby wyświetlić akcje korygowania
description: Wyświetlanie szczegółów i wyników po zautomatyzowanym badaniu za pomocą centrum akcji
keywords: action, center, autoir, automated, investigation, response, remediation
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.technology: mde
ms.openlocfilehash: 6a2cc5d4315c5dd64a852c74176272061789b1ba
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535409"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Odwiedź centrum akcji, aby wyświetlić akcje korygowania

Podczas i po zautomatyzowanym badaniu są identyfikowane akcje korygowania wykrywania zagrożeń. W zależności od konkretnego zagrożenia oraz sposobu [konfigurowania funkcji zautomatyzowanego badania i korygowania](configure-automated-investigations-remediation.md) dla organizacji niektóre akcje korygowania są wykonywane automatycznie, a inne wymagają zatwierdzenia. Jeśli jesteś członkiem zespołu ds. operacji zabezpieczeń w organizacji, możesz wyświetlić oczekujące i ukończone [akcje korygowania](manage-auto-investigation.md#remediation-actions) w **Centrum akcji**.

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/mdb-overview.md)

## <a name="the-unified-action-center"></a>Ujednolicone Centrum akcji

Ostatnio centrum akcji zostało zaktualizowane. Masz teraz ujednolicone środowisko Centrum akcji. Aby uzyskać dostęp do centrum akcji, przejdź do [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) obszaru i zaloguj się.

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Strona Centrum akcji w portalu Microsoft 365 Defender" lightbox="images/mde-action-center-unified.png":::

### <a name="whats-changed"></a>Co się zmieniło?

W poniższej tabeli porównano nowe, ujednolicone centrum akcji z poprzednim centrum akcji.

|Nowe, ujednolicone centrum akcji  |Poprzednie centrum akcji  |
|---------|---------|
|Wyświetla listę oczekujących i zakończonych akcji dla urządzeń i poczty e-mail w jednej lokalizacji <br/>([Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md) plus [Ochrona usługi Office 365 w usłudze Microsoft Defender](/microsoft-365/security/office-365-security/office-365-atp))|Wyświetla listę oczekujących i ukończonych akcji dla urządzeń <br/> (tylko [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md))   |
|Znajduje się pod adresem:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Znajduje się pod adresem:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> wybierz pozycję **Centrum akcji**. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Okienko nawigacji do Centrum akcji w portalu Microsoft 365 Defender" lightbox="images/action-center-nav-new.png"::: | W portalu Microsoft 365 Defender wybierz pozycję **Zautomatyzowane badaniaW** >  **centrum akcji**. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="Starsza wersja okienka nawigacji do Centrum akcji w portalu Microsoft 365 Defender" lightbox="images/action-center-nav-old.png":::  |

Ujednolicone centrum akcji łączy akcje korygowania w usłudze Defender for Endpoint i Ochrona usługi Office 365 w usłudze Defender. Definiuje on wspólny język dla wszystkich akcji korygowania i zapewnia ujednolicone środowisko badania.

Możesz użyć ujednoliconego Centrum akcji, jeśli masz odpowiednie uprawnienia i co najmniej jedną z następujących subskrypcji:

- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md)
- [Ochrona usługi Office 365 w usłudze Defender](/microsoft-365/security/office-365-security/office-365-atp)
- [Defender dla Firm](../defender-business/mdb-overview.md)

## <a name="using-the-action-center"></a>Korzystanie z centrum akcji

Aby przejść do ujednoliconego centrum akcji w ulepszonym portalu Microsoft 365 Defender:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Centrum akcji**.

3. Użyj kart **Oczekujące akcje** i **Historia** . Poniższa tabela zawiera podsumowanie tego, co zobaczysz na każdej karcie:

   |Zakładka|Opis|
   |---|---|
   |**Oczekujące**|Wyświetla listę akcji, które wymagają uwagi. Możesz zatwierdzać lub odrzucać akcje pojedynczo lub wybrać wiele akcji, jeśli mają one ten sam typ akcji (na przykład **plik kwarantanny**). <p> **PORADA**: Sprawdź [i zatwierdź (lub odrzuć) oczekujące akcje](manage-auto-investigation.md) tak szybko, jak to możliwe, aby zautomatyzowane badania mogły zakończyć się w odpowiednim czasie.|
   |**Historia**|Służy jako dziennik inspekcji dla wykonanych akcji, takich jak: <ul><li>Akcje korygujące, które zostały podjęte w wyniku zautomatyzowanych dochodzeń</li><li>Akcje korygowania zatwierdzone przez zespół ds. operacji zabezpieczeń</li><li>Polecenia, które zostały uruchomione i akcje korygowania, które zostały zastosowane podczas sesji odpowiedzi na żywo</li><li>Akcje korygowania, które zostały podjęte przez funkcje ochrony przed zagrożeniami w Program antywirusowy Microsoft Defender</li></ul> <p> Umożliwia cofnięcie niektórych akcji (zobacz [Cofnij ukończone akcje](manage-auto-investigation.md#undo-completed-actions)).|

4. Aby dostosować, sortować, filtrować i eksportować dane w centrum akcji, wykonaj co najmniej jedną z następujących czynności:

   :::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="Centrum akcji z kolumnami i filtrami" lightbox="images/new-action-center-columnsfilters.png":::

   - Wybierz nagłówek kolumny, aby sortować elementy w kolejności rosnącej lub malejącej.
   - Użyj filtru okresu, aby wyświetlić dane z ostatniego dnia, tygodnia, 30 dni lub 6 miesięcy.
   - Wybierz kolumny, które chcesz wyświetlić.
   - Określ liczbę elementów do uwzględnienia na każdej stronie danych.
   - Użyj filtrów, aby wyświetlić tylko elementy, które chcesz zobaczyć.
   - Wybierz pozycję **Eksportuj** , aby wyeksportować wyniki do pliku .csv.

## <a name="next-steps"></a>Następne kroki

- [Wyświetl i zatwierdź akcje korygowania](manage-auto-investigation.md)
- [Zobacz interaktywny przewodnik: Badanie i korygowanie zagrożeń za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)
- [Porównanie funkcji zabezpieczeń w planach Microsoft 365 dla małych i średnich firm](../defender-business/compare-mdb-m365-plans.md)
