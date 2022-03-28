---
title: Dostęp partnera za pośrednictwem Microsoft 365 Defender API
description: Dowiedz się, jak utworzyć aplikację w celu uzyskania dostępu programowego Microsoft 365 Defender w imieniu użytkowników.
keywords: partner, access, api, wiele dzierżaw, zgoda, token dostępu, aplikacja
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: f0ed889cbc0a07a1f64bc0f717fe07fe877a98b9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754691"
---
# <a name="create-an-app-with-partner-access-to-microsoft-365-defender-apis"></a>Tworzenie aplikacji z dostępem partnera do Microsoft 365 Defender API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Na tej stronie opisano, jak utworzyć aplikację Azure Active Directory programowy dostęp do aplikacji Microsoft 365 Defender w imieniu użytkowników w wielu dzierżawach. Aplikacje wielodostępne przydają się do obsługi dużych grup użytkowników.

Jeśli potrzebujesz dostępu programowego do Microsoft 365 Defender w imieniu jednego użytkownika, zobacz Tworzenie aplikacji w celu uzyskiwania dostępu do interfejsów [API usługi Microsoft 365 Defender](api-create-app-user-context.md) w imieniu użytkownika. Jeśli potrzebujesz dostępu bez jawnego zdefiniowanego przez użytkownika (na przykład podczas pisania aplikacji w tle lub daemona), zobacz Tworzenie aplikacji w celu uzyskania dostępu do usługi [Microsoft 365 Defender bez użytkownika](api-create-app-web.md). Jeśli nie masz pewności, jakiego rodzaju dostępu potrzebujesz, zobacz [Wprowadzenie](api-access.md).

Microsoft 365 Defender udostępnia większość danych i akcji za pośrednictwem zestawu interfejsów API programistycznych. Te interfejsy API ułatwiają automatyzowanie przepływów pracy i korzystanie Microsoft 365 Defender możliwości firmy. Ten dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji protokołu OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Aby używać tych interfejsów API, należy wykonać następujące czynności:

- Utwórz aplikację usługi Azure Active Directory (Azure AD).
- Uzyskaj token dostępu przy użyciu tej aplikacji.
- Token umożliwia uzyskanie dostępu do Microsoft 365 Defender API.

Ponieważ ta aplikacja jest wielodostępna, potrzebna będzie również zgoda [](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) administratora z każdej dzierżawy w imieniu jej użytkowników.

W tym artykule wyjaśniono, jak to zrobić:

- Tworzenie aplikacji usługi Azure AD **z wieloma** dzierżawami
- Uzyskaj autoryzowaną zgodę administratora Twojej aplikacji na uzyskiwanie dostępu do zasobów, Microsoft 365 Defender do zasobów, których potrzebuje.
- Uzyskiwanie tokenu dostępu do Microsoft 365 Defender
- Sprawdź poprawność tokenu

Microsoft 365 Defender udostępnia większość danych i akcji za pośrednictwem zestawu interfejsów API programistycznych. Te interfejsy API pomogą Ci zautomatyzować przepływy robocze i wprowadzać innowacje w oparciu Microsoft 365 Defender możliwości. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji protokołu OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Aby korzystać z interfejsów API, musisz wykonać następujące czynności:

- Utwórz aplikację usługi Azure AD **dla wielu** dzierżaw.
- Uzyskaj autoryzowany (zgoda) przez administratora użytkownika dla Twojej aplikacji dostęp do Microsoft 365 Defender zasobów, których potrzebuje.
- Uzyskaj token dostępu przy użyciu tej aplikacji.
- Token umożliwia uzyskanie dostępu do Microsoft 365 Defender API.

Poniższe instrukcje z instrukcjami tworzenia wielodostępnych aplikacji Azure AD, uzyskiwania tokenu dostępu Microsoft 365 Defender weryfikacji tokenu.

## <a name="create-the-multi-tenant-app"></a>Tworzenie aplikacji wielodostępowej

1. Zaloguj się do [platformy Azure](https://portal.azure.com) jako użytkownik z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** >  **Rejestracja aplikacjiAppNew** >  **registration**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Sekcja rejestracji aplikacji w portalu Microsoft 365 Defender aplikacji" lightbox="../../media/atp-azure-new-app2.png":::

3. W formularzu rejestracji:

   - Wybierz nazwę aplikacji.
   - Na **stronie Obsługiwane typy kont** wybierz **pozycję Konta w dowolnym katalogu organizacyjnym (dowolny katalog usługi Azure AD) — usługa Multitenant**.
   - Wypełnij sekcję **Redirect URI (Przekieruj URI** ). Wybierz pozycję **Wpisz nazwę sieci Web** i nadaj adresowi URI przekierowania jako **https://portal.azure.com**.

   Po wypełnieniu formularza wybierz pozycję **Zarejestruj**.

   :::image type="content" source="../..//media/atp-api-new-app-partner.png" alt-text="Sekcje rejestracji aplikacji w portalu Microsoft 365 Defender aplikacji" lightbox="../..//media/atp-api-new-app-partner.png":::

4. Na stronie aplikacji wybierz pozycję Uprawnienia **interfejsu APIUdzyskaj** >  >  **uprawnieniaAPImki** używane przez moją organizację >, wpisz **Microsoft Threat Protection** i wybierz pozycję **Microsoft Threat Protection**. Aplikacja może teraz uzyskać dostęp do Microsoft 365 Defender.

   > [!TIP]
   > *Ochrona przed zagrożeniami firmy Microsoft* to wcześniejsza Microsoft 365 Defender i nie będzie wyświetlana na oryginalnej liście. Aby tekst był wyświetlany, musisz rozpocząć pisanie jego nazwy w polu tekstowym.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Sekcja Użycie interfejsów API w portalu Microsoft 365 Defender interfejsów API" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. Wybierz **pozycję Uprawnienia aplikacji**. Wybierz odpowiednie uprawnienia dla scenariusza (na przykład **Zdarzenie.Odczyt.Wszystko**), a następnie wybierz **pozycję Dodaj uprawnienia**.

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Okienko uprawnień aplikacji w portalu Microsoft 365 Defender aplikacji" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > Musisz wybrać odpowiednie uprawnienia dla swojego scenariusza. *Czytanie wszystkich zdarzeń to* tylko przykład. Aby ustalić, jakich uprawnień potrzebujesz, zapoznaj się z sekcją **Uprawnienia** w interfejsie API, który chcesz wywołać.
    >
    > Aby na przykład [uruchamiać zapytania zaawansowane](api-advanced-hunting.md), wybierz uprawnienie Uruchamianie zapytań zaawansowanych. aby [odizolować urządzenie](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), wybierz uprawnienie "Wyizoluj komputer".

6. Wybierz pozycję **Utłań zgodę administratora**. Za każdym razem, gdy dodajesz uprawnienie, musisz zaznaczyć pozycję Udawaj **administratorów** , aby je obowiązywało.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Sekcja z udzieleniem zgody administratora w portalu Microsoft 365 Defender sieci Microsoft 365 Defender sieci" lightbox="../../media/grant-consent.PNG":::

7. Aby dodać do aplikacji klucz tajny, wybierz pozycję Certyfikaty **& sekretów**, dodaj opis do tajemnicy, a następnie wybierz pozycję **Dodaj**.

    > [!TIP]
    > Po wybraniu **przycisku Dodaj** wybierz **pozycję kopiuj wygenerowaną wartość tajnych**. Po opuszczeniu nie będzie można pobrać wartości tajnej.

      :::image type="content" source="../../media/webapp-create-key2.png" alt-text="Sekcja tajnych dodatku w Microsoft 365 Defender portalu" lightbox="../../media/webapp-create-key2.png":::

8. Zanotuj swój identyfikator aplikacji i identyfikator dzierżawy w bezpiecznym miejscu. Są one wymienione w obszarze **Omówienie** na stronie aplikacji.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Okienko Przegląd w portalu Microsoft 365 Defender wiadomości" lightbox="../../media/app-and-tenant-ids.png":::

9. Dodaj aplikację do dzierżawy użytkownika.

   Ponieważ aplikacja wchodzi w interakcję Microsoft 365 Defender w imieniu użytkowników, musi zostać zatwierdzona dla każdej dzierżawy, w której zamierzasz jej używać.

   Administrator **globalny z** dzierżawy Twojego użytkownika musi wyświetlić link zgody i zatwierdzić Twoją aplikację.

   Link Zgody jest formularzem:

   ```HTTP
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Cyfry powinny `00000000-0000-0000-0000-000000000000` zostać zastąpione Identyfikatorem aplikacji.

   Po kliknięciu linku zgody zaloguj się u administratora globalnego dzierżawy użytkownika i zgotuj aplikację.

   :::image type="content" source="../../media/app-consent-partner.png" alt-text="Strona aplikacji zgody w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/app-consent-partner.png":::

   Musisz również poprosić użytkownika o identyfikator dzierżawy. Identyfikator dzierżawy jest jednym z identyfikatorów używanych do uzyskiwania tokenów dostępu.

- **Ukończono!** Aplikacja została pomyślnie zarejestrowana!
- Zobacz poniższe przykłady dotyczące pozyskiwania i sprawdzania poprawności tokenu.

## <a name="get-an-access-token"></a>Uzyskiwanie tokenu dostępu

Aby uzyskać więcej informacji na temat tokenów usługi Azure AD, zobacz [samouczek dotyczący usługi Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Chociaż przykłady w tej sekcji zachęcają do wklejania tajnych wartości do celów testowych,  nie należy nigdy ująć sekretów firmy w aplikacje działające w środowisku produkcyjnym. Inne firmy mogą używać Twojej tajemnicy do uzyskiwania dostępu do zasobów. Możesz zabezpieczyć tajemnice aplikacji przy użyciu magazynu [kluczy platformy Azure](/azure/key-vault/general/about-keys-secrets-certificates). Aby poznać praktyczne przykłady ochrony aplikacji, zobacz Zarządzanie sekretami aplikacji serwera za pomocą [magazynu kluczy platformy Azure](/learn/modules/manage-secrets-with-azure-key-vault/).

> [!TIP]
> W poniższych przykładach użyj identyfikatora dzierżawy użytkownika, aby sprawdzić, czy skrypt działa.

### <a name="get-an-access-token-using-powershell"></a>Uzyskiwanie tokenu dostępu przy użyciu programu PowerShell

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place!

$resourceAppIdUri = 'https://api.security.microsoft.com'
$oAuthUri = "https://login.windows.net/$tenantId/oauth2/token"

$authBody = [Ordered] @{
    resource = $resourceAppIdUri
    client_id = $clientId
    client_secret = $appSecret
    grant_type = 'client_credentials'
}

$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token

Out-File -FilePath "./Latest-token.txt" -InputObject $token

return $token
```

### <a name="get-an-access-token-using-c"></a>Uzyskiwanie tokenu dostępu przy użyciu C\#

> [!NOTE]
> Poniższy kod został przetestowany w programie Nuget Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

1. Utwórz nową aplikację konsoli.
1. Zainstaluj NuGet [witryny Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. Dodaj następujący wiersz:

    ```C#
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Skopiuj i wklej następujący kod do aplikacji (nie zapomnij zaktualizować trzech zmiennych: `tenantId`, `clientId`, `appSecret`):

    ```C#
    string tenantId = ""; // Paste your directory (tenant) ID here
    string clientId = ""; // Paste your application (client) ID here
    string appSecret = ""; // Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

    const string authority = "https://login.windows.net";
    const string wdatpResourceId = "https://api.security.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(clientId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```

### <a name="get-an-access-token-using-python"></a>Uzyskiwanie tokenu dostępu w języku Python

```Python
import json
import urllib.request
import urllib.parse

tenantId = '' # Paste your directory (tenant) ID here
clientId = '' # Paste your application (client) ID here
appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

url = "https://login.windows.net/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.security.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : clientId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

### <a name="get-an-access-token-using-curl"></a>Uzyskiwanie tokenu dostępu przy użyciu zwijania

> [!NOTE]
> Program Curl jest preinstalowany Windows 10, wersjach 1803 i nowszych. W przypadku innych wersji Windows pobierz i zainstaluj narzędzie bezpośrednio z oficjalnej [witryny internetowej zwijania](https://curl.haxx.se/windows/).

1. Otwórz wiersz polecenia i ustaw dla CLIENT_ID azure identyfikator aplikacji.
1. Ustaw CLIENT_SECRET klucz tajny aplikacji platformy Azure.
1. Ustaw TENANT_ID Azure identyfikator dzierżawy użytkownika, który chce użyć aplikacji w celu uzyskania dostępu do Microsoft 365 Defender.
1. Uruchom następujące polecenie:

```bash
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Pomyślna odpowiedź będzie wyglądać tak:

```bash
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Sprawdź poprawność tokenu

1. Skopiuj i wklej token do witryny [internetowej JSON tokenu sprawdzania prawidłowego tokenu sieci Web (JWT),](https://jwt.ms) aby go odkodować.
1. Upewnij się, że *role w* tokenie dekodowany zawierają odpowiednie uprawnienia.

Na poniższej ilustracji widać dekodowany token nabyte z aplikacji, ```Incidents.Read.All```za pomocą , ```Incidents.ReadWrite.All```i ```AdvancedHunting.Read.All``` uprawnień:

:::image type="content" source="../../media/webapp-decoded-token.png" alt-text="Okienko Token dekodowany w Microsoft 365 Defender sieci Microsoft 365 Defender" lightbox="../../media/webapp-decoded-token.png":::


## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Używanie tokenu w celu uzyskania dostępu do Microsoft 365 Defender API

1. Wybierz odpowiedni interfejs API (zdarzenia lub zaawansowane szukanie). Aby uzyskać więcej informacji, zobacz [Obsługiwane Microsoft 365 Defender API](api-supported.md).
2. W żądaniu http, które chcesz wysłać, `"Bearer" <token>`ustaw nagłówek autoryzacji *na wartość ,* Użytkownik jest schematem autoryzacji, a *token jest tokenem* weryfikowanego przez Ciebie.
3. Token wygaśnie w ciągu godziny. W tym czasie możesz wysłać więcej niż jedno żądanie przy użyciu tego samego tokenu.

W poniższym przykładzie pokazano, jak wysłać żądanie w celu uzyskania listy zdarzeń przy **użyciu języka C#**.

```C#
   var httpClient = new HttpClient();
   var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

   request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

   var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>Artykuły pokrewne

- [Microsoft 365 Defender interfejsów API — omówienie](api-overview.md)
- [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md)
- [Tworzenie aplikacji "Witaj świecie"](api-hello-world.md)
- [Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender dostępu bez użytkownika](api-create-app-web.md)
- [Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender interfejsów API w imieniu użytkownika](api-create-app-user-context.md)
- [Informacje o limitach i licencjonowaniu interfejsu API](api-terms.md)
- [Opis kodów błędów](api-error-codes.md)
- [Zarządzanie sekretami aplikacji serwera za pomocą magazynu kluczy platformy Azure](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Autoryzacja protokołu OAuth 2.0 do logowania użytkownika i dostępu do interfejsu API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
