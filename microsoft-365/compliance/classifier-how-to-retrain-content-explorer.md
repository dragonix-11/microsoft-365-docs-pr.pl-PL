---
title: Jak ponownie przeszkolenie klasyfikatora w Eksploratorze zawartości
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak przekazać opinię przeszkolnym klasyfikatorowi w Eksploratorze zawartości.
ms.openlocfilehash: bbc724b94997a4668115314df0c627dcfa5ddc77
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021289"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Jak ponownie przeszkolenie klasyfikatora w Eksploratorze zawartości

Przeszkolny Microsoft 365 klasyfikator to narzędzie, które może pomóc w rozpoznawczym typach zawartości, dając mu przykłady do oglądu. Po przeszkoleniu możesz za jego pomocą identyfikować elementy do stosowania etykiet wrażliwości Office, zasad zgodności komunikacji i zasad przechowywania etykiet przechowywania.

W tym artykule pokazano, jak zwiększyć wydajność niestandardowych przeszkolnych klasyfikatorów przez przekazywanie im dodatkowych opinii.

Aby dowiedzieć się więcej o różnych typach klasyfikatorów, zobacz [Informacje o przeszkolnych klasyfikatorach](classifier-learn-about.md).

Ten klip wideo zawiera krótkie podsumowanie procesu dostosowywania i ponownego sprawdzania. Aby uzyskać szczegółowe informacje, nadal musisz przeczytać ten pełny artykuł.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGMs]

> [!NOTE]
> Nie można ponownie przeszkolić wstępnie przeszkolonych klasyfikatorów.

## <a name="permissions"></a>Uprawnienia

Aby uzyskać dostęp do klasyfikatorów w centrum Microsoft 365 zgodności:

- Rola administratora zgodności lub administrator danych zgodności jest wymagana w celu przeszkolinia klasyfikatora

Do używania klasyfikatorów w tych scenariuszach potrzebne są konta z tymi uprawnieniami:

- Scenariusz zasad etykiet przechowywania: Role zarządzania rekordami i zarządzania przechowywaniem 

## <a name="overall-workflow"></a>Ogólny przepływ pracy

> [!IMPORTANT]
> W Eksploratorze zawartości możesz przekazać opinię na temat automatycznego stosowania zasad etykiet przechowywania Exchange elementów i stosować klasyfikator jako warunek. **Jeśli nie masz zasad przechowywania, które automatycznie stosuje etykietę przechowywania do elementów Exchange i używa specyfikatora jako warunku, zatrzymaj się tutaj.**

Gdy używasz klasyfikatorów, możesz zwiększyć dokładność klasyfikacji, które są przez nie klasyfikowane. Możesz to zrobić, oceniając jakość klasyfikacji wykonanych dla elementów, które zostały zidentyfikowane jako zgodne lub nie. Po 30 ocenach klasyfikatora przyjmuje on te opinie i automatycznie ponownie dostosowuje się do siebie.

Aby dowiedzieć się więcej o ogólnym przepływie pracy ponownego szkolenia klasyfikatora, zobacz Przepływ przetwarzania [ponownego szkolenia klasyfikatora](classifier-learn-about.md#retraining-classifiers).

> [!NOTE]
> Zanim będzie można przeszkolić klasyfikatora, musi on być już opublikowany i w użyciu.

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Jak ponownie przeszkolenie klasyfikatora w Eksploratorze zawartości

1. Zaloguj się w celu Centrum zgodności platformy Microsoft 365 dostępu za pomocą roli administratora zgodności lub administratora zabezpieczeń i otwórz **Centrum zgodności platformy Microsoft 365** >  KlasyfikacjaDanychSkontentu > . 
2. Na liście **Filtruj według etykiet, typów informacji** lub kategorii rozwiń kategorię **Klasyfikatorzy do przeszkoli.**

> [!IMPORTANT]
> Może upłynie do ośmiu dni, aż elementy zagregowane pojawią się pod nagłówkiem klasyfikatorów przeszkolnych.

3. Wybierz przeszkoliwny klasyfikator użyty w zasadach automatycznego stosowania etykiet przechowywania. Jest to przeszkolny klasyfikator, na temat który chcesz przekazać opinię.

> [!NOTE]
> Jeśli element zawiera wpis w kolumnie **Etykieta** przechowywania, oznacza to, że element został sklasyfikowany jako .`match`  Jeśli element nie ma wpisu w kolumnie Etykieta przechowywania,  oznacza to, że został sklasyfikowany jako .`close match` Możesz ulepszyć dokładność klasyfikatora, podając opinie na temat `close match` elementów. 

4. Wybierz element i otwórz go.
 
 > [!TIP]
> Możesz przekazać opinię na temat wielu elementów jednocześnie, wybierając je wszystkie, a następnie wybierając **pozycję Popraw klasyfikację** na pasku poleceń.

5. Wybierz pozycję **Podaj opinię**.
6. Jeśli element **jest** naprawdę dodatni, w okienku Szczegółowa opinia wybierz pozycję **Dopasuj**.  Jeśli element jest fałszywie dodatni, czyli został nieprawidłowo uwzględniony w kategorii, wybierz pozycję **Nie dopasowano**.
7. Jeśli istnieje inny klasyfikator, który będzie bardziej odpowiedni dla elementu, możesz wybrać go z listy Zaproponuj **innych klasyfikatorów** przeszkolnych. Spowoduje to wyzwolenie innego specyfikatora do oceny elementu.
8. Wybierz **pozycję Wyślij opinię** , aby wysłać ocenę `match`klasyfikacji , `not a match` i zaproponować innych przeszkolnych klasyfikatorów. Po podaniem 30 wystąpień opinii dla klasyfikatora zostanie on automatycznie ponownie przeszkoliny. Ponowne przeszkolenie może trwać od jednej do czterech godzin. Klasyfikatory mogą być przeszkolone tylko dwa razy dziennie.

> [!IMPORTANT]
> Te informacje są przekierowywczane do klasyfikatora w Twojej dzierżawie, **ale nie są powrót do firmy Microsoft**.

9. Otwórz **klasyfikatorów typu Trainable**.
10. Klasyfikator użyty w zasadach zgodności komunikacji zostanie wyświetlony pod **nagłówkiem Ponowne szkolenie** .

![klasyfikator w stanie ponownego treningu.](../media/classifier-retraining.png)

11. Po zakończeniu ponownego szkolenia wybierz klasyfikatora, aby otworzyć omówienie ponownego szkolenia.

![Omówienie wyników ponownego szkolenia klasyfikatora.](../media/classifier-retraining-overview.png)

12. Przejrzyj zalecane działanie i porównania przewidywań przeszkolonych i obecnie opublikowanych wersji specyfikatora.
13. Jeśli wyniki ponownego szkolenia są zadowałe, wybierz pozycję **Opublikuj ponownie**.
14. Jeśli nie podoba Ci się wynik ponownego treningu, możesz przekazać dodatkową opinię klasyfikatorowi w interfejsie Eksploratora zawartości i rozpocząć kolejny cykl ponownego treningu lub nic nie robić — w takim przypadku obecnie opublikowana wersja klasyfikatora nadal będzie używana. 

## <a name="details-on-republishing-recommendations"></a>Szczegółowe informacje na temat zaleceń dotyczących ponownego rozpowszechniania

Oto nieco informacji na temat formułowania zalecenia dotyczącego ponownego publikowania przeszkolonego klasyfikatora lub zaproponowania dalszego ponownego treningu. Wymaga to nieco lepszego zrozumienia sposobu pracy klasyfikatorów, które można przeszkolić.

Po zakończeniu ponownego szkolenia oceniamy wydajność klasyfikatora zarówno w przypadku elementów z opinią, jak i wszystkich elementów pierwotnie używanych do przeszkolenia klasyfikatora. 

- W przypadku wbudowanych modeli elementy służące do przeszkolinia klasyfikatora to elementy używane przez firmę Microsoft do tworzenia modelu.
- W przypadku modeli niestandardowych elementy używane w pierwotnym szkoleniu klasyfikatora są z witryn dodanych do testowania i przeglądania.

Porównujemy numery wydajności obu zestawów elementów dla przeszkolonego i opublikowanego klasyfikatora, aby udzielić zalecenia dotyczącego tego, czy istnieje ulepszenie w celu ponownego opublikowania. 

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o przeszkolnych klasyfikatorach](classifier-learn-about.md)
- [Domyślne rozszerzenia nazw plików przeszukanych i typy plików analizowanych w programie SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)