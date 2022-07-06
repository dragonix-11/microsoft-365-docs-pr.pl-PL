---
title: Konfigurowanie inspekcji (standardowej) na platformie Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: W tym artykule opisano sposób konfigurowania inspekcji (Standardowa), aby można było rozpocząć wyszukiwanie działań inspekcji wykonywanych przez użytkowników i administratorów w organizacji.
ms.openlocfilehash: 17f9e24f4c3159186011d3faefbd8796f51cc5ce
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632206"
---
# <a name="set-up-microsoft-purview-audit-standard"></a>Konfigurowanie Inspekcja w Microsoft Purview (standardowa)

Inspekcja w Microsoft Purview (Standardowa) w usłudze Microsoft 365 umożliwia wyszukiwanie rekordów inspekcji działań wykonywanych w różnych usługach platformy Microsoft 365 przez użytkowników i administratorów. Ponieważ inspekcja (Standardowa) jest domyślnie włączona dla większości organizacji platformy Microsoft 365 i Office 365, należy wykonać tylko kilka czynności, zanim ty i inne osoby w organizacji będą mogły przeszukiwać dziennik inspekcji.

W tym artykule omówiono następujące kroki niezbędne do skonfigurowania inspekcji (Standardowa).

![Kroki konfigurowania inspekcji (Standardowa).](../media/BasicAuditingWorkflow.png)

Te kroki obejmują zapewnienie odpowiednich subskrypcji organizacyjnych i licencjonowania użytkowników wymaganych do generowania i zachowywania rekordów inspekcji oraz przypisywania uprawnień członkom zespołu operacji zabezpieczeń, działów IT, zgodności i zespołów prawnych, aby umożliwić przeszukiwanie dziennika inspekcji.

Aby uzyskać więcej informacji, zobacz [Audit (Standard) in Microsoft 365 (Inspekcja (Standardowa) na platformie Microsoft 365](auditing-solutions-overview.md#audit-standard).

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>Krok 1. Weryfikowanie subskrypcji organizacji i licencjonowania użytkowników

Licencjonowanie inspekcji (Standardowa) wymaga odpowiedniej subskrypcji organizacji, która zapewnia dostęp do narzędzia do wyszukiwania dzienników inspekcji i licencjonowania dla poszczególnych użytkowników, które są wymagane do rejestrowania i przechowywania rekordów inspekcji.

Gdy inspekcja działania jest wykonywana przez użytkownika lub administratora, rekord inspekcji jest generowany i przechowywany w dzienniku inspekcji organizacji. W obszarze Inspekcja (Standardowa) rekordy inspekcji są przechowywane i przeszukiwane w dzienniku inspekcji przez 90 dni.

Aby uzyskać listę wymagań dotyczących subskrypcji i licencjonowania dla usługi Audit (Standard), zobacz [Auditing solutions in Microsoft 365 (Rozwiązania do inspekcji na platformie Microsoft 365](auditing-solutions-overview.md#licensing-requirements)).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>Krok 2. Przypisywanie uprawnień do przeszukiwania dziennika inspekcji

Administratorzy i członkowie zespołów badawczych muszą mieć przypisaną rolę View-Only Dzienniki inspekcji lub Dzienniki inspekcji w Exchange Online, aby przeszukać dziennik inspekcji. Domyślnie te role są przypisywane do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie **Uprawnienia** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centrum administracyjnym programu Exchange</a>. Administratorzy globalni w Office 365 i microsoft 365 są automatycznie dodawani jako członkowie grupy ról Zarządzanie organizacją w Exchange Online. Aby umożliwić użytkownikowi przeszukiwanie dziennika inspekcji z minimalnym poziomem uprawnień, możesz utworzyć niestandardową grupę ról w Exchange Online, dodać rolę View-Only Dzienniki inspekcji lub Dzienniki inspekcji, a następnie dodać użytkownika jako członka nowej grupy ról. Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami ról w Exchange Online](/Exchange/permissions-exo/role-groups).

Poniższy zrzut ekranu przedstawia dwie role związane z inspekcją przypisane do grupy ról Zarządzanie organizacją w Centrum administracyjnym programu Exchange.

![Inspekcja ról przypisanych do grupy ról w Exchange Online.](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>Krok 3. Przeszukiwanie dziennika inspekcji

Teraz możesz już przeszukać dziennik inspekcji w portal zgodności Microsoft Purview.

1. Przejdź do strony <https://compliance.microsoft.com> i zaloguj się przy użyciu konta, do których przypisano odpowiednie uprawnienia inspekcji.

2. W okienku nawigacji po lewej stronie portalu zgodności kliknij pozycję **Pokaż wszystko** , a następnie kliknij pozycję **Inspekcja**.

3. Na stronie **Inspekcja** skonfiguruj wyszukiwanie przy użyciu następujących warunków na karcie **Wyszukiwanie** . 

   ![Ustawienia konfiguracji wyszukiwania dzienników inspekcji.](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Zakres dat i godzin**. Wybierz zakres dat i godzin, aby wyświetlić zdarzenia, które wystąpiły w tym okresie. Data i godzina są prezentowane w godzinach lokalnych. Domyślnie wybierane są ostatnie siedem dni.
  
   2. **Działania**. Wybierz działania do wyszukania. Użyj pola wyszukiwania, aby wyszukać działania, które mają zostać dodane do listy. Aby uzyskać częściową listę inspekcji działań, zobacz [Inspekcja działań](search-the-audit-log-in-security-and-compliance.md#audited-activities). Pozostaw to pole puste, aby zwrócić wpisy dla wszystkich inspekcji działań.
  
   3. **Użytkownicy**.  Kliknij to pole i zacznij wpisywać nazwę użytkowników, aby wyświetlić wyniki wyszukiwania. Wpisy dziennika inspekcji dla wybranych działań wykonywanych przez użytkowników wybranych w tym polu są wyświetlane na liście wyników. Pozostaw to pole puste, aby zwrócić wpisy dla wszystkich użytkowników (i kont usług) w organizacji.
  
   4. **Plik, folder lub witryna**. Wpisz część lub wszystkie nazwy pliku lub folderu, aby wyszukać działanie związane z plikiem folderu zawierającym określone słowo kluczowe. Możesz również określić adres URL pliku lub folderu. Jeśli używasz adresu URL pliku lub folderu, upewnij się, że wpisz pełną ścieżkę adresu URL lub jeśli wpiszesz część adresu URL, nie dołącz żadnych znaków specjalnych ani spacji. Pozostaw to pole puste, aby zwrócić wpisy dla wszystkich plików i folderów w organizacji.

4. Kliknij pozycję **Wyszukaj** , aby uruchomić wyszukiwanie.

Zostanie wyświetlona nowa strona pokazująca, że wyszukiwanie w dzienniku inspekcji jest uruchomione. Po zakończeniu wyszukiwania rekordy inspekcji są wyświetlane na stronie. Kliknij rekord, aby wyświetlić stronę wysuwaną ze szczegółowymi właściwościami.

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Wyszukiwanie dziennika inspekcji w centrum zgodności](search-the-audit-log-in-security-and-compliance.md).
