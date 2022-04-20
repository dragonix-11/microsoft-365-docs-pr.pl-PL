---
title: Kluczowe zagadnienia dotyczące zgodności i zabezpieczeń dla amerykańskich rynków bankowych i kapitałowych
ms.author: bcarter
author: brendacarter
manager: laurawi
audience: ITPro
ms.topic: article
ms.collection:
- M365-security-compliance
ms.prod: microsoft-365-enterprise
ms.custom: seo-marvel-jun2020
ms.localizationpriority: high
description: Dowiedz się, jak instytucje usług finansowych mogą zachować zgodność z zabezpieczeniami finansowymi i efektywnie współpracować przy użyciu Microsoft 365 i Teams.
f1.keywords: NOCSH
ms.openlocfilehash: ed00d120d00253c1abbb6d0c0109fdce0b7ff863
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948270"
---
# <a name="key-compliance-and-security-considerations-for-us-banking-and-capital-markets"></a>Kluczowe zagadnienia dotyczące zgodności i zabezpieczeń dla amerykańskich rynków bankowych i kapitałowych

## <a name="introduction"></a>Wprowadzenie
Instytucje usług finansowych przewyższają niemal wszystkie przedsiębiorstwa komercyjne, które wymagają rygorystycznych kontroli bezpieczeństwa, zgodności i ładu. Ochrona danych, tożsamości, urządzeń i aplikacji jest nie tylko krytyczna dla ich działalności, ale podlega wymogom i wytycznym dotyczącym zgodności ze strony organów regulacyjnych, takich jak Amerykańska Komisja Papierów Wartościowych i Exchange (SEC), Financial Industry Regulatory Authority (FINRA), Federal Financial Institutions Examination Council (FFIEC) i Commodity Futures Trading Commission (CFTC). Ponadto instytucje finansowe podlegają przepisom takim jak Dodd-Frank i ustawa o Sarbanes-Oxley z 2002 r.

W dzisiejszym klimacie zwiększonej czujności w zakresie bezpieczeństwa, obaw związanych z ryzykiem wewnętrznym i naruszeń danych publicznych klienci domagają się również wysokiego poziomu bezpieczeństwa ze strony swoich instytucji finansowych, aby zaufać im swoim danymi osobowymi i aktywami bankowymi.

W przeszłości konieczność kompleksowych kontroli bezpośrednio wpływała i ograniczała systemy i platformy INFORMATYCZNE używane przez instytucje finansowe do umożliwienia współpracy wewnętrznej i zewnętrznej. Obecnie pracownicy usług finansowych potrzebują nowoczesnej platformy współpracy, która jest łatwa do wdrożenia i łatwa w użyciu. Jednak usługi finansowe nie mogą zapewnić elastyczności współpracy między użytkownikami, zespołami i działami przy użyciu mechanizmów kontroli zabezpieczeń i zgodności, które wymuszają zasady ochrony użytkowników i systemów INFORMATYCZNych przed zagrożeniami.

W sektorze usług finansowych należy dokładnie rozważyć konfigurację i wdrożenie narzędzi współpracy i mechanizmów kontroli zabezpieczeń, w tym:
- Ocena ryzyka typowych scenariuszy współpracy organizacyjnej i procesów biznesowych
- Wymagania dotyczące ochrony informacji i ładu danych
- Cyberbezpieczeństwo i zagrożenia wewnętrzne
- Wymagania dotyczące zgodności z przepisami
- Inne zagrożenia operacyjne

**Microsoft 365 to nowoczesne środowisko chmury w miejscu pracy, które może sprostać współczesnym wyzwaniom, przed którymi stoją organizacje usług finansowych. Bezpieczna i elastyczna współpraca w całym przedsiębiorstwie jest połączona z mechanizmami kontroli i wymuszaniem zasad w celu przestrzegania rygorystycznych ram zgodności z przepisami.** W tym artykule opisano, w jaki sposób platforma Microsoft 365 pomaga usługom finansowym przejść na nowoczesną platformę współpracy, jednocześnie pomagając zapewnić bezpieczeństwo danych i systemów oraz zapewnić zgodność z przepisami:

* Zapewnianie produktywności pracowników i organizacji przy użyciu Microsoft 365 i Microsoft Teams
* Ochrona nowoczesnej współpracy przy użyciu Microsoft 365 
* Identyfikowanie poufnych danych i zapobieganie utracie danych
* Bronić twierdzy
* Zarządzanie danymi i przestrzeganie przepisów przez efektywne zarządzanie rekordami
* Ustanawianie etycznych murów z barierami informacyjnymi
* Ochrona przed eksfiltracją danych i ryzykiem wewnętrznym

Jako partner firmy Microsoft firma Protiviti przyczyniła się do tego artykułu i przekazała do tego artykułu istotne opinie.

Poniższe ilustracje do pobrania uzupełniają ten artykuł. Woodgrove Bank i Contoso służą do zademonstrowania możliwości opisanych w tym artykule w celu spełnienia typowych wymagań prawnych dotyczących usług finansowych. Możesz dostosować te ilustracje do własnych potrzeb. 

**Microsoft 365 ilustracje dotyczące ochrony informacji i zgodności**

| Element | Opis |
|:-----|:-----|
|[![Plakat modelu: Microsoft 365 możliwości ochrony informacji i zgodności.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/>Angielski: [pobierz jako plik PDF](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| [jako Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japoński: [pobierz jako plik PDF](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)\| [jako Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)  <br/> Zaktualizowano listopad 2020 r.|Zawiera: <ul><li>  Microsoft Purview Information Protection i Microsoft Purview — zapobieganie utracie danych</li><li>Zasady przechowywania i etykiety przechowywania </li><li>Bariery informacyjne</li><li>Zgodność w komunikacji</li><li>Ryzyko związane z wewnętrznymi testerami</li><li>Pozyskiwanie danych innych firm</li>|


## <a name="empower-organizational-and-employee-productivity-by-using-microsoft-365-and-teams"></a>Zwiększanie produktywności pracowników i organizacji przy użyciu Microsoft 365 i Teams

Współpraca zwykle wymaga różnych form komunikacji, możliwości przechowywania i uzyskiwania dostępu do dokumentów/danych oraz możliwości integracji innych aplikacji w razie potrzeby. Pracownicy usług finansowych zazwyczaj muszą współpracować i komunikować się z członkami innych działów lub zespołów, a czasami z jednostkami zewnętrznymi. W związku z tym korzystanie z systemów, które tworzą silosy lub utrudniają udostępnianie informacji, jest niepożądane. Zamiast tego zaleca się korzystanie z platform i aplikacji, które umożliwiają pracownikom bezpieczną komunikację, współpracę i udostępnianie informacji zgodnie z zasadami firmy.

Zapewnienie pracownikom nowoczesnej, opartej na chmurze platformy współpracy pozwala im wybierać i integrować narzędzia, które czynią ich bardziej produktywnymi i umożliwiają im znalezienie zwinnych sposobów pracy. Korzystanie z Teams w połączeniu z mechanizmami kontroli zabezpieczeń i zasadami zarządzania informacjami, które chronią organizację, może pomóc pracownikom w efektywnej komunikacji i współpracy.

Teams udostępnia centrum współpracy dla organizacji. Pomaga zebrać ludzi, aby wydajnie pracować nad wspólnymi inicjatywami i projektami. Teams umożliwia członkom zespołu prowadzenie konwersacji na czacie 1:1 i wielu firm, współpracę i współtworzenie dokumentów oraz przechowywanie i udostępnianie plików. Teams ułatwia również spotkania online za pośrednictwem zintegrowanego głosu i wideo w przedsiębiorstwie. Teams można również dostosować za pomocą aplikacji firmy Microsoft, takich jak Microsoft Planner, Microsoft Dynamics 365, Power Apps, Power BI i aplikacji biznesowych innych firm. Teams jest przeznaczony do użytku zarówno przez wewnętrznych członków zespołu, jak i dozwolonych użytkowników zewnętrznych, którzy mogą dołączać do kanałów zespołu, uczestniczyć w konwersacjach czatów, uzyskiwać dostęp do przechowywanych plików i korzystać z innych aplikacji

Każdy zespół firmy Microsoft jest wspierany przez grupę Microsoft 365. Ta grupa jest uważana za usługę członkostwa dla wielu usług Office 365, w tym Teams. Microsoft 365 grupy służą do bezpiecznego rozróżniania "właścicieli" i "członków" oraz do kontrolowania dostępu do różnych możliwości w ramach Teams. W połączeniu z odpowiednimi kontrolami ładu i regularnie administrowanym przeglądami dostępu Teams umożliwia tylko członkom i właścicielom korzystanie z autoryzowanych kanałów i możliwości.

Typowym scenariuszem, w którym Teams korzyści z usług finansowych, jest uruchamianie wewnętrznych projektów lub programów. Na przykład wiele instytucji finansowych, w tym banki, firmy zarządzające majątkiem, unii kredytowe i dostawcy ubezpieczeń, musi dysponować programami przeciwdziałania praniu pieniędzy i innym programom zgodności. Do udostępniania danych i komunikowania się o programie lub konkretnych dochodzeniach może być wymagany zespół ds. działalności informatycznej, takich jak zarządzanie sprzedażą detaliczną i majątkiem oraz jednostka ds. przestępczości finansowej. Tradycyjnie te programy korzystały z udostępnionych dysków sieciowych, ale takie podejście może stanowić wiele wyzwań, w tym:
* Tylko jedna osoba może edytować dokument jednocześnie.
* Zarządzanie zabezpieczeniami jest czasochłonne, ponieważ dodawanie/usuwanie osób zwykle obejmuje it.
* Dane pozostają przechowywane na udostępnionych dyskach sieciowych znacznie dłużej niż jest to wymagane lub pożądane.

Teams może zapewnić przestrzeń współpracy w celu bezpiecznego przechowywania poufnych danych klienta i prowadzenia konwersacji między członkami zespołu, w których mogą być omawiane poufne tematy. Wielu członków zespołu może jednocześnie edytować lub współpracować nad jednym dokumentem. Właściciel lub koordynator programu można skonfigurować jako właściciela zespołu, a następnie dodać i usunąć członków w razie potrzeby.

Innym typowym scenariuszem jest użycie Teams jako "wirtualnego pomieszczenia danych" do bezpiecznej współpracy, w tym przechowywania dokumentów i zarządzania nimi. Członkowie zespołu i syndykaty w ramach bankowości inwestycyjnej, zarządzania aktywami lub firm private equity mogą bezpiecznie współpracować nad transakcją lub inwestycją. Zespoły funkcjonalne często biorą udział w planowaniu i realizacji takich transakcji, a możliwość bezpiecznego udostępniania danych i prowadzenia konwersacji jest podstawowym wymaganiem. Kluczowym wymaganiem jest również bezpieczne udostępnianie powiązanych dokumentów inwestorom zewnętrznym. Teams zapewnia bezpieczną i w pełni poddaną inspekcji lokalizację, z której można centralnie przechowywać, chronić i udostępniać dane inwestycyjne.

![Grupa pracowników biurowych na spotkaniu omawia obrazy na dużym pisku.](../media/m365cO19-ent-dell-latitude13-5951.jpg)
 
### <a name="teams-improve-collaboration-and-reduce-compliance-risk"></a>Teams: Zwiększanie współpracy i zmniejszanie ryzyka zgodności

Microsoft 365 udostępnia inne typowe możliwości zasad dla Teams dzięki użyciu grup Microsoft 365 jako podstawowej usługi członkostwa. Te zasady mogą pomóc usprawnić współpracę i spełnić wymagania dotyczące zgodności.

**Microsoft 365 zasad nazewnictwa grup** pomagają zapewnić, że grupy Microsoft 365, a tym samym zespoły, są nazwane zgodnie z zasadami firmy. Nazwy mogą być problematyczne, jeśli nie są odpowiednie. Na przykład pracownicy mogą nie wiedzieć, z którymi zespołami pracować lub udostępniać informacje, jeśli nazwy nie są odpowiednio stosowane. Zasady nazewnictwa grup (w tym obsługa zasad opartych na prefiksach/sufiksach i niestandardowych zablokowanych słów) mogą wymuszać dobrą "higienę" i zapobiegać używaniu określonych słów, takich jak słowa zarezerwowane lub nieodpowiednia terminologia.
  
**Microsoft 365 zasad wygasania grup** pomagają zapewnić, że grupy Microsoft 365, a tym samym zespoły, nie są zachowywane przez dłuższy czas, niż chce lub potrzebuje organizacja. Ta funkcja pomaga zapobiegać dwóm kluczowym problemom z zarządzaniem informacjami:

* Rozprzestrzenianie się zespołów, które nie są konieczne ani używane.
* Nadmierne przechowywanie danych, które nie są już wymagane lub używane przez organizację (z wyjątkiem przypadków archiwizacji/zachowania ze względów prawnych).

Administratorzy mogą określić okres wygaśnięcia dla grup Microsoft 365, takich jak 90, 180 lub 365 dni. Jeśli usługa wspierana przez grupę Microsoft 365 jest nieaktywna w okresie wygaśnięcia, właściciele grupy są powiadamiani. Jeśli nie zostanie podjęta żadna akcja, grupa Microsoft 365 i wszystkie powiązane z nimi usługi, w tym Teams, zostaną usunięte.
  
Nadmierne przechowywanie danych przechowywanych w Teams i innych usługach opartych na grupach może stanowić zagrożenie dla organizacji usług finansowych. Microsoft 365 zasad wygasania grup są zalecanym sposobem zapobiegania przechowywaniu danych, które nie są już potrzebne. W połączeniu z wbudowanymi etykietami i zasadami przechowywania Microsoft 365 pomaga zagwarantować, że organizacje przechowują tylko dane wymagane do spełnienia zasad firmy i zobowiązań w zakresie zgodności z przepisami.

#### <a name="teams-integrate-custom-requirements-with-ease"></a>Teams: Łatwe integrowanie wymagań niestandardowych

Teams domyślnie umożliwia samoobsługowe tworzenie zespołów. Jednak wiele regulowanych organizacji chce kontrolować i zrozumieć, które kanały współpracy są obecnie używane przez swoich pracowników, które kanały mogą zawierać dane poufne i własność kanałów organizacyjnych. Aby ułatwić te mechanizmy kontroli ładu, Microsoft 365 umożliwia organizacji wyłączenie tworzenia zespołów samoobsługowych. Korzystając z narzędzi do automatyzacji procesów biznesowych, takich jak microsoft Power Apps i Power Automate, organizacje mogą tworzyć i wdrażać proste formularze i procesy zatwierdzania dla pracowników w celu żądania utworzenia nowego zespołu. Po zatwierdzeniu można automatycznie aprowizować zespół i wysłać link do żądającego. W ten sposób organizacje mogą projektować i integrować swoje mechanizmy kontroli zgodności i wymagania niestandardowe w procesie tworzenia zespołu.
 
### <a name="acceptable-digital-communication-channels"></a>Akceptowalne kanały komunikacji cyfrowej

FINRA [podkreśla, że komunikacja cyfrowa firm regulowanych spełnia wymagania dotyczące rejestrowania zasad ustawy Exchange 17a-3 i 17a-4, a także finra rule series 4510](https://www.finra.org/rules-guidance/key-topics/books-records). FINRA publikuje roczny raport zawierający kluczowe ustalenia, obserwacje i skuteczne praktyki ułatwiające organizacjom poprawę zgodności i zarządzania ryzykiem. W swoim [raporcie z 2019 r. dotyczącym wyników badań i obserwacji](https://www.finra.org/rules-guidance/guidance/reports/2019-report-exam-findings-and-observations) FINRA określiła komunikację cyfrową jako kluczowy obszar, w którym firmy napotykają wyzwania zgodne z wymogami nadzoru i prowadzenia rejestrów.

Jeśli organizacja zezwala swoim pracownikom na korzystanie z określonej aplikacji, takiej jak usługa obsługi komunikatów oparta na aplikacjach lub platforma współpracy, firma musi archiwizować dokumentację biznesową i nadzorować działania i komunikację tych pracowników w tej aplikacji. Organizacje są odpowiedzialne za przeprowadzenie należytej staranności w celu zachowania zgodności z zasadami FINRA i przepisami dotyczącymi papierów wartościowych oraz za przestrzeganie potencjalnych naruszeń tych zasad związanych z używaniem takich aplikacji przez pracowników.
  
Obowiązujące praktyki zalecane przez FINRA obejmują następujące kwestie:
* Ustanowienie kompleksowego programu ładu dla kanałów komunikacji cyfrowej. Zarządzaj decyzjami organizacji dotyczącymi dozwolonych kanałów komunikacji cyfrowej i zdefiniuj procesy zgodności dla każdego kanału cyfrowego. Uważnie monitoruj szybko zmieniający się krajobraz kanałów komunikacji cyfrowej i aktualizuj procesy zgodności.
* Jasno zdefiniuj i kontroluj dopuszczalne kanały cyfrowe. Zdefiniuj zarówno zatwierdzone, jak i zabronione kanały cyfrowe. Zablokuj lub ogranicz korzystanie z zabronionych kanałów cyfrowych lub zabronionych funkcji w kanałach cyfrowych, które ograniczają zdolność organizacji do spełniania wymagań dotyczących zarządzania rekordami i nadzoru.
* Zapewnianie szkoleń dotyczących komunikacji cyfrowej. Zaimplementuj obowiązkowe programy szkoleniowe przed udzieleniem zarejestrowanym przedstawicielom dostępu do zatwierdzonych kanałów cyfrowych. Szkolenie pomaga wyjaśnić oczekiwania organizacji dotyczące biznesowej i osobistej komunikacji cyfrowej, a także prowadzi pracowników przez używanie dozwolonych funkcji każdego kanału w zgodny sposób.

Ustalenia i obserwacje FINRA dotyczące komunikacji cyfrowej odnoszą się bezpośrednio do zdolności organizacji do przestrzegania [reguły SEC 17a-4](https://www.law.cornell.edu/cfr/text/17/240.17a-4) w celu zachowania całej komunikacji związanej z działalnością biznesową, reguł FINRA [3110](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) i [3120](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) w celu nadzoru i przeglądu komunikacji oraz serii [4510](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4510) dla prowadzenia rejestrów. Commodity Futures Trading Commission (CFTC) promuluje podobne wymagania w ramach 17 CFR 131. Te przepisy zostały szczegółowo omówione w dalszej części tego artykułu.

***Teams, wraz z kompleksowym pakietem ofert Microsoft 365 zabezpieczeń i zgodności, zapewnia korporacyjny kanał komunikacji cyfrowej dla instytucji usług finansowych w celu skutecznego prowadzenia działalności i przestrzegania przepisów.*** W pozostałej części tego artykułu opisano, w jaki sposób Microsoft 365 wbudowane funkcje zarządzania rekordami, ochrony informacji, barier informacyjnych i kontroli nadzoru, Teams niezawodny zestaw narzędzi ułatwiający spełnienie tych zobowiązań regulacyjnych.

## <a name="protect-modern-collaboration-with-microsoft-365"></a>Ochrona nowoczesnej współpracy za pomocą Microsoft 365

### <a name="secure-user-identities-and-control-access"></a>Zabezpieczanie tożsamości użytkowników i kontrolowanie dostępu

***Ochrona dostępu do informacji o klientach, dokumentów finansowych i aplikacji zaczyna się od silnego zabezpieczania tożsamości użytkowników.*** Wymaga to bezpiecznej platformy dla przedsiębiorstwa do przechowywania tożsamości i zarządzania nimi, zapewniania zaufanych środków uwierzytelniania oraz dynamicznego kontrolowania dostępu do tych aplikacji.

Gdy pracownicy pracują, mogą przechodzić z aplikacji do aplikacji lub między wieloma lokalizacjami i urządzeniami. Dostęp do danych musi być uwierzytelniony w każdym kroku po drodze. Proces uwierzytelniania musi obsługiwać silny protokół i wiele czynników uwierzytelniania (takich jak jednorazowy kod dostępu SMS, aplikacja wystawcy uwierzytelniania i certyfikat), aby zapewnić, że tożsamości nie zostaną naruszone. Wymuszanie zasad dostępu opartych na ryzyku ma kluczowe znaczenie dla ochrony danych finansowych i aplikacji przed zagrożeniami wewnętrznymi, niezamierzonymi wyciekami danych i eksfiltracją danych.

Microsoft 365 zapewnia bezpieczną platformę tożsamości w [Azure Active Directory (Azure AD),](/azure/active-directory/) gdzie tożsamości są centralnie przechowywane i bezpiecznie zarządzane. Usługa Azure AD wraz z szeregiem powiązanych Microsoft 365 usług zabezpieczeń stanowi podstawę do zapewnienia pracownikom dostępu, którego potrzebują do bezpiecznej pracy, jednocześnie chroniąc organizację przed zagrożeniami.

[Usługa Azure AD Multi-Factor Authentication (MFA)](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) jest wbudowana w platformę i zapewnia dodatkowy dowód uwierzytelniania, który ułatwia potwierdzenie tożsamości użytkownika podczas uzyskiwania dostępu do poufnych danych finansowych i aplikacji. Usługa Azure MFA wymaga co najmniej dwóch form uwierzytelniania, takich jak hasło i znane urządzenie przenośne. Obsługuje ona kilka opcji uwierzytelniania drugiego czynnika, w tym:

- Aplikacja Microsoft Authenticator
- Jednorazowy kod dostępu dostarczany za pośrednictwem wiadomości SMS
- Połączenie telefoniczne, w którym użytkownik musi wprowadzić numer PIN

Jeśli hasło zostanie w jakiś sposób naruszone, potencjalny haker nadal będzie potrzebował telefonu użytkownika, aby uzyskać dostęp do danych organizacji. Ponadto Microsoft 365 używa nowoczesnego uwierzytelniania jako protokołu klucza, który zapewnia takie samo silne i bogate środowisko uwierzytelniania z przeglądarek internetowych do narzędzi do współpracy, z których pracownicy korzystają z dnia na dzień, w tym microsoft Outlook i innych aplikacji Microsoft Office.

#### <a name="passwordless"></a>Bez hasła

Hasła to najsłabsze łącze w łańcuchu zabezpieczeń. Mogą to być pojedyncze punkty awarii, jeśli nie ma dodatkowej weryfikacji. Firma Microsoft obsługuje szeroką gamę opcji uwierzytelniania dostosowanych do potrzeb instytucji finansowych.

Metody *bez hasła* ułatwiają użytkownikom uwierzytelnianie wieloskładnikowe. Chociaż nie wszystkie uwierzytelnianie wieloskładnikowe jest bez hasła, technologie bez hasła wykorzystują uwierzytelnianie wieloskładnikowe. Firma Microsoft, Google i inni liderzy branży opracowali standardy umożliwiające prostsze i silniejsze środowisko uwierzytelniania na urządzeniach internetowych i przenośnych w grupie o nazwie Fast IDentity Online (FIDO). Niedawno opracowana norma FIDO2 umożliwia użytkownikom łatwe i bezpieczne uwierzytelnianie bez konieczności używania hasła w celu wyeliminowania wyłudzania informacji.

Metody uwierzytelniania wieloskładnikowego firmy Microsoft, które są bez hasła, obejmują:
* [Microsoft Authenticator](/azure/active-directory/user-help/user-help-auth-app-overview): W celu zapewnienia elastyczności, wygody i kosztów zalecamy korzystanie z aplikacji mobilnej Microsoft Authenticator. Microsoft Authenticator obsługuje dane biometryczne, powiadomienia wypychane i jednorazowe kody dostępu dla dowolnej aplikacji połączonej z usługą Azure AD. Jest ona dostępna w sklepach z aplikacjami Apple i Android.
*  [Windows Hello](/windows/security/identity-protection/hello-for-business/hello-overview): Aby uzyskać wbudowane środowisko na komputerze, zalecamy używanie Windows Hello. Używa ona informacji biometrycznych (takich jak twarz lub odcisk palca) do automatycznego logowania.  
* [Klucze zabezpieczeń FIDO2](/windows/security/identity-protection/hello-for-business/microsoft-compatible-security-key) są teraz dostępne od kilku partnerów firmy Microsoft: Yubico, Feitian Technologies i HID Global w wskaźniku USB, wskaźniku z obsługą NFC lub kluczu biometrycznym.

[Dostęp warunkowy usługi Azure AD](/azure/active-directory/conditional-access/) zapewnia niezawodne rozwiązanie do automatyzowania decyzji dotyczących kontroli dostępu i wymuszania zasad organizacji w celu ochrony zasobów firmy. Klasycznym przykładem jest to, że planista finansowy chce uzyskać dostęp do aplikacji zawierającej poufne dane klienta. Są one automatycznie wymagane do przeprowadzenia uwierzytelniania wieloskładnikowego w celu uzyskania dostępu do tej aplikacji, a dostęp musi pochodzić z urządzenia zarządzanego przez firmę. Dostęp warunkowy platformy Azure łączy sygnały dotyczące żądania dostępu użytkownika, takie jak właściwości użytkownika, urządzenia, lokalizacji i sieci oraz aplikacji, do których użytkownik próbuje uzyskać dostęp. Dynamicznie ocenia próby uzyskania dostępu do aplikacji w stosunku do skonfigurowanych zasad. Jeśli ryzyko związane z użytkownikiem lub urządzeniem jest podwyższone lub inne warunki nie są spełnione, usługa Azure AD może automatycznie wymuszać zasady, takie jak wymaganie uwierzytelniania wieloskładnikowego, wymaganie bezpiecznego resetowania hasła lub ograniczanie lub blokowanie dostępu. Pomaga to zapewnić ochronę poufnych zasobów organizacyjnych w dynamicznie zmieniających się środowiskach.
 
Usługa Azure AD i powiązane usługi zabezpieczeń Microsoft 365 stanowią podstawę, na której można wdrożyć nowoczesną platformę współpracy w chmurze dla instytucji finansowych, aby można było zabezpieczyć dostęp do danych i aplikacji oraz spełnić obowiązki dotyczące zgodności z regulatorem. Te narzędzia zapewniają następujące kluczowe możliwości:

* Centralnie przechowuj tożsamości użytkowników i zarządzaj nimi.
* Użyj silnego protokołu uwierzytelniania, w tym uwierzytelniania wieloskładnikowego, aby uwierzytelnić użytkowników na żądaniach dostępu i zapewnić spójne i niezawodne środowisko uwierzytelniania we wszystkich aplikacjach.
* Dynamiczne weryfikowanie zasad we wszystkich żądaniach dostępu, dołączanie wielu sygnałów do procesu podejmowania decyzji dotyczących zasad, w tym tożsamości, członkostwa użytkowników/grup, aplikacji, urządzenia, sieci, lokalizacji i oceny ryzyka w czasie rzeczywistym.
* Weryfikowanie szczegółowych zasad na podstawie zachowania użytkownika i właściwości pliku oraz dynamiczne wymuszanie dodatkowych środków zabezpieczeń w razie potrzeby.
* Zidentyfikuj "shadow IT" w organizacji i zezwól zespołom InfoSec na nakładanie sankcji lub blokowanie aplikacji w chmurze.
* Monitorowanie i kontrolowanie dostępu do aplikacji w chmurze firmy Microsoft i innych firm.
* Proaktywna ochrona przed wyłudzaniem informacji za pomocą poczty e-mail i atakami wymuszającym okup.

#### <a name="azure-ad-identity-protection"></a>Ochrona tożsamości w usłudze Azure AD
Chociaż dostęp warunkowy chroni zasoby przed podejrzanymi żądaniami, usługa Identity Protection idzie dalej, zapewniając ciągłe wykrywanie ryzyka i korygowanie podejrzanych kont użytkowników. Usługa Identity Protection informuje o podejrzanym zachowaniu użytkownika i logowania w środowisku przez całą dobę. Jego automatyczna reakcja proaktywnie zapobiega nadużywaniu naruszeń tożsamości.
 
Identity Protection to narzędzie, które umożliwia organizacjom wykonywanie trzech kluczowych zadań:

* Automatyzowanie wykrywania i korygowania zagrożeń opartych na tożsamościach.
* Badanie ryzyka przy użyciu danych w portalu.
* Eksportuj dane wykrywania ryzyka do narzędzi innych firm w celu dalszej analizy.

Usługa Identity Protection korzysta z wiedzy uzyskanej przez firmę Microsoft z jej pozycji w organizacjach z usługą Azure AD, w przestrzeni konsumentów przy użyciu kont Microsoft oraz w grach z konsolą Xbox, aby chronić użytkowników. Firma Microsoft analizuje 65 bilionów sygnałów dziennie, aby identyfikować i chronić klientów przed zagrożeniami. Sygnały generowane przez usługę Identity Protection i przekazywane do niej mogą być dodatkowo przekazywane do narzędzi, takich jak dostęp warunkowy w celu podejmowania decyzji dotyczących dostępu. Mogą one również zostać przekazane z powrotem do narzędzia do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM) w celu dalszego zbadania na podstawie wymuszonych zasad organizacji.

Usługa Identity Protection pomaga organizacjom automatycznie chronić przed naruszeniami tożsamości dzięki wykorzystaniu analizy w chmurze opartej na zaawansowanym wykrywaniu opartym na heurystyce, analizie zachowania użytkowników i jednostek (UEBA) oraz uczeniu maszynowym (ML) w ekosystemie firmy Microsoft.

![Pięciu pracowników pracownicy informacji oglądać jak inny daje prezentację.](../media/win17-15021-00-n9.jpg)
 
## <a name="identify-sensitive-data-and-prevent-data-loss"></a>Identyfikowanie poufnych danych i zapobieganie utracie danych
Microsoft 365 umożliwia wszystkim organizacjom identyfikowanie poufnych danych w organizacji za pomocą kombinacji zaawansowanych możliwości, w tym:

* **Usługa Microsoft Purview Information Protection** zarówno do klasyfikacji opartej na użytkownikach, jak i zautomatyzowanej klasyfikacji danych poufnych.
* **Microsoft Purview Data Loss Prevention (DLP)** do zautomatyzowanej identyfikacji danych poufnych przy użyciu poufnych typów danych (innymi słowy wyrażeń regularnych) oraz słów kluczowych i wymuszania zasad.

**[Usługa Microsoft Purview Information Protection](../compliance/information-protection.md)** umożliwia organizacjom inteligentne klasyfikowanie dokumentów i wiadomości e-mail przy użyciu etykiet poufności. Etykiety poufności mogą być stosowane ręcznie przez użytkowników do dokumentów w aplikacjach Microsoft Office i do wiadomości e-mail w Outlook. Etykiety mogą automatycznie stosować oznaczenia dokumentów, ochronę za pomocą szyfrowania i wymuszanie zarządzania prawami. Etykiety poufności można również stosować automatycznie, konfigurując zasady, które używają słów kluczowych i poufnych typów danych (takich jak numery kart kredytowych, numery ubezpieczenia społecznego i numery tożsamości), aby automatycznie znajdować i klasyfikować dane poufne.

Ponadto firma Microsoft udostępnia "klasyfikatory z możliwością trenowania", które używają modeli uczenia maszynowego do identyfikowania poufnych danych na podstawie zawartości, w przeciwieństwie do po prostu dopasowania wzorca lub elementów w zawartości. Klasyfikator uczy się, jak zidentyfikować typ zawartości, przeglądając wiele przykładów zawartości, która ma zostać sklasyfikowana. Trenowanie klasyfikatora rozpoczyna się od podania przykładów zawartości w określonej kategorii. Po zapoznaniu się z tymi przykładami model jest testowany przez nadanie mu kombinacji zgodnych i niezgodnych przykładów. Klasyfikator przewiduje, czy dany przykład należy do kategorii, czy nie. Następnie osoba potwierdza wyniki, sortując wyniki dodatnie, ujemne, fałszywie dodatnie i fałszywie ujemne, aby zwiększyć dokładność przewidywań klasyfikatora. Po opublikowaniu wytrenowanego klasyfikatora przetwarza zawartość w Microsoft Office SharePoint Online, Exchange Online i OneDrive dla Firm oraz automatycznie klasyfikuje zawartość.

Zastosowanie etykiet poufności do dokumentów i wiadomości e-mail osadza metadane identyfikujące wybraną czułość w obiekcie. Następnie czułość jest przenoszona wraz z danymi. Dlatego nawet jeśli dokument z etykietą jest przechowywany na pulpicie użytkownika lub w systemie lokalnym, nadal jest chroniony. Ta funkcja umożliwia innym rozwiązaniu Microsoft 365, takim jak Microsoft Defender for Cloud Apps lub urządzenia brzegowe sieci, identyfikowanie poufnych danych i automatyczne wymuszanie mechanizmów kontroli zabezpieczeń. Etykiety poufności mają dodatkową korzyść z informowania pracowników o tym, które dane w organizacji są uważane za poufne i jak obsługiwać te dane po ich otrzymaniu.

**[Usługa Microsoft Purview Data Loss Prevention (DLP)](../compliance/dlp-learn-about-dlp.md)** automatycznie identyfikuje dokumenty, wiadomości e-mail i konwersacje zawierające dane poufne, skanując je pod kątem danych poufnych, a następnie wymuszając zasady dotyczące tych obiektów. Zasady są wymuszane w dokumentach w SharePoint i OneDrive dla Firm. Są one również wymuszane, gdy użytkownicy wysyłają wiadomości e-mail oraz w Teams czatach i konwersacjach na kanale. Zasady można skonfigurować do wyszukiwania słów kluczowych, poufnych typów danych, etykiet przechowywania oraz tego, czy dane są udostępniane w organizacji, czy na zewnątrz. Dostępne są mechanizmy kontroli ułatwiające organizacjom dostosowywanie zasad DLP w celu zmniejszenia liczby wyników fałszywie dodatnich. Po znalezieniu poufnych danych można wyświetlić użytkownikom w aplikacjach Microsoft 365 wskazówki dotyczące zasad umożliwiających dostosowanie, aby poinformować ich, że ich zawartość zawiera dane poufne, a następnie zaproponować działania naprawcze. Zasady mogą również uniemożliwiać użytkownikom dostęp do dokumentów, udostępnianie dokumentów lub wysyłanie wiadomości e-mail zawierających określone typy danych poufnych. Microsoft 365 obsługuje ponad 100 wbudowanych poufnych typów danych. Organizacje mogą konfigurować niestandardowe typy danych poufnych w celu spełnienia ich zasad.

Wprowadzenie zasad usługi Microsoft Purview Information Protection i DLP do organizacji wymaga starannego planowania i programu edukacji użytkowników, aby pracownicy zrozumieli schemat klasyfikacji danych organizacji oraz typy danych, które są uważane za wrażliwe. Zapewnienie pracownikom narzędzi i programów edukacyjnych, które pomagają im identyfikować poufne dane i zrozumieć, jak sobie z nimi radzić, czyni je częścią rozwiązania w celu ograniczenia zagrożeń bezpieczeństwa informacji.

Sygnały generowane przez usługę Identity Protection i przekazywane do niej mogą być również przekazywane do narzędzi, takich jak dostęp warunkowy do podejmowania decyzji dotyczących dostępu, lub do narzędzia do zarządzania informacjami i zdarzeniami zabezpieczeń (SIEM) do badania na podstawie wymuszonych zasad organizacji.

Usługa Identity Protection pomaga organizacjom automatycznie chronić przed naruszeniami tożsamości dzięki wykorzystaniu analizy w chmurze opartej na zaawansowanych wykrywaniach opartych na heurystyce, analizie zachowań użytkowników i jednostek oraz uczeniu maszynowym w ekosystemie firmy Microsoft.

![Proces roboczy informacji jest na zdjęciu przed dużą tablicą monitorów.](../media/clo1718-portrait-006.jpg)

## <a name="defend-the-fortress"></a>Bronić twierdzy

Firma Microsoft niedawno uruchomiła rozwiązanie Microsoft 365 Defender, które ma na celu zabezpieczenie nowoczesnej organizacji przed ewoluującym krajobrazem zagrożeń. Dzięki wykorzystaniu inteligentnego Graph zabezpieczeń rozwiązanie Do ochrony przed zagrożeniami oferuje kompleksowe, zintegrowane zabezpieczenia przed wieloma wektorami ataków.

### <a name="the-intelligent-security-graph"></a>[Inteligentny Graph zabezpieczeń](https://www.microsoft.com/security/business/intelligence) 
Usługi zabezpieczeń z Microsoft 365 są obsługiwane przez usługę Intelligent Security Graph. Aby zwalczać cyberoszerość, Graph Intelligent Security używa zaawansowanej analizy do łączenia analizy zagrożeń i sygnałów bezpieczeństwa od firmy Microsoft i jej partnerów. Firma Microsoft obsługuje globalne usługi na ogromną skalę, zbierając biliony sygnałów bezpieczeństwa, które zapewniają ochronę przed energią w stosie. Modele uczenia maszynowego oceniają tę analizę, a szczegółowe informacje o sygnałach i zagrożeniach są szeroko udostępniane w naszych produktach i usługach. Dzięki temu możemy szybko wykrywać zagrożenia i reagować na nie oraz wysyłać klientom alerty i informacje umożliwiające podjęcie działań w celu ich korygowania. Nasze modele uczenia maszynowego są stale wytrenowane i aktualizowane przy użyciu nowych szczegółowych informacji, co pomaga nam tworzyć bezpieczniejsze produkty i zapewniać bardziej proaktywne zabezpieczenia.

[Ochrona usługi Office 365 w usłudze Microsoft Defender](../security/office-365-security/defender-for-office-365.md) udostępnia zintegrowaną usługę Microsoft 365, która chroni organizacje przed złośliwymi linkami i złośliwym oprogramowaniem dostarczanym za pośrednictwem poczty e-mail i dokumentów Office. Jednym z najczęstszych wektorów ataków, który ma obecnie wpływ na użytkowników, są ataki wyłudzające informacje za pomocą poczty e-mail. Te ataki mogą być skierowane do konkretnych użytkowników i mogą być bardzo przekonujące, z pewnym wywołaniem działania, które monituje użytkownika o kliknięcie złośliwego linku lub otwarcie załącznika zawierającego złośliwe oprogramowanie. Po zainfekowaniu komputera osoba atakująca może ukraść poświadczenia użytkownika i przenieść się później w całej organizacji lub eksfiltrować wiadomości e-mail i dane w celu wyszukania poufnych informacji. Ochrona usługi Office 365 w usłudze Defender obsługuje bezpieczne załączniki i bezpieczne linki, oceniając dokumenty i linki po kliknięciu pod kątem potencjalnie złośliwych intencji i blokując dostęp. Załączniki wiadomości e-mail są otwierane w chronionej piaskownicy przed ich dostarczeniem do skrzynki pocztowej użytkownika. Ocenia również linki w dokumentach Office pod kątem złośliwych adresów URL. Ochrona usługi Office 365 w usłudze Defender chroni również linki i pliki w SharePoint Online, OneDrive dla Firm i Teams. Jeśli zostanie wykryty złośliwy plik, Ochrona usługi Office 365 w usłudze Defender automatycznie blokuje ten plik w celu zmniejszenia potencjalnych uszkodzeń.

[Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) jest ujednoliconą platformą zabezpieczeń punktu końcowego do ochrony zapobiegawczej, wykrywania po naruszeniu zabezpieczeń oraz zautomatyzowanego badania i reagowania. Usługa Defender for Endpoint zapewnia wbudowane możliwości odnajdywania i ochrony poufnych danych w punktach końcowych przedsiębiorstwa.

[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) umożliwia organizacjom wymuszanie zasad na poziomie szczegółowym i wykrywanie anomalii behawioralnych na podstawie profilów poszczególnych użytkowników, które są automatycznie definiowane przy użyciu uczenia maszynowego. Defender dla Chmury Zasady aplikacji mogą opierać się na zasadach dostępu warunkowego platformy Azure, aby chronić poufne zasoby firmy, oceniając dodatkowe sygnały związane z zachowaniem użytkowników i właściwościami dokumentów, do których uzyskuje się dostęp. Z biegiem czasu Defender dla Chmury Apps poznaje typowe zachowanie każdego pracownika w odniesieniu do danych, do których uzyskuje dostęp, oraz używanych przez niego aplikacji. Na podstawie wzorców poznanych zachowań zasady mogą następnie automatycznie wymuszać mechanizmy kontroli zabezpieczeń, jeśli pracownik działa poza tym profilem behawioralnym. Jeśli na przykład pracownik zwykle uzyskuje dostęp do aplikacji księgowej od 9:00 do 17:00 od poniedziałku do piątku, ale nagle zaczyna intensywnie uzyskiwać dostęp do tej aplikacji w niedzielę wieczorem, Defender dla Chmury Aplikacje mogą dynamicznie wymuszać zasady, aby wymagać od użytkownika ponownego uwierzytelnienia. Pomaga to zapewnić, że poświadczenia użytkownika nie zostały naruszone. Defender dla Chmury Apps może również pomóc w identyfikacji "w tle IT" w organizacji, co pomaga zespołom ds. zabezpieczeń informacji zapewnić, że pracownicy korzystają z narzędzi objętych sankcjami podczas pracy z danymi poufnymi. Na koniec usługa Defender dla Chmury Apps może chronić poufne dane w dowolnym miejscu w chmurze, nawet poza platformą Microsoft 365. Umożliwia to organizacjom nakładanie sankcji (lub niesankcjonowanie) określonych zewnętrznych aplikacji w chmurze, kontrolowanie dostępu i monitorowanie użycia.
 
[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) to oparte na chmurze rozwiązanie zabezpieczeń, które wykorzystuje sygnały lokalna usługa Active Directory do identyfikowania, wykrywania i badania zaawansowanych zagrożeń, tożsamości z naruszeniem zabezpieczeń i złośliwych akcji wewnętrznych skierowanych do organizacji. Usługa AATP umożliwia analitykom secop i specjalistom ds. zabezpieczeń wykrywanie zaawansowanych ataków w środowiskach hybrydowych w celu:
* Monitorowanie użytkowników, zachowania jednostek i działań przy użyciu analizy opartej na uczeniu się.
* Ochrona tożsamości użytkowników i poświadczeń przechowywanych w usłudze Active Directory.
* Identyfikowanie i badanie podejrzanych działań użytkowników i zaawansowanych ataków w całym łańcuchu zabijania.
* Podaj jasne informacje o zdarzeniach na prostej osi czasu, aby uzyskać szybką klasyfikację.

![Pracownicy biurowi spotykają się w małej sali konferencyjnej. Jeden daje prezentację.](../media/clo1717-corporate-office-021.jpg)
 
## <a name="govern-data-and-manage-records"></a>Zarządzanie danymi i zarządzanie rekordami

Instytucje finansowe muszą przechowywać swoje rejestry i informacje zgodnie ze swoimi zobowiązaniami regulacyjnymi, prawnymi i biznesowymi, zgodnie z ich harmonogramem przechowywania przedsiębiorstw. Na przykład [sec nakazuje okresy przechowywania](https://www.sec.gov/rules/interp/34-47806.htm) od trzech do sześciu lat, w oparciu o typ rekordu, z natychmiastową dostępnością przez pierwsze dwa lata. Organizacje stoją w obliczu ryzyka zgodności z przepisami i prawnymi, jeśli dane są zaniżone (zbyt wcześnie odrzucone), a teraz zarządzają również przepisami, które nakazują usuwanie, gdy informacje nie są już wymagane. Skuteczne strategie zarządzania rekordami podkreślają praktyczne i spójne podejście, dzięki czemu informacje są odpowiednio usuwane przy jednoczesnym zminimalizowaniu kosztów i ryzyka dla organizacji.
 
Ponadto mandaty regulacyjne departamentu usług finansowych stanu Nowy Jork wymagają podmiotów objętych obsługą zasad i procedur usuwania informacji niepublicznych. 23 NYCRR 500, sekcja 500.13, Ograniczenia dotyczące przechowywania danych wymagają, aby "W ramach programu cyberbezpieczeństwa każdy podmiot objęty ochroną bezpieczeństwa powinien zawierać zasady i procedury dotyczące bezpiecznego usuwania na podstawie okresowych informacji niepublicznych określonych w sekcji 500.01(g)(2)-(3) tej części, która nie jest już niezbędna do prowadzenia działalności gospodarczej lub do innych uzasadnionych celów biznesowych podmiotu objętego ochroną,  z wyjątkiem przypadków, gdy takie informacje są w inny sposób wymagane do zachowania przez prawo lub rozporządzenie".
 
Instytucje finansowe zarządzają ogromnymi ilościami danych. Niektóre okresy przechowywania są wyzwalane przez zdarzenia, takie jak wygaśnięcie umowy lub opuszczenie organizacji przez pracownika. W tej atmosferze stosowanie zasad przechowywania rekordów może być trudne. Podejścia do dokładnego przypisywania okresów przechowywania rekordów w dokumentach organizacyjnych mogą się różnić. Niektóre z nich szeroko stosują zasady przechowywania lub korzystają z technik autoklasyfikacji i uczenia maszynowego. Inne identyfikują podejście, które wymaga bardziej szczegółowego procesu, który unikatowo przypisuje okresy przechowywania do poszczególnych dokumentów.

***Microsoft 365 zapewnia elastyczne możliwości definiowania etykiet przechowywania i zasad w celu inteligentnego implementowania wymagań dotyczących zarządzania rekordami.*** Menedżer rekordów definiuje etykietę przechowywania, która reprezentuje "typ rekordu" w tradycyjnym harmonogramie przechowywania. Etykieta przechowywania zawiera ustawienia definiujące następujące szczegóły:

- Jak długo rekord jest zachowywany
- Co się dzieje, gdy okres przechowywania wygaśnie (usuń dokument, rozpocznij przegląd dyspozycji lub nie podejmij żadnych działań)
-  Co wyzwala rozpoczęcie okresu przechowywania (data utworzenia, data ostatniej modyfikacji, data oznaczona etykietą lub zdarzenie) i oznacza dokument lub wiadomość e-mail jako rekord (co oznacza, że nie można go edytować ani usunąć)

Etykiety przechowywania są następnie publikowane w witrynach SharePoint lub OneDrive, Exchange skrzynkach pocztowych i grupach Microsoft 365. Użytkownicy mogą ręcznie stosować etykiety przechowywania do dokumentów i wiadomości e-mail. Menedżerowie rekordów mogą używać analizy do automatycznego stosowania etykiet. Inteligentne możliwości mogą opierać się na [dziewięćdziesiąt plus wbudowane typy informacji poufnych](../compliance/content-search.md) (takich jak numer wyjścia ABA, numer konta bankowego USA lub numer ubezpieczenia społecznego USA). Można je również dostosowywać na podstawie słów kluczowych lub poufnych danych znalezionych w dokumentach lub wiadomościach e-mail, takich jak numery kart kredytowych lub inne dane osobowe lub na podstawie SharePoint metadanych. W przypadku danych, które nie są łatwo identyfikowane za pomocą ręcznego lub zautomatyzowanego dopasowywania wzorców, klasyfikatory z możliwością trenowania mogą służyć do inteligentnego klasyfikowania dokumentów na podstawie technik uczenia maszynowego.
 
**Komisja Papierów Wartościowych i Exchange (SEC)** wymaga, aby broker-dealerzy i inne regulowane instytucje finansowe zachowały wszystkie komunikaty związane z działalnością gospodarczą. Te wymagania dotyczą wielu typów komunikacji i danych, w tym wiadomości e-mail, dokumentów, wiadomości błyskawicznych, faksów i innych. **Reguła SEC 17a-4** definiuje kryteria, które te organizacje muszą spełnić, aby przechowywać rekordy w elektronicznym systemie przechowywania danych. W 2003 r. SEC wydało wydanie, które wyjaśniło te wymagania. Zawierała ona następujące kryteria:

* Dane zachowane przez elektroniczny system magazynowania muszą być nie do ponownego zapisywania i nie można ich wymazywać. Jest to określane jako wymaganie WORM (zapisuj raz, odczytuj wiele).
* System przechowywania musi mieć możliwość przechowywania danych poza okresem przechowywania wymaganym przez regułę, w przypadku wezwania sądowego lub innego porządku prawnego.
* Organizacja nie naruszyłaby wymogu określonego w akapicie (f)(2)(ii)(A) reguły, jeśli korzystała z elektronicznego systemu magazynowania, który uniemożliwia zastępowanie, wymazywanie lub w inny sposób zmienianie rekordu w wymaganym okresie przechowywania za pomocą zintegrowanych kodów kontroli sprzętu i oprogramowania.
* Elektroniczne systemy magazynowania, które jedynie "eliminują" ryzyko zastąpienia lub usunięcia rekordu, na przykład przez poleganie na kontroli dostępu, nie spełniają wymagań reguły.

Aby ułatwić instytucjom finansowym spełnienie wymagań reguły SEC 17a-4, Microsoft 365 zapewnia kombinację możliwości związanych ze sposobem przechowywania danych, konfigurowania zasad i przechowywania danych w ramach usługi. Obejmują one:

* **Przechowywanie danych (reguła 17a-4(a), (b)(4))** — etykiety i zasady przechowywania są elastyczne w celu spełnienia potrzeb organizacji i mogą być automatycznie lub ręcznie stosowane do różnych typów danych, dokumentów i informacji. Obsługiwane są różne typy danych i komunikacja, w tym dokumenty w SharePoint i OneDrive dla Firm, dane w skrzynkach pocztowych Exchange Online i dane w Teams.  
* **Format nienadający się do ponownego zapisywania, niezdatny do wymazywania (reguła 17a-4(f)(2)(ii)(A))** — funkcja blokady zachowania dla zasad przechowywania umożliwia menedżerom rekordów i administratorom konfigurowanie zasad przechowywania w taki sposób, aby nie można było ich już modyfikować. Uniemożliwia to innym osobom usuwanie, wyłączanie lub modyfikowanie zasad przechowywania w jakikolwiek sposób. Oznacza to, że po włączeniu blokady zachowania nie można jej wyłączyć i nie ma metody, za pomocą której wszelkie dane, do których zostały zastosowane zasady przechowywania, mogą zostać zastąpione, zmodyfikowane lub usunięte w okresie przechowywania. Ponadto nie można skrócić okresu przechowywania. Jednak okres przechowywania można wydłużyć, gdy istnieje wymóg prawny, aby kontynuować przechowywanie danych.<br/><br/>Gdy blokada zachowania jest stosowana do zasad przechowywania, następujące akcje są ograniczone:

  - Okres przechowywania zasad można tylko zwiększyć. Nie można go skrócić.
  - Użytkowników można dodać do zasad, ale nie można usunąć istniejących użytkowników skonfigurowanych w zasadach.
   - Zasady przechowywania nie mogą zostać usunięte przez żadnego administratora w organizacji.
 
  Blokada zachowania pomaga zagwarantować, że żaden użytkownik, nawet administratorzy z najwyższym poziomem dostępu uprzywilejowanego, nie może zmieniać ustawień, modyfikować, zastępować ani usuwać przechowywanych danych, zapewniając archiwizowanie w Microsoft 365 zgodnie ze wskazówkami podanymi w wersji SEC 2003.

* **Jakość, dokładność i weryfikacja magazynu/serializacji i indeksowania danych (reguła 17a-4(f)(2) (ii)(B) i (C))** — Office 365 obciążenia zawierają możliwości automatycznego weryfikowania jakości i dokładności procesu rejestrowania danych na nośnikach magazynu. Ponadto dane są przechowywane przez użycie metadanych i znaczników czasu, aby zapewnić wystarczające indeksowanie, aby umożliwić skuteczne wyszukiwanie i pobieranie danych.
 
* **Oddzielny magazyn dla zduplikowanych kopii (reguła 17a-4(f)(3(iii))** — usługa Office 365 w chmurze przechowuje zduplikowane kopie danych jako podstawowy aspekt wysokiej dostępności. Jest to realizowane przez implementację nadmiarowości na wszystkich poziomach usługi, w tym na poziomie fizycznym na wszystkich serwerach, na poziomie serwera w centrum danych i na poziomie usługi dla geograficznie rozproszonych centrów danych.

* **Dane do pobrania i dostępne do pobrania (reguła 17a-4(f)(2)(ii)(D))** — Office 365 ogólnie zezwala na wyszukiwanie i pobieranie danych oznaczonych etykietą przechowywania, uzyskiwanie do nich dostępu i pobieranie. Umożliwia ona wyszukiwanie danych w archiwach Exchange Online przy użyciu wbudowanych funkcji zbierania elektronicznych materiałów dowodowych. Dane można następnie pobrać zgodnie z potrzebami w formatach standardowych, w tym EDRML i PST.
 
* **Wymagania dotyczące inspekcji (reguła 17a-4(f)(3)(v))** — Office 365 zapewnia rejestrowanie inspekcji dla każdej akcji administracyjnej i użytkownika, która modyfikuje obiekty danych, konfiguruje lub modyfikuje zasady przechowywania, przeprowadza wyszukiwania zbierania elektronicznych materiałów dowodowych lub modyfikuje uprawnienia dostępu. Office 365 prowadzi kompleksowy dziennik inspekcji, w tym dane dotyczące tego, kto wykonał akcję, kiedy została wykonana, szczegóły dotyczące akcji i wykonane polecenia. Dziennik inspekcji może być następnie wyprowadzony i uwzględniony w ramach formalnych procesów inspekcji zgodnie z wymaganiami.

Na koniec reguła 17a-4 wymaga od organizacji przechowywania rekordów dla wielu typów transakcji, tak aby były natychmiast dostępne przez dwa lata. Rekordy muszą być dalej przechowywane przez trzy do sześciu lat z dostępem bez natychmiastowego dostępu. Zduplikowane rekordy muszą być również przechowywane przez ten sam okres w lokalizacji poza lokacją. Microsoft 365 możliwości zarządzania rekordami umożliwiają przechowywanie rekordów w taki sposób, że nie można ich modyfikować ani usuwać, ale można do nich łatwo uzyskać dostęp przez okres kontrolowany przez menedżera rekordów. Okresy te mogą obejmować dni, miesiące lub lata, w zależności od obowiązków organizacji w zakresie zgodności z przepisami.
 
Na żądanie firma Microsoft dostarczy zaświadczenie o zgodności z sec 17a-4, jeśli jest to wymagane przez organizację.

Ponadto te możliwości pomagają również Microsoft 365 spełniać wymagania dotyczące magazynowania dla [reguły CFTC 1.31(c)-(d)](https://www.cftc.gov/sites/default/files/opa/press99/opa4266-99-attch.htm) amerykańskiej **Komisji Handlu Kontraktami Terminowymi na towary** i [reguł finra serii 4510](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4511) od **Financial Industry Regulatory Authority.** Łącznie te reguły stanowią najbardziej nakazowe wskazówki na całym świecie dla instytucji finansowych w celu przechowywania dokumentacji.

Dodatkowe szczegóły dotyczące zgodności Microsoft 365 z regułą SEC 17a-4 i innymi przepisami są dostępne na [stronie Ocena Office 365 Exchange Online SEC 17a-4(f) / CFTC 1.31(c)-(d) by Cohasset Associates](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=9fa8349d-a0c9-47d9-93ad-472aa0fa44ec&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers).

## <a name="establish-ethical-walls-with-information-barriers"></a>Ustanawianie etycznych murów z barierami informacyjnymi

Instytucje finansowe mogą podlegać przepisom, które uniemożliwiają pracownikom na określonych stanowiskach wymianę informacji lub współpracę z innymi rolami. Na przykład funkcja FINRA opublikowała reguły 2241(b)(2)(G), 2242(b)(2) (D), (b)(2)(H)(ii) i (b)(2)(H)(iii), które wymagają od członków:

"G) ustanawia bariery informacyjne lub inne zabezpieczenia instytucjonalne w sposób racjonalny w celu zapewnienia, że analitycy badawczi są odizolowani od przeglądu, presji lub nadzoru przez osoby zaangażowane w działalność w zakresie usług bankowości inwestycyjnej lub inne osoby, w tym pracowników ds. sprzedaży i handlu, którzy mogą być stronniczy w ocenie lub nadzorze; " i "(H) ustanawiają bariery informacyjne lub inne środki instytucjonalne racjonalnie zaprojektowane w celu zapewnienia, że analitycy badań zadłużenia są odizolowani od  przegląd, nacisk lub nadzór osób zaangażowanych w: (i) usługi bankowości inwestycyjnej; ii) działalność handlową lub handlową podmiotów zabezpieczeń lub transakcji handlowych; oraz (iii) inne osoby, które mogą być stronnicze w ocenie lub nadzorze;"

Ostatecznie te reguły wymagają od organizacji ustanowienia zasad i wdrożenia barier informacyjnych między rolami zaangażowanymi w usługi bankowe, sprzedaż lub handel z wymiany informacji i komunikacji z analitykami.

[Bariery informacyjne umożliwiają ustanawianie etycznych murów](../compliance/information-barriers.md) w środowisku Office 365, dzięki czemu administratorzy zgodności lub inni autoryzowani administratorzy mogą definiować zasady, które zezwalają na komunikację między grupami użytkowników w Teams lub uniemożliwiają komunikację między nimi. Bariery informacyjne przeprowadzają kontrole określonych akcji, aby zapobiec nieautoryzowanej komunikacji. Bariery informacyjne mogą również ograniczać komunikację w scenariuszach, w których zespoły wewnętrzne pracują nad fuzjami/przejęciami lub poufnymi transakcjami lub pracują z poufnymi informacjami wewnętrznymi, które muszą być mocno ograniczone.

Bariery informacyjne obsługują konwersacje i pliki w Teams. Mogą one zapobiegać następującym typom akcji związanych z komunikacją, aby pomóc w przestrzeganiu przepisów FINRA:

* Wyszukiwanie użytkownika
* Dodawanie członka do zespołu lub dalsze uczestnictwo z innym członkiem w zespole
* Rozpoczynanie lub kontynuowanie sesji czatu
* Rozpoczynanie lub kontynuowanie czatu grupowego
* Zapraszanie kogoś do dołączenia do spotkania
* Udostępnianie ekranu
* Umieść połączenie

## <a name="implement-supervisory-control"></a>Implementowanie kontroli nadzoru

Instytucje finansowe są zwykle zobowiązane do ustanowienia i utrzymania funkcji nadzorczej w swoich organizacjach w celu monitorowania działalności pracowników i ułatwienia jej osiągnięcia zgodności z obowiązującymi przepisami dotyczącymi papierów wartościowych. W szczególności FINRA ustanowiła następujące wymagania dotyczące nadzoru:
 
* [Zasada 3110 FINRA (Nadzór)](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) wymaga od przedsiębiorstw posiadania pisemnych procedur nadzoru w celu nadzorowania działalności swoich pracowników oraz rodzajów przedsiębiorstw, w które się angażuje. Oprócz innych wymagań procedury muszą obejmować:
   - Nadzór nad personelem nadzorczym
   - Przegląd bankowości inwestycyjnej, działalności papierów wartościowych, komunikacji wewnętrznej i dochodzeń wewnętrznych
   - Przegląd transakcji na potrzeby handlu poufnymi informacjami
   - Przegląd korespondencji i skarg

   Procedury muszą opisywać osoby odpowiedzialne za przeglądy, działania nadzorcze wykonywane przez każdą osobę, częstotliwość przeglądania oraz typy dokumentacji lub komunikacji w trakcie przeglądu.
 
* [Zasada 3120 FINRA (System kontroli nadzoru)](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) wymaga od przedsiębiorstw posiadania systemu zasad i procedur kontroli nadzoru, który weryfikuje ich pisemne procedury nadzoru zgodnie z art. Firmy muszą nie tylko dysponować programami WSP, ale także mieć politykę, która co roku testuje te procedury, aby zweryfikować ich zdolność do zapewnienia zgodności z obowiązującymi przepisami i regulacjami dotyczącymi papierów wartościowych. Metodologie i próbkowanie oparte na ryzyku mogą służyć do definiowania zakresu testowania. Między innymi zasada ta wymaga od firm przedstawienia kierownictwu wyższego szczebla rocznego sprawozdania, które zawiera podsumowanie wyników testów oraz wszelkie istotne wyjątki lub zmienione procedury w odpowiedzi na wyniki testów.

![Pracownik biurowy wyświetla wykres i tabele na ekranie, podczas gdy inne osoby spotykają się w tle.](../media/wco18-desk-work-002.jpg)
 
### <a name="communication-compliance"></a>Zgodność w komunikacji

Zgodność z komunikacją umożliwia organizacjom wstępne konfigurowanie zasad w celu przechwytywania komunikacji pracowników w celu monitorowania i przeglądania przez autoryzowanych nadzorców. Zasady zgodności z komunikacją mogą przechwytywać wewnętrzne/zewnętrzne wiadomości e-mail i załączniki, Teams komunikację czatu i kanału oraz Skype dla firm wiadomości i załączniki czatu online. Ponadto zgodność z komunikacją może pozyskiwać komunikację i dane z usług innych firm (takich jak Bloomberg, Thomson Reuters, LinkedIn, Twitter, Facebook, Box i Dropbox).
Kompleksowy charakter komunikacji, który można przechwytywać i przeglądać w organizacji, oraz rozległe warunki, z którymi można skonfigurować zasady, umożliwiają stosowanie zasad zgodności komunikacji, aby pomóc instytucjom finansowym w przestrzeganiu reguły FINRA 3110. Zasady mogą być skonfigurowane do przeglądania komunikacji dla użytkowników indywidualnych lub grup.  Wyznaczonych nadzorców można przypisać na poziomie jednostki lub grupy. Kompleksowe warunki można skonfigurować do przechwytywania komunikacji na podstawie komunikatów przychodzących lub wychodzących, domen, etykiet przechowywania, słów kluczowych lub fraz, słowników słów kluczowych, poufnych typów danych, załączników, rozmiaru wiadomości lub rozmiaru załącznika. Recenzenci otrzymują pulpit nawigacyjny, na którym mogą przeglądać oflagowane komunikaty, wykonywać działania w komunikacji, które mogą naruszać zasady, i oznaczać oflagowane elementy jako rozwiązane. Mogą również przejrzeć wyniki przeglądów i elementów, które zostały wcześniej rozwiązane.
  
Zgodność z komunikacją udostępnia raporty, które umożliwiają inspekcję działań przeglądu zasad na podstawie zasad i recenzenta. Dostępne są raporty umożliwiające sprawdzenie, czy zasady działają zgodnie z definicją zasad nadzoru pisemnego organizacji. Mogą one również służyć do identyfikowania komunikacji wymagającej przeglądu i tych, które nie są zgodne z zasadami firmy. Na koniec wszystkie działania związane z konfigurowaniem zasad i przeglądaniem komunikacji są poddawane inspekcji w Office 365 ujednoliconego dziennika inspekcji. W związku z tym zgodność z komunikatem pomaga również instytucjom finansowym w przestrzeganie reguły FINRA 3120.

Oprócz zgodności z regułami FINRA zgodność z komunikacją umożliwia organizacjom monitorowanie komunikacji pod kątem zgodności z innymi wymaganiami prawnymi, zasadami firmy i standardami etycznymi. Zgodność z komunikacją zapewnia wbudowane klasyfikatory zagrożeń, nękania i wulgaryzmów, które pomagają zmniejszyć liczbę wyników fałszywie dodatnich podczas przeglądania komunikacji, oszczędzając czas recenzentom podczas procesu badania i korygowania. Umożliwia również organizacjom zmniejszenie ryzyka poprzez monitorowanie komunikacji po przejściu wrażliwych zmian, takich jak fuzje i przejęcia lub zmiany kierownictwa.

![Proces roboczy informacji koncentruje się na ekranie.](../media/msc16-slalom-004.jpg)
 
## <a name="protect-against-data-exfiltration-and-insider-risk"></a>Ochrona przed eksfiltracją danych i ryzykiem wewnętrznym

Typowym zagrożeniem dla przedsiębiorstw jest eksfiltracja danych lub działanie wyodrębniania danych z organizacji. To ryzyko może być istotnym problemem dla instytucji finansowych ze względu na poufny charakter informacji, do których można uzyskiwać dostęp z dnia na dzień. Wraz z rosnącą liczbą dostępnych kanałów komunikacyjnych i rozprzestrzenianiem się narzędzi do przenoszenia danych, zaawansowane możliwości są zwykle wymagane w celu ograniczenia ryzyka związanego z wyciekami danych, naruszeniami zasad i ryzykiem wewnętrznym.

### <a name="insider-risk-management"></a>Zarządzanie ryzykiem wewnętrznym

Włączenie pracowników za pomocą narzędzi do współpracy online, do których można uzyskać dostęp w dowolnym miejscu, z natury niesie ze sobą ryzyko dla organizacji. Pracownicy mogą przypadkowo lub złośliwie wyciekać dane do osób atakujących lub konkurentów.  Alternatywnie mogą eksfiltrować dane do użytku osobistego lub pobierać dane z nimi do przyszłego pracodawcy. Scenariusze te stanowią poważne zagrożenie dla instytucji usług finansowych zarówno z punktu widzenia bezpieczeństwa, jak i zgodności. Zidentyfikowanie tych zagrożeń w przypadku ich wystąpienia i ich szybkie ograniczenie wymaga zarówno inteligentnych narzędzi do zbierania danych, jak i współpracy między działami, takimi jak działy prawne, kadrowe i bezpieczeństwo informacji.

Microsoft 365 niedawno uruchomiono rozwiązanie do zarządzania ryzykiem wewnętrznym, które koreluje sygnały w usługach Microsoft 365 i używa modeli uczenia maszynowego do analizowania zachowania użytkowników pod kątem ukrytych wzorców i oznak ryzyka związanego z wewnętrznym dostępem. To narzędzie umożliwia współpracę między operacjami zabezpieczeń, wewnętrznymi badaczami i działem kadr, dzięki czemu mogą łatwo korygować przypadki na podstawie wstępnie określonych przepływów pracy.  

Na przykład zarządzanie ryzykiem wewnętrznym może skorelować sygnały z pulpitu Windows 10 użytkownika, takie jak kopiowanie plików na dysk USB lub wysyłanie wiadomości e-mail do osobistego konta e-mail, z działaniami z Usługi online, takimi jak Office 365 wiadomości e-mail, SharePoint Online, Microsoft Teams lub OneDrive dla Firm, aby zidentyfikować wzorce eksfiltracji danych. Może również skorelować te działania z pracownikami opuszczającym organizację, co jest typowym wzorcem eksfiltracji danych. Może monitorować wiele działań i zachowań w czasie. Gdy pojawiają się typowe wzorce, może ono zgłaszać alerty i pomagać badaczom skupić się na kluczowych działaniach w celu zweryfikowania naruszenia zasad z wysokim stopniem zaufania. Zarządzanie ryzykiem wewnętrznym może pseudo-anonimizować dane od badaczy, aby pomóc w spełnieniu przepisów dotyczących prywatności danych, przy jednoczesnym zachowaniu kluczowych działań, które pomagają im skutecznie przeprowadzić badania. Umożliwia ona badaczom pakowanie i bezpieczne wysyłanie kluczowych danych dotyczących działań do działów kadr i prawnych, zgodnie z typowymi przepływami pracy eskalacji w celu zgłaszania spraw dotyczących działań naprawczych.

Zarządzanie ryzykiem wewnętrznym znacznie zwiększa możliwości organizacji w zakresie monitorowania i badania ryzyka związanego z wewnętrznymi informacjami, jednocześnie umożliwiając organizacjom zachowanie zgodności z przepisami dotyczącymi prywatności danych i podążanie ustalonymi ścieżkami eskalacji, gdy przypadki wymagają działania wyższego poziomu. Aby uzyskać więcej informacji na temat zarządzania ryzykiem wewnętrznym, zobacz [Nowoczesne punkty bólu ryzyka i Przepływ pracy w zarządzaniu ryzykiem wewnętrznym](../compliance/insider-risk-management.md).

![Proces roboczy call center w kabinie typów podczas wyświetlania ekranu.](../media/clo17-call-center-006.jpg)

### <a name="tenant-restrictions"></a>Ograniczenia dzierżawy

Organizacje, które zajmują się danymi poufnymi i kładą ścisły nacisk na zabezpieczenia, zazwyczaj chcą kontrolować zasoby online, do których użytkownicy mogą uzyskiwać dostęp. Jednocześnie chcą włączyć bezpieczną współpracę za pośrednictwem Usługi online, takich jak Office 365. W związku z tym kontrolowanie środowisk Office 365, do których użytkownicy mogą uzyskiwać dostęp, staje się wyzwaniem, ponieważ środowiska Office 365 niezarejestrowanych mogą służyć do eksfiltrowania danych z urządzeń firmowych złośliwie lub nieumyślnie. Tradycyjnie organizacje ograniczają domeny lub adresy IP, do których użytkownicy mogą uzyskiwać dostęp z urządzeń firmowych. Nie działa to jednak w świecie chmury, w którym użytkownicy muszą legalnie uzyskiwać dostęp do usług Office 365.

Microsoft 365 zapewnia [ograniczenia dzierżawy](/azure/active-directory/manage-apps/tenant-restrictions) możliwość rozwiązania tego problemu. Ograniczenia dzierżawy można skonfigurować tak, aby ograniczały dostęp pracowników do zewnętrznych Office 365 dzierżaw przedsiębiorstwa przy użyciu nieautoryzowanych tożsamości (tożsamości, które nie są częścią katalogu firmowego). Obecnie ograniczenia dzierżawy mają zastosowanie w całej dzierżawie, umożliwiając dostęp tylko do tych dzierżaw, które są wyświetlane na skonfigurowanej liście. Firma Microsoft nadal opracowuje to rozwiązanie, aby zwiększyć stopień szczegółowości kontroli i zwiększyć zapewnianą przez nią ochronę.

![GRAFICZNY.](../media/clo1717-corporate-office-001.jpg)

## <a name="conclusion"></a>Wniosku

Microsoft 365 i Teams zapewniają zintegrowane i kompleksowe rozwiązanie dla firm świadczących usługi finansowe, zapewniając proste, ale zaawansowane funkcje współpracy i komunikacji opartej na chmurze w całym przedsiębiorstwie. Korzystając z technologii zabezpieczeń i zgodności z Microsoft 365, instytucje mogą działać w sposób bezpieczniejszy i zgodny z niezawodnymi mechanizmami kontroli zabezpieczeń, aby chronić dane, tożsamości, urządzenia i aplikacje przed różnymi zagrożeniami operacyjnymi, w tym cyberbezpieczeństwem i zagrożeniami wewnętrznymi. Microsoft 365 zapewnia zasadniczo bezpieczną platformę, na której organizacje usług finansowych mogą osiągnąć więcej, jednocześnie chroniąc swoją firmę, pracowników i klientów.
