---
title: Typ zasobu maszynowego
description: Dowiedz się więcej o metodach i właściwościach typu zasobu Komputer w programie Microsoft Defender for Endpoint.
keywords: apis, obsługiwane api, get, machines
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
ms.openlocfilehash: 80ac3e9ed43de98d32fd14063261452cfd5b1372
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996218"
---
# <a name="machine-resource-type"></a>Typ zasobu maszynowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Metody

<br>

****

|Metoda|Zwracany typ|Opis|
|---|---|---|
|[Komputery na liście](get-machines.md)|[kolekcja maszyn](machine.md)|Lista zestawu [obiektów komputerowych](machine.md) w organizacji.|
|[Uzyskaj komputer](get-machine-by-id.md)|[komputer](machine.md)|Uzyskaj [komputer za](machine.md) pomocą swojej tożsamości.|
|[Wyloguj się z użytkownikami](get-machine-log-on-users.md)|[kolekcja](user.md) użytkowników|Pobierz zestaw użytkownika [,](user.md) który zalogował się na [komputerze](machine.md).|
|[Alerty pokrewne](get-machine-related-alerts.md)|[kolekcja alertów](alerts.md)|Pobierz zestaw obiektów [alertów](alerts.md) , które zostały podniesione na [komputerze](machine.md).|
|[Uzyskiwanie zainstalowanego oprogramowania](get-installed-software.md)|[zbieranie](software.md) oprogramowania|Pobiera zbiór zainstalowanego oprogramowania związanego z danym identyfikatorem komputera.|
|[Uzyskiwanie wykrytych luk](get-discovered-vulnerabilities.md)|[kolekcja luk w](vulnerability.md) zabezpieczeniach|Pobiera zbiór wykrytych luk w zabezpieczeniach związanych z danym identyfikatorem komputera.|
|[Uzyskaj zalecenia dotyczące zabezpieczeń](get-security-recommendations.md)|[kolekcja rekomendacji](recommendation.md)|Pobiera kolekcję zaleceń dotyczących zabezpieczeń związanych z danym identyfikatorem komputera.|
|[Dodawanie lub usuwanie tagów maszynowych](add-or-remove-machine-tags.md)|[komputer](machine.md)|Dodawanie lub usuwanie tagu na określonym komputerze.|
|[Znajdowanie komputerów według adresów IP](find-machines-by-ip.md)|[kolekcja maszyn](machine.md)|Znajdź komputery widziane z adresem IP.|
|[Znajdowanie komputerów według tagu](find-machines-by-tag.md)|[kolekcja maszyn](machine.md)|Znajdź komputery według [tagu](machine-tags.md).|
|[Brakujące KB](get-missing-kbs-machine.md)|Kolekcja KB|Uzyskiwanie listy brakujących kb/kb skojarzonych z identyfikatorem komputera|
|[Ustawianie wartości urządzenia](set-device-value.md)|[kolekcja maszyn](machine.md)|Ustaw [wartość urządzenia](tvm-assign-device-value.md).|
|[Aktualizuj komputer](update-machine-method.md)|[kolekcja maszyn](machine.md)|Uzyskiwanie stanu aktualizacji komputera.|
|

## <a name="properties"></a>Właściwości

<br>

****

|Właściwość|Wpisać|Opis|
|---|---|---|
|identyfikator|Ciąg|[tożsamości maszynowej](machine.md) .|
|computerDnsName|Ciąg|[w](machine.md) pełni kwalifikowaną nazwę komputera.|
|firstSeen|DateTimeOffset|Pierwsza data i godzina obserwowania [komputera przez](machine.md) usługę Microsoft Defender for Endpoint.|
|lastSeen|DateTimeOffset|Godzina i data ostatniego otrzymanego pełnego raportu urządzenia. Urządzenie zazwyczaj wysyła pełny raport co 24 godziny.|
|osPlatform|Ciąg|Platforma systemu operacyjnego.|
|onboardingstatus|Ciąg|Stan dołączania maszyn. Dopuszczalne wartości: "wnoszone" i "wynoszone".|
|osProcessor|Ciąg|Procesor systemu operacyjnego. Zamiast tego należy użyć właściwości osArchitecture.|
|Wersja|Ciąg|Wersja systemu operacyjnego.|
|osBuild|Nullable long|Numer kompilacji systemu operacyjnego.|
|lastIpAddress|Ciąg|Ostatni adres IP w lokalnej nic na [komputerze](machine.md).|
|lastExternalIpAddress|Ciąg|Ostatni adres IP, za pośrednictwem którego [komputer uzyskał](machine.md) dostęp do Internetu.|
|healthStatus (Stan kondycji)|Wyli roku|[stan](machine.md) kondycji komputera. Dopuszczalne wartości to: "Aktywny", "Nieaktywny", "NiepełnosprawnyCommunication", "NoSensorData", "NoSensorDataImpairedCommunication" i "Nieznany".|
|rbacGroupName|Ciąg|Nazwa grupy komputera.|
|rbacGroupId|Ciąg|Identyfikator grupy komputera.|
|riskScore|Wyliczność z wartością null|Wynik ryzyka oceniany przez program Microsoft Defender dla punktu końcowego. Dopuszczalne wartości to: "Brak", "Informacyjne", "Niskie", "Średnie" i "Wysokie".|
|aadDeviceId|Reprezentacji z wartością null Guid|AAD Identyfikator urządzenia (gdy [komputer jest](machine.md) AAD).|
|machineTags|Kolekcja ciągów|Zestaw [tagów maszynowych](machine.md) .|
|exposureLevel|Wyliczność z wartością null|Poziom ekspozycji na poziomie oceniany przez usługę Microsoft Defender dla punktu końcowego. Dopuszczalne wartości: "Brak", "Niskie", "Średnie" i "Wysokie".|
|deviceValue|Wyliczność z wartością null|Wartość [urządzenia](tvm-assign-device-value.md). Dopuszczalne wartości: "Normalny", "Niski" i "Wysoki".|
|ipAddresses|Kolekcja IpAddress|Zestaw ***obiektów IpAddress*** . Zobacz [Uzyskiwanie interfejsu API komputerów](get-machines.md).|
|osArchitecture|Ciąg|Architektura systemu operacyjnego. Dopuszczalne wartości: "32-bitowa", "64-bitowa". Użyj tej właściwości zamiast właściwości osProcessor.|
|
