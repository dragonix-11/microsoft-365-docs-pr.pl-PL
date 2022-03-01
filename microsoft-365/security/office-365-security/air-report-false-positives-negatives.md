---
title: Jak raportować wyniki fałszywie dodatnie lub ujemne po zautomatyzowanym śledztwie w programie Microsoft Defender Office 365
description: Czy coś zostało nieodebrane lub niewłaściwie wykryte przez program AIR w programie Microsoft Defender dla systemu Office 365? Dowiedz się, jak przesłać do firmy Microsoft wyniki fałszywie dodatnie lub ujemne fałszywie ujemne w celu analizy.
keywords: zautomatyzowane, badania, alert, wyzwalacz, akcja, działania naprawcze, wynik fałszywie dodatni, wynik fałszywie ujemny
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
ms.prod: m365-security
ms.date: 01/29/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: how-to
ms.custom:
- autoir
ms.technology: mdo
ms.openlocfilehash: aaf3e052e29893f0584edd730cf80bd82c34257e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021222"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Jak raportować wyniki fałszywie dodatnie/ujemne w funkcji automatycznego badania i odpowiedzi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jeśli [funkcje automatycznego badania i odpowiedzi (AIR)](automated-investigation-response-office.md) w zakresie Office 365 zostały nieodebrane lub błędnie wykryte, zespół operacyjny zabezpieczeń może podjąć odpowiednie kroki w celu jego rozwiązania. Są to między innymi:

- [raportowanie wyników fałszywie dodatnich/ujemnych firmie Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);
- [Dostosowywanie alertów](#adjust-an-alert-to-prevent-false-positives-from-recurring) (w razie potrzeby) i
- [Cofanie działań naprawczych, które zostały wykonane](#undo-a-remediation-action).

Skorzystaj z tego artykułu jako przewodnika.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Zgłaszanie do analizy wyników fałszywie dodatnich/ujemnych dla firmy Microsoft

Jeśli program AIR w programie Microsoft Defender dla programu Office 365 nie przesłał wiadomości e-mail, załącznika wiadomości e-mail, adresu URL w wiadomości e-mail lub adresu URL w pliku Office, możesz przesłać podejrzaną wiadomość-chcianą, frazę wyłudową, adresy URL i pliki do firmy Microsoft w celu Office 365 [skanowania](admin-submission.md).

Możesz również [przesłać plik do firmy Microsoft na analizę złośliwego oprogramowania](https://www.microsoft.com/wdsi/filesubmission).

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Dopasowywanie alertu, aby zapobiec cyklicznym wynikom fałszywie dodatnim

Jeśli alert zostanie wyzwolony przez wiarygodne użycie lub jest nieprawidłowy, możesz zarządzać alertami w portalu [aplikacji usługi Defender dla chmury](/cloud-app-security/managing-alerts).

Jeśli Twoja organizacja oprócz programu Office 365 korzysta z programu [Microsoft Defender for Endpoint](/windows/security/threat-protection), a plik, adres IP, adres URL lub domena są traktowane jak złośliwe oprogramowanie na urządzeniu, mimo że jest bezpieczne, możesz utworzyć wskaźnik niestandardowy z akcją "Zezwalaj[" dla Twojego urządzenia](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators).

## <a name="undo-a-remediation-action"></a>Cofanie akcji rozwiązywania problemów

Jeśli w większości przypadków akcję zaradczych została podjęta w związku z wiadomością e-mail, załącznikiem wiadomości e-mail lub adresem URL, a element w rzeczywistości nie jest zagrożeniem, zespół operacji zabezpieczeń może cofnąć działanie naprawcze i podjąć kroki, aby zapobiec cykliczności wyników fałszywie dodatnich. Aby cofnąć [akcję](#undo-an-action-using-threat-explorer), możesz użyć Eksploratora zagrożeń lub karty Akcje dla badania.[](#undo-an-action-in-the-action-center)

> [!IMPORTANT]
> Przed podjęciem poniższych zadań upewnij się, że masz odpowiednie uprawnienia.

### <a name="undo-an-action-using-threat-explorer"></a>Cofanie akcji przy użyciu Eksploratora zagrożeń

Za pomocą Eksploratora zagrożeń zespół operacyjny zabezpieczeń może znaleźć wiadomość e-mail, na które wpływa akcja, i potencjalnie cofnąć akcję.

<br>

****

|Scenariusz|Opcje cofania|Dowiedz się więcej|
|---|---|---|
|Wiadomość e-mail została rozsyłana do folderu wiadomości-śmieci użytkownika|<ul><li>Przenoszenie wiadomości do folderu Elementy usunięte użytkownika</li><li>Przenoszenie wiadomości do skrzynki odbiorczej użytkownika</li><li>Usuwanie wiadomości</li></ul>|[Znajdowanie i badanie złośliwych wiadomości e-mail dostarczonych w Office 365](investigate-malicious-email-that-was-delivered.md)|
|Wiadomość e-mail lub plik został poddany kwarantannie|<ul><li>Zwolnij wiadomość e-mail lub plik</li><li> Usuwanie wiadomości e-mail lub pliku</li></ul>|[Zarządzanie wiadomościami poddanymi kwarantannie jako administrator](manage-quarantined-messages-and-files.md)|
|

### <a name="undo-an-action-in-the-action-center"></a>Cofanie akcji w Centrum akcji

W Centrum akcji można wyświetlić akcje naprawcze, które zostały wykonane, i potencjalnie cofnąć akcję.

1. W Microsoft 365 Defender akcji w witrynie <https://security.microsoft.com>, przejdź do Centrum akcji, wybierając **pozycję Centrum akcji**. Aby przejść bezpośrednio do Centrum akcji, użyj .<https://security.microsoft.com/action-center/>
2. W Centrum akcji wybierz **kartę Historia** , aby wyświetlić listę ukończonych akcji.
3. Zaznaczanie elementu. Zostanie otwarte okienko wysuwu.
4. W wysuwanych okienkach wybierz pozycję **Cofnij**. (Tylko akcje, które można cofnąć, będą mieć **przycisk Cofnij** ).

## <a name="see-also"></a>Zobacz też

- [Usługa Microsoft Defender dla Office 365](defender-for-office-365.md)
- [Zautomatyzowane badania w programie Microsoft Defender dla Office 365](office-365-air.md)
