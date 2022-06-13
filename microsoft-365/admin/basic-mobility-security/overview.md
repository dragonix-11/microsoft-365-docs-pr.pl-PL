---
title: Omówienie pakietu Basic Mobility and Security dla Microsoft 365
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
- AdminTemplateSet
search.appverid:
- MET150
description: Zarządzaj urządzeniami przenośnymi połączonymi z organizacją Microsoft 365 i zabezpieczaj je, konfigurując i korzystając z pakietu Basic Mobility and Security.
ms.openlocfilehash: 15f9c1f64f43c57de41082962bfc1741b40aa0dd
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042237"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Omówienie pakietu Basic Mobility and Security dla Microsoft 365

Urządzeniami przenośnymi można zarządzać i zabezpieczać je po nawiązaniu połączenia z organizacją Microsoft 365 przy użyciu pakietu Basic Mobility and Security. Urządzenia przenośne, takie jak smartfony i tablety, które są używane do uzyskiwania dostępu do służbowej poczty e-mail, kalendarza, kontaktów i dokumentów, odgrywają znaczącą rolę w zapewnieniu, że pracownicy wykonują swoją pracę w dowolnym czasie i z dowolnego miejsca. Dlatego ważne jest, aby chronić informacje organizacji, gdy użytkownicy korzystają z urządzeń. Usługa Basic Mobility and Security umożliwia ustawianie zasad zabezpieczeń urządzeń i reguł dostępu oraz czyszczenie urządzeń przenośnych w przypadku ich utraty lub kradzieży.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Konfiguracja pakietu Basic Mobility and Security.":::

## <a name="what-types-of-devices-can-you-manage"></a>Jakimi typami urządzeń można zarządzać?

Usługa Basic Mobility and Security umożliwia zarządzanie wieloma typami urządzeń przenośnych, takimi jak Android, iPhone i iPad. Aby zarządzać urządzeniami przenośnymi używanymi przez osoby w organizacji, każda osoba musi mieć odpowiednią licencję Microsoft 365, a jej urządzenie musi być zarejestrowane w usłudze Basic Mobility and Security.

Aby zobaczyć, co usługa Basic Mobility and Security obsługuje dla każdego typu urządzenia, zobacz [Możliwości usługi Basic Mobility and Security](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Kroki konfiguracji dla pakietu Basic Mobility and Security

Administrator globalny Microsoft 365 musi wykonać następujące kroki, aby aktywować i skonfigurować pakiet Basic Mobility and Security. Aby uzyskać szczegółowe instrukcje, postępuj zgodnie ze wskazówkami w [temacie Konfigurowanie pakietu Basic Mobility and Security](set-up.md). 

Oto podsumowanie kroków:

**Krok 1:** Aktywuj pakiet Basic Mobility and Security, wykonując kroki opisane w [temacie Konfigurowanie pakietu Basic Mobility and Security](set-up.md).

**Krok 2:** Skonfiguruj usługę Basic Mobility and Security, na przykład tworząc certyfikat usługi APNs do zarządzania urządzeniami iOS i dodając rekord DNS (Domain Name System) dla domeny.

**Krok 3.** Utwórz zasady urządzeń i zastosuj je do grup użytkowników. Gdy to zrobisz, użytkownicy otrzymają komunikat o rejestracji na swoim urządzeniu, a po zakończeniu rejestracji ich urządzenia będą ograniczone przez skonfigurowane dla nich zasady. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego przy użyciu pakietu Basic Mobility and Security](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Podstawowe ustawienia zasad zabezpieczeń i mobilności.":::

## <a name="device-management-tasks"></a>Zadania zarządzania urządzeniami

Po skonfigurowaniu pakietu Basic Mobility and Security i zarejestrowaniu urządzeń przez użytkowników można zarządzać urządzeniami, blokować dostęp lub czyścić urządzenie, jeśli to konieczne. Aby dowiedzieć się więcej o niektórych typowych zadaniach zarządzania urządzeniami, w tym o tym, gdzie wykonywać zadania, zobacz [Zarządzanie urządzeniami zarejestrowanymi w usłudze Mobile Zarządzanie urządzeniami dla Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Inne sposoby zarządzania urządzeniami i aplikacjami

Jeśli potrzebujesz tylko zarządzania aplikacjami mobilnymi (MAM), być może dla osób aktualizujących projekty służbowe na własnych urządzeniach, Intune oferuje inną opcję oprócz rejestrowania urządzeń i zarządzania nimi. Subskrypcja Intune umożliwia konfigurowanie zasad zarządzania aplikacjami mobilnymi przy użyciu Azure Portal, nawet jeśli urządzenia osób nie są zarejestrowane w Intune. Aby uzyskać więcej informacji, zobacz [omówienie zasad Ochrona aplikacji](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>Zawartość pokrewna

[Konfigurowanie pakietu Basic Mobility and Security](set-up.md) (artykuł)\
[Rejestrowanie urządzenia przenośnego przy użyciu pakietu Basic Mobility and Security](enroll-your-mobile-device.md) (artykuł)\
[Zarządzanie urządzeniami zarejestrowanymi w usłudze Mobile Zarządzanie urządzeniami dla Microsoft 365](manage-enrolled-devices.md) (artykuł)\
[Uzyskiwanie szczegółowych informacji o urządzeniach zarządzanych przez usługę Basic Mobility and Security](get-details-about-managed-devices.md) (artykuł)
