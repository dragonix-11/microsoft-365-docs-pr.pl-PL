---
title: Używanie Microsoft Teams za pomocą blackboard Learn Ultra
ms.author: v-cichur
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
description: Używanie Microsoft Teams za pomocą blackboard Learn Ultra
ms.openlocfilehash: 2cf6c3f3e7c9c8b0004ea08fccdec981c032a491
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990272"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>Używanie Microsoft Teams za pomocą blackboard Learn Ultra

Praca zespołowa to podstawa każdej nowoczesnej organizacji. Przez rozwijanie współpracy jest to definiujące cechy każdej udanej instytucji. Wszystkie funkcje i możliwości aplikacji Blackboard Learn Ultra można ulepszyć, sparując je Microsoft Teams zajęciami.

Zajęcia mogą obejmować konwersacje w czasie rzeczywistym, spotkania wideo lub asynchroniczne interakcje. Możesz dodać do uczniów udostępnianie plików i współtworzenie ich wszystkich w jednym miejscu. Microsoft Teams tych zajęć za pomocą nauki Ultra ponownie zdefiniuj dynamiki nauczania i co oznacza skuteczna nauka.

> [!IMPORTANT]
> Upewnij się, że pole Poczty e-mail instytucji zostało pomyślnie ustawione w systemie [informacji o uczniach (SIS, Student Information System)](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning)
>
>Integracja Microsoft Teams klas korzysta z pola poczty e-mail instytucji w sis do mapowania na właściwą Microsoft Azure Active Directory (AAD) użytkownika ([UPN](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes)). Jeśli nie inicjowanie obsługi poczty e-mail w instytucji nie zostało jeszcze włączone, domyślnie będzie to oznaczać istniejące wiadomości e-mail. Zalecane jest ustawienie tego pola dla każdego użytkownika w celu zapewnienia poprawnej synchronizacji danych oraz tego, że nie występuje konflikt danych poczty e-mail między programem AAD a blackboardem Learn Ultra.
>
> Jeśli dane pole nie zostało odpowiednio ustawione w mapowaniu systemu SIS, integracja będzie nadal działać, ale użytkownicy mogą nie być wyświetlani w utworzonych klasach systemu Teams i mogą wystąpić błędy.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>Obsługa mapowania danych w ramach instytucji — pole systemu SIS poczty e-mail instytucji

W ramach rozwoju rozwiązań integracji z dostawcami chmury firma Blackboard Learn Ultra utworzyła nowe  pole poczty e-mail instytucji, zarówno w ramach integracji programu Student Information System Framework, jak i publicznych interfejsów API usługi REST, dzięki czemu instytucje mogą skutecznie zarządzać procesem synchronizacji danych między tablicą Blackboard Learn Ultra a AAD.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>Co oznacza poczta e-mail instytucji i jakie są jej znaczenie?

Pole **Adres e-mail** instytucji umożliwia dostosowanie mapowań pól między zewnętrznymi źródłami danych obsługiwanymi przez klienta a urządzeniem Blackboard Learn Ultra. Jeśli źródła danych są dostawcami chmury, takimi jak firma Microsoft, główna nazwa użytkownika (UPN) to podstawowa nazwa identyfikator unikatowy dla każdego użytkownika składającego się z prefiksu UPN (nazwy konta użytkownika) i sufiksu głównej nazwy użytkownika (nazwy domeny DNS) połączonego z symbolem @. Powoduje to utworzenie unikatowego adresu e-mail dla każdego określonego użytkownika w Microsoft Azure Active Directory.

Aby zapewnić dokładność danych, rejestracja lub członkostwo między zajęciami Blackboard Learn Ultra i Microsoft Teams jest poprawne, adres e-mail użytkownika musi być zgodne w obu systemach. W aplikacji Blackboard Learn Ultra użytkownicy mogą zmienić lub zastąpić istniejący adres e-mail w interfejsie użytkownika, co może spowodować występujące błędy synchronizacji i nieuzyskie dodanie użytkownika do zespołu zajęć. **Mapowanie pól poczty** e-mail instytucji zapewnia ten poziom sprawdzania poprawności i zabezpieczeń, które można prawidłowo zarządzać, niezależnie od tego, czy użytkownicy zmienili swoją pocztę e-mail w Blackboard Learn Ultra, czy nie.

 Gdy dwa adresy e-mail są różne, możesz:

- Należy podjąć decyzję, które źródło ma pierwszeństwo, i zarówno jako adres e-mail osoby, jak i jako adres e-mail instytucji.
  Lub
- Instytucja może ustawić niestandardowe mapowanie pól w adresie e-mail instytucji, co może rozwiązać potencjalny konflikt.

**Mapowanie pól poczty e-mail** instytucji jest teraz dostępne dla wszystkich istniejących typów integracji systemu SIS na stronie Advanced **Configuration Ustawienia** >  **Users Learn Object TypeField** >  **Mapping** ..

> [!NOTE]
> Należy pamiętać, że domyślnie dla poczty e-mail instytucji jest  ustawiona wartość Person **Email** (Adres e-mail osoby) dla wszystkich formatów sis i musi być unikatowa dla każdej osoby. Wszystkie istniejące integracje, które są ustawione i uruchomione, będą mieć to mapowanie danych w miejscu, ponieważ w sis nie powiedzie się importowanie użytkowników, jeśli ich wiadomości e-mail zostaną zduplikowane. Jeśli instytucja wymaga możliwości zmiany adresu e-mail instytucji na niestandardowy **, będzie** ona musi zarządzać tym za pośrednictwem grupy konfiguracji **zaawansowanej Ustawienia** sis.

## <a name="requirements"></a>Wymagania

Integracja Microsoft Teams kursu jest dostępna tylko dla kursów **Ultra Course View**. Twoja instytucja musi spełniać następujące wymagania, aby jej używać:

- Have Blackboard Learn Ultra Learn SaaS with Ultra Base Navigation enabled

  ![Przykład funkcji jest włączony w kursach.](media/feature-availability.png)

- Włączanie języka LTI do używania w kursach.

  a. Przejdź do **tematu Dostawcy narzędzi** **PanelLTI** >  **administratoraZarządzaj** >  właściwościami globalnymi.

  b. Wybierz **pozycję Włączone LTI w kursach** i opcjonalnie wybierz pozycję **Włączone w organizacjach**.

  c. Wybierz **pozycję Prześlij**.

- Musi być skonfigurowany lti

- Add Blackboard Learn Ultra Teams Classes LTI Integration

- Dodawanie Microsoft Teams klasy LTI 1.3

- Dodawanie narzędzia interfejsu API REST i udostępniania zasobów między pochodzeniem

- Konfigurowanie i zatwierdzanie Microsoft Teams klas

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>Dodawanie narzędzia Blackboard Learn Ultra Teams zajęć LTI 1.3

1. W **Panelu administratora** wybierz pozycję **Dostawcy narzędzi LTI**.

2. Wybierz **pozycję zarejestruj narzędzie LTI 1.3**.

3. W polu **Identyfikator klienta** wpisz lub skopiuj i wklej ten identyfikator:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Przejrzyj wszystkie ustawienia, które zostały wstępnie wypełnione i w menu **Stan narzędzia**, a następnie wybierz pozycję **Włączone**.

5. Na **stronie Zasady instytucji** wybierz **pozycję Rola w kursie, nazwa i** adres **e-mail**, a następnie wybierz pozycję **Tak** dla obu opcji.

6. Wybierz **pozycję Zezwalaj na dostęp do usługi ocen** i **Zezwalaj na dostęp do usługi członkostwa**.

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>Dodawanie narzędzia Microsoft Teams klasy LTI 1.3

1. W **Panelu administratora** wybierz pozycję **Dostawcy narzędzi LTI**.

2. Wybierz **pozycję zarejestruj narzędzie LTI 1.3**.

3. W polu **Identyfikator klienta** wpisz lub skopiuj i wklej ten identyfikator:

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. Przejrzyj wszystkie ustawienia, które zostały wstępnie wypełnione i w menu *Stan narzędzia* , a następnie wybierz pozycję *Włączone.*

5. Na **stronie Zasady instytucji** wybierz **pozycję Rola w kursie, nazwa i** **adres e-mail**. Wybierz **pozycję Tak** dla obu opcji.

6. Wybierz **pozycję Zezwalaj na dostęp do usługi ocen** i **Zezwalaj na dostęp do usługi członkostwa**.

## <a name="add-the-rest-api-tool"></a>Dodawanie narzędzia interfejsu API REST

1. W **Panelu administratora przejdź** do menu **Integracje** i wybierz pozycję **Rest API Integrations**.

2. Wybierz **pozycję Utwórz integrację**.

3. W polu **Identyfikator aplikacji** wpisz lub skopiuj i wklej ten identyfikator:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Wpisz użytkownika do integracji.

   Ten użytkownik będzie tym, który ma dostęp do macierzytego interfejsu API, z którym jest skojarzona aplikacja.

5. Wybierz **pozycję Prześlij**.

## <a name="add-the-cross-origin-resource-sharing"></a>Dodawanie udostępniania zasobów między pochodzeniem

1. W **panelu administratora przejdź** do menu **Integracje** i wybierz pozycję **Udostępnianie zasobów między pochodzeniem*.

2. Wybierz **pozycję Utwórz konfigurację**.

3. W polu **Pochodzenie** wpisz kopię i wklej ten adres URL:

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. W polu **Dozwolone nagłówki** wpisz **Autoryzacja**.

5. Ustaw **wartość Dostępny** na **wartość Tak**.

6. Wybierz **pozycję Prześlij**.

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>Konfigurowanie i zatwierdzanie Microsoft Teams klas

Aby pomyślnie zintegrować wystąpienie Blackboard Learn Ultra z klasami programu Microsoft Teams, musisz upewnić się, że aplikacja Blackboard Learn Ultra została zatwierdzona do uzyskania dostępu w Twojej Microsoft Azure dzierżawie. Jest to proces, który musi zostać ukończony przez administratora globalnego Microsoft 365 Twojej instytucji.

Ten proces można wykonać przed lub po skonfigurowaniu aplikacji LTI w wystąpieniu Blackboard Learn Ultra.

### <a name="before-configuring-the-lti-applications"></a>Przed rozpoczęciem konfigurowania aplikacji LTI

Jeśli zatwierdzisz aplikację Blackboard Learn Ultra Teams Classes azure przed skonfigurowaniem integracji lti, musisz przekierować do punktu końcowego zgody administratora platformy **tożsamości firmy Microsoft**. Adres URL jest widoczny:

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> Zastąpisz element **{Tenant}** konkretnym identyfikatorem Microsoft Azure dzierżawy.

Zostanie otwarte okno uprawnień z wyjaśnieniem, że udzielasz uprawnień aplikacji Blackboard Learn Ultra, aby uzyskać dostęp do Microsoft Teams.

![okno uprawnień dla aplikacji Microsoft i Blackboard.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>Po skonfigurowaniu aplikacji LTI

1. W **Panelu administratora przejdź** do pozycji Narzędzia **i** narzędzia i wybierz pozycję Microsoft Teams **Administratora integracji**.

2. Wybierz **pozycję Włącz Microsoft Teams**.

3. Dodaj swój **identyfikator dzierżawy firmy Microsoft** do dostępnego pola tekstowego.

4. Wybierz jedną z następujących opcji:

   - Jeśli aplikacja ma wstępnie za zgodą, zostanie w nim pokaziony mały znacznik wyboru. Jeśli pojawi się znacznik wyboru, wybierz pozycję **Prześlij**.

   - Jeśli zgoda nie została zatwierdzona, wykonaj czynności opisane w celu wygenerowania adresu URL w celu uzyskania zgody i wysłania go do administratora globalnego usługi Microsoft 365 w celu zatwierdzenia.

5. Po potwierdzeniu zatwierdzenia wybierz pozycję **Ponów** próbę, aby potwierdzić, a następnie wybierz pozycję **Prześlij**.
