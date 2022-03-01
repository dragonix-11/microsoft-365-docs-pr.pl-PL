---
title: Definicje jednostki typu informacji poufnych
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Istnieje wiele typów informacji poufnych, które są gotowe do użycia w Twoich zasadach ochrony przed prywatnością. W tym artykule wymieniono wszystkie te typy informacji poufnych oraz pokazano, co wyszukuje zasady DLP po wykryciu każdego typu.
ms.openlocfilehash: a3d2592af6b7692b5a5e634947deb811412b5650
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015383"
---
# <a name="sensitive-information-type-entity-definitions"></a>Definicje jednostki typu informacji poufnych

W tym artykule wymieniono wszystkie definicje encji typu informacji poufnych. Każda definicja pokazuje, co zasady DLP wyszukuje do wykrycia poszczególnych typów. Aby dowiedzieć się więcej o typach informacji poufnych, zobacz [Typy informacji poufnych.](sensitive-information-type-learn-about.md)

> [!NOTE]
> Mapowanie poziomu ufności (wysokie/średnie/niskie) z liczbą dokładności (wartość liczbowa od 1 do 100)
> - Niska pewność: co najmniej 65
> - Średnia ufność: 75
> - Wysoka pewność: 85


## <a name="aba-routing-number"></a>Numer routingu ABA

### <a name="format"></a>Formatowanie

Dziewięć cyfr, które mogą być sformatowane lub niesformatowane

### <a name="pattern"></a>Deseń

- dwie cyfry w zakresach 00-12, 21-32, 61-72 lub 80
- dwie cyfry
- Łącznik opcjonalny
- cztery cyfry
- Łącznik opcjonalny
- cyfra


### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady mają średnią pewność, że wykrywany jest ten typ informacji poufnych, jeśli w odległości 300 znaków:
- Funkcja Func_aba_routing znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_ABA_Routing.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_aba_routing znajdzie zawartość, która pasuje do wzorca.

```xml
    <!-- ABA Routing Number -->
    <Entity id="cb353f78-2b72-4c3c-8827-92ebe4f69fdf" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_aba_routing" />
        <Match idRef="Keyword_ABA_Routing" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_aba_routing" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- Numer aba
- aba #
- aba
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- bankrouting #
- bankroutingnumber
- routing #
- routing nie
- numer routingu
- przekieruj numer komunikacji miejskiej
- routing #
- RTN


## <a name="all-full-names"></a>Wszystkie imiona i nazwiska

Wszystkie imiona i nazwiska to encją o nazwie powiązanej z pakietem. Wykrywa ono imiona i nazwiska osób ze wszystkich obsługiwanych krajów/regionów, w tym Australii, Chin, Japonii, Stanów Zjednoczonych i krajów Unii Europejskiej. Użyj tej funkcji SIT, aby wykryć wszystkie możliwe dopasowania pełnych imion i nazwisk.

### <a name="format"></a>Formatowanie

Różne.

### <a name="pattern"></a>Deseń

Różne.

### <a name="checksum"></a>Checksum

L.p.

### <a name="description"></a>Opis

Nazwana jednostka SIT jest taka sama jak nazwa osobista, która zostałaby przez człowieka zidentyfikowania jako nazwa z dużą pewnością. Jeśli na przykład ciąg składający się z danego imienia i nazwiska oraz po nim następuje nazwisko rodziny, to dopasowanie zostanie dokonane bez obaw. Są w nim używane trzy zasoby podstawowe:

-   Słownik o podanych nazwach.
-   Słownik imion i nazwisk rodzinnych.
-   Wzorce formowania nazw.

Te trzy zasoby różnią się w zależności od kraju.  Ciągi *OliviaDam może* wyzwolić dopasowanie. Popularne imiona lub nazwiska osób z rodziny są nadano większą pewność niż rzadko spotykane imiona i nazwiska. Wzorzec dopuszcza jednak także częściowo takie dopasowania. Jeśli zostanie znalezione imię i nazwisko ze słownika, a po nim nazwa rodziny, której nie ma w słowniku, zostanie wyzwolone dopasowanie częściowe. Na przykład *Tomasz Tomasz* wyzwoli dopasowanie częściowe. Częściowe dopasowania mają niższy poziom ufności.

Ponadto wzorce, które ludzie zobaczą jako zrównanie imion i nazwisk, również zostaną do siebie dopasowane z odpowiednią pewnością. Like *O. Dryc*, *O.P. Dry,* *Dr. O. P. Chylik*, *Czerń, O.P.* lub *T. Ryszard, Jun.* zostałby dopasowaniami.

### <a name="supported-languages"></a>Obsługiwane języki

- English
- Bulgarian
- Chiński
- Croatian
- Czech
- Danish
- Estonian
- Finnish
- French
- German
- Hungarian
- Islandzki
- Irlandzki
- Italian
- Japanese
- Latvian
- Lithuanian
- Maltański
- Dutch
- Norweski
- Polish
- Portugalski
- Romanian
- Slovak
- Slovenian
- Spanish
- Swedish
- Turkish


## <a name="all-medical-terms-and-conditions"></a>Wszystkie warunki medyczne

Wszystkie warunki medyczne są jednostką podaną w pakiecie, która wykrywa warunki medyczne i medyczne. Wykrywa ona tylko terminy w języku angielskim. Skorzystaj z tej usługi SIT do wykrywania wszystkich możliwych przepisów medycznych.

### <a name="format"></a>Formatowanie

Słownik

### <a name="pattern"></a>Deseń

Słownik

### <a name="checksum"></a>Checksum

Nie

### <a name="description"></a>Opis

Ta nazwana jednostka w pakiecie odpowiada tekstowi, który zawiera wzmianki o stanach medycznych obecnych w słownikach. Dla każdego obsługiwanego języka jest obsługiwany jeden słownik. Słowniki znajdują się w wielu międzynarodowych zasobach medycznych. Słowniki zawierają możliwie najwięcej warunków medycznych, nie ryzykując dużej liczby wyników fałszywie dodatnich. Każda pozycja zawiera różne formularze, w których często występuje pojedynczy warunek w celu zapewnienia zasięgu, na przykład:

- *TB*
- *szamigie*
- *phthisis pulmonalis*

### <a name="contains"></a>Zawiera

Ten dołączony nazwany podmiot SIT zawiera te poszczególne identyfikatory SIT.

- Warunki testowania krwi 
- Typy leki
- Wołoń
- Ogólne nazwy leki
- Niepełnosprawności wymienione w U.S. Disability Evaluation Under Social Security
- Warunki testowania laboratorium
- Style życia związane ze stanem zdrowia
- Specjalizacja medyczna
- Procedury procedur procedur dotyczących procedur dotyczących procedur
- Nazwy produktów marki


## <a name="all-physical-addresses"></a>Wszystkie adresy fizyczne

Wszystkie adresy fizyczne są powiązanymi elementami SIT, które wykrywają wzorce związane z adresami fizycznymi ze wszystkich obsługiwanych krajów/regionów.

### <a name="format"></a>Formatowanie

Różne

### <a name="pattern"></a>Deseń

Różne

### <a name="checksum"></a>Checksum

Nie

### <a name="description"></a>Opis

Dopasowywanie adresów ulicy jest tak zaprojektowane, aby dopasować ciągi, które może być identyfikowane przez człowieka jako adres pocztowy. W tym celu korzysta on z kilku zasobów podstawowych:

-   Słownik dla rozliczeń, powiatów i regionów.
-   Słownik sufiksów ulicy, na przykład Droga, Ulica lub Szosowy.
-   Wzorce kodów pocztowych.
-   Wzorce formatów adresów.

Zasoby są różne dla poszczególnych krajów. Zasobami podstawowymi są wzorce formatów adresów używanych w danym kraju. Wybierane są różne formaty, aby mieć pewność, że zostanie dopasowana jak najwięcej adresów. Takie formaty pozwalają na elastyczność, na przykład adres może pomijać kod pocztowy, pomijać nazwę miasta lub mieć ulicę bez sufiksu ulicy. We wszystkich przypadkach takie dopasowania są używane w celu zwiększenia pewności co do dopasowania.

Wzorce są zaprojektowane tak, aby dopasować pojedyncze adresy, a nie lokalizacje ogólne. Dlatego ciągi takie jak *Redmond, WA 98052* lub *Main Street, Albuquerque* nie zostaną dopasowane.

### <a name="contains"></a>Zawiera

Ten dołączony nazwany podmiot SIT zawiera następujące poszczególne identyfikatory SIT:

- Adresy fizyczne Australii
- Fizyczne adresy w Austrii
- Adresy fizyczne w Belgia
- Adresy fizyczne w Brazylii
- Adresy fizyczne w Bułgarii
- Adresy fizyczne w Kanadzie
- Chorwacja fizyczne adresy
- Adresy fizyczne cypru
- Adresy fizyczne w Czechach
- Adresy fizyczne w Dania
- Estoński adres fizyczny
- Adresy fizyczne w Finlandia
- Adresy fizyczne we Francji
- Adresy fizyczne w Niemczech
- Grecja ( adresy fizyczne)
- Adresy fizyczne Węgry
- Islandzkie adresy fizyczne
- Adresy fizyczne w Irlandii
- Włochy adresy fizyczne
- Łotewskie adresy fizyczne
- Adresy fizyczne Liechtensteinu
- Adresy fizyczne Litwy
- Adresy fizyczne w Luksemburgu
- Adresy fizyczne malta
- Holenderskie adresy fizyczne
- Nowe adresy fizyczne w Nowej Zelandii
- Adresy fizyczne w Norwegiach
- Adresy fizyczne w Polsce
- Fizyczne adresy w Portugalia
- Adresy fizyczne w Rumunii
- Adresy fizyczne na Słowacja
- Adresy fizyczne w Słowenii
- Adresy fizyczne Hiszpanii
- Szwecja ( adresy fizyczne)
- Adresy fizyczne w Szwajcarii
- Adresy fizyczne w Turcja
- Adresy fizyczne w Zjednoczonym Królestwie
- Adresy fizyczne w Stanach Zjednoczonych

### <a name="supported-languages"></a>Obsługiwane języki

- English
- Bulgarian
- Chiński
- Croatian
- Czech
- Danish
- Estonian
- Finnish
- French
- German
- Hungarian
- Islandzki
- Irlandzki
- Italian
- Japanese
- Latvian
- Lithuanian
- Maltański
- Dutch
- Norweski
- Polish
- Portugalski
- Romanian
- Slovak
- Slovenian
- Spanish
- Swedish
- Turkish


## <a name="argentina-national-identity-dni-number"></a>Numer tożsamości państwowej Argentyny (DNI)

### <a name="format"></a>Formatowanie

Osiem cyfr z kropkami lub bez kropek

### <a name="pattern"></a>Deseń

Osiem cyfr:
- dwie cyfry
- okres opcjonalny
- trzy cyfry
- okres opcjonalny
- trzy cyfry

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_argentina_national_id umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z Keyword_argentina_national_id znajduje się.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Argentyna ( numer tożsamości państwowej)
- cedula
- cédula
- dni
- documento nacional de identidad
- documento número
- numero dokumentu
- registro nacional de las personas
- rnp


## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Argentina Unique Tax Identification Key (CUIT/CUIL)

### <a name="format"></a>Formatowanie

11 cyfr z łącznikiem

### <a name="pattern"></a>Deseń

11 cyfr z łącznikiem:
- Dwie cyfry w postaci 20, 23, 24, 27, 30, 33 lub 34
- Łącznik (-)
- osiem cyfr
- Łącznik (-)
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_Argentina_Unique_Tax_Key` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_Argentina_Unique_Tax_Key` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_Argentina_Unique_Tax_Key` zawartość, która odpowiada wzorcowi.

```xml
    <!-- Argentina Unique Tax Identification Key (CUIT/CUIL) -->
      <Entity id="98da3da1-9199-4571-b7c4-b6522980b507" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
          <Match idRef="Keyword_Argentina_Unique_Tax_Key" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- unikatowy kod identyfikacji identyfikatorów na najbłędszej tożsamości 
- Clave Única de Identificación Tributaria
- unikatowy kod identyfikacyjny identyfikatorów
- CUIL
- Unikatowy klucz identyfikacji podatkowej
- Klucz identyfikacyjny unikatowych identyfikatorów
- Unikatowy klucz dowodu tożsamości na najbłędszej tożsamości
- Unikatowy kod identyfikacyjny służbowy
- Unikatowy kod identyfikacyjny pracy
- Unikatowy klucz identyfikacyjny pracy
- Unikatowy klucz identyfikacji pracy
- Unikatowy kod identyfikacji podatkowej
- Unikatowy klucz identyfikacji podatkowej
- Unikatowy kod identyfikacyjny rynku pracy
- Unikatowy kod identyfikacji rynku pracy
- Unikatowy klucz identyfikacji rynku pracy
- Unikatowy klucz identyfikacji rynku pracy
- identyfikator podatku
- taxID #
- taxId
- number
- numer podatku
- nie podatek
- podatek #
- podatek #
- identyfikator vat
- numer identyfikacyjny
- nie
- cycer #
- cycer #
- tożsamość podatkowa
- identyfikacji podatkowej
- Número de Identificación Fiscal
- número de contribuyente


## <a name="australia-bank-account-number"></a>Numer konta bankowego w Australii

### <a name="format"></a>Formatowanie

Od 6 do 10 cyfr z numerem oddziału stanu bankowego lub bez niego

### <a name="pattern"></a>Deseń

Numer konta to od 6 do 10 cyfr.

Numer oddziału banku w Australii:
- trzy cyfry
- Łącznik
- trzy cyfry

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_australia_bank_account_number zawartości, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_australia_bank_account_number.
- Wyrażenie regularne Regex_australia_bank_account_number_bsb umożliwia znalezienie zawartości, która odpowiada wzorcowi.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_australia_bank_account_number zawartości, która jest taka, jak wzorzec.

- Zostanie znalezione słowo kluczowe Keyword_australia_bank_account_number.

```xml
<!-- Australia Bank Account Number -->
<Entity id="74a54de9-2a30-4aa0-a8aa-3d9327fc07c7" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
        <Match idRef="Regex_australia_bank_account_number_bsb" />
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
  </Pattern>
 </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- kod bankowy Swift
- bank korespondenta
- waluta bazowa
- konto w Polsce
- adres posiadacza
- adres bankowy
- konto informacyjne
- Transfery funduszy
- opłaty bankowe
- szczegóły banku
- informacje bankowe
- imię i nazwisko
- iaea


## <a name="australia-business-number"></a>Numer służbowy Australia

Tego typu informacji poufnych można używać tylko w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

11 cyfr z opcjonalnymi ogranicznikami

### <a name="pattern"></a>Deseń

11 cyfr z opcjonalnymi ogranicznikami:

- dwie cyfry
- Łącznik opcjonalny lub spacja
- trzy cyfry
- Łącznik opcjonalny lub spacja
- trzy cyfry
- Łącznik opcjonalny lub spacja
- trzy cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_australian_business_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keywords_australian_business_number.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_australian_business_number znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- Australia Business Number -->
      <Entity id="76e83b3b-01ee-4530-aced-e667a6609f49" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_australian_business_number" />
          <Match idRef="Keywords_australian_business_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_australian_business_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- australia business no
- numer służbowy
- abn #
- businessid #
- identyfikator firmy
- abn
- businessno #


## <a name="australia-company-number"></a>Numer firmy w Australii

Tego typu informacji poufnych można używać tylko w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Dziewięć cyfr z ogranicznikami

### <a name="pattern"></a>Deseń

Dziewięć cyfr z ogranicznikami:

- trzy cyfry
- spacja
- trzy cyfry
- spacja
- trzy cyfry


### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_Australian_Company_Number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z Keyword_Australian_Company_Number znajduje się.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_Australian_Company_Number umożliwia znalezienie zawartości, która odpowiada wzorcowi.

```xml
      <!-- Australia Company Number -->
      <Entity id="b1fba4f7-7b3e-4bb9-8f9a-9366df604dbb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Australian_Company_Number" />
          <Match idRef="Keyword_Australian_Company_Number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_Australian_Company_Number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- może
- australia company no
- australia company no #
- numer firmy Australia
- australian company no
- australian company no #
- numer australijskiej firmy


## <a name="australia-drivers-license-number"></a>Numer prawa jazdy w Australii

### <a name="format"></a>Formatowanie

Dziewięć liter i cyfr

### <a name="pattern"></a>Deseń

dziewięć liter i cyfr:

- Dwie cyfry lub litery (bez wielkości liter)
- dwie cyfry
- Pięć cyfr lub liter (bez wielkości liter)

LUB

- od jednego do dwóch opcjonalnych liter (bez wielkości liter)
- Od czterech do dziewięciu cyfr

LUB

- Dziewięć cyfr lub liter (bez wielkości liter)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_australia_drivers_license_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_australia_drivers_license_number.
- Nie można odnaleźć słowa kluczowego Keyword_australia_drivers_license_number_exclusions.

```xml
<!-- Australia Drivers License Number -->
<Entity id="1cbbc8f5-9216-4392-9eb5-5ac2298d1356" patternsProximity="300" recommendedConfidence="75">
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_drivers_license_number" />
        <Match idRef="Keyword_australia_drivers_license_number" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_australia_drivers_license_number_exclusions" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- międzynarodowe zezwolenia na samochód
- Australijskie skojarzenie samochodów
- międzynarodowe zezwolenie na samochód
- DriverLicence
- DriverLicences
- Lic sterownika
- Licencja sterownika
- Licencje sterowników
- DriversLic
- DriversLicence
- DriversLicences
- Sterowniki Lic
- Kursywa sterowników
- Licencja sterowników
- Licencje sterowników
- Driver'Lic
- Kursywę sterownika
- Prawo jazdy
- Licencje sterownika
- Lic sterownika
- Kursywę sterownika
- Prawo jazdy
- Licencje sterownika
- Lica sterownika
- Kursywę sterownika
- Wiewiązność sterownika
- Prawa jazdy
- Lic sterownika
- Kursywę sterownika
- Prawo jazdy
- Licencje jazdy
- DriverLic #
- DriverLics #
- DriverLicence #
- DriverLicences #
- Lic sterownika #
- Kursywa sterownika #
- Licencja sterownika #
- Licencje sterowników #
- DriversLic #
- DriversLics #
- DriversLicence #
- DriversLicences #
- Sterowniki Lic #
- Kursywa sterowników #
- Licencja sterowników #
- Licencje sterowników #
- Driver'Lic #
- Kursywę sterownika #
- Prawo jazdy #
- Licencje sterownika #
- Lic sterownika #
- Kursywę sterownika #
- Prawo jazdy #
- Licencje sterownika #
- Lica sterownika #
- Kursywę sterownika #
- Wiewiązność sterownika #
- Prawa jazdy #
- Lic sterownika #
- Kursywę sterownika #
- Prawo jazdy #
- Licencje jazdy #

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- aaa
- DriverLicense
- DriverLicenses
- Prawo jazdy
- Licencje na sterownik
- DriversLicense
- DriversLicenses
- Licencja na sterowniki
- Licencje na sterowniki
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Prawa jazdy
- DriverLicense #
- DriverLicenses #
- Prawo jazdy #
- Licencje na sterownik #
- DriversLicense #
- DriversLicenses #
- Licencja na sterowniki #
- Licencje na sterowniki #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Prawa jazdy #


## <a name="australia-medical-account-number"></a>Numer konta medycznego w Australii

### <a name="format"></a>Formatowanie

10–11 cyfr

### <a name="pattern"></a>Deseń

10–11 cyfr:
- Pierwsza cyfra należy do zakresu od 2 do 6
- Trzynastowa cyfra to cyfra kontrolna
- Dziesiąta cyfra jest cyfrą problemu
- 11. cyfra (opcjonalnie) to liczba pojedyncza

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_australian_medical_account_number znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_Australia_Medical_Account_Number znajduje się.
- Pomyślnie przejdzie sprawdzanie.


```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- szczegóły konta bankowego
- płatności w mediach internetowych
- konto kredytów hipotecznych
- płatności bankowe
- Gałąź informacji
- pożyczka na kartę kredytową
- Dział usług ludzkich
- usługa lokalna
- medicare


## <a name="australia-passport-number"></a>Numer paszportu Australii

### <a name="format"></a>Formatowanie

osiem lub dziewięć znaków alfanumerycznych

### <a name="pattern"></a>Deseń

- jedną literę (N, E, D, F, A, C, U, X) i siedem cyfr lub
- Dwie litery (PA, PB, PC, PD, PE, PF, PU, PW, PX, PZ) i siedem cyfr.

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_australia_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_australia_passport_number` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_australia_passport_number` znalezienie zawartości, która odpowiada wzorcowi.

```xml
    <!-- Australia Passport Number -->
    <Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Match idRef="Keyword_australia_passport_number" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_australia_passport_number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów
- szczegóły paszportu
- Szybka i pociesie
- commonwealth of australia
- oddział ds. migracji
- national identity card
- dokument podróży
- urząd wydania


## <a name="australia-physical-addresses"></a>Adresy fizyczne Australii 

Nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Australii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności
średni


## <a name="australia-tax-file-number"></a>Numer pliku podatkowego w Australii

### <a name="format"></a>Formatowanie

od ośmiu do dziewięciu cyfr

### <a name="pattern"></a>Deseń

Od ośmiu do dziewięciu cyfr zazwyczaj prezentowanych ze spacjami w następujący sposób:
- trzy cyfry
- spacja opcjonalna
- trzy cyfry
- spacja opcjonalna
- od dwóch do trzech cyfr, gdzie ostatnia cyfra to cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_australian_tax_file_number znajdzie zawartość, która pasuje do wzorca.
- Nie można odnaleźć słowa kluczowego Keyword_Australia_Tax_File_Number Keyword_number_exclusions słowa kluczowego.
- Pomyślnie przejdzie sprawdzanie.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- numer biznesowy w Australii
- stopa podatkowa
- medicare
- numer portfela
- weteranów służb
- podatek od zamiejscowy
- indywidualne ze zwrotu podatku
- numer pliku podatkowego
- tfn


## <a name="austria-drivers-license-number"></a>Numer prawa jazdy w Austrii

### <a name="format"></a>Formatowanie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Wyrażenie regularne umożliwia  `Regex_austria_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_austria_eu_driver's_license_number` znajduje się.

```xml
      <!-- Austria Driver's License Number -->
      <Entity id="682f18ce-44eb-482b-8198-2bcb96a0761e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_austria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver nie s_license_number

- fuhrerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern


## <a name="austria-identity-card"></a>Karta tożsamości Austria

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

24-znakowa kombinacja liter, cyfr i znaków specjalnych

### <a name="pattern"></a>Deseń

24 znaki:

-  22 litery (bez wielkości liter), cyfry, ukośniki odwrotne, ukośniki lub znaki plus

- dwie litery (bez wielkości liter), cyfry, ukośniki odwrotne, ukośniki, znaki plus lub znaki równości

### <a name="checksum"></a>Checksum

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Wyrażenie regularne umożliwia  `Regex_austria_eu_national_id_card` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_austria_eu_national_id_card` kluczowe od.

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- numer tożsamości
- identyfikator narodowy
- personalausweisö österreich


## <a name="austria-passport-number"></a>Numer paszportu Austrii

### <a name="format"></a>Formatowanie

Jedna litera, po której następuje opcjonalna spacja i siedem cyfr

### <a name="pattern"></a>Deseń

Kombinacja jednej litery, siedmiu cyfr i jednej spacji:

- jedna litera (bez wielkości liter)
- jedna spacja (opcjonalnie)
- Siedem cyfr

### <a name="checksum"></a>Checksum

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_austria_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_austria_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_austria_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_austria_eu_passport_number` znajduje się.

```xml
      <!-- Austria Passport Number -->
      <Entity id="1c96ae4e-303b-447d-86c7-77113ac266bf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_austria_eu_passport_number"></a>Keywords_austria_eu_passport_number

- reisepassnummer
- reisepasse
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="austria-physical-addresses"></a>Fizyczne adresy w Austrii

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Austrii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="austria-social-security-number"></a>Austria social security number

### <a name="format"></a>Formatowanie

10 cyfr w określonym formacie

### <a name="pattern"></a>Deseń

10 cyfr:

- Trzy cyfry odpowiadające numerowi kolejnemu
- jedna cyfra kontrolna
- Sześć cyfr odpowiadających dacie urodzenia (DDMMYY)

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_austria_eu_ssn_or_equivalent` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_austria_eu_ssn_or_equivalent` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_austria_eu_ssn_or_equivalent` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Austria Social Security Number -->
      <Entity id="6896a906-86c9-4d19-a2da-6e43ccd19b7b" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_austria_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_austria_eu_telephone_number" />
            <Match idRef="Keywords_austria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- austria ssn
- Numer ehiczny
- nr ehic
- kod ubezpieczeniowy
- kod ubezpieczeniowy #
- numer ubezpieczenia
- brak ubezpieczenia
- kenkassennummer
- kenversicherung
- socialsecurityno
- socialsecurityno #
- nr ubezpieczenia społecznego
- numer PEZEt
- kod peł.
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- ssn #
- ssn
- versicherungscode
- versicherungsnummer
- zdravsvstv zavarovanje


## <a name="austria-tax-identification-number"></a>Numer identyfikacyjny podatku w Austrii

### <a name="format"></a>Formatowanie

Dziewięć cyfr z opcjonalnym łącznikiem i ukośnikiem do przodu

### <a name="pattern"></a>Deseń

Dziewięć cyfr z opcjonalnym łącznikiem i ukośnikiem do przodu:

- dwie cyfry
- Łącznik (opcjonalny)
- trzy cyfry
- ukośnik (opcjonalny)
- cztery cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_austria_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_austria_eu_tax_file_number` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_austria_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Austria Tax Identification Number -->
      <Entity id="4fd58d22-af28-4451-b18a-6f722430a56d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
          <Match idRef="Keywords_austria_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- österreich
- st.nr.
- steuernummer
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- numer podatku


## <a name="austria-value-added-tax"></a>Podatek od wartości dodanej w Austrii

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

11-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

11-znakowy wzorzec alfanumeryczny:

- A lub a
- T lub t
- Spacja opcjonalna
- U lub u
- spacja opcjonalna
- dwie lub trzy cyfry
- spacja opcjonalna
- cztery cyfry
- spacja opcjonalna
- jedna lub dwie cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_Austria_Value_Added_Tax znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_Austria_Value_Added_Tax.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_Austria_Value_Added_Tax znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- Austria Value Added Tax -->
      <Entity id="b6a3eda2-c56c-4b69-a5f7-dca34db00f48" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
          <Match idRef="Keyword_Austria_Value_Added_Tax" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- numer VAT
- vat #
- Austria numer VAT
- nie vat.
- vatno #
- numer podatku dodanego
- Austria VAT
- mjst
- umsatzsteuernummer
- mistnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- numer identyfikacyjny VAT
- liczba atu
- numer uid


## <a name="azure-documentdb-auth-key"></a>Klucz uwierzytelniania dokumentu Azure DocumentDB

### <a name="format"></a>Formatowanie

Ciąg "DocumentDb" oraz znaki i ciągi opisane w poniższym wzorcu.

### <a name="pattern"></a>Deseń

- Ciąg "DocumentDb"
- Dowolna kombinacja od 3 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- Symbol większy niż (>), znak równości (=), cudzysłów (") lub apostrof (')
- Dowolna kombinacja 86 małych i wielkich liter, cyfr, ukośnika (/) lub znaku plus (+)
- Dwa znaki równości (=)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzureDocumentDBAuthKey umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości, która pasuje do wzorca.

```xml
<!-- Azure Document DB Auth Key -->
<Entity id="0f587d92-eb28-44a9-bd1c-90f2892b47aa" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureDocumentDBAuthKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
          </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Z technicznego punktu widzenia ten typ informacji poufnych identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- contoso
- fabrikam
- northwind
- piaskownica
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Azure IAAS database connection string and Azure SQL connection string

### <a name="format"></a>Formatowanie

Ciąg "Serwer", "serwer" lub "źródło danych" oraz znaki i ciągi opisane w poniższym wzorcu, łącznie z ciągiem "cloudapp.azure.<!--no-hyperlink-->com" lub "cloudapp.azure.<!--no-hyperlink-->net" lub "database.windows.<!--no-hyperlink-->net", a także ciąg "Password" lub "password" lub "pwd".

### <a name="pattern"></a>Deseń

- ciąg "Serwer", "serwer" lub "źródło danych"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- Ciąg "cloudapp.azure.<!--no-hyperlink-->com", "cloudapp.azure.<!--no-hyperlink-->net" lub "database.windows.<!--no-hyperlink-->net"
- dowolna kombinacja od 1 do 300 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "Password", "password" lub "pwd"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- jeden lub więcej znaków innych niż średnik (;) cudzysłów (") lub apostrof (')
- średnik (;), cudzysłów (") lub apostrof (')

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzureConnectionString zawartości, która jest taka, jak wzorzec.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości, która pasuje do wzorca.

```xml
<!--Azure IAAS Database Connection String and Azure SQL Connection String-->
<Entity id="ce1a126d-186f-4700-8c0c-486157b953fd" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Z technicznego punktu widzenia ten typ informacji poufnych identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- contoso
- fabrikam
- northwind
- piaskownica
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-iot-connection-string"></a>Azure IoT connection string

### <a name="format"></a>Formatowanie

Ciąg "HostName" oraz znaki i ciągi opisane w poniższym wzorcu, łącznie z ciągami "azure-devices.<!--no-hyperlink-->net" i "SharedAccessKey".

### <a name="pattern"></a>Deseń

- ciąg "HostName"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "azure-devices.<!--no-hyperlink-->net"
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "SharedAccessKey"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja 43 małych i wielkich liter, cyfr, ukośnika (/) lub znaku plus (+)
- znak równości (=)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzureIoTConnectionString umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości, która pasuje do wzorca.

```xml
<!--Azure IoT Connection String-->
<Entity id="0b34bec3-d5d6-4974-b7b0-dcdb5c90c29d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureIoTConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Ten poufny typ informacji identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- contoso
- fabrikam
- northwind
- piaskownica
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-publish-setting-password"></a>Azure Publish setting password

### <a name="format"></a>Formatowanie

Ciąg "userpwd=" i ciąg alfanumeryczny.

### <a name="pattern"></a>Deseń

- ciąg "userpwd="
- Dowolna kombinacja 60 małych liter lub cyfr
- Cudzysłów (")

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzurePublishSettingPasswords umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości, która pasuje do wzorca.


```xml
<!--Azure Publish Setting Password-->
<Entity id="75f4cc8a-a68e-49e5-89ce-fa8f03d286a5" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
       <IdMatch idRef="CEP_Regex_AzurePublishSettingPasswords" />
       <Any minMatches="0" maxMatches="0">
           <Match idRef="CEP_CommonExampleKeywords" />
       </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Ten poufny typ informacji identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- contoso
- fabrikam
- northwind
- piaskownica
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-redis-cache-connection-string"></a>Azure Redis connection string

### <a name="format"></a>Formatowanie

Ciąg "redis.cache.windows.<!--no-hyperlink-->net" oraz znaki i ciągi opisane w poniższym wzorcu, łącznie z ciągiem "hasło" lub "pwd".

### <a name="pattern"></a>Deseń

- ciąg "redis.cache.windows.<!--no-hyperlink-->net"
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "password" lub "pwd"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja 43 znaków, które są małymi i górnymi literami, cyframi, ukośnikiem (/) lub znakiem plus (+)
- znak równości (=)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzureRedisCacheConnectionString umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości, która pasuje do wzorca.

```xml
<!--Azure Redis Cache Connection String-->
<Entity id="095a7e6c-efd8-46d5-af7b-5298d53a49fc" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureRedisCacheConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Z technicznego punktu widzenia ten typ informacji poufnych identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- contoso
- fabrikam
- northwind
- piaskownica
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>Formatowanie

Ciąg "sig" oraz znaki i ciągi opisane poniżej.

### <a name="pattern"></a>Deseń

- ciąg "sig"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja znaków od 43 do 53, małych lub wielkich liter, cyfr lub znaku procentu (%)
- ciąg "%3d"
- dowolny znak, który nie jest znakiem małej ani wielkiej litery, cyfrą lub znakiem procentu (%)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzureSAS umożliwia znalezienie zawartości, która odpowiada wzorcowi.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Parametrów połączenia autobusu usług platformy Azure

### <a name="format"></a>Formatowanie

Ciąg "EndPoint" oraz znaki i ciągi opisane w poniższym wzorcu, łącznie z ciągami "servicebus.windows.<!--no-hyperlink-->net" i "SharedAccesKey".

### <a name="pattern"></a>Deseń

- ciąg "EndPoint"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "servicebus.windows.<!--no-hyperlink-->net"
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "SharedAccessKey"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja 43 znaków, które są małymi i górnymi literami, cyframi, ukośnikiem (/) lub znakiem plus (+)
- znak równości (=)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzureServiceBusConnectionString umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości, która pasuje do wzorca.

```xml
<!--Azure Service Bus Connection String-->
<Entity id="b9a6578f-a83f-4fcd-bf44-2130bae49a6f" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureServiceBusConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Z technicznego punktu widzenia ten typ informacji poufnych identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- contoso
- fabrikam
- northwind
- piaskownica
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-storage-account-key"></a>Klucz konta magazynu platformy Azure

### <a name="format"></a>Formatowanie

Ciąg "DefaultEndpointsProtocol" oraz znaki i ciągi opisane poniżej, łącznie z ciągiem "KluczDla Klienta".

### <a name="pattern"></a>Deseń

- ciąg "DefaultEndpointsProtocol"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "Klucz Klienta"
- od zera do dwóch znaków białych
- znak równości (=)
- od zera do dwóch znaków białych
- dowolna kombinacja 86 znaków, które są małymi i małymi literami, cyframi, ukośnikiem (/) lub znakiem plus (+)
- dwa znaki równości (=)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzureStorageAccountKey umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Wyrażenie regularne CEP_AzureEmulatorStorageAccountFilter nie znajduje zawartości, która pasuje do wzorca.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości, która pasuje do wzorca.

```xml
<!--Azure Storage Account Key-->
<Entity id="c7bc98e8-551a-4c35-a92d-d2c8cda714a7" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_AzureEmulatorStorageAccountFilter" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

Z technicznego punktu widzenia ten typ informacji poufnych identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Z technicznego punktu widzenia ten typ informacji poufnych identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- contoso
- fabrikam
- northwind
- piaskownica
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-storage-account-key-generic"></a>Klucz Storage konta usługi Azure (generic)

### <a name="format"></a>Formatowanie

Dowolna kombinacja 86 małych i wielkich liter, cyfr, ukośnika (/) lub znaku plus (+), poprzedzonych lub poprzedzonych znakami opisanymi poniżej.

### <a name="pattern"></a>Deseń

- zero do jednego z symboli większych niż (>), apostrof ('), znak równości (=), cudzysłów (") lub znak numeru (#)
- dowolna kombinacja 86 znaków, które są małymi lub małymi literami, cyframi, ukośnikiem (/) lub znakiem plus (+)
- dwa znaki równości (=)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_AzureStorageAccountKeyGeneric umożliwia znalezienie zawartości, która jest taka, jak wzorzec.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```


## <a name="belgium-drivers-license-number"></a>Numer prawa jazdy w Belgia

### <a name="format"></a>Formatowanie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

10 cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_belgium_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z `Keywords_eu_driver's_license_number` lub `Keywords_belgium_eu_driver's_license_number` znajduje się.

```xml
      <!-- Belgium Driver's License Number -->
      <Entity id="d89fd329-9324-433c-b687-2c37bd5166f3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_belgium_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver nie s_license_number

- rijbewijs
- rijbewijsnummer
- führerschein
- führerscheinnummer
- füehrerscheinnummer
- fuhrerschein
- fuehrerschein
- fuhrerscheinnummer
- fuehrerscheinnummer
- permis de conduire
- numéro permis conduire


## <a name="belgium-national-number"></a>Numer krajowy w Belgia

### <a name="format"></a>Formatowanie

11 cyfr i opcjonalne ograniczniki

### <a name="pattern"></a>Deseń

11 cyfr i ograniczniki:
- Sześć cyfr i dwa opcjonalne kropki w formacie YYY. MM.DD dla daty urodzenia
- Opcjonalny ogranicznik od kropki, kreski, spacji
- Trzy kolejne cyfry (nieparzyste dla mężczyzn, nawet dla kobiet)
- Opcjonalny ogranicznik od kropki, kreski, spacji
- dwie cyfry sprawdzania

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_belgium_national_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_belgium_national_number.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_belgium_national_number znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Belgium National Number -->
       <Entity id="fb969c9e-0fd1-4b18-8091-a2123c5e6a54" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_national_number" />
          <Match idRef="Keyword_belgium_national_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_belgium_national_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- aantal
- bnn #
- bnn
- carte d'identité
- identyfikant national
- identifiantnational #
- identificatie
- identyfikacja
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- tożsamość
- 2016
- numer krajowy
- rejestr narodowy
- numer_narodowy #
- numer_narodowy
- nif #
- nif
- numéro d'assuré
- numéro de registre national
- numéro de sécurité
- numéro d'identification
- numéro d'immatriculation
- numéro national
- numéronational #
- identyfikator osobisty
- personalausweis
- numer_osobisty #
- registratie
- rejestracja
- registrationsnumme
- registrierung
- numer PEZEt
- ssn #
- ssn
- steuernummer
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="belgium-passport-number"></a>Numer paszportu w Belgia

### <a name="format"></a>Formatowanie

Dwie litery, po których następuje sześć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Dwie litery i sześć cyfr po nim

### <a name="checksum"></a>Checksum

nie dotyczy

### <a name="definition"></a>Definicja

 Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_belgium_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_belgium_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date2` datę w formacie DD MM YY lub słowo kluczowe od `Keywords_eu_passport_date` lub `Keywords_belgium_eu_passport_number` znajduje się

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_belgium_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_belgium_eu_passport_number` znajduje się.

```xml
      <!-- Belgium Passport Number -->
      <Entity id="d7b1315b-21ca-4774-a32a-596010ff78fd" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
            <Match idRef="Keywords_belgium_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- Passeport carte
- Passeport jen
- Pass-Nr
- Passnummer
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="belgium-physical-addresses"></a>Adresy fizyczne w Belgia

Ta nieoznakowana nazwana jednostka wykrywa wzorce związane z adresami fizycznymi z Belgia. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="belgium-value-added-tax-number"></a>Belgia: numer podatku dodanego

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

12-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

12-znakowy wzorzec alfanumeryczny:

- literę B lub b
- Litera E lub e
- cyfra 0
- Cyfra od 1 do 9
- Opcjonalna kropka lub łącznik albo spacja
- cztery cyfry
- Opcjonalna kropka lub łącznik albo spacja
- cztery cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_belgium_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keywords_belgium_value_added_tax_number.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_belgium_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- Belgium Value Added Tax Number -->
      <Entity id="85b5b3c3-f2de-4ae8-ac46-fd3cb38bf9ed" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
          <Match idRef="Keywords_belgium_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
        </Pattern>
      </Entity>
    </Version>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- numer VAT
- bez podatku VAT
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- btw
- btw #
- vat #


## <a name="blood-test-terms"></a>Warunki testowania krwi

Ta nieoznaczona nazwana jednostka wykrywa terminy związane z testami krwi, takie jak *hCG*. Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="brand-medication-names"></a>Nazwy produktów marki

Ta nieoznaowana nazwana jednostka wykrywa nazwy produktów marki, takich jak *Tyleola*. Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)


## <a name="brazil-cpf-number"></a>Numer CPF w Brazylii

### <a name="format"></a>Formatowanie

11 cyfr, które zawierają cyfrę kontrolną i mogą być sformatowane lub niesformatowane

### <a name="pattern"></a>Deseń

Sformatowane:
- trzy cyfry
- okres
- trzy cyfry
- okres
- trzy cyfry
- Łącznik
- Dwie cyfry oznaczane cyframi kontrolnymi

Niesformatowane:
- 11 cyfr, gdzie ostatnie dwie cyfry to cyfry kontrolne

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_brazil_cpf wyszukuje zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_brazil_cpf.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_brazil_cpf wyszukuje zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Brazil CPF Number -->
<Entity id="78e09124-f2c3-4656-b32a-c1a132cd2711" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cpf"/>
     <Match idRef="Keyword_brazil_cpf"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cpf"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- Identyfikacja
- Rejestracja
- Przychód
- Cadastro de Pessoas Físicas
- Imposto
- Identificação
- Inscrição
- Receita


## <a name="brazil-legal-entity-number-cnpj"></a>Numer podmiotu prawnego w Brazylii (CNPJ)

### <a name="format"></a>Formatowanie

14 cyfr, które zawierają numer rejestracji, numer oddziału i sprawdź cyfry oraz ograniczniki

### <a name="pattern"></a>Deseń

14 cyfr i ograniczniki:

- dwie cyfry
- okres
- trzy cyfry
- okres
- trzy cyfry (te pierwsze osiem cyfr to numer rejestracji)
- ukośnik
- Czterocyfrowy numer oddziału
- Łącznik
- Dwie cyfry oznaczane cyframi kontrolnymi

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_brazil_cnpj znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_brazil_cnpj.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_brazil_cnpj znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Brazil Legal Entity Number (CNPJ) -->
<Entity id="9b58b5cd-5e90-4df6-b34f-1ebcc88ceae4" recommendedConfidence="85" patternsProximity="300">
   <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cnpj"/>
     <Match idRef="Keyword_brazil_cnpj"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cnpj"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- National Registry of Legal Entities
- Rejestr podatkowe
- Podmiot prawny
- Podmioty prawne
- Stan rejestracji
- Business
- Company
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- Cadastro Geral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação cadasø
- Inscrição
- Empresa


## <a name="brazil-national-identification-card-rg"></a>Karta identyfikacyjna Brazylii (RG)

### <a name="format"></a>Formatowanie

Rejestr Dla Wołodzie (stary format): Dziewięć cyfr

Registro de Identidade (RIC) (nowy format): 11 cyfr

### <a name="pattern"></a>Deseń

Registro Geral (stary format):
- dwie cyfry
- okres
- trzy cyfry
- okres
- trzy cyfry
- Łącznik
- jedna cyfra jako cyfra sprawdzana

Registro de Identidade (RIC) (nowy format):
- 10 cyfr
- Łącznik
- jedna cyfra jako cyfra sprawdzana

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_brazil_rg znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_brazil_rg znajduje się.
- Pomyślnie przejdzie sprawdzanie.


```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- karta tożsamości
- identyfikator narodowy
- número de rregistro
- registro de Iidentidade
- registro geral
- RG (to słowo kluczowe z rozróżnianą wielkością liter)
- RIC (to słowo kluczowe zróżnicuje wielkość liter)


## <a name="brazil-physical-addresses"></a>Adresy fizyczne w Brazylii

Ta nieoznazona nazwana jednostka wykrywa wzorce związane z adresem fizycznym w Brazylii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="bulgaria-drivers-license-number"></a>Numer prawa jazdy w Bułgarii

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_bulgaria_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_bulgaria_eu_driver's_license_number` znajduje się.

```xml
      <!-- Bulgaria Driver's License Number -->
      <Entity id="66d39258-94c2-43b2-804b-aa312258e54b" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_bulgaria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver nie s_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки


## <a name="bulgaria-passport-number"></a>Numer paszportu Bułgarii

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_bulgaria_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_bulgaria_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_bulgaria_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_bulgaria_eu_passport_number` znajduje się.

```xml
      <!-- Bulgaria Passport Number -->
      <Entity id="f7172b82-c588-4216-845e-4e54e397f29a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт Nie

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="bulgaria-physical-addresses"></a>Adresy fizyczne w Bułgarii

Ta nieoznakowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Bułgarii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="bulgaria-uniform-civil-number"></a>Bułgaria: ujednolicona liczba domowa
Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

10 cyfr bez spacji i ograniczników

- Sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- Dwie cyfry odpowiadające zamówieniu urodzenia
- Jedna cyfra odpowiadająca płci: parzysta cyfra dla mężczyzny i cyfra nieparzysta dla kobiety
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_bulgaria_eu_national_id_card` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_bulgaria_eu_national_id_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_bulgaria_eu_national_id_card` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Bulgaria Uniform Civil Number -->
      <Entity id="100d58b1-0a35-4fb1-aa89-e4a86fb53fcc" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Match idRef="Keywords_bulgaria_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_bulgaria_eu_telephone_number" />
            <Match idRef="Keywords_bulgaria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn #
- bnn
- bucn #
- bucn
- edinen grazhdanski nomer
- egn #
- egn
- numer identyfikacyjny
- identyfikator narodowy
- numer krajowy
- numer_narodowy #
- numer_narodowy
- identyfikator osobisty
- nie osobiste
- numer osobisty
- numer_osobisty #
- numer PEZEt
- ssn #
- ssn
- Jednolity identyfikator cywilny
- nie
- ujednoliwizowany numer domowy
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- unikatowy numer unikatowy dla unikatowego numeru
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- униформ id
- униформ градански id
- униформ граждански не
- униформ граждански номер
- униформграданскиid #
- униформгражданскине. #


## <a name="canada-bank-account-number"></a>Numer konta bankowego w Kanadzie

### <a name="format"></a>Formatowanie

7 lub 12 cyfr

### <a name="pattern"></a>Deseń

Numer konta bankowego w Kanadzie to 7 lub 12 cyfr.

Numer przesyłania konta bankowego w Kanadzie to:
- pięć cyfr
- Łącznik
- trzycyfrowe LUB
- zero "0"
- osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_canada_bank_account_number zawartości, która jest taka, jak wzorzec.
- Słowo kluczowe z Keyword_canada_bank_account_number znajduje się.
- Wyrażenie regularne Regex_canada_bank_account_transit_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_canada_bank_account_number zawartości, która jest taka, jak wzorzec.
- Słowo kluczowe z Keyword_canada_bank_account_number znajduje się.

```xml
<!-- Canada Bank Account Number -->
<Entity id="552e814c-cb50-4d94-bbaa-bb1d1ffb34de" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
        <Match idRef="Regex_canada_bank_account_transit_number" />
   </Pattern>
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- Kanada oszczędza
- Kanada agencja przychodów
- Kanada instytucja finansowa
- formularz bezpośredniej wpłaty
- Kanada
- przedstawiciel prawny
- notaria publiczna
- sz. dla oaths
- świadczenia na opiekę dzieci
- uniwersalna pielęgnacja dziecka
- Kanada z podatkiem od dzieci
- korzyść z podatku od przychodów
- ujednolicony podatek od sprzedaży
- numer ubezpieczenia społecznego
- zwrot podatku dochodu
- korzyść podatkowa dla dzieci
- 2013-0
- numer instytucji
- żądanie wpłaty
- informacje bankowe
- bezpośrednia wpłaty


## <a name="canada-drivers-license-number"></a>Numer prawa jazdy z Kanady

### <a name="format"></a>Formatowanie

Różni się w zależności od prowincji

### <a name="pattern"></a>Deseń

Różne wzorce obejmujące:
- Alberta
- Kolumbia Brytyjska
- Manitoba
- Nowy Brunszwik
- Nowa Fundlandia/Labrador
- Nowa Szkocja
- Ontario
- Wyspa Księcia Edwarda
- Quebec
- Saskatchewan

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_[province_name]_drivers_license_number znajdzie zawartość, która jest taka, jak wzorzec.
- Słowo kluczowe z Keyword_[province_name]_drivers_license_name zostanie znalezione.
- Zostanie znalezione słowo kluczowe Keyword_canada_drivers_license.

```xml
<!-- Canada Driver's License Number -->
    <Entity id="37186abb-8e48-4800-ad3c-e3d1610b3db0" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_alberta_drivers_license_number" />
        <Match idRef="Keyword_alberta_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_british_columbia_drivers_license_number" />
        <Match idRef="Keyword_british_columbia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_manitoba_drivers_license_number" />
        <Match idRef="Keyword_manitoba_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_brunswick_drivers_license_number" />
        <Match idRef="Keyword_new_brunswick_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_newfoundland_labrador_drivers_license_number" />
        <Match idRef="Keyword_newfoundland_labrador_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_nova_scotia_drivers_license_number" />
        <Match idRef="Keyword_nova_scotia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_ontario_drivers_license_number" />
        <Match idRef="Keyword_ontario_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_prince_edward_island_drivers_license_number" />
        <Match idRef="Keyword_prince_edward_island_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_quebec_drivers_license_number" />
        <Match idRef="Keyword_quebec_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_saskatchewan_drivers_license_number" />
        <Match idRef="Keyword_saskatchewan_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- Skrót prowincji, na przykład AB
- Nazwa prowincji, na przykład Alberta

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- DriverLicence
- DriverLicences
- Lic sterownika
- Kursywa sterownika
- Prawo jazdy
- Licencje na sterownik
- Licencja sterownika
- Licencje sterowników
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- Sterowniki Lic
- Kursywa sterowników
- Licencja na sterowniki
- Licencje na sterowniki
- Licencja sterowników
- Licencje sterowników
- Driver'Lic
- Kursywę sterownika
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Licencje sterownika
- Lic sterownika
- Kursywę sterownika
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Licencje sterownika
- Lica sterownika
- Kursywę sterownika
- Prawo jazdy
- Prawa jazdy
- Wiewiązność sterownika
- Prawa jazdy
- Lic sterownika
- Kursywę sterownika
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Licencje jazdy
- Permis de Conduire
- identyfikator
- identyfikatory
- numer identyfikacyjny
- numery identyfikatorów
- idcard #
- identyfikator #s
- karta identyfikatora
- karty identyfikatorów
- idcard
- numer identyfikacyjny
- numery identyfikacyjne
- identyfikacja #
- identyfikator #s
- dowód osobisty
- karty identyfikacyjne
- identyfikacja
- DL #
- DLS #
- CDL #
- CDLS #
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- DriverLicence #
- DriverLicences #
- Lic sterownika #
- Kursywa sterownika #
- Prawo jazdy #
- Licencje na sterownik #
- Prawo jazdy #
- Licencje sterowników #
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- DriversLicence #
- DriversLicences #
- Sterowniki Lic #
- Kursywa sterowników #
- Licencja na sterowniki #
- Licencje na sterowniki #
- Licencja sterowników #
- Licencje sterowników #
- Driver'Lic #
- Kursywę sterownika #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Licencje sterownika #
- Lic sterownika #
- Kursywę sterownika #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Licencje sterownika #
- Lica sterownika #
- Kursywę sterownika #
- Prawo jazdy #
- Prawa jazdy #
- Wiewiązność sterownika #
- Prawa jazdy #
- Lic sterownika #
- Kursywę sterownika #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Licencje jazdy #
- Permis de Conduire #
- identyfikator #
- identyfikatory #
- karta identyfikatora #
- karty identyfikatorów #
- idcard #
- dowód osobisty #
- karty identyfikacyjne #
- identyfikacja #


## <a name="canada-health-service-number"></a>Numer usługi zdrowia w Kanadzie

### <a name="format"></a>Formatowanie

 10 cyfr

### <a name="pattern"></a>Deseń

10 cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_canada_health_service_number umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Słowo kluczowe z Keyword_canada_health_service_number znajduje się.

```xml
<!-- Canada Health Service Number -->
<Entity id="59c0bf39-7fab-482c-af25-00faa4384c94" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_health_service_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_health_service_number" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- numer zdrowia osobistego
- dane pacjenta
- usługi zdrowia
- usługi specjalne
- wypadku samochodowy
- szpitalny
- taksówna
- Wynagrodzenia pracowników
- niepełnosprawność


## <a name="canada-passport-number"></a>Numer paszportu Kanady

### <a name="format"></a>Formatowanie

Dwie wielkie litery i sześć cyfr

### <a name="pattern"></a>Deseń

Dwie wielkie litery i sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_canada_passport_number umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_canada_passport_number Keyword_passport.

```xml
<!-- Canada Passport Number -->
<Entity id="14d0db8b-498a-43ed-9fca-f6097ae687eb" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_passport_number" />
          <Match idRef="Keyword_passport" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- Kanada
- paszport Kanady
- aplikacja paszportu
- zdjęcia paszportu
- certyfikowany tłumacz
- Kanadyjscy mieszkańcy
- czas przetwarzania
- aplikacja do odnawiania

#### <a name="keyword_passport"></a>Keyword_passport

- Numer paszportu
- Numer paszportu
- Paszport #
- Paszport #
- PassportID
- Paszport
- numer paszportu
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n °
- Passeport Non
- Passeport #
- Passeport #
- PasseportNon
- Passeportn °


## <a name="canada-personal-health-identification-number-phin"></a>Numer identyfikacyjny zdrowia osobistego w Kanadzie (PHIN)

### <a name="format"></a>Formatowanie

dziewięć cyfr

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_canada_phin umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Znaleziono co najmniej dwa słowa kluczowe Keyword_canada_phin lub Keyword_canada_provinces słowa kluczowe.

```xml
<!-- Canada PHIN -->
<Entity id="722e12ac-c89a-4ec8-a1b7-fea3469f89db" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_phin" />
        <Any minMatches="2">
          <Match idRef="Keyword_canada_phin" />
          <Match idRef="Keyword_canada_provinces" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- numer ubezpieczenia społecznego
- działania na temat informacji o stanie zdrowia
- Informacje o podatku od przychodów
- kondycja manitoba
- rejestracja zdrowia
- zakupy rezydne
- prawo do korzyści
- kondycja osobista
- pełnomocnictwo
- numer rejestracji
- numer zdrowia osobistego
- polecane polecenia
- fitness professional
- polecenie pacjenta
- kondycja i zdrowie

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- Nunavut
- Quebec
- Terytoria Północno-Zachodnie
- Ontario
- Kolumbia Brytyjska
- Alberta
- Saskatchewan
- Manitoba
- Jukon
- Nowa Fundlandia i Labrador
- Nowy Brunszwik
- Nowa Szkocja
- Wyspa Księcia Edwarda
- Kanada


## <a name="canada-physical-addresses"></a>Adresy fizyczne w Kanadzie

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Kanady. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="canada-social-insurance-number"></a>Kanada numer ubezpieczenia społecznego

### <a name="format"></a>Formatowanie

Dziewięć cyfr z opcjonalnymi łącznikami lub spacjami

### <a name="pattern"></a>Deseń

Sformatowane:
- trzy cyfry
- Łącznik lub spacja
- trzy cyfry
- Łącznik lub spacja
- trzy cyfry

Niesformatowany: dziewięć cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_canadian_sin znajdzie zawartość, która pasuje do wzorca.
- Co najmniej dwa z następujących wzorców:
    - Słowo kluczowe z Keyword_sin znajduje się.
    - Zostanie znalezione słowo kluczowe Keyword_sin_collaborative.
    - Funkcja Func_eu_date znajdzie datę w odpowiednim formacie daty.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_unformatted_canadian_sin znajdzie zawartość, która odpowiada wzorcowi.
- Słowo kluczowe z Keyword_sin znajduje się.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Canada Social Insurance Number -->
<Entity id="a2f29c85-ecb8-4514-a610-364790c0773e" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_canadian_sin" />
        <Any minMatches="2">
          <Match idRef="Keyword_sin" />
          <Match idRef="Keyword_sin_collaborative" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_canadian_sin" />
        <Match idRef="Keyword_sin" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_sin"></a>Keyword_sin

- sin
- ubezpieczenia społecznego
- numero d'assurance sociale
- sins
- ssn
- ssns
- ubezpieczenia społecznego
- numero d'assurance social
- numer identyfikacyjny kraju
- identyfikator narodowy
- sin #
- soc ins
- ins społecznościowych

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- prawo jazdy
- licencja sterowników
- prawo jazdy
- licencja sterowników
- DOB
- DataUrodze
- Urodziny
- Data urodzenia


## <a name="chile-identity-card-number"></a>Numer karty tożsamości chile

### <a name="format"></a>Formatowanie

Od siedmiu do ośmiu cyfr oraz ograniczniki sprawdź cyfrę lub literę

### <a name="pattern"></a>Deseń

Od siedmiu do ośmiu cyfr oraz ograniczniki:
- od jednej do dwóch cyfr
- okres opcjonalny
- trzy cyfry
- okres opcjonalny
- trzy cyfry
- kreska
- jedna cyfra lub litera (bez wielkości liter), która jest cyfrą kontrolną

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_chile_id_card znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_chile_id_card.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_chile_id_card znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Chile Identity Card Number -->
<Entity id="4e979794-49a0-407e-a0b9-2c536937b925" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_chile_id_card"/>
     <Match idRef="Keyword_chile_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_chile_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- identyfikacja państwowa
- numer identyfikacyjny kraju
- identyfikator narodowy
- número de identificación nacional
- rol único nacional
- rol único tributtributtribut
- URUCHOM
- RUT
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributtributtribut
- URUCHOM #
- RUT #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad numero
- Chilean identity no.
- Numer tożsamości Chilean
- Tożsamość chilejska #
- Unikatowy rejestr podatkowy
- Rola unikatowych przypisów
- Unikatowa rola podatku
- Unikatowy numer tributary
- Unikatowy numer krajowy
- Unikatowa rola państwowa
- Unikatowa rola kraju
- Nie tożsamości Chile.
- Numer tożsamości chile
- Tożsamość Chile #
- R.U.T
- R.U.N


## <a name="china-resident-identity-card-prc-number"></a>Numer karty tożsamości w Chinach (Chiny)

### <a name="format"></a>Formatowanie

18 cyfr

### <a name="pattern"></a>Deseń

18 cyfr:
- Sześć cyfr jako kod adresu
- osiem cyfr w postaci RRRRMMDD, czyli data urodzenia
- Trzy cyfry oznaczace kod zamówienia
- jedna cyfra jako cyfra sprawdzana

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_china_resident_id znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_china_resident_id znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_china_resident_id znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- China Resident Identity Card (PRC) Number -->
<Entity id="c92daa86-2d16-4871-901f-816b3f554fc1" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_china_resident_id"/>
     <Match idRef="Keyword_china_resident_id"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_china_resident_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- Rezydentna karta tożsamości
- ChRL
- Państwowa karta identyfikacyjna
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定


## <a name="credit-card-number"></a>Numer karty kredytowej

### <a name="format"></a>Formatowanie

Od 14 do 19 cyfr, które mogą być sformatowane lub niesformatowane (dddddddd), które muszą przejść test Luhna.

### <a name="pattern"></a>Deseń

Wykrywa karty od wszystkich głównych marek na całym świecie, w tym Visa, MasterCard, Discover Card, JCB, American Express, bony upominkowe, karty firmy Diner, Rupay i China UnionPay.

### <a name="checksum"></a>Checksum

Tak, sprawdzanie luhna

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_credit_card umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Prawdziwe jest jedno z następujących argumentów:
    - Słowo kluczowe z Keyword_cc_verification znajduje się.
    - Zostanie znalezione słowo kluczowe Keyword_cc_name.
    - Funkcja Func_expiration_date znajdzie datę w odpowiednim formacie daty.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_credit_card umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Credit Card Number -->
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_credit_card" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- weryfikacja karty
- numer identyfikacyjny karty
- cvn
- cid
- cvc2
- cvv2
- blok przypinania
- kod zabezpieczeń
- numer zabezpieczeń
- brak zabezpieczeń
- numer problemu
- nr problemu
- cryptogramme
- numéro de sécurité
- numero de securite
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- prufziffer
- sicherheits Kode
- sicherheitscode
- sicherheitsnummer
- verfalldatum
- codice di verifica
- cod. sicurezza
- cod sicurezza
- n autorizzazione
- código
- codigo
- cod. seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- cod. seguranca
- cod. segurança
- cód. seguranca
- cód segurança
- cod seguranca
- cod segurança
- cód seguranca
- número de verificação
- numero de verificacao
- ablauf
- gültig bis
- gültigkeitsdatum
- gultig bis
- gultigkeitsdatum
- scadenza
- data scad
- fecha de expiracion
- fecha de venc
- vencimiento
- válido hasta
- valido hasta
- vto
- data de expiração
- data de expiracao
- data em que expira
- validade
- valor
- vencimento
- transakcja
- numer transakcji
- numer referencyjny
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- amex
- American Express
- americanexpress
- americano nin
- Visa
- karta wzorcowa
- karta wzorcowa
- mc
- karty wzorcowe
- karty wzorcowe
- Diner's Club
- Diners Club
- diners z
- odnajdowanie
- karta odnajdowanie
- discovercard
- odnajdowanie kart
- JCB
- Brand Smart
- biuro karty dla języka japońskiego
- carte blanche
- carteblanche
- karta kredytowa
- DW #
- dw#:
- data wygaśnięcia
- data exp
- data wygaśnięcia
- data wygaśnięcia
- date d'exp
- data wygaśnięcia
- karta bankowa
- bankcard
- numer karty
- numer karty
- numer karty
- liczba_kart
- numery kart
- karta kredytowa
- karty kredytowe
- karty kredytowe
- ccn
- posiadacz karty
- cardholder
- właściciele kart
- cardholders
- karta wyboru
- karta kontrolna
- karty wyboru
- karty wyboru
- karta debetowa
- karta debetowa
- karty debetowe
- karty debetowe
- karta atm
- atmcard
- karty atm
- kartki atmcard
- enroute
- en route
- typ karty
- Cardmember Acct
- konto karty
- Cardno
- Karta firmowa
- Wizytówki firmowe
- Typ karty
- numer konta karty
- konto członka karty
- Cardmember Acct.
- nie.
- karta nie
- numer karty
- carte bancaire
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nº de la carte
- nº de carte
- kreditkarte
- karte
- karteninhaber
- kartenin wiadce
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr
- kartennummer
- kreditkartennummer
- kreditkarten-nummer
- carta di credito
- Carta credito
- n. carta
- n carta
- nr. carta
- nr carta
- numero carta
- numero della carta
- numero di carta
- tarjeta credito
- tarjeta de credito
- tarjeta crédito
- tarjeta de crédito
- tarjeta de atm
- tarjeta atm
- tarjeta debito
- tarjeta de debito
- tarjeta débito
- tarjeta de débito
- nº de tarjeta
- nie. de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjetajetiente
- cartão de crédito
- cartão de credito
- cartao de crédito
- cartao de credito
- cartão de débito
- cartao de débito
- cartão de debito
- cartao de debito
- débito automático
- debito automatico
- número do cartão
- numero do cartão
- número do cartao
- numero do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nº do cartão
- nº do cartao
- nº. do cartão
- no do cartão
- no do cartao
- nie. do cartão
- nie. do cartao
- rupay
- płatność union
- unionpay
- Diner's
- diners
- クレジットカード番号
- クレジットカードナンバー
- クレジットカード＃
- クレジットカード
- クレジット
- クレカ
- カード番号
- カードナンバー
- カード＃
- アメックス
- アメリカンエクスプレス
- アメリカン エクスプレス
- Visaカード
- Visa カード
- マスターカード
- マスター カード
- マスター
- ダイナースクラブ
- ダイナース クラブ
- ダイナース
- 有効期限
- 期限
- キャッシュカード
- キャッシュ カード
- カード名義人
- カードの名義人
- カードの名義
- デビット カード
- デビットカード
- 中国银联
- 银联


## <a name="croatia-drivers-license-number"></a>Numer prawa jazdy w Chorwacja

### <a name="format"></a>Formatowanie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Wyrażenie regularne umożliwia  `Regex_croatia_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z `Keywords_eu_driver's_license_number` lub `Keywords_croatia_eu_driver's_license_number` znajduje się.

```xml
      <!-- Croatia Driver's License Number -->
      <Entity id="005b3ef1-47dd-4e68-bb02-c6db484d00f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_croatia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_croatia_eu_drivers_license_number"></a>Keywords_croatia_eu_driver nie s_license_number

- vozačka dozvola
- vozačke dozvole


## <a name="croatia-identity-card-number"></a>Numer karty tożsamości Chorwacja
Ta jednostka jest uwzględniana w informacjach poufnych numeru identyfikacyjnego UE. Jest dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formatowanie

dziewięć cyfr

### <a name="pattern"></a>Deseń

Dziewięć kolejnych cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_croatia_id_card znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_croatia_id_card.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstolski broj gra naana
- master master master number
- nacionalni identifikacijski broj
- numer identyfikacyjny kraju
- oib #
- oib
- osobna iskaznica
- osobni id
- osobni identifikacijski broj
- numer identyfikacyjny
- porezni broj
- porezni identifikacijski broj
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="croatia-passport-number"></a>Numer paszportu Chorwacja

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_croatia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_croatia_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_croatia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_croatia_eu_passport_number` znajduje się.

```xml
      <!-- Croatia Passport Number -->
      <Entity id="7d7a729d-32d8-4204-8d01-d5e6a6c25581" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovova
- br. Putovova
- br putov jen

## <a name="croatia-personal-identification-oib-number"></a>Numer identyfikacyjny OIB (Chorwacja)

### <a name="format"></a>Formatowanie

11 cyfr

### <a name="pattern"></a>Deseń

11 cyfr:
- 10 cyfr
- ostatnia cyfra to cyfra wyboru

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_croatia_oib_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keywords_croatia_eu_tax_file_number.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_croatia_oib_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.

```xml
      <!-- Croatia Personal Identification (OIB) Number -->
      <Entity id="31983b6d-db95-4eb2-a630-b44bd091968d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_croatia_oib_number" />
          <Match idRef="Keywords_croatia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_croatia_oib_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstolski broj gra naana
- master master master number
- nacionalni identifikacijski broj
- numer identyfikacyjny kraju
- oib #
- oib
- osobna iskaznica
- osobni id
- osobni identifikacijski broj
- numer identyfikacyjny
- porezni broj
- porezni identifikacijski broj
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="croatia-physical-addresses"></a>Chorwacja fizyczne adresy

Ta nieoznazona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Chorwacja. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="cyprus-drivers-license-number"></a>Numer licencji cypryjscy

### <a name="format"></a>Formatowanie

12 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

12 cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_cyprus_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_cyprus_eu_driver's_license_number` znajduje się.

```xml
      <!-- Cyprus Driver's License Number -->
      <Entity id="356fa104-f9ac-4aff-a0e4-2e6e65ea06c4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_cyprus_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver nie s_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης


## <a name="cyprus-identity-card"></a>Karta tożsamości cypryjna

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

10 cyfr

### <a name="checksum"></a>Checksum

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_cyprus_eu_national_id_card` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_cyprus_eu_national_id_card` kluczowe od.

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- numer dowodu osobistego
- numer karty tożsamości
- kimlik karti
- numer identyfikacyjny kraju
- identyfikator osobisty
- ταυτοτητασ


## <a name="cyprus-passport-number"></a>Numer paszportu Cypru

### <a name="format"></a>Formatowanie

Jedna litera, po której następuje 6-8 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Jedna litera, po której następuje od sześciu do ośmiu cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_cyprus_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_cyprus_eu_passport_number` znajduje się.
- Wyrażenie regularne umożliwia `Regex_cyprus_eu_passport_date` znalezienie daty w formacie DD/MM/YYYY lub znalezione słowo `Keywords_cyprus_eu_passport_date` kluczowe

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_cyprus_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_cyprus_eu_passport_number` znajduje się.

```xml
      <!-- Cyprus Passport Number -->
      <Entity id="9193e2e8-7f8c-43c1-a274-ac40d651936f" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_cyprus_eu_passport_date" />
            <Match idRef="Keywords_cyprus_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- taksówek
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- Nawiązać Kimli nai
- edytacja numarası
- Aby tego nie było, należy go do tej pory nie skoj
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- wygasa w dniu
- wystawiony dnia


## <a name="cyprus-physical-addresses"></a>Adresy fizyczne cypru

Ta nieoznazona nazwana jednostka wykrywa wzorce związane z adresem fizycznym Cypru. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="cyprus-tax-identification-number"></a>Numer identyfikacji podatkowej cypru
Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Osiem cyfr i jedna litera we wskazanym wzorcu

### <a name="pattern"></a>Deseń

osiem cyfr i jedna litera:

- a "0" lub "9"
- Siedem cyfr
- jedna litera (bez wielkości liter)

### <a name="checksum"></a>Checksum

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_cyprus_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_cyprus_eu_tax_file_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_cyprus_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Cyprus Tax Identification Number -->
      <Entity id="40e64bd9-55f3-4a09-9bd6-1db18dced9dd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
          <Match idRef="Keywords_cyprus_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- identyfikator podatku
- kod identyfikacji podatkowej
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- tic #
- tic
- identyfikator tin
- nie tin
- tin #
- vergi kimlik kodu
- vergi kimlik numarası
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού


## <a name="czech-drivers-license-number"></a>Numer prawa jazdy w języku czeskim

### <a name="format"></a>Formatowanie

Dwie litery i sześć cyfr

### <a name="pattern"></a>Deseń

osiem liter i cyfr:

- Litera "E" (bez wielkości liter)
- Litera
- spacja (opcjonalnie)
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_czech_republic_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_czech_republic_eu_driver's_license_number` znajduje się.

```xml
      <Entity id="86b40d3b-d8ea-4c36-aab0-ef9416a6769c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_czech_republic_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver's_license_number

- dodičskú prúkaz
- zydičské pr 8kazy
- číslo íidičského príkazu
- čísla íidičsk čch pr indyjska


## <a name="czech-passport-number"></a>Numer paszportu czeskiego

### <a name="format"></a>Formatowanie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

osiem cyfr bez spacji i ograniczników

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_czech_republic_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_czech_republic_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_czech_republic_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_czech_republic_eu_passport_number` znajduje się.

```xml
      <!-- Czech Republic Passport Number -->
      <Entity id="7bcd8ce8-5e92-4bbe-bc92-fa669f0369fa" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- ces doní pas
- číslo pasu
- ces doní pasu
- passeport no
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="czech-personal-identity-number"></a>Czeski numer tożsamości osobistej

### <a name="format"></a>Formatowanie

Dziewięć cyfr z opcjonalnym ukośnikiem (stary format) 10 cyfr z opcjonalnym ukośnikiem (nowy format)

### <a name="pattern"></a>Deseń

dziewięć cyfr (stary format):
- Sześć cyfr oznacza datę urodzenia
- Opcjonalny ukośnik
- trzy cyfry

10 cyfr (nowy format):
- Sześć cyfr oznacza datę urodzenia
- Opcjonalny ukośnik
- Cztery cyfry, gdzie ostatnia cyfra to cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja Func_czech_id_card znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_czech_id_card znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja Func_czech_id_card_new_format znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Czech Personal Identity Number -->
      <!-- Czech Personal Identity Number -->
      <Entity id="60c0725a-4eb6-455b-9dda-05d8a7396497" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_czech_id_card" />
          <Match idRef="Keyword_czech_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.3000.000">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Func_czech_id_card_new_format" />
          </Pattern>
        </Version>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- numer urodzenia
- identyfikator Czechy
- czechidno #
- daňové číslo
- identifikační číslo
- nie tożsamości
- numer tożsamości
- identityno #
- identityno
- numer ubezpieczenia
- numer identyfikacyjny kraju
- numer_narodowy #
- numer krajowy
- osobní číslo
- numer_osobisty #
- identyfikator osobisty
- numer identyfikacyjny
- numer osobisty
- identyfikator pid #
- identyfikator pid
- pojištíní číslo
- rč
- rodne cislo
- rodné číslo
- ssn
- ssn #
- numer PEZEt
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- unikatowy numer identyfikacyjny


## <a name="czech-republic-physical-addresses"></a>Adresy fizyczne w Czechach

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Czech. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="denmark-drivers-license-number"></a>Numer prawa jazdy w Dania

### <a name="format"></a>Formatowanie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_denmark_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_denmark_eu_driver's_license_number` znajduje się.

```xml
      <!-- Denmark Driver's License Number -->
      <Entity id="98a95812-6203-451a-a220-d39870ebef0e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_denmark_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver s_license_number

- kørekort
- kørekortnummer


## <a name="denmark-passport-number"></a>Numer paszportu w Dania

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_denmark_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_denmark_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date2` datę w formacie DD MM YY lub znaleziono słowo `Keywords_eu_passport_date` kluczowe od

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_denmark_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_denmark_eu_passport_number` znajduje się.

```xml
      <!-- Denmark Passport Number -->
      <Entity id="25e8c47e-e6fe-4884-a211-74898f8c0196" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="denmark-personal-identification-number"></a>Dania : osobisty numer identyfikacyjny

### <a name="format"></a>Formatowanie

10 cyfr zawierające łącznik

### <a name="pattern"></a>Deseń

10 cyfr:
- Sześć cyfr w formacie DDMMYY, czyli data urodzenia
- Opcjonalna spacja lub łącznik
- cztery cyfry, gdzie ostatnia cyfra to cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Func_denmark_eu_tax_file_number umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Słowo kluczowe z Keyword_denmark_id znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Func_denmark_eu_tax_file_number umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Denmark Personal Identification Number -->
    <!-- Denmark Personal Identification Number -->
      <Entity id="6c4f2fef-56e1-4c00-8093-88d7a01cf460" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
          <Match idRef="Keyword_denmark_id" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilt registreringssystem
- kwi
- kwi #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- karta zdrowia
- numer karty ubezpieczenia społecznego;
- numer ubezpieczenia społecznego
- numer identyfikacyjny
- identifikationsnummer
- identifikationsnummer #
- numer tożsamości
- kenkassennummer
- nationalid #
- numer_narodowy #
- numer krajowy
- numer_osobisty #
- personalidentityno #
- identyfikator osobisty
- liczba_osob
- liczba_osob #
- reisekrankenversicherungskartenummer
- esygesikringskort
- ssn
- ssn #
- skat id
- kode skat
- skat nummer
- skattenummer
- numer PEZEt
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- kod podatku
- Karta ubezpieczenia zdrowia podróży
- uniqueidentityno #
- numer podatku
- numer rejestracji podatkowej
- identyfikator podatku
- numer identyfikacyjny podatku
- 2016 #
- numer_podatku #
- nie podatek
- taksno #
- numer_podatku
- Brak identyfikacji podatkowej
- tin #
- wydomowy #
- number #
- nie podatek #
- identyfikator tin
- nie tin
- cpr.nr
- cprnr
- cprnummer
- personnr
- personregister
- sygesikringsbevis
- sygesikringsbevisnr
- sygesikringsbevisnummer
- sygesikringskort
- sygesikringskortnr
- sygesikringskortnummer
- sygesikringsnr
- sygesikringsnummer


## <a name="denmark-physical-addresses"></a>Adresy fizyczne w Dania

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Dania. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="diseases"></a>Wołoń

Ta nieoznakowana nazwana jednostka wykrywa tekst, który pasuje do nazw nazwisk, takich jak *cyceta*. Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)


## <a name="drug-enforcement-agency-dea-number"></a>Numer agencji egzekwowania praw osób (DEA)

### <a name="format"></a>Formatowanie

Dwie litery, po których następuje siedem cyfr

### <a name="pattern"></a>Deseń

Wzorzec musi zawierać wszystkie następujące elementy:
- Jedna litera (bez rozróżniania wielkości liter) z tego zestawu możliwych liter: abcdefghjklmnprstux, który jest kodem rejestru
- jedna litera (bez wielkości liter), która jest pierwszą literą nazwiska rejestru lub cyfrą "9"
- Siedem cyfr, z których ostatnia to cyfra wyboru

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja nie Func_dea_number zawartości, która pasuje do wzorca.
- Zostanie znalezione słowo `Keyword_dea_number` kluczowe od
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja nie Func_dea_number zawartości, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
    <!-- DEA Number -->
    <Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_dea_number" />
      </Pattern>
      <Version minEngineVersion="15.20.1207.000" maxEngineVersion="15.20.3134.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
        </Pattern>
      </Version>
      <Version minEngineVersion="15.20.3135.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
          <Match idRef="Keyword_dea_number" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- dea
- dea #
- administracja wymuszania stosowania środków odurzanych
- agencja ds. egzekwowania przepisów odurzanych


## <a name="estonia-drivers-license-number"></a>Numer prawa jazdy w języku estońskim

### <a name="format"></a>Formatowanie

Dwie litery i sześć cyfr

### <a name="pattern"></a>Deseń

dwie litery i sześć cyfr:

- litery "ET" (bez wielkości liter)
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_estonia_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_estonia_eu_driver's_license_number` znajduje się.

```xml
      <!-- Estonia Driver's License Number -->
      <Entity id="51da8171-da70-4cc1-9d65-055a59ca4f83" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_estonia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver s_license_number

- permis de conduire
- juhilubade numbrid
- liczba juhiloa
- juhiluba


## <a name="estonia-passport-number"></a>Numer paszportu Estońskiego

### <a name="format"></a>Formatowanie

jedna litera, po której następuje siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Jedna litera, po której następuje siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_estonia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_estonia_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_estonia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_estonia_eu_passport_number` znajduje się.

```xml
      <!-- Estonia Passport Number -->
      <Entity id="61f7073a-509e-425b-a754-bc01bb5d5b8c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passinumbrid document number document number document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="estonia-personal-identification-code"></a>Estonia Personal Identification Code

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

11 cyfr:

- jedna cyfra odpowiadająca płci i wieku urodzenia (nieparzysta liczba mężczyzna, parzysta kobieta; 1-2: 19 wieku; 3-4: 20 wieku; 5-6: 21 wieku)
- Sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- Trzy cyfry odpowiadające liczbie kolejnej oddzielające osoby urodzenia w tym samym dniu
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_estonia_eu_national_id_card` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_estonia_eu_national_id_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_estonia_eu_national_id_card` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Estonia Personal Identification Code -->
      <Entity id="bfb26de6-dad5-4d48-ab72-4789cdd0654c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Match idRef="Keywords_estonia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_estonia_eu_telephone_number" />
            <Match idRef="Keywords_estonia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- ik
- isikukood #
- isikukood
- maksu id
- maksukohustuslase identifitseerimisnumber
- maksunumer
- numer identyfikacyjny kraju
- numer krajowy
- kod osobisty
- identyfikator osobisty
- kod identyfikacyjny
- numer identyfikacyjny
- numer_osobisty #
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="estonia-physical-addresses"></a>Estoński adres fizyczny

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Estonia. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="eu-debit-card-number"></a>Numer karty debetowej UE

### <a name="format"></a>Formatowanie

16 cyfr

### <a name="pattern"></a>Deseń

Złożony i niezawodny wzorzec

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_eu_debit_card umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Prawdziwe jest co najmniej jedno z następujących argumentów:
    - Zostanie znalezione słowo kluczowe Keyword_eu_debit_card.
    - Słowo kluczowe z Keyword_card_terms_dict znajduje się.
    - Zostanie znalezione słowo kluczowe Keyword_card_security_terms_dict.
    - Zostanie znalezione słowo kluczowe Keyword_card_expiration_terms_dict.
    - Funkcja Func_expiration_date znajdzie datę w odpowiednim formacie daty.
- Pomyślnie przejdzie sprawdzanie.

```xml
    <!-- EU Debit Card Number -->
    <Entity id="0e9b3178-9678-47dd-a509-37222ca96b42" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_eu_debit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_eu_debit_card" />
          <Match idRef="Keyword_card_terms_dict" />
          <Match idRef="Keyword_card_security_terms_dict" />
          <Match idRef="Keyword_card_expiration_terms_dict" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- numer konta
- numer karty
- nie.
- numer zabezpieczeń
- DW #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr
- nr acct
- acct nie
- American Express
- americanexpress
- americano nin
- amex
- karta atm
- karty atm
- atm kaart
- atmcard
- kartki atmcard
- atmkaart
- atmkaarten
- bancontact
- karta bankowa
- bankkaart
- posiadacz karty
- właściciele kart
- numer karty
- numer karty
- numery kart
- typ karty
- cardano numerico
- cardholder
- cardholders
- numer karty
- liczba_kart
- Carta bianca
- Carta credito
- carta di credito
- cartao de credito
- cartao de crédito
- cartao de debito
- cartao de débito
- carte bancaire
- carte blanche
- carte bleue
- carte de credit
- carte de crédit
- carte di credito
- carteblanche
- cartão de credito
- cartão de crédito
- cartão de debito
- cartão de débito
- cb
- ccn
- karta wyboru
- karty wyboru
- karta kontrolna
- karty wyboru
- chequekaart
- cirrus
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- karta kredytowa
- karty kredytowe
- karta kredytowa
- karty kredytowe
- debetkaart
- debetkaarten
- karta debetowa
- karty debetowe
- karta debetowa
- karty debetowe
- debito automatico
- Diners Club
- diners z
- odnajdowanie
- karta odnajdowanie
- odnajdowanie kart
- discovercard
- discovercards
- débito automático
- edc
- eigentümername
- Karta debetowa (European Debit Card)
- hoofdkaart
- hoofdkaarten
- in viagia
- biuro karty dla języka japońskiego
- japanse kaartdienst
- jcb
- kaart
- kaart num
- kaartaantal
- kaartaantallen
- kaarthouder
- kaarthouders
- karte
- karteninhaber
- kartenin wiadce
- kartennr
- kartennummer
- kreditkarte
- kreditkarten-nummer
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartennummer
- kreditkartentyp
- maestro
- karta wzorcowa
- karty wzorcowe
- karta wzorcowa
- karty wzorcowe
- mc
- mister cash
- n carta
- carta
- no de tarjeta
- no do cartao
- no do cartão
- nie. de tarjeta
- nie. do cartao
- nie. do cartão
- nr carta
- nr. carta
- numeri di scheda
- numero carta
- numero de cartao
- numero de carte
- numero de cartão
- numero de tarjeta
- numero della carta
- numero di carta
- numero di scheda
- numero do cartao
- numero do cartão
- numéro de carte
- nº carta
- nº de carte
- nº de la carte
- nº de tarjeta
- nº do cartao
- nº do cartão
- nº. do cartão
- número de cartao
- número de cartão
- número de tarjeta
- número do cartao
- scheda dell'assegno
- scheda dell'dell'cala cala
- scheda dell'dell'cala cala
- scheda della banca
- scheda di controllo
- scheda di debito
- scheda matrice
- schede dell'do przysłaniania
- schede di controllo
- schede di debito
- schede matrici
- scoprono la scheda
- scoprono le schede
- solo
- supporti di scheda
- supporto di scheda
- przełącznik
- tarjeta atm
- tarjeta credito
- tarjeta de atm
- tarjeta de credito
- tarjeta de debito
- tarjeta debito
- tarjeta no
- tarjetajetiente
- tipo della scheda
- ufficio giappo della
- scheda
- v pay
- v-pay
- visa
- visa plus
- visa electron
- visto
- wizja
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- numer identyfikacyjny karty
- weryfikacja karty
- cardi la verifica
- cid
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- cod. seg
- cod. seguranca
- cod. segurança
- cod. sicurezza
- codice di sicurezza
- codice di verifica
- codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- cryptogram
- cryptogramme
- cv2
- cvc
- cvc2
- cvn
- cvv
- cvv2
- cód seguranca
- cód segurança
- cód. seguranca
- cód. segurança
- código
- código de seguranca
- código de segurança
- de kaart controle
- geeft nr uit
- nr problemu
- numer problemu
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- nie. dell'edizione
- nie. di sicurezza
- numero de securite
- numero de verificacao
- numero dell'edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero van cycero
- numéro de sécurité
- nº autorizzazione
- número de verificação
- perno il blob
- blok przypinania
- prufziffer
- prüfziffer
- kod zabezpieczeń
- brak zabezpieczeń
- numer zabezpieczeń
- sicherheits kode
- sicherheitscode
- sicherheitsnummer
- speldblok
- cycero
- aimiheidsaantal
- edytowaniekodu
- cyceroszidynummer
- verfalldatum

#### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

- ablauf
- data de expiracao
- data de expiração
- data del exp
- data di exp
- data di scadenza
- data em que expira
- data scad
- data scadenza
- date de validité
- datum afloop
- datum van exp
- de afloop
- e maska
- e maska
- data exp
- exp datum
- wygasanie
- wygasa
- wygasa
- wygaśnięcie
- fecha de expiracion
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- valable
- validade
- valido hasta
- valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta


## <a name="eu-drivers-license-number"></a>Numer prawa jazdy w UE

Te jednostki znajdują się w numerze prawa jazdy UE i są typami informacji poufnych.

- [Austria](#austria-drivers-license-number)
- [Belgia](#belgium-drivers-license-number)
- [Bułgaria](#bulgaria-drivers-license-number)
- [Chorwacja](#croatia-drivers-license-number)
- [Cypr](#cyprus-drivers-license-number)
- [Czech](#czech-drivers-license-number)
- [Dania](#denmark-drivers-license-number)
- [Estonia](#estonia-drivers-license-number)
- [Finlandia](#finland-drivers-license-number)
- [Francja](#france-drivers-license-number)
- [Niemcy](#germany-drivers-license-number)
- [Grecja](#greece-drivers-license-number)
- [Węgry](#hungary-drivers-license-number)
- [Irlandia](#ireland-drivers-license-number)
- [Włochy](#italy-drivers-license-number)
- [Łotwa](#latvia-drivers-license-number)
- [Litwa](#lithuania-drivers-license-number)
- [Luxemburg](#luxemburg-drivers-license-number)
- [Malta](#malta-drivers-license-number)
- [Holandia](#netherlands-drivers-license-number)
- [Polska](#poland-drivers-license-number)
- [Portugalia](#portugal-drivers-license-number)
- [Rumunia](#romania-drivers-license-number)
- [Słowacja](#slovakia-drivers-license-number)
- [Słowenia](#slovenia-drivers-license-number)
- [Hiszpania](#spain-drivers-license-number)
- [Szwecja](#sweden-drivers-license-number)
- [Zjednoczone Emiraty Zjednoczone](#uk-drivers-license-number)


## <a name="eu-national-identification-number"></a>Krajowy numer identyfikacyjny UE

Te jednostki znajdują się w ramach państwowego numeru identyfikacyjnego UE i są typami informacji poufnych.

- [Austria](#austria-identity-card)
- [Belgia](#belgium-national-number)
- [Bułgaria](#bulgaria-uniform-civil-number)
- [Chorwacja](#croatia-identity-card-number)
- [Cypr](#cyprus-identity-card)
- [Czech](#czech-personal-identity-number)
- [Dania](#denmark-personal-identification-number)
- [Estonia](#estonia-personal-identification-code)
- [Finlandia](#finland-national-id)
- [Francja](#france-national-id-card-cni)
- [Niemcy](#germany-identity-card-number)
- [Grecja](#greece-national-id-card)
- [Węgry](#hungary-personal-identification-number)
- [Irlandia](#ireland-personal-public-service-pps-number)
- [Włochy](#italy-fiscal-code)
- [Łotwa](#latvia-personal-code)
- [Litwa](#lithuania-personal-code)
- [Luxemburg](#luxemburg-national-identification-number-natural-persons)
- [Malta](#malta-identity-card-number)
- [Holandia](#netherlands-citizens-service-bsn-number)
- [Polska](#poland-national-id-pesel)
- [Portugalia](#portugal-citizen-card-number)
- [Rumunia](#romania-personal-numeric-code-cnp)
- [Słowacja](#slovakia-personal-number)
- [Słowenia](#slovenia-unique-master-citizen-number)
- [Hiszpania](#spain-dni)
- [Zjednoczone Emiraty Zjednoczone](#uk-national-insurance-number-nino)


## <a name="eu-passport-number"></a>Numer paszportu UE

Te jednostki znajdują się w numerze paszportu UE i mają typ informacji poufnych. Te jednostki znajdują się w pakiecie numeru paszportu UE.

- [Austria](#austria-passport-number)
- [Belgia](#belgium-passport-number)
- [Bułgaria](#bulgaria-passport-number)
- [Chorwacja](#croatia-passport-number)
- [Cypr](#cyprus-passport-number)
- [Czech](#czech-passport-number)
- [Dania](#denmark-passport-number)
- [Estonia](#estonia-passport-number)
- [Finlandia](#finland-passport-number)
- [Francja](#france-passport-number)
- [Niemcy](#germany-passport-number)
- [Grecja](#greece-passport-number)
- [Węgry](#hungary-passport-number)
- [Irlandia](#ireland-passport-number)
- [Włochy](#italy-passport-number)
- [Łotwa](#latvia-passport-number)
- [Litwa](#lithuania-passport-number)
- [Luxemburg](#luxemburg-passport-number)
- [Malta](#malta-passport-number)
- [Holandia](#netherlands-passport-number)
- [Polska](#poland-passport-number)
- [Portugalia](#portugal-passport-number)
- [Rumunia](#romania-passport-number)
- [Słowacja](#slovakia-passport-number)
- [Słowenia](#slovenia-passport-number)
- [Hiszpania](#spain-passport-number)
- [Szwecja](#sweden-passport-number)
- [Numer paszportu Stanów Zjednoczonych](#usuk-passport-number)


## <a name="eu-social-security-number-or-equivalent-identification"></a>Numer PE PE PEŁ LUB równoważna identyfikacja

Są to jednostki, które znajdują się w numerze PE PEP lub w równoważnej identyfikacji i są typami informacji poufnych.

- [Austria](#austria-social-security-number)
- [Belgia](#belgium-national-number)
- [Chorwacja](#croatia-personal-identification-oib-number)
- [Czech](#czech-personal-identity-number)
- [Dania](#denmark-personal-identification-number)
- [Finlandia](#finland-national-id)
- [Francja](#france-social-security-number-insee)
- [Niemcy](#germany-identity-card-number)
- [Grecja](#greece-national-id-card)
- [Węgry](#hungary-social-security-number-taj)
- [Portugalia](#portugal-citizen-card-number)
- [Hiszpania](#spain-social-security-number-ssn)
- [Szwecja](#sweden-national-id)


## <a name="eu-tax-identification-number"></a>Numer identyfikacyjny podatku UE

Te jednostki należą do typu informacji poufnych numeru identyfikacji podatkowej UE.

- [Austria](#austria-tax-identification-number)
- [Belgia](#belgium-national-number)
- [Bułgaria](#bulgaria-uniform-civil-number)
- [Chorwacja](#croatia-identity-card-number)
- [Cypr](#cyprus-tax-identification-number)
- [Czech](#czech-personal-identity-number)
- [Dania](#denmark-personal-identification-number)
- [Estonia](#estonia-personal-identification-code)
- [Finlandia](#finland-national-id)
- [Francja](#france-tax-identification-number)
- [Niemcy](#germany-tax-identification-number)
- [Grecja](#greece-tax-identification-number)
- [Węgry](#hungary-tax-identification-number)
- [Irlandia](#ireland-personal-public-service-pps-number)
- [Włochy](#italy-fiscal-code)
- [Łotwa](#latvia-personal-code)
- [Litwa](#lithuania-personal-code)
- [Luxemburg](#luxemburg-national-identification-number-non-natural-persons)
- [Malta](#malta-tax-identification-number)
- [Holandia](#netherlands-tax-identification-number)
- [Polska](#poland-tax-identification-number)
- [Portugalia](#portugal-tax-identification-number)
- [Rumunia](#romania-personal-numeric-code-cnp)
- [Słowacja](#slovakia-personal-number)
- [Słowenia](#slovenia-tax-identification-number)
- [Hiszpania](#spain-tax-identification-number)
- [Szwecja](#sweden-tax-identification-number)
- [Zjednoczone Emiraty Zjednoczone](#uk-unique-taxpayer-reference-number)


## <a name="finland-drivers-license-number"></a>Numer prawa jazdy w Finlandia

### <a name="format"></a>Formatowanie

10 cyfr zawierające łącznik

### <a name="pattern"></a>Deseń

10 cyfr zawierających łącznik:

- Sześć cyfr
- Łącznik
- trzy cyfry
- cyfrę lub literę

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_finland_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_finland_eu_driver's_license_number` znajduje się.

```xml
      <!-- Finland Driver's License Number -->
      <Entity id="bb3b27a3-79bd-4ac4-81a7-f9fca3c7d1a7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_finland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver s_license_number

- ajokortti
- permis de conduire
- ajokortin numero
- kuljetteja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot


## <a name="finland-european-health-insurance-number"></a>Finlandia, numer ubezpieczenia społecznego w Niemczech

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

20-cyfrowy numer

### <a name="pattern"></a>Deseń

Numer 20-cyfrowy:

- 10 cyfr — 8024680246
- Opcjonalna spacja lub łącznik
- 10 cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Ta Regex_Finland_European_Health_Insurance_Number wyszukuje zawartość, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_Finland_European_Health_Insurance_Number.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- ehic #
- ehic
- finlandehicnumber #
- finska sjukförsäkringskort
- karta zdrowia
- karta ubezpieczenia społecznego
- numer ubezpieczenia społecznego
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti


## <a name="finland-national-id"></a>Identyfikator narodowy Finlandia

### <a name="format"></a>Formatowanie

Sześć cyfr oraz znak oznaczający wiek oraz trzy cyfry i cyfrę wyboru

### <a name="pattern"></a>Deseń

Wzorzec musi zawierać wszystkie następujące elementy:
- Sześć cyfr w formacie DDMMYY, czyli data urodzenia
- znacznik wieku (albo '-', '+', albo 'a')
- Trzycyfrowy osobisty numer identyfikacyjny
- cyfrę lub literę (bez uwzględniania liter), która jest cyfrą kontrolną

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- funkcja Func_finnish_national_id wyszukuje zawartość, która pasuje do wzorca
- Słowo kluczowe z Keyword_finnish_national_id znajduje się
- jeśli tak się umknie,

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- funkcja Func_finnish_national_id wyszukuje zawartość, która pasuje do wzorca
- jeśli tak się umknie,

```xml
      <!-- Finnish National ID-->
      <Entity id="338FD995-4CB5-4F87-AD35-79BD1DD926C1" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finnish_national_id" />
          <Match idRef="Keyword_finnish_national_id" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_finnish_national_id" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

- ainutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- id no
- numer identyfikacyjny
- numer identyfikacyjny
- identitetti numero
- numer tożsamości
- idnumber
- kansallinen henkilötunnus
- kansallisen henkilökortin
- national id card
- numer dowodu osobistego.
- identyfikator osobisty
- kod tożsamości osobistej
- numer_osobisty #
- personbeteckning
- liczba_osob
- numer PEZEt
- sosiaaliturvatunnus
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- tunnistenumero
- tunnus numero
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus


## <a name="finland-passport-number"></a>Numer paszportu Finlandia

Ta jednostka jest dostępna w ramach typu informacji poufnych numer paszportu UE i jest dostępna jako autonomiczna jednostka tego typu.

### <a name="format"></a>Formatowanie
Kombinacja dziewięciu liter i cyfr

### <a name="pattern"></a>Deseń
Kombinacja dziewięciu liter i cyfr:
- Dwie litery (bez wielkości liter)
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_finland_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z `Keywords_eu_passport_number` lub `Keyword_finland_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_finland_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z `Keywords_eu_passport_number` lub `Keyword_finland_passport_number` znajduje się.

```xml
      <!-- Finland Passport Number -->
      <Entity id="d1685ac3-1d3a-40f8-8198-32ef5669c7a5" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomabicen passi
- passin numero
- passin numero. #
- passin numero #
- passin numero.
- passi #
- numer passi

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="finland-physical-addresses"></a>Adresy fizyczne w Finlandia

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym w Finlandia. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="france-drivers-license-number"></a>Numer prawa jazdy we Francji

Ta jednostka jest dostępna w ramach typu informacji poufnych Numer prawa jazdy w UE i jest dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formatowanie

12 cyfr

### <a name="pattern"></a>Deseń

12 cyfr ze sprawdzaniem poprawności w celu dyskontowania podobnych wzorców, takich jak francuskie numery telefonów

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- funkcja Func_french_drivers_license znajdzie zawartość, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_french_drivers_license.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl
- permis de conduire
- numer licencji
- numer licencji
- numery licencji
- numery licencji
- numéros de licence


## <a name="france-health-insurance-number"></a>Numer ubezpieczenia społecznego we Francji

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Numer 21-cyfrowy

### <a name="pattern"></a>Deseń

Numer 21-cyfrowy:

- 10 cyfr
- spacja opcjonalna
- 10 cyfr
- spacja opcjonalna
- cyfra


### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- regex Regex_France_Health_Insurance_Number umożliwia znalezienie zawartości, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_France_Health_Insurance_Number.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- karta ubezpieczenia
- carte vitale
- carte d'assuré social


## <a name="france-national-id-card-cni"></a>France national id card (CNI)

### <a name="format"></a>Formatowanie

12 cyfr

### <a name="pattern"></a>Deseń

12 cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_france_cni umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Słowo kluczowe z Keywords_france_eu_national_id_card znajduje się.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- numer karty
- carte nationale d'identité
- carte nationale d'idenite no
- cni #
- cni
- compte bancaire
- numer identyfikacyjny kraju
- tożsamość państwowa
- nationalidno #
- numéro d'assurance maladie
- numéro de carte vitale


## <a name="france-passport-number"></a>Numer paszportu Francji

Podmiot ten jest dostępny w ramach numeru paszportu UE typu informacji poufnych. Jest także dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formatowanie

Dziewięć cyfr i liter

### <a name="pattern"></a>Deseń

Dziewięć cyfr i liter:
- dwie cyfry
- Dwie litery (bez wielkości liter)
- pięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_fr_passport` zawartość, która odpowiada wzorcowi.
- Słowo kluczowe z `Keywords_eu_passport_number` lub `Keywords_france_eu_passport_number` znajduje się.
- Wyrażenie regularne umożliwia `Regex_eu_passport_date3` znalezienie daty w formacie DD MM YYYY lub znalezione słowo kluczowe `Keywords_eu_passport_date` od

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_fr_passport` zawartość, która odpowiada wzorcowi.
- Słowo kluczowe z `Keywords_eu_passport_number` lub `Keywords_france_eu_passport_number` znajduje się.


```xml
    <!-- France Passport Number -->
    <Entity id="3008b884-8c8c-4cd8-a289-99f34fc7ff5d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passeport français
- passeport jen
- kartezja passeport
- numéro passeport
- passeport n°
- n° du passeport
- n° passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="france-physical-addresses"></a>Adresy fizyczne we Francji

Ta nieoznakowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Francji. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="france-social-security-number-insee"></a>Numer PE PESZ we Francji (INSEE)

### <a name="format"></a>Formatowanie

15 cyfr

### <a name="pattern"></a>Deseń

Musi odpowiadać jedneowi z dwóch wzorców:
- 13 cyfr, po którym następuje spacja, a po niej dwie cyfry<br/>
lub
- 15 kolejnych cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_french_insee` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_fr_insee.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja może Func_french_insee lub Func_fr_insee zawartości, która jest taka, jak wzorzec.
- Pomyślnie przejdzie sprawdzanie.

```xml
    <!-- France INSEE -->
    <Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Keyword_fr_insee" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- code sécu
- d'identité nationale
- insee
- fssn #
- le numéro d'identification nationale
- le code de la sécurité sociale
- identyfikator narodowy
- identyfikacja państwowa
- no d'identité
- nie. d'identité
- numéro d'assurance
- numéro d'identité
- numero d'identite
- numéro de sécu
- numéro de sécurité sociale
- no d'identite
- nie. d'identite
- ssn
- ssn #
- sécurité sociale
- securité sociale
- securite sociale
- socialsecuritynumber
- numer PEZEt
- kod peł.
- numer ubezpieczenia społecznego


## <a name="france-tax-identification-number"></a>Numer identyfikacji podatkowej we Francji

### <a name="format"></a>Formatowanie

13 cyfr

### <a name="pattern"></a>Deseń

13 cyfr

- Jedna cyfra, która musi być 0, 1, 2 lub 3
- Jedna cyfra
- Spacja (opcjonalnie)
- Dwie cyfry
- Spacja (opcjonalnie)
- Trzy cyfry
- Spacja (opcjonalnie)
- Trzy cyfry
- Spacja (opcjonalnie)
- Trzy cyfry sprawdzania


### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_france_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_france_eu_tax_file_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_france_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- France Tax Identification Number (numéro SPI.) -->
      <Entity id="ed59e77e-171d-442c-9ec1-88e2ebcb5b0a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Match idRef="Keywords_france_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_france_eu_telephone_number" />
            <Match idRef="Keywords_france_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d'identification fiscale
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="france-value-added-tax-number"></a>Numer podatku dodanego we Francji

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

13-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

13-znakowy wzorzec alfanumeryczny:

- Dwie litery — FR (bez uwzględniania liter)
- Opcjonalna spacja lub łącznik
- Dwie litery lub cyfry
- Opcjonalna spacja, kropka, łącznik lub przecinek
- trzy cyfry
- Opcjonalna spacja, kropka, łącznik lub przecinek
- trzy cyfry
- Opcjonalna spacja, kropka, łącznik lub przecinek
- trzy cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_france_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keywords_france_value_added_tax_number.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_france_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- France Value Added Tax Number -->
      <Entity id="949121e6-ad9f-4379-8731-710342baea78" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_value_added_tax_number" />
          <Match idRef="Keywords_france_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- numer VAT
- bez podatku VAT
- vat #
- podatek od wartości dodanej
- identyfikator no numéro d'identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification alexen


## <a name="generic-medication-names"></a>Ogólne nazwy leki

Ta nieoznazona nazwana jednostka wykrywa nazwy ogólnych leki, takich jak *acetaminophen*. Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)


## <a name="germany-drivers-license-number"></a>Niemiecki numer prawa jazdy

Ten typ informacji poufnych jest uwzględniony w poufnym typie informacji numeru rejestracyjnego ue. Jest także dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formatowanie

Kombinacja 11 cyfr i liter

### <a name="pattern"></a>Deseń

11 cyfr i liter (bez wielkości liter):
- cyfrę lub literę
- dwie cyfry
- Sześć cyfr lub liter
- cyfra
- cyfrę lub literę

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_german_drivers_license znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_german_drivers_license_number znajduje się.
- Pomyślnie przejdzie sprawdzanie.

```xml
    <!-- German Driver's License Number -->
    <Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Match idRef="Keyword_german_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_german_drivers_license_number"></a>Keyword_german_drivers_license_number

- ausstellungsdatum
- ausstellungsort
- ausstellende behöde
- ausstellende behorde
- ausstellende behoerde
- führerschein
- fuhrerschein
- fuehrerschein
- führerscheinnummer
- fuhrerscheinnummer
- fuehrerscheinnummer
- führerschein- 
- fuhrerschein- 
- fuehrerschein- 
- führerscheinnummernr
- fuhrerscheinnummernr
- fuehrerscheinnummernr
- führerscheinnummerklasse
- fuhrerscheinnummerklasse
- fuehrerscheinnummerklasse
- nr-führerschein
- nr-fuhrerschein
- nr-fuehrerschein
- no-führerschein
- no-fuhrerschein
- no-fuehrerschein
- n-führerschein
- n-fuhrerschein
- n-fuehrerschein
- permis de conduire
- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dlno


## <a name="germany-identity-card-number"></a>Numer karty tożsamości Niemcy

### <a name="format"></a>Formatowanie

od 1 listopada 2010 r.: Od dziewięciu do jedenastu liter i cyfr

od 1 kwietnia 1987 r. do 31 października 2010 r.: 10 cyfr

### <a name="pattern"></a>Deseń

od 1 listopada 2010 r.: wzorzec alfanumeryczny od 9 do 11 znaków
- jeden L, M, N, P, R, T, V, W, X, Y (bez uwzględniania liter)
- Osiem cyfr lub liter w językach C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y i Z (bez uwzględniania liter)
- opcjonalna cyfra wyboru
- Opcjonalnie d/D

od 1 kwietnia 1987 r. do 31 października 2010 r.:
- 10 cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_german_id_card_with_check` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_germany_id_card` kluczowe od.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne `Regex_germany_id_card` znajduje zawartość, która jest taka sama jak wzorzec (9 znaków bez sprawdzenia, że zostały wydane przed 2010 10-cyfrowym wzorcem wydanym w programie posy 2010).
- Zostanie znalezione słowo kluczowe Keyword_germany_id_card.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_german_id_card_with_check` zawartość, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.


```xml
      <!-- Germany Identity Card Number -->
      <Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" patternsProximity="300" recommendedConfidence="75"> 
        <Pattern confidenceLevel="75">
         <IdMatch idRef="Regex_germany_id_card" /> 
         <Match idRef="Keyword_germany_id_card" /> 
        </Pattern>
        <Version minEngineVersion="15.20.4545.000"> 
          <Pattern confidenceLevel="85">
           <IdMatch idRef="Func_german_id_card_with_check" />
            <Match idRef="Keyword_germany_id_card" /> 
          </Pattern> 
          <Pattern confidenceLevel="65">
           <IdMatch idRef="Func_german_id_card_with_check" /> 
          </Pattern> 
        </Version>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- identyfikacja
- identifikation
- identifizierungsnummer
- karta tożsamości
- numer tożsamości
- id-nummer
- identyfikator osobisty
- personalausweis
- persönliche id nummer
- persönliche identifikationsnummer
- persönliche-id-nummer


## <a name="germany-passport-number"></a>Numer paszportu Niemiec

### <a name="format"></a>Formatowanie

Od 9 do 11 znaków

### <a name="pattern"></a>Deseń

- Jedna litera w literze C, F, G, H, J, K (bez uwzględniania liter)
- Osiem cyfr lub liter w językach C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y i Z (bez uwzględniania liter)
- opcjonalna cyfra wyboru
- Opcjonalnie d/D

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_german_passport_checksum` zawartość, która odpowiada wzorcowi.
- Słowo kluczowe z `Keyword_german_passport` lub `Keywords_eu_passport_number_common` znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_german_passport` zawartość, która odpowiada wzorcowi dziewięciu znaków (bez sprawdzenia cyfry i opcjonalnego d/D).
- Słowo kluczowe z `Keyword_german_passport` lub `Keywords_eu_passport_number_common` znajduje się.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_german_passport_checksum` zawartość, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.

```xml
    <!-- German Passport Number -->
    <Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keywords_eu_passport_number_common" />
        </Any>
      </Pattern>
      <Version minEngineVersion="15.20.4570.0">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_german_passport_checksum" />
          <Any minMatches="1">
            <Match idRef="Keyword_german_passport" />
            <Match idRef="Keywords_eu_passport_number_common" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_german_passport_checksum" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- nie.
- passeport no

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów


## <a name="germany-physical-addresses"></a>Adresy fizyczne w Niemczech

Ta nieoznakowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Niemiec. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="germany-tax-identification-number"></a>Numer identyfikacyjny podatku w Niemczech

### <a name="format"></a>Formatowanie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

11 cyfr

- Dwie cyfry
- Spacja opcjonalna
- Trzy cyfry
- Spacja opcjonalna
- Trzy cyfry
- Spacja opcjonalna
- Dwie cyfry
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_germany_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_germany_eu_tax_file_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_germany_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Germany Tax Identification Number -->
      <Entity id="43316a89-9880-40cf-b980-04bc7eefcec5" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
          <Match idRef="Keywords_germany_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- id użytkownika
- steueridentifikationsnummer
- steuernummer
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- zinn #
- zinn
- zinnnummer


## <a name="germany-value-added-tax-number"></a>Numer podatku dodanego w Niemczech

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

11-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

11-znakowy wzorzec alfanumeryczny:

- a letter D or d
- Litera E lub e
- spacja opcjonalna
- trzy cyfry
- opcjonalna spacja lub przecinek
- trzy cyfry
- opcjonalna spacja lub przecinek
- trzy cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_germany_value_added_tax_number wyszukuje zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keywords_germany_value_added_tax_number znajduje się.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_germany_value_added_tax_number wyszukuje zawartość, która pasuje do wzorca.

```xml
      <!-- Germany Value Added Tax Number -->
      <Entity id="db177eb2-8811-4842-bffc-128c14aa219f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
          <Match idRef="Keywords_germany_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- numer VAT
- bez podatku VAT
- vat #
- vat# mehrwertsteuer
- mjst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer


## <a name="greece-drivers-license-number"></a>Numer prawa jazdy w Grecji

Ten podmiot jest uwzględniony w poufnym typie informacji Numer prawa jazdy w UE. Jest także dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_greece_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_greece_eu_driver's_license_number` znajduje się.

```xml
      <!-- Greece Driver's License Number -->
      <Entity id="7a2200b5-aacf-4e3c-ab36-136d3e68b7da" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_greece_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_greece_eu_drivers_license_number"></a>Keywords_greece_eu_driver nie s_license_number

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης


## <a name="greece-national-id-card"></a>Karta kredytowa państwowa Grecja

### <a name="format"></a>Formatowanie

Kombinacja 7-8 liter i cyfr oraz kreski

### <a name="pattern"></a>Deseń

Siedem liter i cyfr (stary format):
- Jedna litera (dowolna litera alfabetu greckiego)
- Kreska
- Sześć cyfr

Osiem liter i cyfr (nowy format):
- Dwie litery, których znaki wielkich liter występują zarówno w alfabecie greckim, jak i w alfabecie łacińskim (ABEZHIKMNOPTYX)
- Kreska
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_greece_id_card zawartości, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_greece_id_card.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_greece_id_card zawartości, która jest taka, jak wzorzec.

```xml
      <!-- Greece National ID Card -->
      <Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_id_card" />
          <Match idRef="Keyword_greece_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_greece_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- identyfikator grecki
- grecki identyfikator narodowy
- Karta osobistego identyfikatora greckiego
- identyfikator grecki
- karta tożsamości
- tautotita
- ταυτότητα
- ταυτότητας


## <a name="greece-passport-number"></a>Numer paszportu Grecji

### <a name="format"></a>Formatowanie

Dwie litery, po których następuje siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Dwie litery, po których następuje siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_greece_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_greece_eu_passport_number` znajduje się.
- Wyrażenie regularne umożliwia `Regex_greece_eu_passport_date` znalezienie daty w formacie DD MMM YY (przykład — 28 sierpnia 19) `Keywords_greece_eu_passport_date` lub słowa kluczowego z.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_greece_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_greece_eu_passport_number` znajduje się.

```xml
      <!-- Greece Passport Number -->
      <Entity id="7e65eb47-cdf9-4f52-8f90-2a27d5ee67e3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_greece_eu_passport_date" />
            <Match idRef="Keywords_greece_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο


## <a name="greece-physical-addresses"></a>Grecja ( adresy fizyczne)

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Grecji. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="greece-social-security-number-amka"></a>Numer PE PEŁ (AMKA)

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

- Sześć cyfr jako data urodzenia RRMMDD
- Cztery cyfry
- cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_greece_eu_ssn` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_greece_eu_ssn_or_equivalent` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_greece_eu_ssn` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Greece Social Security Number (AMKA) -->
      <Entity id="e39b03f4-50ea-41ae-af7a-a4b9539596ad" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_greece_eu_ssn" />
          <Match idRef="Keywords_greece_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_greece_eu_ssn" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- ssn
- ssn #
- nr ubezpieczenia społecznego
- socialsecurityno #
- numer PEZEt
- amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης


## <a name="greece-tax-identification-number"></a>Numer identyfikacji podatkowej Grecja

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Wyrażenie regularne umożliwia  `Regex_greece_eu_tax_file_number` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_greece_eu_tax_file_number` kluczowe od.

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- afm #
- afm
- aμμ|a naμ αα μ μ 2
- aμμ
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- rejestr podatkowy nie
- numer rejestru podatkowego
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- taxregistryno #
- identyfikator tin
- nie tin
- tin #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο


## <a name="hong-kong-identity-card-hkid-number"></a>Numer karty tożsamości Hongkongu (HKID)

### <a name="format"></a>Formatowanie

Kombinacja 8-9 liter i cyfr oraz opcjonalnych nawiasów wokół końcowego znaku

### <a name="pattern"></a>Deseń

Kombinacja 8-9 liter:
- 1–2 litery (bez wielkości liter)
- Sześć cyfr
- Końcowy znak (dowolna cyfra lub litera A), który jest cyfrą kontrolną i opcjonalnie jest ujęty w nawiasy.

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_hong_kong_id_card znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_hong_kong_id_card znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_hong_kong_id_card znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Hong Kong Identity Card (HKID) number -->
<Entity id="e63c28a7-ad29-4c17-a41a-3d2a0b70fd9c" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_hong_kong_id_card"/>
     <Match idRef="Keyword_hong_kong_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Func_hong_kong_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- hong kong identity card
- HKIDC
- identyfikator
- karta tożsamości
- karta tożsamości hk
- hong kong id
- 香港身份證
- 香港永久性居民身份證
- 身份證
- 身份証
- 身分證
- 身分証
- 香港身份証
- 香港身分證
- 香港身分証
- 香港身份證
- 香港居民身份證
- 香港居民身份証
- 香港居民身分證
- 香港居民身分証
- 香港永久性居民身份証
- 香港永久性居民身分證
- 香港永久性居民身分証
- 香港永久性居民身份證
- 香港非永久性居民身份證
- 香港非永久性居民身份証
- 香港非永久性居民身分證
- 香港非永久性居民身分証
- 香港特別行政區永久性居民身份證
- 香港特別行政區永久性居民身份証
- 香港特別行政區永久性居民身分證
- 香港特別行政區永久性居民身分証
- 香港特別行政區非永久性居民身份證
- 香港特別行政區非永久性居民身份証
- 香港特別行政區非永久性居民身分證
- 香港特別行政區非永久性居民身分証


## <a name="hungary-drivers-license-number"></a>Numer prawa jazdy na Węgry

### <a name="format"></a>Formatowanie

Dwie litery i sześć cyfr

### <a name="pattern"></a>Deseń

Dwie litery i sześć cyfr:

- Dwie litery (bez wielkości liter)
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Wyrażenie regularne umożliwia  `Regex_hungary_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_hungary_eu_driver's_license_number` znajduje się.

```xml
      <Entity id="9d31c46b-6e6b-444c-aeb1-6dd7e604bb24" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_hungary_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver nie s_license_number

- vezetoi engedely
- vezetõi engedély
- vezetõi engedélyek


## <a name="hungary-passport-number"></a>Numer paszportu Węgry

### <a name="format"></a>Formatowanie

Dwie litery, po których następuje sześć lub siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Dwie litery, po których następuje sześć lub siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_hungary_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_hungary_eu_passport_number` znajduje się.
- Wyrażenie regularne umożliwia `Regex_hungary_eu_passport_date` znalezienie daty w formacie DD MMM/MMM YY (przykład — 01 MÁR/MAR 12) `Keywords_eu_passport_date` lub słowa kluczowego od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_hungary_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_hungary_eu_passport_number` znajduje się.

```xml
      <!-- Hungary Passport Number -->
      <Entity id="5b483910-9aa7-4c99-9917-f4001464bda7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_hungary_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="hungary-personal-identification-number"></a>Osobisty numer identyfikacyjny Węgry

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

11 cyfr

### <a name="pattern"></a>Deseń

11 cyfr:

- Jedna cyfra odpowiadająca płci, 1 dla mężczyzny, 2 dla kobiety. Inne liczby są również możliwe dla osób, które mają urodzić się przed 1900 rokiem, lub też tych, którzy mają podwójne zamówienie.
- Sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- Trzy cyfry odpowiadające numerowi kolejnemu
- Jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja znajduje  `Func_hungary_eu_national_id_card` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_hungary_eu_national_id_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja znajduje  `Func_hungary_eu_national_id_card` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Hungary Personal Identification Number -->
      <Entity id="7b5cc218-7046-47d9-80c9-f325b50896ca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Match idRef="Keywords_hungary_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- numer identyfikacyjny
- numer identyfikacyjny
- sz ig
- sz. ig.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány


## <a name="hungary-physical-addresses"></a>Adresy fizyczne Węgry

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym Węgry. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="hungary-social-security-number-taj"></a>Węgry: numer PE PEZ

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Dziewięć cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja znajduje  `Func_hungary_eu_ssn_or_equivalent` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_hungary_eu_ssn_or_equivalent` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja znajduje  `Func_hungary_eu_ssn_or_equivalent` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Hungarian Social Security Number (TAJ) -->
      <Entity id="0de78315-9537-47f5-95ab-b3e77eba3993" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_hungary_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- węgierski numer PESZ
- numer PEZEt
- socialsecuritynumber #
- hssn #
- socialsecuritynno
- hssn
- taj
- taj #
- ssn
- ssn #
- nr ubezpieczenia społecznego
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérk adó
- áfa szám
- magyar áfa szám


## <a name="hungary-tax-identification-number"></a>Numer identyfikacji podatkowej Węgry

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

10 cyfr:

- Jedna cyfra, która musi być "8"
- Osiem cyfr
- Jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja znajduje  `Func_hungary_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_hungary_eu_tax_file_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja znajduje  `Func_hungary_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Hungary Tax Identification Number -->
      <Entity id="ede42eb4-59d9-49eb-9603-d7853fbda91d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Match idRef="Keywords_hungary_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- węgierskia tin
- hungatinatin #
- urząd skarbowy nie
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- numer VAT


## <a name="hungary-value-added-tax-number"></a>Węgry: numer podatku dodanego

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

10-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

10-znakowy wzorzec alfanumeryczny:

- dwa litery — HU lub hu
- spacja opcjonalna
- osiem cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja Func_hungarian_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keywords_hungarian_value_added_tax_number.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja Func_hungarian_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- Hungarian Value Added Tax Number -->
      <Entity id="976349a0-683b-477a-90f8-ff0a220d5592" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
          <Match idRef="Keywords_hungarian_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- vat
- numer podatku dodanego
- vat #
- vatno #
- węgierskievatno #
- nie ma podatku.
- podatek od wartości dodanej áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérk adó
- áfa szám


## <a name="iceland-physical-addresses"></a>Islandzkie adresy fizyczne

Ta nieoznazona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Islandii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>Niepełnosprawności wymienione w amerykańskiej ocenie niepełnosprawności w ramach ubezpieczenia społecznego

Ta nieoznazona nazwana jednostka wykrywa nazwy niepełnosprawności wyszczególnionych w U.S. Disability Evaluation w ramach ubezpieczenia społecznego, takich jak *dystrophy dystrophy*. Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)


## <a name="india-drivers-license-number"></a>Numer prawa jazdy w Indiach

### <a name="format"></a>Formatowanie

15-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

15 liter lub cyfr:
- Dwie litery wskazujące kod województwa
- opcjonalna spacja lub kreska
- Dwie cyfry oznaczające kod miasta
- opcjonalna spacja lub kreska
- Cztery cyfry oznaczające rok wydania
- opcjonalna spacja lub kreska
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_india_driving_license` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keywords_eu_driver's_license_number_common` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_india_driving_license` znalezienie zawartości, która odpowiada wzorcowi.


```xml
      <!-- India Driver's License Number -->
        <Entity id="680788a3-53b6-455a-b891-c38cd76dc917" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_india_driving_license" />
            <Match idRef="Keywords_eu_driver's_license_number_common" />
          </Pattern>
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Regex_india_driving_license" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver nie s_license_number_common

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl



## <a name="india-gst-number"></a>Numer GST w Indiach

### <a name="format"></a>Formatowanie

15-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

15 liter lub cyfr:
- Dwie cyfry reprezentujące prawidłowy kod województwa
- opcjonalna spacja lub kreska
- Dziesięć znaków reprezentujących numer konta trwałego (PAN) 
- jedna litera lub cyfra
- opcjonalna spacja lub kreska
- jedna litera "z" lub "Z"
- opcjonalna spacja lub kreska
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_india_gst_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_india_gst_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_india_gst_number` zawartość, która odpowiada wzorcowi.


```xml
    <!-- India GST number  -->
      <Entity id="9f5a721c-2fd2-446a-a27e-0c02fbe4630c" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_india_gst_number" />
          <Match idRef="Keyword_india_gst_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_india_gst_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- gst
- gstin
- Podatek od towarów i usług
- podatek od towarów i usług


## <a name="india-permanent-account-number-pan"></a>Stały numer konta w Indiach (PAN)

### <a name="format"></a>Formatowanie

10 liter lub cyfr

### <a name="pattern"></a>Deseń

10 liter lub cyfr:
- Trzy litery (bez wielkości liter)
- Litera w literze C, P, H, F, A, T, B, L, J, G (bez wielkości liter)
- Litera
- Cztery cyfry
- Litera, która jest cyfrą kontrolną w porządku alfabetycznym

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_india_permanent_account_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_india_permanent_account_number.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_india_permanent_account_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.


```xml
      <!-- India Permanent Account Number -->
      <Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_india_permanent_account_number" />
          <Match idRef="Keyword_india_permanent_account_number" />
        </Pattern>
        <Version minEngineVersion="15.20.3520.000">
          <Pattern confidenceLevel="65">
            <IdMatch idRef="Regex_india_permanent_account_number" />
          </Pattern>
        </Version>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Trwały numer konta
- PAN

## <a name="india-unique-identification-aadhaar-number"></a>Unikatowy numer identyfikacyjny w Indiach (Aadhaar)

### <a name="format"></a>Formatowanie

12 cyfr zawierających opcjonalne spacje lub kreski

### <a name="pattern"></a>Deseń

12 cyfr:
- Cyfra niebędąca cyfrą 0 lub 1
- Trzy cyfry
- Opcjonalna spacja lub kreska
- Cztery cyfry
- Opcjonalna spacja lub kreska
- Ostatnia cyfra, czyli cyfra wyboru

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_india_aadhaar znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_india_aadhar znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja Func_india_aadhaar znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- India Unique Identification (Aadhaar) number -->
<Entity id="1ca46b29-76f5-4f46-9383-cfa15e91048f" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_india_aadhaar"/>
     <Match idRef="Keyword_india_aadhar"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_india_aadhaar"/>
  </Pattern>
</Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- aadhar
- aadhar #
- uid
- आधार
- uidai


## <a name="india-voter-id-card"></a>India Voter Id Card

### <a name="format"></a>Formatowanie

10-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

10 liter lub cyfr:
- Trzy litery
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_india_voter_id_card` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_india_voter_id_card` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_india_voter_id_card` znalezienie zawartości, która odpowiada wzorcowi.


```xml
      <!-- India Voter Id Card  -->
        <Entity id="646d643f-5228-4408-acc8-f2e81a6df897" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
           <Pattern confidenceLevel="75">
             <IdMatch idRef="Regex_india_voter_id_card" />
             <Match idRef="Keyword_india_voter_id_card" />
            </Pattern>
           <Pattern confidenceLevel="65">
              <IdMatch idRef="Regex_india_voter_id_card" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- głosujący
- voterid
- karta wyborcza
- voteridcard
- Karta tożsamości ze zdjęciem e wyeksymrowa
- ODTĄD
- ECI
- komunikowanie wyborów


## <a name="indonesia-identity-card-ktp-number"></a>Numer karty tożsamości Indonezyjskiej (KTP)

### <a name="format"></a>Formatowanie

16 cyfr zawierające kropki opcjonalne

### <a name="pattern"></a>Deseń

16 cyfr:
- Dwucyfrowy kod prowincji
- Okres (opcjonalny)
- Dwucyfrowy regency lub kod miasta
- Dwucyfrowy kod podrzędny
- Okres (opcjonalny)
- Sześć cyfr w formacie DDMMYY, czyli data urodzenia
- Okres (opcjonalny)
- Cztery cyfry

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Wyrażenie regularne Regex_indonesia_id_card umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z Keyword_indonesia_id_card znajduje się.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk
- Nomor Induk Kependudukan

## <a name="international-banking-account-number-iban"></a>Numer konta bankowego międzynarodowego (IBAN)

### <a name="format"></a>Formatowanie

Kod kraju (dwie litery) oraz cyfry wyboru (dwie cyfry) oraz numer bban (do 30 znaków)

### <a name="pattern"></a>Deseń

Wzorzec musi zawierać wszystkie następujące elementy:

- Dwulitowy kod kraju
- Dwie cyfry sprawdzania (po niej spacja opcjonalna)
- 1–7 grup po czterech literach lub cyfrach (można je rozdzielić spacjami)
- 1-3 litery lub cyfry

Format poszczególnych krajów jest nieco inny. Typ informacji poufnych IBAN obejmuje te 60 krajów:

- ad
- ae
- al
- o godzinie
- az
- ba
- be
- bg
- bh
- ch
- cr
- cy
- cz
- de
- dk
- wykonaj
- ee
- es
- fi
- cy
- fr
- gb
- ge
- gi
- gl
- gr
- z o.o.
- hu
- ie
- il
- jest
- it
- kw
- kz
- lb
- li
- lt
- lu
- lv
- mc
- md
- ja
- mk
- mr
- mt
- mu
- nl
- nie
- pl
- pt
- ro
- rs
- sa
- se
- si
- sk
- sm
- tn
- tr
- vg

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Funkcja Func_iban znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

Brak


## <a name="international-classification-of-diseases-icd-10-cm"></a>Międzynarodowa klasyfikacja kwalifikacji (ICD-10-CM)

### <a name="format"></a>Formatowanie

Słownik

### <a name="pattern"></a>Deseń

Słowo kluczowe

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Zostanie znalezione słowo kluczowe Dictionary_icd_10_updated.
- Zostanie znalezione słowo kluczowe Dictionary_icd_10_codes.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Słowo kluczowe ze Dictionary_icd_10_ zostanie znalezione.

```xml
      <!-- ICD-10 CM -->
      <Entity id="3356946c-6bb7-449b-b253-6ffa419c0ce7" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_10_updated" />
          <Match idRef="Dictionary_icd_10_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_10_updated" />
        </Pattern>

```

### <a name="keywords"></a>Słowa kluczowe

Dowolny termin ze słownika Dictionary_icd_10_updated słów kluczowych, który jest oparty na klasyfikacji międzynarodowej zmian, dziesiątej poprawki i modyfikacji choroby [choroby (ICD-10-CM).](https://go.microsoft.com/fwlink/?linkid=852604). Ten typ wyszukuje tylko termin, a nie kody ubezpieczenia.

Dowolny termin ze słownika słów kluczowych Dictionary_icd_10_codes, który jest oparty na klasyfikacji międzynarodowej, dziesiątej poprawki i modyfikacji choroby [choroby (ICD-10-CM).](https://go.microsoft.com/fwlink/?linkid=852604). Ten typ wyszukuje tylko kody ubezpieczenia, a nie opis.


## <a name="international-classification-of-diseases-icd-9-cm"></a>Międzynarodowa klasyfikacja kwalifikacji (ICD-9-CM)

### <a name="format"></a>Formatowanie

Słownik

### <a name="pattern"></a>Deseń

Słowo kluczowe

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Zostanie znalezione słowo kluczowe Dictionary_icd_9_updated.
- Słowo kluczowe z Dictionary_icd_9_codes znajduje się.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Zostanie znalezione słowo kluczowe Dictionary_icd_9_updated.

```xml
    <Entity id="fa3f9c74-ee07-4c52-b5f2-085d6b2c0ec4" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_9_updated" />
          <Match idRef="Dictionary_icd_9_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_9_updated" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

Dowolny termin ze słownika Dictionary_icd_9_updated słów kluczowych, który jest oparty na klasyfikacji międzynarodowej jeden na jedenastej poprawki, modyfikacje klinicznych [(ICD-9-CM).](https://go.microsoft.com/fwlink/?linkid=852605) Ten typ wyszukuje tylko termin, a nie kody ubezpieczenia.

Dowolny termin ze słownika Dictionary_icd_9_codes słów kluczowych, który jest oparty na klasyfikacji międzynarodowej na podstawie klasyfikacji międzynarodowej, dziewiątej poprawki [, modyfikacji klinicznych (ICD-9-CM).](https://go.microsoft.com/fwlink/?linkid=852605). Ten typ wyszukuje tylko kody ubezpieczenia, a nie opis.

## <a name="ip-address"></a>Adres IP

### <a name="format"></a>Formatowanie

#### <a name="ipv4"></a>IPv4:
Złożony wzorzec, który uwzględnia sformatowane (kropki) i niesformatowane (bez okresów) wersje adresów IPv4

#### <a name="ipv6"></a>IPv6:
Złożony wzorzec, który uwzględnia sformatowane liczby IPv6 (który zawiera dwukropki)

### <a name="pattern"></a>Deseń

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

W przypadku protokołu IPv6 zasady DLP mają wysoką pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_ipv6_address umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Nie można odnaleźć słowa kluczowego Keyword_ipaddress.

W przypadku protokołu IPv4 zasady DLP mają wysoką pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_ipv4_address umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_ipaddress.

W przypadku protokołu IPv6 zasady DLP mają wysoką pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_ipv6_address umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Nie można odnaleźć słowa kluczowego Keyword_ipaddress.

```xml
    <!-- IP Address --> 
    <Entity id="1daa4ad5-e2dd-4ca4-a788-54722c09efb2" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv4_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (to słowo kluczowe zróżnicuje wielkość liter)
- adres IP
- adresy IP
- protokół internetowy
- IP-כתובת  ש


## <a name="ip-address-v4"></a>Adres IP w wersji 4

### <a name="format"></a>Formatowanie

Złożony wzorzec, który uwzględnia sformatowane (kropki) i niesformatowane (bez okresów) wersje adresów IPv4

### <a name="pattern"></a>Deseń


### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_ipv4_address` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_ipaddress` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_ipv4_address` znalezienie zawartości, która odpowiada wzorcowi.


```xml
      <!-- IP Address v4--> 
      <Entity id="a7dd5e5f-e7f9-4626-a2c6-86a8cb6830d2" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv4_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv4_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (zróżnicowa wielkość liter)
- adres IP
- adresy IP
- protokół internetowy
- IP-כתובת  ש


## <a name="ip-address-v6"></a>Adres IP w wersji 6

### <a name="format"></a>Formatowanie

Złożony wzorzec, który uwzględnia sformatowane liczby IPv6 (który zawiera dwukropki)

### <a name="pattern"></a>Deseń


### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_ipv6_address` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_ipaddress` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_ipv6_address` znalezienie zawartości, która odpowiada wzorcowi.


```xml
      <!-- IP Address v6-->
      <Entity id="3f691089-7413-4926-ab3b-3c5ea8a1c17e" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv6_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv6_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (zróżnicowa wielkość liter)
- adres IP
- adresy IP
- protokół internetowy
- IP-כתובת  ש


## <a name="ireland-drivers-license-number"></a>Numer prawa jazdy Irlandii

### <a name="format"></a>Formatowanie

Sześć cyfr, po których następuje cztery litery

### <a name="pattern"></a>Deseń

Sześć cyfr i cztery litery:

- Sześć cyfr
- Cztery litery (bez wielkości liter)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:

- Wyrażenie regularne umożliwia  `Regex_ireland_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_ireland_eu_driver's_license_number` znajduje się.

```xml
      <!-- Ireland Driver's License Number -->
      <Entity id="e01bccd9-eb4d-414f-ace1-e9b6a4c4a2ca" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_ireland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver s_license_number

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>Numer paszportu Irlandii

### <a name="format"></a>Formatowanie

Dwie litery i cyfry, po których następuje siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Dwie litery lub cyfry, po których następuje siedem cyfr:

- Dwie cyfry lub litery (bez wielkości liter)
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_ireland_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_ireland_eu_passport_number` znajduje się.
- Wyrażenie regularne umożliwia `Regex_ireland_eu_passport_date` znalezienie daty w formacie DD MMM/MMM YYYY (przykład — 01 BEA/MAY 1988) `Keywords_eu_passport_date` lub słowa kluczowego od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_ireland_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_ireland_eu_passport_number` znajduje się.

```xml
      <!-- Ireland Passport Number -->
      <Entity id="a2130f27-9ee2-4103-84f9-a6b1ee7d0cbf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_ireland_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha papanna
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cárta
- uimhir chárta

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="ireland-personal-public-service-pps-number"></a>Numer usługi publicznej w Irlandii (PPS)

### <a name="format"></a>Formatowanie

Stary format (do 31 grudnia 2012 r.):
- Siedem cyfr i 1-2 litery

Nowy format (1 stycznia 2013 i później):
- Siedem cyfr, po których następuje dwie litery

### <a name="pattern"></a>Deseń

Stary format (do 31 grudnia 2012 r.):
- Siedem cyfr
- od jednego do dwóch liter (bez wielkości liter)

Nowy format (1 stycznia 2013 i później):
- Siedem cyfr
- literę (bez rozróżnianą wielkości liter), która jest cyfrą sprawdzania alfabetycznego
- Opcjonalna litera z zakresu od A do I lub "W"

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_ireland_pps wyszukuje zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keywords_ireland_eu_national_id_card.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_ireland_pps wyszukuje zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
      <!-- Ireland Personal Public Service (PPS) Number -->
      <Entity id="1cdb674d-c19a-4fcf-9f4b-7f56cc87345a" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_ireland_pps" />
          <Match idRef="Keywords_ireland_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_ireland_pps" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- usługa tożsamości klienta
- numer identyfikacyjny
- identyfikator osobisty
- osobisty numer usługi publicznej
- usługa osobista nie
- phearsantarbhíse poiblí
- pps no
- numer pps
- liczba pps
- Nie usługi pps
- ppsn
- ppsno #
- ppsno
- psp
- nie usługi publicznej
- publicserviceno #
- publicserviceno
- numer przychodów i ubezpieczenia społecznego
- rsi no
- liczba rsi
- rsin
- rbhís aitheantais client
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta przedzmierowejíse poiblí
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="ireland-physical-addresses"></a>Adresy fizyczne w Irlandii

Ta nieoznakowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym Irlandii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="israel-bank-account-number"></a>Izrael : numer konta bankowego

### <a name="format"></a>Formatowanie

13 cyfr

### <a name="pattern"></a>Deseń

Sformatowane:
- dwie cyfry
- kreska
- trzy cyfry
- kreska
- osiem cyfr

Niesformatowane:
- 13 kolejnych cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_israel_bank_account_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_israel_bank_account_number.

```xml
<!-- Israel Bank Account Number -->
<Entity id="7d08b2ff-a0b9-437f-957c-aeddbf9b2b25" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_israel_bank_account_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_israel_bank_account_number" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- Numer konta bankowego
- Konto bankowe
- Numer konta
- מספר חשבון בנק


## <a name="israel-national-identification-number"></a>Numer identyfikacyjny kraju Izrael

### <a name="format"></a>Formatowanie

dziewięć cyfr

### <a name="pattern"></a>Deseń

Dziewięć kolejnych cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_israeli_national_id_number znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_Israel_National_ID znajduje się.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Israel National ID Number -->
<Entity id="e05881f5-1db1-418c-89aa-a3ac5c5277ee" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_israeli_national_id_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_Israel_National_ID" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

-   מספר זהות
-   מספר זיה וי
-   מספר זיהוי ישר אלי      
-   זהותישר אלית
-   هو ية اسرائيل ية عدد
-   هوية إسرائ يلية
-   رقم الهوية
-   عدد هوية فريدة من نوعها
-   idnumber #
-   numer identyfikacyjny
-   nie tożsamości        
-   identitynumber #
-   numer tożsamości
-   izraelskaidentyfik       
-   identyfikator osobisty
-   unikatowy identyfikator  


## <a name="italy-drivers-license-number"></a>Włochy : numer prawa jazdy

Ten typ jednostki jest uwzględniony w poufnym typie informacji Numer prawa jazdy w UE. Jest także dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formatowanie

Kombinacja 10 liter i cyfr

### <a name="pattern"></a>Deseń

Kombinacja 10 liter i cyfr:
- jedna litera (bez wielkości liter)
- litera "A" lub "V" (bez wielkości liter)
- Siedem cyfr
- jedna litera (bez wielkości liter)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia `Regex_italy_drivers_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z `Keywords_eu_driver's_license_number` lub `Keyword_italy_drivers_license_number` znajduje się.

```xml
    <!-- Italy Driver's license Number -->
    <Entity id="97d6244f-9157-41bd-8e0c-9d669a5c4d71" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_italy_drivers_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keyword_italy_drivers_license_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- numero di patentu
- patente di guida
- patent Guida
- patenti di guida
- patenti guida


## <a name="italy-fiscal-code"></a>Kod obrachunkowy Włoch
Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

16-znakowa kombinacja liter i cyfr we wskazanym wzorcu

### <a name="pattern"></a>Deseń

16-znakowa kombinacja liter i cyfr:
- Trzy litery odpowiadające trzem pierwszym spółgłosom w nazwie rodziny
- Trzy litery odpowiadające pierwszej, trzeciej i czwartej spółgłosce imienia
- Dwie cyfry odpowiadające ostatnim cyfrom roku urodzenia
- Jedna litera odpowiadająca literze dla miesiąca urodzenia — litery są używane w kolejności alfabetycznej, ale używane są tylko litery od A do E, H, L, M, P, R do T (tak więc styczeń to A, a październik to R)
- dwie cyfry odpowiadające dniu miesiąca urodzenia w celu rozróżnienia płci, do dnia urodzenia kobiety dodaje się 40 cyfr.
- cztery cyfry odpowiadające numerowi kierunkowemu odpowiadającemu miejsca urodzenia danej osoby (kody dla całego kraju są używane w krajach obcych)
- jedna cyfra parowa

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_italy_eu_national_id_card` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_italy_eu_national_id_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_italy_eu_national_id_card` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Italy Fiscal Code -->
      <Entity id="4cd79172-8da9-4ff5-9188-98b1e7e2eca6" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
          <Match idRef="Keywords_italy_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice fiscal
- codice fiscale
- codice id personale
- codice personale
- kod obrachunkowy
- numero certificato personale
- numero di identificazione fiscale
- numero id personale
- numero personale
- numer certyfikatu osobistego
- kod osobisty
- identyfikator osobisty
- identyfikator osobisty
- kod_osobisty #
- kod podatku
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- numer identyfikacji podatkowej
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="italy-passport-number"></a>Numer paszportu Włoch

### <a name="format"></a>Formatowanie

Dwie litery lub cyfry, po których następuje siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dwie litery lub cyfry, po których następuje siedem cyfr:

- Dwie cyfry lub litery (bez wielkości liter)
- Siedem cyfr

### <a name="checksum"></a>Checksum

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_italy_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_italy_eu_passport_number` znajduje się.
- Wyrażenie regularne `Regex_italy_eu_passport_date` umożliwia znalezienie daty w formacie DD MMM/MMM YYYY (przykład — 01 GEN/STY 1988) `Keywords_eu_passport_date` lub słowa kluczowego od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_italy_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_italy_eu_passport_number` znajduje się.

```xml
      <!-- Italy Passport Number -->
      <Entity id="39811019-4750-445f-b26d-4c0e6c431544" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_italy_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto numero
- numéro passeport
- numero di passaporto
- numeri del passaporto
- passeport italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="italy-physical-addresses"></a>Włochy adresy fizyczne

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Włoch. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="italy-value-added-tax-number"></a>Włochy o wartości dodanej numeru podatkowego

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

13-znakowy wzorzec alfanumeryczny z opcjonalnymi ogranicznikami

### <a name="pattern"></a>Deseń

13-znakowy wzorzec alfanumeryczny z opcjonalnymi ogranicznikami:

- I lub i
- T lub t
- spacja, kropka, łącznik lub przecinek
- 11 cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_italy_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keywords_italy_value_added_tax_number znajduje się.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_italy_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- Italy Value Added Tax -->
      <Entity id="26a8cc07-2283-4a2a-ab1d-4ab643c4c67f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
          <Match idRef="Keywords_italy_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- numer VAT
- bez podatku VAT
- vat #
- iva
- iva #


## <a name="japan-bank-account-number"></a>Numer konta bankowego w Japonii

### <a name="format"></a>Formatowanie

Siedem lub osiem cyfr

### <a name="pattern"></a>Deseń

numer konta bankowego:
- Siedem lub osiem cyfr
- Kod oddziału konta bankowego:
- cztery cyfry
- spacja lub kreska (opcjonalnie)
- trzy cyfry

Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_jp_bank_account znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_jp_bank_account.
- Prawdziwe jest jedno z następujących argumentów:
- Funkcja Func_jp_bank_account_branch_code znajdzie zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_jp_bank_branch_code.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_jp_bank_account znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_jp_bank_account.

```xml
<!-- Japan Bank Account Number -->
<Entity id="d354f95b-96ee-4b80-80bc-4377312b55bc" patternsProximity="300" recommendedConfidence="75">
  <Version minEngineVersion="15.01.0131.000">
    <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_jp_bank_account" />
          <Match idRef="Keyword_jp_bank_account" />
          <Any minMatches="1">
            <Match idRef="Func_jp_bank_account_branch_code" />
            <Match idRef="Keyword_jp_bank_branch_code" />
          </Any>
      </Pattern>
  </Version>
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_bank_account" />
        <Match idRef="Keyword_jp_bank_account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- Sprawdzanie numeru konta
- Sprawdzanie konta
- Sprawdzanie konta #
- Sprawdzanie numeru ACCT
- Sprawdzanie acct #
- Sprawdzanie nie.
- Sprawdzanie, czy nie ma konta.
- Numer konta bankowego
- Konto bankowe
- Konto bankowe #
- Bank Acct Number
- Bank Acct #
- Bank Acct Nie.
- Nr konta bankowego
- Numer konta oszczędnościowego
- Konto oszczędnościowe
- Konto oszczędnościowe #
- Numer Acct oszczędności
- Savings Acct #
- Nr konta oszczędnościowego
- Numer konta oszczędnościowego
- Numer konta debetowego
- Konto debetowe
- Konto debetowe #
- Numer acct debetowego
- Acct polecenia debetowego #
- Nr konta debetowego
- Nie.
- 口座番号
- 銀行口座
- 銀行口座番号
- 総合口座
- 普通預金口座
- 普通口座
- 当座預金口座
- 当座口座
- 預金口座
- 振替口座
- 銀行
- バンク

#### <a name="keyword_jp_bank_branch_code"></a>Keyword_jp_bank_branch_code

- 支店番号
- 支店コード
- 店番号

## <a name="japan-drivers-license-number"></a>Numer prawa jazdy w Japonii

### <a name="format"></a>Formatowanie

12 cyfr

### <a name="pattern"></a>Deseń

12 kolejnych cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_jp_drivers_license_number wyszukuje zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_jp_drivers_license_number.

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- driverlicense
- driverslicense
- driver'slicense
- driverslicenses
- fragmentatory sterownika
- driverlicenses
- dl #
- dls #
- lic #
- kursywa #
- 運転免許証
- 運転免許
- 免許証
- 免許
- 運転免許証番号
- 運転免許番号
- 免許証番号
- 免許番号
- 運転免許証ナンバー
- 運転免許ナンバー
- 免許証ナンバー
- 運転免許証no
- 運転免許no
- 免許証no
- 免許no
- 運転経歴証明書番号
- 運転経歴証明書
- 運転免許証No.
- 運転免許No.
- 免許証No.
- 免許No.
- 運転免許証 #
- 運転免許 #
- 免許証 #
- 免許 #


## <a name="japan-my-number---corporate"></a>Japonia — Mój numer — firmowy

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

13-cyfrowy numer

### <a name="pattern"></a>Deseń

Numer 13-cyfrowy:

- Od jednej cyfry do dziewięciu
- 12 cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_japanese_my_number_corporate umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z Keywords_japanese_my_number_corporate znajduje się.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_japanese_my_number_corporate umożliwia znalezienie zawartości, która odpowiada wzorcowi.

```xml
      <!-- Japanese My Number – Corporate -->
      <Entity id="9e0eaf79-ff20-4ffb-b3e4-e7368d5db6ff" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
          <Match idRef="Keywords_japanese_my_number_corporate" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_japan_my_number_corporate"></a>Keyword_japan_my_number_corporate

- numer firmowy
- マイナンバー
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 法人番号
- 指定通知書


## <a name="japan-my-number---personal"></a>Japonia — Mój numer — Osobiste

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

12-cyfrowy numer

### <a name="pattern"></a>Deseń

Numer 12-cyfrowy:

- cztery cyfry
- Opcjonalna spacja, kropka lub łącznik
- cztery cyfry
- Opcjonalna spacja, kropka lub łącznik
- cztery cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_japanese_my_number_personal umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keywords_japanese_my_number_personal.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_japanese_my_number_personal umożliwia znalezienie zawartości, która odpowiada wzorcowi.

```xml
      <!-- Japanese My Number – Personal -->
      <Entity id="98da8e66-7299-4ebd-9f82-c871ab37d3ef" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_personal" />
          <Match idRef="Keywords_japanese_my_number_personal" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_japanese_my_number_personal" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_japan_my_number_personal"></a>Keyword_japan_my_number_personal

- mój numer
- マイナンバー
- 個人番号
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 通知カード


## <a name="japan-passport-number"></a>Numer paszportu Japonii

### <a name="format"></a>Formatowanie

Dwie litery, po których następuje siedem cyfr

### <a name="pattern"></a>Deseń

Dwie litery (bez wielkości liter), po których następuje siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_jp_passport znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_jp_passport.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- Paszport
- Numer paszportu
- Numer paszportu.
- Paszport #
- パスポート
- パスポート番号
- パスポートナンバー
- パスポート＃
- パスポート #
- パスポートNo.
- 旅券番号
- 旅券番号＃
- 旅券番号♯
- 旅券ナンバー


## <a name="japan-residence-card-number"></a>Numer japońskiej karty zamieszkania

### <a name="format"></a>Formatowanie

12 liter i cyfr

### <a name="pattern"></a>Deseń

12 liter i cyfr:
- Dwie litery (bez wielkości liter)
- osiem cyfr
- Dwie litery (bez wielkości liter)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_jp_residence_card_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z Keyword_jp_residence_card_number znajduje się.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- Numer karty zamieszkania
- Nie karty zamieszkania
- Karta zamieszkania #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Numer rejestracji rezydenta Japonii

### <a name="format"></a>Formatowanie

11 cyfr

### <a name="pattern"></a>Deseń

11 kolejnych cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_jp_resident_registration_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_jp_resident_registration_number.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- Numer rejestracji rezydentnia
- Residents Basic Registry Number
- Numer rejestracji rezydenta.
- Rezydentny rejestr nie.
- Nie rejestru dla mieszkańców.
- Podstawowy rejestr rezydentny nie.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証


## <a name="japan-social-insurance-number-sin"></a>Japoński numer ubezpieczenia społecznego (SIN)

### <a name="format"></a>Formatowanie

7-12 cyfr

### <a name="pattern"></a>Deseń

7-12 cyfr:
- cztery cyfry
- Łącznik (opcjonalny)
- Sześć cyfr LUB
- Od 7 do 12 kolejnych cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_jp_sin znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_jp_sin.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_jp_sin_pre_1997 umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_jp_sin.

```xml
<!-- Japan Social Insurance Number -->
<Entity id="c840e719-0896-45bb-84fd-1ed5c95e45ff" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_jp_sin" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_sin_pre_1997" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- Nr ubezpieczenia społecznego
- Nr ubezpieczenia społecznego
- Numer ubezpieczenia społecznego
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 社会保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号


## <a name="lab-test-terms"></a>Warunki testowania laboratorium

Ta nieoznakowana nazwana jednostka wykrywa terminy związane z testami laboratoryjnymi, takie jak *NarkońC*. Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)


## <a name="latvia-drivers-license-number"></a>Łotewski numer prawa jazdy

### <a name="format"></a>Formatowanie

Trzy litery, po których następuje sześć cyfr

### <a name="pattern"></a>Deseń

Trzy litery i sześć cyfr:

- Trzy litery (bez wielkości liter)
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_latvia_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_latvia_eu_driver's_license_number` znajduje się.

```xml
      <!-- Latvia Driver's License Number -->
      <Entity id="ec996de0-30f2-46b1-b192-4d2ff8805fa7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_latvia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_latvia_eu_drivers_license_number"></a>Keywords_latvia_eu_driver nie s_license_number

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība


## <a name="latvia-passport-number"></a>Numer paszportu Łotwy

### <a name="format"></a>Formatowanie

Dwie litery lub cyfry, po których następuje siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dwie litery lub cyfry, po których następuje siedem cyfr:

- Dwie cyfry lub litery (bez wielkości liter)
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_latvia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_latvia_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_latvia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_latvia_eu_passport_number` znajduje się.

```xml
      <!-- Latvia Passport Number -->
      <Entity id="23ae25ec-cc28-421b-b77a-3054eadf1ede" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase numury
- pase numur
- pases numuri
- pases nr
- passeport no
- n° du Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="latvia-personal-code"></a>Łotewski kod osobisty

### <a name="format"></a>Formatowanie

11 cyfr i opcjonalny łącznik

### <a name="pattern"></a>Deseń

Stary format

11 cyfr i łącznik:

- Sześć cyfr odpowiadających dacie urodzenia (DDMMYY)
- Łącznik
- jedna cyfra odpowiadająca wiekowi urodzenia ("0" dla WIEKU 19, "1" dla 20 wieku i "2" dla 21 wieku)
- Cztery cyfry wygenerowane losowo

Nowy format

11 cyfr

- Dwie cyfry "32"
- Dziewięć cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub  `Func_latvia_eu_national_id_card` regex `Regex_latvia_eu_national_id_card_new_format` umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_latvia_eu_national_id_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub  `Func_latvia_eu_national_id_card` regex `Regex_latvia_eu_national_id_card_new_format` umożliwia znalezienie zawartości, która odpowiada wzorcowi.

```xml
      <!-- Latvia Personal Code -->
      <Entity id="03fcf763-27c2-49ed-9422-2641c6c895c9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- numer administracyjny
- aylwania nē
- numer urodzenia
- numer edytowy
- numer służbowy
- Numer elektronicznego systemu danych cenowych
- numer elektroniczny
- kod obrachunkowy
- numer użytkownika opieki zdrowotnej
- identyfikator #
- id-code
- numer identyfikacyjny
- identifikācijas numurs
- id-number
- numer indywidualny
- latvija alva
- nacionālais id
- identyfikator narodowy
- numer identyfikacyjny kraju
- numer tożsamości państwowej
- numer ubezpieczenia państwowego
- numer rejestru krajowego
- nodok jako numury
- nodok do id
- nodok do identifikācija numurs
- numer certyfikatu osobistego
- kod osobisty
- identyfikator osobisty
- identyfikator osobisty
- kod identyfikacyjny
- identyfikator osobisty
- numer tożsamości osobistej
- numer osobisty
- osobisty kod numeryczny
- kod_osobisty #
- kody personas
- kod identyfikacyjny populacji
- numer usługi publicznej
- numer rejestracji
- numer przychodu
- numer ubezpieczenia społecznego
- numer PEZEt
- kod podatku stanowego
- numer pliku podatkowego
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- Numer osób głosujących


## <a name="latvia-physical-addresses"></a>Łotewskie adresy fizyczne

Ta niepowiązona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Łotwy. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="liechtenstein-physical-addresses"></a>Adresy fizyczne Liechtensteinu

Ta nieoznazona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Liechtensteinu. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT. 

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="lifestyles-that-relate-to-medical-conditions"></a>Style życia związane ze stanem zdrowia

Ta nieoznazona nazwana jednostka wykrywa terminy związane z stylami życia, które mogą powodować stan zdrowia, taki jak zakaz *kamicy.* Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)


## <a name="lithuania-drivers-license-number"></a>Litwa numer prawa jazdy

### <a name="format"></a>Formatowanie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_lithuania_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_lithuania_eu_driver's_license_number` znajduje się.

```xml
      <!-- Lithuania Driver's License Number -->
      <Entity id="86f7628b-e0f4-4dc3-9fbc-e4300e4c7d78" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_lithuania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver nie s_license_number

- vairuotojo pakovymjimas
- vairuotojo pa zamówić numeris
- vairuotojo pa zamówić numeriai


## <a name="lithuania-personal-code"></a>Litwa : kod osobisty

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

11 cyfr bez spacji i ograniczników:

- jedna cyfra (1-6) odpowiadająca płci i wieku urodzenia danej osoby
- Sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- Trzy cyfry odpowiadające kolejnemu numerowi daty urodzenia
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_lithuania_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_lithuania_eu_tax_file_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_lithuania_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Lithuania Personal Code -->
      <Entity id="cd6d3786-8ec3-4524-a2cf-1e0095379171" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Match idRef="Keywords_lithuania_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_lithuania_eu_telephone_number" />
            <Match idRef="Keywords_lithuania_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- numer usługi
- mokesčiči id
- mokesči do identifikavimas numeris
- mokesči do identifikavimo numeris
- mokesči do numeris
- numer identyfikacyjny kraju
- kod osobisty
- osobisty kod numeryczny
- piliečio paslaugos numeris
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #


## <a name="lithuania-physical-addresses"></a>Adresy fizyczne Litwy

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z  Litwa. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="lithuania-passport-number"></a>Numer paszportu Litwy

### <a name="format"></a>Formatowanie

Osiem cyfr lub liter bez spacji i ograniczników

### <a name="pattern"></a>Deseń

osiem cyfr lub liter (bez wielkości liter)

### <a name="checksum"></a>Checksum

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_lithuania_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_lithuania_eu_passport_number` znajduje się.
- Wyrażenie regularne umożliwia `Regex_eu_passport_date3` znalezienie daty w formacie DD MM YYYY lub znalezione słowo kluczowe `Keywords_eu_passport_date` od

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_lithuania_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_lithuania_eu_passport_number` znajduje się.

```xml
      <!-- Lithuania Passport Number -->
      <Entity id="1b79900f-047b-4c3f-846f-7d73b5534bce" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- paso numeris
- paso numeriai
- paso nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="luxemburg-drivers-license-number"></a>Numer prawa jazdy firmy Luxemburg

### <a name="format"></a>Formatowanie

Sześć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_luxemburg_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_luxemburg_eu_driver's_license_number` znajduje się.

```xml
      <!-- Luxemburg Driver's License Number -->
      <Entity id="89daf717-1544-4860-9a2e-fc9166dd8852" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_luxemburg_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver s_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Luxemburg national identification number (natural persons)

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

13 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

13 cyfr:

- 11 cyfr
- dwie cyfry sprawdzania

### <a name="checksum"></a>Checksum

tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_luxemburg_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_luxemburg_eu_national_id_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_luxemburg_eu_tax_file_number` zawartość, która odpowiada wzorcowi.


```xml
      <!-- Luxemburg National Identification Number (Natural persons) -->
      <Entity id="aaf661ed-29ec-426d-8bf9-880cad298ebb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Match idRef="Keywords_luxemburg_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- identyfikator eindeutige
- eindeutige id-nummer
- eindeutigeid #
- id personnelle
- idpersonnelle #
- idpersonnelle
- indywidualny kod
- identyfikator indywidualny
- identyfikacja poszczególnych osób
- tożsamość poszczegomowa
- numéro d'identification personnel
- identyfikator osobisty
- identyfikacja osobista
- tożsamość osobista
- personalidno #
- numer_osobisty #
- persönliche identifikationsnummer
- unikatowy identyfikator
- unikatowa tożsamość
- klucz uniqueid #


## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Państwowy numer identyfikacyjny Luxemburg (osoby nie naturalne)

### <a name="format"></a>Formatowanie

11 cyfr

### <a name="pattern"></a>Deseń

11 cyfr

- dwie cyfry
- spacja opcjonalna
- trzy cyfry
- spacja opcjonalna
- trzy cyfry
- spacja opcjonalna
- dwie cyfry
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_luxemburg_eu_tax_file_number_non_natural` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_luxemburg_eu_tax_file_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_luxemburg_eu_tax_file_number_non_natural` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Luxemburg National Identification Number (Non-natural persons) -->
      <Entity id="84bffa3a-d805-4788-a613-b1e4df3804cf" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Match idRef="Keywords_luxemburg_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- étain non
- étain #
- identifiant d'impôt
- luxembourg tax identifikatiounsnummer
- numéro d'étain
- numéro d'identification fiscal luxembourgeois
- numéro d'identification fiscale
- ubezpieczenia społecznego
- soziaterstützung
- sozialversécherung
- sozialversicherungsausweis
- identyfikator steiera
- steier identifikatiounsnummer
- steier nummer
- id użytkownika
- steueridentifikationsnummer
- steuernummer
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- zinn #
- zinn
- zinnzahl


## <a name="luxemburg-passport-number"></a>Numer paszportu Luksemburga

### <a name="format"></a>Formatowanie

Osiem cyfr lub liter bez spacji i ograniczników

### <a name="pattern"></a>Deseń

osiem cyfr lub liter (bez wielkości liter)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_luxemburg_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_luxemburg_eu_passport_number` znajduje się.
- Wyrażenie regularne umożliwia `Regex_eu_passport_date3` znalezienie daty w formacie DD MM YYYY lub znalezione słowo kluczowe `Keywords_eu_passport_date` od

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_luxemburg_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_luxemburg_eu_passport_number` znajduje się.

```xml
      <!-- Luxemburg Passport Number -->
      <Entity id="81d5c027-bed9-4421-91a0-3b2e55b3eb85" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- Luxembourg Pass
- Luxembourg Passeport
- Paszport Luksemburga
- no de passeport
- no-reisepass
- nr-reisepass
- numéro de passeport
- sieć przechodnia
- pass nr
- passnummer
- passeport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="luxemburg-physical-addresses"></a>Adresy fizyczne w Luxemburgu

Ta nieoznaczana nazwana jednostka wykrywa wzorce związane z adresem fizycznym firmy Luxemburg. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="malaysia-identification-card-number"></a>Numer karty identyfikacyjnej Malezji

### <a name="format"></a>Formatowanie

12 cyfr zawierające łączniki opcjonalne

### <a name="pattern"></a>Deseń

12 cyfr:
- Sześć cyfr w formacie RRMMDD, czyli data urodzenia
- kreska (opcjonalnie)
- Dwulitowy kod miejsca urodzenia
- kreska (opcjonalnie)
- Trzy losowe cyfry
- Jednocyfrowy kod płci

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_malaysia_id_card_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z Keyword_malaysia_id_card_number znajduje się.

```xml
<!-- Malaysia ID Card Number -->
</Entity>
      <Entity id="7f0e921c-9677-435b-aba2-bb8f1013c749" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_malaysia_id_card_number" />
            <Match idRef="Keyword_malaysia_id_card_number" />
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- karta aplikacji cyfrowej
- i/c
- nie i/c
- ic
- ic no
- identyfikator
- karta identyfikacyj
- karta tożsamości
- k/p
- k/p nie
- gdy akuan diri
- gdy aplikasi cyfrowy
- pengenalan malaysia
- kp
- kp nie
- mykad
- mykas
- mykid
- mypr
- mytentera
- Malaysia identity card
- Malaysian identity card
- nric
- osobista karta identyfikacyjna


## <a name="malta-drivers-license-number"></a>Numer prawa jazdy malta

### <a name="format"></a>Formatowanie

Kombinacja dwóch znaków i sześciu cyfr we wskazanym wzorcu

### <a name="pattern"></a>Deseń

kombinacja dwóch znaków i sześciu cyfr:

- dwa znaki (cyfry lub litery, bez wielkości liter)
- spacja (opcjonalnie)
- trzy cyfry
- spacja (opcjonalnie)
- trzy cyfry

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_malta_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_malta_eu_driver's_license_number` znajduje się.

```xml
      <!-- Malta Driver's License Number -->
      <Entity id="a3bdaa4a-8371-4735-8fa5-56ee0fb4afc4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_malta_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver nie s_license_number

- li doenzja tas-faqan
- li zam. tas-wąsów


## <a name="malta-identity-card-number"></a>Numer karty tożsamości malta

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Siedem cyfr, po których następuje jedna litera

### <a name="pattern"></a>Deseń

Siedem cyfr, po których następuje jedna litera:

- Siedem cyfr
- Jedna litera w "M, G, A, P, L, H, B, Z" (bez uwzględniania liter)

### <a name="checksum"></a>Checksum

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_malta_eu_national_id_card` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_malta_eu_national_id_card` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_malta_eu_national_id_card` znalezienie zawartości, która odpowiada wzorcowi.

```xml
      <!-- Malta Identity Card Number -->
      <Entity id="854b36b3-a388-4ac8-a4ec-677c2b5e4356" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
          <Match idRef="Keywords_malta_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- numer usługi
- id tat-taxxa
- identifika numru tal-biljett
- kodi jako numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz ta u-2ittadin
- numru tat-taxxa
- osobisty kod numeryczny
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #


## <a name="malta-passport-number"></a>Numer paszportu Malta

### <a name="format"></a>Formatowanie

Siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_malta_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_malta_eu_passport_number` znajduje się.
- Zostanie znalezione słowo `Keywords_eu_passport_date` kluczowe od

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_malta_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_malta_eu_passport_number` znajduje się.

```xml
      <!-- Malta Passport Number -->
      <Entity id="b2b21198-48f9-4d13-b2a5-03969bff0fb8" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
          <Match idRef="Keywords_eu_passport_date" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="malta-physical-addresses"></a>Adresy fizyczne malta

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Malta. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="malta-tax-identification-number"></a>Numer identyfikacji podatkowej Malta

### <a name="format"></a>Formatowanie

W celu odszukiwnia tego języka:
- Siedem cyfr i jedna litera we wskazanym wzorcu

Nie tylko na odszybkowo oraz jednostki te:
- dziewięć cyfr

### <a name="pattern"></a>Deseń

Nasyć w inne dni: siedem cyfr i jedna litera

- Siedem cyfr
- jedna litera (bez wielkości liter)

Nie tylko na odszybkowo oraz jednostki te: dziewięć cyfr

- dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Regex  `Regex_malta_eu_tax_file_number`  lub znajduje `Regex_malta_eu_tax_file_number_non_maltese_national` zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo  `Keywords_malta_eu_tax_file_number` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Regex  `Regex_malta_eu_tax_file_number` lub znajduje `Regex_malta_eu_tax_file_number_non_maltese_national` zawartość, która pasuje do wzorca.

```xml
      <!-- Malta Tax ID Number -->
      <Entity id="ec830c63-65f4-45d0-9d8c-910dc8334b20" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- numer usługi
- id tat-taxxa
- identifika numru tal-biljett
- kodi jako numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz ta u-2ittadin
- numru tat-taxxa
- osobisty kod numeryczny
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #

## <a name="medical-specialities"></a>Medycznej opieki lekarskiej

Ta nieoznazona nazwana jednostka wykrywa terminy związane z dokumentacją medyczną, takie jak *rybka*.  Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="medicare-beneficiary-identifier-mbi-card"></a>Karta identyfikatorów osób korzystających z usług opieki zdrowotnej (MBI)

### <a name="format"></a>Formatowanie

11-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

- Jedna cyfra między 1 a 9
- jedna litera z wyjątkiem liter S, L, O, I, B, Z
- jedna cyfra lub litera z wyłączeniem liter S, L, O, I, B, Z
- jedna cyfra
- Łącznik opcjonalny
- jedna litera z wyjątkiem liter S, L, O, I, B, Z
- jedna cyfra lub litera z wyłączeniem liter S, L, O, I, B, Z
- jedna cyfra
- Łącznik opcjonalny
- Dwie litery z wyjątkiem liter S, L, O, I, B, Z
- dwie cyfry

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_mbi_card` znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keyword_mbi_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_mbi_card` znalezienie zawartości, która odpowiada wzorcowi.

```xml
    <!-- Medicare Beneficiary Identifier (MBI) card -->
      <Entity id="f753a286-f5cc-47e6-a592-4be25fd02591" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_mbi_card" />
          <Match idRef="Keyword_mbi_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_mbi_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- mbi
- mbi #
- pracowników opieki zdrowotnej #
- identyfikator konta służbowego
- pracowników opieki zdrowotnej
- numer służbowy opieki zdrowotnej
- pracowników opieki zdrowotnej #


## <a name="mexico-unique-population-registry-code-curp"></a>Unikatowy kod rejestru populacji w Meksyku (CURP)

### <a name="format"></a>Formatowanie

18-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

- Cztery litery (bez uwzględniania liter)
- Sześć cyfr oznaczających prawidłową datę
- a letter - H/h lub M/m
- Dwa litery wskazujące prawidłowy kod stanu Meksyku
- Trzy litery
- jedna litera lub cyfra
- jedna cyfra

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_mexico_population_registry_code` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keyword_mexico_population_registry_code` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_mexico_population_registry_code` zawartość, która odpowiada wzorcowi.

```xml
    <!-- Mexico Unique Population Registry Code (CURP) -->
      <Entity id="e905ad4d-5a74-406d-bf36-b1efca798af4" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_mexico_population_registry_code" />
          <Match idRef="Keyword_mexico_population_registry_code" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_mexico_population_registry_code" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- Unikatowy kod rejestru populacji 
- unikatowy kod populacji
- CURP
- Identyfikator osobisty
- Unikatowy identyfikator
- personalid
- numer_osobisty
- klucz uniqueid
- uniqueidnumber
- clave única
- clave unica
- clave personal Identidad
- Osobista Identidad Clave
- ClaveÚnica
- Claveunica
- clavepersonalIdentidad


## <a name="netherlands-citizens-service-bsn-number"></a>Numer usługi holenderskiej (BSN)

### <a name="format"></a>Formatowanie

osiem lub dziewięć cyfr zawierających spacje opcjonalne

### <a name="pattern"></a>Deseń

osiemdziesiąt dziewięć cyfr:
- trzy cyfry
- spacja (opcjonalnie)
- trzy cyfry
- spacja (opcjonalnie)
- dwie-trzy cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_netherlands_bsn umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_netherlands_bsn.
- Pomyślnie przejdzie sprawdzanie.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- bsn #
- bsn
- servicenummer
- numer usługi
- numer osoby
- numer osobisty
- osobisty kod numeryczny
- numer powiązany z osobą
- persununlijk nummer
- persunlijke numerieke code
- persunsgebonden
- persunsnummer
- sociaal-fiscaal nummer
- social-fiscal number
- sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #


## <a name="netherlands-drivers-license-number"></a>Holenderski numer prawa jazdy

### <a name="format"></a>Formatowanie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

10 cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_netherlands_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_netherlands_eu_driver's_license_number` znajduje się.

```xml
      <!-- Netherlands Driver's License Number -->
      <Entity id="6247fbea-ab80-4be5-8233-308b7c031401" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_netherlands_eu_driver's_license_number" />
            </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver nie s_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers


## <a name="netherlands-passport-number"></a>Numer paszportu Holenderskiego

### <a name="format"></a>Formatowanie

Dziewięć liter lub cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

Dziewięć liter lub cyfr

### <a name="checksum"></a>Checksum

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_netherlands_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_netherlands_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_netherlands_eu_passport_date` datę w formacie DD MMM/MMM YYYY (przykład — 26 MAA/MAR 2012)

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_netherlands_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_netherlands_eu_passport_number` znajduje się.

```xml
      <!-- Netherlands Passport Number -->
      <Entity id="61786727-bafd-45f6-94d9-888d815e228e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Match idRef="Regex_netherlands_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- paspoort nummer
- paspoortnummers
- paspoortnummer
- paspoort nr


## <a name="netherlands-physical-addresses"></a>Holenderskie adresy fizyczne

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Holandia. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="netherlands-tax-identification-number"></a>Numer identyfikacji podatkowej Holandia

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_netherlands_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_netherlands_eu_tax_file_number` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_netherlands_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Netherlands Tax Identification Number -->
      <Entity id="01f42a64-eba7-4892-a67b-398237e4ade2" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
          <Match idRef="Keywords_netherlands_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- dokument identyfikacji podatkowej holla
- hulandes impuesto id number
- hulandes impuesto identification
- identificatienummer belasting
- identificatienummer van belasting
- impuesto identification number
- numer impuesto
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- Identyfikacja podatku holenderskiego
- identyfikacji podatkowej użytkownika Netherland
- Holenderskiej tezy
- tyg. Netherland
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- tal identyfikacji podatkowej
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- podatek tal
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="netherlands-value-added-tax-number"></a>Numer podatku od wartości dodanej w Niemczech

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

14-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

14-znakowy wzorzec alfanumeryczny:

- N lub n
- L lub l
- spacja, kropka lub łącznik (opcjonalnie)
- dziewięć cyfr
- spacja, kropka lub łącznik (opcjonalnie)
- B lub b
- dwie cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_netherlands_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keywords_netherlands_value_added_tax_number.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_netherlands_value_added_tax_number znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- Netherlands Value Added Tax Number -->
      <Entity id="4f320d9b-4972-41ae-b337-88d499bb1ade" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
          <Match idRef="Keywords_netherlands_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- numer VAT
- bez podatku VAT
- vat #
- wearde tafoege tax getal
- btw n≤mer
- btw-nummer


## <a name="new-zealand-bank-account-number"></a>Numer konta bankowego w Nowej Zelandii

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Wzorzec 14-cyfrowy do 16-cyfrowy z opcjonalnym ogranicznikiem

### <a name="pattern"></a>Deseń

Wzorzec 14-cyfrowy do 16-cyfrowy z opcjonalnym ogranicznikiem:

- dwie cyfry
- Łącznik opcjonalny lub spacja
- Od trzech do czterech cyfr
- Łącznik opcjonalny lub spacja
- Siedem cyfr
- Łącznik opcjonalny lub spacja
- Od dwóch do trzech cyfr
- Łącznik lub spacja opcji

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_new_zealand_bank_account_number wyszukuje zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keywords_new_zealand_bank_account_number.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_new_zealand_bank_account_number wyszukuje zawartość, która pasuje do wzorca.

```xml
      <!-- New Zealand Bank Account Number -->
      <Entity id="1a97fc2b-dd2f-48f1-bc4e-2ddf25813956" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
          <Match idRef="Keywords_new_zFealand_bank_account_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- numer konta
- konto bankowe
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr


## <a name="new-zealand-drivers-license-number"></a>Numer prawa jazdy nowej Zelandii

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Osiem znaków we wzorcu alfanumerycznym

### <a name="pattern"></a>Deseń

Osiem znaków we wzorcu alfanumerycznym

- dwie litery
- Sześć cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_newzealand_driver_license_number znajdzie zawartość, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keywords_newzealand_driver_license_number.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_newzealand_driver_license_number znajdzie zawartość, która jest taka, jak wzorzec.

```xml
      <!-- New Zealand Driver License Number -->
      <Entity id="1924b377-d287-49c9-a737-cfe7a8a2615a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
          <Match idRef="Keywords_newzealand_driver_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- driverlicence
- driverlicences
- lic sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- driverlic #
- driverlics #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- licencja sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- międzynarodowe zezwolenie na samochód
- międzynarodowe zezwolenia na samochód
- nz samochód skojarzenia
- Nowa Zelandia - Skojarzenie samochodów


## <a name="new-zealand-inland-revenue-number"></a>Nowa Zelandia o numerze przychodu na lądzie

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Osiem lub dziewięć cyfr z opcjonalnymi ogranicznikami

### <a name="pattern"></a>Deseń

Osiem lub dziewięć cyfr z opcjonalnymi ogranicznikami

- dwie lub trzy cyfry
- Opcjonalna spacja lub łącznik
- trzy cyfry
- Opcjonalna spacja lub łącznik
- trzy cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_new_zealand_inland_revenue_number znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keywords_new_zealand_inland_revenue_number znajduje się.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_new_zealand_inland_revenue_number znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- New Zealand Inland Revenue Number -->
      <Entity id="dd0fe2bc-7bcf-455f-bac1-83b1e3eb25fd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
          <Match idRef="Keywords_new_zealand_inland_revenue_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- nie.
- ird no #
- nz ird
- Nowa Zelandia ird
- numer ird
- Numer przychodu ze sprzedaży na lądzie


## <a name="new-zealand-ministry-of-health-number"></a>Nowa Zelandia z liczbą zdrowia

### <a name="format"></a>Formatowanie

Trzy litery i cztery cyfry

### <a name="pattern"></a>Deseń

- Trzy litery (bez wielkości liter), z wyjątkiem liter "I" i "O"
- cztery cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_new_zealand_ministry_of_health_number umożliwia znalezienie zawartości, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_nz_terms.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_new_zealand_ministry_of_health_number umożliwia znalezienie zawartości, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
    <!-- New Zealand Health Number -->
    <Entity id="2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
          <Match idRef="Keyword_nz_terms" />
      </Pattern>
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
       </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- Nowa Zelandia
- National Health Index
- NHI #
- National Health Index #


## <a name="new-zealand-physical-addresses"></a>Nowe adresy fizyczne w Nowej Zelandii

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Nowej Zelandii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="new-zealand-social-welfare-number"></a>Numer nowej Zelandii społecznościowej

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

dziewięć cyfr

### <a name="pattern"></a>Deseń

dziewięć cyfr

- trzy cyfry
- Łącznik opcjonalny
- trzy cyfry
- Łącznik opcjonalny
- trzy cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_newzealand_social_welfare_number wyszukuje zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keywords_newzealand_social_welfare_number znajduje się.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_newzealand_social_welfare_number wyszukuje zawartość, która pasuje do wzorca.

```xml
      <!-- Newzealand Social Welfare Number -->
      <Entity id="20f3c48d-4ac1-4cd2-86bd-34ecc1826e9d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
          <Match idRef="Keywords_newzealand_social_welfare_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- ubezpieczenia społecznego #
- ubezpieczenia społecznego #
- społecznościowych Nie.
- numer ubezpieczenia społecznego
- swn #


## <a name="norway-identification-number"></a>Numer identyfikacyjny Norwegia

### <a name="format"></a>Formatowanie

11 cyfr

### <a name="pattern"></a>Deseń

11 cyfr:
- Sześć cyfr w formacie DDMMYY, czyli data urodzenia
- Trzycyfrowy pojedynczy numer
- dwie cyfry sprawdzania

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_norway_id_number znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_norway_id_number znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_norway_id_numbe znajdzie zawartość, która jest taka, jak wzorzec.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Norway Identification Number -->
<Entity id="d4c8a798-e9f2-4bd3-9652-500d24080fc3" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_norway_id_number"/>
     <Match idRef="Keyword_norway_id_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_norway_id_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- Osobisty numer identyfikacyjny
- Norweski numer identyfikacyjny
- Numer identyfikacyjny
- Identyfikacja
- Liczba_osobowa
- Fødselsnummer


## <a name="norway-physical-addresses"></a>Adresy fizyczne w Norwegiach

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Norwegia. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="philippines-unified-multi-purpose-identification-number"></a>Filipiny, ujednolicony wielozadaniowy numer identyfikacyjny

### <a name="format"></a>Formatowanie

12 cyfr rozdzielonych łącznikami

### <a name="pattern"></a>Deseń

12 cyfr:
- cztery cyfry
- Łącznik
- Siedem cyfr
- Łącznik
- jedna cyfra

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_philippines_unified_id umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_philippines_id.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Ujednolicony identyfikator wielozadaniowy
- UMID
- Identity Card
- Pinag-isang Multi-Layunin ID


## <a name="poland-drivers-license-number"></a>Polski numer prawa jazdy

### <a name="format"></a>Formatowanie

14 cyfr zawierające dwa ukośniki

### <a name="pattern"></a>Deseń

14 cyfr i dwa ukośniki:

- pięć cyfr
- ukośnik
- dwie cyfry
- ukośnik
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_poland_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_poland_eu_driver's_license_number` znajduje się.

```xml
      <!-- Poland Driver's License Number -->
      <Entity id="24d51f99-ee9e-4060-a077-cae58cab1ee4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_poland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_poland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver s_license_number

- prawo jazdy
- prawa jazdy


## <a name="poland-identity-card"></a>Wizytówka w Polsce

### <a name="format"></a>Formatowanie

Trzy litery i sześć cyfr

### <a name="pattern"></a>Deseń

Trzy litery (bez wielkości liter), po których następuje sześć cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_polish_national_id znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_polish_national_id_passport_number.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa i nr dowodu tożsamości
- Dowód Tożsamości
- dow. os.


## <a name="poland-national-id-pesel"></a>Identyfikator narodowy Polski (PESEL)

### <a name="format"></a>Formatowanie

11 cyfr

### <a name="pattern"></a>Deseń

- Sześć cyfr oznaczających datę urodzenia w formacie RRMMDD
- cztery cyfry
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_pesel_identification_number znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_pesel_identification_number znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_pesel_identification_number znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
      <!-- Poland National ID (PESEL) -->
      <Entity id="E3AAF206-4297-412F-9E06-BA8487E22456" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_pesel_identification_number" />
          <Match idRef="Keyword_pesel_identification_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_pesel_identification_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osobisty
- dowódosobisty
- niepowtarzalny numer
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- numer identyfikacyjny
- pesel
- tożsamości aby je zamknąć


## <a name="poland-passport-number"></a>Numer paszportu Polski

Ten typ informacji poufnych jest uwzględniony w typie informacji poufnych numer paszportu UE. Jest także dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formatowanie

Dwie litery i siedem cyfr

### <a name="pattern"></a>Deseń

Dwie litery (bez wielkości liter), po których następuje siedem cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_polish_passport_number_v2` zawartość, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.
- Słowo kluczowe z `Keywords_eu_passport_number` lub `Keyword_polish_national_passport_number` znajduje się.
- Zostanie znalezione słowo `Keywords_eu_passport_date` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_polish_passport_number_v2` zawartość, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.
- Słowo kluczowe z `Keywords_eu_passport_number` lub `Keyword_polish_national_passport_number` znajduje się.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_polish_passport_number_v2` zawartość, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.

```xml
      <!-- Poland Passport Number -->
      <Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_passport_number_v2" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- numer paszportu
- numery paszportów
- numery paszportowe
- nr paszportu
- nr. paszportu
- nr paszportów
- n° passeport
- passeport n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="poland-physical-addresses"></a>Adresy fizyczne w Polsce

Ta nieoznakowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Polski. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="poland-regon-number"></a>Polski numer REGON

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Numer 9- lub 14-cyfrowy

### <a name="pattern"></a>Deseń

liczba dziewięciocyfrowa lub 14-cyfrowa:

- dziewięć cyfr lub
- dziewięć cyfr
- łącznik
- pięć cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_polish_regon_number znajdzie zawartość, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keywords_polish_regon_number.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_polish_regon_number znajdzie zawartość, która jest taka, jak wzorzec.

```xml
      <!-- Polish REGON Number  -->
      <Entity id="fc87b421-f437-4f8b-b739-29a735ead0d9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_regon_number" />
          <Match idRef="Keywords_polish_regon_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_regon_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- identyfikator regon
- numer statystyczny
- identyfikator statystyczny
- brak statystyczny
- numer regon
- regonid #
- regonno #
- identyfikator firmy
- companyid #
- companyidno #
- numer statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #


## <a name="poland-tax-identification-number"></a>Numer identyfikacji podatkowej w Polsce

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

11 cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_poland_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_poland_eu_tax_file_number` kluczowe od.


```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- nip #
- nip
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- identyfikator VAT #
- identyfikator VAT
- bez podatku VAT
- numer VAT
- vatid #
- vatid
- vatno #


## <a name="portugal-citizen-card-number"></a>Numer karty portugalskiej

### <a name="format"></a>Formatowanie

osiem cyfr

### <a name="pattern"></a>Deseń

osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_portugal_citizen_card umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Słowo kluczowe z Keyword_portugal_citizen_card znajduje się.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilbilie de identidade
- cartão de cidadão
- karta card
- numer dokumentu
- documento de identificação
- numer identyfikacyjny
- brak identyfikacji
- numer identyfikacyjny
- brak karty tożsamości
- numer karty tożsamości
- national id card
- nic
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- Numer bi Portugalia


## <a name="portugal-drivers-license-number"></a>Numer prawa jazdy w Portugalia

### <a name="format"></a>Formatowanie

Dwa desenie — dwie litery, po których następuje 5-8 cyfr ze znakami specjalnymi

### <a name="pattern"></a>Deseń

Wzorzec 1. Dwie litery, po których następuje cyfra 5/6 ze znakami specjalnymi:
- Dwie litery (bez wielkości liter)
- Łącznik
- Pięć lub sześć cyfr
- Spacja
- Jedna cyfra

Wzorzec 2: Jedna litera i 6/8 cyfr ze znakami specjalnymi:
- Jedna litera (bez wielkości liter)
- Łącznik
- Sześć lub osiem cyfr
- Spacja
- Jedna cyfra


### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_portugal_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_portugal_eu_driver's_license_number` znajduje się.

```xml
      <!-- Portugal Driver's License Number -->
      <Entity id="977f1e5a-2c33-4bcc-b516-95bb275cff23" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_portugal_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver s_license_number

- carteira de sportista
- carteira sportista
- carteira de habilitação
- carteira habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugal
- carta de condução


## <a name="portugal-passport-number"></a>Numer paszportu Portugalia

### <a name="format"></a>Formatowanie

Jedna litera, po której następuje sześć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

jedna litera i sześć cyfr:

- jedna litera (bez wielkości liter)
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_portugal_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_portugal_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_portugal_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_portugal_eu_passport_number` znajduje się.

```xml
      <!-- Portugal Passport Number -->
      <Entity id="080a52fd-a7bc-431e-b54d-51f08f59db11" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do passaporte
- paszport portugalski
- Portugalski passeport
- Portugalski passaporte
- passaporte nº
- passeport nº
- números de passaporte
- paszporty portugalskie
- número passaporte
- números passaporte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="portugal-physical-addresses"></a>Fizyczne adresy w Portugalia

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Portugalia. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="portugal-tax-identification-number"></a>Numer identyfikacji podatkowej Portugalia

### <a name="format"></a>Formatowanie

Dziewięć cyfr ze spacjami opcjonalnymi

### <a name="pattern"></a>Deseń

- trzy cyfry
- spacja opcjonalna
- trzy cyfry
- spacja opcjonalna
- trzy cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_portugal_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_portugal_eu_tax_file_number` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_portugal_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Portugal Tax Identification Number -->
      <Entity id="65372402-3131-4f1e-9983-4439841d1f15" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
          <Match idRef="Keywords_portugal_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- cpf #
- cpf
- nif #
- nif
- número de identificação fisca
- numero obrachunkowe
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="romania-drivers-license-number"></a>Numer prawa jazdy Rumunii

### <a name="format"></a>Formatowanie

jeden znak i osiem cyfr

### <a name="pattern"></a>Deseń

jeden znak i osiem cyfr:
- jedna litera (bez wielkości liter) lub cyfra
- osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_romania_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_romania_eu_driver's_license_number` znajduje się.

```xml
      <!-- Romania Driver's License Number -->
      <Entity id="b5511ace-2fd8-4ae4-b6fc-c7c6e4689e3c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_romania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver s_license_number

- permis de conducere
- permisului de conducere
- permisului conducere
- permisele de conducere
- conducere permisele
- permis conducere


## <a name="romania-passport-number"></a>Numer paszportu Rumunii

### <a name="format"></a>Formatowanie

osiem lub dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

osiem lub dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_romania_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_romania_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_romania_eu_passport_date` datę w formacie DD MMM/MMM YY (przykład: 01 LUT/10) lub słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_romania_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_romania_eu_passport_number` znajduje się.

```xml
      <!-- Romania Passport Number -->
      <Entity id="5d31b90c-7fe2-4a76-a14b-767b8fd19d6c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_romania_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

num dorul pa gdyaportului numarul9ului numerele pa zaimportujului Paáaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="romania-personal-numeric-code-cnp"></a>Rumunia : osobisty kod numeryczny (CNP)

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

13 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

- Jedna cyfra od 1 do 9
- Sześć cyfr oznaczających datę urodzenia (RRMMDD)
- dwucyfrowa (może to być liczba 01-52 lub 99).
- cztery cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_romania_eu_national_id_card` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_romania_eu_national_id_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_romania_eu_national_id_card` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Romania Personal Numerical Code (CNP) -->
      <Entity id="eb5fa399-fe28-4c67-8188-d63a616ed89c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
          <Match idRef="Keywords_romania_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- cnp #
- cnp
- cod identificare personal
- Cod numeric personal
- cod unic identificare
- codnumericpersonal #
- Codul fiscal nr.
- identificarea fiscal nr #
- id-ul taxei
- numer ubezpieczenia
- numer_ubezpieczenia #
- identyfikator narodowy #
- identyfikator narodowy
- numer identyfikacyjny kraju
- num dor identificare personal
- tożsamości typu liczba_numr
- numör personal unic
- num wiad.identyfikator #
- num wiad.identyfikator
- num dorpersonalunic #
- num dorpersonalunic
- numlnaru de identificare fiscalö
- num dorul de identificare fiscalö
- osobisty kod numeryczny
- przypinanie #
- przypinanie
- Nie pliku podatkowego
- numer pliku podatkowego
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #
- uniqueidentityno


## <a name="romania-physical-addresses"></a>Adresy fizyczne w Rumunii

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym Rumunii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="russia-passport-number-domestic"></a>Numer paszportu Rosji na krajowe

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

10-cyfrowy numer

### <a name="pattern"></a>Deseń

Numer 10-cyfrowy:

- dwie cyfry
- Opcjonalna spacja lub łącznik
- dwie cyfry
- spacja opcjonalna
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Ta Regex_Russian_Passport_Number_Domestic wyszukuje zawartość, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_Russian_Passport_Number.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- numer paszportu
- paszport
- paszport #
- identyfikator paszportu
- paszport #
- numer paszportu #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="russia-passport-number-international"></a>Numer paszportu Rosji za międzynarodowy

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Numer dziewięciocyfrowy

### <a name="pattern"></a>Deseń

Liczba dziewięciocyfrowa:

- dwie cyfry
- Opcjonalna spacja lub łącznik
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regex Regex_Russian_Passport_Number_International umożliwia znalezienie zawartości, która jest taka, jaka jest tego wzorca.
- Zostanie znalezione słowo kluczowe Keyword_Russian_Passport_Number.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- numer paszportu
- paszport
- paszport #
- identyfikator paszportu
- paszport #
- numer paszportu #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="saudi-arabia-national-id"></a>Arabia Saudyjska

### <a name="format"></a>Formatowanie

10 cyfr

### <a name="pattern"></a>Deseń

10 kolejnych cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_saudi_arabia_national_id umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_saudi_arabia_national_id.

```xml
<!-- Saudi Arabia National ID -->
<Entity id="8c5a0ba8-404a-41a3-8871-746aa21ee6c0" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_saudi_arabia_national_id" />
        <Any minMatches="1">
          <Match idRef="Keyword_saudi_arabia_national_id" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- Karta identyfikacyj
- Numer karty
- Numer identyfikacyjny
- الوطنية الهوية بطاقة رقم


## <a name="singapore-national-registration-identity-card-nric-number"></a>Numer dowodu tożsamości państwowej w Singapurze (NRIC)

### <a name="format"></a>Formatowanie

Dziewięć liter i cyfr

### <a name="pattern"></a>Deseń

- dziewięć liter i cyfr:
- litera "F", "G", "S" lub "T" (bez wielkości liter)
- Siedem cyfr
- Cyfra wyboru w porządku alfabetycznym

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_singapore_nric umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z Keyword_singapore_nric znajduje się.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_singapore_nric umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Singapore National Registration Identity Card (NRIC) Number -->
<Entity id="cead390a-dd83-4856-9751-fb6dc98c34da" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_singapore_nric"/>
     <Match idRef="Keyword_singapore_nric"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_singapore_nric"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- National Registration Identity Card
- Numer karty tożsamości
- NRIC
- IC
- Obcy numer identyfikacyjny
- FIN
- 身份证
- 身份證


## <a name="slovakia-drivers-license-number"></a>Numer prawa jazdy na Słowacja

### <a name="format"></a>Formatowanie

jeden znak, po którym następuje siedem cyfr

### <a name="pattern"></a>Deseń

jeden znak, po którym następuje siedem cyfr

- jedna litera (bez wielkości liter) lub cyfra
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_slovakia_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_slovakia_eu_driver's_license_number` znajduje się.

```xml
      <!-- Slovakia Driver's License Number -->
      <Entity id="14240c22-b6de-4ce5-a90b-137f74252513" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovakia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver nie s_license_number

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičskčch preukazov


## <a name="slovakia-passport-number"></a>Numer paszportu Słowacja

### <a name="format"></a>Formatowanie

jedna cyfra lub litera, po której następuje siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

jedna cyfra lub litera (bez wielkości liter), po której następuje siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_slovakia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_slovakia_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_slovakia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_slovakia_eu_passport_number` znajduje się.

```xml
      <!-- Slovakia Passport Number -->
      <Entity id="238e1f08-d80e-4793-af33-9b57918335b7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- číslo pasu
- čísla pasov
- pas č.
- Passeport n°
- n° Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="slovakia-personal-number"></a>Numer osobisty Słowacja

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Dziewięć lub 10 cyfr zawierające opcjonalny ukośnik odwrotny

### <a name="pattern"></a>Deseń

- Sześć cyfr oznaczających datę urodzenia
- opcjonalny ukośnik (/)
- trzy cyfry
- jedna opcjonalna cyfra wyboru

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_slovakia_eu_national_id_card` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_slovakia_eu_national_id_card` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_slovakia_eu_national_id_card` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Slovakia Personal Number -->
      <Entity id="951c26b7-3b35-4f73-924b-15dd599cb9ab" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
          <Match idRef="Keywords_slovakia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- numer urodzenia
- číslo národnej identifikačnej karty
- číslo občianského preukazu
- daňové číslo
- numer identyfikacyjny
- brak identyfikacji
- numer identyfikacyjny
- identifikačná karta č
- identifikačné číslo
- brak karty tożsamości
- numer karty tożsamości
- národná identifikačná značka č
- numer krajowy
- numer_narodowy #
- nemzeti személyazonosító igazolvány
- numer_osobisty #
- rč
- rodne cislo
- rodné číslo
- numer PEZEt
- ssn #
- ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- Nie pliku podatkowego
- numer pliku podatkowego
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="slovakia-physical-addresses"></a>Adresy fizyczne na Słowacja

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym ze Słowacja. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="slovenia-drivers-license-number"></a>Numer prawa jazdy w Słowenii

### <a name="format"></a>Formatowanie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_slovenia_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_slovenia_eu_driver's_license_number` znajduje się.

```xml
      <!-- Slovenia Driver's License Number -->
      <Entity id="d5bc089a-f2ee-433d-a6b1-5c253051d6f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovenia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl

#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver nie s_license_number

- vozniško dovoljenje
- vozniška številka licence
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj


## <a name="slovenia-passport-number"></a>Numer paszportu Słowenii

### <a name="format"></a>Formatowanie

Dwie litery, po których następuje siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

dwie litery, po których następuje siedem cyfr:

- litera "P"
- Jedna wielkie litery
- Siedem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_slovenia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_slovenia_eu_passport_number` znajduje się.
- Wyrażenie regularne znajduje `Regex_eu_passport_date1` datę w formacie DD.MM.YYYY lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_slovenia_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_slovenia_eu_passport_number` znajduje się.

```xml
      <!-- Slovenia Passport Number -->
      <Entity id="235b7976-7bbe-4df5-bb40-08678e749d1a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- lista potni #
- datum rojstva
- lista potni
- številke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="slovenia-physical-addresses"></a>Adresy fizyczne w Słowenii

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym użytkownika ze Słowenii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="slovenia-tax-identification-number"></a>Numer identyfikacji podatkowej w Słowenii

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

- Jedna cyfra od 1 do 9
- Sześć cyfr
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_slovenia_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_slovenia_eu_tax_file_number` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_slovenia_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Slovenia Tax Identification Number -->
      <Entity id="e47b071e-c352-4d70-8241-8c215ad65505" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
          <Match idRef="Keywords_slovenia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- davčna številka
- identifikacijska številka davka
- številka davčne datoteke
- Nie pliku podatkowego
- numer pliku podatkowego
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="slovenia-unique-master-citizen-number"></a>Unikatowy numer dla masterów w słowenii

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

13 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

13 cyfr w określonym wzorcu:

- Siedem cyfr odpowiadających dacie urodzenia (DDMMLLL), gdzie "LLL" odpowiada ostatnim trzem cyfrom roku urodzenia
- dwie cyfry odpowiadające obszarowi urodzenia "50"
- Trzy cyfry odpowiadające kombinacji płci i liczby kolejnej dla osób urodzionych w tym samym dniu. 000-499 dla mężczyzn i 500-999 dla kobiet.
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_slovenia_eu_national_id_card` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_slovenia_eu_national_id_card` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_slovenia_eu_national_id_card` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Slovenia Unique Master Citizen Number -->
      <Entity id="68948b27-803d-41e4-adf1-13e05eb541bb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
          <Match idRef="Keywords_slovenia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka ggalnega drlovavljana
- emšo
- enotna maticna številka obcana
- identyfikator
- numer identyfikacyjny
- identifikacijska številka
- karta tożsamości
- identyfikator nacionalna
- nacionalni potni list
- identyfikator narodowy
- osebna izkaznica
- osebni koda
- osebni ne
- osebni številka
- kod osobisty
- numer osobisty
- osobisty kod numeryczny
- številka drvljana
- unikatowy numer unikatowy
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- unikatowy numer wzorca
- unikatowy numer rejestracji
- uniqueidentityno #
- uniqueidentityno #


## <a name="south-africa-identification-number"></a>Numer identyfikacyjny Republika Południowej Afryki

### <a name="format"></a>Formatowanie

13 cyfr, które mogą zawierać spacje

### <a name="pattern"></a>Deseń

13 cyfr:
- Sześć cyfr w formacie RRMMDD, czyli data urodzenia
- cztery cyfry
- wskaźnik cyfr cyfry
- cyfra "8" lub "9"
- jedna cyfra, czyli cyfra sumy kontrolnej

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_south_africa_identification_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_south_africa_identification_number.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Identity card
- Identyfikator
- Identyfikacja


## <a name="south-korea-resident-registration-number"></a>Numer rejestracji rezydenta Korei Południowej

### <a name="format"></a>Formatowanie

13 cyfr zawierające łącznik

### <a name="pattern"></a>Deseń

13 cyfr:
- Sześć cyfr w formacie RRMMDD, czyli data urodzenia
- Łącznik
- Jedna cyfra określona przez wiek i płeć
- czterocyfrowy kod regionu urodzenia
- Jedna cyfra używana do odróżnienia osób, dla których poprzednie liczby są identyczne
- cyfrę wyboru.

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_south_korea_resident_number znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_south_korea_resident_number.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_south_korea_resident_number znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- National ID card
- Numer rejestracji na wye m.in.
- Jumin deungnok beonho
- WN
- 주민등록번호


## <a name="spain-dni"></a>Hiszpania DNI

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Osiem cyfr, po których następuje jeden znak

### <a name="pattern"></a>Deseń

Siedem cyfr i jeden znak

- osiem cyfr
- Opcjonalna spacja lub łącznik
- Jedna litera wyboru (bez wielkości liter)

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub  `Func_spain_eu_DL_and_NI_number_citizen` znajduje `Func_spain_eu_DL_and_NI_number_foreigner` zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo  `Keywords_spain_eu_national_id_card"` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub  `Func_spain_eu_DL_and_NI_number_citizen` znajduje `Func_spain_eu_DL_and_NI_number_foreigner` zawartość, która pasuje do wzorca.


```xml
      <!-- Spain DNI -->
      <Entity id="8e6251b9-47b4-40e8-a42b-0f80876be192" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- dni #
- dni
- dninúmero #
- documento nacional de identidad
- identidad único
- identidadúnico #
- numer ubezpieczenia
- numer identyfikacyjny kraju
- tożsamość państwowa
- nationalid #
- nationalidno #
- nie #
- nie
- nienúmero #
- número de identificación
- número nacional identidad
- numer identyfikacyjny
- tożsamość osobista nie
- unikatowy numer tożsamości
- uniqueid #


## <a name="spain-drivers-license-number"></a>Numer prawa jazdy Hiszpanii

### <a name="format"></a>Formatowanie

Osiem cyfr, po których następuje jeden znak

### <a name="pattern"></a>Deseń

osiem cyfr i jeden znak:

- osiem cyfr
- Jedna cyfra lub litera (bez wielkości liter)

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub  `Func_spain_eu_DL_and_NI_number_citizen` znajduje `Func_spain_eu_DL_and_NI_number_foreigner` zawartość, która pasuje do wzorca.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_spain_eu_driver's_license_number` znajduje się.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub  `Func_spain_eu_DL_and_NI_number_citizen` znajduje `Func_spain_eu_DL_and_NI_number_foreigner` zawartość, która pasuje do wzorca.

```xml
      <!-- Spain Driver's License Number -->
      <Entity id="d5a82922-b501-4f40-8868-341321146aa2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver nie s_license_number

- permiso de conducción
- permiso conducción
- licencia de conducir
- wzornik licucir
- conducir permiso
- permiso de conducir
- permisos de conducir
- conducir permisos
- carnet conducir
- carnet de conducir
- licencia de manejo
- licencia manejo


## <a name="spain-passport-number"></a>Numer paszportu Hiszpanii

### <a name="format"></a>Formatowanie

8- lub 9-znakowa kombinacja liter i cyfr bez spacji i ograniczników

### <a name="pattern"></a>Deseń

8- lub 9-znakowa kombinacja liter i cyfr:

- Dwie cyfry lub litery
- jedna cyfra lub litera (opcjonalnie)
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_spain_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_spain_eu_passport_number` znajduje się.
- Wyrażenie regularne umożliwia `Regex_spain_eu_passport_date` znalezienie daty w formacie DD-MM-YYYY lub znalezione słowo `Keywords_eu_passport_date` kluczowe od

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_spain_eu_passport_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_passport_number` lub `Keywords_spain_eu_passport_number` znajduje się.

```xml
      <!-- Spain Passport Number -->
      <Entity id="d17a57de-9fa5-4e9f-85d3-85c26d89686e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_spain_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta jeśli nie ma na to danych
- número gdyporte
- españa gdyporte
- números de gdyporte
- número de gdyporte
- números gdyporte
- gdyporte nie
- Passeport n°
- n° Passeport
- gdyporte nie.
- gdyporte n°
- paszport Hiszpanii

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="spain-physical-addresses"></a>Adresy fizyczne Hiszpanii

Ta nieoznazona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Hiszpanii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="spain-social-security-number-ssn"></a>Hiszpania: numer PEŁ(SSN)


### <a name="format"></a>Formatowanie

11–12 cyfr

### <a name="pattern"></a>Deseń

11-12 cyfr:
- dwie cyfry
- ukośnik (opcjonalny)
- Od siedmiu do ośmiu cyfr
- ukośnik (opcjonalny)
- dwie cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_spanish_social_security_number znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.
- - Zostanie znalezione słowo  `Keywords_spain_eu_ssn_or_equivalent` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_spanish_social_security_number znajdzie zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
    <!-- Spain SSN -->
    <Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85" relaxProximity="true" >
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spanish_social_security_number" />
          <Match idRef="Keywords_spain_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spanish_social_security_number" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- ssn
- ssn #
- socialsecurityno
- nr ubezpieczenia społecznego
- numer PEZEt
- número de la seguridad social


## <a name="spain-tax-identification-number"></a>Numer identyfikacji podatkowej Hiszpanii

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Siedem lub osiem cyfr i jedna lub dwie litery określonego wzorca

### <a name="pattern"></a>Deseń

Hiszpańskie osoby naturalne z państwową kartą tożsamości Hiszpanii:

- osiem cyfr
- Jedna wielkie litery (zróżnicowa wielkość liter)

Nieuzyskane spaniardy bez dowodu tożsamości państwowej Hiszpanii

- Jedna wielkie litery "L" (z wielkością liter)
- Siedem cyfr
- Jedna wielkie litery (zróżnicowa wielkość liter)

Rezydentni hiszpanie w wieku poniżej 14 lat bez dowodu tożsamości państwowej Hiszpanii:

- Jedna wielkie litery "K" (z wielkością liter)
- Siedem cyfr
- Jedna wielkie litery (zróżnicowa wielkość liter)

Obcokraje z numerem identyfikacyjnym osoby obcej

- Jedna wielkie litery: "X", "Y" lub "Z" (z wielkością liter)
- Siedem cyfr
- Jedna wielkie litery (zróżnicowa wielkość liter)

Obcokraje bez numeru identyfikacyjnego obcokrajowca

- Jedna wielkie litery, dla których jest to litera "M" (zróżnicowa wielkość liter)
- Siedem cyfr
- Jedna wielkie litery (zróżnicowa wielkość liter)

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub  `Func_spain_eu_tax_file_number` znajduje `Func_spain_eu_DL_and_NI_number_citizen` zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo  `Keywords_spain_eu_tax_file_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub  `Func_spain_eu_tax_file_number` znajduje `Func_spain_eu_DL_and_NI_number_citizen` zawartość, która pasuje do wzorca.

```xml
      <!-- Spain Tax Identification Number -->
      <Entity id="10f0d113-b0e1-47dc-872a-a4f45b9376a3" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- cif
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- hiszpańskicifid #
- hiszpańskicifid
- hiszpańskicifno #
- hiszpańskicifno
- Nie pliku podatkowego
- numer pliku podatkowego
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="sql-server-connection-string"></a>SQL Server parametrów połączenia

### <a name="format"></a>Formatowanie

Ciąg "Identyfikator użytkownika", "Identyfikator użytkownika", "uid" lub "UserId" oraz znaki i ciągi opisane poniżej.

### <a name="pattern"></a>Deseń

- ciąg "Identyfikator użytkownika", "Identyfikator użytkownika", "uid" lub "UserId"
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "Password" lub "pwd", gdzie "pwd" nie jest poprzedzony małą literą
- znak równości (=)
- dowolny znak, który nie jest znakiem dolara ($), symbolem procentu (%), symbolem większym niż (>), symbolem (@), cudzysłowem ("), znakiem cudzysłowu ("), średnikiem (;), lewym nawiasem klamrowym([) lub lewym nawiasem kwadratowym ({)
- dowolna kombinacja znaków od 7 do 128 znaków innych niż średnik (ukośnik, ;) ukośnik (/) lub cudzysłów (")
- Średnik (;) lub cudzysłów (")

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne CEP_Regex_SQLServerConnectionString umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Nie można odnaleźć CEP_GlobalFilter słowa kluczowego z CEP_GlobalFilter.
- Wyrażenie regularne CEP_PasswordPlaceHolder nie znajduje zawartości, która pasuje do wzorca.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości, która pasuje do wzorca.

```sql
<!---SQL Server Connection String>
<Entity id="e76b6205-d3cb-46f2-bd63-c90153f2f97d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_SQLServerConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_GlobalFilter" />
            <Match idRef="CEP_PasswordPlaceHolder" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- some-password
- hasło
- secretPassword
- próbka

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Ten poufny typ informacji identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- Hasło lub pwd, a następnie 0-2 spacje, znak równości (=), 0-2 spacje i gwiazdka (*) -LUB-
- Hasło lub pwd, po którym następuje:
    - Znak równości (=)
    - Symbol mniejszego niż (<)
    - Dowolna kombinacja od 1 do 200 znaków oznaczanych małymi i górnymi literami, cyframi, gwiazdką (*), łącznikiem (-), podkreśleniem (_) lub znakiem białym
    - Symbol większy niż (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Ten poufny typ informacji identyfikuje te słowa kluczowe za pomocą zwykłego wyrażenia, a nie listy słów kluczowych.

- contoso
- fabrikam
- northwind
- piaskownica
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="surgical-procedures"></a>Procedury procedur procedur dotyczących procedur dotyczących procedur

Ta nieopisowana nazwana jednostka wykrywa terminy związane z procedurami związanymi z procedurami dołączania, takimi *jak dołączenie*.  Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)


## <a name="sweden-drivers-license-number"></a>Szwecja numer prawa jazdy

### <a name="format"></a>Formatowanie

10 cyfr zawierające łącznik

### <a name="pattern"></a>Deseń

10 cyfr zawierających łącznik:

- Sześć cyfr
- Łącznik
- cztery cyfry

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne umożliwia  `Regex_sweden_eu_driver's_license_number` znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z  `Keywords_eu_driver's_license_number` lub `Keywords_sweden_eu_driver's_license_number` znajduje się.

```xml
      <!-- Sweden Driver's License Number -->
      <Entity id="70088720-90dd-47f5-805e-5525f3567391" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_sweden_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver nie s_license_number

- ajokortti
- permis de conducere
- ajokortin numero
- kuljettejat lic.
- lic sterownika.
- körkort
- numörul permisului de conducere
-  שאָפער דערלויבעניש נומער
- förare lic.
-  דריווערס דערלויבעניש
- körkortsnummer


## <a name="sweden-national-id"></a>Identyfikator narodowy Szwecja

### <a name="format"></a>Formatowanie

10 lub 12 cyfr i opcjonalny ogranicznik

### <a name="pattern"></a>Deseń

10 lub 12 cyfr i opcjonalny ogranicznik:
- dwie cyfry (opcjonalne)
- Sześć cyfr w formacie daty RRMMDD
- ogranicznik "-" lub "+" (opcjonalny)
- cztery cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_swedish_national_identifier` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keywords_swedish_national_identifier` kluczowe od
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_swedish_national_identifier` zawartość, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.


```xml
    <!-- Sweden National ID -->
    <Entity id="f69aaf40-79be-4fac-8f05-fd1910d272c8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_swedish_national_identifier" />
        <Match idRef="Keywords_swedish_national_identifier" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_swedish_national_identifier" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- id no
- numer identyfikacyjny
- identyfikator #
- brak identyfikacji
- numer identyfikacyjny
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- dokument tożsamości
- nie tożsamości
- numer tożsamości
- id-nummer
- identyfikator osobisty
- liczba_osob #
- liczba_osob
- skattaidentifikationsnummer


## <a name="sweden-passport-number"></a>Numer paszportu Szwecja

### <a name="format"></a>Formatowanie

osiem cyfr

### <a name="pattern"></a>Deseń

osiem kolejnych cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- wyrażenie regularne Regex_sweden_passport_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- słowo kluczowe z `Keywords_eu_passport_number` lub `Keyword_sweden_passport` znajduje się.
- wyrażenie regularne znajduje `Regex_sweden_eu_passport_date` datę w formacie DD MMM/MMM YY (01 STY/12) lub słowo kluczowe od `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- wyrażenie regularne Regex_sweden_passport_number umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- słowo kluczowe z `Keywords_eu_passport_number` lub `Keyword_sweden_passport` znajduje się.


```xml
    <!-- Sweden Passport Number -->
    <Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_sweden_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- karta rejestracji
- g3 opłaty za przetwarzanie
- wiele wpisów
- Numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passnummer
- pass nr
- visa
- visas
- jeden wpis
- przełęcz sverige
- wymagania dotyczące wizy
- przetwarzania wiz
- visa type

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data emisji
- data wygaśnięcia


## <a name="sweden-physical-addresses"></a>Szwecja ( adresy fizyczne)

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym ze Szwecja. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="sweden-tax-identification-number"></a>Szwecja numer identyfikacyjny podatku

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

10 cyfr i symbol we wskazanym wzorcu

### <a name="pattern"></a>Deseń

10 cyfr i symbol:

- Sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- znak plus lub znak minus
- Trzy cyfry, dzięki którym numer identyfikacyjny jest unikatowy w miejscu:
  - w przypadku liczb wydanych przed rokiem 1990 siódma i ósma cyfra wskazują powiat urodzenia lub osoby urodzie się zam.
  - Cyfra na pozycji dziewiątej wskazuje płeć przez płeć przez płeć nieparzystą dla mężczyzny lub nawet dla kobiety
- jedna cyfra kontrolna

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_sweden_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_sweden_eu_tax_file_number` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_sweden_eu_tax_file_number` zawartość, która odpowiada wzorcowi.

```xml
      <!-- Sweden Tax Identification Number -->
      <Entity id="139acba0-a5bc-4fbb-876d-f7a493ae8a40" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Match idRef="Keywords_sweden_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_sweden_eu_telephone_number" />
            <Match idRef="Keywords_sweden_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- identyfikator osobisty
- liczba_osob
- skatt id nummer
- skatt identifikation
- skattabetalarens identifikationsnummer
- sverige tin
- plik podatku
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer podatku
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="swift-code"></a>Kod SWIFT

### <a name="format"></a>Formatowanie

Cztery litery, po których następuje 5–31 liter lub cyfr

### <a name="pattern"></a>Deseń

Cztery litery i 5-31 liter lub cyfr:
- Czteroliterowy kod bankowy (bez wielkości liter)
- spacja opcjonalna
- 4–28 liter lub cyfr (podstawowy numer konta bankowego — BBAN)
- spacja opcjonalna
- od jednej do trzech liter lub cyfr (reszta z kodu BBAN)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_swift umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_swift.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_swift"></a>Keyword_swift

- międzynarodowa organizacja normalizacją 9362
- iso 9362
- iso9362
- swift #
- kod swift
- swiftnumber
- swiftroutingnumber
- kod swift
- numer swift #
- numer routingu swift
- bic number
- kod bic
- bic #
- bic #
- kod identyfikatora banku
- Organizacja internationale de normalisation 9362
- rapide #
- kod SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- # <a name="bic"></a>BIC
- kod identificateur de banque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT 番号
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード


## <a name="switzerland-physical-addresses"></a>Adresy fizyczne w Szwajcarii

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym w Szwajcarii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="switzerland-ssn-ahv-number"></a>Numer AHV WSN w Szwajcarii

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

13-cyfrowy numer

### <a name="pattern"></a>Deseń

Numer 13-cyfrowy:

- Trzy cyfry — 756
- opcjonalna kropka
- cztery cyfry
- opcjonalna kropka
- cztery cyfry
- opcjonalna kropka
- dwie cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_swiss_social_security_number_ahv znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keywords_swiss_social_security_number_ahv znajduje się.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_swiss_social_security_number_ahv znajdzie zawartość, która pasuje do wzorca.

```xml
      <!-- Swiss SSN AHV Number -->
      <Entity id="277cfa4b-6eaa-4a1b-9492-099dec849971" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
          <Match idRef="Keywords_swiss_social_security_number_ahv" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- ahv
- ssn
- identyfikator pid
- numer ubezpieczenia
- personalidno #
- numer PEZEt
- identyfikator osobisty
- brak identyfikacji osobistej.
- insuranceno #
- uniqueidno #
- brak unikatowej identyfikacji.
- numer avs
- tożsamość osobista bez versicherungsnummer
- identifikationsnummer
- einzigartige identität nicht
- sozialversicherungsnummer
- identyfikator identyfikacyjny personelu
- numéro de sécurité sociale


## <a name="taiwan-national-identification-number"></a>Numer identyfikacyjny narodowych na Tajwanie

### <a name="format"></a>Formatowanie

jedna litera (w języku angielskim) i dziewięć cyfr

### <a name="pattern"></a>Deseń

jedna litera (w języku angielskim) i dziewięć cyfr:
- jedna litera (w języku angielskim bez wielkości liter)
- cyfra "1" lub "2"
- osiem cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_taiwanese_national_id wyszukuje zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_taiwanese_national_id.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_taiwanese_national_id wyszukuje zawartość, która pasuje do wzorca.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- Taiwanese National ID -->
<Entity id="4C7BFC34-8DD1-421D-8FB7-6C6182C2AF03" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_taiwanese_national_id" />
          <Match idRef="Keyword_taiwanese_national_id" />
      </Pattern>
       <Pattern confidenceLevel="75">
         <IdMatch idRef="Func_taiwanese_national_id" />
       </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_taiwan_national_id"></a>Keyword_taiwan_national_id

- 身份證字號
- 身份證
- 身份證號碼
- 身份證號
- 身分證字號
- 身分證
- 身分證號碼
- 身份證號
- 身分證統一編號
- 國民身分證統一編號
- 簽名
- 蓋章
- 簽名或蓋章
- 簽章


## <a name="taiwan-passport-number"></a>Numer paszportu na Tajwanie

### <a name="format"></a>Formatowanie

- biometryczny numer paszportu: dziewięć cyfr
- nie biometryczny numer paszportu: dziewięć cyfr

### <a name="pattern"></a>Deseń
biometryczny numer paszportu:
- znak "3"
- osiem cyfr

nie biometryczny numer paszportu:
- dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_taiwan_passport umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_taiwan_passport.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- Numer paszportu ROC
- Numer paszportu
- Paszport nie
- Numer paszportu
- Paszport #
- 护照
- 中華民國護照
- Zhōnghuá Mínguó hùzhào


## <a name="taiwan-resident-certificate-arctarc-number"></a>Numer certyfikatu rezydenta na Tajwanie (ARC/TARC)

### <a name="format"></a>Formatowanie

10 liter i cyfr

### <a name="pattern"></a>Deseń

10 liter i cyfr:
- Dwie litery (bez wielkości liter)
- osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_taiwan_resident_certificate umożliwia znalezienie zawartości, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_taiwan_resident_certificate.

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- Certyfikat rezydentny
- Resident Cert
- Resident Cert.
- Karta identyfikacyj
- Ssl Resident Certificate
- ARC
- Certyfikat dla rezydentnych obszarów Tajwanu
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證


## <a name="thai-population-identification-code"></a>Kod identyfikacyjny populacji w języku tajskim

### <a name="format"></a>Formatowanie

13 cyfr

### <a name="pattern"></a>Deseń

13 cyfr:
- Pierwsza cyfra nie jest zerem ani dziewięć
- 12 cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_Thai_Citizen_Id znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_Thai_Citizen_Id znajduje się.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_Thai_Citizen_Id znajdzie zawartość, która pasuje do wzorca.

```xml
<!-- Thai Citizen ID -->
-<Entity id="44ca9e86-ead7-4c5d-884a-e2eaa401515e" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
      <Match idRef="Keyword_Thai_Citizen_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- Numer identyfikacyjny
- Numer identyfikacyjny
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkey-national-identification-number"></a>Numer identyfikacyjny narodowych w Turcja

### <a name="format"></a>Formatowanie

11 cyfr

### <a name="pattern"></a>Deseń

11 cyfr

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_Turkish_National_Id umożliwia znalezienie zawartości, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_Turkish_National_Id.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_Turkish_National_Id umożliwia znalezienie zawartości, która pasuje do wzorca.

```xml
<!-- Turkish National Identity -->
-<Entity id="fb621f20-3876-4cfc-acec-8c8e73ca32c7" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Turkish_National_Id"/>
      <Match idRef="Keyword_Turkish_National_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Turkish_National_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik numarası
- Vatandaşlık numarası
- Vatandaşlık nie


## <a name="turkey-physical-addresses"></a>Adresy fizyczne w Turcja

Ta nieoznaowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym w Turcja. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="types-of-medication"></a>Typy leki

Ta nieoznaowana nazwana jednostka wykrywa nazwy leki, takich jak *np*.  Obsługuje ona tylko terminy w języku angielskim. Jest on także zawarty w postanowieniach wszystkich [warunków medycznych dołączonych](#all-medical-terms-and-conditions) do pakietu o nazwie SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)


## <a name="uk-drivers-license-number"></a>Zjednoczone Emiraty Zjednoczone numer prawa jazdy;

### <a name="format"></a>Formatowanie

Kombinacja 18 liter i cyfr w określonym formacie

### <a name="pattern"></a>Deseń

18 liter i cyfr:
- Pięć liter (bez wielkości liter) lub cyfra "9" w miejsce litery.
- Jedna cyfra.
- Pięć cyfr w formacie daty MM JAK.J.Y dla daty urodzenia. Jeśli sterownik jest kobieta, siódmy znak jest zwiększany o 50; Na przykład od 51 do 62 zamiast od 01 do 12.
- Dwie litery (bez wielkości liter) lub cyfra "9" w miejsce litery.
- Pięć cyfr.

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_uk_drivers_license` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keywords_eu_driver's_license_number` kluczowe od.
- Pomyślnie przejdzie sprawdzanie.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_uk_drivers_license` zawartość, która odpowiada wzorcowi.
- Pomyślnie przejdzie sprawdzanie.

```xml
    <!-- U.K. Driver's License Number -->
    <Entity id="f93de4be-d94c-40df-a8be-461738047551" patternsProximity="300" recommendedConfidence="75" relaxProximity="true" >
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_uk_drivers_license" />
          <Match idRef="Keywords_eu_driver's_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_uk_drivers_license" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- kursywa sterownika
- prawo jazdy
- licencje sterownika
- licencja sterownika
- licencje sterowników
- driverslic
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- kursywa sterowników
- licencja sterowników
- licencje sterowników
- licencja sterowników
- licencje sterowników
- driver'lic
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- licencje sterownika
- lic sterownika
- kursywa sterownika
- prawo jazdy
- prawo jazdy
- prawo jazdy
- jazdy
- kursywa sterownika
- kursywa sterownika
- driver'slicense
- fragmentatory sterownika
- driver'slicence
- fragmentatory sterownika
- lica sterownika
- kursywa sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- licencje sterownika #
- licencje sterowników #
- driverslic #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- kursywa sterowników #
- licencja sterowników #
- licencje sterowników #
- licencja sterowników #
- licencje sterowników #
- driver'lic #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- licencje sterownika #
- lic sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawo jazdy #
- prawo jazdy #
- jazdy #
- kursywa sterownika #
- kursywa sterownika #
- driver'slicense #
- fragmentatory sterownika #
- driver'slicence #
- fragmentatory sterownika #
- lica sterownika #
- kursywa sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- licencja jazdy 
- licencja jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- driver licen
- drivers licen
- licen sterownika
- driving lic
- driving licen
- licencje jazdy
- licencja jazdy
- licencje jazdy
- prawo jazdy
- dl no
- dlno
- liczba dl


## <a name="uk-electoral-roll-number"></a>Zjednoczone Emiraty Zjednoczone Numer rzutowania e zygeksowania

### <a name="format"></a>Formatowanie

Dwie litery i 1–4 cyfry

### <a name="pattern"></a>Deseń

Dwie litery (bez wielkości liter), po których następuje od 1 do 4 cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_uk_electoral umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_uk_electoral.

```xml
<!-- U.K. Electoral Number -->
<Entity id="a3eea206-dc0c-4f06-9e22-aa1be3059963" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_uk_electoral" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_electoral" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- schowaj
- formularz szybki
- rejestr e zamów
- rzutnie erolne


## <a name="uk-national-health-service-number"></a>Zjednoczone Emiraty Zjednoczone numer służby zdrowia państwowego

### <a name="format"></a>Formatowanie

10–17 cyfr rozdzielonych spacjami

### <a name="pattern"></a>Deseń

10–17 cyfr:
- 3 lub 10 cyfr
- spacja
- trzy cyfry
- spacja
- cztery cyfry

### <a name="checksum"></a>Checksum

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_uk_nhs_number umożliwia znalezienie zawartości, która pasuje do wzorca.
- Prawdziwe jest jedno z następujących argumentów:
    - Słowo kluczowe z Keyword_uk_nhs_number znajduje się.
    - Zostanie znalezione słowo kluczowe Keyword_uk_nhs_number1.
    - Zostanie znalezione słowo kluczowe Keyword_uk_nhs_number_dob.
- Pomyślnie przejdzie sprawdzanie.

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- państwowa usługa opieki zdrowotnej
- nhs
- urząd usług opieki zdrowotnej
- urząd zdrowia

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- identyfikator pacjenta
- identyfikacja pacjenta
- brak pacjenta
- numer pacjenta

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.O.B
- Data urodzenia
- Data urodzenia


## <a name="uk-national-insurance-number-nino"></a>Zjednoczone Emiraty Zjednoczone numer ubezpieczenia państwowego (NINO)

Ten typ informacji poufnych jest uwzględniany w ramach typu informacji poufnych numeru identyfikacyjnego UE. Jest także dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formatowanie

Siedem znaków lub dziewięć znaków rozdzielonych spacjami lub kreskami

### <a name="pattern"></a>Deseń

Dwa możliwe wzorce:

- dwie litery (prawidłowe NINOS używają tylko niektórych znaków w tym prefiksie, co jest sprawdzane przy użyciu tego wzorca; bez wielkości liter)
- Sześć cyfr
- "A", "B", "C" lub "D" (na przykład prefiks, w sufiksie dozwolone są tylko określone znaki; bez wielkości liter)

LUB

- dwie litery
- spacja lub kreska
- dwie cyfry
- spacja lub kreska
- dwie cyfry
- spacja lub kreska
- dwie cyfry
- spacja lub kreska
- "A", "B", "C" lub "D"

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_uk_nino umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo kluczowe Keyword_uk_nino.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_uk_nino umożliwia znalezienie zawartości, która odpowiada wzorcowi.

```xml
    <!-- U.K. NINO -->
    <Entity id="16c07343-c26f-49d2-a987-3daf717e94cc" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nino" />
        <Match idRef="Keyword_uk_nino" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_nino" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- numer ubezpieczenia państwowego
- ubezpieczenia państwowego
- act ochrony
- ubezpieczenia
- numer PEZEt
- aplikacja ubezpieczeniowy
- aplikacja medyczna
- ubezpieczenia społecznego
- pomoc medyczna
- ubezpieczenia społecznego
- Wielkiej Brytanii
- Numer NI
- NR.NI
- NI #
- NI #
- ubezpieczenia #
- numer_ubezpieczenia
- nationalinsurance #
- nationalinsurancenumber


## <a name="uk-physical-addresses"></a>Zjednoczone Emiraty Zjednoczone adresy fizyczne

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Wielkiej Brytanii. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni



## <a name="uk-unique-taxpayer-reference-number"></a>Zjednoczone Emiraty Zjednoczone Unikatowy numer referencyjny podatku

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

10 cyfr bez spacji i ograniczników


### <a name="pattern"></a>Deseń

10 cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje  `Func_uk_eu_tax_file_number` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo  `Keywords_uk_eu_tax_file_number` kluczowe od.

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- numer podatku
- plik podatku
- identyfikator podatku
- Brak identyfikacji podatkowej
- numer identyfikacyjny podatku
- nie podatek #
- nie podatek
- numer rejestracji podatkowej
- 2016 #
- wydomowy #
- number #
- taksno #
- numer_podatku #
- numer_podatku
- identyfikator tin
- nie tin
- tin #


## <a name="us-bank-account-number"></a>Numer konta bankowego w Stanach Zjednoczonych

### <a name="format"></a>Formatowanie

6–17 cyfr

### <a name="pattern"></a>Deseń

Od 6 do 17 kolejnych cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_usa_bank_account_number zawartości, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_usa_Bank_Account.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- Sprawdzanie numeru konta
- Sprawdzanie konta
- Sprawdzanie konta #
- Sprawdzanie numeru ACCT
- Sprawdzanie acct #
- Sprawdzanie nie.
- Sprawdzanie, czy nie ma konta.
- Numer konta bankowego
- Konto bankowe #
- Bank Acct Number
- Bank Acct #
- Bank Acct Nie.
- Nr konta bankowego
- Numer konta oszczędnościowego
- Konto oszczędnościowe.
- Konto oszczędnościowe #
- Numer Acct oszczędności
- Savings Acct #
- Nr konta oszczędnościowego
- Numer konta oszczędnościowego
- Numer konta debetowego
- Konto debetowe
- Konto debetowe #
- Numer acct debetowego
- Acct polecenia debetowego #
- Nr konta debetowego
- Nie.


## <a name="us-drivers-license-number"></a>Numer prawa jazdy w Stanach Zjednoczonych

### <a name="format"></a>Formatowanie

W zależności od stanu

### <a name="pattern"></a>Deseń

w zależności od stanu — na przykład Warszawa:
- Dziewięć cyfr sformatowanych jak ddd ddd ddd będzie zgodne.
- Dziewięć cyfr, takich jak dddddddddd nie będzie zgodne.

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_new_york_drivers_license_number znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_[state_name]_drivers_license_name zostanie znalezione.
- Słowo kluczowe z Keyword_us_drivers_license znajduje się.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_new_york_drivers_license_number znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z Keyword_[state_name]_drivers_license_name zostanie znalezione.
- Słowo kluczowe z Keyword_us_drivers_license_abbreviations znajduje się.
- Nie można odnaleźć słowa kluczowego Keyword_us_drivers_license.

```xml
<Entity id="dfeb356f-61cd-459e-bf0f-7c6d28b458c6 patternsProximity="300">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license" />
    </Pattern>
    <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license_abbreviations" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_us_drivers_license" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- Identyfikator
- Identyfikatory
- DL #
- DLS #
- CDL #
- CDLS #
- Identyfikator #
- Identyfikatory #
- Numer identyfikacyjny
- Numery identyfikacyjne
- LIC
- LIC #

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- Lic sterownika
- Kursywa sterownika
- Prawo jazdy
- Licencje na sterownik
- DriversLic
- DriversLics
- DriversLicense
- DriversLicenses
- Sterowniki Lic
- Kursywa sterowników
- Licencja na sterowniki
- Licencje na sterowniki
- Driver'Lic
- Kursywę sterownika
- Prawo jazdy
- Prawa jazdy
- Lic sterownika
- Kursywę sterownika
- Prawo jazdy
- Prawa jazdy
- Lica sterownika
- Kursywę sterownika
- Prawo jazdy
- Prawa jazdy
- Lic sterownika
- Kursywę sterownika
- Prawo jazdy
- Prawa jazdy
- numer identyfikacyjny
- numery identyfikacyjne
- identyfikacja #
- identyfikator
- identyfikator
- dowód osobisty
- karty identyfikacyjne
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- Lic sterownika #
- Kursywa sterownika #
- Prawo jazdy #
- Licencje na sterownik #
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- Sterowniki Lic #
- Kursywa sterowników #
- Licencja na sterowniki #
- Licencje na sterowniki #
- Driver'Lic #
- Kursywę sterownika #
- Prawo jazdy #
- Prawa jazdy #
- Lic sterownika #
- Kursywę sterownika #
- Prawo jazdy #
- Prawa jazdy #
- Lica sterownika #
- Kursywę sterownika #
- Prawo jazdy #
- Prawa jazdy #
- Lic sterownika #
- Kursywę sterownika #
- Prawo jazdy #
- Prawa jazdy #
- identyfikator #
- identyfikator #
- dowód osobisty #
- karty identyfikacyjne #


#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- skrót stanu (na przykład "NY")
- nazwa województwa (na przykład "Warszawa")


## <a name="us-individual-taxpayer-identification-number-itin"></a>Amerykański numer identyfikacji podatkowej (ITIN)

### <a name="format"></a>Formatowanie

Dziewięć cyfr, które zaczynają się od cyfry "9" i zawierają cyfrę "7" lub "8" jako czwartą cyfrę (opcjonalnie sformatowaną za pomocą spacji lub kresek)

### <a name="pattern"></a>Deseń

sformatowane:
- cyfra "9"
- dwie cyfry
- spacja lub kreska
- a "7" lub "8"
- cyfra
- spacja lub kreska
- cztery cyfry

niesformatowany:
- cyfra "9"
- dwie cyfry
- a "7" lub "8"
- pięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_formatted_itin znajdzie zawartość, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_itin.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_unformatted_itin znajdzie zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo kluczowe Keyword_itin.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja może Func_formatted_itin lub Func_unformatted_itin zawartości, która jest taka, jak wzorzec.

```xml
    <!-- U.S. Individual Taxpayer Identification Number (ITIN) -->
    <Entity id="e55e2a32-f92d-4985-a35d-a0b269eb687b" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_formatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_formatted_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_unformatted_itin" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_itin"></a>Keyword_itin

- cycer
- identyfikator podatku
- identyfikacji podatkowej
- itin
- i.t.i.n.
- ssn
- tin
- ubezpieczenia społecznego
- payer podatku
- itins
- 2016
- indywidualny vat


## <a name="us-physical-addresses"></a>Adresy fizyczne w Stanach Zjednoczonych

Ta nieoznaona nazwana jednostka wykrywa wzorce związane z adresem fizycznym w Stanach Zjednoczonych. Jest także dołączany do pakietu [All Physical Addresses](#all-physical-addresses) bundled named entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni


## <a name="us-social-security-number-ssn"></a>Numer SSN (U.SSN)

### <a name="format"></a>Formatowanie

Dziewięć cyfr, które mogą być sformatowane lub niesformatowane

> [!NOTE]
> Jeśli została wystawiona przed mid-2011, SSN ma silne formatowanie, w którym niektóre części liczby muszą wchodzić w zakresy, aby były prawidłowe (ale nie ma sumy kontrolnej).

### <a name="pattern"></a>Deseń

Cztery funkcje szukają sieci SSN w czterech różnych wzorcach:
- Func_ssn umożliwia znalezienie ssnów o formatowaniu silnych danych przed 2011 r. sformatowanych za pomocą kresek lub spacji (ddd-dd-dddd OR ddd dddd)
- Func_unformatted_ssn umożliwia znalezienie ssnów z formatowaniem znaczącym przed 2011 erą, które są niesformatowane jako dziewięć kolejnych cyfr (dddddddddd)
- Func_randomized_formatted_ssn umożliwia znalezienie po 2011 r. SNS sformatowanych za pomocą kresek lub spacji (ddd-dd-dddd OR ddd dddd)
- Func_randomized_unformatted_ssn umożliwia znalezienie niesformatowanych po 2011 r. numerów SSN, które są niesformatowane jako dziewięć kolejnych cyfr (dddddddddd)

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja znajduje `Func_ssn` zawartość, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_ssn` kluczowe od.

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_unformatted_ssn' umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Zostanie znalezione słowo `Keyword_ssn` kluczowe od.

Zasady DLP mają małą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja lub `Func_randomized_formatted_ssn` znajduje `Func_randomized_unformatted_ssn` zawartość, która pasuje do wzorca.
- Zostanie znalezione słowo `Keyword_ssn` kluczowe od.


```xml
<!-- U.S. Social Security Number (SSN) -->
  <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_randomized_formatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="55">
        <IdMatch idRef="Func_randomized_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
  </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_ssn"></a>Keyword_ssn

- Numer SSA
- numer PEZEt
- ubezpieczenia społecznego #
- ubezpieczenia społecznego #
- nr ubezpieczenia społecznego
- Ubezpieczenia społecznego #
- Soc Sec
- SSN
- SSNS
- SSN #
- SZ #
- SSID


## <a name="usuk-passport-number"></a>Stany Zjednoczone numer paszportu

### <a name="format"></a>Formatowanie

dziewięć cyfr

### <a name="pattern"></a>Deseń

- jedna litera lub cyfra
- osiem cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_usa_uk_passport znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z `Keywords_eu_passport_number` lub `Keywords_uk_eu_passport_number` znajduje się.
- Zostanie znalezione słowo `Keywords_eu_passport_date` kluczowe od

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Funkcja Func_usa_uk_passport znajdzie zawartość, która pasuje do wzorca.
- Słowo kluczowe z `Keywords_eu_passport_number` lub `Keywords_uk_eu_passport_number` znajduje się.

```xml
    <!-- U.S. / U.K. Passport Number -->
    <Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
       <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- paszport #
- paszport #
- paszport
- paszporty
- paszport
- paszport
- numer paszportu
- numer paszportu
- paszport
- numery paszportów

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- paszport brytyjski
- paszport Zjednoczonego Królestwa


## <a name="ukraine-passport-domestic"></a>Paszport Ukrainy

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

dziewięć cyfr

### <a name="pattern"></a>Deseń

dziewięć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Ta Regex_Ukraine_Passport_Domestic wyszukuje zawartość, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_Ukraine_Passport_Domestic.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- Paszport Ukrainy
- numer paszportu
- paszport
- паспорт України
- номер паспорта
- персональний


## <a name="ukraine-passport-international"></a>Paszport Ukrainy

Tego typu informacji poufnych można używać tylko w:
- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie informacjami
- zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze

### <a name="format"></a>Formatowanie

Ośmio znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Deseń

Osiem znaków alfanumerycznych wzorców:
- Dwie litery lub cyfry
- Sześć cyfr

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Ta Regex_Ukraine_Passport_International wyszukuje zawartość, która jest taka, jak wzorzec.
- Zostanie znalezione słowo kluczowe Keyword_Ukraine_Passport_International.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- Paszport Ukrainy
- numer paszportu
- paszport
- паспорт України
- номер паспорта


