---
title: Używanie Microsoft Teams w aplikacji Canvas
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: sovaish
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Integracja Microsoft Teams spotkania za pomocą systemu Canvas
ms.openlocfilehash: 2bd004c86a7d6d2ee5a671d30d98e0af71990a81
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977629"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Używanie Microsoft Teams w aplikacji Canvas

Microsoft Teams spotkania to aplikacja Edukacja Tools Interoperability (LTI), która ułatwia nauczycielom i uczniom nawigowanie między ich systemami LMS (Edukacja Management System) i Teams. Użytkownicy mogą uzyskać dostęp do zespołów klasowych powiązanych z ich kursem bezpośrednio z poziomu systemu LMS.

## <a name="prerequisites-before-deployment"></a>Wymagania wstępne przed wdrożeniem

> [!NOTE]
> Bieżąca wersja Teams LTI obsługuje tylko synchronizację użytkowników systemu Canvas Microsoft Azure Active Directory (AAD) w ograniczonym zakresie. 
> - Dzierżawa musi mieć licencję microsoft education.
> - Do mapowania użytkowników między systemami Canvas i Microsoft można używać tylko jednej dzierżawy firmy Microsoft.
> - Aby uniknąć duplikowania grup, School Data Sync (SDS) należy wyłączyć usługę School Data Sync (SDS) przed użyciem narzędzia Class Teams LTI.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 administratorem

Przed rozpoczęciem zarządzania integracją z usługą Microsoft Teams w systemie Canvas w obrębie struktury należy przed ukończeniem konfiguracji administracyjnej systemu Microsoft Azure zatwierdzoną przez administratora systemu Microsoft Office 365 Twojej instytucji w dzierżawie systemu Microsoft Azure zatwierdzoną przez administratora systemu Canvas aplikację **Teams** Canvas.

1. Zaloguj się do kanwy.

2. Wybierz link **Administrator** w nawigacji globalnej, a następnie wybierz swoje konto.

3. W obszarze nawigacji administratora **wybierz link Ustawienia**, a następnie **kartę Integracje**.

![Pliki w Teams png w obszarze synchronizacji.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. Wprowadź nazwę dzierżawy firmy Microsoft, atrybut logowania, sufiks domeny AAD atrybut wyszukiwania. Te pola będą używane do dopasowywania użytkowników w kanwie do użytkowników w Microsoft Azure Active Directory. 
   * Atrybut logowania to atrybut użytkownika systemu Canvas wykorzystany w celu dopasowania.
   * Pole Sufiks jest opcjonalne i pozwala określić domenę, jeśli nie ma dokładnego mapowania między atrybutami Canvas a polami usługi Microsoft AAD pól. Jeśli na przykład adres e-mail systemu Canvas name@example.edu ma nazwę "name@example.edu", a upn w programie Microsoft AAD to "nazwa", możesz dopasować użytkowników, wprowadzając "example.edu" w polu sufiksu.
   * Atrybut odnośnika usługi Active Directory to pole po stronie firmy Microsoft, do którego są dopasowane atrybuty systemu Canvas. Wybierz między główną siecią danych, podstawowym adresem e-mail lub aliasem e-mail.

5. Wybierz **pozycję Ustawienia** po zakończeniu.

6. Aby zatwierdzić dostęp do aplikacji **Platformy Azure microsoft-Teams-Sync-for-Canvas**, wybierz link Udzielanie dostępu **dzierżawy**. Nastąpi przekierowanie do punktu końcowego zgody administratora platformy tożsamości firmy Microsoft.

   ![uprawnienia.](media/permissions.png)

7. Wybierz **pozycję Zaakceptuj**. 

> [!NOTE]
> Synchronizacja to funkcja, która jest zarządzana przez partnera LMS i jest używana do synchronizowania członkostwa na poziomie kursu z zespołem Teams przy użyciu interfejsów API Microsoft Graph. Jest to przede wszystkim funkcja włączana przez nauczyciela jako prawdziwa na poziomie kursu. Następnie każda zmiana członkostwa wprowadzona po stronie systemu LMS w celu dodatku lub usunięcia członków jest odzwierciedlana przy użyciu synchronizacji zaimplementowanej przez partnera systemu LMS. Jeszcze zanim ten proces zostanie włączony dla nauczycieli administrator M365 Education Institute zezwala ich nauczycielom na uzyskiwanie dostępu do synchronizacji przy użyciu modalnego uprawnień synchronizacji, który został znaleziony poniżej. Te uprawnienia są udzielane partnerowi programu LMS w celu umożliwienia nauczycielom synchronizowania członkostwa między kursem LMS a zespołami Teams zajęć.

8. Włącz Microsoft Teams synchronizacji przez włączenie przełącznika.

   ![teams-sync.](media/teams-sync.png)

## <a name="canvas-admin"></a>Administrator systemu Canvas

Skonfiguruj integrację z Microsoft Teams LTI 1.3.

Jako administrator systemu Canvas musisz dodać aplikację LTI spotkań Microsoft Teams w swoim środowisku. Zanotuj identyfikator klienta LTI aplikacji.

 - Microsoft Teams spotkania — 170000000000703

1. Ustawienia **administratora programu** >  **AccessApps**.

2. Wybierz **pozycję + Aplikacja**, aby dodać Teams LTI.

   ![external-apps.](media/external-apps.png)

3. Wybierz **pozycję Według identyfikatora klienta** dla typu konfiguracji.

   ![dodaj aplikację.](media/add-app.png)

4. Wprowadź podany identyfikator klienta, a następnie wybierz pozycję **Prześlij**.

   Zauważysz, że w spotkaniach Microsoft Teams nazwa aplikacji LTI dla identyfikatora klienta w celu potwierdzenia.

5. Wybranie pozycji **Zainstaluj**.

   Aplikacja Microsoft Teams LTI zostanie dodana do listy aplikacji zewnętrznych.

6. Włącz aplikację, przechodząc do kluczy dewelopera na koncie administratora systemu Canvas, wybierając pozycję dziedziczoną i włączając przełącznik "wł" dla Microsoft Teams spotkania.
   
## <a name="enable-for-canvas-courses"></a>Włączanie kursów dla kanwy

Aby korzystać z lti w ramach kursu, instruktor kursu Canvas musi włączyć synchronizację integracji. Każdy kurs musi zostać włączony przez instruktora w celu utworzenia Teams; nie ma żadnego globalnego mechanizmu Teams tworzenia. Ten sposób tworzona jest z zachowaniem ostrożności, aby zapobiec Teams tworzenia niechcianych wiadomości.

Należy poleć nauczycielom dokumentację [dla nauczycieli](https://support.microsoft.com/en-us/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) w celu włączenia funkcji LTI dla każdego kursu i ukończenia konfiguracji integracji.
