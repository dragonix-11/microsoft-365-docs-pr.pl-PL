---
title: Optymalizowanie wywołań stron na stronach nowoczesnej i klasycznej witryny publikowania w usłudze SharePoint Online
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
description: Dowiedz się, jak zoptymalizować nowoczesne i klasyczne strony witryny publikowania w usłudze SharePoint Online, ograniczając liczbę wywołań do punktów końcowych usługi SharePoint Online.
ms.openlocfilehash: 7636e1cf2dfac6dc7fea4158f1f22a7336d6485e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101232"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optymalizowanie wywołań stron na stronach nowoczesnej i klasycznej witryny publikowania w usłudze SharePoint Online

Zarówno nowoczesne, jak i klasyczne witryny publikowania w usłudze SharePoint Online zawierają linki, które ładują dane z funkcji SharePoint i sieci CDN (lub do których są wywoływane). Tym więcej wywołań wykonywanych przez stronę, tym dłużej trwa ładowanie strony. Jest to **nazywane opóźnieniem postrzeganym przez użytkownika końcowego** lub **EUPL**.

Ten artykuł pomoże Ci zrozumieć, jak określić liczbę i wpływ wywołań zewnętrznych punktów końcowych na stronach nowoczesnej i klasycznej witryny publikowania oraz jak ograniczyć ich wpływ na opóźnienie postrzegane przez użytkownika końcowego.

>[!NOTE]
>Aby uzyskać więcej informacji na temat wydajności nowoczesnych portali usługi SharePoint Online, zobacz [Wydajność w nowoczesnym środowisku SharePoint](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a>Analizowanie wywołań stron przy użyciu narzędzia Diagnostyka strony dla SharePoint

Narzędzie Diagnostyka strony dla SharePoint jest rozszerzeniem przeglądarki dla nowych Microsoft Edge (https://www.microsoft.com/edge)i przeglądarek Chrome, które analizują zarówno nowoczesne strony SharePoint Online, jak i klasyczne strony witryn publikowania. Narzędzie udostępnia raport dla każdej analizowanej strony pokazujący sposób działania strony względem zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować i dowiedzieć się więcej o narzędziu Diagnostyka strony dla SharePoint, odwiedź stronę [Korzystanie z narzędzia diagnostyki strony dla SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Narzędzie diagnostyki strony działa tylko dla SharePoint Online i nie może być używane na stronie systemu SharePoint.

Podczas analizowania strony witryny SharePoint przy użyciu narzędzia Diagnostyka strony dla SharePoint można wyświetlić informacje o wywołaniach zewnętrznych w okienku **Żądania SharePoint** wyniku w okienku _Testy diagnostyczne_. Wiersz będzie wyświetlany na zielono, jeśli strona witryny zawiera mniejszą liczbę wywołań niż punkt odniesienia, a czerwona, jeśli strona przekroczy numer punktu odniesienia. Numer punktu odniesienia różni się w przypadku stron nowoczesnych i klasycznych, ponieważ klasyczne strony witryny używają protokołu HTTP1.1, a strony nowoczesne używają protokołu HTTP2.0:

- Nowoczesne strony witryny nie powinny zawierać więcej niż **25** wywołań
- Klasyczne strony publikowania nie powinny zawierać więcej niż **6** wywołań

Możliwe wyniki obejmują:

- **Wymagana uwaga** (czerwona): strona przekracza liczbę wywołań według planu bazowego
- **Nie jest wymagana żadna akcja** (kolor zielony): strona zawiera mniej niż liczba wywołań według planu bazowego

Jeśli wynik **Żądania SharePoint** zostanie wyświetlony w sekcji **Wymagana uwaga**, możesz kliknąć wynik, aby uzyskać szczegółowe informacje, w tym łączną liczbę wywołań na stronie i listę adresów URL.

![Żądania SharePoint wyników.](../media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a>Korygowanie problemów z wydajnością związanych ze zbyt dużą liczbą wywołań na stronie

Jeśli strona zawiera zbyt wiele wywołań, możesz użyć listy adresów URL w **żądaniach, aby SharePoint** wyniki, aby określić, czy istnieją powtarzające się wywołania, wywołania, które powinny być wsadowe, lub wywołania zwracające dane, które powinny być buforowane.

**Wsadowe wywołania REST** mogą pomóc zmniejszyć obciążenie wydajnością. Aby uzyskać więcej informacji na temat przetwarzania wsadowego wywołań interfejsu API, zobacz [Tworzenie żądań wsadowych za pomocą interfejsów API REST](/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).

**Użycie pamięci podręcznej** do przechowywania wyników wywołania interfejsu API może zwiększyć wydajność ciepłego żądania, umożliwiając klientowi korzystanie z buforowanych danych zamiast wykonywania dodatkowego wywołania dla każdego kolejnego ładowania strony. Istnieje wiele sposobów podejścia do tego rozwiązania w zależności od wymagań biznesowych. Zazwyczaj jeśli dane będą takie same dla wszystkich użytkowników, użycie usługi buforowania warstwy środkowej, takiej jak [pamięć podręczna _Azure Redis_](https://azure.microsoft.com/services/cache/), jest doskonałym rozwiązaniem do znacznego zmniejszenia ruchu interfejsu API w witrynie, ponieważ użytkownicy będą żądać danych z usługi buforowania, a nie bezpośrednio z sieci SPO. Jedynym wymaganym wywołaniem spo byłoby odświeżenie pamięci podręcznej warstwy środkowej. Jeśli dane będą się zmieniać dla poszczególnych użytkowników, najlepszym rozwiązaniem może być zaimplementowanie pamięci podręcznej po stronie klienta, takiej jak LocalStorage, a nawet plik cookie. Spowoduje to zmniejszenie liczby wywołań przez wyeliminowanie kolejnych żądań przez tego samego użytkownika na czas trwania pamięci podręcznej, ale będzie mniej wydajne niż dedykowana usługa buforowania. PnP umożliwia korzystanie z magazynu LocalStorage z niewielkimi dodatkowymi wymaganiami deweloperskimi.

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