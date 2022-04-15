---
title: Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm
description: Dowiedz się, jak wyświetlać & zarządzać alertami, reagować na zagrożenia, zarządzać urządzeniami i przeglądać akcje korygowania
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ec1d85b72cfbe17e182d3aed573476e4fadfdef6
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861449"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

W miarę wykrywania zagrożeń i wyzwalania alertów tworzone są zdarzenia. Zespół ds. zabezpieczeń twojej firmy może wyświetlać zdarzenia i zarządzać nimi w portalu Microsoft 365 Defender.

**Ten artykuł zawiera**:

- [Jak monitorować zdarzenia i alerty](#monitor-your-incidents--alerts)
- [Ważność alertu](#alert-severity)
- [Następne kroki](#next-steps)

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="monitor-your-incidents--alerts"></a>Monitorowanie zdarzeń & alertów

1. W portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w okienku nawigacji wybierz pozycję **Incydenty**. Wszystkie utworzone zdarzenia są wyświetlane na stronie.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="Zrzut ekranu przedstawiający listę zdarzeń":::

2. Wybierz alert, aby otworzyć okienko wysuwane, w którym możesz dowiedzieć się więcej na temat alertu. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="Zrzut ekranu przedstawiający zdarzenie wybrane z otwartym wysuwem":::

3. W okienku wysuwanym można wyświetlić tytuł alertu, wyświetlić listę zasobów (takich jak punkty końcowe lub konta użytkowników), których to dotyczy, podjąć dostępne akcje i użyć linków, aby wyświetlić więcej informacji, a nawet otworzyć stronę szczegółów wybranego alertu. 

> [!TIP]
> Microsoft Defender dla Firm jest przeznaczony do rozwiązywania wykrytych zagrożeń, oferując zalecane akcje. Podczas wyświetlania alertu poszukaj zalecanych akcji do wykonania. Zanotuj również ważność alertu, która jest określana nie tylko na podstawie ważności zagrożenia, ale także poziomu ryzyka dla firmy. 

## <a name="alert-severity"></a>Ważność alertu

Gdy Program antywirusowy Microsoft Defender przypisuje ważność alertu na podstawie bezwzględnej ważności wykrytego zagrożenia (złośliwego oprogramowania) i potencjalnego ryzyka dla pojedynczego punktu końcowego (jeśli zostanie zainfekowany).
Microsoft Defender dla Firm przypisuje ważność alertu na podstawie ważności wykrytego zachowania, rzeczywistego ryzyka dla punktu końcowego (urządzenia) i co ważniejsze, potencjalnego ryzyka dla firmy. W poniższej tabeli wymieniono kilka przykładów:

| Scenariusz | Ważność alertu | Powodu |
|:---|:---|:---|
| Program antywirusowy Microsoft Defender wykrywa i zatrzymuje zagrożenie, zanim wyrządzi jakiekolwiek szkody. | Informacyjne | Zagrożenie zostało zatrzymane, zanim zostały wyrządzone jakiekolwiek szkody. |
| Program antywirusowy Microsoft Defender wykrywa złośliwe oprogramowanie, które było wykonywane w firmie. Złośliwe oprogramowanie zostało zatrzymane i skorygowane. | Niskie | Chociaż niektóre szkody mogły zostać wyrządzone poszczególnym punktom końcowym, złośliwe oprogramowanie nie stanowi teraz zagrożenia dla Twojej firmy. |
| Złośliwe oprogramowanie, które jest wykonywane, jest wykrywane przez Microsoft Defender dla Firm. Złośliwe oprogramowanie jest blokowane niemal natychmiast. | Średni lub wysoki | Złośliwe oprogramowanie stanowi zagrożenie dla poszczególnych punktów końcowych i twojej firmy. |
| Wykryto podejrzane zachowanie, ale nie są jeszcze podejmowane żadne akcje korygujące. | Niski, Średni lub Wysoki | Ważność zależy od stopnia, w jakim zachowanie stanowi zagrożenie dla twojej firmy. |

## <a name="next-steps"></a>Następne kroki

- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)
- [Wyświetlanie lub edytowanie zasad urządzeń w Microsoft Defender dla Firm](mdb-view-edit-policies.md)