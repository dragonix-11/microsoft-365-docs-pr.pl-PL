---
title: Omówienie przetwarzania formularzy w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się, jak tworzyć modele przetwarzania formularzy w usłudze Microsoft SharePoint Syntex za pomocą narzędzia AI Build.
ms.openlocfilehash: 77f316a636d3a59d83bcd881df3bc2005dea722c
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916110"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Omówienie przetwarzania formularzy w usłudze Microsoft SharePoint Syntex

 ![AI Builder.](../media/content-understanding/ai-builder.png)</br>

Firma Microsoft SharePoint Syntex używa przetwarzania formularzy programu Microsoft Power Apps [AI Builder](/ai-builder/overview) do tworzenia modeli w bibliotekach dokumentów SharePoint.

Przetwarzanie formularzy narzędzia AI Builder umożliwia tworzenie modeli sztucznej inteligencji, które wykorzystują technologię uczenia maszynowego do identyfikowania i wyodrębniania par klucz-wartość i danych tabel z dokumentów ustrukturyzowanych lub częściowo ustrukturyzowanych, takich jak formularze i faktury.

Organizacje często otrzymują faktury w dużych ilościach z różnych źródeł, takich jak poczta, faks, poczta e-mail itp. Przetwarzanie tych dokumentów i ręczne wprowadzanie ich do bazy danych może zająć dużo czasu. Za pomocą sztucznej inteligencji do wyodrębniania tekstu, par klucz/wartość i tabel z dokumentów przetwarzanie formularzy automatyzuje ten proces. 

> [!NOTE]
> Aby uzyskać więcej informacji na temat przykładów scenariuszy przetwarzania formularzy, zobacz [przewodnik SharePoint Syntex adoption: Wprowadzenie guide (Wdrażanie SharePoint Syntex: Wprowadzenie](./adoption-getstarted.md)).

Można na przykład utworzyć model przetwarzania formularzy, który identyfikuje wszystkie dokumenty zamówienia zakupu przekazane do biblioteki dokumentów. Z każdego zamówienia zakupu można wyodrębniać i wyświetlać ważne dane, takie jak *numer zamówienia* zakupu, *data* lub *całkowity koszt*.

![Widok biblioteki dokumentów.](../media/content-understanding/doc-lib-done.png)</br>  

Przykładowe pliki umożliwiają trenowanie modelu i definiowanie informacji, które mają zostać wyodrębnione z formularza. Układ dokumentu jest poznany przez szkolenie modelu. Aby rozpocząć pracę, potrzebujesz tylko pięciu dokumentów formularzy. Program AI Builder przeanalizuje przykładowe pliki pod kątem par klucz-wartość, a także można ręcznie zidentyfikować te, które mogły nie zostać wykryte.  Konstruktor sztucznej inteligencji umożliwia testowanie dokładności modelu na przykładowych plikach.

Po wytrenowania i opublikowaniu modelu model tworzy [przepływ Power Automate](/power-automate/getting-started). Przepływ jest uruchamiany po przekazaniu pliku do biblioteki dokumentów SharePoint i wyodrębnia dane zidentyfikowane w modelu. Wyodrębnione dane będą wyświetlane w kolumnach w widoku biblioteki dokumentów modelu.

Administrator Office 365 musi [włączyć przetwarzanie formularzy](./set-up-content-understanding.md) dla biblioteki dokumentów SharePoint, aby użytkownicy mogli utworzyć w niej [model przetwarzania formularzy](create-a-form-processing-model.md). Lokacje można wybrać podczas instalacji lub po instalacji w ustawieniach zarządzania.

### <a name="file-limitations"></a>Ograniczenia dotyczące plików

W przypadku korzystania z modeli przetwarzania formularzy należy pamiętać [o wymaganiach i ograniczeniach dotyczących użycia plików](/ai-builder/form-processing-model-requirements).

### <a name="supported-languages"></a>Obsługiwane języki

Przetwarzanie formularzy obsługuje dokumenty w ponad 73 językach. Aby uzyskać listę języków, zobacz [Obsługa języka przetwarzania formularzy](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support).

### <a name="multi-geo-environments"></a>Środowiska z wieloma lokalizacjami geograficznymi

Podczas konfigurowania SharePoint Syntex w [środowisku Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md) można skonfigurować go tylko do używania przetwarzania formularzy w centralnej lokalizacji. Jeśli chcesz używać przetwarzania formularzy w lokalizacji satelitarnej, skontaktuj się z pomocą techniczną firmy Microsoft.

## <a name="see-also"></a>Zobacz też
  
[dokumentacja Power Automate](/power-automate/)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)

[Omówienie opisu dokumentu](document-understanding-overview.md)

[Szkolenie: Zwiększanie wydajności biznesowej za pomocą narzędzia AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)