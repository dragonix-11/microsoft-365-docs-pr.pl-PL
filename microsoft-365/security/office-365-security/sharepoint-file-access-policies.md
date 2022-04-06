---
title: Zalecane zasady bezpiecznego dokumentu — Microsoft 365 dla firm | Microsoft Docs
description: W tym artykule opisano zasady zalecenia firmy Microsoft dotyczące sposobu zabezpieczania SharePoint dostępu do plików.
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
ms.openlocfilehash: 3057e66352b9bd658ddd4958986cbefd61e4e187
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682950"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Zalecenia dotyczące zasad dotyczące zabezpieczania SharePoint witryn i plików

W tym artykule opisano sposób wdrażania zalecanych zasad dostępu do urządzeń i tożsamości bez zaufania w celu ochrony SharePoint i OneDrive dla Firm. Te wskazówki są opierane na [wspólnych zasadach dostępu do tożsamości i urządzeń](identity-access-policies.md).

Zalecenia te są oparte na trzech różnych warstwach zabezpieczeń i ochrony dla plików SharePoint, które można stosować w zależności od stopnia szczegółowości Twoich **potrzeb: punktu** początkowego **,** przedsiębiorstwa i wyspecjalizowanego **zabezpieczeń**. Możesz dowiedzieć się więcej o tych warstwach zabezpieczeń i zalecanych systemach operacyjnych klientów, do których odwołujemy się w [omówieniem](microsoft-365-policies-configurations.md).

Oprócz wdrażania tych wskazówek pamiętaj o skonfigurowaniu witryn SharePoint z odpowiednią ochroną, łącznie z ustawieniem odpowiednich uprawnień dla przedsiębiorstw i specjalistycznej zawartości zabezpieczeń.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Aktualizowanie wspólnych zasad w celu SharePoint i OneDrive dla Firm

Aby chronić pliki w SharePoint i OneDrive, na poniższym diagramie pokazano zasady, które należy aktualizować na przykładach typowych zasad dostępu do urządzeń i tożsamości.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="Podsumowanie aktualizacji zasad w celu ochrony dostępu do SharePoint." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

Jeśli podczas tworzenia SharePoint uwzględniono zasady wspólne, wystarczy utworzyć tylko nowe zasady. W przypadku zasad dostępu warunkowego SharePoint także OneDrive.

Nowe zasady implementują ochronę urządzeń dla przedsiębiorstw i wyspecjalizowaną zawartość zabezpieczeń przez stosowanie określonych wymagań dostępu do SharePoint określonych przez Ciebie.

W poniższej tabeli wymieniono zasady, które należy przejrzeć i zaktualizować lub utworzyć nowe dla SharePoint. Typowe zasady są linkiem do skojarzonych instrukcji konfiguracji podanych w [artykule Typowe zasady](identity-access-policies.md) dostępu do urządzeń i tożsamości.

|Poziom ochrony|Policies (zasady)|Więcej informacji|
|---|---|---|
|**Punkt początkowy**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania *jest średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Dołącz SharePoint do przypisywania aplikacji w chmurze.|
||[Blokowanie klientów, którzy nie obsługują nowoczesnego uwierzytelniania](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Dołącz SharePoint do przypisywania aplikacji w chmurze.|
||[Stosowanie zasad ochrony danych aplikacji](identity-access-policies.md#apply-app-data-protection-policies)|Upewnij się, że na liście aplikacji znajdują się wszystkie zalecane aplikacje. Pamiętaj o zaktualizowaniu zasad dla każdej platformy (systemy iOS, Android, Windows).|
||[Stosowanie ograniczeń aplikacji wymuszonych w SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Dodaj te nowe zasady. Oznacza to Azure Active Directory że usługa Azure AD ma używać ustawień określonych w programie SharePoint. Te zasady dotyczą wszystkich użytkowników, ale mają wpływ tylko na dostęp do witryn SharePoint dostępu.|
|**Enterprise**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania *jest niskie, średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Dołącz SharePoint do zadań aplikacji w chmurze.|
||[Wymaganie zgodności komputerów i *urządzeń* przenośnych](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Dołącz SharePoint na liście aplikacji w chmurze.|
||[SharePoint kontroli dostępu](#sharepoint-access-control-policies): Zezwalaj na dostęp tylko w przeglądarce do określonych witryn SharePoint z urządzeń niezawiązywanych.|Uniemożliwia to edytowanie i pobieranie plików. Do określania witryn użyj programu PowerShell.|
|**Wyspecjalizowane zabezpieczenia**|[*Zawsze wymagaj* uwierzytelniania wieloskładnikowego](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Dołącz SharePoint do przypisywania aplikacji w chmurze.|
||[SharePoint kontroli dostępu](#use-app-enforced-restrictions-in-sharepoint): Blokowanie dostępu do określonych witryn SharePoint z urządzeń niezawiązywanych.|Do określania witryn użyj programu PowerShell.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Stosowanie ograniczeń wymuszonych przez aplikację w SharePoint

Jeśli implementujesz kontrolki dostępu w programie SharePoint, musisz utworzyć te zasady dostępu warunkowego w usłudze Azure AD, aby skonfigurować zasady konfigurowane w usłudze Azure AD SharePoint. Te zasady dotyczą wszystkich użytkowników, ale mają wpływ tylko na dostęp do witryn określanych przy użyciu programu PowerShell podczas tworzenia kontrolek dostępu w programie SharePoint.

Aby skonfigurować te zasady, zobacz "Blokowanie lub ograniczanie dostępu do określonych SharePoint witryn lub kont OneDrive" w tece Kontrolowanie dostępu z [](/sharepoint/control-access-from-unmanaged-devices)urządzeń niezawiąanych.

## <a name="sharepoint-access-control-policies"></a>SharePoint kontroli dostępu

Firma Microsoft zaleca ochronę zawartości w witrynach SharePoint za pomocą zawartości zabezpieczeń przedsiębiorstwa i specjalistycznej zawartości zabezpieczeń za pomocą kontrolek dostępu urządzeń. W tym celu należy utworzyć zasady określające poziom ochrony oraz witryny, do których ma być stosowane zabezpieczenie.

- Enterprise witryny: Zezwalaj na dostęp tylko w przeglądarce. Uniemożliwia to użytkownikom edytowanie i pobieranie plików.
- Wyspecjalizowane witryny zabezpieczeń: Blokuj dostęp z urządzeń niezamanektowych.

Zobacz "Blokowanie lub ograniczanie dostępu do określonych SharePoint witryn lub kont OneDrive" w tece Kontrolowanie dostępu z urządzeń [niezamenunych](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>Jak te zasady współpracują

Ważne jest, aby zrozumieć, że SharePoint witryn są zazwyczaj oparte na potrzebie biznesowej dotyczącej dostępu do witryn. Te uprawnienia są zarządzane przez właścicieli witryn i mogą być bardzo dynamiczne. Korzystanie SharePoint dostępu do urządzeń zapewnia ochronę tych witryn niezależnie od tego, czy użytkownicy są przypisani do grupy usługi Azure AD skojarzonej z punktem początkowym, przedsiębiorstwem, czy wyspecjalizowaną ochroną zabezpieczeń.

Na poniższej ilustracji przedstawiono przykłady ochrony SharePoint dostępu do urządzeń w celu ochrony dostępu użytkownika do witryn.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="Przykład ochrony SharePoint dostępu do urządzenia." lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

Jakub ma przypisane zasady dostępu warunkowego, ale może mieć dostęp do witryn SharePoint firmowej lub specjalistycznej ochrony zabezpieczeń.

- Jeśli Jakub uzyskuje dostęp do witryny, dokad jest członkiem przedsiębiorstwa lub specjalistycznej ochrony zabezpieczeń za pomocą komputera, jest udzielany mu dostęp.
- Jeśli Jakub uzyskuje dostęp do witryny ochrony przedsiębiorstwa, jest członkiem zespołu korzystającego ze swojego telefonu nieza zarządzaniem, co jest dozwolone dla użytkowników początkowych, otrzyma dostęp tylko do witryny przedsiębiorstwa w przeglądarce ze względu na zasady dostępu do urządzeń skonfigurowane dla tej witryny.
- Jeśli Jakub uzyskuje dostęp do specjalistycznej witryny zabezpieczeń, jest członkiem korzystania z jego telefonu niezakierowanych, zostanie zablokowany z powodu zasad dostępu skonfigurowanych dla tej witryny. Może on uzyskać dostęp do tej witryny tylko za pomocą swojego zarządzanego komputera.

## <a name="next-step"></a>Następny krok

![Krok 4. Zasady dotyczące aplikacji Microsoft 365 chmurze.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Skonfiguruj zasady dostępu warunkowego dla:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)