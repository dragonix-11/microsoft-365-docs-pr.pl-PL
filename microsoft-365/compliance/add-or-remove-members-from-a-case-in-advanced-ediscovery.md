---
title: Dodaj członków do sprawy lub ich usuń
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Dowiedz się, jak dodać lub usunąć członków, którzy mogą uzyskać dostęp do sprawy podczas zarządzania przypadkiem zbierania elektronicznych materiałów dowodowych (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 85a8673e7e3c31ab12cda0109f6c06762adeabf3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091880"
---
# <a name="add-or-remove-members-from-a-case"></a>Dodaj członków do sprawy lub ich usuń

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Możesz dodać lub usunąć członków, aby zarządzać tym, kto może uzyskać dostęp do sprawy. Zanim jednak członek będzie mógł uzyskać dostęp do sprawy zbierania elektronicznych materiałów dowodowych (Premium) (i wykonywać zadania w tym przypadku), musisz dodać użytkownika do grupy ról Menedżera zbierania elektronicznych materiałów dowodowych na stronie **Uprawnienia** w portalu zgodności usługi Microsoft Purview. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](./assign-ediscovery-permissions.md).

1. Na stronie **eDiscovery (Premium)** przejdź do sprawy, do którą chcesz dodać członka.

2. Kliknij kartę **Ustawienia**, a następnie kliknij pozycję **Wybierz** na kafelku **Uprawnienia & dostępu**.

3. W obszarze **Zarządzanie członkami** kliknij pozycję **Dodaj** , aby dodać członków do sprawy. Możesz również dodać grupę ról do sprawy, klikając pozycję  **Dodaj** w obszarze **Zarządzanie grupami ról**.

4. Na liście osób lub grup ról, które można dodać jako członków sprawy, zaznacz pole wyboru obok nazw osób lub grup ról, które chcesz dodać.

   > [!NOTE]
   > Podczas dodawania grupy ról do sprawy można dodać tylko grupy ról, do których należysz.

5. Po wybraniu osób lub grup ról, które mają zostać dodane jako członkowie sprawy, kliknij przycisk **Dodaj**.

6. Na stronie **Manage this case flyout (Zarządzanie tym przypadkiem** ) kliknij pozycję **Zapisz** , aby zapisać nową listę członków sprawy.

> [!IMPORTANT]
> Jeśli rola zostanie dodana lub usunięta z grupy ról, która została dodana jako członek sprawy, grupa ról zostanie automatycznie usunięta jako członek sprawy (lub w każdym przypadku grupa ról jest członkiem). Powodem jest ochrona organizacji przed nieumyślnym udzieleniem dodatkowych uprawnień członkom sprawy. Podobnie, jeśli grupa ról zostanie usunięta, zostanie usunięta ze wszystkich przypadków, do które należała. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases).

## <a name="removing-members-from-a-case"></a>Usuwanie elementów członkowskich ze sprawy

Tylko [administrator zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md) może usunąć członków ze sprawy. Nawet jeśli przypisano Cię do grupy ról menedżera zbierania elektronicznych materiałów dowodowych lub początkowo utworzono przypadek, nie będzie można usunąć siebie ani innych członków ze sprawy, chyba że jesteś również administratorem zbierania elektronicznych materiałów dowodowych. Aby usunąć siebie lub innych członków ze sprawy, skontaktuj się z administratorem zbierania elektronicznych materiałów dowodowych w organizacji.
