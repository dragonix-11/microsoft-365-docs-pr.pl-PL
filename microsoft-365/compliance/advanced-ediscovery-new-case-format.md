---
title: Nowy format przypadku w funkcji zbierania elektronicznych materiałów dowodowych (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: ninachen
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Użyj nowego formatu przypadku zbierania elektronicznych materiałów dowodowych (Premium), aby dodać więcej elementów do przeglądania zestawów i korzystać z innych zwiększonych limitów i nowych funkcji.
ms.openlocfilehash: 6c3e9f86cac5424ae9d9610a9c715c2f86563f64
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993562"
---
# <a name="use-the-new-case-format-in-ediscovery-premium"></a>Użyj nowego formatu przypadku w funkcji zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Więcej organizacji korzysta z rozwiązania zbierania elektronicznych materiałów dowodowych (Premium) w usłudze Microsoft Purview na potrzeby krytycznych procesów zbierania elektronicznych materiałów dowodowych. Obejmuje to odpowiadanie na żądania regulacyjne, dochodzenia i spory sądowe. W miarę wzrostu użycia zbierania elektronicznych materiałów dowodowych (Premium) typowym wymaganiem klienta jest zwiększenie łącznej ilości zawartości, którą można zarządzać w jednym przypadku zbierania elektronicznych materiałów dowodowych (Premium). Aby ułatwić uwzględnienie znacznego wzrostu rozmiaru przypadku, zarówno w przypadku całkowitego woluminu danych, jak i całkowitej liczby elementów, możesz teraz wybrać nowy format przypadku podczas tworzenia sprawy zbierania elektronicznych materiałów dowodowych (Premium).  

## <a name="create-a-case"></a>Tworzenie sprawy

Aby utworzyć przypadek zbierania elektronicznych materiałów dowodowych (Premium) przy użyciu nowego formatu przypadku:

1. Przejdź do i <https://compliance.microsoft.com> zaloguj się.

2. W okienku nawigacji po lewej stronie portalu zgodności usługi Microsoft Purview kliknij pozycję **eDiscovery > Advanced**.

3. Na stronie **eDiscovery (Premium)** kliknij kartę **Przypadki**, a następnie kliknij **pozycję Utwórz przypadek**.

   Zostanie wyświetlona strona Wysuwane **nowe przypadki zbierania elektronicznych** materiałów dowodowych. Sekcja **Format przypadku** zawiera opcję utworzenia sprawy przy użyciu nowego formatu.

   ![Nowa opcja formatu przypadku na stronie Nowy przypadek zbierania elektronicznych materiałów dowodowych.](..\media\AeDNewCaseFormat1.png)

4. Po nazewnictwie sprawy wybierz opcję **Nowy** , a następnie kliknij przycisk **Zapisz** , aby utworzyć przypadek przy użyciu nowego formatu.

## <a name="benefits-of-the-new-case-format"></a>Zalety nowego formatu przypadku

Nowy format przypadku umożliwia zarządzanie przypadkami zawierającymi ponad 40 milionów elementów. Ta funkcja ułatwia efektywne zarządzanie dużymi ilościami danych przypadków za pośrednictwem całego przepływu pracy zbierania elektronicznych materiałów dowodowych.

Oto lista innych korzyści z dużych przypadków w przepływie pracy zbierania elektronicznych materiałów dowodowych (Premium).

- **Kolekcja**: w nowym formacie przypadku można zebrać maksymalnie 1 TB danych dla jednej kolekcji.

   W każdym przypadku ustawienia kolekcji domyślnie będą zbierać załączniki w chmurze oraz kontekstowe Teams i zawartość Yammer. Te ustawienia pomagają zebrać pełny obraz komunikacji cyfrowej w ramach badania. W przypadku konwersacji kontekstowych Teams i Yammer nowy format przypadku konwertuje migawki oparte na czasie 1:1, 1: N i Konwersacje kanału na transkrypcje HTML, aby ułatwić zapewnienie kontekstu konwersacji i zmniejszenie całkowitej liczby elementów generowanych przez zawartość opartą na czatach.  

- **Przegląd**: Każdy zestaw przeglądów będzie obsługiwać do 1 TB zawartości przed rozszerzeniem. Dodatkowe metadane będą dostępne dla filtrów i zapytań, w tym nazwy zespołu, nazwy kanału i nazwy konwersacji dla zawartości Teams. Każda transkrypcja będzie zawierać zawartość opartą na czasie dla elementu odpowiadającego przed i po nim. W przypadku konwersacji w kanale wpis główny i wszystkie odpowiedzi zostaną zebrane w celu odpowiadania zawartości. Aby uzyskać więcej informacji, zobacz [przepływ pracy zbierania elektronicznych materiałów dowodowych (Premium) dla zawartości w Microsoft Teams (wersja zapoznawcza)](teams-workflow-in-advanced-ediscovery.md)

- **Eksportowanie**: duże zestawy zawartości można eksportować w jednym zadaniu eksportowania. Nowy format przypadku umożliwia eksportowanie 5 milionów dokumentów lub 500 GB, w zależności od tego, która z tych wartości jest mniejsza w zadaniu eksportu.

Ponadto nowy format przypadku zawiera zaktualizowany interfejs użytkownika, który wyświetla całkowity rozmiar każdego zestawu przeglądów w tym przypadku. Rozmiary zestawów przeglądów są wyświetlane w kolumnie na karcie **Zestawy przeglądów** .

![Nowe statystyki zestawu przeglądów w interfejsie użytkownika zbierania elektronicznych materiałów dowodowych (Premium).](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Czy próba zebrania ponad 1 TB w jednej kolekcji będzie działać?**

Wydajność będzie mieć negatywny wpływ i może spowodować niestabilność w niektórych przypadkach.

**Jeśli załączniki w chmurze są domyślnie uwzględniane w dużym formacie wielkości liter; jak mogę usunąć tę zawartość z mojego środowiska przeglądu?**  

Filtry zestawu przeglądów umożliwiają filtrowanie według rodzaju komunikatu lub wykluczanie załączników w chmurze przy użyciu filtru HasAttachment. Aby uzyskać więcej informacji, zobacz [Wykonywanie zapytań i filtrowanie zawartości w zestawie przeglądów](review-set-search.md).

**Czy podczas eksportowania transkrypcji konwersacji czatu plik ładowania będzie zawierać wszystkie rozwinięte metadane i pojedynczy element dla każdej transkrypcji?**

Wszystkie metadane konwersacji są osadzone w pliku transkrypcji HTML.  Wiele typowych pól jest dostępnych w pliku ładowania. Aby uzyskać więcej informacji na temat wyeksportowanych metadanych, zobacz [Document metadata fields in eDiscovery (Premium) (Pola metadanych dokumentu w dziedzinie zbierania elektronicznych materiałów dowodowych (Premium)](document-metadata-fields-in-Advanced-eDiscovery.md)).
