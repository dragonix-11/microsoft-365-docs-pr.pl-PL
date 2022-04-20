---
title: Zero Trust konfiguracji tożsamości i dostępu do urządzeń — Microsoft 365 dla przedsiębiorstw
description: Opis zaleceń i podstawowych pojęć firmy Microsoft dotyczących wdrażania zasad i konfiguracji bezpiecznej poczty e-mail, dokumentów i aplikacji dla Zero Trust.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-overview
- m365solution-zero-trust
ms.technology: mdo
ms.openlocfilehash: 066fc33bb5047c354fa6a4b3d954387fdfeae2e9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947786"
---
# <a name="zero-trust-identity-and-device-access-configurations"></a>Zero Trust konfiguracji tożsamości i dostępu do urządzeń

Architektury zabezpieczeń korzystające z zapór sieciowych i wirtualnych sieci prywatnych (VPN) do izolowania i ograniczania dostępu do zasobów i usług technologicznych organizacji nie są już wystarczające dla pracowników, którzy regularnie wymagają dostępu do aplikacji i zasobów, które istnieją poza tradycyjnymi granicami sieci firmowej.

Aby rozwiązać ten nowy świat przetwarzania, firma Microsoft zdecydowanie zaleca model zabezpieczeń Zero Trust, który jest oparty na następujących zasadach przewodnich:

- Jawne weryfikowanie

  Zawsze uwierzytelniaj się i autoryzuj na podstawie wszystkich dostępnych punktów danych. W tym miejscu zasady Zero Trust tożsamości i dostępu do urządzeń mają kluczowe znaczenie dla logowania i ciągłej weryfikacji.

- Korzystanie z dostępu z najniższymi uprawnieniami

  Ogranicz dostęp użytkowników za pomocą funkcji just in time i just-enough-access (JIT/JEA), zasad adaptacyjnych opartych na ryzyku i ochrony danych.

- Załóżmy, że naruszenie

  Minimalizuj promień wybuchu i dostęp do segmentu. Zweryfikuj kompleksowe szyfrowanie i użyj analizy, aby uzyskać widoczność, zwiększyć wykrywanie zagrożeń i ulepszyć ochronę.

Oto ogólna architektura Zero Trust.

:::image type="content" source="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png" alt-text="Architektura Zero Trust firmy Microsoft" lightbox="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png":::

Zero Trust zasady dostępu do tożsamości i urządzeń dotyczą zasady **Jawne** sprawdzanie identyfikatora guid dla:

- Tożsamości

  Gdy tożsamość próbuje uzyskać dostęp do zasobu, sprawdź tę tożsamość przy użyciu silnego uwierzytelniania i upewnij się, że żądany dostęp jest zgodny i typowy.

- Urządzenia (nazywane również punktami końcowymi)

  Monitorowanie i wymuszanie wymagań dotyczących kondycji i zgodności urządzeń w celu zapewnienia bezpiecznego dostępu.

- Aplikacje

  Stosowanie kontrolek i technologii w celu odnajdywania w tle akcji IT, zapewniania odpowiednich uprawnień w aplikacji, uzyskiwania dostępu w oparciu o analizę w czasie rzeczywistym, monitorowania nietypowego zachowania, kontrolowania akcji użytkownika i weryfikowania bezpiecznych opcji konfiguracji.

W tej serii artykułów opisano zestaw konfiguracji wymagań wstępnych dotyczących tożsamości i dostępu do urządzeń oraz zestaw dostępu warunkowego Azure Active Directory (Azure AD), Microsoft Intune i innych zasad Zero Trust dostępu do Microsoft 365  dla aplikacji i usług w chmurze dla przedsiębiorstw, innych usług SaaS i aplikacji lokalnych opublikowanych w usłudze Azure AD serwer proxy aplikacji.

Zero Trust ustawienia i zasady dostępu do tożsamości i urządzeń są zalecane w trzech warstwach: punkt początkowy, przedsiębiorstwo i wyspecjalizowane zabezpieczenia dla środowisk z wysoce regulowanymi lub sklasyfikowanymi danymi. Te warstwy i odpowiednie konfiguracje zapewniają spójne poziomy Zero Trust ochrony danych, tożsamości i urządzeń.

Te możliwości i ich zalecenia:

- Są obsługiwane w Microsoft 365 E3 i Microsoft 365 E5.
- Są dostosowane do [wskaźnika bezpieczeństwa firmy Microsoft](../defender/microsoft-secure-score.md) oraz [oceny tożsamości w usłudze Azure AD](/azure/active-directory/fundamentals/identity-secure-score) i zwiększają te wyniki w organizacji.
- Ułatwi to zaimplementowanie tych [pięciu kroków w celu zabezpieczenia infrastruktury tożsamości](/azure/security/azure-ad-secure-steps).

Jeśli Twoja organizacja ma unikatowe wymagania środowiskowe lub złożoność, skorzystaj z tych zaleceń jako punktu wyjścia. Jednak większość organizacji może zaimplementować te zalecenia zgodnie z zaleceniami.

Obejrzyj ten film wideo, aby zapoznać się z szybkim omówieniem konfiguracji tożsamości i dostępu do urządzeń dla Microsoft 365 dla przedsiębiorstw.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxEDQ]

> [!NOTE]
> Firma Microsoft sprzedaje również licencje Enterprise Mobility + Security (EMS) dla subskrypcji Office 365. Możliwości EMS E3 i EMS E5 są równoważne możliwościom Microsoft 365 E3 i Microsoft 365 E5. Aby uzyskać szczegółowe informacje [, zobacz Plany pakietu EMS](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/compare-plans-and-pricing) .

## <a name="intended-audience"></a>Odbiorcy

Te zalecenia są przeznaczone dla architektów przedsiębiorstwa i specjalistów IT, którzy znają Microsoft 365 usługach produktywności i zabezpieczeń w chmurze, w tym usługi Azure AD (tożsamość), Microsoft Intune (zarządzanie urządzeniami) i Microsoft Purview Information Protection (ochrona danych).

### <a name="customer-environment"></a>Środowisko klienta

Zalecane zasady mają zastosowanie do organizacji korporacyjnych działających zarówno w całości w chmurze firmy Microsoft, jak i dla klientów z infrastrukturą tożsamości hybrydowej, która jest lasem usług lokalna usługa Active Directory Domain Services (AD DS) synchronizowanym z dzierżawą usługi Azure AD.

Wiele z podanych zaleceń opiera się na usługach dostępnych tylko z Microsoft 365 E5, Microsoft 365 E3 z dodatkiem E5 Security, licencjami EMS E5 lub Azure AD — wersja Premium P2.

W przypadku tych organizacji, które nie mają tych licencji, firma Microsoft zaleca co najmniej [zaimplementowanie wartości domyślnych zabezpieczeń](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), które są dołączone do wszystkich planów Microsoft 365.

### <a name="caveats"></a>Zastrzeżenia

Twoja organizacja może podlegać przepisom lub innym wymaganiom dotyczącym zgodności, w tym konkretnym rekomendacjom, które mogą wymagać zastosowania zasad, które różnią się od tych zalecanych konfiguracji. Te konfiguracje zalecają kontrolki użycia, które nie były w przeszłości dostępne. Zalecamy te mechanizmy kontroli, ponieważ uważamy, że stanowią one równowagę między bezpieczeństwem a produktywnością.

Zrobiliśmy wszystko, co w naszej mocy, aby uwzględnić szeroką gamę wymagań dotyczących ochrony organizacji, ale nie możemy uwzględnić wszystkich możliwych wymagań ani wszystkich unikatowych aspektów organizacji.

## <a name="three-tiers-of-protection"></a>Trzy warstwy ochrony

Większość organizacji ma określone wymagania dotyczące zabezpieczeń i ochrony danych. Wymagania te różnią się w zależności od segmentu branżowego i funkcji zadań w organizacjach. Na przykład dział prawny i administratorzy mogą wymagać dodatkowych mechanizmów kontroli zabezpieczeń i ochrony informacji dotyczących korespondencji e-mail, które nie są wymagane dla innych jednostek biznesowych.

Każda branża ma również własny zestaw wyspecjalizowanych przepisów. Zamiast udostępniać listę wszystkich możliwych opcji zabezpieczeń lub rekomendacji dla segmentu branżowego lub funkcji zadania, przedstawiono zalecenia dotyczące trzech różnych poziomów zabezpieczeń i ochrony, które mogą być stosowane na podstawie stopnia szczegółowości twoich potrzeb.

- **Punkt początkowy**: Zalecamy, aby wszyscy klienci ustanawiali i korzystali z minimalnego standardu ochrony danych, a także tożsamości i urządzeń uzyskujących dostęp do danych. Możesz postępować zgodnie z tymi zaleceniami, aby zapewnić silną domyślną ochronę jako punkt wyjścia dla wszystkich organizacji.
- **Enterprise**: Niektórzy klienci mają podzestaw danych, które muszą być chronione na wyższych poziomach lub mogą wymagać ochrony wszystkich danych na wyższym poziomie. Zwiększoną ochronę można zastosować do wszystkich lub określonych zestawów danych w środowisku Microsoft 365. Zalecamy ochronę tożsamości i urządzeń, które uzyskują dostęp do poufnych danych z porównywalnymi poziomami zabezpieczeń.
- **Wyspecjalizowane zabezpieczenia**: w razie potrzeby kilku klientów ma niewielką ilość danych, które są wysoce sklasyfikowane, stanowią tajemnice handlowe lub są regulowane. Firma Microsoft oferuje możliwości ułatwiające tym klientom spełnienie tych wymagań, w tym dodatkową ochronę tożsamości i urządzeń.

:::image type="content" source="../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png" alt-text="Stożek zabezpieczeń" lightbox="../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png":::

W tych wskazówkach pokazano, jak zaimplementować ochronę Zero Trust tożsamości i urządzeń dla każdego z tych poziomów ochrony. Skorzystaj z tych wskazówek jako minimum dla organizacji i dostosuj zasady, aby spełniać określone wymagania organizacji.

Ważne jest, aby używać spójnych poziomów ochrony między tożsamościami, urządzeniami i danymi. Na przykład ochrona użytkowników z kontami&mdash; o priorytecieuuch jako kadra kierownicza, liderzy, menedżerowie i innezasady&mdash; powinny obejmować ten sam poziom ochrony ich tożsamości, urządzeń i danych, do których uzyskują dostęp. 
<!--

The **Zero Trust identity and device protection for Microsoft 365** architecture model shows you which capabilities are comparable.

[![Thumb image for Zero Trust Identity and device protection for Microsoft 365 poster.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-thumbnail.png)](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) <br> [View as a PDF](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.pdf)  \| [Download as a Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.vsdx)

--> 

Ponadto zobacz rozwiązanie [Deploy information protection for data privacy regulations (Wdrażanie ochrony informacji na potrzeby przepisów dotyczących prywatności danych](../../solutions/information-protection-deploy.md)), aby chronić informacje przechowywane w Microsoft 365.

## <a name="security-and-productivity-trade-offs"></a>Kompromisy w zakresie bezpieczeństwa i produktywności

Wdrożenie dowolnej strategii zabezpieczeń wymaga kompromisów między bezpieczeństwem a produktywnością. Warto ocenić, w jaki sposób każda decyzja wpływa na równowagę zabezpieczeń, funkcjonalności i łatwości użycia.

:::image type="content" source="../../media/microsoft-365-policies-configurations/security-triad.png" alt-text="Zabezpieczenia równoważenia triady zabezpieczeń, funkcjonalność i łatwość użycia" lightbox="../../media/microsoft-365-policies-configurations/security-triad.png":::

Podane zalecenia są oparte na następujących zasadach:

- Znaj swoich użytkowników i bądź elastyczny w zależności od ich wymagań dotyczących zabezpieczeń i funkcjonalności.
- Zastosuj zasady zabezpieczeń w samą porę i upewnij się, że są one istotne.

## <a name="services-and-concepts-for-zero-trust-identity-and-device-access-protection"></a>Usługi i pojęcia dotyczące Zero Trust tożsamości i ochrony dostępu do urządzeń

Microsoft 365 dla przedsiębiorstw jest przeznaczony dla dużych organizacji, aby umożliwić wszystkim kreatywne działanie i bezpieczną współpracę.

Ta sekcja zawiera omówienie usług i funkcji Microsoft 365, które są ważne dla Zero Trust tożsamości i dostępu do urządzeń.

### <a name="azure-ad"></a>Azure AD

Usługa Azure AD oferuje pełny zestaw możliwości zarządzania tożsamościami. Zalecamy użycie tych możliwości w celu zabezpieczenia dostępu.

|Możliwość lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|[Uwierzytelnianie wieloskładnikowe (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|Uwierzytelnianie wieloskładnikowe wymaga od użytkowników podania dwóch form weryfikacji, takich jak hasło użytkownika oraz powiadomienie z aplikacji Microsoft Authenticator lub połączenie telefoniczne. Uwierzytelnianie wieloskładnikowe znacznie zmniejsza ryzyko użycia skradzionych poświadczeń w celu uzyskania dostępu do środowiska. Microsoft 365 używa usługi Azure AD Multi-Factor Authentication do logowania opartego na uwierzytelnianiu wieloskładnikowym.|Microsoft 365 E3 lub E5|
|[Dostęp warunkowy](/azure/active-directory/conditional-access/overview)|Usługa Azure AD ocenia warunki logowania użytkownika i używa zasad dostępu warunkowego w celu określenia dozwolonego dostępu. Na przykład w tych wskazówkach przedstawiono sposób tworzenia zasad dostępu warunkowego w celu wymagania zgodności urządzeń w celu uzyskania dostępu do poufnych danych. Znacznie zmniejsza to ryzyko, że haker z własnym urządzeniem i skradzionymi poświadczeniami będzie mógł uzyskać dostęp do poufnych danych. Chroni również poufne dane na urządzeniach, ponieważ urządzenia muszą spełniać określone wymagania dotyczące kondycji i zabezpieczeń.|Microsoft 365 E3 lub E5|
|[Grupy usługi Azure AD](/azure/active-directory/fundamentals/active-directory-manage-groups)|Zasady dostępu warunkowego, zarządzanie urządzeniami z Intune, a nawet uprawnienia do plików i witryn w organizacji zależą od przypisania do kont użytkowników lub grup usługi Azure AD. Zalecamy utworzenie grup usługi Azure AD, które odpowiadają wdrażanym poziomom ochrony. Na przykład pracownicy kadry kierowniczej są prawdopodobnie celami o wyższej wartości dla hakerów. Dlatego warto dodać konta użytkowników tych pracowników do grupy usługi Azure AD i przypisać tę grupę do zasad dostępu warunkowego i innych zasad, które wymuszają wyższy poziom ochrony dostępu.|Microsoft 365 E3 lub E5|
|[Rejestrowanie urządzeń](/azure/active-directory/devices/overview)|Zarejestrowanie urządzenia w usłudze Azure AD w celu utworzenia tożsamości dla urządzenia. Ta tożsamość służy do uwierzytelniania urządzenia podczas logowania użytkownika i stosowania zasad dostępu warunkowego, które wymagają komputerów przyłączonych do domeny lub zgodnych. Aby uzyskać te wskazówki, używamy rejestracji urządzeń do automatycznego rejestrowania przyłączonych do domeny Windows komputerów. Rejestrowanie urządzeń jest wymaganie wstępne do zarządzania urządzeniami z Intune.|Microsoft 365 E3 lub E5|
|[Ochrona tożsamości w usłudze Azure AD](/azure/active-directory/identity-protection/overview)|Umożliwia wykrywanie potencjalnych luk w zabezpieczeniach wpływających na tożsamości organizacji i konfigurowanie zasad zautomatyzowanego korygowania na potrzeby niskiego, średniego i wysokiego ryzyka logowania oraz ryzyka związanego z użytkownikiem. Te wskazówki opierają się na tej ocenie ryzyka w celu zastosowania zasad dostępu warunkowego na potrzeby uwierzytelniania wieloskładnikowego. Te wskazówki obejmują również zasady dostępu warunkowego, które wymagają od użytkowników zmiany hasła w przypadku wykrycia działania wysokiego ryzyka dla konta.|Microsoft 365 E5, Microsoft 365 E3 z dodatkiem E5 Security, licencjami EMS E5 lub Azure AD — wersja Premium P2|
|[Samodzielne resetowanie hasła (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Zezwalaj użytkownikom na bezpieczne resetowanie haseł i bez interwencji pomocy technicznej, zapewniając weryfikację wielu metod uwierzytelniania, które może kontrolować administrator.|Microsoft 365 E3 lub E5|
|[Ochrona haseł w usłudze Azure AD](/azure/active-directory/authentication/concept-password-ban-bad)|Wykrywanie i blokowanie znanych słabych haseł oraz ich wariantów oraz dodatkowych słabych terminów specyficznych dla Organizacji. Domyślne listy haseł z zakazem globalnym są automatycznie stosowane do wszystkich użytkowników w dzierżawie usługi Azure AD. Dodatkowe wpisy można zdefiniować na niestandardowej liście zakazanych haseł. Gdy użytkownicy zmieniają lub resetują swoje hasła, te listy zakazanych haseł są sprawdzane w celu wymuszenia użycia silnych haseł.|Microsoft 365 E3 lub E5|

Poniżej przedstawiono składniki Zero Trust tożsamości i dostępu do urządzeń, w tym Intune i obiektów usługi Azure AD, ustawień i podusług.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-components.png" alt-text="Składniki tożsamości Zero Trust i dostępu do urządzeń" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-components.png":::

### <a name="microsoft-intune"></a>Microsoft Intune

[Intune](/intune/introduction-intune) to oparta na chmurze usługa zarządzania urządzeniami przenośnymi firmy Microsoft. Te wskazówki zalecają zarządzanie urządzeniami Windows komputerów z Intune i zalecają konfiguracje zasad zgodności urządzeń. Intune określa, czy urządzenia są zgodne, i wysyła te dane do usługi Azure AD do użycia podczas stosowania zasad dostępu warunkowego.

#### <a name="intune-app-protection"></a>ochrona aplikacji Intune

[Intune zasad ochrony aplikacji](/intune/app-protection-policy) można używać do ochrony danych organizacji w aplikacjach mobilnych przy użyciu lub bez rejestrowania urządzeń w zarządzaniu. Intune pomaga chronić informacje, upewniając się, że pracownicy mogą nadal pracować wydajnie i zapobiegać utracie danych. Implementując zasady na poziomie aplikacji, możesz ograniczyć dostęp do zasobów firmy i utrzymać dane pod kontrolą działu IT.

W tych wskazówkach przedstawiono sposób tworzenia zalecanych zasad w celu wymuszania korzystania z zatwierdzonych aplikacji i określania, w jaki sposób te aplikacje mogą być używane z danymi biznesowymi.

### <a name="microsoft-365"></a>Microsoft 365

W tych wskazówkach pokazano, jak zaimplementować zestaw zasad w celu ochrony dostępu do usług w chmurze Microsoft 365, w tym Microsoft Teams, Exchange, SharePoint i OneDrive. Oprócz implementowania tych zasad zalecamy również podniesienie poziomu ochrony dzierżawy przy użyciu następujących zasobów:

- [Konfigurowanie dzierżawy w celu zwiększenia bezpieczeństwa](tenant-wide-setup-for-increased-security.md)

  Rekomendacje, które mają zastosowanie do zabezpieczeń punktu początkowego dla dzierżawy.

- [Plan bezpieczeństwa: najważniejsze priorytety dla pierwszych 30 dni, 90 dni i nie tylko](security-roadmap.md)

  Rekomendacje, które obejmują rejestrowanie, zarządzanie danymi, dostęp administratora i ochronę przed zagrożeniami.

### <a name="windows-11-or-windows-10-with-microsoft-365-apps-for-enterprise"></a>Windows 11 lub Windows 10 z Aplikacje Microsoft 365 dla przedsiębiorstw

Windows 11 lub Windows 10 z Aplikacje Microsoft 365 dla przedsiębiorstw jest zalecanym środowiskiem klienckim dla komputerów. Zalecamy Windows 11 lub Windows 10, ponieważ platforma Azure została zaprojektowana tak, aby zapewnić bezproblemowe środowisko zarówno w środowisku lokalnym, jak i w usłudze Azure AD. Windows 11 lub Windows 10 obejmuje również zaawansowane funkcje zabezpieczeń, które można zarządzać za pośrednictwem Intune. Aplikacje Microsoft 365 dla przedsiębiorstw zawiera najnowsze wersje aplikacji Office. Korzystają one z nowoczesnego uwierzytelniania, które jest bezpieczniejsze i wymaga dostępu warunkowego. Te aplikacje obejmują również ulepszone narzędzia do zapewniania zgodności i zabezpieczeń.

## <a name="applying-these-capabilities-across-the-three-tiers-of-protection"></a>Stosowanie tych możliwości w trzech warstwach ochrony

Poniższa tabela zawiera podsumowanie zaleceń dotyczących korzystania z tych funkcji w trzech warstwach ochrony.

|Mechanizm ochrony|Punkt początkowy|Enterprise|Wyspecjalizowane zabezpieczenia|
|---|---|---|---|
|**Wymuszanie uwierzytelniania wieloskładnikowego**|Na średnim lub wyższym ryzyku logowania|Przy niskim lub wyższym ryzyku logowania|We wszystkich nowych sesjach|
|**Wymuszanie zmiany hasła**|Dla użytkowników wysokiego ryzyka|Dla użytkowników wysokiego ryzyka|Dla użytkowników wysokiego ryzyka|
|**Wymuszanie ochrony aplikacji Intune**|Tak|Tak|Tak|
|**Wymuszanie rejestracji Intune dla urządzenia należącego do organizacji**|Wymagaj zgodnego lub przyłączanego do domeny komputera, ale zezwalaj na telefony i tablety byod (bring-your-own devices)|Wymagaj urządzenia zgodnego lub przyłączanego do domeny|Wymagaj urządzenia zgodnego lub przyłączanego do domeny|

## <a name="device-ownership"></a>Własność urządzenia

Powyższa tabela odzwierciedla tendencję wielu organizacji do obsługi kombinacji urządzeń należących do organizacji, a także urządzeń osobistych lub BYOD, aby umożliwić produktywność urządzeń przenośnych dla pracowników. Intune zasady ochrony aplikacji zapewniają ochronę poczty e-mail przed eksfiltrowania z Outlook aplikacji mobilnej i innych Office aplikacji mobilnych, zarówno na urządzeniach należących do organizacji, jak i przy użyciu funkcji BYOD.

Zalecamy, aby urządzenia należące do organizacji były zarządzane przez Intune lub przyłączone do domeny w celu zastosowania dodatkowych zabezpieczeń i kontroli. W zależności od poufności danych organizacja może nie zezwalać na używanie identyfikatorów BYOD dla określonych populacji użytkowników lub określonych aplikacji.

## <a name="deployment-and-your-apps"></a>Wdrażanie i aplikacje

Przed skonfigurowaniem i wprowadzeniem konfiguracji tożsamości Zero Trust i dostępu do urządzenia dla aplikacji zintegrowanych z usługą Azure AD należy wykonać następujące czynności:

- Zdecyduj, które aplikacje są używane w organizacji, które chcesz chronić.
- Przeanalizuj tę listę aplikacji, aby określić zestawy zasad, które zapewniają odpowiednie poziomy ochrony.

  Nie należy tworzyć oddzielnych zestawów zasad dla aplikacji, ponieważ zarządzanie nimi może stać się kłopotliwe. Firma Microsoft zaleca grupowanie aplikacji, które mają te same wymagania dotyczące ochrony dla tych samych użytkowników.

  Na przykład można mieć jeden zestaw zasad, które obejmują wszystkie aplikacje Microsoft 365 dla wszystkich użytkowników na potrzeby ochrony punktu początkowego i drugi zestaw zasad dla wszystkich poufnych aplikacji, takich jak aplikacje używane przez działy kadr lub działy finansowe, i zastosować je do tych grup.

Po określeniu zestawu zasad dla aplikacji, które chcesz zabezpieczyć, należy stopniowo wdrażać zasady dla użytkowników i rozwiązywać problemy po drodze.

Na przykład skonfiguruj zasady, które będą używane dla wszystkich aplikacji Microsoft 365 tylko dla Exchange z dodatkowymi zmianami dla Exchange. Wprowadź te zasady dla użytkowników i przeprowadź wszelkie problemy. Następnie dodaj Teams z dodatkowymi zmianami i wprowadź je dla użytkowników. Następnie dodaj SharePoint z dodatkowymi zmianami. Kontynuuj dodawanie pozostałych aplikacji, dopóki nie będzie można skonfigurować tych zasad punktu początkowego w celu uwzględnienia wszystkich Microsoft 365 aplikacji.

Podobnie w przypadku aplikacji poufnych utwórz zestaw zasad i dodaj jedną aplikację naraz i przeprowadź wszelkie problemy, dopóki nie zostaną uwzględnione w poufnym zestawie zasad aplikacji.

Firma Microsoft zaleca, aby nie tworzyć zestawów zasad, które mają zastosowanie do wszystkich aplikacji, ponieważ może to spowodować pewne niezamierzone konfiguracje. Na przykład zasady blokujące wszystkie aplikacje mogą zablokować administratorów z Azure Portal i nie można skonfigurować wykluczeń dla ważnych punktów końcowych, takich jak Microsoft Graph.

## <a name="steps-to-configure-zero-trust-identity-and-device-access"></a>Kroki konfigurowania tożsamości Zero Trust i dostępu do urządzeń

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps.png" alt-text="Kroki konfigurowania tożsamości Zero Trust i dostępu do urządzeń" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps.png":::

1. Konfigurowanie funkcji tożsamości wymagań wstępnych i ich ustawień.
2. Skonfiguruj typowe zasady dostępu warunkowego i tożsamości.
3. Skonfiguruj zasady dostępu warunkowego dla użytkowników-gości i użytkowników zewnętrznych.
4. Skonfiguruj zasady dostępu warunkowego dla aplikacji&mdash; w chmurze Microsoft 365 uch jako zasady Microsoft Teams, Exchange i SharePoint&mdash; i Microsoft Defender for Cloud Apps.

Po skonfigurowaniu Zero Trust tożsamości i dostępu do urządzeń zapoznaj się z [przewodnikiem wdrażania funkcji usługi Azure AD](/azure/active-directory/fundamentals/active-directory-deployment-checklist-p2), aby zapoznać się z etapową listą kontrolną dodatkowych funkcji do rozważenia i [zarządzaniem tożsamościami usługi Azure AD](/azure/active-directory/governance/) w celu ochrony, monitorowania i inspekcji dostępu.

## <a name="next-step"></a>Następny krok

[Wymagania wstępne dotyczące implementowania zasad Zero Trust tożsamości i dostępu do urządzeń](identity-access-prerequisites.md)
