---
title: Zalecenia dotyczące zabezpieczeń przez Zarządzanie zagrożeniami i lukami
description: Uzyskaj zalecenia dotyczące zabezpieczeń z akcjami określone pod względami zagrożenia, prawdopodobieństwa naruszenia zabezpieczeń i wartości w Zarządzanie zagrożeniami i lukami.
keywords: Zarządzanie zagrożeniami i lukami, Ochrona punktu końcowego w usłudze Microsoft Defender, zalecenie dotyczące bezpieczeństwa tvm, zalecenie dotyczące bezpieczeństwa, zalecenie dotyczące akcji
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
ms.openlocfilehash: e7ff7a98e8550996068686b5b0805ea3a72cd6ae
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468572"
---
# <a name="security-recommendations---threat-and-vulnerability-management"></a>Zalecenia dotyczące zabezpieczeń — Zarządzanie zagrożeniami i lukami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Braki chwalone w organizacji są mapowane na zalecenia dotyczące zabezpieczeń z akcjami i priorytetyzowane na ich wpływ. Zalecenia z określonymi priorytetami pomagają skrócić czas, aby zminimalizować luki w zabezpieczeniach lub je rozwiązać oraz ułatwić zapewnienie zgodności z przepisami.

Każde zalecenie dotyczące zabezpieczeń zawiera kroki rozwiązywania problemów z działaniami. W celu pomocy w zarządzaniu zadaniami można również wysłać Microsoft Intune zadania Microsoft Endpoint Configuration Manager. Gdy zmienia się poziom zagrożeń, zalecenie zmienia się również w momencie, gdy stale zbiera informacje z Twojego środowiska.

> [!TIP]
> Aby uzyskać wiadomości e-mail dotyczące nowych zdarzeń luk w zabezpieczeniach, zobacz [Konfigurowanie powiadomień e-mail dotyczących luk w zabezpieczeniach w programie Ochrona punktu końcowego w usłudze Microsoft Defender](configure-vulnerability-email-notifications.md)

## <a name="how-it-works"></a>Jak to działa

Każde urządzenie w organizacji jest zdobywane na podstawie trzech istotnych czynników, które ułatwiają klientom skoncentrowanie się we właściwym czasie na właściwych rzeczach.

- **Zagrożenie**: cechy luk i wykorzystania w urządzeniach organizacji oraz historia naruszenia. Na podstawie tych czynników w zaleceniach dotyczących zabezpieczeń są wyświetlane odpowiadające im linki do aktywnych alertów, trwających kampanii na temat zagrożeń i odpowiadających im raportów analitycznych dotyczących zagrożeń.
- **Prawdopodobieństwo naruszenia**: zapewnianie przez Twoją organizację zabezpieczeń i odporność przed zagrożeniami.
- **Wartość biznesowa**: zasoby organizacji, krytyczne procesy i właściwości intelektualnej.

## <a name="navigate-to-the-security-recommendations-page"></a>Przechodzenie do strony Zalecenia dotyczące zabezpieczeń

Uzyskaj dostęp do strony Zalecenia dotyczące zabezpieczeń na kilka różnych sposobów:

- Threat and zarządzanie lukami w zabezpieczeniach navigation menu in the [Microsoft 365 Defender portal](portal-overview.md)
- Najważniejsze zalecenia dotyczące zabezpieczeń na [pulpicie Zarządzanie zagrożeniami i lukami nawigacyjnym](tvm-dashboard-insights.md)

Wyświetl pokrewne zalecenia dotyczące zabezpieczeń w następujących miejscach:

- Strona oprogramowania
- Strona urządzenia

### <a name="navigation-menu"></a>Menu nawigacji

Przejdź do menu **nawigacji Zarządzania lukami** w zabezpieczeniach i wybierz pozycję **Rekomendacje**. Strona zawiera listę zaleceń dotyczących zabezpieczeń dotyczących zagrożeń i luk w zabezpieczeniach w organizacji.

### <a name="top-security-recommendations-in-the-threat-and-vulnerability-management-dashboard"></a>Najważniejsze zalecenia dotyczące zabezpieczeń na pulpicie Zarządzanie zagrożeniami i lukami nawigacyjnym

Jeśli jesteś administratorem zabezpieczeń w danym dniu, możesz sprawdzić na pulpicie nawigacyjnym [](tvm-dashboard-insights.md) Zarządzanie zagrożeniami i lukami, aby wyświetlić wyniki ekspozycji obok [](tvm-exposure-score.md) wyniku bezpiecznego wyniku działania firmy Microsoft dla [urządzeń](tvm-microsoft-secure-score-devices.md). Celem tego **jest obniżenie poziomu** ochrony organizacji przed lukami w zabezpieczeniach oraz zwiększenie  bezpieczeństwa urządzeń organizacji w celu większej odporności na ataki zagrożenia bezpieczeństwa bezpieczeństwa. Górna lista zaleceń dotyczących zabezpieczeń może pomóc w osiągnięciu tego celu.

:::image type="content" source="images/top-security-recommendations350.png" alt-text="Karta Najważniejsze zalecenia dotyczące zabezpieczeń" lightbox="images/top-security-recommendations350.png":::


W najważniejszych zaleceniach dotyczących zabezpieczeń wymieniono możliwości doskonalenia priorytetyzowane na podstawie ważnych czynników wymienionych w poprzedniej sekcji: zagrożenia, prawdopodobieństwa naruszenia i wartości. Wybranie zalecenia spowoduje przysłanie strony zaleceń dotyczących zabezpieczeń ze szczegółami.

## <a name="security-recommendations-overview"></a>Omówienie zaleceń dotyczących zabezpieczeń

Wyświetl zalecenia, liczbę odnalezionych braków, pokrewne składniki, szczegółowe informacje o zagrożeniach, liczbę naświetlonych urządzeń, stan, typ działań naprawczych, działania naprawcze, wpływ na ocenę ekspozycji i bezpiecznego wyniku działania firmy Microsoft dla urządzeń i skojarzone tagi.

Kolor wykresu **Naświetlone urządzenia** zmienia się wraz ze zmianami trendu. Jeśli liczba ujawnionych urządzeń rośnie, kolor zmienia się na czerwony. Jeśli liczba ujawnionych urządzeń się zmniejszy, kolor wykresu zmieni się na zielony.

> [!NOTE]
> Zagrożenia i zarządzanie lukami w zabezpieczeniach urządzenia, które były używania do **30** dni temu. To urządzenie różni się od Ochrona punktu końcowego w usłudze Microsoft Defender, jeśli urządzenie nie było używane przez ponad 7 dni, ma status "Nieaktywny".

:::image type="content" source="images/tvmsecrec-updated.png" alt-text="Strona docelowa w celu zalecenia zabezpieczeń" lightbox="images/tvmsecrec-updated.png":::

### <a name="icons"></a>Ikony

Przydatne ikony także szybko zwracają Twoją uwagę na:

- ![naciśnięcie obiektu docelowego.](images/tvm_alert_icon.png) Możliwe aktywne alerty
- ![czerwona usterka.](images/tvm_bug_icon.png) skojarzone wykorzystywanie publiczne
- ![żarówka.](images/tvm_insight_icon.png) informacje o zaleceniach

### <a name="explore-security-recommendation-options"></a>Eksplorowanie opcji zaleceń zabezpieczeń

Wybierz zalecenie zabezpieczeń, które chcesz zbadać lub przetworzyć.

:::image type="content" source="images/secrec-flyouteolsw.png" alt-text="Wysuwana strona zalecenia zabezpieczeń" lightbox="images/secrec-flyouteolsw.png":::

W wysuwanych menu możesz wybrać dowolną z następujących opcji:

- **Otwórz stronę oprogramowania** — otwórz stronę oprogramowania, aby uzyskać więcej kontekstu na oprogramowaniu i sposób jego rozpowszechniania. Informacje te mogą obejmować kontekst zagrożeń, skojarzone zalecenia, wykryte wady, liczbę wykrytych urządzeń, wykryte luki w zabezpieczeniach, nazwy i szczegółowe informacje o urządzeniach z zainstalowanym oprogramowaniem oraz rozpowszechnianie wersji.

- [**Opcje rozwiązywania problemów**](tvm-remediation.md) — prześlij żądanie naprawy w celu otwarcia biletu w Microsoft Intune, aby administrator IT odebrał i zaadresować zgłoszenie. Śledzenie działań naprawczych na stronie Działania naprawcze.

- [**Opcje wyjątków**](tvm-exception.md) — prześlij wyjątek, podaj uzasadnienie i ustaw czas trwania wyjątku, jeśli nie możesz jeszcze rozwiązać problemu.

> [!NOTE]
> W przypadku zmiany oprogramowania na urządzeniu z systemem Windows, Linux lub macOS zazwyczaj odzwierciedlenie danych w portalu zabezpieczeń trwa 2–4 godziny. Odzwierciedlenia zmian na urządzeniach z systemami iOS i Android może potrwać do 8 godzin. Mogą się jednak pojawić sytuacje, w których trwa to dłużej.
> 
> Zmiany konfiguracji mogą trwać od 4 do 24 godzin.

### <a name="investigate-changes-in-device-exposure-or-impact"></a>Badanie zmian w ekspozycji na urządzenie lub wpływie na urządzenie

Jeśli liczba ujawnionych urządzeń znacznie się zwiększy lub zwiększy wpływ na ocenę ekspozycji Twojej organizacji i ocenę bezpieczeństwa firmy Microsoft dla urządzeń, wówczas warto zbadać to zalecenie dotyczące zabezpieczeń.

1. Wybierz zalecenie i **otwórz stronę oprogramowania**
2. Wybierz **kartę Oś czasu** zdarzenia, aby wyświetlić wszystkie efektowne zdarzenia związane z tym oprogramowaniem, takie jak nowe luki w zabezpieczeniach lub nowe luki w zabezpieczeniach publicznych. [Dowiedz się więcej o osi czasu zdarzenia](threat-and-vuln-mgt-event-timeline.md)
3. Zdecyduj, jak rozwiązać ten wzrost lub czas organizacji, na przykład jak przesłać żądanie podjęcia działań naprawczych

## <a name="request-remediation"></a>Żądanie środków zaradczych

Działania Zarządzanie zagrożeniami i lukami zasypuje przerwy między zabezpieczeniami i administratorami IT za pośrednictwem przepływu pracy żądania zaradczego. Administratorzy zabezpieczeń, na przykład ty, mogą poprosić administratora IT o naprawienie luki na stronie zalecenia **zabezpieczeń w celu** Intune. [Dowiedz się więcej o opcjach rozwiązywania problemów](tvm-remediation.md)

### <a name="how-to-request-remediation"></a>Jak zażądać środków zaradczych

Wybierz zalecenie zabezpieczeń, dla których chcesz zażądać środków zaradczych, a następnie wybierz pozycję **Opcje rozwiązywania problemów**. Wypełnij formularz i wybierz pozycję **Prześlij żądanie**. Przejdź na stronę [**Działania naprawcze**](tvm-remediation.md) , aby wyświetlić stan żądania naprawy. [Dowiedz się więcej na temat żądania środków zaradczych](tvm-remediation.md#request-remediation)

## <a name="file-for-exception"></a>Plik wyjątku

Alternatywą dla żądania rozwiązania problemów, gdy w danej chwili zalecenie nie jest istotne, możesz utworzyć wyjątki dla zaleceń. [Dowiedz się więcej o wyjątkach](tvm-exception.md)

Wyjątkiem mogą być tylko użytkownicy z uprawnieniami do obsługi wyjątków. [Dowiedz się więcej o rolach RBAC](user-roles.md).

Gdy dla zalecenia jest tworzony wyjątek, zalecenie nie jest już aktywne. Stan zalecenia zmieni się na **Pełny wyjątek** lub **Częściowy wyjątek** (według grupy urządzeń).

### <a name="how-to-create-an-exception"></a>Jak utworzyć wyjątek

Wybierz zalecenie dotyczące zabezpieczeń, dla których chcesz utworzyć wyjątek, a następnie wybierz pozycję **Opcje wyjątków**.

:::image type="content" source="images/tvm-exception-options.png" alt-text="Przycisk opcji wyjątków w wysuwanych poleceniach zabezpieczeń" lightbox="images/tvm-exception-options.png":::

Wypełnij formularz i prześlij. Aby wyświetlić wszystkie wyjątki (bieżącą i przeszłe), przejdź [](tvm-remediation.md) do strony Działania naprawcze w menu Zarządzanie & zagrożeniami i lukami w zabezpieczeniach, **a** następnie wybierz kartę **Wyjątki**. Dowiedz się więcej na temat tworzenia [wyjątku.](tvm-exception.md#create-an-exception)

## <a name="report-inaccuracy"></a>Nieścisłości raportu

Jeśli zostaną wyświetlony niejasne, niejasne, niedokładne, niepełne lub już usunięte informacje dotyczące zaleceń dotyczących zabezpieczeń, możesz zgłosić wynik fałszywie dodatni.

1. Otwórz zalecenie dotyczące zabezpieczeń.

2. Wybierz trzy kropki obok zalecenia zabezpieczeń, które chcesz zgłosić, a następnie wybierz pozycję Zgłoś **nieścisłości**.

   :::image type="content" source="images/report-inaccuracy500.png" alt-text="Przycisk Nieścisłości raportu" lightbox="images/report-inaccuracy500.png":::

3. W okienku wysuwu wybierz kategorię nieścisłości z menu rozwijanego, wprowadź swój adres e-mail i szczegóły dotyczące nieścisłości.

4. Wybierz **pozycję Prześlij**. Twoja opinia zostanie natychmiast przesłana do Zarządzanie zagrożeniami i lukami ekspertów.

## <a name="related-articles"></a>Artykuły pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Pulpit nawigacyjny](tvm-dashboard-insights.md)
- [Wynik ekspozycji](tvm-exposure-score.md)
- [Microsoft Secure Score dla urządzeń](tvm-microsoft-secure-score-devices.md)
- [Usuwanie luk w zabezpieczeniach](tvm-remediation.md)
- [Tworzenie i wyświetlanie wyjątków dla zaleceń dotyczących zabezpieczeń](tvm-exception.md)
- [Oś czasu zdarzenia](threat-and-vuln-mgt-event-timeline.md)
