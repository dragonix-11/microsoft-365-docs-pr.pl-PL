---
title: Ochrona kont administratorów globalnych w Microsoft 365 dla środowiska testowego przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Wykonaj te kroki, aby chronić konta administratorów globalnych w Microsoft 365 dla środowiska testowego przedsiębiorstwa.
ms.openlocfilehash: bf053b9767aea4a290c5357d6309c57677a36cad
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098279"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Ochrona kont administratorów globalnych w Microsoft 365 dla środowiska testowego przedsiębiorstwa

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

Możesz zapobiec atakom cyfrowym na organizację, zapewniając, że konta administratorów są jak najbardziej bezpieczne. 

W tym artykule opisano sposób używania zasad dostępu warunkowego Azure Active Directory (Azure AD) w celu ochrony kont administratorów globalnych.

Ochrona kont administratorów globalnych w Microsoft 365 dla środowiska testowego przedsiębiorstwa obejmuje dwie fazy:
- [Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Faza 2. Konfigurowanie zasad dostępu warunkowego](#phase-2-configure-conditional-access-policies)

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz przetestować ochronę konta administratora globalnego w sposób uproszczony z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz przetestować ochronę konta administratora globalnego w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie ochrony konta administratora globalnego nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla Active Directory Domain Services (AD DS). Jest ona dostępna tutaj jako opcja, dzięki czemu można przetestować ochronę konta administratora globalnego i eksperymentować z nią w środowisku reprezentującym typową organizację. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Faza 2. Konfigurowanie zasad dostępu warunkowego

Najpierw utwórz nowe konto użytkownika jako dedykowany administrator globalny.

1. Na osobnej karcie otwórz [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/).
2. Wybierz pozycję **UżytkownicyAktywni** >  użytkownicy, a następnie wybierz **pozycję Dodaj użytkownika**.
3. W okienku **Dodawanie użytkownika** wprowadź wartość **DedicatedAdmin** w polach **Imię**, **Nazwa wyświetlana** i **Nazwa użytkownika** .
4. Wybierz pozycję **Hasło**, wybierz pozycję **Pozwól mi utworzyć hasło**, a następnie wprowadź silne hasło. Zarejestruj hasło dla tego nowego konta w bezpiecznej lokalizacji.
5. Wybierz pozycję **Dalej**.
6. W okienku **Przypisywanie licencji produktów** wybierz pozycję **Microsoft 365 E5**, a następnie wybierz pozycję **Dalej**.
7. W okienku **Ustawienia opcjonalne** wybierz pozycję **RoleDministrator** >  dostępu Do  > **centrumGlobal** **adminNext** > .
8. W okienku **Gotowe** wybierz pozycję **Zakończ dodawanie**, a następnie wybierz pozycję **Zamknij**.

Następnie utwórz nową grupę o nazwie GlobalAdmins i dodaj do niej konto DedicatedAdmin.

1. Na karcie **Centrum administracyjne platformy Microsoft 365** wybierz pozycję **Grupy** w lewym obszarze nawigacji, a następnie wybierz pozycję **Grupy**.
2. Wybierz **pozycję Dodaj grupę**.
3. W okienku **Wybierz typ grupy** wybierz pozycję **Zabezpieczenia**, a następnie wybierz pozycję **Dalej**.
4. W **okienku Konfigurowanie podstaw** wybierz pozycję **Utwórz grupę**, a następnie wybierz pozycję **Zamknij**.
5. W okienku **Przejrzyj i zakończ dodawanie grupy** wprowadź ciąg **GlobalAdmins**, a następnie wybierz pozycję **Dalej**.
7. Na liście grup wybierz grupę **GlobalAdmins** .
8. W okienku **GlobalAdmins** wybierz pozycję **Członkowie**, a następnie wybierz pozycję **Wyświetl wszystkie elementy członkowskie i zarządzaj nimi**.
9. W okienku **GlobalAdmins** wybierz pozycję **Dodaj członków**, wybierz konto **DedicatedAdmin** i konto administratora globalnego, a następnie wybierz pozycję **SaveCloseClose** >  > .

Następnie utwórz zasady dostępu warunkowego, aby wymagać uwierzytelniania wieloskładnikowego dla kont administratorów globalnych i odmówić uwierzytelniania, jeśli ryzyko logowania jest średnie lub wysokie.

Te pierwsze zasady wymagają, aby wszystkie konta administratorów globalnych używały uwierzytelniania wieloskładnikowego.

1. Na nowej karcie przeglądarki przejdź do [https://portal.azure.com](https://portal.azure.com)pozycji .
2. Kliknij **pozycję Azure Active Directory** >  **SecurityDostęp** >  **warunkowy**.
3. W okienku **Dostęp warunkowy — zasady** wybierz pozycję **Zasady punktu odniesienia: Wymagaj uwierzytelniania wieloskładnikowego dla administratorów (wersja zapoznawcza).**
4. W okienku **Zasady punktu odniesienia** wybierz pozycję **Użyj zasad natychmiast > Zapisz**.

Te drugie zasady blokują dostęp do uwierzytelniania konta administratora globalnego, gdy ryzyko logowania jest średnie lub wysokie.

1. W okienku **Dostęp warunkowy — zasady** wybierz pozycję **Nowe zasady**.
2. W okienku **Nowy** wprowadź ciąg **Administratorzy globalni** w **polu Nazwa**.
3. W sekcji **Przypisania** wybierz pozycję **Użytkownicy i grupy**.
4. Na karcie **Dołączanie** w okienku **Użytkownicy i grupy** wybierz pozycję **Wybierz użytkowników i** **grupyUżytkownicy** >  i **grupyWybierz** > .
5. W okienku **Wybierz** wybierz grupę **GlobalAdmins**, a następnie wybierz pozycję **WybierzDodaj** > .
6. W sekcji **Przypisania** wybierz pozycję **Warunki**.
7. W okienku **Warunki** wybierz pozycję **Ryzyko logowania**, wybierz pozycję **Tak** dla **pozycji Konfiguruj**, wybierz pozycję **Wysokie** i **Średnie**, a następnie wybierz **pozycję Wybierz** i **gotowe**.
8. W sekcji **Kontrolki dostępu** w okienku **Nowy** wybierz pozycję **Udziel**.
9. W okienku **Udzielanie** wybierz pozycję **Blokuj dostęp**, a następnie wybierz pozycję **Wybierz**.
10. W okienku **Nowy** wybierz pozycję **Włączone** w **obszarze Włącz zasady**, a następnie wybierz pozycję **Utwórz**.
11. Zamknij karty **Azure Portal** i **Centrum administracyjne platformy Microsoft 365**.

Aby przetestować pierwsze zasady, wyloguj się i zaloguj się przy użyciu konta DedicatedAdmin. Powinien zostać wyświetlony monit o skonfigurowanie uwierzytelniania wieloskładnikowego. Pokazuje to, że są stosowane pierwsze zasady.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)