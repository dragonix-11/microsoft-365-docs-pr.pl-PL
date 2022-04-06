---
title: Limit czasu bezczynnej sesji dla Microsoft 365
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
description: Ustaw, jak długo sesja użytkownika będzie trwać w Microsoft 365, zanim minie ich czas.
ms.openlocfilehash: 215b900315b2d98b01a8cf87b14a6fa65289e121
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2022
ms.locfileid: "63705370"
---
# <a name="idle-session-timeout-for-microsoft-365-public-preview"></a>Limit czasu bezczynnej sesji dla Microsoft 365 (publiczna wersja zapoznawcza)

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

Użyj limitu czasu bezczynnej sesji, aby skonfigurować zasady dotyczące tego, jak długo użytkownicy są nieaktywni w organizacji, zanim zostaną wy zalogowani do Microsoft 365 aplikacji sieci Web. Ułatwia to ochronę poufnych danych firmowych i dodaje kolejną warstwę zabezpieczeń dla użytkowników końcowych, którzy pracują na urządzeniach innych niż firmowe lub udostępnione.

Gdy użytkownik dotrze do ustawionej przez Ciebie sesji limitu czasu bezczynności, otrzyma powiadomienie o tym, że ma się wypisać. Musi wybrać opcję pozostania zalogowanym lub automatycznie wypisać się ze wszystkich Microsoft 365 internetowych.

> [!IMPORTANT]
> Limit czasu bezczynny sesji nie wpływa na aplikacje Microsoft 365 i aplikacje mobilne.

## <a name="turn-on-idle-session-timeout"></a>Włączanie limitu czasu sesji bezczynności

Jeśli nie jesteś administratorem globalnym usługi Microsoft 365 ani administratorem Office 365, nie zobaczysz karty Zabezpieczenia i & **prywatności**.

1. Na karcie centrum administracyjne platformy Microsoft 365 wybierz pozycję Organizacja **Ustawienia** **->**[zabezpieczeń &](https://go.microsoft.com/fwlink/p/?linkid=2072756) prywatności i wybierz pozycję Limit czasu sesji **bezczynności**.  

2. W czasie **bezczynności sesji wybierz** przełącznik, aby go włączyć. Możesz wybrać ustawienie domyślne lub własny czas niestandardowy. Zanim sesja bezczynna zostanie włączona w organizacji, zajmie kilka minut.

> [!NOTE]
> Jeśli zasady limitu czasu sesji bezczynnej zostały ustawione dla aplikacji [sieci Web Outlook](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) i usługi [SharePoint Online](/sharepoint/sign-out-inactive-users), włączenie limitu czasu bezczynnej sesji w aplikacji centrum administracyjne platformy Microsoft 365 zastąpi ustawienia aplikacji sieci Web usługi Outlook i SharePoint.

Limit czasu bezczynny sesji jest jednym z wielu zabezpieczeń w programie Microsoft 365. Aby uzyskać informacje o innych zadaniach zabezpieczeń w programie Microsoft 365, zobacz [Najważniejsze zadania związane z zabezpieczeniami w programie Microsoft 365](../../security/top-security-tasks-for-remote-work.md).  

## <a name="what-users-will-see"></a>Co będą widzieć użytkownicy

Jeśli użytkownik był nieaktywny Microsoft 365 sieci Web przez wybrany okres, zostanie wyświetlony następujący monit. Musi wybrać opcję **Wypisać się** lub wypisać.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="Zrzut ekranu: Monituj o powiadomienie, że twoja sesja ma niezwłocznie wygasnąć. Wybierz opcję Pozostań zalogowany, aby nie wypisać się z aplikacji Microsoft 365 Web Apps":::

## <a name="details-about-idle-session-timeout"></a>Szczegóły dotyczące limitu czasu bezczynnej sesji

- Obsługiwane są Microsoft 365 sieci Web. Wkrótce zostanie dodanych więcej aplikacji internetowych.

    - Outlook Web App

    - OneDrive dla Firm

    - SharePoint Online (SPO)

    - Office.com i inne strony startowe

    - Office sieci Web (Word, Excel, PowerPoint)

    - Administracja Microsoft 365 klienta

- Działanie to każda interakcja użytkownika po stronie klienta odbywa się w kontekście aplikacji sieci Web. Na przykład kliknięcia myszą i naciśnięcie klawiszy klawiatury.  

- Limit czasu bezczynnej sesji działa w zależności od sesji przeglądarki. Aktywność użytkownika na tym ekranie Microsoft Edge w inny sposób niż jego aktywność w innych przeglądarkach, takich jak Google Chrome. Użytkownicy zostaną wy zalogowani na wszystkich kartach odpowiadających ich kontach w tej sesji przeglądarki.

- Po włączeniu limitu czasu bezczynnej sesji ma on zastosowanie do całej organizacji i nie można go ustawić w zakresie konkretnych użytkowników, jednostek organizacyjnych ani grup. Dostęp [warunkowy usługi Azure AD umożliwia](/azure/active-directory/conditional-access/) korzystanie z zasad dla różnych użytkowników i grup.

- Użytkownicy muszą być nieaktywni Microsoft 365 na kartach aplikacji sieci Web przez skonfigurowany czas trwania. Jeśli użytkownik jest aktywny na jednej karcie (powiedz OWA), gdy jest nieaktywny na innej karcie (na przykład SPO), zostanie on uznany za aktywnego i nie zostanie wypisać.  

- W takich przypadkach użytkownicy nie będą się wypisać.
    - Jeśli użytkownik otrzyma logowanie jednokrotne (SSO) do aplikacji sieci Web z połączonego konta urządzenia lub wybrał opcję Nie wyloguj się w czasie logowania. Aby uzyskać więcej informacji na temat ukrywania tej opcji dla organizacji, zobacz Dodawanie marki do strony [logowania organizacji](/azure/active-directory/fundamentals/customize-branding).
    - Jeśli urządzenie jest zarządzane (zgodne lub połączone z domeną) i używa obsługiwanej przeglądarki, na przykład Microsoft Edge lub Google Chrome (z rozszerzeniem [Windows Accounts](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji)). Aby ta funkcja nie była wyzwalana na urządzeniu zarządzanym, wymagana jest uprawnia Azure AD — wersja Premium P1 lub P2 oraz określone zasady dostępu warunkowego. Aby uzyskać więcej informacji, zobacz poniżej.

> [!IMPORTANT]
> Limit czasu sesji bezczynnej nie jest dostępny w przypadku Microsoft 365 obsługiwanej przez firmę 21Vianet ani Microsoft 365 Germany.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>Limit czasu bezczynny sesji na urządzeniach niezamenugonych  

Aby limit czasu bezczynnej sesji został wyzwolony na urządzeniach niezamaniowanych, musisz dodać zasady dostępu warunkowego w centrum administracyjnym usługi Azure AD.

1. Na stronie **dostęp warunkowy | Strona** Zasady w centrum administracyjnym usługi Azure AD, wybierz pozycję **Nowe zasady** i wprowadź nazwę zasad.

2. Wybierz **pozycję Użytkownicy lub tożsamości obciążenia pracą**, a następnie wybierz **pozycję Wszyscy użytkownicy**.

3. Wybierz **pozycję Aplikacje lub akcje w** chmurze, **Wybierz aplikacje** i wyszukaj więcej **Office 365**. Wybierz **Office 365**, a następnie **wybierz pozycję Wybierz**.  

4. Wybierz **pozycję Warunki**, **Aplikacje klienckie**, **Konfiguruj na tak**, **Przeglądarka**, a następnie pozycję **Gotowe**.

5. Wybierz **pozycję Sesja**, **Użyj ograniczeń wymuszonych przez aplikację**, a następnie wybierz **pozycję Wybierz**.

6. Włącz zasady i wybierz pozycję **Utwórz**.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>Czy istnieją jakiekolwiek scenariusze przeglądarek, w których funkcja limitu czasu bezczynnej sesji nie działa?  

Limit czasu sesji bezczynności nie jest obsługiwany, gdy w przeglądarce są wyłączone pliki cookie innych firm. Użytkownicy nie zobaczą żadnych monitów o wylogowanie. Zalecamy zachowanie ustawienia zapobiegania śledzeniu dla opcji [Zrównoważone (domyślne)](/microsoft-edge/web-platform/tracking-prevention) dla plików Microsoft Edge oraz plików cookie innych firm włączonych w innych przeglądarkach. Microsoft 365 i usługi przestały obsługiwać program Internet Explorer 11 od 17 sierpnia 2021 r.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>Jak się przygotować, jeśli moja organizacja używa już istniejącej aplikacji Outlook Sieci Web i zasad SharePoint limitów czasu bezczynności w trybie online?  

Jeśli korzystasz już z istniejącej aplikacji Outlook Sieci Web i zasad SharePoint limitów czasu bezczynności w trybie online, nadal możesz włączyć funkcję limitu czasu bezczynnej sesji. Gdy włączysz zasady limitu czasu bezczynności, mają ono pierwszeństwo przed istniejącymi zasadami usługi Outlook Sieci Web i SharePoint Online. Planujemy w niedalekiej przyszłości zaniechanie przyszłych Outlook aplikacji sieci Web i zasad SharePoint Online. Aby lepiej przygotować organizację, zalecamy włączenie limitu czasu bezczynnej sesji.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>Co się stanie, jeśli nieaktywnym użytkownikom dołączonej aplikacji sieci Web usługi Microsoft 365, ale aktywni w aplikacji sieci Web firmy Microsoft lub aplikacji saas, w której nie jest włączony limit czasu sesji bezczynny?  

Obsługiwane są Microsoft 365 sieci Web.

- Outlook Web App

- OneDrive dla Firm

- SharePoint Online (SPO)

- Office.com i inne strony startowe

- Office sieci Web (Word, Excel, PowerPoint)

- Administracja Microsoft 365 klienta

Jeśli pracujesz w innej aplikacji sieci Web przy użyciu tego samego konta, działanie w tej aplikacji nie zostanie zastosowane do limitu czasu bezczynnej sesji.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>Chcę wprowadzić zmiany w zasadach limitu czasu bezczynnej sesji lub je usunąć. Jak to zrobić?

Zaktualizuj zasady:

1. W centrum centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia** organizacji, przejdź do karty Prywatność &  zabezpieczeń i wybierz pozycję **Limit** czasu sesji bezczynności.

2. Z menu rozwijanego wybierz inną wartość limitu czasu, a następnie pozycję **Zapisz**.  

Usuń zasady:

1. W centrum centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia** organizacji, przejdź do karty Prywatność &  zabezpieczeń i wybierz pozycję **Limit** czasu sesji bezczynności.

2. Wyczyść **pole wyboru Włącz, aby ustawić** okres nieaktywności dla użytkowników, którzy mają być wy zalogowani do Office sieci Web, a następnie wybierz pozycję **Zapisz**.
