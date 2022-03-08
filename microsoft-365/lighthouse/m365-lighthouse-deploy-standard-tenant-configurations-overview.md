---
title: Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu planu bazowego
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse informacji o wdrażaniu standardowych konfiguracji dzierżawy przy użyciu planu bazowego.
ms.openlocfilehash: f59ca686892e0b20ce5e9ffb6d62859ce8079896
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323153"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu planu bazowego 

Microsoft 365 Lighthouse bazowe zapewniają powtarzalny i skalowalny sposób zarządzania ustawieniami zabezpieczeń Microsoft 365 w wielu dzierżawach klientów. Linie bazowe ułatwiają również monitorowanie podstawowych zasad zabezpieczeń i standardów zgodności dzierżawy za pomocą konfiguracji zabezpieczających użytkowników, urządzenia i dane.

Zaprojektowane po to, aby ułatwić dostawcom usług zarządzanych (MSP) wdrożenie zabezpieczeń u klientów, lighthouse udostępnia standardowy zestaw parametrów podstawowych i wstępnie zdefiniowanych konfiguracji dla Microsoft 365 usług. Te konfiguracje zabezpieczeń ułatwiają mierzenie postępów Microsoft 365 zabezpieczeń i zgodności dzierżawy.

Domyślny plan bazowy i kroki jego wdrożenia możesz wyświetlić z poziomu usługi Lighthouse. Aby zastosować plan bazowy do dzierżawy, wybierz pozycję **Dzierżawy** w lewym okienku nawigacji, a następnie wybierz dzierżawę. Następnie przejdź do karty **Plany wdrażania** i implementuj plan bazowy.

## <a name="default-baseline-security-templates"></a>Domyślne szablony zabezpieczeń planu bazowego

Domyślne konfiguracje bazowe usług Lighthouse dla obciążeń zabezpieczeniami zaprojektowano tak, aby zapewnić, że wszystkie dzierżawy zarządzane są bezpieczne i zgodne.

Konfiguracje bazowe w poniższej tabeli są standardowe z domyślnym planem bazowym aplikacji Lighthouse.<br><br>

| Konfiguracja planu bazowego | Opis |
|--|--|
| Wymaganie uwierzytelniania wieloskładnikowego dla administratorów | Zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego dla wszystkich administratorów. Jest ona wymagana dla wszystkich aplikacji w chmurze. Aby uzyskać więcej informacji o tym planie bazowym, zobacz [Dostęp warunkowy: Wymaganie uwierzytelniania MFA dla wszystkich administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Wymaganie uwierzytelniania wieloskładnikowego dla użytkowników końcowych | Zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego dla wszystkich użytkowników.  Jest ona wymagana dla wszystkich aplikacji w chmurze. Aby uzyskać więcej informacji o tym planie bazowym, zobacz [Dostęp warunkowy: Wymaganie uwierzytelniania MFA dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Blokowanie starszego uwierzytelniania | Zasady dostępu warunkowego do blokowania starszego uwierzytelniania klienta. Aby uzyskać więcej informacji na temat tego planu bazowego, zobacz [Blokowanie starszego uwierzytelniania w usłudze Azure AD z dostępem warunkowym](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Konfigurowanie rejestrowania urządzenia | Rejestracja urządzeń w celu umożliwienia urządzeniu dzierżawcy zarejestrowania się w Microsoft Endpoint Manager. W tym celu należy skonfigurować automatyczne rejestrowanie między Azure Active Directory a Microsoft Endpoint Manager. Aby uzyskać więcej informacji o tym planie bazowym, [zobacz Konfigurowanie rejestracji Windows urządzeniach](/mem/intune/enrollment/windows-enroll). |
| Konfigurowanie Program antywirusowy Microsoft Defender dla Windows 10 i nowszych | Profil konfiguracji urządzenia dla Windows urządzeń ze wstępnie skonfigurowanymi Program antywirusowy Microsoft Defender ustawieniami. Aby uzyskać więcej informacji na temat tego planu bazowego, [zobacz Konfigurowanie programu Microsoft Defender dla punktu końcowego w usłudze Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Konfigurowanie Zapory programu Microsoft Defender do Windows 10 i nowszych | Zasady zapory ułatwiające zabezpieczanie urządzeń przez zapobieganie niechcianym i nieautoryzowanym ruchom sieciowym. Aby uzyskać więcej informacji na temat tego planu bazowego, zobacz Najlepsze rozwiązania dotyczące [konfigurowania Windows Defender sieciowej](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Konfigurowanie zasad zgodności urządzenia dla Windows 10 i nowszych | Zasady Windows urządzenia ze wstępnie skonfigurowanymi ustawieniami w celu spełnienia podstawowych wymagań dotyczących zgodności. Aby uzyskać więcej informacji na temat tego planu bazowego, zobacz [Dostęp warunkowy: wymaganie zgodnego lub hybrydowego urządzenia połączonego z usługą Azure AD](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |


## <a name="related-content"></a>Zawartość pokrewna

[Wdrażanie Microsoft 365 Lighthouse bazowych](m365-lighthouse-deploy-baselines.md) (artykuł)\
[Typowe zasady dostępu warunkowego](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
