---
title: Korzystanie ze spotkań w aplikacji Microsoft Teams z kanwą
ms.author: danismith
author: DaniEASmith
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
description: Integrowanie spotkań Microsoft Teams z kanwą
ms.openlocfilehash: cbb24972dba7fafe60cb460e514a0fede64a08fb
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621459"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Korzystanie ze spotkań w aplikacji Microsoft Teams z kanwą

Microsoft Teams spotkania to aplikacja Edukacja Tools Interoperability (LTI), która ułatwia nauczycielom i uczniom łatwe przechodzenie między systemem zarządzania Edukacja (LMS) i Teams. Użytkownicy mogą uzyskiwać dostęp do swoich zespołów klas skojarzonych z kursem bezpośrednio z poziomu usługi LMS.

## <a name="prerequisites-before-deployment"></a>Wymagania wstępne przed wdrożeniem

> [!NOTE]
> Bieżąca Teams Meetings LTI obsługuje tylko synchronizowanie użytkowników kanwy z Microsoft Azure Active Directory (AAD) w ograniczonym zakresie.
>
> - Dzierżawca musi mieć licencję microsoft education.
> - Do mapowania użytkowników między aplikacjami Canvas i Microsoft można używać tylko jednej dzierżawy firmy Microsoft.
> - Przed użyciem klasy Teams LTI należy wyłączyć School Data Sync (SDS), aby uniknąć duplikowania grup.

## <a name="microsoft-office-365-admin"></a>administrator Microsoft Office 365

Przed rozpoczęciem zarządzania integracją Microsoft Teams w kanwie Instructure ważne jest, aby aplikacja **Microsoft-Teams-Sync-for-Canvas** platformy Azure firmy Canvas została zatwierdzona przez administratora Microsoft Office 365 instytucji w dzierżawie Microsoft Azure przed ukończeniem konfiguracji administratora kanwy.

1. Zaloguj się do kanwy.

2. Wybierz link **Administrator** w nawigacji globalnej, a następnie wybierz swoje konto.

3. W obszarze nawigacji administratora wybierz link **Ustawienia**, a następnie kartę **Integracje**.

   ![Kanwa Teams Synchronizuj zaktualizowane png.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. Wprowadź nazwę dzierżawy firmy Microsoft, atrybut logowania, sufiks domeny i atrybut wyszukiwania usługi AAD. Te pola będą używane do dopasowywania użytkowników na kanwie do użytkowników w Microsoft Azure Active Directory.
   - Atrybut logowania to atrybut użytkownika kanwy używany do dopasowywania.
   - Pole Sufiks jest opcjonalne i umożliwia określenie domeny, gdy nie ma dokładnego mapowania między atrybutami kanwy a polami usługi Microsoft AAD. Jeśli na przykład adres e-mail kanwy to "name@example.edu", podczas gdy nazwa UPN w usłudze Microsoft AAD to "name", możesz dopasować użytkowników, wprowadzając ciąg "example.edu" w polu sufiksu.
   - Atrybut odnośnika usługi Active Directory to pole po stronie firmy Microsoft, do którego są dopasowywane atrybuty kanwy. Wybierz nazwę UPN, podstawowy adres e-mail lub alias wiadomości e-mail.

5. Po **zakończeniu** wybierz pozycję Aktualizuj Ustawienia.

6. Aby zatwierdzić dostęp do aplikacji **Microsoft-Teams-Sync-for-Canvas** platformy Azure programu Canvas, wybierz link **Udzielanie dostępu do dzierżawy**. Nastąpi przekierowanie do punktu końcowego zgody administratora platformy tożsamości firmy Microsoft.

   ![Uprawnienia.](media/permissions.png)

7. Wybierz pozycję **Zaakceptuj**.

   > [!NOTE]
   > Synchronizacja to funkcja zarządzana przez partnera LMS i używana do synchronizowania członkostwa na poziomie kursu z zespołem Teams przy użyciu interfejsów API programu Microsoft Graph. Jest to przede wszystkim funkcja, którą nauczyciel włącza jako rzeczywisty na poziomie kursu. Następnie wszelkie zmiany członkostwa wprowadzone po stronie usługi LMS dotyczące dodawania lub usuwania elementów członkowskich są odzwierciedlane przy użyciu synchronizacji zaimplementowanego przez partnera LMS. Jeszcze przed włączeniem tego procesu dla nauczyciela administrator instytutu edukacji M365 zezwala nauczycielom na dostęp do synchronizacji przy użyciu metody uprawnień synchronizacji znajdującej się poniżej. Te uprawnienia są przyznawane partnerowi LMS, aby umożliwić nauczycielom synchronizowanie członkostwa między kursem LMS a zespołami Teams Class.

8. Włącz synchronizację Microsoft Teams, włączając przełącznik.

   ![teams-sync.](media/teams-sync.png)

## <a name="canvas-admin"></a>Administrator kanwy

Skonfiguruj integrację Microsoft Teams LTI 1.3.

Jako administrator kanwy musisz dodać aplikację LTI Microsoft Teams spotkań w danym środowisku. Zanotuj identyfikator klienta LTI dla aplikacji.

 - spotkania Microsoft Teams — 170000000000703

1. Dostęp **do ustawień** >  **administratoraAplikacje**.

2. Wybierz pozycję **+ Aplikacja**, aby dodać Teams aplikacji LTI.

   ![aplikacje zewnętrzne.](media/external-apps.png)

3. Wybierz **pozycję Według identyfikatora klienta** dla typu konfiguracji.

   ![dodaj aplikację.](media/add-app.png)

4. Wprowadź podany identyfikator klienta, a następnie wybierz pozycję **Prześlij**.

   Zobaczysz nazwę aplikacji LTI spotkań Microsoft Teams dla identyfikatora klienta w celu potwierdzenia.

5. Wybranie pozycji **Zainstaluj**.

   Aplikacja LTI spotkań Microsoft Teams zostanie dodana do listy aplikacji zewnętrznych.

6. Włącz aplikację, przechodząc do kluczy deweloperów na koncie administratora kanwy, wybierając pozycję dziedziczone i włączając przełącznik dla Microsoft Teams Spotkania.

## <a name="enable-for-canvas-courses"></a>Włącz dla kursów kanwy

Aby korzystać z lti w ramach kursu, instruktor kursu Canvas musi włączyć synchronizację integracji. Każdy kurs musi być włączony przez instruktora w celu utworzenia odpowiedniego Teams; nie ma globalnego mechanizmu tworzenia Teams. Jest to zaprojektowane z zachowaniem ostrożności, aby zapobiec tworzeniu niechcianych Teams.

Zapoznaj się z [dokumentacją nauczycieli](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) dotyczącą włączania lti dla każdego kursu i ukończenia konfiguracji integracji.
