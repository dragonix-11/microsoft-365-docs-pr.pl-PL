---
title: Struktura ładu współpracy dla Microsoft 365
ms.reviewer: mmclean
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-overview
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Poznaj najlepsze rozwiązania dotyczące ładu dla narzędzi do współpracy Microsoft 365, w tym Grupy Microsoft 365, Teams, SharePoint i Yammer.
ms.openlocfilehash: f4afed27fa6d40f7f6967583bcfd3f43c69c7963
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285001"
---
# <a name="what-is-collaboration-governance"></a>Co to jest zarządzanie współpracą?

Ład współpracy to sposób zarządzania dostępem użytkowników do zasobów, zgodnością ze standardami biznesowymi i zapewnieniem bezpieczeństwa danych.

Obecnie organizacje korzystają z zróżnicowanego zestawu narzędzi. Istnieje zespół deweloperów korzystających z czatu zespołowego, kierownictwo wysyłające wiadomości e-mail i cała organizacja łącząca się za pośrednictwem społeczności przedsiębiorstwa. Wiele narzędzi do współpracy jest używanych, ponieważ każda grupa jest unikatowa i ma własne potrzeby funkcjonalne i styl pracy. Niektórzy będą używać tylko poczty e-mail, podczas gdy inni będą żyć głównie na czacie. 

Jeśli użytkownicy uważają, że narzędzia informatyczne nie odpowiadają ich potrzebom, prawdopodobnie pobierzą swoją ulubioną aplikację dla konsumentów, która obsługuje ich scenariusze. Chociaż ten proces umożliwia użytkownikom szybkie rozpoczęcie pracy, prowadzi do frustrującej pracy użytkownika w całej organizacji z wieloma identyfikatorami logowania, trudnościami w udostępnianiu i brakiem jednego miejsca do wyświetlania zawartości. Ta koncepcja jest określana jako "Shadow IT" i stanowi znaczące zagrożenie dla organizacji. Zmniejsza to możliwość jednolitego zarządzania dostępem użytkowników, zapewniania bezpieczeństwa i zgodności usług.

Usługi, takie jak grupy Microsoft 365, Teams i Yammer wzmacniają możliwości użytkowników i zmniejszają ryzyko tworzenia w tle zasobów informatycznych, udostępniając narzędzia potrzebne do współpracy. Microsoft 365 ma bogaty zestaw narzędzi do implementowania wszelkich funkcji ładu, których organizacja może wymagać. 

![Wykres przedstawiający opcje ładu współpracy w Microsoft 365.](../media/collaboration-governance-overview.png)

Ta seria artykułów pomoże Ci zrozumieć, w jaki sposób grupy, zespoły i ustawienia SharePoint współdziałają, jakie możliwości ładu są dostępne, oraz jak utworzyć i zaimplementować strukturę ładu dla funkcji współpracy w Microsoft 365.

### <a name="setting-up-secure-collaboration-with-microsoft-365"></a>Konfigurowanie bezpiecznej współpracy z Microsoft 365

Istnieje wiele opcji wdrażania Grupy Microsoft 365 i Teams na potrzeby bezpiecznej współpracy w organizacji. Zalecamy używanie tej zawartości ładu wraz z [konfigurowaniem bezpiecznego udostępniania plików i współpracy z Microsoft Teams](setup-secure-collaboration-with-teams.md) i skojarzonymi z nimi artykułami w celu utworzenia najlepszego rozwiązania do współpracy dla organizacji.

### <a name="data-residency-governance"></a>Ład dotyczący rezydencji danych

Jeśli Twoja organizacja jest wielonarodowa i masz wymagania dotyczące przechowywania danych dla różnych lokalizacji geograficznych, uwzględnij [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo) w ramach planu ładu współpracy.

## <a name="why-microsoft-365-groups-are-important-in-collaboration-governance"></a>Dlaczego grupy Microsoft 365 są ważne w zakresie zarządzania współpracą

Microsoft 365 grup pozwala wybrać zestaw osób, którym chcesz współpracować, i łatwo skonfigurować kolekcję zasobów do udostępnienia tym osobom. Dodanie członków do grupy automatycznie przyznaje wymagane uprawnienia do wszystkich zasobów dostarczonych przez grupę. Zarówno Teams, jak i Yammer używają grup Microsoft 365 do zarządzania członkostwem.

Microsoft 365 grupy obejmują zestaw połączonych zasobów, których użytkownicy mogą używać do komunikacji i współpracy. Grupy zawsze obejmują witrynę SharePoint, planistę, obszar roboczy Power BI, skrzynkę pocztową i kalendarz oraz usługę Stream. W zależności od sposobu tworzenia grupy możesz opcjonalnie dodać inne usługi, takie jak Teams, Yammer i Project.

![Diagram przedstawiający Grupy Microsoft 365 i powiązane usługi.](../media/microsoft-365-groups-hub-spoke.png)

|Zasób|Opis|
|:------|:----------|
|[Kalendarz](https://support.office.com/article/schedule-a-meeting-on-a-group-calendar-in-outlook-0cf1ad68-1034-4306-b367-d75e9818376a)|Planowanie zdarzeń związanych z grupą|
|[Skrzynki odbiorczej](https://support.office.com/article/have-a-group-conversation-in-outlook-a0482e24-a769-4e39-a5ba-a7c56e828b22)|W przypadku konwersacji e-mail między członkami grupy. Ta skrzynka odbiorcza ma adres e-mail i można ją ustawić tak, aby akceptowała wiadomości od osób spoza grupy, a nawet spoza organizacji, podobnie jak tradycyjna lista dystrybucyjna.|
|[Notes programu OneNote](https://support.office.com/article/get-started-with-onenote-e768fafa-8f9b-4eac-8600-65aa10b2fe97)|Do zbierania pomysłów, badań i informacji|
|[Planner](https://support.office.com/article/microsoft-planner-help-4a9a13c6-3adf-4a60-a6fc-15c0b15e16fc)|Przypisywanie zadań projektu i zarządzanie nimi między członkami grupy|
|[Power BI obszar roboczy](/power-bi/collaborate-share/service-new-workspaces)|Przestrzeń współpracy danych z pulpitami nawigacyjnymi i raportami|
|[Project i plan działania](https://support.microsoft.com/project)|Narzędzia do zarządzania projektami opartymi na sieci Web|
|[witryna zespołu SharePoint](https://support.office.com/article/what-is-a-sharepoint-team-site-75545757-36c3-46a7-beed-0aaa74f0401e)|Centralne repozytorium informacji, linków i zawartości związanych z twoją grupą|
|[Stream](https://support.microsoft.com/microsoft-stream)|Usługa przesyłania strumieniowego wideo|
|[Teams](https://support.microsoft.com/teams)|Obszar roboczy oparty na czacie w Microsoft 365|
|[grupa Yammer](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)|Wspólne miejsce do konwersacji i udostępniania informacji|

Grupy Microsoft 365 obejmuje różne mechanizmy kontroli ładu, w tym zasady wygasania, konwencje nazewnictwa i zasady zablokowanych słów, które ułatwiają zarządzanie grupami w organizacji. Ponieważ grupy kontrolują członkostwo i dostęp do tego zestawu zasobów, zarządzanie grupami jest kluczowym elementem zarządzania współpracą w Microsoft 365.

## <a name="define-collaboration-governance-best-practices-for-your-organization"></a>Definiowanie najlepszych rozwiązań dotyczących ładu współpracy dla organizacji

Istnieje wiele miejsc do współpracy i konwersacji w Microsoft 365. Zrozumienie, gdzie użytkownicy mogą rozpoczynać konwersacje, może pomóc w zdefiniowaniu strategii komunikacji.

Istnieją trzy główne metody komunikacji obsługiwane przez Microsoft 365:

- Outlook: współpraca za pośrednictwem poczty e-mail z udostępnioną skrzynką odbiorczą grupy i kalendarzem
- Microsoft Teams: obszar roboczy oparty na czatach trwałych, w którym można prowadzić nieformalne, w czasie rzeczywistym konwersacje dotyczące różnych tematów organizowanych przez określone grupy podrzędne
- Yammer: środowisko społecznościowe przedsiębiorstwa na potrzeby współpracy

![Diagram przedstawiający, kiedy używać Teams, Yammer i Outlook.](../media/inner-loop-outer-loop.png)

- Teams: obszar roboczy oparty na czatach (współpraca z dużą szybkością) — pętla wewnętrzna
  - Stworzona na potrzeby współpracy z osobami, z którymi użytkownicy pracują na co dzień
  - Umieszcza informacje w zasięgu ręki użytkowników w jednym środowisku
  - Dodawanie kart, łączników i botów
  - Czat na żywo, konferencje audio/wideo, nagrane spotkania

- Yammer: nawiązywanie połączenia między organizacją (enterprise social) — pętla zewnętrzna
  - Społeczności praktyk — grupy funkcjonalne osób, które podzielają wspólny interes lub wiedzę, ale niekoniecznie współpracują ze sobą na co dzień
  - Połączenie przywództwa, społeczności edukacyjne, społeczności oparte na rolach

- Skrzynka pocztowa i kalendarz (współpraca oparta na wiadomościach e-mail)
  - Służy do ukierunkowanej komunikacji z grupą osób
  - Kalendarz udostępniony na spotkania z innymi członkami grupy
 
Podczas określania sposobu używania funkcji współpracy w Microsoft 365 należy wziąć pod uwagę te metody komunikacji i które użytkownicy mogą używać w różnych scenariuszach.

> [!NOTE]
> Po utworzeniu nowej grupy Office 365 za pośrednictwem Yammer lub Teams grupa nie jest widoczna w Outlook ani w książce adresowej, ponieważ podstawowa komunikacja między tymi użytkownikami odbywa się u ich odpowiednich klientów. Yammer grup nie można połączyć z Teams.

## <a name="collaboration-governance-best-practices-checklist"></a>Lista kontrolna najlepszych rozwiązań dotyczących ładu w zakresie współpracy

Podczas rozpoczynania procesu planowania ładu należy pamiętać o następujących najlepszych rozwiązaniach:

- **Porozmawiaj ze swoimi użytkownikami** — zidentyfikuj swoich największych użytkowników funkcji współpracy i spotkaj się z nimi, aby zrozumieć ich podstawowe wymagania biznesowe i scenariusze przypadków użycia.

- **Równoważenie ryzyka i korzyści** — przejrzyj potrzeby biznesowe, prawne, prawne i zgodności oraz zaplanuj rozwiązanie, które optymalizuje pod kątem wszystkich wyników.

- **Dostosuj się do różnych organizacji i różnych typów zawartości i scenariuszy** — weź pod uwagę różne potrzeby różnych grup lub działów oraz różne typy zawartości, takie jak zawartość intranetowa, a nie zawartość OneDrive użytkownika.

- **Dopasowanie do priorytetów biznesowych** — cele biznesowe pomogą Ci określić, ile czasu i energii potrzebujesz do inwestowania w ład.

- **Osadzanie decyzji dotyczących ładu bezpośrednio w utworzonych rozwiązaniach** — wiele decyzji dotyczących ładu można zaimplementować, włączając lub wyłączając funkcje w Microsoft 365.


- **Użyj podejścia etapowego** — najpierw wprowadź funkcje współpracy dla niewielkiej grupy użytkowników. Uzyskaj od nich opinię, obejrzyj bilety pomocy technicznej i zaktualizuj wszelkie wymagane ustawienia lub procesy przed przejściem do większej grupy.

- **Wzmacnianie dzięki szkoleniu** — dostosuj rozwiązania, takie jak [Microsoft 365 ścieżki szkoleniowe](/office365/customlearning), aby zapewnić, że oczekiwania specyficzne dla organizacji zostaną wzmocnione dzięki szkoleniom zapewnianym przez firmę Microsoft.

- **Masz strategię przekazywania zasad i wytycznych dotyczących ładu w organizacji** — utwórz centrum wdrażania Microsoft 365 w witrynie komunikacji SharePoint, aby komunikować się z zasadami i procedurami.

- **Definiowanie ról i obowiązków** — najpierw zidentyfikuj swój podstawowy zespół ds. ładu i pracuj nad kluczowymi decyzjami dotyczącymi ładu dotyczącymi aprowizacji i nazewnictwa oraz dostępu zewnętrznego, a następnie pracuj nad pozostałymi decyzjami.

- **Ponawiaj decyzje w miarę zmian biznesowych i technologicznych** — okresowo wywiązywać się z nowych możliwości i nowych oczekiwań biznesowych.

Aby bliżej przyjrzeć się tym praktykom, przeczytaj [Tworzenie planu ładu współpracy](collaboration-governance-first.md).

## <a name="end-user-impact-and-change-management"></a>Zarządzanie wpływem i zmianami użytkowników końcowych

Ponieważ grupy i zespoły można tworzyć na kilka sposobów, zalecamy szkolenie użytkowników w celu korzystania z metody, która najlepiej pasuje do Twojej organizacji:

- Jeśli twoja organizacja wykonuje większość komunikacji za pomocą poczty e-mail, poproś użytkowników o utworzenie grup w Outlook.
- Jeśli Organizacja intensywnie korzysta z SharePoint lub migruje z SharePoint lokalnie, poproś użytkowników o utworzenie SharePoint witryn zespołowych na potrzeby współpracy.
- Jeśli twoja organizacja wdrożyła Teams, poproś użytkowników, aby utworzyli zespół, gdy potrzebują miejsca do współpracy.

Pomaga to uniknąć nieporozumień, jeśli użytkownicy nie znają sposobu, w jaki grupy odnoszą się do powiązanych usług. Aby uzyskać więcej informacji na temat sposobu mówienia użytkownikom o grupach, zobacz [Objaśnienie Grupy Microsoft 365 dla użytkowników](../admin/create-groups/explain-groups-knowledge-worker.md).

## <a name="key-collaboration-governance-capabilities-and-licensing-requirements"></a>Kluczowe możliwości zarządzania współpracą i wymagania dotyczące licencjonowania

Funkcje ładu do współpracy w Microsoft 365 obejmują funkcje Microsoft 365, Teams, SharePoint i Azure Active Directory.

| Możliwość lub funkcja | Opis | Licencjonowanie |
|:----------------------|:------------|:----------|
|Udostępnianie zespołu i witryny|Oceń, czy zespoły, grupy i witryny mogą być udostępniane osobom spoza organizacji.|Microsoft 365 E5 lub E3|
|Zezwalaj/blokuj domenę|Ogranicz udostępnianie osobom spoza organizacji do osób z określonych domen.|Microsoft 365 E5 lub E3|
|Samoobsługowe tworzenie witryny|Zezwalaj użytkownikom na tworzenie własnych witryn SharePoint lub uniemożliwiaj ich tworzenie.|Microsoft 365 E5 lub E3|
|Ograniczone udostępnianie witryn i plików|Ogranicz udostępnianie witryn, plików i folderów do członków określonej grupy zabezpieczeń.|Microsoft 365 E5 lub E3|
|Tworzenie grupy z ograniczeniami|Ogranicz tworzenie zespołu i grupy do członków określonej grupy zabezpieczeń.|Microsoft 365 E5 lub E3 z licencjami Azure AD — wersja Premium lub Azure AD Basic EDU|
|Zasady nazewnictwa grup|Wymuszanie prefiksów lub sufiksów w nazwach grup i zespołów.|Microsoft 365 E5 lub E3 z licencjami Azure AD — wersja Premium lub Azure AD Basic EDU|
|Zasady wygasania grupy|Ustaw nieaktywne grupy i zespoły, aby wygasły i zostały usunięte po określonym czasie.|Microsoft 365 E5 lub E3 z licencjami Azure AD — wersja Premium|
|Dostęp gościa dla grupy|Zezwalaj na udostępnianie zespołów i grup osobom spoza organizacji lub zapobiegaj ich udostępnianiu w oparciu o grupę.|Microsoft 365 E5 lub E3|

## <a name="collaboration-governance-planning-recommendations"></a>Zalecenia dotyczące planowania zarządzania współpracą

Wykonaj następujące podstawowe kroki, aby utworzyć plan utrzymania ładu:

1. Rozważ kluczowe cele biznesowe i procesy — [utwórz plan utrzymania ładu](collaboration-governance-first.md) , aby zaspokoić potrzeby twojej firmy.
2. Informacje o ustawieniach usług — [ustawienia w grupach i SharePoint](groups-sharepoint-governance.md) współdziałają ze sobą, podobnie jak [ustawienia w grupach, SharePoint i Teams](groups-sharepoint-teams-governance.md) i [innych usługach](groups-services-interactions.md). Pamiętaj, aby zrozumieć te interakcje podczas planowania strategii ładu.
3. Planowanie zarządzania dostępem użytkowników — [zaplanuj poziom dostępu, który chcesz przyznać użytkownikom w grupach, SharePoint i Teams](groups-teams-access-governance.md).
4. Planowanie zarządzania ustawieniami zgodności — przejrzyj dostępne [opcje zgodności dla grup Microsoft 365, Teams i współpracy SharePoint](groups-teams-compliance-governance.md).
5. Planowanie zarządzania komunikacją — zapoznaj się z [dostępnymi opcjami zarządzania komunikacją w scenariuszach współpracy](groups-teams-communication-governance.md).
6. Planowanie ładu w organizacji i cyklu życia — wybierz [zasady, których chcesz użyć do tworzenia grup i zespołów, nazewnictwa, wygasania i archiwizacji](plan-organization-lifecycle-governance.md). Ponadto zapoznaj się [z opcjami zakończenia cyklu życia grup, zespołów i Yammer](end-life-cycle-groups-teams-sites-yammer.md)

![Ilustracja zalecanych kroków nadzoru.](../media/collaboration-governance-steps.png)

## <a name="training-for-administrators"></a>Szkolenie dla administratorów

Te moduły szkoleniowe z usługi Microsoft Learn mogą pomóc w poznaniu funkcji ładu w Microsoft 365.

#### <a name="information-protection"></a>Ochrona informacji

|Szkolenia:|Zarządzanie ochroną informacji i ładem|
|:---|:---|
|![Ikona trenowania ochrony informacji.](../media/information-protection-governance.svg)|Ilość generowanych obecnie danych rośnie szybciej niż kiedykolwiek wcześniej, pracownicy chcą pracować wszędzie, a otoczenie regulacyjne stale się zmienia. Rozwiązania firmy Microsoft do ochrony informacji i ładu pomagają organizacjom osiągnąć właściwą równowagę między ochroną danych a produktywnością pracowników. Ta ścieżka szkoleniowa może pomóc w przygotowaniu się do certyfikacji Microsoft 365 Certified: Security Administrator Associate i Microsoft 365 Certified: Enterprise Administration Expert.<br><br>5 godz. 13 min — ścieżka Edukacja — 7 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/m365-compliance-information-governance/introduction/)

<br><br>

|Szkolenia:|Ochrona informacji o przedsiębiorstwie za pomocą Microsoft 365|
|:---|:---|
|![Teams ikona trenowania.](../media/protect-enterprise-information-microsoft-365.svg)|Ochrona i zabezpieczanie informacji organizacji jest trudniejsze niż kiedykolwiek wcześniej. W ścieżce szkoleniowej Ochrona informacji o przedsiębiorstwie za pomocą Microsoft 365 omówiono sposób ochrony poufnych informacji przed przypadkowym nadmiernym udostępnianiem lub niewłaściwym użyciem, sposobu odnajdywania i klasyfikowania danych, sposobu ich ochrony za pomocą etykiet poufności oraz sposobu monitorowania i analizowania poufnych informacji w celu ochrony przed ich utratą. Ta ścieżka szkoleniowa może pomóc w przygotowaniu się do certyfikacji Microsoft 365 Certified: Security Administrator Associate i Microsoft 365 Certified: Enterprise Administration Expert.<br><br>1 godz. ścieżka Edukacja — 5 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="security-and-compliance"></a>Zabezpieczenia i zgodność

|Szkolenia:|Prezentacja podstawowej wiedzy na temat Microsoft 365 możliwości zabezpieczeń i zgodności|
|:---|:---|
|![Ikona trenowania zabezpieczeń i zgodności.](../media/microsoft-365-security-and-compliance-capabilities.svg)|Dowiedz się więcej o obszarach rozwiązań w zakresie zabezpieczeń i zgodności Microsoft 365 oraz dostępnych możliwościach, które ułatwiają przedsiębiorstwom zabezpieczanie przedsiębiorstwa i spełnianie wymagań prawnych. Jeśli nie znasz podstawowych pojęć dotyczących przetwarzania w chmurze, zalecamy skorzystanie z [pojęć dotyczących chmury — zasad przetwarzania w chmurze](/learn/modules/principles-cloud-computing/index).<br><br>3 godz. 11 min — ścieżka Edukacja — 8 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/what-is-m365/1-introduction/)

## <a name="illustrations"></a>Ilustracje

Te ilustracje pomogą Ci zrozumieć, w jaki sposób grupy i zespoły współdziałają z innymi usługami w Microsoft 365 oraz jakie funkcje zapewniania ładu i zgodności ułatwiają zarządzanie tymi usługami w organizacji.

### <a name="groups-in-microsoft-365-for-it-architects"></a>Grupy w Microsoft 365 dla architektów IT
Co architekci IT muszą wiedzieć o grupach w Microsoft 365

|**Element**|**Opis**|
|:-----|:-----|
|[![Obraz kciuka dla infografiki grup.](../downloads/msft-m365-groups-architecture-thumb.png)](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) <br/> [PDF](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) \| [Visio](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.vsdx) <br> Zaktualizowano maj 2022 r.|Na tych ilustracjach przedstawiono różne typy grup, sposób ich tworzenia i zarządzania oraz kilka zaleceń dotyczących ładu.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams i powiązanych usług produktywności w Microsoft 365 dla architektów IT
Architektura logiczna usług produktywności w Microsoft 365, wiodąca z Microsoft Teams.

|**Element**|**Opis**|
|:-----|:-----|
|[![Obraz kciuka dla Teams plakatu architektury logicznej.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Zaktualizowano kwiecień 2019 r.   |Firma Microsoft oferuje zestaw usług zwiększających produktywność, które współpracują ze sobą w celu zapewnienia współpracy z funkcjami zapewniania ładu, zabezpieczeń i zgodności danych. <br/> <br/>Ta seria ilustracji przedstawia logiczną architekturę usług produktywności dla architektów przedsiębiorstw, prowadzących z Microsoft Teams.|

### <a name="microsoft-365-information-protection-and-compliance-capabilities"></a>Microsoft 365 możliwości ochrony informacji i zgodności

Microsoft 365 obejmuje szeroki zestaw funkcji ochrony informacji i zgodności. Wraz z narzędziami zwiększającymi produktywność firmy Microsoft te funkcje mają na celu ułatwienie organizacjom współpracy w czasie rzeczywistym przy jednoczesnym przestrzeganiu rygorystycznych ram zgodności z przepisami. 

Ten zestaw ilustracji korzysta z jednej z najbardziej regulowanych branż, usług finansowych, aby zademonstrować, w jaki sposób te możliwości mogą być stosowane w celu spełnienia typowych wymagań prawnych. Możesz dostosować te ilustracje do własnych potrzeb. 


| Element | Opis |
|:-----|:-----|
|[![Plakat modelu: Funkcje ochrony informacji i zgodności w usłudze Microsoft Purview.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/> Angielski: [pobierz jako plik PDF](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| [jako Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japoński: [pobierz jako plik PDF](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)\| [jako Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)   <br/> Zaktualizowano listopad 2020 r.|Zawiera: <ul><li>  Microsoft Purview Information Protection i Microsoft Purview Data Loss Prevention</li><li>Zasady przechowywania i etykiety przechowywania </li><li>Bariery informacyjne</li><li>Zgodność w komunikacji</li><li>Ryzyko związane z wewnętrznymi testerami</li><li>Pozyskiwanie danych innych firm</li>|

## <a name="conference-sessions"></a>Sesje konferencyjne

Obejrzyj te sesje konferencyjne, aby dowiedzieć się więcej na temat ładu dla Grupy Microsoft 365 i Teams.

**Podstawy**

Poznaj podstawy i nowe innowacje w Grupy Microsoft 365, w tym zarządzanie i zarządzanie na dużą skalę, najlepsze rozwiązania dotyczące używania i wdrażania oraz samoobsługi.

- [Ogarnij Grupy Microsoft 365](https://www.youtube.com/watch?v=dAamBF1gb7M)

**Nadzór**

Dowiedz się, jak skonfigurować cykl życia wygaśnięcia grup, zasady nazewnictwa, etykiety klasyfikacji, współpracę z gośćmi zewnętrznymi i zarządzać uprawnieniami do tworzenia grup.

- [Przekształcanie współpracy i walka z mroczną it za pomocą grup Office 365](https://www.youtube.com/watch?v=Bhf_bKx3lAg)

**Przykład klienta**

Zobacz zakulisowy przykład współpracy Grupy Microsoft 365, SharePoint, Teams i Yammer w celu zapewnienia globalnej platformy współpracy.

- [Znajdowanie słodkiego miejsca współpracy za pomocą Grupy Microsoft 365, SharePoint, Teams i Yammer](https://www.youtube.com/watch?v=Rx9eVwqXeQk)

## <a name="see-also"></a>Zobacz też

[Dokumentacja zabezpieczeń platformy Microsoft 365](../security/index.yml)

[Dokumentacja usługi Microsoft Purview](../compliance/index.yml)
