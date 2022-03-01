---
title: Wprowadzenie do przeszkolnych klasyfikatorów
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkDEFENDER
search.appverid:
- MOE150
- MET150
description: Klasyfikator Microsoft 365 to narzędzie, które można szkolenie w celu rozpoznawania różnych typów zawartości, dając mu przykłady do oglądu. W tym artykule pokazano, jak utworzyć i przeszkolenie niestandardowego klasyfikatora oraz jak przećwiczać je w celu zwiększenia dokładności.
ms.openlocfilehash: 263791549e314a116f21231e8dc4cde5be380cb7
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005734"
---
# <a name="get-started-with-trainable-classifiers"></a>Wprowadzenie do przeszkolnych klasyfikatorów

Przeszkolny Microsoft 365 klasyfikator to narzędzie, które może pomóc w rozpoznawczym typach zawartości, dając mu przykłady do oglądu. Po przeszkoleniu możesz za jego pomocą zidentyfikować element do stosowania etykiet wrażliwości Office, zasad zgodności komunikacji i zasad etykiet przechowywania.

Utworzenie niestandardowego, przeszkoliwnego klasyfikatora polega najpierw na podaniem próbki, która jest wybierana przez człowieka i dobrze dopasowana do kategorii. Następnie, po przetworzeniu tych danych, należy przetestować możliwość przewidywania klasyfikatorów, podając połączenie próbek dodatnich i ujemnych. W tym artykule pokazano, jak utworzyć i przeszkolenie niestandardowego klasyfikatora oraz jak zwiększyć wydajność niestandardowych przeszkolonych klasyfikatorów i wstępnie przeszkolonych klasyfikatorów przez ich okres istnienia przez ponowne przeszkolenie.

Aby dowiedzieć się więcej o różnych typach klasyfikatorów, zobacz [Informacje o przeszkolnych klasyfikatorach](classifier-learn-about.md).

Obejrzyj ten klip wideo, aby szybko podsumować tworzenie przeszkoliwnego klasyfikatora. Aby uzyskać szczegółowe informacje, nadal musisz przeczytać ten pełny artykuł.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGL7]


## <a name="prerequisites"></a>Wymagania wstępne

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Klasyfikatory to funkcja zgodności Microsoft 365 E5 lub E5. Aby można było korzystać z tych subskrypcji, musisz mieć jedną z tych subskrypcji.

### <a name="permissions"></a>Uprawnienia

Aby uzyskać dostęp do klasyfikatorów w interfejsie użytkownika: 

- Administrator globalny musi wybrać opcję dla dzierżawy, aby tworzyć niestandardowe klasyfikatory.
- Rola administratora zgodności jest wymagana do przeszkolinia klasyfikatora.

Do używania klasyfikatorów w tych scenariuszach potrzebne są konta z tymi uprawnieniami:

- Scenariusz zasad etykiet przechowywania: Role zarządzania rekordami i zarządzania przechowywaniem 
- Scenariusz zasad etykiet wrażliwości: Administrator zabezpieczeń, Administrator zgodności, Administrator danych zgodności
- Scenariusz zasad zgodności komunikacji: Administrator zarządzania ryzykiem w niejawnym programie testów, administrator przeglądu nadzorczych 

> [!IMPORTANT]
> Domyślnie tylko użytkownik, który tworzy niestandardowy klasyfikator, może przeszkolić i przeglądać prognozy wprowadzone przez tego klasyfikatora.

## <a name="prepare-for-a-custom-trainable-classifier"></a>Przygotowanie na niestandardowy klasyfikator przeszkolny 

Warto zrozumieć, co należy zrobić w celu utworzenia niestandardowego, przeszkoliwnego klasyfikatora, zanim zanurzysz się. 

### <a name="timeline"></a>Oś czasu

Ta oś czasu odzwierciedla przykładowe wdrożenie klasyfikatorów przeszkolnych.

![trainable-classifier-timeline.](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> Klauzula opt-in jest wymagana po raz pierwszy dla przeszkolnych klasyfikatorów. Ukończenie oceny planu bazowego Microsoft 365 organizacji w ciągu dwunastu dni. Skontaktuj się z administratorem globalnym, aby rozpostartować proces rejestracji.

### <a name="overall-workflow"></a>Ogólny przepływ pracy

Aby dowiedzieć się więcej o ogólnym przepływie pracy tworzenia niestandardowych, przeszkolnych klasyfikatorów, zobacz Przepływ procesu tworzenia klasyfikatorów przeszkolnych [klientów](classifier-learn-about.md#process-flow-for-creating-custom-classifiers).

### <a name="seed-content"></a>Zawartość iniekcyjna

Aby przeszkolić klasyfikatora niezależnie i dokładnie zidentyfikować element jako element w określonej kategorii treści, musisz najpierw przedstawić go z wieloma przykładami typu zawartości określonej kategorii. To podawanie próbek dla przeszkoliwnego klasyfikatora jest nazywane *inicjatorem*. Zawartość iniekcyjna jest wybierana przez ludzi i oceniana jako kategoria treści.

> [!TIP]
> Należy mieć co najmniej 50 próbek dodatnich i nawet 500. Przeszkolny klasyfikator będzie przetwarzać maksymalnie 500 najnowszych utworzonych przykładów (według sygnatury daty/godziny utworzenia pliku). Im więcej próbek poowie, tym dokładniejszy będzie podpowiadał klasfikator.

### <a name="testing-content"></a>Testowanie zawartości

Gdy przeszkolny klasyfikator przetworzona jest wystarczająca ilość dodatnich próbek do zbudowania modelu prognozowania, należy sprawdzić prognozy, które wykonuje, aby sprawdzić, czy klasyfikator prawidłowo rozróżnia elementy, które pasują do kategorii, a elementy, które nie są takie. W tym celu należy wybrać kolejną, mając większej, zbiór zawartości pobranej przez człowieka, która powinna się znaleźć w kategorii, i próbki, które nie powinny zostać do tej kategorii. Należy testowania danych innych niż początkowe dane inicjalnie podane po raz pierwszy. Po przeprocesów tych danych ręcznie przechodzisz przez wyniki i sprawdzasz, czy każda prognoza jest poprawna, nieprawidłowa lub nie masz pewności. Klasyfikator przeszkoliwczy używa tych opinii w celu ulepszenia swojego modelu prognozowania.

> [!TIP]
> Aby uzyskać najlepsze wyniki, należy mieć w zestawie próbek testowych co najmniej 200 elementów z równomiernym rozkładem wyników dodatnich i ujemnych.

## <a name="how-to-create-a-trainable-classifier"></a>Jak utworzyć przeszkolny klasyfikator

1. Zbierz od 50 do 500 elementów w zawartości iniekcyjną. Muszą to być tylko próbki, które zdecydowanie reprezentują typ zawartości, którą ma przećwiczyć klasyfikator, aby dokładnie identyfikował go jako należący do kategorii klasyfikacji. Aby uzyskać [informacje na](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) temat obsługiwanych typów plików, zobacz Domyślne rozszerzenia nazw plików przeszukanych i typy plików SharePoint server.

   > [!IMPORTANT]
   > Upewnij się, że elementy w zestawie iniekków **są silnymi przykładami** kategorii. Przeszkolny klasyfikator początkowo tworzy swój model na podstawie tego, co jest inicjatorem. Klasyfikator zakłada, że wszystkie próbki iniekatorów są silnymi wartościami dodatnimi i nie wiadomo, czy próbka jest słaba, czy ujemna dla danej kategorii.

2. Umieść zawartość iniekcyjną w folderze SharePoint Online, który jest przeznaczony tylko do przechowywania *zawartości iniekcyjną*. Zanotuj adres URL witryny, biblioteki i folderu.

   > [!TIP]
   > Jeśli utworzysz nową witrynę i folder na dane iniekcyjną, przed utworzeniem przeszkoliwnego klasyfikatora, który użyje danych iniektora, odczekaj co najmniej godzinę na zindeksowanie tej lokalizacji.

3. Zaloguj się w celu Centrum zgodności platformy Microsoft 365 uprawnień przy użyciu roli administratora zgodności lub administratora zabezpieczeń i otwórz <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a> Centrum zgodności platformy Microsoft 365 lub Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">dane portalu</a> > **klasyfikacja**.

4. Wybierz **kartę Klasyfikatory do przeszkoli** .

5. Wybierz **pozycję Create trainable classifier (Utwórz klasyfikator przeszkolny**).

6. Wypełnij odpowiednie wartości dla pól `Name` kategorii `Description` elementów, które ma identyfikować ten przeszkolny klasyfikator.

7. Wybierz adres URL SharePoint Online, biblioteki i folderu dla witryny zawartości iniektora od kroku 2. Wybierz pozycję `Add`.

8. Przejrzyj ustawienia i wybierz pozycję `Create trainable classifier`.

9. W ciągu 24 godzin przeszkolny klasyfikator przetnie dane iniekcyjną i sbuduje model prognozowania. Stan klasyfikatora jest w `In progress` trakcie przetwarzania danych iniekatora. Po zakończeniu przetwarzania danych w iniekcie przez klasyfikatora stan zmieni się na `Need test items`.

10. Możesz teraz wyświetlić stronę szczegółów, wybierając klasyfikator.

    > [!div class="mx-imgBorder"]
    > ![przeszkolny klasyfikator gotowy do testowania.](../media/classifier-trainable-ready-to-test-detail.png)

11. Zbierz co najmniej 200 testowych elementów zawartości (10 000 maks),aby uzyskać najlepsze wyniki. Powinny one być kombinacją elementów, które są silne dodatnie, silne wartości ujemne, a inne, które są nieco mniej oczywiste w ich przymiocie. Aby uzyskać [informacje na](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) temat obsługiwanych typów plików, zobacz Domyślne rozszerzenia nazw plików przeszukanych i typy plików SharePoint server.

12. Umieść testową zawartość w folderze SharePoint Online, który jest przeznaczony tylko do przechowywania *zawartości testowej*. Zanotuj adres URL witryny SharePoint Online, biblioteki i folderu.

    > [!TIP]
    > Jeśli utworzysz nową witrynę i folder na dane testowe, przed utworzeniem przeszkoliwnego klasyfikatora, który użyje danych iniektora, należy zezwolić na zindeksowanie tej lokalizacji co najmniej godzinę.

13. Wybierz pozycję `Add items to test`.

14. Wybierz adres URL SharePoint Online, biblioteki i folderu witryny testowej zawartości z kroku 12. Wybierz pozycję `Add`.

15. Zakończ kreatora, wybierając przycisk `Done`. Przetwarzanie plików testowych przez przeszkolny klasyfikatora może potrwać do godziny.

16. Gdy przeszkolny klasyfikator przejmie przetwarzanie Twoich plików testowych, stan na stronie szczegółów zmieni się na `Ready to review`. Jeśli chcesz zwiększyć rozmiar próbki testowej, `Add items to test` wybierz i zezwomij na przeszkoliwny klasyfikator w celu przetwarzania dodatkowych elementów.

    > [!div class="mx-imgBorder"]
    > ![gotowy do przejrzenia zrzut ekranu.](../media/classifier-trainable-ready-to-review-detail.png)

17. Wybierz kartę `Tested items to review` , aby przejrzeć elementy.

18. Microsoft 365 prezentować 30 elementów jednocześnie. Przejrzyj je i w polu `We predict this item is "Relevant". Do you agree?` wybierz pozycję albo `Yes` `No` lub `Not sure, skip to next item`. Dokładność modelu jest automatycznie aktualizowana po co 30 elementach.

    > [!div class="mx-imgBorder"]
    > ![pole Przeglądanie elementów.](../media/classifier-trainable-review-detail.png)

19. Przejrzyj *co najmniej* 200 elementów. Po stabilizacji wyniku dokładności pojawi się opcja publikowania, a zostanie jej nadany stan `Ready to use`.

    > [!div class="mx-imgBorder"]
    > ![oraz gotowe do opublikowania.](../media/classifier-trainable-review-ready-to-publish.png)

20. Opublikuj klasyfikatora.

21. Po opublikowaniu klasyfikator będzie dostępny jako warunek w Office z etykietami [wrażliwości, zasady](apply-sensitivity-label-automatically.md) automatycznego stosowania etykiet przechowywania [](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) na podstawie warunku i zgodności [komunikacji.](communication-compliance.md)
