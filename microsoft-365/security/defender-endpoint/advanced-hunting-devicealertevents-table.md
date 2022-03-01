---
title: Tabela DeviceAlertEvents w zaawansowanym schemacie wyszukiwania
description: Informacje o zdarzeniach związanych z generowanie alertów w tabeli DeviceAlertEvents zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, mdatp, microsoft defender atp, microsoft defender for endpoint, wyszukiwanie wdatp, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, DeviceAlertEvents, alert, ważność, kategoria
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/22/2020
ms.technology: mde
ms.openlocfilehash: 32dbff60a37c31cdbfd492eb5d746a10d9b7a185
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021326"
---
# <a name="devicealertevents"></a>DeviceAlertEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Tabela `DeviceAlertEvents` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje o alertach w programie Microsoft 365 Defender. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zobacz [informacje dotyczące zaawansowanego schematu łęgowania](advanced-hunting-schema-reference.md).

|Nazwa kolumny|Typ danych|Opis|
|---|---|---|
|`AlertId`|ciąg|Unikatowy identyfikator alertu|
|`Timestamp`|datetime|Data i godzina nagrania zdarzenia|
|`DeviceId`|ciąg|Unikatowy identyfikator urządzenia w usłudze|
|`DeviceName`|ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia|
|`Severity`|ciąg|Wskazuje potencjalny wpływ (wysoki, średni lub niski) wskaźnika zagrożenia lub działania na naruszenie określone przez alert|
|`Category`|ciąg|Typ wskaźnika zagrożenia lub działania w przypadku naruszenia zabezpieczeń wskazanego przez alert|
|`Title`|ciąg|Tytuł alertu|
|`FileName`|ciąg|Nazwa pliku, do których zastosowano akcję|
|`SHA1`|ciąg|SHA-1 pliku, do których zastosowano akcję|
|`RemoteUrl`|ciąg|Adres URL lub w pełni kwalifikowana nazwa domeny (FQDN), z która była połączona|
|`RemoteIP`|ciąg|Adres IP, z który był połączony|
|`AttackTechniques`|ciąg|MiTRE ATT&technik CK skojarzonych z działaniem, które wyzwoliło alert|
|`ReportId`|długo|Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny z kolumnami `DeviceName` i `Timestamp`|
|`Table`|ciąg|Tabela zawierająca szczegóły zdarzenia|

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Opis schematu](advanced-hunting-schema-reference.md)
