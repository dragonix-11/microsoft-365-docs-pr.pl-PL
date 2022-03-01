---
title: Tabela IdentityQueryEvents w zaawansowanym schemacie wyszukiwania
description: Informacje o zdarzeniach zapytań usługi Active Directory w tabeli IdentityQueryEvents zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, schłoń pod niebędący zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, IdentityQueryEvents, Azure AD, Active Directory, Microsoft Defender for Identity, tożsamości, zapytania LDAP
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
ms.openlocfilehash: 0b3c98b629d8984b984af3f3dba25a65ab7671e6
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017911"
---
# <a name="identityqueryevents"></a>IdentityQueryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Tabela `IdentityQueryEvents` w zaawansowanym [schemacie wyszukiwania](advanced-hunting-overview.md) zawiera informacje o zapytaniach wykonywanych na obiektach usługi Active Directory, takich jak użytkownicy, grupy, urządzenia i domeny. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType` wartości) obsługiwanych w tabeli, użyj wbudowanego schematu referencyjnego dostępnego w usłudze Defender dla chmury.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie. Aby uzyskać [szczegółowe informacje, zobacz informacje](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) dotyczące schematu w portalu |
| `Application` | `string` | Aplikacja, która wykonała nagraną akcję |
| `QueryType` | `string` | Typ zapytania, na przykład QueryGroup, QueryUser lub Wyliczanie użytkowników |
| `QueryTarget` | `string` | Nazwa użytkownika, grupy, urządzenia, domeny lub dowolnego innego typu encji, do których jest ponawiane zapytanie |
| `Query` | `string` | Ciąg użyty do uruchomienia zapytania |
| `Protocol` | `string` | Protokół używany podczas komunikacji |
| `AccountName` | `string` | Nazwa użytkownika konta |
| `AccountDomain` | `string` | Domena konta |
| `AccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta |
| `AccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta |
| `AccountObjectId` | `string` | Unikatowy identyfikator konta w usłudze Azure AD |
| `AccountDisplayName` | `string` | Nazwa użytkownika konta wyświetlana w książce adresowej. Zwykle jest to połączenie danego lub imienia, inicjacji średniej i nazwiska lub nazwiska. |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) punktu końcowego |
| `IPAddress` | `string` | Adres IP przypisany do punktu końcowego i używany podczas powiązanej komunikacji sieciowej |
| `Port` | `string` | Port TCP używany podczas komunikacji |
| `DestinationDeviceName` | `string` | Nazwa urządzenia z uruchomionym aplikacją serwera, która przetworzona została nagrana akcja |
| `DestinationIPAddress` | `string` | Adres IP urządzenia z uruchomionym aplikacją serwera, która przetworzyła nagraną akcję |
| `DestinationPort` | `string` | Docelowy port pokrewnej komunikacji sieciowej |
| `TargetDeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia, do których zastosowano zarejestrowane działanie |
| `TargetAccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta, do których zastosowano zarejestrowane działanie |
| `TargetAccountDisplayName` | `string` | Nazwa wyświetlana konta, do których zastosowano akcję |
| `Location` | `string` | Miasto, kraj lub inna lokalizacja geograficzna skojarzona z wydarzeniem |
| `ReportId` | `long` | Unikatowy identyfikator zdarzenia |
| `AdditionalFields` | `string` | Dodatkowe informacje o encji lub zdarzeniu |

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
