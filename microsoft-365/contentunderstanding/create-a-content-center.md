---
title: Tworzenie centrum zawartości w aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.custom: admindeeplinkSPO
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się, jak utworzyć centrum zawartości w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: 0bab102ae440b8cf2c797458e7602c61794d0d06
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311595"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Tworzenie centrum zawartości w aplikacji Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

Do tworzenia modeli zrozumienia dokumentów i zarządzania nimi potrzebne jest najpierw centrum zawartości. Centrum zawartości to interfejs tworzenia modelu, który zawiera również informacje o modelach opublikowanych w bibliotekach dokumentów, do których zastosowano opublikowane modele.

   ![Wybierz bibliotekę dokumentów.](../media/content-understanding/content-center-page.png)

Podczas konfigurowania tworzysz domyślne centrum [zawartości](set-up-content-understanding.md). Jednak administrator SharePoint może również zdecydować się na utworzenie dodatkowych centrów w razie potrzeby. Mimo że pojedyncze centrum zawartości może być dobre dla środowisk, w których chcesz mieć rzutowanie wszystkich działań modelu, możesz chcieć mieć dodatkowe centra dla wielu działów w organizacji, które mogą mieć różne potrzeby i wymagania dotyczące uprawnień dla swoich modeli.

Ponadto, jeśli chcesz wypróbować tę SharePoint Syntex, możesz utworzyć centrum zawartości, korzystając z instrukcji podanych w tym artykule bez kupowania licencji. Nielicencjonowani użytkownicy mogą tworzyć modele opisowe dokumentów, ale nie mogą stosować ich do biblioteki dokumentów.

> [!NOTE]
> Jeśli [w Microsoft 365](../enterprise/microsoft-365-multi-geo.md) wielolokalizacji znajduje się jedno domyślne centrum zawartości, można udostępnić tylko rzutowanie aktywności modelu z poziomu tej lokalizacji. Obecnie nie można uzyskać rzutowania aktywności modelu w granicach farmy w środowisku z wieloma lokalizacjami geograficznymi. 

## <a name="create-a-content-center"></a>Tworzenie centrum zawartości

Administrator SharePoint może utworzyć witrynę centrum zawartości, tak jak każdą inną SharePoint za [](/sharepoint/create-site-collection) pomocą panelu inicjowania obsługi witryny centrum administracyjnego.

Aby utworzyć nowe centrum zawartości:

1. Na stronie centrum administracyjne platformy Microsoft 365 przejdź do centrum <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">administracyjnego usługi SharePoint w > **aktywne witryny**</a>.

2. Na stronie **Aktywne witryny** kliknij pozycję **Utwórz**, a następnie wybierz pozycję **Inne opcje**.

3. W menu **Wybierz szablon** wybierz pozycję **Centrum zawartości**.

4. Dla nowej witryny **podaj nazwę witryny**, **administratora podstawowego** i **język**.</br>

   > [!NOTE] 
   > Możesz wybrać witrynę centrum zawartości do renderowania w dowolnym z dostępnych języków, ale obecnie modele można tworzyć tylko dla plików w języku angielskim. Należy również pamiętać, że podobnie jak w przypadku innych szablonów witryn po utworzeniu witryny nie można edytować domyślnego języka witryny.

5. Wybierz **pozycję Gotowe**.
 
Po utworzeniu witryny centrum zawartości będzie ona wymieniona w pozycji Aktywne <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**witryny w centrum**</a> SharePoint administracyjnego. 

### <a name="give-access-to-additional-users"></a>Daj dostęp dodatkowym użytkownikom
 
Po utworzeniu witryny możesz udzielić dodatkowych użytkownikom dostępu do witryny za pomocą standardowego SharePoint [uprawnień witryny](/sharepoint/modern-experience-sharing-permissions).

### <a name="roll-up-of-models-in-the-default-content-center"></a>Rzutu modeli w domyślnym centrum zawartości

W SharePoint Syntex zawartości pierwszym centrum zawartości tworzonym podczas instalacji jest *domyślnym centrum zawartości*. W przypadku utworzenia kolejnych centrów zawartości ich modele są wyświetlane w domyślnym widoku centrum zawartości.

![Zrzut ekranu przedstawiający bibliotekę modeli w domyślnym centrum zawartości.](../media/content-understanding/model-library-default-content-center.png)

Biblioteka **Modele** w domyślnym widoku centrum zawartości grupuje utworzone modele przez centrum zawartości w celu wyświetlenia widoku podsumowania wszystkich utworzonych modeli dokumentów i modeli przetwarzania formularzy.

> [!NOTE]
> Nie można zmienić wyznaczonego domyślnego centrum zawartości. Zawsze jest to pierwsze centrum zawartości utworzone podczas instalacji. 

## <a name="see-also"></a>Zobacz też
[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Tworzenie centrum zawartości](create-a-content-center.md)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)

[Stosowanie modelu](apply-a-model.md)