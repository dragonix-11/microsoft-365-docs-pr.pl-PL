---
title: Integracja programu Microsoft Defender for Endpoint z innymi rozwiązaniami firmy Microsoft
description: Dowiedz się, jak program Microsoft Defender for Endpoint integruje się z innymi rozwiązaniami firmy Microsoft, w tym z programem Microsoft Defender for Identity i Microsoft Defender for Cloud.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender, dostęp warunkowy, office, Microsoft Defender for Endpoint, microsoft defender for identity, microsoft defender for office, Azure Defender, microsoft cloud app security, azure sentinel
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4f220b16b0402215aa1fad0681edf241b61062ed
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009816"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Program Microsoft Defender dla punktu końcowego i innych rozwiązań firmy Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>Integracja z innymi rozwiązaniami firmy Microsoft

Program Microsoft Defender for Endpoint jest bezpośrednio zintegrowany z różnymi rozwiązaniami firmy Microsoft.

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender dla chmury

Program Microsoft Defender for Endpoint udostępnia kompleksowe rozwiązanie do ochrony serwera, w tym funkcje wykrywanie i reagowanie w punktach końcowych (EDR) na Windows serwerach.

### <a name="microsoft-sentinel"></a>Microsoft Sentinel

Łącznik programu Microsoft Defender dla punktu końcowego umożliwia przesyłanie strumieniowe alertów z programu Microsoft Defender for Endpoint do programu Microsoft Sentinel. Umożliwi to bardziej kompleksowe analizowanie zdarzeń zabezpieczeń w organizacji i tworzenie podręczników w celu efektywnej i natychmiastowej odpowiedzi.

### <a name="azure-information-protection"></a>Azure Information Protection

Ostatnio funkcje integracji usługi Azure Information Protection zostały wycofane, ponieważ funkcje ochrony przed m.in. punktu końcowego zawierają ulepszone rozwiązanie odnajdowania i ochrony dla poufnych danych przechowywanych na urządzeniach punktów końcowych, które ułatwia lepszą widoczność i integrację między rozwiązaniami. Zostało to ogłoszone w poniższym [blogu](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555). Zalecamy, aby klienci przechodzili do korzystania z funkcji DLP punktu końcowego.

### <a name="conditional-access"></a>Dostęp warunkowy

Dynamiczny wynik ryzyka dla programu Microsoft Defender for Endpoint jest zintegrowany z oceną dostępu warunkowego, dzięki czemu można zagwarantować, że tylko bezpieczne urządzenia mają dostęp do zasobów.

### <a name="microsoft-defender-for-cloud-apps"></a>Usługa Microsoft Defender dla aplikacji w chmurze

Program Microsoft Defender for Cloud Apps wykorzystuje program Microsoft Defender jako sygnały punktu końcowego, aby umożliwić bezpośrednią widoczność użycia aplikacji w chmurze, w tym korzystanie z nieobsługiwanych usług w chmurze (w tle IT) ze wszystkich urządzeń monitorowanych przez program Microsoft Defender for Endpoint.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

Podejrzane działania to procesy uruchomione w kontekście użytkownika. Integracja między programem Microsoft Defender for Endpoint a usługą Microsoft Defender for Identity zapewnia elastyczność w zakresie przeprowadzania badań zabezpieczeń cyberprzestępczych w działaniach i tożsamościach.

### <a name="microsoft-defender-for-office"></a>Program Microsoft Defender dla Office

[Program Defender for Office 365](/office365/securitycompliance/office-365-atp) pomaga chronić twoją organizację przed złośliwym oprogramowaniem w wiadomościach e-mail lub plikach za pomocą linków programu Sejf, załączników Sejf, zaawansowanych funkcji ochrony przed wyłudzaniem informacji i fałszowania informacji. Integracja między programem Microsoft Defender for Office 365 a programem Microsoft Defender for Endpoint umożliwia analitykom zabezpieczeń strumieniowe sprawdzenie punktu wejścia do ataków. Dzięki udostępnianiu analizy zagrożeń ataki mogą być zawarte i blokowane.

> [!NOTE]
> Defender for Office 365 data is displayed for events within the last 30 days. W przypadku alertów defender Office 365 dane są wyświetlane na podstawie czasu pierwszej aktywności. Po upływie tego czasu dane nie będą już dostępne w programie Defender dla Office 365.

### <a name="skype-for-business"></a>Skype dla firm

Integracja Skype dla firm umożliwia analitykom komunikowanie się z potencjalnie naruszonym użytkownikiem lub właścicielem urządzenia za pomocą prostego przycisku z portalu.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender

Program Microsoft 365 Defender, program Microsoft Defender for Endpoint i różne rozwiązania zabezpieczeń firmy Microsoft tworzą ujednolicony pakiet ochrony przedsiębiorstwa przed naruszeniem i po nim, który natywnie integruje się we wszystkich punktach końcowych, tożsamości, wiadomościach e-mail i aplikacjach w celu wykrywania, zapobiegania, zbadania i automatycznego reagowania na zaawansowane ataki i automatycznego reagowania na nie.

[Dowiedz się więcej o Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

## <a name="related-topics"></a>Tematy pokrewne

- [Konfigurowanie integracji i innych funkcji zaawansowanych](advanced-features.md)
- [Microsoft 365 Defender omówienie](/microsoft-365/security/defender/microsoft-365-defender)
- [Włączanie Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable)
- [Ochrona użytkowników, danych i urządzeń za pomocą dostępu warunkowego](conditional-access.md)
