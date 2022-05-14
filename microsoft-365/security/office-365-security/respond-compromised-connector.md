---
title: Odpowiadanie na łącznik z naruszeniem zabezpieczeń w programie Microsoft 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Dowiedz się, jak rozpoznawać łącznik z naruszonymi zabezpieczeniami i reagować na nie w Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6f32f9960655c8998abd8d9fb8fa939368373520
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419020"
---
# <a name="respond-to-a-compromised-connector"></a>Reagowanie na łącznik z naruszonymi zabezpieczeniami

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**

- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Łączniki są używane do włączania przepływu poczty między serwerami Microsoft 365 lub Office 365 i poczty e-mail, które znajdują się w środowisku lokalnym. Aby uzyskać więcej informacji, zobacz [Konfigurowanie przepływu poczty przy użyciu łączników w Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

Łącznik ruchu przychodzącego, który został naruszony, jest definiowany jako wtedy, gdy nieautoryzowana osoba stosuje zmiany do istniejącego łącznika przychodzącego lub tworzy nowy łącznik przychodzący w dzierżawie Microsoft 365, z zamiarem wysyłania spamu lub fałszywych wiadomości e-mail. Należy pamiętać, że dotyczy to tylko łączników przychodzących typu OnPremises. 

## <a name="detect-a-compromised-connector"></a>Wykrywanie łącznika z naruszonymi zabezpieczeniami

Poniżej przedstawiono niektóre cechy łącznika, których zabezpieczenia zostały naruszone:

- Nagły wzrost liczby wychodzących wiadomości e-mail. 

- Niezgodność między nadawcami P1 i P2 w wychodzących wiadomościach e-mail. Aby uzyskać więcej informacji na temat nadawców P1 i P2, zobacz [How EOP validates the From address to prevent phishing (Jak funkcja EOP weryfikuje adres Od, aby zapobiec wyłudzaniu informacji](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards)).

- Wychodzące wiadomości e-mail wysyłane z domeny, która nie jest aprowizowana ani zarejestrowana. 

- Łącznik nie może wysyłać wiadomości e-mail z przekazywaniem. 

- Obecność łącznika przychodzącego nie została utworzona przez zamierzonego użytkownika ani administratora. 

- Nieautoryzowane zmiany w istniejącej konfiguracji łącznika, takie jak nazwa, nazwa domeny i adres IP. 

- Niedawno naruszone konto administratora. Pamiętaj, że konfigurację łącznika można edytować tylko wtedy, gdy masz dostęp administracyjny. 

## <a name="secure-and-restore-email-function-to-a-suspected-compromised-connector"></a>Zabezpieczanie i przywracanie funkcji poczty e-mail do podejrzanego łącznika z naruszeniem zabezpieczeń

Aby odzyskać dostęp do łącznika, musisz wykonać wszystkie poniższe kroki. Te kroki ułatwiają usunięcie wszelkich wpisów tylnych drzwi, które mogły zostać dodane do łącznika.

### <a name="step-1-identify-if-an-inbound-connector-has-been-compromised"></a>Krok 1. Określenie, czy łącznik przychodzący został naruszony 

#### <a name="review-recent-suspicious-connector-traffic-or-related-messages"></a>Przeglądanie ostatniego podejrzanego ruchu łącznika lub powiązanych komunikatów

Jeśli masz [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md), przejdź bezpośrednio do obszaru https://security.microsoft.com/threatexplorer. 

1. Wybierz pozycję **Łącznik**, wstaw **nazwę łącznika**, wybierz zakres dat, a następnie kliknij przycisk **Odśwież**. 

    :::image type="content" source="../../media/connector-compromise-explorer.png" alt-text="Widok eksploratora łączników dla ruchu przychodzącego" lightbox="../../media/connector-compromise-explorer.png":::

2. Zidentyfikuj, czy występuje nietypowy wzrost lub spadek ruchu poczty e-mail.

    :::image type="content" source="../../media/connector-compromise-abnormal-spike.png" alt-text="Liczba wiadomości e-mail dostarczonych do folderu wiadomości-śmieci" lightbox="../../media/connector-compromise-abnormal-spike.png":::

3. Identyfikacji: 

    - Jeśli **adres IP nadawcy** jest zgodny z lokalnym adresem IP organizacji. 

    - Jeśli ostatnio do folderu **Wiadomości-śmieci** wysłano znaczną liczbę wiadomości e-mail. Jest to dobry wskaźnik naruszenia zabezpieczeń łącznika używanego do wysyłania spamu. 

    - Jeśli adresaci są adresatami, z którymi organizacja zwykle pozostaje w kontakcie. 

    :::image type="content" source="../../media/connector-compromise-sender-ip.png" alt-text="Adres IP nadawcy i lokalny adres IP organizacji" lightbox="../../media/connector-compromise-sender-ip.png":::

Jeśli masz [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1](defender-for-office-365.md) lub [Exchange Online Protection](exchange-online-protection-overview.md), przejdź do .https://admin.exchange.microsoft.com/#/messagetrace 

1. Otwórz alert **dotyczący działania podejrzanego łącznika** w programie https://security.microsoft.com/alerts.  

2. Wybierz działanie w obszarze **Lista działań** i skopiuj podejrzaną **domenę łącznika** i **adres IP** wykryty w alercie.

    :::image type="content" source="../../media/connector-compromise-outbound-email-details.png" alt-text="Szczegóły wychodzącej poczty e-mail dotyczące naruszenia zabezpieczeń łącznika" lightbox="../../media/connector-compromise-outbound-email-details.png":::
    
3. Wyszukaj przy użyciu **domeny łącznika** i **adresu IP** w [**śledzenia komunikatów**](https://admin.exchange.microsoft.com/#/messagetrace). 

    :::image type="content" source="../../media/connector-compromise-new-message-trace.png" alt-text="Wysuwany nowy ślad komunikatu" lightbox="../../media/connector-compromise-new-message-trace.png":::
    
4. W wynikach wyszukiwania **śledzenia komunikatów** zidentyfikuj: 

    - Jeśli znaczna liczba wiadomości e-mail została ostatnio **oznaczona jako FilteredAsSpam**. Jest to dobry wskaźnik naruszenia zabezpieczeń łącznika używanego do wysyłania spamu. 

    - Jeśli adresaci są adresatami, z którymi organizacja zwykle pozostaje w kontakcie. 

    :::image type="content" source="../../media/connector-compromise-message-trace-results.png" alt-text="Nowe wyniki wyszukiwania śledzenia komunikatów" lightbox="../../media/connector-compromise-message-trace-results.png":::

#### <a name="investigate-and-validate-connector-related-activity"></a>Badanie i weryfikowanie działań związanych z łącznikami 

Użyj następującego wiersza polecenia w programie PowerShell, aby zbadać i zweryfikować działania związane z łącznikiem przez użytkownika w dzienniku inspekcji. Aby uzyskać więcej informacji, zobacz [Używanie skryptu programu PowerShell do przeszukiwania dziennika inspekcji](/compliance/audit-log-search-script). 

```powershell
Search-UnifiedAuditLog -StartDate "<ExDateTime>" -EndDate "<ExDateTime>" -Operations "New-InboundConnector", "Set-InboundConnector", "Remove-InboundConnector
```

### <a name="step-2-review-and-revert-unauthorized-changes-in-a-connector"></a>Krok 2. Przeglądanie i przywracanie nieautoryzowanych zmian w łączniku 

1. Zaloguj się do programu https://admin.exchange.microsoft.com/. 

2. Przejrzyj i przywróć nieautoryzowane zmiany łączników. 

### <a name="step-3-unblock-the-connector-to-re-enable-mail-flow"></a>Krok 3. Odblokuj łącznik, aby ponownie włączyć przepływ poczty 

1. Zaloguj się do programu https://security.microsoft.com/restrictedentities. 

2. Wybierz łącznik z ograniczeniami, aby odblokować łącznik. 

### <a name="step-4-investigate-and-remediate-potentially-compromised-administrative-user-account"></a>Krok 4. Badanie i korygowanie potencjalnie naruszonego konta użytkownika administracyjnego

Jeśli zostanie zidentyfikowany użytkownik z nieautoryzowanym działaniem łącznika, możesz zbadać tego użytkownika pod kątem potencjalnego naruszenia zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Odpowiadanie na naruszone konto e-mail](responding-to-a-compromised-email-account.md).

## <a name="more-information"></a>Więcej informacji

- [Usuwanie zablokowanych łączników](remove-blocked-connectors.md)
- [Usuwanie zablokowanych użytkowników](removing-user-from-restricted-users-portal-after-spam.md)
