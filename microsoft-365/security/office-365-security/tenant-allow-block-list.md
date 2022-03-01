---
title: Zarządzanie zezwalaniami i blokami na liście zezwalania/blokowania dzierżawy
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak zarządzać zezwalania i blokowania na liście zezwalania/blokowania dzierżawy w portalu zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d7e3e56ccdaa59b39a6f65a63684b5b715db352e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033762"
---
# <a name="manage-the-tenant-allowblock-list"></a>Zarządzanie listą zezwalania/blokowania dzierżawy

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> Niektóre funkcje opisane w tym artykule są dostępne w wersji Preview, mogą ulec zmianie i nie są dostępne we wszystkich organizacjach.
>
> Jeśli w Twojej organizacji nie ma funkcji fałszowania opisanych w tym artykule, zobacz starsze środowisko zarządzania fałszerami w artykule Zarządzanie fałszywymi nadawcami przy użyciu zasad ochrony przed fałszerami i wglądu w analizę fałszowania w [uciekinie usługi EOP](walkthrough-spoof-intelligence-insight.md).

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych usług Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online można nie zgodzić się z werdyktem filtrowania usługi EOP. Na przykład dobra wiadomość może zostać oznaczona jako zła (wynik fałszywie dodatni) lub błędna wiadomość może zostać dozwolona przez (wynik fałszywie ujemny).

Lista zezwalania/blokowania dzierżawy w portalu Microsoft 365 Defender umożliwia ręczne zastępowanie Microsoft 365 werdyktów filtrowania. Lista zezwalania/blokowania dzierżawy jest używana podczas przepływu poczty dla wiadomości przychodzących (nie dotyczy wiadomości wewnątrz organizacji) i w momencie kliknięć przez użytkownika. Można określić następujące typy zastępować:

- Adresy URL do zablokowania.
- Pliki do zablokowania.
- Adresy e-mail nadawców i domeny do zablokowania.
- Sfałszowani nadawcy, aby zezwolić lub zablokować. Jeśli zastąpisz zezwalanie na werdykt lub zablokujemy możliwość fałszowania informacji o analizie[, fałszywy](learn-about-spoof-intelligence.md) nadawca stanie się ręcznym wpisem zezwalania lub blokowania, który pojawia się tylko na karcie Fałsz na liście Zezwalaj/Zablokuj dzierżawy. Możesz również ręcznie utworzyć w tym miejscu zezwalanie na lub blokowanie wpisów dla sfałszowanych nadawców, zanim zostaną one wykryte przez fałszywą inteligencję.
- Adresy URL, na które zezwalasz.
- Pliki, na które zezwalasz.
- Adresy e-mail lub domeny nadawców, na które chcesz zezwolić.

W tym artykule opisano sposób konfigurowania wpisów na liście zezwalania/blokowania dzierżawy w portalu usługi Microsoft 365 Defender lub w programie Power Microsoft 365 Shell (program Exchange Online PowerShell dla organizacji z skrzynkami pocztowymi w programie Exchange Online; autonomiczny program PowerShell usługi EOP dla organizacji bez Exchange Online skrzynki pocztowe).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Listy zezwalań/** zablokowanych dzierżaw, użyj .<https://security.microsoft.com/tenantAllowBlockList>

- Pliki można określić, używając wartości skrótu SHA256 pliku. Aby znaleźć wartość skrótu SHA256 pliku w programie Windows, uruchom następujące polecenie w wierszu polecenia:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Przykładowa wartość to `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Wartości skrótu perceptual (pHash) nie są obsługiwane.

- Dostępne wartości adresu URL opisano w składni adresu URL dla sekcji Lista adresów zezwalania [/blokowania dzierżawy](#url-syntax-for-the-tenant-allowblock-list) w dalszej części tego artykułu.

- Lista zezwalania/blokowania dzierżawy umożliwia nadawcom maksymalnie 500 wpisów, 500 wpisów dla adresów URL, 500 wpisów dla skrótów plików i 1024 wpisy dotyczące fałszowania (sfałszowanych nadawców).

- Maksymalna liczba znaków w każdym wpisie to:
  - Skróty plików = 64
  - URL = 250

- Wpis powinien być aktywny w ciągu 30 minut.

- Domyślnie wpisy na liście zezwalania/blokowania dzierżawy wygasają po 30 dniach. Można określić datę lub ustawić ją tak, aby nigdy nie wygasła.

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu, musisz mieć przypisane uprawnienia Microsoft 365 Defender portalu administracyjnego:
  - **Nadawcy, adresy URL i pliki**:
    - Aby dodawać i usuwać wartości z listy ról Zezwalaj/Blokuj dzierżawy, musisz być członkiem grup ról Zarządzanie **organizacją,** **Administrator** zabezpieczeń lub **Operator** zabezpieczeń albo mieć przypisaną rolę **Menedżer allowBlockList dzierżawy** .
    - Aby uzyskać dostęp tylko do odczytu do listy zablokowanych/zezwalanych na dzierżawę, musisz być członkiem  grup ról Czytnik globalny lub **Czytnik** zabezpieczeń.
  - **Fałszowanie**: jedna z następujących kombinacji:
    - **Zarządzanie organizacją**
    - **Administrator zabezpieczeń** <u>i</u> **konfiguracja tylko do wyświetlania** lub **zarządzanie organizacją tylko do odczytu**.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  >
  > - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

## <a name="configure-the-tenant-allowblock-list"></a>Konfigurowanie listy zezwalania/blokowania dzierżawy

### <a name="use-the-microsoft-365-defender-portal"></a>Korzystanie z Microsoft 365 Defender a

W portalu Microsoft 365 Defender przejdź <https://security.microsoft.com>do **strony Zasady i & zasady** \>  \> dotyczące zagrożeń na listach **zezwalania/** blokowania dzierżawy w **sekcji** Reguły. Aby przejść bezpośrednio do strony **Listy zezwalań/** zablokowanych dzierżaw, użyj .<https://security.microsoft.com/tenantAllowBlockList>

Aby dodać wszystkie bloki, zobacz [Dodawanie bloków na liście zezwalania/blokowania dzierżawy](manage-tenant-blocks.md).

Aby dodać wszystkie zezwalają, zobacz [Dodawanie zezwala na na liście zezwalania/blokowania dzierżawy](manage-tenant-allows.md).

Aby zmodyfikować i usunąć wszystkie bloki i zezwalają, zobacz [Modyfikowanie i usuwanie wpisów na liście zezwalania/blokowania dzierżawy](modify-remove-entries-tenant-allow-block.md).

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Używanie Exchange Online PowerShell lub autonomicznego programu PowerShell usługi EOP

Aby zarządzać wszystkimi zezwalaniami i blokami, zobacz Dodawanie bloków na liście zezwalania [/](manage-tenant-blocks.md)blokowania dzierżawy, dodawanie zezwala na nie na liście zezwalania [/](manage-tenant-allows.md)blokowania dzierżawy oraz Modyfikowanie i usuwanie wpisów na liście zezwalania [/blokowania dzierżawy](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Wyświetlanie wpisów na liście zezwalania/blokowania dzierżawy

1. W portalu Microsoft 365 Defender przejdź <https://security.microsoft.com>do **strony Zasady i & zasady** \>  \> dotyczące zagrożeń na listach **zezwalania/** blokowania dzierżawy w **sekcji** Reguły. Aby przejść bezpośrednio do strony **Listy zezwalań/** zablokowanych dzierżaw, użyj .<https://security.microsoft.com/tenantAllowBlockList>

2. Wybierz kartę. Dostępne kolumny zależą od wybranej karty:

   - **Nadawcy**:
     - **Wartość**: domena lub adres e-mail nadawcy.
     - **Akcja**: Wartość **Zezwalaj lub** **Zablokuj**.
     - **Ostatnia aktualizacja**
     - **Usuń w dniu**
     - **Uwagi**
   - **Adresy URL**:
     - **Wartość**: adres URL.
     - **Akcja**: Wartość **Zezwalaj lub** **Zablokuj**.
     - **Ostatnia aktualizacja**
     - **Usuń w dniu**
     - **Uwagi**
   - **Pliki**
     - **Wartość**: skrót pliku.
     - **Akcja**: Wartość **Zezwalaj lub** **Zablokuj**.
     - **Ostatnia aktualizacja**
     - **Usuń w dniu**
     - **Uwagi**
   - **Fałszowanie**
     - **Fałszywy użytkownik**
     - **Infrastruktura wysyłania**
     - **Spoof type (Fałsz**): Wartość **Wewnętrzna** lub **Zewnętrzna**.
     - **Akcja**: Wartość **Blokuj lub** **Zezwalaj**.

   Możesz kliknąć nagłówek kolumny, aby posortować kolumnę w kolejności rosnącej lub malejącej.

   Możesz kliknąć pozycję **Grupuj,** aby pogrupować wyniki. Dostępne wartości zależą od wybranej karty:

   - **Nadawcy**: Wyniki można grupowania według **akcji**.
   - **Adresy URL**: Wyniki można grupowania według **akcji**.
   - **Pliki**: Wyniki można grupowania **według akcji**.
   - **Fałszowanie**: Wyniki można grupowania według **typu** Akcja lub **Fałsz**.

   Kliknij **przycisk** Wyszukaj, wprowadź całą wartość lub jej część, a następnie naciśnij klawisz ENTER, aby znaleźć określoną wartość. Po zakończeniu kliknij ikonę ![Wyczyść wyszukiwanie.](../../media/m365-cc-sc-close-icon.png) **Wyczyść wyszukiwanie**.

   Kliknij **pozycję Filtruj** , aby przefiltrować wyniki. Wartości dostępne w **wysuwanych opcjach Filtruj** zależą od wybranej karty:

   - **Nadawcy**
     - **Akcja**
     - **Nigdy nie wygasają**
     - **Data ostatniej aktualizacji**
     - **Usuń w dniu**
   - **Adresy URL**
     - **Akcja**
     - **Nigdy nie wygasają**
     - **Data ostatniej aktualizacji**
     - **Usuń w dniu**
   - **Pliki**
     - **Akcja**
     - **Nigdy nie wygasają**
     - **Ostatnia aktualizacja**
     - **Usuń w dniu**
   - **Fałszowanie**
     - **Akcja**
     - **Typ fałsz**

   Po zakończeniu kliknij przycisk **Zastosuj**. Aby wyczyścić istniejące filtry, **kliknij pozycję Filtruj**, a następnie w wyświetlonym **wysuwanych** czacie filtru kliknij pozycję **Wyczyść filtry**.

4. Po zakończeniu kliknij przycisk **Dodaj**.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>Wyświetlanie wpisów nadawcy, pliku lub adresu URL na liście zezwalania/blokowania dzierżawy

Aby wyświetlić wpisy zablokowanych nadawców, plików i adresów URL na liście zezwalania/blokowania dzierżawy, użyj następującej składni:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

W tym przykładzie są zwracane informacje dla określonej wartości skrótu pliku.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

W tym przykładzie są zwracane wszystkie zablokowane adresy URL.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>Wyświetlanie fałszywych wpisów nadawców

Aby wyświetlić fałszywych nadawców na liście zezwalania/blokowania dzierżawy, użyj następującej składni:

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

W tym przykładzie zwracane są wszystkie sfałszowane wpisy nadawców na liście zezwalania/blokowania dzierżawy.

```powershell
Get-TenantAllowBlockListSpoofItems
```

W tym przykładzie zwracane są wszystkie wewnętrzne wpisy fałszywych nadawców.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

W tym przykładzie zwracane są wszystkie zewnętrzne wpisy zablokowanych sfałszowanych nadawców.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>Składnia adresu URL dla listy zezwalania/blokowania dzierżawy

- Adresy IP4v i IPv6 są dozwolone, ale porty TCP/UDP nie są.

- Rozszerzenia filename nie są dozwolone (na przykład test.pdf).

- Standard Unicode nie jest obsługiwany, ale kod punycode jest obsługiwany.

- Nazwy hostów są dozwolone, jeśli wszystkie z następujących instrukcji są prawdziwe:
  - Nazwa hosta zawiera okres.
  - Z lewej strony okresu jest co najmniej jeden znak.
  - Z prawej strony okresu znajdują się co najmniej dwa znaki.

  Na przykład jest `t.co` dozwolone lub `.com` `contoso.` niedozwolone.

- Subpaths are not implied for allows.

  Na przykład nie `contoso.com` zawiera .`contoso.com/a`

- Symbole wieloznaczne (*) są dozwolone w następujących scenariuszach:

  - Po lewej stronie symbolu wieloznacznego musi być określony okres, aby określić poddomenę.

    Na przykład jest `*.contoso.com` dozwolone; `*contoso.com` niedozwolone.

  - Aby określić ścieżkę, prawy symbol wieloznaczny musi znajdować się po ukośniku (/).

    Na przykład jest `contoso.com/*` dozwolone lub `contoso.com*` `contoso.com/ab*` niedozwolone.

  - `*.com*` jest nieprawidłowa (nie można jej rozwiązać, a prawy symbol wieloznaczny nie powoduje pomiń ukośnika).

  - Symbole wieloznaczne nie są dozwolone w adresach IP.

- Tylda (~) jest dostępna w następujących scenariuszach:

  - Po lewej stronie tylda oznacza domenę i wszystkie poddomeny.

    Na przykład zawiera `~contoso.com` `contoso.com` i `*.contoso.com`.

- Wpisy adresów URL zawierające protokoły (na `http://`przykład : , `https://`lub `ftp://`) nie powiodą się, ponieważ wpisy adresów URL mają zastosowanie do wszystkich protokołów.

- Nazwa użytkownika lub hasło nie są obsługiwane lub nie są wymagane.

- Cudzysłowy (' lub ") są nieprawidłowymi znakami.

- Adres URL powinien zawierać, o ile to możliwe, wszystkie przekierowania.

### <a name="url-entry-scenarios"></a>Scenariusze wprowadzania adresu URL

Prawidłowe wpisy adresów URL i ich wyniki opisano w poniższych sekcjach.

#### <a name="scenario-no-wildcards"></a>Scenariusz: Brak symboli wieloznacznych

**Wpis**: `contoso.com`

- **Zezwalaj na contoso.com**

- **Zezwalaj na nie dopasowano**:

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Dopasowanie bloku**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Blokuj, który nie jest pasowany**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scenariusz: Symbol wieloznaczny Left (poddomena)

**Wpis**: `*.contoso.com`

- **Zezwalaj na dopasowanie** **i blokowanie dopasowań**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **Zezwalaj na nie dopasowano** i **Nie dopasowano bloku**:

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scenariusz: prawy symbol wieloznaczny u góry ścieżki

**Wpis**: `contoso.com/a/*`

- **Zezwalaj na dopasowanie** **i blokowanie dopasowań**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Zezwalaj na nie dopasowano** i **Nie dopasowano bloku**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Scenariusz: tylda po lewej stronie

**Wpis**: `~contoso.com`

- **Zezwalaj na dopasowanie** **i blokowanie dopasowań**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **Zezwalaj na nie dopasowano** i **Nie dopasowano bloku**:

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Scenariusz: prawy sufiks z symbolami wieloznacznymi

**Wpis**: `contoso.com/*`

- **Zezwalaj na dopasowanie** **i blokowanie dopasowań**:

  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **Zezwalaj na nie dopasowaną i** **Nie dopasowano bloku**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Scenariusz: lewa poddomena z symbolami wieloznacznymi i prawy sufiks z symbolami wieloznacznych

**Wpis**: `*.contoso.com/*`

- **Zezwalaj na dopasowanie** **i blokowanie dopasowań**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Zezwalaj na nie dopasowaną i** **Nie dopasowano bloku**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scenariusz: tylda po lewej i prawej

**Wpis**: `~contoso.com~`

- **Zezwalaj na dopasowanie** **i blokowanie dopasowań**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **Zezwalaj na nie dopasowano** i **Nie dopasowano bloku**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Scenariusz: adres IP

**Wpis**: `1.2.3.4`

- **Zezwalaj na** dopasowanie **i dopasowanie bloku**: 1.2.3.4

- **Zezwalaj na nie dopasowano** i **Nie dopasowano bloku**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>Adres IP z prawym symbole wieloznaczne

**Wpis**: `1.2.3.4/*`

- **Zezwalaj na dopasowanie** **i blokowanie dopasowań**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>Przykłady nieprawidłowych wpisów

Nieprawidłowe są następujące wpisy:

- **Brakujące lub nieprawidłowe wartości domeny**:

  - contoso
  - \*contoso.\*
  - \*com
  - \*.pdf

- **Symbol wieloznaczny w tekście lub bez znaków odstępów**:

  - \*contoso.com
  - contoso.com\*
  - \*1.2.3.4
  - 1.2.3.4\*
  - contoso.com/a\*
  - contoso.com/ab\*

- **Adresy IP z portami**:

  - contoso.com:443
  - abc.contoso.com:25

- **Nieopisowe symbole wieloznaczne**:

  - \*
  - \*.\*

- **Symbole wieloznaczne w środku**:

  - conto\* so.com
  - conto~so.com

- **Podwójne symbole wieloznaczne**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>Składnia pary domen dla fałszywych nadawców na liście zezwalania/blokowania dzierżawy

Para domeny dla fałszywego nadawcy na liście zezwalania/blokowania dzierżawy ma następującą składnię: `<Spoofed user>, <Sending infrastructure>`.

- **Fałszywy użytkownik**: Ta wartość obejmuje adres e-mail fałszywego użytkownika wyświetlany w polu Od w klientach poczty e-mail. Ten adres jest również nazywany adresem `5322.From` . Prawidłowe wartości to:
  - Indywidualny adres e-mail (na przykład chris@contoso.com).
  - Domena poczty e-mail (na przykład contoso.com).
  - Symbol wieloznaczny (na przykład \*).

- **Infrastruktura wysyłania**: Ta wartość wskazuje źródło wiadomości od fałszywego użytkownika. Prawidłowe wartości to:
  - Domena znaleziona w odwrotnym odnośniku DNS (rekord PTR) adresu IP źródłowego serwera poczty e-mail (na przykład fabrikam.com).
  - Jeśli źródłowy adres IP nie ma rekordu PTR, \<source IP\>wówczas infrastruktura wysyłania jest identyfikowana jako /24 (na przykład 192.168.100.100/24).

Oto kilka przykładów prawidłowych par domen do identyfikowania fałszywych nadawców:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Maksymalna liczba fałszywych wpisów nadawców wynosi 1000.

Dodanie pary domeny umożliwia lub blokuje tylko połączenie fałszywego użytkownika *i infrastruktury wysyłania*. Nie zezwala na wiadomości e-mail od sfałszowanych użytkowników z żadnego źródła, ani nie zezwala na pocztę e-mail ze źródła infrastruktury wysyłania dla dowolnego sfałszowaego użytkownika. 

Na przykład możesz dodać wpis zezwalania dla następującej pary domen:

- **Domena**: gmail.com
- **Infrastruktura**: tms.mx.com

Spoofem mogą być  tylko wiadomości z tej domeny i pary infrastruktury wysyłania. Inni nadawcy próbujący fałszować gmail.com są niedozwolone. Wiadomości od nadawców z innych domen pochodzących z tms.mx.com są sprawdzane przez analizę fałszowania.
