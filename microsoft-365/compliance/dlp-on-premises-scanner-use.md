---
title: Używanie Microsoft 365 ochrony przed utratą danych w środowisku lokalnym
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Dowiedz się, jak używać ochrony przed utratą Microsoft 365 w skanerze lokalnym do skanowania danych w spoczynku i implementowania akcji zabezpieczających dla lokalnych udziałów plików i lokalnych SharePoint folderów i bibliotek dokumentów.
ms.openlocfilehash: d726bfccf7dff2e95e3ccf996544f1db26bf09a2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988031"
---
# <a name="use-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>Używanie skanera Microsoft 365 ochrony przed utratą danych

Aby ułatwić Ci zapoznanie się z funkcjami lokalnymi funkcji DLP i ich działaniami w zasadach DLP, poniżej znajdziesz kilka scenariuszy do obserwowania.

> [!IMPORTANT]
> Te lokalne scenariusze ochrony przed dlp nie są oficjalnymi procedurami tworzenia i dostosowywania zasad DLP. Aby pracować z zasadami ochrony przed zasadami DLP w sytuacjach ogólnych, zapoznaj się z poniższymi tematami:
>
> - [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
> - [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)
> - [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
> - [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>Scenariusz: Odnajdowanie plików zgodnych z regułami DLP

Dane z lokalnych powierzchni skanera dlp w kilku obszarach

#### <a name="activity-explorer"></a>Eksplorator aktywności

 Zasady DLP firmy Microsoft w przypadku rozwiązań lokalnych wykrywają dopasowania reguł DLP i raportują je w [Eksploratorze aktywności](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer).

#### <a name="microsoft-365-audit-log"></a>Microsoft 365 inspekcji

Dopasowania reguł DLP są dostępne w interfejsie użytkownika dziennika inspekcji — [](search-the-audit-log-in-security-and-compliance.md) zobacz Przeszukiwanie dziennika inspekcji w centrum zgodności lub dostępnego za pomocą programu PowerShell [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

#### <a name="aip"></a>AIP

Odnajdowanie danych jest dostępne w raporcie lokalnym w formacie csv, który jest przechowywany w obszarze:

**%localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_%timestamp%.csv raport**.

 Poszukaj następujących kolumn:

- Tryb DLP
- Stan ochrony przed kodem DLP
- Komentarz DLP
- Nazwa reguły DLP
- Akcje DLP
- Właściciel
- Bieżące uprawnienia systemu plików NTFS (SDDL)
- Zastosowane uprawnienia systemu plików NTFS (SDDL)
- Typ uprawnień NTFS

### <a name="scenario-enforce-dlp-rule"></a>Scenariusz: wymuszanie reguły DLP

Jeśli chcesz wymusić reguły DLP dotyczące zeskanowanych plików, wymuś to wymuszanie musi być włączone zarówno w zadaniu skanowania zawartości w programie AIP, jak i na poziomie zasad w funkcji DLP.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>Konfigurowanie ochrony przed zasadami w celu wymuszania akcji zasad

1. Otwórz stronę [Ochrona przed utratą](https://compliance.microsoft.com/datalossprevention?viewid=policies) danych i wybierz zasady DLP, które są kierowane do lokalnych repozytoriów lokalizacji skonfigurowanych w UAD.
2. Edytuj zasady.
3. Na stronie **Test lub włącz zasady** wybierz pozycję **Tak, włącz ją od razu**.

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o lokalnym skanerze dlp](dlp-on-premises-scanner-learn.md)
- [Wprowadzenie do lokalnego skanera DLP](dlp-on-premises-scanner-get-started.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)
