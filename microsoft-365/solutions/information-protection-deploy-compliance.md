---
title: Zarządzanie akcjami poprawy za pomocą Menedżera zgodności
ms.author: chvukosw
author: chvukosw
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 09/29/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
description: Dowiedz się, jak zwiększyć poziom ochrony danych osobowych za pomocą Menedżera oceny zgodności i zgodności.
ms.openlocfilehash: 469584abbf784fe6c556aab14a49a5ed44280a69
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947456"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>Zarządzanie akcjami poprawy za pomocą Menedżera zgodności

Menedżer zgodności usługi Microsoft Purview może pomóc w zarządzaniu ulepszeniami związanymi z przepisami dotyczącymi prywatności danych, takimi jak [ogólne rozporządzenie o ochronie danych w Unii Europejskiej (RODO),](/compliance/regulatory/gdpr) [california consumer protection act CCPA),](/compliance/regulatory/ccpa-faq) HIPAA-HITECH (us health care privacy act) i Brazil Data Protection Act (LGPD).

Ten artykuł zawiera wskazówki dotyczące korzystania z tego narzędzia do celów ochrony prywatności danych.

> [!NOTE]
> Rekomendacje programu Compliance Manager nie powinny być interpretowane jako gwarancja zgodności. Do Ciebie należy ocena i weryfikowanie skuteczności kontroli klientów w danym środowisku regulacyjnym. Te usługi podlegają warunkom i postanowień [w Warunkach świadczenia usług online](https://go.microsoft.com/fwlink/?linkid=2108910). Zobacz również [Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zabezpieczeń i zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="getting-started-with-compliance-manager"></a>Wprowadzenie do programu Compliance Manager

#### <a name="what-is-compliance-manager"></a>Co to jest Menedżer zgodności

[Menedżer zgodności](../compliance/compliance-manager.md) to oparte na przepływie pracy narzędzie do oceny ryzyka w portalu zgodności usługi Microsoft Purview do zarządzania działaniami zgodności z przepisami związanymi z usługami firmy Microsoft w chmurze. W ramach subskrypcji Microsoft 365 lub Azure Active Directory (Azure AD) menedżer zgodności ułatwia zarządzanie zgodnością z przepisami w ramach modelu wspólnej odpowiedzialności za usługi w chmurze firmy Microsoft.

**Gotowe do użycia oceny**

Menedżer zgodności udostępnia wstępnie utworzone szablony do [kompilowania ocen](../compliance/compliance-manager-assessments.md) , które są dostosowane do przepisów dotyczących prywatności danych, takich jak RODO i HIPAA/HITECH. Szablony mają wbudowane mapowanie kontroli, które ułatwiają podjęcie działań ulepszeń w celu spełnienia wymagań rozporządzenia. Każda ocena zawiera informacje na temat mechanizmów kontroli, które każde rozporządzenie wywołuje dla konkretnej usługi docelowej, wydzierżawane przez mechanizmy kontroli zarządzane przez firmę Microsoft i zarządza nimi.

Użycie wstępnie utworzonego szablonu ułatwia szybkie rozpoczęcie oceny ryzyka. W miarę jak stajesz się bardziej biegły w korzystaniu z Menedżera zgodności, możesz dostosować wstępnie utworzony szablon, dodając własne kontrolki i akcje ulepszania lub możesz tworzyć własne niestandardowe oceny zgodnie z potrzebami organizacji.

Wyświetl [pełną listę szablonów oceny dostarczonych](../compliance/compliance-manager-templates-list.md) przez menedżera zgodności.

**Ocena zgodności w czasie rzeczywistym**

Menedżer zgodności zapewnia również ocenę zgodności, która mierzy postęp w wykonywaniu zalecanych akcji poprawy w ramach kontrolek. Możesz użyć tego wyniku, aby pomóc w monitorowaniu postępu i określaniu priorytetów akcji na podstawie ich potencjału w celu zmniejszenia ryzyka.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Korzystanie z przewodnika Szybki start dotyczącego menedżera zgodności

Przewodnik [Szybki start dotyczący menedżera zgodności](../compliance/compliance-manager-quickstart.md) zawiera stopniowane kroki i linki do kluczowych zasobów ułatwiających pracę z Menedżerem zgodności:

- [Pierwsza wizyta: zapoznanie się z menedżerem zgodności](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Praca z pulpitem nawigacyjnym programu Compliance Manager
    - Omówienie oceny zgodności
    - Edukacja o akcjach ulepszania
    - Omówienie ocen i szablonów
- [Zwiększanie poziomu: konfigurowanie menedżera zgodności w celu zarządzania działaniami dotyczącymi zgodności](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - Tworzenie pierwszej oceny i zarządzanie nimi
    - Wykonywanie prac związanych z implementacją i testowaniem akcji poprawy w celu ukończenia kontroli w ocenach
    - Opis wpływu różnych akcji na wynik zgodności
- [Skalowanie w górę: korzystanie z zaawansowanych funkcji w celu spełnienia niestandardowych potrzeb](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Tworzenie niestandardowych ocen w celu śledzenia produktów innych niż Microsoft 365
    - Modyfikowanie istniejących szablonów w celu dodawania lub usuwania kontrolek
    - Konfigurowanie zautomatyzowanego testowania akcji poprawy

## <a name="how-your-compliance-score-is-calculated"></a>Dowiedz się, jak jest obliczany wskaźnik zgodności

Wynik zgodności jest obliczany na podstawie kombinacji implementacji kontroli zarządzanej przez firmę Microsoft i klienta. Aby uzyskać szczegółowe objaśnienie, zobacz [obliczanie wskaźnika zgodności](../compliance/compliance-score-calculation.md) .

Kontrolki są przypisywane do wartości oceny na podstawie tego, czy są one obowiązkowe, czy uznaniowe, oraz czy są prewencyjne, detektywistyczne czy naprawcze. Łącznie stanowią one ryzyko niewdrożeń go w stosunku do innych mechanizmów kontroli.

Jak przedstawiono w artykule obliczania oceny zgodności, kontrole zapobiegawcze otrzymują wyższy wynik niż kontrole detektywistyczne i naprawcze, a obowiązkowe mechanizmy kontroli otrzymują wyższą ocenę niż kontrole uznaniowe.

Interfejs użytkownika administratora wyniku zgodności nie zawiera listy tych parametrów ani nie zapewnia możliwości filtrowania według nich. Jeśli jednak pobierzesz skojarzony szablon z Menedżera zgodności, wynikowe zestawy danych będą wyświetlać te parametry dla większości przepisów.

W przypadku kontroli technicznych menedżer zgodności automatycznie aktualizuje wynik akcji poprawy po pomyślnym zaimplementowaniu i przetestowaniu akcji. Inne, nietechnologiczne akcje&mdash; kontroliuj jako te, które są operacyjne lub związane z dokumentacją&mdash;, które mają być rejestrowane ręcznie zgodnie z implementacją, zanim punkty będą wliczane do wyniku.

Wiele z nich implementuje również pewne akcje poprawy do innych celów&mdash;, na przykład przy użyciu etykiet przechowywania z powodów innych niż zgodność&mdash; z przepisami dotyczącymi prywatności danych, dzięki czemu można uzyskać środki za korzystanie z takiej funkcji, nawet jeśli jest ona używana do innych celów, a nie część celowej akcji zgodności.

Wskaźnik zgodności należy uznać za miarę względną w celu śledzenia poprawy na szeroką skalę. Nie należy dążyć do doskonałego wyniku.

## <a name="additional-guidance"></a>Dodatkowe wskazówki

Poniżej przedstawiono kilka ważnych wskazówek dotyczących korzystania z Menedżera zgodności, które ułatwiają osiągnięcie zgodności z przepisami dotyczącymi prywatności danych:

- Każda regulacja dotycząca prywatności danych ma kombinację mechanizmów kontroli technicznych, specyfikacji dokumentacji oraz wymagań operacyjnych, procesowych i raportowania. Wszystkie te elementy są wyświetlane w akcjach poprawy.

- Aby skoncentrować widok akcji ulepszania na obszar zainteresowania, możesz filtrować według typu akcji na karcie **Rozwiązania w administratorze** programu Compliance Manager. Dowiedz się więcej na temat [filtrowania widoku pulpitu nawigacyjnego programu Compliance Manager](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view).

- Względne znaczenie i priorytet akcji poprawy zidentyfikowanych w Menedżerze zgodności należy traktować jako część szerszego przeglądu ryzyka wraz z ryzykiem prywatności danych, którym organizacja musi zarządzać.

- Nawet w przypadku agregacji akcji poprawy w wielu wymaganiach prawnych, jeśli zostaną wybrane szablony oceny przepisów dla RODO, LGPD, CCPA i HIPAA-HITECH, na przykład w Menedżerze zgodności zostanie wyświetlonych prawie 400 działań ulepszeń. Aby lepiej poradzić sobie z tą długą listą, użyj filtru akcji poprawy, aby zmniejszyć zestaw wyników do listy bardziej zarządzalnej.

- Filtr Kategorie zapewnia sposób filtrowania akcji poprawy według grupowania logicznego, do którego pasują artykuły Śledź, Zapobiegaj, Chroń, Zachowaj i Zbadaj w tym ogólnym rozwiązaniu.

- Niektóre z mechanizmów kontroli wymienionych w działaniach ulepszania można uznać za bardziej bezpośrednio powiązane z określonym artykułem regulacyjnym, podczas gdy inne mechanizmy kontroli mogą być bardziej pośrednio związane z duchem regulacji i wiele razy są po prostu zalecanymi działaniami lub najlepszymi rozwiązaniami.