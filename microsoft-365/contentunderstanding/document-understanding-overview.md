---
title: Omówienie dokumentacji w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się więcej o zrozumieniu dokumentów w usłudze Microsoft SharePoint Syntex.
ms.openlocfilehash: 639decf383e534253b014366d9d8c51a83a76675
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822743"
---
# <a name="document-understanding-overview-in-microsoft-sharepoint-syntex"></a>Omówienie dokumentacji w usłudze Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7]

</br>

Omówienie dokumentów używa modeli sztucznej inteligencji (AI) do automatyzacji klasyfikacji plików i wyodrębniania informacji. Najlepiej sprawdza się w przypadku dokumentów bez struktury, takich jak listy lub umowy. Dokumenty te muszą zawierać tekst, który można zidentyfikować na podstawie fraz lub wzorców. Zidentyfikowany tekst określa zarówno typ pliku, który jest (jego klasyfikacja), jak i to, co chcesz wyodrębnić (jego wyodrębniacze).

> [!NOTE]
> Zobacz [przewodnik SharePoint Syntex adoption: Wprowadzenie,](./adoption-getstarted.md) aby uzyskać więcej informacji na temat przykładów scenariuszy interpretacji dokumentów.

Modele interpretacji dokumentów są tworzone i zarządzane w typie witryny SharePoint o nazwie *centrum zawartości*. Po zastosowaniu do biblioteki dokumentów SharePoint model jest skojarzony z typem zawartości ma kolumny do przechowywania wyodrębnianych informacji. Utworzony typ zawartości jest przechowywany w galerii typów zawartości SharePoint. Możesz również użyć istniejących typów zawartości do używania ich schematu.

> [!NOTE]
> Nie można aktualizować typów zawartości tylko do odczytu lub zapieczętowanej zawartości, więc nie można ich używać w modelu.

Dodaj *klasyfikatory* i *wyodrębniacze* do modeli interpretacji dokumentów, aby wykonać następujące akcje:

- Klasyfikatory służą do identyfikowania i klasyfikowania dokumentów przekazanych do biblioteki dokumentów. Na przykład klasyfikator można "wytrenować", aby zidentyfikować wszystkie dokumenty *odnawiania kontraktu* przekazane do biblioteki. Typ zawartości odnawiania kontraktu jest definiowany przez Użytkownika podczas tworzenia klasyfikatora.

- Wyodrębniacze pobierają informacje z tych dokumentów. Na przykład dla każdego dokumentu odnawiania kontraktu określonego w bibliotece dokumentów zostaną wyświetlone kolumny zawierające *datę rozpoczęcia usługi* i *klienta* dla każdego dokumentu. 

Przykładowe pliki umożliwiają trenowanie i testowanie klasyfikatorów i wyodrębniaczy w modelu. Przykładowe pliki zawierają przykłady modelu, na które należy zwrócić uwagę podczas próby zidentyfikowania i wyodrębnienia danych z plików. Na przykład należy wytrenować klasyfikatory i wyodrębniacze odnawiania kontraktów przy użyciu przykładów dokumentów odnawiania kontraktu, z których współpracuje firma. Możesz również użyć przykładowych plików, aby przetestować skuteczność modelu.

Po opublikowaniu modelu użyj centrum zawartości, aby zastosować go do dowolnej biblioteki dokumentów SharePoint, do których masz dostęp.  

## <a name="file-limitations"></a>Ograniczenia dotyczące plików

Modele interpretacji dokumentów używają technologii optycznego rozpoznawania znaków (OCR) do skanowania plików PDF, obrazów i plików TIFF. Pliki są skanowane podczas trenowania modelu przy użyciu przykładowych plików i uruchamiania modelu względem plików w bibliotece dokumentów.

Zwróć uwagę na następujące różnice dotyczące Microsoft Office plików tekstowych i plików zeskanowanych za pomocą protokołu OCR (PDF, obraz lub TIFF):

- Office pliki: obcięte przy użyciu 64 000 znaków (podczas trenowania i uruchamiania względem plików w bibliotece dokumentów).

- Pliki zeskanowane przez protokół OCR: istnieje limit 20 stron.  

### <a name="requirements"></a>Wymagania

Przetwarzanie OCR działa najlepiej w dokumentach spełniających następujące wymagania:

- Format JPG, PNG lub PDF (tekst lub skanowane). Pliki PDF osadzone w tekście są lepsze, ponieważ nie będzie żadnych błędów w wyodrębnianiu znaków i lokalizacji.

- Jeśli pliki PDF są zablokowane hasłem, należy usunąć blokadę przed ich przesłaniem.

- Łączny rozmiar pliku dokumentów używanych do trenowania na kolekcję nie może przekraczać 50 MB, a dokumenty PDF nie powinny mieć więcej niż 500 stron.

- W przypadku obrazów wymiary muszą mieć od 50 x 50 do 10 000 x 10 000 pikseli.
   > [!NOTE]
   > Obrazy, które są bardzo szerokie lub mają nieparzyste wymiary (na przykład plany pomieszczeń), mogą zostać obcięte w procesie OCR i utracić dokładność.

- W przypadku plików PDF wymiary muszą mieć maksymalnie 17 x 17 cali, co odpowiada rozmiarom papieru legalnego lub A3 i mniejszemu rozmiarowi.

- W przypadku skanowania z dokumentów papierowych skanowanie powinno być obrazami wysokiej jakości.

- Musi używać alfabetu łacińskiego (znaków angielskich).

> [!NOTE]
> Narzędzia AI Builder nie obsługują obecnie następujących typów danych wejściowych przetwarzania formularzy:
>
> - Pola wyboru lub przyciski radiowe
> - Podpisów
> - Pliki PDF z możliwością wypełniania

### <a name="supported-file-types"></a>Obsługiwane typy plików

Modele interpretacji dokumentów obsługują następujące typy plików:

- Dok
- Docx
- Eml
- hejt
- heif
- Htm
- Html
- Jpeg
- Jpg
- Markdown
- Md
- Msg
- Pdf
- Png
- Ppt
- Pptx
- Rtf
- Tif
- Tiff
- Txt
- Xls
- Xlsx

### <a name="supported-languages"></a>Obsługiwane języki

Modele interpretacji dokumentów obsługują *wszystkie* języki oparte na języku łacińskim, w tym:

- English
- French
- German
- Italian
- Spanish

## <a name="see-also"></a>Zobacz też

[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Tworzenie centrum zawartości](create-a-content-center.md)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)

[Stosowanie modelu](apply-a-model.md)

[Różnica między interpretacją dokumentu a modelem przetwarzania formularzy](difference-between-document-understanding-and-form-processing-model.md)
  
[Omówienie przetwarzania formularzy](form-processing-overview.md)

[tryb ułatwień dostępu SharePoint Syntex](accessibility-mode.md)
