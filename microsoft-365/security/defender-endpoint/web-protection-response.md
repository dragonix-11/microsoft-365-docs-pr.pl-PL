---
title: Odpowiadanie na zagrożenia w sieci Ochrona punktu końcowego w usłudze Microsoft Defender
description: Odpowiadanie na alerty dotyczące złośliwych i niechcianych witryn internetowych. Zrozumienie, jak ochrona przed zagrożeniami w sieci Web informuje użytkowników końcowych za pośrednictwem przeglądarek internetowych Windows internetowych
keywords: ochrona sieci Web, ochrona przed zagrożeniami internetowymi, przeglądanie Internetu, alerty, odpowiedź, zabezpieczenia, wyłudzanie informacji, złośliwe oprogramowanie, exploit, witryny internetowe, ochrona sieci, Edge, Internet Explorer, Chrome, Firefox, przeglądarka internetowa, powiadomienia, użytkownicy końcowi, powiadomienia Windows, blokowanie strony,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3a7202c6e522441ecbbfd738d3533a242c966f8c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467538"
---
# <a name="respond-to-web-threats"></a>Reagowanie na zagrożenia w sieci Web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Ochrona sieci Web w programie Ochrona punktu końcowego w usłudze Microsoft Defender umożliwia efektywne badanie i odpowiadanie na alerty dotyczące złośliwych witryn internetowych i witryn internetowych na niestandardowej liście wskaźników.

## <a name="view-web-threat-alerts"></a>Wyświetlanie alertów o zagrożeniach w sieci Web

Ochrona punktu końcowego w usłudze Microsoft Defender generuje następujące [alerty dotyczące](manage-alerts.md) złośliwej lub podejrzanej aktywności w sieci Web:

- **Podejrzane połączenie zablokowane** przez ochronę sieci: Ten alert jest generowany, gdy próba uzyskania dostępu do złośliwej witryny lub witryny internetowej na niestandardowej liście wskaźników zostanie  zatrzymana przez ochronę sieci w *trybie blokowania*
- **Podejrzane połączenie wykryte przez** ochronę sieci: Ten alert jest generowany, gdy próba uzyskania dostępu do złośliwej witryny lub witryny internetowej na niestandardowej liście wskaźników jest wykrywana przez ochronę sieci w trybie *tylko inspekcji*

Każdy alert zawiera następujące informacje:

- Urządzenie, które próbowało uzyskać dostęp do zablokowanej witryny internetowej
- Aplikacja lub program użyty do wysłania żądania sieci Web
- Złośliwy adres URL lub adres URL na niestandardowej liście wskaźników
- Zalecane działania dla osób odpowiadających

:::image type="content" source="images/wtp-alert.png" alt-text="Alert związany z ochroną przed zagrożeniami w sieci Web" lightbox="images/wtp-alert.png":::

> [!NOTE]
> Aby zmniejszyć liczbę alertów, Ochrona punktu końcowego w usłudze Microsoft Defender każdego dnia konsoliduje wykrywanie zagrożeń sieci Web dla tej samej domeny na tym samym urządzeniu do jednego alertu. W raporcie ochrony sieci Web jest generowany i liczony tylko [jeden alert](web-protection-monitoring.md).

## <a name="inspect-website-details"></a>Sprawdzanie szczegółów witryny sieci Web

Możesz przejść do bardziej dogłębnych danych, wybierając adres URL lub domenę witryny internetowej w alercie. Spowoduje to otwarcie strony dotyczącej tego konkretnego adresu URL lub domeny z różnymi informacjami, między innymi:

- Urządzenia, które próbowały uzyskać dostęp do witryny internetowej
- Zdarzenia i alerty związane z witryną internetową
- Jak często witryna sieci Web była widziana w zdarzeniach w organizacji

  :::image type="content" source="images/wtp-website-details.png" alt-text="Strona szczegółów domeny lub adresu URL encji" lightbox="images/wtp-website-details.png":::

[Dowiedz się więcej o adresie URL lub stronach encji domeny](investigate-domain.md)

## <a name="inspect-the-device"></a>Sprawdzanie urządzenia

Możesz również sprawdzić urządzenie, które próbowało uzyskać dostęp do zablokowanego adresu URL. Wybranie nazwy urządzenia na stronie alertu spowoduje otwarcie strony z kompletnymi informacjami o urządzeniu.

[Dowiedz się więcej o stronach encji urządzenia](investigate-machines.md)

## <a name="web-browser-and-windows-notifications-for-end-users"></a>Przeglądarka internetowa i powiadomienia Windows dla użytkowników końcowych

Ochrona sieci Web w Ochrona punktu końcowego w usłudze Microsoft Defender sieci Web uniemożliwi użytkownikom końcowy odwiedzanie złośliwych lub niechcianych witryn internetowych za pomocą Microsoft Edge lub innych przeglądarek. Ponieważ blokowanie jest wykonywane przez [ochronę sieci](network-protection.md), pojawi się błąd ogólny z przeglądarki sieci Web. Zobaczą też powiadomienie od Windows.

:::image type="content" source="images/wtp-browser-blocking-page.png" alt-text="Komunikat Microsoft Edge z komunikatem o błędzie 403 i Windows powiadomieniami o błędzie" lightbox="images/wtp-browser-blocking-page.png":::

*Zagrożenia internetowe zablokowane na Microsoft Edge*

:::image type="content" source="images/wtp-chrome-browser-blocking-page.png" alt-text="Przeglądarka Internetowa Chrome z ostrzeżeniem o bezpiecznym połączeniu oraz powiadomieniem o Windows sieci Web" lightbox="images/wtp-chrome-browser-blocking-page.png":::
*Zagrożenia internetowe zablokowane w przeglądarce Chrome*

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie ochrony sieci Web](web-protection-overview.md)
- [Filtrowanie zawartości sieci Web](web-content-filtering.md)
- [Ochrona przed zagrożeniami internetowymi](web-threat-protection.md)
- [Monitorowanie zabezpieczeń sieci Web](web-protection-monitoring.md)
