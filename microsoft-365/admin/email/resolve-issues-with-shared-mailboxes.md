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
description: Podczas konfigurowanie udostępnionych skrzynek pocztowych mogą pojawić się błędy. Jeśli występują problemy z udostępnionymi skrzynkami pocztowymi, wypróbuj poniższe rozwiązania.
ms.openlocfilehash: 2be12810e6651da5b062afbd0a3437913b9a4d60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973551"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>Rozwiązywanie problemów z udostępnionymi skrzynkami pocztowymi

Jeśli podczas tworzenia lub używania udostępnionej skrzynki pocztowej są wyświetlane komunikaty o błędach, wypróbuj te możliwe rozwiązania. 

## <a name="error-when-creating-shared-mailboxes"></a>Błąd podczas tworzenia udostępnionych skrzynek pocztowych
<a name="bkmk_Fix"> </a>

Jeśli zostanie wyświetlony komunikat o błędzie, adres serwera **proxy "smtp:<\> nazwa udostępnionej skrzynki pocztowej" jest już używany przez adresy serwera proxy lub LegacyExchangeDN użytkownika "\<name>". Wybierz inny adres serwera proxy**, oznacza to, że próbujesz nadać udostępnionej skrzynce pocztowej nazwę, która jest już używania. Załóżmy na przykład, że chcesz nadać udostępnionym skrzynkom pocztowym nazwy info@domena1 i info@domena2. Istnieją dwa sposoby wykonywania tej czynności:

  - Za pomocą programu Windows PowerShell. Zobacz ten wpis w blogu, aby uzyskać instrukcje: [Tworzenie udostępnionych skrzynek pocztowych o tym samym aliasie w różnych domenach](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)
    
  - Nazwij drugą udostępnioną skrzynkę pocztową od początku inną, aby ominą ten błąd. Następnie w centrum administracyjnym zmień nazwę udostępnionej skrzynki pocztowej na dokładniejszą.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>Błąd o tym, że nie masz uprawnień do wysyłania podczas korzystania z udostępnionej skrzynki pocztowej

Jeśli utworzono udostępnioną skrzynkę pocztową, a następnie próbujesz wysłać z tej skrzynki wiadomość, możesz uzyskać następujące informacje:

**Nie można wysłać tej wiadomości. Nie masz uprawnienia do wysyłania wiadomości w imieniu określonego użytkownika.**

Ten komunikat jest wyświetlany, Microsoft 365 występuje problem z opóźnieniem replikacji. Powinno to zostać z dala od komputera w ciągu około godziny, gdy informacje o nowej udostępnionej skrzynce pocztowej (lub dodanym użytkowniku) zostaną powielane we wszystkich naszych centrach danych. Odczekaj godzinę, a następnie spróbuj ponownie wysłać wiadomość.

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o udostępnionych skrzynkach pocztowych](about-shared-mailboxes.md) (artykuł)\
[Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md) (artykuł)\
[Konfigurowanie udostępnionej skrzynki pocztowej](configure-a-shared-mailbox.md) (artykuł)\
[Konwertowanie skrzynki pocztowej użytkownika na udostępnioną skrzynkę pocztową](convert-user-mailbox-to-shared-mailbox.md) (artykuł)\
[Usuwanie licencji z udostępnionej skrzynki pocztowej](remove-license-from-shared-mailbox.md) (artykuł)


    

