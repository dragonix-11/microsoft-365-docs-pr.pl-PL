---
title: Jak ponownie wytrenować klasyfikator w eksploratorze zawartości
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
description: Dowiedz się, jak przekazać opinię klasyfikatorowi trenowalnemu w Eksploratorze zawartości.
ms.openlocfilehash: bde570b8bbb104d7f89523eb12bd8b9ac9210ad7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637444"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Jak ponownie wytrenować klasyfikator w eksploratorze zawartości

Klasyfikator trenowalny platformy Microsoft 365 to narzędzie, które można wytrenować w celu rozpoznawania różnych typów zawartości, udostępniając przykłady do obejrzenia. Po wytrenowaniu można go używać do identyfikowania elementów do stosowania etykiet poufności pakietu Office, zasad zgodności komunikacji i zasad etykiet przechowywania.

W tym artykule pokazano, jak zwiększyć wydajność niestandardowych klasyfikatorów z możliwością trenowania, przekazując im dodatkową opinię.

Aby dowiedzieć się więcej na temat różnych typów klasyfikatorów, zobacz [Learn about trainable classifiers (Dowiedz się więcej o klasyfikatorach z możliwością trenowania](classifier-learn-about.md)).

Obejrzyj to wideo, aby zapoznać się z krótkim podsumowaniem procesu dostrajania i ponownego trenowania. Aby uzyskać szczegółowe informacje, nadal musisz przeczytać ten pełny artykuł.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGMs]

> [!NOTE]
> Nie można ponownie wytrenować wstępnie wytrenowanych klasyfikatorów.

## <a name="permissions"></a>Uprawnienia

Aby uzyskać dostęp do klasyfikatorów w portal zgodności Microsoft Purview:

- rola administratora zgodności lub administrator danych zgodności jest wymagana do szkolenia klasyfikatora

Konta z tymi uprawnieniami będą potrzebne do używania klasyfikatorów w następujących scenariuszach:

- Scenariusz zasad przechowywania etykiet: Role zarządzania rekordami i zarządzania przechowywaniem 

## <a name="overall-workflow"></a>Ogólny przepływ pracy

> [!IMPORTANT]
> W Eksploratorze zawartości możesz przekazać opinię dotyczącą zasad automatycznego stosowania etykiet przechowywania do elementów programu Exchange i używać klasyfikatora jako warunku. **Jeśli nie masz zasad przechowywania, które automatycznie stosują etykietę przechowywania do elementów programu Exchange i używają klasyfikatora jako warunku, zatrzymaj się tutaj.**

Podczas korzystania z klasyfikatorów warto zwiększyć precyzję klasyfikacji, które tworzą. Można to zrobić, oceniając jakość klasyfikacji wykonanych dla elementów, które określił jako zgodne lub niezgodne. Po dokonaniu 30 ocen klasyfikatora przyjmuje tę opinię i automatycznie ponownie się trenuje.

Aby dowiedzieć się więcej na temat ogólnego przepływu pracy ponownego trenowania klasyfikatora, zobacz [Przepływ procesu ponownego trenowania klasyfikatora](classifier-learn-about.md#retraining-classifiers).

> [!NOTE]
> Klasyfikator musi być już opublikowany i używany, zanim będzie można go ponownie wytrenować.

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Jak ponownie wytrenować klasyfikator w eksploratorze zawartości

1. Zaloguj się do portal zgodności Microsoft Purview z dostępem administratora zgodności lub administratora zabezpieczeń i otwórz **Eksploratora zawartości** **klasyfikacji** >  **portal zgodności Microsoft Purview** >  Data. 
2. Na liście **Filtruj etykiety, typy informacji lub kategorie** rozwiń węzeł **Klasyfikatory trainable**.

> [!IMPORTANT]
> Może upłynąć do ośmiu dni, aż zagregowane elementy pojawią się pod nagłówkiem klasyfikatorów klasyfikujących możliwość trenowania.

3. Wybierz klasyfikator trenowalny użyty w zasadach automatycznego stosowania etykiet przechowywania. Jest to klasyfikator trenowalny, na który przekażesz opinię.

> [!NOTE]
> Jeśli element ma wpis w kolumnie **Etykieta przechowywania** , oznacza to, że element został sklasyfikowany jako `match`.  Jeśli element nie ma wpisu w kolumnie **Etykieta przechowywania** , oznacza to, że został sklasyfikowany jako `close match`. Precyzję klasyfikatora można zwiększyć najbardziej, przekazując opinie na `close match` temat elementów. 

4. Wybierz element i otwórz go.
 
 > [!TIP]
> Możesz przekazać opinię na temat wielu elementów jednocześnie, wybierając je wszystkie, a następnie wybierając pozycję **Ulepsz klasyfikację** na pasku poleceń.

5. Wybierz **pozycję Przekaż opinię**.
6. Jeśli element jest prawdziwie pozytywny, w okienku **Szczegółowe opinie** wybierz pozycję **Dopasuj**.  Jeśli element jest fałszywie dodatni, to jest niepoprawnie uwzględniony w kategorii, wybierz **pozycję Nie dopasuj**.
7. Jeśli istnieje inny klasyfikator, który byłby bardziej odpowiedni dla elementu, możesz wybrać go z listy **Sugerowanie innych klasyfikatorów z możliwością trenowania** . Spowoduje to wyzwolenie innego klasyfikatora w celu oceny elementu.
8. Wybierz pozycję **Wyślij opinię** , aby wysłać ocenę `match`klasyfikacji , `not a match` i zasugeruj inne klasyfikatory z możliwością trenowania. Po przekazaniu klasyfikatorowi 30 wystąpień opinii zostanie automatycznie ponownie wytrenowany. Ponowne trenowanie może potrwać od jednej do czterech godzin. Klasyfikatory można ponownie trenować tylko dwa razy dziennie.

> [!IMPORTANT]
> Te informacje trafiają do klasyfikatora w dzierżawie, **ale nie wracają do firmy Microsoft**.

9. Otwórz **klasyfikatory trainable**.
10. Klasyfikator użyty w zasadach zgodności usługi Communications zostanie wyświetlony w nagłówku **Ponowne trenowanie** .

![klasyfikatora w stanie ponownego trenowania.](../media/classifier-retraining.png)

11. Po zakończeniu ponownego trenowania wybierz klasyfikator, aby otworzyć przegląd ponownego trenowania.

![omówienie wyników ponownego trenowania klasyfikatora.](../media/classifier-retraining-overview.png)

12. Przejrzyj zalecaną akcję i porównania przewidywania ponownie wytrenowanych i aktualnie opublikowanych wersji klasyfikatora.
13. Jeśli wyniki ponownego trenowania są zadowalające, wybierz pozycję **Opublikuj ponownie**.
14. Jeśli wyniki ponownego trenowania nie są zadowalające, możesz przekazać dodatkową opinię klasyfikatorowi w interfejsie Eksploratora zawartości i rozpocząć kolejny cykl ponownego trenowania lub nie wykonywać żadnych czynności w takim przypadku, gdy obecnie opublikowana wersja klasyfikatora będzie nadal używana. 

## <a name="details-on-republishing-recommendations"></a>Szczegóły dotyczące ponownego publikowania zaleceń

Poniżej przedstawiono niewiele informacji na temat sposobu formułowania zalecenia dotyczącego ponownego opublikowania ponownie wytrenowanego klasyfikatora lub zasugerowania dalszego ponownego trenowania. Wymaga to nieco dokładniejszego zrozumienia sposobu działania klasyfikatorów z możliwością trenowania.

Po ponownym trenowaniu oceniamy wydajność klasyfikatora zarówno dla elementów z opinią, jak i wszystkich elementów pierwotnie używanych do trenowania klasyfikatora. 

- W przypadku modeli wbudowanych elementy używane do trenowania klasyfikatora są elementami używanymi przez firmę Microsoft do kompilowania modelu.
- W przypadku modeli niestandardowych elementy używane w oryginalnym trenowaniu klasyfikator pochodzą z witryn dodanych do testowania i przeglądania.

Porównujemy numery wydajności dla obu zestawów elementów dla ponownie wytrenowanego i opublikowanego klasyfikatora, aby przedstawić zalecenie dotyczące tego, czy nastąpiła poprawa w celu ponownego opublikowania. 

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o klasyfikatorach z możliwością szkolenia](classifier-learn-about.md)
- [Domyślne rozszerzenia nazw plików przeszukanych i analizowane typy plików w programie SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
