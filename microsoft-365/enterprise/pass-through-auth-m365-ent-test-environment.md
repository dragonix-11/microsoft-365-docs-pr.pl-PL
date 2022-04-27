---
title: Uwierzytelnianie przekazywane dla środowiska testowego Microsoft 365
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
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'Podsumowanie: Skonfiguruj uwierzytelnianie z przekazywaniem dla środowiska testowego Microsoft 365.'
ms.openlocfilehash: f6ad952ebde8556bd3c0c9b7e4e66c006b1c7578
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094377"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>Uwierzytelnianie przekazywane dla środowiska testowego Microsoft 365

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

Organizacje, które chcą bezpośrednio korzystać z infrastruktury usług lokalna usługa Active Directory Domain Services (AD DS) na potrzeby uwierzytelniania w usługach i aplikacjach firmy Microsoft w chmurze, mogą używać uwierzytelniania przekazywanego. W tym artykule opisano sposób konfigurowania środowiska testowego Microsoft 365 na potrzeby uwierzytelniania z przekazywaniem, co skutkuje następującą konfiguracją:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania z przekazywaniem.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
Istnieją dwie fazy konfigurowania tego środowiska testowego:

1.    Utwórz Microsoft 365 symulowane środowisko testowe przedsiębiorstwa z synchronizacją skrótów haseł.
2.    Konfigurowanie usługi Azure AD Połączenie w usłudze APP1 na potrzeby uwierzytelniania przekazywanego.
    
![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kliknij [tutaj](../downloads/Microsoft365EnterpriseTLGStack.pdf), aby uzyskać wizualną mapę na wszystkie artykuły w stosie Microsoft 365 for enterprise Test Lab Guide.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365

Postępuj zgodnie z instrukcjami [synchronizacji skrótów haseł dla Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Oto konfiguracja wyniku.
  
![Symulowane przedsiębiorstwo ze środowiskiem testowym synchronizacji skrótów haseł.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z następujących elementów: 
  
- Microsoft 365 E5 wersji próbnej lub płatnej subskrypcji.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure. Usługa Azure AD Połączenie uruchamiana w usłudze APP1, aby okresowo synchronizować domenę usług AD DS TESTLAB z dzierżawą usługi Azure AD subskrypcji Microsoft 365.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>Faza 2. Konfigurowanie Połączenie usługi Azure AD w aplikacji APP1 na potrzeby uwierzytelniania przekazywanego

W tej fazie skonfigurujesz usługę Azure AD Połączenie w aplikacji APP1 tak, aby korzystała z uwierzytelniania przekazywanego, a następnie sprawdzasz, czy działa.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurowanie Połączenie usługi Azure AD w aplikacji APP1

1.    Z [poziomu Azure Portal](https://portal.azure.com) zaloguj się przy użyciu konta administratora globalnego, a następnie połącz się z aplikacją APP1 przy użyciu konta TESTLAB\User1.

2.    Na pulpicie aplikacji APP1 uruchom usługę Azure AD Połączenie.

3.    Na **stronie Powitalnej** kliknij pozycję **Konfiguruj**.

4.    Na stronie Dodatkowe zadania kliknij pozycję **Zmień logowanie użytkownika**, a następnie kliknij przycisk **Dalej**.

5.    Na stronie **Połączenie do usługi Azure AD** wpisz poświadczenia konta administratora globalnego, a następnie kliknij przycisk **Dalej**.

6.    Na stronie **Logowanie użytkownika** kliknij pozycję **Uwierzytelnianie przekazywane**, a następnie kliknij przycisk **Dalej**.

7.    Na stronie **Gotowe do skonfigurowania** kliknij pozycję **Konfiguruj**.

8.    Na **stronie Konfiguracja ukończona** kliknij pozycję **Zakończ**.

9.    W Azure Portal w okienku po lewej stronie kliknij pozycję **Azure Active Directory > Połączenie usługi Azure AD**. Sprawdź, czy funkcja **uwierzytelniania przekazywanego** jest wyświetlana jako **Włączona**.

10.    Kliknij **pozycję Uwierzytelnianie przekazywane**. Okienko **Uwierzytelnianie przekazywane** zawiera listę serwerów, na których są instalowani agenci uwierzytelniania. Na liście powinna zostać wyświetlona aplikacja APP1. Zamknij okienko **Uwierzytelnianie przekazywane** .

Następnie przetestuj możliwość logowania się do subskrypcji przy użyciu <strong>user1@testlab.</strong>\<your public domain> nazwa użytkownika konta User1.

1. W aplikacji APP1 wyloguj się, a następnie zaloguj się ponownie, tym razem określając inne konto.

2. Po wyświetleniu monitu o podanie nazwy użytkownika i hasła określ <strong>user1@testlab.</strong>\<your public domain> i hasło User1. Należy pomyślnie zalogować się jako Użytkownik1.

Zauważ, że chociaż użytkownik User1 ma uprawnienia administratora domeny dla domeny usług AD DS TESTLAB, nie jest administratorem globalnym. W związku z tym ikona **Administrator** nie będzie wyświetlana jako opcja.

Oto twoja konfiguracja wyniku:

![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania z przekazywaniem.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
Ta konfiguracja składa się z następujących elementów:

- Microsoft 365 E5 wersji próbnej lub płatnych subskrypcji z testlab domeny DNS.\<your domain name> Zarejestrowany.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure. Agent uwierzytelniania jest uruchamiany w usłudze APP1 w celu obsługi żądań uwierzytelniania przekazywanego z dzierżawy usługi Azure AD subskrypcji Microsoft 365.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)