---
title: SharePoint nowoczesnych ograniczeń witryny portalu online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się więcej na temat zaleceń dotyczących wydajności dla nowoczesnych witryn w SharePoint Online, takich jak ograniczanie połączeń do SharePoint zewnętrznych punktów końcowych.
ms.openlocfilehash: 6d09af30f5bdc8866b44047771060ced86362565
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988635"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>SharePoint nowoczesnych ograniczeń witryny portalu online

Ten artykuł zawiera zalecenia dotyczące wydajności dla nowoczesnych witryn portali w SharePoint Online. Skorzystaj z wytycznych w tym artykule, aby zoptymalizować wydajność nowoczesnej witryny portalu i uniknąć typowych problemów z wydajnością.

## <a name="performance-considerations-for-modern-portal-sites"></a>Zagadnienia dotyczące wydajności nowoczesnych witryn portalu

Pod kątem optymalizacji wydajności istnieje kilka cech, które sprawiają, że nowoczesne witryny portalu są unikatowe. Główna różnica między współpracą a witrynami portali w u SharePoint Online to skala. Witryny portalu zazwyczaj powinny zawierać więcej widoków stron dla większej liczby użytkowników niż witryny współpracy i mogą zawierać więcej zawartości statycznej i mniej edytowalnych zasobów. Ponadto architektura nowoczesnych witryn różni się od witryn klasycznych tym, że większość przetwarzania związanego z renderowaniem stron i wykonywaniem kodu odbywa się na kliencie, a nie na serwerze.

Optymalizacja wydajności dla nowoczesnych witryn portalu dotyczy przede wszystkim kilku ogólnych celów:

- Zmniejszanie całkowitego rozmiaru składników każdej strony witryny
- Ładowanie hostingu typowych plików statycznych, takich jak obrazy, arkusze stylów i skrypty, CDN
- Ograniczanie połączeń do SharePoint i zewnętrznych punktów końcowych tylko do tego, co jest konieczne
- Unikanie zduplikowanych żądań dla tej samej zawartości

Wiele wytycznych w tym artykule dotyczy minimalizowania i optymalizowania połączeń z siecią SharePoint online. Wykonywanie powtarzających się połączeń za każdym razem, gdy strona jest ładowana, ma wpływ na wydajność, ponieważ informacje będą pobierane z usługi za każdym razem, nawet jeśli się nie zmieniły. W związku z tym żądania dotyczące SharePoint można kategoryzować jako połączenia wspólne dla wszystkich użytkowników lub połączenia wymagane dla poszczególnych użytkowników. Wyniki z tych dwóch kategorii połączeń powinny być przechowywane w pamięci podręcznej, aby zoptymalizować środowisko użytkownika.

>[!NOTE]
>Narzędzie [Diagnostyka stron dla SharePoint](./page-diagnostics-for-spo.md) punktem wyjścia do analizowania konkretnych metryk wydajności na stronach SharePoint w trybie online.

## <a name="modern-portal-site-limits-and-recommendations"></a>Nowoczesne ograniczenia i zalecenia dotyczące witryny portalu

|**Limit**|**Maksymalna zalecana wartość**|**Uwagi**|
|:-----|:-----|:-----|:-----|
|Strony i elementy wiadomości  <br/> |5000 na witrynę  <br/> |Zalecamy ograniczenie liczby stron i elementów wiadomości w nowoczesnej witrynie portalu do poniżej 5000.  <br/> |
|Składników Web Part na stronie  <br/> |20 na stronie  <br/> |Zalecamy używanie 20 lub mniejszej liczby składników Web Part na stronę, w tym zarówno od niestandardowych składników Web Part firmy Microsoft, jak i niestandardowych składników Web Part. <br/> Aby uzyskać więcej informacji, zobacz [Optymalizowanie wydajności składników Web Part w SharePoint nowoczesnych stron witryny w trybie online](modern-web-part-optimization.md).  <br/> |
|Dynamiczne składników Web Part na stronie  <br/> |4 na stronie  <br/> |Dynamiczne składników Web Part, które sprawiają, że co najmniej jedno SharePoint w celu pobrania najnowszych danych powinno być ograniczone do 4 na stronie. Przykładem _dynamicznego_ składników Web Part jest składników Web Part Wiadomości. <br/> Aby uzyskać więcej informacji, zobacz [Optymalizowanie wydajności składników Web Part w SharePoint nowoczesnych stron witryny w trybie online](modern-web-part-optimization.md).    <br/> |
|Grupy zabezpieczeń  <br/> |20 na witrynę  <br/> |Liczba grup zabezpieczeń wpływa na skalę wielu zapytań w nowoczesnych witrynach portalu. Zalecamy ograniczenie liczby grup zabezpieczeń do jak najmniejszego zestawu ( nie więcej niż 20 na witrynę).  <br/> |
|Elementy w nawigacji w witrynie  <br/> |100 na witrynę  <br/> |Zalecamy dodanie mniej niż 100 elementów do nawigacji w witrynie oraz użycie od urządzeniach, które są już w użyciu.  <br/> Aby uzyskać więcej informacji, zobacz [Optymalizowanie wagi stron w SharePoint nowoczesnych stron witryny w trybie online](modern-page-weight-optimization.md). <br/> |
|Maksymalny rozmiar obrazu  <br/> |300 Kb na obraz  <br/> |Zalecamy ograniczenie rozmiaru obrazów do 300 kb lub mniejszych oraz używanie CDN do hostowania obrazów, arkuszy stylów i skryptów. <br/>Aby uzyskać więcej informacji, zobacz Optymalizowanie obrazów na [SharePoint nowoczesnych](modern-image-optimization.md) stronach witryny w trybie online i Używanie Office 365 Content Delivery Network [(CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md).  <br/> |
|Użytkownicy z uprawnieniami do edytowania  <br/> |200 użytkowników na witrynę  <br/> |SharePoint witryn portali są zoptymalizowane pod kątem przeglądania i konsumowanie zawartości. Uprawnienia do edytowania w portalu powinny być ograniczone do grupy użytkowników z ograniczeniami, ponieważ uprawnienia do edycji pobierają dodatkowe kontrolki, przez co będą działać wolniej w przypadku tych użytkowników. Nadmiarowa liczba użytkowników z uprawnieniami do edytowania będzie mieć wpływ na ogólne środowisko użytkownika. <br/> |
|Ramki iFrame innych firm  <br/> |2 na stronie  <br/> |Ramki iFrame w nieprzewidywalny sposób spowalniają, ponieważ wczytują oddzielną stronę zewnętrzną, w tym całą skojarzoną zawartość, taką jak javascript, CSS i elementy struktury. Jeśli musisz użyć ramek iFrame, ogranicz ich liczbę do 2 lub mniejszej na stronie.<br/> Aby uzyskać więcej informacji, zobacz [Optymalizowanie ramek iFrame SharePoint nowoczesnych i klasycznych stron witryny publikowania w trybie online](modern-iframe-optimization.md). <br/> |
|Połączenia z usługą UPA  <br/> |1 na użytkownika na godzinę  <br/> |Nie zalecamy, aby na każde _żądanie_ dzwonić do usługi UPA (aplikacji profilu użytkownika). Interfejs [API Graph](/graph/call-api) i [PageContext](/javascript/api/sp-page-context/pagecontext) mogą być używane do wykonywania zapytań w celu wyszukiwania informacji o użytkownikach.  <br/> Jeśli jest konieczne połączenie z usługą UPA, w razie potrzeby możesz wykonać jedno połączenie, a następnie buforować informacje w celu ponownego użycia w tej samej sesji. |
|Połączenia z usługą Taksonomii  <br/> |5 na użytkownika na godzinę  <br/> |Nie zalecamy, aby na każde _żądanie_ dzwonić do usługi taksonomii. Jeśli jest konieczne wywołanie usługi taksonomii, należy buforować informacje w celu ponownego użycia w tej samej sesji. <br/> Aby uzyskać więcej informacji, zobacz [Optymalizowanie połączeń stron w SharePoint nowoczesnych i klasycznych stron witryny publikowania w trybie online](modern-page-call-optimization.md). <br/> |

## <a name="related-topics"></a>Tematy pokrewne

[Tworzenie zdrowego SharePoint portalu](/sharepoint/portal-health)

[Dostosowywanie SharePoint online](tune-sharepoint-online-performance.md)

[Dostosowywanie Office 365 wydajności](tune-microsoft-365-performance.md)

[SharePoint online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Wydajność w nowoczesnym SharePoint klienta](/sharepoint/modern-experience-performance)

[Wskazówki dotyczące wydajności SharePoint online](/sharepoint/dev/solution-guidance/portal-performance)
