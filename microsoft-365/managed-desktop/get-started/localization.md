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
ms.openlocfilehash: c7930215efac4e02a6a0bab484e9158ad693997a
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016009"
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

Aby [udostępnić](#supported-languages) użytkownikom do instalacji Aplikacje Microsoft 365 obsługiwane języki dla pakietu Enterprise, dodaj użytkowników do grupy Nowoczesne **Office-Language_Packs Workplace-Language_Packs**. Języki będą dostępne w Intune — Portal firmy.

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

### <a name="user-support"></a>Pomoc techniczna dla użytkowników

Microsoft Managed Desktop obsługuje tylko język angielski. Jeśli użytkownik wybierze inny język w aplikacji Uzyskaj pomoc, otrzyma pomoc techniczną z ogólnych kanałów pomocy technicznej firmy Microsoft, a nie bezpośrednio z Microsoft Managed Desktop. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy dla użytkowników](../working-with-managed-desktop/end-user-support.md).

Jeśli użytkownicy potrzebują pomocy technicznej w innych językach, musisz to zapewnić za pośrednictwem źródeł pomocy technicznej innych niż firmy Microsoft lub z Twojej organizacji.

### <a name="admin-support-and-operations"></a>Pomoc techniczna i obsługa administracyjna

Microsoft Managed Desktop obsługuje administratorów tylko w języku angielskim. Ta pomoc techniczna obejmuje portal administratora i całą komunikację z Microsoft Managed Desktop biznesowych. Należy założyć, że wszystkie interakcje i interfejsy związane z administratorami będą w języku angielskim, o ile nie określono inaczej.
