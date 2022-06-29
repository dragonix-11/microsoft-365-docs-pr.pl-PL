---
title: Konfigurowanie ustawień globalnych ustawień bezpiecznych łączy w Ochrona usługi Office 365 w usłudze Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak wyświetlać i konfigurować ustawienia globalne (lista "Blokuj następujące adresy URL" i ochrona aplikacji Office 365) dla bezpiecznych linków w Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6c8b40109f20215b86a2264ed1a9f69c8db43bda
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487570"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Konfigurowanie ustawień globalnych bezpiecznych linków w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych, którzy [mają Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md). Jeśli jesteś użytkownikiem domowym, który szuka informacji o bezpiecznych linkach w programie Outlook, zobacz [Zaawansowane zabezpieczenia Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Bezpieczne linki to funkcja w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md), która umożliwia skanowanie adresów URL przychodzących wiadomości e-mail w przepływie poczty oraz czas weryfikacji kliknięć adresów URL i linków w wiadomościach e-mail i innych lokalizacjach. Aby uzyskać więcej informacji, zobacz [Bezpieczne linki w Ochrona usługi Office 365 w usłudze Microsoft Defender](safe-links.md).

Większość ustawień bezpiecznych łączy można skonfigurować w zasadach bezpiecznych łączy. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad bezpiecznych linków w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md).

Jednak usługa Safe Links używa również następujących ustawień globalnych skonfigurowanych poza samymi zasadami bezpiecznych łączy:

- Lista **Blokuj następujące adresy URL** . To ustawienie dotyczy wszystkich użytkowników, którzy są uwzględniane w żadnych aktywnych zasadach bezpiecznych linków. Aby uzyskać więcej informacji, zobacz ["Blokuj następujące adresy URL" listy bezpiecznych linków](safe-links.md#block-the-following-urls-list-for-safe-links)

- Ochrona bezpiecznych łączy dla aplikacji Office 365. Te ustawienia dotyczą wszystkich użytkowników w organizacji, którzy mają licencję na Ochrona usługi Office 365 w usłudze Defender, niezależnie od tego, czy użytkownicy są uwzględnieni w aktywnych zasadach bezpiecznych linków. Aby uzyskać więcej informacji, zobacz [Ustawienia bezpiecznych linków dla aplikacji Office 365](safe-links.md#safe-links-settings-for-office-365-apps).

Globalne ustawienia bezpiecznych łączy można skonfigurować w portalu Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla kwalifikujących się organizacji platformy Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomicznym programem PowerShell EOP dla organizacji bez Exchange Online skrzynki pocztowe, ale z Ochrona usługi Office 365 w usłudze Microsoft Defender subskrypcjami dodatków).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Chociaż nie ma domyślnych zasad bezpiecznych łączy, wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony** zapewniają ochronę bezpiecznych łączy wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach bezpiecznych łączy). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)). Można również utworzyć zasady bezpiecznych łączy, które będą stosowane do określonych użytkowników, grup lub domen. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad bezpiecznych linków w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-links-policies.md).

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Bezpieczne linki** , użyj polecenia <https://security.microsoft.com/safelinksv2>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Łączenie z programem PowerShell Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Connect to Exchange Online Protection PowerShell (Nawiązywanie połączenia z programem PowerShell).](/powershell/exchange/connect-to-exchange-online-protection-powershell)

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby skonfigurować ustawienia globalne bezpiecznych łączy, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do ustawień globalnych bezpiecznych łączy, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli usługi Azure Active Directory w Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w usłudze Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Aby zapoznać się z naszymi zalecanymi wartościami ustawień globalnych bezpiecznych linków, zobacz [Ustawienia bezpiecznych łączy](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- Zaczekaj do 30 minut na zastosowanie nowych lub zaktualizowanych zasad.

- [Nowe funkcje są stale dodawane do Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Po dodaniu nowych funkcji może być konieczne wprowadzenie zmian w istniejących zasadach bezpiecznych łączy.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>Konfigurowanie listy "Blokuj następujące adresy URL" w portalu Microsoft 365 Defender

> [!NOTE]
> Teraz możesz zarządzać wpisami bloku adresu URL na [liście dozwolonych/zablokowanych dzierżaw](allow-block-urls.md#create-block-url-entries-in-the-tenant-allowblock-list). Lista "Blokuj następujące adresy URL" jest w trakcie wycofywania. Spróbujemy przeprowadzić migrację istniejących wpisów z listy "Blokuj następujące adresy URL", aby zablokować wpisy adresów URL na liście dozwolonych/zablokowanych dzierżaw. Komunikaty zawierające zablokowany adres URL zostaną poddane kwarantannie.

Lista **Blokuj następujące adresy URL** identyfikuje linki, które powinny być zawsze blokowane przez skanowanie bezpiecznych linków w obsługiwanych aplikacjach. Aby uzyskać więcej informacji, zobacz ["Blokuj następujące adresy URL" listy bezpiecznych linków](safe-links.md#block-the-following-urls-list-for-safe-links).

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com> przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady zasad** \> \> **zagrożeń** **— bezpieczne linki** w sekcji Zasady. Aby przejść bezpośrednio do strony **Bezpieczne linki** , użyj polecenia <https://security.microsoft.com/safelinksv2>.

2. Na stronie **Bezpieczne linki** kliknij pozycję **Ustawienia globalne**. W wyświetlonym **polu Zasady bezpiecznych łączy dla twojej organizacji** przejdź do pola **Blokuj następujące adresy URL** .

3. Skonfiguruj co najmniej jeden wpis zgodnie z opisem w [sekcji Składnia wpisu dla listy "Blokuj następujące adresy URL"](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>Konfigurowanie listy "Blokuj następujące adresy URL" w programie PowerShell

Aby uzyskać szczegółowe informacje o składni wpisu, zobacz [Składnia wpisu dla listy "Blokuj następujące adresy URL"](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

Aby wyświetlić istniejące wpisy we właściwości _BlockURLs_, możesz użyć polecenia cmdlet **Get-AtpPolicyForO365**.

- Aby dodać wartości, które zastąpią wszystkie istniejące wpisy, użyj następującej składni w programie Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  W tym przykładzie do listy dano następujące wpisy:

  - Blokuj domenę, poddomeny i ścieżki dla fabrikam.com.
  - Blokuj badania poddomeny, ale nie domenę nadrzędną lub inne poddomeny w tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Aby dodać lub usunąć wartości bez wpływu na inne istniejące wpisy, użyj następującej składni:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  W tym przykładzie dodano nowy wpis dla adatum.com i usunięto wpis dla fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal"></a>Konfigurowanie ochrony bezpiecznych łączy dla aplikacji Office 365 w portalu Microsoft 365 Defender

Ochrona bezpiecznych łączy dla aplikacji Office 365 ma zastosowanie do dokumentów w obsługiwanych aplikacjach klasycznych, mobilnych i internetowych pakietu Office. Aby uzyskać więcej informacji, zobacz [Ustawienia bezpiecznych linków dla aplikacji Office 365](safe-links.md#safe-links-settings-for-office-365-apps).

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com> przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady zasad** \> \> **zagrożeń** **— bezpieczne linki** w sekcji Zasady. Aby przejść bezpośrednio do strony **Bezpieczne linki** , użyj polecenia <https://security.microsoft.com/safelinksv2>.

2. Na stronie **Bezpieczne linki** kliknij pozycję **Ustawienia globalne**. W wyświetlonym **artykule Zasady bezpiecznych łączy dla organizacji** skonfiguruj następujące ustawienia w sekcji **Ustawienia dotyczące zawartości w obsługiwanych aplikacjach Office 365**:

   - **Użyj bezpiecznych linków w aplikacjach Office 365**: sprawdź, czy przełącznik jest po prawej stronie, aby włączyć bezpieczne linki dla obsługiwanych aplikacji Office 365: ![Przełącz wł..](../../media/scc-toggle-on.png)

   - **Nie śledź, kiedy użytkownicy klikają linki chronione w aplikacjach Office 365**: przenieś przełącznik w lewo, aby śledzić kliknięcia użytkowników związane z zablokowanymi adresami URL w obsługiwanych aplikacjach Office 365: ![Przełącz wyłączone.](../../media/scc-toggle-off.png)

   - **Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL w aplikacjach Office 365**: sprawdź, czy przełącznik jest po prawej stronie, aby uniemożliwić użytkownikom klikanie oryginalnego zablokowanego adresu URL w obsługiwanych aplikacjach Office 365: ![Przełącz.](../../media/scc-toggle-on.png)

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>Konfigurowanie ochrony bezpiecznych łączy dla aplikacji Office 365 w programie PowerShell

Jeśli wolisz skonfigurować ochronę bezpiecznych łączy dla aplikacji Office 365 za pomocą programu PowerShell, użyj następującej składni w programie Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell:

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

W tym przykładzie skonfigurowano następujące ustawienia ochrony bezpiecznych łączy w aplikacjach Office 365:

- Bezpieczne linki dla aplikacji Office 365 są włączone (nie używamy parametru _EnableSafeLinksForO365Clients_, a wartość domyślna to $true).
- Kliknięcia użytkownika związane z zablokowanymi adresami URL w obsługiwanych Office 365 aplikacje są śledzone.
- Użytkownicy nie mogą klikać oryginalnego zablokowanego adresu URL w obsługiwanych aplikacjach Office 365 (nie używamy parametru _AllowClickThrough_, a wartość domyślna to $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

Aby sprawdzić, czy ustawienia globalne bezpiecznych łączy zostały pomyślnie skonfigurowane (lista **Blokuj następujące adresy URL** i ustawienia ochrony aplikacji Office 365), wykonaj dowolne z następujących kroków:

- Na stronie **Bezpieczne linki** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/safelinksv2>kliknij pozycję **Ustawienia globalne** i sprawdź ustawienia w wyświetlonym menu wysuwanym.

- W Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell uruchom następujące polecenie i sprawdź ustawienia:

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
