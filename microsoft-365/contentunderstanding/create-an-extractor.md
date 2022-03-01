---
title: Tworzenie wyodrębnianego programu Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się, jak utworzyć wyodrębnianie w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: 1d0aebf610897d07d051ba9e5f3e218dd582bbad
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015420"
---
# <a name="create-an-extractor-in-microsoft-sharepoint-syntex"></a>Tworzenie wyodrębnianego programu w aplikacji Microsoft SharePoint Syntex


<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL2G]

<br/> 

Przed utworzeniem modelu klasyfikatora lub po nim w celu zautomatyzowania identyfikacji i klasyfikacji określonych typów dokumentów możesz opcjonalnie wybrać dodanie do modelu wyodrębniaczy w celu wyodrębnienia określonych informacji z tych dokumentów. Model może na przykład zawierać nie tylko identyfikację wszystkich dokumentów odnawiania  umowy dodanych do biblioteki dokumentów, ale także wyświetlanie daty rozpoczęcia usługi  dla każdego dokumentu jako wartości kolumny w bibliotece dokumentów.

Musisz utworzyć wyodrębnianie dla każdej jednostki w dokumencie, który chcesz wyodrębnić. W naszym przykładzie chcemy wyodrębnić dokument  **Data rozpoczęcia**  usługi dla każdego  **dokumentuContract Renewaldocument**  zidentyfikowanego przez model. Chcemy mieć możliwość wyświetlenia  ****  widoku w bibliotece dokumentów wszystkich Dokumentów Odnowień, w kolumnie z wartością daty **Rozpoczęcia** usługi dla każdego dokumentu. 

> [!NOTE]
> Aby utworzyć wyodrębniacz, należy użyć tych samych plików, które zostały wcześniej przekazane w celu przeszkolinia klasyfikatora. 

## <a name="name-your-extractor"></a>Nadaj nazwę wyodrębniaczowi

1. Na stronie głównej modelu na kafelku **Tworzenie i wyodrębnianie** pociągów kliknij pozycję **Wyodrębniator pociągu**.

2. Na **ekranie Nowy wyodrębniator jednostki** wpisz nazwę wyodrębnianego elementu w **polu Nazwa nowego wyodrębniaka** . Na przykład nadaj jej nazwę **Data rozpoczęcia** usługi, jeśli chcesz wyodrębnić datę rozpoczęcia usługi z każdego dokumentu Odnawianie umowy. Możesz także ponownie użyć poprzednio utworzonej kolumny (na przykład kolumny zarządzanych metadanych).

    Domyślnie typ kolumny to **Pojedynczy wiersz tekstu**. Jeśli chcesz zmienić typ kolumny, wybierz pozycję **Ustawienia** >  zaawansowane Typ kolumny **, a** następnie wybierz typ, którego chcesz użyć.

    ![Zrzut ekranu przedstawiający część ustawień zaawansowanych panelu wyodrębniającego encję Nowa jednostka z wyświetloną opcją Typ kolumny.](../media/content-understanding/advanced-settings-column-type.png) 

    > [!NOTE]
    > W przypadku wyodrębniaczy z typem **kolumny Pojedynczy wiersz tekstu** maksymalne ograniczenie znaków wynosi 255. Znaki przekraczające limit zostaną obcięte.

3. Po utworzeniu kliknij pozycję **Utwórz**.

## <a name="add-a-label"></a>Dodawanie etykiety

Następnym krokiem jest nadanie w przykładowych plikach szkoleniowych etykiety jednostki, którą chcesz wyodrębnić.

Utworzenie wyodrębniaka powoduje otwarcie strony wyodrębniacz. Zostanie wyświetlona lista plików przykładowych, a pierwszy plik na liście zostanie wyświetlony w przeglądarce.

1. W przeglądarce zaznacz dane, które chcesz wyodrębnić z plików. Jeśli na przykład chcesz wyodrębnić datę rozpoczęcia *usługi,* wyróżnij wartość daty w pierwszym pliku (*poniedziałek, 14 października 2019 r*.). a następnie kliknij przycisk **Zapisz**.  Wartość wyświetlana z pliku powinna być wyświetlana na liście Przykłady oznaczone etykietą w **kolumnie** Etykieta.
2. Wybierz **pozycję Następny plik** , aby automatycznie zapisać i otworzyć następny plik na liście w przeglądarce. Możesz też **wybrać pozycję Zapisz** , a następnie wybrać inny plik z **listy Przykłady oznaczone etykietą** .
3. W przeglądarce powtarzaj kroki 1 i 2, a następnie powtarzaj te czynności, aż zapisano etykietę we wszystkich pięciu plikach.

    ![Ustawienia zaawansowane.](../media/content-understanding/select-service-start-date.png) 

 
Po oznaczeniu pięciu plików etykietą zostanie wyświetlony transparent z powiadomieniem z informacjami o tym, aby przejść do szkolenia. Możesz dodać więcej etykiet do większej liczby dokumentów lub przejść do szkolenia. 

### <a name="use-find-to-search-your-file"></a>Przeszukiwanie pliku przy użyciu funkcji Znajdź

Za pomocą funkcji **Znajdź** możesz wyszukać w dokumencie encję, którą chcesz o etykiecie dodać.

   ![Znajdź w pliku.](../media/content-understanding/find-feature.png) 

Funkcja znajdź jest przydatna w przypadku wyszukiwania w dużym dokumencie lub gdy w dokumencie istnieje wiele wystąpień encji. Jeśli znajdziesz wiele wystąpień, możesz wybrać to, które potrzebujesz w wynikach wyszukiwania, aby przejść do tej lokalizacji w przeglądarce, aby dodać do niego etykietę.


## <a name="add-an-explanation"></a>Dodawanie objaśnienia

Na przykład utworzymy objaśnienie, które będzie zawierało wskazówkę co do formatu encji i jego odmian w przykładowych dokumentach. Na przykład wartość daty może mieć wiele różnych formatów, takich jak:
- 10/14/2019
- 14 października 2019 r.
- Poniedziałek, 14 października 2019 r.
 

Aby ułatwić zidentyfikowanie *daty rozpoczęcia* usługi, możesz utworzyć deseń objaśnienia.

1. W sekcji Objaśnienie wybierz pozycję **Nowy** i wpisz nazwę (na przykład *Date*).
2. W przypadku opcji Typ wybierz **pozycję Lista Deseń**.
3. W przypadku wartości podaj odmianę daty wyświetlaną w przykładowych plikach. Jeśli na przykład masz formaty daty wyświetlane jako 00-00-000, wprowadź dowolne odmiany widoczne w twoich dokumentach, takie jak:
    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000
4. Wybierz **Zapisz**.

> [!NOTE]
> Aby uzyskać więcej informacji na temat typów objaśnień, zobacz [Typy objaśnień](./explanation-types-overview.md).  


### <a name="use-the-explanation-library"></a>Korzystanie z biblioteki Objaśnienie

Aby utworzyć objaśnienia elementów, takich jak daty, łatwiej jest korzystać z [](./explanation-types-overview.md) biblioteki objaśnień niż ręcznie wprowadzać wszystkie odmiany. Biblioteka objaśnień to zestaw wstępnie wbudowanych objaśnień fraz i wzorców. Biblioteka próbuje uzyskać dostęp do wszystkich formatów typowych list fraz lub wzorców, takich jak daty, numery telefonów, kody pocztowe i wiele innych. 

W przypadku *przykładu Data* rozpoczęcia usługi bardziej wydajniej jest użyć wstępnie wbudowanego objaśnienia *Date w* bibliotece objaśnień:

1. W sekcji **Objaśnienie wybierz** pozycję **Nowy**, a następnie wybierz pozycję **Z biblioteki objaśnień**.
2. W bibliotece objaśnień wybierz pozycję **Data**. Możesz wyświetlać wszystkie odmiany daty, które zostały rozpoznane.
3. Wybierz opcję **Dodaj**.

    ![Biblioteka objaśnień.](../media/content-understanding/explanation-library.png) 

4. Na stronie **Tworzenie objaśnienia** pola *są* automatycznie wypełniane informacjami z biblioteki objaśnień. Wybierz **Zapisz**.

    ![Data.](../media/content-understanding/date-explanation-library.png) 

## <a name="train-the-model"></a>Szkolenie modelu 

Zapisywanie objaśnienia rozpocznij szkolenie. Jeśli model zawiera wystarczająco dużo informacji, aby wyodrębnić dane z oznaczonych plików przykładowych, zobaczysz każdy plik oznaczony etykietą **Dopasuj**.  

![Dopasuj.](../media/content-understanding/match2.png) 

Jeśli objaśnienie nie zawiera wystarczająco dużo informacji, aby znaleźć dane, które chcesz wyodrębnić, każdy plik zostanie oznaczony etykietą **Niezgodność**. Możesz kliknąć pozycję **Niedopasowane** pliki, aby wyświetlić więcej informacji o tym, dlaczego występują niezgodności.


## <a name="add-another-explanation"></a>Dodawanie kolejnego objaśnienia

Często niezgodność wskazuje, że podane przez nas objaśnienie nie zawierało wystarczającej ilości informacji, aby wyodrębnić wartość daty rozpoczęcia usługi w celu dopasowania jej do plików oznaczonych etykietami. Może być konieczne jego edytowanie lub dodanie kolejnego objaśnienia.

W naszym przykładzie zwróć uwagę, że ciąg tekstowy *Data rozpoczęcia usługi zawsze* poprzedza rzeczywistą wartość. Aby ułatwić zidentyfikowanie daty rozpoczęcia usługi, musisz utworzyć objaśnienie frazy.

1. W sekcji Objaśnienie wybierz pozycję **Nowy**, a następnie wpisz nazwę (na przykład Ciąg *prefiksu*).
2. Na liście Typ wybierz pozycję **Fraza**.
3. Jako *wartości użyj wartości Data* rozpoczęcia usługi.
4. Wybierz **Zapisz**.

    ![Ciąg prefiksu.](../media/content-understanding/prefix-string.png) 

## <a name="train-the-model-again"></a>Szkolenie modelu ponownie

Zapisanie objaśnienia ponownie rozpocznie szkolenie, tym razem z użyciem obu objaśnień z przykładu. Jeśli model zawiera wystarczająco dużo informacji, aby wyodrębnić dane z oznaczonych plików przykładowych, zobaczysz każdy plik oznaczony etykietą **Dopasuj**. 

Jeśli ponownie zostanie wyświetlony komunikat  o niezgodności plików oznaczonych etykietą, prawdopodobnie trzeba będzie utworzyć kolejne objaśnienie, aby udostępnić modelowi więcej informacji na temat typu dokumentu lub rozważyć wprowadzenie zmian w istniejących.

## <a name="test-your-model"></a>Testowanie modelu

Jeśli otrzymasz dopasowanie do oznaczonych plików przykładowych, możesz teraz przetestować model na pozostałych plikach przykładowych bez etykiety. Jest to opcjonalne, ale użyteczny krok w celu oceny "sprawności fizycznej" lub gotowości modelu przed jego użyciem przez przetestowanie go na plikach, których wcześniej nie widział model.

1. Na stronie głównej modelu kliknij **kartę** Test.  Model będzie uruchamiany na przykładowych plikach bez etykiety.
2. Na liście **Pliki testowe** są wyświetlane pliki przykładowe, aby pokazać, czy model umożliwia wyodrębnianie potrzebnych informacji. Skorzystaj z tych informacji, aby pomóc w określeniu skuteczności klasyfikatora w identyfikowaniu Twoich dokumentów.

    ![Przetestuj pliki.](../media/content-understanding/test-filies-extractor.png) 

## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Typy objaśnień](explanation-types-overview.md)

[Korzystanie z taksonomii magazynu terminów podczas tworzenia wyodrębnianego](leverage-term-store-taxonomy.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Stosowanie modelu](apply-a-model.md) 

[SharePoint Syntex tryb ułatwień dostępu](accessibility-mode.md)
