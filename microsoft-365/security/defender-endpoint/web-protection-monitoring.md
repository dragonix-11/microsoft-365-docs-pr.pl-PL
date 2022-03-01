---
title: Monitorowanie zabezpieczeń przeglądania Internetu w programie Microsoft Defender dla punktu końcowego
description: Monitorowanie zabezpieczeń przeglądania Internetu za pomocą ochrony sieci Web w programie Microsoft Defender for Endpoint
keywords: ochrona sieci Web, ochrona przed zagrożeniami internetowymi, przeglądanie Internetu, monitorowanie, raporty, karty, lista domen, zabezpieczenia, wyłudzanie informacji, złośliwe oprogramowanie, exploit, witryny internetowe, ochrona sieci, Edge, Internet Explorer, Chrome, Firefox, przeglądarka internetowa
search.appverid: met150
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
ms.openlocfilehash: 6d10354f68dd5ba26db7f4260425559167c8888c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "63007880"
---
# <a name="monitor-web-browsing-security"></a>Monitorowanie zabezpieczeń przeglądania Internetu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Ochrona sieci Web umożliwia monitorowanie zabezpieczeń przeglądania sieci Web organizacji za pomocą raportów w obszarze Raporty **> ochrony sieci Web** w portalu Microsoft 365 Defender sieci Web. Raport zawiera karty zawierające statystyki wykrywania zagrożeń w sieci Web.

- **Wykrywanie zagrożeń internetowych z** czasem — na tej popularnej karcie jest wyświetlana liczba zagrożeń internetowych wykrytych według typu w wybranym okresie (Ostatnie 30 dni, Ostatnie 3 miesiące, Ostatnie 6 miesięcy)

  :::image type="content" alt-text="Obraz karty pokazującej wykrywanie zagrożeń internetowych w czasie." source="images/wtp-blocks-over-time.png" lightbox="images/wtp-blocks-over-time.png":::

- **Podsumowanie ochrony przed zagrożeniami** internetowymi — na tej karcie jest wyświetlana całkowita liczba wykrycia zagrożeń internetowych w ciągu ostatnich 30 dni, przedstawiająca rozkład między różnymi typami zagrożeń internetowych. Zaznaczenie wycinka powoduje otwarcie listy domen znalezionych razem ze złośliwymi lub niechcianymi witrynami sieci Web.

  :::image type="content" alt-text="Obraz przedstawiający kartę z podsumowaniem ochrony przed zagrożeniami internetowymi." source="images/wtp-summary.png" lightbox="images/wtp-summary.png":::

> [!NOTE]
> Może upłynie do 12 godzin, zanim blokadę odzwierciedli się na kartach lub na liście domen.

## <a name="types-of-web-threats"></a>Typy zagrożeń w sieci Web

Ochrona sieci Web kategoryzuje złośliwe i niechciane witryny internetowe w następujący sposób:

- **Wyłudzanie** informacji — witryny internetowe zawierające sfałszowane formularze sieci Web i inne mechanizmy wyłudzania informacji mające na celu nakłodzenie użytkowników do rozpowszechniania poświadczeń i innych informacji poufnych
- **Złośliwe witryny** internetowe hostowe złośliwe oprogramowanie i wykorzystujące kod
- **Wskaźnik niestandardowy** — witryny sieci Web, których adresy URL lub domeny zostały dodane do Twojej [niestandardowej listy wskaźników w](manage-indicators.md) celu blokowania

## <a name="view-the-domain-list"></a>Wyświetlanie listy domen

Wybierz konkretną kategorię zagrożeń internetowych na karcie podsumowania ochrony przed **zagrożeniami** internetowymi, aby otworzyć **stronę** Domeny. Na tej stronie jest wyświetlana lista domen w tej kategorii zagrożeń. Strona zawiera następujące informacje dla każdej domeny:

- **Liczba dostępu** — liczba żądań adresów URL w domenie
- **Bloki** — liczba zablokowanych żądań
- **Trend programu Access** — zmiana liczby prób dostępu
- **Kategoria Zagrożenia** — typ zagrożenia w sieci Web
- **Urządzenia** — liczba urządzeń z próbami dostępu

Wybierz domenę, aby wyświetlić listę urządzeń, które próbowały uzyskać dostęp do adresów URL w tej domenie, oraz listę adresów URL.

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie ochrony sieci Web](web-protection-overview.md)
- [Filtrowanie zawartości sieci Web](web-content-filtering.md)
- [Ochrona przed zagrożeniami internetowymi](web-threat-protection.md)
- [Reagowanie na zagrożenia w sieci Web](web-protection-response.md)
