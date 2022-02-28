---
title: Omówienie przetwarzania formularzy w aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Informacje o przetwarzaniu formularzy w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: 8079f12c3b05d62de95bcb08808d1acc931a37d7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985101"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Omówienie przetwarzania formularzy w aplikacji Microsoft SharePoint Syntex

 ![AI Builder.](../media/content-understanding/ai-builder.png)</br>

Aplikacja Microsoft SharePoint Syntex używa aplikacji Microsoft Power Apps [Builder](/ai-builder/overview) do tworzenia modeli w SharePoint bibliotekach dokumentów.

Za pomocą przetwarzania formularzy aplikacji AI Builder możesz tworzyć modele aplikacji AI, które korzystają z technologii uczenia maszynowego do identyfikowania i wyodrębniania par klucz-wartości oraz danych tabeli z dokumentów strukturalnych lub pół strukturalnych, takich jak formularze i faktury.

Organizacje często otrzymują faktury w dużych ilościach z różnych źródeł, takich jak poczta, faks, poczta e-mail itp. Przetwarzanie tych dokumentów i ręczne wprowadzanie ich do bazy danych może zająć sporo czasu. Używając drugiej technologii do wyodrębniania tekstu, par kluczy i wartości oraz tabel z dokumentów, przetwarzanie formularzy automatyzuje ten proces. 

> [!NOTE]
> Zobacz [przykłady SharePoint Syntex formularza: wprowadzenie](./adoption-getstarted.md) do tego przewodnika, aby uzyskać więcej informacji na temat przykładów scenariuszy przetwarzania formularzy.

Można na przykład utworzyć model przetwarzania formularzy identyfikujący wszystkie dokumenty zamówień zakupu, które są przekazywane do biblioteki dokumentów. Z każdego zamówienia zakupu możesz następnie wyodrębnić i wyświetlić określone dane, które są dla Ciebie ważne, takie jak Numer zamówienia *zakupu, Data* lub *Koszt całkowity*.

![Widok biblioteki dokumentów.](../media/content-understanding/doc-lib-done.png)</br>  

Pliki przykładowe są służące do przeszkolinia modelu i definiowania informacji do wyodrębnienia z formularza. Układ dokumentu jest uczący się na szkoleniu Twojego modelu. Aby rozpocząć, potrzebujesz tylko pięciu dokumentów formularzy. Za pomocą aplikacji AI Builder przeanalizuje pliki przykładowe pod uwagę pary klucz-wartość, a także można ręcznie zidentyfikować te, które nie zostały wykryte.  Konstruktor AI umożliwia testowanie dokładności modelu na plikach przykładowych.

Model, który zostanie przeszkoliny i publikowany, tworzy [Power Automate Flow.](/power-automate/getting-started) Przepływ jest uruchamiany po przesłaniu pliku do biblioteki SharePoint dokumentów i wyodrębnia dane, które zostały zidentyfikowane w modelu. Wyodrębnione dane będą wyświetlane w kolumnach w widoku biblioteki dokumentów modelu.

Administrator Office 365 musi włączyć przetwarzanie formularza [](./set-up-content-understanding.md) dla biblioteki SharePoint dokumentów, aby użytkownicy mogli w nim tworzyć [model](create-a-form-processing-model.md) przetwarzania formularzy. Witryny możesz wybrać podczas instalacji lub po zakończeniu konfiguracji w ustawieniach zarządzania.

### <a name="file-limitations"></a>Ograniczenia dotyczące plików

Podczas korzystania z modeli przetwarzania formularzy pamiętaj o [wymaganiach i ograniczeniach dotyczących użycia plików](/ai-builder/form-processing-model-requirements).

### <a name="multi-geo-environments"></a>Środowiska z wieloma lokalizacjami geograficznymi

Podczas konfigurowania SharePoint Syntex w środowisku [Microsoft 365 multi-Geo](../enterprise/microsoft-365-multi-geo.md) można skonfigurować je tylko do używania przetwarzania formularzy w lokalizacji centralnej. Jeśli chcesz użyć przetwarzania formularza w lokalizacji satelitarnej, skontaktuj się z pomocą techniczną firmy Microsoft.






## <a name="see-also"></a>Zobacz też
  
[Power Automate dokumentacji](/power-automate/)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Szkolenie: Ulepszanie wydajności biznesowej za pomocą aplikacji AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)