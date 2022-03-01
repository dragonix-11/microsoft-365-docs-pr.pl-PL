---
title: Przywracanie nieaktywnej skrzynki pocztowej
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
ms.assetid: 97e06a7a-ef9a-4ce8-baea-18b9e20449a3
description: Dowiedz się, jak przywrócić (lub scalić) zawartość nieaktywnej skrzynki pocztowej do istniejącej skrzynki pocztowej.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aaf0ce7f67ae0146beceeeb667263908d7cff75d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010641"
---
# <a name="restore-an-inactive-mailbox"></a>Przywracanie nieaktywnej skrzynki pocztowej

Nieaktywna skrzynka pocztowa (typ "miękkiego usunięcia skrzynki pocztowej") służy do zachowywania wiadomości e-mail byłego pracownika po odejechaniu z organizacji. Jeśli inny pracownik przejmie obowiązki odchodzonego pracownika lub wróci do organizacji, można udostępnić użytkownikowi zawartość nieaktywnej skrzynki pocztowej na dwa sposoby:

- **Przywracanie nieaktywnej skrzynki pocztowej** Jeśli inny pracownik przejmie obowiązki odchodzonego pracownika lub jeśli inny użytkownik potrzebuje dostępu do zawartości nieaktywnej skrzynki pocztowej, możesz przywrócić (lub scalić) zawartość nieaktywnej skrzynki pocztowej do istniejącej skrzynki pocztowej. Możesz również przywrócić archiwum z nieaktywnej skrzynki pocztowej. Po przywróceniu nieaktywna skrzynka pocztowa jest zachowywana i zachowywana jako nieaktywna skrzynka pocztowa. W tym temacie opisano procedury przywracania nieaktywnej skrzynki pocztowej.

- **Odzyskiwanie nieaktywnej skrzynki pocztowej** Jeśli odchodzący pracownik wraca do organizacji lub gdy nowy pracownik jest zatrudniony do  obowiązków odchodzonego pracownika, można odzyskać zawartość nieaktywnej skrzynki pocztowej. Ta metoda konwertuje nieaktywną skrzynkę pocztową na nową skrzynkę pocztową zawierającą zawartość tej nieaktywnej skrzynki pocztowej. Po ich odzyskaniu nieaktywna skrzynka pocztowa już nie istnieje. Aby uzyskać procedury krok po kroku, zobacz Odzyskiwanie nieaktywnej skrzynki pocztowej w [programie Office 365](recover-an-inactive-mailbox.md).

Zobacz [sekcję Więcej informacji](#more-information) w tym artykule, aby uzyskać więcej informacji na temat różnic między przywracaniem i odzyskiwaniem nieaktywnej skrzynki pocztowej.

> [!NOTE]
> Nie można odzyskiwać ani przywracać nieaktywnych skrzynek pocztowych skonfigurowanych przy użyciu archiwum powiększania automatycznego. Jeśli chcesz odzyskać dane z nieaktywnej skrzynki pocztowej za pomocą archiwum rozszerzanego automatycznie, za pomocą wyszukiwania zawartości wyeksportuj dane ze skrzynki pocztowej, a następnie zaimportuj je do innej skrzynki pocztowej. Aby uzyskać instrukcje, zobacz następujące tematy:
>
> - [Przeszukiwanie zawartości](content-search.md)
> - [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md)

## <a name="requirements-to-restore-an-inactive-mailbox"></a>Wymagania dotyczące przywracania nieaktywnej skrzynki pocztowej

- Aby przywrócić nieaktywną skrzynkę pocztową, musisz użyć programu Exchange Online PowerShell. Nie możesz korzystać z centrum administracyjnego usługi Exchange(EAC). Instrukcje krok po kroku można znaleźć w [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Uruchom następujące polecenie w programie Exchange Online PowerShell, aby uzyskać informacje o tożsamości dla nieaktywnych skrzynek pocztowych w Twojej organizacji.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Użyj informacji zwróconych za pomocą tego polecenia, aby zidentyfikować i przywrócić określoną nieaktywną skrzynkę pocztową.

- Aby uzyskać więcej informacji o nieaktywnych skrzynkach pocztowych, zobacz [Nieaktywne skrzynki pocztowe w](inactive-mailboxes-in-office-365.md) Office 365.

## <a name="restore-inactive-mailboxes"></a>Przywracanie nieaktywnych skrzynek pocztowych

Użyj polecenia **cmdlet New-MailboxRestoreRequest** z parametrami  _SourceMailbox_ i  _TargetMailbox_ , aby przywrócić zawartość nieaktywnej skrzynki pocztowej do istniejącej skrzynki pocztowej. Aby uzyskać więcej informacji na temat używania tego polecenia cmdlet, zobacz [New-MailboxRestoreRequest](/powershell/module/exchange/new-mailboxrestorerequest).

Zanim będzie można przywrócić nieaktywną skrzynkę pocztową, musisz dodać LegacyExchangeDN nieaktywnej skrzynki pocztowej do docelowej skrzynki pocztowej jako adres serwera proxy X500 docelowej skrzynki pocztowej. Należy to zrobić, ponieważ polecenie cmdlet **New-MailboxRestoreRequest** sprawdza, czy wartość właściwości **LegacyExchangeDN** źródłowej i docelowej skrzynki pocztowej jest taka sama. Po przywróceniu nieaktywnej skrzynki pocztowej możesz opcjonalnie usunąć LegacyExchangeDN nieaktywnej skrzynki pocztowej ze źródłowej skrzynki pocztowej. Przed usunięciem LegacyExchangeDN należy zaczekać na ukończenie żądania przywrócenia skrzynki pocztowej.

Wykonaj poniższe czynności, aby przywrócić nieaktywną skrzynkę pocztową do istniejącej skrzynki pocztowej:

1. Utwórz zmienną zawierającą właściwości nieaktywnej skrzynki pocztowej.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > W poprzednim poleceniu należy użyć wartości właściwości **DistinguishedName** (Nazwa odróżniana) lub **ExchangeGUID (ExchangeGUID** ), aby zidentyfikować nieaktywną skrzynkę pocztową. Te właściwości są unikatowe dla każdej skrzynki pocztowej w organizacji, natomiast istnieje możliwość, że aktywna i nieaktywna skrzynka pocztowa może mieć taki sam podstawowy adres SMTP.

2. Wyświetl LegacyExchangeDN nieaktywnej skrzynki pocztowej, aby dodać ją jako adres serwera proxy do docelowej skrzynki pocztowej w następnym kroku.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Dodaj LegacyExchangeDN nieaktywnej skrzynki pocztowej jako adres serwera proxy X500 do docelowej skrzynki pocztowej.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Przywracanie zawartości nieaktywnej skrzynki pocztowej do istniejącej skrzynki pocztowej. Zawartość nieaktywnej skrzynki pocztowej (źródłowej skrzynki pocztowej) zostanie scalona z odpowiadającymi im folderami w istniejącej skrzynce pocztowej (docelowej skrzynce pocztowej).

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $inactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> 
   ```

   Możesz również określić folder najwyższego poziomu w docelowej skrzynce pocztowej, w którym chcesz przywrócić zawartość z nieaktywnej skrzynki pocztowej. Jeśli w docelowej skrzynce pocztowej nie istnieje jeszcze określony folder docelowy lub docelowa struktura folderów, zostanie ona utworzona w trakcie procesu przywracania.

   W tym przykładzie elementy i podfoldery skrzynki pocztowej są kopiowane z nieaktywnej skrzynki pocztowej do folderu o nazwie "Nieaktywna skrzynka pocztowa" w strukturze folderów najwyższego poziomu w docelowej skrzynce pocztowej.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> -TargetRootFolder "Inactive Mailbox"
   ```

5. Po zakończeniu żądania przywrócenia możesz opcjonalnie usunąć LegacyExchangeDN nieaktywnej skrzynki pocztowej z docelowej skrzynki pocztowej. Pozostawienie LegacyExchangeDN z nieaktywnej skrzynki pocztowej nie będzie mieć wpływu na docelową skrzynkę pocztową.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="restore-the-archive-from-an-inactive-mailbox"></a>Przywracanie archiwum z nieaktywnej skrzynki pocztowej

Jeśli nieaktywna skrzynka pocztowa ma archiwacyjną skrzynkę pocztową, możesz ją również przywrócić do archiwatywnej skrzynki pocztowej istniejącej skrzynki pocztowej. Aby przywrócić archiwum z nieaktywnej skrzynki pocztowej, należy dodać przełączniki _SourceIsArchive_ i _TargetIsArchive_ do polecenia służącego do przywracania nieaktywnej skrzynki pocztowej.

1. Utwórz zmienną zawierającą właściwości nieaktywnej skrzynki pocztowej.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!NOTE]
   > W poprzednim poleceniu należy użyć wartości właściwości **DistinguishedName** (Nazwa odróżniana) lub **ExchangeGUID (ExchangeGUID** ), aby zidentyfikować nieaktywną skrzynkę pocztową. Te właściwości są unikatowe dla każdej skrzynki pocztowej w organizacji, natomiast istnieje możliwość, że aktywna i nieaktywna skrzynka pocztowa może mieć taki sam podstawowy adres SMTP.

2. Wyświetl LegacyExchangeDN nieaktywnej skrzynki pocztowej, aby dodać ją jako adres serwera proxy do docelowej skrzynki pocztowej w następnym kroku.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Dodaj LegacyExchangeDN nieaktywnej skrzynki pocztowej jako adres serwera proxy X500 do docelowej skrzynki pocztowej.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Przywracanie zawartości archiwum z nieaktywnej skrzynki pocztowej (archiwum źródłowe) do archiwum istniejącej skrzynki pocztowej (archiwum docelowe). W tym przykładzie zawartość z archiwum źródłowego jest kopiowana do folderu o nazwie "Nieaktywne archiwum skrzynki pocztowej" w archiwum docelowej skrzynki pocztowej.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -SourceIsArchive -TargetMailbox <identity of target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox Archive"
   ```

5. Po zakończeniu żądania przywrócenia możesz opcjonalnie usunąć LegacyExchangeDN nieaktywnej skrzynki pocztowej z docelowej skrzynki pocztowej. Pozostawienie LegacyExchangeDN z nieaktywnej skrzynki pocztowej nie będzie mieć wpływu na docelową skrzynkę pocztową.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="more-information"></a>Więcej informacji

- **Jaka jest główna różnica między odzyskiwaniem a przywracaniem nieaktywnej skrzynki pocztowej?** Gdy odzyskasz nieaktywną skrzynkę pocztową, zostanie ona przekonwertowana na nową skrzynkę pocztową. Zawartość i struktura folderów nieaktywnej skrzynki pocztowej są zachowywane, a skrzynka pocztowa jest połączona z nowym kontem użytkownika. Po ich odzyskaniu nieaktywna skrzynka pocztowa już nie istnieje, a wszelkie zmiany zawartości w nowej skrzynce pocztowej będą mieć wpływ na zawartość, która pierwotnie była wstrzymywana w nieaktywnej skrzynce pocztowej. Natomiast w przypadku przywracania nieaktywnej skrzynki pocztowej zawartość jest jedynie kopiowana do innej skrzynki pocztowej. Nieaktywna skrzynka pocztowa jest zachowywana i pozostaje nieaktywną skrzynką pocztową. Wszelkie zmiany wprowadzone w zawartości docelowej skrzynki pocztowej nie mają wpływu na oryginalną zawartość w nieaktywnej skrzynce pocztowej. Nieaktywną skrzynkę pocztową nadal można przeszukiwać za pomocą narzędzia Przeszukiwanie [zawartości, można](content-search.md) przywrócić jej zawartość do innej skrzynki pocztowej lub można ją odzyskać lub usunąć później.

- **Jak znaleźć nieaktywne skrzynki pocztowe?** To polecenie umożliwia wyświetlenie listy nieaktywnych skrzynek pocztowych w organizacji i wyświetlenie informacji przydatnych przy przywracaniu nieaktywnej skrzynki pocztowej.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,PrimarySMTPAddress,DistinguishedName,ExchangeGUID,LegacyExchangeDN,ArchiveStatus
  ```

- **Użyj zasad Microsoft 365 przechowywania lub funkcji Postępowaniem sądowym albo do zachowywania nieaktywnej zawartości skrzynki pocztowej.** Jeśli chcesz zachować stan nieaktywnej skrzynki pocztowej po jej przywróceniu, możesz zastosować zasady przechowywania usługi [Microsoft 365](retention.md) do docelowej skrzynki pocztowej lub umieścić docelową skrzynkę pocztową w [Postępowaniem sądowym](create-a-litigation-hold.md przed przywróceniem nieaktywnej skrzynki pocztowej. Pozwoli to zapobiec trwałemu usunięciu wszystkich elementów z nieaktywnej skrzynki pocztowej po ich przywróceniu do docelowej skrzynki pocztowej.

- **Włącz przechowywanie dla docelowej skrzynki pocztowej przed przywróceniem nieaktywnej skrzynki pocztowej.** Ponieważ elementy skrzynki pocztowej z nieaktywnej skrzynki pocztowej mogą być stare, przed przywróceniem nieaktywnej skrzynki pocztowej warto rozważyć włączenie przechowywania w docelowej skrzynce pocztowej. Po dotrzymaniu skrzynki pocztowej przypisane do skrzynki pocztowej zasady przechowywania, które do niego przypisano, nie będą przetwarzane, dopóki nie zostanie usunięte przechowywanie lub do czasu wygaśnięcia okresu przechowywania. Dzięki temu właściciel docelowej skrzynki pocztowej może zarządzać starymi wiadomościami z nieaktywnej skrzynki pocztowej. W przeciwnym razie zasady przechowywania mogą usuwać stare elementy (lub przenosić elementy do archiwaowej skrzynki pocztowej, jeśli zostały włączone), które wygasły na podstawie ustawień przechowywania skonfigurowanych dla docelowej skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Umieść skrzynkę pocztową w miejscu przechowywania w Exchange Online](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Możesz użyć innych parametrów z poleceniem cmdlet New-MailboxRestoreRequest, aby zaimplementować różne scenariusze przywracania dla nieaktywnych skrzynek pocztowych.** Możesz na przykład uruchomić to polecenie, aby przywrócić archiwum z nieaktywnej skrzynki pocztowej do podstawowej skrzynki pocztowej docelowej skrzynki pocztowej.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -SourceIsArchive -TargetMailbox <target mailbox> -TargetRootFolder "Inactive Mailbox Archive"
  ```

  To polecenie pozwala także przywrócić nieaktywną podstawową skrzynkę pocztową do archiwum docelowej skrzynki pocztowej.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -TargetMailbox <target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox"
  ```

- **Do czego służy parametr TargetRootFolder?** Jak wyjaśniono wcześniej, za pomocą parametru **TargetRootFolder** można określić folder w górnej części struktury folderów (nazywanej również katalogiem głównym) w docelowej skrzynce pocztowej, w której zostanie przywrócona zawartość nieaktywnej skrzynki pocztowej. Jeśli nie używasz tego parametru, elementy skrzynki pocztowej z nieaktywnej skrzynki pocztowej są scalane z odpowiadającymi im folderami domyślnymi docelowej skrzynki pocztowej, a foldery niestandardowe są ponownie tworzone w katalogu głównym docelowej skrzynki pocztowej. Na poniższych ilustracjach przedstawiono różnice między nieukończaniem i używaniem **parametru TargetRootFolder** .

  **Hierarchia folderów w docelowej skrzynce pocztowej, gdy parametr TargetRootFolder nie jest używany**

  ![Zrzut ekranu, gdy parametr TargetRootFolder nie jest używany.](../media/76a759af-f483-4d1c-8cc7-243435b5562e.png)

  **Hierarchia folderów w docelowej skrzynce pocztowej, gdy jest używany parametr TargetRootFolder**

  ![Zrzut ekranu, gdy używany jest parametr TargetRootFolder.](../media/300da592-7323-48db-b8a4-07012259d113.png)
