---
title: Dokumentacja dotycząca porad dotyczących zasad ochrony przed utratą danych
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
description: Dowiedz się, jak dodać poradę dotyczącą zasad do zasad ochrony przed utratą danych (DLP), powiadamiając użytkownika o pracy z zawartością powodującą konflikt z zasadami DLP.
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: f9702916831839ac384cd262854fd0a88f90a8ea
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953666"
---
# <a name="data-loss-prevention-policy-tips-reference"></a>Dokumentacja dotycząca porad dotyczących zasad ochrony przed utratą danych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Porady dotyczące zasad DLP w Outlook dostęp do sieci Web są obsługiwane dla wszystkich warunków, wyjątków i akcji mających zastosowanie do obciążenia Exchange w zasadach DLP, z wyjątkiem następujących:

**Warunki:**

- Adresat jest członkiem
- Nagłówek zawiera wyrazy lub frazy
- Nagłówek pasuje do wzorców
- Typ komunikatu to
- Zestaw znaków zawartości zawiera wyrazy
- Czy nadawca przesłaniał poradę dotyczącą zasad
- Rozmiar komunikatu jest równy lub jest większy niż
- Atrybut usługi AD nadawcy zawiera wyrazy lub frazy
- Atrybut usługi AD nadawcy pasuje do wzorców
- Zakresy adresów IP nadawcy
- Atrybut usługi AD adresata zawiera wyrazy lub frazy
- Atrybut usługi AD odbiorcy pasuje do wzorców
- Nazwa dokumentu zawiera wyrazy lub frazy
- Nazwa dokumentu jest zgodna z wzorcami
- Zawartość dokumentu zawiera słowa lub frazy
- Zawartość dokumentu pasuje do wzorców

**Działania:**

- Przekazywanie komunikatu do zatwierdzenia do menedżera nadawcy
- Przekazywanie komunikatu do zatwierdzenia do określonych osób zatwierdzających
- Przekierowywanie komunikatu do określonych użytkowników
- Dodawanie adresatów do pola Do
- Dodawanie adresatów do usługi Cc Box
- Dodawanie adresatów do urządzenia Bcc Box
- Dodawanie menedżera nadawcy jako adresata
- Dodawanie zastrzeżenia HTML
- Temat wstępnej wiadomości e-mail
- Usuwanie szyfrowania komunikatów usługi O365 i ochrony praw

## <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions"></a>Outlook 2013 r. i nowsze obsługuje wyświetlanie wskazówek dotyczących zasad tylko dla niektórych warunków i wyjątków

Obecnie Outlook 2013 r. i nowsze obsługuje wyświetlanie wskazówek dotyczących zasad, które nie zawierają żadnych warunków ani wyjątków oprócz wymienionych poniżej warunków i odpowiadających im wyjątków:

- Zawartość zawiera (działa tylko w przypadku typów informacji poufnych. Etykiety poufności nie są obsługiwane)
- Zawartość jest udostępniana

Należy pamiętać, że wszystkie warunki działają w przypadku wiadomości e-mail utworzonych w Outlook aplikacji klienckiej, gdzie będą one zgodne z zawartością i wymuszają akcje ochronne dotyczące zawartości. Jednak wyświetlanie porad dotyczących zasad dla użytkowników nie jest obsługiwane w przypadku żadnych warunków, które są używane poza tymi wymienionymi powyżej.

## <a name="outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types"></a>Outlook 2013 r. i nowsze oraz Office obsługę aplikacji na pulpicie z poradami dotyczącymi zasad tylko dla niektórych typów informacji poufnych

Lista dostępnych poufnych typów informacji, które zostaną wykryte w celu wyświetlenia wskazówek dotyczących zasad DLP w Outlook na komputerze (2013 lub nowszym) i aplikacjach Office (Word, Excel, PowerPoint) na pulpicie, to:

- Numer routingu ABA
- Numer tożsamości narodowej Argentyny (DNI)
- Numer konta bankowego Australii
- Numer konta medycznego w Australii
- Australia Passport Number
- Numer pliku podatkowego Australia
- Klucz uwierzytelniania usługi Azure DocumentDB  
- Parametry połączenia bazy danych IAAS platformy Azure i parametry połączenia Azure SQL  
- Parametry połączenia usługi Azure IoT  
- Hasło ustawienia publikowania platformy Azure  
- Parametry połączenia usługi Azure Redis Cache  
- Sygnatura dostępu współdzie  
- parametry połączenia Azure Service Bus  
- Klucz konta usługi Azure Storage  
- Klucz konta usługi Azure Storage (ogólny)  
- Numer krajowy Belgii
- Numer CPF w Brazylii
- Numer jednostki prawnej Brazylii (CNPJ)
- Brazylia National ID Card (RG)
- Numer konta bankowego w Kanadzie
- Kanada Numer prawa jazdy
- Kanada — numer Usługa kondycji
- Kanada Numer paszportu
- Kanada Osobisty numer identyfikacyjny zdrowia (PHIN)
- Kanada Numer ubezpieczenia społecznego
- Numer karty tożsamości Chile
- Numer CHRL (China Resident Identity Card)
- Numer karty kredytowej
- Numer chorwackiego numeru karty tożsamości  
- Numer identyfikacji osobistej Chorwacji (OIB)  
- Czeski numer tożsamości osobistej  
- Duński osobisty numer identyfikacyjny
- Numer Agencji Egzekwowania Narkotyków (DEA)
- Numer karty debetowej UE
- Numer prawa jazdy UE  
- Krajowy numer identyfikacyjny UE  
- Numer paszportu UE  
- Numer ubezpieczenia społecznego UE (SSN) lub równoważny identyfikator  
- Numer IDENTYFIKACJI PODATKOWEJ UE (TIN)  
- Identyfikator krajowy Finlandii
- Numer paszportu Finlandii
- Francuski numer prawa jazdy
- Francuska krajowa karta tożsamości (CNI)
- Numer paszportu Francji
- Francuski numer ubezpieczenia społecznego (INSEE)
- Niemiecki numer prawa jazdy
- Niemiecki numer paszportu
- Numer niemieckiego numeru karty tożsamości
- Grecja National ID Card  
- Numer karty tożsamości Hongkongu (HKID)
- Indie — stały numer konta (PAN)
- Indie Unikatowa identyfikacja (Aadhaar) Numer
- Numer karty tożsamości Indonezji (KTP)
- Numer międzynarodowego konta bankowego (IBAN)
- Międzynarodowa klasyfikacja chorób (ICD-10-CM)  
- Międzynarodowa klasyfikacja chorób (ICD-9-CM)  
- IP Address (Adres IP)
- Numer służby publicznej (PPS) w Irlandii 
- Numer konta bankowego Izrael
- Identyfikator narodowy Izraela
- Włochy Numer prawa jazdy
- Numer konta bankowego w Japonii
- Numer japońskiego prawa jazdy
- Japoński numer paszportu
- Numer rejestracyjny rezydenta Japonii
- Japoński numer ubezpieczenia społecznego (SIN)
- Numer karty rezydencji japońskiej
- Numer karty tożsamości Malezji
- Numer usługi obywatela Holandii (BSN)  
- Numer Ministerstwa Zdrowia Nowej Zelandii
- Numer tożsamości Norwegii  
- Filipiny Unified Multi-Purpose ID Number
- Polski dowód tożsamości
- Polski identyfikator krajowy (PESEL)
- Polska Passport
- Numer karty obywatela Portugalii
- Identyfikator narodowy Arabii Saudyjskiej
- Numer krajowego dowodu rejestracyjnego (NRIC) w Singapurze
- Republika Południowej Afryki — numer identyfikacyjny  
- Numer rejestracyjny rezydenta Korei Południowej
- Numer ubezpieczenia społecznego w Hiszpanii (SSN)
- parametry połączenia SQL Server  
- Identyfikator krajowy Szwecji
- Numer paszportu Szwecji
- Kod SWIFT
- Tajwan — identyfikator krajowy
- Numer paszportu Tajwanu
- Certyfikat rezydenta Tajwanu (ARC/TARC)
- Kod identyfikacji populacji tajskiej
- Turecki krajowy numer identyfikacyjny
- WIELKIEJ BRYTANII. Numer prawa jazdy
- WIELKIEJ BRYTANII. Numer listy wyborczej
- WIELKIEJ BRYTANII. Numer Usługa kondycji krajowego
- WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO)
- Stany Zjednoczone /Zjednoczone Zjednoczone Numer paszportu
- Numer konta bankowego w Stanach Zjednoczonych
- Numer prawa jazdy w Stanach Zjednoczonych
- Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN)
- Numer ubezpieczenia społecznego (SSN)

Należy pamiętać, że niestandardowe typy informacji poufnych są również obsługiwane w przypadku porad dotyczących zasad DLP oprócz powyższych wbudowanych typów informacji poufnych.

## <a name="data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types"></a>Ochrona przed utratą danych na urządzeniach punktu końcowego obsługuje porady dotyczące zasad tylko dla niektórych typów informacji poufnych

Lista wbudowanych typów informacji poufnych, które zostaną wykryte w dokumentach znajdujących się na urządzeniach punktu końcowego, jest następująca:

- Numer routingu ABA 
- Numer tożsamości narodowej Argentyny (DNI) 
- Numer konta bankowego Australii 
- Numer konta medycznego w Australii 
- Australia Passport Number 
- Numer pliku podatkowego Australia 
- Australijski numer biznesowy 
- Numer australijskiej firmy 
- Austria Numer prawa jazdy 
- Austria Identity Card 
- Numer paszportu Austrii 
- Numer ubezpieczenia społecznego w Austrii 
- Austriacki numer identyfikacji podatkowej 
- Austria — numer podatku od wartości dodanej (VAT) 
- Klucz uwierzytelniania usługi Azure DocumentDB 
- Parametry połączenia bazy danych IAAS platformy Azure i parametry połączenia Azure SQL 
- Parametry połączenia usługi Azure IoT 
- Hasło ustawienia publikowania platformy Azure 
- Parametry połączenia usługi Azure Redis Cache 
- Sygnatura dostępu współdzie 
- parametry połączenia Azure Service Bus 
- Klucz konta usługi Azure Storage 
- Klucz konta usługi Azure Storage (ogólny) 
- Belgijski numer prawa jazdy 
- Numer krajowy Belgii 
- Numer paszportu Belgia 
- Belgijski numer podatku od wartości dodanej 
- Numer CPF w Brazylii 
- Numer jednostki prawnej Brazylii (CNPJ) 
- Brazylia National ID Card (RG) 
- Bułgarski numer prawa jazdy 
- Numer paszportu Bułgarii 
- Bułgaria — jednolity numer cywilny 
- Numer konta bankowego w Kanadzie 
- Kanada Numer prawa jazdy 
- Kanada — numer Usługa kondycji 
- Kanada Numer paszportu 
- Kanada Osobisty numer identyfikacyjny zdrowia (PHIN) 
- Kanada Numer ubezpieczenia społecznego 
- Numer karty tożsamości Chile 
- Numer CHRL (China Resident Identity Card) 
- Numer karty kredytowej 
- Numer prawa jazdy Chorwacji 
- Numer chorwackiego numeru karty tożsamości 
- Numer krajowego dowodu osobistego Chorwacji 
- Numer paszportu Chorwacji 
- Numer identyfikacji osobistej Chorwacji (OIB) 
- CSCAN-AZURE0060 Sygnatura dostępu współdzielonego konta usługi Azure Storage 
- CSCAN-GENERAL0140 Ogólny klucz symetryczny 
- Numer prawa jazdy cypryjskiego 
- Cypr identity card 
- Numer paszportu cypryjskiego 
- Numer identyfikacyjny podatku cypryjskiego 
- Czeski numer prawa jazdy 
- Czeski numer tożsamości osobistej 
- Numer paszportu w Republice Czeskiej 
- Duński numer prawa jazdy 
- Duński numer paszportu 
- Duński osobisty numer identyfikacyjny 
- Numer Agencji Egzekwowania Narkotyków (DEA) 
- Estoński numer prawa jazdy 
- Numer paszportu Estonii 
- Estoński osobisty kod identyfikacyjny 
- Numer karty debetowej UE 
- Numer prawa jazdy UE 
- Krajowy numer identyfikacyjny UE 
- Numer paszportu UE 
- Numer ubezpieczenia społecznego UE (SSN) lub równoważny identyfikator 
- Numer IDENTYFIKACJI PODATKOWEJ UE (TIN) 
- Numer prawa jazdy w Finlandii 
- Europejski numer ubezpieczenia zdrowotnego w Finlandii 
- Identyfikator krajowy Finlandii 
- Numer paszportu Finlandii 
- Francuski numer prawa jazdy 
- Numer ubezpieczenia zdrowotnego We Francji 
- Francuska krajowa karta tożsamości (CNI) 
- Numer paszportu Francji 
- Francuski numer ubezpieczenia społecznego (INSEE) 
- Francuski numer identyfikacji podatkowej (numéro SPI.) 
- Numer podatku od wartości dodanej we Francji 
- Niemiecki numer prawa jazdy 
- Niemiecki numer paszportu 
- Numer niemieckiego numeru karty tożsamości 
- Numer NIP w Niemczech 
- Numer podatku od wartości dodanej w Niemczech 
- Grecja Numer prawa jazdy 
- Grecja National ID Card 
- Numer paszportu Grecji 
- Numer ubezpieczenia społecznego w Grecji (AMKA) 
- Grecki numer identyfikacji podatkowej 
- Numer karty tożsamości Hongkongu (HKID) 
- Węgierski numer ubezpieczenia społecznego (TAJ) 
- Węgierski numer podatku od wartości dodanej 
- Węgierski numer prawa jazdy 
- Węgierski numer paszportu 
- Węgierski osobisty numer identyfikacyjny 
- Węgry Numer identyfikacji podatkowej 
- Indie — stały numer konta (PAN) 
- Indie Unikatowa identyfikacja (Aadhaar) Numer 
- Numer karty tożsamości Indonezji (KTP) 
- Numer międzynarodowego konta bankowego (IBAN) 
- Międzynarodowa klasyfikacja chorób (ICD-10-CM) 
- Międzynarodowa klasyfikacja chorób (ICD-9-CM) 
- IP Address (Adres IP) 
- Irlandzki numer prawa jazdy 
- Numer paszportu Irlandii 
- Numer służby publicznej (PPS) w Irlandii 
- Numer konta bankowego Izrael 
- Identyfikator narodowy Izraela 
- Włochy Numer prawa jazdy 
- Włoski kodeks obrachunkowy 
- Numer paszportu Włochy 
- Numer podatku od wartości dodanej we Włoszech 
- Numer konta bankowego w Japonii 
- Numer japońskiego prawa jazdy 
- Japoński numer paszportu 
- Numer rejestracyjny rezydenta Japonii 
- Japoński numer ubezpieczenia społecznego (SIN) 
- Japoński Mój numer firmowy 
- Japoński Mój numer osobisty 
- Numer karty rezydencji japońskiej 
- Numer prawa jazdy Łotwy 
- Numer paszportu łotwy 
- Kod osobisty Łotwy 
- Litewski numer prawa jazdy 
- Litewski numer paszportu 
- Litewski kod osobisty 
- Luksemburski numer prawa jazdy 
- Luksemburski krajowy numer identyfikacyjny (osoby fizyczne) 
- Luksemburski krajowy numer identyfikacyjny (osoby niebędące osobami fizycznymi) 
- Numer paszportu luksemburski 
- Numer karty tożsamości Malezji 
- Malta Numer prawa jazdy 
- Numer karty tożsamości Malty 
- Malta Passport Number 
- Numer NIP Malty 
- Numer usługi obywatela Holandii (BSN) 
- Holenderski numer prawa jazdy 
- Holenderski numer paszportu 
- Holenderski numer identyfikacji podatkowej 
- Holenderski numer podatku od wartości dodanej 
- Numer konta bankowego Nowej Zelandii 
- Numer prawa jazdy Nowej Zelandii 
- Nowa Zelandia Numer przychodu w głębi lądu 
- Numer Ministerstwa Zdrowia Nowej Zelandii 
- Numer opieki społecznej w Nowej Zelandii 
- Numer tożsamości Norwegii 
- Filipiny Unified Multi-Purpose ID Number 
- Numer polskiego prawa jazdy 
- Polski dowód tożsamości 
- Polski identyfikator krajowy (PESEL) 
- Polska Passport 
- Numer NIP w Polsce 
- Polski numer REGON 
- Numer karty obywatela Portugalii 
- Numer prawa jazdy Portugalia 
- Numer paszportu Portugalii 
- Numer identyfikacji podatkowej Portugalii 
- Rumunia Numer prawa jazdy 
- Numer paszportu Rumunii 
- Rumunia Osobisty kod numeryczny (CNP) 
- Rosyjski numer paszportu (krajowy) 
- Rosyjski numer paszportu (międzynarodowy) 
- Identyfikator narodowy Arabii Saudyjskiej 
- Numer krajowego dowodu rejestracyjnego (NRIC) w Singapurze 
- Słowacki numer prawa jazdy 
- Numer paszportu Słowacji 
- Słowacja — numer osobisty 
- Słoweński numer prawa jazdy 
- Numer paszportu Słowenii 
- Słoweński numer identyfikacji podatkowej 
- Słoweński unikatowy główny numer obywatela 
- Republika Południowej Afryki — numer identyfikacyjny 
- Numer rejestracyjny rezydenta Korei Południowej 
- Hiszpania DNI 
- Numer hiszpańskiego prawa jazdy 
- Numer paszportu Hiszpanii 
- Numer ubezpieczenia społecznego w Hiszpanii (SSN) 
- Numer identyfikacyjny podatku w Hiszpanii 
- parametry połączenia SQL Server 
- Szwedzki numer prawa jazdy 
- Identyfikator krajowy Szwecji 
- Numer paszportu Szwecji 
- Szwedzki numer identyfikacji podatkowej 
- Kod SWIFT 
- Szwajcarski numer ubezpieczenia społecznego AHV 
- Tajwan — identyfikator krajowy 
- Numer paszportu Tajwanu 
- Certyfikat rezydenta Tajwanu (ARC/TARC) 
- Kod identyfikacji populacji tajskiej 
- Turecki krajowy numer identyfikacyjny 
- WIELKIEJ BRYTANII. Numer prawa jazdy 
- WIELKIEJ BRYTANII. Numer listy wyborczej 
- WIELKIEJ BRYTANII. Numer Usługa kondycji krajowego 
- WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) 
- WIELKIEJ BRYTANII. Unikatowy numer referencyjny podatnika 
- Stany Zjednoczone /Zjednoczone Zjednoczone Numer paszportu 
- Numer konta bankowego w Stanach Zjednoczonych 
- Numer prawa jazdy w Stanach Zjednoczonych 
- Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN) 
- Numer ubezpieczenia społecznego (SSN) 
- Numer paszportu Ukrainy (krajowy) 
- Numer paszportu Ukrainy (międzynarodowy) 
 
Należy pamiętać, że oprócz powyższych wbudowanych typów informacji poufnych zostaną również wykryte niestandardowe typy informacji poufnych

## <a name="support-matrix-for-dlp-policy-tips-across-microsoft-apps"></a>Macierz pomocy technicznej dotycząca porad dotyczących zasad DLP w aplikacjach firmy Microsoft

|**Aplikacja i platforma**|**Obsługa porad dotyczących zasad DLP**|**Obsługiwane typy informacji poufnych**|**Obsługiwane predykaty i akcje**|**Komentarze**|
|:--|:--|:--|:--|:--|
|**Outlook w sieci Web**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Wszystkie|Podzbiór||
|**Outlook Win32 (ver. 2105 build 14026.20000 and semi-annual channel ver. 2102 build 13801.20862)**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Podzbiór|Podzbiór|Zobacz [Outlook 2013 i nowsze wersje pomocy technicznej zawierają wskazówki dotyczące zasad tylko dla niektórych warunków i wyjątków](#outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions) oraz [Outlook 2013 r. i nowszych oraz Office aplikacji na pulpicie z poradami dotyczącymi zasad tylko dla niektórych typów informacji poufnych](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types), aby uzyskać szczegółowe informacje na temat obsługi typów informacji poufnych oraz warunków i akcji DLP obsługiwanych w celu wyświetlania wskazówek dotyczących zasad DLP dotyczących Outlook  Win32.|
|**Outlook Mobile (iOS, Android)/Outlook Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Brak|Brak|Porady dotyczące zasad DLP nie są obsługiwane w Outlook urządzeniach przenośnych|
|**klient sieci Web SharePoint Online/OneDrive dla Firm**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Wszystkie|wszystkie predykaty i akcje SPO/ODB w DLP||
|**klient SharePoint Win32/ OneDrive dla Firm Win32**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Brak|Brak|Porady dotyczące zasad DLP nie są obsługiwane w aplikacjach klienckich SharePoint ani OneDrive klasycznych|
|**Word, Excel, PowerPoint Web Client**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Wszystkie|wszystkie predykaty i akcje SPO/ODB w DLP|Porada dotycząca zasad DLP jest obsługiwana, jeśli dokument jest hostowany w aplikacji internetowej SPO lub ODB, a zasady DLP są już ostemplowane.|
|**Word, Excel, klient PowerPoint Mobile**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Brak|Brak|Porady dotyczące zasad DLP nie są obsługiwane w aplikacjach mobilnych dla Office.|
|**Teams Web/ Teams Desktop/ Teams Mobile/ Teams Mac**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Wszystkie|wszystkie Teams predykaty w zasadach DLP|Porady dotyczące zasad będą wyświetlane, gdy komunikat zostanie oflagowany jako "Ta wiadomość została oflagowana. Co mogę zrobić?" Po kliknięciu linku użytkownik może przejrzeć wykryte i zastąpione typy informacji poufnych lub zgłosić problem, jeśli jest to dozwolone przez administratora. Pamiętaj, że dla plików nie są wyświetlane żadne wskazówki dotyczące zasad. Gdy adresat próbuje uzyskać dostęp do dokumentu, może uzyskać odmowę dostępu, jeśli nie jest dozwolony.|
|**Urządzenia punktu końcowego Win32**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Podzbiór|wszystkie predykaty i akcje DLP punktu końcowego w zasadach DLP|Zobacz [Zapobieganie utracie danych w punkcie końcowym obsługuje porady dotyczące zasad tylko dla niektórych typów informacji poufnych](#data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types)|
|**Urządzenia z systemem macOS**|tylko domyślne porady|Wszystkie|Podzbiór|Zasady zapobiegania utracie danych są wymuszane na urządzeniach z systemem macOS. Porady dotyczące zasad niestandardowych nie są obsługiwane.|
|**Aplikacje w chmurze innych firm**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Brak|Brak|Porady dotyczące zasad ochrony przed utratą danych nie są obsługiwane w aplikacjach w chmurze innych firm|
|**Lokalnie**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Brak|Brak||
|**Klient programu Word, Excel, PowerPoint Win32**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Podzbiór|Podzbiór|Zobacz [Outlook 2013 r. i nowszych oraz Office aplikacji w pomocy technicznej aplikacji klasycznych z poradami dotyczącymi zasad tylko dla niektórych typów informacji poufnych](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) dla listy obsługiwanych typów informacji poufnych</br></br>Porady dotyczące zasad dla aplikacji klienckich WXP będą działać w przypadku dokumentów przechowywanych w witrynach SharePoint Online lub OneDrive dla Firm dla wszystkich zasad DLP, które mają dokładnie poniższe lub podzestaw warunków lub akcji w zasadach DLP:</br> <ul><li>Zawartość zawiera typy informacji poufnych</li><li>Zakres dostępu (zawartość jest współużytkowana wewnętrznie/zewnętrznie)</li><li>Powiadamianie użytkownika (porady dotyczące zasad/powiadomienia użytkowników)</li><li>Blokuj wszystkich</li><li>Raporty o zdarzeniach</li></ul></br> Jeśli istnieje jakikolwiek inny warunek lub akcja, porada dotycząca zasad DLP dla tych zasad nie będzie wyświetlana w aplikacjach klasycznych programu Word, Excel lub PowerPoint.</br>Aby uzyskać więcej informacji[, zobacz Porady dotyczące zasad w Excel, PowerPoint i programie Word](use-notifications-and-policy-tips.md#policy-tips-in-excel-powerpoint-and-word)|
||||||
