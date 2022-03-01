---
title: Instalowanie Intune — Portal firmy na urządzeniach
description: Informacje na temat instalowania aplikacji portalu firmy na Microsoft Managed Desktop urządzeniach
keywords: Microsoft Managed Desktop, Microsoft 365, Portal firmy
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 48d9129689a820816dffe65355fa913fd0742864
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63015971"
---
# <a name="install-intune-company-portal-on-devices"></a>Instalowanie Intune — Portal firmy na urządzeniach

Microsoft Managed Desktop administratorów IT musi zainstalować Intune — Portal firmy użytkowników na Microsoft Managed Desktop urządzeniach. Korzyści dla Twojej organizacji to:

- Użytkownicy mają jedno miejsce, w którym można przeglądać i instalować dostępne aplikacje.
- Administratorzy IT mogą organizować aplikacje według kategorii dla swoich użytkowników.  
- Niektóre aplikacje (takie jak Microsoft Project i Microsoft Visio) wymagają Portal firmy w celu wdrożenia z Microsoft Managed Desktop.
- Administratorzy IT mogą dostosowywać Portal firmy organizacji. Dostosowania obejmują między innymi obrazowanie marki, dodawanie do lokalnych kontaktów pomocy technicznej. Aby uzyskać więcej informacji, [zobacz Jak skonfigurować Microsoft Intune Portal firmy aplikacji](/intune/company-portal-app).

Ten artykuł dokumentuje proces wdrażania aplikacji Intune — Portal firmy u Microsoft Managed Desktop użytkowników. Cały proces wygląda następująco:

1. [Kup Portal firmy produktu Microsoft Store dla Firm i zsynchronizuj usługę Intune](#step-1-purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune).
2. [Przypisz Portal firmy do użytkowników](#step-2-assign-company-portal-to-your-users).
3. [Zakomunikuj zmiany użytkownikom.](#step-3-communicate-change-to-your-users)

## <a name="step-1-purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune"></a>Krok 1. Zakup Portal firmy usłudze Microsoft Store dla Firm i synchronizowanie z usługą Intune

Aby uzyskać informacje na temat kupowania aplikacji i synchronizowania ich z usługą Intune, zobacz Microsoft Store dla Firm [w](deploy-apps.md#msfb-apps) tesłudze *Wdrażanie aplikacji na Microsoft Managed Desktop urządzeniach*.

W tym artykule opisano, jak to zrobić:

- Kup Portal firmy od Microsoft Store dla Firm.
- Wymuszaj synchronizację między usługą Intune a Microsoft Store dla Firm.
- Weryfikowanie aktywnej synchronizacji między usługą Intune a Microsoft Store dla Firm.

## <a name="step-2-assign-company-portal-to-your-users"></a>Krok 2. Przypisywanie Portal firmy do użytkowników

Po zarejestrowaniu się w Microsoft Managed Desktop automatycznie wdrożymy aplikację Portal firmy Twojej dzierżawy i zainstalujemy aplikację na Microsoft Managed Desktop urządzeniach w Twojej organizacji.

## <a name="step-3-communicate-change-to-your-users"></a>Krok 3. Zakomunikuj zmianę użytkownikom

Jako administrator IT w organizacji, ważne jest, aby twoi użytkownicy wiedzieli, jak korzystać Portal firmy w organizacji. Microsoft Managed Desktop zalecamy:

- Kroki instalowania aplikacji z Portal firmy. Aby uzyskać więcej informacji, [zobacz Instalowanie i udostępnianie aplikacji na urządzeniu](/intune-user-help/install-apps-cpapp-windows).
- Jak wysyłać do administratorów IT żądania dla aplikacji, które nie są obecnie dostępne. Aby uzyskać więcej informacji, zobacz [Żądanie aplikacji służbowej lub szkolnej](/intune-user-help/install-apps-cpapp-windows#request-an-app-for-work-or-school).  

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Procedura rozpoczynania pracy z Microsoft Managed Desktop

1. Portalu [administracyjnego programu](access-admin-portal.md) Access.
1. [Dodaj i zweryfikuj kontakty administratora w portalu administracyjnym](add-admin-contacts.md).
1. [Dostosuj ustawienia po rejestracji](conditional-access.md).
1. Wdrażanie i przypisywanie Intune — Portal firmy (ten artykuł).
1. [Przypisywanie licencji](assign-licenses.md).
1. [Wdychuj aplikacje](deploy-apps.md).
1. [Konfigurowanie urządzeń](set-up-devices.md)
1. Skonfiguruj środowisko [pierwszego uruchomienia za pomocą rozwiązania Autopilot i strony stanu rejestracji](esp-first-run.md).
1. [Włączanie funkcji pomocy technicznej dla użytkowników](enable-support.md).
1. [Przygotuj użytkowników do korzystania z urządzeń](get-started-devices.md).
1. [Wprowadzenie do sterowania aplikacją](get-started-app-control.md).
