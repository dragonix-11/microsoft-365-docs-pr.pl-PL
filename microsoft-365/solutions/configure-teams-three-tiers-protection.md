---
title: Konfigurowanie Teams z trzema warstwami zabezpieczeń udostępniania plików
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
description: Dowiedz się, jak skonfigurować Teams w celu zapewnienia lepszych zabezpieczeń udostępniania plików przy użyciu trzech warstw ochrony, równoważąc zabezpieczenia z łatwością współpracy.
ms.openlocfilehash: 4d287d342371a8182a4c9de5742d2d45ca01a1c6
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012478"
---
# <a name="configure-teams-with-three-tiers-of-protection"></a>Konfigurowanie Teams z trzema warstwami ochrony

Artykuły z tej serii zawierają zalecenia dotyczące konfigurowania zespołów w Microsoft Teams i skojarzonych z nimi witryn SharePoint na potrzeby ochrony plików, która równoważy bezpieczeństwo z łatwością współpracy.

W tym artykule zdefiniowano cztery różne konfiguracje, począwszy od zespołu publicznego z najbardziej otwartymi zasadami udostępniania. Każda dodatkowa konfiguracja stanowi znaczący krok w zakresie ochrony, podczas gdy możliwość dostępu do plików przechowywanych w zespołach i współpracy nad nimi jest ograniczona do odpowiedniego zestawu członków zespołu. 

Konfiguracje w tym artykule są zgodne z zaleceniami firmy Microsoft dotyczącymi trzech warstw ochrony danych, tożsamości i urządzeń:

- Ochrona według planu bazowego

- ochrona poufna

- Wysoce wrażliwa ochrona

Aby uzyskać więcej informacji na temat tych warstw i możliwości zalecanych dla każdej warstwy, zobacz [Ilustracje dotyczące architektury chmury firmy Microsoft dla przedsiębiorstw](./cloud-architecture-models.md)

## <a name="three-tiers-at-a-glance"></a>Trzy warstwy w skrócie

Poniższa tabela zawiera podsumowanie konfiguracji dla każdej warstwy. Użyj tych konfiguracji jako zaleceń punktu początkowego i dostosuj konfiguracje do potrzeb organizacji. Może nie być potrzebna każda warstwa.

|&nbsp;|Punkt odniesienia (publiczny)|Plan bazowy (prywatny)|Wrażliwe|Wysoce wrażliwe|
|:-----|:-----|:-----|:-----|:-----|
|Zespół prywatny lub publiczny|Publicznego|Prywatny|Prywatny|Prywatny|
|KtoTo ma dostęp?|Wszyscy w organizacji, w tym użytkownicy B2B.|Tylko członkowie zespołu. Inne osoby mogą zażądać dostępu do skojarzonej witryny.|Tylko członkowie zespołu.|Tylko członkowie zespołu.|
|Kanały prywatne|Właściciele i członkowie mogą tworzyć kanały prywatne|Właściciele i członkowie mogą tworzyć kanały prywatne|Tylko właściciele mogą tworzyć kanały prywatne|Tylko właściciele mogą tworzyć kanały prywatne|
|Kanały udostępnione|Właściciele i członkowie mogą tworzyć kanały udostępnione|Właściciele i członkowie mogą tworzyć kanały udostępnione|Tylko właściciele mogą tworzyć kanały udostępnione|Tylko właściciele mogą tworzyć kanały udostępnione|
|Dostęp gościa na poziomie witryny|**Nowi i istniejący goście** (domyślnie).|**Nowi i istniejący goście** (domyślnie).|**Nowi i istniejący goście** lub **tylko osoby w organizacji w** zależności od potrzeb zespołu.|**Nowi i istniejący goście** lub **tylko osoby w organizacji w** zależności od potrzeb zespołu.|
|Ustawienia udostępniania witryny|**Właściciele i członkowie witryny oraz osoby z uprawnieniami do edycji mogą udostępniać pliki i foldery, ale tylko właściciele witryn mogą udostępniać witrynę**.|**Właściciele i członkowie witryny oraz osoby z uprawnieniami do edycji mogą udostępniać pliki i foldery, ale tylko właściciele witryn mogą udostępniać witrynę**.|**Właściciele i członkowie witryny oraz osoby z uprawnieniami do edycji mogą udostępniać pliki i foldery, ale tylko właściciele witryn mogą udostępniać witrynę**.|**Tylko właściciele witryn mogą udostępniać pliki, foldery i witrynę**.<br>Żądania dostępu **wyłączone**.|
|Dostęp do urządzeń niezarządzanych na poziomie lokacji|**Pełny dostęp z aplikacji klasycznych, aplikacji mobilnych i internetu (domyślnie** ).|**Pełny dostęp z aplikacji klasycznych, aplikacji mobilnych i internetu (domyślnie** ).|**Zezwalaj na ograniczony dostęp tylko do Internetu**.|**Blokuj dostęp**.|
|Domyślny typ łącza udostępniania|**Tylko osoby w organizacji**|**Tylko osoby w organizacji**|**Określone osoby**|**Osoby z istniejącym dostępem**|
|Etykiety wrażliwości|Brak|Brak|Etykieta poufności używana do klasyfikowania zespołu i kontrolowania udostępniania gościa i niezarządzanego dostępu do urządzenia.|Etykieta poufności używana do klasyfikowania zespołu i kontrolowania udostępniania gościa i niezarządzanego dostępu do urządzenia. Etykieta może być również używana w plikach do szyfrowania plików.|

Odmiana opcji Wysoce wrażliwe Teams [z izolacją zabezpieczeń](secure-teams-security-isolation.md) używa unikatowej etykiety poufności dla jednego zespołu, która zapewnia dodatkowe zabezpieczenia. Możesz użyć tej etykiety do szyfrowania plików, a tylko członkowie tego zespołu będą mogli je odczytać.

Ochrona według planu bazowego obejmuje zespoły publiczne i prywatne. Zespoły publiczne mogą być odnalezione i dostępne dla wszystkich osób w organizacji. Prywatne zespoły mogą być odnalezione i dostępne tylko dla członków zespołu. Obie te konfiguracje ograniczają udostępnianie skojarzonej SharePoint lokacji do właścicieli zespołów, aby ułatwić zarządzanie uprawnieniami.

Teams ochrony poufnej i wysoce wrażliwej to zespoły prywatne, w których udostępnianie i żądanie dostępu do skojarzonej witryny jest ograniczone, a etykiety poufności są używane do ustawiania zasad dotyczących udostępniania gościa, dostępu do urządzeń i szyfrowania zawartości.

## <a name="sensitivity-labels"></a>Etykiety wrażliwości

Warstwy wrażliwe i wysoce wrażliwe używają etykiet poufności, aby pomóc w zabezpieczeniu zespołu i jego plików. Aby zaimplementować te warstwy, należy włączyć [etykiety poufności, aby chronić zawartość w witrynach Microsoft Teams, Office 365 i SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

Chociaż warstwa odniesienia nie wymaga etykiet poufności, rozważ utworzenie etykiety "ogólne", a następnie wymaganie, aby wszystkie zespoły były oznaczone etykietą. Pomoże to zapewnić, że użytkownicy dokonają świadomego wyboru poufności podczas tworzenia zespołu. Jeśli planujesz wdrożenie warstw poufnych lub wysoce poufnych, zalecamy utworzenie etykiety "ogólnej", która będzie używana dla zespołów odniesienia i plików, które nie są poufne.

Jeśli dopiero zaczynasz korzystać z etykiet poufności, zalecamy przeczytanie [Wprowadzenie z etykietami poufności](../compliance/get-started-with-sensitivity-labels.md), aby rozpocząć pracę. 

Jeśli etykiety poufności zostały już wdrożone w organizacji, rozważ, w jaki sposób etykiety używane w warstwach poufnych i wysoce wrażliwych pasują do ogólnej strategii etykiet. 

## <a name="sharing-the-sharepoint-site"></a>Udostępnianie witryny SharePoint

Każdy zespół ma skojarzoną witrynę SharePoint, w której przechowywane są dokumenty. (Jest to karta **Pliki** w kanale usługi Teams). Witryna SharePoint zachowuje własne zarządzanie uprawnieniami, ale jest połączona z uprawnieniami zespołu. Właściciele zespołu są uwzględniane jako właściciele witryny i członkowie zespołu są uwzględniane jako członkowie witryny w skojarzonej witrynie.

Wynikające z tego uprawnienia umożliwiają:

- Właściciele zespołu do administrowania witryną i mają pełną kontrolę nad zawartością witryny.
- Członkowie zespołu będą tworzyć i edytować pliki w witrynie. 

Domyślnie właściciele i członkowie zespołu mogą udostępniać witrynę osobom spoza zespołu bez dodawania ich do zespołu. Zalecamy, aby rozwiązać ten problem, ponieważ komplikuje to zarządzanie użytkownikami i może prowadzić do tego, że osoby, które nie są członkami zespołu, mają dostęp do plików zespołu bez realizacji tego przez właścicieli zespołu. Aby temu zapobiec, począwszy od poziomu bazowego ochrony, zalecamy, aby tylko właściciele mogli bezpośrednio udostępniać witrynę.

Chociaż zespoły nie mają opcji uprawnień tylko do odczytu, witryna SharePoint. Jeśli masz interesariuszy grup partnerów, którzy muszą mieć możliwość wyświetlania plików zespołu, ale ich nie edytują, rozważ dodanie ich bezpośrednio do witryny SharePoint z uprawnieniami do odczytu.

## <a name="sharing-files-and-folders"></a>Udostępnianie plików i folderów

Domyślnie zarówno właściciele, jak i członkowie zespołu mogą udostępniać pliki i foldery osobom spoza zespołu. Może to obejmować osoby spoza organizacji, jeśli zezwolisz na udostępnianie gości. We wszystkich trzech warstwach aktualizujemy domyślny typ linku udostępniania, aby uniknąć przypadkowego nadmiernego udostępniania. W wysoce wrażliwej warstwie takie udostępnianie jest ograniczane tylko do właścicieli zespołów.

## <a name="sharing-with-people-outside-your-organization"></a>Udostępnianie osobom spoza organizacji

Jeśli musisz udostępnić zawartość Teams osobom spoza organizacji, dostępne są dwie opcje:

- **Udostępnianie gości** — udostępnianie gości używa Azure AD współpracy B2B, która umożliwia użytkownikom udostępnianie plików, folderów, witryn, grup i zespołów osobom spoza organizacji. Te osoby uzyskują dostęp do udostępnionych zasobów przy użyciu kont gościa w katalogu.
- **Kanały udostępnione** — kanały udostępnione korzystają z Azure AD bezpośredniego połączenia B2B, co umożliwia użytkownikom udostępnianie zasobów w organizacji osobom z innych organizacji Azure AD. Te osoby uzyskują dostęp do udostępnionych kanałów w Teams przy użyciu własnego konta służbowego. W organizacji nie jest tworzone żadne konto gościa.

Udostępnianie gościa i kanały udostępnione są przydatne w zależności od sytuacji. Zobacz [Planowanie współpracy zewnętrznej](plan-external-collaboration.md) , aby uzyskać szczegółowe informacje na temat każdego z nich i jak zdecydować, którego użyć w danym scenariuszu.

Jeśli planujesz korzystać z udostępniania gości, zalecamy skonfigurowanie [integracji SharePoint i OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview), aby uzyskać najlepsze środowisko udostępniania i administrowania.

Teams udostępnianie gościa jest domyślnie włączone, ale można je wyłączyć w razie potrzeby w warstwach poufnych i wysoce poufnych przy użyciu etykiety poufności. Kanały udostępnione są domyślnie włączone, ale wymagają skonfigurowania relacji między organizacjami dla każdej organizacji, z którą chcesz współpracować. Aby uzyskać szczegółowe informacje, zobacz [Współpraca z uczestnikami zewnętrznymi w kanale](collaborate-teams-direct-connect.md) .

W warstwie wysoce wrażliwej konfigurujemy etykietę poufności w celu szyfrowania plików, do których jest stosowana. Jeśli potrzebujesz gości, aby mieć dostęp do tych plików, musisz przyznać im uprawnienia podczas tworzenia etykiety. Uczestnicy zewnętrzni w kanałach udostępnionych nie mogą mieć uprawnień do etykiet poufności i nie mogą uzyskiwać dostępu do zawartości zaszyfrowanej za pomocą etykiety poufności.

Zdecydowanie zalecamy pozostawienie udostępniania gościa dla warstwy odniesienia i warstw poufnych lub wysoce poufnych, jeśli musisz współpracować z osobami spoza organizacji. Funkcje udostępniania gościa w Microsoft 365 zapewniają znacznie bezpieczniejsze i zarządzane środowisko udostępniania niż wysyłanie plików jako załączników w wiadomościach e-mail. Zmniejsza to również ryzyko w tle IT, gdzie użytkownicy używają niezarządzonych produktów konsumenckich do udostępniania legalnym współpracownikom zewnętrznym.

Jeśli regularnie współpracujesz z innymi organizacjami korzystającymi z Azure AD, dobrym rozwiązaniem mogą być kanały udostępnione. Kanały udostępnione są bezproblemowo wyświetlane w kliencie Teams innej organizacji i umożliwiają uczestnikom zewnętrznym korzystanie z ich zwykłego konta użytkownika w organizacji zamiast logowania się osobno przy użyciu konta gościa.

Zapoznaj się z następującymi odwołaniami, aby utworzyć bezpieczne i produktywne środowisko udostępniania gości dla organizacji:

- [Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytelnionym użytkownikom](best-practices-anonymous-sharing.md)
- [Ograniczanie przypadkowego narażenia na pliki podczas udostępniania osobom spoza organizacji](share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gościa](create-secure-guest-sharing-environment.md)

## <a name="access-from-unmanaged-devices"></a>Dostęp z urządzeń niezarządzanych

W przypadku warstw poufnych i wysoce poufnych ograniczamy dostęp do zawartości SharePoint z etykietami poufności. Azure AD dostęp warunkowy oferuje wiele opcji określania, w jaki sposób użytkownicy uzyskują dostęp do Microsoft 365, w tym ograniczenia dotyczące lokalizacji, ryzyka, zgodności urządzeń i innych czynników. Zalecamy [przeczytanie tematu Co to jest dostęp warunkowy?](/azure/active-directory/conditional-access/overview) i rozważenie, które dodatkowe zasady mogą być odpowiednie dla Twojej organizacji.

Należy pamiętać, że goście często nie mają urządzeń zarządzanych przez organizację. Jeśli zezwolisz gościom w dowolnej warstwie, zastanów się, jakiego rodzaju urządzenia będą używać do uzyskiwania dostępu do zespołów i witryn oraz odpowiednio ustawić zasady urządzeń niezarządzanych.

### <a name="control-device-access-across-microsoft-365"></a>Kontrolowanie dostępu do urządzeń w Microsoft 365

Ustawienie urządzeń niezarządzanych w etykietach poufności ma wpływ tylko na dostęp SharePoint. Jeśli chcesz rozszerzyć kontrolę nad urządzeniami niezarządzanych poza SharePoint, możesz zamiast tego [utworzyć zasady dostępu warunkowego Azure Active Directory dla wszystkich aplikacji i usług w organizacji](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). Aby skonfigurować te zasady specjalnie dla [usług Microsoft 365](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365), wybierz aplikację **w chmurze Office 365** w obszarze **Aplikacje lub akcje w chmurze**.

![Zrzut ekranu przedstawiający aplikację w chmurze Office 365 w zasadach dostępu warunkowego Azure Active Directory.](/sharepoint/sharepointonline/media/azure-ca-office365-policy.png)

Korzystanie z zasad, które mają wpływ na wszystkie usługi Microsoft 365, może prowadzić do lepszych zabezpieczeń i lepszego środowiska dla użytkowników. Jeśli na przykład blokujesz dostęp do urządzeń niezarządzanych tylko w SharePoint, użytkownicy mogą uzyskiwać dostęp do czatu w zespole z urządzeniem niezarządzanym, ale utracą dostęp podczas próby uzyskania dostępu do karty **Pliki**. Korzystanie z aplikacji w chmurze Office 365 pomaga uniknąć problemów z [zależnościami usług](/azure/active-directory/conditional-access/service-dependencies).

## <a name="next-step"></a>Następny krok

Rozpocznij od [skonfigurowania poziomu ochrony punktu odniesienia](configure-teams-baseline-protection.md). W razie potrzeby można dodać [ochronę poufną](configure-teams-sensitive-protection.md) i [wysoce wrażliwą ochronę](configure-teams-highly-sensitive-protection.md) na początku punktu odniesienia.

## <a name="see-also"></a>Zobacz też

[Zabezpieczenia i zgodność w Microsoft Teams](/microsoftteams/security-compliance-overview)

[Zasady alertów](../compliance/alert-policies.md)
