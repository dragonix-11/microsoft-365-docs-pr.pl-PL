---
title: Przeglądanie akcji korygowania w Microsoft 365 Business Premium
description: Zobacz, jak wyświetlać korygowania, które zostały wykonane automatycznie lub oczekują na zatwierdzenie w Centrum akcji.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 73790afedc78961562b592d1eb4decd4a8f1b0d4
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490404"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>Przeglądanie akcji korygowania w Microsoft 365 Business Premium

W porządku, wykryto naruszenie zabezpieczeń, ale co robisz? To zależy od jego natury.

Przykłady akcji korygowania obejmują wysyłanie pliku do kwarantanny, zatrzymywanie procesu przed uruchomieniem lub całkowite usunięcie zaplanowanego zadania. Wszystkie akcje korygowania są śledzone w centrum akcji, które znajduje się pod adresem [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="Zrzut ekranu centrum akcji w języku M365.":::

**W tym artykule opisano**:

- [Jak używać centrum akcji](#how-to-use-your-action-center)

- [Typy akcji korygowania](#types-of-remediation-actions)


## <a name="how-to-use-your-action-center"></a>Jak używać centrum akcji

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Centrum akcji**.

3. Wybierz kartę **Oczekujące** , aby wyświetlić i zatwierdzić (lub odrzucić) wszystkie oczekujące akcje. Takie akcje mogą wynikać z ochrony antywirusowej/ochrony przed złośliwym kodem, zautomatyzowanych badań, działań ręcznego reagowania lub sesji odpowiedzi na żywo.

4. Wybierz kartę **Historia** , aby wyświetlić listę ukończonych akcji.

## <a name="types-of-remediation-actions"></a>Typy akcji korygowania

Twoja subskrypcja obejmuje kilka różnych typów akcji korygowania wykrytych zagrożeń. Te akcje obejmują ręczne akcje reagowania, akcje po zautomatyzowanym badaniu i akcje odpowiedzi na żywo.

W poniższej tabeli wymieniono dostępne akcje korygowania:

| Źródło  | Działania  |
|---------|---------|
| [Zautomatyzowane badania](../security/defender-endpoint/automated-investigations.md)      | — Kwarantanna pliku <br/>— Usuwanie klucza rejestru <br/>- Zabij proces <br/>— Zatrzymywanie usługi <br/>— Wyłączanie sterownika <br/>— Usuwanie zaplanowanego zadania        |
| [Ręczne akcje odpowiedzi](../security/defender-endpoint/respond-machine-alerts.md)   | — Uruchamianie skanowania antywirusowego <br/>- Izolowanie urządzenia <br/>— Zatrzymywanie i kwarantanna <br/>- Dodaj wskaźnik, aby zablokować lub zezwolić na plik       |
| [Odpowiedź na żywo](../security/defender-endpoint/live-response.md)   | - Zbieranie danych kryminalistycznych <br/>- Analizowanie pliku <br/>— Uruchamianie skryptu <br/>— Wysyłanie podejrzanej jednostki do firmy Microsoft w celu analizy <br/>— Korygowanie pliku <br/>- Proaktywne wyszukiwanie zagrożeń         |
