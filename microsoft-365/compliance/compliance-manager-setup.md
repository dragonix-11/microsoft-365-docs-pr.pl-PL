---
title: Wprowadzenie do Menedżera zgodności firmy Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
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
description: Ustaw uprawnienia użytkowników i role w Menedżerze zgodności firmy Microsoft oraz skonfiguruj automatyczne testowanie akcji. Zarządzaj historią użytkowników i filtruj widok pulpitu nawigacyjnego.
ms.openlocfilehash: fc7e82880cec01f7d3fd0051f75600948e51cdcc
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016076"
---
# <a name="get-started-with-compliance-manager"></a>Wprowadzenie do Menedżera zgodności

**W tym artykule:** Ten artykuł ułatwia skonfigurowanie Menedżera zgodności. Dowiedz się, jak **uzyskać dostęp do** Menedżera zgodności, **ustawić role** i uprawnienia oraz skonfigurować **automatyczne testowanie działań usprawnień**. Przechodz **przez pulpit nawigacyjny Menedżera** zgodności i poznaj strony główne: stronę akcji udoskonalania, stronę rozwiązań, stronę oceniania i stronę szablonów oceniania.

## <a name="who-can-access-compliance-manager"></a>KtoTo dostęp do Menedżera zgodności

Menedżer zgodności jest dostępny dla organizacji z licencjami usług Office 365 i Microsoft 365, a także dla klientów usług Government Community Cloud (GCC) Umiarkowane, GCC Wysoki i Dział obrony (DoD). Dostępność oceny i możliwości zarządzania zależą od umowy licencyjnej.  [Wyświetl szczegóły opisu usługi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator Microsoft 365 globalnego Twojej organizacji prawdopodobnie będzie pierwszym użytkownikiem, który uzyskuje dostęp do Menedżera zgodności. Zalecamy, aby administrator globalny zalogował się i ustawił uprawnienia użytkowników zgodnie z poniższymi instrukcjami podczas odwiedzania Menedżera zgodności po raz pierwszy.

## <a name="sign-in"></a>Logowanie się

1. Przejdź do tego <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> **i zaloguj się przy** użyciu Microsoft 365 administratora globalnego.
2. Wybierz **pozycję Menedżer zgodności w** lewym okienku nawigacji. Dotrzesz do pulpitu [nawigacyjnego Menedżera zgodności](#understand-the-compliance-manager-dashboard).

Bezpośredni link do Menedżera zgodności to [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager).

## <a name="set-user-permissions-and-assign-roles"></a>Ustawianie uprawnień użytkowników i przypisywanie ról

Menedżer zgodności używa modelu uprawnień kontroli dostępu opartej na rolach (RBAC, Role Based Access Control). Tylko użytkownicy przypisani do roli mogą uzyskać dostęp do Menedżera zgodności, a akcje dozwolone przez poszczególnych użytkowników są ograniczone według [typu roli](#role-types).

### <a name="where-to-set-permissions"></a>Gdzie ustawiać uprawnienia

Osoba pełniąca rolę administratora globalnego w organizacji może ustawić uprawnienia użytkownika dla Menedżera zgodności. Uprawnienia można ustawiać w usłudze Centrum zgodności platformy Microsoft 365 oraz w usłudze Azure Active Directory (Azure AD).

> [!NOTE]
> Klienci w Community środowiskach DoD (High) i Department of Defense (DoD) instytucji rządowych Stanów Zjednoczonych (GCC) mogą ustawiać tylko uprawnienia użytkowników i role dla Menedżera zgodności w usłudze Azure AD. Poniżej podano instrukcje usługi Azure AD i definicje typów ról.

Aby ustawić uprawnienia i przypisać role w Centrum zgodności platformy Microsoft 365, wykonaj poniższe czynności:

1. Przejdź do Centrum zgodności platformy Microsoft 365 i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a>.

2. Na liście **rozwijanej Centrum** zgodności wybierz pozycję **Role**.

3. Znajdź grupę ról, do której chcesz dodać jednego lub więcej użytkowników, i zaznacz pole wyboru po lewej stronie nazwy grupy. (Zobacz [listę ról i powiązanych funkcji poniżej](#role-types). Nazwy grup ról mają na celu naśladowanie nazwy roli).

4. W wysuwanych okienkach dla tej grupy wybierz pozycję **Edytuj** pod **nagłówkiem** Członkowie.

5. Wybierz **pozycję Wybierz członków**. Zostanie wyświetlone kolejne okno wysuwu.

6. Wybierz **pozycję + Dodaj** , aby wybrać jednego lub więcej użytkowników do dodania do grupy.

7. Zaznacz pole wyboru obok nazw, które chcesz dodać, a następnie wybierz przycisk **Dodaj** u dołu.

8. Po przypisaniu użytkowników wybierz pozycję **Gotowe, a** następnie pozycję **Zapisz**, a następnie **Zamknij**.

#### <a name="more-about-azure-ad"></a>Więcej informacji o usłudze Azure AD

Aby przypisać role i ustawić uprawnienia w usłudze Azure AD, zobacz [Przypisywanie ról administratora](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal) i innych administratorów użytkownikom, którzy mają Azure Active Directory.

Użytkownicy korzystający z tożsamości usługi Azure AD, którzy nie mają Office 365 subskrypcji usługi Microsoft 365, nie będą mogli uzyskać dostępu do Menedżera zgodności w Centrum zgodności platformy Microsoft 365. Aby uzyskać pomoc w uzyskiwaniu dostępu do Menedżera zgodności, skontaktuj się z [cmresearch@microsoft.com](mailto:cmresearch@microsoft.com).

### <a name="role-types"></a>Typy ról

W poniższej tabeli przedstawiono funkcje dozwolone przez poszczególne role w Menedżerze zgodności. W tabeli pokazano również, jak [poszczególne role w usłudze Azure AD są mapowanie](/azure/active-directory/roles/permissions-reference) na role Menedżera zgodności. Użytkownicy muszą mieć co najmniej rolę czytnika Menedżera zgodności lub globalną rolę czytnika usługi Azure AD, aby uzyskać dostęp do Menedżera zgodności.

| Użytkownik może: | Rola Menedżera zgodności | Rola usługi Azure AD | 
| :------------- | :-------------: | :------------: |
| **Odczytywanie danych, ale bez ich edytowania**| Czytnik Menedżera zgodności  | Czytnik globalny usługi Azure AD, czytnik zabezpieczeń |
| **Edytowanie danych**| Udział menedżera zgodności | Administrator zgodności |
| **Edytowanie wyników testu**| Ocenianie menedżera zgodności | Administrator zgodności |
| **Zarządzanie ocenami oraz danymi szablonów i dzierżaw**| Administracja Menedżera zgodności | Administrator zgodności, administrator danych zgodności, administrator zabezpieczeń  |
| **Przypisz użytkowników**| Administrator globalny | Administrator globalny |

## <a name="start-a-premium-assessments-trial"></a>Rozpocznij wersję próbną testów premium

Wersja próbna testów premium w menedżerze zgodności to doskonały sposób na szybkie konfigurowanie testów najbardziej istotnych dla twojej organizacji. Nasza biblioteka ponad 300 szablonów odpowiada ustawom rządowych i standardom branżowym na całym świecie.
Dowiedz się więcej o wersji [próbnej testów premium](compliance-easy-trials-compliance-manager-assessments.md).

Możesz rozpocząć wersję próbną bezpośrednio w Menedżerze zgodności i skonfigurować zalecane oceny, korzystając z następujących kroków:

1. Na stronie Menedżer zgodności **— omówienie** wybierz pozycję **Rozpocznij wersję próbną**. Należy wprowadzić kreatora aktywacji próbnej, który zadawaj pytania w celu polecania testów dla Twojej organizacji.

2. Na stronie **Aktywowanie wersji próbnej** wybierz pozycję **Dalej** , aby rozpocząć bezpłatną 90-dniową wersję próbną premium testów i kontynuować tworzenie testów.

3. Wybierz co najmniej jeden branżę identyfikującą Twoją organizację, a następnie wybierz pozycję **Dalej**.

4. Wybierz co najmniej jeden region dla lokalizacji organizacji, a następnie wybierz pozycję **Dalej**.

5. Na **ekranie Wybierz testy** wybierz strzałkę listy rozwijanej obok pozycji Polecane **szablony** , aby wyświetlić listę oceniań, które są według nas stosowane w Twojej organizacji. Zaznacz pola wyboru obok szablonów, których chcesz użyć do tworzenia formularzy oceniania, a następnie wybierz pozycję **Dalej**.

6. Przejrzyj wybrane ostatnie testy i wybierz **pozycję Dodaj zalecane oceny** , aby utworzyć nowe testy.

Dowiedz się więcej na temat rozpoczynania pracy z ocenami, odwiedzając sekcję strony [Assessments (Testy)](#assessments-page) poniżej.

## <a name="settings-for-automated-testing-and-user-history"></a>Ustawienia do automatycznego testowania i historii użytkowników

Ustawienia Menedżera zgodności w Centrum zgodności platformy Microsoft 365 umożliwiają włączanie i wyłączanie automatycznego testowania działań udoskonalania. Te ustawienia umożliwiają również zarządzanie danymi użytkowników skojarzonymi z działaniami udoskonalania, łącznie z możliwością ponownego przypisania akcji udoskonalania do innego użytkownika.  Tylko osoby z rolą administratora globalnego lub administratora menedżera zgodności mogą uzyskać dostęp do ustawień Menedżera zgodności.

> [!NOTE]
> Funkcja automatycznego testowania nie jest dostępna dla klientów w środowiskach GCC i DoD, ponieważ w tych środowiskach bezpieczny wynik nie jest dostępny. GCC high and dod klienci będą musieli ręcznie zaimplementować i przetestować swoje działania udoskonalania.

### <a name="set-up-automated-testing"></a>Konfigurowanie testowania automatycznego

Niektóre działania udoskonalania w Menedżerze zgodności są również monitorowane przez program [Microsoft Secure Score](../security/defender/microsoft-secure-score.md). Możesz skonfigurować zautomatyzowane testowanie akcji, które są monitorowane wspólnie, co oznacza, że wyniki te są synchronizowane z tymi samymi działaniami w Menedżerze zgodności w przypadku przetestowania i zaktualizowania akcji w wynikach bezpiecznego działania i są liczone w wyniku oceny zgodności.

Automatyczne testowanie jest domyślnie włączone dla organizacji, które nie mają menedżera zgodności. Gdy wdrażasz po raz pierwszy Microsoft 365 lub Office 365, pełne zbieranie danych i uwzględnianie ich w wyniku zgodności trwa około siedmiu dni.  Gdy jest włączone automatyczne testowanie, data testu akcji nie zostanie zaktualizowana, ale jej stan zostanie zaktualizowany. Podczas tworzenia nowych ocen wyniki są automatycznie dołączane do wyników kontroli firmy Microsoft i integracji bezpiecznego wyniku.

Administrator globalny Twojej organizacji może w dowolnej chwili zmienić ustawienia do testowania automatycznego. Możesz wyłączyć automatyczne testowanie typowych akcji udoskonalania lub włączyć je dla poszczególnych akcji. Wykonaj poniższe instrukcje, aby zmienić ustawienia testowania automatycznego.

#### <a name="to-manage-your-automated-testing-settings"></a>Aby zarządzać ustawieniami testowania automatycznego:

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> w Centrum zgodności platformy Microsoft 365.

2. Na stronie ustawienia wybierz pozycję **Menedżer zgodności**.

3. Wybierz **pozycję Automatyczne testowanie** w lewym okienku nawigacji.

4. Wybierz przycisk, który ma zastosowanie, aby włączyć automatyczne testowanie dla wszystkich działań udoskonalania, wyłączyć je dla wszystkich akcji lub włączyć według indywidualnej akcji.

5. Jeśli wybierzesz **opcję Włącz dla akcji udoskonalania**, na liście będą wyświetlane wszystkie dostępne działania udoskonaleń do wyboru.  Zaznacz pole wyboru obok akcji, która ma być sprawdzana automatycznie.

6. Wybierz **pozycję Zapisz** , aby zapisać ustawienia. U góry ekranu zostanie wyświetlony komunikat potwierdzający, że wybór został zapisany. Jeśli otrzymasz powiadomienie o niepowodzeniu, spróbuj ponownie.

**Uwaga:** Tylko administrator globalny może włączać i wyłączać aktualizacje automatyczne dla wszystkich akcji. Administrator Menedżera zgodności może włączyć automatyczne aktualizacje dla poszczególnych akcji, ale nie dla wszystkich działań globalnie.

### <a name="manage-user-history"></a>Zarządzanie historią użytkowników

Ustawienia **Zarządzaj historią użytkowników** ułatwiają szybkie identyfikowanie użytkowników, którzy współpracowali z działaniami udoskonalania w Menedżerze zgodności. Możliwe do zidentyfikowania dane użytkowników związane z działaniami udoskonalania obejmują wykonywanie wszelkich działań implementacji i testów, przekazanych dokumentów i wszelkich wprowadzonych notatek. Zrozumienie i pobieranie danych tego typu może być konieczne dla potrzeb Twojej organizacji do zachowania zgodności z przepisami.

Ustawienia historii użytkowników umożliwiają również ponowne przypisanie wszystkich akcji udoskonalania dla jednego użytkownika do drugiego.

**Aby znaleźć ustawienia historii użytkowników:**

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> w Centrum zgodności platformy Microsoft 365.

2. Na stronie ustawienia wybierz pozycję **Menedżer zgodności**.

3. Wybierz **pozycję Zarządzaj historią użytkowników w** lewym okienku nawigacji.

Na **stronie zarządzanie historią** użytkowników jest wyświetlona lista wszystkich użytkowników według adresów e-mail przypisanych do działania usprawniacego. Użyj **przycisku Wyszukaj** , aby szybko znaleźć określonego użytkownika, wpisując jego adres e-mail.

Po prawej stronie adresów e-mail poszczególnych użytkowników menu rozwijane Wybierz  zawiera opcje eksportowania raportu, ponownego przypisania akcji udoskonalania i usuwania historii. Szczegółowe informacje na temat poszczególnych opcji można znaleźć w poszczególnych sekcjach poniżej.

#### <a name="export-a-report-of-user-history-data"></a>Eksportowanie raportu z danych historii użytkowników

Możesz wyeksportować plik Excel zawierający listę akcji udoskonalania obecnie przypisanych do użytkownika.  Raport zawiera również wszelkie pliki dowodów przekazane przez tego użytkownika. Te informacje mogą ułatwić ponowne przypisanie otwartych działań udoskonalania.

Raport odzwierciedla stan akcji udoskonalania od daty jego utworzenia. Nie jest to raport historyczny ze wszystkimi wcześniejszymi zmianami stanu lub przydziału (dowiedz się, jak wyeksportować raport ze [strony akcji udoskonalania](compliance-manager-improvement-actions.md#export-a-report)).

**Wykonaj poniższe czynności, aby wyeksportować raport według użytkownika:**

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> w Centrum zgodności platformy Microsoft 365.

2. Na stronie ustawienia wybierz pozycję **Menedżer zgodności**.

3. Wybierz **pozycję Zarządzaj historią użytkowników w** okienku nawigacji po lewej stronie.

4. Znajdź odpowiedniego użytkownika, przeszukując listę adresów e-mail lub wybierając pozycję **Wyszukaj** i wprowadzając adres e-mail użytkownika.

5. Z menu **rozwijanego** Wybierz wybierz pozycję **Eksportuj raport**.

6. Po Excel pliku raportu możesz go otworzyć i zapisać na komputerze lokalnym.

#### <a name="reassign-improvement-actions-to-another-user"></a>Ponowne przypisanie akcji udoskonalania do innego użytkownika

Możesz ponownie zmienić przypisanie akcji udoskonalania dla jednego użytkownika do innego. Ponowne przypisanie akcji nie zmienia się w historii przekazywania dokumentu, ale nazwa użytkownika, który pierwotnie przesłał dokumentację, nie jest już wyświetlana w ramach akcji udoskonalania.

**Wykonaj poniższe czynności, aby ponownie przypisać akcje udoskonalania do innego użytkownika:**

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> w Centrum zgodności platformy Microsoft 365.

2. Na stronie ustawienia wybierz pozycję **Menedżer zgodności**.

3. Wybierz **pozycję Zarządzaj historią użytkowników w** okienku nawigacji po lewej stronie.

4. Znajdź użytkownika, przeszukując listę adresów e-mail lub wybierając pozycję **Wyszukaj** i wprowadzając adres e-mail tego użytkownika.

5. Z menu **rozwijanego** Wybierz wybierz pozycję **Ponownie przysyłaj akcje udoskonalania**. Zostanie **wyświetlone okienko wysuwu akcji** udoskonalania Ponownie przypisanie.

6. W **polu Wyszukaj użytkowników** wprowadź nazwę lub adres e-mail użytkownika, do którego chcesz przypisać akcje *udoskonalania*.

7. Gdy w obszarze Akcje udoskonalania zostanie przypisana nazwa zamierzonego **użytkownika, wybierz** użytkownika, a następnie wybierz pozycję **Przypisz akcje**.

8. Po zakończeniu ponownego przypisania w okienku wysuwanych pojawi się komunikat z potwierdzeniem informujący, że wszystkie akcje udoskonalania ze strony poprzedniego użytkownika zostały ponownie przypisane do nowego użytkownika. Jeśli otrzymasz powiadomienie o niepowodzeniu ponownego przypisania, zamknij okno i spróbuj ponownie. Aby zamknąć okienko wysuwu, wybierz pozycję **Gotowe**.

Nowy zadedytowany otrzymuje wiadomość e-mail, która została jej przydzielona do działania usprawnień. Wiadomość e-mail zawiera bezpośredni link do strony szczegółów akcji udoskonalania.

 > [!NOTE]
> Jeśli ponownie przypisano akcję, która ma oczekującą aktualizację, bezpośredni link do akcji w wiadomości e-mail dotyczącej ponownego przypisania zostanie zerwany, jeśli aktualizacja zostanie zaakceptowana po ponownej aktualizacji. Ten problem można rozwiązać, ponownie przypisując akcję do użytkownika po zaakceptowaniu aktualizacji. Dowiedz się więcej [o aktualizacjach w zakresie działań udoskonalania](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

#### <a name="delete-user-history"></a>Usuwanie historii użytkowników

Usunięcie historii użytkownika spowoduje usunięcie go jako właściciela akcji udoskonalania i usunięcie jego nazwy ze wszystkich pozostałych pól w Menedżerze zgodności. Po usunięciu historii użytkownika akcje udoskonalania, których jest on właścicielem, nie będą wyświetlać wartości **Przypisane** do, dopóki nowy użytkownik nie zostanie przypisany. W przypadku wszystkich dokumentów przekazanych do działania udoskonalania w miejscu nazwy usuniętego użytkownika będzie pokazywana informacja Usunięto użytkownika. Usuwanie historii użytkowników jest trwałe.

Aby usunąć historię użytkownika, wykonaj poniższe czynności:

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> w Centrum zgodności platformy Microsoft 365.

2. Na stronie ustawienia wybierz pozycję **Menedżer zgodności**.

3. Wybierz **pozycję Zarządzaj historią użytkowników w** okienku nawigacji po lewej stronie.

4. Znajdź użytkownika, przeszukując listę adresów e-mail lub wybierając pozycję **Wyszukaj** i wprowadzając adres e-mail tego użytkownika.

5. Z menu **rozwijanego** Wybierz wybierz polecenie **Usuń historię**.

6. Zostanie wyświetlone okno z prośbą o potwierdzenie trwałego usunięcia historii użytkownika. Aby kontynuować usuwanie, wybierz **pozycję Usuń historię**. Aby opuścić bez usuwania historii, wybierz pozycję **Anuluj**.

7. Wrócisz do strony Zarządzanie historią  użytkowników z komunikatem potwierdzającym u góry, że historia użytkownika została usunięta.

## <a name="understand-the-compliance-manager-dashboard"></a>Opis pulpitu nawigacyjnego Menedżera zgodności

Pulpit nawigacyjny Menedżera zgodności został zaprojektowany tak, aby zapewnić Ci szybki podgląd bieżącej sytuacji dotyczącej zgodności.

:::image type="content" alt-text="Menedżer zgodności — pulpit nawigacyjny." source="../media/compliance-manager-dashboard.png" lightbox="../media/compliance-manager-dashboard.png":::

### <a name="overall-compliance-score"></a>Ogólna ocena zgodności

Twój wynik zgodności jest wyróżniony na górze. Przedstawia on wartość procentową na podstawie punktów, które można uzyskać za ukończenie działań udoskonalania, które są związane z kluczowymi normami i przepisami dotyczącymi ochrony danych. Punkty z [akcji firmy Microsoft](compliance-manager-assessments.md#microsoft-actions-tab), którymi zarządza firma Microsoft, także liczą się w wyniku w zakresie zgodności.

W Przypadku Menedżera zgodności po raz pierwszy Twój początkowy wynik jest oparty na planie bazowym Microsoft 365 [ochrony danych](compliance-manager-assessments.md#data-protection-baseline-default-assessment). Ta ocena podstawowa, dostępna dla wszystkich organizacji, to zestaw kontrolek, który zawiera typowe przepisy branżowe i standardy. Menedżer zgodności skanuje istniejące Microsoft 365 i udostępnia wstępną ocenę na podstawie bieżących ustawień prywatności i zabezpieczeń. W przypadku dodawania ocen odpowiednich dla organizacji twój wynik staje się bardziej zrozumiały.

**Dowiedz się więcej:** [Zrozumienie sposobu obliczania wyniku zgodności](compliance-score-calculation.md).

### <a name="key-improvement-actions"></a>Kluczowe działania udoskonalania

W tej sekcji wymieniono najważniejsze działania ulepszeń, które można obecnie podjąć, aby uzyskać największy pozytywny wpływ na ogólny wynik zgodności. Wybierz **pozycję Wyświetl wszystkie akcje udoskonalania** , aby przejść do strony akcji udoskonalania.

### <a name="solutions-that-affect-your-score"></a>Rozwiązania wpływające na wynik

W tej sekcji wyróżnione są rozwiązania zawierające działania usprawniające, które mogą mieć pozytywny wpływ na wynik, oraz liczbę zaległych działań udoskonalania w tych rozwiązaniach. Wybierz **pozycję Wyświetl wszystkie rozwiązania,** aby odwiedzić stronę swoich rozwiązań.

### <a name="compliance-score-breakdown"></a>Podział wyników zgodności

W tej sekcji można uzyskać bardziej szczegółowy widok wyników na dwa różne sposoby:

- **Kategorie**: przedstawia procent ogólnego wyniku w kategoriach ochrony danych, na przykład "ochrona informacji" lub "zarządzanie urządzeniami".
- **Testy**: przedstawia procent twojego postępu w zarządzaniu ocenami poszczególnych standardów zgodności i ochrony danych, przepisów lub ustaw, takich jak RODO lub NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrowanie widoku pulpitu nawigacyjnego

Widok pulpitu nawigacyjnego można filtrować, aby wyświetlić tylko elementy związane z określonymi przepisami i standardami, rozwiązaniami, typem akcji, grupami oceniania lub kategoriami ochrony danych. Filtrowanie widoku w ten sposób spowoduje również przefiltrowanie wyników na pulpicie nawigacyjnym, pokazujących, ile punktów udało Ci się uzyskać w sumie możliwych punktów na podstawie kryteriów filtru.

Aby zastosować filtry:

1. Wybierz **pozycję** Filtruj w prawym górnym rogu pulpitu nawigacyjnego.
2. Wybierz kryteria filtru w **wysuwanych okienku** Filtry, a następnie wybierz pozycję **Zastosuj**.

Po zastosowaniu filtru wyniki będą dostosowywane w czasie rzeczywistym. Wartość procentowa wyników zgodności i informacje dotyczące podziału, a także działania i rozwiązania ulepszeń, teraz odnoszą się tylko do danych objętych kryteriami filtrowania. Jeśli wylogujesz się z Menedżera zgodności, filtrowany widok pozostanie po zalogowaniu się ponownie.

Aby usunąć filtry:

- W **nagłówku Zastosowane filtry** powyżej wyniku zgodności wybierz **znak X** obok pojedynczego filtru, który chcesz usunąć. lub
- Wybierz **pozycję** Filtruj w prawym górnym rogu pulpitu nawigacyjnego, a następnie w **wysuwanych** okienku Filtry wybierz pozycję **Wyczyść filtry**.

## <a name="improvement-actions-page"></a>Strona Akcje udoskonalania

[Działania udoskonalania](compliance-manager-improvement-actions.md) to akcje zarządzane przez Twoją organizację. Praca z działaniami udoskonalania ułatwia scentralizowanie działań dotyczących zgodności z przepisami i standardami ochrony danych. Każde działanie udoskonalania zawiera szczegółowe wskazówki implementacji oraz link do wprowadzenia Cię do odpowiedniego rozwiązania. Użytkownikom w Twojej organizacji można przypisywać akcje udoskonalania w celu wykonania pracy implementacji i testowania. W ramach działania udoskonalania możesz również przechowywać dokumentację, notatki i aktualizacje stanu rekordów.

### <a name="view-your-improvement-actions"></a>Wyświetlanie działań udoskonalania

Pulpit nawigacyjny Menedżer zgodności pokazuje **kluczowe działania ulepszeń.** Aby wyświetlić wszystkie działania ulepszeń, wybierz kartę Akcje udoskonalania na pulpicie nawigacyjnym, która prowadzi do strony akcji udoskonalania. Możesz również wybrać pozycję Wyświetl wszystkie akcje udoskonalania poniżej listy kluczowych akcji udoskonalania na pulpicie nawigacyjnym, aby przejść do strony akcji udoskonalania.

Strona działań udoskonalania zawiera wszystkie akcje udoskonalania, które są zarządzane przez Twoją organizację. Akcje zarządzane przez firmę Microsoft mogą być przeglądane w ramach każdej oceny (dowiedz się więcej o działaniach [firmy Microsoft](compliance-manager-assessments.md#microsoft-actions-tab)).

Jeśli na stronie akcji udoskonalania jest długa lista działań, pomocne może okazać się przefiltrenie widoku. Wybierz **pozycję** Filtruj w prawym górnym rogu listy akcji. Gdy zostanie **wyświetlone okienko** wysuwu Filtry, wybierz kryteria na podstawie przepisów i standardów, rozwiązania i grupy. Możesz także dostosować widok, wybierając pozycję **Grupuj** w prawym górnym rogu. Z menu rozwijanego wybierz pozycję , aby wyświetlić według grupy, rozwiązania, kategorii, typu akcji lub stanu.

W widoku domyślnym dla tej strony nie są pokazywane akcje udoskonalania ze stanem testowym **"Passed"**. Aby wyświetlić akcje, które zostały już przetestowane, zaznacz pole **Pomyślnie w** okienku wysuwany Filtry. Tylko akcje ze stanem testowym **"Pomyślnie** " liczą się w stosunku do wyniku. Niektóre akcje mogą zawierać **etykietę oczekującej aktualizacji.** Dowiedz się więcej [o aktualizacjach w zakresie działań udoskonalania](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

Na stronie działania udoskonalania są shows the following data points for each improvement action:

- **Punkty udało** się uzyskać: liczba punktów zdobytych w sumie dzięki ukończeniu akcji
- **Przepisy**: przepisy lub standardy dotyczące akcji
- **Grupa**: grupa, do której przypisano akcję
- **Rozwiązania**: rozwiązanie, które umożliwia wykonanie akcji
- **Assessments**: the assessments that contain the action
- **Kategorie**: powiązana kategoria ochrony danych (na przykład ochrona informacji, zarządzanie urządzeniami itp.).
- **Stan testu**:
    - **Brak** — nie jest rejestrowana żadna aktualizacja stanu
    - **Nie oceniono —** testowanie nie zostało rozpoczęte
    - **Pomyślnie ukończono** — pomyślnie przetestowano implementację
    - **Niskie ryzyko,** których testowanie zakończyło się niepowodzeniem, niskie ryzyko
    - **Średnie ryzyko niepowodzenie —** testowanie zakończyło się niepowodzeniem, średnie ryzyko
    - **Wysokie ryzyko, których** testowanie zakończyło się niepowodzeniem, wysokie ryzyko
    - **Poza zakresem** — działanie nie ma zastosowania do oceny i nie ma wpływu na wynik
    - **Do wykrycia —** w przypadku testu ręcznego wskazuje, że akcja została zaimplementowana, ale nie została przetestowana; oznacza, że akcja oczekuje na wynik automatyzacji.
    - **Nie można wykryć** — nie można ustalić stanu automatycznego
    - **Częściowo sprawdzone —** zautomatyzowane zdobywanie punktów, które zdobyły nagrody częściowe

**Dowiedz się więcej:** [Zobacz, jak przypisywać i wykonywać pracę nad działaniami udoskonalania](compliance-manager-improvement-actions.md).

## <a name="solutions-page"></a>Strona Rozwiązania

Strona rozwiązań przedstawia udział zdobytych i potencjalnych punktów w zdobytych przez rozwiązanie. Wyświetlanie pozostałych punktów i działań udoskonalania w tym widoku pomaga zrozumieć, które rozwiązania wymagają natychmiastowej uwagi.

Znajdź stronę rozwiązań, wybierając **kartę Rozwiązania** na pulpicie nawigacyjnym Menedżera zgodności. Możesz również wybrać pozycję **Wyświetl wszystkie rozwiązania poniżej** **Opcji, które wpływają** na wynik w prawej górnej części pulpitu nawigacyjnego.

### <a name="filtering-your-solutions-view"></a>Filtrowanie widoku rozwiązań

Aby przefiltrować widok rozwiązań:

1. Wybierz **pozycję** Filtruj w lewym górnym rogu listy oceniań.
2. W **wysuwanych** okienku Filtry umieść pole wyboru obok odpowiednich kryteriów (standardów i przepisów, rozwiązania, typu akcji, grupy Menedżer zgodności, kategoria).
3. Wybierz przycisk **Zastosuj** . Okienko filtru zostanie zamknięte i zostanie wyświetlony widok filtrowany.

Możesz także zmodyfikować widok, aby wyświetlić oceny według grupy, produktu lub przepisów, wybierając typ grupowania z menu rozwijanego Grupa  powyżej listy oceniań.

### <a name="taking-action-from-the-solution-page"></a>Podejmowanie działań na stronie rozwiązania

Na stronie rozwiązań są wyświetlane rozwiązania Twojej organizacji, które są połączone z działaniami udoskonalania. W tabeli wymieniono udział poszczególnych rozwiązań w ogólnym wyniku, punkty osiągane i możliwe w ramach tego rozwiązania oraz pozostałą liczbę pogrupowanych w tym rozwiązaniu akcji udoskonalania, które mogą zwiększyć wynik.

Istnieją dwa sposoby działania, które możesz podjąć na tym ekranie:

1. W wierszu zamierzonego rozwiązania w kolumnie **Pozostałe** akcje zaznacz numer hiperlinku. Zostanie wyświetlony przefiltrowany widok akcji udoskonalania przedstawiający niestestowane działania ulepszeń dla tego rozwiązania.

2. W wierszu zamierzonego rozwiązania w kolumnie **Otwórz rozwiązanie** wybierz pozycję **Otwórz**. Rozwiązanie lub lokalizację znajdziesz w centrum zabezpieczeń Microsoft 365 i Office 365, w których możesz podjąć zalecane działanie.

## <a name="assessments-page"></a>Strona Assessments (Testy)

Strona assessments (Testy [) zawiera listę](compliance-manager-assessments.md) wszystkich ocen ustawionych dla organizacji. Twój mianownik wyników zgodności jest ustalany na podstawie wszystkich śledzowanych ocen. Po dodaniu kolejnych ocen na stronie akcji udoskonalania zobaczysz więcej akcji udoskonalania, a twój mianownik wyników zgodności zwiększa się.

Licznik **aktywowanych szablonów** u góry strony pokazuje liczbę aktywnych szablonów oceniania, które są obecnie w użyciu, spośród łącznej liczby szablonów dostępnych do użycia w Organizacji. Aby [uzyskać więcej informacji, zobacz Dostępność szablonu i](compliance-manager-templates.md#template-availability-and-licensing) licencjonowanie.

Strona assessments (Testy) zawiera podsumowanie kluczowych informacji dotyczących poszczególnych ocen:

- **Ocena**: nazwa oceny
- **Stan**:
  - **Ukończone** — wszystkie kontrolki mają stan "zakończone pomyślnie" lub co najmniej jedna z nich jest przekazywana, a pozostałe są "poza zakresem"
  - **Nieukończone** — co najmniej jedna kontrolka ma stan "niepowodzenie"
  - **Brak** — nie wszystkie kontrolki nie zostały przetestowane
  - **W toku** — działania udoskonalania mają inny stan, w tym "w toku", "kredyt częściowy" lub "niezauwa że
- **Postęp oceny**: procent pracy wykonanej w kierunku ukończenia, mierzony przez liczbę pomyślnie przetestowanych kontrolek
- **Twoje działania udoskonalania**: liczba ukończonych akcji, które spełniają implementację Twoich kontrolek
- **Akcje firmy Microsoft**: liczba ukończonych akcji, które spełniają implementację kontrolek firmy Microsoft
- **Grupa**: nazwa grupy, do której należy ocena
- **Produkt**: skojarzony produkt, taki jak Microsoft 365 lub inny produkt zdefiniowany do oceny
- **Przepisy**: standard, zasady lub prawo prawne dotyczące oceny

### <a name="filtering-your-assessments-view"></a>Filtrowanie widoku oceny

Aby przefiltrować widok ocen:

1. Wybierz **pozycję** Filtruj w lewym górnym rogu listy oceniań.
2. W **okienku** wysuwany Filtry zaznacz odpowiednie kryteria.
3. Wybierz przycisk **Zastosuj** . Okienko filtru zostanie zamknięte i zostanie wyświetlony widok filtrowany.

Możesz także zmodyfikować widok, aby wyświetlić oceny według grupy, produktu lub przepisów, wybierając typ grupowania z menu rozwijanego Grupa  powyżej listy oceniań.

### <a name="default-assessment"></a>Ocena domyślna

Domyślnie na stronie oceny będzie wyświetlony widok [Ocena planu bazowego ochrony](compliance-manager-assessments.md#data-protection-baseline-default-assessment) danych. Menedżer zgodności udostępnia również kilka wstępnie wbudowanych [szablonów](compliance-manager-templates-list.md) do tworzenia formularzy oceniania.

## <a name="assessment-templates-page"></a>Strona szablonów oceniania

Szablon to wzór tworzenia oceny w Menedżerze zgodności. Na stronie szablony oceniania jest wyświetlana lista szablonów i kluczowych szczegółów. Ta lista zawiera szablony udostępniane przez Menedżera zgodności, a także wszelkie szablony, które zostały zmodyfikowane lub utworzone przez organizację. Możesz zastosować filtry, aby znaleźć szablon na podstawie certyfikacji, zakresu produktu, kraju, branży i tego, kto go utworzył.

Licznik **aktywowanych szablonów** u góry strony pokazuje liczbę aktywnych szablonów oceniania, które są obecnie w użyciu, spośród łącznej liczby szablonów dostępnych do użycia w Organizacji. Aby [uzyskać więcej informacji, zobacz Dostępność szablonu i](compliance-manager-templates.md#template-availability-and-licensing) licencjonowanie.

Wybierz szablon z jego wiersza, aby uzyskać stronę szczegółów z opisem szablonu i  dalszymi informacjami na temat certyfikacji, zakresu i kontrolek. Na tej stronie możesz wybrać odpowiednie przyciski, aby utworzyć ocenę, wyeksportować dane szablonu Excel lub zmodyfikować szablon.

**Dowiedz się więcej:** [Przeczytaj, jak pracować z szablonami oceniania](compliance-manager-templates.md).

## <a name="next-step"></a>Następny krok

Dostosuj Menedżera zgodności, [ustawiając oceny](compliance-manager-assessments.md).
