---
title: Tabela DeviceFileCertificateInfo w zaawansowanym schemacie wyszukiwania
description: Informacje o podpisywaniu plików w tabeli DeviceFileCertificateInfo zaawansowanego schematu chłoń
keywords: zaawansowane wyszukiwania, chylenie przed zagrożeniami, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, podpis cyfrowy, certyfikat, podpisywanie plików, DeviceFileCertificateInfo
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
ms.openlocfilehash: 7b43b6ad8ed1422830f08358f460b20b16588996
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017876"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Tabela `DeviceFileCertificateInfo` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje o certyfikatach podpisywania plików. W poniższej tabeli są używane dane uzyskane z działań weryfikacji certyfikatów, które są regularnie wykonywane na plikach w punktach końcowych.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `DeviceId` | `string` | Unikatowy identyfikator komputera w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `SHA1` | `string` | SHA-1 pliku, do których zastosowano akcję |
| `IsSigned` | `boolean` | Wskazuje, czy plik jest podpisany. |
| `SignatureType` | `string` | Wskazuje, czy informacje o podpisie były odczytywane jako zawartość osadzona w samym pliku, czy odczytywane z pliku wykazu zewnętrznego. |
| `Signer` | `string` | Informacje o podpisie pliku |
| `SignerHash` | `string` | Unikatowa wartość skrótu identyfikująca osobę podpisujące |
| `Issuer` | `string` | Informacje o insektując urząd certyfikacji (UC, issuing certificate authority) |
| `IssuerHash` | `string` | Unikatowa wartość skrótu identyfikująca urząd certyfikacji (UC) |
| `CertificateSerialNumber` | `string` | Identyfikator certyfikatu, który jest unikatowy dla urzędu certyfikacji |
| `CrlDistributionPointUrls` | `string` |  Tablica JSON z listą adresów URL udziałów sieciowych, które zawierają certyfikaty i listy odwołań certyfikatów (listy CRL) |
| `CertificateCreationTime` | `datetime` | Data i godzina utworzenia certyfikatu |
| `CertificateExpirationTime` | `datetime` | Data i godzina wygaśnięcia certyfikatu |
| `CertificateCountersignatureTime` | `datetime` | Data i godzina, o których certyfikat został podpisany |
| `IsTrusted` | `boolean` | Wskazuje, czy plik jest zaufany na podstawie wyników funkcji WinVerifyTrust, która sprawdza nieznane informacje o certyfikacie głównym, nieprawidłowe podpisy, odwołane certyfikaty i inne godne zaufania atrybuty. |
| `IsRootSignerMicrosoft` | `boolean` | Wskazuje, czy podpis cyfrowym certyfikatem głównym jest firma Microsoft. |
| `ReportId` | `long` | Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny w połączeniu z kolumnami DeviceName i Timestamp. | 

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
