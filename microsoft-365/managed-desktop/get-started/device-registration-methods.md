---
title: Metody rejestracji urządzeń w Microsoft Managed Desktop
description: Informacje o metodach rejestracji urządzeń w aplikacji Microsoft Managed Desktop
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 7d0cabc0a9d11d337e5adabde568bd2a56ceca86
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704670"
---
# <a name="device-registration-methods"></a>Metody rejestracji urządzeń

Aby firma Microsoft może zarządzać Twoimi urządzeniami w Microsoft Managed Desktop, musisz mieć urządzenia zarejestrowane w tej usłudze.

## <a name="registration-process"></a>Proces rejestracji

Microsoft Managed Desktop jest obsługiwany przez usługę Windows Autopilot dla przepływu pracy rejestracji urządzeń. Pomyślna rejestracja urządzeń wymaga dwuetapowego procesu:

1. Unikatowa tożsamość sprzętowa urządzenia, znana jako skrót sprzętowy, jest przechwytywana i przekazywany do usługi Autopilot.
1. Urządzenie jest skojarzone z identyfikatorem Azure Active Directory dzierżawy.

Najlepiej, jeśli oba kroki zostały wykonane przez OEM, odsprzedawcę lub dystrybutora, na którym kupiono urządzenia. Producent OEM lub inny dostawca urządzenia korzysta z procesu autoryzacji rejestracji w celu zarejestrowania urządzenia w Twoim imieniu.

## <a name="registration-methods"></a>Metody rejestracji

Rejestrację można również przeprowadzić w obrębie organizacji, zbierając tożsamość sprzętową z nowych lub istniejących urządzeń i ręcznie ją przesyłając. Poniżej przedstawiono metody rejestracji urządzeń, które Microsoft Managed Desktop obsługuje:

- Rejestracja OEM
    - [Korzystanie z portalu partnera](partner-registration.md#register-devices-using-the-partner-center)
    - [Korzystanie z interfejsów API OEM](partner-registration.md#register-devices-by-using-the-oem-api)
- [Ręczna rejestracja](manual-registration.md)
- [Ręczna rejestracja dla istniejących urządzeń](manual-registration-existing-devices.md)

## <a name="recommended-resources"></a>Zalecane zasoby

- [Omówienie rozwiązania Windows Autopilot](/mem/autopilot/windows-autopilot)
- [Omówienie Windows funkcji Autopilot](/mem/autopilot/registration-overview)

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Procedura rozpoczynania pracy z Microsoft Managed Desktop

1. Portalu [administracyjnego programu](access-admin-portal.md) Access.
1. [Dodaj i zweryfikuj kontakty administratora w portalu administracyjnym](add-admin-contacts.md).
1. [Dostosuj ustawienia po rejestracji](conditional-access.md).
1. Wdrażanie i [przypisywanie Intune — Portal firmy](company-portal.md).
1. [Przypisywanie licencji](assign-licenses.md).
1. [Wdychuj aplikacje](deploy-apps.md).
1. [Przygotowywanie urządzeń](prepare-devices.md).
1. Skonfiguruj środowisko [pierwszego uruchomienia za pomocą rozwiązania Autopilot i strony stanu rejestracji](esp-first-run.md).
1. [Włączanie funkcji pomocy technicznej dla użytkowników](enable-support.md).
1. [Przygotuj użytkowników do korzystania z urządzeń](get-started-devices.md).
1. [Wprowadzenie do sterowania aplikacją](get-started-app-control.md).
