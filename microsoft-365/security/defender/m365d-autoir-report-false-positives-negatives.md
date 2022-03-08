---
title: Adres dodatnich lub ujemnych wyników fałszywie dodatnich w Microsoft 365 Defender
description: Czy coś zostało nieodebrane lub błędnie wykrywane przez program AIR w programie Microsoft 365 Defender? Dowiedz się, jak przesłać do firmy Microsoft wyniki fałszywie dodatnie lub ujemne fałszywie ujemne w celu analizy.
keywords: automatyczne, badania, alerty, działania naprawcze, wynik fałszywie dodatni, wynik fałszywie ujemny
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
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 67246d7f7876457e6553818b469987a2b5a59eb0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321797"
---
# <a name="address-false-positives-or-false-negatives-in-microsoft-365-defender"></a>Adres dodatnich lub ujemnych wyników fałszywie dodatnich w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Wyniki fałszywie dodatnie lub ujemne mogą czasami występować w przypadku każdego rozwiązania ochrony przed zagrożeniami. Jeśli [funkcje automatycznego badania i odpowiedzi](m365d-autoir.md) w Microsoft 365 Defender zostały nieodebrane lub błędnie wykryte, Twój zespół operacyjny zabezpieczeń może wykonać następujące czynności:

- [Zgłaszanie wyników fałszywie dodatnich/ujemnych firmie Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis)
- [Dostosowywanie alertów](#adjust-an-alert-to-prevent-false-positives-from-recurring) (w razie potrzeby)
- [Cofanie działań naprawczych, które zostały wykonane na urządzeniach](#undo-a-remediation-action-that-was-taken-on-a-device)

W poniższych sekcjach opisano sposób wykonywania tych zadań.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Zgłaszanie do analizy wyników fałszywie dodatnich/ujemnych dla firmy Microsoft

|Nieodebrany lub błędnie wykryty element |Usługa  |Co należy zrobić  |
|---------|---------|---------|
|— Wiadomość e-mail <br/>— Załącznik wiadomości e-mail <br/>— Adres URL w wiadomości e-mail<br/>— Adres URL w Office pliku      |[Usługa Microsoft Defender dla Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)        |[Przesyłanie podejrzeń o spam, wyłudzy, adresy URL i pliki do firmy Microsoft w celu skanowania](../office-365-security/admin-submission.md)         |
|Plik lub aplikacja na urządzeniu    |[Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection)         |[Przesyłanie pliku do firmy Microsoft w celu analizy złośliwego oprogramowania](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Dopasowywanie alertu, aby zapobiec cyklicznym wynikom fałszywie dodatnim

|Scenariusz |Usługa |Co należy zrobić |
|--------|--------|--------|
|— Alert jest wyzwalany w sposób zgodny z prawem <br/>- Alert jest niedokładny    |[Usługa Microsoft Defender dla aplikacji w chmurze](/cloud-app-security)<br/> lub <br/>[Ochrona przed zagrożeniami w usłudze Azure](/azure/security/fundamentals/threat-detection)         |[Zarządzanie alertami w portalu usługi Defender for Cloud Apps](/cloud-app-security/managing-alerts)         |
|Plik, adres IP, adres URL lub domena są traktowane jak złośliwe oprogramowanie na urządzeniu, mimo że jest bezpieczne|[Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection) |[Tworzenie wskaźnika niestandardowego z akcją "Zezwalaj"](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |

## <a name="undo-a-remediation-action-that-was-taken-on-a-device"></a>Cofanie akcji rozwiązywania problemów wykonanej na urządzeniu

Jeśli w encji (takiej jak urządzenie lub wiadomość e-mail) została podjęta akcja zaradczych, a podmiot, którego dotyczy problem, w rzeczywistości nie jest zagrożeniem, twój zespół operacyjny zabezpieczeń może cofnąć działanie naprawcze w Centrum [akcji.](m365d-action-center.md)

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> zaloguj się. 
2. W okienku nawigacji wybierz pozycję **Centrum akcji**. 
3. Na **karcie Historia** wybierz akcję, którą chcesz cofnąć. Zostanie otwarte okienko wysuwu.
4. W wysuwanych okienkach wybierz pozycję **Cofnij**.

> [!TIP]
> Zobacz [Cofanie zakończonych akcji](m365d-autoir-actions.md#undo-completed-actions).

## <a name="see-also"></a>Zobacz też

- [Wyświetlanie szczegółów i wyników automatycznego badania](m365d-autoir-results.md)
- [Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania w Microsoft 365 Defender](advanced-hunting-overview.md)
