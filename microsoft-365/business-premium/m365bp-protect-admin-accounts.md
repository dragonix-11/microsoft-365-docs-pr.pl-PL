---
title: Ochrona kont administratorów w Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
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
ms.openlocfilehash: a4f6265fd47a449c4768e7aef82ad6fdc004011f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631833"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Ochrona kont administratorów w Microsoft 365 Business Premium

Ponieważ konta administratorów mają podwyższone uprawnienia, są one cennymi celami dla hakerów i cyberprzestępców. W tym artykule opisano:

- [Jak skonfigurować inne konto administratora w nagłych wypadkach](#create-other-admin-accounts).
- [Jak utworzyć konto administratora awaryjnego](#create-an-emergency-admin-account).
- [Jak utworzyć konto użytkownika dla siebie](#create-a-user-account-for-yourself).
- [Jak chronić konta administratorów](#protect-admin-accounts).
- [Dodatkowe zalecenia](#additional-recommendations) i [kolejny cel](#next-objective).

Gdy zarejestrujesz się w usłudze Microsoft 365 i wprowadzisz swoje informacje, automatycznie zostaniesz administratorem globalnym (nazywanym również administratorem globalnym). Administrator globalny ma ostateczną kontrolę nad kontami użytkowników i wszystkimi innymi ustawieniami w centrum administracyjnym firmy Microsoft ([https://admin.microsoft.com](https://admin.microsoft.com)), ale istnieje wiele różnych rodzajów kont administratorów o różnym stopniu dostępu. Zobacz [informacje o rolach administratora](/office365/admin/add-users/about-admin-roles) , aby uzyskać informacje o różnych poziomach dostępu dla każdego rodzaju roli administratora.

## <a name="create-other-admin-accounts"></a>Tworzenie innych kont administratorów

Używaj kont administratora tylko na potrzeby administracji platformy Microsoft 365. Administratorzy powinni mieć oddzielne konto użytkownika do regularnego korzystania z aplikacji pakietu Office i używać ich konta administracyjnego tylko wtedy, gdy jest to konieczne do zarządzania kontami i urządzeniami oraz podczas pracy nad innymi funkcjami administratora. Dobrym pomysłem jest również usunięcie licencji platformy Microsoft 365 z kont administratorów, aby nie trzeba było płacić za dodatkowe licencje.

Należy skonfigurować co najmniej jedno inne konto administratora globalnego w celu udzielenia dostępu administratora innemu zaufanemu pracownikowi. Możesz również utworzyć oddzielne konta administratora do zarządzania użytkownikami (ta rola nosi nazwę **Administrator zarządzania użytkownikami**). Aby uzyskać więcej informacji, zobacz [o rolach administratora](/office365/admin/add-users/about-admin-roles).

> [!IMPORTANT]
> Mimo że zalecamy skonfigurowanie zestawu kont administratorów, należy ograniczyć liczbę administratorów globalnych w organizacji. Ponadto zalecamy przestrzeganie koncepcji dostępu z najniższymi uprawnieniami, co oznacza udzielenie dostępu tylko do danych i operacji potrzebnych do wykonywania ich zadań. [Dowiedz się więcej o zasadzie najniższych uprawnień](/azure/active-directory/develop/secure-least-privileged-access). 

Aby utworzyć więcej kont administratorów:

 1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centrum administracyjne platformy Microsoft 365</a>, a następnie wybierz pozycję **Użytkownicy** \> **Aktywni użytkownicy** w lewej nawigacji.

    ![Wybierz pozycję Użytkownicy, a następnie pozycję Aktywni użytkownicy w lewym pasku nawigacyjnym.](../media/Activeusers.png)

 2. Na stronie **Aktywni użytkownicy** wybierz **pozycję Dodaj użytkownika** w górnej części strony. 

 3. W panelu **Dodawanie użytkownika wprowadź** podstawowe informacje, takie jak nazwa i nazwa użytkownika.

 4. Wprowadź i skonfiguruj informacje o **licencjach produktów** .

 5. W **obszarze Ustawienia opcjonalne** zdefiniuj rolę użytkownika, w tym w razie potrzeby dodaj dostęp Administracja centrum.

    :::image type="content" source="media/m365bp-global-admin.png" alt-text="Zdefiniuj nowe role użytkowników.":::

 6. Zakończ i przejrzyj ustawienia, a następnie wybierz pozycję **Zakończ dodawanie** , aby potwierdzić szczegóły.

## <a name="create-an-emergency-admin-account"></a>Tworzenie konta administratora awaryjnego

Należy również utworzyć konto kopii zapasowej, które nie jest skonfigurowane przy użyciu uwierzytelniania wieloskładnikowego (MFA), aby nie blokować się przypadkowo (na przykład w przypadku utraty telefonu używanego jako druga forma weryfikacji). Upewnij się, że hasło dla tego konta ma frazę lub długość co najmniej 16 znaków. To konto administratora awaryjnego jest często określane jako "konto typu break-glass".

## <a name="create-a-user-account-for-yourself"></a>Tworzenie konta użytkownika dla siebie

Jeśli jesteś administratorem, musisz mieć konto użytkownika do wykonywania zwykłych zadań służbowych, takich jak sprawdzanie poczty. Nadaj swoim kontom nazwę, aby wiedzieć, która z nich jest. Na przykład poświadczenia administratora mogą być podobne do  *Alice.Chavez <span></span>@Contoso.org*, a zwykłe konto użytkownika może być podobne do *alice <span></span>@Contoso.com*.

Aby utworzyć nowe konto użytkownika:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centrum administracyjne platformy Microsoft 365</a>, a następnie wybierz pozycję **Użytkownicy** \> **Aktywni użytkownicy** w lewej nawigacji.

2. Na stronie **Aktywni użytkownicy** wybierz **pozycję Dodaj użytkownika** w górnej części strony, a następnie na panelu **Dodawanie użytkownika** wprowadź nazwę i inne informacje.

3. W sekcji **Licencje produktów** zaznacz pole wyboru **Microsoft 365 Business Premium (bez dostępu administracyjnego).**

4. W sekcji **Ustawienia opcjonalne** pozostaw domyślny przycisk radiowy wybrany dla **pozycji Użytkownik (brak dostępu do centrum administracyjnego).**

5. Zakończ i przejrzyj ustawienia, a następnie wybierz pozycję **Zakończ dodawanie** , aby potwierdzić szczegóły.

## <a name="protect-admin-accounts"></a>Ochrona kont administratorów

Aby chronić wszystkie konta administratorów, postępuj zgodnie z następującymi zaleceniami:

- Wymagaj, aby wszystkie konta administratorów używały uwierzytelniania bez hasła (na przykład Windows Hello lub aplikacji uwierzytelniacza) lub uwierzytelniania wieloskładnikowego. Aby dowiedzieć się więcej o tym, dlaczego uwierzytelnianie bez hasła jest ważne, zobacz [oficjalny dokument dotyczący zabezpieczeń firmy Microsoft: ochrona bez hasła](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2KEup).

- Unikaj używania uprawnień niestandardowych dla administratorów. Zamiast udzielać uprawnień określonym użytkownikom, przypisz uprawnienia za pośrednictwem ról w usłudze Azure Active Directory (Azure AD). Ponadto przyznaj dostęp tylko do danych i operacji potrzebnych do wykonania zadania. [Dowiedz się więcej o rolach o najniższych uprawnieniach w Azure AD](/azure/active-directory/roles/delegate-by-task).

- Użyj wbudowanych ról do przypisywania uprawnień tam, gdzie to możliwe. Kontrola dostępu oparta na rolach (RBAC) platformy Azure ma kilka wbudowanych ról, których można użyć. [Dowiedz się więcej na temat Azure AD wbudowanych ról](/azure/active-directory/roles/permissions-reference).

## <a name="additional-recommendations"></a>Dodatkowe zalecenia

- Przed użyciem kont administratorów zamknij wszystkie niepowiązane sesje przeglądarki i aplikacje, w tym osobiste konta e-mail. Można również używać w oknach przeglądarki prywatnej lub incognito.

- Po wykonaniu zadań administratora wyloguj się z sesji przeglądarki.

## <a name="next-objective"></a>Następny cel

Wykonaj kroki, aby [włączyć ustawienia domyślne zabezpieczeń](m365bp-conditional-access.md).

