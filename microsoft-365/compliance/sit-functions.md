---
title: Funkcje typu informacji poufnych
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
description: Dowiedz się, czego szukają funkcje typów informacji poufnych.
ms.openlocfilehash: 7c2ce289cab93e4a0491cbf13379c169a01e7fbf
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760256"
---
# <a name="sensitive-information-type-functions"></a>Funkcje typu informacji poufnych

Typy informacji poufnych (SIT) mogą używać funkcji jako elementów podstawowych do identyfikowania poufnych elementów. Na przykład typ informacji poufnych Numer karty kredytowej używa funkcji Func_credit_card do wykrywania numeru karty kredytowej.

W tym artykule wyjaśniono, czego szukają te funkcje, aby ułatwić zrozumienie sposobu działania wstępnie zdefiniowanych typów informacji poufnych. Aby uzyskać więcej informacji, zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md)

## <a name="table-of-functions"></a>Tabela funkcji

|Nazwa funkcji | Akcja funkcji | Jest walidatorem|
|---------|----------|---------|
|Func_aba_routing|wykrywa numer routingu ABA|Tak|
|Func_alabama_drivers_license_number|wykrywa numer prawa jazdy w Alabamie|Nr|
|Func_alaska_delaware_oregon_drivers_license_number|wykrywa Alaska, Delaware, Oregon numer prawa jazdy|Nr|
|Func_alaska_drivers_license_number|wykrywa numer prawa jazdy alaski|Nr|
|Func_alberta_drivers_license_number|wykrywa numer prawa jazdy Alberta|Nr|
|Func_argentina_Unique_Tax_Key|wykrywa i weryfikuje Argentyna Unikatowy klucz podatkowy|Nr|
|Func_Argentina_Unique_Tax_Key|wykrywa Argentyna Unikatowy klucz podatkowy|Nr|
|Func_arizona_drivers_license_number|wykrywa numer prawa jazdy Arizona|Nr|
|Func_arkansas_drivers_license_number|wykrywa numer prawa jazdy arkansas|Nr|
|Func_australian_business_number|wykrywa numer biznesowy Australii|Nr|
|Func_Australian_Company_Number|wykrywa numer firmy w Australii|Nr|
|Func_australian_medical_account_number|wykrywa numer konta medycznego w Australii|Nr|
|Func_australian_tax_file_number|wykrywa numer pliku podatkowego Australii|Tak|
|Func_austria_eu_ssn_or_equivalent|wykrywa numer ubezpieczenia społecznego Austrii|Nr|
|Func_austria_eu_tax_file_number|wykrywa numer pliku podatkowego Austrii|Nr|
|Func_Austria_Value_Added_Tax|wykrywa podatek od wartości dodanej w Austrii|Nr|
|Func_belgium_national_number|wykrywa numer krajowy Belgii|Nr|
|Func_belgium_value_added_tax_number|wykrywa belgijski numer podatku od wartości dodanej|Nr|
|Func_brazil_cnpj|wykrywa numer brazylijskiej jednostki prawnej (CNPJ)|Tak|
|Func_brazil_cpf|wykrywa Brazylia CPF|Tak|
|Func_brazil_rg|wykrywa brazylijskie RG|Nr|
|Func_british_columbia_drivers_license_number|wykrywa numer prawa jazdy w Kolumbii Brytyjskiej|Nr|
|Func_bulgaria_eu_national_id_card|wykrywa jednolity numer cywilny Bułgarii|Nr|
|Func_california_drivers_license_number|wykrywa numer prawa jazdy w Kalifornii|Nr|
|Func_canadian_sin|wykrywa grzech Kanady|Tak|
|Func_chile_id_card|wykrywa dowód osobisty Chile|Nr|
|Func_china_resident_id|wykrywa identyfikator rezydenta Chin|Nr|
|Func_colorado_drivers_license_number|wykrywa numer prawa jazdy colorado|Nr|
|Func_connecticut_drivers_license_number|wykrywa numer prawa jazdy connecticut|Nr|
|Func_credit_card|wykrywa kartę kredytową|Tak|
|Func_croatia_id_card|wykrywa chorwacki identyfikator|Nr|
|Func_croatia_oib_number|wykrywa numer OIB Chorwacji|Nr|
|Func_cyprus_eu_tax_file_number|wykrywa numer pliku podatkowego cypryjskiego|Nr|
|Func_czech_id_card_new_format|wykrywa czeski identyfikator w nowym formacie|Nr|
|Func_czech_id_card|wykrywa czeski identyfikator|Nr|
|Func_dea_number|wykrywa numer DEA|Tak|
|Func_denmark_eu_tax_file_number|wykrywa osobisty numer identyfikacyjny Danii|Nr|
|Func_district_of_columbia_drivers_license_number|wykrywa numer prawa jazdy District of Columbia|Nr|
|Func_estonia_eu_national_id_card|wykrywa estoński kod identyfikacji osobistej|Nr|
|Func_eu_debit_card|wykrywa kartę debetową UE|Nr|
|Func_finnish_national_id|wykrywa fiński identyfikator krajowy|Nr|
|Func_florida_drivers_license_number|wykrywa numer prawa jazdy na Florydzie|Nr|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|wykrywa Florida, Maryland, Michigan, Minnesota numer prawa jazdy|Nr|
|Func_formatted_itin|wykrywa sformatowaną amerykańską itinę|Tak|
|Func_fr_insee|wykrywa Francja INSEE|Nr|
|Func_fr_passport|wykrywa paszport Francji|Nr|
|Func_france_eu_tax_file_number|wykrywa numer pliku podatkowego Francja|Nr|
|Func_france_value_added_tax_number|wykrywa numer podatku od wartości dodanej we Francji|Nr|
|Func_french_drivers_license|wykrywa francuskie prawo jazdy|Nr|
|Func_french_insee|wykrywa francuski system INSEE|Nr|
|Func_georgia_drivers_license_number|wykrywa numer prawa jazdy w Gruzji|Nr|
|Func_german_drivers_license|wykrywa niemieckie prawo jazdy|Nr|
|Func_german_passport_data|wykrywa niemiecki paszport|Nr|
|Func_german_passport|wykrywa niemiecki paszport|Nr|
|Func_germany_eu_tax_file_number|wykrywa numer pliku podatkowego w Niemczech|Nr|
|Func_germany_value_added_tax_number|wykrywa niemiecki numer podatku od wartości dodanej|Nr|
|Func_greece_eu_ssn|wykrywa grzech Grecji (AMKA)|Nr|
|Func_hawaii_drivers_license_number|wykrywa numer prawa jazdy hawajskiego|Nr|
|Func_hong_kong_id_card|wykrywa kartę identyfikatora Hongkongu|Nr|
|Func_hungarian_value_added_tax_number|wykrywa węgierski numer podatku od wartości dodanej|Nr|
|Func_hungary_eu_national_id_card|wykrywa węgierski osobisty numer identyfikacyjny|Nr|
|Func_hungary_eu_ssn_or_equivalent|wykrywa węgierski numer ubezpieczenia społecznego|Nr|
|Func_hungary_eu_tax_file_number|wykrywa numer pliku podatkowego Węgry|Nr|
|Func_iban|wykrywa IBAN|Tak|
|Func_idaho_drivers_license_number|wykrywa numer prawa jazdy idaho|Nr|
|Func_illinois_drivers_license_number|wykrywa numer prawa jazdy w stanie Illinois|Nr|
|Func_india_aadhaar|wykrywa aadhaar Indii|Tak|
|Func_indiana_drivers_license_number|wykrywa numer prawa jazdy indiana|Nr|
|Func_iowa_drivers_license_number|wykrywa numer prawa jazdy w stanie Iowa|Nr|
|Func_ireland_pps|wykrywa Irlandia PPS|Nr|
|Func_israeli_national_id_number|wykrywa krajowy numer ID Izraela|Nr|
|Func_italy_eu_national_id_card|wykrywa kod fiskalny Włoch|Nr|
|Func_italy_value_added_tax_number|wykrywa włoski numer podatku od wartości dodanej|Nr|
|Func_japanese_my_number_corporate|wykrywa Japonii mój numer firmowy|Tak|
|Func_japanese_my_number_personal|wykrywa Japonii mój numer osobisty|Tak|
|Func_jp_bank_account_branch_code|wykrywa kod gałęzi konta bankowego w Japonii|Nr|
|Func_jp_bank_account|wykrywa konto bankowe Japonii|Nr|
|Func_jp_drivers_license_number|wykrywa japoński numer prawa jazdy|Nr|
|Func_jp_passport|wykrywa paszport Japonii|Nr|
|Func_jp_resident_registration_number|wykrywa numer rejestracyjny rezydenta Japonii|Nr|
|Func_jp_sin_pre_1997|wykrywa grzech Japonii przed 1997|Nr|
|Func_jp_sin|wykrywa Japan SIN|Nr|
|Func_kansas_drivers_license_number|wykrywa numer prawa jazdy Kansas|Nr|
|Func_kentucky_drivers_license_number|wykrywa numer prawa jazdy kentucky|Nr|
|Func_kentucky_massachusetts_virginia_drivers_license_number|wykrywa numer prawa jazdy kentucky, Massachusetts, Virginia|Nr|
|Func_latvia_eu_national_id_card|wykrywa kod osobisty łotwy|Nr|
|Func_lithuania_eu_tax_file_number|wykrywa kod osobisty Litwy|Nr|
|Func_louisiana_drivers_license_number|wykrywa numer prawa jazdy w Luizjanie|Nr|
|Func_luxemburg_eu_tax_file_number_non_natural|wykrywa luksemburski krajowy numer identyfikacyjny (osoby niebędące osobami fizycznymi)|Nr|
|Func_luxemburg_eu_tax_file_number|wykrywa luksemburski krajowy numer identyfikacyjny (osoby fizyczne)|Nr|
|Func_maine_drivers_license_number|wykrywa numer prawa jazdy maine|Nr|
|Func_manitoba_drivers_license_number|wykrywa numer prawa jazdy Manitoba|Nr|
|Func_maryland_drivers_license_number|wykrywa numer prawa jazdy maryland|Nr|
|Func_massachusetts_drivers_license_number|wykrywa numer prawa jazdy massachusetts|Nr|
|Func_mexico_population_registry_code|wykrywa kod rejestru populacji Meksyku|Nr|
|Func_michigan_minnesota_drivers_license_number|wykrywa Michigan, Minnesota numer prawa jazdy|Nr|
|Func_minnesota_drivers_license_number|wykrywa numer prawa jazdy minnesoty|Nr|
|Func_mississippi_oklahoma_drivers_license_number|wykrywa Missisipi, numer prawa jazdy Oklahoma|Nr|
|Func_missouri_drivers_license_number|wykrywa numer prawa jazdy w stanie Missouri|Nr|
|Func_montana_drivers_license_number|wykrywa numer prawa jazdy montana|Nr|
|Func_nebraska_drivers_license_number|wykrywa numer prawa jazdy Nebraska|Nr|
|Func_netherlands_bsn|wykrywa holenderska nazwa BSN|Nr|
|Func_netherlands_eu_tax_file_number|wykrywa numer holenderskiego pliku podatkowego|Nr|
|Func_netherlands_value_added_tax_number|wykrywa holenderski numer podatku od wartości dodanej|Nr|
|Func_nevada_drivers_license_number|wykrywa numer prawa jazdy w Nevadzie|Nr|
|Func_new_brunswick_drivers_license_number|wykrywa numer prawa jazdy w Nowym Brunszwiku|Nr|
|Func_new_hampshire_drivers_license_number|wykrywa numer prawa jazdy w New Hampshire|Nr|
|Func_new_jersey_drivers_license_number|wykrywa numer prawa jazdy w New Jersey|Nr|
|Func_new_mexico_drivers_license_number|wykrywa numer prawa jazdy w Nowym Meksyku|Nr|
|Func_new_york_drivers_license_number|wykrywa numer prawa jazdy w Nowym Jorku|Nr|
|Func_new_zealand_bank_account_number|wykrywa numer konta bankowego Nowej Zelandii|Nr|
|Func_new_zealand_inland_revenue_number|wykrywa numer przychodu w głębi lądu w Nowej Zelandii|Nr|
|Func_new_zealand_ministry_of_health_number|wykrywa numer służby zdrowia Nowej Zelandii|Nr|
|Func_newfoundland_labrador_drivers_license_number|wykrywa numer prawa jazdy Labradora z Nowej Fundlandii|Nr|
|Func_newzealand_driver_license_number|wykrywa numer prawa jazdy w Nowej Zelandii|Nr|
|Func_newzealand_social_welfare_number|wykrywa numer opieki społecznej w Nowej Zelandii|Nr|
|Func_north_carolina_drivers_license_number|wykrywa numer prawa jazdy w Karolinie Północnej|Nr|
|Func_north_dakota_drivers_license_number|wykrywa numer prawa jazdy w Dakocie Północnej|Nr|
|Func_norway_id_number|wykrywa numer identyfikatora Norwegii|Nr|
|Func_nova_scotia_drivers_license_number|wykrywa numer prawa jazdy Nowej Szkocji|Nr|
|Func_ohio_drivers_license_number|wykrywa numer prawa jazdy ohio|Nr|
|Func_ontario_drivers_license_number|wykrywa numer prawa jazdy ontario|Nr|
|Func_pennsylvania_drivers_license_number|wykrywa numer prawa jazdy w Pensylwanii|Nr|
|Func_pesel_identification_number|wykrywa polski identyfikator krajowy (PESEL)|Nr|
|Func_poland_eu_tax_file_number|wykrywa numer pliku podatkowego w Polsce|Nr|
|Func_polish_national_id|wykrywa polski dowód tożsamości|Nr|
|Func_polish_passport_number|wykrywa polski numer paszportu|Nr|
|Func_polish_regon_number|wykrywa polski numer REGON|Nr|
|Func_portugal_eu_tax_file_number|wykrywa numer identyfikacji podatkowej Portugalii|Nr|
|Func_prince_edward_island_drivers_license_number|wykrywa numer prawa jazdy prince Edward Island|Nr|
|Func_quebec_drivers_license_number|wykrywa numer prawa jazdy Quebecu|Nr|
|Func_randomized_formatted_ssn|wykrywa losową sformatowaną amerykańską nazwę SSN|Tak|
|Func_randomized_unformatted_ssn|wykrywa losową, niesformatowaną amerykańską nazwę SSN|Tak|
|Func_rhode_island_drivers_license_number|wykrywa numer prawa jazdy rhode island|Nr|
|Func_romania_eu_national_id_card|wykrywa rumuński osobisty kod liczbowy (CNP)|Nr|
|Func_saskatchewan_drivers_license_number|wykrywa numer prawa jazdy Saskatchewan|Nr|
|Func_slovakia_eu_national_id_card|wykrywa numer osobisty Słowacji|Nr|
|Func_slovenia_eu_national_id_card|wykrywa słoweński unikatowy numer obywatela głównego|Nr|
|Func_slovenia_eu_tax_file_number|wykrywa numer pliku podatkowego Słowenii|Nr|
|Func_south_africa_identification_number|wykrywa numer identyfikacyjny RPA|Tak|
|Func_south_carolina_drivers_license_number|wykrywa numer prawa jazdy w Karolinie Południowej|Nr|
|Func_south_dakota_drivers_license_number|wykrywa numer prawa jazdy w Dakocie Południowej|Nr|
|Func_south_korea_resident_number|wykrywa numer rezydenta Korei Południowej|Nr|
|Func_spain_eu_DL_and_NI_number_citizen|wykrywa hiszpanii DL i ni numer obywatela|Nr|
|Func_spain_eu_DL_and_NI_number_foreigner|wykrywa hiszpanię DL i numer ni cudzoziemca|Nr|
|s_license_number Func_spain_eu_driver|wykrywa numer prawa jazdy w Hiszpanii|Nr|
|Func_spain_eu_tax_file_number|wykrywa numer pliku podatkowego Hiszpanii|Nr|
|Func_spanish_social_security_number|wykrywa hiszpański numer ubezpieczenia społecznego|Nr|
|Func_ssn|Funkcja wykrywania nie randomizowanych sformatowanych sformatowanych nazw SSN USA|Tak|
|Func_sweden_eu_tax_file_number|wykrywa numer pliku podatkowego Szwecji|Nr|
|Func_swedish_national_identifier|wykrywa szwedzki identyfikator krajowy|Tak|
|Func_swiss_social_security_number_ahv|wykrywa szwajcarski numer ubezpieczenia społecznego AHV|Nr|
|Func_taiwanese_national_id|wykrywa tajwański identyfikator krajowy|Nr|
|Func_tennessee_drivers_license_number|wykrywa numer prawa jazdy tennessee|Nr|
|Func_texas_drivers_license_number|wykrywa numer prawa jazdy w Teksasie|Nr|
|Func_Thai_Citizen_Id|wykrywa identyfikator obywatela tajlandii|Nr|
|Func_Turkish_National_Id|wykrywa identyfikator kraju tureckiego|Tak|
|Func_uk_drivers_license|wykrywa prawo jazdy w Wielkiej Brytanii|Nr|
|Func_uk_eu_tax_file_number|wykrywa unikatowy numer podatnika w Wielkiej Brytanii|Nr|
|Func_uk_nhs_number|wykrywa numer UK NHS|Tak|
|Func_uk_nino|wykrywa UK NINO|Nr|
|Func_unformatted_canadian_sin|wykrywa niesformatowany kanadyjski sin|Nr|
|Func_unformatted_itin|wykrywa niesformatowaną amerykańską itinę|Tak|
|Func_unformatted_ssn|wykrywa nieformatowaną, niesformatowaną nazwę SSN STANÓW Zjednoczonych|Tak|
|Func_usa_uk_passport|wykrywa paszport STANÓW Zjednoczonych i Wielkiej Brytanii|Tak|
|Func_utah_drivers_license_number|wykrywa numer prawa jazdy utah|Nr|
|Func_vermont_drivers_license_number|wykrywa numer prawa jazdy vermont|Nr|
|Func_virginia_drivers_license_number|wykrywa numer prawa jazdy Virginia|Nr|
|Func_washington_drivers_license_number|wykrywa numer prawa jazdy Washingtona|Nr|
|Func_west_virginia_drivers_license_number|wykrywa numer prawa jazdy w Wirginii Zachodniej|Nr|
|Func_wisconsin_drivers_license_number|wykrywa numer prawa jazdy wisconsin|Nr|
|Func_wyoming_drivers_license_number|wykrywa numer prawa jazdy w Wyoming|Nr|

## <a name="func_us_date"></a>Func_us_date

Func_us_date szuka dat w popularnych formatach amerykańskich. Typowe formaty to "month/day/year", "month-day-year" i "month day year". Nazwy lub skróty miesięcy nie uwzględniają wielkości liter.

Przykłady:

- 2 grudnia 2016 r.
- 2 grudnia 2016 r.
- grudzień 02 2016
- 12/2/2016
- 12/02/16
- Grudzień 2-2016
- 12-2-16

Akceptowane nazwy miesięcy:

- English
  - Styczeń, luty, marzec, kwiecień, maj, czerwiec, lipiec, sierpień, wrzesień, październik, listopad, grudzień
  - Jan. Luty mar kwi maja czerwca lipca sie września października listopada grudnia.

## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates szuka dat w typowych E.U. formaty (i większość miejsc spoza Stanów Zjednoczonych), takie jak "dzień/miesiąc/rok", "dzień-miesiąc-rok" i "rok miesiąca dziennego". Nazwy lub skróty miesięcy nie uwzględniają wielkości liter.

Przykłady:

- 2 grudnia 2016 r.
- 02 grudnia 2016 r.
- 2 Grudnia 16
- 2/12/2016
- 02/12/16
- 2 grudnia 2016 r.
- 2-12-16

Akceptowane nazwy miesięcy:

- English
  - Styczeń, luty, marzec, kwiecień, maj, czerwiec, lipiec, sierpień, wrzesień, październik, listopad, grudzień
  - Jan. Luty mar kwi maja czerwca lipca sie września października listopada grudnia.
- Dutch
  - januari, februari, maart, april, mei, juni, juli, augustus, wrzesień, ocktober, październik, listopad, grudzień
  - jan feb maart apr mei jun jul aug sep sept oct okt nov dec
- French
  - janvier, février, mars, avril, mai, juin juillet, août, septembre, octobre, novembre, décembre
  - janv. févr. mars avril mai juin juil. août września. Października. Listopada. déc.
- German
  - jänuar, februar, märz, kwiecień, mai, juni juli, sierpień, wrzesień, oktober, listopad, dezember
  - Jan./Jän. Luty März Kwi Mai Juni Juli sie września Okt. Listopad Dez.
- Italian
  - gennaio, febbraio, marzo, aprile, maggio, giugno, luglio, agosto, settembre, ottobre, novembre, dicembre
  - Genn. febbr. Mar. Kwiecień. magg. giugno luglio ag. Brukowana. Ott. Listopada. Dic.
- Portugalski
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul temu określone nov dez
- Spanish
  - enero, febrero, marzo, abril, mayo, junio, julio, agosto, septiembre, octubre, noviembre, diciembre
  - enero lutego. marzo abr. mayo jun. Lip. agosto sept./set. Października. Listopada. Dic.

## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (przestarzałe)

> [!NOTE]
> Ta funkcja jest przestarzała, ponieważ obsługuje tylko nazwy portugalskich miesięcy, które są teraz zawarte w  `Func_eu_date` powyższej funkcji.

Ta funkcja szuka daty w formacie powszechnie używanym w języku portugalskim. Format tej funkcji jest taki sam jak  `Func_eu_date`, różni się tylko w używanym języku.

Przykłady:

- 2 Dez 2016
- 02 dez 2016
- 2 Dez 16
- 2/12/2016
- 02/12/16
- 2-Dez-2016
- 2-12-16

Akceptowane nazwy miesięcy:

- Portugalski
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul temu określone nov dez

## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (przestarzałe)

> [!NOTE]
> Ta funkcja jest przestarzała, ponieważ obsługuje tylko nazwy miesięcy holenderskich, które są teraz uwzględnione w  `Func_eu_date` powyższej funkcji.

Ta funkcja szuka daty w formacie powszechnie używanym w języku niderlandzkim. Format tej funkcji jest taki sam jak  `Func_eu_date`, różni się tylko w używanym języku.

Przykłady:

- 2 Mei 2016
- 02 mei 2016
- 2 Mei 16
- 2/12/2016
- 02/12/16
- 2-Mei-2016
- 2-12-16

Akceptowane nazwy miesięcy:

- Dutch
  - januari, februari, maart, april, mei, juni, juli, augustus, wrzesień, ocktober, październik, listopad, grudzień
  - jan feb maart apr mei jun jul aug sep sept out okt nov dec

## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date szuka dat, które są w formatach często używanych przez karty kredytowe i debetowe. Ta funkcja będzie zgodna z datami w formacie "miesiąc/rok", "miesiąc-rok", "[nazwa miesiąca] rok" i "[skrót miesiąca] rok". Nazwy lub skróty miesięcy nie uwzględniają wielkości liter.

Przykłady:

- MM/RR — na przykład 01/11 lub 1/11
- MM/RRRR — na przykład 01/2011 lub 1/2011
- MM-YY — na przykład 01-22 lub 1-11
- MM-RRRR — na przykład 01-2000 lub 1-2000

Następujące formaty obsługują RR lub RRRR:

- Miesiąc-RRRR — na przykład styczeń-2010 r. lub styczeń-2010 r., 10 stycznia lub 10 stycznia
- Miesiąc RRRR — na przykład "styczeń 2010" lub "Styczeń 2010" lub "10 stycznia" lub "10 stycznia"
- MonthYYYY — na przykład "january2010" lub "Jan2010" lub "january10" lub "Jan10"
- Miesiąc/RRRR — na przykład "styczeń/2010" lub "Styczeń/2010" lub "styczeń/10" lub "Styczeń/10"

Akceptowane nazwy miesięcy:

- English
  - Styczeń, luty, marzec, kwiecień, maj, czerwiec, lipiec, sierpień, wrzesień, październik, listopad, grudzień
  - Styczeń luty mar kwi może czerwiec lipiec sierpień wrzesień październik listopada grudzień

## <a name="func_us_address"></a>Func_us_address

Func_us_address szuka nazwy stanu USA lub skrótu pocztowego, po którym następuje prawidłowy kod pocztowy. Kod pocztowy musi być jednym z prawidłowych kodów pocztowych skojarzonych z nazwą lub skrótem stanu USA. Nazwy stanu Usa i kodu pocztowego nie można rozdzielić znakiem interpunkcyjnym ani literami.

Przykłady:

- Waszyngton 98052
- Waszyngton 98052-9998
- WA 98052
- WA 98052-9998
