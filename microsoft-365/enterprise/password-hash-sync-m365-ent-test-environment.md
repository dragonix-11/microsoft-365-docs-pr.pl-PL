---
title: Synchronizacja skrótów haseł dla środowiska testowego Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/26/2020
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
- seo-marvel-apr2020
ms.assetid: ''
description: 'Podsumowanie: Konfigurowanie i demonstrowanie synchronizacji skrótów haseł i logowania dla środowiska testowego Microsoft 365.'
ms.openlocfilehash: 91d4de08382149b5089f0c06295e77965ea022cf
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093816"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Synchronizacja skrótów haseł dla środowiska testowego Microsoft 365

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

Wiele organizacji używa synchronizacji skrótów Połączenie usługi Azure AD i haseł w celu zsynchronizowania zestawu kont w lesie usług lokalna usługa Active Directory Domain Services (AD DS) z zestawem kont w dzierżawie usługi Azure AD subskrypcji Microsoft 365. 

W tym artykule opisano sposób dodawania synchronizacji skrótów haseł do środowiska testowego Microsoft 365, co skutkuje następującą konfiguracją:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowym synchronizacji skrótów haseł.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
Konfigurowanie tego środowiska testowego obejmuje trzy fazy:
- [Faza 1. Tworzenie symulowanego środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [Faza 2. Tworzenie i rejestrowanie domeny testlab](#phase-2-create-and-register-the-testlab-domain)
- [Faza 3. Instalowanie usługi Azure AD Połączenie w aplikacji APP1](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>Faza 1. Tworzenie symulowanego środowiska testowego Microsoft 365 przedsiębiorstwa

Postępuj zgodnie z instrukcjami w [symulowanej konfiguracji podstawowej przedsiębiorstwa dla Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). Wynikowe konfiguracje wyglądają następująco:
  
![Symulowana konfiguracja podstawowa przedsiębiorstwa.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z następujących elementów:
  
- Subskrypcja Microsoft 365 E5 wersji próbnej lub płatnej.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w sieci wirtualnej platformy Azure. DC1 jest kontrolerem domeny dla testlab.<*nazwy domeny publicznej*> domenie usług AD DS.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>Faza 2. Tworzenie i rejestrowanie domeny testlab

W tej fazie dodaj publiczną domenę DNS, a następnie dodaj ją do subskrypcji.

Najpierw skontaktuj się z publicznym dostawcą rejestracji DNS, aby utworzyć nową publiczną nazwę domeny DNS opartą na bieżącej nazwie domeny, a następnie dodać ją do subskrypcji. Zalecamy użycie nazwy **testlab.<*domeny*> publicznej**. Jeśli na przykład nazwa domeny publicznej to **<span>contoso.com</span>**, dodaj nazwę domeny publicznej: **<span>testlab.contoso.com</span>**.
  
Następnie dodaj **plik testlab.<domeny *publicznej*>** do Microsoft 365 wersji próbnej lub płatnej subskrypcji, przechodząc przez proces rejestracji domeny. Obejmuje to dodanie dodatkowych rekordów DNS do **pliku testlab.<domeny *publicznej*>** . Aby uzyskać więcej informacji, zobacz [Dodawanie domeny do Microsoft 365](../admin/setup/add-domain.md).

Wynikowe konfiguracje wyglądają następująco:
  
![Rejestracja nazwy domeny testlab.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
Ta konfiguracja składa się z następujących elementów:

- Microsoft 365 E5 wersji próbnej lub płatnej subskrypcji z domeną DNS testlab.<*nazwa domeny publicznej*> zarejestrowana.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.

Zwróć uwagę na to, że> nazwy *domeny publicznej* <testlab.<jest teraz następująca:

- Obsługiwane przez publiczne rekordy DNS.
- Zarejestrowane w subskrypcjach Microsoft 365.
- Domena usług AD DS w symulowanym intranecie.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>Faza 3. Instalowanie usługi Azure AD Połączenie w aplikacji APP1

W tej fazie zainstaluj i skonfiguruj narzędzie Połączenie usługi Azure AD w aplikacji APP1, a następnie sprawdź, czy działa.
  
Najpierw zainstaluj i skonfiguruj Połączenie usługi Azure AD w aplikacji APP1.

1. Z [poziomu Azure Portal](https://portal.azure.com) zaloguj się przy użyciu konta administratora globalnego, a następnie połącz się z aplikacją APP1 przy użyciu konta TESTLABUser1\\.
    
2. Na pulpicie aplikacji APP1 otwórz wiersz polecenia Windows PowerShell na poziomie administratora, a następnie uruchom następujące polecenia, aby wyłączyć rozszerzone zabezpieczenia programu Internet Explorer:
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. Na pasku zadań wybierz pozycję **Internet Explorer** i przejdź do pozycji [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. Na stronie Microsoft Azure Active Directory Połączenie wybierz pozycję **Pobierz**, a następnie wybierz pozycję **Uruchom**.
    
5. Na stronie **Witamy w usłudze Azure AD Połączenie** wybierz **pozycję Zgadzam się**, a następnie wybierz pozycję **Kontynuuj**.
    
6. Na stronie **Express Ustawienia** wybierz pozycję **Użyj ustawień ekspresowych**.
    
7. Na stronie **Połączenie do usługi Azure AD** wprowadź nazwę konta administratora globalnego w polu **Nazwa użytkownika,** wprowadź hasło w polu **Hasło**, a następnie wybierz pozycję **Dalej**.
    
8. Na **stronie Połączenie do usług AD DS** wprowadź **wartość TESTLABUser1\\** w **polu Nazwa użytkownika,** wprowadź hasło w polu **Hasło**, a następnie wybierz pozycję **Dalej**.
    
9. Na stronie **Gotowe do skonfigurowania** wybierz pozycję **Zainstaluj**.
    
10. Na stronie **Konfiguracja ukończona** wybierz pozycję **Zakończ**.
    
11. W programie Internet Explorer przejdź do Centrum administracyjne platformy Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)).
    
12. W okienku nawigacji po lewej stronie wybierz pozycję **Użytkownicy > aktywni użytkownicy**.
    
    Zanotuj konto o nazwie **User1**. To konto pochodzi z domeny TESTLAB AD DS i jest dowodem na to, że synchronizacja katalogów zadziałała.
    
13. Wybierz konto **Użytkownika1** , a następnie wybierz pozycję **Licencje i aplikacje**.
    
14. W **obszarze Licencje produktów** wybierz swoją lokalizację (w razie potrzeby), wyłącz licencję **Office 365 E5**, a następnie włącz licencję **Microsoft 365 E5**. 

15. Wybierz pozycję **Zapisz** w dolnej części strony, a następnie wybierz pozycję **Zamknij**.
    
Następnie przetestuj możliwość logowania się do subskrypcji przy użyciu **user1@testlab.<*nazwy użytkownika nazwy*> domeny** konta Użytkownika1:

1. W aplikacji APP1 wyloguj się, a następnie zaloguj się ponownie, tym razem określając inne konto.

2. Po wyświetleniu monitu o podanie nazwy użytkownika i hasła określ **user1@testlab.<*nazwę*> domeny** i hasło User1. Należy pomyślnie zalogować się jako Użytkownik1.
 
Zauważ, że chociaż użytkownik User1 ma uprawnienia administratora domeny dla domeny usług AD DS TESTLAB, nie jest administratorem globalnym. W związku z tym ikona **Administrator** nie będzie wyświetlana jako opcja. 

Wynikowe konfiguracje wyglądają następująco:

![Symulowane przedsiębiorstwo ze środowiskiem testowym synchronizacji skrótów haseł.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

Ta konfiguracja składa się z następujących elementów: 
  
- Microsoft 365 E5 lub Office 365 E5 subskrypcje próbne lub płatne z domeną DNS TESTLAB.<*nazwa domeny*> zarejestrowana.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure. Usługa Azure AD Połączenie działa w usłudze APP1, aby okresowo synchronizować domenę usług AD DS TESTLAB z dzierżawą usługi Azure AD subskrypcji Microsoft 365.
- Konto użytkownika User1 w domenie usług AD DS TESTLAB zostało zsynchronizowane z dzierżawą usługi Azure AD.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)