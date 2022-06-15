---
title: Odzyskaj nieaktywną skrzynkę pocztową
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 35d0ecdb-7cb0-44be-ad5c-69df2f8f8b25
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak odzyskać zawartość nieaktywnej skrzynki pocztowej w Office 365, konwertując ją na nową skrzynkę pocztową zawierającą zawartość nieaktywnej skrzynki pocztowej.
ms.openlocfilehash: 2c679407cb4f7203bb69d88c871bd844694a7c47
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66101585"
---
# <a name="recover-an-inactive-mailbox"></a>Odzyskaj nieaktywną skrzynkę pocztową

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Nieaktywna skrzynka pocztowa (która jest typem nietrwałej skrzynki pocztowej) służy do zachowania poczty e-mail byłego pracownika po opuszczeniu organizacji. Jeśli ten pracownik wróci do organizacji lub jeśli inny pracownik przejmie obowiązki byłego pracownika, istnieją dwa sposoby udostępniania zawartości nieaktywnej skrzynki pocztowej użytkownikowi:

- **Odzyskaj nieaktywną skrzynkę pocztową.** Jeśli były pracownik wróci do organizacji lub nowy pracownik zostanie zatrudniony do podjęcia obowiązków związanych z pracą byłego pracownika, możesz odzyskać zawartość nieaktywnej skrzynki pocztowej. Ta metoda konwertuje nieaktywną skrzynkę pocztową na nową, aktywną skrzynkę pocztową zawierającą zawartość nieaktywnej skrzynki pocztowej. Po jej odzyskaniu nieaktywna skrzynka pocztowa już nie istnieje. Procedury opisane w tym artykule opisują tę metodę.

- **Przywróć nieaktywną skrzynkę pocztową.** Jeśli inny pracownik przejmuje obowiązki związane z zadaniem byłego pracownika lub jeśli inny użytkownik potrzebuje dostępu do zawartości nieaktywnej skrzynki pocztowej, możesz przywrócić (lub scalić) zawartość nieaktywnej skrzynki pocztowej do istniejącej skrzynki pocztowej. Możesz również przywrócić archiwum z nieaktywnej skrzynki pocztowej. Aby zapoznać się z procedurami dla tej metody, zobacz [Przywracanie nieaktywnej skrzynki pocztowej w Office 365](restore-an-inactive-mailbox.md).

Aby uzyskać więcej informacji, zobacz sekcję [Więcej informacji](#more-information) na temat różnic między odzyskiwaniem i przywracaniem nieaktywnej skrzynki pocztowej oraz opisem tego, co się stanie po odzyskaniu nieaktywnej skrzynki pocztowej.

> [!NOTE]
> Nie można odzyskać ani przywrócić nieaktywnej skrzynki pocztowej skonfigurowanej przy użyciu automatycznie rozwijającego się archiwum. Jeśli musisz odzyskać dane z nieaktywnej skrzynki pocztowej z automatycznie rozszerzającym się archiwum, użyj wyszukiwania zawartości, aby wyeksportować dane ze skrzynki pocztowej, a następnie zaimportować je do innej skrzynki pocztowej. Aby uzyskać instrukcje, zobacz następujące artykuły:
>
> - [Wyszukiwanie zawartości](content-search.md)
> - [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md)

## <a name="requirements-to-recover-an-inactive-mailbox"></a>Wymagania dotyczące odzyskiwania nieaktywnej skrzynki pocztowej

- Aby odzyskać nieaktywną skrzynkę pocztową, należy użyć Exchange Online programu PowerShell. Nie można użyć centrum administracyjnego Exchange (EAC) ani portal zgodności Microsoft Purview dla tej procedury. Aby uzyskać instrukcje krok po kroku dotyczące używania Exchange Online programu PowerShell, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Uruchom następujące polecenie, aby uzyskać informacje o tożsamości dla nieaktywnych skrzynek pocztowych w organizacji.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Użyj informacji zwróconych przez to polecenie, aby odzyskać określoną nieaktywną skrzynkę pocztową.

## <a name="recover-inactive-mailboxes"></a>Odzyskiwanie nieaktywnych skrzynek pocztowych

Użyj polecenia cmdlet **New-Mailbox** z parametrem  *InactiveMailbox*  , aby odzyskać nieaktywną skrzynkę pocztową.

1. Utwórz zmienną zawierającą właściwości nieaktywnej skrzynki pocztowej.

   ```powershell
   $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > W poprzednim poleceniu użyj wartości właściwości **DistinguishedName** lub **ExchangeGUID** , aby zidentyfikować nieaktywną skrzynkę pocztową. Te właściwości są unikatowe dla każdej skrzynki pocztowej w organizacji, podczas gdy istnieje możliwość, że aktywna i nieaktywna skrzynka pocztowa może mieć ten sam podstawowy adres SMTP.

2. W tym przykładzie użyto właściwości uzyskanych w poprzednim poleceniu i odzyska nieaktywną skrzynkę pocztową do aktywnej skrzynki pocztowej użytkownika Ann Beebe. Upewnij się, że wartości określone dla parametrów  *Nazwa*  i  *MicrosoftOnlineServicesID*  są unikatowe w organizacji.

   ```powershell
   New-Mailbox -InactiveMailbox $InactiveMailbox.DistinguishedName -Name annbeebe -FirstName Ann -LastName Beebe -DisplayName "Ann Beebe" -MicrosoftOnlineServicesID Ann.Beebe@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
   ```

   Podstawowy adres SMTP odzyskanej nieaktywnej skrzynki pocztowej będzie miał taką samą wartość jak ten określony przez parametr  *MicrosoftOnlineServicesID*  .

Po odzyskaniu nieaktywnej skrzynki pocztowej zostanie również utworzone nowe konto użytkownika. Musisz aktywować to konto użytkownika, przypisując licencję. Aby przypisać licencję w Centrum administracyjne platformy Microsoft 365, zobacz [Dodawanie użytkowników i przypisywanie licencji w tym samym czasie](../admin/add-users/add-users.md).

## <a name="more-information"></a>Więcej informacji

- **Jaka jest główna różnica między odzyskiwaniem i przywracaniem nieaktywnej skrzynki pocztowej?** Po odzyskaniu nieaktywnej skrzynki pocztowej skrzynka pocztowa jest konwertowana na nową skrzynkę pocztową, zawartość i struktura folderów nieaktywnej skrzynki pocztowej są zachowywane, a skrzynka pocztowa jest połączona z nowym kontem użytkownika. Po jej odzyskaniu nieaktywna skrzynka pocztowa już nie istnieje, a wszelkie zmiany wprowadzone w zawartości w nowej skrzynce pocztowej będą miały wpływ na zawartość, która została pierwotnie wstrzymana w nieaktywnej skrzynce pocztowej. Z drugiej strony podczas przywracania nieaktywnej skrzynki pocztowej zawartość jest kopiowana tylko do innej skrzynki pocztowej. Nieaktywna skrzynka pocztowa jest zachowywana i pozostaje nieaktywną skrzynką pocztową. Wszelkie zmiany wprowadzone w zawartości w docelowej skrzynce pocztowej nie będą miały wpływu na oryginalną zawartość przechowywaną w nieaktywnej skrzynce pocztowej. Nieaktywną skrzynkę pocztową można nadal przeszukiwać przy użyciu In-Place eDiscovery, jej zawartość można przywrócić do innej skrzynki pocztowej lub odzyskać lub usunąć ją w późniejszym terminie.

- **Co się stanie po odzyskaniu nieaktywnej skrzynki pocztowej?** Po odzyskaniu nieaktywnej skrzynki pocztowej występują następujące elementy:

  - Blokada zastosowana do nieaktywnej skrzynki pocztowej jest zmieniana lub usuwana na podstawie typu blokady, który został zastosowany do nieaktywnej skrzynki pocztowej przed jej odzyskaniem.
    
    - **Microsoft 365 zasad przechowywania z blokadą zachowania.** Jeśli nieaktywna skrzynka pocztowa została uwzględniona w zasadach przechowywania z [blokadą zachowania](retention-preservation-lock.md), odzyskana skrzynka pocztowa jest przypisywana do tych samych zasad przechowywania.
    
    - **Microsoft 365 zasad przechowywania bez blokady zachowania.** Nieaktywna skrzynka pocztowa jest usuwana z zasad przechowywania Microsoft 365. Jednak blokada postępowania sądowego jest włączona w odzyskanej skrzynce pocztowej, aby zapobiec usuwaniu zawartości skrzynki pocztowej na podstawie wszelkich zasad przechowywania w całej organizacji, które usuwają zawartość starszą niż określony wiek. Możesz zachować blokadę postępowania sądowego lub usunąć ją. Aby uzyskać więcej informacji, zobacz [Tworzenie blokady postępowania sądowego](create-a-litigation-hold.md).

    - **Blokada postępowania sądowego.** Jeśli blokada postępowania sądowego została włączona dla nieaktywnej skrzynki pocztowej, zostanie usunięta z odzyskanej skrzynki pocztowej.

    - **Archiwi In-Place** blokady w miejscu są usuwane z odzyskanej skrzynki pocztowej. Oznacza to, że odzyskana skrzynka pocztowa jest usuwana jako źródłowa skrzynka pocztowa z dowolnego In-Place Hold lub In-Place wyszukiwania zbierania elektronicznych materiałów dowodowych.

  - Okres odzyskiwania pojedynczego elementu (zdefiniowany przez **właściwość RetainDeletedItemsFor** skrzynki pocztowej) jest ustawiony na 30 dni. Zazwyczaj po utworzeniu nowej skrzynki pocztowej w Exchange Online ten okres przechowywania jest ustawiony na 14 dni. Ustawienie maksymalnej wartości 30 dni daje więcej czasu na odzyskanie wszystkich danych, które zostały trwale usunięte (lub przeczyszczane) z nieaktywnej skrzynki pocztowej. Możesz również wyłączyć odzyskiwanie pojedynczego elementu lub ustawić okres odzyskiwania pojedynczego elementu z powrotem na wartość domyślną 14 dni. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie odzyskiwania pojedynczego elementu dla skrzynki pocztowej](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery).

  - Blokada przechowywania jest włączona, a czas przechowywania jest ustawiony na 30 dni. Oznacza to, że domyślne zasady przechowywania Exchange i wszelkie zasady przechowywania Microsoft 365 w całej organizacji lub Exchange całej organizacji, które są przypisane do nowej skrzynki pocztowej, nie będą przetwarzane przez 30 dni. Daje to pracownikowi zwracającemu lub nowemu właścicielowi odzyskanej nieaktywnej skrzynki pocztowej czas na zarządzanie starymi wiadomościami. W przeciwnym razie zasady przechowywania Exchange lub Microsoft 365 mogą usuwać stare elementy skrzynki pocztowej (lub przenosić elementy do skrzynki pocztowej archiwum, jeśli jest włączona), które wygasły na podstawie ustawień skonfigurowanych dla zasad przechowywania Exchange lub Microsoft 365. Po upływie 30 dni wstrzymanie przechowywania wygaśnie, właściwość **RetentionHoldEnabled** zostanie ustawiona na **wartość False**, a Asystent folderów zarządzanych rozpocznie przetwarzanie zasad przypisanych do skrzynki pocztowej. Jeśli nie potrzebujesz tego dodatkowego czasu, możesz po prostu usunąć blokadę przechowywania. Alternatywnie możesz zwiększyć czas przechowywania za pomocą polecenia **Set-Mailbox -EndDateForRetentionHold** . Aby uzyskać więcej informacji, zobacz [Umieszczanie skrzynki pocztowej w blokadzie przechowywania](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Jeśli chcesz zachować oryginalny stan nieaktywnej skrzynki pocztowej, wstrzymaj odzyskaną skrzynkę pocztową.** Aby uniemożliwić nowemu właścicielowi skrzynki pocztowej lub zasadom przechowywania trwałe usunięcie wszelkich wiadomości z odzyskanej nieaktywnej skrzynki pocztowej, możesz umieścić skrzynkę pocztową w blokadzie postępowania sądowego. Aby uzyskać więcej informacji, zobacz [Tworzenie blokady postępowania sądowego](./create-a-litigation-hold.md).

- **Jakiego identyfikatora użytkownika można użyć podczas odzyskiwania nieaktywnej skrzynki pocztowej?** Po odzyskaniu nieaktywnej skrzynki pocztowej wartość określona dla parametru  *MicrosoftOnlineServicesID*  może różnić się od oryginalnej, która została skojarzona z nieaktywną skrzynką pocztową. Możesz również użyć oryginalnego identyfikatora użytkownika. Jednak zgodnie z wcześniejszymi instrukcjami upewnij się, że wartości używane dla  *nazwy*  i  *identyfikatora MicrosoftOnlineServicesID*  są unikatowe w organizacji podczas odzyskiwania nieaktywnej skrzynki pocztowej.

- **Co zrobić, jeśli okres przechowywania skrzynki pocztowej dla nieaktywnej skrzynki pocztowej nie wygasł?** Jeśli nieaktywna skrzynka pocztowa została usunięta nietrwale mniej niż 30 dni temu, nie można jej odzyskać za pomocą polecenia **New-Mailbox -InactiveMailbox** . Musisz je odzyskać, przywracając odpowiednie konto użytkownika. Aby uzyskać więcej informacji, zobacz [Usuwanie użytkownika z organizacji](../admin/add-users/delete-a-user.md).

- **Skąd wiesz, czy nietrwale usunięty okres przechowywania skrzynki pocztowej dla nieaktywnej skrzynki pocztowej wygasł?** Uruchom następujące polecenie:
    
  ```powershell
  Get-Mailbox -InactiveMailboxOnly <identity of inactive mailbox> | Format-List ExternalDirectoryObjectId
  ```
    
    - Jeśli nie ma wartości właściwości **ExternalDirectoryObjectId** , okres przechowywania skrzynki pocztowej wygasł i możesz odzyskać nieaktywną skrzynkę pocztową, uruchamiając polecenie **New-Mailbox -InactiveMailbox** .
    - Jeśli istnieje wartość właściwości **ExternalDirectoryObjectId** , okres przechowywania nietrwałej skrzynki pocztowej nie wygasł i musisz odzyskać skrzynkę pocztową, [przywracając konto użytkownika](../admin/add-users/delete-a-user.md).

- **Rozważ włączenie archiwum skrzynki pocztowej po odzyskaniu nieaktywnej skrzynki pocztowej.** Dzięki temu powracający użytkownik lub nowy pracownik może przenieść stare wiadomości do archiwum skrzynki pocztowej. Po wygaśnięciu blokady przechowywania zasady archiwum, które są częścią domyślnej Exchange zasad przechowywania usługi MRM przypisanych do skrzynek pocztowych Exchange Online, będą przenosić elementy, które są dwa lata lub starsze, do skrzynki pocztowej archiwum. Jeśli nie włączysz archiwum skrzynki pocztowej, elementy starsze niż dwa lata pozostaną w podstawowej skrzynce pocztowej użytkownika. Aby uzyskać więcej informacji, zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md).
