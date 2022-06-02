---
title: Tabela AADSpnSignInEventsBeta w zaawansowanym schemacie wyszukiwania zagrożeń
description: Dowiedz się więcej o informacjach skojarzonych z jednostką usługi Azure Active Directory i tabelą zdarzeń logowania tożsamości zarządzanej.
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
ms.openlocfilehash: b1b9d6405abdddea42652cfd4c532df91eeb6b30
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842219"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**Dotyczy:**
- Microsoft 365 Defender

> [!IMPORTANT]
> Tabela `AADSpnSignInEventsBeta` jest obecnie w wersji beta i jest oferowana krótkoterminowo, aby umożliwić wyszukiwanie zdarzeń logowania Azure Active Directory (AAD). Klienci muszą mieć licencję Azure Active Directory — wersja Premium P2 do zbierania i wyświetlania działań dla tej tabeli. Firma Microsoft ostatecznie przeniesie wszystkie informacje o schemacie logowania do `IdentityLogonEvents` tabeli.

Tabela `AADSpnSignInEventsBeta` w zaawansowanym schemacie wyszukiwania zagrożeń zawiera informacje o jednostce usługi Azure Active Directory i logowaniach tożsamości zarządzanych. Możesz dowiedzieć się więcej na temat różnych rodzajów logowań w [Azure Active Directory raportach aktywności logowania — wersja zapoznawcza](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

To odwołanie służy do konstruowania zapytań, które zwracają informacje z tabeli.

Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, zobacz [zaawansowane informacje dotyczące wyszukiwania zagrożeń](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Nazwa kolumny|Typ danych|Opis|
|---|---|---|
|`Timestamp`|`datetime`|Data i godzina wygenerowania rekordu|
|`Application`|`string`|Aplikacja, która wykonała zarejestrowaną akcję|
|`ApplicationId`|`string`|Unikatowy identyfikator aplikacji|
|`IsManagedIdentity`|`boolean`|Wskazuje, czy logowanie zostało uruchomione przez tożsamość zarządzaną|
|`ErrorCode`|`int`|Zawiera kod błędu w przypadku wystąpienia błędu logowania. Aby znaleźć opis określonego kodu błędu, odwiedź stronę <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Unikatowy identyfikator zdarzenia logowania|
|`ServicePrincipalName`|`string`|Nazwa jednostki usługi, która uruchomiła logowanie|
|`ServicePrincipalId`|`string`|Unikatowy identyfikator jednostki usługi, która uruchomiła logowanie|
|`ResourceDisplayName`|`string`|Nazwa wyświetlana zasobu, do którego uzyskano dostęp|
|`ResourceId`|`string`|Unikatowy identyfikator zasobu, do których uzyskano dostęp|
|`ResourceTenantId`|`string`|Unikatowy identyfikator dzierżawy zasobu, do których uzyskano dostęp|
|`IPAddress`|`string`|Adres IP przypisany do punktu końcowego i używany podczas powiązanej komunikacji sieciowej|
|`Country`|`string`|Dwuliterowy kod wskazujący kraj, w którym adres IP klienta jest geolokalizowany|
|`State`|`string`|Stan, w którym nastąpiło logowanie, jeśli jest dostępny|
|`City`|`string`|Miasto, w którym znajduje się użytkownik konta|
|`Latitude`|`string`|Współrzędne północ-południe lokalizacji logowania|
|`Longitude`|`string`|Współrzędne ze wschodu na zachód lokalizacji logowania|
|`RequestId`|`string`|Unikatowy identyfikator żądania|
|`ReportId`|`string`|Unikatowy identyfikator zdarzenia|
||||

## <a name="related-articles"></a>Powiązane artykuły:

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [Omówienie zaawansowanego wyszukiwania zagrożeń](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Nauka języka zapytań](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Analiza schematu](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
