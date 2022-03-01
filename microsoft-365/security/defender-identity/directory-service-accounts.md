---
title: Konfigurowanie konta usług katalogowych w usłudze Microsoft Defender dla tożsamości
description: Dowiedz się, jak skonfigurować konto usług katalogowych usługi katalogowej usługi Microsoft Defender for Identity w usłudze Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.openlocfilehash: 8928441e27215e75dc4456116c9a0e7890073852
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2021
ms.locfileid: "62999384"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Konto usług katalogowych usługi katalogowej usługi Microsoft Defender for Identity w usłudze Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak skonfigurować konto usług katalogowych [usługi katalogowej usługi Microsoft Defender dla](/defender-for-identity) tożsamości [w usłudze Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

## <a name="configure-directory-services-account"></a>Konfigurowanie konta usług katalogowych

Aby połączyć [czujnik z](sensor-health.md#add-a-sensor) domenami usługi Active Directory, musisz skonfigurować konta usług katalogowych.

1. Na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **przejdź do Ustawienia** i **Tożsamości**.

    ![Przejdź do Ustawienia, a następnie do identities.](../../media/defender-identity/settings-identities.png)

1. Wybierz **pozycję Konta usługi katalogowej**. Zobaczysz konta skojarzone z którymi domenami.

    ![konta usług katalogowych.](../../media/defender-identity/directory-service-accounts.png)

1. Jeśli wybierzesz konto, zostanie otwarte okienko z ustawieniami tego konta.

    ![Ustawienia konta.](../../media/defender-identity/account-settings.png)

1. Aby dodać nowe konto usług katalogowych, wybierz pozycję **Utwórz nowe konto** i wypełnij pola **Nazwa** konta, **Domena** i **Hasło**. Możesz także wybrać, czy jest to konto usługi zarządzanej przez **grupę (** gMSA) i czy należy ono do domeny **Single label**.

    ![Nowe konto usługi katalogowej.](../../media/defender-identity/new-directory-service-account.png)

1. Wybierz **Zapisz**.

## <a name="see-also"></a>Zobacz też

- [Kondycja i ustawienia czujnika tożsamości usługi Microsoft Defender](sensor-health.md)
