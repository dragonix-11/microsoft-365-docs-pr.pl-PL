---
title: Tworzenie klasyfikatora w usłudze Microsoft SharePoint Syntex
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
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: Dowiedz się, jak utworzyć klasyfikator w usłudze Microsoft SharePoint Syntex.
ms.openlocfilehash: 6c47d2fe2f7f2b67533587f0956281c2b577dbe0
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882379"
---
# <a name="create-a-classifier-in-microsoft-sharepoint-syntex"></a>Tworzenie klasyfikatora w usłudze Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL0R]  

</br>

Klasyfikator to typ modelu, którego można użyć do zautomatyzowania identyfikacji i klasyfikacji typu dokumentu. Możesz na przykład zidentyfikować wszystkie dokumenty *odnawiania kontraktu* dodane do biblioteki dokumentów, takie jak pokazano na poniższej ilustracji.

![Dokument odnawiania kontraktu.](../media/content-understanding/contract-renewal.png)

Utworzenie klasyfikatora umożliwia utworzenie nowego [typu zawartości SharePoint](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview), który będzie skojarzony z modelem.

Podczas tworzenia klasyfikatora należy utworzyć *wyjaśnienia* , aby zdefiniować model. Dzięki temu można zanotować typowe dane, których można oczekiwać od spójnego znajdowania tego typu dokumentu. 

Użyj przykładów typu dokumentu ("pliki przykładowe"), aby "wytrenować" model w celu zidentyfikowania plików o tym samym typie zawartości.

Aby utworzyć klasyfikator, należy wykonać następujące czynności:
1. Nadaj modelowi nazwę.
2. Dodaj przykładowe pliki.
3. Etykietowanie przykładowych plików.
4. Utwórz wyjaśnienie.
5. Przetestuj model.

> [!NOTE]
> Podczas gdy model używa klasyfikatora do identyfikowania i klasyfikowania typów dokumentów, możesz również pobrać określone informacje z każdego pliku zidentyfikowanego przez model. W tym celu utwórz **wyodrębniacz** , który ma zostać dodany do modelu. Zobacz [Tworzenie wyodrębniacza](create-an-extractor.md).

## <a name="name-your-model"></a>Nadaj modelowi nazwę

Pierwszym krokiem tworzenia modelu jest nadanie mu nazwy:

1. W centrum zawartości wybierz pozycję **Nowy**, a następnie **utwórz model**.
2. W okienku **Nowy dokument z opisem modelu** w polu **Nazwa** wpisz nazwę modelu. Jeśli na przykład chcesz zidentyfikować dokumenty odnawiania kontraktu, możesz nadać modelowi nazwę *Odnowienie kontraktu*.
3. Wybierz pozycję **Utwórz**. Spowoduje to utworzenie strony głównej modelu.</br>

    ![Strona główna modelu klasyfikatora.](../media/content-understanding/model-home.png)

Podczas tworzenia modelu tworzysz również nowy typ zawartości witryny. Typ zawartości reprezentuje kategorię dokumentów, które mają wspólne cechy i udostępniają kolekcję kolumn lub właściwości metadanych dla danej zawartości. SharePoint typy zawartości są zarządzane za pośrednictwem [galerii Typy zawartości](https://support.microsoft.com/office/create-or-customize-a-site-content-type-27eb6551-9867-4201-a819-620c5658a60f). W tym przykładzie podczas tworzenia modelu tworzysz nowy typ zawartości *Odnawianie kontraktu* .

Wybierz pozycję **Ustawienia zaawansowane**, jeśli chcesz zamapować ten model na istniejący typ zawartości przedsiębiorstwa w <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">galerii typów zawartości</a> SharePoint, aby użyć jego schematu. Enterprise typy zawartości są przechowywane w Centrum typów zawartości w centrum administracyjnym SharePoint i są syndykatowane we wszystkich lokacjach w dzierżawie. Należy pamiętać, że chociaż możesz użyć istniejącego typu zawartości, aby wykorzystać jego schemat, aby ułatwić identyfikację i klasyfikację, nadal musisz wytrenować model w celu wyodrębnienia informacji z zidentyfikowanych plików.</br>

![Ustawienia zaawansowane.](../media/content-understanding/advanced-settings.png)

## <a name="add-your-example-files"></a>Dodawanie przykładowych plików

Na stronie głównej modelu dodaj przykładowe pliki, które będą potrzebne do wytrenowania modelu w celu zidentyfikowania typu dokumentu. </br>
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4D0iX] 

</br>

> [!NOTE]
> Należy użyć tych samych plików zarówno do trenowania klasyfikatora, jak i [wyodrębniania](create-an-extractor.md). Zawsze możesz dodać więcej później, ale zazwyczaj dodajesz pełny zestaw przykładowych plików. Oznacz niektóre, aby wytrenować model, i przetestuj pozostałe nieoznaczone etykiety, aby ocenić kondycję modelu. 

W przypadku zestawu treningowego chcesz użyć zarówno pozytywnych, jak i negatywnych przykładów:
- Pozytywny przykład: dokumenty reprezentujące typ dokumentu. Zawierają one ciągi i informacje, które zawsze znajdują się w tym typie dokumentu.
- Negatywny przykład: dowolny inny dokument, który nie reprezentuje dokumentu, który chcesz sklasyfikować. 

Pamiętaj, aby użyć co najmniej pięciu pozytywnych przykładów i co najmniej jednego negatywnego przykładu do trenowania modelu.  Chcesz utworzyć dodatkowe, aby przetestować model po zakończeniu procesu trenowania.

Aby dodać przykładowe pliki:

1. Na stronie głównej modelu na kafelku **Dodawanie przykładowych plików** kliknij pozycję **Dodaj pliki**.
2. Na stronie **Wybieranie przykładowych plików dla modelu** wybierz przykładowe pliki z biblioteki Pliki szkoleniowe w centrum zawartości. Jeśli nie przekazano ich w tym miejscu, wybierz, aby przekazać je teraz, klikając **Upload**, aby skopiować je do biblioteki plików szkoleniowych.
3. Po wybraniu przykładowych plików do wytrenowania modelu kliknij przycisk **Dodaj**.

    ![Wybierz przykładowe pliki.](../media/content-understanding/select-sample.png) 

## <a name="label-your-example-files"></a>Etykietowanie przykładowych plików

Po dodaniu przykładowych plików należy oznaczyć je jako przykłady dodatnie lub negatywne.

1. Na stronie głównej modelu na kafelku **Classify files and run training (Klasyfikowanie plików i uruchamianie trenowania)** kliknij pozycję **Train classifier (Trenowanie klasyfikatora**).
   Spowoduje to wyświetlenie strony etykiety zawierającej listę przykładowych plików z pierwszym plikiem widocznym w przeglądarce.
2. W przeglądarce w górnej części pierwszego przykładowego pliku powinien zostać wyświetlony tekst z pytaniem, czy plik jest przykładem właśnie utworzonego modelu. Jeśli jest to pozytywny przykład, wybierz pozycję **Tak**. Jeśli jest to przykład negatywny, wybierz pozycję **Nie**.
3. Z listy **Przykłady oznaczone** po lewej stronie wybierz dodatkowe pliki, których chcesz użyć jako przykłady, i oznacz je etykietami. 

    ![Strona główna klasyfikatora.](../media/content-understanding/classifier-home-page.png) 


> [!NOTE]
> Oznacz co najmniej pięć pozytywnych przykładów. Należy również oznaczyć etykietą co najmniej jeden negatywny przykład. 

## <a name="create-an-explanation"></a>Tworzenie objaśnień

Następnym krokiem jest utworzenie objaśnienia na stronie Trenowanie. Wyjaśnienie ułatwia modelowi zrozumienie sposobu rozpoznawania dokumentu. Na przykład dokumenty odnowienia umowy zawsze zawierają *żądanie dodatkowego* ciągu tekstowego ujawnienia.

> [!Note]
> W przypadku użycia z wyodrębniaczami wyjaśnienie identyfikuje ciąg, który chcesz wyodrębnić z dokumentu. 

Aby utworzyć wyjaśnienie:

1. Na stronie głównej modelu wybierz kartę **Trenowanie** , aby przejść do strony Trenowanie.
2. Na stronie Trenowanie w sekcji **Wytrenowane pliki** powinna zostać wyświetlona lista wcześniej oznaczonych przykładowych plików. Wybierz jeden z pozytywnych plików z listy i zostanie wyświetlony w przeglądarce.
3. W sekcji Wyjaśnienie wybierz pozycję **Nowy** , a następnie pozycję **Puste**.
4. Na stronie **Tworzenie wyjaśnienia** :</br>
    a. Wpisz **nazwę** (na przykład "Blok ujawniania").</br>
    b. Wybierz **typ**. W przykładzie wybierz pozycję **Lista fraz**, ponieważ dodasz ciąg tekstowy.</br>
    c. W polu **Wpisz tutaj** wpisz ciąg. W przykładzie dodaj ciąg "Żądanie dodatkowego ujawnienia". Jeśli ciąg musi uwzględniać wielkość liter, możesz wybrać pozycję **Wielkość** liter.</br>
    d. Kliknij **Zapisz**.

    ![Utwórz wyjaśnienie.](../media/content-understanding/explanation.png) 
    
5. Centrum zawartości sprawdza teraz, czy utworzone wyjaśnienie jest wystarczająco kompletne, aby poprawnie zidentyfikować pozostałe pliki przykładowe oznaczone etykietami jako pozytywne i negatywne przykłady. W sekcji **Wytrenowane pliki** sprawdź kolumnę **Ewaluacja** po zakończeniu trenowania, aby wyświetlić wyniki. W plikach jest wyświetlana wartość **Match (Dopasowanie**), jeśli utworzone wyjaśnienia były wystarczające do dopasowania do wartości oznaczonych jako dodatnie lub ujemne.

    ![Dopasuj wartość.](../media/content-understanding/match.png) 

    Jeśli otrzymasz niezgodność w plikach **oznaczonych** etykietą, może być konieczne utworzenie dodatkowego objaśnienia, aby udostępnić modelowi więcej informacji w celu zidentyfikowania typu dokumentu. W takim przypadku kliknij plik, aby uzyskać więcej informacji o tym, dlaczego wystąpiła niezgodność.

Po wytrenowanym wyodrębniaczu ten wytrenowany wyodrębniacz może być używany jako wyjaśnienie. W sekcji **Wyjaśnienia** jest to wyświetlane jako **odwołanie do modelu**.

![Zrzut ekranu przedstawiający sekcję Objaśnienia przedstawiającą typ Odwołanie do modelu.](../media/content-understanding/explanations-model-reference.png)

## <a name="test-your-model"></a>Testowanie modelu

Jeśli otrzymasz dopasowanie do oznaczonych plików przykładowych, możesz teraz przetestować model w pozostałych nieoznaczonych plikach przykładowych, których model nie widział wcześniej. Jest to opcjonalne, ale przydatny krok do oceny "kondycji" lub gotowości modelu przed jego użyciem przez przetestowanie go na plikach, których model nie widział wcześniej.

1. Na stronie głównej modelu wybierz kartę **Test** . Spowoduje to uruchamianie modelu w nieoznakowanych plikach przykładowych.
2. Na liście **Pliki testowe** przykładowe pliki są wyświetlane i pokazują, czy model przewidział ich wyniki dodatnie lub ujemne. Te informacje ułatwiają określenie skuteczności klasyfikatora w identyfikowaniu dokumentów.

    ![Testowanie nieoznakowanych plików.](../media/content-understanding/test-on-files.png) 

## <a name="see-also"></a>Zobacz też

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Omówienie usługi Document Understanding](document-understanding-overview.md)

[Typy wyjaśnień](explanation-types-overview.md)

[Stosowanie modelu](apply-a-model.md) 

[tryb ułatwień dostępu SharePoint Syntex](accessibility-mode.md)