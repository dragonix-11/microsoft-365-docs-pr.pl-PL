---
title: Konfigurowanie ustawień globalnych dla ustawień Sejf Linków w programie Defender dla Office 365
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
description: Administratorzy mogą dowiedzieć się, jak wyświetlać i konfigurować ustawienia globalne (listę i ochronę następujących adresów URL oraz ochronę aplikacji usługi Office 365) dla linków programu Sejf w programie Microsoft Defender dla Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 857519e93df9490ebeb178a23a44ddddbdfc83ef
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021254"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Konfigurowanie ustawień globalnych dla programu Sejf Links w programie Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych korzystających z programu [Microsoft Defender dla Office 365](defender-for-office-365.md). Jeśli jesteś użytkownikiem domowym i szukasz informacji na temat bezpiecznych linków w u Outlook, zobacz [Zaawansowane zabezpieczenia Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sejf Links to funkcja programu [Microsoft Defender dla programu Office 365](defender-for-office-365.md), która umożliwia skanowanie adresów URL przychodzących wiadomości e-mail w przepływie poczty e-mail oraz czas weryfikacji kliknięciem adresów URL i linków w wiadomościach e-mail oraz w innych lokalizacjach. Aby uzyskać więcej informacji, zobacz [linki Sejf w programie Microsoft Defender dla Office 365](safe-links.md).

Większość ustawień łączy Sejf konfiguruje się w Sejf linków. Aby uzyskać instrukcje, [zobacz Konfigurowanie zasad Sejf Linków w programie Microsoft Defender dla Office 365](set-up-safe-links-policies.md).

Jednak w Sejf Linki używane są również następujące ustawienia globalne, które konfigurujesz poza samymi Sejf linków:

- Lista **Blokuj następujące adresy URL** . To ustawienie dotyczy wszystkich użytkowników uwzględnionych we wszystkich aktywnych zasadach usługi Sejf linków. Aby uzyskać więcej informacji, zobacz ["Blokowanie listy następujących adresów URL" dla następujących Sejf URL.](safe-links.md#block-the-following-urls-list-for-safe-links)
- Sejf ochrony linków dla Office 365 aplikacji. Te ustawienia mają zastosowanie do wszystkich użytkowników w organizacji, którzy mają licencje na usługę Defender dla usługi Office 365, niezależnie od tego, czy użytkownicy są uwzględnioni w aktywnych zasadach usługi Sejf Links. Aby uzyskać więcej informacji, [zobacz Sejf Ustawienia linków dla Office 365 aplikacji](safe-links.md#safe-links-settings-for-office-365-apps).

Ustawienia globalne linków Sejf można skonfigurować w portalu usługi Microsoft 365 Defender lub w programie PowerShell (Exchange Online PowerShell dla uprawnionych organizacji Microsoft 365 ze skrzynkami pocztowymi w programie Exchange Online; autonomiczny program PowerShell usługi EOP dla organizacji bez Exchange Online skrzynek pocztowych, ale za pomocą programu Microsoft Defender Office 365 subskrypcji dodatków).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Mimo że nie istnieją domyślne zasady Sejf, wstępnie ustawione zasady zabezpieczeń wbudowanej  ochrony zapewniają ochronę linków programu Sejf wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach Sejf Linków). Aby uzyskać więcej informacji, zobacz [Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender for Office 365](preset-security-policies.md). Możesz również utworzyć zasady linków Sejf, które będą stosowane do konkretnych użytkowników, grup lub domen. Aby uzyskać instrukcje, [zobacz Konfigurowanie zasad Sejf Linków w programie Microsoft Defender dla Office 365](set-up-safe-links-policies.md).

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do **strony Sejf,** użyj .<https://security.microsoft.com/safelinksv2>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby skonfigurować ustawienia globalne łącza Sejf, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do ustawień globalnych linków programu Sejf, musisz być członkiem grup ról czytnika globalnego lub  **czytnika zabezpieczeń**.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

- Aby uzyskać nasze zalecane wartości dla ustawień globalnych linków Sejf, zobacz Sejf [ustawienia linków](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- Odmów do 30 minut na zastosowanie nowych lub zaktualizowanych zasad.

- [Nowe funkcje są stale dodawane do programu Microsoft Defender dla Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). W związku z dodaniem nowych funkcji może być konieczne dostosowanie istniejących zasad Sejf linków.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>Konfigurowanie listy "Blokowanie następujących adresów URL" w portalu Microsoft 365 Defender adresowych

Na **liście Blokuj poniższe adresy URL** są identyfikowane linki, które powinny być zawsze blokowane przez skanowanie łączy Sejf w obsługiwanych aplikacjach. Aby uzyskać więcej informacji, zobacz ["Blokowanie następujących adresów URL" w celu Sejf url](safe-links.md#block-the-following-urls-list-for-safe-links).

1. W portalu Microsoft 365 Defender przejdź  \> <https://security.microsoft.com>do sekcji Zasady & e-mail **& zasady** \>  \> zagrożeń Sejf **linki** **do** zasad. Aby przejść bezpośrednio do **strony Sejf,** użyj .<https://security.microsoft.com/safelinksv2>

2. Na stronie **Sejf kliknij** pozycję **Ustawienia globalne**. W **wyświetlonym Sejf Linki** wyszukiwania dla organizacji przejdź do pola **Blokuj następujące adresy URL**.

3. Skonfiguruj co najmniej jeden wpis zgodnie z opisem w składni pozycji dla listy ["Blokuj następujące adresy URL"](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>Konfigurowanie listy "Blokowanie następujących adresów URL" w programie PowerShell

Aby uzyskać szczegółowe informacje na temat składni wprowadzania, zobacz [Składnia pozycji dla listy "Blokuj następujące adresy URL"](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

Możesz użyć polecenia cmdlet **Get-AtpPolicyForO365** , aby wyświetlić istniejące wpisy we właściwości _BlockURLs_ .

- Aby dodać wartości, które zastąpią wszelkie istniejące wpisy, użyj następującej składni w programie PowerShell Exchange Online powershell Exchange Online Protection PowerShell:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  W tym przykładzie do listy są dodano następujące wpisy:

  - Blokowanie domen, poddomen i ścieżek dla fabrikam.com.
  - Blokuj badania nad poddomenami, ale nie domenę nadrzędną ani inne poddomeny w tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Aby dodać lub usunąć wartości bez wpływu na inne istniejące wpisy, użyj następującej składni:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  W tym przykładzie dodano nowy wpis adatum.com i usuwa wpis dla fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal"></a>Konfigurowanie Sejf linków do stron Office 365 aplikacji w portalu Microsoft 365 Defender sieci Web

Sejf ochrona linków dla Office 365 dotyczy dokumentów w obsługiwanych aplikacjach Office, urządzeniach przenośnych i aplikacjach sieci Web. Aby uzyskać więcej informacji, [zobacz Sejf Ustawienia linków dla Office 365 aplikacji](safe-links.md#safe-links-settings-for-office-365-apps).

1. W portalu Microsoft 365 Defender przejdź  \> <https://security.microsoft.com>do sekcji Zasady & e-mail **& zasady** \>  \> zagrożeń Sejf **linki** **do** zasad. Aby przejść bezpośrednio do **strony Sejf,** użyj .<https://security.microsoft.com/safelinksv2>

2. Na stronie **Sejf kliknij** pozycję **Ustawienia globalne**. W **wyświetlonym Sejf** Linki do stron sieci Web organizacji skonfiguruj następujące ustawienia w sekcji Ustawienia, które dotyczą zawartości w sekcji obsługiwane **Office 365 aplikacji:**

   - **Używanie Sejf w aplikacjach Office 365:** Sprawdź, czy przełącznik jest po prawej stronie, aby włączyć linki Sejf dla obsługiwanych Office 365 aplikacji: ![Włącz.](../../media/scc-toggle-on.png).

   - **Nie śledź** po kliknięciu przez użytkowników chronionych linków w aplikacjach pakietu Office 365: Przesuń przełącznik w lewo, aby śledzić kliknięcia użytkowników związane z zablokowanymi adresami URL w obsługiwanych aplikacjach pakietu Office 365: ![Wyłącz.](../../media/scc-toggle-off.png)

   - Nie pozwól użytkownikom klikać, aby przejść do pierwotnego adresu URL w aplikacjach pakietu **Office 365**: Sprawdź, czy przełącznik jest po prawej stronie, aby uniemożliwić użytkownikom kliknięcie pierwotnego zablokowanego adresu URL w obsługiwanych Office 365 aplikacjach: ![Włącz.](../../media/scc-toggle-on.png).

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>Konfigurowanie Sejf linków do stron Office 365 w programie PowerShell

Jeśli wolisz używać programu PowerShell do konfigurowania ochrony linków programu Sejf dla aplikacji Office 365, użyj następującej składni w programie Exchange Online PowerShell lub Exchange Online Protection PowerShell:

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

W tym przykładzie konfigurowane są następujące ustawienia ochrony Sejf linków w Office 365 aplikacjach:

- Sejf Linki dla aplikacji Office 365 są włączone (nie używamy _parametru EnableSafeLinksForO365Clients_, a wartość domyślna to $true).
- Kliknięcia użytkowników związane z zablokowanymi adresami URL w obsługiwanych Office 365 są śledzone.
- Użytkownicy nie mogą klikać pierwotnego zablokowanego adresu URL w obsługiwanych aplikacjach pakietu Office 365 (nie używamy parametru _AllowClickThrough_, a wartość domyślna to $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiadomo, że te procedury działały?

Aby sprawdzić, czy ustawienia globalne linków programu Sejf (lista Blokuj następujące adresy **URL** i ustawienia ochrony aplikacji usługi Office 365) zostały pomyślnie skonfigurowane, wykonaj dowolną z następujących czynności:

- Na stronie **Sejf sieci Web** w portalu Microsoft 365 Defender kliknij <https://security.microsoft.com/safelinksv2>pozycję Ustawienia **globalne i sprawdź** ustawienia w wyświetlonym wysuwanych witrynie.

- W Exchange Online PowerShell lub Exchange Online Protection PowerShell uruchom następujące polecenie i sprawdź ustawienia:

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
