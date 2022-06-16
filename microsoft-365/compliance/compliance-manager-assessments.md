---
title: Tworzenie ocen i zarządzanie nimi w programie Microsoft Purview Compliance Manager
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
description: Twórz oceny w programie Microsoft Purview Compliance Manager, aby ułatwić spełnienie wymagań dotyczących przepisów i certyfikatów, które są ważne dla Organizacji.
ms.openlocfilehash: cb2d90bf8dfbdcb2ec2ca534d1659a19d27998bc
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115746"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Tworzenie ocen i zarządzanie nimi w menedżerze zgodności

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**W tym artykule:** Dowiedz się, jak dostosować Menedżera zgodności dla organizacji, tworząc **oceny** i zarządzając nimi. W tym artykule przedstawiono sposób tworzenia ocen, organizowania ich w **grupy**, pracy z **kontrolkami**, akceptowania aktualizacji i eksportowania **raportów** oceny.

## <a name="introduction-to-assessments"></a>Wprowadzenie do ocen

Menedżer zgodności ułatwia tworzenie ocen, które oceniają zgodność z przepisami branżowymi i regionalnymi, które mają zastosowanie do Organizacji. Oceny są oparte na strukturze szablonów oceny, które zawierają niezbędne mechanizmy kontroli, działania ulepszeń i, w stosownych przypadkach, działania firmy Microsoft na potrzeby ukończenia oceny. Skonfigurowanie najbardziej odpowiednich ocen dla organizacji może pomóc w zaimplementowaniu zasad i procedur operacyjnych w celu ograniczenia ryzyka zgodności.

Wszystkie oceny są wymienione na karcie oceny w Menedżerze zgodności. Dowiedz się więcej o [tym, jak filtrować widok ocen i interpretować stany stanu](compliance-manager-setup.md#assessments-page).

> [!IMPORTANT]
> Szablony dostępne dla organizacji na potrzeby tworzenia ocen zależą od umowy licencyjnej. [Przejrzyj szczegóły licencjonowania](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="data-protection-baseline-default-assessment"></a>Domyślna ocena punktu odniesienia ochrony danych

Aby rozpocząć pracę, firma Microsoft udostępnia **domyślną** ocenę w Menedżerze zgodności dla **punktu odniesienia Microsoft 365 ochrony danych**. Ta ocena bazowa obejmuje zestaw mechanizmów kontroli kluczowych przepisów i standardów dotyczących ochrony danych i ogólnego ładu danych. Ten punkt odniesienia czerpie przede wszystkim z NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) i ISO (Międzynarodowa Organizacja Standaryzacji), a także z FedRAMP (Federal Risk and Authorization Management Program) i RODO (ogólne rozporządzenie o ochronie danych Unii Europejskiej).

Ta ocena służy do obliczania początkowego wyniku zgodności przy pierwszym wystąpieniu menedżera zgodności przed skonfigurowaniem innych ocen. Menedżer zgodności zbiera początkowe sygnały z rozwiązań Microsoft 365. Na pierwszy rzut oka zobaczysz, jak twoja organizacja działa w stosunku do kluczowych standardów i przepisów dotyczących ochrony danych, a także zobaczysz sugerowane działania ulepszeń do podjęcia.

Menedżer zgodności staje się bardziej pomocny podczas tworzenia własnych ocen i zarządzania nimi w celu spełnienia konkretnych potrzeb organizacji.

## <a name="understand-groups-before-creating-assessments"></a>Omówienie grup przed utworzeniem ocen

Podczas tworzenia oceny należy przypisać ją do grupy. Grupy to kontenery, które umożliwiają organizowanie ocen w sposób logiczny, na przykład według roku lub regulacji, albo na podstawie działów lub lokalizacji geograficznych organizacji. Dlatego zalecamy zaplanowanie strategii grupowania przed utworzeniem ocen.

Poniżej przedstawiono przykłady dwóch grup i ich podstawowych ocen:

- **Ocena FFIEC IS 2020**
  - FFIEC IS
- **Ocena bezpieczeństwa danych i prywatności**
  - ISO 27001:2013
  - ISO 27018:2014

Różne oceny w grupie lub grupach mogą udostępniać akcje poprawy. Akcje ulepszania mogą być zmianami wprowadzonymi w rozwiązaniach technicznych zamapowanych na dzierżawę, takimi jak włączenie uwierzytelniania dwuskładnikowego lub akcje inne niż techniczne wykonywane poza systemem, takie jak wprowadzenie nowych zasad miejsca pracy. Wszelkie aktualizacje w szczegółach lub stanie, które wprowadzasz w akcji poprawy technicznej, zostaną odebrane przez oceny we wszystkich grupach. Aktualizacje akcji ulepszeń nietechnacyjnych zostaną rozpoznane przez oceny w grupie, w której je zastosujesz. Dzięki temu można zaimplementować jedną akcję poprawy i jednocześnie spełnić kilka wymagań.

### <a name="create-a-group"></a>Tworzenie grupy

Grupę można utworzyć podczas tworzenia nowej oceny. Nie można tworzyć grup jako jednostek autonomicznych.

### <a name="what-to-know-when-working-with-groups"></a>Co należy wiedzieć podczas pracy z grupami

- Grupa musi zawierać co najmniej jedną ocenę.
- Nazwy grup muszą być unikatowe w organizacji.
- Grupy nie mają właściwości zabezpieczeń. Wszystkie uprawnienia są skojarzone z ocenami.
- Po dodaniu oceny do grupy nie można zmienić grupowania.
- Jeśli dodasz nową ocenę do istniejącej grupy, typowe informacje z ocen w tej grupie zostaną skopiowane do nowej oceny.
- Pokrewne mechanizmy kontroli oceny w różnych ocenach w tej samej grupie są automatycznie aktualizowane po zakończeniu.
- Grupy mogą zawierać oceny dla tego samego certyfikatu lub tej samej regulacji, ale każda grupa może zawierać tylko jedną ocenę dla określonej pary certyfikacji produktu. Na przykład grupa nie może zawierać dwóch ocen dla Office 365 i NIST CSF. Grupa może zawierać wiele ocen dla tego samego produktu tylko wtedy, gdy odpowiedni certyfikat lub regulacja dla każdego z nich jest inna.
- Usunięcie oceny powoduje przerwanie relacji między tą oceną a grupą.
- Nie można usunąć grup.

## <a name="understand-templates-before-creating-assessments"></a>Omówienie szablonów przed utworzeniem ocen

Szablony oceny zawierają zalecenia dotyczące kontroli i akcji dla ocen na podstawie certyfikatów dla różnych przepisów i standardów dotyczących prywatności. Twoja organizacja zaczyna od co najmniej jednego i prawdopodobnie większej **liczby dostępnych** szablonów do użycia, w zależności od umowy licencyjnej. Twoja organizacja może również zakupić dodatkowe szablony **premium** .

Każdy szablon istnieje w dwóch wersjach: jeden do użytku z Microsoft 365 (lub innymi produktami firmy Microsoft w miarę dostępności) i uniwersalną wersją, którą można dostosować do oceny innych używanych produktów. Możesz wybrać odpowiedni typ szablonu dla produktu, który chcesz ocenić.

Więcej szczegółów na temat szablonów można znaleźć w [temacie Dowiedz się więcej o szablonach oceny w menedżerze zgodności](compliance-manager-templates.md).

## <a name="create-assessments"></a>Tworzenie ocen

> [!NOTE]
> Oceny mogą tworzyć i modyfikować tylko użytkownicy z rolą administratora globalnego, administracji menedżera zgodności lub oceny menedżera zgodności. Dowiedz się więcej o [rolach i uprawnieniach](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

Przed rozpoczęciem upewnij się, że wiesz, do której grupy ją przypiszesz, lub przygotuj się do utworzenia nowej grupy na potrzeby tej oceny. Przeczytaj szczegółowe informacje o [grupach i ocenach](#understand-groups-before-creating-assessments).

Aby utworzyć ocenę, użyjesz procesu z przewodnikiem, aby wybrać szablon i wyznaczyć skojarzony produkt. Na stronie **Oceny** zalecamy rozpoczęcie od **pozycji Dodaj zalecane oceny**, co pomaga zidentyfikować i szybko skonfigurować najbardziej odpowiednie oceny dla organizacji jednocześnie. Możesz również skonfigurować oceny pojedynczo, wybierając pozycję **Dodaj ocenę**. Wykonaj poniższe kroki, aby rozpocząć ocenę kompilowania.

#### <a name="create-assessments-based-on-recommendations-for-your-org-type"></a>Tworzenie ocen na podstawie zaleceń dotyczących typu organizacji

Menedżer zgodności może wskazać, które oceny mogą być najbardziej istotne dla Twojej organizacji. Po podaniu podstawowych informacji na temat branży i lokalizacji organizacji zalecamy użycie szablonów z naszej biblioteki ponad 300 szablonów. Wystarczy wybrać spośród zalecanych szablonów, aby szybko skonfigurować wiele ocen jednocześnie.

Aby utworzyć co najmniej jedną ocenę na podstawie naszych zaleceń, wybierz pozycję **Dodaj zalecane oceny** na stronie **Oceny** i wykonaj następujące kroki:

- Wybierz co najmniej jedną branżę identyfikującą organizację, a następnie wybierz pozycję **Dalej**
- Wybierz co najmniej jeden region dla lokalizacji organizacji, a następnie wybierz pozycję **Dalej**
- Na ekranie **Wybieranie oceny** wybierz strzałkę listy rozwijanej obok pozycji **Zalecane szablony** , aby wyświetlić listę ocen, które według nas dotyczą Twojej organizacji. Zaznacz pola obok szablonów, których chcesz użyć do tworzenia ocen, a następnie wybierz pozycję **Dalej**.
- Przejrzyj ostateczne wybory i wybierz pozycję **Dodaj zalecane oceny,** aby utworzyć nowe oceny.

#### <a name="create-an-assessment-using-a-guided-process"></a>Tworzenie oceny przy użyciu procesu z przewodnikiem

1. Na stronie **Oceny** wybierz pozycję **Dodaj ocenę**. Spowoduje to przejście do kreatora tworzenia oceny.

2. Na ekranie **Szablon podstawowy** wybierz pozycję **Wybierz szablon** , aby wybrać szablon do oceny.

3. W okienku wysuwanym wybierz szablon dla rozporządzenia lub certyfikatu, na którym należy oprzeć ocenę. Lista szablonów podzielonych na kategorie uwzględnione i premium ([uzyskaj szczegóły](compliance-manager-templates.md#template-availability-and-licensing)). Licznik **Szablony aktywowane/licencjonowane** w górnej części okienka wysuwanego pokazuje, jak szablony mogą być używane poza całkowitą liczbą dostępnych lub używanymi przez organizację ([dowiedz się więcej](compliance-manager-templates.md#active-and-inactive-templates)). Wybierz przycisk radiowy obok wybranego szablonu, a następnie wybierz pozycję **Zapisz**. Wrócisz do ekranu **szablonu podstawowego** , na którym możesz przejrzeć szczegóły szablonu, a następnie kontynuować, wybierając pozycję **Dalej**.

4. **Produkt, nazwa i grupa:** Ustaw te właściwości, aby zidentyfikować ocenę, wybierz produkt, który będzie oceniany, i przypisz go do grupy.

    - **Produkt**: wybierz produkt, do których ma zostać zastosowana ocena. Jeśli używasz szablonu firmy Microsoft, takiego jak przeznaczony dla Microsoft 365, to pole zostanie wypełnione, aby wskazać odpowiedni produkt i nie można go zmienić. Jeśli używasz szablonu uniwersalnego, wybierz, czy tworzysz tę ocenę dla nowego produktu, czy dla produktu niestandardowego, który został już zdefiniowany w Menedżerze zgodności. Jeśli wybierzesz nowy produkt, wprowadź jego nazwę. Należy pamiętać, że nie można wybrać wstępnie zdefiniowanego produktu firmy Microsoft podczas korzystania z szablonu uniwersalnego.
    - **Nazwa oceny**: wprowadź nazwę oceny w polu **Nazwa oceny** . Nazwy ocen muszą być unikatowe w grupach. Jeśli nazwa oceny jest zgodna z nazwą innej oceny w danej grupie, zostanie wyświetlony błąd z prośbą o utworzenie innej nazwy.
    - **Grupa**: Przypisz ocenę do grupy. Możesz wykonać jedną z następujących czynności:
        - Wybierz pozycję **Użyj istniejącej grupy** , aby przypisać ją do już utworzonej grupy. Lub
        - Wybierz pozycję **Utwórz nową grupę** , aby utworzyć nową grupę i przypisać do niej tę ocenę:
            - Określ nazwę grupy i wprowadź ją w polu poniżej przycisku radiowego.
            - Dane **z istniejącej grupy**, takie jak szczegóły implementacji i testowania i dokumenty, można skopiować, wybierając odpowiednie pola.

    Po zakończeniu wybierz pozycję **Dalej**.

5. **Przejrzyj i zakończ:** Przejrzyj wybrane opcje i wprowadź wszelkie niezbędne zmiany. Gdy wszystko będzie gotowe, wybierz pozycję **Utwórz ocenę**.

Następny ekran potwierdza, że ocena została utworzona. Po wybraniu pozycji **Gotowe** nastąpi przekierowanie do strony szczegółów nowej oceny.

Jeśli po wybraniu pozycji **Utwórz ocenę** zostanie wyświetlony ekran **Ocena nie powiodła się**, wybierz pozycję **Spróbuj ponownie**, aby ponownie utworzyć ocenę.

Nazwę oceny można zmienić po jej utworzeniu, wybierając przycisk **Edytuj nazwę** w prawym górnym rogu [strony szczegółów oceny](#monitor-assessment-progress-and-controls).

## <a name="monitor-assessment-progress-and-controls"></a>Monitorowanie postępu i kontroli oceny

Każda ocena ma stronę szczegółów, która zapewnia wgląd w postęp w ukończeniu oceny. Na stronie przedstawiono postęp w wykonywaniu kontrolek oraz stan testu akcji poprawy klucza w ramach tych kontrolek.

### <a name="overview-tab"></a>Karta Przegląd

Karta Przegląd zawiera wykres przedstawiający procent ukończenia oceny. Ten wykres zawiera podział punktów z posiadanych akcji i punktów z akcji należących do firmy Microsoft, dzięki czemu możesz zobaczyć, ile punktów potrzebujesz do ukończenia oceny.

Kluczowe akcje poprawy kontroli w ocenie są wymienione w kolejności największego potencjalnego wpływu na zdobywanie punktów. Skojarzony wykres zawiera szczegółowe informacje o zagregowanym stanie testu akcji poprawy, dzięki czemu można szybko ocenić, co zostało przetestowane i co należy jeszcze zrobić.

Aby uzyskać dostęp do poszczególnych akcji poprawy, odwiedź kartę **Kontrolki** lub Kartę **Twoje akcje poprawy** .

### <a name="controls-tab"></a>Karta Kontrolki

Na karcie kontrolek są wyświetlane szczegółowe informacje dotyczące każdej kontrolki zamapowane na ocenę. Wykres **podziału stanu kontroli** pokazuje stan kontrolek według rodziny, dzięki czemu można szybko zobaczyć, które grupy kontrolek wymagają uwagi.

Pod wykresem tabela zawiera szczegółowe informacje o każdej kontrolce w ramach oceny. Kontrolki są grupowane według rodziny kontroli. Rozwiń każdą nazwę rodziny, aby wyświetlić poszczególne kontrolki, które zawiera. Informacje wymienione dla każdej kontrolki obejmują:

- **Tytuł kontrolki**
- **Stan**: odzwierciedla stan testu akcji poprawy w kontrolce
  - **Przekazano** — wszystkie akcje poprawy mają stan testu "przeszedł" lub co najmniej jeden jest przekazywany, a pozostałe są "poza zakresem"
  - **Niepowodzenie** — co najmniej jedna akcja poprawy ma stan testu "niepowodzenie"
  - **Brak** — wszystkie akcje poprawy nie zostały przetestowane
  - **Poza zakresem** — wszystkie akcje poprawy są poza zakresem tej oceny
  - **W toku** — akcje poprawy mają stan inny niż wymienione powyżej, które mogą obejmować "w toku", "częściowy kredyt" lub "niewykryty"
- **Identyfikator kontroli**: numer identyfikacyjny kontrolki przypisany przez odpowiednie rozporządzenie, standard lub zasady
- **Osiągnięte punkty**: liczba punktów uzyskanych przez wykonanie akcji, z łącznej liczby osiągalnych punktów
- **Twoje akcje**: liczba wykonanych akcji z łącznej liczby akcji do wykonania
- **Akcje firmy Microsoft**: liczba akcji wykonanych przez firmę Microsoft

Aby wyświetlić szczegóły kontrolki, wybierz ją z wiersza w tabeli. Na stronie szczegółów kontrolki jest wyświetlany wykres wskazujący stan testu akcji w ramach tej kontrolki. Tabela poniżej wykresu przedstawia kluczowe akcje poprawy dla tej kontrolki.

Wybierz akcję poprawy z listy, aby przejść do szczegółów akcji poprawy. Na stronie szczegółów są wyświetlane informacje o stanie testu i implementacji oraz uruchamianie w zalecanym rozwiązaniu.

### <a name="your-improvement-actions-tab"></a>Karta akcji poprawy

Na karcie akcji ulepszania są wyświetlane wszystkie kontrolki w ocenie zarządzane przez organizację. Pasek stanu zawiera szczegółowe informacje o zagregowanym stanie testu akcji poprawy w ocenie, dzięki czemu można szybko ocenić, co zostało przetestowane i co należy jeszcze zrobić. Poniżej paska znajduje się pełna lista akcji poprawy i kluczowych szczegółów, w tym: stan testu, liczba potencjalnych i uzyskanych punktów, skojarzone przepisy i standardy, odpowiednie rozwiązanie, typ akcji i rodzina kontroli. Dowiedz się więcej o [tym, jak akcje przyczyniają się do oceny zgodności](compliance-score-calculation.md#action-types-and-points).

Wybierz akcję poprawy, aby wyświetlić jej stronę szczegółów, a następnie wybierz link **Uruchom teraz** , aby otworzyć rozwiązanie do podjęcia akcji.

### <a name="microsoft-actions-tab"></a>Karta Akcje firmy Microsoft

Zostanie wyświetlona karta Akcje firmy Microsoft dla ocen opartych na szablonach, które obsługują produkty firmy Microsoft. Zawiera listę wszystkich akcji w ocenie, które są zarządzane przez firmę Microsoft. Lista zawiera kluczowe szczegóły akcji, w tym: stan testu, punkty, które przyczyniają się do ogólnego wyniku zgodności, skojarzone przepisy i standardy, odpowiednie rozwiązanie, typ akcji i rodzina kontroli. Wybierz akcję poprawy, aby wyświetlić jej stronę szczegółów.

Dowiedz się więcej na temat [sposobu śledzenia i śledzenia akcji ulepszeń oraz śledzenia ich.](compliance-score-calculation.md)

## <a name="accept-updates-to-assessments"></a>Akceptowanie aktualizacji ocen

Gdy aktualizacja jest dostępna dla oceny, zobaczysz powiadomienie i będziesz mieć możliwość zaakceptowania aktualizacji lub odroczenia jej na później.

Aktualizacje są dostępne dla ocen na podstawie szablonów firmy Microsoft, takich jak te przeznaczone do użycia z Microsoft 365. Jeśli Twoja organizacja używa szablonów uniwersalnych do oceny innych produktów, dziedziczenie może nie być obsługiwane. Aby uzyskać więcej informacji, zobacz [Rozszerzanie szablonów oceny](compliance-manager-templates-extend.md).

### <a name="what-causes-an-update"></a>Co powoduje aktualizację

Aktualizacja oceny występuje, gdy istnieją podstawowe zmiany szablonu, które mają wpływ na ocenianie. Zmiany mogą obejmować dostosowanie mapowania kontroli lub innych wskazówek na podstawie zmian w przepisach lub zmian produktów. Aktualizacje oceny mogą pochodzić z twojej organizacji (na przykład podczas [modyfikowania szablonu niestandardowego](compliance-manager-templates-modify.md)), a także od firmy Microsoft.

Jeśli firma Microsoft zaktualizuje rozszerzony szablon programu Compliance Manager, ocena odziedziczy te aktualizacje po ich zaakceptowaniu. Ocena zachowa dodatkowe atrybuty zastosowane do oceny po jej przedłużeniu.

Utworzone niestandardowe oceny nie otrzymują żadnych aktualizacji szablonu od firmy Microsoft. Oceny niestandardowe mogą otrzymywać aktualizacje akcji poprawy, ale wszelkie aktualizacje firmy Microsoft umożliwiające kontrolowanie mapowania między ocenami i akcjami poprawy nie mają zastosowania do szablonów niestandardowych.

> [!NOTE]
> Aktualizacje ocen mają zastosowanie tylko na poziomie grupy. Jeśli masz dwie oceny utworzone na podstawie tego samego szablonu, który istnieje w dwóch różnych grupach, każda ocena będzie mieć oczekujące powiadomienie o aktualizacji i musisz zaakceptować aktualizację każdej oceny w odpowiedniej grupie indywidualnie.

#### <a name="where-youll-see-assessment-update-notifications"></a>Gdzie zostaną wyświetlone powiadomienia o aktualizacji oceny

Na stronie szczegółów oceny jest również wyświetlana etykieta **Oczekująca aktualizacja** obok oceny z aktualizacją. Wybierz tę ocenę, aby przejść do jej strony szczegółów.

Komunikat w górnej części strony szczegółów oceny pokazuje, że dla tej oceny jest dostępna aktualizacja. Wybierz przycisk **Przejrzyj aktualizację** na banerze, aby przejrzeć określone zmiany i zaakceptować lub odroczyć aktualizację.

Strona szczegółów oceny może również wyświetlać listę akcji poprawy, które mają obok nich etykietę **Oczekująca aktualizacja** . Te aktualizacje dotyczą konkretnych zmian w samych akcjach ulepszania i muszą być akceptowane oddzielnie. Odwiedź stronę [Akceptowanie aktualizacji akcji ulepszania,](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) aby dowiedzieć się więcej.

#### <a name="review-update-to-accept-or-defer"></a>Przejrzyj aktualizację, aby zaakceptować lub odroczyć

Po wybraniu pozycji **Przejrzyj aktualizację** na stronie szczegółów oceny po prawej stronie ekranu zostanie wyświetlone okienko wysuwane. Okienko wysuwane zawiera poniżej kluczowe szczegóły dotyczące oczekującej aktualizacji:

- Tytuł szablonu
- Źródło aktualizacji (Microsoft, Twoja organizacja lub określony użytkownik)
- Data utworzenia aktualizacji
- Przegląd objaśniający aktualizację
- Szczegółowe informacje o zmianach, w tym wpływ na wynik zgodności, postęp w ukończeniu oceny oraz określoną liczbę zmian w akcjach poprawy i kontrolkach.

Wybranie linku **Zaktualizowany szablon** spowoduje pobranie pliku Excel zawierającego dane sterujące dla wersji szablonu z oczekującymi aktualizacjami. Wybranie linku **Bieżący szablon** powoduje pobranie pliku istniejącego szablonu bez zmian.

Aby zaakceptować aktualizację i wprowadzić zmiany w ocenie, wybierz pozycję **Zaakceptuj aktualizację**. Zaakceptowane zmiany są trwałe.

Jeśli wybierzesz opcję **Anuluj**, aktualizacja nie zostanie zastosowana do oceny. Będziesz jednak nadal widzieć powiadomienie **Oczekujące na aktualizację** do momentu zaakceptowania aktualizacji.

**Dlaczego zalecamy akceptowanie aktualizacji**

Akceptowanie aktualizacji pomaga zapewnić, że masz najbardziej zaktualizowane wskazówki dotyczące korzystania z rozwiązań i podejmowania odpowiednich działań ulepszeń, które pomogą Ci spełnić wymagania dotyczące certyfikacji.

**Dlaczego warto odroczyć aktualizację**

Jeśli jesteś w trakcie oceny, możesz upewnić się, że zakończono nad nią pracę, zanim zaakceptujesz aktualizację oceny, która może zakłócić mapowanie kontroli. Możesz odroczyć aktualizację na później, wybierając pozycję **Anuluj** w okienku wysuwanej aktualizacji przeglądu.

## <a name="export-an-assessment-report"></a>Eksportowanie raportu oceny

Ocenę można wyeksportować do pliku Excel dla osób biorących udział w projekcie zgodności w organizacji lub zewnętrznych audytorów i regulatorów. Na stronie szczegółów oceny wybierz przycisk **Generuj raport** w górnej części strony, który tworzy plik Excel, który można zapisać i udostępnić.

Raport jest migawką oceny na dzień i godzinę eksportu. Zawiera szczegółowe informacje dotyczące kontrolek zarządzanych zarówno przez Ciebie, jak i firmę Microsoft, w tym stan implementacji, datę testu i wyniki testu.

## <a name="delete-an-assessment"></a>Usuwanie oceny

Usunięcie oceny powoduje usunięcie jej z listy na stronie ocen. Zwróć uwagę na te ważne kwestie dotyczące usuwania ocen:

- **Usunięcie oceny jest trwałe; nie można go odzyskać.** Jeśli chcesz ponownie użyć tej samej oceny, musisz ją ponownie utworzyć.
- Jeśli akcje poprawy w ocenie nie pojawią się w żadnej innej ocenie, zostaną usunięte po usunięciu oceny.
- Zalecamy [wyeksportowanie raportu](#export-an-assessment-report) oceny przed jego trwałym usunięciem.

Aby usunąć ocenę, wykonaj poniższe kroki:

1. Na stronie **ocen** wybierz ocenę, którą chcesz usunąć, aby otworzyć stronę szczegółów oceny.

2. Wybierz pozycję **Usuń ocenę** w prawym górnym rogu ekranu.

3. Zostanie wyświetlone okno z prośbą o potwierdzenie, że chcesz trwale usunąć ocenę. Wybierz pozycję **Usuń ocenę** , aby zamknąć okno. Zostanie wyświetlone okno z potwierdzeniem usunięcia oceny z Menedżera zgodności.

> [!NOTE]
> Nie można usunąć wszystkich ocen. Organizacje potrzebują co najmniej jednej oceny, aby Menedżer zgodności działał prawidłowo. Jeśli ocena, którą chcesz usunąć, jest jedyną, dodaj kolejną ocenę przed usunięciem drugiej oceny.
