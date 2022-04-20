---
title: Omówienie oceny w istotności w zakresie zbierania elektronicznych materiałów dowodowych (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 1d33d4fb-91ed-41c0-b72e-5a26eca3a2a7
description: Zapoznaj się z omówieniem etapu oceny i jego roli w określaniu bogactwa problemów podczas trenowania istotności w usłudze Microsoft Purview eDiscovery (Premium).
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 29376b8c71947b1f09bd86de90facef6f73e0fdd
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943958"
---
# <a name="assessment-in-the-relevance-module-in-ediscovery-premium"></a>Ocena w module Istotność w usłudze eDiscovery (Premium)
  
Usługa Microsoft Purview eDiscovery (Premium) umożliwia wczesną ocenę, na przykład w przypadku zdefiniowanych problemów i danych zaimportowanych w danym przypadku. eDiscovery (Premium) umożliwia ekspertom podejmowanie decyzji dotyczących przyjętego podejścia i stosowanie tych decyzji do projektu przeglądu dokumentu.
  
## <a name="understanding-assessment"></a>Omówienie oceny

W obszarze Ocena ekspert przegląda losowy zestaw co najmniej 500 plików, które służą do określania bogactwa problemów i tworzenia statystyk, które odzwierciedlają wyniki trenowania. Ocena jest pomyślna, gdy zostanie stwierdzona wystarczająca liczba odpowiednich plików, aby osiągnąć poziom statystyczny, który pomoże w zbierania elektronicznych materiałów dowodowych (Premium) Istotność w celu zapewnienia dokładnych statystyk i skutecznego określenia punktu stabilizacji w procesie trenowania. 
  
Im większa liczba odpowiednich plików w zestawie oceny, tym dokładniejsze są statystyki i skuteczność algorytmu stabilności. Liczba odpowiednich plików w plikach oceny zależy od bogactwa problemu. Richness to szacowany procent odpowiednich plików w zestawie istotnych dla problemu. Problemy z wyższym bogactwem szybciej osiągną większą liczbę odpowiednich plików niż problemy z niższym bogactwem. Problemy z bardzo niskim bogactwem (na przykład 2% lub mniej) będą wymagały bardzo dużej oceny ustawionej w celu osiągnięcia znacznej liczby odpowiednich plików.
  
Statystyki przedstawione na kartach Śledź i Zdecyduj podczas trenowania i po obliczeniu usługi Batch obejmują szacowanie odwołania dla różnych zestawów przeglądów. W statystykach oszacowania oparte na przykładowym zestawie (w tym przypadku pliki oceny) obejmują margines błędu i poziom ufności tego marginesu błędu. Na przykład szacowane wycofanie 80% może mieć margines błędu plus lub minus 5%, przy poziomie ufności wynoszącym 95%. Oznacza to, że szacowane wycofanie wynosi w rzeczywistości 75%-85%, a to oszacowanie ma 95% ufności. Większy zestaw oceny, margines błędu staje się mniejszy, a statystyki są dokładniejsze. 
  
Po przeglądzie przez eksperta wstępnego zestawu oceny 500 plików, funkcja Istotność może określić bieżący margines błędu wartości wycofania. Istotność będzie również zalecać domyślny margines błędu, aby osiągnąć, aby zoptymalizować zestaw oceny. Oto kilka przykładów:
  
- Jeśli zestaw oceny już przyniósł margines błędu wynoszący plus lub minus 10%, firma Relevance zaleci przejście do szkolenia (nie jest wymagany dodatkowy przegląd oceny). 

- Jeśli zestaw oceny przyniósł margines błędu wynoszący plus lub minus 13%, funkcja Istotność może zalecić przegląd innego zestawu plików oceny w celu osiągnięcia mniejszego marginesu. 

- Jeśli poziom bogactwa jest bardzo niski, istotność może zalecić zatrzymanie oceny, mimo że margines błędu jest duży (co sprawia, że statystyki są niepraktyczne), ponieważ zestaw oceny potrzebny do osiągnięcia użytecznego marginesu błędu jest zbyt duży.

Każdy problem ma własne bogactwo, bieżący margines błędu i w rezultacie szacowaną liczbę dodatkowych plików oceny. Następny zestaw oceny jest tworzony zgodnie z maksymalną liczbą plików (maksymalnie 1000 w jednym zestawie).
  
Możesz zaakceptować zalecenia dotyczące istotności lub dostosować bieżący margines błędu zgodnie z potrzebami. Domyślny bieżący margines błędu jest określany dla odwołania na poziomie równym lub wyższym niż 75%.
  
> [!NOTE]
> Etap oceny można pominąć na karcie **Śledzenie istotności \>** w rozwiniętym widoku problemu, usuwając pole wyboru **Ocena** dla każdego problemu, a następnie dla "wszystkich problemów". W związku z tym nie będzie żadnych statystyk dla tego problemu. Wyczyszczenie pola wyboru **Ocena** można wykonać tylko przed przeprowadzeniem oceny. Jeśli istnieje wiele problemów w danym przypadku, ocena jest pomijana tylko wtedy, gdy pole wyboru jest wyczyszczone dla każdego problemu.
