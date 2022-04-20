---
title: Wdrażanie łącznika do archiwizacji danych usługi Twitter
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
description: Administratorzy mogą skonfigurować łącznik natywny do importowania i archiwizowania danych usługi Twitter w celu Microsoft 365. Po zaimportowaniu tych danych do Microsoft 365 możesz użyć funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania, aby zarządzać zarządzaniem danymi w usłudze Twitter organizacji.
ms.openlocfilehash: e1ae371d59ef21955612c89b9e0bffc5c24d5950
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64950208"
---
# <a name="deploy-a-connector-to-archive-twitter-data"></a>Wdrażanie łącznika do archiwizacji danych usługi Twitter

Ten artykuł zawiera krok po kroku proces wdrażania łącznika, który używa usługi Office 365 Import do importowania danych z konta twitterowego organizacji do Microsoft 365. Aby zapoznać się z ogólnym omówieniem tego procesu i listą wymagań wstępnych wymaganych do wdrożenia łącznika usługi Twitter, zobacz [Konfigurowanie łącznika w celu archiwizowania danych usługi Twitter ](archive-twitter-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w Azure Active Directory

1. Przejdź do strony <https://portal.azure.com> i zaloguj się przy użyciu poświadczeń konta administratora globalnego.

   ![Zaloguj się do platformy Azure.](../media/TCimage01.png)

2. W okienku nawigacji po lewej stronie kliknij pozycję **Azure Active Directory**.

   ![Przejdź do Azure Active Directory.](../media/TCimage02.png)

3. W okienku nawigacji po lewej stronie kliknij pozycję **Rejestracje aplikacji (wersja zapoznawcza),** a następnie kliknij pozycję **Nowa rejestracja**.

   ![Utwórz nową rejestrację aplikacji.](../media/TCimage03.png)

4. Zarejestruj aplikację. W obszarze **Identyfikator URI przekierowania (opcjonalnie)** wybierz pozycję **Sieć Web** na liście rozwijanej Typ aplikacji, a następnie wpisz `https://portal.azure.com` w polu identyfikator URI.

   ![Wpisz https://portal.azure.com identyfikator URI przekierowania.](../media/TCimage04.png)

5. Skopiuj **identyfikator aplikacji (klienta)** i **identyfikator katalogu (dzierżawy)** i zapisz je w pliku tekstowym lub innej bezpiecznej lokalizacji. Te identyfikatory są używane w kolejnych krokach.

    ![Skopiuj i zapisz identyfikator aplikacji i identyfikator katalogu.](../media/TCimage05.png)

6. Przejdź do pozycji **Certyfikaty & wpisów tajnych dla nowej aplikacji** i w obszarze **Klucze tajne klienta** kliknij pozycję **Nowy wpis tajny klienta**.

   ![Utwórz nowy klucz tajny klienta.](../media/TCimage06.png)

7. Utwórz nowy wpis tajny. W polu opisu wpisz wpis tajny, a następnie wybierz okres wygaśnięcia.

   ![Wpisz wpis tajny i wybierz okres wygaśnięcia.](../media/TCimage08.png)

8. Skopiuj wartość wpisu tajnego i zapisz ją w pliku tekstowym lub innej lokalizacji magazynu. Jest to AAD wpis tajny aplikacji używany w kolejnych krokach.

   ![Skopiuj i zapisz wpis tajny.](../media/TCimage09.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Krok 2. Wdrażanie usługi internetowej łącznika z GitHub na koncie platformy Azure

1. Przejdź do [tej witryny GitHub](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet) i kliknij pozycję **Wdróż na platformie Azure**.

    ![Przejdź do strony głównej platformy Azure.](../media/FBCimage11.png)

2. Po kliknięciu **przycisku Wdróż na platformie Azure** nastąpi przekierowanie do Azure Portal przy użyciu niestandardowej strony szablonu. Wypełnij szczegóły **podstawowe** i **Ustawienia**, a następnie kliknij przycisk **Kup**.

   ![Kliknij pozycję Utwórz zasób i wpisz konto magazynu.](../media/FBCimage12.png)

    - **Subskrypcji:** Wybierz subskrypcję platformy Azure, w ramach którą chcesz wdrożyć usługę internetową łącznika usługi Twitter.

    - **Grupa zasobów:** Wybierz lub utwórz nową grupę zasobów. Grupa zasobów to kontener, który przechowuje powiązane zasoby dla rozwiązania platformy Azure.

    - **Lokalizacji:** Wybierz lokalizację.

    - **Nazwa aplikacji internetowej:** Podaj unikatową nazwę aplikacji internetowej łącznika. Nazwa musi mieć długość od 3 do 18 znaków. Ta nazwa jest używana do tworzenia adresu URL usługi Azure App Service. Jeśli na przykład podasz nazwę aplikacji internetowej **twitterconnector** , adres URL usługi Azure App Service zostanie **twitterconnector.azurewebsites.net**.

    - **tenantId:** Identyfikator dzierżawy organizacji Microsoft 365 skopiowany po utworzeniu aplikacji łącznika Facebook w usłudze Azure Active Directory w kroku 1.

   - **Klucz APISecretKey:** Dowolną wartość można wpisać jako wpis tajny. Służy do uzyskiwania dostępu do aplikacji internetowej łącznika w kroku 5.

3. Po pomyślnym wdrożeniu strona będzie wyglądać podobnie do poniższego zrzutu ekranu:

    ![Kliknij Storage, a następnie kliknij pozycję Storage konto.](../media/FBCimage13.png)

## <a name="step-3-create-the-twitter-app"></a>Krok 3. Tworzenie aplikacji twitterowej

1. Przejdź do https://developer.twitter.compozycji , zaloguj się przy użyciu poświadczeń dla konta dewelopera w organizacji, a następnie kliknij pozycję **Aplikacje**.

   ![Przejdź do obszaru https://developer.twitter.com i zaloguj się.](../media/TCimage25-5.png)
2. Kliknij **pozycję Utwórz aplikację**.

   ![Przejdź do strony Aplikacje, aby utworzyć aplikację.](../media/TCimage26.png)

3. W obszarze **Szczegóły aplikacji** dodaj informacje o aplikacji.

   ![Wprowadź informacje o aplikacji.](../media/TCimage27.png)

4. Na pulpicie nawigacyjnym dewelopera usługi Twitter wybierz właśnie utworzoną aplikację, a następnie kliknij pozycję **Szczegóły**.

   ![Skopiuj i zapisz identyfikator aplikacji.](../media/TCimage28.png)

5. Na **karcie Klucze i tokeny** w obszarze **Klucze interfejsu API konsumenta** skopiuj klucz interfejsu API i klucz tajny interfejsu API i zapisz je w pliku tekstowym lub innej lokalizacji magazynu. Następnie kliknij pozycję **Utwórz** , aby wygenerować token dostępu i wpis tajny tokenu dostępu, a następnie skopiuj je do pliku tekstowego lub innej lokalizacji magazynu.

   ![Skopiuj i zapisz w kluczu tajnym interfejsu API.](../media/TCimage29.png)

   Następnie kliknij przycisk **Utwórz** , aby wygenerować token dostępu i wpis tajny tokenu dostępu, a następnie skopiuj je do pliku tekstowego lub innej lokalizacji magazynu.

6. Kliknij kartę **Uprawnienia** i skonfiguruj uprawnienia, jak pokazano na poniższym zrzucie ekranu:

   ![Konfigurowanie uprawnień.](../media/TCimage30.png)

7. Po zapisaniu ustawień uprawnień kliknij kartę **Szczegóły aplikacji** , a następnie kliknij pozycję **Edytuj > Edytuj szczegóły**.

   ![Edytuj szczegóły aplikacji.](../media/TCimage31.png)

8. Wykonaj następujące zadania:

   - Zaznacz pole wyboru, aby zezwolić aplikacji łącznika na logowanie się do usługi Twitter.

   - Dodaj identyfikator Uri przekierowania OAuth w następującym formacie: **\<connectorserviceuri>/Views/TwitterOAuth**, gdzie wartość *connectorserviceuri* to adres URL usługi Azure App Service dla twojej organizacji, na przykład https://twitterconnector.azurewebsites.net/Views/TwitterOAuth.

    ![Zezwalaj aplikacji łącznika na logowanie się do usługi Twitter i dodawanie identyfikatora URI przekierowania OAuth.](../media/TCimage32.png)

Aplikacja dewelopera usługi Twitter jest teraz gotowa do użycia.

## <a name="step-4-configure-the-connector-web-app"></a>Krok 4. Konfigurowanie aplikacji internetowej łącznika

1. Przejdź do https://\<AzureAppResourceName>.azurewebsites.net (gdzie **AzureAppResourceName** to nazwa zasobu aplikacji platformy Azure nazwanego w kroku 4). Jeśli na przykład nazwa to **twitterconnector**, przejdź do pozycji https://twitterconnector.azurewebsites.net. Strona główna aplikacji wygląda podobnie do poniższego zrzutu ekranu:

   ![Przejdź do strony zasobów aplikacji platformy Azure.](../media/FBCimage41.png)

2. Kliknij pozycję **Konfiguruj** , aby wyświetlić stronę logowania.

   ![Kliknij pozycję Konfiguruj, aby wyświetlić stronę logowania.](../media/FBCimage42.png)

3. W polu Identyfikator dzierżawy wpisz lub wklej identyfikator dzierżawy (uzyskany w kroku 2). W polu hasła wpisz lub wklej klucz APISecretKey (uzyskany w kroku 2), a następnie kliknij pozycję **Ustaw konfigurację Ustawienia**, aby wyświetlić stronę szczegółów konfiguracji.

   ![Zaloguj się przy użyciu identyfikatora dzierżawy i klucza tajnego interfejsu API.](../media/TCimage35.png)

4. Wprowadź następujące ustawienia konfiguracji

   - **Klucz interfejsu API usługi Twitter:** Klucz interfejsu API dla aplikacji twitterowej utworzonej w kroku 3.

   - **Klucz tajny interfejsu API usługi Twitter:** Klucz tajny interfejsu API dla aplikacji twitterowej utworzonej w kroku 3.

   - **Token dostępu do usługi Twitter:** Token dostępu utworzony w kroku 3.

   - **Wpis tajny tokenu dostępu usługi Twitter:** Wpis tajny tokenu dostępu utworzony w kroku 3.

   - **AAD identyfikator aplikacji:** identyfikator aplikacji dla aplikacji Azure Active Directory utworzonej w kroku 1

   - **AAD wpis tajny aplikacji:** wartość klucza tajnego APISecretKey utworzonego w kroku 1.

5. Kliknij **przycisk Zapisz** , aby zapisać ustawienia łącznika.

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>Krok 5. Konfigurowanie łącznika usługi Twitter w portalu zgodności

1. Przejdź do portalu zgodności usługi Microsoft Purview i wybierz stronę <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a.

2. Na stronie **Łączniki danych** w obszarze **Twitter** kliknij pozycję **Wyświetl**.

3. Na stronie **Twitter** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

5. Na stronie **Dodawanie poświadczeń dla aplikacji łącznika** wprowadź następujące informacje, a następnie kliknij pozycję **Weryfikuj połączenie**.

   ![Wprowadź poświadczenia aplikacji łącznika.](../media/TCimage38.png)

    - W polu **Nazwa** wpisz nazwę łącznika, taką jak **obsługa pomocy usługi Twitter**.

    - W polu **Adres URL łącznika** wpisz lub wklej adres URL usługi Azure App Service; na przykład `https://twitterconnector.azurewebsites.net`.

    - W polu **Hasło** wpisz lub wklej wartość klucza APISecretKey utworzonego w kroku 2.

    - W **polu identyfikatora aplikacja systemu Azure** wpisz lub wklej wartość identyfikatora aplikacji aplikacja systemu Azure (nazywanego również *identyfikatorem klienta*) uzyskanym w kroku 1.

6. Po pomyślnym zweryfikowaniu połączenia kliknij przycisk **Dalej**.

7. Na stronie **Autoryzowanie Microsoft 365 importowania danych** ponownie wpisz lub wklej ciąg APISecretKey, a następnie kliknij pozycję **Zaloguj aplikację internetową**.

8. Kliknij **pozycję Zaloguj się za pomocą usługi Twitter**.

9. Na stronie logowania w serwisie Twitter zaloguj się przy użyciu poświadczeń konta twitterowego organizacji.

   ![Zaloguj się do konta w serwisie Twitter.](../media/TCimage42.png)

   Po zalogowaniu na stronie twitterowej zostanie wyświetlony następujący komunikat "Pomyślnie skonfigurowano zadanie łącznika usługi Twitter".

10. Kliknij przycisk **Kontynuuj** , aby zakończyć konfigurowanie łącznika usługi Twitter.

11. Na stronie **Ustaw filtry** możesz zastosować filtr, aby początkowo importować elementy o określonym wieku. Wybierz wiek, a następnie kliknij przycisk **Dalej**.

12. Na stronie **Wybieranie lokalizacji magazynu** wpisz adres e-mail Microsoft 365 skrzynki pocztowej, do których zostaną zaimportowane elementy usługi Twitter, a następnie kliknij przycisk **Dalej**.

13. Kliknij **przycisk Dalej** , aby przejrzeć ustawienia łącznika, a następnie kliknij przycisk **Zakończ** , aby ukończyć konfigurację łącznika.

14. W centrum zgodności przejdź do strony **Łączniki danych** i kliknij kartę **Łączniki** , aby zobaczyć postęp procesu importowania.
