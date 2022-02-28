---
title: Wyświetlanie podglądu wyników wyszukiwania zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Wyświetl podgląd przykładowych wyników zwróconych przez wyszukiwanie zawartości lub podstawowe wyszukiwanie zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365.
ms.openlocfilehash: af0811d0c442d6f064fd336d4261d1f7b2337dc8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985104"
---
# <a name="preview-ediscovery-search-results"></a>Podgląd wyników wyszukiwania zbierania elektronicznych materiałów dowodowych

Po uruchomieniu wyszukiwania zawartości lub wyszukiwania skojarzonego ze sprawą Core eDiscovery możesz wyświetlić podgląd przykładowych wyników zwróconych przez wyszukiwanie. Wyświetlanie podglądu elementów zwróconych przez zapytanie wyszukiwania pomaga ustalić, czy wyszukiwanie zwraca spodziewane wyniki, czy też musisz zmienić zapytanie wyszukiwania i ponownie uruchomić wyszukiwanie.

Aby wyświetlić podgląd przykładowych wyników wyszukiwania:

1. W Centrum zgodności platformy Microsoft 365 przejdź do strony Przeszukiwanie zawartości lub Podstawowej sprawy zbierania elektronicznych materiałów dowodowych.

2. Wybierz pozycję wyszukaj, aby wyświetlić stronę wysuwu.

3. U dołu strony wysuwu kliknij pozycję **Przejrzyj przykład**.

   ![Kliknij pozycję Przejrzyj przykład na wysuwana stronie, aby wyświetlić podgląd wyników.](../media/PreviewSearchResults1.png)

   Zostanie wyświetlona strona zawierająca przykładowe wyniki wyszukiwania.

4. Zaznacz element, aby wyświetlić jego zawartość w okienku odczytu.

   ![Wyświetlanie podglądu elementów w okienku odczytu.](../media/PreviewSearchResults2.png)

   Na poprzednim zrzucie ekranu zwróć uwagę, że słowa kluczowe z zapytania wyszukiwania są wyróżniane podczas wyświetlania podglądu elementów.

## <a name="how-the-search-result-samples-are-selected"></a>Jak wybrano przykłady wyników wyszukiwania

Aby wyświetlić podgląd, dostępnych jest maksymalnie 1000 losowo wybranych elementów. Oprócz losowego wyboru elementy dostępne do podglądu muszą również spełniać następujące kryteria:

- Można wyświetlić podgląd maksymalnie 100 elementów z jednej lokalizacji zawartości (skrzynki pocztowej lub witryny). Oznacza to, że do podglądu może być dostępnych mniej niż 1000 elementów. Jeśli na przykład podczas przeszukiwania czterech skrzynek pocztowych zostanie zwracanych 1500 szacowanych elementów, do podglądu będzie dostępnych tylko 400 elementów, ponieważ można wyświetlić podgląd tylko 100 elementów z każdej skrzynki pocztowej.

- W przypadku elementów skrzynki pocztowej podgląd jest dostępny tylko w przypadku wiadomości e-mail. Nie można wyświetlić podglądu elementów, takich jak zadania, elementy kalendarza i kontakty.

- W przypadku elementów witryny do podglądu są dostępne tylko dokumenty. Nie można wyświetlić podglądu elementów, takich jak foldery, listy lub załączniki listy.

## <a name="file-types-supported-when-previewing-search-results"></a>Typy plików obsługiwane podczas wyświetlania podglądu wyników wyszukiwania

W okienku podglądu można wyświetlać podgląd obsługiwanych typów plików. Jeśli typ pliku nie jest obsługiwany, musisz pobrać kopię pliku na komputer lokalny (klikając pozycję **Pobierz oryginalny element**). W przypadku stron sieci Web aspx adres URL strony jest uwzględniany, ale możesz nie mieć uprawnień dostępu do tej strony. Elementy nieindeksowane nie są dostępne do wyświetlania podglądu.

Następujące typy plików są obsługiwane i można wyświetlać ich podgląd w okienku wyników wyszukiwania.
  
- .txt, .html, mhtml

- eml

- .doc, .docx, docm

- pptm, .pptx

- .pdf

Obsługiwane są również następujące typy kontenerów plików. W okienku podglądu można wyświetlić listę plików w kontenerze.
  
- .zip

- gzip