---
title: Alerty usługi MRS
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appveyor:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Użyj porad dotyczących usługi migracji skrzynek pocztowych, aby monitorować opóźnienia w żądaniach migracji skrzynek pocztowych w organizacji.
ms.openlocfilehash: fe6f60b75fb7d27781d442faf82ff981ac54808a
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810742"
---
# <a name="service-advisories-for-mrs-source-delays-in-exchange-online-monitoring"></a>Porady dotyczące usług dotyczących opóźnień źródła danych w Exchange Online monitorowania

Porady dotyczące usługi opóźniania źródła usługi replikacji skrzynki pocztowej (MRS) informują o ograniczeniach magazynu lub problemach z wysokim wykorzystaniem procesora po stronie dzierżawy (źródła migracji), które mogą opóźniać migracje skrzynek pocztowych w organizacji Microsoft 365. Te porady dotyczące usług zawierają również linki do zasobów firmy Microsoft, które ułatwiają rozwiązanie tych problemów.

Te porady dotyczące usług są wyświetlane w Centrum administracyjne platformy Microsoft 365. Aby wyświetlić te porady dotyczące usług, przejdź do pozycji **Kondycja** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Kondycja usługi**</a> >  **Exchange Online** a następnie kliknij kartę **Aktywne problemy**.

## <a name="what-do-these-service-advisories-indicate"></a>Co wskazują te porady dotyczące usług?

Ta porada dotycząca usługi informuje o potencjalnych opóźnieniach migracji skrzynek pocztowych w organizacji. Obejmuje to migracje między lasami, migracje dołączania i migracje odłączania. Porada dotycząca usługi zawiera tabelę z informacjami o bieżących migracjach w organizacji. Oto przykład tabeli z informacjami o opóźnieniach migracji.

| BatchGuid | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | Sourceserver | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|12345678-1234-1234-1234-1234567891011|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|87654321-4321-4321-4321-1101987654321|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

Na poniższej liście opisano każdą kolumnę w poprzednim przykładzie.

- **BatchGuid**: unikatowy identyfikator GUID zadania migracji.

- **ExchangeGuid**: unikatowy identyfikator globalny (GUID) migrowanej skrzynki pocztowej użytkownika.

- **RequestGuid**: identyfikator GUID żądania migracji.

- **DelayReason**: przyczyna opóźnionej migracji.

- **QueueHours**: czas trwania migracji został umieszczony w kolejce i czeka.

- **DelayInHours**: czas trwania migracji został opóźniony.

- **SourceServer**: serwer lokalny, z którego pochodzi migracja.

- **RemoteDatabaseName**: nazwa bazy danych, z którego pochodzi migracja.

## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji na temat migracji usługi MRS i skrzynek pocztowych, zobacz następujące artykuły:

- [Przenoszenie skrzynki pocztowej w Exchange](/exchange/recipients/mailbox-moves)

- [wydajność i najlepsze rozwiązania dotyczące migracji Microsoft 365 i Office 365](/exchange/mailbox-migration/office-365-migration-best-practices)

- [Analiza wydajności migracji skrzynki pocztowej](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [Rozwiązywanie problemów z powolnymi migracjami](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [Sposoby migracji wielu kont e-mail do Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
