---
title: Odpowiadanie na naruszone konto e-mail
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.collection:
- o365_security_incident_response
- M365-security-compliance
- m365solution-smb
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
ms.localizationpriority: high
search.appverid:
- MET150
description: Dowiedz się, jak rozpoznać naruszone konto e-mail i odpowiedzieć na nie przy użyciu narzędzi dostępnych w Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bdce44bc54c71d03e8064fa10187c06237d38b5b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033024"
---
# <a name="responding-to-a-compromised-email-account"></a>Odpowiadanie na naruszone konto e-mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Podsumowanie** Dowiedz się, jak rozpoznać naruszone konto e-mail i odpowiedzieć na nie w Microsoft 365.

## <a name="what-is-a-compromised-email-account-in-microsoft-365"></a>Co to jest naruszone konto e-mail w Microsoft 365?

Dostęp do Microsoft 365 pocztowych, danych i innych usług jest kontrolowany za pomocą poświadczeń, takich jak nazwa użytkownika i hasło lub numer PIN. Kradzież poświadczeń przez inną osobę niż zamierzony użytkownik może naruszyć skradzione poświadczenia. Wraz z tym atakujący może zalogować się jako oryginalny użytkownik i wykonywać akcje niedozwolone.

W przypadku użycia skradzionych poświadczeń atakujący może uzyskać dostęp do skrzynki Microsoft 365 pocztowej SharePoint folderów lub plików użytkownika w OneDrive. Jedną z powszechnie spotykanych akcji jest wysyłanie przez atakującego wiadomości e-mail jako pierwotnego użytkownika do adresatów z organizacji i spoza organizacji. Gdy atakujący wysyłają dane do adresatów zewnętrznych, jest to nazywane eksymeracją danych.

## <a name="symptoms-of-a-compromised-microsoft-email-account"></a>Objawy naruszonego konta e-mail Microsoft

Użytkownicy mogą zauważyć i zgłosić nietypowe działania w swoich Microsoft 365 pocztowych. Oto kilka typowych symptomów:

- Podejrzane działania, takie jak brakujące lub usunięte wiadomości e-mail.
- Inni użytkownicy mogą otrzymywać wiadomości e-mail z naruszonego konta, ale odpowiadające im wiadomości e-mail nie są już istniejące w folderze **Elementy** wysłane nadawcy.
- Obecność reguł skrzynki odbiorczej, które nie zostały utworzone przez zamierzonego użytkownika lub administratora. Te reguły mogą automatycznie przesyłać dalej wiadomości e-mail na nieznane adresy lub przenosić je do folderów Notatki **,** **Wiadomości-śmieci** lub **Subskrypcje RSS** .
- Nazwa wyświetlana użytkownika może zostać zmieniona na globalnej liście adresowej.
- Użytkownikowi zablokowano wysyłanie wiadomości e-mail.
- Foldery Elementy wysłane lub Elementy usunięte w programie Microsoft Outlook lub Outlook w sieci Web (dawniej znanym jako Outlook Web App) zawierają typowe wiadomości włamane na konto, takie jak "Utknąłem w Londynie, wyślij pieniądze".
- Nietypowe zmiany w profilu, takie jak nazwa, numer telefonu lub kod pocztowy, zostały zaktualizowane.
- Wymagane są nietypowe zmiany poświadczeń, takie jak wiele zmian haseł.
- Ostatnio dodano przesyłanie dalej poczty.
- Ostatnio dodano nietypowe podpisy, na przykład fałszywy podpis bankowy lub podpis lekowy.

Jeśli użytkownik zda jakiekolwiek z powyższych symptomów, należy przeprowadzić dalsze badanie. Portal Microsoft 365 Defender i Azure Portal oferują narzędzia, które pomogą w zbadaniu działań konta użytkownika, które podejrzewasz, że może zostać naruszone.

- **Ujednolicone** dzienniki inspekcji w portalu Microsoft 365 Defender. Przejrzyj wszystkie działania związane z podejrzaną aktywnością konta, filtrując wyniki dla zakresu dat od razu przed rozpoczęciem podejrzanego działania do bieżącej daty. Nie filtruj aktywności podczas wyszukiwania. Aby uzyskać więcej informacji, zobacz [Przeszukiwanie dziennika inspekcji w Centrum zgodności](../../compliance/search-the-audit-log-in-security-and-compliance.md).

- **Dzienniki logowania usługi Azure AD i inne raporty o ryzyku w portalu usługi Azure AD**: Sprawdź wartości w tych kolumnach:
  - Przejrzyj adres IP
  - lokalizacje logowania
  - godziny logowania
  - sukces lub niepowodzenie logowania

## <a name="how-to-secure-and-restore-email-function-to-a-suspected-compromised-microsoft-365-account-and-mailbox"></a>Jak zabezpieczyć i przywrócić funkcję poczty e-mail w przypadku podejrzeń o naruszone Microsoft 365 i skrzynkę pocztową

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=RE2jvOb&AutoPlayVideo=false]

Nawet jeśli odzyskasz dostęp do konta użytkownika, być może atakujący dodał wejścia na back-door, które umożliwiają atakującemu wznowienie kontroli nad kontem.

Należy wykonać wszystkie poniższe czynności, aby odzyskać dostęp do konta tym szybciej, aby upewnić się, że przechwytator nie wznowi kontroli nad Twoim kontem. Te kroki ułatwiają usunięcie wszystkich wpisów drzwi od tyłu, które mógł dodać do konta osoby, która przechwytuje. Po zakończeniu tych czynności zalecamy uruchomienie skanowania antywirusowego w celu upewnieniu się, że komputer nie został naruszony.

### <a name="step-1-reset-the-users-password"></a>Krok 1 Resetowanie hasła użytkownika

Postępuj zgodnie z procedurami [w te sposób: Resetowanie hasła służbowego dla osoby](../../admin/add-users/reset-passwords.md#reset-my-admin-password).

> [!IMPORTANT]
>
> - Nie należy wysyłać nowego hasła do użytkownika za pośrednictwem poczty e-mail, ponieważ ten atakujący nadal ma dostęp do skrzynki pocztowej.
>
> - Upewnij się, że hasło jest silne i zawiera wielkie i małe litery, co najmniej jedną cyfrę i co najmniej jeden znak specjalny.
>
> - Nie używaj ponownie żadnego z pięciu ostatnich haseł. Mimo że wymaganie dotyczące historii haseł umożliwia ponowne używanie ostatnio używanego hasła, należy wybrać opcję, która nie jest odgadywana przez atakującego.
>
> - Jeśli Twoja tożsamość lokalna jest w federacji z usługą Microsoft 365, musisz zmienić hasło lokalnie, a następnie powiadomić administratora o tym, że ktoś je naruszono.
>
> - Pamiętaj o aktualizowaniu haseł aplikacji. Hasła aplikacji nie są automatycznie cofnięte w przypadku resetowania hasła do konta użytkownika. Użytkownik powinien usunąć istniejące hasła aplikacji i utworzyć nowe. Aby uzyskać instrukcje, [zobacz Tworzenie i usuwanie haseł aplikacji na stronie Dodatkowa weryfikacja zabezpieczeń](/azure/active-directory/user-help/multi-factor-authentication-end-user-app-passwords#create-and-delete-app-passwords-from-the-additional-security-verification-page).
>
> - Zdecydowanie zalecamy włączenie uwierzytelniania wieloskładnikowego (MFA) w celu uniknięcia nałamania zabezpieczeń, zwłaszcza w przypadku kont z uprawnieniami administracyjnymi. Aby dowiedzieć się więcej o uwierzytelnianiu MFA, zobacz [Konfigurowanie uwierzytelniania wieloskładnikowego](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

### <a name="step-2-remove-suspicious-email-forwarding-addresses"></a>Krok 2. Usuwanie podejrzanych adresów e-mail przesyłanych dalej

1. Na stronie centrum administracyjne platformy Microsoft 365 przejdź <https://admin.microsoft.com>do tematu **Aktywni** \> **użytkownicy** użytkownicy. Aby przejść bezpośrednio do strony **Aktywni użytkownicy**, użyj .<https://admin.microsoft.com/Adminportal/Home#/users>

2. Na stronie **Aktywni** użytkownicy znajdź odpowiednie konto użytkownika i zaznacz odpowiedniego użytkownika (wiersz) bez zaznaczania tego pola wyboru.

3. W wyświetlonym wysuwu szczegółów wybierz **kartę** Poczta.

4. Jeśli w sekcji Przesyłanie dalej wiadomości **e-mail** znajduje się wartość **Zastosowane**, kliknij pozycję **Zarządzaj przesyłaniem dalej wiadomości e-mail**. W **wyświetlonym wysuwaniu Zarządzaj przesyłaniem** dalej wiadomości e-mail wyczyść pozycję Przesyłaj dalej wszystkie wiadomości e-mail wysyłane do tej skrzynki **pocztowej,** a następnie kliknij pozycję **Zapisz zmiany**.

### <a name="step-3-disable-any-suspicious-inbox-rules"></a>Krok 3 Wyłączenie podejrzanych reguł skrzynki odbiorczej

1. Zaloguj się do skrzynki pocztowej użytkownika przy użyciu Outlook w sieci Web.

2. Kliknij ikonę koła zębatego i kliknij pozycję **Poczta**.

3. Kliknij **pozycję Skrzynka odbiorcza i reguły czyszczenie** i przejrzyj reguły.

4. Wyłącz lub usuń podejrzane reguły.

### <a name="step-4-unblock-the-user-from-sending-mail"></a>Krok 4. Odblokowywanie użytkownika z wysyłania poczty

Jeśli podejrzana naruszona skrzynka pocztowa została użyta do wysyłania wiadomości e-mail ze spamem, istnieje prawdopodobieństwo, że jej wysyłanie zostało zablokowane.

Aby odblokować skrzynkę pocztową przed wysyłaniem poczty, wykonaj procedury w tece Usuwanie użytkownika z portalu Użytkownicy z ograniczeniami [po wysłaniu wiadomości e-mail ze spamem](removing-user-from-restricted-users-portal-after-spam.md).

### <a name="step-5-optional-block-the-user-account-from-signing-in"></a>Krok 5 Opcjonalnie: Zablokowanie logowania się na koncie użytkownika

> [!IMPORTANT]
> Użytkownik może zablokować możliwość zalogowania się na naruszonym koncie, dopóki nie uważasz, że ponowne włączenie dostępu jest bezpieczne.

1. Na stronie centrum administracyjne platformy Microsoft 365 przejdź <https://admin.microsoft.com>do tematu **Aktywni** \> **użytkownicy** użytkownicy. Aby przejść bezpośrednio do strony **Aktywni użytkownicy**, użyj .<https://admin.microsoft.com/Adminportal/Home#/users>

2. Na stronie **Aktywni użytkownicy** znajdź i wybierz konto użytkownika, ![](../../media/ITPro-EAC-MoreOptionsIcon.png)kliknij ikonę Więcej, a następnie wybierz pozycję Edytuj **stan logowania**.

3. W **wyświetlonym okienku Zablokuj** logowanie wybierz pozycję Zablokuj logowanie tego **użytkownika, a** następnie kliknij pozycję **Zapisz zmiany**.

4. W centrum Exchange administracyjnego (EAC) pod adresem <https://admin.exchange.microsoft.com>przejdź do pozycji **Skrzynki** **pocztowe adresatów**\>. Aby przejść bezpośrednio do strony **Skrzynki** pocztowe, użyj .<https://admin.exchange.microsoft.com/#/mailboxes>

5. Na stronie **Skrzynki** pocztowe znajdź i wybierz użytkownika. W otwartej wysuwanych szczegółach skrzynki pocztowej wykonaj następujące czynności:
   - W sekcji **Aplikacje poczty e-mail** wybierz pozycję **Zarządzaj ustawieniami aplikacji poczty e-mail**. W **wyświetlonym wysuwaniu** Zarządzaj ustawieniami aplikacji poczty e-mail zablokuj wszystkie dostępne ustawienia, przesuwając przełącznik w prawo przycisk ![Wyłącz.](../../media/scc-toggle-on.png)
     - **Outlook on the web**
     - **Outlook (MAPI)**
     - **Usługi sieci Web programu Exchange**
     - **Urządzenie przenośne (Exchange ActiveSync)**
     - **IMAP**
     - **POP3**

   Po zakończeniu kliknij **pozycję Zapisz,** a następnie kliknij przycisk **Zamknij**.

### <a name="step-6-optional-remove-the-suspected-compromised-account-from-all-administrative-role-groups"></a>Krok 6 Argument opcjonalny. Usuwanie podejrzewanego konta, które może być naruszone, ze wszystkich grup ról administracyjnych

> [!NOTE]
> Członkostwo w grupie ról administracyjnych można przywrócić po zabezpieczeniu konta.

1. W centrum administracyjne platformy Microsoft 365 o <https://admin.microsoft.com>wykonaj następujące czynności:
   1. Przejdź do pozycji **Użytkownicy** \> **Aktywni użytkownicy**. Aby przejść bezpośrednio do strony **Aktywni użytkownicy**, użyj .<https://admin.microsoft.com/Adminportal/Home#/users>
   2. Na stronie **Aktywni użytkownicy** znajdź i zaznacz konto użytkownika, kliknij ikonę ![](../../media/ITPro-EAC-MoreOptionsIcon.png)Więcej, a następnie wybierz pozycję **Zarządzaj rolami**.
   3. Usuń wszystkie role administracyjne przypisane do tego konta. Po zakończeniu kliknij pozycję **Zapisz zmiany**.

2. w portalu Microsoft 365 Defender podpowiem <https://security.microsoft.com>, wykonaj następujące czynności:
   1. Przejdź do **uprawnień do & E-mail &** \> **role współpracy**\>. Aby przejść bezpośrednio do **strony Uprawnienia**, użyj .<https://security.microsoft.com/emailandcollabpermissions>
   2. Na stronie **Uprawnienia** zaznacz każdą grupę ról na liście i odszukaj konto użytkownika w sekcji Członkowie  wyświetlonego wysuwu szczegółów. Jeśli grupa ról zawiera konto użytkownika, wykonaj następujące czynności:
      1. W sekcji **Członkowie** kliknij pozycję **Edytuj**.
      2. W **wyświetlonym wysuwam menu Edytowanie** wybierz członków kliknij pozycję **Edytuj**.
      3. W **wyświetlonym wysuwam menu** Wybierz członków kliknij pozycję **Usuń**.
      4. W wyświetlonym wysuwu wybierz konto użytkownika, a następnie kliknij pozycję **Usuń**.

         Po zakończeniu kliknij pozycję **Gotowe,** **Zapisz**, a następnie **Zamknij**.

3. W centrum Exchange administracyjnego w miejscu <https://admin.exchange.microsoft.com/>wykonaj następujące czynności:
   1. Wybierz **pozycję Role** \> **Role administratorów**. Aby przejść bezpośrednio do strony **Role administratorów** , użyj pozycji <https://admin.exchange.microsoft.com/#/adminRoles>.
   2. Na stronie **Role administratorów** zaznacz ręcznie poszczególne grupy ról i w okienku szczegółów wybierz kartę Przypisane, aby  zweryfikować konta użytkowników. Jeśli grupa ról zawiera konto użytkownika, wykonaj następujące czynności:
      1. Wybierz konto użytkownika.
      2. Kliknij przycisk ![Ikona Usuń.](../../media/m365-cc-sc-delete-icon.png).

         Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="step-7-optional-additional-precautionary-steps"></a>Krok 7 Argument opcjonalny. Dodatkowe procedury zabezpieczające

1. Upewnij się, że elementy wysłane zostały zweryfikowane. Być może trzeba będzie poinformować osoby z listy kontaktów, że Twoje konto zostało naruszone. Być może atakujący prosił o pieniądze, podszywanie się na przykład pod inne osoby i niezbędne pieniądze. Może też wysłać temu atakującemu wirusa w celu przechwytowania komputera.

2. Inne usługi, które użyły tego Exchange jako alternatywnego konta e-mail, mogą zostać naruszone. Najpierw wykonaj te czynności dla swojej Microsoft 365 subskrypcji usługi, a następnie wykonaj te czynności dla innych kont.

3. Upewnij się, że twoje informacje kontaktowe, takie jak numery telefonów i adresy, są poprawne.

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Zabezpieczanie Microsoft 365 jak najbezpieczniejsi

Subskrypcja Microsoft 365 jest wyposażona w zaawansowany zestaw funkcji zabezpieczeń, za pomocą których można chronić dane i użytkowników.  Korzystaj z planu Microsoft 365 zabezpieczeń — najważniejsze priorytety w ciągu pierwszych [30, 90](security-roadmap.md) dni i nie tylko, aby wdrożyć zalecane przez firmę Microsoft najważniejsze wskazówki dotyczące zabezpieczania Microsoft 365 dzierżawy.

- Zadania, które można wykonać w ciągu pierwszych 30 dni. Mają one natychmiastowy wpływ i mają niski wpływ na twoich użytkowników.
- Zadania, które można wykonać w ciągu 90 dni. Planowanie i implementacja tych aplikacji trwa nieco dłużej, ale znacznie poprawia twoje działania w zakresie zabezpieczeń.
- Dłużej niż 90 dni. Te ulepszenia działają w ciągu pierwszych 90 dni.

## <a name="see-also"></a>Zobacz też

- [Wykrywanie i rozwiązywanie problemów z Outlook i atakami po formularzach niestandardowych w formularzach niestandardowych w Microsoft 365](detect-and-remediate-outlook-rules-forms-attack.md)
- [Centrum skarg internetowych do zbrodni](https://www.ic3.gov/Home/Ransomware)
- [Komisja papierów wartościowych i Exchange — oszustwo "wyłudzanie informacji"](https://www.sec.gov/investor/pubs/phishing.htm)
- Aby zgłosić spam bezpośrednio do firmy Microsoft i administratora [Użyj dodatku Wiadomość raportu](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2)
