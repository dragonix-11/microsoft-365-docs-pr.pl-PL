---
title: Korzystaj z lokalnego skanera w celu zapobiegania utracie danych
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
description: Dowiedz się, jak za pomocą lokalnego skanera zapobiegać utracie danych skanować dane magazynowane i implementować akcje ochronne dla lokalnych udziałów plików oraz lokalnych folderów programu SharePoint i bibliotek dokumentów.
ms.openlocfilehash: ae5ffce9e664ada6e7476bb02b40f4a5c279d441
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624184"
---
# <a name="use-the-data-loss-prevention-on-premises-scanner"></a>Używanie lokalnego skanera zapobiegania utracie danych

Aby ułatwić zapoznanie się z Ochrona przed utratą danych w Microsoft Purview funkcji lokalnych i sposobem ich wyświetlania w zasadach DLP, przygotowaliśmy kilka scenariuszy, które należy wykonać.

> [!IMPORTANT]
> Te lokalne scenariusze DLP nie są oficjalnymi procedurami tworzenia i dostrajania zasad DLP. Zapoznaj się z poniższymi tematami, gdy musisz pracować z zasadami DLP w ogólnych sytuacjach:
>
> - [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
> - [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)
> - [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
> - [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>Scenariusz: odnajdywanie plików pasujących do reguł DLP

Dane z lokalnych powierzchni skanera DLP w kilku obszarach

#### <a name="activity-explorer"></a>Eksplorator działań

 Usługa Microsoft DLP dla środowiska lokalnego wykrywa dopasowania reguł DLP i zgłasza je do [Eksploratora aktywności](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer).

#### <a name="microsoft-365-audit-log"></a>Dziennik inspekcji platformy Microsoft 365

Dopasowania reguł DLP są dostępne w interfejsie użytkownika dziennika inspekcji. Zobacz [Przeszukiwanie dziennika inspekcji w portal zgodności Microsoft Purview](search-the-audit-log-in-security-and-compliance.md) lub dostępne w programie [PowerShell Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

#### <a name="aip"></a>AIP

Dane odnajdywania są dostępne w raporcie lokalnym w formacie csv, który jest przechowywany w następujących obszarach:

**%localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_%timestamp%.csv raportu**.

 Poszukaj następujących kolumn:

- Tryb DLP
- Stan DLP
- Komentarz DLP
- Nazwa reguły DLP
- Akcje DLP
- Właściciel
- Bieżące uprawnienia NTFS (SDDL)
- Zastosowane uprawnienia NTFS (SDDL)
- Typ uprawnień NTFS

### <a name="scenario-enforce-dlp-rule"></a>Scenariusz: wymuszanie reguły DLP

Jeśli chcesz wymusić reguły DLP dla zeskanowanych plików, wymuszanie musi być włączone zarówno w zadaniu skanowania zawartości w usłudze AIP, jak i na poziomie zasad w programie DLP.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>Konfigurowanie DLP w celu wymuszania akcji zasad

1. Otwórz [stronę Zapobieganie utracie danych](https://compliance.microsoft.com/datalossprevention?viewid=policies) i wybierz zasady DLP przeznaczone dla repozytoriów lokalizacji lokalnych skonfigurowanych w usłudze AIP.
2. Edytuj zasady.
3. Na stronie **Testowanie lub włącz zasady** wybierz pozycję **Tak, włącz ją od razu**.

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o lokalnym skanerze DLP](dlp-on-premises-scanner-learn.md)
- [Wprowadzenie do lokalnego skanera DLP](dlp-on-premises-scanner-get-started.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md)
