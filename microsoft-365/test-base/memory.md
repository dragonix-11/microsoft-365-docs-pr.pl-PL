---
title: Analiza regresji pamięci
description: Jak wywychać regresję pamięci
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: c4c6ec61ea96966237976ea71b82931e37efd278
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988039"
---
# <a name="memory-regression-analysis"></a>Analiza regresji pamięci

Baza testowa pomaga wyraźniej zauważyć znaczące wzrosty użycia pamięci podczas testowych maszyn wirtualnych działających w Twoich aplikacjach. Metryki wydajności, takie jak użycie pamięci, mogą być obciążeniem ogólnej kondycji aplikacji i uważamy, że takie dodanie znacznie pomoże w optymalnej wydajności Twoich aplikacji.

Czytaj dalej, aby uzyskać więcej szczegółów, lub obejrzyj ten klip wideo, aby szybko zapoznać się z najnowszymi ulepszeniami. 

Aby uzyskać więcej informacji na temat możliwości pomocy w analizie regresji modelu M365 na podstawie bazy testowej, zobacz Wyniki regresji oparte na niezawodności procesów.

<b>Patrząc bliżej regresji pamięci</b>

W bazie testowej dla pulpitu nawigacyjnego M365 jest przedstawiana pamięć używana przez aplikację w nowej, wydanej wstępnie aktualizacji programu Windows, i porównuje ją z pamięcią używaną w ostatniej wydanej Windows aktualizacji. 

Wraz z ulepszeniami w tym miesiącu w ulubionych procesach jest teraz polecana analiza regresji pamięci. Aplikacje mogą zawierać wiele procesów i można ręcznie wybrać ulubione procesy za pomocą karty Niezawodność. Nasza usługa będzie identyfikować regresję pamięci w tych ulubionych procesach podczas porównywania testów działa w różnych Windows wydaniach aktualizacji. W przypadku wykrycia regresji szczegóły dotyczące regresji są łatwo dostępne.

Teraz przyjrzyjmy się dokładnie tej funkcji i omówimy, jak można rozwiązywać problemy z regresją pamięci przy Windows wydajności.

Sygnał awarii spowodowany regresją pamięci jest wyświetlany na pulpicie nawigacyjnym Test bazy danych dla M365 na stronie Wyniki testowania w obszarze Wykorzystanie pamięci:

![Użycie pamięci powoduje.](Media/01_memory-utilization-results.png)


Błąd aplikacji ze względu na większe zużycie pamięci jest również wyświetlany na ```Fail``` stronie Podsumowanie testu:

![Przetestuj wyniki podsumowania.](Media/02_test-summary.png)

Sygnalizuje to z góry te błędy, dlatego naszym celem jest wyraźnie oflagowanie potencjalnych problemów, które mogą zakłócić działanie aplikacji i wpłynąć na jej działanie. 

Następnie możesz pobrać pliki dziennika i skorzystać z analizatora Windows wydajności lub preferowanego zestawu narzędzi w celu dalszego zbadania. Możesz także współpracować z zespołem Test Base for M365 nad rozwiązywaniem problemów i zapobiegać problemom wpływających na użytkowników końcowych.

Sygnały pamięci są przechwytywane na karcie Wykorzystanie pamięci w bazie testowej dla usługi M365 dla wszystkich testów. W poniższym przykładzie pokazano ostatnie uruchomienie testowe z włodaną aplikacją "Test pamięci testowej w czasie testowym" dla przedpremierowej aktualizacji zabezpieczeń z sierpnia 2020 r. (Ten program został napisany przez nasz zespół, aby ilustrować regresję pamięci).

![Wyniki regresji pamięci.](Media/03_memory-regression%20comparison.png)

W tym przykładzie ulubiony proces "USLTestMemoryStress.exe" zużywał średnio około 100 MB w aktualizacji wstępnej z sierpnia w porównaniu z opublikowaną aktualizacją z lipca, dlatego baza testowa dla M365 zidentyfikowała regresję. 

Pozostałe procesy — przedstawione tutaj jako "USLTestMemoryStress_Aux1.exe" i "USLTestMemoryStress_Aux2.exe" — również należą do tej samej aplikacji, ale w przybliżeniu zużywały tę samą ilość pamięci dla dwóch wersji, więc "minęły" i były uznawane za dobrej kondycji.

Regresja głównego procesu została określona jako "istotna statystycznie", więc usługa komunikowała i wyróżniała tę różnicę dla użytkownika. Jeśli porównanie nie było statystyczne istotne, nie zostanie wyróżnione. Korzystanie z pamięci może być głośne, dlatego używamy modeli statystycznych, aby rozróżnić istotne różnice między kompilacjami i wersjami. 

Porównanie może rzadko być oflagowane, gdy nie ma prawdziwej różnicy (wyników fałszywie dodatnich), ale jest to konieczne kompromis w celu zwiększenia prawdopodobieństwa poprawnego identyfikowania regresji (lub prawdziwych wyników dodatnich).

Następnym krokiem jest zrozumienie, co spowodowało regresję pamięci. Możesz pobrać pliki zip dla obu wykonywania z opcji Pobierz pliki dziennika, jak pokazano poniżej. 

Te pliki zip zawierają wyniki uruchomienia testowego, w tym wyniki skryptów oraz dane dotyczące pamięci i wydajności procesora zawarte w pliku ETL.

![Pliki testowe regresji pamięci.](Media/04_memory-regression-test-files.png)

Możesz pobrać i rozpakować dzienniki dla dwóch uruchomieniu testowych, a następnie zlokalizować plik ETL w każdym folderze i zmienić ich nazwę na target.etl (dla uruchamiania testowego w ramach aktualizacji wstępnej) i baseline.etl (w przypadku uruchomienia testowego w ostatniej wydanej aktualizacji), aby uprościć eksplorowanie i nawigowanie.
 
## <a name="next-steps"></a>Następne kroki

Przejść do następnego artykułu, aby rozpocząć opis inteligentnej analizy regresji procesora.
> [!div class="nextstepaction"]
> [Następny krok](cpu.md)

<!---
Add button for next page
-->
