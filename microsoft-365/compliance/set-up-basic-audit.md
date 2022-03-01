---
title: Konfigurowanie inspekcji podstawowej w programie Microsoft 365
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
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MOE150
- MET150
description: W tym artykule opisano, jak skonfigurować inspekcję podstawową, aby można było rozpocząć wyszukiwanie działań inspekcji wykonanych przez użytkowników i administratorów w organizacji.
ms.openlocfilehash: e4ae5901c9a4f400e2a01659395d27947ad433c2
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017794"
---
# <a name="set-up-basic-audit-in-microsoft-365"></a>Konfigurowanie inspekcji podstawowej w programie Microsoft 365

Podstawowa inspekcja Microsoft 365 umożliwia wyszukiwanie rekordów inspekcji pod poszukiwaniu działań wykonywanych w różnych Microsoft 365 usługach firmy Microsoft przez użytkowników i administratorów. Ponieważ inspekcja podstawowa jest domyślnie włączona dla większości organizacji Microsoft 365 i organizacji Office 365, istnieje tylko kilka czynności, które należy wykonać, aby osoby w organizacji były w stanie przeszukiwać dziennik inspekcji.

W tym artykule omówiono następujące kroki niezbędne do skonfigurowania inspekcji podstawowej.

![Czynności, które należy wykonać, aby skonfigurować inspekcję podstawową.](../media/BasicAuditingWorkflow.png)

Te kroki obejmują zapewnienie odpowiednich subskrypcji organizacyjnych i licencjonowania użytkowników wymaganych do generowania i zachowywania rekordów inspekcji oraz przypisywania uprawnień członkom zespołu do działań zabezpieczających, IT, zgodności i prawnych, aby można było przeszukiwać dziennik inspekcji.

Aby uzyskać więcej informacji, zobacz [Inspekcja podstawowa w programie Microsoft 365](auditing-solutions-overview.md#basic-audit).

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>Krok 1. Weryfikowanie subskrypcji organizacji i licencjonowania użytkowników

Licencjonowanie w ramach inspekcji podstawowej wymaga odpowiedniej subskrypcji organizacji, która zapewnia dostęp do narzędzia do przeszukiwania dziennika inspekcji, oraz licencjonowania na użytkownika wymaganego do logowania i zachowywania rekordów inspekcji.

Gdy użytkownik lub administrator wykonuje rejestrowane działania, w dzienniku inspekcji organizacji jest generowany i przechowywany rekord inspekcji. W przypadku inspekcji podstawowej rekordy inspekcji są zachowywane i dostępne do przeszukiwania w dzienniku inspekcji przez 90 dni.

Aby uzyskać listę wymagań dotyczących subskrypcji i licencjonowania dla inspekcji podstawowej, zobacz [Inspekcja rozwiązań w programie Microsoft 365](auditing-solutions-overview.md#licensing-requirements).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>Krok 2. Przypisywanie uprawnień do przeszukiwania dziennika inspekcji

Administratorzy i członkowie zespołów ds. inspekcji muszą mieć przypisaną do View-Only Dzienniki inspekcji lub Dzienniki inspekcji Exchange Online przeszukiwać dziennik inspekcji. Domyślnie te role są przypisane do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie Uprawnienia w centrum  <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a>. Administratorzy globalni w Office 365 i Microsoft 365 są automatycznie dodawana jako członkowie grupy ról Zarządzanie organizacją w programie Exchange Online. Aby dać użytkownikowi możliwość przeszukiwania dziennika inspekcji z minimalnym poziomem uprawnień, możesz utworzyć niestandardową grupę ról w programie Exchange Online, dodać rolę Dzienniki inspekcji lub Dzienniki inspekcji usługi View-Only, a następnie dodać użytkownika jako członka nowej grupy ról. Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami ról w Exchange Online](/Exchange/permissions-exo/role-groups).

Poniższy zrzut ekranu przedstawia dwie role związane z inspekcją przypisane do grupy ról Zarządzanie organizacją w centrum Exchange administracyjnego.

![Inspekcja ról przypisanych do grupy ról w Exchange Online.](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>Krok 3. Przeszukiwanie dziennika inspekcji

Teraz możesz przeszukiwać dziennik inspekcji w Centrum zgodności platformy Microsoft 365.

1. Przejdź do <https://compliance.microsoft.com> konta z odpowiednimi uprawnieniami inspekcji i zaloguj się przy użyciu tego konta.

2. W lewym okienku nawigacji okna Centrum zgodności platformy Microsoft 365 kliknij pozycję Pokaż **wszystko**, a następnie kliknij pozycję **Inspekcja**.

3. Na stronie **Inspekcja** skonfiguruj wyszukiwanie przy użyciu następujących warunków na **karcie** Wyszukiwanie. 

   ![Ustawienia konfiguracji przeszukiwania dziennika inspekcji.](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Zakres dat i godzin**. Wybierz zakres dat i godzin, aby wyświetlić zdarzenia, które wystąpiły w tym okresie. Data i godzina są prezentowane w godzinach lokalnych. Domyślnie jest zaznaczonych ostatnich siedem dni.
  
   2. **Działania**. Wybierz działania do wyszukania. Użyj pola wyszukiwania, aby wyszukać działania w celu dodania ich do listy. Aby uzyskać częściową listę działań, które są pod kontrolą, zobacz [Działania pod kontrolą](search-the-audit-log-in-security-and-compliance.md#audited-activities). Jeśli pozostawisz to pole puste, zostaną zwrócone wpisy dla wszystkich działań inspekcji.
  
   3. **Użytkownicy**.  Kliknij w tym polu i zacznij wpisywać nazwy użytkowników, dla których mają być wyświetlane wyniki wyszukiwania. Na liście wyników zostaną wyświetlone wpisy dziennika inspekcji dotyczące wybranych działań wykonanych przez użytkowników wybranych w tym polu. Jeśli pozostawisz to pole puste, zostaną zwrócone wpisy dotyczące wszystkich użytkowników (i kont usług) w organizacji.
  
   4. **Plik, folder lub witryna**. Wpisz część lub całą nazwę pliku lub folderu, aby wyszukać działania związane z plikiem folderu zawierającym określone słowo kluczowe. Możesz również określić adres URL pliku lub folderu. Jeśli używasz adresu URL pliku lub folderu, upewnij się, że wpisasz pełną ścieżkę adresu URL lub jeśli wpiszemy część adresu URL, nie dołączaj znaków specjalnych ani spacji. Jeśli pozostawisz to pole puste, zostaną zwrócone wpisy dotyczące wszystkich plików i folderów w organizacji.

4. Kliknij **pozycję** Wyszukaj, aby uruchomić wyszukiwanie.

Zostanie wyświetlana nowa strona z pokazem uruchomionego przeszukiwania dziennika inspekcji. Po zakończeniu wyszukiwania rekordy inspekcji są wyświetlane na stronie. Kliknij rekord, aby wyświetlić stronę wysuwu ze szczegółowymi właściwościami.

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Przeszukiwanie dziennika inspekcji w centrum zgodności](search-the-audit-log-in-security-and-compliance.md).
