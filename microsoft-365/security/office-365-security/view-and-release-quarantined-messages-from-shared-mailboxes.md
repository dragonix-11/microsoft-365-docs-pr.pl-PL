---
title: Wyświetlanie i zwalnianie wiadomości poddanych kwarantannie z udostępnionych skrzynek pocztowych
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Użytkownicy mogą dowiedzieć się, jak wyświetlać wiadomości poddane kwarantannie i działać w nich, które zostały wysłane do udostępnionych skrzynek pocztowych, do których mają uprawnienia.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e78a46bca97ea58a88195c9d05e11332528cf3af
ms.sourcegitcommit: 317fab13e84b2867087a6ba0a593313ecf43bbed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2021
ms.locfileid: "62988665"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Wyświetlanie i zwalnianie wiadomości poddanych kwarantannie z udostępnionych skrzynek pocztowych

> [!NOTE]
> Funkcje opisane w tym artykule są obecnie dostępne w wersji Preview, nie są dostępne dla wszystkich i mogą ulec zmianie.

Użytkownicy mogą zarządzać wiadomościami poddanymi kwarantannie w miejscu, w którym są jednym z adresatów, zgodnie z opisem w tece Znajdowanie i zwalnianie wiadomości poddanych kwarantannie jako [użytkownik w ucieka programie EOP](find-and-release-quarantined-messages-as-a-user.md). Ale co z **udostępnionymi** skrzynkami pocztowymi, w których użytkownik ma uprawnienia Pełny dostęp i Wyślij jako lub Wyślij w imieniu do skrzynki pocztowej zgodnie z opisem w tece Udostępnione skrzynki pocztowe w [programie Exchange Online](/exchange/collaboration-exo/shared-mailboxes)?

Wcześniej możliwość zarządzania poddaną kwarantannie wiadomości wysyłanych do udostępnionej skrzynki pocztowej była przez administratorów wymagana, aby dla tej udostępnionej skrzynki pocztowej było włączone automatyczne mapowanie (ta funkcja jest domyślnie włączona, gdy administrator daje użytkownikowi dostęp do innej skrzynki pocztowej). Jednak w zależności od rozmiaru i liczby skrzynek pocztowych, do których użytkownik ma dostęp, wydajność może mieć wpływ na to, że program Outlook  próbuje otworzyć wszystkie skrzynki pocztowe, do których użytkownik ma dostęp. Z tego powodu wielu administratorów decyduje się usunąć [automatyczne mapowanie dla udostępnionych skrzynek pocztowych](/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

Teraz automatyczne mapowanie nie jest już wymagane, aby użytkownicy zarządzali wiadomościami poddanymi kwarantannie, które zostały wysłane do udostępnionych skrzynek pocztowych. To po prostu działa. Istnieją dwie różne metody uzyskiwania dostępu do wiadomości poddanych kwarantannie, które zostały wysłane do udostępnionej skrzynki pocztowej:

- Jeśli administrator skonfigurował [](quarantine-policies.md) zasady kwarantanny w celu zezwalania na powiadomienia kwarantanny (wcześniej nazywane powiadomieniami użytkowników końcowych o spamie), każdy użytkownik, który ma dostęp do powiadomień kwarantanny  w udostępnionej skrzynce pocztowej, może kliknąć przycisk Recenzja w powiadomieniu, aby przejść do kwarantanny w portalu Microsoft 365 Defender. Ta metoda umożliwia użytkownikom tylko zarządzanie poddanych kwarantannie wiadomości, które zostały wysłane do udostępnionej skrzynki pocztowej. W tym kontekście użytkownicy nie mogą zarządzać własnymi wiadomościami kwarantanny.
- Użytkownik może przejść [do kwarantanny w portalu Microsoft 365 Defender i](find-and-release-quarantined-messages-as-a-user.md) kliknąć pozycję Filtruj, aby przefiltrować wyniki według adresu adresata **(adresu** e-mail udostępnionej skrzynki pocztowej). Na stronie głównej **kwarantanny** możesz kliknąć kolumnę **Adresat** , aby posortować dane według wiadomości wysłanych do udostępnionej skrzynki pocztowej.

## <a name="things-to-keep-in-mind"></a>O których należy pamiętać

- _Zasady kwarantanny_ określają, co użytkownicy mogą, a czego nie mogą robić w kwarantannie wiadomości w zależności od tego, dlaczego wiadomość została poddana kwarantannie (dla obsługiwanych funkcji). Domyślne zasady kwarantanny wymuszają funkcje historyczne, które umożliwiają adresatom wyświetlanie wiadomości i działanie na ich podstawie. Administratorzy mogą tworzyć i stosować niestandardowe zasady kwarantanny definiujące mniej restrykcyjne lub bardziej restrykcyjne funkcje dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

- Pierwszy użytkownik, który podejmie działania w oparciu o poddaną kwarantannie wiadomość, decyduje o pochłonie tej wiadomości dla wszystkich osób, które korzysta z udostępnionej skrzynki pocztowej. Jeśli na przykład dostęp do udostępnionej skrzynki pocztowej uzyskało 10 użytkowników, a użytkownik zdecyduje się usunąć wiadomość kwarantanny, ta wiadomość zostanie usunięta dla wszystkich 10 użytkowników. Podobnie, jeśli użytkownik zdecyduje się zwolnić wiadomość, zostanie ona opublikowana w udostępnionej skrzynce pocztowej i będzie dostępna dla wszystkich pozostałych użytkowników udostępnionej skrzynki pocztowej.

- Obecnie przycisk Zablokuj **nadawcę** nie jest dostępny w **wysuwanych** szczegółach w przypadku wiadomości poddanych kwarantannie, które zostały wysłane do udostępnionej skrzynki pocztowej.

- Jeśli korzystasz z zagnieżdżonych grup zabezpieczeń w celu udzielania dostępu do udostępnionej skrzynki pocztowej w odniesieniu do operacji kwarantanny dla udostępnionych skrzynek pocztowych, zalecamy nie więcej niż dwa poziomy grup zagnieżdżonych. Na przykład grupa A jest członkiem grupy B, która jest członkiem grupy C. Aby przypisać uprawnienia do udostępnionej skrzynki pocztowej, nie dodawaj użytkownika do grupy A, a następnie przypisuj grupę C do udostępnionej skrzynki pocztowej.  

- Aby zarządzać wiadomościami poddanymi kwarantannie dla udostępnionej skrzynki pocztowej w programie [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), użytkownik końcowy będzie musiał użyć polecenia cmdlet [Get-QuarantineMessage z adresem e-mail](/powershell/module/exchange/get-quarantinemessage) udostępnionej skrzynki pocztowej do określenia wiadomości w parametrze _RecipientAddress_. Przykład:

  ```powershell
  Get-QuarantinedMessage -RecipientAddress officeparty@contoso.com
  ```

  Następnie użytkownik końcowy może wybrać poddaną kwarantannie wiadomość z listy, aby wyświetlić lub podjąć działanie w związku z tym.

  W tym przykładzie pokazano wszystkie poddaną kwarantannie wiadomości wysłane do udostępnionej skrzynki pocztowej, a następnie zwolniono pierwszą wiadomość na liście z kwarantanny (pierwsza wiadomość na liście to 0, druga to 1 itd.).

  ```powershell
  $SharedMessages = Get-QuarantinedMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantinedMessage -Identity $SharedMessages[0]
  ```

  Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz następujące tematy:

  - [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](/powershell/module/exchange/get-quarantinemessageheader)
  - [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
