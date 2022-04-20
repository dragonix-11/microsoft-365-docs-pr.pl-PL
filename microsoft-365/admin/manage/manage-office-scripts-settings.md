---
title: Ustawienia dotyczące zarządzania skryptami pakietu Office
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
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
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Dowiedz się, jak zarządzać ustawieniami skryptów Office dla użytkowników w organizacji.
ms.openlocfilehash: fdc9c947ee7f12e284fd215f05f8b5c3dcb127eb
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941154"
---
# <a name="manage-office-scripts-settings"></a>Ustawienia dotyczące zarządzania skryptami pakietu Office

[Office Scripts umożliwia użytkownikom automatyzowanie](/office/dev/scripts) zadań przez rejestrowanie, edytowanie i uruchamianie skryptów w Excel w sieci Web. Office Scripts współpracuje z Power Automate, a użytkownicy uruchamiają skrypty w skoroszytach przy użyciu łącznika Excel Online (business). Microsoft 365 administratorzy mogą zarządzać ustawieniami skryptów Office z Centrum administracyjne platformy Microsoft 365.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Aby zarządzać ustawieniami skryptów Office, musisz być administratorem globalnym. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratora](../add-users/about-admin-roles.md).

- Upewnij się, że użytkownicy w organizacji mają ważną licencję na Microsoft 365 lub Office 365 plan komercyjny lub EDU, który obejmuje dostęp do Office aplikacji klasycznych, takich jak jeden z następujących planów:

- Microsoft 365 Business Standard
- Aplikacje usługi Microsoft 365 dla firm
- Aplikacje usługi Microsoft 365 dla przedsiębiorstw
- Office 365 E3
- Office 365 E5
- Office 365 A3
- Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Zarządzanie dostępnością skryptów Office i udostępnianiem skryptów

1. W Centrum administracyjne platformy Microsoft 365 przejdź do karty **[Usługi](https://go.microsoft.com/fwlink/p/?linkid=2053743)** **ustawień** \> **organizacji Ustawienia**\>.

2. Wybierz **pozycję Office Skrypty**.

3. Office Skrypty są domyślnie włączone, a wszyscy w organizacji mogą uzyskiwać dostęp do funkcji i udostępniać skrypty oraz korzystać z nich. Aby wyłączyć Office Skrypty dla organizacji, wyczyść pole wyboru **Zezwalaj użytkownikom na automatyzowanie zadań w Excel w sieci Web**.

4. Jeśli wcześniej wyłączono Office Skrypty dla organizacji i chcesz ją ponownie włączyć, wybierz pozycję **Zezwalaj użytkownikom na automatyzowanie zadań w Excel w sieci Web**, a następnie określ, kto może uzyskać dostęp do tej funkcji i z niej korzystać:

    - Aby zezwolić wszystkim użytkownikom w organizacji na dostęp do skryptów Office i korzystanie z nich, pozostaw opcję **Wszyscy** (wartość domyślna).

    - Aby zezwolić tylko członkom określonej grupy na dostęp i używanie skryptów Office, wybierz pozycję **Określona grupa**, a następnie wprowadź nazwę lub alias wiadomości e-mail grupy, aby dodać ją do listy dozwolonych. Do listy dozwolonych można dodać tylko jedną grupę, która musi być jednym z następujących typów:
        - grupa Microsoft 365
        - Grupa dystrybucyjna
        - Grupa zabezpieczeń
        - Grupa zabezpieczeń z obsługą poczty

        Aby dowiedzieć się więcej na temat różnych typów grup, zobacz [Porównanie grup](../create-groups/compare-groups.md).

5. Aby umożliwić użytkownikom z dostępem do skryptów Office udostępnianie skryptów innym osobom w organizacji, wybierz pozycję **Zezwalaj użytkownikom na dostęp do skryptów Office udostępniać skrypty innym osobom w organizacji**. Udostępnianie skryptów spoza organizacji jest niedozwolone.

    > [!NOTE]
    > Jeśli później wyłączysz udostępnianie skryptów w organizacji, użytkownicy nadal będą mogli uruchamiać skrypty udostępnione wcześniej.

6. Określ, którzy użytkownicy z dostępem do skryptów Office mogą udostępniać swoje skrypty:

    - Aby zezwolić wszystkim użytkownikom z dostępem do skryptów Office do udostępniania skryptów, pozostaw opcję **Wszyscy** (wartość domyślna).

    - Aby zezwolić na udostępnianie skryptów tylko członkom określonej grupy z dostępem do skryptów Office, wybierz pozycję **Określona grupa**, a następnie wprowadź nazwę lub alias wiadomości e-mail grupy, aby dodać ją do listy dozwolonych. Do listy dozwolonych można dodać tylko jedną grupę, która musi być jednym z następujących typów:
        - grupa Microsoft 365
        - Grupa dystrybucyjna
        - Grupa zabezpieczeń
        - Grupa zabezpieczeń z obsługą poczty

        Aby dowiedzieć się więcej na temat różnych typów grup, zobacz [Porównanie grup](../create-groups/compare-groups.md).

7. Aby umożliwić użytkownikom uruchamianie skryptów Office wewnątrz przepływów Power Automate, wybierz pozycję **Zezwalaj użytkownikom z dostępem do skryptów Office uruchamiać skrypty za pomocą Power Automate**. Dzięki temu użytkownicy mogą dodawać kroki przepływu za pomocą opcji **Skrypt uruchamiania** [łącznika usługi Excel Online (Business](/connectors/excelonlinebusiness)).

    - Aby zezwolić wszystkim użytkownikom z dostępem do skryptów Office na używanie skryptów w przepływach, pozostaw opcję **Wszyscy** (wartość domyślna).

    - Aby zezwolić tylko członkom określonej grupy z dostępem do Office Scripts na używanie ich skryptów w przepływach, wybierz pozycję **Określona grupa**, a następnie wprowadź nazwę lub alias wiadomości e-mail grupy, aby dodać ją do listy dozwolonych. Do listy dozwolonych można dodać tylko jedną grupę, która musi być jednym z następujących typów:
        - grupa Microsoft 365
        - Grupa dystrybucyjna
        - Grupa zabezpieczeń
        - Grupa zabezpieczeń z obsługą poczty

        Aby dowiedzieć się więcej na temat różnych typów grup, zobacz [Porównanie grup](../create-groups/compare-groups.md).

    - Aby dowiedzieć się więcej na temat używania skryptów Office z Power Automate, zobacz [Uruchamianie skryptów Office przy użyciu Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. Wybierz **Zapisz**.

    Wprowadzenie zmian w ustawieniach Skryptów pakietu Office może potrwać do 48 godzin.

## <a name="next-steps"></a>Następne kroki

Ponieważ skrypty Office współdziałają z Power Automate, zalecamy zapoznanie się z istniejącymi zasadami ochrony przed utratą danych (DLP) w usłudze Microsoft Purview, aby zapewnić ochronę danych organizacji, gdy użytkownicy używają skryptów Office. Aby uzyskać więcej informacji, zobacz [ Zasady ochrony przed utratą danych (DLP)](/power-automate/prevent-data-loss).

## <a name="related-content"></a>Zawartość pokrewna

[dokumentacja techniczna skryptów Office](/office/dev/scripts/) (strona linku)\
[Wprowadzenie do skryptów Office w Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (artykuł)\
[Udostępnianie skryptów Office w Excel dla sieci Web](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (artykuł)\
[Rejestrowanie, edytowanie i tworzenie skryptów Office w Excel w sieci Web](/office/dev/scripts/tutorials/excel-tutorial) (artykuł)
