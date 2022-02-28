---
title: Omówienie mobilności podstawowej i zabezpieczeń dla Microsoft 365
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
description: Za pomocą mobilności podstawowej i zabezpieczeń skonfiguruj zasady zabezpieczeń urządzeń i reguły dostępu.
ms.openlocfilehash: 4fb1b8ca467d86259f2608af5140510a2a88b23a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983934"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Omówienie mobilności podstawowej i zabezpieczeń dla Microsoft 365

Korzystając z funkcji Basic Mobility and Security, możesz zabezpieczać urządzenia przenośne, które są połączone z Twoją Microsoft 365 twoją organizacją. Urządzenia przenośne, takie jak smartfony i tablety, które są używane do uzyskiwania dostępu do służbowej poczty e-mail, kalendarza, kontaktów i dokumentów, są bardzo ważną częścią zapewniania pracownikom wykonanej pracy w dowolnym czasie i z dowolnego miejsca. Dlatego bardzo ważne jest, aby chronić informacje organizacji, gdy korzystają z urządzeń. Za pomocą mobilności podstawowej i zabezpieczeń możesz ustawiać zasady zabezpieczeń urządzeń i reguły dostępu oraz czyścić urządzenia przenośne w przypadku ich zgubienia lub kradzieży.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Konfiguracja mobilności podstawowej i zabezpieczeń.":::

## <a name="what-types-of-devices-can-you-manage"></a>Jakimi typami urządzeń można zarządzać?

Za pomocą funkcji Basic Mobility and Security możesz zarządzać wieloma typami urządzeń przenośnych, takich Windows Phone, Android, iPhone i iPad. Aby zarządzać urządzeniami przenośnymi używanymi przez osoby w Twojej organizacji, każda osoba musi mieć mającą zastosowanie licencję usługi Microsoft 365, a jej urządzenie musi być zarejestrowane na stronie Podstawowa mobilność i zabezpieczenia.

Aby sprawdzić, jakie urządzenia obsługuje pakiet Basic Mobility i Zabezpieczenia, zobacz Możliwości  [pakietu Basic Mobility i zabezpieczeń](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Kroki konfigurowania dla mobilności podstawowej i zabezpieczeń

Administrator Microsoft 365 musi wykonać następujące czynności, aby aktywować i skonfigurować pakiet Basic Mobility and Security. Aby uzyskać szczegółowe instrukcje, postępuj zgodnie ze wskazówkami w [tece Konfigurowanie mobilności podstawowej i zabezpieczeń](set-up.md). 

Poniżej podsumowaliśmy kroki:

**Krok 1.** Aktywuj pakiet Basic Mobility and Security, korzystając z procedury  [w tece Jak skonfigurować podstawową mobilność i zabezpieczenia](set-up.md).

**Krok 2.** Skonfiguruj pakiet Basic Mobility and Security, na przykład tworząc certyfikat usługi APN do zarządzania urządzeniami z systemem iOS i dodając rekord systemu nazw domen (DNS) dla swojej domeny w celu obsługi Windows telefonów.

**Krok 3.** Utwórz zasady dotyczące urządzeń i zastosuj je do grup użytkowników. Gdy to zrobisz, użytkownicy otrzymają wiadomość o rejestracji na swoim urządzeniu, a po zakończeniu rejestracji ich urządzenia są ograniczone przez zasady, które dla nich skonfigurujeś. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego za pomocą platformy Basic Mobility and Security](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Ustawienia podstawowych zasad zabezpieczeń i mobilności.":::

## <a name="device-management-tasks"></a>Zadania związane z zarządzaniem urządzeniami

Po skonfigurowaniu funkcji Basic Mobility and Security i zarejestrowaniu urządzeń przez Twoich użytkowników możesz w razie potrzeby zarządzać urządzeniami, zablokować dostęp lub wyczyścić urządzenie. Aby dowiedzieć się więcej o niektórych typowych zadaniach zarządzania urządzeniami, w tym o miejscu ich wykonania, zobacz Zarządzanie urządzeniami zarejestrowanymi w usłudze Zarządzanie urządzeniami przenośnymi w [celu Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Inne sposoby zarządzania urządzeniami i aplikacjami

Jeśli potrzebujesz tylko zarządzania aplikacjami mobilnymi (MAM), być może chcesz, aby osoby aktualizujące projekty służbowe na swoich urządzeniach, usługa Intune udostępnia inną opcję oprócz rejestrowania urządzeń i zarządzania nimi. Subskrypcja usługi Intune umożliwia skonfigurowanie zasad MAM za pomocą portalu Azure Portal, nawet jeśli urządzenia innych osób nie są zarejestrowane w usłudze Intune. Aby uzyskać więcej informacji, zobacz  [Omówienie zasad ochrony aplikacji](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>Zawartość pokrewna

[Konfigurowanie mobilności podstawowej i zabezpieczeń](set-up.md) (artykuł)\
[Zarejestruj swoje urządzenie przenośne za pomocą platformy Basic Mobility and Security](enroll-your-mobile-device.md) (artykuł)\
[Zarządzanie urządzeniami zarejestrowanymi w Zarządzaniu urządzeniami przenośnymi na Microsoft 365](manage-enrolled-devices.md) (artykuł)\
[Uzyskaj szczegółowe informacje na temat urządzeń zarządzanych przez pakiet Basic Mobility and Security](get-details-about-managed-devices.md) (artykuł)