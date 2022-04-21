---
title: Śledzenie analizy istotności w zakresie zbierania elektronicznych materiałów dowodowych (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 3ab1e2c3-28cf-4bf5-b0a8-c0222f32bdf5
ROBOTS: NOINDEX, NOFOLLOW
description: Dowiedz się, jak wyświetlać i interpretować stan trenowania istotności i wyniki dotyczące problemów ze sprawami zbierania elektronicznych materiałów dowodowych (Premium).
ms.openlocfilehash: 72e12fe54b30c3d766f7a198e5e3417ff9d48a22
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000955"
---
# <a name="track-relevance-analysis-in-ediscovery-premium"></a>Śledzenie analizy istotności w zakresie zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
W usłudze Microsoft Purview eDiscovery (Premium) na karcie Śledzenie istotności jest wyświetlana obliczona ważność trenowania istotności wykonywanego na karcie Tag i wskazuje następny krok do wykonania w procesie trenowania iteracyjnego w obszarze Istotność. 
  
## <a name="tracking-relevance-training-status"></a>Śledzenie stanu trenowania istotności

1. Wyświetl następujące szczegóły w obszarze Śledzenie istotności problemów, jak pokazano w poniższym przykładzie okna dialogowego **Nazwa problemu** poniżej.

   - **Ocena**: Ten wskaźnik postępu pokazuje, w jakim stopniu szkolenie w zakresie istotności przeprowadzone do tego momentu osiągnęło cel oceny pod względem marginesu błędu. Zostanie również wyświetlone bogactwo wyników trenowania istotności.

   - **Trenowanie**: Ten wskaźnik postępu z kodem kolorowym i porada narzędzia wskazuje stabilność wyników trenowania istotności oraz skalę liczbową pokazującą liczbę próbek trenowania istotności oznaczonych dla każdego problemu. Ekspert monitoruje postęp iteracyjnego procesu trenowania istotności. 
  
   - **Obliczenia wsadowe**: ten wskaźnik postępu zawiera informacje o ukończeniu obliczeń usługi Batch.
  
   - **Następny krok**: wyświetla zalecenie dotyczące następnego kroku do wykonania. 
  
    W tym przykładzie zostanie wyświetlona pomyślnie ukończona ocena problemu, wskazana przez ukończony wskaźnik postępu koloru i znacznik wyboru. Tagowanie jest w toku, ale sprawa jest nadal uważana za niestabilną (stan stabilności jest również wyświetlany w poradzie narzędzia). Następnym krokiem jest zalecenie "Szkolenie". 
  
    ![Śledzenie istotności — krok 1.](../media/a00fe607-680a-48eb-9d61-4565319f7ab6.png)
  
    Rozszerzony widok zawiera dodatkowe informacje i opcje. Wyświetlany bieżący margines błędu to margines błędu wycofania w bieżącym stanie oceny, biorąc pod uwagę istniejące (już oznaczone) pliki oceny.
  
    > [!NOTE]
    >  Etap oceny można pominąć, usuwając pole wyboru **Ocena** dla każdego problemu, a następnie dla "wszystkich problemów". Jednak w związku z tym nie będzie żadnych statystyk dla tego problemu. > Zaznaczenie pola wyboru **Ocena** można wykonać tylko przed przeprowadzeniem oceny. Jeśli istnieje wiele problemów w danym przypadku, ocena jest pomijana tylko wtedy, gdy pole wyboru jest wyczyszczone dla każdego problemu 
  
    Jeśli ocena nie zostanie ukończona przy użyciu pierwszego przykładowego zestawu plików, ocena może być kolejnym krokiem tagowania większej liczby plików.
  
    W **obszarze Śledzenie istotności** \> wskaźnik postępu trenowania i porada narzędzia wskazują szacowaną liczbę dodatkowych próbek potrzebnych do osiągnięcia stabilności. To oszacowanie zawiera wytyczne dotyczące wymaganych dodatkowych szkoleń.
  
    ![Trenowanie ścieżki istotności.](../media/98dbc3f5-5238-4d73-9f88-1aa4d77ea729.png)
  
2. Po zakończeniu tagowania i kontynuowaniu trenowania kliknij pozycję **Szkolenie**. Inny przykładowy zestaw plików jest generowany z załadowanego zestawu plików na potrzeby dodatkowego trenowania. Następnie wrócisz do karty Tag, aby oznaczyć i wytrenować więcej plików.

### <a name="reaching-stable-training-levels"></a>Osiąganie stabilnych poziomów trenowania

Gdy pliki oceny osiągną stabilny poziom trenowania, funkcja zbierania elektronicznych materiałów dowodowych (Premium) jest gotowa do obliczeń usługi Batch.
  
> [!NOTE]
> Zwykle po trzech stabilnych przykładach trenowania następnym krokiem jest "Obliczenie usługi Batch". Mogą wystąpić wyjątki, na przykład gdy wprowadzono zmiany tagowania plików z wcześniejszych przykładów lub gdy pliki inicjujące zostały dodane. 
  
### <a name="performing-batch-calculation"></a>Wykonywanie obliczeń usługi Batch

Obliczanie usługi Batch jest wykonywane jako następny krok po pomyślnym ukończeniu trenowania (gdy stabilny stan trenowania jest wyświetlany na pasku postępu, znacznik wyboru i stabilny stan w poradzie narzędzia). Obliczenia usługi Batch stosują wiedzę uzyskaną podczas trenowania istotności do całej populacji plików, aby ocenić istotność plików i przypisać wyniki istotności.
  
Jeśli występuje więcej niż jeden problem, obliczenie usługi Batch jest wykonywane dla każdego problemu. Podczas obliczania usługi Batch postęp jest monitorowany podczas przetwarzania wszystkich plików. 
  
W tym miejscu zalecanym następnym krokiem jest "Brak", co oznacza, że w tym momencie nie jest wymagane żadne dodatkowe trenowanie iteracyjnego istotności. Następna faza to karta **Decyzja o istotności\>**. 
  
Jeśli chcesz zaimportować nowe pliki po obliczeniu usługi Batch, administrator może dodać zaimportowane pliki do nowego obciążenia.
  
> [!NOTE]
> Jeśli **klikniesz przycisk Anuluj** podczas obliczania usługi Batch, proces zapisze to, co zostało już wykonane. Jeśli ponownie uruchomisz obliczenia usługi Batch, proces będzie kontynuowany od ostatniego wykonanego punktu. 
  
### <a name="assessing-tagging-consistency"></a>Ocena spójności tagowania

Jeśli w tagowaniu plików występują niespójności, może to mieć wpływ na analizę. Proces spójności tagowania zbierania elektronicznych materiałów dowodowych (Premium) może być używany, gdy wyniki nie są optymalne lub spójność jest wątpliwa. Zwracana jest lista możliwych niespójnie oznaczonych plików. W razie potrzeby można je przejrzeć i ponownie oznaczyć.
  
> [!NOTE]
> Po co najmniej siedmiu rundach szkoleniowych po dokonaniu oceny spójność tagowania można wyświetlić w sekcji Postęp **trenowania** **śledzenia** \> **istotności**\>— **problem** \> **ze szczegółowymi wynikami**\>. Ta recenzja jest wykonywana dla jednego problemu naraz.
  
1. W **obszarze Śledzenie istotności \>** rozwiń wiersz problemu.
  
2. Po prawej stronie pozycji **Następny krok** kliknij przycisk **Modyfikuj**.
  
3. Wybierz opcję **Tagowanie niespójności** jako opcję **Następny krok** , po siedmiu przykładach szkoleniowych i kliknij przycisk **OK**.
  
4. Wybierz pozycję **Niespójności tagów**. Zostanie otwarta karta **Tag** zawierająca listę niespójności do ponownego zatagowania w razie potrzeby.
  
5. Kliknij pozycję **Oblicz** , aby przesłać zmiany. Następnym krokiem po otagowaniu niespójności jest "Trenowanie". 
  
## <a name="viewing-and-using-relevance-results"></a>Wyświetlanie i używanie wyników istotności

Na karcie **Śledzenie istotności \>** rozwiń wiersz problemu, a następnie obok pozycji **Szczegółowe wyniki** kliknij pozycję **Wyświetl**. Wyświetlane są okienka Szczegółowe wyniki, jak pokazano i opisano poniżej.
  
![Szczegółowe wyniki trenowania istotności.](../media/495c04a9-ed1e-4355-8cab-c14270ca2bbb.png)
  
### <a name="tagging-summary"></a>Podsumowanie tagowania

 W poniższym przykładzie **podsumowanie tagowania zawiera sumy** dla każdego z procesów tagowania oceny, trenowania i przechwytywania plików.
  
![Podsumowanie tagowania śledzenie istotności.](../media/0ec906fc-bc84-4245-a964-fb3ca37891db.png)
  
### <a name="keywords"></a>Słowa kluczowe

Słowo kluczowe jest unikatowym ciągiem, słowem, frazą lub sekwencją wyrazów w pliku zidentyfikowanym przez funkcję eDiscovery (Premium) jako znaczący wskaźnik istotności pliku. Kolumny "Dołącz" zawierają słowo kluczowe i wagi w plikach oznaczonych jako Odpowiednie, a kolumny "Wyklucz" zawierają słowa kluczowe i wagi w plikach oznaczonych jako Nieistotne.
  
Funkcja zbierania elektronicznych materiałów dowodowych (Premium) przypisuje ujemne lub dodatnie wartości wagi słowa kluczowego. Im wyższa waga, tym większe prawdopodobieństwo, że plik, w którym pojawia się słowo kluczowe, zostanie przypisany wyższy wynik istotności podczas obliczania usługi Batch.
  
Lista materiałów eDiscovery (Premium) słów kluczowych może służyć do uzupełniania listy utworzonej przez eksperta lub jako pośrednia kontrola poczytalności w dowolnym momencie procesu przeglądu pliku.
  
### <a name="training-progress"></a>Postęp szkolenia

Okienko **Postęp trenowania** zawiera wykres postępu trenowania i wskaźnik jakości, jak pokazano w poniższym przykładzie.
  
![Istotność Śledź postęp trenowania.](../media/8a5089f5-a162-4246-ae09-bc1921859860.png)
  
**Wskaźnik jakości trenowania**: wyświetla ocenę spójności tagowania w następujący sposób:
  
- **Dobra**: pliki są stale oznaczane. (Wyświetlane zielone światło)
  
- **Średni**: Niektóre pliki mogą być tagowane niespójnie. (Żółte światło wyświetlane)

- **Ostrzeżenie**: Wiele plików może być oznakowanych niespójnie. (Wyświetlane czerwone światło)

**Wykres postępu trenowania**: pokazuje stopień stabilności trenowania istotności po wielu cyklach trenowania istotności w porównaniu z wartością F-measure. Gdy przechodzimy od lewej do prawej strony wykresu, interwał ufności zmniejsza się i jest używany wraz z miarą F przez funkcję eDiscovery (Premium) Istotność, aby określić stabilność, gdy wyniki trenowania istotności zostaną zoptymalizowane.
  
> [!NOTE]
> Istotność używa F2, metryki miary F, w której funkcja Recall otrzymuje dwa razy większą wagę niż precyzja. W przypadku przypadków o wysokim bogactwie (ponad 25%), w przypadku istotności jest używana wartość F1 (stosunek 1:1). Współczynnik miarY F można skonfigurować w ustawieniach **zaawansowanych** **konfiguracji** \> istotności.
  
### <a name="batch-calculation-results"></a>Wyniki obliczeń usługi Batch

Okienko **wyników obliczeń usługi Batch** zawiera liczbę plików, które zostały ocenione pod kątem istotności, w następujący sposób: 
  
- **Sukces**
  
- **Puste**: nie zawiera tekstu, na przykład tylko spacje/karty
  
- **Niepowodzenie**: z powodu nadmiernego rozmiaru lub nie można go odczytać
  
- **Ignorowane**: Ze względu na nadmierny rozmiar
  
- **Mglisty**: zawiera tekst bez znaczenia lub nie ma żadnych funkcji istotnych dla problemu
  
> [!NOTE]
> Wartość Pusta, Nie powiodła się, Zignorowana lub Mglista otrzyma wynik istotności -1.
  
### <a name="training-statistics"></a>Statystyki trenowania

W okienku **Statystyki trenowania** są wyświetlane statystyki i wykresy na podstawie wyników trenowania istotności zbierania elektronicznych materiałów dowodowych (Premium). 
  
![Istotność Śledź statystyki trenowania.](../media/9a07740e-20d3-49fb-b9b9-84265e0a1836.png)
  
W tym widoku przedstawiono następujące elementy:
  
- **Współczynnik odwołania do przeglądu**: porównanie wyników zgodnie z wynikami istotności w hipotetycznie liniowym przeglądzie. Przywoływanie jest szacowane, biorąc pod uwagę zestaw rozmiarów zestawu przeglądów.
  
- **Parametry**: Skumulowane statystyki obliczeniowe odnoszące się do zestawu przeglądów w odniesieniu do populacji plików dla całego przypadku.
  
- **Przegląd**: Procent plików do przejrzenia na podstawie tego odcięcia.
  
- **Przypomnij sobie**: procent odpowiednich plików w zestawie przeglądów. 
  
- **Rozkład według wskaźnika istotności**: Pliki na ciemnoszarym ekranie po lewej stronie znajdują się poniżej wyniku odcięcia. Porada narzędzia wyświetla wynik istotności i powiązany procent plików w pliku przeglądu ustawionym w odniesieniu do łącznej liczby plików.
