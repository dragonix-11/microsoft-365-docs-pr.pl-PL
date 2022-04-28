---
title: Wdrażanie łącznika w celu archiwizacji danych stron biznesowych usługi Facebook
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ROBOTS: NOINDEX, NOFOLLOW
description: Administratorzy mogą skonfigurować natywny łącznik do importowania i archiwizowania stron biznesowych serwisu Facebook w celu Microsoft 365. Po zaimportowaniu tych danych do Microsoft 365 możesz użyć funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania, aby zarządzać zarządzaniem danymi w serwisie Facebook organizacji.
ms.openlocfilehash: b3f3770b4e3cf8415111ebdd1881905ae21f4739
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098873"
---
# <a name="deploy-a-connector-to-archive-facebook-business-pages-data"></a>Wdrażanie łącznika w celu archiwizacji danych stron biznesowych usługi Facebook

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Ten artykuł zawiera krok po kroku proces wdrażania łącznika, który używa usługi Office 365 Import do importowania danych ze stron biznesowych serwisu Facebook do Microsoft 365. Aby zapoznać się z ogólnym omówieniem tego procesu i listą wymagań wstępnych wymaganych do wdrożenia łącznika usługi Facebook, zobacz [Konfigurowanie łącznika w celu archiwizowania danych serwisu Facebook](archive-facebook-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w Azure Active Directory

1. Przejdź do strony <https://portal.azure.com> i zaloguj się przy użyciu poświadczeń konta administratora globalnego.

    ![Tworzenie aplikacji w AAD.](../media/FBCimage1.png)

2. W okienku nawigacji po lewej stronie kliknij pozycję **Azure Active Directory**.

    ![Kliknij Azure Active Directory.](../media/FBCimage2.png)

3. W okienku nawigacji po lewej stronie kliknij pozycję **Rejestracje aplikacji (wersja zapoznawcza),** a następnie kliknij pozycję **Nowa rejestracja**.

    ![Kliknij pozycję **Rejestracje aplikacji (wersja zapoznawcza)**, a następnie kliknij pozycję **Nowa rejestracja**.](../media/FBCimage3.png)

4. Zarejestruj aplikację. W obszarze Identyfikator URI przekierowania wybierz pozycję Sieć Web na liście rozwijanej typ aplikacji, a następnie wpisz <https://portal.azure.com> w polu identyfikator URI.

   ![Zarejestruj aplikację.](../media/FBCimage4.png)

5. Skopiuj **identyfikator aplikacji (klienta)** i **identyfikator katalogu (dzierżawy)** i zapisz je w pliku tekstowym lub innej bezpiecznej lokalizacji. Te identyfikatory są używane w kolejnych krokach.

   ![Skopiuj identyfikator aplikacji i identyfikator katalogu i zapisz je.](../media/FBCimage5.png)

6. Przejdź do pozycji **Certyfikaty & wpisów tajnych dla nowej aplikacji.**

   ![Przejdź do pozycji Certyfikaty & wpisów tajnych dla nowej aplikacji.](../media/FBCimage6.png)

7. Kliknij pozycję **Nowy klucz tajny klienta**

   ![Kliknij pozycję Nowy klucz tajny klienta.](../media/FBCimage7.png)

8. Utwórz nowy wpis tajny. W polu opisu wpisz wpis tajny, a następnie wybierz okres wygaśnięcia.

    ![Wpisz wpis tajny, a następnie wybierz okres wygaśnięcia.](../media/FBCimage8.png)

9. Skopiuj wartość wpisu tajnego i zapisz ją w pliku tekstowym lub innej lokalizacji magazynu. Jest to AAD wpis tajny aplikacji używany w kolejnych krokach.

   ![Skopiuj wartość wpisu tajnego i zapisz go.](../media/FBCimage9.png)

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Krok 2. Wdrażanie usługi internetowej łącznika z GitHub na koncie platformy Azure

1. Przejdź do [tej witryny GitHub](https://github.com/microsoft/m365-sample-connector-csharp-aspnet) i kliknij pozycję **Wdróż na platformie Azure**.

    ![Kliknij pozycję Wdróż na platformie Azure.](../media/FBCGithubApp.png)

2. Po kliknięciu **przycisku Wdróż na platformie Azure** nastąpi przekierowanie do Azure Portal przy użyciu niestandardowej strony szablonu. Wypełnij szczegóły **podstawowe** i **Ustawienia**, a następnie kliknij przycisk **Kup**.

   - **Subskrypcji:** Wybierz subskrypcję platformy Azure, w ramach którą chcesz wdrożyć usługę internetową łącznika stron biznesowych w serwisie Facebook.

   - **Grupa zasobów:** Wybierz lub utwórz nową grupę zasobów. Grupa zasobów to kontener, który przechowuje powiązane zasoby dla rozwiązania platformy Azure.

   - **Lokalizacji:** Wybierz lokalizację.

   - **Nazwa aplikacji internetowej:** Podaj unikatową nazwę aplikacji internetowej łącznika. Nazwa musi mieć długość od 3 do 18 znaków. Ta nazwa jest używana do tworzenia adresu URL usługi Azure App Service. Jeśli na przykład podasz nazwę aplikacji internetowej **fbconnector** , adres URL usługi Azure App Service zostanie **fbconnector.azurewebsites.net**.

   - **tenantId:** Identyfikator dzierżawy organizacji Microsoft 365 skopiowany po utworzeniu aplikacji łącznika Facebook w Azure Active Directory w kroku 1.

   - **Klucz APISecretKey:** Dowolną wartość można wpisać jako wpis tajny. Służy do uzyskiwania dostępu do aplikacji internetowej łącznika w kroku 5.

     ![Kliknij pozycję Utwórz zasób i wpisz konto magazynu.](../media/FBCimage12.png)

3. Po pomyślnym wdrożeniu strona będzie wyglądać podobnie do poniższego zrzutu ekranu:

   ![Kliknij Storage, a następnie kliknij pozycję Storage konto.](../media/FBCimage13.png)

## <a name="step-3-register-the-facebook-app"></a>Krok 3. Rejestrowanie aplikacji Facebook

1. Przejdź do <https://developers.facebook.com>obszaru , zaloguj się przy użyciu poświadczeń konta dla stron biznesowych facebookowej organizacji, a następnie kliknij pozycję **Dodaj nową aplikację**.

   ![Dodaj nową stronę biznesową aplikacji dla serwisu Facebook.](../media/FBCimage25.png)

2. Utwórz nowy identyfikator aplikacji.

   ![Utwórz nowy identyfikator aplikacji.](../media/FBCimage26.png)

3. W okienku nawigacji po lewej stronie kliknij pozycję **Dodaj produkty** , a następnie kliknij pozycję **Skonfiguruj** na kafelku **Facebook Login** .

   ![Kliknij pozycję Dodaj produkty.](../media/FBCimage27.png)

4. Na stronie Integrowanie logowania do serwisu Facebook kliknij pozycję **Sieć Web**.

   ![Kliknij pozycję Sieć Web na stronie Integracja logowania do serwisu Facebook.](../media/FBCimage28.png)

5. Dodaj adres URL usługi Azure App Service; na przykład `https://fbconnector.azurewebsites.net`.

   ![Dodaj adres URL usługi Azure App Service.](../media/FBCimage29.png)

6. Ukończ sekcję Szybki start konfiguracji logowania na Facebooku.

   ![Ukończ sekcję Szybki start.](../media/FBCimage30.png)

7. W okienku nawigacji po lewej stronie w obszarze **Logowanie do serwisu Facebook** kliknij pozycję **Ustawienia** i dodaj identyfikator URI przekierowania OAuth w polu **Prawidłowe identyfikatory URI przekierowania OAuth**. Użyj formatu **\<connectorserviceuri>/Views/FacebookOAuth**, gdzie wartość connectorserviceuri to adres URL usługi Azure App Service dla twojej organizacji, na przykład `https://fbconnector.azurewebsites.net`.

   ![Dodaj identyfikator URI przekierowania OAuth do pola Prawidłowe identyfikatory URI przekierowania OAuth.](../media/FBCimage31.png)

8. W okienku nawigacji po lewej stronie kliknij pozycję **Dodaj produkty** , a następnie kliknij pozycję **Elementy webhook.** W menu rozwijanym **Strona** kliknij pozycję **Strona**.

   ![Kliknij pozycję Dodaj produkty, a następnie kliknij pozycję **Elementy webhook.](../media/FBCimage32.png)

9. Dodaj adres URL wywołania zwrotnego elementów webhook i dodaj token weryfikacji. Format adresu URL wywołania zwrotnego, użyj formatu `<connectorserviceuri>/api/FbPageWebhook`, gdzie wartość connectorserviceuri to adres URL usługi Azure App Service dla organizacji, na przykład `https://fbconnector.azurewebsites.net`.

   Token weryfikacji powinien być podobny do silnego hasła. Skopiuj token weryfikacji do pliku tekstowego lub innej lokalizacji magazynu.

   ![Dodaj token weryfikacji.](../media/FBCimage33.png)

10. Testowanie i subskrybowanie punktu końcowego na potrzeby kanału informacyjnego.

    ![Testowanie i subskrybowanie punktu końcowego.](../media/FBCimage34.png)

11. Dodaj adres URL prywatności, ikonę aplikacji i użycie biznesowe. Ponadto skopiuj identyfikator aplikacji i wpis tajny aplikacji do pliku tekstowego lub innej lokalizacji magazynu.

    ![Dodaj adres URL prywatności, ikonę aplikacji i użycie biznesowe.](../media/FBCimage35.png)

12. Upublicznij aplikację.

    ![Upublicznij aplikację.](../media/FBCimage36.png)

13. Dodaj użytkownika do roli administratora lub testera.

    ![Dodaj użytkownika do roli administratora lub testera.](../media/FBCimage37.png)

14. Dodaj uprawnienie **Dostęp do zawartości publicznej strony** .

    ![dd uprawnienia dostępu do zawartości publicznej strony.](../media/FBCimage38.png)

15. Dodaj uprawnienie Zarządzaj stronami.

    ![Dodaj uprawnienie Zarządzaj stronami.](../media/FBCimage39.png)

16. Przejrzyj aplikację przez serwis Facebook.

    ![Przejrzyj aplikację przez serwis Facebook.](../media/FBCimage40.png)

## <a name="step-4-configure-the-connector-web-app"></a>Krok 4. Konfigurowanie aplikacji internetowej łącznika

1. Przejdź do strony `https://<AzureAppResourceName>.azurewebsites.net` (gdzie AzureAppResourceName to nazwa zasobu aplikacji platformy Azure nazwanego w kroku 4). Jeśli na przykład nazwa to **fbconnector**, przejdź do pozycji `https://fbconnector.azurewebsites.net`. Strona główna aplikacji będzie wyglądać podobnie do poniższego zrzutu ekranu:

   ![Przejdź do aplikacji internetowej łącznika.](../media/FBCimage41.png)

2. Kliknij pozycję **Konfiguruj** , aby wyświetlić stronę logowania.

   ![Kliknij pozycję Konfiguruj, aby wyświetlić stronę logowania.](../media/FBCimage42.png)

3. W polu Identyfikator dzierżawy wpisz lub wklej identyfikator dzierżawy (uzyskany w kroku 2). W polu hasła wpisz lub wklej klucz APISecretKey (uzyskany w kroku 2), a następnie kliknij pozycję **Ustaw konfigurację Ustawienia**, aby wyświetlić stronę szczegółów konfiguracji.

    ![Zaloguj się przy użyciu identyfikatora dzierżawy i hasła, a następnie przejdź do strony szczegółów konfiguracji.](../media/FBCimage43.png)

4. Wprowadź następujące ustawienia konfiguracji

   - **Identyfikator aplikacji Facebook:** Identyfikator aplikacji dla aplikacji facebookowej uzyskany w kroku 3.

   - **Wpis tajny aplikacji Facebook:** Wpis tajny aplikacji dla aplikacji Facebook uzyskany w kroku 3.

   - **Elementy webhook serwisu Facebook weryfikują token:** Token weryfikacji utworzony w kroku 3.

   - **AAD identyfikator aplikacji:** identyfikator aplikacji dla aplikacji Azure Active Directory utworzonej w kroku 1.

   - **AAD wpis tajny aplikacji:** wartość klucza tajnego APISecretKey utworzonego w kroku 1.

5. Kliknij **przycisk Zapisz** , aby zapisać ustawienia łącznika.

## <a name="step-5-set-up-a-facebook-connector-in-the-compliance-portal"></a>Krok 5. Konfigurowanie łącznika usługi Facebook w portalu zgodności

1. Przejdź do portalu zgodności usługi Microsoft Purview, a następnie wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a.

2. Na stronie **Łączniki danych** w obszarze **Strony biznesowe serwisu Facebook** kliknij pozycję **Wyświetl**.

3. Na stronie **Strony biznesowe w serwisie Facebook** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

5. Na stronie **Dodawanie poświadczeń dla aplikacji łącznika** wprowadź następujące informacje, a następnie kliknij pozycję **Weryfikuj połączenie**.

   ![Wprowadź poświadczenia aplikacji łącznika.](../media/TCimage38.png)

   - W polu **Nazwa** wpisz nazwę łącznika, na przykład **stronę z wiadomościami na Facebooku**.

   - W polu **Adres URL połączenia** wpisz lub wklej adres URL usługi Azure App Service; na przykład `https://fbconnector.azurewebsites.net`.

   - W polu **Hasło** wpisz lub wklej wartość klucza APISecretKey, który został dodany w kroku 2.

   - W **polu identyfikatora aplikacja systemu Azure** wpisz lub wklej wartość identyfikatora aplikacji (klienta) nazywanego również identyfikatorem aplikacji AAD utworzonym w kroku 1.

6. Po pomyślnym zweryfikowaniu połączenia kliknij przycisk **Dalej**.

7. Na stronie **Autoryzowanie Microsoft 365 importowania danych** ponownie wpisz lub wklej ciąg APISecretKey, a następnie kliknij pozycję **Zaloguj aplikację internetową**.

8. Na stronie **Konfigurowanie aplikacji łącznika Facebooka** kliknij pozycję **Zaloguj się przy użyciu serwisu Facebook** i zaloguj się przy użyciu poświadczeń konta dla stron biznesowych Facebook w organizacji. Upewnij się, że konto facebookowe, na które zalogowano się, ma przypisaną rolę administratora dla stron biznesowych Facebook w organizacji.

   ![Zaloguj się za pomocą serwisu Facebook.](../media/FBCimage50.png)

9. Zostanie wyświetlona lista stron biznesowych zarządzanych przez zalogowane konto na Facebooku. Wybierz stronę do archiwizacji, a następnie kliknij przycisk **Dalej**.

   ![Wybierz stronę biznesową organizacji, którą chcesz zarchiwizować.](../media/FBCimage52.png)

10. Kliknij przycisk **Kontynuuj** , aby zakończyć konfigurację aplikacji usługi łącznika.

11. Na stronie **Ustaw filtry** możesz zastosować filtr, aby początkowo importować elementy o określonym wieku. Wybierz wiek, a następnie kliknij przycisk **Dalej**.

12. Na stronie **Wybieranie lokalizacji magazynu** wpisz adres e-mail Microsoft 365 skrzynki pocztowej, do których zostaną zaimportowane elementy serwisu Facebook, a następnie kliknij przycisk **Dalej**.

13. Kliknij **przycisk Dalej** , aby przejrzeć ustawienia łącznika, a następnie kliknij przycisk **Zakończ** , aby ukończyć konfigurację łącznika.

14. W centrum zgodności przejdź do strony **Łączniki danych** i kliknij kartę **Łączniki** , aby zobaczyć postęp procesu importowania.
