---
title: Optymalizowanie połączeń stron na SharePoint nowoczesnych i klasycznych stron witryny publikowania w trybie online
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
description: Dowiedz się, jak zoptymalizować nowoczesne i klasyczne strony witryny publikowania w usłudze SharePoint Online przez ograniczenie liczby połączeń do SharePoint punktów końcowych usługi online.
ms.openlocfilehash: 298e928f339d82f472f73e22998b8762461cc209
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988371"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optymalizowanie połączeń stron na SharePoint nowoczesnych i klasycznych stron witryny publikowania w trybie online

Obie SharePoint nowoczesnych i klasycznych witryn publikowania w trybie online zawierają linki służące do ładowania danych z SharePoint i sieci CDN. Im więcej połączeń jest na stronie, tym dłużej trwa ładowanie strony. Jest to nazywane postrzegane **przez użytkownika końcowego opóźnieniem lub** **eupl**.

Ten artykuł pomoże Ci zrozumieć, jak ustalić liczbę i wpływ połączeń do zewnętrznych punktów końcowych z nowoczesnych i klasycznych stron witryny publikowania oraz jak ograniczyć ich wpływ na użytkownika końcowego odbierane opóźnienie.

>[!NOTE]
>Aby uzyskać więcej informacji na temat wydajności w nowoczesnych SharePoint Online, zobacz Wydajność w [nowoczesnym SharePoint sieci](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a>Używanie narzędzia Diagnostyka stron do SharePoint do analizowania połączeń stron

Narzędzie Diagnostyka stron dla programu SharePoint to rozszerzenie przeglądarki dla nowych przeglądarek Microsoft Edge (https://www.microsoft.com/edge)i Chrome), które analizuje zarówno nowoczesne portal SharePoint Online, jak i klasyczne strony witryn publikowania. To narzędzie udostępnia raport dla każdej analizowanej strony pokazujący, jak ta strona działa w stosunku do zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować narzędzie Diagnostyka stron dla SharePoint informacji, odwiedź stronę Używanie narzędzia Diagnostyka stron dla usługi [SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Narzędzie Diagnostyka stron działa tylko w SharePoint Online i nie można go używać na SharePoint stronie systemu.

Podczas analizowania strony SharePoint za pomocą narzędzia Diagnostyka strony dla usługi SharePoint można wyświetlić informacje o połączeniach zewnętrznych w okienku Żądania SharePoint w okienku _Testy diagnostyczne._  Jeśli strona witryny zawiera mniej połączeń, linia będzie wyświetlana w kolorze zielonym, a kolor czerwony, jeśli strona przekracza numer planu bazowego. Numer planu bazowego jest inny w przypadku stron nowoczesnych i klasycznych, ponieważ na klasycznych stronach witryny jest używanie protokołu HTTP1.1, a dla stron nowoczesnych jest użycie protokołu HTTP2.0:

- Nowoczesne strony witryny powinny zawierać nie więcej niż **25** połączeń
- Klasyczne strony publikowania powinny zawierać nie więcej niż **6** połączeń

Możliwe wyniki:

- **Wymagana uwaga** (kolor czerwony): strona przekracza podstawową liczbę połączeń
- **Nie jest wymagane żadne** działanie (kolor zielony): strona zawiera mniej niż podstawowa liczba połączeń

Jeśli sekcja Prośby o **SharePoint** zostanie wyświetlona w sekcji Wymagana uwaga, możesz kliknąć wynik, aby uzyskać szczegółowe informacje, w tym łączną liczbę połączeń na stronie i listę adresów URL.

![Prośby o SharePoint wyników.](../media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a>Rozwiązywanie problemów z wydajnością związanych ze zbyt wieloma połączeniami na stronie

Jeśli strona zawiera zbyt wiele połączeń, możesz użyć listy adresów URL w wynikach funkcji Żądania dostępu **do usługi SharePoint** w celu określenia, czy powtarzają się połączenia, połączenia powinny być wsadowe lub połączenia, które zwracają dane, które powinny być buforowane.

**Wsadowe połączenia REST** mogą zmniejszyć obciążenie związane z wydajnością. Aby uzyskać więcej informacji na temat partii połączeń interfejsu API, zobacz [Zawieranie żądań wsadowych przy użyciu interfejsów API usługi REST](/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).

**Użycie pamięci podręcznej** do przechowywania wyników wywołania interfejsu API może poprawić wydajność powitania, zezwalając klientowi na używanie danych z pamięci podręcznej zamiast wykonywania dodatkowego wywołania dla każdego kolejnego ładowania strony. Istnieje wiele sposobów podejścia do tego rozwiązania w zależności od wymagania biznesowego. Zazwyczaj, jeśli dane będą takie same dla wszystkich użytkowników, użycie usługi pamięci podręcznej średniej warstwy, takiej jak pamięć podręczna [_Azure Redis_](https://azure.microsoft.com/services/cache/), to doskonałe rozwiązanie do znacznego zmniejszenia ruchu interfejsu API w witrynie, ponieważ użytkownicy żądali danych z usługi pamięci podręcznej zamiast bezpośrednio z usługi SPO. Jedyne połączenia usługi SPO potrzebne do odświeżenia pamięci podręcznej warstwy środkowej. Jeśli dane będą podlegać  fluktuacji po stronie użytkownika, najlepszym rozwiązaniem może być zaimplementowanie pamięci podręcznej po stronie klienta, na przykład LocalStorage, a nawet pliku cookie. Będzie to nadal zmniejszać liczbę połączeń przez wyeliminowanie kolejnych żądań składanych przez tego samego użytkownika na potrzeby czasu trwania pamięci podręcznej, ale będzie mniej efektywne niż dedykowana usługa buforowania. PnP umożliwia korzystanie z localStorage z niewielkimi dodatkowymi wymaganiami programistyki.

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