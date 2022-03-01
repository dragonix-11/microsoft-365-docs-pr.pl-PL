---
title: Metody i właściwości działań naprawczych
description: Odpowiedź interfejsu API zawiera zagrożenia & zarządzanie lukami w zabezpieczeniach działania naprawcze utworzone w dzierżawie. Możesz zażądać wszystkich działań naprawczych, tylko jednego działania naprawczego lub informacji o urządzeniach ujawnionych w wybranym zadaniu naprawczym.
keywords: api, działania naprawcze, api działań naprawczych, uzyskiwanie, zadania naprawcze, metody rozwiązywania problemów, właściwości rozwiązywania problemów,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 124a44f6a04e4e4e77d80ac91ed4da169e2a4aae
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013281"
---
# <a name="remediation-activity-methods-and-properties"></a>Metody i właściwości działań naprawczych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Odpowiedź interfejsu API zawiera [informacje & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md) działania naprawcze, które zostały utworzone w dzierżawie.

## <a name="methods"></a>Metody

Metoda|Typ danych|Opis
:---|:---|:---
[Lista wszystkich działań naprawczych](get-remediation-all-activities.md)|Kolekcja badania|Zwraca informacje o wszystkich działaniach naprawczych.
[Lista dostępnych urządzeń w przypadku jednego działania naprawczego](get-remediation-exposed-devices-activities.md)|Jednostka badania|Zwraca informacje o urządzeniach ujawnionych dla określonego działania naprawczego.
[Uzyskiwanie jednego działania naprawczego według identyfikatora](get-remediation-one-activity.md)|Jednostka badania|Zwraca informacje dotyczące określonego działania naprawczego.

Dowiedz się więcej o [działaniach naprawczych](tvm-remediation.md).

## <a name="properties"></a>Właściwości

Identyfikator właściwości|Typ danych|Opis
:---|:---|:---
Kategoria|Ciąg|Kategoria działań naprawczych (konfiguracja oprogramowania/zabezpieczeń)
completerEmail|Ciąg|Jeśli działania naprawcze zostały wykonane ręcznie przez inną osobę, ta kolumna zawiera adres e-mail tej osoby
completerId|Ciąg|Jeśli działania naprawcze zostały wykonane ręcznie przez inną osobę, ta kolumna zawiera identyfikator obiektu
completionMethod|Ciąg|Działania naprawcze mogą być wykonywane "automatycznie" (jeśli wszystkie urządzenia zostały naprawone) lub "ręcznie" przez osobę, która wybierze pozycję "Oznacz jako ukończone".
createdOn|DateTime|Godzina utworzenia tego działania naprawczego
Opis|Ciąg|Opis tego działania naprawczego
dueOn|DateTime|Termin realizacji tego działania naprawczego ustawiony przez twórcę
fixedDevices||Liczba urządzeń, które zostały naprawione
Identyfikator|Ciąg|Identyfikator tego działania naprawczego
nameId|Ciąg|Powiązana nazwa produktu
Priority (Priorytet)|Ciąg|Priorytet zestawu twórców dla tego działania naprawczego (Wysoki\Średni\Niski)
productId|Ciąg|Identyfikator produktu pokrewnego
productivityImpactRemediationType|Ciąg|O kilka zmian w konfiguracji można zażądać tylko w przypadku urządzeń, które nie wpływają na użytkowników. Ta wartość wskazuje wybór między "wszystkimi ujawnione urządzeniami" lub "tylko urządzeniami bez wpływu na użytkownika".
rbacGroupNames|Ciąg|Nazwy grup urządzeń pokrewnych
recommendedProgram|Ciąg|Zalecany program do uaktualnienia do wersji
zalecana firmaVendor|Ciąg|Zaleca się uaktualnienie do wersji zalecanej przez dostawcę
recommendedVersion|Ciąg|Zalecana wersja do aktualizacji/uaktualnienia do
relatedComponent|Ciąg|Powiązany składnik tego działania naprawczego (podobny do składnika pokrewnego w przypadku zalecenia zabezpieczeń)
requesterEmail|Ciąg|Adres e-mail twórcy
requesterId|Ciąg|Identyfikator obiektu Kreatora
requesterNotes|Ciąg|Uwagi (bezpłatny tekst) dodane przez autora w celu działania naprawczego
Scid|Ciąg|SCID pokrewnego zalecenia zabezpieczeń
Stan|Ciąg|Stan działań naprawczych (Aktywne/Ukończone)
statusLastModifiedOn|DateTime|Data zaktualizowania pola stanu
targetDevices|Długa|Liczba ujawnionych urządzeń, których działania naprawcze mają zastosowanie
Tytuł|Ciąg|Tytuł tego działania naprawczego
Wpisać|Ciąg|Typ działań naprawczych
vendorId|Ciąg|Nazwa dostawcy pokrewnego

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie jednego działania naprawczego według identyfikatora](get-remediation-one-activity.md)

- [Lista wszystkich działań naprawczych](get-remediation-all-activities.md)

- [Lista dostępnych urządzeń w przypadku jednego działania naprawczego](get-remediation-exposed-devices-activities.md)

- [Zagrożenia oparte na czynnikach ryzyka & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)

- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
