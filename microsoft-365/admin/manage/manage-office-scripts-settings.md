---
title: Zarządzanie Office skryptów
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
description: Dowiedz się, jak zarządzać Office skryptów dla użytkowników w organizacji.
ms.openlocfilehash: f03ee34e0ff41c3eb082beca79127cd609496564
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973741"
---
# <a name="manage-office-scripts-settings"></a>Zarządzanie Office skryptów

[Office skrypty](/office/dev/scripts) umożliwiają użytkownikom automatyzowanie zadań przez nagrywanie, edytowanie i uruchamianie skryptów w Excel w sieci Web. Office skrypty działają Power Automate, a użytkownicy uruchamiają skrypty w skoroszytach za pomocą łącznika usługi Excel Online (Business). Microsoft 365 administratorzy mogą zarządzać ustawieniami skryptów Office skryptów z centrum administracyjne platformy Microsoft 365.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Aby zarządzać Office skryptów, musisz być administratorem globalnym. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../add-users/about-admin-roles.md).

- Upewnij się, że użytkownicy w Twojej organizacji mają ważną licencję planu usługi Microsoft 365 lub usługi Office 365 komercyjnego lub EDU, która obejmuje dostęp do aplikacji klasycznych Office, takich jak jeden z następujących planów:

- Microsoft 365 Business Standard
- Aplikacje usługi Microsoft 365 dla firm
- Aplikacje usługi Microsoft 365 dla przedsiębiorstw
- Office 365 E3
- Office 365 E5
- Office 365 A3
- Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Zarządzanie dostępnością Office skryptów i udostępnianiem skryptów

1. W centrum administracyjne platformy Microsoft 365 przejdź do karty Ustawienia  \> **ustawienia organizacji**\>.**[](https://go.microsoft.com/fwlink/p/?linkid=2053743)**

2. Wybierz **pozycję Office skryptów**.

3. Office Skrypty są domyślnie włączone i wszyscy w organizacji mogą korzystać z tej funkcji i udostępniać je. Aby wyłączyć skrypty Office twojej organizacji, wyczyść pole wyboru Pozwalaj użytkownikom na **automatyczne** wykonywanie Excel w sieci Web zadań w aplikacji.

4. Jeśli wcześniej wyłączysz skrypty Office dla organizacji i chcesz włączyć je ponownie, wybierz pozycję Pozwalaj użytkownikom automatyzować zadania w programie **Excel w sieci Web, a** następnie określ, kto może uzyskać dostęp do tej funkcji i korzystać z tej funkcji:

    - Aby zezwolić wszystkim użytkownikom w organizacji na dostęp do skryptów Office skryptów **, pozostaw** zaznaczoną opcję Wszyscy (ustawienie domyślne).

    - Aby zezwolić na dostęp do skryptów programu Office i korzystanie z nich tylko członkom określonej grupy, wybierz pozycję Konk **grupa, a** następnie wprowadź nazwę lub alias e-mail grupy, aby dodać ją do listy zezwalań. Do listy zezwalań można dodać tylko jedną grupę, która musi być jedną z następujących typów:
        - Microsoft 365 grupy
        - Grupa dystrybucyjna
        - Grupa zabezpieczeń
        - Grupa zabezpieczeń z obsługą poczty

        Aby dowiedzieć się więcej o różnych typach grup, zobacz [Porównanie grup](../create-groups/compare-groups.md).

5. Aby zezwolić użytkownikom z dostępem do skryptów Office skryptów na udostępnianie ich skryptów innym osobom w organizacji, wybierz pozycję Zezwalaj użytkownikom z dostępem do skryptów **Office Skrypty** udostępniania skryptów innym osobom w organizacji. Udostępnianie skryptów spoza organizacji jest niedozwolone.

    > [!NOTE]
    > Jeśli później wyłączysz udostępnianie skryptów dla organizacji, użytkownicy nadal będą mogli uruchamiać udostępnione wcześniej skrypty.

6. Określ użytkowników z dostępem do tych Office skryptów:

    - Aby zezwolić wszystkim użytkownikom z dostępem Office skryptów na udostępnianie swoich skryptów, pozostaw zaznaczoną opcję **Wszyscy** (ustawienie domyślne).

    - Aby zezwolić na udostępnianie skryptów tylko członkom określonej grupy z dostępem do skryptów Office Skrypty, wybierz pozycję Konkscriptuj **grupę, a** następnie wprowadź nazwę lub alias e-mail grupy, aby dodać ją do listy zezwalań. Do listy zezwalań można dodać tylko jedną grupę, która musi być jedną z następujących typów:
        - Microsoft 365 grupy
        - Grupa dystrybucyjna
        - Grupa zabezpieczeń
        - Grupa zabezpieczeń z obsługą poczty

        Aby dowiedzieć się więcej o różnych typach grup, zobacz [Porównanie grup](../create-groups/compare-groups.md).

7. Aby umożliwić użytkownikom uruchamianie skryptów Office w Power Automate, wybierz pozycję Zezwalaj użytkownikom na dostęp do skryptów Office **skryptów** uruchamianych przez Power Automate. Dzięki temu użytkownicy mogą dodawać kroki przepływu za pomocą Excel Uruchom skrypt dodatku [Excel Online (](/connectors/excelonlinebusiness)**Business**).

    - Aby zezwolić wszystkim użytkownikom z dostępem Office skryptów na używanie ich skryptów w przepływach **, pozostaw** zaznaczoną opcję Wszyscy (ustawienie domyślne).

    - Aby zezwolić tylko członkom określonej grupy z dostępem do skryptów Office na używanie skryptów przez skrypty we przepływach, wybierz pozycję Konkscriptuj **grupę, a** następnie wprowadź nazwę lub alias e-mail grupy, aby dodać ją do listy zezwalań. Do listy zezwalań można dodać tylko jedną grupę, która musi być jedną z następujących typów:
        - Microsoft 365 grupy
        - Grupa dystrybucyjna
        - Grupa zabezpieczeń
        - Grupa zabezpieczeń z obsługą poczty

        Aby dowiedzieć się więcej o różnych typach grup, zobacz [Porównanie grup](../create-groups/compare-groups.md).

    - Aby dowiedzieć się więcej na temat Office skryptów w Power Automate skryptach, zobacz Uruchamianie skryptów Office [skryptów za pomocą Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. Wybierz **Zapisz**.

    Wprowadzenie zmian w ustawieniach Skryptów pakietu Office może potrwać do 48 godzin.

## <a name="next-steps"></a>Następne kroki

Ponieważ skrypty Office współpracuje z Power Automate, zalecamy zapoznanie się z istniejącymi zasadami ochrony przed utratą danych (DLP, data loss prevention), aby mieć pewność, że dane twojej organizacji pozostają chronione, gdy użytkownicy używają skryptów Office skryptów. Aby uzyskać więcej informacji, zobacz [ Zasady ochrony przed utratą danych (DLP)](/power-automate/prevent-data-loss).

## <a name="related-content"></a>Zawartość pokrewna

[Office dokumentacji technicznej skryptów](/office/dev/scripts/) (strona linku)\
[Wprowadzenie do Office skryptów w Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (artykuł)\
[Udostępnianie Office skryptów w Excel sieci Web](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (artykuł)\
[Nagrywanie, edytowanie i tworzenie skryptów Office skryptów w Excel w sieci Web](/office/dev/scripts/tutorials/excel-tutorial) (artykuł)
