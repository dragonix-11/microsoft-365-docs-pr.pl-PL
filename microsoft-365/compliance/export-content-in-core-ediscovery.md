---
title: Eksportowanie i pobieranie zawartości z podstawowej sprawy zbierania elektronicznych materiałów dowodowych
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
search.appverid:
- MOE150
- MET150
ms.custom: admindeeplinkCOMPLIANCE
description: W tym artykule opisano, jak eksportować i pobierać zawartość z podstawowej sprawy zbierania elektronicznych materiałów dowodowych w Microsoft 365.
ms.openlocfilehash: 1d998a4b1eb540a1d96afc3acd3518d0c604a7e9
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990510"
---
# <a name="export-content-from-a-core-ediscovery-case"></a>Eksportowanie zawartości z podstawowej sprawy zbierania elektronicznych materiałów dowodowych

Po pomyślnym uruchomieniu wyszukiwania skojarzonego z podstawową sprawą zbierania elektronicznych materiałów dowodowych możesz wyeksportować wyniki wyszukiwania. Podczas eksportowania wyników wyszukiwania elementy skrzynki pocztowej są pobierane w plikach PST lub jako pojedyncze wiadomości. Podczas eksportowania zawartości z witryn SharePoint i OneDrive dla Firm są eksportowane kopie natywnych dokumentów Office i innych dokumentów. Eksportowany jest również plik Results.csv zawierający informacje o wszystkich eksportowanych elementach oraz plik manifestu (w formacie XML), który zawiera informacje o każdym wyniku wyszukiwania.
  
## <a name="export-search-results"></a>Eksportowanie wyników wyszukiwania

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się przy użyciu poświadczeń dla konta użytkownika, do których zostały przypisane odpowiednie uprawnienia zbierania elektronicznych materiałów dowodowych.

2. W lewym okienku nawigacji okna Centrum zgodności platformy Microsoft 365 pozycję Pokaż **wszystko**, a następnie wybierz **pozycję EDiscoveryCore** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. Na **stronie Podstawowe zbierania elektronicznych materiałów dowodowych** kliknij nazwę sprawy, w której chcesz utworzyć wstrzymanie.

4. Na stronie **głównej** sprawy kliknij **kartę** Wyszukiwania.

5. W menu **Akcje** u dołu strony wysuwu kliknij polecenie **Eksportuj wyniki**.

   ![Opcja Eksportuj wyniki w menu Akcje.](../media/ActionMenuExportResults.png)

   Przepływ pracy służący do eksportowania wyników wyszukiwania skojarzonego ze sprawą core eDiscovery jest taki sam jak eksportowanie wyników wyszukiwania dla wyszukiwania na **stronie Przeszukiwanie** zawartości. Aby uzyskać instrukcje krok po kroku, zobacz [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md).

   > [!NOTE]
   > Podczas eksportowania wyników wyszukiwania można włączyć de duplikowanie, dzięki czemu będzie eksportowana tylko jedna kopia wiadomości e-mail, nawet jeśli w przeszukanych skrzynkach pocztowych może być kilka wystąpień tej samej wiadomości. Aby uzyskać więcej informacji na temat de duplikowania i sposobu identyfikowania zduplikowanych elementów, zobacz [Duplikowanie w wynikach wyszukiwania zbierania elektronicznych materiałów dowodowych](de-duplication-in-ediscovery-search-results.md).

   Po rozpoczęciu eksportowania wyniki wyszukiwania są przygotowane do pobrania, co oznacza, że są one przenoszone do lokalizacji w chmurze firmy Microsoft dostępnej pod Storage Azure.
  
6. Kliknij **kartę Eksporty** , aby wyświetlić listę zadań eksportu.
  
   ![Eksportuj zadania na karcie Eksportowanie w podstawowej sprawie zbierania elektronicznych materiałów dowodowych.](../media/CoreeDiscoveryExport.png)

   Może być konieczne kliknięcie **przycisku Odśwież** w celu zaktualizowania listy zadań eksportu tak, aby wyświetlała utworzone zadanie eksportu. Zadania eksportowania mają taką samą nazwę jak odpowiadające im wyszukiwanie **z _Export** dołączona do nazwy wyszukiwania.

7. Kliknij utworzone zadanie eksportu, aby wyświetlić informacje o stanie na stronie wysuwu. Te informacje obejmują procent elementów, które zostały przeniesione do lokalizacji usługi Azure Storage lokalizacji.

8. Po przeniesieniu wszystkich elementów kliknij pozycję **Pobierz** wyniki, aby pobrać wyniki wyszukiwania na komputer lokalny. Aby uzyskać więcej informacji o pobieraniu wyników wyszukiwania, zobacz krok 2 w tece [Eksportowanie wyników wyszukiwania zawartości.](export-search-results.md#step-2-download-the-search-results)

> [!NOTE]
> Wyeksportowane wyniki wyszukiwania należy pobrać w ciągu 14 dni od utworzenia zadania eksportu.

### <a name="more-information-about-exporting-searches-from-a-case"></a>Więcej informacji na temat eksportowania wyszukiwań ze sprawy

- Aby uzyskać więcej informacji na temat plików eksportu uwzględnianych podczas eksportowania wyników wyszukiwania, zobacz [Eksportowanie raportu przeszukiwania zawartości](export-a-content-search-report.md#whats-included-in-the-report).

- Jeśli ponownie uruchomisz eksportowanie, wszelkie zmiany zapytań wyszukiwania, które są zadaniami eksportowania, nie będą mieć wpływu na pobierane wyniki wyszukiwania. Po ponownym uruchomieniu eksportu zostanie uruchomione to samo zadanie połączonego zapytania wyszukiwania, które zostało uruchomione podczas tworzenia zadania eksportu.

- Ponadto po ponownym uruchomieniu eksportu wyniki wyszukiwania skopiowane do lokalizacji usługi Azure Storage zastąpią poprzednie wyniki. Poprzednie skopiowane wyniki nie będą dostępne do pobrania.
