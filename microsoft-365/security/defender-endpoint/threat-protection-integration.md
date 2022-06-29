---
title: Integrowanie Ochrona punktu końcowego w usłudze Microsoft Defender z innymi rozwiązaniami firmy Microsoft
description: Dowiedz się, jak Ochrona punktu końcowego w usłudze Microsoft Defender integruje się z innymi rozwiązaniami firmy Microsoft, takimi jak Microsoft Defender for Identity i Microsoft Defender for Cloud.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender, dostęp warunkowy, office, Ochrona punktu końcowego w usłudze Microsoft Defender, microsoft defender for identity, microsoft defender for office, Microsoft Defender for Cloud, microsoft cloud app security, azure sentinel
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 24244fa9b0cbb9ed452c8b09b6a108055ac6f770
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489431"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Ochrona punktu końcowego w usłudze Microsoft Defender i inne rozwiązania firmy Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>Integracja z innymi rozwiązaniami firmy Microsoft

Ochrona punktu końcowego w usłudze Microsoft Defender bezpośrednio integruje się z różnymi rozwiązaniami firmy Microsoft.

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender for Cloud

Ochrona punktu końcowego w usłudze Microsoft Defender zapewnia kompleksowe rozwiązanie ochrony serwera, w tym funkcje wykrywania i reagowania na punkty końcowe (EDR) w systemie Windows Server.

### <a name="microsoft-sentinel"></a>Microsoft Sentinel

Łącznik Ochrona punktu końcowego w usłudze Microsoft Defender umożliwia przesyłanie strumieniowe alertów z Ochrona punktu końcowego w usłudze Microsoft Defender do usługi Microsoft Sentinel. Umożliwi to bardziej kompleksowe analizowanie zdarzeń zabezpieczeń w całej organizacji i tworzenie podręczników w celu zapewnienia skutecznej i natychmiastowej reakcji.

### <a name="azure-information-protection"></a>Azure Information Protection

Niedawno wycofaliśmy integrację z usługą Azure Information Protection, ponieważ nasze możliwości DLP punktu końcowego obejmują ulepszone rozwiązanie odnajdywania i ochrony danych poufnych przechowywanych na urządzeniach punktu końcowego, które ułatwia większą widoczność i integrację między rozwiązaniami. Zostało to ogłoszone w następującym [blogu](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555). Zalecamy, aby klienci przechodzili do korzystania z programu Endpoint DLP.

### <a name="conditional-access"></a>Dostęp warunkowy

dynamiczny wynik ryzyka urządzenia Ochrona punktu końcowego w usłudze Microsoft Defender jest zintegrowany z oceną dostępu warunkowego, zapewniając, że tylko bezpieczne urządzenia mają dostęp do zasobów.

### <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps wykorzystuje sygnały Ochrona punktu końcowego w usłudze Microsoft Defender, aby umożliwić bezpośredni wgląd w użycie aplikacji w chmurze, w tym korzystanie z nieobsługiwanych usług w chmurze (w tle IT) ze wszystkich Ochrona punktu końcowego w usłudze Microsoft Defender monitorowanych urządzeń.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

Podejrzane działania to procesy uruchomione w kontekście użytkownika. Integracja między Ochrona punktu końcowego w usłudze Microsoft Defender i Microsoft Defender for Identity zapewnia elastyczność prowadzenia dochodzeń w sprawie bezpieczeństwa cybernetycznego w różnych działaniach i tożsamościach.

### <a name="microsoft-defender-for-office"></a>Microsoft Defender dla pakietu Office

[Ochrona usługi Office 365 w usłudze Defender](/office365/securitycompliance/office-365-atp) pomaga chronić organizację przed złośliwym oprogramowaniem w wiadomościach e-mail lub plikach za pośrednictwem bezpiecznych linków, bezpiecznych załączników, zaawansowanych funkcji analizy przed wyłudzaniem informacji i fałszowania. Integracja między Ochrona usługi Office 365 w usłudze Microsoft Defender i Ochrona punktu końcowego w usłudze Microsoft Defender umożliwia analitykom zabezpieczeń przejście w górę w celu zbadania punktu wejścia ataku. Dzięki udostępnianiu analizy zagrożeń ataki mogą być blokowane i blokowane.

> [!NOTE]
> Ochrona usługi Office 365 w usłudze Defender dane są wyświetlane dla zdarzeń w ciągu ostatnich 30 dni. W przypadku alertów dane Ochrona usługi Office 365 w usłudze Defender są wyświetlane na podstawie pierwszego czasu działania. Następnie dane nie są już dostępne w Ochrona usługi Office 365 w usłudze Defender.

### <a name="skype-for-business"></a>Skype dla firm

Integracja Skype dla firm umożliwia analitykom komunikowanie się z potencjalnie naruszonym użytkownikiem lub właścicielem urządzenia za pomocą prostego przycisku z portalu.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender

Dzięki Microsoft 365 Defender, Ochrona punktu końcowego w usłudze Microsoft Defender i różnym rozwiązaniom zabezpieczeń firmy Microsoft tworzymy ujednolicony pakiet ochrony przedsiębiorstwa przed i po naruszeniu zabezpieczeń, który natywnie integruje się między punktami końcowymi, tożsamościami, pocztą e-mail i aplikacjami w celu wykrywania, zapobiegania, badania i automatycznego reagowania do zaawansowanych ataków.

[Dowiedz się więcej o Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

## <a name="related-topics"></a>Tematy pokrewne

- [Konfigurowanie integracji i innych zaawansowanych funkcji](advanced-features.md)
- [omówienie Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)
- [Włączanie usługi Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable)
- [Ochrona użytkowników, danych i urządzeń przy użyciu dostępu warunkowego](conditional-access.md)
