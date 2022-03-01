---
title: Używanie edytora KQL do tworzenia zapytań wyszukiwania
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
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
description: Za pomocą edytora KQL można skonfigurować zapytania wyszukiwania zbierania elektronicznych materiałów dowodowych w przeszukiwaniu zawartości, podstawowym zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery.
ms.openlocfilehash: 6c553a20116eba478961b606f30fa7af8c4c322e
ms.sourcegitcommit: 6b24f65c987e5ca06e6d5f4fc10804cdbe68b034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996402"
---
# <a name="use-the-kql-editor-to-build-search-queries"></a>Używanie edytora KQL do tworzenia zapytań wyszukiwania

Nowe środowisko zapytań KQL w narzędziach zbierania elektronicznych materiałów dowodowych w programie Microsoft 365 udostępnia opinie i wskazówki podczas tworzenia zapytań wyszukiwania w przeszukiwaniu zawartości, podstawowych usługach zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery. Podczas wpisywania zapytań w edytorze udostępnia on autouzupełnianie obsługiwanych właściwości i warunków, które można wyszukiwać, oraz udostępnia listy obsługiwanych wartości dla standardowych właściwości i warunków. Jeśli na przykład określisz właściwość `kind` poczty e-mail w zapytaniu, edytor przedstawi listę obsługiwanych wartości, które można wybrać. Edytor KQL wyświetla również w czasie rzeczywistym potencjalne błędy zapytań, które można naprawić przed uruchomieniem wyszukiwania. Co więcej, można wklejać złożone zapytania bezpośrednio do edytora bez konieczności ręcznego tworzenia zapytań przy użyciu słów kluczowych i kart warunków w konstruktorze warunków standardowych.
  
Oto najważniejsze korzyści z używania edytora KQL:

- Zapewnia wskazówki i pomaga tworzyć zapytania wyszukiwania od podstaw.

- Umożliwia szybkie wklejenie długich i złożonych zapytań bezpośrednio do edytora. Jeśli na przykład otrzymasz złożone zapytanie od przeciwstawnych porad, możesz wkleić je do edytora KQL, zamiast korzystać z konstruktora warunków.

- Umożliwia szybkie identyfikowanie potencjalnych błędów i wyświetlanie wskazówek dotyczących rozwiązywania problemów.

Edytor KQL jest również dostępny w przypadku tworzenia na podstawie zapytań blokady w podstawowych zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery.

## <a name="displaying-the-kql-editor"></a>Wyświetlanie edytora KQL

Podczas tworzenia lub edytowania wyszukiwania zbierania elektronicznych materiałów dowodowych opcja wyświetlania i używania edytora KQL znajduje się na  stronie Warunki w kreatorze wyszukiwania lub kolekcji.

### <a name="kql-editor-in-content-search-and-core-ediscovery"></a>Edytor KQL w wyszukiwaniu zawartości i podstawowym zbierania elektronicznych materiałów dowodowych

![Edytor KQL w wyszukiwaniu zawartości i podstawowym zbierania elektronicznych materiałów dowodowych](../media/KQLEditorCore.png)

### <a name="kql-editor-in-advanced-ediscovery"></a>Edytor KQL w programie Advanced eDiscovery

![Edytor KQL w programie Advanced eDiscovery](../media/KQLEditorAdvanced.png)

## <a name="using-the-kql-editor"></a>Używanie edytora KQL

W poniższych sekcjach popisano przykłady tego, jak edytor KQL udostępnia sugestie i wykrywa potencjalne błędy.

### <a name="autocompletion-of-search-properties-and-operators"></a>Autouzupełnianie właściwości i operatorów wyszukiwania

Po rozpoczęciu wpisywania zapytania wyszukiwania w edytorze KQL jest wyświetlane sugerowane autouzupełnianie obsługiwanych właściwości wyszukiwania (nazywanych również ograniczeniami *właściwości), które* można wybrać. Aby wyświetlić listę obsługiwanych właściwości, które zaczynają się od tych dwóch znaków, należy wpisać co najmniej dwa znaki. Na przykład poniższy zrzut ekranu przedstawia sugerowane właściwości wyszukiwania, które zaczynają się od `Se`.

![Edytor KQL sugeruje obsługiwane właściwości](../media/KQLEditorAutoCompleteProperties.png)

Ponadto po wpisaniu pełnej nazwy właściwości redaktor sugeruje również listę obsługiwanych operatorów ( `:`takich jak , `=` `<>`i ). Poniższy zrzut ekranu przedstawia na przykład sugerowane operatory dla tej `Date` właściwości.

![Edytor KQL sugeruje operatory](../media/KQLEditorOperatorSuggestions.png)

Aby uzyskać więcej informacji na temat obsługiwanych właściwości i operatorów wyszukiwania, zobacz Zapytania słów kluczowych i [warunki wyszukiwania dotyczące zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

### <a name="property-value-suggestions"></a>Sugestie wartości właściwości

Edytor KQL udostępnia sugestie dotyczące możliwych wartości niektórych właściwości. Poniższy zrzut ekranu przedstawia na przykład sugerowane wartości tej `Kind` właściwości.

![Edytor KQL sugeruje wartości dla niektórych właściwości](../media/KQLEditorValueSuggestions.png)

Edytor sugeruje również listę użytkowników (w formacie UPN) po wpisaniu właściwości adresata wiadomości e-mail, `From`takich jak , `To`i `Recipients` `Participants`.

![Edytor KQL sugeruje użytkowników we właściwościach poczty e-mail adresata](../media/KQLEditorRecipientSuggestions.png)

### <a name="detection-of-potential-errors"></a>Wykrywanie potencjalnych błędów

Edytor KQL wykrywa potencjalne błędy w zapytaniach wyszukiwania i podpowiada, co jest przyczyną tego błędu, co pomaga w jego rozwiązaniu. Edytor wskazuje również potencjalny błąd, gdy właściwość nie ma odpowiadającej jej operacji lub wartości. Potencjalne błędy w zapytaniu są wyróżniane kolorem czerwonym, a objaśnienia i możliwe rozwiązania tego błędu są wyświetlane w sekcji **rozwijanej** Potencjalne błędy. Jeśli na przykład wklejasz poniższe zapytanie do edytora KQL, zostaną wykryte cztery potencjalne błędy.

![Wykrywanie błędów edytora KQL](../media/KQLEditorErrorDetection.png)

W takim przypadku możesz użyć potencjalnych wskazówek dotyczących błędów, aby rozwiązać problem i rozwiązać problem z zapytaniem.

## <a name="more-information"></a>Więcej informacji

- Możesz przełączać się między konstruktorem warunków a edytorem KQL. Jeśli na przykład użyjesz konstruktora warunków do skonfigurowania zapytania za pomocą pola Słowa kluczowe i wielu kart warunków, wynikowe zapytanie możesz wyświetlić w edytorze KQL. Jeśli jednak utworzysz zapytanie złożone (ze słowami kluczowymi i warunkami) w edytorze KQL, wynikowe zapytanie będzie wyświetlane tylko w polu Słowa kluczowe podczas wyświetlania go w konstruktorze warunków.

- Po wklejeniu złożonego zapytania do edytora KQL redaktor wykrywa potencjalne błędy i sugeruje możliwe rozwiązania w celu usunięcia błędów.
