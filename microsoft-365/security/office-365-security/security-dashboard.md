---
title: Omówienie pulpitu nawigacyjnego zabezpieczeń
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: fe0b9b8f-faa9-44ff-8095-4d1b2f507b74
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Za pomocą nowego pulpitu nawigacyjnego zabezpieczeń możesz sprawdzać Office 365 stan ochrony przed zagrożeniami oraz wyświetlać alerty zabezpieczeń i działać na ich podstawie.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4bc9d813732c4c67531aeb47a673111d62bbf417
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475746"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>Pulpit nawigacyjny zabezpieczeń w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="basic-functions-and-how-to-open-security-dashboard"></a>Podstawowe funkcje i otwieranie pulpitu nawigacyjnego zabezpieczeń

Centrum zabezpieczeń & umożliwia <https://protection.office.com> Twojej organizacji zarządzanie ochroną i zgodnością danych. Przy założeniu, że masz niezbędne uprawnienia, pulpit nawigacyjny zabezpieczeń umożliwia ci przeglądanie stanu ochrony przed zagrożeniami, a także wyświetlanie alertów zabezpieczeń i działanie z nimi.

Obejrzyj klip wideo, aby zapoznać się z omówieniem, a następnie przeczytaj ten artykuł, aby dowiedzieć się więcej.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

W zależności od tego, co obejmuje subskrypcja twojej organizacji, pulpit nawigacyjny zabezpieczeń zawiera kilka widżetów, takich jak podsumowanie zarządzania zagrożeniami, stan ochrony przed zagrożeniami, cotygodniowe wykrywanie zagrożeń na całym świecie, złośliwe oprogramowanie itp., zgodnie z opisem w poniższych sekcjach.

Aby wyświetlić pulpit nawigacyjny zabezpieczeń w Centrum zabezpieczeń & zgodności, przejdź do strony **Pulpit nawigacyjny zarządzania zagrożeniami**\>. Aby przejść bezpośrednio do pulpitu nawigacyjnego zabezpieczeń, użyj .<https://protection.office.com/searchandinvestigation/dashboard>

> [!NOTE]
> Aby wyświetlić pulpit nawigacyjny zabezpieczeń, musisz być administratorem globalnym, administratorem zabezpieczeń lub czytelnikiem zabezpieczeń. Niektóre widżety wymagają dodatkowych uprawnień do wyświetlania. Aby dowiedzieć się więcej, zobacz [Uprawnienia w Centrum zabezpieczeń & zgodności](permissions-in-the-security-and-compliance-center.md)[.

## <a name="threat-management-summary"></a>Podsumowanie zarządzania zagrożeniami

Widżet Podsumowanie zagrożeń zarządzania pozwala od razu sprawdzić, jak Twoja organizacja była chroniona przed zagrożeniami w ciągu ostatnich siedmiu (7) dni.

:::image type="content" source="../../media/SecDash-ThreatMgmtSummary.png" alt-text="Widżet Pulpit nawigacyjny zabezpieczeń — podsumowanie zarządzania zagrożeniami" lightbox="../../media/SecDash-ThreatMgmtSummary.png":::

Informacje zawarte w podsumowaniu zarządzania zagrożeniami zależą od tego, co obejmuje Twoja subskrypcja. W poniższej tabeli opisano, jakie informacje są Office 365 E3 i Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|Wiadomości z złośliwym oprogramowaniem zablokowane<br>Wiadomości wyłudzdzce informacje zablokowane<br>Wiadomości zgłoszone przez użytkowników<br><br><br><br>|Wiadomości z złośliwym oprogramowaniem zablokowane<br>Wiadomości wyłudzdzce informacje zablokowane<br>Wiadomości zgłoszone przez użytkowników<br>Zero-day malware blocked<br>Wykryto zaawansowane wiadomości wyłudzdzące informacje<br>Zablokowane złośliwe adresy URL|

Aby wyświetlić widżet Podsumowanie zagrożeń zarządzania zagrożeniami lub uzyskać do niego dostęp, musisz mieć uprawnienia do wyświetlania Ochrona usługi Office 365 w usłudze Defender raportów. Aby dowiedzieć się więcej, zobacz [Jakie uprawnienia są potrzebne do wyświetlania raportów Ochrona usługi Office 365 w usłudze Defender?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

## <a name="threat-protection-status"></a>Stan ochrony przed zagrożeniami

Widżet Stan ochrony przed zagrożeniami umożliwia wyświetlanie skuteczności ochrony przed zagrożeniami przy użyciu popularnego i szczegółowego widoku wyłudzy informacji i złośliwego oprogramowania.

:::image type="content" source="../../media/tpswidget.png" alt-text="Widżet stanu ochrony przed zagrożeniami" lightbox="../../media/tpswidget.png":::

Szczegóły zależą od tego, czy Microsoft 365 obejmuje subskrypcję usługi [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) z usługą lub bez [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md).

|Jeśli Subskrypcja obejmuje...|Zobaczysz te szczegóły|
|---|---|
|EOP, ale nie Ochrona usługi Office 365 w usłudze Microsoft Defender|Złośliwe wiadomości e-mail wykryte i zablokowane przez usługę EOP.<p> Zobacz [Raport o stanie ochrony przed zagrożeniami (EOP).](view-email-security-reports.md#threat-protection-status-report)|
|Ochrona usługi Office 365 w usłudze Microsoft Defender|Złośliwa zawartość oraz złośliwa wiadomość e-mail wykrywana i blokowana przez usługę EOP i Ochrona usługi Office 365 w usłudze Defender <p> Zagregowana liczba unikatowych wiadomości [e-mail](zero-hour-auto-purge.md) ze złośliwą zawartością zablokowaną przez aparat ochrony przed złośliwym oprogramowaniem, funkcjami automatycznego przeczyszczania o zerowej godzinie i usługami Ochrona usługi Office 365 w usłudze Defender (w tym linki programu [Sejf](safe-links.md)[,](safe-attachments.md) załączniki Sejf i ochrona przed wyłudzaniem informacji w [ Ochrona usługi Office 365 w usłudze Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). <p> Zobacz [Raport o stanie ochrony przed zagrożeniami](view-reports-for-mdo.md#threat-protection-status-report).|

Aby wyświetlić widżet Stanu ochrony przed zagrożeniami lub uzyskać do niego dostęp, musisz mieć uprawnienia do Ochrona usługi Office 365 w usłudze Defender raportów. Aby dowiedzieć się więcej, zobacz [Jakie uprawnienia są wymagane do wyświetlania Ochrona usługi Office 365 w usłudze Defender raportów?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>Cotygodniowe wykrywanie zagrożeń na całym świecie

Widżet Globalne cotygodniowe wykrywanie zagrożeń wskazuje, ile zagrożeń zostało wykrytych w wiadomościach e-mail w ciągu ostatnich siedmiu (7) dni.

:::image type="content" source="../../media/globalweeklythreatdetections.png" alt-text="Widżet Globalne cotygodniowe wykrywanie zagrożeń" lightbox="../../media/globalweeklythreatdetections.png":::

Metryki są obliczane zgodnie z opisem w poniższej tabeli:

|Metryczny|Sposób obliczania|
|---|---|
|Wiadomości zeskanowane|Liczba zeskanowanych wiadomości e-mail pomnożona przez liczbę adresatów|
|Zagrożenia zatrzymały się|Liczba wiadomości e-mail zidentyfikowanych jako zawierające złośliwe oprogramowanie pomnożona przez liczbę adresatów|
|Zablokowane przez [Ochrona usługi Office 365 w usłudze Defender](defender-for-office-365.md)|Liczba wiadomości e-mail zablokowanych przez Ochrona usługi Office 365 w usłudze Defender pomnożona przez liczbę adresatów|
|Usunięto po dostarczeniu|Liczba wiadomości usuniętych przez [automatyczne przeczyszczanie zerowe (ZAP)](zero-hour-auto-purge.md) pomnożona przez liczbę adresatów|

## <a name="malware"></a>Złośliwe oprogramowanie

Widżety złośliwego oprogramowania pokazują szczegółowe informacje na temat trendów złośliwego oprogramowania i typów rodzinnych złośliwego oprogramowania w ciągu ostatnich siedmiu (7) dni.

:::image type="content" source="../../media/malwarewidgetatpe5.png" alt-text="Trendy złośliwego oprogramowania i typy rodzinne" lightbox="../../media/malwarewidgetatpe5.png":::

## <a name="insights"></a>Szczegółowe informacje

Szczegółowe informacje główne problemy, które należy przejrzeć, zawierają również zalecenia i działania do rozważenia.

:::image type="content" source="../../media/smartinsights.png" alt-text="Szczegółowe informacje" lightbox="../../media/smartinsights.png":::

Na przykład może się okazać, że wiadomości e-mail wyłudzają informacje, ponieważ niektórzy użytkownicy wyłączyli opcje wiadomości-śmieci. Aby dowiedzieć się więcej na temat sposobu działania szczegółowych informacji, zobacz Raporty i [szczegółowe informacje w Centrum & zabezpieczeń i zgodności](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>Badanie zagrożeń i odpowiedź

Jeśli subskrypcja Twojej organizacji obejmuje plan [Ochrona usługi Office 365 w usłudze Microsoft Defender 2](office-365-ti.md), pulpit nawigacyjny zabezpieczeń zawiera sekcję, która zawiera zaawansowane narzędzia do analizy zagrożeń i reagowania. Te narzędzia obejmują [funkcje automatycznego badania i reakcji](automated-investigation-response-office.md). Zautomatyzowane badanie i odpowiedź mogą być przydatne w scenariuszach, takich jak szybkie [rozwiązanie problemu naruszonych kont użytkowników](address-compromised-users-quickly.md).

Aby dowiedzieć się więcej, [zobacz Wprowadzenie automatyczne badanie i odpowiedź (AIR) w programie Office 365](office-365-air.md).

## <a name="trends"></a>Trendy

U dołu pulpitu nawigacyjnego zabezpieczeń znajduje się sekcja **Trendy** , która zawiera podsumowanie trendów przepływu poczty e-mail w organizacji. Raporty zawierają informacje na temat wiadomości e-mail sklasyfikowanych jako spam, złośliwe oprogramowanie, próby wyłudzenia informacji i dobre wiadomości e-mail. Kliknij kafelek, aby wyświetlić bardziej szczegółowe informacje w raporcie.

:::image type="content" source="../../media/trends.png" alt-text="Sekcja Trendy, która zawiera podsumowanie trendów przepływu poczty e-mail w organizacji" lightbox="../../media/trends.png":::

Jeśli subskrypcja twojej organizacji obejmuje plan [Ochrona usługi Office 365 w usłudze Defender Plan 2](office-365-ti.md), w tej sekcji będzie również miał raport Ostatnie alerty dotyczące zarządzania  zagrożeniami, który umożliwia zespołowi zabezpieczeń wyświetlanie alertów zabezpieczeń o wysokim priorytecie i działanie w związku z nimi.

Aby wyświetlić widżet Wysłane i odebrane wiadomości e-mail lub uzyskać do niego dostęp, musisz mieć uprawnienia do Ochrona usługi Office 365 w usłudze Defender raportów. Aby dowiedzieć się więcej, zobacz [Jakie uprawnienia są potrzebne do wyświetlania raportów Ochrona usługi Office 365 w usłudze Defender?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

Aby wyświetlić widżet Ostatnie alerty zarządzania zagrożeniami lub uzyskać do niego dostęp, musisz mieć uprawnienia do wyświetlania alertów. Aby dowiedzieć się więcej, zobacz [Uprawnienia RBAC wymagane do wyświetlania alertów](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>Artykuły pokrewne

[Wyświetlanie raportów zabezpieczeń poczty e-mail w Centrum & zgodności](view-email-security-reports.md)

[Wyświetlanie raportów dla Ochrona usługi Office 365 w usłudze Microsoft Defender](view-reports-for-mdo.md)

[Ochrona usługi Office 365 w usłudze Defender](defender-for-office-365.md)

[Office 365 i reagowanie na zagrożenia](office-365-ti.md)
