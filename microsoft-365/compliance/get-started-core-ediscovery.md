---
title: Wprowadzenie z przypadkami zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) w usłudze Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: W tym artykule opisano, jak rozpocząć korzystanie z eDiscovery (Standard) w usłudze Microsoft Purview. Po przypisaniu uprawnień do zbierania elektronicznych materiałów dowodowych i utworzeniu sprawy można dodać członków, utworzyć blokady zbierania elektronicznych materiałów dowodowych, a następnie wyszukać i wyeksportować zawartość, która jest odpowiednia dla badania.
ms.openlocfilehash: e224bf22741d0e1599d099802470e231b11fd785
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094951"
---
# <a name="get-started-with-ediscovery-standard-in-microsoft-purview"></a>Wprowadzenie zbierania elektronicznych materiałów dowodowych (Standard) w usłudze Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Usługa Microsoft Purview eDiscovery (Standard) w usłudze Microsoft Purview udostępnia podstawowe narzędzie zbierania elektronicznych materiałów dowodowych, którego organizacje mogą używać do wyszukiwania i eksportowania zawartości w Microsoft 365 i Office 365. Możesz również użyć funkcji zbierania elektronicznych materiałów dowodowych (Standardowa), aby umieścić blokadę zbierania elektronicznych materiałów dowodowych w lokalizacjach zawartości, takich jak skrzynki pocztowe Exchange, witryny SharePoint, konta OneDrive i Microsoft Teams. Do wdrożenia zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) nie jest wymagane żadne zadanie, ale istnieją pewne zadania wstępne, które musi wykonać administrator IT i menedżer zbierania elektronicznych elektronicznych materiałów dowodowych, zanim organizacja będzie mogła rozpocząć wyszukiwanie, eksportowanie i zachowywanie zawartości przy użyciu zbierania elektronicznych materiałów dowodowych (Standard).

W tym artykule omówiono kroki niezbędne do skonfigurowania zbierania elektronicznych materiałów dowodowych (Standard). Obejmuje to zapewnienie właściwego licencjonowania wymaganego do uzyskania dostępu do zbierania elektronicznych materiałów dowodowych (Standard) i wstrzymanie zbierania elektronicznych materiałów dowodowych w lokalizacjach zawartości, a także przypisanie uprawnień do zespołu IT, prawnego i dochodzeniowego w celu uzyskania dostępu do spraw i zarządzania nimi. Ten artykuł zawiera również ogólne omówienie przypadków użycia do wyszukiwania i eksportowania zawartości.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Krok 1. Weryfikowanie i przypisywanie odpowiednich licencji

Licencjonowanie zbierania elektronicznych materiałów dowodowych (Standardowa) wymaga odpowiedniej subskrypcji organizacji i licencjonowania dla poszczególnych użytkowników.

- **Subskrypcja organizacji:** Aby uzyskać dostęp do zbierania elektronicznych materiałów dowodowych (Standard) w portalu zgodności usługi Microsoft Purview i korzystać z funkcji przechowywania i eksportowania, organizacja musi mieć subskrypcję Microsoft 365 E3 lub Office 365 E3 lub nowszą. Microsoft 365 organizacje linii frontu muszą mieć subskrypcję F5.

- **Licencjonowanie na użytkownika:** Aby umieścić blokadę zbierania elektronicznych materiałów dowodowych w skrzynkach pocztowych i witrynach, użytkownicy muszą mieć przypisaną jedną z następujących licencji, w zależności od subskrypcji organizacji:

  - Licencja Microsoft 365 E3 lub Office 365 E3 lub nowsza

   LUB

  - licencja Office 365 E1 z licencją dodatku Exchange Online Plan 2 lub Exchange Online — archiwum

   LUB

  - Microsoft 365 licencja dodatku Zgodność z usługą Frontline F5 lub F5 Security & Compliance  

  I

  - licencja Office 365 E1 z licencją dodatku SharePoint Online Plan 2 lub OneDrive dla Firm Plan 2
  
  Aby uzyskać informacje na temat przypisywania licencji, zobacz [Przypisywanie licencji do użytkowników](../admin/manage/assign-licenses-to-users.md).

Aby uzyskać informacje i wskazówki dotyczące zabezpieczeń i zgodności:

- Pobierz i zobacz sekcję eDiscovery and auditing (Wykrywanie elektroniczne i inspekcja) w [tabeli Microsoft 365 Comparison (Porównanie Microsoft 365](https://aka.ms/M365EnterprisePlans)).

- Zapoznaj się ze [wskazówkami Microsoft 365 dotyczącymi zgodności & zabezpieczeń — opisy usług | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="step-2-assign-ediscovery-permissions"></a>Krok 2. Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych

Aby uzyskać dostęp do zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) lub zostać dodanym jako członek sprawy zbierania elektronicznych materiałów dowodowych (Standardowa), użytkownik musi mieć przypisane odpowiednie uprawnienia. W szczególności użytkownik musi zostać dodany jako członek grupy ról Menedżera zbierania elektronicznych materiałów dowodowych w portalu zgodności. Członkowie tej grupy ról mogą tworzyć przypadki zbierania elektronicznych materiałów dowodowych (standardowa) i zarządzać nimi. Mogą dodawać i usuwać członków, umieszczać blokadę zbierania elektronicznych materiałów dowodowych dla użytkowników, tworzyć i edytować wyszukiwania oraz eksportować zawartość ze sprawy zbierania elektronicznych materiałów dowodowych (standardowa).

Wykonaj następujące kroki, aby dodać użytkowników do grupy ról menedżera zbierania elektronicznych materiałów dowodowych:

1. Przejdź do portalu zgodności i zaloguj się przy użyciu poświadczeń konta administratora w organizacji Microsoft 365 lub Office 365.

2. Na stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a> wybierz grupę ról **Menedżera zbierania elektronicznych materiałów dowodowych** .

3. Na stronie wysuwanego Menedżera zbierania elektronicznych materiałów dowodowych kliknij pozycję **Edytuj** obok sekcji **Menedżer zbierania elektronicznych** materiałów dowodowych.

4. Na stronie **Wybieranie menedżera zbierania elektronicznych materiałów dowodowych** w kreatorze edytowania grupy ról kliknij pozycję **Wybierz menedżera odnajdywania**.

5. Kliknij przycisk **Dodaj** , a następnie zaznacz pole wyboru dla wszystkich użytkowników, którzy chcesz dodać do grupy ról.

6. Kliknij **przycisk Dodaj** , aby dodać wybranych użytkowników, a następnie kliknij przycisk **Gotowe**.

7. Kliknij przycisk **Zapisz** , aby dodać użytkowników do grupy ról, a następnie kliknij przycisk **Zamknij** , aby ukończyć ten krok.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Więcej informacji o grupie ról menedżera zbierania elektronicznych materiałów dowodowych

W grupie ról Menedżera zbierania elektronicznych materiałów dowodowych znajdują się dwie podgrupy. Różnica między tymi podgrupami zależy od zakresu.

- **Menedżer zbierania** elektronicznych materiałów dowodowych: może wyświetlać tworzone przez nich przypadki zbierania elektronicznych materiałów dowodowych (standard) lub zarządzać nimi. Jeśli inny menedżer zbierania elektronicznych materiałów dowodowych tworzy przypadek, ale nie dodaje drugiego menedżera zbierania elektronicznych materiałów dowodowych jako członka tej sprawy, drugi menedżer zbierania elektronicznych materiałów dowodowych nie będzie mógł wyświetlić ani otworzyć sprawy na stronie zbierania elektronicznych materiałów dowodowych (Standard) w centrum zgodności. Ogólnie rzecz biorąc, większość osób w organizacji może zostać dodana do podgrupy Menedżera zbierania elektronicznych materiałów dowodowych.

- **Administrator zbierania elektronicznych materiałów dowodowych**: może wykonywać wszystkie zadania zarządzania przypadkami, które może wykonać menedżer zbierania elektronicznych materiałów dowodowych. Ponadto administrator zbierania elektronicznych materiałów dowodowych może:

  - Wyświetl wszystkie przypadki wymienione na stronie eDiscovery (Standard).
  
  - Zarządzaj dowolnym przypadkiem w organizacji po dodaniu się jako członek sprawy.

  - Uzyskiwanie dostępu do danych przypadków i eksportowanie ich w dowolnym przypadku w organizacji.
  
  - Usuń elementy członkowskie ze sprawy zbierania elektronicznych materiałów dowodowych. Tylko administrator zbierania elektronicznych materiałów dowodowych może usunąć członków ze sprawy. Użytkownicy, którzy są członkami podgrupy Menedżera zbierania elektronicznych materiałów dowodowych, nie mogą usuwać członków ze sprawy, nawet jeśli użytkownik utworzył przypadek.

  Ze względu na szeroki zakres dostępu organizacja powinna mieć tylko kilku administratorów, którzy są członkami podgrupy administratorzy zbierania elektronicznych materiałów dowodowych.

Aby uzyskać więcej informacji o uprawnieniach do zbierania elektronicznych materiałów dowodowych i opis każdej roli przypisanej do grupy ról menedżera zbierania elektronicznych materiałów dowodowych, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

## <a name="step-3-create-a-ediscovery-standard-case"></a>Krok 3. Tworzenie sprawy zbierania elektronicznych materiałów dowodowych (standardowa)

Następnym krokiem jest utworzenie sprawy i rozpoczęcie korzystania z eDiscovery (Standard). Wykonaj poniższe kroki, aby utworzyć przypadek i dodać członków. Użytkownik tworzący sprawę jest automatycznie dodawany jako członek.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności</a> i zaloguj się przy użyciu poświadczeń dla konta użytkownika, do których przypisano odpowiednie uprawnienia zbierania elektronicznych materiałów dowodowych. Członkowie grupy ról Zarządzanie organizacją mogą również tworzyć przypadki zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa).

2. W okienku nawigacji po lewej stronie portalu zgodności kliknij pozycję **Pokaż wszystko**, a następnie kliknij pozycję **eDiscoveryCore** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. Na stronie **eDiscovery (Standard)** kliknij **pozycję Utwórz przypadek**.

4. Na stronie **Wysuwany nowy przypadek** nadaj przypadkowi nazwę (wymaganą), a następnie wpisz opcjonalny opis. Nazwa sprawy musi być unikatowa w organizacji.

5. Kliknij przycisk **Zapisz** , aby utworzyć przypadek.

   Nowy przypadek jest tworzony i wyświetlany na stronie eDiscovery (Standard). Może być konieczne **kliknięcie** przycisku Odśwież, aby wyświetlić nowy przypadek.

## <a name="step-4-optional-add-members-to-a-ediscovery-standard-case"></a>Krok 4 (opcjonalnie): Dodawanie członków do sprawy zbierania elektronicznych materiałów dowodowych (standardowa)

Jeśli utworzysz przypadek w kroku 3 i jesteś jedyną osobą, która będzie używać sprawy, nie musisz wykonywać tego kroku. Możesz zacząć używać sprawy do tworzenia blokad zbierania elektronicznych materiałów dowodowych, wyszukiwania zawartości i eksportowania wyników wyszukiwania. Wykonaj ten krok, jeśli chcesz udzielić innym użytkownikom (lub grupie ról) dostępu do sprawy.

1. Na stronie **eDiscovery (Standard)** w portalu zgodności kliknij nazwę przypadku, do którego chcesz dodać członków.

2. Na stronie głównej sprawy wybierz kartę **Ustawienia**, a następnie wybierz pozycję **Dostęp & uprawnienia**.

3. Na stronie **wysuwanej Uprawnienia & dostępu** w obszarze **Członkowie** kliknij pozycję **Dodaj** , aby dodać członków do sprawy.

    Możesz również dodać grupy ról jako elementy członkowskie sprawy. W obszarze **Grupy ról** kliknij pozycję **Dodaj**. Do sprawy można przypisać tylko grupy ról, których jesteś członkiem. Dzieje się tak dlatego, że grupy ról kontrolują, kto może przypisywać członków do sprawy zbierania elektronicznych materiałów dowodowych.

4. Na liście osób lub grup ról, które mogą zostać dodane jako członkowie sprawy, kliknij po lewej stronie nazwy osób (lub grup ról), które chcesz dodać. Jeśli masz dużą listę osób lub grup ról, które mogą zostać dodane jako członkowie, użyj pola **Wyszukiwania** , aby wyszukać określoną osobę lub grupę ról na liście.
  
5. Po wybraniu osób lub grup ról, które mają zostać dodane jako członkowie sprawy, kliknij przycisk **Zapisz** , aby zapisać nowych członków lub grupy ról.

> [!IMPORTANT]
>
>- Jeśli rola zostanie dodana lub usunięta z grupy ról, która została dodana jako członek sprawy, grupa ról zostanie automatycznie usunięta jako członek sprawy (lub w każdym przypadku grupa ról jest członkiem). Powodem jest ochrona organizacji przed nieumyślnym udzieleniem dodatkowych uprawnień członkom sprawy. Podobnie, jeśli grupa ról zostanie usunięta, zostanie usunięta ze wszystkich przypadków, do które należała. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases). 
>
>- Jak wyjaśniono wcześniej, tylko administrator zbierania elektronicznych materiałów dowodowych może usunąć członków ze sprawy. Użytkownicy, którzy są członkami podgrupy Menedżera zbierania elektronicznych materiałów dowodowych, nie mogą usuwać członków ze sprawy, nawet jeśli użytkownik utworzył przypadek.
>

## <a name="explore-the-ediscovery-standard-workflow"></a>Eksplorowanie przepływu pracy zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa)

Aby rozpocząć korzystanie z eDiscovery (Standard), oto prosty przepływ pracy tworzenia blokad zbierania elektronicznych materiałów dowodowych dla osób zainteresowanych, wyszukiwania zawartości odpowiedniej dla badania, a następnie eksportowania tych danych do dalszego przeglądu. W każdym z tych kroków wyróżnimy również niektóre rozszerzone funkcje zbierania elektronicznych materiałów dowodowych (Standard), które można eksplorować.

![Przepływ pracy zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa).](../media/CoreEdiscoveryWorkflow.png)

1. **[Utwórz blokadę zbierania elektronicznych materiałów dowodowych](create-ediscovery-holds.md)**. Pierwszym krokiem po utworzeniu sprawy jest wstrzymanie ( *nazywane również blokadą zbierania elektronicznych materiałów dowodowych*) w lokalizacjach zawartości osób zainteresowanych badaniem. Lokalizacje zawartości obejmują Exchange skrzynki pocztowe, witryny SharePoint, konta OneDrive oraz skrzynki pocztowe i witryny skojarzone z Microsoft Teams i Grupy Microsoft 365. Chociaż ten krok jest opcjonalny, utworzenie blokady zbierania elektronicznych materiałów dowodowych zachowuje zawartość, która może być istotna dla sprawy podczas badania. Podczas tworzenia blokady zbierania elektronicznych materiałów dowodowych można zachować całą zawartość w określonych lokalizacjach zawartości lub utworzyć blokadę opartą na zapytaniach, aby zachować tylko zawartość zgodną z zapytaniem blokady. Oprócz zachowania zawartości innym dobrym powodem do utworzenia blokad zbierania elektronicznych materiałów dowodowych jest szybkie przeszukiwanie lokalizacji zawartości w stanie wstrzymania (zamiast wybierania każdej lokalizacji do wyszukania) podczas tworzenia i uruchamiania wyszukiwań w następnym kroku. Po zakończeniu badania możesz zwolnić wszystkie utworzone blokady.

2. **[Wyszukaj zawartość](search-for-content-in-core-ediscovery.md)**. Po utworzeniu blokad zbierania elektronicznych materiałów dowodowych użyj wbudowanego narzędzia wyszukiwania do przeszukiwania lokalizacji zawartości w stanie wstrzymania. Możesz również wyszukać w innych lokalizacjach zawartości dane, które mogą być istotne dla danego przypadku. Możesz tworzyć i uruchamiać różne wyszukiwania skojarzone ze sprawą. Słowa kluczowe, właściwości i warunki umożliwiają [tworzenie zapytań wyszukiwania zwracających](keyword-queries-and-search-conditions.md) wyniki wyszukiwania z danymi, które najprawdopodobniej są istotne dla danego przypadku. Możesz również:

   - Wyświetl statystyki wyszukiwania, które mogą ułatwić uściślanie zapytania wyszukiwania w celu zawężenia wyników.

   - Wyświetl podgląd wyników wyszukiwania, aby szybko sprawdzić, czy znaleziono odpowiednie dane.

   - Popraw zapytanie i uruchom ponownie wyszukiwanie.

3. **[Eksportowanie i pobieranie wyników wyszukiwania](export-content-in-core-ediscovery.md)**. Po wyszukaniu i znalezieniu danych istotnych dla badania możesz wyeksportować je z Office 365 do przeglądu przez osoby spoza zespołu dochodzeniowego. Eksportowanie danych jest procesem dwuetapowym. Pierwszym krokiem jest wyeksportowanie wyników wyszukiwania w przypadku braku Office 365. Jest to realizowane przez skopiowanie wyników wyszukiwania do lokalizacji Storage platformy Azure udostępnionej przez firmę Microsoft. Następnym krokiem jest użycie narzędzia eDiscovery Export do pobrania zawartości na komputer lokalny. Oprócz wyeksportowanych plików danych pakiet eksportu zawiera raport eksportu, raport podsumowania i raport o błędach.
