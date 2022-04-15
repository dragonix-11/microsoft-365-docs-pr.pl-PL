---
title: Tworzenie centrum zawartości w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się, jak utworzyć centrum zawartości w usłudze Microsoft SharePoint Syntex.
ms.openlocfilehash: c630bba8bafad8bcbf9749e7a4d08ae1e86f4d68
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882225"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Tworzenie centrum zawartości w usłudze Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

Aby tworzyć modele zrozumienia dokumentów i zarządzać nimi, musisz najpierw utworzyć centrum zawartości. Centrum zawartości jest interfejsem tworzenia modelu i zawiera również informacje o tym, do których bibliotek dokumentów zostały zastosowane opublikowane modele.

   ![Wybierz bibliotekę dokumentów.](../media/content-understanding/content-center-page.png)

Podczas [instalacji](set-up-content-understanding.md) tworzysz domyślne centrum zawartości. Ale administrator SharePoint może również wybrać utworzenie dodatkowych centrów w razie potrzeby. Chociaż pojedyncze centrum zawartości może być odpowiednie dla środowisk, dla których chcesz utworzyć zestawienie wszystkich działań modelu, możesz mieć dodatkowe centra dla wielu działów w organizacji, które mogą mieć różne potrzeby i wymagania dotyczące uprawnień dla swoich modeli.

Ponadto, jeśli chcesz spróbować SharePoint Syntex, możesz utworzyć centrum zawartości, korzystając z instrukcji zawartych w tym artykule bez kupowania licencji. Użytkownicy nielicencjonowani mogą tworzyć modele zrozumienia dokumentów, ale nie mogą ich stosować do biblioteki dokumentów.

> [!NOTE]
> W [środowisku Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md), jeśli w centralnej lokalizacji znajduje się jedno domyślne centrum zawartości, możesz udostępnić tylko zestawienie aktywności modelu z tej lokalizacji. Obecnie nie można uzyskać zestawienia aktywności modelu ponad granicami farmy w środowisku multi-Geo. 

## <a name="create-a-content-center"></a>Tworzenie centrum zawartości

Administrator SharePoint może utworzyć witrynę centrum zawartości w taki sposób, aby [utworzyć dowolną inną witrynę SharePoint](/sharepoint/create-site-collection) za pośrednictwem panelu aprowizacji witryny centrum administracyjnego.

Aby utworzyć nowe centrum zawartości:

1. Na Centrum administracyjne platformy Microsoft 365 przejdź do <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">centrum administracyjnego SharePoint > **aktywne witryny**</a>.

2. Na stronie **Aktywne witryny** kliknij pozycję **Utwórz**, a następnie wybierz pozycję **Inne opcje**.

3. W menu **Wybierz szablon** wybierz pozycję **Centrum zawartości**.

4. W przypadku nowej witryny podaj **nazwę lokacji**, **administratora podstawowego** i **język**.</br>

   > [!NOTE] 
   > Możesz wybrać witrynę centrum zawartości do renderowania w dowolnym z dostępnych języków, ale należy pamiętać, że obecnie modele można tworzyć tylko dla plików angielskich. Należy również pamiętać, że podobnie jak w przypadku innych szablonów witryn, po utworzeniu witryny nie można edytować domyślnego języka witryny.

5. Wybierz pozycję **Zakończono**.
 
Po utworzeniu witryny centrum zawartości zostanie ona wyświetlona w <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**witrynach active**</a> w centrum administracyjnym SharePoint. 

### <a name="give-access-to-additional-users"></a>Udzielanie dostępu dodatkowym użytkownikom
 
Po utworzeniu witryny możesz udzielić dodatkowym użytkownikom dostępu do witryny za pośrednictwem standardowego [modelu uprawnień SharePoint lokacji](/sharepoint/modern-experience-sharing-permissions).

### <a name="roll-up-of-models-in-the-default-content-center"></a>Zestawienie modeli w domyślnym centrum zawartości

W SharePoint Syntex pierwszym centrum zawartości utworzonym podczas instalacji jest *domyślne centrum zawartości*. Jeśli zostaną utworzone kolejne centra zawartości, ich modele będą wyświetlane w domyślnym widoku centrum zawartości.

![Zrzut ekranu przedstawiający bibliotekę modelów w domyślnym centrum zawartości.](../media/content-understanding/model-library-default-content-center.png)

Biblioteka **Modele** w domyślnym widoku centrum zawartości grupuje utworzone modele według centrum zawartości, aby uzyskać widok podsumowania wszystkich modeli interpretacji dokumentów i modeli przetwarzania formularzy, które zostały utworzone.

> [!NOTE]
> Nie można zmienić wyznaczonego domyślnego centrum zawartości. Jest to zawsze pierwsze centrum zawartości utworzone podczas instalacji. 

## <a name="see-also"></a>Zobacz też

[Tworzenie klasyfikatora](create-a-classifier.md)

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Tworzenie centrum zawartości](create-a-content-center.md)

[Omówienie opisu dokumentu](document-understanding-overview.md)

[Tworzenie modelu przetwarzania formularzy](create-a-form-processing-model.md)

[Stosowanie modelu](apply-a-model.md)