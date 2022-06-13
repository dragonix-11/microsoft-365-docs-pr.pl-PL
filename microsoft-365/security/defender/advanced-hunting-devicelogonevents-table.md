---
title: Tabela DeviceLogonEvents w zaawansowanym schemacie wyszukiwania zagrożeń
description: Dowiedz się więcej o zdarzeniach uwierzytelniania lub logowania w tabeli DeviceLogonEvents zaawansowanego schematu wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, odwołanie do schematu, kusto, tabela, kolumna, typ danych, opis, logonevents, DeviceLogonEvents, uwierzytelnianie, logowanie, logowanie
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
ms.openlocfilehash: ec3002a30e9b5f20636a272574dcc3d6d00e4389
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044415"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender



Tabela `DeviceLogonEvents` w zaawansowanym schemacie [wyszukiwania zagrożeń](advanced-hunting-overview.md) zawiera informacje o logowaniach użytkowników i innych zdarzeniach uwierzytelniania na urządzeniach. To odwołanie służy do konstruowania zapytań, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType`wartości) obsługiwanych przez tabelę, użyj wbudowanego odwołania do schematu dostępnego w Defender dla Chmury.

Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, [zobacz zaawansowane informacje dotyczące wyszukiwania zagrożeń](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina zarejestrowania zdarzenia |
| `DeviceId` | `string` | Unikatowy identyfikator maszyny w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) maszyny |
| `ActionType` | `string` |Typ działania, które wyzwoliło zdarzenie |
| `LogonType` | `string` | Typ sesji logowania, w szczególności:<br><br> - **Interaktywne** — użytkownik fizycznie wchodzi w interakcje z maszyną przy użyciu lokalnej klawiatury i ekranu<br><br> - **Zdalne logowanie interakcyjne (RDP)** — użytkownik korzysta z maszyny zdalnie przy użyciu usług pulpitu zdalnego, usług terminalowych, pomocy zdalnej lub innych klientów RDP<br><br> - **Sieć** — sesja inicjowana, gdy dostęp do maszyny jest uzyskiwany przy użyciu programu PsExec lub gdy są dostępne udostępnione zasoby na komputerze, takie jak drukarki i foldery udostępnione<br><br> - **Batch** — sesja zainicjowana przez zaplanowane zadania<br><br> - **Usługa** — sesja zainicjowana przez usługi podczas ich uruchamiania<br> |
| `AccountDomain` | `string` | Domena konta |
| `AccountName` | `string` | Nazwa użytkownika konta |
| `AccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta |
| `Protocol` | `string` | Protokół używany podczas komunikacji |
| `FailureReason` | `string` | Informacje wyjaśniające, dlaczego zarejestrowana akcja nie powiodła się |
| `IsLocalAdmin` | `boolean` | Wskaźnik logiczny określający, czy użytkownik jest administratorem lokalnym na maszynie |
| `LogonId` | `string` | Identyfikator sesji logowania. Ten identyfikator jest unikatowy na tej samej maszynie tylko między ponownymi uruchomieniami |
| `RemoteDeviceName` | `string` | Nazwa maszyny, która wykonała zdalną operację na komputerze, którego dotyczy problem. W zależności od zgłoszonego zdarzenia ta nazwa może być w pełni kwalifikowaną nazwą domeny (FQDN), nazwą NetBIOS lub nazwą hosta bez informacji o domenie |
| `RemoteIP` | `string` | Adres IP urządzenia, z którego wykonano próbę logowania |
| `RemoteIPType` | `string` | Typ adresu IP, na przykład Publiczny, Prywatny, Zarezerwowany, Loopback, Teredo, FourToSixMapping i Broadcast |
| `RemotePort` | `int` | Port TCP na urządzeniu zdalnym, z |
| `InitiatingProcessAccountDomain` | `string` | Domena konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountName` | `string` | Nazwa użytkownika konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessAccountUpn` | `string` | Główna nazwa użytkownika (UPN) konta, które uruchomiło proces odpowiedzialny za zdarzenie |
| ` InitiatingProcessAccountObjectId` | `string` | Azure AD identyfikatora obiektu konta użytkownika, które uruchomiło proces odpowiedzialny za zdarzenie |
| `InitiatingProcessIntegrityLevel` | `string` | Poziom integralności procesu, który zainicjował zdarzenie. Windows przypisuje poziomy integralności do procesów opartych na pewnych cechach, takich jak uruchamianie z pobierania z Internetu. Te poziomy integralności wpływają na uprawnienia do zasobów |
| `InitiatingProcessTokenElevation` | `string` | Typ tokenu wskazujący obecność lub brak podniesienia uprawnień użytkownika Access Control (UAC) zastosowaną do procesu, który zainicjował zdarzenie |
| `InitiatingProcessSHA1` | `string` | SHA-1 procesu (pliku obrazu), który zainicjował zdarzenie |
| `InitiatingProcessSHA256` | `string` | SHA-256 procesu (plik obrazu), który zainicjował zdarzenie. To pole zwykle nie jest wypełnione — użyj kolumny SHA1, jeśli jest dostępne |
| `InitiatingProcessMD5` | `string` | Skrót MD5 procesu (pliku obrazu), który zainicjował zdarzenie |
| `InitiatingProcessFileName` | `string` | Nazwa procesu, który zainicjował zdarzenie |
| `InitiatingProcessFileSize` | `long` | Rozmiar pliku, który uruchomił proces odpowiedzialny za zdarzenie |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Nazwa firmy z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoProductName` | `string` | Nazwa produktu z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Wersja produktu z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | Wewnętrzna nazwa pliku z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Oryginalna nazwa pliku z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Opis z informacji o wersji procesu (pliku obrazu) odpowiedzialnego za zdarzenie |
| `InitiatingProcessId` | `int` | Identyfikator procesu (PID) procesu, który zainicjował zdarzenie |
| `InitiatingProcessCommandLine` | `string` | Wiersz polecenia używany do uruchamiania procesu, który zainicjował zdarzenie |
| `InitiatingProcessCreationTime` | `datetime` | Data i godzina rozpoczęcia procesu, który zainicjował zdarzenie |
| `InitiatingProcessFolderPath` | `string` | Folder zawierający proces (plik obrazu), który zainicjował zdarzenie |
| `InitiatingProcessParentId` | `int` | Identyfikator procesu (PID) procesu nadrzędnego, który zduplikował proces odpowiedzialny za zdarzenie |
| `InitiatingProcessParentFileName` | `string` | Nazwa procesu nadrzędnego, który zduplikował proces odpowiedzialny za zdarzenie |
| `InitiatingProcessParentCreationTime` | `datetime` | Data i godzina rozpoczęcia nadrzędnego procesu odpowiedzialnego za zdarzenie |
| `ReportId` | `long` | Identyfikator zdarzenia na podstawie licznika powtarzającego się. Aby zidentyfikować unikatowe zdarzenia, ta kolumna musi być używana w połączeniu z kolumnami DeviceName i Timestamp |
| `AppGuardContainerId` | `string` | Identyfikator zwirtualizowanego kontenera używanego przez usługę Application Guard do izolowania działania przeglądarki |
| `AdditionalFields` | `string` | Dodatkowe informacje o zdarzeniu w formacie tablicy JSON |

>[!NOTE]
>Kolekcja devicelogonEvents nie jest obsługiwana na urządzeniach Windows 7 lub Windows Server 2008R2 dołączonych do usługi Defender for Endpoint. Zalecamy uaktualnienie do nowszego systemu operacyjnego w celu uzyskania optymalnego wglądu w działania logowania użytkowników.

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
