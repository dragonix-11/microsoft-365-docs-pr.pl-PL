---
title: Współpraca z osobami spoza organizacji
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się, jak skonfigurować Microsoft 365, takie jak Teams, OneDrive i SharePoint do współpracy z osobami spoza organizacji.
ms.openlocfilehash: 65511cbafdc1f5a666c11e1bef7fefd6e6852ee3
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712779"
---
# <a name="collaborating-with-people-outside-your-organization"></a>Współpraca z osobami spoza organizacji

Funkcje udostępniania zewnętrznego w usłudze Microsoft 365 zapewniają osobom w Twojej organizacji możliwość współpracy z partnerami, dostawcami, klientami i innymi osobami, które nie mają konta w katalogu. Możesz udostępniać całe zespoły, kanały lub witryny osobom spoza organizacji lub tylko poszczególnym plikom.

Współpraca z osobami spoza organizacji składa się z tych głównych składników:

- **Włącz** udostępnianie — skonfiguruj kontrolki udostępniania Azure Active Directory, Teams, Microsoft 365 Grup SharePoint, aby zezwolić na poziom udostępniania, który chcesz udostępnić organizacji.
- **Konfigurowanie relacji** organizacyjnych — jeśli korzystasz z kanałów udostępnionych, musisz skonfigurować ustawienia dostępu między dzierżawami w programie Azure Active Directory, aby zezwolić na dostęp bezpośredni B2B dla każdej organizacji, z którą chcesz współpracować. (Te organizacje muszą także skonfigurować relacje organizacyjne z dzierżawą).
- Włączanie dodatkowych **zabezpieczeń — podczas** gdy podstawowe funkcje udostępniania można skonfigurować tak, aby wymagały uwierzytelniania osób spoza organizacji, program Microsoft 365 oferuje wiele dodatkowych funkcji zabezpieczeń i zgodności, które pomagają chronić dane i zachować zasady zarządzania podczas udostępniania zewnętrznego.

Przeczytaj [Konfigurowanie bezpiecznej współpracy z](/microsoft-365/solutions/setup-secure-collaboration-with-teams) innymi Microsoft 365 i Microsoft Teams, aby dowiedzieć się, w jaki sposób udostępnianie zewnętrzne wiąże się z ogólnymi wskazówkami Microsoft 365 współpracy.

## <a name="enable-sharing"></a>Włączanie udostępniania

Domyślnie udostępnianie osobom spoza organizacji przy użyciu dostępu gościa lub dostępu anonimowego jest włączone, ale kanały udostępnione muszą być włączone przez skonfigurowanie relacji organizacyjnych w usłudze Azure AD. Większość scenariuszy udostępniania gościa działa bez dalszej konfiguracji. Aby potwierdzić ustawienia dla scenariusza lub włączyć nowy, wybierz jedną z następujących opcji:

- [Współpraca nad dokumentami](collaborate-on-documents.md) — dowiedz się, jak Microsoft 365 zezwolić na udostępnianie i współpracę z osobami spoza organizacji (zarówno gośćmi, jak i nieuwierzytami użytkownikami) nad plikami i folderami.
- [Współpraca w witrynie —](collaborate-in-site.md) dowiedz się, jak skonfigurować usługę Microsoft 365 w celu umożliwienia SharePoint witryn gościom.
- [Współpraca w zespole — dowiedz](collaborate-as-team.md) się, jak skonfigurować usługę Microsoft 365 w celu umożliwienia współpracy gościa w Teams.
- [Współpracuj z uczestnikami zewnętrznymi w kanale](/microsoft-365/solutions/collaborate-teams-direct-connect) w celu współpracy z osobami spoza organizacji w kanale udostępnionym.

Aby uzyskać pełny przegląd ustawień udostępniania gościa dostępnych w różnych Microsoft 365, zobacz Microsoft 365 [informacje dotyczące ustawień udostępniania gościa](microsoft-365-guest-settings.md).

## <a name="enable-additional-security"></a>Włącz dodatkowe zabezpieczenia

Po włączeniu scenariusza, który ma być przez Ciebie udostępniany osobom spoza organizacji, rozważ dodatkowe środki zabezpieczające przed przypadkowym lub celowym udostępnianiem zawartości.

- [Najlepsze rozwiązania dotyczące udostępniania](best-practices-anonymous-sharing.md) plików i folderów nieuwierzysznionym użytkownikom — poznaj najlepsze rozwiązania dotyczące udostępniania nieuwierzytanych użytkowników.
- [Ogranicz przypadkowy dostęp](share-limit-accidental-exposure.md) — dowiedz się, jak ograniczyć ryzyko przypadkowego udostępniania poufnej zawartości osobom spoza organizacji.
- [Tworzenie](create-secure-guest-sharing-environment.md) bezpiecznego środowiska udostępniania gości — dowiedz się więcej o narzędziach dostępnych w programie Microsoft 365, aby zapewnić bezpieczne i bezpieczne udostępnianie danych osobom spoza organizacji oraz spełniać wymagania w zakresie zarządzania.

## <a name="collaborate-with-partner-companies"></a>Współpraca z firmami partnerskimi

Jeśli pracujesz nad dużym projektem, który obejmuje gości z innej organizacji, rozważ kanały udostępnione. Ponieważ kanały udostępnione nie korzystają z kont gości, użytkownicy w innej organizacji mogą uzyskać dostęp do kanału udostępnionego bezpośrednio bez konieczności osobnego logowania się do organizacji.

Jeśli masz bieżącą relację z dostawcami, w której goście często się zmieniają, możesz skorzystać z zarządzania uprawnieniami w programie Azure Active Directory, aby uprościć zarządzanie gośćmi i umożliwić firmie partnerskiej udostępnianie tych obowiązków. Aby [uzyskać szczegółowe informacje, zobacz Tworzenie ekstranetu B2B z zarządzanymi gośćmi](b2b-extranet.md) .

## <a name="limit-sharing"></a>Ogranicz udostępnianie

Jeśli niektóre funkcje udostępniania w programie Microsoft 365 być w konflikcie z zasadami zarządzania, zobacz Ograniczanie udostępniania w programie [Microsoft 365](microsoft-365-limit-sharing.md), aby dowiedzieć się więcej o możliwościach ograniczenia udostępniania.

## <a name="related-topics"></a>Tematy pokrewne

[Wprowadzenie do współpracy nad plikami w Microsoft 365](/sharepoint/intro-to-file-collaboration)

[Planowanie współpracy nad plikami w SharePoint za pomocą Microsoft 365](/sharepoint/deploy-file-collaboration)
