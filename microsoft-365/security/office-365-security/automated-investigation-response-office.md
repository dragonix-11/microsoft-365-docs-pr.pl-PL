---
title: Jak działa zautomatyzowane badanie i reagowanie w Ochrona usługi Office 365 w usłudze Microsoft Defender
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
keywords: zautomatyzowane reagowanie na zdarzenia, badanie, korygowanie, ochrona przed zagrożeniami
ms.date: 01/29/2021
description: Zobacz, jak działają funkcje zautomatyzowanego badania i reagowania w Ochrona usługi Office 365 w usłudze Microsoft Defender
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 78dc31c055f563f0f9f03bcf12642296459de491
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974240"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Jak działa zautomatyzowane badanie i reagowanie w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W miarę wyzwalania alertów zabezpieczeń zespół ds. operacji zabezpieczeń musi przeanalizować te alerty i podjąć kroki w celu ochrony organizacji. Czasami zespoły ds. operacji zabezpieczeń mogą czuć się przeciążone przez liczbę wyzwalanych alertów. Funkcje zautomatyzowanego badania i reagowania (AIR) w Ochrona usługi Office 365 w usłudze Microsoft Defender mogą pomóc.

Funkcja AIR umożliwia zespołowi ds. operacji zabezpieczeń wydajniejsze i wydajniejsze działanie. Możliwości air obejmują zautomatyzowane procesy badania w odpowiedzi na znane zagrożenia, które istnieją obecnie. Odpowiednie akcje korygowania oczekują na zatwierdzenie, umożliwiając zespołowi ds. operacji zabezpieczeń reagowanie na wykryte zagrożenia.

W tym artykule opisano sposób działania funkcji AIR w kilku przykładach. Gdy wszystko będzie gotowe do rozpoczęcia korzystania z funkcji AIR, zobacz [Automatyczne badanie zagrożeń i reagowanie na nie](office-365-air.md).

- [Przykład 1: Komunikat phish zgłoszony przez użytkownika uruchamia podręcznik badania](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Przykład 2. Administrator zabezpieczeń wyzwala badanie z poziomu Eksploratora zagrożeń](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Przykład 3: Zespół ds. operacji zabezpieczeń integruje środowisko AIR ze swoim rozwiązaniem SIEM przy użyciu interfejsu API działania zarządzania Office 365](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Przykład: komunikat phish zgłoszony przez użytkownika uruchamia podręcznik badania

Załóżmy, że użytkownik w organizacji otrzymuje wiadomość e-mail, która jego zdaniem jest próbą wyłudzania informacji. Użytkownik wytrenowany do zgłaszania takich komunikatów używa [dodatku Komunikat raportu](enable-the-report-message-add-in.md) lub [dodatku Report Phishing,](enable-the-report-phish-add-in.md) aby wysłać go do firmy Microsoft w celu analizy. Przesyłanie jest również wysyłane do systemu i jest widoczne w Eksploratorze w widoku **Przesłane** (wcześniej nazywanym widokiem **zgłaszanym przez użytkownika** ). Ponadto komunikat zgłoszony przez użytkownika wyzwala teraz alert informacyjny oparty na systemie, który automatycznie uruchamia podręcznik badania.

W fazie badania głównego są oceniane różne aspekty wiadomości e-mail. Te aspekty obejmują:

- Określenie, jakiego rodzaju zagrożenie może być;
- KtoTo go wysłali;
- Skąd wysłano wiadomość e-mail (wysyłanie infrastruktury);
- Czy inne wystąpienia wiadomości e-mail zostały dostarczone lub zablokowane;
- Ocena od naszych analityków;
- Czy wiadomość e-mail jest skojarzona ze znanymi kampaniami;
- i nie tylko.

Po zakończeniu badania głównego podręcznik zawiera listę zalecanych akcji do wykonania dla oryginalnej wiadomości e-mail i skojarzonych z nim jednostek.

Następnie jest wykonywanych kilka kroków badania zagrożeń i wyszukiwania zagrożeń:

- Podobne wiadomości e-mail są identyfikowane za pośrednictwem wyszukiwania klastra poczty e-mail.
- Sygnał jest udostępniany innym platformom, takim jak [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Ustala się, czy użytkownicy klikną złośliwe linki w podejrzanych wiadomościach e-mail.
- Sprawdzanie odbywa się w różnych Exchange Online Protection ([EOP](exchange-online-protection-overview.md) i ([Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md), aby sprawdzić, czy istnieją inne podobne komunikaty zgłaszane przez użytkowników.
- Sprawdzanie jest wykonywane w celu sprawdzenia, czy użytkownik został naruszony. Ta kontrola wykorzystuje sygnały w Office 365, [Microsoft Defender for Cloud Apps](/cloud-app-security) i [Azure Active Directory](/azure/active-directory), korelując wszelkie anomalie związane z działaniami użytkowników.

W fazie polowania zagrożenia i zagrożenia są przypisywane do różnych kroków wyszukiwania zagrożeń.

Korygowanie to ostatnia faza podręcznika. W tej fazie są podejmowane kroki korygowania w oparciu o fazy badania i wyszukiwania zagrożeń.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Przykład: administrator zabezpieczeń wyzwala badanie z Eksploratora zagrożeń

Oprócz zautomatyzowanych badań wyzwalanych przez alert zespół ds. operacji zabezpieczeń organizacji może wyzwolić automatyczne badanie z widoku w [Eksploratorze zagrożeń](threat-explorer.md). To badanie również tworzy alert, dzięki czemu Microsoft 365 Defender zdarzenia i zewnętrzne narzędzia SIEM mogą zobaczyć, że to badanie zostało wyzwolone.

Załóżmy na przykład, że używasz widoku **Złośliwe oprogramowanie** w Eksploratorze. Korzystając z kart poniżej wykresu, wybierz kartę **Poczta e-mail** . Jeśli wybierzesz co najmniej jeden element na liście, zostanie aktywowany przycisk **+ Akcje** .

:::image type="content" source="../../media/Explorer-Malware-Email-ActionsInvestigate.png" alt-text="Eksplorator z wybranymi komunikatami" lightbox="../../media/Explorer-Malware-Email-ActionsInvestigate.png":::

Za pomocą menu **Akcje** możesz wybrać pozycję **Wyzwól badanie**.

:::image type="content" source="../../media/explorer-malwareview-selectedemails-actions.jpg" alt-text="Menu Akcje dla wybranych komunikatów" lightbox="../../media/explorer-malwareview-selectedemails-actions.jpg":::

Podobnie jak w przypadku podręczników wyzwalanych przez alert, automatyczne badania, które są wyzwalane z widoku w Eksploratorze, obejmują główne badanie, kroki identyfikowania i korelowania zagrożeń oraz zalecane działania w celu wyeliminowania tych zagrożeń.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Przykład: zespół ds. operacji zabezpieczeń integruje środowisko AIR ze swoim rozwiązaniem SIEM przy użyciu interfejsu API działania zarządzania Office 365

Funkcje air w Ochrona usługi Office 365 w usłudze Microsoft Defender obejmują [raporty & szczegółów](air-view-investigation-results.md), których zespoły ds. operacji zabezpieczeń mogą używać do monitorowania zagrożeń i reagowania na nie. Można jednak również zintegrować funkcje AIR z innymi rozwiązaniami. Przykłady obejmują system zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM), system zarządzania przypadkami lub niestandardowe rozwiązanie do raportowania. Tego rodzaju integracje można przeprowadzić przy użyciu [interfejsu API działania zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

Na przykład niedawno organizacja skonfigurowała dla swojego zespołu ds. operacji zabezpieczeń sposób wyświetlania alertów phish zgłaszanych przez użytkowników, które zostały już przetworzone przez air. Ich rozwiązanie integruje odpowiednie alerty z serwerem SIEM organizacji i systemem zarządzania przypadkami. Rozwiązanie znacznie zmniejsza liczbę wyników fałszywie dodatnich, dzięki czemu zespół ds. operacji zabezpieczeń może skoncentrować swój czas i nakład pracy na rzeczywistych zagrożeniach. Aby dowiedzieć się więcej o tym rozwiązaniu niestandardowym, zobacz [blog Tech Community: Improve the Effectiveness of your SOC with Ochrona usługi Office 365 w usłudze Microsoft Defender and the O365 Management API (Ulepszanie skuteczności soc za pomocą Ochrona usługi Office 365 w usłudze Microsoft Defender i interfejsu API zarządzania O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185)).

## <a name="next-steps"></a>Następne kroki

- [Wprowadzenie przy użyciu funkcji AIR](office-365-air.md)
- [Wyświetlanie oczekujących lub ukończonych akcji korygowania](air-review-approve-pending-completed-actions.md)
