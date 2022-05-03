---
title: Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender
ms.reviewer: ''
description: Dowiedz się, jak zaprojektować natywną aplikację Windows, aby uzyskać programowy dostęp do Ochrona punktu końcowego w usłudze Microsoft Defender bez użytkownika.
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
ms.openlocfilehash: aec4c7bdc0da76a6a52a8b8f19d89b8b54f3df9f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173474"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/index.yml)

> [!IMPORTANT]
> Zaawansowane możliwości wyszukiwania zagrożeń nie są uwzględniane w usłudze Defender dla firm. Zobacz [Porównanie Microsoft Defender dla Firm z planami Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Na tej stronie opisano sposób tworzenia aplikacji w celu uzyskania dostępu programowego do usługi Defender for Endpoint w imieniu użytkownika.

Jeśli potrzebujesz dostępu programowego Ochrona punktu końcowego w usłudze Microsoft Defender bez użytkownika, zapoznaj się z artykułem [Access Ochrona punktu końcowego w usłudze Microsoft Defender with application context (Dostęp Ochrona punktu końcowego w usłudze Microsoft Defender z kontekstem aplikacji](exposed-apis-create-app-webapp.md)).

Jeśli nie masz pewności, jakiego dostępu potrzebujesz, przeczytaj [stronę Wprowadzenie](apis-intro.md).

Ochrona punktu końcowego w usłudze Microsoft Defender uwidacznia wiele swoich danych i akcji za pośrednictwem zestawu programowych interfejsów API. Te interfejsy API umożliwiają automatyzację przepływów roboczych i wprowadzanie innowacji w oparciu o Ochrona punktu końcowego w usłudze Microsoft Defender możliwości. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Ogólnie rzecz biorąc, należy wykonać następujące kroki, aby korzystać z interfejsów API:

- Tworzenie aplikacji AAD
- Uzyskiwanie tokenu dostępu przy użyciu tej aplikacji
- Uzyskiwanie dostępu do interfejsu API usługi Defender for Endpoint przy użyciu tokenu

Na tej stronie wyjaśniono, jak utworzyć aplikację AAD, uzyskać token dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender i zweryfikować token.

> [!NOTE]
> Podczas uzyskiwania dostępu do interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender w imieniu użytkownika potrzebne są odpowiednie uprawnienia aplikacji i uprawnienia użytkownika.
> Jeśli nie znasz uprawnień użytkowników na Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Zarządzanie dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md).

> [!TIP]
> Jeśli masz uprawnienia do wykonywania akcji w portalu, masz uprawnienia do wykonywania akcji w interfejsie API.

## <a name="create-an-app"></a>Tworzenie aplikacji

1. Zaloguj się na platformie [Azure](https://portal.azure.com) przy użyciu konta użytkownika z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** \> **Rejestracje aplikacji** \> **Nowa rejestracja**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Strona Rejestracje aplikacji w portalu Microsoft Azure" lightbox="images/atp-azure-new-app2.png":::

3. Po **wyświetleniu strony Rejestrowanie aplikacji** wprowadź informacje o rejestracji aplikacji:
   - **Nazwa** — wprowadź znaczącą nazwę aplikacji, która będzie wyświetlana użytkownikom aplikacji.
   - **Obsługiwane typy kont** — wybierz konta, które chcesz obsługiwać w aplikacji.

     <br>

     |Obsługiwane typy kont|Opis|
     |---|---|
     |**Konta tylko w tym katalogu organizacyjnym**|Wybierz tę opcję, jeśli tworzysz aplikację biznesową (LOB). Ta opcja jest niedostępna, jeśli nie rejestrujesz aplikacji w katalogu. <p> Ta opcja jest mapowana na Azure AD tylko jedną dzierżawę. <p> Jest to opcja domyślna, chyba że rejestrujesz aplikację poza katalogiem. W przypadkach, gdy aplikacja jest zarejestrowana poza katalogiem, ustawieniem domyślnym jest Azure AD wielodostępnych i osobistych kont Microsoft.|
     |**Konta w dowolnym katalogu organizacyjnym**|Wybierz tę opcję, jeśli chcesz kierować dane do wszystkich klientów biznesowych i edukacyjnych. <p> Ta opcja jest mapowana na Azure AD tylko wielodostępną. <p> Jeśli aplikacja została zarejestrowana jako Azure AD tylko jednej dzierżawy, możesz ją zaktualizować tak, aby była Azure AD wielodostępna i z powrotem do jednej dzierżawy za pośrednictwem bloku **Uwierzytelnianie**.|
     |**Konta w dowolnym katalogu organizacyjnym i osobistych kontach Microsoft**|Wybierz tę opcję, aby kierować dane do najszerszego zestawu klientów. <p> Ta opcja jest mapowana na Azure AD wielodostępnych i osobistych kont Microsoft. <p> Jeśli aplikacja została zarejestrowana jako Azure AD wielodostępnych i osobistych kont Microsoft, nie można tego zmienić w interfejsie użytkownika. Zamiast tego należy użyć edytora manifestu aplikacji, aby zmienić obsługiwane typy kont.|

   - **Identyfikator URI przekierowania (opcjonalnie)** — wybierz typ aplikacji, którą tworzysz, klienta **internetowego** lub **publicznego (mobile & desktop),** a następnie wprowadź identyfikator URI przekierowania (lub adres URL odpowiedzi) dla aplikacji.

     - W przypadku aplikacji internetowych podaj podstawowy adres URL aplikacji. Może to być na przykład `http://localhost:31544` adres URL aplikacji internetowej działającej na komputerze lokalnym. Użytkownicy będą używać tego adresu URL do logowania się do aplikacji klienckiej sieci Web.

     - W przypadku publicznych aplikacji klienckich podaj identyfikator URI używany przez Azure AD do zwracania odpowiedzi tokenu. Wprowadź wartość specyficzną dla aplikacji, taką jak `myapp://auth`.

     Aby wyświetlić konkretne przykłady aplikacji internetowych lub aplikacji natywnych, zapoznaj się z [naszymi przewodnikami Szybki start](/azure/active-directory/develop/#quickstarts).

     Po zakończeniu wybierz pozycję **Zarejestruj**.

4. Zezwalaj aplikacji na dostęp do Ochrona punktu końcowego w usłudze Microsoft Defender i przypisz jej uprawnienie "Odczyt alertów":

   - Na stronie aplikacji wybierz pozycję **Uprawnienia interfejsu API Dodaj interfejsy** \> API **uprawnień**\>, **których moja organizacja używa** > wpisz **WindowsDefenderATP** i wybierz pozycję **WindowsDefenderATP**.

     > [!NOTE]
     > *WindowsDefenderATP* nie jest wyświetlany na oryginalnej liście. Zacznij pisać jego nazwę w polu tekstowym, aby zobaczyć, jak jest wyświetlana.

     :::image type="content" alt-text="dodaj uprawnienie." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - Wybierz **pozycję Uprawnienia** \> delegowane **Alert.Odczyt** > wybierz pozycję **Dodaj uprawnienia**.

      :::image type="content" source="images/application-permissions-public-client.png" alt-text="Okienka typów i uprawnień aplikacji" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > Wybierz odpowiednie uprawnienia. Alerty odczytu to tylko przykład.

     Przykład:

     - Aby [uruchomić zaawansowane zapytania](run-advanced-query-api.md), wybierz pozycję **Uruchom zaawansowane zapytania uprawnienie** .
     - Aby [wyizolować urządzenie](isolate-machine.md), wybierz pozycję **Izolowanie uprawnień maszyny** .
     - Aby określić, które uprawnienia są potrzebne, zapoznaj się z sekcją **Uprawnienia** w interfejsie API, który chcesz wywołać.

   - Wybierz pozycję **Udziel zgody**.

      > [!NOTE]
      > Za każdym razem, gdy dodasz uprawnienie, musisz wybrać pozycję **Udziel zgody** , aby nowe uprawnienie weszło w życie.

      :::image type="content" source="images/grant-consent.png" alt-text="Opcja zgody administratora wielkiego" lightbox="images/grant-consent.png":::

5. Zapisz identyfikator aplikacji i identyfikator dzierżawy.

    Na stronie aplikacji przejdź do pozycji **Przegląd** i skopiuj następujące informacje:

    :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Identyfikator utworzonej aplikacji"  lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Uzyskiwanie tokenu dostępu

Aby uzyskać więcej informacji na temat tokenów AAD, zobacz [samouczek Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="using-c"></a>Korzystanie z języka C\#

- Skopiuj/wklej poniższą klasę w aplikacji.
- Użyj metody **AcquireUserTokenAsync** z identyfikatorem aplikacji, identyfikatorem dzierżawy, nazwą użytkownika i hasłem, aby uzyskać token.

    ```csharp
    namespace WindowsDefenderATP
    {
        using System.Net.Http;
        using System.Text;
        using System.Threading.Tasks;
        using Newtonsoft.Json.Linq;

        public static class WindowsDefenderATPUtils
        {
            private const string Authority = "https://login.microsoftonline.com";

            private const string WdatpResourceId = "https://api.securitycenter.microsoft.com";

            public static async Task<string> AcquireUserTokenAsync(string username, string password, string appId, string tenantId)
            {
                using (var httpClient = new HttpClient())
                {
                    var urlEncodedBody = $"resource={WdatpResourceId}&client_id={appId}&grant_type=password&username={username}&password={password}";

                    var stringContent = new StringContent(urlEncodedBody, Encoding.UTF8, "application/x-www-form-urlencoded");

                    using (var response = await httpClient.PostAsync($"{Authority}/{tenantId}/oauth2/token", stringContent).ConfigureAwait(false))
                    {
                        response.EnsureSuccessStatusCode();

                        var json = await response.Content.ReadAsStringAsync().ConfigureAwait(false);

                        var jObject = JObject.Parse(json);

                        return jObject["access_token"].Value<string>();
                    }
                }
            }
        }
    }
    ```

## <a name="validate-the-token"></a>Weryfikowanie tokenu

Sprawdź, czy masz prawidłowy token:

- Skopiuj/wklej do [narzędzia JWT](https://jwt.ms) token uzyskany w poprzednim kroku, aby go odkodować.
- Sprawdź, czy otrzymasz oświadczenie "scp" z odpowiednimi uprawnieniami aplikacji.
- Na poniższym zrzucie ekranu widać dekodowany token uzyskany z aplikacji w samouczku:

  :::image type="content" source="images/nativeapp-decoded-token.png" alt-text="Strona weryfikacji tokenu" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Uzyskiwanie dostępu do interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu tokenu

- Wybierz interfejs API, którego chcesz użyć — [obsługiwane Ochrona punktu końcowego w usłudze Microsoft Defender interfejsy API](exposed-apis-list.md).
- Ustaw nagłówek autoryzacji w żądaniu HTTP wysyłanym do elementu "Bearer {token}" (element nośny jest schematem autoryzacji).
- Czas wygaśnięcia tokenu wynosi 1 godzinę (możesz wysłać więcej niż jedno żądanie z tym samym tokenem).

- Przykład wysyłania żądania uzyskania listy alertów **przy użyciu języka C#**:

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Zobacz też

- [interfejsy API Ochrona punktu końcowego w usłudze Microsoft Defender](exposed-apis-list.md)
- [Dostęp Ochrona punktu końcowego w usłudze Microsoft Defender z kontekstem aplikacji](exposed-apis-create-app-webapp.md)
