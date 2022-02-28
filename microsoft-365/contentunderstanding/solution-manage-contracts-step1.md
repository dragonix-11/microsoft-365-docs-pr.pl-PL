---
title: Krok nr 1. Identyfikowanie plików SharePoint Syntex wyodrębnianie danych przy użyciu funkcji podpisów
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
description: Dowiedz się, jak za SharePoint Syntex identyfikować pliki kontraktu i wyodrębniać dane przy użyciu Microsoft 365 danych.
ms.openlocfilehash: c654c72ef36bf86337b7564efc68e4523516f4f9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985486"
---
# <a name="step-1-use-sharepoint-syntex-to-identify-contract-files-and-extract-data"></a>Krok nr 1. Identyfikowanie plików SharePoint Syntex wyodrębnianie danych przy użyciu funkcji podpisów

Twoja organizacja potrzebuje sposobu identyfikowania i klasyfikowania wszystkich dokumentów kontraktowych z wielu obierania plików. Ponadto warto mieć możliwość szybkiego wyświetlania kilku kluczowych elementów w każdym z zidentyfikowanych plików umowy (na przykład *klient, wykonawca* *i kwota opłaty*). Można to zrobić za pomocą narzędzia [SharePoint Syntex](index.md) w celu utworzenia modelu rozumienia dokumentu i zastosowania go do biblioteki dokumentów.

## <a name="overview-of-the-process"></a>Omówienie procesu

[W zrozumieniu](document-understanding-overview.md) dokumentu są używane modele sztucznej inteligencji w celu zautomatyzowania klasyfikacji plików i wyodrębniania informacji. Model zrozumienia dokumentów jest również optymalny w przypadku wyodrębniania informacji z dokumentów niestrukturalnych i półstrukturalnych, gdy potrzebne informacje nie są zawarte w tabelach lub formularzach, takich jak umowy. 

Modele opisowe dokumentów korzystają z technologii optycznego rozpoznawania znaków (OCR, Optical Character Recognition) do skanowania plików PDF, obrazów i plików TIFF podczas przeszkolania modelu przy użyciu plików przykładowych, jak i podczas uruchamiania modelu z plikami w bibliotece dokumentów.

1. Najpierw należy znaleźć co najmniej pięć plików przykładowych, przy użyciu których można "przeszkolić" model w celu wyszukania cech charakterystycznych dla typu zawartości, który próbujesz zidentyfikować (umowa). 

2. Za SharePoint Syntex utwórz nowy model zrozumienia dokumentu. W przypadku plików przykładowych należy [utworzyć klasyfikatora](create-a-classifier.md). Wyszukując klasyfikatora za pomocą plików przykładowych, uczysz go, jak wyszukiwać cechy specyficzne dla tego, co będzie widać w umowach firmowych. Można na przykład [utworzyć "](create-a-classifier.md#create-an-explanation)objaśnienie", które wyszukuje określone ciągi znaków w umowach, takie jak Umowa o świadczenie *usług, Warunki* umowy i *Wynagrodzenia*. Możesz nawet przeszkolić wyjaśnienie w celu wyszukiwania tych ciągów w określonych sekcjach dokumentu lub znajdujących się obok innych ciągów. Jeśli uważasz, że twój klasyfikator został przeszkolony w zakresie informacji, których potrzebujesz, możesz przetestować model na przykładowym zestawie plików przykładowych, aby sprawdzić, jak wydajna jest ta klasa. Po przetestowaniu w razie potrzeby możesz wprowadzić zmiany w objaśnieniach, aby ułatwić ich przeprowadzanie. 

3. W swoim modelu możesz utworzyć [wyodrębnianie](create-an-extractor.md) konkretnych fragmentów danych z każdej umowy. Na przykład w przypadku każdej umowy najważniejszą informacją jest to, kto jest klientem, nazwa wykonawcy i całkowity koszt.

4. Po pomyślnym utworzeniu modelu [zastosuj go do SharePoint dokumentów](apply-a-model.md). Podczas przekazywania dokumentów do biblioteki dokumentów będzie uruchamiany model rozumienia dokumentu, który będzie identyfikować i klasyfikować wszystkie pliki zgodne z typem zawartości kontraktów zdefiniowanym w modelu. Wszystkie pliki sklasyfikowane jako umowy będą wyświetlane w widoku biblioteki niestandardowej. W plikach będą również wyświetlane wartości z każdej umowy zdefiniowanej w wyodrębniarze.

   ![Umowy w bibliotece dokumentów.](../media/content-understanding/doc-lib-solution.png)

5. W przypadku stosowania wymagań dotyczących przechowywania lub zabezpieczeń dotyczących umów można również użyć modelu w celu zastosowania etykiety przechowywania [](apply-a-retention-label-to-a-model.md) lub etykiety wrażliwości[](apply-a-sensitivity-label-to-a-model.md), która zapobiegnie usunięciu umów przez określony czas lub ograniczeniu dostępu do umów.

## <a name="steps-to-create-and-train-your-model"></a>Procedura tworzenia i szkolenia modelu

> [!NOTE]
> W tych krokach możesz użyć przykładowych plików w repozytorium Zasoby rozwiązania do zarządzania [umowami](https://github.com/pnp/syntex-samples/tree/main/scenario%20assets/Contracts%20Management). Przykłady w tym repozytorium zawierają zarówno dokument opisowy pliki modelu, jak i pliki służące do przeszkolinia modelu.

### <a name="create-a-contract-model"></a>Tworzenie modelu umowy

Pierwszym krokiem jest utworzenie modelu umowy.

1. W centrum zawartości wybierz pozycję **Nowy**, **a następnie pozycję Utwórz model**.

2. W **okienku Nowy dokument opisowy modelu** w polu **Nazwa** wpisz nazwę modelu. W przypadku tego rozwiązania do zarządzania umowami możesz nazwać model *Umowa*.

4. Wybierz pozycję **Utwórz**. Powoduje to utworzenie strony głównej modelu.</br>

    ![Zrzut ekranu przedstawiający stronę główną Umowa.](../media/content-understanding/models-contract-home-page.png)


### <a name="train-your-model-to-classify-a-type-of-file"></a>Szkolenie modelu w celu klasyfikowania typu pliku

#### <a name="add-example-files-for-your-model"></a>Dodawanie przykładowych plików do modelu

Musisz dodać co najmniej pięć plików przykładowych, które są dokumentami kontraktu, a jeden plik przykładowy nie jest dokumentem kontraktowym (na przykład zestawieniem pracy). 

1. Na stronie **Modele > w** obszarze **Akcje klawiszyDadowane** >  **pliki przykładowe** wybierz pozycję **Dodaj pliki**.

   ![Zrzut ekranu przedstawiający stronę Umowy z wyróżniona opcją Dodaj przykładowe pliki.](../media/content-understanding/key-actions-add-example-files.png)

2. Na **stronie Wybierz pliki przykładowe swojego modelu** otwórz folder Umowa, wybierz pliki, których chcesz użyć, a następnie wybierz pozycję **Dodaj**. Jeśli nie masz tam plików przykładowych, **wybierz pozycję Upload**, aby je dodać.

#### <a name="label-the-files-as-positive-or-negative-examples"></a>Przykłady oznaczania plików jako dodatnich lub ujemnych

1. Na stronie **Modele > w** obszarze **Akcje** >  kluczaSklasyfikuj pliki i **uruchom szkolenie** wybierz pozycję **Klasyfikator pociągu**.

   ![Zrzut ekranu przedstawiający stronę Umowy z wyróżniona opcją Klasyfikowanie plików i uruchamianie szkolenia.](../media/content-understanding/key-actions-classify-files.png)

2. Na stronie Klasyfikator kontraktu **> Modele >** w podglądzie u góry pierwszego pliku przykładowego zobaczysz tekst z pytaniem, czy plik jest przykładem utworzonego modelu Umowy. Jeśli jest to dodatni przykład, wybierz pozycję **Tak**. Jeśli jest to przykład ujemny, wybierz pozycję **Nie**.

3. Z listy **Przykłady oznaczone** etykietami po lewej stronie zaznacz inne pliki, których chcesz użyć jako przykładów, i oznacz je etykietami. 

    ![Strona główna klasyfikatora.](../media/content-understanding/models-contract-classifier.png) 

#### <a name="add-at-least-one-explanation-to-train-the-classifier"></a>Dodawanie co najmniej jednego objaśnienia w celu przeszkolinia klasyfikatora 

1. Na stronie **> Typ > klasyfikatora kontraktu** wybierz **kartę** Pociąg.

2. W **sekcji Przeszkolone** pliki zostanie wyświetlona lista plików przykładowych oznaczonych wcześniej etykietą. Wybierz jeden z dodatnich plików z listy, aby wyświetlić go w przeglądarce.

3. W sekcji **Objaśnienia** wybierz **pozycję Nowy,** a następnie Pozycję **Puste**.

4. Na **stronie Tworzenie objaśnienia** :

    a. W **polu Nazwa** wpisz nazwę objaśnienia (na przykład "Umowa").

    b. W polu **Typ objaśnienia** wybierz pozycję **Lista fraz**, ponieważ dodajesz ciąg tekstowy.

    c. W polu **listy Fraza** wpisz ciąg (na przykład "UMOWA"). Możesz wybrać pozycję Wielkość **liter,** jeśli w ciągu musi być wróżniana wielkość liter.

    d. Wybierz **pozycję Zapisz i pociąg.**

    ![Zrzut ekranu przedstawiający panel Tworzenie objaśnienia.](../media/content-understanding/contract-classifier-create-explanation.png) 

#### <a name="test-your-model"></a>Testowanie modelu

Możesz przetestować model Kontrakt na przykładowych plikach, które nie widziały go wcześniej. Jest to opcjonalne, ale może być przydatne najlepszym rozwiązaniem.

1. Na stronie **> Typ > klasyfikatora kontraktu** wybierz **kartę** Test. Model będzie uruchamiany w przypadku plików przykładowych bez etykiety.

2. Na liście **Pliki testowe** pliki przykładowe są wyświetlane i pokazują, czy model przewidział, że są dodatnie, czy ujemne. Skorzystaj z tych informacji, aby pomóc w określeniu skuteczności klasyfikatora w identyfikowaniu Twoich dokumentów.

    ![Zrzut ekranu przedstawiający pliki bez etykiety na liście Pliki tekstowe.](../media/content-understanding/test-on-files.png) 

3. Gdy zakończysz, wybierz pozycję **Zakończ szkolenie**.

### <a name="create-and-train-an-extractor"></a>Tworzenie i szkolenie wyodrębniacz

1. Na stronie **Modele > w** obszarze **Akcje** >  **kluczoweTworzenie** i szkolenie wyodrębniaczy wybierz pozycję **Utwórz wyodrębniator**.

   ![Zrzut ekranu przedstawiający stronę Umowy z wyróżniona opcją Utwórz i wyodrębniacze pociągów.](../media/content-understanding/key-actions-create-extractors.png)

2. W **panelu New entity extractor (Nowa** jednostka) w polu **New name (** Nowa nazwa) wpisz nazwę wyodrębniającego. Na przykład nadaj jej nazwę *Klient* , jeśli chcesz wyodrębnić nazwę klienta z każdej umowy.

3. Po utworzeniu konta wybierz pozycję **Utwórz**.

#### <a name="label-the-entity-you-want-to-extract"></a>Oznaczanie jednostki, którą chcesz wyodrębnić

Po utworzeniu wyodrębnianego fragmentatora zostanie otwarta strona wyodrębnianego fragmentatora. Zostanie wyświetlona lista plików przykładowych, a pierwszy plik na liście zostanie wyświetlony w przeglądarce.

![Zrzut ekranu przedstawiający stronę Client Extractor Labeled Examples (Przykłady klientów).](../media/content-understanding/client-extractor-labeled-examples.png) 

Aby o etykiecie encji:

1. W przeglądarce zaznacz dane, które chcesz wyodrębnić z plików. Jeśli na przykład chcesz wyodrębnić *klienta,* wyróżnij wartość klienta w pierwszym pliku (w tym przykładzie *Best For You Organics*), a następnie wybierz pozycję **Zapisz**. Wartość z pliku będzie wyświetlana na liście Przykłady oznaczone etykietą **w kolumnie Etykieta**.

2. Wybierz **pozycję Następny plik** , aby autozazadać i otworzyć następny plik na liście w przeglądarce. Możesz też **wybrać pozycję Zapisz**, a następnie wybrać inny plik z listy **Przykłady oznaczone etykietą** .

3. W przeglądarce powtarzaj kroki 1 i 2, a następnie powtarzaj te czynności do momentu zapisania etykiety we wszystkich plikach.

Po oznaczeniu plików etykietą zostanie wyświetlony transparent z powiadomieniem z informacjami o tym, aby przejść do szkolenia. Możesz dodać etykiety do większej liczby dokumentów lub przejść do szkolenia.

#### <a name="add-an-explanation"></a>Dodawanie objaśnienia

Możesz utworzyć objaśnienie, które daje wskazówkę co do formatu jednostki i jego odmian w plikach przykładowych. Na przykład wartość daty może być w wielu różnych formatach, takich jak:

- 10/14/2019
- 14 października 2019 r.
- Poniedziałek, 14 października 2019 r.

Aby ułatwić zidentyfikowanie *daty rozpoczęcia umowy*, możesz utworzyć objaśnienie wzorca.

1. W sekcji **Objaśnienia** wybierz **pozycję Nowy,** a następnie Pozycję **Puste**.

2. Na **stronie Tworzenie objaśnienia** :

    a. W **polu Nazwa** wpisz nazwę objaśnienia (na przykład *Data*).

    b. W polu **Typ objaśnienia** wybierz pozycję **Lista Deseń**.

    c. W **polu Wartość** podaj odmianę daty wyświetlaną w plikach przykładowych. Jeśli na przykład masz formaty daty wyświetlane jako 00-00-000, wprowadź dowolne odmiany widoczne w twoich dokumentach, takie jak:

    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000

4. Wybierz **pozycję Zapisz i pociąg.**

#### <a name="test-your-model-again"></a>Ponownie przetestuj model

Możesz przetestować model Kontrakt na przykładowych plikach, które nie widziały go wcześniej. Jest to opcjonalne, ale może być przydatne najlepszym rozwiązaniem.

1. Na stronie **> Typ > klasyfikatora kontraktu** wybierz **kartę** Test. Model będzie uruchamiany w przypadku plików przykładowych bez etykiety.

2. Na liście **Pliki testowe** są wyświetlane twoje pliki przykładowe i pokazuje, czy model umożliwia wyodrębnianie potrzebnych informacji. Skorzystaj z tych informacji, aby pomóc w określeniu skuteczności klasyfikatora w identyfikowaniu Twoich dokumentów.

3. Gdy zakończysz, wybierz pozycję **Zakończ szkolenie**.

### <a name="apply-your-model-to-a-document-library"></a>Stosowanie modelu do biblioteki dokumentów

Aby zastosować model do SharePoint dokumentów:

1. Na stronie **Modele > w** obszarze **Akcje** >  kluczyStosowanie **modelu do bibliotek** wybierz pozycję **Zastosuj model**.

   ![Zrzut ekranu przedstawiający stronę Umowy z wyróżniona opcją Zastosuj model do bibliotek.](../media/content-understanding/key-actions-apply-model.png)

2. W **panelu Dodaj umowę** wybierz witrynę SharePoint zawierającą bibliotekę dokumentów, do której chcesz zastosować model. Jeśli witryna nie jest wyświetlona na liście, użyj pola wyszukiwania, aby ją znaleźć. Wybierz opcję **Dodaj**.

    > [!NOTE]
    > Musisz mieć uprawnienia *do zarządzania listą* lub *uprawnienia do* edytowania biblioteki dokumentów, do których chcesz zastosować model.

3. Po wybraniu witryny wybierz bibliotekę dokumentów, do której chcesz zastosować model.

4. Ponieważ model jest skojarzony z typem zawartości, po zastosowaniu go do biblioteki zostanie on dodajony typ zawartości i jego widok z wyodrębnioną etykietą wyświetloną jako kolumny. Ten widok jest domyślnie widokiem domyślnym biblioteki, ale opcjonalnie możesz zdecydować, aby nie był to widok domyślny, zaznaczając pozycję Ustawienia  zaawansowane i czyszcząc pole wyboru Ustaw ten nowy widok jako domyślny.

5. Wybierz **pozycję Dodaj** , aby zastosować model do biblioteki.

6. Na **stronie > Typ** umowy w sekcji Biblioteki z tym **modelem** zobaczysz adres URL witryny SharePoint na liście.

    ![Zrzut ekranu przedstawiający stronę główną Umowa z wyświetloną sekcją Biblioteki w tym modelu.](../media/content-understanding/contract-libraries-with-this-model.png)

7. W **Ustawienia** >  **Ustawienia Ustawienia library**:

   - Dodaj kolumnę o nazwie **Stan** i wybierz **pozycję Wybór** jako typ kolumny.
   - Stosowanie wartości **W recenzji**, **Zatwierdzone** **i Odrzucone** .

Po zastosowaniu modelu do biblioteki dokumentów możesz rozpocząć przekazywanie dokumentów do witryny i wyświetlić wyniki.

## <a name="next-step"></a>Następny krok

[Krok 2. Użyj Microsoft Teams, aby utworzyć kanał zarządzania umowami](solution-manage-contracts-step2.md)