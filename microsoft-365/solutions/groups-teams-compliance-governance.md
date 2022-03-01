---
title: Opcje zgodności dla grup Microsoft 365, grup Teams i SharePoint współpracy
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
description: Dowiedz się więcej o opcjach zgodności Microsoft 365 grup, Teams i SharePoint współpracy.
ms.openlocfilehash: ab840ea5652a13087ecc8d505391bac152ca1052
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63004956"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Opcje zgodności dla grup Microsoft 365, grup Teams i SharePoint współpracy

Microsoft 365 oferuje pełny zestaw narzędzi do zachowania zgodności podczas współpracy z innymi użytkownikami. Przejrzyj te opcje i rozważ ich mapowanie na potrzeby Twojej firmy, czułość danych i zakres osób, z którymi twoi użytkownicy muszą współpracować.

W poniższej tabeli przedstawiono podręczną informacje na temat kontrolek zgodności dostępnych w programie Microsoft 365. Dalsze informacje podano w poniższych sekcjach.

|Kategoria|Opis|Odwołanie|
|:-------|:----------|:--------|
|Przechowywanie informacji|||
||Zachowywanie poczty grupy i SharePoint zawartości|[Informacje o zasadach przechowywania dla SharePoint i OneDrive](../compliance/retention-policies-sharepoint.md)|
||Zachowywanie czatu i wiadomości|[Informacje o zasadach przechowywania dla Microsoft Teams](../compliance/retention-policies-teams.md)|
|Klasyfikacja informacji|||
||Klasyfikowanie grup i zespołów|[Używanie etykiet wrażliwości w celu ochrony zawartości Microsoft Teams, grup Microsoft 365 i SharePoint internetowych](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Automatyczne klasyfikowanie poufnej zawartości|[Automatyczne stosowanie etykiet wrażliwości do zawartości](../compliance/apply-sensitivity-label-automatically.md)|
||Szyfrowanie zawartości poufnej|[Ograniczanie dostępu do zawartości przy użyciu etykiet wrażliwości w celu zastosowania szyfrowania](../compliance/encryption-sensitivity-labels.md)|
|Ochrona informacji|||
||Zapobieganie utracie informacji poufnych|[Informacje na temat ochrony przed utratą danych](../compliance/dlp-learn-about-dlp.md)|
||Ochrona poufnych informacji na czacie.|[Ochrona przed utratą danych i Microsoft Teams](../compliance/dlp-microsoft-teams.md)|
||Definiowanie informacji poufnych organizacji|[Niestandardowe typy informacji poufnych](../compliance/sensitive-information-type-learn-about.md)|
|Segmentacja użytkowników|||
||Ograniczanie komunikacji między segmentami użytkowników|[Bariery informacyjne](../compliance/information-barriers.md)|
|Data residency|||
||Przechowywanie danych w określonych lokalizacjach geograficznych|[Microsoft 365 multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>Przechowywanie informacji

Dostępne są zasady przechowywania w celu przechowywania lub usuwania elementów używanych do współpracy w grupach i zespołach, w tym plików, wiadomości i poczty. Zasady można skonfigurować w celu zachowania i usunięcia, zachowania tylko tych zasad, a także ich usuwania. Informacje objęte zasadami przechowywania są chronione na wypadek, gdyby grupa lub zespół wygasły lub zostały usunięte w inny sposób.

Konfigurowanie zasad przechowywania dla grup Microsoft 365 obejmuje skrzynkę pocztową grupy oraz SharePoint i pliki grupy.

- [Informacje o zasadach przechowywania dla SharePoint i OneDrive](../compliance/retention-policies-sharepoint.md)

Zasady przechowywania dla Teams wiadomości czatu i kanałów. Wiadomości na czacie i kanałach są przechowywane Exchange skrzynkach pocztowych, jednak nie mają one wpływu Exchange przechowywania. Musisz skonfigurować zasady przechowywania, aby stosowane Teams czatach i Teams wiadomościach w kanałach. 

Czaty użytkowników są zachowywane przez czas nieograniczony, nawet po usunięciu konta użytkownika. Jeśli nie chcesz zachować tych danych przez czas nieograniczony, rozważ usunięcie czatów użytkowników po upływie określonego czasu przy użyciu zasad przechowywania lub dołączenie tego usunięcia do procesu usuwania użytkownika.

- [Informacje o zasadach przechowywania dla Microsoft Teams](../compliance/retention-policies-teams.md)

- [Zasady przechowywania w programie Microsoft Teams](/microsoftteams/retention-policies)

Można skonfigurować pojedyncze zasady przechowywania, które będą stosowane do czatu Teams i wiadomości Teams kanałach. 

Dodatkowe zasoby:

- [Informacje o zasadach przechowywania](../compliance/retention.md)

- [Tagi przechowywania i zasady przechowywania w](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) aplikacji Exchange

## <a name="information-classification"></a>Klasyfikacja informacji

Etykiety wrażliwości mogą określać zasady dostępu gości, prywatności grupy i zespołu, a także dostęp do nich za pomocą urządzeń niezawiązywanych dla grup i zespołów. Stosując etykietę, te ustawienia są automatycznie konfigurowane zgodnie z ustawieniami etykiet.

- [Używanie etykiet wrażliwości w celu ochrony zawartości Microsoft Teams, grup Microsoft 365 i SharePoint internetowych](../compliance/sensitivity-labels-teams-groups-sites.md)

Możesz skonfigurować Microsoft 365 automatycznego stosowania etykiet wrażliwości do plików i wiadomości e-mail na podstawie określonych kryteriów, na przykład wykrywania typów informacji poufnych lub dopasowywania wzorców do klasyfikatorów przeszkolnych.

- [Automatyczne stosowanie etykiet wrażliwości do zawartości](../compliance/apply-sensitivity-label-automatically.md)

Za pomocą etykiet wrażliwości możesz szyfrować pliki, zezwalając tylko osobom z uprawnieniami do odszyfrowywania i odczytywania ich.

- [Ograniczanie dostępu do zawartości przy użyciu etykiet wrażliwości w celu zastosowania szyfrowania](../compliance/encryption-sensitivity-labels.md)

- [Konfigurowanie zespołu z izolacji zabezpieczeń](./secure-teams-security-isolation.md)

Dodatkowe zasoby:

- [Dowiedz się więcej o etykietach poufności](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>Ochrona informacji

Zasady DLP mogą zapobiegać przypadkowemu udostępnianiu poufnych informacji w SharePoint, Exchange i Teams. Możesz utworzyć zasady określające akcje do podjęcia (takie jak blokowanie dostępu) na podstawie zestawu reguł.

- [Informacje na temat ochrony przed utratą danych](../compliance/dlp-learn-about-dlp.md)

Ochrona przed Teams w czacie i wiadomościach kanałowych Teams, usuwając wiadomości zawierające informacje poufne.

- [Ochrona przed utratą danych i Microsoft Teams](../compliance/dlp-microsoft-teams.md)

Jeśli masz informacje poufne, które są unikatowe dla Twojej organizacji, takie jak nazwy kodów projektów, możesz utworzyć własne typy informacji poufnych i zastosować je do zasad DLP w celu ochrony zawartości w grupach, zespołach i SharePoint.

- [Niestandardowe typy informacji poufnych](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>Segmentacja użytkowników

Dzięki barierom informacyjnym możesz segmentować dane i użytkowników, aby ograniczyć niechcianą komunikację i współpracę między grupami oraz uniknąć konfliktów zainteresowania w organizacji. Bariery informacyjne pozwalają tworzyć zasady uniemożliwiające współpracę nad plikami, czatowanie, rozmowy telefoniczne lub zaproszenia na spotkania między grupami osób w organizacji.

- [Bariery informacyjne](../compliance/information-barriers.md)

- [Bariery informacyjne w programie Microsoft Teams](/microsoftteams/information-barriers-in-teams)

- [Korzystanie z barier informacyjnych dzięki SharePoint](/sharepoint/information-barriers)

## <a name="data-residency"></a>Data residency

Dzięki Microsoft 365 multi-Geo możesz zapewniać i przechowywać dane w spoczynku w lokalizacjach geograficznych wybranych do spełnienia wymagań dotyczących przechowywania danych. W środowisku z wieloma lokalizacjami geograficznymi dzierżawa usługi Microsoft 365 składa się z lokalizacji centralnej (w której pierwotnie aprowizowana była subskrypcja usługi Microsoft 365) oraz co najmniej jednej lokalizacji satelitarnej, w której można przechowywać dane.

- [Microsoft 365 multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [Planowanie pod Microsoft 365 wielolokalizacji](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Zabezpieczenia i zgodność z przepisami dla Exchange Online](/exchange/security-and-compliance/security-and-compliance)

[Ochrona informacji](../compliance/information-protection.md)
