---
title: Metody i właściwości zalecenia
description: Pobiera najnowsze alerty na początku.
keywords: apis, api Graph, obsługiwane api, get, alerts, recent
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: f6e8295d83d5ab6fb86726903800d2779f394836
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996306"
---
# <a name="recommendation-resource-type"></a>Typ zasobu zalecenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Metody

<br>

****

|Metoda|Zwracany typ|Opis|
|---|---|---|
|[Wyeksymuj wszystkie zalecenia](get-all-recommendations.md)|Kolekcja zalecenia|Pobiera listę wszystkich zaleceń dotyczących zabezpieczeń mających wpływ na organizację.|
|[Uzyskaj zalecenia według identyfikatora](get-recommendation-by-id.md)|Zalecenie|Pobiera zalecenia dotyczące zabezpieczeń na pomocą identyfikatora.|
|[Uzyskaj oprogramowanie zalecenia](list-recommendation-software.md)|[Oprogramowanie](software.md)|Pobiera zalecenia zabezpieczeń związane z konkretnym oprogramowaniem.|
|[Uzyskaj urządzenia zalecenia](get-recommendation-machines.md)|Kolekcja MachineRef|Pobiera listę urządzeń skojarzonych z zaleceniem zabezpieczeń.|
|[Uzyskiwanie luk w zabezpieczeniach w przypadku zalecenia](get-recommendation-vulnerabilities.md)|[Kolekcja luk](vulnerability.md)|Pobiera listę luk w zabezpieczeniach związanych z zaleceniem zabezpieczeń.|
|

## <a name="properties"></a>Właściwości

<br>

****

|Właściwość|Wpisać|Opis|
|---|---|---|
|identyfikator|Ciąg|Identyfikator zalecenia|
|nazwa_produktu|Ciąg|Nazwa powiązanego oprogramowania|
|recommendationName|Ciąg|Nazwa zalecenia|
|Braki|Długa|Liczba wykrytych luk|
|Dostawca|Ciąg|Nazwa dostawcy pokrewnego|
|recommendedVersion|Ciąg|Zalecana wersja|
|recommendedProgram|Ciąg|Zalecany program|
|zalecana firmaVendor|Ciąg|Polecany dostawca|
|recommendationCategory|Ciąg|Kategoria zalecenia. Dopuszczalne wartości: "Konta", "Aplikacja", "Sieć", "System operacyjny", "Kontrolki zabezpieczeń"|
|podkategoria|Ciąg|Podkategorie zalecenia|
|severityScore|Double|Potencjalny wpływ konfiguracji na ocenę bezpieczeństwa urządzeń w firmie Microsoft (1–10)|
|publicExploit|Wartość logiczna|Dostępne są publiczne luki|
|activeAlert|Wartość logiczna|Z tym zaleceniem jest skojarzony aktywny alert|
|associatedThreats|Kolekcja ciągów|Raport analizy zagrożeń jest skojarzony z tym zaleceniem|
|remediationType (Typ rozwiązywania problemów)|Ciąg|Typ działań naprawczych. Dopuszczalne wartości: "ConfigurationChange", "Update", "Upgrade", "Uninstall"|
|Stan|Wyli roku|Stan wyjątku zalecenia. Dopuszczalne wartości: "Aktywne" i "Wyjątek"|
|configScoreImpact|Double|Microsoft Secure Score for Devices impact|
|exposureImpact|Double|Wpływ na wyniki ekspozycji|
|totalMachineCount|Długa|Liczba zainstalowanych urządzeń|
|exposedMachinesCount|Długa|Liczba zainstalowanych urządzeń, które są narażone na luki w zabezpieczeniach|
|nonProductivityImpactedAssets|Długa|Liczba urządzeń, których to nie dotyczy|
|relatedComponent|Ciąg|Składnik oprogramowania pokrewnego|
|
