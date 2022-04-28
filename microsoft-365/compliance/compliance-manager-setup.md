---
title: Wprowadzenie za pomocą programu Microsoft Purview Compliance Manager
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
description: Ustaw uprawnienia i role użytkownika programu Microsoft Purview Compliance Manager oraz skonfiguruj automatyczne testowanie akcji. Zarządzanie historią użytkowników i filtrowanie widoku pulpitu nawigacyjnego.
ms.openlocfilehash: c7920a9eac06128f3cf9bfb54645a83296ca7e53
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091032"
---
# <a name="get-started-with-compliance-manager"></a>Wprowadzenie do Menedżera zgodności

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**W tym artykule:** Ten artykuł ułatwia skonfigurowanie Menedżera zgodności. Dowiedz się, jak **uzyskać dostęp** do Menedżera zgodności, **ustawić role i uprawnienia oraz** skonfigurować **automatyczne testowanie akcji poprawy**. Zapoznaj **się z pulpitem nawigacyjnym programu Compliance Manager** i zapoznaj się ze stronami głównymi: stroną akcji poprawy, stroną rozwiązań, stroną ocen i stroną szablonów oceny.

## <a name="who-can-access-compliance-manager"></a>KtoTo może uzyskać dostęp do Menedżera zgodności

Menedżer zgodności jest dostępny dla organizacji z licencjami Office 365 i Microsoft 365 oraz dla klientów us Government Community Cloud (GCC) Moderate, GCC High i Department of Defense (DoD). Dostępność oceny i możliwości zarządzania zależą od umowy licencyjnej.  [Wyświetl szczegóły opisu usługi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny Microsoft 365 w twojej organizacji będzie prawdopodobnie pierwszym użytkownikiem, który uzyska dostęp do Menedżera zgodności. Zalecamy zalogowanie się administratora globalnego i ustawienie uprawnień użytkownika zgodnie z poniższym opisem podczas pierwszego wizyty w Menedżerze zgodności.

## <a name="sign-in"></a>Logowanie się

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności usługi Microsoft Purview</a> i **zaloguj się** przy użyciu konta administratora globalnego Microsoft 365.
2. Wybierz pozycję **Menedżer zgodności** w okienku nawigacji po lewej stronie. Zostanie wyświetlony [pulpit nawigacyjny programu Compliance Manager](#understand-the-compliance-manager-dashboard).

Bezpośredni link umożliwiający dostęp do Menedżera zgodności to [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager).

## <a name="set-user-permissions-and-assign-roles"></a>Ustawianie uprawnień użytkownika i przypisywanie ról

Menedżer zgodności używa modelu uprawnień kontroli dostępu opartej na rolach (RBAC). Tylko użytkownicy, którzy mają przypisaną rolę, mogą uzyskiwać dostęp do Menedżera zgodności, a akcje dozwolone przez każdego użytkownika są ograniczone przez [typ roli](#role-types).

### <a name="where-to-set-permissions"></a>Gdzie ustawić uprawnienia

Osoba pełniąca rolę administratora globalnego w organizacji może ustawić uprawnienia użytkownika dla Menedżera zgodności. Uprawnienia można ustawić w portalu zgodności usługi Microsoft Purview, a także w Azure Active Directory (Azure AD).

> [!NOTE]
> Klienci w środowiskach Us Government Community (GCC) High i Department of Defense (DoD) mogą ustawiać uprawnienia i role użytkowników tylko dla Menedżera zgodności w usłudze Azure AD. Zobacz poniżej, aby uzyskać instrukcje usługi Azure AD i definicje typów ról.

Aby ustawić uprawnienia i przypisać role w portalu zgodności usługi Microsoft Purview, wykonaj poniższe kroki:

1. Przejdź do portalu zgodności usługi Microsoft Purview i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a>.

2. Na liście rozwijanej portalu zgodności wybierz pozycję **Role**.

3. Znajdź grupę ról, do której chcesz dodać co najmniej jednego użytkownika, i zaznacz pole wyboru po lewej stronie nazwy grupy. (Zobacz [listę ról i powiązanych funkcji poniżej](#role-types). Nazwy grup ról naśladują nazwę roli).

4. W okienku wysuwanym dla tej grupy wybierz pozycję **Edytuj** w nagłówku **Członkowie** .

5. Wybierz pozycję **Wybierz członków**. Zostanie wyświetlone kolejne okno wysuwane.

6. Wybierz pozycję **+ Dodaj** , aby wybrać co najmniej jednego użytkownika do dodania do grupy.

7. Zaznacz pole wyboru obok nazw, które chcesz dodać, a następnie wybierz przycisk **Dodaj** u dołu.

8. Po zakończeniu przypisywania użytkowników wybierz pozycję **Gotowe**, a następnie wybierz pozycję **Zapisz**, a następnie **zamknij**.

#### <a name="more-about-azure-ad"></a>Więcej informacji o usłudze Azure AD

Aby przypisać role i ustawić uprawnienia w usłudze Azure AD, zobacz [Przypisywanie ról administratora i nieadministratora do użytkowników z Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

Użytkownicy z tożsamościami usługi Azure AD, którzy nie mają subskrypcji Office 365 lub Microsoft 365, nie będą mogli uzyskać dostępu do Menedżera zgodności w portalu zgodności usługi Microsoft Purview. Aby uzyskać pomoc dotyczącą uzyskiwania dostępu do Menedżera zgodności, skontaktuj się z [cmresearch@microsoft.com](mailto:cmresearch@microsoft.com).

### <a name="role-types"></a>Typy ról

W poniższej tabeli przedstawiono funkcje dozwolone przez każdą rolę w Menedżerze zgodności. W tabeli przedstawiono również sposób mapowania poszczególnych [ról usługi Azure AD](/azure/active-directory/roles/permissions-reference) na role Menedżera zgodności. Aby uzyskać dostęp do Menedżera zgodności, użytkownicy będą potrzebować co najmniej roli czytelnika programu Compliance Manager lub globalnej roli czytelnika usługi Azure AD.

| Użytkownik może: | Rola Menedżera zgodności | Rola usługi Azure AD | 
| :------------- | :-------------: | :------------: |
| **Odczytywanie, ale nie edytowanie danych**| Czytelnik programu Compliance Manager  | Czytelnik globalny usługi Azure AD, czytelnik zabezpieczeń |
| **Edytowanie danych**| Wkład menedżera zgodności | Administrator zgodności |
| **Edytowanie wyników testu**| Asesor menedżera zgodności | Administrator zgodności |
| **Zarządzanie ocenami oraz danymi szablonu i dzierżawy**| Administracja programu Compliance Manager | Administrator zgodności, administrator danych zgodności, administrator zabezpieczeń  |
| **Przypisywanie użytkowników**| Administrator globalny | Administrator globalny |

## <a name="start-a-premium-assessments-trial"></a>Rozpoczynanie wersji próbnej ocen w warstwie Premium

Wersja próbna ocen premium programu Compliance Manager to doskonały sposób na szybkie skonfigurowanie ocen, które są najbardziej istotne dla Twojej organizacji. Nasza biblioteka ponad 300 szablonów odpowiada przepisom rządowym i standardom branżowym na całym świecie.
Dowiedz się więcej o [wersji próbnej ocen premium](compliance-easy-trials-compliance-manager-assessments.md).

Możesz rozpocząć wersję próbną bezpośrednio z poziomu Menedżera zgodności i skonfigurować zalecane oceny, wykonując następujące kroki:

1. Na stronie **Przegląd** programu Compliance Manager wybierz pozycję **Rozpocznij wersję próbną**. Wprowadzisz kreatora aktywacji próbnej, który będzie zadawać pytania, które pomogą nam polecić oceny dla Twojej organizacji.

2. Na stronie **Aktywuj wersję próbną** wybierz pozycję **Dalej** , aby rozpocząć bezpłatną 90-dniowy okres próbny ocen premium i kontynuować tworzenie ocen.

3. Wybierz co najmniej jedną branżę identyfikującą organizację, a następnie wybierz pozycję **Dalej**.

4. Wybierz co najmniej jeden region dla lokalizacji organizacji, a następnie wybierz pozycję **Dalej**.

5. Na ekranie **Wybieranie ocen** wybierz strzałkę listy rozwijanej obok pozycji **Zalecane szablony** , aby wyświetlić listę ocen, które według nas dotyczą Twojej organizacji. Zaznacz pola obok szablonów, których chcesz użyć do tworzenia ocen, a następnie wybierz pozycję **Dalej**.

6. Przejrzyj ostateczne wybory i wybierz pozycję **Dodaj zalecane oceny,** aby utworzyć nowe oceny.

Dowiedz się więcej na temat rozpoczynania oceny, odwiedzając sekcję [Oceny](#assessments-page) poniżej.

## <a name="settings-for-automated-testing-and-user-history"></a>Ustawienia do testowania automatycznego i historii użytkowników

Ustawienia menedżera zgodności w portalu zgodności usługi Microsoft Purview umożliwiają włączanie i wyłączanie automatycznego testowania akcji poprawy. Ustawienia umożliwiają również zarządzanie danymi użytkowników skojarzonymi z akcjami ulepszania, w tym możliwością ponownego przypisywania akcji poprawy do innego użytkownika.  Tylko osoby z rolą administratora globalnego lub administratora menedżera zgodności mogą uzyskać dostęp do ustawień Menedżera zgodności.

> [!NOTE]
> Funkcja automatycznego testowania nie jest dostępna dla klientów w środowiskach GCC High i DoD, ponieważ wskaźnik bezpieczeństwa nie jest dostępny w tych środowiskach. klienci GCC High i DoD będą musieli ręcznie zaimplementować i przetestować swoje działania poprawy.

### <a name="set-up-automated-testing"></a>Konfigurowanie testowania automatycznego

Menedżer zgodności wykrywa sygnały z innych rozwiązań usługi Microsoft Purview subskrybowanych przez organizację, w tym zarządzania cyklem życia danych, ochrony informacji, ochrony przed utratą danych w usłudze Microsoft Purview, zgodności z komunikacją i zarządzania ryzykiem wewnętrznym. Na stronie szczegółów każdej akcji poprawy pole **Logika testowania** na karcie **Testowanie** pokaże, co jest wymagane w innym rozwiązaniu, aby akcja przekazywała i zdobywała punkty w kierunku oceny zgodności.

Menedżer zgodności wykrywa również sygnały z uzupełniających akcji poprawy, które są również monitorowane przez [wskaźnik bezpieczeństwa firmy Microsoft](../security/defender/microsoft-secure-score.md). Korzystając z tych sygnałów, Menedżer zgodności może automatycznie przetestować pewne akcje poprawy, co pomaga zmaksymalizować wydajność działań związanych ze zgodnością. Po pomyślnym przetestowaniu i zaimplementowaniu akcji poprawy otrzymasz pełną ilość punktów, które zostaną zapisane w ogólnym wyniku zgodności.

Automatyczne testowanie jest domyślnie włączone dla organizacji nowych w Menedżerze zgodności. Po pierwszym wdrożeniu Microsoft 365 lub Office 365 pełne zebranie danych i uwzględnienie ich w wyniku zgodności zajmuje około siedmiu dni. Po włączeniu testowania automatycznego data testu akcji nie zostanie zaktualizowana, ale jej stan testu zostanie zaktualizowany. Po utworzeniu nowych ocen wyniki są automatycznie uwzględniane w wynikach kontroli firmy Microsoft i integracji z bezpiecznym wynikiem.

#### <a name="manage-automated-testing-settings"></a>Zarządzanie ustawieniami testowania automatycznego

Administrator globalny organizacji może w dowolnym momencie zmienić ustawienia testowania automatycznego. Możesz wyłączyć testowanie automatyczne dla typowych akcji poprawy lub włączyć je dla poszczególnych akcji. Postępuj zgodnie z poniższymi instrukcjami, aby zmienić ustawienia testowania automatycznego.

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**pozycję Ustawienia**</a> w portalu zgodności usługi Microsoft Purview.

2. Na stronie ustawień wybierz pozycję **Menedżer zgodności**.

3. Wybierz pozycję **Testowanie źródła** w obszarze nawigacji po lewej stronie.

4. Wybierz odpowiedni przycisk, aby włączyć automatyczne testowanie dla wszystkich akcji poprawy, wyłączyć go dla wszystkich akcji lub włączyć według poszczególnych akcji.

5. Jeśli **wybierzesz opcję Włącz dla akcji poprawy**, na liście zostaną wyświetlone wszystkie dostępne akcje poprawy do wyboru.  Zaznacz pole wyboru obok dowolnej akcji, którą chcesz przetestować automatycznie.

6. Wybierz pozycję **Zapisz** , aby zapisać ustawienia. W górnej części ekranu zostanie wyświetlony komunikat z potwierdzeniem, że wybór został zapisany. Jeśli zostanie wyświetlone powiadomienie o błędzie, spróbuj ponownie.

**Uwaga:** Tylko administrator globalny może włączać lub wyłączać automatyczne aktualizacje dla wszystkich akcji. Administrator programu Compliance Manager może włączyć automatyczne aktualizacje dla poszczególnych akcji, ale nie dla wszystkich akcji globalnie.

**Dowiedz się więcej**
- [Dowiedz się więcej o tym, jak ciągłe monitorowanie przyczynia się do oceny zgodności](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).
- [Dowiedz się więcej na temat wyznaczania źródła testowania dla akcji poprawy](compliance-manager-improvement-actions.md#update-testing-source).

### <a name="manage-user-history"></a>Zarządzanie historią użytkowników

Ustawienia **Zarządzanie historią użytkowników** ułatwiają szybkie identyfikowanie użytkowników, którzy pracowali z akcjami ulepszania w Menedżerze zgodności. Identyfikowalne dane użytkownika skojarzone z akcjami poprawy obejmują wszelkie wykonane implementacje i testowanie, przekazane dokumenty oraz wszelkie wprowadzone notatki. Zrozumienie i pobranie tego typu danych może być konieczne dla własnych potrzeb organizacji w zakresie zgodności.

Ustawienia historii użytkowników umożliwiają również ponowne przypisanie wszystkich akcji poprawy między użytkownikami.

**Aby znaleźć ustawienia historii użytkownika:**

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**pozycję Ustawienia**</a> w portalu zgodności usługi Microsoft Purview.

2. Na stronie ustawień wybierz pozycję **Menedżer zgodności**.

3. Wybierz pozycję **Zarządzaj historią użytkowników** w obszarze nawigacji po lewej stronie.

Strona **Zarządzanie historią użytkowników** zawiera listę wszystkich użytkowników według adresu e-mail, którzy są przypisani do akcji poprawy. Użyj przycisku **Wyszukaj** , aby szybko znaleźć określonego użytkownika, wpisując jego adres e-mail.

Po prawej stronie adresu e-mail każdego użytkownika menu rozwijane **Wybierz** zawiera opcje eksportowania raportu, ponownego przypisywania akcji poprawy lub usuwania historii. Zobacz każdą sekcję poniżej, aby uzyskać szczegółowe informacje o każdej opcji.

#### <a name="export-a-report-of-user-history-data"></a>Eksportowanie raportu danych historii użytkowników

Możesz wyeksportować plik Excel zawierający listę akcji poprawy aktualnie przypisanych do użytkownika.  Raport zawiera również listę wszelkich plików dowodowych przekazanych przez tego użytkownika. Te informacje mogą pomóc w ponownym przypisaniu otwartych akcji poprawy.

Raport odzwierciedla stan akcji poprawy od daty utworzenia. Nie jest to historyczny raport wszystkich poprzednich zmian stanu lub przypisania (dowiedz się, jak [wyeksportować raport ze strony akcji poprawy](compliance-manager-improvement-actions.md#export-a-report)).

**Wykonaj poniższe kroki, aby wyeksportować raport według użytkownika:**

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**pozycję Ustawienia**</a> w portalu zgodności usługi Microsoft Purview.

2. Na stronie ustawień wybierz pozycję **Menedżer zgodności**.

3. Wybierz pozycję **Zarządzaj historią użytkowników** w obszarze nawigacji po lewej stronie.

4. Znajdź zamierzonego użytkownika, wyszukując adresy e-mail listy lub wybierając pozycję **Wyszukaj** i wprowadzając adres e-mail użytkownika.

5. Z menu rozwijanego **Wybierz** wybierz pozycję **Eksportuj raport**.

6. Po wygenerowaniu pliku Excel raportu możesz go otworzyć i zapisać na komputerze lokalnym.

#### <a name="reassign-improvement-actions-to-another-user"></a>Ponowne przypisywanie akcji poprawy do innego użytkownika

Możesz ponownie przypisać akcje poprawy od jednego użytkownika do innego. Po ponownym przypisaniu akcji historia przekazywania dokumentu nie zmienia się, ale nazwa użytkownika, który pierwotnie przekazał dokumentację, nie jest już wyświetlana w ramach akcji poprawy.

**Wykonaj poniższe kroki, aby ponownie przypisać akcje poprawy do innego użytkownika:**

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**pozycję Ustawienia**</a> w portalu zgodności usługi Microsoft Purview.

2. Na stronie ustawień wybierz pozycję **Menedżer zgodności**.

3. Wybierz pozycję **Zarządzaj historią użytkowników** w obszarze nawigacji po lewej stronie.

4. Znajdź użytkownika, wyszukując listę adresów e-mail lub wybierając pozycję **Wyszukaj** i wprowadzając adres e-mail tego użytkownika.

5. Z menu rozwijanego **Wybierz** wybierz pozycję **Przydziel ponownie akcje poprawy**. Zostanie wyświetlone okienko wysuwane **Reassign improvement actions (Ponowne przypisywanie akcji poprawy** ).

6. W polu **Wyszukaj użytkowników** wprowadź nazwę lub adres e-mail użytkownika, *do* którego chcesz przypisać akcje poprawy.

7. Gdy zobaczysz nazwę zamierzonego użytkownika w obszarze **Akcje poprawy zostaną przypisane do**, wybierz użytkownika, a następnie wybierz pozycję **Przypisz akcje**.

8. Po zakończeniu ponownego przypisywania w okienku wysuwanym zostanie wyświetlony komunikat z potwierdzeniem, że wszystkie akcje poprawy od poprzedniego użytkownika zostały ponownie przypisane do nowego użytkownika. Jeśli zostanie wyświetlone powiadomienie o niepowodzeniu ponownego przypisania, zamknij okno i spróbuj ponownie. Aby zamknąć okienko wysuwane, wybierz pozycję **Gotowe**.

Nowy przypisany otrzymuje wiadomość e-mail z informacją, że został przypisany do akcji poprawy. Wiadomość e-mail zawiera bezpośredni link do strony szczegółów akcji poprawy.

 > [!NOTE]
> Jeśli ponownie przypiszesz akcję, która ma oczekującą aktualizację, bezpośredni link do akcji w wiadomości e-mail ponownego przypisania zostanie przerwany, jeśli aktualizacja zostanie zaakceptowana po ponownym przypisaniu. Możesz rozwiązać ten problem, ponownie przypisując akcję użytkownikowi po zaakceptowaniu aktualizacji. Dowiedz się więcej o [aktualizacjach akcji ulepszania](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

#### <a name="delete-user-history"></a>Usuwanie historii użytkowników

Usunięcie historii użytkownika spowoduje usunięcie ich jako właściciela akcji poprawy i usunie jego nazwę ze wszystkich innych pól w Menedżerze zgodności. Po usunięciu historii użytkownika należące do niego akcje poprawy nie będą wyświetlane **jako przypisane do** wartości, dopóki nowy użytkownik nie zostanie przypisany. Wszystkie dokumenty przekazane do akcji poprawy będą pokazywać **, że użytkownik został usunięty** zamiast nazwy usuniętego użytkownika. Usuwanie historii użytkowników jest trwałe.

Aby usunąć historię użytkownika, wykonaj poniższe kroki:

1. Wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**pozycję Ustawienia**</a> w portalu zgodności usługi Microsoft Purview.

2. Na stronie ustawień wybierz pozycję **Menedżer zgodności**.

3. Wybierz pozycję **Zarządzaj historią użytkowników** w obszarze nawigacji po lewej stronie.

4. Znajdź użytkownika, wyszukując listę adresów e-mail lub wybierając pozycję **Wyszukaj** i wprowadzając adres e-mail tego użytkownika.

5. Z menu rozwijanego **Wybierz** wybierz pozycję **Usuń historię**.

6. Zostanie wyświetlone okno z prośbą o potwierdzenie trwałego usunięcia historii użytkownika. Aby kontynuować usuwanie, wybierz pozycję **Usuń historię**. Aby pozostawić bez usuwania historii, wybierz pozycję **Anuluj**.

7. Nastąpi powrót na stronę **Zarządzanie historią użytkownika** z komunikatem potwierdzającym, że historia użytkownika została usunięta.

## <a name="understand-the-compliance-manager-dashboard"></a>Omówienie pulpitu nawigacyjnego programu Compliance Manager

Pulpit nawigacyjny programu Compliance Manager został zaprojektowany z myślą o zapewnieniu wglądu w aktualną postawę zgodności.

:::image type="content" alt-text="Menedżer zgodności — pulpit nawigacyjny." source="../media/compliance-manager-dashboard.png" lightbox="../media/compliance-manager-dashboard.png":::

### <a name="overall-compliance-score"></a>Ogólny wynik zgodności

Wskaźnik zgodności jest wyróżniony w górnej części. Pokazuje ona wartość procentową w oparciu o punkty osiągalne do wykonania działań ulepszeń, które odnoszą się do kluczowych standardów i przepisów dotyczących ochrony danych. Punkty z [akcji firmy Microsoft](compliance-manager-assessments.md#microsoft-actions-tab), które są zarządzane przez moją firmę Microsoft, również są wliczane do oceny zgodności.

Gdy po raz pierwszy przychodzisz do Menedżera zgodności, twój początkowy wynik jest oparty na [Microsoft 365 punktu odniesienia ochrony danych](compliance-manager-assessments.md#data-protection-baseline-default-assessment). Ta ocena bazowa, dostępna dla wszystkich organizacji, to zestaw mechanizmów kontroli, który obejmuje wspólne przepisy branżowe i standardy. Menedżer zgodności skanuje istniejące rozwiązania Microsoft 365 i umożliwia wstępną ocenę na podstawie bieżących ustawień prywatności i zabezpieczeń. Po dodaniu ocen, które są istotne dla Twojej organizacji, twój wynik staje się dla Ciebie bardziej zrozumiały.

**Dowiedz się więcej: Dowiedz się**[, jak jest obliczana ocena zgodności](compliance-score-calculation.md).

### <a name="key-improvement-actions"></a>Kluczowe akcje poprawy

W tej sekcji wymieniono najważniejsze akcje poprawy, które można teraz wykonać, aby mieć największy pozytywny wpływ na ogólny wynik zgodności. Wybierz pozycję **Wyświetl wszystkie akcje poprawy** , aby przejść do strony akcji poprawy.

### <a name="solutions-that-affect-your-score"></a>Rozwiązania wpływające na wynik

W tej sekcji wyróżniono rozwiązania zawierające akcje poprawy, które mogą pozytywnie wpłynąć na wynik, oraz liczbę nierozstrzygniętych akcji poprawy w tych rozwiązaniach. Wybierz pozycję **Wyświetl wszystkie rozwiązania** , aby odwiedzić stronę rozwiązań.

### <a name="compliance-score-breakdown"></a>Podział wyników zgodności

W tej sekcji przedstawiono bardziej szczegółowy widok wyniku na dwa różne sposoby:

- **Kategorie**: pokazuje procent ogólnej oceny w kategoriach ochrony danych, takich jak "ochrona informacji" lub "zarządzanie urządzeniami".
- **Oceny**: pokazuje procent postępów w zarządzaniu ocenami dla określonych standardów zgodności i ochrony danych, przepisów lub przepisów, takich jak RODO lub NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrowanie widoku pulpitu nawigacyjnego

Widok pulpitu nawigacyjnego można filtrować, aby wyświetlić tylko elementy związane z określonymi przepisami i standardami, rozwiązaniami, typem akcji, grupami oceny lub kategoriami ochrony danych. Filtrowanie widoku w ten sposób spowoduje również odfiltrowanie wyniku na pulpicie nawigacyjnym, pokazując liczbę punktów uzyskanych z łącznej liczby możliwych punktów na podstawie kryteriów filtru.

Aby zastosować filtry:

1. Wybierz pozycję **Filtruj** w prawym górnym rogu pulpitu nawigacyjnego.
2. Wybierz kryteria filtru w okienku wysuwanym **Filtry** , a następnie wybierz pozycję **Zastosuj**.

Po zastosowaniu filtru wynik zostanie skorygowany w czasie rzeczywistym. Procent oceny zgodności i informacje o podziale oraz akcje poprawy i rozwiązania odnoszą się teraz tylko do danych objętych kryteriami filtru. Jeśli wylogujesz się z Menedżera zgodności, filtrowany widok pozostanie po zalogowaniu się ponownie.

Aby usunąć filtry:

- W nagłówku **Zastosowane filtry** powyżej wskaźnika zgodności wybierz znak **X** obok pojedynczego filtru, który chcesz usunąć; Lub
- Wybierz pozycję **Filtruj** w prawym górnym rogu pulpitu nawigacyjnego, a następnie w okienku wysuwanym Filtry wybierz pozycję **Wyczyść filtry**.

## <a name="improvement-actions-page"></a>Strona akcji ulepszania

[Akcje ulepszania](compliance-manager-improvement-actions.md) to akcje zarządzane przez organizację. Praca z akcjami ulepszania pomaga scentralizować działania związane ze zgodnością i dostosować je do przepisów i standardów ochrony danych. Każda akcja poprawy zapewnia szczegółowe wskazówki dotyczące implementacji i link umożliwiający uruchomienie odpowiedniego rozwiązania. Akcje poprawy można przypisać do użytkowników w organizacji w celu wykonywania zadań implementacji i testowania. W ramach akcji poprawy można również przechowywać dokumentację, notatki i aktualizacje stanu rekordów.

### <a name="view-your-improvement-actions"></a>Wyświetlanie akcji ulepszania

Na pulpicie nawigacyjnym Programu Compliance Manager są wyświetlane kluczowe akcje ulepszania. Aby wyświetlić wszystkie akcje poprawy, wybierz kartę **Akcje poprawy** na pulpicie nawigacyjnym, która umożliwia wyświetlenie strony akcji poprawy. Możesz również wybrać pozycję **Wyświetl wszystkie akcje poprawy** poniżej listy akcji poprawy klucza na pulpicie nawigacyjnym, aby przejść do strony akcji poprawy.

Na stronie akcji poprawy są wyświetlane wszystkie akcje poprawy zarządzane przez organizację. Akcje zarządzane przez firmę Microsoft można wyświetlać w ramach każdej oceny (dowiedz się więcej o [akcjach firmy Microsoft](compliance-manager-assessments.md#microsoft-actions-tab)).

Jeśli masz długą listę akcji na stronie akcji poprawy, może być przydatne filtrowanie widoku. Wybierz pozycję **Filtruj** w prawym górnym rogu listy akcji. Po wyświetleniu okienka wysuwanego **Filtry** wybierz kryteria z dostępnych opcji. Możesz również dostosować widok, wybierając pozycję **Grupa** w prawym górnym rogu. Z menu rozwijanego wybierz pozycję , aby wyświetlić według grupy, rozwiązania, kategorii, typu akcji lub stanu.

Domyślny widok dla tej strony nie pokazuje akcji poprawy ze stanem testu **z wynikiem Passed.The** default view for this page does not show improvement actions with a test status of Passed (Widok domyślny dla tej strony nie pokazuje akcji poprawy ze stanem testu z wynikiem Pass Aby wyświetlić akcje, które przeszły testy, zaznacz pole **Passed (Przekazano** ) w okienku wysuwanym Filtry. Tylko akcje ze stanem testu **Liczba przeszłych** do wyniku. Niektóre akcje mogą pokazywać **oczekującą etykietę aktualizacji.** Dowiedz się więcej o [aktualizacjach akcji ulepszania](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

Na stronie akcji poprawy przedstawiono następujące punkty danych dla każdej akcji poprawy:

- **Produkty**: oceniany produkt.
- **Osiągnięte punkty**: liczba punktów osiągniętych z łącznej liczby dostępnych punktów przez ukończenie akcji
- **Przepisy**: przepisy lub normy odnoszące się do działania
- **Grupa**: grupa, do której przypisano akcję
- **Rozwiązania**: rozwiązanie, do którego można przejść, aby wykonać akcję
- **Oceny**: oceny zawierające akcję
- **Kategorie**: powiązana kategoria ochrony danych (na przykład ochrona informacji, zarządzanie urządzeniami itp.)
- **Stan testu**:
  - **Brak** — nie zarejestrowano aktualizacji stanu
  - **Nie oceniono** — testowanie nie zostało rozpoczęte
  - **Przekazano** — pomyślnie przetestowano implementację
  - **Niepowodzenie niskiego ryzyka** — testowanie nie powiodło się, niskie ryzyko
  - **Średnie ryzyko zakończone niepowodzeniem** — testowanie nie powiodło się, średnie ryzyko
  - **Niepowodzenie wysokiego ryzyka** — testowanie nie powiodło się, wysokie ryzyko
  - **Poza zakresem** — akcja nie jest w zakresie oceny i nie ma wpływu na wynik
  - **Do wykrycia** — w przypadku testu ręcznego wskazuje, że akcja została zaimplementowana, ale nie została przetestowana; w przypadku testu automatycznego oznacza, że akcja czeka na wynik automatyzacji
  - **Nie można wykryć** — nie można określić stanu zautomatyzowanego
  - **Częściowo przetestowane — automatyczne ocenianie** , które przyznaje częściowe punkty
- **Typ akcji**: wskazuje, czy akcja poprawy jest techniczna, co oznacza, że można ją zaimplementować w ramach rozwiązania lub produktu, czy też nietechnii, które zostałoby zaimplementowane poza rozwiązaniem technicznym
- **Przypisana do**: osoba, do której przypisano tę akcję, jeśli ma to zastosowanie
- **Źródło testowania**: wskazuje, czy źródło testowania akcji jest ręczne, automatyczne lub dziedziczone po elemencie nadrzędnym

**Dowiedz się więcej:** [Zobacz, jak przypisywać i wykonywać prace nad akcjami poprawy](compliance-manager-improvement-actions.md).

## <a name="solutions-page"></a>Strona rozwiązania

Na stronie rozwiązań przedstawiono udział zdobytych i potencjalnych punktów uporządkowany według rozwiązania. Wyświetlanie pozostałych punktów i akcji poprawy z tego widoku pomaga zrozumieć, które rozwiązania wymagają natychmiastowej uwagi.

Znajdź stronę rozwiązań, wybierając kartę **Rozwiązania** na pulpicie nawigacyjnym Menedżera zgodności. Możesz również wybrać pozycję **Wyświetl wszystkie rozwiązania** poniżej pozycji **Rozwiązania, które wpływają na wynik** w prawej górnej części pulpitu nawigacyjnego.

### <a name="filtering-your-solutions-view"></a>Filtrowanie widoku rozwiązań

Aby filtrować widok rozwiązań:

1. Wybierz pozycję **Filtruj** w lewym górnym rogu listy ocen.
2. W okienku wysuwanym **Filtry** umieść znacznik wyboru obok żądanych kryteriów (przepisów, rozwiązań, typów akcji, grup, kategorii).
3. Wybierz przycisk **Zastosuj** . Okienko filtru zostanie zamknięte, a zobaczysz filtrowany widok.

Możesz również zmodyfikować widok, aby wyświetlić oceny według grupy, produktu lub regulacji, wybierając typ grupowania z menu rozwijanego **Grupa** nad listą ocen.

### <a name="taking-action-from-the-solution-page"></a>Podejmowanie akcji na stronie rozwiązania

Na stronie rozwiązania są wyświetlane rozwiązania organizacji połączone z akcjami poprawy. W tabeli wymieniono wkład każdego rozwiązania w ogólny wynik, punkty osiągnięte i możliwe w ramach tego rozwiązania oraz pozostałą liczbę akcji poprawy pogrupowanych w tym rozwiązaniu, które mogą zwiększyć wynik.

Istnieją dwa sposoby podejmowania akcji na tym ekranie:

1. W wierszu zamierzonego rozwiązania w kolumnie **Pozostałe akcje** wybierz numer hiperłącza. Zobaczysz filtrowany widok ekranu akcji poprawy przedstawiający niesprawdzone akcje poprawy dla tego rozwiązania.

2. W wierszu zamierzonego rozwiązania w kolumnie **Otwórz rozwiązanie** wybierz pozycję **Otwórz**. Rozwiązanie lub lokalizacja zostaną wyświetlone w Microsoft 365 i Office 365 centrach zabezpieczeń i zgodności, w których można wykonać zalecaną akcję.

## <a name="assessments-page"></a>Strona Ocen

Na stronie ocen wymieniono wszystkie [oceny skonfigurowane](compliance-manager-assessments.md) dla organizacji. Mianownik oceny zgodności jest określany przez wszystkie śledzone oceny. Po dodaniu kolejnych ocen na stronie akcji poprawy zostanie wyświetlonych więcej akcji poprawy, a mianownik oceny zgodności wzrośnie.

Licznik **aktywowanych szablonów** w górnej części strony pokazuje liczbę aktywnych szablonów oceny aktualnie używanych z łącznej liczby szablonów dostępnych dla organizacji do użycia. Aby uzyskać więcej informacji, zobacz [Dostępność szablonu i licencjonowanie](compliance-manager-templates.md#template-availability-and-licensing) .

Strona ocen zawiera podsumowanie kluczowych informacji o każdej ocenie:

- **Ocena**: nazwa oceny
- **Stan**:
  - **Ukończono** — wszystkie kontrolki mają stan "przekazany" lub co najmniej jeden jest przekazywany, a pozostałe są "poza zakresem"
  - **Niekompletne** — co najmniej jedna kontrolka ma stan "niepowodzenie"
  - **Brak** — wszystkie kontrolki nie zostały przetestowane
  - **W toku** — akcje poprawy mają inny stan, w tym "w toku", "częściowe środki" lub "niewykryte
- **Postęp oceny**: procent pracy wykonanej w kierunku ukończenia, mierzony liczbą pomyślnie przetestowanych mechanizmów kontroli
- **Twoje akcje poprawy**: liczba ukończonych akcji w celu spełnienia wymagań implementacji kontrolek
- **Akcje firmy Microsoft**: liczba ukończonych akcji w celu spełnienia wymagań implementacji kontrolek firmy Microsoft
- **Grupa**: nazwa grupy, do której należy ocena
- **Produkt**: skojarzony produkt, taki jak Microsoft 365 lub inny produkt zdefiniowany do oceny
- **rozporządzenie**: norma prawna, polityka lub prawo, które ma zastosowanie do oceny

### <a name="filtering-your-assessments-view"></a>Filtrowanie widoku ocen

Aby filtrować widok ocen:

1. Wybierz pozycję **Filtruj** w lewym górnym rogu listy ocen.
2. W okienku wysuwanym **Filtry** sprawdź żądane kryteria.
3. Wybierz przycisk **Zastosuj** . Okienko filtru zostanie zamknięte i zostanie wyświetlony filtrowany widok.

Możesz również zmodyfikować widok, aby wyświetlić oceny według grupy, produktu lub regulacji, wybierając typ grupowania z menu rozwijanego **Grupa** nad listą ocen.

### <a name="default-assessment"></a>Ocena domyślna

Domyślnie ocena [punktu odniesienia ochrony danych](compliance-manager-assessments.md#data-protection-baseline-default-assessment) zostanie wyświetlona na stronie ocen. Menedżer zgodności udostępnia również kilka wstępnie [utworzonych szablonów](compliance-manager-templates-list.md) do kompilowania ocen.

## <a name="assessment-templates-page"></a>Strona szablonów oceny

Szablon to platforma do tworzenia oceny w menedżerze zgodności. Na stronie szablonów oceny jest wyświetlana lista szablonów i kluczowych szczegółów. Lista zawiera szablony udostępniane przez menedżera zgodności, a także wszelkie szablony zmodyfikowane lub utworzone przez organizację. Filtry można zastosować, aby znaleźć szablon na podstawie certyfikacji, zakresu produktu, kraju, branży i tego, kto go utworzył.

Licznik **aktywowanych szablonów** w górnej części strony pokazuje liczbę aktywnych szablonów oceny aktualnie używanych z łącznej liczby szablonów dostępnych dla organizacji do użycia. Aby uzyskać więcej informacji, zobacz [Dostępność szablonu i licencjonowanie](compliance-manager-templates.md#template-availability-and-licensing) .

Wybierz szablon z jego wiersza, aby wyświetlić jego stronę szczegółów, która zawiera opis szablonu oraz dalsze informacje o certyfikacie, zakresie i szczegółach kontrolek. Na tej stronie możesz wybrać odpowiednie przyciski, aby utworzyć ocenę, wyeksportować dane szablonu do Excel lub zmodyfikować szablon.

**Dowiedz się więcej:** [Przeczytaj, jak pracować z szablonami oceny](compliance-manager-templates.md).

## <a name="next-step"></a>Następny krok

Dostosuj Menedżera zgodności, [konfigurując oceny](compliance-manager-assessments.md).
