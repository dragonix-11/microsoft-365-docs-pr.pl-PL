---
title: Optymalizowanie wydajności składników Web Part na SharePoint nowoczesnych stron witryny w trybie online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
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
description: Dowiedz się, jak za pomocą Diagnostyki stron zoptymalizować wydajność składników Web Part na SharePoint nowoczesnych stron witryny w trybie online.
ms.openlocfilehash: 15b15e56a1c490cab86f225c5784d8bb9adcb36e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977631"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a>Optymalizowanie wydajności składników Web Part na SharePoint nowoczesnych stron witryny w trybie online

SharePoint witryny w trybie online zawierają składników Web Part, które mogą przyczyniać się do ogólnego ładowania stron. Ten artykuł pomoże Ci zrozumieć, jak określić wpływ składników Web Part na strony na odbierane opóźnienia przez użytkownika i jak rozwiązać typowe problemy.

> [!NOTE]
> Aby uzyskać więcej informacji na temat wydajności w nowoczesnych SharePoint Online, zobacz Wydajność w [nowoczesnym SharePoint sieci](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a>Używanie narzędzia Diagnostyka stron do SharePoint do analizowania składników Web Part

Narzędzie Diagnostyka stron dla programu SharePoint to rozszerzenie przeglądarki dla nowych przeglądarek Microsoft Edge (https://www.microsoft.com/edge)i Chrome), które analizuje zarówno nowoczesne portal SharePoint Online, jak i klasyczne strony witryn publikowania. To narzędzie udostępnia raport dla każdej analizowanej strony pokazujący, jak ta strona działa w stosunku do zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować narzędzie Diagnostyka stron dla SharePoint informacji, odwiedź stronę Używanie narzędzia Diagnostyka stron dla usługi [SharePoint Online](page-diagnostics-for-spo.md).

> [!NOTE]
> Narzędzie Diagnostyka stron działa tylko w SharePoint Online i nie można go używać na SharePoint stronie systemu.

Podczas analizowania strony witryny usługi SharePoint za pomocą narzędzia Diagnostyka strony dla usługi SharePoint można wyświetlić informacje o składników Web Part, które przekraczają metrykę planu bazowego w tych częściach, wpływają  na czas ładowania strony w okienku Testy diagnostyczne.

Możliwe wyniki:

- **Wymagana uwaga** (kolor czerwony): każdy niestandardowy _składników Web Part_ widoczny w rzutni (widoczny na ekranie fragment strony, który jest ładowany jako pierwszy), którego ładowanie trwa dłużej niż **dwie** sekundy. Wszystkie _niestandardowe_ składników Web Part poza rzutnią, których ładowanie trwa dłużej niż **cztery** sekundy. Całkowity czas ładowania jest wyświetlany w wynikach testów i jest rozbity na obciążenie modułu, opóźnienie, init i renderowanie.
- **Możliwości udoskonalania** (kolor żółty): Elementy, które mogą mieć wpływ na czas ładowania strony, są widoczne w tej sekcji i powinny być przeglądane i monitorowane. Może to dotyczyć składników Web Part firmy Microsoft "out of the box" (OOTB). Wyniki dotyczące wszelkich składników Web Part firmy Microsoft pokazanych w tej sekcji są automatycznie raportowane do firmy Microsoft, więc **nie jest wymagane żadne działanie**. W przypadku bardzo wolnego działania na stronie należy rejestrować zgłoszenie do pomocy technicznej tylko w przypadku, gdy na tej stronie występują bardzo wolne wyniki, a wszystkie składników **Web Part firmy Microsoft** na tej stronie są wyświetlane w wynikach w sekcji Możliwości **udoskonalania** . Pamiętaj, że przyszła aktualizacja narzędzia SharePoint spowoduje dalsze podziały wyników na podstawie określonej konfiguracji składników Web Part firmy Microsoft.
- **Nie są wymagane żadne** działania (kolor zielony): Zwracanie danych nie trwa dłużej niż **dwie** sekundy.

Jeśli składników **Web Part** wpływają na czas ładowania strony jest wyświetlany w sekcji Uwaga wymagana lub Możliwości  udoskonalania wyników, kliknij wynik, aby wyświetlić szczegółowe informacje o tym, które składników Web Part są ładowane powoli. Przyszłe aktualizacje narzędzia Diagnostyka stron dla programu SharePoint mogą obejmować aktualizacje reguł analizy, dlatego upewnij się, że zawsze masz najnowszą wersję tego narzędzia.

![Wyniki narzędzia Diagnostyka stron.](../media/modern-portal-optimization/pagediag-web-part.png)

Dostępne w wynikach informacje obejmują:

- **Na stronie Made by** (Wykonane przez) pokazano, czy ten element web part jest niestandardowy, czy też ma format Microsoft OOTB.
- **Pola Nazwa i identyfikator** zawierają informacje identyfikujące, które mogą pomóc w odnalezieniu składników Web Part na stronie.
- **Suma** pokazuje całkowity czas ładowania, inicjowania i renderowania składników Web Part dla składników Web Part. Jest to całkowity względny czas renderowania na stronie przez ten element, od początku do końca.
- **Ładowanie modułu** pokazuje czas pobierania, oceniania i ładowania rozszerzeń JavaScript i plików CSS. Następnie rozpocznie się proces init.
- **Opóźnienie ładowanie pokazuje** czas odroczonego ładowania składników Web Part, które nie są widoczne w głównej sekcji strony. Istnieją pewne warunki, w których jest zbyt wiele składników Web Part do renderowania i są one w kolejce w celu zminimalizowania czasu ładowania strony.
- **Program Init** pokazuje czas inicjaliizacji danych przez ten element Web Part.

  Jest to asynchroniczne wywołanie, a czas init to obliczenie czasu dla funkcji onInit, gdy zwrócona obietnica zostanie rozwiązana.

- **Renderowanie** pokazuje czas renderowania interfejsu użytkownika (interfejsu użytkownika) po załadowaniu modułu i ukończeniu działania init.

  Czas wykonywania kodu JavaScript jest czas instalacji dom w dokumencie (stronie).
  Renderowanie asynchronicznych zasobów, na przykład obrazów, może zająć więcej czasu.

Te informacje są udostępniane projektantom i deweloperom w rozwiązywaniu problemów. Te informacje powinny być udostępniane zespołowi projektoweowi i zespołowi programistów.

## <a name="remediate-web-part-performance-issues"></a>Rozwiązywanie problemów z wydajnością składników Web Part

Postępuj zgodnie z wskazówkami w tej sekcji, aby zidentyfikować i rozwiązać problemy z wydajnością składników Web Part wymienionych w tych częściach wpływają na **wyniki ładowania** stron.

Istnieją trzy kategorie możliwych przyczyn niskiej wydajności składników Web Part. Skorzystaj z poniższych informacji, aby ustalić, które problemy dotyczą Twojego scenariusza, i rozwiązać je.

- Rozmiar skryptu i zależności składników Web Part
  - Zoptymalizuj początkowy skrypt renderowany w scenariuszu głównej linii tylko _pod kątem trybu wyświetlania_.
  - Przenieś rzadziejsze scenariusze i kod trybu edycji (na przykład okienko właściwości), aby rozdzielić fragmenty za pomocą instrukcji _import(_ ).
  - Przejrzyj zależności pliku _package.json_ , aby całkowicie usunąć martwy kod. Przenoszenie dowolnych zależności testowych/kompilacji tylko do devDependencies.
  - Korzystanie z Office 365 CDN jest wymagane do optymalnego pobierania zasobów statycznych. Pochodzenie CDN jest preferowane w przypadku _plików js/css_. Aby uzyskać więcej informacji na temat korzystania z Office 365 CDN, zobacz Używanie Office 365 Content Delivery Network [(CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Ponowne używanie ram, _takich jak React_ _i_ importy tkanin, które są częścią SharePoint Framework (SPFx). Aby uzyskać więcej informacji, [zobacz Omówienie SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Upewnij się, że korzystasz z najnowszej wersji pakietu SharePoint Framework i uaktualnij je do nowych wersji w przyszłych wersjach.
- Pobieranie i buforowanie danych
  - Jeśli część Web Part korzysta z dodatkowych wywołań serwera w celu pobrania danych w celu ich wyświetlenia, upewnij się, że te interfejsy API serwera są szybkie i/lub implementują buforowanie po stronie klienta (na przykład używanie _localStorage_ lub _IndexedDB_ w przypadku większych zestawów).
  - Jeśli do renderowania krytycznych danych jest wymaganych wiele połączeń, rozważ grupowanie na serwerze lub inne metody konsolidowania żądań w jednym wywołaniu.
  - Ewentualnie, jeśli niektóre elementy danych wymagają wolniejszego interfejsu API, ale nie są krytyczne do początkowego renderowania, oddziel je do oddzielnego wywołania, które jest wykonywane po renderowaniu krytycznych danych.
  - Jeśli wiele części używa tych samych danych, używaj wspólnej warstwy danych, aby uniknąć zduplikowanych połączeń.
- Czas renderowania
  - Wszelkie źródła multimediów, takie jak obrazy i klipy wideo, powinny mieć rozmiar do limitów kontenera, urządzenia i/lub sieci, aby uniknąć pobierania niepotrzebnych dużych zasobów. Aby uzyskać więcej informacji na temat zależności zawartości, zobacz Używanie Office 365 Content Delivery Network [(CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Unikaj wywołań interfejsu API, które powodują ponowne przepływy, złożone reguły CSS lub skomplikowane animacje. Aby uzyskać więcej informacji, zobacz [Minimalizowanie układu ponownego układu przeglądarki](https://developers.google.com/speed/docs/insights/browser-reflow).
  - Unikaj używania zadań uruchomionych w łańcuch, których wykonywanie jest długie. Zamiast tego należy rozdzielić długo wykonywane zadania na oddzielne kolejki. Aby uzyskać więcej informacji, zobacz [Optymalizowanie wykonywania kodu JavaScript](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).
  - Rezerwuj odpowiednie miejsce na asynchroniczne renderowanie multimediów lub elementów wizualnych, aby uniknąć pominiętych ramek i zacinania (znanego _również jako jank_).
  - Jeśli funkcja używana w określonej przeglądarce nie obsługuje renderowania, załaduj wypełnienie polyfill lub wyklucz uruchomiony kod zależny. Jeśli ta funkcja nie jest krytyczna, usuwaj zasoby, takie jak programy obsługi zdarzeń, aby uniknąć wycieków pamięci.

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
