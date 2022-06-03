---
title: Wyłącz funkcję Podstawowa mobilność i zabezpieczenia
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
description: Usuń grupy lub zasady, aby wyłączyć pakiety Basic Mobility and Security.
ms.openlocfilehash: 59a54b9969bf16c7523a6862c6f0960bb1527e8a
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863037"
---
# <a name="turn-off-basic-mobility-and-security"></a>Wyłącz funkcję Podstawowa mobilność i zabezpieczenia

Aby skutecznie wyłączyć usługę Basic Mobility and Security, należy usunąć grupy osób zdefiniowanych przez grupy zabezpieczeń z zasad zarządzania urządzeniami lub usunąć same zasady.

- Usuń grupy użytkowników, usuwając grupy zabezpieczeń użytkowników z utworzonych zasad urządzeń.

- Wyłącz opcję Podstawowa mobilność i zabezpieczenia dla wszystkich użytkowników, usuwając wszystkie zasady urządzeń w warstwie Podstawowa mobilność i zabezpieczenia.

Te opcje usuwają wymuszanie usługi Basic Mobility and Security dla urządzeń w organizacji. Niestety nie można po prostu "anulować aprowizacji" pakietu Basic Mobility and Security po jego skonfigurowaniu.

> [!IMPORTANT]
> Należy pamiętać o wpływie na urządzenia użytkowników podczas usuwania grup zabezpieczeń użytkowników z zasad lub usuwania samych zasad. Na przykład profile poczty e-mail i buforowane wiadomości e-mail mogą zostać usunięte w zależności od urządzenia. Aby uzyskać więcej informacji, zobacz [Co się stanie po usunięciu zasad lub usunięciu użytkownika z zasad?](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Usuwanie grup zabezpieczeń użytkowników z zasad urządzeń usługi Basic Mobility and Security

1. W przeglądarce wpisz: [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Wybierz zasady urządzenia, a następnie wybierz pozycję **Edytuj zasady**.

3. Na stronie **Wdrożenie** wybierz pozycję **Usuń**.

4. W obszarze **Grupy** wybierz grupę zabezpieczeń.

5. Wybierz pozycję **Usuń**, a następnie wybierz pozycję **Zapisz**.

## <a name="remove-basic-mobility-and-security-device-policies"></a>Usuwanie zasad urządzeń w warstwie Podstawowa mobilność i zabezpieczenia

1. W przeglądarce wpisz: [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Wybierz zasady urządzenia, a następnie wybierz pozycję **Usuń zasady**.

3. W oknie dialogowym Ostrzeżenie wybierz pozycję **Tak**.

> [!NOTE]
> Aby uzyskać więcej kroków odblokowania urządzeń, jeśli urządzenia organizacji są nadal w stanie zablokowanym, zobacz wpis w blogu [Usuwanie Access Control z Zarządzanie urządzeniami przenośnymi dla Office 365](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
