---
title: Zaplanuj zarządzanie ryzykiem wewnętrznym
description: Dowiedz się, jak planować korzystanie z zasad zarządzania ryzykiem wewnętrznym w organizacji.
keywords: Microsoft 365, Microsoft Purview, ryzyko wewnętrzne, zarządzanie ryzykiem, zgodność
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: ad69d525ac8cf105761286c59e8bce54d446ae8f
ms.sourcegitcommit: b5529afa84f7dde0a89b1e08aeaf6a3a15cd7679
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65599596"
---
# <a name="plan-for-insider-risk-management"></a>Zaplanuj zarządzanie ryzykiem wewnętrznym

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Przed rozpoczęciem [zarządzania ryzykiem wewnętrznym](insider-risk-management.md) w organizacji istnieją ważne działania związane z planowaniem i zagadnienia, które powinny zostać poddane przeglądowi przez zespoły ds. technologii informatycznych i zarządzania zgodnością. Dokładne zrozumienie i planowanie wdrożenia w następujących obszarach pomoże zapewnić bezproblemowe wdrożenie i korzystanie z funkcji zarządzania ryzykiem wewnętrznym i jest zgodne z najlepszymi rozwiązaniami dla rozwiązania. 

Aby uzyskać więcej informacji i omówienie procesu planowania w celu rozwiązania ryzykownych działań w organizacji, zobacz [Uruchamianie programu do zarządzania ryzykiem wewnętrznym](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Obejrzyj poniższy film wideo, aby dowiedzieć się, w jaki sposób przepływ pracy zarządzania ryzykiem wewnętrznym może pomóc organizacji w zapobieganiu, wykrywaniu i ograniczaniu ryzyka przy jednoczesnym określaniu priorytetów wartości, kultury i środowiska użytkownika organizacji:
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

## <a name="work-with-stakeholders-in-your-organization"></a>Praca z osobami biorącymi udział w projekcie w organizacji

Zidentyfikuj odpowiednie osoby biorące udział w projekcie w organizacji, aby współpracować przy podejmowaniu działań dotyczących alertów i przypadków dotyczących zarządzania ryzykiem wewnętrznym. Niektóre zalecane osoby biorące udział w projekcie, które należy wziąć pod uwagę, uwzględniają w planowaniu wstępnym i [kompleksowym przepływie pracy zarządzania ryzykiem wewnętrznym](insider-risk-management.md#workflow) osoby z następujących obszarów organizacji:

- Technologia informacyjna
- Zgodność
- Prywatność
- Bezpieczeństwo
- Zasoby ludzkie
- Prawnych

## <a name="determine-any-regional-compliance-requirements"></a>Określanie wszelkich regionalnych wymagań dotyczących zgodności

Różne obszary geograficzne i organizacyjne mogą mieć wymagania dotyczące zgodności i prywatności, które różnią się od innych obszarów organizacji. Współpracuj z zainteresowanymi stronami w tych obszarach, aby upewnić się, że rozumieją oni mechanizmy kontroli zgodności i prywatności w zarządzaniu ryzykiem wewnętrznym oraz sposób ich stosowania w różnych obszarach organizacji. W niektórych scenariuszach wymagania dotyczące zgodności i prywatności mogą wymagać zasad, które wyznaczają lub ograniczają niektórych uczestników badania i sprawy w oparciu o wymagania dotyczące użytkownika lub przepisów lub zasad dla danego obszaru.

Jeśli masz wymagania dotyczące udziału określonych uczestników projektu w badaniach przypadków, które dotyczą użytkowników w niektórych regionach, rolach lub działach, możesz zaimplementować oddzielne (nawet identyczne) [zasady zarządzania ryzykiem wewnętrznym](insider-risk-management-policies.md) przeznaczone dla różnych regionów i populacji. Ta konfiguracja ułatwi odpowiednim uczestnikom projektu klasyfikację przypadków istotnych dla ich ról i regionów oraz zarządzanie nimi. Ponadto warto rozważyć utworzenie procesów i zasad dla regionów, w których badacze i recenzenci mówią tym samym językiem co użytkownicy, aby usprawnić proces eskalacji alertów i przypadków zarządzania ryzykiem wewnętrznym.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planowanie przepływu pracy przeglądu i badania

W zależności od sposobu zarządzania zasadami i alertami dotyczącymi zarządzania ryzykiem wewnętrznym należy przypisać użytkowników do określonych grup ról, aby zarządzać różnymi zestawami funkcji zarządzania ryzykiem wewnętrznym. Istnieje możliwość przypisania użytkowników z różnymi obowiązkami zgodności do określonych grup ról w celu zarządzania różnymi obszarami funkcji zarządzania ryzykiem wewnętrznym. Możesz też zdecydować się na przypisanie wszystkich kont użytkowników wyznaczonym administratorom, analitykom, badaczom i widzom do grupy ról Insider Risk Management. Użyj jednej grupy ról lub wielu grup ról, aby najlepiej dopasować wymagania dotyczące zarządzania zgodnością.

Podczas pracy z zarządzaniem ryzykiem wewnętrznym wybierzesz spośród tych opcji grupy ról i akcji rozwiązania:

|**Działania**|**Zarządzanie ryzykiem wewnętrznym**|**Administrator zarządzania ryzykiem wewnętrznym**|**Analitycy zarządzania ryzykiem wewnętrznym**|**Badacze zarządzania ryzykiem wewnętrznym**|**Audytorzy zarządzania ryzykiem wewnętrznym**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| Konfigurowanie zasad i ustawień | Tak | Tak | Nie | Nie | Nie |
| Uzyskiwanie dostępu do szczegółowych informacji analitycznych | Tak | Tak | Tak | Nie | Nie |
| & dostępu bada alerty | Tak | Nie | Tak | Tak | Nie |
| & dostępu bada przypadki | Tak | Nie | Tak | Tak | Nie |
| Uzyskiwanie dostępu & wyświetlenie Eksploratora zawartości | Tak | Nie | Nie | Tak | Nie |
| Konfigurowanie szablonów powiadomień | Tak | Nie | Tak | Tak | Nie |
| Wyświetlanie dzienników inspekcji eksportu & | Tak | Nie | Nie | Nie | Tak |

>[!IMPORTANT]
>Upewnij się, że zawsze masz co najmniej jednego użytkownika w grupach ról *Insider Risk Management* lub *Insider Risk Management Admin* (w zależności od wybranej opcji), aby konfiguracja zarządzania ryzykiem wewnętrznym nie mogła przejść do scenariusza "zero administratora", jeśli określoni użytkownicy opuszczą Twoją organizację.

Członkowie następujących ról mogą przypisywać użytkowników do grup ról zarządzania ryzykiem wewnętrznym i mieć te same uprawnienia rozwiązania dołączone do grupy ról *Administrator zarządzania ryzykiem wewnętrznym* :

- *administrator globalny* Azure Active Directory
- *administrator zgodności* Azure Active Directory
- *zarządzanie organizacją* portal zgodności Microsoft Purview
- *administrator zgodności* portal zgodności Microsoft Purview

## <a name="understand-requirements-and-dependencies"></a>Omówienie wymagań i zależności

W zależności od tego, jak planujesz zaimplementować zasady zarządzania ryzykiem wewnętrznym, musisz mieć odpowiednie Microsoft 365 subskrypcje licencjonowania oraz poznać i zaplanować niektóre wymagania wstępne rozwiązania.

**Licencjonowania:** Zarządzanie ryzykiem wewnętrznym jest dostępne w ramach szerokiego wyboru subskrypcji licencjonowania Microsoft 365. Aby uzyskać szczegółowe informacje, zobacz artykuł [Wprowadzenie do zarządzania ryzykiem wewnętrznym](insider-risk-management-configure.md#subscriptions-and-licensing) .

> [!IMPORTANT]
> Zarządzanie ryzykiem wewnętrznym jest obecnie dostępne w dzierżawach hostowanych w regionach geograficznych i krajach obsługiwanych przez zależności usługi platformy Azure. Aby sprawdzić, czy zarządzanie ryzykiem wewnętrznym jest obsługiwane w organizacji, zobacz [Dostępność zależności platformy Azure według kraju/regionu](/troubleshoot/azure/general/dependency-availability-by-country).

Jeśli nie masz istniejącego planu Microsoft 365 Enterprise E5 i chcesz wypróbować zarządzanie ryzykiem wewnętrznym, możesz [dodać Microsoft 365](/office365/admin/try-or-buy-microsoft-365) do istniejącej subskrypcji lub [utworzyć konto próbne](https://www.microsoft.com/microsoft-365/enterprise) Microsoft 365 Enterprise E5.

**Wymagania szablonu zasad:** W zależności od wybranego szablonu zasad istnieją wymagania, które należy zrozumieć i zaplanować przed skonfigurowaniem zarządzania ryzykiem wewnętrznym w organizacji:

- W przypadku korzystania z szablonu **Kradzież danych przez odchodzących użytkowników** należy skonfigurować łącznik Microsoft 365 HR, aby okresowo importować informacje o rezygnacji i dacie zakończenia dla użytkowników w organizacji. Zapoznaj się [z artykułem Importowanie danych za pomocą łącznika HR,](import-hr-data.md) aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika Microsoft 365 HR dla organizacji.
- W przypadku korzystania z **szablonów wycieków danych** należy skonfigurować co najmniej jedną zasadę Ochrona przed utratą danych w Microsoft Purview (DLP) w celu zdefiniowania poufnych informacji w organizacji i otrzymywania alertów o ryzyku wewnętrznym dla alertów zasad DLP o wysokiej ważności. Zapoznaj się z [artykułem Tworzenie, testowanie i dostrajanie zasad DLP,](create-test-tune-dlp-policy.md) aby uzyskać szczegółowe wskazówki dotyczące konfigurowania zasad DLP dla organizacji.
- W przypadku korzystania z szablonów **naruszeń zasad zabezpieczeń** należy włączyć Ochrona punktu końcowego w usłudze Microsoft Defender integracji zarządzania ryzykiem wewnętrznym w usłudze Defender Security Center, aby importować alerty naruszenia zabezpieczeń. Aby uzyskać szczegółowe wskazówki dotyczące włączania integracji usługi Defender for Endpoint z zarządzaniem ryzykiem wewnętrznym, zobacz [Konfigurowanie zaawansowanych funkcji w Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/advanced-features).
- W przypadku korzystania z **niezadowolonych szablonów użytkowników** należy skonfigurować łącznik Microsoft 365 HR, aby okresowo importować informacje o stanie wydajności lub degradacji dla użytkowników w organizacji. Zapoznaj się [z artykułem Importowanie danych za pomocą łącznika HR,](import-hr-data.md) aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika Microsoft 365 HR dla organizacji.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Testowanie z niewielką grupą użytkowników w środowisku produkcyjnym

Przed włączeniem rozwiązania szeroko w środowisku produkcyjnym możesz rozważyć przetestowanie zasad z niewielką grupą użytkowników produkcyjnych podczas przeprowadzania niezbędnych przeglądów zgodności, prywatności i prawnych w organizacji. Ocena zarządzania ryzykiem wewnętrznym w środowisku testowym wymagałaby wygenerowania symulowanych akcji użytkownika i innych sygnałów w celu utworzenia alertów dotyczących klasyfikacji i przypadków przetwarzania. Takie podejście nie jest praktyczne dla większości organizacji, dlatego preferowane jest testowanie zarządzania ryzykiem wewnętrznym z niewielką grupą użytkowników w środowisku produkcyjnym.

Zachowaj włączoną funkcję anonimizacji w ustawieniach zasad, aby anonimizować nazwy wyświetlane użytkowników w konsoli zarządzania ryzykiem wewnętrznym podczas tych testów, aby zachować prywatność w narzędziu. To ustawienie pomaga chronić prywatność użytkowników, którzy mają dopasowania zasad i mogą pomóc w promowaniu obiektywizmu w badaniach danych i przeglądach analiz dla alertów o ryzyku wewnętrznym.

Jeśli nie widzisz żadnych alertów natychmiast po skonfigurowaniu zasad zarządzania ryzykiem wewnętrznym, może to oznaczać, że minimalny próg ryzyka nie został jeszcze osiągnięty. Dobrym sposobem sprawdzenia, czy zasady są wyzwalane i działają zgodnie z oczekiwaniami, jest sprawdzenie, czy użytkownik jest w zakresie zasad na stronie **Użytkownicy** .

## <a name="resources-for-stakeholders"></a>Zasoby dla uczestników projektu

Udostępnij dokumentację dotyczącą zarządzania ryzykiem wewnętrznym uczestnikom projektu w organizacji, które są uwzględnione w przepływie pracy zarządzania i korygowania:

- [Twórz zasady ryzyka wewnętrznego i zarządzaj nimi](insider-risk-management-policies.md)
- [Badaj działania związane z ryzykiem wewnętrznym](insider-risk-management-activities.md)
- [Podejmij działanie w przypadku zdarzeń związanych z ryzykiem wewnętrznym](insider-risk-management-cases.md)
- [Przeglądanie danych sprawy za pomocą eksploratora zawartości ryzyka związanego z informacjami poufnymi](insider-risk-management-content-explorer.md)
- [Twórz szablony powiadomień o ryzyku wewnętrznym](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Chcesz rozpocząć pracę?

Chcesz skonfigurować zarządzanie ryzykiem wewnętrznym dla swojej organizacji? Zapoznaj się z następującymi artykułami:

- [Wprowadzenie z ustawieniami zarządzania ryzykiem wewnętrznym](insider-risk-management-settings.md) w celu skonfigurowania ustawień zasad globalnych.
- [Wprowadzenie z zarządzaniem ryzykiem wewnętrznym](insider-risk-management-configure.md) w celu skonfigurowania wymagań wstępnych, utworzenia zasad i rozpoczęcia otrzymywania alertów.
