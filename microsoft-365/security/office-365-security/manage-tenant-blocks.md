---
title: Zarządzanie blokami na liście zezwalania/blokowania dzierżawy
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
description: Administratorzy mogą dowiedzieć się, jak konfigurować bloki na liście zezwalania/blokowania dzierżawy w portalu zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cb4bdef35928a3a2672c6897676d3c90932bd7ec
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010661"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>Dodawanie bloków na liście zezwalania/blokowania dzierżawy

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>Korzystanie z Microsoft 365 Defender a 

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>Tworzenie wpisów zablokowanych nadawców na liście zezwalania/blokowania dzierżawy

1. W portalu Microsoft 365 Defender przejdź do **sekcji Zasady i reguły &** \>  \> reguły **zagrożeń w sekcji** \> Listy zezwalania **i blokowania** dzierżaw.

2. Na stronie **Lista zablokowanych/zezwalania na dzierżawę** sprawdź, czy wybrano kartę Nadawcy, a następnie kliknij ikonę ![Zablokuj.](../../media/m365-cc-sc-create-icon.png) **Zablokuj**.

3. W **wyświetlonym wysuwu** Blokuj nadawców skonfiguruj następujące ustawienia:
   - **Adresy e-mail lub domeny nadawcy**: Wprowadź jednego nadawcę (adres e-mail lub domenę) w wierszu (maksymalnie 20).
   - **Nigdy nie wygasaj**: Wykonaj jedną z następujących czynności:
     - Sprawdź, czy ustawienie jest wyłączone (![](../../media/scc-toggle-off.png)przełącznik wyłączony) i użyj pola Usuń w, aby określić datę wygaśnięcia wpisów.

       lub

     - Przesuń przełącznik w prawo, aby skonfigurować pozycje tak, aby nigdy nie wygasały: ![Włącz.](../../media/scc-toggle-on.png).
   - **Uwaga opcjonalna**: Wprowadź opisowy tekst wpisów.

4. Po zakończeniu kliknij przycisk **Dodaj**.

> [!NOTE]
> Wiadomości e-mail od tych nadawców zostaną zablokowane jako *spam*. 

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Tworzenie wpisów zablokowanych adresów URL na liście zablokowanych/zezwalanych na dzierżawę

1. W portalu Microsoft 365 Defender przejdź do **sekcji Zasady i reguły &** \>  \> reguły **zagrożeń w sekcji** \> Listy zezwalania **i blokowania** dzierżaw.

2. Na stronie **Lista zablokowanych/zezwalania na dzierżawcę** sprawdź, czy wybrano kartę Adresy **URL** , a następnie kliknij ikonę ![Blokuj.](../../media/m365-cc-sc-create-icon.png) **Zablokuj**.

3. W **wyświetlonym wysuwanych** czacie adresów URL bloku skonfiguruj następujące ustawienia:
   - **Dodawanie adresów URL przy użyciu symboli wieloznacznych**: Wprowadź jeden adres URL w wierszu (maksymalnie 20). Aby uzyskać szczegółowe informacje na temat składni wpisów adresu URL, zobacz sekcję składni adresu URL w sekcji Zarządzanie [listą zezwalania/blokowania dzierżawy](tenant-allow-block-list.md).
   - **Nigdy nie wygasaj**: Wykonaj jedną z następujących czynności:
     - Sprawdź, czy ustawienie jest wyłączone (![](../../media/scc-toggle-off.png)przełącznik wyłączony) i użyj pola Usuń w, aby określić datę wygaśnięcia wpisów.

       lub

     - Przesuń przełącznik w prawo, aby skonfigurować pozycje tak, aby nigdy nie wygasały: ![Włącz.](../../media/scc-toggle-on.png).
   - **Uwaga opcjonalna**: Wprowadź opisowy tekst wpisów.

4. Po zakończeniu kliknij przycisk **Dodaj**.

> [!NOTE]
> Wiadomości e-mail zawierające te adresy URL zostaną zablokowane jako *wiadomości wyłudające*. 

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>Tworzenie zablokowanych wpisów plików na liście zezwalania/blokowania dzierżawy

1. W portalu Microsoft 365 Defender przejdź do **sekcji Zasady i reguły &** \>  \> reguły **zagrożeń w sekcji** \> Listy zezwalania **i blokowania** dzierżaw.

2. Na stronie **Lista zezwalania/blokowania dzierżawy** wybierz **kartę Pliki** , a następnie kliknij ikonę ![Blokuj.](../../media/m365-cc-sc-create-icon.png) **Zablokuj**.

3. W **wyświetlonym wysuwanych** czacie Blokuj pliki skonfiguruj następujące ustawienia:
   - **Dodawanie skrótów plików**: Wprowadź jedną wartość skrótu SHA256 w wierszu (maksymalnie 20).
   - **Nigdy nie wygasaj**: Wykonaj jedną z następujących czynności:
     - Sprawdź, czy ustawienie jest wyłączone (![](../../media/scc-toggle-off.png)przełącznik wyłączony) i użyj pola Usuń w, aby określić datę wygaśnięcia wpisów.

     lub

     - Przesuń przełącznik w prawo, aby skonfigurować pozycje tak, aby nigdy nie wygasały: ![Włącz.](../../media/scc-toggle-on.png).
   - **Uwaga opcjonalna**: Wprowadź opisowy tekst wpisów.

4. Po zakończeniu kliknij przycisk **Dodaj**.

> [!NOTE]
> Wiadomości e-mail zawierające te pliki zostaną zablokowane jako *złośliwe oprogramowanie*. 

### <a name="create-spoofed-sender-block-entries"></a>Tworzenie fałszywych wpisów zablokowanych nadawców

**Uwagi**:

- _Fałszowanie_ jest dozwolone lub blokowane  tylko przez połączenie sfałszowanej infrastruktury nadawczej i użytkownika zdefiniowanego w parach domen.
- Po skonfigurowaniu wpisu zezwalania lub blokowania dla pary domen wiadomości z tej pary domen nie będą już wyświetlane w szczegółowych informacjach o analizie fałszowania.
- Wpisy sfałszowanych nadawców nigdy nie wygasają.
- Fałsz obsługuje zarówno zezwalanie, jak i blokowanie. Adres URL obsługuje tylko zezwalanie.

1. W portalu Microsoft 365 Defender przejdź do **sekcji Zasady i reguły &** \>  \> reguły **zagrożeń w sekcji** \> Listy zezwalania **i blokowania** dzierżaw.

2. Na stronie **Lista zezwalania/blokowania dzierżawy** wybierz kartę **Fałszowanie** , a następnie kliknij ikonę ![Blokuj.](../../media/m365-cc-sc-create-icon.png) **Dodaj**.

3. W **wyświetlonym wysuwam menu Add new domain pairs** (Dodaj nowe pary domen) skonfiguruj następujące ustawienia:
   - **Dodaj nowe pary domen z symbolami wieloznacznymi**: Wprowadź jedną parę domen w wierszu (maksymalnie 20). Aby uzyskać szczegółowe informacje na temat składni fałszywych wpisów nadawców, zobacz [Zarządzanie listą zezwalania/blokowania dzierżawy](tenant-allow-block-list.md).
   - **Fałsz typ**: Wybierz jedną z następujących wartości:
     - **Wewnętrzny**: sfałszowany nadawca należy do Twojej organizacji ( [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Zewnętrzne**: sfałszowany nadawca znajduje się w domenie zewnętrznej.
   - **Akcja**: Wybierz pozycję **Zezwalaj** lub **Zablokuj**.

4. Po zakończeniu kliknij przycisk **Dodaj**.

## <a name="use-powershell"></a>Używanie programu PowerShell

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>Dodawanie pozycji zablokowanych nadawców, plików lub adresów URL do listy zablokowanych/zezwalania na dzierżawę

Aby dodać wpisy zablokowanych nadawców, plików lub adresów URL na liście zezwalania/blokowania dzierżawy, użyj następującej składni:

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

W tym przykładzie dodano wpis zablokowania nadawcy dla określonego nadawcy, który wygasa określonego dnia.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

W tym przykładzie dodano wpis pliku bloku dla określonych plików, które nigdy nie wygasają.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

W tym przykładzie dodano wpis block URL dla contoso.com oraz wszystkich poddomen (na przykład contoso.com, www.contoso.com i xyz.abc.contoso.com). W związku z tym, że nie korzystano z parametrów ExpirationDate ani NoExpiration, wpis wygaśnie po 30 dniach.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>Dodawanie fałszywych wpisów zablokowanych nadawców 

Aby dodać sfałszowane wpisy nadawców na liście zezwalania/blokowania dzierżawy, użyj następującej składni:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
