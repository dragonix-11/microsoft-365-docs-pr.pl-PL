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
ms.openlocfilehash: 49e3e2a0d63303b1c5cbdbfd941ba8aaa40594a7
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66491708"
---
# <a name="differences-between-document-understanding-and-form-processing-models"></a>Różnice między interpretacją dokumentów a modelami przetwarzania formularzy 

Opis zawartości w usłudze Microsoft SharePoint Syntex umożliwia identyfikowanie i klasyfikowanie dokumentów przekazanych do bibliotek dokumentów programu SharePoint, a następnie wyodrębnianie odpowiednich informacji z każdego pliku. Na przykład, ponieważ pliki są przekazywane do biblioteki dokumentów programu SharePoint, wszystkie pliki, które są identyfikowane jako *zamówienia zakupu* , są klasyfikowane jako takie, a następnie wyświetlane w niestandardowym widoku biblioteki dokumentów. Ponadto można pobrać określone informacje z każdego pliku (na przykład *numer zamówienia* zakupu i *sumę*) i wyświetlić je jako kolumnę w widoku biblioteki dokumentów. 

Zrozumienie zawartości umożliwia tworzenie *modeli* w celu identyfikowania i wyodrębniania potrzebnych informacji. Modele mają wartość ułatwiającą rozwiązywanie problemów biznesowych dotyczących wyszukiwania, procesów biznesowych, zgodności i wielu innych.

Istnieją dwa niestandardowe typy modeli, których można użyć:

- [Omówienie dokumentów modeli](document-understanding-overview.md)
- [Modele przetwarzania formularzy](form-processing-overview.md)

Chociaż oba modele są zwykle używane w tym samym celu, kluczowe różnice wymienione poniżej wpływają na to, których modeli można użyć.

> [!NOTE]
> Zobacz [Wprowadzenie do wdrażania SharePoint Syntex](./adoption-getstarted.md), aby uzyskać więcej informacji na temat przetwarzania formularzy i opisu dokumentów przykładów scenariuszy.

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Zawartość strukturalna i nieustrukturyzowana i częściowo ustrukturyzowana

Użyj modeli interpretacji dokumentów, aby identyfikować i wyodrębniać dane z dokumentów bez struktury, takich jak litery lub kontrakty, gdzie jednostki tekstowe, które chcesz wyodrębnić, znajdują się w zdaniach lub określonych regionach dokumentu. Na przykład dokument bez struktury może być listem odnawiającym umowę, który można napisać na różne sposoby. Jednak informacje istnieją spójnie w treści każdego dokumentu odnawiania umowy, na przykład ciąg `Service start date of` tekstowy, po którym następuje rzeczywista data.

Użyj modeli przetwarzania formularzy, aby identyfikować pliki i wyodrębniać dane ze strukturalnych lub częściowo ustrukturyzowanych dokumentów, takich jak formularze lub faktury. Modele przetwarzania formularzy są wytrenowane w celu zrozumienia układu formularza z przykładowych dokumentów i dowiedz się, jak szukać danych potrzebnych do wyodrębnienia z podobnych lokalizacji. Formularze zwykle mają bardziej ustrukturyzowany układ, w którym jednostki znajdują się w tej samej lokalizacji (na przykład numer ubezpieczenia społecznego w formularzu podatkowym).

> [!NOTE]
> Aby utworzyć model zrozumienia dokumentów lub zastosować go do biblioteki dokumentów programu SharePoint, musisz mieć dostęp do witryny centrum zawartości. 

## <a name="where-models-are-created"></a>Gdzie są tworzone modele

Modele interpretacji dokumentów są tworzone i zarządzane w witrynie centrum zawartości programu SharePoint. 

> [!NOTE]
> Aby uzyskać więcej informacji na temat dokumentów wejściowych, zobacz [Wymagania i ograniczenia modelu przetwarzania formularzy](/ai-builder/form-processing-model-requirements). 

Modele przetwarzania formularzy są tworzone w narzędziu Power Apps [AI Builder](/ai-builder/overview), ale tworzenie rozpoczyna się bezpośrednio z biblioteki dokumentów programu SharePoint. Biblioteka dokumentów musi mieć włączone tworzenie modelu przetwarzania formularzy, zanim użytkownik będzie mógł utworzyć dla niej model przetwarzania formularzy. Administratorzy mogą włączyć tworzenie modelu przetwarzania formularzy w obszarze zawartości z ustawieniami administratora. Modele przetwarzania formularzy używają przepływów usługi Power Automate do przetwarzania plików po ich przekazaniu do biblioteki dokumentów.

Podczas tworzenia modelu interpretacji dokumentów tworzysz nowy [typ zawartości programu SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) , który jest zapisywany w galerii Typów zawartości programu SharePoint. Możesz też użyć istniejących typów zawartości, aby zdefiniować model w razie potrzeby.

Po utworzeniu i skojarzeniu typu zawartości z modelem można również odwołać się do tego modelu z panelu właściwości **Typ zawartości witryny** .

:::image type="content" source="../media/content-understanding/site-content-type-panel.png" alt-text="Zrzut ekranu przedstawiający panel Typ zawartości witryny z wyróżnionym modelem opisu dokumentu." lightbox="../media/content-understanding/site-content-type-panel.png":::

Modele przetwarzania formularzy tworzą również nowe [typy zawartości programu SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), a także są przechowywane w galerii Typów zawartości programu SharePoint.

## <a name="where-they-can-be-applied"></a>Gdzie można je zastosować

Modele interpretacji dokumentów można zastosować do bibliotek dokumentów programu SharePoint, do których masz dostęp. Użyj centrum zawartości, aby utworzyć model interpretacji dokumentów i zastosować go do różnych bibliotek dokumentów. Centrum zawartości zapewnia bardziej centralną kontrolę sposobu użycia modeli interpretacji dokumentów i miejsca ich stosowania. Należy pamiętać, że te informacje muszą również zostać rzutowane do centrum zawartości.

Modele przetwarzania formularzy można obecnie stosować tylko do biblioteki dokumentów programu SharePoint, na podstawie której zostały utworzone. Umożliwia to licencjonowanym użytkownikom z dostępem do witryny tworzenie modelu przetwarzania formularzy. Należy pamiętać, że administrator musi włączyć przetwarzanie formularzy w bibliotece dokumentów programu SharePoint, aby była dostępna dla licencjonowanych użytkowników.

## <a name="comparison-of-form-processing-and-document-understanding"></a>Porównanie przetwarzania formularzy i interpretacji dokumentów

Poniższa tabela zawiera informacje o tym, kiedy używać przetwarzania formularzy i kiedy używać zrozumienia dokumentów.

| Funkcja | Przetwarzanie formularza | Analiza dokumentu |
| ------- | ------- | ------- |
| Typ modelu — kiedy używać każdego z nich | Formaty plików ustrukturyzowane i częściowo ustrukturyzowane, na przykład pliki PDF dla zawartości formularzy, takie jak faktury lub zamówienia zakupu, w których układ i formatowanie są podobne.  | Formaty plików bez struktury lub częściowo ustrukturyzowane, na przykład dokumenty pakietu Office, w których występują różnice w układzie, ale nadal podobne informacje do wyodrębnienia. |
| Tworzenie modelu | Model utworzony w konstruktorze sztucznej inteligencji z bezproblemowym dostępem z biblioteki dokumentów programu SharePoint.| Model utworzony w programie SharePoint w nowej witrynie — centrum zawartości. |
| Typ klasyfikacji| Klasyfikator settable służy do udzielania systemowi wskazówek dotyczących wyodrębniania danych.| Klasyfikator trainable z opcjonalnymi wyodrębniaczami przy użyciu nauczania maszynowego w celu przypisania lokalizacji dokumentu do wyodrębnienia danych.|
| Lokalizacje | Wytrenowane dla pojedynczej biblioteki dokumentów.| Można zastosować do wielu bibliotek.|
| Obsługiwane typy plików| Trenuj w formacie PDF, JPG, PNG, łącznie 50 MB i 500 stron.| Trenuj w plikach PDF 5–10, Office lub e-mail, w tym w negatywnych przykładach.<br>Pliki pakietu Office są obcinane przy użyciu znaków 64K. Pliki zeskanowane przez protokół OCR są ograniczone do 20 stron. Modele interpretacji dokumentów obsługują następujące typy plików doc, docx, eml, heic, heif, htm, html, jpeg, jpg, markdown, md, msg, pdf, png, ppt, pptx, rtf, tif, tiff, txt, xls i xlsx.|
| Integracja z zarządzanymi metadanymi | Nie | Tak, przez trenowanie wyodrębniania jednostek odwołującego się do skonfigurowanego pola zarządzanych metadanych.|
| Integracja funkcji zgodności z Microsoft Purview Information Protection | Ustaw opublikowane etykiety przechowywania.<br>Nadchodzą etykiety poufności ustawić. | Ustaw opublikowane etykiety przechowywania.<br>Ustaw opublikowane etykiety poufności. |
| Obsługiwane regiony| Przetwarzanie formularzy opiera się na usłudze Power Platform. Aby uzyskać informacje o globalnej dostępności platformy Power Platform i narzędzia AI Builder, zobacz [Dostępność platformy Power Platform](https://dynamics.microsoft.com/geographic-availability/). | Dostępne we wszystkich regionach.|
| Koszt transakcyjny | Używa środków narzędzia AI Builder.<br>3,5 tys. środków są uwzględniane dla każdej licencji SharePoint Syntex miesięcznie.<br>Środki w wysokości 1 mln umożliwią przetwarzanie 2000 stron plików.<br>| Nie dotyczy |
| Pojemność | Używa domyślnego środowiska platformy Power Platform (środowiska niestandardowe z obsługiwaną bazą danych Dataverse). | Nie ma ograniczeń pojemności.|
| Obsługiwane języki| Obsługa języka dla ponad [73 języków](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support). | Modele działają we wszystkich językach alfabetu łacińskiego. Oprócz języka angielskiego: niemiecki, szwedzki, francuski, hiszpański, włoski i portugalski.|


## <a name="see-also"></a>Zobacz też

[Szkolenie: Zwiększanie wydajności biznesowej za pomocą narzędzia AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[Omówienie opisu dokumentu](document-understanding-overview.md)

[Omówienie przetwarzania formularzy](form-processing-overview.md)

[Wprowadzenie do SharePoint Syntex](index.md)
