---
title: Role administratora usługi Intune w sieci centrum administracyjne platformy Microsoft 365
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
description: Role administratora są powiązane z funkcjami biznesowymi i zapewniają uprawnienia do wykonywania określonych zadań w centrum administracyjnym. Na przykład administrator usługi otwiera bilety pomocy technicznej firmy Microsoft.
ms.openlocfilehash: 650a46c20acaf207f757ebbbe8f8b7179c29158f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983671"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Role administratora usługi Intune w centrum administracyjne platformy Microsoft 365

Subskrypcja Microsoft 365 lub Office 365 zawiera zestaw ról administratora, które można przypisać użytkownikom w organizacji przy użyciu aplikacji <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a>. Każda rola administratora jest powiązana z typowymi funkcjami biznesowymi i zapewnia osobom w Twojej organizacji uprawnienia do wykonywania określonych zadań w centrum administracyjnym.

Ta centrum administracyjne platformy Microsoft 365 umożliwia zarządzanie niektórymi Microsoft Intune ról. Te role to jednak podzbiór ról dostępnych w centrum administracyjnym usługi Intune. Szukasz szczegółowych opisów ról dla Microsoft Intune? Zobacz Kontrola [dostępu oparta na rolach (RBAC, Role-based Access Control) z Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Aby uzyskać więcej informacji na temat przypisywania ról w <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">centrum administracyjne platformy Microsoft 365, zobacz</a> [Przypisywanie ról administratora](assign-admin-roles.md).

W centrum administracyjne platformy Microsoft 365 przejdź do **role, a** następnie wybierz dowolną rolę, aby otworzyć jej okienko szczegółów. Wybierz **kartę Uprawnienia** , aby wyświetlić szczegółową listę administratorów przypisanych do tej roli. Wybierz **kartę Przypisani** lub **Przypisani administratorzy** , aby dodać użytkowników do ról.

## <a name="microsoft-intune-roles-available-in-the-microsoft-365-admin-center"></a>Microsoft Intune role dostępne w centrum administracyjne platformy Microsoft 365

|Rola administratora     |Komu powinna być przypisana ta rola?  |
|---------|---------|
|Menedżer aplikacji     |   Przypisz rolę Menedżer aplikacji użytkownikom, którzy chcą dzielić cykl życia aplikacji dla aplikacji mobilnych, konfigurując aplikacje zarządzane przez zasady oraz widoki informacji o urządzeniu i profilów konfiguracji.  |
|Operator pomocy technicznej     |   Przypisz rolę operatora pomocy technicznej użytkownikom, którzy przypisują aplikacje i zasady do użytkowników i urządzeń. |
|Administrator roli w usłudze Intune    |   Przypisz administratora roli usługi Intune użytkownikom, którzy mogą przypisywać uprawnienia usługi Intune innym administratorom oraz zarządzać niestandardowymi i wbudowanymi rolami usługi Intune.   |
|Zasady i menedżer profilów     |   Przypisz rolę menedżera zasad i profilu do użytkowników, aby zarządzali zasadami zgodności, profilami konfiguracji i rejestracją firmy Apple.   |
|Operator tylko do odczytu     |   Przypisz rolę operatora tylko do odczytu użytkownikom, którzy mogą tylko wyświetlać użytkowników, urządzenia, szczegóły rejestracji i konfiguracje.   |
|Administrator szkoły     |   Przypisz rolę administratora szkoły użytkownikom w celu pełnego dostępu do zarządzania urządzeniami, Windows 10 iOS, aplikacjami i konfiguracjami w usłudze Intune for Education.   |

## <a name="delegated-administration-for-microsoft-partners"></a>Administracja delegowana dla partnerów firmy Microsoft

Jeśli pracujesz z partnerem firmy Microsoft, możesz przypisać mu role administratora. Z kolei on może przypisać użytkownikom w Twojej firmie — lub swojej — role administratora. Możesz chcieć, aby partner to zrobił, na przykład w sytuacji, gdy konfiguruje za Ciebie Twoją organizację online i zarządza nią.
  
Partner może przypisywać następujące role: 
  
- Pełna administracja, która ma uprawnienia równoważne administratorowi globalnemu z wyjątkiem zarządzania uwierzytelnianiem wieloskładnikowym za pośrednictwem Centrum partnerskiego.

- Ograniczona administracja, która ma uprawnienia równoważne administratorowi pomocy technicznej.

Zanim Partner będzie mógł przypisywać te role do użytkowników, musisz dodać go jako administratora delegowanego do swojego konta. Ten proces jest inicjowany przez autoryzowanego partnera. Musi wysłać Ci wiadomość e-mail z prośbą o nadanie uprawnień administratora delegowanego. Aby uzyskać instrukcje, zobacz [Autoryzowanie i usuwanie relacji partnerskich](../misc/add-partner.md).
  
## <a name="related-content"></a>Zawartość pokrewna

[Informacje Microsoft 365 administratora](about-admin-roles.md) (artykuł)\
[Przypisywanie ról administratora](assign-admin-roles.md) (artykuł)\
[Raporty aktywności w centrum administracyjne platformy Microsoft 365](../activity-reports/activity-reports.md) (artykuł)