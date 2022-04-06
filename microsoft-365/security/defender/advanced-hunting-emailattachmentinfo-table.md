---
title: Tabela EmailAttachmentInfo w zaawansowanym schemacie wyszukiwania zagrożeń
description: Informacje o załącznikach wiadomości e-mail w tabeli EmailAttachmentInfo zaawansowanego schematu wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, odwołanie do schematu, kusto, tabela, kolumna, typ danych, opis, EmailAttachmentInfo, identyfikator wiadomości sieciowej, nadawca, adresat, identyfikator załącznika, nazwa załącznika, werdykt w sprawie złośliwego oprogramowania
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
ms.openlocfilehash: e787f79b5af90f45dd2823f53402830c7fc287db
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664045"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Tabela `EmailAttachmentInfo` w zaawansowanym schemacie [wyszukiwania zagrożeń](advanced-hunting-overview.md) zawiera informacje o załącznikach wiadomości e-mail przetwarzanych przez Ochrona usługi Office 365 w usłudze Microsoft Defender. To odwołanie służy do konstruowania zapytań, które zwracają informacje z tej tabeli.

Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, [zobacz zaawansowane informacje dotyczące wyszukiwania zagrożeń](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina zarejestrowania zdarzenia |
| `NetworkMessageId` | `string` | Unikatowy identyfikator wiadomości e-mail wygenerowany przez Microsoft 365 |
| `SenderFromAddress` | `string` | Adres e-mail nadawcy w nagłówku FROM, który jest widoczny dla adresatów poczty e-mail na klientach poczty e-mail |
| `SenderDisplayName` | `string` | Nazwa nadawcy wyświetlana w książce adresowej, zazwyczaj kombinacja danego lub imienia, inicjał środkowy oraz nazwisko lub nazwisko |
| `SenderObjectId` | `string` | Unikatowy identyfikator konta nadawcy w usłudze Azure AD |
| `RecipientEmailAddress` | `string` | Adres e-mail odbiorcy lub adres e-mail odbiorcy po rozszerzeniu listy dystrybucyjnej |
| `RecipientObjectId` | `string` | Unikatowy identyfikator adresata wiadomości e-mail w usłudze Azure AD |
| `FileName` | `string` | Nazwa pliku, do którego została zastosowana zarejestrowana akcja |
| `FileType` | `string` | Typ rozszerzenia pliku |
| `SHA256` | `string` | SHA-256 pliku, do który zastosowano zarejestrowaną akcję. To pole zwykle nie jest wypełnione — użyj kolumny SHA1, jeśli jest dostępna. |
| `ThreatTypes` | `string` | Werdykt ze stosu filtrowania wiadomości e-mail dotyczący tego, czy wiadomość e-mail zawiera złośliwe oprogramowanie, wyłudzanie informacji lub inne zagrożenia |
| `ThreatNames` | `string` | Wykryto nazwę wykrywania złośliwego oprogramowania lub innych zagrożeń |
| `DetectionMethods` | `string` | Metody służące do wykrywania złośliwego oprogramowania, wyłudzania informacji lub innych zagrożeń znalezionych w wiadomości e-mail |
| `ReportId` | `long` | Identyfikator zdarzenia na podstawie licznika powtarzającego się. Aby zidentyfikować unikatowe zdarzenia, ta kolumna musi być używana w połączeniu z kolumnami DeviceName i Timestamp. |
| `FileSize` | `string` | Rozmiar pliku w bajtach |

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
