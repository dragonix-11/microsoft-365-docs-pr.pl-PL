---
title: Jak działa automatyczne badanie i reagowanie w Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
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
keywords: automatyczna reakcja na incydenty, badania, działania naprawcze i ochrona przed zagrożeniami
ms.date: 01/29/2021
description: Zobacz, jak działają automatyczne funkcje badania i reagowania w Ochrona usługi Office 365 w usłudze Microsoft Defender
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 41ba3bcf31725cd5a9fb8b25bc22b6c8bb591363
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569296"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Jak działa automatyczne badanie i reagowanie w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W związku z wyzwoleniem alertów zabezpieczeń zespół operacyjny zabezpieczeń musi przyjrzeć się tym alertom i podjąć odpowiednie kroki w celu ochrony organizacji. Czasami zespoły ds. operacji zabezpieczeń mogą mieć poczucie zalewu liczby alertów, które są wyzwalane. Funkcje automatycznego badania i odpowiedzi (AIR) w programach Ochrona usługi Office 365 w usłudze Microsoft Defender mogą pomóc.

Funkcja AIR umożliwia Twojemu zespołowi ds. bezpieczeństwa wydajniejsze i skuteczniejsze działanie. Funkcje AIR obejmują zautomatyzowane procesy badania w reakcji na znane obecnie zagrożenia. Na zatwierdzenie oczekują odpowiednie działania naprawcze, co umożliwia zespołowi ds. bezpieczeństwa reagowanie na wykryte zagrożenia.

W tym artykule opisano sposób działania air w kilku przykładach. Gdy wszystko będzie gotowe do korzystania z funkcji AIR, zobacz [Automatyczne badanie zagrożeń i reagowanie na nie](office-365-air.md).

- [Przykład 1. Wiadomość wyłudniana przez użytkownika uruchamia podręcznik badania](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Przykład 2. Administrator zabezpieczeń wyzwala badanie z Eksploratora zagrożeń](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Przykład 3. Zespół operacyjny ds. zabezpieczeń integruje program AIR ze swoim interfejsem SIEM przy użyciu interfejsu API działań zarządzania Office 365 zarządzania](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Przykład: Wiadomość wyłud treści ze zgłoszonym przez użytkownika błędem uruchamia podręcznik badania

Załóżmy, że użytkownik w Twojej organizacji otrzymuje wiadomość e-mail, która według tego użytkownika jest próbą wyłudzenia informacji. Użytkownik przeszkolony w zakresie zgłaszania takich wiadomości używa dodatku Report [Message](enable-the-report-message-add-in.md) (Wiadomość raportu) lub dodatku do wyłudzania informacji ( [Report Phishing](enable-the-report-phish-add-in.md) ) w celu wysłania go do firmy Microsoft w celu analizy. Przesyłanie jest również wysyłane do systemu i jest widoczne w Eksploratorze w widoku Przesłane  materiały (dawniej nazywanym widokiem **zgłoszonym** przez użytkownika). Ponadto zgłoszony przez użytkownika komunikat powoduje teraz wyzwolenie alertu informacyjnego opartego na systemie, który powoduje automatyczne uruchamianie podręcznika badania.

W fazie badania głównego oceniane są różne aspekty wiadomości e-mail. Są to między innymi następujące aspekty:

- Określenie, jakiego typu zagrożenia może to być;
- KtoTo wysłano wiadomość;
- Miejsce wysłania wiadomości e-mail (infrastruktura wysyłania);
- czy inne wystąpienia wiadomości e-mail zostały dostarczone, czy zablokowane;
- Ocena naszych analityków;
- czy wiadomość e-mail jest skojarzona z jakąkolwiek znaną kampanią;
- i nie tylko.

Po zakończeniu głównego badania podręcznik zawiera listę zalecanych działań do podjęcia w pierwotnego przypadku wiadomości e-mail i jednostek, które są z nim skojarzone.

Następnie wykonano kilka etapów badań zagrożeń i łętw:

- Podobne wiadomości e-mail są identyfikowane za pośrednictwem wyszukiwania grup poczty e-mail.
- Sygnał jest udostępniany innym platformom, takim [jak Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Określa się, czy użytkownicy kliknął złośliwe linki w podejrzanych wiadomościach e-mail.
- Sprawdzanie odbywa się w Exchange Online Protection ([EOP](exchange-online-protection-overview.md) i ([Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md), aby sprawdzić, czy istnieją inne podobne wiadomości zgłoszone przez użytkowników.
- Wykonywana jest kontrola w celu sprawdzenia, czy użytkownik został naruszony. Ten sprawdzanie wykorzystuje sygnały na Office 365, [Microsoft Defender for Cloud Apps](/cloud-app-security) i [Azure Active Directory,](/azure/active-directory) korelując wszelkie pokrewne anomalie aktywności użytkownika.

W fazie łęgowania do różnych etapów łęgów przypisywane są czynniki ryzyka i zagrożenia.

Działania naprawcze to końcowa faza podręcznika. W tym etapie są podejmowane kroki rozwiązywania problemów na podstawie faz badania i pracy.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Przykład: Administrator zabezpieczeń wyzwala badanie z Eksploratora zagrożeń

Poza zautomatyzowanymi badaniami wyzwolanych przez alert zespół operacji zabezpieczeń Twojej organizacji może wyzwolić automatyczne badanie z widoku w [Eksploratorze zagrożeń](threat-explorer.md). To badanie także tworzy alert, dzięki czemu Microsoft 365 Defender zdarzenia i zewnętrzne narzędzia SIEM mogą zobaczyć, że to badanie zostało wyzwolone.

Załóżmy na przykład, że używasz widoku Złośliwe **oprogramowanie** w Eksploratorze. Korzystając z kart poniżej wykresu, wybierz kartę Poczta **e-mail** . Jeśli wybierzesz co najmniej jeden element na liście, zostanie uaktywniony przycisk **+** Akcje.

:::image type="content" source="../../media/Explorer-Malware-Email-ActionsInvestigate.png" alt-text="Eksplorator z zaznaczonymi wiadomościami" lightbox="../../media/Explorer-Malware-Email-ActionsInvestigate.png":::


W menu **Akcje** możesz wybrać pozycję **Wyzwolić badanie**.

:::image type="content" source="../../media/explorer-malwareview-selectedemails-actions.jpg" alt-text="Menu Akcje dla wybranych wiadomości" lightbox="../../media/explorer-malwareview-selectedemails-actions.jpg":::

Podobnie jak podręczniki wyzwalane przez alert, automatyczne badania wyzwalane z widoku w Eksploratorze obejmują badanie główne, kroki w celu zidentyfikowania zagrożeń i skorelowania ich oraz zalecane działania w celu ograniczenia tych zagrożeń.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Przykład: Zespół operacyjny ds. zabezpieczeń integruje program AIR ze swoim interfejsem SIEM przy użyciu interfejsu API działań zarządzania Office 365 zarządzania

Funkcje AIR w programie Ochrona usługi Office 365 w usłudze Microsoft Defender obejmują [raporty & szczegóły](air-view-investigation-results.md), których zespoły operacyjne bezpieczeństwa mogą używać do monitorowania zagrożeń i adresem ich. Można też zintegrować funkcje funkcji AIR z innymi rozwiązaniami. Przykłady obejmują system zarządzania informacjami zabezpieczającymi i zdarzeniami, system zarządzania zdarzeniami lub niestandardowe rozwiązanie do raportowania. Tego rodzaju integracje można wykonać przy użyciu interfejsu [API działań Office 365 zarządzania](/office/office-365-management-api/office-365-management-activity-api-reference).

Na przykład ostatnio zespół operacyjny ds. zabezpieczeń schował dla organizacji sposób wyświetlania zgłoszonych przez użytkowników alertów wyłudniczych, które zostały już przetworzone przez air. Ich rozwiązanie integruje odpowiednie alerty z serwerem SIEM organizacji i ich systemem zarządzania projektami. Rozwiązanie znacznie zmniejsza liczbę wyników fałszywie dodatnich, dzięki czemu zespół operacyjny ds. zabezpieczeń może skoncentrować swój czas i wysiłki na rzeczywistych zagrożeniach. Aby dowiedzieć się więcej o tym niestandardowym rozwiązaniu, zobacz blog Community tech[: Improve the Effectiveness of your SOC with Ochrona usługi Office 365 w usłudze Microsoft Defender and the O365 Management API](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>Następne kroki

- [Wprowadzenie funkcji AIR](office-365-air.md)
- [Wyświetlanie oczekujących lub ukończonych działań naprawczych](air-review-approve-pending-completed-actions.md)
