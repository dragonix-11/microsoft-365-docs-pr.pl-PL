---
title: Bezproblemowe logowanie jednokrotne usługi Azure AD dla środowiska testowego Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/21/2019
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
description: 'Podsumowanie: Konfigurowanie i testowanie bezproblemowego logowania jednokrotnego usługi Azure AD dla środowiska testowego Microsoft 365.'
ms.openlocfilehash: 2d6af0600044dea59cbcdd9ee51f76c061e3dcd7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093333"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Bezproblemowe logowanie jednokrotne usługi Azure AD dla środowiska testowego Microsoft 365

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

Usługa Azure AD Seamless Single Sign-On (Seamless SSO) automatycznie loguje użytkowników, gdy znajdują się na komputerach lub urządzeniach połączonych z siecią organizacji. Bezproblemowe logowanie jednokrotne usługi Azure AD zapewnia użytkownikom łatwy dostęp do aplikacji opartych na chmurze bez konieczności używania dodatkowych składników lokalnych.

W tym artykule opisano sposób konfigurowania środowiska testowego Microsoft 365 dla bezproblemowego logowania jednokrotnego usługi Azure AD.

Konfigurowanie bezproblemowego logowania jednokrotnego usługi Azure AD obejmuje dwie fazy:
- [Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Faza 2. Konfigurowanie usługi Azure AD Połączenie w usłudze APP1 dla bezproblemowego logowania jednokrotnego usługi Azure AD](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365

Postępuj zgodnie z instrukcjami [synchronizacji skrótów haseł dla Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

Wynikowe konfiguracje wyglądają następująco:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowym synchronizacji skrótów haseł.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z następujących elementów:
  
- Subskrypcja Microsoft 365 E5 wersji próbnej lub płatnej.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w usłudze APP1, aby okresowo synchronizować domenę Active Directory Domain Services TESTLAB (AD DS) z dzierżawą usługi Azure AD subskrypcji Microsoft 365.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Faza 2. Konfigurowanie usługi Azure AD Połączenie w usłudze APP1 dla bezproblemowego logowania jednokrotnego usługi Azure AD

W tej fazie skonfiguruj usługę Azure AD Połączenie w usłudze APP1 dla bezproblemowego logowania jednokrotnego usługi Azure AD, a następnie sprawdź, czy działa.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurowanie Połączenie usługi Azure AD w aplikacji APP1

1. Z [poziomu Azure Portal](https://portal.azure.com) zaloguj się przy użyciu konta administratora globalnego, a następnie połącz się z aplikacją APP1 przy użyciu konta TESTLAB\User1.

2. Na pulpicie app1 uruchom usługę Azure AD Połączenie.

3. Na **stronie Powitalna** wybierz pozycję **Konfiguruj**.

4. Na stronie **Dodatkowe zadania** wybierz pozycję **Zmień logowanie użytkownika**, a następnie wybierz pozycję **Dalej**.

5. Na stronie **Połączenie do usługi Azure AD** wprowadź poświadczenia konta administratora globalnego, a następnie wybierz pozycję **Dalej**.

6. Na stronie **Logowanie użytkownika** wybierz pozycję **Włącz logowanie jednokrotne**, a następnie wybierz pozycję **Dalej**.

7. Na stronie **Włącz logowanie jednokrotne** wybierz pozycję **Wprowadź poświadczenia**.

8. W oknie dialogowym **Zabezpieczenia Windows** wprowadź **ciąg user1** i hasło konta użytkownika1, wybierz przycisk **OK**, a następnie wybierz pozycję **Dalej**.

9. Na stronie **Gotowe do skonfigurowania** wybierz pozycję **Konfiguruj**.

10. Na stronie **Konfiguracja ukończona** wybierz pozycję **Zakończ**.

11. W Azure Portal w okienku po lewej stronie wybierz pozycję **Azure Active Directory** >  **Azure AD Połączenie**. Sprawdź, czy funkcja **bezproblemowego logowania jednokrotnego** jest wyświetlana jako **Włączona**.

Następnie przetestuj możliwość logowania się do subskrypcji przy użyciu <strong>user1@testlab.</strong>\<*your public domain*> nazwa użytkownika konta User1.

1. W programie Internet Explorer w aplikacji APP1 wybierz ikonę ustawień, a następnie wybierz pozycję **Opcje internetowe**.
 
2. W **obszarze Opcje internetowe** wybierz kartę **Zabezpieczenia** .

3. Wybierz pozycję **Lokalny intranet**, a następnie wybierz pozycję **Witryny**.

4. W **lokalnym intranecie** wybierz pozycję **Zaawansowane**.

5. W **obszarze Dodaj tę witrynę internetową do strefy** wprowadź **ciąg https <span>://</span>autologon.microsoftazuread-sso.com**, wybierz pozycję **AddCloseOKOK** >  >  > .

6. Wyloguj się, a następnie zaloguj się ponownie, tym razem określając inne konto.

7. Po wyświetleniu monitu o zalogowanie określ <strong>user1@testlab.</strong>\<*your public domain*> nazwa, a następnie wybierz przycisk **Dalej**. Należy pomyślnie zalogować się jako Użytkownik1 bez monitowania o podanie hasła. To dowodzi, że bezproblemowe logowanie jednokrotne usługi Azure AD działa.

Zauważ, że chociaż użytkownik User1 ma uprawnienia administratora domeny dla domeny USŁUG AD DS TESTLAB, nie jest administratorem globalnym usługi Azure AD. W związku z tym ikona **Administrator** nie będzie wyświetlana jako opcja.

Oto twoja konfiguracja wyniku:

![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania z przekazywaniem.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Ta konfiguracja składa się z następujących elementów:

- Microsoft 365 E5 wersji próbnej lub płatnych subskrypcji z testlab domeny DNS.\<*your domain name*> Zarejestrowany.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w usłudze APP1, aby zsynchronizować listę kont i grup z dzierżawy usługi Azure AD subskrypcji Microsoft 365 z domeną usług AD DS TESTLAB.
- Bezproblemowe logowanie jednokrotne usługi Azure AD jest włączone, dzięki czemu komputery w symulowanym intranecie mogą logować się do Microsoft 365 zasobów w chmurze bez określania hasła konta użytkownika.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)