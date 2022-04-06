---
title: Używanie Microsoft Teams z kanwą
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
description: Integracja Microsoft Teams zajęć za pomocą systemu Canvas
ms.openlocfilehash: 08edb2065cd91ccb0e0d52290dfe83f8a3e60392
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569009"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Używanie Microsoft Teams z kanwą

Microsoft Teams to aplikacja Edukacja Tools Interoperability (LTI), która ułatwia nauczycielom i uczniom nawigowanie między ich systemami LMS (Edukacja Management System) i Teams. Użytkownicy mogą uzyskać dostęp do zespołów klasowych powiązanych z ich kursem bezpośrednio z poziomu systemu LMS.

## <a name="prerequisites-before-deployment"></a>Wymagania wstępne przed wdrożeniem

> [!NOTE]
> Bieżące klasy Teams lti obsługują tylko synchronizację użytkowników systemu Canvas Microsoft Azure Active Directory (AAD) w ograniczonym zakresie.
>
> - Dzierżawa musi mieć licencję Microsoft Education (A1 lub wyższą).
> - Do mapowania użytkowników między systemami Canvas i Microsoft można używać tylko jednej dzierżawy firmy Microsoft.
> - Dzierżawa musi mieć dokładne dopasowanie między polem Canvas (adresem e-mail, unikatowym identyfikatorem użytkownika, identyfikatorem SIS lub identyfikatorem integracji) a polem w programie AAD (główna nazwa użytkownika ( UPN), podstawowy adres e-mail (poczta) lub alias e-mail (mailNickname)).
> - Jeśli tworzysz klasy i grupy za pomocą aplikacji SDS, zalecamy wyłączenie opcji tworzenia zespołu w aplikacji SDS i wykonanie czynności Oczyszczanie grupy, aby uniknąć duplikowania zajęć.[](/schooldatasync/group-cleanup) Nadal można używać aplikacji SDS do synchronizowania danych organizacji i użytkowników.

## <a name="enable-the-microsoft-teams-app-in-canvas"></a>Włączanie aplikacji Microsoft Teams Canvas

Aby rozpocząć integrację, należy włączyć aplikację w systemie Canvas przez włączenie kluczy dewelopera, włączenie synchronizacji Microsoft Teams i zatwierdzanie aplikacji Microsoft-Teams-Sync-for-Canvas. Zauważ, że zatwierdzanie aplikacji może być wykonywane tylko przez administratora dzierżawy firmy Microsoft, który może zatwierdzać aplikacje.

**Aby włączyć Microsoft Teams i zatwierdzić dostęp dla aplikacji**:

1. Zaloguj się do systemu Canvas jako administrator.

2. Wybierz link **Administrator** w nawigacji globalnej, a następnie wybierz swoje konto.
3. W obszarze nawigacji administratora wybierz link **Klucze** dewelopera, a następnie wybierz **kartę Dziedziczone** .
4. Włącz aplikacje LTI, które zamierzasz wdrożyć, wybierając stan **ON** dla każdej z odpowiednich aplikacji.

5. W obszarze nawigacji administratora **wybierz link Ustawienia**, a następnie **kartę Integracje**.

6. Włącz Microsoft Teams synchronizacji, włączając przełącznik. Ta synchronizacja umożliwia tworzenie zajęć w Teams na podstawie rejestracji w kursie.

   ![Pliki w Teams png w obszarze synchronizacji.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

7. Wypełnij poniższe pola odpowiednimi informacjami. Te pola będą używane do dopasowywania użytkowników w kanwie do użytkowników w AAD.
   - Nazwa **dzierżawy to** nazwa Twojej dzierżawy firmy Microsoft.
   - Atrybut **logowania to** jeden z następujących atrybutów użytkownika systemu Canvas użytych do mapowania:
      - **Poczta** e-mail to domyślny adres e-mail użytkownika systemu Canvas. Jeśli użytkownicy zmienią domyślny adres e-mail w płótnie, ich rejestracja w kursie może być zablokowana na synchronizację z Teams.
      - **Unikatowy identyfikator użytkownika** to identyfikator logowania użytkownika z systemu Canvas.
      - **Identyfikator użytkownika SIS** to wartość identyfikatora wypełniona w systemie informacji o uczniach (SIS, Student Information System) i wyświetlana na stronie profilu użytkownika.
      - **Identyfikator integracji** jest wypełniany tylko za pośrednictwem importu systemu SIS i jest można go wyświetlić na stronie profilu użytkownika. Zazwyczaj ta identyfikator unikatowy jest zapewniana przez tę instytucję i używana w przypadku zaufania kont lub konsolidacji do identyfikowania użytkowników z różnych kont.

   - Pole **Sufiks** jest opcjonalne i pozwala określić domenę, jeśli nie ma dokładnego mapowania między atrybutami canvas a polami usługi Microsoft AAD pola. Jeśli na przykład adres e-mail systemu Canvas to "name@example.edu", a upn w programie Microsoft AAD to "nazwa", możesz dopasować użytkowników, wprowadzając "@example.edu" w polu sufiksu. W tym polu należy wprowadzić domenę ze @.
   - Atrybut odnośnika usługi Active Directory to pole w programie AAD, do którego są dopasowane atrybuty kanwy. Wybierz między główną siecią danych, podstawowym adresem e-mail lub aliasem e-mail.

8. Wybierz **pozycję Aktualizuj Ustawienia**.

9. Aby zatwierdzić dostęp do aplikacji **Platformy Azure microsoft-Teams-Sync-for-Canvas**, wybierz link Udzielanie dostępu **dzierżawy**. Nastąpi przekierowanie do punktu końcowego zgody administratora platformy tożsamości firmy Microsoft.

   ![uprawnienia.](media/permissions.png)

   > [!NOTE]
   > Ten krok musi zostać wykonany przez administratora dzierżawy firmy Microsoft, który może zatwierdzać aplikacje.

10. Wybierz **pozycję Zaakceptuj**.

## <a name="integrate-teams-classes-lti-in-canvas"></a>Integracja Teams lti w płótnie

Po włączeniu synchronizacji i zatwierdzaniu aplikacji Platformy Azure administrator systemu Canvas może teraz dodać klasy Teams aplikacji LTI do środowiska canvas, aby była wyświetlana w nawigacji interfejsu użytkownika systemu Canvas.

**Aby dodać klasy Teams aplikacji LTI do środowiska systemu Canvas**:

1. Na karcie **Aplikacje** w **ustawieniach administratora** wybierz pozycję **+ Aplikacja**, aby dodać Teams LTI.

   ![external-apps.](media/external-apps.png)

2. W **przypadku ustawienia Typ konfiguracji** wybierz pozycję **Według identyfikatora klienta**.

   ![dodaj aplikację.](media/add-app.png)

3. W **przypadku identyfikatora klienta** wprowadź **170000000000570** dla klas Microsoft Teams LTI, a następnie wybierz pozycję **Prześlij**.

4. W wyświetlonym potwierdzeniu sprawdź nazwę aplikacji (Microsoft Teams zajęć), a następnie wybierz pozycję **Zainstaluj**.

   Klasy Microsoft Teams aplikacji LTI zostały dodane do listy aplikacji zewnętrznych.

## <a name="enabling-the-lti-app-for-canvas-courses"></a>Włączanie kursów lti dla systemu Canvas

Aby korzystać z aplikacji LTI w ramach kursu, instruktor kursu Canvas musi włączyć synchronizację integracji. Aby każdy kurs został utworzony, musi zostać włączony przez instruktora; nie ma żadnego globalnego mechanizmu tworzenia zespołów. Jest to środek ostrożności zapobiegający utworzeniu niechcianych zespołów.

Skorzystaj z dokumentacji nauczycieli[](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas), aby zasuńli od instruktorów dokumentację umożliwiającą włączenie aplikacji LTI dla każdego kursu i ukończenie konfiguracji integracji.
