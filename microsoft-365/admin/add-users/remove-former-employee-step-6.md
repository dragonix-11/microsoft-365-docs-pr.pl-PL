---
title: Krok 6. Usunięcie licencji Microsoft 365 byłego pracownika
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Wykonaj poniższe czynności, aby usunąć licencję Microsoft 365 od byłego pracownika.
ms.openlocfilehash: 52ab851c88d05c33de58d28d566a46b5e8b1710b
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019250"
---
# <a name="step-6---remove-the-microsoft-365-license-from-a-former-employee"></a>Krok 6. Usunięcie Microsoft 365 pracownika

Jeśli nie chcesz płacić za licencję osoby, która odejdzie z organizacji, musisz usunąć licencję usługi Microsoft 365, a następnie usunąć ją z subskrypcji. Możesz przypisać licencję do innego użytkownika, jeśli nie usuniesz jej.

Jeśli skrzynka pocztowa musi być dostępna dla autoryzowanych osób, które uzyskały uprawnienia zbierania elektronicznych materiałów dowodowych ze względów prawnych lub zgodności z przepisami, musi ona mieć przypisaną licencję planu Exchange Online (plan 2) lub licencję planu Exchange Online (plan 1) z Exchange Online — archiwum  licencję dodatku), aby można było zastosować do skrzynki pocztowej hold przed jej usunięciem. Po usunięciu konta użytkownika wszystkie Exchange Online skojarzone z tym kontem użytkownika będą dostępne do przypisania noweowi użytkownikowi.
  
Po odebraniu licencji wszystkie dane użytkownika są przechowywane przez 30 dni. Możesz [uzyskać dostęp](get-access-to-and-back-up-a-former-user-s-data.md) do danych lub [przywrócić](restore-user.md) konto, jeśli użytkownik powróci. Po 30 dniach wszystkie dane użytkownika (z wyjątkiem dokumentów przechowywanych w u administratorach usługi SharePoint Online) zostaną trwale usunięte z usługi Microsoft 365 i nie będzie można ich odzyskać.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.
2. Wybierz imię i nazwisko pracownika, którego chcesz zablokować, a następnie wybierz **kartę Licencje i** aplikacje.
3. Wyczyść pola wyboru licencji, które chcesz usunąć, a następnie wybierz pozycję **Zapisz zmiany**.

**Aby zmniejszyć liczbę licencji, za** które płacisz do czasu zatrudnienia innej osoby, wykonaj następujące czynności:

1. W centrum administracyjnym przejdź **do strony** \> Rozliczenia <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">z produktami</a> i wybierz **kartę** Produkty.
2. Wybierz subskrypcję, z której chcesz usunąć licencje.
3. Na stronie szczegółów wybierz pozycję **Usuń licencje**.
4. W **okienku Usuwanie licencji** w obszarze Nowa liczba w polu Łączna liczba  licencji wprowadź łączną liczbę licencji, które chcesz uzyskać dla tej subskrypcji. Jeśli na przykład masz 25 licencji i chcesz usunąć jedną z nich, wprowadź wartość 24.
5. Wybierz **Zapisz**.

Po [dodaniu kolejnej](add-users.md) osoby do firmy zostanie wyświetlony monit o zakup licencji w tym samym czasie, w jednym kroku!

Aby uzyskać więcej informacji na temat zarządzania licencjami użytkowników usługi Microsoft 365 dla firm, zobacz Przypisywanie licencji użytkownikom w programie [Microsoft 365](../manage/assign-licenses-to-users.md) dla firm i Nieprzypisuj licencje użytkowników w programie [Microsoft 365 dla firm](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Jak usunięte konto pracownika wpływa na program Skype dla firm

Gdy usuniesz licencję użytkownika z usługi Office 365, skojarzony z tym użytkownikiem numer telefoniczny PSTN zostanie zwolniony. Możesz go przypisać innemu użytkownikowi.
  
Jeśli użytkownik należy do grupy kolejki, nie będzie już prawidłowym obiektem docelowym agentów kolejki połączeń. Dlatego zalecamy, aby również usunąć użytkownika z grup skojarzonych z kolejką połączeń.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Konfigurowanie przekazywania połączeń do osób w organizacji

Jeśli musisz skonfigurować przekazywanie połączeń dla numeru telefonu zakończonego pracownika, ustawienie przekazywania połączeń w obszarze Zasady połączeń może skonfigurować przesyłanie połączeń przychodzących do innych użytkowników lub dzwonić do innej osoby w tym samym czasie. Aby uzyskać więcej informacji, zobacz [Zasady połączeń w Microsoft Teams](/microsoftteams/teams-calling-policy).
