---
title: Wykorzystaj taksonomię magazynu terminów podczas tworzenia wyodrębnianego programu w aplikacji Microsoft SharePoint Syntex
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
description: Taksonomia magazynu okresów jest używaj podczas tworzenia wyodrębnianego w dokumencie modelu rozumienia w programie Microsoft SharePoint Syntex.
ms.openlocfilehash: dd064a1e93692f79b5cfc5417b0b5b09df09c9fd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986650"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>Wykorzystaj taksonomię magazynu terminów podczas tworzenia wyodrębnianego programu w aplikacji Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

Po utworzeniu wyodrębnianego w dokumencie modelu rozumienia przy użyciu programu SharePoint Syntex można skorzystać z globalnych zestawów terminów w magazynie terminów, aby [](/sharepoint/managed-metadata) wyświetlić preferowane terminy dla wyodrębnianych danych.  

Na przykład model identyfikuje i klasyfikuje wszystkie dokumenty kontraktu,  które są przekazywane do biblioteki dokumentów.  Ponadto model wyodrębnia wartość usługi **kontraktowej** z każdej umowy i wyświetla ją w kolumnie w widoku biblioteki. Między innymi wartości usług kontraktowych w umowach znajduje się kilka starszych wartości, które nie są już używane w Twojej firmie i zostały zmienione. Na przykład teraz wszystkie odwołania do terminów *Projektowanie,* *Grafika* lub *Topografia* powinny mieć nazwę *Creative*. Za każdym razem, gdy model wyodrębnia jeden z przestarzałych terminów z dokumentu umowy, chcesz, aby w widoku biblioteki był wyświetlany bieżący termin — Creative. W poniższym przykładzie podczas szkolenia modelu widać, że jeden przykładowy dokument zawiera nieaktualny termin *"Projektowanie"*.

   ![Magazyn okresów.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>Używanie kolumny zarządzanych metadanych w wyodrębniarze

Zestawy okresów są konfigurowane w magazynie terminów usług zarządzanych metadanych (MMS, Managed Metadata services) w centrum SharePoint administracyjnego. W poniższym przykładzie zestaw terminów *usług* [kontraktowych](/sharepoint/managed-metadata#term-set) jest skonfigurowany tak, aby zawierał kilka terminów, w tym *Creative*.  Szczegóły tego terminu wskazują, że ten termin ma trzy synonimy *(Projektowanie**, Grafika* i *Topografia*), a synonimy należy przetłumaczyć *na creative*. 

   ![Zestaw okresów.](../media/content-understanding/term-store.png)</br>

Istnieje wiele powodów, dla których warto używać synonimu w zestawie terminów. Na przykład mogą być nieaktualne terminy, terminy o zmienionej nazwy lub odmiany między działami Twojej organizacji nad nazewnictwem.

Aby udostępnić pole zarządzanych metadanych do wyboru podczas tworzenia wyodrębnianego elementu w modelu, musisz dodać je jako kolumnę witryny zarządzanych [metadanych](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). Po dodaniu kolumny witryny można ją wybrać podczas tworzenia wyodrębnianego fragmentatora dla modelu.

   ![Usługa kontraktowa.](../media/content-understanding/contract-services.png)</br>

Po zastosowaniu modelu do biblioteki dokumentów po przesłaniu dokumentów do biblioteki w kolumnie *Usługi Creative Services* zostanie wyświetlany preferowany termin (*Creative*), gdy wyodrębniator znajdzie dowolną z wartości synonimów (*Projektowanie*, *Grafika* i *Topografia*).

   ![Kolumna Umowa usługi.](../media/content-understanding/creative.png)</br>


## <a name="see-also"></a>Zobacz też
[Wprowadzenie do zarządzanych metadanych](/sharepoint/managed-metadata#terms)

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Tworzenie kolumny zarządzanych metadanych](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)