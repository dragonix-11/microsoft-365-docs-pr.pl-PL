---
title: Włączanie środowiska oceny dla Microsoft Defender for Cloud Apps
description: Zapoznaj się z architekturą aplikacji Defender dla Chmury w obrębie Ochrona usługi Office 365 w usłudze Microsoft Defender i opis interakcji między produktami Microsoft 365 Defender produktami.
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
ms.openlocfilehash: a66a3563d01e8e4239a0f4815fec9234fd46e1fc
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498984"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Włączanie środowiska oceny dla Microsoft Defender for Cloud Apps

**Dotyczy:**

- Microsoft 365 Defender

Ten artykuł zawiera [krok 2 z 2](eval-defender-mcas-overview.md) w procesie konfigurowania środowiska oceny dla Microsoft Defender for Cloud Apps. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-mcas-overview.md).

Ten artykuł zawiera kroki uzyskiwania dostępu do portalu Defender dla Chmury Apps i konfigurowania integracji niezbędnej do zbierania danych o ruchu aplikacji w chmurze.

Aby odkryć aplikacje w chmurze używane w Twoim środowisku, możesz wdrożyć jedną lub obie z następujących metod:

- Szybko przygotuj się do pracy dzięki odnajdowi w chmurze, integrując się z usługą Ochrona punktu końcowego w usłudze Microsoft Defender. Ta natywna integracja umożliwia natychmiastowe rozpoczęcie zbierania danych dotyczących ruchu w chmurze na Windows 10 i Windows 11 urządzeniach sieciowych oraz poza siecią.
- Aby odkryć wszystkie aplikacje w chmurze dostępne dla wszystkich urządzeń połączonych z Siecią, wdaj dziennik aplikacji usługi Defender dla Chmury na zaporach i innych serwerach proxy. To wdrożenie ułatwia zbieranie danych z punktów końcowych i wysyłanie ich do usługi Defender dla Chmury do analizy. Defender dla Chmury aplikacje natywnie integrują się z niektórymi serwerów proxy innych firm, aby uzyskać jeszcze więcej możliwości.

Ten artykuł zawiera wskazówki dotyczące obu metod.

Aby skonfigurować Microsoft Defender for Cloud Apps, należy wykonać Microsoft Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-eval-enable-steps.png" alt-text="Procedura włączania programu Microsoft Microsoft Defender for Cloud Apps w środowisku oceny usługi Microsoft Defender" lightbox="../../media/defender/m365-defender-mcas-eval-enable-steps.png":::

- [Krok 1. Połączenie do portalu Defender dla Chmury Apps](#step-1)
- [Krok 2. Integracja z Ochrona punktu końcowego w usłudze Microsoft Defender](#step-2)
- [Krok 3. Wdrażanie dziennika Defender dla Chmury aplikacji na zaporach i innych serwerach proxy](#step-3)
- [Krok 4. Wyświetlanie pulpitu nawigacyjnego odnajdowania chmury w celu wyświetlenia informacji o aplikacjach używanych w organizacji](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Krok nr 1. Połączenie do portalu Defender dla Chmury Apps

Aby zweryfikować licencjonowanie i połączyć się z portalem Defender dla Chmury Apps, zobacz Szybki [start: Wprowadzenie pomocą Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security).

Jeśli nie możesz od razu połączyć się z portalem, może być konieczne dodanie adresu IP do listy adresów IP zapory. Zobacz [Konfiguracja podstawowa aplikacji Defender dla Chmury Apps](/cloud-app-security/general-setup).

Jeśli nadal masz problemy, przejrzyj wymagania [dotyczące sieci](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Krok nr 2. Integracja z Ochrona punktu końcowego w usłudze Microsoft Defender

Microsoft Defender for Cloud Apps integruje się z Ochrona punktu końcowego w usłudze Microsoft Defender natywnie. Integracja upraszcza korzystanie z funkcji odnajdowania w chmurze, rozszerza możliwości odnajdowania chmury poza sieć firmową i umożliwia badanie oparte na urządzeniach. Dzięki tej integracji aplikacje i usługi w chmurze są dostępne z systemów zarządzania Windows 10 i Windows 11 urządzeniach.

Jeśli konfiguracja została już Ochrona punktu końcowego w usłudze Microsoft Defender, skonfigurowanie integracji z aplikacją Defender dla Chmury apps to przełącznik w Microsoft 365 Defender. Po włączeniu integracji możesz wrócić do portalu Defender dla Chmury Apps i wyświetlić sformatowane dane na pulpicie nawigacyjnym odnajdowania w chmurze.

Aby wykonać te zadania, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender integracji z programem Microsoft Defender for Cloud Apps](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>Krok nr 3. Wdrażanie dziennika Defender dla Chmury aplikacji na zaporach i innych serwerach proxy

W przypadku zasięgu na wszystkich urządzeniach połączonych z Twoją siecią wdeksuj dziennik aplikacji usługi Defender dla Chmury na zaporach i innych serwerach proxy, aby zbierać dane z punktów końcowych i wysyłać je do usługi Defender dla Chmury Apps do analizy.

Jeśli korzystasz z jednej z następujących bezpiecznych bram sieci Web (SWG, Secure Web Gateways), aplikacje Defender dla Chmury zapewniają bezproblemowe wdrożenie i integrację:

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

Krok 3 z 3: [Przewodnik Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md)

Powrót do omówieniem [funkcji Szacowanie Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
