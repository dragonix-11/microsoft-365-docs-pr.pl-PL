---
title: Najważniejsze zagadnienia dotyczące zgodności z przepisami i zabezpieczeń na rynkach bankowych i giełdowych w Usa
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
description: Dowiedz się, jak instytucje usług finansowych mogą utrzymać zgodność z zabezpieczeniami finansowymi i wydajnie współpracować przy Microsoft 365 i Teams.
f1.keywords: NOCSH
ms.openlocfilehash: e94ad0e1f7b6f0c8b76f40b6492f69b23655855c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014716"
---
# <a name="key-compliance-and-security-considerations-for-us-banking-and-capital-markets"></a>Najważniejsze zagadnienia dotyczące zgodności z przepisami i zabezpieczeń na rynkach bankowych i giełdowych w Usa

## <a name="introduction"></a>Wprowadzenie
Instytucje usług finansowych przewyższa niemal wszystkie komercyjne firmy, których żądają rygorystycznych kontroli zabezpieczeń, zgodności i zarządzania. Ochrona danych, tożsamości, urządzeń i aplikacji jest nie tylko krytyczna dla jej działalności, ale podlega ona wymagań i wytycznych dotyczących zgodności z przepisami, takich jak Amerykańskie Organizacje Papierów Wartościowych i Exchange Commission (SEC), Financial Industry Regulatory Authority (FINRA), Federal Financial Institutions111na (FFIEC) i Cftc (Cftc). Ponadto instytucje finansowe podlegają ustawom takim jak Dodd-Frank i Sarbanes-Oxley 2002.

W dzisiejszych czasach coraz większe obawy dotyczące bezpieczeństwa, ryzyka niejawnego programu testów i naruszenia danych publicznych klienci wymagają również od swoich instytucji finansowych wysokiego poziomu zabezpieczeń, aby ufać im za pomocą danych osobistych i środków bankowych.

W przeszłości konieczność kompleksowej kontroli bezpośrednio wywłasz umożliwiającej współpracę wewnętrznie i zewnętrznie oraz mająca wpływ na systemy informatyczne i platformy, z których korzystają instytucje finansowe. Obecnie pracownicy usług finansowych potrzebują nowoczesnej platformy współpracy, łatwej w użyciu i łatwej w obsłudze. Usługi finansowe nie mogą jednak zapewniać elastyczności w zakresie współpracy między użytkownikami, zespołami i działami za pomocą kontroli zabezpieczeń i zgodności, które wymuszają zasady ochrony użytkowników i systemów informatycznych przed zagrożeniami.

W przypadku sektora usług finansowych w przypadku konfigurowania i wdrażania narzędzi do współpracy i kontroli zabezpieczeń należy zachować ostrożność, w tym:
- Ocena ryzyka w przypadku typowych scenariuszy współpracy w organizacji i procesów biznesowych
- Wymagania dotyczące ochrony informacji i zarządzania danymi
- Bezpieczeństwo i zagrożenia niejawnego programu testów
- Wymagania dotyczące zgodności z przepisami
- Inne zagrożenia operacyjne

**Microsoft 365 to nowoczesne środowisko w chmurze w miejscu pracy, które może stawić o sobie uwagę na współczesne wyzwania związane z usługami finansowymi, przed którymi stoi organizacje. Bezpieczna i elastyczna współpraca na całym przedsiębiorstwie jest połączona z mechanizmami kontroli i egzekwowaniem zasad, zgodnie z rygorystycznymi wytycznymi dotyczącymi zgodności z przepisami.** W tym artykule opisano, jak platforma Microsoft 365 ułatwia przechodzenie usług finansowych na nowoczesną platformę współpracy, pomagając jednocześnie zapewnić bezpieczeństwo danych i systemów oraz zgodność z przepisami:

* Umożliwienie organizacji i pracownikom produktywności za pomocą Microsoft 365 i Microsoft Teams
* Chroń nowoczesną współpracę za pomocą Microsoft 365 
* Identyfikowanie danych poufnych i zapobieganie utracie danych
* Obrona fortecy
* Skuteczne zarządzanie rekordami w celu przestrzegania danych i przestrzegania przepisów
* Omyłowe ściany można osłaniać barierami informacyjnymi
* Ochrona przed wykrzykniem danych i ryzykiem w niejawnym programie testów

Jako partner firmy Microsoft protiviti współtwoował ten artykuł i przekazał istotne opinie na jego temat.

Poniższe ilustracje uzupełniające ten artykuł można pobrać. Bank Woodgrove i firma Contoso ilustrują sposób zastosowania funkcji opisanych w tym artykule w celu rozwiązania typowych wymogów prawnych dotyczących usług finansowych. Zachęcamy do dostosowywania tych ilustracji do własnego użytku. 

**Microsoft 365 dotyczące ochrony informacji i zgodności z przepisami**

| Element | Opis |
|:-----|:-----|
|[![Plakat modelu: Microsoft 365 funkcji ochrony informacji i zgodności.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/>Angielski: [Pobierz jako plik PDF](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| [Pobierz jako plik Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japoński: [Pobierz jako plik PDF](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)\| [Pobierz jako plik Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)  <br/> Zaktualizowano w listopadzie 2020 r.|Zawiera: <ul><li>  ochrona informacji firmy Microsoft i ochrona przed utratą danych</li><li>Zasady przechowywania i etykiety przechowywania </li><li>Bariery informacyjne</li><li>Zgodność komunikacji</li><li>Ryzyko niejawnego programu testów</li><li>Ingestion danych innych firm</li>|


## <a name="empower-organizational-and-employee-productivity-by-using-microsoft-365-and-teams"></a>Zwiększanie produktywności organizacji i pracowników za pomocą Microsoft 365 i Teams

Współpraca zazwyczaj wymaga różnych form komunikacji, możliwości przechowywania dokumentów i danych oraz uzyskiwania do nich dostępu oraz integracji innych aplikacji zgodnie z potrzebami. Pracownicy usług finansowych zazwyczaj muszą współpracować i komunikować się z członkami innych działów lub zespołów, a czasem z jednostkami zewnętrznymi. Dlatego korzystanie z systemów, które tworzą silosy lub utrudnia udostępnianie informacji, jest utrudnione. Zamiast tego lepiej jest korzystać z platform i aplikacji, które umożliwiają pracownikom bezpieczne komunikowanie się, współpracę i udostępnianie informacji zgodnie z zasadami firmy.

Udostępnienie pracownikom nowoczesnej platformy współpracy opartej na chmurze umożliwia im wybieranie i integrowanie narzędzi, które zwiększą ich produktywność, oraz umożliwia im znajdowanie metod adaptacyjnych pracy. Korzystanie Teams w połączeniu z mechanizmami kontroli zabezpieczeń i zasadami zarządzania informacjami, które chronią organizację, może ułatwić pracownikom komunikowanie się i efektywną współpracę.

Teams centrum współpracy dla organizacji. Pomaga ona zjednać ludzi w wydajną pracę nad wspólnymi inicjatywami i projektami. Teams umożliwia członkom zespołu prowadzenie konwersacji 1:1 i wielosektowych czatów, współpracę i współtworzenie dokumentów oraz przechowywanie i udostępnianie plików. Teams także spotkania online za pośrednictwem zintegrowanego systemu komunikacji głosowej i wideo w przedsiębiorstwie. Teams można również dostosowywać za pomocą aplikacji firmy Microsoft, takich jak Microsoft Planner, Microsoft Dynamics 365, Power Apps, Power BI i aplikacji biznesowych innych firm. Teams jest przeznaczony zarówno dla wewnętrznych członków zespołu, jak i dozwolonych użytkowników zewnętrznych, którzy mogą dołączać do kanałów zespołu, uczestniczyć w konwersacjach na czacie, uzyskać dostęp do przechowywanych plików i korzystać z innych aplikacji

Każdy zespół Microsoft Team jest Microsoft 365 grupy. Ta grupa jest uznawana za usługę członkostwa dla wielu Office 365 usług, w tym Teams. Microsoft 365 służą do bezpiecznego rozróżniania "właścicieli" i "członków" oraz do kontrolowania dostępu do różnych funkcji w ramach Teams. W połączeniu z odpowiednimi mechanizmami kontroli zarządzania i regularnie administrowały przeglądami dostępu, Teams tylko członkowie i właściciele mogą korzystać z autoryzowanych kanałów i możliwości.

Częstym scenariuszem, Teams świadczeń finansowych jest prowadzenie wewnętrznych projektów lub programów. Na przykład wiele instytucji finansowych, w tym banków, banków, firm zarządzających majątkami, banków kredytowych i dostawców ubezpieczeniowych, jest wymaganych do zapewnienia ochrony przed pieniędzmi i innych programów do zapewnienia zgodności z przepisami. Od zespołu wewnętrznego składa się firma IT, firmy, takie jak sprzedaż detaliczna i zarządzanie majątkami oraz jednostka przestępcza, może być wymagane udostępnianie między sobą danych i komunikowanie się na temat programu lub określonych badań. Zazwyczaj te programy używały współużytkacyjnych dysków sieciowych, ale takie podejście może dzielić wiele wyzwań, między innymi:
* Tylko jedna osoba może edytować dokument na raz.
* Zarządzanie zabezpieczeniami jest czasochłonne, ponieważ dodawanie/usuwanie osób zazwyczaj obejmuje infrastrukturę IT.
* Dane pozostają w zamieszkania na współużytkowanych dyskach sieciowych znacznie dłużej niż jest to wymagane lub wymagane.

Teams udostępnić obszar współpracy do bezpiecznego przechowywania poufnych danych klienta i prowadzenia konwersacji między członkami zespołu, w których mogą być omawiane poufne tematy. Wielu członków zespołu może jednocześnie edytować jeden dokument lub współpracować nad jednym dokumentem. Właściciel lub schowek programu można skonfigurować jako właściciela zespołu, a następnie, w razie potrzeby, może dodawać i usuwać członków.

Innym najczęstszym scenariuszem jest używanie Teams jako "wirtualnego pokoju danych" do bezpiecznej współpracy, w tym przechowywania dokumentów i zarządzania nimi. Członkowie zespołu i syndicates w ramach banku inwestycji, zarządzania aktywami lub prywatnych firm kapitału mogą bezpiecznie współpracować nad transakcjami lub inwestycjami. Zespoły współfunkcjonalne często biorą udział w planowaniu i realizacji takich transakcji, a możliwość bezpiecznego udostępniania danych i prowadzenia konwersacji to podstawowe wymaganie. Bezpieczne udostępnianie powiązanych dokumentów inwestorzom zewnętrznym jest również kluczowym wymaganiem. Teams udostępnia bezpieczną i w pełni możliwości inspekcji lokalizację, z której można centralnie przechowywać, chronić i udostępniać dane inwestycji.

![Grupa pracowników biurowych na spotkaniu dyskutuje o obrazach w dużej sprawie.](../media/m365cO19-ent-dell-latitude13-5951.jpg)
 
### <a name="teams-improve-collaboration-and-reduce-compliance-risk"></a>Teams: Usprawnij współpracę i zmniejsz ryzyko związane ze zgodnością

Microsoft 365 udostępnia inne typowe funkcje zasad dotyczące Teams dzięki użyciu grup Microsoft 365 jako podstawowej usługi członkostwa. Te zasady mogą ułatwić współpracę i spełniać wymagania dotyczące zgodności.

**Microsoft 365 nazewnictwa grup** pomagają zagwarantować, że Microsoft 365 grupy, a zatem zespoły, są nazwane zgodnie z zasadami firmy. Nazwy mogą być problematyczne, jeśli nie są odpowiednie. Na przykład pracownicy mogą nie wiedzieć, z którymi zespołami pracować lub którym mają udostępniać informacje, jeśli imiona i nazwiska nie zostały odpowiednio zastosowane. Zasady nazewnictwa grup (w tym obsługa zasad opartych na prefiksach/sufiksach i niestandardowych blokowanych wyrazów) mogą wymuszać dobre "zablokowanie" i zapobiegać używaniu określonych wyrazów, takich jak słowa zastrzeżone lub nieodpowiednia terminologia.
  
**Microsoft 365** wygasania grup pomagają zagwarantować, Microsoft 365 grupy, a zatem zespoły nie są zachowywane przez dłuższy czas niż organizacja chce lub potrzebuje. Funkcja ta pomaga zapobiec dwu kluczowym problemom z zarządzaniem informacjami:

* Zespołów, które nie są potrzebne lub używane.
* Przechowanie danych, które nie są już wymagane ani nie są używane przez organizację (z wyjątkiem sytuacji, gdy są wstrzymane/zachowywane ze względu na przepisy prawne).

Administratorzy mogą określić okres wygasania grup Microsoft 365, na przykład 90, 180 lub 365 dni. Jeśli usługa, która jest Microsoft 365 przez grupę użytkowników, jest nieaktywna przez okres wygaśnięcia, właściciele grupy są o tym powiadomieni. Jeśli nie zostanie wykonane żadne działanie, grupa Microsoft 365 i wszystkie powiązane z nią usługi, w tym Teams, zostaną usunięte.
  
Over-retention of data that's stored in Teams other group-based services can risks to financial services organizations. Microsoft 365 wygasania grup są zalecanym sposobem zapobiegania przechowywania danych, które nie są już potrzebne. W połączeniu z wbudowanymi etykietami przechowywania i zasadami firma Microsoft 365 pomaga zagwarantować, że organizacje zachowują tylko dane, które są wymagane do spełnienia firmowych zasad i obowiązków związanych ze zgodnością z przepisami.

#### <a name="teams-integrate-custom-requirements-with-ease"></a>Teams: Łatwo zintegruj wymagania niestandardowe

Teams umożliwia samodzielne tworzenie zespołów. Jednak wiele organizacji uregulowanych w prawach chce kontrolować i zrozumieć, które kanały współpracy są obecnie wykorzystywane przez ich pracowników, które kanały mogą zawierać poufne dane i własność kanałów organizacyjnych. W celu ułatwienia tych kontroli zarządzania Microsoft 365 organizacji wyłączenie samoobsługowego tworzenia zespołów. Korzystając z narzędzi do automatyzacji procesów biznesowych, takich jak microsoft Power Apps i Power Automate, organizacje mogą tworzyć i wdrażać proste formularze i procesy zatwierdzania dla pracowników, aby zażądać utworzenia nowego zespołu. Po zatwierdzeniu zespół może być automatycznie zapewniany za pomocą łącza wysyłanego do żądacego. W ten sposób organizacje mogą projektować i integrować swoje mechanizmy kontroli zgodności oraz wymagania niestandardowe z procesem tworzenia procesów zespołowych.
 
### <a name="acceptable-digital-communication-channels"></a>Dopuszczalne kanały komunikacji cyfrowej

Firma FINRA podkreśla, że komunikacja cyfrowa firm prawnych spełnia wymagania dotyczące przechowywania dokumentacji określone w regułach [programu Exchange Act 17a-3 i 17a-4, a także w regułach FINRA series 4510](https://www.finra.org/rules-guidance/key-topics/books-records). Organizacja FINRA wydaje raport roczny, który zawiera najważniejsze wnioski, spostrzeżenia i skuteczne rozwiązania, aby pomóc organizacjom w usprawnieniu zarządzania zgodnością i ryzykiem. W raporcie [z 2019](https://www.finra.org/rules-guidance/guidance/reports/2019-report-exam-findings-and-observations) r. na temat wyników wyszukiwania i spostrzeżeń firma FINRA zidentyfikuje komunikację cyfrową jako kluczowy obszar, w którym firmy napotykają wyzwania związane z nadzorem i przechowywaniem dokumentacji.

Jeśli organizacja zezwala jej pracownikom na korzystanie z określonej aplikacji, takiej jak oparta na aplikacjach usługa obsługi wiadomości lub platforma do współpracy, firma musi archiwizować rekordy biznesowe i nadzór nad działaniami i komunikacją tych pracowników w tej aplikacji. Organizacje są odpowiedzialne za przeprowadzanie należnej procedury w celu zachowania zgodności z regułami i prawami papierów wartościowych FINRA oraz za przestrzeganie potencjalnych naruszeń tych reguł w związku z korzystaniem przez pracowników z takich aplikacji.
  
Skuteczne rozwiązania zalecane przez usługę FINRA obejmują:
* Ustanawianie kompleksowego programu zarządzania kanałami komunikacji cyfrowej. Zarządzaj decyzjami organizacji, jakie kanały komunikacji cyfrowej są dozwolone, i definiuj procesy zgodności dla każdego kanału cyfrowego. Należy dokładnie monitorować szybko zmieniający się obszar kanałów komunikacji cyfrowej i na bieżąco śledzić procesy zgodności.
* Wyraźnie zdefiniuj i kontroluj kanały cyfrowe. Zdefiniuj zarówno zatwierdzone, jak i zabronione kanały cyfrowe. Blokowanie lub ograniczanie korzystania z zabronionych kanałów cyfrowych lub zabronionych funkcji w kanałach cyfrowych, które ograniczają organizacji możliwość zachowania zgodności z wymaganiami nadzorczymi i zarządzania rekordami.
* Zapewnij szkolenia dotyczące komunikacji cyfrowej. Przed udzieleniem zarejestrowanym przedstawicielom dostępu do zatwierdzonych kanałów cyfrowych należy wdrożyć obowiązkowe programy szkoleniowe. Szkolenie pomaga w sprecyzowaniu oczekiwań organizacji w zakresie biznesowej i osobistej komunikacji cyfrowej, a także prowadzi pracowników przez stosowanie dozwolonych funkcji każdego kanału w sposób zgodny.

Ustalenia i spostrzeżenia f finra dotyczące komunikacji cyfrowej odnoszą się bezpośrednio do możliwości organizacji zachowania zgodności z regułą [SEC 17a-4](https://www.law.cornell.edu/cfr/text/17/240.17a-4) w celu zachowania całej komunikacji związanej z firmą, reguł FINRA [3110](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) i [3120](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) pod nadzorem i przeglądem komunikacji oraz serii [4510](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4510) do zachowania dokumentacji. Komisja Notacji Handlowej Futures (CFTC) ogłasza podobne wymagania zgodnie z artykułem 17 CFR 131. Te przepisy szczegółowo omówiono w dalszej części tego artykułu.

***Teams wraz z kompleksowym pakietem ofert zabezpieczeń i zgodności usługi Microsoft 365 zapewnia firmowy kanał komunikacji cyfrowej dla instytucji usług finansowych do efektywnego prowadzenia działalności i przestrzegania przepisów.*** W dalszej części tego artykułu opisano, Microsoft 365 wbudowane funkcje zarządzania rekordami, ochrony informacji, barier informacyjnych i kontroli nadzorczych Teams rozbudowane narzędzia służące do spełniania tych zobowiązań prawnych.

## <a name="protect-modern-collaboration-with-microsoft-365"></a>Chroń nowoczesną współpracę za pomocą Microsoft 365

### <a name="secure-user-identities-and-control-access"></a>Zabezpieczanie tożsamości użytkowników i kontrolowanie dostępu

***Ochrona dostępu do informacji o klientach, dokumentach finansowych i aplikacjach zaczyna się od zdecydowanie zabezpieczania tożsamości użytkowników.*** Wymaga to bezpiecznej platformy dla przedsiębiorstwa do przechowywania tożsamości i zarządzania nimi, zapewnienia zaufanych sposobów uwierzytelniania i dynamicznego kontrolowania dostępu do tych aplikacji.

Gdy pracownicy pracują, mogą przechodzić z aplikacji do aplikacji lub między wieloma lokalizacjami i urządzeniami. Dostęp do danych musi zostać uwierzytelniony na każdym etapie. Proces uwierzytelniania musi obsługiwać silny protokół i wiele czynników uwierzytelniania (takich jak kod SMS-ów, aplikacja uwierzytelniania i certyfikat) w celu zagwarantowania, że tożsamości nie będą naruszone. Wymuszanie zasad dostępu opartych na czynnikach ryzyka ma kluczowe znaczenie dla ochrony danych finansowych i aplikacji przed zagrożeniami niejawnego programu testów, niezamierzonymi wyciekami danych i eksygymzacją danych.

Microsoft 365 udostępnia platformę bezpiecznej tożsamości w usłudze [Azure Active Directory (Azure AD),](/azure/active-directory/) gdzie tożsamości są przechowywane centralnie i bezpiecznie zarządzane. Usługa Azure AD wraz z hostem powiązanych Microsoft 365 zabezpieczeń stanowi podstawę zapewniania pracownikom dostępu potrzebnego do bezpiecznej pracy oraz ochrony organizacji przed zagrożeniami.

[Uwierzytelnianie wieloskładnikowe (MFA) usługi Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) jest wbudowane na platformie i zapewnia dodatkowy dowód uwierzytelniania, aby ułatwić potwierdzanie tożsamości użytkownika podczas uzyskiwania dostępu do poufnych danych finansowych i aplikacji. Uwierzytelnianie wieloskładnikowe Azure wymaga co najmniej dwóch formularzy uwierzytelniania, takich jak hasło oraz znane urządzenie przenośne. Obsługuje on kilka opcji uwierzytelniania drugiego czynnika, takich jak:

- Aplikacja Microsoft Authenticator aplikacji
- A one-time passcode delivered via SMS
- Połączenie telefoniczne, w którym użytkownik musi wprowadzić numer PIN

Jeśli hasło jest w jakiś sposób naruszone, potencjalny haker nadal potrzebuje telefonu użytkownika, aby uzyskać dostęp do danych organizacyjnych. Ponadto usługa Microsoft 365 używa nowoczesnego uwierzytelniania jako kluczowego protokołu, który zapewnia takie same silne i rozbudowane środowisko uwierzytelniania od przeglądarek internetowych do narzędzi do współpracy, z których pracownicy korzystają codziennie, w tym usługi Microsoft Outlook i innych aplikacji pakietu Microsoft Office.

#### <a name="passwordless"></a>Bez hasła

Hasła są najmniejszym linkiem w łańcuchu zabezpieczeń. Jeśli nie będzie dodatkowej weryfikacji, mogą one stanowić pojedynczy punkt błędu. Firma Microsoft obsługuje szeroki zakres opcji uwierzytelniania dopasowanych do potrzeb instytucji finansowych.

*Metody bez* haseł ułatwiają użytkownikom uwierzytelniania wieloskładnikowego. Mimo że nie wszystkie uwierzytelnianie wieloskładnikowe jest bez haseł, technologie bez haseł stosuje uwierzytelnianie wieloskładnikowe. Firma Microsoft, firma Google i inni liderzy branży opracowali standardy, aby umożliwić prostsze i silniejsze środowisko uwierzytelniania na stronach internetowych i urządzeniach przenośnych w grupie o nazwie Fast IDentity Online (FIDO). Niedawno opracowany standard FIDO2 umożliwia użytkownikom łatwe i bezpieczne uwierzytelnianie bez konieczności użycia hasła w celu wyeliminowania prób wyłudzania informacji.

Metody uwierzytelniania wieloskładnikowego Microsoft, które nie mają hasła, obejmują:
* [Microsoft Authenticator](/azure/active-directory/user-help/user-help-auth-app-overview): Aby zapewnić elastyczność, wygodę i koszt, zalecamy korzystanie Microsoft Authenticator mobilnej. Microsoft Authenticator biometryczne, powiadomienia wypychane i kod dostępu w dowolnej aplikacji połączonej z usługą Azure AD. Jest dostępna w sklepach z aplikacjami firmy Apple i dla systemu Android.
*  [Windows Hello](/windows/security/identity-protection/hello-for-business/hello-overview): Aby korzystać z wbudowanych funkcji na komputerze, zalecamy używanie programu Windows Hello. Używa informacji biometrycznych (takich jak twarz lub linie papilarne) do automatycznego logowania się.  
* Klucze [zabezpieczeń FIDO2](/windows/security/identity-protection/hello-for-business/microsoft-compatible-security-key) są teraz dostępne od kilku partnerów firmy Microsoft: Yubico, Feibic Technologies i HID Global w interfejsie USB, znaczek z obsługą interfejsu NFC lub klucz biometryczny.

[Dostęp warunkowy usługi Azure AD](/azure/active-directory/conditional-access/) oferuje zaawansowane rozwiązanie do automatyzowania decyzji dotyczących kontroli dostępu i wymuszania zasad organizacji w celu ochrony zasobów firmy. Klasycznym przykładem jest uzyskanie dostępu do aplikacji, która ma poufne dane klienta, przez terminarz finansowy. Są one automatycznie wymagane do przeprowadzenia uwierzytelniania wieloskładnikowego w celu uzyskania dostępu do aplikacji, a dostęp musi pochodzić z urządzenia zarządzanego w przedsiębiorstwie. Dostęp warunkowy Azure łączy sygnały dotyczące żądania dostępu użytkownika, takie jak właściwości użytkownika, urządzenia, lokalizacji i sieci oraz aplikacja, do których użytkownik próbuje uzyskać dostęp. Dynamicznie ocenia on próby dostępu do aplikacji pod względem skonfigurowanych zasad. Jeśli poziom ryzyka użytkownika lub urządzenia jest podwyższony lub nie są spełnione inne warunki, usługa Azure AD może automatycznie wymuszać zasady, takie jak wymaganie uwierzytelniania wieloskładnikowego, wymaganie bezpiecznego resetowania hasła albo ograniczanie lub blokowanie dostępu. Dzięki temu poufne zasoby organizacji są chronione w dynamicznie zmieniających się środowiskach.
 
Usługa Azure AD i powiązane z nimi usługi zabezpieczeń Microsoft 365 stanowią podstawę tego, na podstawie której można udostępnić nowoczesną platformę współpracy w chmurze dla instytucji finansowych, co umożliwia zabezpieczanie dostępu do danych i aplikacji oraz spełnianie zobowiązań w zakresie zgodności z przepisami w ramach systemu wiad. Te narzędzia zapewniają następujące kluczowe funkcje:

* Scentralicznie przechowuj tożsamości użytkowników i bezpiecznie zarządzaj nimi.
* Użyj silnego protokołu uwierzytelniania, w tym uwierzytelniania wieloskładnikowego, aby uwierzytelnić użytkowników w żądaniach dostępu oraz zapewnić spójne i niezawodne środowisko uwierzytelniania we wszystkich aplikacjach.
* Dynamiczne weryfikowanie zasad we wszystkich żądaniach dostępu, uwzględniając wiele sygnałów w procesie decyzyjnym zasad, w tym tożsamość, członkostwo użytkownika/grupy, aplikacja, urządzenie, sieć, lokalizacja i wynik ryzyka w czasie rzeczywistym.
* Weryfikuj szczegółowe zasady na podstawie zachowania użytkownika i właściwości pliku oraz dynamicznie wymuszaj dodatkowe miary zabezpieczeń, jeśli jest to wymagane.
* Zidentyfikuj "cień IT" w organizacji i zezwalaj zespołom InfoSec na zablokowanie lub zablokowanie aplikacji w chmurze.
* Monitoruj i kontroluj dostęp do aplikacji firmy Microsoft oraz aplikacji w chmurze innych niż firmy Microsoft.
* Aktywnie chroń przed wyłudzaniem informacji e-mail i atakami oprogramowania wymuszającego okup.

#### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection
Chociaż dostęp warunkowy chroni zasoby przed podejrzanymi żądaniami, ochrona tożsamości zapewnia dalsze działania, zapewniając wykrywanie i korygowanie bieżących problemów z podejrzanymi kontami użytkowników. Ochrona tożsamości zapewnia Ci informacje o podejrzanych działaniach użytkowników i logowania w Twoim środowisku przez całą dobę. Jej automatyczna odpowiedź aktywnie zapobiega nadużyciom tożsamości, które podszyły się pod nie.
 
Ochrona tożsamości to narzędzie, które umożliwia organizacjom wykonywanie trzech kluczowych zadań:

* Automatyzowanie wykrywania i korygowania zagrożeń opartych na tożsamości.
* Zbadaj zagrożenia przy użyciu danych w portalu.
* Dane wykrywania ryzyka można wyeksportować do narzędzi innych firm w celu dalszej analizy.

Identity Protection korzysta z wiedzy, która została nabyta przez firmę Microsoft po witrynie firmy Microsoft w organizacjach korzystających z usługi Azure AD, w przestrzeni dla klientów indywidualnych z kontami Microsoft oraz w grach w konsoli Xbox w celu ochrony użytkowników. Firma Microsoft analizuje 65 sygnałów trakcji dziennie w celu identyfikowania klientów i ochrony przed zagrożeniami. Sygnały generowane przez usługę Identity Protection i fedowane do usługi Identity Protection mogą być bardziej federowane z narzędziami, na przykład dostępem warunkowym, w celu podejmowania decyzji dotyczących dostępu. Można ich także wrócić do narzędzia do zarządzania informacjami i zdarzeniami zabezpieczeń w celu dalszego badania na podstawie zasad wymuszonych przez organizację.

Ochrona tożsamości ułatwia organizacjom automatyczne zabezpieczanie się przed zagrożeniami tożsamości dzięki możliwości korzystania z analizy chmury obsługiwanej przez zaawansowane wykrywanie oparte na heuristicsach, analizie zachowań użytkowników i jednostek (UEBA) oraz uczenia maszynowego (ML) w całym ekosystemie firmy Microsoft.

![Pięciu pracowników udostępniaujących informacje może przedstawiać prezentację.](../media/win17-15021-00-n9.jpg)
 
## <a name="identify-sensitive-data-and-prevent-data-loss"></a>Identyfikowanie danych poufnych i zapobieganie utracie danych
Microsoft 365 umożliwia wszystkim organizacjom identyfikowanie poufnych danych w organizacji za pomocą kombinacji zaawansowanych funkcji, takich jak:

* **Microsoft Information Protection (MIP)** zarówno w przypadku klasyfikacji opartej na użytkowniku, jak i automatycznej klasyfikacji poufnych danych.
* **Office 365 zapobieganie utracie danych (DLP, Data Loss Prevention)** do automatycznej identyfikacji danych poufnych przy użyciu typów danych poufnych (czyli wyrażeń regularnych) oraz słów kluczowych i wymuszania zasad.

**[Microsoft Information Protection (MIP)](../compliance/information-protection.md)** umożliwia organizacjom inteligentne klasyfikowanie dokumentów i wiadomości e-mail przy użyciu etykiet wrażliwości. Etykiety wrażliwości mogą być stosowane ręcznie przez użytkowników do dokumentów w Microsoft Office i do wiadomości e-mail Outlook. Etykiety mogą automatycznie stosować oznaczenia dokumentów, chronić je za pomocą szyfrowania i wymuszać zarządzanie prawami. Etykiety wrażliwości można również stosować automatycznie, konfigurując zasady korzystające ze słów kluczowych i poufnych typów danych (takich jak numery kart kredytowych, numery ubezpieczenia społecznego i numery tożsamości) w celu automatycznego odnajdowania i klasyfikowania poufnych danych.

Ponadto firma Microsoft udostępnia "przeszkoliwnych klasyfikatorów", którzy używają modeli uczenia maszynowego do identyfikowania poufnych danych na podstawie zawartości, a nie po prostu przez dopasowywanie wzorców lub elementy w obrębie zawartości. Klasyfikator uczy się, jak zidentyfikować typ zawartości, patrząc na wiele przykładów zawartości do klasyfikacji. Szkolenie klasyfikatora zaczyna się od podania przykładów zawartości w określonej kategorii. Po  wyciągeniu wnioski z tych przykładów testowany jest model, podając połączenie zgodnych i niepasujących przykładów. Klasyfikator przewiduje, czy dany przykład należy do kategorii. Następnie osoba potwierdza wyniki, sortując wartości dodatnie, ujemne, fałszywie dodatnie i fałszywie ujemne, aby zwiększyć dokładność prognoz klasyfikatora. Po opublikowaniu przeszkolonego klasyfikatora przetwarza on zawartość w Microsoft Office SharePoint Online, Exchange Online i OneDrive dla Firm klasyfikuje zawartość.

Stosowanie etykiet wrażliwości do dokumentów i wiadomości e-mail osadza metadane identyfikujące wybraną czułość w obiekcie. Czułość jest następnie przesyłana wraz z danymi. Dlatego nawet jeśli dokument z etykietą jest przechowywany na pulpicie użytkownika lub w systemie lokalnym, jest nadal chroniony. Ta funkcja umożliwia innym Microsoft 365, takim jak usługa Microsoft Defender dla aplikacji w chmurze lub urządzenia brzegowe sieci, w celu identyfikowania poufnych danych i automatycznego wymuszania kontroli zabezpieczeń. Etykiety wrażliwości mają dodatkową zaletę, gdy pracownicy wiedzą, które dane w organizacji są uznawane za poufne, i jak poradzić sobie z danymi, gdy je otrzymają.

Office 365 zapobieganie utracie danych **[(DLP, Data Loss Prevention)](../compliance/dlp-learn-about-dlp.md)** automatycznie identyfikuje dokumenty, wiadomości e-mail i konwersacje zawierające poufne dane, skanując je w celu ochrony danych poufnych, a następnie wymuszając zasady dotyczące tych obiektów. Zasady są wymuszane dla dokumentów w SharePoint i OneDrive dla Firm. Są one wymuszane także podczas wysyłania wiadomości e-mail przez Teams czatach i konwersacjach na kanale. Zasady można skonfigurować tak, aby wyszukiwały słowa kluczowe, poufne typy danych, etykiety przechowywania oraz czy dane są udostępniane w organizacji, czy zewnętrznie. Dostępne są kontrolki, które ułatwiają organizacjom dostosowanie zasad DLP w celu zmniejszenia wyników fałszywie dodatnich. W przypadku odnalezionia poufnych danych użytkownikom w aplikacjach mobilnych mogą być wyświetlane porady dotyczące dostosowywalnych zasad, Microsoft 365 poinformować ich, że ich zawartość zawiera poufne dane, a następnie zaproponuje działania naprawcze. Zasady mogą także uniemożliwiać użytkownikom uzyskiwanie dostępu do dokumentów, udostępnianie dokumentów lub wysyłanie wiadomości e-mail zawierających określone typy danych poufnych. Microsoft 365 obsługuje ponad 100 wbudowanych typów danych poufnych. Organizacje mogą konfigurować niestandardowe poufne typy danych w celu spełnienia swoich zasad.

Aby pracownicy zrozumieli schemat klasyfikacji danych organizacji i które typy danych są uznawane za poufne, należy w tych organizacjach wprowadzać zasady ochrony przed migracją i ochrony przed nią. Udostępnienie pracownikom narzędzi i programów edukacyjnych, które ułatwiają identyfikowanie poufnych danych i zrozumienie sposobu ich obsługi, stanowi część rozwiązania ograniczającego ryzyko związane z zabezpieczeniami informacji.

Sygnały generowane przez usługę Identity Protection i fedowane do usługi Identity Protection mogą być także federowane do narzędzi, takich jak dostęp warunkowy, w celu podejmowania decyzji dotyczących dostępu lub do narzędzia do zarządzania informacjami i zdarzeniami zabezpieczeń na podstawie zasad wymuszonych przez organizację.

Ochrona tożsamości ułatwia organizacjom automatyczne zabezpieczanie się przed zagrożeniami tożsamości dzięki możliwości korzystania z analizy chmury obsługiwanej przez zaawansowane wykrywanie oparte na heuristicsach, analizach zachowania użytkowników i jednostek oraz uczenia maszynowego w całym ekosystemie firmy Microsoft.

![Pracownik informacji jest obrazowany przed dużą tablicą monitorów.](../media/clo1718-portrait-006.jpg)

## <a name="defend-the-fortress"></a>Obrona fortecy

Firma Microsoft niedawno wprowadziła Microsoft 365 Defender, które zostało zaprojektowane tak, aby zabezpieczyć nowoczesną organizację przed rozwijającym się krajobrazem zagrożeń. Korzystając z narzędzia Intelligent Security Graph, rozwiązanie ochrony przed zagrożeniami oferuje kompleksowe, zintegrowane zabezpieczenia przed wieloma wektorami ataków.

### <a name="the-intelligent-security-graph"></a>[Inteligentne zabezpieczenia Graph](https://www.microsoft.com/security/business/intelligence) 
Usługi zabezpieczeń firmy Microsoft 365 są obsługiwane przez usługę Intelligent Security Graph. Aby zwalczać cyberataki, inteligentny Graph używa zaawansowanej analizy do łączenia analizy zagrożeń i sygnałów zabezpieczeń od firmy Microsoft i jej partnerów. Firma Microsoft operuje usługami globalnymi na olbrzymią skalę, zbierając wiele sygnałów zabezpieczeń, które warstwy ochrony zasilania w stosie. Modele uczenia maszynowego oceniają tę analizę, a informacje o sygnałach i zagrożeniach są powszechnie udostępniane w naszych produktach i usługach. Dzięki temu możemy szybko wykrywać zagrożenia i reagować na nie oraz wprowadzać klientom alerty i informacje umożliwiające działanie w celu podejmowania działań naprawczych. Nasze modele uczenia maszynowego są stale przeszkolone i aktualizowane w celu budowania bezpieczniejszych produktów i zapewnienia bardziej proaktywnych zabezpieczeń.

[Program Microsoft Defender dla Office 365](../security/office-365-security/defender-for-office-365.md) udostępnia zintegrowaną usługę poczty Microsoft 365, która chroni organizacje przed złośliwymi linkami i złośliwym oprogramowaniem dostarczanym za pośrednictwem poczty e-mail Office dokumentów. Jednym z najczęstszych wektorów ataków, które dotykają użytkowników w dzisiejszych czasach, są ataki służące do wyłudzania informacji e-mail. Takie ataki mogą być kierowane do konkretnych użytkowników i mogą być bardzo chłone, a niektóre z nich mogą stanowić wezwanie do działania, które monituje użytkownika o kliknięcie złośliwego linku lub otwarcie załącznika zawierającego złośliwe oprogramowanie. Po zainfekowaniu komputera atakujący może ukraść poświadczenia użytkownika i poruszać się później po organizacji albo eksfiltrować wiadomości e-mail i dane w celu wyszukiwania informacji poufnych. Program Defender for Office 365 obsługuje bezpieczne załączniki i bezpieczne linki, oceniając dokumenty i linki w momencie kliknięcia pod celu uzyskania potencjalnie złośliwych intencji i blokuje dostęp. Załączniki wiadomości e-mail są otwierane w chronionej piaskownicy, zanim zostaną dostarczone do skrzynki pocztowej użytkownika. Sprawdza również łącza w dokumentach zawierających złośliwe Office URL. Program Defender Office 365 także linki i pliki w usługach SharePoint Online, OneDrive dla Firm i Teams. W przypadku wykrycia złośliwego pliku program Defender for Office 365 automatycznie blokuje ten plik, aby zmniejszyć potencjalne szkody.

[Program Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) to ujednolicona platforma zabezpieczeń punktów końcowych do zapobiegania ochrony, wykrywania po naruszeniu oraz automatycznego badania i reagowania. Program Defender for Endpoint oferuje wbudowane funkcje odnajdowania i ochrony poufnych danych w punktach końcowych przedsiębiorstwa.

[Usługa Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) umożliwia organizacjom stosowanie zasad na poziomie szczegółowości oraz wykrywanie anomalii zachowania na podstawie profilów poszczególnych użytkowników definiowanych automatycznie za pomocą uczenia maszynowego. Zasady usługi Defender for Cloud Apps mogą opierać się na zasadach dostępu warunkowego platformy Azure w celu ochrony poufnych zasobów firmy, oceniając dodatkowe sygnały związane z zachowaniem użytkownika i właściwościami dokumentów, do których uzyskano dostęp. Z czasem usługa Defender for Cloud Apps uczy się typowego zachowania każdego pracownika w odniesieniu do danych i aplikacji, do których uzyskuje dostęp. Na podstawie wzorców zachowania w zakresie wyuczonych informacji zasady mogą następnie automatycznie wymuszać mechanizmy kontroli zabezpieczeń, jeśli pracownik działa poza tym profilem. Na przykład jeśli pracownik zazwyczaj uzyskuje dostęp do aplikacji księgowej w godzinach od 9:00 do 17:00 od poniedziałku do piątku, ale nagle zaczyna mieć dostęp do tej aplikacji intensywnie w niedzielę wieczór, usługa Defender dla aplikacji w chmurze może dynamicznie wymuszać zasady wymagające ponownego uwierzytelnienia użytkownika. Dzięki temu poświadczenia użytkownika nie zostaną naruszone. Usługa Defender for Cloud Apps może także pomóc w zidentyfikowaniu "cienia IT" w organizacji, co ułatwia zespołom ds. bezpieczeństwa informacji zapewnianie pracownikom korzystania z chronionych narzędzi podczas pracy z poufnymi danymi. Ponadto usługa Defender dla aplikacji w chmurze może chronić poufne dane w dowolnym miejscu w chmurze, nawet poza Microsoft 365 platformą. Umożliwia organizacjom skonserdzenie (lub odblokowanie) określonych zewnętrznych aplikacji w chmurze, kontrolowanie dostępu i monitorowanie użycia.
 
[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) to oparte na chmurze rozwiązanie zabezpieczeń, które wykorzystuje sygnały lokalnej usługi Active Directory do identyfikowania, wykrywania i badanie zaawansowanych zagrożeń, naruszonych tożsamości i złośliwych działań niejawnych testerów skierowanych do organizacji. Serwer AATP umożliwia analitykom i specjalistom bezpieczeństwa w programie SecOp wykrywanie zaawansowanych ataków w środowiskach hybrydowych w celu:
* Monitoruj użytkowników, działania encji i działania za pomocą analizy opartej na nauczaniu.
* Chroń tożsamości i poświadczenia użytkowników przechowywane w usłudze Active Directory.
* Identyfikuj i badaj podejrzane działania użytkowników oraz zaawansowane ataki w ciągu ciągu kill-chain.
* Zapewnij jasne informacje o zdarzeniach na prostej osi czasu, aby szybko identywić informacje.

![Pracownicy biurowi spotkają się w małej sali konferencyjnej. Jeden umożliwia prezentację.](../media/clo1717-corporate-office-021.jpg)
 
## <a name="govern-data-and-manage-records"></a>Zarządzanie danymi i zarządzanie rekordami

Instytucje finansowe muszą przechowywać swoją dokumentację i informacje zgodnie ze swoimi zobowiązaniami prawnymi, prawnymi i biznesowymi reprezentowanmi w firmowym harmonogramie przechowywania danych. Na przykład [sec upoważnia](https://www.sec.gov/rules/interp/34-47806.htm) do przechowywania okresów przechowywania od trzech do sześciu lat, w zależności od typu rekordu, z natychmiastowym ułatwieniami dostępu przez pierwsze dwa lata. Organizacje pozostają w granicach wymogów prawnych i prawnych, jeśli dane są przechowywane za mało (odrzucone zbyt wcześnie), a także zarządzają przepisami, które nie są już wymagane do usuwania informacji. Skuteczne strategie zarządzania rekordami uwydatniają praktyczne i spójne podejście do właściwej ich usuwania, minimalizując jednocześnie koszty i ryzyko dla organizacji.
 
Ponadto upoważnienie prawne z Departamentu Usług Finansowych stanu Nowy Jork wymagają, aby objęte podmioty zachowywały zasady i procedury w celu usuwania informacji niepublikowych. 23 NYCRR 500, sekcja 500.13 Ograniczenia dotyczące przechowywania danych wymagają, że "W ramach programu zgodności podmiotu objętego będzie zawierał zasady i procedury dotyczące bezpiecznego usuwania na okres wszelkich informacji niepublikacyjnych zidentyfikowanych w sekcji 500.01(g)(2)-(3) tej części, które nie są już konieczne do działań biznesowych ani do innych uzasadnionych celów biznesowych objętego podmiotu,  z wyjątkiem sytuacji, gdy takie informacje są w inny sposób wymagane przez prawo lub przepisy".
 
Instytucje finansowe zarządzają ogromną ilością danych. Niektóre okresy przechowywania są wyzwalane przez zdarzenia, takie jak wygasanie umowy lub pracownik opuszcza organizację. W takim przypadku stosowanie zasad przechowywania rekordów może być trudne. Metody przypisywania okresów przechowywania rekordów dokładnie we wszystkich dokumentach organizacji mogą się różnić. Niektóre zasady przechowywania mają szerokie zastosowanie lub wykorzystują techniki autosklasyfikacji i uczenia maszynowego. Inni identyfikują podejście wymagające bardziej szczegółowego procesu, który w sposób unikatowy przypisuje okresy przechowywania poszczególnym dokumentom.

***Microsoft 365 elastyczne definiowanie etykiet przechowywania i zasad w celu inteligentnego implementowania wymagań dotyczących zarządzania rekordami.*** Menedżer rekordów definiuje etykietę przechowywania reprezentującą "typ rekordu" w tradycyjnym harmonogramie przechowywania. Etykieta przechowywania zawiera ustawienia definiujące następujące szczegóły:

- Jak długo jest zachowywany rekord
- Co się dzieje po wygaśnięciu okresu przechowywania (usuwanie dokumentu, rozpoczynanie przeglądania usuwania lub nie podejmiesz żadnych działań)
-  Co wyzwala okres przechowywania do początku (data utworzenia, data ostatniej modyfikacji, data oznaczony lub zdarzenie) i oznacza dokument lub wiadomość e-mail jako rekord (co oznacza, że nie można go edytować ani usuwać)

Etykiety przechowywania są następnie publikowane SharePoint lub OneDrive, Exchange skrzynek pocztowych i Microsoft 365 grupy. Użytkownicy mogą ręcznie stosować etykiety przechowywania do dokumentów i wiadomości e-mail. Menedżerowie rekordów mogą automatycznie stosować etykiety za pomocą analizy. Funkcje inteligentne mogą być oparte na [dziewięćdziesiąt plus](../compliance/content-search.md) wbudowanych typach informacji poufnych (takich jak numer wychodzący ABA, numer konta bankowego w USA lub numer PEST). Można je również dostosowywać na podstawie słów kluczowych lub danych poufnych znalezionych w dokumentach lub wiadomościach e-mail, takich jak numery kart kredytowych lub inne dane umożliwiające identyfikację użytkownika, lub na podstawie SharePoint metadanych. W przypadku danych, których nie da się łatwo zidentyfikować za pomocą ręcznego lub automatycznego dopasowywania wzorców, przeszkolne klasyfikatory mogą być używane do inteligentnego klasyfikowania dokumentów w oparciu o techniki uczenia maszynowego.
 
Komisja **Papierów Wartościowych i Exchange(SEC)** wymaga, aby papiery wartościowe i inne uregulowane instytucje finansowe zachowywały całą komunikację związaną z działalnością biznesową. Te wymagania mają zastosowanie do wielu typów komunikacji i danych, w tym wiadomości e-mail, dokumentów, wiadomości błyskawicznych, faksów i nie tylko. **Reguła SEC 17a-4** określa kryteria, które muszą spełnić te organizacje, aby przechowywać rekordy w elektronicznym systemie przechowywania danych. W 2003 r. sec opublikował publikację, która objaśniała te wymagania. Zawierała następujące kryteria:

* Dane zachowywane w elektronicznym systemie magazynowania muszą być nie do przepisywania i nie można ich wymazać. Nazywa się to wymaganiem WORM (napisz raz, przeczytaj wiele).
* W przypadku wezwania lub innego zlecenia prawnego system magazynowania musi mieć możliwość przechowywania danych poza okresem przechowywania wymaganym przez regułę.
* Organizacja nie narusza wymagań określonych w punkcie (f)(2)(ii)(A) reguły, jeśli użyła elektronicznego systemu magazynu, który uniemożliwia nadpisanie, wymazanie lub w inny sposób modyfikowanie rekordu w wymaganym okresie przechowywania dzięki użyciu zintegrowanych kodów sterowania sprzętem i oprogramowaniem.
* Elektroniczne systemy magazynowania, które jedynie "kontrolują" ryzyko, że rekord zostanie zastąpiony lub usunięty, na przykład przez kontrolę dostępu, nie spełnia wymagań tej reguły.

Aby ułatwić instytucjom finansowym spełnienie wymagań reguły SEC 17a–4, program Microsoft 365 udostępnia połączenie funkcji związanych ze sposobu przechowywania danych, konfigurowania zasad i przechowywania danych w ramach usługi. Obejmują one:

* **Zachowywanie danych (reguła 17a-4(a), (b)(4))** — Etykiety i zasady przechowywania są elastyczne w celu zaspokojenia potrzeb organizacji i mogą być automatycznie lub ręcznie stosowane do różnych typów danych, dokumentów i informacji. Obsługiwane są różne typy danych i sposób komunikacji, w tym dokumenty w programach SharePoint i OneDrive dla Firm, dane ze skrzynek pocztowych programu Exchange Online oraz dane w Teams.  
* Format nie do przepisywania **, nie erazybowalny (reguła 17a-4(f)(2)(ii)(A))** — funkcja Blokady zachowywania dla zasad przechowywania umożliwia menedżerom rekordów i administratorom konfigurowanie zasad przechowywania na restrykcyjne, takie jak nie można ich już modyfikować. Uniemożliwia to wszystkim usuwanie, wyłączanie i modyfikowanie zasad przechowywania w jakikolwiek sposób. Oznacza to, że po włączeniu funkcji Zachowywanie blokady nie można jej wyłączyć i nie ma żadnej metody, w której dane, do których zastosowano zasady przechowywania, mogą zostać zastąpione, zmodyfikowane lub usunięte w trakcie okresu przechowywania. Ponadto nie można skrócić okresu przechowywania. Okres przechowywania może jednak zostać wydłużony, gdy prawnie wymagane jest kontynuowanie przechowywania danych.<br/><br/>W przypadku stosowania blokady zachowywania do zasad przechowywania następujące akcje są ograniczone:

  - Okres przechowywania zasad można zwiększyć tylko. Nie można go skrócić.
  - Użytkowników można dodawać do zasad, ale nie można usuwać istniejących użytkowników skonfigurowanych w zasadach.
   - Zasady przechowywania nie mogą zostać usunięte przez żadnego administratora w organizacji.
 
  Blokada zachowania gwarantuje, że żaden użytkownik, a nie nawet administratorzy o najwyższych poziomach dostępu, nie będzie miał możliwości zmiany ustawień, modyfikowania, zastępowania lub usuwania przechowywanych danych, archiwizowania w programie Office 365 zgodnie z wytycznymi w wersji sec 2003.

* Jakość, dokładność oraz weryfikacja przechowywania/serializacji i indeksowania danych **(reguła 17a-4(f)(2) (ii)(B) i (C))** — obciążenia każdego z nich Office 365 zawierają funkcje automatycznego weryfikowania jakości i dokładności procesu rejestrowania danych na nośnikach magazynu. Ponadto dane są przechowywane przez korzystanie z metadanych i sygnatur czasowych, aby zapewnić wystarczające indeksowanie, aby umożliwić wydajne wyszukiwanie i pobieranie danych.
 
* Oddzielne przechowywanie zduplikowanych kopii **(reguła 17a-4(f)(3(iii))** — usługa Office 365 w chmurze przechowuje zduplikowane kopie danych jako podstawowy aspekt ich wysokiej dostępności. Jest to możliwe dzięki zaimplementowaniu nadmiarowości na wszystkich poziomach usługi, w tym na poziomie fizycznym na wszystkich serwerach, na poziomie serwera w centrum danych oraz na poziomie usługi dla geograficznych rozproszenia centrów danych.

* Dane dostępne do pobrania i dostępne **(reguła 17a-4(f)(2)(ii)(D))** — program Office 365 zasadniczo zezwala na wyszukiwanie, pobieranie i wyszukiwanie danych oznaczonych jako przechowywanie. Dzięki temu można przeszukiwać Exchange Online archiwach elektronicznych przy użyciu wbudowanych funkcji zbierania elektronicznych materiałów dowodowych. Następnie można pobierać dane w razie potrzeby w formatach standardowych, takich jak EDRML i PST.
 
* Wymagania inspekcji **(reguła 17a-4(f)(3)(v))** — program Office 365 udostępnia rejestrowanie inspekcji dla wszystkich akcji administracyjnych i działań użytkownika, które modyfikują obiekty danych, konfigurują lub modyfikują zasady przechowywania, wyszukuje zbierania elektronicznych materiałów dowodowych lub modyfikuje uprawnienia dostępu. Office 365 obsługuje kompleksowy dziennik inspekcji, w tym dane o tym, kto wykonał dane działanie, kiedy zostało wykonane, szczegóły dotyczące akcji i wykonywane polecenia. Dziennik inspekcji można następnie wy wyjściowy i w razie potrzeby uwzględniać w ramach formalnych procesów inspekcji.

Ponadto reguła 17a-4 wymaga, aby organizacje zachowywały rekordy dla wielu typów transakcji, aby były natychmiast dostępne przez dwa lata. Rekordy należy dodatkowo przechowywać przez okres od trzech do sześciu lat przy braku natychmiastowego dostępu. Zduplikowane rekordy muszą być również przechowywane przez ten sam okres w lokalizacji poza witryną. Office 365 zarządzania rekordami umożliwiają zachowywanie rekordów w taki sposób, że nie można ich modyfikować ani usuwać, ale można uzyskać do nich łatwy dostęp przez okres kontrolowany przez menedżera rekordów. Okres ten może obejmować dni, miesiące lub lata w zależności od zobowiązań organizacji dotyczących zgodności z przepisami.
 
Na żądanie firma Microsoft udostępni poświadczenie zgodności z normą SEC 17a-4, jeśli tego wymaga organizacja.

Ponadto te funkcje pomagają także spełnić wymagania dotyczące magazynowania dla reguły [CFTC 1.31(c)-(d)](https://www.cftc.gov/sites/default/files/opa/press99/opa4266-99-attch.htm) amerykańskiej komisja ds **.** handlu towarami i serii [4510 reguł FINRA](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4511) od urzędu certyfikacji **.** Microsoft 365 Te reguły stanowią globalnie najbardziej wstępną wskazówek dla instytucji finansowych, które mogą przechowywać rekordy.

Dodatkowe szczegółowe informacje dotyczące zgodności Microsoft 365 z regułą SEC 17a-4 oraz inne przepisy są dostępne w tece Ocena [Office 365 Exchange Online SEC 17a-4(f) / CFTC 1.31(c)-(d) firmy Cohasset Associates](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=9fa8349d-a0c9-47d9-93ad-472aa0fa44ec&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers).

## <a name="establish-ethical-walls-with-information-barriers"></a>Omyłowe ściany można osłaniać barierami informacyjnymi

Instytucje finansowe mogą podlegać regulacjom, które uniemożliwiają pracownikom pełniącym określone role wymianę informacji lub współpracę z innymi rolami. Na przykład opublikowane zostały reguły 2241(b)(2)(G), 2242(b)(2) (D), (b)(2)(H)(ii) oraz (b)(2)(H)(iii), które wymagają od członków:

"(G) ustanawiają bariery informacyjne lub inne zabezpieczenia w ramach instytucji mające na celu zapewnienie, że analitycy badawczi są izolują się od recenzji, nacisków lub nadzórów ze strony osób zaangażowanych w działania związane z usługami inwestycji lub innych osób, w tym pracowników działu sprzedaży i handlowego, które mogą być pod ich kontrolą lub pod ich nadzorem;" oraz "(H) ustanawiają bariery informacyjne lub inne zabezpieczenia w ramach instytucji mających na celu zapewnienie, że analitycy ds. badań naukowych i tym, z których są wykluczone tylko te osoby.  przegląd, naciski lub nadzór ze strony osób zaangażowanych w: (i) usługi banku inwestycji; (ii) głównego działalności handlowej lub handlowej i handlowej; oraz (iii) inne osoby, które mogą podlegać ich orzeczeń lub pod nadzorem;"

Ostatecznie te reguły wymagają, aby organizacje określały zasady i wdrażały bariery informacyjne między rolami w usługach bankowych, sprzedaży lub handlu w zakresie wymiany informacji i komunikacji z analitykami.

[Bariery informacyjne umożliwiają](../compliance/information-barriers.md) utworzenie ścian e-mail w środowisku firmy Office 365, umożliwiając administratorom zgodności lub innym autoryzowanym administratorom definiowanie zasad, które umożliwiają lub uniemożliwiają komunikację między grupami użytkowników w Teams. Bariery informacyjne kontrolają konkretne działania, aby zapobiec nieautoryzowanej komunikacji. Bariery informacyjne mogą również ograniczać komunikację w scenariuszach, w których zespoły wewnętrzne pracują nad fuzjami/zakupami lub poufnymi transakcjami albo pracują z poufnymi informacjami wewnętrznymi, które muszą być mocno ograniczone.

Bariery informacyjne w programie Microsoft 365 obsługują konwersacje i pliki w Teams. Mogą one zapobiegać następującym typom działań związanych z komunikacją w celu zapewnienia zgodności z przepisami FINRA:

* Wyszukiwanie użytkownika
* Dodawanie członka do zespołu lub kontynuowanie uczestniczenia w zespole z innym członkiem
* Rozpoczynanie lub kontynuowanie sesji czatu
* Rozpoczynanie lub kontynuowanie czatu grupowego
* Zapraszanie osoby do dołączenia do spotkania
* Udostępnianie ekranu
* Nakieruj rozmowę

## <a name="implement-supervisory-control"></a>Wdrażanie kontroli nadzorczych

Instytucje finansowe zwykle mają obowiązek ustanawiania i utrzymywania funkcji nadzorczych w swoich organizacjach w celu monitorowania działań pracowników i w celu zapewnienia zgodności z obowiązującym prawem papierów wartościowych. W szczególności finRA ustanowiła następujące wymagania pod nadzorem:
 
* Reguła [FINRA 3110 (Nadzór)](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) wymaga, aby firmy posiadały pisemne procedury nadzorczy w celu nadzór nad działaniami jej pracowników i typów firm, w których ta firma uczestniczy. Oprócz innych wymagań procedury muszą obejmować:
   - Nadzór nadzorcy
   - Przegląd usług bankowych, papierów wartościowych, komunikacji wewnętrznej i analiz wewnętrznych firmy
   - Przeglądanie transakcji dla niejawnych testerów
   - Przegląd korespondencji i skarg

   Procedury muszą opisywać osoby odpowiedzialne za przeglądy, działania nadzorczych, częstotliwość przeglądu oraz typy dokumentacji lub przeglądanych wiadomości.
 
* Reguła [FINRA 3120 (](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120)system kontroli nadzorczyj) wymaga, aby firmy posiadały system zasad i procedur nadzorczych, który umożliwia weryfikację pisemnego procedur nadzorczych określonych w art. 3110. Firmy muszą nie tylko mieć sieci WSP, ale również zasady, które testują te procedury co rok w celu weryfikacji ich możliwości zapewnienia zgodności z obowiązującymi przepisami i regulacjami dotyczącymi papierów wartościowych. W celu zdefiniowania zakresu testów można użyć metodyki i próbkowania opartych na czynnikach ryzyka. Ta reguła wymaga między innymi, aby kierownictwo wyższego szczebla udostępniło raport roczny, który będzie zawierał podsumowanie wyników testów oraz wszelkie znaczące wyjątki lub inne procedury wymagane do przetestowania wyników.

![Pracownik biura pokazuje wykres i tabele na ekranie, gdy inni spotykają się w tle.](../media/wco18-desk-work-002.jpg)
 
### <a name="communication-compliance"></a>Zgodność komunikacji

Zgodność komunikacji w programie Microsoft 365 umożliwia organizacjom wstępne skonfigurowanie zasad do przechwytywania komunikacji z pracownikami w celu monitorowania i przeglądu przez autoryzowanych przełożonych. Zasady dotyczące zgodności komunikacji mogą przechwytywać wewnętrzną/zewnętrzną pocztę e-mail i załączniki, Teams czatów i kanałów komunikacji oraz Skype dla firm komunikacji za pośrednictwem czatu online i załączników. Ponadto zgodność z przepisami komunikacji może być związana z komunikacją i danymi z usług innych firm (takich jak Bloomberg, Thomson Reuters, LinkedIn, Twitter, Facebook, Box i Dropbox).
Kompleksowy charakter komunikacji, która może być chwycona i przeglądana w ramach organizacji, oraz rozbudowane warunki, na których można konfigurować zasady, pozwalają na stosowanie się do zasad zgodności komunikacji, aby ułatwić instytucjom finansowym zachowanie zgodności z regułą FINRA 3110. Zasady mogą być skonfigurowane do przeglądania komunikacji poszczególnych osób lub grup.  Wyznaczeni przełożeni mogą być przypisywani na poziomie osoby lub grupy. Pełne warunki można skonfigurować do przechwytywania komunikacji na podstawie wiadomości przychodzących i wychodzących, domen, etykiet przechowywania, słów kluczowych lub fraz, słowników słów kluczowych, typów danych poufnych, załączników, rozmiaru wiadomości lub rozmiaru załącznika. Recenzentzy otrzymają pulpit nawigacyjny, na którym mogą przeglądać oflagowane wiadomości, działać na wiadomości, które mogą naruszać zasady, i oznaczać oflagowane elementy jako rozwiązane. Mogą oni także przeglądać wyniki recenzji i elementów, które zostały poprzednio rozwiązane.
  
Zgodność komunikacji zawiera raporty umożliwiające inspekcję działań przeglądu zasad na podstawie zasad i recenzenta. Dostępne są raporty w celu sprawdzenia, czy zasady działają zgodnie z definicjami pisemnych zasad nadzorów organizacji. Mogą być także używane do identyfikowania komunikacji wymagającej przeglądu oraz komunikacji niezgodnej z zasadami firmy. Ponadto wszystkie działania związane z konfigurowaniem zasad i przeglądaniem komunikacji są sprawdzane w ramach Office 365 ujednoliconego dziennika inspekcji. W wyniku tego zgodność komunikacji z przepisami w Microsoft 365 także instytucjach finansowych zgodnie z regułą FINRA 3120.

Zgodność komunikacji nie tylko jest zgodna z regułami FINRA, ale również umożliwia organizacjom monitorowanie komunikacji pod celu zapewnienia zgodności z innymi wymaganiami prawnymi, zasadami firmowymi i standardami e-mail. Zgodność z komunikacją udostępnia wbudowane klasyfikatory podszywają się pod nie, molestowania i wulgarności, które ułatwiają redukowanie wyników fałszywie dodatnich podczas przeglądania komunikacji, co pozwala zaoszczędzić czas recenzentów w trakcie procesu badania i rozwiązywania problemów. Pozwala również organizacjom na zmniejszenie ryzyka przez monitorowanie komunikacji w momencie poddania im zmian poufnych, takich jak fuzje i przejęcie lub zmiany kierownictwa.

![Pracownik informacyjny koncentruje się na ekranie.](../media/msc16-slalom-004.jpg)
 
## <a name="protect-against-data-exfiltration-and-insider-risk"></a>Ochrona przed wykrzykniem danych i ryzykiem w niejawnym programie testów

Częstym zagrożeniem dla przedsiębiorstw jest eksymrowanie danych lub działanie wyodrębniania danych z organizacji. To ryzyko może stanowić istotne zagrożenie dla instytucji finansowych ze względu na poufny charakter informacji, do których można codziennie uzyskiwać dostęp. Wraz z rosnącą liczbą dostępnych kanałów komunikacji i liczbą narzędzi do przenoszenia danych zaawansowane funkcje są zazwyczaj wymagane do ograniczenia ryzyka związanego z wyciekami danych, naruszeniami zasad i ryzykiem niejawnego programu testów.

### <a name="insider-risk-management"></a>Zarządzanie ryzykiem w niejawnym programie testów

Umożliwienie pracownikom narzędzi do współpracy w trybie online, które z natury są dostępne z dowolnego miejsca, zwiększa ryzyko dla organizacji. Pracownicy mogą przypadkowo lub w sposób złośliwy wyciekać dane do atakujących lub konkurentów.  Ewentualnie mogą oni eksfiltrować dane do użytku osobistego lub zabrać dane razem z nimi do przyszłego pracodawcy. Te scenariusze stwarzają poważne zagrożenia dla instytucji usług finansowych zarówno z perspektywy zabezpieczeń, jak i zgodności. Zidentyfikowanie tych czynników ryzyka w przypadku ich wystąpienia i ich szybkiego ograniczanie wymaga zarówno inteligentnych narzędzi do zbierania i współpracy danych z różnych działów, takich jak dział prawowy, kadrowy, jak i zabezpieczenia informacji.

Microsoft 365 niedawno w ramach rozwiązania do zarządzania ryzykiem w ramach niejawnego programu testów, które skoreluje sygnały we wszystkich usługach Microsoft 365 i używa modeli uczenia maszynowego do analizowania zachowań użytkowników pod kątem ukrytych wzorców i znaków ryzyka niejawnego programu testów. To narzędzie umożliwia współpracę między działaniami zabezpieczeń, schłodami wewnętrznymi i kadrami, co ułatwia rozwiązywanie spraw na podstawie wstępnie ustalonych przepływów pracy.  

Na przykład zarządzanie ryzykiem niejawnego programu testów w programie Microsoft 365 może skorelować sygnały z pulpitu programu Windows 10 użytkownika, takie jak kopiowanie plików na dysk USB lub wysyłanie wiadomości e-mail do osobistego konta e-mail, z działaniami z usług online, takimi jak poczta Office 365 e-mail, SharePoint Online, Microsoft Teams lub OneDrive dla Firm, aby zidentyfikować wzorce wykrzykowania danych. Te działania mogą także skorelować z pracownikami opuszczających organizację, co jest częstym wzorcem eksymrowania danych. Może monitorować wiele działań i zachowań w czasie. W przypadku wyłaniania się typowych wzorców można podnieść alerty i ułatwić skoncentrować się na kluczowych działaniach w celu weryfikacji naruszenia zasad z dużą pewnością siebie. Zarządzanie ryzykiem niejawnego programu testów może pseudonimizować dane od schronień w celu spełnienia przepisów dotyczących prywatności danych, jednocześnie jednocześnie przeglądając kluczowe działania, które ułatwiają im wydajne wykonywanie badań. Umożliwia schowanie i bezpieczne wysyłanie kluczowych danych dotyczących aktywności do działów kadr i prawniczych po typowych przepływach pracy eskalacji umożliwiających zwiększenie spraw na działania naprawcze.

Zarządzanie ryzykiem niejawnego programu testów w programie Microsoft 365 znacznie zwiększa możliwości organizacji w zakresie monitorowania i zbadania ryzyka niejawnego programu testów, umożliwiając jednocześnie organizacjom dalsze spełnianie przepisów dotyczących prywatności danych i stosowanie ustalonych ścieżek eskalacji, gdy sprawy wymagają działania wyższego poziomu. Aby uzyskać więcej informacji na temat zarządzania ryzykiem w niejawnym programie testów Microsoft 365, zobacz Nowoczesne punkty związane z ryzykiem i Przepływ pracy w te dotyczące zarządzania ryzykiem w niejawnym [programie testów w programie Microsoft 365](../compliance/insider-risk-management.md).

![Pracownik centrum obsługi w typie biurowym podczas wyświetlania ekranu.](../media/clo17-call-center-006.jpg)
 
### <a name="tenant-restrictions"></a>Ograniczenia dzierżawy
Organizacje, które zajmują się poufnymi danymi i ściśle kładą nacisk na bezpieczeństwo, zazwyczaj chcą kontrolować zasoby online dostępne dla użytkowników. Jednocześnie chcą umożliwić bezpieczną współpracę za pośrednictwem usług online, takich jak Office 365. W efekcie kontrolowanie środowisk Office 365, do których użytkownicy mogą uzyskać dostęp, staje się wyzwaniem, ponieważ za pomocą środowiska Office 365 niekorektowego można w sposób złośliwy lub przypadkowo eksfiltrować dane z urządzeń firmowych. Tradycyjne organizacje ograniczają domeny lub adresy IP, do których użytkownicy mogą uzyskać dostęp z urządzeń firmowych. Nie działa to jednak w pierwszym świecie chmury, w którym użytkownicy muszą mieć legalny dostęp do Office 365 usług.

Microsoft 365 ograniczenia dzierżawy [możliwości](/azure/active-directory/manage-apps/tenant-restrictions) rozwiązania tego wyzwania. Ograniczenia dzierżawy można skonfigurować tak, aby ograniczyć dostęp pracowników Office 365 dzierżawy przedsiębiorstwa za pomocą tożsamości rogu (tożsamości, które nie są częścią katalogu firmowego). Obecnie ograniczenia dzierżawy obowiązują dla całej dzierżawy, zezwalając na dostęp tylko do tych dzierżaw, które są wyświetlane na skonfigurowanej przez Ciebie liście. Firma Microsoft nieustannie opracowuje to rozwiązanie w celu zwiększenia poziomu kontroli i wzbogacić zapewniane przez nie zabezpieczenia.

![GRAFIKA.](../media/clo1717-corporate-office-001.jpg)
 
## <a name="conclusion"></a>Wnioski

Microsoft 365 i Teams to zintegrowane i kompleksowe rozwiązanie dla firm finansowych, umożliwiające prostą, a jednocześnie zaawansowaną współpracę w chmurze oraz funkcje komunikacji na całym przedsiębiorstwie. Używając technologii zabezpieczeń i zgodności firmy Microsoft 365, instytucje mogą działać w bezpieczniejszy i zgodny sposób dzięki niezawodnej kontroli zabezpieczeń w celu ochrony danych, tożsamości, urządzeń i aplikacji przed różnymi czynnikami operacyjnymi, w tym zagrożeniami bezpieczeństwa i niejawnego programu testów. Microsoft 365 stanowi podstawową, bezpieczną platformę, na której organizacje usług finansowych mogą osiągnąć więcej, chroniąc jednocześnie swoją firmę, pracowników i klientów.
