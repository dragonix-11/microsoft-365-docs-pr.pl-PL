---
title: Informacje o kluczu dostępności dla klucza klienta
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
ms.openlocfilehash: 72e66e9deb74400944c6ea65ea3ac167a703da26
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985644"
---
# <a name="learn-about-the-availability-key-for-customer-key"></a>Informacje o kluczu dostępności dla klucza klienta

Klucz dostępności to klucz główny generowany automatycznie i zapewniany przy tworzeniu zasad szyfrowania danych. Microsoft 365 przechowywane i chroni klucz dostępności. Klucz dostępności działa podobnie do dwóch kluczy głównych, które pośrękujesz do szyfrowania usługi za pomocą klucza klienta. Klucz dostępności będzie otaczał klucze o jedną warstwę niższą niżej w hierarchii kluczy. Inaczej niż w przypadku kluczy, które dostarczasz i zarządzasz w magazynie kluczy platformy Azure, nie możesz uzyskać bezpośredniego dostępu do klucza dostępności. Microsoft 365, które programowo zarządzają kluczem dostępności. Te usługi inicjują zautomatyzowane operacje, które nigdy nie wymagają bezpośredniego dostępu do klucza dostępności.

Podstawowym celem klucza dostępności jest zapewnienie funkcji odzyskiwania po nieoczekiwanej utracie kluczy głównych, które zarządzasz. Utrata może być wynikiem nieuprawniania lub złośliwego działania. Jeśli utracisz kontrolę nad kluczami głównymi, skontaktuj się z pomocą techniczną firmy Microsoft, a firma Microsoft pomoże Ci w procesie odzyskiwania przy użyciu klucza dostępności. Użyjesz klucza dostępności, aby przeprowadzić migrację do nowych zasad szyfrowania danych z nowymi kluczami głównymi, które zapewniasz.

Storage kluczem dostępności i jego kontrolą są celowo inne niż klucze magazynu kluczy platformy Azure z trzech powodów:

- Klucz dostępności zapewnia odzyskiwanie, funkcję "break-glass", jeśli kontrola nad obu kluczami magazynu kluczy platformy Azure zostanie utracona.
- Rozdzielenie kontrolek logicznych i bezpiecznych lokalizacji przechowywania zapewnia szczegółową ochronę i ochronę przed utratą wszystkich kluczy i danych przed pojedynczym atakiem lub punktem awarii.
- Klucz dostępności zapewnia funkcję wysokiej dostępności, jeśli Microsoft 365 nie mogą się połączyć z kluczami hostowanych w magazynie kluczy platformy Azure z powodu błędów przejściowych. Ta reguła dotyczy tylko Exchange Online i Skype dla firm szyfrowania usługi. SharePoint online, OneDrive dla Firm i Teams nigdy nie używają klucza dostępności, chyba że jawnie poinstruujesz firmę Microsoft, aby zainicjowała proces odzyskiwania.

Współdzielenie odpowiedzialności za ochronę danych przy użyciu różnych zabezpieczeń i procesów zarządzania kluczami ostatecznie ogranicza ryzyko trwałej utraty lub traceniu wszystkich kluczy (a zatem danych). Podczas opuszczania usługi firma Microsoft udziela Ci wyłącznych uprawnień do wyłączania lub wyłączania klucza dostępności. Z tego względu nikt w firmie Microsoft nie ma dostępu do klucza dostępności: jest on dostępny tylko Microsoft 365 kodu usługi.

Aby uzyskać [więcej informacji na temat sposobu](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) zabezpieczania kluczy, zobacz Centrum zaufania firmy Microsoft.
  
## <a name="availability-key-uses"></a>Zastosowania klucza dostępności

Klucz dostępności umożliwia odzyskiwanie w scenariuszach, w których zewnętrzny maleńczy lub złośliwy niejawny tester ukraść kontrolę nad Twoim magazynem kluczy lub w przypadku przypadkowego błędu zarządzania powoduje utratę kluczy głównych. Ta funkcja odzyskiwania ma zastosowanie do wszystkich Microsoft 365 zgodnych z kluczem klienta. Poszczególne usługi używają klucza dostępności w inny sposób. Microsoft 365 korzysta z klucza dostępności tylko w sposób opisany poniżej.

### <a name="exchange-online-and-skype-for-business-uses"></a>Exchange Online i Skype dla firm używane

Poza możliwością odzyskiwania usługi Exchange Online i Skype dla firm, aby zapewnić dostępność danych podczas przejściowych lub sporadycznych problemów operacyjnych związanych z dostępem usługi do kluczy głównych. Gdy usługa nie może uzyskać dostępu do jednego z Twoich kluczy klienta w magazynie kluczy platformy Azure z powodu błędów przejściowych, usługa automatycznie używa klucza dostępności. Usługa NIGDY nie przechodzi bezpośrednio do klucza dostępności.

Automatyczne systemy w systemach Exchange Online i Skype dla firm mogą używać klucza dostępności podczas błędów przejściowych w celu obsługi automatycznych usług końcowych, takich jak oprogramowanie antywirusowe, wykrywanie e-discovery, ochrona przed utratą danych, przenoszenia skrzynek pocztowych i indeksowanie danych.

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-uses"></a>SharePoint online, OneDrive dla Firm i Teams używane pliki

W przypadku plików SharePoint Online, OneDrive dla Firm i Teams klucz dostępności NIE jest używany poza możliwością odzyskiwania, a klienci muszą jawnie poinstruować firmę Microsoft, aby zainicjowała korzystanie z klucza dostępności podczas scenariusza odzyskiwania. Automatyczne operacje serwisowe opierają się wyłącznie na kluczach klientów w magazynie kluczy platformy Azure. Aby uzyskać szczegółowe informacje na temat sposobu działania hierarchii kluczowych dla tych usług, zobacz Jak SharePoint w trybie online, OneDrive dla Firm i jak pliki Teams używają [klucza dostępności](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key).

## <a name="availability-key-security"></a>Zabezpieczenia klucza dostępności

Firma Microsoft spoczywa na Użytkowniku odpowiedzialność za ochronę danych, ponieważ nawiązała w ten sposób odpowiedzialność za klucz dostępności i mierzy, czy jest w stanie go chronić. Firma Microsoft nie udostępnia klientom bezpośredniej kontroli nad kluczem dostępności. Na przykład możesz wyłącznie obracać (obracać) klucze, których jesteś właścicielem w magazynie kluczy platformy Azure. Aby uzyskać więcej informacji, [zobacz Obracanie lub obracanie klucza klienta lub klucza dostępności](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Klucz dostępności tajnych magazynów

Firma Microsoft chroni klucze dostępności w wewnętrznych tajnych magazynach kontrolowanych przez dostęp, takich jak magazyn kluczy platformy Azure skierowany do klienta. Implementuje się mechanizmy kontroli dostępu, aby uniemożliwić administratorom firmy Microsoft bezpośredni dostęp do tajemnic, które się w nich znajdują. Operacje tajnych magazynów, w tym obrót i usuwanie klawiszy, są wykonywane za pośrednictwem zautomatyzowanych poleceń, które nigdy nie wymagają bezpośredniego dostępu do klucza dostępności. Operacje zarządzania tajnym magazynem są ograniczone do konkretnych inżynierów i wymagają eskalacji uprawnień za pośrednictwem wewnętrznego narzędzia Lockbox. Eskalacja uprawnień wymaga zatwierdzenia i uzasadnienia kierownika przed ich przyznanią. Skrytka zapewnia, że dostęp jest powiązany z automatycznym odwołań dostępu po wygaśnięciu czasu lub wylogowaniu inżyniera.

**Exchange Online klucza Skype dla firm** usługi Active Directory są przechowywane w Exchange Online tajnym usługi Active Directory. Klucze dostępności są bezpiecznie przechowywane wewnątrz kontenerów określonej dzierżawy w folderze usługi Active Directory Kontroler domeny. Ta bezpieczna lokalizacja przechowywania jest oddzielona i odizolowana od magazynu SharePoint Online, OneDrive dla Firm i Teams tajnych magazynów.

**SharePoint klucza dostępności plików OneDrive dla Firm online,** plików Teams oraz plików są przechowywane w wewnętrznym tajnym magazynie zarządzanym przez zespół usługi. Ta zabezpieczona usługa magazynu sekretów ma serwery frontonu z punktami końcowymi aplikacji i SQL Database jako back end. Klucze dostępności są przechowywane w p SQL Database i są zawijane (szyfrowane) przez klucze szyfrowania tajnego magazynu, które używają kombinacji AES-256 i HMAC do szyfrowania klucza dostępności w spoczynku. Klucze szyfrowania tajnego magazynu są przechowywane w logicznie odizolowanym składniku tego samego pakietu SQL Database i są dodatkowo szyfrowane przy użyciu kluczy RSA-2048 zawartych w certyfikatach zarządzanych przez urząd certyfikacji firmy Microsoft. Te certyfikaty są przechowywane na serwerach fronto stronie tajnego magazynu, które wykonują operacje na bazie danych.

### <a name="defense-in-depth"></a>Analiza obrony

Firma Microsoft stosuje strategię ochrony przed złośliwymi atakami, która ma na celu zapobieganie wpływaniu na poufność, integralność lub dostępność danych klientów przechowywanych w chmurze firmy Microsoft. W ramach strategii zabezpieczeń wdrażane są określone mechanizmy działań kontrolnych i kontrolnych w celu ochrony tajnego magazynu i klucza dostępności.

Microsoft 365, aby zapobiec błędnemu użyciu klucza dostępności. Warstwa aplikacji jest jedyną metodą, za pomocą której kluczy, w tym klucza dostępności, można używać do szyfrowania i odszyfrowywania danych. Tylko Microsoft 365 usługi może interpretować i przechodzić w ramach hierarchii kluczowych działań szyfrowania i odszyfrowywania. Istnieje izolacji logicznej lokalizacji przechowywania kluczy klienta, kluczy dostępności, innych kluczy hierarchicznych i danych klienta. Ta izolacji ogranicza ryzyko związanego z ekspozycją na dane w przypadku naruszenia jednej lub większej liczby lokalizacji. Każda warstwa w hierarchii ma wbudowane funkcje wykrywania zdarzeń 24 godziny na 7 dni w roku, aby chronić przechowywane dane i tajemnice.

Kontrolki dostępu są zaimplementowane, aby uniemożliwić nieautoryzowany dostęp do systemów wewnętrznych, w tym do tajnych magazynów kluczy dostępności. Inżynierowie firmy Microsoft nie mają bezpośredniego dostępu do tajnych magazynów klucza dostępności. Aby uzyskać dodatkowe informacje na temat kontroli dostępu, zapoznaj się z [administracyjnymi mechanizmami kontroli dostępu w programie Microsoft 365](/compliance/assurance/assurance-administrative-access-controls-overview).

Mechanizmy kontroli technicznej uniemożliwiają pracownikom firmy Microsoft logowanie się do bardzo uprzywilejowanych kont usług, które mogą być w inny sposób używane przez atakujących do personifikacji usługi firmy Microsoft. Na przykład te kontrolki uniemożliwiają interakcyjne logowanie.

Mechanizmy rejestrowania i monitorowania zabezpieczeń to kolejna zaimplementowana ochrona obrony, która pozwala na ograniczenie ryzyka usługi firmy Microsoft danych. Zespoły usług firmy Microsoft wdrożyły aktywne rozwiązania monitorujące, które generują alerty i dzienniki inspekcji. Wszystkie zespoły usługi przekażą swoje dzienniki do centralnego repozytorium, w którym dzienniki są agregowane i przetwarzane. Narzędzia wewnętrzne automatycznie analizują rekordy w celu potwierdzenia, że usługi działają w optymalnym, odpornej i bezpiecznym stanie. Nietypowe działania są oflagowywane do dalszego przeglądu.

Wszystkie zdarzenia dziennika wskazujące na potencjalne naruszenie zasad zabezpieczeń firmy Microsoft są natychmiast zwracane do zespołów ds. zabezpieczeń firmy Microsoft. Microsoft 365 zabezpieczenia skonfigurowali alerty w celu wykrycia prób uzyskania dostępu do tajnych magazynów kluczy dostępności. Alerty są również generowane, jeśli pracownicy firmy Microsoft próbują interakcyjne logować się na kontach usług, co jest zabronione i chronione przez mechanizmy kontroli dostępu. Microsoft 365 zabezpieczeń wykrywają również alerty i alerty po odchyleniu usługi Microsoft 365 względem normalnego planu bazowego. Manskładniki próbujące błędnie Microsoft 365 w usługach wywołują alerty, co powoduje wywwolenie przez offendera w środowisku chmury firmy Microsoft.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Odzyskiwanie po utracie klucza przy użyciu klucza dostępności

W przypadku utraty kontroli nad kluczami klienta klucz dostępności umożliwia odzyskanie i ponowne zaszyfrowanie danych.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>Procedura odzyskiwania dla Exchange Online i Skype dla firm

W przypadku utraty kontroli nad kluczami klienta klucz dostępności umożliwia odzyskanie danych i powrót zasobów Microsoft 365 w tryb online. Klucz dostępności będzie nadal chronił dane podczas odzyskiwania. Na wysokim poziomie, aby w pełni odzyskać dostęp do danych po utracie klucza, musisz utworzyć nową funkcje DEP i przenieść zasoby, na które wpływa ta utrata, do nowych zasad.

Aby zaszyfrować dane przy użyciu nowych kluczy klienta, utwórz nowe klucze w magazynie kluczy platformy Azure, utwórz nowy element DEP przy użyciu nowych kluczy klientów, a następnie przypisz nowy element DEP do skrzynek pocztowych zaszyfrowanych obecnie przy użyciu poprzedniego funkcji DEP, w przypadku której klucze zostały utracone lub naruszone.

Ten proces ponownego szyfrowania może potrwać do 72 godzin. Jest to standardowy czas trwania po zmianie funkcji DEP.
  
### <a name="recovery-procedure-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Procedura odzyskiwania dla SharePoint Online, OneDrive dla Firm i Teams plików

W SharePoint plików online, OneDrive dla Firm i Teams klucz dostępności NIE jest używany poza możliwością odzyskiwania. Należy jawnie poinstruować firmę Microsoft, aby zainicjowała korzystanie z klucza dostępności podczas scenariusza odzyskiwania. Aby zainicjować proces odzyskiwania, skontaktuj się z firmą Microsoft w celu aktywowania klucza dostępności. Po aktywowaniu klucz dostępności jest automatycznie używany do odszyfrowywania danych, co pozwala zaszyfrować dane przy użyciu nowo utworzonego funkcji DEP skojarzonej z nowymi kluczami klienta.  

Ta operacja jest proporcjonalna do liczby witryn w organizacji. Gdy zadzwonisz do firmy Microsoft w celu użycia klucza dostępności, powinno być w pełni online w ciągu około czterech godzin.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Jak Exchange Online i Skype dla firm z klucza dostępności

Po utworzeniu funkcji DEP przy użyciu klucza klienta funkcja Microsoft 365 generuje klucz zasad szyfrowania danych (klucz dep) skojarzony z tym funkcją DEP. Usługa szyfruje klucz funkcji DEP trzy razy: raz z każdym kluczem klienta i raz przy użyciu klucza dostępności. Przechowywane są tylko zaszyfrowane wersje klucza funkcji DEP, a klucz funkcji DEP można odszyfrowywać tylko przy użyciu kluczy klienta lub klucza dostępności. Klawisz DEP jest następnie używany do szyfrowania kluczy skrzynek pocztowych, które szyfrują poszczególne skrzynki pocztowe.
  
Microsoft 365 ten proces w celu odszyfrowania i podania danych, gdy klienci będą korzystać z usługi:
  
1. Odszyfrowywanie klucza funkcji DEP przy użyciu klucza klienta.

2. Odszyfrowany klucz funkcji DEP odszyfrowywuje klucz skrzynki pocztowej.

3. Odszyfrowany klucz skrzynki pocztowej umożliwia odszyfrowanie samej skrzynki pocztowej, co umożliwia uzyskanie dostępu do danych w skrzynce pocztowej.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>Jak SharePoint online, OneDrive dla Firm i Teams używają klucza dostępności

Architektura SharePoint online OneDrive dla Firm i implementacja klucza klienta oraz klucza dostępności różnią się od Exchange Online i Skype dla firm.
  
Gdy organizacja przechodzi do kluczy zarządzanych przez klienta, program Microsoft 365 klucz pośredni (TIK) dla organizacji. Microsoft 365 dwa razy szyfruje TIK przy użyciu każdego z kluczy klienta i przechowuje dwie zaszyfrowane wersje TIK. Przechowywane są tylko zaszyfrowane wersje TIK, a TIK można odszyfrowywać tylko za pomocą kluczy klienta. TIK jest następnie używana do szyfrowania kluczy witryny, które są następnie używane do szyfrowania kluczy obiektów blob (nazywanych również kluczami fragmentu pliku). W zależności od rozmiaru pliku usługa może podzielić plik na wiele fragmentów przy użyciu unikatowego klucza. Same obiekty blob (fragmenty plików) są szyfrowane przy użyciu kluczy obiektów blob i przechowywane w Microsoft Azure magazynu obiektów blob.
  
Microsoft 365 ten proces odszyfrowywania i odszyfrowywania plików klientów, gdy klienci będą korzystać z usługi:

1. Odszyfrowywanie TIK przy użyciu klucza klienta.

2. Odszyfrowany klucz witryny można odszyfrowywać przy użyciu TIK.

3. Odszyfrowany klucz witryny do odszyfrowania klucza obiektu blob.

4. Odszyfrowany klucz obiektu blob ma na celu odszyfrowanie tego obiektu blob.

Microsoft 365 odszyfrowuje TIK, wystawiając dwa żądania odszyfrowywania do magazynu kluczy platformy Azure z niewielkim przesunięciem. Pierwszy, który ma zakończyć subskrypcję, anuluje drugie żądanie.
  
W przypadku utraty dostępu do kluczy klienta kod Microsoft 365 również szyfruje TIK za pomocą klucza dostępności i przechowuje ten kod razem z kodami TIKs zaszyfrowanymi z każdym kluczem klienta. Kod TIK zaszyfrowany za pomocą klucza dostępności jest używany tylko wtedy, gdy klient dzwoni do firmy Microsoft w celu uzyskania ścieżki odzyskiwania, gdy utracił dostęp do swoich kluczy, złośliwego lub przypadkowego.
  
Ze względu na dostępność i skalę odszyfrowane tiksy są przechowywane w pamięci podręcznej z ograniczoną limitem czasu pamięci. Dwie godziny przed wygaśnięciem pamięci podręcznej TIK może na Microsoft 365 próby odszyfrowania każdego z tych danych. Odszyfrowywanie zestawów TIKs rozszerza okres istnienia pamięci podręcznej. Jeśli odszyfrowywanie TIK nie powiedzie się przez znaczący czas, Microsoft 365 zostanie wygenerowany alert powiadamiający o danych inżynierskich przed wygaśnięciem pamięci podręcznej. Tylko jeśli klient dzwoni do firmy Microsoft, Microsoft 365 inicjuje operację odzyskiwania, która obejmuje odszyfrowywanie TIK przy użyciu klucza dostępności przechowywanego w tajnym magazynie firmy Microsoft i ponownie dołączanie dzierżawy przy użyciu odszyfrowanych TIK i nowego zestawu kluczy magazynu kluczy dostarczonych przez klienta.
  
Obecnie klucz klienta jest związany z łańcuchem szyfrowania i odszyfrowywania danych plików usługi SharePoint Online przechowywanych w magazynie obiektów blob platformy Azure, ale nie elementów list i metadanych przechowywanych w usłudze SharePoint Online przechowywanych w SQL Database. Microsoft 365 nie korzysta z klucza dostępności dla plików Exchange Online, Skype dla firm, SharePoint Online, OneDrive dla Firm i Teams innych niż opisane powyżej przypadku, który jest inicjowany przez klienta. Dostęp użytkowników do danych klientów jest chroniony przez skrytkę klienta.

## <a name="availability-key-triggers"></a>Wyzwalacze klucza dostępności

Microsoft 365 klucz dostępności jest wyzwalany tylko w określonych okolicznościach. Te okoliczności różnią się w zależności od usługi.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Wyzwalacze dla Exchange Online i Skype dla firm
  
1. Microsoft 365 odczytuje element DEP, do którego przypisano skrzynkę pocztową, w celu określenia lokalizacji dwóch kluczy klienta w magazynie kluczy platformy Azure.

2. Microsoft 365 losowo wybiera jeden z dwóch kluczy klienta z funkcji DEP i wysyła żądanie do magazynu kluczy platformy Azure w celu cofwienia klucza funkcji DEP przy użyciu klucza klienta.

3. Jeśli żądanie cofania dezkomplacji klucza funkcji DEP przy użyciu klucza klienta nie powiedzie się, usługa Microsoft 365 wyśle drugie żądanie do magazynu kluczy platformy Azure, tym razem instruuje go, aby używał alternatywnego (drugiego) klucza klienta.

4. Jeśli drugie żądanie cofniania naciśnięcia klawisza DEP przy użyciu klucza klienta kończy się niepowodzeniem, Microsoft 365 sprawdza wyniki obu żądań.

    - Jeśli jednak wynika z tego, że żądania nie zwróciły błędu systemowego:

       - Microsoft 365 wyzwala klucz dostępności w celu odszyfrowania klucza funkcji DEP.

       - Microsoft 365 następnie używa klawisza DEP do odszyfrowywania klucza skrzynki pocztowej i pełnego żądania użytkownika. 

       - W tym przypadku magazyn kluczy platformy Azure nie może odpowiedzieć lub jest nieosiągalny z powodu błędu chwilowego.

    - Jeśli zwrócone żądania nie powiodły się, a program ACCESS DENIED:

       - Oznacza to, że klucze klienta są niedostępne (na przykład w ramach procesu przeczyszczania danych w ramach opuszczania usługi) wykonane zostały celowe, przypadkowe lub złośliwe działania.

       - W tym przypadku klucz dostępności będzie używany tylko do akcji systemowych, a nie do akcji użytkownika, żądania użytkownika kończy się niepowodzeniem i użytkownik otrzymuje komunikat o błędzie.

> [!IMPORTANT]
> Microsoft 365 usługi zawsze ma prawidłowy token logowania, który zawiera uzasadnienie dla danych klienta w celu zapewnienia usług w chmurze o dodawaniu wartości. Dlatego do czasu usunięcia klucza dostępności można go używać jako rezerwy dla akcji inicjowanych przez firmy Exchange Online i Skype dla firm, takich jak tworzenie indeksu wyszukiwania lub przenoszenie skrzynek pocztowych. Dotyczy to zarówno błędów przejściowych, jak i żądań ACCESS DENIED do magazynu kluczy platformy Azure.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Wyzwalacze dla SharePoint online, OneDrive dla Firm i Teams plików

W przypadku plików SharePoint Online, OneDrive dla Firm i Teams klucz dostępności NIE jest używany poza możliwością odzyskiwania, a klienci muszą jawnie poinstruować firmę Microsoft, aby zainicjowała korzystanie z klucza dostępności podczas scenariusza odzyskiwania.

## <a name="audit-logs-and-the-availability-key"></a>Dzienniki inspekcji i klucz dostępności

Automatyczne systemy w Microsoft 365 przetwarzają wszystkie dane przepływane przez system w celu zapewnienia usług w chmurze, na przykład oprogramowania antywirusowego, wykrywania elektronicznego, ochrony przed utratą danych i indeksowania danych. Microsoft 365 nie generuje dzienników tego działania widocznych dla klienta. Ponadto pracownicy firmy Microsoft nie mają dostępu do Twoich danych w ramach tych normalnych operacji systemowych.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>Exchange Online i Skype dla firm klucz dostępności

Gdy Exchange Online i Skype dla firm dostępu do klucza dostępności w celu świadczenia usługi, Microsoft 365 dzienniki widoczne dla klienta dostępne z Centrum zabezpieczeń i zgodności. Rekord dziennika inspekcji dla operacji klucza dostępności jest generowany za każdym razem, gdy usługa korzysta z klucza dostępności. Nowy typ rekordu o nazwie "Szyfrowanie usługi klucza klienta" z typem działania "Rezerwa na klucz dostępności" umożliwia administratorom [](./search-the-audit-log-in-security-and-compliance.md) filtrowanie wyników wyszukiwania ujednoliconego dziennika inspekcji w celu wyświetlania rekordów kluczy dostępności.

Rekordy dziennika zawierają atrybuty, takie jak data, godzina, działanie, identyfikator organizacji i identyfikator zasad szyfrowania danych. Rekord jest dostępny w ramach ujednoliconych dzienników inspekcji i dostępny z karty Przeszukiwanie dziennika inspekcji w Centrum & zabezpieczeń.

![Przeszukiwanie dziennika inspekcji w celu wyszukania kluczowych zdarzeń dostępności](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

Exchange Online i Skype dla firm dostępności używają wspólnego schematu działań zarządzania Office 365 z dodanymi parametrami niestandardowymi[](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema): Identyfikator zasad, Identyfikator wersji klucza zakresu i Identyfikator żądania.

![Parametry niestandardowe kluczowych klawiszy dostępności](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>SharePoint klucz dostępności plików OneDrive dla Firm online, Teams i plików

Rejestrowanie klucza dostępności nie jest jeszcze dostępne dla tych usług. W SharePoint online, OneDrive dla Firm i Teams klucz dostępności jest aktywowany tylko przez firmę Microsoft, zgodnie z instrukcjami użytkownika, na potrzeby odzyskiwania. Dzięki temu wiesz już wszystkie zdarzenia, w których klucz dostępności jest używany dla tych usług.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Klucz dostępności w hierarchii Klucz klienta
  
Microsoft 365 używa klucza dostępności do zawijania warstwy kluczy niższej w hierarchii kluczy ustanowionej dla szyfrowania usługi klucza klienta. W usługach istnieją różne hierarchie kluczy. Algorytmy klucza różnią się również w przypadku kluczy dostępności od innych kluczy w hierarchii poszczególnych usług. Algorytmy klucza dostępności używane przez różne usługi są następujące:

- Klucz Exchange Online i Skype dla firm dostępności używają skrótu AES-256.

- Klucze SharePoint online, OneDrive dla Firm i Teams używają programu RSA-2048.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Szyfruj szyfrowania używane do szyfrowania kluczy do Exchange Online i Skype dla firm

![Encryption ciphers for Exchange Online customer key](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>Szyfrowania używane do szyfrowania kluczy do szyfrowania wiadomości SharePoint Online i OneDrive dla Firm

![Encryption ciphers for SharePoint Online Customer Key](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Artykuły pokrewne

- [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md)

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Obracanie lub obracanie klucza klienta lub klucza dostępności](customer-key-availability-key-roll.md)