---
title: Tabela AADSignInEventsBeta w zaawansowanym schemacie wyszukiwania
description: Poznaj tabelę Azure Active Directory wydarzeń dotyczących logowania, która zawiera zaawansowany schemat łowiectwo
keywords: zaawansowane szukanie, schłoń pod niebędący zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, plik, adres IP, urządzenie, komputer, użytkownik, konto, tożsamość, AAD
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
ms.openlocfilehash: dad3ea9fe4297d93864032130e3f6d6b5f6e4e82
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013287"
---
# <a name="aadsignineventsbeta"></a>AADSignInEventsBeta

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Tabela `AADSignInEventsBeta` jest obecnie w wersji beta i będzie oferowana wkrótce, aby umożliwić ci poszukanie zdarzeń logowania w wersji Azure Active Directory (AAD). Klienci muszą mieć licencję Azure Active Directory — wersja Premium P2, aby zbierać i wyświetlać działania dotyczące tej tabeli. Wszystkie informacje schematu logowania zostaną później przenieść do `IdentityLogonEvents` tabeli.

Tabela `AADSignInEventsBeta` w zaawansowanym schemacie chłoń zawiera informacje Azure Active Directory dotyczących interakcyjnych i nieinterakcyjnych logowań. Dowiedz się więcej o logowaniach w [Azure Active Directory aktywności logowania — podgląd](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

To odwołanie pozwala konstruować zapytania, które zwracają informacje z tabeli. Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zapoznaj się z [zaawansowanymi informacjami na temat wyszukiwania](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Nazwa kolumny|Typ danych|Opis|
|---|---|---|
|`Timestamp`|`datetime`|Data i godzina wygenerowania rekordu|
|`Application`|`string`|Aplikacja, która wykonała nagraną akcję|
|`ApplicationId`|`string`|Unikatowy identyfikator aplikacji|
|`LogonType`|`string`|Typ sesji logowania, interakcyjnej, interakcyjnej, zdalnej (RDP), sieci, partii i usługi|
|`ErrorCode`|`int`|Zawiera kod błędu, jeśli wystąpi błąd logowania. Aby znaleźć opis określonego kodu błędu, odwiedź stronę <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Unikatowy identyfikator zdarzenia logowania|
|`SessionId`|`string`|Unikatowy numer przypisany do użytkownika przez serwer witryny sieci Web podczas odwiedzin lub sesji|
|`AccountDisplayName`|`string`|Nazwa użytkownika konta wyświetlana w książce adresowej. Zwykle jest to połączenie imienia lub danego imienia, inicjała środkowego oraz nazwiska lub nazwiska.|
|`AccountObjectId`|`string`|Unikatowy identyfikator konta w usłudze Azure AD|
|`AccountUpn`|`string`|Główna nazwa użytkownika (UPN) dla konta|
|`IsExternalUser`|`int`|Wskazuje, czy zalogowany użytkownik jest zewnętrzny. Możliwe wartości: -1 (nie ustawiono), 0 (nie zewnętrzna), 1 (zewnętrzna).|
|`IsGuestUser`|`boolean`|Wskazuje, czy użytkownik, który się zalogował, jest gościem w dzierżawie.|
|`AlternateSignInName`|`string`|Lokalna główna nazwa użytkownika (UPN) użytkownika logującej się do usługi Azure AD|
|`LastPasswordChangeTimestamp`|`datetime`|Data i godzina ostatniej zmiany hasła przez użytkownika, który się zalogował|
|`ResourceDisplayName`|`string`|Nazwa wyświetlana zasobu, do którego uzyskano dostęp|
|`ResourceId`|`string`|Unikatowy identyfikator zasobu, do którego uzyskano dostęp|
|`ResourceTenantId`|`string`|Unikatowy identyfikator dzierżawy zasobu, do którego uzyskano dostęp|
|`DeviceName`|`string`|W pełni kwalifikowana nazwa domeny (FQDN) komputera|
|`AadDeviceId`|`string`|Unikatowy identyfikator urządzenia w usłudze Azure AD|
|`OSPlatform`|`string`|Platforma systemu operacyjnego działającego na komputerze. Wskazuje określone systemy operacyjne, w tym odmiany tej samej rodziny, takie jak Windows 11, Windows 10 i Windows 7.|
|`DeviceTrustType`|`string`|Wskazuje typ zaufania urządzenia, które się zalogowało. Tylko w przypadku scenariuszy zarządzanych urządzeń. Dopuszczalne wartości to Workplace, AzureAd i ServerAd.|
|`IsManaged`|`int`|Wskazuje, czy urządzenie, które zainicjowało logowanie, jest urządzeniem zarządzanym (1), czy nie (0)|
|`IsCompliant`|`int`|Wskazuje, czy urządzenie, które zainicjowało logowanie jest zgodne (1), czy niezgodne (0)|
|`AuthenticationProcessingDetails`|`string`|Szczegółowe informacje o procesorze uwierzytelniania|
|`AuthenticationRequirement`|`string`|Typ uwierzytelniania wymaganego do zalogowania się. Możliwe wartości: MultiFactorAuthentication (wymagane było uwierzytelnianie MFA) i singleFactorAuthentication (nie było wymagane uwierzytelnianie MFA).|
|`TokenIssuerType`|`int`|Wskazuje, czy wystawca tokenu ma Azure Active Directory (0) lub usługi feder służące do federacji Active Directory (1).|
|`RiskLevelAggregated`|`int`|Zagregowany poziom ryzyka podczas logowania. Możliwe wartości: 0 (zagregowany poziom ryzyka nie jest ustawiany), 1 (brak), 10 (niski), 50 (średni) lub 100 (wysoki).|
|`RiskDetails`|`int`|Szczegółowe informacje o ryzykownych stanach użytkownika, który się zalogował|
|`RiskState`|`int`|Oznacza ryzykowny stan użytkownika. Możliwe wartości: 0 (brak), 1 (bezpieczne potwierdzono), 2 (usunięte), 3 (odrzucone), 4 (zagrożenia) lub 5 (naruszone).|
|`UserAgent`|`string`|Informacje dotyczące agenta użytkownika z przeglądarki sieci Web lub innej aplikacji klienckiej|
|`ClientAppUsed`|`string`|Wskazuje używaną aplikację kliencną|
|`Browser`|`string`|Szczegóły dotyczące wersji przeglądarki używanej do logowania się|
|`ConditionalAccessPolicies`|`string`|Szczegóły zasad dostępu warunkowego zastosowanych do zdarzenia logowania|
|`ConditionalAccessStatus`|`int`|Stan zasad dostępu warunkowego zastosowanych do logowania. Dopuszczalne wartości to 0 (stosowane zasady), 1 (próba zastosowania zasad nie powiodła się) lub 2 (nie zastosowano zasad).|
|`IPAddress`|`string`|Adres IP przypisany do punktu końcowego i używany podczas powiązanej komunikacji sieciowej|
|`Country`|`string`|Dwuliterowy kod wskazujący kraj, do którego został geolokalizacji adresu IP klienta|
|`State`|`string`|Województwo, w którym wystąpiło logowanie, jeśli jest dostępne|
|`City`|`string`|Miasto, w którym znajduje się użytkownik konta|
|`Latitude`|`string`|Współrzędna od północ do południe lokalizacji logowania|
|`Longitude`|`string`|Współrzędna regionu wschodniego do zachodniego lokalizacji logowania|
|`NetworkLocationDetails`|`string`|Szczegóły lokalizacji sieciowej procesora uwierzytelniania dla zdarzenia logowania|
|`RequestId`|`string`|Unikatowy identyfikator wniosku|
|`ReportId`|`string`|Unikatowy identyfikator zdarzenia|

## <a name="related-articles"></a>Artykuły pokrewne

- [AADSpnSignInEventsBeta](./advanced-hunting-aadspnsignineventsbeta-table.md)
- [Omówienie zaawansowanego wyszukiwania](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Poznaw język zapytań](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Opis schematu](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
