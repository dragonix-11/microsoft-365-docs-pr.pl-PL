---
title: Konfigurowanie Teams przy użyciu trzech warstw zabezpieczeń udostępniania plików
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
- m365solution-securecollab
- m365solution-scenario
ms.custom:
- Ent_Architecture
- seo-marvel-jun2020
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
recommendations: false
description: Dowiedz się, jak Teams w celu lepszej zabezpieczeń udostępniania plików przy użyciu trzech poziomów ochrony, co zapewnia równoważenie zabezpieczeń z łatwością współpracy.
ms.openlocfilehash: 116675ac6736e1761286226a8bf724915627574f
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712726"
---
# <a name="configure-teams-with-three-tiers-of-protection"></a>Konfigurowanie Teams z trzema poziomami ochrony

Artykuły z tej serii zawierają zalecenia dotyczące konfigurowania zespołów w programie Microsoft Teams i skojarzonych z nimi witryn SharePoint w celu ochrony plików, która zapewnia bezpieczeństwo z łatwością współpracy.

W tym artykule zdefiniowano cztery różne konfiguracje, począwszy od zespołu publicznego z najbardziej otwartymi zasadami udostępniania. Każda dodatkowa konfiguracja odzwierciedla istotny krok ochrony, natomiast możliwość dostępu do plików przechowywanych w zespołach i współpracy nad nimi jest ograniczona do odpowiedniego zestawu członków zespołu. 

Konfiguracje w tym artykule są zgodne z zaleceniami firmy Microsoft dla trzech warstw ochrony danych, tożsamości i urządzeń:

- Ochrona planu bazowego

- ochrona po poufnej ochronie

- Wysoce wrażliwa ochrona

Aby uzyskać więcej informacji o tych warstwach i możliwościach zalecanych dla poszczególnych warstw, zobacz Ilustracje przedstawiające firmę [Microsoft Cloud dla architektów przedsiębiorstwa](./cloud-architecture-models.md)


## <a name="three-tiers-at-a-glance"></a>Rzut oka na trzy warstwy

W poniższej tabeli podsumowano konfiguracje poszczególnych warstw. Konfiguracje te należy stosować jako zalecenia punktu początkowego i dostosowywać je do potrzeb organizacji. Każda warstwa może nie być potrzebna.

|-|Plan bazowy (publiczny)|Plan bazowy (prywatna)|Pochylić|Wysoce ważnych|
|:-----|:-----|:-----|:-----|:-----|
|Zespół prywatny lub publiczny|Publiczne|Prywatna|Prywatna|Prywatna|
|KtoTo ma dostęp?|Wszyscy w organizacji, w tym użytkownicy B2B.|Tylko członkowie zespołu. Inne osoby mogą zażądać dostępu do skojarzonej witryny.|Tylko członkowie zespołu.|Tylko członkowie zespołu.|
|Kanały prywatne|Właściciele i członkowie mogą tworzyć kanały prywatne|Właściciele i członkowie mogą tworzyć kanały prywatne|Tylko właściciele mogą tworzyć kanały prywatne|Tylko właściciele mogą tworzyć kanały prywatne|
|Kanały udostępnione|Właściciele i członkowie mogą tworzyć kanały udostępnione|Właściciele i członkowie mogą tworzyć kanały udostępnione|Tylko właściciele mogą tworzyć kanały udostępnione|Tylko właściciele mogą tworzyć kanały udostępnione|
|Dostęp gości na poziomie witryny|**Nowi i istniejący goście** (domyślnie).|**Nowi i istniejący goście** (domyślnie).|**Nowi i istniejący goście** lub **Tylko osoby w Twojej organizacji w** zależności od potrzeb zespołu.|**Nowi i istniejący goście** lub **Tylko osoby w Twojej organizacji w** zależności od potrzeb zespołu.|
|Ustawienia udostępniania witryn|**Właściciele i członkowie witryny oraz osoby z** uprawnieniami do edytowania mogą udostępniać pliki i foldery, ale tylko właściciele witryn mogą udostępniać witrynę.|**Właściciele i członkowie witryny oraz osoby z** uprawnieniami do edytowania mogą udostępniać pliki i foldery, ale tylko właściciele witryn mogą udostępniać witrynę.|**Właściciele i członkowie witryny oraz osoby z** uprawnieniami do edytowania mogą udostępniać pliki i foldery, ale tylko właściciele witryn mogą udostępniać witrynę.|**Tylko właściciele witryny mogą udostępniać pliki, foldery i witrynę**.<br>Żądania dostępu **są wyłączone**.|
|Niezamanektowany dostęp do urządzenia na poziomie witryny|**Pełny dostęp z aplikacji klasycznych, aplikacji mobilnych i Internetu** (domyślnie).|**Pełny dostęp z aplikacji klasycznych, aplikacji mobilnych i Internetu** (domyślnie).|**Zezwalaj na ograniczony dostęp tylko w sieci Web**.|**Blokowanie dostępu**.|
|Domyślny typ linku udostępniania|**Tylko osoby w Twojej organizacji**|**Tylko osoby w Twojej organizacji**|**Określone osoby**|**Osoby z istniejącym dostępem**|
|Etykiety wrażliwości|Brak|Brak|Etykieta wrażliwości używana do klasyfikowania zespołu i kontrolowania udostępniania gościa oraz niezakieregotowego dostępu do urządzenia.|Etykieta wrażliwości używana do klasyfikowania zespołu i kontrolowania udostępniania gościa oraz niezakieregotowego dostępu do urządzenia. Etykieta może być także używana do szyfrowania plików.|

Odmiana opcji Wysoce wrażliwa, Teams [izolacji](secure-teams-security-isolation.md) zabezpieczeń używa unikatowej etykiety wrażliwości dla jednego zespołu, co zapewnia dodatkowe bezpieczeństwo. Za pomocą tej etykiety możesz szyfrować pliki i tylko członkowie tego zespołu będą mogli je odczytywać.

Ochrona podstawowa obejmuje zespoły publiczne i prywatne. Zespoły publiczne mogą być odkryte i dostępne dla każdego użytkownika w organizacji. Prywatne zespoły mogą być odkryte i dostępne tylko dla członków zespołu. Obie te konfiguracje ograniczają udostępnianie skojarzonej SharePoint witrynie zespołu, aby pomóc w zarządzaniu uprawnieniami.

Teams ochrony poufnej i bardzo poufnej to prywatne zespoły, w których udostępnianie i żądanie dostępu do skojarzonej witryny jest ograniczone, a etykiety wrażliwości służą do ustawiania zasad związanych z udostępnianiem gości, dostępem do urządzeń i szyfrowaniem zawartości.

## <a name="sensitivity-labels"></a>Etykiety wrażliwości

Poufne i wysoce poufne warstwy chronią zespół i jego pliki za pomocą etykiet wrażliwości. Aby zaimplementować te warstwy, należy włączyć etykiety wrażliwości, aby chronić zawartość w Microsoft Teams[, Office 365 grupy i SharePoint witrynach](../compliance/sensitivity-labels-teams-groups-sites.md).

Podczas gdy warstwa podstawowa nie wymaga etykiet wrażliwości, rozważ utworzenie etykiety "ogólne", a następnie wymaganie oznaczenia wszystkich zespołów. Dzięki temu użytkownicy będą mieli możliwość korzystania z opcji wrażliwości podczas tworzenia zespołu. Jeśli planujesz wdrożyć poufne lub wysoce poufne warstwy, zalecamy utworzenie etykiety "ogólne", która będzie używać dla zespołów planu bazowego i dla plików, które nie są poufne.

Jeśli nie masz jeszcze pomysłu na używanie etykiet wrażliwości, zalecamy zapoznanie się z wprowadzeniem do etykiet [wrażliwości](../compliance/get-started-with-sensitivity-labels.md) . 

Jeśli w organizacji wpisano już etykiety wrażliwości, zastanów się, w jaki sposób etykiety używane na wrażliwych i wysoce poufnych warstwach są wpasowane w ogólną strategię etykiet. 

## <a name="sharing-the-sharepoint-site"></a>Udostępnianie SharePoint sieci Web

Z każdym zespołem jest skojarzona SharePoint, w której są przechowywane dokumenty. (To jest karta **Pliki** w kanale zespołu). Witryna SharePoint zachowuje własne zarządzanie uprawnieniami, ale jest połączona z uprawnieniami zespołu. Właściciele zespołu są uwzględniani jako właściciele witryn, a członkowie zespołu są uwzględniani jako członkowie witryny w skojarzonej witrynie.

Uprawnienia wynikające z tego umożliwiają:

- Właściciele witrynie mogą administrować witryną i mieć pełną kontrolę nad jej zawartością.
- Członkowie zespołu mogą tworzyć i edytować pliki w witrynie. 

Domyślnie właściciele i członkowie zespołu mogą udostępniać witrynę osobom spoza zespołu bez dodawania ich do zespołu. Zalecamy użycie tej aplikacji, ponieważ komplikuje zarządzanie użytkownikami i może prowadzić do osób, które nie są członkami zespołu, które nie mają dostępu do plików zespołu, nie zdając sobie z tego sprawę. Aby temu zapobiec, począwszy od poziomu ochrony według planu bazowego, zalecamy, aby tylko właściciele mogli udostępniać witrynę bezpośrednio.

Mimo że zespoły nie mają opcji uprawnień tylko do odczytu, witryna SharePoint dostępna. Jeśli masz uczestników projektu z grupami partnerów, którzy muszą mieć możliwość wyświetlania plików zespołu, ale nie edytowania ich, rozważ dodanie ich bezpośrednio do witryny SharePoint z uprawnieniami do odczytu.

## <a name="sharing-files-and-folders"></a>Udostępnianie plików i folderów

Domyślnie właściciele i członkowie zespołu mogą udostępniać pliki i foldery osobom spoza zespołu. Może to dotyczyć osób spoza twojej organizacji, jeśli zezwolisz na udostępnianie gości. We wszystkich trzech warstwach aktualizujemy domyślny typ linku udostępniania, aby zapobiec przypadkowemu zasłaniu. W przypadku bardzo poufnej warstwy takie udostępnianie jest ograniczane tylko do właścicieli zespołu.

## <a name="sharing-with-people-outside-your-organization"></a>Udostępnianie osobom spoza organizacji

Jeśli chcesz udostępnić Teams osobom spoza organizacji, dostępne są dwie opcje:

- **Udostępnianie gości —** funkcja udostępniania gościa korzysta z współpracy B2B w usłudze Azure AD, która umożliwia użytkownikom udostępnianie plików, folderów, witryn, grup i zespołów osobom spoza organizacji. Te osoby uzyskają dostęp do zasobów udostępnionych przy użyciu kont gości w Twoim katalogu.
- **Kanały udostępnione** — w kanałach udostępnionych jest używana funkcja bezpośredniego połączenia B2B w usłudze Azure AD, która umożliwia użytkownikom udostępnianie zasobów w organizacji osobom z innych organizacji korzystających z usługi Azure AD. Te osoby uzyskają dostęp do kanałów udostępnionych Teams za pomocą własnego konta służbowego. W Twojej organizacji nie jest tworzone żadne konto gościa.

W zależności od sytuacji zarówno udostępnianie gości, jak i kanały udostępnione są przydatne. Zobacz [Planowanie współpracy zewnętrznej](plan-external-collaboration.md) , aby uzyskać szczegółowe informacje na temat każdego z nich i zdecydować, którego z nich użyć w danym scenariuszu.

Jeśli planujesz korzystać z udostępniania gościa, zalecamy skonfigurowanie integracji usług SharePoint i OneDrive z usługą [Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) w celu jak najlepszego udostępniania i obsługi administracyjnej.

Teams udostępniania gościa jest domyślnie włączone, ale w razie potrzeby możesz je wyłączyć na poufnych i wysoce poufnych warstwach, używając etykiety wrażliwości. Kanały udostępnione są domyślnie włączone, ale wymaga to skonfigurowania relacji między organizacjami dla każdej organizacji, z którą chcesz współpracować. Aby [uzyskać szczegółowe informacje, zobacz Współpraca z uczestnikami zewnętrznymi w kanale](collaborate-teams-direct-connect.md) .

W bardzo poufnej warstwie konfigurujemy etykietę wrażliwości w celu szyfrowania plików, do których jest stosowana. Jeśli potrzebujesz dostępu gości do tych plików, musisz nadać im uprawnienia podczas tworzenia etykiety. Uczestnicy zewnętrzni w kanałach udostępnionych nie mogą mieć uprawnień do etykiet wrażliwości i nie mogą uzyskać dostępu do zawartości zaszyfrowanej za pomocą etykiety wrażliwości.

Zdecydowanie zalecamy pozostawienie udostępniania gościa dla warstwy podstawowej oraz dla warstw poufnych lub bardzo poufnych, jeśli musisz współpracować z osobami spoza organizacji. Funkcje udostępniania gości w programie Microsoft 365 zapewniają o wiele bezpieczniejsze i lepiej regulalne udostępnianie niż wysyłanie plików jako załączników w wiadomościach e-mail. Pozwala również zmniejszyć ryzyko cienia it, w którym użytkownicy używają odtajonych produktów konsumenckich w celu udostępniania ich zewnętrznym współpracownikom.

Jeśli regularnie współpracujesz z innymi organizacjami, które korzystają z usługi Azure AD, dobrym rozwiązaniem może być korzystanie z kanałów udostępnionych. Kanały udostępnione są bezproblemowo wyświetlane w kliencie poczty Teams drugiej organizacji i umożliwiają uczestnikom zewnętrznym korzystanie ze swoich zwykłych kont użytkowników w organizacji zamiast konieczności logowania się osobno przy użyciu konta gościa.

Zapoznaj się z poniższymi odwołaniami, aby utworzyć bezpieczne i produktywne środowisko udostępniania gościa dla organizacji:

- [Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytanych użytkownikom](best-practices-anonymous-sharing.md)
- [Ograniczanie przypadkowego udostępnienia plików osobom spoza organizacji](share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gości](create-secure-guest-sharing-environment.md)

## <a name="access-from-unmanaged-devices"></a>Dostęp z urządzeń niezamanektowych

W przypadku warstw poufnych i bardzo poufnych dostęp do zawartości SharePoint etykietami wrażliwości. Dostęp warunkowy usługi Azure AD oferuje wiele opcji określania sposobu uzyskiwania dostępu do usługi Microsoft 365, w tym ograniczeń dotyczących lokalizacji, ryzyka, zgodności urządzenia i innych czynników. Zalecamy przeczytanie [tematu Co to jest dostęp warunkowy?](/azure/active-directory/conditional-access/overview) i rozważenie, które dodatkowe zasady mogą być odpowiednie dla Twojej organizacji.

Goście często nie mają urządzeń zarządzanych przez Twoją organizację. Jeśli zezwalasz gościom na dostęp do dowolnej warstwy, rozważ, jakiego rodzaju urządzeń będą oni używać do uzyskiwania dostępu do zespołów i witryn oraz odpowiednio ustawiać zasady dotyczące urządzeń niezawiązywanych.

### <a name="control-device-access-across-microsoft-365"></a>Kontrolowanie dostępu do urządzenia na Microsoft 365

Ustawienie urządzeń niezamanektowych na etykietach wrażliwości ma wpływ tylko na SharePoint dostępu. Jeśli chcesz rozszerzyć kontrolę nad urządzeniami, na których nie są zainstalowane SharePoint, możesz zamiast tego utworzyć zasady dostępu warunkowego programu [Azure Active Directory](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device) dla wszystkich aplikacji i usług w organizacji. Aby skonfigurować te zasady w szczególności [Microsoft 365,](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365) wybierz aplikację w **Office 365** w obszarze **Aplikacje lub akcje w chmurze**.

![Zrzut ekranu przedstawiający aplikację Office 365 w chmurze w Azure Active Directory dostępu warunkowego.](/sharepoint/sharepointonline/media/azure-ca-office365-policy.png)

Korzystanie z zasad mających wpływ na wszystkie Microsoft 365 może prowadzić do lepszej ochrony i lepszej jakości obsługi dla użytkowników. Na przykład w przypadku zablokowania dostępu do urządzeń nieza zarządzania tylko w usłudze SharePoint użytkownicy mogą uzyskać dostęp do czatu w zespole za pomocą urządzenia nieza zarządzania, ale utracą dostęp, gdy próbują uzyskać dostęp do karty Pliki. Korzystanie  z aplikacji w chmurze Office 365 pomaga uniknąć problemów ze współzależnościami [usługi.](/azure/active-directory/conditional-access/service-dependencies)

## <a name="next-step"></a>Następny krok

Zacznij od [skonfigurowania poziomu ochrony według planu bazowego](configure-teams-baseline-protection.md). W razie potrzeby możesz dodać [ochronę ważnych i](configure-teams-sensitive-protection.md) [bardzo wrażliwą](configure-teams-highly-sensitive-protection.md) na wierzchu planu bazowego.

## <a name="see-also"></a>Zobacz też

[Zabezpieczenia i zgodność z przepisami w Microsoft Teams](/microsoftteams/security-compliance-overview)

[Zasady alertów w centrum zabezpieczeń i zgodności](../compliance/alert-policies.md)
