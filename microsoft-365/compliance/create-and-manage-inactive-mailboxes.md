---
title: Twórz nieaktywne skrzynki pocztowe i zarządzaj nimi
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
ms.assetid: 296a02bd-ebde-4022-900e-547acf38ddd7
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi, które zachowują zawartość usuniętych skrzynek pocztowych na platformie Microsoft 365.
ms.openlocfilehash: 15a9db1099eb687195d5c54b12d5bfca9a8c6f22
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634626"
---
# <a name="create-and-manage-inactive-mailboxes"></a>Twórz nieaktywne skrzynki pocztowe i zarządzaj nimi

Nieaktywne skrzynki pocztowe umożliwiają przechowywanie poczty e-mail byłych pracowników po opuszczeniu organizacji i mogą być dostępne dla autoryzowanych osób, którym udzielono [uprawnień do zbierania elektronicznych materiałów dowodowych ze względów](assign-ediscovery-permissions.md) prawnych lub zgodności. Na przykład administratorzy, funkcjonariusze ds. zgodności i menedżerowie rekordów, którzy mogą następnie używać wyszukiwania zawartości do wyszukiwania i eksportowania zawartości nieaktywnej skrzynki pocztowej. Nieaktywne skrzynki pocztowe nie mogą otrzymywać wiadomości e-mail i nie są wyświetlane w udostępnionej książce adresowej organizacji ani na innych listach.

Aby uzyskać więcej informacji na temat nieaktywnych skrzynek pocztowych, zobacz [Dowiedz się więcej o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md).

## <a name="create-an-inactive-mailbox"></a>Tworzenie nieaktywnej skrzynki pocztowej

Nieaktywność skrzynki pocztowej wymaga blokady w skrzynce pocztowej, a następnie usunięcia skrzynki pocztowej lub odpowiedniego konta użytkownika.

Aby skrzynka pocztowa była nieaktywna, musi mieć przypisaną licencję Exchange Online plan 2 (lub licencję Exchange Online plan 1 z licencją dodatku Exchange Online — archiwum), aby można było zastosować blokadę do skrzynki pocztowej przed jej usunięciem. Po usunięciu konta użytkownika każda licencja Exchange Online skojarzona z kontem użytkownika będzie dostępna do przypisania nowemu użytkownikowi.

Zalecamy użycie przechowywania usługi Microsoft 365 w celu zastosowania blokady w skrzynce pocztowej. Inne metody są omówione w [artykule Dowiedz się więcej o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md).

Najlepszym sposobem usunięcia skrzynki pocztowej jest usunięcie odpowiedniego konta użytkownika w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Aby uzyskać informacje na temat usuwania kont użytkowników, zobacz [Usuwanie użytkownika z organizacji](../admin/add-users/delete-a-user.md). Można jednak również usunąć skrzynkę pocztową przy użyciu polecenia cmdlet **Remove-Mailbox** w programie Exchange Online programu PowerShell. Aby uzyskać więcej informacji, zobacz [Usuwanie lub przywracanie skrzynek pocztowych użytkowników w Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes).

Poniższa tabela zawiera podsumowanie procesu tworzenia nieaktywnej skrzynki pocztowej dla różnych scenariuszy przechowywania.

<br/>

|Do...|Zrób to...|Result (Wynik)|
|---|---|---|
|Zachowywanie zawartości skrzynki pocztowej przez czas nieokreślony po opuszczeniu organizacji przez pracownika|1. Zastosuj ustawienia przechowywania platformy Microsoft 365, zachowując akcje dla skrzynki pocztowej (zasady przechowywania) lub określonych elementów poczty e-mail (co najmniej jedną etykietę przechowywania). <br /><br> 2. Poczekaj na zastosowanie ustawień przechowywania. <br /><br> 3. Usuń konto użytkownika platformy Microsoft 365.|Cała zawartość nieaktywnej skrzynki pocztowej z zastosowanymi ustawieniami przechowywania, w tym elementami w folderze Elementy możliwe do odzyskania, jest zachowywana przez czas nieokreślony.|
|Zachowaj całą zawartość skrzynki pocztowej przez określony okres po opuszczeniu organizacji przez pracownika, a następnie usuń skrzynkę pocztową|1. Zastosuj zasady przechowywania platformy Microsoft 365 do skrzynki pocztowej z ustawieniami przechowywania, które zachowują, a następnie usuwają elementy po upływie okresu przechowywania. <br /><br> 2. Poczekaj na zastosowanie ustawień przechowywania. <br /><br> 3. Usuń konto użytkownika platformy Microsoft 365.|Gdy okres przechowywania elementu skrzynki pocztowej wygaśnie, element zostanie przeniesiony do folderu Elementy możliwe do odzyskania, a następnie zostanie trwale usunięty (usunięty) ze skrzynki pocztowej nieaktywnej po upływie okresu przechowywania usuniętego elementu (dla skrzynek pocztowych programu Exchange). Okres przechowywania zasad przechowywania usługi Microsoft 365 jest zawsze oparty na oryginalnej dacie odebrania lub utworzenia elementu skrzynki pocztowej.|


> [!NOTE]
> Jeśli ustawienia przechowywania usługi Microsoft 365 skonfigurowane do przechowywania lub przechowywania, a następnie usuwania zawartości, są już stosowane do skrzynki pocztowej lub elementów skrzynki pocztowej albo blokada postępowania sądowego jest już umieszczona w skrzynce pocztowej, a następnie wszystko, co musisz zrobić, aby utworzyć nieaktywną skrzynkę pocztową, to usunąć odpowiednie konto użytkownika.


## <a name="view-a-list-of-inactive-mailboxes"></a>Wyświetlanie listy nieaktywnych skrzynek pocztowych

Aby wyświetlić listę nieaktywnych skrzynek pocztowych w organizacji:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> i zaloguj się przy użyciu poświadczeń dla administrator globalny lub konta administratora zgodności w organizacji.

2. W okienku nawigacji po lewej stronie wybierz pozycję **Pokaż wszystko**, a następnie wybierz pozycję **Zasady przechowywania** **zarządzania cyklem** >  życia danych.

3. Wybierz opcję **Nieaktywna skrzynka pocztowa** :

   ![Opcja Nieaktywna skrzynka pocztowa na stronie Zasady przechowywania z zarządzania cyklem życia danych.](../media/inactive-mailbox-option.png)

4. Na stronie **Nieaktywne skrzynki pocztowe** jest wyświetlana lista nieaktywnych skrzynek pocztowych. Wybierz jedną, aby wyświetlić szczegółowe informacje o tej nieaktywnej skrzynce pocztowej. Szczegóły obejmują identyfikator programu Exchange dla skrzynki pocztowej i to, czy jest on [w blokadzie postępowania sądowego](create-a-litigation-hold.md).
    
    W okienku szczegółów nie będą widoczne inne typy blokad, na przykład zasady przechowywania platformy Microsoft 365 lub blokada zbierania elektronicznych materiałów dowodowych. Aby znaleźć te informacje, zobacz [How to identify the type of hold placed on an Exchange Online mailbox (Jak zidentyfikować typ blokady umieszczonej w Exchange Online skrzynce pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md)).

Jeśli masz wiele nieaktywnych skrzynek pocztowych, możesz łatwiej wyszukać i posortować plik CSV pod kątem szczegółów widocznych na liście: na stronie **Nieaktywne skrzynki pocztowe** wybierz pozycję :::image type="icon" source="../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png"::: **Eksportuj**.

Alternatywnie możesz uruchomić następujące polecenie w programie Exchange Online programu PowerShell, aby wyświetlić listę nieaktywnych skrzynek pocztowych:

```powershell
 Get-Mailbox -InactiveMailboxOnly | FT DisplayName,PrimarySMTPAddress,WhenSoftDeleted
```

Możesz również uruchomić następujące polecenie, aby wyeksportować listę nieaktywnych skrzynek pocztowych i innych informacji do pliku CSV. W tym przykładzie plik CSV jest tworzony w bieżącym katalogu.

```powershell
Get-Mailbox -InactiveMailboxOnly | Select Displayname,PrimarySMTPAddress,DistinguishedName,ExchangeGuid,WhenSoftDeleted | Export-Csv InactiveMailboxes.csv -NoType
```

> [!NOTE]
> Istnieje możliwość, że nieaktywna skrzynka pocztowa może mieć taki sam adres SMTP jak aktywna skrzynka pocztowa użytkownika. W takim przypadku wartość właściwości **DistinguishedName** lub **ExchangeGuid** może służyć do unikatowego identyfikowania nieaktywnej skrzynki pocztowej.
  
## <a name="search-and-export-the-contents-of-an-inactive-mailbox"></a>Wyszukiwanie i eksportowanie zawartości nieaktywnej skrzynki pocztowej

Dostęp do zawartości nieaktywnej skrzynki pocztowej można uzyskać za pomocą narzędzia wyszukiwania zawartości w portal zgodności Microsoft Purview. Podczas wyszukiwania nieaktywnej skrzynki pocztowej możesz utworzyć zapytanie wyszukiwania słów kluczowych w celu wyszukania określonych elementów lub zwrócić całą zawartość nieaktywnej skrzynki pocztowej. Możesz wyświetlić podgląd wyników wyszukiwania lub wyeksportować wyniki wyszukiwania do pliku danych programu Outlook (PST) lub jako pojedyncze wiadomości e-mail. Aby zapoznać się z procedurami krok po kroku dotyczącymi wyszukiwania skrzynek pocztowych i eksportowania wyników wyszukiwania, zobacz następujące tematy:
  
- [Wyszukiwanie zawartości](content-search.md)

- [Eksportuj wyniki wyszukiwania](export-search-results.md)

Oto kilka kwestii, o których należy pamiętać podczas wyszukiwania nieaktywnych skrzynek pocztowych.
  
- Jeśli wyszukiwanie zawartości zawiera skrzynkę pocztową użytkownika i ta skrzynka pocztowa jest nieaktywna, wyszukiwanie zawartości będzie nadal przeszukiwać nieaktywną skrzynkę pocztową po ponownym uruchomieniu wyszukiwania po tym, jak stanie się ona nieaktywna.

- W niektórych przypadkach użytkownik może mieć aktywną skrzynkę pocztową i nieaktywną skrzynkę pocztową z tym samym adresem SMTP. W takim przypadku przeszukiwana będzie tylko określona skrzynka pocztowa wybrana jako lokalizacja wyszukiwania zawartości. Innymi słowy, jeśli dodasz skrzynkę pocztową użytkownika do wyszukiwania, nie można założyć, że będą przeszukiwane zarówno aktywne, jak i nieaktywne skrzynki pocztowe. przeszukiwana będzie tylko skrzynka pocztowa jawnie dodana do wyszukiwania.

- Zdecydowanie zalecamy unikanie aktywnej skrzynki pocztowej i nieaktywnej skrzynki pocztowej z tym samym adresem SMTP. Jeśli musisz ponownie użyć adresu SMTP, który jest obecnie przypisany do nieaktywnej skrzynki pocztowej, zalecamy odzyskanie nieaktywnej skrzynki pocztowej lub przywrócenie zawartości nieaktywnej skrzynki pocztowej do aktywnej skrzynki pocztowej (lub archiwum aktywnej skrzynki pocztowej), a następnie usunięcie nieaktywnej skrzynki pocztowej.

## <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Zmień czas trwania archiwizacji dla nieaktywnej skrzynki pocztowej

Po nieaktywności skrzynki pocztowej możesz zmienić czas przechowywania zastosowany do nieaktywnej skrzynki pocztowej.

Aby zapoznać się z procedurami krok po kroku, zobacz [Zmienianie czasu przechowywania nieaktywnej skrzynki pocztowej](change-the-hold-duration-for-an-inactive-mailbox.md).
  
## <a name="recover-an-inactive-mailbox"></a>Odzyskaj nieaktywną skrzynkę pocztową

Jeśli były pracownik wróci do twojej organizacji lub nowy pracownik zostanie zatrudniony do podjęcia obowiązków związanych z pracą zmarłego pracownika, możesz odzyskać zawartość nieaktywnej skrzynki pocztowej. 

Po odzyskaniu nieaktywnej skrzynki pocztowej skrzynka pocztowa jest konwertowana na nową skrzynkę pocztową, zawartość i struktura folderów nieaktywnej skrzynki pocztowej są zachowywane, a skrzynka pocztowa jest połączona z nowym kontem użytkownika. Po jej odzyskaniu nieaktywna skrzynka pocztowa już nie istnieje. 

Aby zapoznać się z procedurami krok po kroku i więcej informacji na temat dzieje się po odzyskaniu nieaktywnej skrzynki pocztowej, zobacz [Odzyskiwanie nieaktywnej skrzynki pocztowej](recover-an-inactive-mailbox.md).
  
## <a name="restore-the-contents-of-an-inactive-mailbox-to-another-mailbox"></a>Przywracanie zawartości nieaktywnej skrzynki pocztowej do innej skrzynki pocztowej

Jeśli inny pracownik przejmuje obowiązki związane z pracą byłego pracownika lub jeśli inna osoba potrzebuje dostępu do zawartości nieaktywnej skrzynki pocztowej, możesz przywrócić (lub scalić) zawartość nieaktywnej skrzynki pocztowej do istniejącej skrzynki pocztowej. 

Po przywróceniu nieaktywnej skrzynki pocztowej zawartość jest kopiowana do innej skrzynki pocztowej. Nieaktywna skrzynka pocztowa jest zachowywana i pozostaje nieaktywną skrzynką pocztową. Nieaktywną skrzynkę pocztową można nadal przeszukiwać przy użyciu zbierania elektronicznych materiałów dowodowych, jej zawartość można przywrócić do innej skrzynki pocztowej lub odzyskać lub usunąć ją w późniejszym terminie. 

Aby zapoznać się z procedurami krok po kroku, zobacz [Przywracanie nieaktywnej skrzynki pocztowej](restore-an-inactive-mailbox.md).
  
## <a name="delete-an-inactive-mailbox"></a>Usuń nieaktywną skrzynkę pocztową

Jeśli nie musisz już zachowywać zawartości nieaktywnej skrzynki pocztowej, możesz trwale usunąć nieaktywną skrzynkę pocztową, usuwając blokadę zastosowaną do nieaktywnej skrzynki pocztowej. Skrzynka pocztowa zostanie zachowana przez 183 dni po usunięciu zasad blokady lub przechowywania i będzie można jej odzyskać w tym czasie. Po 183 dniach skrzynka pocztowa zostanie oznaczona do trwałego usunięcia, a skrzynka pocztowa stanie się nie do odzyskania. 

Aby zapoznać się z procedurami krok po kroku dotyczącymi usuwania blokady lub zasad przechowywania w celu trwałego usunięcia nieaktywnej skrzynki pocztowej, zobacz [Usuwanie nieaktywnej skrzynki pocztowej](delete-an-inactive-mailbox.md).
