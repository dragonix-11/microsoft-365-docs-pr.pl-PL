---
title: Zarządzanie niestandardowymi typami informacji poufnych w Centrum zgodności
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak modyfikować i usuwać niestandardowe typy informacji poufnych w Centrum zgodności.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0efbb93096fc3c0b61a57319aa2d23a079f684d1
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014892"
---
# <a name="manage-custom-sensitive-information-types-in-the-compliance-center"></a>Zarządzanie niestandardowymi typami informacji poufnych w Centrum zgodności

Ten artykuł zawiera instrukcje modyfikowania i usuwania istniejącego niestandardowego typu informacji poufnych w Centrum zgodności.

## <a name="modify-custom-sensitive-information-types-in-the-compliance-center"></a>Modyfikowanie niestandardowych typów informacji poufnych w Centrum zgodności

1. W Centrum zgodności przejdź do tematu **Typy** \> informacji poufnych klasyfikacji danych i wybierz z listy typ informacji poufnych, który chcesz zmodyfikować, wybierz pozycję **Edytuj**.

2. Możesz dodać inne wzorce, z unikatowymi elementami podstawowymi i obsługowymi, poziomami ufności, [](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) sąsiedztwem znaków oraz dodatkowymi testami lub edytowaniem/usuwaniem istniejących.

## <a name="remove-custom-sensitive-information-types-in-the-compliance-center"></a>Usuwanie niestandardowych typów informacji poufnych z Centrum zgodności 

> [!NOTE]
> Możesz usuwać tylko niestandardowe typy informacji poufnych. nie można usunąć wbudowanych typów informacji poufnych.

> [!IMPORTANT]
> Przed usunięciem niestandardowego typu informacji poufnych upewnij się, że żadne zasady DLP Exchange przepływu poczty e-mail (nazywane także regułami transportu) nadal odwołują się do typu informacji poufnych.

1. W Centrum zgodności przejdź do tematu **Typy** \> informacji poufnych klasyfikacji danych i wybierz z listy typ informacji poufnych, który chcesz usunąć.

2. Z otwartego wysuwu wybierz pozycję **Usuń**.
