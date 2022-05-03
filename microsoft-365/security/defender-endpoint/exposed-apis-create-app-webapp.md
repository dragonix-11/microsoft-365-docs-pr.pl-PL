---
title: Tworzenie aplikacji w celu uzyskania dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender bez użytkownika
ms.reviewer: ''
description: Dowiedz się, jak zaprojektować aplikację internetową w celu uzyskania dostępu programowego do Ochrona punktu końcowego w usłudze Microsoft Defender bez użytkownika.
keywords: apis, graph api, supported apis, actor, alerts, device, user, domain, ip, file, advanced hunting, query
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: f8b620d519b0e27fd54313329040096f10c070f9
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172333"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>Tworzenie aplikacji w celu uzyskania dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender bez użytkownika

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/index.yml)

> [!IMPORTANT]
> Zaawansowane możliwości wyszukiwania zagrożeń nie są uwzględniane w usłudze Defender dla firm. Zobacz [Porównanie Microsoft Defender dla Firm z planami Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Na tej stronie opisano sposób tworzenia aplikacji w celu uzyskania dostępu programowego do usługi Defender for Endpoint bez użytkownika. Jeśli potrzebujesz dostępu programowego do usługi Defender for Endpoint w imieniu użytkownika, zobacz [Uzyskiwanie dostępu za pomocą kontekstu użytkownika](exposed-apis-create-app-nativeapp.md). Jeśli nie masz pewności, jakiego dostępu potrzebujesz, zobacz [Wprowadzenie](apis-intro.md).

Ochrona punktu końcowego w usłudze Microsoft Defender uwidacznia wiele swoich danych i akcji za pośrednictwem zestawu programowych interfejsów API. Te interfejsy API pomogą Ci zautomatyzować przepływy robocze i wprowadzać innowacje w oparciu o możliwości usługi Defender for Endpoint. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Ogólnie rzecz biorąc, należy wykonać następujące kroki, aby korzystać z interfejsów API:
- Utwórz aplikację Azure Active Directory (Azure AD).
- Pobierz token dostępu przy użyciu tej aplikacji.
- Użyj tokenu, aby uzyskać dostęp do interfejsu API usługi Defender for Endpoint.

W tym artykule wyjaśniono, jak utworzyć aplikację Azure AD, uzyskać token dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender i zweryfikować token.

## <a name="create-an-app"></a>Tworzenie aplikacji

1. Zaloguj się na [platformie Azure](https://portal.azure.com) przy użyciu użytkownika z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** \> **Rejestracje aplikacji** \> **Nowa rejestracja**. 

    :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Okienko rejestracji aplikacji" lightbox="images/atp-azure-new-app2.png":::

3. W formularzu rejestracji wybierz nazwę aplikacji, a następnie wybierz pozycję **Zarejestruj**.

4. Aby umożliwić aplikacji dostęp do usługi Defender for Endpoint i przypisać jej **uprawnienie "Odczyt wszystkich alertów",** na stronie aplikacji wybierz pozycję **Uprawnienia interfejsu API Dodaj interfejsy** \> API **uprawnień**\>, **które moja organizacja używa** >, wpisz **WindowsDefenderATP**, a następnie wybierz pozycję **WindowsDefenderATP**.

   > [!NOTE]
   > *WindowsDefenderATP* nie jest wyświetlany na oryginalnej liście. Zacznij pisać jego nazwę w polu tekstowym, aby zobaczyć, jak jest wyświetlana.

   :::image type="content" source="images/add-permission.png" alt-text="Okienko uprawnień interfejsu API" lightbox="images/add-permission.png":::

   Wybierz pozycję **Uprawnienia** \> aplikacji **Alert.Read.All**, a następnie wybierz pozycję **Dodaj uprawnienia**.

   :::image type="content" source="images/application-permissions.png" alt-text="Okienko informacji o uprawnieniach aplikacji" lightbox="images/application-permissions.png":::

     Musisz wybrać odpowiednie uprawnienia. "Odczyt wszystkich alertów" jest tylko przykładem. Przykład:

     - Aby [uruchamiać zaawansowane zapytania](run-advanced-query-api.md), wybierz uprawnienie "Uruchom zaawansowane zapytania".
     - Aby [wyizolować urządzenie](isolate-machine.md), wybierz uprawnienie "Izolowanie maszyny".
     - Aby określić, którego uprawnienia potrzebujesz, zapoznaj się z sekcją **Uprawnienia** w interfejsie API, który chcesz wywołać.

5. Wybierz pozycję **Udziel zgody**.

     > [!NOTE]
     > Za każdym razem, gdy dodasz uprawnienie, musisz wybrać pozycję **Udziel zgody** , aby nowe uprawnienie weszło w życie.

    :::image type="content" source="images/grant-consent.png" alt-text="Strona udzielania uprawnień" lightbox="images/grant-consent.png":::

6. Aby dodać wpis tajny do aplikacji, wybierz pozycję **Certyfikaty & wpisów tajnych**, dodaj opis do wpisu tajnego, a następnie wybierz pozycję **Dodaj**.

    > [!NOTE]
    > Po wybraniu pozycji **Dodaj** wybierz pozycję **Skopiuj wygenerowaną wartość wpisu tajnego**. Nie będzie można pobrać tej wartości po opuszczeniu.

      :::image type="content" source="images/webapp-create-key2.png" alt-text="Opcja tworzenia aplikacji" lightbox="images/webapp-create-key2.png":::

7. Zapisz identyfikator aplikacji i identyfikator dzierżawy. Na stronie aplikacji przejdź do pozycji **Przegląd** i skopiuj następujące elementy.

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Utworzone identyfikatory aplikacji i dzierżawy" lightbox="images/app-and-tenant-ids.png":::

8. **Tylko w przypadku partnerów Ochrona punktu końcowego w usłudze Microsoft Defender**. Ustaw aplikację na wielodostępną (dostępną we wszystkich dzierżawach po wyrażeniu zgody). Jest to wymagane w przypadku aplikacji innych firm (na przykład w przypadku utworzenia aplikacji, która ma być **uruchamiana** w dzierżawie wielu klientów). Nie jest to **wymagane** , jeśli utworzysz usługę, którą chcesz uruchomić tylko w dzierżawie (na przykład jeśli utworzysz aplikację dla własnego użycia, która będzie wchodzić w interakcje tylko z własnymi danymi). Aby ustawić aplikację jako wielodostępną:

    - Przejdź do pozycji **Uwierzytelnianie** i dodaj `https://portal.azure.com` jako **identyfikator URI przekierowania**.

    - W dolnej części strony w obszarze **Obsługiwane typy kont** wybierz pozycję **Konta w dowolnej zgody aplikacji katalogu organizacyjnego** dla aplikacji wielodostępnej.

    Aplikacja musi zostać zatwierdzona w każdej dzierżawie, w której ma być używana. Dzieje się tak, ponieważ aplikacja współdziała z usługą Defender for Endpoint w imieniu klienta.

    Użytkownik (lub klient piszący aplikację innej firmy) musi wybrać link zgody i zatwierdzić aplikację. Zgodę należy wyrazić z użytkownikiem, który ma uprawnienia administracyjne w usłudze Active Directory.

    Link zgody jest tworzony w następujący sposób: 

    ```https
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Gdzie 00000000-0000-0000-0000-000000000000 jest zastępowany identyfikatorem aplikacji.


**Ukończono!** Aplikacja została pomyślnie zarejestrowana! Zapoznaj się z poniższymi przykładami dotyczącymi uzyskiwania i walidacji tokenu.

## <a name="get-an-access-token"></a>Uzyskiwanie tokenu dostępu

Aby uzyskać więcej informacji na temat tokenów Azure AD, zobacz [samouczek Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="use-powershell"></a>Korzystanie z programu PowerShell

```powershell
# This script acquires the App Context Token and stores it in the variable $token for later use in the script.
# Paste your Tenant ID, App ID, and App Secret (App key) into the indicated quotes below.

$tenantId = '' ### Paste your tenant ID here
$appId = '' ### Paste your Application ID here
$appSecret = '' ### Paste your Application key here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token
```

### <a name="use-c"></a>Użyj języka C#:

Poniższy kod został przetestowany przy użyciu NuGet Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

1. Utwórz nową aplikację konsolową.
1. Zainstaluj NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. Dodaj następujące elementy:

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Skopiuj i wklej następujący kod w aplikacji (nie zapomnij zaktualizować trzech zmiennych: ```tenantId, appId, appSecret```):

    ```csharp
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 

    const string authority = "https://login.microsoftonline.com";
    const string wdatpResourceId = "https://api.securitycenter.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(appId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```


### <a name="use-python"></a>Korzystanie z języka Python

Zobacz [Pobieranie tokenu przy użyciu języka Python](run-advanced-query-sample-python.md#get-token).

### <a name="use-curl"></a>Korzystanie z narzędzia Curl

> [!NOTE]
> W poniższej procedurze przyjęto założenie, że program Curl for Windows jest już zainstalowany na komputerze.

1. Otwórz wiersz polecenia i ustaw CLIENT_ID na identyfikator aplikacji platformy Azure.
1. Ustaw CLIENT_SECRET na wpis tajny aplikacji platformy Azure.
1. Ustaw TENANT_ID na identyfikator dzierżawy platformy Azure klienta, który chce używać aplikacji do uzyskiwania dostępu do usługi Defender for Endpoint.
1. Uruchom następujące polecenie:

    ```console
    curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
    ```
    
    Odpowiedź otrzymasz w następującym formularzu:
    
    ```console
    {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
    ```
    
## <a name="validate-the-token"></a>Weryfikowanie tokenu

Upewnij się, że masz prawidłowy token:

1. Skopiuj i wklej token uzyskany w poprzednim kroku do [narzędzia JWT](https://jwt.ms) , aby go odkodować.

1. Sprawdź, czy otrzymasz oświadczenie "role" z żądanymi uprawnieniami.

   Na poniższej ilustracji widać dekodowany token uzyskany z aplikacji z uprawnieniami do wszystkich ról Ochrona punktu końcowego w usłudze Microsoft Defender:

   :::image type="content" source="images/webapp-decoded-token.png" alt-text="Część szczegółów tokenu" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Uzyskiwanie dostępu do interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu tokenu

1. Wybierz interfejs API, którego chcesz użyć. Aby uzyskać więcej informacji, zobacz [Supported Defender for Endpoint APIs (Obsługiwana usługa Defender dla interfejsów API punktu końcowego](exposed-apis-list.md)).
1. Ustaw nagłówek autoryzacji w żądaniu http wysyłanym do elementu "Bearer {token}" (Element nośny jest schematem autoryzacji).
1. Czas wygaśnięcia tokenu wynosi jedną godzinę. Możesz wysłać więcej niż jedno żądanie z tym samym tokenem.

Poniżej przedstawiono przykład wysyłania żądania uzyskania listy alertów **przy użyciu języka C#**:

```csharp
var httpClient = new HttpClient();

var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

// Do something useful with the response
```

## <a name="see-also"></a>Zobacz też
- [Obsługiwane interfejsy API usługi ochrony punktu końcowego w usłudze Microsoft Defender](exposed-apis-list.md)
- [Dostęp Ochrona punktu końcowego w usłudze Microsoft Defender w imieniu użytkownika](exposed-apis-create-app-nativeapp.md)
