---
title: Usuwanie urządzeń
description: Usuwanie urządzeń z zarządzania Microsoft Managed Desktop sieci
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 82e14fbd2bc991505c84d219c0624f52791376d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324581"
---
# <a name="remove-devices"></a>Usuwanie urządzeń

Urządzenia można usuwać z Microsoft Managed Desktop, korzystając z portalu administracyjnego. Ta akcja jest trwała, ale możesz zarejestrować je w Microsoft Managed Desktop ponownie, korzystając z instrukcji [ręcznej rejestracji](../get-started/manual-registration.md).

Po usunięciu urządzenia występują wszystkie następujące zdarzenia:

- Usuwamy urządzenie z rozwiązania Autopilot.
- Usuwamy urządzenie ze wszystkich grup urządzeń "Nowoczesne miejsce pracy".
- Usuwamy urządzenie z **bladego Urządzenia** w portalu administracyjnym.

Po usunięciu urządzenia możesz je również usunąć z usługi Azure Active Directory (Azure AD) i Microsoft Intune.
  
> [!CAUTION]
> Usuwanie obiektów powiązanych z urządzeniem z usług Azure AD i Microsoft Intune jest trwałe. Po usunięciu obiektów nie będzie można wyświetlać urządzeń ani nimi zarządzać z usług Intune i Azure Portals. Urządzenia nie będą mogły uzyskać dostępu do zasobów firmy. Dane firmy mogą zostać z nich usunięte, jeśli urządzenia spróbują się zalogować po ich usunięciu.

**Aby usunąć urządzenie:**

1. W [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) nawigacji wybierz **pozycję Urządzenia** w lewym okienku nawigacji.
2. W sekcji **Microsoft Managed Desktop** wybierz pozycję **Urządzenia**.
3. W obszarze **Microsoft Managed Desktop obszar roboczy** Urządzenia wybierz urządzenia, które chcesz usunąć.
4. Wybierz **pozycję Akcje urządzenia**, a następnie wybierz **pozycję Usuń urządzenie** , co spowoduje otwarcie wysuwu w celu usunięcia urządzeń.
5. W locie przejrzyj wybrane urządzenia, a następnie wybierz pozycję **Usuń urządzenia**. Jeśli chcesz jednocześnie usunąć obiekty usług Azure AD i Intune, zaznacz pole wyboru. Usunięcie urządzenia może potrwać kilka minut.

> [!NOTE]
> Nie można usuwać urządzeń, które znajdują się w stanie **oczekującym** na rejestrację.
