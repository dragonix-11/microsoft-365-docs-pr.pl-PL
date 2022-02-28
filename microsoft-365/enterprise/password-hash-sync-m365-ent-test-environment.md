---
title: Synchronizacja skrótów haseł w środowisku Microsoft 365 testowym
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Podsumowanie: Skonfiguruj i zademonstruj synchronizację skrótów haseł oraz logowanie w twoim Microsoft 365 testowym.'
ms.openlocfilehash: 746a0e1112df6ebf99569bfed58d08d0a4519d7a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986412"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Synchronizacja skrótów haseł w środowisku Microsoft 365 testowym

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

Wiele organizacji używa usługi Azure AD Połączenie i synchronizacji skrótów haseł do synchronizowania zestawu kont w ich lokalnym lesie programu Usługi domenowe w usłudze Active Directory (AD DS) do zestawu kont w dzierżawie usługi Azure AD subskrypcji usługi Microsoft 365. 

W tym artykule opisano, jak dodać do środowiska testowego programu Microsoft 365 synchronizację skrótów haseł, co powoduje dodanie tej konfiguracji:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowania skrótów haseł.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
Konfigurowanie tego środowiska testowego obejmuje trzy fazy:
- [Etap 1. Tworzenie symulowanego Microsoft 365 testowania przedsiębiorstwa](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [Etap 2. Tworzenie i rejestrowanie domeny testlab](#phase-2-create-and-register-the-testlab-domain)
- [Etap 3. Instalowanie usługi Azure AD Połączenie aplikacji APP1](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>Etap 1. Tworzenie symulowanego Microsoft 365 testowania przedsiębiorstwa

Postępuj zgodnie z instrukcjami w [symulowanej konfiguracji bazy przedsiębiorstwa dla Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). Wynikowa konfiguracja wygląda następująco:
  
![Symulowana konfiguracja bazy przedsiębiorstwa.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z:
  
- Subskrypcja Microsoft 365 E5 próbna lub płatna.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w sieci wirtualnej platformy Azure. DC1 jest kontrolerem domeny testlab.<*domeny publicznej,> AD DS* domeny.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>Etap 2. Tworzenie i rejestrowanie domeny testlab

W tym etapie dodaj publiczną domenę DNS, a następnie dodaj ją do swojej subskrypcji.

Najpierw utwórz u swojego publicznego dostawcę rejestracji DNS nową nazwę publicznej domeny DNS na podstawie bieżącej nazwy domeny, a następnie dodaj ją do swojej subskrypcji. Zalecamy używanie nazwy **testlab.<*domeny publicznej*>**. Jeśli na przykład nazwa domeny publicznej to **<span>contoso.com</span>**, dodaj nazwę domeny publicznej: **<span>testlab.contoso.com</span>**.
  
Następnie dodaj domenę **testlab.<>** domeny publicznej do subskrypcji Microsoft 365 próbnej lub płatnej, przechodząc przez proces rejestracji domeny. Obejmuje to dodanie kolejnych rekordów DNS do domeny **testlab.<*domeny publicznej*>** . Aby uzyskać więcej informacji, [zobacz Dodawanie domeny do Microsoft 365](../admin/setup/add-domain.md).

Wynikowa konfiguracja wygląda następująco:
  
![Rejestracja nazwy domeny testlab.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
Ta konfiguracja składa się z:

- Subskrypcja Microsoft 365 E5 próbna lub płatna z domeną DNS testlab.<*zarejestrowaną nazwą*> domeny publicznej.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.

Zauważ, że teraz jest <testlab.> *domeny* publicznej:

- Obsługiwane przez publiczne rekordy DNS.
- Zarejestrowane w Twoich Microsoft 365 subskrypcji.
- Domena AD DS w symulowanym intranecie.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>Etap 3. Instalowanie usługi Azure AD Połączenie aplikacji APP1

W tym etapie zainstaluj i skonfiguruj narzędzie azure AD Połączenie w aplikacji APP1, a następnie sprawdź, czy działa.
  
Najpierw zainstaluj i skonfiguruj usługę Azure AD, Połączenie aplikacji APP1.

1. W portalu [Azure zaloguj](https://portal.azure.com) się przy użyciu konta administratora globalnego, a następnie połącz się z aplikacją APP1 za pomocą konta TESTLABUser1\\.
    
2. Na pulpicie aplikacji APP1 otwórz wiersz polecenia aplikacji na poziomie Windows PowerShell, a następnie uruchom następujące polecenia, aby wyłączyć rozszerzone zabezpieczenia programu Internet Explorer:
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. Na pasku zadań wybierz pozycję **Internet Explorer i** przejdź do opcji [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. Na Microsoft Azure Active Directory Połączenie wybierz pozycję **Pobierz**, a następnie wybierz pozycję **Uruchom**.
    
5. Na stronie **Połączenie usługi Azure AD** wybierz pozycję Zgadzam **się,** a następnie wybierz pozycję **Kontynuuj**.
    
6. Na stronie **Ustawienia** Express wybierz pozycję **Użyj ustawień ekspresowych**.
    
7. Na stronie **Połączenie do usługi Azure AD** wprowadź nazwę konta administratora globalnego w witrynie Nazwa użytkownika **,** wprowadź hasło do konta w witrynie **Hasło, a** następnie wybierz pozycję **Dalej**.
    
8. Na stronie **Połączenie do AD DS** wpisz **TESTLABUser1\\** w nazwa_użytkownika **,** wprowadź hasło w **password, a** następnie wybierz przycisk **Dalej**.
    
9. Na **stronie Wszystko gotowe do skonfigurowania** wybierz pozycję **Zainstaluj**.
    
10. Na stronie **Ukończono konfigurację** wybierz pozycję **Zakończ**.
    
11. W programie Internet Explorer przejdź do centrum administracyjne platformy Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)).
    
12. W lewym okienku nawigacji wybierz pozycję Użytkownicy > **aktywni użytkownicy**.
    
    Zwróć uwagę na konto o **nazwie Użytkownik1**. To konto pochodzi z domeny TESTLAB AD DS i ma dowód na to, że synchronizacja katalogów działała.
    
13. Wybierz konto **Użytkownika1** , a następnie wybierz **pozycję Licencje i aplikacje**.
    
14. Na **stronie Licencje na** produkty wybierz swoją lokalizację (w razie potrzeby), wyłącz licencję produktu **Office 365 E5**, a następnie włącz **licencję Microsoft 365 E5** produktu. 

15. Wybierz **pozycję** Zapisz u dołu strony, a następnie wybierz pozycję **Zamknij**.
    
Następnie przetestuj możliwość zalogowania się do subskrypcji za pomocą pliku **user1@testlab.<>** nazwy domeny nazwa użytkownika konta User1:

1. W aplikacji APP1 wyloguj się, a następnie zaloguj się ponownie, tym razem określając inne konto.

2. Gdy zostanie wyświetlony monit o podanie nazwy użytkownika i hasła, **user1@testlab.<*nazwę*>** domeny i hasło użytkownika User1. Należy pomyślnie zalogować się jako Użytkownik1.
 
Użytkownik1 ma uprawnienia administratora domeny dla domeny TESTLAB AD DS, ale nie jest administratorem globalnym. Dlatego nie **zobaczysz ikony Administrator** jako opcji. 

Wynikowa konfiguracja wygląda następująco:

![Symulowane przedsiębiorstwo ze środowiskiem testowania skrótów haseł.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

Ta konfiguracja składa się z: 
  
- Microsoft 365 E5 lub Office 365 E5 wersji próbnej lub płatnej z domeną DNS TESTLAB.<*zarejestrowaną* nazwą> domeny.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure. Usługa Azure AD Połączenie działa w aplikacji APP1 w celu okresowego synchronizowania domeny TESTLAB AD DS z dzierżawą usługi Azure AD twojej subskrypcji usługi Microsoft 365 usługi.
- Konto użytkownika User1 w programie TESTLAB AD DS zostało zsynchronizowane z dzierżawą usługi Azure AD.

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)