---
title: Możliwości wielu obszarów geograficznych w OneDrive i SharePoint Online
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Rozwiń swoją obecność Microsoft 365 do wielu regionów geograficznych przy użyciu funkcji wielu obszarów geograficznych w usłudze OneDrive Online.
ms.openlocfilehash: e49df6054e30e9e288e893da8d914ebb567eb8e5
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622238"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Możliwości wielu obszarów geograficznych w OneDrive i SharePoint Online

Funkcje multi-Geo w OneDrive i SharePoint Online umożliwiają kontrolę nad udostępnionymi zasobami, takimi jak witryny zespołu SharePoint i skrzynki pocztowe grupy Microsoft 365 przechowywane w spoczynku w określonej lokalizacji geograficznej.

Każdy użytkownik, skrzynka pocztowa grupy i witryna SharePoint mają preferowaną lokalizację danych (PDL), która oznacza lokalizację geograficzną, w której mają być przechowywane powiązane dane. Dane osobowe użytkowników (Exchange skrzynki pocztowej i OneDrive) wraz z Grupy Microsoft 365 lub SharePoint witrynami, które tworzą, mogą być przechowywane w określonej lokalizacji geograficznej w celu spełnienia wymagań dotyczących przechowywania danych. Dla [każdej lokalizacji geograficznej można określić różnych administratorów](add-a-sharepoint-geo-admin.md).

Użytkownicy mogą bezproblemowo korzystać z usług Microsoft 365, w tym aplikacji Office, OneDrive i wyszukiwania. Aby uzyskać szczegółowe informacje [, zobacz Środowisko użytkownika w środowisku z wieloma obszarami geograficznymi](multi-geo-user-experience.md) .

## <a name="onedrive"></a>OneDrive

OneDrive każdego użytkownika mogą być aprowizowane lub [przenoszone przez administratora](move-onedrive-between-geo-locations.md) do lokalizacji satelitarnej zgodnie z biblioteką PDL użytkownika. Pliki osobiste są następnie przechowywane w tej lokalizacji geograficznej, chociaż mogą być udostępniane użytkownikom w innych lokalizacjach geograficznych.

## <a name="sharepoint-sites-and-groups"></a>SharePoint lokacje i grupy

Zarządzanie funkcją Multi-Geo jest dostępne za pośrednictwem <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnego SharePoint</a>. Szczegółowe informacje można znaleźć w [odpowiednim wpisie w blogu](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

Gdy użytkownik tworzy lokację połączoną z grupą SharePoint w środowisku z wieloma lokalizacjami geograficznymi, jego biblioteka PDL jest używana do określania lokalizacji geograficznej, w której jest tworzona witryna i skojarzona z nią skrzynka pocztowa grupy. (Jeśli wartość PDL użytkownika nie została ustawiona lub została ustawiona na lokalizację geograficzną, która nie została skonfigurowana jako lokalizacja satelitarna, lokacja i skrzynka pocztowa są tworzone w centralnej lokalizacji).

usługi Microsoft 365 inne niż Exchange, OneDrive, SharePoint i Teams nie są multi-geo. Jednak Grupy Microsoft 365 tworzone przez te usługi zostaną skonfigurowane przy użyciu biblioteki PDL twórcy i skrzynki pocztowej grupy Exchange, SharePoint lokacja zostanie aprowizowana w odpowiednim obszarze geograficznym. 

## <a name="managing-the-multi-geo-environment"></a>Zarządzanie środowiskiem z wieloma lokalizacjami geograficznymi

Konfigurowanie środowiska z wieloma lokalizacjami geograficznymi i zarządzanie nim odbywa się za pośrednictwem <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnego SharePoint</a>. 

![Zrzut ekranu przedstawiający stronę lokalizacji geograficznych w centrum administracyjnym SharePoint.](../media/sharepoint-multi-geo-admin-center.png)

(Niektóre akcje, takie jak przeniesienie witryny SharePoint lub witryny OneDrive wymagają programu Microsoft PowerShell).

## <a name="see-also"></a>Zobacz też

[Multi-Geo w SharePoint i Grupy Microsoft 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[Administrowanie środowiskiem usługi Multi-Geo](administering-a-multi-geo-environment.md)

[SharePoint limity przydziału magazynu w środowiskach z wieloma lokalizacjami geograficznymi](sharepoint-multi-geo-storage-quota.md)

[Administrowanie skrzynkami pocztowymi Exchange Online w środowisku z wieloma lokalizacjami geograficznymi](administering-exchange-online-multi-geo.md)
