---
title: Przeszukiwanie dziennika inspekcji w celu rozwiązania typowych scenariuszy
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Dowiedz się, jak używać narzędzia Microsoft 365 przeszukiwania dziennika inspekcji w celu rozwiązywania typowych problemów z obsługą kont e-mail.
ms.openlocfilehash: 496729c7955448519d6cb1447e08b5a4b15aa655
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63013762"
---
# <a name="search-the-audit-log-to-investigate-common-support-issues"></a>Przeszukiwanie dziennika inspekcji w celu zbadania typowych problemów z obsługą

W tym artykule opisano, jak korzystać z narzędzia do przeszukiwania dziennika inspekcji w celu dalszego zbadania typowych problemów z pomocą techniczną. Obejmuje to korzystanie z dziennika inspekcji w celu:

- Znajdowanie adresu IP komputera używanego do uzyskiwania dostępu do naruszonego konta
- Określanie, kto s skonfigurować przesyłanie dalej poczty e-mail dla skrzynki pocztowej
- Ustalanie, czy użytkownik usunął elementy poczty e-mail w jego skrzynce pocztowej
- Określanie, czy użytkownik utworzył regułę skrzynki odbiorczej
- Badanie przyczyny pomyślnego logowania użytkownika spoza organizacji
- Wyszukiwanie działań w skrzynce pocztowej wykonanych przez użytkowników z licencjami innymi niż E5
- Wyszukiwanie działań w skrzynce pocztowej wykonywanych przez użytkowników delegowanych

## <a name="using-the-audit-log-search-tool"></a>Korzystanie z narzędzia do przeszukiwania dziennika inspekcji

Wszystkie scenariusze rozwiązywania problemów opisane w tym artykule są oparte na użyciu narzędzia do przeszukiwania dziennika inspekcji w p Centrum zgodności platformy Microsoft 365. W tej sekcji wymieniono uprawnienia wymagane do przeszukiwania dziennika inspekcji oraz instrukcje dotyczące uzyskiwania dostępu do dzienników inspekcji i uruchamiania ich. W każdej sekcji scenariuszy wyjaśniono, jak skonfigurować zapytanie przeszukiwania dziennika inspekcji oraz co należy znaleźć w szczegółowych informacjach w rekordach inspekcji, które są zgodne z kryteriami wyszukiwania.

### <a name="permissions-required-to-use-the-audit-log-search-tool"></a>Uprawnienia wymagane do korzystania z narzędzia do przeszukiwania dziennika inspekcji

Do przeszukiwania dziennika inspekcji View-Only musi być przypisana rola Dzienniki inspekcji Exchange Online Dzienniki inspekcji. Domyślnie te role są przypisane do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie Uprawnienia w centrum  <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a>. Administratorzy globalni w Office 365 i Microsoft 365 są automatycznie dodawana jako członkowie grupy ról Zarządzanie organizacją w programie Exchange Online. Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami ról w Exchange Online](/Exchange/permissions-exo/role-groups).

### <a name="running-audit-log-searches"></a>Uruchamianie przeszukiwań dziennika inspekcji

W tej sekcji opisano podstawowe informacje dotyczące tworzenia i uruchamiania przeszukiwań dziennika inspekcji. Skorzystaj z tych instrukcji jako punktu wyjścia dla każdego scenariusza rozwiązywania problemów w tym artykule. Aby uzyskać bardziej szczegółowe instrukcje krok po kroku, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md#step-1-run-an-audit-log-search).

1. Przejdź do <https://compliance.microsoft.com/auditlogsearch> konta służbowego lub szkolnego i zaloguj się.
  
    Zostanie **wyświetlona** strona Inspekcja.
  
    ![Skonfiguruj kryteria, a następnie wybierz pozycję Wyszukaj, aby uruchomić wyszukiwanie.](../media/AuditLogSearchPage1.png)
  
2. Możesz skonfigurować następujące kryteria wyszukiwania. W każdym scenariuszu rozwiązywania problemów w tym artykule zaleca się stosowanie konkretnych wskazówek dotyczących konfigurowania tych pól.
  
   a. **Data rozpoczęcia** **i Data zakończenia.** Wybierz zakres dat i godzin, aby wyświetlić zdarzenia, które wystąpiły w tym okresie. Domyślnie jest zaznaczonych ostatnich siedem dni. Data i godzina są przedstawiane w formacie uniwersalnego czasu koordynowaowego (UTC). Maksymalny zakres dat, który można określić, to 90 dni.

   b. **Działania:** Wybierz listę rozwijaną, aby wyświetlić działania, które można wyszukać. Po uruchomieniu wyszukiwania są wyświetlane tylko rekordy inspekcji dotyczące wybranych działań. Zaznaczenie **opcji Pokaż wyniki dla wszystkich działań** powoduje wyświetlenie wyników dla wszystkich działań spełniających pozostałe kryteria wyszukiwania. W niektórych scenariuszach rozwiązywania problemów musisz również pozostawić to pole puste.
  
    c. **Użytkownicy:** Kliknij w tym polu, a następnie wybierz co najmniej jednego użytkownika, dla których chcesz wyświetlić wyniki wyszukiwania. Na liście wyników zostaną wyświetlone rekordy inspekcji wybranych działań wykonanych przez użytkowników wybranych w tym polu. Jeśli pozostawisz to pole puste, zostaną zwrócone wpisy dotyczące wszystkich użytkowników (i kont usług) w organizacji.
  
    d. **Plik, folder lub witryna:** Wpisz część lub całą nazwę pliku lub folderu, aby wyszukać działania związane z plikiem folderu zawierającym określone słowo kluczowe. Możesz również określić adres URL pliku lub folderu. Jeśli używasz adresu URL, upewnij się, że wpisz pełną ścieżkę adresu URL lub jeśli wpiszemy tylko część adresu URL, nie dołączaj żadnych znaków specjalnych ani spacji. Jeśli pozostawisz to pole puste, zostaną zwrócone wpisy dotyczące wszystkich plików i folderów w organizacji. To pole pozostaje puste we wszystkich scenariuszach rozwiązywania problemów możliwych do rozwiązania w tym artykule.
  
3. Wybierz **pozycję** Wyszukaj, aby uruchomić wyszukiwanie z użyciem kryteriów wyszukiwania.
  
    Wyniki wyszukiwania zostaną załadowane i po chwili wyświetlone na stronie w narzędziu do przeszukiwania dziennika inspekcji. Każda sekcja tego artykułu zawiera wskazówki dotyczące czynności, których należy szukać w kontekście konkretnego scenariusza rozwiązywania problemów.

    Aby uzyskać więcej informacji na temat wyświetlania i eksportowania wyników przeszukiwania dziennika inspekcji, zobacz:

    - [Wyświetlanie wyników wyszukiwania](search-the-audit-log-in-security-and-compliance.md#step-2-view-the-search-results)
  
    - [Eksportowanie wyników wyszukiwania](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file)

## <a name="find-the-ip-address-of-the-computer-used-to-access-a-compromised-account"></a>Znajdowanie adresu IP komputera używanego do uzyskiwania dostępu do naruszonego konta

Adres IP odpowiadający działaniu wykonywanego przez dowolnego użytkownika jest uwzględniany w większości rekordów inspekcji. Informacje o używanym kliencie są również zawarte w rekordzie inspekcji.

Poniżej opisano, jak skonfigurować zapytanie przeszukiwania dziennika inspekcji w tym scenariuszu:

**Działania:** Jeśli jest to istotne dla danej sprawy, wybierz konkretne działanie do wyszukania. Aby rozwiązać problemy z naruszonymi kontami, rozważ wybranie działań użytkownika zalogowanych do skrzynki pocztowej w obszarze Exchange **skrzynce pocztowej**. W ten sposób są zwracane rekordy inspekcji pokazujące adres IP, który był podany podczas logowania do skrzynki pocztowej. W przeciwnym razie pozostaw to pole puste, aby zwrócić rekordy inspekcji dla wszystkich działań. 

> [!TIP]
> Pozostawienie tego pola pustego spowoduje zwrócenie **działań userLoggedIn**, które jest działaniem Azure Active Directory, które wskazuje, że ktoś zalogował się do konta użytkownika. Użyj filtrowania w wynikach wyszukiwania, aby wyświetlić **rekordy inspekcji UserLoggedIn** .

**Data rozpoczęcia** **i Data zakończenia:** wybierz zakres dat, który ma zastosowanie do twojego badania.

**Użytkownicy:** Jeśli badasz naruszone konto, wybierz użytkownika, którego konto zostało naruszone. W ten sposób są zwracane rekordy inspekcji dotyczące działań wykonywanych przez to konto użytkownika.

**Plik, folder lub witryna:** Pozostaw to pole puste.

Po uruchomieniu wyszukiwania adres IP każdego działania jest wyświetlany w kolumnie Adres **IP** w wynikach wyszukiwania. Wybierz rekord w wynikach wyszukiwania, aby wyświetlić bardziej szczegółowe informacje na stronie wysuwu.

## <a name="determine-who-set-up-email-forwarding-for-a-mailbox"></a>Określanie, kto s skonfigurować przesyłanie dalej poczty e-mail dla skrzynki pocztowej

Jeśli dla skrzynki pocztowej skonfigurowano przesyłanie dalej wiadomości e-mail, wiadomości e-mail wysyłane do tej skrzynki są przesyłane dalej do innej skrzynki pocztowej. Wiadomości można przesyłać dalej do użytkowników w organizacji lub poza nią. Podczas przesyłania dalej poczty e-mail w skrzynce pocztowej jest używane Exchange Online cmdlet **Set-Mailbox**.

Poniżej opisano, jak skonfigurować zapytanie przeszukiwania dziennika inspekcji w tym scenariuszu:

**Działania:** Pozostaw to pole puste, aby wyszukiwanie zwracało rekordy inspekcji dla wszystkich działań. Jest to konieczne w celu zwrócenia wszystkich rekordów inspekcji związanych z poleceniem cmdlet **Set-Mailbox** .

**Data rozpoczęcia** **i Data zakończenia:** wybierz zakres dat, który ma zastosowanie do twojego badania.

**Użytkownicy:** Jeśli nie badasz problemu z przesyłaniem dalej poczty e-mail dla określonego użytkownika, pozostaw to pole puste. Dzięki temu można sprawdzić, czy dla każdego użytkownika zostało ustawione przesyłanie dalej poczty e-mail.

**Plik, folder lub witryna:** Pozostaw to pole puste.

Po uruchomieniu wyszukiwania wybierz pozycję **Filtruj wyniki** na stronie wyników wyszukiwania. W polu w obszarze **nagłówka** kolumny Działanie wpisz **set-mailbox** , aby były wyświetlane tylko rekordy inspekcji związane z poleceniem cmdlet **Set-Mailbox** .

![Filtrowanie wyników przeszukiwania dziennika inspekcji.](../media/emailforwarding1.png)

W tym momencie należy przyjrzeć się szczegółom każdego rekordu inspekcji, aby ustalić, czy dane działanie jest związane z przesyłaniem dalej poczty e-mail. Wybierz rekord inspekcji, aby wyświetlić stronę **wysuwaną** Szczegóły, a następnie wybierz **pozycję Więcej informacji**. Na poniższym zrzucie ekranu i w opisach wyróżniono informacje wskazujące, że w skrzynce pocztowej zostało ustawione przesyłanie dalej wiadomości e-mail.

![Szczegółowe informacje z rekordu inspekcji.](../media/emailforwarding2.png)

a. W polu **ObjectId** jest wyświetlany alias skrzynki pocztowej, dla których ustawiono przesyłanie dalej wiadomości e-mail. Ta skrzynka pocztowa jest również wyświetlana w **kolumnie Element** na stronie wyników wyszukiwania.

b. W polu **Parameters** wartość *ForwardingSmtpAddress* oznacza, że w skrzynce pocztowej ustawiono przesyłanie dalej wiadomości e-mail. W tym przykładzie poczta jest przesyłana dalej na adres e-mike@contoso.com, który znajduje się poza alpinehouse.onmicrosoft.com organizacji.

c. Wartość *True* *parametru DeliverToMailboxAndForward* oznacza, że kopia wiadomości jest dostarczana do usługi sarad@alpinehouse.onmicrosoft.com i jest przesyłana na adres  e-mail określony w parametrze *ForwardingSmtpAddress*, który w tym przykładzie jest mike@contoso.com. Jeśli dla parametru *DeliverToMailboxAndForward* ustawiono wartość *False*, wiadomość e-mail jest przesyłana dalej tylko na adres określony przez parametr *ForwardingSmtpAddress* . Nie jest ona dostarczana do skrzynki pocztowej określonej w polu **ObjectId** .

d. Pole **UserId** wskazuje użytkownika, który ustawi przesyłanie dalej poczty e-mail w skrzynce pocztowej określonej w polu **ObjectId** . Ten użytkownik jest również wyświetlany w **kolumnie Użytkownik** na stronie wyników wyszukiwania. W tym przypadku wygląda na to, że właściciel skrzynki pocztowej ustawił przesyłanie dalej wiadomości e-mail w swojej skrzynce pocztowej.

Jeśli stwierdzisz, że w skrzynce pocztowej nie powinno być ustawione przesyłanie dalej poczty e-mail, możesz ją usunąć, uruchamiając następujące polecenie w programie Exchange Online PowerShell:

```powershell
Set-Mailbox <mailbox alias> -ForwardingSmtpAddress $null 
```

Aby uzyskać więcej informacji na temat parametrów dotyczących przesyłania dalej poczty [e-mail, zobacz artykuł Set-Mailbox](/powershell/module/exchange/set-mailbox) .

## <a name="determine-if-a-user-deleted-email-items"></a>Określanie, czy użytkownik usunął elementy poczty e-mail

Począwszy od stycznia 2019 r., firma Microsoft domyślnie włączona jest rejestrowanie inspekcji skrzynki pocztowej dla wszystkich organizacji Office 365 i firmy Microsoft. Oznacza to, że niektóre akcje wykonane przez właścicieli skrzynek pocztowych są automatycznie rejestrowane, a odpowiadające im rekordy inspekcji skrzynki pocztowej są dostępne podczas wyszukiwania ich w dzienniku inspekcji skrzynki pocztowej. Przed domyślnym włączeniem inspekcji skrzynki pocztowej trzeba było ręcznie włączyć tę funkcję dla wszystkich skrzynek pocztowych użytkowników w organizacji. 

Rejestrowane domyślnie akcje skrzynki pocztowej obejmują akcje skrzynek pocztowych SoftDelete i HardDelete wykonywane przez właścicieli skrzynek pocztowych. Oznacza to, że możesz wykonać poniższe czynności, aby przeszukać dziennik inspekcji w poszukiwaniu zdarzeń związanych z usuniętymi elementami poczty e-mail. Aby uzyskać więcej informacji na temat domyślnego tematu inspekcji skrzynki pocztowej, zobacz [Zarządzanie inspekcją skrzynki pocztowej](enable-mailbox-auditing.md).

Poniżej opisano, jak skonfigurować zapytanie przeszukiwania dziennika inspekcji w tym scenariuszu:

**Działania:** W **Exchange skrzynce pocztowej** wybierz co najmniej jedno z następujących działań:

- **Usunięto wiadomości z folderu Elementy usunięte:** To działanie odpowiada akcji inspekcji **skrzynki pocztowej SoftDelete** . To działanie jest również rejestrowane, gdy użytkownik trwale usunie element, zaznaczając go i naciskając klawisze **Shift+Delete**. Po trwałym usunięciu elementu użytkownik może go odzyskać do momentu wygaśnięcia okresu przechowywania elementów usuniętych.

- **Przeczyszczona wiadomości ze skrzynki pocztowej:** To działanie odpowiada akcji inspekcji **skrzynki pocztowej HardDelete** . Jest on rejestrowany, gdy użytkownik przeczyści element z folderu Elementy do odzyskania. Administratorzy mogą używać narzędzia Wyszukiwanie zawartości w Centrum zabezpieczeń i zgodności, aby wyszukiwać i odzyskiwać przeczyszone elementy do momentu wygaśnięcia okresu przechowywania elementów usuniętych lub dłużej, jeśli skrzynka pocztowa użytkownika znajduje się w a hold.

**Data rozpoczęcia** **i Data zakończenia:** wybierz zakres dat, który ma zastosowanie do twojego badania.

**Użytkownicy:** Jeśli wybierzesz użytkownika w tym polu, narzędzie do przeszukiwania dziennika inspekcji zwróci rekordy inspekcji elementów poczty e-mail usuniętych przez użytkownika (SoftDeleted lub HardDeleted) przez użytkownika. Czasami użytkownik, który usunie wiadomość e-mail, może nie być właścicielem skrzynki pocztowej.

**Plik, folder lub witryna:** Pozostaw to pole puste.

Po uruchomieniu wyszukiwania można filtrować wyniki wyszukiwania, aby wyświetlić rekordy inspekcji w poszukiwaniu elementów usuniętych "miękko" lub elementów trudno usuniętych. Wybierz rekord inspekcji, aby wyświetlić stronę **wysuwaną** Szczegóły, a następnie wybierz **pozycję Więcej informacji**. W polu **Elementy** objęte problemem są wyświetlane dodatkowe informacje dotyczące usuniętego elementu, takie jak wiersz tematu i lokalizacja usuniętego elementu. Na poniższych zrzutach ekranu przedstawiono przykładowe pole **AffectedItems** (Elementy objęte problemem) z elementu "miękkiego usunięcia" i elementu trudno usuniętego.

**Example of AffectedItems field for soft-deleted item**

![Rekord inspekcji elementu "miękkiego usunięcia".](../media/softdeleteditem.png)

**Example of AffectedItems field for hard-deleted item**

![Rekord inspekcji trudnego do usunięcia elementu wiadomości e-mail.](../media/harddeleteditem.png)

### <a name="recover-deleted-email-items"></a>Odzyskiwanie usuniętych elementów wiadomości e-mail

Użytkownicy mogą odzyskać elementy usunięte "miękkie", jeśli okres przechowywania elementów usuniętych nie wygasł. W Exchange Online domyślny okres przechowywania elementów usuniętych wynosi 14 dni, ale administratorzy mogą zwiększyć to ustawienie do maksymalnie 30 dni. Wskaż użytkownikom artykuł Odzyskiwanie [usuniętych elementów lub wiadomości e-Outlook w sieci Web,aby](https://support.office.com/article/Recover-deleted-items-or-email-in-Outlook-Web-App-C3D8FC15-EEEF-4F1C-81DF-E27964B7EDD4) uzyskać instrukcje dotyczące odzyskiwania elementów usuniętych.

Jak wyjaśniono wcześniej, administratorzy mogą odzyskać elementy usunięte, jeśli okres przechowywania elementów usuniętych nie wygasł lub jeśli skrzynka pocztowa znajduje się w stanie przechowywania — w takim przypadku elementy są przechowywane do czasu wygaśnięcia czasu trwania przechowywania. Po uruchomieniu wyszukiwania zawartości elementy usunięte "miękkie" i trudne do usunięcia w folderze Elementy do odzyskania są zwracane w wynikach wyszukiwania, jeśli są zgodne z zapytaniem wyszukiwania. Aby uzyskać więcej informacji na temat uruchamiania wyszukiwań zawartości, zobacz [Wyszukiwanie zawartości w programie Office 365](content-search.md).

> [!TIP]
> Aby wyszukać usunięte elementy wiadomości e-mail, wyszukaj cały wiersz tematu lub jego część, który jest wyświetlany w polu **Elementy** objęte problemem w rekordzie inspekcji.

## <a name="determine-if-a-user-created-an-inbox-rule"></a>Określanie, czy użytkownik utworzył regułę skrzynki odbiorczej

Gdy użytkownicy tworzą regułę skrzynki odbiorczej dla swojej Exchange Online pocztowej, odpowiedni rekord inspekcji jest zapisywany w dzienniku inspekcji. Aby uzyskać więcej informacji na temat reguł skrzynki odbiorczej, zobacz:

- [Używanie reguł skrzynki odbiorczej w Outlook w sieci Web](https://support.office.com/article/use-inbox-rules-in-outlook-on-the-web-8400435c-f14e-4272-9004-1548bb1848f2)
- [Zarządzanie wiadomościami e-mail Outlook użyciu reguł](https://support.office.com/article/Manage-email-messages-by-using-rules-C24F5DEA-9465-4DF4-AD17-A50704D66C59)

Poniżej opisano, jak skonfigurować zapytanie przeszukiwania dziennika inspekcji w tym scenariuszu:

**Działania:** W **Exchange skrzynce pocztowej** wybierz co najmniej jedno z następujących działań:

- **New-InboxRule Create new inbox rule from Outlook Web App**. To działanie zwraca rekordy inspekcji, gdy reguły skrzynki odbiorczej są tworzone Outlook sieci Web lub Exchange Online PowerShell.

- **Zaktualizowane reguły skrzynki odbiorczej z Outlook klienta**. To działanie zwraca rekordy inspekcji, gdy reguły skrzynki odbiorczej są tworzone, modyfikowane lub usuwane za pomocą Outlook klasycznego.

**Data rozpoczęcia** **i Data zakończenia:** wybierz zakres dat, który ma zastosowanie do twojego badania.

**Użytkownicy:** Jeśli nie badasz określonego użytkownika, pozostaw to pole puste. Ułatwia to identyfikowanie nowych reguł skrzynki odbiorczej, które są ustawione przez dowolnego użytkownika.

**Plik, folder lub witryna:** Pozostaw to pole puste.

Po uruchomieniu wyszukiwania w wynikach wyszukiwania zostaną wyświetlone wszystkie rekordy inspekcji tego działania. Wybierz rekord inspekcji, aby wyświetlić stronę **wysuwaną** Szczegóły, a następnie wybierz **pozycję Więcej informacji**. Informacje o ustawieniach reguły skrzynki odbiorczej są wyświetlane w polu **Parametry** . Poniższy zrzut ekranu i opisy podkreślą informacje dotyczące reguł skrzynki odbiorczej.

![Rekord inspekcji dla nowej reguły skrzynki odbiorczej.](../media/NewInboxRuleRecord.png)

a. W polu **ObjectId** jest wyświetlana pełna nazwa reguły skrzynki odbiorczej. Ta nazwa zawiera alias skrzynki pocztowej użytkownika (na przykład Ewa) i nazwę reguły skrzynki odbiorczej (na przykład "Przenoszenie wiadomości od administratora").

b. W **polu Parametry** jest wyświetlany warunek reguły skrzynki odbiorczej. W tym przykładzie warunek jest określony przez *parametr From* (Od). Wartość zdefiniowana dla *parametru From* (Od) wskazuje, że reguła skrzynki odbiorczej działa w wiadomościach e-mail wysyłanych przez admin@alpinehouse.onmicrosoft.com. Aby uzyskać pełną listę parametrów, których można użyć do definiowania warunków reguł skrzynki odbiorczej, zobacz artykuł [Nowa Skrzynka odbiorcza.](/powershell/module/exchange/new-inboxrule)

c. Parametr *MoveToFolder* określa akcję reguły skrzynki odbiorczej. W tym przykładzie wiadomości otrzymane z aplikacji admin@alpinehouse.onmicrosoft.com są przenoszone do folderu o nazwie *AdminSearch*. Pełną listę parametrów[](/powershell/module/exchange/new-inboxrule), których można użyć do zdefiniowania akcji reguły skrzynki odbiorczej, można również znaleźć w artykule Nowa skrzynka odbiorcza.

d. Pole **UserId** wskazuje użytkownika, który utworzył regułę skrzynki odbiorczej określoną w polu **ObjectId** . Ten użytkownik jest również wyświetlany w **kolumnie Użytkownik** na stronie wyników wyszukiwania.

## <a name="investigate-why-there-was-a-successful-login-by-a-user-outside-your-organization"></a>Badanie przyczyny pomyślnego logowania użytkownika spoza organizacji

Podczas przeglądania rekordów inspekcji w dzienniku inspekcji mogą być widać rekordy wskazujące, że użytkownik zewnętrzny został uwierzytelniony przez Azure Active Directory i pomyślnie zalogowany do organizacji. Administrator usługi contoso.onmicrosoft.com może na przykład zobaczyć rekord inspekcji pokazujący, że użytkownik z innej organizacji (na przykład fabrikam.onmicrosoft.com) pomyślnie zalogował się do contoso.onmicrosoft.com. Podobnie możesz zobaczyć rekordy inspekcji, które wskazują użytkowników, którzy mają konto Microsoft (MSA), takie jak Outlook.com lub Live.com, po pomyślnym zalogowaniu się do organizacji. W takich sytuacjach rejestrowane działanie to **Zalogowano użytkownika**. 

Takie działanie jest celowe. Azure Active Directory (Azure AD), usługa katalogowa, umożliwia tak zwane uwierzytelnianie *pass-through*, gdy użytkownik zewnętrzny próbuje uzyskać dostęp do witryny SharePoint lub lokalizacji OneDrive w organizacji. Gdy użytkownik zewnętrzny spróbuje to zrobić, zostanie wyświetlony monit o wprowadzenie poświadczeń. Usługa Azure AD używa poświadczeń do uwierzytelniania użytkownika, co oznacza, że tylko usługa Azure AD weryfikuje, czy użytkownik jest tym, kim jest. Wskaźnik pomyślnego logowania w rekordzie inspekcji jest wynikiem uwierzytelniania użytkownika w usłudze Azure AD. Pomyślne zalogowanie nie oznacza, że użytkownik mógł uzyskać dostęp do jakichkolwiek zasobów ani wykonywać żadnych innych akcji w organizacji. Wskazuje tylko, że użytkownik został uwierzytelniony w usłudze Azure AD. Aby użytkownik przekazać uprawnienia dostępu do zasobów usługi SharePoint lub OneDrive, użytkownik w Twojej organizacji musi jawnie udostępnić użytkownikowi zewnętrznego zasób, wysyłając do niego zaproszenie do udostępniania lub link do udostępniania anonimowego. 

> [!NOTE]
> Usługa Azure AD umożliwia uwierzytelnianie przekazać tylko w przypadku aplikacji innych *firm*, takich SharePoint Online i OneDrive dla Firm. Niedozwolone jest w przypadku innych aplikacji innych firm.

Oto przykład i opisy odpowiednich właściwości w rekordzie inspekcji dla użytkownika zalogowanego W  przypadku, gdy jest to wynik uwierzytelniania przekazać. Wybierz rekord inspekcji, aby wyświetlić stronę **wysuwaną** Szczegóły, a następnie wybierz **pozycję Więcej informacji**.

![Przykład rekordu inspekcji na celu pomyślnego uwierzytelnienia pass-przez.](../media/PassThroughAuth1.png)

   a. To pole wskazuje, że użytkownika, który próbował uzyskać dostęp do zasobu w organizacji, nie znaleziono w usłudze Azure AD organizacji.

   b. W tym polu jest wyświetlana nazwa UPN użytkownika zewnętrznego, który próbował uzyskać dostęp do zasobu w organizacji. Ten identyfikator użytkownika jest także identyfikowany we **właściwościach User** (Użytkownik) i **UserId** (Identyfikator użytkownika) w rekordzie inspekcji.

   c. Właściwość **ApplicationId** określa aplikację, która wyzwoliła żądanie logowania. Wartość 00000003-0000-0ff1-ce00-0000000000000 jest wyświetlana we właściwości ApplicationId tego rekordu inspekcji wskazuje na wartość SharePoint Online. OneDrive dla Firm także ten sam applicationId.

   d. Oznacza to, że uwierzytelnienie przekaże pomyślnie. Innymi słowy, użytkownik został pomyślnie uwierzytelniony w usłudze Azure AD. 

   e. Wartość **RecordType (Typ** Rekordu) dla **wartości 15** wskazuje, że rejestrowane działanie (UserLoggedIn) to zdarzenie logowania usługi tokenu bezpiecznego (STS) w usłudze Azure AD.

Aby uzyskać więcej informacji o innych właściwościach wyświetlanych w rekordzie inspekcji UserLoggedIn, zobacz informacje o schemacie związanych z usługą Azure AD w schemacie interfejsu [API](/office/office-365-management-api/office-365-management-activity-api-schema#azure-active-directory-base-schema) działań zarządzania Office 365.

Oto dwa przykłady scenariuszy, które w wyniku uwierzytelniania  pass-through pomyślnie zalogują się użytkownicy: 

  - Użytkownik z kontem Microsoft (takim jak SaraD@outlook.com) próbował uzyskać dostęp do dokumentu na koncie programu OneDrive dla Firm w programie fourthcoffee.onmicrosoft.com i nie ma odpowiedniego konta użytkownika gościa dla programu SaraD@outlook.com w programie fourthcoffee.onmicrosoft.com.

  - Użytkownik z kontem służbowym w organizacji (takiej jak pilarp@fabrikam.onmicrosoft.com) próbował uzyskać dostęp do witryny programu SharePoint w programie contoso.onmicrosoft.com i nie ma odpowiedniego konta użytkownika gościa dla konta pilarp@fabrikam.com w programie contoso.onmicrosoft.com.

### <a name="tips-for-investigating-successful-logins-resulting-from-pass-through-authentication"></a>Wskazówki do zbadania pomyślnych logowania wynikających z uwierzytelniania przekazać

- Wyszukaj w dzienniku inspekcji działania wykonane przez użytkownika zewnętrznego wskazanego w rekordzie inspekcji **zalogowanym** przez tego użytkownika. Wpisz nazwę UPN dla użytkownika zewnętrznego w **polu** Użytkownicy i użyj zakresu dat, jeśli jest to związane z danym scenariuszem. Można na przykład utworzyć wyszukiwanie przy użyciu następujących kryteriów wyszukiwania:

   ![Wyszukaj wszystkie działania wykonywane przez użytkownika zewnętrznego.](../media/PassThroughAuth2.png)

    Oprócz działań zalogowanych  przez użytkownika mogą być zwracane inne rekordy inspekcji, takie jak wskazujące użytkownikowi w organizacji zasoby udostępnione użytkownikowi zewnętrzneowi oraz to, czy użytkownik zewnętrzny uzyskał dostęp do udostępnionego użytkownikowi zewnętrznego, zmodyfikował lub pobrał udostępniony im dokument.

- Wyszukaj SharePoint udostępniania, które wskazywały, że plik został udostępniony użytkownikowi zewnętrzneowi określone przez użytkownika zalogowanego **do rekordu** inspekcji. Aby uzyskać więcej informacji, [zobacz Korzystanie z inspekcji udostępniania w dzienniku inspekcji](use-sharing-auditing.md).

- Wyeksportuj wyniki przeszukiwania dziennika inspekcji zawierające rekordy istotne dla twojego badania, aby można Excel innych działań związanych z użytkownikiem zewnętrznym. Aby uzyskać więcej informacji, zobacz  [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md).

## <a name="search-for-mailbox-activities-performed-by-users-with-non-e5-licenses"></a>Wyszukiwanie działań w skrzynce pocztowej wykonanych przez użytkowników z licencjami innymi niż E5

Nawet jeśli [](enable-mailbox-auditing.md) inspekcja skrzynek pocztowych jest domyślnie włączona w organizacji, możesz zauważyć, że w przypadku niektórych użytkowników nie znaleziono zdarzeń inspekcji skrzynki pocztowej w dziennikach inspekcji za pomocą centrum zgodności, polecenia cmdlet **Search-UnifiedAuditLog** lub interfejsu API działań zarządzania Office 365. Przyczyną tego jest to, że zdarzenia inspekcji skrzynki pocztowej zostaną zwrócone tylko użytkownikom z licencjami E5, gdy jedna z poprzednich metod przeszukiwania ujednoliconego dziennika inspekcji.

Aby pobrać rekordy dziennika inspekcji skrzynki pocztowej dla użytkowników niebędących użytkownikami E5, możesz wykonać jedno z następujących obejść:

- Ręczne włączanie inspekcji skrzynki pocztowej dla poszczególnych skrzynek pocztowych (uruchom `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true` polecenie w programie Exchange Online PowerShell). Po zakończeniu wyszukiwania działań inspekcji skrzynki pocztowej można użyć centrum zgodności, polecenia cmdlet **Search-UnifiedAuditLog** lub interfejsu API działań Office 365 zarządzania.
  
  > [!NOTE]
  > Jeśli inspekcja skrzynki pocztowej wydaje się już włączona w skrzynce pocztowej, ale w wynikach wyszukiwania nie są zwracane żadne wyniki, zmień wartość parametru _AuditEnabled na wartość parametru AuditEnabled_`$false`, a następnie z powrotem na `$true`.
  
- Użyj następujących poleceń cmdlet w programie Exchange Online PowerShell:

  - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) , aby przeszukać dziennik inspekcji skrzynki pocztowej dla określonych użytkowników.

  - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) to search the mailbox audit log for specific users and have the results sent via email to specified recipients.

## <a name="search-for-mailbox-activities-performed-in-a-specific-mailbox-including-shared-mailboxes"></a>Wyszukiwanie działań wykonywanych w skrzynce pocztowej w określonej skrzynce pocztowej (w tym udostępnionych skrzynek pocztowych)

W przypadku korzystania z  listy rozwijanej Użytkownicy w narzędziu do przeszukiwania dziennika inspekcji w centrum zgodności lub polecenia **Search-UnifiedAuditLog -UserIds** w programie Exchange Online PowerShell można wyszukiwać działania wykonywane przez określonego użytkownika. W przypadku działań inspekcji skrzynki pocztowej ten typ wyszukiwania będzie wyszukiwał działania wykonywane przez określonego użytkownika. Nie gwarantuje to, że wszystkie działania wykonywane w tej samej skrzynce pocztowej zostaną zwrócone w wynikach wyszukiwania. Na przykład przeszukiwanie dziennika inspekcji nie zwróci rekordów inspekcji w przypadku działań wykonanych przez użytkownika pełnomocnika, ponieważ wyszukiwanie działań w skrzynce pocztowej wykonanych przez określonego użytkownika nie spowoduje zwrócenia działań wykonanych przez użytkownika pełnomocnika z przypisanymi uprawnieniami dostępu do skrzynki pocztowej innego użytkownika. (Użytkownik pełnomocnika to osoba, która ma uprawnienia skrzynki pocztowej SendAs, SendOnBehalf lub FullAccess do skrzynki pocztowej innego użytkownika).

Ponadto korzystanie z listy  rozwijanej Użytkownik w narzędziu do przeszukiwania dziennika inspekcji lub za pomocą funkcji **Search-UnifiedAuditLog -UserIds** nie zwraca wyników działań wykonywanych w udostępnionej skrzynce pocztowej.

Aby wyszukać działania wykonywane w określonej skrzynce pocztowej lub działania wykonywane w udostępnionej skrzynce pocztowej, podczas uruchamiania polecenia cmdlet **Search-UnifiedAuditLog** użyj następującej składni:

```powershell
Search-UnifiedAuditLog  -StartDate <date> -EndDate <date> -FreeText (Get-Mailbox <mailbox identity).ExchangeGuid
```

Na przykład następujące polecenie zwraca rekordy inspekcji dotyczące działań wykonywanych w udostępnionej skrzynce pocztowej udostępnionej zespołu zgodności Contoso między sierpniem 2020 r. a październikiem 2020 r.:

```powershell
Search-UnifiedAuditLog  -StartDate 08/01/2020 -EndDate 10/31/2020 -FreeText (Get-Mailbox complianceteam@contoso.onmicrosoft.com).ExchangeGuid
```

Możesz również użyć polecenia cmdlet **Search-MailboxAuditLog** w celu wyszukania rekordów inspekcji działań wykonywanych w określonej skrzynce pocztowej. Obejmuje to wyszukiwanie działań wykonywanych w udostępnionej skrzynce pocztowej.

W poniższym przykładzie są zwracane rekordy dziennika inspekcji skrzynki pocztowej dotyczące działań wykonywanych w udostępnionej skrzynce pocztowej zespołu zgodności Contoso:

```powershell
Search-MailboxAuditLog -Identity complianceteam@contoso.onmicrosoft.com -StartDate 08/01/2020 -EndDate 10/31/2020 -ShowDetails
```

W poniższym przykładzie są zwracane rekordy dziennika inspekcji skrzynki pocztowej dotyczące działań wykonywanych w określonej skrzynce pocztowej przez użytkowników delegowanych:

```powershell
Search-MailboxAuditLog -Identity <mailbox identity> -StartDate <date> -EndDate <date> -LogonTypes Delegate -ShowDetails
```

Za pomocą polecenia cmdlet **New-MailboxAuditLogSearch** można także przeszukiwać dziennik inspekcji konkretnej skrzynki pocztowej i wysyłać wyniki za pośrednictwem poczty e-mail do określonych adresatów.