---
title: Przeglądanie działań naprawczych w programie Microsoft Defender dla firm
description: Wyświetlanie działań naprawczych, które zostały wykonane automatycznie lub które oczekują na zatwierdzenie w Centrum akcji
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 5a0fed3ebdb3c7b7275425c24288efab293d6a6d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322957"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Przeglądanie działań naprawczych w Centrum akcji

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W przypadku wykrycia zagrożeń są podejmowane działania naprawcze. W zależności od określonego zagrożenia i konfiguracji ustawień zabezpieczeń działania naprawcze mogą być podejmowane automatycznie lub tylko po zatwierdzeniu. Przykłady działań naprawczych obejmują wysyłanie pliku do kwarantanny, zatrzymywanie procesu i usuwanie zaplanowanego zadania. Wszystkie działania naprawcze są śledzone w Centrum akcji.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Zrzut ekranu przedstawiający Centrum akcji":::

**W tym artykule opisano**:

- [Jak korzystać z Centrum akcji](#how-to-use-the-action-center)

- [Działania naprawcze](#remediation-actions)

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="how-to-use-the-action-center"></a>Jak korzystać z Centrum akcji

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Centrum akcji**.

3. Wybierz **kartę Oczekujące** , aby wyświetlić i zatwierdzić (lub odrzucić) wszystkie oczekujące akcje. Takie działania mogą być związane z ochroną antywirusową/antymalware, automatycznymi badaniami, działaniami ręcznej odpowiedzi lub sesjami odpowiedzi na żywo.

4. Wybierz **kartę** Historia, aby wyświetlić listę ukończonych akcji. 

## <a name="remediation-actions"></a>Działania naprawcze

Usługa Microsoft Defender dla firm oferuje kilka działań naprawczych. Te działania obejmują akcje ręcznej odpowiedzi, akcje po zautomatyzowanym śledztwu i akcje odpowiedzi na żywo.

W poniższej tabeli wymieniono dostępne działania naprawcze:

| Źródło  | Akcje  |
|---------|---------|
| [Zautomatyzowane badania](../defender-endpoint/automated-investigations.md)      | - Poddaj plikowi kwarantannę <br/>- Usunięcie klucza rejestru <br/>- Zaśmieć proces <br/>— Zatrzymywanie usługi <br/>- Wyłączanie sterownika <br/>— Usuwanie zaplanowanego zadania        |
| [Ręczne akcje odpowiedzi](../defender-endpoint/respond-machine-alerts.md)   | - Uruchom skanowanie antywirusowe <br/>- Wyizoluj urządzenie <br/>— Zatrzymaj i poddaj kwarantannie <br/>— Dodaj wskaźnik, aby zablokować lub zezwolić na plik       |
| [Odpowiedź na żywo](../defender-endpoint/live-response.md)   | - Zbieranie danych forensycznych <br/>- Analizowanie pliku <br/>- Uruchamianie skryptu <br/>— Wysłać podejrzaną jednostkę do firmy Microsoft w celu analizy <br/>— Rozwiązywanie problemów z plikiem <br/>— proaktywne poszukiwania zagrożeń         |

## <a name="next-steps"></a>Następne kroki

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm](mdb-manage-devices.md)