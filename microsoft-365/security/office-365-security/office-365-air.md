---
title: Zautomatyzowane badanie i reagowanie w Ochrona usługi Office 365 w usłudze Microsoft Defender
keywords: AIR, autoIR, Ochrona punktu końcowego w usłudze Microsoft Defender, zautomatyzowany, badania, odpowiedzi, działania naprawcze, zagrożenia, zaawansowane, zagrożenia, ochrona
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 01/29/2021
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Wprowadzenie automatyczne badanie i reagowanie w programie Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e9cd2388d3551ccc0c180d20a92ec0c513472797
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473678"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Zautomatyzowane badania i odpowiedzi (AIR) w programie Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) zaawansowane funkcje automatycznego badania i reakcji (AIR), które mogą zaoszczędzić czas i nakład pracy zespołowej związanej z zabezpieczeniami. W przypadku wyzwalania alertów to zespół operacyjny zabezpieczeń może je przeglądać, priorytetyzować i odpowiadać na nie. Śledzenie liczby alertów przychodzących może być przytłaczające. Automatyzowanie niektórych z tych zadań może być pomocne.

Funkcja AIR umożliwia Twojemu zespołowi ds. bezpieczeństwa wydajniejsze i skuteczniejsze działanie. Funkcje AIR obejmują zautomatyzowane procesy badania w reakcji na znane obecnie zagrożenia. Odpowiednie działania naprawcze oczekują zatwierdzenia, umożliwiając Twoje zespołowi ds. bezpieczeństwa skuteczne reagowanie na wykryte zagrożenia. Dzięki air Twój zespół operacyjny ds. zabezpieczeń może skoncentrować się na zadaniach o wyższym priorytecie bez utraty wzroku ważnych alertów, które są wyzwalane.

W tym artykule opisano:

- Ogólny [przepływ air;](#the-overall-flow-of-air)
- [Jak uzyskać air](#how-to-get-air); i
- Wymagane [uprawnienia do konfigurowania](#required-permissions-to-use-air-capabilities) i używania funkcji AIR.
- Zmiany, które zostaną wkrótce wprowadzone w Twoim Microsoft 365 Defender sieci Microsoft 365 Defender

Ten artykuł zawiera również [kolejne kroki](#next-steps) i zasoby, aby dowiedzieć się więcej.

## <a name="the-overall-flow-of-air"></a>Całkowity przepływ air

Zostanie wyzwolony alert i podręcznik zabezpieczeń uruchomi automatyczne badanie, którego skutkiem będą ustalenia i zalecane działania. Oto ogólny przepływ pracy z programem AIR, krok po kroku:

1. Zautomatyzowane badanie jest inicjowane przy użyciu jednej z następujących metod:
   - W [wiadomości e-mail jest wyzwolony](#which-alert-policies-trigger-automated-investigations) alert wywołany przez coś podejrzanego (na przykład wiadomość, załącznik, adres URL lub naruszone konto użytkownika). Zdarzenie zostanie utworzone i rozpocznie się zautomatyzowane badanie. lub
   - Analityk zabezpieczeń rozpoczyna [zautomatyzowane badanie przy](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) użyciu [Eksploratora](threat-explorer.md).
2. Gdy jest uruchamiane zautomatyzowane badanie, gromadzi ono dane dotyczące danych wiadomości e-mail oraz jednostek powiązanych z pocztą e-mail. Takimi jednostkami mogą być pliki, adresy URL i adresaci. Zakres badania może zwiększyć się w przypadku uruchomienia nowych i powiązanych alertów.
3. Podczas automatycznego badania i po jego zakończeniu dostępne są szczegóły i wyniki. [](air-view-investigation-results.md) Wyniki obejmują [zalecane działania](air-remediation-actions.md) , które można podjąć, aby zareagować i rozwiązać wszelkie znalezione zagrożenia.
4. Zespół operacyjny ds. zabezpieczeń przegląda [wyniki badania i](air-view-investigation-results.md) zalecenia, [a następnie zatwierdza lub](air-review-approve-pending-completed-actions.md) odrzuca działania naprawcze.
5. Ponieważ oczekujące działania naprawcze zostaną zatwierdzone (lub odrzucone), zautomatyzowane badanie zostaje zakończone.

W Ochrona usługi Office 365 w usłudze Microsoft Defender działania naprawcze nie są podejmowane automatycznie. Działania naprawcze są podejmowane tylko po zatwierdzeniu ich przez zespół zabezpieczeń Twojej organizacji. Funkcje AIR oszczędzają czas pracy zespołu związanego z zabezpieczeniami, identyfikując działania naprawcze i podając szczegółowe informacje potrzebne do podejmowania przejętej decyzji.

W trakcie każdego zautomatyzowanego badania i po jego zakończeniu twój zespół operacyjny zabezpieczeń może:

- [Wyświetlanie szczegółów alertu związanego z badaniem](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Wyświetlanie szczegółów wyników badania](air-view-investigation-results.md#view-details-of-an-investigation)
- [Przeglądanie i zatwierdzanie akcji na skutek badania](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Aby uzyskać bardziej szczegółowe omówienie, zobacz [Jak działa program AIR](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>Jak uzyskać air

Funkcje AIR są zawarte w [programie Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) pod warunkiem skonfigurowania zasad i alertów. Potrzebujesz pomocy? Postępuj zgodnie z [wskazówkami w tece](protect-against-threats.md) Ochrona przed zagrożeniami, aby skonfigurować następujące ustawienia ochrony:

- [Rejestrowanie inspekcji](../../compliance/turn-audit-log-search-on-or-off.md) (powinna być włączona)
- [Ochrona przed złośliwym oprogramowaniem](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Ochrona przed wyłudzaniem informacji](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Ochrona przed spamem](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Sejf i załączniki Sejf wiadomości](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

Ponadto należy zapoznać się z zasadami [alertów](../../compliance/alert-policies.md) organizacji, zwłaszcza domyślnymi [w kategorii Zarządzanie zagrożeniami](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>Które zasady alertów powodują automatyczne badanie?

Microsoft 365 zawiera wiele wbudowanych zasad alertów, które ułatwiają identyfikowanie nadużyć Exchange uprawnień administratora, działań złośliwego oprogramowania, potencjalnych zagrożeń zewnętrznych i wewnętrznych oraz zagrożeń związanych z zarządzaniem informacjami. Niektóre z [domyślnych zasad alertów mogą](../../compliance/alert-policies.md#default-alert-policies) wyzwalać automatyczne badania. W poniższej tabeli opisano alerty wyzwalaujące zautomatyzowane badania, ich ważność w portalu Microsoft 365 Defender oraz sposób ich generowania:

|Alert|Ważność|Sposób wygenerowania alertu|
|---|---|---|
|Wykryto potencjalnie złośliwe kliknięcie adresu URL|**High (Wysoki)**|Ten alert jest generowany, gdy wystąpi którakolwiek z następujących sytuacji: <ul><li>Użytkownik chroniony za pomocą [linków Sejf w](safe-links.md) organizacji klika złośliwy link</li><li>Zmiany w werdyktach adresów URL są identyfikowane przez Ochrona usługi Office 365 w usłudze Microsoft Defender</li><li>Użytkownicy zastępują Sejf z łączami ostrzegawczymi (w zależności od zasad Sejf [linków sieciowych w organizacji](set-up-safe-links-policies.md)).</li></ul> <p> Aby uzyskać więcej informacji na temat zdarzeń, które powodują wyzwolenie tego alertu, zobacz [Konfigurowanie Sejf linków](set-up-safe-links-policies.md).|
|Wiadomość e-mail jest zgłaszana przez użytkownika jako złośliwe oprogramowanie lub wyłudzy|**Informacyjne**|Ten alert jest generowany, gdy użytkownicy w organizacji zgłaszają wiadomości jako wiadomości wyłudzdzce informacje przy użyciu dodatku Report [Message](enable-the-report-message-add-in.md) (Wiadomość raportu) lub [dodatku Wyłudzanie informacji (Report Phishing).](enable-the-report-phish-add-in.md)|
|Wiadomości e-mail zawierające złośliwe oprogramowanie są usuwane po dostarczeniu|**Informacyjne**|Ten alert jest generowany, gdy wszystkie wiadomości e-mail zawierające złośliwe oprogramowanie są dostarczane do skrzynek pocztowych w organizacji. Jeśli to zdarzenie wystąpi, firma Microsoft usunie zainfekowane wiadomości z Exchange Online pocztowych za pomocą automatycznego przeczyszczania [bez godzin (ZAP](zero-hour-auto-purge.md)).|
|Wiadomości e-mail zawierające adresy URL wyłudów są usuwane po dostarczeniu|**Informacyjne**|Ten alert jest generowany, gdy wszystkie wiadomości zawierające frazę phish są dostarczane do skrzynek pocztowych w organizacji. W przypadku wystąpienia tego zdarzenia firma Microsoft usunie zainfekowane wiadomości z Exchange Online pocztowych [za pomocą zap](zero-hour-auto-purge.md).|
|Wykrywane są podejrzane wzorce wysyłania wiadomości e-mail|**Średni**|Ten alert jest generowany, gdy ktoś z Twojej organizacji wysłał podejrzaną wiadomość e-mail i istnieje ryzyko ograniczenia możliwości wysyłania wiadomości e-mail. Alert jest wczesnym ostrzeżeniem o zachowaniu, które może wskazywać, że konto zostało naruszone, ale nie jest wystarczająco poważne, aby ograniczyć użytkownika. <p> Chociaż zdarza się to rzadko, alert wygenerowany przez te zasady może być anomaly. Warto jednak sprawdzić, czy konto użytkownika [nie zostało naruszone](responding-to-a-compromised-email-account.md).|
|Użytkownikowi ograniczono możliwości wysyłania wiadomości e-mail|**High (Wysoki)**|Ten alert jest generowany, gdy ktoś z Twojej organizacji ma ograniczenie dostępu do wysyłania poczty wychodzącej. Ten alert zwykle powoduje, że [konto e-mail zostało naruszone](responding-to-a-compromised-email-account.md). <p> Aby uzyskać więcej informacji o użytkownikach z ograniczeniami, zobacz Usuwanie zablokowanych użytkowników z [portalu Użytkownicy z ograniczeniami w programie Microsoft 365](removing-user-from-restricted-users-portal-after-spam.md).|

> [!TIP]
> Aby dowiedzieć się więcej o zasadach alertów lub edytować ustawienia domyślne, zobacz [Zasady alertów w Centrum zgodności platformy Microsoft 365](../../compliance/alert-policies.md).

## <a name="required-permissions-to-use-air-capabilities"></a>Wymagane uprawnienia do używania funkcji AIR

Uprawnienia są udzielane za pośrednictwem określonych ról, takich jak te opisane w poniższej tabeli:

|Zadanie|Role wymagane|
|---|---|
|Konfigurowanie funkcji AIR|Jedna z następujących ról: <ul><li>Administrator globalny</li><li>Administrator zabezpieczeń</li></ul> <p> Te role można przypisywać [w Azure Active Directory lub](/azure/active-directory/roles/permissions-reference) w portalu [Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).|
|Rozpoczynanie automatycznego badania <p> --- lub --- <p> Zatwierdzanie lub odrzucanie zalecanych akcji|Jedna z następujących ról przypisywanych w [programie Azure Active Directory](/azure/active-directory/roles/permissions-reference) lub w portalu [Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md): <ul><li>Administrator globalny</li><li>Administrator zabezpieczeń</li><li>Operator zabezpieczeń</li><li>Czytnik zabezpieczeń <br> --- i --- </li><li>Wyszukiwanie i przeczyszczanie (ta rola jest przypisana tylko w portalu [Microsoft 365 Defender sieci.](permissions-microsoft-365-security-center.md) Może być konieczne utworzenie nowej grupy ról **współpracy &** e-mail i dodanie roli Wyszukaj i Przeczyść do tej nowej grupy ról.</li></ul>|

## <a name="required-licenses"></a>Wymagane licencje

[Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) powinny być przypisane do:

- Administratorzy zabezpieczeń (w tym administratorzy globalni)
- Zespół operacyjny Twojej organizacji ds. zabezpieczeń (w tym czytelnicy zabezpieczeń i osoby pełniące rolę **Wyszukiwania i przeczyszczania** )
- Użytkownicy końcowi

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>Zmiany w portalu Microsoft 365 Defender zostaną wkrótce wprowadzone

Jeśli korzystasz już z funkcji AIR w programie Ochrona usługi Office 365 w usłudze Microsoft Defender, za jakiś czas zobaczysz pewne zmiany w ulepszonym portalu Microsoft 365 Defender [air](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Ujednolicone Centrum akcji" lightbox="../../media/m3d-action-center-unified.png":::

Nowy i ulepszony Microsoft 365 Defender łączy <https://security.microsoft.com> funkcje AIR w programach [Ochrona usługi Office 365 w usłudze Microsoft Defender i in](defender-for-office-365.md) [ Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/automated-investigations.md). Dzięki tym aktualizacjom i ulepszeniom Twój zespół operacyjny ds. zabezpieczeń będzie mógł wyświetlać szczegółowe informacje o zautomatyzowanych badaniach i działaniach naprawczych w ramach poczty e-mail, zawartości współpracy, kont użytkowników i urządzeń w jednym miejscu.

> [!TIP]
> Nowy portal Microsoft 365 Defender zastępuje następujące centra administracyjne:
>
> - Centrum & zgodności (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> Poza zmianą adresu URL pojawił się nowy wygląd i sposób działania, zaprojektowany tak, aby zapewnić Twojemu zespołowi zabezpieczeń usprawnione środowisko z widocznością większej liczby wykrycia zagrożeń w jednym miejscu.

### <a name="what-to-expect"></a>Czego można się spodziewać

W poniższej tabeli wymieniono zmiany i ulepszenia wprowadzone w programie AIR w programie Ochrona usługi Office 365 w usłudze Microsoft Defender.

|Element|Co się zmienia?|
|---|---|
|**Strona Badania**|Zaktualizowana **strona Badania** jest spójna z tym, co widzisz w [Ochrona punktu końcowego w usłudze Microsoft Defender.](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) Zobaczysz kilka ogólnych zmian formatowania i stylu, które są zgodne z nowym, **ujednoliconym widokiem Badania** . Na przykład wykres badania ma bardziej ujednolicony format.|
|**Karta** Użytkownicy|Karta **Użytkownicy** jest teraz **kartą Skrzynki** pocztowe. Szczegółowe informacje o użytkownikach znajdują się na karcie **Skrzynka** pocztowa.|
|**Karta Poczta e-mail**|**Usunięto** kartę Poczta e-mail. Odwiedź **kartę Jednostki**, aby wyświetlić listę elementów grup poczty e-mail i poczty e-mail.|
|**Karta Jednostki**|Karta **Jednostki** ma styl karty na karcie, który zawiera widok podsumowania oraz możliwość filtrowania według typu encji. Na **karcie Jednostki** **oprócz opcji Otwórz** w Eksploratorze jest teraz dostępna opcja Idź do **wyszukiwania** . Teraz możesz używać [Eksploratora lub](threat-explorer.md) [zaawansowanego](../defender-endpoint/advanced-hunting-overview.md) wyszukiwania, aby znaleźć jednostki i zagrożenia, oraz filtrować według wyników.|
|**Karta** Akcje|Zaktualizowana **karta Akcje** zawiera teraz kartę **Oczekujące** akcje i **kartę Historia** akcji. Akcje można zatwierdzić (lub odrzucić) w okienku bocznym, które jest otwierane po wybraniu akcji oczekującej.|
|**Karta Dowód**|Nowa karta **Dowód** pokazuje kluczowe ustalenia dotyczące encji związane z akcjami. Akcje związane z każdym dowodem można zatwierdzić (lub odrzucić) w okienku bocznym, które jest otwierane po wybraniu akcji oczekującej.|
|**Centrum akcji**|Zaktualizowane Centrum **akcji** (<https://security.microsoft.com/action-center>) łączy oczekujące i ukończone akcje z poczty e-mail, urządzeń i tożsamości. Aby dowiedzieć się więcej, zobacz Centrum akcji. (Aby dowiedzieć się więcej, zobacz [Centrum akcji](../defender/m365d-action-center.md)).|
|**Strona Zdarzenia**|Strona **Zdarzenia jest** teraz skorelowana z wieloma badaniami, aby zapewnić lepszy skonsolidowany widok badań. ([Dowiedz się więcej o zdarzeniach](../defender/incidents-overview.md)).|

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie szczegółów i wyników automatycznego badania](air-view-investigation-results.md#view-details-of-an-investigation)
- [Przeglądanie i zatwierdzanie oczekujących akcji](air-remediation-actions.md)
