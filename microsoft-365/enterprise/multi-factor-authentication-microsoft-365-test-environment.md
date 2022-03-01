---
title: Microsoft 365 do uwierzytelniania wieloskładnikowego w środowisku testowym w przedsiębiorstwie
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Skonfiguruj uwierzytelnianie wieloskładnikowe przy użyciu wiadomości SMS wysyłanych na smartfon w Microsoft 365 testowania przedsiębiorstwa.
ms.openlocfilehash: d3207db4d8537e78ecc83ae18f8539f0e4f56106
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013872"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Uwierzytelnianie wieloskładnikowe w Microsoft 365 testowania przedsiębiorstwa

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

Aby zapewnić dodatkowy poziom zabezpieczeń podczas logowania się do usługi Microsoft 365 lub dowolnej usługi lub dowolnej aplikacji, która korzysta z dzierżawy usługi Azure AD dla Twojej subskrypcji, możesz włączyć uwierzytelnianie wieloskładnikowe usługi Azure AD, które do zweryfikowania konta wymaga więcej niż tylko nazwy użytkownika i hasła.

W przypadku uwierzytelniania wieloskładnikowego użytkownicy muszą potwierdzić połączenie telefoniczne, wpisać kod weryfikacyjny wysłany w wiadomości SMS lub zweryfikować uwierzytelnianie za pomocą aplikacji na telefonach inteligentnych po prawidłowym wprowadzeniu haseł. Mogą zalogować się dopiero po zadowoleniu z tego drugiego czynnika uwierzytelniania.
  
W tym artykule opisano, jak włączyć i przetestować uwierzytelnianie oparte na wiadomościach SMS dla określonego konta użytkownika.
  
Konfigurowanie uwierzytelniania wieloskładnikowego dla konta w środowisku testowania Microsoft 365 dla przedsiębiorstwa obejmuje dwie fazy i trzecią fazę opcjonalną:
- [Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Etap 2. Włączanie i testowanie uwierzytelniania wieloskładnikowego dla konta użytkownika 2](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [Etap 3. Włączanie i testowanie uwierzytelniania wieloskładnikowego przy użyciu zasad dostępu warunkowego](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz tylko przetestować uwierzytelnianie wieloskładnikowe przy minimalnym poziomie wymagań, postępuj zgodnie z instrukcjami w teście Konfiguracja podstawowa[.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Jeśli chcesz przetestować uwierzytelnianie wieloskładnikowe w symulowanym przedsiębiorstwie, wykonaj instrukcje z uwierzytelniania [pass-through](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie uwierzytelniania wieloskładnikowego nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Usługi domenowe w usłudze Active Directory (AD DS). Jest on podany jako opcja, która umożliwia przetestowanie uwierzytelniania wieloskładnikowego i eksperymentowanie z nim w środowisku reprezentującym typową organizację.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Etap 2. Włączanie i testowanie uwierzytelniania wieloskładnikowego dla konta użytkownika 2

Aby włączyć uwierzytelnianie wieloskładnikowe dla konta użytkownika 2, należy wykonać następujące czynności:
  
1. Otwórz osobne prywatne wystąpienie przeglądarki, przejdź do centrum administracyjne platformy Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)), a następnie zaloguj się przy użyciu konta administratora globalnego.
    
2. W lewym okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UżytkownicyAktywowanie**</a> >  użytkowników.
    
3. W okienku Aktywni użytkownicy wybierz pozycję **Uwierzytelnianie wieloskładnikowe**.
    
4. Z listy wybierz konto **użytkownika 2** .
    
5. W sekcji **Użytkownik 2** w obszarze **Szybkie kroki** wybierz pozycję **Włącz**.
    
6. W **oknie dialogowym Włączanie uwierzytelniania wieloskładnikowego —** informacje wybierz pozycję **Włącz usługę Multi-FactorAuth**.
    
7. W **oknie dialogowym** Aktualizacje po pomyślnym wybraniu przycisku **Zamknij**.
    
8. Na karcie **centrum administracyjne platformy Microsoft 365** wybierz ikonę konta użytkownika w prawym górnym rogu, a następnie wybierz pozycję **Wyloguj.**
    
9. Zamknij wystąpienie przeglądarki.
   
Wykonaj konfigurację dla konta użytkownika 2, aby użyć wiadomości SMS do sprawdzenia poprawności i przetestować ją za pomocą poniższych kroków:
  
1. Otwórz nowe, prywatne wystąpienie przeglądarki.
    
2. Przejdź do tego [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) i zaloguj się za pomocą nazwy konta użytkownika 2 i hasła.
    
3. Po zalogowaniu się zostanie wyświetlony monit o skonfigurowanie konta, aby uzyskać więcej informacji. Wybierz pozycję **Dalej**.
    
4. Na stronie **Dodatkowa weryfikacja** zabezpieczeń:
    
   - Wybierz swój kraj lub region.
    
   - Wprowadź numer telefonu inteligentnego, który będzie odbierał wiadomości TEKSTOWE.
    
   - W **polu Metoda** wybierz **pozycję Wyślij mi kod za pomocą wiadomości SMS**.
    
5. Wybierz pozycję **Dalej**.
    
6. Wprowadź kod weryfikacyjny z wiadomości SMS otrzymanej na smartfonie, a następnie wybierz pozycję **Weryfikuj**.
    
7. Na stronie **Krok 3. Zachowaj istniejące aplikacje** wybierz pozycję **Gotowe**.
    
8. Jeśli po raz pierwszy zalogowano się przy użyciu konta użytkownika 2, zostanie wyświetlony monit o zmianę hasła. Wprowadź hasło oryginalne i nowe dwa razy, a następnie wybierz pozycję **Aktualizuj hasło i zaloguj się**. Zanotuj nowe hasło w bezpiecznym miejscu.
    
    Na karcie Narzędzia Office główne w przeglądarce powinien zostać wyświetlony portal Office dla użytkowników **Microsoft Office** 2.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Etap 3. Włączanie i testowanie uwierzytelniania wieloskładnikowego przy użyciu zasad dostępu warunkowego

*Tej fazy można używać tylko w przypadku Microsoft 365 w środowisku testowania przedsiębiorstwa.*

W tej fazie włącz uwierzytelnianie wieloskładnikowe dla konta użytkownika 3 przy użyciu grupy i zasad dostępu warunkowego.

Następnie utwórz nową grupę o nazwie MFAUsers i dodaj do niego konto Użytkownika 3.

1. Na karcie **centrum administracyjne platformy Microsoft 365** grupy w lewym obszarze nawigacji,  a następnie wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a>.
2. Wybierz **pozycję Dodaj grupę**.
3. W **okienku Wybierz typ grupy** wybierz pozycję **Zabezpieczenia**, a następnie wybierz pozycję **Dalej**.
4. W **okienku Konfigurowanie podstawowych funkcji** wybierz pozycję **Utwórz grupę**, a następnie wybierz pozycję **Zamknij**.
5. W **okienku Przeglądanie i kończanie dodawania grupy** wprowadź **nazwę MFAUsers**, a następnie wybierz pozycję **Dalej**.
6. Na liście grup wybierz **grupę MFAUsers** .
7. W **okienku Użytkownicy uwierzytelniania wieloskładnikowego** wybierz **pozycję Członkowie**, a następnie wybierz pozycję **Wyświetl wszystkich członków i zarządzaj nimi**.
8. W **okienku Użytkownicy uwierzytelniania wieloskładnikowego** wybierz pozycję **Dodaj** członków, wybierz konto użytkownika **3**, a następnie wybierz pozycję **SaveCloseClose** >  > .

Następnie utwórz zasady dostępu warunkowego, aby wymagać uwierzytelniania wieloskładnikowego dla członków grupy Użytkownicy uwierzytelniania WIELOSKŁADNIKOWEGO.

1. Na nowej karcie przeglądarki przejdź do .[https://portal.azure.com](https://portal.azure.com)
2. Wybierz **Azure Active Directory** >  **SecurityConditional** >  Access.
3. W **okienku Dostęp warunkowy —** zasady wybierz pozycję **Nowe zasady**.
4. W **okienku Nowy** wprowadź **uwierzytelniania MFA dla kont użytkowników** w **polu** Nazwa.
5. W sekcji **Zadania wybierz** pozycję **Użytkownicy i grupy**.
6. Na karcie **Dołączanie** **okienka Użytkownicy i** grupy wybierz pozycję **Zaznacz użytkowników i** >  **grupyUżytkowcy i grupyZaznaczanie** > .
7. W **okienku** Wybieranie wybierz **grupę MfAUsers**, a następnie wybierz **pozycję** **SelectDone** > .
8. W sekcji **Kontrolki programu Access** w **okienku Nowy** wybierz pozycję **U grant**.
9. W **okienku Udzielanie** wybierz pozycję **Wymagaj uwierzytelniania wieloskładnikowego**, a następnie wybierz pozycję **Wybierz**.
10. W **okienku Nowy** wybierz pozycję **Włącz dla** **opcji Włącz zasady**, a następnie wybierz pozycję **Utwórz**.
11. Zamknij Portal **Azure i** **centrum administracyjne platformy Microsoft 365** karty.

Aby przetestować te zasady, wyloguj się i zaloguj się przy użyciu konta Użytkownika 3. Powinien zostać wyświetlony monit o skonfigurowanie uwierzytelniania MFA. Pokazuje to, że stosowana jest zasada MFAUsers.

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)