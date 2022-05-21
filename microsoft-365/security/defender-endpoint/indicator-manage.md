---
title: Zarządzaj wskaźnikami
ms.reviewer: ''
description: Zarządzaj wskaźnikami dla skrótu pliku, adresu IP, adresów URL lub domen definiujących wykrywanie, zapobieganie i wykluczanie jednostek.
keywords: import, indicator, list, ioc, csv, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 72509f7480d54819fc29f40bab0e2bf65dcd8660
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622027"
---
# <a name="manage-indicators"></a>Zarządzaj wskaźnikami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Wskaźniki** **punktów końcowych** (w obszarze **Reguły**\>).

2. Wybierz kartę typu jednostki, którą chcesz zarządzać.

3. Zaktualizuj szczegóły wskaźnika i kliknij przycisk **Zapisz** lub kliknij przycisk **Usuń** , jeśli chcesz usunąć jednostkę z listy.

## <a name="import-a-list-of-iocs"></a>Importowanie listy IoCs

Możesz również przekazać plik CSV, który definiuje atrybuty wskaźników, akcję do wykonania i inne szczegóły.

Pobierz przykładowy plik CSV, aby poznać obsługiwane atrybuty kolumn.

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Wskaźniki** **punktów końcowych** (w obszarze **Reguły**\>).

2. Wybierz kartę typu jednostki, dla którą chcesz zaimportować wskaźniki.

3. Wybierz pozycję **Importuj** \> **Wybierz plik**.

4. Wybierz pozycję **Importuj**. Zrób to dla wszystkich plików, które chcesz zaimportować.

5. Wybierz pozycję **Gotowe**.

> [!NOTE]
> Dla każdej partii można przekazać tylko 500 wskaźników.

W poniższej tabeli przedstawiono obsługiwane parametry.

Parametr|Wpisać|Opis
:---|:---|:---
indicatorType|Enum|Typ wskaźnika. Możliwe wartości to: "FileSha1", "FileSha256", "IpAddress", "DomainName" i "Url". **Wymagany**
indicatorValue|Ciąg|Tożsamość jednostki [Wskaźnik](ti-indicator.md) . **Wymagany**
Działania|Enum|Akcja, która zostanie podjęta, jeśli wskaźnik zostanie odnaleziony w organizacji. Możliwe wartości to: "Alert", "AlertAndBlock" i "Allowed". **Wymagany**
Tytuł|Ciąg|Tytuł alertu wskaźnika. **Wymagany**
Opis|Ciąg| Opis wskaźnika. **Wymagany**
expirationTime|Datetimeoffset|Czas wygaśnięcia wskaźnika w następującym formacie RRRR-MM-DDTHH:MM:SS.0Z. Wskaźnik zostanie usunięty, jeśli czas wygaśnięcia upłynął, a cokolwiek się stanie w czasie wygaśnięcia, przypada na wartość sekund (SS). **Opcjonalny**
Ważności|Enum|Ważność wskaźnika. Możliwe wartości to: "Informational", "Low", "Medium" i "High". **Opcjonalny**
recommendedActions|Ciąg|Zalecane akcje alertu wskaźnika TI. **Opcjonalny**
rbacGroupNames|Ciąg|Rozdzielana przecinkami lista nazw grup RBAC, do których wskaźnik zostanie zastosowany. **Opcjonalny**
Kategorii|Ciąg|Kategoria alertu. Przykłady: wykonywanie i dostęp poświadczeń. **Opcjonalny**
mitretechniques|Ciąg|Kod/identyfikator technik MITRE (rozdzielany przecinkami). Aby uzyskać więcej informacji, zobacz [Enterprise taktyka](https://attack.mitre.org/tactics/enterprise/). **Opcjonalne** Zaleca się dodanie wartości w kategorii, gdy technika MITRE.
GenerateAlert|Ciąg|Czy alert powinien zostać wygenerowany. Możliwe wartości to: True lub False. **Opcjonalny**

> [!NOTE]
> Bezklasowa notacja routingu Inter-Domain (CIDR) dla adresów IP nie jest obsługiwana.
Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender kategorie alertów są teraz zgodne z programem MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

Obejrzyj ten film wideo, aby dowiedzieć się, jak Ochrona punktu końcowego w usłudze Microsoft Defender oferuje wiele sposobów dodawania wskaźników naruszenia zabezpieczeń i zarządzania nimi. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVw]

## <a name="see-also"></a>Zobacz też

- [Utwórz wskaźniki](manage-indicators.md)
- [Utwórz wskaźniki dla plików](indicator-file.md)
- [Utwórz wskaźniki adresów IP i adresów URL/domen](indicator-ip-domain.md)
- [Tworzenie wskaźników na podstawie certyfikatów](indicator-certificates.md)
