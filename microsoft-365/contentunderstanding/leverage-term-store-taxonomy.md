---
title: Korzystanie z taksonomii magazynu terminów podczas tworzenia ekstraktora w usłudze Microsoft SharePoint Syntex
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
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: Użyj taksonomii magazynu terminów podczas tworzenia wyodrębniacza w modelu zrozumienia dokumentu w usłudze Microsoft SharePoint Syntex.
ms.openlocfilehash: d3f2acf32231558f9f56a62b18c6dd7ffbc4e20f
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861493"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>Korzystanie z taksonomii magazynu terminów podczas tworzenia ekstraktora w usłudze Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

Podczas tworzenia wyodrębniacza w modelu zrozumienia dokumentów przy użyciu SharePoint Syntex możesz skorzystać z globalnych zestawów terminów w [magazynie terminów](/sharepoint/managed-metadata), aby wyświetlić preferowane terminy wyodrębnianych danych.  

Na przykład model identyfikuje i klasyfikuje wszystkie dokumenty **umowy** przekazane do biblioteki dokumentów.  Ponadto model wyodrębnia również wartość **usługi kontraktu** z każdego kontraktu i wyświetli ją w kolumnie w widoku biblioteki. Wśród różnych wartości usług kontraktowych w umowach istnieje kilka starszych wartości, których firma już nie używa i których nazwa została zmieniona. Na przykład wszystkie odwołania do terminów *Projektowanie*, *Grafika* lub Usługi *kontraktowe topografii* powinny być teraz nazywane *kreatywnymi*. Za każdym razem, gdy model wyodrębnia jeden z nieaktualnych warunków z dokumentu kontraktu, chcesz wyświetlić bieżący termin — Creative — w widoku biblioteki. W poniższym przykładzie podczas trenowania modelu widzimy, że jeden przykładowy dokument zawiera nieaktualny termin *Projektowanie*.

   ![Magazyn terminów.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>Używanie kolumny Zarządzanych metadanych w wyodrębniaczu

Zestawy terminów są konfigurowane w magazynie terminów zarządzanych usług metadanych (MMS) w <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnym SharePoint</a>. W poniższym przykładzie [zestaw terminów](/sharepoint/managed-metadata#term-set) *Usług kontraktowych* jest skonfigurowany tak, aby zawierał kilka terminów, w tym *Creative*.  Szczegóły tego terminu pokazują, że termin ma trzy synonimy (*Design*, *Graphics* i *Topography*), a synonimy należy przetłumaczyć na *Creative*. 

   ![Zestaw terminów.](../media/content-understanding/term-store.png)</br>

Może istnieć wiele powodów, dla których warto użyć synonimu w zestawie terminów. Na przykład mogą istnieć nieaktualne terminy, zmieniono nazwy terminów lub różnice między działami organizacji w zakresie nazewnictwa.

Aby udostępnić pole zarządzanych metadanych do wybrania podczas tworzenia ekstraktora w modelu, należy [dodać je jako kolumnę witryny zarządzanych metadanych](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). Po dodaniu kolumny witryny można ją wybrać podczas tworzenia wyodrębniacza dla modelu.

   ![Usługa kontraktu.](../media/content-understanding/contract-services.png)</br>

Po zastosowaniu modelu do biblioteki dokumentów po przekazaniu dokumentów do biblioteki w kolumnie *Creative Services* zostanie wyświetlony preferowany termin (*Creative*), gdy wyodrębniacz znajdzie dowolną z wartości synonimów (*Design*, *Graphics* i *Topography*).

   ![Kolumna usługi kontraktu.](../media/content-understanding/creative.png)</br>

> [!NOTE]
> Jeśli zestaw terminów jest otwarty, wszystkie wyodrębnione wartości, które nie pasują do preferowanego terminu lub wartości synonimu, zostaną dodane jako nowy termin do katalogu głównego zestawu terminów. Te nowe terminy można przenosić, scalać lub tworzyć synonimy w magazynie terminów, w którym znajduje się zestaw terminów.

## <a name="see-also"></a>Zobacz też
[Wprowadzenie do zarządzanych metadanych](/sharepoint/managed-metadata#terms)

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Tworzenie kolumny zarządzanych metadanych](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)