---
title: Konfigurowanie zbierania elektronicznych materiałów dowodowych (Premium) w usłudze Microsoft Purview
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
description: W tym artykule opisano sposób konfigurowania zbierania elektronicznych materiałów dowodowych (Premium), aby można było rozpocząć tworzenie spraw i zarządzanie nimi. Opisano w nim również wymagane subskrypcje i licencjonowanie firmy Microsoft. Po wykonaniu kilku szybkich kroków narzędzie eDiscovery (Premium) jest gotowe do użycia.
ms.openlocfilehash: dff99ab432ce5f2380a6fd5a81e855c946146c8c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997719"
---
# <a name="set-up-microsoft-purview-ediscovery-premium"></a>Konfigurowanie zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Usługa Microsoft Purview eDiscovery (Premium) udostępnia kompleksowy przepływ pracy umożliwiający przechowywanie, zbieranie, przeglądanie, analizowanie i eksportowanie danych, które reagują na wewnętrzne i zewnętrzne badania organizacji. Do wdrożenia zbierania elektronicznych materiałów dowodowych (Premium) nie jest potrzebne żadne zadanie, ale istnieją pewne zadania wstępne, które musi wykonać administrator IT i menedżer zbierania elektronicznych materiałów dowodowych, zanim organizacja będzie mogła rozpocząć tworzenie i używanie spraw zbierania elektronicznych materiałów dowodowych (Premium) do zarządzania badaniami.

W tym artykule omówiono następujące kroki niezbędne do skonfigurowania zbierania elektronicznych materiałów dowodowych (Premium).

![Kroki konfigurowania zbierania elektronicznych materiałów dowodowych (Premium).](../media/set-up-advanced-ediscovery.png)

Obejmuje to zapewnienie odpowiedniego licencjonowania wymaganego do uzyskania dostępu do zbierania elektronicznych materiałów dowodowych (Premium) oraz dodawanie opiekunów do spraw oraz przypisywanie uprawnień zespołowi prawnemu i dochodzeniowemu, aby mogli oni uzyskiwać dostęp do spraw i zarządzać nimi.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Krok 1. Weryfikowanie i przypisywanie odpowiednich licencji

Licencjonowanie zbierania elektronicznych materiałów dowodowych (Premium) wymaga odpowiedniej subskrypcji organizacji i licencjonowania dla poszczególnych użytkowników. Aby uzyskać listę wymagań licencyjnych dotyczących zbierania elektronicznych materiałów dowodowych (Premium), zobacz [Subskrypcje i licencjonowanie](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>Krok 2. Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych

Aby uzyskać dostęp do zbierania elektronicznych materiałów dowodowych (Premium) lub dodać go jako członka sprawy zbierania elektronicznych materiałów dowodowych (Premium), użytkownikowi muszą zostać przypisane odpowiednie uprawnienia. W szczególności użytkownik musi zostać dodany jako członek grupy ról menedżera zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview. Członkowie tej grupy ról mogą tworzyć przypadki zbierania elektronicznych materiałów dowodowych (Premium) i zarządzać nimi. Mogą dodawać i usuwać członków, umieszczać opiekunów i lokalizacje zawartości, zarządzać powiadomieniami o blokadzie prawnej, tworzyć i edytować wyszukiwania skojarzone w danym przypadku, dodawać wyniki wyszukiwania do zestawu przeglądów, analizować dane w zestawie przeglądów oraz eksportować i pobierać ze sprawy zbierania elektronicznych materiałów dowodowych (Premium).

Wykonaj następujące kroki, aby dodać użytkowników do grupy ról menedżera zbierania elektronicznych materiałów dowodowych:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">portalu zgodności</a> i zaloguj się przy użyciu poświadczeń konta administratora w organizacji Microsoft 365.

2. Na stronie **Uprawnienia** wybierz grupę ról **Menedżera zbierania elektronicznych materiałów dowodowych** .

3. Na stronie wysuwanego Menedżera zbierania elektronicznych materiałów dowodowych kliknij pozycję **Edytuj** obok sekcji **Menedżer zbierania elektronicznych** materiałów dowodowych.

4. Na stronie **Wybieranie menedżera zbierania elektronicznych** materiałów dowodowych w kreatorze edytowania grupy ról kliknij pozycję **Wybierz menedżera zbierania elektronicznych materiałów dowodowych**.

5. Kliknij przycisk **Dodaj** , a następnie zaznacz pole wyboru dla wszystkich użytkowników, którzy chcesz dodać do grupy ról.

6. Kliknij **przycisk Dodaj** , aby dodać wybranych użytkowników, a następnie kliknij przycisk **Gotowe**.

7. Kliknij przycisk **Zapisz** , aby dodać użytkowników do grupy ról, a następnie kliknij przycisk **Zamknij** , aby ukończyć ten krok.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Więcej informacji o grupie ról menedżera zbierania elektronicznych materiałów dowodowych

W grupie ról Menedżera zbierania elektronicznych materiałów dowodowych znajdują się dwie podgrupy. Różnica między tymi podgrupami zależy od zakresu.

- **Menedżer zbierania elektronicznych** materiałów dowodowych: może wyświetlać przypadki zbierania elektronicznych materiałów dowodowych (Premium) lub zarządzać nimi. Jeśli inny menedżer zbierania elektronicznych materiałów dowodowych tworzy przypadek, ale nie dodaje drugiego menedżera zbierania elektronicznych materiałów dowodowych jako członka tej sprawy, drugi menedżer zbierania elektronicznych materiałów dowodowych nie będzie mógł wyświetlić ani otworzyć sprawy na stronie zbierania elektronicznych materiałów dowodowych (Premium) w centrum zgodności. Ogólnie rzecz biorąc, większość osób w organizacji może zostać dodana do podgrupy Menedżera zbierania elektronicznych materiałów dowodowych.

- **Administrator zbierania elektronicznych materiałów dowodowych**: może wykonywać wszystkie zadania zarządzania przypadkami, które może wykonać menedżer zbierania elektronicznych materiałów dowodowych. Ponadto administrator zbierania elektronicznych materiałów dowodowych może:

  - Wyświetl wszystkie przypadki wymienione na stronie zbierania elektronicznych materiałów dowodowych (Premium).
  
  - Zarządzaj dowolnym przypadkiem w organizacji po dodaniu się jako członek sprawy.

  - Uzyskiwanie dostępu do danych przypadków i eksportowanie ich w dowolnym przypadku w organizacji.

  Ze względu na szeroki zakres dostępu organizacja powinna mieć tylko kilku administratorów, którzy są członkami podgrupy administratorzy zbierania elektronicznych materiałów dowodowych.

Aby uzyskać więcej informacji o uprawnieniach do zbierania elektronicznych materiałów dowodowych i opis każdej roli przypisanej do grupy ról menedżera zbierania elektronicznych materiałów dowodowych, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-ediscovery-premium"></a>Krok 3. Konfigurowanie ustawień globalnych dla zbierania elektronicznych materiałów dowodowych (Premium)

Ostatnim krokiem, który należy wykonać przed rozpoczęciem tworzenia i używania przypadków użycia przez osoby w organizacji, jest skonfigurowanie ustawień globalnych, które mają zastosowanie do wszystkich przypadków w organizacji. Obecnie jedynym ustawieniem globalnym jest *wykrywanie uprawnień klienta-adwokata* (więcej ustawień globalnych będzie dostępnych w przyszłości). To ustawienie umożliwia uruchamianie modelu uprawnień adwokackiego klienta podczas analizowania danych w zestawie przeglądów. Model używa uczenia maszynowego do określenia prawdopodobieństwa, że dokument zawiera zawartość o charakterze prawnym. Porównuje również uczestników dokumentów z listą adwokatów (którą przesyłasz podczas konfigurowania modelu), aby ustalić, czy dokument ma co najmniej jednego uczestnika, który jest adwokatem.

Aby uzyskać więcej informacji na temat konfigurowania i używania modelu wykrywania uprawnień klienta-adwokata, zobacz [Konfigurowanie wykrywania uprawnień klienta-adwokata w usłudze eDiscovery (Premium)](attorney-privilege-detection.md).

> [!NOTE]
> Jest to opcjonalny krok, który można wykonać w dowolnym momencie. Nie implementowanie modelu wykrywania uprawnień klienta-adwokata nie uniemożliwia tworzenia i używania przypadków zbierania elektronicznych materiałów dowodowych (Premium).

## <a name="next-steps"></a>Następne kroki

Po skonfigurowaniu funkcji zbierania elektronicznych materiałów dowodowych (Premium) możesz utworzyć [przypadek](create-and-manage-advanced-ediscoveryv2-case.md).