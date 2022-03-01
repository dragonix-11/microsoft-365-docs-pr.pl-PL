---
title: Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)
description: Dowiedz się, jak & alertami, odpowiadać na zagrożenia, zarządzać urządzeniami i przeglądać działania naprawcze
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 01/06/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 7b637b729cce02f00aa035571504266452e3bcd4
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027064"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business-preview"></a>Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W przypadku wykrycia zagrożeń i wyzwolenia alertów są tworzone zdarzenia. Zespół zabezpieczeń organizacji może wyświetlać zdarzenia i zarządzać nimi w portalu Microsoft 365 Defender sieci.

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
> Usługa Microsoft Defender dla firm (w wersji Preview) ma na celu pomoc w przypadku wykrytych zagrożeń, oferując zalecane działania. Podczas wyświetlania alertu poszukaj zalecanych akcji do podjęcia. Zanotuj także ważność alertów, która jest określana nie tylko na podstawie zagrożenia, ale także poziomu ryzyka dla Twojej organizacji. 

## <a name="alert-severity"></a>Ważność alertu

Gdy Program antywirusowy Microsoft Defender alertu o ważności zależy od bezwzględnej ważności wykrytego zagrożenia (złośliwego oprogramowania) i potencjalnego ryzyka dla pojedynczego punktu końcowego (jeśli został on zainfekowany).
Program Microsoft Defender dla firm (wersja Preview) przypisuje ważność alertów w zależności od dotkliwości wykrytego zachowania, rzeczywistego ryzyka dla punktu końcowego (urządzenia) i, co ważniejsze, potencjalnego ryzyka dla Twojej organizacji. W poniższej tabeli podano kilka przykładów: <br/><br/>

| Scenariusz | Ważność alertu | Przyczyna |
|:---|:---|:---|
| Program antywirusowy Microsoft Defender wykrywa i zatrzymuje zagrożenia, zanim doszkoni. | Informacyjne | Zagrożenie zostało zatrzymane, zanim zostanie wykonane jakiekolwiek uszkodzenie. |
| Program antywirusowy Microsoft Defender wykrywa złośliwe oprogramowanie, które wykonywało w organizacji. Złośliwe oprogramowanie zostało zatrzymane i usunięte. | Niska | Mimo że niektóre uszkodzenia mogły zostać wykonane na poszczególnych punktach końcowych, teraz złośliwe oprogramowanie nie stwarza zagrożenia dla organizacji. |
| Złośliwe oprogramowanie, które jest wykonywane, jest wykrywane przez program Microsoft Defender dla firm (wersja Preview). Złośliwe oprogramowanie jest blokowane niemal natychmiast. | Średni lub Wysoki | Złośliwe oprogramowanie stwarza zagrożenie dla poszczególnych punktów końcowych i organizacji. |
| Podejrzane zachowanie jest wykrywane, ale nie są jeszcze podejmowane żadne działania naprawcze. | Niska, Średnia lub Wysoka | Istotność zależy od stopnia zagrożenia organizacji. |

## <a name="next-steps"></a>Następne kroki

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm (wersja Preview)](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)

- [Wyświetlanie i edytowanie zasad urządzeń w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-edit-policies.md)