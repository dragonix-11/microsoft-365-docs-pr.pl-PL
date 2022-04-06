---
title: Konfigurowanie konta usług katalogowych w aplikacji Microsoft Defender for Identity
description: Dowiedz się, jak skonfigurować Microsoft Defender for Identity usług katalogowych w programie Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e31c226037d5d9e945350ba73e1df9abc79571e9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470004"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Microsoft Defender for Identity usług katalogowych w aplikacji Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak skonfigurować [Microsoft Defender for Identity](/defender-for-identity) usług katalogowych w aplikacji [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

## <a name="configure-directory-services-account"></a>Konfigurowanie konta usług katalogowych

Aby połączyć [czujnik z](sensor-health.md#add-a-sensor) domenami usługi Active Directory, musisz skonfigurować konta usług katalogowych.

1. Na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **przejdź do Ustawienia** i **Tożsamości**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Opcja Tożsamości na Ustawienia sieci Web" lightbox="../../media/defender-identity/settings-identities.png":::


1. Wybierz **pozycję Konta usługi katalogowej**. Zobaczysz konta skojarzone z którymi domenami.

   :::image type="content" source="../../media/defender-identity/directory-service-accounts.png" alt-text="Element menu Konta usługi katalogowej" lightbox="../../media/defender-identity/directory-service-accounts.png":::

1. Jeśli wybierzesz konto, zostanie otwarte okienko z ustawieniami tego konta.

   :::image type="content" source="../../media/defender-identity/account-settings.png" alt-text="Strona Ustawienia kont" lightbox="../../media/defender-identity/account-settings.png":::

1. Aby dodać nowe konto usług katalogowych, wybierz pozycję **Utwórz nowe konto** i wypełnij pola **Nazwa** konta, **Domena** i **Hasło**. Możesz także wybrać, czy jest to konto usługi zarządzanej przez **grupę (** gMSA) i czy należy ono do domeny **Single label**.

   :::image type="content" source="../../media/defender-identity/new-directory-service-account.png" alt-text="Opcja Utwórz nowe konto" lightbox="../../media/defender-identity/new-directory-service-account.png":::

1. Wybierz **Zapisz**.

## <a name="see-also"></a>Zobacz też

- [Microsoft Defender for Identity kondycji i ustawień czujnika](sensor-health.md)
