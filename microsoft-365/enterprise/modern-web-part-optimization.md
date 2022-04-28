---
title: Optymalizowanie wydajności składników Web Part na nowoczesnych stronach witryny usługi SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak za pomocą diagnostyki strony zoptymalizować wydajność składników Web Part na nowoczesnych stronach witryny SharePoint Online.
ms.openlocfilehash: 543ee889831d08b2b465c077cc391a653fa0b9a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093355"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a>Optymalizowanie wydajności składników Web Part na nowoczesnych stronach witryny usługi SharePoint Online

SharePoint Nowoczesne strony witryny online zawierają składniki Web Part, które mogą przyczynić się do ogólnego czasu ładowania stron. Ten artykuł pomoże Ci zrozumieć, jak określić, w jaki sposób składniki Web Part na stronach wpływają na opóźnienie postrzegane przez użytkownika oraz jak rozwiązywać typowe problemy.

> [!NOTE]
> Aby uzyskać więcej informacji na temat wydajności nowoczesnych portali usługi SharePoint Online, zobacz [Wydajność w nowoczesnym środowisku SharePoint](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a>Używanie narzędzia Diagnostyka strony dla SharePoint do analizowania składników Web Part

Narzędzie Diagnostyka strony dla SharePoint jest rozszerzeniem przeglądarki dla nowych Microsoft Edge (https://www.microsoft.com/edge)i przeglądarek Chrome, które analizują zarówno nowoczesne strony SharePoint Online, jak i klasyczne strony witryn publikowania. Narzędzie udostępnia raport dla każdej analizowanej strony pokazujący sposób działania strony względem zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować i dowiedzieć się więcej o narzędziu Diagnostyka strony dla SharePoint, odwiedź stronę [Korzystanie z narzędzia diagnostyki strony dla SharePoint Online](page-diagnostics-for-spo.md).

> [!NOTE]
> Narzędzie diagnostyki strony działa tylko dla SharePoint Online i nie może być używane na stronie systemu SharePoint.

Podczas analizowania strony witryny SharePoint za pomocą narzędzia Diagnostyka strony dla SharePoint można zobaczyć informacje o składnikach Web Part przekraczających metrykę punktu odniesienia w składnikach Web Part, które **mają wpływ na wynik czasu ładowania strony** w okienku _Testy diagnostyczne_.

Możliwe wyniki obejmują:

- **Wymagana uwaga (czerwona** ): _dowolny niestandardowy_ składnik Web Part widoczny w okienku widoków (widoczny na ekranie część strony, która jest ładowana jako pierwsza), który trwa dłużej niż **dwie** sekundy. Wszystkie _niestandardowe_ składniki Web Part poza portem widoków, które mogą być ładowane dłużej niż **cztery** sekundy. Łączny czas ładowania jest wyświetlany w wynikach testu i jest podzielony na obciążenia modułów, obciążenie z opóźnieniem, init i renderowanie.
- **Możliwości poprawy** (żółty): Elementy, które mogą mieć wpływ na czas ładowania strony, są wyświetlane w tej sekcji i powinny być przeglądane i monitorowane. Może to obejmować składniki Web Part firmy Microsoft "po wyjętej z pudełka" (OOTB). Wyniki dla wszystkich składników Web Part firmy Microsoft pokazanych w tej sekcji są automatycznie zgłaszane do firmy Microsoft, więc **nie jest wymagana żadna akcja**. Bilet pomocy technicznej na potrzeby badania należy rejestrować tylko wtedy, gdy na stronie występuje bardzo niska wydajność, a **wszystkie składniki Web Part firmy Microsoft** na stronie są wyświetlane w **wynikach w sekcji Możliwości poprawy** . Należy pamiętać, że przyszła aktualizacja narzędzia diagnostyki strony SharePoint dodatkowo podzieli wyniki na podstawie określonej konfiguracji składnika Web Part firmy Microsoft.
- **Nie jest wymagana żadna akcja** (kolor zielony): zwracanie danych przez żaden składnik Web Part nie trwa dłużej niż **dwie** sekundy.

Jeśli składnik **Web Part ma wpływ na wynik czasu ładowania strony** , zostanie wyświetlony w sekcji Wymagania **dotyczące uwagi** lub **Możliwości poprawy** wyników, kliknij wynik, aby wyświetlić szczegółowe informacje o tym, które składniki Web Part ładują się powoli. Przyszłe aktualizacje narzędzia Diagnostyka strony dla SharePoint mogą obejmować aktualizacje reguł analizy, dlatego upewnij się, że zawsze masz najnowszą wersję narzędzia.

![Wyniki narzędzia diagnostyki strony.](../media/modern-portal-optimization/pagediag-web-part.png)

Informacje dostępne w wynikach obejmują:

- **Wykonane przez** pokazuje, czy składnik Web Part jest niestandardowy, czy microsoft OOTB.
- **Nazwa i identyfikator** zawierają informacje identyfikujące, które mogą pomóc w znalezieniu składnika Web Part na stronie.
- **Suma** przedstawia całkowity czas ładowania, inicjowania i renderowania składnika Web Part. Jest to całkowity względny czas renderowania składnika Web Part na stronie od początku do końca.
- **Ładowanie modułu** pokazuje czas potrzebny do pobrania, oceny i załadowania rozszerzeń plików JavaScript i CSS. Następnie rozpocznie się proces Init.
- **Ładowanie z opóźnieniem** pokazuje czas odroczonego ładowania składników Web Part, które nie są widoczne w sekcji głównej strony. Istnieją pewne warunki, w których istnieje zbyt wiele składników Web Part do renderowania i są one umieszczane w kolejce do renderowania w celu zminimalizowania czasu ładowania strony.
- **Init** pokazuje czas potrzebny składnikowi Web Part na zainicjowanie danych.

  Jest to wywołanie asynchroniczne i czas init jest obliczeniem czasu dla funkcji onInit po rozwiązaniu zwróconej obietnicy.

- **Renderowanie** pokazuje czas potrzebny na renderowanie interfejsu użytkownika po zakończeniu ładowania modułu i inicjowania.

  Jest to czas wykonywania języka JavaScript, aby zainstalować dom w dokumencie (strona).
  Renderowanie zasobów asynchronicznych, na przykład obrazów, może zająć więcej czasu.

Te informacje ułatwiają projektantom i deweloperom rozwiązywanie problemów. Te informacje należy przekazać zespołowi projektowemu i programistycznemu.

## <a name="remediate-web-part-performance-issues"></a>Korygowanie problemów z wydajnością składników Web Part

Postępuj zgodnie ze wskazówkami w tej sekcji, aby zidentyfikować i rozwiązać problemy z wydajnością składników Web Part wymienione w **składnikach Web Part mają wpływ na wyniki czasu ładowania strony** .

Istnieją trzy kategorie możliwych przyczyn niskiej wydajności składników Web Part. Skorzystaj z poniższych informacji, aby określić, które problemy dotyczą twojego scenariusza, i skorygować je.

- Rozmiar i zależności skryptu składnika Web Part
  - Zoptymalizuj skrypt początkowy, który renderuje scenariusz linii głównej _tylko dla trybu wyświetlania_.
  - Przenieś rzadziej używane scenariusze i edytuj kod trybu (na przykład okienko właściwości) do oddzielnych fragmentów przy użyciu instrukcji _import(_ ).
  - Przejrzyj zależności pliku _package.json,_ aby całkowicie usunąć utracony kod. Przenieś wszystkie zależności tylko do testowania/kompilacji do devDependencies.
  - Użycie Office 365 CDN jest wymagane do optymalnego pobierania zasobów statycznych. Źródła publiczne CDN są preferowane w przypadku _plików js/css_. Aby uzyskać więcej informacji na temat korzystania z Office 365 CDN, zobacz [Korzystanie z Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Ponownie używaj struktur, takich jak _React_ i _importowanie sieci szkieletowej_, które są częścią SharePoint Framework (SPFx). Aby uzyskać więcej informacji, zobacz [Omówienie SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Upewnij się, że używasz najnowszej wersji SharePoint Framework i uaktualniasz je do nowych wersji w miarę ich udostępniania.
- Pobieranie/buforowanie danych
  - Jeśli składnik Web Part korzysta z dodatkowych wywołań serwera w celu pobrania danych do wyświetlenia, upewnij się, że te interfejsy API serwera są szybkie i/lub implementują buforowanie po stronie klienta (na przykład przy użyciu _localStorage_ lub _IndexedDB_ dla większych zestawów).
  - Jeśli do renderowania krytycznych danych jest wymaganych wiele wywołań, rozważ utworzenie partii na serwerze lub inne metody konsolidowania żądań do pojedynczego wywołania.
  - Alternatywnie, jeśli niektóre elementy danych wymagają wolniejszego interfejsu API, ale nie są krytyczne dla początkowego renderowania, należy je oddzielić od oddzielnego wywołania wykonywanego po renderowaniu krytycznych danych.
  - Jeśli wiele części używa tych samych danych, użyj wspólnej warstwy danych, aby uniknąć zduplikowanych wywołań.
- Czas renderowania
  - Wszystkie źródła multimediów, takie jak obrazy i filmy wideo, powinny mieć rozmiar do granic kontenera, urządzenia i/lub sieci, aby uniknąć pobierania niepotrzebnych dużych zasobów. Aby uzyskać więcej informacji na temat zależności zawartości, zobacz [Korzystanie z Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Unikaj wywołań interfejsu API, które powodują ponowne przepływy, złożone reguły CSS lub skomplikowane animacje. Aby uzyskać więcej informacji, zobacz [Minimizing browser reflow (Minimalizowanie ponownego przepływu przeglądarki](https://developers.google.com/speed/docs/insights/browser-reflow)).
  - Unikaj używania długotrwałych zadań łańcuchowych. Zamiast tego podziel długotrwałe zadania na oddzielne kolejki. Aby uzyskać więcej informacji, zobacz [Optymalizowanie wykonywania języka JavaScript](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).
  - Zarezerwuj odpowiednie miejsce na asynchroniczne renderowanie multimediów lub elementów wizualnych, aby uniknąć pominięcia ramek i jąkania (znanego również jako _jank_).
  - Jeśli określona przeglądarka nie obsługuje funkcji używanej w renderowaniu, załaduj wypełnienie lub wyklucz uruchomiony kod zależny. Jeśli funkcja nie jest krytyczna, należy usunąć zasoby, takie jak programy obsługi zdarzeń, aby uniknąć przecieków pamięci.

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
