---
title: Ustawienia interakcje między grupami Microsoft 365, grupami Teams i SharePoint
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
description: Informacje o interakcjach ustawień między grupami Microsoft 365, grupami Teams i SharePoint
ms.openlocfilehash: 64f00fcb5ace9e2f2f4a6630def6beb0a51d40bf
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005209"
---
# <a name="settings-interactions-between-microsoft-365-groups-teams-and-sharepoint"></a>Ustawienia interakcje między grupami Microsoft 365, grupami Teams i SharePoint

Niektóre ustawienia grup Microsoft 365, Microsoft Teams i SharePoint w programie Microsoft 365, w szczególności dotyczące udostępniania, grupowania/zespołu i witryn SharePoint nakładają się ze sobą. Ten artykuł zawiera opisy tych interakcji oraz najlepsze rozwiązania dotyczące pracy z tymi ustawieniami.

![Diagram Venna przedstawiający SharePoint, Teams i grup.](../media/teams-groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-groups-and-teams"></a>Efekty zmiany SharePoint grup i zespołów

|SharePoint ustawienia|Opis|Wpływ na Microsoft 365 grup i Teams|Zalecenie|
|:-----------------|:----------|:---------------------------------------|:-------------|
|Udostępnianie zewnętrzne w organizacji i witrynie|Określa, czy witryny, pliki i foldery można udostępniać osobom spoza organizacji.|Jeśli SharePoint, grupy i Teams nie są zgodne, goście w zespole mogą mieć zablokowany dostęp do witryny lub może wystąpić nieoczekiwany dostęp zewnętrzny.|Podczas zmieniania ustawień udostępniania sprawdzaj ustawienia grup, Teams i SharePoint witryn  zespołu połączonych z grupą.<br><br> Zobacz [Współpraca z gośćmi w zespole](./collaborate-as-team.md)|
|Zezwalanie/blokowanie domeny|Zezwala na dostęp do zawartości w określonych domenach lub zapobiega jej udostępnianiu.|Grupy i Teams nie rozpoznają SharePoint list zablokowanych ani zezwalanych. Użytkownicy z domen niezamówiony w SharePoint mogą uzyskać dostęp do SharePoint witryn lub zawartości za pośrednictwem zespołu.|Zarządzaj listami zezwalania na domeny i listami zablokowanymi dla usługi Azure AD SharePoint domenami jednocześnie. Tworzenie procesu zarządzania dla całej organizacji w celu zezwalania na domeny i blokowania ich.<br><br>Zobacz [SharePoint ustawień domeny i](/sharepoint/restricted-domains-sharing) [ustawienia domeny usługi Azure AD](/azure/active-directory/b2b/allow-deny-list)|
|Zezwalanie na zewnętrzne udostępnianie plików tylko użytkownikom w określonych grupach zabezpieczeń|Określa grupy zabezpieczeń, które mogą SharePoint zewnętrzne witryny internetowe, foldery i pliki.|To ustawienie nie uniemożliwia właścicielom zespołów zewnętrznego udostępniania zespołów. Goście zespołu mają dostęp do skojarzonej SharePoint zespołu.||
|SharePoint ustawień udostępniania witryn|Określa, kto może udostępniać witrynę bezpośrednio poza członkostwem w zespole. Ta konfiguracja jest konfigurowana przez właściciela zespołu lub witryny.|To ustawienie nie wpływa bezpośrednio na zespół, ale umożliwia dodanie użytkowników do witryny i nie ma dostępu do samego zespołu ani innych zasobów Teams zasobów|Rozważ użycie tego ustawienia, aby bezpośrednio ograniczyć udostępnianie witryny i zarządzać dostępem do witryny za pośrednictwem zespołu.|
|Umożliwianie użytkownikom tworzenia witryn na SharePoint startowej i w OneDrive|Określa, czy użytkownicy mogą tworzyć nowe SharePoint witryny.|Jeśli to ustawienie jest wyłączone, użytkownicy mogą nadal tworzyć witryny zespołu połączone z grupą, tworząc zespół.||

## <a name="the-effects-of-groups-settings-on-teams"></a>Efekty ustawień grup w zespołach

|Microsoft 365 grup|Opis|Wpływ na Teams|Zalecenie|
|:---------------------------|:----------|:--------------|:-------------|
|Zasady nazewnictwa|Określa prefiksy i sufiksy nazw grup oraz blokowane wyrazy do tworzenia grup|Zasady są wymuszane dla użytkowników tworzących zespoły.||
|Dostęp gościa do grupy|Określa, czy osoby spoza organizacji mogą być dodawane do grup.|Jeśli grupy lub Teams udostępniania gości są wyłączone, nie można udostępnić zespołu gościom.|Podczas zmieniania ustawień udostępniania gościa sprawdź ustawienia grup Teams Grupy i witryny SharePoint skojarzonej z zespołem.<br><br> Zobacz [Współpraca z gośćmi w zespole](./collaborate-as-team.md)|
|Tworzenie grup według grupy zabezpieczeń|Grupy mogą tworzyć tylko członkowie określonej grupy zabezpieczeń.|Użytkownicy, którzy nie są członkami grupy zabezpieczeń, nie będą mogli utworzyć zespołu.|Pamiętaj, aby proces żądania grupy zawiera instrukcje dotyczące żądania zespołu lub witryny SharePoint sieci Web.|
|Zasady wygasania grupy|Określa okres, po upływie którego grupy, które nie są aktywnie używane, zostaną automatycznie usunięte.|Gdy grupa zostanie usunięta, usunięty zostanie również zespół SharePoint skojarzona z nią witryna. Zawartość chroniona przez zasady przechowywania jest zachowywana.|Użyj zasad wygasania, aby uniknąć problemów z nieużywanymi zespołami, grupami i witrynami.|

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Współpraca z osobami spoza organizacji](./collaborate-with-people-outside-your-organization.md)

[Zarządzanie tworzeniem witryn w SharePoint](/sharepoint/manage-site-creation)