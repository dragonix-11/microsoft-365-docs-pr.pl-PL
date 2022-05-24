---
title: Wyświetlanie i zwalnianie komunikatów poddanych kwarantannie z udostępnionych skrzynek pocztowych
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
description: Użytkownicy mogą dowiedzieć się, jak wyświetlać komunikaty poddane kwarantannie i działać na nich, które zostały wysłane do udostępnionych skrzynek pocztowych, do których mają uprawnienia.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2613d3b8be200db3a9107355a27b0dd79ce537d3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647343"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Wyświetlanie i zwalnianie komunikatów poddanych kwarantannie z udostępnionych skrzynek pocztowych

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Użytkownicy mogą zarządzać komunikatami objętymi kwarantanną, w których są jednym z adresatów, zgodnie z [opisem w temacie Znajdowanie i zwalnianie komunikatów poddanych kwarantannie jako użytkownik w ramach EOP](find-and-release-quarantined-messages-as-a-user.md). Ale co z **udostępnionymi skrzynkami pocztowymi**, w których użytkownik ma uprawnienia Pełny dostęp i Wyślij jako lub Wyślij w imieniu do skrzynki pocztowej zgodnie z opisem w [temacie Udostępnione skrzynki pocztowe w Exchange Online](/exchange/collaboration-exo/shared-mailboxes)?

Wcześniej możliwość zarządzania wiadomościami w kwarantannie wysyłanych do udostępnionej skrzynki pocztowej wymagała od administratorów pozostawienia włączonego automatycznego aplikowania dla udostępnionej skrzynki pocztowej (jest ona domyślnie włączona, gdy administrator zapewnia użytkownikowi dostęp do innej skrzynki pocztowej). Jednak w zależności od rozmiaru i liczby skrzynek pocztowych, do których użytkownik ma dostęp, wydajność może wystąpić, ponieważ program Outlook próbuje otworzyć _wszystkie_ skrzynki pocztowe, do których użytkownik ma dostęp. Z tego powodu wielu administratorów decyduje się [usunąć automatyczne aplikacje dla udostępnionych skrzynek pocztowych](/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

Teraz automatyczne aplikacje nie są już wymagane, aby użytkownicy mogli zarządzać wiadomościami w kwarantannie, które zostały wysłane do udostępnionych skrzynek pocztowych. To po prostu działa. Istnieją dwie różne metody uzyskiwania dostępu do wiadomości poddanych kwarantannie, które zostały wysłane do udostępnionej skrzynki pocztowej:

- Jeśli administrator skonfigurował [zasady kwarantanny](quarantine-policies.md) tak, aby zezwalały na powiadomienia o kwarantannie (wcześniej nazywane powiadomieniami o spamie użytkowników końcowych), każdy użytkownik, który ma dostęp do powiadomień kwarantanny w udostępnionej skrzynce pocztowej, może kliknąć przycisk **Przejrzyj** w powiadomieniu, aby przejść do kwarantanny w portalu Microsoft 365 Defender. Należy pamiętać, że ta metoda umożliwia użytkownikom zarządzanie wiadomościami objętymi kwarantanną, które zostały wysłane do udostępnionej skrzynki pocztowej. Użytkownicy nie mogą zarządzać własnymi komunikatami kwarantanny w tym kontekście.
- Użytkownik może [przejść do kwarantanny w portalu Microsoft 365 Defender](find-and-release-quarantined-messages-as-a-user.md) i kliknąć pozycję **Filtruj**, aby filtrować wyniki według **adresu adresata** (adres e-mail udostępnionej skrzynki pocztowej). Na głównej stronie **Kwarantanna** możesz kliknąć kolumnę **Adresat** , aby sortować według wiadomości wysłanych do udostępnionej skrzynki pocztowej.

## <a name="things-to-keep-in-mind"></a>Rzeczy, o których należy pamiętać

- _Zasady kwarantanny_ definiują, którzy użytkownicy mogą wykonywać komunikaty poddane kwarantannie lub nie, na podstawie przyczyn, dla których komunikat został poddany kwarantannie (w przypadku obsługiwanych funkcji). Domyślne zasady kwarantanny wymuszają historyczne możliwości, które umożliwiają odbiorcom wyświetlanie komunikatów i działanie na nie. Administratorzy mogą tworzyć i stosować niestandardowe zasady kwarantanny, które definiują mniej restrykcyjne lub bardziej restrykcyjne możliwości dla użytkowników. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

- Pierwszy użytkownik, który podejmie działania w sprawie wiadomości poddanej kwarantannie, decyduje o losie wiadomości dla wszystkich użytkowników korzystających z udostępnionej skrzynki pocztowej. Jeśli na przykład udostępniona skrzynka pocztowa jest dostępna dla 10 użytkowników, a użytkownik zdecyduje się usunąć wiadomość kwarantanny, wiadomość zostanie usunięta dla wszystkich 10 użytkowników. Podobnie jeśli użytkownik zdecyduje się wydać wiadomość, zostanie ona udostępniona do udostępnionej skrzynki pocztowej i będzie dostępna dla wszystkich innych użytkowników udostępnionej skrzynki pocztowej.

- Obecnie przycisk **Blokuj nadawcę** nie jest dostępny w wysuwaniu **Szczegóły** dla wiadomości objętych kwarantanną, które zostały wysłane do udostępnionej skrzynki pocztowej.

- Jeśli w przypadku operacji kwarantanny dla udostępnionych skrzynek pocztowych używasz zagnieżdżonych grup zabezpieczeń do udzielania dostępu do udostępnionej skrzynki pocztowej, zalecamy nie więcej niż dwa poziomy zagnieżdżonych grup. Na przykład grupa A jest członkiem grupy B, która jest członkiem grupy C. Aby przypisać uprawnienia do udostępnionej skrzynki pocztowej, nie należy dodawać użytkownika do grupy A, a następnie przypisywać grupy C do udostępnionej skrzynki pocztowej.  

- Aby zarządzać komunikatami poddanymi kwarantannie dla udostępnionej skrzynki pocztowej w [programie Exchange Online programie PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), użytkownik końcowy będzie musiał użyć polecenia cmdlet [Get-QuarantineMessage z udostępnionym](/powershell/module/exchange/get-quarantinemessage) adresem e-mail skrzynki pocztowej dla wartości parametru _RecipientAddress_ w celu zidentyfikowania wiadomości. Przykład:

  ```powershell
  Get-QuarantineMessage -RecipientAddress officeparty@contoso.com
  ```

  Następnie użytkownik końcowy może wybrać z listy komunikat poddany kwarantannie, aby wyświetlić lub podjąć działania.

  W tym przykładzie przedstawiono wszystkie wiadomości poddane kwarantannie, które zostały wysłane do udostępnionej skrzynki pocztowej, a następnie zwalnia pierwszą wiadomość z listy z kwarantanny (pierwsza wiadomość na liście to 0, druga to 1 itd.).

  ```powershell
  $SharedMessages = Get-QuarantineMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantineMessage -Identity $SharedMessages[0]
  ```

  Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz następujące tematy:

  - [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](/powershell/module/exchange/get-quarantinemessageheader)
  - [Wersja zapoznawcza — Kwarantanna](/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
