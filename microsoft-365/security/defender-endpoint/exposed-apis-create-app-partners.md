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
ms.openlocfilehash: fde2cc894fb989628f9e2e0d9d7297bdb3c9e9da
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172398"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>Dostęp partnerów za pośrednictwem interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/index.yml)

> [!IMPORTANT]
> Zaawansowane możliwości wyszukiwania zagrożeń nie są uwzględniane w usłudze Defender dla firm. Zobacz [Porównanie Microsoft Defender dla Firm z planami Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Na tej stronie opisano sposób tworzenia aplikacji Azure Active Directory (Azure AD) w celu uzyskania dostępu programowego do Ochrona punktu końcowego w usłudze Microsoft Defender w imieniu klientów.

Ochrona punktu końcowego w usłudze Microsoft Defender uwidacznia wiele swoich danych i akcji za pośrednictwem zestawu programowych interfejsów API. Te interfejsy API pomogą Ci zautomatyzować przepływy robocze i wprowadzać innowacje w oparciu o Ochrona punktu końcowego w usłudze Microsoft Defender możliwości. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Ogólnie rzecz biorąc, należy wykonać następujące kroki, aby korzystać z interfejsów API:

- Utwórz aplikację Azure AD z **wieloma dzierżawami**.
- Uzyskaj autoryzację (zgodę) administratora klienta dla aplikacji, aby uzyskać dostęp do potrzebnych zasobów usługi Defender for Endpoint.
- Pobierz token dostępu przy użyciu tej aplikacji.
- Użyj tokenu, aby uzyskać dostęp do interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender.

Poniższe kroki przeprowadzą Cię przez proces tworzenia aplikacji Azure AD, uzyskiwania tokenu dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender i weryfikowania tokenu.

## <a name="create-the-multi-tenant-app"></a>Tworzenie aplikacji wielodostępnej

1. Zaloguj się do [dzierżawy platformy Azure](https://portal.azure.com) przy użyciu użytkownika z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** \> **Rejestracje aplikacji** \> **Nowa rejestracja**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Okienko nawigacji do rejestracji aplikacji" lightbox="images/atp-azure-new-app2.png":::

3. W formularzu rejestracji:

   - Wybierz nazwę aplikacji.

   - Obsługiwane typy kont — konta w dowolnym katalogu organizacyjnym.

   - Identyfikator URI przekierowania — typ: Sieć Web, identyfikator URI: https://portal.azure.com

     :::image type="content" source="images/atp-api-new-app-partner.png" alt-text="Strona rejestracji aplikacji partnera Microsoft Azure" lightbox="images/atp-api-new-app-partner.png":::

4. Zezwalaj aplikacji na dostęp do Ochrona punktu końcowego w usłudze Microsoft Defender i przypisz ją z minimalnym zestawem uprawnień wymaganych do ukończenia integracji.

   - Na stronie aplikacji wybierz pozycję **Uprawnienia interfejsu API Dodaj interfejsy** \> API **uprawnień**\>, **których moja organizacja używa** > wpisz **WindowsDefenderATP** i wybierz pozycję **WindowsDefenderATP**.

   - **Uwaga**: *system WindowsDefenderATP* nie jest wyświetlany na oryginalnej liście. Zacznij pisać jego nazwę w polu tekstowym, aby zobaczyć, jak jest wyświetlana.

     :::image type="content" source="images/add-permission.png" alt-text="Opcja Dodaj uprawnienie" lightbox="images/add-permission.png":::

### <a name="request-api-permissions"></a>Żądanie uprawnień interfejsu API

Aby określić, którego uprawnienia potrzebujesz, zapoznaj się z sekcją **Uprawnienia** w interfejsie API, który chcesz wywołać. Na przykład:

- Aby [uruchamiać zaawansowane zapytania](run-advanced-query-api.md), wybierz uprawnienie "Uruchamianie zapytań zaawansowanych"
- Aby [wyizolować urządzenie](isolate-machine.md), wybierz uprawnienie "Izolowanie maszyny"

W poniższym przykładzie użyjemy uprawnienia **"Odczyt wszystkich alertów"** :

1. Wybierz pozycję **Uprawnienia** \> aplikacji **Alert.Read.All** > wybierz pozycję **Dodaj uprawnienia**

   :::image type="content" source="images/application-permissions.png" alt-text="Opcja umożliwiająca dodanie uprawnienia" lightbox="images/application-permissions.png":::

2. Wybierz pozycję **Udziel zgody**

   - **Uwaga**: za każdym razem, gdy dodasz uprawnienie, musisz wybrać pozycję **Udziel zgody** , aby nowe uprawnienie weszło w życie.

   :::image type="content" source="images/grant-consent.png" alt-text="Opcja umożliwiająca udzielenie zgody" lightbox="images/grant-consent.png":::

3. Dodaj wpis tajny do aplikacji.

   - Wybierz pozycję **Certyfikaty & wpisy tajne**, dodaj opis do wpisu tajnego i wybierz pozycję **Dodaj**.

    **Ważne**: po **kliknięciu przycisku Dodaj skopiuj wygenerowaną wartość wpisu tajnego**. Nie będzie można pobrać po opuszczeniu!

     :::image type="content" source="images/webapp-create-key2.png" alt-text="Klucz tworzenia aplikacji" lightbox="images/webapp-create-key2.png":::

4. Zapisz identyfikator aplikacji:

   - Na stronie aplikacji przejdź do pozycji **Przegląd** i skopiuj następujące informacje:

     :::image type="content" source="images/app-id.png" alt-text="Identyfikator tworzenia aplikacji" lightbox="images/app-id.png":::

5. Dodaj aplikację do dzierżawy klienta.

   Aplikacja musi zostać zatwierdzona w każdej dzierżawie klienta, w której zamierzasz jej używać. Dzieje się tak, ponieważ aplikacja współdziała z aplikacją Ochrona punktu końcowego w usłudze Microsoft Defender w imieniu klienta.

   Użytkownik z **administratorem globalnym** z dzierżawy klienta musi wybrać link zgody i zatwierdzić aplikację.

   Link zgody ma następujący formularz:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Gdzie 00000000-0000-0000-0000-000000000000 należy zastąpić identyfikatorem aplikacji

   Po kliknięciu linku zgody zaloguj się za pomocą administratora globalnego dzierżawy klienta i wyrazić zgodę na aplikację.

   :::image type="content" source="images/app-consent-partner.png" alt-text="Przycisk Akceptuj" lightbox="images/app-consent-partner.png":::

   Ponadto należy poprosić klienta o identyfikator dzierżawy i zapisać go do użycia w przyszłości podczas uzyskiwania tokenu.

6. **Ukończono!** Aplikacja została pomyślnie zarejestrowana! Zapoznaj się z poniższymi przykładami dotyczącymi uzyskiwania i walidacji tokenu.

## <a name="get-an-access-token-example"></a>Przykład uzyskiwania tokenu dostępu

**Uwaga:** Aby uzyskać token dostępu w imieniu klienta, użyj identyfikatora dzierżawy klienta w następujących przejęciach tokenu.

Aby uzyskać więcej informacji na temat tokenu AAD, zobacz [samouczek AAD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

### <a name="using-powershell"></a>Korzystanie z programu PowerShell

```powershell
# That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
# Paste below your Tenant ID, App ID and App Secret (App key).

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
Out-File -FilePath "./Latest-token.txt" -InputObject $token
return $token
```

### <a name="using-c"></a>Korzystanie z języka C #

> Poniższy kod został przetestowany za pomocą narzędzia Nuget Microsoft.IdentityModel.Clients.ActiveDirectory

- Tworzenie nowej aplikacji konsolowej
- Instalowanie NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)
- Dodaj poniższe elementy przy użyciu polecenia

    ```console
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

- Skopiuj/wklej poniższy kod w aplikacji (nie zapomnij zaktualizować trzech zmiennych: `tenantId`, `appId`i `appSecret`)

    ```console
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

### <a name="using-python"></a>Korzystanie z języka Python

Zapoznaj się [z tematem Pobieranie tokenu przy użyciu języka Python](run-advanced-query-sample-python.md#get-token)

### <a name="using-curl"></a>Korzystanie z narzędzia Curl

> [!NOTE]
> Poniższa procedura ma curl dla Windows jest już zainstalowany na komputerze

- Otwieranie okna polecenia
- Ustaw CLIENT_ID na identyfikator aplikacji platformy Azure
- Ustawianie CLIENT_SECRET na wpis tajny aplikacji platformy Azure
- Ustaw TENANT_ID na identyfikator dzierżawy platformy Azure klienta, który chce używać aplikacji do uzyskiwania dostępu do aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender
- Uruchom poniższe polecenie:

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Otrzymasz odpowiedź formularza:

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Weryfikowanie tokenu

Sprawdzanie kondycji, aby upewnić się, że masz prawidłowy token:

- Skopiuj/wklej do [narzędzia JWT](https://jwt.ms) token pobrany w poprzednim kroku w celu jego dekodowania
- Sprawdź, czy otrzymasz oświadczenie "role" z żądanymi uprawnieniami
- Na poniższym zrzucie ekranu widać dekodowany token uzyskany z aplikacji z wieloma uprawnieniami do Ochrona punktu końcowego w usłudze Microsoft Defender:
- Oświadczenie "tid" jest identyfikatorem dzierżawy, do którego należy token.

:::image type="content" source="images/webapp-decoded-token.png" alt-text="Strona weryfikacji tokenu" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Uzyskiwanie dostępu do interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu tokenu

- Aby uzyskać więcej informacji, wybierz interfejs API, którego chcesz użyć, zobacz [Obsługiwane interfejsy API Ochrona punktu końcowego w usłudze Microsoft Defender](exposed-apis-list.md)
- Ustaw nagłówek autoryzacji w żądaniu Http wysyłanym do elementu "Bearer {token}" (Element nośny jest schematem autoryzacji)
- Czas wygaśnięcia tokenu wynosi 1 godzinę (możesz wysłać więcej niż jedno żądanie z tym samym tokenem)

- Przykład wysyłania żądania uzyskania listy alertów **przy użyciu języka C#**

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
