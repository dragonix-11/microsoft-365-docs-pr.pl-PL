---
title: Konfigurowanie integracji pomocy technicznej z usługą ServiceNow — uwierzytelnianie podstawowe
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Przewodnik po instalacji i konfiguracji certyfikowanej dla programu ServiceNow z zakresem.
ms.openlocfilehash: 23fab410b17cea9635c63b0ed0e4225d158dfdc8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323853"
---
# <a name="configure-support-integration-with-servicenow---basic-authentication"></a>Konfigurowanie integracji pomocy technicznej z usługą ServiceNow — uwierzytelnianie podstawowe

## <a name="prerequisites-basic-authentication"></a>Wymagania wstępne (uwierzytelnianie podstawowe)

Te wymagania wstępne są niezbędne do skonfigurowania integracji z **usługą Microsoft 365 technicznej**.

1. \[AAD administratorem\] Utwórz aplikację usługi Azure AD w ramach Microsoft 365 dzierżawy usługi.

    1. Zaloguj się do portalu Azure Portal przy użyciu poświadczeń Microsoft 365 dzierżawy i przejdź do strony [Rejestracji](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) aplikacji, aby utworzyć nową aplikację.

    1. Wybierz **pozycję Konta tylko w tym katalogu organizacyjnym ({Microsoft-365-tenant-name} —** jedna **dzierżawa**) i wybierz pozycję Zarejestruj.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. Przejdź do **uwierzytelniania** i **wybierz pozycję Dodaj platformę**. Wybierz opcję **Sieci Web** i wprowadź adres URL przekierowania: `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. Uzyskaj identyfikator klienta aplikacji, utwórz klucz tajny klienta i uzyskaj wartość.

1. \[ServiceNow Admin\] Set up the Outbound OAuth Provider in ServiceNow.

    Jeśli zakres nie ma ustawienia **Globalne,****&gt; przejdź do Ustawienia Deweloper &gt; i** przełącz się na **globalną**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, czat lub wiadomość tekstowa Opis wygenerowany automatycznie":::

1. Przejdź do **rejestru aplikacji systemu OAuth&gt;**.

1. Utwórz nową aplikację, używając opcji **Połączenie dostawcy OAuth innej** firmy i wprowadzając następujące wartości:

    - Identyfikator klienta: Identyfikator klienta aplikacji utworzonej w kroku \#1.

    - Klucz tajny klienta: Wartość tajna klienta aplikacji utworzonej w kroku \#1.

    - Domyślny typ przyznawania: Poświadczenia klienta

    - Adres URL tokenu: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - Przekieruj adres URL: `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany Opis aplikacji":::

1. \[ServiceNow Admin\] Set up the Inbound OAuth Provider.

    Jeśli zakres nie ma ustawienia **Globalne,****&gt; przejdź do Ustawienia aplikacje &gt;** deweloperskiej i przełącz na **globalną**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, czat lub wiadomość tekstowa Opis wygenerowany automatycznie":::

1. Przejdź do **rejestru aplikacji systemu OAuth&gt;**.

1. Utwórz nową aplikację, używając opcji **Utwórz punkt końcowy interfejsu API OAuth dla klientów zewnętrznych** . Nazwij dostawcę przychodzącego protokołu OAuth i pozostaw wszystkie inne pola z ich wartościami domyślnymi.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image7.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image7.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany Opis aplikacji":::

1. \[ServiceNow Admin\] Create an integration user( Utwórz użytkownika integracji).

    Należy określić użytkownika integracji. Jeśli nie masz jeszcze użytkownika integracji lub chcesz utworzyć go specjalnie na tę integrację, **&gt;** przejdź do strony Użytkownicy organizacji, aby utworzyć nowego użytkownika.

    Jeśli tworzysz nowego użytkownika integracji, sprawdź opcję Tylko dostęp **do usługi sieci Web** . Musisz także przyznać temu użytkownikowi rolę **menedżera zdarzeń\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image8.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image8.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany Opis aplikacji":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[OPTIONAL\] Allow the IP addresses to the IP addresses to Microsoft 365 support integration

Jeśli Twoja firma ogranicza dostęp do Internetu przy użyciu własnych zasad, włącz dostęp sieciowy do usługi integracji usługi Microsoft 365, zezwalając na poniższe adresy IP zarówno dla przychodzącego, jak i wychodzącego dostępu do interfejsu API:

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> To polecenie terminalu wyświetla listę wszystkich aktywnych ip usługi na Microsoft 365 pomocy technicznej:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Konfigurowanie aplikacji Microsoft 365 i integracji

Aplikację Microsoft 365 pomocą techniczną można skonfigurować w obszarze Microsoft 365 technicznej.

Te kroki są wymagane do skonfigurowania integracji między wystąpieniem ServiceNow a Microsoft 365 technicznej.

1. \[Administrator ServiceNow Przełącz\] zakres na Microsoft 365 **integracji z obsługą techniczną**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany opis w tabeli":::

1. \[ServiceNow Admin\] Go to **Microsoft 365 Setup pomocy &gt; technicznej,** aby otworzyć przepływ pracy integracji.

    > [!NOTE]
    > Jeśli zostanie wyświetlony błąd "Operacja odczytu dla "oauthentity\_" z zakresu "xmiomsm365assis\_\_\_", został odrzucony ze względu na zasady dostępu krzyżowego tabeli", został on spowodowany przez Zasady dostępu do tabeli. Upewnij się, że dla tabeli **oauthentity &gt; jest** zaznaczona opcja Wszystkie zakresy aplikacji Może odczytywać\_.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image10.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image10.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Select **Agree** to continue.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-1.png" lightbox="../../media/ServiceNow-guide/snowbasic-1.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Configure the environment and setup type.

    Jeśli ta instalacja znajduje się w środowisku testowym, wybierz opcję To jest środowisko testowe. Możesz szybko wyłączyć tę opcję po instalacji i ukończeniu wszystkich testów później.
    Jeśli Twoje wystąpienie zezwala na uwierzytelnianie podstawowe dla połączeń przychodzących, wybierz pozycję Tak, w przeciwnym razie zapoznaj się z konfiguracją [zaawansowaną z AAD](servicenow-aad-oauth-token.md). :::image type="content" source="../../media/ServiceNow-guide/snowbasic-2.png" lightbox="../../media/ServiceNow-guide/snowbasic-2.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Enter your Microsoft 365 tenant domain.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-3.png" lightbox="../../media/ServiceNow-guide/snowbasic-3.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin Configure\] Outbound settings.
    1. Zarejestruj aplikację Azure Active Directory (AAD).
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych kliknij pozycję **Gotowe**. W przeciwnym razie postępuj zgodnie z instrukcjami kreatora, aby utworzyć potrzebną rejestrację aplikacji w AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-4.png" lightbox="../../media/ServiceNow-guide/snowbasic-4.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

    1. Zarejestruj aplikację ServiceNow OAuth.
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych wybierz nowo utworzoną rejestrację aplikacji OAuth i kliknij przycisk Dalej. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć jednostkę w usłudze ServiceNow, a następnie wybierz nową rejestrację aplikacji.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-5.png" lightbox="../../media/ServiceNow-guide/snowbasic-5.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Configure Inbound settings.
    1. Skonfiguruj punkt końcowy przychodzącego interfejsu API OAuth.
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych wybierz nowo utworzoną rejestrację aplikacji OAuth i kliknij przycisk Gotowe. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć encję w następnie wybierz nową rejestrację punktu końcowego REST.
     
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-6.png" lightbox="../../media/ServiceNow-guide/snowbasic-6.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

    1. Skonfiguruj użytkownika integracji.
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych wybierz nowo utworzonego użytkownika integracji i kliknij przycisk Dalej. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć jednostkę w usłudze ServiceNow, a następnie wybierz nowego użytkownika integracji.
    
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-7.png" lightbox="../../media/ServiceNow-guide/snowbasic-7.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::


1. \[Microsoft 365 administratorem dzierżawy\] Ukończ integrację w portalu Administracja Microsoft 365 sieci.

    Sprawdź, czy poniższe informacje są poprawne. W tej chwili NIE **wybieraj** przycisku Dalej.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image17.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image17.png" alt-text="Graficzny interfejs użytkownika, tekst, opis aplikacji wygenerowany automatycznie":::

1. Przejdź do **Administracja Microsoft 365 Ustawienia &gt; Ustawienia &gt; organizacji &gt; Profile organizacji**.

1. Konfigurowanie ustawień integracji pomocy technicznej:

    Wybierz **kartę Informacje podstawowe** > **naprawu** >  **serwisowegoServiceNow** i wprowadź wartość **Identyfikator** aplikacji wychodzącej w polu Identyfikator aplikacji, aby wydać **token** uwierzytelniania. Ten identyfikator aplikacji wychodzącej znajduje się w kroku 6— Ukończ integrację utworzoną w kroku 1, który został utworzony w kroku [Wstępnie wymagane (uwierzytelnianie podstawowe\#](#prerequisites-basic-authentication)).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. Na karcie **Repozytoria** wybierz pozycję **Nowe repozytorium** i zaktualizuj je przy użyciu następujących ustawień:

    - Repozytorium: Wartość **identyfikatora repozytorium** z kroku 6 — Ukończ integrację.

    - Punkt końcowy: Wartość **punktu** końcowego z kroku 6 — Ukończ integrację.

    - Typ uwierzytelniania: Wybierz **pozycję Podstawowe uwierzytelnianie**.

    - Identyfikator klienta: **Wartość identyfikatora klienta** z kroku 6 — Ukończ integrację.

    - Klucz tajny klienta: tajny dostawcy przychodzącego protokołu OAuth, który został utworzony w kroku 3 w \#wersji Wstępne (uwierzytelnianie podstawowe).

    - Odświeżanie wygaśnięcia tokenu: 864000

    - Nazwa użytkownika rest: **Wartość User Name** (Nazwa użytkownika) z kroku 6. Ukończ integrację.

    - Hasło użytkownika rest: hasło użytkownika integracji utworzone w kroku 4 w obszarze [Wymagania wstępne (uwierzytelnianie podstawowe\#](#prerequisites-basic-authentication)).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image19.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image19.png" alt-text="Graficzny interfejs użytkownika, automatycznie generowany jest opis aplikacji":::

1. Wróć do serviceNow.

1. Wybierz **pozycję Dalej** , aby ukończyć integrację.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image20.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image20.png" alt-text="Graficzny interfejs użytkownika, aplikacja, opis witryny sieci Web wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Test the connection After completing the previous step, click **Test connection**.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-8.png" lightbox="../../media/ServiceNow-guide/snowbasic-8.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::
    Aplikacja Microsoft 365 będzie wykonywać testy w celu zapewnienia działania integracji. Jeśli występuje problem z konfiguracją, zostanie wyświetlony komunikat o błędzie z wyjaśnieniem, co należy naprawić. W przeciwnym razie aplikacja jest gotowa.
     :::image type="content" source="../../media/ServiceNow-guide/snowbasic-9.png" lightbox="../../media/ServiceNow-guide/snowbasic-9.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[Administrator ServiceNow Włącz\] integrację pomocy technicznej firmy Microsoft dla istniejącego użytkownika.

    Microsoft 365 jest włączona integracja z pomocą techniczną dla użytkownika z jedną z tych ról:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[OPCJONALNIE\] [Użytkownik z rolą x_mioms_m365_assis.administrator] Połącz Administracja Microsoft 365 konto.

    Jeśli jakiś użytkownik ma rolę x_mioms_m365_assis.administrator i do zarządzania sprawą techniczną w programie Microsoft 365 Microsoft 365 używa różnych kont, musi przejść do pomocy technicznej usługi Microsoft 365 > Link Account, aby skonfigurować swój adres e-mail Microsoft 365 administratora.
    
    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image21.png" alt-text="Graficzny interfejs użytkownika, tekst, opis aplikacji wygenerowany automatycznie":::
