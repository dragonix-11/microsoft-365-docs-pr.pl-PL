---
title: Zgłaszanie wiadomości spamu, niespamowania i wyłudzania informacji firmie Microsoft
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
description: Administratorzy mogą poznać różne sposoby raportowania dobrych i złych komunikatów i plików do firmy Microsoft w celu analizy.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 56ef5cd5a376f4d10af1ad8c592dad02dbc8ef0a
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188443"
---
# <a name="report-messages-and-files-to-microsoft"></a>Zgłaszanie wiadomości i plików firmie Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, zarówno użytkownicy, jak i administratorzy mają kilka różnych metod raportowania wiadomości e-mail i plików do firmy Microsoft.

|Metoda|Opis|
|---|---|
|[Przesyłanie do firmy Microsoft podejrzanych wiadomości spamowych, adresów URL i plików przy użyciu portalu Przesyłania](admin-submission.md)|Zalecana metoda raportowania dla administratorów w organizacjach z Exchange Online skrzynkami pocztowymi (niedostępna w autonomicznej operacji EOP).|
|[Włączanie komunikatu raportu lub dodatków wyłudzania informacji o raportach](enable-the-report-message-add-in.md)|Współpracuje z Outlook i Outlook w sieci Web (dawniej znany jako Outlook Web App). <br/><br/> W zależności od subskrypcji komunikaty zgłaszane przez użytkowników przy użyciu dodatków są dostępne w [portalu Przesyłania administratora](admin-submission.md), [wynikach zautomatyzowanego badania i odpowiedzi (AIR),](air-view-investigation-results.md) [raporcie komunikatów zgłoszonych przez użytkownika](view-email-security-reports.md#user-reported-messages-report) i [Eksploratorze](threat-explorer-views.md#email--submissions). <br/><br/> Zgłoszone wiadomości można skonfigurować tak, aby były kopiowane lub przekierowywane do określonej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Zasady przesyłania użytkowników](user-submission.md).
|[Zgłaszanie wyników fałszywie dodatnich i fałszywie ujemnych w programie Outlook](report-false-positives-and-false-negatives.md)|Prześlij wyniki fałszywie dodatnie (dobra wiadomość e-mail, która została zablokowana lub wysłana do folderu śmieci) i fałszywie ujemne (niechciane wiadomości e-mail lub phish dostarczone do skrzynki odbiorczej) do Exchange Online Protection (EOP) przy użyciu funkcji komunikatu raportu.|
|[Używanie reguł przepływu poczty, aby zobaczyć, co użytkownicy zgłaszają firmie Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Dowiedz się, jak utworzyć regułę przepływu poczty (znaną również jako reguła transportu), która powiadamia użytkownika, gdy użytkownicy zgłaszają komunikaty do firmy Microsoft w celu analizy.|
|[Przesyłanie złośliwego oprogramowania i innych niż złośliwe oprogramowanie do firmy Microsoft w celu analizy](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Użyj witryny Microsoft Security Intelligence, aby przesłać załączniki i inne pliki.|

> [!NOTE]
> Gdy zgłaszasz jednostkę poczty e-mail firmie Microsoft, tworzymy kopię wszystkich elementów skojarzonych z wiadomością e-mail w celu uwzględnienia jej w naszych ciągłych przeglądach algorytmów. Ta kopia zawiera zawartość wiadomości e-mail, nagłówki wiadomości e-mail i powiązane dane dotyczące routingu wiadomości e-mail. Dołączono również załączniki w wiadomości.
>
> Firma Microsoft traktuje Twoją opinię jako uprawnienie organizacji do analizowania wszystkich wcześniej opisanych informacji i pracy nad dostosowaniem algorytmów higieny komunikatów. Wiadomość jest przechowywana w naszych bezpiecznych centrach danych z inspekcją w Stanach Zjednoczonych, dopóki nie usuniemy twojego przesłania nie później niż 30 dni po jego przekazaniu. Pracownicy firmy Microsoft mogą odczytywać przesłane wiadomości i załączniki, co zwykle nie jest dozwolone w przypadku wiadomości e-mail w Office 365. Jednak Twoja wiadomość e-mail jest nadal traktowana jako poufna między Tobą a firmą Microsoft i nie przekażemy Twojego przesłania żadnej innej stronie w celu przeczytania wiadomości e-mail lub załączników do tego procesu przeglądu.
