---
title: Tabela EmailEvents w zaawansowanym schemacie wyszukiwania zagrożeń
description: Informacje o zdarzeniach skojarzonych z wiadomościami e-mail Microsoft 365 w tabeli EmailEvents zaawansowanego schematu wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, odwołanie do schematu, kusto, tabela, kolumna, typ danych, opis, EmailEvents, identyfikator wiadomości sieciowej, nadawca, adresat, identyfikator załącznika, nazwa załącznika, werdykt złośliwego oprogramowania, werdykt wyłudzania informacji, liczba załączników, liczba linków, liczba adresów URL
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
ms.openlocfilehash: f4456dc29f4d62703041b9c386aa7c9fa132695a
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667367"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Tabela `EmailEvents` w zaawansowanym schemacie [wyszukiwania zagrożeń](advanced-hunting-overview.md) zawiera informacje o zdarzeniach związanych z przetwarzaniem wiadomości e-mail na Ochrona usługi Office 365 w usłudze Microsoft Defender. To odwołanie służy do konstruowania zapytań, które zwracają informacje z tej tabeli.

> [!TIP]
> Aby uzyskać szczegółowe informacje na temat typów zdarzeń (`ActionType`wartości) obsługiwanych przez tabelę, użyj wbudowanego odwołania do schematu dostępnego w Defender dla Chmury.

Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, [zobacz zaawansowane informacje dotyczące wyszukiwania zagrożeń](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina zarejestrowania zdarzenia |
| `NetworkMessageId` | `string` | Unikatowy identyfikator wiadomości e-mail wygenerowany przez Microsoft 365 |
| `InternetMessageId` | `string` | Publiczny identyfikator wiadomości e-mail ustawionej przez system wysyłania wiadomości e-mail |
| `SenderMailFromAddress` | `string` | Adres e-mail nadawcy w nagłówku MAIL FROM, znany również jako nadawca koperty lub adres Return-Path |
| `SenderFromAddress` | `string` | Adres e-mail nadawcy w nagłówku FROM, który jest widoczny dla adresatów poczty e-mail na klientach poczty e-mail |
| `SenderDisplayName` | `string` | Nazwa nadawcy wyświetlana w książce adresowej, zazwyczaj kombinacja danego lub imienia, inicjał środkowy oraz nazwisko lub nazwisko |
| `SenderObjectId` | `string` |Unikatowy identyfikator konta nadawcy w usłudze Azure AD |
| `SenderMailFromDomain` | `string` | Domena nadawcy w nagłówku MAIL FROM, znana również jako nadawca koperty lub adres Return-Path |
| `SenderFromDomain` | `string` | Domena nadawcy w nagłówku FROM, która jest widoczna dla adresatów poczty e-mail na klientach poczty e-mail |
| `SenderIPv4` | `string` | Adres IPv4 ostatniego wykrytego serwera poczty, który przekaźnikował wiadomość |
| `SenderIPv6` | `string` | Adres IPv6 ostatniego wykrytego serwera poczty, który przekaźnikował wiadomość |
| `RecipientEmailAddress` | `string` | Adres e-mail odbiorcy lub adres e-mail odbiorcy po rozszerzeniu listy dystrybucyjnej |
| `RecipientObjectId` | `string` | Unikatowy identyfikator adresata wiadomości e-mail w usłudze Azure AD |
| `Subject` | `string` | Temat wiadomości e-mail |
| `EmailClusterId` | `string` | Identyfikator grupy podobnych wiadomości e-mail klastrowanych na podstawie heurystycznej analizy ich zawartości |
| `EmailDirection` | `string` | Kierunek wiadomości e-mail względem sieci: przychodzący, wychodzący, wewnątrz organizacji |
| `DeliveryAction` | `string` | Akcja dostarczania wiadomości e-mail: dostarczona, zablokowana, zablokowana lub zamieniona |
| `DeliveryLocation` | `string` | Lokalizacja, w której została dostarczona wiadomość e-mail: Skrzynka odbiorcza/Folder, Lokalna/Zewnętrzna, Śmieci, Kwarantanna, Niepowodzenie, Porzucone, Usunięte elementy |
| `ThreatTypes` | `string` | Werdykt ze stosu filtrowania wiadomości e-mail dotyczący tego, czy wiadomość e-mail zawiera złośliwe oprogramowanie, wyłudzanie informacji lub inne zagrożenia |
| `ThreatNames` | `string` |Wykryto nazwę wykrywania złośliwego oprogramowania lub innych zagrożeń |
| `DetectionMethods` | `string` | Metody służące do wykrywania złośliwego oprogramowania, wyłudzania informacji lub innych zagrożeń znalezionych w wiadomości e-mail |
| `ConfidenceLevel` | `string` | Lista poziomów ufności wszelkich werdyktów dotyczących spamu lub wyłudzania informacji. W przypadku spamu ta kolumna pokazuje poziom ufności spamu (SCL), wskazujący, czy wiadomość e-mail została pominięta (-1), która nie jest spamem (0,1), została uznana za spam z umiarkowanym zaufaniem (5,6) lub uznany za spam z dużą pewnością (9). W przypadku wyłudzania informacji w tej kolumnie jest wyświetlana informacja o tym, czy poziom ufności to "Wysoki" czy "Niski". |
| `EmailAction` | `string` | Ostateczna akcja wykonywana w wiadomości e-mail na podstawie werdyktu filtru, zasad i akcji użytkownika: przenoszenie wiadomości do folderu wiadomości-śmieci, dodawanie nagłówka X, modyfikowanie tematu, wiadomości przekierowania, usuwanie wiadomości, wysyłanie do kwarantanny, Brak wykonania akcji, wiadomość Bcc |
| `EmailActionPolicy` | `string` | Zasady akcji, które weszły w życie: Antispam high-confidence, Antispam, Antispam bulk mail, Antispam phishing, Anti-phishing domain impersonation, Anti-phishing user impersonation, Anti-phishing spoof, Anti-phishing graph impersonation, Antimalware, Sejf Attachments, Enterprise Transport Rules (ETR) |
| `EmailActionPolicyGuid` | `string` | Unikatowy identyfikator zasad, które określają ostateczną akcję poczty |
| `AttachmentCount` | `int` | Liczba załączników w wiadomości e-mail |
| `UrlCount` | `int` | Liczba osadzonych adresów URL w wiadomości e-mail |
| `EmailLanguage` | `string` | Wykryty język zawartości wiadomości e-mail |
| `Connectors` | `string` | Instrukcje niestandardowe definiujące przepływ poczty organizacji i sposób kierowania wiadomości e-mail |
| `OrgLevelAction` | `string` | Akcja wykonywana w wiadomości e-mail w odpowiedzi na dopasowania do zasad zdefiniowanych na poziomie organizacji |
| `OrgLevelPolicy` | `string` | Zasady organizacyjne, które wyzwoliły akcję podjętą w wiadomości e-mail |
| `UserLevelAction` | `string` | Akcja wykonywana w wiadomości e-mail w odpowiedzi na dopasowania do zasad skrzynki pocztowej zdefiniowanych przez adresata |
| `UserLevelPolicy` | `string` | Zasady skrzynki pocztowej użytkownika końcowego, które wyzwoliły akcję podjętą w wiadomości e-mail |
| `ReportId` | `long` | Identyfikator zdarzenia na podstawie licznika powtarzającego się. Aby zidentyfikować unikatowe zdarzenia, ta kolumna musi być używana w połączeniu z kolumnami DeviceName i Timestamp. |
| `AuthenticationDetails` | `string` | Lista werdyktów dotyczących przebiegu lub niepowodzenia za pomocą protokołów uwierzytelniania poczty e-mail, takich jak DMARC, DKIM, SPF lub kombinacja wielu typów uwierzytelniania (CompAuth) |

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
