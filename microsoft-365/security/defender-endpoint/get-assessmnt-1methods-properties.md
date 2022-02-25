---
title: Eksportowanie metod i właściwości oceny na urządzenie
description: Zawiera informacje o interfejsach API, które ściągają Zarządzanie zagrożeniami i lukami danych. Istnieją różne wywołania interfejsu API w celu uzyskania różnych typów danych. Ogólnie każde wywołanie interfejsu API zawiera dane wymagane dla urządzeń w organizacji. Ponieważ ilość danych może być duża, można ją pobrać na dwa sposoby
keywords: api, apis, ocena eksportu, ocena na urządzenie, ocena na komputer, raport oceny luk w zabezpieczeniach, ocena luk w zabezpieczeniach urządzenia, raport na temat luk w zabezpieczeniach urządzeń, bezpieczna ocena konfiguracji, raport o zabezpieczeniach podczas konfiguracji, ocena luk w oprogramowaniu, raport z lukami w oprogramowaniu, raport na temat luk w zabezpieczeniach komputera,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: e820875a3350761824c3e4e67311e55507a9cb6f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2021
ms.locfileid: "62959231"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Eksportowanie metod i właściwości oceny na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="api-description"></a>Opis interfejsu API

Zawiera metody i szczegóły właściwości dotyczące interfejsów API, które Zarządzanie zagrożeniami i lukami danych na podstawie urządzenia. Istnieją różne wywołania interfejsu API w celu uzyskania różnych typów danych. Ogólnie każde wywołanie interfejsu API zawiera dane wymagane dla urządzeń w organizacji.

> [!Note]
>
> O ile nie zaznaczono inaczej, wszystkie wymienione metody **** oceny eksportu są pełne i według **_urządzenia_** (określane również jako **_urządzenia_**).

Istnieją trzy metody interfejsu API, za pomocą których można pobierać (eksportować) różne typy informacji:

1. Eksportowanie oceny bezpiecznych konfiguracji

2. Ocena spisu oprogramowania eksportu

3. Ocena luk w zabezpieczeniach oprogramowania w eksporcie

Dla każdej metody istnieją różne wywołania interfejsu API, aby uzyskać różne typy danych. Ponieważ ilość danych może być duża, można ją pobrać na dwa sposoby:

- **Dane OData**  Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi Json, zgodnie z protokołem OData. Ta metoda jest najlepsza dla _małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K_. Odpowiedź jest podzielony na strony, \@więc można użyć pola odata.nextLink z odpowiedzi w celu pobrania następnych wyników.

- **za pośrednictwem plików** To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Dlatego jest to zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywowej sieci WI-Do. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób:

  - Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji.

  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

Dane zbierane (przy użyciu źródeł _danych OData_ lub za pośrednictwem _plików) to_ bieżąca migawka stanu bieżącego, która nie zawiera danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisać te dane we własnych magazynach danych.

## <a name="1-export-secure-configurations-assessment"></a>1. Eksportowanie oceny bezpiecznych konfiguracji

Zwraca wszystkie konfiguracje i ich stan na podstawie  per-device.

### <a name="11-methods"></a>1.1 Metody

Metoda | Typ danych | Opis
:---|:---|:---
Eksportowanie bezpiecznej oceny **konfiguracji (OData)** | Bezpieczna konfiguracja za pomocą kolekcji urządzeń. Zobacz: [Właściwości 1.2 (OData)](#12-properties-odata) | Zwraca tabelę z wpisem dla każdej unikatowej kombinacji deviceId, ConfigurationId. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi Json, zgodnie z protokołem OData. Ta metoda jest najlepsza dla małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników.
Eksportowanie bezpiecznego oceny **konfiguracji (za pośrednictwem plików)** | Bezpieczna konfiguracja za pomocą kolekcji urządzeń. Zobacz: [Właściwości 1.2 (OData)](#12-properties-odata) | Zwraca tabelę z wpisem dla każdej unikatowej kombinacji deviceId, ConfigurationId. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Dlatego jest to zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywowej sieci WI-Do. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób: 1.  Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji. 2.  Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

### <a name="12-properties-odata"></a>1.2 Właściwości (OData)

Właściwość (identyfikator) | Typ danych | Opis
:---|:---|:---
ConfigurationCategory | ciąg | Kategoria lub grupowanie, do których należy konfiguracja: Aplikacja, system operacyjny, sieć, konta, kontrolki zabezpieczeń
ConfigurationId | ciąg | Unikatowy identyfikator określonej konfiguracji
ConfigurationImpact | ciąg | Wpływ oceny konfiguracji na ogólny wynik konfiguracji (1–10)
ConfigurationName | ciąg | Nazwa wyświetlana konfiguracji
ConfigurationSubcategory | ciąg | Podkategoria lub podgrupowanie, do którego należy konfiguracja. W wielu przypadkach opisano konkretne funkcje.
DeviceId | ciąg | Unikatowy identyfikator urządzenia w usłudze.
DeviceName | ciąg | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
IsApplicable | bool | Wskazuje, czy konfiguracja lub zasady mają zastosowanie.
IsCompliant | bool | Wskazuje, czy konfiguracja lub zasady są poprawnie skonfigurowane.
IsExpectedUserImpact | bool | Wskazuje, czy jeśli konfiguracja zostanie zastosowana, będzie mieć wpływ na użytkowników
OSPlatform | ciąg | Platforma systemu operacyjnego działającego na urządzeniu. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 10 i Windows 7. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm.
RbacGroupName | ciąg | Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
ZalecenieReference | ciąg | Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.
Timestamp | ciąg | Ostatni czas, gdy konfiguracja była widziana na urządzeniu

### <a name="13-properties-via-files"></a>1.3 Właściwości (za pośrednictwem plików)

Właściwość (identyfikator) | Typ danych | Opis
:---|:---|:---
Eksportowanie plików | arraystring\[\] | Lista adresów URL pobierania plików z bieżącą migawką organizacji.
GeneratedTime | ciąg | Godzina wygenerowania eksportu.

## <a name="2-export-software-inventory-assessment"></a>2. Eksportowanie oceny spisu oprogramowania

Zwraca wszystkie zainstalowane oprogramowanie i ich szczegóły na każdym urządzeniu.

### <a name="21-methods"></a>2.1 Metody

Metoda | Typ danych | Opis
:---|:---|:---
Ocena eksportu spisu **oprogramowania (OData)** | Spis oprogramowania według kolekcji urządzeń. Zobacz: [Właściwości 2.2 (OData)](#22-properties-odata) | Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi Json, zgodnie z protokołem OData. Ta metoda jest najlepsza dla małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników.
Eksportowanie oceny spisu oprogramowania **(za pośrednictwem plików)** | Spis oprogramowania według plików urządzeń. Zobacz: [Właściwości 2.3 (za pośrednictwem plików)](#23-properties-via-files) | Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Dlatego jest to zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywowej sieci WI-Do. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób: 1.  Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji. 2.  Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

### <a name="22-properties-odata"></a>2.2 Właściwości (OData)

Właściwość (identyfikator) | Typ danych | Opis
:---|:---|:---
DeviceId | ciąg | Unikatowy identyfikator urządzenia w usłudze.
DeviceName | ciąg | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
DiskPaths | Array[string]  | Dowód dysku, że produkt jest zainstalowany na urządzeniu.
EndOfSupportDate | ciąg | Data zakończenia obsługi tego oprogramowania.
EndOfSupportStatus | ciąg | Stan zakończenia pomocy technicznej. Mogą zawierać następujące możliwe wartości: Brak, Wersja EOS, Nadchodzące wersja systemu EOS, Oprogramowanie EOS, Nadchodzące oprogramowanie EOS.
Identyfikator | ciąg | Unikatowy identyfikator rekordu.
NumberOfWeaknesses | int|Liczba słabego sprzętu w tym oprogramowaniu na tym urządzeniu
OSPlatform | ciąg | Platforma systemu operacyjnego działającego na urządzeniu. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 10 i Windows 7. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm.
RbacGroupName | ciąg | Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
RegistryPaths | Array[string] | Dowód rejestru, że produkt jest zainstalowany w urządzeniu.
SoftwareFirstSeenTimestamp | ciąg | To oprogramowanie było widoczne na urządzeniu po raz pierwszy.
Nazwa_oprogramowania | ciąg | Nazwa produktu.
SoftwareVendor | ciąg | Nazwa dostawcy oprogramowania.
SoftwareVersion | ciąg | Numer wersji produktu oprogramowania.

### <a name="23-properties-via-files"></a>2.3 Właściwości (za pośrednictwem plików)

Właściwość (identyfikator) | Typ danych | Opis
:---|:---|:---
Eksportowanie plików | arraystring\[\] | Lista adresów URL pobierania plików z bieżącą migawką organizacji.
GeneratedTime | ciąg | Godzina wygenerowania eksportu.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Ocena luk w zabezpieczeniach oprogramowania w eksporcie

Zwraca wszystkie znane luki w zabezpieczeniach na urządzeniu oraz ich szczegóły dotyczące wszystkich urządzeń.

### <a name="31-methods"></a>3.1 Metody

Metoda | Typ danych | Opis
:---|:---|:---
Ocena luk w zabezpieczeniach oprogramowania **(OData)** | Kolekcja badania Zobacz: [Właściwości 3.2 (OData)](#32-properties-odata) | Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi Json, zgodnie z protokołem OData. Ta metoda jest najlepsza dla małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników.
Ocena luk w oprogramowaniu **(za pośrednictwem plików)** | Jednostka badania Zobacz: [Właściwości 3.3 (za pośrednictwem plików)](#33-properties-via-files) | Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Dlatego jest to zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywowej sieci WI-Do. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób: 1.  Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji. 2.  Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

### <a name="32-properties-odata"></a>3.2 Właściwości (OData)

Właściwość (identyfikator) | Typ danych | Opis
:---|:---|:---
CveId | ciąg | Unikatowy identyfikator przypisany do luki w zabezpieczeniach systemu cve (Common Vulnerabilities and Exposures).
CvssScore | ciąg | Wynik CVSS dla CVE.
DeviceId | ciąg | Unikatowy identyfikator urządzenia w usłudze.
DeviceName | ciąg | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
DiskPaths | Arraystring\[\] | Dowód dysku, że produkt jest zainstalowany na urządzeniu.
ExploitabilityLevel | ciąg | Poziom wykorzystania tej luki (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp | ciąg | Po raz pierwszy cvE tego produktu zostało widziane na urządzeniu.
Identyfikator | ciąg | Unikatowy identyfikator rekordu.
LastSeenTimestamp | ciąg | Ostatni czas, gdy cvE było widoczne na urządzeniu.
OSPlatform | ciąg | Platforma systemu operacyjnego działającego na urządzeniu. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 10 i Windows 7. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm.
RbacGroupName | ciąg | Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
ZalecenieReference | ciąg | Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.
RecommendedSecurityUpdate | ciąg | Nazwa lub opis aktualizacji zabezpieczeń udostępnianej przez dostawcę oprogramowania w celu rozwiązania problemu.
RecommendedSecurityUpdateId | ciąg | Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikator odpowiednich wytycznych lub artykułów z bazy wiedzy (KB)
Ścieżki rejestru arraystring\[\] | Dowód rejestru, że produkt jest zainstalowany w urządzeniu.
Nazwa_oprogramowania | ciąg | Nazwa produktu.
SoftwareVendor | ciąg | Nazwa dostawcy oprogramowania.
SoftwareVersion | ciąg | Numer wersji produktu oprogramowania.
VulnerabilitySeverityLevel | ciąg | Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i dynamicznych czynników, na które wpływa poziom zagrożeń.

### <a name="33-properties-via-files"></a>3.3 Właściwości (za pośrednictwem plików)

Właściwość (identyfikator) | Typ danych | Opis
:---|:---|:---
Eksportowanie plików | arraystring\[\]  | Lista adresów URL pobierania plików z bieżącą migawką organizacji.
GeneratedTime | ciąg | Godzina wygenerowania eksportu.

## <a name="see-also"></a>Zobacz też

- [Eksportowanie bezpiecznego oceny konfiguracji na urządzenie](get-assessmnt-secure-cfg.md)

- [Eksportowanie oceny spisu oprogramowania na urządzenie](get-assessmnt-software-inventory.md)

- [Ocena luk w zabezpieczeniach oprogramowania na urządzeniu](get-assessmnt-software-vulnerabilities.md)

Inne powiązane

- [Zagrożenia oparte na & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)

- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
