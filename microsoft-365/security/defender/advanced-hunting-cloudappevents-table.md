---
title: Tabela CloudAppEvents w zaawansowanym schemacie wyszukiwania
description: Informacje o wydarzeniach z aplikacji i usług w chmurze w tabeli CloudAppEvents zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, CloudAppEvents, Defender for Cloud Apps
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
ms.openlocfilehash: daed3fb87aab498cdf91247a59e48af685aed010
ms.sourcegitcommit: 27eb93a7d46bcbb9c948a50b0a8481ffd3832ca0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/28/2021
ms.locfileid: "63018981"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender



Tabela `CloudAppEvents` w zaawansowanym [schemacie chłonia](advanced-hunting-overview.md) zawiera informacje o działaniach w różnych aplikacjach i usługach w chmurze objętych programem Microsoft Defender for Cloud Apps. Aby uzyskać pełną listę, przejdź do [listy Aplikacje i usługi objęte usługami](#apps-and-services-covered). To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli. 

>[!IMPORTANT]
>Ta tabela zawiera informacje, które używane w tabeli są `AppFileEvents` dostępne. Począwszy od 7 marca 2021 r., `CloudAppEvents` użytkownicy muszą zamiast tego korzystać z tabeli przez działania związane z plikami w usługach w chmurze i później. <br><br>Pamiętaj o wyszukiwaniu zapytań i niestandardowych reguł wykrywania, które `AppFileEvents` nadal używają tabeli, i edytowaniu ich w celu używania `CloudAppEvents` tabeli. Więcej wskazówek dotyczących konwertowania zapytań, których dotyczy problem, można znaleźć w tece Wyszukiwanie w aplikacjach w chmurze z Microsoft 365 Defender [wyszukiwania zaawansowanego](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857).


Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie |
| `Application` | `string` | Aplikacja, która wykonała nagraną akcję |
| `ApplicationId` | `string` | Unikatowy identyfikator aplikacji |
| `AccountObjectId` | `string` | Unikatowy identyfikator konta w aplikacji Azure Active Directory |
| `AccountId` | `string` | Identyfikator konta znaleziony przez program Microsoft Defender dla aplikacji w chmurze. Może to Azure Active Directory identyfikator, główna nazwa użytkownika lub inne identyfikatory. |
| `AccountDisplayName` | `string` | Nazwa użytkownika konta wyświetlana w książce adresowej. Zwykle jest to połączenie danego lub imienia, inicjacji średniej i nazwiska lub nazwiska. |
| `IsAdminOperation` | `string` | Wskazuje, czy działanie zostało wykonane przez administratora. |
| `DeviceType` | `string` | Typ urządzenia zależnie od przeznaczenia i funkcji, na przykład "Urządzenie sieciowe", "Stacja robocza", "Serwer", "Urządzenie przenośne", "Konsola do gier" lub "Drukarka" | 
| `OSPlatform` | `string` | Platforma systemu operacyjnego działającego na urządzeniu. Ta kolumna zawiera informacje o konkretnych systemach operacyjnych, łącznie z odmianami tej samej rodziny, takimi jak wersje Windows 11, Windows 10 i Windows 7. |
| `IPAddress` | `string` | Adres IP przypisany do punktu końcowego i używany podczas powiązanej komunikacji sieciowej |
| `IsAnonymousProxy` | `string` | Wskazuje, czy adres IP należy do znanego anonimowego serwera proxy. |
| `CountryCode` | `string` | Dwuliterowy kod wskazujący kraj, do którego został geolokalizacji adresu IP klienta |
| `City` | `string` | Miasto, w którym jest geolokalizacji adresu IP klienta |
| `Isp` | `string` | Internet usługodawca(ISP) skojarzony z adresem IP |
| `UserAgent` | `string` | Informacje dotyczące agenta użytkownika z przeglądarki sieci Web lub innej aplikacji klienckiej |
| `ActivityType` | `string` | Typ działania, które wyzwoliło zdarzenie |
| `ActivityObjects` | `dynamic` | Lista obiektów, takich jak pliki lub foldery, które uczestniczyły w zarejestrowanym działaniu |
| `ObjectName` | `string` | Nazwa obiektu, do których zastosowano akcję |
| `ObjectType` | `string` | Typ obiektu, na przykład pliku lub folderu, do których zastosowano akcję Nagrywania |
| `ObjectId` | `string` | Unikatowy identyfikator obiektu, do których zastosowano akcję |
| `ReportId` | `string` | Unikatowy identyfikator zdarzenia |
| `RawEventData` | `string` | Nieprzetworzone informacje o zdarzeniu z aplikacji źródłowej lub usługi w formacie JSON |
| `AdditionalFields` | `dynamic` | Dodatkowe informacje o encji lub zdarzeniu |
| `AccountType` | `string` | Typ konta użytkownika, wskazujący jego ogólną rolę i poziomy dostępu, takie jak Zwykły, System, Administrator, DcAdmin, System, Aplikacja | 
| `IsExternalUser` | `boolean` | Wskazuje, czy użytkownik w sieci nie należy do domeny organizacji. | 
| `IsImpersonated` | `boolean` | Wskazuje, czy działanie zostało wykonane przez jednego użytkownika dla innego (personifikowane) użytkownika. | 
| `IPTags` | `dynamic` | Informacje zdefiniowane przez klienta stosowane do określonych adresów IP i zakresów adresów IP | 
| `IPCategory` | `string` | Dodatkowe informacje o adresie IP | 
| `UserAgentTags` | `dynamic` | Więcej informacji na temat programu Microsoft Defender dla aplikacji w chmurze w tagu w polu agenta użytkownika. Może mieć dowolną z następujących wartości: Natywny klient, Nieaktualna przeglądarka, Nieaktualny system operacyjny, Robot | 

## <a name="apps-and-services-covered"></a>Aplikacje i usługi objęte usługami

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
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
