---
title: Włącz automatycznie rozszerzane archiwizowanie
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
description: 'Dla administratorów: dowiedz się, jak włączyć automatyczne rozszerzanie archiwizacji, co zapewnia użytkownikom dodatkowy magazyn dla skrzynek pocztowych Exchange Online. Możesz włączyć automatyczne rozszerzanie archiwizacji dla całej organizacji lub tylko dla określonych użytkowników.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7f1155eaf95a8cf814561650acee4784e8c469df
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012770"
---
# <a name="enable-auto-expanding-archiving"></a>Włącz automatycznie rozszerzane archiwizowanie

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Możesz użyć funkcji automatycznego rozszerzania archiwizacji Exchange Online, aby włączyć dodatkowe miejsce do magazynowania dla archiwalnych skrzynek pocztowych. Po włączeniu automatycznego rozszerzania archiwizacji dodatkowe miejsce do magazynowania jest automatycznie dodawane do skrzynki pocztowej archiwum użytkownika do momentu osiągnięcia limitu magazynu wynoszącego 1,5 TB. Możesz włączyć automatyczne rozszerzanie archiwizacji dla wszystkich w organizacji lub tylko dla określonych użytkowników. Aby uzyskać więcej informacji na temat automatycznego rozszerzania archiwizacji, zobacz [Dowiedz się więcej na temat automatycznego rozszerzania archiwizacji](autoexpanding-archiving.md).

## <a name="before-you-enable-auto-expanding-archiving"></a>Przed włączeniem automatycznego rozszerzania archiwizacji

- Po włączeniu automatycznego rozszerzania archiwizacji dla organizacji lub dla określonego użytkownika nie można go wyłączyć. Ponadto administratorzy nie mogą dostosować limitu przydziału magazynu na potrzeby automatycznego rozszerzania archiwizacji.

- Aby umożliwić automatyczne rozszerzanie archiwizacji, musisz być administratorem globalnym w organizacji lub członkiem grupy ról Zarządzanie organizacją w organizacji Exchange Online. Alternatywnie musisz być członkiem grupy ról, do których przypisano rolę Adresaci poczty, aby umożliwić automatyczne rozszerzanie archiwizacji dla określonych użytkowników.

- Przed włączeniem automatycznego rozszerzania archiwizacji należy włączyć skrzynkę pocztową archiwizacji archiwizacji użytkownika. Użytkownik musi mieć przypisaną licencję Exchange Online plan 2, aby włączyć skrzynkę pocztową archiwum. Jeśli użytkownikowi przypisano licencję Exchange Online Plan 1, należy przypisać mu oddzielną licencję Exchange Online — archiwum, aby włączyć jego archiwum skrzynki pocztowej. Zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md).

- Po włączeniu automatycznego rozszerzania archiwizacji skrzynka pocztowa archiwum jest konwertowana na automatycznie rozszerzające się archiwum, gdy skrzynka pocztowa archiwum (w tym folder Elementy możliwe do odzyskania) osiągnie 90 GB. Aprowizowanie dodatkowego miejsca do magazynowania może potrwać do 30 dni.

- Możesz również użyć programu PowerShell, aby włączyć archiwalne skrzynki pocztowe. Zobacz sekcję [Więcej informacji](#more-information) , aby zapoznać się z przykładem polecenia programu PowerShell, za pomocą którego można włączyć archiwalne skrzynki pocztowe dla wszystkich użytkowników w organizacji.

- Automatyczne rozszerzanie archiwizacji obsługuje również udostępnione skrzynki pocztowe. Aby włączyć archiwum udostępnionej skrzynki pocztowej, wymagana jest licencja Exchange Online Plan 2 lub licencja Exchange Online Plan 1 z licencją Exchange Online — archiwum.

- Automatyczne rozszerzanie archiwizacji uniemożliwia odzyskanie lub przywrócenie [nieaktywnej skrzynki pocztowej](inactive-mailboxes-in-office-365.md#what-are-inactive-mailboxes). Oznacza to, że jeśli włączysz automatyczne rozszerzanie archiwizacji dla skrzynki pocztowej, a skrzynka pocztowa zostanie nieaktywna w późniejszym terminie, nie będzie można [odzyskać nieaktywnej skrzynki pocztowej](recover-an-inactive-mailbox.md) (konwertując ją na aktywną skrzynkę pocztową) ani [przywrócić](restore-an-inactive-mailbox.md) jej (scalając zawartość z istniejącą skrzynką pocztową). Jeśli automatyczne rozszerzanie archiwizacji jest włączone w nieaktywnej skrzynce pocztowej, jedynym sposobem odzyskania danych jest użycie narzędzia do wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview w celu wyeksportowania danych ze skrzynki pocztowej i zaimportowania ich do innej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz sekcję "Nieaktywne skrzynki pocztowe i automatyczne rozszerzanie archiwów" w [temacie Dowiedz się więcej o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-auto-expanding-archives).

- Nie można użyć centrum administracyjnego Exchange ani portalu zgodności usługi Microsoft Purview, aby włączyć automatyczne rozszerzanie archiwizacji. Musisz użyć Exchange Online programu PowerShell. Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="enable-auto-expanding-archiving-for-your-entire-organization"></a>Włączanie automatycznego rozszerzania archiwizacji dla całej organizacji

Możesz włączyć automatyczne rozszerzanie archiwizacji dla całej organizacji. Po włączeniu tej funkcji automatyczne rozszerzanie archiwizacji zostanie włączone dla istniejących skrzynek pocztowych użytkowników i dla nowo utworzonych skrzynek pocztowych użytkowników. Podczas tworzenia skrzynek pocztowych użytkownika należy włączyć główną skrzynkę pocztową archiwum użytkownika, aby funkcja automatycznego rozszerzania archiwizacji działała dla nowej skrzynki pocztowej użytkownika.
  
1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Uruchom następujące polecenie w programie Exchange Online Programu PowerShell, aby włączyć automatyczne rozszerzanie archiwizacji dla całej organizacji.

    ```powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

## <a name="enable-auto-expanding-archiving-for-specific-users"></a>Włączanie automatycznego rozszerzania archiwizacji dla określonych użytkowników

Zamiast włączać automatyczne rozszerzanie archiwizacji dla każdego użytkownika w organizacji, można włączyć ją tylko dla określonych użytkowników. Można to zrobić, ponieważ tylko niektórzy użytkownicy mogą potrzebować dużej pojemności magazynu archiwum.
  
Po włączeniu automatycznego rozszerzania archiwizacji dla określonego użytkownika i skrzynki pocztowej użytkownika wstrzymanej lub przypisanej do zasad przechowywania zostaną wprowadzone dwie następujące zmiany konfiguracji:
  
- Limit przydziału magazynu dla podstawowej skrzynki pocztowej archiwum użytkownika został zwiększony o 10 GB (ze 100 GB do 110 GB). Limit przydziału ostrzeżeń archiwum jest również zwiększony o 10 GB (z 90 GB do 100 GB).

- Limit przydziału magazynu dla folderu Elementy możliwe do odzyskania w podstawowej skrzynce pocztowej użytkownika jest zwiększany o 10 GB (również ze 100 GB do 110 GB). Limit przydziału ostrzeżeń elementów możliwych do odzyskania jest również zwiększony o 10 GB (z 90 GB do 100 GB). Te zmiany mają zastosowanie tylko wtedy, gdy skrzynka pocztowa jest wstrzymana lub przypisana do zasad przechowywania.

To dodatkowe miejsce jest dodawane, aby zapobiec wszelkim problemom z magazynem, które mogą wystąpić przed aprowizowaniem automatycznie rozwijającego się archiwum. Dodatkowe miejsce do  *magazynowania nie jest*  dodawane po włączeniu automatycznego rozszerzania archiwizacji dla całej organizacji, zgodnie z opisem w poprzedniej sekcji.
  
1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Uruchom następujące polecenie w programie Exchange Online Programu PowerShell, aby włączyć automatyczne rozszerzanie archiwizacji dla określonego użytkownika. Jak wyjaśniono wcześniej, skrzynka pocztowa archiwum użytkownika (archiwum główne) musi być włączona, aby można było włączyć automatyczne rozszerzanie archiwizacji dla tego użytkownika.

    ```powershell
    Enable-Mailbox <user mailbox> -AutoExpandingArchive
    ```

> [!IMPORTANT]
> W Exchange wdrożenia hybrydowego nie można użyć polecenia **Enable-Mailbox -AutoExpandingArchive**, aby włączyć automatyczne rozszerzanie archiwizacji dla określonego użytkownika, którego podstawowa skrzynka pocztowa jest lokalna i której skrzynka pocztowa archiwum jest oparta na chmurze. Aby włączyć automatyczne rozszerzanie archiwizacji skrzynek pocztowych archiwum opartego na chmurze w Exchange wdrożenia hybrydowego, należy uruchomić polecenie **Set-OrganizationConfig -AutoExpandingArchive** w Exchange Online programie PowerShell, aby umożliwić automatyczne rozszerzanie archiwizacji dla całej organizacji. Jeśli podstawowe i archiwalne skrzynki pocztowe użytkownika są oparte na chmurze, możesz użyć polecenia **Enable-Mailbox -AutoExpandingArchive** , aby włączyć automatyczne rozszerzanie archiwizacji dla danego użytkownika.
  
## <a name="verify-that-auto-expanding-archiving-is-enabled"></a>Sprawdź, czy włączono automatyczne rozszerzanie archiwizacji

Aby sprawdzić, czy automatyczne rozszerzanie archiwizacji jest włączone dla Twojej organizacji, uruchom następujące polecenie w programie Exchange Online programu PowerShell.

```powershell
Get-OrganizationConfig | FL AutoExpandingArchiveEnabled
```

Wartość  `True` wskazuje, że automatyczne rozszerzanie archiwizacji jest włączone dla organizacji. 
  
Aby sprawdzić, czy automatyczne rozszerzanie archiwizacji jest włączone dla określonego użytkownika, uruchom następujące polecenie w programie Exchange Online programu PowerShell.
  
```powershell
Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
```

Wartość  `True` wskazuje, że automatyczne rozszerzanie archiwizacji jest włączone dla użytkownika.
  
Aby ustalić, czy automatyczne rozszerzanie archiwizacji jest włączone dla nieaktywnych skrzynek pocztowych, uruchom następujące polecenie w programie Exchange Online programu PowerShell.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL UserPrincipalName,AutoExpandingArchiveEnabled
```

Wartość  `True` wskazuje, że automatyczne rozszerzanie archiwizacji jest włączone dla nieaktywnej skrzynki pocztowej. Wartość `False` wskazuje, że automatyczne rozszerzanie archiwizacji nie jest włączone.

Po włączeniu automatycznego rozszerzania archiwizacji należy pamiętać o następujących kwestiach:
  
- Jeśli uruchomisz polecenie **Set-OrganizationConfig -AutoExpandingArchive** , aby włączyć automatyczne rozszerzanie archiwizacji dla organizacji, nie musisz uruchamiać polecenia **Enable-Mailbox -AutoExpandingArchive** w poszczególnych skrzynkach pocztowych. Uruchomienie polecenia cmdlet **Set-OrganizationConfig** w celu włączenia automatycznego rozszerzania archiwizacji dla organizacji nie powoduje zmiany właściwości  *AutoExpandingArchiveEnabled*  w skrzynkach pocztowych użytkownika na `True`.

- Podobnie wartości właściwości skrzynki pocztowej  *ArchiveQuota*  i  *ArchiveWarningQuota*  nie są zmieniane po włączeniu automatycznego rozszerzania archiwizacji. W rzeczywistości po włączeniu automatycznego rozszerzania archiwizacji dla skrzynki pocztowej użytkownika i właściwości  *AutoExpandingArchiveEnabled*  jest ustawiona wartość  `True`, właściwości  *ArchiveQuota*  i  *ArchiveWarningQuota*  są ignorowane. Oto przykład tych właściwości skrzynki pocztowej po włączeniu automatycznego rozszerzania archiwizacji dla skrzynki pocztowej użytkownika. 

    ![Właściwości ArchiveQuota i ArchiveWarningQuota są ignorowane po włączeniu automatycznego rozszerzania archiwizacji.](../media/6a1c1b69-5c4c-4267-aac8-53577667f03e.png)

## <a name="more-information"></a>Więcej informacji

- Możesz również użyć programu PowerShell, aby włączyć archiwalne skrzynki pocztowe. Na przykład możesz uruchomić następujące polecenie w programie Exchange Online programu PowerShell, aby włączyć archiwalne skrzynki pocztowe dla wszystkich użytkowników, których archiwum skrzynki pocztowej nie jest jeszcze włączone.

    ```powershell
    Get-Mailbox -Filter {ArchiveStatus -Eq "None" -AND RecipientTypeDetails -eq "UserMailbox"} | Enable-Mailbox -Archive
    ```

- Automatyczne rozszerzanie archiwizacji jest obsługiwane w przypadku skrzynek pocztowych archiwum opartego na chmurze w Exchange wdrożenia hybrydowego dla użytkowników, którzy mają lokalną podstawową skrzynkę pocztową. Jednak po włączeniu automatycznego rozszerzania archiwizacji dla skrzynki pocztowej archiwum opartej na chmurze nie można odłączyć tej skrzynki pocztowej archiwum z powrotem do lokalnej Exchange organizacji. Automatyczne rozszerzanie archiwizacji nie jest obsługiwane w przypadku lokalnych skrzynek pocztowych w żadnej wersji Exchange Server.

- Aby uzyskać listę klientów Outlook, których użytkownicy mogą używać do uzyskiwania dostępu do elementów w dodatkowej przestrzeni magazynowej w skrzynce pocztowej archiwum, zobacz sekcję "wymagania Outlook dotyczące uzyskiwania dostępu do elementów w automatycznie rozwiniętym archiwum" w [temacie Dowiedz się więcej na temat automatycznego rozszerzania archiwizacji](autoexpanding-archiving.md#outlook-requirements-for-accessing-items-in-an-auto-expanded-archive).

- Jak wyjaśniono wcześniej, 10 GB jest dodawane do limitu przydziału magazynu podstawowej skrzynki pocztowej archiwum użytkownika (i do folderu Elementy możliwe do odzyskania, jeśli skrzynka pocztowa jest wstrzymana) po uruchomieniu polecenia **Enable-Mailbox -AutoExpandingArchive** . Zapewnia to dodatkowy magazyn do momentu aprowizowania automatycznie rozwiniętej przestrzeni dyskowej (co może potrwać do 30 dni). To dodatkowe miejsce do magazynowania nie jest dodawane po uruchomieniu polecenia **Set-OrganizationConfig -AutoExpandingArchive** , aby umożliwić automatyczne rozszerzanie archiwizacji dla wszystkich skrzynek pocztowych w organizacji. Jeśli włączono automatyczne rozszerzanie archiwizacji dla całej organizacji, ale trzeba dodać dodatkowe 10 GB miejsca do magazynowania dla określonego użytkownika, możesz uruchomić polecenie **Enable-Mailbox -AutoExpandingArchive** w tej skrzynce pocztowej. Zostanie wyświetlony komunikat o błędzie informujący o tym, że automatyczne rozszerzanie archiwizacji zostało już włączone, ale dodatkowe miejsce do magazynowania zostanie dodane do skrzynki pocztowej.

> [!IMPORTANT]
> Automatyczne rozszerzanie archiwizacji jest obsługiwane tylko w przypadku skrzynek pocztowych używanych przez poszczególnych użytkowników lub udostępnionych skrzynek pocztowych z szybkością wzrostu, która nie przekracza 1 GB dziennie. Używanie dzienników, reguł transportu lub reguł automatycznego przekazywania do kopiowania wiadomości do archiwum skrzynki pocztowej na potrzeby archiwizacji jest niedozwolone. Skrzynka pocztowa archiwum użytkownika jest przeznaczona tylko dla tego użytkownika. Firma Microsoft zastrzega sobie prawo do odmowy dodatkowej archiwizacji w przypadkach, gdy skrzynka pocztowa archiwum użytkownika jest używana do przechowywania danych archiwalnych dla innych użytkowników lub w innych przypadkach niewłaściwego użycia.
