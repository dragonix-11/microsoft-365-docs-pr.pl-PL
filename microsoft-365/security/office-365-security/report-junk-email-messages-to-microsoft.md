---
title: Zgłaszanie spamu, wiadomości niebędących spamem i wiadomości wyłudzających informacje do firmy Microsoft
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c31406ea-2979-4fac-9288-f835269b9d2f
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się więcej na temat różnych sposobów zgłaszania do firmy Microsoft dobrze i źle wysyłanych wiadomości i plików do analizy.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f7818b15d97d8d7ee33005927ff899e9f5ff5a06
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682730"
---
# <a name="report-messages-and-files-to-microsoft"></a>Zgłaszanie wiadomości i plików do firmy Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W organizacjach Microsoft 365 ze skrzynkami pocztowymi w organizacjach korzystających z usługi Exchange Online lub autonomicznej usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online użytkownicy i administratorzy mają kilka różnych metod raportowania wiadomości e-mail i plików do firmy Microsoft.

|Metoda|Opis|
|---|---|
|[Korzystanie z portalu Przesyłanie w celu przesyłania podejrzanych wiadomości-śmieci, wyłudków, adresów URL i plików do firmy Microsoft](admin-submission.md)|Zalecana metoda raportowania dla administratorów w organizacjach Exchange Online pocztowych (ta metoda nie jest dostępna w autonomicznej u korzystać z usługi EOP).|
|[Włączanie dodatku Wiadomość raportu lub Wyłudzanie informacji](enable-the-report-message-add-in.md)|Współpracuje z Outlook i Outlook w sieci Web (wcześniej znany jako Outlook Web App). <p> W zależności od subskrypcji wiadomości zgłoszone przez użytkowników wraz z dodatków są dostępne w portalu przesyłania [administratora, w](admin-submission.md) wynikach automatycznego badania i odpowiedzi [(AIR](air-view-investigation-results.md)), w raporcie wiadomości zgłoszonym [](view-email-security-reports.md#user-reported-messages-report)przez użytkowników oraz w [Eksploratorze](threat-explorer-views.md#email--submissions). <p> Zgłoszone wiadomości można skonfigurować w taki sposób, aby zostały skopiowane lub przekierowane do  specify przez Ciebie skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Zasady przesyłania użytkowników](user-submission.md).
|[Zgłaszanie wyników fałszywie dodatnich i ujemnych w Outlook](report-false-positives-and-false-negatives.md)|Prześlij wartości fałszywie dodatnie (dobre wiadomości e-mail, które zostały zablokowane lub wysłane do folderu wiadomości-śmieci), oraz wartości fałszywie ujemne (niechciane wiadomości e-mail lub wiadomości wyłudzane, które zostały dostarczone do skrzynki odbiorczej) do usługi Exchange Online Protection (EOP) za pomocą funkcji Wiadomości raportu.|
|[Używanie reguł przepływu poczty e-mail w celu zobaczenia, co użytkownicy zgłaszają firmie Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Dowiedz się, jak utworzyć regułę przepływu poczty e-mail (z znaną także regułą transportu), która będzie powiadamiać Cię, gdy użytkownicy będą raportować wiadomości do firmy Microsoft w celu analizy.|
|[Przesyłanie złośliwego oprogramowania i oprogramowania niebędące złośliwym oprogramowaniem do firmy Microsoft w celu analizy](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Aby przesłać załączniki i inne pliki, użyj Microsoft Security Intelligence witryny sieci Web.|

> [!NOTE]
> Dane z przesyłania do firmy Microsoft znajdują się Office 365 zgodności w amerykańskich centrach danych. Dane są przeglądane przez analityków w zespole inżynierów, aby zwiększyć skuteczność filtrów. Za przesłanie uważa się opinię, która pomoże ulepszyć filtry i jest przechowywana przez okres 30 dni. Następnie jest usuwany.
