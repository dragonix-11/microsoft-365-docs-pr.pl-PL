---
title: Ochrona kont administratora globalnego w środowisku Microsoft 365 testowania przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Aby chronić konta administratora globalnego w środowisku testowania Microsoft 365 przedsiębiorstwa, należy wykonać poniższe czynności.
ms.openlocfilehash: a759d4e8720216019886f33ca0df7325b5209930
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013879"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Ochrona kont administratora globalnego w środowisku Microsoft 365 testowania przedsiębiorstwa

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

Możesz zapobiec atakom cyfrowym na Twoją organizację, upewniając się, że Twoje konta administratora są jak najbezpieczniej. 

W tym artykule opisano, jak używać zasad Azure Active Directory dostępu warunkowego (Azure AD) w celu ochrony kont administratora globalnego.

Ochrona kont administratora globalnego w środowisku Microsoft 365 w środowisku testowania przedsiębiorstwa składa się z dwóch etapów:
- [Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Etap 2. Konfigurowanie zasad dostępu warunkowego](#phase-2-configure-conditional-access-policies)

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz przetestować ochronę konta administratora globalnego w sposób bardzo podstawowy z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w teście [Konfiguracja podstawowa.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Jeśli chcesz przetestować ochronę konta administratora globalnego w symulowanym przedsiębiorstwie, wykonaj instrukcje uwierzytelniania [pass-through](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie ochrony konta administratora globalnego nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów na Usługi domenowe w usłudze Active Directory (AD DS). Jest on podany jako opcja, która umożliwia przetestowanie ochrony konta administratora globalnego i eksperymentowanie z nim w środowisku reprezentującym typową organizację. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Etap 2. Konfigurowanie zasad dostępu warunkowego

Najpierw utwórz nowe konto użytkownika jako dedykowanego administratora globalnego.

1. Na osobnej karcie [otwórz centrum administracyjne platformy Microsoft 365.](https://admin.microsoft.com/)
2. Wybierz **pozycję** **UżytkownicyAktywowanie** >  użytkowników, a następnie wybierz **pozycję Dodaj użytkownika**.
3. W **okienku Dodaj** użytkownika wprowadź nazwę **DedicatedAdmin** w **polach Imię**, **Nazwa wyświetlana** i **Nazwa** użytkownika.
4. Wybierz **pozycję** Hasło, **wybierz pozycję Pozwól mi utworzyć hasło**, a następnie wprowadź silne hasło. Zanotuj hasło dla tego nowego konta w bezpiecznym miejscu.
5. Wybierz pozycję **Dalej**.
6. W **okienku Przypisywanie licencji produktu** **wybierz pozycję Microsoft 365 E5**, a następnie wybierz pozycję **Dalej**.
7. W **okienku Ustawienia opcjonalne** wybierz pozycję **RoleAdmin** >  **center dostępGlobal** >  **adminNext** > .
8. W **okienku Prawie gotowe wybierz** pozycję Zakończ **dodawanie**, a następnie wybierz pozycję **Zamknij**.

Następnie utwórz nową grupę o nazwie GlobalAdmins i dodaj do niego konto DedicatedAdmin.

1. Na karcie **centrum administracyjne platformy Microsoft 365** grupy w lewym obszarze nawigacji,  a następnie wybierz pozycję **Grupy**.
2. Wybierz **pozycję Dodaj grupę**.
3. W **okienku Wybierz typ grupy** wybierz pozycję **Zabezpieczenia**, a następnie wybierz pozycję **Dalej**.
4. W **okienku Konfigurowanie podstawowych funkcji** wybierz pozycję **Utwórz grupę**, a następnie wybierz pozycję **Zamknij**.
5. W **okienku Przeglądanie i kończanie dodawania grupy** wprowadź nazwę **GlobalAdmins**, a następnie wybierz pozycję **Dalej**.
7. Na liście grup wybierz grupę **GlobalAdmins** .
8. W **okienku GlobalAdmins** wybierz pozycję **Członkowie**, a następnie wybierz pozycję **Wyświetl wszystkich członków i zarządzaj nimi**.
9. W **okienku GlobalAdmins** wybierz pozycję Dodaj **członków, wybierz** konto **DedicatedAdmin** i konto administratora globalnego, a następnie wybierz **pozycję SaveCloseCloseClose** >  > .

Następnie należy utworzyć zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego dla kont administratora globalnego oraz odmawiać uwierzytelniania w przypadku średniego lub wysokiego ryzyka związanego z logowaniem.

Te pierwsze zasady wymagają, aby wszystkie konta administratora globalnego korzystały z uwierzytelniania MFA.

1. Na nowej karcie przeglądarki przejdź do .[https://portal.azure.com](https://portal.azure.com)
2. Kliknij **Azure Active Directory** >  **SecurityConditional** >  Access.
3. W **okienku Dostęp warunkowy —** zasady wybierz pozycję Zasady planu bazowego **: Wymagaj uwierzytelniania WIELOSKŁADNIKowego dla administratorów (wersja Preview)**.
4. W **okienku Zasady planu** bazowego wybierz **pozycję Użyj zasad natychmiast > Zapisz**.

Te drugie zasady blokują dostęp do uwierzytelniania konta administratora globalnego, gdy ryzyko logowania jest średnie lub wysokie.

1. W **okienku Dostęp warunkowy —** zasady wybierz pozycję **Nowe zasady**.
2. W **okienku Nowy** wprowadź wartość **Administratorzy globalni w** **nazwach**.
3. W sekcji **Zadania wybierz** pozycję **Użytkownicy i grupy**.
4. Na karcie **Dołączanie** **okienka Użytkownicy i** grupy wybierz pozycję **Zaznacz użytkowników i** >  **grupyUżytkowcy i grupyZaznaczanie** > .
5. W **okienku** Zaznaczanie wybierz **grupę GlobalAdmins**, a następnie wybierz **pozycję SelectDone** > .
6. W **sekcji Zadania** wybierz pozycję **Warunki**.
7. W **okienku Warunki** wybierz pozycję **Ryzyko** logowania, dla opcji Konfiguracja  wybierz pozycję **Tak, wybierz** pozycję Wysoki i **średni, a** następnie wybierz **pozycję Wybierz** i **gotowe**.
8. W sekcji **Kontrolki programu Access** w **okienku Nowy** wybierz pozycję **U grant**.
9. W **okienku Udzielanie** wybierz pozycję **Zablokuj dostęp**, a następnie wybierz pozycję **Wybierz**.
10. W **okienku Nowy** wybierz pozycję **Włącz dla** **opcji Włącz zasady**, a następnie wybierz pozycję **Utwórz**.
11. Zamknij Portal **Azure i** **centrum administracyjne platformy Microsoft 365** karty.

Aby przetestować pierwsze zasady, wyloguj się i zaloguj się przy użyciu konta DedicatedAdmin. Powinien zostać wyświetlony monit o skonfigurowanie uwierzytelniania MFA. Pokazuje to, że są stosowane pierwsze zasady.

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)