---
title: Czyszczenie urządzenia przenośnego w usłudze Basic Mobility and Security
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
description: Użyj wbudowanej usługi Basic Mobility and Security, aby usunąć informacje z zarejestrowanych urządzeń.
ms.openlocfilehash: 932380b735e3fea2543832417e7911e9216f70fc
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780802"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Czyszczenie urządzenia przenośnego w usłudze Basic Mobility and Security

Możesz użyć wbudowanej usługi Basic Mobility and Security dla Microsoft 365, aby usunąć tylko informacje organizacyjne lub przeprowadzić resetowanie do ustawień fabrycznych, aby usunąć wszystkie informacje z urządzenia przenośnego i przywrócić je do ustawień fabrycznych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Urządzenia przenośne mogą przechowywać poufne informacje organizacyjne i zapewniać dostęp do Microsoft 365 zasobów organizacji. Aby chronić informacje organizacji, możesz zresetować do ustawień fabrycznych lub usunąć dane firmowe:

- **Resetowanie do ustawień fabrycznych**: usuwa wszystkie dane na urządzeniu przenośnym użytkownika, w tym zainstalowane aplikacje, zdjęcia i dane osobowe. Po zakończeniu czyszczenia urządzenie zostanie przywrócone do ustawień fabrycznych.

- **Usuwanie danych firmowych**: usuwa tylko dane organizacji i pozostawia zainstalowane aplikacje, zdjęcia i dane osobowe na urządzeniu przenośnym użytkownika.

- **Po wyczyszczoniu urządzenia (resetowanie do ustawień fabrycznych lub usuwanie danych firmy)** urządzenie zostanie usunięte z listy zarządzanych urządzeń.

- **Automatyczne resetowanie urządzenia**: można skonfigurować zasady podstawowej mobilności i zabezpieczeń, które automatycznie resetują urządzenie do ustawień fabrycznych po tym, jak użytkownik bezskutecznie spróbuje wprowadzić hasło urządzenia określoną liczbę razy. W tym celu wykonaj kroki opisane w temacie [Tworzenie zasad zabezpieczeń urządzeń w podstawowej mobilności i zabezpieczeniach](create-device-security-policies.md).

- **Jeśli chcesz poznać środowisko użytkownika** podczas czyszczenia urządzenia, zobacz [Jaki jest wpływ na użytkownika i urządzenie?](#whats-the-user-and-device-impact).

## <a name="wipe-a-mobile-device"></a>Czyszczenie urządzenia przenośnego

1. Przejdź do [Centrum administracyjne platformy Microsoft 365](../../admin/admin-overview/about-the-admin-center.md).

2. Wpisz Mobile Zarządzanie urządzeniami w polu wyszukiwania i wybierz pozycję **Mobile Zarządzanie urządzeniami** z listy wyników.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Opcja zarządzania urządzeniami przenośnymi Basic Mobility i Secruity.":::

3. Wybierz pozycję **Zarządzaj urządzeniami**.

4. Wybierz urządzenie, które chcesz wyczyścić.

5. Wybierz pozycję **Zarządzaj**.

6. Wybierz wymagany typ zdalnego czyszczenia.

    - Aby przeprowadzić pełne czyszczenie i przywrócić urządzenie do ustawień fabrycznych, wybierz pozycję **Resetowanie do ustawień fabrycznych**.
    - Aby przeprowadzić selektywne czyszczenie i usuwanie tylko Microsoft 365 informacji o organizacji, wybierz pozycję **Usuń dane firmy**.
    - Aby usunąć urządzenie z organizacji, wybierz pozycję **Usuń urządzenie**.

7. Wybierz pozycję **Tak**, aby potwierdzić.

## <a name="how-do-i-know-it-worked"></a>Jak mogę wiedzieć, że to zadziałało?

Urządzenie przenośne nie jest już widoczne na liście urządzeń zarządzanych.

## <a name="why-would-you-want-to-wipe-a-device"></a>Dlaczego chcesz wyczyścić urządzenie?

Wyczyść urządzenie z następujących powodów:

- Urządzenia przenośne, takie jak smartfony i tablety, stają się coraz bardziej funkcjonalne przez cały czas. Oznacza to, że użytkownicy mogą łatwiej przechowywać poufne informacje firmowe, takie jak identyfikacja osobista lub poufna komunikacja, i uzyskiwać do nich dostęp w podróży. Jeśli jedno z tych urządzeń przenośnych zostanie utracone lub skradzione, wyczyszczenie urządzenia może pomóc zapobiec trafieniu informacji organizacji w niepowołane ręce.
- Gdy użytkownik opuszcza organizację przy użyciu urządzenia osobistego zarejestrowanego w usłudze Basic Mobility and Security, możesz zapobiec przechodzeniu informacji organizacji z tym użytkownikiem, przeprowadzając resetowanie do ustawień fabrycznych.
- Jeśli Organizacja udostępnia urządzenia przenośne użytkownikom, może być konieczne ponowne przypisanie urządzeń od czasu do czasu. Przeprowadzenie resetowania do ustawień fabrycznych na urządzeniu przed przypisaniem go do nowego użytkownika pomaga zapewnić usunięcie wszelkich poufnych informacji od poprzedniego właściciela.

## <a name="whats-the-user-and-device-impact"></a>Jaki jest wpływ na użytkownika i urządzenie?

Czyszczenie jest wysyłane natychmiast do urządzenia przenośnego, a urządzenie jest oznaczone jako niezgodne w usłudze Azure Active Directory. Podczas gdy wszystkie dane są usuwane po zresetowaniu urządzenia do ustawień domyślnych fabrycznych, w poniższej tabeli opisano, jaka zawartość jest usuwana dla każdego typu urządzenia podczas usuwania danych firmowych.

|Wpływ na zawartość|iOS|Android|
|---|---|---|
|Microsoft 365 dane aplikacji zostaną wyczyszczone, jeśli urządzenie jest chronione przez zasady usługi Intune App Protection. Aplikacje nie są usuwane. W przypadku urządzeń, które nie są chronione przez zasady zarządzania aplikacjami mobilnymi (MAM), Outlook i OneDrive nie będą usuwać danych w pamięci podręcznej.<br/>**Uwaga** Do stosowania zasad Intune Ochrona aplikacji musisz mieć licencję Intune.|Tak|Tak|
|Ustawienia zasad stosowane przez pakiety Basic Mobility and Security do urządzeń nie są już wymuszane; użytkownicy mogą zmieniać ustawienia.|Tak|Tak|
|Profile poczty e-mail utworzone przez usługi Basic Mobility and Security są usuwane, a buforowana wiadomość e-mail na urządzeniu jest usuwana.|Tak|nd.|

> [!NOTE]
> Portal firmy aplikacja jest dostępna w App Store dla urządzeń z systemem iOS i Sklep Play dla urządzeń z systemem Android.
