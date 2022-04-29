---
title: Tabela EmailPostDeliveryEvents w zaawansowanym schemacie wyszukiwania zagrożeń
description: Dowiedz się więcej o akcjach po dostarczeniu wykonanych w Microsoft 365 wiadomościach e-mail w tabeli EmailPostDeliveryEvents zaawansowanego schematu wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, dokumentacja schematu, kusto, tabela, kolumna, typ danych, opis, EmailPostDeliveryEvents, identyfikator wiadomości sieciowej, nadawca, adresat, identyfikator załącznika, nazwa załącznika, werdykt w sprawie złośliwego oprogramowania, werdykt wyłudzania informacji, liczba załączników, liczba linków, liczba adresów URL
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
ms.openlocfilehash: 876b240d73613637cc2f564ce6415873b645293c
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130588"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona usługi Office 365 w usłudze Microsoft Defender

Tabela `EmailPostDeliveryEvents` w zaawansowanym schemacie [wyszukiwania zagrożeń](advanced-hunting-overview.md) zawiera informacje o akcjach po dostarczeniu wykonanych w wiadomościach e-mail przetwarzanych przez Microsoft 365. To odwołanie służy do konstruowania zapytań, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType`wartości) obsługiwanych przez tabelę, użyj wbudowanego odwołania do schematu dostępnego w Defender dla Chmury.

Aby uzyskać więcej informacji na temat poszczególnych wiadomości e-mail, możesz również użyć [`EmailEvents`](advanced-hunting-emailevents-table.md)tabel , [`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md)i [`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) . Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, [zobacz zaawansowane informacje dotyczące wyszukiwania zagrożeń](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina zarejestrowania zdarzenia |
| `NetworkMessageId` | `string` | Unikatowy identyfikator wiadomości e-mail wygenerowany przez Microsoft 365 |
| `InternetMessageId` | `string` | Publiczny identyfikator wiadomości e-mail ustawionej przez system wysyłania wiadomości e-mail |
| `Action` | `string` | Akcja podjęta w jednostce |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie: Ręczne korygowanie, Phish ZAP, Złośliwe oprogramowanie ZAP |
| `ActionTrigger` | `string` | Wskazuje, czy akcja została wyzwolona przez administratora (ręcznie lub poprzez zatwierdzenie oczekującej akcji zautomatyzowanej), czy też przez specjalny mechanizm, taki jak zap lub dynamiczne dostarczanie |
| `ActionResult` | `string` | Wynik akcji |
| `RecipientEmailAddress` | `string` | Adres e-mail odbiorcy lub adres e-mail odbiorcy po rozszerzeniu listy dystrybucyjnej |
| `DeliveryLocation` | `string` | Lokalizacja, w której została dostarczona wiadomość e-mail: Skrzynka odbiorcza/Folder, Lokalna/Zewnętrzna, Śmieci, Kwarantanna, Niepowodzenie, Porzucone, Usunięte elementy |
| `ReportId` | `long` | Identyfikator zdarzenia na podstawie licznika powtarzającego się. Aby zidentyfikować unikatowe zdarzenia, ta kolumna musi być używana w połączeniu z kolumnami DeviceName i Timestamp. |
| `ThreatTypes` | `string` | Werdykt ze stosu filtrowania wiadomości e-mail dotyczący tego, czy wiadomość e-mail zawiera złośliwe oprogramowanie, wyłudzanie informacji lub inne zagrożenia |
| `DetectionMethods` | `string` | Metody służące do wykrywania złośliwego oprogramowania, wyłudzania informacji lub innych zagrożeń znalezionych w wiadomości e-mail |

## <a name="supported-event-types"></a>Obsługiwane typy zdarzeń
Ta tabela przechwytuje zdarzenia z następującymi `ActionType` wartościami:

- **Ręczne korygowanie** — administrator ręcznie podjął akcję w wiadomości e-mail po dostarczeniu jej do skrzynki pocztowej użytkownika. Obejmuje to akcje wykonywane ręcznie za pośrednictwem [Eksploratora zagrożeń](../office-365-security/threat-explorer.md) lub zatwierdzenia [zautomatyzowanych akcji badania i reagowania (AIR](m365d-autoir-actions.md)).
- **Phish ZAP** — [automatyczne przeczyszczanie o zerowej godzinie (ZAP)](../office-365-security/zero-hour-auto-purge.md) podjęło działania w wiadomości e-mail wyłudzającej informacje po dostarczeniu.
- **Złośliwe oprogramowanie ZAP** — zerogodzinne automatyczne przeczyszczanie (ZAP) podjęło działania w wiadomości e-mail zawierającej złośliwe oprogramowanie po dostarczeniu.

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
