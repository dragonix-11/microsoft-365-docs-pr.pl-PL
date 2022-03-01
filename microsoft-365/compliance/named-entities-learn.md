---
title: Informacje o nazwanych jednostkach (wersja zapoznawcza)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak nazwane jednostki ułatwiają wykrywanie poufnych elementów zawierających imiona i nazwiska osób, adresy fizyczne i terminy medyczne za pośrednictwem zasad ochrony przed utratą danych
ms.openlocfilehash: 002905264d789e7ebe0b163a80fe033c028a6b4b
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006162"
---
# <a name="learn-about-named-entities-preview"></a>Informacje o nazwanych jednostkach (wersja zapoznawcza)

> [!IMPORTANT]
> Funkcja nazwanych jednostek jest obecnie wprowadzana i będzie wyświetlana w dzierżawie, gdy będzie dla Ciebie dostępna. Sprawdź je w Eksploratorze zawartości i w przepływie tworzenia zasad ochrony przed utratą danych (DLP). 

*Nazwane jednostki* są [typami informacji poufnych](sensitive-information-type-learn-about.md) (SIT). Są to złożone słowniki i klasyfikatory oparte na wzorcu, których można używać do wykrywania imion i nazwisk, adresów fizycznych oraz warunków medycznych. Możesz je wyświetlić w Centrum zgodności i > **klasyfikacji danych > typów informacji poufnych**. Poniżej znajduje się częściowa lista, na której można używać sits:

- [Zasady ochrony przed utratą danych (DLP)](dlp-learn-about-dlp.md) 
- [Etykiety wrażliwości](sensitivity-labels.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management-solution-overview.md)
- [Usługa Microsoft Defender dla aplikacji w chmurze](/cloud-app-security/what-is-cloud-app-security)

Zasady DLP używają specjalnych nazwanych jednostek w ulepszonych szablonach *zasad, które* są wstępnie skonfigurowanymi zasadami ochrony przed zasadami DLP, które można dostosowywać do potrzeb organizacji. Możesz również utworzyć [własne zasady ochrony](create-test-tune-dlp-policy.md) przed zasadami ochrony przed zasadami na [podstawie pustego](create-a-dlp-policy-from-a-template.md) szablonu i użyć jako warunku nazwanej jednostki SIT.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>Przykłady nazwanych identyfikatorów SIT encji

Nazwane jednostki SIT są dostępne w dwóch odmianach: *powiązane* i *nieposkutane*

Powiązane nazwane jednostki STS wykryją wszystkie możliwe dopasowania. Korzystaj z nich jako szerokiego kryterium wykrywania poufnych elementów w zasadach ochrony przed użyciem funkcji DLP.

Nieoznaczana nazwana jednostka ma węższą koncentrację, jak jeden kraj. Używaj ich, gdy potrzebujesz zasad DLP o węższym zakresie wykrywania.
 
Oto kilka przykładów nazwanych identyfikatorów STS jednostki. Wszystkie 52 z nich można znaleźć w Centrum zgodności > **klasyfikacji danych > typów informacji poufnych**.

|Nazwana jednostka |Opis  |Bundled/Unrathdled  |
|---------|---------|---------|
|Wszystkie imiona i nazwiska    |wykryje wszystkie możliwe dopasowania pełnego nazwiska         |   pakiet      |
|Wszystkie adresy fizyczne    |wykryje wszystkie możliwe dopasowania adresów fizycznych     | pakiet |
|Wszystkie warunki medyczne    |wykryje wszystkie możliwe dopasowania warunków i terminów medycznych |pakiet |
|Adresy fizyczne (Australia) |  Wykrywa wzorce związane z adresami fizycznymi z Australii. |unbardled |
|Warunki testowania krwi     |Wykrywa terminy związane z testami krwi, takie jak "hCG". Tylko w języku angielskim.      |unbardled |
|Nazwy leki marki     |Wykrywa nazwy leki marki, na przykład "Tylefen". Tylko w języku angielskim.         |unbardled |

## <a name="examples-of-enhanced-dlp-policies"></a>Przykłady rozszerzonych zasad DLP

Oto kilka przykładów rozszerzonych zasad DLP, które korzystają z nazwanych identyfikatorów SIT encji. Wszystkie 10 z nich możesz znaleźć w Centrum zgodności, aby uzyskać > ochrony przed utratą danych **> tworzenie zasad**. Ulepszone szablony mogą być używane w funkcjach DLP i automatycznych etykietach.

|Kategoria zasad  |Szablon  |Opis  |
|---------|---------|---------|
|Finanse|Ulepszona amerykańska ustawa Gramm-Leach-Bliley Act (GLBA)         |Pomaga wykryć obecność informacji podlegających ustawie Gramm-Leach-Blileya (GLBA), w tym informacji, takich jak numery PESEL lub numery kart kredytowych. Ten rozszerzony szablon rozszerza oryginał, wykrywając też imiona i nazwiska osób (Stany Zjednoczone) numer paszportu, numer prawa jazdy w Stanach Zjednoczonych i adresy fizyczne w Stanach Zjednoczonych.         |
| Medyczne i medyczne   |Rozszerzona ustawa Australia Health Records Act (HRIP Act)         |Pomaga wykryć obecność informacji uznanych za podlegające ustawie dotyczącej ochrony danych o stanie zdrowia i informacji (H ZAOPATRZE WJR) w Australii, na przykład numeru konta medycznego i numeru pliku podatkowego. Ten rozszerzony szablon rozszerza oryginał, wykrywając też pełne imiona i nazwiska, warunki medyczne i adresy fizyczne Australii.         |
|Prywatność   |Rozszerzone Ogólne Rozporządzenie o Ochronie Danych (RODO)         | Pomaga wykryć obecność informacji osobistych u poszczególnych osób w Unii Europejskiej, aby pomóc w dochylić zobowiązania do zachowania poufności informacji w związku z RODO. Ten rozszerzony szablon wykrywa pełne imiona i nazwiska oraz adresy fizyczne osób w krajach Unii Europejskiej.        |


## <a name="next-steps"></a>Następne kroki

- [Używanie nazwanych obiektów w zasadach ochrony przed utratą danych (wersja zapoznawcza)](named-entities-use.md)


## <a name="for-further-information"></a>Więcej informacji
<!--- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md)
- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
- [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Zasady ochrony przed utratą danych (DLP)](data-loss-prevention-policies.md) 
- [Etykiety wrażliwości](sensitivity-labels.md)
- [Etykiety przechowywania](retention.md)
- [Zgodność komunikacji](communication-compliance.md)
- [Zasady autolabeli](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md) 
