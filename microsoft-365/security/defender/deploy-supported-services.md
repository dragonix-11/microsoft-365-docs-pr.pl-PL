---
title: Wdrażanie usług obsługiwanych przez Microsoft 365 Defender
description: Dowiedz się więcej o usługach zabezpieczeń firmy Microsoft, które mogą być zintegrowane przez Microsoft 365 Defender, wymaganiach licencyjnych i procedurach wdrażania
keywords: deploy, licenses, supported services, provisioning, configuration Microsoft 365 Defender, M365, license eligibility, Ochrona punktu końcowego w usłudze Microsoft Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Microsoft Defender for Identity, Microsoft Cloud App Security, MCAS, E5, A5, EMS
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 4ac6186f3ec8ca7d4888a995b2352ec50529e4f1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664903"
---
# <a name="deploy-supported-services"></a>Wdrażanie obsługiwanych usług

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Microsoft 365 Defender](microsoft-365-defender.md) integruje różne usługi zabezpieczeń firmy Microsoft w celu zapewnienia scentralizowanych możliwości wykrywania, zapobiegania i badania przed zaawansowanymi atakami. W tym artykule opisano obsługiwane usługi, ich wymagania licencyjne, zalety i ograniczenia związane z wdrażaniem co najmniej jednej usługi oraz linki do sposobu ich pełnego wdrażania indywidualnie.

## <a name="supported-services"></a>Obsługiwane usługi

Licencja Microsoft 365 E5, E5 Security, A5 lub A5 Security lub ważna kombinacja licencji zapewnia dostęp do następujących obsługiwanych usług i uprawnia do korzystania z Microsoft 365 Defender. [Zobacz wymagania dotyczące licencjonowania](prerequisites.md#licensing-requirements)

| Obsługiwana usługa | Opis |
| ------ | ------ |
| Ochrona punktu końcowego w usłudze Microsoft Defender | Pakiet endpoint protection oparty na zaawansowanych czujnikach behawioralnych, analizie chmury i analizie zagrożeń |
|Ochrona usługi Office 365 w usłudze Microsoft Defender | Zaawansowana ochrona aplikacji i danych w Office 365, w tym poczty e-mail i innych narzędzi do współpracy |
| Microsoft Defender for Identity | Ochrona przed zaawansowanymi zagrożeniami, tożsamościami z naruszonymi zabezpieczeniami i złośliwymi insiderami przy użyciu skorelowanych sygnałów usługi Active Directory |
| Microsoft Defender for Cloud Apps | Identyfikowanie i zwalczanie zagrożeń cybernetycznych w usługach firmy Microsoft i innych firm w chmurze |

## <a name="deployed-services-and-functionality"></a>Wdrożone usługi i funkcje

Microsoft 365 Defender zapewnia lepszą widoczność, korelację i korygowanie podczas wdrażania bardziej obsługiwanych usług.

### <a name="benefits-of-full-deployment"></a>Zalety pełnego wdrożenia

Aby uzyskać pełne korzyści wynikające z Microsoft 365 Defender, zalecamy wdrożenie wszystkich obsługiwanych usług. Poniżej przedstawiono niektóre z kluczowych korzyści z pełnego wdrożenia:

- Zdarzenia są identyfikowane i korelowane na podstawie alertów i sygnałów zdarzeń ze wszystkich dostępnych czujników i funkcji analizy specyficznej dla usługi
- Podręczniki zautomatyzowanego badania i korygowania (AIR) mają zastosowanie do różnych typów jednostek, w tym urządzeń, skrzynek pocztowych i kont użytkowników
- Bardziej kompleksowy, zaawansowany schemat wyszukiwania zagrożeń można wykonywać w poszukiwaniu danych zdarzeń i jednostek z urządzeń, skrzynek pocztowych i innych jednostek

### <a name="limited-deployment-scenarios"></a>Scenariusze wdrażania ograniczonego

Każda obsługiwana usługa, którą wdrażasz, zapewnia bardzo bogaty zestaw nieprzetworzonych sygnałów, a także skorelowane informacje. Chociaż ograniczone wdrożenie nie powoduje wyłączenia funkcji Microsoft 365 Defender, ma to wpływ na możliwość zapewnienia kompleksowego wglądu w punkty końcowe, aplikacje, dane i tożsamości. Jednocześnie wszystkie możliwości korygowania mają zastosowanie tylko do jednostek, które mogą być zarządzane przez wdrożone usługi.

W poniższej tabeli przedstawiono sposób, w jaki każda obsługiwana usługa zapewnia dodatkowe dane, możliwości uzyskania dodatkowych szczegółowych informacji przez skorelowanie danych oraz lepsze możliwości korygowania i reagowania.

| Usługa | Dane (sygnały & skorelowane informacje) | Zakres odpowiedzi & korygowania |
| ------ | ------ | ------ |
| Ochrona punktu końcowego w usłudze Microsoft Defender |<ul><li>Stany punktu końcowego i nieprzetworzone zdarzenia</li><li>Wykrywanie punktów końcowych i alerty, w tym oprogramowanie antywirusowe, EDR, zmniejszanie obszaru ataków</li><li>Informacje o plikach i innych jednostkach obserwowanych w punktach końcowych</li></ul> | Punkty końcowe |
|Ochrona usługi Office 365 w usłudze Microsoft Defender |<ul><li>Stany poczty i skrzynki pocztowej oraz nieprzetworzone zdarzenia</li><li>Wykrywanie wiadomości e-mail, załączników i linków</li></ul> | <ul><li>Skrzynek pocztowych</li><li>konta Microsoft 365</li></ul> |
| Microsoft Defender for Identity |<ul><li>Sygnały usługi Active Directory, w tym zdarzenia uwierzytelniania</li><li>Wykrywanie behawioralne związane z tożsamością</li></ul> | Tożsamości |
| Microsoft Defender for Cloud Apps |<ul><li>Wykrywanie niesankcjonowanych aplikacji i usług w chmurze (w tle IT)</li><li>Narażenie danych na aplikacje w chmurze</li><li>Działanie związane z zagrożeniami skojarzone z aplikacjami w chmurze</li></ul> | Aplikacje w chmurze |

## <a name="deploy-the-services"></a>Wdrażanie usług

Wdrożenie każdej usługi zwykle wymaga aprowizowania w dzierżawie i wstępnej konfiguracji. Zapoznaj się z poniższą tabelą, aby zrozumieć sposób wdrażania każdej z tych usług.

| Usługa | Instrukcje aprowizacji | Konfiguracja początkowa |
| ------ | ------ | ------ |
| Ochrona punktu końcowego w usłudze Microsoft Defender | [przewodnik wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/deployment-phases.md) | *Zobacz instrukcje aprowizacji* |
|Ochrona usługi Office 365 w usłudze Microsoft Defender | *Brak, aprowizowane przy użyciu Office 365* | [Konfigurowanie zasad Ochrona usługi Office 365 w usłudze Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) |
| Microsoft Defender for Identity | [Szybki start: tworzenie wystąpienia Microsoft Defender for Identity](/azure-advanced-threat-protection/install-atp-step1) | *Zobacz instrukcje aprowizacji* |
| Microsoft Defender for Cloud Apps | *Brak* | [Szybki start: Wprowadzenie z Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security) |

Po wdrożeniu obsługiwanych usług [włącz Microsoft 365 Defender](m365d-enable.md).

## <a name="related-topics"></a>Tematy pokrewne

- [omówienie Microsoft 365 Defender](microsoft-365-defender.md)
- [Włączanie usługi Microsoft 365 Defender](m365d-enable.md)
- [omówienie Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md)
- [omówienie Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/defender-for-office-365.md)
- [omówienie Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [omówienie Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)
