---
title: Tworzenie ocen i zarządzanie nimi w Menedżerze zgodności firmy Microsoft
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
search.appverid:
- MOE150
- MET150
description: Twórz oceny w Menedżerze zgodności firmy Microsoft, aby ułatwić spełnianie wymagań przepisów i certyfikatów ważnych dla Twojej organizacji.
ms.openlocfilehash: 59f2bd89a798567d51c3e28fda574e7b9f0ba326
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319535"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Tworzenie ocen i zarządzanie nimi w Menedżerze zgodności

**W tym artykule:** Dowiedz się, jak dostosować Menedżera zgodności dla organizacji, tworząc oceny i zarządzając **nimi**. W tym artykule opisano, jak tworzyć oceny, organizować je w **grupy, pracować** z kontrolkami **, akceptować** aktualizacje i eksportować raporty z **ocen**.

## <a name="introduction-to-assessments"></a>Wprowadzenie do ocen

Menedżer zgodności ułatwia tworzenie ocen, które oceniają zgodność z branżą i przepisami regionalnymi, które dotyczą Twojej organizacji. Formularze oceniania są zbudowane na podstawie szablonów formularzy oceniania, które zawierają niezbędne mechanizmy kontroli, działania udoskonalania oraz , tam gdzie to konieczne, akcje firmy Microsoft służące do ukończenia oceny. Skonfigurowanie najbardziej istotnych ocen dla organizacji może ułatwić zaimplementowanie zasad i procedur operacyjnych w celu ograniczenia ryzyka związanego ze zgodnością.

Wszystkie testy są wyświetlane na karcie oceny w Menedżerze zgodności. Dowiedz się więcej [na temat filtrowania widoku swoich ocen i interpretowania stanów](compliance-manager-setup.md#assessments-page).

> [!IMPORTANT]
> Szablony dostępne dla Twojej organizacji do tworzenia ocen zależą od umowy licencyjnej. [Przejrzyj szczegóły licencjonowania](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="data-protection-baseline-default-assessment"></a>Ocena domyślna planu bazowego ochrony danych

Aby rozpocząć, firma Microsoft udostępnia **domyślną** ocenę w Menedżerze zgodności pod Microsoft 365 **bazowym ochrony danych**. Ta ocena podstawowa oferuje zestaw kontrolek kluczowych przepisów i standardów w zakresie ochrony danych i ogólnego zarządzania danymi. Ten plan bazowy rysuje elementy przede wszystkim z NIST CSF (National Institute of Standards and Technology Nacjonalizacja) i ISO (Międzynarodowa Organizacja Normalizacji), a także fedRAMP (Federal Risk and Authorization Management Program) i RODO (Ogólne Rozporządzenie o Ochronie Danych Unii Europejskiej).

Ta ocena służy do obliczania początkowego wyniku zgodności po pierwszym zajdzie do Menedżera zgodności, zanim skonfigurujesz jakiekolwiek inne oceny. Menedżer zgodności zbiera początkowe sygnały od Twoich Microsoft 365 rozwiązania. Zobaczysz w skrócie, jak Twoja organizacja działa w odniesieniu do kluczowych standardów i przepisów dotyczących ochrony danych, oraz zobaczysz sugerowane działania ulepszeń do podjęcia.

Menedżer zgodności staje się bardziej przydatny podczas tworzenia własnych ocen i zarządzania nimi w celu zaspokojenia konkretnych potrzeb organizacji.

## <a name="understand-groups-before-creating-assessments"></a>Opis grup przed utworzeniem ocen

Podczas tworzenia oceny musisz przypisać ją do grupy. Grupy to kontenery umożliwiające organizowanie ocen w logiczny sposób, na przykład według roku lub przepisów albo na podstawie działów lub obszarów geograficznych organizacji. Dlatego zalecamy planowanie strategii grupowania przed utworzeniem ocen.

Poniżej przedstawiono przykłady dwóch grup i ich podstawowych ocen:

- **FFIEC IS assessment 2020**
  - FFIEC IS
- **Oceny zabezpieczeń i prywatności danych**
  - ISO 27001:2013
  - ISO 27018:2014

Różne oceny w obrębie grupy lub grup mogą dzielić się działaniami udoskonalania. Działania udoskonalania mogą być zmianami wprowadzonymi w rozwiązaniach technicznych zamapowanych na dzierżawcę, na przykład włączenie uwierzytelniania dwuskładnikowego lub działań nietechnnych, które wykonujesz poza systemem, takich jak przekształcanie nowych zasad pracy. Wszystkie aktualizacje szczegółowe lub o stanie w działaniu w zakresie ulepszania technicznego będą wybierane przez testy we wszystkich grupach. Aktualizacje działań niebędące udoskonalaniami technicznymi będą rozpoznawane przez oceny w grupie, w której je stosujesz. Dzięki temu można wdrożyć jedno działanie udoskonalania i jednocześnie spełnić kilka wymagań.

### <a name="create-a-group"></a>Tworzenie grupy

Podczas tworzenia nowej oceny możesz utworzyć grupę. Grup nie można tworzyć jako jednostek autonomicznych.

### <a name="what-to-know-when-working-with-groups"></a>Co należy wiedzieć podczas pracy z grupami

- Grupa musi zawierać co najmniej jedną ocenę.
- Nazwy grup muszą być unikatowe w organizacji.
- Grupy nie mają właściwości zabezpieczeń. Wszystkie uprawnienia są skojarzone z ocenami.
- Po dodaniu oceny do grupy nie można zmienić grupowania.
- Po dodaniu nowej oceny do istniejącej grupy typowe informacje dotyczące ocen z tej grupy są kopiowane do nowej oceny.
- Powiązane mechanizmy kontroli ocen w różnych ocenach w tej samej grupie są automatycznie aktualizowane po ukończeniu.
- Grupy mogą zawierać oceny dla tego samego certyfikatu lub przepisów, ale każda grupa może zawierać tylko jedną ocenę określonej pary certyfikacji produktu. Na przykład grupa nie może zawierać dwóch ocen dla programu Office 365 i NIST CSF. Grupa może zawierać wiele ocen dla tego samego produktu tylko wtedy, gdy odpowiadające im certyfikaty lub przepisy dla każdej z nich są inne.
- Usunięcie oceny przerywa relację między tym oceniam a grupą.
- Grup nie można usuwać ręcznie.

## <a name="understand-templates-before-creating-assessments"></a>Opis szablonów przed utworzeniem ocen

Szablony oceniań zawierają kontrolki i zalecenia dotyczące działań w zakresie ocen na podstawie certyfikatów dla różnych przepisów i standardów ochrony prywatności. Dostępne szablony w Twojej organizacji mogą zawierać jeden lub więcej szablonów, które zostały uwzględnione w ramach umowy licencyjnej, wraz z dowolnymi dodatkowymi zakupionymi szablonami premium.

Każdy szablon, dołączony lub premium, istnieje w dwóch wersjach: jednej do użytku z programem Microsoft 365 (lub innymi dostępnymi produktami firmy Microsoft) i uniwersalnej wersji, która może być dostosowana do oceny innych produktów, których używasz. Możesz wybrać odpowiedni typ szablonu dla produktu, który chcesz ocenić.

Aby dowiedzieć się więcej o szablonach, zobacz [Praca z szablonami oceniania](compliance-manager-templates.md).

## <a name="create-assessments"></a>Tworzenie ocen

> [!NOTE]
> Tylko użytkownicy, którzy mają uprawnienia administratora globalnego, administratora zgodności lub roli oceniania menedżera zgodności, mogą tworzyć i modyfikować oceny. Dowiedz się więcej o [rolach i uprawnieniach](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

Przed rozpoczęciem upewnij się, że wiesz, do której grupy chcesz przypisać tę grupę, lub przygotuj się do utworzenia nowej grupy na podstawie tej oceny. Przeczytaj szczegółowe informacje o [grupach i ocenach](#understand-groups-before-creating-assessments).

Aby utworzyć ocenę, skorzystaj z procedury ze przewodnikiem w celu wybrania szablonu i wyznaczenia skojarzonego produktu. Na stronie **Assessments (Testy** ) zalecamy rozpoczęcie od przycisku **Add Recommended Assessments** (Dodaj zalecane oceny), który ułatwia określenie i szybkie skonfigurowanie najbardziej odpowiednich ocen dla organizacji jednocześnie. Możesz również skonfigurować testy po jednej na raz, wybierając pozycję **Dodaj testy**. Wykonaj poniższe czynności, aby rozpocząć tworzenie ocen.

#### <a name="create-assessments-based-on-recommendations-for-your-org-type"></a>Tworzenie ocen na podstawie zaleceń dotyczących typu organizacji

Menedżer zgodności może wskazać, które oceny mogą być najbardziej istotne dla twojej organizacji. Gdy po podajesz podstawowe informacje na temat branży i lokalizacji Twojej organizacji, zalecamy szablony, których można użyć z naszej biblioteki z ponad 300 szablonami. Po prostu wybierz jeden z zalecanych szablonów, aby szybko skonfigurować wiele formularzy oceniania jednocześnie. 

Aby utworzyć jedną lub więcej ocen na podstawie naszych zaleceń, wybierz pozycję **Dodaj** polecane testy na stronie **Assessments** (Testy) i wykonaj następujące czynności:
   - Wybierz co najmniej jeden branżę identyfikującą Twoją organizację, a następnie wybierz pozycję **Dalej.**
   - Wybierz co najmniej jeden region dla lokalizacji organizacji, a następnie wybierz pozycję **Dalej**
   - Na **ekranie Wybierz testy** wybierz strzałkę listy rozwijanej obok pozycji Polecane **szablony** , aby wyświetlić listę oceniań, które według nas obowiązują w Twojej organizacji. Zaznacz pola wyboru obok szablonów, których chcesz użyć do tworzenia formularzy oceniania, a następnie wybierz pozycję **Dalej**.
   - Przejrzyj wybrane ostatnie testy i wybierz **pozycję Dodaj zalecane oceny** , aby utworzyć nowe testy.

#### <a name="create-an-assessment-using-a-guided-process"></a>Tworzenie oceny przy użyciu procesu ze przewodnikiem

1. Na stronie **Assessments (Testy** ) wybierz pozycję **Add assessment (Dodaj testy**). Spowoduje to utworzenie kreatora tworzenia ocen.

2. Na **ekranie Szablon** podstawowy wybierz pozycję **Wybierz szablon** , aby wybrać szablon do oceny.

3. W okienku wysuwanych wybierz szablon rozporządzenia lub certyfikacji, na podstawie którego zostanie podstawą oceny. Lista szablonów podzielonych na kategorie dostępne i klasy premium ([szczegóły](compliance-manager-templates.md#template-availability-and-licensing)). **Liczniki aktywowanych/** licencjonowanych szablonów u góry okienka wysuwanego pokazują, jak mogą zawierać szablony, których używasz, z łącznej liczby dostępnych w Twojej organizacji lub z nich możesz korzystać (dowiedz się [więcej](compliance-manager-templates.md#active-and-inactive-templates)). Wybierz przycisk radiowy obok wybranego szablonu, a następnie wybierz pozycję **Zapisz**. Powrócisz do ekranu Szablon **podstawowy** , gdzie będzie można przejrzeć szczegóły szablonu, a następnie kontynuować, wybierając przycisk **Dalej**.

4. **Produkt, nazwa i grupa:** Ustaw te właściwości, aby zidentyfikować ocenę, wybierz produkt, który będzie oceniany, i przypisz go do grupy.

    - **Produkt**: Wybierz produkt, którego ma dotyczyć Twoja ocena. Jeśli używasz szablonu firmy Microsoft, na przykład przeznaczonego dla systemu Microsoft 365, to pole zostanie wypełnione w celu wskazania odpowiedniego produktu i nie będzie można go zmienić. Jeśli korzystasz z szablonu uniwersalnego, wybierz, czy chcesz utworzyć tę ocenę dla nowego produktu, czy dla produktu niestandardowego, który został już zdefiniowany w Menedżerze zgodności. Jeśli wybierzesz nowy produkt, wprowadź jego nazwę. Pamiętaj, że nie możesz wybrać wstępnie zdefiniowanego produktu firmy Microsoft, używając szablonu uniwersalnego.
    - **Nazwa oceny**: wprowadź nazwę oceniania w polu **Nazwa oceniania** . Nazwy oceniań muszą być unikatowe w grupach. Jeśli nazwa twojego oceniania jest inna niż nazwa innej oceny w dowolnej grupie, zostanie wyświetlony komunikat o błędzie z prośbą o utworzenie innej nazwy.
    - **Grupa**: Przypisz ocenę do grupy. Możesz:
        - Wybierz **pozycję Użyj istniejącej** grupy, aby przypisać ją do już utworzonej grupy. lub
        - Wybierz **pozycję Utwórz nową** grupę, aby utworzyć nową grupę i przypisać do tej grupy tę ocenę:
            - Określ nazwę grupy i wprowadź ją w polu poniżej przycisku radiowego.
            - Możesz **skopiować dane z istniejącej** grupy, takie jak szczegóły implementacji i testów oraz dokumenty, zaznaczając odpowiednie pola.

    Po zakończeniu wybierz pozycję **Dalej**.

5. **Przejrzyj i zakończ:** Przejrzyj wybrane opcje i dokonaj niezbędnych zmian. Gdy wszystko będzie gotowe, wybierz pozycję **Utwórz ocenę**.

Na następnym ekranie zostanie potwierdzające, że została utworzona ocena. Po wybraniu **przycisku** Gotowe zostanie przejdę do strony szczegółów nowego oceniania.

Jeśli po wybraniu **przycisku Utwórz** ocena zostanie wyświetlony ekran z niepowodzeniem **, wybierz** **pozycję Spróbuj** ponownie, aby ponownie utworzyć ocenę.

Po utworzeniu oceniania możesz zmienić jego nazwę, wybierając przycisk Edytuj nazwę w  prawym górnym rogu strony ze szczegółami [oceniania](#monitor-assessment-progress-and-controls).

## <a name="monitor-assessment-progress-and-controls"></a>Monitorowanie postępu i kontroli nad ocenami

Każda ocena zawiera stronę ze szczegółami, która pozwala na szybki podgląd postępów w jej ukończeniu. Na stronie pokazano postęp kończenie kontrolek i stan testowania kluczowych działań udoskonalania w tych kontrolkach.

### <a name="overview-tab"></a>Karta Omówienie

Karta Przegląd zawiera wykres pokazujący Twój procent w kierunku ukończenia oceny. Ten wykres zawiera zestawienie punktów za posiadane akcje i punkty z akcji należących do firmy Microsoft, dzięki czemu możesz zobaczyć, ile punktów potrzebujesz, aby ukończyć ocenę.

W kolejności największego potencjalnego wpływu na zdobywanie punktów wymieniono najważniejsze działania usprawnień dla kontroli w ramach oceny. Skojarzony wykres przedstawia zagregowany stan testów działań udoskonalania, aby można było szybko sprawdzić, co zostało przetestowane, a co jeszcze należy zrobić.

Aby uzyskać dostęp do poszczególnych działań udoskonalania, odwiedź **kartę Kontrolki** lub **kartę Akcje udoskonalania** .

### <a name="controls-tab"></a>Karta Kontrolki

Na karcie Kontrolki są wyświetlane szczegółowe informacje dotyczące każdej kontrolki zamapowane na ocenę. Wykres **podziału stanu kontrolki** przedstawia stan kontrolek według rodziny, dzięki czemu możesz od razu zobaczyć, które grupy kontrolek wymagają uwagi.

Poniżej wykresu znajduje się tabela ze szczegółowymi informacjami o każdej kontrolce w ramach oceny. Kontrolki są pogrupowane według rodziny kontrolek. Rozwiń nazwę każdej rodziny, aby odsłonić poszczególne kontrolki, które zawiera. W przypadku każdej kontrolki wymienione są między innymi:

- **Tytuł kontrolki**
- **Stan**: odzwierciedla stan testowy działań udoskonalania w ramach kontroli. 
    - **Pomyślnie** przekazane — wszystkie działania udoskonalania mają stan testowy "pomyślnie" lub co najmniej jeden, a pozostałe są "poza zakresem"
    -  **Niepowodzenie —** co najmniej jedna akcja udoskonalania ma stan testu "nie powiodło się"
    - **Brak** — nie przetestowano wszystkich działań udoskonalania
    - **Poza zakresem** — nie ma możliwości działań udoskonalania w ramach tej oceny
    - **W toku** — działania udoskonalania mają status inny niż wymienione powyżej, który może obejmować "w toku", "częściowe środków" lub "niewykrywone"
- **Identyfikator kontrolki**: numer identyfikacyjny kontrolki przypisany na podstawie odpowiadającego jej przepisami, standardem lub zasadami
- **Punkty zdobyte**: liczba punktów zdobytych w ukończeniu akcji ( w łącznej liczbie osiągalnych punktów) 
- **Twoje akcje**: liczba akcji ukończonych w ramach łącznej liczby akcji do ukończenia
- **Akcje firmy Microsoft**: liczba akcji ukończonych przez firmę Microsoft

Aby wyświetlić szczegóły kontrolki, wybierz ją z jej wiersza w tabeli. Strona szczegółów kontrolki zawiera wykres wskazujący stan testu akcji w tej kontrolce. W tabeli poniżej wykresu przedstawiono kluczowe działania ulepszeń tej kontrolki.

Wybierz z listy akcję udoskonalania, aby przejść do strony szczegółów akcji udoskonalania. Na stronie szczegółów przedstawiono informacje o stanie testowania i implementacji oraz wpadniesz do zalecanego rozwiązania.

### <a name="your-improvement-actions-tab"></a>Karta Działania udoskonalania

Karta działań udoskonalania zawiera listę wszystkich kontrolek w ramach oceny, które są zarządzane przez Twoją organizację. Na pasku stanu jest szczegółowo o zagregowanym stanie testów działań udoskonalania w ramach testu, co pozwala szybko sprawdzić, co zostało przetestowane, a co jeszcze należy zrobić. Poniżej paska znajduje się pełna lista działań udoskonalania i kluczowych szczegółów, w tym: stan testu, liczba potencjalnych i zdobytych punktów, skojarzone przepisy i standardy, mające zastosowanie rozwiązanie, typ akcji i kontrola rodziny. Dowiedz się więcej [o tym, jak akcje współtworą Twój wynik zgodności](compliance-score-calculation.md#action-types-and-points).

Wybierz akcję udoskonalania, aby wyświetlić jej stronę szczegółów, a następnie wybierz link **Uruchom** teraz, aby otworzyć rozwiązanie do podjęcia działania.

### <a name="microsoft-actions-tab"></a>Karta Akcje Microsoft

Karta Akcje firmy Microsoft jest wyświetlana dla ocen na podstawie szablonów, które obsługują produkty firmy Microsoft. Zawiera on listę wszystkich działań w ramach oceny, które są zarządzane przez firmę Microsoft. Lista zawiera najważniejsze szczegóły akcji, w tym: stan testu, punkty, które współtwoarzą ogólną ocenę zgodności, skojarzone przepisy i standardy, odpowiednie rozwiązanie, typ akcji i rodzinę kontroli. Wybierz akcję udoskonalania, aby wyświetlić jej stronę szczegółów.

Dowiedz się więcej o [tym, w jaki sposób są śledzone i poprawiane mechanizmy kontroli i działania ulepszeń.](compliance-score-calculation.md)

## <a name="accept-updates-to-assessments"></a>Akceptowanie aktualizacji ocen

Gdy jest dostępna aktualizacja w celu oceny, zostanie wyświetlony powiadomienie i będzie można zaakceptować aktualizację lub odroczyć ją na później.

Dostępne są aktualizacje dla formularzy oceniania opartych na szablonach firmy Microsoft, takich jak przeznaczone do używania z Microsoft 365. Jeśli Twoja organizacja używa szablonów uniwersalnych do oceny innych produktów, dziedziczenie może nie być obsługiwane. Aby uzyskać więcej informacji, zobacz [Rozszerzanie szablonów formularzy oceniania](compliance-manager-templates-extend.md).

### <a name="what-causes-an-update"></a>Co powoduje aktualizację

Aktualizacja oceny występuje w przypadku zmian szablonu źródłowego, które wpływają na wynik. Zmiany mogą obejmować dopasowywanie mapowania kontrolek lub innych wskazówek na podstawie zmian prawnych lub zmian w produktach. Aktualizacje oceny mogą pochodzić od Twojej organizacji (na przykład w przypadku zmodyfikowania szablonu niestandardowego [) oraz](compliance-manager-templates-modify.md) od firmy Microsoft.

Jeśli firma Microsoft aktualizuje rozszerzony szablon Menedżera zgodności, twoja ocena odziedziczy te aktualizacje po ich zaakceptowaniu. Podczas rozszerzonej oceny zostaną zachowają dodatkowe atrybuty zastosowane do oceny.

W przypadku niestandardowych formularzy oceniania nie są odbierane żadne aktualizacje szablonów od firmy Microsoft. Oceny niestandardowe mogą otrzymywać aktualizacje działań udoskonalania, ale wszelkie aktualizacje firmy Microsoft dotyczące kontrolowania mapowania między ocenami i działaniami udoskonalania nie mają zastosowania do szablonów niestandardowych.

> [!NOTE]
> Aktualizacje oceniania mają zastosowanie tylko na poziomie grupy. Jeśli masz dwie oceny z tego samego szablonu, które istnieją w dwóch różnych grupach, każda ocena będzie zawierała powiadomienie o oczekującej aktualizacji i musisz zaakceptować aktualizację każdej oceny w poszczególnych grupach.

#### <a name="where-youll-see-assessment-update-notifications"></a>Gdzie są wyświetlane powiadomienia o aktualizacjach oceny

Na stronie szczegółów oceny jest również **pokazana** etykieta Oczekująca aktualizacja obok oceny z aktualizacją. Wybierz tę ocenę, aby uzyskać dostęp do jej strony szczegółów.

Komunikat w górnej części strony szczegółów oceny pokazuje, że jest dostępna aktualizacja dla tego oceniania. Wybierz przycisk **Sprawdź aktualizację** na banerze, aby przejrzeć określone zmiany i zaakceptować lub odroczyć aktualizację.

Strona szczegółów oceny może również zawierać działania udoskonaleń z **etykietą** Oczekująca aktualizacja. Te aktualizacje dotyczą konkretnych zmian w samych działaniach udoskonalania i muszą być akceptowane oddzielnie. Odwiedź [stronę Akceptowanie aktualizacji, aby udoskonalić działania](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) , aby dowiedzieć się więcej.

#### <a name="review-update-to-accept-or-defer"></a>Przejrzyj aktualizację, aby zaakceptować lub odroczyć

Po wybraniu **przycisku Sprawdź aktualizację** na stronie szczegółów oceny po prawej stronie ekranu pojawi się okienko wysuwu. W okienku wysuwu znajduje się poniżej najważniejsze informacje o oczekującej aktualizacji:

- Tytuł szablonu
- Źródło aktualizacji (firma Microsoft, Twoja organizacja lub określony użytkownik)
- Data utworzenia aktualizacji
- Omówienie wyjaśniające aktualizację
- Szczegółowe informacje na temat zmian, w tym wpływ na ocenę zgodności, ilość postępu w kierunku ukończenia oceny i konkretną liczbę zmian w działaniach usprawnień i kontrolkach.

Wybranie **linku Zaktualizowano** szablon spowoduje pobranie pliku Excel zawierającego dane kontrolek dla wersji szablonu z oczekującymi aktualizacjami. Wybranie **linku Bieżący** szablon pobiera plik istniejącego szablonu bez zmian.

Aby zaakceptować aktualizację i wprowadzić zmiany w ocenach, wybierz pozycję **Zaakceptuj aktualizację**. Zaakceptowane zmiany są trwałe.

Jeśli wybierzesz **pozycję Anuluj**, aktualizacja nie zostanie zastosowana do oceny. Jednak do czasu zaakceptowania aktualizacji nadal będziesz widzieć  powiadomienie o oczekującej aktualizacji.

**Dlaczego zalecamy akceptowanie aktualizacji**

Zaakceptowanie aktualizacji pomaga zapewnić, że masz najbardziej zaktualizowane wskazówki dotyczące korzystania z rozwiązań i podejmowania odpowiednich działań udoskonalania, aby pomóc Ci w spełnianiu wymagań certyfikacji.

**Dlaczego warto odroczyć aktualizację**

Jeśli jesteś w trakcie oceniania, warto upewnić się, że praca nad nim została zakończona, zanim zaakceptujesz aktualizację oceny, która może zakłócić mapowanie kontroli. Aktualizację można odroczyć na później, wybierając pozycję **Anuluj** w okienku wysuwanej aktualizacji recenzji.

## <a name="export-an-assessment-report"></a>Eksportowanie raportu z oceny

Możesz wyeksportować ocenę do pliku Excel dla uczestników projektu zgodności w organizacji lub dla zewnętrznych audytorów i źródeł danych. Na stronie szczegółów oceny wybierz przycisk Generuj raport w górnej części strony, co powoduje utworzenie Excel pliku, który możesz zapisać i udostępnić.

Raport jest migawką oceny od daty i czasu eksportu. Zawiera on szczegóły dotyczące kontrolek zarządzanych przez Ciebie i firmę Microsoft, w tym stan implementacji, datę testu i wyniki testów.

## <a name="delete-an-assessment"></a>Usuwanie oceny

Usunięcie oceny powoduje usunięcie jej z listy na stronie oceny. Zwróć uwagę na następujące ważne kwestie dotyczące usuwania ocen:

- **Usunięcie oceny jest trwałe; nie można go odzyskać.** Jeśli chcesz ponownie użyć tej samej oceny, musisz utworzyć ją ponownie.
- Jeśli działania udoskonalania w ramach oceny nie są widoczne w żadnej innej ocenie, zostaną one usunięte po usunięciu oceny.
- Zalecamy [wyeksportowanie raportu z](#export-an-assessment-report) oceny przed jej trwałym usunięciem.

Aby usunąć formularz oceniania, wykonaj poniższe czynności:

1. Na stronie **oceny** wybierz testy, które chcesz usunąć, aby otworzyć stronę szczegółów tego oceniania.

2. Wybierz **pozycję Usuń** ocenę w prawym górnym rogu ekranu.

3. Zostanie wyświetlone okno z prośbą o potwierdzenie trwałego usunięcia oceny. Wybierz **pozycję Usuń ocenę** , aby zamknąć okno. Zostanie otwarte okno potwierdzenia usunięcia oceny z Menedżera zgodności.

> [!NOTE]
> Nie można usunąć wszystkich swoich ocen. Aby Menedżer zgodności działał prawidłowo, organizacje muszą mieć co najmniej jedną ocenę. Jeśli ocena, którą chcesz usunąć, jest jedyną oceną, dodaj kolejną ocenę przed jej usunięciem.
