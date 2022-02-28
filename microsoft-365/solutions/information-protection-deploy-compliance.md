---
title: Zarządzanie działaniami udoskonalania za pomocą Menedżera zgodności
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
description: Dowiedz się, jak korzystać z wyników zgodności i Menedżera zgodności w celu poprawy poziomu ochrony danych osobowych.
ms.openlocfilehash: 5a655d504551e42398cdabbcf7a3f651d788c0ad
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990497"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>Zarządzanie działaniami udoskonalania za pomocą Menedżera zgodności

Menedżer zgodności firmy Microsoft może ułatwić zarządzanie ulepszeniami dotyczącymi przepisów o ochronie prywatności danych, takich jak Ogólne Rozporządzenie o Ochronie Danych [(](/compliance/regulatory/gdpr)RODO) Unii Europejskiej, california [Consumer Protection Act HIPAA),](/compliance/regulatory/ccpa-faq) HIPAA-HITECH (us health care privacy act) oraz brazylijskiej ustawy o ochronie danych (LGPD).

Ten artykuł zawiera wskazówki dotyczące używania tego narzędzia w celu ochrony prywatności danych.

> [!NOTE]
> Rekomendacje Menedżera zgodności nie należy interpretować jako gwarancji zgodności. Ocena i weryfikacja skuteczności kontroli klienta w środowisku wymogów prawnych należy do Użytkownika. Te usługi podlegają regulaminom i regulaminom usług [online](https://go.microsoft.com/fwlink/?linkid=2108910). Zobacz też [Microsoft 365 licencjonowania w zakresie zabezpieczeń i zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="getting-started-with-compliance-manager"></a>Wprowadzenie do Menedżera zgodności

#### <a name="what-is-compliance-manager"></a>Co to jest Menedżer zgodności

[Menedżer zgodności to](../compliance/compliance-manager.md) narzędzie do oceny ryzyka oparte na przepływie pracy w usłudze Centrum zgodności platformy Microsoft 365 zarządzania działaniami związanymi ze zgodnością z przepisami związanymi z usługami firmy Microsoft w chmurze. W ramach subskrypcji usługi Microsoft 365 lub Azure Active Directory (Azure AD) Menedżer zgodności ułatwia zarządzanie zgodnością z przepisami w modelu współodpowiedzialność za usługi w chmurze firmy Microsoft.

**Gotowe do użycia ocen**

Menedżer zgodności udostępnia wstępnie zbudowane szablony do tworzenia [](../compliance/compliance-manager-assessments.md) ocen zgodnych z przepisami związanymi z prywatnością danych, takimi jak RODO i HIPAA/HITECH. Szablony mają wbudowane mapowanie kontrolek, które ułatwiają działania usprawnianie w zakresie spełniania wymagań przepisów. Każda ocena zawiera informacje na temat kontroli, za pomocą których poszczególne przepisy określa się w poszczególnych usługach docelowych, podzielone na kontrolki, które zarządzasz i kontrolami zarządza firma Microsoft.

Używanie wbudowanego szablonu ułatwia szybkie rozpoczynanie oceny ryzyka. Gdy stajesz się bardziej ekspertem w zakresie korzystania z Menedżera zgodności, możesz dostosować wstępnie wbudowany szablon, dodając własne kontrolki i akcje udoskonalania lub tworzyć własne niestandardowe oceny dopasowane do potrzeb organizacji.

Wyświetl pełną [listę szablonów oceniań dostarczonych](../compliance/compliance-manager-templates-list.md) przez Menedżera zgodności.

**Wynik zgodności w czasie rzeczywistym**

Menedżer zgodności udostępnia również ocenę zgodności, która mierzy postęp wykonywania zalecanych działań udoskonalania w ramach kontrolek. Na podstawie tej oceny można monitorować postęp i priorytetyzować akcje na podstawie ich możliwości zmniejszenia ryzyka.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Korzystanie z przewodnika Szybki start dla menedżera zgodności

Przewodnik [Szybki start menedżera zgodności udostępnia](../compliance/compliance-manager-quickstart.md) stopniowe etapy oraz linki do kluczowych zasobów, które ułatwiają pracę z Menedżerem zgodności:

- [Pierwsza wizyta: zapoznanie się z Menedżerem zgodności](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Praca z pulpitem nawigacyjnym Menedżera zgodności
    - Opis wyniku w zakresie zgodności
    - Edukacja o działaniach udoskonalania
    - Opis formularzy oceniania i szablonów
- [Rozszerz: konfigurowanie Menedżera zgodności w celu zarządzania działaniami zgodności](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - Tworzenie pierwszej oceny i zarządzanie nimi
    - Wykonywanie prac implementacji i testów nad działaniami udoskonalania w celu ukończenia kontroli w testach
    - Opis wpływu różnych akcji na wynik zgodności
- [Skalowanie: korzystanie z zaawansowanych funkcji w celu zaspokojenia potrzeb niestandardowych](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Tworzenie niestandardowych formularzy oceniania w celu śledzenia Microsoft 365 produktów
    - Modyfikowanie istniejących szablonów w celu dodania lub usunięcia kontrolek
    - Konfigurowanie automatycznego testowania działań udoskonalania

## <a name="how-your-compliance-score-is-calculated"></a>Sposób obliczania wyniku zgodności

Twój wynik zgodności jest obliczany na podstawie kombinacji implementacji firmy Microsoft i implementacji kontroli zarządzanej przez klienta. Zobacz [obliczanie wyników zgodności,](../compliance/compliance-score-calculation.md) aby uzyskać szczegółowe objaśnienie.

Kontrolkom przypisywana jest wartość wyniku na podstawie tego, czy są one obowiązkowe, czy dyskrecjonalne, oraz od tego, czy mają one charakter uniemożliwiający, deklarowany lub korygający. Stanowią one zbiorczo ryzyko, że nie zostanie ono zaimplementowane względem innych kontrolek.

Jak przedstawiono w artykule obliczania wyników zgodności, kontrolki zapobiegające uzyskać wyższą ocenę niż kontrolki wykrywające i poprawiające, a kontrolki obowiązkowe mają wyższą ocenę niż kontrolki dyskrecjonalne.

Interfejs użytkownika administratora wyników zgodności nie zawiera listy tych parametrów ani nie umożliwia filtrowania według nich. Jednak w przypadku pobrania skojarzonego szablonu z Menedżera zgodności zestaw danych wynikowy zawiera listę tych parametrów dla większości przepisów.

W przypadku kontroli technicznej Menedżer zgodności automatycznie aktualizuje wynik działania udoskonalania po pomyślnym wdrożeniu i przetestowaniu akcji. Inne działania niezwiązyane&mdash;&mdash; z kontrolą techniczną, takie jak działania operacyjne lub związane z dokumentacją, które muszą być rejestrowane ręcznie jako zaimplementowane, zanim punkty będą liczone w wyniku.

Wiele osób&mdash;&mdash; wdraża również pewne działania udoskonalania do innych celów, na przykład za pomocą etykiet przechowywania w celach innych niż zgodność z przepisami dotyczącymi prywatności danych. Użytkownik otrzyma środki za korzystanie z takiej funkcji nawet w przypadku, gdy jest ona używana do innych celów, a nie w ramach rozmyślnej akcji zgodności.

Twój wynik zgodności powinien być uznawany za miarę względną w celu śledzenia poprawy na szeroką skalę. Nie należy podysyłać idealnego wyniku.

## <a name="additional-guidance"></a>Dodatkowe wskazówki

Oto kilka ważnych porad dotyczących korzystania z Menedżera zgodności w celu zapewnienia zgodności z przepisami dotyczącymi prywatności danych:

- Każde rozporządzenie o ochronie prywatności danych ma połączenie kontroli technicznej, specyfikacji dokumentacji oraz wymagań operacyjnych, procesów i raportowania. Wszystkie te działania są wyświetlane w działaniach udoskonalania.

- Aby skoncentrować się na działaniach udoskonalania w określonym obszarze, możesz filtrować według typu akcji na karcie Rozwiązania  w administracyjnym Menedżera zgodności. Dowiedz się więcej o [filtrowaniu widoku pulpitu nawigacyjnego Menedżera zgodności](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view).

- Względna ważność i priorytet działań udoskonalania zidentyfikowanych w Menedżerze zgodności należy traktować jako część szerszego przeglądu ryzyka oraz ryzyka związanego z prywatnością danych, które musi zarządzać Twoja organizacja.

- Nawet w przypadku doskonalenia agregacji działań w wielu wymaganiach prawnych, jeśli na przykład zaznaczono szablony oceny przepisów dotyczące RODO, LGPD, HIPAA i HIPAA-HITECH, w Menedżerze zgodności zostanie wymienionych niemal 400 działań usprawnień. Aby lepiej zająć się tą długą listą, użyj filtru akcji udoskonalania, aby zmniejszyć zestaw wyników do listy, która będzie lepiej zarządzana.

- Filtr Kategorie umożliwia filtrowanie akcji udoskonalania według grupowania logicznego, do którego są dostosowane artykuły Śledź, Chroń, Zachowaj i Badanie w ramach tego ogólnego rozwiązania.

- Niektóre kontrolki wymienione w działaniach udoskonalania można uznać za bardziej bezpośrednio powiązane z określonym artykułem regulacyjną, natomiast inne mechanizmy kontroli mogą być pośrednio związane z działaniem przepisów, a wielokrotnie są po prostu zalecanymi działaniami lub najlepszymi rozwiązaniami.