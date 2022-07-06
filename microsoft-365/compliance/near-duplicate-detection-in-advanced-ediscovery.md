---
title: Niemal zduplikowane wykrywanie w środowisku zbierania elektronicznych materiałów dowodowych
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
description: Wykrywanie zbliżonych do duplikatów umożliwia grupowanie dokumentów podobnych tekstowo podczas analizowania danych przypadków w usłudze eDiscovery (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 985374558189b2001c6f11e09581f7cb3ed6d11b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622574"
---
# <a name="near-duplicate-detection-in-ediscovery-premium"></a>Wykrywanie niemal duplikatów w środowisku zbierania elektronicznych materiałów dowodowych (Premium)

Rozważmy zestaw dokumentów do przejrzenia, w którym podzestaw jest oparty na tym samym szablonie i ma w większości ten sam język standardowy, z kilkoma różnicami tu i tam. Jeśli recenzent może zidentyfikować ten podzestaw, dokładnie przejrzyj jeden z nich i przejrzyj różnice w pozostałych, nie przegapiłby żadnych unikatowych informacji, poświęcając tylko ułamek czasu, który zajęłoby im przeczytanie wszystkich dokumentów. Niemal zduplikowane grupy wykrywania razem zbliżą się tekstowo do dokumentów, aby ułatwić bardziej wydajny proces przeglądu.

## <a name="how-does-it-work"></a>Jak to działa?

Po uruchomieniu wykrywania zduplikowanych zbliżeń system analizuje każdy dokument za pomocą tekstu. Następnie porównuje każdy dokument ze sobą, aby określić, czy ich podobieństwo jest większe niż ustalony próg. Jeśli tak jest, dokumenty są grupowane razem. Po porównaniu i zgrupowania wszystkich dokumentów dokument z każdej grupy jest oznaczony jako "przestawny"; przeglądając dokumenty, możesz najpierw przejrzeć tabelę przestawną i przejrzeć inne dokumenty w tym samym zestawie niemal zduplikowanym, koncentrując się na różnicy między tabelą przestawną a dokumentem, który jest w trakcie przeglądu.
