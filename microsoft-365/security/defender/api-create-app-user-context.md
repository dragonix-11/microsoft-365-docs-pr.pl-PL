---
title: Tworzenie aplikacji w celu uzyskania dostępu do interfejsów API Microsoft 365 Defender w imieniu użytkownika
description: Dowiedz się, jak uzyskiwać dostęp do interfejsów API Microsoft 365 Defender w imieniu użytkownika.
keywords: dostęp w imieniu użytkownika, interfejsu API, aplikacji, użytkownika, tokenu dostępu, tokenu,
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
ms.openlocfilehash: 41f2763d73bbb9ed0b7ae32dce431cb2c1a4d71f
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102597"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>Tworzenie aplikacji w celu uzyskania dostępu do interfejsów API Microsoft 365 Defender w imieniu użytkownika

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Na tej stronie opisano sposób tworzenia aplikacji w celu uzyskania dostępu programowego do Microsoft 365 Defender w imieniu jednego użytkownika.

Jeśli potrzebujesz dostępu programowego do Microsoft 365 Defender bez zdefiniowanego użytkownika (na przykład w przypadku pisania aplikacji w tle lub demona), zobacz [Tworzenie aplikacji w celu uzyskania dostępu do Microsoft 365 Defender bez użytkownika](api-create-app-web.md). Jeśli chcesz zapewnić dostęp dla wielu dzierżaw — na przykład jeśli obsługujesz dużą organizację lub grupę klientów — zobacz [Tworzenie aplikacji z dostępem partnera do interfejsów API Microsoft 365 Defender](api-partner-access.md). Jeśli nie masz pewności, jakiego rodzaju dostępu potrzebujesz, zobacz [Első lépések](api-access.md).

Microsoft 365 Defender uwidacznia wiele swoich danych i akcji za pośrednictwem zestawu programowych interfejsów API. Te interfejsy API ułatwiają automatyzowanie przepływów pracy i korzystanie z możliwości Microsoft 365 Defender. Ten dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Ogólnie rzecz biorąc, należy wykonać następujące kroki, aby użyć tych interfejsów API:

- Utwórz aplikację Azure Active Directory (Azure AD).
- Pobierz token dostępu przy użyciu tej aplikacji.
- Użyj tokenu, aby uzyskać dostęp do interfejsu API Microsoft 365 Defender.

W tym artykule wyjaśniono, jak:

- Tworzenie aplikacji Azure AD
- Uzyskiwanie tokenu dostępu do Microsoft 365 Defender
- Weryfikowanie tokenu

> [!NOTE]
> Podczas uzyskiwania dostępu do interfejsu API Microsoft 365 Defender w imieniu użytkownika potrzebne są odpowiednie uprawnienia aplikacji i uprawnienia użytkownika.

> [!TIP]
> Jeśli masz uprawnienia do wykonywania akcji w portalu, masz uprawnienia do wykonywania akcji w interfejsie API.

## <a name="create-an-app"></a>Tworzenie aplikacji

1. Zaloguj się do [platformy Azure](https://portal.azure.com) jako użytkownik z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** >  **App-registraties** >  **Nowa rejestracja**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Opcja Nowa rejestracja w okienku Zarządzanie w Azure-Portal" lightbox="../../media/atp-azure-new-app2.png":::

3. W formularzu wybierz nazwę aplikacji i wprowadź następujące informacje dotyczące identyfikatora URI przekierowania, a następnie wybierz pozycję **Zarejestruj**.

   :::image type="content" source="../../media/nativeapp-create2.PNG" alt-text="Okienko rejestracji aplikacji w Azure-Portal" lightbox="../../media/nativeapp-create2.PNG":::
   

   - **Typ aplikacji:** Klient publiczny
   - **Identyfikator URI przekierowania:** https://portal.azure.com

4. Na stronie aplikacji wybierz pozycję **Uprawnienia interfejsu API****Dodaj interfejsy** >  API uprawnień  > **używane przez moją organizację** >, wpisz **Microsoft Threat Protection** i wybierz pozycję **Microsoft Threat Protection**. Aplikacja może teraz uzyskiwać dostęp do Microsoft 365 Defender.

   > [!TIP]
   > *Usługa Microsoft Threat Protection* jest poprzednią nazwą Microsoft 365 Defender i nie będzie wyświetlana na oryginalnej liście. Aby je wyświetlić, musisz zacząć pisać jego nazwę w polu tekstowym.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Okienko interfejsów API organizacji w portalu Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - Wybierz **pozycję Uprawnienia delegowane**. Wybierz odpowiednie uprawnienia dla danego scenariusza (na przykład **Incident.Read**), a następnie wybierz pozycję **Dodaj uprawnienia**.

     :::image type="content" source="../../media/request-api-permissions-delegated.PNG" alt-text="Okienko Uprawnienia delegowane w portalu Microsoft 365 Defender" lightbox="../../media/request-api-permissions-delegated.PNG":::

    > [!NOTE]
    > Musisz wybrać odpowiednie uprawnienia dla danego scenariusza. *Przeczytaj, że wszystkie zdarzenia* to tylko przykład. Aby określić, którego uprawnienia potrzebujesz, zapoznaj się z sekcją **Uprawnienia** w interfejsie API, który chcesz wywołać.
    >
    > Aby na przykład [uruchamiać zaawansowane zapytania](api-advanced-hunting.md), wybierz uprawnienie "Uruchamianie zaawansowanych zapytań". Aby [wyizolować urządzenie](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), wybierz uprawnienie "Izolowanie maszyny".

5. Wybierz pozycję **Udziel zgody administratora**. Za każdym razem, gdy dodasz uprawnienie, musisz wybrać opcję **Udziel zgody administratora** , aby ta zgoda weszła w życie.

   :::image type="content" source="../../media/grant-consent-delegated.PNG" alt-text="Okienko udzielania zgody administratora w portalu Microsoft 365 Defender" lightbox="../../media/grant-consent-delegated.PNG":::

6. Zarejestruj identyfikator aplikacji i identyfikator dzierżawy w bezpiecznym miejscu. Są one wyświetlane w obszarze **Przegląd** na stronie aplikacji.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Okienko Przegląd w portalu Microsoft 365 Defender" lightbox="../../media/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Uzyskiwanie tokenu dostępu

Aby uzyskać więcej informacji na temat tokenów Azure Active Directory, zobacz [samouczek Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-on-behalf-of-a-user-using-powershell"></a>Uzyskiwanie tokenu dostępu w imieniu użytkownika przy użyciu programu PowerShell

Użyj biblioteki MSAL.PS, aby uzyskać tokeny dostępu z uprawnieniami delegowanymi. Uruchom następujące polecenia, aby uzyskać token dostępu w imieniu użytkownika:

```PowerShell
Install-Module -Name MSAL.PS # Install the MSAL.PS module from PowerShell Gallery

$TenantId = " " # Paste your directory (tenant) ID here.
$AppClientId="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" # Paste your application (client) ID here.

$MsalParams = @{
   ClientId = $AppClientId
   TenantId = $TenantId
   Scopes   = 'https://graph.microsoft.com/User.Read.All','https://graph.microsoft.com/Files.ReadWrite'
}

$MsalResponse = Get-MsalToken @MsalParams
$AccessToken  = $MsalResponse.AccessToken
 
$AccessToken # Display the token in PS console
```
## <a name="validate-the-token"></a>Weryfikowanie tokenu

1. Skopiuj i wklej token do [narzędzia JWT,](https://jwt.ms) aby go odkodować.
2. Upewnij się, że *oświadczenia ról* w ramach dekodowanego tokenu zawierają żądane uprawnienia.

Na poniższej ilustracji widać dekodowany token uzyskany z aplikacji z ```Incidents.Read.All```uprawnieniami , ```Incidents.ReadWrite.All```i :```AdvancedHunting.Read.All```

:::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Sekcja uprawnień w okienku Token dekodowany w portalu Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

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

## <a name="related-articles"></a>Powiązane artykuły:

- [Omówienie interfejsów API Microsoft 365 Defender](api-overview.md)
- [Uzyskiwanie dostępu do interfejsów API Microsoft 365 Defender](api-access.md)
- [Tworzenie aplikacji "Hello world"](api-hello-world.md)
- [Tworzenie aplikacji w celu uzyskania dostępu do Microsoft 365 Defender bez użytkownika](api-create-app-web.md)
- [Tworzenie aplikacji z dostępem partnerów z wieloma dzierżawami do interfejsów API Microsoft 365 Defender](api-partner-access.md)
- [Dowiedz się więcej o limitach interfejsu API i licencjonowaniu](api-terms.md)
- [Omówienie kodów błędów](api-error-codes.md)
- [Autoryzacja protokołu OAuth 2.0 na potrzeby logowania użytkownika i dostępu do interfejsu API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
