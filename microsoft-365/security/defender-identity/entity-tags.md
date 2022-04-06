---
title: Microsoft Defender for Identity tagów encji w Microsoft 365 Defender
description: Dowiedz się, jak Microsoft Defender for Identity tagów encji w Microsoft 365 Defender
ms.date: 06/08/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: c960f0cc1726155e733a0e88386fa7788cfc35e0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468066"
---
# <a name="defender-for-identity-entity-tags-in-microsoft-365-defender"></a>Tagi jednostki tożsamości usługi Defender w programie Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak [Microsoft Defender for Identity](/defender-for-identity) tagów [encji w Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

## <a name="entity-tags"></a>Tagi encji

W Microsoft 365 Defender można ustawić trzy typy tagów encji tożsamości usługi **Defender: tagi** poufne, tagi **Honeytoken** i Exchange **serwera**.

Aby ustawić te tagi, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">na Microsoft 365 Defender</a> przejdź **do Ustawienia i** **Tożsamości**.

:::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Opcja Tożsamości w kolumnie Nazwa na Ustawienia sieci Web" lightbox="../../media/defender-identity/settings-identities.png":::

Ustawienia tagów zostaną wyświetlone w obszarze **Tagi encji**.

:::image type="content" source="../../media/defender-identity/tag-settings.png" alt-text="Okienko Tagi encja" lightbox="../../media/defender-identity/tag-settings.png":::

Aby ustawić każdy typ tagu, postępuj zgodnie z poniższymi instrukcjami.

## <a name="sensitive--tags"></a>Tagi poufne

Tag **Sensitive służy** do identyfikowania zasobów o wysokiej wartości. Ścieżka ruchu bocznego również zależy od stanu wrażliwości encji. Niektóre jednostki są automatycznie traktowane jako poufne przez program Defender dla tożsamości. Aby uzyskać listę tych środków trwałych, zobacz [Poufne jednostki](/defender-for-identity/manage-sensitive-honeytoken-accounts#sensitive-entities).

Możesz również ręcznie otagować użytkowników, urządzenia lub grupy jako poufne.

1. Wybierz **pozycję Poufne**. Pojawi się istniejący poufny obszar **Użytkownicy**, **Urządzenia** i **Grupy**.

   :::image type="content" source="../../media/defender-identity/sensitive-entities.png" alt-text="Karta Urządzenia w pozycji menu Poufne jednostki" lightbox="../../media/defender-identity/sensitive-entities.png":::

1. W obszarze każdej kategorii wybierz **pozycję Tag...** , aby otagować ten typ encji. Na przykład w obszarze **Grupy** wybierz pozycję **Grupy znaczników.** Zostanie otwarte okienko z grupami, które możesz oznaczyć. Aby wyszukać grupę, wprowadź jej nazwę w polu wyszukiwania.

   :::image type="content" source="../../media/defender-identity/add-groups.png" alt-text="Opcja dodania grupy" lightbox="../../media/defender-identity/add-groups.png":::

1. Zaznacz grupę i kliknij pozycję **Dodaj zaznaczenie.**

   :::image type="content" source="../../media/defender-identity/add-selection.png" alt-text="Opcja Dodaj zaznaczenie" lightbox="../../media/defender-identity/add-selection.png":::

## <a name="honeytoken-tags"></a>Tagi Honeytoken

Jednostki Honeytoken są używane jako groty złośliwych szpadów. Każde uwierzytelnianie skojarzone z tymi jednostkami honeytoken powoduje wyzwolenie alertu.

Użytkownicy lub urządzenia za pomocą tagu **Honeytoken** można oznaczać tak samo jak poufne konta.

1. Wybierz **pozycję Honeytoken**. Zobaczysz istniejących użytkowników i urządzeń korzystających z  poszczegłonia.

    ![Jednostki Honeytoken.](../../media/defender-identity/honeytoken-entities.png)

1. W obszarze każdej kategorii wybierz **pozycję Tag...** , aby otagować ten typ encji. Na przykład w obszarze **Użytkownicy** wybierz pozycję **Otaguj użytkowników.** Zostanie otwarte okienko z grupami, które możesz oznaczyć. Aby wyszukać grupę, wprowadź jej nazwę w polu wyszukiwania.

   :::image type="content" source="../../media/defender-identity/add-users.png" alt-text="Opcja dodawania użytkowników" lightbox="../../media/defender-identity/add-users.png":::

1. Wybierz użytkownika i kliknij pozycję **Dodaj zaznaczenie.**

   :::image type="content" source="../../media/defender-identity/add-selected-user.png" alt-text="Opcja dodania wybranego użytkownika" lightbox="../../media/defender-identity/add-selected-user.png":::

## <a name="exchange-server-tags"></a>Exchange tagów serwera

Program Defender for Identity uznaje Exchange jako zasoby o wysokiej wartości i automatycznie oznacza je jako **poufne**. Możesz także ręcznie otagować urządzenia jako Exchange serwerach.

1. Wybierz **Exchange serwera**. Następnie zobaczysz istniejące urządzenia z etykietą Exchange **serwera**.

   :::image type="content" source="../../media/defender-identity/exchange-servers.png" alt-text="Element menu Exchange serwera" lightbox="../../media/defender-identity/exchange-servers.png":::

1. Aby otagować urządzenie jako serwer Exchange, wybierz pozycję **Urządzenia tagów**.  Zostanie otwarte okienko z urządzeniami, które możesz oznaczyć. Aby wyszukać urządzenie, wprowadź jego nazwę w polu wyszukiwania.

   :::image type="content" source="../../media/defender-identity/add-devices.png" alt-text="Opcja dodania urządzenia" lightbox="../../media/defender-identity/add-devices.png":::

1. Wybierz urządzenie i kliknij pozycję **Dodaj zaznaczenie.**

   :::image type="content" source="../../media/defender-identity/select-device.png" alt-text="Wybór urządzenia" lightbox="../../media/defender-identity/select-device.png":::

## <a name="see-also"></a>Zobacz też

- [Zarządzanie alertami zabezpieczeń usługi Defender for Identity](manage-security-alerts.md)
