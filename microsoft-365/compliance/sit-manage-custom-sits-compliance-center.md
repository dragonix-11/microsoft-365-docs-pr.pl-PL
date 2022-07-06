---
title: Zarządzaj niestandardowymi typami informacji poufnych w centrum zgodności
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
ms.openlocfilehash: 5e0b1b91fd19a5e0705ad95affe888a87847caf8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621973"
---
# <a name="manage-custom-sensitive-information-types-in-the-compliance-center"></a>Zarządzanie niestandardowymi typami informacji poufnych w Centrum zgodności

W tym artykule przedstawiono kroki modyfikowania i usuwania istniejącego niestandardowego typu informacji poufnych w Centrum zgodności.

## <a name="modify-custom-sensitive-information-types-in-the-compliance-center"></a>Modyfikowanie niestandardowych typów informacji poufnych w Centrum zgodności

1. W Centrum zgodności przejdź do pozycji Typy **informacji poufnych** **klasyfikacji** \> danych i wybierz typ informacji poufnych z listy, którą chcesz zmodyfikować, wybierz pozycję **Edytuj**.

2. Możesz dodać inne wzorce z unikatowymi elementami podstawowymi i pomocniczymi, poziomami ufności, bliskością znaków oraz [**dodatkowymi kontrolami**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) lub edytować/usunąć istniejące.

## <a name="remove-custom-sensitive-information-types-in-the-compliance-center"></a>Usuwanie niestandardowych typów informacji poufnych w Centrum zgodności 

> [!NOTE]
> Można usuwać tylko niestandardowe typy informacji poufnych; Nie można usunąć wbudowanych typów informacji poufnych.

> [!IMPORTANT]
> Przed usunięciem niestandardowego typu informacji poufnych sprawdź, czy żadne zasady DLP ani reguły przepływu poczty programu Exchange (znane również jako reguły transportu) nie odwołują się do typu informacji poufnych.

1. W Centrum zgodności przejdź do pozycji **Typy informacji poufnych** **klasyfikacji** \> danych i wybierz typ informacji poufnych z listy, którą chcesz usunąć.

2. W wyświetlonym menu wysuwnym wybierz pozycję **Usuń**.
