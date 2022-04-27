---
title: limity witryn nowoczesnego portalu SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
description: Dowiedz się więcej na temat zaleceń dotyczących wydajności nowoczesnych witryn w usłudze SharePoint Online, takich jak ograniczanie wywołań do SharePoint i zewnętrznych punktów końcowych.
ms.openlocfilehash: a0163cd808ce3eb25da8d1c94fb27ed9d238d75a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091154"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>limity witryn nowoczesnego portalu SharePoint Online

Ten artykuł zawiera zalecenia dotyczące wydajności nowoczesnych witryn portalu w usłudze SharePoint Online. Skorzystaj z wytycznych w tym artykule, aby zoptymalizować wydajność nowoczesnej witryny portalu i uniknąć typowych problemów z wydajnością.

## <a name="performance-considerations-for-modern-portal-sites"></a>Zagadnienia dotyczące wydajności nowoczesnych witryn portalu

Z punktu widzenia optymalizacji wydajności istnieje kilka cech, które sprawiają, że nowoczesne witryny portalu są unikatowe. Główna różnica między witrynami współpracy i portalu w SharePoint Online jest skalowana. Ogólnie oczekuje się, że witryny portalu będą obsługiwać więcej widoków stron dla większej liczby użytkowników niż witryny współpracy i prawdopodobnie będą zawierać więcej zawartości statycznej i mniej edytowalnych zasobów. Ponadto architektura nowoczesnych lokacji różni się od lokacji klasycznych, ponieważ większość przetwarzania związanego z renderowaniem stron i wykonywaniem kodu odbywa się na kliencie, a nie na serwerze.

Optymalizacja wydajności dla nowoczesnych witryn portali koncentruje się przede wszystkim na kilku ogólnych celach:

- Zmniejsz całkowity rozmiar składników każdej strony witryny
- Odciąż hosting typowych plików statycznych, takich jak obrazy, arkusze stylów i skrypty, aby CDN
- Ograniczanie wywołań do SharePoint i zewnętrznych punktów końcowych tylko do tego, co jest konieczne
- Unikaj zduplikowanych żądań dotyczących tej samej zawartości

Wiele wytycznych w tym artykule koncentruje się na minimalizowaniu i optymalizowaniu wywołań SharePoint Online. Wykonywanie powtarzających się wywołań przy każdym załadowaniu strony będzie miało wpływ na wydajność użytkowników, ponieważ informacje będą pobierane z usługi za każdym razem, nawet jeśli nie uległy zmianie. W związku z tym żądania SharePoint można podzielić na wywołania typowe dla wszystkich użytkowników lub wywołania wymagane dla każdego użytkownika. Wyniki z tych dwóch kategorii wywołań powinny być buforowane w celu zoptymalizowania środowiska użytkownika.

>[!NOTE]
>Użyj [narzędzia Diagnostyka strony dla SharePoint](./page-diagnostics-for-spo.md) jako punktu początkowego do analizowania określonych metryk wydajności na stronach witryny usługi SharePoint Online.

## <a name="modern-portal-site-limits-and-recommendations"></a>Limity i zalecenia dotyczące witryny nowoczesnego portalu

|**Limit**|**Maksymalna zalecana wartość**|**Uwagi**|
|:-----|:-----|:-----|:-----|
|Strony i elementy wiadomości  <br/> |5000 na witrynę  <br/> |Zalecamy ograniczenie liczby stron i elementów wiadomości w nowoczesnej witrynie portalu do poniżej 5000.  <br/> |
|Składniki Web Part na stronie  <br/> |20 na stronę  <br/> |Zalecamy użycie co najmniej 20 składników Web Part na stronę, w tym zarówno wbudowanych składników Web Part firmy Microsoft, jak i niestandardowych składników Web Part. <br/> Aby uzyskać więcej informacji, zobacz [Optymalizowanie wydajności składników Web Part na stronach nowoczesnej witryny SharePoint Online](modern-web-part-optimization.md).  <br/> |
|Dynamiczne składniki Web Part na stronie  <br/> |4 na stronę  <br/> |Dynamiczne składniki Web Part, które wysyłają co najmniej jedno zapytanie do SharePoint w celu pobrania najnowszych danych, powinny być ograniczone do 4 na stronę. Składnik Web Part _Wiadomości_ jest przykładem dynamicznego składnika Web Part. <br/> Aby uzyskać więcej informacji, zobacz [Optymalizowanie wydajności składników Web Part na stronach nowoczesnej witryny SharePoint Online](modern-web-part-optimization.md).    <br/> |
|Grupy zabezpieczeń  <br/> |20 na witrynę  <br/> |Liczba grup zabezpieczeń wpływa na skalę wielu zapytań w nowoczesnych witrynach portalu. Zalecamy ograniczenie liczby grup zabezpieczeń do możliwie najmniejszego zestawu z maksymalnie 20 grupami zabezpieczeń na lokację.  <br/> |
|Elementy w nawigacji w witrynie  <br/> |100 na witrynę  <br/> |Zalecamy dodanie mniej niż 100 elementów do nawigacji w witrynie i użycie wbudowanych kontrolek nawigacji.  <br/> Aby uzyskać więcej informacji, zobacz [Optimize page weight in SharePoint Online modern site pages (Optymalizowanie wagi strony w nowoczesnej witrynie usługi SharePoint Online](modern-page-weight-optimization.md)). <br/> |
|Maksymalny rozmiar obrazu  <br/> |300 Kb na obraz  <br/> |Zalecamy ograniczenie rozmiaru obrazów do 300 kb lub mniejszego oraz użycie CDN do hostowania obrazów, arkuszy stylów i skryptów. <br/>Aby uzyskać więcej informacji, zobacz Optimize images in SharePoint Online modern site pages and Use the Office 365 Content Delivery Network (CDN) with SharePoint Online ([Optymalizowanie obrazów na nowoczesnych stronach witryny SharePoint Online](modern-image-optimization.md)) i [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online (Korzystanie z Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)).  <br/> |
|Użytkownicy z uprawnieniami do edycji  <br/> |200 użytkowników na witrynę  <br/> |SharePoint witryn portalu są zoptymalizowane pod kątem wyświetlania i używania zawartości. Uprawnienia do edycji w portalu powinny być ograniczone do ograniczonej grupy użytkowników, ponieważ uprawnienia do edycji pobierają dodatkowe kontrolki i w związku z tym będą działać wolniej dla tych użytkowników. W związku z tym nadmierna liczba użytkowników z uprawnieniami do edycji wpłynie na ogólne środowisko pracy. <br/> |
|Elementy iFrame innej firmy  <br/> |2 na stronę  <br/> |Elementy iFrame są nieprzewidywalnie powolne, ponieważ ładują oddzielną stronę zewnętrzną, w tym całą skojarzoną zawartość, taką jak javascript, CSS i elementy struktury. Jeśli musisz używać ramek iFrame, ogranicz ich liczbę do 2 lub mniej na stronę.<br/> Aby uzyskać więcej informacji, zobacz [Optimize iFrames in SharePoint Online modern and classic publishing site pages (Optymalizowanie ramek iFrame w nowoczesnych i klasycznych stronach witryny publikowania w usłudze SharePoint Online](modern-iframe-optimization.md)). <br/> |
|Wywołania usługi UPA  <br/> |1 na użytkownika na godzinę  <br/> |Zalecamy, aby nie wykonywać żadnych _wywołań na żądanie_ do usługi UPA (aplikacja profilu użytkownika). Narzędzia [Microsoft interfejs Graph API](/graph/call-api) i [PageContext](/javascript/api/sp-page-context/pagecontext) mogą służyć do wykonywania zapytań dotyczących informacji o użytkowniku.  <br/> Jeśli konieczne jest wywołanie usługi UPA, wykonaj pojedyncze wywołanie, gdy jest to wymagane, a następnie buforuj informacje do ponownego użycia w tej samej sesji. |
|Wywołania usługi taksonomii  <br/> |5 na użytkownika na godzinę  <br/> |Zalecamy, aby nie wykonywać żadnych _wywołań na żądanie_ do usługi Taksonomii. Jeśli wywołania usługi taksonomii są niezbędne, buforuj informacje do ponownego użycia w tej samej sesji. <br/> Aby uzyskać więcej informacji, zobacz [Optimize page calls in SharePoint Online modern and classic publishing site pages (Optymalizowanie wywołań stron w nowoczesnej i klasycznej witrynie publikowania w usłudze SharePoint Online](modern-page-call-optimization.md)). <br/> |

## <a name="related-topics"></a>Tematy pokrewne

[Tworzenie portalu SharePoint w dobrej kondycji](/sharepoint/portal-health)

[Dostrajanie wydajności usługi SharePoint Online](tune-sharepoint-online-performance.md)

[Dostrajanie wydajności Office 365](tune-microsoft-365-performance.md)

[limity usługi SharePoint Online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Wydajność w nowoczesnym środowisku SharePoint](/sharepoint/modern-experience-performance)

[Wskazówki dotyczące wydajności portali SharePoint Online](/sharepoint/dev/solution-guidance/portal-performance)
