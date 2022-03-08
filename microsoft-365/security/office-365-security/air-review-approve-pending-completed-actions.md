---
title: Przeglądanie działań naprawczych i zarządzanie nimi w programie Microsoft Defender dla Office 365
keywords: AIR, autoIR, Microsoft Defender for Endpoint, automated, investigation, response, remediation, threats, advanced, threat, protection
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
description: Dowiedz się więcej o działaniach naprawczych w zakresie zautomatyzowanych badań i reakcji w programie Microsoft Defender dla Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: 35e9293fa83b86fb80c1c907fbf3a0769e323503
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318623"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>Przeglądanie działań naprawczych w programie Office 365

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)

Ponieważ zautomatyzowane badania nad wiadomościami e-& zawartości współpracy są werdyktami, takimi jak  złośliwe lub *podejrzane, niektóre* działania naprawcze są tworzone. W programie Microsoft Defender for Office 365 działania naprawcze mogą obejmować:

- Niechętne usuwanie wiadomości e-mail lub grup
- Wyłączanie zewnętrznego przesyłania dalej poczty

Te działania naprawcze nie są podejmowane, chyba że i do czasu zatwierdzenia ich przez zespół operacji zabezpieczeń. Zalecamy jak najszybciej przejrzenie i zatwierdzenie wszystkich oczekujących akcji, tak aby zautomatyzowane badania ukończono w terminie. W niektórych przypadkach można ponownie przemyśleć przesłane akcje.  Musisz być częścią funkcji wyszukiwania i & przed podjęciem jakichkolwiek działań.

## <a name="approve-or-reject-pending-actions"></a>Zatwierdzanie (lub odrzucanie) oczekujących akcji

Istnieją cztery różne sposoby odnajdowania i podjęcia działań autowydaju:

- [Kolejka zdarzeń](https://security.microsoft.com/incidents)
- Samo badanie (dostępne za pośrednictwem zdarzenia lub alertu)
- [Centrum akcji](https://security.microsoft.com/action-center/pending)
- [Kolejka badania i rozwiązywania problemów](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>Kolejka zdarzeń

1. W portalu Microsoft 365 Defender przejdź <https://security.microsoft.com>do strony Zdarzenia w witrynie Zdarzenia  **& Zdarzenia**\>. Aby przejść bezpośrednio do **strony Zdarzenia** , użyj funkcji <https://security.microsoft.com/incidents>.
2. Na stronie **Zdarzenia wybierz** nazwę zdarzenia, aby otworzyć jej stronę podsumowania.
3. Wybierz **kartę Dowód i** odpowiedź.
4. Zaznacz element na liście. Zostanie otwarte okienko boczne tej aplikacji.
5. W okienku bocznym zatwierdź lub odrzuć akcje.

## <a name="action-center"></a>Centrum akcji

1. W Microsoft 365 Defender akcji w witrynie <https://security.microsoft.com>, przejdź do **strony Centrum** akcji, wybierając **pozycję Centrum akcji**. Aby przejść bezpośrednio do **strony Centrum akcji** , użyj aplikacji <https://security.microsoft.com/action-center/pending>.
2. Na stronie **Centrum akcji** sprawdź, **czy jest** zaznaczona karta Oczekujące, a następnie przejrzyj listę akcji, które oczekują na zatwierdzenie.
   - Wybierz **pozycję Otwórz stronę badania,** aby wyświetlić więcej szczegółów dotyczących badania.
   - Wybierz **pozycję Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz **pozycję Odrzuć** , aby zapobiec podejmowanej akcji oczekującej.

## <a name="investigation-and-remediation-investigations-queue"></a>Kolejka badania i rozwiązywania problemów

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do strony **Badania zagrożeń** w witrynie Poczta e-mail & **badania** \> **dotyczące współpracy**. Aby przejść bezpośrednio do strony **Analizy zagrożeń**, użyj .<https://security.microsoft.com/airinvestigation>
2. Na stronie **Badanie zagrożeń** znajdź i element z listy, którego stan to Akcja **oczekująca**.
3. Kliknij pozycję ![Otwórz w nowym oknie.](../../media/m365-cc-sc-open-icon.png) **Otwieranie w nowym oknie** w czasie listy (między **wartościami Identyfikator** i **Stan**).
4. Na otwartej stronie zatwierdź lub odrzuć akcje.

## <a name="change-or-undo-one-remediation-action"></a>Zmienianie lub cofanie jednej akcji naprawczej

Istnieją dwa różne sposoby ponownego przemyślenia przesłanych akcji:

- Za [pośrednictwem ujednoliconego centrum akcji](https://security.microsoft.com/action-center).
- Chociaż Office [akcji](https://security.microsoft.com/threatincidents).

## <a name="change-or-undo-through-the-unified-action-center"></a>Zmienianie lub cofanie w ujednoliconym centrum akcji

1. W portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com>, przejdź do ujednoliconego centrum akcji, wybierając **pozycję Centrum akcji**. Aby przejść bezpośrednio do ujednoliconego centrum akcji, użyj funkcji <https://security.microsoft.com/action-center/>.
2. Na stronie **Centrum akcji** **wybierz kartę** Historia, a następnie wybierz akcję, którą chcesz zmienić lub cofnąć.
3. W okienku po prawej stronie ekranu wybierz odpowiednią **akcję (przejście** do skrzynki odbiorczej, przejście do folderu **Wiadomości-śmieci****, przejście** do elementów usuniętych **,** niechybne usunięcie lub usunięcie **twarde**).

## <a name="change-or-undo-through-the-office-action-center"></a>Zmienianie lub cofanie w Office akcji

1. W portalu Microsoft 365 Defender w <https://security.microsoft.com>witrynie , przejdź do Centrum Office akcji w witrynie Centrum akcji przeglądanie  & **e-mail**\>.\> Aby przejść bezpośrednio do centrum Office akcji, użyj .<https://security.microsoft.com/threatincidents>
2. Na stronie **Centrum akcji** wybierz odpowiednie środki zaradcze.
3. W panelu bocznym kliknij wpis elementów przesyłania poczty i poczekaj, aż lista zostanie załadowana.
4. Poczekaj, aż przycisk Akcja zostanie włączyć, a następnie wybierz przycisk Akcja, aby zmienić typ akcji.
5. Spowoduje to utworzenie odpowiednich akcji.

## <a name="next-steps"></a>Następne kroki

- [Używanie Eksploratora zagrożeń](threat-explorer.md)
- [Akcje administracyjne/ręczne](remediate-malicious-email-delivered-office-365.md)
- [Jak raportować wyniki fałszywie dodatnie/ujemne w funkcji automatycznego badania i odpowiedzi](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Zobacz też

- [Wyświetlanie szczegółów i wyników automatycznego badania w programie Office 365](air-view-investigation-results.md)
