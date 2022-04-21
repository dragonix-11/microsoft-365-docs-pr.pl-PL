---
title: Zalecane zasady bezpiecznego dokumentu — Microsoft 365 dla | przedsiębiorstwa Microsoft Docs
description: W tym artykule opisano zasady dotyczące zaleceń firmy Microsoft dotyczących zabezpieczania dostępu SharePoint plików.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 3a2a8e5be8fb78824e8670f94a2e087da9538329
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972150"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Zalecenia dotyczące zasad dotyczące zabezpieczania witryn i plików SharePoint

W tym artykule opisano sposób implementowania zalecanych zasad Zero Trust tożsamości i dostępu do urządzeń w celu ochrony SharePoint i OneDrive dla Firm. Te wskazówki bazują na [typowych zasadach dostępu do tożsamości i urządzeń](identity-access-policies.md).

Te zalecenia są oparte na trzech różnych warstwach zabezpieczeń i ochrony dla plików SharePoint, które mogą być stosowane w oparciu o stopień szczegółowości twoich potrzeb: **punkt początkowy**, **przedsiębiorstwo** i **wyspecjalizowane zabezpieczenia**. Więcej informacji na temat tych warstw zabezpieczeń i zalecanych systemów operacyjnych klienta, do których odnoszą się te zalecenia, można znaleźć w [omówieniu](microsoft-365-policies-configurations.md).

Oprócz zaimplementowania tych wskazówek należy skonfigurować witryny SharePoint z odpowiednią ochroną, w tym ustawić odpowiednie uprawnienia dla zawartości zabezpieczeń dla przedsiębiorstw i wyspecjalizowanych.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Aktualizowanie typowych zasad w celu uwzględnienia SharePoint i OneDrive dla Firm

Aby chronić pliki w SharePoint i OneDrive, na poniższym diagramie przedstawiono zasady, które należy zaktualizować na podstawie typowych zasad dostępu do tożsamości i urządzeń.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="Podsumowanie aktualizacji zasad dotyczących ochrony dostępu do SharePoint" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

Jeśli podczas tworzenia typowych zasad uwzględniono SharePoint, musisz tylko utworzyć nowe zasady. W przypadku zasad dostępu warunkowego SharePoint obejmuje OneDrive.

Nowe zasady implementują ochronę urządzeń dla zawartości zabezpieczeń dla przedsiębiorstw i wyspecjalizowanych, stosując określone wymagania dotyczące dostępu do określonych witryn SharePoint.

Poniższa tabela zawiera listę zasad, które należy przejrzeć i zaktualizować lub utworzyć nowe dla SharePoint. Typowe zasady łączą się ze skojarzonymi instrukcjami konfiguracji w artykule [Common identity and device access policies (Typowe zasady dotyczące tożsamości i dostępu do urządzeń](identity-access-policies.md) ).

|Poziom ochrony|Policies (zasady)|Więcej informacji|
|---|---|---|
|**Punkt początkowy**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest *średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Uwzględnij SharePoint w przypisywaniu aplikacji w chmurze.|
||[Blokuj klientów, którzy nie obsługują nowoczesnego uwierzytelniania](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Uwzględnij SharePoint w przypisywaniu aplikacji w chmurze.|
||[Stosowanie zasad ochrony danych aplikacji](identity-access-policies.md#apply-app-data-protection-policies)|Upewnij się, że wszystkie zalecane aplikacje znajdują się na liście aplikacji. Pamiętaj, aby zaktualizować zasady dla każdej platformy (iOS, Android, Windows).|
||[Używanie ograniczeń wymuszonych przez aplikację w SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Dodaj te nowe zasady. Dzięki temu Azure Active Directory (Azure AD) będzie używać ustawień określonych w SharePoint. Te zasady mają zastosowanie do wszystkich użytkowników, ale mają wpływ tylko na dostęp do witryn zawartych w zasadach dostępu SharePoint.|
|**Enterprise**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest *niskie*, *średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Dołącz SharePoint do przypisań aplikacji w chmurze.|
||[Wymagaj zgodnych komputerów *i* urządzeń przenośnych](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Uwzględnij SharePoint na liście aplikacji w chmurze.|
||[SharePoint zasad kontroli dostępu](#sharepoint-access-control-policies): zezwalaj na dostęp tylko do przeglądarki do określonych witryn SharePoint z urządzeń niezarządzanych.|Uniemożliwia to edytowanie i pobieranie plików. Użyj programu PowerShell, aby określić lokacje.|
|**Wyspecjalizowane zabezpieczenia**|[*Zawsze* wymagaj uwierzytelniania wieloskładnikowego](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Uwzględnij SharePoint w przypisywaniu aplikacji w chmurze.|
||[SharePoint zasad kontroli dostępu](#use-app-enforced-restrictions-in-sharepoint): blokuj dostęp do określonych witryn SharePoint z urządzeń niezarządzanych.|Użyj programu PowerShell, aby określić lokacje.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Używanie ograniczeń wymuszonych przez aplikację w SharePoint

Jeśli zaimplementujesz mechanizmy kontroli dostępu w SharePoint, zasady dostępu warunkowego zostaną utworzone w usłudze Azure AD, aby poinformować usługę Azure AD o wymuszaniu zasad skonfigurowanych w SharePoint. Domyślnie te zasady mają zastosowanie do wszystkich użytkowników, ale mają wpływ tylko na dostęp do witryn określonych przy użyciu programu PowerShell podczas tworzenia kontrolek dostępu w SharePoint. Zasady mogą być również ograniczone do określonych użytkowników, grup lub witryn.

Aby skonfigurować te zasady, zobacz "Blokuj lub ograniczaj dostęp do określonych SharePoint zbiorów witryn lub kont OneDrive" w [temacie Kontrola dostępu z urządzeń niezarządzanych](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>zasady kontroli dostępu SharePoint

Firma Microsoft zaleca ochronę zawartości w witrynach SharePoint z zawartością dla przedsiębiorstw i wyspecjalizowaną zawartością zabezpieczeń za pomocą mechanizmów kontroli dostępu do urządzeń. Można to zrobić, tworząc zasady określające poziom ochrony i witryny, do których ma zostać zastosowana ochrona.

- Enterprise witryn: zezwalaj na dostęp tylko do przeglądarki. Uniemożliwia to użytkownikom edytowanie i pobieranie plików.
- Wyspecjalizowane witryny zabezpieczeń: blokuj dostęp z urządzeń niezarządzanych.

Zobacz sekcję "Blokuj lub ogranicz dostęp do określonych SharePoint zbiorów witryn lub kont OneDrive" w [temacie Kontrolowanie dostępu z urządzeń niezarządzanych](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>Jak te zasady współpracują ze sobą

Ważne jest, aby zrozumieć, że uprawnienia SharePoint lokacji są zwykle oparte na potrzebach biznesowych dostępu do witryn. Te uprawnienia są zarządzane przez właścicieli witryn i mogą być bardzo dynamiczne. Korzystanie z SharePoint zasad dostępu urządzeń zapewnia ochronę tych witryn niezależnie od tego, czy użytkownicy są przypisani do grupy usługi Azure AD skojarzonej z punktem początkowym, przedsiębiorstwem czy wyspecjalizowaną ochroną zabezpieczeń.

Poniższa ilustracja przedstawia przykład sposobu, w jaki zasady dostępu SharePoint urządzenia chronią dostęp użytkownika do witryn.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="Przykład sposobu ochrony witryn SharePoint zasad dostępu urządzeń" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

James ma przypisane zasady dostępu warunkowego punktu początkowego, ale może mieć dostęp do SharePoint lokacji z ochroną przedsiębiorstwa lub wyspecjalizowaną ochroną zabezpieczeń.

- Jeśli James uzyskuje dostęp do witryny, którą należy do przedsiębiorstwa lub wyspecjalizowanej ochrony zabezpieczeń przy użyciu swojego komputera, jego dostęp jest udzielany.
- Jeśli James uzyskuje dostęp do witryny ochrony przedsiębiorstwa, jest członkiem jego niezarządzanego telefonu, co jest dozwolone dla użytkowników punktu początkowego, otrzyma dostęp tylko do przeglądarki do witryny przedsiębiorstwa ze względu na zasady dostępu urządzeń skonfigurowane dla tej witryny.
- Jeśli James uzyskuje dostęp do wyspecjalizowanej witryny zabezpieczeń, jest członkiem jego niezarządzanego telefonu, zostanie zablokowany ze względu na zasady dostępu skonfigurowane dla tej witryny. Dostęp do tej witryny można uzyskać tylko przy użyciu zarządzanego komputera.

## <a name="next-step"></a>Następny krok

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Krok 4 — zasady dotyczące aplikacji w chmurze Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Skonfiguruj zasady dostępu warunkowego dla:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
