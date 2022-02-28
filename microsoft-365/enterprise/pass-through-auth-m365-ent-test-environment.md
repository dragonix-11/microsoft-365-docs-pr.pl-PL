---
title: Uwierzytelnianie pass-through w środowisku Microsoft 365 testowym
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
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'Podsumowanie: Skonfiguruj uwierzytelnianie pass-through w środowisku testowym Microsoft 365 testowym.'
ms.openlocfilehash: dcc23662683ffaf65a0ec5fa3698f729dc215af7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983798"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>Uwierzytelnianie pass-through w środowisku Microsoft 365 testowym

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

Organizacje, które chcą bezpośrednio korzystać ze swojej lokalnej infrastruktury usług Usługi domenowe w usłudze Active Directory (AD DS) na AD DS uwierzytelniania do usług i aplikacji opartych na chmurze firmy Microsoft, mogą korzystać z uwierzytelniania przekazać. W tym artykule opisano sposób konfigurowania środowiska testowego Microsoft 365 na podstawie uwierzytelniania pass-through, co spowoduje następującą konfigurację:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania przekazać.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
Istnieją dwie fazy konfigurowania tego środowiska testowego:

1.    Utwórz symulowane Microsoft 365 testowe przedsiębiorstwa z synchronizacją skrótów haseł.
2.    Skonfiguruj usługę Azure AD Połączenie w aplikacji APP1 na podstawie uwierzytelniania przekazać.
    
![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kliknij [tutaj,](../downloads/Microsoft365EnterpriseTLGStack.pdf) aby uzyskać wizualną mapę do wszystkich artykułów w p Microsoft 365 przewodników laboratorium testowego dla przedsiębiorstw.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku testowania Microsoft 365 hasła

Postępuj zgodnie z instrukcjami [w te dotyczące synchronizacji skrótów haseł, aby uzyskać Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Oto wynikowa konfiguracja.
  
![Symulowane przedsiębiorstwo ze środowiskiem testowania skrótów haseł.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z: 
  
- Microsoft 365 E5 wersji próbnej lub płatnej subskrypcji.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure. Usługa Azure AD Połączenie działa w aplikacji APP1 w celu synchronizowania domeny usługi TESTLAB AD DS z dzierżawą usługi Azure AD subskrypcji usługi Microsoft 365 okresowe.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>Etap 2. Konfigurowanie usługi Azure AD Połączenie w aplikacji APP1 na podstawie uwierzytelniania przekazać

W tej fazie konfigurujesz usługę Azure AD, która Połączenie w aplikacji APP1, w celu używania uwierzytelniania przekażego, a następnie sprawdzasz, czy działa.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurowanie usługi Azure AD Połączenie w aplikacji APP1

1.    W portalu [Azure zaloguj](https://portal.azure.com) się przy użyciu konta administratora globalnego, a następnie połącz się z aplikacją APP1 za pomocą konta TESTLAB\User1.

2.    Na komputerze z aplikacją APP1 uruchom usługę Azure AD Połączenie.

3.    Na stronie **powitałej** kliknij pozycję **Konfiguruj**.

4.    Na stronie Dodatkowe zadania kliknij pozycję **Zmień logowanie użytkownika**, a następnie kliknij przycisk **Dalej**.

5.    Na stronie **Połączenie do usługi Azure AD** wpisz poświadczenia konta administratora globalnego, a następnie kliknij przycisk **Dalej**.

6.    Na stronie **Logowanie użytkownika kliknij** pozycję Uwierzytelnianie **przekaż**, a następnie kliknij przycisk **Dalej**.

7.    Na **stronie Wszystko gotowe do skonfigurowania** kliknij pozycję **Konfiguruj**.

8.    Na stronie **Ukończono konfigurację** kliknij pozycję **Zakończ**.

9.    W portalu Azure Portal w okienku po lewej stronie kliknij pozycję Azure Active Directory > **Azure AD Połączenie**. Sprawdź, czy **funkcja uwierzytelniania przekaż** jest widoczna jako **Włączona**.

10.    Kliknij **pozycję Uwierzytelnianie przekaż**. Okienko **uwierzytelniania przekazać** zawiera listę serwerów, na których są zainstalowane agentów uwierzytelniania. Na liście powinien być wyświetlony app1. Zamknij okienko **uwierzytelniania przekaż** .

Następnie przetestuj możliwość zalogowania się do swojej subskrypcji przy użyciu <strong>user1@testlab.</strong>\<your public domain> nazwę użytkownika konta Użytkownik1.

1. W aplikacji APP1 wyloguj się, a następnie zaloguj się ponownie, tym razem określając inne konto.

2. Po wyświetleniu monitu o podanie nazwy użytkownika i hasła określ, <strong>user1@testlab.</strong>\<your public domain> i hasło użytkownika Użytkownik1. Należy pomyślnie zalogować się jako Użytkownik1.

Użytkownik1 ma uprawnienia administratora domeny dla domeny TESTLAB AD DS, ale nie jest administratorem globalnym. Dlatego nie **zobaczysz ikony Administrator** jako opcji.

Oto wynikowa konfiguracja:

![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania przekazać.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
Ta konfiguracja składa się z:

- A Microsoft 365 E5 trial or paid subscriptions with the DNS domain testlab.\<your domain name> zarejestrowano.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure. Agent uwierzytelniania działa w aplikacji APP1 w celu obsługi żądań uwierzytelniania przekazać z dzierżawy usługi Azure AD Microsoft 365 subskrypcji usługi.

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)