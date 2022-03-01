---
title: Oceniaj zagrożenia związane z prywatnością danych i identyfikowanie elementów poufnych za pomocą Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 07/13/2020
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
description: Określ przepisy dotyczące prywatności danych, odpowiednie scenariusze, gotowość użytkowników i typy informacji poufnych w Twoim Microsoft 365 sieci.
ms.openlocfilehash: 5f8b5844ad3db4152a6144f9506a0267fa3af8f2
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009797"
---
# <a name="assess-data-privacy-risks-and-identify-sensitive-items-with-microsoft-365"></a>Oceniaj zagrożenia związane z prywatnością danych i identyfikowanie elementów poufnych za pomocą Microsoft 365

Ocena przepisów dotyczących prywatności danych i zagrożeń, których podlega Twoja organizacja, to pierwszy krok przed zaimplementowaniem jakichkolwiek powiązanych działań udoskonalania, w tym akcji, które można Microsoft 365 za pomocą funkcji i usług.

## <a name="potentially-applicable-data-privacy-regulations"></a>Potencjalnie obowiązujące przepisy dotyczące prywatności danych

Aby uzyskać więcej informacji na temat szerszej struktury prawnej dotyczącej przepisów dotyczących prywatności danych, zobacz Portal zaufania usług firmy [Microsoft](https://servicetrust.microsoft.com/) i szereg artykułów dotyczących ogólnego rozporządzenia o ochronie danych [(RODO](/compliance/regulatory/gdpr)). Zapoznaj się także z materiałami dotyczącymi przepisów, które mogą podlegać w swojej branży lub regionie.

### <a name="gdpr"></a>RODO

RODO to najbardziej znane i cytowane przepisy dotyczące ochrony prywatności danych. Reguła ta dotyczy gromadzenia, przechowywania, przetwarzania i udostępniania wszelkich danych osobowych związanych z identyfikowaną lub możliwa do zidentyfikowania osobą fizyczną, która jest rezydentem Unii Europejskiej.

Zgodnie z artykułem 4 rodo:

- "dane osobowe" oznaczają wszelkie informacje związane z identyfikowaną lub identyfikowalną osobą fizyczną ('podmiotem danych); identyfikowalna osoba fizyczna to osoba, która może być identyfikowana bezpośrednio lub pośrednio, w szczególności przez odwołanie się do identyfikatora, takiego jak imię i nazwisko, numer identyfikacyjny, dane lokalizacji, identyfikator online lub jeden lub więcej czynników specyficznych dla tożsamości fizycznej, genetycznej, genetycznej, umysłowej, ekonomicznej, kultury lub tożsamości społecznościowej tej osoby fizycznej.

### <a name="iso-27001"></a>ISO 27001

Wstrzymywanie się od innych standardów, takich jak ISO 27001, zostały również rozpoznane przez kilka europejskich urzędów nadzorczych jako prawidłowy serwer proxy intencji dla wszystkich osób, procesów i zakresu technologii. Standardy nakładające się i odpowiednie dla mechanizmów ochrony sterowanych normą ISO-27001 można uznać za serwera proxy, który w określonych okolicznościach spełnia niektóre zobowiązania dotyczące prywatności.

### <a name="other-data-privacy-regulations"></a>Inne przepisy dotyczące ochrony prywatności danych

Inne widoczne przepisy dotyczące ochrony prywatności dotyczące danych określają również wymagania dotyczące przetwarzania danych osobowych.

W Stanach Zjednoczonych obejmują one ustawę California Consumer Protection Act ([HIPAA), HIPAA-HITECH](/compliance/regulatory/ccpa-faq) (United States health care privacy act) i Grahama Leacha Bliley Act (GLBA). Dodatkowe przepisy specyficzne dla województwa są również w miejscu lub w miejscu opracowywania.

Na całym świecie mogą to być na przykład niemiecka państwowa ustawa implementacji RODO (BDSG), ustawa o ochronie danych w Brazylii (LGPD) i wiele innych.

## <a name="regulation-mapping-to-microsoft-365-technical-control-categories"></a>Mapowanie przepisów Microsoft 365 kategoriach kontroli technicznej

Wiele przepisów związanych z prywatnością danych ma nakładające się wymagania, dlatego przed opracowaniem jakiegokolwiek schematu kontroli technicznej należy zrozumieć, jakich przepisów one podlegają.

W dalszej części artykułów dotyczących tego ogólnego rozwiązania ta tabela zawiera fragmenty przykładów przepisów dotyczących prywatności danych.

|Rozporządzenie|Artykuł/sekcja|Fragment|Odpowiednie kategorie kontroli technicznej|
|---|---|---|---|
|RODO|Artykuł 5(1)(f)|Dane osobowe będą przetwarzane w sposób zapewniający odpowiednie bezpieczeństwo danych osobowych, w tym ochronę przed nieautoryzowanym lub niezgodnym z prawem przetwarzaniem oraz przed przypadkową utratą, naruszeniem lub uszkodzeniem przy użyciu odpowiednich środków technicznych lub organizacyjnych (integralności i poufności).|(Wszystko) <br> Tożsamości <br> Urządzenie <br> Ochrona przed zagrożeniami <br> Ochrona informacji <br> Reguluj informacje <br> Odnajdowanie i odpowiadanie|
||Artykuł (32)(1)(a)|Uwzględniając stan techniki, koszty wdrożenia oraz charakter, zakres, kontekst i cele przetwarzania, a także ryzyko zróżnicowanego prawdopodobieństwa i istotności praw i swobody osób naturalnych, kontroler i podmiot przetwarzający będą wdrażać odpowiednie środki techniczne i organizacyjne w celu zapewnienia poziomu zabezpieczeń odpowiedniego dla ryzyka.  w tym między między, jeśli to konieczne: (a) pseudonimizacja i szyfrowanie danych osobistych.|Ochrona informacji|
||Artykuł (13)(2)(a)|"... W momencie zbierania danych osobowych administrator musi podać podmiotowi danych następujące dodatkowe informacje niezbędne do zapewnienia uczciwego i przejrzystego przetwarzania: (a) okres przechowywania danych osobowych lub, jeśli jest to niemożliwe, kryteria użyte do określenia tego okresu.|Reguluj informacje|
||Artykuł (15)(1)(e)|Podmiot danych ma prawo do uzyskania od kontrolera potwierdzenia, że dane osobowe dotyczące tej podmiotu są przetwarzane, a w takim przypadku dostęp do danych osobowych oraz do następujących informacji: (e) istnieje prawo do żądania od administratora danych danych osobowych lub usunięcia danych osobowych albo ograniczenia przetwarzania danych osobowych dotyczących danych osobowych osób, których dane dotyczą, lub do obiektu takiego przetwarzanie|Odnajdowanie i odpowiadanie|
|LGPD|Artykuł 46|Pełnomocnicy przetwarzania będą korzystać z zabezpieczeń, środków technicznych i administracyjnych w celu ochrony danych osobowych przed nieautoryzowanym dostępem i przypadkowymi lub niedozwolonymi sytuacjami, w przypadku których użytkownik utracił możliwość zmiany, zmiany, komunikacji albo wszelkiego rodzaju nieprawidłowego lub niezgodnego z prawem przetwarzania.|Ochrona informacji <br> Reguluj informacje <br> Odnajdowanie i odpowiadanie|
||Artykuł 48|Kontroler musi przekazać dane właściwemu organowi państwowemu i podmiotowi danych informacje o wystąpieniu zdarzenia związanego z zabezpieczeniami, które może spowodować wystąpienie ryzyka lub istotnego uszkodzenia danych.|Odnajdowanie i odpowiadanie|
|HIPPA-HITECH|45 CFR 164.312(e)(1)|Wdrażaj zabezpieczenia techniczne, aby chronić się przed nieautoryzowanym dostępem do chronionych informacji o kondycji elektronicznej przesyłanych przez sieć komunikacji elektronicznej.|Ochrona informacji|
||45 c.F.R. 164.312(e)(2)(ii)|Wdrożenie mechanizmu szyfrowania chronionych elektronicznych informacji o stanie zdrowia, gdy zostanie to uznane za odpowiednie.|Ochrona informacji|
||45 CFR 164.312(c)(2)|Wdrażaj mechanizmy elektroniczne w celu potwierdzenia, że informacje o kondycji chronionej drogą elektroniczną nie zostały zmienione ani zniszczyne w nieautoryzowany sposób.|Reguluj informacje|
||45 CFR 164.316(b)(1)(i)|Jeśli w ramach tej podczęści wymagane jest akcję, działanie lub ocena do dokumentacji, zachowaj pisemny (elektroniczny) rejestr akcji, działania lub oceny.|Reguluj informacje|
||45 CFR 164.316(b)(1)(ii)|Zachowaj dokumentację wymaganą w punkcie (b)(1) tej sekcji przez 6 lat od daty jej utworzenia lub daty, kiedy ostatnio obowiązywała, w zależności od tego, co nastąpi później.|Reguluj informacje|
||45 c.F.R. 164.308(a)(1)(ii)(D)|Implementowanie procedur w celu regularnego przeglądania rejestrów działań systemu informacyjnego, takich jak dzienniki inspekcji, raporty dostępu i raporty śledzenia zdarzeń związanych z zabezpieczeniami|Odnajdowanie i odpowiadanie|
||45 c.F.R. 164.308(a)(6)(ii)|identyfikować podejrzewanych lub znanych zdarzeń zabezpieczających i odpowiadać na nie; ograniczanie w takim zakresie szkodliwych efektów zdarzeń zabezpieczających znanych podmiotowi objętemu lub skojarzeń biznesowych; i udokumentuj zdarzenia dotyczące zabezpieczeń oraz ich wyniki.|Odnajdowanie i odpowiadanie|
||45 c.F.R. 164,312(b)|Wdrożenie mechanizmów sprzętu, oprogramowania i procedur, które rejestrują i badają działania w systemach informacyjnych, które zawierają lub używają elektronicznych informacji o kondycji.|Odnajdowanie i odpowiadanie|
|PRZEJDĘĆ DO PRACY|1798.105(c)|Firma, która otrzymuje od klienta weryfikowalne żądanie usunięcia danych osobowych klienta na mocy częściowej (a) tej sekcji, spowoduje usunięcie danych osobowych klienta z jego rekordów i pokieruje wszystkich usługodawców do usunięcia danych osobowych klienta z jego rekordów.|Odnajdowanie i odpowiadanie|
||1798.105(d)|(wyjątki od 1798.105(c) <br> Firma lub usługodawca nie jest zobowiązany do przestrzegania wniosku konsumenckiego o usunięcie danych osobowych klienta, jeśli jest to konieczne, aby firma lub firma usługodawca zachowywała dane osobowe klienta w celu: (dodatkowe informacje można znaleźć w niniejszym rozporządzeniem).|Odnajdowanie i odpowiadanie|
|||||

> [!IMPORTANT]
> Nie jest to pełna lista. Aby uzyskać [więcej](../compliance/compliance-manager.md) informacji na temat stosowania cytowanych sekcji do wymienionych kategorii kontroli technicznej, zobacz Menedżer zgodności lub doradca ds. zgodności.

## <a name="knowing-your-data"></a>Znajomość danych

Niezależnie od przepisów, których podlegasz, interakcja różnych typów danych użytkowników w Twojej organizacji i poza nią z Twoimi systemami to wszystkie ważne czynniki, które mogą mieć wpływ na ogólną strategię ochrony danych osobowych, z zastrzeżeniem przepisów branżowych i rządowych dotyczących Twojej organizacji. Obejmuje to miejsce przechowywania danych osobowych, ich typ i ich miejsce oraz okoliczności ich zebrania.

![Wiedza o danych: Jaki to jest typ i jaka jest ich część oraz w jakich okolicznościach zostały zebrane.](../media/information-protection-deploy-assess/information-protection-deploy-assess-knowing-data.png)

### <a name="data-portability"></a>Przenośność danych

Dane są także przemieszczane w czasie, gdy są przetwarzane, udoskonalone, a inne wersje są z nich wyprowadzane. Początkowa migawka nigdy nie wystarcza. Znajomość danych musi być w toku. Jest to jedno z największych wyzwań dla dużych organizacji, które obsługują duże ilości danych osobowych. Organizacje, które nie mają rozwiązania problemu z "znajmij swoje dane", mogą mieć potencjalnie duże ryzyko i zostać nałożona na wiele możliwych nałogów ze strony organów prawnych.

![Cykl życia danych.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-lifecycle.png)

### <a name="where-the-personal-data-is"></a>Gdzie są dane osobowe

Aby zająć się przepisami dotyczącymi prywatności danych, nie możesz polegać na ogólnych rozwiązaniach dotyczących tego, gdzie mogą istnieć dane osobowe teraz lub w przyszłości. Przepisy dotyczące ochrony prywatności danych wymagają, aby organizacje potwierdzały, że na bieżąco znają miejsca, w których dane osobowe są aktualne. Dlatego ważne jest utworzenie wstępnej migawki wszystkich źródeł danych w celu ewentualnego przechowywania informacji osobistych, w tym środowiska usługi Microsoft 365, oraz utworzenie mechanizmów ciągłego monitorowania i wykrywania.

Jeśli twoja ogólna gotowość i ryzyko związane z przepisami dotyczącymi prywatności danych nie zostały jeszcze ocenić, skorzystaj z 3-krokowej poniższej struktury, aby rozpocząć pracę.

![Procedura oceny ogólnej gotowości i ryzyka związanego z przepisami dotyczącymi prywatności danych.](../media/information-protection-deploy-assess/information-protection-deploy-assess-grid.png)

> [!NOTE]
> Ten artykuł i jego zawartość nie mogą służyć jako miejsce porad prawnych. Udostępnia jedynie podstawowe wskazówki i linki do narzędzi, które mogą okazać się pomocne na wczesnych etapach procesu oceny.

## <a name="step-1-develop-a-foundational-understanding-of-your-organizations-personal-data-scenarios"></a>Krok 1. Opracuj wiedzę na temat scenariuszy dotyczących danych osobistych w Twojej organizacji

Musisz ocenić narażenie na ryzyko związane z prywatnością danych na podstawie typu danych osobowych, którym obecnie zarządza, gdzie są one przechowywane, jakie środki zabezpieczające są na nim umieszczone, jak jest zarządzana ich cykl życia i kto ma do nich dostęp.

Na początek warto zasypować, jakie typy danych osobistych istnieją w twoim środowisku Microsoft 365 danych. Użyj tych kategorii:

- Dane pracowników wymagane do wykonywania codziennie funkcji biznesowych
- Dane organizacji dotyczące klientów biznesowych, partnerów i innych relacji w scenariuszu między firmami (B2B)
- Dane organizacji dotyczące klientów, którzy dostarczają informacje do usług online, które organizacja zarządza w scenariuszu business-to-customer (B2C)

Oto przykład różnych typów danych dla typowych działów organizacji.

![Typy danych osobowych.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-types.png)

Duża część danych osobowych, które podlegają rozporządzeniem o ochronie prywatności danych, jest zazwyczaj zbierana i przechowywana poza Microsoft 365. Wszelkie dane osobowe z aplikacji mobilnych i internetowych dla klientów przenośnych powinny być wyeksportowane z takich aplikacji do firmy Microsoft 365 w celu zachowania kontroli prywatności w ramach Microsoft 365.

Ochrona prywatności w Twoich danych w Microsoft 365 może być bardziej ograniczona w porównaniu z Twoimi aplikacjami internetowymi i systemami CRM, których to rozwiązanie nie dotyczy.

Oceniając profil ryzyka, należy również pamiętać o następujących typowych wyzwaniach związanych ze zgodnością z prywatnością danych:

- **Rozpowszechnianie danych osobowych.** Jak rozproszone są informacje dotyczące danego tematu? Czy jest to wystarczająco dobrze znane, aby przekonać podmioty prawne, że w ich miejscu są właściwe mechanizmy kontroli? Czy w razie potrzeby można go zbadać i rozwiązać?
- **Ochrona przed wykrzykniem.** Jak chronić dane osobowe danego typu lub źródła przed naruszeniami zabezpieczeń i jak zareagować na nie?
- **Ochrona a ryzyko.** Jakie mechanizmy ochrony informacji są odpowiednie w odniesieniu do ryzyka i jak zapewnić ciągłość działania i produktywność oraz zminimalizować wpływ użytkowników końcowych, jeśli wymagana jest interwencja użytkownika końcowego? Na przykład czy należy użyć ręcznej klasyfikacji lub szyfrowania?
- **Przechowywanie danych osobowych.** Jak długo informacje zawierające dane osobowe muszą być przechowywane z ważnego powodu biznesowego i jak unikać praktyk zachowania bez końca życia, które są równoważyć potrzebami przechowywania dla ciągłości działania firmy?
- **Obsługa żądań osób, których dane dotyczą.** Jakie mechanizmy będą potrzebne do obsługi żądań osób, których dane dotyczą, i wszelkich działań naprawczych, takich jak anonimizacja, ponowne działanie i usuwanie?
- **Bieżące monitorowanie i raportowanie.** Jakie rodzaje technik monitorowania, badania i raportowania są dostępne w przypadku różnych typów danych i źródeł?
- **Ograniczenia przetwarzania danych.** Czy istnieją ograniczenia dotyczące używania danych do informacji zbieranych lub przechowywanych przy użyciu tych metod, które organizacja musi odzwierciedlić w mechanizmach kontroli prywatności? Na przykład zobowiązania, za pomocą których pracownicy działu sprzedaży nie będą używać danych osobowych, mogą wymagać od organizacji stosować mechanizmy uniemożliwiające przekazywanie lub przechowywanie tych informacji w systemach powiązanych z organizacją sprzedaży.

### <a name="employee-data-required-to-carry-out-day-to-day-business-functions"></a>Dane pracowników wymagane do wykonywania codziennie funkcji biznesowych

Organizacje z natury muszą zbierać dane na temat pracowników na potrzeby tożsamości elektronicznej i celów kadrowych, z zastrzeżeniem zgody zawartej w ich umowach pracowników. O ile osoba pracuje w firmie, zwykle nie stanowi to problemu. Organizacja może chcieć wprowadzić mechanizmy, aby zapobiec złośliwym atakom, które podszywają się pod innych pracowników lub wyciekają ich dane osobowe.

Gdy osoba odchodzi z firmy, organizacje zazwyczaj mają procesy, procedury oraz harmonogramy przechowywania i usuwania dotyczące usuwania kont użytkowników, likwidowania skrzynek pocztowych i dysków osobistych oraz zmieniania statusu pracownika w systemach kadrowych. W przypadku postępowania sądowego pracownik lub inna strona w śledztwie sądowym może mieć prawidłowe powody uzyskiwania informacji o danych osobowych przechowywanych w systemach organizacji. W niektórych przypadkach strona ta może zażądać usunięcia lub zanonimizacji takich danych.

Aby można było rozwiązać takie potrzeby, organizacje powinny stosować procesy i procedury służące do zapobiegania, wykrywania i rozwiązywania problemów, które muszą ułatwić takie żądania, zauważyć, że niektóre informacje o pracowniku mogą być w uzasadniony sposób traktowane jako kluczowe dla ciągłości działalności. Mogą to być na przykład informacje o tym, że autorem pliku lub funkcja została wykonana przez poszczególnych użytkowników.

> [!NOTE]
> Aby uzyskać informacje na temat technik badania i rozwiązywania problemów dotyczących danych Microsoft 365 danych osobowych, zobacz [artykuł monitorowanie i odpowiadanie](information-protection-deploy-monitor-respond.md). Możesz również stosować automatyczne schematy klasyfikacji i ochrony w celu upewnienia się, że dane osobowe są kontrolowane w organizacji, a także aby zapobiec opuszczeniu organizacji w sytuacjach złośliwego podmiotu. Aby uzyskać [więcej informacji, zobacz artykuł](information-protection-deploy-protect-information.md) na temat ochrony informacji.

### <a name="data-the-organization-has-about-its-business-customers-in-the-b2b-scenario"></a>Dane organizacji dotyczące klientów biznesowych w scenariuszu B2B

Zbieranie informacji B2B również stanowi wyzwanie, ponieważ w celu zapewnienia ciągłości działania informacji w organizacji może być konieczne zachowanie informacji o nazwach klientów i transakcjach w różnych systemach, aby zapewnić ciągłość działania tych informacji. Podobnie jak dane pracowników, organizacje muszą mieć zasady, procedury i mechanizmy kontroli technicznej, aby chronić takie dane, a także wiekować je zgodnie ze zdefiniowanymi harmonogramami przechowywania i usuwania.

Zazwyczaj umowy z kontrahentami zewnętrznymi, partnerami i innymi jednostkami, z którymi współpracuje firma, będą mieć język adresowania do obsługi takich danych, w tym ochrony, przechowywania i usuwania zarówno podczas, jak i po nawiązyniu relacji z organizacją.

### <a name="data-the-organization-has-about-consumers-who-provide-information-to-online-services-that-the-organization-manages-in-the-b2c-scenario"></a>Dane organizacji dotyczące klientów, którzy dostarczają informacje usługom online, które organizacja zarządza w scenariuszu B2C

Jest to kategoria, która jest tą, która jest według większości użytkowników uważana za prywatność danych ze względu na wiele publicznych wystąpień wycieku danych klientów. To działanie może być celowe, na przykład w przypadku innej firmy w ramach umowy z dostawcą, lub niezamierzone, na przykład eksstrukcje ze strony złośliwego podmiotu. Ochrona danych klientów jest jednym z głównych powodów, dla których Te przepisy są przenoszone przez Ue i inne. Przepisy dotyczące ochrony prywatności danych, takie jak GDPR iKUTA, wymagają planowania:

- [Plany działania](/compliance/regulatory/gdpr-action-plan) [i listy kontrolne gotowości do odpowiedzialności](/compliance/regulatory/gdpr-arc-Office365)
- [Oceny wpływu na ochronę danych](/compliance/regulatory/gdpr-data-protection-impact-assessments)
- [Powiadomienia o naruszeniach zabezpieczeń](/compliance/regulatory/gdpr-breach-Office365)
- [Żądania osób, których dane dotyczą](/compliance/regulatory/gdpr-dsr-Office365)

Jeśli Twoja organizacja nie chce gromadzenia danych bezpośrednio od klientów, ta kategoria może być mniej problemów. Jednak w celu zapewnienia zgodności może być nadal konieczne spełnienie procesów opisanych w tych artykułach.

### <a name="step-1-summary"></a>Podsumowanie kroku 1

Zrozumienie twojego ryzyka i przepisów o ochronie prywatności danych to ważny pierwszy krok, który opiera się na podstawowego zrozumieniu scenariuszy dotyczących danych osobowych Twojej organizacji.

Jeśli nie masz danych osobowych poszczególnych klientów w Twoim środowisku Microsoft 365 lub są one ograniczone do określonych części środowiska i konieczność kontroli technicznej jest przesądzona o tym, że istnieje ekspozycja danych konsumentów, oznacza to, że kontrola techniczna może być potrzebna tylko w bardzo ryzykownych częściach środowiska, nie wszędzie.

Podczas gdy organizacja zewnętrzna lub standardowa organizacja zestawu kontrolek, na przykład z Menedżera zgodności w programie Microsoft 365, może pomóc Ci w poinformowaniu o strategii kontroli, Twój wybór implementacji powinien być prowadzony przez poinformowanie o zapasach danych, aby określić rzeczywisty poziom ryzyka.

Większość organizacji będzie mieć dostęp do jednego z powyższych scenariuszy. Ważne jest, aby można było zdać ocenę w sposób zawęziowy.

## <a name="step-2-assess-your-readiness-for-complying-with-data-privacy-regulations"></a>Krok 2. Ocena gotowości do przestrzegania przepisów dotyczących prywatności danych

Chociaż są one specyficzne dla RODO, pytania zadawane w bezpłatnym narzędziu do oceny RODO firmy [Microsoft](https://clouddamcdnprodep.azureedge.net/gdc/1863571/original) stanowią dobry początek zrozumienia Twojej ogólnej gotowości do ochrony prywatności danych.

Organizacje objęte innymi przepisami dotyczącymi prywatności danych, takimi jak PONAZ() w Stanach Zjednoczonych lub LGPD Brazylii, mogą również korzystać ze spisu gotowości tego narzędzia ze względu na nakładające się postanowienia RODO.

Ocena RODO składa się z tych sekcji:

|Sekcja|Opis|
|:-------|:-----|
|Nadzór|<ol><li>Czy twoje zasady ochrony prywatności jawnie podają, które informacje o danych są przetwarzane? </li><li>Czy regularnie przeprowadzasz oceny wpływu na prywatność? </li><li> Czy używasz narzędzia do zarządzania informacjami osobistymi?. </li><li> Czy masz uprawnienia do prowadzenia działalności biznesowej przy użyciu danych PI dla dowolnej osoby? Czy śledzisz zgodę na dane? </li><li> Czy śledzisz i wdrażasz kontrolki inspekcji oraz zarządzasz nimi? Czy monitorujesz się pod wykrywaniem wycieków danych? </li></ol>|
|Usuwanie i powiadamianie|<ol><li>Czy udzielasz jawnych instrukcji dotyczących sposobu, w jaki można uzyskać dostęp do danych użytkowników? </li><li> Czy zostały przez Ciebie udokumentowane procesy obsługi wyrażania zgody na rezygnację? </li><li> Czy masz proces automatycznego usuwania danych? </li><li> Czy masz proces weryfikacji tożsamości podczas współpracy z klientem? </li></ol>|
|Ograniczanie ryzyka i bezpieczeństwo informacji|<ol><li>Czy używasz narzędzi do skanowania danych bez struktury? </li><li>Czy wszystkie serwery są aktualne i czy korzystasz z zapór w celu ich ochrony? </li><li>Czy uruchamiasz regularne kopie zapasowe serwerów? </li><li>Czy aktywnie monitorujesz wycieki danych? </li><li>Czy szyfrujesz dane w czasie spoczynku i podczas transmisji? </li></ol>|
|Zarządzanie zasadami|<ol><li>Jak zarządzać wiążące reguły firmowe? </li><li>Czy śledzisz zgodę na dane? </li><li> Czy twoje kontrakty obejmują całkowicie klasyfikacje danych i wymagania w zakresie obsługi, których zakres wynosi od 1 do 5? </li><li>Czy masz i regularnie testujesz plan reakcji na incydenty? </li><li>Jakich zasad używasz do zarządzania dostępem? </li></ol>|
|||

## <a name="step-3-identify-sensitive-information-types-that-occur-in-your-microsoft-365-environment"></a>Krok 3. Identyfikowanie typów informacji poufnych, które występują w Microsoft 365 użytkownika

Ten krok obejmuje identyfikację określonych typów informacji poufnych, które podlegają określonym kontrolom regulacyjnym, a także występowanie ich w Twoim środowisku Microsoft 365 informacji.

Znajdowanie zawartości w środowisku zawierającej dane osobowe może być bardzo groźnym zadaniem, które wcześniej polegało na skojarzeniu z wyszukiwaniem zgodności, zbierania elektronicznych materiałów dowodowych, zbierania elektronicznych materiałów dowodowych, Advanced eDiscovery dlp i inspekcją.

Dzięki nowemu  rozwiązaniu klasyfikacji danych w centrum administracyjnym zgodności firmy Microsoft stało się to o wiele prostsze [](../compliance/data-classification-content-explorer.md) dzięki funkcji Eksploratora zawartości, która działa z wbudowanymi lub niestandardowymi typami informacji poufnych, w tym z danymi osobistymi.

### <a name="sensitive-information-types"></a>Typy informacji poufnych

Centrum administracyjne zgodności firmy Microsoft jest wstępnie załadowane z ponad 100 typami informacji poufnych, z których większość dotyczy identyfikowania i lokalizowania danych osobistych. Te wbudowane typy informacji poufnych pomagają identyfikować i chronić numery kart kredytowych, numery kont bankowych, numery paszportów i inne dane na podstawie wzorców zdefiniowanych przez wyrażenie regularne (regex) lub funkcję. Aby dowiedzieć się więcej, zobacz [Temat, jakiego typu informacje poufne należy szukać](../compliance/sensitive-information-type-entity-definitions.md).

Jeśli musisz zidentyfikować i chronić określony w organizacji lub regionalny typ elementów poufnych, taki jak format niestandardowy identyfikatorów pracowników lub inne informacje osobiste, które nie są jeszcze objęte wbudowanym typem informacji poufnych, możesz utworzyć niestandardowy typ informacji poufnych, korzystając z tych metod:

- PowerShell
- Reguły niestandardowe z dokładnym dopasowaniem danych (EDM)
- Za pośrednictwem interfejsu użytkownika administratora Centrum zgodności, jak podkreślono w artykule Korzystanie z wyników [zgodności i Menedżera zgodności](information-protection-deploy-compliance.md)

Możesz także dostosować istniejący, wbudowany typ informacji poufnych.

Aby uzyskać więcej informacji, zobacz następujące artykuły:

- [Dostosowywanie wbudowanego typu informacji poufnych](../compliance/customize-a-built-in-sensitive-information-type.md)
- [Informacje o typach informacji poufnych](../compliance/sensitive-information-type-learn-about.md)
- [Tworzenie niestandardowego typu informacji poufnych w Centrum & zabezpieczeń](../compliance/create-a-custom-sensitive-information-type.md)
- [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell & w Centrum zgodności](../compliance/create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Tworzenie niestandardowych typów informacji poufnych z klasyfikacją na podstawie dokładnego dopasowania danych](../compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)

### <a name="content-explorer"></a>Eksplorator zawartości

Ważnym narzędziem do określania wystąpienia poufnych elementów w środowisku jest nowy Eksplorator zawartości w [](../compliance/data-classification-content-explorer.md) centrum administracyjnym Microsoft 365 zgodności. Jest to zautomatyzowane narzędzie do początkowego i trwającego skanowania całej subskrypcji usługi Microsoft 365 w celu wystąpienia typów informacji poufnych i wyświetlania wyników.

Nowe narzędzie Eksplorator zawartości umożliwia szybkie identyfikowanie lokalizacji poufnych elementów w środowisku przy użyciu wbudowanych typów informacji poufnych lub niestandardowych. Może to obejmować ustanowienie procesu i przypisanie mu odpowiedzialności za regularne badanie obecności i lokalizacji poufnych elementów.

Oprócz pozostałych czynności ważnych w tym artykule stanowi to punkt wyjścia do zidentyfikowania ogólnego narażenia na ryzyko, gotowości i lokalizacji poufnych elementów w celu ochrony za pomocą zaplanowanych Microsoft 365 konfiguracji i monitorowania.

### <a name="other-methods-to-identify-personal-data-in-your-environment"></a>Inne metody identyfikowania danych osobowych w środowisku użytkownika

Poza Eksploratorem zawartości organizacje mają dostęp do funkcji przeszukiwania zawartości w celu wyszukiwania niestandardowego w celu znalezienia danych osobistych w ich środowisku przy użyciu zaawansowanych kryteriów wyszukiwania i filtrów niestandardowych.

Szczegółowe wskazówki dotyczące korzystania z wyszukiwania zawartości w celu odnajdowania danych osobistych podano w [tym artykule](/compliance/regulatory/gdpr). Przeszukiwanie zawartości i inne techniki odnajdowania są również eksplorowane w [regułach DSR (RODO) i KPI(-a).](/compliance/regulatory/gdpr-dsr-Office365#introduction-to-dsrs)

Dodatkowe informacje na temat technik badań i rozwiązywania problemów dotyczących danych osobowych w programie Microsoft 365 znajdują się w [artykule na temat monitorowania i odpowiadania](information-protection-deploy-monitor-respond.md).

> [!NOTE]
> Informacje poufne zapisane w plikach przechowywanych lokalnie można znaleźć w [usłudze Azure Information Protection](/azure/information-protection/quickstart-findsensitiveinfo).
