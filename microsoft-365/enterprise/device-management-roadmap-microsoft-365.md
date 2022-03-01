---
title: Przewodnik po zarządzaniu urządzeniami dla Microsoft 365
keywords: Microsoft 365, Microsoft 365 dla przedsiębiorstw, Microsoft 365, zarządzanie urządzeniami przenośnymi, Intune
author: kelleyvice-msft
ms.author: kvice
manager: laurawi
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
description: Przewodnik po skonfigurowaniu zarządzania urządzeniami na Microsoft 365.
ms.openlocfilehash: 0fef31697657b4694090ae7a1b63516920d8c71b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021285"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>Przewodnik po zarządzaniu urządzeniami dla Microsoft 365

Microsoft 365 dla przedsiębiorstwa zawiera funkcje, które ułatwiają zarządzanie urządzeniami i ich aplikacjami w organizacji. Zarządzanie urządzeniami przenośnymi ułatwia zabezpieczanie i ochronę zasobów organizacji.

Istnieją dwie opcje zarządzania urządzeniami:

- [Microsoft Intune](#microsoft-intune)
- [Podstawowa mobilność i zabezpieczenia](#basic-mobility-and-security)

## <a name="microsoft-intune"></a>Microsoft Intune

Za pomocą aplikacji Microsoft Intune zarządzać dostępem do organizacji za pomocą zarządzania urządzeniami przenośnymi lub zarządzania aplikacją mobilną. Zarządzanie urządzeniami przenośnymi jest oznaczane przez użytkowników podczas "rejestrowania" swoich urządzeń w usłudze Intune. Po zarejestrowaniu urządzenia jest ono urządzeniem zarządzanym. dlatego może on otrzymywać zasady, reguły i ustawienia Twojej organizacji. Możesz na przykład zainstalować określone aplikacje, utworzyć zasady dotyczące haseł, zainstalować połączenie VPN i nie tylko.

Użytkownicy z własnymi urządzeniami osobistymi mogą nie chcieć rejestrować swoich urządzeń lub być zarządzani przez usługę Intune i zasady Twojej organizacji. Nadal jednak musisz chronić zasoby i dane organizacji. W tym scenariuszu możesz chronić aplikacje za pomocą zarządzania aplikacjami mobilnymi. Możesz na przykład użyć zasad zarządzania aplikacją mobilną, które wymagają od użytkownika wprowadzenia numeru PIN podczas uzyskiwania dostępu do aplikacji SharePoint Online na urządzeniu.

Dowiesz się także, jak będziesz zarządzać urządzeniami osobistymi i urządzeniami należącymi do organizacji. Urządzenia można traktować inaczej w zależności od ich zastosowania.

## <a name="basic-mobility-and-security"></a>Podstawowa mobilność i zabezpieczenia

Jest to wbudowane Microsoft 365 i ułatwia zabezpieczanie urządzeń przenośnych użytkowników, takich jak telefony iPhone, tablety iPad, urządzenia z systemem Android Windows przenośnych. Możesz tworzyć zasady zabezpieczeń urządzeń i zarządzać nimi, zdalnie wyczyścić urządzenie i wyświetlać szczegółowe raporty dotyczące urządzeń.

## <a name="choose-between-the-two-options"></a>Wybierz jedną z dwóch opcji

Aby ułatwić ocenę najlepszej dla Ciebie opcji zarządzania urządzeniami, zobacz Wybór [między pakietem Basic Mobility Security a usługą Intune](/office365/securitycompliance/choose-between-mdm-and-intune).

Na podstawie oceny, wprowadzenie do zarządzania urządzeniami za pomocą:

- [Intune](/microsoft-365/solutions/manage-devices-with-intune-overview)
- [Podstawowa mobilność i zabezpieczenia](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd)
 
## <a name="identity-and-device-access-recommendations"></a>Zalecenia dotyczące dostępu do urządzenia i tożsamości

Firma Microsoft udostępnia zestaw zaleceń dotyczących tożsamości i [dostępu](../security/office-365-security/microsoft-365-policies-configurations.md) do urządzeń, aby zapewnić bezpieczeństwo i produktywność pracowników. Aby uzyskać dostęp do urządzenia, skorzystaj z zaleceń i ustawień poszczególnych artykułów:

- [Wymagania wstępne](../security/office-365-security/identity-access-prerequisites.md)
- [Typowe zasady dostępu do urządzeń i tożsamości](../security/office-365-security/identity-access-policies.md)

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>Jak firma Contoso miała zarządzanie urządzeniami w Microsoft 365

Aby uzyskać informacje o tym, jak fikcyjna, ale reprezentatywna, wielonarodowa firma wdrożyła swoją infrastrukturę zarządzania urządzeniami przenośnymi za pomocą usług Microsoft 365 w chmurze, zobacz Zarządzanie urządzeniami przenośnymi [dla firmy Contoso](contoso-mdm.md).