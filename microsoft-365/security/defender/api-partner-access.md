---
title: Dostęp partnerów za pośrednictwem interfejsów API Microsoft 365 Defender
description: Dowiedz się, jak utworzyć aplikację w celu uzyskania dostępu programowego do Microsoft 365 Defender w imieniu użytkowników.
keywords: partner, dostęp, interfejs API, wiele dzierżaw, zgoda, token dostępu, aplikacja
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
ms.openlocfilehash: 612cbb4005285f46594bc900cbbc14497b72ffec
ms.sourcegitcommit: 265a4fb38258e9428a1ecdd162dbf9afe93eb11b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2022
ms.locfileid: "65268832"
---
# <a name="create-an-app-with-partner-access-to-microsoft-365-defender-apis"></a>Tworzenie aplikacji z dostępem partnera do interfejsów API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Na tej stronie opisano sposób tworzenia aplikacji Azure Active Directory, która ma programowy dostęp do Microsoft 365 Defender w imieniu użytkowników w wielu dzierżawach. Aplikacje wielodostępne są przydatne do obsługi dużych grup użytkowników.

Jeśli potrzebujesz dostępu programowego do Microsoft 365 Defender w imieniu jednego użytkownika, zobacz [Tworzenie aplikacji w celu uzyskania dostępu do interfejsów API Microsoft 365 Defender w imieniu użytkownika](api-create-app-user-context.md). Jeśli potrzebujesz dostępu bez jawnie zdefiniowanego użytkownika (na przykład w przypadku pisania aplikacji lub demona w tle), zobacz [Tworzenie aplikacji w celu uzyskania dostępu do Microsoft 365 Defender bez użytkownika](api-create-app-web.md). Jeśli nie masz pewności, jakiego rodzaju dostępu potrzebujesz, zobacz [Wprowadzenie](api-access.md).

Microsoft 365 Defender uwidacznia wiele swoich danych i akcji za pośrednictwem zestawu programowych interfejsów API. Te interfejsy API ułatwiają automatyzowanie przepływów pracy i korzystanie z możliwości Microsoft 365 Defender. Ten dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Ogólnie rzecz biorąc, należy wykonać następujące kroki, aby użyć tych interfejsów API:

- Utwórz aplikację Azure Active Directory (Azure AD).
- Pobierz token dostępu przy użyciu tej aplikacji.
- Użyj tokenu, aby uzyskać dostęp do interfejsu API Microsoft 365 Defender.

Ponieważ ta aplikacja jest wielodostępna, musisz również wyrazić [zgodę administratora od każdej dzierżawy](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) w imieniu jej użytkowników.

W tym artykule wyjaśniono, jak:

- Tworzenie aplikacji Azure AD **wielodostępnej**
- Uzyskaj autoryzowaną zgodę administratora użytkownika dla aplikacji, aby uzyskać dostęp do Microsoft 365 Defender potrzebnych zasobów.
- Uzyskiwanie tokenu dostępu do Microsoft 365 Defender
- Weryfikowanie tokenu

Microsoft 365 Defender uwidacznia wiele swoich danych i akcji za pośrednictwem zestawu programowych interfejsów API. Te interfejsy API pomogą Ci zautomatyzować przepływy robocze i wprowadzać innowacje w oparciu o Microsoft 365 Defender możliwości. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Ogólnie rzecz biorąc, należy wykonać następujące kroki, aby korzystać z interfejsów API:

- Utwórz aplikację Azure AD z **wieloma dzierżawami**.
- Uzyskaj autoryzację (zgodę) administratora użytkownika, aby aplikacja uzyskiwała dostęp do Microsoft 365 Defender potrzebnych zasobów.
- Pobierz token dostępu przy użyciu tej aplikacji.
- Użyj tokenu, aby uzyskać dostęp do interfejsu API Microsoft 365 Defender.

W poniższych krokach przedstawiono sposób tworzenia aplikacji Azure AD z wieloma dzierżawami, uzyskiwania tokenu dostępu do Microsoft 365 Defender i weryfikowania tokenu.

## <a name="create-the-multi-tenant-app"></a>Tworzenie aplikacji wielodostępnej

1. Zaloguj się do [platformy Azure](https://portal.azure.com) jako użytkownik z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** >  **Rejestracje aplikacji** >  **Nowa rejestracja**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Sekcja rejestracji aplikacji w portalu Microsoft 365 Defender" lightbox="../../media/atp-azure-new-app2.png":::

3. W formularzu rejestracji:

   - Wybierz nazwę aplikacji.
   - W obszarze **Obsługiwane typy kont** wybierz pozycję **Konta w dowolnym katalogu organizacyjnym (dowolny katalog Azure AD) — wielodostępny**.
   - Wypełnij sekcję **Identyfikator URI przekierowania** . Wybierz pozycję Wpisz **Sieć Web** i podaj identyfikator URI przekierowania jako **https://portal.azure.com**.

   Po zakończeniu wypełniania formularza wybierz pozycję **Zarejestruj**.

   :::image type="content" source="../..//media/atp-api-new-app-partner.png" alt-text="Sekcje rejestracji aplikacji w portalu Microsoft 365 Defender" lightbox="../..//media/atp-api-new-app-partner.png":::

4. Na stronie aplikacji wybierz pozycję **Uprawnienia** >  interfejsu **APIDodaj** **uprawnieniaUdodatki** >  używane przez moją organizację >, wpisz **Microsoft Threat Protection** i wybierz pozycję **Microsoft Threat Protection**. Aplikacja może teraz uzyskiwać dostęp do Microsoft 365 Defender.

   > [!TIP]
   > *Usługa Microsoft Threat Protection* jest poprzednią nazwą Microsoft 365 Defender i nie będzie wyświetlana na oryginalnej liście. Aby je wyświetlić, musisz zacząć pisać jego nazwę w polu tekstowym.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Sekcja użycia interfejsów API w portalu Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. Wybierz pozycję **Uprawnienia aplikacji**. Wybierz odpowiednie uprawnienia dla danego scenariusza (na przykład **Incident.Read.All**), a następnie wybierz pozycję **Dodaj uprawnienia**.

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Okienko uprawnień aplikacji w portalu Microsoft 365 Defender" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > Musisz wybrać odpowiednie uprawnienia dla danego scenariusza. *Przeczytaj, że wszystkie zdarzenia* to tylko przykład. Aby określić, którego uprawnienia potrzebujesz, zapoznaj się z sekcją **Uprawnienia** w interfejsie API, który chcesz wywołać.
    >
    > Aby na przykład [uruchamiać zaawansowane zapytania](api-advanced-hunting.md), wybierz uprawnienie "Uruchamianie zaawansowanych zapytań". Aby [wyizolować urządzenie](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), wybierz uprawnienie "Izolowanie maszyny".

6. Wybierz pozycję **Udziel zgody administratora**. Za każdym razem, gdy dodasz uprawnienie, musisz wybrać opcję **Udziel zgody administratora** , aby ta zgoda weszła w życie.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Sekcja umożliwiająca udzielenie zgody administratora w portalu Microsoft 365 Defender" lightbox="../../media/grant-consent.PNG":::

7. Aby dodać wpis tajny do aplikacji, wybierz pozycję **Certyfikaty & wpisów tajnych**, dodaj opis do wpisu tajnego, a następnie wybierz pozycję **Dodaj**.

    > [!TIP]
    > Po wybraniu pozycji **Dodaj** wybierz pozycję **Skopiuj wygenerowaną wartość wpisu tajnego**. Nie będzie można pobrać wartości wpisu tajnego po opuszczeniu.

      :::image type="content" source="../../media/webapp-create-key2.png" alt-text="Sekcja dodawania wpisu tajnego w portalu Microsoft 365 Defender" lightbox="../../media/webapp-create-key2.png":::

8. Zarejestruj identyfikator aplikacji i identyfikator dzierżawy w bezpiecznym miejscu. Są one wyświetlane w obszarze **Przegląd** na stronie aplikacji.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Okienko Przegląd w portalu Microsoft 365 Defender" lightbox="../../media/app-and-tenant-ids.png":::

9. Dodaj aplikację do dzierżawy użytkownika.

   Ponieważ aplikacja współdziała z Microsoft 365 Defender w imieniu użytkowników, musi zostać zatwierdzona dla każdej dzierżawy, w której zamierzasz z niej korzystać.

   **Administrator globalny** z dzierżawy użytkownika musi wyświetlić link zgody i zatwierdzić aplikację.

   Link zgody ma następujący formularz:

   ```HTTP
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Cyfry `00000000-0000-0000-0000-000000000000` powinny zostać zastąpione identyfikatorem aplikacji.

   Po kliknięciu linku zgody zaloguj się przy użyciu administratora globalnego dzierżawy użytkownika i zgody aplikacji.

   :::image type="content" source="../../media/app-consent-partner.png" alt-text="Strona aplikacji zgody w portalu Microsoft 365 Defender" lightbox="../../media/app-consent-partner.png":::

   Musisz również poprosić użytkownika o identyfikator dzierżawy. Identyfikator dzierżawy jest jednym z identyfikatorów używanych do uzyskiwania tokenów dostępu.

- **Ukończono!** Aplikacja została pomyślnie zarejestrowana.
- Zapoznaj się z poniższymi przykładami dotyczącymi uzyskiwania i walidacji tokenu.

## <a name="get-an-access-token"></a>Uzyskiwanie tokenu dostępu

Aby uzyskać więcej informacji na temat tokenów Azure AD, zobacz [samouczek Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Chociaż przykłady w tej sekcji zachęcają do wklejania wartości wpisów tajnych do celów testowych, **nigdy nie należy kodować wpisów tajnych** do aplikacji działającej w środowisku produkcyjnym. Inna firma może użyć Twojego wpisu tajnego do uzyskania dostępu do zasobów. Możesz pomóc w zabezpieczeniu wpisów tajnych aplikacji przy użyciu [usługi Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). Praktyczny przykład sposobu ochrony aplikacji można znaleźć [w temacie Zarządzanie wpisami tajnymi w aplikacjach serwera przy użyciu usługi Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

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

### <a name="get-an-access-token-using-c"></a>Uzyskiwanie tokenu dostępu przy użyciu języka C\#

> [!NOTE]
> Poniższy kod został przetestowany przy użyciu narzędzia Nuget Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

> [!IMPORTANT]
> Pakiet [microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) NuGet i biblioteka uwierzytelniania Azure AD (ADAL) zostały przestarzałe. Od 30 czerwca 2020 r. nie dodano żadnych nowych funkcji.   Zdecydowanie zachęcamy do uaktualnienia. Aby uzyskać więcej informacji, zobacz [przewodnik migracji](/azure/active-directory/develop/msal-migration) .

1. Utwórz nową aplikację konsolową.
1. Zainstaluj NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
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

### <a name="get-an-access-token-using-python"></a>Uzyskiwanie tokenu dostępu przy użyciu języka Python

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

### <a name="get-an-access-token-using-curl"></a>Uzyskiwanie tokenu dostępu przy użyciu narzędzia curl

> [!NOTE]
> Program Curl jest wstępnie instalowany w Windows 10, wersjach 1803 i nowszych. W przypadku innych wersji Windows pobierz i zainstaluj narzędzie bezpośrednio z [oficjalnej witryny internetowej curl](https://curl.haxx.se/windows/).

1. Otwórz wiersz polecenia i ustaw CLIENT_ID na identyfikator aplikacji platformy Azure.
1. Ustaw CLIENT_SECRET na wpis tajny aplikacji platformy Azure.
1. Ustaw TENANT_ID na identyfikator dzierżawy platformy Azure użytkownika, który chce korzystać z aplikacji w celu uzyskania dostępu do Microsoft 365 Defender.
1. Uruchom następujące polecenie:

```bash
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Pomyślna odpowiedź będzie wyglądać następująco:

```bash
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Weryfikowanie tokenu

1. Skopiuj i wklej token do [witryny internetowej modułu sprawdzania poprawności tokenu internetowego JSON JWT,](https://jwt.ms) aby go odkodować.
1. Upewnij się, że *oświadczenia ról* w ramach dekodowanego tokenu zawierają żądane uprawnienia.

Na poniższej ilustracji widać dekodowany token uzyskany z aplikacji z ```Incidents.Read.All```uprawnieniami , ```Incidents.ReadWrite.All```i :```AdvancedHunting.Read.All```

:::image type="content" source="../../media/webapp-decoded-token.png" alt-text="Okienko Token dekodowany w portalu Microsoft 365 Defender" lightbox="../../media/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Uzyskiwanie dostępu do interfejsu API Microsoft 365 Defender przy użyciu tokenu

1. Wybierz interfejs API, którego chcesz użyć (zdarzenia lub zaawansowane wyszukiwanie zagrożeń). Aby uzyskać więcej informacji, zobacz [Obsługiwane interfejsy API Microsoft 365 Defender](api-supported.md).
2. W żądaniu http, które zamierzasz wysłać, ustaw nagłówek autoryzacji na `"Bearer" <token>`wartość , *Element nośny* jest schematem autoryzacji, a *token* jest zweryfikowanym tokenem.
3. Token wygaśnie w ciągu jednej godziny. W tym czasie możesz wysłać więcej niż jedno żądanie z tym samym tokenem.

W poniższym przykładzie pokazano, jak wysłać żądanie, aby uzyskać listę zdarzeń **przy użyciu języka C#**.

```C#
   var httpClient = new HttpClient();
   var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

   request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

   var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>Artykuły pokrewne

- [Omówienie interfejsów API Microsoft 365 Defender](api-overview.md)
- [Uzyskiwanie dostępu do interfejsów API Microsoft 365 Defender](api-access.md)
- [Tworzenie aplikacji "Hello world"](api-hello-world.md)
- [Tworzenie aplikacji w celu uzyskania dostępu do Microsoft 365 Defender bez użytkownika](api-create-app-web.md)
- [Tworzenie aplikacji w celu uzyskania dostępu do interfejsów API Microsoft 365 Defender w imieniu użytkownika](api-create-app-user-context.md)
- [Dowiedz się więcej o limitach interfejsu API i licencjonowaniu](api-terms.md)
- [Omówienie kodów błędów](api-error-codes.md)
- [Zarządzanie wpisami tajnymi w aplikacjach serwera przy użyciu usługi Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Autoryzacja protokołu OAuth 2.0 na potrzeby logowania użytkownika i dostępu do interfejsu API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
