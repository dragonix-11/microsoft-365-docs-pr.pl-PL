---
title: Tabela IdentityDirectoryEvents w zaawansowanym schemacie wyszukiwania
description: Informacje o kontrolerze domeny i zdarzeniach usługi Active Directory w tabeli IdentityDirectoryEvents zaawansowanego schematu wyszukiwania
keywords: zaawansowane łowiectwo, chylenie przed zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, IdentityDirectoryEvents, kontroler domeny, usługa Active Directory, usługa Microsoft Defender for Identity, tożsamości
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
ms.openlocfilehash: b7d880e0865ebeaf09e40fc543abba37566d2081
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017938"
---
# <a name="identitydirectoryevents"></a>IdentityDirectoryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Tabela `IdentityDirectoryEvents` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera zdarzenia dotyczące lokalnego kontrolera domeny z uruchomionym kontrolerem domeny Active Directory (AD). Ta tabela zawiera różne zdarzenia związane z tożsamością, takie jak zmiany haseł, wygasanie haseł i zmiany głównej nazwy użytkownika (UPN). Przechwytuje także zdarzenia systemowe na kontrolerze domeny, takie jak planowanie zadań i aktywność programu PowerShell. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType` wartości) obsługiwanych w tabeli, użyj wbudowanego schematu referencyjnego dostępnego w usłudze Defender dla chmury.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie. Aby uzyskać [szczegółowe informacje, zobacz informacje](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) dotyczące schematu w portalu |
| `Application` | `string` | Aplikacja, która wykonała nagraną akcję |
| `TargetAccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta, do których zastosowano zarejestrowane działanie |
| `TargetAccountDisplayName` | `string` | Nazwa wyświetlana konta, do których zastosowano akcję |
| `TargetDeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia, do których zastosowano zarejestrowane działanie |
| `DestinationDeviceName` | `string` | Nazwa urządzenia z uruchomionym aplikacją serwera, która przetworzona została nagrana akcja |
| `DestinationIPAddress` | `string` | Adres IP urządzenia z uruchomionym aplikacją serwera, która przetworzyła nagraną akcję |
| `DestinationPort` | `string` | Port docelowy działania |
| `Protocol` | `string` | Protokół używany podczas komunikacji |
| `AccountName` | `string` | Nazwa użytkownika konta |
| `AccountDomain` | `string` | Domena konta |
| `AccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta |
| `AccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta |
| `AccountObjectId` | `string` | Unikatowy identyfikator konta w aplikacji Azure Active Directory |
| `AccountDisplayName` | `string` | Nazwa użytkownika konta wyświetlana w książce adresowej. Zwykle jest to połączenie danego lub imienia, inicjacji średniej i nazwiska lub nazwiska. |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia |
| `IPAddress` | `string` | Adres IP przypisany do urządzenia podczas komunikacji |
| `Port` | `string` | Port TCP używany podczas komunikacji |
| `Location` | `string` | Miasto, kraj lub inna lokalizacja geograficzna skojarzona z wydarzeniem |
| `ISP` | `string` | Internet usługodawca skojarzony z adresem IP |
| `ReportId` | `long` | Unikatowy identyfikator zdarzenia |
| `AdditionalFields` | `string` | Dodatkowe informacje o encji lub zdarzeniu |

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
