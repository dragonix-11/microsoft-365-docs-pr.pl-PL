---
title: Scenariusz rozlanie danych w serii rozwiązań zbierania elektronicznych materiałów dowodowych — wyszukiwanie i przeczyszczanie
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MET150
ms.assetid: d945f7dd-f62f-4ca7-b3e7-469824cfd493
description: Za pomocą funkcji zbierania elektronicznych materiałów dowodowych i narzędzi wyszukiwania możesz zarządzać incydentem rozlanie danych w organizacji i reagować na nie.
ms.openlocfilehash: 98dbb4ec36b7fb8166732aa855eefe3db6c5bbdc
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449558"
---
# <a name="ediscovery-solution-series-data-spillage-scenario---search-and-purge"></a>Seria rozwiązań zbierania elektronicznych materiałów dowodowych: Scenariusz rozlanie danych — wyszukiwanie i przeczyszczanie

 **Co to jest rozlanie danych i dlaczego warto się tym zająć?** Rozlanie danych jest wtedy, gdy dokument poufny jest wydany w niezaufanym środowisku. W przypadku wykrycia zdarzenia związanego z rozlaniem danych należy szybko ocenić rozmiar i lokalizacje rozlanie, zbadać działania użytkowników wokół niego, a następnie trwale usunąć rozlane dane z systemu. 
  
## <a name="data-spillage-scenario"></a>Scenariusz rozlanie danych

Jesteś potencjalnym dyrektorem ds. zabezpieczeń informacji w firmie Contoso. Masz informację o sytuacji, w której pracownik nieuznajomie udostępnił wysoce poufny dokument wielu osobom za pośrednictwem poczty e-mail. Chcesz szybko ocenić, kto otrzymał ten dokument wewnętrznie i zewnętrznie. Po zidentyfikowaniu należy udostępnić ustalenia dotyczące sprawy innym chętniom do przejrzenia, a następnie trwale usunąć dane z Office 365. Po zakończeniu badania chcesz wygenerować raport z dowodami trwałego usunięcia i innymi szczegółami sprawy do użycia w przyszłości.
  
### <a name="scope-of-this-article"></a>Zakres tego artykułu

Ten dokument zawiera listę instrukcji dotyczących trwałego usuwania wiadomości z programu Microsoft 365, aby nie była dostępna ani nie można jej odzyskać. Aby usunąć wiadomość i przywrócić ją do czasu wygaśnięcia okresu przechowywania elementów usuniętych, zobacz Wyszukiwanie i usuwanie wiadomości [e-mail w organizacji](search-for-and-delete-messages-in-your-organization.md).
  
## <a name="workflow-for-managing-data-spillage-incidents"></a>Przepływ pracy do zarządzania zdarzeniami z rozlaniem danych

Poniżej opisano, jak można zarządzać zdarzeniem rozlanie danych:

![8-stopniowy przepływ pracy do zarządzania zdarzeniami typu rozlanie danych.](../media/O365-eDiscoverySolutions-DataSpillage-workflow.png)
  
[(Opcjonalnie) Krok 1. Zarządzanie dostępem osób do sprawy i ustawianie granic zgodności](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries)<br/>
[Krok 2. Tworzenie sprawy zbierania elektronicznych materiałów dowodowych](#step-2-create-an-ediscovery-case)<br/>
[Krok 3. Wyszukiwanie rozlanych danych](#step-3-search-for-the-spilled-data)<br/>
[Krok 4. Przeglądanie i weryfikowanie wniosków o sprawy](#step-4-review-and-validate-case-findings)<br/>
[Krok 5. Sprawdzanie sposobu współużytknia danych rozlanej przy użyciu dziennika śledzenia wiadomości](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared)<br/>
[Krok 6. Przygotowywanie skrzynek pocztowych](#step-6-prepare-the-mailboxes)<br/>
[Krok 7. Trwałe usuwanie rozlanej danych](#step-7-permanently-delete-the-spilled-data)<br/>
[Krok 8. Weryfikowanie, dostarczenie dowodu usunięcia i inspekcja](#step-8-verify-provide-a-proof-of-deletion-and-audit)<br/>

## <a name="things-to-know-before-you-start"></a>Co należy wiedzieć przed rozpoczęciem

- Gdy skrzynka pocztowa jest wstrzymywana, usunięta wiadomość pozostaje w folderze Elementy do odzyskania do momentu wygaśnięcia okresu przechowywania lub usunięcia zawieszonego konta. [Krok 6](#step-6-prepare-the-mailboxes) opisuje sposób usuwania wstrzymywania ze skrzynek pocztowych. Skontaktuj się z kierownictwem ds. rekordów lub działami prawnymi przed usunięciem zawieszonego rekordu. Twoja organizacja może mieć zasady definiujące, czy skrzynka pocztowa w miejscu przechowywania lub zdarzenie rozlanie danych ma pierwszeństwo. 
    
- Aby kontrolować, które skrzynki pocztowe użytkowników, dla których może być przeszukiwane źródło danych i zarządzać tym, kto może mieć dostęp do sprawy, możesz skonfigurować granice zgodności i utworzyć niestandardową grupę ról, która jest opisana w kroku [1](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries). Aby to zrobić, musisz być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę zarządzania rolami. Jeśli Ty lub administrator w organizacji ustawiliśmy już granice zgodności, możesz pominąć krok 1.
    
- Aby utworzyć sprawę, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych lub członkiem niestandardowej grupy ról z przypisaną rolą Zarządzanie sprawymi. Jeśli nie jesteś członkiem grupy, poproś administratora usługi Microsoft 365 o dodanie Cię do grupy ról Menedżera [zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).
    
- Aby utworzyć i uruchomić wyszukiwanie zawartości, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych lub mieć przypisaną rolę zarządzania wyszukiwaniem zgodności. Aby usuwać wiadomości, musisz być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę zarządzania Wyszukiwaniem i przeczyszczanie. Aby uzyskać informacje na temat dodawania użytkowników do grupy ról, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](./assign-ediscovery-permissions.md).
    
- Aby przeszukiwać działania zbierania elektronicznych materiałów dowodowych dziennika inspekcji w kroku 8, inspekcja musi być włączona w organizacji. Możesz wyszukiwać działania wykonane w ciągu ostatnich 90 dni. Aby dowiedzieć się więcej na temat włączania i używania inspekcji, [zobacz sekcję](#auditing-the-data-spillage-investigation-process) Inspekcja procesu badania rozlanie danych w kroku 8. 
    
## <a name="optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries"></a>(Opcjonalnie) Krok 1. Zarządzanie dostępem osób do sprawy i ustawianie granic zgodności

W zależności od praktyk organizacyjnych, musisz kontrolować, kto może uzyskać dostęp do sprawy zbierania elektronicznych materiałów dowodowych w celu zbadania zdarzenia rozlanie danych i skonfigurowania granic zgodności. Najłatwiej to zrobić przez dodanie chętnych jako członków istniejącej grupy ról w Centrum zgodności platformy Microsoft 365 a następnie dodanie grupy ról jako członka sprawy zbierania elektronicznych materiałów dowodowych. Aby uzyskać informacje na temat wbudowanych grup ról zbierania elektronicznych materiałów dowodowych i sposobu dodawania członków do sprawy zbierania elektronicznych materiałów dowodowych, zobacz Przypisywanie uprawnień zbierania elektronicznych materiałów [dowodowych](assign-ediscovery-permissions.md).
  
Można również utworzyć nową grupę ról dopasowaną do potrzeb organizacji. Na przykład możesz zechcieć, aby grupa części danych w organizacji mogła mieć dostęp do wszystkich spraw rozlanie danych i współpracować nad nimi. W tym celu należy utworzyć grupę ról "Pochylanie danych Pochylanie danych", przypisać odpowiednie role (Eksportowanie, Odszyfrowywanie, Przegląd, Podgląd, Wyszukiwanie zgodności i Zarządzanie case), dodanie grupy ról do grupy ról, a następnie dodanie grupy ról jako członka sprawy zbierania elektronicznych materiałów dowodowych danych. Zobacz [Konfigurowanie granic zgodności dla badań zbierania](set-up-compliance-boundaries.md) elektronicznych materiałów dowodowych w programie Office 365, aby uzyskać szczegółowe instrukcje dotyczące tego, jak to zrobić. 
  
## <a name="step-2-create-an-ediscovery-case"></a>Krok 2. Tworzenie sprawy zbierania elektronicznych materiałów dowodowych

Sprawa zbierania elektronicznych materiałów dowodowych zapewnia skuteczny sposób zarządzania badaniem rozlanie danych. Możesz dodawać członków do grupy ról utworzonej w kroku 1, dodawać grupę ról jako członka nowej sprawy zbierania elektronicznych materiałów dowodowych, przeprowadzać iteracyjne wyszukiwania w celu znalezienia rozlanej danych, eksportować raport do udostępnienia, śledzić stan sprawy, a następnie w razie potrzeby odwoływać się do szczegółów sprawy. Rozważ ustanowienie konwencji nazewnictwa dla spraw zbierania elektronicznych materiałów dowodowych używanej w przypadku zdarzeń rozlanie danych i podaj tyle informacji, ile można w nazwie i opisie sprawy, aby w razie potrzeby odnaleźć i odwołać się do sprawy w przyszłości.
  
Aby utworzyć nową sprawę, możesz korzystać z zbierania elektronicznych materiałów dowodowych w Centrum zabezpieczeń i zgodności. Zobacz "Tworzenie nowej sprawy" [w rozpoczynanie pracy z core eDiscovery](get-started-core-ediscovery.md#step-3-create-a-core-ediscovery-case).
  
## <a name="step-3-search-for-the-spilled-data"></a>Krok 3. Wyszukiwanie rozlanych danych

Po utworzeniu sprawy i dostępie zarządzanym możesz jej użyć w celu iteracyjnych wyszukiwań w celu znalezienia rozlanej danych i zidentyfikowania skrzynek pocztowych, które zawierają rozlane dane. Użyjemy tego samego zapytania wyszukiwania, które zostało użyte do znalezienia wiadomości e-mail w celu usunięcia tych samych wiadomości w [kroku 7](#step-7-permanently-delete-the-spilled-data).
  
Aby utworzyć przeszukiwanie zawartości skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych, zobacz Wyszukiwanie zawartości w podstawowej sprawie [zbierania elektronicznych materiałów dowodowych](search-for-content-in-core-ediscovery.md).
  
> [!IMPORTANT]
> Słowa kluczowe, których używasz w zapytaniu wyszukiwania, mogą zawierać rzeczywiste rozlane dane, które szukasz. Jeśli na przykład wyszukujesz dokumenty zawierające numer PESZ i użyjemy go jako słowa kluczowego wyszukiwania, musisz później usunąć zapytanie, aby uniknąć dalszej rozlanie. Zobacz [Usuwanie zapytania wyszukiwania w](#deleting-the-search-query) kroku 8.
  
## <a name="step-4-review-and-validate-case-findings"></a>Krok 4. Przeglądanie i weryfikowanie wniosków o sprawy

Po utworzeniu wyszukiwania zawartości należy przejrzeć i sprawdzić, czy wyniki wyszukiwania zawierają tylko te wiadomości e-mail, które należy usunąć. W przeszukiwaniu zawartości możesz wyświetlić podgląd losowej próbki 1000 wiadomości e-mail bez eksportowania wyników wyszukiwania, aby uniknąć rozlewu danych. Aby dowiedzieć się więcej o ograniczeniach wersji Preview, zobacz [Limity wyszukiwania zawartości](limits-for-content-search.md).
  
Jeśli masz więcej niż 1000 skrzynek pocztowych lub więcej niż 100 wiadomości e-mail do przejrzenia, możesz podzielić wyszukiwanie początkowe na wiele wyszukiwań przy użyciu dodatkowych słów kluczowych lub warunków, takich jak zakres dat lub nadawca/adresat, i osobno przeglądać wyniki każdego wyszukiwania. Zanotuj wszystkie zapytania wyszukiwania, których będziesz używać podczas usuwania wiadomości w [kroku 7](#step-7-permanently-delete-the-spilled-data).

Gdy znajdziesz wiadomość e-mail zawierającą rozlane dane, sprawdź, czy adresaci wiadomości ustalili, czy została udostępniona zewnętrznie. Aby jeszcze bardziej prześledzić wiadomość, możesz zebrać informacje o nadawcy i zakresy dat w celu używania dzienników śledzenia wiadomości. Ten proces jest opisany w [kroku 5](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared).

Po zweryfikowaniu wyników wyszukiwania możesz udostępnić uzyskane wyniki innym osobom w celu ich drugiego przejrzenia. Osoby, które zostały przypisane do sprawy w kroku 1, mogą przeglądać zawartość sprawy zarówno w zbierania elektronicznych materiałów dowodowych, jak i w Advanced eDiscovery i zatwierdzać ustalenia sprawy. Można również wygenerować raport bez eksportowania rzeczywistej zawartości. Możesz również użyć tego samego raportu, który jest dowodem usunięcia, co opisano w [kroku 8](#step-8-verify-provide-a-proof-of-deletion-and-audit).
  
 **Aby wygenerować raport statystyczny:**
  
1. Przejdź do **strony wyszukiwania** w przypadku zbierania elektronicznych materiałów dowodowych i kliknij wyszukiwanie, dla którego chcesz wygenerować raport. 
    
2. Na stronie wysuwu kliknij pozycję **Więcej > eksportu raportu**.
 
      Zostanie wyświetlona strona Eksportuj raport.

    ![Zaznacz wyszukiwanie, a następnie kliknij pozycję Więcej > eksportu raportu na wysuwana strona.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport1.png)
    
3. Zaznacz **pozycję Wszystkie elementy,** łącznie z elementami, które mają nierozpoznany format, są szyfrowane lub nie zostały zindeksowane z innych powodów, a następnie kliknij pozycję **Generuj raport**.

4. W przypadku zbierania elektronicznych materiałów dowodowych kliknij pozycję **Eksportuj** , aby wyświetlić listę zadań eksportu. Może być trzeba kliknąć pozycję **Odśwież** , aby zaktualizować listę w celu wyświetlenia utworzonego zadania eksportu.

5. Kliknij zadanie eksportu, a następnie kliknij pozycję **Pobierz** raport na wysuwanych stronie.
 
    ![Na stronie Eksportowanie kliknij eksportuj, a następnie kliknij pozycję "Pobierz raport".](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport2.png)

Raport **Podsumowanie eksportu** zawiera liczbę znalezionych lokalizacji z wynikami i rozmiar wyników wyszukiwania. Można go użyć do porównania z raportem wygenerowanym po usunięciu i stanowić dowód usunięcia. Raport **Wyniki** zawiera bardziej szczegółowe podsumowanie wyników wyszukiwania, łącznie z tematem, nadawcą, adresatami, jeśli wiadomość e-mail została odczytana, datami i rozmiarem każdej wiadomości. Jeśli którykolwiek ze szczegółów w tym raporcie zawiera rzeczywiste dane rozlane, pamiętaj o trwałym usunięciu pliku Results.csv po zakończeniu badania.

Aby uzyskać więcej informacji na temat eksportowania raportów, [zobacz Eksportowanie raportu przeszukiwania zawartości](export-a-content-search-report.md).
    
## <a name="step-5-use-message-trace-log-to-check-how-spilled-data-was-shared"></a>Krok 5. Sprawdzanie sposobu współużytknia danych rozlanej przy użyciu dziennika śledzenia wiadomości

Aby dokładniej zbadać, czy udostępniono pocztę e-mail z danymi rozlanej, możesz opcjonalnie wysłać zapytanie do dzienników śledzenia wiadomości z informacjami o nadawcy i zakresie dat zebranych w kroku 4. Okres przechowywania dla śledzenia wiadomości to 30 dni dla danych w czasie rzeczywistym i 90 dni dla danych historycznych.
  
W centrum zabezpieczeń i zgodności możesz użyć funkcji śledzenia wiadomości lub odpowiednich poleceń cmdlet w programie Exchange Online PowerShell. Należy pamiętać, że śledzenie wiadomości nie daje pełnych gwarancji dotyczących kompletności zwracanych danych. Aby uzyskać więcej informacji na temat korzystania z śledzenia wiadomości, zobacz: 
  
- [Śledzenie wiadomości w Centrum & zgodności](../security/office-365-security/message-trace-scc.md)
    
- [Śledzenie nowych wiadomości w Centrum & zgodności](https://techcommunity.microsoft.com/t5/exchange-team-blog/new-message-trace-in-office-365-security-038-compliance-center/ba-p/607893)
    
## <a name="step-6-prepare-the-mailboxes"></a>Krok 6. Przygotowywanie skrzynek pocztowych

Po przejrzeniu i zweryfikowaniu, że wyniki wyszukiwania zawierają tylko wiadomości, które muszą zostać usunięte, musisz zebrać listę adresów e-mail skrzynek pocztowych, których dotyczy problem, do użycia w kroku 7 podczas usuwania rozlanego danych. Może być również trzeba przygotować skrzynki pocztowe przed trwałym usunięciem wiadomości e-mail w zależności od tego, czy w skrzynkach pocztowych zawierających rozlane dane włączono odzyskiwanie pojedynczych elementów, czy którekolwiek z tych skrzynek pocztowych jest zawieszone.
  
### <a name="get-a-list-of-addresses-of-mailboxes-with-spilled-data"></a>Uzyskiwanie listy adresów skrzynek pocztowych z danymi rozlanej

Istnieją dwa sposoby gromadzenia listy adresów e-mail skrzynek pocztowych z rozlanej danych.

**Opcja 1. Uzyskiwanie listy adresów skrzynek pocztowych z rozlanej danych**

1. Otwórz sprawę zbierania elektronicznych materiałów dowodowych, przejdź do **strony wyszukiwania** i wybierz odpowiednie wyszukiwanie zawartości. 
    
2. Na wysuwana strona kliknij pozycję **Wyświetl wyniki**.
    
3. Na liście **rozwijanej Poszczególne** wyniki kliknij pozycję **Statystyki wyszukiwania**.
    
4. Na **liście rozwijanej** Typ kliknij pozycję **Najlepsze lokalizacje**.
    
    ![Lista skrzynek pocztowych, które zawierają wyniki wyszukiwania, znajduje się na stronie Najlepsze lokalizacje w statystyce wyszukiwania.](../media/O365-eDiscoverySolutions-DataSpillage-TopLocations.png)

    Zostanie wyświetlona lista skrzynek pocztowych zawierających wyniki wyszukiwania. Zostanie również wyświetlona liczba elementów w każdej skrzynce pocztowej, które pasują do zapytania wyszukiwania.
    
5. Skopiuj informacje z listy i zapisz je w pliku lub **kliknij pozycję Pobierz** , aby pobrać te informacje do pliku CSV. 
    
**Opcja 2. Uzyskiwanie lokalizacji skrzynki pocztowej z raportu eksportu**

Otwórz raport Podsumowania eksportu pobrany w [kroku 4](#step-4-review-and-validate-case-findings). W pierwszej kolumnie raportu w obszarze Lokalizacje jest podany adres e-mail każdej **skrzynki pocztowej**.
  
### <a name="prepare-the-mailboxes-so-you-can-delete-the-spilled-data"></a>Przygotowywanie skrzynek pocztowych w celu usunięcia rozlanej danych

Jeśli funkcja odzyskiwania pojedynczych elementów jest włączona lub jeśli skrzynka pocztowa zostanie umieszczona w stanie przechowywania, trwale usunięta (usunięta) wiadomość zostanie zachowana w folderze Elementy do odzyskania. Dlatego zanim będzie można przeczyścić rozlane dane, musisz sprawdzić istniejące konfiguracje skrzynek pocztowych i wyłączyć odzyskiwanie pojedynczych elementów oraz usunąć wszelkie zasady przechowywania i blokowania. Pamiętaj, że możesz przygotować jedną skrzynkę pocztową na raz, a następnie uruchomić to samo polecenie dla różnych skrzynek pocztowych lub utworzyć skrypt programu PowerShell, aby przygotować wiele skrzynek pocztowych na raz.

- Zobacz "Krok 1. Zbieranie informacji o skrzynce pocztowej" w tesłudze Usuwanie elementów w [folderze](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-1-collect-information-about-the-mailbox) Elementy odzyskiwalne w chmurze skrzynek pocztowych umieszczonych w chmurze, aby uzyskać instrukcje dotyczące sprawdzania, czy funkcja odzyskiwania pojedynczych elementów jest włączona, czy skrzynka pocztowa została umieszczona w a hold lub jest przypisana do zasad przechowywania. 

- Aby uzyskać instrukcje dotyczące wyłączania odzyskiwania pojedynczych elementów, zobacz "Krok 2. Przygotowywanie skrzynki pocztowej" w tesłudze Usuwanie elementów w [folderze](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-2-prepare-the-mailbox) Elementy do odzyskania w chmurowych skrzynkach pocztowych w chmurze. 

- Aby uzyskać instrukcje dotyczące usuwania blokady lub zasad przechowywania ze skrzynki pocztowej, zobacz "Krok 3. Usuwanie wszystkich blokady ze skrzynki pocztowej" w tesłudze Usuwanie elementów w [folderze](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox) Elementy odzyskiwalne w chmurze skrzynek pocztowych w chmurze. 

- Aby uzyskać instrukcje dotyczące usuwania opóźnienia umieszczonego w skrzynce pocztowej po usunięciu dowolnego typu opóźnienia, zobacz "Krok 4. Usunięcie opóźnienia ze skrzynki pocztowej" w tece Usuwanie elementów z [folderu](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-4-remove-the-delay-hold-from-the-mailbox) Elementy odzyskiwalne w chmurowych skrzynkach pocztowych.

> [!IMPORTANT]
> Skontaktuj się z  swoimi działami zarządzania rekordami lub działami owymi przed usunięciem blokowania lub zasad przechowywania. Twoja organizacja może mieć zasady definiujące, czy skrzynka pocztowa w miejscu przechowywania lub zdarzenie rozlanie danych ma pierwszeństwo. 
  
Pamiętaj o przywróceniu skrzynki pocztowej do poprzednich konfiguracji po upewnieniu się, że rozlane dane zostały trwale usunięte. Zobacz szczegóły w [kroku 7](#step-7-permanently-delete-the-spilled-data).

## <a name="step-7-permanently-delete-the-spilled-data"></a>Krok 7. Trwałe usuwanie rozlanej danych

Teraz za pomocą lokalizacji skrzynki pocztowej zebranych i przygotowanych w kroku 6 oraz utworzonego i udoskonalonego w kroku 3 zapytania wyszukiwania w celu znalezienia wiadomości e-mail zawierających rozlane dane możesz teraz trwale usunąć rozlane dane.  Jak wyjaśniono wcześniej, aby usuwać wiadomości, musisz być członkiem grupy ról Zarządzanie organizacją lub mieć przypisaną rolę zarządzania Wyszukiwaniem i przeczyszczanie. Aby uzyskać informacje na temat dodawania użytkowników do grupy ról, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](./assign-ediscovery-permissions.md).

Aby usunąć rozlane wiadomości, zobacz [Wyszukiwanie i usuwanie wiadomości e-mail](search-for-and-delete-messages-in-your-organization.md).

Podczas usuwania danych rozlanej należy pamiętać o następujących ograniczeniach:

- Maksymalna liczba skrzynek pocztowych w wyszukiwaniu, za pomocą których można usuwać elementy przez wykonanie akcji wyszukiwania i przeczyszczania, wynosi 50 000. Jeśli wyszukiwanie w kroku 3 spowoduje przeszukanie ponad 50 000 skrzynek pocztowych, akcja przeczyszczania nie powiedzie się. Wyszukiwanie w więcej niż 50 000 skrzynek pocztowych w jednym wyszukiwaniu może się zazwyczaj odbywać po skonfigurowaniu wyszukiwania tak, aby uwzględniała wszystkie skrzynki pocztowe w organizacji. To ograniczenie obowiązuje nawet wtedy, gdy mniej niż 50 000 skrzynek pocztowych zawiera elementy zgodne z zapytaniem wyszukiwania.

- Jednocześnie można usunąć maksymalnie 10 elementów na skrzynkę pocztową. Funkcja wyszukiwania i usuwania wiadomości jest w zamierzony sposób narzędziem do reagowania na zdarzenia, dlatego ten limit pomaga szybko usuwać wiadomości ze skrzynek pocztowych. Ta funkcja nie jest przeznaczona do oczyszczania skrzynek pocztowych użytkowników.

> [!IMPORTANT]
> Za pomocą procedur  podanych w tym artykule nie można usuwać elementów Advanced eDiscovery e-mail z zestawu recenzji w przypadku Advanced eDiscovery przypadku. Jest tak, ponieważ elementy w zestawie recenzji są kopiami elementów w usłudze na żywo, które są kopiowane i przechowywane w lokalizacji usługi Azure Storage lokalizacji. Oznacza to, że nie zostaną one zwrócone przez wyszukiwanie zawartości, które tworzysz w kroku 3. Aby usunąć elementy z zestawu recenzji, należy usunąć Advanced eDiscovery przypadku, która zawiera zestaw recenzji. Aby uzyskać więcej informacji, [zobacz Zamykanie lub usuwanie Advanced eDiscovery przypadku](close-or-delete-case.md).
  
## <a name="step-8-verify-provide-a-proof-of-deletion-and-audit"></a>Krok 8. Weryfikowanie, dostarczenie dowodu usunięcia i inspekcja

Ostatnim krokiem przepływu pracy do zarządzania zdarzeniem rozlanie danych jest sprawdzenie, czy rozlane dane zostały trwale usunięte ze skrzynki pocztowej, przechodząc do sprawy zbierania elektronicznych materiałów dowodowych i ponownie uruchomić to samo zapytanie wyszukiwania, które zostało użyte do usunięcia tych danych, w celu potwierdzenia, że nie są zwracane żadne wyniki. Po potwierdzeniu, że rozlane dane zostały trwale usunięte, możesz wyeksportować raport i dołączyć go (wraz z oryginalnym raportem) jako dowód usunięcia. Następnie możesz zamknąć [sprawę, co](close-reopen-delete-core-ediscovery-cases.md) pozwoli na jej ponowne otwarcie, jeśli trzeba będzie odwołać się do tej sprawy w przyszłości. Ponadto można przywrócić skrzynki pocztowe do poprzedniego stanu, usunąć zapytanie wyszukiwania używane do znalezienia rozlanej danych i wyszukać rekordy inspekcji zadań wykonywanych podczas zarządzania zdarzeniem rozlanie danych.
  
### <a name="reverting-the-mailboxes-to-their-previous-state"></a>Przywracanie skrzynek pocztowych do poprzedniego stanu

Jeśli w kroku 6 zmieniono konfigurację skrzynek pocztowych w celu przygotowania skrzynek pocztowych przed usunięciem rozlanej danych, należy przywrócić ich poprzedni stan. Zobacz "Krok 6. Przywróć poprzedni stan skrzynki pocztowej" w tesłudze Usuwanie elementów z [folderu](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-6-revert-the-mailbox-to-its-previous-state) Elementy do odzyskania w chmurze skrzynki pocztowe zawieszone.
  
### <a name="deleting-the-search-query"></a>Usuwanie zapytania wyszukiwania

Jeśli słowa kluczowe w zapytaniu wyszukiwania utworzonym i użytym w kroku 3 zawierają część rzeczywistych danych rozlanych, należy usunąć zapytanie wyszukiwania, aby zapobiec dalszemu rozlewowi danych.
  
1. W Centrum zabezpieczeń i zgodności otwórz sprawę zbierania elektronicznych materiałów dowodowych, przejdź do strony wyszukiwania  i wybierz odpowiednie wyszukiwanie zawartości.

2. Na stronie wysuwu kliknij pozycję **Usuń**.

    ![Zaznacz wyszukiwanie, a następnie na wysuwanych stronie kliknij pozycję Usuń.](../media/O365-eDiscoverySolutions-DataSpillage-DeleteSearch.png)

### <a name="auditing-the-data-spillage-investigation-process"></a>Inspekcja procesu badania rozlanie danych

W dzienniku inspekcji można wyszukiwać działania zbierania elektronicznych materiałów dowodowych wykonane podczas badania. Możesz również przeszukać dziennik inspekcji, aby zwrócić rekordy inspekcji pod poszukiwaniu polecenia **New-ComplianceSearchAction -Purge** , które uruchomiono w kroku 7, w celu usunięcia rozlanej danych. Więcej informacji można znaleźć w następujących artykułach:

- [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md)

- [Wyszukiwanie działań zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji](search-for-ediscovery-activities-in-the-audit-log.md)
