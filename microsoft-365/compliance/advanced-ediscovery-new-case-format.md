---
title: Nowy format liter w programie Advanced eDiscovery
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
description: Nowy format przypadków można stosować w programie Advanced eDiscovery, aby można było przeglądać zestawy i korzystać z innych podwyższonych limitów oraz nowych funkcji.
ms.openlocfilehash: 9b0e87e7d24565bb89444fe5b1e5cbf43d915e42
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2021
ms.locfileid: "63007492"
---
# <a name="use-the-new-case-format-in-advanced-ediscovery"></a>Nowy format liter w programie Advanced eDiscovery

Więcej organizacji korzysta z Advanced eDiscovery w programie Microsoft 365 w krytycznych procesach zbierania elektronicznych materiałów dowodowych. Obejmuje to odpowiadanie na żądania prawne, dochodzenia i procesy. Wraz ze Advanced eDiscovery coraz częstym wymaganiem klienta jest rozszerzenie całkowitej ilości zawartości, która może być zarządzana w jednym przypadku Advanced eDiscovery przypadku. Aby uwzględnić znaczące wzrosty wielkości liter zarówno w przypadku całkowitego obrotu danych, jak i łącznej liczby elementów, możesz teraz wybrać nowy format wielkości liter podczas tworzenia Advanced eDiscovery przypadku.  

## <a name="create-a-case"></a>Tworzenie sprawy

Aby utworzyć nową Advanced eDiscovery sprawy przy użyciu nowego formatu sprawy:

1. Przejdź do i <https://compliance.microsoft.com> zaloguj się.

2. W okienku nawigacji po lewej stronie okna Centrum zgodności platformy Microsoft 365 pozycję **zbierania elektronicznych materiałów** dowodowych > zaawansowane.

3. Na stronie **Advanced eDiscovery** kliknij kartę **Sprawy**, a następnie kliknij pozycję **Utwórz sprawę**.

   Zostanie **wyświetlona strona wysuwana** Nowa sprawa zbierania elektronicznych materiałów dowodowych. Sekcja **Format sprawy** udostępnia opcję utworzenia sprawy przy użyciu nowego formatu.

   ![Opcja nowego formatu sprawy na stronie Nowa sprawa zbierania elektronicznych materiałów dowodowych.](..\media\AeDNewCaseFormat1.png)

4. Po nazewnictwie sprawy wybierz opcję **Nowy** , a następnie kliknij przycisk **Zapisz** , aby utworzyć sprawę przy użyciu nowego formatu.

## <a name="benefits-of-the-new-case-format"></a>Zalety nowego formatu sprawy

Nowy format sprawy umożliwia zarządzanie sprawami, które zawierają ponad 40 milionów elementów. Ta funkcja ułatwia efektywne zarządzanie dużymi ilościami danych sprawy w całym przepływie pracy zbierania elektronicznych materiałów dowodowych.

Oto lista innych korzyści związanych z dużymi sprawami w Advanced eDiscovery przepływu pracy.

- **Kolekcja**: W nowym formacie sprawy możesz zebrać maksymalnie 1 TB danych dla jednej kolekcji.

   W przypadku poszczególnych przypadków ustawienia kolekcji będą domyślnie gromadzić załączniki w chmurze oraz załączniki i zawartość Teams i Yammer kontekstowe. Te ustawienia ułatwiają zbieranie pełnego obrazu komunikacji cyfrowej w ramach badania. W przypadku konwersacji kontekstowych Teams i Yammer nowy format sprawy konwertuje migawki czasu (1:1, 1: N i Channel) na transkrypcje HTML, aby zapewnić kontekst konwersacji i zmniejszyć łączną liczbę elementów powiązanych przez zawartość opartą na czacie.  

- **Recenzja**: Każdy zestaw recenzji będzie obsługiwać do 1 TB zawartości przed rozszerzeniami. Dla filtrów i zapytań będą dostępne dodatkowe metadane, w tym nazwa zespołu, nazwa kanału i nazwa konwersacji dla Teams zawartości. Każda transkrypcja będzie zawierać zawartość opartą na czasie dla elementu przed i po nim. W przypadku konwersacji w kanale będzie zbierany wpis główny i wszystkie odpowiedzi na zawartość reakcji. Aby uzyskać więcej informacji, [Advanced eDiscovery przepływu pracy dla zawartości w programie Microsoft Teams (wersja zapoznawcza)](teams-workflow-in-advanced-ediscovery.md)

- **Eksportowanie**: Możesz eksportować duże zestawy zawartości w jednym zadaniu eksportowania. Nowy format sprawy umożliwia wyeksportowanie 5 milionów dokumentów lub 500 GB, w zależności od tego, co jest mniejsze w zadaniu eksportu.

Ponadto nowy format wielkości liter zawiera zaktualizowany interfejs użytkownika, w którym jest wyświetlany całkowity rozmiar każdego zestawu recenzji w tym przypadku. Rozmiary zestawów recenzji są wyświetlane w kolumnie na **karcie Zestawy** recenzji.

![Statystyki zestawu nowych recenzji Advanced eDiscovery interfejsie użytkownika.](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Jeśli spróbuję zebrać w jednej kolekcji ponad 1 TB danych, to będzie działać?**

W niektórych przypadkach wydajność będzie mieć negatywny wpływ i może spowodować niestabilność.

**Jeśli załączniki w chmurze są domyślnie uwzględniane w formacie dużych liter; jak usunąć zawartość z przeglądania?**  

Użyj filtrów zestawu recenzji, aby filtrować według rodzaju wiadomości lub wykluczyć załączniki w chmurze przy użyciu filtru HasAttachment. Aby uzyskać więcej informacji, zobacz [Wykonywanie zapytań i filtrowanie zawartości w zestawie recenzji](review-set-search.md).

**Czy podczas eksportowania transkrypcji konwersacji czatu plik ładowania będzie zawierał wszystkie rozwinięte metadane i jeden element dla każdego transkrypcji?**

Wszystkie metadane konwersacji są osadzone w pliku transkrypcji HTML.  W pliku ładowania jest dostępnych wiele pól wspólnych. Aby uzyskać więcej informacji na temat wyeksportowanych metadanych, zobacz [Pola metadanych dokumentu Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).
