---
title: Tabela DeviceFileEvents w zaawansowanym schemacie wyszukiwania
description: Informacje o zdarzeniach związanych z plikami w tabeli DeviceFileEvents zaawansowanego schematu łęgowania
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, filecreationevents, DeviceFileEvents, pliki, ścieżka, skrót, sha1, sha256, md5
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
ms.openlocfilehash: 2350e2dfd4736743f23d181d4fc2c6de0d82ccc0
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017942"
---
# <a name="devicefileevents"></a>DeviceFileEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Tabela `DeviceFileEvents` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje na temat tworzenia plików, modyfikowania i innych zdarzeń systemowych plików. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType` wartości) obsługiwanych w tabeli, użyj wbudowanego schematu referencyjnego dostępnego w usłudze Defender dla chmury.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `DeviceId` | `string` | Unikatowy identyfikator komputera w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie. Aby uzyskać [szczegółowe informacje, zobacz informacje](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) dotyczące schematu w portalu |
| `FileName` | `string`| Nazwa pliku, do których zastosowano akcję |
| `FolderPath` | `string` | Folder zawierający plik, do którym zastosowano akcję |
| `SHA1` | `string` | SHA-1 pliku, do których zastosowano akcję |
| `SHA256` | `string` | SHA-256 pliku, do których zastosowano akcję. To pole zwykle nie jest wypełnione — jeśli jest dostępne, użyj kolumny SHA1. |
| `MD5` | `string` | Skrót MD5 pliku, do których zastosowano akcję |
| `FileOriginUrl` | `string` | Adres URL, z którego pobrano plik |
| `FileOriginReferrerUrl` | `string` | Adres URL strony internetowej, która zawiera link do pobranego pliku |
| `FileOriginIP` | `string` | Adres IP, z którego pobrano plik |
| `PreviousFolderPath` | `string` | Oryginalny folder zawierający plik przed zastosowaniem zarejestrowanej akcji |
| `PreviousFileName` | `string` | Oryginalna nazwa pliku, dla których zmieniono nazwę w wyniku akcji |
| `FileSize` | `long` | Rozmiar pliku (w bajtach) |
| `InitiatingProcessAccountDomain` | `string` | Domena konta, na które uruchomiono proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountName` | ciąg | Nazwa użytkownika konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountObjectId` | `string` | Identyfikator obiektu usługi Azure AD konta użytkownika, który uruchomił proces odpowiedzialny za zdarzenie |
| `InitiatingProcessMD5` | `string` | Skrót MD5 procesu (pliku obrazu), który zainicjował zdarzenie |
| `InitiatingProcessSHA1` | `string` | SHA-1 procesu (pliku obrazu), który zainicjował zdarzenie |
| `InitiatingProcessSHA256` | `string` | SHA-256 procesu (pliku obrazu), który zainicjował zdarzenie. To pole zwykle nie jest wypełnione — jeśli jest dostępne, użyj kolumny SHA1. |
| `InitiatingProcessFolderPath` | `string` | Folder zawierający proces (plik obrazu), który zainicjował zdarzenie |
| `InitiatingProcessFileName` | `string` | Nazwa procesu, który zainicjował zdarzenie |
| `InitiatingProcessFileSize` | `long` | Rozmiar procesu (pliku obrazu), który zainicjował zdarzenie |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Nazwa firmy z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoProductName` | `string` | Nazwa produktu z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
|` InitiatingProcessVersionInfoProductVersion` | `string` | Wersja produktu z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
|` InitiatingProcessVersionInfoInternalFileName` | `string` | Wewnętrzna nazwa pliku z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Oryginalna nazwa pliku z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Opis z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessId` | `int` | Identyfikator procesu (PID) procesu, który zainicjował zdarzenie |
| `InitiatingProcessCommandLine` | `string` | Wiersz polecenia użyty do uruchomienia procesu, który zainicjował zdarzenie |
| `InitiatingProcessCreationTime` | `datetime` | Data i godzina rozpoczęcia procesu, który zainicjował zdarzenie |
| `InitiatingProcessIntegrityLevel` | `string` | Poziom integralności procesu, który zainicjował zdarzenie. Windows przypisać poziomy integralności do procesów na podstawie określonych cech, na przykład tych, które zostały uruchomione z poziomu pobierania z Internetu. Te poziomy integralności wpływają na uprawnienia do zasobów |
| `InitiatingProcessTokenElevation` | `string` | Typ tokenu wskazujący obecność lub brak podwyższenia uprawnień kontroli dostępu użytkownika zastosowanego do procesu, który zainicjował zdarzenie |
| `InitiatingProcessParentId` | `int` | Identyfikator procesu (PID) procesu nadrzędnego, który obsługiował proces odpowiedzialny za zdarzenie |
| `InitiatingProcessParentFileName` | `string` | Nazwa procesu nadrzędnego, który obsługiował proces odpowiedzialny za zdarzenie |
| `InitiatingProcessParentCreationTime` | `datetime` | Data i godzina rozpoczęcia procesu odpowiedzialnego za zdarzenie jako element nadrzędny |
| `RequestProtocol` | `string` | Protokół sieciowy, jeśli ma zastosowanie, używany do inicjowania działania: Nieznany, Lokalny, SMB lub NFS |
| `RequestSourceIP` | `string` | Adres IPv4 lub IPv6 urządzenia zdalnego, które zainicjowało działanie |
| `RequestSourcePort` | `string` | Port źródłowy na urządzeniu zdalnym, które zainicjowało działanie |
| `RequestAccountName` | `string` | Nazwa użytkownika konta używanego do zdalnego inicjowania działania |
| `RequestAccountDomain` | `string` | Domena konta używanego do zdalnego inicjowania działania |
| `RequestAccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta używanego do zdalnego inicjowania działania |
| `ShareName` | `string` | Nazwa folderu udostępnionego zawierającego plik |
| `InitiatingProcessFileSize` | `long` | Rozmiar pliku, w przypadku których uruchomiono proces odpowiedzialny za zdarzenie |
| `SensitivityLabel` | `string` | Etykieta zastosowana do wiadomości e-mail, pliku lub innej zawartości w celu jej klasyfikowania w celu ochrony informacji |
| `SensitivitySubLabel` | `string` | Etykieta podrzędna zastosowana do wiadomości e-mail, pliku lub innej zawartości w celu jej klasyfikowania w celu ochrony informacji; Etykiety wrażliwości są grupowane pod etykietami wrażliwości, ale są traktowane niezależnie |
| `IsAzureInfoProtectionApplied` | `boolean` | Wskazuje, czy plik jest zaszyfrowany przez usługę Azure Information Protection. |
| `ReportId` | `long` | Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny w połączeniu z kolumnami DeviceName i Timestamp. |
| `AppGuardContainerId` | `string` | Identyfikator zwirtualizowanego kontenera używanego przez application Guard do odizolowanie aktywności przeglądarki |
| `AdditionalFields` | `string` | Dodatkowe informacje o encji lub zdarzeniu |
>[!NOTE]
> Informacje o skrótach plików będą zawsze wyświetlane, gdy będą dostępne. Istnieje jednak kilka możliwych powodów, dla których nie można obliczyć wartości SHA1, SHA256 lub MD5. Na przykład plik może być zlokalizowany w magazynie zdalnym, zablokowany przez inny proces, skompresowany lub oznaczony jako wirtualny. W takich scenariuszach informacje z skrótów plików są puste.

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
