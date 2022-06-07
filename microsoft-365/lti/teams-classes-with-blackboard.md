---
title: Korzystanie z zajęć w aplikacji Microsoft Teams z aplikacją Blackboard Learn Ultra
ms.author: danismith
author: cichur
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Korzystanie z zajęć w aplikacji Microsoft Teams z aplikacją Blackboard Learn Ultra
ms.openlocfilehash: f5e53c54db893a184a5b2afe86b61c823b62f5a6
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923067"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>Korzystanie z zajęć w aplikacji Microsoft Teams z aplikacją Blackboard Learn Ultra

Praca zespołowa jest podstawą każdej nowoczesnej organizacji. Wspieranie współpracy jest charakterystyczną cechą każdej udanej instytucji. Możesz rozszerzyć wszystkie możliwości i funkcje aplikacji Blackboard Learn Ultra, łącząc je z klasami usługi Microsoft Teams.

Klasy mogą obejmować konwersacje w czasie rzeczywistym, spotkania wideo lub interakcje asynchroniczne. Możesz dodać środowiska udostępniania plików i współtworzenia dla uczniów w jednym miejscu. Klasy w usłudze Microsoft Teams z aplikacją Learn Ultra na nowo definiują dynamikę nauczania i to, co oznacza efektywne uczenie się.

> [!IMPORTANT]
> Upewnij się, że pomyślnie skonfigurowano pole Poczta e-mail instytucji w [systemie informacji o uczniach (SIS)](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning)
>
>Integracja klas usługi Microsoft Teams opiera się na polu poczty e-mail instytucji w usłudze SIS, aby zamapować na poprawną [nazwę zasady użytkownika (UPN](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes)) usługi Microsoft Azure Active Directory (AAD). Jeśli nie zainicjowano obsługi poczty e-mail instytucji, domyślnie będzie to istniejąca wiadomość e-mail. Zaleca się ustawienie tego pola dla każdego użytkownika, aby upewnić się, że jego dane są poprawnie zsynchronizowane i że nie ma konfliktu danych poczty e-mail między usługami AAD i Blackboard Learn Ultra.
>
> Jeśli to pole nie zostało odpowiednio ustawione w mapowaniu SIS, integracja będzie nadal działać, ale użytkownicy mogą nie pojawiać się w utworzonych klasach usługi Teams i mogą wystąpić błędy.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>Obsługa mapowania danych instytucjonalnych — pole SIS poczty e-mail instytucji

W ramach ewolucji integracji dostawców usług w chmurze firma Blackboard Learn Ultra utworzyła nowe pole **Poczty e-mail** instytucji zarówno w ramach integracji z platformą Student Information System Framework, jak i w publicznych interfejsach API REST, dzięki czemu instytucje mogą efektywnie zarządzać procesem synchronizacji danych między aplikacjami Blackboard Learn Ultra i AAD.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>Co oznacza wiadomość e-mail instytucji i co obsługuje?

Pole **Poczta e-mail instytucji** umożliwia mapowanie niestandardowych pól między zewnętrznymi źródłami danych klienta i aplikacją Blackboard Learn Ultra. Jeśli źródła danych są dostawcami usług w chmurze, takimi jak Firma Microsoft, nazwa zasady użytkownika (UPN) jest podstawowym unikatowym identyfikatorem dla każdego użytkownika składającym się z prefiksu nazwy UPN (nazwy konta użytkownika) i sufiksu NAZWY UPN (nazwy domeny DNS) połączonego z symbolem @. Spowoduje to utworzenie unikatowego adresu e-mail dla każdego określonego użytkownika w usłudze Microsoft Azure Active Directory.

Aby upewnić się, że dane są dokładne, a rejestracje lub członkostwa między klasami Blackboard Learn Ultra i Microsoft Teams są prawidłowo osiągane, adres e-mail użytkownika musi być zgodny z obydwoma systemami. W usłudze Blackboard Learn Ultra użytkownicy mogą zmienić lub zastąpić swój istniejący adres e-mail w interfejsie użytkownika, co może spowodować wystąpienie błędów synchronizacji, a użytkownik nie zostanie poprawnie dodany do zespołu klas. Mapowanie pola **Poczta e-mail instytucji** zapewnia prawidłowe zarządzanie tym poziomem zabezpieczeń i sprawdzania poprawności, niezależnie od tego, czy użytkownicy zmienili pocztę e-mail w usłudze Blackboard Learn Ultra, czy też nie.

 Jeśli dwa adresy e-mail są różne, albo:

- Należy podjąć decyzję o tym, które źródło ma pierwszeństwo i które zostanie podjęte jako wiadomości e-mail osoby i instytucji.
  Lub
- Instytucja może ustawić mapowanie pól niestandardowych w wiadomości e-mail instytucji, co może rozwiązać potencjalny konflikt.

Mapowanie pól **Poczty e-mail instytucji** jest teraz dostępne dla wszystkich istniejących typów integracji usługi SIS w **temacie Advanced Configuration Settings****Users Learn Object Type****Field Mapping (Mapowanie pól** typu  >  obiektu dla użytkowników zaawansowanych ustawień  >  konfiguracji).

> [!NOTE]
> Należy pamiętać, że domyślnie adres **e-mail instytucji** jest ustawiony na **adres e-mail osoby** dla wszystkich formatów SIS i musi być unikatowy dla każdej osoby. Wszystkie istniejące integracje, które są skonfigurowane i uruchomione, będą miały to mapowanie danych, ponieważ usługa SIS nie będzie importować użytkowników, jeśli ich adres e-mail zostanie zduplikowany. Jeśli instytucja wymaga możliwości zmiany poczty e-mail instytucji na **niestandardową**, będzie musiała zarządzać nią za pośrednictwem **ustawień konfiguracji zaawansowanej** w usłudze SIS.

## <a name="requirements"></a>Wymagania

Integracja klas usługi Microsoft Teams jest dostępna **tylko dla kursów Ultra Course View**. Twoja instytucja musi spełnić następujące wymagania, aby z niej korzystać:

- Włącz funkcję Blackboard Learn Ultra Learn SaaS z włączoną nawigacją ultra base

  ![przykładowa funkcja jest włączona na kursach.](media/feature-availability.png)

- Włącz lti do użycia w kursach.

  a. Przejdź do **panelu administratorów** > **Dostawcy narzędzi LTI zarządzają właściwościami globalnymi** > .

  b. Wybierz pozycję **LTI Włączone w kursach** i opcjonalnie wybierz pozycję **Włączone w organizacjach**.

  c. Wybierz pozycję **Prześlij**.

- Musi mieć skonfigurowany interfejs LTI

- Dodawanie integracji LTI klasy Blackboard Learn Ultra Teams

- Dodawanie narzędzia LTI 1.3 klasy usługi Microsoft Teams

- Dodawanie narzędzia interfejsu API REST i udostępniania zasobów między źródłami

- Konfigurowanie i zatwierdzanie integracji klas usługi Microsoft Teams

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>Dodawanie narzędzia Blackboard Learn Ultra Teams Classes LTI 1.3

1. W **panelu administratora** wybierz pozycję **Dostawcy narzędzi LTI**.

2. Wybierz **pozycję Zarejestruj narzędzie LTI 1.3**.

3. W polu **Identyfikator klienta** wpisz lub skopiuj i wklej ten identyfikator:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Przejrzyj wszystkie ustawienia, które zostały wstępnie wypełnione i w **obszarze Stan narzędzia**, a następnie wybierz pozycję **Włączone**.

5. W **obszarze Zasady instytucji** wybierz pozycję **Rola w kursie, nazwie** i **adresie e-mail**, a następnie wybierz pozycję **Tak** dla obu.

6. Wybierz pozycję **Zezwalaj na dostęp do usługi klasy** i **Zezwalaj na dostęp do usługi członkostwa**.

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>Dodawanie narzędzia Klasy usługi Microsoft Teams LTI 1.3

1. W **panelu administratora** wybierz pozycję **Dostawcy narzędzi LTI**.

2. Wybierz **pozycję Zarejestruj narzędzie LTI 1.3**.

3. W polu **Identyfikator klienta** wpisz lub skopiuj i wklej ten identyfikator:

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. Przejrzyj wszystkie ustawienia, które zostały wstępnie wypełnione, w obszarze *Stan narzędzia* i wybierz pozycję *Włączone.*

5. W **obszarze Zasady instytucji** wybierz pozycję **Rola w kursie, nazwie** i **adresie e-mail**. Wybierz pozycję **Tak** dla obu tych opcji.

6. Wybierz pozycję **Zezwalaj na dostęp do usługi klasy** i **Zezwalaj na dostęp do usługi członkostwa**.

## <a name="add-the-rest-api-tool"></a>Dodawanie narzędzia interfejsu API REST

1. W **panelu administratora** przejdź do pozycji **Integracje** i wybierz pozycję **Integracje interfejsu API rest**.

2. Wybierz pozycję **Utwórz integrację**.

3. W polu **Identyfikator aplikacji** wpisz lub skopiuj i wklej ten identyfikator:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Wpisz użytkownika na potrzeby tej integracji.

   Ten użytkownik będzie miał dostęp do macierzystego interfejsu API, z którym jest skojarzona aplikacja.

5. Wybierz pozycję **Prześlij**.

## <a name="add-the-cross-origin-resource-sharing"></a>Dodawanie udostępniania zasobów między źródłami

1. W **panelu Administrator** przejdź do pozycji **Integracje** i wybierz pozycję **Udostępnianie zasobów między źródłami*.

2. Wybierz pozycję **Utwórz konfigurację**.

3. W polu **Źródło** wpisz kopię i wklej ten adres URL:

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. W polu **Dozwolone nagłówki** wpisz **Autoryzacja**.

5. Ustaw **opcję Dostępne** na **Wartość Tak**.

6. Wybierz pozycję **Prześlij**.

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>Konfigurowanie i zatwierdzanie integracji klas usługi Microsoft Teams

Aby pomyślnie zintegrować wystąpienie aplikacji Blackboard Learn Ultra z klasami usługi Microsoft Teams, należy upewnić się, że aplikacja Blackboard Learn Ultra została zatwierdzona do uzyskania dostępu w ramach dzierżawy platformy Microsoft Azure. Jest to proces, który musi zostać ukończony przez administratora globalnego platformy Microsoft 365 twojej instytucji.

Ten proces można wykonać przed lub po skonfigurowaniu aplikacji LTI w wystąpieniu blackboard Learn Ultra.

### <a name="before-configuring-the-lti-applications"></a>Przed skonfigurowaniem aplikacji LTI

Jeśli zdecydujesz się zatwierdzić aplikację Azure Blackboard Learn Ultra Teams Classes przed skonfigurowaniem integracji LTI, musisz przekierować ją do **punktu końcowego zgody administratora platformy tożsamości firmy Microsoft**. Zostanie wyświetlony adres URL:

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> Zastąpisz element **{Tenant}** określonym identyfikatorem dzierżawy platformy Microsoft Azure.

Zostanie wyświetlone okno uprawnień, w którym wyjaśniono, że udzielasz uprawnień do aplikacji Blackboard Learn Ultra w celu uzyskania dostępu do usługi Microsoft Teams.

![okno uprawnień dla firm Microsoft i Blackboard.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>Po skonfigurowaniu aplikacji LTI

1. W **panelu administratora** przejdź do pozycji **Narzędzia i narzędzia** , a następnie wybierz pozycję **Administrator integracji usługi Microsoft Teams**.

2. Wybierz pozycję **Włącz usługę Microsoft Teams**.

3. Dodaj identyfikator **dzierżawy firmy Microsoft** do dostępnego pola tekstowego.

4. Wybierz jedną z następujących opcji:

   - Jeśli aplikacja ma zgodę wstępną, zostanie wyświetlony mały znacznik wyboru. Jeśli zostanie wyświetlony znacznik wyboru, wybierz pozycję **Prześlij**.

   - Jeśli zgoda nie została zatwierdzona, wykonaj opisane kroki, aby wygenerować adres URL w celu uzyskania zgody i wysłać go do administratora globalnego platformy Microsoft 365 w celu zatwierdzenia.

5. Po potwierdzeniu zatwierdzenia wybierz pozycję **Ponów próbę** potwierdzenia, a następnie wybierz pozycję **Prześlij**.
