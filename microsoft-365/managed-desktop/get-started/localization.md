---
title: Localize the user experience
description: Jak zlokalizowane urządzenia dla użytkowników
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
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
ms.openlocfilehash: c429a072d6ceb2d5d1472533649e30d1fc1a0078
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525005"
---
# <a name="localize-the-user-experience"></a>Localize the user experience

Użytkownicy Microsoft Managed Desktop urządzeniach mogą wybrać język podczas procesu konfiguracji ("out of box experience") lub później.

## <a name="during-setup-the-out-of-box-experience"></a>Podczas instalacji ("środowisko", które jest poza polem wyboru)

Podczas instalacji użytkownicy mogą wybrać język. To zaznaczenie ma wpływ na następujące atrybuty:

| Atrybut | Opis |
| ------ | ------ |
| Windows 10 funkcji językowych | <ul><li>Język wyświetlania</li><li>Język klawiatury</li><li>Funkcje związane z językiem na żądanie</li><ul> |
| Aplikacje Microsoft 365 do Enterprise funkcji językowych | <ul><li>Język wyświetlania</li><li>Narzędzia do erowania i tworzenia</li></ul> |

> [!NOTE]
> Użytkownicy mogą uzyskać funkcje na żądanie związane z językiem tylko przez wybranie języka w trakcie procesu konfiguracji.

## <a name="after-completing-setup"></a>Po ukończeniu instalacji

Użytkownicy mogą wybrać język używany w programie Windows 10, a Aplikacje Microsoft 365 dla Enterprise dowolnym momencie po zakończeniu procesu konfiguracji. Konkretnie:

| Funkcja | Opis |
| ------ | ------ |
| Windows 10 funkcji językowych | <ul><li>Język wyświetlania</li><li>Język klawiatury</li><ul> |
| Aplikacje Microsoft 365 do Enterprise funkcji językowych | <ul><li>Język wyświetlania</li><li>Narzędzia do erowania i tworzenia</li></ul> |

## <a name="install-more-languages"></a>Instalowanie większej liczby języków

> [!NOTE]
> Z dniem 16 marca 2022 r. wycofujemy grupę Modern Workplace-Office-Language_Packs, która umożliwia Twoim użytkownikom dodawanie języków do Microsoft Office. Przejście na nową metodę (zobacz poniżej) zostanie ukończone w kwietniu 2022 r. Jeśli w tym okresie przejścia będą jakieś problemy, skontaktuj się z pomocy [technicznej](../working-with-managed-desktop/admin-support.md).

Domyślnie pakiet Microsoft Office administratorów. Program Microsoft Managed Desktop wdraża zasady programu Office w celu umożliwienia użytkownikom standardowym instalowania pakietów akcesoriów językowych bezpośrednio z ich Office aplikacji. Aby uzyskać więcej informacji, zobacz [Zezwalanie użytkownikom, którzy nie są administratorami, na instalowanie dodatkowych języków](/deployoffice/overview-deploying-languages-microsoft-365-apps#allow-users-who-arent-admins-to-install-additional-languages).

## <a name="supported-languages"></a>Obsługiwane języki

W przypadku nowych urządzeń producent musi udostępnić obrazy urządzeń, które zawierają wymagane języki. Jeśli obraz producenta zawiera języki, których nie ma na liście obsługiwanych języków, urządzenie jest nadal obsługiwane przez usługę.

Jeśli używasz istniejących urządzeń, może być konieczne uzyskanie odpowiednich obrazów we współpracy z przedstawicielem konta Microsoft. Aby uzyskać więcej informacji, zobacz [Obrazy urządzeń](../service-description/device-images.md).

Obraz [uniwersalny dostarczony](../service-description/device-images.md#universal-image) przez program Microsoft Managed Desktop zawiera następujące języki oraz pliki Windows 10:

- Arabski
- Bulgarian
- Chinese Simplified
- Chinese Traditional
- Croatian
- Czech
- Danish  
- Dutch  
- Angielski (US, GB, AU, CA, IN)
- Estonian
- Finnish
- Francuski (Francja, Kanada)
- German
- Greek
- Hebrew
- Hungarian
- Indonesian
- Italian
- Japanese
- Korean
- Latvian
- Lithuanian
- Norweski (Bokmål)
- Polish
- Portugalski (Brazylia)
- Portugalski (Portugalia)
- Romanian
- Russian
- Serbski (alfabet łaciński)
- Slovak
- Slovenian
- Hiszpański (Hiszpania, Meksyk)
- Swedish
- Thai
- Turkish
- Ukrainian
- Vietnamese

> [!NOTE]
> Aplikacje Microsoft 365 for Enterprise może obsługiwać nieco inną listę.

Jeśli użytkownicy potrzebują języka innego niż wymienione tutaj, zsyłaj wniosek o pomoc [techniczną](../working-with-managed-desktop/admin-support.md) za pomocą [portalu administracyjnego](access-admin-portal.md).

## <a name="languages-for-support-and-operations"></a>Języki pomocy technicznej i operacji

### <a name="admin-support-and-operations"></a>Pomoc techniczna i obsługa administracyjna

Microsoft Managed Desktop obsługuje administratorów tylko w języku angielskim. Ta pomoc techniczna obejmuje portal administratora i całą komunikację z Microsoft Managed Desktop biznesowych. Należy założyć, że wszystkie interakcje i interfejsy związane z administratorami będą w języku angielskim, o ile nie określono inaczej.
