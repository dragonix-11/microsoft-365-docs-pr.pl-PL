---
title: Działania naprawcze w programie Microsoft 365 Defender
description: Przegląd działań naprawczych w wyniku zautomatyzowanych badań prowadzonych w ramach Microsoft 365 Defender
keywords: zautomatyzowane, badania, alert, wyzwalacz, akcja, działania naprawcze
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: c922213a262fdc9c61d6f79d0205e6ead96fd44a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326431"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Działania naprawcze w programie Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

W trakcie zautomatyzowanego badania w związku z Microsoft 365 Defender i po nich zidentyfikowano działania naprawcze dotyczące złośliwych lub podejrzanych elementów. Niektóre rodzaje działań naprawczych są podejmowane na urządzeniach, nazywane również punktami końcowymi. W przypadku zawartości wiadomości e-mail są podejmowane inne działania naprawcze. Po zakończeniu działań naprawczych, zatwierdzenia lub odrzucenia są ukończone zautomatyzowane badania.

> [!IMPORTANT]
> To, czy działania naprawcze mają być podejmowane automatycznie, czy tylko po zatwierdzeniu, zależy od określonych ustawień, na przykład od sposobu automatyzacji. Aby dowiedzieć się więcej, zobacz następujące artykuły:
> - [Konfigurowanie funkcji automatycznego badania i reakcji w programie Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [Jak są naprawiane zagrożenia na urządzeniach](../defender-endpoint/automated-investigations.md)
> - [Zagrożenia i działania naprawcze dotyczące zawartości współpracy & e-mail](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

W poniższej tabeli podsumowano działania naprawcze, które są obecnie obsługiwane w programie Microsoft 365 Defender. 

|Działania naprawcze na urządzeniu (punkcie końcowym)  |Akcje dotyczące rozwiązywania problemów z pocztą e-mail  |
|:---------|:---------|
|- Zbierz pakiet badania <br/>- Wyizoluj urządzenie (tę akcję można cofnąć)<br/>- Urządzenie typu Offboard <br/>- Wykonywanie kodu wydania <br/>- Zwolnienie z kwarantanny <br/>— przykładowy wniosek <br/>- Ograniczanie wykonywania kodu (tę akcję można cofnąć) <br/>- Uruchom skanowanie antywirusowe <br/>— Zatrzymaj i poddaj kwarantannie      |- Blokowanie adresu URL (po kliknięciu)<br/>- Niechyłne usuwanie wiadomości e-mail lub grup<br/>- Poddaj wiadomości e-mail kwarantannie<br/>- Poddaj kwarantannie załącznik wiadomości e-mail<br/>- Wyłączanie przesyłania dalej poczty zewnętrznej          |

Działania naprawcze, zarówno oczekujące na zatwierdzenie, jak i ukończone, można wyświetlić w [Centrum akcji](m365d-action-center.md).

## <a name="remediation-actions-that-follow-automated-investigations"></a>Działania naprawcze, które są prowadzone po zautomatyzowanym śledztwie

Po zakończeniu zautomatyzowanego badania dla wszystkich zgromadzonych dowodów jest wyciągany werdykt. W zależności od werdyktu są identyfikowane akcje naprawcze. W niektórych przypadkach działania naprawcze są podejmowane automatycznie. w innych przypadkach działania naprawcze oczekują na zatwierdzenie. Wszystko zależy od konfiguracji [automatycznego badania i odpowiedzi](m365d-configure-auto-investigation-response.md).

W poniższej tabeli wymieniono możliwe werdykty i wyniki:

| Werdykt    | Jednostki, których dotyczy problem    | Wyniki|
|------|------|------|
| Złośliwy    | Urządzenia (punkty końcowe)    | Działania naprawcze są podejmowane automatycznie (przy założeniu, że w [](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) grupach urządzeń organizacji ustawiono pełne — **korygowanie zagrożeń automatycznie**)|
| Złośliwy    | Zawartość wiadomości e-mail (adresy URL lub załączniki) | Zalecane działania naprawcze oczekują na zatwierdzenie|
| Podejrzane    | Urządzenia lub zawartość poczty e-mail | Zalecane działania naprawcze oczekują na zatwierdzenie|
| Nie znaleziono zagrożeń    | Urządzenia lub zawartość poczty e-mail    | Nie są wymagane żadne działania naprawcze|


## <a name="remediation-actions-that-are-taken-manually"></a>Akcje naprawcze wykonywane ręcznie

Poza działaniami naprawczymi, które są wykonywane w wyniku zautomatyzowanych badań, zespół operacyjny zabezpieczeń może podjąć określone działania naprawcze ręcznie. Są to między innymi następujące elementy:

- Ręczna akcja urządzenia, taka jak izolacji urządzenia lub kwarantanna pliku
- Ręczna akcja wiadomości e-mail, taka jak "miękkie usunięcie" wiadomości e-mail 
- [Zaawansowana akcja](../defender-endpoint/advanced-hunting-overview.md) łętwna na urządzeniach lub w wiadomościach e-mail
- [Akcja Eksploratora](../office-365-security/threat-explorer.md) na temat zawartości wiadomości e-mail, taka jak przenoszenie wiadomości e-mail do wiadomości-śmieci, "miękkie usuwanie" lub trudne usuwanie wiadomości e-mail
- [Ręczna akcja odpowiedzi](/windows/security/threat-protection/microsoft-defender-atp/live-response) na żywo, taka jak usunięcie pliku, zatrzymanie procesu i usunięcie zaplanowanego zadania
- Akcja odpowiedzi na żywo z interfejsami [API programu Microsoft Defender dla](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis) punktu końcowego, na przykład izolowanie urządzenia, uruchamianie skanowania antywirusowego i uzyskiwanie informacji o pliku

## <a name="next-steps"></a>Następne kroki

- [Odwiedź Centrum akcji](m365d-action-center.md)
- [Wyświetlanie działań naprawczych i zarządzanie nimi](m365d-autoir-actions.md)
- [Adresuje wartości fałszywie dodatnie lub ujemne](m365d-autoir-report-false-positives-negatives.md)
