---
title: Hello World for Microsoft 365 Defender REST API
description: Dowiedz się, jak utworzyć aplikację i używać tokenu w celu uzyskiwania dostępu do Microsoft 365 Defender API
keywords: app, token, dostęp, aad, aplikacja, rejestracja aplikacji, powershell, skrypt, administrator globalny, uprawnienia, microsoft 365 defender
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
ms.openlocfilehash: 3a8696a14b85374d4bcb0a8704c14b82fdd845b5
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754599"
---
# <a name="hello-world-for-microsoft-365-defender-rest-api"></a>Hello World for Microsoft 365 Defender REST API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

## <a name="get-incidents-using-a-simple-powershell-script"></a>Uzyskiwanie zdarzeń przy użyciu prostego skryptu programu PowerShell

Ukończenie projektu powinno potrwać od 5 do 10 minut. Ten szacowany czas obejmuje rejestrowanie aplikacji i stosowanie kodu z przykładowego skryptu programu PowerShell.

### <a name="register-an-app-in-azure-active-directory"></a>Rejestrowanie aplikacji w aplikacji Azure Active Directory

1. Zaloguj się do [platformy Azure](https://portal.azure.com) jako użytkownik z rolą **administratora** globalnego.

2. Przejdź do **Azure Active Directory** >  **Rejestracja aplikacjiAppNew** >  **registration**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Sekcja Nowa rejestracja w portalu Microsoft 365 Defender nową" lightbox="../../media/atp-azure-new-app2.png":::

3. W formularzu rejestracji wybierz nazwę aplikacji, a następnie wybierz pozycję **Zarejestruj**. Wybranie przekierowania URI jest opcjonalne. Nie będzie potrzebna do wykonania tego przykładu.

4. Na stronie aplikacji wybierz pozycję Uprawnienia **interfejsu APIUdzyskaj** >  >  **uprawnieniaAPImki** używane przez moją organizację >, wpisz **Microsoft Threat Protection** i wybierz pozycję **Microsoft Threat Protection**. Aplikacja może teraz uzyskać dostęp do Microsoft 365 Defender.

   > [!TIP]
   > *Ochrona przed zagrożeniami firmy Microsoft* to wcześniejsza Microsoft 365 Defender i nie będzie wyświetlana na oryginalnej liście. Aby tekst był wyświetlany, musisz rozpocząć pisanie jego nazwy w polu tekstowym.
   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Sekcja użycia interfejsów API w portalu Microsoft 365 Defender sieci" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - Wybierz **pozycję Uprawnienia** **aplikacjiIncident.Read.All** >  i **wybierz pozycję Dodaj uprawnienia**.

     :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Okienko uprawnień aplikacji w portalu Microsoft 365 Defender aplikacji" lightbox="../../media/request-api-permissions.PNG":::

5. Wybierz pozycję **Utłań zgodę administratora**. Za każdym razem, gdy dodajesz uprawnienie, musisz zaznaczyć pozycję Udawaj **administratorów** , aby je obowiązywało.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Sekcja Udzielanie zgody administratora w portalu Microsoft 365 Defender użytkowników" lightbox="../../media/grant-consent.PNG":::

6. Dodaj do aplikacji klucz tajny. Wybierz **pozycję Certyfikaty & sekrety**, dodaj opis tajemnicy, a następnie wybierz pozycję **Dodaj**.

    > [!TIP]
    > Po wybraniu **przycisku Dodaj** wybierz **pozycję kopiuj wygenerowaną wartość tajnych**. Po opuszczeniu nie będzie można pobrać wartości tajnej.

    :::image type="content" source="../../media/webapp-create-key2.png" alt-text="Sekcja add secret w Microsoft 365 Defender portal" lightbox="../../media/webapp-create-key2.png":::
    

7. Zanotuj swój identyfikator aplikacji i identyfikator dzierżawy w bezpiecznym miejscu. Są one wymienione w obszarze **Omówienie** na stronie aplikacji.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Sekcja Omówienie w portalu Microsoft 365 Defender informacje" lightbox="../../media/app-and-tenant-ids.png":::

### <a name="get-a-token-using-the-app-and-use-the-token-to-access-the-api"></a>Uzyskiwanie tokenu za pomocą aplikacji i uzyskiwanie dostępu do interfejsu API

Aby uzyskać więcej informacji Azure Active Directory tokenów, zobacz [samouczek dotyczący usługi Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Mimo że w przykładzie w tej pokazie aplikacja zachęcała do wklejania swojej tajnej wartości do celów testowych, nie należy nigdy kodować sekretów firmy do aplikacji działającej w środowisku produkcyjnym. Inne firmy mogą używać Twojej tajemnicy do uzyskiwania dostępu do zasobów. Możesz zabezpieczyć tajemnice aplikacji przy użyciu magazynu [kluczy platformy Azure](/azure/key-vault/general/about-keys-secrets-certificates). Aby poznać praktyczne przykłady ochrony aplikacji, zobacz Zarządzanie sekretami aplikacji serwera za pomocą [magazynu kluczy platformy Azure](/learn/modules/manage-secrets-with-azure-key-vault/).

1. Skopiuj poniższy skrypt i wklej go do ulubionego edytora tekstów. Zapisz jako **Get-Token.ps1**. W programie PowerShell ISE można również uruchomić kod w stanie, w którym się znajduje, ale należy go zapisać, ponieważ będzie trzeba go ponownie uruchomić podczas korzystania ze skryptu zdalnego od zdarzeń w następnej sekcji.

    Ten skrypt wygeneruje token i zapisze go w folderze roboczy pod nazwą, na *Latest-token.txt*.

    ```PowerShell
    # This script gets the app context token and saves it to a file named "Latest-token.txt" under the current directory.
    # Paste in your tenant ID, client ID and app secret (App key).

    $tenantId = '' # Paste your directory (tenant) ID here
    $clientId = '' # Paste your application (client) ID here
    $appSecret = '' # # Paste your own app secret here to test, then store it in a safe place!

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

#### <a name="validate-the-token"></a>Sprawdź poprawność tokenu

1. Skopiuj otrzymany token i wklej go do pliku [JWT](https://jwt.ms) , aby go odkodować.
1. *JWT* to skrót od *JSON Web Token*. Dekodowany token będzie zawierać wiele elementów lub roszczeń w formacie JSON. Upewnij się, że *role w* tokenie dekodowany zawierają odpowiednie uprawnienia.

    Na poniższej ilustracji widać dekodowany token nabyte z aplikacji, ```Incidents.Read.All```za pomocą , ```Incidents.ReadWrite.All```i ```AdvancedHunting.Read.All``` uprawnień:

    :::image type="content" source="../../media/api-jwt-ms.png" alt-text="Sekcja Token dekodowany w portalu Microsoft 365 Defender sieci Microsoft 365 Defender" lightbox="../../media/api-jwt-ms.png":::

### <a name="get-a-list-of-recent-incidents"></a>Uzyskiwanie listy ostatnich zdarzeń

W poniższym skrypcie **Get-Token.ps1uzyskać** dostęp do interfejsu API. Następnie pobiera listę zdarzeń, które zostały ostatnio zaktualizowane w ciągu ostatnich 48 godzin, i zapisuje listę jako plik JSON.

> [!IMPORTANT]
> Zapisz ten skrypt w tym samym folderze, który został **Get-Token.ps1**.

```PowerShell
# This script returns incidents last updated within the past 48 hours.

$token = ./Get-Token.ps1

# Get incidents from the past 48 hours.
# The script may appear to fail if you don't have any incidents in that time frame.
$dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

# This URL contains the type of query and the time filter we created above.
# Note that `$filter` does not refer to a local variable in our script --
# it's actually an OData operator and part of the API's syntax.
$url = "https://api.security.microsoft.com/api/incidents?$filter=lastUpdateTime+ge+$dateTime"

# Set the webrequest headers
$headers = @{
    'Content-Type' = 'application/json'
    'Accept' = 'application/json'
    'Authorization' = "Bearer $token"
}

# Send the request and get the results.
$response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

# Extract the incidents from the results.
$incidents =  ($response | ConvertFrom-Json).value | ConvertTo-Json -Depth 99

# Get a string containing the execution time. We concatenate that string to the name 
# of the output file to avoid overwriting the file on consecutive runs of the script.
$dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

# Save the result as json
$outputJsonPath = "./Latest Incidents $dateTimeForFileName.json"

Out-File -FilePath $outputJsonPath -InputObject $incidents
```

Wszystko gotowe! Pomyślnie:

- Utworzono i zarejestrowano aplikację.
- Ta aplikacja udzieliła uprawnień do odczytu alertów.
- Połączony z interfejsem API.
- Używali skryptu programu PowerShell do zwracania zdarzeń zaktualizowanych w ciągu ostatnich 48 godzin.

## <a name="related-articles"></a>Artykuły pokrewne

- [Microsoft 365 Defender interfejsów API — omówienie](api-overview.md)
- [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md)
- [Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender dostępu bez użytkownika](api-create-app-web.md)
- [Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender interfejsów API w imieniu użytkownika](api-create-app-user-context.md)
- [Tworzenie aplikacji z dostępem partnera z wieloma dzierżawami do Microsoft 365 Defender API](api-partner-access.md)
- [Zarządzanie sekretami aplikacji serwera za pomocą magazynu kluczy platformy Azure](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Autoryzacja protokołu OAuth 2.0 do logowania użytkownika i dostępu do interfejsu API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)