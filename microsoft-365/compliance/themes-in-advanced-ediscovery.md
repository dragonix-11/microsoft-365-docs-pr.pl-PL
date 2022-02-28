---
title: Motywy — zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Użyj motywów w Advanced eDiscovery, aby uporządkować zestawy recenzji, znajdując motyw motywu dominującego w każdym dokumencie.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: ed7759353230e80359a771416c01e62d2ec03337
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987271"
---
# <a name="themes-in-advanced-ediscovery"></a>Motywy w programie Advanced eDiscovery

Jak osoba może napisać dokument? Zazwyczaj zaczynają się od jednego lub większej liczby pomysłów, które chcą przekazać w dokumencie, i redagują za pomocą wyrazów, które są zgodne z pomysłami. Im bardziej rozpowszechniony jest pomysł, tym częściej wyrazy związane z tym pomysłem zwykle się powtarzają. Dzięki temu można dowiedzieć się, jak inne osoby również mogą korzystać z dokumentów. Ważną rzeczą, którą należy zrozumieć podczas czytania dokumentu, są pomysły, które dokument próbuje przekazać, które pomysły pojawiają się w miejscu, i relacje między nimi.

Można to rozszerzyć do sposobu, w jaki dana osoba chce korzystać z zestawu dokumentów. Chcą zobaczyć, które pomysły są obecne w zestawach, a które dokumenty mówią o tych pomysłach. Ponadto jeśli znajdą konkretny dokument, który ich interesuje, chcą mieć możliwość zobaczenia dokumentów, w których omawiają podobne pomysły.

Funkcja Motywy w programie Advanced eDiscovery próbach naśladowania przyczyn przyczyn dokumentu przez analizowanie motywów omówinych w zestawie  recenzji i przypisywanie motywu do dokumentów w zestawie recenzji. W Advanced eDiscovery motywy poszły o krok dalej i zidentyfikowały *motyw motywu dominującego* w każdym dokumencie. Motyw dominującej jest tym, który występuje najczęściej w dokumencie.

## <a name="how-does-themes-work"></a>Jak działają motywy?

Funkcja Motywy analizuje dokumenty z tekstem w zestawie recenzji w celu przeanalizowania typowych motywów wyświetlanych we wszystkich dokumentach w zestawie recenzji. Advanced eDiscovery te motywy są przypisywane do dokumentów, w których są wyświetlane. Ponadto każdy motyw jest oznaczany wyrazami w dokumentach, które są reprezentatywne dla motywu. Dokument może zawierać różnego rodzaju tematy, dlatego Advanced eDiscovery często przypisuje do dokumentów wiele motywów. Motyw, który jest najbardziej widoczny w dokumencie, jest wyznaczony jako motyw motywu dominującego.
