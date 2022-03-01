---
title: Eksportowanie metod i właściwości oceny na urządzenie
description: Zawiera informacje o interfejsach API, które ściągają Zarządzanie zagrożeniami i lukami danych. Istnieją różne wywołania interfejsu API w celu uzyskania różnych typów danych. Ogólnie każde wywołanie interfejsu API zawiera dane wymagane dla urządzeń w organizacji.
keywords: api, apis, ocena eksportu, ocena na urządzenie, ocena na komputer, raport oceny luk w zabezpieczeniach, ocena luk w zabezpieczeniach urządzenia, raport na temat luk w zabezpieczeniach urządzeń, bezpieczna ocena konfiguracji, raport o zabezpieczeniach podczas konfiguracji, ocena luk w oprogramowaniu, raport z lukami w oprogramowaniu, raport na temat luk w zabezpieczeniach komputera,
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: c10f454919afc725b37537aa354fed05b95cb571
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013273"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Eksportowanie metod i właściwości oceny na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="api-description"></a>Opis interfejsu API

Zawiera metody i szczegóły właściwości dotyczące interfejsów API, które Zarządzanie zagrożeniami i lukami danych w zależności od urządzenia. Istnieją różne wywołania interfejsu API w celu uzyskania różnych typów danych. Ogólnie każde wywołanie interfejsu API zawiera dane wymagane dla urządzeń w organizacji.

> [!NOTE]
> O ile nie zaznaczono inaczej, wszystkie wymienione metody **** oceny eksportu są pełne i według **_urządzenia_** (określane również jako **_urządzenia_**).

Za pomocą interfejsów API oceny eksportu można pobierać (eksportować) różne typy informacji:

- [1. Eksportowanie oceny bezpiecznych konfiguracji](#1-export-secure-configurations-assessment)
- [2. Eksportowanie oceny spisu oprogramowania](#2-export-software-inventory-assessment)
- [3. Ocena luk w zabezpieczeniach oprogramowania w eksporcie](#3-export-software-vulnerabilities-assessment)

Interfejsy API odpowiadające typom informacji o eksportowaniu są opisane w sekcjach 1, 2 i 3.

Każda metoda ma inne wywołania interfejsu API w celu uzyskania różnych typów danych. Ponieważ ilość danych może być duża, można ją pobrać na dwa sposoby:

- **Odpowiedź JSON**  Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza dla _małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K_. Odpowiedź jest podzielony na strony, \@więc można użyć pola odata.nextLink z odpowiedzi w celu pobrania następnych wyników.

- **za pośrednictwem plików** To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Jest to więc zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywce. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób:
  - Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji.
  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

Dane zbierane przy użyciu "odpowiedzi _JSON lub_ za pośrednictwem _plików" to_ bieżąca migawka bieżącego stanu. Nie zawiera ona danych historycznych. Aby zbierać dane historyczne, klienci muszą je zapisywać we własnych magazynach danych.

## <a name="1-export-secure-configurations-assessment"></a>1. Eksportowanie oceny bezpiecznych konfiguracji

Zwraca wszystkie konfiguracje i ich stan na podstawie  per-device.

### <a name="11-methods"></a>1.1 Metody

Metoda|Typ danych|Opis
:---|:---|:---
Eksportowanie bezpiecznej oceny **konfiguracji (odpowiedź JSON)**|Bezpieczna konfiguracja za pomocą kolekcji urządzeń. Zobacz: [Właściwości 1.2 (odpowiedź JSON)](#12-properties-json-response)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji deviceId, ConfigurationId. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza dla małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników.
Eksportowanie bezpiecznego oceny **konfiguracji (za pośrednictwem plików)**|Bezpieczna konfiguracja za pomocą kolekcji urządzeń. Zobacz: [Właściwości 1.3 (za pośrednictwem plików)](#13-properties-via-files)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji deviceId, ConfigurationId. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Jest to więc zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywce. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób: <ol><li>Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji.</li><li>Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.</li></ol>

### <a name="12-properties-json-response"></a>1.2 Właściwości (odpowiedź JSON)

Właściwość (identyfikator)|Typ danych|Opis
:---|:---|:---
configurationCategory|Ciąg|Kategoria lub grupowanie, do których należy konfiguracja: Aplikacja, system operacyjny, sieć, konta, kontrolki zabezpieczeń.
configurationId|Ciąg|Unikatowy identyfikator określonej konfiguracji.
configurationImpact|Ciąg|Oceniono wpływ konfiguracji na ogólny wynik konfiguracji (1–10).
configurationName|Ciąg|Nazwa wyświetlana konfiguracji.
configurationSubcategory|Ciąg|Podkategoria lub podgrupowanie, do którego należy konfiguracja. W wielu przypadkach są to określone funkcje.
deviceId|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
deviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
isApplicable|Wartość logiczna|Wskazuje, czy konfiguracja lub zasady mają zastosowanie.
isCompliant|Wartość logiczna|Wskazuje, czy konfiguracja lub zasady są poprawnie skonfigurowane.
isExpectedUserImpact|Wartość logiczna|Wskazuje, czy użytkownik może mieć wpływ na to, czy konfiguracja zostanie zastosowana.
osPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu. Określone systemy operacyjne z odmianami tej samej rodziny, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz Systemy operacyjne i platformy obsługiwane przez program tvm.
osVersion|Ciąg|Konkretną wersję systemu operacyjnego działającego na urządzeniu.
rbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
rbacGroupId|Ciąg|Identyfikator grupy opartej na rolach (RBAC, role based access control).
zalecenieReference|Ciąg|Odwołanie do identyfikatora zalecenia związanego z oprogramowaniem.
timestamp|Ciąg|Ostatni raz konfiguracja była widziana na urządzeniu.

### <a name="13-properties-via-files"></a>1.3 Właściwości (za pośrednictwem plików)

Właściwość (identyfikator)|Typ danych|Opis
:---|:---|:---
Eksportowanie plików|arraystring\[\]|Lista adresów URL pobierania plików z bieżącą migawką organizacji.
GeneratedTime|Ciąg|Godzina wygenerowania eksportu.

## <a name="2-export-software-inventory-assessment"></a>2. Eksportowanie oceny spisu oprogramowania

Zwraca wszystkie zainstalowane oprogramowanie i ich szczegóły na każdym urządzeniu.

### <a name="21-methods"></a>2.1 Metody

|Metoda|Typ danych|Opis|
|:---|:---|:---|
|Ocena eksportu spisu **oprogramowania (odpowiedź JSON)**|Spis oprogramowania według kolekcji urządzeń. Zobacz: [Właściwości 2.2 (odpowiedź JSON)](#22-properties-json-response)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza dla małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników. |
| Eksportowanie oceny spisu oprogramowania **(za pośrednictwem plików)**|Spis oprogramowania według plików urządzeń. Zobacz: [Właściwości 2.3 (za pośrednictwem plików)](#23-properties-via-files)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Jest to więc zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywce. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie danych z usługi Azure Storage w następujący sposób: <ol><li>Wywołaj interfejs API, aby uzyskać listę pobieranych adresów URL wraz z danymi Twojej organizacji</li><li>Pobierz pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.</li></ol> |

### <a name="22-properties-json-response"></a>2.2 Właściwości (odpowiedź JSON)

Właściwość (identyfikator)|Typ danych|Opis
:---|:---|:---
DeviceId|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
DiskPaths|Array[string]|Dowód dysku, że produkt jest zainstalowany na urządzeniu.
EndOfSupportDate|Ciąg|Data zakończenia obsługi tego oprogramowania.
EndOfSupportStatus|Ciąg|Stan zakończenia pomocy technicznej. Mogą zawierać następujące możliwe wartości: Brak, Wersja EOS, Nadchodzące wersja systemu EOS, Oprogramowanie EOS, Nadchodzące oprogramowanie EOS.
NumberOfWeaknesses|Int|Liczba wad tego oprogramowania na tym urządzeniu.
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu; poszczególnych systemów operacyjnych z odmianami tej samej rodziny, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm.
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
rbacGroupId|Ciąg|Identyfikator grupy opartej na rolach (RBAC, role based access control).
RegistryPaths|Array[string]|Dowód rejestru, że produkt jest zainstalowany w urządzeniu.
SoftwareFirstSeenTimestamp|Ciąg|To oprogramowanie było widoczne na urządzeniu po raz pierwszy.
Nazwa_oprogramowania|Ciąg|Nazwa produktu.
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.

### <a name="23-properties-via-files"></a>2.3 Właściwości (za pośrednictwem plików)

Właściwość (identyfikator)|Typ danych|Opis
:---|:---|:---
Eksportowanie plików|arraystring\[\]|Lista adresów URL pobierania plików z bieżącą migawką organizacji.
GeneratedTime|Ciąg|Godzina wygenerowania eksportu.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Ocena luk w zabezpieczeniach oprogramowania w eksporcie

Zwraca wszystkie znane luki w zabezpieczeniach na urządzeniu oraz ich szczegóły dotyczące wszystkich urządzeń.

### <a name="31-methods"></a>3.1 Metody

Metoda|Typ danych|Opis
:---|:---|:---
Ocena luk w zabezpieczeniach oprogramowania **(odpowiedź JSON)**|Kolekcja badania Zobacz: [właściwości 3.2 (odpowiedź JSON)](#32-properties-json-response)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza dla małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników.
Ocena luk w oprogramowaniu **(za pośrednictwem plików)**|Jednostka badania Zobacz: [Właściwości 3.3 (za pośrednictwem plików)](#33-properties-via-files)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Jest to więc zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywce. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób: <ol><li>Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji.</li><li>Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.</li></ol>
**Ocena luk w zabezpieczeniach** oprogramowania eksportu różnicowego **(odpowiedź JSON)**|Kolekcja badań Zobacz: [Eksport 3.4 Properties Delta (odpowiedź JSON)](#34-properties-delta-export-json-response)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId i EventTimestamp. <p> Interfejs API wyciąga dane z Twojej organizacji jako odpowiedzi JSON. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników. Pełna ocena luk w oprogramowaniu (odpowiedź JSON) służy do uzyskania pełnej migawki oceny luk w oprogramowaniu organizacji według urządzenia. Jednak wywołanie interfejsu API eksportu różnicowego jest używane do pobierania tylko zmian, które miały miejsce między wybraną datą a bieżącą datą (wywołaniem interfejsu API różnicy). Zamiast pełnego eksportu z dużą ilością danych za każdym razem będziesz otrzymywać tylko określone informacje dotyczące nowych, stałych i zaktualizowanych luk w zabezpieczeniach. Za pomocą wywołania interfejsu API eksportu różnicowego można również obliczać różne wskaźniki KPI, na przykład "ile luk zostało naprawinych?". lub "ile nowych luk w zabezpieczeniach dodano do mojej organizacji?". <p> Ponieważ wywołanie interfejsu API eksportu różnicowego w przypadku luk w oprogramowaniu zwraca dane tylko dla docelowego zakresu dat, nie jest uznawane za pełne _wyeksportowanie_.

### <a name="32-properties-json-response"></a>3.2 Właściwości (odpowiedź JSON)

Właściwość (identyfikator)|Typ danych|Opis
:---|:---|:---
CveId|Ciąg|Unikatowy identyfikator przypisany do luki w zabezpieczeniach systemu cve (Common Vulnerabilities and Exposures).
CvssScore|Ciąg|Wynik CVSS dla CVE.
DeviceId|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
DiskPaths|Arraystring\[\]|Dowód dysku, że produkt jest zainstalowany na urządzeniu.
ExploitabilityLevel|Ciąg|Poziom wykorzystania tej luki (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Ciąg|Po raz pierwszy cvE tego produktu zostało widziane na urządzeniu.
Identyfikator|Ciąg|Unikatowy identyfikator rekordu.
LastSeenTimestamp|Ciąg|Ostatni czas, gdy cvE było widoczne na urządzeniu.
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu; poszczególnych systemów operacyjnych z odmianami tej samej rodziny, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm.
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
rbacGroupId|Ciąg|Identyfikator grupy opartej na rolach (RBAC, role based access control).
ZalecenieReference|Ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.
RecommendedSecurityUpdate|Ciąg|Nazwa lub opis aktualizacji zabezpieczeń udostępnianej przez dostawcę oprogramowania w celu rozwiązania problemu.
RecommendedSecurityUpdateId|Ciąg|Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikator odpowiednich wytycznych lub artykułów z bazy wiedzy (KB).
Ścieżki rejestru arraystring\[\]|Dowód rejestru, że produkt jest zainstalowany w urządzeniu.
Nazwa_oprogramowania|Ciąg|Nazwa produktu.
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.
VulnerabilitySeverityLevel|Ciąg|Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i dynamicznych czynników, na które wpływa poziom zagrożeń.

### <a name="33-properties-via-files"></a>3.3 Właściwości (za pośrednictwem plików)

Właściwość (identyfikator)|Typ danych|Opis
:---|:---|:---
Eksportowanie plików|arraystring\[\]|Lista adresów URL pobierania plików z bieżącą migawką organizacji.
GeneratedTime|Ciąg|Godzina wygenerowania eksportu.

### <a name="34-properties-delta-export-json-response"></a>3.4 Właściwości (odpowiedź JSON eksportu różnicowego)

Właściwość (identyfikator)|Typ danych|Opis
:---|:---|:---
CveId |Ciąg|Unikatowy identyfikator przypisany do luki w zabezpieczeniach systemu cve (Common Vulnerabilities and Exposures).
CvssScore|Ciąg|Wynik CVSS dla CVE.
DeviceId|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
DiskPaths|Array[string]|Dowód dysku, że produkt jest zainstalowany na urządzeniu.
EventTimestamp|Ciąg|Czas znalezionego zdarzenia różnicowego.
ExploitabilityLevel|Ciąg|Poziom wykorzystania luki (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Ciąg|Po raz pierwszy cvE produktu zostało widziane na urządzeniu.
Identyfikator|Ciąg|Unikatowy identyfikator rekordu.  
LastSeenTimestamp|Ciąg|Ostatni czas, gdy cvE było widoczne na urządzeniu.
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu; poszczególnych systemów operacyjnych z odmianami tej samej rodziny, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm.
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
ZalecenieReference|Ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.
RecommendedSecurityUpdate |Ciąg|Nazwa lub opis aktualizacji zabezpieczeń udostępnianej przez dostawcę oprogramowania w celu rozwiązania problemu.
RecommendedSecurityUpdateId |Ciąg|Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikator odpowiednich wytycznych lub artykułów z bazy wiedzy (KB)
RegistryPaths |Array[string]|Dowód rejestru, że produkt jest zainstalowany w urządzeniu.
Nazwa_oprogramowania|Ciąg|Nazwa produktu.
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.
Stan|Ciąg|**Nowość** (w przypadku nowej luki w zabezpieczeniach wprowadzonej na urządzeniu). **Usunięto** (w przypadku luki, która nie istnieje już na urządzeniu, co oznacza, że została usunięta). **Zaktualizowano** (w przypadku luki w zabezpieczeniach na urządzeniu, które uległo zmianie. Możliwe zmiany to: wynik CVSS, poziom wykorzystania, poziom ważności, DiskPaths, RegistryPaths, RecommendedSecurityUpdate).
VulnerabilitySeverityLevel|Ciąg|Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i dynamicznych czynników, na które wpływa poziom zagrożeń.

## <a name="see-also"></a>Zobacz też

- [Eksportowanie bezpiecznego oceny konfiguracji na urządzenie](get-assessment-secure-config.md)
- [Eksportowanie oceny spisu oprogramowania na urządzenie](get-assessment-software-inventory.md)
- [Ocena luk w zabezpieczeniach oprogramowania na urządzeniu](get-assessment-software-vulnerabilities.md)

Inne powiązane

- [Zagrożenia oparte na czynnikach ryzyka & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
