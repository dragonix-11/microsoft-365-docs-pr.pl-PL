---
title: Podgląd wyników wyszukiwania zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Wyświetl podgląd przykładu wyników zwróconych przez wyszukiwanie zawartości lub wyszukiwanie zbierania elektronicznych materiałów dowodowych (Standard) w portal zgodności Microsoft Purview.
ms.openlocfilehash: f369148c6f898c4150d0c86f898640f71ab367a0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628600"
---
# <a name="preview-ediscovery-search-results"></a>Eksportowanie wyników wyszukiwania w ramach zbierania elektronicznych materiałów dowodowych

Po uruchomieniu wyszukiwania zawartości lub wyszukiwania skojarzonego ze sprawą Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Standardowa) możesz wyświetlić podgląd przykładu wyników zwróconych przez wyszukiwanie. Podgląd elementów zwracanych przez zapytanie wyszukiwania może pomóc w określeniu, czy wyszukiwanie zwraca wyniki, których oczekujesz, lub jeśli chcesz zmienić zapytanie wyszukiwania i ponownie uruchomić wyszukiwanie.

Aby wyświetlić podgląd przykładu wyników zwróconych przez wyszukiwanie:

1. W portal zgodności Microsoft Purview przejdź do strony wyszukiwania zawartości lub zgłoszenia zbierania elektronicznych materiałów dowodowych (Standardowa).

2. Wybierz pozycję Wyszukaj, aby wyświetlić stronę wysuwaną.

3. W dolnej części strony wysuwanej kliknij pozycję **Przejrzyj przykład**.

   ![Kliknij pozycję Przejrzyj przykład na stronie wysuwanej, aby wyświetlić podgląd wyników.](../media/PreviewSearchResults1.png)

   Zostanie wyświetlona strona zawierająca przykład wyników wyszukiwania.

4. Wybierz element, aby wyświetlić jego zawartość w okienku odczytu.

   ![Podgląd elementów w okienku odczytu.](../media/PreviewSearchResults2.png)

   Na poprzednim zrzucie ekranu zwróć uwagę, że słowa kluczowe z zapytania wyszukiwania są wyróżnione podczas podglądu elementów.

## <a name="how-the-search-result-samples-are-selected"></a>Wybieranie przykładów wyników wyszukiwania

Do wyświetlenia podglądu jest dostępnych maksymalnie 1000 losowo wybranych elementów. Oprócz losowego wybierania elementy dostępne w wersji zapoznawczej muszą również spełniać następujące kryteria:

- Można wyświetlić podgląd maksymalnie 100 elementów z jednej lokalizacji zawartości (skrzynki pocztowej lub witryny). Oznacza to, że może być dostępnych mniej niż 1000 elementów w wersji zapoznawczej. Jeśli na przykład wyszukasz cztery skrzynki pocztowe, a wyszukiwanie zwróci 1500 szacowanych elementów, tylko 400 będzie dostępnych w wersji zapoznawczej, ponieważ można wyświetlić podgląd tylko 100 elementów z każdej skrzynki pocztowej.

- W przypadku elementów skrzynki pocztowej tylko wiadomości e-mail są dostępne w wersji zapoznawczej. Nie można wyświetlić podglądu elementów, takich jak zadania, elementy kalendarza i kontakty.

- W przypadku elementów witryny tylko dokumenty są dostępne w wersji zapoznawczej. Nie można wyświetlić podglądu elementów, takich jak foldery, listy lub załączniki listy.

## <a name="file-types-supported-when-previewing-search-results"></a>Typy plików obsługiwane podczas podglądu wyników wyszukiwania

W okienku podglądu można wyświetlić podgląd obsługiwanych typów plików. Jeśli typ pliku nie jest obsługiwany, musisz pobrać kopię pliku na komputer lokalny (klikając pozycję **Pobierz oryginalny element**). W przypadku stron sieci Web aspx adres URL strony jest uwzględniany, ale możesz nie mieć uprawnień dostępu do strony. Elementy z systemem Unindexed nie są dostępne do podglądu.

Następujące typy plików są obsługiwane i można je wyświetlić w okienku wyników wyszukiwania.
  
- .txt, .html, mhtml

- .eml

- .doc, .docx, docm

- pptm, .pptx

- .pdf

Obsługiwane są również następujące typy kontenerów plików. Listę plików w kontenerze można wyświetlić w okienku podglądu.
  
- .zip

- .gzip