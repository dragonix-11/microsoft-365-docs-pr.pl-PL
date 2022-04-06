---
title: Recenzja dla zgłoszonych wiadomości przez administratora
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Dowiedz się, jak przeglądać zgłoszone wiadomości i przekazać opinie użytkownikom.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 44476e7a8ad3bad9b21e82a9528593ceb350257d
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470906"
---
# <a name="admin-review-for-reported-messages"></a>Recenzja dla zgłoszonych wiadomości przez administratora

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z Exchange Online skrzynek pocztowych i Ochrona usługi Office 365 w usłudze Microsoft Defender administratorzy mogą teraz wysyłać szablonowe wiadomości z powrotem do użytkowników końcowych po przejrzeniu zgłoszonych wiadomości. Szablony można dostosować do potrzeb organizacji, a także na podstawie werdyktów administratora.

Ta funkcja została zaprojektowana tak, aby przekazać opinię użytkownikom, ale nie zmienia werdyktów wiadomości w systemie. Aby pomóc firmie Microsoft w aktualizacji i ulepszyć jej filtry, musisz przesłać wiadomości do analizy przy użyciu [przesyłania przez administratora](admin-submission.md).

Użytkownikom można będzie oznaczać i powiadamiać użytkowników o wynikach przeglądu tylko wtedy, gdy wiadomość została zgłoszone jako wynik fałszywie dodatni lub jako wynik fałszywie [ujemny](report-false-positives-and-false-negatives.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do **strony Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

- Aby zmodyfikować konfigurację przesyłania użytkowników, musisz być członkiem jednej z następujących grup ról:
  - Administrator zabezpieczeń lub zarządzanie organizacją w portalu [Microsoft 365 Defender sieci.](permissions-microsoft-365-security-center.md)
  - Zarządzanie organizacją w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

- Będziesz także potrzebować dostępu do programu Exchange Online PowerShell. Jeśli konto, które próbujesz użyć, nie ma dostępu do programu Exchange Online PowerShell, zostanie wyświetlony komunikat o błędzie Określanie adresu e-mail *w domenie*. Aby uzyskać więcej informacji na temat włączania lub wyłączania dostępu do programu Exchange Online PowerShell, zobacz następujące tematy:
  - [Włączanie lub wyłączanie dostępu do programu Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Reguły dostępu klienta w programie Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="notify-users-from-within-the-portal"></a>Powiadamianie użytkowników z poziomu portalu

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do strony **Przesyłanie w witrynie** e-mail **& Przesyłanie** \> **.** Aby przejść bezpośrednio do **strony Materiały**, użyj .<https://security.microsoft.com/reportsubmission>

2. Kliknij **pozycję Użytkownik zgłosił wiadomości**, a następnie zaznacz wiadomość, którą chcesz oznaczyć i powiadomić.

3. Wybierz menu **rozwijane Oznacz jako i powiadom** , a następnie wybierz pozycję **Nie** znaleziono zagrożeń, **Wyłudzanie informacji** lub **Wiadomości-śmieci**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/admin-review-send-message-from-portal.png" alt-text="Strona z wyświetlonymi wiadomościami zgłoszonymi przez użytkownika" lightbox="../../media/admin-review-send-message-from-portal.png":::

Zgłoszona wiadomość zostanie oznaczona jako fałszywie dodatnia lub fałszywie ujemna, a z portalu zostanie automatycznie wysłana wiadomość e-mail z powiadomieniem użytkownika, który zgłosił wiadomość.

## <a name="customize-the-messages-used-to-notify-users"></a>Dostosowywanie wiadomości używanych do powiadamiania użytkowników

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź do strony Przesyłanie użytkowników w witrynie  Zasady współpracy z usługą **e-mail &** \> zasady współpracy **& Zasady** \>  \> zagrożeń, które użytkownik zgłosił ustawienia wiadomości w **sekcji** Inne. Aby przejść bezpośrednio do **strony Przesyłanie użytkowników**, użyj .<https://security.microsoft.com/userSubmissionsReportMessage>

2. Jeśli chcesz  określić nazwę wyświetlaną nadawcy, na stronie Przesyłanie użytkowników zaznacz pole Określ adres e-mail do użycia jako nadawca w sekcji Powiadomienia e-mail dla administratorów  z wynikami przeglądu, **Office 365** następnie wprowadź nazwę, której chcesz użyć. Adres e-mail, który będzie widoczny w Outlook i wszystkie odpowiedzi będą tam trafiać.

3. Jeśli chcesz dostosować dowolny z szablonów, kliknij pozycję Dostosuj powiadomienia  e-mail u dołu strony. W otwieranych wysuwanych menu możesz dostosować tylko następujące elementy:

    - Wyłudzanie informacji
    - Wiadomości-śmieci
    - Nie znaleziono zagrożeń
    - Stopka

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/admin-review-customize-message.png" alt-text="Strona komunikatu potwierdzenia Dostosuj" lightbox="../../media/admin-review-customize-message.png":::

4. Po zakończeniu kliknij przycisk **Zapisz**. Aby wyczyścić te wartości, kliknij pozycję **Odrzuć** na **stronie Przesyłanie użytkowników** .
