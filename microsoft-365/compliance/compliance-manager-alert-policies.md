---
title: Alerty i zasady alertów Menedżera zgodności firmy Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak tworzyć alerty dotyczące działań w Menedżerze zgodności firmy Microsoft, które mogą mieć wpływ na twoją ocenę zgodności.
ms.openlocfilehash: bb81588be31b2c13113953c585112ee2f5a56875
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704690"
---
# <a name="microsoft-compliance-manager-alerts-and-alert-policies"></a>Alerty i zasady alertów Menedżera zgodności firmy Microsoft

**W tym artykule:** Dowiedz się, jak **ustawiać alerty** dla określonych działań w Menedżerze zgodności, jak zarządzać alertami i jak tworzyć zasady **alertów** definiujące warunki alertów.

## <a name="overview"></a>Omówienie
Dział zgodności może powiadamiać Cię o zmianach zaraz po ich w wmietrzeniu, dzięki czemu możesz śledzić swoje cele dotyczące zgodności. Możesz na przykład skonfigurować alerty informujące o tym, że wartość wyniku akcji udoskonalania wzrasta lub maleje wskutek zmiany konfiguracji w dzierżawie lub gdy użytkownikowi przypisano działanie udoskonalania w celu wykonania pracy implementacji lub testowania. Wyświetlaj [typy zdarzeń,](#create-an-alert-policy) dla których możesz tworzyć alerty.

Aby utworzyć alerty, najpierw skonfiguruj zasady alertów w celu utworzenia konspektu warunków wyzwalania alertu i częstotliwości powiadomień. Po wykryciu dopasowania do warunków Twoich zasad otrzymasz wiadomość e-mail ze szczegółami, dzięki czemu będziesz w stanie ustalić, czy chcesz go zbadać, czy podjąć dalsze działania.


Wszystkie alerty są wyświetlane na karcie **Alerty** w Obszarze kontroli zgodności, a wszystkie zasady alertów są wyświetlane na **karcie Zasady alertów**.

## <a name="understanding-the-alerts-and-alert-policies-pages"></a>Opis stron Alerty i Zasady alertów

> [!IMPORTANT]
> Użytkownicy muszą **mieć rolę** czytnika zabezpieczeń w u Azure Active Directory (AD), aby uzyskać dostęp do stron Alerty  i Zasady **alertów** w Menedżerze zgodności. Do pracy z alertami i zasadami alertów potrzebne są dodatkowe role w Menedżerze zabezpieczeń i zgodności. Szczegóły poniżej znajdziesz w artykule [Uprawnienia do zasad alertów](#alert-policy-permissions).

### <a name="alert-policies-page"></a>Strona Zasady alertów

Wybierz **kartę Zasady alertów** w Obszarze Zarządzania zgodnością, aby wyświetlić zasady alertów i zarządzać nimi. Strona **Zasady alertów** zawiera tabelę zawierającą wszystkie zasady utworzone przez Twoją organizację. Na tej stronie możesz tworzyć nowe zasady, edytować istniejące zasady, zmieniać stan aktywacji i usuwać zasady.

W kolumnie **Stan kolumna Aktywne oznacza****, że** zasady są w mocy i powodują wyzwalanie alertów, gdy warunki są spełnione. **Nieaktywny** oznacza, że zasady istnieją, ale nie generują alertów. W tabeli zasad pokazano także ważność zasad i datę ich ostatniej modyfikacji.

Aby wyświetlić szczegóły poszczególnych zasad, wybierz jej wiersz w tabeli. Zostanie wyświetlone okienko wysuwu ze wszystkimi szczegółami. Wybierz przycisk **Akcja** u dołu okienka i wybierz jedną z opcji, aby edytować zasady, wyświetlać alerty lub je usuwać. Polecenia dodawania, edytowania, usuwania, aktywowania i wyłączania są również dostępne w górnej części tabeli powyżej filtrów.

Aby rozpocząć tworzenie zasad alertów, zobacz [Tworzenie zasad alertów](#create-an-alert-policy).

### <a name="alerts-page"></a>Strona Alerty

Wybierz **kartę Alerty** w Menedżerze zgodności, aby wyświetlić alerty i zarządzać nimi. Strona **Alerty** zawiera tabelę z listą alertów wygenerowanych przez zasady alertów, wraz z ich ważnością i zdarzeniem wyzwalania (na przykład zmianą wyniku akcji) oraz datą alertu.

Aby wyświetlić pojedynczy alert, zaznacz jego wiersz w tabeli. Zostanie wyświetlone okienko wysuwu ze wszystkimi szczegółami **na karcie** Przegląd w okienku. Na **karcie Dziennik zdarzeń** są wyświetlane akcje wykonane przez użytkowników, którzy wyzwolyli alert.

**Przycisk Akcja** w dolnej części okienka zawiera opcje przypisania alertu do użytkownika w celu dosyć do użytkownika w celu dosyć jego działania w wiadomości e-mail, a także wyświetlenie szczegółów zasad, które wygenerują alert. Te same akcje można też podjąć, wybierając przycisk zaokrąglania wyświetlany po lewej stronie nazwy alertu po umieszczeniu wskaźnika myszy na jego wierszu, a następnie wybierając jeden z przycisków w górnej części tabeli nad filtrami.

Aby rozpocząć pracę z alertami, zobacz [Wyświetlanie alertów i zarządzanie nimi](#viewing-and-managing-alerts).

## <a name="alert-policy-permissions"></a>Alert policy permissions

W poniższej tabeli przedstawiono, którzy użytkownicy mogą tworzyć i edytować alerty oraz zasady alertów na podstawie typu roli. Oprócz posiadania roli Menedżera zgodności użytkownicy muszą mieć również następującą rolę w usłudze Azure AD:

- Rola **czytnika zabezpieczeń** w usłudze Azure AD do wyświetlania alertów i zasad alertów
- Rola **administratora zabezpieczeń w** usłudze Azure AD do tworzenia lub aktualizowania zasad alertów
 
Dowiedz się więcej [o rolach platformy Azure w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#azure-roles-in-the-microsoft-365-compliance-center).


| Rola | Może tworzyć i edytować zasady | Może edytować alerty | 
| :------------- | :-------------: | :------------: |
| **Administracja Menedżera zgodności**| Tak  | Tak | 
| **Ocenianie menedżera zgodności**| Tak | Tak | 
| **Udział menedżera zgodności**| Tak | Tak | 
| **Administrator globalny**| Nie | Nie  | 
| **Czytnik Menedżera zgodności**| Nie | Nie | 

Dowiedz się, jak [ustawić uprawnienia użytkowników i przypisać role w Menedżerze zgodności](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-an-alert-policy"></a>Tworzenie zasad alertów

Możesz utworzyć zasady, aby powiadamiać Cię o pewnych zmianach lub zdarzeniach związanych z działaniami udoskonalania. Poniżej wymieniono typy zdarzeń.

### <a name="alert-event-types"></a>Typy zdarzeń alertów

- **Zmiana wyniku**: zwiększenie lub zmniejszenie liczby punktów przyznanych za działanie usprawnione ze względu na zmiany w konfiguracji wprowadzone przez osobę w Twojej organizacji. Jeśli na przykład organizacja tworzy zasady zarządzania ryzykiem niejawnego programu testów, liczba punktów za określone działanie może zwiększyć się o określonej kwoty.
- **Zmiana przydziału**: użytkownikowi przypisano akcję udoskonalania, przypisano go ponownie do innego użytkownika lub nie przypisano go użytkownikowi.
- **Zmiana stanu implementacji**: użytkownik zmienił stan implementacji akcji udoskonalania.
- **Zmiana stanu testu**: użytkownik zmienił stan testowania w działaniu usprawniacym.
- **Zmiana dowodu**: użytkownik przesłał lub usunął dokument dowodowy  na karcie Dokumenty w działaniu usprawniacym.

### <a name="policy-creation-steps"></a>Kroki tworzenia zasad

Aby utworzyć zasady generowania alertów na podstawie jednego lub większej liczby zdarzeń, wykonaj poniższe czynności:

1. W **Menedżerze zgodności** przejdź do strony **Zasady alertów** i wybierz pozycję **+Dodaj** , aby uruchomić kreatora tworzenia zasad.

2. Na **stronie Nazwa i opis** wprowadź nazwę zasad i opcjonalny opis, a następnie wybierz pozycję **Dalej**.

3. Na stronie **Warunki** wybierz co najmniej jedno zdarzenie, które spowoduje wyzwolenie alertu. W **nagłówku Działanie akcji Udoskonalanie** wybierz pozycję **Dodaj** warunki podrzędne i zaznacz pole wyboru, które pojawia się po umieszczeniu wskaźnika myszy z lewej strony nazwy każdego warunku. Możesz wybrać jeden lub więcej warunków zasad: zmiana przydziału, zmiana dowodu, zmiana stanu implementacji, zmiana wyniku, zmiana stanu testu. Po zakończeniu wybierz pozycję **Dalej**.

4. Na **stronie Wyniki wybierz** , co się stanie, gdy zostanie wykryte dopasowanie zasad:
      - Wybierz poziom ważności alertu, gdy zostanie wykryte dopasowanie: niski, średni lub wysoki.
      - Określ, jak często wiadomości e-mail mają być powiadamiane o wykryciu dopasowania. Możesz wybrać opcję powiadomienia o każdym dopasowaniu lub wybrać próg określonej liczby dopasowań powyżej trzech.
      - Jeśli zdecydujesz się na powiadomienie po trzech lub większej liczbie spotkań, następnie określisz liczbę minut, w których ten próg musi zostać osiągnięty (na przykład 4 dopasowania w ciągu 90 minut).
  
    Po wybraniu przycisku **Dalej**.

5. Na stronie **Adresat alertu** wybierz dodatkowych użytkowników w organizacji, aby otrzymać wiadomość e-mail po spełnieniu warunków zasad. Domyślnym adresatem jest użytkownik tworzący zasady. Wybierz **pozycję +Wybierz adresatów** i zaznacz pola wyboru obok nazw poszczególnych użytkowników w okienku wysuwanych, do których chcesz otrzymać powiadomienie e-mail. Gdy wszystko jest gotowe, wybierz **pozycję Dodaj adresatów**, a następnie wybierz pozycję **Dalej**.

6. Przejrzyj wszystkie opcje i w każdej sekcji dokonaj zmian, wybierając pozycję , a następnie pozycję **Dalej**. Po zakończeniu przeglądania wybierz pozycję **Utwórz zasady**.

7. Po utworzeniu zasad wybierz pozycję **Gotowe**. Dotrzesz do strony **Zasady alertów** z okienkiem wysuwanym dla właśnie utworzonych zasad.

Zasady są aktywne po ich utworzeniu, co oznacza, że zaczną wykrywać dopasowania i generować alerty. Zobacz **sekcję Zarządzanie zasadami** poniżej, aby dowiedzieć się, jak dezaktywować lub usuwać zasady.

Utworzenie lub zaktualizowanie zasad może potrwać do 24 godzin, zanim alerty zostaną wygenerowane przez te zasady. Zobacz [Wyświetlanie szczegółów alertów](#view-alert-details) poniżej, aby dowiedzieć się więcej o wyzwalaniu zdarzeń i agregacji alertów.

## <a name="managing-policies"></a>Zarządzanie zasadami

Strona **Zasady alertów** zawiera tabelę zawierającą listę wszystkich zasad. Zobacz [stronę Zasady alertów,](#alert-policies-page) aby lepiej poznać tę stronę. Każdy użytkownik w organizacji może wyświetlać zasady, ale niektóre akcje są ograniczone do określonych ról. zobacz [Alert o uprawnieniach zasad](#alert-policy-permissions).

### <a name="view-policy-details"></a>Wyświetl szczegóły zasad

Wybierz zasady z jej wiersza na stronie Zasady **alertów** , aby włączyć panel wysuwu przedstawiający szczegóły zasad, w tym warunki ich dopasowania, informacje o tym, czy i kiedy są wysyłane powiadomienia alertów oraz do kogo i na poziomie ważności.

Przycisk **Akcje** u dołu panelu udostępnia opcje edytowania zasad, usuwania zasad i wyświetlania alertów.

### <a name="view-a-policys-alerts"></a>Wyświetlanie alertów dotyczących zasad

W panelu wysuwu zasad wybierz pozycję Akcje **,** a następnie **Wyświetl alerty**. Zostaniesz przejść bezpośrednio do strony Alerty z przefiltrowanym widokiem wszystkich alertów wygenerowanych przez te zasady. Dowiedz się, jak [pracować z alertami](#viewing-and-managing-alerts).

### <a name="edit-a-policy"></a>Edytowanie zasad

Możesz edytować dowolny aspekt zasad, z wyjątkiem jego nazwy. Jeśli chcesz zmienić jej nazwę, musisz utworzyć nowe zasady pod nową nazwą.

Aby edytować zasady, wybierz przycisk rundy, który pojawia się po lewej stronie jej nazwy po umieszczeniu wskaźnika myszy na wierszu na stronie **Zasady alertów** i  wybraniu przycisku Edytuj w górnej części nad filtrami.

Zostaniesz przejść do kreatora tworzenia zasad, w którym możesz wprowadzać i zapisywać zmiany zasad.  Możesz także wybrać zasady, aby wyprowadzić ich panel szczegółów, a następnie na **przycisku Akcje** wybrać pozycję **Edytuj zasady**. Po zakończeniu pracy z kreatorem ponownie przejrzyj wybrane ustawienia i w ostatnim kroku wybierz pozycję **Aktualizuj** , aby zapisać zmiany.

Wygenerowanie alertów przez zaktualizowane zasady może potrwać do 24 godzin.

### <a name="activate-or-inactivate-a-policy"></a>Aktywowanie lub dezaktywowanie zasad

Zasady są domyślnie aktywowane zaraz po ich utworzeniu. Gdy zasady są aktywne, po spełnieniu warunków zasady (wyświetlane na  stronie Alerty) są wyświetlane alerty, a wskazanym adresatom zostanie wysyłana wiadomość e-mail z powiadomieniem.

Aby zmienić zasady na stan nieaktywny, co oznacza, że nie będą generowane alerty, wybierz przycisk zaokrąglony, który jest wyświetlany po lewej stronie nazwy zasad po umieszczeniu wskaźnika myszy na jej wierszu. Następnie wybierz **polecenie Wyłącz** powyżej tabeli. Stan zasad będzie teraz miał stan Nieaktywny. Aby ponownie aktywować zasady, postępuj zgodnie z tym samym procesem i wybierz przycisk **Aktywuj** powyżej filtrów.

### <a name="delete-a-policy"></a>Usuwanie zasad

Aby usunąć zasady, wybierz przycisk obok jej nazwy na stronie **Zasady alertów** i wybierz pozycję Usuń w górnej  części strony. Możesz także wybrać zasady, aby wyprowadzić ich panel szczegółów, a następnie na **przycisku Akcje** wybrać pozycję **Usuń zasady**.

Usuwanie jest trwałe. Po usunięciu zasad nie będą one już generować alertów ani powiadomień e-mail. Dowiedz się więcej o [alertach połączonych z usuniętymi zasadami](#when-policies-are-deleted).

## <a name="viewing-and-managing-alerts"></a>Wyświetlanie alertów i zarządzanie nimi

Na **stronie Alerty** jest pokazana tabela ze wszystkimi alertami wygenerowania przez wszystkie zasady. Alerty są generowane niemal natychmiast po zdarzeniu zgodnym z warunkami określonych przez zasady. Nazwa alertu jest taka sama jak nazwa zasady, która wygenerowała alert.

Alert można wygenerować tylko na podstawie aktywnych zasad. Po wygenerowaniu alertu pozostanie on wymieniony na stronie **Alerty** bez względu na to, czy zasady są aktywne, czy nieaktywne.

### <a name="filter-your-view-of-alerts"></a>Filtrowanie widoku alertów
Widok alertów można filtrować, wybierając polecenie **Filtruj** powyżej tabeli na **stronie Alerty** . W **okienku** wysuwany Filtr wybierz jedną z tych opcji filtru:

- Typ zdarzenia
- Ważność
- Stan
- Użytkownik przypisany do
- Data wykrywania
- Nazwa zasad

Po wybraniu opcji wybierz pozycję **Zastosuj**. Okienko wysuwu zostanie zamknięte, a na zaktualizowanej stronie **alertów** zostanie pokazany widok filtrowany. Filtry są wyświetlane u góry tabeli, ale nie wszystkie kolumny filtrów mogą być widoczne w tabeli.

### <a name="view-alert-details"></a>Wyświetlanie szczegółów alertu

Aby wyświetlić wszystkie szczegóły alertu, w tym zdarzenia, które go wyzwoliły, zaznacz jego wiersz w tabeli. W okienku wysuwanym na karcie Przegląd panelu zostaną wyświetlane  szczegóły alertu.

Karta **Dziennik** zdarzeń w panelu wysuwanym zawiera informacje o działaniach, które wygenerowały alert, takich jak zmiana wyniku lub zmiana przydziału, wraz z nazwą użytkownika skojarzonego z każdą akcją i wykrytym datą.

### <a name="alert-events"></a>Zdarzenia alertów

W **kolumnie Zdarzenia** na **stronie Alerty** są wskazywane warunki wykrytych zasad. innymi słowy: działanie, które wygenerowała alert. Karta **Dziennik zdarzeń** w panelu szczegółów alertu zawiera listę wszystkich wystąpień zdarzenia, skojarzonego użytkownika i wykrytej daty. Poniżej wymieniono wartości zdarzeń:

- **Zmiana wyniku**: pokazuje liczbę wzrostu lub spadku punktów.
- **Zmiana przydziału**: użytkownikowi przypisano akcję udoskonalania, przypisano go ponownie do innego użytkownika lub nie przypisano go użytkownikowi
- **Zmiana stanu implementacji**: użytkownik zmienił stan implementacji akcji udoskonalania
- **Zmiana stanu testu**: użytkownik zmienił stan testowania w działaniu usprawniacym.
- **Zmiana dowodu**: użytkownik przesłał lub usunął dokument dowodowy na karcie Dokumenty w działaniu usprawniacym
- **Wiele zdarzeń**: wykryto wiele wystąpień tego samego typu zdarzenia. na przykład jedno działanie ulepszeń, które zostało ponownie ponownie przypisane wielokrotnie
- **Warunek wielokrotny**: wykryto wiele warunków w ramach jednej zasady

#### <a name="alert-aggregation-for-multiple-events-within-one-minute"></a>Agregacja alertów dla wielu zdarzeń w ciągu jednej minuty

Gdy w jednej minucie występuje wiele zdarzeń, które są zgodne z warunkami zasad alertu, są one dodawane do istniejącego alertu przez proces nazywany agregacją alertów.

Na przykład w przypadku wystąpienia jednego zdarzenia, które jest odpowiada zasad, jest generowany i wyświetlany na stronie **Alerty** oraz jest wysyłane powiadomienie. Jeśli w ciągu jednej minuty od pierwszego zdarzenia wystąpi inne zdarzenie zgodne z tym samymi zasadami, Menedżer zgodności doda szczegółowe informacje o dodatkowym zdarzeniu na karcie Dziennik zdarzeń istniejącego alertu, zamiast wyzwalać nowy alert. Celem agregacji alertów jest ograniczenie "zmęczenia" alertów oraz skupienie się i działanie na mniejszej liczbie alertów.

### <a name="taking-action-on-alerts"></a>Podejmowanie działań dotyczących alertów

Gdy jedna z zasad generuje alert, możesz wyświetlić zdarzenia, które spowodowały alert, i określić, czy należy je zweryfikować, czy dokładniej zbadać.

Aby podjąć akcję dla alertu, wybierz jego wiersz na stronie Alerty, aby wyprowadzić panel wysuwu z jego szczegółami, wybierz przycisk Akcje i wybierz jedną z opcji wymienionych poniżej. Możesz również podjąć działania, wybierając przycisk zaokrąglania wyświetlany po lewej stronie nazwy alertu po umieszczeniu wskaźnika myszy na jego wierszu i wybierając jeden z przycisków akcji w górnej części strony powyżej filtrów.

**Przypisywanie alertu**: Możesz przypisać alert do użytkownika, aby zbadał lub zweryfikował zdarzenia, które spowodowały alert. Po wybraniu tej opcji zostanie otwarty panel, w którym możesz wybrać użytkownika w organizacji i przypisać mu alert. Widok alertów można filtrować, wybierając  pozycję Filtry na stronie **Alerty** i wprowadzając nazwę użytkownika w polu Przypisany **do**.

**Alert e-mail**: Możesz wysłać wiadomość e-mail do użytkownika skojarzonego z aktywnością alertu, aby potwierdzić, że zrobił to działanie. W przypadku wybrania tej opcji zostanie otwarty szablon wiadomości e-mail z podstawowymi informacjami o alercie, który można dostosować, korzystając z dodatkowych instrukcji i wysłanych do użytkownika.

**Wyświetl szczegóły zasad**: Możesz przejrzeć ustawienia zasad, które wyzwolyły alert. Pamiętaj, że po wybraniu tej opcji zostanie bezpośrednio otwarta strona **Zasady alertów** z już otwartym panelem szczegółów zasad. Po zamknięciu panelu szczegółów zasad nie  będziesz już mieć dostępu do strony Alerty.

**Zmień stan**: Stan alertu można zaktualizować na podstawie jego wpływu i tego, czy jest on wymaga zbadania. Więcej informacji o stanie alertów zawiera następna sekcja.

### <a name="alert-status"></a>Stan alertu

Po utworzeniu alertu jego stan to **Aktywny**. Podczas przeglądania szczegółów poszczególnych alertów możesz zaktualizować jego stan do dowolnego z wymienionych poniżej stanów:

- **Aktywny**: domyślny stan alertu do czasu jego zmiany
- **Badanie**: trwa badanie alertu
- **Rozwiązano**: alert nie wymaga dalszego badania ani dalszych działań
- **Odrzucone**: alert nie jest istotny lub nie wymaga badania

Aby przypisać lub zmienić stan alertu, wybierz alert z jego wiersza w tabeli, wybierz pozycję Zmień **stan** w górnej części strony powyżej filtrów. W okienku wysuwanym Aktualizuj stan alertu wybierz stan z menu rozwijanego, a następnie wybierz pozycję **Aktualizuj alert**.

Po wygenerowaniu alertu jego stan jest niezależny od stanu zasad, które wygenerują alert. Z zasadami nieaktywnymi można na przykład skojarzyć **aktywny alert** i można mieć stan badania nad alertem wygenerowanym przez  zasady, które zostały następnie dezaktywowane lub usuwane.

### <a name="when-policies-are-deleted"></a>Po usunięciu zasad

Po usunięciu zasad wszystkie alerty, które zostały wygenerowane przez te zasady, pozostaną na stronie **Alerty** , ale nie będą generowane żadne nowe alerty.

## <a name="email-notifications-of-alerts"></a>Powiadomienia e-mail o alertach

Podczas tworzenia zasad do użytkownika, który utworzył zasady, jest wysyłana wiadomość e-mail z ostrzeżeniem o wykryciu dopasowania. Możesz wysyłać te powiadomienia e-mail do dodatkowych użytkowników w Twojej organizacji. Alerty występują w czasie rzeczywistym, a powiadomienia e-mail są wysyłane zaraz po wygenerowaniu alertu. Wiadomość e-mail będzie zawierać nazwę zdarzenia, ważność, wykryty czas i link do wyświetlania alertu w Menedżerze zgodności.

### <a name="remove-users-from-receiving-alerts"></a>Usuwanie użytkowników z otrzymywania alertów

Jeśli określisz adresatów alertów, a następnie później zdecydujesz się ich usunąć, wykonaj poniższe czynności. Pamiętaj, że twórca zasad nadal będzie otrzymywać powiadomienia e-mail po wykryciu dopasowania zasad.

1. Rozpocznij procedurę [edytowania zasad](#edit-a-policy).
2. Po dojecheniu do **ekranu Adresatów alertów** wybierz pozycję **+Wybierz adresatów**.
3. W panelu wysuwanego Wybierz adresatów znajdź użytkownika, którego chcesz usunąć z powiadomień, i wyczyść pole wyboru po lewej stronie jego nazwy, a następnie  wybierz przycisk Dodaj adresatów (co ma wpływ na zapisanie wyboru).
4. Kontynuuj korzystanie z kreatora i upewnij się, że użytkownik nie jest widoczny w obszarze **Adresaci** na stronie Recenzja i zakończenie. Wybierz **pozycję Aktualizuj** , aby zapisać ustawienia i zakończyć.
