---
title: Tabela DeviceLogonEvents w zaawansowanym schemacie wyszukiwania
description: Informacje na temat uwierzytelniania lub zdarzeń logowania w tabeli DeviceLogonEvents zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, chwała przed zagrożeniami, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, zdarzenia logowania, DeviceLogonEvents, uwierzytelnianie, logowanie, logowanie
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
ms.openlocfilehash: dbafb4c967bca09195277aa4c79c95dd1dc87afb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017875"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender



Tabela `DeviceLogonEvents` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje o logowaniach użytkowników i innych zdarzeniach uwierzytelniania na urządzeniach. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType` wartości) obsługiwanych w tabeli, użyj wbudowanego schematu referencyjnego dostępnego w usłudze Defender dla chmury.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `DeviceId` | `string` | Unikatowy identyfikator komputera w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `ActionType` | `string` |Typ działania, które wyzwoliło zdarzenie |
| `LogonType` | `string` | Typ sesji logowania, zwłaszcza:<br><br> -  Interakcyjnie — fizyczny interakcja użytkownika z urządzeniem przy użyciu lokalnej klawiatury i ekranu<br><br> - **Zdalne interakcyjne logowania (RDP)** — użytkownik wchodzi w interakcję z komputerem zdalnie przy użyciu pulpitu zdalnego, usług terminalowych, pomocy zdalnej lub innych klientów RDP<br><br> - **Sieć** — sesja inicjowana, gdy komputer uzyskuje dostęp przy użyciu programu PsExec lub gdy są dostępne zasoby udostępnione na komputerze, takie jak drukarki i foldery udostępnione,<br><br> - **Partia —** sesja zainicjowana przez zaplanowane zadania<br><br> - **Usługa** — sesja inicjowana przez usługi w trakcie ich rozpoczynania<br> |
| `AccountDomain` | `string` | Domena konta |
| `AccountName` | `string` | Nazwa użytkownika konta |
| `AccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta |
| `Protocol` | `string` | Protokół używany podczas komunikacji |
| `FailureReason` | `string` | Informacje wyjaśniające przyczynę niepowodzenie zarejestrowanej akcji |
| `IsLocalAdmin` | `boolean` | Logiczny wskaźnik tego, czy użytkownik jest administratorem lokalnym na komputerze |
| `LogonId` | `string` | Identyfikator sesji logowania. Ten identyfikator jest unikatowy na tym samym komputerze tylko między ponownym uruchomieniem |
| `RemoteDeviceName` | `string` | Nazwa komputera, na którego komputerze została wykonana operacja zdalna. W zależności od zgłoszonego zdarzenia może to być w pełni kwalifikowana nazwa domeny (FQDN), nazwa systemu NetBIOS lub nazwa hosta bez informacji o domenie. |
| `RemoteIP` | `string` | Adres IP, z który był połączony |
| `RemoteIPType` | `string` | Typ adresu IP, na przykład Publiczny, Prywatny, Zastrzeżony, Loopback, Teredo, FourToSixMapping i Emisja |
| `RemotePort` | `int` | Port TCP na urządzeniu zdalnym, z które było połączone |
| `InitiatingProcessAccountDomain` | `string` | Domena konta, na które uruchomiono proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountName` | `string` | Nazwa użytkownika konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| ` InitiatingProcessAccountObjectId` | `string` | Identyfikator obiektu usługi Azure AD konta użytkownika, który uruchomił proces odpowiedzialny za zdarzenie |
| `InitiatingProcessIntegrityLevel` | `string` | Poziom integralności procesu, który zainicjował zdarzenie. Windows przypisać poziomy integralności do procesów na podstawie określonych cech, na przykład tych, które zostały uruchomione z poziomu pobierania z Internetu. Te poziomy integralności wpływają na uprawnienia do zasobów |
| `InitiatingProcessTokenElevation` | `string` | Typ tokenu wskazujący obecność lub brak podwyższenia uprawnień kontroli dostępu użytkownika zastosowanego do procesu, który zainicjował zdarzenie |
| `InitiatingProcessSHA1` | `string` | SHA-1 procesu (pliku obrazu), który zainicjował zdarzenie |
| `InitiatingProcessSHA256` | `string` | SHA-256 procesu (pliku obrazu), który zainicjował zdarzenie. To pole zwykle nie jest wypełnione — jeśli jest dostępne, użyj kolumny SHA1 |
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
