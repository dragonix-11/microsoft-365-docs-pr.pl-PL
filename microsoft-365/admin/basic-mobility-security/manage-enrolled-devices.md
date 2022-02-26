---
title: Zarządzanie urządzeniami zarejestrowanymi w usłudze Zarządzanie urządzeniami przenośnymi w Microsoft 365
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
description: Podstawowa mobilność i zabezpieczenia mogą ułatwić zabezpieczanie urządzeń przenośnych organizacji i zarządzanie nimi.
ms.openlocfilehash: 152b4cc33fab740516d7138cca8f4a15096c8312
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973641"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Zarządzanie urządzeniami zarejestrowanymi w usłudze Zarządzanie urządzeniami przenośnymi w Microsoft 365

Wbudowane zarządzanie urządzeniami przenośnymi dla aplikacji Microsoft 365 ułatwia zabezpieczanie urządzeń przenośnych użytkowników, takich jak telefony iPhone, tablety iPad, urządzenia z systemem Android Windows telefony. Pierwszym krokiem jest zalogowanie się w celu Microsoft 365 skonfigurowania mobilności podstawowej i zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Konfigurowanie mobilności podstawowej i zabezpieczeń](set-up.md).

Po jej skonfigurowaniu osoby w Twojej organizacji muszą zarejestrować swoje urządzenia w usłudze. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego za pomocą platformy Basic Mobility and Security](enroll-your-mobile-device.md).Następnie możesz używać funkcji Basic Mobility i Security, aby ułatwić zarządzanie urządzeniami w Twojej organizacji. Na przykład za pomocą zasad zabezpieczeń urządzeń możesz ograniczyć dostęp do poczty e-mail lub inne usługi, wyświetlać raporty dotyczące urządzeń i zdalnie wyczyścić urządzenie. Aby wykonać te zadania, zwykle należy przejść & Centrum zgodności zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Centrum zgodności platformy Microsoft 365](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Zadania związane z zarządzaniem urządzeniami

Aby uzyskać dostęp do panelu zarządzania urządzeniami, wykonaj następujące czynności:

1. Przejdź do  [centrum administracyjne platformy Microsoft 365](../../admin/admin-overview/about-the-admin-center.md).

2. Wpisz Zarządzanie urządzeniami przenośnymi w polu wyszukiwania i wybierz pozycję **Zarządzanie**  urządzeniami przenośnymi z listy wyników.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Opcja zarządzania urządzeniami przenośnymi.":::

3. Wybierz   **Pozycję Wprowadzenie**.

## <a name="manage-mobile-devices"></a>Zarządzanie urządzeniami przenośnymi

Po skonfigurowaniu mobilności podstawowej i zabezpieczeń możesz zarządzać urządzeniami przenośnymi w swojej organizacji na kilka sposobów.

|**W tym celu**|**Wykonaj te**|
|:----------------|:------------------------------------------------------------------------------|
|Czyszczenie urządzenia |W panelu Zarządzanie urządzeniami wybierz nazwę  *urządzenia, a* następnie Wyczyść pole wyboru, aby usunąć wszystkie informacje,  ****    ****  lub wyczyść zaznaczenie, aby usunąć na urządzeniu tylko informacje organizacyjne. Aby uzyskać więcej informacji, zobacz [Czyszczenie urządzenia przenośnego w pakietach Basic Mobility and Security](wipe-mobile-device.md).|
|Blokowanie nieobsługiwanych urządzeń z dostępem do poczty Exchange e-mail przy użyciu Exchange ActiveSync |W panelu Zarządzanie urządzeniami wybierz   **pozycjęBlock**. |
|Konfigurowanie zasad dotyczących urządzeń, takich jak wymagania dotyczące haseł i ustawienia zabezpieczeń |W panelu Zarządzanie urządzeniami wybierz pozycję **Zasady zabezpieczeń**  **urządzeńDdd** > +. Aby uzyskać więcej informacji,  [zobaczTworzenie zasad zabezpieczeń urządzeń w mobilności podstawowej i zabezpieczeniach](create-device-security-policies.md).|
|Wyświetlanie listy zablokowanych urządzeń  |W panelu Zarządzanie urządzeniami w obszarze   **Wybierz widok wybierz**    **pozycjęBlokowane**. |
|Odblokowywanie nieuzupełniającego lub nieobsługiwanego urządzenia dla użytkownika lub grupy użytkowników  |Aby odblokować urządzenia, wybierz jedną z następujących czynności:<br/>— usunąć użytkownika lub użytkowników z grupy zabezpieczeń, do których zastosowano zasady. Przejdź do centrum administracyjne platformy Microsoft 365 > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a>, a następnie wybierz nazwę grupy. Wybierz **pozycję Edytuj członków i administratorów**.<br/>— usunąć grupę zabezpieczeń, do których należy użytkownik, z zasad urządzenia. Przejdź do centrum zabezpieczeń & zgodności i > **zabezpieczeń Zasady** >  **zabezpieczeńUsuń zasady zabezpieczeń**. Wybierz nazwę zasad urządzenia, a następnie wybierz **pozycję** **EdytujDeployment** > .<br/>— Odblokować wszystkie urządzenia nieuprawniające na zasadach urządzenia. Przejdź do centrum zabezpieczeń & zgodności i > **zabezpieczeń Zasady** >  **zabezpieczeńUsuń zasady zabezpieczeń**. Wybierz nazwę zasad urządzenia, a następnie wybierz **pozycję Wymagania dotyczące funkcji EditAccess** >. **** Wybierz  **pozycję Zezwalaj na dostęp i naruszenie raportu**.<br/>— Aby odblokować nieuzupełnione lub nieobsługiwane urządzenie dla użytkownika lub grupy użytkowników, przejdź do Centrum zabezpieczeń & zgodności > ****  **** >> Zasady zabezpieczeń Zarządzanie urządzeniamiUrządzyanie ustawieniami dostępu do  **urządzenia**. Dodaj grupę zabezpieczeń z członkami, których chcesz wykluczyć z możliwości zablokowania dostępu do Microsoft 365. Aby uzyskać więcej informacji, [zobacz Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń w centrum administracyjne platformy Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).|
|Usuń użytkowników, aby ich urządzenia nie są już zarządzane przez pakiet Basic Mobility and Security |Aby usunąć użytkownika, edytuj grupę zabezpieczeń, która ma zasady zarządzania urządzeniami w zakresie mobilności podstawowej i zabezpieczeń. Aby uzyskać więcej informacji,   [zobaczTwoz, edytuj lub usuń grupę zabezpieczeń w](../../admin/email/create-edit-or-delete-a-security-group.md) centrum administracyjne platformy Microsoft 365.<br/>Aby usunąć pakiet Basic Mobility and Security ze wszystkich użytkowników pakietu Microsoft 365, zobacz [Wyłączanie mobilności podstawowej i zabezpieczeń](turn-off.md).|

Live (w wersji 14)