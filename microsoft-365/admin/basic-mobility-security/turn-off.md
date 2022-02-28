---
title: Wyłączanie mobilności podstawowej i zabezpieczeń
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Usuń grupy lub zasady, aby wyłączyć pakiet Basic Mobility and Security.
ms.openlocfilehash: ff3fe72e1ca3a6445aa29ac18404aae139a70f8a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983924"
---
# <a name="turn-off-basic-mobility-and-security"></a>Wyłączanie mobilności podstawowej i zabezpieczeń

Aby skutecznie wyłączyć podstawową mobilność i zabezpieczenia, należy usunąć grupy osób zdefiniowane przez grupy zabezpieczeń z zasad zarządzania urządzeniami lub usunąć same zasady.

- Usuń grupy użytkowników, usuwając grupy zabezpieczeń użytkowników z utworzonych zasad urządzenia.

- Wyłącz podstawową mobilność i zabezpieczenia dla wszystkich użytkowników, usuwając wszystkie zasady dotyczące mobilności podstawowej i zabezpieczeń.

Te opcje usuwają wymuszanie mobilności podstawowej i zabezpieczeń dla urządzeń w Twojej organizacji. Niestety, po jej skonfigurowaniu nie można po prostu "odblokować" pakietu Basic Mobility and Security.

> [!IMPORTANT]
> Podczas usuwania grup zabezpieczeń użytkowników z zasad lub usuwania samych zasad należy pamiętać o wpływie na urządzenia użytkowników. Na przykład w zależności od urządzenia profile poczty e-mail i buforowane wiadomości e-mail mogą zostać usunięte. Aby uzyskać więcej informacji, zobaczCo się dzieje w przypadku usunięcia   [zasad lub usunięcia użytkownika z zasad?](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Usuwanie grup zabezpieczeń użytkowników z zasad pakietu Basic Mobility i urządzeń zabezpieczających

1. W przeglądarce wpisz: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Wybierz zasady urządzenia, a następnie wybierz pozycję **Edytuj zasady**.

3. Na stronie  **Wdrażanie**  wybierz pozycję **Usuń**.

4. W   **obszarze Grupy** wybierz grupę zabezpieczeń.

5. Wybierz  **pozycję Usuń**, a następnie wybierz **pozycję Zapisz**.

## <a name="remove-basic-mobility-and-security-device-policies"></a>Usuwanie zasad dostępu podstawowego do urządzeń mobilnych i zabezpieczeń

1. W przeglądarce wpisz: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Wybierz zasady urządzenia, a następnie wybierz pozycję  **Usuń zasady**.

3. W oknie dialogowym Ostrzeżenie wybierz pozycję **Tak**.

> [!NOTE]
> Aby uzyskać więcej kroków odblokowywania urządzeń, jeśli urządzenia Twojej organizacji nadal znajdują się w stanie zablokowanym, zobacz wpis w blogu Usuwanie kontroli dostępu z aplikacji [Zarządzanie urządzeniami przenośnymi dla Office 365](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
