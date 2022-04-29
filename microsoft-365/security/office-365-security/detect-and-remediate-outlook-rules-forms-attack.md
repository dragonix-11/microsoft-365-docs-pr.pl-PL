---
title: Wykrywanie i korygowanie Outlook reguł i niestandardowych formularzy iniekcji ataków.
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
description: Dowiedz się, jak rozpoznawać i korygować Outlook reguły i niestandardowe formy ataków iniekcji w Office 365
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 10cbb57018cb0e7c30282ca2c89b6a8dab812e24
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131113"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Wykrywanie i korygowanie ataków na reguły Outlook i iniekcje formularzy niestandardowych

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Krótki opis** Dowiedz się, jak rozpoznawać i korygować Outlook reguły i niestandardowe ataki iniekcji formularzy w Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Jaki jest atak polegający na wstrzyknięciu reguł Outlook i formularzy niestandardowych?

Gdy osoba atakująca uzyska dostęp do Twojej organizacji, spróbuje ustanowić przyczółek, aby pozostać w organizacji lub wrócić do niej po odnalezieniu. To działanie jest *nazywane ustanawianiem mechanizmu trwałości*. Istnieją dwa sposoby, na jakie osoba atakująca może użyć Outlook w celu ustanowienia mechanizmu trwałości:

- Wykorzystując reguły Outlook.
- Przez wstrzyknięcie formularzy niestandardowych do Outlook.

Ponowne zainstalowanie Outlook, a nawet nadanie osobie, której dotyczy problem, nowego komputera nie pomoże. Gdy nowa instalacja Outlook łączy się ze skrzynką pocztową, wszystkie reguły i formularze są synchronizowane z chmury. Reguły lub formularze są zwykle przeznaczone do uruchamiania kodu zdalnego i instalowania złośliwego oprogramowania na komputerze lokalnym. Złośliwe oprogramowanie kradnie poświadczenia lub wykonuje inną nielegalną działalność.

Dobra wiadomość jest następująca: jeśli Outlook klientów zostanie poprawiona do najnowszej wersji, nie będziesz narażony na zagrożenie, ponieważ bieżące Outlook domyślne ustawienia klienta blokują oba mechanizmy.

Ataki zwykle są zgodne z następującymi wzorcami:

**Luki w zabezpieczeniach reguł**:

1. Osoba atakująca kradnie poświadczenia użytkownika.

2. Osoba atakująca loguje się do skrzynki pocztowej Exchange użytkownika (Exchange Online lub lokalnego Exchange).

3. Osoba atakująca tworzy regułę skrzynki odbiorczej przesyłania dalej w skrzynce pocztowej. Reguła przekazywania jest wyzwalana, gdy skrzynka pocztowa odbiera od osoby atakującej określoną wiadomość zgodną z warunkami reguły. Warunki reguły i format komunikatów są dostosowane do siebie nawzajem.

4. Osoba atakująca wysyła wiadomość e-mail wyzwalacza do zagrożonej skrzynki pocztowej, która jest nadal używana normalnie przez niczego nie podejrzewającego użytkownika.

5. Gdy skrzynka pocztowa otrzyma komunikat zgodny z warunkami reguły, zostanie zastosowana akcja reguły. Zazwyczaj akcją reguły jest uruchomienie aplikacji na serwerze zdalnym (WebDAV).

6. Zazwyczaj aplikacja instaluje złośliwe oprogramowanie na maszynie użytkownika (na przykład [w programie PowerShell Empire](https://www.powershellempire.com/)).

7. Złośliwe oprogramowanie pozwala atakującemu ukraść (lub ukraść ponownie) nazwę użytkownika i hasło użytkownika lub inne poświadczenia z komputera lokalnego i wykonywać inne złośliwe działania.

**Luki w zabezpieczeniach formularzy**:

1. Osoba atakująca kradnie poświadczenia użytkownika.

2. Osoba atakująca loguje się do skrzynki pocztowej Exchange użytkownika (Exchange Online lub lokalnego Exchange).

3. Osoba atakująca wstawia niestandardowy szablon formularza poczty do skrzynki pocztowej użytkownika. Formularz niestandardowy jest wyzwalany, gdy skrzynka pocztowa odbiera określoną wiadomość od osoby atakującej, która wymaga, aby skrzynka pocztowa załadował formularz niestandardowy. Formularz niestandardowy i format wiadomości są dostosowane do siebie nawzajem.

4. Osoba atakująca wysyła wiadomość e-mail wyzwalacza do zagrożonej skrzynki pocztowej, która jest nadal używana normalnie przez niczego nie podejrzewającego użytkownika.

5. Gdy skrzynka pocztowa odbiera wiadomość, skrzynka pocztowa ładuje wymagany formularz. Formularz uruchamia aplikację na serwerze zdalnym (WebDAV).

6. Zazwyczaj aplikacja instaluje złośliwe oprogramowanie na maszynie użytkownika (na przykład [w programie PowerShell Empire](https://www.powershellempire.com/)).

7. Złośliwe oprogramowanie pozwala atakującemu ukraść (lub ukraść ponownie) nazwę użytkownika i hasło użytkownika lub inne poświadczenia z komputera lokalnego i wykonywać inne złośliwe działania.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Jak może wyglądać atak polegający na wstrzyknięciu reguł i formularzy niestandardowych Office 365?

Te mechanizmy trwałości prawdopodobnie nie zostaną zauważone przez użytkowników, a w niektórych przypadkach mogą być nawet niewidoczne dla nich. W tym artykule opisano, jak wyszukać dowolny z siedmiu znaków (Wskaźniki kompromisu) wymienionych poniżej. Jeśli znajdziesz dowolną z nich, musisz wykonać kroki korygowania.

- **Wskaźniki naruszenia zabezpieczeń reguł**:
  - Akcja reguły polega na uruchomieniu aplikacji.
  - Reguła odwołuje się do pliku EXE, ZIP lub adresu URL.
  - Na komputerze lokalnym poszukaj nowego procesu, który pochodzi z Outlook PID.

- **Wskaźniki naruszenia zabezpieczeń formularzy niestandardowych**:
  - Formularze niestandardowe obecne jako własne klasy komunikatów.
  - Klasa Message zawiera kod wykonywalny.
  - Zazwyczaj złośliwe formularze są przechowywane w bibliotece formularzy osobistych lub folderach skrzynki odbiorczej.
  - Formularz ma nazwę IPM. Uwaga. [nazwa niestandardowa].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Kroki znajdowania oznak tego ataku i potwierdzania go

Aby potwierdzić atak, możesz użyć jednej z następujących metod:

- Ręcznie sprawdź reguły i formularze dla każdej skrzynki pocztowej przy użyciu klienta Outlook. Ta metoda jest dokładna, ale jednocześnie można zaznaczyć tylko jedną skrzynkę pocztową. Ta metoda może być bardzo czasochłonna, jeśli masz wielu użytkowników do sprawdzenia, a także może zainfekować komputer, który używasz.

- Użyj [ skryptuGet-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) programu PowerShell, aby automatycznie zrzucić wszystkie reguły przekazywania wiadomości e-mail i formularze niestandardowe dla wszystkich użytkowników dzierżawy. Jest to najszybsza i najbezpieczniejsza metoda z najmniejszym obciążeniem.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Potwierdzanie ataku reguł przy użyciu klienta Outlook

1. Otwórz użytkowników Outlook klienta jako użytkownika. Użytkownik może potrzebować Twojej pomocy w badaniu reguł w swojej skrzynce pocztowej.

2. Zapoznaj się [z artykułem Zarządzanie wiadomościami e-mail przy użyciu reguł](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59), aby zapoznać się z procedurami otwierania interfejsu reguł w Outlook.

3. Poszukaj reguł, których użytkownik nie utworzył, ani żadnych nieoczekiwanych reguł lub reguł o podejrzanych nazwach.

4. Poszukaj w opisie reguły akcji reguł, które uruchamiają się i aplikacji lub odwołują się do .EXE, .ZIP pliku lub do uruchamiania adresu URL.

5. Poszukaj nowych procesów, które zaczynają używać identyfikatora procesu Outlook. Zapoznaj się [z tematem Znajdowanie identyfikatora procesu](/windows-hardware/drivers/debugger/finding-the-process-id).

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Kroki potwierdzania ataku formularzy przy użyciu klienta Outlook

1. Otwórz użytkownika Outlook klienta jako użytkownika.

2. Wykonaj kroki opisane w [temacie Pokaż kartę Deweloper](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45) dla wersji Outlook użytkownika.

3. Otwórz teraz widoczną kartę dewelopera w Outlook i kliknij **pozycję Zaprojektuj formularz**.

4. Wybierz **skrzynkę odbiorczą** z listy **Wyszukaj w** . Poszukaj dowolnych formularzy niestandardowych. Formularze niestandardowe są na tyle rzadkie, że jeśli w ogóle masz formularze niestandardowe, warto przyjrzeć się bardziej szczegółowo.

5. Zbadaj wszelkie formularze niestandardowe, zwłaszcza te oznaczone jako ukryte.

6. Otwórz dowolne formularze niestandardowe i w grupie **Formularz** kliknij pozycję **Wyświetl kod** , aby zobaczyć, co działa po załadowaniu formularza.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Kroki potwierdzania ataku Reguły i formularze przy użyciu programu PowerShell

Najprostszym sposobem zweryfikowania ataku na reguły lub formularze niestandardowe jest uruchomienie [ skryptuGet-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) programu PowerShell. Ten skrypt łączy się z każdą skrzynką pocztową w dzierżawie i zrzuca wszystkie reguły i formularze do dwóch plików .csv.

#### <a name="pre-requisites"></a>Wymagania wstępne

Aby uruchomić skrypt, musisz mieć uprawnienia administratora globalnego, ponieważ skrypt nawiązuje połączenie z każdą skrzynką pocztową w dzierżawie w celu odczytania reguł i formularzy.

1. Zaloguj się do maszyny, z poziomu którą uruchomisz skrypt z uprawnieniami administratora lokalnego.

2. Pobierz lub skopiuj skrypt Get-AllTenantRulesAndForms.ps1 z GitHub do folderu, z którego go uruchomisz. Skrypt utworzy dwa pliki ostemplowane datą w tym folderze, MailboxFormsExport-yyyy-mm-dd.csv i MailboxRulesExport-yyyy-mm-dd.csv.

3. Otwórz wystąpienie programu PowerShell jako administrator i otwórz folder, w jakim zapisano skrypt.

4. Uruchom ten wiersz polecenia programu PowerShell w następujący sposób `.\Get-AllTenantRulesAndForms.ps1`: .\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Interpretowanie danych wyjściowych

- ***MailboxRulesExport-yyyy-mm-dd*.csv**: Sprawdź reguły (jeden na wiersz) pod kątem warunków akcji, które obejmują aplikacje lub pliki wykonywalne:

  - **ActionType (kolumna A)**: jeśli widzisz wartość "ID_ACTION_CUSTOM", reguła jest prawdopodobnie złośliwa.

  - **IsPotentiallyMalicious (kolumna D)**: Jeśli ta wartość to "TRUE", reguła jest prawdopodobnie złośliwa.

  - **ActionCommand (kolumna G)**: jeśli ta kolumna zawiera listę aplikacji lub dowolnego pliku z rozszerzeniami .exe lub .zip albo nieznany wpis, który odwołuje się do adresu URL, reguła jest prawdopodobnie złośliwa.

- ***MailboxFormsExport-yyyy-mm-dd*.csv**: Ogólnie rzecz biorąc, użycie formularzy niestandardowych jest rzadkie. Jeśli znajdziesz dowolny element w tym skoroszycie, otworzysz skrzynkę pocztową tego użytkownika i sprawdzisz sam formularz. Jeśli twoja organizacja nie umieściła jej w tym miejscu celowo, prawdopodobnie jest złośliwa.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Jak zatrzymać i skorygować atak na reguły Outlook i formularze

Jeśli znajdziesz jakiekolwiek dowody na jeden z tych ataków, korygowanie jest proste, wystarczy usunąć regułę lub formularz ze skrzynki pocztowej. Można to zrobić za pomocą klienta Outlook lub zdalnego programu PowerShell w celu usunięcia reguł.

### <a name="using-outlook"></a>Korzystanie z Outlook

1. Zidentyfikuj wszystkie urządzenia używane przez użytkownika z Outlook. Wszystkie będą musiały zostać oczyszczone z potencjalnego złośliwego oprogramowania. Nie zezwalaj użytkownikowi na logowanie się i używanie poczty e-mail, dopóki wszystkie urządzenia nie zostaną wyczyszczone.

2. Wykonaj kroki opisane w [temacie Usuwanie reguły](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f) dla każdego urządzenia.

3. Jeśli nie masz pewności co do obecności innego złośliwego oprogramowania, możesz sformatować i ponownie zainstalować całe oprogramowanie na urządzeniu. W przypadku urządzeń przenośnych możesz wykonać kroki producentów, aby zresetować urządzenie do obrazu fabrycznego.

4. Zainstaluj najbardziej aktualne wersje Outlook. Pamiętaj, że bieżąca wersja Outlook domyślnie blokuje oba typy tego ataku.

5. Po usunięciu wszystkich kopii skrzynki pocztowej w trybie offline zresetuj hasło użytkownika (użyj wysokiej jakości) i wykonaj kroki opisane w [temacie Konfigurowanie uwierzytelniania wieloskładnikowego dla użytkowników](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) , jeśli uwierzytelnianie wieloskładnikowe nie zostało jeszcze włączone. Dzięki temu poświadczenia użytkownika nie są udostępniane za pomocą innych środków (takich jak wyłudzanie informacji lub ponowne użycie hasła).

### <a name="using-powershell"></a>Korzystanie z programu PowerShell

Istnieją dwa zdalne polecenia cmdlet programu PowerShell, których można użyć do usuwania lub wyłączania niebezpiecznych reguł. Po prostu wykonaj kroki.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Kroki dotyczące skrzynek pocztowych znajdujących się na serwerze Exchange

1. Połączenie do serwera Exchange przy użyciu zdalnego programu PowerShell. Wykonaj kroki opisane w [Połączenie, aby Exchange serwerów przy użyciu zdalnego programu PowerShell](/powershell/exchange/connect-to-exchange-servers-using-remote-powershell).

2. Jeśli chcesz całkowicie usunąć pojedynczą regułę, wiele reguł lub wszystkie reguły ze skrzynki pocztowej, użyj polecenia cmdlet [Remove-InboxRule](/powershell/module/exchange/Remove-InboxRule) .

3. Jeśli chcesz zachować regułę i jej zawartość do dalszego badania, użyj polecenia cmdlet [Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Kroki dotyczące skrzynek pocztowych w Exchange Online

1. Wykonaj kroki opisane w [Połączenie, aby Exchange Online przy użyciu programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Jeśli chcesz całkowicie usunąć pojedynczą regułę, wiele reguł lub wszystkie reguły ze skrzynki pocztowej, użyj polecenia cmdlet [Remove-Inbox Rule](/powershell/module/exchange/Remove-InboxRule) .

3. Jeśli chcesz zachować regułę i jej zawartość do dalszego badania, użyj polecenia cmdlet [Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

## <a name="how-to-minimize-future-attacks"></a>Jak zminimalizować przyszłe ataki

### <a name="first-protect-your-accounts"></a>Po pierwsze: ochrona kont

Luki w zabezpieczeniach Reguły i Formularze są używane przez osobę atakującą tylko po kradzieży lub naruszeniu jednego z kont użytkownika. Dlatego pierwszym krokiem zapobiegania wykorzystywaniu tych luk w zabezpieczeniach w organizacji jest agresywna ochrona kont użytkowników. Niektóre z najbardziej typowych sposobów naruszenia kont to ataki polegające na wyłudzaniu informacji lub [atakach z użyciem hasła](https://www.microsoft.com/security/blog/2020/04/23/protecting-organization-password-spray-attacks/).

Najlepszym sposobem ochrony kont użytkowników, a zwłaszcza kont [administratorów, jest skonfigurowanie uwierzytelniania wieloskładnikowego dla użytkowników](../../admin/security-and-compliance/set-up-multi-factor-authentication.md). Należy również:

- Monitorowanie sposobu [uzyskiwania dostępu do kont użytkowników i ich użycia](/azure/active-directory/active-directory-view-access-usage-reports). Nie można zapobiec początkowemu naruszeniu, ale skrócisz czas trwania i wpływ naruszenia, wykrywając go wcześniej. Możesz użyć tych [zasad Office 365 Cloud App Security](/cloud-app-security/what-is-cloud-app-security), aby monitorować konta i otrzymywać alerty dotyczące nietypowych działań:

  - **Wiele nieudanych prób logowania**: te zasady profilują środowisko i wyzwalają alerty, gdy użytkownicy wykonują wiele nieudanych działań logowania w jednej sesji w odniesieniu do wyuczonych punktów odniesienia, co może wskazywać na próbę naruszenia.

  - **Niemożliwa podróż**: te zasady profilują środowisko i wyzwalają alerty, gdy działania są wykrywane przez tego samego użytkownika w różnych lokalizacjach w okresie krótszym niż oczekiwany czas podróży między dwiema lokalizacjami. Może to wskazywać, że inny użytkownik używa tych samych poświadczeń. Wykrycie tego nietypowego zachowania wymaga początkowego okresu nauki wynoszącego siedem dni, podczas którego uczy się wzorca aktywności nowego użytkownika.

  - **Nietypowe działanie personifikowane (przez użytkownika)**: te zasady profilują środowisko i wyzwalają alerty, gdy użytkownicy wykonują wiele personifikowanych działań w jednej sesji w odniesieniu do poznanego punktu odniesienia, co może wskazywać na próbę naruszenia.

- Użyj narzędzia, takiego jak [Office 365 Secure Score](https://securescore.office.com/), aby zarządzać konfiguracjami i zachowaniami zabezpieczeń konta.

### <a name="second-keep-your-outlook-clients-current"></a>Po drugie: zachowaj aktualną Outlook klientów

W pełni zaktualizowane i poprawione wersje Outlook 2013 r. i 2016 r. domyślnie wyłączają akcję "Uruchom aplikację" /formularz. Zapewni to, że nawet jeśli osoba atakująca naruszy konto, reguła i akcje formularza zostaną zablokowane. Najnowsze aktualizacje i poprawki zabezpieczeń można zainstalować, wykonując kroki opisane w [temacie Instalowanie aktualizacji Office](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5).

Oto wersje poprawek dla klientów Outlook 2013 i 2016:

- **Outlook 2016**: 16.0.4534.1001 lub nowsza.

- **Outlook 2013** r.: 15.0.4937.1000 lub nowsza.

Aby uzyskać więcej informacji na temat poszczególnych poprawek zabezpieczeń, zobacz:

- [poprawka zabezpieczeń Outlook 2016](https://support.microsoft.com/help/3191883)

- [poprawka zabezpieczeń Outlook 2013](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>Po trzecie: monitorowanie klientów Outlook

Należy pamiętać, że nawet po zainstalowaniu poprawek i aktualizacji osoba atakująca może zmienić konfigurację komputera lokalnego w celu ponownego włączenia zachowania "Uruchom aplikację". Usługa [Advanced zasady grupy Management](/microsoft-desktop-optimization-pack/agpm/) umożliwia monitorowanie i wymuszanie zasad komputera lokalnego na klientach.

Możesz sprawdzić, czy funkcja "Uruchom aplikację" została ponownie włączona za pośrednictwem przesłonięcia w rejestrze, korzystając z informacji w temacie [Jak wyświetlić rejestr systemowy przy użyciu 64-bitowych wersji Windows](https://support.microsoft.com/help/305097). Sprawdź następujące podklucze:

- **Outlook 2016**:`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013 r.**:`HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

Poszukaj klucza EnableUnsafeClientMailRules. Jeśli jest tam i ustawiono wartość 1, poprawka zabezpieczeń Outlook została zastąpiona, a komputer jest narażony na atak formularzy/reguł. Jeśli wartość to 0, akcja "Uruchom aplikację" jest wyłączona. Jeśli zainstalowano zaktualizowaną i poprawioną wersję Outlook, a ten klucz rejestru nie jest obecny, system nie jest narażony na te ataki.

Klienci z lokalnymi instalacjami Exchange powinni rozważyć zablokowanie starszych wersji Outlook, które nie mają dostępnych poprawek. Szczegółowe informacje na temat tego procesu można znaleźć w artykule [Konfigurowanie blokowania klienta Outlook](/exchange/configure-outlook-client-blocking-exchange-2013-help).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Zabezpieczanie Microsoft 365 jak profesjonalista ds. cyberbezpieczeństwa

Subskrypcja Microsoft 365 oferuje zaawansowany zestaw funkcji zabezpieczeń, których można użyć do ochrony danych i użytkowników. Użyj [planu zabezpieczeń Microsoft 365 — najważniejsze priorytety dla pierwszych 30 dni, 90 dni i nie tylko,](security-roadmap.md) aby zaimplementować zalecane przez firmę Microsoft najlepsze rozwiązania dotyczące zabezpieczania dzierżawy Microsoft 365.

- Zadania do wykonania w ciągu pierwszych 30 dni. Mają one natychmiastowy wpływ i mają niski wpływ na użytkowników.

- Zadania do wykonania w ciągu 90 dni. Planowanie i wdrażanie tych rozwiązań zajmuje nieco więcej czasu, ale znacznie poprawia stan zabezpieczeń.

- Ponad 90 dni. Te ulepszenia są kompilowane w ciągu pierwszych 90 dni pracy.

## <a name="see-also"></a>Zobacz też:

- [Złośliwe reguły Outlook](https://silentbreaksecurity.com/malicious-outlook-rules/) według funkcji SilentBreak Security Post dotyczące wektora reguł udostępniają szczegółowy przegląd sposobu Outlook reguł.

- [Mapi przez HTTP i Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) na blogu Sensepost o Mailrule Pwnage omawia narzędzie o nazwie Linijka, które pozwala wykorzystać skrzynki pocztowe za pośrednictwem reguł Outlook.

- [Outlook formularzy i powłok](https://sensepost.com/blog/2017/outlook-forms-and-shells/) na blogu Sensepost o forms Threat Vector.

- [Linijka Codebase](https://github.com/sensepost/ruler)

- [Wskaźniki linijki kompromisu](https://github.com/sensepost/notruler/blob/master/iocs.md)
