---
title: Optymalizowanie ramek iFrame SharePoint nowoczesnych i klasycznych stron witryny publikowania w trybie online
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Dowiedz się, jak zoptymalizować wydajność ramek iFrame w SharePoint nowoczesnych i klasycznych stron witryny publikowania w trybie online.
ms.openlocfilehash: e38dd3922444228cdf54c8ef306fbbd9eafb81c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984278"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optymalizowanie ramek iFrame SharePoint nowoczesnych i klasycznych stron witryny publikowania w trybie online

Ramki iFrame mogą być przydatne do wyświetlania podglądu zawartości sformatowanych, takiej jak klipy wideo lub inne multimedia. Ponieważ jednak elementy iFrame wczytują osobną stronę w obrębie strony witryny SharePoint, zawartość załadowana w elementach iFrame może zawierać duże obrazy, klipy wideo lub inne elementy, które mogą przyczyniać się do ogólnego ładowania strony i których nie można kontrolować na stronie. Ten artykuł pomoże Ci zrozumieć, jak określić, jak ramki iFrame na stronach wpływają na odbierane opóźnienia użytkowników i jak rozwiązać typowe problemy.

>[!NOTE]
>Aby uzyskać więcej informacji na temat wydajności w SharePoint witrynach nowoczesnych w trybie online, zobacz Wydajność [w nowoczesnym SharePoint witryn.](/sharepoint/modern-experience-performance)

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>Używanie narzędzia Diagnostyka stron dla SharePoint do analizowania składników Web Part za pomocą ramek iFrame

Narzędzie Diagnostyka stron dla programu SharePoint to rozszerzenie przeglądarki dla nowych przeglądarek Microsoft Edge (https://www.microsoft.com/edge)i Chrome), które analizuje zarówno nowoczesne portal SharePoint Online, jak i klasyczne strony witryn publikowania. To narzędzie udostępnia raport dla każdej analizowanej strony pokazujący, jak ta strona działa w stosunku do zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować narzędzie Diagnostyka stron dla SharePoint informacji, odwiedź stronę Używanie narzędzia Diagnostyka stron dla usługi [SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Narzędzie Diagnostyka stron działa tylko w SharePoint Online i nie można go używać na SharePoint stronie systemu.

Podczas analizowania strony SharePoint za pomocą narzędzia Diagnostyka SharePoint strony można wyświetlić informacje o elementach Web Part zawierających elementy iFrame w okienku _Testy_ diagnostyczne. Metryka planu bazowego jest taka sama w przypadku stron nowoczesnych i klasycznych.

Możliwe wyniki:

- **Wymagana uwaga** (kolor czerwony): strona zawiera **co najmniej trzy** składniki Web Part używające ramek iFrame
- **Możliwości udoskonalania** (kolor żółty): strona zawiera **jeden lub dwa** składniki Web Part używające ramek iFrame
- **Nie jest wymagane żadne działanie** (kolor zielony): strona nie zawiera składników Web Part używających elementów iFrame

Jeśli składników **Web Part** używające wyników wykrytych przez elementy iFrame pojawia  się w sekcji  Wymagane możliwości udoskonalania lub Uwaga), możesz kliknąć wynik, aby wyświetlić party Web Part zawierające elementy iFrame.

![Wyniki narzędzia Diagnostyka stron.](../media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>Rozwiązywanie problemów z wydajnością ramek iFrame

Używanie składników **Web Part przy użyciu** wyników wykrytych za pomocą ramek iFrame w narzędziu Diagnostyka stron do określenia, które części Web Part zawierają elementy iFrame i mogą skutkować wolnym czasem ładowania stron.

Ramki iFrame są z natury wolne, ponieważ ładują oddzielną stronę zewnętrzną, w tym całą skojarzoną z nią zawartość, taką jak kod JavaScript, CSS i elementy struktury, co potencjalnie zwiększa obciążenie strony witryny o współczynnik co najmniej dwa.

Postępuj zgodnie z poniższymi wskazówkami, aby zapewnić optymalne użycie ramek iFrame.

- Jeśli to możliwe, użyj obrazów zamiast ramek iFrame, jeśli podgląd jest mały, aby rozpocząć od lub nieinterakcyjnie.
- Jeśli musisz użyć ramek iFrame, zminimalizuj ich liczbę i/lub przenieś je poza rzutni.
- Osadzone Office, takie jak word, Excel i PowerPoint są interakcyjne, ale ich ładowanie jest powolne. Miniatury obrazów z linkiem do pełnego dokumentu często są lepsze.
- Osadzone klipy wideo z serwisu YouTube i kanały serwisu Twitter zwykle lepiej się w nich wykonują w przypadku ramek iFrame, ale korzystaj z tego rodzaju osadzania w sposób żmudny.
- Odizolowane części web part stanowią rozsądny wyjątek, ale minimalizują ich liczbę i położenie w rzutni.
- Jeśli element iFrame znajduje się poza rzutnią, rozważ opóźnienie renderowania  ramki iFrame do momentu jego wyświetlenia za pomocą serwera PrzecięciaOb.

Zanim dokonasz poprawek stron w celu rozwiązania problemów z wydajnością zanotuj czas ładowania stron w wynikach analizy. Uruchom ponownie narzędzie po poprawce, aby sprawdzić, czy nowy wynik nie jest w standardzie bazowym, i sprawdź czas ładowania nowej strony, aby sprawdzić, czy w programie Wiad.

![Wyniki czasu ładowania stron.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Czas ładowania stron może się różnić w zależności od różnych czynników, takich jak obciążenie sieci, godzina dnia i inne warunki przejściowy. Należy przetestować czas ładowania strony kilka razy przed wprowadzeniem zmian i po ich wymuseniu, aby ułatwić uśredninie wyników.

## <a name="related-topics"></a>Tematy pokrewne

[Dostosowywanie SharePoint online](tune-sharepoint-online-performance.md)

[Dostosowywanie Office 365 wydajności](tune-microsoft-365-performance.md)

[Wydajność w nowoczesnym SharePoint klienta](/sharepoint/modern-experience-performance)