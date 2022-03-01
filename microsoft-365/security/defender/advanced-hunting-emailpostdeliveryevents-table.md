---
title: EmailPostDeliveryEvents tabela w zaawansowanym schemacie wyszukiwania
description: Dowiedz się więcej o działaniach po dostarczeniu podjętych na Microsoft 365 e-mail w tabeli EmailPostDeliveryEvents zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, schłodzenie przed zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, EmailPostDeliveryEvents, identyfikator wiadomości sieciowej, nadawca, adresat, identyfikator załącznika, nazwa załącznika, werdykt złośliwego oprogramowania, werdykt wyłudzania informacji, liczba załączników, liczba linków, liczba adresów URL
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
ms.openlocfilehash: 59d611ae89aeedf386cd0dcad5939a9510f0820e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017872"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Tabela `EmailPostDeliveryEvents` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje o akcjach po dostarczeniu, które są podejmowane w wiadomościach e-mail przetwarzanych przez Microsoft 365. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType` wartości) obsługiwanych w tabeli, użyj wbudowanego schematu referencyjnego dostępnego w usłudze Defender dla chmury.

Aby uzyskać więcej informacji na temat poszczególnych wiadomości e-mail, [`EmailEvents`](advanced-hunting-emailevents-table.md)możesz również użyć tabel , [`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md)i [`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) . Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `NetworkMessageId` | `string` | Unikatowy identyfikator wiadomości e-mail wygenerowany przez Microsoft 365 |
| `InternetMessageId` | `string` | Publiczny identyfikator wiadomości e-mail ustawiany przez wysyłający system poczty e-mail |
| `Action` | `string` | Czynność podejmowane w encji |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie: Ręczne działania naprawcze, Phish ZAP, Malware ZAP |
| `ActionTrigger` | `string` | Wskazuje, czy akcja została wyzwolona przez administratora (ręcznie lub za pośrednictwem zatwierdzenia oczekującej akcji automatycznej), czy przez jakiś specjalny mechanizm, taki jak ZAP lub Dynamic Delivery (Dostarczanie dynamiczne). |
| `ActionResult` | `string` | Wynik akcji |
| `RecipientEmailAddress` | `string` | Adres e-mail adresata lub adres e-mail odbiorcy po rozwinięciu listy dystrybucyjnej |
| `DeliveryLocation` | `string` | Lokalizacja, w której wiadomość e-mail została dostarczona: Skrzynka odbiorcza/folder, Lokalnie/Zewnętrzne, Wiadomości-śmieci, Kwarantanna, Niepowodzenie, Upuszczenie, Elementy usunięte |
| `ReportId` | `long` | Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny w połączeniu z kolumnami DeviceName i Timestamp. |
| `ThreatTypes` | `string` | Werdykt z stosu filtrowania wiadomości e-mail na temat tego, czy wiadomość e-mail zawiera złośliwe oprogramowanie, wyłudzanie informacji lub inne zagrożenia |
| `DetectionMethods` | `string` | Metody używane do wykrywania złośliwego oprogramowania, wyłudzania informacji lub innych zagrożeń znalezionych w wiadomości e-mail |

## <a name="supported-event-types"></a>Obsługiwane typy zdarzeń
W poniższej tabeli są przechwycone zdarzenia z następującymi wartościami `ActionType` :

- **Ręczne działania naprawcze —** administrator ręcznie podjęł działania dotyczące wiadomości e-mail po jej dostarczyć do skrzynki pocztowej użytkownika. Dotyczy to czynności prowadzonych ręcznie za pośrednictwem [Eksploratora](../office-365-security/threat-explorer.md) zagrożeń lub zatwierdzeń zautomatyzowanych [akcji badania i odpowiedzi (AIR](m365d-autoir-actions.md)).
- **Phish ZAP** — [akcja automatycznego przeczyszczania bez godzin (ZAP)](../office-365-security/zero-hour-auto-purge.md) miała miejsce w wiadomości e-mail służącej do wyłudzania informacji po dostarczeniu.
- **Malware ZAP** — akcja automatycznego przeczyszczania bez godzin (ZAP) zajęła się wiadomością e-mail, która zawierała złośliwe oprogramowanie po dostarczeniu.

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
