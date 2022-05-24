---
title: Szczegółowe informacje i raportuje szkolenie dotyczące symulacji ataków
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak trenowanie symulacji ataków w portalu Microsoft 365 Defender wpływa na użytkowników i może uzyskiwać szczegółowe informacje na podstawie wyników symulacji i trenowania.
ms.technology: mdo
ms.openlocfilehash: 72ed46d1676f4abd97ecd4fccfe4ef20d971f0b3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649458"
---
# <a name="insights-and-reports-for-attack-simulation-training-in-defender-for-office-365"></a>Szczegółowe informacje i raporty dotyczące trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

W ramach trenowania symulacji ataków w usłudze Microsoft Defender dla Office Plan 2 lub Microsoft 365 E5 firma Microsoft udostępnia szczegółowe informacje i raporty z wyników symulacji i odpowiednich szkoleń. Te informacje informują o postępie gotowości użytkowników do zagrożeń, a także zalecają kolejne kroki, aby lepiej przygotować użytkowników do przyszłych ataków.

Szczegółowe informacje i raporty są dostępne w następujących miejscach w szkoleniu symulacji ataków w portalu Microsoft 365 Defender:

- Karta **Przegląd** .
- Szczegóły symulacji na **karcie Symulacje** .

W pozostałej części tego artykułu opisano dostępne informacje.

Aby uzyskać informacje o rozpoczęciu trenowania symulacji ataków, zobacz [Wprowadzenie korzystanie z trenowania symulacji ataków](attack-simulation-training-get-started.md).

## <a name="insights-and-reports-on-the-overview-tab-of-attack-simulation-training"></a>Szczegółowe informacje i raporty na karcie Omówienie trenowania symulacji ataków

Aby przejść do karty **Przegląd**, otwórz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>, przejdź do pozycji Email & collaboration **Attack simulation training (Trenowanie symulacji ataków** & **poczty** \> e-mail) i sprawdź, czy **wybrano kartę Przegląd** (jest to ustawienie domyślne). Aby przejść bezpośrednio do karty **Przegląd** na stronie **trenowania symulacji ataków** , użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=overview>.

W pozostałej części tej sekcji opisano informacje dostępne na karcie **Omówienie** trenowania symulacji ataków.

### <a name="recent-simulations-card"></a>Karta Ostatnio używane symulacje

Karta **Ostatnie symulacje** na karcie **Przegląd** przedstawia trzy ostatnie symulacje utworzone lub uruchomione w organizacji.

Możesz wybrać symulację, aby wyświetlić szczegóły.

Wybranie pozycji **Wyświetl wszystkie symulacje** spowoduje przejście na kartę **Symulacje** .

Wybranie pozycji **Uruchom symulację** powoduje uruchomienie kreatora tworzenia symulacji. Aby uzyskać więcej informacji, zobacz [Symulowanie ataku wyłudzania informacji w Ochrona usługi Office 365 w usłudze Defender](attack-simulation-training.md).

:::image type="content" source="../../media/attack-sim-training-overview-recent-simulations-card.png" alt-text="Karta Ostatnie symulacje na karcie Przegląd w szkoleniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-overview-recent-simulations-card.png":::

### <a name="behavior-impact-on-compromise-rate-card"></a>Wpływ zachowania na kartę szybkości naruszenia zabezpieczeń

Karta **Wpływ zachowania na wskaźnik naruszeń** na karcie **Przegląd** pokazuje, jak użytkownicy reagowali na symulacje w porównaniu z danymi historycznymi w Microsoft 365. Możesz użyć tych szczegółowych informacji, aby śledzić postęp gotowości użytkowników do korzystania z zagrożeń, uruchamiając wiele symulacji dla tych samych grup użytkowników.

Na samych danych wykresu przedstawiono następujące informacje:

- **Przewidywany współczynnik**<sup>\*</sup> kompromisów: średni wskaźnik kompromisów dla symulacji trenowania symulacji ataków, które używają tego samego typu ładunku we wszystkich innych organizacjach Microsoft 365.
- **Rzeczywisty wskaźnik**<sup>\*</sup> kompromisu: rzeczywisty odsetek użytkowników, którzy spadli na potrzeby symulacji.

Jeśli zatrzymasz kursor na punkcie danych na wykresie, zostaną wyświetlone rzeczywiste wartości procentowe.

Na karcie są również wyświetlane następujące informacje podsumowujące:

- **użytkownicy mniej podatni na wyłudzanie informacji**: różnica między rzeczywistą liczbą użytkowników zagrożonych symulowanym atakiem a przewidywanym wskaźnikiem naruszenia zabezpieczeń. Ta liczba użytkowników jest mniej prawdopodobne, że w przyszłości nastąpi naruszenie zabezpieczeń przez podobne ataki.
- **x% lepsze niż przewidywana szybkość**: wskazuje, jak użytkownicy radzili sobie ogólnie w przeciwieństwie do przewidywanego wskaźnika kompromisu.

:::image type="content" source="../../media/attack-sim-training-overview-behavior-impact-card.png" alt-text="Wpływ zachowania na kartę szybkości naruszenia zabezpieczeń na karcie Przegląd w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-overview-behavior-impact-card.png":::

Aby wyświetlić bardziej szczegółowy raport, kliknij pozycję **Wyświetl symulacje i raport skuteczności trenowania**. Ten raport został wyjaśniony [w dalszej części tego artykułu](#training-efficacy-tab-for-the-attack-simulation-report).

### <a name="simulation-coverage-card"></a>Karta pokrycia symulacji

Karta **Pokrycie symulacji** na karcie **Przegląd** pokazuje odsetek użytkowników w organizacji, którzy otrzymali symulację (**symulowanych użytkowników**) w porównaniu z tymi, którzy nie otrzymali symulacji (**użytkownicy niesymulowane**). Możesz zatrzymać kursor nad sekcją na wykresie, aby zobaczyć rzeczywistą liczbę użytkowników w każdej kategorii.

Wybranie pozycji **Uruchom symulację dla niesymulowanych użytkowników** uruchamia kreatora tworzenia symulacji, w którym użytkownicy, którzy nie otrzymali symulacji, są automatycznie wybierani na stronie **Użytkownik docelowy** . Aby uzyskać więcej informacji, zobacz [Symulowanie ataku wyłudzania informacji w Ochrona usługi Office 365 w usłudze Defender](attack-simulation-training.md).

Wybranie **pozycji Wyświetl raport pokrycia symulacji** spowoduje przejście do [karty Pokrycie użytkownika dla raportu symulacji ataku](#user-coverage-tab-for-the-attack-simulation-report).

:::image type="content" source="../../media/attack-sim-training-overview-sim-coverage-card.png" alt-text="Karta Pokrycie symulacji na karcie Przegląd w trenowaniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-overview-sim-coverage-card.png":::

### <a name="training-completion-card"></a>Karta ukończenia szkolenia

Karta **Ukończenie szkolenia** na karcie **Przegląd** organizuje odsetek użytkowników, którzy otrzymali szkolenia na podstawie wyników symulacji, w następujących kategoriach:

- **Zakończone**
- **W toku**
- **Niekompletna**

Możesz zatrzymać kursor nad sekcją na wykresie, aby zobaczyć rzeczywistą liczbę użytkowników w każdej kategorii.

Wybranie pozycji **Wyświetl raport ukończenia trenowania** spowoduje przejście do [karty Ukończenie szkolenia dla raportu symulacji ataku](#training-completion-tab-for-the-attack-simulation-report).

### <a name="repeat-offenders-card"></a>Karta recydywistów

Karta **Recydywistów** na karcie **Przegląd** zawiera informacje o recydywistach. _Recydywista_ jest użytkownikiem, który został naruszony przez kolejne symulacje. Domyślna liczba kolejnych symulacji to dwie, ale możesz zmienić wartość na karcie **Ustawienia** trenowania symulacji ataku pod adresem <https://security.microsoft.com/attacksimulator?viewid=setting>.

Wykres organizuje dane recydywisty według [typu symulacji](attack-simulation-training.md#select-a-social-engineering-technique):

- **Wszystkie**
- **Załącznik złośliwego oprogramowania**
- **Link do złośliwego oprogramowania**
- **Zbieranie poświadczeń**
- **Link w załącznikach**
- **Drive-by URL**

Wybranie pozycji **Wyświetl raport recydywisty** spowoduje przejście do [karty Recydywisty dla raportu symulacji ataku](#repeat-offenders-tab-for-the-attack-simulation-report).

### <a name="recommendations-card"></a>karta Rekomendacje

Karta **Rekomendacje** na karcie **Przegląd** sugeruje różne typy symulacji do uruchomienia.

Wybranie pozycji **Uruchom powoduje uruchomienie** kreatora tworzenia symulacji z wybranym automatycznie typem symulacji na stronie **Wybieranie techniki** . Aby uzyskać więcej informacji, zobacz [Symulowanie ataku wyłudzania informacji w Ochrona usługi Office 365 w usłudze Defender](attack-simulation-training.md).

:::image type="content" source="../../media/attack-sim-training-overview-recommendations-card.png" alt-text="Karta Rekomendacje na karcie Przegląd w szkoleniu symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-overview-recommendations-card.png":::

### <a name="attack-simulation-report"></a>Raport symulacji ataku

Raport **Symulacja ataku** można otworzyć na karcie **Przegląd** , klikając pozycję **Wyświetl... przyciski raportu** , które są dostępne w wielu kartach opisanych w tym artykule. Aby przejść bezpośrednio do raportu, użyj polecenia <https://security.microsoft.com/attacksimulationreport>

#### <a name="training-efficacy-tab-for-the-attack-simulation-report"></a>Karta Skuteczność trenowania dla raportu symulacji ataków

Na stronie **Raport symulacji ataku** domyślnie wybrano kartę **Skuteczność trenowania** . Ta karta zawiera te same informacje, które są dostępne w karcie **Wpływ zachowania na kartę szybkości naruszenia zabezpieczeń** , z dodatkowym kontekstem z samej symulacji.

:::image type="content" source="../../media/attack-sim-report-training-efficacy-view.png" alt-text="Karta Skuteczność trenowania w raporcie symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-report-training-efficacy-view.png":::

Na wykresie **przedstawiono przewidywaną szybkość naruszenia zabezpieczeń** i **rzeczywistą wskaźnik naruszona**. Jeśli umieścisz kursor nad sekcją na wykresie, zostaną wyświetlone rzeczywiste wartości procentowe.

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Nazwa symulacji**
- **Technika symulacji**
- **Taktyka symulacji**
- **Przewidywana szybkość naruszona**
- **Rzeczywista szybkość naruszona**
- **Łączna liczba docelowych użytkowników**
- **Liczba klikniętych użytkowników**

Wyniki można posortować, klikając dostępny nagłówek kolumny.

Kliknij **pozycję Dostosuj kolumny** , aby usunąć wyświetlane kolumny. Po zakończeniu kliknij przycisk **Zastosuj**.

Użyj ![ikony](../../media/m365-cc-sc-search-icon.png) **wyszukiwania Pole wyszukiwania** , aby filtrować wyniki według **nazwy symulacji** lub **techniki symulacji**. Symbole wieloznaczne nie są obsługiwane.

Jeśli klikniesz ikonę ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **Przycisk Eksportuj raport** , postęp generowania raportu jest wyświetlany jako procent ukończenia. W otwartym oknie dialogowym możesz otworzyć plik .csv, zapisać plik .csv i zapamiętać zaznaczenie.

#### <a name="user-coverage-tab-for-the-attack-simulation-report"></a>Karta Pokrycie użytkowników dla raportu symulacji ataków

:::image type="content" source="../../media/attack-sim-report-user-coverage-view.png" alt-text="Karta Pokrycie użytkownikami w raporcie symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-report-user-coverage-view.png":::

Na karcie **Pokrycie użytkownikami** na wykresie **przedstawiono symulowanych użytkowników** i **użytkowników niesymulowanych**. Jeśli umieścisz kursor nad punktem danych na wykresie, zostaną wyświetlone rzeczywiste wartości.

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Nazwa użytkownika**
- **Adres e-mail**
- **Uwzględnione w symulacji**
- **Data ostatniej symulacji**
- **Ostatni wynik symulacji**
- **Liczba klikniętych**
- **Liczba naruszeń zabezpieczeń**

Wyniki można posortować, klikając dostępny nagłówek kolumny.

Kliknij **pozycję Dostosuj kolumny** , aby usunąć wyświetlane kolumny. Po zakończeniu kliknij przycisk **Zastosuj**.

Użyj ![ikony](../../media/m365-cc-sc-search-icon.png) **wyszukiwania Pole wyszukiwania** , aby filtrować wyniki według **nazwy użytkownika** lub **adresu e-mail**. Symbole wieloznaczne nie są obsługiwane.

Jeśli klikniesz ikonę ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **Przycisk Eksportuj raport** , postęp generowania raportu jest wyświetlany jako procent ukończenia. W otwartym oknie dialogowym możesz otworzyć plik .csv, zapisać plik .csv i zapamiętać zaznaczenie.

#### <a name="training-completion-tab-for-the-attack-simulation-report"></a>Karta Ukończenie szkolenia dla raportu symulacji ataku

:::image type="content" source="../../media/attack-sim-report-training-completion-view.png" alt-text="Karta Ukończenie trenowania w raporcie symulacji ataków w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-report-training-completion-view.png":::

Na karcie **Ukończenie trenowania** na wykresie przedstawiono liczbę symulacji **Ukończono**, **W toku** i **Niekompletne** . Jeśli umieścisz kursor nad sekcją na wykresie, zostaną wyświetlone rzeczywiste wartości.

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Nazwa użytkownika**
- **Adres e-mail**
- **Uwzględnione w symulacji**
- **Data ostatniej symulacji**
- **Ostatni wynik symulacji**
- **Nazwa ostatniego ukończonego szkolenia**
- **Data ukończenia**
- **Wszystkie szkolenia**

Wyniki można posortować, klikając dostępny nagłówek kolumny.

Kliknij **pozycję Dostosuj kolumny** , aby usunąć wyświetlane kolumny. Po zakończeniu kliknij przycisk **Zastosuj**.

Kliknij ikonę ![Filtruj.](../../media/m365-cc-sc-filter-icon.png) **Filtruj** , aby filtrować tabelę wykresów i szczegółów według co najmniej jednej z następujących wartości:

- **Zakończone**
- **W toku**
- **Wszystkie**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Użyj ![ikony](../../media/m365-cc-sc-search-icon.png) **wyszukiwania Pole wyszukiwania** , aby filtrować wyniki według **nazwy użytkownika** lub **adresu e-mail**. Symbole wieloznaczne nie są obsługiwane.

Jeśli klikniesz ikonę ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **Przycisk Eksportuj raport** , postęp generowania raportu jest wyświetlany jako procent ukończenia. W otwartym oknie dialogowym możesz otworzyć plik .csv, zapisać plik .csv i zapamiętać zaznaczenie.

#### <a name="repeat-offenders-tab-for-the-attack-simulation-report"></a>Karta Recydywistów dla raportu symulacji ataku

:::image type="content" source="../../media/attack-sim-report-repeat-offenders-view.png" alt-text="Karta Recydywistów w raporcie symulacji ataku w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-report-repeat-offenders-view.png":::

_Recydywista_ jest użytkownikiem, który został naruszony przez kolejne symulacje. Domyślna liczba kolejnych symulacji to dwie, ale możesz zmienić wartość na karcie **Ustawienia** trenowania symulacji ataku pod adresem <https://security.microsoft.com/attacksimulator?viewid=setting>.

Na karcie **Recydywatorzy** wykres organizuje dane recydywisty według [typu symulacji](attack-simulation-training.md#select-a-social-engineering-technique):

- **Wszystkie**
- **Zbieranie poświadczeń**
- **Załącznik złośliwego oprogramowania**
- **Link w załączniku**
- **Link do złośliwego oprogramowania**
- **Drive-by URL**

Jeśli umieścisz kursor nad punktem danych na wykresie, zostaną wyświetlone rzeczywiste wartości.

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Użytkownik**
- **Liczba powtórzeń**
- **Typy symulacji**
- **Symulacje**

Wyniki można posortować, klikając dostępny nagłówek kolumny.

Kliknij **pozycję Dostosuj kolumny** , aby usunąć wyświetlane kolumny. Po zakończeniu kliknij przycisk **Zastosuj**.

Kliknij ikonę ![Filtruj.](../../media/m365-cc-sc-filter-icon.png) **Filtruj** , aby filtrować tabelę wykresów i szczegółów według niektórych lub wszystkich wartości typu symulacji:

- **Zbieranie poświadczeń**
- **Załącznik złośliwego oprogramowania**
- **Link w załączniku**
- **Link do złośliwego oprogramowania**
- **Drive-by URL**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Użyj ![ikony](../../media/m365-cc-sc-search-icon.png) wyszukiwania **Pole wyszukiwania** , aby filtrować wyniki według dowolnych wartości kolumn. Symbole wieloznaczne nie są obsługiwane.

Jeśli klikniesz ikonę ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **Przycisk Eksportuj raport** , postęp generowania raportu jest wyświetlany jako procent ukończenia. W otwartym oknie dialogowym możesz otworzyć plik .csv, zapisać plik .csv i zapamiętać zaznaczenie.

## <a name="insights-and-reports-in-the-simulation-details-of-attack-simulation-training"></a>Szczegółowe informacje i raporty w szczegółach symulacji trenowania symulacji ataków

Aby przejść do karty **Symulacje**, otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do obszaru Email & collaboration **Attack simulation training (Trenowanie symulacji ataków** & **poczty** \> e-mail), a następnie wybierz kartę **Symulacje**. Aby przejść bezpośrednio do karty **Symulacje** na stronie **trenowania symulacji ataku**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=simulations>.

Po wybraniu symulacji z listy zostanie otwarta strona szczegółów. Ta strona zawiera ustawienia konfiguracji symulacji, które powinny zostać wyświetlone (stan, data uruchomienia, użyty ładunek itp.).

W pozostałej części tej sekcji opisano szczegółowe informacje i raporty dostępne na stronie szczegółów symulacji.

### <a name="simulation-impact-section"></a>Sekcja wpływu symulacji

Sekcja **Wpływ symulacji** na stronie szczegółów symulacji pokazuje, ilu użytkowników zostało całkowicie oszukanych przez symulację i całkowitą liczbę użytkowników w symulacji. Wyświetlane informacje różnią się w zależności od typu symulacji. Przykład:

- Linki: **wprowadzono poświadczenia** i **nie wprowadzono poświadczeń**.

  :::image type="content" source="../../media/attack-sim-training-sim-details-sim-impact-links.png" alt-text="Sekcja Wpływ symulacji na szczegóły symulacji związanej z linkiem" lightbox="../../media/attack-sim-training-sim-details-sim-impact-links.png":::

- Załączniki: **otwarto załącznik** i **nie otwarto załącznika**.

  :::image type="content" source="../../media/attack-sim-training-sim-details-sim-impact-attachments.png" alt-text="Sekcja Wpływ symulacji na szczegóły symulacji związanej z załącznikami" lightbox="../../media/attack-sim-training-sim-details-sim-impact-attachments.png":::

Jeśli umieścisz kursor nad sekcją na wykresie, zostaną wyświetlone rzeczywiste liczby dla każdej kategorii.

### <a name="all-user-activity-section"></a>Cała sekcja aktywności użytkownika

Sekcja **Wszystkie działania użytkownika** na stronie szczegółów symulacji zawiera liczby możliwych wyników symulacji. Wyświetlane informacje różnią się w zależności od typu symulacji. Przykład:

- **PomyślnieDeliveredEmail**
- **ReportedEmail**: Ilu użytkowników zgłosiło komunikat symulacji jako podejrzany.
- Linki:
  - **EmailLinkClicked**: Ilu użytkowników kliknął link w komunikacie symulacji.
  - **CredSupplied: Po kliknięciu** linku ilu użytkowników podało swoje poświadczenia.

    :::image type="content" source="../../media/attack-sim-training-sim-details-all-user-activity-links.png" alt-text="Sekcja Wszystkie działania użytkownika dotycząca szczegółów symulacji związanych z linkiem" lightbox="../../media/attack-sim-training-sim-details-all-user-activity-links.png":::

- Załączniki:
  - **AttachmentOpened**: Ilu użytkowników otworzyło załącznik w komunikacie symulacji.

    :::image type="content" source="../../media/attack-sim-training-sim-details-all-user-activity-attachments.png" alt-text="Sekcja Wszystkie działania użytkownika dotycząca szczegółów symulacji związanych z załącznikami" lightbox="../../media/attack-sim-training-sim-details-all-user-activity-attachments.png":::

### <a name="training-completion-section"></a>Sekcja ukończenia szkolenia

Sekcja **Ukończenie trenowania** na stronie szczegółów symulacji przedstawia szkolenia wymagane do symulacji oraz liczbę użytkowników, którzy ukończyli szkolenia.

:::image type="content" source="../../media/attack-sim-training-sim-details-training-completed.png" alt-text="Sekcja Ukończenie szkolenia dotycząca szczegółów symulacji związanych z załącznikami" lightbox="../../media/attack-sim-training-sim-details-training-completed.png":::

## <a name="recommended-actions-section"></a>Zalecana sekcja akcji

Sekcja **Zalecane akcje** na stronie szczegółów symulacji przedstawia akcje rekomendacji z programu [Microsoft Secure Score](../defender/microsoft-secure-score.md) oraz wpływ akcji na wskaźnik bezpieczeństwa. Te zalecenia są oparte na ładunku użytym w symulacji i pomogą chronić użytkowników i środowisko. Wybranie **akcji Ulepszenie** z listy spowoduje przejście do lokalizacji w celu zaimplementowania sugerowanej akcji.

:::image type="content" source="../../media/attack-sim-training-sim-details-recommended-actions.png" alt-text="Sekcja Akcje rekomendacji dotycząca trenowania symulacji ataków" lightbox="../../media/attack-sim-training-sim-details-recommended-actions.png":::

## <a name="related-links"></a>Linki pokrewne

[Wprowadzenie do szkolenia z symulacji ataku](attack-simulation-training-get-started.md)

[Tworzenie symulacji ataku wyłudzania informacji](attack-simulation-training.md)

[tworzenie ładunku do szkolenia osób](attack-simulation-training-payloads.md)
