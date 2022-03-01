---
title: Użyj kontroli dostępu opartej na rolach, aby udzielić dostępu precyzyjnego do Microsoft 365 Defender sieci Microsoft 365 Defender.
description: Utwórz role i grupy w ramach swoich operacji zabezpieczeń, aby udzielić dostępu do portalu.
keywords: rbac, rola, based, access, control, groups, control, tier, aad
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8c1ff743aa6c9c215c3894185a4096c9a35a16e0
ms.sourcegitcommit: 6b24f65c987e5ca06e6d5f4fc10804cdbe68b034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996404"
---
# <a name="manage-portal-access-using-role-based-access-control"></a>Zarządzanie dostępem do portalu przy użyciu kontroli dostępu opartej na rolach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Azure Active Directory
- Usługa Office 365

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-rbac-abovefoldlink)

Za pomocą kontroli dostępu opartej na rolach (RBAC, role i grupy) możesz tworzyć role i grupy w ramach zespołu operacji zabezpieczeń, aby udzielić odpowiedniego dostępu do portalu. W zależności od tego, jakie role i grupy utworzysz, masz pełną kontrolę nad tym, co użytkownicy z dostępem do portalu mogą widzieć i robić. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bJ2a]

Duże zespoły ds. operacji zabezpieczeń rozproszonej geograficznie zazwyczaj przyjmują model oparty na warstwie w celu przypisywania i autoryzowania dostępu do portali zabezpieczeń. Typowe warstwy obejmują następujące trzy poziomy:

Warstwa|Opis|
:---|:---|
Poziom 1|**Lokalny zespół operacyjny ds. zabezpieczeń / zespół IT** <br> Ten zespół zazwyczaj sprawdza i bada alerty zawarte w ich lokalizacji geograficznej i eskalacji do warstwy 2 w przypadkach, gdy wymagane jest aktywne działania naprawcze.|
Warstwa 2|**Regionalny zespół operacyjny ds. zabezpieczeń** <br> Ten zespół może wyświetlić wszystkie urządzenia dla swojego regionu i wykonywać działania naprawcze.|
Warstwa 3|**Globalny zespół operacyjny ds. zabezpieczeń** <br> Ten zespół składa się z ekspertów do spraw zabezpieczeń oraz ma uprawnienia do wykonywania wszystkich czynności z portalu.|

> [!NOTE]
> W przypadku zasobów warstwy 0 zapoznaj się z [](/azure/active-directory/privileged-identity-management/pim-configure) Privileged Identity Management administratorami zabezpieczeń, aby zapewnić bardziej szczegółową kontrolę nad usługą Microsoft Defender dla punktów końcowych i Microsoft 365 Defender.  

Program Defender for Endpoint RBAC jest przeznaczony do obsługi wybranego modelu warstwowego lub opartego na rolach i zapewnia szczegółową kontrolę nad tym, jakie role mogą zobaczyć, do jakich urządzeń mogą mieć dostęp i jakie akcje mogą podjąć. W ramach RBAC są wyśrodkowane następujące mechanizmy kontroli:

- **Kontrolowanie, kto może podjąć określone działanie**
  - Twórz niestandardowe role i kontroluj, do jakich funkcji programu Defender dla punktu końcowego mogą uzyskać dostęp w sposób szczegółowy.
- **Sterowanie tym, kto może widzieć informacje dotyczące konkretnych grup urządzeń**
  - [Twórz grupy urządzeń](machine-groups.md) według określonych kryteriów, takich jak nazwy, tagi, domeny i inne, a następnie udzielaj im dostępu roli za pomocą określonej grupy użytkowników usługi Azure Active Directory (Azure AD).

Aby wdrożyć dostęp oparty na rolach, musisz zdefiniować role administratora, przypisać odpowiednie uprawnienia i przypisać do tych ról grupy użytkowników usługi Azure AD.

### <a name="before-you-begin"></a>Przed rozpoczęciem

Przed użyciem RBAC należy zrozumieć role, które mogą udzielać uprawnień i konsekwencje włączania RBAC.

> [!WARNING]
> Przed włączeniem tej funkcji należy mieć rolę administratora globalnego lub administratora zabezpieczeń w usłudze Azure AD i przygotować grupy usługi Azure AD, aby zmniejszyć ryzyko zablokowania dostępu do portalu. 

Gdy logujesz się po raz pierwszy do Microsoft 365 Defender, uzyskujesz pełny dostęp lub dostęp tylko do odczytu. Użytkownikom z rolami administratora zabezpieczeń lub administratora globalnego w usłudze Azure AD są udzielane pełne prawa dostępu. Dostęp tylko do odczytu jest udzielany użytkownikom z rolą czytnika zabezpieczeń w usłudze Azure AD. 

Osoba z rolą administratora globalnego usługi Defender for Endpoint ma nieograniczony dostęp do wszystkich urządzeń, niezależnie od skojarzenia ich grup urządzeń i przypisań grup użytkowników usługi Azure AD.

> [!WARNING]
> Początkowo tylko osoby z uprawnieniami administratora globalnego usługi Azure AD lub administratora zabezpieczeń będą mogły tworzyć i przypisywać role w portalu usługi Microsoft 365 Defender, dlatego ważne jest, aby w usłudze Azure AD były gotowe odpowiednie grupy.
>
> **Włączenie kontroli dostępu opartej na rolach spowoduje, że użytkownicy z uprawnieniami tylko do odczytu (na przykład użytkownicy przypisani do roli czytnika zabezpieczeń usługi Azure AD) utracą dostęp, dopóki nie zostaną przypisani do roli.** 
>
>Użytkownikom z uprawnieniami administratora jest automatycznie przypisywana domyślna wbudowana rola administratora globalnego usługi Defender for Endpoint z pełnymi uprawnieniami. Po wybraniu RBAC możesz przypisać dodatkowych użytkowników, którzy nie są administratorami globalnymi usługi Azure AD ani administratorami zabezpieczeń, do roli administratora globalnego usługi Defender for Endpoint. 
>
> Po zalogowaniu się do korzystania z RBAC nie można przywrócić początkowych ról, tak jak podczas pierwszego logowania do portalu.

## <a name="related-topic"></a>Temat pokrewny

- [Role RBAC](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Tworzenie grup urządzeń i zarządzanie nimi w programie Microsoft Defender dla punktu końcowego](machine-groups.md)
