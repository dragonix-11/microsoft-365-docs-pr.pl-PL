---
title: Planowanie wydajności i testowanie obciążenia usługi SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: W tym artykule opisano, jak wdrożyć usługę SharePoint Online bez przeprowadzania tradycyjnych testów ładowania, ponieważ nie jest to dozwolone.
ms.openlocfilehash: 8792c59ef96ef97cc36d0908100fd9ebb330857a
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014675"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planowanie wydajności i testowanie obciążenia usługi SharePoint Online
W tym artykule opisano, jak wdrożyć usługę SharePoint Online bez tradycyjnego testowania obciążenia, ponieważ testowanie ładowania nie jest dozwolone w SharePoint Online. SharePoint Online to usługa w chmurze, a firma Microsoft zarządza możliwościami ładowania, kondycją i ogólną równoważością obciążenia w usłudze.
  
Najlepszym sposobem zapewnienia sukcesu uruchomienia witryny jest obserwowanie podstawowych zasad, praktyk i zaleceń, które zostały wyróżnione w planie wprowadzenia witryny na [rynek](planportallaunchroll-out.md).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Omówienie sposobu, w jaki SharePoint online wykonuje planowanie pojemności 
Jedną z głównych zalet usługi SharePoint online w przypadku wdrożenia lokalnego jest elastyczność chmury i optymalizacji dla użytkowników w regionach rozproszonych. W naszym środowisku o dużej skali codziennie są obsługiwane miliony użytkowników, dlatego ważne jest efektywne wykorzystanie wydajności przez bilansowanie i rozwijanie farm.
  
Mimo że wzrost jest często nieprzewidywalny dla dowolnej dzierżawy w jednej farmie, zagregowana suma żądań jest przewidywalna w czasie. Identyfikując trendy wzrostu w usługach SharePoint Online, możemy zaplanować przyszłą rozszerzeń.
  
W celu efektywnego wykorzystania wydajności i radzenia sobie z nieoczekiwanym przyrostem w każdej farmie używamy automatyzacji, która śledzi i monitoruje różne elementy usługi. Używa się wielu metryk, a jedną z nich jest obciążenie procesora, które jest używane jako sygnał do skalowania serwerów front frontu. Ponadto zalecamy podejście etapowe[/](planportallaunchroll-out.md)etapowe, ponieważ środowiska SQL będą skalować się według obciążenia i wzrostu w czasie, a stosowanie się do faz i fal umożliwia poprawny rozkład tego obciążenia i wzrostu. 

Pojemność to nie tylko dodanie sprzętu w sposób ciągły, ale także zarządzanie i kontrolowanie tej pojemności w celu zapewnienia obsługi prawidłowych żądań ładowania. Zalecamy, aby klienci postępowali zgodnie z zalecanymi wskazówkami, aby upewnić się, że mają najlepsze środowisko pracy. Oznacza to również, że we wzorcach i mechanizmach kontroli ograniczania w miejscu nie dopuszczamy "obraźliwych" zachowań w usłudze. Chociaż nie wszystkie "złe" zachowania są celowe, musimy się upewnić, że ograniczymy jego efekt. Aby uzyskać więcej informacji na temat ograniczania i sposobu ich unikania, zapoznaj się z artykułem z poradami na temat [unikania](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) ograniczania.

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Dlaczego nie można załadować testów SharePoint Online
W środowiskach lokalnych testowanie obciążenia służy do weryfikowania założenia skalowania i ostatecznie do znalezienia punktu rozerwętego farmy. przez nasycenie go załaduj. 

W SharePoint Online musimy zrobić coś inaczej, ponieważ skala jest stosunkowo płynna i dostosowuje, ogranicza i steruje ładowaniem w oparciu o pewne heuristics. Jesteśmy tak dużym środowiskiem wielodostępnym, że musimy chronić wszystkie dzierżawy w tej samej farmie, więc automatycznie ograniczamy wszelkie testy ładowania. Jednak próby załadowania testów, oprócz ograniczania, będą poważnie i potencjalnie mylące, ponieważ w przetestowanych farmach prawdopodobnie zaszły zmiany skali w trakcie okna testowania lub w ciągu kilku godzin po testowaniu, ponieważ działania na rzecz równoważenia skali i równoważenia farmy są wykonywane na bieżąco.

Zamiast próbować załadować test SharePoint jako usługę, zamiast koncentrować się na zalecanych wskazówkach i postępować zgodnie z wytycznymi w zakresie tworzenia, uruchamiania i utrzymywania prawidłowego [działania portalu](/sharepoint/portal-health).