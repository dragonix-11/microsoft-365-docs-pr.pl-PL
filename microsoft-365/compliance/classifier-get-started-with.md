---
title: Wprowadzenie do klasyfikatorów z możliwością szkolenia
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
description: Klasyfikator platformy Microsoft 365 to narzędzie, które można wytrenować w celu rozpoznawania różnych typów zawartości, udostępniając przykłady do obejrzenia. W tym artykule przedstawiono sposób tworzenia i trenowania klasyfikatora niestandardowego oraz sposobu ich ponownego trenowania w celu zwiększenia dokładności.
ms.openlocfilehash: ff23f24145cee1b694f96e933919dddf779dfd9a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631386"
---
# <a name="get-started-with-trainable-classifiers"></a>Wprowadzenie do klasyfikatorów z możliwością szkolenia

Klasyfikator trenowalny platformy Microsoft 365 to narzędzie, które można wytrenować w celu rozpoznawania różnych typów zawartości, udostępniając przykłady do obejrzenia. Po wytrenowaniu można go używać do identyfikowania elementów do stosowania etykiet poufności pakietu Office, zasad zgodności komunikacji i zasad etykiet przechowywania.

Najpierw utworzenie niestandardowego klasyfikatora trenowalnego polega na nadaniu mu próbek, które są wybierane przez człowieka i pozytywnie pasują do kategorii. Następnie, po przetworzeniu tych, można przetestować zdolność klasyfikatorów do przewidywania, dając mu mieszankę pozytywnych i negatywnych próbek. W tym artykule pokazano, jak utworzyć i wytrenować klasyfikator niestandardowy oraz jak zwiększyć wydajność niestandardowych klasyfikatorów trenowalnych i wstępnie wytrenowanych klasyfikatorów w okresie ich istnienia poprzez ponowne trenowanie.

Aby dowiedzieć się więcej na temat różnych typów klasyfikatorów, zobacz [Learn about trainable classifiers (Dowiedz się więcej o klasyfikatorach z możliwością trenowania](classifier-learn-about.md)).

Obejrzyj to wideo, aby zapoznać się z krótkim podsumowaniem tworzenia klasyfikatora z możliwością trenowania. Aby uzyskać szczegółowe informacje, nadal musisz przeczytać ten pełny artykuł.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGL7]


## <a name="prerequisites"></a>Wymagania wstępne

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Klasyfikatory są funkcją Microsoft 365 E5 lub E5 Compliance. Aby móc z nich korzystać, musisz mieć jedną z tych subskrypcji.

### <a name="permissions"></a>Uprawnienia

Aby uzyskać dostęp do klasyfikatorów w interfejsie użytkownika: 

- Administrator globalny musi wyrazić zgodę na dzierżawę w celu utworzenia niestandardowych klasyfikatorów.
- Rola administratora zgodności jest wymagana do trenowania klasyfikatora.

Konta z tymi uprawnieniami będą potrzebne do używania klasyfikatorów w następujących scenariuszach:

- Scenariusz zasad przechowywania etykiet: Role zarządzania rekordami i zarządzania przechowywaniem 
- Scenariusz zasad etykiet poufności: Administrator zabezpieczeń, Administrator zgodności, Administrator danych zgodności
- Scenariusz zasad zgodności z komunikacją: Administracja zarządzania ryzykiem wewnętrznym, administrator przeglądu nadzoru 

> [!IMPORTANT]
> Domyślnie tylko użytkownik tworzący klasyfikator niestandardowy może trenować i przeglądać przewidywania dokonane przez ten klasyfikator.

## <a name="prepare-for-a-custom-trainable-classifier"></a>Przygotowanie do niestandardowego klasyfikatora trenowalnego 

Warto zrozumieć, co jest związane z tworzeniem niestandardowego klasyfikatora trenowalnego przed rozpoczęciem pracy. 

### <a name="timeline"></a>Oś czasu

Ta oś czasu odzwierciedla przykładowe wdrożenie klasyfikatorów z możliwością trenowania.

![trainable-classifier-timeline.](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> Zgoda jest wymagana po raz pierwszy dla klasyfikatorów z możliwością trenowania. Ukończenie podstawowej oceny zawartości organizacji trwa dwanaście dni, a platforma Microsoft 365. Skontaktuj się z administratorem globalnym, aby rozpocząć proces zgody.

### <a name="overall-workflow"></a>Ogólny przepływ pracy

Aby dowiedzieć się więcej na temat ogólnego przepływu pracy tworzenia niestandardowych klasyfikatorów trenowalnych, zobacz [Przepływ procesów tworzenia niestandardowych klasyfikatorów trenowalnych](classifier-learn-about.md#process-flow-for-creating-custom-classifiers).

### <a name="seed-content"></a>Zawartość inicjowania

Jeśli chcesz, aby klasyfikator trenowalny niezależnie i dokładnie identyfikował element jako znajdujący się w określonej kategorii zawartości, najpierw musisz przedstawić go z wieloma przykładami typu zawartości, które znajdują się w kategorii. To podawanie próbek klasyfikatorowi trainable jest znane jako *rozsiewanie*. Zawartość inicjowania jest wybierana przez człowieka i jest oceniana jako reprezentująca kategorię zawartości.

> [!TIP]
> Musisz mieć co najmniej 50 pozytywnych próbek i aż 500. Klasyfikator trainable będzie przetwarzać maksymalnie 500 najnowszych utworzonych przykładów (według daty/sygnatury czasowej utworzonego pliku). Im więcej przykładów podasz, tym dokładniejsze będą przewidywania klasyfikatora.

### <a name="testing-content"></a>Testowanie zawartości

Gdy klasyfikator trenowalny przetworzy wystarczająco dużo pozytywnych przykładów, aby utworzyć model przewidywania, musisz przetestować przewidywania, które wykonuje, aby sprawdzić, czy klasyfikator może poprawnie odróżnić elementy zgodne z kategorią i elementami, które tego nie zrobią. Można to zrobić, wybierając inny, miejmy nadzieję większy, zestaw zawartości wybranej przez człowieka, który składa się z próbek, które powinny należeć do kategorii i próbek, które nie będą. Należy przetestować dane inne niż początkowe dane inicjowania podane po raz pierwszy. Po ich przeróżniu możesz ręcznie przejść przez wyniki i sprawdzić, czy każde przewidywanie jest poprawne, niepoprawne, czy też nie masz pewności. Klasyfikator trainable używa tej opinii, aby ulepszyć swój model przewidywania.

> [!TIP]
> Aby uzyskać najlepsze wyniki, masz co najmniej 200 elementów w zestawie przykładów testowych z równomiernym rozkładem dopasowań dodatnich i ujemnych.

## <a name="how-to-create-a-trainable-classifier"></a>Jak utworzyć klasyfikator trenowalny

1. Zbierz od 50 do 500 elementów zawartości inicjowania. Muszą to być tylko przykłady, które silnie reprezentują typ zawartości, którą klasyfikator trainable ma pozytywnie zidentyfikować jako będącą w kategorii klasyfikacji. Zobacz [Domyślne rozszerzenia nazw przeszukanych plików i analizowane typy plików w programie SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) dla obsługiwanych typów plików.

   > [!IMPORTANT]
   > Upewnij się, że elementy w zestawie inicjowania są **silnymi** przykładami kategorii. Klasyfikator trainable początkowo tworzy swój model w oparciu o to, z czym go inicjujesz. Klasyfikator zakłada, że wszystkie próbki nasion są silnymi wynikami dodatnimi i nie ma możliwości poznania, czy próbka jest słabym lub negatywnym dopasowaniem do kategorii.

2. Umieść zawartość inicjowania w folderze usługi SharePoint Online przeznaczonym tylko do przechowywania *zawartości inicjującej*. Zanotuj adres URL witryny, biblioteki i folderu.

   > [!TIP]
   > Jeśli utworzysz nową lokację i folder dla danych inicjatora, przed utworzeniem klasyfikatora trainable, który będzie używać tych danych inicjacyjnych, zaczekaj co najmniej godzinę na indeksowanie tej lokalizacji.

3. Zaloguj się do portal zgodności Microsoft Purview z dostępem administratora zgodności lub administratora zabezpieczeń i otwórz <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> lub <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalu</a> > **Klasyfikacja danych**.

4. Wybierz kartę **Trainable classifiers (Klasyfikatory z możliwością trenowania** ).

5. Wybierz **pozycję Utwórz klasyfikator trenowalny**.

6. Wypełnij odpowiednie wartości dla `Name` pól i `Description` kategorii elementów, które chcesz zidentyfikować w tym klasyfikatorze trenowalnym.

7. Wybierz witrynę, bibliotekę i adres URL folderu usługi SharePoint Online dla witryny zawartości inicjowania z kroku 2. Wybierz pozycję `Add`.

8. Przejrzyj ustawienia i wybierz pozycję `Create trainable classifier`.

9. W ciągu 24 godzin klasyfikator trainable przetworzy dane inicjowania i utworzy model przewidywania. Stan klasyfikatora to `In progress` czas, w jaki przetwarza dane inicjowania. Po zakończeniu przetwarzania danych inicjałów przez klasyfikator stan zmieni się na `Need test items`.

10. Teraz możesz wyświetlić stronę szczegółów, wybierając klasyfikator.

    > [!div class="mx-imgBorder"]
    > ![klasyfikator trainable gotowy do testowania.](../media/classifier-trainable-ready-to-test-detail.png)

11. Zbierz co najmniej 200 testowych elementów zawartości (maksymalnie 10 000), aby uzyskać najlepsze wyniki. Powinny to być mieszanka elementów, które są silne pozytywy, silne negatywy i niektóre, które są nieco mniej oczywiste w ich naturze. Zobacz [Domyślne rozszerzenia nazw przeszukanych plików i analizowane typy plików w programie SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) dla obsługiwanych typów plików.

12. Umieść zawartość testową w folderze usługi SharePoint Online przeznaczonym tylko do przechowywania *zawartości testowej*. Zanotuj adres URL witryny, biblioteki i folderu usługi SharePoint Online.

    > [!TIP]
    > Jeśli utworzysz nową lokację i folder dla danych testowych, przed utworzeniem klasyfikatora trainable, który będzie używać tych danych inicjacyjnych, zaczekaj co najmniej godzinę na indeksowanie tej lokalizacji.

13. Wybierz pozycję `Add items to test`.

14. Wybierz witrynę, bibliotekę i adres URL folderu usługi SharePoint Online dla witryny zawartości testowej z kroku 12. Wybierz pozycję `Add`.

15. Zakończ pracę kreatora, wybierając pozycję `Done`. Przetwarzanie plików testowych przez klasyfikator trainable potrwa do godziny.

16. Po zakończeniu przetwarzania plików testowych klasyfikator trenowalny stan na stronie szczegółów zmieni się na `Ready to review`. Jeśli chcesz zwiększyć rozmiar próbki testowej, wybierz `Add items to test` i zezwól klasyfikatorowi trainable na przetwarzanie dodatkowych elementów.

    > [!div class="mx-imgBorder"]
    > ![gotowy do przejrzenia zrzutu ekranu.](../media/classifier-trainable-ready-to-review-detail.png)

17. Wybierz `Tested items to review` kartę, aby przejrzeć elementy.

18. Platforma Microsoft 365 będzie prezentować 30 elementów jednocześnie. Przejrzyj je i w `We predict this item is "Relevant". Do you agree?` polu wybierz albo `Yes` lub `No` `Not sure, skip to next item`. Dokładność modelu jest automatycznie aktualizowana po każdym 30 elementach.

    > [!div class="mx-imgBorder"]
    > ![przejrzyj pole elementów.](../media/classifier-trainable-review-detail.png)

19. Przejrzyj *co najmniej* 200 elementów. Po ustabilizowaniu wyniku dokładności opcja **publikowania** stanie się dostępna, a stan klasyfikatora to `Ready to use`.

    > [!div class="mx-imgBorder"]
    > ![wynik dokładności i gotowy do opublikowania.](../media/classifier-trainable-review-ready-to-publish.png)

20. Opublikuj klasyfikator.

21. Po opublikowaniu klasyfikator będzie dostępny jako warunek automatycznego [etykietowania pakietu Office z etykietami poufności](apply-sensitivity-label-automatically.md), [automatycznie zastosuj zasady etykiet przechowywania na podstawie warunku](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) i [zgodności z komunikacją](communication-compliance.md).
