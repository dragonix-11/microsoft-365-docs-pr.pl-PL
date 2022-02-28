---
title: Wykonywanie akcji na zaawansowanych wynikach zapytania wyszukiwania w Microsoft 365 Defender
description: Szybkie adresuj zagrożenia i zasoby, których dotyczy problem, w wynikach zapytania wyszukiwania zaawansowanego
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, take action
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: cd4423ab63019b554157de3a05da3c6c7e7d3d4c
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990512"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Weź udział w zaawansowanych wyszukiwaniach wyników kwerendy

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Używając zaawansowanych i rozbudowanych opcji akcji, możesz szybko zawierać zagrożenia lub [](advanced-hunting-overview.md) rozwiązać naruszone zasoby, które znajdziesz podczas zaawansowanego wyszukiwania. Za pomocą tych opcji możesz:

- Na urządzeniach można podjąć różne działania
- Poddaj pliki kwarantannie

## <a name="required-permissions"></a>Wymagane uprawnienia
Aby podjąć działania przez zaawansowane szukanie, potrzebujesz roli w programie Microsoft Defender for Endpoint z uprawnieniami do przesyłania akcji naprawczych [na urządzeniach](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). Jeśli nie możesz podjąć działania, skontaktuj się z administratorem globalnym w celu uzyskania następujących uprawnień:

*Aktywne działania naprawcze związane > zagrożeniami i zarządzanie lukami w zabezpieczeniach — obsługa działań naprawczych*

## <a name="take-various-actions-on-devices"></a>Na urządzeniach można podjąć różne działania
Na urządzeniach `DeviceId` oznaczonych w kolumnie wyników zapytania można podjąć następujące działania:

- Wyizoluj urządzenia, których dotyczy problem, w celu wyizolowania ich w celu zapobiegania późniejszemu przenoszeniu się ataków
- Zbieranie pakietu badania w celu uzyskania dodatkowych informacji forensycznych
- Uruchamianie skanowania antywirusowego w celu znalezienia i usunięcia zagrożeń przy użyciu najnowszych aktualizacji analizy zabezpieczeń
- Rozpoczynanie zautomatyzowanego badania w celu sprawdzenia i rozwiązania problemów związanych z zagrożeniami na urządzeniu i potencjalnie innymi urządzeniami, których to dotyczy
- Ograniczanie wykonywania aplikacji tylko do plików wykonywalnych podpisanych przez firmę Microsoft, aby uniemożliwić dalsze działania pod kątem zagrożeń za pomocą złośliwego oprogramowania lub innych niezaufanych plików wykonywalnych

Aby dowiedzieć się więcej o tym, jak te akcje odpowiedzi są wykonywane za pomocą programu Microsoft Defender for Endpoint, przeczytaj [o działaniach odpowiedzi na urządzeniach](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
## <a name="quarantine-files"></a>Poddaj pliki kwarantannie
Akcję *kwarantanny można* wdrożyć dla plików, aby były one automatycznie poddane kwarantannie w przypadku ich napotkania. Po wybraniu tej akcji możesz wybrać między następującymi kolumnami, aby określić, które pliki w wynikach zapytania mają zostać poddane kwarantannie:

- `SHA1` — W większości zaawansowanych tabel wyszukiwania jest to SHA-1 pliku, na który wpłynęła zarejestrowane działanie. Jeśli na przykład plik został skopiowany, będzie to skopiowany plik.
- `InitiatingProcessSHA1` — W przypadku większości zaawansowanych tabel myśliwnych jest to plik, który jest odpowiedzialny za inicjowanie zarejestrowanej akcji. Jeśli na przykład został uruchomiony proces podrzędny, będzie to proces nadrzędny. 
- `SHA256` — Odpowiada wartości SHA-256 pliku zidentyfikowanego w kolumnie `SHA1` .
- `InitiatingProcessSHA256` — Odpowiada wartości SHA-256 pliku zidentyfikowanego w kolumnie `InitiatingProcessSHA1` .

Aby dowiedzieć się więcej o tym, jak są podejmowane akcje kwarantanny i jak można je przywrócić, przeczytaj o [akcjach odpowiedzi dotyczących plików](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>Aby znaleźć pliki i poddać je kwarantannie, wyniki zapytania powinny także zawierać `DeviceId` wartości jako identyfikatory urządzeń.  

## <a name="take-action"></a>Działanie
Aby podjąć dowolną z opisanych akcji, zaznacz jeden lub więcej rekordów w wynikach zapytania, a następnie wybierz pozycję **Akcje**. Kreator przeprowadzi Cię przez proces zaznaczania, a następnie przesyłania preferowanych akcji.

![Obraz zaznaczonego rekordu z panelem inspekcji rekordu.](../../media/take-action-multiple.png)

## <a name="review-actions-taken"></a>Przejrzenie działań, które zostały wykonane
Każda akcja jest pojedynczo rejestrowana w centrum [](m365d-action-center.md) akcji w **obszarze Centrum** >  **akcjiHistory** ([security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history)). Przejdź do centrum akcji, aby sprawdzić stan każdej akcji.
 
>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w programie Microsoft Defender for Endpoint. [Włącz Microsoft 365 Defender](m365d-enable.md), aby poszukać zagrożeń przy użyciu większej liczby źródeł danych. Możesz przenieść zaawansowane przepływy pracy wyszukiwania z programu Microsoft Defender for Endpoint do programu Microsoft 365 Defender, korzystając z procedury migrowania zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytania](advanced-hunting-query-results.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Omówienie Centrum akcji](m365d-action-center.md)
