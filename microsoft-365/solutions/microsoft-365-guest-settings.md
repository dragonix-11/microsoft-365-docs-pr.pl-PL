---
title: Informacje dotyczące ustawień udostępniania dla gości na platformie Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
f1.keywords: NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkTEAMS
- admindeeplinkSPO
ms.localizationpriority: high
recommendations: false
description: Dowiedz się więcej o ustawieniach udostępniania gości dostępnych w Microsoft 365, które mogą mieć wpływ na udostępnianie osobom spoza organizacji.
ms.openlocfilehash: 4c472fb20a85c0f00f7623cc63c4d33556b511e2
ms.sourcegitcommit: 2f6a0096038d09f0e43e1231b01c19e0b40fb358
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64687269"
---
# <a name="microsoft-365-guest-sharing-settings-reference"></a>Informacje dotyczące ustawień udostępniania dla gości na platformie Microsoft 365

Ten artykuł zawiera dokumentację różnych ustawień, które mogą mieć wpływ na udostępnianie osobom spoza organizacji obciążeń Microsoft 365: Teams, Grupy Microsoft 365, SharePoint i OneDrive. Te ustawienia znajdują się w centrach administracyjnych usługi Azure Active Directory, platformy Microsoft 365, usługi Teams i programu SharePoint.

## <a name="azure-active-directory"></a>Azure Active Directory

**Rola administratora:** administrator globalny

Azure Active Directory jest usługą katalogową używaną przez Microsoft 365. Ustawienia relacji organizacyjnych Azure Active Directory bezpośrednio wpływają na udostępnianie w Teams, Grupy Microsoft 365, SharePoint i OneDrive.

> [!NOTE]
> Te ustawienia mają wpływ na SharePoint tylko wtedy, gdy skonfigurowano [integrację SharePoint i OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview). W poniższej tabeli założono, że zostało to skonfigurowane.

### <a name="external-collaboration-settings"></a>Ustawienia współpracy zewnętrznej

**Nawigacja:** [centrum administracyjne Azure Active Directory](https://aad.portal.azure.com) > Azure Active Directory > tożsamości zewnętrznych > ustawienia współpracy zewnętrznej

![Zrzut ekranu przedstawiający stronę Ustawienia Azure Active Directory Relacje organizacyjne.](../media/azure-ad-organizational-relationships-settings.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Dostęp użytkownika-gościa|Użytkownicy-goście mają ograniczony dostęp do właściwości i członkostwa obiektów katalogu|Określa [uprawnienia, które goście mają w Azure Active Directory](/azure/active-directory/fundamentals/users-default-permissions).|
|Ustawienia zaproszenia gościa|Każda osoba w organizacji może zapraszać użytkowników-gości, w tym gości i nieadministracyjnych|Określa, czy goście, członkowie i administratorzy mogą zapraszać gości do organizacji. <p> To ustawienie ma wpływ na środowisko udostępniania Microsoft 365, takie jak Teams i SharePoint.|
|Włączanie samoobsługowej rejestracji gościa za pośrednictwem przepływów użytkownika|Nie|Określa, czy można tworzyć przepływy użytkownika, które umożliwiają innej osobie rejestrację w utworzonej aplikacji i utworzenie nowego konta gościa.|
|Ograniczenia współpracy|Zezwalaj na wysyłanie zaproszeń do dowolnej domeny|To ustawienie umożliwia określenie listy dozwolonych lub zablokowanych domen do udostępniania. Po określeniu dozwolonych domen zaproszenia do udostępniania mogą być wysyłane tylko do tych domen. Po określeniu niedozwolonych domen nie można wysyłać zaproszeń do tych domen. <p> To ustawienie ma wpływ na środowisko udostępniania Microsoft 365, takie jak Teams i SharePoint. Domeny można zezwalać lub blokować na bardziej szczegółowym poziomie, używając filtrowania domen w SharePoint lub Teams.|

Te ustawienia wpływają na sposób zapraszania użytkowników do katalogu. Nie mają one wpływu na udostępnianie gościom, którzy już znajdują się w katalogu.

### <a name="cross-tenant-access-settings"></a>Ustawienia dostępu między dzierżawami

**Nawigacja:** [Azure Active Directory centrum administracyjne](https://aad.portal.azure.com) > Azure Active Directory > tożsamości zewnętrznych > ustawienia dostępu między dzierżawami > karty Ustawienia domyślne

Ustawienia domyślne mają zastosowanie do wszystkich zewnętrznych organizacji usługi Azure AD, z wyjątkiem tych z ustawieniami specyficznymi dla organizacji. Ustawienia dla określonej organizacji można skonfigurować na karcie **Ustawienia organizacyjne**. Istnieją oddzielne ustawienia dla gości (współpraca B2B) i użytkownicy [bezpośrednich połączeń usługi Azure AD B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview).

![Zrzut ekranu przedstawiający stronę ustawień dostępu między dzierżawami Azure Active Directory.](../media/azure-ad-cross-tenant-default-settings.png)

**Ustawienia dostępu przychodzącego**

Ustawienia dostępu przychodzącego kontrolują, czy użytkownicy z zewnętrznych organizacji usługi Azure AD mogą uzyskiwać dostęp do zasobów w organizacji.

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Współpraca B2B — zewnętrzni użytkownicy i grupy|Wszystkie dozwolone|Określa, jakie osoby w innych organizacjach usługi Azure AD mogą mieć dostęp do zasobów w organizacji jako goście.|
|Współpraca B2B — aplikacje|Wszystkie dozwolone|Określa, do których aplikacji w organizacji można udzielić dostępu gościom.|
|Bezpośrednie połączenie B2B — użytkownicy zewnętrzni i grupy|Wszystkie zablokowane|Określa, czy osobom w innych organizacjach usługi Azure AD można udzielić dostępu do zasobów w organizacji za pośrednictwem połączenia bezpośredniego B2B.|
|Bezpośrednie połączenie B2B — aplikacje|Wszystkie zablokowane|Określa, do których aplikacji w organizacji można udzielić dostępu użytkownikom usługi B2B direct connect.|
|Ustawienia zaufania|Wyłączona|Określa, czy zasady dostępu warunkowego będą akceptować oświadczenia innych organizacji usługi Azure AD, gdy osoby z tych organizacji uzyskują dostęp do twoich zasobów.|

**Ustawienia dostępu wychodzącego**

Ustawienia dostępu wychodzącego kontrolują, czy użytkownicy mogą uzyskiwać dostęp do zasobów w organizacji zewnętrznej.

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Współpraca B2B — zewnętrzni użytkownicy i grupy|Wszystkie dozwolone|Określa, którym użytkownikom w organizacji można udzielić dostępu do zasobów w innych organizacjach usługi Azure AD jako goście.|
|Współpraca B2B — aplikacje|Wszystkie dozwolone|Określa aplikacje w innych organizacjach usługi Azure AD, do których użytkownicy mogą mieć dostęp jako goście.|
|Bezpośrednie połączenie B2B — użytkownicy zewnętrzni i grupy|Wszystkie zablokowane|Określa, którym użytkownikom w organizacji można udzielić dostępu do zasobów w innych organizacjach usługi Azure AD za pośrednictwem połączenia bezpośredniego B2B.|
|Bezpośrednie połączenie B2B — aplikacje|Wszystkie zablokowane|Określa aplikacje w innych organizacjach usługi Azure AD, do których użytkownicy mogą uzyskać dostęp za pośrednictwem bezpośredniego połączenia B2B.|

## <a name="microsoft-365"></a>Microsoft 365

**Rola administratora:** administrator globalny

Centrum administracyjne platformy Microsoft 365 ma ustawienia na poziomie organizacji dotyczące udostępniania i Grupy Microsoft 365.

### <a name="sharing"></a>Udostępnianie

**Nawigacja:** [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) >  **Ustawienia** >  **Ustawienia** >  grupy <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**zabezpieczeńZabezpieczenia &** karty</a> >  **PrywatnośćSharing**.

![Zrzut ekranu przedstawiający ustawienie udostępniania gościa zabezpieczeń i prywatności w Centrum administracyjne platformy Microsoft 365.](../media/sharepoint-security-privacy-sharing-setting.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Zezwalaj użytkownikom na dodawanie nowych gości do organizacji|Na|Po ustawieniu pozycji **Tak** członkowie usługi Azure AD mogą zapraszać gości za pośrednictwem usługi Azure AD. Po ustawieniu wartości **Nie** nie mogą. Po ustawieniu opcji **Tak** członkowie grupy Microsoft 365 mogą zapraszać gości z zatwierdzeniem właściciela; po ustawieniu opcji **Nie** członkowie grupy Microsoft 365 mogą zapraszać gości z zatwierdzeniem właściciela, ale właściciele muszą być administratorami globalnymi, aby je zatwierdzić. <p> Należy **pamiętać, że członkowie mogą zapraszać** członków w usłudze Azure AD (w przeciwieństwie do gości), a nie do członków witryny lub grupy w Microsoft 365. <p> Jest to identyczne z ustawieniem **Członkowie mogą zapraszać** w Azure Active Directory ustawieniach relacji organizacyjnych.|

### <a name="microsoft-365-groups"></a>Grupy Microsoft 365

**Nawigacja:** [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) >  **Ustawienia** >  **Ustawienia > Grupy Microsoft 365**

![Zrzut ekranu przedstawiający Grupy Microsoft 365 ustawienia gościa w Centrum administracyjne platformy Microsoft 365.](../media/office-365-groups-guest-settings.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Zezwalaj członkom grupy spoza organizacji na dostęp do zawartości grupy|Na|Po ustawieniu pozycji **Włączone** goście mogą uzyskiwać dostęp do zawartości grup; Po ustawieniu pozycji **Wył**. nie mogą. To ustawienie powinno być **włączone** w przypadku każdego scenariusza, w którym goście wchodzą w interakcję z Grupy Microsoft 365 lub Teams.|
|Zezwalaj właścicielom grup na dodawanie osób spoza organizacji do grup|Na|Po **włączeniu** właściciele Grupy Microsoft 365 lub Teams mogą zapraszać nowych gości do grupy. Po **wył.**, nie mogą. To ustawienie powinno być **włączone** dla każdego scenariusza, w którym goście mają być dodawani do grup.|

Te ustawienia są na poziomie organizacji. Zobacz [Tworzenie ustawień dla określonej grupy](/azure/active-directory/users-groups-roles/groups-settings-cmdlets#create-settings-for-a-specific-group) , aby uzyskać informacje o sposobie zmiany tych ustawień na poziomie grupy przy użyciu programu PowerShell.

## <a name="teams"></a>Teams

Przełącznik dostępu gościa głównego Teams **Zezwalaj na dostęp gościa w Teams** musi być **włączony**, aby inne ustawienia gościa były dostępne.

**Rola administratora:** administrator usługi Teams

### <a name="guest-access"></a>Dostęp gościa

**Nawigacja:** [Teams centrum](https://admin.teams.microsoft.com) >  **administracyjneUstawienia** >  dla całej <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**grupyUzyskaj dostęp**</a>

![Zrzut ekranu przedstawiający przełącznik dostępu gościa Teams.](../media/teams-guest-access-toggle.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Zezwalaj na dostęp gościa w Teams|Na|Włącza lub wyłącza dostęp gościa dla Teams ogólnej. Po zmianie tego ustawienia może upłynąć 24 godziny.|

### <a name="guest-calling"></a>Wywołanie gościa

**Nawigacja:** [Teams centrum](https://admin.teams.microsoft.com) >  **administracyjneUstawienia** >  dla całej <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**grupyUzyskaj dostęp**</a>

![Zrzut ekranu przedstawiający opcje Teams połączeń gościa.](../media/teams-guest-calling-setting.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Wykonywanie połączeń prywatnych|Na|Po **włączeniu** goście mogą wykonywać połączenia równorzędne w Teams; gdy są **wyłączone**, nie mogą.|

### <a name="guest-meeting"></a>Spotkanie gościa

**Nawigacja:** [Teams centrum](https://admin.teams.microsoft.com) >  **administracyjneUstawienia** >  dla całej <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**grupyUzyskaj dostęp**</a>

![Zrzut ekranu przedstawiający Teams ustawień spotkania gościa.](../media/teams-guest-meeting-settings.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Zezwalaj na wideo ip|Na|Po **włączeniu** goście mogą korzystać z wideo w swoich rozmowach i spotkaniach; gdy **wyłączone**, nie mogą.|
|Tryb udostępniania ekranu|Cały ekran|Po **wyłączeniu** goście nie mogą udostępniać swoich ekranów w Teams. Po ustawieniu pozycji **Pojedyncza aplikacja** goście mogą udostępniać tylko jedną aplikację na ekranie. Po ustawieniu opcji **Cały ekran** goście mogą udostępnić aplikację lub cały ekran.|
|Zezwalaj na spotkanie teraz|Na|Po **włączeniu** goście mogą korzystać z funkcji Spotkaj się teraz w Teams; gdy jest **wyłączona**, nie mogą.|

### <a name="guest-messaging"></a>Komunikaty gościa

**Nawigacja:** [Teams centrum](https://admin.teams.microsoft.com) >  **administracyjneUstawienia** >  dla całej <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**grupyUzyskaj dostęp**</a>

![Zrzut ekranu przedstawiający Teams ustawienia obsługi komunikatów gościa.](../media/teams-guest-messaging-settings.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Edytowanie wysłanych komunikatów|Na|Po **włączeniu** goście mogą edytować wiadomości, które wcześniej wysyłali; gdy **wyłączone**, nie mogą.|
|Usuwanie wysłanych komunikatów|Na|Po **włączeniu** goście mogą usuwać wiadomości, które wcześniej wysyłali; gdy **wyłączone**, nie mogą.|
|Czat|Na|Po **włączeniu** goście mogą korzystać z czatu w Teams; gdy są **wyłączone**, nie mogą.|
|Używanie usługi Giphys w konwersacjach|Na|Po **włączeniu** goście mogą korzystać z usługi Giphys w konwersacjach; gdy **wyłączone**, nie mogą.|
|Ocena zawartości w usłudze Giphy|Umiarkowane|Po ustawieniu opcji **Zezwalaj na całą zawartość** goście mogą wstawiać wszystkie usługi Giphys w czatach, niezależnie od klasyfikacji zawartości. Po ustawieniu pozycji **Umiarkowany** goście mogą wstawiać usługę Giphys w czatach, ale będą umiarkowanie ograniczeni do zawartości dla dorosłych. Po ustawieniu pozycji **Ścisłe** goście mogą wstawiać usługę Giphys w czatach, ale nie będą mogli wstawiać zawartości dla dorosłych.|
|Używanie memów w konwersacjach|Na|Gdy **on**, goście mogą używać memów w rozmowach; gdy **wyłączone**, nie mogą.|
|Naklejki użytkowników w konwersacjach|Na|Po **włączeniu** goście mogą używać naklejek w rozmowach; gdy **wyłączone**, nie mogą.|
|Zezwalaj czytnikowi immersyjnej na wyświetlanie komunikatów|Na|Po **włączeniu** goście mogą wyświetlać komunikaty w Czytnik immersyjny; gdy są **wyłączone**, nie mogą.|

## <a name="sharepoint-and-onedrive-organization-level"></a>SharePoint i OneDrive (na poziomie organizacji)

**Rola administratora:** administrator SharePoint

Te ustawienia mają wpływ na wszystkie witryny w organizacji. Nie mają one bezpośredniego wpływu na Grupy Microsoft 365 ani Teams, jednak zalecamy dostosowanie tych ustawień do ustawień Grupy Microsoft 365 i Teams, aby uniknąć problemów ze środowiskiem użytkownika. (Jeśli na przykład udostępnianie gości jest dozwolone w Teams, ale nie SharePoint, goście w Teams nie będą mieli dostępu do karty Pliki, ponieważ pliki Teams są przechowywane w SharePoint).

### <a name="sharepoint-and-onedrive-sharing-settings"></a>ustawienia udostępniania SharePoint i OneDrive

Ponieważ OneDrive jest hierarchią lokacji w SharePoint, ustawienia udostępniania na poziomie organizacji mają bezpośredni wpływ na OneDrive podobnie jak inne SharePoint lokacje.

**Nawigacja:** SharePoint centrum administracyjne > <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**ZasadySharmoniowanie**</a>  > 

![Zrzut ekranu przedstawiający SharePoint ustawienia udostępniania na poziomie organizacji.](../media/external-sharing.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|SharePoint|Ktoś|Określa najbardziej permisywne uprawnienia do udostępniania dozwolone dla witryn SharePoint.|
|OneDrive|Ktoś|Określa najbardziej permisywne uprawnienia do udostępniania dozwolone dla OneDrive witryn. To ustawienie nie może być bardziej permisywne niż ustawienie SharePoint.|

### <a name="sharepoint-and-onedrive-advanced-sharing-settings"></a>SharePoint i OneDrive zaawansowanych ustawień udostępniania

**Nawigacja:** SharePoint centrum administracyjne > <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**ZasadySharmoniowanie**</a>  > 

![Zrzut ekranu przedstawiający SharePoint dodatkowych ustawień udostępniania na poziomie organizacji.](../media/external-sharing.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Ograniczanie udostępniania zewnętrznego według domeny|Wył.|To ustawienie umożliwia określenie listy dozwolonych lub zablokowanych domen do udostępniania. Po określeniu dozwolonych domen zaproszenia do udostępniania mogą być wysyłane tylko do tych domen. Po określeniu niedozwolonych domen nie można wysyłać zaproszeń do tych domen. <p> To ustawienie ma wpływ na wszystkie witryny SharePoint i OneDrive w organizacji.|
|Zezwalaj tylko użytkownikom w określonych grupach zabezpieczeń na udostępnianie zewnętrzne|Wył.|Jeśli chcesz ograniczyć liczbę osób, które mogą udostępniać gościom w SharePoint i OneDrive, możesz to zrobić, ograniczając udostępnianie do osób w określonych grupach zabezpieczeń. Te ustawienia nie mają wpływu na udostępnianie za pośrednictwem Grupy Microsoft 365 lub Teams. Goście zaproszeni za pośrednictwem grupy lub zespołu będą mieli również dostęp do skojarzonej witryny, chociaż udostępnianie dokumentów i folderów może być wykonywane tylko przez osoby w określonych grupach zabezpieczeń. <p> Dla każdej określonej grupy możesz wybrać, którzy z tych użytkowników mogą udostępniać linki Dowolna osoba.|
|Goście muszą zalogować się przy użyciu tego samego konta, na które wysyłane są zaproszenia do udostępniania|Wył.|Uniemożliwia gościom realizację zaproszeń do udostępniania witryn przy użyciu innego adresu e-mail niż zaproszenie zostało wysłane. <p> [integracja SharePoint i OneDrive z usługą Azure AD B2B (wersja zapoznawcza)](/sharepoint/sharepoint-azureb2b-integration-preview) nie używa tego ustawienia, ponieważ wszyscy goście są dodawani do katalogu na podstawie adresu e-mail, na który wysłano zaproszenie. Alternatywne adresy e-mail nie mogą być używane do uzyskiwania dostępu do witryny.|
|Zezwalaj gościom na udostępnianie elementów, których nie są właścicielami|Na|Po **włączeniu** goście mogą udostępniać przedmioty, które nie są ich własnością, innym użytkownikom lub gościom; gdy **nie** mogą. Goście mogą zawsze udostępniać elementy, dla których mają pełną kontrolę.|
|Osoby korzystające z kodu weryfikacyjnego muszą ponownie uwierzytelnić się po upływie tych wielu dni|Wył.|To ustawienie umożliwia wymaganie, aby użytkownicy uwierzytelniający się przy użyciu jednorazowego kodu dostępu musieli ponownie uwierzytelnić się po określonej liczbie dni.|
|Dostęp gościa do witryny lub OneDrive wygaśnie automatycznie po upływie tych wielu dni|Na|Jeśli administrator ustawił czas wygaśnięcia dostępu gościa, każdy gość, którego zaprosisz do witryny lub któremu udostępniasz poszczególne pliki i foldery, będzie miał dostęp przez określoną liczbę dni. Aby uzyskać więcej informacji, odwiedź [stronę Manage guest expiration for a site (Zarządzanie wygaśnięciem gościa dla witryny)](https://support.microsoft.com/en-us/office/manage-guest-expiration-for-a-site-25bee24f-42ad-4ee8-8402-4186eed74dea)

### <a name="sharepoint-and-onedrive-file-and-folder-link-settings"></a>ustawienia linku plików i folderów SharePoint i OneDrive

Gdy pliki i foldery są udostępniane w SharePoint i OneDrive, adresaci udostępniania otrzymują link z uprawnieniami do pliku lub folderu, zamiast mieć bezpośredni dostęp do samego pliku lub folderu. Dostępnych jest kilka typów łączy i można wybrać domyślny typ łącza prezentowany użytkownikom podczas udostępniania pliku lub folderu. Możesz również ustawić uprawnienia i opcje wygaśnięcia dla linków *Każdy* .

**Nawigacja:** SharePoint centrum administracyjne > <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**ZasadySharmoniowanie**</a>  > 

![Zrzut ekranu przedstawiający SharePoint ustawień udostępniania plików i folderów na poziomie organizacji.](../media/sharepoint-organization-files-folders-sharing-settings.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Łącza plików i folderów|Każda osoba z linkiem|Określa, który link udostępniania jest wyświetlany domyślnie, gdy użytkownik udostępnia plik lub folder. Użytkownicy mogą zmienić tę opcję przed udostępnieniem, jeśli chcą. Jeśli wartość domyślna to **Każda osoba z linkiem** i Udostępnianie *osób* nie jest dozwolone dla danej witryny, jako wartość domyślną dla tej witryny będą wyświetlane **tylko osoby w organizacji** .|
|Te linki muszą wygasnąć w ciągu tylu dni|Wyłączone (bez wygaśnięcia)|Określa liczbę dni po utworzeniu linku *Każdy* , który wygaśnie. Nie można odnowić wygasłych łączy. Utwórz nowy link, jeśli musisz kontynuować udostępnianie po wygaśnięciu.|
|Uprawnienia do pliku|Wyświetlanie i edytowanie|Określa poziomy uprawnień plików dostępne dla użytkowników podczas tworzenia linku *Każdy* . Jeśli wybrano **opcję Widok** , użytkownicy mogą tworzyć tylko łącza do plików *Dowolna osoba* z uprawnieniami do wyświetlania. Jeśli wybrano **opcję Wyświetl i edytuj** , użytkownicy mogą wybierać między uprawnieniami wyświetlania i wyświetlania i edytowania podczas tworzenia linku.|
|Uprawnienia folderu|Wyświetlanie, edytowanie i przekazywanie|Określa poziomy uprawnień folderu dostępne dla użytkowników podczas tworzenia linku *Każdy* . Jeśli wybrano opcję **Widok** , użytkownicy mogą tworzyć łącza do folderu *Każdy* tylko z uprawnieniami do wyświetlania. Jeśli **wybrano opcję Wyświetl, Edytuj i przekaż** , użytkownicy mogą wybierać między wyświetlaniem i wyświetlaniem, edytowaniem i przekazywaniem uprawnień podczas tworzenia linku.|

## <a name="sharepoint-site-level"></a>SharePoint (poziom witryny)

**Rola administratora:** administrator SharePoint

Ponieważ te ustawienia podlegają ustawieniu całej organizacji dla SharePoint, obowiązujące ustawienie udostępniania witryny może ulec zmianie, jeśli zmieni się ustawienie na poziomie organizacji. Jeśli wybierzesz tutaj ustawienie, a poziom organizacji zostanie później ustawiony na bardziej restrykcyjną wartość, ta witryna będzie działać z tą bardziej restrykcyjną wartością. Jeśli na przykład wybierzesz pozycję **Każdy** , a ustawienie na poziomie organizacji zostanie później ustawione na **Nowy i istniejących gości**, ta witryna będzie zezwalać tylko nowym i istniejącym gościom. Jeśli ustawienie na poziomie organizacji zostanie ustawione z powrotem na **Wartość Dowolna**, ta *witryna* ponownie zezwoli na łącza Każdy.

### <a name="site-sharing"></a>Udostępnianie witryny

W SharePoint można ustawić uprawnienia udostępniania gościa dla każdej witryny. To ustawienie ma zastosowanie zarówno do udostępniania witryn, jak i udostępniania plików i folderów. (*Udostępnianie* dowolnej osoby jest niedostępne w przypadku udostępniania witryny. Jeśli wybierzesz pozycję **Ktoś**, użytkownicy będą mogli udostępniać pliki i foldery przy użyciu linków *Każdy* , a sama witryna z nowymi i istniejącymi gośćmi).

Jeśli witryna ma zastosowaną etykietę poufności, ta etykieta może kontrolować ustawienia udostępniania zewnętrznego. Aby uzyskać więcej informacji, zobacz [Używanie etykiet poufności do ochrony zawartości w witrynach Microsoft Teams, Microsoft 365 i SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!NOTE]
> Ustawienia udostępniania witryn kanału można zmienić tylko za pomocą polecenia cmdlet [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) programu PowerShell.

**Nawigacja:** SharePoint centrum administracyjne > <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**aktywnych witryn**</a> > wybierz kartę **Zasady** > lokacji > **Edytowanie udostępniania zewnętrznego**

![Zrzut ekranu przedstawiający SharePoint ustawienia udostępniania zewnętrznego witryny.](../media/sharepoint-site-external-sharing-settings.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Zawartość witryny może być udostępniana|Różni się w zależności od typu witryny (zobacz poniższą tabelę)|Wskazuje typ udostępniania zewnętrznego dozwolony dla tej witryny. Dostępne tutaj opcje podlegają ustawień udostępniania na poziomie organizacji dla SharePoint.|

### <a name="site-file-and-folder-link-settings"></a>Ustawienia linku plików i folderów lokacji

Możesz ustawić wartości domyślne dla typu łącza i uprawnień oraz ustawień wygaśnięcia dla linków *Każdy* dla każdej witryny. Po ustawieniu na poziomie witryny te ustawienia zastępują ustawienia na poziomie organizacji. Należy pamiętać, że jeśli łącza *Dowolna osoba* są wyłączone na poziomie organizacji, *każda osoba* nie będzie dostępnym typem linku na poziomie witryny.

**Nawigacja:** SharePoint centrum administracyjne > <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**aktywnych witryn**</a> > wybierz kartę **Zasady** > lokacji > **Edytowanie udostępniania zewnętrznego**

![Zrzut ekranu przedstawiający SharePoint ustawień udostępniania linków na poziomie witryny.](../media/sharepoint-site-link-sharing-settings.png)

| Ustawienie | Domyślne | Opis |
|:-----|:-----|:-----|
|Ograniczanie udostępniania według domeny|Wył.|To ustawienie umożliwia określenie listy dozwolonych lub zablokowanych domen do udostępniania. Po określeniu dozwolonych domen zaproszenia do udostępniania mogą być wysyłane tylko do tych domen. Po określeniu niedozwolonych domen nie można wysyłać zaproszeń do tych domen. <p> Tego ustawienia nie można użyć do zastąpienia ograniczeń domeny ustawionych na poziomie organizacji lub usługi Azure AD.|
|Domyślny typ łącza udostępniania|Takie samo jak ustawienie na poziomie organizacji|To ustawienie umożliwia określenie domyślnego linku udostępniania przedstawionego użytkownikom w tej witrynie. Ta *sama opcja ustawienia na poziomie organizacji* jest definiowana przez kombinację ustawień organizacji i udostępniania witryn.|
|Ustawienia zaawansowane dla linków Dowolna osoba|Takie samo jak ustawienie na poziomie organizacji|Określa liczbę dni po utworzeniu linku *Każdy* dla pliku w tej witrynie, który wygaśnie. Nie można odnowić wygasłych łączy. Utwórz nowy link, jeśli musisz kontynuować udostępnianie po wygaśnięciu.|
|Domyślne uprawnienie łącza|Takie samo jak ustawienie na poziomie organizacji|To ustawienie umożliwia określenie domyślnego uprawnienia (Wyświetl lub Edytuj) do udostępniania linków utworzonych dla plików w tej witrynie.|

### <a name="default-site-sharing-settings"></a>Domyślne ustawienia udostępniania witryny

W poniższej tabeli przedstawiono domyślne ustawienie udostępniania dla każdego typu witryny.

| Typ witryny | Domyślne ustawienie udostępniania |
|:-----|:-----|
|Klasyczne|**Tylko osoby w organizacji**|
|OneDrive|**Ktoś**|
|Lokacje połączone z grupą (w tym Teams)|**Nowi i istniejący goście**, jeśli ustawienie Grupy Microsoft 365 **Zezwalaj właścicielom grup na dodawanie osób spoza organizacji do grup** jest **włączone**; w przeciwnym razie **tylko istniejący goście**|
|Komunikacja|**Tylko osoby w organizacji**|
|Nowoczesne witryny bez grupy (#STS3 TeamSite)|**Tylko osoby w organizacji**|

> [!NOTE]
> Główna witryna komunikacji (tenant-name.sharepoint.com) ma domyślne ustawienie udostępniania **Dla każdego**.

## <a name="see-also"></a>Zobacz też

[omówienie udostępniania zewnętrznego SharePoint i OneDrive](/sharepoint/external-sharing-overview)

[Dostęp gościa w Microsoft Teams](/MicrosoftTeams/guest-access)

[Dodawanie gości do Grupy Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)
