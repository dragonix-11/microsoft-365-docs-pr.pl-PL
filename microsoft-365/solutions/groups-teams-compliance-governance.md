---
title: Opcje zgodności dla grup Microsoft 365, Teams i współpracy SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się więcej o opcjach zgodności dla grup Microsoft 365, Teams i współpracy SharePoint.
ms.openlocfilehash: afbbc6e507d613e028f65dbc157ec2222414af8c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939131"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Opcje zgodności dla grup Microsoft 365, Teams i współpracy SharePoint

Microsoft 365 oferuje pełny zestaw narzędzi do utrzymania zgodności w miarę współpracy użytkowników. Przejrzyj te opcje i zastanów się, w jaki sposób są one mapowane na potrzeby biznesowe, poufność danych i zakres osób, z którymi użytkownicy muszą współpracować.

Poniższa tabela zawiera krótkie informacje dotyczące mechanizmów kontroli zgodności dostępnych w Microsoft 365. Dalsze informacje znajdują się w poniższych sekcjach.

|Kategoria|Opis|Odwołanie|
|:-------|:----------|:--------|
|Przechowywanie informacji|||
||Zachowywanie zawartości poczty i SharePoint grup|[Dowiedz się więcej o zasadach przechowywania dla SharePoint i OneDrive](../compliance/retention-policies-sharepoint.md)|
||Zachowywanie czatu i wiadomości|[Dowiedz się więcej o zasadach przechowywania dla Microsoft Teams](../compliance/retention-policies-teams.md)|
|Klasyfikacja informacji|||
||Klasyfikowanie grup i zespołów|[Używanie etykiet poufności do ochrony zawartości w witrynach Microsoft Teams, Microsoft 365 i SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Automatyczne klasyfikowanie poufnej zawartości|[Automatyczne stosowanie etykiety poufności do zawartości](../compliance/apply-sensitivity-label-automatically.md)|
||Szyfrowanie poufnej zawartości|[Ogranicz dostęp do zawartości przy użyciu etykiet poufności w celu zastosowania szyfrowania](../compliance/encryption-sensitivity-labels.md)|
|Ochrona informacji|||
||Zapobieganie utracie informacji poufnych|[Dowiedz się więcej o zapobieganiu utracie danych w usłudze Microsoft Purview](../compliance/dlp-learn-about-dlp.md)|
||Ochrona poufnych informacji na czacie.|[Zapobieganie utracie danych i Microsoft Teams w usłudze Microsoft Purview](../compliance/dlp-microsoft-teams.md)|
||Definiowanie poufnych informacji organizacji|[Niestandardowe typy informacji poufnych](../compliance/sensitive-information-type-learn-about.md)|
|Segmentacja użytkowników|||
||Ograniczanie komunikacji między segmentami użytkowników|[Bariery informacyjne](../compliance/information-barriers.md)|
|Miejsce przechowywania danych|||
||Przechowywanie danych w określonych lokalizacjach geograficznych|[Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>Przechowywanie informacji

Zasady przechowywania są dostępne do przechowywania lub usuwania elementów używanych do współpracy w grupach i zespołach, w tym plików, wiadomości i poczty. Zasady można ustawić tak, aby były zachowywane i usuwane, tylko do zachowania lub usuwania. Informacje objęte zasadami przechowywania są chronione w przypadku wygaśnięcia lub usunięcia grupy lub zespołu.

Konfigurowanie zasad przechowywania dla Grupy Microsoft 365 obejmuje skrzynkę pocztową grupy oraz skojarzoną SharePoint witrynę i pliki.

- [Dowiedz się więcej o zasadach przechowywania dla SharePoint i OneDrive](../compliance/retention-policies-sharepoint.md)

Zasady przechowywania dla Teams zachować wiadomości czatu i kanału. Wiadomości czatu i kanału są przechowywane w Exchange skrzynkach pocztowych, ale zasady przechowywania Exchange nie mają na nie wpływu. Należy ustawić zasady przechowywania, aby były stosowane do czatów Teams i wiadomości kanałów Teams. 

Czaty użytkowników są zachowywane przez czas nieokreślony, nawet jeśli konto użytkownika zostało usunięte. Jeśli nie chcesz przechowywać tych danych przez czas nieokreślony, rozważ użycie zasad przechowywania, aby usunąć czaty użytkowników po określonym czasie lub uwzględnić to usunięcie w procesie usuwania użytkownika.

- [Dowiedz się więcej o zasadach przechowywania dla Microsoft Teams](../compliance/retention-policies-teams.md)

- [Zasady przechowywania w Microsoft Teams](/microsoftteams/retention-policies)

Pojedyncze zasady przechowywania można ustawić tak, aby były stosowane do wiadomości Teams czatu i kanału Teams. 

Dodatkowe zasoby:

- [Dowiedz się więcej o zasadach przechowywania](../compliance/retention.md)

- [Tagi przechowywania i zasady przechowywania](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) w Exchange

## <a name="information-classification"></a>Klasyfikacja informacji

Etykiet poufności można używać do zarządzania dostępem gościa, prywatnością grupy i zespołu oraz dostępem przez niezarządzane urządzenia dla grup i zespołów. Stosując etykietę, te ustawienia są automatycznie konfigurowane zgodnie z ustawieniami etykiety.

- [Używanie etykiet poufności do ochrony zawartości w witrynach Microsoft Teams, Microsoft 365 i SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)

Można skonfigurować Microsoft 365 do automatycznego stosowania etykiet poufności do plików i wiadomości e-mail na podstawie określonych kryteriów, w tym wykrywania typów informacji poufnych lub dopasowywania wzorców do klasyfikatorów z możliwością trenowania.

- [Automatyczne stosowanie etykiety poufności do zawartości](../compliance/apply-sensitivity-label-automatically.md)

Etykiet poufności można używać do szyfrowania plików, umożliwiając odszyfrowywanie i odczytywanie tylko tych, którzy mają uprawnienia.

- [Ogranicz dostęp do zawartości przy użyciu etykiet poufności w celu zastosowania szyfrowania](../compliance/encryption-sensitivity-labels.md)

- [Konfigurowanie zespołu z izolacją zabezpieczeń](./secure-teams-security-isolation.md)

Dodatkowe zasoby:

- [Dowiedz się więcej o etykietach poufności](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>Ochrona informacji

Zasady DLP mogą zapobiegać przypadkowemu udostępnianiu poufnych informacji w SharePoint, Exchange i Teams. Można utworzyć zasady określające akcje do wykonania (takie jak blokowanie dostępu) na podstawie zestawu reguł.

- [Dowiedz się więcej o ochronie przed utratą danych](../compliance/dlp-learn-about-dlp.md)

Protokół DLP w Teams może pomóc w ochronie poufnych informacji w Teams wiadomościach czatu i kanału przez usunięcie wiadomości zawierających poufne informacje.

- [Zapobieganie utracie danych i Microsoft Teams](../compliance/dlp-microsoft-teams.md)

Jeśli masz poufne informacje unikatowe dla organizacji, takie jak nazwy kodu projektu, możesz utworzyć własne typy informacji poufnych i zastosować je do zasad DLP, aby chronić zawartość w grupach, zespołach i SharePoint.

- [Niestandardowe typy informacji poufnych](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>Segmentacja użytkowników

Dzięki barierom informacyjnym możesz podzielić dane i użytkowników na segmenty, aby ograniczyć niepożądaną komunikację i współpracę między grupami oraz uniknąć konfliktów interesów w organizacji. Bariery informacyjne umożliwiają tworzenie zasad umożliwiających współpracę plików, rozmowy, rozmowy lub zaproszenia na spotkania między grupami osób w organizacji lub uniemożliwiają ich współpracę.

- [Bariery informacyjne](../compliance/information-barriers.md)

- [Bariery informacyjne w Microsoft Teams](/microsoftteams/information-barriers-in-teams)

- [Używanie barier informacyjnych z SharePoint](/sharepoint/information-barriers)

## <a name="data-residency"></a>Miejsce przechowywania danych

Dzięki Microsoft 365 Multi-Geo można aprowizować i przechowywać dane magazynowane w lokalizacjach geograficznych wybranych w celu spełnienia wymagań dotyczących przechowywania danych. W środowisku z wieloma lokalizacjami geograficznymi dzierżawa Microsoft 365 składa się z centralnej lokalizacji (w której pierwotnie aprowizowano subskrypcję Microsoft 365) oraz co najmniej jednej lokalizacji satelitarnej, w której można przechowywać dane.

- [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [Planowanie Microsoft 365 multi-geo](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Zabezpieczenia i zgodność dla Exchange Online](/exchange/security-and-compliance/security-and-compliance)

[Ochrona informacji](../compliance/information-protection.md)
