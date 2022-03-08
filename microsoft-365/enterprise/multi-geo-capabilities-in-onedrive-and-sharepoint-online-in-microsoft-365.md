---
title: Funkcje multi-Geo Capabilities OneDrive i SharePoint Online
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
description: Rozszerz swoją Microsoft 365 o wiele regionów geograficznych dzięki możliwości multilokalizacji w u OneDrive Online.
ms.openlocfilehash: 778efca6035dad05ec9bc77298b888e50f381ca1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330037"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Funkcje multi-Geo Capabilities OneDrive i SharePoint Online

Funkcje multi-Geo w usługach OneDrive i SharePoint Online umożliwiają kontrolowanie udostępnionych zasobów, takich jak witryny SharePoint zespołu i skrzynki pocztowe grup Microsoft 365 przechowywane w miejscu w określonej lokalizacji geograficznej.

Każdy użytkownik, skrzynka pocztowa grupy i witryna SharePoint mają preferowaną lokalizację danych (PDL), która oznacza lokalizację geograficzną, w której mają być przechowywane powiązane dane. Dane osobowe użytkowników (skrzynki Exchange i konta OneDrive) wraz z dowolnymi grupami Microsoft 365 lub witrynami usługi SharePoint mogą być przechowywane w określonej lokalizacji geograficznej w celu spełnienia wymagań dotyczących przechowywania danych. Dla [poszczególnych lokalizacji geograficznych możesz określić różnych administratorów](add-a-sharepoint-geo-admin.md).

Użytkownicy uzyskają bezproblemowe środowisko podczas korzystania z usług Microsoft 365, w tym aplikacji Office, OneDrive i wyszukiwania. Aby [uzyskać szczegółowe informacje, zobacz Środowisko użytkownika w środowisku wielolokalowym](multi-geo-user-experience.md) .

## <a name="onedrive"></a>OneDrive

Ustawienia administracyjne poszczególnych OneDrive w lokalizacjach satelitarnych lub przenoszone przez administratora zgodnie [](move-onedrive-between-geo-locations.md) z jego plikami PDL. Pliki osobiste są następnie przechowywane w tej lokalizacji geograficznej, chociaż można je udostępniać użytkownikom w innych lokalizacjach geograficznych.

## <a name="sharepoint-sites-and-groups"></a>SharePoint witryny i grupy

Zarządzanie funkcją multi-Geo jest dostępne za pośrednictwem <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum SharePoint administracyjnego</a>. Szczegółowe informacje można znaleźć w odpowiednim [wpisie w blogu](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

Gdy użytkownik tworzy witrynę połączoną SharePoint w środowisku wielolokalowym, jego plik PDL jest używany do określenia lokalizacji geograficznej, w której witryna i skojarzona z nią skrzynka pocztowa grupy są tworzone. Jeśli wartość PDL użytkownika nie została ustawiona lub ustawiono lokalizację geograficzną, która nie została skonfigurowana jako lokalizacja satelitarna, witryna i skrzynka pocztowa są tworzone w lokalizacji centralnej.

Microsoft 365 inne niż Exchange, OneDrive, SharePoint i Teams nie są wielowymiarowe. Jednak grupy Microsoft 365 utworzone przez te usługi zostaną skonfigurowane przy użyciu pliku PDL twórcy i skrzynki pocztowej grupy usługi Exchange, SharePoint witryna będzie aprowizacji w odpowiednim miejscu geograficznym. 

## <a name="managing-the-multi-geo-environment"></a>Zarządzanie środowiskiem wielolokalowym

Konfigurowanie środowiska wielolokalowego i zarządzanie nimi odbywa się za pośrednictwem <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint administracyjnego</a>. 

![Zrzut ekranu przedstawiający stronę lokalizacje geograficzne w centrum SharePoint administracyjnego.](../media/sharepoint-multi-geo-admin-center.png)

(Niektóre akcje, takie jak przenoszenie witryny SharePoint lub witryny programu OneDrive wymagają programu Microsoft PowerShell).

## <a name="see-also"></a>Zobacz też

[Multi-Geo in SharePoint and Microsoft 365 Groups](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[Administrowanie środowiskiem wielolokalowym](administering-a-multi-geo-environment.md)

[SharePoint przydziałów magazynowania w środowiskach wielowymiarowych](sharepoint-multi-geo-storage-quota.md)

[Administrowanie Exchange Online w środowisku wielolokalowym](administering-exchange-online-multi-geo.md)
