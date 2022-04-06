---
title: Różnice między zrozumieniem dokumentu a modelami przetwarzania formularzy
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
description: Zapoznaj się z kluczowymi różnicami między modelem rozumienia dokumentu a modelem przetwarzania formularzy.
ms.openlocfilehash: e5de4c55cc8a559ad03d722b1f7235797db76e07
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681287"
---
# <a name="differences-between-document-understanding-and-form-processing-models"></a>Różnice między zrozumieniem dokumentu a modelami przetwarzania formularzy 

Zrozumienie zawartości w aplikacji Microsoft SharePoint Syntex umożliwia identyfikowanie i klasyfikowanie dokumentów przekazanych do SharePoint dokumentów, a następnie wyodrębnianie odpowiednich informacji z poszczególnych plików. Na przykład po przesłaniu plików do biblioteki SharePoint dokumentów wszystkie pliki zidentyfikowane jako Zamówienia zakupu są klasyfikowane jako  takie, a następnie wyświetlane w niestandardowym widoku biblioteki dokumentów. Ponadto można pociągnąć określone informacje z każdego pliku (na przykład numer punktu usług  posumowych i sumę *) i* wyświetlić je jako kolumnę w widoku biblioteki dokumentów. 

Zrozumienie zawartości umożliwia tworzenie *modeli w* celu identyfikowania i wyodrębniania potrzebnych informacji. Modele pomagają rozwiązywać problemy biznesowe związane z wyszukiwaniem, procesami biznesowymi, zgodnością i wieloma innymi.

Można użyć dwóch typów modeli niestandardowych:

- [Dokument opisowy modele](document-understanding-overview.md)
- [Modele przetwarzania formularzy](form-processing-overview.md)

Oba modele są zwykle używane do tego samego celu, jednak wymienione poniżej główne różnice wpływają na to, których z nich można użyć.

> [!NOTE]
> Zobacz [przykłady SharePoint Syntex: Wprowadzenie](./adoption-getstarted.md), aby uzyskać więcej informacji na temat przetwarzania formularzy i opisów scenariuszy.

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Zawartość strukturalne a niestrukturalna i półstrukturalna

Używaj dokumentów do zrozumienia modeli, aby identyfikować i wyodrębniać dane z dokumentów niestrukturryzowanych, takich jak listy lub umowy, w których jednostki tekstowe, które chcesz wyodrębnić, są w zdaniach lub określonych regionach dokumentu. Na przykład dokument bez struktury może być listem o odnowieniu umowy, który można opisać na różne sposoby. Jednak w treści każdego dokumentu odnowienia umowy istnieją spójne informacje, takie jak ciąg tekstowy Data rozpoczęcia usługi,  po której następuje rzeczywista data.

Za pomocą modeli przetwarzania formularzy można identyfikować pliki i wyodrębniać dane z dokumentów strukturalnych lub pół strukturalnych, takich jak formularze lub faktury. Modele przetwarzania formularzy są przeszkolone w celu zrozumienia układu formularza na podstawie przykładowych dokumentów i uczą się wyszukiwania danych do wyodrębnienia z podobnych lokalizacji. Formularze mają zazwyczaj bardziej ustrukturyzowany układ, w którym jednostki znajdują się w tym samym miejscu (na przykład numer PEP w formularzu podatkowym).

> [!NOTE]
> Musisz mieć dostęp do witryny centrum zawartości, aby utworzyć model rozumienia dokumentu lub zastosować go do SharePoint dokumentów. 

## <a name="where-models-are-created"></a>Gdzie są tworzone modele

Modele opisowe dokumentów są tworzone i zarządzane w SharePoint centrum zawartości. 

> [!NOTE]
> Aby uzyskać więcej informacji na temat dokumentów wejściowych, [zobacz Wymagania i ograniczenia dotyczące modelu przetwarzania formularzy](/ai-builder/form-processing-model-requirements). 

Modele przetwarzania formularzy są tworzone Power Apps [aplikacji AI Builder](/ai-builder/overview), ale tworzenie rozpoczyna się bezpośrednio z SharePoint dokumentów. Aby można było utworzyć dla biblioteki dokumentów model przetwarzania formularzy, użytkownik musi mieć włączoną funkcję tworzenia modelu przetwarzania formularzy. Administratorzy mogą włączyć tworzenie modelu przetwarzania formularzy w zawartości opisowej ustawienia administratora. Modele przetwarzania formularzy Power Automate przepływów do przetwarzania plików po ich przesłaniu do biblioteki dokumentów.

Podczas tworzenia modelu rozumienia dokumentu jest tworzyć nowy typ [SharePoint, który](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) jest zapisywany w galerii typów SharePoint zawartości. Możesz również w razie potrzeby zdefiniować model za pomocą istniejących typów zawartości.

Po utworzeniu typu zawartości i skojarzeniu go z modelem możesz również odwoływać się do tego modelu za pomocą panelu właściwości **Typ zawartości witryny** .

![Zrzut ekranu przedstawiający panel Typ zawartości witryny z wyróżnionym modelem opisowym dokumentu.](../media/content-understanding/site-content-type-panel.png)

Modele przetwarzania formularzy tworzą [nowe SharePoint typów zawartości](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), które są również przechowywane w SharePoint typów zawartości.

## <a name="where-they-can-be-applied"></a>Gdzie można je stosować

Modele opisowe dokumentów można stosować do SharePoint dokumentów, do których masz dostęp. Centrum zawartości umożliwia utworzenie modelu rozumienia dokumentu i zastosowanie go do różnych bibliotek dokumentów. Centrum zawartości zapewnia bardziej centralną kontrolę nad tym, w jaki sposób są używane modele zrozumienia dokumentów i gdzie są stosowane. Uwaga: te informacje muszą być także rzutować na centrum zawartości.

Modele przetwarzania formularzy można obecnie stosować tylko do biblioteki SharePoint dokumentów, z której zostały utworzone. Dzięki temu licencjonowani użytkownicy z dostępem do witryny mogą utworzyć model przetwarzania formularzy. Zwróć uwagę, że administrator musi włączyć przetwarzanie formularzy na SharePoint dokumentów, aby było dostępne dla licencjonowanych użytkowników.

## <a name="comparison-of-forms-processing-and-document-understanding"></a>Porównanie przetwarzania formularzy i zrozumienia dokumentu

Skorzystaj z poniższej tabeli, aby dowiedzieć się, kiedy i kiedy używać przetwarzania formularzy.

| Funkcja | Przetwarzanie formularzy | Opis dokumentu |
| ------- | ------- | ------- |
| Typ modelu — kiedy używać każdej z nich | Formaty plików pół strukturalne, na przykład pliki PDF do formatowania zawartości formularzy, takiej jak faktury lub zamówienia zakupu, w których układ i formatowanie są podobne.  | Używany w przypadku pół strukturalnych formatów plików — na przykład w Office dokumentów, w których występują różnice w układzie, ale nadal podobne informacje do wyodrębnienia. |
| Tworzenie modeli | Model utworzony w konstruktorze AI z bezproblemowym dostępem z SharePoint dokumentów.| Model utworzony SharePoint w nowej witrynie, w centrum zawartości. |
| Typ klasyfikacji| Klasyfikator tabeli służy do zasyłania wskazówek systemu na temat danych do wyodrębnienia.| Klasyfikator przeszkolny z opcjonalnymi wyodrębniaczami za pomocą maszynowego nauczania w celu przypisania lokalizacji dokumentu na temat danych do wyodrębnienia.|
| Lokalizacje | Przeszkolone w zakresie jednej biblioteki dokumentów.| Można stosować je do wielu bibliotek.|
| Obsługiwane typy plików| Szkolenie dotyczące formatu PDF, JPG i PNG o rozmiarze 50 MB i 500 stron.| Szkolenie dotyczące 5–10 plików PDF, Office e-mail, w tym przykładów ujemnych.<br>Office są obcinane do 64 znaków. Pliki skanowane za na rozpoznawanie danych (OCR) są ograniczone do 20 stron.|
| Integracja z zarządzanymi metadanymi | Nie | Tak, wyodrębnianie encji szkoleniowej odwołującej się do pola skonfigurowanych zarządzanych metadanych.|
| Integracja funkcji zgodności, gdy Microsoft Information Protection jest włączona | Ustaw opublikowane etykiety przechowywania.<br>Ustaw etykiety wrażliwości. | Ustaw opublikowane etykiety przechowywania.<br>Ustaw opublikowane etykiety wrażliwości. |
| Obsługiwane regiony| Przetwarzanie formularzy korzysta z platformy Power Platform. Aby uzyskać informacje na temat globalnej dostępności dla platformy Power Platform i aplikacji AI Builder, zobacz Dostępność [platformy Power.](https://dynamics.microsoft.com/geographic-availability/) | Dostępne we wszystkich regionach.|
| Koszt transakcji | Używa środków na użycie aplikacji AI Builder.<br>Środki można kupować w partiach po 1M.<br>Środki 1M są uwzględniane przy zakupie ponad 300 SharePoint Syntex licencji.<br>1M pozwala na przetwarzanie 2000 stron plików.<br>| Nie dotyczy |
| Pojemność | Korzysta z domyślnego środowiska platformy Power Platform (środowiska niestandardowe z obsługiwaną bazą danych Dataverse). | Nie ma ograniczeń pojemności.|
| Obsługiwane języki| English <br>Dostępne później w 2022 roku: języki alfabetu łacińskiego | Modele działają we wszystkich językach alfabetu łacińskiego. Oprócz języka angielskiego: niemiecki, szwedzki, francuski, hiszpański, włoski i portugalski.|

## <a name="see-also"></a>Zobacz też

[Szkolenie: Ulepszanie wydajności biznesowej za pomocą aplikacji AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Omówienie przetwarzania formularzy](form-processing-overview.md)

[Wprowadzenie do SharePoint Syntex](index.md)