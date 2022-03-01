---
title: Przypisywanie dostępu użytkownika do Centrum zabezpieczeń usługi Microsoft Defender
description: Przypisz dostęp tylko do odczytu i zapisu lub odczytu do portalu programu Microsoft Defender dla punktu końcowego.
keywords: przypisywanie ról użytkowników, przypisywanie dostępu do odczytu i zapisu, przypisywanie dostępu tylko do odczytu, użytkownik, role użytkownika, role
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.date: 11/28/2018
ms.technology: mde
ms.openlocfilehash: fa0157a37cf25efcdcf1b578473b4dc2f6deb10d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998133"
---
# <a name="assign-user-access-to-microsoft-defender-security-center"></a>Przypisywanie dostępu użytkownika do Centrum zabezpieczeń usługi Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- Azure Active Directory
- Usługa Office 365
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Program Defender for Endpoint obsługuje dwa sposoby zarządzania uprawnieniami:

- **Podstawowe zarządzanie uprawnieniami**: Ustaw uprawnienia na pełny dostęp lub tylko do odczytu.
- **Kontrola dostępu oparta na rolach( RBAC**, Role based access control): Ustaw szczegółowe uprawnienia, definiując role, przypisując grupy użytkowników usługi Azure AD do ról i udzielając grupom użytkowników dostępu do grup urządzeń. Aby uzyskać więcej informacji na temat RBAC, zobacz [Zarządzanie dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md).

> [!NOTE]
> Jeśli masz już przypisane uprawnienia podstawowe, możesz przełączyć się do RBAC w dowolnym momencie. Przed dokonaniem zmiany warto rozważyć następujące kwestie:
>
> - Użytkownikom z pełnym dostępem (z przypisaną rolą administratora globalnego lub administratora zabezpieczeń w usłudze Azure AD) jest automatycznie przypisywana domyślna rola administratora programu Defender dla punktu końcowego, która również ma pełny dostęp. Po przełączeniu do RBAC można przypisywać dodatkowe grupy użytkowników usługi Azure AD do roli administratora programu Defender dla punktu końcowego. Tylko użytkownicy przypisani do roli administratora programu Defender dla punktu końcowego mogą zarządzać uprawnieniami przy użyciu RBAC. 
> - Użytkownicy z dostępem tylko do odczytu (czytniki zabezpieczeń) utracą dostęp do portalu, dopóki nie zostaną przypisani do roli. W ramach RBAC można przypisywać tylko grupy użytkowników usługi Azure AD.
> - Po przełączeniu do RBAC nie będzie można wrócić do korzystania z podstawowego zarządzania uprawnieniami.

## <a name="related-topics"></a>Tematy pokrewne

- [Używanie podstawowych uprawnień w celu uzyskiwania dostępu do portalu](basic-permissions.md)
- [Zarządzanie dostępem do portalu przy użyciu RBAC](rbac.md)
