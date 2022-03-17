---
title: Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm
description: Dowiedz się, jak & alertami, odpowiadać na zagrożenia, zarządzać urządzeniami i przeglądać działania naprawcze
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: a814aa4ad002672fa3451ef1bcc524d9b03d4eb5
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63527074"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W przypadku wykrycia zagrożeń i wyzwolenia alertów są tworzone zdarzenia. Zespół zabezpieczeń Twojej firmy może wyświetlać zdarzenia i zarządzać nimi w portalu Microsoft 365 Defender sieci.

**Ten artykuł zawiera:**

- [Jak monitorować zdarzenia i alerty](#monitor-your-incidents--alerts)

- [Ważność alertu](#alert-severity)

- [Następne kroki](#next-steps)

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="monitor-your-incidents--alerts"></a>Monitorowanie alertów dotyczących & zdarzeń

1. W portalu Microsoft 365 Defender nawigacji ([https://security.microsoft.com](https://security.microsoft.com)) w okienku nawigacji wybierz **pozycję Zdarzenia**. Wszelkie zdarzenia, które zostały utworzone, są wymienione na stronie.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="Zrzut ekranu przedstawiający listę Zdarzenia":::

2. Wybierz alert, aby otworzyć jego okienko wysuwu, w którym możesz dowiedzieć się więcej o tym alertie. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="Zrzut ekranu przedstawiający wybrane zdarzenie z otwartym wysuwem wysuwanego ekranu":::

3. W okienku wysuwanym można wyświetlić tytuł alertu, wyświetlić listę zasobów (takich jak punkty końcowe lub konta użytkowników), których dotyczy problem, podjąć dostępne działania, a także użyć linków w celu wyświetlenia większej liczby informacji, a nawet otwarcia strony szczegółów dla wybranego alertu. 

> [!TIP]
> Usługa Microsoft Defender dla firm ma na celu pomoc w przypadku wykrytych zagrożeń, oferując zalecane działania. Podczas wyświetlania alertu poszukaj zalecanych akcji do podjęcia. Zanotuj także ważność alertów, która jest określana nie tylko na podstawie zagrożenia zagrożenia, ale również poziomu ryzyka dla firmy. 

## <a name="alert-severity"></a>Ważność alertu

Gdy Program antywirusowy Microsoft Defender alertu o ważności zależy od bezwzględnej ważności wykrytego zagrożenia (złośliwego oprogramowania) i potencjalnego ryzyka dla pojedynczego punktu końcowego (jeśli został on zainfekowany).
Usługa Microsoft Defender dla firm przypisuje ważność alertu na podstawie ważności wykrytego zachowania, rzeczywistego ryzyka dla punktu końcowego (urządzenia) oraz, co ważniejsze, potencjalnego ryzyka dla firmy. W poniższej tabeli podano kilka przykładów: <br/><br/>

| Scenariusz | Ważność alertu | Przyczyna |
|:---|:---|:---|
| Program antywirusowy Microsoft Defender wykrywa i zatrzymuje zagrożenia, zanim doszkoni. | Informacyjne | Zagrożenie zostało zatrzymane, zanim zostanie wykonane jakiekolwiek uszkodzenie. |
| Program antywirusowy Microsoft Defender wykrywa złośliwe oprogramowanie, które zostało wykonane w twojej firmie. Złośliwe oprogramowanie zostało zatrzymane i usunięte. | Niska | Mimo że niektóre uszkodzenia mogły zostać wykonane na poszczególnych punktach końcowych, złośliwe oprogramowanie nie stwarza teraz zagrożenia dla firmy. |
| Złośliwe oprogramowanie, które jest wykonywane, jest wykrywane przez usługę Microsoft Defender for Business. Złośliwe oprogramowanie jest blokowane niemal natychmiast. | Średni lub Wysoki | Złośliwe oprogramowanie stwarza zagrożenie dla poszczególnych punktów końcowych i dla twojej firmy. |
| Podejrzane zachowanie jest wykrywane, ale nie są jeszcze podejmowane żadne działania naprawcze. | Niska, Średnia lub Wysoka | Ważność zależy od stopnia, w jakim zachowanie stwarza zagrożenie dla firmy. |

## <a name="next-steps"></a>Następne kroki

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)

- [Wyświetlanie i edytowanie zasad urządzenia w u programie Microsoft Defender dla firm](mdb-view-edit-policies.md)