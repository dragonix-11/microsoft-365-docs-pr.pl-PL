---
title: Tabela EmailAttachmentInfo w zaawansowanym schemacie wyszukiwania
description: Informacje o załącznikach wiadomości e-mail w tabeli EmailAttachmentInfo zaawansowanego schematu wyszukiwania
keywords: zaawansowane wyszukiwania, chwalenie przed zagrożeniami, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, EmailAttachmentInfo, identyfikator wiadomości sieciowej, nadawca, adresat, identyfikator załącznika, nazwa załącznika, werdykt złośliwego oprogramowania
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: ac3e7aeff6778709f68aa1da74446cf55a1a6c06
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017906"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Tabela `EmailAttachmentInfo` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje o załącznikach w wiadomościach e-mail przetwarzanych przez usługę Microsoft Defender for Office 365. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `NetworkMessageId` | `string` | Unikatowy identyfikator wiadomości e-mail wygenerowany przez Microsoft 365 |
| `SenderFromAddress` | `string` | Adres e-mail nadawcy w nagłówku OD, który jest widoczny dla adresatów wiadomości e-mail w ich klientach poczty e-mail |
| `SenderDisplayName` | `string` | Imię i nazwisko nadawcy wyświetlane w książce adresowej. Zwykle jest to połączenie imienia lub danego imienia, inicjała środkowego oraz nazwiska lub nazwiska. |
| `SenderObjectId` | `string` | Unikatowy identyfikator konta nadawcy w usłudze Azure AD |
| `RecipientEmailAddress` | `string` | Adres e-mail adresata lub adres e-mail odbiorcy po rozwinięciu listy dystrybucyjnej |
| `RecipientObjectId` | `string` | Unikatowy identyfikator adresata poczty e-mail w usłudze Azure AD |
| `FileName` | `string` | Nazwa pliku, do których zastosowano akcję |
| `FileType` | `string` | Typ rozszerzenia pliku |
| `SHA256` | `string` | SHA-256 pliku, do których zastosowano akcję. To pole zwykle nie jest wypełnione — jeśli jest dostępne, użyj kolumny SHA1. |
| `ThreatTypes` | `string` | Werdykt z stosu filtrowania wiadomości e-mail na temat tego, czy wiadomość e-mail zawiera złośliwe oprogramowanie, wyłudzanie informacji lub inne zagrożenia |
| `ThreatNames` | `string` | Nazwa wykrywania w przypadku znalezionego złośliwego oprogramowania lub innych zagrożeń |
| `DetectionMethods` | `string` | Metody używane do wykrywania złośliwego oprogramowania, wyłudzania informacji lub innych zagrożeń znalezionych w wiadomości e-mail |
| `ReportId` | `long` | Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny w połączeniu z kolumnami DeviceName i Timestamp. |
| `FileSize` | `string` | Rozmiar pliku (w bajtach) |

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
