---
title: Czyszczenie urządzenia przenośnego w pakietach Basic Mobility and Security
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: Aby usunąć informacje z zarejestrowanych urządzeń, skorzystaj z wbudowanych funkcji basic mobility i zabezpieczeń.
ms.openlocfilehash: ed658abc55d065e6d271893dc80a293e19373a34
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983926"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Czyszczenie urządzenia przenośnego w pakietach Basic Mobility and Security

Możesz używać wbudowanych funkcji Basic Mobility and Security dla usługi Microsoft 365, aby usunąć tylko informacje organizacyjne, lub wykonać przywracanie ustawień fabrycznych w celu usunięcia wszystkich informacji z urządzenia przenośnego i przywrócenia ich do ustawień fabrycznych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Urządzenia przenośne mogą przechowywać poufne informacje organizacyjne i zapewniać dostęp do zasobów Microsoft 365 organizacji. Aby chronić informacje Twojej organizacji, możesz wykonać resetowanie ustawień fabrycznych lub usunąć dane firmowe:

- **Resetowanie** do ustawień fabrycznych: Usuwa wszystkie dane na urządzeniu przenośnym użytkownika, w tym zainstalowane aplikacje, zdjęcia i informacje osobiste. Po zakończeniu czyszczenia urządzenie zostanie przywrócone do ustawień fabrycznych.

- **Usuwanie danych firmowych**: Usuwa tylko dane organizacji i pozostawia zainstalowane aplikacje, zdjęcia i informacje osobiste na urządzeniu przenośnym użytkownika.

- **Po wyczyszczeniu urządzenia (resetowanie do ustawień fabrycznych** lub usunięcie danych firmy) urządzenie zostanie usunięte z listy urządzeń zarządzanych.
    
- **Automatyczne resetowanie** urządzenia: Możesz skonfigurować zasady mobilności podstawowej i zabezpieczeń, które będą automatycznie resetować urządzenie przy użyciu ustawień fabrycznych po określonej liczbie nieudanych prób wprowadzenia hasła do urządzenia przez użytkownika. W tym celu wykonaj czynności opisane  [wTworzenie zasad zabezpieczeń urządzeń w zakresie podstawowej mobilności i zabezpieczeń](create-device-security-policies.md).
    
- **Jeśli chcesz poznać sposób obsługi użytkownika** podczas czyszczenia urządzenia, zobaczCo   [to jest wpływ na użytkownika i urządzenie?](#whats-the-user-and-device-impact).

## <a name="wipe-a-mobile-device"></a>Czyszczenie urządzenia przenośnego

1. Przejdź do  [centrum administracyjne platformy Microsoft 365](../../admin/admin-overview/about-the-admin-center.md).

2. Wpisz Zarządzanie urządzeniami przenośnymi w polu wyszukiwania, a następnie z listy wyników wybierz pozycję **Zarządzanie** urządzeniami przenośnymi.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Opcja zarządzania urządzeniami przenośnymi w wersji Basic Mobility i Secruity.":::

3. Wybierz **pozycję Zarządzaj urządzeniami**.

4. Wybierz urządzenie, które chcesz wyczyścić.

5. Wybierz **pozycję Zarządzaj**.

6. Wybierz wymagany typ zdalnego czyszczenia.

    - Aby wykonać pełne czyszczenie i przywrócić ustawienia fabryczne urządzenia, wybierz pozycję **Resetowanie do ustawień fabrycznych**.
    - Aby wykonać czyszczenie selektywne i usunąć tylko Microsoft 365 informacji o organizacji, wybierz **pozycję Usuń dane firmowe**.
    - Aby usunąć urządzenie ze swojej organizacji, wybierz **pozycję Usuń urządzenie**.

7. Wybierz pozycję **Tak**, aby potwierdzić.

## <a name="how-do-i-know-it-worked"></a>Skąd wiadomo, że to zadziałało?

Nie widzisz już tego urządzenia przenośnego na liście urządzeń zarządzanych.

## <a name="why-would-you-want-to-wipe-a-device"></a>Dlaczego warto wyczyścić urządzenie?

Wyczyść urządzenie z tych powodów:

- Urządzenia przenośne, takie jak smartfony i tablety, cały czas stają się pełniejsze. Oznacza to, że użytkownicy mogą łatwiej przechowywać poufne informacje firmowe, takie jak dane osobowe lub poufna komunikacja, i korzystać z nich w podróży. Jeśli jedno z tych urządzeń przenośnych zostanie zgubione lub skradzione, jego wyigrowanie może zapobiec dojściu informacji Twojej organizacji do niewłaściwych ręce.
- Gdy użytkownik odchodzi z organizacji, korzystając z urządzenia osobistego zarejestrowanego w pakietach Basic Mobility and Security, można zapobiec kontaktom z informacjami organizacyjnymi, wykonując resetowanie ustawień fabrycznych.
- Jeśli Twoja organizacja udostępnia użytkownikom urządzenia przenośne, od czasu do czasu może być konieczne ponowne przypisanie tych urządzeń. Wykonanie resetowania ustawień fabrycznych na urządzeniu przed przypisaniem go nowemu użytkownikowi pozwala zagwarantować, że poufne informacje poprzedniego właściciela zostały usunięte.

## <a name="whats-the-user-and-device-impact"></a>Jaki jest wpływ na użytkownika i urządzenie?

Czyszczenie jest natychmiast wysyłane do urządzenia przenośnego, a urządzenie jest oznaczone jako niezgodne w usłudze Azure Active Directory. Mimo że wszystkie dane są usuwane po przywróceniu urządzenia do ustawień domyślnych fabrycznych, w poniższej tabeli opisano, jaka zawartość jest usuwana dla każdego typu urządzenia w przypadku usunięcia danych firmowych.

|**Wpływ na zawartość**|**iOS 10 lub nowszy**|**Android 5 lub nowszy**|
|:-----|:-----|:-----|
|Microsoft 365 dane aplikacji są czyszowane, jeśli urządzenie jest chronione przez zasady usługi Intune App Protection. Aplikacje nie zostaną usunięte. W przypadku urządzeń, które nie są chronione przez zasady zarządzania aplikacjami mobilnymi (MAM), Outlook i OneDrive nie usuwają danych buforowanych.<br/>**Uwaga** Aby zastosować zasady ochrony aplikacji Intune, musisz mieć licencję usługi Intune.|Tak|Tak|
|Ustawienia zasad stosowane w pakietach Basic Mobility i Security do urządzeń nie są już wymuszane. użytkownicy mogą zmienić te ustawienia.|Tak|Tak|
|Profile poczty e-mail utworzone w pakietach Basic Mobility i Security są usuwane oraz są usuwane z pamięci podręcznej wiadomości e-mail na urządzeniu.|Tak|Nie dotyczy|

> [!NOTE]
> Portal firmy aplikacja jest dostępna w sklepach App Store dla systemu iOS i Play Store dla urządzeń z systemem Android.
