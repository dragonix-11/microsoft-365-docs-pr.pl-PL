---
title: Zapisywanie zwrotne haseł dla środowiska testowego Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Skonfiguruj zapisywanie zwrotne haseł dla środowiska testowego Microsoft 365.'
ms.openlocfilehash: 0477e2200db7252dcce4351b2f96298e075f3b29
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091110"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Zapisywanie zwrotne haseł dla środowiska testowego Microsoft 365

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

Użytkownicy mogą używać funkcji zapisywania zwrotnego haseł do aktualizowania swoich haseł za pośrednictwem usługi Azure Active Directory (Azure AD), która jest następnie replikowana do lokalnego Active Directory Domain Services (AD DS). W przypadku zapisywania zwrotnego haseł użytkownicy nie muszą aktualizować swoich haseł za pośrednictwem lokalnych usług AD DS, w których są przechowywane ich oryginalne konta użytkowników. Pomaga to użytkownikom mobilnym lub zdalnym, którzy nie mają połączenia dostępu zdalnego z siecią lokalną.

W tym artykule opisano sposób konfigurowania środowiska testowego Microsoft 365 na potrzeby zapisywania zwrotnego haseł.

Konfigurowanie środowiska testowego pod kątem zapisywania zwrotnego haseł obejmuje dwie fazy:
- [Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Faza 2. Włączanie zapisywania zwrotnego haseł dla domeny usług AD DS TESTLAB](#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain)
  
![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365

Najpierw postępuj zgodnie z instrukcjami [synchronizacji skrótów haseł](password-hash-sync-m365-ent-test-environment.md). Wynikowe konfiguracje wyglądają następująco:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowym synchronizacji skrótów haseł.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z następujących elementów:
  
- Subskrypcja Microsoft 365 E5 wersji próbnej lub płatnej.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w usłudze APP1, aby zsynchronizować domenę usług AD DS TESTLAB z dzierżawą usługi Azure AD subskrypcji Microsoft 365.

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>Faza 2. Włączanie zapisywania zwrotnego haseł dla domeny usług AD DS TESTLAB

Najpierw skonfiguruj konto użytkownika 1 z rolą administratora globalnego.

1. Z [poziomu Centrum administracyjne platformy Microsoft 365](https://portal.microsoft.com) zaloguj się przy użyciu konta administratora globalnego.

2. Wybierz pozycję **Aktywni użytkownicy**.
 
3. Na stronie **Aktywni użytkownicy** wybierz konto **użytkownika1** ,

4. W okienku **user1** wybierz pozycję **Edytuj** obok pozycji **Role**.

5. W okienku **Edytowanie ról użytkowników** dla użytkownika1 wybierz pozycję **administrator globalny**, wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Zamknij**.

Następnie skonfiguruj konto użytkownika 1 przy użyciu ustawień zabezpieczeń, które umożliwiają zmianę haseł w imieniu innych użytkowników w domenie usług AD DS TESTLAB.

1. Z [poziomu Azure Portal](https://portal.azure.com) zaloguj się przy użyciu konta administratora globalnego, a następnie połącz się z aplikacją APP1 przy użyciu konta TESTLAB\User1.

2. Na pulpicie aplikacji APP1 wybierz pozycję **Start**, wprowadź **wartość active**, a następnie wybierz **pozycję Użytkownicy i komputery usługi Active Directory**.

3. Na pasku menu wybierz pozycję **Widok**. Jeśli **funkcje zaawansowane** nie są włączone, wybierz je, aby je włączyć.

4. W okienku drzewa wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy) domenę, wybierz pozycję **Właściwości**, a następnie wybierz kartę **Zabezpieczenia** .

5. Wybierz pozycję **Zaawansowane**.

6. Na **karcie Uprawnienia** wybierz pozycję **Dodaj**.

7. Wybierz **pozycję Wybierz podmiot zabezpieczeń**, wprowadź **user1**, a następnie wybierz przycisk **OK**.

8. W **obszarze Dotyczy** wybierz pozycję **Obiekty użytkownika potomnego**.

9. W obszarze Uprawnienia wybierz następujące **opcje**:

    - **Zmienianie hasła**
    - **Resetuj hasło**

10. W obszarze **Właściwości** wybierz następujące opcje:
    - **Zapis lockoutTime**
    - **Napisz pwdLastSet**

11. Wybierz przycisk **OK** trzy razy, aby zapisać zmiany.

12. Zamknij **Użytkownicy i komputery usługi Active Directory**.

Następnie skonfiguruj usługę Azure AD Połączenie w usłudze APP1 pod kątem zapisywania zwrotnego haseł.

1. W razie potrzeby połącz się z aplikacją APP1 przy użyciu konta TESTLAB\User1.

2. Na pulpicie aplikacji APP1 kliknij dwukrotnie **usługę Azure AD Połączenie**.

3. Na **stronie Powitalna** wybierz pozycję **Konfiguruj**.

4. Na stronie **Dodatkowe zadania** wybierz pozycję **Dostosuj opcje synchronizacji**, a następnie wybierz pozycję **Dalej**.

5. Na stronie **Połączenie do usługi Azure AD** wprowadź poświadczenia konta administratora globalnego, a następnie wybierz pozycję **Dalej**.

6. Na **stronach filtrowania katalogów Połączenie** i **domeny/jednostki organizacyjnej** wybierz pozycję **Dalej**.

7. Na stronie **Funkcje opcjonalne** wybierz pozycję **Zapisywanie zwrotne haseł**, a następnie wybierz pozycję **Dalej**.

8. Na stronie **Gotowe do skonfigurowania** wybierz pozycję **Konfiguruj** i poczekaj na zakończenie procesu.

9. Po zakończeniu konfiguracji wybierz pozycję **Zakończ**.

Teraz możesz przetestować zapisywanie zwrotne haseł dla użytkowników na komputerach, które nie są połączone z siecią wirtualną symulowanego intranetu.

Wynikowe konfiguracje wyglądają następująco:

![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania z przekazywaniem.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Ta konfiguracja składa się z następujących elementów:

- Microsoft 365 E5 wersji próbnej lub płatnych subskrypcji z domeną DNS TESTLAB.\<*your domain name*> Zarejestrowany.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w usłudze APP1, aby zsynchronizować listę kont i grup z dzierżawy usługi Azure AD subskrypcji Microsoft 365 z domeną usług AD DS TESTLAB.
- Zapisywanie zwrotne haseł jest włączone, dzięki czemu użytkownicy mogą zmieniać swoje hasła za pośrednictwem usługi Azure AD bez konieczności nawiązywania połączenia z uproszczonym intranetem.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)