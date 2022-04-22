---
title: Wyświetlanie kondycji usługi dzierżawy w Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się, jak wyświetlać kondycję usługi dzierżawy.
ms.openlocfilehash: c5cfed4449fbdbb6cb63bc80dfd8e23ca4d5c4bb
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023618"
---
# <a name="view-tenant-service-health-in-microsoft-365-lighthouse"></a>Wyświetlanie kondycji usługi dzierżawy w Microsoft 365 Lighthouse

Kondycję usługi można wyświetlić dla dzierżaw zarządzanych w Microsoft 365 Lighthouse. Kondycja usługi obejmuje zdarzenia i porady dotyczące kilku usług, w tym usług w chmurze Microsoft Intune, Azure Active Directory (Azure AD) i zarządzania urządzeniami przenośnymi (MDM). Możesz również zobaczyć, ilu dzierżaw zarządzanych dotyczy zdarzenia. Jeśli na przykład w jednej z dzierżaw wystąpią problemy, możesz sprawdzić stronę Kondycja usługi, aby ustalić, czy jest to znany problem z rozwiązaniem w toku, czy też ostatnia zmiana może mieć na nie wpływ. Może to zaoszczędzić czas na rozwiązywaniu problemów i zmniejsz liczbę wywołań pomocy technicznej.

Jeśli nie możesz zalogować się do usługi Lighthouse, możesz użyć strony stanu [kondycji usługi Microsoft 365](https://status.office365.com/), aby sprawdzić, czy występują znane problemy uniemożliwiające zalogowanie się do dzierżawy partnera. Ponadto zarejestruj się, aby śledzić [@MSFT365status](https://twitter.com/MSFT365Status) w serwisie Twitter, aby wyświetlić informacje o konkretnych zdarzeniach usługi.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wyświetlić kondycję usługi, musisz mieć rolę usługi Azure AD w dzierżawie partnera z następującym zestawem właściwości: **microsoft.office365.serviceHealth/allEntities/allTasks**. Aby uzyskać listę ról usługi Azure AD, zobacz [Role wbudowane usługi Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>Wyświetlanie stanu kondycji usługi dla wszystkich dzierżaw

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Kondycja usługi**.

2. Na stronie **Kondycja usługi** przejrzyj bieżący stan kondycji usługi, w tym:

   - Całkowita liczba zdarzeń
   - Całkowita liczba porad mających wpływ na dowolną z zarządzanych dzierżaw
   - Liczba usług z aktywnymi zdarzeniami.

3. Na karcie **Wszystkie usługi** przejrzyj problemy według usługi.

4. Na karcie **Wszystkie problemy** przejrzyj wszystkie bieżące problemy.

## <a name="review-issue-details"></a>Przejrzyj szczegóły problemu

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Kondycja usługi**.

2. Na stronie **Kondycja usługi** wybierz kartę **Wszystkie usługi** lub **Wszystkie problemy**.

3. Wybierz problem z listy.

4. W okienku szczegółów problemu przejrzyj szczegółowe informacje, w tym typ problemu, dzierżawy, których dotyczy problem, wpływ na użytkownika i historię problemów.

Na **karcie Dzierżawy, których dotyczy problem** , możesz wyeksportować listę dzierżaw, których dotyczy problem, do pliku wartości rozdzielanych przecinkami (.csv), aby można było go udostępnić zespołom pomocy technicznej.

## <a name="related-content"></a>Zawartość pokrewna

[Jak sprawdzić kondycję usługi Microsoft 365](/microsoft-365/enterprise/view-service-health) (artykuł)\
[Znane problemy z Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (artykuł)
