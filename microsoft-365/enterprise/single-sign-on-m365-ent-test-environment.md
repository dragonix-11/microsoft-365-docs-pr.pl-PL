---
title: Bezproblemowe logowanie pojedyncze w usłudze Azure AD w środowisku Microsoft 365 testowym
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Podsumowanie: Skonfiguruj i przetestuj bezproblemowe logowanie pojedyncze usługi Azure AD w środowisku Microsoft 365 testowym.'
ms.openlocfilehash: 4a420da5251ecef900f2efe9573db1d51a6bd597
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988009"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Bezproblemowe logowanie pojedyncze w usłudze Azure AD w środowisku Microsoft 365 testowym

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

Bezproblemowe logowanie jednokrotne Sign-On w usłudze Azure AD (bezproblemowe logowanie jednokrotne) automatycznie logowania użytkowników, gdy znajdują się na swoich komputerach lub urządzeniach połączonych z ich siecią organizacji. Bezproblemowe logowanie jednokrotne w usłudze Azure AD zapewnia użytkownikom łatwy dostęp do aplikacji opartych na chmurze bez konieczności wytłaniania żadnych dodatkowych składników lokalnych.

W tym artykule opisano, jak skonfigurować środowisko Microsoft 365 testowego dla bezproblemowego logowania jednokrotnego usługi Azure AD.

Konfigurowanie bezproblemowego logowania jednokrotnego usługi Azure AD obejmuje dwie fazy:
- [Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku testowania Microsoft 365 hasła](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Etap 2. Konfigurowanie logowania jednokrotnego usługi Azure AD Połączenie w aplikacji APP1 dla bezproblemowego logowania jednokrotnego w usłudze Azure AD](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku testowania Microsoft 365 hasła

Postępuj zgodnie z instrukcjami [w te dotyczące synchronizacji skrótów haseł, aby uzyskać Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

Wynikowa konfiguracja wygląda następująco:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowania skrótów haseł.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z:
  
- Subskrypcja Microsoft 365 E5 próbna lub płatna.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w aplikacji APP1 w celu okresowego synchronizowania domeny TESTLAB Usługi domenowe w usłudze Active Directory (AD DS) z dzierżawą usługi Azure AD subskrypcji usługi Microsoft 365.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Etap 2. Konfigurowanie logowania jednokrotnego usługi Azure AD Połączenie w aplikacji APP1 dla bezproblemowego logowania jednokrotnego w usłudze Azure AD

W tej fazie skonfiguruj narzędzie Azure AD Połączenie w aplikacji APP1 dla bezproblemowego logowania jednokrotnego usługi Azure AD, a następnie sprawdź, czy działa.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurowanie usługi Azure AD Połączenie w aplikacji APP1

1. W portalu [Azure zaloguj](https://portal.azure.com) się przy użyciu konta administratora globalnego, a następnie połącz się z aplikacją APP1 za pomocą konta TESTLAB\User1.

2. Na komputerze stacjonarnym APP1 uruchom usługę Azure AD Połączenie.

3. Na stronie **powitałej** wybierz pozycję **Konfiguruj**.

4. Na stronie **Dodatkowe zadania** wybierz pozycję **Zmień logowanie użytkownika**, a następnie wybierz pozycję **Dalej**.

5. Na stronie **Połączenie do usługi Azure AD** wprowadź poświadczenia konta administratora globalnego, a następnie wybierz pozycję **Dalej**.

6. Na stronie **Logowanie użytkownika wybierz** pozycję **Włącz logowanie pojedyncze**, a następnie wybierz pozycję **Dalej**.

7. Na stronie **Włączanie logowania pojedynczego** wybierz pozycję **Wprowadź poświadczenia**.

8. W **Zabezpieczenia Windows** dialogowym Wprowadź nazwę **użytkownika użytkownik1** i hasło do konta użytkownika użytkownik1, wybierz przycisk **OK**, a następnie wybierz przycisk **Dalej**.

9. Na stronie **Ready to Configure (Gotowe do konfigurowania** ) wybierz pozycję **Configure (Konfiguruj**).

10. Na stronie **Ukończono konfigurację** wybierz pozycję **Zakończ**.

11. W portalu Azure Portal w okienku po lewej stronie wybierz pozycję **Azure Active Directory** >  **Azure AD Połączenie**. Sprawdź, czy funkcja **bezproblemowego logowania pojedynczego** jest wyświetlana jako **Włączona**.

Następnie przetestuj możliwość zalogowania się do swojej subskrypcji przy użyciu <strong>user1@testlab.</strong>\<*your public domain*> nazwę użytkownika konta Użytkownik1.

1. W programie Internet Explorer w aplikacji APP1 wybierz ikonę ustawień, a następnie wybierz pozycję **Opcje internetowe**.
 
2. W **obszarze Opcje** internetowe wybierz **kartę** Zabezpieczenia.

3. Wybierz **pozycję Lokalny intranet**, a następnie wybierz pozycję **Witryny**.

4. W **lokalnym intranecie** wybierz pozycję **Zaawansowane**.

5. W **witrynie Add this website to the zone** (Dodaj tę **witrynę sieci Web do strefy) wprowadź adres https <span>://</span>autologon.microsoftazuread-sso.com**, a następnie wybierz **pozycję** **AddCloseOKOK** >  >  > .

6. Wyloguj się, a następnie zaloguj się ponownie, tym razem określając inne konto.

7. Po wyświetleniu monitu o zalogowanie się określ user1@testlab <strong>.</strong>\<*your public domain*> , a następnie wybierz przycisk **Dalej**. Pomyślnie zaloguj się jako użytkownik1 bez monitowania o hasło. Jest to dowód na to, że bezproblemowe logowanie jednokrotne usługi Azure AD działa.

Użytkownik1 ma uprawnienia administratora domeny dla domeny TESTLAB AD DS, ale nie jest administratorem globalnym usługi Azure AD. Dlatego nie **zobaczysz ikony Administrator** jako opcji.

Oto wynikowa konfiguracja:

![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania przekazać.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Ta konfiguracja składa się z:

- A Microsoft 365 E5 trial or paid subscriptions with the DNS domain testlab.\<*your domain name*> zarejestrowano.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w aplikacji APP1 w celu zsynchronizowania listy kont i grup z dzierżawy usługi Azure AD twojej subskrypcji usługi Microsoft 365 do domeny AD DS TESTLAB.
- Bezproblemowe logowanie jednokrotne usługi Azure AD jest włączone, dzięki czemu komputery w symulowanym intranecie mogą logować się Microsoft 365 w chmurze bez określania hasła do konta użytkownika.

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)