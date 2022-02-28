---
title: Opis oceny według istotności w programie Advanced eDiscovery
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
description: Przegląd etapu oceny i jego roli w określaniu stopnia istotności problemów podczas szkolenia na temat istotności w programie Microsoft 365 Advanced eDiscovery.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 80ec4f0c362ff403f45123bf837e82c5d2f6ed7e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985111"
---
# <a name="assessment-in-the-relevance-module-in-advanced-ediscovery"></a>Ocena w module Istotność w programie Advanced eDiscovery
  
Advanced eDiscovery umożliwia wcześniejszą ocenę, na przykład zdefiniowanych problemów i danych zaimportowanych w przypadku sprawy. Advanced eDiscovery umożliwia ekspertowi podejmowanie decyzji dotyczących przyjętego podejścia oraz stosowanie tych decyzji do projektu przeglądu dokumentu.
  
## <a name="understanding-assessment"></a>Opis oceny

W ramach oceny ekspert przegląda losowy zestaw co najmniej 500 plików, które są używane do określenia bogatych problemów i tworzenia statystyk, które odzwierciedlają wyniki szkoleń. Ocena jest skuteczna, gdy zostanie znaleziona wystarczająca ilość odpowiednich plików, aby osiągnąć poziom statystyczny, który pomoże ustalić Advanced eDiscovery istotności w celu zapewnienia dokładnych statystyk i skutecznego określenia punktu stabilizacji w procesie szkoleniowym. 
  
Im większa liczba odpowiednich plików w zestawie oceniań, tym dokładniejszy jest statystyki i skuteczność algorytmu stabilności. Liczba odpowiednich plików w plikach oceniania zależy od skali problemu. Richness to szacowany procent odpowiednich plików w zestawie odpowiednim dla problemu. Problemy o wyższym poziomie bogatości dotrą do większej liczby plików szybciej niż problemy o niższym poziomie rozbudowy. Problemy o bardzo niskim poziomie (na przykład 2% lub mniej) będą wymagały bardzo dużego zestawu ocen do osiągnięcia znacznej liczby odpowiednich plików.
  
Statystyki, które są prezentowane na kartach Śledź i zdecyduj podczas szkolenia i po obliczeniach wsadowych, obejmują szacunki odwołania dla różnych zestawów recenzji. W statystyce oszacowania oparte na przykładowym zestawie (w tym przypadku pliki testów) obejmują margines błędu i poziom ufności marginesu błędu. Na przykład przy szacowanym odwołaniu 80% może być margines błędu plus lub minus 5% przy poziomie ufności 95%. Oznacza to, że szacowane odwołanie w rzeczywistości wynosi 75%–85%, a to oszacowanie jest ufne na poziomie 95%. Im większy zestaw ocen, margines błędu staje się mniejszy, a statystyki są bardziej dokładne. 
  
Po przeglądzie przez eksperta wstępnego zestawu 500 plików oceny wstępnej istotność może ustalić bieżącą marżę błędu przy odwołaniu wartości. Istotność będzie również zalecać osiągnięcie domyślnego marginesu błędu w celu zoptymalizowania zestawu ocen. Oto kilka przykładów:
  
- Jeśli w zestawie ocen margines błędu wynosi plus lub minus 10%, nie zaleca się przechodzenia do szkolenia (nie jest wymagany żaden dodatkowy przegląd oceny). 

- Jeśli w zestawie oceniań margines błędu wynosi plus lub minus 13%, istotność może zalecić osiągnięcie mniejszego marginesu podczas przeglądania innego zestawu plików ocen. 

- Jeśli ich poziom jest bardzo niski, istotność może zatrzymać ocenę, nawet jeśli margines błędu jest duży (co czyni statystykę niepraktyczną), ponieważ zestaw ocen niezbędny do osiągnięcia użytecznej marginesu błędu jest za duży.

Każdy problem ma swój własny bogaty i aktualny margines błędu, w wyniku czego szacowana liczba dodatkowych plików oceny. Następny zestaw ocen jest tworzony zgodnie z maksymalną liczbą plików (maksymalnie 1000 w jednym zestawie).
  
Możesz zaakceptować zalecenia dotyczące istotności lub dostosować bieżącą marżę błędu do swoich potrzeb. Domyślna bieżąca marginesu błędu jest określana do odwołania przy wartości równej lub powyżej 75%.
  
> [!NOTE]
> Etap oceny można pominąć na **\>** karcie Śledzenie istotności w rozwiniętym widoku problemu przez wyczyszczenie pola wyboru Ocena dla każdego problemu, a  następnie w przypadku "wszystkich problemów". W efekcie nie będzie żadnych statystyk dotyczących tego problemu. Wyczyszczenie **pola wyboru** Ocena jest możliwe tylko przed rozpoczęciem oceniania. Jeśli w przypadku sprawy występuje wiele problemów, ocena jest pomijana tylko w przypadku wyczyszczenia pola wyboru dla każdego problemu.
