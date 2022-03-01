---
title: Odzyskiwanie nieaktywnej skrzynki pocztowej
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
description: Dowiedz się, jak odzyskać zawartość nieaktywnej skrzynki pocztowej w programie Office 365, konwertując ją na nową skrzynkę pocztową zawierającą zawartość nieaktywnej skrzynki pocztowej.
ms.openlocfilehash: ce09d218d86e7cd949da1df80cc75a19fce64159
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010643"
---
# <a name="recover-an-inactive-mailbox"></a>Odzyskiwanie nieaktywnej skrzynki pocztowej

Nieaktywna skrzynka pocztowa (która jest typem "miękkiej" skrzynki pocztowej) służy do zachowywania wiadomości e-mail byłego pracownika po odejechaniu z organizacji. Jeśli ten pracownik powróci do organizacji lub gdy inny pracownik przejmie obowiązki byłego pracownika, można udostępnić użytkownikowi zawartość nieaktywnej skrzynki pocztowej na dwa sposoby:

- **Odzyskiwanie nieaktywnej skrzynki pocztowej.** Jeśli były pracownik powraca do organizacji lub gdy nowy pracownik jest zatrudniony do  obowiązków byłego pracownika, można odzyskać zawartość nieaktywnej skrzynki pocztowej. Ta metoda konwertuje nieaktywną skrzynkę pocztową na nową, aktywną skrzynkę pocztową zawierającą jej zawartość. Po ich odzyskaniu nieaktywna skrzynka pocztowa już nie istnieje. Procedury w tym temacie opisują tę metodę.

- **Przywracanie nieaktywnej skrzynki pocztowej.** Jeśli inny pracownik przejmie obowiązki byłego pracownika lub jeśli inny użytkownik potrzebuje dostępu do zawartości nieaktywnej skrzynki pocztowej, możesz przywrócić (lub scalić) zawartość nieaktywnej skrzynki pocztowej z istniejącą skrzynką pocztową. Możesz również przywrócić archiwum z nieaktywnej skrzynki pocztowej. Aby uzyskać procedury dotyczące tej metody, zobacz [Przywracanie nieaktywnej skrzynki pocztowej w programie Office 365](restore-an-inactive-mailbox.md).

Zobacz [sekcję Więcej](#more-information) informacji, aby uzyskać więcej informacji na temat różnic między odzyskiwaniem i przywracaniem nieaktywnej skrzynki pocztowej, a także opis tego, co się stanie, gdy nieaktywna skrzynka pocztowa zostanie odzyskana.

> [!NOTE]
> Nie można odzyskiwać ani przywracać nieaktywnych skrzynek pocztowych skonfigurowanych przy użyciu archiwum powiększania automatycznego. Jeśli chcesz odzyskać dane z nieaktywnej skrzynki pocztowej za pomocą archiwum rozszerzanego automatycznie, za pomocą wyszukiwania zawartości wyeksportuj dane ze skrzynki pocztowej, a następnie zaimportuj je do innej skrzynki pocztowej. Aby uzyskać instrukcje, zobacz następujące tematy:
>
> - [Przeszukiwanie zawartości](content-search.md)
> - [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md)

## <a name="requirements-to-recover-an-inactive-mailbox"></a>Wymagania dotyczące odzyskiwania nieaktywnej skrzynki pocztowej

- Aby odzyskać nieaktywną skrzynkę pocztową, musisz użyć programu Exchange Online PowerShell. Nie możesz korzystać z centrum administracyjnego usługi Exchange(EAC). Instrukcje krok po kroku można znaleźć w [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Uruchom następujące polecenie, aby uzyskać informacje o tożsamości dla nieaktywnych skrzynek pocztowych w organizacji.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Użyj informacji zwróconych za pomocą tego polecenia, aby odzyskać określoną nieaktywną skrzynkę pocztową.

## <a name="recover-inactive-mailboxes"></a>Odzyskiwanie nieaktywnych skrzynek pocztowych

Aby odzyskać **nieaktywną** skrzynkę pocztową, użyj polecenia cmdlet New-Mailbox z parametrem  *InactiveMailbox*  .

1. Utwórz zmienną zawierającą właściwości nieaktywnej skrzynki pocztowej.

   ```powershell
   $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > W poprzednim poleceniu należy użyć wartości właściwości **DistinguishedName** (Nazwa odróżniana) lub **ExchangeGUID (ExchangeGUID** ), aby zidentyfikować nieaktywną skrzynkę pocztową. Te właściwości są unikatowe dla każdej skrzynki pocztowej w organizacji, natomiast istnieje możliwość, że aktywna i nieaktywna skrzynka pocztowa może mieć taki sam podstawowy adres SMTP.

2. W tym przykładzie użyto właściwości uzyskanych w poprzednim poleceniu i odzyskano nieaktywną skrzynkę pocztową do aktywnej skrzynki pocztowej użytkownika Anny Beebe. Upewnij się, że wartości określone dla parametrów  *Name (*  Nazwa) i  *MicrosoftOnlineServicesID (Identyfikator usługi MicrosoftOnlineServicesID*  ) są unikatowe w organizacji.

   ```powershell
   New-Mailbox -InactiveMailbox $InactiveMailbox.DistinguishedName -Name annbeebe -FirstName Ann -LastName Beebe -DisplayName "Ann Beebe" -MicrosoftOnlineServicesID Ann.Beebe@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
   ```

   Podstawowy adres SMTP odzyskanej nieaktywnej skrzynki pocztowej będzie miał tę samą wartość co wartość określona przez parametr  *MicrosoftOnlineServicesID*  .

Po odzyskaniu nieaktywnej skrzynki pocztowej jest również tworzone nowe konto użytkownika. Musisz aktywować to konto użytkownika, przypisując licencję. Aby przypisać licencję w centrum administracyjne platformy Microsoft 365, zobacz Dodawanie użytkowników i [przypisywanie licencji w tym samym czasie](../admin/add-users/add-users.md).

## <a name="more-information"></a>Więcej informacji

- **Jaka jest główna różnica między odzyskiwaniem a przywracaniem nieaktywnej skrzynki pocztowej?** Po odzyskaniu nieaktywnej skrzynki pocztowej jest ona konwertowana na nową skrzynkę pocztową, a zawartość i struktura folderów nieaktywnej skrzynki pocztowej jest zachowywana, a skrzynka pocztowa jest połączona z nowym kontem użytkownika. Po ich odzyskaniu nieaktywna skrzynka pocztowa już nie istnieje, a wszelkie zmiany zawartości w nowej skrzynce pocztowej będą mieć wpływ na zawartość, która pierwotnie była wstrzymywana w nieaktywnej skrzynce pocztowej. Natomiast w przypadku przywracania nieaktywnej skrzynki pocztowej zawartość jest jedynie kopiowana do innej skrzynki pocztowej. Nieaktywna skrzynka pocztowa jest zachowywana i pozostaje nieaktywną skrzynką pocztową. Wszelkie zmiany wprowadzone w zawartości docelowej skrzynki pocztowej nie mają wpływu na oryginalną zawartość w nieaktywnej skrzynce pocztowej. Nieaktywną skrzynkę pocztową nadal można przeszukiwać przy użyciu zbierania elektronicznych materiałów dowodowych In-Place, jej zawartość można przywrócić do innej skrzynki pocztowej lub można ją odzyskać bądź usunąć później.

- **Co się stanie, gdy odzyskasz nieaktywną skrzynkę pocztową?** Podczas odzyskiwania nieaktywnej skrzynki pocztowej występują następujące zdarzenia:

  - Hold, który został zastosowany do nieaktywnej skrzynki pocztowej jest zmieniany lub usuwany w zależności od typu hold, który został zastosowany do nieaktywnej skrzynki pocztowej przed jej odzyskaniem.

    - **Zawieszenie w  postępowaniem sądowym.** Jeśli dla nieaktywnej skrzynki pocztowej włączono funkcję hold w związku z postępowaniem sądowym, jest ona usuwana z odzyskanej skrzynki pocztowej.

    - **Z odzyskanej** skrzynki In-Place usuwane są blokady miejsca. Oznacza to, że odzyskana skrzynka pocztowa jest usuwana jako źródłowa skrzynka pocztowa z In-Place wstrzymywania lub In-Place zbierania elektronicznych materiałów dowodowych.

    - **Microsoft 365 przechowywania przy użyciu blokady zachowywania.** Jeśli nieaktywna skrzynka pocztowa została przypisana do zasad przechowywania z zachowaniem blokady zachowywania (nazywanych zablokowanymi zasadami *przechowywania),* odzyskana skrzynka pocztowa zostanie przypisana do tych samych zablokowanych zasad przechowywania. Aby uzyskać więcej informacji na temat zablokowanych zasad przechowywania, zobacz [Użyj blokady zachowywania, aby ograniczyć zmiany zasad przechowywania i [zasad etykiet przechowywania.](retention-preservation-lock.md)

    - **Microsoft 365 przechowywania bez blokady zachowywania.** Nieaktywna skrzynka pocztowa zostanie usunięta z Microsoft 365 przechowywania, które do niego zastosowano. Jednak w odzyskanej skrzynce pocztowej jest włączone zawieszenie w związku z postępowaniem sądowym, aby zapobiec usuwaniu zawartości skrzynki pocztowej na podstawie wszelkich zasad przechowywania w całej organizacji, które usuwają zawartość starszą niż określony wiek. Możesz zachować zawieszenie w  postępowaniach sądowych lub je usunąć. Aby uzyskać więcej informacji, zobacz [Tworzenie postępowania w związku z postępowaniem sądowym](create-a-litigation-hold.md).

  - Okres odzyskiwania jednego elementu (który jest zdefiniowany przez właściwość **RetainDeletedItemsFor** mailbox) jest ustawiony na 30 dni. Zazwyczaj po utworzeniu nowej skrzynki pocztowej w programie Exchange Online ten okres przechowywania jest ustawiany na 14 dni. Ustawienie tej wartości na wartość maksymalną 30 dni daje więcej czasu na odzyskanie wszelkich danych, które zostały trwale usunięte (lub usunięte) z nieaktywnej skrzynki pocztowej. Możesz również wyłączyć odzyskiwanie pojedynczych elementów lub ustawić domyślny okres odzyskiwania pojedynczych elementów na 14 dni. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie odzyskiwania pojedynczych elementów dla skrzynki pocztowej](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery).

  - Hold is enabled, and the retention hold duration is set to 30 days. Oznacza Exchange Exchange przechowywania w całej organizacji lub organizacji albo w całej organizacji, Microsoft 365, które są przypisane do nowej skrzynki pocztowej, nie będą przetwarzane przez 30 dni. Dzięki temu zwracający pracownik lub nowy właściciel odzyskanej nieaktywnej skrzynki pocztowej może zarządzać starymi wiadomościami. W przeciwnym razie zasady przechowywania usługi Exchange lub Microsoft 365 mogą usuwać stare elementy skrzynki pocztowej (lub przenosić elementy do archiwaowej skrzynki pocztowej, jeśli jest włączona), które wygasły na podstawie ustawień skonfigurowanych dla zasad przechowywania usługi Exchange lub Microsoft 365. Po 30 dniach ważność przechowywania wygasa, właściwość **skrzynki pocztowej RetentionHoldEnabled** jest ustawiona na wartość **False**, a asystent folderów zarządzanych rozpoczyna przetwarzanie zasad przypisanych do skrzynki pocztowej. Jeśli nie potrzebujesz tego dodatkowego czasu, możesz po prostu usunąć hold przechowywania. Można również zwiększyć czas trwania przechowywania za pomocą polecenia **Set-Mailbox -EndDateForRetentionHold** . Aby uzyskać więcej informacji, zobacz [Umieść skrzynkę pocztową w miejscu przechowywania](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Jeśli chcesz zachować pierwotny stan nieaktywnej skrzynki pocztowej, umieść w nich stan przechowywania.** Aby uniemożliwić nowemu właścicielowi skrzynki pocztowej lub zasadom przechowywania trwałe usunięcie wszystkich wiadomości z odzyskanej nieaktywnej skrzynki pocztowej, możesz umieścić skrzynkę pocztową w związku z postępowaniem sądowym. Aby uzyskać więcej informacji, zobacz [Tworzenie postępowania w związku z postępowaniem sądowym](./create-a-litigation-hold.md).

- **Jakiego identyfikatora użytkownika można użyć podczas odzyskiwania nieaktywnej skrzynki pocztowej?** Po odzyskaniu nieaktywnej skrzynki pocztowej wartość parametru  *MicrosoftOnlineServicesID*  może różnić się od wartości oryginalnej, która była skojarzona z nieaktywną skrzynką pocztową. Możesz również użyć pierwotnego identyfikatora użytkownika. Jednak jak wspomniano wcześniej, podczas odzyskiwania nieaktywnej skrzynki pocztowej upewnij się, że wartości używane dla pól  *Name*  (Nazwa) i  *MicrosoftOnlineServicesID (Identyfikator usługi MicrosoftOnlineServicesID*  ) są unikatowe w Twojej organizacji.

- **Co zrobić, jeśli okres przechowywania skrzynki pocztowej dla nieaktywnej skrzynki pocztowej nie wygasł?** Jeśli nieaktywna skrzynka pocztowa została nieaktywna usunięta mniej niż 30 dni temu, nie można jej odzyskać za pomocą polecenia Nowa skrzynka pocztowa **-** Nieaktywna poczta. Aby je odzyskać, należy przywrócić odpowiednie konto użytkownika. Aby uzyskać więcej informacji, [zobacz Usuwanie użytkownika z organizacji](../admin/add-users/delete-a-user.md).

- **Skąd wiadomo, że okres przechowywania "miękkiego usunięcia" skrzynki pocztowej dla nieaktywnej skrzynki pocztowej wygasł?** Uruchom następujące polecenie:

  ```powershell
  Get-Mailbox -InactiveMailboxOnly <identity of inactive mailbox> | Format-List ExternalDirectoryObjectId
  ```

  Jeśli nie ma wartości właściwości **ExternalDirectoryObjectId** , okres przechowywania skrzynki pocztowej wygasł i możesz odzyskać nieaktywną skrzynkę pocztową, uruchamiając polecenie **New-Mailbox -InactiveMailbox** . Jeśli właściwość **ExternalDirectoryObjectId** ma wartość, okres przechowywania "miękkiego usunięcia" skrzynki pocztowej nie wygasł i trzeba odzyskać skrzynkę pocztową przez przywrócenie konta użytkownika. Zobacz [Usuwanie użytkownika z organizacji](../admin/add-users/delete-a-user.md).

- **Rozważ włączenie archiwatywnej skrzynki pocztowej po odzyskaniu nieaktywnej skrzynki pocztowej.** Dzięki temu zwracany użytkownik lub nowy pracownik może przenieść stare wiadomości do archiwaowej skrzynki pocztowej. Gdy archiwum wygaśnie, zasady archiwizacji, które są częścią domyślnych zasad przechowywania usługi Exchange przypisanych do skrzynek pocztowych programu Exchange Online, będą przenosić do archiwaowej skrzynki pocztowej elementy, które mają dwa lata lub więcej lat. Jeśli archiwalne skrzynki pocztowe nie zostaną włączyć, elementy starsze niż dwa lata pozostaną w podstawowej skrzynce pocztowej użytkownika. Aby uzyskać więcej informacji, zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md).