---
title: Importowanie przykładowego modelu zrozumienia dokumentu dla usługi Microsoft SharePoint Syntex
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
description: Dowiedz się więcej o zrozumieniu modeli dokumentów za pośrednictwem przykładowego modelu.
ms.openlocfilehash: 210d5865a6e3208faff16fe1ce14748ee66d63c8
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916210"
---
# <a name="import-a-sample-document-understanding-model-for-microsoft-sharepoint-syntex"></a>Importowanie przykładowego modelu zrozumienia dokumentu dla usługi Microsoft SharePoint Syntex

SharePoint Syntex udostępnia przykładowy model, którego można użyć do zbadania, co zapewnia lepsze zrozumienie sposobu tworzenia własnych modeli. Przykładowy model umożliwia również badanie składników modelu, takich jak klasyfikator, wyodrębniacze i wyjaśnienia. Możesz również użyć przykładowych plików, aby wytrenować model.

## <a name="import-the-sample-model"></a>Importowanie przykładowego modelu

Aby uzyskać dostęp do przykładowego modelu, musisz najpierw zaimportować model do centrum zawartości.

1. W centrum zawartości wybierz pozycję **Modele** , aby wyświetlić listę modeli.</br>
2. Na stronie **Modele** wybierz pozycję **Importuj przykładowy model**.</br>

    ![Importuj przykładowy model.](../media/content-understanding/import-sample-model.png) </br>

3. Po zakończeniu importowania zostanie otwarta strona główna modelu **BenefitsChangeNotice** . Jeśli w przyszłości musisz otworzyć przykładowy model, możesz to zrobić z listy modeli w centrum zawartości. </br>

     ![Przykładowa strona główna.](../media/content-understanding/sample-home-page.png)</br>

Możesz nie tylko przeanalizować przykładowy model, aby lepiej zrozumieć sposób konstruowania modelu, ale jako model roboczy może pójść dalej i wykonywać takie czynności, jak:

- Dodaj inny wyodrębniacz. Na przykład dodaj taki, który wyodrębnia *opłatę rabatu*.
- Zastosuj model do biblioteki dokumentów i przekaż do niej niektóre pliki szkoleniowe, aby zobaczyć, jak model klasyfikuje pliki i wyodrębnia z nich dane.

## <a name="get-sample-models"></a>Pobieranie przykładowych modeli

Możesz uzyskać dostęp do [repozytorium SharePoint Syntex Samples](https://github.com/pnp/syntex-samples), które zawiera przykłady społeczności, które pokazują różne wzorce użycia modeli interpretacji dokumentów. Przykłady w tym repozytorium zawierają zarówno pliki modelu, jak i pliki używane do trenowania modelu. Po zaimportowaniu można użyć tych modeli do przetwarzania plików oraz wyświetlania i edytowania klasyfikatora i wyodrębniaczy.

## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Omówienie usługi Document Understanding](document-understanding-overview.md)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)  
