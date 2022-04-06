---
title: Tabela CloudAppEvents w zaawansowanym schemacie wyszukiwania zagrożeń
description: Informacje o zdarzeniach z aplikacji i usług w chmurze w tabeli CloudAppEvents zaawansowanego schematu wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, odwołanie do schematu, kusto, tabela, kolumna, typ danych, opis, CloudAppEvents, Defender dla Chmury Apps
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 77b4ebd42a8c105340d6d965380aa42b64ae6734
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664969"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Tabela `CloudAppEvents` w zaawansowanym schemacie [wyszukiwania zagrożeń](advanced-hunting-overview.md) zawiera informacje o działaniach w różnych aplikacjach i usługach w chmurze objętych Microsoft Defender for Cloud Apps. Aby uzyskać pełną listę, przejdź do [pozycji Aplikacje i usługi.](#apps-and-services-covered) To odwołanie służy do konstruowania zapytań, które zwracają informacje z tej tabeli.

> [!IMPORTANT]
> Ta tabela zawiera informacje, które były dostępne w `AppFileEvents` tabeli. Od 7 marca 2021 r. użytkownicy polujący na działania związane z plikami w usługach w chmurze i poza tą datą `CloudAppEvents` powinni zamiast tego używać tabeli. <br><br>Pamiętaj, aby wyszukać zapytania i niestandardowe reguły wykrywania, które nadal używają `AppFileEvents` tabeli, i edytować je w `CloudAppEvents` celu korzystania z tabeli. Więcej wskazówek dotyczących konwertowania zapytań, których dotyczy problem, można znaleźć w artykule [Hunt across cloud app activities with Microsoft 365 Defender advanced hunting (Wyszukiwanie w działaniach aplikacji w chmurze z Microsoft 365 Defender zaawansowanym wyszukiwaniem zagrożeń](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857)).

Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, [zobacz zaawansowane informacje dotyczące wyszukiwania zagrożeń](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina zarejestrowania zdarzenia |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie |
| `Application` | `string` | Aplikacja, która wykonała zarejestrowaną akcję |
| `ApplicationId` | `string` | Unikatowy identyfikator aplikacji |
| `AccountObjectId` | `string` | Unikatowy identyfikator konta w Azure Active Directory |
| `AccountId` | `string` | Identyfikator konta znaleziony przez Microsoft Defender for Cloud Apps. Może to być Azure Active Directory identyfikator, główna nazwa użytkownika lub inne identyfikatory. |
| `AccountDisplayName` | `string` | Nazwa użytkownika konta wyświetlanego w książce adresowej. Zazwyczaj jest to kombinacja danego lub imienia, inicjacji środkowej oraz nazwiska lub nazwiska. |
| `IsAdminOperation` | `string` | Wskazuje, czy działanie zostało wykonane przez administratora |
| `DeviceType` | `string` | Typ urządzenia w oparciu o przeznaczenie i funkcje, takie jak "Urządzenie sieciowe", "Stacja robocza", "Serwer", "Mobile", "Konsola do gier" lub "Drukarka" |
| `OSPlatform` | `string` | Platforma systemu operacyjnego działającego na urządzeniu. Ta kolumna wskazuje określone systemy operacyjne, w tym odmiany w tej samej rodzinie, takie jak Windows 11, Windows 10 i Windows 7. |
| `IPAddress` | `string` | Adres IP przypisany do punktu końcowego i używany podczas powiązanej komunikacji sieciowej |
| `IsAnonymousProxy` | `string` | Wskazuje, czy adres IP należy do znanego anonimowego serwera proxy |
| `CountryCode` | `string` | Dwuliterowy kod wskazujący kraj, w którym adres IP klienta jest geolokalizowany |
| `City` | `string` | Miasto, w którym adres IP klienta jest geolokalizowany |
| `Isp` | `string` | Dostawca usług internetowych (ISP) skojarzony z adresem IP |
| `UserAgent` | `string` | Informacje o agentze użytkownika z przeglądarki internetowej lub innej aplikacji klienckiej |
| `ActivityType` | `string` | Typ działania, które wyzwoliło zdarzenie |
| `ActivityObjects` | `dynamic` | Lista obiektów, takich jak pliki lub foldery, które brały udział w zapisanym działaniu |
| `ObjectName` | `string` | Nazwa obiektu, do którego została zastosowana zarejestrowana akcja |
| `ObjectType` | `string` | Typ obiektu, taki jak plik lub folder, do których została zastosowana zarejestrowana akcja |
| `ObjectId` | `string` | Unikatowy identyfikator obiektu, do który została zastosowana zarejestrowana akcja |
| `ReportId` | `string` | Unikatowy identyfikator zdarzenia |
| `RawEventData` | `string` | Nieprzetworzone informacje o zdarzeniu z aplikacji źródłowej lub usługi w formacie JSON |
| `AdditionalFields` | `dynamic` | Dodatkowe informacje o jednostce lub zdarzeniu |
| `AccountType` | `string` | Typ konta użytkownika, wskazujący jego ogólną rolę i poziomy dostępu, takie jak Regular, System, Admin, DcAdmin, System, Application |
| `IsExternalUser` | `boolean` | Wskazuje, czy użytkownik w sieci nie należy do domeny organizacji |
| `IsImpersonated` | `boolean` | Wskazuje, czy działanie zostało wykonane przez jednego użytkownika dla innego (personifikowanego) użytkownika |
| `IPTags` | `dynamic` | Informacje zdefiniowane przez klienta stosowane do określonych adresów IP i zakresów adresów IP |
| `IPCategory` | `string` | Dodatkowe informacje o adresie IP |
| `UserAgentTags` | `dynamic` | Więcej informacji dostarczonych przez Microsoft Defender for Cloud Apps w tagu w polu agenta użytkownika. Może mieć dowolną z następujących wartości: Klient natywny, Nieaktualna przeglądarka, Nieaktualny system operacyjny, Robot |

## <a name="apps-and-services-covered"></a>Aplikacje i usługi objęte

- Dropbox
- Dynamics 365
- Exchange Online
- Microsoft Teams
- OneDrive dla Firm
- Power Automate
- Power BI
- SharePoint Online
- Skype dla firm
- Usługa Office 365
- Yammer

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
