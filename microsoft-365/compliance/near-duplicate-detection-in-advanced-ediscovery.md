---
title: Wykrywanie niemal duplikatów — zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Grupowanie dokumentów podobnych tekstowo podczas analizowania danych dotyczących sprawy w programie Advanced eDiscovery.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: cbd01bd38f45a397a82a8db3774997349f4eec88
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987273"
---
# <a name="near-duplicate-detection-in-advanced-ediscovery"></a>Wykrywanie niemal duplikatów w Advanced eDiscovery

Rozważ przejrzenie zestawu dokumentów, w którym podzbiór jest oparty na tym samym szablonie i ma przeważnie ten sam język boilerplate i istnieje kilka różnic między nimi. Jeśli recenzent będzie mógł dokładnie zidentyfikować ten podzbiór, dokładnie przejrzeć jeden z nich i zapoznać się z różnicami dla pozostałych, nie przegapi żadnych unikatowych informacji, nie przeocząc w ciągu zaledwie ułamka czasu, który zajęłoby im przeczytanie wszystkich dokumentów, które zostałyby omówne. Niemal duplikaty wykrywania grupuje dokumenty podobne tekstowo, aby ułatwić wydajniejszą weryfikację.

## <a name="how-does-it-work"></a>Jak to działa?

Po uruchomieniu niemal automatycznego wykrywania duplikatów system analizuje wszystkie dokumenty z tekstem. Następnie porównuje każdy dokument ze sobą, aby ustalić, czy ich podobieństwo jest większe od ustawionego progu. Jeśli tak, dokumenty są grupowane. Po porównaniu i zgrupowaniu wszystkich dokumentów dokumenty z poszczególnych grup są oznaczane jako "przestawne". Przeglądając dokumenty, można najpierw przejrzeć tabelę przestawną i przejrzeć pozostałe dokumenty w tym samym, niemal zduplikowaowym zestawie, skupiając się na różnicy między tabelą przestawną a recenzentem dokumentu.
