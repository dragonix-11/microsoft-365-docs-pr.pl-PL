---
title: Wbudowana ochrona przed wirusami w usługach SharePoint Online, OneDrive i Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: reference
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Dowiedz się, SharePoint online wykrywa wirusy w plikach przesyłanych przez użytkowników i uniemożliwia użytkownikom pobieranie lub synchronizowanie plików.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ddb424458e991becefb98efbad5b2a86c5f9441c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988391"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>Wbudowana ochrona przed wirusami w usługach SharePoint Online, OneDrive i Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)

Microsoft 365 do skanowania plików, które użytkownicy przekażą do usługi SharePoint Online, OneDrive i Microsoft Teams. Ta ochrona jest zawarta we wszystkich subskrypcjach, które obejmują usługi SharePoint Online, OneDrive i Microsoft Teams.

> [!IMPORTANT]
> Wbudowane funkcje antywirusowe ułatwiają działanie wirusów. Nie są one w zamierzony sposób ochrony środowiska przed złośliwym oprogramowaniem. Zachęcamy wszystkich klientów do zbadania i wdrożenia ochrony przed złośliwym oprogramowaniem na różnych warstwach oraz do stosowania najlepszych rozwiązań w zakresie zabezpieczania swojej infrastruktury przedsiębiorstwa. Aby uzyskać więcej informacji na temat strategii i najlepszych rozwiązań, zobacz Przewodnik [po zabezpieczeniach](security-roadmap.md).

## <a name="what-happens-if-an-infected-file-is-uploaded-to-sharepoint-online"></a>Co się stanie, jeśli zainfekowany plik zostanie przekazany do usługi SharePoint Online?

Aparat Microsoft 365 wykrywania wirusów działa asynchronicznie (niezależnie od przekazywania plików) w SharePoint Online. **Nie wszystkie pliki są automatycznie skanowane**. Heuristics określają pliki do skanowania. Jeśli plik zawiera wirusa, jest oflagowany. W kwietniu 2018 r. usunęliśmy limit 25 MB zeskanowanych plików.

Oto, co się stanie:

1. Użytkownik przekaże plik do usługi SharePoint Online.
2. SharePoint online, w ramach procesów skanowania wirusów, określa później, czy plik spełnia kryteria skanowania.
3. Jeśli plik spełnia kryteria skanowania, aparat wykrywania wirusów skanuje ten plik.
4. Jeśli w zeskanowanym pliku znajduje się wirus, jego właściwość wskazuje, że plik został zainfekowany.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>Co się dzieje, gdy użytkownik próbuje pobrać zainfekowany plik przy użyciu przeglądarki?

Jeśli plik został zainfekowany, użytkownicy nie mogą go pobrać z usługi SharePoint online przy użyciu przeglądarki.

Oto, co się stanie:

1. Użytkownik otwiera przeglądarkę internetową i próbuje pobrać zainfekowany plik z witryny SharePoint Online.
2. Użytkownikowi jest wyświetlane ostrzeżenie, że wykryto wirusa. Domyślnie użytkownik może pobrać plik i spróbować go wyczyścić przy użyciu oprogramowania antywirusowego na własnym urządzeniu.

> [!NOTE]
>
> Administratorzy mogą użyć parametru *DisallowInfectedFileDownload* w oknie cmdlet [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant) w programie SharePoint Online PowerShell, aby uniemożliwić użytkownikom pobieranie zainfekowanych plików, nawet w oknie ostrzegawczym przed wirusami antywirusowymi. Aby uzyskać instrukcje, [zobacz SharePoint Online PowerShell](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files), aby uniemożliwić użytkownikom pobieranie złośliwych plików.
>
> Gdy tylko włączysz parametr *DisallowInfectedFileDownload* , dostęp do wykrytych/zablokowanych plików zostanie całkowicie zablokowany dla użytkowników i administratorów.

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>Co się stanie, gdy synchronizacja usługi OneDrive spróbuje zsynchronizować zainfekowany plik?

Kiedy złośliwy plik zostanie przekazany OneDrive, zostanie on zsynchronizowany z komputerami lokalnymi, zanim zostanie oznaczony jako złośliwe oprogramowanie. Po oznaczeniu go jako złośliwego oprogramowania użytkownik nie może już otworzyć synchronizowanych plików na swoim komputerze lokalnym.

## <a name="extended-capabilities-with-microsoft-defender-for-office-365"></a>Funkcje rozszerzone dzięki programowi Microsoft Defender dla Office 365

Microsoft 365 organizacje, w których usługa [Microsoft Defender dla systemu Office 365](defender-for-office-365.md) jest uwzględniona w subskrypcji lub została zakupiona jako dodatek, mogą włączyć załączniki programu Sejf dla usług SharePoint, OneDrive i Microsoft Teams w celu zwiększenia możliwości raportowania i ochrony. Aby uzyskać więcej informacji, [zobacz Sejf załączniki wiadomości SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).

## <a name="related-articles"></a>Artykuły pokrewne

[Ochrona przed złośliwym oprogramowaniem i oprogramowaniem wymuszającym okup w Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)

Aby uzyskać więcej informacji na temat oprogramowania antywirusowego w usługach SharePoint Online, OneDrive i Microsoft Teams, zobacz Ochrona przed zagrożeniami i [](protect-against-threats.md) Włączanie załączników programu Sejf dla SharePoint[, OneDrive i Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).
