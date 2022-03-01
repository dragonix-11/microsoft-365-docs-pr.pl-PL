---
title: Wyświetlanie kondycji usług dzierżawy
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
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse się, jak wyświetlić kondycję usług dzierżawy.
ms.openlocfilehash: b7361865e0ad3f070e128207a92669f3515e9969
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027078"
---
# <a name="view-tenant-service-health"></a>Wyświetlanie kondycji usług dzierżawy

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i są dostępne tylko dla partnerów spełniających [te wymagania](m365-lighthouse-requirements.md). Jeśli Twoja organizacja nie ma konta Microsoft 365 Lighthouse, zobacz Logowanie [się w celu Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Możesz wyświetlić kondycję usług dla dzierżaw, które zarządzasz w Microsoft 365 Lighthouse. Kondycja usługi obejmuje zdarzenia i doradcy dotyczące kilku usług, w tym usług Microsoft Intune, usług tożsamości usługi Azure Active Directory (Azure AD) i usług zarządzania urządzeniami przenośnymi w chmurze. Możesz również zobaczyć, na ilu dzierżawach zarządzanych mają wpływ zdarzenia. Jeśli na przykład u jednej z dzierżaw występują problemy, możesz sprawdzić na stronie Kondycja usługi, czy jest to znany problem w trakcie rozwiązywania lub czy ostatnia zmiana może mieć na nie wpływ. Może to zaoszczędzić czas podczas rozwiązywania problemów i ograniczyć liczbę rozmów z wołami o pomoc techniczną.

Jeśli nie możesz zalogować się do usługi Lighthouse, możesz za pomocą strony stanu usługi [Microsoft 365](https://status.office365.com/) sprawdzić znane problemy uniemożliwiające zalogowanie się do dzierżawy partnera. Zarejestruj się, aby obserwować [@MSFT365status w](https://twitter.com/MSFT365Status) serwisie Twitter, aby wyświetlić informacje na temat określonych zdarzeń dotyczących usługi.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wyświetlić kondycję usługi, potrzebujesz roli usługi Azure AD w dzierżawie partnera z następującym zestawem właściwości: **microsoft.office365.serviceHealth/allEntities/allTasks**. Aby uzyskać listę ról usługi Azure AD, zobacz [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>Wyświetlanie stanu kondycji usługi dla wszystkich dzierżaw

1. W lewym okienku nawigacji w aplikacji Lighthouse wybierz pozycję **Kondycja usługi**.

2. Na stronie **Kondycja** usługi sprawdź bieżący stan kondycji usługi, w tym:

   -   Łączna liczba zdarzeń
   -   Łączna liczba porad mających wpływ na dowolną dzierżawę zarządzaną
   -   Liczba usług z aktywnymi zdarzeniami.

3. Na karcie **Wszystkie usługi** przejrzyj problemy według usług.

4. Na karcie **Wszystkie problemy** przejrzyj wszystkie bieżące problemy.

## <a name="review-issue-details"></a>Przejrzyj szczegóły problemu

1. W lewym okienku nawigacji w aplikacji Lighthouse wybierz pozycję **Kondycja usługi**.

2. Na stronie **Kondycja** usługi wybierz **kartę Wszystkie usługi** lub **Wszystkie** problemy.

3. Wybierz problem z listy.

4. W okienku szczegółów problemu przejrzyj szczegółowe informacje, takie jak typ problemu, dzierżawy, wpływ na użytkownika i historia problemów.

Na karcie **Dzierżawy** , których dotyczy problem, możesz wyeksportować listę dzierżaw, których dotyczy problem, do pliku wartości wspólnych (cvs), aby udostępnić go zespołom pomocy technicznej.

## <a name="related-content"></a>Zawartość pokrewna
[Jak sprawdzić Microsoft 365 kondycji usługi](/microsoft-365/enterprise/view-service-health) (artykuł)
