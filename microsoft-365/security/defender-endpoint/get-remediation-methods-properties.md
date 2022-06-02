---
title: Metody i właściwości akcji korygowania
description: Odpowiedź interfejsu API zawiera działania korygujące & zarządzanie lukami w zabezpieczeniach zagrożeń utworzone w dzierżawie. Możesz zażądać wszystkich działań korygowania, tylko jednego działania korygowania lub informacji o uwidocznionych urządzeniach dla wybranego zadania korygowania.
keywords: apis, korygowanie, interfejs API korygowania, pobieranie, zadania korygowania, metody korygowania, właściwości korygowania,
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
ms.openlocfilehash: 14f57d6590d580e0145abc2da788f184c88a721e
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840260"
---
# <a name="remediation-activity-methods-and-properties"></a>Metody i właściwości akcji korygowania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Odpowiedź interfejsu API zawiera działania korygowania [& zarządzanie lukami w zabezpieczeniach zagrożeń](next-gen-threat-and-vuln-mgt.md) utworzone w dzierżawie.

## <a name="methods"></a>Metody

Metoda|Typ danych|Opis
:---|:---|:---
[Wylistuj wszystkie działania korygujące](get-remediation-all-activities.md)|Kolekcja badania|Zwraca informacje o wszystkich działaniach korygowania.
[Wylistuj narażone urządzenia z jednym działaniem korygowania](get-remediation-exposed-devices-activities.md)|Jednostka badania|Zwraca informacje o uwidocznianych urządzeniach dla określonego działania korygowania.
[Pobierz jedną akcję korygującą według identyfikatora](get-remediation-one-activity.md)|Jednostka badania|Zwraca informacje dotyczące określonego działania korygowania.

Dowiedz się więcej o [działaniach korygowania](tvm-remediation.md).

## <a name="properties"></a>Właściwości

Identyfikator właściwości|Typ danych|Opis
:---|:---|:---
Kategoria|Ciąg|Kategoria działania korygowania (konfiguracja oprogramowania/zabezpieczeń)
completerEmail|Ciąg|Jeśli działanie korygujące zostało wykonane ręcznie przez kogoś, ta kolumna zawiera adres e-mail
completerId|Ciąg|Jeśli działanie korygowania zostało wykonane ręcznie przez kogoś, ta kolumna zawiera identyfikator obiektu
completionMethod|Ciąg|Działanie korygowania może zostać wykonane "automatycznie" (jeśli wszystkie urządzenia zostaną poprawione) lub "ręcznie" przez osobę, która wybierze pozycję "oznacz jako ukończone".
createdOn|Datetime|Czas utworzenia tego działania korygowania
Opis|Ciąg|Opis tego działania korygowania
dueOn|Datetime|Data ukończenia ustawiona przez twórcę dla tego działania korygowania
fixedDevices||Liczba urządzeń, które zostały naprawione
ID|Ciąg|Identyfikator tego działania korygowania
nameId|Ciąg|Pokrewna nazwa produktu
Priority (Priorytet)|Ciąg|Priorytet dla tego działania korygowania ustawionego przez twórcę (High\Medium\Low)
Productid|Ciąg|Identyfikator produktu pokrewne
productivityImpactRemediationType|Ciąg|Można zażądać kilku zmian konfiguracji tylko w przypadku urządzeń, które nie mają wpływu na użytkowników. Ta wartość wskazuje wybór między "wszystkimi uwidocznionymi urządzeniami" lub "tylko urządzeniami bez wpływu na użytkownika".
rbacGroupNames|Ciąg|Nazwy powiązanych grup urządzeń
recommendedProgram|Ciąg|Zalecany program do uaktualnienia do
recommendedVendor|Ciąg|Zalecany dostawca do uaktualnienia do
recommendedVersion|Ciąg|Zalecana wersja do aktualizacji/uaktualnienia do
Relatedcomponent|Ciąg|Powiązany składnik tego działania korygowania (podobny do powiązanego składnika zalecenia dotyczącego zabezpieczeń)
requesterEmail|Ciąg|Adres e-mail twórcy
requesterId|Ciąg|Identyfikator obiektu twórcy
requesterNotes|Ciąg|Notatki (bezpłatny tekst) dodane przez twórcę dla tego działania korygowania
Scid|Ciąg|SCID powiązanego zalecenia dotyczącego zabezpieczeń
Stan|Ciąg|Stan działania korygowania (aktywny/ukończony)
statusLastModifiedOn|Datetime|Data aktualizacji pola stanu
targetDevices|Długi|Liczba uwidocznionych urządzeń, których dotyczy to korygowanie
Tytuł|Ciąg|Tytuł tego działania korygowania
Wpisać|Ciąg|Typ korygowania
Vendorid|Ciąg|Nazwa powiązanego dostawcy

## <a name="see-also"></a>Zobacz też

- [Pobierz jedną akcję korygującą według identyfikatora](get-remediation-one-activity.md)

- [Wylistuj wszystkie działania korygujące](get-remediation-all-activities.md)

- [Wylistuj narażone urządzenia z jednym działaniem korygowania](get-remediation-exposed-devices-activities.md)

- [& zarządzanie lukami w zabezpieczeniach zagrożeń opartych na ryzyku](next-gen-threat-and-vuln-mgt.md)

- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
