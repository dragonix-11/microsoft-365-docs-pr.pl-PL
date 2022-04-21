---
title: Typowe zasady tożsamości Zero Trust i dostępu do urządzeń — Microsoft 365 dla | przedsiębiorstwa Microsoft Docs
description: W tym artykule opisano zalecane typowe zasady i konfiguracje dotyczące tożsamości Zero Trust i urządzeń.
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
- remotework
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 0c7facc2ac5a20b21a6862b115b62c576ebaeb1f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972194"
---
# <a name="common-zero-trust-identity-and-device-access-policies"></a>Typowe zasady dotyczące tożsamości Zero Trust i dostępu do urządzeń

W tym artykule opisano typowe zalecane zasady Zero Trust dotyczące tożsamości i dostępu urządzeń do zabezpieczania dostępu do usług w chmurze Microsoft 365, w tym aplikacji lokalnych opublikowanych w serwer proxy aplikacji Azure Active Directory (Azure AD).

W tych wskazówkach omówiono sposób wdrażania zalecanych zasad w nowo aprowizowanym środowisku. Skonfigurowanie tych zasad w oddzielnym środowisku laboratoryjnym umożliwia zrozumienie i ocenę zalecanych zasad przed przygotowaniem wdrożenia do środowisk przedprodukcyjnych i produkcyjnych. Nowo aprowizowane środowisko może być tylko w chmurze lub hybrydowe, aby odzwierciedlać potrzeby oceny.

## <a name="policy-set"></a>Zestaw zasad

Na poniższym diagramie przedstawiono zalecany zestaw zasad. Pokazuje ona, do której warstwy ochrony mają zastosowanie poszczególne zasady i czy zasady mają zastosowanie do komputerów, telefonów i tabletów, czy obu kategorii urządzeń. Wskazuje również miejsce konfigurowania tych zasad.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png" alt-text="Typowe zasady konfigurowania tożsamości Zero Trust i dostępu do urządzeń." lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png":::

<!--

Here's a one-page PDF summary:

[![Thumb image for the Zero Trust identity and device protection for Microsoft 365 handout.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-handout-thumbnail.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [View as a PDF](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)

-->

W pozostałej części tego artykułu opisano sposób konfigurowania tych zasad.

> [!NOTE]
> Wymaganie korzystania z uwierzytelniania wieloskładnikowego (MFA) jest zalecane przed zarejestrowaniem urządzeń w Intune w celu zapewnienia, że urządzenie jest w posiadaniu zamierzonego użytkownika. Aby można było wymusić zasady zgodności urządzeń, należy zarejestrować urządzenia w Intune.

Aby dać ci czas na wykonanie tych zadań, zalecamy zaimplementowanie zasad punktu początkowego w kolejności wymienionej w tej tabeli. Jednak zasady uwierzytelniania wieloskładnikowego dla przedsiębiorstw i wyspecjalizowanych poziomów zabezpieczeń ochrony można zaimplementować w dowolnym momencie.

|Poziom ochrony|Policies (zasady)|Więcej informacji|Licencjonowanie|
|---|---|---|---|
|**Punkt początkowy**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest *średnie* lub *wysokie*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem E5 Security|
||[Blokuj klientów, którzy nie obsługują nowoczesnego uwierzytelniania](#block-clients-that-dont-support-multi-factor)|Klienci, którzy nie korzystają z nowoczesnego uwierzytelniania, mogą pominąć zasady dostępu warunkowego, dlatego ważne jest, aby je zablokować.|Microsoft 365 E3 lub E5|
||[Użytkownicy wysokiego ryzyka muszą zmienić hasło](#high-risk-users-must-change-password)|Wymusza na użytkownikach zmianę hasła podczas logowania w przypadku wykrycia działania wysokiego ryzyka dla ich konta.|Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem E5 Security|
||[Stosowanie ochrony danych zasad ochrony aplikacji (APP)](#apply-app-data-protection-policies)|Jedna Intune zasad ochrony aplikacji na platformę (Windows, iOS/iPadOS, Android).|Microsoft 365 E3 lub E5|
||[Wymagaj zatwierdzonych aplikacji i ochrony aplikacji](#require-approved-apps-and-app-protection)|Wymusza ochronę aplikacji mobilnych dla telefonów i tabletów przy użyciu systemów iOS, iPadOS lub Android.|Microsoft 365 E3 lub E5|
|**Enterprise**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest *niskie*, *średnie* lub *wysokie*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem E5 Security|
||[Definiowanie zasad zgodności urządzeń](#define-device-compliance-policies)|Jedna zasada dla każdej platformy.|Microsoft 365 E3 lub E5|
||[Wymagaj zgodnych komputerów i urządzeń przenośnych](#require-compliant-pcs-and-mobile-devices)|Wymusza zarządzanie Intune dla komputerów (Windows lub macOS) oraz telefonów lub tabletów (iOS, iPadOS lub Android).|Microsoft 365 E3 lub E5|
|**Wyspecjalizowane zabezpieczenia**|[*Zawsze* wymagaj uwierzytelniania wieloskładnikowego](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 lub E5|

## <a name="assigning-policies-to-groups-and-users"></a>Przypisywanie zasad do grup i użytkowników

Przed skonfigurowaniem zasad zidentyfikuj grupy usługi Azure AD używane dla każdej warstwy ochrony. Zazwyczaj ochrona punktu początkowego ma zastosowanie do wszystkich w organizacji. Użytkownik, który jest uwzględniony zarówno dla punktu początkowego, jak i ochrony przedsiębiorstwa, będzie miał zastosowane wszystkie zasady punktu początkowego oraz zasady przedsiębiorstwa. Ochrona jest skumulowana i wymuszane są najbardziej restrykcyjne zasady.

Zalecanym rozwiązaniem jest utworzenie grupy usługi Azure AD na potrzeby wykluczenia dostępu warunkowego. Dodaj tę grupę do wszystkich zasad dostępu warunkowego w wartości **Wyklucz** ustawienia **Użytkownicy i grupy** w sekcji **Przypisania** . Zapewnia to metodę zapewniającą dostęp do użytkownika podczas rozwiązywania problemów z dostępem. Jest to zalecane tylko jako rozwiązanie tymczasowe. Monitoruj tę grupę pod kątem zmian i upewnij się, że grupa wykluczeń jest używana tylko zgodnie z oczekiwaniami.

Oto przykład przypisywania grup i wykluczeń wymagających uwierzytelniania wieloskładnikowego.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png" alt-text="Przykładowe przypisanie grupy i wykluczenia dla zasad uwierzytelniania wieloskładnikowego" lightbox="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png":::

Oto wyniki:

- Wszyscy użytkownicy muszą używać uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest średnie lub wysokie.

- Członkowie grupy Personel wykonawczy muszą używać uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest niskie, średnie lub wysokie.

  W tym przypadku członkowie grupy Kadra wykonawcza są zgodni zarówno z punktem początkowym, jak i zasadami dostępu warunkowego przedsiębiorstwa. Mechanizmy kontroli dostępu dla obu zasad są łączone, co w tym przypadku jest równoważne zasadom dostępu warunkowego przedsiębiorstwa.

- Członkowie grupy Ściśle tajne Project X są zawsze wymagane do korzystania z uwierzytelniania wieloskładnikowego

  W tym przypadku członkowie grupy Top Secret Project X są zgodni zarówno z punktem początkowym, jak i wyspecjalizowane zasady dostępu warunkowego zabezpieczeń. Mechanizmy kontroli dostępu dla obu zasad są łączone. Ponieważ kontrola dostępu dla wyspecjalizowanych zasad dostępu warunkowego zabezpieczeń jest bardziej restrykcyjna, jest używana.

Należy zachować ostrożność podczas stosowania wyższych poziomów ochrony do grup i użytkowników. Na przykład członkowie grupy Ściśle tajne Project X będą musieli używać uwierzytelniania wieloskładnikowego za każdym razem, gdy się logują, nawet jeśli nie pracują nad wyspecjalizowaną zawartością zabezpieczeń dla Project X.

Wszystkie grupy usługi Azure AD utworzone w ramach tych zaleceń muszą zostać utworzone jako grupy Microsoft 365. Jest to ważne w przypadku wdrażania etykiet poufności podczas zabezpieczania dokumentów w Microsoft Teams i SharePoint.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png" alt-text="Tworzenie grupy Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png":::

## <a name="require-mfa-based-on-sign-in-risk"></a>Wymaganie uwierzytelniania wieloskładnikowego na podstawie ryzyka logowania

Użytkownicy powinni zarejestrować się w celu uzyskania uwierzytelniania wieloskładnikowego przed wymaganiem jego użycia. Jeśli masz Microsoft 365 E5, Microsoft 365 E3 z dodatkiem E5 Security, Office 365 z licencjami EMS E5 lub indywidualnymi licencjami Azure AD — wersja Premium P2, możesz użyć zasad rejestracji usługi MFA w usłudze Azure AD Identity Protection, aby wymagać, aby użytkownicy rejestrowali się w usłudze MFA. Praca [z wymaganiami wstępnymi obejmuje rejestrowanie](identity-access-prerequisites.md) wszystkich użytkowników za pomocą uwierzytelniania wieloskładnikowego.

Po zarejestrowaniu użytkowników możesz wymagać uwierzytelniania wieloskładnikowego w celu zalogowania się przy użyciu nowych zasad dostępu warunkowego.

1. Przejdź do [Azure Portal](https://portal.azure.com) i zaloguj się przy użyciu poświadczeń.
2. Na liście usług platformy Azure wybierz pozycję **Azure Active Directory**.
3. Na liście **Zarządzanie** wybierz pozycję **Zabezpieczenia**, a następnie wybierz pozycję **Dostęp warunkowy**.
4. Wybierz pozycję **Nowe zasady** i wpisz nazwę nowych zasad.

W poniższych tabelach opisano ustawienia zasad dostępu warunkowego, które wymagają uwierzytelniania wieloskładnikowego na podstawie ryzyka logowania.

W sekcji **Przypisania** :

|Ustawienie|Właściwości|Wartości|Uwagi|
|---|---|---|---|
|Użytkownicy i grupy|Obejmują|**Wybierz użytkowników i grupy > Użytkownicy i grupy**: wybierz określone grupy zawierające docelowe konta użytkowników.|Rozpocznij od grupy obejmującej konta użytkowników pilotażowych.|
||Wykluczyć|**Użytkownicy i grupy**: wybierz grupę wyjątków dostępu warunkowego; konta usługi (tożsamości aplikacji).|Członkostwo powinno być modyfikowane w zależności od potrzeb, tymczasowo.|
|Aplikacje lub akcje w chmurze|**Aplikacje w chmurze > dołączane**|**Wybierz aplikacje**: wybierz aplikacje, do których mają być stosowane te zasady. Na przykład wybierz pozycję Exchange Online.||
|Warunki|||Skonfiguruj warunki specyficzne dla danego środowiska i potrzeb.|
||Ryzyko logowania||Zapoznaj się ze wskazówkami w poniższej tabeli.|

### <a name="sign-in-risk-condition-settings"></a>Ustawienia warunku ryzyka logowania

Zastosuj ustawienia poziomu ryzyka na podstawie docelowego poziomu ochrony.

|Poziom ochrony|Wymagane wartości poziomu ryzyka|Akcja|
|---|---|---|
|Punkt początkowy|Wysoki, średni|Sprawdź oba.|
|Enterprise|Wysoki, średni, niski|Sprawdź wszystkie trzy.|
|Wyspecjalizowane zabezpieczenia||Pozostaw wszystkie opcje niezaznaczone, aby zawsze wymuszać uwierzytelnianie wieloskładnikowe.|

W sekcji **Kontrolki dostępu** :

|Ustawienie|Właściwości|Wartości|Akcja|
|---|---|---|---|
|Udzielić|**Grant access**||Wybieranie|
|||**Wymaganie uwierzytelniania wieloskładnikowego**|Czek|
||**Wymagaj wszystkich wybranych kontrolek**||Wybieranie|

Wybierz **pozycję Wybierz** , aby zapisać ustawienia **Udzielanie** .

Na koniec wybierz pozycję **Włączone** , aby **włączyć zasady**, a następnie wybierz pozycję **Utwórz**.

Rozważ również użycie narzędzia [Co jeśli](/azure/active-directory/active-directory-conditional-access-whatif) , aby przetestować zasady.

## <a name="block-clients-that-dont-support-multi-factor"></a>Blokuj klientów, którzy nie obsługują wieloskładnikowych

Użyj ustawień w tych tabelach dla zasad dostępu warunkowego, aby zablokować klientów, którzy nie obsługują uwierzytelniania wieloskładnikowego.

Zapoznaj się z [tym artykułem](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md), aby uzyskać listę klientów w Microsoft 365, którzy obsługują uwierzytelnianie wieloskładnikowe.

W sekcji **Przypisania** :

|Ustawienie|Właściwości|Wartości|Uwagi|
|---|---|---|---|
|Użytkownicy i grupy|Obejmują|**Wybierz użytkowników i grupy > Użytkownicy i grupy**: wybierz określone grupy zawierające docelowe konta użytkowników.|Rozpocznij od grupy obejmującej konta użytkowników pilotażowych.|
||Wykluczyć|**Użytkownicy i grupy**: wybierz grupę wyjątków dostępu warunkowego; konta usługi (tożsamości aplikacji).|Członkostwo powinno być modyfikowane w zależności od potrzeb, tymczasowo.|
|Aplikacje lub akcje w chmurze|**Aplikacje w chmurze > dołączane**|**Wybierz aplikacje**: wybierz aplikacje odpowiadające klientom, którzy nie obsługują nowoczesnego uwierzytelniania.||
|Warunki|**Aplikacje klienckie**|Wybierz pozycję **Tak** , **aby skonfigurować** <p> Wyczyść znaczniki wyboru dla aplikacji **przeglądarki** i **aplikacji mobilnych oraz klientów klasycznych**||

W sekcji **Kontrolki dostępu** :

|Ustawienie|Właściwości|Wartości|Akcja|
|---|---|---|---|
|Udzielić|**Blokuj dostęp**||Wybieranie|
||**Wymagaj wszystkich wybranych kontrolek**||Wybieranie|

Wybierz **pozycję Wybierz** , aby zapisać ustawienia **Udzielanie** .

Na koniec wybierz pozycję **Włączone** , aby **włączyć zasady**, a następnie wybierz pozycję **Utwórz**.

Rozważ użycie narzędzia [Co jeśli](/azure/active-directory/active-directory-conditional-access-whatif) , aby przetestować zasady.

W przypadku Exchange Online można użyć zasad uwierzytelniania, aby [wyłączyć uwierzytelnianie podstawowe](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online), co wymusza użycie nowoczesnego uwierzytelniania przez wszystkie żądania dostępu klientów.

## <a name="high-risk-users-must-change-password"></a>Użytkownicy wysokiego ryzyka muszą zmienić hasło

Aby upewnić się, że wszystkie konta użytkowników wysokiego ryzyka, których bezpieczeństwo zostało naruszone, są zmuszone do zmiany hasła podczas logowania, należy zastosować następujące zasady.

Zaloguj się do [portalu Microsoft Azure (https://portal.azure.com)](https://portal.azure.com/) przy użyciu poświadczeń administratora, a następnie przejdź do usługi **Azure AD Identity Protection > zasad ryzyka użytkownika**.

W sekcji **Przypisania** :

|Wpisać|Właściwości|Wartości|Akcja|
|---|---|---|---|
|Użytkownicy|Obejmują|**Wszyscy użytkownicy**|Wybieranie|
|Ryzyko związane z użytkownikiem|**High (Wysoki)**||Wybieranie|

W drugiej sekcji **Przypisania** :

|Wpisać|Właściwości|Wartości|Akcja|
|---|---|---|---|
|Access|**Zezwalaj na dostęp**||Wybieranie|
|||**Wymagaj zmiany hasła**|Czek|

Wybierz pozycję **Gotowe** , aby zapisać ustawienia **dostępu** .

Na koniec wybierz pozycję **Włączone** , aby **wymusić zasady**, a następnie wybierz pozycję **Zapisz**.

Rozważ użycie narzędzia [Co jeśli](/azure/active-directory/active-directory-conditional-access-whatif) , aby przetestować zasady.

Użyj tych zasad w połączeniu z [funkcją Konfigurowanie ochrony haseł usługi Azure AD](/azure/active-directory/authentication/concept-password-ban-bad), która wykrywa i blokuje znane słabe hasła oraz ich warianty oraz dodatkowe słabe terminy specyficzne dla organizacji. Korzystanie z ochrony hasłem w usłudze Azure AD zapewnia, że zmienione hasła są silne.

## <a name="apply-app-data-protection-policies"></a>Stosowanie zasad ochrony danych aplikacji

Dostawcy APP definiują, które aplikacje są dozwolone, oraz akcje, które mogą wykonywać z danymi organizacji. Opcje dostępne w usłudze APP umożliwiają organizacjom dostosowanie ochrony do ich konkretnych potrzeb. Dla niektórych może nie być oczywiste, które ustawienia zasad są wymagane do zaimplementowania kompletnego scenariusza. Aby ułatwić organizacjom ustalanie priorytetów zabezpieczeń punktów końcowych klientów mobilnych, firma Microsoft wprowadziła taksonomię dla struktury ochrony danych aplikacji na potrzeby zarządzania aplikacjami mobilnymi dla systemów iOS i Android.

Struktura ochrony danych aplikacji jest zorganizowana na trzy różne poziomy konfiguracji, a każdy poziom jest kompilowany na poprzednim poziomie:

- **Poziom 1: Enterprise podstawowa ochrona danych** gwarantuje, że aplikacje są chronione przy użyciu numeru PIN i szyfrowane oraz wykonują operacje selektywnego czyszczenia. W przypadku urządzeń z systemem Android ten poziom sprawdza poprawność zaświadczania urządzeń z systemem Android. Jest to konfiguracja na poziomie podstawowym, która zapewnia podobną kontrolę ochrony danych w Exchange Online zasad skrzynki pocztowej i wprowadza dział IT i populację użytkowników do aplikacji.
- **Poziom 2: Enterprise rozszerzonej ochrony danych** wprowadza mechanizmy zapobiegania wyciekom danych aplikacji i minimalne wymagania dotyczące systemu operacyjnego. Jest to konfiguracja, która ma zastosowanie do większości użytkowników mobilnych uzyskujących dostęp do danych służbowych.
- **Poziom 3: Enterprise wysoka ochrona danych** wprowadza zaawansowane mechanizmy ochrony danych, ulepszoną konfigurację numeru PIN i usługę APP Mobile Threat Defense. Ta konfiguracja jest pożądana dla użytkowników uzyskujących dostęp do danych wysokiego ryzyka.

Aby wyświetlić konkretne zalecenia dotyczące każdego poziomu konfiguracji i minimalnych aplikacji, które muszą być chronione, zapoznaj się [z artykułem Struktura ochrony danych przy użyciu zasad ochrony aplikacji](/mem/intune/apps/app-protection-framework).

Korzystając z zasad opisanych w [Zero Trust konfiguracji tożsamości i dostępu do urządzeń](microsoft-365-policies-configurations.md), warstwy Punktu początkowego i ochrony Enterprise są mapowane ściśle z ustawieniami rozszerzonej ochrony danych na poziomie 2 przedsiębiorstwa. Warstwa wyspecjalizowanej ochrony zabezpieczeń jest ściśle mapowana na ustawienia wysokiej ochrony danych na poziomie 3 przedsiębiorstwa.

|Poziom ochrony|Zasady ochrony aplikacji|Więcej informacji|
|---|---|---|
|Punkt początkowy|[Zwiększona ochrona danych na poziomie 2](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Ustawienia zasad wymuszane na poziomie 2 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 1.|
|Enterprise|[Zwiększona ochrona danych na poziomie 2](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Ustawienia zasad wymuszane na poziomie 2 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 1.|
|Wyspecjalizowane zabezpieczenia|[Wysoka ochrona danych na poziomie 3 przedsiębiorstwa](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|Ustawienia zasad wymuszane na poziomie 3 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i 2 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 2.|

Aby utworzyć nowe zasady ochrony aplikacji dla każdej platformy (iOS i Android) w ramach Microsoft Endpoint Manager przy użyciu ustawień struktury ochrony danych, możesz:

1. Ręcznie utwórz zasady, wykonując kroki opisane w temacie [How to create and deploy app protection policies with Microsoft Intune (Jak tworzyć i wdrażać zasady ochrony aplikacji za pomocą Microsoft Intune](/mem/intune/apps/app-protection-policies)).
2. Zaimportuj przykładowe [szablony JSON programu Intune App Protection Policy Configuration Framework](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) przy użyciu [skryptów programu PowerShell Intune](https://github.com/microsoftgraph/powershell-intune-samples).

## <a name="require-approved-apps-and-app-protection"></a>Wymagaj zatwierdzonych aplikacji i ochrony aplikacji

Aby wymusić zasady Ochrona aplikacji zastosowane w Intune, należy utworzyć zasady dostępu warunkowego, aby wymagać zatwierdzonych aplikacji klienckich i warunków określonych w zasadach ochrony aplikacji.

Wymuszanie zasad Ochrona aplikacji wymaga zestawu zasad opisanych w temacie [Wymagaj zasad ochrony aplikacji na potrzeby dostępu aplikacji w chmurze przy użyciu dostępu warunkowego](/azure/active-directory/conditional-access/app-protection-based-conditional-access). Te zasady są uwzględniane w tym zalecanym zestawie zasad konfiguracji tożsamości i dostępu.

Aby utworzyć zasady dostępu warunkowego, które wymagają zatwierdzonych aplikacji i ochrony aplikacji, wykonaj kroki opisane w [temacie Wymagaj zatwierdzonych aplikacji klienckich lub zasad ochrony aplikacji na urządzeniach przenośnych](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices), które zezwalają na dostęp do Microsoft 365 punktów końcowych tylko na kontach w aplikacjach mobilnych chronionych przez zasady Ochrona aplikacji.

   > [!NOTE]
   > Te zasady zapewniają użytkownikom mobilnym dostęp do wszystkich Microsoft 365 punktów końcowych przy użyciu odpowiednich aplikacji.

Te zasady uniemożliwiają również Exchange ActiveSync klientom na urządzeniach przenośnych nawiązywanie połączenia z Exchange Online. Można jednak utworzyć oddzielne zasady obsługi Exchange ActiveSync na wszystkich urządzeniach. Aby uzyskać więcej informacji, zobacz [Blokuj klientów ActiveSync](secure-email-recommended-policies.md#block-activesync-clients), co uniemożliwia klientom Exchange ActiveSync korzystającym z uwierzytelniania podstawowego nawiązywanie połączenia z Exchange Online. Te zasady nie są przedstawione na ilustracji w górnej części tego artykułu. Jest ona opisana i przedstawiona w [temacie Zalecenia dotyczące zasad dotyczące zabezpieczania poczty e-mail](secure-email-recommended-policies.md).

 Te zasady korzystają z mechanizmów kontroli przyznawania [Wymagaj zatwierdzonej aplikacji klienckiej](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) i [Wymagaj zasad ochrony aplikacji](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

Na koniec zablokowanie starszego uwierzytelniania dla innych aplikacji klienckich na urządzeniach z systemami iOS i Android gwarantuje, że klienci nie będą mogli pominąć zasad dostępu warunkowego. Jeśli postępujesz zgodnie ze wskazówkami w tym artykule, skonfigurowano już [klientów bloku, którzy nie obsługują nowoczesnego uwierzytelniania](#block-clients-that-dont-support-multi-factor).

<!---
With Conditional Access, organizations can restrict access to approved (modern authentication capable) iOS and Android client apps with Intune app protection policies applied to them. Several Conditional Access policies are required, with each policy targeting all potential users. Details on creating these policies can be found in [Require app protection policy for cloud app access with Conditional Access](/azure/active-directory/conditional-access/app-protection-based-conditional-access).

1. Follow "Step 1: Configure an Azure AD Conditional Access policy for Microsoft 365" in [Scenario 1: Microsoft 365 apps require approved apps with app protection policies](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), which allows Outlook for iOS and Android, but blocks OAuth capable Exchange ActiveSync clients from connecting to Exchange Online.

   > [!NOTE]
   > This policy ensures mobile users can access all Office endpoints using the applicable apps.

2. If enabling mobile access to Exchange Online, implement [Block ActiveSync clients](secure-email-recommended-policies.md#block-activesync-clients), which prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online.

   The above policies leverage the grant controls [Require approved client app](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) and [Require app protection policy](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

3. Disable legacy authentication for other client apps on iOS and Android devices. For more information, see [Block clients that don't support modern authentication](#block-clients-that-dont-support-modern-authentication).
-->

## <a name="define-device-compliance-policies"></a>Definiowanie zasad zgodności urządzeń

Zasady zgodności urządzeń definiują wymagania, które urządzenia muszą spełniać, aby zostały określone jako zgodne. Zasady zgodności urządzeń Intune są tworzone z poziomu centrum administracyjnego Microsoft Endpoint Manager.

Należy utworzyć zasady dla każdej platformy komputera, telefonu lub tabletu:

- Administratora urządzenia z systemem Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1 i nowsze
- Windows 10 lub nowszy

Aby utworzyć zasady zgodności urządzeń, zaloguj się do [centrum administracyjnego Microsoft Endpoint Manager](https://endpoint.microsoft.com) przy użyciu poświadczeń administratora, a następnie przejdź do obszaru **Zasady**\> **zgodności** **urządzeń**\>. Wybierz pozycję **Utwórz zasady**.

Aby zasady zgodności urządzeń zostały wdrożone, muszą być przypisane do grup użytkowników. Zasady są przypisywane po utworzeniu i zapisaniu. W centrum administracyjnym wybierz zasady, a następnie wybierz pozycję **Przypisania**. Po wybraniu grup, które mają zostać odebrane zasady, wybierz pozycję **Zapisz** , aby zapisać to przypisanie grupy i wdrożyć zasady.

Aby uzyskać szczegółowe wskazówki dotyczące tworzenia zasad zgodności w Intune, zobacz [Tworzenie zasad zgodności w Microsoft Intune](/mem/intune/protect/create-compliance-policy) w dokumentacji Intune.

### <a name="recommended-settings-for-ios"></a>Zalecane ustawienia dla systemu iOS

System iOS/iPadOS obsługuje kilka scenariuszy rejestracji, z których dwa są objęte tą strukturą:

- [Rejestracja urządzeń osobistych](/mem/intune/enrollment/ios-enroll) — te urządzenia są własnością osobistą i są używane zarówno do użytku służbowego, jak i osobistego.
- [Nadzorowana automatyczna rejestracja urządzeń dla urządzeń należących do firmy](/mem/intune/enrollment/device-enrollment-program-enroll-ios) — te urządzenia są własnością firmy, są skojarzone z pojedynczym użytkownikiem i są używane wyłącznie do użytku służbowego, a nie osobistego.

Struktura konfiguracji zabezpieczeń systemu iOS/iPadOS jest zorganizowana w kilka różnych scenariuszy konfiguracji, zapewniając wskazówki dotyczące urządzeń osobistych i nadzorowanych.

W przypadku urządzeń należących do użytkownika:

- Zabezpieczenia podstawowe (poziom 1) — firma Microsoft zaleca tę konfigurację jako minimalną konfigurację zabezpieczeń dla urządzeń osobistych, na których użytkownicy uzyskują dostęp do danych służbowych. Odbywa się to przez wymuszanie zasad haseł, charakterystyki blokady urządzenia i wyłączanie niektórych funkcji urządzeń (np. niezaufanych certyfikatów).
- Rozszerzone zabezpieczenia (poziom 2) — firma Microsoft zaleca tę konfigurację dla urządzeń, na których użytkownicy uzyskują dostęp do informacji poufnych lub poufnych. Ta konfiguracja wprowadza mechanizmy kontroli udostępniania danych. Ta konfiguracja ma zastosowanie do większości użytkowników mobilnych uzyskujących dostęp do danych służbowych na urządzeniu.
- Wysoki poziom zabezpieczeń (poziom 3) — firma Microsoft zaleca tę konfigurację dla urządzeń używanych przez określonych użytkowników lub grupy, które są wyjątkowo wysokiego ryzyka (użytkownicy obsługują wysoce poufne dane, gdy nieautoryzowane ujawnienie powoduje znaczne straty materialne w organizacji). Ta konfiguracja wprowadza silniejsze zasady haseł, wyłącza niektóre funkcje urządzenia i wymusza dodatkowe ograniczenia transferu danych.

W przypadku urządzeń nadzorowanych:

- Podstawowe zabezpieczenia (poziom 1) — firma Microsoft zaleca tę konfigurację jako minimalną konfigurację zabezpieczeń dla urządzeń nadzorowanych, na których użytkownicy uzyskują dostęp do danych służbowych. Odbywa się to przez wymuszanie zasad haseł, charakterystyki blokady urządzenia i wyłączanie niektórych funkcji urządzeń (np. niezaufanych certyfikatów).
- Rozszerzone zabezpieczenia (poziom 2) — firma Microsoft zaleca tę konfigurację dla urządzeń, na których użytkownicy uzyskują dostęp do informacji poufnych lub poufnych. Ta konfiguracja wprowadza mechanizmy kontroli udostępniania danych i blokuje dostęp do urządzeń USB. Ta konfiguracja ma zastosowanie do większości użytkowników mobilnych uzyskujących dostęp do danych służbowych na urządzeniu.
- Wysoki poziom zabezpieczeń (poziom 3) — firma Microsoft zaleca tę konfigurację dla urządzeń używanych przez określonych użytkowników lub grupy, które są wyjątkowo wysokiego ryzyka (użytkownicy obsługują wysoce poufne dane, gdy nieautoryzowane ujawnienie powoduje znaczne straty materialne w organizacji). Ta konfiguracja wprowadza silniejsze zasady haseł, wyłącza niektóre funkcje urządzenia, wymusza dodatkowe ograniczenia transferu danych i wymaga instalowania aplikacji za pośrednictwem programu zakupów zbiorczych firmy Apple.

Korzystając z zasad opisanych w [Zero Trust konfiguracji tożsamości i dostępu do urządzeń](microsoft-365-policies-configurations.md), warstwy Punkt początkowy i Enterprise ochrony są mapowane ściśle przy użyciu rozszerzonych ustawień zabezpieczeń poziomu 2. Warstwa wyspecjalizowanej ochrony zabezpieczeń jest ściśle mapowana na ustawienia zabezpieczeń wysokiego poziomu 3.

|Poziom ochrony  |Zasady dotyczące urządzeń |Więcej informacji  |
|---------|---------|---------|
|Punkt początkowy     |Rozszerzone zabezpieczenia (poziom 2)         |Ustawienia zasad wymuszane na poziomie 2 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 1.         |
|Enterprise     |Rozszerzone zabezpieczenia (poziom 2)         |Ustawienia zasad wymuszane na poziomie 2 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 1.         |
|Wyspecjalizowane zabezpieczenia     |Wysokie zabezpieczenia (poziom 3)         |Ustawienia zasad wymuszane na poziomie 3 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i 2 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 2.         |

Aby wyświetlić konkretne zalecenia dotyczące zgodności urządzeń i ograniczeń urządzeń dla każdego poziomu konfiguracji, zapoznaj się z platformą [Konfiguracja zabezpieczeń systemu iOS/iPadOS](/mem/intune/enrollment/ios-ipados-configuration-framework).

### <a name="recommended-settings-for-android"></a>Zalecane ustawienia dla systemu Android

System Android Enterprise obsługuje kilka scenariuszy rejestracji, z których dwa są objęte w ramach tej struktury:

- [Profil służbowy systemu Android Enterprise](/intune/android-work-profile-enroll) — ten model rejestracji jest zwykle używany w przypadku urządzeń osobistych, gdzie it chce zapewnić wyraźną granicę separacji między danymi służbowymi i osobistymi. Zasady kontrolowane przez it zapewniają, że dane służbowe nie mogą być przesyłane do profilu osobistego.
- [Urządzenia z systemem Android Enterprise w pełni zarządzane](/intune/android-fully-managed-enroll) — te urządzenia są własnością firmy, są skojarzone z jednym użytkownikiem i są używane wyłącznie do użytku służbowego, a nie osobistego.

Struktura konfiguracji zabezpieczeń systemu Android Enterprise jest zorganizowana w kilka różnych scenariuszy konfiguracji, zapewniając wskazówki dotyczące profilu służbowego i w pełni zarządzanych scenariuszy.

W przypadku urządzeń z profilem służbowym systemu Android Enterprise:

- Rozszerzone zabezpieczenia profilu służbowego (poziom 2) — firma Microsoft zaleca tę konfigurację jako minimalną konfigurację zabezpieczeń dla urządzeń osobistych, na których użytkownicy uzyskują dostęp do danych służbowych. Ta konfiguracja wprowadza wymagania dotyczące haseł, oddziela dane służbowe i osobowe oraz weryfikuje zaświadczanie urządzeń z systemem Android.
- Wysoki poziom zabezpieczeń profilu służbowego (poziom 3) — firma Microsoft zaleca tę konfigurację dla urządzeń używanych przez określonych użytkowników lub grupy, którzy są wyjątkowo wysokiego ryzyka (użytkownicy obsługują wysoce poufne dane, gdy nieautoryzowane ujawnienie powoduje znaczne straty materialne w organizacji). Ta konfiguracja wprowadza ochronę przed zagrożeniami mobilnymi lub Ochrona punktu końcowego w usłudze Microsoft Defender, ustawia minimalną wersję systemu Android, wprowadza silniejsze zasady haseł i dodatkowo ogranicza separację służb i osobistą.

W przypadku urządzeń z systemem Android Enterprise w pełni zarządzanych:

- W pełni zarządzane podstawowe zabezpieczenia (poziom 1) — firma Microsoft zaleca tę konfigurację jako minimalną konfigurację zabezpieczeń dla urządzenia przedsiębiorstwa. Ta konfiguracja ma zastosowanie do większości użytkowników mobilnych uzyskujących dostęp do danych służbowych. Ta konfiguracja wprowadza wymagania dotyczące haseł, ustawia minimalną wersję systemu Android i wprowadza pewne ograniczenia dotyczące urządzeń.
- W pełni zarządzane rozszerzone zabezpieczenia (poziom 2) — firma Microsoft zaleca tę konfigurację dla urządzeń, na których użytkownicy uzyskują dostęp do informacji poufnych lub poufnych. Ta konfiguracja wprowadza silniejsze zasady haseł i wyłącza możliwości użytkownika/konta.
- W pełni zarządzane wysokie zabezpieczenia (poziom 3) — firma Microsoft zaleca tę konfigurację dla urządzeń używanych przez określonych użytkowników lub grupy, które są wyjątkowo wysokiego ryzyka (użytkownicy obsługują wysoce poufne dane, gdy nieautoryzowane ujawnienie powoduje znaczne straty materialne w organizacji). Ta konfiguracja zwiększa minimalną wersję systemu Android, wprowadza ochronę przed zagrożeniami mobilnymi lub Ochrona punktu końcowego w usłudze Microsoft Defender i wymusza dodatkowe ograniczenia dotyczące urządzeń.

Korzystając z zasad opisanych w [Zero Trust konfiguracji tożsamości i dostępu do urządzeń](microsoft-365-policies-configurations.md), warstwy Punktu początkowego i ochrony Enterprise są ściśle mapowane z podstawowymi zabezpieczeniami poziomu 1 dla urządzeń osobistych i rozszerzonymi ustawieniami zabezpieczeń poziomu 2 dla w pełni zarządzanych urządzeń. Warstwa wyspecjalizowanej ochrony zabezpieczeń jest ściśle mapowana na ustawienia zabezpieczeń wysokiego poziomu 3.

W przypadku urządzeń z profilem służbowym systemu Android Enterprise:

|Poziom ochrony  |Zasady dotyczące urządzeń |Więcej informacji  |
|---------|---------|---------|
|Punkt początkowy     |Profil służbowy: zabezpieczenia podstawowe (poziom 1)      |nd.         |
|Enterprise     |Profil służbowy: zabezpieczenia podstawowe (poziom 1)         |nd.         |
|Punkt początkowy     |W pełni zarządzane: rozszerzone zabezpieczenia (poziom 2)       |Ustawienia zasad wymuszane na poziomie 2 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 1.         |
|Enterprise     |W pełni zarządzane: rozszerzone zabezpieczenia (poziom 2)         |Ustawienia zasad wymuszane na poziomie 2 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 1.         |
|Wyspecjalizowane zabezpieczenia     |Wysokie zabezpieczenia (poziom 3)         |Ustawienia zasad wymuszane na poziomie 3 obejmują wszystkie ustawienia zasad zalecane dla poziomu 1 i 2 i tylko dodaje lub aktualizuje poniższe ustawienia zasad w celu zaimplementowania większej liczby kontrolek i bardziej zaawansowanej konfiguracji niż poziom 2.         |

Aby wyświetlić konkretne zalecenia dotyczące zgodności urządzeń i ograniczeń urządzeń dla każdego poziomu konfiguracji, zapoznaj się z platformą [Konfiguracja zabezpieczeń systemu Android Enterprise](/mem/intune/enrollment/android-configuration-framework).

### <a name="recommended-settings-for-windows-10-and-later"></a>Zalecane ustawienia dla Windows 10 i nowszych

Następujące ustawienia są zalecane dla komputerów z systemem Windows 10 i nowszych, zgodnie z konfiguracją w **kroku 2: Ustawienia zgodności** procesu tworzenia zasad.

Aby **zapoznać się z regułami oceny usługi zaświadczania o kondycji urządzenia > Windows** kondycji, zobacz tę tabelę.

|Właściwości|Value|Akcja|
|---|---|---|
|Wymagaj funkcji BitLocker|Wymagają|Wybieranie|
|Wymagaj włączenia bezpiecznego rozruchu na urządzeniu|Wymagają|Wybieranie|
|Wymagaj integralności kodu|Wymagają|Wybieranie|

W obszarze **Właściwości urządzenia** określ odpowiednie wartości dla wersji systemu operacyjnego na podstawie zasad IT i zabezpieczeń.

W obszarze **Configuration Manager Zgodność** wybierz pozycję **Wymagaj**.

Aby uzyskać **informacje o zabezpieczeniach systemu**, zobacz tę tabelę.

|Wpisać|Właściwości|Value|Akcja|
|---|---|---|---|
|Password (hasło)|Wymagaj hasła do odblokowania urządzeń przenośnych|Wymagają|Wybieranie|
||Proste hasła|Blokuj|Wybieranie|
||Typ hasła|Domyślne urządzenie|Wybieranie|
||Minimalna długość hasła|6|Wpisać|
||Maksymalna liczba minut braku aktywności przed wymaganiem hasła|15|Wpisać <p> To ustawienie jest obsługiwane w systemie Android w wersji 4.0 lub nowszej lub KNOX 4.0 lub nowszej. W przypadku urządzeń z systemem iOS jest ona obsługiwana w systemie iOS 8.0 lub nowszym.|
||Wygaśnięcie hasła (dni)|41|Wpisać|
||Liczba poprzednich haseł, aby zapobiec ponownemu użyciu|5|Wpisać|
||Wymagaj hasła po powrocie urządzenia ze stanu bezczynności (urządzenia przenośne i holograficzne)|Wymagają|Dostępne dla Windows 10 i nowszych|
|Szyfrowanie|Szyfrowanie magazynu danych na urządzeniu|Wymagają|Wybieranie|
|Zabezpieczenia urządzenia|Zapory|Wymagają|Wybieranie|
||Antivirus|Wymagają|Wybieranie|
||Antyspyware|Wymagają|Wybieranie <p> To ustawienie wymaga rozwiązania chroniącego przed oprogramowaniem szpiegującym zarejestrowanego w aplikacji Zabezpieczenia Windows.|
|Defender dla Chmury|Microsoft Defender Antimalware|Wymagają|Wybieranie|
||Minimalna wersja ochrony przed złośliwym kodem w usłudze Microsoft Defender||Wpisać <p> Obsługiwane tylko w przypadku Windows 10 pulpitu. Firma Microsoft zaleca wersje nie więcej niż pięć z tyłu od najnowszej wersji.|
||Aktualizowanie sygnatury ochrony przed złośliwym kodem w usłudze Microsoft Defender|Wymagają|Wybieranie|
||Ochrona w czasie rzeczywistym|Wymagają|Wybieranie <p> Obsługiwane tylko w przypadku Windows 10 i nowszych pulpitów|

#### <a name="microsoft-defender-for-endpoint"></a>Ochrona punktu końcowego w usłudze Microsoft Defender

|Wpisać|Właściwości|Value|Akcja|
|---|---|---|---|
|reguły Ochrona punktu końcowego w usłudze Microsoft Defender w centrum administracyjnym Microsoft Endpoint Manager|[Wymagaj, aby urządzenie było na poziomie lub poniżej oceny ryzyka maszyny](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Średni|Wybieranie|

<!--
## Require compliant PCs (but not compliant phones and tablets)

Before adding a policy to require compliant PCs, be sure to enroll your devices for management in Intune. Using multi-factor authentication is recommended before enrolling devices into Intune for assurance that the device is in the possession of the intended user.

To require compliant PCs:

1. Go to the [Azure portal](https://portal.azure.com), and sign in with your credentials.
2. In the list of Azure services, choose **Azure Active Directory**.
3. In the **Manage** list, choose **Security**, and then choose **Conditional Access**.
4. Choose **New policy** and type the new policy's name.

5. Under **Assignments**, choose **Users and groups** and include who you want the policy to apply to. Also exclude your Conditional Access exclusion group.

6. Under **Assignments**, choose **Cloud apps or actions**.

7. For **Include**, choose **Select apps > Select**, and then select the desired apps from the **Cloud apps** list. For example, select Office 365. Choose **Select** when done.

8. To require compliant PCs (but not compliant phones and tablets), under **Assignments**, choose **Conditions > Device platforms**. Select **Yes** for **Configure**. Choose  **Select device platforms**, select **Yes** and select **Any device** and under Exclude select **iOS** and **Android**, and then choose **Done**.

9. Under **Access controls**, choose **Grant** .

10. Choose **Grant access** and then check **Require device to be marked as compliant**. For multiple controls, select **Require all the selected controls**. When complete, choose **Select**.

11. Select **On** for **Enable policy**, and then choose **Create**.

> [!NOTE]
> Make sure that your device is compliant before enabling this policy. Otherwise, you could get locked out and will be unable to change this policy until your user account has been added to the Conditional Access exclusion group.

-->

## <a name="require-compliant-pcs-and-mobile-devices"></a>Wymagaj zgodnych komputerów i urządzeń przenośnych

Aby wymagać zgodności dla wszystkich urządzeń:

1. Przejdź do [Azure Portal](https://portal.azure.com) i zaloguj się przy użyciu poświadczeń.
2. Na liście usług platformy Azure wybierz pozycję **Azure Active Directory**.
3. Na liście **Zarządzanie** wybierz pozycję **Zabezpieczenia**, a następnie wybierz pozycję **Dostęp warunkowy**.
4. Wybierz pozycję **Nowe zasady** i wpisz nazwę nowych zasad.

5. W obszarze **Przypisania** wybierz pozycję **Użytkownicy i grupy** i uwzględnij, do kogo mają zostać zastosowane zasady. Wykluczaj również grupę wykluczeń dostępu warunkowego.

6. W obszarze **Przypisania** wybierz pozycję **Aplikacje lub akcje w chmurze**.

7. W obszarze **Uwzględnij** wybierz **pozycję Wybierz aplikacje > Wybierz**, a następnie wybierz żądane aplikacje z listy **Aplikacje w chmurze** . Na przykład wybierz pozycję Office 365. Wybierz **pozycję Wybierz** po zakończeniu.

8. W obszarze **Kontrola dostępu** wybierz pozycję **Udziel** .

9. Wybierz pozycję **Udziel dostępu** , a następnie wybierz pozycję **Wymagaj, aby urządzenie było oznaczone jako zgodne**. W przypadku wielu kontrolek wybierz pozycję **Wymagaj wszystkich wybranych kontrolek**. Po zakończeniu wybierz **pozycję Wybierz**.

10. Wybierz pozycję **Włączone** , aby **włączyć zasady**, a następnie wybierz pozycję **Utwórz**.

> [!NOTE]
> Przed włączeniem tych zasad upewnij się, że urządzenie jest zgodne. W przeciwnym razie możesz zostać zablokowany i nie będzie można zmienić tych zasad, dopóki konto użytkownika nie zostanie dodane do grupy wykluczeń dostępu warunkowego.

## <a name="next-step"></a>Następny krok

[![Krok 3. Zasady dla użytkowników-gości i użytkowników zewnętrznych.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png#lightbox)](identity-access-policies-guest-access.md)

[Dowiedz się więcej o zaleceniach dotyczących zasad dla gości i użytkowników zewnętrznych](identity-access-policies-guest-access.md)
