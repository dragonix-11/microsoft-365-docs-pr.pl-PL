---
title: Optymalizowanie ramek iFrame na stronach nowoczesnej i klasycznej witryny publikowania w usłudze SharePoint Online
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Dowiedz się, jak zoptymalizować wydajność ramek iFrame na stronach nowoczesnej i klasycznej witryny publikowania w usłudze SharePoint Online.
ms.openlocfilehash: 0e8710b76d20388ba3514b32fe598e982a7a9561
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100704"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optymalizowanie ramek iFrame na stronach nowoczesnej i klasycznej witryny publikowania w usłudze SharePoint Online

Elementy iFrame mogą być przydatne do podglądu rozbudowanej zawartości, takiej jak filmy wideo lub inne nośniki. Jednak ponieważ elementy iFrame ładują oddzielną stronę na stronie witryny SharePoint, zawartość załadowana w elemencie iFrame może zawierać duże obrazy, filmy wideo lub inne elementy, które mogą przyczyniać się do ogólnego czasu ładowania strony i nie można kontrolować na stronie. Ten artykuł pomoże Ci zrozumieć, jak określić, w jaki sposób elementy iFrame na stronach wpływają na opóźnienie postrzegane przez użytkownika i jak rozwiązywać typowe problemy.

>[!NOTE]
>Aby uzyskać więcej informacji na temat wydajności nowoczesnych witryn usługi SharePoint Online, zobacz [Wydajność w nowoczesnym środowisku SharePoint](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>Używanie narzędzia Diagnostyka strony dla SharePoint do analizowania składników Web Part przy użyciu elementów iFrame

Narzędzie Diagnostyka strony dla SharePoint jest rozszerzeniem przeglądarki dla nowych Microsoft Edge (https://www.microsoft.com/edge)i przeglądarek Chrome, które analizują zarówno nowoczesne strony SharePoint Online, jak i klasyczne strony witryn publikowania. Narzędzie udostępnia raport dla każdej analizowanej strony pokazujący sposób działania strony względem zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować i dowiedzieć się więcej o narzędziu Diagnostyka strony dla SharePoint, odwiedź stronę [Korzystanie z narzędzia diagnostyki strony dla SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Narzędzie diagnostyki strony działa tylko dla SharePoint Online i nie może być używane na stronie systemu SharePoint.

Podczas analizowania strony witryny SharePoint za pomocą narzędzia Diagnostyka strony dla SharePoint można wyświetlić informacje o składnikach Web Part zawierających elementy iFrame w okienku _Testy diagnostyczne_. Metryka punktu odniesienia jest taka sama dla nowoczesnych i klasycznych stron.

Możliwe wyniki obejmują:

- **Wymagana uwaga** (czerwona): strona zawiera **co najmniej trzy** składniki Web Part korzystające z ramek iFrame
- **Możliwości poprawy** (żółty): strona zawiera **jeden lub dwa** składniki Web Part przy użyciu elementów iFrame
- **Nie jest wymagana żadna akcja** (kolor zielony): strona nie zawiera składników Web Part korzystających z elementów iFrame

Jeśli w sekcji **Możliwości poprawy** lub **Wymagana uwaga** w **wynikach zostaną wyświetlone składniki Web Part używające elementów iFrame**, możesz kliknąć wynik, aby wyświetlić składniki Web Part zawierające elementy iFrame.

![Wyniki narzędzia diagnostyki strony.](../media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>Korygowanie problemów z wydajnością elementu iFrame

Użyj **składników Web Part przy użyciu wykrytych elementów iFrame** , aby określić, które składniki Web Part zawierają elementy iFrame i mogą przyczyniać się do wydłużenia czasu ładowania strony.

Elementy iFrame są z natury powolne, ponieważ ładują oddzielną stronę zewnętrzną, w tym całą skojarzoną zawartość, taką jak javascript, CSS i elementy struktury, potencjalnie zwiększając obciążenie strony witryny o co najmniej dwa czynniki.

Postępuj zgodnie ze wskazówkami poniżej, aby zapewnić optymalne wykorzystanie ramek iFrame.

- Jeśli to możliwe, użyj obrazów zamiast ramek iFrame, jeśli wersja zapoznawcza jest mała na początek lub nieinterakcyjna.
- Jeśli elementy iFrame muszą być używane, zminimalizuj liczbę i/lub przenieś je z widoku.
- Osadzone pliki Office, takie jak Word, Excel i PowerPoint, są interaktywne, ale wolno się ładują. Miniatury obrazów z linkiem do pełnego dokumentu często będą działać lepiej.
- Osadzone filmy z YouTube i kanały twitterowe mają tendencję do lepszego działania w ramkach iFrame, ale używają tego rodzaju osadzania rozsądnie.
- Izolowane składniki Web Part są rozsądnym wyjątkiem, ale minimalizują ich liczbę i położenie w okienku widoków.
- Jeśli obiekt iFrame znajduje się poza portem widoków, rozważ użycie serwera _IntersectionObserver_ , aby opóźnić renderowanie elementu iFrame, dopóki nie zostanie on wyświetlony.

Przed wprowadzeniem poprawek strony w celu rozwiązania problemów z wydajnością zanotuj czas ładowania strony w wynikach analizy. Uruchom narzędzie ponownie po poprawce, aby sprawdzić, czy nowy wynik mieści się w standardowej linii bazowej, i sprawdź czas ładowania nowej strony, aby sprawdzić, czy nastąpiła poprawa.

![Wyniki czasu ładowania strony.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Czas ładowania strony może się różnić w zależności od różnych czynników, takich jak obciążenie sieci, godzina dnia i inne przejściowe warunki. Czas ładowania strony należy przetestować kilka razy przed wprowadzeniem zmian i po nich, aby ułatwić uśrednienie wyników.

## <a name="related-topics"></a>Tematy pokrewne

[Dostrajanie wydajności usługi SharePoint Online](tune-sharepoint-online-performance.md)

[Dostrajanie wydajności Office 365](tune-microsoft-365-performance.md)

[Wydajność w nowoczesnym środowisku SharePoint](/sharepoint/modern-experience-performance)