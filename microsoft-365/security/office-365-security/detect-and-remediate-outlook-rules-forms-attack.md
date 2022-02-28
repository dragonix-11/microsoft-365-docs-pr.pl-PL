---
title: Wykrywaj i reagotuj ataki Outlook formularzach niestandardowych.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: 04/23/2018
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
description: Dowiedz się, jak rozpoznać i rozwiązać te Outlook i formularze niestandardowe podszywają się pod formularze Office 365
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6c715552fedeefeb87206d889aa448609e8d7f60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983435"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Wykrywanie i rozwiązywanie problemów z Outlook i atakami po formularzach niestandardowych

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**Podsumowanie** Dowiedz się, jak rozpoznać i rozwiązać te Outlook i niestandardowe ataki w formularzach niestandardowych w programie Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Jaki jest atak Outlook i formularzy niestandardowych?

Gdy atakujący uzyska dostęp do organizacji, spróbuje ustalić jego stopkę, aby pozostać w domu lub wrócić do niego po ich odkryniu. To działanie jest nazywane *ustanawianiem mechanizmu stabilności*. Istnieją dwa sposoby, za pomocą których atakujący mogą Outlook mechanizmu utrwalania:

- Wykorzystywanie reguł Outlook.
- Wsuń formularze niestandardowe do Outlook.

Ponowne zainstalowanie Outlook, a nawet udzielenie osobie, której dotyczy problem, nowego komputera nie pomoże. Gdy nowa instalacja aplikacji Outlook się ze skrzynką pocztową, wszystkie reguły i formularze są synchronizowane z chmurą. Reguły lub formularze są zwykle zaprojektowane do uruchamiania kodu zdalnego i instalowania złośliwego oprogramowania na komputerze lokalnym. Złośliwe oprogramowanie ukradzi poświadczenia lub wykona inną aktywność aktywności.

Dobra wiadomość jest taka: jeśli dbasz o to, Outlook Twoi klienci pakietu Outlook są poprawki do najnowszej wersji, nie naraż się na zagrożenia, ponieważ bieżące ustawienia domyślne klienta Outlook blokują oba mechanizmy.

W atakach są zazwyczaj stosowane następujące wzorce:

**Reguły wykorzystujące**:

1. Atakujący ukraść poświadczenia użytkownika.

2. Atakujący może się do tego celu Exchange skrzynce pocztowej użytkownika (Exchange Online lokalnym lub lokalnym Exchange).

3. Atakujący tworzy w skrzynce pocztowej regułę przesyłania dalej skrzynki odbiorczej. Reguła przesyłania dalej jest wyzwalana, gdy skrzynka pocztowa otrzymuje określoną wiadomość od atakującego, która jest taka, która jest taka jak jej zasada. Warunki reguły i format wiadomości są dostosowane do siebie nawzajem.

4. Atakujący wysyła wiadomość e-mail wyzwalacza do naruszonej skrzynki pocztowej, która jest nadal używana przez niczego nie podejrzewającego użytkownika.

5. Gdy do skrzynki pocztowej zostanie wyświetlony komunikat, który odpowiada regułom, zostanie zastosowana akcja reguły. Akcja reguły zwykle dotyczy uruchamiania aplikacji na serwerze zdalnym (WebDAV).

6. Zazwyczaj aplikacja instaluje złośliwe oprogramowanie na komputerze użytkownika (na przykład [PowerShell Empire](https://www.powershellempire.com/)).

7. Złośliwe oprogramowanie umożliwia atakującemu wykradzenie (lub ponownie kradzież) nazwy użytkownika i hasła lub innych poświadczeń z komputera lokalnego oraz wykonywanie innych złośliwych działań.

**Wykorzystywanie formularzy**:

1. Atakujący ukraść poświadczenia użytkownika.

2. Atakujący może się do tego celu Exchange skrzynce pocztowej użytkownika (Exchange Online lokalnym lub lokalnym Exchange).

3. Atakujący wstawia niestandardowy szablon formularza poczty do skrzynki pocztowej użytkownika. Formularz niestandardowy jest wyzwalany, gdy skrzynka pocztowa otrzymuje określoną wiadomość od atakującego, który wymaga, aby skrzynka pocztowa załadowała formularz niestandardowy. Formularz niestandardowy i format wiadomości są dostosowane do siebie nawzajem.

4. Atakujący wysyła wiadomość e-mail wyzwalacza do naruszonej skrzynki pocztowej, która jest nadal używana przez niczego nie podejrzewającego użytkownika.

5. Gdy skrzynka pocztowa otrzyma wiadomość, załaduje do skrzynki pocztowej wymagany formularz. Formularz uruchamia aplikację na serwerze zdalnym (WebDAV).

6. Zazwyczaj aplikacja instaluje złośliwe oprogramowanie na komputerze użytkownika (na przykład [PowerShell Empire](https://www.powershellempire.com/)).

7. Złośliwe oprogramowanie umożliwia atakującemu wykradzenie (lub ponownie kradzież) nazwy użytkownika i hasła lub innych poświadczeń z komputera lokalnego oraz wykonywanie innych złośliwych działań.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Jak może wyglądać atak w postaci podania reguł i formularzy niestandardowych Office 365?

Te mechanizmy nie są mało prawdopodobne do zauważenia przez użytkowników, a w niektórych przypadkach mogą być nawet niewidoczne dla nich. W tym artykule podano informacje, jak szukać dowolnych z siedmiu znaków (Wskaźników naruszenia zabezpieczeń) wymienionych poniżej. Jeśli znajdziesz dowolne z tych czynności, musisz podjąć kroki rozwiązywania problemów.

- **Wskaźniki naruszenia reguł**:
  - Reguła Akcja to uruchomienie aplikacji.
  - Reguła odwołuje się do pliku EXE, pliku ZIP lub adresu URL.
  - Na komputerze lokalnym poszukaj nowego procesu, który pochodzi z nowego Outlook PID.

- **Wskaźniki naruszenia bezpieczeństwa formularzy niestandardowych**:
  - Formularze niestandardowe prezentują się jako klasa wiadomości.
  - Klasa wiadomości zawiera kod wykonywalny.
  - Zazwyczaj złośliwe formularze są przechowywane w folderach biblioteki formularzy osobistych lub skrzynki odbiorczej.
  - Formularz nosi nazwę IPM. Uwaga. [nazwa niestandardowa].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Procedura znajdowania znaków tego ataku i potwierdzania go

Możesz potwierdzić atak za pomocą jednej z następujących metod:

- Ręcznie sprawdź reguły i formularze dla każdej skrzynki pocztowej przy użyciu Outlook klienta. Ta metoda jest dokładna, ale można sprawdzać tylko jedną skrzynkę pocztową na raz. Ta metoda może być bardzo czasochłonne, jeśli masz wielu użytkowników do sprawdzenia i może również zainfekować komputer, z których korzystasz.

- Użyj skryptu [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell, aby automatycznie zrzucić wszystkie reguły przesyłania dalej poczty i formularze niestandardowe dla wszystkich użytkowników w waności. Jest to najszybszy i najbezpieczniejszy sposób przy jak najmniejszym narzucie.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Potwierdź atak reguły przy użyciu Outlook klienta

1. Otwórz klienta Outlook jako użytkownik. Użytkownik może potrzebować Twojej pomocy przy analizie reguł w jego skrzynce pocztowej.

2. Aby zapoznać [się z](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) procedurami otwierania interfejsu reguł w programie Outlook, zobacz Zarządzanie wiadomościami e-mail za pomocą Outlook.

3. Odszukaj reguły, których użytkownik nie tworzy, oraz wszelkie nieoczekiwane reguły lub reguły z podejrzanymi nazwami.

4. W opisie reguły znajdziesz akcje reguły, które uruchamiają się i odwołują się do .EXE, .ZIP lub uruchamiają adres URL.

5. Poszukaj nowych procesów, które zaczynają Outlook identyfikatora procesu. Zobacz [Znajdowanie identyfikatora procesu](/windows-hardware/drivers/debugger/finding-the-process-id).

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Procedura potwierdzania ataków przy użyciu klienta Outlook Forms

1. Otwórz klienta Outlook jako użytkownika.

2. Postępuj zgodnie z instrukcjami [na stronie Pokazywanie karty Deweloper](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45) dla wersji programu Outlook.

3. Otwórz teraz widoczną kartę Deweloper w programie Outlook a następnie kliknij **pozycję projektowanie formularza**.

4. Wybierz **skrzynkę odbiorczą** z **listy Szukaj w** . Poszukaj dowolnych formularzy niestandardowych. Formularze niestandardowe występują na tyle rzadko, że jeśli istnieją w ogóle jakiekolwiek formularze niestandardowe, warto przyjrzeć się bliżej.

5. Zbadaj wszelkie formularze niestandardowe, zwłaszcza te oznaczone jako ukryte.

6. Otwórz dowolne formularze niestandardowe i w grupie **Formularz** kliknij pozycję **Wyświetl** kod, aby sprawdzić, co jest uruchamiane po załadowaniu formularza.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Procedura potwierdzania ataków dotyczących reguł i formularzy przy użyciu programu PowerShell

Najprostszym sposobem weryfikowania reguł lub formularzy niestandardowych jest uruchomienie skryptu [ programuGet-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell. Ten skrypt nawiązuje połączenie z każdą skrzynką pocztową w dzierżawie i łączy wszystkie reguły i formularze w dwa .csv pliki.

#### <a name="pre-requisites"></a>Wymagania wstępne

Uruchomienie skryptu będzie wymagało uprawnień administratora globalnego, ponieważ skrypt nawiązuje połączenie z każdą skrzynką pocztową w zakresie obsługi klienta w celu odczytania reguł i formularzy.

1. Zaloguj się na komputerze, z których zostanie uruchomiony skrypt, z uprawnieniami administratora lokalnego.

2. Pobierz lub skopiuj skrypt Get-AllTenantRulesAndForms.ps1 z GitHub do folderu, z którego zostanie uruchomiony. Skrypt utworzy dwa pliki z sygnaturami dat do tego folderu, pliki MailboxFormsExport-yyyy-mm-dd.csv i MailboxRulesExport-yyyy-mm-dd.csv.

3. Otwórz wystąpienie programu PowerShell jako administrator i otwórz folder, w którym został zapisany skrypt.

4. Uruchom ten wiersz polecenia programu PowerShell w następujący sposób: `.\Get-AllTenantRulesAndForms.ps1`\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Interpretowanie danych wyjściowych

- ***MailboxRulesExport-yyyy-mm-dd*.csv**: Zbadaj reguły (jeden na wiersz) pod uwagę warunki akcji, które obejmują aplikacje lub pliki wykonywalne:

  - **ActionType (kolumna A)**: Jeśli zobaczysz wartość "ID_ACTION_CUSTOM", reguła jest prawdopodobnie złośliwa.

  - **IsPotentiallyMali nieujemne (kolumna D)**: Jeśli ta wartość to "PRAWDA", reguła jest prawdopodobnie złośliwa.

  - **ActionCommand (kolumna G)**: Jeśli w tej kolumnie znajduje się lista aplikacji lub dowolnego pliku z rozszerzeniami programu .exe lub .zip albo nieznanym wpisem, który odwołuje się do adresu URL, reguła jest prawdopodobnie złośliwa.

- ***MailboxFormsExport-yyyy-mm-dd*.csv**: Na ogół rzadko używa się formularzy niestandardowych. Jeśli znajdziesz w tym skoroszycie, otwórz skrzynkę pocztową tego użytkownika i zbadasz sam formularz. Jeśli Twoja organizacja nie umieściła jej w tym miejscu celowo, prawdopodobnie jest ona złośliwa.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Jak zatrzymać i rozwiązać te Outlook dotyczące reguł i formularzy

Jeśli znajdziesz jakiekolwiek dowody na te ataki, działania naprawcze są proste, po prostu usuń regułę lub formularz ze skrzynki pocztowej. Możesz to zrobić za pomocą klienta Outlook lub przy użyciu zdalnej obsługi programu PowerShell w celu usunięcia reguł.

### <a name="using-outlook"></a>Korzystanie z Outlook

1. Zidentyfikuj wszystkie urządzenia używane przez użytkownika z Outlook. Wszystkie one muszą zostać wyczyszczone z potencjalnego złośliwego oprogramowania. Nie zezwalaj użytkownikowi na logowanie się i korzystanie z poczty e-mail, dopóki wszystkie urządzenia nie zostaną wyczyszczone.

2. Postępuj zgodnie z [instrukcjami Usuwanie reguły](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f) dla każdego urządzenia.

3. Jeśli nie masz pewności co do obecności innego złośliwego oprogramowania, możesz sformatować i ponownie zainstalować całe oprogramowanie na urządzeniu. W przypadku urządzeń przenośnych możesz wykonać instrukcje producentów, aby przywrócić obraz fabryczny.

4. Zainstaluj najnowsze wersje pakietu Outlook. Pamiętaj, że bieżąca wersja programu Outlook domyślnie blokuje oba typy tego typu ataków.

5. Po usunięciu wszystkich kopii offline skrzynki pocztowej zresetuj hasło użytkownika (użyj wysokiej jakości) i wykonaj czynności opisane w konfigurowanie uwierzytelniania wieloskładnikowego dla użytkowników, jeśli uwierzytelnianie wieloskładnikowe nie zostało jeszcze włączone.[](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) Dzięki temu poświadczenia użytkownika nie będą widoczne za pomocą innych środków (takich jak wyłudzanie informacji lub ponowne użycie hasła).

### <a name="using-powershell"></a>Korzystanie z programu PowerShell

Istnieją dwa zdalne polecenia cmdlet programu PowerShell, za pomocą których można usunąć lub wyłączyć niebezpieczne reguły. Po prostu postępuj zgodnie z instrukcjami.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Procedura dla skrzynek pocztowych na Exchange poczty

1. Połączenie się z serwerem Exchange przy użyciu zdalnej pracy programu PowerShell. Postępuj zgodnie z instrukcjami [w Połączenie, aby Exchange serwerach przy użyciu zdalnej pracy programu PowerShell](/powershell/exchange/connect-to-exchange-servers-using-remote-powershell).

2. Aby całkowicie usunąć jedną regułę, wiele reguł lub wszystkie reguły ze skrzynki pocztowej, użyj polecenia cmdlet [Remove-InboxRule](/powershell/module/exchange/Remove-InboxRule) .

3. Aby zachować regułę i jej zawartość do dalszego badania, użyj polecenia cmdlet [Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Procedura dla skrzynek pocztowych w programie Exchange Online

1. Postępuj zgodnie z instrukcjami [w Połączenie, aby Exchange Online przy użyciu programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Aby całkowicie usunąć jedną regułę, wiele reguł lub wszystkie reguły ze skrzynki pocztowej, użyj polecenia cmdlet [Reguła](/powershell/module/exchange/Remove-InboxRule) usuwania skrzynki odbiorczej.

3. Aby zachować regułę i jej zawartość do dalszego badania, użyj polecenia cmdlet [Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

## <a name="how-to-minimize-future-attacks"></a>Jak zminimalizować przyszłe ataki

### <a name="first-protect-your-accounts"></a>Najpierw: ochrona kont

Luki w zasadach i formularzach są używane przez atakującego tylko w przypadku kradzieży lub naruszenia jednego z kont użytkownika. Dlatego pierwszym krokiem, aby zapobiec używaniu tych luk w organizacji, jest agresywna ochrona kont użytkowników. Do najczęstszych sposobów naruszenia zabezpieczeń kont należy naruszenie hasła lub wyłudzania [informacji](https://www.microsoft.com/security/blog/2020/04/23/protecting-organization-password-spray-attacks/).

Najlepszym sposobem na ochronę kont użytkowników, a zwłaszcza kont administratora, jest skonfigurowanie uwierzytelniania [wieloskładnikowego dla użytkowników](../../admin/security-and-compliance/set-up-multi-factor-authentication.md). Należy również:

- Monitoruj sposób, w jaki uzyskujesz [dostęp do kont użytkowników i jak z nich korzystasz](/azure/active-directory/active-directory-view-access-usage-reports). Użytkownik nie może zapobiec początkowemu naruszeniu, ale skrócenie czasu trwania i wpływu naruszenia zostanie skrócone, wykrywając je szybciej. Za pomocą tych zasad [Office 365 Cloud App Security możesz](/cloud-app-security/what-is-cloud-app-security) monitorować Konta i ostrzegać Cię o nietypowej aktywności:

  - **Wiele nieudanych** prób logowania: Te profile zasad powodują profilowanie środowiska i wyzwalają alerty, gdy użytkownicy wykonują w jednej sesji wiele działań logowania nieudanych względem poziomu początkowego, co może wskazywać na próbę naruszenia zabezpieczeń.

  - **Niemożliwy podróż**: te zasady profileją Twoje środowisko i powodują wyzwalanie alertów, gdy działania tego samego użytkownika są wykrywane od tego samego użytkownika w różnych lokalizacjach w czasie krótszym niż oczekiwany czas podróży między tymi dwoma lokalizacjami. Może to oznaczać, że inny użytkownik używa tych samych poświadczeń. Wykrycie tego anomalii zachowania wymaga początkowego okresu nauki siedmiu dni, w trakcie którego uczy się wzorca aktywności nowego użytkownika.

  - **Nietypowe personifikowane działanie (** według użytkownika): Te profile zasad powodują profile Twojego środowiska i wyzwalają alerty, gdy użytkownicy wykonują w jednej sesji wiele personifikowanych działań względem poziomu początkowego, co może wskazywać na próbę naruszenia zabezpieczeń.

- Do zarządzania konfiguracjami [i zachowaniami zabezpieczeń konta](https://securescore.office.com/) Office 365 użyć narzędzia, takiego jak ocena bezpiecznego konta.

### <a name="second-keep-your-outlook-clients-current"></a>Po drugie: dbaj o aktualn Outlook klienta

W pełni zaktualizowane i uaktualnione wersje programu Outlook 2013 i 2016 domyślnie wyłączą akcję reguły/formularza "Uruchom aplikację". Zapewni to zablokowanie nawet w przypadku naruszenia konta przez atakującego, działania związane z regułami i formularzami zostaną zablokowane. Możesz zainstalować najnowsze aktualizacje i poprawki zabezpieczeń, korzystając z procedury opisanej w te [Office aktualizacji](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5).

Oto wersje poprawek dla Twoich klientów Outlook 2013 i 2016:

- **Outlook 2016**: 16.0.4534.1001 lub więcej.

- **Outlook 2013**: 15.0.4937.1000 lub więcej.

Aby uzyskać więcej informacji na temat poszczególnych poprawek zabezpieczeń, zobacz:

- [Outlook 2016 zabezpieczeń](https://support.microsoft.com/help/3191883)

- [poprawka Outlook 2013](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>Trzecie: Monitorowanie klientów Outlook klientach

Pamiętaj, że nawet w przypadku zainstalowania poprawek i aktualizacji możliwe jest, że atakujący może zmienić konfigurację komputera lokalnego w celu ponownego włączenia zachowania "Uruchom aplikację". Za pomocą [zaawansowanego zarządzania zasady grupy komputerami](/microsoft-desktop-optimization-pack/agpm/) możesz monitorować i wymuszać zasady komputera lokalnego na swoich klientach.

Możesz sprawdzić, czy funkcja "Uruchom aplikację" została ponownie włączona za pośrednictwem zastępowania w rejestrze, korzystając z informacji w tece Jak wyświetlić rejestr systemu przy użyciu [64-bitowych](https://support.microsoft.com/help/305097) wersji Windows. Sprawdź następujące podklucze:

- **Outlook 2016**:`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013**:`HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

Poszukaj klucza EnableUnsafeClientMailRules. Jeśli poprawka zabezpieczeń ma wartość 1, Outlook została zastąpiona, a komputer jest narażony na ataki formularzy/reguł. Jeśli ta wartość wynosi 0, akcja "Uruchom aplikację" zostanie wyłączona. Jeśli zainstalowano zaktualizowaną i zainstalowaną Outlook pakietu i ten klucz rejestru nie jest aktualny, wówczas system nie jest narażony na te ataki.

Klienci korzystający z lokalnych instalacji Exchange powinny rozważyć zablokowanie starszych wersji Outlook, które nie mają dostępnych poprawek. Szczegóły tego procesu można znaleźć w artykule Konfigurowanie blokowania [Outlook klienta](/exchange/configure-outlook-client-blocking-exchange-2013-help).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Zabezpieczanie Microsoft 365 jak najbezpieczniejsi

Subskrypcja Microsoft 365 jest wyposażona w zaawansowany zestaw funkcji zabezpieczeń, za pomocą których można chronić dane i użytkowników. Korzystaj z planu Microsoft 365 zabezpieczeń — najważniejsze priorytety w ciągu pierwszych [30, 90](security-roadmap.md) dni i nie tylko, aby wdrożyć zalecane przez firmę Microsoft najważniejsze wskazówki dotyczące zabezpieczania Microsoft 365 dzierżawy.

- Zadania, które można wykonać w ciągu pierwszych 30 dni. Mają one natychmiastowy efekt i mają niski wpływ na użytkowników.

- Zadania, które można wykonać w ciągu 90 dni. Planowanie i implementacja tych aplikacji trwa nieco dłużej, ale znacznie poprawia twoje działania w zakresie zabezpieczeń.

- Dłużej niż 90 dni. Te ulepszenia działają w ciągu pierwszych 90 dni.

## <a name="see-also"></a>Zobacz też:

- [Złośliwe Outlook przez](https://silentbreaksecurity.com/malicious-outlook-rules/) wpis zabezpieczeń SilentBreak na temat wektora reguł udostępnia szczegółowy przegląd sposobu działania Outlook zabezpieczeń.

- [W blogu](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) usługi Sensepost o aplikacji Mailrule Pwnage funkcja MAPI przez HTTP i skrzynkę pocztową omawiane jest narzędzie o nazwie Linijka, które umożliwia wykorzystywanie skrzynek pocztowych za pomocą Outlook pocztowych.

- [Outlook formularzy i powłoki w](https://sensepost.com/blog/2017/outlook-forms-and-shells/) blogu Sensepost na temat wektora zagrożeń Forms.

- [Linijka Codebase](https://github.com/sensepost/ruler)

- [Wskaźniki naruszenia linijki](https://github.com/sensepost/notruler/blob/master/iocs.md)