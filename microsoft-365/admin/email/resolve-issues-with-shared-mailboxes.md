---
title: Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Podczas konfigurowania udostępnionych skrzynek pocztowych mogą wystąpić błędy. Wypróbuj te rozwiązania, jeśli wystąpią problemy z udostępnionymi skrzynkami pocztowymi.
ms.openlocfilehash: cf121504b53951e0aaaf248d43d045cfa937f4ed
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437112"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi

Jeśli podczas tworzenia lub używania udostępnionej skrzynki pocztowej są wyświetlane komunikaty o błędach, wypróbuj te możliwe rozwiązania. 

## <a name="error-when-creating-shared-mailboxes"></a>Błąd podczas tworzenia udostępnionych skrzynek pocztowych

Jeśli zostanie wyświetlony komunikat o błędzie, **adres serwera proxy "smtp:<nazwa\> udostępnionej skrzynki pocztowej" jest już używany przez adresy proxy lub LegacyExchangeDN "\<name>". Wybierz inny adres serwera proxy**, co oznacza, że próbujesz nadać udostępnionej skrzynce pocztowej nazwę, która jest już używana. Załóżmy na przykład, że chcesz nadać udostępnionym skrzynkom pocztowym nazwy info@domena1 i info@domena2. Istnieją dwa sposoby wykonywania tej czynności:

  - Za pomocą programu Windows PowerShell. Zobacz ten wpis w blogu, aby uzyskać instrukcje: [Tworzenie udostępnionych skrzynek pocztowych z tym samym aliasem w różnych domenach](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)
    
  - Nadaj drugiej udostępnionej skrzynce pocztowej nazwę inną niż początkowa, aby obejść błąd. Następnie w centrum administracyjnym zmień nazwę udostępnionej skrzynki pocztowej na odpowiednią.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>Błąd dotyczący braku uprawnień do wysyłania w przypadku korzystania z udostępnionej skrzynki pocztowej

Jeśli utworzono udostępnioną skrzynkę pocztową, a następnie podjęto próbę wysłania z niej wiadomości, możesz uzyskać następujące informacje:

**Nie można wysłać tej wiadomości. Nie masz uprawnień do wysyłania wiadomości w imieniu określonego użytkownika.**

Ten komunikat jest wyświetlany, gdy Microsoft 365 występuje problem z opóźnieniem replikacji. Powinno ono zniknąć w ciągu godziny, gdy informacje o nowej udostępnionej skrzynce pocztowej (lub dodanym użytkowniku) są replikowane we wszystkich naszych centrach danych. Poczekaj godzinę, a następnie spróbuj ponownie wysłać wiadomość.

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Usuwanie licencji ze udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)