---
title: Przejrzyj działania naprawcze w programie Microsoft 365 Business Premium
description: Zobacz, jak wyświetlić działania naprawcze wykonane automatycznie lub oczekujące na zatwierdzenie w Centrum akcji
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 160cef2ec7691fbc9debad809b20461a0d3efe23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705540"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>Przejrzyj działania naprawcze w programie Microsoft 365 Business Premium

W przypadku wykrycia zagrożeń są podejmowane działania naprawcze. W zależności od określonego zagrożenia i konfiguracji ustawień zabezpieczeń działania naprawcze mogą być podejmowane automatycznie lub tylko po zatwierdzeniu. Przykłady działań naprawczych obejmują wysyłanie pliku do kwarantanny, zatrzymywanie procesu i usuwanie zaplanowanego zadania. Wszystkie akcje naprawcze są śledzone w Centrum akcji, które znajduje się w [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="Zrzut ekranu przedstawiający Centrum akcji na ekranie M365.":::

**W tym artykule opisano**:

- [Jak korzystać z Centrum akcji](#how-to-use-your-action-center)

- [Typy działań naprawczych](#types-of-remediation-actions)


## <a name="how-to-use-your-action-center"></a>Jak korzystać z Centrum akcji

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Centrum akcji**.

3. Wybierz **kartę Oczekujące** , aby wyświetlić i zatwierdzić (lub odrzucić) wszystkie oczekujące akcje. Takie działania mogą być związane z ochroną antywirusową/antymalware, automatycznymi badaniami, działaniami ręcznej odpowiedzi lub sesjami odpowiedzi na żywo.

4. Wybierz **kartę** Historia, aby wyświetlić listę ukończonych akcji. 

## <a name="types-of-remediation-actions"></a>Typy działań naprawczych

Subskrypcja zawiera kilka różnych typów działań naprawczych w przypadku wykrytych zagrożeń. Te działania obejmują akcje ręcznej odpowiedzi, akcje po zautomatyzowanym śledztwu i akcje odpowiedzi na żywo.

W poniższej tabeli wymieniono dostępne działania naprawcze:

| Źródło  | Akcje  |
|---------|---------|
| [Zautomatyzowane badania](../security/defender-endpoint/automated-investigations.md)      | - Poddaj plikowi kwarantannę <br/>- Usunięcie klucza rejestru <br/>- Zaśmieć proces <br/>— Zatrzymywanie usługi <br/>- Wyłączanie sterownika <br/>— Usuwanie zaplanowanego zadania        |
| [Ręczne akcje odpowiedzi](../security/defender-endpoint/respond-machine-alerts.md)   | - Uruchom skanowanie antywirusowe <br/>- Wyizoluj urządzenie <br/>— Zatrzymaj i poddaj kwarantannie <br/>— Dodaj wskaźnik, aby zablokować lub zezwolić na plik       |
| [Odpowiedź na żywo](../security/defender-endpoint/live-response.md)   | - Zbieranie danych forensycznych <br/>- Analizowanie pliku <br/>- Uruchamianie skryptu <br/>— Wysłać podejrzaną jednostkę do firmy Microsoft w celu analizy <br/>— Rozwiązywanie problemów z plikiem <br/>— proaktywne poszukiwania zagrożeń         |
