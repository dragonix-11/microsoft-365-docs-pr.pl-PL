---
title: Tabela IdentityInfo w zaawansowanym schemacie chłoniania
description: Informacje o kontach użytkowników w tabeli IdentityInfo zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, AccountInfo, IdentityInfo, konto
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
ms.openlocfilehash: b09d1774ab35dbca9119deb98864d6c6f78051a9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017915"
---
# <a name="identityinfo"></a>IdentityInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Tabela `IdentityInfo` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje o kontach użytkowników uzyskiwanych z różnych usług, w tym dotyczących Azure Active Directory. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!NOTE]
>Nazwa tabeli została zmieniona na `AccountInfo`. Podczas zmieniania nazw wszystkie zapytania zapisane w portalu są automatycznie aktualizowane. Sprawdź zapytania zapisane w innym miejscu.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `AccountObjectId` | `string` | Unikatowy identyfikator konta w usłudze Azure AD |
| `AccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta |
| `OnPremSid` | `string` | Identyfikator zabezpieczeń lokalnych (SID) konta |
| `CloudSid` | `string` | Identyfikator zabezpieczeń konta w chmurze |
| `GivenName` | `string` | Imię lub imię użytkownika konta |
| `Surname` | `string` | Nazwisko, nazwisko lub nazwisko użytkownika konta |
| `AccountDisplayName` | `string` | Nazwa użytkownika konta wyświetlana w książce adresowej. Zwykle jest to połączenie danego lub imienia, inicjacji średniej i nazwiska lub nazwiska. |
| `Department` | `string` | Nazwa działu, do którego należy użytkownik konta |
| `JobTitle` | `string` | Stanowisko użytkownika konta |
| `AccountName` | `string` | Nazwa użytkownika konta |
| `AccountDomain` | `string` | Domena konta |
| `EmailAddress` | `string` | Adres SMTP konta |
| `SipProxyAddress` | `string` | Adres konta protokołu inicjowania sesji funkcji Voice over IP (VOIP, Voice over IP) |
| `City` | `string` | Miasto, w którym znajduje się użytkownik konta |
| `Country` | `string` | Kraj/region, w którym znajduje się użytkownik konta |
| `IsAccountEnabled` | `boolean` | Wskazuje, czy konto jest włączone. |

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
