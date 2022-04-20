---
title: Tworzenie modelu kodowania predykcyjnego w usłudze eDiscovery (Premium)
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
description: Dowiedz się, jak utworzyć model kodowania predykcyjnego w usłudze eDiscovery (Premium). Jest to pierwszy krok w zakresie korzystania z funkcji uczenia maszynowego w usłudze eDiscovery (Premium), aby ułatwić zidentyfikowanie odpowiedniej i nieistotnej zawartości w zestawie przeglądów.
ms.openlocfilehash: 86fc72ae73faf25184c5b137a0e433af8125eb54
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942276"
---
# <a name="create-a-predictive-coding-model-preview"></a>Tworzenie modelu kodowania predykcyjnego (wersja zapoznawcza)

Pierwszym krokiem w zakresie korzystania z funkcji uczenia maszynowego w kodowaniu predykcyjnym w dziedzinie zbierania elektronicznych materiałów dowodowych (Premium) jest utworzenie modelu kodowania predykcyjnego. Po utworzeniu modelu można go wytrenować, identyfikując odpowiednią i nieistotną zawartość w zestawie przeglądów.

Aby przejrzeć przepływ pracy kodowania predykcyjnego, zobacz [Learn about predictive coding in eDiscovery (Premium) (Informacje o kodowaniu predykcyjnym w usłudze eDiscovery (Premium)](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-create-a-model"></a>Przed utworzeniem modelu

- Aby utworzyć model kodowania predykcyjnego, musi istnieć co najmniej 2000 elementów w zestawie przeglądów.

- Przed utworzeniem modelu należy zatwierdzić wszystkie kolekcje w zestawie przeglądów. Elementy dodane do zestawu przeglądów po utworzeniu modelu nie zostaną przetworzone i nie zostaną przypisane do wyniku przewidywania wygenerowanego przez model.

- Żaden element w zestawie przeglądów, który nie zawiera tekstu, nie zostanie przetworzony przez model ani nie zostanie przypisany do wyniku przewidywania. Elementy z tekstem zostaną uwzględnione w zestawie kontrolek lub zestawie szkoleniowym.

## <a name="create-a-model"></a>Tworzenie modelu

1. W portalu zgodności usługi Microsoft Purview otwórz przypadek zbierania elektronicznych materiałów dowodowych (Premium), a następnie wybierz kartę **Zestawy przeglądów**.

2. Otwórz zestaw przeglądów, a następnie kliknij pozycję **AnalizaZarządzanie** >  **kodowaniem predykcyjnym (wersja zapoznawcza).**

   ![Kliknij menu rozwijane Analizuj w zestawie przeglądów, aby przejść do strony Kodowanie predykcyjne.](..\media\ManagePredictiveCoding.png)

3. Na stronie **Modele kodowania predykcyjnego (wersja zapoznawcza)** kliknij pozycję **Nowy model**.

4. Na stronie wysuwanej wpisz nazwę modelu i opcjonalny opis.

5. Opcjonalnie można skonfigurować ustawienia zaawansowane (klikając **opcje zaawansowane** na stronie wysuwanej) związane z poziomem ufności i marginesem błędu. Te ustawienia mają wpływ na liczbę elementów uwzględnionych w zestawie kontrolek. *Zestaw sterowania* jest używany podczas procesu trenowania do oceny wyników przewidywania przypisywanych przez model do elementów z etykietami wykonywanymi podczas rund szkoleniowych. Jeśli organizacja ma wytyczne dotyczące poziomu ufności i marginesu błędu dla przeglądu dokumentu, określ je w odpowiednich polach. W przeciwnym razie użyj ustawień domyślnych.

6. Kliknij przycisk **Zapisz** , aby utworzyć model.

   Przygotowanie modelu przez system potrwa kilka minut. Gdy wszystko będzie gotowe, możesz wykonać pierwszą rundę trenowania.

## <a name="what-happens-after-you-create-a-model"></a>Co się stanie po utworzeniu modelu

Po utworzeniu modelu podczas tworzenia i przygotowywania modelu w tle występują następujące elementy:

- System oblicza liczbę elementów dla zestawu sterowania. Ten rozmiar jest oparty na liczbie elementów w zestawie przeglądów oraz ustawieniach poziomu ufności i marginesu błędu. Elementy zestawu kontrolek są wybierane losowo i wyznaczane jako elementy zestawu sterowania. System zawiera 10 elementów z zestawu sterowania w pierwszej rundzie trenowania.

- System losowo wybiera 40 elementów z zestawu przeglądów, które mają zostać uwzględnione w zestawie szkoleniowym dla pierwszej rundy trenowania. W związku z tym pierwsza runda trenowania obejmuje 50 elementów do etykietowania: 40 elementów z zestawu treningowego i 10 elementów z zestawu sterowania.

## <a name="next-steps"></a>Następne kroki

Po utworzeniu modelu dla zestawu przeglądów następnym krokiem jest przeprowadzenie rund szkoleniowych w celu "nauczenia" modelu identyfikowania zawartości, która jest odpowiednia dla badania. Aby uzyskać więcej informacji, zobacz [Train a predictive coding model (Trenowanie modelu kodowania predykcyjnego](predictive-coding-train-model.md)).
