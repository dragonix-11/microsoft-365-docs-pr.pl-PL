---
title: Tabela AlertEvidence w zaawansowanym schemacie myśliwski
description: Informacje dotyczące alertów w tabeli AlertY dotyczące zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, schłoń pod niebędące zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, AlertInfo, alert, jednostki, dowody, plik, adres IP, urządzenie, komputer, użytkownik, konto
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
ms.openlocfilehash: 9d7fc7e757b15c3682368cbd6c41b32c18724422
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017899"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Tabela w zaawansowanym schemacie chłoń zawiera informacje o różnych jednostkach — plikach, adresach IP, adresach URL, użytkownikach lub urządzeniach — skojarzonych z alertami z programu Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps i Microsoft Defender for Identity.[](advanced-hunting-overview.md) `AlertEvidence` To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `AlertId` | `string` | Unikatowy identyfikator alertu |
| `ServiceSource` | `string` | Produkt lub usługa, która podała informacje o alertach |
| `EntityType` | `string` | Typ obiektu, na przykład plik, proces, urządzenie lub użytkownik |
| `EvidenceRole` | `string` | Sposób, w jaki jednostka bierze udział w alercie, wskazując, czy ma ona wpływ, czy jest jedynie powiązana |
| `EvidenceDirection` | `string` | Wskazuje, czy jednostka jest źródłem, czy miejscem docelowym połączenia sieciowego. |
| `FileName` | `string` | Nazwa pliku, do których zastosowano akcję |
| `FolderPath` | `string` | Folder zawierający plik, do którym zastosowano akcję |
| `SHA1` | `string` | SHA-1 pliku, do których zastosowano akcję |
| `SHA256` | `string` | SHA-256 pliku, do których zastosowano akcję. To pole zwykle nie jest wypełnione — jeśli jest dostępne, użyj kolumny SHA1. |
| `FileSize` | `int` | Rozmiar pliku (w bajtach) |
| `ThreatFamily` | `string` | Rodzina złośliwego oprogramowania, w ramach których sklasyfikowano podejrzany lub złośliwy plik lub proces |
| `RemoteIP` | `string` | Adres IP, z który był połączony |
| `RemoteUrl` | `string` | Adres URL lub w pełni kwalifikowana nazwa domeny (FQDN), z która była połączona |
| `AccountName` | `string` | Nazwa użytkownika konta |
| `AccountDomain` | `string` | Domena konta |
| `AccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta |
| `AccountObjectId` | `string` | Unikatowy identyfikator konta w aplikacji Azure Active Directory |
| `AccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta |
| `DeviceId` | `string` | Unikatowy identyfikator urządzenia w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `LocalIP` | `string` | Adres IP przypisany do urządzenia lokalnego używanego podczas komunikacji |
| `NetworkMessageId` | `string` | Unikatowy identyfikator wiadomości e-mail wygenerowany przez Office 365 |
| `EmailSubject` | `string` | Temat wiadomości e-mail |
| `ApplicationId` | `string` | Unikatowy identyfikator aplikacji |
| `Application` | `string` | Aplikacja, która wykonała nagraną akcję |
| `ProcessCommandLine` | `string` | Wiersz polecenia użyty do utworzenia nowego procesu |
| `AdditionalFields` | `string` | Dodatkowe informacje o zdarzeniu w formacie tablicowym JSON |
| `RegistryKey` |`string` | Klucz rejestru, do których zastosowano zarejestrowane działanie |
| `RegistryValueName` |`string` | Nazwa wartości rejestru, do których zastosowano zarejestrowane działanie |
| `RegistryValueData` |`string` | Dane wartości rejestru, do których zastosowano zarejestrowane działanie |

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
