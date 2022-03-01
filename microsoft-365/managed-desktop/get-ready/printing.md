---
title: Przygotowywanie zasobów do drukowania Microsoft Managed Desktop
description: Ważne czynności, które należy wykonać, aby zapewnić płynne drukowanie
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: a66075637a15eb39eda38e318070af2bcbdc8fe6
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016074"
---
# <a name="prepare-printing-resources-for-microsoft-managed-desktop"></a>Przygotowywanie zasobów do drukowania Microsoft Managed Desktop

Gdy przygotujesz się do rejestracji w programie Microsoft Managed Desktop, musisz ocenić wymagania dotyczące drukowania i określić odpowiednie podejście do środowiska. Dostępne są trzy opcje:

| Opcja | Opis |
| ------ | ------ |
| Wdrażanie rozwiązania Microsoft Universal Print | Uniwersalne rozwiązanie firmy Microsoft do drukowania ułatwia Microsoft Managed Desktop drukarki. Aby uzyskać więcej informacji, zobacz [Co to jest drukowanie uniwersalne](/universal-print/fundamentals/universal-print-whatis). |
| Bezpośrednie wdrażanie drukarek przy użyciu niestandardowego skryptu programu PowerShell | Postępuj zgodnie z instrukcjami [w sekcji Konfigurowanie drukarek lokalnych](#set-up-local-printers) . |
| Używanie rozwiązania do drukowania w chmurze firmy innych niż Firma Microsoft | Użyj rozwiązania do drukowania w chmurze innych niż firma Microsoft, które jest zgodne z Windows 10 i przyłączone do domeny Azure Active Directory danych. Rozwiązanie musi spełniać wymagania dotyczące oprogramowania Microsoft Managed Desktop. Aby uzyskać więcej informacji, [Microsoft Managed Desktop wymagania dotyczące aplikacji](../service-description/mmd-app-requirements.md). |

We wszystkich powyższych opcjach, jeśli sterowniki drukarek nie są dostępne w uwitrynie Microsoft Update lub programie Microsoft Store, musisz uzyskać je samodzielnie i zapakować do wdrożenia na urządzeniach z systemem Microsoft Managed Desktop z systemem Microsoft Intune. Aby uzyskać więcej informacji, zobacz [Autonomiczna usługa Intune — zarządzanie aplikacją Win32](/mem/intune/apps/apps-win32-app-management)

## <a name="set-up-local-printers"></a>Konfigurowanie drukarek lokalnych

W poniższych instrukcjach założono, że zostały przygotowane zasoby do drukowania i zdecydowano się na wdrożenie drukarek przy użyciu niestandardowego skryptu programu PowerShell.

**Aby wdrożyć drukarki przy użyciu niestandardowego skryptu programu PowerShell:**

1. Przejdź do Microsoft Managed Desktop witryny.
1. Prześlij żądanie z etykietą *Wdrożenie drukarki* w sekcji pomoc **> pomocy technicznej** w portalu administracyjnym.
1. Podaj następujące szczegóły:
    - Wszystkie ścieżki UNC do udostępnionych lokalizacji drukarek, które należy wdrożyć na Microsoft Managed Desktop urządzeniach.
    - Grupy użytkowników wymagające dostępu do tych drukarek udostępnionych.
1. Za pomocą portalu administracyjnego otrzymasz informacje po zakończeniu żądania. Początkowo konfigurację wdrożymy tylko na urządzeniach w grupie Testowanie wdrożenia.
1. Przetestuj i potwierdź, czy konfiguracja działa zgodnie z oczekiwaniami.
1. Odpowiedz, używając karty **Dyskusja** w wniosku o pomoc techniczną, aby nas o tym wiedzieć po zakończeniu testowania.
1. Następnie wdrożymy konfigurację w innych grupach wdrożeniowych.

## <a name="steps-to-get-ready"></a>Czynności, które należy wykonać, aby się przygotować

1. Przejrzyj [wymagania wstępne dotyczące Microsoft Managed Desktop](prerequisites.md).
1. Uruchom [narzędzia do oceny gotowości](readiness-assessment-tool.md).
1. Kup [Portal firmy](../get-started/company-portal.md).
1. Przejrzyj [wymagania wstępne dotyczące kont gości](guest-accounts.md).
1. Sprawdź [konfigurację sieci](network.md).
1. [Przygotowywanie certyfikatów i profilów sieci](certs-wifi-lan.md).
1. [Przygotowywanie dostępu użytkownika do danych](authentication.md).
1. [Przygotowywanie aplikacji](apps.md).
1. [Przygotowywanie zamapowanych dysków](mapped-drives.md).
1. Przygotowywanie zasobów do drukowania (ten artykuł).
1. Nazwy [urządzeń adresowych](address-device-names.md).
