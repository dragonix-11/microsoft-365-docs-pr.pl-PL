---
title: Zarządzanie wskaźnikami
ms.reviewer: ''
description: Zarządzanie wskaźnikami skrótu plików, adresu IP, adresów URL lub domen definiującymi wykrywanie, zapobieganie i wykluczenie obiektów.
keywords: import, wskaźnik, lista, ioc, csv, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
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
ms.openlocfilehash: 2f66106dd39b9cd1f590148addfdd2cae89748c6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032096"
---
# <a name="manage-indicators"></a>Zarządzanie wskaźnikami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. W okienku nawigacji wybierz pozycję Wskaźnik **Ustawienia** \> **punktów** \> **końcowych** (w obszarze **Reguły**).

2. Wybierz kartę typu encji, który chcesz zarządzać.

3. Zaktualizuj szczegóły wskaźnika i **kliknij pozycję Zapisz** lub kliknij przycisk **Usuń** , jeśli chcesz usunąć encję z listy.

## <a name="import-a-list-of-iocs"></a>Importowanie listy plików IoCs

Możesz również przekazać plik CSV definiujący atrybuty wskaźników, akcję do wykonanego działania i inne szczegóły.

Pobierz przykładowy plik CSV, aby poznać obsługiwane atrybuty kolumn.

1. W okienku nawigacji wybierz pozycję Wskaźnik **Ustawienia** \> **punktów** \> **końcowych** (w obszarze **Reguły**).

2. Wybierz kartę typu encji, dla których chcesz zaimportować wskaźniki.

3. Wybierz **pozycję Importuj** \> **wybierz plik**.

4. Wybierz **pozycję Importuj**. Zrób to dla wszystkich plików, które chcesz zaimportować.

5. Wybierz pozycję **Gotowe**.

> [!NOTE]
> Dla każdej partii można przekazać tylko 500 wskaźników.

W poniższej tabeli przedstawiono obsługiwane parametry.

Parametr|Wpisać|Opis
:---|:---|:---
indicatorType (Typ wskaźnika)|Wyli roku|Typ wskaźnika. Dopuszczalne wartości to: "FileSha1", "FileSha256", "IpAddress", "DomainName" i "Url". **Wymagane**
indicatorValue|Ciąg|Tożsamość [encji Wskaźnik](ti-indicator.md) . **Wymagane**
akcja|Wyli roku|Akcja, która zostanie podjęta, jeśli wskaźnik zostanie wykryty w organizacji. Dopuszczalne wartości to: "Alert", "AlertAndBlock" i "Allowed". **Wymagane**
tytuł|Ciąg|Tytuł alertu wskaźnika. **Wymagane**
opis|Ciąg| Opis wskaźnika. **Wymagane**
expirationTime|DateTimeOffset|Czas wygaśnięcia wskaźnika w następującym formacie YYYY-MM-DDTHH:MM:SS.0Z. Wskaźnik zostanie usunięty, jeśli upłynie czas wygaśnięcia i cokolwiek się stanie w momencie wygaśnięcia w sekundach (S). **Opcjonalne**
ważność|Wyli roku|Ważność wskaźnika. Dopuszczalne wartości: "Informacyjne", "Niskie", "Średnie" i "Wysokie". **Opcjonalne**
zalecaneActions|Ciąg|Alert wskaźnika TI: zalecane działania. **Opcjonalne**
rbacGroupNames|Ciąg|Rozdzielana przecinkami lista nazw grup RBAC, do których zostanie zastosowany wskaźnik. **Opcjonalne**
kategoria|Ciąg|Kategoria alertu. Przykłady: wykonywanie i dostęp poświadczeń. **Opcjonalne**
mitretechniques|Ciąg|Kod/identyfikator technik MITRE (rozdzielany przecinkami). Aby uzyskać więcej informacji, zobacz [Enterprise taktyk.](https://attack.mitre.org/tactics/enterprise/) **Opcjonalne** Zaleca się dodawanie wartości do kategorii, gdy jest to technika MITRE.
GenerateAlert|Ciąg|Czy alert powinien zostać wygenerowany, czy nie. Dopuszczalne wartości: Prawda lub Fałsz. **Opcjonalne**



> [!NOTE]
> Notacja CIDR (Classless Inter-Domain routingu adresów IP) nie jest obsługiwana.
Aby uzyskać więcej informacji, zobacz [Kategorie alertów programu Microsoft Defender for Endpoint są teraz dostosowane do miTRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

## <a name="see-also"></a>Zobacz też

- [Tworzenie wskaźników](manage-indicators.md)
- [Tworzenie wskaźników dla plików](indicator-file.md)
- [Tworzenie wskaźników adresów IP oraz adresów URL/domen](indicator-ip-domain.md)
- [Tworzenie wskaźników na podstawie certyfikatów](indicator-certificates.md)
