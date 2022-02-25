---
title: Microsoft 365 Tenant Isolation w programie Microsoft Graph i Delve
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: W tym artykule wyjaśnij, jak działa Microsoft 365 izolacji dzierżawy w Office Graph i w Delve.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 966f02726a2cce18e30e4d5bc7ab0beb5db51a29
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959261"
---
# <a name="microsoft-365-tenant-isolation-in-the-microsoft-graph-and-delve"></a>Microsoft 365 Tenant Isolation w programie Microsoft Graph i Delve

## <a name="tenant-isolation-in-the-microsoft-graph"></a>Tenant Isolation in the Microsoft Graph

Aktywność [modelu Graph firmy Microsoft](https://developer.microsoft.com/graph) w usługach Microsoft 365, w tym w usługach Exchange Online, SharePoint Online, Yammer, Skype dla firm i Azure Active Directory i nie tylko, oraz w usługach zewnętrznych, takich jak usługi firmy Microsoft innych firm lub innych firm. Microsoft Graph są używane w całym okresie Microsoft 365. Microsoft Graph reprezentuje zbiór zawartości i aktywności oraz relacje między nimi, które mają miejsce w całym pakiecie Office pakietu. Korzysta on z zaawansowanych technik uczenia maszynowego, aby łączyć ludzi z odpowiednią zawartością, konwersacjami i osobami wokół nich. Na przykład indeks dzierżawy w uścisku usługi SharePoint Online ma indeks usługi Microsoft Graph używany do obsługi zapytań programu Delve, aparat przetwarzania analizy w uścisku usługi SharePoint Online służy do przechowywania sygnałów i obliczania szczegółowych informacji, Exchange Online oblicza pamięć podręczną adresatów poszczególnych użytkowników jako dane wejściowe do analizy dzierżawy.

Witryna Microsoft Graph zawiera informacje o obiektach przedsiębiorstwa, takich jak osoby i dokumenty, a także o relacjach i interakcjach między tymi obiektami. Relacje i interakcje są reprezentowane jako *krawędzie*. Witryna Microsoft Graph segmentowana według dzierżawy, tak aby krawędzie istniały tylko między  węzłami w tej samej dzierżawie. Węzeł *to* jednostka z identyfikatorem URI, typem węzła, listą kontrolek dostępu i zestawem faset zawierających *metadane* i krawędzie. Każdy węzeł ma skojarzone metadane i krawędzie rozmieszczone w *fasetach* , tak jak w modelu wspólnej wiedzy. *Metadane* to właściwości przechowywane w węźle, których można używać do wyszukiwania, filtrowania lub analizowania w obrębie witryny firmy Microsoft Graph. *Faseta* to logiczny zbiór metadanych i krawędzi w węźle. Każdy aspekt opisuje jeden aspekt węzła. 

Witryna Microsoft Graph nie przeniosła wszystkich danych do pojedynczego repozytorium, a zamiast tego przechowuje metadane i relacje dotyczące danych, które mieszkają w innym miejscu. Witryna Microsoft Graph składa się z kilku magazynów danych i składników przetwarzania:

- Magazyn dzierżawy Graph udostępnia magazyn zbiorczy zoptymalizowany pod kątem efektywnej analizy.
- Pamięć podręczna zawartości aktywnej zapewnia szybki, losowy dostęp do aktywnego węzła i krawędzi, które są dostępne dla użytkowników.
- Router wejściowy powiadomi składniki wewnętrzne i zewnętrzne o zmianach na wykresie dzierżawy.

Analiza w ramach poszczególnych informacji deduce obciążenia istotnych dla obliczeń w całej dzierżawie i wypychanie ich na wykres dzierżawy. Przyczyny analizy dzierżawy dotyczące wszystkich działań w dzierżawie w celu uzyskania szczegółowych informacji na temat wzorców zachowania. Na przykład Exchange Online oblicza pamięć podręczną adresatów dla każdego użytkownika za pomocą analizy, która skutecznie oblicza powody dla skrzynek pocztowych poszczególnych użytkowników. Te analizy dla poszczególnych użytkowników dają zestaw krawędzi *adresatów Dla* każdej osoby, który jest wypychany na wykres dzierżawy. Dzięki temu jak najwięcej przetwarzania analiz jest możliwie jak najbardziej zbliżone do danych źródłowych.

## <a name="tenant-isolation-in-delve"></a>Izolacji dzierżawy w Delve

Jak wspomniano wcześniej, usługa Microsoft Graph umożliwia osobom odnajdowanie i współpracę nad bieżącymi działaniami w przedsiębiorstwie oraz zapewnia platformę encja-analiza, która umożliwia analizę zawartości i aktywności w obciążeniach pracą i nie tylko Microsoft 365. Delve to pierwsze takie środowisko obsługiwane przez microsoft Graph.
Delve to środowisko Microsoft 365 Sieci Web, które ujmuje zawartość od użytkowników Microsoft 365 Yammer Enterprise do Microsoft 365 za pośrednictwem witryny Microsoft Graph. Środowisko internetowe wyświetla dane w różnych tablicach z określonym tematem, takim jak *Popularne* wokół mnie lub *Zmodyfikowane przeze mnie*. Każda tablica składa się z kilku kart dokumentów z tekstem podsumowania i obrazem z dokumentu. Karta umożliwia użytkownikom czynności, takich jak otwarcie dokumentu Yammer strony głównej dokumentu. Istnieje strona dla każdej osoby w dzierżawie usługi Microsoft 365, która zawiera najbardziej istotne dokumenty dla tej osoby, oraz ikony, które mogą wywoływać Exchange Online lub Skype dla firm do interakcji z tą osobą. Ponieważ Delve jest oparty na interfejsie API microsoft Graph, jest on powiązany izolacjim tego interfejsu API opartym na dzierżawie.