---
title: Dowiedz się więcej o kluczu dostępności dla klucza klienta
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
description: Dowiedz się więcej o kluczu dostępności używanym do odzyskiwania utraconych kluczy klienta.
ms.openlocfilehash: 1fd80d23980957402ae7d5e79a91e57d28df38f9
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761842"
---
# <a name="learn-about-the-availability-key-for-customer-key"></a>Dowiedz się więcej o kluczu dostępności dla klucza klienta

Klucz dostępności jest kluczem głównym automatycznie generowanym i aprowizowanym podczas tworzenia zasad szyfrowania danych. Microsoft 365 przechowuje i chroni klucz dostępności. Klucz dostępności jest funkcjonalnie podobny do dwóch kluczy głównych dostarczanych do szyfrowania usługi przy użyciu klucza klienta. Klucz dostępności otacza klucze o jedną warstwę niżej w hierarchii kluczy. W przeciwieństwie do kluczy, które udostępniasz i zarządzasz w usłudze Azure Key Vault, nie możesz bezpośrednio uzyskać dostępu do klucza dostępności. Microsoft 365 zautomatyzowane usługi programowo zarządzają kluczem dostępności. Te usługi inicjują zautomatyzowane operacje, które nigdy nie wymagają bezpośredniego dostępu do klucza dostępności.

Podstawowym celem klucza dostępności jest zapewnienie możliwości odzyskiwania po nieprzewidanej utracie zarządzanych kluczy głównych. Utrata może być wynikiem niegospodarności lub złośliwego działania. Jeśli utracisz kontrolę nad kluczami głównymi, skontaktuj się z pomoc techniczna firmy Microsoft, a firma Microsoft pomoże Ci w procesie odzyskiwania przy użyciu klucza dostępności. Użyjesz klucza dostępności, aby przeprowadzić migrację do nowych zasad szyfrowania danych przy użyciu nowych aprowizowanych kluczy głównych.

Storage i kontrola klucza dostępności celowo różnią się od kluczy usługi Azure Key Vault z trzech powodów:

- Klucz dostępności zapewnia możliwość odzyskiwania, "break-glass" w przypadku utraty kontroli nad obydwoma kluczami Key Vault platformy Azure.
- Rozdzielenie kontrolek logicznych i bezpiecznych lokalizacji magazynu zapewnia ochronę przed utratą wszystkich kluczy i danych przed pojedynczym atakiem lub punktem awarii.
- Klucz dostępności zapewnia możliwość wysokiej dostępności, jeśli usługi Microsoft 365 nie mogą uzyskać dostępu do kluczy hostowanych na platformie Azure Key Vault z powodu błędów przejściowych. Ta reguła ma zastosowanie tylko do szyfrowania usług Exchange Online i Skype dla firm. SharePoint Online, OneDrive dla Firm i Teams pliki nigdy nie używają klucza dostępności, chyba że jawnie instruujesz firmę Microsoft o zainicjowaniu procesu odzyskiwania.

Dzielenie się odpowiedzialnością za ochronę danych przy użyciu różnych zabezpieczeń i procesów zarządzania kluczami ostatecznie zmniejsza ryzyko trwałego utraty lub zniszczenia wszystkich kluczy (a w związku z tym danych). Firma Microsoft zapewnia ci wyłączną władzę nad wyłączeniem lub zniszczeniem klucza dostępności po opuszczeniu usługi. Zgodnie z projektem nikt w firmie Microsoft nie ma dostępu do klucza dostępności: jest dostępny tylko za pomocą Microsoft 365 kodu usługi.

Zobacz [Centrum zaufania firmy Microsoft](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) , aby uzyskać więcej informacji na temat sposobu zabezpieczania kluczy.
  
## <a name="availability-key-uses"></a>Użycie klucza dostępności

Klucz dostępności zapewnia możliwość odzyskiwania w scenariuszach, w których zewnętrzny podmiot złośliwy lub złośliwy insider kradnie kontrolę nad magazynem kluczy lub gdy nieumyślne niegospodarność powoduje utratę kluczy głównych. Ta funkcja odzyskiwania ma zastosowanie do wszystkich usług Microsoft 365 zgodnych z kluczem klienta. Poszczególne usługi używają klucza dostępności inaczej. Microsoft 365 używa klucza dostępności tylko w sposób opisany poniżej.

### <a name="exchange-online-and-skype-for-business-uses"></a>używa Exchange Online i Skype dla firm

Oprócz możliwości odzyskiwania Exchange Online i Skype dla firm użyć klucza dostępności, aby zapewnić dostępność danych podczas przejściowych lub sporadycznych problemów operacyjnych związanych z dostępem usługi do kluczy głównych. Gdy usługa nie może uzyskać dostępu do żadnego z kluczy klienta na platformie Azure Key Vault z powodu błędów przejściowych, usługa automatycznie używa klucza dostępności. Usługa NIGDY nie przechodzi bezpośrednio do klucza dostępności.

Zautomatyzowane systemy w Exchange Online i Skype dla firm mogą używać klucza dostępności podczas przejściowych błędów do obsługi zautomatyzowanych usług zaplecza, takich jak ochrona przed wirusami, odnajdywanie elektroniczne, zapobieganie utracie danych, przenoszenie skrzynek pocztowych i indeksowanie danych.

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-uses"></a>pliki SharePoint Online, OneDrive dla Firm i Teams

W przypadku plików SharePoint Online, OneDrive dla Firm i Teams klucz dostępności nigdy nie jest używany poza funkcją odzyskiwania, a klienci muszą jawnie poinstruować firmę Microsoft, aby zainicjowała użycie klucza dostępności podczas scenariusza odzyskiwania. Zautomatyzowane operacje usług polegają wyłącznie na kluczach klienta w usłudze Azure Key Vault. Aby uzyskać szczegółowe informacje na temat działania hierarchii kluczy dla tych usług, zobacz [How SharePoint Online, OneDrive dla Firm, and Teams files use the availability key (Jak pliki SharePoint Online, OneDrive dla Firm i Teams używają klucza dostępności](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key)).

## <a name="availability-key-security"></a>Zabezpieczenia klucza dostępności

Firma Microsoft dzieli się z Tobą odpowiedzialnością za ochronę danych, tworząc wystąpienie klucza dostępności i podejmując szeroko zakrojone działania w celu jego ochrony. Firma Microsoft nie ujawnia klientom bezpośredniej kontroli nad kluczem dostępności. Na przykład możesz rzutować (obracać) tylko klucze, które należy do Ciebie w usłudze Azure Key Vault. Aby uzyskać więcej informacji, zobacz [Rzutowanie lub obracanie klucza klienta lub klucza dostępności](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Magazyny kluczy tajnych kluczy dostępności

Firma Microsoft chroni klucze dostępności w kontrolowanych przez dostęp wewnętrznych magazynach wpisów tajnych, takich jak usługa Azure Key Vault dostępna dla klientów. Zaimplementujemy mechanizmy kontroli dostępu, aby uniemożliwić administratorom firmy Microsoft bezpośredni dostęp do wpisów tajnych zawartych w nim. Operacje magazynu wpisów tajnych, w tym rotacja i usuwanie kluczy, są wykonywane za pośrednictwem zautomatyzowanych poleceń, które nigdy nie obejmują bezpośredniego dostępu do klucza dostępności. Operacje zarządzania magazynem wpisów tajnych są ograniczone do konkretnych inżynierów i wymagają eskalacji uprawnień za pośrednictwem wewnętrznego narzędzia Lockbox. Eskalacja uprawnień wymaga zatwierdzenia i uzasadnienia menedżera przed udzieleniem. Skrytka zapewnia, że dostęp jest powiązany z automatycznym odwoływaniem dostępu po wygaśnięciu czasu lub wylogowaniu inżyniera.

**klucze dostępności Exchange Online i Skype dla firm** są przechowywane w Exchange Online magazynie wpisów tajnych usługi Active Directory. Klucze dostępności są bezpiecznie przechowywane wewnątrz kontenerów specyficznych dla dzierżawy w ramach kontrolera domena usługi Active Directory. Ta bezpieczna lokalizacja magazynu jest oddzielona i odizolowana od magazynu wpisów tajnych SharePoint Online, OneDrive dla Firm i Teams plików.

**SharePoint Online, OneDrive dla Firm i Teams klucze dostępności plików** są przechowywane w wewnętrznym magazynie wpisów tajnych zarządzanym przez zespół usługi. Ta zabezpieczona usługa magazynu wpisów tajnych ma serwery frontonu z punktami końcowymi aplikacji i SQL Database jako zaplecze. Klucze dostępności są przechowywane w SQL Database i są opakowane (szyfrowane) za pomocą kluczy szyfrowania magazynu wpisów tajnych, które używają kombinacji AES-256 i HMAC do szyfrowania klucza dostępności w spoczynku. Klucze szyfrowania magazynu wpisów tajnych są przechowywane w logicznie izolowanym składniku tego samego SQL Database i są dodatkowo szyfrowane za pomocą kluczy RSA-2048 zawartych w certyfikatach zarządzanych przez urząd certyfikacji firmy Microsoft. Te certyfikaty są przechowywane na serwerach frontonu magazynu wpisów tajnych, które wykonują operacje względem bazy danych.

### <a name="defense-in-depth"></a>Ochrona w głębi obrony

Firma Microsoft stosuje szczegółową strategię ochrony, aby zapobiec wpływowi złośliwych podmiotów na poufność, integralność lub dostępność danych klientów przechowywanych w chmurze firmy Microsoft. Konkretne mechanizmy zapobiegawcze i detektywistyczne są implementowane w celu ochrony magazynu wpisów tajnych i klucza dostępności w ramach nadrzędnej strategii bezpieczeństwa.

Microsoft 365 jest tworzone w celu zapobiegania niewłaściwemu użyciu klucza dostępności. Warstwa aplikacji jest jedyną metodą, za pomocą której klucze, w tym klucz dostępności, mogą służyć do szyfrowania i odszyfrowywania danych. Tylko Microsoft 365 kod usługi może interpretować i przechodzić przez hierarchię kluczy na potrzeby działań szyfrowania i odszyfrowywania. Istnieje izolacja logiczna między lokalizacjami magazynu kluczy klienta, kluczami dostępności, innymi kluczami hierarchicznymi i danymi klienta. Ta izolacja zmniejsza ryzyko ujawnienia danych w przypadku naruszenia co najmniej jednej lokalizacji. Każda warstwa w hierarchii ma wbudowane funkcje wykrywania włamań 24x7 w celu ochrony przechowywanych danych i wpisów tajnych.

Mechanizmy kontroli dostępu są implementowane w celu zapobiegania nieautoryzowanemu dostępowi do systemów wewnętrznych, w tym magazynów kluczy tajnych kluczy dostępności. Inżynierowie firmy Microsoft nie mają bezpośredniego dostępu do magazynów kluczy tajnych kluczy dostępności. Aby uzyskać więcej szczegółów na temat kontroli dostępu, zapoznaj się z [artykułem Administracyjne kontrole dostępu w Microsoft 365](/compliance/assurance/assurance-administrative-access-controls-overview).

Mechanizmy techniczne uniemożliwiają pracownikom firmy Microsoft logowanie się do wysoce uprzywilejowanych kont usług, które w przeciwnym razie mogą być używane przez osoby atakujące do personifikacji usługi firmy Microsoft. Na przykład te kontrolki uniemożliwiają logowanie interakcyjne.

Mechanizmy rejestrowania i monitorowania zabezpieczeń to kolejna ochrona w głębi obrony zaimplementowana, która zmniejsza ryzyko usługi firmy Microsoft i danych. Zespoły usług firmy Microsoft wdrożyły aktywne rozwiązania do monitorowania, które generują alerty i dzienniki inspekcji. Wszystkie zespoły usług przekazują swoje dzienniki do centralnego repozytorium, w którym dzienniki są agregowane i przetwarzane. Narzędzia wewnętrzne automatycznie sprawdzają rekordy, aby potwierdzić, że usługi działają w optymalnym, odpornym i bezpiecznym stanie. Nietypowe działanie jest oflagowane do dalszego przeglądu.

Każde zdarzenie dziennika wskazujące potencjalne naruszenie zasad zabezpieczeń firmy Microsoft jest natychmiast zwracane do zespołów ds. zabezpieczeń firmy Microsoft. Microsoft 365 zabezpieczenia skonfigurowały alerty do wykrywania próby uzyskania dostępu do magazynów kluczy tajnych kluczy dostępności. Alerty są również generowane, jeśli personel firmy Microsoft podejmie próbę interaktywnego logowania do kont usług, co jest zabronione i chronione przez mechanizmy kontroli dostępu. Microsoft 365 zabezpieczenia wykrywają również i alerty po odchyleniach usługi Microsoft 365 od normalnych operacji punktu odniesienia. Mężczyźni próbujący nadużywać usług Microsoft 365 wyzwalają alerty powodujące eksmisję sprawcy ze środowiska chmury firmy Microsoft.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Odzyskiwanie po utracie klucza przy użyciu klucza dostępności

Jeśli utracisz kontrolę nad kluczami klienta, klucz dostępności zapewnia możliwość odzyskiwania i ponownego szyfrowania danych.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>Procedura odzyskiwania Exchange Online i Skype dla firm

Jeśli utracisz kontrolę nad kluczami klienta, klucz dostępności zapewnia możliwość odzyskania danych i przywrócenia zasobów Microsoft 365, które mają wpływ, do trybu online. Klucz dostępności nadal chroni dane podczas odzyskiwania. Na wysokim poziomie, aby w pełni odzyskać sprawności po utracie klucza, należy utworzyć nowy program DEP i przenieść zasoby, których dotyczy problem, do nowych zasad.

Aby zaszyfrować dane przy użyciu nowych kluczy klienta, utwórz nowe klucze w usłudze Azure Key Vault, utwórz nowy program DEP przy użyciu nowych kluczy klienta, a następnie przypisz nowy program DEP do skrzynek pocztowych obecnie zaszyfrowanych przy użyciu poprzedniego programu DEP, dla których klucze zostały utracone lub naruszone.

Ten proces ponownego szyfrowania może potrwać do 72 godzin. Jest to standardowy czas trwania zmiany programu DEP.
  
### <a name="recovery-procedure-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Procedura odzyskiwania plików SharePoint Online, OneDrive dla Firm i Teams

W przypadku plików SharePoint Online, OneDrive dla Firm i Teams klucz dostępności NIGDY nie jest używany poza funkcją odzyskiwania. Należy jawnie poinstruować firmę Microsoft, aby zainicjowała użycie klucza dostępności podczas scenariusza odzyskiwania. Aby zainicjować proces odzyskiwania, skontaktuj się z firmą Microsoft, aby aktywować klucz dostępności. Po aktywowaniu klucz dostępności jest automatycznie używany do odszyfrowywania danych, co umożliwia szyfrowanie danych przy użyciu nowo utworzonego programu DEP skojarzonego z nowymi kluczami klienta.  

Ta operacja jest proporcjonalna do liczby witryn w organizacji. Po wywołaniu firmy Microsoft w celu użycia klucza dostępności powinno nastąpić pełne połączenie online w ciągu około czterech godzin.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Jak Exchange Online i Skype dla firm używać klucza dostępności

Podczas tworzenia programu DEP z kluczem klienta Microsoft 365 generuje klucz zasad szyfrowania danych (DEP Key) skojarzony z tym programem DEP. Usługa szyfruje klucz DEP trzy razy: raz z każdym kluczem klienta i raz z kluczem dostępności. Przechowywane są tylko zaszyfrowane wersje klucza DEP, a klucz DEP można odszyfrować tylko za pomocą kluczy klienta lub klucza dostępności. Klucz DEP jest następnie używany do szyfrowania kluczy skrzynki pocztowej, które szyfruje poszczególne skrzynki pocztowe.
  
Microsoft 365 jest zgodny z tym procesem, aby odszyfrować i dostarczyć dane, gdy klienci korzystają z usługi:
  
1. Odszyfruj klucz PROGRAMU DEP przy użyciu klucza klienta.

2. Odszyfrowany klucz DEP służy do odszyfrowywania klucza skrzynki pocztowej.

3. Użyj odszyfrowanego klucza skrzynki pocztowej, aby odszyfrować samą skrzynkę pocztową, umożliwiając dostęp do danych w skrzynce pocztowej.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>Jak pliki SharePoint Online, OneDrive dla Firm i Teams używają klucza dostępności

Architektura i implementacja SharePoint Online i OneDrive dla Firm klucza klienta i klucza dostępności różnią się od Exchange Online i Skype dla firm.
  
Gdy organizacja przechodzi do kluczy zarządzanych przez klienta, Microsoft 365 tworzy klucz pośredni specyficzny dla organizacji (TIK). Microsoft 365 dwukrotnie szyfruje TIK przy użyciu każdego klucza klienta i przechowuje dwie zaszyfrowane wersje TIK. Przechowywane są tylko zaszyfrowane wersje TIK, a TIK można odszyfrować tylko za pomocą kluczy klienta. Interfejs TIK jest następnie używany do szyfrowania kluczy lokacji, które są następnie używane do szyfrowania kluczy obiektów blob (nazywanych również kluczami fragmentów plików). W zależności od rozmiaru pliku usługa może podzielić plik na wiele fragmentów plików, z których każdy ma unikatowy klucz. Same obiekty blob (fragmenty plików) są szyfrowane za pomocą kluczy obiektów blob i przechowywane w usłudze Microsoft Azure Blob Storage.
  
Microsoft 365 jest zgodny z tym procesem, aby odszyfrować i dostarczyć pliki klienta, gdy klienci korzystają z usługi:

1. Odszyfruj TIK przy użyciu klucza klienta.

2. Użyj odszyfrowanego interfejsu TIK, aby odszyfrować klucz lokacji.

3. Odszyfrowany klucz lokacji służy do odszyfrowywania klucza obiektu blob.

4. Użyj odszyfrowanego klucza obiektu blob, aby odszyfrować obiekt blob.

Microsoft 365 odszyfrowuje TIK, wysyłając dwa żądania odszyfrowywania do usługi Azure Key Vault z niewielkim przesunięciem. Pierwszy, który zakończy, dostarcza wynik, anulując drugie żądanie.
  
W przypadku utraty dostępu do kluczy klienta Microsoft 365 również szyfruje TIK za pomocą klucza dostępności i przechowuje go wraz z zestawami TIK zaszyfrowanymi przy użyciu każdego klucza klienta. Funkcja TIK zaszyfrowana za pomocą klucza dostępności jest używana tylko wtedy, gdy klient wywołuje firmę Microsoft w celu zarejestrowania ścieżki odzyskiwania, gdy utracił dostęp do kluczy, złośliwie lub przypadkowo.
  
Ze względu na dostępność i skalę odszyfrowane zestawy TIK są buforowane w pamięci podręcznej ograniczonej czasowo. Dwie godziny przed wygaśnięciem pamięci podręcznej TIK Microsoft 365 próbuje odszyfrować każdą TIK. Odszyfrowywanie zestawów TIK wydłuża okres istnienia pamięci podręcznej. Jeśli odszyfrowywanie TIK nie powiedzie się przez długi czas, Microsoft 365 generuje alert powiadamiający inżynierów przed wygaśnięciem pamięci podręcznej. Tylko wtedy, gdy klient wywołuje firmę Microsoft, Microsoft 365 zainicjować operację odzyskiwania, która obejmuje odszyfrowanie TIK przy użyciu klucza dostępności przechowywanego w magazynie wpisów tajnych firmy Microsoft i ponowne dołączenie dzierżawy przy użyciu odszyfrowanego interfejsu TIK i nowego zestawu kluczy usługi Azure Key Vault dostarczonych przez klienta.
  
Obecnie klucz klienta jest zaangażowany w łańcuch szyfrowania i odszyfrowywania danych plików usługi SharePoint Online przechowywanych w magazynie obiektów blob platformy Azure, ale nie SharePoint elementów listy online ani metadanych przechowywanych w SQL Database. Microsoft 365 nie używa klucza dostępności dla plików Exchange Online, Skype dla firm, SharePoint Online, OneDrive dla Firm i Teams innych niż opisany powyżej przypadek inicjowany przez klienta. Dostęp człowieka do danych klientów jest chroniony przez skrytki klienta.

## <a name="availability-key-triggers"></a>Wyzwalacze klucza dostępności

Microsoft 365 wyzwala klucz dostępności tylko w określonych okolicznościach. Te okoliczności różnią się w zależności od usługi.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Wyzwalacze dla Exchange Online i Skype dla firm
  
1. Microsoft 365 odczytuje program DEP, do którego jest przypisana skrzynka pocztowa w celu określenia lokalizacji dwóch kluczy klienta w usłudze Azure Key Vault.

2. Microsoft 365 losowo wybiera jeden z dwóch kluczy klienta z programu DEP i wysyła żądanie do usługi Azure Key Vault, aby odpakować klucz DEP przy użyciu klucza klienta.

3. Jeśli żądanie odpakowania klucza DEP przy użyciu klucza klienta zakończy się niepowodzeniem, Microsoft 365 wysyła drugie żądanie do usługi Azure Key Vault, tym razem nakazując mu użycie alternatywnego (drugiego) klucza klienta.

4. Jeśli drugie żądanie odpakowania klucza DEP przy użyciu klucza klienta zakończy się niepowodzeniem, Microsoft 365 zbada wyniki obu żądań.

    - Jeśli badanie ustali, że żądania nie zwróciły błędu systemu:

       - Microsoft 365 wyzwala klucz dostępności w celu odszyfrowania klucza DEP.

       - Microsoft 365 następnie używa klucza DEP do odszyfrowania klucza skrzynki pocztowej i ukończenia żądania użytkownika. 

       - W takim przypadku usługa Azure Key Vault nie jest w stanie odpowiedzieć lub nieosiągalna z powodu błędu przejściowego.

    - Jeśli badanie ustali, że żądania nie powiodły się, zwracając odmowę dostępu:

       - Oznacza to, że podjęto celowe, nieumyślne lub złośliwe działanie, aby uniemożliwić klientowi dostęp do kluczy (na przykład podczas procesu przeczyszczania danych w ramach opuszczania usługi).

       - W takim przypadku klucz dostępności będzie używany tylko w przypadku akcji systemowych, a nie akcji użytkownika, żądanie użytkownika kończy się niepowodzeniem, a użytkownik otrzymuje komunikat o błędzie.

> [!IMPORTANT]
> Microsoft 365 kod usługi zawsze ma prawidłowy token logowania do analizowania danych klientów w celu zapewnienia usług w chmurze dodających wartość. W związku z tym, dopóki klucz dostępności nie zostanie usunięty, może służyć jako rezerwa dla akcji inicjowanych przez Exchange Online i Skype dla firm, takich jak tworzenie indeksu wyszukiwania lub przenoszenie skrzynek pocztowych. Dotyczy to zarówno przejściowych błędów, jak i żądań ODMOWY DOSTĘPU do usługi Azure Key Vault.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Wyzwalacze dla plików SharePoint Online, OneDrive dla Firm i Teams

W przypadku plików SharePoint Online, OneDrive dla Firm i Teams klucz dostępności nigdy nie jest używany poza funkcją odzyskiwania, a klienci muszą jawnie poinstruować firmę Microsoft, aby zainicjowała użycie klucza dostępności podczas scenariusza odzyskiwania.

## <a name="audit-logs-and-the-availability-key"></a>Dzienniki inspekcji i klucz dostępności

Zautomatyzowane systemy w Microsoft 365 przetwarzają wszystkie dane, gdy przepływają przez system w celu świadczenia usług w chmurze, na przykład ochrony przed wirusami, e-odnajdywania, zapobiegania utracie danych i indeksowania danych. Microsoft 365 nie generuje dzienników widocznych dla klienta dla tego działania. Ponadto pracownicy firmy Microsoft nie uzyskują dostępu do danych w ramach tych normalnych operacji systemowych.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>rejestrowanie kluczy dostępności Exchange Online i Skype dla firm

Gdy Exchange Online i Skype dla firm uzyskują dostęp do klucza dostępności w celu zapewnienia usługi, Microsoft 365 publikuje dzienniki widoczne dla klientów dostępne w Centrum zabezpieczeń i zgodności. Rekord dziennika inspekcji dla operacji klucza dostępności jest generowany za każdym razem, gdy usługa używa klucza dostępności. Nowy typ rekordu o nazwie "Szyfrowanie usługi klucza klienta" z typem działania "Powrót do klucza dostępności" umożliwia administratorom [filtrowanie wyników wyszukiwania ujednoliconego dziennika inspekcji](./search-the-audit-log-in-security-and-compliance.md) w celu wyświetlenia rekordów klucza dostępności.

Rekordy dzienników obejmują atrybuty, takie jak data, godzina, działanie, identyfikator organizacji i identyfikator zasad szyfrowania danych. Rekord jest dostępny w ramach ujednoliconych dzienników inspekcji i jest dostępny na karcie Wyszukiwanie dzienników inspekcji w Centrum zgodności & zabezpieczeń.

![Przeszukiwanie dziennika inspekcji pod kątem zdarzeń klucza dostępności](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

rekordy kluczy Exchange Online i Skype dla firm dostępności używają [wspólnego schematu](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) działania zarządzania Office 365 z dodanymi parametrami niestandardowymi: identyfikatorem zasad, identyfikatorem wersji klucza zakresu i identyfikatorem żądania.

![Parametry niestandardowe klucza dostępności](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>rejestrowanie kluczy dostępności plików SharePoint Online, OneDrive dla Firm i Teams

Rejestrowanie klucza dostępności nie jest jeszcze dostępne dla tych usług. W przypadku plików SharePoint Online, OneDrive dla Firm i Teams klucz dostępności jest aktywowany przez firmę Microsoft tylko wtedy, gdy zostanie to przez Ciebie poinstruowane, na potrzeby odzyskiwania. W związku z tym znasz już każde zdarzenie, w którym klucz dostępności jest używany dla tych usług.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Klucz dostępności w hierarchii klucza klienta
  
Microsoft 365 używa klucza dostępności, aby opakować warstwę kluczy poniżej hierarchii kluczy ustanowionej na potrzeby szyfrowania usługi Klucz klienta. Między usługami istnieją różne hierarchie kluczy. Algorytmy kluczy różnią się również między kluczami dostępności i innymi kluczami w hierarchii każdej odpowiedniej usługi. Algorytmy klucza dostępności używane przez różne usługi są następujące:

- Klucze dostępności Exchange Online i Skype dla firm używają protokołu AES-256.

- Klucze dostępności plików SharePoint Online, OneDrive dla Firm i Teams używają RSA-2048.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Szyfry szyfrowania używane do szyfrowania kluczy dla Exchange Online i Skype dla firm

![Szyfry szyfrowania dla klucza klienta Exchange Online](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>Szyfry szyfrowania używane do szyfrowania kluczy dla usługi SharePoint Online i OneDrive dla Firm

![Szyfry szyfrowania dla klucza klienta SharePoint Online](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Artykuły pokrewne

- [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md)

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Tocz lub obracaj klucz klienta lub klucz dostępności](customer-key-availability-key-roll.md)
