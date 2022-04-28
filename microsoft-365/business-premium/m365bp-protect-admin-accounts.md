---
title: Ochrona kont administratorów w Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
description: Dowiedz się, jak skonfigurować i chronić konta administratorów w Microsoft 365 Business Premium.
ms.openlocfilehash: b054267264b8440929559ad1a2e335449f3c0309
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091528"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Ochrona kont administratorów w Microsoft 365 Business Premium

Ponieważ konta administratorów mają podwyższone uprawnienia, są one cennymi celami dla hakerów i cyberprzestępców. W tym artykule opisano:

- Jak skonfigurować dodatkowe konto administratora w nagłych wypadkach.
- Jak chronić te konta.

Po utworzeniu konta w celu Microsoft 365 i wprowadzeniu informacji automatycznie stajesz się administratorem globalnym (nazywanym również administratorem globalnym). Administrator globalny ma ostateczną kontrolę nad kontami użytkowników i wszystkimi innymi ustawieniami w centrum administracyjnym firmy Microsoft ([https://admin.microsoft.com](https://admin.microsoft.com)), ale istnieje wiele różnych rodzajów kont administratorów o różnym stopniu dostępu. Zobacz [informacje o rolach administratora](/office365/admin/add-users/about-admin-roles) , aby uzyskać informacje o różnych poziomach dostępu dla każdego rodzaju roli administratora.

## <a name="create-additional-admin-accounts"></a>Tworzenie dodatkowych kont administratorów

Używaj kont administratora tylko do administrowania. Administratorzy powinni mieć oddzielne konto użytkownika do regularnego korzystania z aplikacji Office i używać ich konta administracyjnego tylko wtedy, gdy jest to konieczne do zarządzania kontami i urządzeniami oraz podczas pracy nad innymi funkcjami administratora. Dobrym pomysłem jest również usunięcie licencji Microsoft 365 z kont administratorów, aby nie trzeba było za nie płacić.

Chcesz skonfigurować co najmniej jedno dodatkowe konto administratora globalnego, aby przyznać administratorowi dostęp do innego zaufanego pracownika. Możesz również utworzyć oddzielne konta administratora do zarządzania użytkownikami (ta rola nosi nazwę **Administrator zarządzania użytkownikami**). Aby uzyskać więcej informacji, zobacz [o rolach administratora](/office365/admin/add-users/about-admin-roles).

Aby utworzyć dodatkowe konta administratora:

 1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centrum administracyjne platformy Microsoft 365</a>, a następnie wybierz pozycję **Użytkownicy** \> **Aktywni użytkownicy** w lewej nawigacji.

    ![Wybierz pozycję Użytkownicy, a następnie pozycję Aktywni użytkownicy w lewym pasku nawigacyjnym.](../media/Activeusers.png)

 2. Na stronie **Aktywni użytkownicy** wybierz **pozycję Dodaj użytkownika** w górnej części strony, a następnie w panelu **Nowy użytkownik** wprowadź nazwę i inne informacje.

 3. Rozwiń sekcję **Role** i wybierz **pozycję administrator globalny**, aby udzielić temu użytkownikowi dostępu administratora globalnego. Możesz również wybrać opcję **Dostosowany administrator** i wybrać dowolną z wyświetlanych ról.

    Wprowadź alternatywną wiadomość e-mail w polu tekstowym **Alternatywny adres e-mail** . Możesz użyć tego adresu, aby odzyskać informacje o haśle, jeśli zostanie zablokowane. W przypadku administratorów globalnych na ten adres zostanie również wysłana instrukcja rozliczeniowa.

    ![Wybierz rolę administratora.](../media/adminroles.png)

 4. W sekcji **Licencje produktów** przenieś selektor dla **Microsoft 365 Business** do **pozycji Wył.**, a pozycję **Utwórz użytkownika bez licencji produktu** na **Wł**.

    ![Wybierz licencję produktu.](../media/productlicense.png)

## <a name="create-an-emergency-admin-account"></a>Tworzenie konta administratora awaryjnego

Należy również utworzyć konto kopii zapasowej, które nie jest skonfigurowane z uwierzytelnianiem wieloskładnikowym(MFA), aby nie blokować się przypadkowo (na przykład w przypadku utraty telefonu używanego jako druga forma weryfikacji). Upewnij się, że hasło dla tego konta ma frazę lub długość co najmniej 16 znaków. Jest to często określane jako "konto typu break-glass".

## <a name="create-a-user-account-for-yourself"></a>Tworzenie konta użytkownika dla siebie

Użyj konta użytkownika, aby uczestniczyć we współpracy z organizacją, w tym w sprawdzaniu poczty. Oznacza to, że poświadczenia administratora mogą być podobne do  *Alice.Chavez <span></span>@Contoso.org* , a zwykłe konto użytkownika może być podobne do *alice <span></span>@Contoso.com*.

Aby utworzyć nowe konto użytkownika:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centrum administracyjne platformy Microsoft 365</a>, a następnie wybierz pozycję **Użytkownicy** \> **Aktywni użytkownicy** w lewej nawigacji.

2. Na stronie **Aktywni użytkownicy** wybierz **pozycję Dodaj użytkownika** w górnej części strony, a następnie w panelu **Nowy użytkownik** wprowadź nazwę i inne informacje.

3. Rozwiń sekcję **Role** i wybierz pozycję **Użytkownik (bez dostępu administracyjnego).**

4. W sekcji **Licencje produktów** przenieś selektor dla **Microsoft 365 Business** do **pozycji Włączone**.

## <a name="additional-recommendations"></a>Dodatkowe zalecenia

- Przed użyciem kont administratorów zamknij wszystkie niepowiązane sesje przeglądarki i aplikacje, w tym osobiste konta e-mail. Można również używać w oknach przeglądarki prywatnej lub incognito.

- Po wykonaniu zadań administratora wyloguj się z sesji przeglądarki.

## <a name="next-objective"></a>Następny cel

Wykonaj kroki, aby [włączyć ustawienia domyślne zabezpieczeń](m365bp-conditional-access.md).

