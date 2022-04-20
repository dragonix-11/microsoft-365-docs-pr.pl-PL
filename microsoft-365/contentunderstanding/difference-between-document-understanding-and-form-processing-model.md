---
title: Różnice między interpretacją dokumentów a modelami przetwarzania formularzy
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się więcej o kluczowych różnicach między modelem zrozumienia dokumentu a modelem przetwarzania formularzy.
ms.openlocfilehash: 571516a7112e3f145d9e3ca392ad3488a33b4887
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947830"
---
# <a name="differences-between-document-understanding-and-form-processing-models"></a>Różnice między interpretacją dokumentów a modelami przetwarzania formularzy 

Opis zawartości w usłudze Microsoft SharePoint Syntex umożliwia identyfikowanie i klasyfikowanie dokumentów przekazanych do bibliotek dokumentów SharePoint, a następnie wyodrębnianie odpowiednich informacji z każdego pliku. Na przykład w miarę przekazywania plików do biblioteki dokumentów SharePoint wszystkie pliki, które są identyfikowane jako *zamówienia zakupu*, są klasyfikowane jako takie, a następnie wyświetlane w niestandardowym widoku biblioteki dokumentów. Ponadto można pobrać określone informacje z każdego pliku (na przykład *numer zamówienia* zakupu i *sumę*) i wyświetlić je jako kolumnę w widoku biblioteki dokumentów. 

Zrozumienie zawartości umożliwia tworzenie *modeli* w celu identyfikowania i wyodrębniania potrzebnych informacji. Modele mają wartość ułatwiającą rozwiązywanie problemów biznesowych dotyczących wyszukiwania, procesów biznesowych, zgodności i wielu innych.

Istnieją dwa niestandardowe typy modeli, których można użyć:

- [Omówienie dokumentów modeli](document-understanding-overview.md)
- [Modele przetwarzania formularzy](form-processing-overview.md)

Chociaż oba modele są zwykle używane w tym samym celu, kluczowe różnice wymienione poniżej wpływają na to, których modeli można użyć.

> [!NOTE]
> Zobacz [przewodnik SharePoint Syntex adoption: Wprowadzenie ,](./adoption-getstarted.md) aby uzyskać więcej informacji na temat przetwarzania formularzy i przykładów scenariuszy interpretacji dokumentów.

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Zawartość strukturalna i nieustrukturyzowana i częściowo ustrukturyzowana

Użyj modeli interpretacji dokumentów, aby identyfikować i wyodrębniać dane z dokumentów bez struktury, takich jak litery lub kontrakty, gdzie jednostki tekstowe, które chcesz wyodrębnić, znajdują się w zdaniach lub określonych regionach dokumentu. Na przykład dokument bez struktury może być listem odnawiającym umowę, który można napisać na różne sposoby. Jednak informacje istnieją spójnie w treści każdego dokumentu odnawiania umowy, na przykład *ciąg tekstowy Data rozpoczęcia usługi* , po którym następuje rzeczywista data.

Użyj modeli przetwarzania formularzy, aby identyfikować pliki i wyodrębniać dane ze strukturalnych lub częściowo ustrukturyzowanych dokumentów, takich jak formularze lub faktury. Modele przetwarzania formularzy są wytrenowane w celu zrozumienia układu formularza z przykładowych dokumentów i dowiedz się, jak szukać danych potrzebnych do wyodrębnienia z podobnych lokalizacji. Formularze zwykle mają bardziej ustrukturyzowany układ, w którym jednostki znajdują się w tej samej lokalizacji (na przykład numer ubezpieczenia społecznego w formularzu podatkowym).

> [!NOTE]
> Aby utworzyć model zrozumienia dokumentów lub zastosować go do biblioteki dokumentów SharePoint, musisz mieć dostęp do witryny centrum zawartości. 

## <a name="where-models-are-created"></a>Gdzie są tworzone modele

Modele z opisem dokumentów są tworzone i zarządzane w witrynie centrum zawartości SharePoint. 

> [!NOTE]
> Aby uzyskać więcej informacji na temat dokumentów wejściowych, zobacz [Wymagania i ograniczenia modelu przetwarzania formularzy](/ai-builder/form-processing-model-requirements). 

Modele przetwarzania formularzy są tworzone w narzędziu Power Apps [AI Builder](/ai-builder/overview), ale tworzenie rozpoczyna się bezpośrednio z biblioteki dokumentów SharePoint. Biblioteka dokumentów musi mieć włączone tworzenie modelu przetwarzania formularzy, zanim użytkownik będzie mógł utworzyć dla niej model przetwarzania formularzy. Administratorzy mogą włączyć tworzenie modelu przetwarzania formularzy w obszarze zawartości z ustawieniami administratora. Modele przetwarzania formularzy używają przepływów Power Automate do przetwarzania plików po ich przekazaniu do biblioteki dokumentów.

Podczas tworzenia modelu interpretacji dokumentów tworzysz nowy [typ zawartości SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) zapisywany w galerii SharePoint Typy zawartości. Możesz też użyć istniejących typów zawartości, aby zdefiniować model w razie potrzeby.

Po utworzeniu i skojarzeniu typu zawartości z modelem można również odwołać się do tego modelu z panelu właściwości **Typ zawartości witryny** .

![Zrzut ekranu przedstawiający panel Typ zawartości witryny z wyróżnionym modelem opisu dokumentu.](../media/content-understanding/site-content-type-panel.png)

Modele przetwarzania formularzy tworzą również nowe [typy zawartości SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), a także są przechowywane w galerii SharePoint Typy zawartości.

## <a name="where-they-can-be-applied"></a>Gdzie można je zastosować

Modele interpretacji dokumentów można zastosować do SharePoint bibliotek dokumentów, do których masz dostęp. Użyj centrum zawartości, aby utworzyć model interpretacji dokumentów i zastosować go do różnych bibliotek dokumentów. Centrum zawartości zapewnia bardziej centralną kontrolę sposobu użycia modeli interpretacji dokumentów i miejsca ich stosowania. Należy pamiętać, że te informacje muszą również zostać rzutowane do centrum zawartości.

Modele przetwarzania formularzy można obecnie stosować tylko do biblioteki dokumentów SharePoint, z której zostały utworzone. Umożliwia to licencjonowanym użytkownikom z dostępem do witryny tworzenie modelu przetwarzania formularzy. Należy pamiętać, że administrator musi włączyć przetwarzanie formularzy w bibliotece dokumentów SharePoint, aby była dostępna dla licencjonowanych użytkowników.

## <a name="comparison-of-forms-processing-and-document-understanding"></a>Porównanie przetwarzania formularzy i interpretacji dokumentów

Poniższa tabela służy do zrozumienia, kiedy używać przetwarzania formularzy i kiedy używać zrozumienia dokumentów.

| Funkcja | Przetwarzanie formularzy | Omówienie dokumentu |
| ------- | ------- | ------- |
| Typ modelu — kiedy używać każdego z nich | Służy do częściowo ustrukturyzowanych formatów plików, na przykład plików PDF dla zawartości formularzy, takich jak faktury lub zamówienia zakupu, w których układ i formatowanie są podobne.  | Służy do częściowo ustrukturyzowanych formatów plików — na przykład Office dokumentów, w których występują różnice w układzie, ale nadal podobne informacje do wyodrębnienia. |
| Tworzenie modelu | Model utworzony w konstruktorze sztucznej inteligencji z bezproblemowym dostępem z biblioteki dokumentów SharePoint.| Model utworzony w SharePoint w nowej witrynie— centrum zawartości. |
| Typ klasyfikacji| Klasyfikator settable służy do udzielania systemowi wskazówek dotyczących wyodrębniania danych.| Klasyfikator trainable z opcjonalnymi wyodrębniaczami przy użyciu nauczania maszynowego w celu przypisania lokalizacji dokumentu do wyodrębnienia danych.|
| Lokalizacje | Wytrenowane dla pojedynczej biblioteki dokumentów.| Można zastosować do wielu bibliotek.|
| Obsługiwane typy plików| Trenuj w formacie PDF, JPG, PNG, łącznie 50 MB i 500 stron.| Wytrenuj pliki PDF, Office lub e-mail 5–10, w tym negatywne przykłady.<br>Office pliki są obcinane przy użyciu 64 tys. znaków. Pliki zeskanowane przez protokół OCR są ograniczone do 20 stron.|
| Integracja z zarządzanymi metadanymi | Nie | Tak, przez trenowanie wyodrębniania jednostek odwołującego się do skonfigurowanego pola zarządzanych metadanych.|
| Integracja funkcji zgodności z usługą Microsoft Purview Information Protection | Ustaw opublikowane etykiety przechowywania.<br>Nadchodzą etykiety poufności ustawić. | Ustaw opublikowane etykiety przechowywania.<br>Ustaw opublikowane etykiety poufności. |
| Obsługiwane regiony| Przetwarzanie formularzy opiera się na usłudze Power Platform. Aby uzyskać informacje o globalnej dostępności platformy Power Platform i narzędzia AI Builder, zobacz [Dostępność platformy Power Platform](https://dynamics.microsoft.com/geographic-availability/). | Dostępne we wszystkich regionach.|
| Koszt transakcyjny | Używa środków narzędzia AI Builder.<br>Środki można kupić w partiach po 1 mln.<br>Środki na korzystanie z 1 mln są uwzględniane w przypadku zakupu ponad 300 SharePoint Syntex licencji.<br>Środki w wysokości 1 mln umożliwią przetwarzanie 2000 stron plików.<br>| nd. |
| Pojemność | Używa domyślnego środowiska platformy Power Platform (środowiska niestandardowe z obsługiwaną bazą danych Dataverse). | Nie ma ograniczeń pojemności.|
| Obsługiwane języki| Obsługa języka dla większej [liczby 73 języków](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support). | Modele działają we wszystkich językach alfabetu łacińskiego. Oprócz języka angielskiego: niemiecki, szwedzki, francuski, hiszpański, włoski i portugalski.|


## <a name="see-also"></a>Zobacz też

[Szkolenie: Zwiększanie wydajności biznesowej za pomocą narzędzia AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[Omówienie opisu dokumentu](document-understanding-overview.md)

[Omówienie przetwarzania formularzy](form-processing-overview.md)

[Wprowadzenie do SharePoint Syntex](index.md)
