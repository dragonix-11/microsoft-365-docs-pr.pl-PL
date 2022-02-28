---
title: Wprowadzenie do podstawowych spraw zbierania elektronicznych materiałów dowodowych w programie Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: W tym artykule opisano, jak rozpocząć korzystanie z podstawowych funkcji zbierania elektronicznych materiałów dowodowych w Microsoft 365. Po przypisaniu uprawnień zbierania elektronicznych materiałów dowodowych i utworzeniu sprawy możesz dodawać członków, tworzyć zbierania elektronicznych materiałów dowodowych, a następnie wyszukiwać i eksportować zawartość, która jest istotne dla prowadzonego badania.
ms.openlocfilehash: 0e6e29ced6e6dfb535d169cbf5c41193d5d46cfd
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990504"
---
# <a name="get-started-with-core-ediscovery-in-microsoft-365"></a>Wprowadzenie do zbierania elektronicznych materiałów dowodowych w programie Microsoft 365

Podstawowe usługi zbierania elektronicznych materiałów dowodowych w programie Microsoft 365 zapewniają podstawowe narzędzie zbierania elektronicznych materiałów dowodowych, za pomocą których organizacje mogą wyszukiwać i eksportować zawartość w usługach Microsoft 365 i Office 365. Za pomocą funkcji Podstawowe zbierania elektronicznych materiałów dowodowych możesz także umieścić w stanie przechowywania zawartości lokalizacje zawartości, takie jak skrzynki pocztowe usługi Exchange, witryny usługi SharePoint, konta OneDrive i Microsoft Teams. Do wdrożenia podstawowego zbierania elektronicznych materiałów dowodowych nie jest wymagane nic, ale istnieje kilka wstępnych zadań, które musi wykonać administrator IT i menedżer zbierania elektronicznych materiałów dowodowych, zanim Twoja organizacja będzie w stanie zacząć korzystać z podstawowych funkcji zbierania elektronicznych materiałów dowodowych w celu przeszukiwania, eksportowania i zachowywania zawartości.

W tym artykule omówiono czynności niezbędne do skonfigurowania podstawowego zbierania elektronicznych materiałów dowodowych. Obejmuje to zapewnienie odpowiedniego licencjonowania wymaganego do uzyskiwania dostępu do podstawowych zbierania elektronicznych materiałów dowodowych i umieszczenie miejsc zbierania elektronicznych materiałów dowodowych w lokalizacjach zawartości, a także przypisanie uprawnień do zespołu IT, prawnego i badania w celu uzyskiwania dostępu do spraw i zarządzania nimi. Ten artykuł zawiera również ogólne omówienie korzystania ze spraw w celu wyszukiwania i eksportowania zawartości.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Krok 1. Weryfikowanie i przypisywanie odpowiednich licencji

Licencjonowanie dla podstawowego zbierania elektronicznych materiałów dowodowych wymaga odpowiedniej subskrypcji organizacji i licencjonowania na użytkownika.

- **Subskrypcja organizacji:** Aby uzyskać dostęp do core eDiscovery w p Centrum zgodności platformy Microsoft 365 i korzystać z funkcji blokowania i eksportowania, Twoja organizacja musi mieć subskrypcję usługi Microsoft 365 E3 lub Office 365 E3 lub wyższą. Microsoft 365 Frontline organizacje muszą mieć subskrypcję F5.

- **Licencjonowanie na użytkownika:** Aby umieścić wstrzymywanie zbierania elektronicznych materiałów dowodowych w skrzynkach pocztowych i witrynach, użytkownicy muszą mieć przypisaną jedną z następujących licencji, w zależności od subskrypcji twojej organizacji:

  - Licencja Microsoft 365 E3 lub Office 365 E3 lub wyższa

   LUB

  - Office 365 E1 z licencją Exchange Online Plan 2 lub Exchange Online — archiwum dodatku

   LUB

  - Microsoft 365 Frontline F5 Compliance lub F5 Security & Security & Compliance  

  AND

  - Office 365 E1 z licencją dodatku SharePoint Online (plan 2) lub OneDrive dla Firm Plan 2
  
  Aby uzyskać informacje na temat przypisywania licencji, zobacz [Przypisywanie licencji do użytkowników](../admin/manage/assign-licenses-to-users.md).

Aby uzyskać informacje na temat licencjonowania:

- Pobierz i zobacz sekcję zbierania elektronicznych materiałów dowodowych i inspekcji w [Microsoft 365 porównania.](https://go.microsoft.com/fwlink/?linkid=2139145)

- Zobacz opis [usługi Centrum & zgodności](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

## <a name="step-2-assign-ediscovery-permissions"></a>Krok 2. Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych

Aby uzyskać dostęp do core eDiscovery lub zostać dodany jako członek podstawowej sprawy zbierania elektronicznych materiałów dowodowych, użytkownik musi mieć odpowiednie uprawnienia. W szczególności należy dodać użytkownika jako członka grupy ról Menedżer zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365. Członkowie tej grupy ról mogą tworzyć podstawowe sprawy zbierania elektronicznych materiałów dowodowych i zarządzać nimi. Mogą dodawać i usuwać członków, tworzyć i edytować wyszukiwania użytkowników oraz eksportować zawartość ze sprawy zbierania elektronicznych materiałów dowodowych.

Wykonaj następujące czynności, aby dodać użytkowników do grupy ról Menedżer zbierania elektronicznych materiałów dowodowych:

1. Przejdź do tego Centrum zgodności platformy Microsoft 365 i zaloguj się przy użyciu poświadczeń administratora dla konta administratora w Twojej organizacji usługi Microsoft 365 lub Office 365 organizacji.

2. Na stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a> wybierz grupę ról **Menedżer zbierania** elektronicznych materiałów dowodowych.

3. Na stronie wysuwu Menedżera zbierania elektronicznych materiałów dowodowych kliknij pozycję **Edytuj** obok sekcji **Menedżer zbierania** elektronicznych materiałów dowodowych.

4. Na stronie **Wybieranie menedżera zbierania elektronicznych materiałów** dowodowych w kreatorze edytowania grupy ról kliknij pozycję **Wybierz menedżera zbierania elektronicznych materiałów dowodowych**.

5. Kliknij **pozycję** Dodaj, a następnie zaznacz pole wyboru dla wszystkich użytkowników, których chcesz dodać do grupy ról.

6. Kliknij **pozycję Dodaj** , aby dodać wybranych użytkowników, a następnie kliknij pozycję **Gotowe**.

7. Kliknij **pozycję** Zapisz, aby dodać użytkowników do grupy ról, a następnie kliknij przycisk **Zamknij** , aby ukończyć ten krok.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Więcej informacji na temat grupy ról Menedżer zbierania elektronicznych materiałów dowodowych

W grupie ról Menedżer zbierania elektronicznych materiałów dowodowych są dwie podgrupy. Różnica między tymi podgrupami zależy od zakresu.

- **Menedżer zbierania elektronicznych materiałów dowodowych**: Może wyświetlać podstawowe sprawy zbierania elektronicznych materiałów dowodowych i zarządzać nimi, które tworzą, lub do których należy. Jeśli inny menedżer zbierania elektronicznych materiałów dowodowych utworzy sprawę, ale nie doda drugiego menedżera zbierania elektronicznych materiałów dowodowych jako członka tej sprawy, drugi menedżer zbierania elektronicznych materiałów dowodowych nie będzie mógł wyświetlić ani otworzyć sprawy na stronie Podstawowe zbierania elektronicznych materiałów dowodowych w Centrum zgodności. Na ogół większość osób w organizacji może zostać dodana do podgrupy Menedżer zbierania elektronicznych materiałów dowodowych.

- **Administrator zbierania elektronicznych materiałów** dowodowych: może wykonywać wszystkie zadania związane z zarządzaniem sprawymi, które może wykonywać Menedżer zbierania elektronicznych materiałów dowodowych. Ponadto administrator zbierania elektronicznych materiałów dowodowych może:

  - Wyświetlanie wszystkich spraw wymienionych na stronie Podstawowe zbierania elektronicznych materiałów dowodowych.
  
  - Zarządzanie wszystkimi sprawymi w organizacji po dodaniu siebie jako członka do sprawy.

  - Uzyskiwanie dostępu do danych sprawy i eksportowanie ich dla dowolnej sprawy w organizacji.
  
  - Usuwanie członków ze sprawy zbierania elektronicznych materiałów dowodowych. Tylko administrator zbierania elektronicznych materiałów dowodowych może usuwać członków ze sprawy. Użytkownicy, którzy są członkami podgrupy Menedżer zbierania elektronicznych materiałów dowodowych, nie mogą usuwać członków ze sprawy, nawet jeśli użytkownik utworzył sprawę.

  Ze względu na szeroki zakres dostępu organizacja powinna mieć tylko kilku administratorów, którzy są członkami podgrupy Administratorzy zbierania elektronicznych materiałów dowodowych.

Aby uzyskać więcej informacji o uprawnieniach zbierania elektronicznych materiałów dowodowych i opis każdej roli przypisanej do grupy ról Menedżer zbierania elektronicznych materiałów dowodowych, zobacz Przypisywanie uprawnień [zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

## <a name="step-3-create-a-core-ediscovery-case"></a>Krok 3. Tworzenie podstawowej sprawy zbierania elektronicznych materiałów dowodowych

Następnym krokiem jest utworzenie sprawy i rozpoczęcie korzystania z podstawowych funkcji zbierania elektronicznych materiałów dowodowych. Wykonaj poniższe czynności, aby utworzyć sprawę i dodać członków. Użytkownik, który tworzy sprawę, jest automatycznie dodawany jako członek.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się przy użyciu poświadczeń dla konta użytkownika, do których zostały przypisane odpowiednie uprawnienia zbierania elektronicznych materiałów dowodowych. Członkowie grupy ról Zarządzanie organizacją mogą również tworzyć podstawowe sprawy zbierania elektronicznych materiałów dowodowych.

2. W okienku nawigacji po lewej stronie Centrum zgodności platformy Microsoft 365 kliknij pozycję Pokaż **wszystko**, a następnie kliknij **pozycję eDiscoveryCore** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. Na stronie **Podstawowe zbierania elektronicznych materiałów dowodowych** kliknij pozycję **Utwórz sprawę**.

4. Na stronie **wysuwana** Nowa sprawa nadaj sprawę nazwę (wymagane), a następnie wpisz opcjonalny opis. Nazwa sprawy musi być unikatowa w Twojej organizacji.

5. Kliknij **przycisk Zapisz** , aby utworzyć sprawę.

   Nowa sprawa zostanie utworzona i wyświetlona na stronie Core eDiscovery. Może być trzeba kliknąć pozycję **Odśwież,** aby wyświetlić nową sprawę.

## <a name="step-4-optional-add-members-to-a-core-ediscovery-case"></a>Krok 4 (opcjonalnie): Dodawanie członków do podstawowej sprawy zbierania elektronicznych materiałów dowodowych

Jeśli utworzysz sprawę w kroku 3 i jesteś jedyną osobą, która będzie korzystać ze sprawy, nie musisz wykonywać tego kroku. Możesz rozpocząć tworzenie zbierania elektronicznych materiałów dowodowych, wyszukiwanie zawartości i eksportowanie wyników wyszukiwania. Wykonaj tę czynności, jeśli chcesz udzielić innym użytkownikom (lub grupie ról) dostępu do sprawy.

1. Na **stronie Podstawowe zbierania** elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365 kliknij nazwę sprawy, do której chcesz dodać członków.

2. Na stronie głównej sprawy wybierz kartę **numer Ustawienia,** a następnie wybierz pozycję **Dostęp & uprawnienia**.

3. Na stronie **wysuwu & uprawnień** dostępu programu Access w obszarze **Członkowie** kliknij pozycję **Dodaj** , aby dodać członków do sprawy.

    Możesz również dodać grupy ról jako członków sprawy. W **obszarze Grupy ról** kliknij pozycję **Dodaj**. Do sprawy można przypisywać tylko te grupy ról, których jesteś członkiem. Jest tak dlatego, że grupy ról kontrolują, kto może przypisywać członków do sprawy zbierania elektronicznych materiałów dowodowych.

4. Na liście osób lub grup ról, które mogą być dodawane jako członkowie sprawy, kliknij po lewej stronie nazwiska osób (lub grup ról), które chcesz dodać. Jeśli masz dużą listę osób lub grup ról, które mogą być dodawane jako członkowie, użyj pola Wyszukaj, aby wyszukać określoną osobę lub grupę ról na liście.
  
5. Po wybraniu osób lub grup ról do dodania jako członków sprawy kliknij pozycję Zapisz, aby zapisać  nowych członków lub grupy ról.

> [!IMPORTANT]
>
>- Jeśli rola zostanie dodana lub usunięta z grupy ról dodanej jako członek sprawy, grupa ról zostanie automatycznie usunięta jako członek sprawy (lub w dowolnym przypadku, do których należy grupa ról). Przyczyną tego jest ochrona organizacji przed nieumyślnie udostępnieniem dodatkowych uprawnień członkom sprawy. Podobnie, jeśli grupa ról zostanie usunięta, zostanie usunięta ze wszystkich spraw, do których była członkiem. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases). 
>
>- Jak wyjaśniono wcześniej, tylko administrator zbierania elektronicznych materiałów dowodowych może usuwać członków ze sprawy. Użytkownicy, którzy są członkami podgrupy Menedżer zbierania elektronicznych materiałów dowodowych, nie mogą usuwać członków ze sprawy, nawet jeśli użytkownik utworzył sprawę.
>

## <a name="explore-the-core-ediscovery-workflow"></a>Poznawanie przepływu pracy Podstawowe zbieranie elektronicznych materiałów dowodowych

Aby rozpocząć korzystanie z podstawowych funkcji zbierania elektronicznych materiałów dowodowych, oto prosty przepływ pracy służący do tworzenia zbierania elektronicznych materiałów dowodowych dla osób zainteresowanych, wyszukiwania zawartości istotnej dla prowadzonego badania, a następnie eksportowania tych danych do dalszego przeglądu. W każdej z tych czynności wyróżnimy też niektóre rozszerzone funkcje podstawowe zbierania elektronicznych materiałów dowodowych, które możesz odkrywać.

![Podstawowy przepływ pracy zbierania elektronicznych materiałów dowodowych.](../media/CoreEdiscoveryWorkflow.png)

1. **[Tworzenie zbierania elektronicznych materiałów dowodowych](create-ediscovery-holds.md)**. Pierwszym krokiem po utworzeniu sprawy jest umieszczenie w miejscu zawartości lokalizacji osób, które są interesujące w prowadzonym śledzeniu, nazywane także holdm zbierania elektronicznych materiałów dowodowych. Lokalizacje zawartości obejmują Exchange pocztowe, witryny SharePoint, konta OneDrive oraz skrzynki pocztowe i witryny skojarzone z grupami Microsoft Teams i Microsoft 365. Mimo że ten krok jest opcjonalny, utworzenie funkcji zbierania elektronicznych materiałów dowodowych zachowuje zawartość, która może być istotny dla sprawy w trakcie badania. Po utworzeniu przechowywania zbierania elektronicznych materiałów dowodowych można zachować całą zawartość w określonych lokalizacjach zawartości lub utworzyć hold oparty na kwerendzie, aby zachować tylko zawartość, która odpowiada zapytaniu wstrzymywaniu. Oprócz zachowania zawartości innym dobrym powodem tworzenia zbierania elektronicznych materiałów dowodowych jest szybkie przeszukiwanie lokalizacji zawartości (zamiast wybierania poszczególnych lokalizacji do wyszukania) podczas tworzenia i uruchamiania wyszukiwań w następnym kroku. Po zakończeniu badania możesz zwolnić wszelkie utworzone przez Ciebie wstrzymywanie.

2. **[Wyszukiwanie zawartości](search-for-content-in-core-ediscovery.md)**. Po utworzeniu zbierania elektronicznych materiałów dowodowych użyj wbudowanego narzędzia wyszukiwania, aby przeszukać wstrzymywane lokalizacje zawartości. Możesz również przeszukiwać inne lokalizacje zawartości w poszukiwaniu danych, które mogą być istotne dla danej sprawy. Można tworzyć i uruchamiać różne wyszukiwania skojarzone ze sprawą. Za pomocą słów kluczowych, właściwości i warunków można [](keyword-queries-and-search-conditions.md) tworzyć zapytania wyszukiwania zwracające wyniki wyszukiwania z danymi, które najprawdopodobniej są istotne dla danej sprawy. Możesz również:

   - Wyświetlanie statystyk wyszukiwania, które mogą pomóc uściślić zapytanie wyszukiwania w celu zawężenia wyników.

   - Wyświetl podgląd wyników wyszukiwania, aby szybko sprawdzić, czy odpowiednie dane są wyszukiwane.

   - Popraw kwerendę i ponownie uruchomić wyszukiwanie.

3. **[Eksportowanie i pobieranie wyników wyszukiwania](export-content-in-core-ediscovery.md)**. Po wyszukaniu i odnalezieniu danych, które są istotne dla prowadzonego badania, możesz wyeksportować je Office 365 do przeglądu przez osoby spoza zespołu badania. Eksportowanie danych jest procesem dwuetapowym. Pierwszym krokiem jest wyeksportowanie wyników wyszukiwania w przypadku, gdy nie Office 365. Jest to możliwe dzięki skopiowaniu wyników wyszukiwania do lokalizacji danych usługi Azure Storage firmy Microsoft. Następnym krokiem jest pobranie zawartości na komputer lokalny za pomocą narzędzia eDiscovery Export Tool. Oprócz wyeksportowanych plików danych pakiet eksportu zawiera również raport eksportu, raport podsumowujący i raport o błędach.
