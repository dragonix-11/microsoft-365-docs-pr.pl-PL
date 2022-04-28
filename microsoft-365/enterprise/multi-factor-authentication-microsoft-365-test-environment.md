---
title: Microsoft 365 na potrzeby uwierzytelniania wieloskładnikowego w środowisku testowym przedsiębiorstwa
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
- seo-marvel-apr2020
- admindeeplinkMAC
description: Skonfiguruj uwierzytelnianie wieloskładnikowe przy użyciu wiadomości sms wysyłanych do telefonu inteligentnego w Microsoft 365 dla środowiska testowego przedsiębiorstwa.
ms.openlocfilehash: aa72375342bdf60e1fe1bc504f14b1f51a48b701
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078740"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Uwierzytelnianie wieloskładnikowe dla Microsoft 365 dla środowiska testowego przedsiębiorstwa

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

Aby uzyskać dodatkowy poziom zabezpieczeń logowania do Microsoft 365 lub dowolnej usługi lub aplikacji korzystającej z dzierżawy usługi Azure AD w ramach subskrypcji, możesz włączyć uwierzytelnianie wieloskładnikowe usługi Azure AD, które wymaga więcej niż tylko nazwy użytkownika i hasła w celu zweryfikowania konta.

W przypadku uwierzytelniania wieloskładnikowego użytkownicy muszą potwierdzić połączenie telefoniczne, wpisać kod weryfikacyjny wysłany w wiadomości SMS lub zweryfikować uwierzytelnianie przy użyciu aplikacji na swoich smartfonach po poprawnym wprowadzeniu haseł. Mogą zalogować się dopiero po spełnieniu tego drugiego współczynnika uwierzytelniania.
  
W tym artykule opisano sposób włączania i testowania uwierzytelniania opartego na wiadomościach tekstowych dla określonego konta użytkownika.
  
Konfigurowanie uwierzytelniania wieloskładnikowego dla konta w Microsoft 365 dla środowiska testowego przedsiębiorstwa obejmuje dwie fazy i trzecią fazę opcjonalną:
- [Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Faza 2. Włączanie i testowanie uwierzytelniania wieloskładnikowego dla konta użytkownika 2](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [Faza 3. Włączanie i testowanie uwierzytelniania wieloskładnikowego przy użyciu zasad dostępu warunkowego](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz tylko przetestować uwierzytelnianie wieloskładnikowe w sposób uproszczony z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz przetestować uwierzytelnianie wieloskładnikowe w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie uwierzytelniania wieloskładnikowego nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services (AD DS). Jest ona dostępna tutaj jako opcja, dzięki czemu można przetestować uwierzytelnianie wieloskładnikowe i eksperymentować z nim w środowisku reprezentującym typową organizację.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Faza 2. Włączanie i testowanie uwierzytelniania wieloskładnikowego dla konta użytkownika 2

Włącz uwierzytelnianie wieloskładnikowe dla konta użytkownika 2, wykonując następujące kroki:
  
1. Otwórz oddzielne prywatne wystąpienie przeglądarki, przejdź do Centrum administracyjne platformy Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)), a następnie zaloguj się przy użyciu konta administratora globalnego.
    
2. W obszarze nawigacji po lewej stronie wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UżytkownicyAktywni**</a> >  użytkownicy.
    
3. W okienku Aktywni użytkownicy wybierz pozycję **Uwierzytelnianie wieloskładnikowe**.
    
4. Na liście wybierz konto **Użytkownika 2** .
    
5. W sekcji **Użytkownik 2** w obszarze **Szybkie kroki** wybierz pozycję **Włącz**.
    
6. W oknie dialogowym **Informacje o włączaniu uwierzytelniania wieloskładnikowego** wybierz pozycję Włącz uwierzytelnianie **wieloskładnikowe**.
    
7. W oknie dialogowym **Aktualizacje zakończone pomyślnie** wybierz pozycję **Zamknij**.
    
8. Na karcie **Centrum administracyjne platformy Microsoft 365** wybierz ikonę konta użytkownika w prawym górnym rogu, a następnie wybierz pozycję **Wyloguj.**
    
9. Zamknij wystąpienie przeglądarki.
   
Wykonaj konfigurację konta użytkownika 2, aby użyć wiadomości SMS do weryfikacji i przetestować je, wykonując następujące kroki:
  
1. Otwórz nowe, prywatne wystąpienie przeglądarki.
    
2. Przejdź do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) i zaloguj się przy użyciu nazwy konta użytkownika 2 i hasła.
    
3. Po zalogowaniu zostanie wyświetlony monit o skonfigurowanie konta, aby uzyskać więcej informacji. Wybierz pozycję **Dalej**.
    
4. Na stronie **Dodatkowa weryfikacja zabezpieczeń** :
    
   - Wybierz swój kraj lub region.
    
   - Wprowadź numer telefonu inteligentnego, który będzie odbierać wiadomości SMS.
    
   - W **obszarze Metoda** wybierz **pozycję Wyślij mi kod według wiadomości SMS**.
    
5. Wybierz pozycję **Dalej**.
    
6. Wprowadź kod weryfikacyjny z wiadomości SMS odebranej na telefonie inteligentnym, a następnie wybierz pozycję **Weryfikuj**.
    
7. Na stronie **Krok 3: Zachowaj istniejące aplikacje** wybierz pozycję **Gotowe**.
    
8. Jeśli po raz pierwszy zalogowano się przy użyciu konta użytkownika 2, zostanie wyświetlony monit o zmianę hasła. Wprowadź dwa razy oryginalne hasło i nowe hasło, a następnie wybierz pozycję **Zaktualizuj hasło i zaloguj się**. Zarejestruj nowe hasło w bezpiecznej lokalizacji.
    
    Na karcie **Narzędzia główne Microsoft Office** w przeglądarce powinien zostać wyświetlony portal Office dla użytkownika 2.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Faza 3. Włączanie i testowanie uwierzytelniania wieloskładnikowego przy użyciu zasad dostępu warunkowego

*Ta faza może być używana tylko dla Microsoft 365 dla środowiska testowego przedsiębiorstwa.*

W tej fazie włączysz uwierzytelnianie wieloskładnikowe dla konta użytkownika 3 przy użyciu grupy i zasad dostępu warunkowego.

Następnie utwórz nową grupę o nazwie MFAUsers i dodaj do niej konto Użytkownika 3.

1. Na karcie **Centrum administracyjne platformy Microsoft 365** wybierz pozycję **Grupy** w lewym obszarze nawigacji, a następnie wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a>.
2. Wybierz **pozycję Dodaj grupę**.
3. W okienku **Wybierz typ grupy** wybierz pozycję **Zabezpieczenia**, a następnie wybierz pozycję **Dalej**.
4. W **okienku Konfigurowanie podstaw** wybierz pozycję **Utwórz grupę**, a następnie wybierz pozycję **Zamknij**.
5. W okienku **Przeglądanie i zakończenie dodawania grupy** wprowadź **wartość MFAUsers**, a następnie wybierz pozycję **Dalej**.
6. Na liście grup wybierz grupę **MFAUsers** .
7. W okienku **MFAUsers** wybierz pozycję **Członkowie**, a następnie wybierz pozycję **Wyświetl wszystkich członków i zarządzaj nimi**.
8. W okienku **MFAUsers** wybierz pozycję **Dodaj członków**, wybierz konto **Użytkownika 3**, a następnie wybierz pozycję **SaveCloseClose** >  > .

Następnie utwórz zasady dostępu warunkowego, aby wymagać uwierzytelniania wieloskładnikowego dla członków grupy MFAUsers.

1. Na nowej karcie przeglądarki przejdź do [https://portal.azure.com](https://portal.azure.com)pozycji .
2. Wybierz **pozycję Azure Active Directory** >  **SecurityDostęp** >  **warunkowy**.
3. W okienku **Dostęp warunkowy — zasady** wybierz pozycję **Nowe zasady**.
4. W okienku **Nowy** wprowadź uwierzytelnianie wieloskładnikowe **dla kont użytkowników** w polu **Nazwa** .
5. W sekcji **Przypisania** wybierz pozycję **Użytkownicy i grupy**.
6. Na karcie **Dołączanie** w okienku **Użytkownicy i grupy** wybierz pozycję **Wybierz użytkowników i** **grupyUżytkownicy** >  i **grupyWybierz** > .
7. W okienku **Wybierz** wybierz grupę **MFAUsers**, a następnie wybierz pozycję **SelectDone** > .
8. W sekcji **Kontrolki dostępu** w okienku **Nowy** wybierz pozycję **Udziel**.
9. W okienku **Udzielanie** wybierz pozycję **Wymagaj uwierzytelniania wieloskładnikowego**, a następnie wybierz pozycję **Wybierz**.
10. W okienku **Nowy** wybierz pozycję **Włączone** w **obszarze Włącz zasady**, a następnie wybierz pozycję **Utwórz**.
11. Zamknij karty **Azure Portal** i **Centrum administracyjne platformy Microsoft 365**.

Aby przetestować te zasady, wyloguj się i zaloguj się przy użyciu konta użytkownika 3. Powinien zostać wyświetlony monit o skonfigurowanie uwierzytelniania wieloskładnikowego. Pokazuje to, że zasady MFAUsers są stosowane.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)