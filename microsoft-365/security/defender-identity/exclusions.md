---
title: Wykluczenia wykrywania tożsamości w programie Microsoft Defender dla Microsoft 365 Defender
description: Dowiedz się, jak skonfigurować program Microsoft Defender pod celu wykrywania wykluczeń tożsamości Microsoft 365 Defender.
ms.date: 11/02/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 98ead1d0bde488cee0b35e11b477ea5fe81fe66e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683016"
---
# <a name="configure-defender-for-identity-detection-exclusions-in-microsoft-365-defender"></a>Konfigurowanie usługi Defender pod celu wykrywania wykluczeń tożsamości w Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak skonfigurować program [Microsoft Defender pod celu wykrywania](/defender-for-identity) tożsamości w innych [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

[!INCLUDE [Product long](includes/product-long.md)] umożliwia wyłączenie określonych adresów IP, komputerów, domen lub użytkowników z szeregu wykryciy.

Na przykład **alert rekonesansu DNS** może zostać wyzwolony przez skaner zabezpieczeń, który używa systemu DNS jako mechanizmu skanowania. Utworzenie wykluczenia pomaga w ignorowania takich skanerów przez defender for Identity i zmniejszaniu wyników fałszywie dodatnich.

>[!NOTE]
>W przypadku najpopularniejszych domen z otwartą podejrzaną komunikacją przez [alerty DNS](/defender-for-identity/exfiltration-alerts#suspicious-communication-over-dns-external-id-2031) obserwowaliśmy domeny wykluczonych przez klientów najczęstszą z alertów. Te domeny są domyślnie dodawane do listy wykluczeń, ale możesz je łatwo usunąć.

## <a name="how-to-add-detection-exclusions"></a>Jak dodać wykluczenia wykrywania

1. Na [Microsoft 365 Defender](https://security.microsoft.com/) **przejdź do Ustawienia** i **Tożsamości**.

    ![Przejdź do Ustawienia, a następnie do identities.](../../media/defender-identity/settings-identities.png)

1. W menu po lewej  stronie zobaczysz pozycję Wykluczone jednostki.

    ![Wykluczane jednostki.](../../media/defender-identity/excluded-entities.png)

Wykluczenia można następnie ustawić za pomocą dwóch metod: Wykluczenia z reguły **wykrywania** i jednostek **wykluczonych globalnie**.

## <a name="exclusions-by-detection-rule"></a>Wykluczenia z reguły wykrywania

1. W menu po lewej stronie wybierz pozycję **Wykluczenia z reguły wykrywania**. Zostanie wyświetlona lista reguł wykrywania.

    ![Wykluczenia z reguły wykrywania.](../../media/defender-identity/exclusions-by-detection-rule.png)

1. Dla każdego wykrywania, który chcesz skonfigurować, wykonaj następujące czynności:

    1. Zaznacz regułę. Wykrywanie można wyszukiwać za pomocą paska wyszukiwania. Po wybraniu tej opcji zostanie otwarte okienko ze szczegółami reguły wykrywania.

        ![Szczegóły reguły wykrywania.](../../media/defender-identity/detection-rule-details.png)

    1. Aby dodać wykluczenie, wybierz przycisk **Wyklucz encje** , a następnie wybierz typ wykluczenia. Dla każdej reguły są dostępne różne wykluczone jednostki. Należą do nich użytkownicy, urządzenia, domeny i adresy IP. W tym przykładzie dostępne opcje to **Wyklucz urządzenia** i **Wyklucz adresy IP**.

        ![Wyklucz urządzenia lub adresy IP.](../../media/defender-identity/exclude-devices-or-ip-addresses.png)

    1. Po wybraniu typu wykluczenia możesz dodać wykluczenie. W okienku, które zostanie otwarte, wybierz ten przycisk **+** , aby dodać wykluczenie.

        ![Dodaj wykluczenie.](../../media/defender-identity/add-exclusion.png)

    1. Następnie dodaj jednostkę do wykluczenia. Wybierz **pozycję + Dodaj** , aby dodać jednostkę do listy.

        ![Dodaj jednostkę do wykluczenia.](../../media/defender-identity/add-excluded-entity.png)

    1. Następnie wybierz **pozycję Wyklucz adresy IP** (w tym przykładzie), aby zakończyć wykluczenie.

        ![Wyklucz adresy IP.](../../media/defender-identity/exclude-ip-addresses.png)

    1. Po dodaniu wykluczeń możesz wyeksportować listę lub usunąć wykluczenia, wracając do przycisku **Wyklucz encji** . W tym przykładzie zwróciliśmy do **wykluczania urządzeń**. Aby wyeksportować listę, wybierz przycisk ze strzałką w dół.

        ![Wróć do wykluczania urządzeń.](../../media/defender-identity/return-to-exclude-devices.png)

    1. Aby usunąć wykluczenie, wybierz wykluczenie i wybierz ikonę kosza.

        ![Usuwanie wykluczenia.](../../media/defender-identity/delete-exclusion.png)

## <a name="global-excluded-entities"></a>Global excluded entities

Teraz możesz również konfigurować wykluczenia dla **jednostek wykluczonych globalnie**. Wykluczenia globalne umożliwiają definiowanie określonych jednostek (adresów IP, podsieci, urządzeń lub domen) w celu wykluczenia ich we wszystkich wykryciach, które ma program Defender for Identity. Jeśli więc wykluczysz urządzenie, będzie ono stosowane tylko do wykrywania, które w ramach wykrywania ma identyfikację urządzenia.

1. Z menu po lewej stronie wybierz pozycję Globalne **wykluczone jednostki**. Zobaczysz kategorie jednostek, które możesz wykluczyć.

    ![Globalne jednostki wykluczane.](../../media/defender-identity/global-excluded-entities.png)

1. Wybierz typ wykluczenia. W tym przykładzie wybrano opcję **Wyklucz domeny**.

    ![Wyklucz domeny.](../../media/defender-identity/exclude-domains.png)

1. Zostanie otwarte okienko, w którym możesz dodać domenę do wykluczenia. Dodaj domenę, którą chcesz wykluczyć.

    ![Dodaj domenę do wykluczenia.](../../media/defender-identity/add-excluded-domain.png)

1. Domena zostanie dodana do listy. Wybierz **pozycję Wyklucz domeny** , aby ukończyć wykluczenie.

    ![Wybierz pozycję wyklucz domeny.](../../media/defender-identity/select-exclude-domains.png)

1. Następnie zobaczysz domenę na liście jednostek do wykluczenia ze wszystkich reguł wykrywania. Możesz wyeksportować listę lub usunąć encje, zaznaczając je i **klikając przycisk Usuń** .

    ![Lista wykluczonych pozycji globalnych.](../../media/defender-identity/global-excluded-entries-list.png)

## <a name="see-also"></a>Zobacz też

- [Zarządzanie alertami zabezpieczeń usługi Defender for Identity](manage-security-alerts.md)
