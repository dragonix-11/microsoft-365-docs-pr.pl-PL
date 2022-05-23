---
title: Informacje o rolach administratora Intune w Centrum administracyjne platformy Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
description: Centrum administracyjne platformy Microsoft 365 umożliwia zarządzanie niektórymi rolami Microsoft Intune, które są mapowane na funkcje biznesowe i dają uprawnienia do wykonywania określonych zadań.
ms.openlocfilehash: 61c73ea49b132dee12839112bdc08624a750989f
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636267"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Intune role administratora w Centrum administracyjne platformy Microsoft 365

Subskrypcja Microsoft 365 lub Office 365 zawiera zestaw ról administratora, które można przypisać do użytkowników w organizacji przy użyciu <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Każda rola administratora jest powiązana z typowymi funkcjami biznesowymi i zapewnia osobom w Twojej organizacji uprawnienia do wykonywania określonych zadań w centrum administracyjnym.

Centrum administracyjne platformy Microsoft 365 umożliwia zarządzanie niektórymi rolami Microsoft Intune. Jednak te role są podzbiorem ról dostępnych w centrum administracyjnym Intune. Szukasz szczegółowych opisów ról dla Microsoft Intune? Zapoznaj się z [kontrolą dostępu opartą na rolach (RBAC) w usłudze Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Aby uzyskać więcej informacji na temat przypisywania ról w <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">centrum administracyjnym platformy Microsoft 365</a>, zobacz artykuł [Przypisywanie ról administratora](assign-admin-roles.md).

W Centrum administracyjne platformy Microsoft 365 możesz przejść do pozycji **Role**, a następnie wybrać dowolną rolę, aby otworzyć okienko szczegółów. Wybierz kartę **Uprawnienia**, aby wyświetlić szczegółową listę uprawnień administratorów, którym została przypisana dana rola. Wybierz kartę **Przypisani** lub **Przypisani administratorzy**, aby dodać użytkowników do ról.

## <a name="microsoft-intune-roles-available-in-the-microsoft-365-admin-center"></a>Microsoft Intune role dostępne w Centrum administracyjne platformy Microsoft 365

|Rola administratora     |Komu powinna być przypisana ta rola?  |
|---------|---------|
|Menedżer aplikacji     |   Przypisz rolę Menedżera aplikacji do użytkowników, którzy zarządzają cyklem życia aplikacji dla aplikacji mobilnych, konfigurują aplikacje zarządzane przez zasady oraz wyświetlają informacje o urządzeniu i profile konfiguracji.  |
|Operator pomocy technicznej     |   Przypisz rolę operatora pomocy technicznej do użytkowników, którzy przypisują aplikacje i zasady do użytkowników i urządzeń. |
|administrator roli Intune    |   Przypisz administratora roli Intune użytkownikom, którzy mogą przypisywać uprawnienia Intune innym administratorom oraz zarządzać niestandardowymi i wbudowanymi rolami Intune.   |
|Menedżer zasad i profilów     |   Przypisz rolę menedżera zasad i profilów do użytkowników, którzy zarządzają zasadami zgodności, profilami konfiguracji i rejestracją firmy Apple.   |
|Operator tylko do odczytu     |   Przypisz rolę operatora tylko do odczytu użytkownikom, którzy mogą wyświetlać tylko użytkowników, urządzenia, szczegóły rejestracji i konfiguracje.   |
|Administrator szkoły     |   Przypisz użytkownikom rolę administratora szkoły w celu uzyskania pełnego dostępu do zarządzania urządzeniami, aplikacjami i konfiguracjami Windows 10 i iOS w programie Intune for Education.   |

## <a name="delegated-administration-for-microsoft-partners"></a>Administracja delegowana dla partnerów firmy Microsoft

Jeśli pracujesz z partnerem firmy Microsoft, możesz przypisać mu role administratora. Z kolei on może przypisać użytkownikom w Twojej firmie — lub swojej — role administratora. Możesz chcieć, aby to zrobili, na przykład jeśli konfigurują twoją organizację online i zarządzają tą organizacją.
  
Partner może przypisywać następujące role: 
  
- Pełna administracja, która ma uprawnienia równoważne administratorowi globalnemu, z wyjątkiem zarządzania uwierzytelnianiem wieloskładnikowym za pośrednictwem Centrum partnerskiego.

- Ograniczona administracja, która ma uprawnienia równoważne administratorowi pomocy technicznej.

Zanim partner będzie mógł przypisywać te role użytkownikom, musisz dodać tego partnera jako administratora delegowanego do swojego konta. Ten proces jest inicjowany przez partnera autoryzowanego. Partner wysyła do Ciebie wiadomość e-mail z pytaniem, czy chcesz nadać mu uprawnienia do działania jako administrator delegowany. Aby uzyskać instrukcje, zobacz [Autoryzowanie i usuwanie relacji partnerskich](../misc/add-partner.md).
  
## <a name="related-content"></a>Zawartość pokrewna

[Informacje o rolach administratora Microsoft 365](about-admin-roles.md) (artykuł)\
[Przypisywanie ról administratora](assign-admin-roles.md) (artykuł)\
[Raporty aktywności w Centrum administracyjne platformy Microsoft 365](../activity-reports/activity-reports.md) (artykuł)
