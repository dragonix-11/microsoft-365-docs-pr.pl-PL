---
title: Tabela EmailEvents w zaawansowanym schemacie wyszukiwania
description: Informacje o wydarzeniach związanych z Microsoft 365 e-mail w tabeli EmailEvents zaawansowanego schematu wyszukiwania
keywords: zaawansowane szukanie, schłodzenie przed zagrożeniami, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, EmailEvents, identyfikator wiadomości sieciowej, nadawca, adresat, identyfikator załącznika, nazwa załącznika, werdykt złośliwego oprogramowania, werdykt wyłudzania informacji, liczba załączników, liczba linków, liczba adresów URL
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
ms.openlocfilehash: baf6e8d6d896e31b5092f7d2b8948bb7771382bd
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017919"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Tabela `EmailEvents` w zaawansowanym [schemacie chłoniania](advanced-hunting-overview.md) zawiera informacje o wydarzeniach dotyczących przetwarzania wiadomości e-mail w programie Microsoft Defender for Office 365. To odwołanie pozwala konstruować zapytania, które zwracają informacje z tej tabeli.

>[!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType` wartości) obsługiwanych w tabeli, użyj wbudowanego schematu referencyjnego dostępnego w usłudze Defender dla chmury.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, [zapoznaj się z zaawansowanymi informacjami na temat wyszukiwania](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina nagrania zdarzenia |
| `NetworkMessageId` | `string` | Unikatowy identyfikator wiadomości e-mail wygenerowany przez Microsoft 365 |
| `InternetMessageId` | `string` | Publiczny identyfikator wiadomości e-mail ustawiany przez wysyłający system poczty e-mail |
| `SenderMailFromAddress` | `string` | Sender email address in the MAIL FROM header, also known as the envelope sender or the Return-Path address |
| `SenderFromAddress` | `string` | Adres e-mail nadawcy w nagłówku OD, który jest widoczny dla adresatów wiadomości e-mail w ich klientach poczty e-mail |
| `SenderDisplayName` | `string` | Imię i nazwisko nadawcy wyświetlane w książce adresowej. Zwykle jest to połączenie imienia lub danego imienia, inicjała środkowego oraz nazwiska lub nazwiska. |
| `SenderObjectId` | `string` |Unikatowy identyfikator konta nadawcy w usłudze Azure AD |
| `SenderMailFromDomain` | `string` | Domena nadawcy w nagłówku MAIL FROM, z nazwą nadawcy koperty lub Return-Path adres |
| `SenderFromDomain` | `string` | Domena nadawcy w nagłówku FROM, który jest widoczny dla adresatów wiadomości e-mail w ich klientach poczty e-mail |
| `SenderIPv4` | `string` | Adres IPv4 ostatniego wykrytego serwera poczty, który przekazał wiadomość |
| `SenderIPv6` | `string` | Adres IPv6 ostatniego wykrytego serwera poczty, który przekazał wiadomość |
| `RecipientEmailAddress` | `string` | Adres e-mail adresata lub adres e-mail odbiorcy po rozwinięciu listy dystrybucyjnej |
| `RecipientObjectId` | `string` | Unikatowy identyfikator adresata poczty e-mail w usłudze Azure AD |
| `Subject` | `string` | Temat wiadomości e-mail |
| `EmailClusterId` | `string` | Identyfikator grupy podobnych wiadomości e-mail grupowanych na podstawie analizy heuristycznej ich zawartości |
| `EmailDirection` | `string` | Kierunek wiadomości e-mail względem Twojej sieci: przychodzący, wychodzący, wewnątrz organizacji |
| `DeliveryAction` | `string` | Akcja dostarczenia wiadomości e-mail: Dostarczono, Wiadomości-śmieci, Zablokowane lub Zamienione |
| `DeliveryLocation` | `string` | Lokalizacja, w której wiadomość e-mail została dostarczona: Skrzynka odbiorcza/folder, Lokalnie/Zewnętrzne, Wiadomości-śmieci, Kwarantanna, Niepowodzenie, Upuszczenie, Elementy usunięte |
| `ThreatTypes` | `string` | Werdykt z stosu filtrowania wiadomości e-mail na temat tego, czy wiadomość e-mail zawiera złośliwe oprogramowanie, wyłudzanie informacji lub inne zagrożenia |
| `ThreatNames` | `string` |Nazwa wykrywania w przypadku znalezionego złośliwego oprogramowania lub innych zagrożeń |
| `DetectionMethods` | `string` | Metody używane do wykrywania złośliwego oprogramowania, wyłudzania informacji lub innych zagrożeń znalezionych w wiadomości e-mail |
| `ConfidenceLevel` | `string` | Lista poziomów ufności wszystkich werdyktów spamu lub próby wyłudzenia informacji. W przypadku spamu w tej kolumnie jest podany poziom ufności filtru spamu, który wskazuje, że wiadomość e-mail została pominięta (-1), która nie jest spamem (0,1), została znaleziona jako spam z umiarkowaną ufnością (5,6) lub została znaleziona jako spam z dużą pewnością (9). W przypadku wyłudzania informacji ta kolumna wyświetla, czy poziom ufności jest "Wysoki" czy "Niski". |
| `EmailAction` | `string` | Ostateczna akcja podjęta w związku z wiadomością e-mail na podstawie werdyktu filtru, zasad i akcji użytkownika: Przeniesienie wiadomości do folderu wiadomości-śmieci, Dodawanie nagłówka X, Modyfikowanie tematu, Przekierowywanie wiadomości, Usuwanie wiadomości, wysyłanie do kwarantanny, Brak wykonanej akcji, wiadomość UDW |
| `EmailActionPolicy` | `string` | Zasady akcji, które zostały wprowadzone: Ochrona przed dużą pewnośćą, ochrona przed złośliwym oprogramowaniem, poczta masowa ochrony przed wiadomościami, wyłudzanie informacji o wyłudzaniu informacji, personifikacja użytkowników przed wyłudzaniem informacji, wyłudzanie informacji, personifikacja wyłudzania informacji, załączniki ochrony przed złośliwym oprogramowaniem, załączniki Sejf, reguły transportu firmy Enterprise (ETR) |
| `EmailActionPolicyGuid` | `string` | Unikatowy identyfikator zasady, która określała ostateczną akcję poczty |
| `AttachmentCount` | `int` | Liczba załączników w wiadomości e-mail |
| `UrlCount` | `int` | Liczba osadzonych adresów URL w wiadomości e-mail |
| `EmailLanguage` | `string` | Wykryty język zawartości wiadomości e-mail |
| `Connectors` | `string` | Niestandardowe instrukcje definiujące przepływ poczty e-mail organizacji i sposób rozsyłania wiadomości e-mail |
| `OrgLevelAction` | `string` | Działanie podejmowane w związku z wiadomością e-mail w odpowiedzi na dopasowania do zasad zdefiniowanych na poziomie organizacji |
| `OrgLevelPolicy` | `string` | Zasady organizacji, które wyzwoliły akcję podejmowane na wiadomości e-mail |
| `UserLevelAction` | `string` | Działanie podejmowane w związku z wiadomością e-mail w odpowiedzi na dopasowania do zasad skrzynki pocztowej zdefiniowanych przez adresata |
| `UserLevelPolicy` | `string` | Zasady skrzynki pocztowej użytkownika końcowego, które wyzwoliły akcję podejmowane na wiadomości e-mail |
| `ReportId` | `long` | Identyfikator zdarzenia oparty na liczniku powtarzających się. Aby zidentyfikować unikatowe zdarzenia, należy użyć tej kolumny w połączeniu z kolumnami DeviceName i Timestamp. |
| `AuthenticationDetails` | `string` | Lista zdanych lub nieudanych werdyktów przez protokoły uwierzytelniania poczty e-mail, takie jak DMARC, DKIM, SPF lub połączenie wielu typów uwierzytelniania (CompAuth) |

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)
