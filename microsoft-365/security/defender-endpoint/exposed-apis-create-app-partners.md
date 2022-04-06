---
title: Tworzenie aplikacji w celu uzyskania Ochrona punktu końcowego w usłudze Microsoft Defender dostępu bez użytkownika
ms.reviewer: ''
description: Dowiedz się, jak zaprojektować aplikację sieci Web, aby uzyskać dostęp programowy Ochrona punktu końcowego w usłudze Microsoft Defender dostępu bez użytkownika.
keywords: apis, api Graph, obsługiwane api, actor, alerts, device, user, domain, ip, file, advanced hunting, query
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
ms.openlocfilehash: 454d385c66a0019ba6059a2b8038907dd630b443
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469872"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>Dostęp partnera za pośrednictwem Ochrona punktu końcowego w usłudze Microsoft Defender API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Na tej stronie opisano, jak utworzyć aplikację usługi Azure Active Directory (Azure AD), aby uzyskać dostęp programowy do aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender w imieniu klientów.

Ochrona punktu końcowego w usłudze Microsoft Defender udostępnia większość danych i akcji za pośrednictwem zestawu interfejsów API programistycznych. Te interfejsy API pomogą Ci zautomatyzować przepływy robocze i wprowadzać w nich innowacje na podstawie Ochrona punktu końcowego w usłudze Microsoft Defender biznesowych. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji protokołu OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Aby korzystać z interfejsów API, musisz wykonać następujące czynności:

- Utwórz aplikację usługi Azure AD **dla wielu** dzierżaw.
- Uzyskaj autoryzowany(zgodę) przez administratora klienta dla Twojej aplikacji na potrzeby uzyskiwania dostępu do usługi Defender dla zasobów punktu końcowego, których potrzebuje.
- Uzyskaj token dostępu przy użyciu tej aplikacji.
- Token umożliwia uzyskanie dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender API.

Poniższe instrukcje po to, jak utworzyć aplikację usługi Azure AD, uzyskać token dostępu do usługi Ochrona punktu końcowego w usłudze Microsoft Defender i zweryfikować token.

## <a name="create-the-multi-tenant-app"></a>Tworzenie aplikacji wielodostępowej

1. Zaloguj się do dzierżawy [platformy Azure przy](https://portal.azure.com) użyciu użytkownika z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** \> **Rejestracje aplikacji** \> **Rejestracja**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Okienko nawigacji do rejestracji aplikacji" lightbox="images/atp-azure-new-app2.png":::

3. W formularzu rejestracji:

   - Wybierz nazwę aplikacji.

   - Obsługiwane typy kont — konta w dowolnym katalogu organizacyjnym.

   - Przekieruj URI — wpisz: Web, URI: https://portal.azure.com

     :::image type="content" source="images/atp-api-new-app-partner.png" alt-text="Strona Microsoft Azure rejestracji aplikacji partnera" lightbox="images/atp-api-new-app-partner.png":::

4. Zezwalaj aplikacji na Ochrona punktu końcowego w usłudze Microsoft Defender i przypisywanie jej z minimalnym zestawem uprawnień wymaganych do ukończenia integracji.

   - Na stronie aplikacji wybierz pozycję Uprawnienia **interfejsów API** Dodaj interfejsy **API**  \> \> uprawnień używane przez moją organizację, > **wpisz WindowsDefenderATP** i wybierz pozycję na **WindowsDefenderATP**.

   - **Uwaga**: *WindowsDefenderATP* nie jest wyświetlany na oryginalnej liście. Zacznij pisać jego nazwę w polu tekstowym, aby ją wyświetlić.

     :::image type="content" source="images/add-permission.png" alt-text="Opcja Dodaj uprawnienie" lightbox="images/add-permission.png":::

### <a name="request-api-permissions"></a>Żądanie uprawnień interfejsu API

Aby ustalić, jakich uprawnień potrzebujesz, przejrzyj **sekcję Uprawnienia** w interfejsie API, który chcesz wywołać. Na przykład:

- Aby [uruchomić zapytania zaawansowane](run-advanced-query-api.md), wybierz uprawnienie Uruchamianie zapytań zaawansowanych
- Aby [odizolować urządzenie](isolate-machine.md), wybierz uprawnienie "Wyizoluj komputer"

W poniższym przykładzie użyjemy uprawnień **"Czytaj wszystkie alerty** ":

1. Wybierz **pozycję Alert uprawnień** **aplikacji.Odczyt**\>.> wybierz pozycję Dodaj **uprawnienia**

   :::image type="content" source="images/application-permissions.png" alt-text="Opcja umożliwiająca dodanie uprawnień" lightbox="images/application-permissions.png":::

2. Wybierz pozycję **Ut przyznaj zgodę**

   - **Uwaga**: za każdym razem, gdy dodajesz uprawnienie, musisz zaznaczyć **pozycję U** udzielić zgody, aby nowe uprawnienie było skuteczne.

   :::image type="content" source="images/grant-consent.png" alt-text="Opcja zezwalaca na wyrażenie zgody" lightbox="images/grant-consent.png":::

3. Dodaj do aplikacji klucz tajny.

   - Wybierz **pozycję Certyfikaty & sekrety**, dodaj opis do tajemnicy, a następnie wybierz pozycję **Dodaj**.

    **Ważne**: po kliknięciu przycisku Dodaj **skopiuj wygenerowaną wartość tajnych**. Po opuszczeniu programu nie będzie można ich odzyskać!

     :::image type="content" source="images/webapp-create-key2.png" alt-text="Klucz aplikacji Utwórz" lightbox="images/webapp-create-key2.png":::

4. Zapisz swój identyfikator aplikacji:

   - Na stronie aplikacji przejdź do strony **Omówienie i** skopiuj następujące informacje:

     :::image type="content" source="images/app-id.png" alt-text="Identyfikator aplikacji do tworzenia" lightbox="images/app-id.png":::

5. Dodaj aplikację do dzierżawy klienta.

   Twój wniosek powinien zostać zatwierdzony w każdej dzierżawie klienta, której zamierzasz używać. Jest to spowodowane tym, że Twoja aplikacja Ochrona punktu końcowego w usłudze Microsoft Defender aplikacją w imieniu klienta.

   Użytkownik z **administratorem globalnym** w dzierżawie Twojego klienta musi wybrać link zgody i zatwierdzić Twoją aplikację.

   Link Zgody jest formularzem:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Gdzie 00000000-0000-0000-0000-000000000000 aplikacji powinien zostać zastąpiony Identyfikator aplikacji

   Po kliknięciu linku zgody zaloguj się u administratora globalnego dzierżawy klienta i zgotuj aplikację.

   :::image type="content" source="images/app-consent-partner.png" alt-text="Przycisk Zaakceptuj" lightbox="images/app-consent-partner.png":::

   Ponadto podczas uzyskiwania tokenu musisz poprosić klienta o identyfikator dzierżawy i zapisać go do użycia w przyszłości.

6. **Ukończono!** Aplikacja została pomyślnie zarejestrowana! Zobacz poniższe przykłady dotyczące pozyskiwania i sprawdzania poprawności tokenu.

## <a name="get-an-access-token-example"></a>Przykład tokenu dostępu

**Uwaga:** Aby uzyskać token dostępu w imieniu klienta, użyj identyfikatora dzierżawy klienta w następujących zakupach tokenów.

Aby uzyskać więcej informacji na AAD tokenu, zobacz AAD [samouczka](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

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

### <a name="using-c"></a>Używanie języka C #

> Poniższy kod został przetestowany przez firmę Nuget Microsoft.IdentityModel.Clients.ActiveDirectory

- Tworzenie nowej aplikacji konsoli
- Instalowanie NuGet [witryny Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)
- Dodaj poniższe przy użyciu

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

### <a name="using-python"></a>Używanie języka Python

Zobacz Uzyskiwanie [tokenu za pomocą języka Python](run-advanced-query-sample-python.md#get-token)

### <a name="using-curl"></a>Używanie zwijania

> [!NOTE]
> Poniżej przedstawiono procedurę curl dla Windows jest już zainstalowana na komputerze

- Otwieranie okna polecenia
- Konfigurowanie CLIENT_ID do identyfikatora aplikacji platformy Azure
- Konfigurowanie CLIENT_SECRET azure jako tajnej
- Ustaw TENANT_ID na identyfikator dzierżawy platformy Azure klienta, który chce używać Twojej aplikacji do uzyskiwania dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender aplikacji
- Uruchom poniższe polecenie:

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Otrzymasz odpowiedź na formularz:

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Sprawdź poprawność tokenu

Sprawdź poprawność, aby upewnić się, że token jest poprawny:

- Skopiuj/wklej do [pliku JWT](https://jwt.ms) token, który otrzymasz w poprzednim kroku w celu jego odkodowania
- Sprawdź, czy masz "role" z wymaganymi uprawnieniami
- Na poniższym zrzucie ekranu widać dekodowany token pozyskany z aplikacji z wieloma uprawnieniami do Ochrona punktu końcowego w usłudze Microsoft Defender:
- Żądanie "uporządkowane" to identyfikator dzierżawy, do której należy token.

:::image type="content" source="images/webapp-decoded-token.png" alt-text="Strona sprawdzania poprawności tokenu" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Uzyskiwanie dostępu do interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender tokenu

- Wybierz odpowiedni interfejs API, aby uzyskać więcej informacji, zobacz Obsługiwane Ochrona punktu końcowego w usłudze Microsoft Defender [API](exposed-apis-list.md)
- Ustaw nagłówek Autoryzacja w żądaniu Http, które wysyłasz na adres "Bearer {token}" (Bearer is the Authorization scheme)
- Czas wygaśnięcia tokenu to 1 godzina (możesz wysłać więcej niż jedno żądanie z tym samym tokenem)

- Przykład wysyłania żądania w celu uzyskania listy alertów przy **użyciu języka C#**

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Zobacz też

- [Obsługiwane Ochrona punktu końcowego w usłudze Microsoft Defender API](exposed-apis-list.md)
- [Uzyskiwanie Ochrona punktu końcowego w usłudze Microsoft Defender w imieniu użytkownika](exposed-apis-create-app-nativeapp.md)
