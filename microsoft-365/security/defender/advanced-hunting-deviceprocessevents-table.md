---
title: Tabela DeviceProcessEvents w zaawansowanym schemacie wyszukiwania
description: Informacje na temat procesu przetwarzania lub tworzenia zdarzeń w tabeli DeviceProcessEventstable zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, procescreationevents, DeviceProcessEvents, identyfikator procesu, wiersz polecenia, DeviceProcessEvents
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
ms.openlocfilehash: 9bd0b658141395ac09d530dfecfa29befa892fcc
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017907"
---
# <a name="deviceprocessevents"></a>DeviceProcessEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender



Tabela `DeviceProcessEvents` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje na temat tworzenia procesów i pokrewnych wydarzeń. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType` wartości) obsługiwanych w tabeli, użyj wbudowanego schematu referencyjnego dostępnego w usłudze Defender dla chmury.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `DeviceId` | `string` | Unikatowy identyfikator komputera w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie. Aby uzyskać [szczegółowe informacje, zobacz informacje](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) dotyczące schematu w portalu |
| `FileName` | `string` | Nazwa pliku, do których zastosowano akcję |
| `FolderPath` | `string` | Folder zawierający plik, do którym zastosowano akcję |
| `SHA1` | `string` | SHA-1 pliku, do których zastosowano akcję |
| `SHA256` | `string` | SHA-256 pliku, do których zastosowano akcję. To pole zwykle nie jest wypełnione — jeśli jest dostępne, użyj kolumny SHA1. |
| `MD5` | `string` | Skrót MD5 pliku, do których zastosowano akcję |
| `FileSize` | `long` | Rozmiar pliku (w bajtach) |
| `ProcessVersionInfoCompanyName` | `string` | Nazwa firmy z informacji o wersji nowo utworzonego procesu |
| `ProcessVersionInfoProductName` | `string` | Nazwa produktu z informacji o wersji nowo utworzonego procesu |
| `ProcessVersionInfoProductVersion` | `string` | Wersja produktu z informacji o wersji nowo utworzonego procesu |
| `ProcessVersionInfoInternalFileName` | `string` | Wewnętrzna nazwa pliku z informacji o wersji nowo utworzonego procesu |
| `ProcessVersionInfoOriginalFileName` | `string` | Oryginalna nazwa pliku z informacji o wersji nowo utworzonego procesu |
| `ProcessVersionInfoFileDescription` | `string` | Opis z informacji o wersji nowo utworzonego procesu |
| `ProcessId` | `int` | Identyfikator procesu (PID) nowo utworzonego procesu |
| `ProcessCommandLine` | `string` | Wiersz polecenia użyty do utworzenia nowego procesu |
| `ProcessIntegrityLevel` | `string` | Poziom integralności nowo utworzonego procesu. Windows przypisać poziomy integralności do procesów na podstawie określonych cech, na przykład tych, które zostały uruchomione z pobranego Internetu. Te poziomy integralności wpływają na uprawnienia do zasobów |
| `ProcessTokenElevation` | `string` | Wskazuje typ podwyższenia tokenu zastosowany do nowo utworzonego procesu. Możliwe wartości: TokenElevationTypeLimited (restricted), TokenElevationTypeDefault (standard) oraz TokenElevationTypeFull (podwyższony poziom) |
| `ProcessCreationTime` | `datetime` | Data i godzina utworzenia procesu |
| `AccountDomain` | `string` | Domena konta |
| `AccountName` | `string` | Nazwa użytkownika konta |
| `AccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta |
| `AccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta |
| `AccountObjectId` | `string` | Unikatowy identyfikator konta w usłudze Azure AD |
| `LogonId` | `string` | Identyfikator sesji logowania. Ten identyfikator jest unikatowy na tym samym komputerze tylko między ponownym uruchomieniem |
| `InitiatingProcessAccountDomain` | `string` | Domena konta, na które uruchomiono proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountName` | `string` | Nazwa użytkownika konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountObjectId` | `string` | Identyfikator obiektu usługi Azure AD konta użytkownika, który uruchomił proces odpowiedzialny za zdarzenie |
| `InitiatingProcessLogonId` | `string` | Identyfikator sesji logowania procesu, który zainicjował zdarzenie. Ten identyfikator jest unikatowy na tym samym komputerze tylko między ponownym uruchomieniem. |
| `InitiatingProcessIntegrityLevel` | `string` | Poziom integralności procesu, który zainicjował zdarzenie. Windows przypisać poziomy integralności do procesów na podstawie określonych cech, na przykład tych, które zostały uruchomione z poziomu pobierania z Internetu. Te poziomy integralności wpływają na uprawnienia do zasobów |
| `InitiatingProcessTokenElevation` | `string` | Typ tokenu wskazujący obecność lub brak podwyższenia uprawnień kontroli dostępu użytkownika zastosowanego do procesu, który zainicjował zdarzenie |
| `InitiatingProcessSHA1` | `string` | SHA-1 procesu (pliku obrazu), który zainicjował zdarzenie |
| `InitiatingProcessSHA256` | `string` | SHA-256 procesu (pliku obrazu), który zainicjował zdarzenie. To pole zwykle nie jest wypełnione — jeśli jest dostępne, użyj kolumny SHA1. |
| `InitiatingProcessMD5` | `string` | Skrót MD5 procesu (pliku obrazu), który zainicjował zdarzenie |
| `InitiatingProcessFileName` | `string` | Nazwa procesu, który zainicjował zdarzenie |
| `InitiatingProcessFileSize` | `long` | Rozmiar pliku, w przypadku których uruchomiono proces odpowiedzialny za zdarzenie |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Nazwa firmy z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoProductName` | `string` | Nazwa produktu z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Wersja produktu z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | Wewnętrzna nazwa pliku z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Oryginalna nazwa pliku z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Opis z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessId` | `int` | Identyfikator procesu (PID) procesu, który zainicjował zdarzenie |
| `InitiatingProcessCommandLine` | `string` | Wiersz polecenia użyty do uruchomienia procesu, który zainicjował zdarzenie |
| `InitiatingProcessCreationTime` | `datetime` | Data i godzina rozpoczęcia procesu, który zainicjował zdarzenie |
| `InitiatingProcessFolderPath` | `string` | Folder zawierający proces (plik obrazu), który zainicjował zdarzenie |
| `InitiatingProcessParentId` | `int` | Identyfikator procesu (PID) procesu nadrzędnego, który obsługiował proces odpowiedzialny za zdarzenie |
| `InitiatingProcessParentFileName` | `string` | Nazwa procesu nadrzędnego, który obsługiował proces odpowiedzialny za zdarzenie |
| `InitiatingProcessParentCreationTime` | `datetime` | Data i godzina rozpoczęcia procesu odpowiedzialnego za zdarzenie jako element nadrzędny |
| `InitiatingProcessSignerType` | `string` | Typ pliku podpiszcego proces (plik obrazu), który zainicjował zdarzenie |
| `InitiatingProcessSignatureStatus` | `string` | Informacje o stanie podpisu procesu (pliku obrazu), który zainicjował zdarzenie |
| `ReportId` | `long` | Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny w połączeniu z kolumnami DeviceName i Timestamp |
| `AppGuardContainerId` | `string` | Identyfikator zwirtualizowanego kontenera używanego przez application Guard do odizolowanie aktywności przeglądarki |
| `AdditionalFields` | `string` | Dodatkowe informacje o zdarzeniu w formacie tablicowym JSON |


## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
