---
title: Zautomatyzowane badanie i reagowanie w Ochrona usługi Office 365 w usłudze Microsoft Defender
keywords: AIR, autoIR, Ochrona punktu końcowego w usłudze Microsoft Defender, automated, investigation, response, remediation, threats, advanced, threat, protection
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
description: Wprowadzenie przy użyciu funkcji zautomatyzowanego badania i reagowania w Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ca64509321ff43bbe8b7baf7ec7dfa270d9afdc4
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941528"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Zautomatyzowane badanie i reagowanie (AIR) w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) obejmuje zaawansowane funkcje zautomatyzowanego badania i reagowania (AIR), które pozwalają zaoszczędzić czas i nakład pracy zespołu ds. operacji zabezpieczeń. W miarę wyzwalania alertów do zespołu ds. operacji zabezpieczeń należy przeglądanie, określanie priorytetów i reagowanie na te alerty. Nadążanie za ilością alertów przychodzących może być przytłaczające. Automatyzacja niektórych z tych zadań może pomóc.

Funkcja AIR umożliwia zespołowi ds. operacji zabezpieczeń wydajniejsze i wydajniejsze działanie. Możliwości air obejmują zautomatyzowane procesy badania w odpowiedzi na znane zagrożenia, które istnieją obecnie. Odpowiednie akcje korygowania oczekują na zatwierdzenie, umożliwiając zespołowi ds. operacji zabezpieczeń skuteczne reagowanie na wykryte zagrożenia. Dzięki funkcji AIR zespół ds. operacji zabezpieczeń może skoncentrować się na zadaniach o wyższym priorytecie bez utraty z oczu ważnych alertów, które są wyzwalane.

W tym artykule opisano:

- [Ogólny przepływ air](#the-overall-flow-of-air);
- [Jak uzyskać AIR](#how-to-get-air); I
- [Wymagane uprawnienia](#required-permissions-to-use-air-capabilities) do konfigurowania lub używania funkcji AIR.
- Zmiany, które pojawią się wkrótce w portalu Microsoft 365 Defender

Ten artykuł zawiera również [kolejne kroki](#next-steps) i zasoby, aby dowiedzieć się więcej.

## <a name="the-overall-flow-of-air"></a>Ogólny przepływ powietrza

Wyzwalany jest alert, a podręcznik zabezpieczeń uruchamia zautomatyzowane badanie, co skutkuje ustaleniami i zalecanymi akcjami. Oto ogólny przepływ air, krok po kroku:

1. Zautomatyzowane badanie jest inicjowane na jeden z następujących sposobów:
   - [Alert jest wyzwalany przez coś podejrzanego](#which-alert-policies-trigger-automated-investigations) w wiadomości e-mail (na przykład wiadomość, załącznik, adres URL lub naruszone konto użytkownika). Zostanie utworzone zdarzenie i rozpocznie się zautomatyzowane badanie. Lub
   - Analityk zabezpieczeń [uruchamia zautomatyzowane badanie](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) podczas korzystania z [Eksploratora](threat-explorer.md).
2. Podczas automatycznego badania zbiera dane dotyczące danej wiadomości e-mail i jednostek związanych z tą wiadomością e-mail. Takie jednostki mogą zawierać pliki, adresy URL i adresatów. Zakres badania może wzrosnąć w miarę wyzwalania nowych i powiązanych alertów.
3. W trakcie i po zautomatyzowanym badaniu dostępne są [szczegóły i wyniki](air-view-investigation-results.md) do wyświetlenia. Wyniki obejmują [zalecane akcje](air-remediation-actions.md) , które można wykonać w celu reagowania na znalezione zagrożenia i ich korygowania.
4. Twój zespół ds. operacji zabezpieczeń przegląda [wyniki badania i zalecenia](air-view-investigation-results.md) oraz [zatwierdza lub odrzuca akcje korygowania](air-review-approve-pending-completed-actions.md).
5. Ponieważ oczekujące akcje korygowania są zatwierdzane (lub odrzucane), zautomatyzowane badanie zostaje zakończone.

W Ochrona usługi Office 365 w usłudze Microsoft Defender żadne akcje korygowania nie są wykonywane automatycznie. Akcje korygowania są podejmowane tylko po zatwierdzeniu przez zespół ds. zabezpieczeń organizacji. Funkcje AIR oszczędzają czas zespołu operacji zabezpieczeń, identyfikując akcje korygujące i podając szczegóły potrzebne do podjęcia świadomej decyzji.

Podczas i po każdym zautomatyzowanym badaniu zespół ds. operacji zabezpieczeń może wykonywać następujące czynności:

- [Wyświetlanie szczegółów dotyczących alertu związanego z badaniem](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Wyświetlanie szczegółów wyników badania](air-view-investigation-results.md#view-details-of-an-investigation)
- [Przeglądanie i zatwierdzanie akcji w wyniku badania](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Aby uzyskać bardziej szczegółowe omówienie, zobacz [Jak działa system AIR](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>Jak uzyskać air

Funkcje AIR są uwzględniane w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2), pod warunkiem skonfigurowania zasad i alertów. Potrzebujesz pomocy? Postępuj zgodnie ze wskazówkami w [temacie Ochrona przed zagrożeniami](protect-against-threats.md) , aby skonfigurować lub skonfigurować następujące ustawienia ochrony:

- [Rejestrowanie inspekcji](../../compliance/turn-audit-log-search-on-or-off.md) (powinno być włączone)
- [Ochrona przed złośliwym oprogramowaniem](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Ochrona przed wyłudzaniem informacji](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Ochrona przed spamem](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Sejf łącza i załączniki Sejf](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

Ponadto sprawdź [zasady alertów organizacji](../../compliance/alert-policies.md), zwłaszcza [zasady domyślne w kategorii Zarządzanie zagrożeniami](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>Które zasady alertów wyzwalają zautomatyzowane badania?

Microsoft 365 udostępnia wiele wbudowanych zasad alertów, które ułatwiają identyfikowanie zagrożeń związanych z uprawnieniami administratora Exchange, złośliwym oprogramowaniem, potencjalnymi zagrożeniami zewnętrznymi i wewnętrznymi oraz zagrożeniami związanymi z ładem informacyjnym. Niektóre z [domyślnych zasad alertów](../../compliance/alert-policies.md#default-alert-policies) mogą wyzwalać zautomatyzowane badania. W poniższej tabeli opisano alerty, które wyzwalają zautomatyzowane badania, ich ważność w portalu Microsoft 365 Defender i sposób ich generowania:

|Alert|Ważności|Sposób generowania alertu|
|---|---|---|
|Wykryto potencjalnie złośliwe kliknięcie adresu URL|**High (Wysoki)**|Ten alert jest generowany, gdy wystąpi dowolny z następujących elementów: <ul><li>Użytkownik chroniony przez [Sejf Linki](safe-links.md) w organizacji klika złośliwy link</li><li>Zmiany werdyktów dla adresów URL są identyfikowane przez Ochrona usługi Office 365 w usłudze Microsoft Defender</li><li>Użytkownicy zastępują strony ostrzegawcze linków Sejf (na podstawie [zasad linków Sejf](set-up-safe-links-policies.md) organizacji).</li></ul> <p> Aby uzyskać więcej informacji na temat zdarzeń wyzwalających ten alert, zobacz [Konfigurowanie zasad linków Sejf](set-up-safe-links-policies.md).|
|Wiadomość e-mail jest zgłaszana przez użytkownika jako złośliwe oprogramowanie lub phish|**Informacyjne**|Ten alert jest generowany, gdy użytkownicy w organizacji zgłaszają komunikaty jako wiadomość e-mail wyłudzającą informacje przy użyciu [dodatku Komunikat raportu](enable-the-report-message-add-in.md) lub [dodatku Wyłudzanie informacji o raportach](enable-the-report-phish-add-in.md).|
|Wiadomości e-mail zawierające złośliwe oprogramowanie są usuwane po dostarczeniu|**Informacyjne**|Ten alert jest generowany, gdy wszystkie wiadomości e-mail zawierające złośliwe oprogramowanie są dostarczane do skrzynek pocztowych w organizacji. W przypadku wystąpienia tego zdarzenia firma Microsoft usuwa zainfekowane wiadomości z Exchange Online skrzynek pocztowych przy użyciu [automatycznego przeczyszczania o wartości zero godzin (ZAP).](zero-hour-auto-purge.md)|
|Wiadomości e-mail zawierające fałszywe adresy URL są usuwane po dostarczeniu|**Informacyjne**|Ten alert jest generowany, gdy wszystkie wiadomości zawierające phish są dostarczane do skrzynek pocztowych w organizacji. W przypadku wystąpienia tego zdarzenia firma Microsoft usuwa zainfekowane wiadomości z Exchange Online skrzynek pocztowych przy użyciu [zap](zero-hour-auto-purge.md).|
|Wykryto podejrzane wzorce wysyłania wiadomości e-mail|**Średni**|Ten alert jest generowany, gdy ktoś w organizacji wysłał podejrzaną wiadomość e-mail i istnieje ryzyko ograniczenia wysyłania wiadomości e-mail. Alert jest wczesnym ostrzeżeniem dla zachowania, które może wskazywać, że konto zostało naruszone, ale nie jest wystarczająco poważne, aby ograniczyć użytkownika. <p> Chociaż jest to rzadkie, alert wygenerowany przez te zasady może być anomalią. Warto jednak [sprawdzić, czy konto użytkownika zostało naruszone](responding-to-a-compromised-email-account.md).|
|Użytkownik nie może wysyłać wiadomości e-mail|**High (Wysoki)**|Ten alert jest generowany, gdy ktoś w organizacji nie może wysyłać poczty wychodzącej. Ten alert zazwyczaj jest wynikiem [naruszenia zabezpieczeń konta e-mail](responding-to-a-compromised-email-account.md). <p> Aby uzyskać więcej informacji na temat użytkowników z ograniczeniami, zobacz [Usuwanie zablokowanych użytkowników z portalu Użytkownicy z ograniczeniami w Microsoft 365](removing-user-from-restricted-users-portal-after-spam.md).|

> [!TIP]
> Aby dowiedzieć się więcej o zasadach alertów lub edytować ustawienia domyślne, zobacz [Zasady alertów w portalu zgodności usługi Microsoft Purview](../../compliance/alert-policies.md).

## <a name="required-permissions-to-use-air-capabilities"></a>Wymagane uprawnienia do korzystania z funkcji AIR

Uprawnienia są przyznawane za pośrednictwem niektórych ról, takich jak te opisane w poniższej tabeli:

|Zadanie|Wymagane role|
|---|---|
|Konfigurowanie funkcji AIR|Jedna z następujących ról: <ul><li>Administrator globalny</li><li>Administrator zabezpieczeń</li></ul> <p> Te role można przypisać w [Azure Active Directory](/azure/active-directory/roles/permissions-reference) lub w [portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|Rozpocznij automatyczne badanie <p> --- lub --- <p> Zatwierdzanie lub odrzucanie zalecanych akcji|Jedna z następujących ról, przypisana w [Azure Active Directory](/azure/active-directory/roles/permissions-reference) lub w [portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md): <ul><li>Administrator globalny</li><li>Administrator zabezpieczeń</li><li>Operator zabezpieczeń</li><li>Czytelnik zabezpieczeń <br> --- i --- </li><li>Wyszukiwanie i przeczyszczanie (ta rola jest przypisywana tylko w [portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md). Może być konieczne utworzenie nowej grupy ról **współpracy & poczty e-mail** i dodanie roli Wyszukaj i przeczyszczanie do nowej grupy ról.</li></ul>|

## <a name="required-licenses"></a>Wymagane licencje

Ochrona usługi Office 365 w usłudze Microsoft Defender licencje [planu 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) powinny być przypisane do:

- Administratorzy zabezpieczeń (w tym administratorzy globalni)
- Zespół ds. operacji zabezpieczeń w organizacji (w tym czytelnicy zabezpieczeń i osoby z rolą **Wyszukiwania i przeczyszczania** )
- Użytkownicy końcowi

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>Zmiany pojawią się wkrótce w portalu Microsoft 365 Defender

Jeśli korzystasz już z funkcji AIR w Ochrona usługi Office 365 w usłudze Microsoft Defender, zobaczysz pewne zmiany w [ulepszonym portalu Microsoft 365 Defender](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Centrum ujednoliconej akcji" lightbox="../../media/m3d-action-center-unified.png":::

Nowy i ulepszony portal <https://security.microsoft.com> Microsoft 365 Defender łączy możliwości air w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) i w [ Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/automated-investigations.md). Dzięki tym aktualizacjom i ulepszeniom zespół ds. operacji zabezpieczeń będzie mógł wyświetlać szczegółowe informacje o zautomatyzowanych badaniach i akcjach korygowania w ramach poczty e-mail, zawartości współpracy, kont użytkowników i urządzeń w jednym miejscu.

> [!TIP]
> Nowy portal Microsoft 365 Defender zastępuje następujące centra administracyjne:
>
> - Centrum zgodności & zabezpieczeń (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> Oprócz zmiany adresu URL wprowadzono nowy wygląd i działanie, które mają zapewnić zespołowi ds. zabezpieczeń bardziej usprawnione środowisko z widocznością większej liczby wykrywania zagrożeń w jednym miejscu.

### <a name="what-to-expect"></a>Czego się spodziewać

W poniższej tabeli wymieniono zmiany i ulepszenia wprowadzone w środowisku AIR w Ochrona usługi Office 365 w usłudze Microsoft Defender.

|Element|Co się zmienia?|
|---|---|
|Strona **Badania**|Zaktualizowana strona **Badania** jest bardziej spójna z tym, co widać w [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations). Zobaczysz ogólne zmiany formatu i stylu, które są zgodne z nowym, ujednoliconym widokiem **Badania** . Na przykład wykres badania ma bardziej ujednolicony format.|
|Karta **Użytkownicy**|Karta **Użytkownicy** jest teraz kartą **Skrzynki pocztowe** . Szczegóły dotyczące użytkowników są wyświetlane na karcie **Skrzynka pocztowa** .|
|Karta **Poczta e-mail**|Karta **Poczta e-mail** została usunięta. odwiedź kartę **Jednostki** , aby wyświetlić listę elementów klastra poczty e-mail i poczty e-mail.|
|Karta **Jednostki**|Karta **Jednostki** ma styl tabulacji na karcie, który zawiera widok podsumowania i możliwość filtrowania według typu jednostki. Karta **Jednostki** zawiera teraz opcję **wyszukiwania w** języku Go oprócz opcji **Otwórz w Eksploratorze** . Teraz możesz użyć [Eksploratora](threat-explorer.md) lub [zaawansowanego wyszukiwania zagrożeń](../defender-endpoint/advanced-hunting-overview.md) w celu znajdowania jednostek i zagrożeń oraz filtrowania wyników.|
|**Karta Akcje**|Zaktualizowana karta **Akcje** zawiera teraz kartę **Oczekujące akcje** i kartę **Historia akcji** . Akcje można zatwierdzać (lub odrzucać) w okienku bocznym otwieranym po wybraniu oczekującej akcji.|
|Karta **Dowody**|Nowa karta **Evidence (Dowody)** zawiera wyniki kluczowych jednostek związane z akcjami. Akcje związane z poszczególnymi dowodami można zatwierdzić (lub odrzucić) w okienku bocznym otwieranym po wybraniu oczekującej akcji.|
|**Centrum akcji**|Zaktualizowane **centrum akcji** (<https://security.microsoft.com/action-center>) łączy oczekujące i ukończone akcje na adresach e-mail, urządzeniach i tożsamościach. Aby dowiedzieć się więcej, zobacz Centrum akcji. (Aby dowiedzieć się więcej, zobacz [Centrum akcji](../defender/m365d-action-center.md)).|
|Strona **Zdarzenia**|Strona **Zdarzenia** skoreluje teraz wiele dochodzeń w celu zapewnienia lepszego skonsolidowanego widoku dochodzeń. ([Dowiedz się więcej o zdarzeniach](../defender/incidents-overview.md)).|

## <a name="next-steps"></a>Następne kroki

- [Zobacz szczegóły i wyniki zautomatyzowanego badania](air-view-investigation-results.md#view-details-of-an-investigation)
- [Przeglądanie i zatwierdzanie oczekujących akcji](air-remediation-actions.md)
