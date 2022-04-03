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
description: Alerty usługi migracji skrzynek pocztowych są służące do monitorowania opóźnień żądań migracji skrzynek pocztowych w organizacji.
ms.openlocfilehash: 6b4b618bae602c7c06b2d6371e39cc865d0a3407
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64567989"
---
# <a name="service-alerts-for-mrs-source-delays-in-exchange-online-monitoring"></a>Alerty usługi dotyczące opóźnień źródła MRS w Exchange Online sieci

Alerty usługi replikacji skrzynek pocztowych (MRS, Mailbox Replication Service) informują o ograniczeniach magazynowania lub problemach użycia procesora po stronie dzierżawy (źródła migracji), które mogą opóźniać migrację skrzynek pocztowych w Microsoft 365 organizacji. Te alerty usługi zawierają również linki do zasobów firmy Microsoft, które ułatwiają rozwiązanie tych problemów.

Alerty usługi są wyświetlane w Centrum administracyjne platformy Microsoft 365. Aby wyświetlić te alerty usługi, przejdź  > <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank"></a> >  do Kondycja usługi **Exchange Online** a następnie kliknij **kartę Aktywne** problemy.

## <a name="what-do-these-service-alerts-indicate"></a>Co oznaczają te alerty usługi?

Ten alert usługi informuje o potencjalnych opóźnieniach migracji skrzynek pocztowych w organizacji. Obejmuje to migracje z lasów innych niż lasy, migracje w celu wywrócenia i migracje wywróceń. Alert usługi zawiera tabelę z informacjami o bieżących migracjach w organizacji. Oto przykład tabeli z informacjami o opóźnieniach migracji.

| BatchName | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | SourceServer (Serwer źródłowy) | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|Migracja MRS|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|Monitorowanie dzierżawy MRS|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

Na poniższej liście opisano każdą kolumnę z poprzedniego przykładu.

- **BatchName**: Unikatowa nazwa zadania migracji.

- **ExchangeGuid**: unikatowy identyfikator globalny (GUID) skrzynki pocztowej użytkownika, która jest migrowana.

- **RequestGuid**: Identyfikator GUID żądania migracji.

- **DelayReason**: Przyczyna opóźnionej migracji.

- **QueueHours**: Czas trwania migracji znajduje się w kolejce i czekania.

- **DelayInHours**: Czas trwania migracji został opóźniony.

- **SourceServer(Serwer** źródłowy): serwer lokalnego, z którego pochodzi migracja.

- **RemoteDatabaseName**: nazwa bazy danych, z której pochodzi migracja.

## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji na temat migracji mrs i skrzynek pocztowych, zobacz następujące artykuły:

- [Skrzynka pocztowa jest przesu ń w Exchange](/exchange/recipients/mailbox-moves)

- [Microsoft 365 i Office 365 migracji oraz najlepsze rozwiązania](/exchange/mailbox-migration/office-365-migration-best-practices)

- [Analiza wydajności migracji skrzynek pocztowych](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [Rozwiązywanie problemów z powolną migracją](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [Sposoby migrowania wielu kont e-mail do Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
