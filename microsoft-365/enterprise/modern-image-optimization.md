---
title: Optymalizowanie obrazów na nowoczesnych stronach witryny usługi SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: Dowiedz się, jak używać narzędzi dostępnych w usłudze SharePoint Online do optymalizowania obrazów na nowoczesnych stronach witryny usługi SharePoint Online.
ms.openlocfilehash: 102555e25e48af19432a26e6e2a0cb17c78044b3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093838"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>Optymalizowanie obrazów na nowoczesnych stronach witryny usługi SharePoint Online

Ten artykuł pomoże Ci zrozumieć, jak zoptymalizować obrazy na nowoczesnych stronach witryny SharePoint Online.

Aby uzyskać informacje na temat optymalizacji obrazów w klasycznych witrynach publikowania, zobacz [Optymalizacja obrazów dla SharePoint Online](image-optimization-for-sharepoint-online.md)..

>[!NOTE]
>Aby uzyskać więcej informacji na temat wydajności nowoczesnych portali usługi SharePoint Online, zobacz [Wydajność w nowoczesnym środowisku SharePoint](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Analizowanie optymalizacji obrazów za pomocą narzędzia Diagnostyka strony dla SharePoint

Narzędzie Diagnostyka strony dla SharePoint jest rozszerzeniem przeglądarki dla nowych Microsoft Edge (https://www.microsoft.com/edge)i przeglądarek Chrome, które analizują zarówno nowoczesne strony SharePoint Online, jak i klasyczne strony witryn publikowania. Narzędzie udostępnia raport dla każdej analizowanej strony pokazujący sposób działania strony względem zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować i dowiedzieć się więcej o narzędziu Diagnostyka strony dla SharePoint, odwiedź stronę [Korzystanie z narzędzia diagnostyki strony dla SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Narzędzie diagnostyki strony działa tylko dla SharePoint Online i nie może być używane na stronie systemu SharePoint.

Podczas analizowania SharePoint nowoczesnej witryny przy użyciu narzędzia Diagnostyka strony dla SharePoint w okienku _Testy diagnostyczne_ można wyświetlić informacje o dużych obrazach.

Możliwe wyniki obejmują:

- **Wymagana uwaga** (czerwona): strona zawiera **co najmniej jeden** obraz o rozmiarze powyżej 300 KB
- **Nie jest wymagana żadna akcja** (kolor zielony): strona nie zawiera obrazów o rozmiarze powyżej 300 KB

Jeśli wynik **wykrytych dużych obrazów** zostanie **wyświetlony w sekcji Wymaganej uwagi** wyników, możesz kliknąć wynik, aby wyświetlić dodatkowe szczegóły.

![Wyniki narzędzia diagnostyki strony.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Korygowanie problemów z dużym obrazem

Jeśli strona zawiera obrazy o rozmiarze powyżej 300 KB, wybierz wynik **Wykryte duże obrazy** , aby zobaczyć, które obrazy są zbyt duże. Na nowoczesnych stronach SharePoint Online odwzorowania obrazów są automatycznie udostępniane i mają rozmiar w zależności od rozmiaru okna przeglądarki i rozdzielczości monitora klienta. Przed przekazaniem do usługi SharePoint Online należy zawsze optymalizować obrazy pod kątem korzystania z Internetu. Bardzo duże obrazy zostaną automatycznie zmniejszone w rozmiarze i rozdzielczości, co może spowodować nieoczekiwane cechy renderowania.

Przed wprowadzeniem poprawek strony w celu rozwiązania problemów z wydajnością zanotuj czas ładowania strony w wynikach analizy. Uruchom narzędzie ponownie po poprawce, aby sprawdzić, czy nowy wynik mieści się w standardowej linii bazowej, i sprawdź czas ładowania nowej strony, aby sprawdzić, czy nastąpiła poprawa.

![Wyniki czasu ładowania strony.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Czas ładowania strony może się różnić w zależności od różnych czynników, takich jak obciążenie sieci, godzina dnia i inne przejściowe warunki. Czas ładowania strony należy przetestować kilka razy przed wprowadzeniem zmian i po nich, aby ułatwić uśrednienie wyników.

## <a name="related-topics"></a>Tematy pokrewne

[Dostrajanie wydajności usługi SharePoint Online](tune-sharepoint-online-performance.md)

[Dostrajanie wydajności Office 365](tune-microsoft-365-performance.md)

[Wydajność w nowoczesnym środowisku SharePoint](/sharepoint/modern-experience-performance)

[Sieci dostarczania zawartości](content-delivery-networks.md)

[Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)