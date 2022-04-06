---
title: Luki w zabezpieczeniach w mojej organizacji — Zarządzanie zagrożeniami i lukami
description: Lista typowych luk i ekspozycji (CVE, Common Vulnerabilits) identyfikatorów luk w zabezpieczeniach, które można znaleźć w oprogramowaniu uruchomionym w organizacji. Możliwość wykrywania Ochrona punktu końcowego w usłudze Microsoft Defender Zarządzanie zagrożeniami i lukami danych.
keywords: Ochrona punktu końcowego w usłudze Microsoft Defender zagrożenia & zarządzanie lukami w zabezpieczeniach, Zarządzanie zagrożeniami i lukami, Ochrona punktu końcowego w usłudze Microsoft Defender strona luk w zabezpieczeniach programu tvm, znalezienie luk w zabezpieczeniach programu tvm, lista luk w zabezpieczeniach programu tvm, szczegóły luk w zabezpieczeniach programu tvm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a2f3db3a28755c5e2bce46f7134eb1c977d1aa0a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476648"
---
# <a name="vulnerabilities-in-my-organization---threat-and-vulnerability-management"></a>Luki w zabezpieczeniach w mojej organizacji — Zarządzanie zagrożeniami i lukami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!IMPORTANT]
> Zagrożenia i zarządzanie lukami w zabezpieczeniach mogą pomóc w zidentyfikowaniu luk w log4j w aplikacjach i składnikach. [Dowiedz się więcej](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/#TVM).

Zagrożenia i zarządzanie lukami w zabezpieczeniach wykorzystujące te same sygnały w programie Defender na temat ochrony punktu końcowego w celu skanowania i wykrycia luk.

Strona **Słabe zawiera** listę luk w oprogramowaniu, jakie mogą przed to zrobić Twoje urządzenia, wyszczególnione w identyfikatorze Common Vulnerabilities and Exposures (CVE). Możesz również przejrzeć oceny ważności, wspólnego systemu oceniania luk, ochrony przed zagrożeniami itp.

> [!NOTE]
> Jeśli do luki nie przypisano oficjalnego identyfikatora CVE, nazwa luki w zabezpieczeniach jest przypisywana przez Zarządzanie zagrożeniami i lukami.

> [!TIP]
> Aby uzyskać wiadomości e-mail dotyczące nowych zdarzeń luk w zabezpieczeniach, zobacz [Konfigurowanie powiadomień e-mail dotyczących luk w zabezpieczeniach w programie Ochrona punktu końcowego w usłudze Microsoft Defender](configure-vulnerability-email-notifications.md)

## <a name="navigate-to-the-weaknesses-page"></a>Przejdź do strony Braki

Uzyskaj dostęp do strony Braki na kilka różnych sposobów:

- Wybieranie **opcji Słabe** z menu **nawigacji zarządzania** lukami w portalu Microsoft 365 Defender [luk](portal-overview.md)
- Wyszukiwanie globalne

### <a name="navigation-menu"></a>Menu nawigacji

Przejdź do menu **nawigacji zarządzania lukami** w zabezpieczeniach i wybierz pozycję **Słabe,** aby otworzyć listę CW.

### <a name="vulnerabilities-in-global-search"></a>Luki w zabezpieczeniach wyszukiwanie globalne

1. Przejdź do wyszukiwanie globalne rozwijanego.
2. Wybierz **lukę i** klucz w identyfikatorze Typowe luki w zabezpieczeniach i ekspozycje (CVE, Common Vulnerabilities and Exposures), którego szukasz, a następnie wybierz ikonę wyszukiwania. Zostanie **otwarta strona** Braki z informacjami CVE, których szukasz.

:::image type="content" source="images/tvm-vuln-globalsearch.png" alt-text="Pole wyszukiwania globalnego z zaznaczoną luką w opcji listy rozwijanej" lightbox="images/tvm-vuln-globalsearch.png":::

3. Wybierz opcję CVE, aby otworzyć panel wysuwu z większej liczby informacji, takich jak opis luki w zabezpieczeniach, szczegóły, szczegółowe informacje o zagrożeniach i ujawnione urządzenia.

Aby zobaczyć pozostałe luki na stronie Braki, wpisz  CVE, a następnie wybierz pozycję wyszukaj.

## <a name="weaknesses-overview"></a>Omówienie braków

Zaradcze w przypadku luk w zabezpieczeniach w ujawnionych urządzeniach w celu zmniejszenia ryzyka dla twoich zasobów i organizacji. Jeśli w **kolumnie Dostępne urządzenia** jest pokazana 0, oznacza to, że nie jest to ryzykowne.

:::image type="content" source="images/tvm-weaknesses-overview.png" alt-text="Strona docelowa Braki" lightbox="images/tvm-weaknesses-overview.png":::

### <a name="breach-and-threat-insights"></a>Analiza naruszenia i zagrożeń

Wyświetlaj wszelkie związane z tym informacje o naruszeniach zabezpieczeń i zagrożeniach w kolumnie **Zagrożenia,** gdy ikony mają kolor czerwony.

 > [!NOTE]
 > Zawsze priorytetyzuj zalecenia związane z bieżącymi zagrożeniami. Te zalecenia są oznaczone ikoną szczegółowej informacji o zagrożeniach ![Prosty rysunek czerwonej usterki.](images/tvm_bug_icon.png) Ikona analizy naruszenia prostego ![rysunku strzałki trafiacej do celu](images/tvm_alert_icon.png).

Ikona analizy naruszenia jest wyróżniona, jeśli w organizacji istnieje luka.
![Przykład tekstu informacji o naruszeniu, który może się pojawiać po umieszczeniu wskaźnika myszy na ikonie. Jest to komunikat "Z tym zaleceniem jest skojarzony możliwy aktywny alert.](images/tvm-breach-insights.png)

Ikona Szczegółowych informacji o zagrożeniach jest wyróżniona, jeśli skojarzona z nim luka w zabezpieczeniach, która znajduje się w organizacji. Umieszczenie wskaźnika myszy na ikonie wskazuje, czy zagrożenie jest elementem zestawu wykorzystującego luki, czy związane z określonymi zaawansowanymi trwałymi kampaniami lub grupami działań. Jeśli jest to możliwe, dostępny jest link do raportu analizy zagrożeń z wiadomościami o zerowej wykorzystywaniu, ujawnianiu informacji i powiązanych poradach dotyczących zabezpieczeń.

![Wiadomość z analizą zagrożeń, która może być wyświetlana po umieszczeniu wskaźnika myszy na ikonie. Ten ma wiele punktów punktorów i tekst połączony.](images/tvm-threat-insights.png)

### <a name="gain-vulnerability-insights"></a>Zdobywanie luk w zabezpieczeniach

Jeśli wybierzesz opcję CVE, zostanie otwarty panel wysuwu z większej liczby informacji, takich jak opis luki w zabezpieczeniach, szczegóły, szczegółowe informacje o zagrożeniach i ujawnione urządzenia.

- Kategoria "Funkcja systemu operacyjnego" jest wyświetlana w odpowiednich scenariuszach
- Możesz przejść do pokrewnego zalecenia zabezpieczeń dla każdego CVE z ujawnionym urządzeniem

 :::image type="content" source="images/tvm-weakness-flyout400.png" alt-text="Strona opisu luki w zabezpieczeniach" lightbox="images/tvm-weakness-flyout400.png":::

### <a name="software-that-isnt-supported"></a>Oprogramowanie, które nie jest obsługiwane

W przypadku oprogramowania, które nie jest obecnie obsługiwane przez zagrożenia, & zarządzanie lukami w zabezpieczeniach nadal występuje na stronie Braki. Ponieważ to oprogramowanie nie jest obsługiwane, dostępne będą tylko ograniczone dane.

Udostępniane informacje o urządzeniach nie będą dostępne w programach CWI z nieobsługiwanym oprogramowaniem. Filtruj według nieobsługiwanego oprogramowania, wybierając opcję "Niedostępne" w sekcji "Dostępne urządzenia".

:::image type="content" alt-text="Widoczne urządzenia filtru." source="images/tvm-exposed-devices-filter.png":::

## <a name="view-common-vulnerabilities-and-exposures-cve-entries-in-other-places"></a>Wyświetlanie typowych luk i naświetleń (CVE) w innych miejscach

### <a name="top-vulnerable-software-in-the-dashboard"></a>Najbardziej narażone oprogramowanie na pulpicie nawigacyjnym

1. Przejdź do [pulpitu Zarządzanie zagrożeniami i lukami i](tvm-dashboard-insights.md) przewiń w dół do **widżetu oprogramowania, który jest** najbardziej narażony na zagrożenia. Zobaczysz liczbę luk w zabezpieczeniach znalezionych w poszczególnych oprogramowaniu, a także informacje o zagrożeniach i wysokopoziomowy widok informacji o narażeniu na urządzenia w czasie.

   :::image type="content" source="images/tvm-top-vulnerable-software500.png" alt-text="Kolumna Słabe na stronie oprogramowanie, która jest podatna na zagrożenia" lightbox="images/tvm-top-vulnerable-software500.png":::

2. Wybierz oprogramowanie, które chcesz zbadać, aby przejść do strony szczegółów.

3. Wybierz **kartę Wykryj luki** .

4. Wybierz lukę w zabezpieczeniach, którą chcesz zbadać, aby uzyskać więcej informacji na temat luk w zabezpieczeniach

   :::image type="content" source="images/windows-server-drilldown.png" alt-text="Omówienie Windows Server 2019" lightbox="images/windows-server-drilldown.png":::

### <a name="discover-vulnerabilities-in-the-device-page"></a>Odnajdowanie luk na stronie urządzenia

Wyświetlanie powiązanych informacji na stronie urządzenia.

1. Przejdź do paska Microsoft 365 Defender nawigacji, a następnie wybierz ikonę urządzenia. Zostanie **otwarta strona Spis** urządzeń.

2. Na stronie **Spis urządzeń** wybierz nazwę urządzenia, które chcesz zbadać.

   :::image type="content" source="images/tvm_machinetoinvestigate.png" alt-text="Lista Urządzenie z wybranym urządzeniem do zbadania" lightbox="images/tvm_machinetoinvestigate.png":::

3. Zostanie otwarta strona urządzenia ze szczegółami i opcjami odpowiedzi dla urządzenia, które chcesz zbadać.

4. Wybierz **pozycję Wykryj luki w zabezpieczeniach**.

   :::image type="content" source="images/tvm-discovered-vulnerabilities.png" alt-text="Strona Urządzenie ze szczegółami i opcjami odpowiedzi." lightbox="images/tvm-discovered-vulnerabilities.png":::

5. Wybierz lukę, którą chcesz zbadać, aby otworzyć panel wysuwu z informacjami typu CVE, takimi jak opis luki w zabezpieczeniach, analiza zagrożeń i logika wykrywania.

#### <a name="cve-detection-logic"></a>Logika wykrywania CVE

Podobnie jak w przypadku dowodów z oprogramowania, pokazujemy teraz logikę wykrywania zastosowaną na urządzeniu, aby było wiadomo, że jest podatny na zagrożenia. Nowa sekcja nosi nazwę "Logika wykrywania" (w przypadku wszelkich wykrytych luk na stronie urządzenia) i zawiera logikę oraz źródło wykrywania.

Kategoria "Funkcja systemu operacyjnego" jest również wyświetlana w odpowiednich scenariuszach. Funkcja CVE dotyczy urządzeń, na których działa narażony system operacyjny, tylko w przypadku, gdy jest włączony określony składnik systemu operacyjnego. Załóżmy, że Windows Server 2019 lub Windows Server 2022 ma lukę w jego składniku DNS. Dzięki tej nowej funkcji dołączymy ten kod CVE tylko do urządzeń z systemami Windows Server 2019 i Windows Server 2022 z włączoną możliwością DNS w ich systemie operacyjnym.

:::image type="content" source="images/tvm-cve-detection-logic.png" alt-text="Przykład logiki wykrywania, który zawiera listę oprogramowania wykrytego na urządzeniu i kb/s" lightbox="images/tvm-cve-detection-logic.png":::

## <a name="report-inaccuracy"></a>Nieścisłości raportu

Zgłaszaj błędy fałszywie dodatnie, jeśli widzisz niejasne, nieprawidłowe lub niepełne informacje. Możesz również zgłaszać zalecenia dotyczące zabezpieczeń, które zostały już usunięte.

1. Otwórz oknem cve na stronie Słabe.
2. Wybierz **pozycję Nieścisłości raportu** , a zostanie otwarte okienko wysuwu.
3. Wybierz kategorię nieścisłości z menu rozwijanego i wprowadź swój adres e-mail oraz szczegóły nieścisłości.
4. Wybierz **pozycję Prześlij**. Twoja opinia zostanie natychmiast przesłana do Zarządzanie zagrożeniami i lukami ekspertów.

## <a name="related-articles"></a>Artykuły pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md)
- [Spis oprogramowania](tvm-software-inventory.md)
- [Szczegółowe informacje pulpitu nawigacyjnego](tvm-dashboard-insights.md)
- [Wyświetlanie i organizowanie listy Ochrona punktu końcowego w usłudze Microsoft Defender Urządzenia](machines-view-overview.md)
