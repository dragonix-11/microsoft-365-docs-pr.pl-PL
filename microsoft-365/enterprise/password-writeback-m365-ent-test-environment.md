---
title: Writeback password for your Microsoft 365 test environment
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/22/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Podsumowanie: Skonfiguruj pisanie zwrotne haseł w środowisku Microsoft 365 testowym.'
ms.openlocfilehash: 0c0660008aea4a676da4be3c13e8d5c15cb3a51d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973656"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Writeback password for your Microsoft 365 test environment

*Ten przewodnik laboratorium testowego może być używany tylko do Microsoft 365 testowych w przedsiębiorstwie.*

Użytkownicy mogą używać funkcji zapisu zwrotnego haseł, aby aktualizować swoje hasła za pośrednictwem usługi Azure Active Directory (Azure AD), która jest następnie replikowana do folderu Usługi domenowe w usłudze Active Directory (AD DS). Dzięki zapisywaniu hasła użytkownicy nie muszą aktualizować swoich haseł za pośrednictwem lokalnego portalu, AD DS w którym są przechowywane ich oryginalne konta użytkowników. Pomoże to użytkownikom roamingowym lub zdalnym, którzy nie mają połączenia dostępu zdalnego ze swoją siecią lokalną.

W tym artykule opisano sposób konfigurowania środowiska Microsoft 365 testowego pod Microsoft 365 zapisu hasła.

Konfigurowanie środowiska testowego do pisania hasła obejmuje dwie fazy:
- [Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku Microsoft 365 testowym](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Etap 2. Włączanie funkcji zapisu hasła dla domeny AD DS TESTLAB](#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain)
  
![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Przewodnik laboratorium testowego dla przedsiębiorstw Microsoft 365 stos przewodników [laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku Microsoft 365 testowym

Najpierw postępuj zgodnie z instrukcjami [dotyczącymi synchronizacji skrótów haseł](password-hash-sync-m365-ent-test-environment.md). Wynikowa konfiguracja wygląda następująco:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowania skrótów haseł.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z:
  
- Subskrypcja Microsoft 365 E5 próbna lub płatna.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w aplikacji APP1 w celu zsynchronizowania domeny testLAB AD DS z dzierżawą usługi Azure AD twojej subskrypcji Microsoft 365 usługi.

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>Etap 2. Włączanie funkcji zapisu hasła dla domeny testlab AD DS TESTLAB

Najpierw skonfiguruj konto użytkownika 1 z rolą administratora globalnego.

1. W [centrum administracyjne platformy Microsoft 365 zaloguj](https://portal.microsoft.com) się przy użyciu konta administratora globalnego.

2. Wybierz **pozycję Aktywni użytkownicy**.
 
3. Na **stronie Aktywni** użytkownicy wybierz **konto użytkownika 1**

4. W **okienku użytkownik1** wybierz pozycję **Edytuj obok** opcji **Role**.

5. W **okienku Edytuj role użytkowników** dla użytkownika użytkownik1 wybierz pozycję **Administrator globalny**, wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Zamknij**.

Następnie skonfiguruj konto użytkownika 1 przy użyciu ustawień zabezpieczeń, które umożliwiają mu zmienianie haseł w imieniu innych użytkowników w domenie TESTLAB AD DS.

1. W portalu [Azure zaloguj](https://portal.azure.com) się przy użyciu konta administratora globalnego, a następnie połącz się z aplikacją APP1 za pomocą konta TESTLAB\User1.

2. Na pulpicie aplikacji APP1 wybierz **pozycję Start**, **wprowadź aktywnego**, a następnie wybierz pozycję Użytkownicy **i komputery usługi Active Directory**.

3. Na pasku menu wybierz pozycję **Widok**. Jeśli **funkcje zaawansowane** nie są włączone, zaznacz je, aby je włączyć.

4. W drzewie okienka wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy) domenę, wybierz pozycję **Właściwości, a** następnie wybierz **kartę** Zabezpieczenia.

5. Wybierz **pozycję Zaawansowane**.

6. Na karcie **Uprawnienia** wybierz pozycję **Dodaj**.

7. Wybierz **pozycję Wybierz kapitał**, wprowadź **nazwę Użytkownik1**, a następnie wybierz przycisk **OK**.

8. W **ustawieniach Dotyczy** zaznacz pole **wyboru Obiekt Użytkownik szybki**.

9. W **obszarze** Uprawnienia wybierz następujące elementy:

    - **Zmień hasło**
    - **Resetuj hasło**

10. W **obszarze** Właściwości wybierz następujące polecenie:
    - **Write lockoutTime**
    - **Pisanie pwdLastSet**

11. Wybierz **przycisk OK** trzy razy, aby zapisać zmiany.

12. Zamknij **folder Użytkownicy i komputery usługi Active Directory**.

Następnie skonfiguruj usługę Azure AD, Połączenie w aplikacji APP1 na podstawie zapisu hasła.

1. W razie potrzeby połącz się z aplikacją APP1 przy użyciu konta TESTLAB\User1.

2. Na komputerze z aplikacją APP1 kliknij dwukrotnie pozycję **Azure AD Połączenie**.

3. Na stronie **powitałej** wybierz pozycję **Konfiguruj**.

4. Na stronie **Dodatkowe zadania** wybierz pozycję **Dostosuj opcje synchronizacji**, a następnie wybierz pozycję **Dalej**.

5. Na stronie **Połączenie do usługi Azure AD** wprowadź poświadczenia konta administratora globalnego, a następnie wybierz pozycję **Dalej**.

6. Na stronach **Połączenie i** **Filtrowanie domeny/użytkownika** wybierz pozycję **Dalej**.

7. Na stronie **Funkcje opcjonalne** wybierz pozycję **Funkcja zapisu hasła**, a następnie wybierz pozycję **Dalej**.

8. Na stronie **Wszystko gotowe do skonfigurowania** wybierz pozycję **Konfiguruj** i poczekaj na ukończenie procesu.

9. Po zakończeniu konfiguracji wybierz pozycję **Zakończ**.

Teraz możesz rozpocząć testowanie funkcji zapisu hasła dla użytkowników komputerów, które nie są połączone z siecią wirtualną w symulowanym intranecie.

Wynikowa konfiguracja wygląda następująco:

![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania przekazać.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Ta konfiguracja składa się z:

- A Microsoft 365 E5 trial or paid subscriptions with the DNS domain TESTLAB.\<*your domain name*> zarejestrowano.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w aplikacji APP1 w celu zsynchronizowania listy kont i grup z dzierżawy usługi Azure AD twojej subskrypcji usługi Microsoft 365 do domeny AD DS TESTLAB.
- Funkcja zapisu hasła jest włączona, dzięki czemu użytkownicy mogą zmieniać swoje hasła za pośrednictwem usługi Azure AD bez konieczności połączenia z uproszczonym intranetem.

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Microsoft 365 — omówienie przedsiębiorstwa](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)