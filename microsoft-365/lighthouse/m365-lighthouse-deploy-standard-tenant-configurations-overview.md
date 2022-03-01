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
ms.openlocfilehash: 23ebc0d0562cf06bd92456e18c0833a61c564673
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63013758"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu planu bazowego 

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i są dostępne tylko dla partnerów spełniających [te wymagania](m365-lighthouse-requirements.md). Jeśli Twoja organizacja nie ma konta Microsoft 365 Lighthouse, zobacz Logowanie [się w celu Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse bazowe zapewniają powtarzalny i skalowalny sposób oceny ustawień zabezpieczeń Microsoft 365 zarządzania nimi w wielu dzierżawach klientów. Linie bazowe ułatwiają również monitorowanie podstawowych zasad zabezpieczeń i standardów zgodności dzierżawy za pomocą konfiguracji zabezpieczających użytkowników, urządzenia i dane.

Zaprojektowane po to, aby ułatwić partnerom we własnym tempie wdrożenie bezpieczeństwa przez klientów, lighthouse oferuje standardowy zestaw parametrów bazowych i wstępnie zdefiniowanych konfiguracji dla Microsoft 365 usług. Te konfiguracje zabezpieczeń ułatwiają mierzenie postępów Microsoft 365 zabezpieczeń i zgodności dzierżawy.

Domyślny plan bazowy i kroki jego wdrożenia możesz wyświetlić z poziomu usługi Lighthouse. Aby zastosować linie bazowe do dzierżawy, wybierz pozycję **Dzierżawy** w lewym okienku nawigacji, a następnie wybierz dzierżawę. Następnie przejdź do karty **Plany wdrażania** i zaimplementowanie odpowiedniego planu bazowego.

## <a name="standard-baseline-security-templates"></a>Standardowe szablony zabezpieczeń planu bazowego

Standardowe konfiguracje bazowe usługi Lighthouse dla obciążeń pracą zabezpieczeń zaprojektowano tak, aby ułatwić wszystkim dzierżawom zarządzanym osiągnięcie akceptowalnego stanu ochrony i zgodności.

Konfiguracje bazowe w poniższej tabeli są standardowe z domyślnym planem bazowym aplikacji Lighthouse.<br><br>

| Konfiguracja planu bazowego | Opis |
|--|--|
| Wymaganie uwierzytelniania wieloskładnikowego dla administratorów | Zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego dla administratorów. Jest ona wymagana dla wszystkich aplikacji w chmurze. |
| Wymaganie uwierzytelniania wieloskładnikowego dla użytkowników końcowych | Zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego dla użytkowników. Jest ona wymagana dla wszystkich aplikacji w chmurze. |
| Blokowanie starszego uwierzytelniania | Zasady dostępu warunkowego do blokowania starszego uwierzytelniania klienta. |
| Konfigurowanie rejestrowania urządzenia | Rejestracja urządzeń w celu umożliwienia urządzeniu dzierżawcy zarejestrowania się w Microsoft Endpoint Manager. W tym celu należy skonfigurować automatyczne rejestrowanie między Azure Active Directory a Microsoft Endpoint Manager. |
| Konfigurowanie Program antywirusowy Microsoft Defender dla Windows 10 i nowszych | Profil konfiguracji urządzenia dla Windows urządzeń ze wstępnie skonfigurowanymi Program antywirusowy Microsoft Defender ustawieniami. |
| Konfigurowanie zasad zgodności urządzenia dla Windows 10 i nowszych | Zasady Windows urządzenia ze wstępnie skonfigurowanymi ustawieniami w celu spełnienia podstawowych wymagań dotyczących zgodności. |

## <a name="related-content"></a>Zawartość pokrewna

[Wdrażanie Microsoft 365 Lighthouse bazowych](m365-lighthouse-deploy-baselines.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
