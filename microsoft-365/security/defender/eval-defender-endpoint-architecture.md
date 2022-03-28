---
title: Przegląd wymagań architektury programu Microsoft Defender dla punktów końcowych i kluczowych pojęć
description: Diagram techniczny programu Microsoft Defender for Endpoint w programie Microsoft 365 Defender pomaga zrozumieć tożsamość w programie Microsoft 365 przed rozpoczęciem tworzenia laboratorium próbnego lub środowiska pilotażowego.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: b1381e7c2be2224818c72fb8e269ad65ffcacfc8
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755023"
---
# <a name="review-microsoft-defender-for-endpoint-architecture-requirements-and-key-concepts"></a>Przegląd wymagań architektury programu Microsoft Defender dla punktów końcowych i kluczowych pojęć

**Dotyczy:** Microsoft 365 Defender

Ten artykuł zawiera  przewodnik po procesie konfigurowania oceny środowiska programu Microsoft Defender dla punktu końcowego.

Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-endpoint-overview.md).

Przed włączeniem programu Microsoft Defender for Endpoint upewnij się, że rozumiesz architekturę i może spełniać wymagania.

## <a name="understand-the-architecture"></a>Opis architektury

Poniższy diagram przedstawia architekturę i integracje programu Microsoft Defender for Endpoint. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-architecture.png" alt-text="Procedura dodawania programu Microsoft Defender dla Office do środowiska oceny usługi Defender" lightbox="../../media/defender/m365-defender-endpoint-architecture.png":::

W poniższej tabeli opisano ilustrację.

Call-out | Opis
:---|:---|
1 | Urządzenia są na pokładzie jednego z obsługiwanych narzędzi do zarządzania. 
2 | Urządzenia podłączone do sieci bezprzewodowej zapewniają dane sygnału punktu końcowego programu Microsoft Defender i reagują na nie.
3 | Urządzenia zarządzane są dołączane i/lub zarejestrowane w Azure Active Directory.
4 | Urządzenia przyłączone do Windows domen są synchronizowane Azure Active Directory przy użyciu Azure Active Directory Połączenie.
5 | Alerty, badania i odpowiedzi usługi Microsoft Defender for Endpoint są zarządzane w Microsoft 365 Defender.

## <a name="understand-key-concepts"></a>Opis kluczowych pojęć

W poniższej tabeli przedstawiono kluczowe pojęcia, które należy zrozumieć podczas oceniania, konfigurowania i wdrażania programu Microsoft Defender dla punktu końcowego: 

Pojęcie | Opis | Więcej informacji
:---|:---|:---|
Portal administracyjny | Microsoft 365 Defender w celu monitorowania i pomagania w reagowaniu na alerty o potencjalnych zaawansowanych trwałych działaniach zagrożeń lub naruszeniach danych. | [Omówienie portalu programu Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/portal-overview)
Zmniejszenie powierzchni ataków | Pomaga zmniejszyć liczbę miejsc ataków, minimalizując miejsca, w których Twoja organizacja jest podatna na cyberataki i ataki. | [Omówienie zmniejszania powierzchni ataków](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction)
Wykrywanie punktu końcowego i odpowiedź | Funkcje wykrywania punktu końcowego i odpowiedzi zapewniają zaawansowane wykrywanie ataków w czasie rzeczywistym, które mogą być wykrywane w czasie rzeczywistym. | [Omówienie wykrywanie i reagowanie w punktach końcowych funkcji](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
Blokowanie i blokowanie zachowania | Możliwości blokowania i blokowania zachowań mogą ułatwić identyfikowanie i zatrzymywanie zagrożeń na podstawie ich zachowań i drzew procesowych, nawet gdy zagrożenie rozpoczęło się. | [Blokowanie i ograniczanie behawioralne](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment)
Zautomatyzowane badanie i odpowiedź | W automatycznym śledztwie są używane różne algorytmy inspekcji na podstawie procesów, które są używane przez analityków zabezpieczeń i przeznaczone do analizy alertów i natychmiastowego podjęcia działań w celu rozwiązania naruszeń. | [Używanie zautomatyzowanych analiz w celu zbadania i rozwiązania problemów związanych z zagrożeniami](/microsoft-365/security/defender-endpoint/automated-investigations)
Zaawansowane łowiectwo | Zaawansowane szukanie to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które pozwala eksplorować nawet 30 dni pierwotne dane, dzięki czemu możesz aktywnie sprawdzać zdarzenia w swojej sieci w celu znalezienia wskaźników zagrożeń i jednostek. | [Omówienie wyszukiwania zaawansowanego](/microsoft-365/security/defender-endpoint/advanced-hunting-overview)
Analiza zagrożeń | Analiza zagrożeń to zestaw raportów ekspertów firmy Microsoft ds. zabezpieczeń dotyczących najbardziej istotnych zagrożeń. | [Śledzenie pojawiających się zagrożeń i reagowanie na nie](/microsoft-365/security/defender-endpoint/threat-analytics)


Aby uzyskać bardziej szczegółowe informacje o możliwościach programu Microsoft Defender dla punktu końcowego, zobacz Co [to jest program Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="siem-integration"></a>Integracja zarządzania informacjami i zdarzeniami zabezpieczeń

Możesz zintegrować usługę Microsoft Defender for Endpoint z programem Microsoft Sentinel, aby bardziej wyczerpująco analizować zdarzenia dotyczące zabezpieczeń w całej organizacji i tworzyć podręczniki w celu efektywnej i natychmiastowej odpowiedzi. 

Program Microsoft Defender for Endpoint może być również zintegrowany z innymi rozwiązaniami do zarządzania informacjami o zabezpieczeniach i zdarzeniami. Aby uzyskać więcej informacji, [zobacz Włączanie integracji SIEM w programie Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/enable-siem-integration).


## <a name="next-steps"></a>Następne kroki
[Włączanie oceny](eval-defender-endpoint-enable-eval.md)

Powrót do omówieniem [Szacowanie programu Microsoft Defender dla punktu końcowego](eval-defender-endpoint-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
