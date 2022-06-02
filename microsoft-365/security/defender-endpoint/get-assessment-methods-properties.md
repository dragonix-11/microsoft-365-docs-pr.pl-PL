---
title: Eksportowanie metod oceny i właściwości na urządzenie
description: Zawiera informacje o interfejsach API, które ściągają dane "Zarządzanie zagrożeniami i lukami". Istnieją różne wywołania interfejsu API umożliwiające pobieranie różnych typów danych. Ogólnie rzecz biorąc, każde wywołanie interfejsu API zawiera wymagane dane dla urządzeń w organizacji.
keywords: api, apis, export assessment, per device assessment, per machine assessment, vulnerability assessment report, device vulnerability assessment, device vulnerability report, secure configuration assessment, secure configuration report, software vulnerabilities assessment, software vulnerability report, vulnerability report, vulnerability report by machine,
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
ms.openlocfilehash: fc2686b9ef6a30c9c81d7633ce8a59a0454d622d
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838948"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Eksportowanie metod oceny i właściwości na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="api-description"></a>Opis interfejsu API

Zawiera metody i szczegóły właściwości dotyczące interfejsów API, które ściągają dane Zarządzanie zagrożeniami i lukami na poszczególnych urządzeniach. Istnieją różne wywołania interfejsu API umożliwiające pobieranie różnych typów danych. Ogólnie rzecz biorąc, każde wywołanie interfejsu API zawiera wymagane dane dla urządzeń w organizacji.

> [!NOTE]
> O ile nie wskazano inaczej, wszystkie wymienione metody oceny eksportu to **_pełny eksport_** i **_urządzenie_** (określane również jako **_dla każdego urządzenia_**).

Interfejsy API oceny eksportu umożliwiają pobieranie (eksportowanie) różnych typów informacji:

- [1. Eksportowanie oceny bezpiecznych konfiguracji](#1-export-secure-configurations-assessment)
- [2. Eksportowanie oceny spisu oprogramowania](#2-export-software-inventory-assessment)
- [3. Eksportowanie oceny luk w zabezpieczeniach oprogramowania](#3-export-software-vulnerabilities-assessment)

Interfejsy API odpowiadające typom informacji eksportu są opisane w sekcjach 1, 2 i 3.

Każda metoda ma różne wywołania interfejsu API w celu pobrania różnych typów danych. Ponieważ ilość danych może być duża, można pobrać je na dwa sposoby:

- **Odpowiedź JSON**  Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza w _przypadku małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K_. Odpowiedź jest podzielona na strony, więc możesz użyć \@pola odata.nextLink z odpowiedzi, aby pobrać następne wyniki.

- **za pośrednictwem plików** To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne ściąganie większych ilości danych. Dlatego jest to zalecane w przypadku dużych organizacji z ponad 100-K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL umożliwiające pobranie wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobranie wszystkich danych z usługi Azure Storage w następujący sposób:
  - Wywołaj interfejs API, aby uzyskać listę adresów URL pobierania ze wszystkimi danymi organizacji.
  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwórz dane zgodnie z tym, co chcesz.

Dane zbierane przy użyciu "_odpowiedzi JSON_ lub _za pośrednictwem plików_" to bieżąca migawka bieżącego stanu. Nie zawiera danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisywać dane we własnych magazynach danych.

## <a name="1-export-secure-configurations-assessment"></a>1. Eksportowanie oceny bezpiecznych konfiguracji

Zwraca wszystkie konfiguracje i ich stan na poszczególnych urządzeniach.

### <a name="11-methods"></a>Metody 1.1

Metoda|Typ danych|Opis
:---|:---|:---
Eksportowanie oceny bezpiecznej konfiguracji **(odpowiedź JSON)**|Bezpieczna konfiguracja według kolekcji urządzeń. Zobacz: [Właściwości 1.2 (odpowiedź JSON)](#12-properties-json-response)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji identyfikatora DeviceId, ConfigurationId. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza w przypadku małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielona na strony, więc możesz użyć pola @odata.nextLink z odpowiedzi, aby pobrać następne wyniki.
Eksportowanie oceny bezpiecznej konfiguracji **(za pośrednictwem plików)**|Bezpieczna konfiguracja według kolekcji urządzeń. Zobacz: [1.3 Właściwości (za pośrednictwem plików)](#13-properties-via-files)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji identyfikatora DeviceId, ConfigurationId. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne ściąganie większych ilości danych. Dlatego jest to zalecane w przypadku dużych organizacji z ponad 100-K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL umożliwiające pobranie wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobranie wszystkich danych z usługi Azure Storage w następujący sposób: <ol><li>Wywołaj interfejs API, aby uzyskać listę adresów URL pobierania ze wszystkimi danymi organizacji.</li><li>Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwórz dane zgodnie z tym, co chcesz.</li></ol>

### <a name="12-properties-json-response"></a>1.2 Właściwości (odpowiedź JSON)

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
configurationCategory|Ciąg|Kategoria lub grupowanie, do których należy konfiguracja: aplikacja, system operacyjny, sieć, konta, mechanizmy kontroli zabezpieczeń.
configurationId|Ciąg|Unikatowy identyfikator określonej konfiguracji.
configurationImpact|Ciąg|Oceniono wpływ konfiguracji na ogólny wynik konfiguracji (1–10).
Configurationname|Ciąg|Nazwa wyświetlana konfiguracji.
configurationSubcategory|Ciąg|Podkategoria lub podgrupa, do której należy konfiguracja. W wielu przypadkach określone możliwości lub funkcje.
Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
deviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
isApplicable|Bool|Wskazuje, czy konfiguracja lub zasady mają zastosowanie.
isCompliant|Bool|Wskazuje, czy konfiguracja lub zasady są prawidłowo skonfigurowane.
isExpectedUserImpact|Bool|Wskazuje, czy problem dotyczy użytkownika, jeśli konfiguracja zostanie zastosowana.
osPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu. Określone systemy operacyjne z odmianami w tej samej rodzinie, takie jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz Systemy operacyjne i platformy obsługiwane przez program TVM.
Osversion|Ciąg|Określona wersja systemu operacyjnego działającego na urządzeniu.
rbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
rbacGroupId|Ciąg|Identyfikator grupy kontroli dostępu opartej na rolach (RBAC).
recommendationReference|Ciąg|Odwołanie do identyfikatora zalecenia związanego z oprogramowaniem.
Sygnatury czasowej|Ciąg|Ostatni raz konfiguracja była widoczna na urządzeniu.

### <a name="13-properties-via-files"></a>1.3 Właściwości (za pośrednictwem plików)

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
Eksportowanie plików|ciąg tablicy\[\]|Lista adresów URL pobierania plików przechowujących bieżącą migawkę organizacji.
GeneratedTime|Ciąg|Czas wygenerowania eksportu.

## <a name="2-export-software-inventory-assessment"></a>2. Eksportowanie oceny spisu oprogramowania

Zwraca wszystkie zainstalowane oprogramowanie i jego szczegóły na każdym urządzeniu.

### <a name="21-methods"></a>2.1 Metody

|Metoda|Typ danych|Opis|
|:---|:---|:---|
|Eksportowanie oceny spisu oprogramowania **(odpowiedź JSON)**|Spis oprogramowania według kolekcji urządzeń. Zobacz: [Właściwości 2.2 (odpowiedź JSON)](#22-properties-json-response)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName i SoftwareVersion. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza w przypadku małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielona na strony, więc możesz użyć pola @odata.nextLink z odpowiedzi, aby pobrać następne wyniki. |
| Eksportowanie oceny spisu oprogramowania **(za pośrednictwem plików)**|Spis oprogramowania według plików urządzeń. Zobacz: [Właściwości 2.3 (za pośrednictwem plików)](#23-properties-via-files)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName i SoftwareVersion. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne ściąganie większych ilości danych. Dlatego jest to zalecane w przypadku dużych organizacji z ponad 100-K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL umożliwiające pobranie wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie danych z usługi Azure Storage w następujący sposób: <ol><li>Wywoływanie interfejsu API w celu uzyskania listy adresów URL pobierania z danymi organizacji</li><li>Pobierz pliki przy użyciu adresów URL pobierania i przetwórz dane zgodnie z tym, co chcesz.</li></ol> |

### <a name="22-properties-json-response"></a>2.2 Właściwości (odpowiedź JSON)

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
DiskPaths|Tablica[ciąg]|Dysk wskazuje, że produkt jest zainstalowany na urządzeniu.
EndOfSupportDate|Ciąg|Data zakończenia pomocy technicznej dla tego oprogramowania.
EndOfSupportStatus|Ciąg|Stan zakończenia pomocy technicznej. Mogą zawierać następujące możliwe wartości: Brak, wersja systemu EOS, nadchodząca wersja systemu EOS, oprogramowanie EOS, nadchodzące oprogramowanie EOS.
LiczbaOfWeaknesses|Int|Liczba słabych stron tego oprogramowania na tym urządzeniu.
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu; specyficznych systemów operacyjnych z odmianami w tej samej rodzinie, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy tvm.
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
rbacGroupId|Ciąg|Identyfikator grupy kontroli dostępu opartej na rolach (RBAC).
RegistryPaths|Tablica[ciąg]|Rejestr wskazuje, że produkt jest zainstalowany na urządzeniu.
SoftwareFirstSeenTimestamp|Ciąg|Po raz pierwszy to oprogramowanie było widoczne na urządzeniu.
SoftwareName|Ciąg|Nazwa produktu programowego.
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.

### <a name="23-properties-via-files"></a>2.3 Właściwości (za pośrednictwem plików)

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
Eksportowanie plików|ciąg tablicy\[\]|Lista adresów URL pobierania plików przechowujących bieżącą migawkę organizacji.
GeneratedTime|Ciąg|Czas wygenerowania eksportu.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Eksportowanie oceny luk w zabezpieczeniach oprogramowania

Zwraca wszystkie znane luki w zabezpieczeniach na urządzeniu i ich szczegóły dla wszystkich urządzeń.

### <a name="31-methods"></a>Metody 3.1

Metoda|Typ danych|Opis
:---|:---|:---
Eksportowanie oceny luk w zabezpieczeniach oprogramowania **(odpowiedź JSON)**|Kolekcja badania Zobacz: [Właściwości 3.2 (odpowiedź JSON)](#32-properties-json-response)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza w przypadku małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K. Odpowiedź jest podzielona na strony, więc możesz użyć pola @odata.nextLink z odpowiedzi, aby pobrać następne wyniki.
Eksportowanie oceny luk w zabezpieczeniach oprogramowania **(za pośrednictwem plików)**|Jednostka badania Zobacz: [3.3 Właściwości (za pośrednictwem plików)](#33-properties-via-files)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne ściąganie większych ilości danych. Dlatego jest to zalecane w przypadku dużych organizacji z ponad 100-K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL umożliwiające pobranie wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobranie wszystkich danych z usługi Azure Storage w następujący sposób: <ol><li>Wywołaj interfejs API, aby uzyskać listę adresów URL pobierania ze wszystkimi danymi organizacji.</li><li>Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwórz dane zgodnie z tym, co chcesz.</li></ol>
Ocena luk w zabezpieczeniach oprogramowania **eksportu różnicowego** **(odpowiedź JSON)**|Kolekcja badań Zobacz: [eksport różnicowy właściwości 3.4 (odpowiedź JSON)](#34-properties-delta-export-json-response)|Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId i EventTimestamp. <p> Interfejs API pobiera dane w organizacji jako odpowiedzi JSON. Odpowiedź jest podzielona na strony, więc możesz użyć pola @odata.nextLink z odpowiedzi, aby pobrać następne wyniki. Pełna ocena luk w zabezpieczeniach oprogramowania (odpowiedź JSON) służy do uzyskania całej migawki oceny luk w zabezpieczeniach oprogramowania organizacji według urządzenia. Jednak wywołanie interfejsu API eksportu różnicowego służy do pobierania tylko zmian, które wystąpiły między wybraną datą a bieżącą datą (wywołanie interfejsu API "delta"). Zamiast za każdym razem uzyskiwać pełny eksport z dużą ilością danych, uzyskasz tylko konkretne informacje o nowych, stałych i zaktualizowanych lukach w zabezpieczeniach. Wywołanie interfejsu API eksportowania różnic może być również używane do obliczania różnych wskaźników KPI, takich jak "ile luk w zabezpieczeniach zostało naprawionych?" lub "ile nowych luk w zabezpieczeniach dodano do mojej organizacji?" <p> Ponieważ wywołanie interfejsu API eksportowania różnic dla luk w zabezpieczeniach oprogramowania zwraca dane tylko dla docelowego zakresu dat, nie jest ono uważane za _pełny eksport_.

### <a name="32-properties-json-response"></a>3.2 Właściwości (odpowiedź JSON)

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
CveId|Ciąg|Unikatowy identyfikator przypisany do luki w zabezpieczeniach w systemie Common Vulnerabilities and Exposures (CVE).
CvssScore|Ciąg|Wynik CVSS CVE.
Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
DiskPaths|Ciąg tablicy\[\]|Dysk wskazuje, że produkt jest zainstalowany na urządzeniu.
ExploitabilityLevel|Ciąg|Poziom wykorzystania tej luki w zabezpieczeniach (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Ciąg|Po raz pierwszy cve tego produktu był widoczny na urządzeniu.
Id|Ciąg|Unikatowy identyfikator rekordu.
LastSeenTimestamp|Ciąg|Ostatni raz cve był widoczny na urządzeniu.
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu; specyficznych systemów operacyjnych z odmianami w tej samej rodzinie, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy tvm.
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
rbacGroupId|Ciąg|Identyfikator grupy kontroli dostępu opartej na rolach (RBAC).
ZalecenieReferencja|Ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.
RecommendedSecurityUpdate|Ciąg|Nazwa lub opis aktualizacji zabezpieczeń udostępnionej przez dostawcę oprogramowania w celu rozwiązania problemu z luką w zabezpieczeniach.
RecommendedSecurityUpdateId|Ciąg|Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikatora odpowiednich wskazówek lub artykułów baza wiedzy (KB).
Ciąg tablicy\[ścieżki rejestru\]|Rejestr wskazuje, że produkt jest zainstalowany na urządzeniu.
SoftwareName|Ciąg|Nazwa produktu programowego.
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.
VulnerabilitySeverityLevel|Ciąg|Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i czynników dynamicznych, na które wpływa poziom zagrożenia.

### <a name="33-properties-via-files"></a>3.3 Właściwości (za pośrednictwem plików)

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
Eksportowanie plików|ciąg tablicy\[\]|Lista adresów URL pobierania plików przechowujących bieżącą migawkę organizacji.
GeneratedTime|Ciąg|Czas wygenerowania eksportu.

### <a name="34-properties-delta-export-json-response"></a>3.4 Właściwości (odpowiedź JSON eksportu różnicowego)

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
CveId |Ciąg|Unikatowy identyfikator przypisany do luki w zabezpieczeniach w systemie Common Vulnerabilities and Exposures (CVE).
CvssScore|Ciąg|Wynik CVSS CVE.
Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
DiskPaths|Tablica[ciąg]|Dysk wskazuje, że produkt jest zainstalowany na urządzeniu.
EventTimestamp|Ciąg|Czas znalezienia zdarzenia różnicowego.
ExploitabilityLevel|Ciąg|Poziom wykorzystania luki w zabezpieczeniach (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Ciąg|Po raz pierwszy cve produktu był widoczny na urządzeniu.
Id|Ciąg|Unikatowy identyfikator rekordu.  
LastSeenTimestamp|Ciąg|Ostatni raz cve był widoczny na urządzeniu.
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu; specyficznych systemów operacyjnych z odmianami w tej samej rodzinie, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy tvm.
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
ZalecenieReferencja|Ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.
RecommendedSecurityUpdate |Ciąg|Nazwa lub opis aktualizacji zabezpieczeń udostępnionej przez dostawcę oprogramowania w celu rozwiązania problemu z luką w zabezpieczeniach.
RecommendedSecurityUpdateId |Ciąg|Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikatora odpowiednich wskazówek lub artykułów baza wiedzy (KB)
RegistryPaths |Tablica[ciąg]|Rejestr wskazuje, że produkt jest zainstalowany na urządzeniu.
SoftwareName|Ciąg|Nazwa produktu programowego.
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.
Stan|Ciąg|**Nowość** (dla nowej luki w zabezpieczeniach wprowadzonej na urządzeniu). **Naprawiono** (w przypadku luki w zabezpieczeniach, która nie istnieje już na urządzeniu, co oznacza, że została skorygowana). **Zaktualizowano** (w przypadku luki w zabezpieczeniach na urządzeniu, które uległo zmianie. Możliwe zmiany to: wynik CVSS, poziom możliwości wykorzystania, poziom ważności, DiskPaths, RegistryPaths, RecommendedSecurityUpdate).
VulnerabilitySeverityLevel|Ciąg|Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i czynników dynamicznych, na które wpływa poziom zagrożenia.

## <a name="see-also"></a>Zobacz też

- [Eksportowanie oceny bezpiecznej konfiguracji na urządzenie](get-assessment-secure-config.md)
- [Eksportowanie oceny spisu oprogramowania na urządzenie](get-assessment-software-inventory.md)
- [Eksportowanie oceny luk w zabezpieczeniach oprogramowania na urządzenie](get-assessment-software-vulnerabilities.md)

Inne powiązane

- [& zarządzanie lukami w zabezpieczeniach zagrożeń opartych na ryzyku](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
