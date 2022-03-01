---
title: Funkcje typów informacji poufnych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: low
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
recommendations: false
description: Informacje na temat wyszukiwania funkcji typów informacji poufnych.
ms.openlocfilehash: d00b61aeeb435940436bd0c901edce2fef81a3e4
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014903"
---
# <a name="sensitive-information-type-functions"></a>Funkcje typów informacji poufnych

Typy informacji poufnych (SIT) mogą używać funkcji jako elementów podstawowych do identyfikowania elementów poufnych. Na przykład typ informacji poufnych Numer karty kredytowej używa Func_credit_card do wykrywania numeru karty kredytowej.

W tym artykule wyjaśniono, czego szukają tych funkcji, aby ułatwić zrozumienie sposobu działania wstępnie zdefiniowanych typów informacji poufnych. Aby uzyskać więcej informacji, zobacz [Definicje encji typu informacji poufnych.](sensitive-information-type-entity-definitions.md)

## <a name="table-of-functions"></a>Tabela funkcji

|Nazwa funkcji | Akcja funkcji | Jest validatorem|
|---------|----------|---------|
|Func_aba_routing|wykrywa numer routingu ABA|tak|
|Func_alabama_drivers_license_number|Wykrywa numer prawa jazdy firmy Alabama|nie|
|Func_alaska_delaware_oregon_drivers_license_number|Wykrywa numer prawa jazdy użytkownika Alaska, Delaware, Oregon|nie|
|Func_alaska_drivers_license_number|Wykrywa numer prawa jazdy Alaska|nie|
|Func_alberta_drivers_license_number|Wykrywa numer prawa jazdy z Alberty|nie|
|Func_argentina_Unique_Tax_Key|wykrywa i sprawdza unikatowy klucz podatkowy Argentyny|nie|
|Func_Argentina_Unique_Tax_Key|wykrywa unikatowy klucz podatkowy Argentyny|nie|
|Func_arizona_drivers_license_number|Wykrywa numer prawa jazdy z A arizona|nie|
|Func_arkansas_drivers_license_number|wykrywa numer prawa jazdy użytkownika Dlaansas|nie|
|Func_australian_business_number|Wykrywa numer biznesowy Australii|nie|
|Func_Australian_Company_Number|wykrywa numer firmy w Australii|nie|
|Func_australian_medical_account_number|wykrywa numer konta medycznego w Australii|nie|
|Func_australian_tax_file_number|wykrywa numer pliku podatkowego w Australii|tak|
|Func_austria_eu_ssn_or_equivalent|wykrywa numer PEP w Austrii.|nie|
|Func_austria_eu_tax_file_number|wykrywa numer pliku podatkowego w Austrii|nie|
|Func_Austria_Value_Added_Tax|Wykrywa podatek od wartości dodanej w Austrii|nie|
|Func_belgium_national_number|Wykrywa numer krajowy w Belgia|nie|
|Func_belgium_value_added_tax_number|Wykrywa numer podatku do dodania z Belgia|nie|
|Func_brazil_cnpj|wykrywa numer podmiotu prawnego w Brazylii (CNPJ)|tak|
|Func_brazil_cpf|wykrywa Brazylia CPF|tak|
|Func_brazil_rg|wykrywa brazylia RG|nie|
|Func_british_columbia_drivers_license_number|Wykrywa numer prawa jazdy w Kolumbii Brytyjskiej|nie|
|Func_bulgaria_eu_national_id_card|Wykrywa ujednoliwną liczbę domową w Bułgarii|nie|
|Func_california_drivers_license_number|Wykrywa numer prawa jazdy z Kalifornii|nie|
|Func_canadian_sin|wykrywa sin kanadyjny|tak|
|Func_chile_id_card|Wykrywa kartę identyfikatora Chile|nie|
|Func_china_resident_id|wykrywa identyfikator zamieszkania w Chinach|nie|
|Func_colorado_drivers_license_number|Wykrywa numer prawa jazdy w Kolorado|nie|
|Func_connecticut_drivers_license_number|Wykrywa numer prawa jazdy aplikacji Connecticut|nie|
|Func_credit_card|wykrywa kartę kredytową|tak|
|Func_croatia_id_card|Wykrywa kartę identyfikatora Chorwacja|nie|
|Func_croatia_oib_number|Wykrywa numer OIB Chorwacja|nie|
|Func_cyprus_eu_tax_file_number|Wykrywa numer pliku podatkowego Cypru|nie|
|Func_czech_id_card_new_format|Wykrywa kartę czeskiego identyfikatora w nowym formacie|nie|
|Func_czech_id_card|Wykrywa kartę czeskiego identyfikatora|nie|
|Func_dea_number|Wykrywa numer DEA|tak|
|Func_denmark_eu_tax_file_number|Wykrywa osobisty numer identyfikacyjny w Dania|nie|
|Func_district_of_columbia_drivers_license_number|Wykrywa numer prawa jazdy dystryktu Kolumbia|nie|
|Func_estonia_eu_national_id_card|Wykrywa osobisty kod identyfikacyjny Estonia|nie|
|Func_eu_debit_card|wykrywa kartę debetową UE|nie|
|Func_finnish_national_id|wykrywa fiński identyfikator narodowy|nie|
|Func_florida_drivers_license_number|Wykrywa numer prawa jazdy na Florydzie|nie|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|Wykrywa numer licencji dla Florydy, Maryland, Michigan, Michigan|nie|
|Func_formatted_itin|Wykrywa sformatowany us ITIN|tak|
|Func_fr_insee|wykrywa Francja INSEE|nie|
|Func_fr_passport|wykrywa paszport Francji|nie|
|Func_france_eu_tax_file_number|wykrywa numer pliku podatkowego we Francji|nie|
|Func_france_value_added_tax_number|Wykrywa numer podatku dodanego do Francji|nie|
|Func_french_drivers_license|wykrywa prawo jazdy w języku francuskim|nie|
|Func_french_insee|Wykrywa francuski INSEE|nie|
|Func_georgia_drivers_license_number|Wykrywa numer prawa jazdy w Georgia|nie|
|Func_german_drivers_license|wykrywa prawo jazdy w Niemczech|nie|
|Func_german_passport_data|wykrywa paszport Niemców|nie|
|Func_german_passport|wykrywa paszport Niemców|nie|
|Func_germany_eu_tax_file_number|Wykrywa numer pliku podatkowego Germany|nie|
|Func_germany_value_added_tax_number|Wykrywa numer podatku dodanego w Niemczech|nie|
|Func_greece_eu_ssn|wykrywa sin Grecję (AMKA)|nie|
|Func_hawaii_drivers_license_number|Wykrywa numer licencji dla sterownika Hawaje|nie|
|Func_hong_kong_id_card|wykrywa kartę identyfikatora Hongkongu|nie|
|Func_hungarian_value_added_tax_number|Wykrywa numer podatku do dodania z Węgry|nie|
|Func_hungary_eu_national_id_card|Wykrywa osobisty numer identyfikacyjny Węgry|nie|
|Func_hungary_eu_ssn_or_equivalent|wykrywa numer PEP węgry|nie|
|Func_hungary_eu_tax_file_number|Wykrywa numer pliku podatkowego Węgry|nie|
|Func_iban|wykrywa IBAN|tak|
|Func_idaho_drivers_license_number|wykrywa numer prawa jazdy Idaho|nie|
|Func_illinois_drivers_license_number|Wykrywa numer prawa jazdy illinois|nie|
|Func_india_aadhaar|wykrywa Aadhaar w Indiach|tak|
|Func_indiana_drivers_license_number|wykrywa numer prawa jazdy Indiany|nie|
|Func_iowa_drivers_license_number|wykrywa numer prawa jazdy w programie Iowa|nie|
|Func_ireland_pps|Wykrywa Irlandii PPS|nie|
|Func_israeli_national_id_number|Wykrywa numer identyfikacyjny kraju Izrael|nie|
|Func_italy_eu_national_id_card|Wykrywa kod obrachunkowy Włoch|nie|
|Func_italy_value_added_tax_number|Wykrywa liczbę podatków dodaną do Włoch|nie|
|Func_japanese_my_number_corporate|wykrywa Japonię mój numer firmowy|tak|
|Func_japanese_my_number_personal|Wykrywa japonię mój numer osobisty|tak|
|Func_jp_bank_account_branch_code|Wykrywa kod oddziału konta bankowego w Japonii|nie|
|Func_jp_bank_account|wykrywa konto bankowe w Japonii|nie|
|Func_jp_drivers_license_number|wykrywa numer prawa jazdy z Japonii|nie|
|Func_jp_passport|wykrywa paszport Japonii|nie|
|Func_jp_resident_registration_number|wykrywa numer rejestru w Japonii|nie|
|Func_jp_sin_pre_1997|wykrywa sin Japonii przed 1997|nie|
|Func_jp_sin|wykrywa japonię|nie|
|Func_kansas_drivers_license_number|Wykrywa numer licencji sterownika Kansas|nie|
|Func_kentucky_drivers_license_number|Wykrywa numer prawa jazdy firmy Kentucky|nie|
|Func_kentucky_massachusetts_virginia_drivers_license_number|Wykrywa numer prawa jazdy Kentucky, Alegos, Virginii|nie|
|Func_latvia_eu_national_id_card|Wykrywa łotewski kod osobisty|nie|
|Func_lithuania_eu_tax_file_number|Wykrywa kod osobisty Litwa|nie|
|Func_louisiana_drivers_license_number|wykrywa numer prawa jazdy luizjany|nie|
|Func_luxemburg_eu_tax_file_number_non_natural|Wykrywa narodowy numer identyfikacyjny Luxemburga (osoby nie naturalne)|nie|
|Func_luxemburg_eu_tax_file_number|Wykrywa narodowy numer identyfikacyjny Luxemburga (osoby fizyczne)|nie|
|Func_maine_drivers_license_number|Wykrywa numer prawa jazdy głównej|nie|
|Func_manitoba_drivers_license_number|Wykrywa numer prawa jazdy manitoba|nie|
|Func_maryland_drivers_license_number|wykrywa numer prawa jazdy w maryland|nie|
|Func_massachusetts_drivers_license_number|Wykrywa numer prawa jazdy dla Oprogramowania|nie|
|Func_mexico_population_registry_code|Wykrywa kod rejestru populacji Meksyku|nie|
|Func_michigan_minnesota_drivers_license_number|Wykrywa numer prawa jazdy w Michigan, Michigan|nie|
|Func_minnesota_drivers_license_number|Wykrywa numer prawa jazdy w Torze|nie|
|Func_mississippi_oklahoma_drivers_license_number|Wykrywa błędy missisipi, numer prawa jazdy firmy Oklahoma|nie|
|Func_missouri_drivers_license_number|Wykrywa numer prawa jazdy missouri|nie|
|Func_montana_drivers_license_number|Wykrywa numer prawa jazdy montana|nie|
|Func_nebraska_drivers_license_number|wykrywa numer prawa jazdy firmy Nebraska|nie|
|Func_netherlands_bsn|wykrywa BSN Holandia|nie|
|Func_netherlands_eu_tax_file_number|Wykrywa numer pliku podatkowego Holandia|nie|
|Func_netherlands_value_added_tax_number|Wykrywa numer podatku dodanej wartości holenderskiej|nie|
|Func_nevada_drivers_license_number|Wykrywa numer prawa jazdy firmy Nevada|nie|
|Func_new_brunswick_drivers_license_number|wykrywa numer prawa jazdy nowego Brunszwika|nie|
|Func_new_hampshire_drivers_license_number|Wykrywa numer prawa jazdy w Nowym Hampsterie|nie|
|Func_new_jersey_drivers_license_number|wykrywa numer prawa jazdy w New Jersey|nie|
|Func_new_mexico_drivers_license_number|Wykrywa numer prawa jazdy nowego Meksyku|nie|
|Func_new_york_drivers_license_number|wykrywa numer prawa jazdy z Nowego Jorku|nie|
|Func_new_zealand_bank_account_number|Wykrywa numer konta bankowego w Nowej Zelandii|nie|
|Func_new_zealand_inland_revenue_number|Wykrywa liczbę przychodów Nowej Zelandii na lądzie|nie|
|Func_new_zealand_ministry_of_health_number|Wykrywa nową Zelandię z liczbą kondycji|nie|
|Func_newfoundland_labrador_drivers_license_number|Wykrywa numer prawa jazdy Nowej Fundlandii Labrador|nie|
|Func_newzealand_driver_license_number|Wykrywa numer prawa jazdy w Nowej Zelandii|nie|
|Func_newzealand_social_welfare_number|Wykrywa numer społeczności nowej Zelandii|nie|
|Func_north_carolina_drivers_license_number|Wykrywa numer prawa jazdy w Karolinie Północnej|nie|
|Func_north_dakota_drivers_license_number|Wykrywa numer prawa jazdy North Macedonia|nie|
|Func_norway_id_number|Wykrywa numer identyfikacyjny Norwegia|nie|
|Func_nova_scotia_drivers_license_number|Wykrywa numer prawa jazdy Nowej Szkocji|nie|
|Func_ohio_drivers_license_number|Wykrywa numer prawa jazdy w ohio|nie|
|Func_ontario_drivers_license_number|wykrywa numer prawa jazdy w Ontario|nie|
|Func_pennsylvania_drivers_license_number|Wykrywa numer prawa jazdy w Pensylwanii|nie|
|Func_pesel_identification_number|Wykrywa polski identyfikator narodowy (PESEL, Poland National ID)|nie|
|Func_poland_eu_tax_file_number|Wykrywa numer pliku podatkowego w Polsce|nie|
|Func_polish_national_id|wykrywa kartę tożsamości Polska|nie|
|Func_polish_passport_number|wykrywa polski numer paszportu|nie|
|Func_polish_regon_number|Wykrywa polski numer REGON|nie|
|Func_portugal_eu_tax_file_number|Wykrywa numer identyfikacji podatkowej Portugalia|nie|
|Func_prince_edward_island_drivers_license_number|Wykrywa numer prawa jazdy Wyspy Księcia Edwarda|nie|
|Func_quebec_drivers_license_number|wykrywa numer prawa jazdy w prowincji Quebec|nie|
|Func_randomized_formatted_ssn|Wykrywa losowe sformatowane us SSN|tak|
|Func_randomized_unformatted_ssn|Wykrywa losowe, niesformatowane us SSN|tak|
|Func_rhode_island_drivers_license_number|Wykrywa numer prawa jazdy firmy Rhode Island|nie|
|Func_romania_eu_national_id_card|Wykrywa osobisty kod numeryczny Rumunii (CNP)|nie|
|Func_saskatchewan_drivers_license_number|Wykrywa numer prawa jazdy Saskatchewan|nie|
|Func_slovakia_eu_national_id_card|Wykrywa numer osobisty Słowacja|nie|
|Func_slovenia_eu_national_id_card|Wykrywa unikatowy numer wzorca dla słowenii|nie|
|Func_slovenia_eu_tax_file_number|Wykrywa numer pliku podatkowego w Słowenii|nie|
|Func_south_africa_identification_number|Wykrywa numer identyfikacyjny Republika Południowej Afryki|tak|
|Func_south_carolina_drivers_license_number|Wykrywa numer prawa jazdy w Karolinie Południowej|nie|
|Func_south_dakota_drivers_license_number|Wykrywa numer prawa jazdy z South Korea|nie|
|Func_south_korea_resident_number|Wykrywa numer rezydenta Korei Południowej|nie|
|Func_spain_eu_DL_and_NI_number_citizen|wykrywa liczbę dl i NI Hiszpanii|nie|
|Func_spain_eu_DL_and_NI_number_foreigner|Wykrywa obcokrajowiec liczb z listą dystrybucyjną i NI Hiszpanii|nie|
|Func_spain_eu_driver s_license_number|wykrywa numer prawa jazdy Hiszpanii|nie|
|Func_spain_eu_tax_file_number|wykrywa numer pliku podatkowego Hiszpanii|nie|
|Func_spanish_social_security_number|Wykrywa hiszpański numer PE PEZET.|nie|
|Func_ssn|Funkcja wykrywa nie randomizowana SSN w nie randomizowanym formacie|tak|
|Func_sweden_eu_tax_file_number|Wykrywa numer pliku podatkowego w Szwecja|nie|
|Func_swedish_national_identifier|wykrywa szwedzki identyfikator narodowy|tak|
|Func_swiss_social_security_number_ahv|wykrywa numer SG WIG w Szwajcarii|nie|
|Func_taiwanese_national_id|wykrywa identyfikator narodowy Tajwanu|nie|
|Func_tennessee_drivers_license_number|Wykrywa numer prawa jazdy|nie|
|Func_texas_drivers_license_number|wykrywa numer prawa jazdy w Teksasie|nie|
|Func_Thai_Citizen_Id|Wykrywa identyfikator dla języka tajskiego|nie|
|Func_Turkish_National_Id|wykrywa turecki identyfikator narodowy|tak|
|Func_uk_drivers_license|wykrywa prawo jazdy Wielkiej Brytanii|nie|
|Func_uk_eu_tax_file_number|wykrywa unikatowy numer podatkowej w Wielkiej Brytanii|nie|
|Func_uk_nhs_number|Wykrywa numer NHS Zjednoczonego Królestwa.|tak|
|Func_uk_nino|wykrywa nino zjednoczonego królestwa|nie|
|Func_unformatted_canadian_sin|wykrywa niesformatowany kanadyjski sin|nie|
|Func_unformatted_itin|wykrywa niesformatowany us ITIN|tak|
|Func_unformatted_ssn|wykrywa nie randomizowane, niesformatowane us SSN|tak|
|Func_usa_uk_passport|wykrywa paszport Usa i ZjednoczoneGo Królestwa|tak|
|Func_utah_drivers_license_number|Wykrywa numer prawa jazdy w Utah|nie|
|Func_vermont_drivers_license_number|Wykrywa numer prawa jazdy w Vermont|nie|
|Func_virginia_drivers_license_number|Wykrywa numer prawa jazdy w Virginii|nie|
|Func_washington_drivers_license_number|Wykrywa numer prawa jazdy z Waszyngton|nie|
|Func_west_virginia_drivers_license_number|Wykrywa numer prawa jazdy w Virginii Zachodniej|nie|
|Func_wisconsin_drivers_license_number|Wykrywa numer prawa jazdy w wisconsin|nie|
|Func_wyoming_drivers_license_number|wykrywa numer prawa jazdy w programie Wyoming|nie|

## <a name="func_us_date"></a>Func_us_date

Func_us_date daty w popularnych amerykańskich formatach. Typowe formaty to: "miesiąc/dzień/rok", "miesiąc-dzień-rok" i "rok miesiąca". W nazwach i skrótach miesięcy nie jest w nich wróżniana wielkość liter.

Przykłady:

- 2 grudnia 2016 r.
- 2 grudnia 2016 r.
- 2016-02-02
- 12/2/2016
- 12/02/16
- 2 grudnia 2016 r.
- 12-2-16

Zaakceptowane nazwy miesięcy:

- English
  - Styczeń, luty, marzec, kwiecień, maj, czerwiec, lipiec, sierpień, wrzesień, październik, listopad, grudzień
  - sty. lut. kwi. maj czerwiec lipiec sie. wrze. paź nov. gru.

## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates wyszukuje daty we wspólnej Polsce (i większość miejsc poza Stanami Zjednoczonych), na przykład "dzień/miesiąc/rok", "dzień-miesiąc-rok" i "dzień-miesiąc-rok" oraz "dzień w miesiącu". W nazwach i skrótach miesięcy nie jest w nich wróżniana wielkość liter.

Przykłady:

- 2 grudnia 2016 r.
- 2 grudnia 2016 r.
- 2 grudnia 16
- 2/12/2016
- 02/12/16
- 2 grudnia 2016 r.
- 2-12-16

Zaakceptowane nazwy miesięcy:

- English
  - Styczeń, luty, marzec, kwiecień, maj, czerwiec, lipiec, sierpień, wrzesień, październik, listopad, grudzień
  - sty. lut. kwi. maj czerwiec lipiec sie. wrze. paź nov. gru.
- Dutch
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, October, November, December
  - jan feb maart apr mei jun lip aug sep sept oct okt nov dec
- French
  - janvier, février, mars, av av, mai, juin juillet, aobrowt, septembre, octobre, novembre, décembre
  - janv. févr. mars avique mai juin juil. ao wrze. paź. lis. déc.
- German
  - jänuar, februar, märz, April, mai, juni juli, August, September, oktober, November, dezember
  - Sty./Jän. Lut. März Apr. Mai Juni Juli Aug. Sept. Okt. Lis. Dez.
- Italian
  - gennaio, febbraio, marzo, aprile, malio, giugno, luglio, agosto, settembre, bre, novembre, dicembre
  - genn. lut. mar. kwi. magg. giugno luglio ag. ustaw. ott. lis. dic.
- Portugalski
  - janeiro, rioeiro, março, abc, abdio, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul ago set out nov dez
- Spanish
  - enero, febrero, marzo, ablio, mayo, junio, julio, agosto, septiembre, octubre, noviembre, diciembre
  - enero feb. marzo abr. majo cze. lip. agosto sept./set. paź. lis. dic.

## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (przestarzałe)

> [!NOTE]
> Ta funkcja jest przestarzała, ponieważ obsługuje tylko portugalskie nazwy miesięcy, które są teraz zawarte w funkcji  `Func_eu_date` powyżej.

Ta funkcja wyszukuje datę w formacie często używanym w języku portugalskim. Format tej funkcji jest taki sam, jak format  `Func_eu_date`, różni się tylko w używanym języku.

Przykłady:

- 2 dez 2016
- 2016-02-dez
- 2 dez 16
- 2/12/2016
- 02/12/16
- 2-Dez-2016
- 2-12-16

Zaakceptowane nazwy miesięcy:

- Portugalski
  - janeiro, rioeiro, março, abc, abdio, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul ago set out nov dez

## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (przestarzałe)

> [!NOTE]
> Ta funkcja jest przestarzała, ponieważ obsługuje tylko nazwy miesięcy w języku holenderskim, które są teraz zawarte w powyższej  `Func_eu_date` funkcji.

Ta funkcja wyszukuje datę w formacie używanym w języku holenderskim. Format tej funkcji jest taki sam, jak format  `Func_eu_date`, różni się tylko w używanym języku.

Przykłady:

- 2 Mei 2016
- 02 mei 2016
- 2 Mei 16
- 2/12/2016
- 02/12/16
- 2.Mei-2016
- 2-12-16

Zaakceptowane nazwy miesięcy:

- Dutch
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, October, November, December
  - jan feb maart apr mei jun lip aug sep sept out okt nov dec

## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date wyszukuje daty w formatach używanych przez karty kredytowe i debetowe. Ta funkcja będzie dorównać datami w formacie "miesiąc/rok", "miesiąc-rok", "[nazwa miesiąca] roku" i "[skrót miesiąca] roku". W nazwach i skrótach miesięcy nie jest w nich wróżniana wielkość liter.

Przykłady:

- MM/YYY — na przykład 01/11 lub 1/11
- MM/YYYY — na przykład 2011-01-01 lub 2011-01-01
- MM-YY — na przykład 01-22 lub 1-11
- MM-YYYY — na przykład 01-2000 lub 1-2000

Następujące formaty obsługują format YYY lub YYYY:

- Miesiąc YYYY — na przykład sty 2010, 1 stycznia 2010 lub 10 stycznia 2010
- Miesiąc YYYY — na przykład "styczeń 2010" lub "sty 2010" albo "10 stycznia" lub "10 stycznia"
- MonthYYY — na przykład "styczeń2010" lub "sty 2010" albo "styczeń10" lub "sty 10"
- Miesiąc/YYYY — na przykład "styczeń/2010" lub "sty 2010" albo "10-sty" lub "sty 10"

Zaakceptowane nazwy miesięcy:

- English
  - Styczeń, luty, marzec, kwiecień, maj, czerwiec, lipiec, sierpień, wrzesień, październik, listopad, grudzień
  - sty mar kwi maj czerwiec sie września paź lis gru

## <a name="func_us_address"></a>Func_us_address

Func_us_address szuka nazwy województwa (lub skrótu pocztowego), po którym następuje prawidłowy kod pocztowy. Kod pocztowy musi być jednym z prawidłowych kodów pocztowych skojarzonych z nazwą województwa amerykańskiego lub skrótem. Nie można rozdzielić amerykańskiej nazwy województwa i kodu pocztowego znakami interpunkcji ani liter.

Przykłady:

- Waszyngton 98052
- Washington 98052-9998
- WA 98052
- WA 98052-9998
