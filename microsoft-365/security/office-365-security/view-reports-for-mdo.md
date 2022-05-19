---
title: Wyświetlanie raportów ochrony usługi Office 365 w usłudze Defender
f1.keywords:
- CSH
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
ms.assetid: e47e838c-d99e-4c0b-b9aa-e66c4fae902f
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorzy mogą dowiedzieć się, jak znaleźć raporty Ochrona usługi Office 365 w usłudze Defender dostępne w portalu Microsoft 365 Defender i korzystać z nich.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 08fd6e2fed34296b42fb3b12bec9b5b2b4cb91f8
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535851"
---
# <a name="view-defender-for-office-365-reports-in-the-microsoft-365-defender-portal"></a>Wyświetlanie raportów Ochrona usługi Office 365 w usłudze Defender w portalu Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Ochrona usługi Office 365 w usłudze Microsoft Defender organizacje (na przykład Microsoft 365 E5 subskrypcje lub Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 lub dodatki Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2) zawierają różne raporty związane z zabezpieczeniami. Jeśli masz [niezbędne uprawnienia](#what-permissions-are-needed-to-view-the-defender-for-office-365-reports), możesz wyświetlać i pobierać te raporty w portalu Microsoft 365 Defender.

## <a name="view-and-download-reports"></a>Wyświetlanie oraz pobieranie raportów

### <a name="view-reports"></a>Wyświetlanie raportów

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Raporty** \> **e-mail & współpracy** \> **e-mail raporty dotyczące współpracy & poczty e-mail**. Aby przejść bezpośrednio do strony **Raporty współpracy & poczty e-mail** , użyj polecenia <https://security.microsoft.com/emailandcollabreport>.

1. Wybierz raport, który chcesz wyświetlić, a następnie wybierz pozycję **Wyświetl szczegóły**.

### <a name="download-reports"></a>Pobieranie raportów

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **RaportySzaporty** >  **& współpracy** \> pocztą **e-mail do pobrania**. Aby przejść bezpośrednio do strony **Raporty do pobrania** , użyj polecenia <https://security.microsoft.com/ReportsForDownload?viewid=custom>.

:::image type="content" source="../../media/email-collaboration-download-reports.png" alt-text="Strona Raporty dotyczące współpracy & poczty e-mail w portalu Microsoft 365 Defender" lightbox="../../media/email-collaboration-download-reports.png":::

> [!NOTE]
>
> Raporty zabezpieczeń poczty e-mail, które nie wymagają Ochrona usługi Office 365 w usłudze Defender, zostały opisane w [temacie Wyświetlanie raportów zabezpieczeń poczty e-mail w portalu Microsoft 365 Defender](view-email-security-reports.md).
>
> Raporty związane z przepływem poczty znajdują się teraz w centrum administracyjnym Exchange (EAC). Aby uzyskać więcej informacji na temat tych raportów, zobacz [Raporty przepływu poczty w nowym centrum administracyjnym Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="safe-attachments-file-types-report"></a>raport typów plików załączników Sejf

> [!NOTE]
> Ten raport został przestarzały. Te same informacje są dostępne w [raporcie o stanie ochrony przed zagrożeniami](#threat-protection-status-report).

## <a name="safe-attachments-message-disposition-report"></a>raport dyspozycji komunikatów załączników Sejf

> [!NOTE]
> Ten raport został przestarzały. Te same informacje są dostępne w [raporcie o stanie ochrony przed zagrożeniami](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Raport opóźnienia poczty

**Raport Opóźnienie poczty** przedstawia zagregowany widok opóźnienia dostarczania i detonacji poczty w organizacji. Na czas dostarczania wiadomości e-mail w usłudze wpływa wiele czynników, a bezwzględny czas dostarczania w sekundach często nie jest dobrym wskaźnikiem sukcesu lub problemu. Powolny czas dostarczania w jednym dniu można uznać za średni czas dostawy w innym dniu lub odwrotnie. Próbuje to zakwalifikować dostarczanie komunikatów na podstawie danych statystycznych dotyczących obserwowanych czasów dostarczania innych komunikatów.

Opóźnienie po stronie klienta i sieci nie jest uwzględniane.

Aby wyświetlić raport, otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do pozycji **Raporty** **e-mail & współpracy** \> **E-mail Raporty**\> & raporty współpracy. Aby przejść bezpośrednio do strony **Raporty współpracy & poczty e-mail** , użyj polecenia <https://security.microsoft.com/emailandcollabreport>.

Na stronie **Raporty współpracy & poczty e-mail** znajdź **raport opóźnienia poczty** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, użyj polecenia <https://security.microsoft.com/mailLatencyReport>.

:::image type="content" source="../../media/mail-latency-report-widget.png" alt-text="Widżet Raport opóźnienia poczty na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/mail-latency-report-widget.png":::

Na stronie **Raport opóźnienia poczty** na stronie **Raport opóźnienia** poczty są dostępne następujące karty:

- **50. percentyl**: jest to środek czasu dostarczania komunikatów. Tę wartość można traktować jako średni czas dostarczania. Ta karta jest domyślnie zaznaczona.
- **90. percentyl**: oznacza to duże opóźnienie dostarczania komunikatów. Dostarczenie tylko 10% komunikatów trwało dłużej niż ta wartość.
- **99. percentyl**: oznacza to największe opóźnienie dostarczania komunikatów.

Niezależnie od wybranej karty na wykresie są wyświetlane komunikaty uporządkowane w następujących kategoriach:

- **Ogólnej**
- **Detonacji**

Po umieszczeniu wskaźnika myszy na kategorii na wykresie można zobaczyć podział opóźnienia w każdej kategorii.

:::image type="content" source="../../media/mail-latency-report-50th-percentile-view.png" alt-text="Widok 50. percentyli raportu opóźnienia poczty" lightbox="../../media/mail-latency-report-50th-percentile-view.png":::

Jeśli klikniesz pozycję **Filtruj**, możesz filtrować wykres i tabelę szczegółów według następujących wartości:

- **Data (UTC)**: **data rozpoczęcia** i **data zakończenia**
- **Widok komunikatu**: Jedna z następujących wartości:
  - **Wszystkie wiadomości**
  - **Zdetonowane komunikaty**: Jedna z następujących wartości:
    - **Detonacja wbudowana**: zawiera komunikaty, które są w pełni przetestowane przed dostarczeniem.
    - **Detonacja asynchroniczna**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

W tabeli szczegółów poniżej wykresu dostępne są następujące informacje:

- **Data (UTC)**
- **Opóźnienie**
- **Liczba komunikatów**
- **50. percentyl**
- **90. percentyl**
- **99. percentyl**

Na stronie raportu głównego ikona ![Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przycisk Eksportuj](view-email-security-reports.md#export-report)** jest dostępny.

## <a name="threat-protection-status-report"></a>Raport o stanie ochrony przed zagrożeniami

Raport o **stanie ochrony przed zagrożeniami** to pojedynczy widok, który łączy informacje o złośliwej zawartości i złośliwej wiadomości e-mail wykrytej i zablokowanej przez [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) i Ochrona usługi Office 365 w usłudze Microsoft Defender. Aby uzyskać więcej informacji, zobacz [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).

## <a name="top-senders-and-recipients-report"></a>Raport najpopularniejszych nadawców i adresatów

W raporcie **Najważniejsi nadawcy i adresaci** są widoczni najważniejsi adresaci funkcji EOP i Ochrona usługi Office 365 w usłudze Defender ochrony. Aby uzyskać więcej informacji, zobacz [Raport najpopularniejszych nadawców i adresatów](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="url-protection-report"></a>Raport ochrony adresu URL

**Raport ochrony adresu URL** zawiera podsumowanie i wyświetlenia trendów dla wykrytych zagrożeń i akcji wykonywanych przy kliknięciach adresu URL w ramach [linków Sejf](safe-links.md). Ten raport nie będzie zawierać danych kliknięć od użytkowników, dla których zasady Sejf Łącza zostały zastosowane, gdy opcja **Śledź kliknięcia użytkownika** nie jest zaznaczona.

Aby wyświetlić raport, otwórz [portal Microsoft 365 Defender](https://security.microsoft.com), przejdź do obszaru **Raporty Poczta** **e-mail & współpracy** \> **e-mail Raporty & raporty współpracy w wiadomościach e-mail**.\> Na stronie **Raporty współpracy & poczty e-mail** znajdź **stronę ochrony adresu URL** , a następnie kliknij pozycję **Wyświetl szczegóły**. Aby przejść bezpośrednio do raportu, otwórz plik <https://security.microsoft.com/reports/URLProtectionActionReport>.

:::image type="content" source="../../media/url-protection-report-widget.png" alt-text="Widżet raportu ochrony adresu URL na stronie Raporty współpracy & poczty e-mail" lightbox="../../media/url-protection-report-widget.png":::

Dostępne widoki na stronie raportu **ochrony adresu URL** zostały opisane w poniższych sekcjach.

> [!NOTE]
> Jest to *raport trendu ochrony*, co oznacza, że dane reprezentują trendy w większym zestawie danych. W związku z tym dane na wykresach nie są tutaj dostępne w czasie rzeczywistym, ale dane w tabeli szczegółów są takie, że mogą wystąpić niewielkie rozbieżności między nimi. Wykresy są odświeżane co cztery godziny i zawierają dane z ostatnich 90 dni.

### <a name="view-data-by-url-click-protection-action"></a>Wyświetlanie danych według adresu URL — akcja ochrony

:::image type="content" source="../../media/url-threat-protection-report-url-click-protection-action-view.png" alt-text="Widok, czyli akcja ochrony kliknięcia adresu URL w raporcie ochrony adresu URL" lightbox="../../media/url-threat-protection-report-url-click-protection-action-view.png":::

Widok **danych według adresu URL kliknij widok akcji ochrony** pokazuje liczbę kliknięć adresu URL przez użytkowników w organizacji i wyniki kliknięcia:

- **Dozwolone**: kliknięcia są dozwolone.
- **Dozwolone przez administratora dzierżawy**: kliknięcia dozwolone w zasadach linków Sejf.
- **Zablokowane**: kliknij pozycję Zablokowane.
- **Zablokowane przez administratora dzierżawy**: kliknięcia zablokowane w zasadach linków Sejf.
- **Zablokowane i kliknięty:** zablokowane kliknięcia, w których użytkownicy klikają zablokowany adres URL.
- **Zablokowane przez administratora dzierżawy i klikniętych przez**: Administrator zablokował link, ale użytkownik kliknął.
- **Kliknięty podczas skanowania**: kliknięcia, w których użytkownicy klikają oczekującą stronę skanowania pod adresem URL.
- **Oczekujące skanowanie**: klika adresy URL oczekujące na werdykt skanowania.

Kliknięcie oznacza, że użytkownik kliknął stronę bloku do złośliwej witryny internetowej (administratorzy mogą wyłączyć klikanie w zasadach linków Sejf).

Jeśli klikniesz pozycję **Filtry**, możesz zmodyfikować raport i tabelę szczegółów, wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwaniu:

- **Data (UTC)**: **data rozpoczęcia** i **data zakończenia**
- **Akcja**:
  - **Dozwolone**
  - **Zablokowany**
  - **Dozwolone przez administratora dzierżawy**
  - **Zablokowane i klikniętych**
  - **Zablokowane przez administratora dzierżawy i klikniętych**
  - **Kliknięcie podczas skanowania**
  - **Oczekujące skanowanie**
- **Domeny**: domeny adresów URL wymienione w wynikach raportu.
- **Adresatów**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Tabela szczegółów poniżej wykresu zawiera następujący widok niemal w czasie rzeczywistym wszystkich kliknięć, które wystąpiły w organizacji w ciągu ostatnich 7 dni:

- **Godzina kliknięcia**
- **Użytkownik**
- **ADRES URL**
- **Akcja**
- **Aplikacja**

Na głównej stronie raportu ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](view-email-security-reports.md#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](view-email-security-reports.md#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](view-email-security-reports.md#export-report)** są dostępne.

### <a name="view-data-by-url-click-by-application"></a>Wyświetlanie danych według adresu URL kliknij według aplikacji

:::image type="content" source="../../media/url-threat-protection-report-url-click-by-application-view.png" alt-text="Widok akcji kliknij adres URL ochrony w raporcie ochrony adresu URL" lightbox="../../media/url-threat-protection-report-url-click-by-application-view.png":::

Widok **danych według adresu URL kliknięty według widoku aplikacji** pokazuje liczbę kliknięć adresu URL przez aplikacje obsługujące łącza Sejf:

- **Klient poczty e-mail**
- **dokument Office**
- **Teams**

Jeśli klikniesz pozycję **Filtry**, możesz zmodyfikować raport i tabelę szczegółów, wybierając co najmniej jedną z następujących wartości w wyświetlonym wysuwaniu:

- **Data (UTC)**: **data rozpoczęcia** i **data zakończenia**
- **Wykrywanie**: dostępne aplikacje z wykresu.
- **Domeny**: domeny adresów URL wymienione w wynikach raportu.
- **Adresatów**

Po zakończeniu konfigurowania filtrów kliknij pozycję **Zastosuj**, **Anuluj** lub **Wyczyść filtry**.

Tabela szczegółów poniżej wykresu zawiera następujący widok niemal w czasie rzeczywistym wszystkich kliknięć, które wystąpiły w organizacji w ciągu ostatnich 7 dni:

- **Godzina kliknięcia**
- **Użytkownik**
- **ADRES URL**
- **Akcja**
- **Aplikacja**

Na głównej stronie raportu ikona ![Utwórz harmonogram.](../../media/m365-cc-sc-create-icon.png) **[Tworzenie harmonogramu](view-email-security-reports.md#schedule-report)**, ![ikona raportu żądania.](../../media/m365-cc-sc-download-icon.png) **[Żądanie raportu](view-email-security-reports.md#request-report)** i ![ikona Eksportuj.](../../media/m365-cc-sc-download-icon.png) **[Przyciski eksportu](view-email-security-reports.md#export-report)** są dostępne.

## <a name="additional-reports-to-view"></a>Dodatkowe raporty do wyświetlenia

Oprócz raportów opisanych w tym artykule dostępnych jest kilka innych raportów, zgodnie z opisem w poniższej tabeli:

|Raport|Temat|
|---|---|
|**Eksplorator** (Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2) lub **wykrywanie w czasie rzeczywistym** (Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1)|[Eksplorator zagrożeń (i wykrywanie w czasie rzeczywistym)](threat-explorer.md)|
|Wysyłanie wiadomości e-mail z raportami zabezpieczeń, które nie wymagają Ochrona usługi Office 365 w usłudze Defender|[Wyświetlanie raportów zabezpieczeń poczty e-mail w portalu Microsoft 365 Defender](view-email-security-reports.md)|
|Raporty przepływu poczty w centrum administracyjnym Exchange (EAC)|[Raporty przepływu poczty w nowym centrum administracyjnym Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|

Polecenia cmdlet raportowania programu PowerShell:

|Raport|Temat|
|---|---|
|Najważniejsi nadawcy i adresaci|[Get-MailTrafficTopReport](/powershell/module/exchange/get-mailtraffictopreport) <p> [Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Najważniejsze złośliwe oprogramowanie|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Ruch poczty|[Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <p> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|
|Bezpieczne linki|[Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <p> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|
|Użytkownicy z naruszonymi zabezpieczeniami|[Get-CompromisedUserAggregateReport](/powershell/module/exchange/get-compromiseduseraggregatereport) <p> [Get-CompromisedUserDetailReport](/powershell/module/exchange/get-compromiseduserdetailreport)|
|Stan przepływu poczty|[Get-MailflowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|
|Sfałszowane użytkowników|[Get-SpoofMailReport](/powershell/module/exchange/get-spoofmailreport)|

## <a name="what-permissions-are-needed-to-view-the-defender-for-office-365-reports"></a>Jakie uprawnienia są potrzebne do wyświetlania raportów Ochrona usługi Office 365 w usłudze Defender?

Aby wyświetlić raporty opisane w tym artykule i korzystać z nich, musisz być członkiem jednej z następujących grup ról w portalu Microsoft 365 Defender:

- **Zarządzanie organizacją**
- **Administrator zabezpieczeń**
- **Czytelnik zabezpieczeń**
- **Czytelnik globalny**

Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

**Uwaga**: dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender _i_ uprawnienia do innych funkcji w witrynie Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Co zrobić, jeśli raporty nie pokazują danych?

Jeśli nie widzisz danych w raportach Ochrona usługi Office 365 w usłudze Defender, sprawdź, czy zasady są prawidłowo skonfigurowane. Aby ochrona [Ochrona usługi Office 365 w usłudze Defender](set-up-safe-links-policies.md) była włączona, organizacja musi mieć [zdefiniowane zasady linków Sejf i zasady załączników Sejf](set-up-safe-attachments-policies.md). Zobacz również [ochronę przed spamem](anti-spam-protection.md) i [złośliwym oprogramowaniem](anti-malware-protection.md).

## <a name="related-topics"></a>Tematy pokrewne

[Inteligentne raporty i szczegółowe informacje w portalu Microsoft 365 Defender](reports-and-insights-in-security-and-compliance.md)

[Azure AD role wbudowane](/azure/active-directory/roles/permissions-reference)
