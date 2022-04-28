---
title: Planowanie wydajności i testowanie obciążenia usługi SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: W tym artykule opisano sposób wdrażania w usłudze SharePoint Online bez przeprowadzania tradycyjnych testów obciążeniowych, ponieważ jest to niedozwolone.
ms.openlocfilehash: 1d1714bbcdefdbc41ff3ac5d038c6b59a7043a26
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101100"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planowanie wydajności i testowanie obciążenia usługi SharePoint Online
W tym artykule opisano sposób wdrażania w usłudze SharePoint Online bez tradycyjnych testów obciążeniowych, ponieważ testowanie obciążenia nie jest dozwolone w usłudze SharePoint Online. SharePoint Online to usługa w chmurze, a możliwości ładowania, kondycja i ogólny saldo obciążenia w usłudze są zarządzane przez firmę Microsoft.
  
Najlepszym podejściem do zapewnienia powodzenia uruchamiania witryny jest przestrzeganie podstawowych zasad, praktyk i zaleceń, które zostały wyróżnione w [planie wdrożenia portalu](planportallaunchroll-out.md).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Omówienie sposobu, w jaki usługa SharePoint Online wykonuje planowanie pojemności 
Jedną z głównych zalet usługi SharePoint Online w ramach wdrożenia lokalnego jest elastyczność chmury i optymalizacja dla użytkowników w regionach rozproszonych. Nasze środowisko na dużą skalę jest codziennie konfigurowane do obsługi milionów użytkowników, dlatego ważne jest, aby efektywnie obsługiwać pojemność przez równoważenie i rozszerzanie farm.
  
Chociaż wzrost jest często nieprzewidywalny dla jednej dzierżawy w jednej farmie, zagregowana suma żądań jest przewidywalna w czasie. Identyfikując trendy wzrostu w usłudze SharePoint Online, możemy zaplanować przyszłą ekspansję.
  
Aby efektywnie korzystać z pojemności i radzić sobie z nieoczekiwanym wzrostem, w każdej farmie mamy automatyzację, która śledzi i monitoruje różne elementy usługi. Wykorzystuje się wiele metryk, a jedną z głównych jest obciążenie procesora CPU, które jest używane jako sygnał do skalowania serwerów frontonu w górę. Ponadto zalecamy [podejście etapowe/falowe](planportallaunchroll-out.md), ponieważ środowiska SQL będą skalowane w zależności od obciążenia i wzrostu w czasie, a obserwowanie faz i fal pozwala na prawidłowy rozkład tego obciążenia i wzrostu. 

Pojemność to coś więcej niż tylko ciągłe dodawanie większej ilości sprzętu, ale odnosi się również do zarządzania tą pojemnością i kontrolowania jej, aby zapewnić obsługę prawidłowych żądań obciążenia. Zalecamy, aby klienci postępowali zgodnie z zalecanymi wskazówkami, aby mieć pewność, że mają najlepsze środowisko pracy. Oznacza to również, że mamy wzorce ograniczania przepustowości i mechanizmy kontroli w celu zapewnienia, że nie zezwalamy na "obraźliwe" zachowanie w usłudze. Chociaż nie wszystkie "złe" zachowanie jest zamierzone, musimy upewnić się, że ograniczamy wpływ tego zachowania. Aby uzyskać więcej informacji na temat ograniczania przepustowości i sposobu jej uniknięcia, zapoznaj się z artykułem [dotyczącym unikania ograniczania przepustowości](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) .

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Dlaczego nie można załadować testu SharePoint Online
W środowiskach lokalnych testowanie obciążenia służy do weryfikowania założenia skalowania i ostatecznie znalezienia punktu krytycznego farmy; przez nasycenie go obciążeniem. 

Dzięki usłudze SharePoint Online musimy wykonywać różne czynności, ponieważ skala jest względnie płynna i dostosowuje obciążenie, ogranicza przepustowość i kontroluje obciążenie w oparciu o pewne algorytmy heurystyki. Będąc takim środowiskiem wielodostępnym na dużą skalę, musimy chronić wszystkie dzierżawy w tej samej farmie, więc automatycznie ograniczymy wszelkie testy obciążeniowe. Jeśli jednak spróbujesz przeprowadzić test obciążeniowy, oprócz ograniczenia przepustowości, otrzymasz rozczarowujące i potencjalnie wprowadzające w błąd wyniki, ponieważ testowana farma prawdopodobnie miała zmiany skali w oknie testowania lub w ciągu kilku godzin po przetestowaniu, ponieważ akcje równoważenia skali i farmy są wykonywane w toku.

Zamiast próbować ładować test SharePoint jako usługa, skup się raczej na przestrzeganiu zalecanych rozwiązań i postępuj zgodnie ze wskazówkami dotyczącymi [tworzenia, uruchamiania i utrzymywania dobrej kondycji portalu](/sharepoint/portal-health).