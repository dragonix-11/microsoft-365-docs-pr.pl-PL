---
title: Microsoft Defender for Identity wykluczeń wykrywania w Microsoft 365 Defender
description: Dowiedz się, jak skonfigurować Microsoft Defender for Identity wykrywania w Microsoft 365 Defender.
ms.date: 11/02/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e2df92e44b323bd0555407d72ebd48a7e050c9a5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473920"
---
# <a name="configure-defender-for-identity-detection-exclusions-in-microsoft-365-defender"></a>Konfigurowanie usługi Defender pod celu wykrywania wykluczeń tożsamości w Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak [konfigurować](/defender-for-identity) Microsoft Defender for Identity wykrywania [w Microsoft 365 Defender.](/microsoft-365/security/defender/overview-security-center)

> [!IMPORTANT]
> W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

[!INCLUDE [Product long](includes/product-long.md)] umożliwia wyłączenie określonych adresów IP, komputerów, domen lub użytkowników z szeregu wykryciy.

Na przykład **alert rekonesansu DNS** może zostać wyzwolony przez skaner zabezpieczeń, który używa systemu DNS jako mechanizmu skanowania. Utworzenie wykluczenia pomaga w ignorowania takich skanerów przez defender for Identity i zmniejszaniu wyników fałszywie dodatnich.

>[!NOTE]
>W przypadku najpopularniejszych domen z otwartą podejrzaną komunikacją przez [alerty DNS](/defender-for-identity/exfiltration-alerts#suspicious-communication-over-dns-external-id-2031) obserwowaliśmy domeny wykluczonych przez klientów najczęstszą z alertów. Te domeny są domyślnie dodawane do listy wykluczeń, ale możesz je łatwo usunąć.

## <a name="how-to-add-detection-exclusions"></a>Jak dodać wykluczenia wykrywania

1. Na [Microsoft 365 Defender](https://security.microsoft.com/) **przejdź do Ustawienia** i **Tożsamości**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Opcja Tożsamości w kolumnie Nazwa" lightbox="../../media/defender-identity/settings-identities.png":::

1. W menu po lewej  stronie zobaczysz pozycję Wykluczone jednostki.

   :::image type="content" source="../../media/defender-identity/excluded-entities.png" alt-text="Okienko Excluded entities (Wykluczone jednostki)" lightbox="../../media/defender-identity/excluded-entities.png":::

Wykluczenia można następnie ustawić za pomocą dwóch metod: Wykluczenia z reguły **wykrywania** i jednostek **wykluczonych globalnie**.

## <a name="exclusions-by-detection-rule"></a>Wykluczenia z reguły wykrywania

1. W menu po lewej stronie wybierz pozycję **Wykluczenia z reguły wykrywania**. Zostanie wyświetlona lista reguł wykrywania.

   :::image type="content" source="../../media/defender-identity/exclusions-by-detection-rule.png" alt-text="Opcja Wykluczenia według reguły wykrywania w pozycji Wykluczone jednostki w okienku po lewej stronie" lightbox="../../media/defender-identity/exclusions-by-detection-rule.png":::

1. Dla każdego wykrywania, który chcesz skonfigurować, wykonaj następujące czynności:

    1. Zaznacz regułę. Wykrywanie można wyszukiwać za pomocą paska wyszukiwania. Po wybraniu tej opcji zostanie otwarte okienko ze szczegółami reguły wykrywania.

       :::image type="content" source="../../media/defender-identity/detection-rule-details.png" alt-text="Szczegóły reguły wykrywania" lightbox="../../media/defender-identity/detection-rule-details.png":::

    1. Aby dodać wykluczenie, wybierz przycisk **Wyklucz encje** , a następnie wybierz typ wykluczenia. Dla każdej reguły są dostępne różne wykluczone jednostki. Należą do nich użytkownicy, urządzenia, domeny i adresy IP. W tym przykładzie dostępne opcje to **Wyklucz urządzenia** i **Wyklucz adresy IP**.

       :::image type="content" source="../../media/defender-identity/exclude-devices-or-ip-addresses.png" alt-text="Opcja wykluczenia urządzeń lub adresów IP" lightbox="../../media/defender-identity/exclude-devices-or-ip-addresses.png":::

    1. Po wybraniu typu wykluczenia możesz dodać wykluczenie. W okienku, które zostanie otwarte, wybierz ten przycisk **+** , aby dodać wykluczenie.

       :::image type="content" source="../../media/defender-identity/add-exclusion.png" alt-text="Opcja dodania wykluczenia" lightbox="../../media/defender-identity/add-exclusion.png":::

    1. Następnie dodaj jednostkę do wykluczenia. Wybierz **pozycję + Dodaj** , aby dodać jednostkę do listy.

       :::image type="content" source="../../media/defender-identity/add-excluded-entity.png" alt-text="Opcja dodania encji do wykluczenia" lightbox="../../media/defender-identity/add-excluded-entity.png":::

    1. Następnie wybierz **pozycję Wyklucz adresy IP** (w tym przykładzie), aby zakończyć wykluczenie.

       :::image type="content" source="../../media/defender-identity/exclude-ip-addresses.png" alt-text="Opcja wyłączenia adresów IP" lightbox="../../media/defender-identity/exclude-ip-addresses.png":::

    1. Po dodaniu wykluczeń możesz wyeksportować listę lub usunąć wykluczenia, wracając do przycisku **Wyklucz encji** . W tym przykładzie zwróciliśmy do **wykluczania urządzeń**. Aby wyeksportować listę, wybierz przycisk ze strzałką w dół.

       :::image type="content" source="../../media/defender-identity/return-to-exclude-devices.png" alt-text="Opcja Wróć do wyklucz urządzeń" lightbox="../../media/defender-identity/return-to-exclude-devices.png":::

    1. Aby usunąć wykluczenie, wybierz wykluczenie i wybierz ikonę kosza.

       :::image type="content" source="../../media/defender-identity/delete-exclusion.png" alt-text="Opcja Usuń wykluczenie" lightbox="../../media/defender-identity/delete-exclusion.png":::

## <a name="global-excluded-entities"></a>Global excluded entities

Teraz możesz również konfigurować wykluczenia dla **jednostek wykluczonych globalnie**. Wykluczenia globalne umożliwiają definiowanie określonych jednostek (adresów IP, podsieci, urządzeń lub domen) w celu wykluczenia ich we wszystkich wykryciach, które ma program Defender for Identity. Jeśli więc wykluczysz urządzenie, będzie ono stosowane tylko do wykrywania, które w ramach wykrywania ma identyfikację urządzenia.

1. Z menu po lewej stronie wybierz pozycję Globalne **wykluczone jednostki**. Zobaczysz kategorie jednostek, które możesz wykluczyć.

   :::image type="content" source="../../media/defender-identity/global-excluded-entities.png" alt-text="Element podmenu Wykluczony globalnie" lightbox="../../media/defender-identity/global-excluded-entities.png":::

1. Wybierz typ wykluczenia. W tym przykładzie wybrano opcję **Wyklucz domeny**.

   :::image type="content" source="../../media/defender-identity/exclude-domains.png" alt-text="Karta Domeny" lightbox="../../media/defender-identity/exclude-domains.png":::

1. Zostanie otwarte okienko, w którym możesz dodać domenę do wykluczenia. Dodaj domenę, którą chcesz wykluczyć.

   :::image type="content" source="../../media/defender-identity/add-excluded-domain.png" alt-text="Opcja dodania domeny do wykluczenia" lightbox="../../media/defender-identity/add-excluded-domain.png":::

1. Domena zostanie dodana do listy. Wybierz **pozycję Wyklucz domeny** , aby ukończyć wykluczenie.

   :::image type="content" source="../../media/defender-identity/select-exclude-domains.png" alt-text="Opcja Wybierz domeny do wykluczenia" lightbox="../../media/defender-identity/select-exclude-domains.png":::

1. Następnie zobaczysz domenę na liście jednostek do wykluczenia ze wszystkich reguł wykrywania. Możesz wyeksportować listę lub usunąć encje, zaznaczając je i **klikając przycisk Usuń** .

   :::image type="content" source="../../media/defender-identity/global-excluded-entries-list.png" alt-text="Lista wykluczonych pozycji globalnych" lightbox="../../media/defender-identity/global-excluded-entries-list.png":::

## <a name="see-also"></a>Zobacz też

- [Zarządzanie alertami zabezpieczeń usługi Defender for Identity](manage-security-alerts.md)
