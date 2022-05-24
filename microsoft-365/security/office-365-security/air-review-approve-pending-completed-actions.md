---
title: Przeglądanie akcji korygowania i zarządzanie nimi w Ochrona usługi Office 365 w usłudze Microsoft Defender
keywords: AIR, autoIR, Ochrona punktu końcowego w usłudze Microsoft Defender, automated, investigation, response, remediation, threats, advanced, threat, protection
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Dowiedz się więcej o akcjach korygowania w ramach funkcji zautomatyzowanego badania i reagowania w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: aaa444a2bada254aeed83540aee361ed806ab0a0
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649126"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>Przeglądanie akcji korygowania i zarządzanie nimi w Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)

Ponieważ zautomatyzowane badania dotyczące poczty e-mail & zawartości współpracy powodują werdykty, takie jak *Złośliwe* lub *Podejrzane*, są tworzone pewne akcje korygowania. W Ochrona usługi Office 365 w usłudze Microsoft Defender akcje korygowania mogą obejmować:

- Usuwanie nietrwałe wiadomości e-mail lub klastrów
- Wyłączanie przekazywania poczty zewnętrznej

Te akcje korygowania nie są wykonywane, chyba że i dopóki zespół ds. operacji zabezpieczeń nie zatwierdzi ich. Zalecamy jak najszybsze przejrzenie i zatwierdzenie wszelkich oczekujących akcji, aby zautomatyzowane badania zostały zakończone w odpowiednim czasie. W niektórych przypadkach można ponownie rozważyć przesłane akcje.  Musisz być częścią roli & wyszukiwania przeczyszczania przed podjęciem jakichkolwiek akcji.

## <a name="approve-or-reject-pending-actions"></a>Zatwierdzanie (lub odrzucanie) oczekujących akcji

Istnieją cztery różne sposoby znajdowania i podejmowania akcji automatycznego badania:

- [Kolejka zdarzeń](https://security.microsoft.com/incidents)
- Samo badanie (dostępne za pośrednictwem zdarzenia lub alertu)
- [Centrum akcji](https://security.microsoft.com/action-center/pending)
- [Kolejka dochodzeń i dochodzeń korygowania](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>Kolejka zdarzeń

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do strony **Zdarzenia** w **temacie Incydenty & alerty** \> **Zdarzenia**. Aby przejść bezpośrednio do strony **Zdarzenia** , użyj polecenia <https://security.microsoft.com/incidents>.
2. Na stronie **Zdarzenia** wybierz nazwę zdarzenia, aby otworzyć jego stronę podsumowania.
3. Wybierz kartę **Dowody i odpowiedź** .
4. Wybierz element z listy. Zostanie otwarte okienko boczne.
5. W okienku bocznym wykonaj akcje zatwierdzania lub odrzucania.

## <a name="action-center"></a>Centrum akcji

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do strony **Centrum akcji**, wybierając pozycję **Centrum akcji**. Aby przejść bezpośrednio do strony **Centrum akcji** , użyj polecenia <https://security.microsoft.com/action-center/pending>.
2. Na stronie **Centrum akcji** sprawdź, czy **wybrano kartę Oczekujące** , a następnie przejrzyj listę akcji oczekujących na zatwierdzenie.
   - Wybierz **pozycję Otwórz stronę badania** , aby wyświetlić więcej szczegółów na temat badania.
   - Wybierz pozycję **Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz pozycję **Odrzuć** , aby zapobiec podjęciu oczekującej akcji.

## <a name="investigation-and-remediation-investigations-queue"></a>Kolejka dochodzeń i dochodzeń korygowania

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do strony **Badanie zagrożeń** w witrynie Email & collaboration **Investigations** (**Badanie współpracy** \> & poczty e-mail). Aby przejść bezpośrednio do strony **Badanie zagrożeń** , użyj polecenia <https://security.microsoft.com/airinvestigation>.
2. Na stronie **Badanie zagrożeń** znajdź element z listy, którego stan to **Oczekująca akcja**.
3. Kliknij przycisk ![Otwórz w nowym oknie ikona.](../../media/m365-cc-sc-open-icon.png) **Otwórz w nowym oknie** w czasie listy (między **identyfikatorem** a **stanem**).
4. Na otwartej stronie wykonaj akcje zatwierdzania lub odrzucania.

## <a name="change-or-undo-one-remediation-action"></a>Zmienianie lub cofanie jednej akcji korygowania

Istnieją dwa różne sposoby ponownego rozważenia przesłanych akcji:

- Za pośrednictwem [ujednoliconego centrum akcji](https://security.microsoft.com/action-center).
- Chociaż [centrum akcji Office](https://security.microsoft.com/threatincidents).

## <a name="change-or-undo-through-the-unified-action-center"></a>Zmienianie lub cofanie za pośrednictwem ujednoliconego centrum akcji

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do ujednoliconego centrum akcji, wybierając pozycję **Centrum akcji**. Aby przejść bezpośrednio do ujednoliconego centrum akcji, użyj polecenia <https://security.microsoft.com/action-center/>.
2. Na stronie **Centrum akcji** wybierz kartę **Historia** , a następnie wybierz akcję, którą chcesz zmienić lub cofnąć.
3. W okienku po prawej stronie ekranu wybierz odpowiednią akcję (**przejdź do skrzynki odbiorczej**, **przejdź do wiadomości-śmieci**, **przejdź do usuniętych elementów**, **usuń nietrwałe** lub **usuń je na stałe**).

## <a name="change-or-undo-through-the-office-action-center"></a>Zmienianie lub cofanie za pośrednictwem centrum akcji Office

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do centrum akcji Office w witrynie **Email & collaboration** \> **Review** \> **Action Center**. Aby przejść bezpośrednio do centrum akcji Office, użyj polecenia <https://security.microsoft.com/threatincidents>.
2. Na stronie **Centrum akcji** wybierz odpowiednie korygowanie.
3. W panelu bocznym kliknij wpis przesyłania wiadomości e-mail i poczekaj na załadowanie listy.
4. Poczekaj na przycisk Akcja u góry, aby włączyć i wybierz przycisk Akcja, aby zmienić typ akcji.
5. Spowoduje to utworzenie odpowiednich akcji.

## <a name="next-steps"></a>Następne kroki

- [Korzystanie z Eksploratora zagrożeń](threat-explorer.md)
- [Administracja /Akcje ręczne](remediate-malicious-email-delivered-office-365.md)
- [Jak zgłaszać wyniki fałszywie dodatnie/ujemne w zautomatyzowanych możliwościach badania i reagowania](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Zobacz też

- [Wyświetlanie szczegółów i wyników zautomatyzowanego badania w Office 365](air-view-investigation-results.md)
