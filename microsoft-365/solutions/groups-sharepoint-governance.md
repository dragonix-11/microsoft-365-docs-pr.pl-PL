---
title: Ustawienia interakcje między Microsoft 365 grupami i SharePoint
ms.reviewer: mmclean
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
description: Informacje o interakcjach ustawień między Microsoft 365 grupami i SharePoint
ms.openlocfilehash: 76f3772685dbf67e61d68a47373f514ab2dabfbc
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005211"
---
# <a name="settings-interactions-between-microsoft-365-groups-and-sharepoint"></a>Ustawienia interakcje między Microsoft 365 grupami i SharePoint

Niektóre ustawienia grup Microsoft 365 i SharePoint w Microsoft 365, w szczególności związane z udostępnianiem, tworzeniem grup i witryn  zespołowych, nakładają się wzajemnie. Ten artykuł zawiera opisy tych interakcji oraz najlepsze rozwiązania dotyczące pracy z tymi ustawieniami.

![Diagram Venna przedstawiający SharePoint, Yammer i grup.](../media/groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-microsoft-365-groups"></a>Efekty ustawień SharePoint grup Microsoft 365 grupy

|SharePoint ustawienia|Opis|Wpływ na Microsoft 365 grup|Zalecenie|
|:-----------------|:----------|:-----------------------------|:-------------|
|Udostępnianie zewnętrzne w organizacji i witrynie|Określa, czy witryny, pliki i foldery można udostępniać osobom spoza organizacji.|Jeśli SharePoint grupy i ustawienia grupy są inne, goście w grupie mogą mieć zablokowany dostęp do witryny lub dostęp zewnętrzny może być dostępny w witrynie, ale nie w grupie.|Podczas zmieniania ustawień udostępniania sprawdź ustawienia grup i SharePoint witryny dla witryn zespołu połączonych z grupą.<br><br>Zobacz [Współpraca z gośćmi w witrynie](./collaborate-in-site.md).|
|Zezwalanie/blokowanie domeny|Zezwala na dostęp do zawartości w określonych domenach lub zapobiega jej udostępnianiu.|Grupy nie rozpoznają list SharePoint ani list zablokowanych. Użytkownicy z domen niedozwolone w SharePoint mogą uzyskać dostęp do SharePoint za pośrednictwem grupy.|Zarządzaj listami zezwalania na domeny i listami zablokowanymi dla usługi Azure AD SharePoint domenami jednocześnie. Tworzenie procesu zarządzania dla całej organizacji w celu zezwalania na domeny i blokowania ich.<br><br>Zobacz [SharePoint ustawień domeny i](/sharepoint/restricted-domains-sharing) [ustawienia domeny usługi Azure AD](/azure/active-directory/b2b/allow-deny-list)|
|Zezwalanie na zewnętrzne udostępnianie plików tylko użytkownikom w określonych grupach zabezpieczeń|Określa grupy zabezpieczeń, które mogą udostępniać witryny, foldery i pliki na zewnątrz.|To ustawienie nie ma wpływu na właścicieli grup udostępniając grupy zewnętrznie. Goście grupy mają dostęp do skojarzonej SharePoint sieci Web.||
|SharePoint ustawień udostępniania witryn|Określa, kto może udostępniać witrynę bezpośrednio poza członkostwem w grupie. Ta konfiguracja jest konfigurowana przez właściciela witryny lub grupy.|To ustawienie nie wpływa bezpośrednio na grupę, ale umożliwia dodanie użytkowników do witryny bez dostępu do innych zasobów grupy|Rozważ użycie tego ustawienia, aby bezpośrednio ograniczyć udostępnianie witryny i zarządzać dostępem do witryny za pośrednictwem grupy.|
|Umożliwianie użytkownikom tworzenia witryn na SharePoint startowej i w OneDrive|Określa, czy użytkownicy mogą tworzyć nowe SharePoint witryny.|Jeśli to ustawienie jest wyłączone, użytkownicy nadal mogą tworzyć witryny zespołu połączone z grupą, tworząc grupę.||

## <a name="the-effects-of-microsoft-365-groups-setting-on-sharepoint"></a>Efekty ustawienia Microsoft 365 grup na SharePoint

|Microsoft 365 grup|Opis|Wpływ na SharePoint|Zalecenie|
|:---------------------------|:----------|:-------------------|:-------------|
|Zasady nazewnictwa|Określa prefiksy i sufiksy nazw grup oraz blokowane wyrazy do tworzenia grup|Zasady są wymuszane dla użytkowników tworzących witryny zespołu połączone z grupą, ale nie witryn do komunikacji z innymi szablonami.|W razie potrzeby utwórz oddzielne wskazówki nazewnictwa dla witryn do komunikacji.|
|Dostęp gościa do grupy|Określa, czy osoby spoza organizacji mogą być dodawane do grup.|Jeśli SharePoint grupy i ustawienia grupy są inne, goście w grupie mogą mieć zablokowany dostęp do witryny lub dostęp zewnętrzny może być dostępny w witrynie, ale nie w grupie.|Podczas zmieniania ustawień udostępniania sprawdź ustawienia grup i SharePoint witryny dla witryn zespołu połączonych z grupą.<br><br>Zobacz [Współpraca z gośćmi w witrynie](./collaborate-in-site.md)|
|Tworzenie grup według grupy zabezpieczeń|Grupy mogą tworzyć tylko członkowie określonej grupy zabezpieczeń.|Użytkownicy, którzy nie są członkami grupy zabezpieczeń, nie będą mogli tworzyć witryny zespołu połączonej z grupą.|Pamiętaj, aby proces żądania grupy zawiera instrukcje dotyczące żądania witryny.|
|Zasady wygasania grupy|Określa okres, po upływie którego grupy, które nie są aktywnie używane, zostaną automatycznie usunięte.|Po usunięciu grupy skojarzona SharePoint również usuwana. Zawartość chroniona przez zasady przechowywania jest zachowywana.|Użyj zasad wygasania, aby uniknąć problemów z nieużywanymi grupami i witrynami.|

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Współpraca z osobami spoza organizacji](./collaborate-with-people-outside-your-organization.md)

[Zarządzanie tworzeniem witryn w SharePoint](/sharepoint/manage-site-creation)