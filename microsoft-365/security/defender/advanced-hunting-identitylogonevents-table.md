---
title: Tabela IdentityLogonEvents w zaawansowanym schemacie wyszukiwania
description: Informacje o zdarzeniach uwierzytelniania zarejestrowanych przez usługę Active Directory w tabeli IdentityLogonEvents zaawansowanego schematu wyszukiwania
keywords: zaawansowane łowiectwo, chwała przed zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, IdentityLogonEvents, Azure AD, Active Directory, Microsoft Defender for Identity, tożsamości
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
ms.openlocfilehash: c5f8de4015ed8b031d3f228f29a6a0d63a57bf2a
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017912"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Tabela w zaawansowanym schemacie chwycenia zawiera informacje o działaniach uwierzytelniania wykonanych za pośrednictwem lokalnej usługi Active Directory przechwytywanych przez usługę Microsoft Defender na temat tożsamości i działań uwierzytelniania związanych z usługami online firmy Microsoft przechwytywami przez usługę Microsoft Defender for Cloud Apps.[](advanced-hunting-overview.md) `IdentityLogonEvents` To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType` wartości) obsługiwanych w tabeli, użyj wbudowanego schematu referencyjnego dostępnego w usłudze Defender dla chmury.

>[!NOTE]
>W poniższej tabeli Azure Active Directory (Azure AD) aktywności logowania śledzone przez usługę Defender for Cloud Apps, a w szczególności interakcyjne logowania i działania uwierzytelniania przy użyciu protokołu ActiveSync i innych starszych protokołów. Nieakcyjne logowania, które nie są dostępne w tej tabeli, można wyświetlać w dzienniku inspekcji usługi Azure AD. [Dowiedz się więcej o łączeniu aplikacji Defender for Cloud z usługą Microsoft 365](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security)

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `ActionType` | `string` | Typ działania, które wyzwoliło zdarzenie. Aby uzyskać [szczegółowe informacje, zobacz informacje](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) dotyczące schematu w portalu |
| `Application` | `string` | Aplikacja, która wykonała nagraną akcję |
| `LogonType` | `string` | Typ sesji logowania, zwłaszcza:<br><br> -  Interakcyjnie — fizyczny interakcja użytkownika z urządzeniem przy użyciu lokalnej klawiatury i ekranu<br><br> - **Zdalne interakcyjne logowania (RDP)** — użytkownik wchodzi w interakcję z komputerem zdalnie przy użyciu pulpitu zdalnego, usług terminalowych, pomocy zdalnej lub innych klientów RDP<br><br> - **Sieć** — sesja inicjowana, gdy komputer uzyskuje dostęp przy użyciu programu PsExec lub gdy są dostępne zasoby udostępnione na komputerze, takie jak drukarki i foldery udostępnione,<br><br> - **Partia —** sesja zainicjowana przez zaplanowane zadania<br><br> - **Usługa** — sesja inicjowana przez usługi w trakcie ich rozpoczynania |
| `Protocol` | `string` | Używany protokół sieciowy |
| `FailureReason` | `string` | Informacje wyjaśniające przyczynę niepowodzenie zarejestrowanej akcji |
| `AccountName` | `string` | Nazwa użytkownika konta |
| `AccountDomain` | `string` | Domena konta |
| `AccountUpn` | `string` | Główna nazwa użytkownika (UPN) dla konta |
| `AccountSid` | `string` | Identyfikator zabezpieczeń (SID) konta |
| `AccountObjectId` | `string` | Unikatowy identyfikator konta w usłudze Azure AD |
| `AccountDisplayName` | `string` | Nazwa użytkownika konta wyświetlana w książce adresowej. Zwykle jest to połączenie danego lub imienia, inicjacji średniej i nazwiska lub nazwiska. |
| `DeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia |
| `DeviceType` | `string` | Typ urządzenia |
| `OSPlatform` | `string` | Platforma systemu operacyjnego działającego na komputerze. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 11, Windows 10 i Windows 7. |
| `IPAddress` | `string` | Adres IP przypisany do punktu końcowego i używany podczas powiązanej komunikacji sieciowej |
| `Port` | `string` | Port TCP używany podczas komunikacji |
| `DestinationDeviceName` | `string` | Nazwa urządzenia z uruchomionym aplikacją serwera, która przetworzona została nagrana akcja |
| `DestinationIPAddress` | `string` | Adres IP urządzenia z uruchomionym aplikacją serwera, która przetworzyła nagraną akcję |
| `DestinationPort` | `string` | Docelowy port pokrewnej komunikacji sieciowej |
| `TargetDeviceName` | `string` | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia, do których zastosowano zarejestrowane działanie |
| `TargetAccountDisplayName` | `string` | Nazwa wyświetlana konta, do których zastosowano akcję |
| `Location` | `string` | Miasto, kraj lub inna lokalizacja geograficzna skojarzona z wydarzeniem |
| `Isp` | `string` | Internet usługodawca (ISP) skojarzony z adresem IP punktu końcowego |
| `ReportId` | `long` | Unikatowy identyfikator zdarzenia |
| `AdditionalFields` | `string` | Dodatkowe informacje o encji lub zdarzeniu |

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
