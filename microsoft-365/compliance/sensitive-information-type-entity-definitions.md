---
title: Definicje jednostek typu informacji poufnych
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
description: Istnieje wiele typów informacji poufnych, które są gotowe do użycia w zasadach DLP. W tym artykule wymieniono wszystkie te typy informacji poufnych i pokazano, czego szukają zasady DLP podczas wykrywania poszczególnych typów.
ms.openlocfilehash: af2cbd03de426aa34b9db82691a22684c4c1df0b
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130807"
---
# <a name="sensitive-information-type-entity-definitions"></a>Definicje jednostek typu informacji poufnych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W tym artykule wymieniono wszystkie definicje jednostek typów informacji poufnych. Każda definicja pokazuje, czego szukają zasady DLP w celu wykrycia każdego typu. Aby dowiedzieć się więcej o typach informacji poufnych, zobacz [Typy informacji poufnych](sensitive-information-type-learn-about.md)

> [!NOTE]
> Mapowanie poziomu ufności (wysoki/średni/niski) z dokładnością (wartość liczbowa od 1 do 100)
>
> - Niska pewność: 65 lub mniej
> - Średnie zaufanie: 75
> - Wysoka pewność siebie: 85

## <a name="aba-routing-number"></a>Numer routingu usługi ABA

### <a name="format"></a>Formacie

dziewięć cyfr, które mogą znajdować się w sformatowanym lub niesformatowanym wzorcu

### <a name="pattern"></a>Wzór

- dwie cyfry w zakresach 00-12, 21-32, 61-72 lub 80
- dwie cyfry
- opcjonalny łącznik
- cztery cyfry
- opcjonalny łącznik
- cyfra

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli znajduje się w pobliżu 300 znaków:

- Funkcja Func_aba_routing znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_ABA_Routing.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_aba_routing znajduje zawartość zgodną ze wzorcem.

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

- aba number
- Aba #
- Aba
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- bankrouting #
- bankroutingnumber
- Routingu #
- brak routingu
- numer routingu
- numer tranzytu routingu
- Routingu #
- RTN

## <a name="all-full-names"></a>Wszystkie pełne nazwy

Wszystkie pełne nazwy to jednostka o nazwie bundled. Wykrywa pełne nazwiska osób ze wszystkich obsługiwanych krajów/regionów, w tym Australii, Chin, Japonii, USA i krajów UE. Użyj tego interfejsu SIT, aby wykryć wszystkie możliwe dopasowania pełnych nazw.

### <a name="format"></a>Formacie

Różnych.

### <a name="pattern"></a>Wzór

Różnych.

### <a name="checksum"></a>Suma kontrolna

Nie.

### <a name="description"></a>Opis

Ta nazwana jednostka SIT jest zgodna z nazwiskami osobistymi, które człowiek będzie identyfikował jako imię z dużą pewnością. Jeśli na przykład znaleziono ciąg składający się z danej nazwy, po którym następuje nazwa rodziny, dopasowanie jest tworzone z dużą pewnością. Używa trzech zasobów podstawowych:

- Słownik o podanych nazwach.
- Słownik imion rodzinnych.
- Wzorce sposobu tworzenia nazw.

Te trzy zasoby są różne dla każdego kraju.  Ciągi *Olivia Wilson* wyzwoli mecz. Wspólne imiona i nazwiska rodzin mają większe zaufanie niż rzadsze nazwy. Jednak wzorzec umożliwia również częściowe dopasowania. Jeśli zostanie znaleziona dana nazwa ze słownika, po której następuje nazwa rodziny, której nie ma w słowniku, zostanie wyzwolone częściowe dopasowanie. Na przykład *Tomas Richard* wyzwoli częściowe dopasowanie. Częściowe dopasowania mają mniejszą pewność siebie.

Ponadto wzorce, które człowiek postrzegałby jako wskazujące nazwy, są również dopasowywane z odpowiednim zaufaniem. Podobnie jak *O. Wilson*, *O.P. Wilson*, *Dr. O. P. Wilson*, *Wilson, O.P.* lub *T. Richard, Jr będzie* mecze.

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

## <a name="all-medical-terms-and-conditions"></a>Wszystkie warunki i postanowienia medyczne

Wszystkie warunki i postanowienia medyczne to jednostka o nazwie wiązanej, która wykrywa warunki medyczne i medyczne. Wykrywa tylko angielskie terminy. Użyj tego narzędzia SIT, aby wykryć wszystkie możliwe dopasowania warunków i postanowień medycznych.

### <a name="format"></a>Formacie

Słownik

### <a name="pattern"></a>Wzór

Słownik

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="description"></a>Opis

Ta powiązana nazwana jednostka jest zgodna z tekstem, który wspomina o schorzeniach występujących w wyselekcjonowanych słownikach. Istnieje jeden wyselekcjonowany słownik na obsługiwany język. Słowniki pochodzą z wielu międzynarodowych zasobów medycznych. Słowniki zawierają jak najwięcej schorzeń, jak to możliwe bez ryzyka dużej liczby fałszywie dodatnich. Każdy wpis zawiera różne formularze, w których często zapisywany jest pojedynczy warunek, aby zapewnić pokrycie, na przykład:

- *TB*
- *Gruźlicy*
- *pulmonalis phthisis*

### <a name="contains"></a>Zawiera

Ta powiązana nazwana jednostka SIT zawiera te pojedyncze interfejsy API.

- Terminy badania krwi
- Typy leków
- Chorób
- Nazwy leków ogólnych
- Upośledzenia wymienione w us Disability Evaluation Under Social Security
- Terminy testowe laboratorium
- Styl życia, który odnosi się do schorzeń
- Specjalności medyczne
- Procedury chirurgiczne
- Markowe nazwy leków

## <a name="all-physical-addresses"></a>Wszystkie adresy fizyczne

Wszystkie adresy fizyczne to jednostka w pakiecie SIT, która wykrywa wzorce związane z adresami fizycznymi ze wszystkich obsługiwanych krajów/regionów.

### <a name="format"></a>Formacie

Różnych

### <a name="pattern"></a>Wzór

Różnych

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="description"></a>Opis

Dopasowanie adresów ulicznych zostało zaprojektowane tak, aby pasowało do ciągów identyfikowanych przez człowieka jako adres ulicy. W tym celu jest używanych kilka zasobów podstawowych:

- Słownik rozliczeń, powiatów i regionów.
- Słownik sufiksów ulicznych, takich jak Road, Street lub Avenue.
- Wzorce kodów pocztowych.
- Wzorce formatów adresów.

Zasoby są różne dla każdego kraju. Zasoby podstawowe to wzorce formatów adresów, które są używane w danym kraju. Różne formaty są wybierane w celu upewnienia się, że jest dopasowanych jak najwięcej adresów. Formaty te umożliwiają elastyczność, na przykład adres może pominąć kod pocztowy lub pominąć nazwę miasta lub mieć ulicę bez sufiksu ulicy. We wszystkich przypadkach takie dopasowania są używane w celu zwiększenia ufności dopasowania.

Wzorce zostały zaprojektowane tak, aby pasowały do pojedynczych adresów, a nie lokalizacji ogólnych. Dlatego ciągi takie jak *Redmond, WA 98052* lub *Main Street, Albuquerque* nie zostaną dopasowane.

### <a name="contains"></a>Zawiera

Ta powiązana nazwana jednostka SIT zawiera następujące pojedyncze interfejsy API:

- Adresy fizyczne w Australii
- Adresy fizyczne Austrii
- Adresy fizyczne w Belgii
- Adresy fizyczne Brazylii
- Adresy fizyczne Bułgarii
- Adresy fizyczne w Kanadzie
- Adresy fizyczne Chorwacji
- Adresy fizyczne cypryjskie
- Adresy fizyczne w Czechach
- Adresy fizyczne Danii
- Adresy fizyczne Estonii
- Adresy fizyczne Finlandii
- Adresy fizyczne We Francji
- Adresy fizyczne w Niemczech
- Adresy fizyczne Grecji
- Adresy fizyczne Na Węgrzech
- Adresy fizyczne Islandii
- Adresy fizyczne Irlandii
- Adresy fizyczne Włoch
- Adresy fizyczne Łotwy
- Adresy fizyczne Liechtensteinu
- Adresy fizyczne Litwy
- Adresy fizyczne w Luksemburgu
- Adresy fizyczne Malty
- Holenderskie adresy fizyczne
- Adresy fizyczne Nowej Zelandii
- Adresy fizyczne Norwegii
- Adresy fizyczne w Polsce
- Adresy fizyczne Portugalii
- Adresy fizyczne Rumunii
- Adresy fizyczne Słowacji
- Adresy fizyczne Słowenii
- Adresy fizyczne Hiszpanii
- Adresy fizyczne Szwecji
- Adresy fizyczne Szwajcarii
- Adresy fizyczne Turcji
- Adresy fizyczne w Wielkiej Brytanii
- adresy fizyczne Stany Zjednoczone

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

## <a name="argentina-national-identity-dni-number"></a>Numer tożsamości narodowej Argentyny (DNI)

### <a name="format"></a>Formacie

Osiem cyfr z kropkami lub bez

### <a name="pattern"></a>Wzór

Osiem cyfr:

- dwie cyfry
- opcjonalny okres
- trzy cyfry
- opcjonalny okres
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_argentina_national_id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_argentina_national_id.

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

- Numer tożsamości narodowej Argentyny
- cedula
- cédula
- dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- rnp

## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Argentyna Unikatowy klucz identyfikacji podatkowej (CUIT/CUIL)

### <a name="format"></a>Formacie

11 cyfr z kreską

### <a name="pattern"></a>Wzór

11 cyfr z kreską:

- dwie cyfry w 20, 23, 24, 27, 30, 33 lub 34
- łącznik (-)
- osiem cyfr
- łącznik (-)
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_Argentina_Unique_Tax_Key` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_Argentina_Unique_Tax_Key`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_Argentina_Unique_Tax_Key` znajduje zawartość zgodną ze wzorcem.

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
- unikatowy kod identyfikacji pracowników
- Clave Única de Identificación Tributaria
- unikatowy kod identyfikacji pracowników
- CUIL
- Unikatowy klucz identyfikacji podatkowej
- Unikatowy klucz identyfikacji siły roboczej
- Unikatowy klucz identyfikacji pracowników
- Unikatowy kod identyfikacji służbowych
- Unikatowy kod identyfikacji pracy
- Unikatowy klucz identyfikacji pracy
- Unikatowy klucz identyfikacji pracy
- Unikatowy kod identyfikacji podatkowej
- Unikatowy klucz identyfikacji podatkowej
- Unikatowy kod identyfikacji pracy
- Unikatowy kod identyfikacji pracy
- Unikatowy klucz identyfikacji siły roboczej
- Unikatowy klucz identyfikacji pracy
- identyfikator podatkowy
- taxID #
- taxId
- taxidnumber
- numer podatkowy
- numer podatkowy
- Podatku #
- Podatku #
- identyfikator podatnika
- numer podatnika
- brak podatnika
- Podatnik #
- Podatnik #
- tożsamość podatkowa
- identyfikacja podatkowa
- Número de Identificación Fiscal
- número de contribuyente

## <a name="australia-bank-account-number"></a>Numer konta bankowego w Australii

### <a name="format"></a>Formacie

od sześciu do 10 cyfr z numerem oddziału stanu banku lub bez go

### <a name="pattern"></a>Wzór

Numer konta to od 6 do 10 cyfr.

Numer oddziału bankowego w Australii:

- trzy cyfry
- łącznik
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_australia_bank_account_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_australia_bank_account_number.
- Wyrażenie regularne Regex_australia_bank_account_number_bsb znajduje zawartość zgodną ze wzorcem.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_australia_bank_account_number znajduje zawartość zgodną ze wzorcem.

- Znaleziono słowo kluczowe z Keyword_australia_bank_account_number.

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

- swift bank code
- bank korespondenta
- waluta bazowa
- konto usa
- adres posiadacza
- adres banku
- konto informacyjne
- transfery funduszy
- opłaty bankowe
- szczegóły banku
- informacje bankowe
- pełne nazwy
- Maea

## <a name="australia-business-number"></a>Numer biznesowy Australii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

11 cyfr z opcjonalnymi ogranicznikami

### <a name="pattern"></a>Wzór

11 cyfr z opcjonalnymi ogranicznikami:

- dwie cyfry
- opcjonalny łącznik lub spacja
- trzy cyfry
- opcjonalny łącznik lub spacja
- trzy cyfry
- opcjonalny łącznik lub spacja
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_australian_business_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_australian_business_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_australian_business_number znajduje zawartość zgodną ze wzorcem.

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
- numer biznesowy
- Abn #
- businessid #
- identyfikator firmy
- Abn
- businessno #

## <a name="australia-company-number"></a>Numer firmy w Australii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

dziewięć cyfr z ogranicznikami

### <a name="pattern"></a>Wzór

dziewięć cyfr z ogranicznikami:

- trzy cyfry
- spację
- trzy cyfry
- spację
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_Australian_Company_Number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Australian_Company_Number.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_Australian_Company_Number znajduje zawartość zgodną ze wzorcem.

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

- Cna
- australia company no
- australia company no #
- numer firmy w Australii
- australian company no
- australian company no #
- numer australijskiej firmy

## <a name="australia-drivers-license-number"></a>Numer prawa jazdy w Australii

### <a name="format"></a>Formacie

dziewięć liter i cyfr

### <a name="pattern"></a>Wzór

dziewięć liter i cyfr:

- dwie cyfry lub litery (bez uwzględniania wielkości liter)
- dwie cyfry
- pięć cyfr lub liter (bez uwzględniania wielkości liter)

LUB

- od jednej do dwóch opcjonalnych liter (bez uwzględniania wielkości liter)
- od czterech do dziewięciu cyfr

LUB

- dziewięć cyfr lub liter (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_australia_drivers_license_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_australia_drivers_license_number.
- Nie znaleziono słowa kluczowego z Keyword_australia_drivers_license_number_exclusions.

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

- międzynarodowe zezwolenia na jazdę
- australijskie stowarzyszenie motoryzacyjne
- międzynarodowe prawo jazdy
- DriverLicence
- DriverLicences
- Sterownik Lic
- Prawo jazdy
- Prawa jazdy
- Sterowniki
- SterownikiLicence
- DriversLicences
- Sterowniki Lic
- Sterowniki Lics
- Prawo jazdy
- Prawa jazdy
- Driver'Lic
- Driver'Lics
- Prawo jazdy
- Prawa jazdy
- Lic sterownika
- Lics kierowcy
- Prawo jazdy
- Prawa jazdy
- Driver'sLic
- Kursywę sterownika
- Driver'sLicence
- Kursywą kierowcy
- Lic kierowcy
- Lics kierowcy
- Prawo jazdy
- Prawa jazdy
- DriverLic #
- DriverLics #
- DriverLicence #
- DriverLicences #
- Sterownik Lic #
- Sterownik Lics #
- Prawo jazdy #
- Prawa jazdy #
- Sterowniki #
- SterownikiLics #
- SterownikiLicence #
- DriversLicences #
- Sterowniki Lic #
- Sterowniki Lics #
- Prawo jazdy #
- Prawa jazdy #
- Driver'Lic #
- Driver'Lics #
- Prawo jazdy #
- Prawa jazdy #
- Lic sterownika #
- Lics kierowcy #
- Prawo jazdy #
- Prawa jazdy #
- Driver'sLic #
- Kursywę sterownika #
- Driver'sLicence #
- Kursywą kierowcy #
- Lic kierowcy #
- Lics kierowcy #
- Prawo jazdy #
- Prawa jazdy #

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- Aaa
- DriverLicense
- DriverLicenses
- Prawo jazdy
- Prawa jazdy
- DriversLicense
- DriversLicenses
- Licencja kierowcy
- Licencje kierowców
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Prawa jazdy
- Driver'sLicense
- Driver'sLicenses
- Prawo jazdy
- Prawa jazdy
- DriverLicense #
- DriverLicenses #
- Prawo jazdy #
- Prawa jazdy #
- DriversLicense #
- DriversLicenses #
- Licencja kierowcy #
- Licencje kierowców #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Prawa jazdy #
- Driver'sLicense #
- Driver'sLicenses #
- Prawo jazdy #
- Prawa jazdy #

## <a name="australia-medical-account-number"></a>Numer konta medycznego w Australii

### <a name="format"></a>Formacie

10–11 cyfr

### <a name="pattern"></a>Wzór

10–11 cyfr:

- Pierwsza cyfra znajduje się w zakresie od 2 do 6
- Dziewiąta cyfra to cyfra kontrolna
- Dziesiąta cyfra to cyfra problemu
- 11 cyfra (opcjonalnie) to indywidualna liczba

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_australian_medical_account_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Australia_Medical_Account_Number.
- Suma kontrolna przechodzi.

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
- płatności medicare
- konto kredytu hipotecznego
- płatności bankowe
- gałąź informacyjna
- pożyczka na kartę kredytową
- dział usług ludzkich
- usługa lokalna
- Medicare

## <a name="australia-passport-number"></a>Numer paszportu Australii

### <a name="format"></a>Formacie

osiem lub dziewięć znaków alfanumerycznych

### <a name="pattern"></a>Wzór

- jedną literę (N, E, D, F, A, C, U, X), po której następuje siedem cyfr lub
- Dwie litery (PA, PB, PC, PD, PE, PF, PU, PW, PX, PZ), a następnie siedem cyfr.

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_australia_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_australia_passport_number`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie `Regex_australia_passport_number` regularne znajduje zawartość zgodną ze wzorcem.

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów
- szczegóły paszportu
- imigracja i obywatelstwo
- wspólnota australii
- departament imigracji
- krajowego dowodu osobistego
- dokument podróży
- organ wystawiający

## <a name="australia-physical-addresses"></a>Adresy fizyczne w Australii

Odbuntowana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Australii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności
Średni

## <a name="australia-tax-file-number"></a>Numer pliku podatkowego Australii

### <a name="format"></a>Formacie

od ośmiu do dziewięciu cyfr

### <a name="pattern"></a>Wzór

od ośmiu do dziewięciu cyfr zwykle przedstawianych ze spacjami w następujący sposób:

- trzy cyfry
- opcjonalne miejsce
- trzy cyfry
- opcjonalne miejsce
- od dwóch do trzech cyfr, gdzie ostatnia cyfra jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_australian_tax_file_number znajduje zawartość zgodną ze wzorcem.
- Nie znaleziono słowa kluczowego z Keyword_Australia_Tax_File_Number lub Keyword_number_exclusions.
- Suma kontrolna przechodzi.

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

- australijski numer biznesowy
- marginalna stawka podatkowa
- opłata medicare
- numer portfela
- weterani usług
- Podatku
- indywidualne zeznanie podatkowe
- numer pliku podatkowego
- Tfn

## <a name="austria-drivers-license-number"></a>Numer prawa jazdy w Austrii

### <a name="format"></a>Formacie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_austria_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_austria_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver s_license_number

- fuhrerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern

## <a name="austria-identity-card"></a>Austria identity card (Austria)

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

24-znakowa kombinacja liter, cyfr i znaków specjalnych

### <a name="pattern"></a>Wzór

24 znaki:

- 22 litery (bez uwzględniania wielkości liter), cyfry, ukośniki odwrotne, ukośniki do przodu lub znaki plus

- dwie litery (bez uwzględniania wielkości liter), cyfry, ukośniki odwrotne, ukośniki do przodu, znaki plus znaki lub znaki równości

### <a name="checksum"></a>Suma kontrolna

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_austria_eu_national_id_card` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_austria_eu_national_id_card`

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
- identyfikator krajowy
- personalausweis republik österreich

## <a name="austria-passport-number"></a>Numer paszportu Austrii

### <a name="format"></a>Formacie

Jedna litera, po której następuje opcjonalne spacja i siedem cyfr

### <a name="pattern"></a>Wzór

Kombinacja jednej litery, siedmiu cyfr i jednego spacji:

- jedna litera (bez uwzględniania wielkości liter)
- jedno miejsce (opcjonalnie)
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_austria_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_austria_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_austria_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_austria_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_austria_eu_passport_number"></a>Keywords_austria_eu_passport_number

- reisepassnummer
- reisepasse
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Numer dostępu
- reisepässe

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="austria-physical-addresses"></a>Adresy fizyczne Austrii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Austrii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="austria-social-security-number"></a>Numer ubezpieczenia społecznego w Austrii

### <a name="format"></a>Formacie

10 cyfr w określonym formacie

### <a name="pattern"></a>Wzór

10 cyfr:

- trzy cyfry odpowiadające numerowi seryjnemu
- jedna cyfra kontrolna
- sześć cyfr odpowiadających dacie urodzenia (DDMMYY)

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_austria_eu_ssn_or_equivalent` znajduje zawartość zgodną ze wzorcem.
- odnaleziono słowo kluczowe z `Keywords_austria_eu_ssn_or_equivalent` .

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_austria_eu_ssn_or_equivalent` znajduje zawartość zgodną ze wzorcem.

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

- austrian ssn
- Numer ehic
- Brak ehic
- kod ubezpieczenia
- kod ubezpieczenia #
- numer ubezpieczenia
- brak ubezpieczenia
- krankenkassennummer
- krankenversicherung
- socialsecurityno
- socialsecurityno #
- zabezpieczenia społecznego nie
- numer ubezpieczenia społecznego
- kod zabezpieczenia społecznego
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- Ssn #
- Ssn
- versicherungscode
- versicherungsnummer
- zdravstveno zavarovanje

## <a name="austria-tax-identification-number"></a>Numer identyfikacji podatkowej Austrii

### <a name="format"></a>Formacie

dziewięć cyfr z opcjonalnym łącznikiem i ukośnikiem do przodu

### <a name="pattern"></a>Wzór

dziewięć cyfr z opcjonalnym łącznikiem i ukośnikiem do przodu:

- dwie cyfry
- łącznik (opcjonalnie)
- trzy cyfry
- ukośnik (opcjonalnie)
- cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_austria_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_austria_eu_tax_file_number`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_austria_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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

- Österreich
- st.nr.
- steuernummer
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- numer podatkowy

## <a name="austria-value-added-tax"></a>Podatek od wartości dodanej w Austrii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

11-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

11-znakowy wzorzec alfanumeryczny:

- A lub a
- T lub t
- Opcjonalne miejsce
- U lub u
- opcjonalne miejsce
- dwie lub trzy cyfry
- opcjonalne miejsce
- cztery cyfry
- opcjonalne miejsce
- jedna lub dwie cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_Austria_Value_Added_Tax znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Austria_Value_Added_Tax.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_Austria_Value_Added_Tax znajduje zawartość zgodną ze wzorcem.

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
- Podatku vat #
- austriacki numer VAT
- vat no.
- vatno #
- numer podatku od wartości dodanej
- vat austriacki
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- numer identyfikacyjny vat
- numer atu
- numer uid

## <a name="azure-documentdb-auth-key"></a>Klucz uwierzytelniania usługi Azure DocumentDB

### <a name="format"></a>Formacie

Ciąg "DocumentDb", po którym następują znaki i ciągi opisane we wzorcu poniżej.

### <a name="pattern"></a>Wzór

- Ciąg "DocumentDb"
- Dowolna kombinacja od 3 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- Symbol większy niż (>), znak równości (=), cudzysłów () lub apostrof (")
- Dowolna kombinacja 86 małych lub wielkich liter, cyfr, ukośnika (/) lub znaku plus (+)
- Dwa znaki równości (=)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzureDocumentDBAuthKey znajduje zawartość zgodną ze wzorcem.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości zgodnej ze wzorcem.

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

(Technicznie ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych).

- Contoso
- Fabrikam
- Northwind
- Piaskownicy
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Netto

## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Parametry połączenia bazy danych IAAS platformy Azure i parametry połączenia usługi Azure SQL

### <a name="format"></a>Formacie

Ciąg "Serwer", "serwer" lub "źródło danych", po którym następuje znaki i ciągi opisane we wzorcu poniżej, w tym ciąg "cloudapp.azure.<!--no-hyperlink-->com" lub "cloudapp.azure.<!--no-hyperlink-->net" lub "database.windows.<!--no-hyperlink-->net", a ciąg "Password" lub "password" lub "pwd".

### <a name="pattern"></a>Wzór

- ciąg "Serwer", "serwer" lub "źródło danych"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- Ciąg "cloudapp.azure.<!--no-hyperlink-->com", "cloudapp.azure.<!--no-hyperlink-->net" lub "database.windows.<!--no-hyperlink-->net"
- dowolna kombinacja od 1 do 300 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "Password", "password" lub "pwd"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- co najmniej jeden znak, który nie jest średnikiem (;), cudzysłów () lub apostrof (")
- średnik (;), cudzysłów () lub apostrof (")

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzureConnectionString znajduje zawartość zgodną ze wzorcem.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości zgodnej ze wzorcem.

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

(Technicznie ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych).

- Contoso
- Fabrikam
- Northwind
- Piaskownicy
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Netto

## <a name="azure-iot-connection-string"></a>Parametry połączenia usługi Azure IoT

### <a name="format"></a>Formacie

Ciąg "Nazwa hosta", po którym następuje znaki i ciągi opisane we wzorcu poniżej, w tym ciągi "azure-devices.<!--no-hyperlink-->net" i "SharedAccessKey".

### <a name="pattern"></a>Wzór

- ciąg "Nazwa hosta"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "azure-devices.<!--no-hyperlink-->net"
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "SharedAccessKey"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja 43 małych lub wielkich liter, cyfr, ukośnika (/) lub znaku plus (+)
- znak równości (=)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzureIoTConnectionString znajduje zawartość zgodną ze wzorcem.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości zgodnej ze wzorcem.

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

Ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych.

- Contoso
- Fabrikam
- Northwind
- Piaskownicy
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Netto

## <a name="azure-publish-setting-password"></a>Hasło ustawienia publikowania platformy Azure

### <a name="format"></a>Formacie

Ciąg "userpwd=", po którym następuje ciąg alfanumeryczny.

### <a name="pattern"></a>Wzór

- ciąg "userpwd="
- dowolna kombinacja 60 małych liter lub cyfr
- znak cudzysłów (")

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzurePublishSettingPasswords znajduje zawartość zgodną ze wzorcem.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości zgodnej ze wzorcem.

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

Ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych.

- Contoso
- Fabrikam
- Northwind
- Piaskownicy
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Netto

## <a name="azure-redis-cache-connection-string"></a>Parametry połączenia usługi Azure Redis Cache

### <a name="format"></a>Formacie

Ciąg "redis.cache.windows.<!--no-hyperlink-->net", a następnie znaki i ciągi opisane we wzorcu poniżej, w tym ciąg "password" lub "pwd".

### <a name="pattern"></a>Wzór

- ciąg "redis.cache.windows.<!--no-hyperlink-->net"
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "password" lub "pwd"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja 43 znaków, które są małymi lub wielkimi literami, cyframi, ukośnikiem (/) lub znakiem plus (+)
- znak równości (=)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzureRedisCacheConnectionString znajduje zawartość zgodną ze wzorcem.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości zgodnej ze wzorcem.

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

(Technicznie ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych).

- Contoso
- Fabrikam
- Northwind
- Piaskownicy
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Netto

## <a name="azure-sas"></a>Sygnatura dostępu współdzie

### <a name="format"></a>Formacie

Ciąg "sig", po którym następuje znaki i ciągi opisane we wzorcu poniżej.

### <a name="pattern"></a>Wzór

- ciąg "sig"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja od 43 do 53 znaków, które są małymi lub wielkimi literami, cyframi lub znakiem procentu (%)
- ciąg "%3d"
- dowolny znak, który nie jest znakiem małej lub wielkiej litery, cyfry lub procentu (%)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzureSAS znajduje zawartość zgodną ze wzorcem.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Parametry połączenia usługi Azure Service Bus

### <a name="format"></a>Formacie

Ciąg "EndPoint", po którym następuje znaki i ciągi opisane we wzorcu poniżej, w tym ciągi "servicebus.windows.<!--no-hyperlink-->net" i "SharedAccesKey".

### <a name="pattern"></a>Wzór

- ciąg "EndPoint"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "servicebus.windows.<!--no-hyperlink-->net"
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "SharedAccessKey"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja 43 znaków, które są małymi lub wielkimi literami, cyframi, ukośnikiem (/) lub znakiem plus (+)
- znak równości (=)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzureServiceBusConnectionString znajduje zawartość zgodną ze wzorcem.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości zgodnej ze wzorcem.

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

(Technicznie ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych).

- Contoso
- Fabrikam
- Northwind
- Piaskownicy
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Netto

## <a name="azure-storage-account-key"></a>Klucz konta usługi Azure Storage

### <a name="format"></a>Formacie

Ciąg "DefaultEndpointsProtocol", po którym następuje znaki i ciągi opisane we wzorcu poniżej, w tym ciąg "AccountKey".

### <a name="pattern"></a>Wzór

- ciąg "DefaultEndpointsProtocol"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "AccountKey"
- znak od zera do dwóch białych znaków
- znak równości (=)
- znak od zera do dwóch białych znaków
- dowolna kombinacja 86 znaków, które są małymi lub wielkimi literami, cyframi, ukośnikiem (/) lub znakiem plus (+)
- dwa znaki równości (=)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzureStorageAccountKey znajduje zawartość zgodną ze wzorcem.
- Wyrażenie regularne CEP_AzureEmulatorStorageAccountFilter nie znajduje zawartości zgodnej ze wzorcem.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości zgodnej ze wzorcem.

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

(Technicznie ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych).

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Technicznie ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych).

- Contoso
- Fabrikam
- Northwind
- Piaskownicy
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Netto

## <a name="azure-storage-account-key-generic"></a>Klucz konta usługi Azure Storage (ogólny)

### <a name="format"></a>Formacie

Dowolna kombinacja 86 małych lub wielkich liter, cyfr, ukośnika (/) lub znaku plus (+), poprzedzona znakami lub po nich znakami opisanymi we wzorcu poniżej.

### <a name="pattern"></a>Wzór

- zero do jednego z symboli większych niż (>), apostrof ('), znak równości (=), cudzysłów () lub znak numeru (#)
- dowolna kombinacja 86 znaków, które są małymi lub wielkimi literami, cyframi, ukośnikiem (/) lub znakiem plus (+)
- dwa znaki równości (=)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_AzureStorageAccountKeyGeneric znajduje zawartość zgodną ze wzorcem.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```

## <a name="belgium-drivers-license-number"></a>Belgijski numer prawa jazdy

### <a name="format"></a>Formacie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

10 cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_belgium_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_belgium_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_belgium_eu_drivers_license_number"></a>s_license_number Keywords_belgium_eu_driver

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

## <a name="belgium-national-number"></a>Numer krajowy Belgii

### <a name="format"></a>Formacie

11 cyfr i opcjonalne ograniczniki

### <a name="pattern"></a>Wzór

11 cyfr plus ograniczniki:

- sześć cyfr i dwa opcjonalne okresy w formacie RR. MM.DD dla daty urodzenia
- Opcjonalny ogranicznik z kropki, kreski, spacji
- trzy cyfry sekwencyjne (nieparzyste dla mężczyzn, nawet dla kobiet)
- Opcjonalny ogranicznik z kropki, kreski, spacji
- dwie cyfry kontrolne

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_belgium_national_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_belgium_national_number.
- Suma kontrolna przechodzi.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_belgium_national_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- belasting aantal
- Bnn #
- Bnn
- carte d'identité
- identyfikator krajowy
- identifiantnational #
- identificatie
- Identyfikacji
- identyfikator
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- Tożsamości
- Napis
- numer krajowy
- rejestr krajowy
- nationalnumber #
- nationalnumber
- Nif #
- Nif
- numéro d'assuré
- numéro de registre national
- numéro de sécurité
- numéro d'identification
- numéro d'immatriculation
- numéro national
- numéronational #
- osobisty numer identyfikatora
- personalausweis
- personalidnumber #
- registratie
- Rejestracji
- registrationsnumme
- registrierung
- numer ubezpieczenia społecznego
- Ssn #
- Ssn
- steuernummer
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="belgium-passport-number"></a>Belgijski numer paszportu

### <a name="format"></a>Formacie

dwie litery, po których następuje sześć cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

dwie litery, po których następuje sześć cyfr

### <a name="checksum"></a>Suma kontrolna

nie dotyczy

### <a name="definition"></a>Definicja

 Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_belgium_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_belgium_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date2` regularne znajduje datę w formacie DD MM YY lub słowo kluczowe z `Keywords_eu_passport_date` pliku lub `Keywords_belgium_eu_passport_number` zostanie znalezione

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_belgium_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_belgium_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- Koszyk passeportu
- Passeport livre
- Pass-Nr
- Numer dostępu
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="belgium-physical-addresses"></a>Adresy fizyczne w Belgii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresami fizycznymi z Belgii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="belgium-value-added-tax-number"></a>Numer podatku od wartości dodanej w Belgii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

12-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

12-znakowy wzorzec alfanumeryczny:

- litera B lub b
- litera E lub e
- cyfra 0
- cyfra z zakresu od 1 do 9
- opcjonalna kropka lub łącznik lub spacja
- cztery cyfry
- opcjonalna kropka lub łącznik lub spacja
- cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_belgium_value_added_tax_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_belgium_value_added_tax_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_belgium_value_added_tax_number znajduje zawartość zgodną ze wzorcem.

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

- n° tva
- numer VAT
- numer vat
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- Btw
- Btw #
- Podatku vat #

## <a name="blood-test-terms"></a>Terminy badania krwi

Ta uwolniona nazwana jednostka wykrywa terminy związane z badaniami krwi, takimi jak *hCG*. Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="brand-medication-names"></a>Markowe nazwy leków

Ta uwolniona nazwana jednostka wykrywa nazwy leków marki, takich jak *Tylenol*. Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="brazil-cpf-number"></a>Numer CPF w Brazylii

### <a name="format"></a>Formacie

11 cyfr, które zawierają cyfrę wyboru i mogą być sformatowane lub niesformatowane

### <a name="pattern"></a>Wzór

Sformatowany:

- trzy cyfry
- okres
- trzy cyfry
- okres
- trzy cyfry
- łącznik
- dwie cyfry, które są cyframi kontrolnymi

Niesformatowany:

- 11 cyfr, w których ostatnie dwie cyfry są cyframi kontrolnymi

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_brazil_cpf znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_brazil_cpf.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_brazil_cpf znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Identyfikacji
- Rejestracja
- Dochodów
- Cadastro de Pessoas Físicas
- Imposto
- Identificação
- Inscrição
- Receita

## <a name="brazil-legal-entity-number-cnpj"></a>Numer brazylijskiej jednostki prawnej (CNPJ)

### <a name="format"></a>Formacie

14 cyfr zawierających numer rejestracji, numer gałęzi i cyfry wyboru oraz ograniczniki

### <a name="pattern"></a>Wzór

14 cyfr plus ograniczniki:

- dwie cyfry
- okres
- trzy cyfry
- okres
- trzy cyfry (te pierwsze osiem cyfr to numer rejestracji)
- ukośnik do przodu
- czterocyfrowy numer gałęzi
- łącznik
- dwie cyfry, które są cyframi kontrolnymi

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_brazil_cnpj znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_brazil_cnpj.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_brazil_cnpj znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Krajowy rejestr podmiotów prawnych
- Rejestr podatników
- Prawnej
- Prawnych
- Stan rejestracji
- Business
- Company
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- Cadastro Geral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação cadastral
- Inscrição
- Empresa

## <a name="brazil-national-identification-card-rg"></a>Brazylijska krajowa karta identyfikacyjna (RG)

### <a name="format"></a>Formacie

Registro Geral (stary format): Dziewięć cyfr

Registro de Identidade (RIC) (nowy format): 11 cyfr

### <a name="pattern"></a>Wzór

Registro Geral (stary format):

- dwie cyfry
- okres
- trzy cyfry
- okres
- trzy cyfry
- łącznik
- jedna cyfra, która jest cyfrą kontrolną

Registro de Identidade (RIC) (nowy format):

- 10 cyfr
- łącznik
- jedna cyfra, która jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_brazil_rg znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_brazil_rg.
- Suma kontrolna przechodzi.

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
- Dowód tożsamości
- identyfikator krajowy
- número de rregistro
- registro de Iidentidade
- registro geral
- RG (to słowo kluczowe uwzględnia wielkość liter)
- RIC (to słowo kluczowe uwzględnia wielkość liter)

## <a name="brazil-physical-addresses"></a>Adresy fizyczne Brazylii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Brazylii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="bulgaria-drivers-license-number"></a>Numer prawa jazdy Bułgarii

### <a name="format"></a>Formacie

dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_bulgaria_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_bulgaria_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>s_license_number Keywords_bulgaria_eu_driver

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки

## <a name="bulgaria-passport-number"></a>Numer paszportu Bułgarii

### <a name="format"></a>Formacie

dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_bulgaria_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_bulgaria_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_bulgaria_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_bulgaria_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт Nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="bulgaria-physical-addresses"></a>Adresy fizyczne Bułgarii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Bułgarii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="bulgaria-uniform-civil-number"></a>Jednolity numer cywilny Bułgarii
Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

10 cyfr bez spacji i ograniczników

- sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- dwie cyfry odpowiadające kolejności urodzeń
- jedna cyfra odpowiadająca płci: cyfra parzysta dla mężczyzn i cyfra nieparzysta dla kobiety
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_bulgaria_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_bulgaria_eu_national_id_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_bulgaria_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.

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

- Bnn #
- Bnn
- bucn #
- bucn
- edinen grazhdanski nomer
- np. #
- np.
- numer identyfikacyjny
- identyfikator krajowy
- numer krajowy
- nationalnumber #
- nationalnumber
- osobisty identyfikator
- nie osobiste
- numer osobisty
- personalidnumber #
- numer ubezpieczenia społecznego
- Ssn #
- Ssn
- jednolity identyfikator cywilny
- jednolity numer cywilny
- jednolity numer cywilny
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- unikatowy numer obywatelstwa
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
- униформ граждански id
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #

## <a name="canada-bank-account-number"></a>Numer konta bankowego w Kanadzie

### <a name="format"></a>Formacie

7 lub 12 cyfr

### <a name="pattern"></a>Wzór

Numer konta bankowego w Kanadzie to 7 lub 12 cyfr.

Numer tranzytu konta bankowego w Kanadzie to:

- pięć cyfr
- łącznik
- trzy cyfry OR
- a zero "0"
- osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_canada_bank_account_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_canada_bank_account_number.
- Wyrażenie regularne Regex_canada_bank_account_transit_number znajduje zawartość zgodną ze wzorcem.

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_canada_bank_account_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_canada_bank_account_number.

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

- kanada obligacji oszczędnościowych
- kanada revenue agency
- kanadyjska instytucja finansowa
- formularz depozytu bezpośredniego
- obywatel Kanady
- przedstawiciel prawny
- Notariusza
- komisarz do składania przysięgi
- zasiłek na opiekę nad dziećmi
- uniwersalna opieka nad dziećmi
- kanada zasiłek podatkowy na dziecko
- korzyść z podatku dochodowego
- zharmonizowany podatek od sprzedaży
- numer ubezpieczenia społecznego
- zwrot podatku dochodowego
- zasiłek podatkowy na dziecko
- płatności terytorialne
- numer instytucji
- wniosek o depozyt
- informacje bankowe
- depozyt bezpośredni

## <a name="canada-drivers-license-number"></a>Numer prawa jazdy w Kanadzie

### <a name="format"></a>Formacie

Różni się w zależności od prowincji

### <a name="pattern"></a>Wzór

Różne wzory obejmujące:

- Alberta
- Kolumbia Brytyjska
- Manitoba
- Nowy Brunszwik
- Nowa Fundlandia/Labrador
- Szkocji
- Ontario
- Wyspa Księcia Edwarda
- Quebec
- Saskatchewan

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_[province_name]_drivers_license_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_[province_name]_drivers_license_name.
- Znaleziono słowo kluczowe z Keyword_canada_drivers_license.

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
- Sterownik Lic
- Sterownik Lics
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Prawa jazdy
- Sterowniki
- SterownikiLics
- SterownikiLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- Sterowniki Lic
- Sterowniki Lics
- Licencja kierowcy
- Licencje kierowców
- Prawo jazdy
- Prawa jazdy
- Driver'Lic
- Driver'Lics
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Prawa jazdy
- Lic sterownika
- Lics kierowcy
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Prawa jazdy
- Driver'sLic
- Kursywę sterownika
- Driver'sLicense
- Driver'sLicenses
- Driver'sLicence
- Kursywą kierowcy
- Lic kierowcy
- Lics kierowcy
- Prawo jazdy
- Prawa jazdy
- Prawo jazdy
- Prawa jazdy
- Permis de Conduire
- Identyfikator
- Identyfikatory
- numer karty idcard
- Numery kart idcard
- idcard #
- #s idcard
- karta idcard
- karty idcard
- idcard
- numer identyfikacyjny
- numery identyfikacyjne
- Identyfikacji #
- #s identyfikacji
- karta identyfikacyjna
- karty identyfikacyjne
- Identyfikacji
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
- Sterownik Lic #
- Sterownik Lics #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Prawa jazdy #
- Sterowniki #
- SterownikiLics #
- DriversLicense #
- DriversLicenses #
- SterownikiLicence #
- DriversLicences #
- Sterowniki Lic #
- Sterowniki Lics #
- Licencja kierowcy #
- Licencje kierowców #
- Prawo jazdy #
- Prawa jazdy #
- Driver'Lic #
- Driver'Lics #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Prawa jazdy #
- Lic sterownika #
- Lics kierowcy #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Prawa jazdy #
- Driver'sLic #
- Kursywę sterownika #
- Driver'sLicense #
- Driver'sLicenses #
- Driver'sLicence #
- Kursywą kierowcy #
- Lic kierowcy #
- Lics kierowcy #
- Prawo jazdy #
- Prawa jazdy #
- Prawo jazdy #
- Prawa jazdy #
- Permis de Conduire #
- Identyfikator #
- Identyfikatory #
- karta idcard #
- karty idcard #
- idcard #
- karta identyfikacyjna #
- karty identyfikacyjne #
- Identyfikacji #

## <a name="canada-health-service-number"></a>Numer usługi kondycji Kanady

### <a name="format"></a>Formacie

 10 cyfr

### <a name="pattern"></a>Wzór

10 cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_canada_health_service_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_canada_health_service_number.

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

- osobisty numer służby zdrowia
- informacje o pacjencie
- usługi zdrowotne
- usługi specjalistyczne
- wypadek samochodowy
- szpital pacjentów
- Psychiatra
- odszkodowania dla pracowników
- Niepełnosprawności

## <a name="canada-passport-number"></a>Numer paszportu Kanada

### <a name="format"></a>Formacie

dwie wielkie litery, po których następuje sześć cyfr

### <a name="pattern"></a>Wzór

dwie wielkie litery, po których następuje sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_canada_passport_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_canada_passport_number lub Keyword_passport.

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

- obywatelstwo kanadyjskie
- paszport kanadyjski
- aplikacja paszportowa
- zdjęcia paszportowe
- certyfikowany tłumacz
- obywatele kanadyjscy
- czas przetwarzania
- aplikacja do odnawiania

#### <a name="keyword_passport"></a>Keyword_passport

- Numer paszportu
- Nr paszportu
- Paszport #
- Paszport #
- PassportID
- Passportno
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n °
- Passeport — inne niż
- Passeport #
- Passeport #
- PasseportNon
- Passeportn °

## <a name="canada-personal-health-identification-number-phin"></a>Kanada osobisty numer identyfikacyjny zdrowia (PHIN)

### <a name="format"></a>Formacie

dziewięć cyfr

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_canada_phin znajduje zawartość zgodną ze wzorcem.
- Odnaleziono co najmniej dwa słowa kluczowe z Keyword_canada_phin lub Keyword_canada_provinces.

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
- akt dotyczący informacji o zdrowiu
- informacje o podatku dochodowym
- zdrowie manitoba
- rejestracja kondycji
- zakupy na receptę
- uprawnienia do świadczeń
- zdrowie osobiste
- pełnomocnictwo
- numer rejestracji
- osobisty numer służby zdrowia
- skierowanie lekarza
- specjalista ds. odnowy biologiczn
- skierowanie pacjenta
- zdrowie i dobre samopoczucie

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- Nunavut
- Quebec
- Terytoria północno-zachodnie
- Ontario
- Kolumbia Brytyjska
- Alberta
- Saskatchewan
- Manitoba
- Yukon
- Nowa Fundlandia i Labrador
- Nowy Brunszwik
- Szkocji
- Wyspa Księcia Edwarda
- Kanada

## <a name="canada-physical-addresses"></a>Adresy fizyczne w Kanadzie

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Kanady. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="canada-social-insurance-number"></a>Kanada numer ubezpieczenia społecznego

### <a name="format"></a>Formacie

dziewięć cyfr z opcjonalnymi łącznikami lub spacjami

### <a name="pattern"></a>Wzór

Sformatowany:

- trzy cyfry
- łącznik lub spacja
- trzy cyfry
- łącznik lub spacja
- trzy cyfry

Niesformatowane: dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_canadian_sin znajduje zawartość zgodną ze wzorcem.
- Co najmniej dwa z następujących wzorców:
    - Znaleziono słowo kluczowe z Keyword_sin.
    - Znaleziono słowo kluczowe z Keyword_sin_collaborative.
    - Funkcja Func_eu_date znajduje datę w odpowiednim formacie daty.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_unformatted_canadian_sin znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_sin.
- Suma kontrolna przechodzi.

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

- Grzechu
- ubezpieczenie społeczne
- numero d'assurance sociale
- Grzechy
- Ssn
- ssns
- zabezpieczenia społeczne
- numero d'assurance social
- krajowy numer identyfikacyjny
- identyfikator krajowy
- Grzechu #
- soc ins
- social ins

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- prawo jazdy
- prawo jazdy
- prawo jazdy
- prawo jazdy
- DOB
- Dataurodzenia
- Urodziny
- Data urodzenia

## <a name="chile-identity-card-number"></a>Numer karty tożsamości Chile

### <a name="format"></a>Formacie

od siedmiu do ośmiu cyfr oraz ograniczniki cyfry lub litery kontrolnej

### <a name="pattern"></a>Wzór

od siedmiu do ośmiu cyfr oraz ograniczników:

- od jednej do dwóch cyfr
- opcjonalny okres
- trzy cyfry
- opcjonalny okres
- trzy cyfry
- kreska
- jedna cyfra lub litera (bez uwzględniania wielkości liter), która jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_chile_id_card znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_chile_id_card.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_chile_id_card znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- identyfikacja krajowa
- krajowy numer identyfikacyjny
- identyfikator krajowy
- número de identificación nacional
- rol único nacional
- rol único tributario
- URUCHOMIĆ
- KOLEINY
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- URUCHOMIĆ #
- KOLEINY #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad numero
- Chilijska tożsamość nie.
- Chilijski numer tożsamości
- Tożsamość chilijska #
- Unikatowy rejestr podatkowy
- Unikatowa rola dopływowa
- Unikatowa rola podatkowa
- Unikatowy numer dopływowy
- Unikatowy numer krajowy
- Unikatowa rola krajowa
- Unikatowa rola krajowa
- Chile tożsamość nie.
- Numer tożsamości Chile
- Tożsamość Chile #
- R.U.T
- R.U.N

## <a name="china-resident-identity-card-prc-number"></a>Numer karty tożsamości rezydenta Chin (ChRL)

### <a name="format"></a>Formacie

18 cyfr

### <a name="pattern"></a>Wzór

18 cyfr:

- sześć cyfr, które są kodem adresu
- osiem cyfr w postaci RRRRMMDD, które są datą urodzenia
- trzy cyfry, które są kodem zamówienia
- jedna cyfra, która jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_china_resident_id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_china_resident_id.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_china_resident_id znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- Identyfikator rezydenta
- CHRL
- Krajowa karta identyfikacyjna
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定

## <a name="credit-card-number"></a>Numer karty kredytowej

### <a name="format"></a>Formacie

Od 14 do 19 cyfr, które mogą być sformatowane lub niesformatowane (dddddddd) i które muszą przejść test Luhna.

### <a name="pattern"></a>Wzór

Wykrywa karty ze wszystkich głównych marek na całym świecie, w tym Visa, MasterCard, Discover Card, JCB, American Express, karty upominkowe, karty diner, Rupay i China UnionPay.

### <a name="checksum"></a>Suma kontrolna

Tak, sprawdzanie luhna

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_credit_card znajduje zawartość zgodną ze wzorcem.
- Spełniony jest jeden z następujących warunków:
  - Znaleziono słowo kluczowe z Keyword_cc_verification.
  - Znaleziono słowo kluczowe z Keyword_cc_name.
  - Funkcja Func_expiration_date znajduje datę w odpowiednim formacie daty.
- Suma kontrolna przechodzi.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_credit_card znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Cvn
- Cid
- cvc2
- cvv2
- blok pinezki
- kod zabezpieczeń
- numer zabezpieczeń
- nie zabezpieczeń
- numer problemu
- problem nie
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
- Dorsza. sicurezza
- dojrzew sicurezza
- n autorizzazione
- código
- codigo
- Dorsza. Seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- Dorsza. seguranca
- Dorsza. segurança
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
- Vto
- data de expiração
- data de expiracao
- data em que expira
- validade
- Valor
- vencimento
- Transakcji
- numer transakcji
- numer referencyjny
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- Amex
- american express
- americanexpress
- americano espresso
- Visa
- Mastercard
- karta główna
- Mc
- Mastercard
- karty główne
- diner's Club
- diners club
- dinersclub
- Odkryj
- odnajdywanie karty
- discovercard
- odnajdywanie kart
- JCB
- BrandSmart
- japońskie biuro kart
- carte blanche
- carteblanche
- karta kredytowa
- Cc #
- cc#:

- data wygaśnięcia
- exp, data
- data wygaśnięcia
- data wygaśnięcia
- data d'exp
- data wygaśnięcia
- karta bankowa
- Karta bankowa
- numer karty
- numer karty
- numer karty
- cardnumbers
- numery kart
- karta kredytowa
- karty kredytowe
- karty kredytowe
- Ccn
- posiadacz karty
- Karty
- posiadacze kart
- Posiadaczy kart
- sprawdzanie karty
- checkcard
- sprawdzanie kart
- karty wyboru
- Debetową
- Debitcard
- Debetowe
- karty debetowe
- karta atm
- atmcard
- karty atm
- atmcards
- Enroute
- Drodze
- typ karty
- Cardmember Acct
- konto cardmember
- Cardno
- Karta firmowa
- Karty firmowe
- Typ karty
- numer konta karty
- konto członka karty
- Cardmember Acct.
- numer karty.
- brak karty
- numer karty
- carte bancaire
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- n° de la carte
- n° de carte
- kreditkarte
- karte
- karteninhaber
- karteninhabers
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr
- kartennumer
- kreditkartennummer
- kreditkarten-nummer
- carta di credito
- carta credito
- N. Carta
- n carta
- nr. Carta
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
- n° de tarjeta
- Nr. de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjetahabiente
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
- nÏ do cartão
- n° do cartao
- Nº. do cartão
- no do cartão
- no do cartao
- Nr. do cartão
- Nr. do cartao
- rupay
- wynagrodzenie związkowe
- Unionpay
- diner's
- Diner amerykański
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

## <a name="croatia-drivers-license-number"></a>Numer prawa jazdy Chorwacji

### <a name="format"></a>Formacie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_croatia_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_croatia_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_croatia_eu_drivers_license_number"></a>s_license_number Keywords_croatia_eu_driver

- vozačka dozvola
- vozačke dozvole

## <a name="croatia-identity-card-number"></a>Numer karty tożsamości Chorwacji

Jednostka ta znajduje się w typie informacji poufnych o krajowym numerze identyfikacyjnym UE. Jest ona dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie

dziewięć cyfr

### <a name="pattern"></a>Wzór

dziewięć kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_croatia_id_card znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_croatia_id_card.

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

- majstorski broj građana
- główny numer obywatela
- nacionalni identifikacijski broj
- krajowy numer identyfikacyjny
- oib #
- oib
- osobna iskaznica
- identyfikator osobni
- osobni identifikacijski broj
- osobisty numer identyfikacyjny
- porezni broj
- porezni identifikacijski broj
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="croatia-passport-number"></a>Numer paszportu Chorwacji

### <a name="format"></a>Formacie

dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_croatia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_croatia_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_croatia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_croatia_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- Br. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>Numer identyfikacyjny Chorwacji (OIB)

### <a name="format"></a>Formacie

11 cyfr

### <a name="pattern"></a>Wzór

11 cyfr:

- 10 cyfr
- cyfra końcowa jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_croatia_oib_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_croatia_eu_tax_file_number.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_croatia_oib_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- majstorski broj građana
- główny numer obywatela
- nacionalni identifikacijski broj
- krajowy numer identyfikacyjny
- oib #
- oib
- osobna iskaznica
- identyfikator osobni
- osobni identifikacijski broj
- osobisty numer identyfikacyjny
- porezni broj
- porezni identifikacijski broj
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="croatia-physical-addresses"></a>Adresy fizyczne Chorwacji

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Chorwacji. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="cyprus-drivers-license-number"></a>Numer licencji kierowcy cypryjskiego

### <a name="format"></a>Formacie

12 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

12 cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_cyprus_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_cyprus_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>s_license_number Keywords_cyprus_eu_driver

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης

## <a name="cyprus-identity-card"></a>Cypryjski dowód tożsamości

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

10 cyfr

### <a name="checksum"></a>Suma kontrolna

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_cyprus_eu_national_id_card` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_cyprus_eu_national_id_card`

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

- numer karty identyfikatora
- numer karty tożsamości
- kimlik karti
- krajowy numer identyfikacyjny
- osobisty numer identyfikatora
- ταυτοτητασ

## <a name="cyprus-passport-number"></a>Numer paszportu cypryjskiego

### <a name="format"></a>Formacie

jedna litera, po której następuje od 6 do 8 cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

jedna litera, po której następuje od sześciu do ośmiu cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_cyprus_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_cyprus_eu_passport_number` .
- Wyrażenie `Regex_cyprus_eu_passport_date` regularne znajduje datę w formacie DD/MM/RRRR lub znaleziono słowo kluczowe z `Keywords_cyprus_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_cyprus_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_cyprus_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- pasaportu
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- Pasaport Kimliği
- pasaport numarası
- Pasaport nie.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- wygaśnie
- wydane w dniu

## <a name="cyprus-physical-addresses"></a>Adresy fizyczne cypryjskie

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Cypru. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="cyprus-tax-identification-number"></a>Numer identyfikacyjny podatku cypryjskiego

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

osiem cyfr i jedna litera w określonym wzorcu

### <a name="pattern"></a>Wzór

osiem cyfr i jedna litera:

- a "0" lub "9"
- siedem cyfr
- jedna litera (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_cyprus_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_cyprus_eu_tax_file_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_cyprus_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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

- identyfikator podatkowy
- kod identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- Tic #
- Tic
- identyfikator cyny
- nie cyny
- Tin #
- vergi kimlik kodu
- vergi kimlik numarası
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού

## <a name="czech-drivers-license-number"></a>Czeski numer prawa jazdy

### <a name="format"></a>Formacie

dwie litery, po których następuje sześć cyfr

### <a name="pattern"></a>Wzór

osiem liter i cyfr:

- litera "E" (bez uwzględniania wielkości liter)
- litera
- spację (opcjonalnie)
- sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_czech_republic_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_czech_republic_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>s_license_number Keywords_czech_republic_eu_driver

- řidičský prúkaz
- řidičské průkazy
- číslo řidičského průkazu
- čísla řidičských průkazů

## <a name="czech-passport-number"></a>Czeski numer paszportu

### <a name="format"></a>Formacie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

osiem cyfr bez spacji i ograniczników

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_czech_republic_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_czech_republic_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_czech_republic_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_czech_republic_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cestovní pas
- číslo pasu
- cestovní pasu
- passeport no
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="czech-personal-identity-number"></a>Czeski numer tożsamości osobistej

### <a name="format"></a>Formacie

dziewięć cyfr z opcjonalnym ukośnikiem (stary format)

10 cyfr z opcjonalnym ukośnikiem (nowy format)

### <a name="pattern"></a>Wzór

dziewięć cyfr (stary format):

- sześć cyfr reprezentujących datę urodzenia
- opcjonalny ukośnik do przodu
- trzy cyfry

10 cyfr (nowy format):

- sześć cyfr reprezentujących datę urodzenia
- opcjonalny ukośnik do przodu
- cztery cyfry, w których ostatnia cyfra jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_czech_id_card znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_czech_id_card.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_czech_id_card_new_format znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- identyfikator Republiki Czeskiej
- czechidno #
- daňové číslo
- identifikační číslo
- brak tożsamości
- numer tożsamości
- identityno #
- identityno
- numer ubezpieczenia
- krajowy numer identyfikacyjny
- nationalnumber #
- numer krajowy
- osobní číslo
- personalidnumber #
- osobisty numer identyfikatora
- osobisty numer identyfikacyjny
- numer osobisty
- Pid #
- Pid
- pojištění číslo
- rč
- rodne cislo
- rodné číslo
- Ssn
- Ssn #
- numer ubezpieczenia społecznego
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- unikatowy numer identyfikacyjny

## <a name="czech-republic-physical-addresses"></a>Adresy fizyczne w Czechach

Ta rozdzielona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Czech. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="denmark-drivers-license-number"></a>Duński numer prawa jazdy

### <a name="format"></a>Formacie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_denmark_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_denmark_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_denmark_eu_drivers_license_number"></a>s_license_number Keywords_denmark_eu_driver

- kørekort
- kørekortnummer

## <a name="denmark-passport-number"></a>Numer paszportu Danii

### <a name="format"></a>Formacie

dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_denmark_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_denmark_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date2` regularne znajduje datę w formacie DD MM YY lub odnaleziono słowo kluczowe `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_denmark_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_denmark_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="denmark-personal-identification-number"></a>Osobisty numer identyfikacyjny Danii

### <a name="format"></a>Formacie

10 cyfr zawierających łącznik

### <a name="pattern"></a>Wzór

10 cyfr:

- sześć cyfr w formacie DDMMYY, które są datą urodzenia
- opcjonalne spacja lub łącznik
- cztery cyfry, w których cyfra końcowa jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Func_denmark_eu_tax_file_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_denmark_id.
- Suma kontrolna przechodzi.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie regularne Func_denmark_eu_tax_file_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Cpr
- Cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- karta kondycji
- numer karty ubezpieczenia zdrowotnego
- numer ubezpieczenia zdrowotnego
- numer identyfikacyjny
- identifikationsnummer
- identifikationsnummer #
- numer tożsamości
- krankenkassennummer
- nationalid #
- nationalnumber #
- numer krajowy
- personalidnumber #
- personalidentityno #
- osobisty numer identyfikatora
- personnummer
- personnummer #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- Ssn
- Ssn #
- identyfikator skat
- kode skat
- skat nummer
- skattenummer
- numer ubezpieczenia społecznego
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- kod podatkowy
- karta ubezpieczenia zdrowotnego podróży
- uniqueidentityno #
- numer podatkowy
- numer rejestracji podatkowej
- identyfikator podatkowy
- numer identyfikacji podatkowej
- taxid #
- taxnumber #
- numer podatkowy
- taksoń #
- taxnumber
- numer identyfikacji podatkowej
- Tin #
- taxidno #
- taxidnumber #
- numer podatkowy #
- identyfikator cyny
- nie cyny
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

## <a name="denmark-physical-addresses"></a>Adresy fizyczne Danii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Danii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="diseases"></a>Chorób

Ta uwolniona nazwana jednostka wykrywa tekst, który pasuje do nazw chorób, takich jak *cukrzyca*. Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="drug-enforcement-agency-dea-number"></a>Numer Agencji Egzekwowania Narkotyków (DEA)

### <a name="format"></a>Formacie

dwie litery, po których następuje siedem cyfr

### <a name="pattern"></a>Wzór

Wzorzec musi zawierać wszystkie następujące elementy:

- jedna litera (bez uwzględniania wielkości liter) z tego zestawu możliwych liter: A/B/F/G/M/P/R, który jest kodem rejestrującym
- jedna litera (bez uwzględniania wielkości liter), która jest pierwszą literą nazwiska lub cyfry rejestrujący "9"
- siedem cyfr, z których ostatni to cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_dea_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z `Keyword_dea_number`
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_dea_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- Dea
- Dea #
- administracja egzekwowania narkotyków
- organ ścigania narkotyków

## <a name="estonia-drivers-license-number"></a>Numer prawa jazdy Estonii

### <a name="format"></a>Formacie

dwie litery, po których następuje sześć cyfr

### <a name="pattern"></a>Wzór

dwie litery i sześć cyfr:

- litery "ET" (bez uwzględniania wielkości liter)
- sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_estonia_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_estonia_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_estonia_eu_drivers_license_number"></a>s_license_number Keywords_estonia_eu_driver

- permis de conduire
- juhilubade numbrid
- numer juhiloa
- juhiluba

## <a name="estonia-passport-number"></a>Numer paszportu Estonii

### <a name="format"></a>Formacie

jedna litera, po której następuje siedem cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

jedna litera, po której następuje siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_estonia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_estonia_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_estonia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_estonia_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passi number passinumbrid document number document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="estonia-personal-identification-code"></a>Estoński osobisty kod identyfikacyjny

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

11 cyfr:

- jedna cyfra, która odpowiada płci i wieku urodzenia (nieparzysta liczba mężczyzn, parzysta liczba kobiet; 1-2: 19 wieku; 3-4: 20 wieku; 5-6: 21 wieku)
- sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- trzy cyfry, które odpowiadają numerowi seryjnemu oddzielającemu osoby urodzone w tym samym dniu
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_estonia_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_estonia_eu_national_id_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_estonia_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.

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
- Ik
- isikukood #
- isikukood
- maksu id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- krajowy numer identyfikacyjny
- numer krajowy
- kod osobisty
- osobisty numer identyfikatora
- osobisty kod identyfikacyjny
- osobisty numer identyfikacyjny
- personalidnumber #
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="estonia-physical-addresses"></a>Adresy fizyczne Estonii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Estonii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="eu-debit-card-number"></a>Numer karty debetowej UE

### <a name="format"></a>Formacie

16 cyfr

### <a name="pattern"></a>Wzór

Złożony i niezawodny wzorzec

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_eu_debit_card znajduje zawartość zgodną ze wzorcem.
- Co najmniej jedna z następujących wartości jest prawdziwa:
    - Znaleziono słowo kluczowe z Keyword_eu_debit_card.
    - Znaleziono słowo kluczowe z Keyword_card_terms_dict.
    - Znaleziono słowo kluczowe z Keyword_card_security_terms_dict.
    - Znaleziono słowo kluczowe z Keyword_card_expiration_terms_dict.
    - Funkcja Func_expiration_date znajduje datę w odpowiednim formacie daty.
- Suma kontrolna przechodzi.

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
- numer karty.
- numer zabezpieczeń
- Cc #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr
- acct num
- acct no
- american express
- americanexpress
- americano espresso
- Amex
- karta atm
- karty atm
- atm kaart
- atmcard
- atmcards
- atmkaart
- atmkaarten
- Bancontact
- karta bankowa
- bankkaart
- posiadacz karty
- posiadacze kart
- numer karty
- numer karty
- numery kart
- typ karty
- cardano numerico
- Karty
- Posiadaczy kart
- numer karty
- cardnumbers
- carta bianca
- carta credito
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
- Cb
- Ccn
- sprawdzanie karty
- sprawdzanie kart
- checkcard
- karty wyboru
- chequekaart
- Cirrus
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- karta kredytowa
- karty kredytowe
- karta kredytowa
- karty kredytowe
- debetkaart
- debetkaarten
- Debetową
- Debetowe
- Debitcard
- karty debetowe
- debito automatico
- diners club
- dinersclub
- Odkryj
- odnajdywanie karty
- odnajdywanie kart
- discovercard
- discovercards
- débito automático
- Edc
- eigentümername
- europejska karta debetowa
- hoofdkaart
- hoofdkaarten
- w viaggio
- japońskie biuro kart
- japanse kaartdienst
- Jcb
- kaart
- kaart num
- kaartaantal
- kaartaantallen
- kaarthouder
- kaarthouders
- karte
- karteninhaber
- karteninhabers
- kartennr
- kartennumer
- kreditkarte
- kreditkarten-nummer
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartennummer
- kreditkartentyp
- Maestro
- karta główna
- karty główne
- Mastercard
- Mastercard
- Mc
- mister cash
- n carta
- Carta
- no de tarjeta
- no do cartao
- no do cartão
- Nr. de tarjeta
- Nr. do cartao
- Nr. do cartão
- nr carta
- nr. Carta
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
- n° carta
- n° de carte
- n° de la carte
- n° de tarjeta
- n° do cartao
- nÏ do cartão
- Nº. do cartão
- número de cartao
- número de cartão
- número de tarjeta
- número do cartao
- scheda dell'assegno
- scheda dell'atmosfera
- scheda dell'atmosfera
- scheda della banca
- scheda di controllo
- scheda di debito
- scheda matrice
- schede dell'atmosfera
- schede di controllo
- schede di debito
- schede matrici
- scoprono la scheda
- scoprono le schede
- Podróżujący samotnie
- supporti di scheda
- supporto di scheda
- Przełącznik
- tarjeta atm
- tarjeta credito
- tarjeta de atm
- tarjeta de credito
- tarjeta de debito
- tarjeta debito
- tarjeta no
- tarjetahabiente
- tipo della scheda
- ufficio giapponese della
- scheda
- v pay
- v-pay
- Visa
- wiza plus
- visa electron
- Visto
- visum
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- numer identyfikacyjny karty
- weryfikacja karty
- cardi la verifica
- Cid
- cod seg
- cod seguranca
- cod segurança
- dojrzew sicurezza
- Dorsza. Seg
- Dorsza. seguranca
- Dorsza. segurança
- Dorsza. sicurezza
- codice di sicurezza
- codice di verifica
- codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- cryptogram
- cryptogramme
- cv2
- Cvc
- cvc2
- Cvn
- Cvv
- cvv2
- cód seguranca
- cód segurança
- cód. seguranca
- cód. segurança
- código
- código de seguranca
- código de segurança
- de kaart, kontrolka
- geeft nr uit
- problem nie
- numer problemu
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- Nr. dell'edizione
- Nr. di sicurezza
- numero de securite
- numero de verificacao
- numero dell'edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero van veiligheid
- numéro de sécurité
- n° autorizzazione
- número de verificação
- perno il blocco
- blok pinezki
- prufziffer
- prüfziffer
- kod zabezpieczeń
- nie zabezpieczeń
- numer zabezpieczeń
- sicherheits kode
- sicherheitscode
- sicherheitsnummer
- speldblok
- veiligheid nr
- veiligheidsaantal
- veiligheidscode
- veiligheidsnummer
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
- espira
- espira
- exp, data
- exp datum
- Wygaśnięcia
- Wygasa
- Wygasa
- Upływie terminu ważności
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
- Valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- Vto
- válido hasta

## <a name="eu-drivers-license-number"></a>Numer prawa jazdy UE

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
- [Luksemburg](#luxemburg-drivers-license-number)
- [Malta](#malta-drivers-license-number)
- [Holandia](#netherlands-drivers-license-number)
- [Polska](#poland-drivers-license-number)
- [Portugalia](#portugal-drivers-license-number)
- [Rumunia](#romania-drivers-license-number)
- [Słowacja](#slovakia-drivers-license-number)
- [Słowenia](#slovenia-drivers-license-number)
- [Hiszpania](#spain-drivers-license-number)
- [Szwecja](#sweden-drivers-license-number)
- [WIELKIEJ BRYTANII.](#uk-drivers-license-number)

## <a name="eu-national-identification-number"></a>Krajowy numer identyfikacyjny UE

Te jednostki znajdują się w krajowym numerze identyfikacyjnym UE i są typami informacji poufnych.

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
- [Luksemburg](#luxemburg-national-identification-number-natural-persons)
- [Malta](#malta-identity-card-number)
- [Holandia](#netherlands-citizens-service-bsn-number)
- [Polska](#poland-national-id-pesel)
- [Portugalia](#portugal-citizen-card-number)
- [Rumunia](#romania-personal-numeric-code-cnp)
- [Słowacja](#slovakia-personal-number)
- [Słowenia](#slovenia-unique-master-citizen-number)
- [Hiszpania](#spain-dni)
- [WIELKIEJ BRYTANII.](#uk-national-insurance-number-nino)

## <a name="eu-passport-number"></a>Numer paszportu UE

Te jednostki znajdują się w numerze paszportu UE i są typami informacji poufnych. Te jednostki znajdują się w pakiecie numerów paszportów UE.

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
- [Luksemburg](#luxemburg-passport-number)
- [Malta](#malta-passport-number)
- [Holandia](#netherlands-passport-number)
- [Polska](#poland-passport-number)
- [Portugalia](#portugal-passport-number)
- [Rumunia](#romania-passport-number)
- [Słowacja](#slovakia-passport-number)
- [Słowenia](#slovenia-passport-number)
- [Hiszpania](#spain-passport-number)
- [Szwecja](#sweden-passport-number)
- [Numer paszportu USA/Wielkiej Brytanii](#usuk-passport-number)

## <a name="eu-social-security-number-or-equivalent-identification"></a>Numer ubezpieczenia społecznego UE lub równoważna identyfikacja

Te jednostki znajdują się w numerze ubezpieczenia społecznego UE lub równoważnej identyfikacji i są typami informacji poufnych.

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

## <a name="eu-tax-identification-number"></a>Numer identyfikacji podatkowej UE

Te jednostki znajdują się w typie informacji poufnych o numerze identyfikacji podatkowej UE.

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
- [Luksemburg](#luxemburg-national-identification-number-non-natural-persons)
- [Malta](#malta-tax-identification-number)
- [Holandia](#netherlands-tax-identification-number)
- [Polska](#poland-tax-identification-number)
- [Portugalia](#portugal-tax-identification-number)
- [Rumunia](#romania-personal-numeric-code-cnp)
- [Słowacja](#slovakia-personal-number)
- [Słowenia](#slovenia-tax-identification-number)
- [Hiszpania](#spain-tax-identification-number)
- [Szwecja](#sweden-tax-identification-number)
- [WIELKIEJ BRYTANII.](#uk-unique-taxpayer-reference-number)

## <a name="finland-drivers-license-number"></a>Numer prawa jazdy Finlandii

### <a name="format"></a>Formacie

10 cyfr zawierających łącznik

### <a name="pattern"></a>Wzór

10 cyfr zawierających łącznik:

- sześć cyfr
- łącznik
- trzy cyfry
- cyfra lub litera

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_finland_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_finland_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_finland_eu_drivers_license_number"></a>s_license_number Keywords_finland_eu_driver

- ajokortti
- permis de conduire
- ajokortin numero
- kuljettaja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot

## <a name="finland-european-health-insurance-number"></a>Europejski numer ubezpieczenia zdrowotnego w Finlandii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

20-cyfrowy numer

### <a name="pattern"></a>Wzór

20-cyfrowy numer:

- 10 cyfr — 8024680246
- opcjonalne spacja lub łącznik
- 10 cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Rejestr Regex_Finland_European_Health_Insurance_Number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Finland_European_Health_Insurance_Number.

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

- Ekuz #
- Ekuz
- finlandehicnumber #
- finska sjukförsäkringskort
- karta kondycji
- karta ubezpieczenia zdrowotnego
- numer ubezpieczenia zdrowotnego
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti

## <a name="finland-national-id"></a>Identyfikator krajowy Finlandii

### <a name="format"></a>Formacie

sześć cyfr plus znak wskazujący wiek plus trzy cyfry oraz cyfrę kontrolną

### <a name="pattern"></a>Wzór

Wzorzec musi zawierać wszystkie następujące elementy:

- sześć cyfr w formacie DDMMYY, które są datą urodzenia
- znacznik wieku ("-", "+" lub "a")
- trzycyfrowy osobisty numer identyfikacyjny
- cyfra lub litera (bez uwzględniania wielkości liter), która jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- funkcja Func_finnish_national_id znajduje zawartość zgodną ze wzorcem
- znaleziono słowo kluczowe z Keyword_finnish_national_id
- suma kontrolna przechodzi

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- funkcja Func_finnish_national_id znajduje zawartość zgodną ze wzorcem
- suma kontrolna przechodzi

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
- numer identyfikatora
- numer identyfikacyjny
- identiteetti, numero
- numer tożsamości
- idnumber
- kansallinen henkilötunnus
- kansallisen henkilökortin
- dowód osobisty
- identyfikator krajowy nr.
- osobisty identyfikator
- kod tożsamości osobistej
- personalidnumber #
- personbeteckning
- personnummer
- numer ubezpieczenia społecznego
- sosiaaliturvatunnus
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- tunnistenumero
- numero usługi tunnus
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus

## <a name="finland-passport-number"></a>Numer paszportu Finlandii

Ta jednostka jest dostępna w typie informacji poufnych numeru paszportu UE i jest dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie
kombinacja dziewięciu liter i cyfr

### <a name="pattern"></a>Wzór

kombinacja dziewięciu liter i cyfr:

- dwie litery (bez uwzględniania wielkości liter)
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_finland_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keyword_finland_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_finland_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keyword_finland_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomalainen passi
- passin numero
- passin numero. #
- passin numero #
- passin numero.
- Passi #
- numer passi

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="finland-physical-addresses"></a>Adresy fizyczne Finlandii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Finlandii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="france-drivers-license-number"></a>Numer prawa jazdy we Francji

Ta jednostka jest dostępna w typie poufnych informacji o numerze prawa jazdy UE i jest dostępna jako samodzielna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie

12 cyfr

### <a name="pattern"></a>Wzór

12 cyfr z weryfikacją, aby zdyskontować podobne wzorce, takie jak francuskie numery telefonów

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- funkcja Func_french_drivers_license znajduje zawartość zgodną ze wzorcem.
- znaleziono słowo kluczowe z Keyword_french_drivers_license.

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
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl
- permis de conduire
- numer licencji
- numer licencji
- numery licencji
- numery licencji
- numéros de licence

## <a name="france-health-insurance-number"></a>Numer ubezpieczenia zdrowotnego we Francji

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

21-cyfrowy numer

### <a name="pattern"></a>Wzór

21-cyfrowy numer:

- 10 cyfr
- opcjonalne miejsce
- 10 cyfr
- opcjonalne miejsce
- cyfra

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Regex_France_Health_Insurance_Number znajduje zawartość zgodną ze wzorcem.
- znaleziono słowo kluczowe z Keyword_France_Health_Insurance_Number.

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

## <a name="france-national-id-card-cni"></a>Francuski identyfikator krajowy (CNI)

### <a name="format"></a>Formacie

12 cyfr

### <a name="pattern"></a>Wzór

12 cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie regularne Regex_france_cni znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_france_eu_national_id_card.

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
- carte nationale d'idenite nie
- cni #
- cni
- compte bancaire
- krajowy numer identyfikacyjny
- tożsamość narodowa
- nationalidno #
- numéro d'assurance maladie
- numéro de carte vitale

## <a name="france-passport-number"></a>Numer paszportu We Francji

Ta jednostka jest dostępna w typie informacji poufnych o numerze paszportu UE. Jest również dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie

dziewięć cyfr i liter

### <a name="pattern"></a>Wzór

dziewięć cyfr i liter:

- dwie cyfry
- dwie litery (bez uwzględniania wielkości liter)
- pięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_fr_passport` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_france_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date3` regularne znajduje datę w formacie DD MM RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_fr_passport` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_france_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
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
- passeport livre
- passeport carte
- numéro passeport
- passeport n°
- n° du passeport
- n° passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="france-physical-addresses"></a>Adresy fizyczne We Francji

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Francji. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="france-social-security-number-insee"></a>Numer ubezpieczenia społecznego We Francji (INSEE)

### <a name="format"></a>Formacie

15 cyfr

### <a name="pattern"></a>Wzór

Musi być zgodny z jednym z dwóch wzorców:

- 13 cyfr, po których następuje spację, po której następuje dwie cyfry

  lub

- 15 kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_french_insee` znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_fr_insee.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_french_insee lub Func_fr_insee znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- kod sécu
- d'identité nationale
- insee
- fssn #
- le numéro d'identification nationale
- le code de la sécurité sociale
- identyfikator krajowy
- identyfikacja krajowa
- no d'identité
- Nr. d'identité
- numéro d'assurance
- numéro d'identité
- numero d'identite
- numéro de sécu
- numéro de sécurité sociale
- no d'identite
- Nr. d'identite
- Ssn
- Ssn #
- sécurité sociale
- securité sociale
- securite sociale
- socialsecuritynumber
- numer ubezpieczenia społecznego
- kod zabezpieczenia społecznego
- numer ubezpieczenia społecznego

## <a name="france-tax-identification-number"></a>Numer identyfikacyjny podatku we Francji

### <a name="format"></a>Formacie

13 cyfr

### <a name="pattern"></a>Wzór

13 cyfr

- Jedna cyfra, która musi mieć wartość 0, 1, 2 lub 3
- Jedna cyfra
- Spacja (opcjonalnie)
- Dwie cyfry
- Spacja (opcjonalnie)
- Trzy cyfry
- Spacja (opcjonalnie)
- Trzy cyfry
- Spacja (opcjonalnie)
- Trzy cyfry kontrolne

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_france_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_france_eu_tax_file_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_france_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="france-value-added-tax-number"></a>Numer podatku od wartości dodanej we Francji

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

13-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

13-znakowy wzorzec alfanumeryczny:

- dwie litery — FR (bez uwzględniania wielkości liter)
- opcjonalne spacja lub łącznik
- dwie litery lub cyfry
- opcjonalne spacja, kropka, łącznik lub przecinek
- trzy cyfry
- opcjonalne spacja, kropka, łącznik lub przecinek
- trzy cyfry
- opcjonalne spacja, kropka, łącznik lub przecinek
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_france_value_added_tax_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_france_value_added_tax_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_france_value_added_tax_number znajduje zawartość zgodną ze wzorcem.

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
- numer vat
- Podatku vat #
- podatek od wartości dodanej
- identyfikacja syreny bez numéro d'identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification syrena

## <a name="generic-medication-names"></a>Nazwy leków ogólnych

Ta uwolniona nazwana jednostka wykrywa nazwy leków ogólnych, takich jak *acetaminophen*. Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="germany-drivers-license-number"></a>Numer niemieckiego prawa jazdy

Ta jednostka typu informacji poufnych jest uwzględniana w typie informacji poufnych numer licencji kierowcy UE. Jest również dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie

kombinacja 11 cyfr i liter

### <a name="pattern"></a>Wzór

11 cyfr i liter (bez uwzględniania wielkości liter):

- cyfra lub litera
- dwie cyfry
- sześć cyfr lub liter
- cyfra
- cyfra lub litera

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_german_drivers_license znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_german_drivers_license_number.
- Suma kontrolna przechodzi.

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
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dlno

## <a name="germany-identity-card-number"></a>Numer niemieckiego numeru karty tożsamości

### <a name="format"></a>Formacie

od 1 listopada 2010 r.: od dziewięciu do 11 liter i cyfr

od 1 kwietnia 1987 r. do 31 października 2010 r.: 10 cyfr

### <a name="pattern"></a>Wzór

od 1 listopada 2010 r.: od 9 do 11 znaków wzorzec alfanumeryczny
- jeden L, M, N, P, R, T, V, W, X, Y (bez uwzględniania wielkości liter)
- osiem cyfr lub liter w C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y i Z (bez uwzględniania wielkości liter)
- opcjonalna cyfra kontrolna
- Opcjonalne d/D

od dnia 1 kwietnia 1987 r. do dnia 31 października 2010 r.:

- 10 cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_german_id_card_with_check` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_germany_id_card`
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_germany_id_card` regularne znajduje zawartość zgodną ze wzorcem (9 znaków bez cyfry kontrolnej wystawionej przed 2010 r. lub 10 cyfr wzorzec wystawiony posy 2010).
- Znaleziono słowo kluczowe z Keyword_germany_id_card.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_german_id_card_with_check` znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Identyfikacji
- identyfikator
- identifizierungsnummer
- Dowód tożsamości
- numer tożsamości
- id-nummer
- osobisty identyfikator
- personalausweis
- persönliche id nummer
- persönliche identifikationsnummer
- persönliche-id-nummer

## <a name="germany-passport-number"></a>Numer paszportu w Niemczech

### <a name="format"></a>Formacie

Od 9 do 11 znaków

### <a name="pattern"></a>Wzór

- jedna litera w C, F, G, H, J, K (bez uwzględniania wielkości liter)
- osiem cyfr lub liter w C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y i Z (bez uwzględniania wielkości liter)
- opcjonalna cyfra kontrolna
- Opcjonalne d/D

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_german_passport_checksum` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keyword_german_passport` `Keywords_eu_passport_number_common` .
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_german_passport` znajduje zawartość zgodną ze wzorcem dziewięciu znaków (bez cyfry wyboru i opcjonalnie d/D).
- Odnaleziono słowo kluczowe lub `Keyword_german_passport` `Keywords_eu_passport_number_common` .

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_german_passport_checksum` znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Numer dostępu
- reisepässe
- passeport no.
- passeport no

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

## <a name="germany-physical-addresses"></a>Adresy fizyczne w Niemczech

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Niemiec. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="germany-tax-identification-number"></a>Numer identyfikacji podatkowej w Niemczech

### <a name="format"></a>Formacie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

11 cyfr

- Dwie cyfry
- Opcjonalne miejsce
- Trzy cyfry
- Opcjonalne miejsce
- Trzy cyfry
- Opcjonalne miejsce
- Dwie cyfry
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_germany_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_germany_eu_tax_file_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_germany_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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
- identyfikator steuer
- steueridentifikationsnummer
- steuernummer
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- Zinn #
- Zinn
- zinnnummer

## <a name="germany-value-added-tax-number"></a>Numer podatku od wartości dodanej w Niemczech

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

11-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

11-znakowy wzorzec alfanumeryczny:

- litera D lub d
- litera E lub e
- opcjonalne miejsce
- trzy cyfry
- opcjonalne miejsce lub przecinek
- trzy cyfry
- opcjonalne miejsce lub przecinek
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_germany_value_added_tax_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_germany_value_added_tax_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_germany_value_added_tax_number znajduje zawartość zgodną ze wzorcem.

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
- numer vat
- Podatku vat #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer

## <a name="greece-drivers-license-number"></a>Numer prawa jazdy w Grecji

Ta jednostka jest uwzględniona w typie informacji poufnych numeru prawa jazdy UE. Jest również dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie

dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_greece_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_greece_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_greece_eu_drivers_license_number"></a>s_license_number Keywords_greece_eu_driver

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης

## <a name="greece-national-id-card"></a>Krajowa karta tożsamości Grecji

### <a name="format"></a>Formacie

Kombinacja 7-8 liter i cyfr plus kreska

### <a name="pattern"></a>Wzór

Siedem liter i cyfr (stary format):

- Jedna litera (dowolna litera alfabetu greckiego)
- Kreska
- Sześć cyfr

Osiem liter i cyfr (nowy format):

- Dwie litery, których wielkie litery występują zarówno w alfabecie greckim, jak i łacińskim (ABEZHIKMNOPTYX)
- Kreska
- Sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_greece_id_card znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_greece_id_card.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie regularne Regex_greece_id_card znajduje zawartość zgodną ze wzorcem.

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

- grecki identyfikator
- grecki identyfikator krajowy
- grecki osobisty identyfikator
- identyfikator policji greckiej
- Dowód tożsamości
- Tautotita
- Ταυτότητα
- ταυτότητας

## <a name="greece-passport-number"></a>Numer paszportu Grecji

### <a name="format"></a>Formacie

Dwie litery, po których następuje siedem cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

Dwie litery, po których następuje siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_greece_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_greece_eu_passport_number` .
- Wyrażenie `Regex_greece_eu_passport_date` regularne znajduje datę w formacie DD MMM RR (przykład — 28 sierpnia 19) lub znaleziono słowo kluczowe z `Keywords_greece_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_greece_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_greece_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο

## <a name="greece-physical-addresses"></a>Adresy fizyczne Grecji

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Grecji. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="greece-social-security-number-amka"></a>Numer ubezpieczenia społecznego w Grecji (AMKA)

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

- Sześć cyfr jako data urodzenia RRMMDD
- Cztery cyfry
- cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_greece_eu_ssn` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_greece_eu_ssn_or_equivalent`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_greece_eu_ssn` znajduje zawartość zgodną ze wzorcem.

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

- Ssn
- Ssn #
- zabezpieczenia społecznego nie
- socialsecurityno #
- numer ubezpieczenia społecznego
- Amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης

## <a name="greece-tax-identification-number"></a>Numer identyfikacji podatkowej Grecji

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

Dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_greece_eu_tax_file_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_greece_eu_tax_file_number`

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

- Afm #
- Afm
- aφμ|aφμ αριθμιι
- aφμ
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- rejestr podatkowy nie
- numer rejestru podatkowego
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- taxregistryno #
- identyfikator cyny
- nie cyny
- Tin #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο

## <a name="hong-kong-identity-card-hkid-number"></a>Numer karty tożsamości (HKID) w Hongkongu

### <a name="format"></a>Formacie

Kombinacja od 8 do 9 liter i cyfr oraz opcjonalnych nawiasów wokół znaku końcowego

### <a name="pattern"></a>Wzór

Kombinacja od 8 do 9 liter:

- 1–2 litery (bez uwzględniania wielkości liter)
- Sześć cyfr
- opcjonalne miejsce
- znak wyboru (dowolna cyfra lub litera A), który jest opcjonalnie ujęty w nawiasy

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_hong_kong_id_card znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_hong_kong_id_card.
- Suma kontrolna przechodzi.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_hong_kong_id_card znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- id card
- Dowód tożsamości
- hk identity card
- identyfikator hongkongu
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

## <a name="hungary-drivers-license-number"></a>Węgierski numer prawa jazdy

### <a name="format"></a>Formacie

Dwie litery, po których następuje sześć cyfr

### <a name="pattern"></a>Wzór

Dwie litery i sześć cyfr:

- Dwie litery (bez uwzględniania wielkości liter)
- Sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_hungary_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_hungary_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver s_license_number Keywords_hungary_eu_driver

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek

## <a name="hungary-passport-number"></a>Węgierski numer paszportu

### <a name="format"></a>Formacie

Dwie litery, po których następuje sześć lub siedem cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

Dwie litery, po których następuje sześć lub siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_hungary_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_hungary_eu_passport_number` .
- Wyrażenie `Regex_hungary_eu_passport_date` regularne znajduje datę w formacie DD MMM/MMM RR (przykład — 01 MÁR/MAR 12) lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_hungary_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_hungary_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="hungary-personal-identification-number"></a>Węgierski osobisty numer identyfikacyjny

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

11 cyfr

### <a name="pattern"></a>Wzór

11 cyfr:

- Jedna cyfra odpowiadająca płci, 1 dla mężczyzn, 2 dla kobiety. Inne liczby są również możliwe dla obywateli urodzonych przed 1900 r. lub obywateli z podwójnym obywatelstwem.
- Sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- Trzy cyfry odpowiadające numerowi seryjnemu
- Jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_hungary_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_hungary_eu_national_id_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_hungary_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.

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

- numer identyfikatora
- numer identyfikacyjny
- sz ig
- Sz. Ig.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány

## <a name="hungary-physical-addresses"></a>Adresy fizyczne Na Węgrzech

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Węgier. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="hungary-social-security-number-taj"></a>Węgierski numer ubezpieczenia społecznego (TAJ)

### <a name="format"></a>Formacie

Dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

Dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_hungary_eu_ssn_or_equivalent` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_hungary_eu_ssn_or_equivalent`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_hungary_eu_ssn_or_equivalent` znajduje zawartość zgodną ze wzorcem.

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

- węgierski numer ubezpieczenia społecznego
- numer ubezpieczenia społecznego
- socialsecuritynumber #
- hssn #
- socialsecuritynno
- hssn
- Taj
- Taj #
- Ssn
- Ssn #
- zabezpieczenia społecznego nie
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám

## <a name="hungary-tax-identification-number"></a>Węgierski numer identyfikacji podatkowej

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

10 cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

10 cyfr:

- Jedna cyfra, która musi mieć wartość "8"
- Osiem cyfr
- Jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_hungary_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_hungary_eu_tax_file_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_hungary_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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
- węgierski cyna
- hungatiantin #
- organ podatkowy nie
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- numer VAT

## <a name="hungary-value-added-tax-number"></a>Węgierski numer podatku od wartości dodanej

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

10-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

10-znakowy wzorzec alfanumeryczny:

- dwie litery — HU lub hu
- opcjonalne miejsce
- osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_hungarian_value_added_tax_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_hungarian_value_added_tax_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_hungarian_value_added_tax_number znajduje zawartość zgodną ze wzorcem.

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

- Podatku vat
- numer podatku od wartości dodanej
- Podatku vat #
- vatno #
- hungarianvatno #
- numer podatkowy.
- podatek od wartości dodanej áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám

## <a name="iceland-physical-addresses"></a>Adresy fizyczne Islandii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Islandii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>Upośledzenia wymienione w ocenie niepełnosprawności w USA w ramach zabezpieczenia społecznego

Ta uwolniona nazwana jednostka wykrywa nazwy upośledzenia wymienione w amerykańskiej ocenie niepełnosprawności w ramach ubezpieczenia społecznego, takie jak *dystrofia mięśniowa*. Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="india-drivers-license-number"></a>Numer prawa jazdy w Indiach

### <a name="format"></a>Formacie

15-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

15 liter lub cyfr:

- dwie litery wskazujące kod stanu
- opcjonalne miejsce lub kreska
- dwie cyfry wskazujące kod miasta
- opcjonalne miejsce lub kreska
- cztery cyfry wskazujące rok problemu
- opcjonalne miejsce lub kreska
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_india_driving_license` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_eu_driver's_license_number_common`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_india_driving_license` regularne znajduje zawartość zgodną ze wzorcem.

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

#### <a name="keywords_eu_drivers_license_number_common"></a>s_license_number_common Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

## <a name="india-gst-number"></a>Numer GST w Indiach

### <a name="format"></a>Formacie

15-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

15 liter lub cyfr:

- dwie cyfry reprezentujące prawidłowy kod stanu
- opcjonalne miejsce lub kreska
- dziesięć znaków reprezentujących stały numer konta (PAN)
- jedna litera lub cyfra
- opcjonalne miejsce lub kreska
- jedna litera "z" lub "Z"
- opcjonalne miejsce lub kreska
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_india_gst_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_india_gst_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_india_gst_number` znajduje zawartość zgodną ze wzorcem.

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

- Gst
- gstin
- podatek od towarów i usług
- podatek od towarów i usług

## <a name="india-permanent-account-number-pan"></a>Numer konta stałego w Indiach (PAN)

### <a name="format"></a>Formacie

10 liter lub cyfr

### <a name="pattern"></a>Wzór

10 liter lub cyfr:

- Trzy litery (bez uwzględniania wielkości liter)
- Litera w C, P, H, F, A, T, B, L, J, G (bez uwzględniania wielkości liter)
- Litera
- Cztery cyfry
- Litera, która jest alfabetyczną cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_india_permanent_account_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_india_permanent_account_number.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie regularne Regex_india_permanent_account_number znajduje zawartość zgodną ze wzorcem.

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

- Numer konta stałego
- PAN

## <a name="india-unique-identification-aadhaar-number"></a>Unikatowy numer identyfikacyjny Indii (Aadhaar)

### <a name="format"></a>Formacie

12 cyfr zawierających opcjonalne spacje lub kreski

### <a name="pattern"></a>Wzór

12 cyfr:

- Cyfra, która nie jest 0 lub 1
- Trzy cyfry
- Opcjonalne miejsce lub kreska
- Cztery cyfry
- Opcjonalne miejsce lub kreska
- Cyfra końcowa, która jest cyfrą kontrolną

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_india_aadhaar znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_india_aadhar.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_india_aadhaar znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Uid
- आधार
- uidai

## <a name="india-voter-id-card"></a>India Voter Id Card

### <a name="format"></a>Formacie

10-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

10 liter lub cyfr:

- trzy litery
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_india_voter_id_card` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_india_voter_id_card`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie `Regex_india_voter_id_card` regularne znajduje zawartość zgodną ze wzorcem.

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

- Wyborców
- voterid
- karta wyborców
- karta voteridcard
- dowód tożsamości ze zdjęciem wyborczym
- EPIC
- INE
- przemieszczenia wyborcze

## <a name="indonesia-identity-card-ktp-number"></a>Numer karty tożsamości Indonezji (KTP)

### <a name="format"></a>Formacie

16 cyfr zawierających opcjonalne kropki

### <a name="pattern"></a>Wzór

16 cyfr:

- Dwucyfrowy kod prowincji
- Okres (opcjonalnie)
- Rejestr dwucyfrowy lub kod miasta
- Dwucyfrowy kod podokrężny
- Okres (opcjonalnie)
- Sześć cyfr w formacie DDMMYY, które są datą urodzenia
- Okres (opcjonalnie)
- Cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_indonesia_id_card znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_indonesia_id_card.

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

## <a name="international-banking-account-number-iban"></a>Numer międzynarodowego konta bankowego (IBAN)

### <a name="format"></a>Formacie

Kod kraju (dwie litery) plus cyfry kontrolne (dwie cyfry) oraz numer bban (do 30 znaków)

### <a name="pattern"></a>Wzór

Wzorzec musi zawierać wszystkie następujące elementy:

- Dwuliterowy kod kraju
- Dwie cyfry kontrolne (po których następuje opcjonalne spacja)
- Od 1 do 7 grup po cztery litery lub cyfry (mogą być oddzielone spacjami)
- 1–3 litery lub cyfry

Format dla każdego kraju jest nieco inny. Typ informacji poufnych IBAN obejmuje następujące 60 krajów:

- Ad
- Ae
- Al
- O
- Az
- Ba
- Bve
- Bg
- Bh
- Ch
- Cr
- Cy
- Cz
- De
- Dk
- Zrobić
- Ee
- Es
- Fi
- Fo
- O
- Gb
- Ge
- Gi
- Gl
- Gr
- Hr
- Hu
- Ie
- Il
- Jest
- to
- Kw
- Kz
- Funtów
- Li
- Por
- Lu
- Lv
- Mc
- Md
- Me
- Mk
- Pan
- Mt
- mu
- Nl
- Nr
- Pl
- Pt
- Ro
- rs
- Sa
- Se
- Si
- Sk
- Sm
- Tn
- Tr
- Vg

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_iban znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

Brak

## <a name="international-classification-of-diseases-icd-10-cm"></a>Międzynarodowa klasyfikacja chorób (ICD-10-CM)

### <a name="format"></a>Formacie

Słownik

### <a name="pattern"></a>Wzór

Słowa kluczowego

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Znaleziono słowo kluczowe z Dictionary_icd_10_updated.
- Znaleziono słowo kluczowe z Dictionary_icd_10_codes.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Znaleziono słowo kluczowe z Dictionary_icd_10_ zaktualizowane.

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

Dowolny termin ze słownika słów kluczowych Dictionary_icd_10_updated, który jest oparty na [międzynarodowej klasyfikacji chorób, dziesiątej poprawce, modyfikacji klinicznej (ICD-10-CM)](https://icd10cmtool.cdc.gov/). Ten typ szuka tylko terminu, a nie kodów ubezpieczeniowych.

Dowolny termin ze słownika słów kluczowych Dictionary_icd_10_codes, który jest oparty na [międzynarodowej klasyfikacji chorób, dziesiątej poprawce, modyfikacji klinicznej (ICD-10-CM)](https://icd10cmtool.cdc.gov/). Ten typ szuka tylko kodów ubezpieczeniowych, a nie opisu.

## <a name="international-classification-of-diseases-icd-9-cm"></a>Międzynarodowa klasyfikacja chorób (ICD-9-CM)

### <a name="format"></a>Formacie

Słownik

### <a name="pattern"></a>Wzór

Słowa kluczowego

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Znaleziono słowo kluczowe z Dictionary_icd_9_updated.
- Znaleziono słowo kluczowe z Dictionary_icd_9_codes.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Znaleziono słowo kluczowe z Dictionary_icd_9_updated.

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

Dowolny termin ze słownika słów kluczowych Dictionary_icd_9_updated, który jest oparty na [Międzynarodowej Klasyfikacji Chorób, Dziewiąta poprawka, Modyfikacja kliniczna (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Ten typ szuka tylko terminu, a nie kodów ubezpieczeniowych.

Dowolny termin ze słownika słów kluczowych Dictionary_icd_9_codes, który jest oparty na [Międzynarodowej Klasyfikacji Chorób, Dziewiąta poprawka, Modyfikacja kliniczna (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Ten typ szuka tylko kodów ubezpieczeniowych, a nie opisu.

## <a name="ip-address"></a>Adres IP

### <a name="format"></a>Formacie

#### <a name="ipv4"></a>IPv4:
Złożony wzorzec, który uwzględnia sformatowane (okresy) i niesformatowane (bez kropki) wersje adresów IPv4

#### <a name="ipv6"></a>IPv6:
Złożony wzorzec, który uwzględnia sformatowane liczby IPv6 (które obejmują dwukropki)

### <a name="pattern"></a>Wzór

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

W przypadku protokołu IPv6 zasady DLP mają dużą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie regularne Regex_ipv6_address znajduje zawartość zgodną ze wzorcem.
- Nie znaleziono słowa kluczowego z Keyword_ipaddress.

W przypadku protokołu IPv4 zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_ipv4_address znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_ipaddress.

W przypadku protokołu IPv6 zasady DLP mają dużą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie regularne Regex_ipv6_address znajduje zawartość zgodną ze wzorcem.
- Nie znaleziono słowa kluczowego z Keyword_ipaddress.

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

- Adres IP (to słowo kluczowe uwzględnia wielkość liter)
- adres IP
- adresy IP
- protokół internetowy
- IP-כתובת ה

## <a name="ip-address-v4"></a>Adres IP w wersji 4

### <a name="format"></a>Formacie

Złożony wzorzec, który uwzględnia sformatowane (okresy) i niesformatowane (bez kropki) wersje adresów IPv4

### <a name="pattern"></a>Wzór

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_ipv4_address` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_ipaddress`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_ipv4_address` regularne znajduje zawartość zgodną ze wzorcem.

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

- Adres IP (uwzględnia wielkość liter)
- adres IP
- adresy IP
- protokół internetowy
- IP-כתובת ה

## <a name="ip-address-v6"></a>Adres IP w wersji 6

### <a name="format"></a>Formacie

Złożony wzorzec, który uwzględnia sformatowane liczby IPv6 (które obejmują dwukropki)

### <a name="pattern"></a>Wzór

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_ipv6_address` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_ipaddress`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_ipv6_address` regularne znajduje zawartość zgodną ze wzorcem.

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

- Adres IP (uwzględnia wielkość liter)
- adres IP
- adresy IP
- protokół internetowy
- IP-כתובת ה

## <a name="ireland-drivers-license-number"></a>Numer prawa jazdy w Irlandii

### <a name="format"></a>Formacie

Sześć cyfr, po których następuje cztery litery

### <a name="pattern"></a>Wzór

Sześć cyfr i cztery litery:

- Sześć cyfr
- Cztery litery (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_ireland_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_ireland_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_ireland_eu_drivers_license_number"></a>s_license_number Keywords_ireland_eu_driver

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>Numer paszportu Irlandii

### <a name="format"></a>Formacie

Dwie litery lub cyfry, po których następuje siedem cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

Dwie litery lub cyfry, po których następuje siedem cyfr:

- Dwie cyfry lub litery (bez uwzględniania wielkości liter)
- Siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_ireland_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_ireland_eu_passport_number` .
- Wyrażenie `Regex_ireland_eu_passport_date` regularne znajduje datę w formacie DD MMM/MMM RRRR (przykład - 01 BEA/MAY 1988) lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_ireland_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_ireland_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha pasanna
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cárta
- uimhir chárta

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="ireland-personal-public-service-pps-number"></a>Numer służby publicznej (PPS) w Irlandii

### <a name="format"></a>Formacie

Stary format (do 31 grudnia 2012 r.):

- siedem cyfr, po których następuje od 1 do 2 liter

Nowy format (1 stycznia 2013 r. i później):

- siedem cyfr, po których następuje dwie litery

### <a name="pattern"></a>Wzór

Stary format (do 31 grudnia 2012 r.):

- siedem cyfr
- od jednej do dwóch liter (bez uwzględniania wielkości liter)

Nowy format (1 stycznia 2013 r. i później):

- siedem cyfr
- litera (bez uwzględniania wielkości liter), która jest alfabetyczną cyfrą kontrolną
- Opcjonalna litera w zakresie A-I lub "W"

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_ireland_pps znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_ireland_eu_national_id_card.
- Suma kontrolna przechodzi.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_ireland_pps znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- osobisty numer identyfikatora
- osobisty numer usługi publicznej
- usługa osobista nie
- phearsanta seirbhíse poiblí
- pps nie
- numer pps
- pps num
- pps service no
- ppsn
- ppsno #
- ppsno
- Psp
- brak usługi publicznej
- publicserviceno #
- publicserviceno
- przychód i numer ubezpieczenia społecznego
- rsi no
- numer rsi
- rsin
- seirbhís aitheantais, klient
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="ireland-physical-addresses"></a>Adresy fizyczne Irlandii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Irlandii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="israel-bank-account-number"></a>Numer konta bankowego Izraela

### <a name="format"></a>Formacie

13 cyfr

### <a name="pattern"></a>Wzór

Sformatowany:

- dwie cyfry
- kreska
- trzy cyfry
- kreska
- osiem cyfr

Niesformatowany:

- 13 kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_israel_bank_account_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_israel_bank_account_number.

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

## <a name="israel-national-identification-number"></a>Narodowy numer identyfikacyjny Izraela

### <a name="format"></a>Formacie

dziewięć cyfr

### <a name="pattern"></a>Wzór

dziewięć kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_israeli_national_id_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Israel_National_ID.
- Suma kontrolna przechodzi.

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

- מספר זהות
- מספר זיה וי
- מספר זיהוי ישר אלי
- זהותישר אלית
- هو ية اسرائيل ية عدد
- هوية إسرائ يلية
- رقم الهوية
- عدد هوية فريدة من نوعها
- idnumber #
- numer identyfikatora
- brak tożsamości
- identitynumber #
- numer tożsamości
- israeliidentitynumber
- osobisty identyfikator
- unikatowy identyfikator

## <a name="italy-drivers-license-number"></a>Numer prawa jazdy Włoch

Jednostka tego typu jest uwzględniana w typie informacji poufnych Numer prawa jazdy UE. Jest również dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie

kombinacja 10 liter i cyfr

### <a name="pattern"></a>Wzór

kombinacja 10 liter i cyfr:

- jedna litera (bez uwzględniania wielkości liter)
- litera "A" lub "V" (bez uwzględniania wielkości liter)
- siedem cyfr
- jedna litera (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_italy_drivers_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keyword_italy_drivers_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- numero di patente
- patente di guida
- patente guida
- patenti di guida
- patenti guida

## <a name="italy-fiscal-code"></a>Włoski kod fiskalny
Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

16-znakowa kombinacja liter i cyfr w określonym wzorcu

### <a name="pattern"></a>Wzór

16-znakowa kombinacja liter i cyfr:

- trzy litery, które odpowiadają trzem pierwszym spedycjom w imieniu rodziny
- trzy litery, które odpowiadają pierwszym, trzecim i czwartym spedyantom w imieniu
- dwie cyfry odpowiadające ostatnim cyfrom roku urodzenia
- jedna litera odpowiadająca literze w miesiącu urodzenia — litery są używane w kolejności alfabetycznej, ale używane są tylko litery od A do E, H, L, M, P, R do T (tak więc styczeń to A, a październik to R)
- dwie cyfry odpowiadające dniu miesiąca urodzenia w celu rozróżnienia płci, 40 jest dodawane do dnia urodzenia dla kobiet
- cztery cyfry odpowiadające kodowi obszaru specyficznemu dla gminy, w której dana osoba urodziła się (kody dla całego kraju są używane w innych krajach)
- jedna cyfra parity

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_italy_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_italy_eu_national_id_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_italy_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.

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
- kod fiskalny
- numero certificato personale
- numero di identificazione fiscale
- numero id personale
- numero personale
- osobisty numer certyfikatu
- kod osobisty
- osobisty kod identyfikatora
- osobisty numer identyfikatora
- personalcodeno #
- kod podatkowy
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer tożsamości podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="italy-passport-number"></a>Numer paszportu Włochy

### <a name="format"></a>Formacie

dwie litery lub cyfry, po których następuje siedem cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

dwie litery lub cyfry, po których następuje siedem cyfr:

- dwie cyfry lub litery (bez uwzględniania wielkości liter)
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_italy_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_italy_eu_passport_number` .
- Wyrażenie `Regex_italy_eu_passport_date` regularne znajduje datę w formacie DD MMM/MMM RRRR (przykład — 01 GEN/JAN 1988) lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_italy_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_italy_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
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

- data wydania
- data wygaśnięcia

## <a name="italy-physical-addresses"></a>Adresy fizyczne Włoch

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Włoch. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="italy-value-added-tax-number"></a>Numer podatku od wartości dodanej we Włoszech

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

13-znakowy wzorzec alfanumeryczny z opcjonalnymi ogranicznikami

### <a name="pattern"></a>Wzór

13-znakowy wzorzec alfanumeryczny z opcjonalnymi ogranicznikami:

- Ja lub i
- T lub t
- opcjonalne spacja, kropka, łącznik lub przecinek
- 11 cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_italy_value_added_tax_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_italy_value_added_tax_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_italy_value_added_tax_number znajduje zawartość zgodną ze wzorcem.

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
- numer vat
- Podatku vat #
- Iva
- Iva #

## <a name="japan-bank-account-number"></a>Numer konta bankowego w Japonii

### <a name="format"></a>Formacie

siedem lub osiem cyfr

### <a name="pattern"></a>Wzór

numer konta bankowego:

- siedem lub osiem cyfr
- kod oddziału konta bankowego:

- cztery cyfry
- spacja lub kreska (opcjonalnie)
- trzy cyfry

Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_jp_bank_account znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_bank_account.
- Jedno z następujących elementów jest prawdziwe:

- Funkcja Func_jp_bank_account_branch_code znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_bank_branch_code.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_jp_bank_account znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_bank_account.

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
- Sprawdzanie numeru akcesu
- Sprawdzanie dostępu #
- Sprawdzanie nr dostępu
- Sprawdzanie nr konta
- Numer konta bankowego
- Konto bankowe
- Konto bankowe #
- Numer akcesu bankowego
- Bank Acct #
- Bank Acct Nr.
- Nr konta bankowego
- Numer konta oszczędnościowego
- Konto oszczędnościowe
- Konto oszczędnościowe #
- Numer akcesu oszczędności
- Oszczędności acct #
- Nr dostępu oszczędnościowego
- Nr konta oszczędnościowego
- Numer konta debetowego
- Konto debetowe
- Konto debetowe #
- Numer akcesu debetowego
- Akces debetowy #
- Numer akcesu debetowego
- Numer konta debetowego
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

## <a name="japan-drivers-license-number"></a>Numer japońskiego prawa jazdy

### <a name="format"></a>Formacie

12 cyfr

### <a name="pattern"></a>Wzór

12 kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_jp_drivers_license_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_drivers_license_number.

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
- Dl #
- Dls #
- Lic #
- lics #
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

## <a name="japan-my-number---corporate"></a>Japonia Mój numer — firmowy

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

13-cyfrowy numer

### <a name="pattern"></a>Wzór

13-cyfrowy numer:

- jedna cyfra od jednej do dziewięciu
- 12 cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_japanese_my_number_corporate znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_japanese_my_number_corporate.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_japanese_my_number_corporate znajduje zawartość zgodną ze wzorcem.

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

## <a name="japan-my-number---personal"></a>Japonia Mój numer - Osobisty

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

12-cyfrowy numer

### <a name="pattern"></a>Wzór

12-cyfrowy numer:

- cztery cyfry
- opcjonalne spacja, kropka lub łącznik
- cztery cyfry
- opcjonalne spacja, kropka lub łącznik
- cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_japanese_my_number_personal znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_japanese_my_number_personal.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_japanese_my_number_personal znajduje zawartość zgodną ze wzorcem.

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

### <a name="format"></a>Formacie

dwie litery, po których następuje siedem cyfr

### <a name="pattern"></a>Wzór

dwie litery (bez uwzględniania wielkości liter), po których następuje siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_jp_passport znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_passport.

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
- Nr paszportu
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

## <a name="japan-residence-card-number"></a>Numer karty pobytu w Japonii

### <a name="format"></a>Formacie

12 liter i cyfr

### <a name="pattern"></a>Wzór

12 liter i cyfr:

- dwie litery (bez uwzględniania wielkości liter)
- osiem cyfr
- dwie litery (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_jp_residence_card_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_residence_card_number.

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

- Numer karty pobytu
- Karta rezydencji nie
- Karta rezydencji #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Numer rejestracyjny rezydenta Japonii

### <a name="format"></a>Formacie

11 cyfr

### <a name="pattern"></a>Wzór

11 kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_jp_resident_registration_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_resident_registration_number.

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

- Numer rejestracji rezydenta
- Podstawowy numer rejestru rezydentów
- Numer rejestracji rezydenta
- Numer rejestru rezydenta
- Liczba podstawowych rejestrów rezydentów
- Podstawowy numer rejestru rezydenta.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証

## <a name="japan-social-insurance-number-sin"></a>Japoński numer ubezpieczenia społecznego (SIN)

### <a name="format"></a>Formacie

7–12 cyfr

### <a name="pattern"></a>Wzór

7–12 cyfr:

- cztery cyfry
- łącznik (opcjonalnie)
- sześć cyfr OR
- 7–12 kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_jp_sin znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_sin.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_jp_sin_pre_1997 znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_jp_sin.

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
- Numer ubezpieczenia społecznego
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

## <a name="lab-test-terms"></a>Terminy testowe laboratorium

Ta uwolniona nazwana jednostka wykrywa terminy związane z testami laboratoryjnymi, takimi jak *insulina C-peptyd*. Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="latvia-drivers-license-number"></a>Numer prawa jazdy łotwy

### <a name="format"></a>Formacie

trzy litery, po których następuje sześć cyfr

### <a name="pattern"></a>Wzór

trzy litery i sześć cyfr:

- trzy litery (bez uwzględniania wielkości liter)
- sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_latvia_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_latvia_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_latvia_eu_drivers_license_number"></a>s_license_number Keywords_latvia_eu_driver

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība

## <a name="latvia-passport-number"></a>Numer paszportu łotwy

### <a name="format"></a>Formacie

dwie litery lub cyfry, po których następuje siedem cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

dwie litery lub cyfry, po których następuje siedem cyfr:

- dwie cyfry lub litery (bez uwzględniania wielkości liter)
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_latvia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_latvia_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_latvia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_latvia_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase numurs
- pase numur
- pases numuri
- pases nr
- passeport no
- n° du Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="latvia-personal-code"></a>Kod osobisty Łotwy

### <a name="format"></a>Formacie

11 cyfr i opcjonalny łącznik

### <a name="pattern"></a>Wzór

Stary format

11 cyfr i łącznik:

- sześć cyfr odpowiadających dacie urodzenia (DDMMYY)
- łącznik
- jedna cyfra odpowiadająca stuleciu urodzenia ("0" dla XIX wieku, "1" dla XX wieku i "2" dla XXI wieku)
- cztery cyfry wygenerowane losowo

Nowy format

11 cyfr

- Dwie cyfry "32"
- Dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_latvia_eu_national_id_card` lub rejestr `Regex_latvia_eu_national_id_card_new_format` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_latvia_eu_national_id_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_latvia_eu_national_id_card` lub rejestr `Regex_latvia_eu_national_id_card_new_format` znajduje zawartość zgodną ze wzorcem.

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
- alvas nē
- numer urodzenia
- numer obywatela
- numer cywilny
- elektroniczny numer spisu
- numer elektroniczny
- kod fiskalny
- numer użytkownika opieki zdrowotnej
- Identyfikator #
- id-code
- numer identyfikacyjny
- identifikācijas numurs
- id-number
- numer indywidualny
- latvija alva
- nacionālais id
- identyfikator krajowy
- krajowy numer identyfikacyjny
- krajowy numer tożsamości
- krajowy numer ubezpieczenia
- numer krajowego rejestru
- nodokļa numurs
- nodokļu id
- nodokļu identifikācija numurs
- osobisty numer certyfikatu
- kod osobisty
- osobisty kod identyfikatora
- osobisty numer identyfikatora
- osobisty kod identyfikacyjny
- identyfikator osobisty
- osobisty numer tożsamości
- numer osobisty
- osobisty kod liczbowy
- personalcodeno #
- personas kods
- kod identyfikacji populacji
- numer usługi publicznej
- numer rejestracji
- numer przychodu
- numer ubezpieczenia społecznego
- numer ubezpieczenia społecznego
- kod podatkowy stanu
- numer pliku podatkowego
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- numer wyborcy

## <a name="latvia-physical-addresses"></a>Adresy fizyczne Łotwy

Ta rozdzielona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Łotwy. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="liechtenstein-physical-addresses"></a>Adresy fizyczne Liechtensteinu

Ta rozdzielana nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Liechtensteinu. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="lifestyles-that-relate-to-medical-conditions"></a>Styl życia, który odnosi się do schorzeń

Ta uwolniona nazwana jednostka wykrywa terminy związane ze stylem życia, które mogą prowadzić do stanu zdrowia, takiego jak *palenie tytoniu*. Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="lithuania-drivers-license-number"></a>Litewski numer prawa jazdy

### <a name="format"></a>Formacie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_lithuania_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_lithuania_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_lithuania_eu_drivers_license_number"></a>s_license_number Keywords_lithuania_eu_driver

- vairuotojo pažymėjimas
- vairuotojo pažymėjimo numeris
- vairuotojo pažymėjimo numeriai

## <a name="lithuania-personal-code"></a>Litewski kod osobisty

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

11 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

11 cyfr bez spacji i ograniczników:

- jedna cyfra (1–6), która odpowiada płci i wieku urodzenia danej osoby
- sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- trzy cyfry odpowiadające numerowi seryjnemu daty urodzenia
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_lithuania_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_lithuania_eu_tax_file_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_lithuania_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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
- numer usługi obywatelskiej
- mokesčių id
- mokesčių identifikavimas numeris
- mokesčių identifikavimo numeris
- mokesčių numeris
- krajowy numer identyfikacyjny
- kod osobisty
- osobisty kod liczbowy
- piliečio paslaugos numeris
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #

## <a name="lithuania-physical-addresses"></a>Adresy fizyczne Litwy

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Litwy. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="lithuania-passport-number"></a>Numer paszportu litwy

### <a name="format"></a>Formacie

osiem cyfr lub liter bez spacji lub ograniczników

### <a name="pattern"></a>Wzór

osiem cyfr lub liter (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_lithuania_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_lithuania_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date3` regularne znajduje datę w formacie DD MM RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_lithuania_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_lithuania_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- paso numeris
- paso numeriai
- paso nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="luxemburg-drivers-license-number"></a>Numer prawa jazdy w Luksemburgu

### <a name="format"></a>Formacie

sześć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_luxemburg_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_luxemburg_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>s_license_number Keywords_luxemburg_eu_driver

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Luksemburski krajowy numer identyfikacyjny (osoby fizyczne)

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

13 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

13 cyfr:

- 11 cyfr
- dwie cyfry kontrolne

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_luxemburg_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_luxemburg_eu_national_id_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_luxemburg_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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

- eindeutige id
- eindeutige id-nummer
- eindeutigeid #
- id personnelle
- idpersonnelle #
- idpersonnelle
- indywidualny kod
- indywidualny identyfikator
- identyfikacja indywidualna
- indywidualna tożsamość
- numéro d'identification personnel
- osobisty identyfikator
- identyfikacja osobista
- tożsamość osobista
- personalidno #
- personalidnumber #
- persönliche identifikationsnummer
- unikatowy identyfikator
- unikatowa tożsamość
- uniqueidkey #

## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Luksemburski krajowy numer identyfikacyjny (osoby niebędące osobami fizycznymi)

### <a name="format"></a>Formacie

11 cyfr

### <a name="pattern"></a>Wzór

11 cyfr

- dwie cyfry
- opcjonalne miejsce
- trzy cyfry
- opcjonalne miejsce
- trzy cyfry
- opcjonalne miejsce
- dwie cyfry
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_luxemburg_eu_tax_file_number_non_natural` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_luxemburg_eu_tax_file_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_luxemburg_eu_tax_file_number_non_natural` znajduje zawartość zgodną ze wzorcem.

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
- luksemburski identyfikator podatkowykatiounsnummer
- numéro d'étain
- numéro d'identification fiscal luxembourgeois
- numéro d'identification fiscale
- zabezpieczenia społeczne
- sozialunterstützung
- sozialversécherung
- sozialversicherungsausweis
- identyfikator steier
- steier identifikatiounsnummer
- steier nummer
- identyfikator steuer
- steueridentifikationsnummer
- steuernummer
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- Zinn #
- Zinn
- zinnzahl

## <a name="luxemburg-passport-number"></a>Numer paszportu w Luksemburgu

### <a name="format"></a>Formacie

osiem cyfr lub liter bez spacji lub ograniczników

### <a name="pattern"></a>Wzór

osiem cyfr lub liter (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_luxemburg_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_luxemburg_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date3` regularne znajduje datę w formacie DD MM RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_luxemburg_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_luxemburg_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- luksemburski przełę
- luksemburski port passeport
- paszport luksemburski
- no de passeport
- no-reisepass
- nr-reisepass
- numéro de passeport
- pass net
- pass nr
- passnummer
- passeport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="luxemburg-physical-addresses"></a>Adresy fizyczne w Luksemburgu

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Luksemburga. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="malaysia-identification-card-number"></a>Numer karty identyfikacyjnej Malezji

### <a name="format"></a>Formacie

12 cyfr zawierających opcjonalne łączniki

### <a name="pattern"></a>Wzór

12 cyfr:

- sześć cyfr w formacie YYMMDD, które są datą urodzenia
- kreska (opcjonalnie)
- dwuliterowy kod miejsca urodzenia
- kreska (opcjonalnie)
- trzy cyfry losowe
- jednocyfrowy kod płci

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_malaysia_id_card_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_malaysia_id_card_number.

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
- i/c nie
- Ic
- ic no
- id card
- karta identyfikacyjna
- Dowód tożsamości
- k/p
- k/p nie
- kad akuan diri
- kad aplikasi digital
- kad pengenalan malezja
- Kp
- kp nie
- mykad
- mykas
- mykid
- mypr
- mytentera
- malaysia identity card
- malezyjski dowód tożsamości
- nric
- osobista karta identyfikacyjna

## <a name="malta-drivers-license-number"></a>Numer prawa jazdy Malty

### <a name="format"></a>Formacie

Kombinacja dwóch znaków i sześciu cyfr w określonym wzorcu

### <a name="pattern"></a>Wzór

kombinacja dwóch znaków i sześciu cyfr:

- dwa znaki (cyfry lub litery, bez uwzględniania wielkości liter)
- spację (opcjonalnie)
- trzy cyfry
- spację (opcjonalnie)
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_malta_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_malta_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_malta_eu_drivers_license_number"></a>s_license_number Keywords_malta_eu_driver

- liċenzja tas-sewqan
- liċenzji tas-sewwieq

## <a name="malta-identity-card-number"></a>Numer karty tożsamości Malty

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

siedem cyfr, po których następuje jedna litera

### <a name="pattern"></a>Wzór

siedem cyfr, po których następuje jedna litera:

- siedem cyfr
- jedna litera w "M, G, A, P, L, H, B, Z" (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_malta_eu_national_id_card` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_malta_eu_national_id_card`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Wyrażenie `Regex_malta_eu_national_id_card` regularne znajduje zawartość zgodną ze wzorcem.

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

- numer usługi obywatelskiej
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- osobisty kod liczbowy
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #

## <a name="malta-passport-number"></a>Numer paszportu Malta

### <a name="format"></a>Formacie

siedem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_malta_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_malta_eu_passport_number` .
- Znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_malta_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_malta_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="malta-physical-addresses"></a>Adresy fizyczne Malty

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Malty. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="malta-tax-identification-number"></a>Numer identyfikacji podatkowej Malty

### <a name="format"></a>Formacie

W przypadku obywateli Malty:

- siedem cyfr i jedna litera w określonym wzorcu

Obywatele spoza Malty i podmioty maltańskie:

- dziewięć cyfr

### <a name="pattern"></a>Wzór

Obywatele Malty: siedem cyfr i jedna litera

- siedem cyfr
- jedna litera (bez uwzględniania wielkości liter)

Obywatele spoza Malty i podmioty maltańskie: dziewięć cyfr

- dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- `Regex_malta_eu_tax_file_number` Rejestr lub `Regex_malta_eu_tax_file_number_non_maltese_national` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_malta_eu_tax_file_number`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- `Regex_malta_eu_tax_file_number` Rejestr lub `Regex_malta_eu_tax_file_number_non_maltese_national` znajduje zawartość zgodną ze wzorcem.

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

- numer usługi obywatelskiej
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- osobisty kod liczbowy
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #

## <a name="medical-specialities"></a>Specjalności medyczne

Ta uwolniona nazwana jednostka wykrywa terminy związane ze specjalnościami medycznymi, takimi jak *dermatologia*.  Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="medicare-beneficiary-identifier-mbi-card"></a>Karta identyfikatora beneficjenta medicare (MBI)

### <a name="format"></a>Formacie

11-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

- jedna cyfra z zakresu od 1 do 9
- jedna litera z wyłączeniem S, L, O, I, B, Z
- jedna cyfra lub litera z wyjątkiem S, L, O, I, B, Z
- jedna cyfra
- opcjonalny łącznik
- jedna litera z wyłączeniem S, L, O, I, B, Z
- jedna cyfra lub litera z wyjątkiem S, L, O, I, B, Z
- jedna cyfra
- opcjonalny łącznik
- dwie litery z wyjątkiem S, L, O, I, B, Z
- dwie cyfry

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_mbi_card` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_mbi_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_mbi_card` regularne znajduje zawartość zgodną ze wzorcem.

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

- Mbi
- Mbi #
- beneficjent medicare #
- identyfikator beneficjenta medicare
- beneficjenta medicare nie
- numer beneficjenta medicare
- beneficjent medicare #

## <a name="mexico-unique-population-registry-code-curp"></a>Meksyk Unikatowy kod rejestru populacji (CURP)

### <a name="format"></a>Formacie

18-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

- cztery litery (bez uwzględniania wielkości liter)
- sześć cyfr wskazujących prawidłową datę
- litera - H/h lub M/m
- dwie litery wskazujące prawidłowy meksykański kod stanu
- trzy litery
- jedna litera lub cyfra
- jedna cyfra

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_mexico_population_registry_code` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_mexico_population_registry_code`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_mexico_population_registry_code` znajduje zawartość zgodną ze wzorcem.

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
- personalidnumber
- uniqueidkey
- uniqueidnumber
- clave única
- clave unica
- clave osobiste Identidad
- osobisty Identidad Clave
- ClaveÚnica
- claveunica
- clavepersonalIdentidad

## <a name="netherlands-citizens-service-bsn-number"></a>Numer usługi obywatela Holandii (BSN)

### <a name="format"></a>Formacie

osiem lub dziewięć cyfr zawierających opcjonalne spacje

### <a name="pattern"></a>Wzór

osiem-dziewięć cyfr:

- trzy cyfry
- spację (opcjonalnie)
- trzy cyfry
- spację (opcjonalnie)
- dwie-trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_netherlands_bsn znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_netherlands_bsn.
- Suma kontrolna przechodzi.

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

- Bsn #
- Bsn
- burgerservicenummer
- numer usługi obywatelskiej
- numer osoby
- numer osobisty
- osobisty kod liczbowy
- numer związany z osobą
- persoonlijk nummer
- persoonlijke numerieke code
- persoonsgebonden
- persoonsnummer
- nummer sociaal-fiscaal
- numer społeczno-fiskalny
- Sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #

## <a name="netherlands-drivers-license-number"></a>Holenderski numer prawa jazdy

### <a name="format"></a>Formacie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

10 cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_netherlands_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_netherlands_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_netherlands_eu_drivers_license_number"></a>s_license_number Keywords_netherlands_eu_driver

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers

## <a name="netherlands-passport-number"></a>Numer paszportu holandii

### <a name="format"></a>Formacie

dziewięć liter lub cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

dziewięć liter lub cyfr

### <a name="checksum"></a>Suma kontrolna

nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_netherlands_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_netherlands_eu_passport_number` .
- Wyrażenie `Regex_netherlands_eu_passport_date` regularne znajduje datę w formacie DD MMM/MMM RRRR (przykład — 26 MAA/MAR 2012)

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_netherlands_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_netherlands_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- paspoort nummer
- paspoortnummers
- paspoortnummer
- paspoort nr

## <a name="netherlands-physical-addresses"></a>Holenderskie adresy fizyczne

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Holandii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="netherlands-tax-identification-number"></a>Holenderski numer identyfikacji podatkowej

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_netherlands_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_netherlands_eu_tax_file_number`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_netherlands_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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
- hollânske identyfikacji podatkowej
- hulandes impuesto id number
- hulandes impuesto identification
- identificatienummer belasting
- identificatienummer van belasting
- numer identyfikacyjny impuesto
- numer impuesto
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- identyfikacja podatkowa w Holandii
- identyfikacji podatkowej netherlandu
- holenderski cyna
- cyna netherland
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- identyfikacja podatkowa
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- tax tal
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="netherlands-value-added-tax-number"></a>Holenderski numer podatku od wartości dodanej

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

14-znakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

14-znakowy wzorzec alfanumeryczny:

- N lub n
- L lub l
- opcjonalne spacja, kropka lub łącznik
- dziewięć cyfr
- opcjonalne spacja, kropka lub łącznik
- B lub b
- dwie cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_netherlands_value_added_tax_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_netherlands_value_added_tax_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_netherlands_value_added_tax_number znajduje zawartość zgodną ze wzorcem.

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
- numer vat
- Podatku vat #
- wearde tafoege podatku getal
- btw nûmer
- btw-nummer

## <a name="new-zealand-bank-account-number"></a>Numer konta bankowego Nowej Zelandii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

Wzorzec od 14 do 16 cyfr z opcjonalnym ogranicznikiem

### <a name="pattern"></a>Wzór

Wzorzec od 14 do 16 cyfr z opcjonalnym ogranicznikiem:

- dwie cyfry
- opcjonalny łącznik lub spacja
- od trzech do czterech cyfr
- opcjonalny łącznik lub spacja
- siedem cyfr
- opcjonalny łącznik lub spacja
- od dwóch do trzech cyfr
- opcje łącznika lub spacji

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_new_zealand_bank_account_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_new_zealand_bank_account_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_new_zealand_bank_account_number znajduje zawartość zgodną ze wzorcem.

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

## <a name="new-zealand-drivers-license-number"></a>Numer prawa jazdy w Nowej Zelandii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

wzorzec alfanumeryczny z ośmioma znakami

### <a name="pattern"></a>Wzór

wzorzec alfanumeryczny z ośmioma znakami

- dwie litery
- sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_newzealand_driver_license_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_newzealand_driver_license_number.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_newzealand_driver_license_number znajduje zawartość zgodną ze wzorcem.

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
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki lic
- lics sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- driverlic #
- driverlics #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- międzynarodowe prawo jazdy
- międzynarodowe zezwolenia na jazdę
- nz stowarzyszenie samochodów
- Nowa Zelandia Stowarzyszenie Samochodowe

## <a name="new-zealand-inland-revenue-number"></a>Numer przychodu w głębi lądu w Nowej Zelandii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

osiem lub dziewięć cyfr z opcjonalnymi ogranicznikami

### <a name="pattern"></a>Wzór

osiem lub dziewięć cyfr z opcjonalnymi ogranicznikami

- dwie lub trzy cyfry
- opcjonalne spacja lub łącznik
- trzy cyfry
- opcjonalne spacja lub łącznik
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_new_zealand_inland_revenue_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_new_zealand_inland_revenue_number.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_new_zealand_inland_revenue_number znajduje zawartość zgodną ze wzorcem.

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

- ird no.
- ird no #
- nz ird
- nowa Zelandia ird
- ird number (Numer ird)
- numer przychodu w głębi lądu

## <a name="new-zealand-ministry-of-health-number"></a>Numer ministerstwa zdrowia Nowej Zelandii

### <a name="format"></a>Formacie

trzy litery i cztery cyfry

### <a name="pattern"></a>Wzór

- trzy litery (bez uwzględniania wielkości liter) z wyjątkiem liter "I" i "O"
- cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_new_zealand_ministry_of_health_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_nz_terms.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_new_zealand_ministry_of_health_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Krajowy indeks kondycji
- NHI #
- Krajowy indeks kondycji #

## <a name="new-zealand-physical-addresses"></a>Adresy fizyczne Nowej Zelandii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Nowej Zelandii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="new-zealand-social-welfare-number"></a>Numer opieki społecznej w Nowej Zelandii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

dziewięć cyfr

### <a name="pattern"></a>Wzór

dziewięć cyfr

- trzy cyfry
- opcjonalny łącznik
- trzy cyfry
- opcjonalny łącznik
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_newzealand_social_welfare_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_newzealand_social_welfare_number.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_newzealand_social_welfare_number znajduje zawartość zgodną ze wzorcem.

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

- Opieki społecznej #
- Opieki społecznej #
- opieki społecznej nr.
- numer opieki społecznej
- swn #

## <a name="norway-identification-number"></a>Numer identyfikacyjny Norwegii

### <a name="format"></a>Formacie

11 cyfr

### <a name="pattern"></a>Wzór

11 cyfr:

- sześć cyfr w formacie DDMMYY, które są datą urodzenia
- trzycyfrowy numer indywidualny
- dwie cyfry kontrolne

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_norway_id_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_norway_id_number.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_norway_id_numbe znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- Norweski numer identyfikatora
- Numer identyfikatora
- Identyfikacji
- Liczba osób
- Fødselsnummer

## <a name="norway-physical-addresses"></a>Adresy fizyczne Norwegii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Norwegii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="philippines-unified-multi-purpose-identification-number"></a>Filipiny ujednolicony wielozadaniowy numer identyfikacyjny

### <a name="format"></a>Formacie

12 cyfr rozdzielonych łącznikami

### <a name="pattern"></a>Wzór

12 cyfr:

- cztery cyfry
- łącznik
- siedem cyfr
- łącznik
- jedna cyfra

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_philippines_unified_id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_philippines_id.

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
- Dowód tożsamości
- Pinag-isang Multi-Layunin ID

## <a name="poland-drivers-license-number"></a>Numer polskiego prawa jazdy

### <a name="format"></a>Formacie

14 cyfr zawierających dwa ukośniki do przodu

### <a name="pattern"></a>Wzór

14 cyfr i dwa ukośniki do przodu:

- pięć cyfr
- ukośnik do przodu
- dwie cyfry
- ukośnik do przodu
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_poland_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_poland_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_poland_eu_drivers_license_number"></a>s_license_number Keywords_poland_eu_driver

- prawo jazdy
- prawa jazdy

## <a name="poland-identity-card"></a>Polski dowód tożsamości

### <a name="format"></a>Formacie

trzy litery i sześć cyfr

### <a name="pattern"></a>Wzór

trzy litery (bez uwzględniania wielkości liter), po których następuje sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_polish_national_id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_polish_national_id_passport_number.
- Suma kontrolna przechodzi.

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
- Dow. Os.

## <a name="poland-national-id-pesel"></a>Polski identyfikator krajowy (PESEL)

### <a name="format"></a>Formacie

11 cyfr

### <a name="pattern"></a>Wzór

- sześć cyfr reprezentujących datę urodzenia w formacie RRMMD
- cztery cyfry
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_pesel_identification_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_pesel_identification_number.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_pesel_identification_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- liczba niepowtarzalna
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- numer identyfikacyjny
- Pesel
- tożsamości narodowej

## <a name="poland-passport-number"></a>Polski numer paszportu

Ta jednostka typu informacji poufnych jest uwzględniana w typie informacji poufnych numeru paszportu UE. Jest również dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie

dwie litery i siedem cyfr

### <a name="pattern"></a>Wzór

Dwie litery (bez uwzględniania wielkości liter), po których następuje siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_polish_passport_number_v2` znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keyword_polish_national_passport_number` .
- Odnaleziono słowo kluczowe.`Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_polish_passport_number_v2` znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keyword_polish_national_passport_number` .

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_polish_passport_number_v2` znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
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

- data wydania
- data wygaśnięcia

## <a name="poland-physical-addresses"></a>Adresy fizyczne w Polsce

Ta rozdzielona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Polski. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="poland-regon-number"></a>Numer REGON w Polsce

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

9-cyfrowy lub 14-cyfrowy numer

### <a name="pattern"></a>Wzór

dziewięciocyfrowy lub 14-cyfrowy numer:

- dziewięć cyfr lub
- dziewięć cyfr
- Łącznik
- pięć cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_polish_regon_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_polish_regon_number.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_polish_regon_number znajduje zawartość zgodną ze wzorcem.

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
- liczba statystyczna
- identyfikator statystyczny
- statystyczne nie
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

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

11 cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

11 cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_poland_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_poland_eu_tax_file_number`

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

- Nip #
- Nip
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- identyfikator vat #
- identyfikator vat
- numer vat
- numer VAT
- vatid #
- vatid
- vatno #

## <a name="portugal-citizen-card-number"></a>Numer karty obywatela Portugalii

### <a name="format"></a>Formacie

osiem cyfr

### <a name="pattern"></a>Wzór

osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_portugal_citizen_card znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_portugal_citizen_card.

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

- bilhete de identidade
- cartão de cidadão
- karta obywatela
- numer dokumentu
- documento de identificação
- numer identyfikatora
- brak identyfikacji
- numer identyfikacyjny
- brak karty tożsamości
- numer karty tożsamości
- dowód osobisty
- nic
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- portugal bi number

## <a name="portugal-drivers-license-number"></a>Numer prawa jazdy Portugalia

### <a name="format"></a>Formacie

dwa wzorce — dwie litery, po których następuje od 5 do 8 cyfr ze znakami specjalnymi

### <a name="pattern"></a>Wzór

Wzorzec 1: Dwie litery, po którym następuje 5/6 ze znakami specjalnymi:

- Dwie litery (bez uwzględniania wielkości liter)
- Łącznik
- Pięć lub sześć cyfr
- Przestrzeń
- Jedna cyfra

Wzorzec 2: jedna litera, po której następuje 6/8 cyfr ze znakami specjalnymi:

- Jedna litera (bez uwzględniania wielkości liter)
- Łącznik
- Sześć lub osiem cyfr
- Przestrzeń
- Jedna cyfra

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_portugal_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_portugal_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_portugal_eu_drivers_license_number"></a>s_license_number Keywords_portugal_eu_driver

- carteira de motorista
- carteira motorista
- carteira de habilitação
- carteira habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugalia
- carta de condução

## <a name="portugal-passport-number"></a>Numer paszportu Portugalii

### <a name="format"></a>Formacie

jedna litera, po której następuje sześć cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

jedna litera, po której następuje sześć cyfr:

- jedna litera (bez uwzględniania wielkości liter)
- sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_portugal_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_portugal_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_portugal_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_portugal_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do passaporte
- portugalski paszport
- portugalski passeport
- portugalski passaporte
- passaporte n°
- passeport n°
- números de passaporte
- portugalskie paszporty
- número passaporte
- números passaporte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="portugal-physical-addresses"></a>Adresy fizyczne Portugalii

Ta uwolniona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Portugalii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="portugal-tax-identification-number"></a>Numer identyfikacji podatkowej Portugalii

### <a name="format"></a>Formacie

dziewięć cyfr z opcjonalnymi spacjami

### <a name="pattern"></a>Wzór

- trzy cyfry
- opcjonalne miejsce
- trzy cyfry
- opcjonalne miejsce
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_portugal_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_portugal_eu_tax_file_number`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_portugal_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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

- Cpf #
- Cpf
- Nif #
- Nif
- número de identificação fisca
- numero fiscal
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="romania-drivers-license-number"></a>Numer prawa jazdy Rumunii

### <a name="format"></a>Formacie

jeden znak, po którym następuje osiem cyfr

### <a name="pattern"></a>Wzór

jeden znak, po którym następuje osiem cyfr:

- jedna litera (bez uwzględniania wielkości liter) lub cyfra
- osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_romania_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_romania_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_romania_eu_drivers_license_number"></a>s_license_number Keywords_romania_eu_driver

- permis de conducere
- permisului de conducere
- permisului conducere
- permisele de conducere
- permisele conducere
- permis conducere

## <a name="romania-passport-number"></a>Numer paszportu Rumunii

### <a name="format"></a>Formacie

osiem lub dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

osiem lub dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_romania_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_romania_eu_passport_number` .
- Wyrażenie `Regex_romania_eu_passport_date` regularne znajduje datę w formacie DD MMM/MMM RR (przykład- 01 FEB/FEB 10) lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_romania_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_romania_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numărul pașaportului numarul pasaportului numerele paşaportului Paşaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="romania-personal-numeric-code-cnp"></a>Rumunia osobisty kod liczbowy (CNP)

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

13 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

- jedna cyfra z zakresu od 1 do 9
- sześć cyfr reprezentujących datę urodzenia (RRMMDD)
- dwie cyfry, które mogą być 01-52 lub 99
- cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_romania_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_romania_eu_national_id_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_romania_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.

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

- Cnp #
- Cnp
- cod identificare personal
- cod numeric personal
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscală nr #
- id-ul taxei
- numer ubezpieczenia
- numer ubezpieczenia #
- identyfikator krajowy #
- identyfikator krajowy
- krajowy numer identyfikacyjny
- număr identificare personal
- număr identitate
- număr personal unic
- număridentitate #
- număridentitate
- numărpersonalunic #
- numărpersonalunic
- număru de identificare fiscală
- numărul de identificare fiscală
- osobisty kod liczbowy
- Pin #
- Pin
- plik podatkowy nie
- numer pliku podatkowego
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #
- unikatowy numer identyfikacyjny
- unikatowy numer tożsamości
- uniqueidentityno #
- uniqueidentityno

## <a name="romania-physical-addresses"></a>Adresy fizyczne Rumunii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Rumunii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="russia-passport-number-domestic"></a>Numer paszportu Rosji krajowy

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

10-cyfrowy numer

### <a name="pattern"></a>Wzór

10-cyfrowy numer:

- dwie cyfry
- opcjonalne spacja lub łącznik
- dwie cyfry
- opcjonalne miejsce
- sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Rejestr Regex_Russian_Passport_Number_Domestic znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Russian_Passport_Number.

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
- nr paszportu
- Paszport #
- identyfikator paszportu
- passportno #
- passportnumber #
- паспорт нет
- Identyfikator паспорт
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #

## <a name="russia-passport-number-international"></a>Numer paszportu Rosji międzynarodowy

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

liczba dziewięciocyfrowa

### <a name="pattern"></a>Wzór

liczba dziewięciocyfrowa:

- dwie cyfry
- opcjonalne spacja lub łącznik
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Rejestr Regex_Russian_Passport_Number_International znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Russian_Passport_Number.

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
- nr paszportu
- Paszport #
- identyfikator paszportu
- passportno #
- passportnumber #
- паспорт нет
- Identyfikator паспорт
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #

## <a name="saudi-arabia-national-id"></a>Identyfikator narodowy Arabii Saudyjskiej

### <a name="format"></a>Formacie

10 cyfr

### <a name="pattern"></a>Wzór

10 kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_saudi_arabia_national_id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_saudi_arabia_national_id.

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

- Karta identyfikacyjna
- Numer karty I
- Numer identyfikatora
- الوطنية الهوية بطاقة رقم

## <a name="singapore-national-registration-identity-card-nric-number"></a>Numer krajowego dowodu rejestracyjnego (NRIC) w Singapurze

### <a name="format"></a>Formacie

dziewięć liter i cyfr

### <a name="pattern"></a>Wzór

- dziewięć liter i cyfr:

- litery "F", "G", "M", "S" lub "T" (bez uwzględniania wielkości liter)
- siedem cyfr
- alfabetyczna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_singapore_nric znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_singapore_nric.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_singapore_nric znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- Krajowa karta rejestracyjna
- Numer karty tożsamości
- NRIC
- IC
- Numer identyfikacyjny obcy
- FIN
- 身份证
- 身份證

## <a name="slovakia-drivers-license-number"></a>Numer prawa jazdy słowacji

### <a name="format"></a>Formacie

jeden znak, po którym następuje siedem cyfr

### <a name="pattern"></a>Wzór

jeden znak, po którym następuje siedem cyfr

- jedna litera (bez uwzględniania wielkości liter) lub cyfra
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_slovakia_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_slovakia_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_slovakia_eu_drivers_license_number"></a>s_license_number Keywords_slovakia_eu_driver

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičských preukazov

## <a name="slovakia-passport-number"></a>Numer paszportu Słowacji

### <a name="format"></a>Formacie

wzorzec alfanumeryczny o ośmiu lub dziewięciu znakach

### <a name="pattern"></a>Wzór

jedna litera (bez uwzględniania wielkości liter), po której następuje siedem cyfr lub dwie litery (bez uwzględniania wielkości liter), po których następuje sześć lub siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_slovakia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_slovakia_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_slovakia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_slovakia_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- číslo pasu
- čísla pasov
- pas č.
- Passeport n°
- n° Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="slovakia-personal-number"></a>Numer osobisty Słowacji

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

dziewięć lub 10 cyfr zawierających opcjonalny ukośnik odwrotny

### <a name="pattern"></a>Wzór

- sześć cyfr reprezentujących datę urodzenia
- opcjonalny ukośnik (/)
- trzy cyfry
- jedna opcjonalna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_slovakia_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_slovakia_eu_national_id_card`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_slovakia_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.

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
- numer identyfikatora
- brak identyfikacji
- numer identyfikacyjny
- identifikačná karta č
- identifikačné číslo
- brak karty tożsamości
- numer karty tożsamości
- národná identifikačná značka č
- numer krajowy
- nationalnumber #
- nemzeti személyazonosító igazolvány
- personalidnumber #
- rč
- rodne cislo
- rodné číslo
- numer ubezpieczenia społecznego
- Ssn #
- Ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- plik podatkowy nie
- numer pliku podatkowego
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="slovakia-physical-addresses"></a>Adresy fizyczne Słowacji

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym ze Słowacji. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="slovenia-drivers-license-number"></a>Słoweński numer prawa jazdy

### <a name="format"></a>Formacie

dziewięć cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_slovenia_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_slovenia_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver s_license_number

- vozniško dovoljenje
- licencja vozniška številka
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj

## <a name="slovenia-passport-number"></a>Numer paszportu Słowenii

### <a name="format"></a>Formacie

dwie litery, po których następuje siedem cyfr bez spacji ani ograniczników

### <a name="pattern"></a>Wzór

dwie litery, po których następuje siedem cyfr:

- litera "P"
- jedna wielkie litery
- siedem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_slovenia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_slovenia_eu_passport_number` .
- Wyrażenie `Regex_eu_passport_date1` regularne znajduje datę w formacie DD.MM.RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_slovenia_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_slovenia_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- lista potni #
- datum rojstva
- lista potni
- številke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="slovenia-physical-addresses"></a>Adresy fizyczne Słowenii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym ze Słowenii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="slovenia-tax-identification-number"></a>Słoweński numer identyfikacji podatkowej

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

osiem cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

- jedna cyfra z zakresu od 1 do 9
- sześć cyfr
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_slovenia_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_slovenia_eu_tax_file_number`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_slovenia_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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
- plik podatkowy nie
- numer pliku podatkowego
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="slovenia-unique-master-citizen-number"></a>Słoweński unikatowy główny numer obywatela

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

13 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

13 cyfr w określonym wzorcu:

- siedem cyfr, które odpowiadają dacie urodzenia (DDMMLLL), gdzie "LLL" odpowiada ostatnim trzem cyfrom roku urodzenia
- dwie cyfry odpowiadające obszarowi urodzenia "50"
- trzy cyfry, które odpowiadają kombinacji płci i numeru seryjnego dla osób urodzonych tego samego dnia. 000-499 dla mężczyzn i 500-999 dla kobiet.
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_slovenia_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_slovenia_eu_national_id_card`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_slovenia_eu_national_id_card` znajduje zawartość zgodną ze wzorcem.

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

- edinstvena številka glavnega državljana
- emšo
- enotna maticna številka obcana
- id card
- numer identyfikacyjny
- identifikacijska številka
- Dowód tożsamości
- identyfikator nacionalna
- nacionalni potni list
- identyfikator krajowy
- osebna izkaznica
- koda osebni
- osebni ne
- osebni številka
- kod osobisty
- numer osobisty
- osobisty kod liczbowy
- številka državljana
- unikatowy numer obywatela
- unikatowy numer identyfikatora
- unikatowy numer tożsamości
- unikatowy numer obywatela głównego
- unikatowy numer rejestracji
- uniqueidentityno #
- uniqueidentityno #

## <a name="south-africa-identification-number"></a>Republika Południowej Afryki — numer identyfikacyjny

### <a name="format"></a>Formacie

13 cyfr, które mogą zawierać spacje

### <a name="pattern"></a>Wzór

13 cyfr:

- sześć cyfr w formacie YYMMDD, które są datą urodzenia
- cztery cyfry
- jednocyfrowy wskaźnik obywatelstwa
- cyfra "8" lub "9"
- jedna cyfra, która jest cyfrą sumy kontrolnej

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_south_africa_identification_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_south_africa_identification_number.
- Suma kontrolna przechodzi.

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

- Dowód tożsamości
- ID
- Identyfikacji

## <a name="south-korea-resident-registration-number"></a>Numer rejestracyjny rezydenta Korei Południowej

### <a name="format"></a>Formacie

13 cyfr zawierających łącznik

### <a name="pattern"></a>Wzór

13 cyfr:

- sześć cyfr w formacie YYMMDD, które są datą urodzenia
- łącznik
- jedna cyfra określona przez wiek i płeć
- czterocyfrowy kod regionu urodzenia
- jedna cyfra używana do rozróżniania osób, dla których poprzednie liczby są identyczne
- cyfrę kontrolną.

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_south_korea_resident_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_south_korea_resident_number.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_south_korea_resident_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- Krajowa karta tożsamości
- Numer rejestracyjny obywatela
- Jumin deungnok beonho
- RRN
- 주민등록번호

## <a name="spain-dni"></a>Hiszpania DNI

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

osiem cyfr, po których następuje jeden znak

### <a name="pattern"></a>Wzór

siedem cyfr, po których następuje jeden znak

- osiem cyfr
- Opcjonalne spacja lub łącznik
- jedna litera kontrolna (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_spain_eu_DL_and_NI_number_citizen` lub `Func_spain_eu_DL_and_NI_number_foreigner` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_spain_eu_national_id_card"`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_spain_eu_DL_and_NI_number_citizen` lub `Func_spain_eu_DL_and_NI_number_foreigner` znajduje zawartość zgodną ze wzorcem.

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
- krajowy numer identyfikacyjny
- tożsamość narodowa
- nationalid #
- nationalidno #
- nie #
- nie
- nienúmero #
- número de identificación
- número nacional identidad
- osobisty numer identyfikacyjny
- tożsamość osobista nie
- unikatowy numer tożsamości
- Uniqueid #

## <a name="spain-drivers-license-number"></a>Numer hiszpańskiego prawa jazdy

### <a name="format"></a>Formacie

osiem cyfr, po których następuje jeden znak

### <a name="pattern"></a>Wzór

osiem cyfr, po których następuje jeden znak:

- osiem cyfr
- jedna cyfra lub litera (bez uwzględniania wielkości liter)

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_spain_eu_DL_and_NI_number_citizen` lub `Func_spain_eu_DL_and_NI_number_foreigner` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_spain_eu_driver's_license_number` .

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_spain_eu_DL_and_NI_number_citizen` lub `Func_spain_eu_DL_and_NI_number_foreigner` znajduje zawartość zgodną ze wzorcem.

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_spain_eu_drivers_license_number"></a>s_license_number Keywords_spain_eu_driver

- permiso de conducción
- permiso conducción
- licencia de conducir
- licencia conducir
- permiso conducir
- permiso de conducir
- permisos de conducir
- permisos conducir
- carnet conducir
- carnet de conducir
- licencia de manejo
- licencia manejo

## <a name="spain-passport-number"></a>Numer paszportu Hiszpanii

### <a name="format"></a>Formacie

ośmio- lub dziewięcioznakowe połączenie liter i cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

ośmio- lub dziewięcioznakowe połączenie liter i cyfr:

- dwie cyfry lub litery
- jedna cyfra lub litera (opcjonalnie)
- sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie dotyczy

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_spain_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_spain_eu_passport_number` .
- Wyrażenie `Regex_spain_eu_passport_date` regularne znajduje datę w formacie DD-MM-RRRR lub znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_spain_eu_passport_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_spain_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta pasaporte
- número pasaporte
- españa pasaporte
- números de pasaporte
- número de pasaporte
- números pasaporte
- pasaporte no
- Passeport n°
- n° Passeport
- pasaporte no.
- pasaporte n°
- paszport hiszpanii

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="spain-physical-addresses"></a>Adresy fizyczne Hiszpanii

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Hiszpanii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="spain-social-security-number-ssn"></a>Numer ubezpieczenia społecznego w Hiszpanii (SSN)

### <a name="format"></a>Formacie

11–12 cyfr

### <a name="pattern"></a>Wzór

11–12 cyfr:

- dwie cyfry
- ukośnik (opcjonalnie)
- od siedmiu do ośmiu cyfr
- ukośnik (opcjonalnie)
- dwie cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_spanish_social_security_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.
- - Odnaleziono słowo kluczowe.`Keywords_spain_eu_ssn_or_equivalent`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_spanish_social_security_number znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

- Ssn
- Ssn #
- socialsecurityno
- zabezpieczenia społecznego nie
- numer ubezpieczenia społecznego
- número de la seguridad social

## <a name="spain-tax-identification-number"></a>Numer identyfikacji podatkowej Hiszpanii

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

siedem lub osiem cyfr i jedna lub dwie litery w określonym wzorcu

### <a name="pattern"></a>Wzór

Hiszpańskie osoby fizyczne z krajowym dowodem tożsamości Hiszpanii:

- osiem cyfr
- jedna wielkie litery (wielkość liter)

Hiszpanie niebędący rezydentami bez narodowego dowodu osobistego Hiszpanii

- jedna wielkie litery "L" (wielkość liter)
- siedem cyfr
- jedna wielkie litery (wielkość liter)

Rezydent Hiszpanie w wieku poniżej 14 lat bez hiszpańskiego dowodu osobistego:

- jedna wielkie litery "K" (wielkość liter)
- siedem cyfr
- jedna wielkie litery (wielkość liter)

Obcokrajowcy z numerem identyfikacyjnym cudzoziemca

- jedną wielką literę, która ma wartość "X", "Y" lub "Z" (wielkość liter)
- siedem cyfr
- jedna wielkie litery (wielkość liter)

Obcokrajowcy bez numeru identyfikacyjnego cudzoziemca

- jedna wielkie litery, która jest literą "M" (wielkość liter)
- siedem cyfr
- jedna wielkie litery (wielkość liter)

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_spain_eu_tax_file_number` lub `Func_spain_eu_DL_and_NI_number_citizen` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_spain_eu_tax_file_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_spain_eu_tax_file_number` lub `Func_spain_eu_DL_and_NI_number_citizen` znajduje zawartość zgodną ze wzorcem.

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

- Cif
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- plik podatkowy nie
- numer pliku podatkowego
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="sql-server-connection-string"></a>parametry połączenia SQL Server

### <a name="format"></a>Formacie

Ciąg "User Id", "User ID", "uid" lub "UserId", a następnie znaki i ciągi opisane we wzorcu poniżej.

### <a name="pattern"></a>Wzór

- ciąg "User Id", "User ID", "uid" lub "UserId"
- dowolna kombinacja od 1 do 200 małych lub wielkich liter, cyfr, symboli, znaków specjalnych lub spacji
- ciąg "Password" lub "pwd", gdzie "pwd" nie jest poprzedzony małą literą
- znak równości (=)
- dowolny znak, który nie jest znakiem dolara ($), symbolem procentu (%), większym niż symbol (>), symbolem (@), cudzysłem ("), średnikiem (;), lewym nawiasem klamrowym([) lub lewym nawiasem kwadratowym ({)
- dowolna kombinacja od 7 do 128 znaków, które nie są średnikami (;), ukośnikiem (/) lub cudzysłów (")
- średnik (;) lub cudzysłów (")

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne CEP_Regex_SQLServerConnectionString znajduje zawartość zgodną ze wzorcem.
- Nie można odnaleźć słowa kluczowego z CEP_GlobalFilter.
- Wyrażenie regularne CEP_PasswordPlaceHolder nie znajduje zawartości zgodnej ze wzorcem.
- Wyrażenie regularne CEP_CommonExampleKeywords nie znajduje zawartości zgodnej ze wzorcem.

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
- somepassword
- secretPassword
- Przykładowe

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych.

- Hasło lub pwd, po którym następuje 0-2 spacje, znak równości (=), spacje 0-2 i gwiazdka (*) -OR-
- Hasło lub pwd, po którym następuje:
    - Znak równości (=)
    - Mniej niż symbol (<)
    - Dowolna kombinacja od 1 do 200 znaków, które są wielkimi lub małymi literami, cyframi, gwiazdką (*), łącznikiem (-), podkreśleniem (_) lub znakiem odstępu
    - Symbol większy niż (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Ten typ informacji poufnych identyfikuje te słowa kluczowe przy użyciu wyrażenia regularnego, a nie listy słów kluczowych.

- Contoso
- Fabrikam
- Northwind
- Piaskownicy
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Netto

## <a name="surgical-procedures"></a>Procedury chirurgiczne

Ta uwolniona nazwana jednostka wykrywa terminy związane z zabiegami chirurgicznymi, takimi jak *wyrostek robakowy*.  Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="sweden-drivers-license-number"></a>Szwedzki numer prawa jazdy

### <a name="format"></a>Formacie

10 cyfr zawierających łącznik

### <a name="pattern"></a>Wzór

10 cyfr zawierających łącznik:

- sześć cyfr
- łącznik
- cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie `Regex_sweden_eu_driver's_license_number` regularne znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_driver's_license_number` `Keywords_sweden_eu_driver's_license_number` .

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver's_license_number

- ajokortti
- permis de conducere
- ajokortin numero
- kuljettajat lic.
- drivere lic.
- körkort
- numărul permisului de conducere
- שאָפער דערלויבעניש נומער
- förare lic.
- דריווערס דערלויבעניש
- körkortsnummer

## <a name="sweden-national-id"></a>Identyfikator krajowy Szwecji

### <a name="format"></a>Formacie

10 lub 12 cyfr i opcjonalny ogranicznik

### <a name="pattern"></a>Wzór

10 lub 12 cyfr i opcjonalny ogranicznik:

- dwie cyfry (opcjonalnie)
- Sześć cyfr w formacie daty RRMMDD
- ogranicznik "-" lub "+" (opcjonalnie)
- cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_swedish_national_identifier` znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z `Keywords_swedish_national_identifier`
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_swedish_national_identifier` znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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
- numer identyfikatora
- Identyfikator #
- brak identyfikacji
- numer identyfikacyjny
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- dokument tożsamości
- brak tożsamości
- numer tożsamości
- id-nummer
- osobisty identyfikator
- personnummer #
- personnummer
- skatteidentifikationsnummer

## <a name="sweden-passport-number"></a>Numer paszportu Szwecji

### <a name="format"></a>Formacie

osiem cyfr

### <a name="pattern"></a>Wzór

osiem kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- wyrażenie regularne Regex_sweden_passport_number znajduje zawartość zgodną ze wzorcem.
- słowo kluczowe z `Keywords_eu_passport_number` lub `Keyword_sweden_passport` zostanie znalezione.
- wyrażenie `Regex_sweden_eu_passport_date` regularne znajduje datę w formacie DD MMM/MMM RR (01 JAN/JAN 12) lub znaleziono słowo kluczowe z `Keywords_eu_passport_date` .

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- wyrażenie regularne Regex_sweden_passport_number znajduje zawartość zgodną ze wzorcem.
- słowo kluczowe z `Keywords_eu_passport_number` lub `Keyword_sweden_passport` zostanie znalezione.

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- karta rejestracji obcych
- g3 opłaty za przetwarzanie
- wpis wielokrotny
- Numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passnummer
- pass nr
- wiza schengen
- wizy schengen
- pojedynczy wpis
- sverige pass
- wymogi wizowe
- przetwarzanie wiz
- typ wizy

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- data wydania
- data wygaśnięcia

## <a name="sweden-physical-addresses"></a>Adresy fizyczne Szwecji

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym ze Szwecji. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="sweden-tax-identification-number"></a>Szwedzki numer identyfikacji podatkowej

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

10 cyfr i symbol w określonym wzorcu

### <a name="pattern"></a>Wzór

10 cyfr i symbol:

- sześć cyfr odpowiadających dacie urodzenia (RRMMDD)
- znak plusa lub znak minus
- trzy cyfry, które sprawiają, że numer identyfikacyjny jest unikatowy, gdzie:
  - w przypadku liczb wydanych przed 1990 r. siódma i ósma cyfra identyfikują powiat urodzenia lub osoby urodzone za granicą
  - cyfra na dziewiątej pozycji wskazuje płeć jako nieparzystą dla mężczyzn, a nawet dla kobiet
- jedna cyfra kontrolna

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_sweden_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_sweden_eu_tax_file_number`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_sweden_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.

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

- osobisty numer identyfikatora
- personnummer
- skatt id nummer
- skatt identifikation
- skattebetalarens identifikationsnummer
- sverige cyny
- plik podatkowy
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="swift-code"></a>Kod SWIFT

### <a name="format"></a>Formacie

cztery litery, po których następuje od 5 do 31 liter lub cyfr

### <a name="pattern"></a>Wzór

cztery litery, po których następuje od 5 do 31 liter lub cyfr:

- czteroliterowy kod banku (bez uwzględniania wielkości liter)
- opcjonalne miejsce
- 4–28 liter lub cyfr (podstawowy numer konta bankowego (BBAN))
- opcjonalne miejsce
- od jednej do trzech liter lub cyfr (pozostała część BBAN)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_swift znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_swift.

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

- międzynarodowa organizacja do standaryzacji 9362
- iso 9362
- iso9362
- Swift #
- swiftcode
- swiftnumber
- swiftroutingnumber
- kod swift
- numer swift #
- numer szybkiego routingu
- bic number
- kod bic
- Bic #
- Bic #
- kod identyfikatora banku
- Organizacja internationale de normalisation 9362
- Rapide #
- kod SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- \# BIC
- code identificateur de banque
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

## <a name="switzerland-physical-addresses"></a>Adresy fizyczne Szwajcarii

Ta uwolniona nazwana jednostka wykrywa wzorce związane z adresem fizycznym ze Szwajcarii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="switzerland-ssn-ahv-number"></a>Szwajcaria SSN AHV number

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

13-cyfrowy numer

### <a name="pattern"></a>Wzór

13-cyfrowy numer:

- trzy cyfry — 756
- opcjonalna kropka
- cztery cyfry
- opcjonalna kropka
- cztery cyfry
- opcjonalna kropka
- dwie cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_swiss_social_security_number_ahv znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keywords_swiss_social_security_number_ahv.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_swiss_social_security_number_ahv znajduje zawartość zgodną ze wzorcem.

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

- Ahv
- Ssn
- Pid
- numer ubezpieczenia
- personalidno #
- numer ubezpieczenia społecznego
- osobisty numer identyfikatora
- numer identyfikacji osobistej.
- insuranceno #
- uniqueidno #
- unikatowy numer identyfikacyjny.
- numer avs
- tożsamość osobista bez versicherungsnummer
- identifikationsnummer
- einzigartige identität nicht
- sozialversicherungsnummer
- identyfikator identyfikacyjny personelu
- numéro de sécurité sociale

## <a name="taiwan-national-identification-number"></a>Krajowy numer identyfikacyjny Tajwanu

### <a name="format"></a>Formacie

jedna litera (w języku angielskim), po której następuje dziewięć cyfr

### <a name="pattern"></a>Wzór

jedna litera (w języku angielskim), po której następuje dziewięć cyfr:

- jedna litera (w języku angielskim, bez uwzględniania wielkości liter)
- cyfra "1" lub "2"
- osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_taiwanese_national_id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_taiwanese_national_id.
- Suma kontrolna przechodzi.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_taiwanese_national_id znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

## <a name="taiwan-passport-number"></a>Numer paszportu Tajwanu

### <a name="format"></a>Formacie

- numer paszportu biometrycznego: dziewięć cyfr
- numer paszportu nie biometrycznego: dziewięć cyfr

### <a name="pattern"></a>Wzór
biometryczny numer paszportu:

- znak "3"
- osiem cyfr

nie biometryczny numer paszportu:

- dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_taiwan_passport znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_taiwan_passport.

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
- Numer paszportu
- Numer paszportu
- Paszport #
- 护照
- 中華民國護照
- Zhōnghuá Mínguó hùzhào

## <a name="taiwan-resident-certificate-arctarc-number"></a>Numer certyfikatu rezydenta Tajwanu (ARC/TARC)

### <a name="format"></a>Formacie

10 liter i cyfr

### <a name="pattern"></a>Wzór

10 liter i cyfr:

- dwie litery (bez uwzględniania wielkości liter)
- osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_taiwan_resident_certificate znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_taiwan_resident_certificate.

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

- Certyfikat rezydenta
- Certyfikat rezydenta
- Certyfikat rezydenta.
- Karta identyfikacyjna
- Certyfikat rezydenta cudzoziemca
- ŁUKU
- Certyfikat rezydenta obszaru Tajwanu
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證

## <a name="thai-population-identification-code"></a>Kod identyfikacji populacji tajskiej

### <a name="format"></a>Formacie

13 cyfr

### <a name="pattern"></a>Wzór

13 cyfr:

- pierwsza cyfra nie jest równa zero lub dziewięć
- 12 cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_Thai_Citizen_Id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Thai_Citizen_Id.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_Thai_Citizen_Id znajduje zawartość zgodną ze wzorcem.

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

- Numer identyfikatora
- Numer identyfikacyjny
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkey-national-identification-number"></a>Krajowy numer identyfikacyjny Turcji

### <a name="format"></a>Formacie

11 cyfr

### <a name="pattern"></a>Wzór

11 cyfr

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_Turkish_National_Id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Turkish_National_Id.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_Turkish_National_Id znajduje zawartość zgodną ze wzorcem.

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

- TC Kimlik Nie
- TC Kimlik numarası
- Vatandaşlık numarası
- Vatandaşlık nie

## <a name="turkey-physical-addresses"></a>Adresy fizyczne Turcji

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Turcji. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="types-of-medication"></a>Typy leków

Ta uwolniona nazwana jednostka wykrywa nazwy leków, takie jak *insulina*.  Obsługuje tylko angielskie terminy. Jest on również zawarty w [wszystkich warunkach medycznych](#all-medical-terms-and-conditions) w pakiecie o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

High (Wysoki)

## <a name="uk-drivers-license-number"></a>WIELKIEJ BRYTANII. numer prawa jazdy

### <a name="format"></a>Formacie

Kombinacja 18 liter i cyfr w określonym formacie

### <a name="pattern"></a>Wzór

18 liter i cyfr:

- Pięć liter (bez uwzględniania wielkości liter) lub cyfra "9" zamiast litery.
- Jedna cyfra.
- Pięć cyfr w formacie daty MMDDY dla daty urodzenia. Siódmy znak jest zwiększany o 50, jeśli kierowca jest kobietą; na przykład od 51 do 62 zamiast od 01 do 12.
- Dwie litery (bez uwzględniania wielkości liter) lub cyfra "9" zamiast litery.
- Pięć cyfr.

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_uk_drivers_license` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_eu_driver's_license_number`
- Suma kontrolna przechodzi.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_uk_drivers_license` znajduje zawartość zgodną ze wzorcem.
- Suma kontrolna przechodzi.

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

#### <a name="keywords_eu_drivers_license_number"></a>s_license_number Keywords_eu_driver

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- sterowniki
- sterowniki
- sterowniki
- sterowniki
- driverslicense
- driverslicenses
- sterowniki lic
- lics sterowników
- prawo jazdy
- licencje sterowników
- prawo jazdy
- prawa jazdy
- driver'lic
- driver'lics
- driver'license
- prawa jazdy
- prawo jazdy
- prawa jazdy
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawo jazdy
- kolka sterownika
- kolki sterownika
- driver'slicense
- fragmentatory sterownika
- kolidacja kierowcy
- driver'slicences
- lic sterownika
- lics sterownika
- prawo jazdy
- prawa jazdy
- prawo jazdy
- prawa jazdy
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawa jazdy #
- sterowniki #
- sterowniki #
- driverslicense #
- driverslicenses #
- sterowniki #
- sterowniki #
- sterowniki lic #
- lics sterowników #
- prawo jazdy #
- licencje sterowników #
- prawo jazdy #
- prawa jazdy #
- driver'lic #
- driver'lics #
- driver'license #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawo jazdy #
- kolka sterownika #
- kolki sterownika #
- driver'slicense #
- fragmentatory sterownika #
- kolidacja kierowcy #
- driver'slicences #
- lic sterownika #
- lics sterownika #
- prawo jazdy #
- prawa jazdy #
- prawo jazdy #
- prawa jazdy #
- Prawa jazdy
- Prawo jazdy
- dlno #
- driv lic
- driv licen
- licencja driv
- licencje driv
- licencja driv
- licencje driv
- sterownik licen
- sterowniki licen
- licen kierowcy
- lic jazdy
- jazdy licen
- prawo jazdy
- Prawa jazdy
- Prawa jazdy
- prawo jazdy
- dl nie
- dlno
- Numer dl

## <a name="uk-electoral-roll-number"></a>WIELKIEJ BRYTANII. numer listy wyborczej

### <a name="format"></a>Formacie

dwie litery, po których następuje od 1 do 4 cyfr

### <a name="pattern"></a>Wzór

dwie litery (bez uwzględniania wielkości liter), po którym następuje od 1 do 4 cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_uk_electoral znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_uk_electoral.

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

- nominacja rady
- formularz nominacji
- rejestr wyborców
- spis wyborców

## <a name="uk-national-health-service-number"></a>WIELKIEJ BRYTANII. numer krajowej służby zdrowia

### <a name="format"></a>Formacie

10–17 cyfr rozdzielonych spacjami

### <a name="pattern"></a>Wzór

10–17 cyfr:

- 3 lub 10 cyfr
- spację
- trzy cyfry
- spację
- cztery cyfry

### <a name="checksum"></a>Suma kontrolna

Tak

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_uk_nhs_number znajduje zawartość zgodną ze wzorcem.
- Jedno z następujących elementów jest prawdziwe:
    - Znaleziono słowo kluczowe z Keyword_uk_nhs_number.
    - Znaleziono słowo kluczowe z Keyword_uk_nhs_number1.
    - Znaleziono słowo kluczowe z Keyword_uk_nhs_number_dob.
- Suma kontrolna przechodzi.

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

- krajowa służba zdrowia
- Nhs
- urząd usług zdrowotnych
- służba zdrowia

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- identyfikator pacjenta
- identyfikacja pacjenta
- nie pacjent
- numer pacjenta

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.O.B
- Data urodzenia
- Data urodzenia

## <a name="uk-national-insurance-number-nino"></a>WIELKIEJ BRYTANII. krajowy numer ubezpieczenia (NINO)

Ta jednostka typu informacji poufnych jest uwzględniana w typie informacji poufnych krajowego numeru identyfikacyjnego UE. Jest również dostępna jako autonomiczna jednostka typu informacji poufnych.

### <a name="format"></a>Formacie

siedem znaków lub dziewięć znaków rozdzielonych spacjami lub kreskami

### <a name="pattern"></a>Wzór

dwa możliwe wzorce:

- dwie litery (prawidłowe nazwy NINO używają tylko pewnych znaków w tym prefiksie, co jest weryfikowane przez ten wzorzec, a nie uwzględnia wielkość liter)
- sześć cyfr
- "A", "B", "C" lub "D" (podobnie jak prefiks, tylko niektóre znaki są dozwolone w sufiksie; nie uwzględnia wielkość liter)

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

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_uk_nino znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_uk_nino.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_uk_nino znajduje zawartość zgodną ze wzorcem.

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

- krajowy numer ubezpieczenia
- składki na ubezpieczenie społeczne
- akt ochrony
- Ubezpieczenia
- numer ubezpieczenia społecznego
- wniosek o ubezpieczenie
- aplikacja medyczna
- ubezpieczenie społeczne
- Lekarskiej
- zabezpieczenia społeczne
- Wielka Brytania
- Numer ni
- Nr ni.
- NI #
- NI #
- Ubezpieczenia #
- numer ubezpieczenia
- nationalinsurance #
- nationalinsurancenumber

## <a name="uk-physical-addresses"></a>WIELKIEJ BRYTANII. adresy fizyczne

Ta uwolniona nazwana jednostka wykrywa wzorce związane z adresem fizycznym z Zjednoczonej Brytanii. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="uk-unique-taxpayer-reference-number"></a>WIELKIEJ BRYTANII. Unikatowy numer referencyjny podatnika

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

10 cyfr bez spacji i ograniczników

### <a name="pattern"></a>Wzór

10 cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_uk_eu_tax_file_number` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keywords_uk_eu_tax_file_number`

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

- numer podatkowy
- plik podatkowy
- identyfikator podatkowy
- numer identyfikacji podatkowej
- numer identyfikacji podatkowej
- numer podatkowy #
- numer podatkowy
- numer rejestracji podatkowej
- taxid #
- taxidno #
- taxidnumber #
- taksoń #
- taxnumber #
- taxnumber
- identyfikator cyny
- nie cyny
- Tin #

## <a name="us-bank-account-number"></a>Numer konta bankowego w Stanach Zjednoczonych

### <a name="format"></a>Formacie

6–17 cyfr

### <a name="pattern"></a>Wzór

6–17 kolejnych cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_usa_bank_account_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_usa_Bank_Account.

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
- Sprawdzanie numeru akcesu
- Sprawdzanie dostępu #
- Sprawdzanie nr dostępu
- Sprawdzanie nr konta
- Numer konta bankowego
- Konto bankowe #
- Numer akcesu bankowego
- Bank Acct #
- Bank Acct Nr.
- Nr konta bankowego
- Numer konta oszczędnościowego
- Konto oszczędnościowe.
- Konto oszczędnościowe #
- Numer akcesu oszczędności
- Oszczędności acct #
- Nr dostępu oszczędnościowego
- Nr konta oszczędnościowego
- Numer konta debetowego
- Konto debetowe
- Konto debetowe #
- Numer akcesu debetowego
- Akces debetowy #
- Numer akcesu debetowego
- Numer konta debetowego

## <a name="us-drivers-license-number"></a>Numer prawa jazdy w Stanach Zjednoczonych

### <a name="format"></a>Formacie

Zależy od stanu

### <a name="pattern"></a>Wzór

zależy od stanu — na przykład Nowy Jork:

- dziewięć cyfr sformatowanych jak ddd ddd ddd będzie zgodne.
- dziewięć cyfr, takich jak dddddddddd, nie będzie zgodne.

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_new_york_drivers_license_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_[state_name]_drivers_license_name.
- Znaleziono słowo kluczowe z Keyword_us_drivers_license.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_new_york_drivers_license_number znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_[state_name]_drivers_license_name.
- Znaleziono słowo kluczowe z Keyword_us_drivers_license_abbreviations.
- Nie znaleziono słowa kluczowego z Keyword_us_drivers_license.

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
- ID
- Identyfikatory
- DL #
- DLS #
- CDL #
- CDLS #
- IDENTYFIKATOR #
- Identyfikatory #
- Numer identyfikatora
- Numery identyfikatorów
- LIC
- LIC #
- DLN

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- Sterownik Lic
- Sterownik Lics
- Prawo jazdy
- Prawa jazdy
- Sterowniki
- SterownikiLics
- DriversLicense
- DriversLicenses
- Sterowniki Lic
- Sterowniki Lics
- Licencja kierowcy
- Licencje kierowców
- Driver'Lic
- Driver'Lics
- Prawo jazdy
- Prawa jazdy
- Lic sterownika
- Lics kierowcy
- Prawo jazdy
- Prawa jazdy
- Driver'sLic
- Kursywę sterownika
- Driver'sLicense
- Driver'sLicenses
- Lic kierowcy
- Lics kierowcy
- Prawo jazdy
- Prawa jazdy
- numer identyfikacyjny
- numery identyfikacyjne
- Identyfikacji #
- id card
- karty identyfikatorów
- karta identyfikacyjna
- karty identyfikacyjne
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- Sterownik Lic #
- Sterownik Lics #
- Prawo jazdy #
- Prawa jazdy #
- Sterowniki #
- SterownikiLics #
- DriversLicense #
- DriversLicenses #
- Sterowniki Lic #
- Sterowniki Lics #
- Licencja kierowcy #
- Licencje kierowców #
- Driver'Lic #
- Driver'Lics #
- Prawo jazdy #
- Prawa jazdy #
- Lic sterownika #
- Lics kierowcy #
- Prawo jazdy #
- Prawa jazdy #
- Driver'sLic #
- Kursywę sterownika #
- Driver'sLicense #
- Driver'sLicenses #
- Lic kierowcy #
- Lics kierowcy #
- Prawo jazdy #
- Prawa jazdy #
- id card #
- karty identyfikatorów #
- karta identyfikacyjna #
- karty identyfikacyjne #

#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- skrót stanu (na przykład "NY")
- nazwa stanu (na przykład "Nowy Jork")

## <a name="us-individual-taxpayer-identification-number-itin"></a>Numer identyfikacyjny indywidualnego podatnika w USA (ITIN)

### <a name="format"></a>Formacie

dziewięć cyfr rozpoczynających się od cyfry "9" i zawierających znak "7" lub "8" jako czwartą cyfrę, opcjonalnie sformatowaną spacjami lub kreskami

### <a name="pattern"></a>Wzór

Sformatowany:

- cyfra "9"
- dwie cyfry
- spacja lub kreska
- a "7" lub "8"
- cyfra
- spacja lub kreska
- cztery cyfry

Niesformatowany:

- cyfra "9"
- dwie cyfry
- a "7" lub "8"
- pięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_formatted_itin znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_itin.

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_unformatted_itin znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_itin.

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja Func_formatted_itin lub Func_unformatted_itin znajduje zawartość zgodną ze wzorcem.

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

- Podatnik
- identyfikator podatkowy
- identyfikacja podatkowa
- itin
- i.t.i.n.
- Ssn
- Tin
- zabezpieczenia społeczne
- Podatnika
- itiny
- taxid
- indywidualny podatnik

## <a name="us-physical-addresses"></a>Adresy fizyczne w Stanach Zjednoczonych

Ta odłączona nazwana jednostka wykrywa wzorce związane z adresem fizycznym ze Stanów Zjednoczonych. Jest również uwzględniony w [pakiecie Wszystkie adresy fizyczne](#all-physical-addresses) o nazwie entity SIT.

### <a name="confidence-level"></a>Poziom ufności

Średni

## <a name="us-social-security-number-ssn"></a>Numer ubezpieczenia społecznego (SSN)

### <a name="format"></a>Formacie

dziewięć cyfr, które mogą mieć sformatowany lub niesformatowany wzorzec

> [!NOTE]
> Jeśli została wydana przed połową 2011 r., nazwa SSN ma silne formatowanie, w którym niektóre części liczby muszą znajdować się w określonych zakresach, aby były prawidłowe (ale nie ma sumy kontrolnej).

### <a name="pattern"></a>Wzór

cztery funkcje poszukają sieci SSN w czterech różnych wzorcach:

- Func_ssn znajduje nazwy SSN z silnym formatowaniem sprzed 2011 r., które są sformatowane z kreskami lub spacjami (ddd-dd-dddd OR ddd dddd)
- Func_unformatted_ssn znajduje sieci SSN z silnym formatowaniem sprzed 2011 r., które nie są sformatowane jako dziewięć kolejnych cyfr (ddddddddd)
- Func_randomized_formatted_ssn znajduje nazwy SSN po 2011 r., które są sformatowane kreskami lub spacjami (ddd-dd-dddd OR ddd dddd)
- Func_randomized_unformatted_ssn znajduje nazwy SSN po 2011 r., które nie są sformatowane jako dziewięć kolejnych cyfr (ddddddddd)

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja `Func_ssn` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_ssn`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_unformatted_ssn" znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_ssn`

Zasady DLP mają małą pewność, że wykryto tego typu poufne informacje, jeśli znajdują się w pobliżu 300 znaków:

- Funkcja `Func_randomized_formatted_ssn` lub `Func_randomized_unformatted_ssn` znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe.`Keyword_ssn`

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
- numer ubezpieczenia społecznego
- zabezpieczenia społeczne #
- zabezpieczenia społeczne #
- zabezpieczenia społecznego nie
- Zabezpieczenia społeczne #
- Soc S
- SSN
- SSNS
- SSN #
- SS #
- SSID

## <a name="usuk-passport-number"></a>Stany Zjednoczone/Zjednoczone Zjednoczone numer paszportu

### <a name="format"></a>Formacie

dziewięć cyfr

### <a name="pattern"></a>Wzór

- jedna litera lub cyfra
- osiem cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają dużą pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_usa_uk_passport znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_uk_eu_passport_number` .
- Znaleziono słowo kluczowe z `Keywords_eu_passport_date`

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Funkcja Func_usa_uk_passport znajduje zawartość zgodną ze wzorcem.
- Odnaleziono słowo kluczowe lub `Keywords_eu_passport_number` `Keywords_uk_eu_passport_number` .

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

- Paszport #
- Paszport #
- passportid
- Paszporty
- passportno
- nr paszportu
- passportnumber
- numer paszportu
- passportnumbers
- numery paszportów

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- brytyjski paszport
- brytyjski paszport

## <a name="ukraine-passport-domestic"></a>Paszport ukrainy krajowy

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

dziewięć cyfr

### <a name="pattern"></a>Wzór

dziewięć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Rejestr Regex_Ukraine_Passport_Domestic znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Ukraine_Passport_Domestic.

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

- paszport ukrainy
- numer paszportu
- nr paszportu
- паспорт України
- номер паспорта
- персональний

## <a name="ukraine-passport-international"></a>Ukraina paszport międzynarodowy

Ten typ informacji poufnych jest dostępny tylko do użycia w:

- zasady ochrony przed utratą danych
- zasady zgodności komunikacji
- zarządzanie cyklem życia danych
- zarządzanie rekordami
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Formacie

ośmioznakowy wzorzec alfanumeryczny

### <a name="pattern"></a>Wzór

ośmioznakowy wzorzec alfanumeryczny:

- dwie litery lub cyfry
- sześć cyfr

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Rejestr Regex_Ukraine_Passport_International znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_Ukraine_Passport_International.

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

- paszport ukrainy
- numer paszportu
- nr paszportu
- паспорт України
- номер паспорта
