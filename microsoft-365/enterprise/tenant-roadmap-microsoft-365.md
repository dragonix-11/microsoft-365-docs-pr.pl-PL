---
title: Przewodnik po dzierżawie usługi Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Przewodnik po skonfigurowaniu dzierżaw dla Microsoft 365.
ms.openlocfilehash: 180f7f998819986d05febe6ae19877da290d20a5
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015949"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Przewodnik po dzierżawie usługi Microsoft 365

Dzierżawa Microsoft 365 to zestaw usług przypisanych do Twojej organizacji. Zazwyczaj ta dzierżawa jest skojarzona z co najmniej jedną z nazw domen publicznych DNS i działa jako centralny i odizolowany kontener dla różnych subskrypcji i licencji w ramach nich, które przypisujesz do kont użytkowników. Aby uzyskać więcej informacji, [zobacz Subskrypcje, licencje, konta i dzierżawy](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md) usług chmurowych firmy Microsoft.

Tworząc dzierżawę usługi Microsoft 365, przypisujesz ją do konkretnej lokalizacji geograficznej. Możesz również utworzyć dzierżawę z wieloma lokalizacjami geograficznymi i przenieść dzierżawę z jednej lokalizacji do innej.

Aby przygotować dzierżawę na użytkowników, grupy, licencje i aplikacje w chmurze, należy starannie zaplanować i wykonać konfigurację dzierżawy.

## <a name="set-up-your-microsoft-365-tenant"></a>Konfigurowanie dzierżawy Microsoft 365 dzierżawy

Po upewnieniu się, że sieć jest zoptymalizowana pod kątem dostępu do usługi Microsoft 365 zarówno dla pracowników lokalnych, jak i pracowników zdalnych, następne duże zadania planujesz, a następnie konfigurujesz dzierżawę usługi Microsoft 365 pod kątem nazw domen DNS, typowych usług i tej infrastruktury tożsamości obsługującej bezpieczne logowanie użytkowników.

### <a name="plan"></a>Planowanie

Aby zaplanować implementację dzierżawy:

- [Opis subskrypcji, licencji i dzierżaw Azure Active Directory (Azure AD)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Opis sposobu używania certyfikatów SSL innych firm](plan-for-third-party-ssl-certificates.md)
- [Opis sposobów integracji dzierżawy usługi Microsoft 365 z usługami Azure AD](integrated-apps-and-azure-ads.md)
- [Planowanie obsługi aplikacji klienckiej](microsoft-365-client-support-certificate-based-authentication.md)
- [Określanie sposobu używania nowoczesnego uwierzytelniania hybrydowego](hybrid-modern-auth-overview.md)
- [Planowanie uaktualnienia Office 2007 Office 2010](plan-upgrade-previous-versions-office.md)
- [Opis izolacji dzierżawy](/compliance/assurance/microsoft-365-isolation-controls)

### <a name="deploy"></a>Wdrażanie

Aby wdrożyć dzierżawę: 

- Dodaj domeny [DNS](../admin/setup/add-domain.md) dla swojej organizacji.
- Skorzystaj z [przewodników konfiguracji w centrum administracyjne platformy Microsoft 365](setup-guides-for-microsoft-365.md).
- Stwórz swoją [infrastrukturę tożsamości](deploy-identity-solution-overview.md).

### <a name="move-a-tenants-geographic-locations"></a>Przenoszenie lokalizacji geograficznych dzierżawy

Firma Microsoft nadal otwiera nowe lokalizacje geograficzne (lokalizacje geograficzne) centrum danych dla Microsoft 365 danych. Te nowe lokalizacje geograficzne centrum danych dodają wydajność i zasoby obliczeniowe, aby obsługiwać zapotrzebowanie klientów i wzrost użycia. Ponadto nowe lokalizacje geolokalizacji centrum danych oferują lokalizację przechowywania danych w lokalizacji geograficznej na podstawowe dane klientów.

Aby uzyskać więcej informacji, zobacz [Przenoszenie podstawowych danych do nowych Microsoft 365 lokalizacji geograficznych centrum danych](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>Wdrażanie Microsoft 365 wielu lokalizacji geograficznych

Dzięki Microsoft 365 wielolokalizacji organizacja może rozszerzyć swoją obecność Microsoft 365 o wiele regionów geograficznych i/lub krajów w ramach istniejącej dzierżawy.

Aby uzyskać więcej informacji, zobacz [Microsoft 365 Multi-Geo](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Zarządzanie wieloma Microsoft 365 dzierżawami 

Mimo że posiadanie jednej dzierżawy dla Twojej organizacji to idealne rozwiązanie, być może należysz do wielu organizacji mających wiele dzierżaw. Przyczyny mogą obejmować fuzje i pozyskiwanie, potrzebujesz izolacji administracyjnej lub masz zdecentralizowany system IT.

Jeśli masz wiele Microsoft 365 dzierżaw, zapoznaj się z tymi artykułami, aby uzyskać więcej informacji o:

- [Współpraca w ramach dzierżawy](microsoft-365-inter-tenant-collaboration.md)
- [Migracja skrzynek pocztowych między dzierżawami](cross-tenant-mailbox-migration.md)
- [Migracje z dzierżawy do dzierżawy](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Następny krok

Rozpocznij planowanie dzierżawy za [pomocą subskrypcji, licencji, kont i dzierżaw](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).