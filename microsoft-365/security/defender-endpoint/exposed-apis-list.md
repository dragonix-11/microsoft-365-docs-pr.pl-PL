---
title: Obsługiwane interfejsy API usługi ochrony punktu końcowego w usłudze Microsoft Defender
ms.reviewer: ''
description: Dowiedz się więcej o określonych obsługiwanych jednostkach Ochrona punktu końcowego w usłudze Microsoft Defender, do których można tworzyć wywołania interfejsu API.
keywords: apis, obsługiwane interfejsy API, aktor, alerty, urządzenie, użytkownik, domena, adres IP, plik, zaawansowane zapytania, zaawansowane wyszukiwanie zagrożeń
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fe43d4df71b0801ae89149797068873577c77c38
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174683"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>Obsługiwane interfejsy API usługi ochrony punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/index.yml)

> [!IMPORTANT]
> Zaawansowane możliwości wyszukiwania zagrożeń nie są uwzględniane w usłudze Defender dla firm. Zobacz [Porównanie Microsoft Defender dla Firm z planami Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>Identyfikator URI punktu końcowego i przechowywanie wersji

### <a name="endpoint-uri"></a>Identyfikator URI punktu końcowego

> Identyfikator URI bazy usług to: [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> Dane OData oparte na zapytaniach mają prefiks "/api". Aby na przykład uzyskać alerty, możesz wysłać żądanie GET do [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>Wersji

> Interfejs API obsługuje przechowywanie wersji.
>
> Bieżąca wersja to **V1.0**.
>
> Aby użyć określonej wersji, użyj następującego formatu: `https://api.securitycenter.microsoft.com/api/{Version}`. Przykład: `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> Jeśli nie określisz żadnej wersji (np. `https://api.securitycenter.microsoft.com/api/alerts`), przejdziesz do najnowszej wersji.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Dowiedz się więcej o poszczególnych obsługiwanych jednostkach, do których można uruchamiać wywołania interfejsu API, oraz o szczegółach, takich jak wartości żądań HTTP, nagłówki żądań i oczekiwane odpowiedzi.

## <a name="in-this-section"></a>W tej sekcji

Temat | Opis
:---|:---
[Zaawansowane wyszukiwanie zagrożeń](run-advanced-query-api.md) | Uruchamianie zapytań z interfejsu API.<p>*Zaawansowane możliwości wyszukiwania zagrożeń nie są uwzględniane w [usłudze Defender dla firm](../defender-business/mdb-overview.md)*.
[Metody alertu i właściwości](alerts.md) | Uruchamianie wywołań interfejsu API, takich jak \- uzyskiwanie alertów, tworzenie alertów, aktualizowanie alertów i nie tylko.
[Eksportowanie metod oceny i właściwości na urządzenie](get-assessment-methods-properties.md) | Uruchom wywołania interfejsu API, aby zbierać oceny luk w zabezpieczeniach na poszczególnych urządzeniach, takie jak: \- eksportowanie bezpiecznej oceny konfiguracji, eksportowanie oceny spisu oprogramowania, eksportowanie oceny luk w zabezpieczeniach oprogramowania i ocena luk w zabezpieczeniach oprogramowania eksportowania różnicowego.
[Zautomatyzowane metody i właściwości badania](investigation.md) | Uruchamianie wywołań interfejsu API, takich jak \- pobieranie kolekcji badania.
[Pobierz alerty powiązane z domeną](get-domain-related-alerts.md) | Uruchamianie wywołań interfejsu API, takich jak \- pobieranie urządzeń związanych z domeną, statystyki domeny i nie tylko.
[Metody i właściwości pliku](files.md) | Uruchom wywołania interfejsu API, takie jak \- pobieranie informacji o pliku, alerty związane z plikami, urządzenia związane z plikami i statystyki plików.
[Metody i właściwości wskaźników](ti-indicator.md) | Uruchom wywołanie interfejsu API, takie jak \- pobieranie wskaźników, tworzenie wskaźnika i usuwanie wskaźników.
[Pobierz alerty związane z adresem IP](get-ip-related-alerts.md) | Uruchamianie wywołań interfejsu API, takich jak \- uzyskiwanie alertów związanych z adresem IP i pobieranie statystyk adresów IP.
[Metody i właściwości komputera](machine.md) | Uruchamianie wywołań interfejsu API, takich jak \- pobieranie urządzeń, pobieranie urządzeń według identyfikatora, informacje o zalogowanych użytkownikach, edytowanie tagów i nie tylko.
[Metody i właściwości akcji komputera](machineaction.md) | Uruchom wywołanie interfejsu API, takie jak \- Izolacja, Uruchom skanowanie antywirusowe i nie tylko.
[Metody i właściwości rekomendacji](recommendation.md) | Uruchamianie wywołań interfejsu API, takich jak \- uzyskiwanie rekomendacji według identyfikatora.
[Metody i właściwości akcji korygowania](get-remediation-methods-properties.md) | Uruchom wywołanie interfejsu API, takie jak \- pobieranie wszystkich zadań korygowania, pobieranie uwidocznionego zadania korygowania urządzeń i pobieranie jednego zadania korygowania według identyfikatora.
[Metody i właściwości wyniku](score.md) | Uruchamianie wywołań interfejsu API, takich jak \- uzyskiwanie oceny ekspozycji lub uzyskiwanie wskaźnika bezpieczeństwa urządzenia.
[Metody i właściwości oprogramowania](software.md) | Uruchamianie wywołań interfejsu API, takich jak \- lista luk w zabezpieczeniach według oprogramowania.
[Metody użytkownika](user.md) | Uruchamianie wywołań interfejsu API, takich jak \- uzyskiwanie alertów związanych z użytkownikiem i urządzeń związanych z użytkownikiem.
[Metody i właściwości luki w zabezpieczeniach](vulnerability.md) | Uruchamianie wywołań interfejsu API, takich jak \- wyświetlanie listy urządzeń według luk w zabezpieczeniach.

## <a name="see-also"></a>Zobacz też

- [interfejsy API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md)

- [Informacje o wersji interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender](api-release-notes.md)
