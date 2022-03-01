---
title: Funkcja FileProfile() podczas zaawansowanego wyszukiwania Microsoft 365 Defender
description: Dowiedz się, jak za pomocą pliku FileProfile() wzbogacić informacje o plikach podczas zaawansowanych zapytań wyszukiwania
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, FileProfile, profil pliku, funkcja, wzbogacenie
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
ms.openlocfilehash: 2cd8c91717af8390160bf45a625ae3a3044ee387
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017916"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Jest `FileProfile()` to funkcja wzbogacania [podczas zaawansowanego](advanced-hunting-overview.md) wyszukiwania, która dodaje następujące dane do plików znalezionych przez zapytanie.

| Kolumna | Typ danych | Opis |
|------------|---------------|-------------|
| `SHA1` | `string` | SHA-1 pliku, do których zastosowano akcję |
| `SHA256` | `string` | SHA-256 pliku, do których zastosowano akcję |
| `MD5` | `string` | Skrót MD5 pliku, do których zastosowano akcję |
| `FileSize` | `int` | Rozmiar pliku (w bajtach) |
| `GlobalPrevalence` | `int` | Liczba wystąpień encji obserwowanych globalnie przez firmę Microsoft |
| `GlobalFirstSeen` | `datetime` | Data i godzina, kiedy jednostka została obserwowana globalnie przez firmę Microsoft |
| `GlobalLastSeen` | `datetime` | Data i godzina ostatniego obserwowania jednostki przez firmę Microsoft globalnie |
| `Signer` | `string` | Informacje o podpisie pliku |
| `Issuer` | `string` | Informacje o insektując urząd certyfikacji (UC, issuing certificate authority) |
| `SignerHash` | `string` | Unikatowa wartość skrótu identyfikująca osobę podpisujące |
| `IsCertificateValid` | `boolean` | Czy certyfikat użyty do podpisania pliku jest prawidłowy |
| `IsRootSignerMicrosoft` | `boolean` | Wskazuje, czy podpis cyfrowym certyfikatem głównym jest firma Microsoft. |
| `SignatureState` | `string` | Stan podpisu pliku: SignedValid — plik jest podpisany z prawidłowym podpisem, SignedInvalid — plik jest podpisany, ale certyfikat jest nieprawidłowy, Niepodpisane — plik nie jest podpisany, Nieznany — nie można pobrać informacji o pliku
| `IsExecutable` | `boolean` | Czy plik jest plikiem wykonywalnym (PE, Portable Executable) |
| `ThreatName` | `string` | Nazwa wykrywania w przypadku znalezionego złośliwego oprogramowania lub innych zagrożeń |
| `Publisher` | `string` | Nazwa organizacji, która opublikowała plik |
| `SoftwareName` | `string` | Nazwa produktu oprogramowania |

## <a name="syntax"></a>Składnia

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Argumenty

- **x** — kolumna identyfikatora pliku do użycia: `SHA1`, `SHA256`, `InitiatingProcessSHA1`, lub `InitiatingProcessSHA256`; funkcja używa `SHA1` , jeśli nieokreślona
- **y** — ograniczenie do liczby rekordów, które mają się wzbogacić, od 1 do 1000; funkcja używa 100, jeśli nieokreślona


>[!TIP]
> Funkcje wzbogacania będą wyświetlać informacje uzupełniające tylko wtedy, gdy są dostępne. Dostępność informacji jest zróżnicowane i zależy od wielu czynników. Pamiętaj, aby wziąć to pod uwagę podczas używania fileProfile() w zapytaniach lub podczas tworzenia niestandardowych wykrywania. Aby uzyskać najlepsze wyniki, zalecamy użycie funkcji FileProfile() z funkcją SHA1.

## <a name="examples"></a>Przykłady

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Project tylko kolumnę SHA1 i ją wzbogacisz

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>Wzbogacanie pierwszych 500 rekordów i lista plików o niskiej jakości

```kusto
DeviceFileEvents
| where ActionType == "FileCreated" and Timestamp > ago(1d)
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 500) 
| where GlobalPrevalence < 15
```

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Więcej przykładów zapytań](advanced-hunting-shared-queries.md)
