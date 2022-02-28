---
title: Konfigurowanie Advanced eDiscovery w programie Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: W tym artykule opisano, jak skonfigurować Advanced eDiscovery, aby można było rozpocząć tworzenie spraw i zarządzać nimi. Opisano w nim również wymagane subskrypcje i licencje firmy Microsoft. Po ukończeniu kilku szybkich kroków narzędzie do Advanced eDiscovery jest gotowe do użycia.
ms.openlocfilehash: cf2d7c6bc770dd6125777c895771b3b61c8ee593
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990509"
---
# <a name="set-up-microsoft-365-advanced-ediscovery"></a>Konfigurowanie Microsoft 365 Advanced eDiscovery

Advanced eDiscovery w programie Microsoft 365 zapewnia szczegółowe przepływy pracy do zachowywania, zbierania, przeglądania, analizowania i eksportowania danych, które reagują na wewnętrzne i zewnętrzne badania Twojej organizacji. Do wdrożenia usługi Advanced eDiscovery nie jest wymagane nic, ale istnieją pewne wstępnie wymagane zadania, które musi wykonać administrator IT i menedżer zbierania elektronicznych materiałów dowodowych, zanim Twoja organizacja będzie w stanie zacząć tworzyć sprawy Advanced eDiscovery i używać ich do zarządzania badaniami.

W tym artykule omówiono następujące kroki niezbędne do skonfigurowania Advanced eDiscovery.

![Kroki procedury Advanced eDiscovery.](../media/set-up-advanced-ediscovery.png)

Obejmuje to zapewnienie odpowiedniego licencjonowania wymaganego do uzyskiwania dostępu do Advanced eDiscovery i dodawanie osób do spraw oraz przypisywanie uprawnień do zespołu prawnego i sądowego, aby ten zespół był w stanie uzyskać dostęp do spraw i zarządzać nimi.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Krok 1. Weryfikowanie i przypisywanie odpowiednich licencji

Licencjonowanie Advanced eDiscovery wymaga odpowiedniej subskrypcji organizacji i licencjonowania na użytkownika. Aby uzyskać listę wymagań licencjonowania dla Advanced eDiscovery, zobacz [Subskrypcje i licencjonowanie](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>Krok 2. Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych

Aby uzyskać Advanced eDiscovery lub dodać go jako członka do sprawy Advanced eDiscovery, użytkownikowi muszą zostać przypisane odpowiednie uprawnienia. W szczególności należy dodać użytkownika jako członka grupy ról Menedżer zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365. Członkowie tej grupy ról mogą tworzyć sprawy Advanced eDiscovery i zarządzać nimi. Mogą dodawać i usuwać członków, umieszczać pliki przechowywania i lokalizacje zawartości w czeku, zarządzać powiadomieniami o zawartości, tworzyć i edytować wyszukiwania skojarzone ze sprawą, dodawać wyniki wyszukiwania do zestawu recenzji, analizować dane w zestawie recenzji oraz eksportować i pobierać dane ze Advanced eDiscovery przypadku.

Wykonaj następujące czynności, aby dodać użytkowników do grupy ról Menedżer zbierania elektronicznych materiałów dowodowych:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się przy użyciu poświadczeń administratora konta administratora w Twojej Microsoft 365 organizacji.

2. Na stronie **Uprawnienia** wybierz grupę ról **Menedżer zbierania** elektronicznych materiałów dowodowych.

3. Na stronie wysuwu Menedżera zbierania elektronicznych materiałów dowodowych kliknij pozycję **Edytuj** obok sekcji **Menedżer zbierania** elektronicznych materiałów dowodowych.

4. Na stronie **Wybieranie menedżera zbierania elektronicznych materiałów** dowodowych w kreatorze edytowania grupy ról kliknij pozycję **Wybierz menedżera zbierania elektronicznych materiałów dowodowych**.

5. Kliknij **pozycję** Dodaj, a następnie zaznacz pole wyboru dla wszystkich użytkowników, których chcesz dodać do grupy ról.

6. Kliknij **pozycję Dodaj** , aby dodać wybranych użytkowników, a następnie kliknij pozycję **Gotowe**.

7. Kliknij **pozycję** Zapisz, aby dodać użytkowników do grupy ról, a następnie kliknij przycisk **Zamknij** , aby ukończyć ten krok.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Więcej informacji na temat grupy ról Menedżer zbierania elektronicznych materiałów dowodowych

W grupie ról Menedżer zbierania elektronicznych materiałów dowodowych są dwie podgrupy. Różnica między tymi podgrupami zależy od zakresu.

- **Menedżer zbierania elektronicznych materiałów dowodowych**: Może wyświetlać i Advanced eDiscovery spraw, które tworzyć lub do których należy. Jeśli inny menedżer zbierania elektronicznych materiałów dowodowych utworzy sprawę, ale nie doda drugiego menedżera zbierania elektronicznych materiałów dowodowych jako członka tej sprawy, drugi menedżer zbierania elektronicznych materiałów dowodowych nie będzie mógł wyświetlić ani otworzyć sprawy na stronie programu Advanced eDiscovery w Centrum zgodności. Na ogół większość osób w organizacji może zostać dodana do podgrupy Menedżer zbierania elektronicznych materiałów dowodowych.

- **Administrator zbierania elektronicznych materiałów** dowodowych: może wykonywać wszystkie zadania związane z zarządzaniem sprawymi, które może wykonywać Menedżer zbierania elektronicznych materiałów dowodowych. Ponadto administrator zbierania elektronicznych materiałów dowodowych może:

  - Wyświetlanie wszystkich spraw wymienionych na Advanced eDiscovery głównej.
  
  - Zarządzanie wszystkimi sprawymi w organizacji po dodaniu siebie jako członka do sprawy.

  - Uzyskiwanie dostępu do danych sprawy i eksportowanie ich dla dowolnej sprawy w organizacji.

  Ze względu na szeroki zakres dostępu organizacja powinna mieć tylko kilku administratorów, którzy są członkami podgrupy Administratorzy zbierania elektronicznych materiałów dowodowych.

Aby uzyskać więcej informacji o uprawnieniach zbierania elektronicznych materiałów dowodowych i opis każdej roli przypisanej do grupy ról Menedżer zbierania elektronicznych materiałów dowodowych, zobacz Przypisywanie uprawnień [zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-advanced-ediscovery"></a>Krok 3. Konfigurowanie ustawień globalnych dla Advanced eDiscovery

Ostatnim krokiem do wykonania przed rozpoczęciem tworzenia i używania spraw przez osoby w organizacji jest skonfigurowanie ustawień globalnych dotyczących wszystkich spraw w organizacji. Obecnie jedynym ustawieniem globalnym jest wykrywanie uprawnień klienta-klienta *(w* przyszłości będzie dostępnych więcej ustawień globalnych). To ustawienie umożliwia uruchomienie modelu uprawnień klienta obsługi klienta podczas analizowania danych w zestawie recenzji. W modelu jest używane uczenie maszynowe w celu określenia prawdopodobieństwa, że dokument zawiera zawartość z natury prawnej. Porównuje także uczestników dokumentów z listą prawniczych (przesłaną przez Ciebie podczas konfigurowania modelu) w celu ustalenia, czy w dokumencie co najmniej jednego uczestnika jest pełnomocnik.

Aby uzyskać więcej informacji na temat konfigurowania i używania modelu wykrywania uprawnień prawni-klienta, zobacz Konfigurowanie wykrywania prawa do obsługi klienta w [programie Advanced eDiscovery](attorney-privilege-detection.md).

> [!NOTE]
> Jest to krok opcjonalny, który można wykonać w dowolnym momencie. Nie zaimplementowanie modelu wykrywania uprawnień klienta obsługi klienta nie uniemożliwia tworzenia i używania innych Advanced eDiscovery przypadkach.

## <a name="next-steps"></a>Następne kroki

Po skonfigurowaniu Advanced eDiscovery można utworzyć [sprawę](create-and-manage-advanced-ediscoveryv2-case.md).