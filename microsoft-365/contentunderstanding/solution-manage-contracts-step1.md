---
title: Krok nr 1. Używanie SharePoint Syntex do identyfikowania plików kontraktów i wyodrębniania danych
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Dowiedz się, jak używać SharePoint Syntex do identyfikowania plików kontraktów i wyodrębniania danych przy użyciu rozwiązania Microsoft 365.
ms.openlocfilehash: 7d2874260ce7a307aa42c67ba571104ed4c4da87
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368094"
---
# <a name="step-1-use-sharepoint-syntex-to-identify-contract-files-and-extract-data"></a>Krok nr 1. Używanie SharePoint Syntex do identyfikowania plików kontraktów i wyodrębniania danych

Twoja organizacja potrzebuje sposobu identyfikowania i klasyfikowania wszystkich dokumentów kontraktowych z wielu otrzymywanych plików. Chcesz również szybko wyświetlić kilka kluczowych elementów w każdym z zidentyfikowanych plików kontraktu (na przykład *Klient*, *Wykonawca* i *Kwota opłaty*). Można to zrobić za pomocą [SharePoint Syntex](index.md), aby utworzyć model zrozumienia dokumentu i zastosować go do biblioteki dokumentów.

## <a name="overview-of-the-process"></a>Omówienie procesu

[Omówienie dokumentów](document-understanding-overview.md) używa modeli sztucznej inteligencji (AI) do automatyzacji klasyfikacji plików i wyodrębniania informacji. Modele interpretacji dokumentów są również optymalne w wyodrębnianiu informacji z dokumentów bez struktury i częściowo ustrukturyzowanych, w których potrzebne informacje nie są zawarte w tabelach lub formularzach, takich jak kontrakty. 

Modele interpretacji dokumentów używają technologii optycznego rozpoznawania znaków (OCR) do skanowania plików PDF, obrazów i plików TIFF, zarówno podczas trenowania modelu z przykładowymi plikami, jak i podczas uruchamiania modelu względem plików w bibliotece dokumentów.

1. Najpierw należy znaleźć co najmniej pięć przykładowych plików, których można użyć do "wytrenowania" modelu w celu wyszukania cech specyficznych dla typu zawartości, który próbujesz zidentyfikować (kontrakt). 

2. Za pomocą SharePoint Syntex utwórz nowy model interpretacji dokumentów. Korzystając z przykładowych plików, musisz [utworzyć klasyfikator](create-a-classifier.md). Szkoląc klasyfikator przy użyciu przykładowych plików, nauczysz go wyszukiwać cechy specyficzne dla tego, co można zobaczyć w kontraktach firmy. Na przykład [utwórz "wyjaśnienie",](create-a-classifier.md#create-an-explanation) które wyszukuje określone ciągi znajdujące się w umowach, takie jak *umowa serwisowa*, *warunki umowy* i *kompensacja*. Możesz nawet wytrenować wyjaśnienie, aby wyszukać te ciągi w określonych sekcjach dokumentu lub znajdujących się obok innych ciągów. Jeśli uważasz, że wytrenowałeś klasyfikator z wymaganymi informacjami, możesz przetestować model na przykładowym zestawie przykładowych plików, aby zobaczyć, jak wydajny jest. Po przetestowaniu w razie potrzeby możesz wprowadzić zmiany w wyjaśnieniach, aby były bardziej wydajne. 

3. W modelu można [utworzyć wyodrębniacz](create-an-extractor.md) do ściągania określonych fragmentów danych z każdego kontraktu. Na przykład dla każdej umowy najbardziej interesuje Cię informacja o tym, kim jest klient, nazwa wykonawcy i całkowity koszt.

4. Po pomyślnym utworzeniu modelu [zastosuj go do biblioteki dokumentów SharePoint](apply-a-model.md). Podczas przekazywania dokumentów do biblioteki dokumentów model interpretacji dokumentów będzie uruchamiany i będzie identyfikować i klasyfikować wszystkie pliki zgodne z typem zawartości kontraktów zdefiniowanym w modelu. Wszystkie pliki sklasyfikowane jako kontrakty będą wyświetlane w widoku biblioteki niestandardowej. Pliki będą również wyświetlać wartości z każdego kontraktu zdefiniowanego w wyodrębniaczu.

   ![Kontrakty w bibliotece dokumentów.](../media/content-understanding/doc-lib-solution.png)

5. Jeśli masz wymagania dotyczące przechowywania lub zabezpieczeń dla kontraktów, możesz również użyć modelu, aby zastosować [etykietę przechowywania](apply-a-retention-label-to-a-model.md) lub [etykietę poufności](apply-a-sensitivity-label-to-a-model.md) , która uniemożliwi usunięcie kontraktów przez określony okres lub ograniczyć, kto może uzyskać dostęp do umów.

## <a name="steps-to-create-and-train-your-model"></a>Kroki tworzenia i trenowania modelu

> [!NOTE]
> W tych krokach można użyć przykładowych plików w [repozytorium Zasobów rozwiązania do zarządzania kontraktami](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management). Przykłady w tym repozytorium zawierają zarówno pliki modelu, jak i pliki używane do trenowania modelu.

### <a name="create-a-contract-model"></a>Tworzenie modelu kontraktu

Pierwszym krokiem jest utworzenie modelu kontraktu.

1. W centrum zawartości wybierz pozycję **Nowy**, a następnie **utwórz model**.

2. W okienku **Nowy model zrozumienia dokumentu** w polu **Nazwa** wpisz nazwę modelu. W przypadku tego rozwiązania do zarządzania kontraktami możesz nazwać model *Contract*.

4. Wybierz pozycję **Utwórz**. Spowoduje to utworzenie strony głównej modelu.</br>

    ![Zrzut ekranu przedstawiający stronę główną Kontraktu.](../media/content-understanding/models-contract-home-page.png)


### <a name="train-your-model-to-classify-a-type-of-file"></a>Trenowanie modelu w celu klasyfikowania typu pliku

#### <a name="add-example-files-for-your-model"></a>Dodawanie przykładowych plików dla modelu

Musisz dodać co najmniej pięć przykładowych plików, które są dokumentami kontraktów, oraz jeden przykładowy plik, który nie jest dokumentem kontraktu (na przykład instrukcja pracy). 

1. Na stronie **Modele > Kontrakt** w obszarze **Akcje** >  **kluczyDodaj przykładowe pliki** wybierz pozycję **Dodaj pliki**.

   ![Zrzut ekranu przedstawiający stronę Kontrakty z wyróżnioną opcją Dodaj przykładowe pliki.](../media/content-understanding/key-actions-add-example-files.png)

2. Na stronie **Wybieranie przykładowych plików dla modelu** otwórz folder Kontrakt, wybierz pliki, których chcesz użyć, a następnie wybierz pozycję **Dodaj**. Jeśli nie masz tam przykładowych plików, wybierz pozycję **Przekaż** , aby je dodać.

#### <a name="label-the-files-as-positive-or-negative-examples"></a>Oznaczanie plików jako pozytywnych lub negatywnych przykładów

1. Na stronie **Modele > Kontrakt** w obszarze **Akcje** >  **kluczyKlasyzowanie plików i uruchamianie trenowania** wybierz pozycję **Train classifier (Trenowanie klasyfikatora**).

   ![Zrzut ekranu przedstawiający stronę Kontrakty z wyróżnioną opcją klasyfikowania plików i uruchamiania trenowania.](../media/content-understanding/key-actions-classify-files.png)

2. Na stronie **Model > Contract > Contract classifier (Model > Contract > Contract)** w przeglądarce w górnej części pierwszego przykładowego pliku zobaczysz tekst z pytaniem, czy plik jest przykładem utworzonego modelu kontraktu. Jeśli jest to pozytywny przykład, wybierz pozycję **Tak**. Jeśli jest to przykład negatywny, wybierz pozycję **Nie**.

3. Z listy **Przykłady oznaczone** po lewej stronie wybierz inne pliki, których chcesz użyć jako przykłady, i oznacz je etykietami. 

    ![Strona główna klasyfikatora.](../media/content-understanding/models-contract-classifier.png) 

#### <a name="add-at-least-one-explanation-to-train-the-classifier"></a>Dodaj co najmniej jedno wyjaśnienie, aby wytrenować klasyfikator 

1. Na stronie **Model > Contract > Contract classifier (Klasyfikator kontraktów)** wybierz kartę **Train (Trenowanie** ).

2. W sekcji **Wytrenowane pliki** zostanie wyświetlona lista plików przykładowych, które zostały wcześniej oznaczone etykietą. Wybierz jeden z pozytywnych plików z listy, aby wyświetlić go w przeglądarce.

3. W sekcji **Wyjaśnienia** wybierz pozycję **Nowy** , a następnie pozycję **Puste**.

4. Na stronie **Tworzenie wyjaśnienia** :

    a. W polu **Nazwa** wpisz nazwę wyjaśnienia (np. "Umowa").

    b. W polu **Typ wyjaśnienia** wybierz pozycję **Lista fraz**, ponieważ dodajesz ciąg tekstowy.

    c. W polu **Lista fraz** wpisz ciąg (na przykład "AGREEMENT"). Jeśli ciąg musi uwzględniać wielkość liter, możesz wybrać pozycję **Wielkość** liter.

    d. Wybierz pozycję **Zapisz i wytrenuj**.

    ![Zrzut ekranu przedstawiający panel Tworzenie wyjaśnienia.](../media/content-understanding/contract-classifier-create-explanation.png) 

#### <a name="test-your-model"></a>Testowanie modelu

Model kontraktu można przetestować na przykładowych plikach, których wcześniej nie widział. Jest to opcjonalne rozwiązanie, ale może być przydatnym najlepszym rozwiązaniem.

1. Na stronie **Model > Contract > Contract classifier (Klasyfikator kontraktów)** wybierz kartę **Test** . Spowoduje to uruchamianie modelu w plikach przykładowych bez etykiet.

2. Na liście **Pliki testowe** przykładowe pliki są wyświetlane i pokazują, czy model przewidział ich wyniki dodatnie lub ujemne. Te informacje ułatwiają określenie skuteczności klasyfikatora w identyfikowaniu dokumentów.

    ![Zrzut ekranu przedstawiający nieoznakowane pliki na liście Pliki tekstowe.](../media/content-understanding/test-on-files.png) 

3. Po zakończeniu wybierz pozycję **Zakończ trenowanie**.

### <a name="create-and-train-an-extractor"></a>Tworzenie i trenowanie ekstraktora

1. Na stronie **Modele > Kontrakt** w obszarze **Akcje** >  **kluczyUtwórz i wytrenuj wyodrębniacze** wybierz pozycję **Utwórz wyodrębniacz**.

   ![Zrzut ekranu przedstawiający stronę Kontrakty z wyróżnioną opcją Tworzenie i trenowanie wyodrębniaczy.](../media/content-understanding/key-actions-create-extractors.png)

2. W panelu **New entity extractor (Nowy wyodrębniacz jednostki** ) w polu **Nowa nazwa** wpisz nazwę swojego wyodrębniacza. Na przykład nadaj mu nazwę *Klient* , jeśli chcesz wyodrębnić nazwę klienta z każdego kontraktu.

3. Po zakończeniu wybierz pozycję **Utwórz**.

#### <a name="label-the-entity-you-want-to-extract"></a>Etykieta jednostki, którą chcesz wyodrębnić

Podczas tworzenia ekstraktora zostanie otwarta strona wyodrębniacza. W tym miejscu zostanie wyświetlona lista przykładowych plików z pierwszym plikiem na liście wyświetlonej w przeglądarce.

![Zrzut ekranu przedstawiający stronę przykładów z etykietami klienta.](../media/content-understanding/client-extractor-labeled-examples.png) 

Aby oznaczyć jednostkę etykietą:

1. W przeglądarce wybierz dane, które chcesz wyodrębnić z plików. Jeśli na przykład chcesz wyodrębnić *klienta*, wyróżnisz wartość klienta w pierwszym pliku (w tym przykładzie *Best For You Organics*), a następnie wybierz pozycję **Zapisz**. Wartość wyświetlana z pliku zostanie wyświetlona na liście **Przykłady oznaczone** w kolumnie **Etykieta** .

2. Wybierz pozycję **Następny plik** , aby automatycznie zapisać i otworzyć następny plik na liście w przeglądarce. Lub wybierz pozycję **Zapisz**, a następnie wybierz inny plik z listy **Przykłady oznaczone etykietami** .

3. W przeglądarce powtórz kroki 1 i 2, a następnie powtarzaj je do momentu zapisania etykiety we wszystkich plikach.

Po oznaczeniu plików etykietą zostanie wyświetlony baner powiadomień informujący o przejściu do szkolenia. Możesz wybrać etykietę większej liczby dokumentów lub przejść do szkolenia.

#### <a name="add-an-explanation"></a>Dodawanie objaśnienia

Możesz utworzyć wyjaśnienie, które zawiera wskazówkę dotyczącą samego formatu jednostki i odmian, które może mieć w przykładowych plikach. Na przykład wartość daty może być w wielu różnych formatach, takich jak:

- 10/14/2019
- 14 października 2019 r.
- Poniedziałek, 14 października 2019 r.

Aby ułatwić identyfikację *daty rozpoczęcia kontraktu*, możesz utworzyć wyjaśnienie wzorca.

1. W sekcji **Wyjaśnienia** wybierz pozycję **Nowy** , a następnie pozycję **Puste**.

2. Na stronie **Tworzenie wyjaśnienia** :

    a. W polu **Nazwa** wpisz nazwę wyjaśnienia (na przykład *Date*).

    b. W polu **Typ wyjaśnienia** wybierz pozycję **Lista wzorców**.

    c. W polu **Wartość** podaj odmianę daty wyświetlaną w przykładowych plikach. Jeśli na przykład masz formaty dat, które są wyświetlane jako 0/00/0000, wprowadź wszelkie odmiany wyświetlane w dokumentach, takie jak:

    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000

4. Wybierz pozycję **Zapisz i wytrenuj**.

#### <a name="test-your-model-again"></a>Ponownie przetestuj model

Model kontraktu można przetestować na przykładowych plikach, których wcześniej nie widział. Jest to opcjonalne rozwiązanie, ale może być przydatnym najlepszym rozwiązaniem.

1. Na stronie **Model > Contract > Contract classifier (Klasyfikator kontraktów)** wybierz kartę **Test** . Spowoduje to uruchamianie modelu w plikach przykładowych bez etykiet.

2. Na liście **Pliki testowe** przykładowe pliki są wyświetlane i pokazują, czy model może wyodrębnić potrzebne informacje. Te informacje ułatwiają określenie skuteczności klasyfikatora w identyfikowaniu dokumentów.

3. Po zakończeniu wybierz pozycję **Zakończ trenowanie**.

### <a name="apply-your-model-to-a-document-library"></a>Stosowanie modelu do biblioteki dokumentów

Aby zastosować model do biblioteki dokumentów SharePoint:

1. Na stronie **Models > Contract (Modele > kontraktu**) w obszarze **Akcje kluczyAplikuj** >  model do bibliotek wybierz pozycję **Zastosuj model**.

   ![Zrzut ekranu przedstawiający stronę Kontrakty z wyróżnioną opcją Zastosuj model do bibliotek.](../media/content-understanding/key-actions-apply-model.png)

2. Na panelu **Dodawanie kontraktu** wybierz witrynę SharePoint zawierającą bibliotekę dokumentów, do których chcesz zastosować model. Jeśli witryna nie jest wyświetlana na liście, użyj pola wyszukiwania, aby ją znaleźć. Wybierz opcję **Dodaj**.

    > [!NOTE]
    > Musisz mieć uprawnienia *Do zarządzania listą* lub *Uprawnienia do edycji* do biblioteki dokumentów, do których stosujesz model.

3. Po wybraniu witryny wybierz bibliotekę dokumentów, do której chcesz zastosować model.

4. Ponieważ model jest skojarzony z typem zawartości, po zastosowaniu go do biblioteki doda typ zawartości i jego widok z wyodrębnionymi etykietami wyświetlanymi jako kolumny. Ten widok jest domyślnie widokiem domyślnym biblioteki, ale opcjonalnie możesz wybrać, aby nie był to widok domyślny, wybierając pozycję **Ustawienia zaawansowane** i wyczyść pole wyboru **Ustaw nowy widok jako domyślny** .

5. Wybierz pozycję **Dodaj** , aby zastosować model do biblioteki.

6. Na stronie **Model > Contract** w sekcji **Biblioteki z tym modelem** zostanie wyświetlony adres URL witryny SharePoint.

    ![Zrzut ekranu strony głównej Kontrakt przedstawiający sekcję Biblioteki z tym modelem.](../media/content-understanding/contract-libraries-with-this-model.png)

7. W **obszarze ustawień Ustawienia** >  **Library**:

   - Dodaj kolumnę o nazwie **Status** i wybierz pozycję **Wybór** jako typ kolumny.
   - Zastosuj wartości **W przeglądzie**, **Zatwierdzone** i **Odrzucone** .

Po zastosowaniu modelu do biblioteki dokumentów możesz rozpocząć przekazywanie dokumentów do witryny i wyświetlić wyniki.

## <a name="next-step"></a>Następny krok

[Krok 2. Tworzenie kanału zarządzania kontraktami przy użyciu Microsoft Teams](solution-manage-contracts-step2.md)
