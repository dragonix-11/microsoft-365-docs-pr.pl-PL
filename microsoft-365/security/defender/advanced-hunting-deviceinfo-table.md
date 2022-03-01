---
title: Tabela DeviceInfo w zaawansowanym schemacie chłoń
description: Informacje o systemach operacyjnych, nazwach komputerów i innych informacjach o komputerze są zawarte w tabeli DeviceInfo zaawansowanego schematu wyszukiwania
keywords: zaawansowane wyszukiwania, chłonianie pod zagrożeniami, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, machineinfo, DeviceInfo, urządzenie, komputer, system operacyjny, platforma, użytkownicy
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
ms.openlocfilehash: 245a9aa11bcaf10ba6f3b8fe0fe429267a355560
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033730"
---
# <a name="deviceinfo"></a>DeviceInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Tabela `DeviceInfo` w zaawansowanym [schemacie chłoń](advanced-hunting-overview.md) zawiera informacje o urządzeniach w organizacji, w tym o wersji systemu operacyjnego, aktywnych użytkownikach i nazwie komputera. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `DeviceId` | `string` | Unikatowy identyfikator komputera w usłudze |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) komputera |
| `ClientVersion` | `string` | Wersja agenta punktu końcowego lub czujnika działającego na komputerze |
| `PublicIP` | `string` | Publiczny adres IP używany przez komputer dołączany do łączenia się z usługą programu Microsoft Defender for Endpoint. Może to być adres IP komputera, urządzenia NAT lub serwera proxy. |
| `OSArchitecture` | `string` | Architektura systemu operacyjnego działającego na komputerze |
| `OSPlatform` | `string` | Platforma systemu operacyjnego działającego na komputerze. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 11, Windows 10 i Windows 7. |
| `OSBuild` | `string` | Kompilacja systemu operacyjnego działającego na komputerze |
| `IsAzureADJoined` | `boolean` | Logiczny wskaźnik tego, czy komputer jest przyłączony do Azure Active Directory |
| `AadDeviceId` | `string` | Unikatowy identyfikator urządzenia w usłudze Azure AD |
| `LoggedOnUsers` | `string` | Lista wszystkich użytkowników, którzy są zalogowani na komputerze w czasie zdarzenia w formacie tablicy JSON |
| `RegistryDeviceTag` | `string` | Tag maszynowy dodany za pośrednictwem rejestru |
| `OSVersion` | `string` | Wersja systemu operacyjnego działającego na komputerze |
| `MachineGroup` | `string` | Grupa maszynowa komputera. Ta grupa jest używana przez opartą na rolach kontrolę dostępu do określenia dostępu do komputera |
| `ReportId` | `long` | Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny w połączeniu z kolumnami DeviceName i Timestamp |
| `OnboardingStatus` | `string` | Wskazuje, czy urządzenie jest obecnie wnoszone do programu Microsoft Defender for Endpoint, czy też nie jest obsługiwane. |
|`AdditionalFields` | `string` | Dodatkowe informacje o zdarzeniu w formacie tablicowym JSON |
|`DeviceCategory` | `string` | Szersza klasyfikacja grupuje określone typy urządzeń w następujących kategoriach: Punkt końcowy, Urządzenie sieciowe, IoT, Nieznany |
|`DeviceType` | `string` | Typ urządzenia zależnie od przeznaczenia i funkcji, takich jak urządzenie sieciowe, stacja robocza, serwer, urządzenie przenośne, konsola do gier lub drukarka |
|`DeviceSubType` | `string` | Dodatkowy modyfikator dla określonych typów urządzeń, na przykład urządzenie przenośne może być tabletem lub smartfonem. Dostępne tylko w przypadku, gdy funkcja odnajdowania urządzeń znajdzie wystarczającą ilość informacji o tym atrybutzie |
|`Model` | `string` | Nazwa modelu lub numer produktu od dostawcy lub producenta, dostępne tylko w przypadku, gdy odnajdowanie urządzeń znajdzie wystarczającą ilość informacji na temat tego atrybutu |
|`Vendor` | `string` | Nazwa producenta lub dostawcy produktu dostępna tylko wtedy, gdy funkcja odnajdowania urządzeń znajdzie wystarczającą ilość informacji na temat tego atrybutu |
|`OSDistribution` | `string` | Rozpowszechnianie platformy systemu operacyjnego, takiej jak Ubuntu lub RedHat dla platform systemu Linux |
|`OSVersionInfo` | `string` | Dodatkowe informacje o wersji systemu operacyjnego, takie jak nazwa popularnego systemu operacyjnego, nazwa kodu lub numer wersji |
|`MergedDeviceIds` | `string` | Identyfikatory poprzednich urządzeń, które zostały przypisane do tego samego urządzenia |
|`MergedToDeviceId` | `string` | Najnowszy identyfikator urządzenia przypisany do urządzenia |

Ta `DeviceInfo` tabela zawiera informacje o urządzeniu na podstawie pulsów, które są okresowymi raportami lub sygnałami od urządzenia. Co piętnaście minut urządzenie wysyła część pulsu zawierającą często zmieniane atrybuty, takie jak `LoggedOnUsers`. Raz dziennie jest wysyłane pełne puls zawierające atrybuty urządzenia.

Aby pobrać najnowszy stan urządzenia, możesz użyć następującego przykładowego zapytania:

```kusto
// Get latest information on user/device
DeviceInfo
| where DeviceName == "example" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId 
```

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
