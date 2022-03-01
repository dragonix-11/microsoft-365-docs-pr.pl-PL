---
title: Importowanie przykładowego modelu zrozumienia dokumentu dla aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.custom: intro-get-started
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się więcej o zrozumieniu modeli za pomocą przykładowego modelu.
ms.openlocfilehash: 6e7c680bcb136b52e0b3c9821471d922d43b614b
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2022
ms.locfileid: "63009726"
---
# <a name="import-a-sample-document-understanding-model-for-microsoft-sharepoint-syntex"></a>Importowanie przykładowego modelu zrozumienia dokumentu dla aplikacji Microsoft SharePoint Syntex

SharePoint Syntex udostępnia przykładowy model, który można wykorzystać do analizy, który zapewnia lepszy opis sposobu tworzenia własnych modeli. Przykładowy model pozwala również zbadać składniki modelu, takie jak klasyfikator, wyodrębniacze i objaśnienia. Za pomocą przykładowych plików można również przeszkolić model.

## <a name="import-the-sample-model"></a>Importowanie przykładowego modelu

Aby uzyskać dostęp do przykładowego modelu, należy najpierw zaimportować ten model do centrum zawartości.

1. W centrum zawartości wybierz pozycję **Modele** , aby wyświetlić listę modeli.</br>
2. Na stronie **Modele** wybierz pozycję **Importuj przykładowy model**.</br>

    ![Zaimportuj przykładowy model.](../media/content-understanding/import-sample-model.png) </br>

3. Po zakończeniu importowania zostanie otwarta strona główna modelu **BenefitsChangeNotice** . Jeśli w przyszłości będzie konieczne otwarcie przykładowego modelu, możesz to zrobić z listy modeli w centrum zawartości. </br>

     ![Przykładowa strona główna.](../media/content-understanding/sample-home-page.png)</br>

Możesz nie tylko przeanalizować przykładowy model, aby lepiej zrozumieć sposób skonstruowania modelu, ale także jako model roboczy wykonać inne czynności, takie jak:

- Dodaj kolejny wyodrębniator. Na przykład dodaj ten, który wyodrębnia *opłatę rabatową*.
- Zastosuj model do biblioteki dokumentów i przekaż do niego niektóre pliki szkoleniowe, aby zobaczyć, jak model klasyfikuje pliki i wyodrębnia z nich dane.

## <a name="get-sample-models"></a>Pobierz przykładowe modele

Możesz uzyskać dostęp do [repozytorium SharePoint Syntex Przykłady](https://github.com/pnp/syntex-samples) społeczności, które przedstawia różne wzorce użytkowania modeli opisów dokumentów. Przykłady w tym repozytorium zawierają zarówno dokument opisowy pliki modelu, jak i pliki służące do przeszkolinia modelu. Po zaimportowaniu możesz używać tych modeli do przetwarzania plików oraz do wyświetlania i edytowania klasyfikatorów i wyodrębniaczy.

## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)  
