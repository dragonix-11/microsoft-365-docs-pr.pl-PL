---
title: Moduł kodowania predykcyjnego dla eDiscovery (Premium) (wersja zapoznawcza)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Nowy moduł kodowania predykcyjnego w usłudze eDiscovery (Premium) używa uczenia maszynowego do analizowania elementów w zestawie przeglądów w celu przewidywania elementów, które są istotne dla twojego przypadku lub badania.
ms.openlocfilehash: 7d45c995fafe5b802713e101ad36a362ab77fa37
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998997"
---
# <a name="learn-about-predictive-coding-in-ediscovery-premium-preview"></a>Dowiedz się więcej o kodowaniu predykcyjnym w usłudze eDiscovery (Premium) (wersja zapoznawcza)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Moduł kodowania predykcyjnego w usłudze eDiscovery (Premium) korzysta z inteligentnych możliwości uczenia maszynowego, które ułatwiają zmniejszenie ilości zawartości do przeglądania. Kodowanie predykcyjne pomaga ograniczyć i zlikwidować duże ilości zawartości przypadków do odpowiedniego zestawu elementów, które można określić jako priorytet do przeglądu. Można to osiągnąć, tworząc i szkoląc własne modele kodowania predykcyjnego, które ułatwiają określenie priorytetów przeglądu najbardziej odpowiednich elementów w zestawie przeglądów.

Moduł kodowania predykcyjnego ma na celu usprawnienie złożoności zarządzania modelem w ramach zestawu przeglądów i zapewnienie iteracyjnego podejścia do trenowania modelu, dzięki czemu można szybciej rozpocząć pracę z możliwościami uczenia maszynowego w dziedzinie zbierania elektronicznych materiałów dowodowych (Premium). Aby rozpocząć pracę, możesz utworzyć model, oznaczać etykietą tylko 50 elementów jako odpowiednich lub nieistotnych. System używa tego szkolenia do stosowania wyników przewidywania do każdego elementu w zestawie przeglądów. Umożliwia to filtrowanie elementów na podstawie wyniku przewidywania, co pozwala najpierw przejrzeć najbardziej odpowiednie (lub nieistotne) elementy. Jeśli chcesz trenować modele z wyższymi wskaźnikami akustyków i współczynników wycofywania, możesz kontynuować etykietowanie elementów w kolejnych rundach szkoleniowych, dopóki model się nie ustabilizuje.  

## <a name="the-predictive-coding-workflow"></a>Przepływ pracy kodowania predykcyjnego

Oto omówienie i opis każdego kroku przepływu pracy kodowania predykcyjnego. Aby uzyskać bardziej szczegółowy opis pojęć i terminologii procesu kodowania predykcyjnego, zobacz [Dokumentacja kodowania predykcyjnego](predictive-coding-reference.md).

![Przepływ pracy kodowania predykcyjnego.](..\media\PredictiveCodingWorkflow.png)

1. **Utwórz nowy model kodowania predykcyjnego w zestawie przeglądów**. Pierwszym krokiem jest utworzenie nowego modelu kodowania predykcyjnego w zestawie przeglądów. Aby utworzyć model, musisz mieć co najmniej 2000 elementów w zestawie przeglądów. Po utworzeniu modelu system określi liczbę elementów do użycia jako *zestaw sterowania*. Zestaw sterowania jest używany podczas procesu trenowania do oceny wyników przewidywania przypisywanych przez model do elementów z etykietami wykonywanymi podczas rund szkoleniowych. Rozmiar zestawu kontrolek jest oparty na liczbie elementów w zestawie przeglądów oraz poziomie ufności i marginesie wartości błędów ustawionych podczas tworzenia modelu. Elementy w zestawie kontrolek nigdy się nie zmieniają i nie są identyfikowalne dla użytkowników.

   Aby uzyskać więcej informacji, zobacz [Tworzenie modelu kodowania predykcyjnego](predictive-coding-create-model.md).

2. **Ukończ pierwszą rundę trenowania, oznaczając elementy jako odpowiednie lub nieistotne**. Następnym krokiem jest szkolenie modelu przez rozpoczęcie pierwszej rundy trenowania. Po rozpoczęciu rundy szkoleniowej model losowo wybiera dodatkowe elementy z zestawu przeglądów, który jest nazywany *zestawem szkoleniowym*. Te elementy (zarówno z zestawu sterowania, jak i zestawu szkoleniowego) są prezentowane, aby można było oznaczyć każdy z nich jako "odpowiedni" lub "nieistotny". Trafność jest oparta na zawartości w elemencie, a nie na żadnym z metadanych dokumentu. Po zakończeniu procesu etykietowania w rundzie trenowania model będzie "uczyć się" w oparciu o sposób etykietowania elementów w zestawie szkoleniowym. Na podstawie tego szkolenia model będzie przetwarzać elementy w zestawie przeglądów i stosować ocenę przewidywania do każdego z nich.

   Aby uzyskać więcej informacji, zobacz [Train a predictive coding model (Trenowanie modelu kodowania predykcyjnego](predictive-coding-train-model.md)).

3. **Zastosuj filtr wyniku przewidywania do elementów w zestawie przeglądów**. Po zakończeniu poprzedniego kroku trenowania następnym krokiem jest zastosowanie filtru wyniku przewidywania do elementów w przeglądzie, aby wyświetlić elementy, które został określony przez model, są "najbardziej istotne" (alternatywnie można również użyć filtru przewidywania, aby wyświetlić elementy, które są "nieistotne"). Po zastosowaniu filtru przewidywania należy określić zakres wyników przewidywania do filtrowania. Zakres wyników przewidywania mieści się w zakresie od **0** do **1**, przy czym **0** jest "nieistotne" i **1** jest istotne. Ogólnie rzecz biorąc, elementy z wynikami przewidywania z zakresu od **0** do **0,5** są uważane za "nieistotne", a elementy z wynikami przewidywania z zakresu **od 0,5** do **1** są uważane za istotne.

   Aby uzyskać więcej informacji, zobacz [Stosowanie filtru przewidywania do zestawu przeglądów](predictive-coding-apply-prediction-filter.md).

4. **Wykonaj więcej rund szkoleniowych, dopóki model nie ustabilizuje się**. Możesz wykonać dodatkowe rundy trenowania, jeśli chcesz utworzyć model z większą dokładnością przewidywania i zwiększonymi wskaźnikami wycofywania. *Wskaźnik wycofania* mierzy odsetek elementów przewidywanych przez model, które były istotne dla elementów, które są faktycznie istotne (te, które zostały oznaczone jako istotne podczas trenowania). Wskaźnik współczynnika wycofywania waha się od **0** do **1**. Wynik bliżej **1** wskazuje, że model zidentyfikuje bardziej odpowiednie elementy. W nowej rundzie trenowania należy oznaczyć dodatkowe elementy w nowym zestawie szkoleniowym. Po zakończeniu tej rundy trenowania model jest aktualizowany na podstawie nowej nauki z ostatniej rundy etykietowania elementów w zestawie szkoleniowym. Model ponownie przetworzy elementy w zestawie przeglądów i zastosuje nowe wyniki przewidywania. Możesz kontynuować wykonywanie rund szkoleniowych, dopóki model nie ustabilizuje się. Model jest uznawany za ustabilizowany, gdy współczynnik zmian po ostatniej rundzie trenowania jest mniejszy niż 5%. *Współczynnik zmian* jest definiowany jako procent elementów w zestawie przeglądów, w którym wynik przewidywania zmienia się między rundami szkoleniowymi. Na pulpicie nawigacyjnym kodowania predykcyjnego są wyświetlane informacje i statystyki ułatwiające ocenę stabilności modelu.

5. **Zastosuj "końcowy" filtr wyników przewidywania, aby przejrzeć ustawione elementy, aby określić priorytet przeglądu**. Po zakończeniu wszystkich rund szkoleniowych i ustabilizowaniu modelu ostatnim krokiem jest zastosowanie końcowego wyniku przewidywania do zestawu przeglądów w celu nadania priorytetu przeglądowi odpowiednich i nieistotnych elementów. Jest to to to samo zadanie, które wykonano w kroku 3, ale w tym momencie model jest stabilny i nie planujesz uruchamiania kolejnych rund szkoleniowych.
