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
description: Możesz utworzyć szablon i użyć go, aby zaoszczędzić czas i ustandaryzować ustawienia podczas dodawania wielu użytkowników w Centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: 0f0d737bcf600acb4084c5e2b85e5595c6387fee
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436996"
---
# <a name="create-and-use-a-template-to-add-users"></a>Tworzenie i używanie szablonu w celu dodania użytkowników

Możesz utworzyć szablon i użyć go, aby zaoszczędzić czas i ustandaryzować ustawienia podczas dodawania wielu użytkowników. Szablony są szczególnie przydatne, jeśli masz użytkowników, którzy mają wiele wspólnych właściwości, takich jak ci, którzy mają tę samą rolę i pracują w tej samej lokalizacji, oraz ci, którzy wymagają tego samego oprogramowania. Na przykład możesz mieć zespół inżynierów pomocy technicznej, którzy pracują w tym samym biurze.  

## <a name="create-a-template"></a>Tworzenie szablonu

Szablony można łatwo utworzyćUżytkowniki&mdash; mogą wybrać pozycję **UżytkownicyAktywni** >  **użytkownicySzadresy** >  użytkownika, a następnie wybrać **pozycję Dodaj szablon** z listy rozwijanej lub dodać nowego użytkownika, a po zakończeniu będziesz mieć możliwość zapisania wpisu jako szablonu.

Podczas tworzenia szablonu po dodaniu użytkownika wartości wybierane dla następujących ustawień są zapisywane w szablonie:

- Nazwa domeny
- Wybór ustawień hasła: możesz utworzyć hasła lub wygenerować je automatycznie
- Wybór hasła jednorazowego: możesz wymagać od użytkownika utworzenia nowego hasła po pierwszym zalogowaniu
- Lokalizacja licencji
- Opcje licencji
- Opcje aplikacji
- Rola
- Większość informacji o profilu, takich jak **profil zadania**, **dział**, **Office**, **telefon Office** i **adres ulicy** 

Następujące informacje są specyficzne dla użytkownika i nie są zapisywane w szablonie:

- Imię i nazwisko
- Nazwa wyświetlana
- Nazwa użytkownika
- Wybór, aby wysłać hasło w wiadomości e-mail i do kogo jest wysyłana wiadomość e-mail z hasłem
- Numer telefonu komórkowego

Jeśli nie chcesz wprowadzać informacji o ustawieniu w sekcji, ta wartość będzie pusta, a to ustawienie nie będzie wyświetlane w szablonie. Jeśli na przykład pozostawisz **stanowisko puste** , podczas przeglądania szablonu i używania szablonu **stanowisko** nie będzie w ogóle wyświetlane. Jeśli pozostawisz wszystkie ustawienia sekcji **Profil** puste, w sekcji **Profil** zostanie wyświetlona wartość **Brak podana** w ostatnim szablonie.

Po utworzeniu szablonu przez wybranie opcji **Dodaj szablon** możesz wybrać, które wartości mają zostać ukończone. Wszystko, co pozostanie puste, będzie wyświetlane jako **Brak podane** w szablonie.

## <a name="use-a-template-to-add-a-user"></a>Dodawanie użytkownika przy użyciu szablonu

Aby dodać użytkownika przy użyciu istniejącego szablonu:

1. W centrum administracyjnym wybierz pozycję **UżytkownicyAktywni** >  użytkownicy.

2. Wybierz pozycję **Szablony użytkowników**, a następnie wybierz szablon z listy rozwijanej. (Lista będzie zawierać tylko utworzone szablony, a nie utworzone przez innych administratorów).

   > [!NOTE]
   > Możesz również użyć szablonu, aby dodać użytkownika, wybierając pozycję **Szablony** **użytkownikówZarządzanie** >  szablonami, wybieranie szablonu, a następnie wybieranie pozycji **Użyj szablonu**.

3. Wykonaj kroki, aby utworzyć użytkownika na podstawie wybranego szablonu.

   > [!NOTE]
   > Jeśli masz niewystarczające licencje dla dodanego użytkownika, a informacje o płatności są dostępne, spróbujemy kupić inną licencję, korzystając z istniejących informacji o płatności. Jeśli informacje o płatności są niedostępne, użytkownik zostanie utworzony jako użytkownik bez licencji.

## <a name="manage-templates"></a>Zarządzanie szablonami

Możesz usuwać tylko szablony, których już nie potrzebujesz, i dodawać nowe. Aby usunąć szablon:

1. W centrum administracyjnym wybierz pozycję **UżytkownicyAktywni** >  użytkownicy.

2. Wybierz pozycję **Szablony**, a następnie wybierz pozycję **Zarządzaj szablonami** z listy rozwijanej.

3. Zostanie wyświetlona lista szablonów. Szablon można usunąć, wykonując dowolne z następujących czynności:
    - Wybierz co najmniej jeden szablon, a następnie wybierz pozycję **Usuń**. 
    - Wybierz trzy kropki po prawej stronie nazwy szablonu, a następnie wybierz pozycję **Usuń**.
    - Wybierz nazwę szablonu. Gdy szczegóły szablonu pojawią się po prawej stronie ekranu, wybierz pozycję **Usuń szablon**.

## <a name="related-articles"></a>Powiązane artykuły:

[Dodawanie użytkowników i jednoczesne przypisywanie licencji](add-users.md)

[Usuwanie byłego pracownika z Microsoft 365](remove-former-employee.md)
  
