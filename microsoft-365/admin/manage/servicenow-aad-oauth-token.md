---
title: Konfigurowanie Microsoft 365 integracji z tokenem uwierzytelniania usługi Azure AD
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
description: Przewodnik po instalacji i konfiguracji certyfikowanej aplikacji o określonym zakresie dla usługi ServiceNow.
ms.openlocfilehash: d3991355779228cf1562e23ddd0e97cb37225a43
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093751"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>Konfigurowanie Microsoft 365 integracji z tokenem uwierzytelniania usługi Azure AD

## <a name="prerequisites-azure-ad-auth-token"></a>Wymagania wstępne (token uwierzytelniania usługi Azure AD)

Te wymagania wstępne są niezbędne do skonfigurowania integracji Microsoft 365 pomocy technicznej.

1. \[administrator\] AAD Utwórz aplikację usługi Azure AD dla ruchu wychodzącego w ramach dzierżawy Microsoft 365.

    1. Zaloguj się do witryny Azure Portal przy użyciu poświadczeń dzierżawy Microsoft 365 i przejdź do [strony Rejestracje aplikacji](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade), aby utworzyć nową aplikację.

    2. Wybierz pozycję **Konta tylko w tym katalogu organizacyjnym ({Tylko nazwa-dzierżawy microsoft-365-tenant} — pojedyncza dzierżawa)** i wybierz pozycję **Zarejestruj**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. Przejdź do pozycji **Uwierzytelnianie** i wybierz **pozycję Dodaj platformę**. Wybierz opcję **Sieć Web** i wprowadź adres URL przekierowania: `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. Pobierz identyfikator klienta aplikacji i utwórz wpis tajny klienta i pobierz tę wartość.

1. \[administrator\] AAD Utwórz aplikację usługi Azure AD dla interfejsu API Rest w ramach dzierżawy Microsoft 365.

    1. Zaloguj się do [witryny Azure Portal](https://portal.azure.com/) przy użyciu poświadczeń dzierżawy Microsoft 365 i przejdź do strony Rejestracje aplikacji, aby utworzyć nową aplikację.

    1. Wybierz pozycję **Konta tylko w tym katalogu organizacyjnym {(Tylko nazwa-dzierżawy microsoft-365- — pojedyncza dzierżawa)**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. Pobierz identyfikator klienta aplikacji i utwórz wpis tajny klienta i pobierz tę wartość.

1. \[administrator\] AAD Utwórz aplikację usługi Azure AD dla użytkownika rest w ramach dzierżawy Microsoft 365.

    1. Zaloguj się do [witryny Azure Portal](https://portal.azure.com/) przy użyciu poświadczeń dzierżawy Microsoft 365 i przejdź do strony Rejestracje aplikacji, aby utworzyć nową aplikację.

    1. Wybierz pozycję **Konta tylko w tym katalogu organizacyjnym {(Tylko nazwa-dzierżawy microsoft-365- — pojedyncza dzierżawa)**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. Pobierz identyfikator klienta aplikacji i utwórz wpis tajny klienta i pobierz tę wartość.

1. \[Administrator\] usługi ServiceNow Skonfiguruj wychodzącego dostawcę OAuth w usłudze ServiceNow.

    Jeśli zakres nie jest ustawiony na **Wartość globalna**, zrób to, przechodząc do **Ustawienia &gt; Aplikacje dla deweloperów &gt;** i przełączając się na **globalne**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, czat lub wiadomość SMS Opis":::

1. Przejdź do **pozycji System OAuth &gt; Application Registry**.

1. Utwórz nową aplikację przy użyciu **opcji Połączenie do dostawcy OAuth innej firmy** i wprowadź następujące wartości:

    - Identyfikator klienta: jest to identyfikator klienta aplikacji utworzonej w kroku \#1 wymagań wstępnych (token uwierzytelniania usługi Azure AD).

    - Klucz tajny klienta: jest to wartość klucza tajnego klienta aplikacji utworzonej w kroku \#1 wymagań wstępnych (token uwierzytelniania usługi Azure AD).

    - Domyślny typ udzielenia: Poświadczenia klienta

    - Adres URL tokenu: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - Adres URL przekierowania: `https://{service-now-instance-name``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany opis aplikacji":::

1. \[Administrator\] usługi ServiceNow Aby skonfigurować dostawcę OIDC w usłudze ServiceNow, zapoznaj się z [dokumentacją online](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    Jeśli zakres nie jest ustawiony na **Wartość globalna**, przejdź do **Ustawienia &gt; Aplikacje dla deweloperów &gt;** i przejdź do pozycji **Globalne**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, czat lub wiadomość SMS Opis":::

1. Przejdź do **pozycji System OAuth &gt; Application Registry**.

1. Wybierz pozycję **Nowy**, a następnie wybierz pozycję **Utwórz nowy otwarty identyfikator Połączenie Provider**.

1. W **konfiguracji dostawcy OAuth OIDC** wybierz pozycję **Wyszukaj** i utwórz nową konfigurację dostawcy OIDC w obszarze **oidcproviderconfiguration.list\_\_** z następującymi wartościami:

    - Dostawca OIDC: **{TenantName\_} Azure** (przykład: Contoso Azure)

    - Adres URL metadanych OIDC: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appid**

    - UserField: **identyfikator użytkownika**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="Graficzny interfejs użytkownika, tekst, automatycznie wygenerowany opis aplikacji":::

1. Utwórz nową aplikację, wybierając **pozycję Konfiguruj dostawcę OIDC, aby zweryfikować tokeny identyfikatorów** z następującymi wartościami:

    - Nazwa: **{TenantName\_}\_applicationinboundapi\_\_** (przykład: contosoapplicationinboundapi\_\_\_)

    - Identyfikator klienta: identyfikator klienta aplikacji utworzonej w kroku \#3 wymagań wstępnych (token uwierzytelniania usługi Azure AD).

    - Klucz tajny klienta: wpis tajny aplikacji utworzonej w kroku \#3 wymagań wstępnych (token uwierzytelniania usługi Azure AD).

    - Konfiguracja dostawcy OAuth OIDC: dostawca OIDC utworzony w poprzednim kroku

    - Adres URL przekierowania: `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany opis aplikacji":::

1. \[Administrator\] usługi ServiceNow tworzy użytkowników integracji.

    Musisz określić użytkownika integracji. Jeśli nie masz istniejącego użytkownika integracji lub chcesz utworzyć go specjalnie na potrzeby tej integracji, przejdź do **pozycji Użytkownicy organizacji&gt;**, aby utworzyć nowego użytkownika. Wartość **identyfikatora użytkownika** to identyfikator klienta aplikacji utworzony w obszarze [Wymagania wstępne (token uwierzytelniania usługi Azure AD)](#prerequisites-azure-ad-auth-token).

    Jeśli tworzysz nowego użytkownika integracji, sprawdź opcję **Tylko dostęp do usługi sieci Web** . Należy również przyznać temu użytkownikowi rolę **incidentmanager\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany opis aplikacji":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[OPCJONALNIE\] Zezwalaj adresom IP usługi na Microsoft 365 integrację z pomocą techniczną

Jeśli Twoja firma ogranicza dostęp do Internetu za pomocą własnych zasad, włącz dostęp do sieci dla usługi Microsoft 365 integracji pomocy technicznej, zezwalając na poniższe adresy IP dla przychodzącego i wychodzącego dostępu do interfejsu API.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> To polecenie terminalu wyświetla listę wszystkich aktywnych adresów IP usługi na potrzeby integracji Microsoft 365 pomocy technicznej:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Konfigurowanie aplikacji integracji Microsoft 365 pomocy technicznej

Aplikację integracji Microsoft 365 pomocy technicznej można skonfigurować w ramach Microsoft 365 pomocy technicznej.

Te kroki są wymagane do skonfigurowania integracji między wystąpieniem usługi ServiceNow i Microsoft 365 pomocy technicznej.

1. \[Administrator\] usługi ServiceNow Przełącz zakres na **Microsoft 365 integrację pomocy technicznej**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany opis tabeli":::

1. \[Administrator\] usługi ServiceNow przejdź do **Microsoft 365 Konfiguracja pomocy technicznej&gt;**, aby otworzyć przepływ pracy integracji.

    > [!NOTE]
    > Jeśli zostanie wyświetlony komunikat o błędzie "Operacja odczytu względem jednostki "oauthentity\_" z zakresu "xmiomsm365assis\_\_\_" została odrzucona z powodu zasad dostępu między zakresami tabeli, zostało to spowodowane przez zasady dostępu do tabel. Musisz upewnić się, że dla jednostki oauthentity\_ tabeli są sprawdzane **wszystkie zakresy &gt; aplikacji, które można odczytać**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. \[Administrator\] usługi ServiceNow wybierz pozycję **Zgoda** na monit o wyrażenie zgody, aby kontynuować.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. \[Administrator\] usługi ServiceNow Skonfiguruj środowisko i typ konfiguracji.
    Jeśli ta instalacja znajduje się w środowisku testowym, wybierz opcję To jest środowisko testowe. Po skonfigurowaniu będzie można szybko wyłączyć tę opcję, a wszystkie testy zostaną ukończone później.
    Jeśli wystąpienie zezwala na uwierzytelnianie podstawowe dla połączeń przychodzących, wybierz pozycję Tak i zapoznaj się z [procesem konfiguracji uwierzytelniania podstawowego](servicenow-basic-authentication.md). W przeciwnym razie wybierz pozycję **Nie** , a następnie kliknij pozycję **Rozpocznij instalację**. 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. \[Administrator\] usługi ServiceNow wprowadź domenę dzierżawy Microsoft 365.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. \[Administrator\] usługi ServiceNow konfiguruje wychodzącego dostawcę OAuth.
    1. Skonfiguruj wychodzącego dostawcę OAuth.
    1. Po wykonaniu instrukcji w sekcji wymagań wstępnych kliknij pozycję Gotowe. W przeciwnym razie postępuj zgodnie z instrukcjami w kreatorze, aby utworzyć niezbędną rejestrację aplikacji w AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::
    1. Zarejestruj aplikację OAuth usługi ServiceNow.
    1. Po wykonaniu instrukcji w sekcji wymagań wstępnych wybierz nowo utworzoną rejestrację aplikacji OAuth i kliknij przycisk Dalej. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć jednostkę w usłudze ServiceNow, a następnie wybierz nową rejestrację aplikacji.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. \[Administrator\] usługi ServiceNow konfiguruje ustawienia ruchu przychodzącego.
    1. Skonfiguruj aplikację AAD dla ruchu przychodzącego.
    1. Po wykonaniu instrukcji w sekcji wymagań wstępnych kliknij pozycję Gotowe, aby przejść do następnego kroku. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć AAD rejestrację aplikacji na potrzeby łączności przychodzącej.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::
    1. Skonfiguruj zewnętrznego dostawcę Połączenie OpenID usługi ServiceNow (dostawca OIDC).
    1. Po wykonaniu instrukcji w sekcji wymagań wstępnych wybierz nowo utworzoną jednostkę i kliknij pozycję Gotowe. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć jednostkę w usłudze ServiceNow, a następnie wybierz nową rejestrację aplikacji zewnętrznego dostawcy OIDC.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::
    1. Skonfiguruj rejestrację aplikacji AAD dla użytkownika integracji przychodzącej.
    1. Po wykonaniu instrukcji w sekcji wymagań wstępnych kliknij pozycję Gotowe, aby przejść do następnego kroku. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć AAD Rejestracja aplikacji dla przychodzącego użytkownika REST (użytkownika integracji).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::
    1. Skonfiguruj użytkownika integracji.
    1. Po wykonaniu instrukcji w sekcji wymagań wstępnych wybierz nowo utworzoną jednostkę i kliknij przycisk Dalej. W przeciwnym razie postępuj zgodnie z instrukcjami, aby utworzyć użytkownika integracji w usłudze ServiceNow, a następnie wybierz jednostkę.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. \[Microsoft 365 administrator dzierżawy\] Zakończ integrację.

    Sprawdź, czy poniższe informacje są poprawne. NIE wybieraj w tej chwili **przycisku Dalej** .

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

    1. Przejdź do **obszaru Administracja Microsoft 365 Portal &gt; Ustawienia &gt; ustawienia &gt; organizacji Profile organizacji**.

    1. Skonfiguruj ustawienia integracji pomocy technicznej:

    Wybierz kartę **Podstawowe informacje** > **Wewnętrzne narzędzie** >  pomocy **technicznejServiceNow** i wprowadź wartość **Identyfikator aplikacji ruchu wychodzącego** w polu **Identyfikator aplikacji, aby wydać token uwierzytelniania**. Ten identyfikator aplikacji wychodzącej znajduje się w kroku 6 — ukończ integrację, która została utworzona w sekcji [Wymagania wstępne (token uwierzytelniania usługi Azure AD)](#prerequisites-azure-ad-auth-token).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

    1. Na karcie **Repozytoria** wybierz pozycję **Nowe repozytorium** i zaktualizuj go przy użyciu następujących ustawień:

    - Repozytorium: wartość **identyfikatora repozytorium** z sekcji "Krok 6 — zakończenie integracji".

    - Punkt końcowy: wartość **punktu końcowego** z kroku 6 — zakończenie integracji.

    - Typ uwierzytelniania: wybierz **pozycję AAD uwierzytelniania**.

    - Identyfikator klienta: wartość **identyfikatora klienta** z kroku 6 — zakończenie integracji.

    - Klucz tajny klienta: wpis tajny przychodzącego dostawcy OAuth utworzony w kroku \#2 wymagań wstępnych (token uwierzytelniania usługi Azure AD).

    - Nazwa użytkownika rest: wartość **Nazwa użytkownika** z kroku 6 — ukończ integrację, czyli **identyfikator klienta** aplikacji utworzonej w kroku \#3.

    - Hasło użytkownika rest: wpis tajny aplikacji, który został utworzony w kroku \#3 wymagań wstępnych (token uwierzytelniania usługi Azure AD).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="Graficzny interfejs użytkownika, automatycznie wygenerowany opis aplikacji":::

    1. Wstecz do usługi ServiceNow.

    1. Wybierz pozycję **Dalej** , aby ukończyć integrację.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::
    Aplikacja integracji Microsoft 365 pomocy technicznej wykona testy, aby upewnić się, że integracja działa. Jeśli wystąpił problem z konfiguracją, zostanie wyświetlony komunikat o błędzie wyjaśniający, co należy naprawić. W przeciwnym razie aplikacja jest gotowa.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="Automatycznie wygenerowany graficzny interfejs użytkownika, tekst, aplikacja, opis wiadomości e-mail":::

1. \[Administrator\] usługi ServiceNow Włączanie integracji pomocy technicznej firmy Microsoft dla istniejącego użytkownika.

    Microsoft 365 integracja z pomocą techniczną jest włączona dla użytkownika z jedną z następujących ról:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[OPCJONALNIE\] \[Użytkownik z rolą xmiomsm365assis.administrator\_\_\_ link Link\] Microsoft 365 konta administratora.

    Jeśli jakikolwiek użytkownik ma rolę xmiomsm365assis.administrator\_\_\_ i używa różnych kont Microsoft 365 do zarządzania sprawą pomocy technicznej Microsoft 365, musi przejść do Microsoft 365 obsługi &gt; konta linku, aby skonfigurować Microsoft 365 adres e-mail administratora.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Graficzny interfejs użytkownika, tekst, automatycznie wygenerowany opis aplikacji":::
