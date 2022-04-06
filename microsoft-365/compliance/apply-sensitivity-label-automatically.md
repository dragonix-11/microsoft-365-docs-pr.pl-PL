---
title: Automatyczne stosowanie etykiet wrażliwości do zawartości w Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Po utworzeniu etykiety wrażliwości możesz automatycznie przypisać etykietę do plików i wiadomości e-mail lub poprosić użytkowników o wybranie etykiety, która jest zalecana.
ms.openlocfilehash: 21ee443ba9bab0ac7071377befee5d6e6143a398
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634630"
---
# <a name="apply-a-sensitivity-label-to-content-automatically"></a>Automatyczne stosowanie etykiety poufności do zawartości

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Aby uzyskać informacje na temat automatycznego stosowania etykiety wrażliwości w usłudze Azure Purview, zobacz [Oznaczanie etykiet w usłudze Azure Purview](/azure/purview/create-sensitivity-label).

Po utworzeniu etykiety wrażliwości możesz ją automatycznie przypisać do plików i wiadomości e-mail, jeśli jest ona taka, jaka jest do warunków określonych przez Ciebie.

Ta możliwość automatycznego stosowania etykiet wrażliwości do zawartości jest ważna, ponieważ:

- Nie musisz szkolenie użytkowników, kiedy należy używać każdej z klasyfikacji.

- Nie musisz polegać na użytkownikach, aby prawidłowo klasyfikować całą zawartość.

- Użytkownicy nie muszą już znać twoich zasad — zamiast tego mogą skoncentrować się na swojej pracy.

Istnieją dwie różne metody automatycznego stosowania etykiet wrażliwości do zawartości w Microsoft 365:

- **Etykiety po** stronie klienta, gdy użytkownicy edytują dokumenty lub tworzą wiadomości e-mail (także odpowiadaj na nie lub przesyłaj je dalej): użyj etykiety skonfigurowanej do automatycznego oznaczania plików i wiadomości e-mail (obejmuje Excel, PowerPoint i Outlook).

    Ta metoda obsługuje polecanie etykiet użytkownikom, a także automatyczne stosowanie etykiety. Jednak w obu przypadkach użytkownik decyduje, czy zaakceptować, czy odrzucić tę etykietę w celu zapewnienia prawidłowego oznaczania zawartości. To etykiety po stronie klienta mają minimalne opóźnienia w przypadku dokumentów, ponieważ tę etykietę można zastosować nawet przed zapisaniem dokumentu. Jednak nie wszystkie aplikacje klienckie obsługują automatyczne oznaczanie etykiet. Ta funkcja jest obsługiwana przez wbudowane etykiety w niektórych wersjach programu [Office](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps), a także w kliencie usługi Azure Information Protection etykiet ujednoliconej.

    Aby uzyskać instrukcje dotyczące konfiguracji, [zobacz Jak skonfigurować automatyczne oznaczanie etykiet dla Office na](#how-to-configure-auto-labeling-for-office-apps) tej stronie.

- **Etykiety** po stronie usługi, gdy zawartość jest już zapisana (w usłudze SharePoint lub OneDrive) lub wysłana pocztą e-mail (przetwarzana przez Exchange Online): Użyj zasad automatycznego oznaczania.
    
    Możesz również usłyszeć tę metodę, określaną mianem automatycznego oznaczania danych w spoczynku (dokumenty w systemach SharePoint i OneDrive) oraz przesyłanych danych (wiadomości e-mail wysyłanych lub otrzymywanych przez Exchange). Na Exchange wiadomości e-mail nie są uwzględniane w spoczynku (skrzynki pocztowe).
    
    Ponieważ to etykiety są stosowane przez usługi, a nie przez aplikacje, nie musisz martwić się o to, jakie aplikacje mają użytkownicy i która wersja. W efekcie ta funkcja jest natychmiast dostępna w całej organizacji i nadaje się do stosowania etykiet w skali. Zasady automatycznego oznaczania etykiet nie obsługują zalecanych etykiet, ponieważ użytkownik nie wchodzi w interakcję z procesem oznaczania. Zamiast tego administrator uruchamia zasady w sposób symulowany, aby zapewnić prawidłowe etykiety zawartości przed ich zastosowaniem.

    Aby uzyskać instrukcje dotyczące konfiguracji, zobacz Jak skonfigurować zasady automatycznego oznaczania etykiet dla SharePoint[, OneDrive i](#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) Exchange na tej stronie.
    
    Specyficzne dla automatycznego oznaczania etykiet dla SharePoint i OneDrive:
    
    - Office dla programu Word (.docx), PowerPoint (.pptx) i Excel (.xlsx).
        - Te pliki można automatycznie oznaczać etykietami w miejscu przed lub po utworzeniu zasad automatycznego oznaczania etykiet. Plików nie można automatycznie oznaczać, jeśli są częścią otwartej sesji (plik jest otwarty).
        - Obecnie załączniki do elementów listy nie są obsługiwane i nie są oznaczane automatycznie.
    - Maksymalnie 25 000 automatycznie oznaczonych plików w dzierżawie dziennie.
    - Maksymalnie 100 zasad automatycznego oznaczania na dzierżawcę, przy każdym określaniu docelowych wartości docelowych do 100 witryn (SharePoint lub OneDrive), jeśli są określone indywidualnie. Możesz także określić wszystkie witryny, a ta konfiguracja będzie wykluczana z maksymalnej liczby 100 witryn.
    - Istniejące wartości modyfikacji, modyfikacji i daty nie są zmieniane w wyniku zasad automatycznego oznaczania etykiet — zarówno w trybie symulowania, jak i podczas stosowania etykiet.
    - Gdy etykieta stosuje szyfrowanie [, wystawca](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) zarządzania prawami i właściciel zarządzania prawami to konto, które ostatnio zmodyfikował plik. Jeśli tego konta nie ma Azure Active Directory, etykiety nie można ustawić, ponieważ tych wartości nie można ustawić.

    Specyficzne dla automatycznego oznaczania etykiet dla Exchange:
    
    - W odróżnieniu od ręcznego oznaczania etykiet lub automatycznego oznaczania etykiet za pomocą aplikacji pakietu Office załączniki PDF oraz załączniki Office są również skanowane w celu zachowania określonych warunków określonych w zasadach automatycznego oznaczania etykiet. W przypadku dopasowania wiadomość e-mail jest oznaczona etykietą, ale nie załącznikiem.
        - W przypadku plików PDF, jeśli etykieta stosuje szyfrowanie, te pliki są szyfrowane przy użyciu narzędzia [Office 365 Message Encryption (OME),](ome.md) gdy dla dzierżawy włączono [załączniki PDF](ome-faq.yml#are-pdf-file-attachments-supported-).
        - Dla tych Office obsługiwane są pliki programu Word, PowerPoint i Excel. Jeśli etykieta stosuje szyfrowanie, są one szyfrowane przy użyciu Office 365 [OME (Message Encryption).](ome.md)
    - Jeśli masz reguły przepływu poczty e-mail lub zasady ochrony przed utratą danych (DLP), które stosują szyfrowanie IRM: jeśli zawartość jest identyfikowana przez te reguły i zasady automatycznego oznaczania etykiet, etykieta jest stosowana. Exchange Jeśli ta etykieta ma zastosowanie szyfrowanie, ustawienia usługi IRM na Exchange przepływu poczty e-mail lub zasady DLP są ignorowane. Jeśli jednak etykieta nie zastosuje szyfrowania, oprócz etykiety zostaną zastosowane ustawienia usługi IRM z reguł przepływu poczty e-mail lub zasad DLP.
    - Wiadomość e-mail z szyfrowaniem IRM bez etykiet zostanie zastąpiona etykietą z dowolnymi ustawieniami szyfrowania, jeśli zostanie dopasowana za pomocą automatycznego oznaczania etykiet.
    - Przychodząca wiadomość e-mail jest oznaczana w przypadku dopasowania do warunków automatycznego oznaczania etykiet. Jeśli ta etykieta jest skonfigurowana do [szyfrowania](encryption-sensitivity-labels.md), to szyfrowanie jest zawsze stosowane, gdy nadawca pochodzi z Twojej organizacji. Domyślnie to szyfrowanie nie jest stosowane, gdy nadawca znajduje się poza organizacją, ale można je zastosować, konfigurując  dodatkowe ustawienia poczty e-mail i określając właściciela zarządzania prawami.
    - Gdy etykieta stosuje szyfrowanie, wystawca usługi zarządzanie prawami i właściciel usługi [zarządzania](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) prawami to osoba, która wysyła wiadomość e-mail, gdy nadawca pochodzi z Twojej organizacji. Jeśli nadawca znajduje się poza organizacją, możesz określić właściciela zarządzania prawami dostępu dla przychodzącej wiadomości e-mail oznaczonej i zaszyfrowanej przez zasady.
    - Jeśli etykieta jest skonfigurowana do stosowania oznaczenia [dynamicznego,](sensitivity-labels-office-apps.md#dynamic-markings-with-variables) należy pamiętać, że w przypadku przychodzących wiadomości e-mail ta konfiguracja może spowodować wyświetlanie imion i nazwisk osób spoza organizacji.

## <a name="compare-auto-labeling-for-office-apps-with-auto-labeling-policies"></a>Porównanie automatycznego oznaczania etykiet dla aplikacji Office z zasadami automatycznego oznaczania etykiet

Skorzystaj z poniższej tabeli, aby ułatwić zidentyfikowanie różnic w zachowaniu dwóch dopełniających metod automatycznego oznaczania etykiet:

|Funkcja lub zachowanie|Ustawienie etykiet: automatyczne oznaczanie plików i wiadomości e-mail  |Zasady: Automatyczne oznaczanie etykiet|
|:-----|:-----|:-----|
|Zależność aplikacji|Tak ([minimalne wersje](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)) |Nie \* |
|Ograniczanie według lokalizacji|Nie |Tak |
|Warunki: Klasyfikatorzy przeszkoli|Tak |Nie |
|Warunki: Opcje udostępniania i dodatkowe opcje dla poczty e-mail|Nie |Tak |
|Warunki: Wyjątki|Nie |Tak (tylko poczta e-mail) |
|Rekomendacje, etykietka narzędzia zasad i zastępowanie użytkownika|Tak |Nie |
|Tryb symulowania|Nie |Tak |
|Exchange sprawdzane pod kątem warunków|Nie | Tak|
|Stosowanie oznaczeń wizualnych |Tak |Tak (tylko poczta e-mail) |
|Zastępowanie szyfrowania IRM zastosowanego bez etykiety|Tak, jeśli użytkownik ma minimalne prawo do korzystania z eksportu |Tak (tylko poczta e-mail) |
|Etykieta przychodzącej wiadomości e-mail|Nie |Tak|
|Przypisywanie właściciela zarządzania prawami do wiadomości e-mail wysłanych z innej organizacji |Nie |Tak|
|W przypadku wiadomości e-mail zamień istniejącą etykietę o tym samym lub niższym priorytecie |Nie |Tak (możliwość konfigurowania)|

\* Automatyczne oznaczanie etykiet nie jest obecnie dostępne we wszystkich regionach ze względu na współzależność platformy Azure w ramach zaplecza. Jeśli dzierżawa nie obsługuje tej funkcji, karta **Auto etykiety** nie jest widoczna w centrum zgodności. Aby uzyskać więcej informacji, zobacz [Dostępność platformy Azure w zależności od kraju](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Jak ocenia się wiele warunków, gdy dotyczą więcej niż jednej etykiety

Etykiety są uporządkowane do oceny zgodnie z ich położeniem, które zostało określone w zasadach: Etykieta pozycjonowana jako pierwsza ma najmniejszą pozycję (najmniejsza poufne), a ostatnia etykieta ma największą pozycję (najbardziej wrażliwą). Aby uzyskać więcej informacji o priorytecie, zobacz [Priorytet etykiety (pierwszeństwo zamówień ma znaczenie).](sensitivity-labels.md#label-priority-order-matters)

## <a name="dont-configure-a-parent-label-to-be-applied-automatically-or-recommended"></a>Nie konfiguruj etykiety nadrzędnej do automatycznego lub zalecanego zastosowania

Pamiętaj, że do zawartości nie można zastosować etykiety nadrzędnej (etykiety z pod etykietami). Upewnij się, że nie skonfigurowano etykiety nadrzędnej do automatycznego stosowania lub polecania w aplikacjach pakietu Office i nie wybieraj etykiety nadrzędnej dla zasad automatycznego oznaczania etykiet. Jeśli to zrobisz, etykieta nadrzędna nie zostanie zastosowana do zawartości.

Aby użyć etykiet automatycznych z pod etykietami, upewnij się, że publikujesz zarówno etykietę nadrzędną, jak i etykietę podrzędną.

Aby uzyskać więcej informacji na temat etykiet nadrzędnych i pod etykiet, zobacz Etykiety podrzędne [(etykiety grupowania).](sensitivity-labels.md#sublabels-grouping-labels)

## <a name="will-an-existing-label-be-overridden"></a>Czy istniejąca etykieta zostanie zastąpiona?

> [!NOTE]
> Niedawno dodane ustawienie zasad automatycznego oznaczania wiadomości e-mail umożliwia określenie, że pasującą etykietę wrażliwości zawsze zastępuje istniejącą etykietę.

Zachowanie domyślne niezależnie od tego, czy etykiety automatyczne zastąpią istniejącą etykietę:

- Jeśli zawartość została oznaczona ręcznie etykietą, etykieta ta nie zostanie zastąpiona etykietą automatyczną.

- Automatyczne oznaczanie etykiet spowoduje zastąpienie etykiety [wrażliwości o niższym priorytecie](sensitivity-labels.md#label-priority-order-matters) , która została automatycznie zastosowana, ale nie będzie miała wyższego priorytetu.
    
    > [!TIP]
    > Na przykład etykieta poufności u góry listy w Centrum zgodności ma nazwę Publiczny z numerem zamówienia (priorytet) 0, a etykieta wrażliwości u dołu listy nosi nazwę Wysoce poufne z numerem zamówienia (priorytet 4). **Etykieta Wysoce poufne** może zastąpić **etykietę** publiczną, ale nie na drugi sposób.

W przypadku zasad automatycznego oznaczania wiadomości e-mail możesz wybrać ustawienie, które zawsze zastępuje istniejącą etykietę wrażliwości, niezależnie od tego, jak została zastosowana.

|Istniejąca etykieta |Zastępowanie za pomocą ustawienia etykiet: Automatyczne oznaczanie plików i wiadomości e-mail  |Zastępowanie przy użyciu zasad: automatyczne oznaczanie etykiet|
|:-----|:-----|:-----|
|Stosowane ręcznie, dowolny priorytet|Word, Excel, PowerPoint: Nie <br /><br> Outlook: Nie  |SharePoint i OneDrive: Nie <br /><br> Exchange: Domyślnie nie, ale można je skonfigurować |
|Etykieta automatycznie zastosowana lub domyślna z zasad o niskim priorytecie |Word, Excel, PowerPoint: Tak <br /><br> Outlook: Tak | SharePoint i OneDrive: Tak <br /><br> Exchange: Tak |
|Etykieta automatycznie zastosowana lub domyślna z zasad, wyższy priorytet |Word, Excel, PowerPoint: Nie <br /><br> Outlook: Nie |SharePoint i OneDrive: Nie <br /><br> Exchange: Domyślnie nie, ale można je skonfigurować |

Konfigurowalne ustawienie zasad automatycznego oznaczania wiadomości e-mail znajduje się na **stronie Dodatkowe ustawienia dla poczty e-mail** . Ta strona zostanie wyświetlona po wybraniu etykiety wrażliwości dla zasad automatycznego oznaczania, które zawierają Exchange lokalizacji.

## <a name="how-to-configure-auto-labeling-for-office-apps"></a>Jak skonfigurować automatyczne etykiety dla Office aplikacji

Aby uzyskać wbudowane etykiety w Office, sprawdź minimalne wersje wymagane do automatycznego oznaczania etykiet w Office aplikacjach.[](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)

Klient ujednoliconej etykiet usługi Azure Information Protection obsługuje automatyczne oznaczanie etykiet tylko dla wbudowanych i niestandardowych typów informacji poufnych i nie obsługuje klasyfikatorów przeszkolnych ani typów informacji poufnych, które używają funkcji Dokładne dopasowanie danych (EDM) lub nazwanych obiektów.

Ustawienia automatycznego oznaczania etykiet dla Office są dostępne po utworzeniu lub [edytowaniu etykiety wrażliwości](create-sensitivity-labels.md). Upewnij się **& że** w zakresie etykiety wybrano opcję Pliki i wiadomości e-mail:

![Opcje zakresu etykiet wrażliwości dla plików i wiadomości e-mail.](../media/filesandemails-scope-options-sensitivity-label.png)

Podczas poruszania się po konfiguracji jest wyświetlona strona Automatyczne oznaczanie plików i wiadomości **e-mail** , na której możesz wybrać z listy typów informacji poufnych lub przeszkolnych klasyfikatorów:

![Label conditions for auto-labeling in Office apps.](../media/sensitivity-labels-conditions.png)

Gdy ta etykieta wrażliwości zostanie automatycznie zastosowana, użytkownik zobaczy powiadomienie w aplikacja pakietu Office. Przykład:

![Powiadomienie o tym, że w dokumencie zastosowano etykietę automatycznie.](../media/sensitivity-labels-msg-doc-was-auto-labeled.PNG)

### <a name="configuring-sensitive-info-types-for-a-label"></a>Konfigurowanie typów informacji poufnych dla etykiety

Po wybraniu opcji **Typy informacji poufnych** jest dostępna ta sama lista typów informacji poufnych co podczas tworzenia zasad ochrony przed utratą danych (DLP). W związku z tym możesz na przykład automatycznie zastosować etykietę o wysokim poufnej treści do dowolnej zawartości zawierającej dane osobowe klientów, na przykład numery kart kredytowych, numery PESEL czy numery paszportów:

![Typy informacji poufnych do automatycznego oznaczania etykiet w Office aplikacjach.](../media/sensitivity-labels-sensitive-info-types.png)

Podobnie jak podczas konfigurowania zasad DLP można uściślić warunek, zmieniając liczbę wystąpień i dokładność dopasowania. Przykład:

![Opcje dokładności dopasowania i liczby wystąpień.](../media/sit-confidence-level.png)

Więcej informacji o tych opcjach konfiguracji można znaleźć w dokumentacji dotyczącej zasad DLP: Dostosowywanie reguł tak, aby były łatwiejsze lub [trudniejsze do dopasowania](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Typy informacji poufnych mają dwa różne sposoby definiowania parametrów maksymalnej liczby unikatowych wystąpień. Aby dowiedzieć się więcej, zobacz [Obsługiwane wartości liczby wystąpień dla usługi SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Podobnie jak w przypadku konfiguracji zasad DLP można określić, czy warunek ma wykrywać wszystkie typy informacji poufnych, czy tylko jeden z nich. Aby twoje warunki bardziej elastyczne lub złożone, można dodawać grupy i używać operatorów logicznych [między grupami](data-loss-prevention-policies.md).

> [!NOTE]
> Automatyczne oznaczanie etykietami opartymi na niestandardowych typach informacji poufnych dotyczy tylko nowo utworzonej lub zmodyfikowanej zawartości w OneDrive i SharePoint, a nie do istniejącej zawartości. Niniejsze ograniczenie dotyczy również zasady automatycznego oznaczania etykiet.

#### <a name="custom-sensitive-information-types-with-exact-data-match"></a>Niestandardowe typy informacji poufnych z dokładnym dopasowaniem danych

Możesz skonfigurować etykietę wrażliwości, [aby dla niestandardowych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) typów informacji poufnych używać dokładnych typów informacji poufnych opartych na danych. Jednak obecnie musisz także określić co najmniej jeden rodzaj informacji poufnych, który nie korzysta z funkcji EDM. Może to być na przykład jeden z wbudowanych typów informacji poufnych, na przykład **numer karty kredytowej**.

Jeśli skonfigurujesz etykietę wrażliwości tylko przy użyciu funkcji EDM dla warunków typu informacji poufnych, ustawienie automatycznego oznaczania etykiety zostanie automatycznie wyłączone.

### <a name="configuring-trainable-classifiers-for-a-label"></a>Konfigurowanie klasyfikatorów przeszkolnych dla etykiety

Jeśli używasz tej opcji z programem Aplikacje Microsoft 365 dla systemu Windows w wersji 2106 lub niższej albo Aplikacje Microsoft 365 dla komputerów Mac w wersji 16.50 lub niższej, upewnij się, że opublikowano w dzierżawie co najmniej jedną inną etykietę wrażliwości skonfigurowaną do automatycznego oznaczania etykiet i opcję informacji poufnych[.](#configuring-sensitive-info-types-for-a-label) To wymaganie nie jest konieczne, gdy używasz nowszych wersji na tych platformach.

Po wybraniu opcji **Klasyfikatorzy** przeszkolone wybierz co najmniej jeden z wstępnie przeszkolonych lub niestandardowych przeszkolonych klasyfikatorów:

![Opcje klasyfikatorów przeszkolnych i etykiet wrażliwości.](../media/sensitivity-labels-classifers.png)

> [!CAUTION]
> Wyszkodziliśmy wstępnie  przeszkolonych klasyfikatorów w języku obraźliwym, ponieważ został w nim wyszkolonych duża liczba wyników fałszywie dodatnich. Nie używaj tego klasyfikatora, a jeśli obecnie go używasz, zalecamy przeniesienie procesów biznesowych, a zamiast tego użyj wcześniej przeszkolonych klasyfikatorów: Molestowanie **kierowane,** **Profanity** i Zagrożenia.

Aby uzyskać więcej informacji na temat tych klasyfikatorów, zobacz [Informacje na temat przeszkolnych klasyfikatorów](classifier-learn-about.md).

### <a name="recommend-that-the-user-applies-a-sensitivity-label"></a>Poleć użytkownikowi stosowanie etykiety wrażliwości

Jeśli wolisz, możesz polecić użytkownikom stosowanie etykiety. Po użyciu tej opcji użytkownicy mogą zaakceptować klasyfikację i skojarzoną ochronę lub odrzucić zalecenie, jeśli etykieta nie nadaje się do ich zawartości.

![Opcja polecania użytkownikom etykiety wrażliwości.](../media/Sensitivity-labels-Recommended-label-option.png)

Oto przykład monitu z klienta ujednoliconej etykiet usługi Azure Information Protection podczas konfigurowania warunku do stosowania etykiety jako zalecanej akcji z etykietą niestandardową poradą o zasadach. Możesz wybrać tekst, który ma być wyświetlany w poradzie dotyczącej zasad.

![Monituj o zastosowanie zalecanej etykiety.](../media/Sensitivity-label-prompt-for-required-label.png)

### <a name="when-automatic-or-recommended-labels-are-applied"></a>W przypadku stosowania etykiet automatycznych lub zalecanych

Implementacja automatycznego i zalecanego oznaczania etykiet w aplikacjach Office zależy od tego, czy używasz etykiet wbudowanych w usługę Office, czy klienta ujednoliconego Information Protection azure Information Protection etykiet. Jednak w obu przypadkach:

- W dokumentach i wiadomościach e-mail, które wcześniej były ręcznie lub automatycznie oznaczane z większą wrażliwością, nie można używać etykiet automatycznych. Pamiętaj, że do dokumentu lub wiadomości e-mail możesz zastosować tylko jedną etykietę wrażliwości (oprócz jednej etykiety przechowywania).

- Nie można używać zalecanych etykiet w dokumentach ani wiadomościach e-mail, które wcześniej były oznaczone wyższym poziomem wrażliwości. Jeśli zawartość jest już oznaczona wyższym poziomem wrażliwości, użytkownik nie zobaczy monitu z zaleceniem i poradą o zasadach.

Specyficzne dla wbudowanych etykiet:

- Nie wszystkie Office obsługują etykiety automatyczne (i zalecane). Aby uzyskać więcej informacji, zobacz [Pomoc techniczna dla funkcji etykiet wrażliwości w aplikacjach](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

- W przypadku etykiet zalecanych w klasycznych wersjach programu Word zawartość, która wyzwolyła zalecane etykiety, jest oflagowana, aby użytkownicy mogą przeglądać i usuwać po poufnej zawartości zamiast stosowania zalecanej etykiety wrażliwości.

- Aby uzyskać szczegółowe informacje na temat stosowania tych etykiet w aplikacjach pakietu Office, przykładowych zrzutów ekranu i wykrywania poufnych informacji, zobacz Automatyczne stosowanie etykiet wrażliwości do plików i wiadomości e-mail w aplikacji [Office.](https://support.microsoft.com/office/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)

Specyficzne dla klienta usługi Azure Information Protection etykiet ujednoliconej:

- Automatyczne i zalecane etykiety dotyczą programu Word, Excel i PowerPoint podczas zapisywania dokumentu oraz do Outlook podczas wysyłania wiadomości e-mail.

- Aby Outlook zalecane etykiety, musisz najpierw skonfigurować [zaawansowane ustawienie zasad](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook).

- Informacje poufne mogą być wykrywane w tekście treści dokumentów i wiadomości e-mail oraz w nagłówkach i stopce, ale nie mogą znaleźć się w wierszu tematu ani w załącznikach wiadomości e-mail.

## <a name="how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange"></a>Jak skonfigurować zasady automatycznego oznaczania SharePoint, OneDrive i Exchange

Przed skonfigurowaniem zasad automatycznego oznaczania upewnij się, że wymagania wstępne są spełnione.

### <a name="prerequisites-for-auto-labeling-policies"></a>Wymagania wstępne dotyczące zasad automatycznego oznaczania etykiet

- Tryb symulowania:
  - Inspekcja dla Microsoft 365 musi być włączona. Jeśli musisz włączyć inspekcję lub nie masz pewności, czy inspekcja jest już własna, zobacz Włączanie lub wyłączanie przeszukiwania dziennika [inspekcji](turn-audit-log-search-on-or-off.md).
  - Aby wyświetlić zawartość pliku lub wiadomości e-mail w widoku źródłowym, musisz  mieć rolę Podgląd zawartości klasyfikacji danych, która jest dostępna  w grupie ról Podgląd zawartości Eksploratora zawartości, lub grupy ról Podgląd zawartości programu **Information Protection** i **Information Protection** (obecnie dostępne w wersji zapoznawczej). Bez wymaganej roli okienko podglądu nie jest widać po zaznaczeniu elementu na karcie **Elementy dopasowane** . Administratorzy globalni domyślnie nie mają tej roli.

- Aby automatycznie oznaczać pliki w SharePoint i OneDrive:
  - Włączono [etykiety wrażliwości dla Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).
  - Po uruchamianiu zasad auto etykiet plik nie może być otwarty przez inny proces lub użytkownika. Plik wyewidencjonowany do edycji należy do tej kategorii.

- Jeśli zamierzasz używać [niestandardowych typów informacji poufnych](sensitive-information-type-learn-about.md) , a nie wbudowanych typów wrażliwości:
  - Niestandardowe typy informacji wrażliwości mają zastosowanie tylko do zawartości dodanej lub zmodyfikowanej SharePoint lub OneDrive po utworzeniu niestandardowych typów informacji o wrażliwości.
  - Aby przetestować nowe niestandardowe typy informacji poufnych, utwórz je przed utworzeniem zasad auto etykiet, a następnie utwórz nowe dokumenty z przykładami danych do testowania.

- Utworzono i opublikowano co najmniej jedną etykietę [wrażliwości (dla](create-sensitivity-labels.md) co najmniej jednego użytkownika), które można wybrać dla zasad automatycznego oznaczania etykiet. W przypadku tych etykiet:
  - Nie ma znaczenia, czy ustawienie etykiet automatycznych w aplikacjach pakietu Office jest włączone, czy wyłączone, ponieważ takie zasady automatycznego oznaczania etykiet są uzupełnieniem zasad automatycznego oznaczania etykiet, jak wyjaśniono we wprowadzeniu.
  - Jeśli etykiety, których chcesz użyć do automatycznego oznaczania etykiet, są skonfigurowane do używania oznaczeń wizualnych (nagłówków, stopek, znaków wodnych), pamiętaj, że nie są one stosowane do dokumentów.
  - Jeśli etykiety [mają szyfrowanie:](encryption-sensitivity-labels.md)
    - Jeśli zasady automatycznego oznaczania zawierają lokalizacje dla SharePoint lub OneDrive, etykieta musi być teraz skonfigurowana dla ustawienia **Przypisz** uprawnienia.
    - Gdy zasady automatycznego oznaczania są przeznaczone tylko dla usługi Exchange, etykietę można skonfigurować pod pomocą opcji Przypisz uprawnienia **teraz** lub Pozwól użytkownikom na przypisywanie **uprawnień (w** przypadku opcji Nie przesyłaj dalej Encrypt-Only).

### <a name="learn-about-simulation-mode"></a>Informacje na temat trybu symulacyjnego

Tryb symulowania jest unikatowy dla zasad automatycznego oznaczania etykiet i może być uwzględniany w przepływie pracy. Nie można automatycznie oznaczać dokumentów i wiadomości e-mail, dopóki zasady nie uruchomą co najmniej jednej symulacyjnej.

Tryb symulowania obsługuje maksymalnie 1000 000 dopasowanych plików. Jeśli zasady auto etykiet pasują do większej liczby plików niż ta liczba, nie można włączyć tych zasad w celu zastosowania etykiet. W takim przypadku należy ponownie skonfigurować zasady automatycznego oznaczania etykiet tak, aby dopasować mniej plików i uruchomić symulację ponownego konfigurowania. Ta maksymalna liczba 1000 000 dopasowanych plików dotyczy tylko trybu symulacyjnego, a nie zasad automatycznego oznaczania, które są już włączone w celu stosowania etykiet wrażliwości.

Przepływ pracy dla zasad auto etykiet:

1. Tworzenie i konfigurowanie zasad automatycznego oznaczania etykiet.

2. Zasady należy uruchamiać w trybie symulacyjnej, który może potrwać do 12 godzin. Ukończona symulacja wyzwala powiadomienie e-mail wysyłane do użytkownika skonfigurowanego do odbierania [alertów dotyczących aktywności](alert-policies.md).

3. Przejrzyj wyniki i w razie potrzeby uściślij zasady. Na przykład może być konieczne edytowanie reguł zasad w celu zmniejszenia wyników fałszywie dodatnich lub usunięcie niektórych witryn, tak aby liczba dopasowanych plików nie przekroczyła 1 000 000. Tryb powtarzania symulacyjnego i poczekaj na jego ponowne ukończenie.

4. W razie potrzeby powtórz krok 3.

5. Wdrożenie w środowisku produkcyjnym.

Symulowane wdrożenie działa podobnie jak parametr WhatIf dla programu PowerShell. Zostaną zgłoszone wyniki, tak jakby zasady auto etykiet zastosowano wybraną etykietę przy użyciu zdefiniowanych reguł. Następnie można w razie potrzeby uściślić reguły w celu zapewnienia dokładności i ponownie uruchomić symulację. Ponieważ jednak automatyczne oznaczanie etykiet w programie Exchange dotyczy wysyłanych i otrzymywanych wiadomości e-mail, a nie wiadomości przechowywanych w skrzynkach pocztowych, nie należy oczekiwać spójności wyników, ponieważ wiadomość e-mail jest spójna, chyba że można wysyłać i odbierać takie same wiadomości e-mail.

Tryb symulowania pozwala również stopniowo zwiększać zakres zasad auto etykiet przed wdrożeniem. Na przykład można zacząć od jednej lokalizacji, na przykład SharePoint dokumentów, z jedną biblioteką dokumentów. Następnie, w przypadku zmian iteracyjnych, zwiększ zakres do wielu witryn, a następnie do innej lokalizacji, na przykład OneDrive.

Ponadto można użyć trybu symulowania, aby przedstawić przybliżenie czasu potrzebnego do uruchomienia zasad auto etykiet, co pomoże zaplanować i zaplanować, kiedy zostanie uruchomione bez użycia trybu symulacyjnego.

### <a name="creating-an-auto-labeling-policy"></a>Tworzenie zasad automatycznego oznaczania etykiet

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365 przejdź</a> do etykiet wrażliwości:

    - **Rozwiązania** >  **Ochrona informacji**

    Jeśli nie widzisz tej opcji od razu, najpierw wybierz pozycję **Pokaż wszystko**.

2. Wybierz **kartę Automatyczne etykiety** :

    ![Karta Auto-etykieta.](../media/auto-labeling-tab.png)

    > [!NOTE]
    > Jeśli nie widzisz karty **Automatyczne** etykiety, ta funkcja nie jest obecnie dostępna w Twoim regionie ze względu na współzależność zaplecza platformy Azure. Aby uzyskać więcej informacji, zobacz [Dostępność platformy Azure w zależności od kraju](/troubleshoot/azure/general/dependency-availability-by-country).

3. Wybierz **pozycję + Utwórz zasady auto etykiet**. To uruchamia konfigurację nowych zasad:

    ![Konfiguracja nowych zasad do automatycznego oznaczania etykiet.](../media/auto-labeling-wizard.png)

4. Dla strony **Wybierz informacje, do których chcesz zastosować tę etykietę**: Wybierz jeden z szablonów, na przykład **Finanse** lub **Prywatność**. Możesz uściślić wyszukiwanie przy użyciu **listy rozwijanej Pokaż opcje** . Lub wybierz pozycję **Zasady niestandardowe** , jeśli szablony nie spełniają Twoich wymagań. Wybierz pozycję **Dalej**.

5. Dla strony **Nadaj nazwę zasadom auto** etykiet: Podaj unikatową nazwę i opcjonalnie opis ułatwiający identyfikację automatycznie zastosowanej etykiety, lokalizacji i warunków identyfikującej zawartość do o etykiecie.

6. Dla strony **Wybierz lokalizacje, w których chcesz** zastosować etykietę: Wybierz i określ lokalizacje dla etykiet Exchange, SharePoint i OneDrive. Jeśli nie chcesz zachować domyślnego ustawienia Wszystkie w wybranych lokalizacjach, wybierz link, aby wybrać konkretne wystąpienia do dołączyć, lub wybierz link, aby wybrać konkretne wystąpienia, które mają zostać wykluczone. Następnie wybierz pozycję **Dalej**.

    ![Wybierz stronę lokalizacje w celu konfiguracji automatycznego oznaczania etykiet.](../media/locations-auto-labeling-wizard.png)
    
    Jeśli zmienisz ustawienia domyślne za pomocą ustawień **Uwzględniany lub** **Wykluczony**:
    
    - W przypadku **Exchange** adres e-mail zasady są stosowane zgodnie z adresem nadawcy określonym adresatom. W większości przypadków warto zachować wartość domyślną Wszystkie z wartością **Brak wykluczonych**. Ta konfiguracja jest odpowiednia nawet w przypadku testów dla podzestawu użytkowników. Zamiast określać podzbiór użytkowników w tym miejscu, użyj zaawansowanych reguł w następnym kroku w celu skonfigurowania warunków dołączania lub wykluczania adresatów w organizacji. W przeciwnym razie po zmianie ustawień domyślnych w tym miejscu:
        -  Jeśli zmienisz domyślne ustawienie Wszystkie  uwzględnione i zamiast tego wybierz konkretnych użytkowników lub grupy, wiadomości e-mail wysyłane spoza organizacji zostaną wyłączone z zasad. 
        -  Jeśli nie określisz wartości  domyślnej Wszystkie, ale określisz wykluczanych użytkowników lub grupy, wiadomości e-mail, które te wykluczeni użytkownicy będą wykluczane z zasad, ale nie będą z nich wyłączane wiadomości e-mail.
    
    - Aby OneDrive konta, zobacz Uzyskiwanie listy wszystkich [](/onedrive/list-onedrive-urls) adresów URL OneDrive użytkowników w organizacji, aby ułatwić określanie poszczególnych kont OneDrive, które mają być dołączane lub wykluczane.

7. Na stronie **Konfigurowanie reguł typowych** lub zaawansowanych: Zachowaj domyślną regułę Common,  aby zdefiniować reguły identyfikujące zawartość do oznaczania etykietą we wszystkich wybranych lokalizacjach. Jeśli dla poszczególnych lokalizacji są potrzebne różne reguły, w tym więcej opcji dla Exchange, wybierz **pozycję Reguły zaawansowane**. Następnie wybierz pozycję **Dalej**.

    Reguły używają warunków, które obejmują typy informacji poufnych i opcje udostępniania:
    - W przypadku typów informacji poufnych możesz wybrać zarówno wbudowane, jak i niestandardowe typy informacji poufnych.
    - W przypadku opcji udostępnionych możesz wybrać opcję tylko z osobami **w** mojej organizacji lub **z osobami spoza mojej organizacji**.

    Jeśli lokalizacja **jest Exchange i** wybrano pozycję **Reguły** zaawansowane, możesz wybrać inne warunki:
    - Adres IP nadawcy to
    - Domena adresata to
    - Adresatem jest
    - Rozszerzenie pliku załącznika to
    - Załącznik jest chroniony hasłem
    - Nie można było zeskanować zawartości dowolnego załącznika wiadomości e-mail
    - Zawartość każdego załącznika wiadomości e-mail nie ukończono skanowania
    - Nagłówek odpowiada wzorcom
    - Temat odpowiada wzorcom
    - Adres adresata zawiera wyrazy
    - Adres adresata pasuje do wzorców
    - Adres nadawcy odpowiada wzorcom
    - Domena nadawcy to
    - Adresat jest członkiem
    - Nadawca:

    Dla każdego z tych warunków możesz określić wyjątki.

8. W zależności od poprzednich opcji możesz teraz tworzyć nowe reguły, korzystając z warunków i wyjątków.

    Opcje konfiguracji dla typów informacji poufnych są takie same jak opcje wybrane do automatycznego oznaczania etykiet dla Office aplikacji. Jeśli potrzebujesz dodatkowych informacji, zobacz [Konfigurowanie typów informacji poufnych dla etykiety](#configuring-sensitive-info-types-for-a-label).

    Po wybraniu wszystkich potrzebnych reguł i potwierdzeniu, że ich status jest wł. wybierz pozycję  Dalej, aby przejść do wybierania etykiety do automatycznego zastosowania.

9. Na stronie **Wybierz etykietę do automatycznego** zastosowania: Wybierz pozycję **+ Wybierz** etykietę, wybierz etykietę w okienku Wybierz **etykietę** wrażliwości, a następnie wybierz pozycję **Dalej**.

10. Jeśli zasady zawierają lokalizację Exchange: Określ opcjonalne konfiguracje na **stronie Dodatkowe ustawienia poczty e-mail**:
    
    - **Automatyczne zamienianie istniejących** etykiet o takim samym lub niskim priorytecie: Dotyczy zarówno przychodzących, jak i wychodzących wiadomości e-mail. Wybranie tego ustawienia zapewnia, że zawsze będzie stosowana pasująca etykieta wrażliwości. Jeśli nie wybierzesz tego ustawienia, pasującą etykietę wrażliwości nie zostanie zastosowana do wiadomości e-mail, które mają istniejącą etykietę [](sensitivity-labels.md#label-priority-order-matters) wrażliwości o wyższym priorytecie lub ręcznie oznaczone etykietą.
    
    - Zastosuj szyfrowanie do wiadomości e-mail otrzymanych spoza **organizacji: Po** wybraniu tej opcji musisz przypisać właściciela zarządzania [](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) prawami, aby zapewnić, że upoważniona osoba w Twojej organizacji będzie mieć uprawnienia [](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) do używania pełnej kontroli dla wiadomości e-mail wysyłanych z Twojej organizacji spoza organizacji oraz etykiet zasad za pomocą szyfrowania. Ta rola może być potrzebna do późniejszego usunięcia szyfrowania lub przypisania różnych praw użytkowania użytkownikom w organizacji.
        
        W **przypadku ustawienia Przypisz właściciela zarządzania prawami** określ pojedynczego użytkownika za pomocą adresu e-mail należącego do Twojej organizacji. Nie określaj kontaktu pocztowego, udostępnionej skrzynki pocztowej ani żadnego typu grupy, ponieważ nie są one obsługiwane dla tej roli.

10. Na **stronie** Zdecyduj, czy chcesz przetestować zasady teraz, czy później: Wybierz pozycję Uruchom  zasady w trybie symulacyjnej, jeśli chcesz teraz uruchomić zasady auto etykiet w trybie symulacyjnej. W przeciwnym razie **wybierz pozycję Odejdzie z zasad wyłączonych**. Wybierz **pozycję Dalej**:

    ![Przetestuj skonfigurowane zasady automatycznego oznaczania etykiet.](../media/simulation-mode-auto-labeling-wizard.png)

11. Strona **Podsumowanie:** Przejrzyj konfigurację zasad automatycznego oznaczania etykiet i w razie potrzeby wprowadzić wymagane zmiany, a następnie dokończ konfigurację.

 Teraz na stronie  **Information** **protectionAuto-labeling** >  (Ochrona informacjiAutomatyczne etykiety) są dostępne zasady auto etykiet w sekcji Symulacja lub Wyłączone w zależności od tego, czy ma ona być uruchamiana w trybie symulacyjnej, czy nie. Wybierz zasady, aby wyświetlić szczegóły konfiguracji i stanu (na przykład nadal działa **symulacyjna zasada**). W przypadku zasad w trybie symulowania  wybierz kartę Dopasowane elementy, aby sprawdzić, które wiadomości e-mail lub dokumenty są zgodne z określonymi regułami.

Zasady można modyfikować bezpośrednio w tym interfejsie:

- W przypadku zasad w **sekcji Wyłączone** wybierz przycisk **Edytuj zasady** .

- Dla zasad w sekcji **Symulacja** wybierz opcję Edytuj  zasady w górnej części strony, z jednej z kart:

    ![Opcja Edytuj zasady auto etykiet.](../media/auto-labeling-edit.png)

    Gdy wszystko będzie gotowe do uruchomienia zasad bez symulowania, wybierz opcję **Włącz zasady** .

Zasady automatycznego oznaczania są uruchamiane w sposób ciągły do momentu ich usunięcia. Na przykład nowe i zmodyfikowane pliki zostaną uwzględnione w bieżących ustawieniach zasad.

### <a name="monitoring-your-auto-labeling-policy"></a>Monitorowanie zasad auto etykiet

Po włączeniu zasad automatycznego oznaczania możesz wyświetlić postęp oznaczania etykiet dla plików w wybranych SharePoint i OneDrive lokalizacjach. Wiadomości e-mail nie są uwzględniane w postępie oznaczania etykiet, ponieważ są automatycznie oznaczane w trakcie ich wysłania.

Postęp oznaczania etykiet obejmuje pliki, które mają zostać oznaczone etykietą przez zasady, pliki oznaczone etykietą w ciągu ostatnich siedmiu dni oraz całkowitą liczbę plików oznaczonych etykietą. Ponieważ dziennie może oznaczać maksymalnie 25 000 plików, te informacje zapewniają wgląd w bieżący postęp oznaczania zasad i liczbę plików, które nadal mają zostać oznaczone etykietą.

Po pierwszym włączeniu zasad początkowo jest widać wartość 0, aby oznaczać pliki do momentu pobrania najnowszych danych. Te informacje o postępie są aktualizowane co 48 godzin, więc można się spodziewać, że co drugi dzień będą dostępne najnowsze dane. Po wybraniu zasad auto etykiet można wyświetlić więcej szczegółów dotyczących zasad w okienku wysuwu, które zawiera informacje o postępie etykiet dla 10 najlepszych witryn. Informacje w tym wysuwanych okienku mogą być bardziej aktualne niż zagregowane informacje o zasadach wyświetlane na stronie głównej Auto **etykiecie** .

Wyniki zasad auto etykiet można również wyświetlić przy użyciu [Eksploratora](data-classification-content-explorer.md) zawartości, gdy masz odpowiednie [uprawnienia](data-classification-content-explorer.md#permissions):

- **Grupa ról Podgląd listy Eksploratora** zawartości umożliwia wyświetlanie etykiety pliku, ale nie zawartości pliku.
- **Grupy ról podglądu zawartości** w Eksploratorze zawartości **oraz** grupy Information Protection i **Information Protection** Grupy ról (obecnie dostępne w wersji zapoznawczej) eksploratora zawartości umożliwiają wyświetlanie zawartości pliku.

> [!TIP]
> Za pomocą Eksploratora zawartości można również identyfikować lokalizacje, w których znajdują się dokumenty z informacjami poufnymi, ale nie mają etykiety. Korzystając z tych informacji, rozważ dodanie tych lokalizacji do zasad auto etykiet i dołącz jako reguły określone typy informacji poufnych.

### <a name="use-powershell-for-auto-labeling-policies"></a>Używanie programu PowerShell do automatycznego oznaczania zasad

Za pomocą programu [PowerShell &](/powershell/exchange/scc-powershell) zabezpieczeń i zgodności możesz tworzyć i konfigurować zasady automatycznego oznaczania. Oznacza to, że można w pełni skrybować tworzenie i konserwację zasad auto etykiet, co zapewnia również bardziej skuteczną metodę określania wielu adresów URL dla lokalizacji OneDrive i SharePoint etykiet.

Przed uruchomieniem poleceń w programie PowerShell należy najpierw połączyć się z programem [PowerShell w centrum zabezpieczeń & zgodności](/powershell/exchange/connect-to-scc-powershell).

Aby utworzyć nowe zasady automatycznego oznaczania etykiet:

```powershell
New-AutoSensitivityLabelPolicy -Name <AutoLabelingPolicyName> -SharePointLocation "<SharePointSiteLocation>" -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

To polecenie tworzy zasady automatycznego oznaczania etykiet dla SharePoint witrynie. Aby uzyskać OneDrive lokalizacji, użyj zamiast tego *parametru OneDriveLocation*.

Aby dodać więcej witryn do istniejących zasad automatycznego oznaczania etykiet:

```powershell
$spoLocations = @("<SharePointSiteLocation1>","<SharePointSiteLocation2>")
Set-AutoSensitivityLabelPolicy -Identity <AutoLabelingPolicyName> -AddSharePointLocation $spoLocations -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

To polecenie określa nowe adresy SHAREPOINT URL w zmiennej, która jest następnie dodawana do istniejących zasad auto etykiet. Aby zamiast OneDrive lokalizacji, użyj *parametru AddOneDriveLocation* z inną zmienną, taką *jak $OneDriveLocations*.

Aby utworzyć nową regułę zasad automatycznego oznaczania:

```powershell
New-AutoSensitivityLabelRule -Policy <AutoLabelingPolicyName> -Name <AutoLabelingRuleName> -ContentContainsSensitiveInformation @{"name"= "a44669fe-0d48-453d-a9b1-2cc83f2cba77"; "mincount" = "2"} -Workload SharePoint
```

W przypadku istniejących zasad automatycznego oznaczania to polecenie tworzy nową regułę zasad wykrywającą typ informacji poufnych numer **SSN,** który ma identyfikator jednostki a44669fe-0d48-453d-a9b1-2cc83f2cba77. Aby znaleźć identyfikatory encji dla innych typów informacji poufnych, zobacz Definicje encji [typu informacji poufnych](sensitive-information-type-entity-definitions.md).

Aby uzyskać więcej informacji na temat poleceń cmdlet programu PowerShell, które obsługują zasady auto etykietowania, ich dostępne parametry i kilka przykładów, zobacz następującą pomoc w zakresie poleceń cmdlet:

- [Get-AutoSensitivityLabelPolicy](/powershell/module/exchange/get-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelPolicy](/powershell/module/exchange/new-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelRule](/powershell/module/exchange/new-autosensitivitylabelrule)
- [Remove-AutoSensitivityLabelPolicy](/powershell/module/exchange/remove-autosensitivitylabelpolicy)
- [Remove-AutoSensitivityLabelRule](/powershell/module/exchange/remove-autosensitivitylabelrule)
- [Set-AutoSensitivityLabelPolicy](/powershell/module/exchange/set-autosensitivitylabelpolicy)
- [Set-AutoSensitivityLabelRule](/powershell/module/exchange/set-autosensitivitylabelrule)

## <a name="tips-to-increase-labeling-reach"></a>Wskazówki, aby zwiększyć zasięg etykiet

Mimo że automatyczne oznaczanie etykiet jest jednym z najbardziej efektywnych sposobów klasyfikowania, oznaczania i chroniania plików programu Office, których właścicielami jest Twoja organizacja, sprawdź, czy można je uzupełnić za pomocą dowolnej z następujących metod, aby zwiększyć zasięg etykiet:

- W SharePoint Syntex można zastosować etykietę wrażliwości do modelu zrozumienia [dokumentu, dzięki](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) czemu dokumenty zidentyfikowane w bibliotece dokumentów SharePoint są automatycznie oznaczane.

- W przypadku korzystania z [klienta usługi Azure Information Protection etykiet ujednoliconej](/azure/information-protection/rms-client/aip-clientv2):

  - W przypadku plików w lokalnych magazynach danych, takich jak udziały sieciowe i biblioteki programu SharePoint Server: Skaner umożliwia [](/azure/information-protection/deploy-aip-scanner) odnajdowanie poufnych informacji w tych plikach i odpowiednie oznaczanie ich etykietami. Jeśli planujesz migrację lub przekazanie tych plików do usługi SharePoint w programie Microsoft 365, użyj skanera do oznaczania plików etykietami przed przeniesieniem ich do chmury.

  - Jeśli używasz innego rozwiązania do etykiet przed użyciem etykiet wrażliwości: Użyj programu PowerShell i [zaawansowanego](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#migrate-labels-from-secure-islands-and-other-labeling-solutions) ustawienia, aby ponownie użyć etykiet z tych rozwiązań.

- [Zachęcaj użytkowników do ręcznego](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) oznaczania etykiet po zasypceniu ich, jakie etykiety wrażliwości należy zastosować. Jeśli masz pewność, że użytkownicy zrozumieją, którą etykietę zastosować, rozważ skonfigurowanie etykiety domyślnej i obowiązkowych etykiet jako [ustawień zasad](sensitivity-labels.md#what-label-policies-can-do).

Ponadto rozważ domyślne oznaczanie nowych plików jako poufnych w programie SharePoint, aby uniemożliwić gościom dostęp do nowo dodanych plików, dopóki co najmniej jedna zasada DLP nie przeskanuje zawartości pliku.[](/sharepoint/sensitive-by-default)
