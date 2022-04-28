---
title: Optymalizowanie rozszerzeń niestandardowych na stronach nowoczesnej witryny usługi SharePoint Online
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Dowiedz się, jak zoptymalizować wydajność rozszerzeń niestandardowych na stronach nowoczesnej witryny usługi SharePoint Online.
ms.openlocfilehash: a31b6e68227d433359537b9655d68c63b5893cce
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093860"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a>Optymalizowanie wydajności rozszerzenia niestandardowego na stronach nowoczesnej witryny usługi SharePoint Online

Ten artykuł pomoże Ci zrozumieć, jak określić, w jaki sposób rozszerzenia niestandardowe wpływają na opóźnienie postrzegane przez użytkownika i jak rozwiązywać typowe problemy.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a>Analizowanie rozszerzeń niestandardowych za pomocą narzędzia Diagnostyka strony dla SharePoint

Narzędzie Diagnostyka strony dla SharePoint jest rozszerzeniem przeglądarki dla nowych Microsoft Edge (https://www.microsoft.com/edge)i przeglądarek Chrome, które analizują zarówno nowoczesne strony SharePoint Online, jak i klasyczne strony witryn publikowania. Narzędzie udostępnia raport dla każdej analizowanej strony pokazujący sposób działania strony względem zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować i dowiedzieć się więcej o narzędziu Diagnostyka strony dla SharePoint, odwiedź stronę [Korzystanie z narzędzia diagnostyki strony dla SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Narzędzie diagnostyki strony działa tylko dla SharePoint Online i nie może być używane na stronie systemu SharePoint.

Podczas analizowania strony witryny SharePoint za pomocą narzędzia Diagnostyka strony dla SharePoint można wyświetlić informacje o rozszerzeniach niestandardowych przekraczających metrykę punktu odniesienia w **rozszerzeniach, które mają wpływ na czas ładowania** i/lub zbyt **wiele używanych rozszerzeń** powoduje wyświetlenie _okienka Testy diagnostyczne_ 

Możliwe wyniki obejmują:

- **Wymagana uwaga (czerwona** ): każde _rozszerzenie niestandardowe_ , które trwa dłużej niż **jedna** sekunda. Łączny czas ładowania wyświetlany w wynikach testu jest podzielony według obciążenia modułu i init. Ponadto jeśli na stronie jest zbyt wiele rozszerzeń, mogą one mieć wpływ na czas ładowania strony i zostanie on wyróżniony, jeśli na stronie jest używanych **co najmniej siedem** rozszerzeń.
- **Szanse poprawy** (żółty) Jeśli jest używanych **co najmniej pięć** rozszerzeń, zostaną one wyróżnione w tej sekcji jako ostrzeżenie do czasu użycia co najmniej siedmiu rozszerzeń, które zostaną wyróżnione jako Wymagane do uwagi.
- **Nie jest wymagana żadna akcja** (kolor zielony): ładowanie rozszerzenia trwa dłużej niż jedna sekunda.

Jeśli rozszerzenie ma wpływ na czas ładowania strony lub na stronie jest zbyt wiele rozszerzeń, wynik zostanie wyświetlony w sekcji **Wymaganej uwagi** wyników. Kliknij wynik, aby wyświetlić szczegółowe informacje o tym, które rozszerzenie ładuje się powoli lub wyróżniono zbyt wiele rozszerzeń. Przyszłe aktualizacje narzędzia Diagnostyka strony dla SharePoint mogą obejmować aktualizacje reguł analizy, dlatego upewnij się, że zawsze masz najnowszą wersję narzędzia.

![Wyniki czasu ładowania strony.](../media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

Informacje dostępne w wynikach obejmują:

- **Nazwa i identyfikator** zawierają informacje identyfikujące, które mogą pomóc w znalezieniu rozszerzenia na stronie
- **Suma** pokazuje całkowity czas ładowania i inicjowania rozszerzenia do modułu. Jest to całkowity czas względny wykonywany przez rozszerzenie na stronie od początku do końca.
- **Ładowanie modułu** pokazuje czas potrzebny do pobrania, oceny i załadowania rozszerzeń plików JavaScript i CSS. Następnie rozpocznie się proces Init.
- **Init** pokazuje czas potrzebny na zainicjowanie danych przez rozszerzenie.

  Jest to wywołanie asynchroniczne i czas init jest obliczeniem czasu dla funkcji onInit po rozwiązaniu zwróconej obietnicy.

Te informacje ułatwiają projektantom i deweloperom rozwiązywanie problemów. Te informacje należy przekazać zespołowi projektowemu i programistycznemu.

## <a name="overview-of-extensions"></a>Omówienie rozszerzeń

rozszerzenia SharePoint Framework (SPFx) mogą służyć do rozszerzania środowiska użytkownika SharePoint. Dzięki SharePoint Framework Extensions możesz dostosować więcej aspektów środowiska SharePoint, w tym obszary powiadomień, paski narzędzi i widoki danych listy.

Rozszerzenia mogą mieć zły wpływ na wydajność strony SharePoint, ponieważ wymaga to również użycia procesora CPU i zasobów sieciowych.

Istnieją cztery typy rozszerzeń:

- **Konfiguratorzy aplikacji** dodają skrypty do strony i uzyskują dostęp do dobrze znanych symboli zastępczych elementów HTML i rozszerzają je o niestandardowe renderowanie.
- **Konfiguratorzy pól** udostępniają zmodyfikowane widoki danych dla pól na liście.
- **Zestawy poleceń** rozszerzają powierzchnie poleceń SharePoint w celu dodawania nowych akcji i udostępniają kod po stronie klienta, którego można użyć do implementowania zachowań.
- **Modyfikator zapytań wyszukiwania (tylko wersja zapoznawcza)** jest wywoływany tuż przed wykonaniem zapytania wyszukiwania.

## <a name="remediate-extension-performance-issues"></a>Korygowanie problemów z wydajnością rozszerzeń

Postępuj zgodnie ze wskazówkami w tej sekcji, aby zidentyfikować i rozwiązać problemy z wydajnością rozszerzeń wymienionych w **sekcji Rozszerzenia mają wpływ na wyniki czasu ładowania strony** .

>[!NOTE]
>Konfiguratory aplikacji mogą być wykonywane na wczesnym etapie cyklu życia strony i mogą mieć wpływ na wydajność innych rozszerzeń na stronie.

Wyniki inspekcji w narzędziu do diagnostyki strony będą wyświetlać dwa etapy wykonywania rozszerzenia w celu zidentyfikowania potencjalnego wpływu na wydajność.

- **Ładowanie modułu** to czas ładowania rozszerzenia, na który ma wpływ rozmiar rozszerzenia, dlatego dobrym pomysłem jest powiązanie tylko niezbędnych bibliotek w rozszerzeniu, a także wybranie lżejszych bibliotek.
- **Init** to czas inicjowania rozszerzenia, a deweloperzy rozszerzenia powinni rozważyć, czy rozszerzenie wykonuje niepotrzebną pracę, czy wykonuje zbyt wiele poleceń na etapie inicjowania.

Autorzy stron mogą również użyć wyniku inspekcji, aby sprawdzić, czy strona ma zbyt wiele rozszerzeń, ponieważ zbyt wiele rozszerzeń negatywnie wpłynie na wydajność strony.

- **Rozmiar rozszerzenia i zależności**
  - Użycie Office 365 CDN jest wymagane do optymalnego pobierania zasobów statycznych. Źródła publiczne CDN są preferowane w przypadku _plików js/css_. Aby uzyskać więcej informacji na temat korzystania z Office 365 CDN, zobacz [Korzystanie z Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Ponownie używaj struktur, takich jak _React_ i _importowanie sieci szkieletowej_, które są częścią SharePoint Framework (SPFx). Aby uzyskać więcej informacji, zobacz [Omówienie SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Upewnij się, że używasz najnowszej wersji SharePoint Framework i uaktualniasz je do nowych wersji w miarę ich udostępniania.
- **Pobieranie/buforowanie danych**
  - Jeśli rozszerzenie korzysta z dodatkowych wywołań serwera w celu pobrania danych do wyświetlania, upewnij się, że te interfejsy API serwera są szybkie i/lub implementują buforowanie po stronie klienta (na przykład przy użyciu _localStorage_ lub _IndexDB_ dla większych zestawów).
  - Jeśli do renderowania krytycznych danych jest wymaganych wiele wywołań, rozważ utworzenie partii na serwerze lub inne metody konsolidowania żądań do pojedynczego wywołania.
  - Alternatywnie, jeśli niektóre elementy danych wymagają wolniejszego interfejsu API, ale nie są krytyczne dla początkowego renderowania, należy je oddzielić od oddzielnego wywołania wykonywanego po renderowaniu krytycznych danych.
  - Jeśli wiele części używa tych samych danych, użyj wspólnej warstwy danych, aby uniknąć zduplikowanych wywołań.
- **Czas renderowania**
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