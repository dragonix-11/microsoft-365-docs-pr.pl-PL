---
title: Omówienie opisów dokumentów w aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.customer: intro-overview
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się więcej o zrozumieniu dokumentu w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: 0c72c4e0d3865a7247db78760d02a51f7f91dbcf
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016013"
---
# <a name="document-understanding-overview-in-microsoft-sharepoint-syntex"></a>Omówienie opisów dokumentów w aplikacji Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7] 

</br>

W zrozumieniu dokumentu są używane modele sztucznej inteligencji w celu zautomatyzowania klasyfikacji plików i wyodrębniania informacji. Najlepiej się sprawdza w przypadku dokumentów niestrukturryzowanych, takich jak listy lub umowy. Te dokumenty muszą zawierać tekst, który można zidentyfikować na podstawie fraz lub wzorców. Wskazany tekst wyznacza zarówno typ pliku, który jest (jego klasyfikacja), jak i to, co chcesz wyodrębnić (jego wyodrębniacze).

> [!NOTE]
> Zobacz [przykłady SharePoint Syntex: Wprowadzenie](./adoption-getstarted.md) do tego przewodnika, aby uzyskać więcej informacji na temat przykładów scenariuszy opisanych w dokumentach.

Dokumenty opisowe modele są tworzone i zarządzane w typie witryny SharePoint *nazywanej centrum zawartości*. Po zastosowaniu do biblioteki SharePoint dokumentów model jest skojarzony z typem zawartości i zawiera kolumny do przechowywania wyodrębnianych informacji. Tworzyć typy zawartości są przechowywane w galerii SharePoint typów zawartości. Możesz także użyć istniejących typów zawartości, aby użyć ich schematu.

> [!NOTE]
> Typów zawartości tylko do odczytu lub zawartości zawartości nie można aktualizować, więc nie można ich używać w modelu.

Dodaj *klasyfikatory i* *wyodrębniacze do* dokumentu, aby zrozumieć modele, aby wykonać następujące czynności: 

- Klasyfikatory służą do identyfikowania i klasyfikowania dokumentów przekazywanych do biblioteki dokumentów. Na przykład klasyfikator może być "przeszkolony" w celu identyfikowania  wszystkich dokumentów dotyczących odnawiania umowy, które są przekazywane do biblioteki. Typ zawartości odnawiania umowy jest definiowany przez Ciebie podczas tworzenia klasyfikatora.

- Wyodrębniacze ściągają informacje z tych dokumentów. Na przykład w przypadku każdego dokumentu odnowienia umowy wskazanego w bibliotece dokumentów są wyświetlane kolumny z datami rozpoczęcia usługi i  z klientem dla każdego dokumentu. 

Za pomocą plików przykładowych możesz szkolenie i testowanie klasyfikatorów i wyodrębniaczy w Twoim modelu. Przykładowe pliki stanowią przykłady modelu wyszukiwania podczas próby zidentyfikowania i wyodrębnienia danych z plików. Na przykład możesz przeszkolić klasyfikatorów odnawiania umowy i wyodrębnić ich przykłady dokumentów dotyczących odnawiania umowy, z których współpracuje Twoja firma. Możesz również użyć plików przykładowych, aby przetestować skuteczność twojego modelu.

Po opublikowaniu modelu zastosuj go do dowolnej biblioteki SharePoint dokumentów, do których masz dostęp.  

## <a name="file-limitations"></a>Ograniczenia dotyczące plików

Modele opisowe dokumentów korzystają z technologii optycznego rozpoznawania znaków (OCR, Optical Character Recognition) do skanowania plików PDF, obrazów i plików TIFF. Pliki są skanowane podczas szkolenia modelu z plikami przykładowym i podczas uruchamiania modelu na plikach w bibliotece dokumentów.

Zwróć uwagę na następujące różnice Microsoft Office plików tekstowych i plików zeskanowanych za pomocą rozpoznawania znaków OCR (PDF, obraz lub TIFF):

- Office: Obcięte z 64 000 znaków (w szkoleniu i po uruchomieniu dla plików w bibliotece dokumentów).

- Pliki skanowane zaybko:  limit strony wynosi 20.  

### <a name="requirements"></a>Wymagania

Przetwarzanie OCR działa najlepiej w przypadku dokumentów spełniających następujące wymagania:

- Formaty JPG, PNG i PDF (tekst lub zeskanowane). Pliki PDF osadzone w tekście są lepsze, ponieważ nie występują żadne błędy wyodrębniania znaków i lokalizacji.

- Jeśli pliki PDF są zablokowane hasłem, przed przesłaniem pliku musisz usunąć blokadę.

- Połączony rozmiar plików dokumentów używanych na szkolenia na kolekcję nie może przekraczać 50 MB, a dokumenty PDF nie powinny mieć więcej niż 500 stron.

- W przypadku obrazów wymiary muszą być pomiędzy 50 × 50 a 10 000 × 10 000 pikseli.
   > [!NOTE]
   > Obrazy o bardzo szerokich szerokościach lub nietypowych wymiarach (na przykład plany podłogi) mogą zostać obcięte w procesie OCR i tracą dokładność.
 
- W przypadku plików PDF wymiary muszą być nie mniejsze niż 17 x 17 cali, odpowiadające rozmiarom papieru legal lub A3.

- W przypadku skanowania z dokumentów papierowych skany powinny być obrazami wysokiej jakości.

- Należy używać alfabetu łacińskiego (angielskich znaków).

> [!NOTE]
> AI Builder obecnie nie obsługuje następujących typów danych wejściowych przetwarzania formularza:<br>— Pola wyboru lub przyciski radiowe<br>- Podpisy<br>- Pliki PDF z wypełnianiem

### <a name="supported-file-types"></a>Obsługiwane typy plików

Modele opisowe dokumentów obsługują następujące typy plików:

- doc
- docx
- eml
- heic
- heif
- htm
- html
- jpeg
- jpg
- zaznaczanie
- md
- msg
- pdf
- png
- ppt
- pptx
- rtf
- tif
- tiff
- txt
- xls
- xlsx

### <a name="supported-languages"></a>Obsługiwane języki

Modele opisowe dokumentów obsługują następujące języki:
- French
- German
- Italian
- Spanish


## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Tworzenie centrum zawartości](create-a-content-center.md)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)

[Stosowanie modelu](apply-a-model.md)   

[Różnica między zrozumieniem dokumentu a modelem przetwarzania formularza](difference-between-document-understanding-and-form-processing-model.md)
  
[Omówienie przetwarzania formularzy](form-processing-overview.md)

[SharePoint Syntex tryb ułatwień dostępu](accessibility-mode.md)
