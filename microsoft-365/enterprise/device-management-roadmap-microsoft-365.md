---
title: Plan zarządzania urządzeniami dla Microsoft 365
keywords: Microsoft 365, Microsoft 365 dla przedsiębiorstw, dokumentacja Microsoft 365, zarządzanie urządzeniami przenośnymi, Intune
author: kelleyvice-msft
ms.author: kvice
manager: scotv
ms.date: 08/10/2020
ms.topic: conceptual
f1.keywords:
- NOCSH
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
audience: ITPro
ms.custom: microsoft-intune
description: Plan konfigurowania zarządzania urządzeniami dla Microsoft 365.
ms.openlocfilehash: eeed1a69fc1724f3feb75f4bc096cad3a3c25cf0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095317"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>Plan zarządzania urządzeniami dla Microsoft 365

Microsoft 365 dla przedsiębiorstw obejmuje funkcje ułatwiające zarządzanie urządzeniami i ich aplikacjami w organizacji. Zarządzanie urządzeniami przenośnymi ułatwia zabezpieczanie i ochronę zasobów organizacji.

Istnieją dwie opcje zarządzania urządzeniami:

- [Microsoft Intune](#microsoft-intune)
- [Funkcja Podstawowa mobilność i zabezpieczenia](#basic-mobility-and-security)

## <a name="microsoft-intune"></a>Microsoft Intune

Za pomocą Microsoft Intune można zarządzać dostępem do organizacji przy użyciu zarządzania urządzeniami przenośnymi lub zarządzania aplikacjami mobilnymi. Zarządzanie urządzeniami przenośnymi polega na tym, że użytkownicy "rejestrują" swoje urządzenia w Intune. Po zarejestrowaniu urządzenia jest to urządzenie zarządzane. W związku z tym może odbierać zasady, reguły i ustawienia organizacji. Można na przykład zainstalować określone aplikacje, utworzyć zasady haseł, zainstalować połączenie sieci VPN i nie tylko.

Użytkownicy z własnymi urządzeniami osobistymi mogą nie chcieć rejestrować swoich urządzeń ani zarządzać nimi za pomocą Intune i zasad organizacji. Jednak nadal musisz chronić zasoby i dane organizacji. W tym scenariuszu możesz chronić aplikacje przy użyciu zarządzania aplikacjami mobilnymi. Na przykład można użyć zasad zarządzania aplikacjami mobilnymi, które wymagają od użytkownika wprowadzenia numeru PIN podczas uzyskiwania dostępu do SharePoint Online na urządzeniu.

Określisz również sposób zarządzania urządzeniami osobistymi i urządzeniami należącymi do organizacji. W zależności od ich zastosowań warto traktować urządzenia inaczej.

## <a name="basic-mobility-and-security"></a>Funkcja Podstawowa mobilność i zabezpieczenia

Jest to wbudowane w Microsoft 365 i ułatwia zabezpieczanie urządzeń przenośnych użytkowników, takich jak telefony iPhone, iPady, Androidy i Windows telefony oraz zarządzanie nimi. Możesz tworzyć zasady zabezpieczeń urządzeń i zarządzać nimi, zdalnie czyścić urządzenie oraz wyświetlać szczegółowe raporty dotyczące urządzeń.

## <a name="choose-between-the-two-options"></a>Wybierz jedną z dwóch opcji

Aby lepiej ocenić, która opcja zarządzania urządzeniami jest najlepsza, zobacz [Wybieranie między usługą Basic Mobility Security i Intune](/office365/securitycompliance/choose-between-mdm-and-intune).

Na podstawie oceny rozpocznij zarządzanie urządzeniami za pomocą:

- [Intune](/microsoft-365/solutions/manage-devices-with-intune-overview)
- [Funkcja Podstawowa mobilność i zabezpieczenia](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd)
 
## <a name="identity-and-device-access-recommendations"></a>Zalecenia dotyczące tożsamości i dostępu do urządzeń

Firma Microsoft udostępnia zestaw zaleceń dotyczących [tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md) w celu zapewnienia bezpiecznej i produktywnej siły roboczej. Aby uzyskać dostęp do urządzenia, skorzystaj z zaleceń i ustawień w następujących artykułach:

- [Wymagania wstępne](../security/office-365-security/identity-access-prerequisites.md)
- [Wspólne zasady tożsamości i dostępu do urządzeń](../security/office-365-security/identity-access-policies.md)

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>Jak firma Contoso wykonywała zarządzanie urządzeniami dla Microsoft 365

Aby uzyskać informacje o tym, jak fikcyjna, ale reprezentatywna firma wielonarodowa wdrożyła infrastrukturę zarządzania urządzeniami przenośnymi za pomocą usług w chmurze Microsoft 365, zobacz [Zarządzanie urządzeniami przenośnymi w firmie Contoso](contoso-mdm.md).