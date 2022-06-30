---
title: Tabela DeviceFileCertificateInfo w zaawansowanym schemacie wyszukiwania zagrożeń
description: Dowiedz się więcej o informacjach dotyczących podpisywania plików w tabeli DeviceFileCertificateInfo zaawansowanego schematu wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, odwołanie do schematu, kusto, tabela, kolumna, typ danych, podpis cyfrowy, certyfikat, podpisywanie plików, DeviceFileCertificateInfo
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
ms.openlocfilehash: 019ca8eced735b8a9e24c2b0f3e3baae37757875
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554560"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Tabela `DeviceFileCertificateInfo` w zaawansowanym schemacie [wyszukiwania zagrożeń](advanced-hunting-overview.md) zawiera informacje o certyfikatach podpisywania plików. Ta tabela używa danych uzyskanych z działań weryfikacji certyfikatu regularnie wykonywanych w plikach w punktach końcowych.

Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, [zobacz zaawansowane informacje dotyczące wyszukiwania zagrożeń](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina zarejestrowania zdarzenia |
| `DeviceId` | `string` | Unikatowy identyfikator maszyny w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) maszyny |
| `SHA1` | `string` | SHA-1 pliku, do który zastosowano zarejestrowaną akcję |
| `IsSigned` | `boolean` | Wskazuje, czy plik jest podpisany |
| `SignatureType` | `string` | Wskazuje, czy informacje o podpisie były odczytywane jako zawartość osadzona w samym pliku, czy odczytywane z pliku wykazu zewnętrznego |
| `Signer` | `string` | Informacje dotyczące podpisywania pliku |
| `SignerHash` | `string` | Unikatowa wartość skrótu identyfikująca osoby podpisujące |
| `Issuer` | `string` | Informacje o urzędzie wystawiającym certyfikaty (CA) |
| `IssuerHash` | `string` | Unikatowa wartość skrótu identyfikująca urząd wystawiający certyfikat (CA) |
| `CertificateSerialNumber` | `string` | Identyfikator certyfikatu, który jest unikatowy dla urzędu wystawiającego certyfikaty (CA) |
| `CrlDistributionPointUrls` | `string` |  Tablica JSON z listą adresów URL udziałów sieciowych zawierających certyfikaty i listy odwołania certyfikatów |
| `CertificateCreationTime` | `datetime` | Data i godzina utworzenia certyfikatu |
| `CertificateExpirationTime` | `datetime` | Data i godzina wygaśnięcia certyfikatu |
| `CertificateCountersignatureTime` | `datetime` | Data i godzina podpisania certyfikatu |
| `IsTrusted` | `boolean` | Wskazuje, czy plik jest zaufany na podstawie wyników funkcji WinVerifyTrust, która sprawdza, czy nie ma informacji o nieznanym certyfikacie głównym, nieprawidłowych podpisów, odwołanych certyfikatów i innych wątpliwych atrybutów |
| `IsRootSignerMicrosoft` | `boolean` | Wskazuje, czy podpisywaniem certyfikatu głównego jest firma Microsoft i czy plik jest uwzględniony w systemie operacyjnym Windows |
| `ReportId` | `long` | Identyfikator zdarzenia na podstawie licznika powtarzającego się. Aby zidentyfikować unikatowe zdarzenia, ta kolumna musi być używana w połączeniu z kolumnami DeviceName i Timestamp. | 

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
