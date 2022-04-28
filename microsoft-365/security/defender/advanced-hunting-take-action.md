---
title: Wykonywanie akcji w wyniku zaawansowanego zapytania wyszukiwania zagrożeń w Microsoft 365 Defender
description: Szybkie rozwiązywanie problemów z zagrożeniami i zasobami, których dotyczy problem, w wynikach zaawansowanego zapytania wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie, zapytania, telemetria, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria
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
ms.openlocfilehash: b7fbe659902bf89023e994f4e1304f25f3934db8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097616"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Podjęcie akcji w oparciu o zaawansowane wyniki zapytania wyszukiwania zagrożeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Możesz szybko zawierać zagrożenia lub rozwiązywać problemy z zagrożonymi zasobami, które można znaleźć w [zaawansowanym wyszukiwaniu zagrożeń](advanced-hunting-overview.md) przy użyciu zaawansowanych i kompleksowych opcji akcji. Te opcje umożliwiają:

- Wykonaj różne akcje na urządzeniach
- Pliki kwarantanny

## <a name="required-permissions"></a>Wymagane uprawnienia
Aby podejmować działania na urządzeniach za pomocą zaawansowanego wyszukiwania zagrożeń, musisz mieć rolę w Ochrona punktu końcowego w usłudze Microsoft Defender z [uprawnieniami do przesyłania akcji korygowania na urządzeniach](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). Jeśli nie możesz wykonać akcji, skontaktuj się z administratorem globalnym w celu uzyskania następującego uprawnienia:

*Aktywne akcje korygowania > zagrożenia i zarządzanie lukami w zabezpieczeniach — obsługa korygowania*

Aby podjąć działania w przypadku wiadomości e-mail za pośrednictwem zaawansowanego wyszukiwania zagrożeń, potrzebujesz roli w Ochrona usługi Office 365 w usłudze Microsoft Defender do [wyszukiwania i przeczyszczania wiadomości e-mail](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

## <a name="take-various-actions-on-devices"></a>Wykonaj różne akcje na urządzeniach
Możesz wykonać następujące akcje na urządzeniach zidentyfikowanych przez kolumnę `DeviceId` w wynikach zapytania:

- Wyizoluj urządzenia, których dotyczy problem, aby zawierały infekcję lub zapobiegają późniejszemu przenoszeniu ataków
- Zbieranie pakietu dochodzeniowego w celu uzyskania dodatkowych informacji kryminalistycznych
- Uruchamianie skanowania antywirusowego w celu znajdowania i usuwania zagrożeń przy użyciu najnowszych aktualizacji analizy zabezpieczeń
- Zainicjowanie zautomatyzowanego badania w celu sprawdzenia i skorygowania zagrożeń na urządzeniu i prawdopodobnie innych urządzeniach, których dotyczy problem
- Ograniczanie wykonywania aplikacji tylko do plików wykonywalnych podpisanych przez firmę Microsoft, co zapobiega kolejnym działaniom zagrożeń za pośrednictwem złośliwego oprogramowania lub innych niezaufanych plików wykonywalnych

Aby dowiedzieć się więcej na temat sposobu wykonywania tych akcji odpowiedzi za pośrednictwem Ochrona punktu końcowego w usłudze Microsoft Defender, [przeczytaj o akcjach reagowania na urządzeniach](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
### <a name="quarantine-files"></a>Pliki kwarantanny
Akcję *kwarantanny* można wdrożyć w plikach, tak aby były automatycznie poddawane kwarantannie po napotkaniu. Podczas wybierania tej akcji możesz wybrać jedną z następujących kolumn, aby określić, które pliki w zapytaniu mają zostać poddane kwarantannie:

- `SHA1`: W większości zaawansowanych tabel wyszukiwania zagrożeń ta kolumna odnosi się do algorytmu SHA-1 pliku, na który miała wpływ zarejestrowana akcja. Jeśli na przykład plik został skopiowany, plik, którego dotyczy problem, będzie skopiowanym plikiem.
- `InitiatingProcessSHA1`: W większości zaawansowanych tabel wyszukiwania zagrożeń ta kolumna odnosi się do pliku odpowiedzialnego za zainicjowanie zarejestrowanej akcji. Jeśli na przykład uruchomiono proces podrzędny, ten plik inicjatora będzie częścią procesu nadrzędnego. 
- `SHA256`: Ta kolumna jest odpowiednikiem SHA-256 pliku zidentyfikowanego przez kolumnę `SHA1` .
- `InitiatingProcessSHA256`: Ta kolumna jest odpowiednikiem SHA-256 pliku zidentyfikowanego przez kolumnę `InitiatingProcessSHA1` .

Aby dowiedzieć się więcej na temat sposobu wykonywania akcji kwarantanny i sposobu przywracania plików, [przeczytaj o akcjach reagowania na pliki](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>Aby zlokalizować pliki i poddać je kwarantannie, wyniki zapytania powinny również zawierać `DeviceId` wartości jako identyfikatory urządzeń.  

Aby wykonać dowolną z opisanych akcji, wybierz co najmniej jeden rekord w wynikach zapytania, a następnie wybierz pozycję **Wykonaj akcje**. Kreator przeprowadzi Cię przez proces wybierania, a następnie przesyłania preferowanych akcji.

:::image type="content" source="../../media/take-action-multiple.png" alt-text="Opcja Wykonaj akcje w portalu Microsoft 365 Defender" lightbox="../../media/take-action-multiple.png":::


## <a name="take-various-actions-on-emails"></a>Wykonaj różne akcje w wiadomościach e-mail
Oprócz kroków korygowania skoncentrowanych na urządzeniu można również wykonać pewne akcje dotyczące wiadomości e-mail z wyników zapytania. Wybierz rekordy, na które chcesz wykonać akcję, wybierz pozycję **Wykonaj akcje**, a następnie w obszarze **Wybierz akcje** wybierz swój wybór z następujących opcji:
- `Move to mailbox folder` — wybierz tę opcję, aby przenieść wiadomości e-mail do folderu Wiadomości-śmieci, Skrzynka odbiorcza lub Usunięte elementy

   :::image type="content" source="../../media/advanced-hunting-take-actions-email.png" alt-text="Opcja Wykonaj akcje w portalu Microsoft 365 Defender" lightbox="../../media/advanced-hunting-take-actions-email.png":::

- `Delete email` — wybierz tę opcję, aby przenieść wiadomości e-mail do folderu Usunięte elementy (**usuwanie nietrwałe**) lub usunąć je trwale (**usuwanie twarde**)

   :::image type="content" source="../../media/advanced-hunting-take-actions-email-del.png" alt-text="Opcja Wykonaj akcje w portalu Microsoft 365 Defender" lightbox="../../media/advanced-hunting-take-actions-email-del.png":::

Możesz również podać nazwę korygowania i krótki opis akcji podjętej w celu łatwego śledzenia jej w historii centrum akcji. Możesz również użyć identyfikatora zatwierdzenia, aby odfiltrować te akcje w centrum akcji. Ten identyfikator jest podany na końcu kreatora:

:::image type="content" source="../../media/choose-email-actions-entities.png" alt-text="Kreator podejmowania akcji przedstawiający wybieranie akcji dla jednostek" lightbox="../../media/choose-email-actions-entities.png":::

Te akcje poczty e-mail mają również zastosowanie do [wykrywania niestandardowego](custom-detections-overview.md) .


## <a name="review-actions-taken"></a>Przejrzyj podjęte akcje
Każda akcja jest rejestrowana indywidualnie w [centrum akcji](m365d-action-center.md) w obszarze **Centrum** >  **akcjiHistory** ([security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history)). Przejdź do centrum akcji, aby sprawdzić stan każdej akcji.
 
>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender. [Włącz Microsoft 365 Defender](m365d-enable.md), aby wyszukiwać zagrożenia przy użyciu większej liczby źródeł danych. Zaawansowane przepływy pracy wyszukiwania zagrożeń można przenieść z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender, wykonując kroki opisane w [temacie Migrowanie zaawansowanych zapytań wyszukiwania zagrożeń z Ochrona punktu końcowego w usłudze Microsoft Defender](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytań](advanced-hunting-query-results.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Centrum akcji — omówienie](m365d-action-center.md)
