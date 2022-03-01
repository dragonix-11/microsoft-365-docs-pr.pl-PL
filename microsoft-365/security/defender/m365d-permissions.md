---
title: Zarządzanie dostępem do Microsoft 365 Defender danych w portalu Microsoft 365 Defender sieci Microsoft 365 Defender sieci
description: Dowiedz się, jak zarządzać uprawnieniami do danych w aplikacji Microsoft 365 Defender
keywords: dostęp, uprawnienia, Microsoft 365 Defender, M365, zabezpieczenia, MCAS, Cloud App Security, Microsoft Defender for Endpoint, zakres, zakres, RBAC
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 8e9cacf3fb7d74acc210ac0b77ed5e68c7a93961
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2022
ms.locfileid: "63009675"
---
# <a name="manage-access-to-microsoft-365-defender-with-azure-active-directory-global-roles"></a>Zarządzanie dostępem do Microsoft 365 Defender za pomocą Azure Active Directory ról globalnych

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Istnieją dwa sposoby zarządzania dostępem do Microsoft 365 Defender:
- **Role Azure Active Directory globalnej (AD)**
- **Niestandardowy dostęp do roli**

Konta z przypisanymi **następującymi rolami Azure Active Directory globalnej (AD)** mogą Microsoft 365 Defender funkcji i danych:
- Administrator globalny
- Administrator zabezpieczeń
- Operator zabezpieczeń
- Czytnik globalny
- Czytnik zabezpieczeń

Aby przejrzeć konta z tymi rolami, [wyświetl uprawnienia w portalu Microsoft 365 Defender użytkowników](https://security.microsoft.com/permissions).

**Niestandardowy dostęp do** roli to nowa funkcja w programie Microsoft 365 Defender umożliwiająca zarządzanie dostępem do określonych danych, zadań i możliwości w aplikacji Microsoft 365 Defender. Role niestandardowe zapewniają większą kontrolę niż globalne role w usłudze Azure AD, zapewniając użytkownikom tylko potrzebny dostęp przy użyciu ról o najmniejszych możliwościach.  Oprócz ról globalnych usługi Azure AD można tworzyć role niestandardowe. [Dowiedz się więcej o rolach niestandardowych](custom-roles.md).

> [!NOTE]
> Ten artykuł dotyczy tylko zarządzania rolami globalnymi Azure Active Directory użytkowników. Aby uzyskać więcej informacji na temat używania niestandardowej kontroli dostępu opartej na rolach, zobacz [Niestandardowe role dla kontroli dostępu opartej na rolach.](custom-roles.md)

## <a name="access-to-functionality"></a>Dostęp do funkcji
Dostęp do konkretnych funkcji jest ustalany na podstawie [roli usługi Azure AD](/azure/active-directory/roles/permissions-reference). Skontaktuj się z administratorem globalnym, jeśli potrzebujesz dostępu do konkretnych funkcji, które wymagają przypisania Ci lub Twojej grupy użytkowników do nowej roli.

### <a name="approve-pending-automated-tasks"></a>Zatwierdzanie oczekujących zadań automatycznych
[Zautomatyzowane badania i działania](m365d-autoir-actions.md) naprawcze mogą być podejmowanie działań w związku z wiadomościami e-mail, regułami przesyłania dalej, plikami, mechanizmami trwałymi i innymi artefaktami znalezionymi podczas dochodzenia. Aby zatwierdzać lub odrzucać akcje oczekujące wymagające jawnego zatwierdzenia, musisz mieć przypisane określone role w Microsoft 365. Aby dowiedzieć się więcej, zobacz [Uprawnienia do Centrum akcji](m365d-action-center.md#required-permissions-for-action-center-tasks).

## <a name="access-to-data"></a>Dostęp do danych
Dostęp do Microsoft 365 Defender danych można kontrolować przy użyciu zakresu przypisanego do grup użytkowników w programie Microsoft Defender dla kontroli dostępu opartej na rolach (RBAC, Endpoint for Endpoint). Jeśli Twój dostęp nie został ograniczony do określonego zestawu urządzeń w uchcie Defender for Endpoint, będziesz mieć pełny dostęp do danych w programie Microsoft 365 Defender. Jednak po zawę zobaczycie tylko dane o urządzeniach w zakresie.

Jeśli na przykład należysz tylko do jednej grupy użytkowników z rolą Programu Microsoft Defender dla punktu końcowego i ta grupa użytkowników otrzymała dostęp tylko do urządzeń sprzedaży, będą dla Ciebie dostępne tylko dane o urządzeniach do sprzedaży w Microsoft 365 Defender. [Dowiedz się więcej o ustawieniach RBAC w programie Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/rbac)

### <a name="microsoft-defender-for-cloud-apps-access-controls"></a>Program Microsoft Defender dla aplikacji w chmurze kontroli dostępu
Podczas wyświetlania wersji zapoznawczej Microsoft 365 Defender kontroli dostępu opartej na ustawieniach usługi Defender dla aplikacji w chmurze. Te ustawienia nie Microsoft 365 Defender mają wpływu na dostęp do danych.

## <a name="related-topics"></a>Tematy pokrewne
- [Niestandardowe role w kontroli dostępu opartej na rolach dla Microsoft 365 Defender](custom-roles.md)
- [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference)
- [Program Microsoft Defender dla punktu końcowego RBAC](/windows/security/threat-protection/microsoft-defender-atp/rbac)
- [Role w usłudze Defender dla aplikacji w chmurze](/cloud-app-security/manage-admins)
