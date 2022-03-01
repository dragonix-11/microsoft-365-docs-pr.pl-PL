---
title: Ochrona informacji podlegających rozporządzeniem o ochronie prywatności danych
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Wdrażaj Microsoft 365 zabezpieczeń i zgodności oraz chroń swoje informacje osobiste.
ms.openlocfilehash: 2739da0b5e9c4896b65751c63d9b2e5f3b026a2e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "63012468"
---
# <a name="protect-information-subject-to-data-privacy-regulation"></a>Ochrona informacji podlegających rozporządzeniem o ochronie prywatności danych

W ramach subskrypcji można stosować szereg kontroli ochrony informacji, aby pomóc w spełnianiu wymagań i przepisów dotyczących zgodności z przepisami dotyczącymi prywatności danych. Należą do nich: Ogólne Rozporządzenie o Ochronie Danych (RODO), HIPAA-HITECH (amerykańskiej ustawy o ochronie prywatności w zakresie opieki zdrowotnej), california Consumer Protection Act (HIPA) i brazylijskiej ustawy o ochronie danych (LGPD).

Te kontrolki znajdują się w następujących obszarach rozwiązania:

- Etykiety wrażliwości
- Ochrona przed utratą danych (DLP)
- Office szyfrowania wiadomości (OME)
- Teams dostępu do witryn i witryn

![Kluczowe usługi w celu ochrony informacji osobistych, których dane podlegają rozporządzeniem o ochronie prywatności danych.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-grid.png)

> [!NOTE]
> W tym rozwiązaniu opisano funkcje zabezpieczeń i zgodności w celu ochrony informacji podlegających regulacjom dotyczącym prywatności danych. Aby uzyskać pełną listę funkcji zabezpieczeń dostępnych w Microsoft 365, zobacz Microsoft 365 [zabezpieczeń](../security/index.yml). Aby uzyskać pełną listę funkcji zgodności w p Microsoft 365, [zobacz Microsoft 365 zgodności](../compliance/index.yml).

## <a name="data-privacy-regulations-that-impact-information-protection-controls"></a>Przepisy dotyczące ochrony prywatności danych, które mają wpływ na mechanizmy kontroli ochrony informacji

Oto przykładowa lista przepisów dotyczących ochrony prywatności danych, które mogą dotyczyć kontroli ochrony informacji:

- Artykuł 5(1)(f)) RODO
- Artykuł RODO (32)(1)(a)
- LGPD, artykuł 46
- HIPAA-HITECH (45 CFR 164.312(e)(1))
- HIPAA-HITECH (45 C.F.R. 164.312(e)(2)(ii))

Aby uzyskać [więcej informacji na](information-protection-deploy-assess.md) temat każdego z powyższych, zobacz ocenianie ryzyka związanego z prywatnością danych i identyfikowanie elementów poufnych.

Przepisy dotyczące ochrony prywatności danych w zakresie ochrony informacji zalecają:

- Ochrona przed utratą lub nieautoryzowanym dostępem, użyciem i/lub transmisją.
- Stosowanie mechanizmów zabezpieczających w oparciu o ryzyko.
- Korzystanie z szyfrowania, jeśli to konieczne.

Twoja organizacja może również chcieć chronić Microsoft 365 do innych celów, takich jak potrzeby w zakresie zgodności z przepisami lub ze względów biznesowych. Ustanawianie schematu ochrony informacji w celu ochrony prywatności danych należy stosować w ramach ogólnego planowania, wdrażania i zarządzania informacjami.

Aby ułatwić ci wprowadzenie do schematu ochrony informacji w programie Microsoft 365, w poniższej sekcji przedstawiono krótką listę powiązanych funkcji i działań udoskonalania w zakresie Microsoft 365. Ta lista zawiera funkcje i działania usprawnień, które mają zastosowanie do przepisów dotyczących prywatności danych. Lista nie zawiera jednak starszych technologii, jeśli istnieje nowsza funkcja, która w dużym stopniu zasypuje starszą. Na przykład zarządzanie prawami do informacji (IRM, Information Rights Management) dla systemów SharePoint i OneDrive nie jest uwzględniane na liście, ale są uwzględniane etykiety wrażliwości.

## <a name="managing-information-protection-in-microsoft-365"></a>Zarządzanie ochroną informacji w programie Microsoft 365

Rozwiązania [firmy Microsoft do ochrony](../compliance/information-protection.md) informacji obejmują szereg zintegrowanych funkcji dla systemów Microsoft 365, Microsoft Azure i Microsoft Windows. W Microsoft 365 rozwiązania do ochrony informacji obejmują:

- [Typy informacji poufnych](../compliance/sensitive-information-type-entity-definitions.md) (opisane w [artykule Ocenianie ryzyka związanego z prywatnością danych i identyfikowanie elementów poufnych)](information-protection-deploy-assess.md)
- [Etykiety wrażliwości](../compliance/sensitivity-labels.md)
  - Service/container-level
  - Po stronie klienta/na poziomie zawartości
  - Zautomatyzowane w celu przechowywania danych w SharePoint i OneDrive
- Ochrona przed utratą danych (DLP)
- [Microsoft 365 punktu końcowego ochrony przed utratą danych](../compliance/endpoint-dlp-learn-about.md)
- [Szyfrowanie wiadomości usługi Office 365 nowych funkcji (OME)](../compliance/ome.md) i zaawansowanego szyfrowania [wiadomości](../compliance/ome-advanced-message-encryption.md) OME

Ponadto ochrona na poziomie witryny i biblioteki to ważne mechanizmy dołączane do każdego schematu ochrony.

Aby uzyskać informacje na temat innych funkcji ochrony informacji poza Microsoft 365, zobacz:

- [Usługa Microsoft Defender dla aplikacji w chmurze](/cloud-app-security/)
- [Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
- [Windows informacji](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)

## <a name="sensitivity-labels"></a>Etykiety wrażliwości

Etykiety wrażliwości Microsoft Information Protection umożliwiają klasyfikowanie i chronienie danych organizacji bez utrudniania pracy użytkowników i możliwości współpracy.

> [!div class="mx-imgBorder"]
> ![Etykiety wrażliwości w Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-labels.png)

### <a name="prerequisites-for-sensitivity-labels"></a>Wymagania wstępne dotyczące etykiet wrażliwości

Wykonaj te czynności przed zaimplementowaniem dowolnego z poniższych funkcji opartych na etykietach wrażliwości:

1. Opis:
   - **Wymagania biznesowe.** Ustal powody biznesowe do stosowania etykiet wrażliwości w przedsiębiorstwie. Mogą to być na przykład wymagania dotyczące ochrony prywatności danych użytkownika dotyczące ochrony informacji.
   - **Możliwości etykiet wrażliwości.** Etykiety wrażliwości mogą być złożone, dlatego przed rozpoczęciem koniecznie przeczytaj dokumentację [etykiet](../compliance/sensitivity-labels.md) wrażliwości.
   - **Najważniejsze rzeczy do zapamiętania** Etykietami wrażliwości zarządza się w centrum administracyjnym zgodności firmy Microsoft, ale opcje określania docelowych wartości docelowych i aplikacji znacznie się różnią.
      - Na poziomie kontenera znajdują się etykiety wrażliwości Teams, grup i witryn (ustawienia nie dotyczą zawartości wewnątrz kontenera). Są one publikowane dla użytkowników i grup, które zastosują je po inicjowaniu obsługi administracyjnej witryny, grupy lub zespołu.
      - Istnieją etykiety wrażliwości dla zawartości aktywnej. Są one również publikowane dla użytkowników lub grup, które mają zastosowanie ręcznie lub są stosowane automatycznie w następującej sytuacji:
        - Plik zostanie otwarty/edytowany/zapisany na pulpicie użytkownika lub w SharePoint sieci Web.
        - Wiadomość e-mail jest edytowana i wysyłana.
      - Istnieją etykiety wrażliwości automatycznych aplikacji dla plików w stanie spoczynku SharePoint i OneDrive, oprócz wiadomości e-mail wysyłanych przez Exchange. Są one kierowane do wszystkich witryn lub określonych witryn i automatycznie dotyczą plików w spoczynku w tych środowiskach.

2. Wymiernie etykiety wrażliwości bieżącej za pomocą wcześniejszych lub alternatywnych metod

   - Azure Information Protection

      Może być konieczne uzgadnianie obecnego schematu etykiet wrażliwości z dowolną istniejącą implementacją usługi [Azure Information Protection](../compliance/sensitivity-labels.md#sensitivity-labels-and-azure-information-protection) z etykietami.
   - OME

      Jeśli planujesz korzystanie z nowoczesnych etykiet wrażliwości w celu ochrony poczty e-mail i istniejących metod szyfrowania poczty e-mail, takich jak OME, mogą one istnieć we współpracy, ale musisz zrozumieć scenariusze, w których należy zastosować tę usługę. Zobacz [Szyfrowanie wiadomości usługi Office 365 o nowych możliwościach (OME),](#office-365-message-encryption-ome-new-capabilities) która zawiera tabelę porównującą nowoczesną ochronę typu etykiety za pomocą ochrony opartej na OME.

3. Zaplanuj integrację z szerszym schematem ochrony informacji. Oprócz współistnienia z usługą OME etykiety wrażliwości mogą być używane wraz z możliwościami, Microsoft 365 ochrony przed utratą danych (DLP) i programu Microsoft Defender dla aplikacji w chmurze. Zobacz [Microsoft Information Protection w Microsoft 365](../compliance/information-protection.md), aby zrealizować cele związane z ochroną informacji związane z ochroną danych.

4. Opracuj klasyfikację wrażliwości i schemat kontroli etykiet wrażliwości. Zobacz [Klasyfikacja danych i taksonomia etykiet wrażliwości](https://aka.ms/dataclassificationwhitepaper).

### <a name="general-guidance"></a>Ogólne wskazówki

1. **Definicja schematu.** Zanim zastosuj etykiety i ochronę za pomocą funkcji technicznych w całej organizacji zdefiniuj schemat klasyfikacji. Być może masz już schemat klasyfikacji, co ułatwia dodawanie danych osobistych.
2. **Wprowadzenie.** Zacznij od podjęcia decyzji o liczbie i nazwach etykiet do wdrożenia. Możesz wykonać tę czynność, nie martwiąc się o to, której technologii użyć i jak zostaną zastosowane etykiety. Ten schemat można stosować uniwersalne w całej organizacji, łącznie z danymi, które znajdują się lokalnie i w innych usługach w chmurze.
3. **Dodatkowe zalecenia** Projektując i implementując zasady, etykiety i warunki, rozważ następujące zalecenia:

   - **Użyj istniejącego schematu klasyfikacji (jeśli jest).** Wiele organizacji już używa klasyfikacji danych w pewnych postaciach. Starannie oceń istniejący schemat etykiet i, jeśli to możliwe, użyj go bez zmian. Używanie znanych etykiet, które są rozpoznawalne dla użytkowników końcowych, będzie dysków przyjęcia.
   - **Zacznij mały.** Liczba etykiet, które można utworzyć, jest praktycznie nieograniczona. Jednak duża liczba etykiet i pod etykiet może spowolnić ich przyjęcia.
   - **Używanie scenariuszy i przypadków użycia.** Zidentyfikuj typowe przypadki użycia w organizacji i korzystaj ze scenariuszy wynikających z przepisów dotyczących prywatności danych, których podlegasz. Sprawdź, czy konfiguracja etykiety i klasyfikacji, która jest przewiduje, będzie działać w praktyce.
   - **Pytaj wszystkie prośby o nową etykietę.** Czy każdy scenariusz lub przypadek użycia rzeczywiście wymaga nowej etykiety, czy można użyć już posiadanych etykiet? Zapewnienie minimalnej liczby etykiet zwiększa ich wdrożenie.
   - **Stosowanie etykiet podrzędnych dla kluczowych działów.** Niektóre działy będą mieć określone potrzeby, które wymagają określonych etykiet. Zdefiniuj te etykiety jako etykiety podrzędne do istniejącej etykiety i rozważ użycie zasad o zakresach, które są przypisywane do grup użytkowników zamiast globalnie.
   - **Rozważenie zasad o zakresach.** Zasady kierowane do podzbiorów użytkowników zapobiegają przeciążeniu etykietami. Zasady zakresowe umożliwiają przypisywanie etykiet lub podkategorie roli lub działu tylko do pracowników, którzy pracują w danym dziale.
   - **Używaj zrozumiałych nazw etykiet.** Nie używaj żargonu, standardów ani akronimów jako nazw etykiet. Spróbuj użyć nazw, które są ponownie odwłaszniane dla użytkownika końcowego, aby poprawić wdrożenie. Zamiast etykiet, takich jak PII, PCI, HIPAA, LBI, MBI i LBI, rozważ nazwy niekomercyjne, publiczne, ogólne, poufne i wysoce poufne.

### <a name="create-and-deploy-sensitivity-labels-for-sites-groups-and-teams"></a>Tworzenie i wdrażanie etykiet wrażliwości dla witryn, grup i zespołów

Etykiety wrażliwości [w skoroszycie](../compliance/sensitivity-labels-teams-groups-sites.md) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">można Centrum zgodności platformy Microsoft 365</a> zastosować do tych kontenerów:

- Microsoft Teams witryn
- Microsoft 365 grupy (wcześniej Office 365 grupy)
- SharePoint witryn

Aby chronić zawartość w tych kontenerach, użyj następujących ustawień etykiet:

- Prywatność (publiczna lub prywatna) Microsoft 365 powiązanych z Teams sieci web
- Dostęp użytkowników zewnętrznych
- Dostęp z urządzeń niezamanektowych

W celu ochrony prywatności danych, aby zapobiec udostępnianiu zewnętrznemu kontenerów, które będą używane do przechowywania zawartości z poufnymi danymi osobistymi, oznaczania plików zawierających dane jako prywatne i wymagania urządzeń zarządzanych.

### <a name="create-and-deploy-sensitivity-labels-for-content"></a>Tworzenie i wdrażanie etykiet wrażliwości dla zawartości

Etykiety wrażliwości zastosowane do plików umożliwiają szyfrowanie ich zawartości, znakowanie zawartości znakiem wodnym oraz definiowanie innych kontrolek dla zawartości aplikacji Office, w tym Outlook i Office w sieci Web.

Gdy wszystko będzie gotowe do rozpoczęcia ochrony danych organizacji za pomocą etykiet wrażliwości:

1. **Utwórz etykiety.** Utwórz etykiety wrażliwości i nadaj ich nazwy zgodnie z taksonomią klasyfikacji organizacji dla różnych poziomów wrażliwości zawartości. Aby uzyskać więcej informacji na temat opracowywania taksonomii klasyfikacji, zobacz oficjalny dokument Klasyfikacja i [taksonomia etykiet wrażliwości](https://aka.ms/dataclassificationwhitepaper).
2. **Zdefiniuj zakres, jaki może mieć każda etykieta.** Skonfiguruj ustawienia ochrony, które chcesz skojarzyć z każdą etykietą. Na przykład możesz chcieć, aby zawartość wrażliwości (na przykład etykieta "Ogólne" zawierała tylko nagłówek lub stopkę), a wyższa zawartość wrażliwości (na przykład etykieta "Poufne") powinna zawierać znak wodny z włączonym szyfrowaniem.
3. **Publikowanie etykiet.** Po skonfigurowaniu etykiet wrażliwości opublikuj je przy użyciu zasad etykiet. Zdecyduj, którzy użytkownicy i grupy powinni mieć etykiety i jakich ustawień zasad należy użyć. Pojedyncza etykieta może być wielokrotnego użytku. Zdefiniowano ją raz, a następnie można dołączyć do kilku etykiet zasad przypisanych do różnych użytkowników.

Po opublikowaniu etykiet wrażliwości z poziomu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a>Centrum zgodności platformy Microsoft 365 są one wyświetlane w aplikacjach pakietu [Office](../compliance/sensitivity-labels-office-apps.md), aby użytkownicy klasyfikowali i chronili zawartość podczas jej tworzenia lub edytowania.

![Przepływ wdrażania etykiet wrażliwości w Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-label-flow.png)

W celu ochrony prywatności danych do wiadomości e-mail lub zawartości zawierającej poufne informacje osobiste ręcznie stosuje się etykietę poufności z szyfrowaniem i innymi regułami.

> [!NOTE]
> Etykiety wrażliwości z włączonym szyfrowaniem stosowane do wiadomości e-mail mogą nakładać się na siebie w OME. Zobacz [Zabezpieczanie scenariuszy wiadomości e-mail z OME i etykietami wrażliwości](#secure-email-scenarios-comparison-with-ome-and-sensitivity-labels).

### <a name="client-side-auto-labeling-when-users-edit-documents-or-compose-emails"></a>Automatyczne oznaczanie po stronie klienta podczas edytowania dokumentów lub redagowania wiadomości e-mail

Po utworzeniu etykiety wrażliwości możesz automatycznie przypisać [](../compliance/apply-sensitivity-label-automatically.md) ją do zawartości, w tym do wiadomości e-mail, jeśli jest ona taka, jaka jest taka, jaka jest podana przez Ciebie.

Możliwość automatycznego stosowania etykiet wrażliwości do zawartości jest ważna, ponieważ:

- Nie musisz szkolenie użytkowników, kiedy należy używać każdej z klasyfikacji.
- Nie musisz polegać na użytkownikach, aby prawidłowo klasyfikować całą zawartość.
- Użytkownicy nie muszą już znać twoich zasad — zamiast tego mogą skoncentrować się na swojej pracy.

Automatyczne etykiety obsługują polecanie etykiet użytkownikom, a także automatyczne stosowanie etykiet. Jednak w obu przypadkach użytkownik decyduje, czy zaakceptować, czy odrzucić tę etykietę w celu zapewnienia prawidłowego oznaczania zawartości.

To etykiety po stronie klienta mają minimalne opóźnienia w przypadku dokumentów, ponieważ tę etykietę można zastosować nawet przed zapisaniem dokumentu. Jednak nie wszystkie aplikacje klienckie obsługują automatyczne oznaczanie etykiet. Ta funkcja jest obsługiwana przez klienta ujednoliconego etykiet usługi Azure Information Protection, a niektóre [wersje Office etykiet](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Aby uzyskać instrukcje dotyczące konfiguracji, zobacz Jak [skonfigurować automatyczne oznaczanie etykiet dla Office aplikacji](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

W celu zachowania poufności danych etykiety wrażliwości są stosowane automatycznie do zawartości zawierającej poufne informacje osobiste.

### <a name="service-side-auto-labeling-when-content-is-already-saved"></a>Automatyczne oznaczanie po stronie usługi, gdy zawartość jest już zapisana

Ta metoda jest nazywana automatyczną klasyfikacją z etykietami wrażliwości. Możesz również usłyszeć informacje o nim nazywane automatycznym oznaczaniem danych w spoczynku (w przypadku dokumentów w usługach SharePoint i OneDrive) i przesyłanych danych (w przypadku wiadomości e-mail wysyłanych lub otrzymywanych przez Exchange). Na Exchange nie obejmuje ono wiadomości e-mail w skrzynkach pocztowych w spoczynku.

Ponieważ to etykiety są stosowane przez samą usługę, a nie przez aplikację użytkownika, nie musisz martwić się o to, jakie aplikacje mają użytkownicy i jaką wersję. W efekcie ta funkcja jest natychmiast dostępna w całej organizacji i nadaje się do stosowania etykiet w skali. Zasady automatycznego oznaczania etykiet nie obsługują zalecanych etykiet, ponieważ użytkownik nie wchodzi w interakcję z procesem oznaczania. Zamiast tego administrator uruchamia zasady w trybie symulowania, aby zapewnić prawidłowe etykiety zawartości przed ich zastosowaniem.

Aby uzyskać instrukcje dotyczące konfiguracji, zobacz Jak [skonfigurować zasady automatycznego SharePoint, OneDrive i Exchange](../compliance/apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

Aby chronić prywatność danych w witrynach, których dotyczy problem, należy wypychać etykiety wrażliwości w celu automatycznego szyfrowania zawartości zawierającej poufne informacje osobiste.

## <a name="data-loss-prevention"></a>Ochrona przed utratą danych

Za pomocą funkcji ochrony przed utratą danych [(DLP, data loss prevention)](../compliance/dlp-learn-about-dlp.md) w programie Microsoft 365 możesz wykrywać, ostrzegać i blokować ryzykowne, przypadkowe lub nieodpowiednie udostępnianie, takie jak udostępnianie danych zawierających informacje osobiste zarówno wewnętrznie, jak i zewnętrznie.

Funkcja DLP umożliwia:

- Identyfikowanie i monitorowanie ryzykownych działań udostępniania.
- Informacje dla użytkowników dotyczące odpowiednich wskazówek kontekstowych w celu podejmowania właściwych decyzji.
- Wymuszaj stosowanie zasad używania danych w przypadku zawartości bez zwiększenia produktywności.
- Integruj z klasyfikacją i etykietami, aby wykrywać i chronić dane podczas ich udostępniania.

### <a name="supported-workloads-for-dlp"></a>Obsługiwane obciążenia pracą DLP

Dzięki zasadom DLP w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a>Centrum zgodności platformy Microsoft 365 możesz identyfikować, monitorować i automatycznie chronić poufne elementy w wielu lokalizacjach w Microsoft 365, takich jak Exchange Online, SharePoint OneDrive i Microsoft Teams.

Można na przykład zidentyfikować dowolny dokument zawierający numer karty kredytowej przechowywany w dowolnej witrynie usługi OneDrive lub monitorować tylko OneDrive witryn określonych osób.

Możesz również monitorować i chronić poufne elementy w lokalnie zainstalowanych wersjach produktów Excel, PowerPoint i Word, które obejmują możliwość identyfikowania elementów poufnych i stosowania zasad DLP. Zasady DLP zapewniają ciągłe monitorowanie w sytuacji, gdy osoby udostępniają zawartość z tych Office aplikacji.

> [!div class="mx-imgBorder"]
> ![Obsługiwane obciążenia pracą DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-supported-workloads.png)

Na tej ilustracji przedstawiono przykład ochrony danych osobowych przez ochrona danych osobowych przez ochronę danych.

> [!div class="mx-imgBorder"]
> ![Przykład ochrony danych osobowych za pomocą funkcji DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-use.png)

Ochrona przed zagrożeniami (DLP) służy do identyfikowania dokumentu lub wiadomości e-mail zawierającego rekord kondycji, a następnie automatycznie blokuje dostęp do tego dokumentu lub blokuje wysyłanie wiadomości e-mail. Dzięki zasadom DLP adresat otrzymuje powiadomienie z poradą o zasadach i wysyła alert do użytkownika końcowego i administratora.

### <a name="planning-for-dlp"></a>Planowanie w przypadku zasad DLP

Zaplanuj zasady ochrony przed zasadami ochrony przed prywatnością pod:

- Wymagania biznesowe.

- Ocena organizacji oparta na czynniku ryzyka zgodnie z opisem w artykule Ocena ryzyka związanego z prywatnością danych i [identyfikowanie elementów poufnych](information-protection-deploy-assess.md).

- Inne mechanizmy ochrony informacji i zarządzania w miejscu lub w planowaniu ochrony prywatności danych.

- Typy informacji poufnych określone dla danych osobowych na podstawie prac oceniania zgodnie z opisem w artykule Ocenianie ryzyka związanego z prywatnością [danych i identyfikowanie elementów poufnych](information-protection-deploy-assess.md). Warunki zasad DLP mogą być oparte zarówno na typach informacji poufnych, jak i na etykietach przechowywania.

- Etykiety przechowywania musisz określić warunki dotyczące zasad DLP. Aby uzyskać [więcej informacji, zobacz](information-protection-deploy-govern.md) artykuł organizacji, którym podlega rozporządzenie o ochronie prywatności danych.

- Bieżące zarządzanie zasadami DLP, które wymaga, aby inna osoba w organizacji operuje i dostrajała zasady dotyczące zmian typów informacji poufnych, etykiet przechowywania, przepisów i zasad zgodności.

Etykiet wrażliwości nie można używać w warunkach zasad DLP, jednak niektórych scenariuszy ochrony w celu uniemożliwienia dostępu można używać tylko w przypadku etykiet wrażliwości, które można stosować automatycznie na podstawie typów informacji poufnych. Jeśli stosowane jest wydajne etykiety wrażliwości, rozważ, czy ochrony przed zabezpieczeniami DLP należy używać do rozszerzenia ochrony, ponieważ:

  - Zapobieganie utracie danych może uniemożliwiać udostępnianie plików. Etykiety wrażliwości mogą po prostu uniemożliwiać dostęp.

  - Zasady DLP mają bardziej szczegółowe poziomy kontroli pod względem reguł, warunków i akcji.

  - Zasady DLP można stosować do wiadomości Teams wiadomości na czacie i w kanałach. Etykiety wrażliwości można stosować tylko do dokumentów i wiadomości e-mail.


### <a name="dlp-policies"></a>Zasady DLP

Zasady DLP są konfigurowane w Centrum administracyjnym zgodności firmy Microsoft i określają poziom ochrony, typ informacji poufnych, których szukają zasady, oraz docelowe obciążenia pracą. Ich podstawowe składniki składają się na identyfikowanie ochrony i typów danych.

> [!div class="mx-imgBorder"]
> ![Konfiguracja zasad DLP w aplikacji Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-config.png)

Oto przykładowa zasada ochrony przed zasadami DLP mająca na celu świadomość RODO.

![Przykład zasad DLP na temat ochrony przed RODO.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-policy.png)

Zobacz [ten artykuł,](../compliance/create-test-tune-dlp-policy.md) aby uzyskać więcej informacji na temat tworzenia i stosowania zasad DLP.

### <a name="protection-levels-for-data-privacy"></a>Poziomy ochrony prywatności danych

W poniższej tabeli wymieniono trzy konfiguracje zwiększające ochronę za pomocą funkcji DLP.

![Poziomy ochrony prywatności dzięki zasadom DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-protection-levels.png)

Pierwszą konfigurację, "Świadomość", można wykorzystać jako punkt wyjścia i minimalny poziom ochrony w celu spełniania wymagań w zakresie zgodności z przepisami dotyczącymi prywatności danych.

> [!NOTE]
> Wraz ze zwiększającym się poziomem ochrony możliwość udostępniania informacji i uzyskiwania do nich dostępu przez użytkowników w niektórych przypadkach zmniejszy się, co mogłoby potencjalnie wpłynąć na ich produktywność lub możliwość wykonywania codziennych zadań.

Aby ułatwić pracownikom wydajną pracę w bezpieczniejszym środowisku, gdy poziom ochrony jest coraz większy, należy czasem ćwicować tych pracowników w zakresie nowych zasad i procedur zabezpieczeń oraz kształcić ich.

### <a name="example-of-using-sensitivity-labels-with-dlp"></a>Przykład korzystania z etykiet wrażliwości w funkcji DLP

Etykiety wrażliwości mogą współpracować z usługą DLP, aby zapewnić prywatność danych w środowisku ściśle uregulowanym. Oto najważniejsze kroki wdrożenia zintegrowanego:

1. Udokumentowano tu wymagania prawne i inne wymagania biznesowe dotyczące ochrony prywatności danych.
2. Docelowe źródła danych, typy i własność są względnie względnie związane z problemami dotyczącymi prywatności danych.
3. Ogólną strategię w zakresie spełniania wymagań oraz ochrony i zarządzania hotspotami prywatności danych.
4. Jest on etapowy plan działań w zakresie realizacji strategii kontroli prywatności danych.

Po  ustaliniu tych elementów możesz używać do tego celu typów informacji poufnych, taksonomii wrażliwych i zasad DLP. Na poniższym rysunku pokazano przykład.

> [!div class="mx-imgBorder"]
> ![Przykład etykiet wrażliwości w przypadku działania zasad DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

[Zobacz większą wersję tego obrazu](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

Poniżej przedstawiono kilka scenariuszy ochrony danych korzystających z funkcji DLP i etykiet wrażliwości, jak pokazano na ilustracji.

| Scenariusz | Proces |
|:-------|:-----|
| A | <ol><li>Etykiety wrażliwości zawartości są publikowane przez administratora użytkownikom i grupom w celu ręcznego lub automatycznego zastosowania do zawartości i wiadomości e-mail. </li><li>Użytkownik A stosuje etykiety ręcznie lub automatycznie podczas interakcji z zawartością, korzystając z szyfrowania lub innych zastosowanych ustawień. </li><li>Użytkownik A wysyła chronioną wiadomość e-mail lub plik do użytkownika B, gościa. </li></ol> |
| B | Zasady DLP opublikowane przez administratora w celu użytkownika A blokuje użytkownikowi A wysyłanie wiadomości e-mail i/lub pliku do użytkownika B. |
| C |  Etykieta wrażliwości z ustawieniem "właściciel nie może zapraszać gości" jest publikowana dla użytkownika A, który iniekuje witrynę Teams lub witrynę sieci SharePoint sieci Web. Inny użytkownik witryny próbuje selektywnie udostępnić plik użytkownikowi B, ale działanie funkcji DLP blokuje ten plik. |
| D | Etykieta wrażliwości autoplikowania zawartości witryny jest publikowana w co najmniej jednej witrynie, zapewniając kolejną warstwę ochrony, co spowoduje, że witryna chroniona. |
|||

## <a name="office-365-message-encryption-ome-new-capabilities"></a>Szyfrowanie wiadomości usługi Office 365 (OME) nowe funkcje

Wiadomości e-mail często są używane do wymiany poufnych elementów, takich jak dane dotyczące zdrowia pacjentów lub dane klientów i pracowników. Szyfrowanie wiadomości e-mail pozwala zagwarantować, że tylko zamierzony adresaci mogą wyświetlać zawartość wiadomości.

Za [pomocą OME](../compliance/ome.md) możesz wysyłać i odbierać zaszyfrowane wiadomości między osobami w organizacji i poza nią. OME współpracuje z usługami Outlook.com, Yahoo!, Gmail i innymi usługami poczty e-mail. Dzięki OME tylko zamierzony adresaci mogą wyświetlać zawartość wiadomości.

W celu ochrony prywatności danych należy używać OME do ochrony wiadomości wewnętrznych zawierających poufne elementy. Szyfrowanie wiadomości usługi Office 365 to usługa online wbudowana w usługę Microsoft Azure rights Management (Azure RMS), która jest częścią usługi Azure Information Protection. Obejmuje to zasady szyfrowania, tożsamości i autoryzacji, które ułatwiają zabezpieczanie poczty e-mail. Wiadomości można szyfrować przy użyciu szablonów zarządzania prawami dostępu, opcji Nie przesyłaj dalej i opcji tylko do szyfrowania.

Możesz również zdefiniować reguły przepływu poczty, aby zastosować tę ochronę. Można na przykład utworzyć regułę wymaganą szyfrowania wszystkich wiadomości zaadresowanych do określonego adresata lub zawierającej określone słowa kluczowe w wierszu tematu, a także określić, że adresaci nie mogą kopiować ani drukować zawartości wiadomości.

Ponadto zaawansowane szyfrowanie wiadomości [OME ułatwia](../compliance/ome-advanced-message-encryption.md) spełnienie wymagań dotyczących zgodności, które wymagają bardziej elastycznej kontroli nad adresatami zewnętrznymi i ich dostępu do zaszyfrowanych wiadomości e-mail. Dzięki zaawansowanemu szyfrowaniu wiadomości OME w aplikacji Microsoft 365 możesz kontrolować poufne wiadomości e-mail udostępniane poza organizacją przy użyciu automatycznych zasad wykrywania typów informacji poufnych.

W celu ochrony prywatności danych, jeśli chcesz udostępnić wiadomość e-mail stronie zewnętrznej, możesz określić datę wygaśnięcia i odwołać wiadomości. Datę wygaśnięcia można odwołać i ustawić tylko dla wiadomości wysyłanych do adresatów zewnętrznych.

### <a name="secure-email-scenarios-comparison-with-ome-and-sensitivity-labels"></a>Zabezpieczanie porównania scenariuszy wiadomości e-mail z OME i etykietami wrażliwości

Etykiety OME i wrażliwości stosowane do wiadomości e-mail z szyfrowaniem nakładają się, dlatego ważne jest zrozumienie scenariuszy, których może dotyczyć szyfrowanie, jak pokazano w poniższej tabeli.

| Scenariusz | Etykiety wrażliwości | OME |
|:-------|:-----|:-------|
| Wewnętrzni + partnerzy <br> Bezpieczna komunikacja i współpraca między użytkownikami wewnętrznymi i zaufanymi partnerami | Zalecane — etykiety z w pełni dostosowaną klasyfikacją i ochroną | Tak — tylko szyfrowanie lub nie przesyłaj dalej ochrony bez klasyfikacji |
| Strony zewnętrzne <br> Bezpieczna komunikacja i współpraca z dowolnymi użytkownikami zewnętrznymi/konsumenckimi | Tak — wstępnie zdefiniowany adresaci w etykiecie | Zalecane — ochrona przed just-in-time na podstawie adresatów |
| Wewnętrzni + partnerzy z wygasaniem/odwołaniami <br> Kontrolowanie dostępu do poczty i zawartości za pomocą wygasania i odwołań w przypadku użytkowników wewnętrznych i zaufanych partnerów | Zalecane — w pełni dostosowana ochrona z czasem trwania dostępu, użytkownik może ręcznie śledzić i cofać pliki | Nie — brak odwołania lub wygaśnięcia dla poczty wewnętrznej |
| Strony zewnętrzne z wygasaniem/odwołaniami <br> Kontrolowanie dostępu do poczty i zawartości z użytkownikami zewnętrznymi/konsumenckimi za pomocą wygasania i odwołania | Tak — użytkownik może ręcznie śledzić pliki | Zalecane (E5) — administrator może odwołać pocztę z Centrum zabezpieczeń & zgodności |
| Automatyczne oznaczanie etykiet <br> Organizacja chce automatycznie chronić wiadomości/załączniki za pomocą konkretnej poufnej zawartości i/lub określonych adresatów | Zalecane (E5) — automatyczne oznaczanie etykiet w klientach Exchange i Outlook, ulepsza reguły przepływu poczty i zasady DLP | Tak — reguły przepływu poczty i zasady DLP z tylko szyfrowaniem lub ochroną Nie przesyłaj dalej |
||||

Między tymi dwiema metodami wystąpią również różnice w działaniach użytkowników końcowych i administratorów.

## <a name="teams-with-protection-for-highly-sensitive-data"></a>Teams z ochroną bardzo poufnych danych

W przypadku organizacji, które planują przechowywać dane osobowe objęte przepisami dotyczącymi prywatności danych w programie Teams, zobacz Konfigurowanie zespołu izolacji [zabezpieczeń, który](secure-teams-security-isolation.md) zawiera szczegółowe wskazówki i kroki konfiguracyjne dla:

- Tożsamość i dostęp do urządzeń
- Tworzenie zespołu prywatnego
- Blokowanie podstawowych uprawnień witryny zespołu
- Etykieta wrażliwości grupowej z szyfrowaniem
