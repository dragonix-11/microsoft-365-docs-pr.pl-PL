---
title: Krok 6. Usuwanie i usuwanie licencji Microsoft 365 od byłego pracownika
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
description: Możesz usunąć licencję Microsoft 365 byłego pracownika, a następnie usunąć ją z subskrypcji lub przypisać licencję innemu użytkownikowi.
ms.openlocfilehash: 95f95403a316e176f91c7f120ce5a26487a7a59f
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436234"
---
# <a name="step-6---remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>Krok 6. Usuwanie i usuwanie licencji Microsoft 365 od byłego pracownika

Jeśli nie chcesz płacić za licencję po opuszczeniu organizacji przez kogoś, musisz usunąć licencję Microsoft 365, a następnie usunąć ją z subskrypcji. Możesz przypisać licencję innemu użytkownikowi, jeśli jej nie usuniesz.

Jeśli dostęp do skrzynki pocztowej muszą uzyskać autoryzowane osoby, którym udzielono uprawnień do zbierania elektronicznych materiałów dowodowych ze względów prawnych lub zgodności, musi mieć przypisaną licencję Exchange Online plan 2 (lub licencję Exchange Online plan 1 z Exchange Online — archiwum  licencji dodatku), aby blokada mogła zostać zastosowana do skrzynki pocztowej przed jej usunięciem. Po usunięciu konta użytkownika każda licencja Exchange Online skojarzona z kontem użytkownika będzie dostępna do przypisania nowemu użytkownikowi.
  
Po odebraniu licencji wszystkie dane użytkownika są przechowywane przez 30 dni. Możesz [uzyskać dostęp](get-access-to-and-back-up-a-former-user-s-data.md) do danych lub [przywrócić](restore-user.md) konto, jeśli użytkownik powróci. Po upływie 30 dni wszystkie dane użytkownika (z wyjątkiem dokumentów przechowywanych w usłudze SharePoint Online) są trwale usuwane z Microsoft 365 i nie można ich odzyskać.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.
2. Wybierz nazwę pracownika, którego chcesz zablokować, a następnie wybierz kartę **Licencje i aplikacje** .
3. Wyczyść pola wyboru dla licencji, które chcesz usunąć, a następnie wybierz pozycję **Zapisz zmiany**.

**Aby zmniejszyć liczbę licencji, za które płacisz** do czasu zatrudnienia innej osoby, wykonaj następujące kroki:

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a> i wybierz kartę **Produkty** .
2. Wybierz subskrypcję, z której chcesz usunąć licencje.
3. Na stronie szczegółów wybierz pozycję **Usuń licencje**.
4. W okienku **Usuń licencje** w obszarze Nowa ilość w polu **Łączna liczba licencji** wprowadź całkowitą liczbę licencji, które mają być przeznaczone dla tej subskrypcji. Jeśli na przykład masz 25 licencji i chcesz usunąć jedną z nich, wprowadź 24.
5. Wybierz **Zapisz**.

Po [dodaniu innej osoby](add-users.md) do firmy zostanie wyświetlony monit o zakup licencji w tym samym czasie, z jednym krokiem!

Aby uzyskać więcej informacji na temat zarządzania licencjami użytkowników dla Microsoft 365 dla firm, zobacz [Przypisywanie licencji do użytkowników w Microsoft 365 dla firm](../manage/assign-licenses-to-users.md) i [Anulowanie przypisywania licencji od użytkowników w Microsoft 365 dla firm](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Jak usunięte konto pracownika wpływa na program Skype dla firm

Gdy usuniesz licencję użytkownika z usługi Office 365, skojarzony z tym użytkownikiem numer telefoniczny PSTN zostanie zwolniony. Możesz go przypisać innemu użytkownikowi.
  
Jeśli użytkownik należy do grupy kolejki, nie będzie już prawidłowym obiektem docelowym agentów kolejki połączeń. Dlatego zalecamy, aby również usunąć użytkownika z grup skojarzonych z kolejką połączeń.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Konfigurowanie przekazywania połączeń do osób w organizacji

Jeśli musisz skonfigurować przekazywanie połączeń dla numeru telefonu zakończonego pracownika, ustawienie przekazywania połączeń w obszarze Zasady połączeń może skonfigurować przekazywanie dalej, w którym połączenia przychodzące mogą być przekazywane innym użytkownikom lub mogą dzwonić do innej osoby w tym samym czasie. Aby uzyskać więcej informacji, zobacz [Wywoływanie zasad w Microsoft Teams](/microsoftteams/teams-calling-policy).
