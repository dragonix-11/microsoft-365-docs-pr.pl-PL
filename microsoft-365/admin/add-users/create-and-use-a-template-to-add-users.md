---
title: Tworzenie i używanie szablonu w celu dodania użytkowników
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Można utworzyć szablon i za jego pomocą zaoszczędzić czas i ujednolicić ustawienia podczas dodawania wielu użytkowników.
ms.openlocfilehash: cacb3fc6ef2a145cbfe4c4131b2e5e38eca2c257
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983672"
---
# <a name="create-and-use-a-template-to-add-users"></a>Tworzenie i używanie szablonu w celu dodania użytkowników

Szablon można utworzyć i za jego pomocą zaoszczędzić czas i ujednolicić ustawienia podczas dodawania wielu użytkowników. Szablony są szczególnie przydatne, jeśli użytkownicy mają wiele wspólnych właściwości, takich jak użytkownicy o tej samej roli i jednocześnie korzystający z tego samego oprogramowania. Na przykład zespół inżynierów pomocy technicznej może pracować w tym samym biurze.  

## <a name="create-a-template"></a>Tworzenie szablonu

&mdash; >  Szablony można łatwo tworzyćMożesz wybrać pozycję **UżytkownicyAktywowanie** >  użytkownikówUżytkowuj **szablonów,** **a** następnie wybrać pozycję Dodaj szablon z listy rozwijanej. Możesz też dodać nowego użytkownika, a po zakończeniu pracy będzie dostępna opcja zapisania wpisu jako szablonu.

Podczas tworzenia szablonu po dodaniu użytkownika w szablonie są zapisywane wartości, które można wybrać dla następujących ustawień:

- Nazwa domeny
- Wybór ustawień haseł: możesz utworzyć hasła lub ustawić ich automatyczne generowanie
- Wybór hasła raz: możesz wymagać od użytkownika utworzenia nowego hasła po pierwszym zalogowaniu się
- Lokalizacja licencji
- Opcje wyboru licencji
- Opcje wyboru aplikacji
- Rola
- Większość informacji w profilu, takich jak **profil stanowiska****, dział**, **Office**, **Office i** **adres ulicy** 

Poniższe informacje są specyficzne dla użytkownika i nie są zapisywane w szablonie:

- Imię i nazwisko
- Nazwa wyświetlana
- Nazwa użytkownika
- Możliwość wysłania hasła w wiadomości e-mail oraz tego, do kogo jest wysyłana wiadomość e-mail z hasłem
- Numer telefonu komórkowego

Jeśli użytkownik nie chce wprowadzać informacji o ustawieniu w sekcji, ta wartość będzie pusta, a to ustawienie nie będzie wyświetlane w szablonie. Jeśli na przykład pozostawisz pole  Stanowisko puste, podczas przeglądania szablonu i korzystania z **szablonu stanowisko w** ogóle nie będzie wyświetlane. Jeśli wszystkie ustawienia sekcji Profil **pozostawisz** puste, w **sekcji Profil** w sekcji Profil będzie wyświetlana wartość **Brak podany** w ostatecznym szablonie.

Podczas tworzenia szablonu, wybierając opcję **Dodaj szablon** , możesz wybrać wartości do ukończenia. Wszystko, co pozostało puste, będzie wyświetlane jako **Brak podane** w szablonie.

## <a name="use-a-template-to-add-a-user"></a>Dodawanie użytkownika za pomocą szablonu

Aby dodać użytkownika za pomocą istniejącego szablonu:

1. W centrum administracyjnym wybierz pozycję **UżytkownicyAktywowanie** >  użytkowników.

2. Wybierz **pozycję Szablony** użytkownika, a następnie wybierz szablon z listy rozwijanej. (Lista będzie zawierać tylko szablony utworzone przez Ciebie, a nie te utworzone przez innych administratorów).

   > [!NOTE]
   > Możesz również dodać użytkownika za pomocą szablonu, wybierając pozycję **Szablony** >  **użytkownikaU szablony**, wybieranie szablonu, a następnie pozycję **Użyj szablonu**.

3. Postępuj zgodnie z instrukcjami, aby utworzyć użytkownika na podstawie wybranego szablonu.

   > [!NOTE]
   > Jeśli nie masz wystarczających licencji dla dodawania użytkownika i Twoje informacje dotyczące płatności są dostępne, podejmiemy próbę zakupu kolejnej licencji przy użyciu twoich istniejących informacji dotyczących płatności. Jeśli Informacje o płatności są niedostępne, użytkownik zostanie utworzony jako nielicencjonowany użytkownik.

## <a name="manage-templates"></a>Zarządzanie szablonami

Możesz usuwać tylko szablony, które nie są już potrzebne, i dodawać nowe. Aby usunąć szablon:

1. W centrum administracyjnym wybierz pozycję **UżytkownicyAktywowanie** >  użytkowników.

2. Wybierz **pozycję** Szablony, a **następnie z listy** rozwijanej wybierz pozycję Zarządzaj szablonami.

3. Zostanie wyświetlona lista szablonów. Szablon możesz usunąć, wykonując dowolną z następujących czynności:
    - Zaznacz jeden lub więcej szablonów, a następnie wybierz pozycję **Usuń**. 
    - Wybierz trzy kropki po prawej stronie nazwy szablonu, a następnie wybierz pozycję **Usuń**.
    - Wybierz nazwę szablonu. Gdy szczegóły szablonu zostaną wyświetlone po prawej stronie ekranu, wybierz pozycję **Usuń szablon**.

## <a name="related-articles"></a>Artykuły pokrewne

[Dodawanie użytkowników i przypisywanie licencji w tym samym czasie](add-users.md)

[Usuwanie byłego pracownika z Microsoft 365](remove-former-employee.md)
  
