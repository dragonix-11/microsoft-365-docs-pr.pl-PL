---
title: Alerty i zasady alertów programu Microsoft Purview Compliance Manager
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
description: Dowiedz się, jak tworzyć alerty dla działań w programie Microsoft Purview Compliance Manager, które mogą mieć wpływ na wynik zgodności.
ms.openlocfilehash: b1e5630e20ace4835f8651d1878e731e423f58b1
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129161"
---
# <a name="microsoft-purview-compliance-manager-alerts-and-alert-policies"></a>Alerty i zasady alertów programu Microsoft Purview Compliance Manager

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**W tym artykule:** Dowiedz się, jak **ustawić alerty** dla niektórych działań w Menedżerze zgodności, jak zarządzać alertami i jak **tworzyć zasady alertów** na potrzeby definiowania warunków alertów.

## <a name="overview"></a>Omówienie
Menedżer zgodności może otrzymywać alerty o zmianach natychmiast po ich wystąpieniu, dzięki czemu możesz być na bieżąco ze swoimi celami zgodności. Można na przykład skonfigurować alerty, aby poinformować użytkownika, kiedy wartość oceny akcji poprawy została zwiększona lub zmniejszona z powodu zmiany konfiguracji w dzierżawie lub gdy do użytkownika została przypisana akcja poprawy w celu wykonania operacji implementacji lub testowania. Wyświetl [typy zdarzeń,](#create-an-alert-policy) dla których można tworzyć alerty.

Aby utworzyć alerty, najpierw skonfiguruj zasady alertów, aby określić warunki wyzwalające alert i częstotliwość powiadomień. Po wykryciu dopasowania do warunków zasad otrzymasz powiadomienie e-mail ze szczegółowymi informacjami, aby określić, czy należy zbadać, czy podjąć dalsze działania.


Wszystkie alerty są wyświetlane na karcie **Alerty** w obszarze Zarządzanie zgodnością, a wszystkie zasady alertów są wyświetlane na **karcie Zasady alertów**.

## <a name="understanding-the-alerts-and-alert-policies-pages"></a>Omówienie stron Alerty i zasady alertów

> [!IMPORTANT]
> Użytkownicy muszą mieć rolę **czytelnika zabezpieczeń** w Azure Active Directory (AD), aby uzyskać dostęp do stron **Alerty** i **zasady alertów** w Menedżerze zgodności. Dodatkowe role menedżera zabezpieczeń i zgodności są potrzebne do pracy z alertami i zasadami alertów. Uzyskaj szczegółowe informacje poniżej w [obszarze Uprawnienia zasad alertów](#alert-policy-permissions).

### <a name="alert-policies-page"></a>Strona zasad alertów

Wybierz kartę **Zasady alertów** w obszarze Zarządzanie zgodnością, aby wyświetlić zasady alertów i zarządzać nimi. Strona **Zasady alertów** zawiera tabelę zawierającą listę wszystkich zasad utworzonych przez organizację. Na tej stronie można tworzyć nowe zasady, edytować istniejące zasady, zmieniać stan aktywacji i usuwać zasady.

W **kolumnie Stan** **wartość Aktywne** oznacza, że zasady obowiązują i wyzwalają alerty po spełnieniu warunków. **Nieaktywne** oznacza, że zasady istnieją, ale nie generują alertów. W tabeli zasad przedstawiono również ważność zasad i datę ostatniej modyfikacji zasad.

Aby wyświetlić szczegóły poszczególnych zasad, wybierz jego wiersz w tabeli. Zostanie wyświetlone okienko wysuwane zawierające wszystkie szczegóły. Wybierz przycisk **Akcja** w dolnej części okienka i wybierz opcje, aby edytować zasady, wyświetlać alerty lub usuwać je. Polecenia dodawania, edytowania, usuwania, aktywowania i wyłączania są również dostępne w górnej części tabeli powyżej filtrów.

Aby rozpocząć tworzenie zasad alertów, zobacz [Tworzenie zasad alertów](#create-an-alert-policy).

### <a name="alerts-page"></a>Strona Alerty

Wybierz kartę **Alerty** w Menedżerze zgodności, aby wyświetlić alerty i zarządzać nimi. Strona **Alerty** zawiera tabelę zawierającą listę każdego alertu wygenerowanego przez zasady alertów wraz z jego ważnością i zdarzeniem wyzwalającym (na przykład zmianą wyniku akcji) i datą alertu.

Aby wyświetlić pojedynczy alert, wybierz jego wiersz w tabeli. Zostanie wyświetlone okienko wysuwane, w którym zostaną wyświetlone wszystkie szczegóły na karcie **Przegląd** okienka. Na karcie **Dziennik zdarzeń** są wyświetlane akcje wykonywane przez użytkowników, którzy wyzwolili alert.

Przycisk **Akcja** w dolnej części okienka zawiera opcje przypisywania alertu do użytkownika w celu podjęcia dalszych działań, wysłania wiadomości e-mail do użytkownika, którego akcje wygenerowały alert, lub wyświetlenia szczegółów zasad, które generują alert. Możesz również wykonać te same akcje, wybierając okrągły przycisk wyświetlany po lewej stronie nazwy alertu po umieszczeniu wskaźnika myszy nad jego wierszem, a następnie wybierając jeden z przycisków w górnej części tabeli powyżej filtrów.

Aby rozpocząć pracę z alertami, zobacz [Wyświetlanie alertów i zarządzanie nimi](#viewing-and-managing-alerts).

## <a name="alert-policy-permissions"></a>Uprawnienia zasad alertów

W poniższej tabeli przedstawiono, którzy użytkownicy mogą tworzyć i edytować alerty i zasady alertów na podstawie typu roli. Oprócz posiadania roli Menedżera zgodności użytkownicy potrzebują również roli Azure AD w następujący sposób:

- Rola **czytelnika zabezpieczeń** w Azure AD do wyświetlania alertów i zasad alertów
- Rola **administratora zabezpieczeń** w Azure AD do tworzenia lub aktualizowania zasad alertów
 
Dowiedz się więcej o [rolach platformy Azure w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#azure-roles-in-the-compliance-portal).


| Rola | Może tworzyć i edytować zasady | Może edytować alerty | 
| :------------- | :-------------: | :------------: |
| **Administracja programu Compliance Manager**| Tak  | Tak | 
| **Asesor menedżera zgodności**| Tak | Tak | 
| **Wkład menedżera zgodności**| Tak | Tak | 
| **Administrator globalny**| Tak | Tak  | 
| **Czytelnik programu Compliance Manager**| Nie | Nie | 

Dowiedz się, jak [ustawić uprawnienia użytkownika i przypisać role dla Menedżera zgodności](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-an-alert-policy"></a>Tworzenie zasad alertów

Możesz utworzyć zasady, aby otrzymywać alerty, gdy wystąpią pewne zmiany lub zdarzenia związane z akcjami poprawy. Typy zdarzeń są wymienione poniżej.

### <a name="alert-event-types"></a>Typy zdarzeń alertów

- **Zmiana wyniku**: wzrost lub spadek liczby punktów przyznawanych za akcję poprawy z powodu zmian konfiguracji wprowadzonych przez kogoś w organizacji. Jeśli na przykład organizacja tworzy zasady zarządzania ryzykiem wewnętrznym, może to zwiększyć liczbę punktów dla określonej akcji o określoną kwotę.
- **Zmiana przypisania**: akcja poprawy została przypisana do użytkownika, ponownie przypisana do innego użytkownika lub nie została przypisana od użytkownika.
- **Zmiana stanu implementacji**: użytkownik zmienił stan implementacji akcji poprawy.
- **Zmiana stanu testu**: użytkownik zmienił stan testowania akcji poprawy.
- **Zmiana dowodów**: użytkownik przekazał lub usunął dokument dowodowy na karcie **Dokumenty** akcji poprawy.

### <a name="policy-creation-steps"></a>Kroki tworzenia zasad

Aby utworzyć zasady do generowania alertów na podstawie co najmniej jednego zdarzenia, wykonaj poniższe kroki:

1. W **Menedżerze zgodności** przejdź do strony **Zasady alertów** i wybierz pozycję **+Dodaj** , aby uruchomić kreatora tworzenia zasad.

2. Na stronie **Nazwa i opis** wprowadź nazwę zasad i opcjonalny opis, a następnie wybierz pozycję **Dalej**.

3. Na stronie **Warunki** wybierz co najmniej jedno zdarzenie, które wyzwoli alert. W nagłówku **działania Akcja poprawy** wybierz pozycję **Dodaj warunki podrzędne** i zaznacz pole wyboru wyświetlane po umieszczeniu wskaźnika myszy na lewo od nazwy każdego warunku. Możesz wybrać jeden lub więcej warunków dla zasad: zmiana przypisania, zmiana dowodów, zmiana stanu implementacji, zmiana wyniku, zmiana stanu testu. Po zakończeniu wybierz pozycję **Dalej**.

4. Na stronie **Wyniki** wybierz, co się stanie po wykryciu dopasowania zasad:
      - Wybierz poziom ważności alertu po wykryciu dopasowania: niski, średni lub wysoki.
      - Wybierz, jak często chcesz być powiadamiany pocztą e-mail po wykryciu dopasowania. Możesz zdecydować się na powiadomienie o każdym dopasowaniu lub wybrać próg określonej liczby dopasowań powyżej trzech.
      - Jeśli zdecydujesz się na powiadomienie po co najmniej trzech meczach, wyznaczysz liczbę minut, w których ten próg musi zostać osiągnięty (na przykład 4 dopasowania w ciągu 90 minut).
  
    Po zakończeniu wybierz pozycję **Dalej**.

5. Na stronie **Adresat alertu** wybierz dodatkowych użytkowników w organizacji, którzy otrzymają wiadomość e-mail po spełnieniu warunków zasad. Użytkownik, który tworzy zasady, jest adresatem domyślnym. Wybierz **pozycję +Wybierz adresatów** i zaznacz pola obok każdej nazwy użytkownika w okienku wysuwanego, którego chcesz otrzymać powiadomienie e-mail. Po zakończeniu wybierz pozycję **Dodaj adresatów**, a następnie wybierz pozycję **Dalej**.

6. Przejrzyj wszystkie wybrane opcje i wprowadź wszelkie zmiany w każdej sekcji, wybierając pozycję , a następnie wybierz pozycję **Dalej**. Po zakończeniu przeglądania wybierz pozycję **Utwórz zasady**.

7. Po utworzeniu zasad wybierz pozycję **Gotowe**. Zostanie wyświetlona strona **Zasady alertów** z okienkiem wysuwanym dla właśnie utworzonych zasad.

Zasady są aktywne po utworzeniu, co oznacza, że zaczną wykrywać dopasowania i generować alerty. Zobacz sekcję **Zarządzanie zasadami** poniżej, aby dowiedzieć się, jak inaktywować lub usuwać zasady.

Utworzenie lub zaktualizowanie zasad może potrwać do 24 godzin, zanim alerty zostaną wygenerowane przez te zasady. Zobacz [Wyświetlanie szczegółów alertów](#view-alert-details) poniżej, aby dowiedzieć się więcej o wyzwalaniu zdarzeń i agregacji alertów.

## <a name="managing-policies"></a>Zarządzanie zasadami

Strona **Zasady alertów** zawiera tabelę zawierającą listę wszystkich zasad. Zobacz [stronę Zasady alertów](#alert-policies-page) , aby dokładniej zrozumieć tę stronę. Każdy użytkownik w organizacji może wyświetlać zasady, ale niektóre akcje są ograniczone do określonych ról; zobacz [Uprawnienia zasad alertów](#alert-policy-permissions).

### <a name="view-policy-details"></a>Wyświetlanie szczegółów zasad

Wybierz zasady z wiersza na stronie **Zasady alertów** , aby wyświetlić panel wysuwany zawierający szczegóły zasad, w tym warunki dopasowania, informacje o tym, czy i kiedy są wysyłane powiadomienia o alertach oraz do kogo i na poziomie ważności.

Przycisk **Akcje** w dolnej części panelu umożliwia edytowanie zasad, usuwanie zasad lub wyświetlanie alertów.

### <a name="view-a-policys-alerts"></a>Wyświetlanie alertów zasad

Z panelu wysuwanego zasad wybierz pozycję **Akcje** , a następnie **pozycję Wyświetl alerty**. Nastąpi przekierowanie bezpośrednio do strony Alerty z filtrowanym widokiem wszystkich alertów generowanych przez te zasady. Dowiedz się, jak [pracować z alertami](#viewing-and-managing-alerts).

### <a name="edit-a-policy"></a>Edytowanie zasad

Możesz edytować dowolny aspekt zasad z wyjątkiem jego nazwy. Jeśli chcesz zmienić jego nazwę, musisz utworzyć nowe zasady o nowej nazwie.

Aby edytować zasady, wybierz okrągły przycisk wyświetlany po lewej stronie jego nazwy po umieszczeniu wskaźnika myszy nad jego wierszem na stronie **Zasady alertów** i wybraniu przycisku **Edytuj** u góry nad filtrami.

Nastąpi przekierowanie do kreatora tworzenia zasad, w którym można wprowadzać i zapisywać zmiany w zasadach.  Możesz również wybrać zasady, aby wyświetlić jej panel szczegółów, a następnie na przycisku **Akcje** wybierz pozycję **Edytuj zasady**. Po ponownym przejściu przez kreatora przejrzyj wybrane opcje i w ostatnim kroku wybierz pozycję **Zaktualizuj** , aby zapisać zmiany.

Wygenerowanie alertów przez zaktualizowane zasady może potrwać do 24 godzin.

### <a name="activate-or-inactivate-a-policy"></a>Aktywowanie lub inaktywowanie zasad

Zasady są aktywowane domyślnie od razu po ich utworzeniu. Gdy są aktywne, zasady utworzy alert (wyświetlany na stronie **Alerty** ), gdy warunki zostaną spełnione, i wyśle wiadomość e-mail z powiadomieniem do wyznaczonych adresatów.

Aby zmienić zasady na stan **nieaktywny** , co oznacza, że nie będzie generować alertów, wybierz okrągły przycisk wyświetlany po lewej stronie nazwy zasad po umieszczeniu wskaźnika myszy na jego wierszu. Następnie wybierz polecenie **Wyłącz** powyżej tabeli. Stan zasad będzie teraz odczytywany jako Nieaktywny. Aby ponownie uaktywnić zasady, wykonaj ten sam proces i wybierz przycisk **Aktywuj** nad filtrami.

### <a name="delete-a-policy"></a>Usuwanie zasad

Aby usunąć zasady, możesz wybrać przycisk obok jego nazwy na stronie **Zasady alertów** i wybrać pozycję **Usuń** w górnej części strony. Możesz również wybrać zasady, aby wyświetlić jej panel szczegółów, a następnie na przycisku **Akcje** wybierz pozycję **Usuń zasady**.

Usuwanie jest trwałe. Po usunięciu zasad nie będą już generować alertów ani powiadomień e-mail. Dowiedz się więcej o [alertach połączonych z usuniętymi zasadami](#when-policies-are-deleted).

## <a name="viewing-and-managing-alerts"></a>Wyświetlanie alertów i zarządzanie nimi

Na stronie **Alerty** jest wyświetlana tabela ze wszystkimi alertami generowanymi przez wszystkie zasady. Alerty są generowane niemal natychmiast po wystąpieniu zdarzenia pasującego do warunków zasad. Nazwa alertu to ta sama nazwa co zasady, które wygenerowały alert.

Alert może być generowany tylko na podstawie aktywnych zasad. Po wygenerowaniu alertu pozostaje on wyświetlany na stronie **Alerty** niezależnie od tego, czy zasady są aktywne, czy nieaktywne.

### <a name="filter-your-view-of-alerts"></a>Filtrowanie widoku alertów
Widok alertów można filtrować, wybierając polecenie **Filtr** nad tabelą na stronie **Alerty** . W okienku **Wysuwany filtr** wybierz jedną z następujących opcji filtru:

- Typ zdarzenia
- Ważności
- Stan
- Użytkownik przypisany do
- Data wykrycia
- Nazwa zasad

Po dokonaniu wybranych opcji wybierz pozycję **Zastosuj**. Okienko wysuwane zostanie zamknięte, a na zaktualizowanej stronie **Alerty zostanie wyświetlony** filtrowany widok. Filtry są wyświetlane w górnej części tabeli, ale nie wszystkie kolumny filtrów mogą być wyświetlane w tabeli.

### <a name="view-alert-details"></a>Wyświetlanie szczegółów alertu

Aby wyświetlić wszystkie szczegóły alertu, w tym zdarzenia, które go wyzwoliły, wybierz jego wiersz w tabeli. Okienko wysuwane wyświetli szczegóły alertu na karcie **Przegląd** panelu.

Karta **Dziennik zdarzeń** panelu wysuwanego zawiera listę działań, które wygenerowały alert, takich jak zmiana wyniku lub zmiana przypisania, wraz z nazwą użytkownika skojarzoną z każdą akcją i wykrytą datą.

### <a name="alert-events"></a>Zdarzenia alertu

Kolumna **Zdarzenia** na stronie **Alerty** wskazuje warunki wykrytych zasad; Innymi słowy, działanie, które wygenerowało alert. Karta **Dziennik zdarzeń** w panelu szczegółów alertu zawiera listę każdego wystąpienia zdarzenia, skojarzonego użytkownika i wykrytej daty. Poniżej wymieniono wartości zdarzeń:

- **Zmiana wyniku**: pokazuje liczbę wzrostu lub spadku liczby punktów
- **Zmiana przypisania**: akcja poprawy została przypisana do użytkownika, ponownie przypisana do innego użytkownika lub nie przypisana od użytkownika
- **Zmiana stanu implementacji**: użytkownik zmienił stan implementacji akcji poprawy
- **Zmiana stanu testu**: użytkownik zmienił stan testowania akcji poprawy.
- **Zmiana dowodów**: użytkownik przekazał lub usunął dokument dowodowy na karcie Dokumenty akcji poprawy
- **Wiele zdarzeń**: wykryto wiele wystąpień tego samego typu zdarzenia; na przykład pojedyncza akcja poprawy, która została ponownie przypisana wielokrotnie
- **Wiele warunków**: wykryto wiele warunków w ramach jednej zasady

#### <a name="alert-aggregation-for-multiple-events-within-one-minute"></a>Agregacja alertów dla wielu zdarzeń w ciągu jednej minuty

W przypadku wystąpienia wielu zdarzeń zgodnych z warunkami zasad alertów w ciągu jednej minuty są one dodawane do istniejącego alertu przez proces nazywany agregacją alertów.

Na przykład w przypadku wystąpienia jednego zdarzenia zgodnego z zasadami alert jest generowany i wyświetlany na stronie **Alerty** i wysyłane jest powiadomienie. Jeśli inne zdarzenie pasujące do tych samych zasad występuje w ciągu minuty od pierwszego zdarzenia, menedżer zgodności dodaje szczegóły dotyczące dodatkowego zdarzenia na karcie **Dziennik zdarzeń** istniejącego alertu zamiast wyzwalania nowego alertu. Celem agregacji alertów jest zmniejszenie "zmęczenia" alertów i umożliwienie skoncentrowania się na mniejszej liczbie alertów i podjęcia działań.

### <a name="taking-action-on-alerts"></a>Podejmowanie akcji w alertach

Gdy jedna z zasad generuje alert, możesz wyświetlić zdarzenia, które spowodowały alert, i określić, czy należy zweryfikować lub dokładniej zbadać zdarzenia.

Aby wykonać akcję dotyczącą alertu, wybierz jego wiersz na stronie **Alerty** , aby wyświetlić panel wysuwany ze szczegółami, wybierz przycisk **Akcje** i wybierz spośród opcji wymienionych poniżej. Możesz również wykonać akcje, wybierając okrągły przycisk wyświetlany po lewej stronie nazwy alertu po umieszczeniu wskaźnika myszy nad jego wierszem i wybierając jeden z przycisków akcji w górnej części strony powyżej filtrów.

**Przypisz alert**: możesz przypisać alert do użytkownika w celu zbadania lub zweryfikowania zdarzeń, które spowodowały alert. Po wybraniu tej opcji zostanie otwarty panel, w którym można wybrać użytkownika w organizacji i przypisać do niego alert. Widok alertów można filtrować, wybierając pozycję **Filtry** na stronie **Alerty** i wprowadzając nazwę użytkownika w polu **Przypisane do** .

**Alert e-mail**: możesz wysłać wiadomość e-mail do użytkownika skojarzonego z działaniem alertu, aby potwierdzić, że podjął akcję. Po wybraniu tej opcji zostanie otwarty szablon wiadomości e-mail z podstawowymi informacjami na temat alertu, który można dostosować za pomocą dalszych instrukcji i wysłać do użytkownika.

**Wyświetl szczegóły zasad**: możesz przejrzeć ustawienia zasad, które wyzwoliły alert. Pamiętaj, że po wybraniu tej opcji nastąpi przekierowanie bezpośrednio do strony **Zasady alertów** z otwartym panelem szczegółów zasad. Po zamknięciu panelu szczegółów zasad nie będziesz już znajdować się na stronie **Alerty** .

**Zmień stan**: możesz zaktualizować stan alertu na podstawie przeglądu jego wpływu i tego, czy wymaga on badania. Dowiedz się więcej o stanie alertów w następnej sekcji.

### <a name="alert-status"></a>Stan alertu

Po utworzeniu alertu jego stan to **Aktywny**. Podczas przeglądania szczegółów każdego alertu możesz zaktualizować jego stan do dowolnego ze stanów wymienionych poniżej:

- **Aktywne**: domyślny stan alertu do momentu zmiany jego stanu
- **Badanie**: alert jest badany
- **Rozwiązano** problem: alert nie wymaga dalszych badań ani dalszych czynności
- **Odrzucono**: alert nie jest istotny lub nie wymaga badania

Aby przypisać lub zmienić stan alertu, wybierz alert z jego wiersza w tabeli, wybierz pozycję **Zmień stan** w górnej części strony powyżej filtrów. W okienku wysuwnym Aktualizowanie stanu alertu wybierz stan z menu rozwijanego, a następnie wybierz pozycję **Aktualizuj alert**.

Po wygenerowaniu alertu jego stan jest niezależny od stanu zasad, które wygenerowały alert. Na przykład istnieje możliwość skojarzenia **aktywnego** alertu z **nieaktywnymi** zasadami i istnieje możliwość **zbadania** stanu alertu wygenerowanego przez zasady, które zostały następnie aktywowane lub usunięte.

### <a name="when-policies-are-deleted"></a>Kiedy zasady są usuwane

Po usunięciu zasad wszystkie alerty wygenerowane przez te zasady pozostaną na stronie **Alerty** , ale żadne nowe alerty nie zostaną wygenerowane.

## <a name="email-notifications-of-alerts"></a>Powiadomienia e-mail o alertach

Podczas tworzenia zasad do użytkownika, który utworzył zasady, jest wysyłana wiadomość e-mail z powiadomieniem o wykryciu dopasowania. Możesz wysłać te powiadomienia e-mail do dodatkowych użytkowników w organizacji. Alerty występują niemal w czasie rzeczywistym, a powiadomienia e-mail są wysyłane natychmiast po wygenerowaniu alertu. Wiadomość e-mail będzie zawierać nazwę zdarzenia, ważność, wykryty czas i link do wyświetlania alertu w Menedżerze zgodności.

### <a name="remove-users-from-receiving-alerts"></a>Usuwanie użytkowników z otrzymywania alertów

Jeśli wyznaczysz adresatów alertów, a następnie zdecydujesz się je usunąć, wykonaj poniższe kroki. Pamiętaj, że twórca zasad nadal będzie otrzymywać powiadomienia e-mail po wykryciu dopasowań zasad.

1. Rozpocznij kroki [edytowania zasad](#edit-a-policy).
2. Po wyświetleniu ekranu **Adresaci alertów** wybierz pozycję **+Wybierz adresatów**.
3. W panelu **wysuwanym Wybieranie adresatów** znajdź użytkownika, którego chcesz usunąć z powiadomień, i usuń zaznaczenie pola wyboru po lewej stronie jego nazwy, a następnie wybierz przycisk **Dodaj adresatów** (co skutkuje zapisaniem zaznaczenia).
4. Przejdź przez kreatora i upewnij się, że użytkownik nie jest wyświetlany w obszarze **Adresaci na stronie Przeglądanie** i zakończenie. Wybierz pozycję **Aktualizuj** , aby zapisać ustawienia i zakończyć.
