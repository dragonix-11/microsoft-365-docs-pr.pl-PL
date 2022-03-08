---
title: Krok nr 4. Wdrażanie zarządzania punktami końcowymi dla urządzeń, komputerów i innych punktów końcowych
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Zarządzaj Microsoft Endpoint Manager, komputerami i innymi punktami końcowymi, zarządzaj nimi.
ms.openlocfilehash: d18a001021486c617aaf0fa04972e9464a5c2016
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328627"
---
# <a name="step-4-deploy-endpoint-management-for-your-devices-pcs-and-other-endpoints"></a>Krok nr 4. Wdrażanie zarządzania punktami końcowymi dla urządzeń, komputerów i innych punktów końcowych

Pracownicy hybrydowi muszą obsługiwać coraz więcej urządzeń osobistych. Zarządzanie punktami końcowymi to oparte na zasadach podejście do zabezpieczeń, które wymaga, aby urządzenia przestrzegały określonych kryteriów, zanim uzyskają dostęp do zasobów. Microsoft Endpoint Manager zapewnia nowoczesne funkcje zarządzania, które zapewniają bezpieczeństwo danych w chmurze i lokalnie. 

[Microsoft Endpoint Manager](/mem/endpoint-manager-overview) udostępnia usługi i narzędzia do zarządzania urządzeniami przenośnymi, komputerami stacjonarnymi, maszynami wirtualnymi, urządzeniami osadzonymi i serwerami przez połączenie następujących usług, które być może znasz i z których już korzystasz.

:::image type="content" source="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png" alt-text="Składniki zarządzania punktami końcowymi dla Microsoft 365" lightbox="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png":::

## <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune to usługa oparta na chmurze, która skupia się na zarządzaniu urządzeniami przenośnymi (MDM) i zarządzaniu aplikacjami mobilnymi dołączonymi do programu Microsoft 365. 

- **MDM:** W przypadku urządzeń należących do organizacji możesz mieć pełną kontrolę nad ustawieniami, funkcjami i zabezpieczeniami. Urządzenia są "zarejestrowane" w usłudze Intune, gdzie otrzymują zasady usługi Intune z regułami i ustawieniami. Możesz na przykład ustawić wymagania dotyczące haseł i numeru PIN, utworzyć połączenie VPN, skonfigurować ochronę przed zagrożeniami i nie tylko.

- **MAM:** Pracownicy zdalni mogą nie chcieć, aby Twoi pracownicy mieli pełną kontrolę nad ich urządzeniami osobistymi, nazywanymi także urządzeniami bring-your-own device (BYOD). Możesz zapewnić pracownikom hybrydowym opcje i nadal chronić swoją organizację. Na przykład pracownicy hybrydowi mogą zarejestrować swoje urządzenia, jeśli chcą mieć pełny dostęp do zasobów organizacji. Jeśli ci użytkownicy chcą mieć dostęp tylko do poczty e-mail Microsoft Teams poczty e-mail, skorzystaj z zasad ochrony aplikacji, które wymagają uwierzytelniania wieloskładnikowego (MFA), aby korzystać z tych aplikacji.

Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami za pomocą rozwiązania Intune Foundation](manage-devices-with-intune-overview.md) .

## <a name="configuration-manager"></a>Menedżer konfiguracji

Menedżer konfiguracji to lokalne rozwiązanie do zarządzania komputerami stacjonarnymi, serwerami i komputerami przenośnymi w sieci lub Internecie. Wdrażaj Menedżer konfiguracji, aktualizacje oprogramowania i systemy operacyjne za pomocą aplikacji. Możesz również monitorować zgodność z przepisami, zapytania i działać na klientach w czasie rzeczywistym i nie tylko. Można ją włączyć w chmurze do integracji z usługami Intune, Azure AD, Microsoft Defender for Endpoint i innymi usługami w chmurze. 

Aby uzyskać więcej informacji, zobacz [to omówienie Menedżer konfiguracji](/mem/configmgr/core/understand/introduction).

## <a name="co-management"></a>Współzawłasnie

Funkcja współzawłasniania łączy istniejące lokalne inwestycje Menedżer konfiguracji z chmurą przy użyciu usługi Intune i innych usług Microsoft 365 w chmurze. Możesz określić Menedżer konfiguracji czy usługa Intune jest organem zarządzającym różnymi obciążeniami pracą. 

W funkcji współzawłasniania używane są funkcje chmury oparte na usłudze Intune, w tym dostęp warunkowy i wymuszanie zgodności urządzenia. Niektóre zadania należy przechowywać lokalnie, jednocześnie uruchamiając inne zadania w chmurze.

Aby uzyskać więcej informacji, zobacz [omówienie funkcji współzawłasniania](/mem/configmgr/comanage/overview).

## <a name="endpoint-analytics"></a>Analiza punktu końcowego

Analiza punktów końcowych ma na celu zwiększenie produktywności użytkowników i zmniejszenie kosztów pomocy technicznej IT dzięki umożliwieniu wglądu w środowisko użytkownika. Szczegółowe informacje umożliwiają działowi IT zoptymalizowanie środowiska użytkownika końcowego dzięki proaktywnej obsłudze oraz wykrywanie regresji do środowiska użytkownika przez ocenę wpływu zmian konfiguracji na użytkowników.

Aby uzyskać więcej informacji, zobacz omówienie [analizy punktu końcowego](/mem/analytics/overview)

## <a name="windows-autopilot"></a>Windows Autopilot

Windows Rozwiązania Autopilot to samoobsługowa platforma do Windows zerowej obsługi. Obejmuje on kolekcję technologii, za pomocą których konfigurujesz i wstępnie konfigurujesz nowe urządzenia, aby przygotować je do użycia w produktywnej pracy. Możesz również zresetować, Windows, ponownie wykorzystać i odzyskać urządzenia za pomocą rozwiązania Autopilot. 

Windows rozwiązania Autopilot umożliwia działowi IT wstępne skonfigurowanie urządzeń bez małej infrastruktury do zarządzania, przy użyciu łatwego i prostego procesu. 

- Z perspektywy użytkownika wystarczy wykonać tylko kilka prostych operacji, aby urządzenie było gotowe do użycia. 
- Z perspektywy profesjonalistów IT jedyną interakcją wymaganą przez użytkownika końcowego jest połączenie się z siecią i zweryfikowanie poświadczeń.

Aby uzyskać więcej informacji, zobacz to [omówienie rozwiązania Windows Autopilot](/windows/deployment/windows-autopilot/windows-autopilot).

## <a name="admin-technical-resources-for-endpoint-management"></a>Zasoby techniczne dla administratorów do zarządzania punktami końcowymi

- [Przewodnik po zarządzaniu urządzeniami dla Microsoft 365](../enterprise/device-management-roadmap-microsoft-365.md)
- [Jak zarejestrować różne typy urządzeń do zarządzania urządzeniami przenośnymi](/mem/intune/enrollment/device-enrollment)
- [Informacje dla użytkowników końcowych dotyczące Microsoft Intune](/mem/intune/fundamentals/end-user-educate)
 
## <a name="results-of-step-4"></a>Wyniki kroku 4

Używasz pakietu funkcji i możliwości pakietu Endpoint Manager do zarządzania urządzeniami przenośnymi, komputerami stacjonarnymi, maszynami wirtualnymi, urządzeniami osadzonymi i serwerami.

## <a name="next-step"></a>Następny krok

[![Krok 5. Wdrażanie aplikacji i usług zwiększających produktywność dla pracowników zdalnych.](../media/empower-people-to-work-remotely/remote-workers-step-grid-5.png)](empower-people-to-work-remotely-teams-productivity-apps.md)

Przejdź do [kroku 5,](empower-people-to-work-remotely-teams-productivity-apps.md) aby rozpocząć pracę z pracownikami hybrydowymi przy Microsoft 365 biurowych, takich jak Microsoft Teams.