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
description: Użyj nowego pulpitu nawigacyjnego zabezpieczeń, aby przejrzeć Office 365 stan ochrony przed zagrożeniami oraz wyświetlić alerty zabezpieczeń i działać na nich.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: defda5c112cf29cb944b502f442cf0e721a32676
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971743"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>Pulpit nawigacyjny zabezpieczeń w Centrum zgodności & zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="basic-functions-and-how-to-open-security-dashboard"></a>Podstawowe funkcje i sposób otwierania pulpitu nawigacyjnego zabezpieczeń

Usługa Security & Compliance Center w witrynie <https://protection.office.com> umożliwia organizacji zarządzanie ochroną i zgodnością danych. Zakładając, że masz niezbędne uprawnienia, pulpit nawigacyjny zabezpieczeń umożliwia przeglądanie stanu ochrony przed zagrożeniami, a także wyświetlanie alertów zabezpieczeń i działanie na nich.

Obejrzyj film wideo, aby uzyskać przegląd, a następnie przeczytaj ten artykuł, aby dowiedzieć się więcej.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

W zależności od subskrypcji organizacji pulpit nawigacyjny zabezpieczeń zawiera kilka widżetów, takich jak podsumowanie zarządzania zagrożeniami, stan ochrony przed zagrożeniami, globalne cotygodniowe wykrywanie zagrożeń, złośliwe oprogramowanie i inne, zgodnie z opisem w poniższych sekcjach.

Aby wyświetlić pulpit nawigacyjny zabezpieczeń w Centrum zgodności & zabezpieczeń, przejdź do **obszaru Pulpit nawigacyjny** **zarządzania zagrożeniami**\>. Aby przejść bezpośrednio do pulpitu nawigacyjnego Zabezpieczenia, użyj polecenia <https://protection.office.com/searchandinvestigation/dashboard>.

> [!NOTE]
> Aby wyświetlić pulpit nawigacyjny zabezpieczeń, musisz być administratorem globalnym, administratorem zabezpieczeń lub czytelnikiem zabezpieczeń. Niektóre widżety wymagają dodatkowych uprawnień do wyświetlania. Aby dowiedzieć się więcej, zobacz [Uprawnienia w Centrum zgodności & zabezpieczeń](permissions-in-the-security-and-compliance-center.md)[.

## <a name="threat-management-summary"></a>Podsumowanie zarządzania zagrożeniami

Widżet Podsumowanie zarządzania zagrożeniami informuje, jak twoja organizacja była chroniona przed zagrożeniami w ciągu ostatnich siedmiu (7) dni.

:::image type="content" source="../../media/SecDash-ThreatMgmtSummary.png" alt-text="Widżet Pulpit nawigacyjny zabezpieczeń — podsumowanie zarządzania zagrożeniami" lightbox="../../media/SecDash-ThreatMgmtSummary.png":::

Informacje widoczne w podsumowaniu zarządzania zagrożeniami zależą od subskrypcji. W poniższej tabeli opisano informacje dotyczące Office 365 E3 i Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|Zablokowane komunikaty o złośliwym oprogramowaniu<br>Zablokowane wiadomości wyłudzające informacje<br>Komunikaty zgłaszane przez użytkowników<br><br><br><br>|Zablokowane komunikaty o złośliwym oprogramowaniu<br>Zablokowane wiadomości wyłudzające informacje<br>Komunikaty zgłaszane przez użytkowników<br>Zablokowane złośliwe oprogramowanie typu zero-day<br>Wykryto zaawansowane wiadomości wyłudzające informacje<br>Zablokowane złośliwe adresy URL|

Aby wyświetlić widżet Podsumowanie zarządzania zagrożeniami lub uzyskać do nich dostęp, musisz mieć uprawnienia do wyświetlania Ochrona usługi Office 365 w usłudze Defender raportów. Aby dowiedzieć się więcej, zobacz [Jakie uprawnienia są potrzebne do wyświetlania raportów Ochrona usługi Office 365 w usłudze Defender?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

## <a name="threat-protection-status"></a>Stan ochrony przed zagrożeniami

Widżet Stan ochrony przed zagrożeniami pokazuje skuteczność ochrony przed zagrożeniami z popularnym i szczegółowym widokiem języka phish i złośliwego oprogramowania.

:::image type="content" source="../../media/tpswidget.png" alt-text="Widżet stanu ochrony przed zagrożeniami" lightbox="../../media/tpswidget.png":::

Szczegóły zależą od tego, czy subskrypcja Microsoft 365 obejmuje [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) z [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) lub bez niej.

|Jeśli Twoja subskrypcja obejmuje...|Te szczegóły zostaną wyświetlone|
|---|---|
|EOP, ale nie Ochrona usługi Office 365 w usłudze Microsoft Defender|Złośliwa wiadomość e-mail, która została wykryta i zablokowana przez funkcję EOP.<p> Zobacz [Raport o stanie ochrony przed zagrożeniami (EOP).](view-email-security-reports.md#threat-protection-status-report)|
|Ochrona usługi Office 365 w usłudze Microsoft Defender|Złośliwa zawartość i złośliwa wiadomość e-mail wykryte i zablokowane przez EOP i Ochrona usługi Office 365 w usłudze Defender <p> Zagregowana liczba unikatowych wiadomości e-mail ze złośliwą zawartością zablokowaną przez aparat ochrony przed złośliwym oprogramowaniem, automatyczne [przeczyszczanie o wartości zero godzin](zero-hour-auto-purge.md) i funkcje Ochrona usługi Office 365 w usłudze Defender (w tym [linki Sejf](safe-links.md), [załączniki Sejf](safe-attachments.md) i [ochrona przed wyłudzaniem informacji Ochrona usługi Office 365 w usłudze Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). <p> Zobacz [Raport o stanie ochrony przed zagrożeniami](view-reports-for-mdo.md#threat-protection-status-report).|

Aby wyświetlić widżet Stan ochrony przed zagrożeniami lub uzyskać do nich dostęp, musisz mieć uprawnienia do wyświetlania Ochrona usługi Office 365 w usłudze Defender raportów. Aby dowiedzieć się więcej, zobacz [Jakie uprawnienia są potrzebne do wyświetlania raportów Ochrona usługi Office 365 w usłudze Defender?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>Globalne cotygodniowe wykrywanie zagrożeń

Widżet Global Weekly Threat Detections pokazuje, ile zagrożeń wykryto w wiadomościach e-mail w ciągu ostatnich siedmiu (7) dni.

:::image type="content" source="../../media/globalweeklythreatdetections.png" alt-text="Widżet Global Weekly Threat Detections" lightbox="../../media/globalweeklythreatdetections.png":::

Metryki są obliczane zgodnie z opisem w poniższej tabeli:

|Metrycznych|Jak jest obliczana|
|---|---|
|Przeskanowane komunikaty|Liczba skanowanych wiadomości e-mail pomnożona przez liczbę adresatów|
|Zatrzymano zagrożenia|Liczba wiadomości e-mail zidentyfikowanych jako zawierające złośliwe oprogramowanie pomnożone przez liczbę adresatów|
|Zablokowane przez [Ochrona usługi Office 365 w usłudze Defender](defender-for-office-365.md)|Liczba wiadomości e-mail zablokowanych przez Ochrona usługi Office 365 w usłudze Defender pomnożona przez liczbę adresatów|
|Usunięto po dostarczeniu|Liczba komunikatów usuniętych przez [automatyczne przeczyszczanie o zerowej godzinie (ZAP)](zero-hour-auto-purge.md) pomnożone przez liczbę adresatów|

## <a name="malware"></a>Złośliwego oprogramowania

Widżety złośliwego oprogramowania pokazują szczegółowe informacje o trendach złośliwego oprogramowania i typach rodzin złośliwego oprogramowania w ciągu ostatnich siedmiu (7) dni.

:::image type="content" source="../../media/malwarewidgetatpe5.png" alt-text="Trendy i typy rodzin złośliwego oprogramowania" lightbox="../../media/malwarewidgetatpe5.png":::

## <a name="insights"></a>Szczegółowe informacje

Szczegółowe informacje nie tylko kwestie dotyczące kluczowych elementów powierzchni, które należy przejrzeć, obejmują one również zalecenia i akcje, które należy wziąć pod uwagę.

:::image type="content" source="../../media/smartinsights.png" alt-text="Inteligentne szczegółowe informacje" lightbox="../../media/smartinsights.png":::

Na przykład może się okazać, że wiadomości e-mail wyłudzające informacje są dostarczane, ponieważ niektórzy użytkownicy wyłączyli opcje wiadomości-śmieci. Aby dowiedzieć się więcej na temat działania szczegółowych informacji, zobacz [Raporty i szczegółowe informacje w Centrum zgodności & zabezpieczeń](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>Badanie zagrożeń i reagowanie na nie

Jeśli subskrypcja organizacji obejmuje [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](office-365-ti.md), pulpit nawigacyjny zabezpieczeń zawiera sekcję zawierającą zaawansowane narzędzia do badania zagrożeń i reagowania na nie. Te narzędzia obejmują [możliwości zautomatyzowanego badania i reagowania](automated-investigation-response-office.md). Zautomatyzowane badanie i reagowanie może być pomocne w scenariuszach, takich jak [szybkie rozwiązywanie problemów z kontami użytkowników, których zabezpieczenia zostały naruszone](address-compromised-users-quickly.md).

Aby dowiedzieć się więcej, zobacz [Wprowadzenie używanie zautomatyzowanego badania i reagowania (AIR) w Office 365](office-365-air.md).

## <a name="trends"></a>Trendy

W dolnej części pulpitu nawigacyjnego zabezpieczeń znajduje się sekcja **Trendy** , która podsumowuje trendy przepływu poczty e-mail w organizacji. Raporty zawierają informacje o wiadomościach e-mail sklasyfikowanych jako spam, złośliwe oprogramowanie, próby wyłudzania informacji i dobra wiadomość e-mail. Kliknij kafelek, aby wyświetlić bardziej szczegółowe informacje w raporcie.

:::image type="content" source="../../media/trends.png" alt-text="Sekcja Trendy zawierająca podsumowanie trendów przepływu wiadomości e-mail dla organizacji" lightbox="../../media/trends.png":::

Jeśli subskrypcja twojej organizacji obejmuje [Ochrona usługi Office 365 w usłudze Defender plan 2](office-365-ti.md), w tej sekcji zostanie również wyświetlony raport **Ostatnie alerty zarządzania zagrożeniami**, który umożliwia zespołowi ds. zabezpieczeń wyświetlanie alertów zabezpieczeń o wysokim priorytecie i wykonywanie akcji w przypadku alertów zabezpieczeń o wysokim priorytecie.

Aby wyświetlić widżet Wysłane i Odebrane wiadomości e-mail lub uzyskać do nich dostęp, musisz mieć uprawnienia do wyświetlania Ochrona usługi Office 365 w usłudze Defender raportów. Aby dowiedzieć się więcej, zobacz [Jakie uprawnienia są potrzebne do wyświetlania raportów Ochrona usługi Office 365 w usłudze Defender?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

Aby wyświetlić widżet Ostatnie alerty zarządzania zagrożeniami lub uzyskać do nich dostęp, musisz mieć uprawnienia do wyświetlania alertów. Aby dowiedzieć się więcej, zobacz [Uprawnienia RBAC wymagane do wyświetlania alertów](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>Artykuły pokrewne

[Wyświetlanie raportów zabezpieczeń poczty e-mail w Centrum zgodności usługi Security &](view-email-security-reports.md)

[Wyświetlanie raportów dla Ochrona usługi Office 365 w usłudze Microsoft Defender](view-reports-for-mdo.md)

[Ochrona usługi Office 365 w usłudze Defender](defender-for-office-365.md)

[Office 365 Badanie zagrożeń i reagowanie na nie](office-365-ti.md)
