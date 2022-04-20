---
title: Twórz zapytania wyszukiwania za pomocą edytora KQL
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
description: Za pomocą edytora KQL można skonfigurować zapytania wyszukiwania zbierania elektronicznych materiałów dowodowych w obszarze Wyszukiwanie zawartości, zbierania elektronicznych materiałów dowodowych (Standard) i eDiscovery (Premium).
ms.openlocfilehash: f1339b064c736d19bb428f812429cf0620cb3f53
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949966"
---
# <a name="use-the-kql-editor-to-build-search-queries"></a>Twórz zapytania wyszukiwania za pomocą edytora KQL

Nowe środowisko zapytań KQL w wyszukiwaniu narzędzi do zbierania elektronicznych materiałów dowodowych Microsoft 365 udostępnia opinie i wskazówki podczas tworzenia zapytań wyszukiwania w obszarze Wyszukiwanie zawartości, Microsoft Purview eDiscovery (Standard) i eDiscovery (Premium). Wpisywanie zapytań w edytorze zapewnia automatyczne uzupełnianie obsługiwanych właściwości i warunków z możliwością wyszukiwania oraz zawiera listy obsługiwanych wartości standardowych właściwości i warunków. Jeśli na przykład określisz właściwość `kind` poczty e-mail w zapytaniu, edytor wyświetli listę obsługiwanych wartości, które można wybrać. Edytor KQL wyświetla również potencjalne błędy zapytań w czasie rzeczywistym, które można naprawić przed uruchomieniem wyszukiwania. Najlepiej jest wkleić złożone zapytania bezpośrednio do edytora bez konieczności ręcznego tworzenia zapytań przy użyciu kart słów kluczowych i warunków w konstruktorze warunków standardowych.
  
Poniżej przedstawiono najważniejsze zalety korzystania z edytora KQL:

- Zawiera wskazówki i ułatwia tworzenie zapytań wyszukiwania od podstaw.

- Umożliwia szybkie wklejanie długich, złożonych zapytań bezpośrednio do edytora. Jeśli na przykład otrzymasz złożone zapytanie od przeciwnego doradcy, możesz wkleić je do edytora KQL zamiast używać konstruktora warunków.

- Szybko identyfikuje potencjalne błędy i wyświetla wskazówki dotyczące sposobu rozwiązywania problemów.

Edytor KQL jest również dostępny podczas tworzenia blokad opartych na zapytaniach w systemach eDiscovery (Standard) i eDiscovery (Premium).

## <a name="displaying-the-kql-editor"></a>Wyświetlanie edytora KQL

Podczas tworzenia lub edytowania wyszukiwania zbierania elektronicznych materiałów dowodowych opcja wyświetlania i używania edytora KQL znajduje się na stronie **Warunki** w kreatorze wyszukiwania lub kolekcji.

### <a name="kql-editor-in-content-search-and-ediscovery-standard"></a>edytor KQL w funkcji wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych (standardowa)

![edytor KQL w funkcji wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych (standardowa)](../media/KQLEditorCore.png)

### <a name="kql-editor-in-ediscovery-premium"></a>edytor KQL w eDiscovery (Premium)

![edytor KQL w eDiscovery (Premium)](../media/KQLEditorAdvanced.png)

## <a name="using-the-kql-editor"></a>Korzystanie z edytora KQL

W poniższych sekcjach przedstawiono przykłady sposobu, w jaki edytor KQL udostępnia sugestie i wykrywa potencjalne błędy.

### <a name="autocompletion-of-search-properties-and-operators"></a>Automatyczne uzupełnianie właściwości i operatorów wyszukiwania

Po rozpoczęciu wpisywania zapytania wyszukiwania w edytorze KQL edytor wyświetla sugerowane autouzupełnianie obsługiwanych właściwości wyszukiwania (*nazywanych również ograniczeniami właściwości*), które można wybrać. Musisz wpisać co najmniej dwa znaki, aby wyświetlić listę obsługiwanych właściwości, które zaczynają się od tych dwóch znaków. Na przykład poniższy zrzut ekranu przedstawia sugerowane właściwości wyszukiwania rozpoczynające się od `Se`.

![Edytor KQL sugeruje obsługiwane właściwości](../media/KQLEditorAutoCompleteProperties.png)

Ponadto edytor sugeruje również wyświetlenie listy obsługiwanych operatorów (takich jak `:`, `=` i `<>`) podczas wpisywania pełnej nazwy właściwości. Na przykład na poniższym zrzucie ekranu przedstawiono sugerowane operatory `Date` dla właściwości.

![Edytor KQL sugeruje operatory](../media/KQLEditorOperatorSuggestions.png)

Aby uzyskać więcej informacji na temat obsługiwanych właściwości i operatorów wyszukiwania, zobacz [Zapytania dotyczące słów kluczowych i warunki wyszukiwania zbierania elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).

### <a name="property-value-suggestions"></a>Sugestie dotyczące wartości właściwości

Edytor KQL zawiera sugestie dotyczące możliwych wartości niektórych właściwości. Na przykład na poniższym zrzucie ekranu przedstawiono sugerowane wartości właściwości `Kind` .

![edytor KQL sugeruje wartości niektórych właściwości](../media/KQLEditorValueSuggestions.png)

Edytor sugeruje również listę użytkowników (w formacie NAZWY UPN) podczas wpisywania właściwości adresatów wiadomości e-mail, takich jak `From`, `To``Recipients` i `Participants`.

![edytor KQL sugeruje użytkownikom właściwości poczty e-mail adresata](../media/KQLEditorRecipientSuggestions.png)

### <a name="detection-of-potential-errors"></a>Wykrywanie potencjalnych błędów

Edytor KQL wykrywa potencjalne błędy w zapytaniach wyszukiwania i zawiera wskazówki dotyczące przyczyny błędu ułatwiającego rozwiązanie błędu. Edytor wskazuje również potencjalny błąd, gdy właściwość nie ma odpowiedniej operacji ani wartości. Potencjalne błędy w zapytaniu są wyróżnione czerwonym tekstem, a wyjaśnienia i możliwe poprawki błędu są wyświetlane w sekcji listy rozwijanej **Potencjalne błędy** . Jeśli na przykład wklejono następujące zapytanie do edytora KQL, zostaną wykryte cztery potencjalne błędy.

![Wykrywanie błędów edytora KQL](../media/KQLEditorErrorDetection.png)

W takim przypadku możesz użyć wskazówek dotyczących potencjalnych błędów, aby rozwiązać problemy i naprawić zapytanie.

## <a name="more-information"></a>Więcej informacji

- Możesz przełączać się między konstruktorem warunków a edytorem KQL. Jeśli na przykład konstruktor warunków służy do konfigurowania zapytania przy użyciu pola Słowa kluczowe i wielu kart warunków, możesz wyświetlić wynikowe zapytanie w edytorze KQL. Jeśli jednak utworzysz złożone zapytanie (ze słowami kluczowymi i warunkami) w edytorze KQL, wynikowe zapytanie będzie wyświetlane tylko w polu Słowa kluczowe podczas wyświetlania go w konstruktorze warunków.

- Jeśli wklejysz złożone zapytanie do edytora KQL, edytor wykryje potencjalne błędy i zasugeruje możliwe rozwiązania w celu rozwiązania problemów z błędami.
