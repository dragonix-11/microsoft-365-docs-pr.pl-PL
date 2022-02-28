---
title: Optymalizowanie obrazów na SharePoint nowoczesnych stronach witryny w trybie online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak używać narzędzi dostępnych w aplikacji SharePoint Online do optymalizowania obrazów na SharePoint nowoczesnych stronach witryny w trybie online.
ms.openlocfilehash: 85280dfc903c56c89308c50fa94979fd98b2003c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983948"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>Optymalizowanie obrazów na SharePoint nowoczesnych stronach witryny w trybie online

Ten artykuł pomoże Ci zrozumieć, jak optymalizować obrazy na SharePoint nowoczesnych stron witryny w trybie online.

Aby uzyskać informacje na temat optymalizowania obrazów w klasycznych witrynach publikowania, zobacz Optymalizacja [obrazów dla witryny SharePoint online](image-optimization-for-sharepoint-online.md).

>[!NOTE]
>Aby uzyskać więcej informacji na temat wydajności w nowoczesnych SharePoint Online, zobacz Wydajność w [nowoczesnym SharePoint sieci](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Używanie narzędzia Diagnostyka stron dla SharePoint do analizowania optymalizacji obrazów

Narzędzie Diagnostyka stron dla programu SharePoint to rozszerzenie przeglądarki dla nowych przeglądarek Microsoft Edge (https://www.microsoft.com/edge)i Chrome), które analizuje zarówno nowoczesne portal SharePoint Online, jak i klasyczne strony witryn publikowania. To narzędzie udostępnia raport dla każdej analizowanej strony pokazujący, jak ta strona działa w stosunku do zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować narzędzie Diagnostyka stron dla SharePoint informacji, odwiedź stronę Używanie narzędzia Diagnostyka stron dla usługi [SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Narzędzie Diagnostyka stron działa tylko w SharePoint Online i nie można go używać na SharePoint stronie systemu.

Podczas analizowania witryny SharePoint za pomocą narzędzia Diagnostyka SharePoint strony można wyświetlić informacje o dużych obrazach w _okienku Testy diagnostyczne_.

Możliwe wyniki:

- **Wymagana uwaga** (kolor czerwony): strona zawiera **co najmniej** jeden obraz o rozmiarze ponad 300 KB.
- **Nie jest wymagane żadne działanie** (kolor zielony): strona nie zawiera obrazów o rozmiarze ponad 300 KB.

Jeśli zostanie **wyświetlony wynik Duży wykryty obraz** w sekcji  Wymagana uwaga wyników, możesz kliknąć wynik, aby wyświetlić dodatkowe informacje.

![Wyniki narzędzia Diagnostyka stron.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Rozwiązywanie problemów z dużymi obrazami

Jeśli strona zawiera obrazy o rozmiarze ponad 300 KB, wybierz wynik w  przypadku dużych wykrytych obrazów, aby sprawdzić, które obrazy są za duże. W nowoczesnych SharePoint w trybie online odwzorowania obrazów są automatycznie udostępniane i zmieniane w zależności od rozmiaru okna przeglądarki i rozdzielczości monitora klienta. Obrazy należy zawsze optymalizować pod kątem użycia w sieci Web przed przekazaniem ich do witryny SharePoint Online. Bardzo duże obrazy zostaną automatycznie zmniejszone o rozmiar i rozdzielczość, co może spowodować nieoczekiwane cechy renderowania.

Zanim dokonasz poprawek stron w celu rozwiązania problemów z wydajnością zanotuj czas ładowania stron w wynikach analizy. Uruchom ponownie narzędzie po poprawce, aby sprawdzić, czy nowy wynik nie jest w standardzie bazowym, i sprawdź czas ładowania nowej strony, aby sprawdzić, czy w programie Wiad.

![Wyniki czasu ładowania stron.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Czas ładowania stron może się różnić w zależności od różnych czynników, takich jak obciążenie sieci, godzina dnia i inne warunki przejściowy. Należy przetestować czas ładowania strony kilka razy przed wprowadzeniem zmian i po ich wymuseniu, aby ułatwić uśredninie wyników.

## <a name="related-topics"></a>Tematy pokrewne

[Dostosowywanie SharePoint online](tune-sharepoint-online-performance.md)

[Dostosowywanie Office 365 wydajności](tune-microsoft-365-performance.md)

[Wydajność w nowoczesnym SharePoint klienta](/sharepoint/modern-experience-performance)

[Sieci dostarczania zawartości](content-delivery-networks.md)

[Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)