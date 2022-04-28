---
title: Optymalizowanie wagi strony na nowoczesnych stronach witryny usługi SharePoint Online
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
description: Dowiedz się, jak za pomocą narzędzia diagnostyki strony zoptymalizować wagę strony na nowoczesnych stronach witryny SharePoint Online.
ms.openlocfilehash: 01a1976972983cccf3e93006e395f789d5882eff
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101210"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a>Optymalizowanie wagi strony na nowoczesnych stronach witryny usługi SharePoint Online

SharePoint Nowoczesne strony witryny online zawierają serializowany kod, który jest wymagany do renderowania zawartości strony, w tym obrazów, tekstu, obiektów w obszarze zawartości poniżej pasków nawigacji/poleceń i innego kodu HTML, który tworzy strukturę strony. Waga strony jest miarą tego kodu HTML i powinna być ograniczona w celu zapewnienia optymalnego czasu ładowania strony.

Ten artykuł pomoże Ci zrozumieć, jak zmniejszyć wagę strony na nowoczesnych stronach witryny.

>[!NOTE]
>Aby uzyskać więcej informacji na temat wydajności nowoczesnych portali usługi SharePoint Online, zobacz [Wydajność w nowoczesnym środowisku SharePoint](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a>Analizowanie wagi strony przy użyciu narzędzia Diagnostyka strony dla SharePoint

Narzędzie Diagnostyka strony dla SharePoint jest rozszerzeniem przeglądarki dla nowych Microsoft Edge (https://www.microsoft.com/edge)i przeglądarek Chrome, które analizują zarówno nowoczesne strony SharePoint Online, jak i klasyczne strony witryn publikowania. Narzędzie udostępnia raport dla każdej analizowanej strony pokazujący sposób działania strony względem zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować i dowiedzieć się więcej o narzędziu Diagnostyka strony dla SharePoint, odwiedź stronę [Korzystanie z narzędzia diagnostyki strony dla SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Narzędzie diagnostyki strony działa tylko dla SharePoint Online i nie może być używane na stronie systemu SharePoint.

Podczas analizowania strony witryny SharePoint za pomocą narzędzia Diagnostyka strony dla SharePoint można wyświetlić informacje o stronie w wyniku **500 KB** strony w okienku _Testy diagnostyczne_. Wynik zostanie wyświetlony na zielono, jeśli waga strony znajduje się poniżej wartości odniesienia, i czerwona, jeśli waga strony przekroczy wartość punktu odniesienia.

Możliwe wyniki obejmują:

- **Wymagana uwaga (czerwona** ): waga strony przekracza 500 KB
- **Nie jest wymagana żadna akcja** (kolor zielony): waga strony jest poniżej 500 KB

Jeśli w sekcji **Wymagana uwaga** zostanie wyświetlony wynik **Waga strony poniżej 500 KB**, możesz kliknąć wynik, aby uzyskać szczegółowe informacje.

![Żądania SharePoint wyników.](../media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a>Korygowanie problemów z wagą strony

Jeśli waga strony przekroczy 500 KB, możesz skrócić ogólny czas ładowania strony, zmniejszając liczbę składników Web Part i ograniczając zawartość strony do odpowiedniego stopnia.

Ogólne wskazówki dotyczące zmniejszania wagi strony obejmują:

- Ogranicz zawartość strony do rozsądnej ilości i użyj wielu stron do powiązanej zawartości.
- Zminimalizuj użycie składników Web Part, które mają duże torby właściwości.
- Jeśli to możliwe, użyj nieinterakcyjnych widoków zestawienia.
- Zoptymalizuj rozmiary obrazów, odpowiednio określając rozmiary obrazów, używając skompresowanych formatów obrazów i zapewniając, że są one pobierane z CDN.

Dodatkowe wskazówki dotyczące ograniczania wagi strony można znaleźć w następującym artykule:

- [Optymalizowanie wydajności strony w SharePoint](/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

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