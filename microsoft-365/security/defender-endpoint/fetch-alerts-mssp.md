---
title: Pobieranie alertów z dzierżawy klientów programu MSSP
description: Dowiedz się, jak pobierać alerty z dzierżawy klienta
keywords: zarządzane zabezpieczenia usługodawca, mssp, konfigurowanie, integracja
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: e2ac36689f9f41badb2f4216198d8818e568778b
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010451"
---
# <a name="fetch-alerts-from-mssp-customer-tenant"></a>Pobieranie alertów z dzierżawy klientów programu MSSP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!NOTE]
> To działanie jest podejmowane przez program MSSP.

Istnieją dwa sposoby pobierania alertów:

- Korzystanie z metody SIEM
- Korzystanie z interfejsów API

## <a name="fetch-alerts-into-your-siem"></a>Pobieranie alertów do SIEM

Aby pobrać alerty do systemu SIEM, musisz wykonać następujące czynności:

- Krok 1. Tworzenie aplikacji innej firmy
- Krok 2. Uzyskiwanie dostępu i odświeżanie tokenów z dzierżawy klienta
- Krok 3. Zezwalanie na dostęp do aplikacji na Microsoft 365 Defender

### <a name="step-1-create-an-application-in-azure-active-directory-azure-ad"></a>Krok 1. Tworzenie aplikacji w usłudze Azure Active Directory (Azure AD)

Musisz utworzyć aplikację i przyznać jej uprawnienia do pobierania alertów z dzierżawy Microsoft 365 Defender klienta.

1. Zaloguj się do portalu [usługi Azure AD](https://aad.portal.azure.com/).

2. Wybierz **Azure Active Directory** \> **rejestracji aplikacji**.

3. Kliknij **pozycję Nowa rejestracja**.

4. Określ następujące wartości:

    - Nazwa: \<Tenant_name\> Łącznik SIEM MSSP (zastąp Tenant_name nazwą wyświetlaną dzierżawy)

    - Obsługiwane typy kont: Tylko konto w tym katalogu organizacyjnym
    - Przekieruj URI: wybierz pozycję Sieć Web `https://<domain_name>/SiemMsspConnector`i wpisz (<domain_name> na nazwę dzierżawy)

5. Kliknij **przycisk Zarejestruj**. Aplikacja zostanie wyświetlona na liście aplikacji, których jesteś właścicielem.

6. Wybierz aplikację, a następnie kliknij pozycję **Omówienie**.

7. Skopiuj wartość z pola **Identyfikator aplikacji (klienta)** do bezpiecznego miejsca. Będzie ona potrzebna w następnym kroku.

8. W **panelu & wybierz** pozycję Certyfikaty i tajemnice.

9. Kliknij **pozycję Nowy klient klucz tajny**.

    - Opis. Wprowadź opis klucza.
    - Wygasa: Wybierz **w ciągu 1 roku**

10. Kliknij **przycisk** Dodaj, skopiuj wartość klienta tajnego do bezpiecznego miejsca. Będzie ona potrzebna w następnym kroku.

### <a name="step-2-get-access-and-refresh-tokens-from-your-customers-tenant"></a>Krok 2. Uzyskiwanie dostępu i odświeżanie tokenów z dzierżawy klienta

W tej sekcji opisano sposób używania skryptu programu PowerShell do uzyskania tokenów z dzierżawy klienta. Ten skrypt używa aplikacji z poprzedniego kroku do uzyskiwania dostępu i odświeżania tokenów przy użyciu kodu autoryzacji OAuth Flow.

Po poświadczeń musisz udzielić zgody na aplikację, aby aplikacja została aprowowana w dzierżawie klienta.

1. Utwórz nowy folder i nadaj temu nazwę: `MsspTokensAcquisition`.

2. Pobierz moduł [LoginBrowser.psm1](https://github.com/shawntabrizi/Microsoft-Authentication-with-PowerShell-and-MSAL/blob/master/Authorization%20Code%20Grant%20Flow/LoginBrowser.psm1) i zapisz go w `MsspTokensAcquisition` folderze.

    > [!NOTE]
    > W wierszu 30 zamień na `authorzationUrl` `authorizationUrl`.

3. Utwórz plik z następującą zawartością i zapisz go pod nazwą `MsspTokensAcquisition.ps1` w folderze:

    ```powershell
    param (
        [Parameter(Mandatory=$true)][string]$clientId,
        [Parameter(Mandatory=$true)][string]$secret,
        [Parameter(Mandatory=$true)][string]$tenantId
    )
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

    # Load our Login Browser Function
    Import-Module .\LoginBrowser.psm1

    # Configuration parameters
    $login = "https://login.microsoftonline.com"
    $redirectUri = "https://SiemMsspConnector"
    $resourceId = "https://graph.windows.net"

    Write-Host 'Prompt the user for his credentials, to get an authorization code'
    $authorizationUrl = ("{0}/{1}/oauth2/authorize?prompt=select_account&response_type=code&client_id={2}&redirect_uri={3}&resource={4}" -f
                        $login, $tenantId, $clientId, $redirectUri, $resourceId)
    Write-Host "authorzationUrl: $authorizationUrl"

    # Fake a proper endpoint for the Redirect URI
    $code = LoginBrowser $authorizationUrl $redirectUri

    # Acquire token using the authorization code

    $Body = @{
        grant_type = 'authorization_code'
        client_id = $clientId
        code = $code
        redirect_uri = $redirectUri
        resource = $resourceId
        client_secret = $secret
    }

    $tokenEndpoint = "$login/$tenantId/oauth2/token?"
    $Response = Invoke-RestMethod -Method Post -Uri $tokenEndpoint -Body $Body
    $token = $Response.access_token
    $refreshToken= $Response.refresh_token

    Write-Host " ----------------------------------- TOKEN ---------------------------------- "
    Write-Host $token

    Write-Host " ----------------------------------- REFRESH TOKEN ---------------------------------- "
    Write-Host $refreshToken
    ```
4. Otwórz wiersz polecenia programu PowerShell z podwyższonym poziomem uprawnień w tym `MsspTokensAcquisition` folderze.

5. Uruchom następujące polecenie: `Set-ExecutionPolicy -ExecutionPolicy Bypass`

6. Wprowadź następujące polecenia: `.\MsspTokensAcquisition.ps1 -clientId <client_id> -secret <app_key> -tenantId <customer_tenant_id>`

    - Zamień \<client_id\> **na identyfikator aplikacji (klienta)** z poprzedniego kroku.
    - Zamień \<app_key\> **na klucz tajny klienta** utworzony w poprzednim kroku.
    - Zamień \<customer_tenant_id\> na identyfikator **dzierżawy klienta**.

7. Zostaniesz poproszony o podanie Twoich poświadczeń i zgody. Zignoruj przekierowanie strony.

8. W oknie programu PowerShell otrzymasz token dostępu i token odświeżania. Zapisz token odświeżania, aby skonfigurować łącznik SIEM.

### <a name="step-3-allow-your-application-on-microsoft-365-defender"></a>Krok 3. Zezwalanie aplikacji na Microsoft 365 Defender

Musisz zezwolić na aplikację utworzoną w programie Microsoft 365 Defender.

Aby zezwolić na aplikację, musisz mieć uprawnienia do zarządzania **ustawieniami systemowym** portalu. W przeciwnym razie musisz poprosić klienta, aby zezwolił na aplikację.

1. Przejdź do `https://security.microsoft.com?tid=<customer_tenant_id>` (zamień \<customer_tenant_id\> na identyfikator dzierżawy klienta).

2. Kliknij **Ustawienia** \> **interfejsów** \> **API interfejsów SIEM** **punktów końcowych**\>.

3. Wybierz **kartę MSSP** .

4. Wprowadź **identyfikator aplikacji w** pierwszym kroku i identyfikator **dzierżawy**.

5. Kliknij **pozycję Autoryzuj aplikację**.

Teraz możesz pobrać odpowiedni plik konfiguracji dla swojego SIEM i połączyć się z interfejsem API Microsoft 365 Defender API. Aby uzyskać więcej informacji, zobacz [Przyciąganie alertów do narzędzi SIEM](configure-siem.md).

- W pliku konfiguracji ArcSight / Splunk Authentication Properties (Właściwości uwierzytelniania Splunk) ręcznie napisz klucz aplikacji, ustawiając wartość tajny.
- Zamiast używać tokenu odświeżania w portalu, użyj skryptu z poprzedniego kroku, aby uzyskać token odświeżania (lub uzyskać go w inny sposób).

## <a name="fetch-alerts-from-mssp-customers-tenant-using-apis"></a>Pobieranie alertów z dzierżawy klienta MSSP przy użyciu interfejsów API

Aby uzyskać informacje na temat zdalnego dostępu do alertów przy użyciu interfejsu API usługi REST, zobacz [Pobieranie alertów z dzierżawy klienta MSSP](fetch-alerts-mssp.md).

## <a name="see-also"></a>Zobacz też

- [Udzielanie dostępu do portalu przez program MSSP](grant-mssp-access.md)
- [Uzyskiwanie dostępu do portalu klientów programu MSSP](access-mssp-portal.md)
- [Konfigurowanie powiadomień alertów](configure-mssp-notifications.md)
