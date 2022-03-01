---
title: Konfigurowanie Microsoft 365 technicznej za pomocą tokenu uwierzytelniania usługi Azure AD
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
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
ms.openlocfilehash: f8bc7ee4647bf14521b9d29f616539acb95e7495
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2022
ms.locfileid: "63009763"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>Konfigurowanie Microsoft 365 technicznej za pomocą tokenu uwierzytelniania usługi Azure AD

## <a name="prerequisites-azure-ad-auth-token"></a>Wymagania wstępne (token uwierzytelniania usługi Azure AD)

Te wymagania wstępne są niezbędne do skonfigurowania integracji z usługą Microsoft 365 technicznej.

1. \[AAD administratorem\] Utwórz aplikację Azure AD dla ruchu wychodzącego w Microsoft 365 dzierżawie.

    1. Zaloguj się do portalu Azure Portal przy użyciu poświadczeń Microsoft 365 dzierżawy i przejdź do strony [Rejestracji](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) aplikacji, aby utworzyć nową aplikację.

    2. Wybierz **pozycję Konta tylko w tym katalogu organizacyjnym ({Microsoft-365-tenant-name} —** jedna **dzierżawa**) i wybierz pozycję Zarejestruj.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. Przejdź do **uwierzytelniania** i **wybierz pozycję Dodaj platformę**. Wybierz opcję **Sieci Web** i wprowadź adres URL przekierowania: `https://{your-servicenow-instance``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. Uzyskaj identyfikator klienta aplikacji, utwórz klucz tajny klienta i uzyskaj wartość.

1. \[AAD administratorem\] Utwórz interfejs API usługi Azure AD dla usługi Rest w ramach Microsoft 365 dzierżawy.

    1. Zaloguj się do portalu [Azure Portal](https://portal.azure.com/) przy użyciu poświadczeń Microsoft 365 dzierżawy i przejdź do strony Rejestracji aplikacji, aby utworzyć nową aplikację.

    1. Wybierz **pozycję Konta w tym katalogu organizacyjnym tylko {(Microsoft-365-tenant-name} — jedna dzierżawa)**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. Uzyskaj identyfikator klienta aplikacji, utwórz klucz tajny klienta i uzyskaj wartość.

1. \[AAD administratorem\] Utwórz aplikację Usługi Azure AD dla użytkownika rest w ramach Microsoft 365 dzierżawy.

    1. Zaloguj się do portalu [Azure Portal](https://portal.azure.com/) przy użyciu poświadczeń Microsoft 365 dzierżawy i przejdź do strony Rejestracji aplikacji, aby utworzyć nową aplikację.

    1. Wybierz **pozycję Konta w tym katalogu organizacyjnym tylko {(Microsoft-365-tenant-name} — jedna dzierżawa)**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. Uzyskaj identyfikator klienta aplikacji, utwórz klucz tajny klienta i uzyskaj wartość.

1. \[ServiceNow Admin\] Set up the Outbound OAuth Provider in ServiceNow.

    Jeśli zakres nie ma ustawienia **Globalne,****&gt; &gt;** przejdź do centrum Ustawienia aplikacji deweloperskiej i przełącz się na **globalną**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, czat lub wiadomość tekstowa Opis wygenerowany automatycznie":::

1. Przejdź do **rejestru aplikacji systemu OAuth&gt;**.

1. Utwórz nową aplikację, używając Połączenie **dostawcy OAuth innej** firmy i wprowadzając następujące wartości:

    - Identyfikator klienta: Jest to identyfikator klienta aplikacji utworzonej w kroku 1 w wymaganiach wstępnych (token \#uwierzytelniania usługi Azure AD).

    - Klucz tajny klienta: Jest to wartość tajna klienta aplikacji utworzonej w kroku 1 w wymaganiach wstępnych (token \#uwierzytelniania usługi Azure AD).

    - Domyślny typ przyznawania: Poświadczenia klienta

    - Adres URL tokenu: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - Przekieruj adres URL: `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany Opis aplikacji":::

1. \[ServiceNow Admin\] Aby skonfigurować dostawcę OIDC w programie ServiceNow, zapoznaj się z [dokumentacją online](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    Jeśli zakres nie ma ustawienia **Globalne,****&gt; przejdź do Ustawienia Deweloper &gt; i** przełącz się na **globalną**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, czat lub wiadomość tekstowa Opis wygenerowany automatycznie":::

1. Przejdź do **rejestru aplikacji systemu OAuth&gt;**.

1. Wybierz **pozycję Nowy**, a następnie **wybierz pozycję Utwórz nowy otwarty identyfikator Połączenie dostawcy**.

1. W **obszarze OAuth OIDC Provider Configuration** (Konfiguracja dostawcy OIDC) wybierz pozycję **Search** (Wyszukaj) i utwórz nową konfigurację dostawcy OIDC w obszarze **oidcproviderconfiguration.list\_\_** z tymi wartościami:

    - Dostawca OIDC: **{TenantName\_} Azure** (przykład: Contoso Azure)

    - Adres URL metadanych OIDC: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appId**

    - UserField: **Identyfikator użytkownika**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="Graficzny interfejs użytkownika, tekst, opis aplikacji wygenerowany automatycznie":::

1. Utwórz nową aplikację, wybierając pozycję **Skonfiguruj dostawcę OIDC, aby zweryfikować tokeny identyfikatorów** za pomocą tych wartości:

    - Nazwa: **{TenantName\_}\_applicationinboundapi\_\_** (przykład: contosoapplicationinboundapi\_\_\_)

    - Identyfikator klienta: Identyfikator klienta aplikacji utworzonej w wymaganiach wstępnych (token uwierzytelniania usługi Azure AD) w kroku \#2.

    - Klucz tajny klienta: Klucz tajny aplikacji utworzonej w wymaganiach wstępnych (token uwierzytelniania usługi Azure AD) w kroku \#2.

    - Konfiguracja dostawcy OAuth OIDC: dostawca OIDC utworzony w poprzednim kroku

    - Przekieruj adres URL: `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany Opis aplikacji":::

1. \[ServiceNow Admin\] Create Integration Users.

    Należy określić użytkownika integracji. Jeśli nie masz jeszcze użytkownika integracji lub chcesz utworzyć go specjalnie na tę integrację, **&gt;** przejdź do strony Użytkownicy organizacji, aby utworzyć nowego użytkownika. Wartość identyfikatora użytkownika to **identyfikator** klienta aplikacji utworzony w wymaganiach [wstępnych (token uwierzytelniania usługi Azure AD)](#prerequisites-azure-ad-auth-token).

    Jeśli tworzysz nowego użytkownika integracji, sprawdź opcję **Tylko dostęp do usługi sieci Web** . Musisz także przyznać temu użytkownikowi rolę **menedżera zdarzeń\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany Opis aplikacji":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[OPTIONAL\] Allow the IP addresses to the IP addresses to Microsoft 365 support integration

Jeśli Twoja firma ogranicza dostęp do Internetu przy użyciu własnych zasad, włącz dostęp sieciowy do usługi integracji usługi Microsoft 365, zezwalając na poniższe adresy IP zarówno dla przychodzącego, jak i wychodzącego dostępu do interfejsu API.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> To polecenie terminalu wyświetla listę wszystkich aktywnych ip usługi na Microsoft 365 pomocy technicznej:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Konfigurowanie aplikacji integracji Microsoft 365 pomocy technicznej

Aplikację Microsoft 365 pomocą techniczną można skonfigurować w obszarze Microsoft 365 technicznej.

Te kroki są wymagane do skonfigurowania integracji między wystąpieniem ServiceNow a Microsoft 365 technicznej.

1. \[Administrator ServiceNow Przełącz\] zakres na Microsoft 365 **integracji z obsługą techniczną**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany opis w tabeli":::

1. \[ServiceNow Admin\] Go to **Microsoft 365 Setup pomocy &gt; technicznej,** aby otworzyć przepływ pracy integracji.

    > [!NOTE]
    > Jeśli zostanie wyświetlony błąd "Operacja odczytu dla "oauthentity\_" z zakresu "xmiomsm365assis\_\_\_", został odrzucony ze względu na zasady dostępu krzyżowego tabeli", został on spowodowany przez Zasady dostępu do tabeli. Upewnij się, że dla tabeli **oauthentity &gt; jest** zaznaczona opcja Wszystkie zakresy aplikacji Może odczytywać\_.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Select **Agree** to the consent prompt to continue.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Configure the environment and setup type.
    Jeśli ta instalacja znajduje się w środowisku testowym, wybierz opcję To jest środowisko testowe. Możesz szybko wyłączyć tę opcję po instalacji i ukończeniu wszystkich testów później.
    Jeśli dane wystąpienie zezwala na uwierzytelnianie podstawowe dla połączeń przychodzących, wybierz pozycję Tak i zapoznaj się z procesem [konfiguracji uwierzytelniania podstawowego](servicenow-basic-authentication.md). W przeciwnym razie wybierz **pozycję Nie** i kliknij pozycję **Rozpocznij konfigurowanie**. 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Enter your Microsoft 365 tenant domain.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Configure Outbound OAuth provider.
    1. Skonfiguruj dostawcę wychodzącego protokołu OAuth.
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych kliknij pozycję Gotowe. W przeciwnym razie postępuj zgodnie z instrukcjami kreatora, aby utworzyć potrzebną rejestrację aplikacji w AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::
    1. Zarejestruj aplikację ServiceNow OAuth.
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych wybierz nowo utworzoną rejestrację aplikacji OAuth i kliknij przycisk Dalej. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć jednostkę w usłudze ServiceNow, a następnie wybierz nową rejestrację aplikacji.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[ServiceNow Admin\] Configure Inbound settings.
    1. Skonfiguruj aplikację poczty przychodzącej AAD przychodzącej.
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych kliknij przycisk Gotowe, aby przejść do następnego kroku. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć AAD rejestracji aplikacji na temat łączności przychodzącej.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::
    1. Skonfiguruj dostawcę usług ServiceNow External OpenID Połączenie Provider (OIDC Provider).
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych wybierz nowo utworzoną jednostkę i kliknij pozycję Gotowe. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć jednostkę w serwisie ServiceNow, a następnie wybierz nową rejestrację aplikacji zewnętrznego dostawcy OIDC.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::
    1. Skonfiguruj AAD aplikacji dla użytkownika integracji ruchu przychodzącego.
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych kliknij przycisk Gotowe, aby przejść do następnego kroku. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć AAD rejestracji aplikacji dla przychodzącego użytkownika REST (użytkownika integracji).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::
    1. Skonfiguruj użytkownika integracji.
    1. Po zakończeniu wykonywania instrukcji w sekcji wymagań wstępnych wybierz nowo utworzoną jednostkę i kliknij przycisk Dalej. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć użytkownika integracji w usłudze ServiceNow, a następnie wybierz encję.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[Microsoft 365 administratorem dzierżawy\] Ukończ integrację.

    Sprawdź, czy poniższe informacje są poprawne. W tej chwili NIE **wybieraj** przycisku Dalej.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

    1. Przejdź do **Administracja Microsoft 365 Ustawienia &gt; Ustawienia &gt; organizacji &gt; Profile organizacji**.

    1. Konfigurowanie ustawień integracji pomocy technicznej:

    Wybierz **kartę Informacje podstawowe** > **naprawu** >  **serwisowegoServiceNow** i wprowadź wartość **Identyfikator** aplikacji wychodzącej w polu Identyfikator aplikacji, aby wydać **token** uwierzytelniania. Ten identyfikator aplikacji wychodzącej znajduje się w kroku 6 . Ukończ integrację utworzoną w wymaganiach wstępnych [(token uwierzytelniania usługi Azure AD).](#prerequisites-azure-ad-auth-token)

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

    1. Na karcie **Repozytoria** wybierz pozycję **Nowe repozytorium** i zaktualizuj je przy użyciu następujących ustawień:

    - Repozytorium: Wartość **identyfikatora repozytorium** z "Krok 6. Ukończ integrację".

    - Punkt końcowy: **Wartość punktu** końcowego z "Krok 6 — Ukończ integrację".

    - Typ uwierzytelniania: wybierz **AAD uwierzytelniania**.

    - Identyfikator klienta: **Wartość identyfikatora klienta** z kroku 6 — Ukończ integrację.

    - Klucz tajny klienta: tajny dostawcy przychodzącego protokołu OAuth, który został utworzony w kroku 2 wymagań wstępnych (token \#uwierzytelniania usługi Azure AD).

    - Nazwa użytkownika usługi Rest: Wartość User **Name** z kroku 6 — Ukończ integrację, czyli identyfikator klienta aplikacji  utworzonej w kroku 3 w wymaganiach wstępnych (token uwierzytelniania usługi Azure AD\#).

    - Rest user password: The App Secret of the application that was created in Prerequisites (Azure AD Auth Token) step \#3.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany Opis aplikacji":::

    1. Wróć do serviceNow.

    1. Wybierz **pozycję Dalej** , aby ukończyć integrację.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::
    Aplikacja Microsoft 365 będzie wykonywać testy w celu zapewnienia działania integracji. Jeśli występuje problem z konfiguracją, zostanie wyświetlony komunikat o błędzie z wyjaśnieniem, co należy naprawić. W przeciwnym razie aplikacja jest gotowa.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="Graficzny interfejs użytkownika, tekst, aplikacja, opis e-mail wygenerowany automatycznie":::

1. \[Administrator ServiceNow Włącz\] integrację pomocy technicznej firmy Microsoft dla istniejącego użytkownika.

    Microsoft 365 jest włączona integracja z pomocą techniczną dla użytkownika z jedną z tych ról:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[OPCJONALNIe\] \[Użytkownik z rolą xmiomsm365assis.administrator\_\_\_ link\] Microsoft 365 konta administratora.

    Jeśli jakiś użytkownik ma rolę xmiomsm365assis.administrator\_\_\_ i używa różnych kont Microsoft 365 do zarządzania obsługą klienta usługi Microsoft 365, musi przejść do pomocy technicznej usługi Microsoft 365, aby skonfigurować swój adres e-mail administratora usługi Microsoft 365&gt;.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Graficzny interfejs użytkownika, tekst, opis aplikacji wygenerowany automatycznie":::
