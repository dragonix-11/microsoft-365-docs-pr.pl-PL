---
title: Krok nr 5. Zarządzanie urządzeniami i aplikacjami dla Microsoft 365 dla dzierżaw przedsiębiorstwa
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Wdróż poprawną opcję zarządzania urządzeniami i aplikacjami dla dzierżaw Microsoft 365.
ms.openlocfilehash: 3999d30aaeee9ebfc2af90b0aeeeaea1b46986fb
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419467"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>Krok nr 5. Zarządzanie urządzeniami i aplikacjami dla Microsoft 365 dla dzierżaw przedsiębiorstwa

Microsoft 365 dla przedsiębiorstw obejmuje funkcje ułatwiające zarządzanie urządzeniami i korzystanie z aplikacji na tych urządzeniach w organizacji za pomocą zarządzania urządzeniami przenośnymi (MDM) i zarządzania aplikacjami mobilnymi (MAM). Możesz zarządzać urządzeniami iOS, Android, macOS i Windows, aby chronić dostęp do zasobów organizacji, w tym danych. Możesz na przykład uniemożliwić wysyłanie wiadomości e-mail do osób spoza organizacji lub odizolować dane organizacji od danych osobowych na urządzeniach osobistych pracownika.

Oto przykład weryfikacji i zarządzania użytkownikami, ich urządzeniami oraz korzystaniem z lokalnych i chmurowych aplikacji zwiększających produktywność, takich jak Microsoft Teams.

![Walidacja użytkowników, urządzeń i aplikacji oraz zarządzanie nimi.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

Aby ułatwić zabezpieczanie i ochronę zasobów organizacji, Microsoft 365 dla przedsiębiorstw obejmuje funkcje ułatwiające zarządzanie urządzeniami i dostępem do aplikacji. Istnieją dwie opcje zarządzania urządzeniami:

- Microsoft Intune, która jest kompleksowym rozwiązaniem do zarządzania urządzeniami i aplikacjami dla przedsiębiorstw.
- Podstawowa mobilność i zabezpieczenia, która jest podzestawem usług Intune dołączonych do wszystkich produktów Microsoft 365 do zarządzania urządzeniami w organizacji. Aby uzyskać więcej informacji, zobacz [Możliwości usługi Basic Mobility and Security](../admin/basic-mobility-security/capabilities.md).

Jeśli masz Microsoft 365 E3 lub E5, należy użyć Intune.

## <a name="microsoft-intune"></a>Microsoft Intune

Używasz [Microsoft Intune](/mem/intune/fundamentals/planning-guide) do zarządzania dostępem do organizacji przy użyciu zarządzania urządzeniami przenośnymi lub zarządzania aplikacjami mobilnymi. Rozwiązanie MDM jest wtedy, gdy użytkownicy "rejestrują" swoje urządzenia w Intune. Po zarejestrowaniu urządzenia jest to urządzenie zarządzane i może odbierać zasady, reguły i ustawienia organizacji. Można na przykład zainstalować określone aplikacje, utworzyć zasady haseł, zainstalować połączenie sieci VPN i nie tylko.

Użytkownicy z własnymi urządzeniami osobistymi mogą nie chcieć rejestrować swoich urządzeń ani zarządzać nimi za pomocą Intune i zasad organizacji. Jednak nadal musisz chronić zasoby i dane organizacji. W tym scenariuszu możesz chronić aplikacje przy użyciu funkcji ZARZĄDZANIA aplikacjami mobilnymi. Na przykład można użyć zasad zarządzania aplikacjami mobilnymi, które wymagają od użytkownika wprowadzenia numeru PIN podczas uzyskiwania dostępu do SharePoint na urządzeniu.

Określisz również sposób zarządzania urządzeniami osobistymi i urządzeniami należącymi do organizacji. W zależności od ich zastosowań warto traktować urządzenia inaczej.

## <a name="identity-and-device-access-configurations"></a>Konfiguracje dostępu do tożsamości i urządzeń

Firma Microsoft udostępnia zestaw konfiguracji dla [tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md) w celu zapewnienia bezpiecznej i produktywnej siły roboczej. Te konfiguracje obejmują korzystanie z następujących elementów:

- zasady dostępu warunkowego Azure AD
- Microsoft Intune zasad zgodności urządzeń i ochrony aplikacji
- zasady ryzyka użytkownika usługi Azure AD Identity Protection
- Dodatkowe zasady aplikacji w chmurze

Oto przykład zastosowania tych ustawień i zasad w celu weryfikowania i ograniczania użytkowników, ich urządzeń oraz korzystania z lokalnych i chmurowych aplikacji zwiększających produktywność, takich jak Microsoft Teams.

![Konfiguracje tożsamości i dostępu do urządzeń dla wymagań i ograniczeń dotyczących użytkowników, ich urządzeń i korzystania z aplikacji.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

Aby uzyskać dostęp do urządzeń i zarządzanie aplikacjami, skorzystaj z konfiguracji w następujących artykułach:

- [Wymagania wstępne](../security/office-365-security/identity-access-prerequisites.md)
- [Wspólne zasady tożsamości i dostępu do urządzeń](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>Wyniki kroku 5

W przypadku zarządzania urządzeniami i aplikacjami dla dzierżawy Microsoft 365 określono ustawienia i zasady Intune w celu weryfikowania i ograniczania użytkowników, ich urządzeń oraz korzystania z lokalnych i chmurowych aplikacji zwiększających produktywność.

Oto przykład dzierżawy z Intune zarządzania urządzeniami i aplikacjami z wyróżnionymi nowymi elementami.

![Przykład dzierżawy z Intune zarządzaniem urządzeniami i aplikacjami.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

Na tej ilustracji dzierżawa ma następujące elementy:

- Urządzenia należące do organizacji zarejestrowane w Intune.
- Intune zasad dotyczących urządzeń i aplikacji dla zarejestrowanych i osobistych urządzeń.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>Bieżąca konserwacja zarządzania urządzeniami i aplikacjami

Na bieżąco może być konieczne: 

- Zarządzanie rejestracją urządzeń.
- Popraw ustawienia i zasady dotyczące dodatkowych aplikacji, urządzeń i wymagań dotyczących zabezpieczeń.
