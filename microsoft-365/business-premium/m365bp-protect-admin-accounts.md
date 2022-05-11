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
ms.openlocfilehash: 1428ee6b447f3f841e7e8e9b77cfd82c2f7a6444
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320016"
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

 1. Na stronie **Aktywni użytkownicy** wybierz **pozycję Dodaj użytkownika** w górnej części strony. 

 1. W panelu **Dodawanie użytkownika wprowadź** podstawowe informacje, takie jak nazwa i nazwa użytkownika.

 1. Wprowadź i skonfiguruj informacje o **licencjach produktów** .

 1. W **obszarze Ustawienia opcjonalne** zdefiniuj rolę użytkownika, w tym w razie potrzeby dodaj dostęp do centrum administracyjnego.

    :::image type="content" source="media/m365bp-global-admin.png" alt-text="Zdefiniuj nowe role użytkowników.":::

 1. Zakończ i przejrzyj ustawienia, a następnie wybierz pozycję **Zakończ dodawanie** , aby potwierdzić szczegóły.

## <a name="create-an-emergency-admin-account"></a>Tworzenie konta administratora awaryjnego

Należy również utworzyć konto kopii zapasowej, które nie jest skonfigurowane z uwierzytelnianiem wieloskładnikowym(MFA), aby nie blokować się przypadkowo (na przykład w przypadku utraty telefonu używanego jako druga forma weryfikacji). Upewnij się, że hasło dla tego konta ma frazę lub długość co najmniej 16 znaków. Jest to często określane jako "konto typu break-glass".

## <a name="create-a-user-account-for-yourself"></a>Tworzenie konta użytkownika dla siebie

Użyj konta użytkownika, aby uczestniczyć we współpracy z organizacją, w tym w sprawdzaniu poczty. Oznacza to, że poświadczenia administratora mogą być podobne do  *alice.Chavez <span></span>@Contoso.org*, a zwykłe konto użytkownika może być podobne do *alice <span></span>@Contoso.com*.

Aby utworzyć nowe konto użytkownika:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centrum administracyjne platformy Microsoft 365</a>, a następnie wybierz pozycję **Użytkownicy** \> **Aktywni użytkownicy** w lewej nawigacji.

1. Na stronie **Aktywni użytkownicy** wybierz **pozycję Dodaj użytkownika** w górnej części strony, a następnie na panelu **Dodawanie użytkownika** wprowadź nazwę i inne informacje.

1. W sekcji **Licencje produktów** zaznacz pole wyboru **Microsoft 365 Business Premium (bez dostępu administracyjnego).**

1. W sekcji **Ustawienia opcjonalne** pozostaw domyślny przycisk radiowy wybrany dla **pozycji Użytkownik (brak dostępu do centrum administracyjnego).**

1. Zakończ i przejrzyj ustawienia, a następnie wybierz pozycję **Zakończ dodawanie** , aby potwierdzić szczegóły.

## <a name="additional-recommendations"></a>Dodatkowe zalecenia

- Przed użyciem kont administratorów zamknij wszystkie niepowiązane sesje przeglądarki i aplikacje, w tym osobiste konta e-mail. Można również używać w oknach przeglądarki prywatnej lub incognito.

- Po wykonaniu zadań administratora wyloguj się z sesji przeglądarki.

## <a name="next-objective"></a>Następny cel

Wykonaj kroki, aby [włączyć ustawienia domyślne zabezpieczeń](m365bp-conditional-access.md).

