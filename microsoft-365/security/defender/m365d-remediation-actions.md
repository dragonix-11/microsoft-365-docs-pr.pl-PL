---
title: Akcje korygowania w Microsoft 365 Defender
description: Zapoznaj się z omówieniem akcji korygowania, które są wykonywane po zautomatyzowanych badaniach w Microsoft 365 Defender
keywords: zautomatyzowane, badanie, alert, wyzwalacz, akcja, korygowanie
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
ms.openlocfilehash: 5605678a1fcc30719d7f838a16452ba527c554b7
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847054"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Akcje korygowania w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Podczas i po zautomatyzowanym badaniu w Microsoft 365 Defender są identyfikowane akcje korygowania dla złośliwych lub podejrzanych elementów. Niektóre rodzaje akcji korygowania są podejmowane na urządzeniach, nazywanych również punktami końcowymi. Inne akcje korygowania są podejmowane w przypadku tożsamości, kont i zawartości poczty e-mail. Zautomatyzowane badania są wykonywane po wykonaniu akcji korygowania, zatwierdzeniu lub odrzuceniu.

> [!IMPORTANT]
> To, czy akcje korygowania są wykonywane automatycznie, czy tylko po zatwierdzeniu, zależy od pewnych ustawień, takich jak poziomy automatyzacji. Aby dowiedzieć się więcej, zobacz następujące artykuły:
>
> - [Konfigurowanie możliwości zautomatyzowanego badania i reagowania w Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [Konfigurowanie kont akcji w Microsoft Defender for Identity](/defender-for-identity/manage-action-accounts)
> - [Sposób korygowanie zagrożeń na urządzeniach](../defender-endpoint/automated-investigations.md)
> - [Zagrożenia i akcje korygowania dotyczące zawartości współpracy & poczty e-mail](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

Poniższa tabela zawiera podsumowanie akcji korygowania, które są obecnie obsługiwane w Microsoft 365 Defender.

|Akcje korygowania urządzenia (punktu końcowego)  |Akcje korygowania poczty e-mail  |Użytkownicy (konta)  |
|:---------|:---------|----------|
|— Zbieranie pakietu badania <br/>- Izolowanie urządzenia (tę akcję można cofnąć)<br/>- Maszyna odłączona <br/>— Wykonywanie kodu wydania <br/>— Zwolnienie z kwarantanny <br/>— Przykład żądania <br/>— Ograniczanie wykonywania kodu (tę akcję można cofnąć) <br/>— Uruchamianie skanowania antywirusowego <br/>— Zatrzymywanie i kwarantanna      |- Blokuj adres URL (czas kliknięcia)<br/>- Usuwanie nietrwałe wiadomości e-mail lub klastrów<br/>— Wiadomość e-mail o kwarantannie<br/>— Kwarantanna załącznika wiadomości e-mail<br/>- Wyłącz przekazywanie poczty zewnętrznej          |— Wyłączanie użytkownika<br />- Resetowanie hasła użytkownika<br />— Potwierdź, że użytkownik został naruszona          |

Akcje korygowania, oczekujące na zatwierdzenie lub już zakończone, można wyświetlić w [Centrum akcji](m365d-action-center.md).

## <a name="remediation-actions-that-follow-automated-investigations"></a>Akcje korygowania, które są wykonywane po zautomatyzowanych badaniach

Po zakończeniu zautomatyzowanego dochodzenia zostaje osiągnięty werdykt dla każdego dowodu. W zależności od werdyktu są identyfikowane akcje korygowania. W niektórych przypadkach akcje korygowania są wykonywane automatycznie; w innych przypadkach akcje korygowania oczekują na zatwierdzenie. Wszystko zależy od tego, jak [jest skonfigurowane zautomatyzowane badanie i reagowanie](m365d-configure-auto-investigation-response.md).

Poniższa tabela zawiera listę możliwych werdyktów i wyników:

| Werdykt    | Jednostki, których dotyczy problem    | Wyniki|
|------|------|------|
| Złośliwy    | Urządzenia (punkty końcowe)    | Akcje korygowania są wykonywane automatycznie (przy założeniu, że [grupy urządzeń](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) w organizacji są ustawione na **Pełne — automatycznie koryguj zagrożenia**)|
| Zagrożone | Użytkownicy | Akcje korygowania są wykonywane automatycznie |
| Złośliwy    | Zawartość wiadomości e-mail (adresy URL lub załączniki) | Zalecane akcje korygowania oczekują na zatwierdzenie|
| Podejrzanych    | Zawartość urządzeń lub wiadomości e-mail | Zalecane akcje korygowania oczekują na zatwierdzenie|
| Nie znaleziono zagrożeń    | Zawartość urządzeń lub wiadomości e-mail    | Nie są wymagane żadne akcje korygowania|

## <a name="remediation-actions-that-are-taken-manually"></a>Akcje korygowania, które są podejmowane ręcznie

Oprócz akcji korygowania, które są wykonywane po zautomatyzowanych badaniach, zespół ds. operacji zabezpieczeń może ręcznie wykonać pewne akcje korygowania. Są to następujące funkcje:

- Ręczne działanie urządzenia, takie jak izolacja urządzenia lub kwarantanna pliku
- Ręczne działanie poczty e-mail, takie jak usuwanie nietrwałe wiadomości e-mail
- Ręczne działanie użytkownika, takie jak wyłączenie użytkownika lub zresetowanie hasła użytkownika
- [Zaawansowana akcja wyszukiwania zagrożeń](../defender-endpoint/advanced-hunting-overview.md) na urządzeniach, użytkownikach lub w wiadomościach e-mail
- [Akcja Eksploratora](../office-365-security/threat-explorer.md) dotycząca zawartości poczty e-mail, taka jak przenoszenie wiadomości e-mail do wiadomości-śmieci, usuwanie nietrwałe wiadomości e-mail lub usuwanie wiadomości e-mail
- Ręczna akcja [odpowiedzi na żywo](/windows/security/threat-protection/microsoft-defender-atp/live-response) , taka jak usuwanie pliku, zatrzymywanie procesu i usuwanie zaplanowanego zadania
- Akcja odpowiedzi na żywo za pomocą [interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis), takich jak izolowanie urządzenia, uruchamianie skanowania antywirusowego i uzyskiwanie informacji o pliku

## <a name="next-steps"></a>Następne kroki

- [Odwiedź centrum akcji](m365d-action-center.md)
- [Wyświetlanie działań naprawczych i zarządzanie nimi](m365d-autoir-actions.md)
- [Adres fałszywie dodatnie lub fałszywie ujemne](m365d-autoir-report-false-positives-negatives.md)
