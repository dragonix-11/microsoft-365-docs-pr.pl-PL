---
title: Korzystanie z zajęć w aplikacji Microsoft Teams z kanwą
ms.author: danismith
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
description: Integrowanie klas usługi Microsoft Teams z aplikacją Canvas
ms.openlocfilehash: 10024e124ce50ab542e6e68a5c237a47e1f7af83
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923024"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Korzystanie z zajęć w aplikacji Microsoft Teams z kanwą

Klasy usługi Microsoft Teams to aplikacja do współdziałania narzędzi szkoleniowych (LTI), która ułatwia nauczycielom i uczniom łatwe przechodzenie między systemem zarządzania uczeniem się (LMS) i usługą Teams. Użytkownicy mogą uzyskiwać dostęp do swoich zespołów klas skojarzonych z kursem bezpośrednio z poziomu usługi LMS.

## <a name="prerequisites-before-deployment"></a>Wymagania wstępne przed wdrożeniem

> [!NOTE]
> Bieżące klasy usługi Teams LTI obsługują tylko synchronizowanie użytkowników kanwy z usługą Microsoft Azure Active Directory (AAD) w ograniczonym zakresie.
>
> - Dzierżawca musi mieć licencję microsoft education (A1 lub nowszą).
> - Do mapowania użytkowników między aplikacjami Canvas i Microsoft można używać tylko jednej dzierżawy firmy Microsoft.
> - Dzierżawa musi mieć dokładne dopasowanie między polem Kanwy (adres e-mail, unikatowy identyfikator użytkownika, identyfikator SIS lub identyfikator integracji) a polem w usłudze AAD (główna nazwa użytkownika (UPN), podstawowym adresem e-mail (poczta) lub aliasem poczty e-mail (mailNickname)).
> - Jeśli używasz usług SDS do tworzenia klas i grup, zalecamy wyłączenie opcji tworzenia zespołu w usługach SDS i przeprowadzenie oczyszczania [grupy](/schooldatasync/group-cleanup) , aby uniknąć duplikowania klas. Usług SDS można nadal używać do synchronizowania danych organizacji i użytkowników.

## <a name="enable-the-microsoft-teams-app-in-canvas"></a>Włączanie aplikacji Microsoft Teams na kanwie

Aby rozpocząć integrację, musisz włączyć aplikację na kanwie, włączając klucze deweloperów, włączając usługę Microsoft Teams Sync i zatwierdzając aplikację Microsoft-Teams-Sync-for-Canvas. Należy pamiętać, że zatwierdzenie aplikacji może być wykonywane tylko przez administratora dzierżawy firmy Microsoft, który może zatwierdzać aplikacje.

**Aby włączyć usługę Microsoft Teams Sync i zatwierdzić dostęp do aplikacji**:

1. Zaloguj się do aplikacji Canvas jako administrator.

2. Wybierz link **Administrator** w nawigacji globalnej, a następnie wybierz swoje konto.
3. W obszarze nawigacji administratora wybierz link **Klucze deweloperów** , a następnie wybierz kartę **Dziedziczone** .
4. Włącz aplikacje LTI, które chcesz wdrożyć, wybierając stan **ON** dla każdej z odpowiednich aplikacji.

5. W obszarze nawigacji administratora wybierz link **Ustawienia** , a następnie kartę **Integracje** .

6. Włącz usługę Microsoft Teams Sync, włączając przełącznik. Ta synchronizacja umożliwia tworzenie klas w usłudze Teams na podstawie rejestracji kursu.

   ![Canvas Teams Sync Zaktualizowano png.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

7. Wypełnij następujące pola odpowiednimi informacjami. Te pola będą używane do dopasowywania użytkowników na kanwie do użytkowników w usłudze AAD.
   - **Nazwa dzierżawy** to nazwa dzierżawy firmy Microsoft.
   - **Atrybut logowania** jest jednym z następujących atrybutów użytkownika kanwy używanych do mapowania:
      - **Adres e-mail** to domyślny adres e-mail użytkownika kanwy. Jeśli użytkownicy zmienią swój domyślny adres e-mail na kanwie, ich rejestracja w kursie może uniemożliwić synchronizację z usługą Teams.
      - **Unikatowy identyfikator użytkownika** to identyfikator logowania kanwy użytkownika.
      - **Identyfikator użytkownika usługi SIS** to wartość identyfikatora wypełniona z systemu informacji o uczniach (SIS) i widoczna na stronie profilu użytkownika.
      - **Identyfikator integracji** jest wypełniany tylko za pośrednictwem importu SIS i można go wyświetlić na stronie profilu użytkownika. Zazwyczaj ten unikatowy identyfikator jest dostarczany przez instytucję i używany w relacjach zaufania kont lub sytuacjach konsorcjów do identyfikowania użytkowników na wielu kontach.

   - Pole **Sufiks** jest opcjonalne i umożliwia określenie domeny, gdy nie ma dokładnego mapowania między atrybutami kanwy a polami usługi Microsoft AAD. Jeśli na przykład adres e-mail kanwy to "name@example.edu", podczas gdy nazwa UPN w usłudze Microsoft AAD to "name", możesz dopasować użytkowników, wprowadzając ciąg "@example.edu" w polu sufiksu. Domena powinna zostać wprowadzona w tym polu z powyższym @.
   - Atrybut odnośnika usługi Active Directory to pole w usłudze AAD, do którego są dopasowywane atrybuty kanwy. Wybierz nazwę UPN, podstawowy adres e-mail lub alias wiadomości e-mail.

8. Wybierz pozycję **Aktualizuj ustawienia**.

9. Aby zatwierdzić dostęp do aplikacji **Microsoft-Teams-Sync-for-Canvas** platformy Azure w aplikacji Canvas, wybierz link **Udzielanie dostępu do dzierżawy** . Nastąpi przekierowanie do punktu końcowego zgody administratora platformy tożsamości firmy Microsoft.

   ![Uprawnienia.](media/permissions.png)

   > [!NOTE]
   > Ten krok musi zostać wykonany przez administratora dzierżawy firmy Microsoft, który może zatwierdzać aplikacje.

10. Wybierz pozycję **Zaakceptuj**.

## <a name="integrate-teams-classes-lti-in-canvas"></a>Integrowanie klas usługi Teams LTI na kanwie

Po włączeniu synchronizacji i zatwierdzeniu aplikacji platformy Azure administrator kanwy może teraz dodać aplikację LTI klasy Teams do środowiska kanwy, aby była wyświetlana w nawigacji interfejsu użytkownika kanwy.

**Aby dodać aplikację LTI klasy Teams do środowiska kanwy**:

1. Na **karcie Aplikacje** w **ustawieniach administratora** wybierz pozycję **+ Aplikacja** , aby dodać aplikacje LTI usługi Teams.

   ![aplikacje zewnętrzne.](media/external-apps.png)

2. W polu **Typ konfiguracji** wybierz pozycję **Według identyfikatora klienta**.

   ![dodaj aplikację.](media/add-app.png)

3. W polu **Identyfikator klienta** wprowadź **170000000000570** dla klas Usługi Microsoft Teams LTI, a następnie wybierz pozycję **Prześlij**.

4. W wyświetlonym potwierdzeniu sprawdź nazwę aplikacji (klasy Microsoft Teams), a następnie wybierz pozycję **Zainstaluj**.

   Aplikacja LTI klasy Microsoft Teams jest teraz dodawana do listy aplikacji zewnętrznych.

## <a name="enabling-the-lti-app-for-canvas-courses"></a>Włączanie aplikacji LTI dla kursów kanwy

Aby korzystać z aplikacji LTI w ramach kursu, instruktor kursu Canvas musi włączyć synchronizację integracji. Każdy kurs musi być włączony przez instruktora w celu utworzenia odpowiedniego zespołu; nie ma globalnego mechanizmu tworzenia zespołów. Zostało to zaprojektowane jako środek ostrożności, aby zapobiec tworzeniu niechcianych zespołów.

Zapoznaj się z [dokumentacją nauczycieli](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) dotyczącą włączania aplikacji LTI dla każdego kursu i ukończenia konfiguracji integracji.
