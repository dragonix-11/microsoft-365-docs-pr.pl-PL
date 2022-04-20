---
title: Wyświetlanie raportów zabezpieczeń poczty e-mail
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 3a137e28-1174-42d5-99af-f18868b43e86
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak znaleźć raporty zabezpieczeń poczty e-mail dostępne w portalu Microsoft 365 Defender i korzystać z nich.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d97442fc2c3767a30c1ea98dc4a1ee7a38e56b45
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971006"
---
# <a name="view-email-security-reports-in-the-microsoft-365-defender-portal"></a>Wyświetlanie raportów zabezpieczeń poczty e-mail w portalu Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W portalu <https://security.microsoft.com> Microsoft 365 Defender dostępnych jest wiele raportów, które ułatwiają sprawdzenie, w jaki sposób funkcje zabezpieczeń poczty e-mail, takie jak funkcje ochrony przed spamem i złośliwym oprogramowaniem w Microsoft 365 chronią Organizację. Jeśli masz [niezbędne uprawnienia](#what-permissions-are-needed-to-view-these-reports), możesz wyświetlać i pobierać te raporty zgodnie z opisem w tym artykule.

> [!NOTE]
>
> Niektóre raporty na stronie **Raporty współpracy & poczty e-mail** wymagają Ochrona usługi Office 365 w usłudze Microsoft Defender. Aby uzyskać informacje o tych raportach, zobacz [Wyświetlanie raportów Ochrona usługi Office 365 w usłudze Defender w portalu Microsoft 365 Defender](view-reports-for-mdo.md).
>
> Raporty związane z przepływem poczty znajdują się teraz w centrum administracyjnym Exchange. Aby uzyskać więcej informacji na temat tych raportów, zobacz [Raporty przepływu poczty w nowym centrum administracyjnym Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="email-security-report-changes-in-the-microsoft-365-defender-portal"></a>Zmiany raportu zabezpieczeń poczty e-mail w portalu Microsoft 365 Defender

Raporty Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Microsoft Defender w portalu Microsoft 365 Defender, które zostały zastąpione, przeniesione lub przestarzałe, zostały opisane w poniższej tabeli.

|Przestarzały raport i polecenia cmdlet|Nowy raport i polecenia cmdlet|Identyfikator centrum komunikatów|Data|
|---|---|:---:|:---:|
|**Śledzenie adresu URL** <p> Get-URLTrace|[Raport ochrony adresu URL](view-reports-for-mdo.md#url-protection-report) <p> [Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <br> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|MC239999|Czerwiec 2021|
|**Wysłany i odebrany raport e-mail** <p> Get-MailTrafficReport <br> Get-MailDetailReport|[Raport o stanie ochrony przed zagrożeniami](#threat-protection-status-report) <br> [Raport o stanie przepływu poczty](#mailflow-status-report) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport) <br> [Get-MailFlowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|MC236025|Czerwiec 2021|
|**Przekazywanie raportu** <p> brak poleceń cmdlet|[Raport komunikatów przesyłanych automatycznie w usłudze EAC](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) <p> brak poleceń cmdlet|MC250533|Czerwiec 2021|
|**raport typów plików załączników Sejf** <p> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Raport o stanie ochrony przed zagrożeniami: wyświetlanie danych według złośliwego oprogramowania poczty e-mail \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250532|Czerwiec 2021|
|**raport dyspozycji komunikatów załączników Sejf** <p> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Raport o stanie ochrony przed zagrożeniami: wyświetlanie danych według złośliwego oprogramowania poczty e-mail \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250531|Czerwiec 2021|
|**Wykryto złośliwe oprogramowanie w raporcie poczty e-mail** <p> Get-MailTrafficReport <br> Get-MailDetailMalwareReport|[Raport o stanie ochrony przed zagrożeniami: wyświetlanie danych według złośliwego oprogramowania poczty e-mail \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250530|Czerwiec 2021|
|**Raport wykrywania spamu** <p> Get-MailTrafficReport <br> Get-MailDetailSpamReport|[Raport o stanie ochrony przed zagrożeniami: wyświetlanie danych według spamu poczty e-mail \>](#view-data-by-email--spam-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250529|Październik 2021|
|Get-AdvancedThreatProtectionDocumentReport <p> Get-AdvancedThreatProtectionDocumentDetail|[Get-ContentMalwareMdoAggregateReport](/powershell/module/exchange/get-contentmalwaremdoaggregatereport) <p> [Get-ContentMalwareMdoDetailReport](/powershell/module/exchange/get-contentmalwaremdodetailreport)|TBA|Maj 2022 r.|
|**raport reguł transportu Exchange** <p> [Get-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailTransportRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|[Exchange raport reguł transportu w EAC](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report) <p> [Get-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailTransportRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|MC316157|Kwiecień 2022 r.|
|Get-MailTrafficTopReport|[Raport o stanie ochrony przed zagrożeniami: wyświetlanie danych według złośliwego oprogramowania poczty e-mail \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport) <p> **Uwaga**: Funkcja raportowania szyfrowania nie zastępuje funkcji Get-MailTrafficTopReport.|MC315742|Kwiecień 2022 r.|

## <a name="compromised-users-report"></a>Raport użytkowników z naruszonymi zabezpieczeniami

> [!NOTE]
> Ten raport jest dostępny w Microsoft 365 organizacjach z Exchange Online skrzynkami pocztowymi. Nie jest ona dostępna w autonomicznych organizacjach Exchange Online Protection (EOP).

Raport **Użytkownicy, których bezpieczeństwo zostało naruszone** , pokazuje liczbę kont użytkowników, które zostały oznaczone jako **Podejrzane** lub **Ograniczone** w ciągu ostatnich 7 dni. Konta w każdym z tych stanów są problematyczne, a nawet zagrożone. W przypadku częstego użycia raport umożliwia wykrywanie skoków, a nawet trendów na podejrzanych lub ograniczonych kontach. Aby uzyskać więcej informacji na temat użytkowników, którzy naruszyli bezpieczeństwo, zobacz [Odpowiadanie na naruszone konto e-mail](responding-to-a-compromised-email-account.md).

:::image type="content" source="../../media/compromised-users-report-widget.png" alt-text="Widżet Naruszeni użytkownicy na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/compromised-users-report-widget.png":::

Widok agregacji przedstawia dane z ostatnich 90 dni, a widok szczegółów przedstawia dane z ostatnich 30 dni.

Aby wyświetlić raport w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do pozycji **Raporty Wiadomości** \> **e-mail & współpracy** \> **Wiadomości e-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź pozycję **Użytkownicy z naruszeniem zabezpieczeń** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz plik <https://security.microsoft.com/reports/CompromisedUsers>.

Na stronie **Użytkownicy, którzy naruszyli** bezpieczeństwo, na wykresie przedstawiono następujące informacje dotyczące określonego zakresu dat:

- **Ograniczone**: Konto użytkownika zostało ograniczone do wysyłania wiadomości e-mail z powodu wysoce podejrzanych wzorców.
- **Podejrzane**: konto użytkownika wysłało podejrzaną wiadomość e-mail i istnieje ryzyko ograniczenia wysyłania wiadomości e-mail.

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Czas tworzenia**
- **Identyfikator użytkownika**
- **Akcja**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Data (UTC)**: **data rozpoczęcia** i **data zakończenia**.
- **Działanie**: **Ograniczone** lub **podejrzane**
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu).

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Użytkownicy, którzy naruszyli** bezpieczeństwo, ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

:::image type="content" source="../../media/compromised-users-report-activity-view.png" alt-text="Widok raportów w raporcie Użytkownicy, którzy naruszyli bezpieczeństwo" lightbox="../../media/compromised-users-report-activity-view.png":::

## <a name="exchange-transport-rule-report"></a>raport reguł transportu Exchange

Raport **reguł transportu Exchange** pokazuje wpływ reguł przepływu poczty (nazywanych również regułami transportu) na wiadomości przychodzące i wychodzące w organizacji.

Aby wyświetlić raport w portalu Microsoft 365 Defender, przejdź do pozycji **Raporty** \> **Wiadomości e-mail & współpracy** \> **E-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź **Exchange regułę transportu**, a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz plik <https://security.microsoft.com/reports/ETRRuleReport>.

:::image type="content" source="../../media/transport-rule-report-widget.png" alt-text="Widżet reguły transportu Exchange na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/transport-rule-report-widget.png":::

Na stronie **raportu reguły transportu Exchange** dostępne wykresy i dane są opisane w poniższych sekcjach.
> [!NOTE]
> **Raport reguł transportu Exchange** jest teraz dostępny w eac. Aby uzyskać więcej informacji, zobacz [Exchange raport reguł transportu w nowym eac](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

### <a name="chart-breakdown-by-direction"></a>Podział wykresu według kierunku

:::image type="content" source="../../media/transport-rule-report-etr-direction-view.png" alt-text="Widok Kierunek dla reguł transportu Exchange w raporcie reguł transportu Exchange" lightbox="../../media/transport-rule-report-etr-direction-view.png":::

Jeśli **wybierzesz pozycję Podział wykresu według kierunku**, dostępne są następujące wykresy:

- **Wyświetlanie danych według reguł transportu Exchange**: liczba wiadomości **przychodzących** i **wychodzących**, na które miały wpływ reguły przepływu poczty.
- **Wyświetlanie danych według reguł transportu Exchange DLP**: liczba komunikatów **przychodzących** i **wychodzących**, na które miały wpływ reguły przepływu poczty zapobiegania utracie danych (DLP).

Poniższe informacje są wyświetlane w tabeli szczegółów poniżej wykresu:

- **Data**
- **Zasady DLP** (**tylko wyświetlanie danych według DLP Exchange reguł transportu**)
- **Reguła transportu**
- **Temat**
- **Adres nadawcy**
- **Adres odbiorcy**
- **Ważności**
- **Kierunek**

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**.
- **Kierunek**: **wychodzący** i **przychodzący**.
- **Ważność**: **wysoka ważność**, **średnia ważność** i **niska ważność**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **raportu reguły transportu Exchange** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

### <a name="chart-breakdown-by-severity"></a>Podział wykresu według ważności

:::image type="content" source="../../media/transport-rule-report-etr-severity-view.png" alt-text="Widok Ważność dla reguł transportu Exchange w raporcie reguł transportu Exchange" lightbox="../../media/transport-rule-report-etr-severity-view.png":::

Jeśli **wybierzesz pozycję Podział wykresu według ważności**, dostępne są następujące wykresy:

- **Wyświetlanie danych według reguł transportu Exchange**: liczba komunikatów **o wysokiej ważności**, **średniej ważności** i **niskiej ważności**. Poziom ważności należy ustawić jako akcję w **regule (Przeprowadź inspekcję tej reguły z poziomem ważności** lub _SetAuditSeverity_). Aby uzyskać więcej informacji, zobacz [Akcje reguł przepływu poczty w Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions).

- **Wyświetlanie danych według reguł transportu Exchange DLP**: liczba komunikatów **o wysokiej ważności**, **średniej ważności** i **niskiej ważności**, na które miały wpływ reguły przepływu poczty DLP.

Poniższe informacje są wyświetlane w tabeli szczegółów poniżej wykresu:

- **Data**
- **Zasady DLP** (**tylko wyświetlanie danych według DLP Exchange reguł transportu**)
- **Reguła transportu**
- **Temat**
- **Adres nadawcy**
- **Adres odbiorcy**
- **Ważności**
- **Kierunek**

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Kierunek**: **ruch wychodzący** i **przychodzący**
- **Ważność**: **wysoka ważność**, **średnia ważność** i **niska ważność**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **raportu reguły transportu Exchange** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

## <a name="forwarding-report"></a>Przekazywanie raportu

> [!NOTE]
> Ten raport jest teraz dostępny w usłudze EAC. Aby uzyskać więcej informacji, zobacz [Raport automatycznego przekazywania komunikatów w nowym eac](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Raport o stanie przepływu poczty

**Raport o stanie przepływu poczty** to inteligentny raport zawierający informacje o przychodzącej i wychodzącej wiadomości e-mail, wykrywaniu spamu, złośliwym oprogramowaniu, wiadomościach e-mail zidentyfikowanych jako "dobre" oraz informacjach o dozwolonych lub zablokowanych wiadomościach e-mail na brzegu. Jest to jedyny raport, który zawiera informacje o ochronie krawędzi i pokazuje, ile wiadomości e-mail zostało zablokowanych przed dopuszczeniem do usługi do oceny przez Exchange Online Protection (EOP). Ważne jest, aby zrozumieć, że jeśli wiadomość zostanie wysłana do pięciu adresatów, zliczmy ją jako pięć różnych wiadomości, a nie jedną wiadomość.

Aby wyświetlić raport w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do pozycji **Raporty Wiadomości** \> **e-mail & współpracy** \> **Wiadomości e-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź **podsumowanie stanu przepływu poczty** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz plik <https://security.microsoft.com/reports/mailflowStatusReport>.

:::image type="content" source="../../media/mail-flow-status-report-widget.png" alt-text="Widżet podsumowania stanu przepływu poczty e-mail na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/mail-flow-status-report-widget.png":::

### <a name="type-view-for-the-mailflow-status-report"></a>Widok typów dla raportu o stanie przepływu poczty

:::image type="content" source="../../media/mail-flow-status-report-type-view.png" alt-text="Widok Typ w raporcie o stanie przepływu poczty" lightbox="../../media/mail-flow-status-report-type-view.png":::

Na stronie **Raport o stanie przepływu poczty** domyślnie jest zaznaczona karta **Typ** . Na wykresie przedstawiono następujące informacje dotyczące określonego zakresu dat:

- **Dobra wiadomość e-mail**: wiadomość e-mail, która nie jest spamem lub jest dozwolona przez zasady użytkownika lub organizacji.
- **Suma**
- **Złośliwe oprogramowanie**: wiadomości e-mail zablokowane jako złośliwe oprogramowanie przez różne filtry.
- **Wiadomość e-mail wyłudzająca informacje**: wiadomość e-mail zablokowana jako wyłudzanie informacji przez różne filtry.
- **Spam**: wiadomości e-mail zablokowane jako spam przez różne filtry.
- **Ochrona krawędzi**: wiadomość e-mail odrzucona na krawędzi/obwodzie przed oceną przez EOP lub Ochrona usługi Office 365 w usłudze Defender.
- **Komunikaty reguł**: Wiadomości e-mail, które zostały podjęte przez reguły przepływu poczty (nazywane również regułami transportu).

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Kierunek**
- **Type**
- **24 godziny**
- **3 dni**
- **7 dni**
- **15 dni**
- **30 dni**

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Data (UTC)**: **data rozpoczęcia** i **data zakończenia**.
- **Kierunek poczty**: **przychodzący** i **wychodzący**.
- **Typ**:
  - **Dobra poczta**
  - **Złośliwego oprogramowania**
  - **Spam**
  - **Ochrona krawędzi**
  - **Komunikaty reguł**
  - **Poczta e-mail wyłudzająca informacje**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Po powrocie na stronę **raportu o stanie przepływu** poczty, jeśli klikniesz **pozycję Wybierz kategorię, aby uzyskać więcej szczegółów**, możesz wybrać jedną z następujących wartości:

- **Wiadomość e-mail dotycząca wyłudzania informacji**: ten wybór spowoduje przejście do [raportu o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
- **Złośliwe oprogramowanie w wiadomości e-mail**: ten wybór spowoduje przejście do [raportu o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
- **Wykrywanie spamu**: ten wybór powoduje przejście do [raportu Wykrywanie spamu](view-email-security-reports.md#spam-detections-report).
- **Spam zablokowany przez** przeglądarę Edge: ten wybór powoduje przejście do [raportu Wykrywanie spamu](view-email-security-reports.md#spam-detections-report).

Na stronie **Raport o stanie przepływu poczty** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Utwórz ikonę harmonogramu](#schedule-report)** i ![eksportu.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

### <a name="direction-view-for-the-mailflow-status-report"></a>Widok kierunku dla raportu o stanie przepływu poczty

:::image type="content" source="../../media/mail-flow-status-report-direction-view.png" alt-text="Widok Kierunek w raporcie o stanie przepływu poczty" lightbox="../../media/mail-flow-status-report-direction-view.png":::

Jeśli klikniesz kartę **Kierunek** , wykres wyświetli następujące informacje dla określonego zakresu dat:

- **Przychodzących**
- **Wychodzące**

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Data (UTC)**: **data rozpoczęcia** i **data zakończenia**.
- **Kierunek poczty**: **przychodzący** i **wychodzący**.
- **Typ**:
  - **Dobra poczta**
  - **Złośliwego oprogramowania**
  - **Spam**
  - **Ochrona krawędzi**
  - **Komunikaty reguł**
  - **Poczta e-mail wyłudzająca informacje**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Po powrocie na stronę **raportu o stanie przepływu** poczty, jeśli klikniesz **pozycję Wybierz kategorię, aby uzyskać więcej szczegółów**, możesz wybrać jedną z następujących wartości:

- **Wiadomość e-mail dotycząca wyłudzania informacji**: ten wybór spowoduje przejście do [raportu o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
- **Złośliwe oprogramowanie w wiadomości e-mail**: ten wybór spowoduje przejście do [raportu o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
- **Wykrywanie spamu**: ten wybór powoduje przejście do [raportu Wykrywanie spamu](view-email-security-reports.md#spam-detections-report).
- **Spam zablokowany przez** przeglądarę Edge: ten wybór powoduje przejście do [raportu Wykrywanie spamu](view-email-security-reports.md#spam-detections-report).

Na stronie **Raport o stanie przepływu poczty** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **Utwórz ikonę harmonogramu** i ![eksportu.](../../media/m365-cc-sc-download-icon.png) **Przyciski eksportu** są dostępne.

### <a name="mailflow-view-for-the-mailflow-status-report"></a>Widok przepływu poczty dla raportu o stanie przepływu poczty

Widok **Przepływ poczty** pokazuje, jak funkcje ochrony przed zagrożeniami poczty e-mail firmy Microsoft filtruje przychodzące i wychodzące wiadomości e-mail w organizacji. Ten widok używa diagramu przepływu poziomego (znanego jako diagram _Sankey_ ), aby podać szczegółowe informacje na temat łącznej liczby wiadomości e-mail oraz wpływu skonfigurowanych funkcji ochrony przed zagrożeniami, w tym ochrony krawędzi, ochrony przed złośliwym oprogramowaniem, ochrony przed wyłudzaniem informacji, ochrony przed spamem i ochrony przed fałszowaniem.

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view.png" alt-text="Widok Przepływ poczty w raporcie o stanie przepływu poczty" lightbox="../../media/mail-flow-status-report-mailflow-view.png":::

Widok agregujący i widok tabeli szczegółów umożliwiają filtrowanie przez 90 dni.

Informacje na diagramie są kodowane kolorami za pomocą technologii **EOP** lub **Ochrona usługi Office 365 w usłudze Defender**.

Diagram składa się z następujących poziomych pasm:

- Łączna liczba pasm **poczty e-mail**: ta wartość jest zawsze wyświetlana jako pierwsza.
- **Blok krawędzi** i **pasek przetworzony** :
  - **Blok krawędzi**: komunikaty, które są filtrowane na krawędzi i identyfikowane jako ochrona krawędzi.
  - **Przetworzone**: komunikaty obsługiwane przez stos filtrowania.
- Zespół wyników:
  - **Blok reguły**: komunikaty przetwarzane przez Exchange reguły przepływu poczty (reguły transportu).
  - **Blok złośliwego oprogramowania**: komunikaty, które są identyfikowane jako złośliwe oprogramowanie za pomocą różnych filtrów.<sup>\*</sup>
  - **Blok phish**: komunikaty zidentyfikowane jako phish podczas przetwarzania przez różne filtry.<sup>\*</sup>
  - **Blok spamu**: wiadomości zidentyfikowane jako spam podczas przetwarzania przez różne filtry.<sup>\*</sup>
  - **Blok personifikacji**: komunikaty wykryte jako personifikacja użytkownika lub personifikacja domeny w Ochrona usługi Office 365 w usłudze Defender.<sup>\*</sup>
  - **Blok detonacji**: komunikaty wykryte podczas detonacji pliku lub adresu URL przez zasady załączników Sejf lub zasady linków Sejf w Ochrona usługi Office 365 w usłudze Defender.<sup>\*</sup>
  - **Usunięto zap**: komunikaty, które są usuwane przez automatyczne przeczyszczanie zero godzin (ZAP).<sup>\*</sup>
  - **Dostarczone**: komunikaty dostarczane do użytkowników z powodu zezwolenia.<sup>\*</sup>

Po umieszczeniu wskaźnika myszy na pasmie poziomym na diagramie zobaczysz liczbę powiązanych komunikatów.

<sup>\*</sup> Kliknięcie tego elementu spowoduje rozwinięcie diagramu w celu wyświetlenia dalszych szczegółów. Opis każdego elementu w węzłach rozwiniętych można znaleźć w [temacie Technologie wykrywania](/office/office-365-management-api/office-365-management-activity-api-schema#detection-technologies).

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view-details.png" alt-text="Szczegóły bloku wyłudzania informacji w widoku Przepływ poczty w raporcie o stanie przepływu poczty" lightbox="../../media/mail-flow-status-report-mailflow-view-details.png":::

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Data**
- **Łączna liczba wiadomości e-mail**
- **Filtrowana krawędź**
- **Komunikaty reguł**
- **Aparat chroniący przed złośliwym oprogramowaniem, Sejf załączniki, filtrowane reguły**
- **Personifikacja DMARC, fałszowanie, phish filtrowane**
- **Wykrywanie detonacji**
- **Filtrowane antyspamowe**
- **Usunięto zap**
- **Komunikaty, w których nie wykryto zagrożeń**

Jeśli wybierzesz wiersz w tabeli szczegółów, kolejny podział liczby wiadomości e-mail zostanie wyświetlony w wyświetlonym oknie wysuwnym szczegółów.

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**.
- **Kierunek**: **wychodzący** i **przychodzący**.

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Po powrocie na stronę **raportu o stanie przepływu** poczty możesz kliknąć pozycję **Pokaż trendy** , aby wyświetlić wykresy trendów w wyświetlonym wysuwaniu **trendów przepływu poczty** .

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view-show-trends.png" alt-text="Wysuwane trendy przepływu poczty w widoku Przepływ poczty w raporcie o stanie przepływu poczty" lightbox="../../media/mail-flow-status-report-mailflow-view-show-trends.png":::

Na stronie **Raport o stanie przepływu poczty** ikona ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **Przycisk Eksportuj** jest dostępny.

## <a name="malware-detections-report"></a>Raport wykrywania złośliwego oprogramowania

> [!NOTE]
> Ten raport został przestarzały. Te same informacje są dostępne w [raporcie o stanie ochrony przed zagrożeniami](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Raport opóźnienia poczty

**Raport opóźnienia poczty** w Ochrona usługi Office 365 w usłudze Defender zawiera informacje na temat opóźnienia dostarczania i detonacji poczty w organizacji. Aby uzyskać więcej informacji, zobacz [Raport opóźnienia poczty](view-reports-for-mdo.md#mail-latency-report).

## <a name="spam-detections-report"></a>Raport dotyczący wykrywania spamu

> [!NOTE]
> Ten raport został przestarzały. Te same informacje są dostępne w [raporcie o stanie ochrony przed zagrożeniami](#threat-protection-status-report).

## <a name="spoof-detections-report"></a>Raport dotyczący wykrywania fałszowania

Raport **Wykrywanie fałszowania** zawiera informacje o komunikatach, które zostały zablokowane lub dozwolone z powodu fałszowania. Aby uzyskać więcej informacji na temat fałszowania, zobacz [Ochrona przed fałszowaniem w ramach EOP](anti-spoofing-protection.md).

Zagregowany widok raportu umożliwia filtrowanie przez 90 dni, podczas gdy widok szczegółów umożliwia filtrowanie tylko przez dziesięć dni.

Aby wyświetlić raport w portalu Microsoft 365 Defender, przejdź do pozycji **Raporty** \> **Wiadomości e-mail & współpracy** \> **E-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź pozycję **Wykrywanie fałszowania** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz plik <https://security.microsoft.com/reports/SpoofMailReport>.

:::image type="content" source="../../media/spoof-detections-widget.png" alt-text="Widżet Wykrywanie fałszowania na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/spoof-detections-widget.png":::

Na wykresie przedstawiono następujące informacje:

- **Przekazać**
- **Nie**
- **SoftPass**
- **Brak**
- **Inne**

Po umieszczeniu wskaźnika myszy na dniu (punkcie danych) na wykresie możesz zobaczyć, ile sfałszowanych komunikatów zostało wykrytych i dlaczego.

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Wynik**:
  - **Przekazać**
  - **Nie**
  - **SoftPass**
  - **Brak**
  - **Inne**
- **Typ fałszowania**: **wewnętrzny** i **zewnętrzny**

:::image type="content" source="../../media/spoof-detections-report-page.png" alt-text="Strona Raport dotyczący fałszowania poczty w portalu Microsoft 365 Defender" lightbox="../../media/spoof-detections-report-page.png":::

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Data**
- **Sfałszowany użytkownik**
- **Wysyłanie infrastruktury**
- **Typ fałszowania**
- **Result (Wynik)**
- **Kod wyniku**
- **SPF**
- **DKIM**
- **DMARC**
- **Liczba komunikatów**

Aby uzyskać więcej informacji na temat kodów wyników uwierzytelniania złożonego, zobacz [Nagłówki wiadomości antyspamowych w Microsoft 365](anti-spam-message-headers.md).

Na stronie **Wykrywanie fałszowania** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

## <a name="submissions-report"></a>Raport dotyczący przesyłania

Raport **Przesłane** zawiera informacje o elementach, które administratorzy zgłosili firmie Microsoft do analizy. Aby uzyskać więcej informacji, zobacz [Przesyłanie przez administratora w celu przesyłania do firmy Microsoft podejrzanych wiadomości spamowych, phish, adresów URL i plików](admin-submission.md).

Aby wyświetlić raport w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do pozycji **Raporty Wiadomości** \> **e-mail & współpracy** \> **Wiadomości e-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź pozycję **Przesłane** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz plik <https://security.microsoft.com/adminSubmissionReport>. Aby przejść do [przesyłania przez administratora w portalu Microsoft 365 Defender](admin-submission.md), kliknij pozycję **Przejdź do pozycji Przesłane**. Administratorzy będą mogli wyświetlać raport przez ostatnie 30 dni.

:::image type="content" source="../../media/submissions-report-widget.png" alt-text="Widżet Przesłane na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/submissions-report-widget.png":::

Na wykresie przedstawiono następujące informacje:

- **Oczekujące**
- **Zakończone**

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Zgłoszona data**: **godzina rozpoczęcia** i **godzina zakończenia**
- **Typ przesyłania**:
  - **Poczta e-mail**
  - **ADRES URL**
  - **Plik**
- **Identyfikator przesyłania**
- **Identyfikator komunikatu sieci**
- **Nadawcy**
- **Nazwa**
- **Przesłane przez**
- **Przyczyna przesłania**:
  - **Nie śmieci**
  - **Phish**
  - **Złośliwego oprogramowania**
  - **Spam**
- **Stan ponownego skanowania**:
  - **Oczekujące**
  - **Zakończone**

Tabela szczegółów poniżej wykresu zawiera te same informacje i ma te same opcje **grupowania** lub **dostosowywania kolumn**, co na karcie **Przesłane do analizy** na stronie **Przesyłanie** współpracy \> **& poczty e-mail**. Aby uzyskać więcej informacji, zobacz [Wyświetlanie przesłanych przez administratorów do firmy Microsoft](admin-submission.md#view-admin-submissions-to-microsoft).

Na stronie **Przesłane** dostępny jest przycisk **[Eksportuj](#export-report)** .

:::image type="content" source="../../media/submissions-report-page.png" alt-text="Strona raportu Przesłane w portalu Microsoft 365 Defender" lightbox="../../media/submissions-report-page.png":::

## <a name="threat-protection-status-report"></a>Raport o stanie ochrony przed zagrożeniami

Raport **o stanie ochrony przed zagrożeniami** jest dostępny zarówno w ramach operacji EOP, jak i Ochrona usługi Office 365 w usłudze Defender, jednak raporty zawierają różne dane. Na przykład klienci EOP mogą wyświetlać informacje o złośliwym oprogramowaniu wykrytym w wiadomości e-mail, ale nie informacje o złośliwych plikach [wykrytych przez Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Raport zawiera liczbę wiadomości e-mail ze złośliwą zawartością, takich jak pliki lub adresy witryny sieci Web (ADRESY URL), które zostały zablokowane przez aparat ochrony przed złośliwym oprogramowaniem, [automatyczne przeczyszczanie o wartości zero godzin (ZAP)](zero-hour-auto-purge.md) i funkcje Ochrona usługi Office 365 w usłudze Defender, takie jak [linki Sejf](safe-links.md), [Sejf załączniki](safe-attachments.md) i [ funkcje ochrony przed personifikacją w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Te informacje umożliwiają identyfikowanie trendów lub określanie, czy zasady organizacji wymagają dostosowania.

**Uwaga**: Ważne jest, aby zrozumieć, że jeśli wiadomość zostanie wysłana do pięciu adresatów, zliczmy ją jako pięć różnych wiadomości, a nie jedną wiadomość.

Aby wyświetlić raport w portalu Microsoft 365 Defender, przejdź do pozycji **Raporty** \> **Wiadomości e-mail & współpracy** \> **E-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź **pozycję Stan ochrony przed zagrożeniami** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz jeden z następujących adresów URL:

- Ochrona usługi Office 365 w usłudze Defender:<https://security.microsoft.com/reports/TPSAggregateReportATP>
- EOP: <https://security.microsoft.com/reports/TPSAggregateReport>

:::image type="content" source="../../media/threat-protection-status-report-widget.png" alt-text="Widżet stan ochrony przed zagrożeniami na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/threat-protection-status-report-widget.png":::

Domyślnie na wykresie są wyświetlane dane z ostatnich 7 dni. Jeśli klikniesz pozycję **Filtruj** na stronie **Raport o stanie ochrony przed zagrożeniami** , możesz wybrać 90-dniowy zakres dat (subskrypcje wersji próbnej mogą być ograniczone do 30 dni). Tabela szczegółów umożliwia filtrowanie przez 30 dni.

Dostępne widoki zostały opisane w poniższych sekcjach.

### <a name="view-data-by-overview"></a>Wyświetlanie danych według przeglądu

:::image type="content" source="../../media/threat-protection-status-report-overview-view.png" alt-text="Widok Przegląd w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-overview-view.png":::

W widoku **Wyświetl dane według przeglądu** na wykresie są wyświetlane następujące informacje o wykrywaniu:

- **Złośliwe oprogramowanie poczty e-mail**
- **Poczta e-mail phish**
- **Spam e-mail**
- **Złośliwe oprogramowanie zawartości**

Tabela szczegółów nie jest dostępna poniżej wykresu.

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**.
- **Wykrywanie**:
  - **Złośliwe oprogramowanie poczty e-mail**
  - **Poczta e-mail phish**
  - **Spam e-mail**
  - **Złośliwe oprogramowanie zawartości**
- **Chronione przez**: **MDO** (Ochrona usługi Office 365 w usłudze Defender) i **EOP**.
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu). Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).
- **Kierunek**:
  - **Wszystkie**
  - **Przychodzących**
  - **Wychodzące**
- **Domena**: **Wszystkie** lub [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Typ zasad**:
  - **Wszystkie**
  - **Ochrona przed złośliwym oprogramowaniem**
  - **załączniki Sejf**
  - **Anty-phish**
  - **Ochrona przed spamem**
  - **Reguła przepływu poczty** (reguła transportu)
  - **Innych**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

### <a name="view-data-by-email--phish-and-chart-breakdown-by-detection-technology"></a>Wyświetlanie danych według języka e-mail \> i podział wykresu według technologii wykrywania

:::image type="content" source="../../media/threat-protection-status-report-phishing-detection-tech-view.png" alt-text="Widok technologii wykrywania wiadomości e-mail wyłudzającej informacje w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-phishing-detection-tech-view.png":::

> [!NOTE]
> Od maja 2021 r. wykrywanie wyłudzania informacji w wiadomościach e-mail zostało zaktualizowane w celu uwzględnienia **załączników wiadomości zawierających adresy URL wyłudzania** informacji. Ta zmiana może przenieść część woluminu wykrywania z widoku **Wyświetl dane według złośliwego oprogramowania poczty e-mail \>** i do widoku **Wyświetl dane według języka e-mail \> Phish**. Innymi słowy, załączniki wiadomości z adresami URL wyłudzania informacji, które zostały tradycyjnie zidentyfikowane jako złośliwe oprogramowanie, mogą być zamiast tego identyfikowane jako wyłudzanie informacji.

W widoku View data by Email Phish and **Chart breakdown by Detection Technology** (**Wyświetlanie danych według języka e-mail \>** i wykresu według technologii wykrywania) na wykresie przedstawiono następujące informacje:

- **Złośliwa reputacja**<sup>\*</sup> adresu URL: reputacja złośliwego adresu URL wygenerowana na podstawie detonacji Ochrona usługi Office 365 w usłudze Defender w innych Microsoft 365 klientów.
- **Filtr zaawansowany**: sygnały wyłudzające informacje oparte na uczeniu maszynowym.
- **Filtr ogólny**: wyłudzanie informacji na podstawie reguł analityków.
- **Fałszowanie wewnątrz organizacji**: nadawca próbuje sfałszować domenę adresata.
- **Fałszowanie domeny zewnętrznej**: nadawca próbuje sfałszować inną domenę.
- **Spoof DMARC**: błąd uwierzytelniania DMARC w komunikatach.
- **Marka personifikacji**: Personifikacja znanych marek na podstawie nadawców.
- **Wykrywanie analizy mieszanej**
- **Reputacja pliku**
- **Dopasowywanie odcisków palców**
- **Reputacja detonacji adresu URL**<sup>\*</sup>
- **Detonacja adresu URL**<sup>\*</sup>
- **Personifikacja użytkownika**<sup>\*</sup>
- Domena <sup>\*</sup>**personifikacji**: personifikacja domen, które klient jest właścicielem lub definiuje.
- **Personifikacja analizy skrzynki pocztowej**: personifikacja użytkowników zdefiniowanych przez administratora lub poznana za pośrednictwem analizy skrzynki pocztowej.<sup>\*</sup>
- **Detonacja pliku**<sup>\*</sup>
- **Reputacja detonacji plików**<sup>\*</sup>
- **Kampanii**<sup>\*</sup>

<sup>\*</sup>tylko Ochrona usługi Office 365 w usłudze Defender

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data**
- **Temat**
- **Nadawcy**
- **Adresatów**
- **Technologia wykrywania**
- **Stan dostarczania**
- **Adres IP nadawcy**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Wykrywanie**: te same wartości co na wykresie.
- **Chronione przez**: **MDO** (Ochrona usługi Office 365 w usłudze Defender) lub **EOP**
- **Kierunek**:
  - **Wszystkie**
  - **Przychodzących**
  - **Wychodzące**
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu).
- **Domena**: **Wszystkie** lub [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Typ zasad**:
  - **Wszystkie**
  - **Ochrona przed złośliwym oprogramowaniem**
  - **załączniki Sejf**
  - **Anty-phish**
  - **Ochrona przed spamem**
  - **Reguła przepływu poczty** (reguła transportu)
  - **Innych**
- **Nazwa zasad (tylko widok tabeli szczegółów)**: **Wszystkie** lub określone zasady.
- **Adresatów**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Stan ochrony przed zagrożeniami** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

### <a name="view-data-by-email--spam-and-chart-breakdown-by-detection-technology"></a>Wyświetlanie danych według spamu poczty e-mail \> i podział wykresów według technologii wykrywania

:::image type="content" source="../../media/threat-protection-status-report-spam-detection-tech-view.png" alt-text="Widok technologii wykrywania spamu w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-spam-detection-tech-view.png":::

W widoku **Wyświetlanie danych według spamu poczty e-mail \>** i **wykresu według technologii wykrywania** na wykresie przedstawiono następujące informacje:

- **Złośliwa reputacja adresu URL**
- **Filtr zaawansowany**
- **Filtr ogólny**
- **Wykrywanie analizy mieszanej**: do werdyktu komunikatu przyczyniło się wiele filtrów.
- **Dopasowywanie odcisku palca**: komunikat został oznaczony jako nieprawidłowy z powodu poprzednich komunikatów.
- **Reputacja domeny**: ta wiadomość została uznana za spam w oparciu o reputację domeny nadawcy.
- **Zbiorczo**: elementy wykryte jako przekraczające ustawienie zbiorcze dla użytkownika.
- **Reputacja adresu IP**: wiadomość została uznana za spam na podstawie reputacji adresu IP wysyłającego.

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data**
- **Temat**
- **Nadawcy**
- **Adresatów**
- **Technologia wykrywania**
- **Stan dostarczania**
- **Adres IP nadawcy**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Wykrywanie**: te same wartości co na wykresie.
- **Kierunek**:
  - **Wszystkie**
  - **Przychodzących**
  - **Wychodzące**
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu).
- **Domena**: **Wszystkie** lub [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Typ zasad**:
  - **Wszystkie**
  - **Ochrona przed złośliwym oprogramowaniem**
  - **załączniki Sejf**
  - **Anty-phish**
  - **Ochrona przed spamem**
  - **Reguła przepływu poczty** (reguła transportu)
  - **Innych**
- **Nazwa zasad (tylko widok tabeli szczegółów)**: **Wszystkie** lub określone zasady.
- **Adresatów**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Stan ochrony przed zagrożeniami** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

### <a name="view-data-by-email--malware-and-chart-breakdown-by-detection-technology"></a>Wyświetlanie danych według złośliwego oprogramowania poczty e-mail \> i podział wykresu według technologii wykrywania

:::image type="content" source="../../media/threat-protection-status-report-malware-detection-tech-view.png" alt-text="Widok technologii wykrywania złośliwego oprogramowania w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-malware-detection-tech-view.png":::

> [!NOTE]
> Począwszy od maja 2021 r., wykrywanie złośliwego oprogramowania w wiadomościach e-mail zostało zaktualizowane w celu uwzględnienia **szkodliwych adresów URL** w załącznikach wiadomości. Ta zmiana może przenieść część woluminu wykrywania z widoku **Wyświetl dane według języka e-mail \>** i do widoku **Wyświetl dane według złośliwego oprogramowania poczty e-mail\>**. Innymi słowy, szkodliwe adresy URL w załącznikach wiadomości, które tradycyjnie były teraz identyfikowane jako wyłudzanie informacji, mogą zostać zidentyfikowane jako złośliwe oprogramowanie.

W widoku **Wyświetl dane według złośliwego oprogramowania poczty e-mail \>** i **wykresu według technologii wykrywania** na wykresie przedstawiono następujące informacje:

- **Detonacja**<sup>\*</sup> pliku: wykrywanie za pomocą załączników Sejf.
- Reputacja <sup>\*</sup>**detonacji plików**: Cała reputacja złośliwych plików generowana przez detonacje Ochrona usługi Office 365 w usłudze Defender.
- **Reputacja pliku**
- Aparat <sup>\*</sup>**chroniący przed złośliwym oprogramowaniem**: wykrywanie z aparatów chroniących przed złośliwym oprogramowaniem.
- **Blok typu pliku zasad ochrony przed złośliwym oprogramowaniem**: są to wiadomości e-mail odfiltrowane ze względu na typ złośliwego pliku zidentyfikowanego w wiadomości.
- **Złośliwa reputacja adresu URL**<sup>\*</sup>
- **Detonacja adresu URL**<sup>\*</sup>
- **Reputacja detonacji adresu URL**<sup>\*</sup>
- **Kampanii**<sup>\*</sup>

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data**
- **Temat**
- **Nadawcy**
- **Adresatów**
- **Technologia wykrywania**
- **Stan dostarczania**
- **Adres IP nadawcy**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Wykrywanie**: te same wartości co na wykresie.
- **Chronione przez**: **MDO** (Ochrona usługi Office 365 w usłudze Defender) lub **EOP**
- **Kierunek**:
  - **Wszystkie**
  - **Przychodzących**
  - **Wychodzące**
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu).
- **Domena**: **Wszystkie** lub [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Typ zasad**:
  - **Wszystkie**
  - **Ochrona przed złośliwym oprogramowaniem**
  - **załączniki Sejf**
  - **Anty-phish**
  - **Ochrona przed spamem**
  - **Reguła przepływu poczty** (reguła transportu)
  - **Innych**
- **Nazwa zasad (tylko widok tabeli szczegółów)**: **Wszystkie** lub określone zasady.
- **Adresatów**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Stan ochronyZajmowanie** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

### <a name="chart-breakdown-by-policy-type"></a>Podział wykresu według typu zasad

:::image type="content" source="../../media/threat-protection-status-report-phishing-policy-type-view.png" alt-text="Widok typów zasad dla wiadomości e-mail wyłudzającej informacje, wiadomości e-mail ze spamem lub wiadomości e-mail ze złośliwym oprogramowaniem w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-phishing-policy-type-view.png":::

W **widokach Wyświetl dane według języka e-mail \> Phish** **wyświetl dane według spamu poczty e-mail \>** lub **Wyświetl dane według złośliwego oprogramowania poczty e-mail\>**, wybierając pozycję **Podział wykresu według typu zasad**, na wykresie przedstawiono następujące informacje:

- **Ochrona przed złośliwym oprogramowaniem**
- **załączniki Sejf**<sup>\*</sup>
- **Anty-phish**
- **Ochrona przed spamem**
- **Reguła przepływu poczty** (znana również jako reguła transportu)
- **Innych**

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data**
- **Temat**
- **Nadawcy**
- **Adresatów**
- **Technologia wykrywania**
- **Stan dostarczania**
- **Adres IP nadawcy**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Wykrywanie**:
  - **Złośliwa reputacja**<sup>\*</sup> adresu URL: reputacja złośliwego adresu URL wygenerowana na podstawie detonacji Ochrona usługi Office 365 w usłudze Defender w innych Microsoft 365 klientów.
  - **Filtr zaawansowany**: sygnały wyłudzające informacje oparte na uczeniu maszynowym.
  - **Filtr ogólny**: wyłudzanie informacji na podstawie reguł analityków.
  - **Fałszowanie wewnątrz organizacji**: nadawca próbuje sfałszować domenę adresata.
  - **Fałszowanie domeny zewnętrznej**: nadawca próbuje sfałszować inną domenę.
  - **Spoof DMARC**: błąd uwierzytelniania DMARC w komunikatach.
  - **Marka personifikacji**: Personifikacja znanych marek na podstawie nadawców.
  - **Wykrywanie analizy mieszanej**
  - **Reputacja pliku**
  - **Dopasowywanie odcisków palców**
  - **Reputacja detonacji adresu URL**<sup>\*</sup>
  - **Detonacja adresu URL**<sup>\*</sup>
  - **Personifikacja użytkownika**<sup>\*</sup>
  - Domena <sup>\*</sup>**personifikacji**: personifikacja domen, które klient jest właścicielem lub definiuje.
  - **Personifikacja analizy skrzynki pocztowej**: personifikacja użytkowników zdefiniowanych przez administratora lub poznana za pośrednictwem analizy skrzynki pocztowej.<sup>\*</sup>
  - **Detonacja pliku**<sup>\*</sup>
  - **Reputacja detonacji plików**<sup>\*</sup>
  - **Kampanii**<sup>\*</sup>
- **Chronione przez**: **MDO** (Ochrona usługi Office 365 w usłudze Defender) lub **EOP**
- **Kierunek**:
  - **Wszystkie**
  - **Przychodzących**
  - **Wychodzące**
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu).
- **Domena**: **Wszystkie** lub [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Typ zasad**:
  - **Wszystkie**
  - **Ochrona przed złośliwym oprogramowaniem**
  - **załączniki Sejf**
  - **Anty-phish**
  - **Ochrona przed spamem**
  - **Reguła przepływu poczty** (reguła transportu)
  - **Innych**
- **Nazwa zasad (tylko widok tabeli szczegółów)**: **Wszystkie** lub określone zasady.
- **Adresatów**

<sup>\*</sup>tylko Ochrona usługi Office 365 w usłudze Defender

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Stan ochrony przed zagrożeniami** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

### <a name="chart-breakdown-by-delivery-status"></a>Podział wykresu według stanu dostarczania

:::image type="content" source="../../media/threat-protection-status-report-phishing-delivery-status-view.png" alt-text="Widok stanu dostarczania wiadomości e-mail wyłudzającej informacje i wiadomości e-mail o złośliwym oprogramowaniu w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-phishing-delivery-status-view.png":::

W **widokach Wyświetl dane według poczty e-mail \> Phish**, **Wyświetl dane według spamu poczty e-mail \>** lub **Wyświetl dane według złośliwego oprogramowania pocztą e-mail \>** wybranie **pozycji Podział wykresu według stanu dostarczania** pokazuje następujące informacje na wykresie:

- **Hostowana skrzynka pocztowa: Skrzynka odbiorcza**
- **Hostowana skrzynka pocztowa: Śmieci**
- **Hostowana skrzynka pocztowa: folder niestandardowy**
- **Hostowana skrzynka pocztowa: usunięte elementy**
- **Przekazywane**
- **Serwer lokalny: Dostarczone**
- **Kwarantanna**
- **Dostarczanie nie powiodło się**
- **Spadła**

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data**
- **Temat**
- **Nadawcy**
- **Adresatów**
- **Technologia wykrywania**
- **Stan dostarczania**
- **Adres IP nadawcy**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Wykrywanie**:
  - **Złośliwa reputacja**<sup>\*</sup> adresu URL: reputacja złośliwego adresu URL wygenerowana na podstawie detonacji Ochrona usługi Office 365 w usłudze Defender w innych Microsoft 365 klientów.
  - **Filtr zaawansowany**: sygnały wyłudzające informacje oparte na uczeniu maszynowym.
  - **Filtr ogólny**: wyłudzanie informacji na podstawie reguł analityków.
  - **Fałszowanie wewnątrz organizacji**: nadawca próbuje sfałszować domenę adresata.
  - **Fałszowanie domeny zewnętrznej**: nadawca próbuje sfałszować inną domenę.
  - **Spoof DMARC**: błąd uwierzytelniania DMARC w komunikatach.
  - **Marka personifikacji**: Personifikacja znanych marek na podstawie nadawców.
  - **Wykrywanie analizy mieszanej**
  - **Reputacja pliku**
  - **Dopasowywanie odcisków palców**
  - **Reputacja detonacji adresu URL**<sup>\*</sup>
  - **Detonacja adresu URL**<sup>\*</sup>
  - **Personifikacja użytkownika**<sup>\*</sup>
  - Domena <sup>\*</sup>**personifikacji**: personifikacja domen, które klient jest właścicielem lub definiuje.
  - **Personifikacja analizy skrzynki pocztowej**: personifikacja użytkowników zdefiniowanych przez administratora lub poznana za pośrednictwem analizy skrzynki pocztowej.<sup>\*</sup>
  - **Detonacja pliku**<sup>\*</sup>
  - **Reputacja detonacji plików**<sup>\*</sup>
  - **Kampanii**<sup>\*</sup>
- **Chronione przez**: **MDO** (Ochrona usługi Office 365 w usłudze Defender) lub **EOP**
- **Kierunek**:
  - **Wszystkie**
  - **Przychodzących**
  - **Wychodzące**
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu).
- **Domena**: **Wszystkie** lub [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Typ zasad**:
  - **Wszystkie**
  - **Ochrona przed złośliwym oprogramowaniem**
  - **załączniki Sejf**
  - **Anty-phish**
  - **Ochrona przed spamem**
  - **Reguła przepływu poczty** (reguła transportu)
  - **Innych**
- **Nazwa zasad (tylko widok tabeli szczegółów)**: **Wszystkie** lub określone zasady.
- **Adresatów**

<sup>\*</sup>tylko Ochrona usługi Office 365 w usłudze Defender

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Stan ochrony przed zagrożeniami** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

### <a name="view-data-by-content--malware"></a>Wyświetlanie danych według złośliwego oprogramowania zawartości \>

:::image type="content" source="../../media/threat-protection-status-report-content-malware-view.png" alt-text="Widok Złośliwe oprogramowanie zawartości w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-content-malware-view.png":::

W widoku **Wyświetl dane według złośliwego oprogramowania zawartości \>** na wykresie przedstawiono następujące informacje dla organizacji Ochrona usługi Office 365 w usłudze Microsoft Defender:

- **Aparat ochrony przed złośliwym oprogramowaniem**: złośliwe pliki wykryte w SharePoint, OneDrive i Microsoft Teams przez [wbudowane wykrywanie wirusów w Microsoft 365](virus-detection-in-spo.md).
- **Detonacja MDO**: złośliwe pliki wykryte przez [Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).
- **Reputacja pliku**

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data (UTC)**
- **Nazwa pliku załącznika**
- **Obciążenia**
- **Technologia wykrywania**
- **Rozmiar pliku**
- **Ostatnia modyfikacja użytkownika**

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Wykrywanie**: **aparat chroniący przed złośliwym oprogramowaniem**, **detonacja MDO** i **detonacja plików**
- **Obciążenie**: **Teams**, **SharePoint** i **OneDrive**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Stan ochrony przed zagrożeniami** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

### <a name="view-data-by-system-override-and-chart-breakdown-by-reason"></a>Wyświetlanie danych według zastąpienia systemu i podział wykresu według przyczyny

:::image type="content" source="../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png" alt-text="Widok Przesłoń komunikat i Wykres według przyczyny w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png":::

W widoku **Wyświetl dane według przesłonięcia systemu** i **wykresu według przyczyny** na wykresie przedstawiono następujące informacje o przyczynach zastąpienia:

- **Pominięcie w środowisku lokalnym**
- **Zezwalaj na adres IP**
- **reguła transportu Exchange** (reguła przepływu poczty)
- **Dozwoloni nadawcy w organizacji**
- **Dozwolone domeny organizacji**
- **Zap nie jest włączona**
- **Nadawca Sejf użytkownika**
- **Domena Sejf użytkownika**
- **Symulacja wyłudzania** informacji: Aby uzyskać więcej informacji, zobacz [Konfigurowanie dostarczania symulacji wyłudzania informacji innym firmom użytkownikom i niefiltrowanych wiadomości do skrzynek pocztowych SecOps](configure-advanced-delivery.md).
- **Filtr innej firmy**

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data**
- **Temat**
- **Nadawcy**
- **Adresatów**
- **Zastępowanie systemu**
- **Adres IP nadawcy**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Przyczyna**: te same wartości co wykres.
- **Lokalizacja dostarczania**: **folder wiadomości-śmieci nie jest włączony** lub **skrzynka pocztowa SecOps**.
- **Kierunek**:
  - **Wszystkie**
  - **Przychodzących**
  - **Wychodzące**
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu).
- **Domena**: **Wszystkie** lub [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Typ zasad**: **Wszystkie**
- **Nazwa zasad (tylko widok tabeli szczegółów)**: **Wszystkie**
- **Adresatów**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Stan ochrony przed zagrożeniami** ikona ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przycisk Eksportuj](#export-report)** jest dostępny.

### <a name="view-data-by-system-override-and-chart-breakdown-by-delivery-location"></a>Wyświetlanie danych według zastąpienia systemu i podział wykresu według lokalizacji dostarczania

:::image type="content" source="../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png" alt-text="Widok Przesłoń komunikaty i Wykres według lokalizacji dostarczania w raporcie o stanie ochrony przed zagrożeniami" lightbox="../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png":::

W widoku **Wyświetl dane według przesłonięcia systemu** i **wykresu według widoku Lokalizacja dostarczania** na wykresie są wyświetlane następujące informacje o przyczynach zastąpienia:

- **Folder wiadomości-śmieci nie jest włączony**
- **Skrzynka pocztowa SecOps**: Aby uzyskać więcej informacji, zobacz [Konfigurowanie dostarczania symulacji wyłudzania informacji innym firmom użytkownikom i niefiltrowanych wiadomości do skrzynek pocztowych SecOps](configure-advanced-delivery.md).

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data**
- **Temat**
- **Nadawcy**
- **Adresatów**
- **Zastępowanie systemu**
- **Adres IP nadawcy**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Jeśli klikniesz pozycję **Filtruj**, dostępne są następujące filtry:

- **Data (UTC)** **data rozpoczęcia** i **data zakończenia**
- **Powodu**
  - **Pominięcie w środowisku lokalnym**
  - **Zezwalaj na adres IP**
  - **reguła transportu Exchange** (reguła przepływu poczty)
  - **Dozwoloni nadawcy w organizacji**
  - **Dozwolone domeny organizacji**
  - **Zap nie jest włączona**
  - **Nadawca Sejf użytkownika**
  - **Domena Sejf użytkownika**
  - **Symulacja wyłudzania** informacji: Aby uzyskać więcej informacji, zobacz [Konfigurowanie dostarczania symulacji wyłudzania informacji innym firmom użytkownikom i niefiltrowanych wiadomości do skrzynek pocztowych SecOps](configure-advanced-delivery.md).
  - **Filtr innej firmy**
- **Lokalizacja dostarczania**: **folder wiadomości-śmieci nie jest włączony** lub **skrzynka pocztowa SecOps**.
- **Kierunek**:
  - **Wszystkie**
  - **Przychodzących**
  - **Wychodzące**
- **Tag**: **Wszystkie** lub określony tag użytkownika (w tym konta priorytetu). Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).
- **Domena**: **Wszystkie** lub [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Typ zasad**:
  - **Wszystkie**
  - **Ochrona przed złośliwym oprogramowaniem**
  - **załączniki Sejf**<sup>\*</sup>
  - **Anty-phish**
  - **Ochrona przed spamem**
  - **Reguła przepływu poczty** (reguła transportu)
  - **Innych**
- **Nazwa zasad (tylko widok tabeli szczegółów)**: **Wszystkie**
- **Adresatów**

<sup>\*</sup>tylko Ochrona usługi Office 365 w usłudze Defender

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Stan ochrony przed zagrożeniami** ikona ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przycisk Eksportuj](#export-report)** jest dostępny.

## <a name="top-malware-report"></a>Raport o najpopularniejszym złośliwym oprogramowaniu

Raport **Najpopularniejsze złośliwe oprogramowanie** przedstawia różne rodzaje złośliwego oprogramowania wykryte przez [ochronę przed złośliwym oprogramowaniem w ramach EOP](anti-malware-protection.md).

Aby wyświetlić raport w portalu Microsoft 365 Defender, przejdź do pozycji **Raporty** \> **Wiadomości e-mail & współpracy** \> **E-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź **najważniejsze złośliwe oprogramowanie** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz plik <https://security.microsoft.com/reports/TopMalware>.

:::image type="content" source="../../media/top-malware-report-widget.png" alt-text="Widżet Najlepsze złośliwe oprogramowanie na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/top-malware-report-widget.png":::

Po umieszczeniu wskaźnika myszy na klinze na wykresie kołowym można zobaczyć nazwę rodzaju złośliwego oprogramowania i liczbę wykrytych komunikatów jako mających to złośliwe oprogramowanie.

Na stronie **Raport o najpopularniejszym złośliwym oprogramowaniu** jest wyświetlana większa wersja wykresu kołowego. Poniższa tabela szczegółów przedstawia następujące informacje:

- **Najważniejsze złośliwe oprogramowanie**
- **Liczba**

Jeśli klikniesz pozycję **Filtruj**, możesz określić zakres dat z **datą rozpoczęcia** i **datą zakończenia**.

Na stronie **Najważniejsze złośliwe oprogramowanie** ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Utwórz ikonę harmonogramu](#schedule-report)** i ![eksportu.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](#export-report)** są dostępne.

:::image type="content" source="../../media/top-malware-report-view.png" alt-text="Widokraportuegoaa" lightbox="../../media/top-malware-report-view.png":::

## <a name="top-senders-and-recipients-report"></a>Raport najpopularniejszych nadawców i adresatów

Raport **Najpopularniejszych nadawców i adresatów** jest dostępny zarówno w ramach operacji EOP, jak i Ochrona usługi Office 365 w usłudze Defender. Raporty zawierają jednak inne dane. Na przykład klienci EOP mogą wyświetlać informacje o najważniejszych adresatach złośliwego oprogramowania, spamu i wyłudzania informacji (fałszowanie), ale nie o złośliwym oprogramowaniu wykrytym przez [Sejf Załączniki lub wyłudzanie](safe-attachments.md) informacji wykryte przez [ochronę przed personifikacją](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

**W obszarze Najważniejsi nadawcy i adresaci** są wyświetlane najważniejsze wiadomości nadawców w organizacji, a także najważniejsi adresaci wiadomości wykrytych przez funkcję EOP i funkcje ochrony Ochrona usługi Office 365 w usłudze Defender. Domyślnie raport pokazuje dane z ostatniego tygodnia, ale dane są dostępne w ciągu ostatnich 90 dni.

Aby wyświetlić raport w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do pozycji **Raporty Wiadomości** \> **e-mail & współpracy** \> **Wiadomości e-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź **raport Najpopularniejszi nadawcy i adresaci** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz jeden z następujących adresów URL:

- Ochrona usługi Office 365 w usłudze Defender:<https://security.microsoft.com/reports/TopSenderRecipientsATP>
- EOP: <https://security.microsoft.com/reports/TopSenderRecipient>

:::image type="content" source="../../media/top-senders-and-recipients-widget.png" alt-text="Widżet Najważniejsi nadawcy i adresaci na pulpicie nawigacyjnym Raporty" lightbox="../../media/top-senders-and-recipients-widget.png":::

Po umieszczeniu wskaźnika myszy na klinze na wykresie kołowym zobaczysz liczbę komunikatów dla nadawcy lub odbiorcy.

Na stronie **Najwięksi nadawcy i adresaci** zostanie wyświetlona większa wersja wykresu kołowego. Dostępne są następujące wykresy:

- **Pokaż dane dla najpopularniejszych nadawców poczty** (jest to widok domyślny)
- **Pokaż dane dla najpopularniejszych adresatów poczty**
- **Pokaż dane dla najpopularniejszych adresatów spamu**
- **Pokaż dane dla najpopularniejszych adresatów złośliwego oprogramowania** (EOP)
- **Pokaż dane dla najważniejszych adresatów wyłudzania informacji**
- **Pokaż dane dla najważniejszych adresatów złośliwego oprogramowania (MDO)**
- **Pokaż dane dla najważniejszych adresatów języka phish (MDO)**

Dane są zmieniane na podstawie wybranego ustawienia.

Po umieszczeniu wskaźnika myszy na klinze na wykresie kołowym będzie widoczna liczba komunikatów dla określonego nadawcy lub odbiorcy.

W tabeli szczegółów poniżej wykresu przedstawiono nadawców lub adresatów oraz liczbę wiadomości na podstawie wybranego widoku.

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając **pozycję Data rozpoczęcia** i **Data zakończenia**.

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Na stronie **Najważniejsi nadawcy i adresaci** ikona ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **Przycisk Eksportuj** jest dostępny.

:::image type="content" source="../../media/top-senders-and-recipients-report-view.png" alt-text="Widok Pokaż dane dla najpopularniejszych nadawców poczty w raporcie Najważniejsi nadawcy i adresaci" lightbox="../../media/top-senders-and-recipients-report-view.png":::

## <a name="url-protection-report"></a>Raport ochrony adresu URL

**Raport ochrony adresu URL** jest dostępny tylko w Ochrona usługi Office 365 w usłudze Microsoft Defender. Aby uzyskać więcej informacji, zobacz [Raport ochrony adresu URL](view-reports-for-mdo.md#url-protection-report).

## <a name="user-reported-messages-report"></a>Raport komunikatów zgłoszonych przez użytkownika

> [!IMPORTANT]
> Aby raport Komunikaty **zgłaszane przez użytkownika** działał poprawnie, **należy włączyć rejestrowanie inspekcji** dla środowiska Microsoft 365. Zwykle jest to wykonywane przez osobę, która ma rolę Dzienniki inspekcji przypisane w Exchange Online. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji Microsoft 365](../../compliance/turn-audit-log-search-on-or-off.md).

Raport **Wiadomości zgłaszane przez użytkownika** zawiera informacje o wiadomościach e-mail zgłaszanych przez użytkowników jako wiadomości-śmieci, próbach wyłudzania informacji lub dobrej wiadomości za pomocą [dodatku Wiadomości raportu](enable-the-report-message-add-in.md) lub [dodatku Wyłudzanie informacji o raportach](enable-the-report-phish-add-in.md).

Aby wyświetlić raport w portalu Microsoft 365 Defender, przejdź do pozycji **Raporty** \> **Wiadomości e-mail & współpracy** \> **E-mail & raporty współpracy**. Na stronie **Raporty współpracy & poczty e-mail** znajdź **komunikaty zgłaszane przez użytkownika** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz plik <https://security.microsoft.com/reports/userSubmissionReport>. Aby przejść do [przesyłania przez administratora w portalu Microsoft 365 Defender](admin-submission.md), kliknij pozycję **Przejdź do pozycji Przesłane**.

:::image type="content" source="../../media/user-reported-messages-widget.png" alt-text="Widżet wiadomości zgłoszonych przez użytkownika na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/user-reported-messages-widget.png":::

Możesz filtrować zarówno wykres, jak i tabelę szczegółów, klikając pozycję **Filtruj** i wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwie:

- **Zgłoszona data**: **godzina rozpoczęcia** i **godzina zakończenia**
- **Zgłoszone przez**
- **Temat wiadomości e-mail**
- **Identyfikator zgłoszonych komunikatów**
- **Identyfikator komunikatu sieci**
- **Nadawcy**
- **Zgłoszona przyczyna**
  - **Nie śmieci**
  - **Phish**
  - **Spam**
- **Symulacja phish**: **Tak** lub **Nie**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Aby pogrupować wpisy, kliknij pozycję **Grupuj** i wybierz jedną z następujących wartości z listy rozwijanej:

- **Brak**
- **Powodu**
- **Nadawcy**
- **Zgłoszone przez**
- **Wynik ponownego skanowania**
- **Symulacja phish**

:::image type="content" source="../../media/user-reported-messages-report.png" alt-text="Raport komunikatów zgłaszanych przez użytkownika" lightbox="../../media/user-reported-messages-report.png":::

Poniższa tabela szczegółów przedstawia następujące informacje:

- **Temat wiadomości e-mail**
- **Zgłoszone przez**
- **Data zgłoszenia**
- **Nadawcy**
- **Zgłoszona przyczyna**
- **Wynik ponownego skanowania**
- **Tagi**: Aby uzyskać więcej informacji na temat tagów użytkowników, zobacz [Tagi użytkowników](user-tags.md).

Aby przesłać wiadomość do firmy Microsoft do analizy, wybierz wpis komunikatu z tabeli, kliknij pozycję **Prześlij do firmy Microsoft do analizy** , a następnie wybierz jedną z następujących wartości z listy rozwijanej:

- **Raport jest czysty**
- **Zgłaszanie wyłudzania informacji**
- **Zgłaszanie złośliwego oprogramowania**
- **Zgłaszanie spamu**
- **Badanie wyzwalacza** (Ochrona usługi Office 365 w usłudze Defender)

Na stronie **Komunikaty zgłaszane przez użytkownika** ikona ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przycisk Eksportuj](#export-report)** jest dostępny.

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Jakie uprawnienia są potrzebne do wyświetlania tych raportów?

Aby wyświetlić raporty opisane w tym artykule i korzystać z nich, musisz być członkiem jednej z następujących grup ról w portalu Microsoft 365 Defender:

- **Zarządzanie organizacją**
- **Administrator zabezpieczeń**
- **Czytelnik zabezpieczeń**
- **Czytelnik globalny**

Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

**Uwaga**: dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender _i_ uprawnienia do innych funkcji w witrynie Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Co zrobić, jeśli raporty nie pokazują danych?

Jeśli nie widzisz danych w raportach, sprawdź używane filtry i sprawdź, czy zasady są prawidłowo skonfigurowane. Aby dowiedzieć się więcej, zobacz [Ochrona przed zagrożeniami](protect-against-threats.md).

## <a name="schedule-report"></a>Raport harmonogramu

1. Na stronie głównej określonego raportu kliknij ikonę ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **Utwórz harmonogram**.
2. Zostanie otwarty kreator **Tworzenia zaplanowanego raportu** . Na stronie **Nazwa zaplanowanego raportu** przejrzyj lub dostosuj wartość **Nazwa** , a następnie kliknij przycisk **Dalej**.
3. Na stronie **Ustawianie preferencji** skonfiguruj następujące ustawienia:
   - **Częstotliwość**: wybierz jedną z następujących wartości:
     - **Tygodniowy** (domyślny)
     - **Miesięczne**
   - **Data rozpoczęcia**: kiedy rozpoczyna się generowanie raportu. Wartość domyślna to dzisiaj.
   - **Data wygaśnięcia**: po zakończeniu generowania raportu. Wartość domyślna to rok od dnia dzisiejszego.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Adresaci** wybierz adresatów raportu. Wartość domyślna to Twój adres e-mail, ale możesz dodać inne.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Przegląd** przejrzyj wybrane opcje. Aby wprowadzić zmiany, możesz kliknąć przycisk **Wstecz** lub link **Edytuj** w odpowiednich sekcjach.

   Po zakończeniu kliknij pozycję **Prześlij**.

### <a name="managed-existing-scheduled-reports"></a>Zarządzane istniejące zaplanowane raporty

Aby zarządzać utworzonymi już zaplanowanymi raportami, wykonaj następujące czynności:

1. W portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com>przejdź do pozycji **Raporty** rozwiń węzeł Poczta \> **e-mail & współpracy** \> wybierz pozycję **Zarządzaj harmonogramami**.

   Aby przejść bezpośrednio do strony **Zarządzanie harmonogramami** , użyj polecenia <https://security.microsoft.com/ManageSubscription>.

2. Na stronie **Zarządzanie harmonogramami** są wyświetlane następujące informacje dla każdego zaplanowanego raportu:
   - **Data rozpoczęcia harmonogramu**
   - **Nazwa harmonogramu**
   - **Typ raportu**
   - **Częstotliwości**
   - **Ostatnio wysłane**

   Znajdź istniejący zaplanowany raport, który chcesz zmodyfikować.

3. Po wybraniu zaplanowanego raportu wykonaj dowolną z następujących akcji w wyświetlonym wysuwanym oknie szczegółów:
   - **Edytuj nazwę**: kliknij ten przycisk, zmień nazwę raportu w wyświetlonym wysuwaniu, a następnie kliknij przycisk **Zapisz**.
   - **Harmonogram usuwania**: kliknij ten przycisk, przeczytaj wyświetlone ostrzeżenie (poprzednie raporty nie będą już dostępne do pobrania), a następnie kliknij przycisk **Zapisz**.
   - Sekcja **Szczegóły harmonogramu**: Kliknij pozycję **Edytuj preferencje,** aby zmienić następujące ustawienia:
     - **Częstotliwość**: **co tydzień** lub **co miesiąc**
     - **Data rozpoczęcia**
     - **Data wygaśnięcia**

     Po zakończeniu kliknij przycisk **Zapisz**.

   - Sekcja **Adresaci**: kliknij pozycję **Edytuj adresatów**, aby dodać lub usunąć adresatów zaplanowanego raportu. Po zakończeniu kliknij pozycję **Zapisz**

   Po wprowadzeniu wszystkich zmian kliknij przycisk **Zamknij**.

## <a name="request-report"></a>Raport żądania

1. Na stronie głównej konkretnego raportu kliknij ikonę ![Zażądaj raportu.](../../media/m365-cc-sc-download-icon.png) **Żądanie raportu**.
2. Zostanie otwarty kreator **tworzenia raportu na żądanie** . Na stronie **Raport nazwa na żądanie** przejrzyj lub dostosuj wartość **Nazwa** , a następnie kliknij przycisk **Dalej**.
3. Na stronie **Ustawianie preferencji** przejrzyj lub skonfiguruj następujące ustawienia:
   - **Data rozpoczęcia**: kiedy rozpoczyna się generowanie raportu. Wartość domyślna to miesiąc temu.
   - **Data wygaśnięcia**: po zakończeniu generowania raportu. Wartość domyślna to dzisiaj.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Adresaci** wybierz adresatów raportu. Wartość domyślna to Twój adres e-mail, ale możesz dodać inne.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Przegląd** przejrzyj wybrane opcje. Aby wprowadzić zmiany, możesz kliknąć przycisk **Wstecz** lub link **Edytuj** w odpowiednich sekcjach.

   Po zakończeniu kliknij pozycję **Prześlij**.

6. Po pomyślnym utworzeniu raportu nastąpi przekierowanie do strony **Nowy raport na żądanie,** na której można kliknąć pozycję **Utwórz inny raport** lub **Gotowe**.

   Raport jest również dostępny na stronie **Raporty do pobrania** zgodnie z opisem w następnej sekcji.

### <a name="download-reports"></a>Pobieranie raportów

1. W portalu Microsoft 365 Defender pod adresem przejdź do obszaru <https://security.microsoft.com>Raporty rozwiń węzeł **Poczta** \> **e-mail & współpracy** \> wybierz pozycję **Raporty do pobrania**.

   Aby przejść bezpośrednio do strony **Raporty do pobrania** , użyj polecenia <https://security.microsoft.com/ReportsForDownload>.

2. Na stronie **Raporty do pobrania** są wyświetlane następujące informacje dla każdego dostępnego raportu:
   - **Data rozpoczęcia**
   - **Nazwa**
   - **Typ raportu**
   - **Ostatnio wysłane**
   - **Kierunek**

   Znajdź i wybierz raport, który chcesz pobrać.

## <a name="export-report"></a>Eksportowanie raportu

Na stronie głównej określonego raportu kliknij ikonę ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **Eksportuj** (jeśli ten link jest dostępny). Zostanie wyświetlone okno wysuwane **Warunki eksportu** , w którym można skonfigurować następujące ustawienia:

- **Wybierz widok do wyeksportowania**: Wybierz jedną z następujących wartości:
  - **Podsumowanie**: Dane są dostępne w ciągu ostatnich 90 dni.
  - **Szczegóły**: Dane są dostępne w ciągu ostatnich 30 dni.
- **Data (UTC)**: **data rozpoczęcia** i **data zakończenia**.

Po zakończeniu konfigurowania filtrów kliknij pozycję **Eksportuj**. W otwartym oknie dialogowym możesz otworzyć plik, zapisać plik lub zapamiętać zaznaczenie.

Każdy wyeksportowany plik .csv jest ograniczony do 150 000 wierszy. Jeśli dane zawierają więcej niż 150 000 wierszy, zostanie utworzonych wiele .csv plików.

## <a name="related-topics"></a>Tematy pokrewne

[Ochrona przed spamem i złośliwym oprogramowaniem w ramach EOP](anti-spam-and-anti-malware-protection.md)

[Inteligentne raporty i szczegółowe informacje w portalu Microsoft 365 Defender](reports-and-insights-in-security-and-compliance.md)

[Wyświetlanie raportów przepływu poczty w portalu Microsoft 365 Defender](view-mail-flow-reports.md)

[Wyświetlanie raportów dla Ochrona usługi Office 365 w usłudze Defender](view-reports-for-mdo.md)
