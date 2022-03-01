---
title: Badanie naruszonych kont za pomocą inspekcji zaawansowanej
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Za pomocą akcji inspekcji skrzynki pocztowej MailItemsAccessed można przeprowadzać dochodzenia sądowe dotyczące naruszonych kont użytkowników.
ms.openlocfilehash: 8bfba164bf3bfb0f4fa4bea687d0fe040cff4836
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019273"
---
# <a name="use-advanced-audit-to-investigate-compromised-accounts"></a>Badanie naruszonych kont za pomocą inspekcji zaawansowanej

Naruszone konto użytkownika (nazywane także przejęciem *konta) jest* rodzajem ataków, gdy atakujący uzyskuje dostęp do konta użytkownika i działa jak użytkownik. Tego typu ataki powodują czasami więcej szkód, niż może on zamierzyć. Podczas badania naruszonych kont e-mail należy założyć, że naruszono więcej danych poczty, niż można na to wskazać, śledząc rzeczywistą obecność atakującego. W zależności od typu danych w wiadomościach e-mail musisz założyć, że naruszono informacje poufne lub nałożysz na siebie przepisy prawne, chyba że możesz udowodnić, że informacje poufne nie zostały ujawnione. Na przykład organizacje, które są uregulowane ustawą HIPAA, podlegają istotnymi regulacjom, jeśli istnieją dowody na to, że dane na temat zdrowia pacjentów (PHI) są ujawnione. W takich przypadkach atakujący są mało zainteresowani phI, ale mimo to organizacje muszą zgłaszać naruszenia danych, o ile nie mogą udowodnić inaczej.

Aby pomóc w zbadaniu łamania kont e-mail, teraz inspekcja dostępu do danych poczty przez protokoły poczty i klientów przy użyciu akcji inspekcji skrzynki pocztowej *MailItemsAccessed* . Ta nowa akcja, która została objęte inspekcją, pomoże w lepszym zrozumieniu naruszeń danych poczty e-mail oraz zidentyfikowaniu zakresu naruszenia bezpieczeństwa określonych elementów poczty, które mogą zostać naruszone. Użycie tej nowej akcji inspekcji ma na celu zapewnianie ochrony przed naruszeniami danych, które nie zostały naruszone. Jeśli atakujący uzyskał dostęp do określonej poczty, może sprawdzić Exchange Online, mimo że nie ma wskazania, że element został odczytany.

## <a name="the-mailitemsaccessed-mailbox-auditing-action"></a>Akcja inspekcji skrzynki pocztowej MailItemsAccessed

Nowa akcja MailItemsAccessed jest częścią [nowej funkcji](advanced-audit.md) zaawansowanej inspekcji. Jest ona częścią inspekcji skrzynki pocztowej programu [Exchange](/office365/securitycompliance/enable-mailbox-auditing#mailbox-auditing-actions) i jest domyślnie włączona dla użytkowników, do których przypisano licencję usługi Office 365 lub Microsoft 365 E5, albo dla organizacji z subskrypcją dodatkową Zgodność platformy Microsoft 365 E5.

Akcja inspekcji skrzynki pocztowej MailItemsAccessed obejmuje wszystkie protokoły poczty: POP, IMAP, MAPI, EWS, Exchange ActiveSync i REST. O obejmuje ono również oba typy uzyskiwania dostępu do poczty: *synchronizowanie i* *powiązanie*.

### <a name="auditing-sync-access"></a>Inspekcja dostępu do synchronizacji

Operacje synchronizacji są rejestrowane tylko wtedy, gdy skrzynka pocztowa jest dostępna w klasycznej wersji klienta poczty Outlook komputerów Windows lub Mac. Podczas synchronizacji ci klienci zazwyczaj pobierają duży zestaw elementów poczty z chmury na komputer lokalny. Wielkość inspekcji dla operacji synchronizacji jest ogromna. Dlatego zamiast generować rekord inspekcji dla każdego synchronizowanego elementu poczty, generuj zdarzenie inspekcji dla folderu poczty zawierającego elementy, które zostały zsynchronizowane, i założono, że wszystkie elementy poczty w folderze synchronizowanego zostały naruszone. Typ dostępu jest rejestrowany w polu OperationProperties rekordu inspekcji.

Zobacz krok 2 w sekcji Używanie rekordów inspekcji [MailItemsAccessed](#use-mailitemsaccessed-audit-records-for-forensic-investigations) na użytek dochodzenia sądowego, aby uzyskać przykład wyświetlania typu dostępu do synchronizacji w rekordzie inspekcji.

### <a name="auditing-bind-access"></a>Inspekcja powiązywania dostępu

Operacja powiązania to pojedynczy dostęp do wiadomości e-mail. W celu powiązania dostępu do rekordu inspekcji zostanie zarejestrowany adres InternetMessageId poszczególnych wiadomości. Rekordy akcji inspekcji MailItemsAccessed powiążą operacje, a następnie połączą się w jeden rekord inspekcji. Wszystkie operacje powiązania wykonywane w interwale 2-minutowym są agregowane w jednym rekordzie inspekcji w polu Foldery we właściwości Dane inspekcji. Każda wiadomość, do której uzyskano dostęp, jest identyfikowana przez jej adres InternetMessageId. Liczba operacji powiązania, które zostały zagregowane w rekordzie, jest wyświetlana w polu OperationCount we właściwości Dane inspekcji.

Zobacz krok 4 w sekcji Używanie rekordów inspekcji [MailItemsAccessed](#use-mailitemsaccessed-audit-records-for-forensic-investigations) na użytek dochodzenia sądowego, aby uzyskać przykład wyświetlania typu dostępu powiążowego w rekordzie inspekcji.

### <a name="throttling-of-mailitemsaccessed-audit-records"></a>Ograniczanie rekordów inspekcji MailItemsAccessed

Jeśli w ciągu mniej niż 24 godzin zostanie wygenerowanych więcej niż 1000 rekordów inspekcji MailItemsAccessed, program Exchange Online przestanie generować rekordy inspekcji dla działania MailItemsAccessed. Gdy skrzynka pocztowa zostanie ograniczona, aktywność funkcji MailItemsAccessed nie będzie rejestrowana przez 24 godziny po jej ograniczaniu. Jeśli skrzynka pocztowa została ograniczona, istnieje możliwość, że w tym okresie skrzynka pocztowa mogła zostać naruszona. Rejestrowanie działania MailItemsAccessed zostanie wznowione po 24-godzinnym okresie.

Oto kilka rzeczy, o których należy pamiętać w przypadku ograniczania:

- Mniej niż 1% wszystkich skrzynek pocztowych w Exchange Online są ograniczone
- Gdy skrzynka pocztowa ogranicza, nie są insektowane tylko rekordy inspekcji dotyczące działań MailItemsAccessed. Nie ma to wpływu na inne akcje inspekcji skrzynki pocztowej.
- Skrzynki pocztowe są ograniczane tylko w przypadku operacji Powiązywa. Rekordy inspekcji dotyczące operacji synchronizacji nie są ograniczane.
- Jeśli skrzynka pocztowa jest ograniczona, prawdopodobnie możesz założyć, że było działanie MailItemsAccessed, które nie zostało zarejestrowane w dziennikach inspekcji.

Zobacz krok 1 w sekcji Używanie rekordów inspekcji [MailItemsAccessed](#use-mailitemsaccessed-audit-records-for-forensic-investigations) na użytek dochodzenia sądowego, aby uzyskać przykład wyświetlania właściwości IsThrottled w rekordzie inspekcji.

## <a name="use-mailitemsaccessed-audit-records-for-forensic-investigations"></a>Używanie rekordów inspekcji programu MailItemsAccessed na użytek dochodzenia sądowego

Inspekcja skrzynek pocztowych generuje rekordy inspekcji dotyczące dostępu do wiadomości e-mail, dzięki czemu masz pewność, że wiadomości e-mail nie zostały naruszone. Z tego powodu w przypadkach, w których nie jesteśmy pewni, że dostęp do niektórych danych został uzyskany, przyjmuje się, że został on uzyskany przez nagranie całej aktywności w zakresie dostępu do poczty.

Korzystanie z rekordów inspekcji mailItemsAccessed na potrzeby celów forensic jest zazwyczaj wykonywane po rozpoznaniu naruszenia danych i wyeksjonowaniu atakującego. Aby rozpocząć badanie, należy określić zestaw skrzynek pocztowych, które zostały naruszone, oraz określić ramy czasowe, w których atakujący mieli dostęp do skrzynek pocztowych w Twojej organizacji. Następnie możesz użyć poleceń **cmdlet Search-UnifiedAuditLog** lub **Search-MailboxAuditLog** w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) do wyszukiwania rekordów inspekcji, które odpowiadają naruszeniu danych.

Aby wyszukać rekordy inspekcji MailItemsAccessed, możesz uruchomić jedno z następujących poleceń:

**Ujednolicony dziennik inspekcji**:

```powershell
Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000
```

**Dziennik inspekcji skrzynki pocztowej**:

```powershell
Search-MailboxAuditLog -Identity <user> -StartDate 01/06/2020 -EndDate 01/20/2020 -Operations MailItemsAccessed -ResultSize 1000 -ShowDetails
```

> [!TIP]
> Podstawowa różnica między tymi dwoma poleceniami cmdlet polega na tym, że za pomocą polecenia cmdlet **Search-UnifiedAuditLog** można wyszukiwać rekordy inspekcji pod względem działań wykonywanych przez co najmniej jednego użytkownika. Wynika to z tego, *że identyfikatory użytkownika* są parametrem wielokolorowym. Polecenie **cmdlet Search-MailboxAuditLog** przeszukuje dziennik inspekcji skrzynki pocztowej dla jednego użytkownika.

Poniżej odpowiedzialności za pomocą rekordów inspekcji MailItemsAccessed można zbadać naruszony atak użytkownika. W każdym kroku przedstawiono składnię poleceń **dla poleceń cmdlet Search-UnifiedAuditLog** lub **Search-MailboxAuditLog** .

1. Sprawdź, czy skrzynka pocztowa została ograniczona. Jeśli tak, oznacza to, że niektóre rekordy inspekcji skrzynki pocztowej nie zostałyby zarejestrowane. W przypadku, gdy wszystkie rekordy inspekcji mają wartość "IsThrottled" (Prawda), należy przyjąć, że przez 24 godziny później ten rekord został wygenerowany, że nie został zweryfikowany żaden dostęp do skrzynki pocztowej i że naruszono wszystkie dane poczty.

   Aby wyszukać rekordy MailItemsAccessed, których skrzynka pocztowa została ograniczona, uruchom następujące polecenie:

   **Ujednolicony dziennik inspekcji**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"IsThrottled","Value":"True"*'} | FL
   ```

   **Dziennik inspekcji skrzynki pocztowej**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*IsThrottled:True*"} | FL
   ```

2. Sprawdzanie działań synchronizacji. Jeśli atakujący pobiera wiadomości ze skrzynki pocztowej za pomocą klienta poczty e-mail, może odłączyć komputer od Internetu i uzyskać dostęp do wiadomości lokalnie bez konieczności interakcji z serwerem. W takim przypadku inspekcja skrzynek pocztowych nie będzie mogła inspekcji tych działań.

   Aby wyszukać rekordy MailItemsAccessed, w których elementy poczty były dostępne podczas synchronizacji, uruchom następujące polecenie:

   **Ujednolicony dziennik inspekcji**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 02/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Sync"*'} | FL
   ```

   **Dziennik inspekcji skrzynki pocztowej**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Sync*"} | FL
   ```

3. Sprawdź działania synchronizacji, aby ustalić, czy miały one miejsce w tym samym kontekście co działania używane przez atakującego podczas uzyskiwania dostępu do skrzynki pocztowej. Kontekst jest identyfikowany i odróżniany od adresu IP komputera klienckiego używanego do uzyskiwania dostępu do skrzynki pocztowej i protokołu poczty. Aby uzyskać więcej informacji, zobacz sekcję Identyfikowanie kontekstu [dostępu dla różnych rekordów inspekcji](#identifying-the-access-contexts-of-different-audit-records) .

   Do zbadania użyj wymienionych poniżej właściwości. Te właściwości znajdują się we właściwości AuditData lub OperationProperties. Jeśli którakolwiek synchronizacja ma miejsce w tym samym kontekście co działanie atakującego, załóżmy, że atakujący zsynchronizował wszystkie elementy poczty ze swoim klientem, co oznacza, że prawdopodobnie naruszono całą skrzynkę pocztową.

   <br>

   ****

   |Właściwość|Opis|
   |---|---|
   |ClientInfoString|W tym artykule opisano protokół, klient (zawiera wersję)|
   |ClientIPAddress (ClientIPAddress)|Adres IP komputera klienckiego.|
   |SessionId|Identyfikator sesji ułatwia odróżnienie działań atakujących od codziennie czynów użytkowników na tym samym koncie (przydatne w przypadku naruszonych kont)|
   |UserId|UpN użytkownika czyta wiadomości.|
   |

4. Sprawdź, czy nie ma działań powiązania. Po wykonaniu kroków 2 i 3 masz pewność, że każdy inny dostęp do wiadomości e-mail przez atakującego będzie przechwytywany w rekordach inspekcji MailItemsAccessed, które mają właściwość MailAccessType o wartości "Bind".

   Aby wyszukać rekordy MailItemsAccessed, w których elementy poczty uzyskały dostęp podczas operacji Powiąż, uruchom następujące polecenie.

   **Ujednolicony dziennik inspekcji**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Bind"*'} | FL
   ```

   **Dziennik inspekcji skrzynki pocztowej**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Bind*"} | FL
   ```

   Wiadomości e-mail, do których uzyskano dostęp, są identyfikowane za pomocą ich identyfikatorów wiadomości internetowych. Możesz również sprawdzić, czy jakiekolwiek rekordy inspekcji mają taki sam kontekst jak rekordy innych działań atakujących. Aby uzyskać więcej informacji, zobacz sekcję Identyfikowanie kontekstu [dostępu dla różnych rekordów inspekcji](#identifying-the-access-contexts-of-different-audit-records) .

   Dane inspekcji można stosować do operacji powiązywania na dwa różne sposoby:

   - Dostęp do wszystkich wiadomości e-mail, do których uzyskał dostęp użytkownik, można uzyskać dostęp przy użyciu adresu InternetMessageId, a następnie sprawdzając, czy któreś z tych wiadomości zawiera informacje poufne.
   - Funkcja InternetMessageId pozwala przeszukiwać rekordy inspekcji dotyczące zestawu potencjalnie poufnych wiadomości e-mail. Jest to przydatne, jeśli martwi Cię tylko kilka wiadomości.

## <a name="filtering-of-duplicate-audit-records"></a>Filtrowanie zduplikowanych rekordów inspekcji

Zduplikowane rekordy inspekcji dotyczące tych samych operacji powiązywań, które mają miejsce w ciągu godziny odfiltrowywowane w celu usunięcia szumu inspekcji. Operacje synchronizacji są również filtrowane w odstępach jednogodzinnych. Wyjątek od tego procesu de duplikowania występuje, jeśli dla tego samego obiektu InternetMessageId dowolne właściwości opisane w poniższej tabeli są inne. Jeśli jedna z tych właściwości jest inna w przypadku zduplikowanej operacji, jest generowany nowy rekord inspekcji. Ten proces został opisany bardziej szczegółowo w następnej sekcji.

<br>

****

|Właściwość|Opis|
|---|---|
|ClientIPAddress (ClientIPAddress)|Adres IP klienta.|
|ClientInfoString|Protokół klienta używany do uzyskiwania dostępu do skrzynki pocztowej.|
|ParentFolder|Pełna ścieżka folderu elementu poczty, do którego uzyskano dostęp.|
|Logon_type|Typ logowania użytkownika, który wykonał akcję. Typy logowania (i odpowiadająca im wartość wum), to Właściciel (0), Administrator (1) lub Pełnomocnik (2).|
|MailAccessType|Czy dostęp jest operacją powiązy, czy operacją synchronizacji.|
|MailboxUPN (Pn) skrzynki pocztowej|UpN skrzynki pocztowej, w której jest odczytywana wiadomość.|
|Użytkownik|UpN użytkownika czyta wiadomość.|
|SessionId|Identyfikator sesji ułatwia odróżnienie działań atakujących i codziennie czynów użytkowników w tej samej skrzynce pocztowej (w przypadku naruszenia bezpieczeństwa konta) Aby uzyskać więcej informacji na temat sesji, zobacz Kontekstowe działania atakujące na sesjach w programie [Exchange Online](https://techcommunity.microsoft.com/t5/exchange-team-blog/contextualizing-attacker-activity-within-sessions-in-exchange/ba-p/608801).|
|

## <a name="identifying-the-access-contexts-of-different-audit-records"></a>Identyfikowanie kontekstu dostępu do różnych rekordów inspekcji

Często atakujący może uzyskać dostęp do skrzynki pocztowej w tym samym czasie, gdy właściciel skrzynki pocztowej uzyskuje do takiej skrzynki pocztowej dostęp. Aby odróżnić dostęp atakującego i właściciela skrzynki pocztowej, istnieją właściwości rekordu inspekcji definiujące kontekst dostępu. Jak wyjaśniono wcześniej, gdy wartości tych właściwości są różne, nawet jeśli działanie występuje w interwale agregacji, są generowane oddzielne rekordy inspekcji. W poniższym przykładzie istnieją trzy różne rekordy inspekcji. Każdy z nich jest wyróżniony właściwościami Identyfikator sesji i ClientIPAddress. Wiadomości, do których uzyskano dostęp, również są identyfikowane.

<br>

****

|Rekord inspekcji 1|Rekord inspekcji 2|Rekord inspekcji 3|
|---|---|---|
|ClientIPAddress1 (ClientIPAddress1)<br/>**SessionId2**|ClientIPAddress2<br/>**SessionId2**|ClientIPAddress1 (ClientIPAddress1)<br/>**SessionId3**|
|**InternetMessageIdA**<br/>**InternetMessageIdd**<br/>**InternetMessageIde**<br/>**InternetMessageIdF**<br/>|**InternetMessageIdA**<br/>**InternetMessageIdC**|**InternetMessageIdB**|
|

Jeśli którakolwiek z właściwości wymienionych w tabeli w poprzedniej [](#filtering-of-duplicate-audit-records) sekcji jest inna, jest generowany osobny rekord inspekcji w celu śledzenia nowego kontekstu. Dostępy będą sortowane do osobnych rekordów inspekcji w zależności od kontekstu, w którym miało miejsce działanie.

Na przykład w rekordach inspekcji pokazanych na poniższym zrzucie ekranu, chociaż jednocześnie uzyskujemy dostęp do poczty od EWSEditor i OWA, działanie dostępu jest sortowane w różnych rekordach inspekcji w zależności od kontekstu, w którym miała miejsce dostęp. W tym przypadku kontekst jest zdefiniowany przez inne wartości właściwości ClientInfoString.

![Różne rekordy inspekcji w zależności od kontekstu.](../media/MailItemsAccessed4.png)

Poniżej przedstawiono składnię polecenia pokazanego na poprzednim zrzucie ekranu:

```powershell
Search-MailboxAuditLog -Identity admin -ShowDetails -Operations MailItemsAccessed -ResultSize 2000 | Select LastAccessed,Operation,AuditOperationsCountInAggregatedRecord,ClientInfoString
```
