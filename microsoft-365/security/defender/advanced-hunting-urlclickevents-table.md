---
title: Tabela UrlClickEvents w zaawansowanym schemacie wyszukiwania zagrożeń
description: Dowiedz się, jak wyszukiwać kampanie phishingowe i podejrzane kliknięcia przy użyciu tabeli UrlClickEvents w zaawansowanym schemacie wyszukiwania zagrożeń.
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, Microsoft 365 Defender wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, telemetria, dokumentacja schematu, kusto, tabela, kolumna, typ danych, opis, UrlClickEvents, SafeLinks, phishing, złośliwe oprogramowanie, złośliwe kliknięcia, outlook, zespoły, poczta e-mail, office365
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
ms.openlocfilehash: bb7ee0397c79cc64c6f7396b6c3ca9450c8306f2
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130290"
---
# <a name="urlclickevents"></a>UrlClickEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona usługi Office 365 w usłudze Microsoft Defender


Tabela `UrlClickEvents` w zaawansowanym schemacie wyszukiwania zagrożeń zawiera informacje o [kliknięciach linków Sejf](../office-365-security/safe-links.md) z wiadomości e-mail, Microsoft Teams i aplikacji Office 365 w obsługiwanych aplikacjach klasycznych, mobilnych i internetowych. 

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Aby uzyskać informacje na temat innych tabel w zaawansowanym schemacie wyszukiwania zagrożeń, zobacz [zaawansowane informacje dotyczące wyszukiwania zagrożeń](advanced-hunting-schema-tables.md).

| Nazwa kolumny | Typ danych | Opis |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Data i godzina kliknięcia linku przez użytkownika |
| `Url` | `string` | Pełny adres URL, który został kliknięty przez użytkownika |
| `ActionType` | `string` | Wskazuje, czy kliknięcie zostało dozwolone, zablokowane przez Sejf Łącza, czy zablokowane z powodu zasad dzierżawy, np. z listy Blokuj zezwalanie na dzierżawę|
| `AccountUpn` | `string` | Główna nazwa użytkownika konta, które kliknął link|
| `Workload` | `string` | Aplikacja, z której użytkownik kliknął link, z wartościami Email, Office i Teams|
| `NetworkMessageId` | `string` | Unikatowy identyfikator wiadomości e-mail zawierającej klikniętą link wygenerowaną przez Microsoft 365|
| `IPAddress` | `string` | Publiczny adres IP urządzenia, z którego użytkownik kliknął link|
| `ThreatTypes` | `string` | Werdykt w momencie kliknięcia, który informuje, czy adres URL doprowadził do złośliwego oprogramowania, phish lub innych zagrożeń|
| `DetectionMethods` | `string` | Technologia wykrywania, która została użyta do zidentyfikowania zagrożenia w momencie kliknięcia|
| `IsClickedThrough` | `bool` | Wskazuje, czy użytkownik mógł kliknąć oryginalny adres URL, czy też nie był dozwolony|
| `UrlChain` | `string` | W przypadku scenariuszy obejmujących przekierowania zawiera on adresy URL obecne w łańcuchu przekierowań|
| `ReportId` | `string` | Jest to unikatowy identyfikator zdarzenia kliknięcia. Należy pamiętać, że w przypadku scenariuszy przeglądania kliknięć identyfikator raportu będzie miał taką samą wartość, dlatego powinien służyć do skorelowania zdarzenia kliknięcia.|

Możesz wypróbować to przykładowe zapytanie, które używa `UrlClickEvents` tabeli do zwrócenia listy linków, w których użytkownik mógł kontynuować: 

```kusto
// Search for malicious links where user was allowed to proceed through
UrlClickEvents
| where ActionType == "ClickAllowed" or IsClickedThrough !="0"
| where ThreatTypes has "Phish"
| summarize by ReportId, IsClickedThrough, AccountUpn, NetworkMessageId, ThreatTypes, Timestamp
```

## <a name="related-topics"></a>Tematy pokrewne

- [Proaktywne wyszukiwanie zagrożeń](advanced-hunting-overview.md)
- [linki Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/safe-links.md)
- [Podjęcie akcji w oparciu o zaawansowane wyniki zapytania wyszukiwania zagrożeń](advanced-hunting-take-action.md)