---
title: Tagi encji usługi Microsoft Defender dla tożsamości w programie Microsoft 365 Defender
description: Dowiedz się, jak stosować tagi encji usługi Microsoft Defender dla tożsamości w Microsoft 365 Defender
ms.date: 06/08/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 1d589f2eb34a66dda47532394b987bd4b00b86bf
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683280"
---
# <a name="defender-for-identity-entity-tags-in-microsoft-365-defender"></a>Tagi jednostki tożsamości usługi Defender w programie Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak stosować [tagi encji tożsamości usługi Microsoft Defender](/defender-for-identity) [w Microsoft 365 Defender.](/microsoft-365/security/defender/overview-security-center)

>[!IMPORTANT]
>W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

## <a name="entity-tags"></a>Tagi encji

W Microsoft 365 Defender można ustawić trzy typy tagów encji tożsamości usługi **Defender: tagi** poufne, tagi **Honeytoken** i Exchange **serwera**.

Aby ustawić te tagi, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">na Microsoft 365 Defender</a> przejdź **do Ustawienia i** **Tożsamości**.

![Przejdź do Ustawienia, a następnie do identities.](../../media/defender-identity/settings-identities.png)

Ustawienia tagów zostaną wyświetlone w obszarze **Tagi encji**.

![Typy ustawień tagów.](../../media/defender-identity/tag-settings.png)

Aby ustawić każdy typ tagu, postępuj zgodnie z poniższymi instrukcjami.

## <a name="sensitive--tags"></a>Tagi poufne

Tag **Sensitive służy** do identyfikowania zasobów o wysokiej wartości. Ścieżka ruchu bocznego również zależy od stanu wrażliwości encji. Niektóre jednostki są automatycznie traktowane jako poufne przez program Defender dla tożsamości. Aby uzyskać listę tych środków trwałych, zobacz [Poufne jednostki](/defender-for-identity/manage-sensitive-honeytoken-accounts#sensitive-entities).

Możesz również ręcznie otagować użytkowników, urządzenia lub grupy jako poufne.

1. Wybierz **pozycję Poufne**. Pojawi się istniejący poufny obszar **Użytkownicy**, **Urządzenia** i **Grupy**.

    ![Poufne jednostki.](../../media/defender-identity/sensitive-entities.png)

1. W obszarze każdej kategorii wybierz **pozycję Tag...** , aby otagować ten typ encji. Na przykład w obszarze **Grupy** wybierz pozycję **Grupy znaczników.** Zostanie otwarte okienko z grupami, które możesz oznaczyć. Aby wyszukać grupę, wprowadź jej nazwę w polu wyszukiwania.

    ![Dodaj grupy.](../../media/defender-identity/add-groups.png)

1. Zaznacz grupę i kliknij pozycję **Dodaj zaznaczenie.**

    ![Dodawanie zaznaczenia.](../../media/defender-identity/add-selection.png)

## <a name="honeytoken-tags"></a>Tagi Honeytoken

Jednostki Honeytoken są używane jako groty złośliwych szpadów. Każde uwierzytelnianie skojarzone z tymi jednostkami honeytoken powoduje wyzwolenie alertu.

Użytkownicy lub urządzenia za pomocą tagu **Honeytoken** można oznaczać tak samo jak poufne konta.

1. Wybierz **pozycję Honeytoken**. Zobaczysz istniejących użytkowników i urządzeń korzystających z  poszczegłonia.

    ![Jednostki Honeytoken.](../../media/defender-identity/honeytoken-entities.png)

1. W obszarze każdej kategorii wybierz **pozycję Tag...** , aby otagować ten typ encji. Na przykład w obszarze **Użytkownicy** wybierz pozycję **Otaguj użytkowników.** Zostanie otwarte okienko z grupami, które możesz oznaczyć. Aby wyszukać grupę, wprowadź jej nazwę w polu wyszukiwania.

    ![Dodaj użytkowników.](../../media/defender-identity/add-users.png)

1. Wybierz użytkownika i kliknij pozycję **Dodaj zaznaczenie.**

    ![Dodaj wybranego użytkownika.](../../media/defender-identity/add-selected-user.png)

## <a name="exchange-server-tags"></a>Exchange tagów serwera

Program Defender for Identity uznaje Exchange jako zasoby o wysokiej wartości i automatycznie oznacza je jako **poufne**. Możesz także ręcznie otagować urządzenia jako Exchange serwerach.

1. Wybierz **Exchange serwera**. Następnie zobaczysz istniejące urządzenia z etykietą Exchange **serwera**.

    ![Exchange serwerach.](../../media/defender-identity/exchange-servers.png)

1. Aby otagować urządzenie jako serwer Exchange, wybierz pozycję **Urządzenia tagów**.  Zostanie otwarte okienko z urządzeniami, które możesz oznaczyć. Aby wyszukać urządzenie, wprowadź jego nazwę w polu wyszukiwania.

    ![Dodaj urządzenia.](../../media/defender-identity/add-devices.png)

1. Wybierz urządzenie i kliknij pozycję **Dodaj zaznaczenie.**

    ![Wybierz urządzenie.](../../media/defender-identity/select-device.png)

## <a name="see-also"></a>Zobacz też

- [Zarządzanie alertami zabezpieczeń usługi Defender for Identity](manage-security-alerts.md)
