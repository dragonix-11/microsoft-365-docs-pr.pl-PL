---
title: Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender dostępu bez użytkownika
description: Dowiedz się, jak utworzyć aplikację, aby uzyskać Microsoft 365 Defender dostępu bez użytkownika.
keywords: app, access, api, create
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
ms.openlocfilehash: 01d6a00bba5bd286e6c741dce6ec6ba3fa3625a1
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755607"
---
# <a name="create-an-app-to-access-microsoft-365-defender-without-a-user"></a>Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender dostępu bez użytkownika

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Na tej stronie opisano, jak utworzyć aplikację, aby uzyskać dostęp programowy do usługi Microsoft 365 Defender bez zdefiniowanego użytkownika — na przykład w przypadku tworzenia daemona lub usługi tła.

Jeśli potrzebujesz dostępu programowego do usługi Microsoft 365 Defender w imieniu jednego lub większej liczby użytkowników, zobacz Tworzenie aplikacji w celu uzyskiwania dostępu do interfejsów [API usługi Microsoft 365 Defender](api-create-app-user-context.md) w imieniu użytkownika i Tworzenie aplikacji z dostępem partnera do interfejsów [API](api-partner-access.md) usługi Microsoft 365 Defender. Jeśli nie masz pewności, jakiego rodzaju dostępu potrzebujesz, zobacz [Wprowadzenie](api-access.md).

Microsoft 365 Defender udostępnia większość danych i akcji za pośrednictwem zestawu interfejsów API programistycznych. Te interfejsy API ułatwiają automatyzowanie przepływów pracy i korzystanie Microsoft 365 Defender możliwości firmy. Ten dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji protokołu OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Aby używać tych interfejsów API, należy wykonać następujące czynności:

- Utwórz aplikację usługi Azure Active Directory (Azure AD).
- Uzyskaj token dostępu przy użyciu tej aplikacji.
- Token umożliwia uzyskanie dostępu do Microsoft 365 Defender API.

W tym artykule wyjaśniono, jak to zrobić:

- Tworzenie aplikacji usługi Azure AD
- Uzyskiwanie tokenu dostępu do Microsoft 365 Defender
- Sprawdź poprawność tokenu.

## <a name="create-an-app"></a>Tworzenie aplikacji

1. Zaloguj się do [platformy Azure](https://portal.azure.com) jako użytkownik z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** >  **Rejestracja aplikacjiAppNew** >  **registration**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Karta Nowa rejestracja w portalu Microsoft 365 Defender nową" lightbox="../../media/atp-azure-new-app2.png":::

3. W formularzu wybierz nazwę aplikacji, a następnie wybierz pozycję **Zarejestruj**.

4. Na stronie aplikacji wybierz pozycję Uprawnienia **interfejsu APIUdzyskaj** >  >  **uprawnieniaAPImki** używane przez moją organizację >, wpisz **Microsoft Threat Protection** i wybierz pozycję **Microsoft Threat Protection**. Aplikacja może teraz uzyskać dostęp do Microsoft 365 Defender.

   > [!TIP]
   > *Ochrona przed zagrożeniami firmy Microsoft* to wcześniejsza Microsoft 365 Defender i nie będzie wyświetlana na oryginalnej liście. Aby tekst był wyświetlany, musisz rozpocząć pisanie jego nazwy w polu tekstowym.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Karta użycia interfejsów API organizacji w portalu Microsoft 365 Defender sieci" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. Wybierz **pozycję Uprawnienia aplikacji**. Wybierz odpowiednie uprawnienia dla scenariusza (na przykład **Zdarzenie.Odczyt.Wszystko**), a następnie wybierz **pozycję Dodaj uprawnienia**.

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Okienko uprawnień aplikacji w portalu Microsoft 365 Defender aplikacji" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > Musisz wybrać odpowiednie uprawnienia dla swojego scenariusza. *Czytanie wszystkich zdarzeń to* tylko przykład. Aby ustalić, jakich uprawnień potrzebujesz, zapoznaj się z sekcją **Uprawnienia** w interfejsie API, który chcesz wywołać.
    >
    > Aby na przykład [uruchamiać zapytania zaawansowane](api-advanced-hunting.md), wybierz uprawnienie Uruchamianie zapytań zaawansowanych. aby [odizolować urządzenie](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), wybierz uprawnienie "Wyizoluj komputer".

6. Wybierz pozycję **Utłań zgodę administratora**. Za każdym razem, gdy dodajesz uprawnienie, musisz zaznaczyć pozycję Udawaj **administratorów** , aby je obowiązywało.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Okienko dotyczące udzielania zgody w portalu Microsoft 365 Defender użytkowników" lightbox="../../media/grant-consent.PNG":::

7. Aby dodać do aplikacji klucz tajny, wybierz pozycję Certyfikaty **& sekretów**, dodaj opis do tajemnicy, a następnie wybierz pozycję **Dodaj**.

    > [!TIP]
    > Po wybraniu **przycisku Dodaj** wybierz **pozycję kopiuj wygenerowaną wartość tajnych**. Po opuszczeniu nie będzie można pobrać wartości tajnej.

    :::image type="content" source="../../media/defender-endpoint/webapp-create-key2.png" alt-text="Okienko Tworzenie aplikacji w Microsoft 365 Defender aplikacji" lightbox="../../media/defender-endpoint/webapp-create-key2.png":::

8. Zanotuj swój identyfikator aplikacji i identyfikator dzierżawy w bezpiecznym miejscu. Są one wymienione w obszarze **Omówienie** na stronie aplikacji.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Okienko Przegląd w portalu Microsoft 365 Defender wiadomości" lightbox="../../media/app-and-tenant-ids.png":::

9. **Dotyczy tylko Microsoft 365 Defender partnerów**[: wykonaj](./api-partner-access.md) poniższe instrukcje, aby uzyskać dostęp partnera za pośrednictwem interfejsów API usługi Microsoft 365 Defender, ustaw aplikację jako wielodostępną, aby była dostępna we wszystkich dzierżawach po otrzymaniu zgody administratora. Dostęp partnera jest **wymagany** dla aplikacji innych firm — na przykład w przypadku tworzenia aplikacji, która jest przeznaczona do uruchamiania w dzierżawach wielu klientów. Nie jest **to wymagane** , jeśli utworzysz usługę, którą chcesz uruchomić tylko w dzierżawie, na przykład aplikację do własnego użycia, która będzie wchodzić w interakcje tylko z Twoimi danymi. Aby ustawić aplikację jako wielodostępną:

    - Przejdź do **uwierzytelniania** i dodaj jako https://portal.azure.com redirect **URI (Przekieruj URI**).

    - U dołu strony w obszarze Obsługiwane **typy kont** wybierz opcję Konta w dowolnej  aplikacji katalogu organizacyjnego dla aplikacji z wieloma dzierżawami.

    Ponieważ aplikacja wchodzi w interakcję Microsoft 365 Defender w imieniu użytkowników, musi zostać zatwierdzona dla każdej dzierżawy, w której zamierzasz jej używać.

    Administrator globalny usługi Active Directory dla każdej dzierżawy musi wybrać link zgody i zatwierdzić aplikację.

    Link zgody ma następującą strukturę:

    ```http
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=<00000000-0000-0000-0000-000000000000>&response_type=code&sso_reload=true
    ```

    Cyfry powinny `00000000-0000-0000-0000-000000000000` zostać zastąpione Identyfikatorem aplikacji.  

**Ukończono!** Aplikacja została pomyślnie zarejestrowana! Zobacz poniższe przykłady dotyczące pozyskiwania i sprawdzania poprawności tokenu.

## <a name="get-an-access-token"></a>Uzyskiwanie tokenu dostępu

Aby uzyskać więcej informacji Azure Active Directory tokenów, zobacz [samouczek dotyczący usługi Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Chociaż przykłady w tej sekcji zachęcają do wklejania tajnych wartości do celów testowych,  nie należy nigdy ująć sekretów firmy w aplikacje działające w środowisku produkcyjnym. Inne firmy mogą używać Twojej tajemnicy do uzyskiwania dostępu do zasobów. Możesz zabezpieczyć tajemnice aplikacji przy użyciu magazynu [kluczy platformy Azure](/azure/key-vault/general/about-keys-secrets-certificates). Aby poznać praktyczne przykłady ochrony aplikacji, zobacz Zarządzanie sekretami aplikacji serwera za pomocą [magazynu kluczy platformy Azure](/learn/modules/manage-secrets-with-azure-key-vault/).

### <a name="get-an-access-token-using-powershell"></a>Uzyskiwanie tokenu dostępu przy użyciu programu PowerShell

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

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

1. Ustaw TENANT_ID na identyfikator dzierżawy platformy Azure klienta, który chce używać Twojej aplikacji do uzyskiwania dostępu do Microsoft 365 Defender.

1. Uruchom następujące polecenie:

   ```bash
   curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://api.security.microsoft.com/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
   ```

   Pomyślna odpowiedź będzie wyglądać tak:

   ```bash
   {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
   ```

## <a name="validate-the-token"></a>Sprawdź poprawność tokenu

1. Skopiuj i wklej token do witryny [internetowej JSON tokenu sprawdzania prawidłowego tokenu sieci Web (JWT),](https://jwt.ms) aby go odkodować.

1. Upewnij się, że *role w* tokenie dekodowany zawierają odpowiednie uprawnienia.

   Na poniższej ilustracji widać dekodowany token nabyte z aplikacji, `Incidents.Read.All`za pomocą , `Incidents.ReadWrite.All`i `AdvancedHunting.Read.All` uprawnień:

   :::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Okienko Token dekodowany w Microsoft 365 Defender sieci Microsoft 365 Defender sieci" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

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
- [Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender interfejsów API w imieniu użytkownika](api-create-app-user-context.md)
- [Tworzenie aplikacji z dostępem partnera z wieloma dzierżawami do Microsoft 365 Defender API](api-partner-access.md)
- [Informacje o limitach i licencjonowaniu interfejsu API](api-terms.md)
- [Opis kodów błędów](api-error-codes.md)
- [Zarządzanie sekretami aplikacji serwera za pomocą magazynu kluczy platformy Azure](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Autoryzacja protokołu OAuth 2.0 do logowania użytkownika i dostępu do interfejsu API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)