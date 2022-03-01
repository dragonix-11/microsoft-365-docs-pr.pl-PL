---
title: Włączanie środowiska oceny dla programu Microsoft Defender dla aplikacji w chmurze
description: Poznaj architekturę programu Defender dla aplikacji w chmurze w usłudze Microsoft Defender Office 365 interakcje między produktami Microsoft 365 Defender produktami.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4c8f0ff2ca13d7f1c0e8adfcf4e0bdf09aa1c2ac
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013681"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Włączanie środowiska oceny dla programu Microsoft Defender dla aplikacji w chmurze

**Dotyczy:**

- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 2 z 2](eval-defender-mcas-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender dla aplikacji w chmurze. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-mcas-overview.md).

Ten artykuł zawiera kroki uzyskiwania dostępu do portalu usługi Defender dla aplikacji w chmurze i konfigurowania integracji niezbędnej do zbierania danych o ruchu aplikacji w chmurze.

Aby odkryć aplikacje w chmurze używane w Twoim środowisku, możesz wykonać jedną lub obie z następujących czynności:

- Szybko przygotuj się do pracy dzięki odnajdowi w chmurze przez integrację z usługą Microsoft Defender for Endpoint. Ta natywna integracja umożliwia natychmiastowe rozpoczęcie zbierania danych dotyczących ruchu w chmurze na Windows 10 i Windows 11 urządzeń w sieci i poza siecią.
- Aby odkryć wszystkie aplikacje w chmurze dostępne na wszystkich urządzeniach połączonych z Twoją siecią, wdaj dziennik usługi Defender for Cloud Apps na zapory i innych serwerach proxy. Dane z punktów końcowych są zbierane i wysyłane do usługi Defender for Cloud Apps w celu analizy. Usługa Defender for Cloud Apps natywnie integruje się z niektórymi serwerów proxy innych firm, aby uzyskać jeszcze więcej możliwości.

Ten artykuł zawiera wskazówki dotyczące obu metod.

Aby skonfigurować usługę Microsoft Defender dla aplikacji w chmurze, należy wykonać poniższe czynności.

![Procedura włączania programu Microsoft Defender dla aplikacji w chmurze w środowisku oceny programu Microsoft Defender.](../../media/defender/m365-defender-mcas-eval-enable-steps.png)

- [Krok 1. Połączenie portalu usługi Defender for Cloud Apps](#step-1)
- [Krok 2. Integracja z programem Microsoft Defender for Endpoint](#step-2)
- [Krok 3. Wdrażanie dziennika usługi Defender for Cloud Apps na zapory i innych serwerach proxy](#step-3)
- [Krok 4. Wyświetlanie pulpitu nawigacyjnego odnajdowania chmury w celu wyświetlenia informacji o aplikacjach używanych w organizacji](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Krok nr 1. Połączenie portalu usługi Defender for Cloud Apps

Aby zweryfikować licencjonowanie i połączyć się z portalem aplikacji usługi Defender dla chmury, zobacz Szybki start: wprowadzenie do programu [Microsoft Defender dla aplikacji w chmurze](/cloud-app-security/getting-started-with-cloud-app-security).

Jeśli nie możesz od razu połączyć się z portalem, może być konieczne dodanie adresu IP do listy zezwalań zapory. Zobacz [Podstawowa konfiguracja usługi Defender dla aplikacji w chmurze](/cloud-app-security/general-setup).

Jeśli nadal masz problemy, przejrzyj wymagania [dotyczące sieci](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Krok nr 2. Integracja z programem Microsoft Defender for Endpoint

Program Microsoft Defender for Cloud Apps integruje się z programem Microsoft Defender for Endpoint natywnie. Integracja upraszcza korzystanie z funkcji odnajdowania w chmurze, rozszerza możliwości odnajdowania chmury poza sieć firmową i umożliwia badanie oparte na urządzeniach. Dzięki tej integracji aplikacje i usługi w chmurze są dostępne z systemów zarządzania Windows 10 i Windows 11 urządzeń.

Jeśli program Microsoft Defender dla punktu końcowego został już zainstalowany, skonfigurowanie integracji z usługą Defender dla aplikacji w chmurze jest przełącznikiem w Microsoft 365 Defender. Po włączeniu integracji możesz wrócić do portalu aplikacji usługi Defender dla chmury i wyświetlić sformatowane dane na pulpicie nawigacyjnym odnajdowania w chmurze.

Aby wykonać te zadania, zobacz Integracja programu [Microsoft Defender dla punktu końcowego z programem Microsoft Defender dla aplikacji w chmurze](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>Krok nr 3. Wdrażanie dziennika usługi Defender for Cloud Apps na zapory i innych serwerach proxy

W przypadku zasięgu na wszystkich urządzeniach połączonych z Twoją siecią wdeksuj dziennik usługi Defender for Cloud Apps na swoich zaporach i innych serwerach proxy, aby zbierać dane z punktów końcowych i wysyłać je do usługi Defender for Cloud Apps w celu analizy.

Jeśli korzystasz z jednej z następujących bezpiecznych bram sieci Web (SWG, Secure Web Gateways), usługa Defender dla aplikacji w chmurze zapewnia bezproblemowe wdrażanie i integrację:

- Skala Z
- iboss
- Corrata
- Menlo Security

Aby uzyskać więcej informacji na temat integracji z tymi urządzeniami sieciowym, zobacz [Konfigurowanie odnajdowania w chmurze](/cloud-app-security/set-up-cloud-discovery).

<a name="step-4"></a>

## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>Krok nr 4. Wyświetlanie pulpitu nawigacyjnego odnajdowania chmury w celu wyświetlenia informacji o aplikacjach używanych w organizacji

Pulpit nawigacyjny odnajdowania w chmurze został zaprojektowany tak, aby dać Ci więcej informacji na temat sposobu, w jaki aplikacje w chmurze są używane w Twojej organizacji. Udostępnia on krótkie omówienie typów aplikacji, które są używane, otwartych alertów i poziomów ryzyka aplikacji w organizacji.

Aby rozpocząć korzystanie z pulpitu nawigacyjnego odnajdowania w chmurze, zobacz [Praca z wykrytymi aplikacjami](/cloud-app-security/discovered-apps).

## <a name="next-steps"></a>Następne kroki

Krok 3 z 3: [Pilotaż programu Microsoft Defender dla aplikacji w chmurze](eval-defender-mcas-pilot.md)

Powrót do omówieniem Szacowanie [programu Microsoft Defender dla aplikacji w chmurze](eval-defender-mcas-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
