---
title: Włączanie automatycznego rozwijania archiwizacji
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: e2a789f2-9962-4960-9fd4-a00aa063559e
description: 'Dla administratorów: Dowiedz się, jak włączyć automatyczne rozszerzanie archiwizacji, co zapewnia użytkownikom dodatkową przestrzeń dyskową dla swoich skrzynek Exchange Online pocztowych. Możesz włączyć automatyczne archiwizowanie dla całej organizacji lub tylko dla określonych użytkowników.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c6f1514ed4bb9c12ac666b366cab91358216357a
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010653"
---
# <a name="enable-auto-expanding-archiving"></a>Włączanie automatycznego rozwijania archiwizacji

Aby włączyć dodatkowe miejsce do Exchange Online archiwalnych skrzynek pocztowych, możesz użyć funkcji automatycznego rozszerzania archiwizacji. Po włączeniu automatycznego rozszerzania archiwizacji do archiwalnej skrzynki pocztowej użytkownika jest automatycznie dodawana dodatkowa przestrzeń dyskowa do momentu osiągnięcia limitu magazynowania 1,5 TB. Automatyczne archiwizowanie można włączyć dla wszystkich osób w organizacji lub tylko dla określonych użytkowników. Aby uzyskać więcej informacji na temat automatycznego rozszerzania archiwizacji, zobacz [Informacje na temat automatycznego rozwijania archiwizacji](autoexpanding-archiving.md).

## <a name="before-you-enable-auto-expanding-archiving"></a>Przed włączeniem automatycznego rozwijania archiwizacji

- Po włączeniu automatycznego archiwizowania dla organizacji lub konkretnego użytkownika nie można go wyłączyć. Ponadto administratorzy nie mogą dostosowywać przydziału miejsca do magazynowania dla automatycznego rozszerzania archiwizacji.

- Aby włączyć automatyczne archiwizowanie, musisz być administratorem globalnym w organizacji lub członkiem grupy ról Zarządzanie organizacją Exchange Online organizacji. Aby włączyć automatyczne archiwizowanie dla określonych użytkowników, musisz być członkiem grupy ról, do która ma przypisaną rolę Adresaci poczty.

- Archiwalne skrzynki pocztowe użytkowników muszą być włączone, aby można było włączyć automatyczne rozszerzanie archiwum. Aby włączyć archiwacyjną skrzynkę pocztową, Exchange Online przypisać użytkownikowi licencję w planie 2. W przypadku przypisania użytkownikowi licencji Exchange Online Plan 1 należy przypisać mu osobną licencję Exchange Online — archiwum, aby włączyć jego archiwalne skrzynki pocztowe. Zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md).

- Po włączeniu automatycznego archiwizowania archiwalna skrzynka pocztowa zostanie przekonwertowana na archiwum automatycznie rozszerzające się, gdy archiwalna skrzynka pocztowa (w tym folder Elementy do odzyskania) osiągnie 90 GB. Może upłynieć do 30 dni, aż zostanie aprowowana dodatkowa przestrzeń dyskowa.

- Za pomocą programu PowerShell możesz również włączyć archiwalne skrzynki pocztowe. Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać przykład polecenia programu PowerShell umożliwiającego włączanie archiwalnych skrzynek pocztowych dla wszystkich użytkowników w organizacji.

- Automatyczne rozszerzanie archiwizacji obsługuje również udostępnione skrzynki pocztowe. Aby włączyć archiwum dla udostępnionej skrzynki pocztowej, wymagana jest licencja usługi Exchange Online Plan 2 lub Exchange Online Plan 1 z licencją Exchange Online — archiwum e-mail.

- Automatyczne rozszerzanie archiwizacji zapobiega odzyskiwaniu lub przywracaniu nieaktywnej [skrzynki pocztowej](inactive-mailboxes-in-office-365.md#what-are-inactive-mailboxes). Oznacza to, że jeśli włączysz automatyczne rozszerzanie archiwizacji dla skrzynki pocztowej, a skrzynka pocztowa zostanie później przekształcona w nieaktywną skrzynkę pocztową, nie będzie można jej [odzyskać (](recover-an-inactive-mailbox.md) konwertując na aktywną skrzynkę pocztową) ani przywrócić [jej (](restore-an-inactive-mailbox.md) przez scalenie zawartości z istniejącą skrzynką pocztową). Jeśli dla nieaktywnej skrzynki pocztowej włączono automatyczne rozszerzanie archiwizacji, jedynym sposobem na odzyskanie danych jest użycie narzędzia Przeszukiwanie zawartości w programie Centrum zgodności platformy Microsoft 365 w celu wyeksportowania danych ze skrzynki pocztowej i zaimportowania ich do innej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz sekcję "Nieaktywne skrzynki pocztowe i automatyczne rozwijanie archiwów" w tece Informacje o nieaktywnych [skrzynkach pocztowych](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-auto-expanding-archives).

- Za pomocą centrum administracyjnego programu Exchange ani centrum administracyjnego Centrum zgodności platformy Microsoft 365 włączyć automatyczne rozszerzanie archiwizacji. Musisz użyć programu Exchange Online PowerShell. Aby połączyć się ze swoją Exchange Online przy użyciu zdalnego programu PowerShell, zobacz Połączenie [się Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="enable-auto-expanding-archiving-for-your-entire-organization"></a>Włączanie automatycznego archiwizowania dla całej organizacji

Możesz włączyć automatyczne rozszerzanie archiwizacji dla całej organizacji. Po włączeniu tej funkcji automatyczne archiwizowanie będzie włączone dla istniejących skrzynek pocztowych użytkowników i dla nowo utworzonych skrzynek pocztowych użytkowników. Podczas tworzenia skrzynek pocztowych użytkowników pamiętaj o włączeniu głównej archiwalnej skrzynki pocztowej użytkownika, aby funkcja automatycznego rozszerzania archiwizacji sprawdzała się w przypadku nowej skrzynki pocztowej użytkownika.
  
1. [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Uruchom następujące polecenie w programie Exchange Online PowerShell, aby włączyć automatyczne archiwizowanie dla całej organizacji.

    ```powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

## <a name="enable-auto-expanding-archiving-for-specific-users"></a>Włączanie automatycznego archiwizowania dla określonych użytkowników

Zamiast włączać automatyczne archiwizowanie dla każdego użytkownika w organizacji, możesz włączyć tę funkcję tylko dla określonych użytkowników. Może to być spowodowane tym, że tylko niektórzy użytkownicy mogą potrzebować dużej pojemności magazynu archiwum.
  
Po włączeniu automatycznego archiwizowania dla określonego użytkownika i jego skrzynki pocztowej w archiwum lub przypisaniu go do zasad przechowywania są dokonywane następujące dwie zmiany:
  
- Przydział magazynowania dla podstawowej archiwaowej skrzynki pocztowej użytkownika został zwiększony o 10 GB (z 100 GB do 110 GB). Został również zwiększony przydział z ostrzeżeniem o archiwum o 10 GB (z 90 GB do 100 GB).

- Przydział magazynowania dla folderu Elementy do odzyskania w podstawowej skrzynce pocztowej użytkownika został zwiększony o 10 GB (również z 100 GB do 110 GB). Został również zwiększony przydział z ostrzeżeniem Elementy do odzyskania o 10 GB (z 90 GB do 100 GB). Te zmiany mają zastosowanie tylko wtedy, gdy skrzynka pocztowa jest wstrzymana lub przypisana do zasad przechowywania.

To dodatkowe miejsce jest dodawane, aby zapobiec problemom z przechowywaniem, które mogą wystąpić przed udostępnieniem archiwum rozszerzające się automatycznie. W przypadku włączenia automatycznego  *rozszerzania*  archiwizacji dla całej organizacji nie jest dodawane dodatkowe miejsce do magazynowania, zgodnie z opisem w poprzedniej sekcji.
  
1. [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Uruchom następujące polecenie w programie Exchange Online PowerShell, aby włączyć automatyczne archiwizowanie dla określonego użytkownika. Jak wyjaśniono wcześniej, archiwalne skrzynki pocztowe (archiwum główne) użytkownika muszą być włączone, aby można było włączyć automatyczne rozszerzanie archiwizacji dla tego użytkownika.

    ```powershell
    Enable-Mailbox <user mailbox> -AutoExpandingArchive
    ```

> [!IMPORTANT]
> We wdrożeniu hybrydowym programu Exchange nie można użyć polecenia **Enable-Mailbox -AutoExpandingArchive** w celu włączenia automatycznego archiwizowania dla określonego użytkownika, którego podstawowa skrzynka pocztowa jest lokalna i ma archiwalne skrzynki pocztowe w chmurze. Aby włączyć automatyczne rozszerzanie archiwizacji dla archiwalnych skrzynek pocztowych w chmurze we wdrożeniu hybrydowym programu Exchange, musisz uruchomić polecenie **Set-OrganizationConfig -AutoExpandingArchive** w programie Exchange Online PowerShell, aby włączyć automatyczne archiwizowanie rozszerzania dla całej organizacji. Jeśli podstawowe i archiwalne skrzynki pocztowe użytkownika są oparte na chmurze, możesz użyć polecenia **Enable-Mailbox -AutoExpandingArchive** , aby włączyć automatyczne archiwizowanie rozszerzania dla tego konkretnego użytkownika.
  
## <a name="verify-that-auto-expanding-archiving-is-enabled"></a>Sprawdzanie, czy włączono automatyczne rozszerzanie archiwum

Aby sprawdzić, czy w organizacji włączono automatyczne rozszerzanie archiwizacji, uruchom następujące polecenie w programie Exchange Online PowerShell.

```powershell
Get-OrganizationConfig | FL AutoExpandingArchiveEnabled
```

Wartość of oznacza  `True` , że dla organizacji włączono automatyczne rozszerzanie archiwizacji. 
  
Aby sprawdzić, czy dla określonego użytkownika włączono automatyczne rozszerzanie archiwum, uruchom następujące polecenie w programie Exchange Online PowerShell.
  
```powershell
Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
```

Wartość of oznacza  `True` , że dla użytkownika włączono automatyczne rozszerzanie archiwizacji.
  
Aby sprawdzić, czy dla nieaktywnych skrzynek pocztowych włączono automatyczne rozszerzanie archiwizacji, uruchom następujące polecenie w programie Exchange Online PowerShell.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL UserPrincipalName,AutoExpandingArchiveEnabled
```

Wartość of oznacza  `True` , że dla nieaktywnej skrzynki pocztowej włączono automatyczne rozszerzanie archiwizacji. Wartość of oznacza `False` , że automatyczne rozszerzanie archiwizacji nie jest włączone.

Po włączeniu automatycznego rozszerzania archiwizacji należy pamiętać o następujących kwestiach:
  
- Jeśli uruchamiasz polecenie **Set-OrganizationConfig -AutoExpandingArchive** w celu włączenia automatycznego archiwizowania dla organizacji, nie musisz uruchamiać polecenia **Enable-Mailbox -AutoExpandingArchive** dla poszczególnych skrzynek pocztowych. Uruchomienie polecenia cmdlet **Set-OrganizationConfig** w celu włączenia automatycznego rozwijania archiwizacji dla organizacji nie zmienia właściwości  *AutoExpandingArchiveEnabled*  dla skrzynek pocztowych użytkowników na `True`.

- Podobnie wartości właściwości skrzynki pocztowej  *ArchiveQuota*  i  *ArchiveWarningQuota*  nie są zmieniane po włączeniu automatycznego archiwizowania. W rzeczywistości po włączeniu automatycznego archiwizowania dla skrzynki pocztowej użytkownika i dla właściwości  *AutoExpandingArchiveEnabled*  `True`jest ustawiona wartość , właściwości  *ArchiveQuota*  i  *ArchiveWarningQuota*  są ignorowane. Oto przykład tych właściwości skrzynki pocztowej po włączeniu automatycznego rozszerzania archiwizacji dla skrzynki pocztowej użytkownika. 

    ![Po włączeniu automatycznego archiwizowania właściwości ArchiveQuota i ArchiveWarningQuota są ignorowane.](../media/6a1c1b69-5c4c-4267-aac8-53577667f03e.png)

## <a name="more-information"></a>Więcej informacji

- Za pomocą programu PowerShell możesz również włączyć archiwalne skrzynki pocztowe. Na przykład poniższe polecenie można uruchomić w programie Exchange Online PowerShell, aby włączyć archiwalne skrzynki pocztowe dla wszystkich użytkowników, których archiwalne skrzynki pocztowe nie zostały jeszcze włączone.

    ```powershell
    Get-Mailbox -Filter {ArchiveStatus -Eq "None" -AND RecipientTypeDetails -eq "UserMailbox"} | Enable-Mailbox -Archive
    ```

- Automatyczne rozszerzanie archiwizacji jest obsługiwane w archiwalnych skrzynkach pocztowych w chmurze w Exchange hybrydowym dla użytkowników, którzy mają lokalną podstawową skrzynkę pocztową. Jednak po włączeniu automatycznego rozszerzania archiwizacji dla archiwalnej skrzynki pocztowej w chmurze nie możesz wyłączyć tej archiwalnej skrzynki pocztowej z powrotem do lokalnej Exchange organizacji. Automatyczne rozszerzanie archiwizacji nie jest obsługiwane w lokalnych skrzynkach pocztowych w żadnej wersji programu Exchange Server.

- Aby uzyskać listę klientów programu Outlook, z których użytkownicy mogą korzystać w celu uzyskania dostępu do elementów w dodatkowym obszarze przechowywania w archiwalnej skrzynce pocztowej, zobacz sekcję "Wymagania programu Outlook dotyczące uzyskiwania dostępu do elementów w archiwum rozszerzonym automatycznie" w tece Informacje na temat automatycznego rozszerzania archiwizacji[.](autoexpanding-archiving.md#outlook-requirements-for-accessing-items-in-an-auto-expanded-archive)

- Jak wyjaśniono wcześniej, po uruchomieniu polecenia **Włącz-Skrzynka pocztowa -AutoExpandingArchive** do przydziału magazynowania podstawowego skrzynki pocztowej użytkownika (oraz do folderu Elementy do odzyskania, jeśli skrzynka pocztowa znajduje się w archiwum) dodano 10 GB. Zapewnia to dodatkową przestrzeń dyskową do czasu zapewnienia automatycznie rozszerzonego miejsca do magazynowania (może to potrwać do 30 dni). To dodatkowe miejsce do magazynowania nie jest dodawane po uruchomieniu ustawienia **Set-OrganizationConfig -AutoExpandingArchive** w celu włączenia automatycznego archiwizowania dla wszystkich skrzynek pocztowych w organizacji. Jeśli włączono automatyczne archiwizowanie dla całej organizacji, ale musisz dodać dodatkowe 10 GB miejsca do magazynowania dla określonego użytkownika, możesz uruchomić polecenie **Enable-Mailbox -AutoExpandingArchive** dla tej skrzynki pocztowej. Zostanie wyświetlony komunikat o błędzie z informacją, że automatyczne rozszerzanie archiwizacji zostało już włączone, ale dodatkowe miejsce do magazynowania zostanie dodane do skrzynki pocztowej.

> [!IMPORTANT]
> Automatyczne rozszerzanie archiwizacji jest obsługiwane tylko w przypadku skrzynek pocztowych używanych przez poszczególnych użytkowników lub udostępnionych skrzynek pocztowych ze stopą wzrostu, która nie przekracza 1 GB na dzień. Kopiowanie wiadomości do archiwalnej skrzynki pocztowej na potrzeby archiwizacji przy użyciu reguł dziennika, reguł transportu lub reguł automatycznego przesyłania dalej nie jest dozwolone. Archiwalne skrzynki pocztowe użytkowników są przeznaczone tylko dla tego użytkownika. Firma Microsoft zastrzega sobie prawo do zablokowania dodatkowego archiwizowania w przypadkach, gdy archiwizowa skrzynka pocztowa użytkownika jest używana do przechowywania danych archiwum dla innych użytkowników lub w innych nieodpowiednich przypadkach.
