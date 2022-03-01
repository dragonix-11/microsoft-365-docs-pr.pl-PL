---
title: Wdrażanie aplikacji na urządzeniach
description: Informacje dotyczące dodawania i wdrażania aplikacji na Microsoft Managed Desktop urządzeniach.
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja, aplikacje, aplikacje biznesowe, aplikacje LOB
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 7e4ee96fb336205633430f34111d3d845c1f0e6e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015930"
---
# <a name="deploy-apps-to-devices"></a>Wdrażanie aplikacji na urządzeniach

Elementem wdrażania pakietu Microsoft Managed Desktop jest dodawanie i wdrażanie aplikacji na urządzeniach użytkowników. Gdy korzystasz z portalu Microsoft Managed Desktop, możesz dodawać i wdrażać aplikacje.

Cały proces wygląda następująco:

1. [Dodawanie aplikacji do Microsoft Managed Desktop](#1): Mogą to być istniejące aplikacje firmowe (LOB) lub aplikacje z usługi Microsoft Store dla Firm zsynchronizowane z usługą Intune.
2. [Tworzenie Azure Active Directory aplikacji (AD](#2)): te grupy będą używać do zarządzania przypisaniem aplikacji.
3. [Przypisz aplikacje do użytkowników](#3).

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>Krok 1. Dodawanie aplikacji do Microsoft Managed Desktop sieci Web

Możesz dodać [aplikacje systemu Win32 lub](#lob-apps) Windows oparte na Microsoft Store dla Firm MSI w aplikacji Microsoft Managed Desktop, a [](#msfb-apps) następnie wdrożyć je na Microsoft Managed Desktop urządzeniach.

<span id="lob-apps">

### <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>Win32 lub Windows oparte na msI do Microsoft Managed Desktop

Aplikacje biznesowe (LOB) możesz dodać do portalu Microsoft Managed Desktop biznesowego. Aby uzyskać informacje o wymaganiach dotyczących aplikacji zainstalowanych Microsoft Managed Desktop urządzeniach, [zobacz Microsoft Managed Desktop wymagań aplikacji](../service-description/mmd-app-requirements.md).

W tej procedurze wybierzesz rodzaj aplikacji, którą chcesz dodać, a następnie skonfigurujesz i przekażesz źródło aplikacji.

**Aby dodać aplikację LOB lub aplikację Windows do Microsoft Managed Desktop aplikacji:**

Możesz zalogować się do portalu Microsoft Managed Desktop lub zalogować się w usłudze Intune, a następnie wyszukać Microsoft Managed Desktop. Logowanie się do portalu Microsoft Managed Desktop pokażemy poniżej:

1. Zaloguj się do [Microsoft Managed Desktop administratora](https://aka.ms/mmdportal).
2. W **obszarze Spis** wybierz pozycję **Aplikacje**.
3. W sekcji Obciążenie pracą aplikacji wybierz pozycję **Dodaj**.
4. W **daniu aplikacji** wybierz **pozycję Aplikacja biznesowa** lub Windows **aplikacji (Win32)**.
    - Jeśli wybrano aplikację biznesową **, zobacz** Dodawanie aplikacji biznesowej Windows do usługi [Microsoft Intune](/intune/lob-apps-windows), aby uzyskać instrukcje dotyczące dodawania i konfigurowania aplikacji biznesowych.
    - Jeśli wybrano **aplikację Windows (Win32),** zobacz Zarządzanie aplikacjami [Win32](/intune/apps-win32-app-management), aby uzyskać instrukcje dotyczące dodawania i konfigurowania Windows aplikacji.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>Microsoft Store dla Firm aplikacji

Jeśli jeszcze tego nie zrobić, możesz Microsoft Store dla Firm, gdy znajdziesz aplikacje. Po wymuseniu aplikacji możesz je zsynchronizować z usługą Microsoft Managed Desktop.

**Aby kupić aplikacje z Microsoft Store dla Firm:**

1. Zaloguj się, [Microsoft Store dla Firm](https://businessstore.microsoft.com) za pomocą Microsoft Store dla Firm administratora.
2. Wybierz **pozycję Kup dla mojej grupy**.
3. Użyj funkcji wyszukiwania, aby znaleźć aplikację, której chcesz użyć, a następnie wybierz ją.
4. W szczegółach produktu wybierz **pozycję Pobierz aplikację**.
Microsoft Store dodaje aplikację do **twoich produktów** organizacji.

**Aby sprawdzić, czy synchronizacja między usługą Intune a usługą Microsoft Store dla Firm jest aktywna:**

1. Zaloguj się, [Microsoft Store dla Firm](https://businessstore.microsoft.com) za pomocą Microsoft Store dla Firm administratora.
2. Wybierz **pozycję Zarządzaj**.
3. Wybierz **Ustawienia**, a następnie wybierz pozycję **Rozpowszechnij**.
4. W **obszarze Narzędzia do** zarządzania sprawdź, czy usługa Intune znajduje się na liście i czy ma stan **Aktywny**.  

**Aby wymusić synchronizację między usługą Intune a usługą Microsoft Store dla Firm:**

1. Zaloguj się do [centrum administracyjnego programu Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Wybierz **pozycję Administracja dzierżawą** , **następnie Łączniki i tokeny**, **a następnie wybierz Microsoft Store dla Firm**.
3. Wybierz **pozycję Włączone** dla **opcji Microsoft Store dla Firm synchronizacji pozwala uzyskać dostęp do aplikacji kupionych woluminowo w usłudze Intune.**
4. Wybierz preferowany język, a następnie **wybierz pozycję** Synchronizuj, aby pobrać aplikacje kupione w chmurze Microsoft Store Intune.

<span id="2" />

## <a name="step-2-create-azure-ad-groups"></a>Krok 2. Tworzenie grup usługi Azure AD

Utwórz trzy grupy usługi Azure AD dla każdej aplikacji. W poniższej tabeli przedstawiono potrzebne grupy (Dostępne, Wymagane i Odinstaluj).

Typ zadania aplikacji | Korzystanie z grup | Przykładowa nazwa usługi Azure AD |
--- | --- | --- |
Dostępna |  Aplikacja będzie dostępna z Portal firmy lub witryny internetowej. | MMD — *nazwa aplikacji —* dostępne |
Wymagany |  Aplikacja jest instalowana na urządzeniach w wybranych grupach. | MMD — *nazwa aplikacji —* wymagane |
Odinstalowanie |  Aplikacja zostanie odinstalowana z urządzeń w wybranych grupach. | MMD — *nazwa aplikacji —* Odinstaluj |

Dodaj użytkowników do tych grup, aby:

- Udostępnij aplikację
- Zainstaluj aplikację lub
- Usuń aplikację z urządzenia Microsoft Managed Desktop urządzenia.

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>Krok 3. Przypisywanie aplikacji do użytkowników

**Aby przypisać aplikację do użytkowników:**

1. Zaloguj się do [Microsoft Managed Desktop administratora](https://aka.ms/mmdportal).
2. W okienku Zarządzany pulpit wybierz pozycję **Aplikacje**.
3. W sekcji Obciążenie pracą aplikacji wybierz aplikację, do której chcesz przypisać użytkowników, a następnie wybierz pozycję **Przypisz grupy użytkowników**.
4. W przypadku konkretnej aplikacji wybierz typ zadania (Dostępny, Wymagany, Odinstaluj) i przypisz odpowiednią grupę.
5. W okienku Przypisywanie aplikacji wybierz przycisk **OK**.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Procedura rozpoczynania pracy z Microsoft Managed Desktop

1. Portalu [administracyjnego programu](access-admin-portal.md) Access.
1. [Dodaj i zweryfikuj kontakty administratora w portalu administracyjnym](add-admin-contacts.md).
1. [Dostosuj ustawienia po rejestracji](conditional-access.md).
1. Wdrażanie i [przypisywanie Intune — Portal firmy](company-portal.md).
1. [Przypisywanie licencji](assign-licenses.md).
1. Wdrażanie aplikacji (ten artykuł).
1. [Konfigurowanie urządzeń](set-up-devices.md).
1. Skonfiguruj środowisko [pierwszego uruchomienia za pomocą rozwiązania Autopilot i strony stanu rejestracji](esp-first-run.md).
1. [Włączanie funkcji pomocy technicznej dla użytkowników](enable-support.md).
1. [Przygotuj użytkowników do korzystania z urządzeń](get-started-devices.md).
1. [Wprowadzenie do sterowania aplikacją](get-started-app-control.md).

<!--# Preparing apps for Microsoft Managed Desktop

This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.

-->
