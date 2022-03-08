---
title: Porady dotyczące zasad ochrony przed utratą danych
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
recommendations: false
description: Dowiedz się, jak dodać poradę o zasadach do zasad ochrony przed utratą danych (DLP, Data Loss Prevention) i poinformować użytkowników, że pracują oni z zawartością, która powoduje konflikty z zasadami DLP.
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 52bb2fba47c5588dc6a44eb5f8e1d7b745e69e70
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319381"
---
# <a name="data-loss-prevention-policy-tips-reference"></a>Porady dotyczące zasad ochrony przed utratą danych

Porady dotyczące zasad DLP w programie Outlook Web Access są obsługiwane dla wszystkich warunków, wyjątków i akcji mających zastosowanie do obciążenia pracą usługi Exchange w zasadach DLP z wyjątkiem następujących:

**Warunki:**

- Adresat jest członkiem
- Nagłówek zawiera wyrazy lub frazy
- Nagłówek odpowiada wzorcom
- Typ wiadomości to
- Zestaw znaków zawartości zawiera wyrazy
- Czy nadawca zastąpić poradę o zasadach
- Rozmiar wiadomości jest równy lub większy niż
- Atrybut AD nadawcy zawiera wyrazy lub frazy
- Atrybut Sender AD jest dosyć do wzorców
- Zakresy adresów IP nadawców
- Atrybut AD adresata zawiera wyrazy lub frazy
- Atrybut ad adresata jest do dopasowania wzorców
- Nazwa dokumentu zawiera wyrazy lub frazy
- Nazwa dokumentu pasuje do wzorców
- Zawartość dokumentu zawiera wyrazy lub frazy
- Zawartość dokumentu jest do dopasowania do wzorców

**Akcje:**

- Przesyłanie wiadomości dalej do zatwierdzenia do menedżera nadawcy
- Przesyłanie wiadomości do zatwierdzenia określonym zatwierdzającym
- Przekierowywanie wiadomości do konkretnych użytkowników
- Dodawanie adresatów do pola Do
- Dodawanie adresatów do pola DW
- Dodawanie adresatów do pola UDW
- Dodawanie menedżera nadawcy jako adresata
- Dodawanie zastrzeżenia w formacie HTML
- Przedimek tematu wiadomości e-mail
- Usuwanie szyfrowania wiadomości usługi O365 i ochrony praw

## <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions"></a>Outlook 2013 i nowszych obsługuje wyświetlanie porad dotyczących zasad tylko dla niektórych warunków i wyjątków

Obecnie program Outlook 2013 i nowsze obsługuje wyświetlanie porad dotyczących zasad dotyczących zasad, które nie zawierają żadnych warunków ani wyjątków oprócz wymienionych poniżej warunków i odpowiadających im wyjątków:

- Zawartość zawiera (działa tylko w przypadku typów informacji poufnych. Etykiety wrażliwości nie są obsługiwane)
- Zawartość jest udostępniana

Pamiętaj, że wszystkie warunki działają w przypadku wiadomości e-mail Outlook w aplikacji klienckiej, gdzie będą one do siebie do siebie dorównać i wymuszać akcje zabezpieczające przed zawartością. Jednak pokazywanie użytkownikom porad dotyczących zasad nie jest obsługiwane w przypadku jakichkolwiek warunków, które są używane poza warunkami wymienionymi powyżej.

## <a name="outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types"></a>Outlook 2013 i nowsze oraz aplikacje Office na komputerze stacjonarnym z poradami dotyczącymi zasad dotyczącymi tylko niektórych typów informacji poufnych

Lista typów informacji poufnych, które są wykrywane w celu wyświetlania porad dotyczących zasad DLP w programie Outlook w wersji klasycznej (2013 i nowszej) oraz w aplikacjach Office (Word, Excel, PowerPoint) na komputerze stacjonarnym są następujące:

- Numer routingu ABA
- Argentina National Identity (DNI) Number
- Numer konta bankowego w Australii
- Numer konta medycznego w Australii
- Numer paszportu Australii
- Numer pliku podatkowego w Australii
- Klucz uwierzytelniania dokumentu Azure DocumentDB  
- Azure IAAS Database Connection String and Azure SQL Connection String  
- Azure IoT Connection String  
- Azure Publish Setting Password  
- Azure Redis Cache Connection String  
- Azure SAS  
- Azure Service Bus Connection String  
- Klucz konta usługi Azure Storage  
- Klucz konta usługi Azure Storage (ogólne)  
- Numer narodowy w Belgia
- Numer CPF w Brazylii
- Numer jednostki prawnej w Brazylii (CNPJ)
- National ID Card (RG) (Brazylia National ID Card)
- Numer konta bankowego w Kanadzie
- Numer prawa jazdy w Kanadzie
- Numer Usługa kondycji Kanada
- Numer paszportu Kanady
- Kanada : numer identyfikacyjny zdrowia osobistego (PHIN)
- Numer ubezpieczenia społecznego w Kanadzie
- Numer karty tożsamości Chile
- Numer karty tożsamości rezydentnych w Chinach (Chiny)
- Numer karty kredytowej
- Numer karty tożsamości Chorwacja  
- Numer identyfikacyjny OIB (Chorwacja)  
- Czeski numer tożsamości osobistej  
- Dania Osobisty numer identyfikacyjny
- Numer agencji egzekwowania praw osób (DEA)
- Numer karty debetowej UE
- Numer prawa jazdy w UE  
- Krajowy numer identyfikacyjny UE  
- Numer paszportu UE  
- Numer PE PE PE PEŁ lub identyfikator równoważne  
- Numer identyfikacyjny podatku UE (TIN)  
- Finland National ID
- Numer paszportu Finlandia
- Numer prawa jazdy we Francji
- France National ID Card (CNI)
- Numer paszportu Francji
- Numer UBEZPIECZENIA SPOŁECZNEGO we Francji (INSEE)
- Niemiecki numer prawa jazdy
- Numer paszportu niemieckiego
- Numer karty tożsamości w Niemczech
- Karta kredytowa państwowa Grecja  
- Numer karty tożsamości Hongkongu (HKID)
- Numer konta trwałego w Indiach (PAN)
- Unikatowy numer identyfikacyjny w Indiach (Aadhaar)
- Numer karty tożsamości Indonezyjskiej (KTP)
- Numer konta bankowego międzynarodowego (IBAN)
- Klasyfikacja międzynarodowa najbłędszej (ICD-10-CM)  
- Klasyfikacja międzynarodowa najbłędszej (ICD-9-CM)  
- IP Address (Adres IP)
- Numer usługi publicznej w Irlandii (PPS) 
- Izrael Numer konta bankowego
- Identyfikator narodowy Izrael
- Włochy Numer prawa jazdy
- Japan Bank Account Number
- Numer prawa jazdy w Japonii
- Numer paszportu Japonii
- Japoński numer rejestru rezydentny
- Japoński numer ubezpieczenia społecznego (SIN)
- Numer japońskiej karty zamieszkania
- Numer karty tożsamości w Malezji
- Numer usługi holenderskiej (BSN)  
- Nowa Zelandia, Która ma numer zdrowia
- Numer tożsamości w Norwegia  
- Philippines Unified Multi-Purpose ID Number
- Wizytówka w Polsce
- Identyfikator narodowy w Polsce (PESEL)
- Paszport Polski
- Numer karty Wi-Wi-Do
- Arabia Saudyjska
- Numer dowodu tożsamości państwowej w Singapurze (NRIC, National Registration Identity Card)
- Numer identyfikacyjny Republika Południowej Afryki  
- Numer rejestracji rezydenta Korei Południowej
- Hiszpania Numer PE PEŁ(SSN)
- SQL Server parametrów połączenia  
- Identyfikator narodowy Szwecja
- Numer paszportu Szwecja
- Kod SWIFT
- Identyfikator narodowy na Tajwanie
- Numer paszportu na Tajwanie
- Certyfikat rezydentny na Tajwanie (ARC/TARC)
- Kod identyfikacyjny populacji tajskiej
- Numer identyfikacyjny tureckiego numeru identyfikacyjnego
- Zjednoczone Emiraty Zjednoczone Numer prawa jazdy
- Zjednoczone Emiraty Zjednoczone Numer listy adresowej
- Zjednoczone Emiraty Zjednoczone Numer Usługa kondycji państwowej
- Zjednoczone Emiraty Zjednoczone Numer ubezpieczenia państwowego (NINO)
- Stany Zjednoczone Numer paszportu
- Numer konta bankowego w Stanach Zjednoczonych
- Numer prawa jazdy w Stanach Zjednoczonych
- Numer identyfikacyjny identyfikacji indywidualnej (ITIN) Stanów Zjednoczonych
- Numer SSN (U.SSN)

Pamiętaj, że niestandardowe typy informacji poufnych są również obsługiwane w przypadku porad dotyczących zasad DLP, a także powyższych, ważnych typów informacji.

## <a name="data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types"></a>Ochrona przed utratą danych na urządzeniach końcowych obsługuje porady dotyczące zasad tylko dla niektórych typów informacji poufnych

Lista dostępnych typów informacji poufnych, które będą wykrywane w dokumentach znajdujących się na urządzeniach końcowych, są następujące:

- Numer routingu ABA 
- Argentina National Identity (DNI) Number 
- Numer konta bankowego w Australii 
- Numer konta medycznego w Australii 
- Numer paszportu Australii 
- Numer pliku podatkowego w Australii 
- Numer biznesowy w Australii 
- Australijski numer firmy 
- Numer prawa jazdy w Austrii 
- Austria Identity Card 
- Numer paszportu Austrii 
- Austria Social Security Number 
- Austria Tax Identification Number 
- Numer podatku VAT (Austria Value Added Tax) 
- Klucz uwierzytelniania dokumentu Azure DocumentDB 
- Azure IAAS Database Connection String and Azure SQL Connection String 
- Azure IoT Connection String 
- Azure Publish Setting Password 
- Azure Redis Cache Connection String 
- Azure SAS 
- Azure Service Bus Connection String 
- Klucz konta usługi Azure Storage 
- Klucz konta usługi Azure Storage (ogólne) 
- Numer prawa jazdy w Belgia 
- Numer narodowy w Belgia 
- Numer paszportu Belgia 
- Numer podatku dodanego do belgia 
- Numer CPF w Brazylii 
- Numer jednostki prawnej w Brazylii (CNPJ) 
- National ID Card (RG) (Brazylia National ID Card) 
- Numer prawa jazdy w Bułgarii 
- Numer paszportu Bułgarii 
- Bułgaria ( jednolity numer cywilny) 
- Numer konta bankowego w Kanadzie 
- Numer prawa jazdy w Kanadzie 
- Numer Usługa kondycji Kanada 
- Numer paszportu Kanady 
- Kanada : numer identyfikacyjny zdrowia osobistego (PHIN) 
- Numer ubezpieczenia społecznego w Kanadzie 
- Numer karty tożsamości Chile 
- Numer karty tożsamości rezydentnych w Chinach (Chiny) 
- Numer karty kredytowej 
- Numer prawa jazdy Chorwacja 
- Numer karty tożsamości Chorwacja 
- Numer wizytówki państwowej Chorwacja 
- Numer paszportu Chorwacja 
- Numer identyfikacyjny OIB (Chorwacja) 
- CSCAN-AZURE0060 — Storage dostępu udostępnionego konta Azure 
- CSCAN-GENERAL0140 Klucz symetryczny ogólny 
- Numer prawa jazdy Cypru 
- Karta tożsamości cypryjna 
- Numer paszportu Cypru 
- Numer identyfikacji podatkowej Cypru 
- Numer prawa jazdy czeskiego 
- Czeski numer tożsamości osobistej 
- Numer paszportu Czech 
- Dania Numer prawa jazdy 
- Numer paszportu w Danii 
- Dania Osobisty numer identyfikacyjny 
- Numer agencji egzekwowania praw osób (DEA) 
- Estoński numer prawa jazdy 
- Numer paszportu Estońskiego 
- Estonia Personal Identification Code 
- Numer karty debetowej UE 
- Numer prawa jazdy w UE 
- Krajowy numer identyfikacyjny UE 
- Numer paszportu UE 
- Numer PE PE PE PEŁ lub identyfikator równoważne 
- Numer identyfikacyjny podatku UE (TIN) 
- Numer prawa jazdy w Finlandia 
- Fiński numer ubezpieczenia społecznego w Niemczech 
- Finland National ID 
- Numer paszportu Finlandia 
- Numer prawa jazdy we Francji 
- Numer ubezpieczenia społecznego we Francji 
- France National ID Card (CNI) 
- Numer paszportu Francji 
- Numer UBEZPIECZENIA SPOŁECZNEGO we Francji (INSEE) 
- Numer identyfikacji podatkowej Francji (numéro SPI. 
- Numer podatku od wartości dodanej we Francji 
- Niemiecki numer prawa jazdy 
- Numer paszportu niemieckiego 
- Numer karty tożsamości w Niemczech 
- Niemiecki numer identyfikacyjny podatku 
- Numer podatku dodanego w Niemczech 
- Numer prawa jazdy w Grecji 
- Karta kredytowa państwowa Grecja 
- Numer paszportu Grecja 
- Numer PE PEŁ (AMKA) 
- Grecki numer identyfikacyjny podatku 
- Numer karty tożsamości Hongkongu (HKID) 
- Węgierski numer PE PEZ 
- Numer podatku dodanego w języku węgierskim 
- Numer prawa jazdy na Węgry 
- Numer paszportu Węgry 
- Węgry Osobisty numer identyfikacyjny 
- Numer identyfikacji podatkowej Węgry 
- Numer konta trwałego w Indiach (PAN) 
- Unikatowy numer identyfikacyjny w Indiach (Aadhaar) 
- Numer karty tożsamości Indonezyjskiej (KTP) 
- Numer konta bankowego międzynarodowego (IBAN) 
- Klasyfikacja międzynarodowa najbłędszej (ICD-10-CM) 
- Klasyfikacja międzynarodowa najbłędszej (ICD-9-CM) 
- IP Address (Adres IP) 
- Numer prawa jazdy Irlandii 
- Numer paszportu Irlandii 
- Numer usługi publicznej w Irlandii (PPS) 
- Izrael Numer konta bankowego 
- Identyfikator narodowy Izrael 
- Włochy Numer prawa jazdy 
- Kod obrachunkowy Włoch 
- Numer paszportu Włoch 
- Włoski numer podatku od wartości dodanej 
- Japan Bank Account Number 
- Numer prawa jazdy w Japonii 
- Numer paszportu Japonii 
- Japoński numer rejestru rezydentny 
- Japoński numer ubezpieczenia społecznego (SIN) 
- Japoński Mój numer firmowy 
- Japoński mój numer osobisty 
- Numer japońskiej karty zamieszkania 
- Łotewski numer prawa jazdy 
- Numer paszportu Łotwy 
- Kod osobisty Łotwa 
- Litwa Numer prawa jazdy 
- Numer paszportu Litwy 
- Litwa Kod osobisty 
- Luxemburg Driver's License Number 
- Luxemburg National Identification Number (Osoby naturalne) 
- Luxemburg National Identification Number (Osoby nie naturalne) 
- Numer paszportu w Luksemburgu 
- Numer karty tożsamości w Malezji 
- Numer prawa jazdy w Malta 
- Numer karty tożsamości malta 
- Numer paszportu Malta 
- Numer identyfikacyjny podatku Malta 
- Numer usługi holenderskiej (BSN) 
- Holenderski numer prawa jazdy 
- Numer paszportu Holenderskiego 
- Holenderski numer identyfikacyjny podatku 
- Numer podatku od wartości dodanej w Niemczech 
- Numer konta bankowego w Nowej Zelandii 
- Numer prawa jazdy nowej Zelandii 
- Nowa Zelandia (nr przychodu) 
- Nowa Zelandia, Która ma numer zdrowia 
- Numer nowej Zelandii na społeczności 
- Numer tożsamości w Norwegia 
- Philippines Unified Multi-Purpose ID Number 
- Polski numer prawa jazdy 
- Wizytówka w Polsce 
- Identyfikator narodowy w Polsce (PESEL) 
- Paszport Polski 
- Numer identyfikacji podatkowej w Polsce 
- Polski numer REGON 
- Numer karty Wi-Wi-Do 
- Numer prawa jazdy portugalia 
- Numer paszportu Portugalia 
- Numer identyfikacji podatkowej Portugalia 
- Numer prawa jazdy Rumunii 
- Numer paszportu Rumunii 
- Rumunia Personal Numerical Code (CNP) 
- Numer paszportu rosyjskiego (krajowe) 
- Numer paszportu rosyjskiego (międzynarodowy) 
- Arabia Saudyjska 
- Numer dowodu tożsamości państwowej w Singapurze (NRIC, National Registration Identity Card) 
- Słowacja Numer prawa jazdy 
- Numer paszportu Słowacja 
- Słowacja Numer osobisty 
- Numer prawa jazdy w Słowenii 
- Numer paszportu Słowenii 
- Numer identyfikacji podatkowej w Słowenii 
- Unikatowy numer dla masterów w słowenii 
- Numer identyfikacyjny Republika Południowej Afryki 
- Numer rejestracji rezydenta Korei Południowej 
- Hiszpania DNI 
- Numer prawa jazdy w Hiszpanii 
- Numer paszportu Hiszpanii 
- Hiszpania Numer PE PEŁ(SSN) 
- Numer identyfikacji podatkowej Hiszpanii 
- SQL Server parametrów połączenia 
- Szwecja Numer prawa jazdy 
- Identyfikator narodowy Szwecja 
- Numer paszportu Szwecja 
- Szwecja Numer identyfikacyjny podatku 
- Kod SWIFT 
- Swiss Social Security Number AHV 
- Identyfikator narodowy na Tajwanie 
- Numer paszportu na Tajwanie 
- Certyfikat rezydentny na Tajwanie (ARC/TARC) 
- Kod identyfikacyjny populacji tajskiej 
- Numer identyfikacyjny tureckiego numeru identyfikacyjnego 
- Zjednoczone Emiraty Zjednoczone Numer prawa jazdy 
- Zjednoczone Emiraty Zjednoczone Numer listy adresowej 
- Zjednoczone Emiraty Zjednoczone Numer Usługa kondycji państwowej 
- Zjednoczone Emiraty Zjednoczone Numer ubezpieczenia państwowego (NINO) 
- Zjednoczone Emiraty Zjednoczone Unikatowy numer referencyjny podatku 
- Stany Zjednoczone Numer paszportu 
- Numer konta bankowego w Stanach Zjednoczonych 
- Numer prawa jazdy w Stanach Zjednoczonych 
- Numer identyfikacyjny identyfikacji indywidualnej (ITIN) Stanów Zjednoczonych 
- Numer SSN (U.SSN) 
- Numer paszportu Ukrainy (krajowe) 
- Numer paszportu Ukrainy (międzynarodowy) 
 
Pamiętaj, że oprócz powyższych, niestandardowych typów informacji poufnych będą również wykrywane dodatkowe typy informacji poufnych, które są obecnie wykrywane.

## <a name="support-matrix-for-dlp-policy-tips-across-microsoft-apps"></a>Macierz obsługi dla porad dotyczących zasad DLP w aplikacjach firmy Microsoft

|**Aplikacja i platforma**|**Obsługa porad zasad DLP**|**Obsługiwane typy informacji poufnych**|**Predykaty i obsługiwane akcje**|**Komentarze**|
|:--|:--|:--|:--|:--|
|**Outlook w sieci Web**|:::image type="icon" source="../media/rightmrk.png" border="false":::|wszystkie|podzbiór||
|**Outlook Win32 (kompilacja 2105 14026.20000 i półroczny kanał wer. 2102 kompilacja 13801.20862)**|:::image type="icon" source="../media/rightmrk.png" border="false":::|podzbiór|podzbiór|Zobacz program [Outlook 2013](#outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions) i nowsze programy obsługuje wyświetlanie porad dotyczących zasad tylko dla niektórych warunków i wyjątków oraz programu [Outlook 2013](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) i nowszych wersji oraz aplikacje Office w wersji klasycznej, przedstawiając porady dotyczące zasad tylko dla niektórych typów informacji poufnych, aby uzyskać szczegółowe informacje na temat pomocy technicznej dla typów informacji poufnych oraz warunków i akcji DLP obsługiwanych podczas wyświetlania porad dotyczących zasad DLP na Outlook  Win32.|
|**Outlook Mobile (iOS, Android)/Outlook Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|brak|brak|Porady dotyczące zasad DLP nie są obsługiwane na Outlook urządzeniach przenośnych|
|**SharePoint online/OneDrive dla Firm klienta sieci Web**|:::image type="icon" source="../media/rightmrk.png" border="false":::|wszystkie|wszystkie predykaty i akcje spo/ODB w programie DLP||
|**SharePoint win32/ OneDrive dla Firm Win32**|:::image type="icon" source="../media/crsmrk.png" border="false":::|brak|brak|Porady dotyczące zasad DLP nie są obsługiwane w SharePoint ani w OneDrive klienckich klasycznych|
|**Word, Excel, PowerPoint Web Client**|:::image type="icon" source="../media/rightmrk.png" border="false":::|wszystkie|wszystkie predykaty i akcje spo/ODB w programie DLP|Porada w zakresie zasad DLP jest obsługiwana, jeśli dokument jest hostowany w aplikacji sieci Web usługi SPO lub ODB i zasady DLP są już sygnaturowane.|
|**Word, Excel, PowerPoint Mobile Client**|:::image type="icon" source="../media/crsmrk.png" border="false":::|brak|brak|Porady dotyczące zasad DLP nie są obsługiwane w aplikacjach mobilnych dla Office.|
|**Teams Web/ Teams desktop/ Teams Mobile/ Teams Mac**|:::image type="icon" source="../media/rightmrk.png" border="false":::|wszystkie|wszystkie Teams zasad DLP|Porady dotyczące zasad będą wyświetlane, gdy wiadomość jest oflagowana jako "Ta wiadomość została oflagowana. Co mogę zrobić?" Po kliknięciu linku użytkownik może przejrzeć typy informacji poufnych wykryte i zastąpić lub zgłosić problem, jeśli zezwoli na to administrator. Pamiętaj, że w przypadku plików nie są wyświetlane żadne porady dotyczące zasad. Gdy adresat spróbuje uzyskać dostęp do dokumentu, może uzyskać odmowa dostępu, jeśli nie jest dozwolony.|
|**Urządzenia punktu końcowego Win32**|:::image type="icon" source="../media/rightmrk.png" border="false":::|podzbiór|wszystkie predykaty i akcje ochrony przed dlp punktami końcowymi w zasadach DLP|Zobacz [Ochrona przed utratą danych w punkcie końcowym obsługuje porady dotyczące zasad tylko dla niektórych typów informacji poufnych](#data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types).|
|**Urządzenia z systemem macOS (wersja zapoznawcza)**|tylko porady domyślne|wszystkie|podzbiór|Zasady ochrony przed utratą danych można wymusić na urządzeniach z systemem macOS. Porady dotyczące zasad niestandardowych nie są obsługiwane.|
|**Aplikacje w chmurze innych firm**|:::image type="icon" source="../media/crsmrk.png" border="false":::|brak|brak|Porady dotyczące zasad ochrony przed utratą danych nie są obsługiwane w aplikacjach innych firm w chmurze|
|**On-prem**|:::image type="icon" source="../media/crsmrk.png" border="false":::|brak|brak||
|**Word, Excel, PowerPoint Win32**|:::image type="icon" source="../media/crsmrk.png" border="false":::|podzbiór|podzbiór|Zobacz Outlook [2013](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) i nowsze oraz Pomoc techniczna usługi Office na komputerze stacjonarnym, aby wyświetlić porady dotyczące zasad tylko dla niektórych typów informacji poufnych, aby uzyskać listę obsługiwanych typów informacji poufnych.</br></br>Porady dotyczące zasad dla aplikacji klienckich WXP będą działać w przypadku dokumentów przechowywanych w witrynach usługi SharePoint Online lub OneDrive dla Firm dla wszystkich zasad DLP, które mają dokładnie poniższy lub podzestaw warunków lub akcji w zasadach DLP:</br> <ul><li>Zawartość zawiera typy informacji poufnych</li><li>Zakres programu Access (zawartość jest udostępniana wewnętrznie/zewnętrznie)</li><li>Powiadamianie użytkownika (porady dotyczące zasad/powiadomienia użytkownika)</li><li>Blokowanie wszystkich</li><li>Raporty o incydentach</li></ul></br> Jeśli istnieje inny warunek lub akcja, porada o zasadach DLP dla tych zasad nie będzie wyświetlana w aplikacjach klasycznych Word, Excel lub PowerPoint.</br>Zobacz [Porady dotyczące zasad w Excel, PowerPoint i Word,](use-notifications-and-policy-tips.md#policy-tips-in-excel-powerpoint-and-word) aby uzyskać więcej szczegółowych informacji|
||||||
