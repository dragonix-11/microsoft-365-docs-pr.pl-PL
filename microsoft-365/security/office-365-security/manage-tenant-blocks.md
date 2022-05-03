---
title: Zarządzanie blokami na liście dozwolonych/zablokowanych dzierżaw
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak skonfigurować bloki na liście dozwolonych/zablokowanych dzierżaw w portalu zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 03c56e5e7e540766bb4a6048fba15b494c46d815
ms.sourcegitcommit: 4d6a8e9d69a421d6c293b2485a8aa5e806b71616
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65182722"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>Dodawanie blokad na liście dozwolonych/zablokowanych dzierżaw

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>Korzystanie z portalu Microsoft 365 Defender

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>Tworzenie wpisów nadawcy bloku na liście dozwolonych/zablokowanych dzierżaw

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do sekcji **Zasady, & reguły zasad** \> **zagrożeń** \> **,** sekcja \> **Zezwalaj/blokuj listy dzierżawy**. Możesz też przejść bezpośrednio do strony **Zezwalaj/blokuj listę dzierżawy** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList>.

2. Na stronie **Lista dozwolonych/zablokowanych dzierżawy** sprawdź, czy wybrano kartę **Nadawcy** , a następnie kliknij ikonę ![Blokuj.](../../media/m365-cc-sc-create-icon.png) **Blokuj**.

3. W wyświetlonym wysuwu **Blokuj nadawców** skonfiguruj następujące ustawienia:
   - **Adresy e-mail nadawcy lub domeny**: wprowadź jeden nadawca (adres e-mail lub domenę) na wiersz, maksymalnie 20.
   - **Nigdy nie wygasaj**: Wykonaj jedną z następujących czynności:
     - Sprawdź, czy ustawienie jest wyłączone (![Przełącz wyłączone](../../media/scc-toggle-off.png)) i użyj pola **Usuń włączone** , aby określić datę wygaśnięcia wpisów.

       lub

     - Przenieś przełącznik w prawo, aby skonfigurować wpisy tak, aby nigdy nie wygasały: ![Przełącz wł.](../../media/scc-toggle-on.png).
   - **Opcjonalna uwaga**: wprowadź opisowy tekst dla wpisów.

4. Po zakończeniu kliknij przycisk **Dodaj**.

> [!NOTE]
> Wiadomości e-mail od tych nadawców zostaną zablokowane jako _spam o wysokim poziomie zaufania_ (SCL = 9).

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Tworzenie wpisów bloku adresu URL na liście dozwolonych/zablokowanych dzierżaw

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do sekcji **Zasady, & reguły zasad** \> **zagrożeń** \> **,** sekcja \> **Zezwalaj/blokuj listy dzierżawy**. Możesz też przejść bezpośrednio do strony **Zezwalaj/blokuj listę dzierżawy** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList>.

2. Na stronie **Lista dozwolonych/zablokowanych dzierżawy** sprawdź, czy wybrano kartę **Adresy URL** , a następnie kliknij pozycję Blokuj ikonę ![.](../../media/m365-cc-sc-create-icon.png) **Blokuj**.

3. W wyświetlonym wysuwu **Blokuj adresy URL** skonfiguruj następujące ustawienia:
   - **Dodaj adresy URL z symbolami wieloznaczowymi**: wprowadź jeden adres URL na wiersz, maksymalnie 20. Aby uzyskać szczegółowe informacje na temat składni wpisów adresów URL, zobacz sekcję Składnia adresu URL w [temacie Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md).
   - **Nigdy nie wygasaj**: Wykonaj jedną z następujących czynności:
     - Sprawdź, czy ustawienie jest wyłączone (![Przełącz wyłączone](../../media/scc-toggle-off.png)) i użyj pola **Usuń włączone** , aby określić datę wygaśnięcia wpisów.

       lub

     - Przenieś przełącznik w prawo, aby skonfigurować wpisy tak, aby nigdy nie wygasały: ![Przełącz wł.](../../media/scc-toggle-on.png).
   - **Opcjonalna uwaga**: wprowadź opisowy tekst dla wpisów.

4. Po zakończeniu kliknij przycisk **Dodaj**.

> [!NOTE]
> Wiadomości e-mail zawierające te adresy URL zostaną zablokowane jako _phish_.

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>Tworzenie wpisów pliku blokowego na liście dozwolonych/zablokowanych dzierżaw

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do sekcji **Zasady, & reguły zasad** \> **zagrożeń** \> **,** sekcja \> **Zezwalaj/blokuj listy dzierżawy**. Możesz też przejść bezpośrednio do strony **Zezwalaj/blokuj listę dzierżawy** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList>.

2. Na stronie **Lista dozwolonych/blokowych dzierżawy** wybierz kartę **Pliki** , a następnie kliknij ikonę ![Blokuj.](../../media/m365-cc-sc-create-icon.png) **Blokuj**.

3. W wyświetlonym wysuwu **Blokuj pliki** skonfiguruj następujące ustawienia:
   - **Dodaj skróty plików**: wprowadź jedną wartość skrótu SHA256 na wiersz, maksymalnie do 20.
   - **Nigdy nie wygasaj**: Wykonaj jedną z następujących czynności:
     - Sprawdź, czy ustawienie jest wyłączone (![Przełącz wyłączone](../../media/scc-toggle-off.png)) i użyj pola **Usuń włączone** , aby określić datę wygaśnięcia wpisów.

     lub

     - Przenieś przełącznik w prawo, aby skonfigurować wpisy tak, aby nigdy nie wygasały: ![Przełącz wł.](../../media/scc-toggle-on.png).
   - **Opcjonalna uwaga**: wprowadź opisowy tekst dla wpisów.

4. Po zakończeniu kliknij przycisk **Dodaj**.

> [!NOTE]
> Wiadomości e-mail zawierające te pliki zostaną zablokowane jako _złośliwe oprogramowanie_.

### <a name="create-spoofed-sender-block-entries"></a>Tworzenie sfałszowanych wpisów bloku nadawcy

**Uwagi**:

- Tylko _kombinacja_ sfałszowanego użytkownika _i_ infrastruktury wysyłania zdefiniowanej w parze domeny jest wyraźnie dozwolona lub zablokowana przed fałszowaniem.
- Podczas konfigurowania wpisu zezwalania lub blokowania dla pary domeny komunikaty z tej pary domeny nie są już wyświetlane w szczegółowych informacjach analizy na temat fałszowania.
- Wpisy dla sfałszowanych nadawców nigdy nie wygasają.
- Spoof obsługuje zarówno zezwalanie, jak i blokowanie.

1. W portalu Microsoft 365 Defender przejdź **do sekcji** **Zasady & reguły zasad** \> **zagrożeń** \> w sekcji \> **Zezwalaj/blokuj listy dzierżawy**.

2. Na stronie **Lista dozwolonych/blokowych dzierżawy** wybierz kartę **Fałszowanie** , a następnie kliknij ikonę ![Blokuj.](../../media/m365-cc-sc-create-icon.png) **Dodaj**.

3. W wyświetlonym menu wysuwowym **Dodawanie nowych par domeny** skonfiguruj następujące ustawienia:
   - **Dodaj nowe pary domen z symbolami wieloznacznymi**: wprowadź jedną parę domeny na wiersz, maksymalnie do 20. Aby uzyskać szczegółowe informacje na temat składni fałszywych wpisów nadawcy, zobacz [Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md).
   - **Typ fałszowania**: wybierz jedną z następujących wartości:
     - **Wewnętrzne**: sfałszowany nadawca znajduje się w domenie należącej do Organizacji ( [akceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Zewnętrzne**: sfałszowany nadawca znajduje się w domenie zewnętrznej.
   - **Akcja**: wybierz pozycję **Blokuj**.

4. Po zakończeniu kliknij przycisk **Dodaj**.

> [!NOTE]
> Wiadomości e-mail od tych nadawców zostaną zablokowane jako _phish_.

## <a name="use-powershell"></a>Korzystanie z programu PowerShell

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>Dodawanie pozycji nadawcy blokowego, pliku lub adresu URL do listy dozwolonych/zablokowanych dzierżaw

Aby dodać wpisy nadawcy blokowego, pliku lub adresu URL na liście dozwolonych/zablokowanych dzierżaw, użyj następującej składni:

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

W tym przykładzie dodano wpis nadawcy blokowego dla określonego nadawcy, który wygasa w określonym dniu.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

W tym przykładzie dodano wpis pliku blokowego dla określonych plików, które nigdy nie wygasają.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

W tym przykładzie dodano wpis adresu URL bloku dla contoso.com i wszystkich poddomen (na przykład contoso.com, www.contoso.com i xyz.abc.contoso.com). Ponieważ nie użyto parametrów ExpirationDate lub NoExpiration, wpis wygasa po 30 dniach.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>Dodawanie sfałszowanych wpisów bloku nadawcy

Aby dodać sfałszowane wpisy nadawcy na liście zezwalania/blokowania dzierżawy, użyj następującej składni:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
