---
title: Działania naprawcze w programie Microsoft Defender dla Office 365
keywords: AIR, autoIR, Microsoft Defender for Endpoint, automated, investigation, response, remediation, threats, advanced, threat, protection
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Dowiedz się więcej o działaniach naprawczych po automatycznym śledztwu w programie Microsoft Defender dla Office 365.
ms.date: 04/30/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c994783506f1ba8bc2807b7261d98303cc72f76b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986637"
---
# <a name="remediation-actions-in-microsoft-defender-for-office-365"></a>Działania naprawcze w programie Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="remediation-actions"></a>Działania naprawcze

Funkcje ochrony przed zagrożeniami w [programie Microsoft Defender Office 365](defender-for-office-365.md) zawierają pewne działania naprawcze. Takie działania naprawcze mogą obejmować:

- Niechybne usuwanie wiadomości e-mail lub grup
- Blokowanie adresu URL (czas kliknięcia)
- Wyłączanie przesyłania dalej poczty zewnętrznej
- Wyłączanie delegowania

W programie Microsoft Defender Office 365 działania naprawcze nie są podejmowane automatycznie. Zamiast tego działania naprawcze są podejmowane tylko po zatwierdzeniu ich przez zespół operacyjny ds. zabezpieczeń Twojej organizacji.

## <a name="threats-and-remediation-actions"></a>Zagrożenia i działania naprawcze

Usługa Microsoft Defender dla Office 365 zawiera działania naprawcze w celu rozwiązania różnych zagrożeń. Automatyczne badania często skutkować co najmniej jedną czynnością zaradczych do przejrzenia i zatwierdzenia. W niektórych przypadkach zautomatyzowane badanie nie powoduje określonego działania naprawczego. Aby dokładniej zbadać i podjąć odpowiednie działania, skorzystaj z wskazówek w poniższej tabeli.

|Kategoria|Zagrożenie/ryzyko|Działania naprawcze|
|:---|:---|:---|
|Poczta e-mail|Złośliwe oprogramowanie|Niechyłne usunięcie wiadomości e-mail/klastrów <p> Jeśli więcej niż kilka wiadomości e-mail w klastrze zawiera złośliwe oprogramowanie, klastr jest uważany za złośliwy.|
|Poczta e-mail|Złośliwy adres URL <br> (Złośliwy adres URL został wykryty przez [link Sejf](safe-links.md)).|Niechyłne usunięcie wiadomości e-mail/klastrów <br> Blokowanie adresu URL (weryfikacja po kliknięciu) <p> Wiadomość e-mail zawierająca złośliwy adres URL jest uznawana za złośliwą.|
|Poczta e-mail|Phish|Niechyłne usunięcie wiadomości e-mail/klastrów <p> Jeśli więcej niż kilka wiadomości e-mail w klastrze zawiera próby wyłudzenia informacji, cały klaster jest uznawany za próbę wyłudzenia informacji.|
|Poczta e-mail|Zamapowany phish <br> (Wiadomości e-mail zostały dostarczone, a [następnie zamapowane](zero-hour-auto-purge.md)).|Niechyłne usunięcie wiadomości e-mail/klastrów <p> Raporty są dostępne do wyświetlania zamapowanych wiadomości. [Sprawdź, czy zap przeniesiono wiadomość, i odpowiedzi na często zadawane pytania](zero-hour-auto-purge.md#how-to-see-if-zap-moved-your-message).|
|Poczta e-mail|Nieodebrane wiadomości e-mail [zgłoszone](enable-the-report-message-add-in.md) przez użytkownika|[Zautomatyzowane badanie wyzwolone przez raport użytkownika](automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook)|
|Poczta e-mail|Anomaly głośności <br> (Ostatnie liczby wiadomości e-mail przekraczają poprzednie 7–10 dni w przypadku pasujących kryteriów).|Automatyczne badanie nie powoduje wytłaniania konkretnej oczekującej akcji. <p>Anomaly głośność nie jest wyraźnym zagrożeniem, ale wskazuje jedynie na większe liczby wiadomości e-mail w ostatnich dniach w porównaniu z ostatnimi 7–10 dniami. <p>Mimo że duża liczba wiadomości e-mail może wskazywać potencjalne problemy, konieczne jest potwierdzenie w zakresie złośliwych werdyktów lub ręcznego przejrzenia wiadomości e-mail/klastrów. Zobacz [Znajdowanie podejrzanych wiadomości e-mail, które zostały dostarczone](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered).|
|Poczta e-mail|Nie znaleziono zagrożeń <br> (System nie znalazł żadnych zagrożeń na podstawie plików, adresów URL ani analizy werdyktów grup poczty e-mail).|Automatyczne badanie nie powoduje wytłaniania konkretnej oczekującej akcji. <p>Zagrożenia odnalezione [i zamapowane](zero-hour-auto-purge.md) po zakończeniu badania nie są odzwierciedlane w wynikach liczbowych badania, ale takie zagrożenia są dostępne w [Eksploratorze zagrożeń](threat-explorer.md).|
|Użytkownik|Użytkownik kliknął złośliwy adres URL <br> (Użytkownik przechodzi do strony, która została później znaleziona jako złośliwa, lub użytkownik ominął [](safe-links.md#warning-pages-from-safe-links) stronę z ostrzeżeniem łącza Sejf, aby przejść do złośliwej strony).|Automatyczne badanie nie powoduje wytłaniania konkretnej oczekującej akcji. <p> Blokowanie adresu URL (czas kliknięcia) <p> Za pomocą Eksploratora zagrożeń [możesz wyświetlać dane dotyczące adresów URL i klikać werdykty](threat-explorer.md#view-phishing-url-and-click-verdict-data). <p> Jeśli Twoja organizacja używa programu [Microsoft Defender for Endpoint](/windows/security/threat-protection/), rozważ [badanie](/microsoft-365/security/defender-endpoint/investigate-user) użytkownika w celu ustalenia, czy jego konto zostało naruszone.|
|Użytkownik|Użytkownik wysyła złośliwe oprogramowanie/wyłudzy|Automatyczne badanie nie powoduje wytłaniania konkretnej oczekującej akcji. <p> Użytkownik może zgłaszać złośliwe oprogramowanie/wyłudzy lub ktoś może [](anti-spoofing-protection.md) w ramach ataku podszyć się pod tego użytkownika. Używaj [Eksploratora zagrożeń do](threat-explorer.md) wyświetlania i obsługi wiadomości e-mail [zawierających złośliwe oprogramowanie](threat-explorer-views.md#email--malware) lub [wiadomości wyłudające informacje](threat-explorer-views.md#email--phish).|
|Użytkownik|Przesyłanie dalej poczty e-mail <br> (Skonfigurowano reguły przesyłania dalej skrzynki pocztowej. chch może być używany do eksseksuacji danych).|Usuwanie reguły przesyłania dalej <p> Skorzystaj [z szczegółowych informacji dotyczących przepływu](mail-flow-insights-v2.md) poczty e-mail, w tym raportu wiadomości automatycznie [określonych, aby](mfi-auto-forwarded-messages-report.md) wyświetlić bardziej szczegółowe informacje o przesyłanych dalej wiadomościach e-mail.|
|Użytkownik|Reguły delegowania poczty e-mail <br> (Konto użytkownika ma ustawione delegowanie).|Usuwanie reguły delegowania <p> Jeśli Twoja organizacja używa programu [Microsoft Defender dla punktu końcowego](/windows/security/threat-protection/), rozważ [badanie](/microsoft-365/security/defender-endpoint/investigate-user) użytkownika, który ma uprawnienia delegowania.|
|Użytkownik|Ex exfiltracja danych <br> (Użytkownik naruszał zasady [DLP](../../compliance/dlp-learn-about-dlp.md) dotyczące poczty e-mail lub udostępniania plików |Automatyczne badanie nie powoduje wytłaniania konkretnej oczekującej akcji. <p> [Wyświetlanie raportów DLP i działanie](../../compliance/view-the-dlp-reports.md).|
|Użytkownik|Nieumiejętne wysyłanie wiadomości e-mail <br> (Użytkownik wysłał ostatnio więcej wiadomości e-mail niż w ciągu poprzednich 7–10 dni).|Automatyczne badanie nie powoduje wytłaniania konkretnej oczekującej akcji. <p> Wysyłanie dużej liczby wiadomości e-mail samo w sobie nie jest złośliwe; Użytkownik mógł właśnie wysłać wiadomość e-mail do dużej grupy adresatów na zdarzenie. Aby go zbadać, [skorzystaj](mail-flow-insights-v2.md) z szczegółowych informacji o przepływie poczty, w tym raportu mapy przepływu poczty e-mail, aby ustalić, co się dzieje i podjąć działania.[](mfi-mail-flow-map-report.md)|

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie szczegółów i wyników automatycznego badania w programie Microsoft Defender dla Office 365](air-view-investigation-results.md)
- [Wyświetlanie oczekujących lub ukończonych działań naprawczych w przypadku zautomatyzowanego badania w programie Microsoft Defender dla Office 365](air-review-approve-pending-completed-actions.md)

## <a name="related-articles"></a>Artykuły pokrewne

- [Dowiedz się więcej o automatycznym śledztwie w programie Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
- [Informacje o możliwościach w aplikacji Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)
