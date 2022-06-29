---
title: Limit czasu bezczynności sesji dla platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Adm_TOC
description: Określ, jak długo potrwa sesja użytkownika na platformie Microsoft 365, zanim upłynął limit czasu.
ms.openlocfilehash: 611541ebc16c3ee8c187b8fc1a5b33661b221897
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487482"
---
# <a name="idle-session-timeout-for-microsoft-365"></a>Limit czasu bezczynności sesji dla platformy Microsoft 365

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

Użyj limitu czasu bezczynnej sesji, aby skonfigurować zasady dotyczące czasu, przez jaki użytkownicy są nieaktywni w organizacji przed wylogowaniem się z aplikacji internetowych platformy Microsoft 365. Pomaga to chronić poufne dane firmowe i dodaje kolejną warstwę zabezpieczeń dla użytkowników końcowych, którzy pracują na urządzeniach innych niż firmowe lub udostępnione.

Gdy użytkownik osiągnie ustawioną bezczynną sesję limitu czasu, otrzyma powiadomienie, że ma zostać wylogowywane. Muszą wybrać opcję pozostania zalogowany lub zostaną automatycznie wylogowany ze wszystkich aplikacji internetowych platformy Microsoft 365.

> [!IMPORTANT]
> Limit czasu bezczynności sesji nie ma wpływu na aplikacje klasyczne i mobilne platformy Microsoft 365.

## <a name="turn-on-idle-session-timeout"></a>Włącz limit czasu bezczynności sesji

Jeśli nie jesteś administratorem globalnym platformy Microsoft 365 lub Office 365, nie zobaczysz karty **Zabezpieczenia & prywatności**.

1. W Centrum administracyjne platformy Microsoft 365 wybierz kartę [Zabezpieczenia ustawień](https://go.microsoft.com/fwlink/p/?linkid=2072756) **->****organizacji** & prywatności, a następnie wybierz pozycję **Limit czasu sesji bezczynności**.  

2. W obszarze **Limit czasu sesji bezczynności** wybierz przełącznik, aby go włączyć. Możesz wybrać ustawienie domyślne lub wybrać własny czas niestandardowy. Zanim bezczynna sesja zostanie włączona w organizacji, upłynie kilka minut.

> [!NOTE]
> Jeśli skonfigurowano zasady limitu czasu bezczynności sesji dla [aplikacji internetowej Outlook](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) i usługi [SharePoint Online](/sharepoint/sign-out-inactive-users), włączenie limitu czasu bezczynności sesji w Centrum administracyjne platformy Microsoft 365 zastąpi ustawienia aplikacji internetowej outlook i programu SharePoint.

Limit czasu bezczynności sesji jest jednym z wielu środków zabezpieczeń w usłudze Microsoft 365. Aby dowiedzieć się więcej o innych zadaniach zabezpieczeń w usłudze Microsoft 365, zobacz [Najważniejsze zadania zabezpieczeń w usłudze Microsoft 365](../../security/top-security-tasks-for-remote-work.md).  

## <a name="what-users-will-see"></a>Co zobaczą użytkownicy

Gdy użytkownik jest nieaktywny w aplikacjach internetowych platformy Microsoft 365 w wybranym okresie, zobaczy następujący monit. Muszą wybrać pozycję **Pozostań zalogowany** lub wylogować się.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="Zrzut ekranu: monit informujący o tym, że sesja wkrótce wygaśnie. Wybierz pozycję Pozostań zalogowany, aby nie wylogować się z aplikacji internetowych platformy Microsoft 365":::

## <a name="details-about-idle-session-timeout"></a>Szczegóły dotyczące limitu czasu bezczynności sesji

- Obsługiwane są następujące aplikacje internetowe platformy Microsoft 365. Więcej aplikacji internetowych zostanie dodanych wkrótce.

    - Outlook Web App

    - OneDrive dla Firm

    - SharePoint Online (SPO)

    - Office.com i inne strony początkowe

    - Pakiet Office (Word, Excel, PowerPoint) w Internecie

    - centrum Administracja Microsoft 365

- Działanie odnosi się do dowolnej interakcji użytkownika po stronie klienta w kontekście aplikacji internetowej. Na przykład kliknięcia myszą i naciśnięcia klawiatury.  

- Limit czasu sesji bezczynności działa na podstawie sesji w przeglądarce. Aktywność użytkownika w przeglądarce Microsoft Edge jest traktowana inaczej niż jego aktywność w innych przeglądarkach, takich jak Google Chrome. Użytkownicy będą wylogowali się ze wszystkich kart odpowiadających ich kontu w tej sesji przeglądarki.

- Po włączeniu limitu czasu bezczynności sesji ma on zastosowanie do całej organizacji i nie może być ograniczony do określonych użytkowników, jednostek organizacyjnych ani grup. Użyj [Azure AD zasad dostępu warunkowego](/azure/active-directory/conditional-access/) dla różnych użytkowników i grup, aby uzyskać dostęp do programu SharePoint i Exchange Online.

- Użytkownicy muszą być nieaktywni na wszystkich kartach aplikacji internetowej platformy Microsoft 365 przez skonfigurowany czas trwania. Jeśli użytkownik jest aktywny na jednej karcie (np. OWA), gdy jest nieaktywny na innej karcie (np. SPO), zostanie uznany za aktywnego i nie zostanie wylogowywane.  

- Użytkownicy nie będą wylogować się w tych przypadkach.
    - Jeśli użytkownik pobierze logowanie jednokrotne do aplikacji internetowej z konta dołączonego do urządzenia lub wybierze pozycję **Pozostań zalogowany podczas** logowania. Aby uzyskać więcej informacji na temat ukrywania tej opcji dla organizacji, zobacz [Dodawanie znakowania do strony logowania organizacji](/azure/active-directory/fundamentals/customize-branding).
    - Jeśli znajdują się na urządzeniu zarządzanym (zgodnym lub przyłączonym do domeny) i korzysta z obsługiwanej przeglądarki, takiej jak Microsoft Edge lub Google Chrome (z [rozszerzeniem Konta systemu Windows](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji)). Aby ta funkcja nie była wyzwalana na zarządzanym urządzeniu, wymagana jest kwalifikująca się subskrypcja Azure AD — wersja Premium P1 lub P2 oraz określone zasady dostępu warunkowego. Aby uzyskać więcej informacji, zobacz poniżej.

> [!IMPORTANT]
> Limit czasu bezczynności sesji nie jest dostępny dla platformy Microsoft 365 obsługiwanej przez firmę 21Vianet lub Microsoft 365 Germany.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>Limit czasu bezczynności sesji na urządzeniach niezarządzanych  

Aby limit czasu bezczynności sesji został wyzwolony na urządzeniach niezarządzanych, należy dodać zasady dostępu warunkowego w centrum administracyjnym Azure AD.

1. Na **| dostępu warunkowego Strona Zasady** centrum administracyjnego Azure AD wybierz pozycję **Nowe zasady** i wprowadź nazwę zasad.

2. Wybierz pozycję **Użytkownicy lub tożsamości obciążenia**, a następnie wybierz pozycję **Wszyscy użytkownicy**.

3. Wybierz pozycję **Aplikacje lub akcje w chmurze**, **Wybierz aplikacje** i wyszukaj **Office 365**. Wybierz **pozycję Office 365**, a następnie **pozycję Wybierz**.  

4. Wybierz pozycję **Warunki**, **Aplikacje klienckie**, **Konfiguruj na wartość Tak**, **Przeglądarka**, a następnie wybierz pozycję **Gotowe**.

5. Wybierz pozycję **Sesja**, **Użyj ograniczeń wymuszonych przez aplikację**, a następnie **pozycję Wybierz**.

6. Włącz zasady i wybierz pozycję **Utwórz**.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>Czy istnieją jakieś przeglądarki lub scenariusze przeglądarki, w których funkcja limitu czasu bezczynności sesji nie działa?  

Limit czasu bezczynności sesji nie jest obsługiwany, gdy pliki cookie innych firm są wyłączone w przeglądarce. Użytkownicy nie będą widzieć żadnych monitów o wylogowanie. Zalecamy zachowanie ustawienia zapobiegania śledzeniu na wartość [Zrównoważone (domyślne)](/microsoft-edge/web-platform/tracking-prevention) dla przeglądarki Microsoft Edge i obsługę plików cookie innych firm w innych przeglądarkach. Aplikacje i usługi platformy Microsoft 365 przestały obsługiwać program Internet Explorer 11 od 17 sierpnia 2021 r.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>Jak przygotować się, jeśli moja organizacja korzysta już z istniejących zasad limitu czasu bezczynności aplikacji Outlook i usługi SharePoint Online?  

Jeśli już używasz istniejących zasad limitu czasu bezczynności aplikacji Outlook i usługi SharePoint Online, nadal możesz włączyć funkcję limitu czasu bezczynności sesji. Włączenie zasad limitu czasu bezczynności ma pierwszeństwo przed istniejącą aplikacją internetową programu Outlook i zasadami usługi SharePoint Online. Planujemy w najbliższej przyszłości wycofać istniejącą aplikację internetową outlook i zasady usługi SharePoint Online. Aby lepiej przygotować organizację, zalecamy włączenie limitu czasu bezczynności sesji.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>Co się stanie, jeśli jestem nieaktywny w dołączonej aplikacji internetowej platformy Microsoft 365, ale aktywny w aplikacji internetowej firmy Microsoft lub aplikacji internetowej SaaS, która nie ma włączonego limitu czasu bezczynności sesji?  

Obsługiwane są następujące aplikacje internetowe platformy Microsoft 365.

- Outlook Web App

- OneDrive dla Firm

- SharePoint Online (SPO)

- Office.com i inne strony początkowe

- Pakiet Office (Word, Excel, PowerPoint) w Internecie

- centrum Administracja Microsoft 365

Jeśli pracujesz nad inną aplikacją internetową z tym samym kontem, działanie w tej aplikacji internetowej nie zostanie zastosowane do limitu czasu bezczynnej sesji.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>Chcę wprowadzić zmiany w zasadach limitu czasu bezczynności sesji lub usunąć je. Jak mogę to zrobić?

Zaktualizuj zasady:

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia organizacji**, przejdź do karty **Zabezpieczenia & prywatność** i wybierz pozycję **Limit czasu sesji bezczynności**.

2. Z menu rozwijanego wybierz inną wartość limitu czasu, a następnie **pozycję Zapisz**.  

Usuń zasady:

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia organizacji**, przejdź do karty **Zabezpieczenia & prywatność** i wybierz pozycję **Limit czasu sesji bezczynności**.

2. Usuń **zaznaczenie pola wyboru Włącz, aby ustawić okres braku aktywności dla użytkowników, którzy mają być wylogowywane z aplikacji internetowych pakietu Office** , i wybierz pozycję **Zapisz**.
