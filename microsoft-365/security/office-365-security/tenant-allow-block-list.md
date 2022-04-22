---
title: Zarządzanie zezwoleniami i blokami na liście dozwolonych/zablokowanych dzierżaw
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
description: Administratorzy mogą dowiedzieć się, jak zarządzać zezwoleniami i blokami na liście dozwolonych/zablokowanych dzierżaw w portalu zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0ed23cf7bfe8db25ed216859c434e86f14710db8
ms.sourcegitcommit: 363bdc517bd2564c6420cf21f352e97079f950e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2022
ms.locfileid: "65031846"
---
# <a name="manage-the-tenant-allowblock-list"></a>Zarządzanie listą dozwolonych/zablokowanych dzierżaw

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> Niektóre funkcje opisane w tym artykule są w wersji zapoznawczej, mogą ulec zmianie i nie są dostępne we wszystkich organizacjach.
>
> Jeśli Twoja organizacja nie ma funkcji fałszowania zgodnie z opisem w tym artykule, zobacz starsze środowisko zarządzania fałszowaniem w [temacie Manage spoofed senders using the spoof intelligence policy and spoof intelligence insight in EOP (Zarządzanie fałszowaniem nadawców przy użyciu zasad analizy fałszowania i fałszowanie analizy w ramach EOP](walkthrough-spoof-intelligence-insight.md)).

W Microsoft 365 organizacji ze skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacji Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, możesz nie zgodzić się z werdyktem filtrowania EOP. Na przykład dobra wiadomość może zostać oznaczona jako zła (fałszywie dodatnia) lub zła wiadomość może zostać przepuszczona (fałszywie ujemna).

Lista dozwolonych/zablokowanych dzierżaw w portalu Microsoft 365 Defender umożliwia ręczne zastąpienie Microsoft 365 filtrowania werdyktów. Lista zezwalania/blokowania dzierżawy jest używana podczas przepływu poczty dla wiadomości przychodzących (nie dotyczy wiadomości wewnątrz organizacji) i w momencie kliknięcia przez użytkownika. Można określić następujące typy przesłonięcia:

- Adresy URL do zablokowania.
- Pliki do zablokowania.
- Wiadomości e-mail lub domeny nadawcy do zablokowania.
- Spoofed nadawców, aby zezwolić lub zablokować. Jeśli przesłonisz werdykt zezwalania lub blokowania w [analizie analizy fałszowania](learn-about-spoof-intelligence.md), sfałszowany nadawca staje się ręcznym wpisem zezwalającym lub blokowym, który pojawia się tylko na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżaw. Możesz również ręcznie utworzyć wpisy zezwalania lub blokowania dla sfałszowanych nadawców w tym miejscu, zanim zostaną wykryte przez analizę fałszowania.
- Adresy URL do zezwolenia.
- Pliki, które mają być dozwolone.
- Wysyłanie wiadomości e-mail lub domen nadawcy do zezwolenia.

W tym artykule opisano sposób konfigurowania wpisów na liście dozwolonych/zablokowanych dzierżaw w portalu Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomiczny program PowerShell EOP dla organizacji bez Exchange Online skrzynki pocztowe).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zezwalaj/blokuj listy dzierżawy** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList>.

- Pliki można określić przy użyciu wartości skrótu SHA256 pliku. Aby znaleźć wartość skrótu SHA256 pliku w Windows, uruchom następujące polecenie w wierszu polecenia:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Przykładowa wartość to `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Wartości skrótu perceptualnego (pHash) nie są obsługiwane.

- Dostępne wartości adresu URL są opisane w [składni adresu URL dla sekcji Zezwalanie na dzierżawę/Lista zablokowanych w dalszej](#url-syntax-for-the-tenant-allowblock-list) części tego artykułu.

- Lista dozwolonych/blokowych dzierżawy zezwala na maksymalnie 500 wpisów dla nadawców, 500 wpisów adresów URL, 500 wpisów skrótów plików i 1024 wpisy na potrzeby fałszowania (sfałszowanych nadawców).

- Maksymalna liczba znaków dla każdego wpisu to:
  - Skróty plików = 64
  - Adres URL = 250

- Wpis powinien być aktywny w ciągu 30 minut.

- Domyślnie wpisy na liście zezwalania/blokowania dzierżawy wygasają po 30 dniach. Możesz określić datę lub ustawić ją tak, aby nigdy nie wygasały.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w portalu Microsoft 365 Defender:
  - **Nadawcy, adresy URL i pliki**:
    - Aby dodać i usunąć wartości z listy dozwolonych/zablokowanych dzierżaw, musisz być członkiem 
      -   **Zarządzanie organizacją** lub grupa ról **administratora zabezpieczeń** (**rola administratora zabezpieczeń**)
      -    Grupa ról **operatora zabezpieczeń** (**Menedżer AllowBlockList dzierżawy**).
    - Aby uzyskać dostęp tylko do odczytu do listy dozwolonych/zablokowanych dzierżaw, musisz być członkiem 
      - **Globalna grupa ról czytelnika**
      - Grupa ról **czytelnika zabezpieczeń**
  - **Fałszowanie**: jedna z następujących kombinacji:
    - **Zarządzanie organizacją**
    - **Administrator zabezpieczeń** <u>i</u> **konfiguracja tylko do wyświetlania** lub **zarządzanie organizacją tylko do wyświetlania**.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  >
  > - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

## <a name="configure-the-tenant-allowblock-list"></a>Konfigurowanie listy dozwolonych/zablokowanych dzierżaw

### <a name="use-the-microsoft-365-defender-portal"></a>Korzystanie z portalu Microsoft 365 Defender

W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Zasady & reguły** \> zasad \> **zagrożeń** **Zezwalaj na dzierżawę/blokuj listy** w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zezwalaj/blokuj listy dzierżawy** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList>.

Aby dodać wszystkie bloki, zobacz [Dodawanie bloków na liście zezwalania/blokowania dzierżawy](manage-tenant-blocks.md).

Aby dodać wszystkie opcje zezwala, zobacz [Dodawanie dozwolonych na liście dozwolonych/zablokowanych dzierżaw](manage-tenant-allows.md).

Aby zmodyfikować i usunąć wszystkie bloki i zezwolenia, zobacz [Modyfikowanie i usuwanie wpisów na liście dozwolonych/zablokowanych dzierżaw](modify-remove-entries-tenant-allow-block.md).

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Używanie Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP

Aby zarządzać wszystkimi zezwoleniami i blokami, zobacz [Dodawanie bloków na liście dozwolonych/zablokowanych dzierżaw](manage-tenant-blocks.md), [Dodawanie dozwolonych elementów na liście dozwolonych/zablokowanych dzierżaw](manage-tenant-allows.md) oraz [Modyfikowanie i usuwanie wpisów na liście dozwolonych/zablokowanych dzierżawców](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Wyświetlanie wpisów na liście dozwolonych/zablokowanych dzierżaw

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Zasady & reguły** \> zasad \> **zagrożeń** **Zezwalaj na dzierżawę/blokuj listy** w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zezwalaj/blokuj listy dzierżawy** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList>.

2. Wybierz odpowiednią kartę. Dostępne kolumny zależą od wybranej karty:

   - **Nadawcy**:
     - **Wartość**: domena nadawcy lub adres e-mail.
     - **Akcja**: wartość **Zezwalaj** lub **Blokuj**.
     - **Zmodyfikowane przez**
     - **Ostatnia aktualizacja**
     - **Usuń przy**
     - **Uwagi**
   - **Adresy URL**:
     - **Wartość**: adres URL.
     - **Akcja**: wartość **Zezwalaj** lub **Blokuj**.
     - **Zmodyfikowane przez**
     - **Ostatnia aktualizacja**
     - **Usuń przy**
     - **Uwagi**
   - **Pliki**
     - **Wartość**: skrót pliku.
     - **Akcja**: wartość **Zezwalaj** lub **Blokuj**.
     - **Zmodyfikowane przez**
     - **Ostatnia aktualizacja**
     - **Usuń przy**
     - **Uwagi**
   - **Fałszowanie**
     - **Sfałszowany użytkownik**
     - **Wysyłanie infrastruktury**
     - **Typ fałszowania**: wartość **Wewnętrzna** lub **Zewnętrzna**.
     - **Akcja**: wartość **Blokuj** lub **Zezwalaj**.

   Możesz kliknąć nagłówek kolumny, aby posortować w kolejności rosnącej lub malejącej.

   Możesz kliknąć pozycję **Grupuj** , aby pogrupować wyniki. Dostępne wartości zależą od wybranej karty:

   - **Nadawcy**: wyniki można grupować według **akcji**.
   - **Adresy URL**: wyniki można grupować według **akcji**.
   - **Pliki**: wyniki można grupować według **akcji**.
   - **Fałszowanie**: wyniki można grupować według typu **Akcja** lub **Fałszowanie**.

   Kliknij **pozycję Wyszukaj**, wprowadź całość lub część wartości, a następnie naciśnij klawisz ENTER, aby znaleźć określoną wartość. Po zakończeniu kliknij pozycję ![Wyczyść ikonę wyszukiwania.](../../media/m365-cc-sc-close-icon.png) **Wyczyść wyszukiwanie**.

   Kliknij **pozycję Filtruj** , aby filtrować wyniki. Wartości dostępne w wyświetlonym **wysuwu filtru** zależą od wybranej karty:

   - **Nadawców**
     - **Akcja**
     - **Nigdy nie wygasaj**
     - **Data ostatniej aktualizacji**
     - **Usuń przy**
   - **Adresy url**
     - **Akcja**
     - **Nigdy nie wygasaj**
     - **Data ostatniej aktualizacji**
     - **Usuń przy**
   - **Pliki**
     - **Akcja**
     - **Nigdy nie wygasaj**
     - **Ostatnia aktualizacja**
     - **Usuń przy**
   - **Fałszowanie**
     - **Akcja**
     - **Typ fałszowania**

   Po zakończeniu kliknij przycisk **Zastosuj**. Aby wyczyścić istniejące filtry, kliknij pozycję **Filtruj**, a następnie w wyświetlonym wysuwu **Filtr** kliknij pozycję **Wyczyść filtry**.

4. Po zakończeniu kliknij przycisk **Dodaj**.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>Wyświetlanie wpisów nadawcy, pliku lub adresu URL na liście dozwolonych/zablokowanych dzierżaw

Aby wyświetlić wpisy nadawcy bloku, pliku lub adresu URL na liście dozwolonych/zablokowanych dzierżawców, użyj następującej składni:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

Ten przykład zwraca informacje o określonej wartości skrótu pliku.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Ten przykład zwraca wszystkie zablokowane adresy URL.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>Wyświetlanie fałszywych wpisów nadawcy

Aby wyświetlić sfałszowane wpisy nadawcy na liście dozwolonych/zablokowanych dzierżaw, użyj następującej składni:

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

Ten przykład zwraca wszystkie sfałszowane wpisy nadawcy na liście Zezwalaj/Blokuj dzierżawę.

```powershell
Get-TenantAllowBlockListSpoofItems
```

Ten przykład zwraca wszystkie wewnętrzne wpisy nadawcy zezwalające na sfałszowane wpisy nadawcy.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

Ten przykład zwraca wszystkie zablokowane sfałszowane wpisy nadawcy, które są zewnętrzne.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>Składnia adresu URL listy dozwolonych/zablokowanych dzierżaw

- Adresy IPv4 i IPv6 są dozwolone, ale porty TCP/UDP nie są.

- Rozszerzenia nazw plików są niedozwolone (na przykład test.pdf).

- Unicode nie jest obsługiwane, ale punycode jest.

- Nazwy hostów są dozwolone, jeśli wszystkie następujące instrukcje są prawdziwe:
  - Nazwa hosta zawiera kropkę.
  - Po lewej stronie kropki znajduje się co najmniej jeden znak.
  - Po prawej stronie okresu znajdują się co najmniej dwa znaki.

  Na przykład `t.co` jest dozwolone lub `.com` `contoso.` niedozwolone.

- Ścieżki podrzędne nie są dorozumiane w przypadku zezwalania.

  Na przykład `contoso.com` nie zawiera elementu `contoso.com/a`.

- Symbole wieloznaczne (*) są dozwolone w następujących scenariuszach:

  - Po lewym symbolu wieloznacznym musi następować kropka określająca poddomenę.

    Na przykład `*.contoso.com` jest dozwolone; `*contoso.com` jest niedozwolone.

  - Aby określić ścieżkę, prawy symbol wieloznaczny musi być zgodny z ukośnikiem (/).

    Na przykład `contoso.com/*` jest dozwolone lub `contoso.com*` `contoso.com/ab*` niedozwolone.

  - `*.com*` jest nieprawidłowa (nie jest to domena rozpoznawalna, a prawy symbol wieloznaczny nie podąża za ukośnikiem).

  - Symbole wieloznaczne nie są dozwolone w adresach IP.

- Znak kafelka (~) jest dostępny w następujących scenariuszach:

  - Lewy kafelek oznacza domenę i wszystkie poddomeny.

    Na przykład `~contoso.com` obejmuje `contoso.com` i `*.contoso.com`.

- Wpisy adresów URL zawierające protokoły (na przykład `http://`, `https://`lub `ftp://`) nie powiedzie się, ponieważ wpisy adresu URL mają zastosowanie do wszystkich protokołów.

- Nazwa użytkownika lub hasło nie są obsługiwane ani wymagane.

- Cudzysłowy (' lub ") są nieprawidłowymi znakami.

- Adres URL powinien zawierać wszystkie przekierowania tam, gdzie to możliwe.

### <a name="url-entry-scenarios"></a>Scenariusze wpisu adresu URL

Prawidłowe wpisy adresów URL i ich wyniki są opisane w poniższych sekcjach.

#### <a name="scenario-no-wildcards"></a>Scenariusz: Brak symboli wieloznacznych

**Wpis**: `contoso.com`

- **Zezwalaj na dopasowanie**: contoso.com

- **Nie dopasuj zezwalaj**:

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Blokuj dopasowanie**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Nie dopasuj blokuj**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scenariusz: Symbol wieloznaczny z lewej (poddomena)

**Wpis**: `*.contoso.com`

- **Zezwalaj na dopasowanie** i **blokuj dopasowanie**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **Nie dopasuj opcji Zezwalaj** i **Blokuj nie dopasuj**:

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scenariusz: symbol wieloznaczny z prawej strony u góry ścieżki

**Wpis**: `contoso.com/a/*`

- **Zezwalaj na dopasowanie** i **blokuj dopasowanie**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Nie dopasuj opcji Zezwalaj** i **Blokuj nie dopasuj**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Scenariusz: Lewy kafelek

**Wpis**: `~contoso.com`

- **Zezwalaj na dopasowanie** i **blokuj dopasowanie**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **Nie dopasuj opcji Zezwalaj** i **Blokuj nie dopasuj**:

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Scenariusz: Sufiks z prawej symboli wieloznaczny

**Wpis**: `contoso.com/*`

- **Zezwalaj na dopasowanie** i **blokuj dopasowanie**:

  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **Pozycja Zezwalaj nie jest dopasowana** i **nie dopasuj blokuj**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Scenariusz: Lewa poddomena wieloznaczna i sufiks z prawej symboli wieloznaczowych

**Wpis**: `*.contoso.com/*`

- **Zezwalaj na dopasowanie** i **blokuj dopasowanie**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Pozycja Zezwalaj nie jest dopasowana** i **Blokuj nie jest dopasowana**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scenariusz: lewy i prawy kafelek

**Wpis**: `~contoso.com~`

- **Zezwalaj na dopasowanie** i **blokuj dopasowanie**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **Nie dopasuj opcji Zezwalaj** i **Blokuj nie dopasuj**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Scenariusz: adres IP

**Wpis**: `1.2.3.4`

- **Zezwalaj na dopasowanie** i **blokuj dopasowanie**: 1.2.3.4

- **Nie dopasuj opcji Zezwalaj** i **Blokuj nie dopasuj**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>Adres IP z prawą symbolem wieloznacznym

**Wpis**: `1.2.3.4/*`

- **Zezwalaj na dopasowanie** i **blokuj dopasowanie**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>Przykłady nieprawidłowych wpisów

Następujące wpisy są nieprawidłowe:

- **Brakujące lub nieprawidłowe wartości domeny**:

  - Contoso
  - \*.contoso.\*
  - \*.com
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

- **Symbole wieloznaczne bez opisu**:

  - \*
  - \*.\*

- **Symbole wieloznaczne środkowe**:

  - conto\* so.com
  - conto~so.com

- **Podwójne symbole wieloznaczne**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>Składnia pary domeny dla sfałszowanych wpisów nadawcy na liście zezwalania/blokowania dzierżawy

Para domeny dla sfałszowanego nadawcy na liście dozwolonych/blokowych dzierżawy używa następującej składni: `<Spoofed user>, <Sending infrastructure>`.

- **Sfałszowany użytkownik**: ta wartość obejmuje adres e-mail sfałszowanego użytkownika, który jest wyświetlany w polu **Od** w klientach poczty e-mail. Ten adres jest również znany jako `5322.From` adres. Prawidłowe wartości obejmują:
  - Indywidualny adres e-mail (na przykład chris@contoso.com).
  - Domena poczty e-mail (na przykład contoso.com).
  - Symbol wieloznaczny (na przykład \*).

- **Wysyłanie infrastruktury**: ta wartość wskazuje źródło komunikatów od sfałszowanego użytkownika. Prawidłowe wartości obejmują:
  - Domena znaleziona w odwrotnym wyszukiwaniu DNS (rekord PTR) adresu IP źródłowego serwera poczty e-mail (na przykład fabrikam.com).
  - Jeśli źródłowy adres IP nie ma rekordu PTR, infrastruktura wysyłania jest identyfikowana jako \<source IP\>/24 (na przykład 192.168.100.100/24).

Oto kilka przykładów prawidłowych par domen do identyfikowania sfałszowanych nadawców:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Maksymalna liczba fałszywych wpisów nadawcy wynosi 1000.

Dodanie pary domeny umożliwia lub blokuje *tylko kombinację* sfałszowanego użytkownika *i* infrastruktury wysyłania. Nie zezwala na wysyłanie wiadomości e-mail od sfałszowanego użytkownika z żadnego źródła ani nie zezwala na wysyłanie wiadomości e-mail ze źródła infrastruktury wysyłania dla żadnego sfałszowanego użytkownika. 

Możesz na przykład dodać wpis zezwalania dla następującej pary domen:

- **Domena**: gmail.com
- **Infrastruktura**: tms.mx.com

Tylko komunikaty z tej domeny *i* wysyłanie pary infrastruktury mogą się fałszować. Inni nadawcy próbujący podszywać się pod gmail.com nie są dozwolone. Komunikaty od nadawców w innych domenach pochodzących z tms.mx.com są sprawdzane przez analizę fałszowania.
