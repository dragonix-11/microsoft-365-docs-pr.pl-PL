---
title: Badanie adresu IP skojarzonego z alertem
description: Użyj opcji analizy, aby zbadać możliwe komunikacji między urządzeniami a zewnętrznymi adresami IP.
keywords: badanie, badanie, adres IP, alert, usługa Microsoft Defender dla punktu końcowego, zewnętrzny adres IP
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 2e314f15719d4a6a0e75d5fd26ae788e2382b75a
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996790"
---
# <a name="investigate-an-ip-address-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Badanie adresu IP skojarzonego z alertem programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Sprawdź możliwa komunikację między urządzeniami a adresami IP.

Zidentyfikowanie wszystkich urządzeń w organizacji, które komunikowały się z podejrzanymi lub znanymi złośliwymi adresami IP, takimi jak serwery Command i Control (C2), pomaga ustalić potencjalny zakres naruszenia zabezpieczeń, skojarzonych plików i zainfekowanych urządzeń.

Informacje w następujących sekcjach można znaleźć w widoku adresu IP:

- Ip worldwide (Ip worldwide)
- Odwracanie nazw DNS
- Alerty związane z tym adresem IP
- Adres IP w organizacji
- Wytła dla

## <a name="ip-worldwide-and-reverse-dns-names"></a>Adresy IP Worldwide i Reverse DNS names

Sekcja szczegóły adresu IP zawiera atrybuty adresu IP, takie jak nazwa ASN, i jego odwrotne nazwy DNS.

## <a name="alerts-related-to-this-ip"></a>Alerty związane z tym adresem IP

Sekcja **Alerty związane z tym adresem IP** zawiera listę alertów skojarzonych z tym adresem IP.

## <a name="ip-in-organization"></a>Adres IP w organizacji

Sekcja **Ip in organization** (Adres IP w organizacji) zawiera szczegółowe informacje o tym, co należy do adresu IP w organizacji.

## <a name="prevalence"></a>Wytła dla

W **sekcji Można** sprawdzić, ile urządzeń zostało połączonych z tym adresem IP oraz kiedy adres IP był pierwszy i ostatni. Wyniki tej sekcji można filtrować według okresów. domyślny okres wynosi 30 dni.

## <a name="most-recent-observed-devices-with-ip"></a>Najnowsze obserwowane urządzenia z adresem IP

Najnowsze **obserwowane urządzenia z** sekcją IP zapewniają chronologiczny widok wydarzeń i skojarzonych alertów obserwowanych przy użyciu adresu IP.

**Badanie zewnętrznego adresu IP:**

1. Wybierz **pozycję IP** z **menu** rozwijanego paska wyszukiwania.
2. Wprowadź adres IP w **polu** Wyszukiwania.
3. Kliknij ikonę wyszukiwania lub naciśnij klawisz **Enter**.

Wyświetlane są szczegółowe informacje o adresie IP, w tym: szczegóły rejestracji (jeśli jest dostępne), zwrotne adresy IP (na przykład domeny), urządzenia w organizacji, które komunikują się z tym adresem IP (w okresie, który można wybrać), oraz urządzenia w organizacji, które zostały obserwowane, komunikują się z tym adresem IP.

> [!NOTE]
> Wyniki wyszukiwania zostaną zwrócone tylko w przypadku adresów IP obserwowanych w komunikacji z urządzeniami w organizacji.

Zdefiniuj kryteria wyszukiwania za pomocą filtrów wyszukiwania. Za pomocą pola wyszukiwania osi czasu możesz również filtrować wyświetlane wyniki wszystkich urządzeń obserwowanych w organizacji komunikują się z adresem IP, plikiem skojarzonym z komunikacją i ostatnią obserwowaną datą.

Kliknięcie dowolnej nazwy urządzenia spowoduje wyświetlenie widoku tego urządzenia, w którym możesz kontynuować badanie zgłoszonych alertów, zachowań i zdarzeń.

## <a name="related-topics"></a>Tematy pokrewne

- [Wyświetlanie i organizowanie kolejki alertów programu Microsoft Defender dla punktu końcowego](alerts-queue.md)
- [Zarządzanie alertami programu Microsoft Defender dla punktów końcowych](manage-alerts.md)
- [Badanie alertów programu Microsoft Defender dla punktów końcowych](investigate-alerts.md)
- [Badanie pliku skojarzonego z alertem programu Microsoft Defender dla punktu końcowego](investigate-files.md)
- [Badanie urządzeń na liście programu Microsoft Defender dla urządzeń końcowych](investigate-machines.md)
- [Badanie domeny skojarzonej z alertem programu Microsoft Defender dla punktu końcowego](investigate-domain.md)
- [Badanie konta użytkownika w programie Microsoft Defender dla punktu końcowego](investigate-user.md)
