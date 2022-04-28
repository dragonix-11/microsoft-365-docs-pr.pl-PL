---
title: Plan dzierżawy dla Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Plan konfigurowania dzierżaw dla Microsoft 365.
ms.openlocfilehash: 85695c38f724f215192d7659963c35f25b006dc5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092056"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Plan dzierżawy dla Microsoft 365

Dzierżawa Microsoft 365 to zestaw usług przypisanych do organizacji. Zazwyczaj ta dzierżawa jest skojarzona z co najmniej jedną publiczną nazwą domeny DNS i działa jako centralny i izolowany kontener dla różnych subskrypcji i licencji w nich przypisywanych do kont użytkowników. Aby uzyskać więcej informacji [, zobacz Subskrypcje, licencje, konta i dzierżawy dla ofert firmy Microsoft w chmurze](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Podczas tworzenia dzierżawy Microsoft 365 należy przypisać ją do określonej lokalizacji geograficznej. Możesz również mieć dzierżawę z wieloma lokalizacjami geograficznymi i przenieść dzierżawę z jednej lokalizacji do innej.

Aby przygotować dzierżawę na potrzeby użytkowników, grup, licencji i aplikacji w chmurze, ważne jest dokładne zaplanowanie i wykonanie konfiguracji dzierżawy.

## <a name="set-up-your-microsoft-365-tenant"></a>Konfigurowanie dzierżawy Microsoft 365

Po upewnieniu się, że sieć jest zoptymalizowana pod kątem dostępu do Microsoft 365 dla pracowników lokalnych i zdalnych, kolejne duże zadania są planowane, a następnie konfigurowanie dzierżawy Microsoft 365 nazw domen DNS, usług wspólnych i dla tej infrastruktury tożsamości, która obsługuje bezpieczne logowanie użytkowników.

### <a name="plan"></a>Plan

Aby zaplanować implementację dzierżawy:

- [Informacje o subskrypcjach, licencjach i dzierżawach Azure Active Directory (Azure AD)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Dowiedz się, jak używać certyfikatów SSL innych firm](plan-for-third-party-ssl-certificates.md)
- [Omówienie sposobu integracji dzierżawy Microsoft 365 z usługami Azure AD](integrated-apps-and-azure-ads.md)
- [Planowanie obsługi aplikacji klienckich](microsoft-365-client-support-certificate-based-authentication.md)
- [Określanie sposobu używania nowoczesnego uwierzytelniania hybrydowego](hybrid-modern-auth-overview.md)
- [Planowanie uaktualnień Office 2007 i Office 2010](plan-upgrade-previous-versions-office.md)
- [Omówienie izolacji dzierżawy](/compliance/assurance/microsoft-365-isolation-controls)

### <a name="deploy"></a>Wdrażanie

Aby wdrożyć dzierżawę: 

- Dodaj [domeny DNS](../admin/setup/add-domain.md) dla swojej organizacji.
- Użyj [przewodników konfiguracji w Centrum administracyjne platformy Microsoft 365](setup-guides-for-microsoft-365.md).
- Tworzenie [infrastruktury tożsamości](deploy-identity-solution-overview.md).

### <a name="move-a-tenants-geographic-locations"></a>Przenoszenie lokalizacji geograficznych dzierżawy

Firma Microsoft kontynuuje otwieranie nowych lokalizacji geograficznych centrum danych (obszarów geograficznych) dla usług Microsoft 365. Te nowe lokalizacje geograficzne centrum danych dodają pojemność i zasoby obliczeniowe w celu obsługi wzrostu zapotrzebowania klientów i użycia. Ponadto nowe lokalizacje geograficzne centrum danych oferują miejsce przechowywania danych w obszarze geograficznym dla podstawowych danych klientów.

Aby uzyskać więcej informacji, zobacz [Przenoszenie danych podstawowych do nowych obszarów geograficznych Microsoft 365 centrum danych](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>Wdrażanie Microsoft 365 wielu obszarach geograficznych

Dzięki Microsoft 365 Multi-Geo twoja organizacja może rozszerzyć swoją obecność Microsoft 365 do wielu regionów geograficznych i/lub krajów w ramach istniejącej dzierżawy.

Aby uzyskać więcej informacji, zobacz [Microsoft 365 Multi-Geo](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Zarządzanie wieloma dzierżawami Microsoft 365 

Mimo że posiadanie jednej dzierżawy dla twojej oganizacji jest idealne, może być jedną z wielu organizacji, które mają wiele dzierżaw. Przyczyny mogą obejmować fuzje i przejęcia, izolację administracyjną lub zdecentralizowaną it.

Jeśli masz wiele dzierżaw Microsoft 365, zobacz następujące artykuły, aby uzyskać więcej informacji na temat:

- [Współpraca między dzierżawami](microsoft-365-inter-tenant-collaboration.md)
- [Migracja skrzynki pocztowej między dzierżawami](cross-tenant-mailbox-migration.md)
- [Migracje z dzierżawy do dzierżawy](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Następny krok

Rozpocznij planowanie [dzierżawy od subskrypcji, licencji, kont i dzierżaw](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).