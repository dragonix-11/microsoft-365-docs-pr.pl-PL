---
title: Dowiedz się więcej o nazywanych obiektach
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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak nazwane jednostki ułatwiają wykrywanie poufnych elementów zawierających nazwiska osób, adresy fizyczne i terminy medyczne za pośrednictwem zasad ochrony przed utratą danych
ms.openlocfilehash: 013d2453190c692eeb3ae9a0dfd48437bded1f0c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633504"
---
# <a name="learn-about-named-entities"></a>Dowiedz się więcej o nazywanych obiektach

*Nazwane jednostki* to [poufne typy informacji](sensitive-information-type-learn-about.md) (SIT). Są to złożone słowniki i klasyfikatory oparte na wzorcach, których można użyć do wykrywania nazwisk osób, adresów fizycznych oraz warunków medycznych. Można je zobaczyć w **typach portal zgodności Microsoft Purview > Klasyfikacja danych > Informacje poufne**. Poniżej znajduje się częściowa lista miejsc, w których można używać interfejsów SIC:


- [zasady Ochrona przed utratą danych w Microsoft Purview (DLP)](dlp-learn-about-dlp.md) 
- [Etykiety wrażliwości](sensitivity-labels.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management-solution-overview.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Purview Information Protection](apply-sensitivity-label-automatically.md)
- [Zarządzanie cyklem życia danych](information-governance.md)
- [Zarządzanie rekordami](records-management.md)
- [Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview](ediscovery.md)
- [Microsoft Priva](/privacy/priva/priva-overview.md)
- [Dokładne dane pasują do typów informacji poufnych](sit-learn-about-exact-data-match-based-sits.md)

DLP korzysta z jednostek nazwanych w *rozszerzonych szablonach zasad*, które są wstępnie skonfigurowanymi zasadami DLP, które można dostosować do potrzeb organizacji. Możesz również [utworzyć własne zasady DLP](create-test-tune-dlp-policy.md) na podstawie [pustego szablonu](create-a-dlp-policy-from-a-template.md) i użyć nazwanej jednostki SIT jako warunku.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>Przykłady nazwanych SIC jednostek

Nazwane interfejsy SIC jednostki są dostępne w dwóch wersjach, *w pakiecie* i *oddzielenie*

Dołączone nazwane jednostki SIC wykrywają wszystkie możliwe dopasowania. Użyj ich jako szerokich kryteriów w zasadach DLP do wykrywania poufnych elementów.

Węższe fokus mają węższe jednostki, takie jak pojedynczy kraj. Użyj ich, gdy potrzebujesz zasad DLP z węższym zakresem wykrywania.
 
Oto kilka przykładów nazwanych jednostek SIC. Wszystkie z nich można znaleźć w [definicjach jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md).

|Nazwana jednostka |Opis  |Pakiety/rozdzielenie  |
|---------|---------|---------|
|Wszystkie pełne nazwy    |wykryje wszystkie możliwe dopasowania pełnych nazw         |   Pakiecie      |
|Wszystkie adresy fizyczne    |wykryje wszystkie możliwe dopasowania adresów fizycznych     | Pakiecie |
|Wszystkie warunki i postanowienia medyczne    |wykryje wszystkie możliwe dopasowania warunków medycznych |Pakiecie |
|Adresy fizyczne w Australii |  Wykrywa wzorce związane z adresami fizycznymi z Australii. Uwzględnione we wszystkich adresach fizycznych SIT. |Uwolnionego |
|Warunki badania krwi     |Wykrywa terminy związane z badaniami krwi, takie jak "hCG". Tylko terminy angielskie. Zawarte we wszystkich warunkach medycznych SIT      |Uwolnionego |
|Markowe nazwy leków     |Wykrywa nazwy leków marki, takich jak "Tylenol". Tylko terminy angielskie. Zawarte we wszystkich warunkach medycznych.         |Uwolnionego |

## <a name="examples-of-enhanced-dlp-policies"></a>Przykłady rozszerzonych zasad DLP

Oto kilka przykładów rozszerzonych zasad DLP, które używają nazwanych jednostek SIC. Wszystkie 10 z nich można znaleźć w **zasadach portal zgodności Microsoft Purview > Ochrona przed utratą danych > Tworzenie**. Ulepszonych szablonów można używać w programie DLP i automatycznym etykietowaniu.

|Kategoria zasad  |Szablon  |Opis  |
|---------|---------|---------|
|Finansowych|U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced         |Pomaga wykrywać obecność informacji podlegających gramm-Leach-Bliley Act (GLBA), w tym informacji, takich jak numery ubezpieczenia społecznego lub numery kart kredytowych. Ten rozszerzony szablon rozszerza oryginał, wykrywając również imię i nazwisko osób, USA/Zjednoczone Zjednoczone Zjednoczone Strony. numer paszportu, numer prawa jazdy w Stanach Zjednoczonych i adresy fizyczne w Stanach Zjednoczonych.         |
| Medycyna i zdrowie   |Australia Health Records Act (HRIP Act) Enhanced         |Pomaga wykrywać obecność informacji powszechnie uważanych za podlegające ustawie o ochronie danych i informacji zdrowotnych (HRIP) w Australii, takiej jak numer konta medycznego i numer pliku podatkowego. Ten rozszerzony szablon rozszerza oryginał, wykrywając również pełne nazwiska osób, warunki i postanowienia medyczne oraz adresy fizyczne Australii.         |
|Prywatność   |Rozszerzono ogólne rozporządzenie o ochronie danych (RODO)         | Pomaga wykrywać obecność danych osobowych osób fizycznych w Unii Europejskiej (UE), aby pomóc w spełnieniu obowiązków wynikających z rozporządzenia RODO w zakresie ochrony prywatności. Ten rozszerzony szablon wykrywa imię i nazwisko i adresy fizyczne osób w krajach UE.        |


## <a name="next-steps"></a>Następne kroki

- [Używaj nazwanych obiektów w zasadach zapobiegania utracie danych](named-entities-use.md)


## <a name="for-further-information"></a>Aby uzyskać więcej informacji

- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Dowiedz się więcej o typach informacji poufnych](sensitive-information-type-learn-about.md)
- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
- [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Zasady ochrony przed utratą danych (DLP)](data-loss-prevention-policies.md) 
- [Etykiety wrażliwości](sensitivity-labels.md)
- [Etykiety przechowywania](retention.md)
- [Zgodność w komunikacji](communication-compliance.md)
- [Zasady automatycznego etykietowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md) 
