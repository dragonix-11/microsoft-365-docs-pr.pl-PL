---
title: Wdrażanie łącznika w celu archiwizowania danych stron biznesowych serwisu Facebook
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Administratorzy mogą skonfigurować łącznik natywny w celu importowania i archiwizowania stron biznesowych serwisu Facebook w celu Microsoft 365. Po zaimportowaniu tych danych do witryny Microsoft 365 można używać funkcji zgodności, takich jak zastosowanie prawnych, wyszukiwanie zawartości i zasady przechowywania, w celu zarządzania danymi organizacji w serwisie Facebook.
ms.openlocfilehash: 0bbe7f65ef6226386911817b40bbaaa418cdabec
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990269"
---
# <a name="deploy-a-connector-to-archive-facebook-business-pages-data"></a>Wdrażanie łącznika w celu archiwizowania danych stron biznesowych serwisu Facebook

Ten artykuł zawiera szczegółowe instrukcje dotyczące wdrażania łącznika, który używa usługi importowania Office 365 w celu importowania danych ze stron biznesowych serwisu Facebook w celu Microsoft 365. Aby uzyskać ogólne omówienie tego procesu i listę wymagań wstępnych wymaganych do wdrożenia łącznika serwisu Facebook, zobacz Konfigurowanie łącznika do archiwizowania danych [serwisu Facebook](archive-facebook-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w aplikacji Azure Active Directory

1. Przejdź do <https://portal.azure.com> konta administratora globalnego i zaloguj się przy użyciu poświadczeń administratora globalnego.

    ![Tworzenie aplikacji w aplikacji AAD.](../media/FBCimage1.png)

2. W lewym okienku nawigacji kliknij pozycję **Azure Active Directory**.

    ![Kliknij Azure Active Directory.](../media/FBCimage2.png)

3. W lewym okienku nawigacji kliknij pozycję Rejestracje **aplikacji (wersja Preview),** a następnie kliknij **pozycję Nowa rejestracja**.

    ![Kliknij **Rejestracje aplikacji (wersja Preview)**, a następnie kliknij pozycję **Nowa rejestracja**.](../media/FBCimage3.png)

4. Zarejestruj aplikację. W obszarze Przekierowywanie URI wybierz pozycję Sieć Web na liście <https://portal.azure.com> rozwijanej typu aplikacji, a następnie wpisz w polu dla URI.

   ![Zarejestruj aplikację.](../media/FBCimage4.png)

5. Skopiuj identyfikator **aplikacji (klienta) i** identyfikator katalogu (dzierżawy **)** i zapisz go w pliku tekstowym lub w innej bezpiecznej lokalizacji. Te identyfikatory należy stosować w kolejnych krokach.

   ![Skopiuj identyfikator aplikacji i identyfikator katalogu i zapisz je.](../media/FBCimage5.png)

6. Przejdź do **& certyfikatów i sekretów nowej aplikacji.**

   ![Przejdź do & Certyfikatów i sekretów nowej aplikacji.](../media/FBCimage6.png)

7. Kliknij **pozycję Nowy klucz tajny klienta**

   ![Kliknij pozycję Nowy klient klucz tajny.](../media/FBCimage7.png)

8. Utwórz nową tajemnicę. W polu Opis wpisz klucz tajny, a następnie wybierz okres wygasania.

    ![Wpisz klucz tajny, a następnie wybierz okres wygasania.](../media/FBCimage8.png)

9. Skopiuj wartość tajemnicy i zapisz ją w pliku tekstowym lub innej lokalizacji przechowywania. Jest to klucz AAD tajny, z których korzystasz w kolejnych krokach.

   ![Skopiuj wartość tajemnicy i zapisz ją.](../media/FBCimage9.png)

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Krok 2. Wdrażanie usługi sieci Web łącznika z programu GitHub do konta Azure

1. Przejdź do [tej witryny GitHub i](https://github.com/microsoft/m365-sample-connector-csharp-aspnet) kliknij pozycję **Wdeksuj na platformie Azure**.

    ![Kliknij pozycję Wdeksuj na platformie Azure.](../media/FBCGithubApp.png)

2. Po kliknięciu **przycisku Wdeksuj** w usłudze Azure nastąpi przekierowanie do portalu Azure Portal z stroną szablonu niestandardowego. Wprowadź informacje podstawowe **i szczegóły** **Ustawienia** a następnie kliknij pozycję **Zakup**.

   - **Subskrypcja:** Wybierz subskrypcję platformy Azure, w której chcesz wdrożyć usługę sieci Web łącznika stron biznesowych serwisu Facebook.

   - **Grupa zasobów:** Wybierz lub utwórz nową grupę zasobów. Grupa zasobów to kontener, który zawiera pokrewne zasoby dla rozwiązania platformy Azure.

   - **Lokalizacja:** Wybierz lokalizację.

   - **Nazwa aplikacji sieci Web:** Nadaj unikatową nazwę aplikacji sieci Web łącznika. Ta nazwa musi mieć od 3 do 18 znaków. Ta nazwa służy do tworzenia adresu URL usługi aplikacji Azure; Jeśli na przykład po podajisz nazwę aplikacji internetowej **fbconnector** , adres URL usługi aplikacji Azure zostanie **fbconnector.azurewebsites.net**.

   - **tenantId:** Identyfikator dzierżawy organizacji Microsoft 365, która została skopiowana po utworzeniu aplikacji łącznika serwisu Facebook w programie Azure Active Directory kroku 1.

   - **APISecretKey:** Jako klucz tajny możesz wpisać dowolną wartość. Służy to do uzyskiwania dostępu do aplikacji sieci Web łącznika w kroku 5.

     ![Kliknij pozycję Utwórz zasób i wpisz konto magazynu.](../media/FBCimage12.png)

3. Po pomyślnym wdrożeniu strona będzie wyglądać podobnie do poniższego zrzutu ekranu:

   ![Kliknij Storage, a następnie kliknij pozycję Storage konto.](../media/FBCimage13.png)

## <a name="step-3-register-the-facebook-app"></a>Krok 3. Rejestrowanie aplikacji Facebook

1. Przejdź do <https://developers.facebook.com>usługi , zaloguj się przy użyciu poświadczeń konta na stronach biznesowych organizacji w serwisie Facebook, a następnie kliknij pozycję **Dodaj nową aplikację**.

   ![Dodaj nową aplikację dla firm w serwisie Facebook.](../media/FBCimage25.png)

2. Utwórz nowy identyfikator aplikacji.

   ![Utwórz nowy identyfikator aplikacji.](../media/FBCimage26.png)

3. W lewym okienku nawigacji kliknij pozycję **Dodaj produkty** , a następnie kliknij pozycję **Skonfiguruj na** kafelku **Logowanie do serwisu Facebook** .

   ![Kliknij pozycję Dodaj produkty.](../media/FBCimage27.png)

4. Na stronie Logowania do serwisu Facebook integracja kliknij pozycję **Sieć Web**.

   ![Kliknij pozycję Sieć Web na stronie Logowania do serwisu Facebook Integruj.](../media/FBCimage28.png)

5. Dodaj adres URL usługi aplikacji Azure; na przykład `https://fbconnector.azurewebsites.net`.

   ![Dodaj adres URL usługi aplikacji Azure.](../media/FBCimage29.png)

6. Wykonaj sekcję Szybki start w konfiguracji logowania do serwisu Facebook.

   ![Ukończ sekcję Szybki start.](../media/FBCimage30.png)

7. W lewym okienku nawigacji w obszarze Logowanie do serwisu **Facebook** kliknij pozycję **Ustawienia** i dodaj identyfikator URI przekierowywania protokołu OAuth w polu Prawidłowe identyfikatory URI przekierowywania protokołu **OAuth**. Użyj formatu **\<connectorserviceuri>/Views/FacebookOAuth**, gdzie wartością dla connectorserviceuri jest adres URL usługi aplikacji Azure dla organizacji, na przykład `https://fbconnector.azurewebsites.net`.

   ![Dodaj adres URI przekierowania protokołu OAuth do pola Prawidłowe URI przekierowywania protokołu OAuth.](../media/FBCimage31.png)

8. W lewym okienku nawigacji kliknij pozycję **Dodaj produkty** , a następnie kliknij pozycję **Webhoox.** W menu **rozwijanego** Strona kliknij pozycję **Strona**.

   ![Kliknij pozycję Dodaj produkty, a następnie kliknij pozycję **Webhoox.](../media/FBCimage32.png)

9. Dodaj adres URL callback usługi Webhokuj i dodaj token weryfikacji. Format adresu URL funkcji callback, użyj formatu `<connectorserviceuri>/api/FbPageWebhook`, gdzie wartością dla connectorserviceuri jest adres URL usługi aplikacji Azure dla Organizacji, na przykład `https://fbconnector.azurewebsites.net`.

   Token weryfikacji powinien przypominać silne hasło. Skopiuj token weryfikacji do pliku tekstowego lub innej lokalizacji przechowywania.

   ![Dodaj token weryfikacji.](../media/FBCimage33.png)

10. Testowanie i subskrybowanie punktu końcowego kanału informacyjnego.

    ![Testowanie i subskrybowanie punktu końcowego.](../media/FBCimage34.png)

11. Dodaj adres URL prywatności, ikonę aplikacji i użytku biznesowego. Ponadto skopiuj identyfikator aplikacji i aplikację klucz tajny do pliku tekstowego lub innej lokalizacji przechowywania.

    ![Dodaj adres URL prywatności, ikonę aplikacji i użytku biznesowego.](../media/FBCimage35.png)

12. Udostępnij aplikację publicznie.

    ![Udostępnij aplikację publicznie.](../media/FBCimage36.png)

13. Dodaj użytkownika do roli administratora lub testera.

    ![Dodaj użytkownika do roli administratora lub testera.](../media/FBCimage37.png)

14. Dodaj uprawnienie **Dostęp do zawartości publicznej** strony.

    ![dd uprawnienia Dostęp do zawartości publicznej strony.](../media/FBCimage38.png)

15. Dodaj uprawnienie Zarządzanie stronami.

    ![Dodaj uprawnienie Zarządzanie stronami.](../media/FBCimage39.png)

16. Pobierz aplikację przeglądaną przez serwis Facebook.

    ![Pobierz aplikację przeglądaną przez serwis Facebook.](../media/FBCimage40.png)

## <a name="step-4-configure-the-connector-web-app"></a>Krok 4. Konfigurowanie aplikacji sieci Web Łącznik

1. Przejdź do `https://<AzureAppResourceName>.azurewebsites.net` (gdzie nazwa zasobu aplikacji platformy Azure, o nazwie AzureAppResourceName) jest nazwą Twojego zasobu aplikacji platformy Azure, o nazwie Krok 4. Jeśli na przykład nazwa to **fbconnector**, przejdź do `https://fbconnector.azurewebsites.net`. Strona główna aplikacji będzie wyglądać jak na poniższym zrzucie ekranu:

   ![Przejdź do aplikacji sieci Web Łącznik.](../media/FBCimage41.png)

2. Kliknij **pozycję** Konfiguruj, aby wyświetlić stronę logowania.

   ![Kliknij pozycję Konfiguruj, aby wyświetlić stronę logowania.](../media/FBCimage42.png)

3. W polu Identyfikator dzierżawy wpisz lub wklej identyfikator dzierżawy (uzyskany w kroku 2). W polu hasła wpisz lub wklej kod APISecretKey (uzyskany w kroku 2), a następnie kliknij pozycję Ustaw konfigurację **Ustawienia**, aby wyświetlić stronę szczegółów konfiguracji.

    ![Zaloguj się przy użyciu identyfikatora dzierżawy i hasła, a następnie przejdź do strony szczegółów konfiguracji.](../media/FBCimage43.png)

4. Wprowadź następujące ustawienia konfiguracji

   - **Identyfikator aplikacji serwisu Facebook:** Identyfikator aplikacji dla aplikacji serwisu Facebook uzyskany w kroku 3.

   - **Tajny program serwisu Facebook:** Aplikacja tajna dla aplikacji serwisu Facebook uzyskanej w kroku 3.

   - **Token weryfikacji w sieci Web serwisu Facebook:** Token weryfikacji utworzony w kroku 3.

   - **AAD aplikacji:** Identyfikator aplikacji dla aplikacji Azure Active Directory utworzonej w kroku 1.

   - **AAD klucza tajnego aplikacji:** Wartość klucza tajnego interfejsu APISecretKey utworzonego w kroku 1.

5. Kliknij **przycisk Zapisz** , aby zapisać ustawienia łącznika.

## <a name="step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center"></a>Krok 5. Konfigurowanie łącznika serwisu Facebook w Centrum zgodności platformy Microsoft 365

1. Przejdź do Centrum zgodności platformy Microsoft 365, a następnie wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki**</a.

2. Na stronie **Łączniki danych** w obszarze **Strony biznesowe w** serwisie Facebook kliknij pozycję **Widok**.

3. Na stronie **firmy w serwisie Facebook** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

5. Na **stronie Dodawanie poświadczeń dla aplikacji łącznika** wprowadź następujące informacje, a następnie kliknij pozycję **Sprawdź poprawność połączenia**.

   ![Wprowadź poświadczenia aplikacji łącznika.](../media/TCimage38.png)

   - W **polu Nazwa** wpisz nazwę łącznika, na przykład stronę wiadomości w **serwisie Facebook**.

   - W polu **Adres URL połączenia** wpisz lub wklej adres URL usługi aplikacji Azure; na przykład `https://fbconnector.azurewebsites.net`.

   - W **polu Hasło** wpisz lub wklej wartość klucza APISecretKey dodaną w kroku 2.

   - W polu **Identyfikator aplikacji Azure** wpisz lub wklej wartość identyfikatora aplikacji (klienta) nazywanego również AAD identyfikatorem aplikacji utworzonym w kroku 1.

6. Po pomyślnym weryfikacji połączenia kliknij przycisk **Dalej**.

7. Na stronie **Authorize Microsoft 365 to import data** (Autoryzowanie Microsoft 365 importowania danych) ponownie wpisz lub wklej kod APISecretKey, a następnie kliknij pozycję **Zaloguj się w aplikacji sieci Web**.

8. Na stronie **Konfigurowanie aplikacji łącznika serwisu Facebook** kliknij pozycję Zaloguj się przy użyciu serwisu **Facebook** i zaloguj się przy użyciu poświadczeń konta na stronach biznesowych organizacji w serwisie Facebook. Upewnij się, że do konta w serwisie Facebook, do którego się zalogowano, przypisano rolę administratora dla stron biznesowych organizacji w serwisie Facebook.

   ![Zaloguj się przy użyciu serwisu Facebook.](../media/FBCimage50.png)

9. Zostanie wyświetlona lista stron biznesowych zarządzanych przez konto w serwisie Facebook, do którego zalogowano się. Wybierz stronę do zarchiwizować, a następnie kliknij przycisk **Dalej**.

   ![Wybierz stronę biznesową organizacji, którą chcesz zarchiwizować.](../media/FBCimage52.png)

10. Kliknij **przycisk Kontynuuj** , aby zakończyć konfigurowanie aplikacji usługi łącznika.

11. Na stronie **Ustawianie filtrów** możesz zastosować filtr, aby początkowo zaimportować elementy, które mają określony wiek. Wybierz wiek, a następnie kliknij przycisk **Dalej**.

12. Na stronie **Wybierz lokalizację przechowywania** wpisz adres e-mail skrzynki Microsoft 365, do których będą importowane elementy z serwisu Facebook, a następnie kliknij przycisk **Dalej**.

13. Kliknij **przycisk Dalej** , aby przejrzeć ustawienia łącznika, a następnie kliknij przycisk **Zakończ,** aby zakończyć konfigurację łącznika.

14. W centrum zgodności przejdź do strony **Łączniki** danych i kliknij kartę Łączniki, aby wyświetlić postęp procesu importowania.
