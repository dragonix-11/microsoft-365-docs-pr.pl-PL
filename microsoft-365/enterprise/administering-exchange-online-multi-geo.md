---
title: Administrowanie Exchange Online w środowisku wielolokalowym
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-mar2020
ms.localizationpriority: medium
description: Dowiedz się, jak administrować Exchange Online wielowymiarowych lokalizacji geograficznych w środowisku Microsoft 365 za pomocą programu PowerShell.
ms.openlocfilehash: 2e4be2fd506f89579866c61bbf4a8a41aadc0d03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985092"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administrowanie Exchange Online w środowisku wielolokalowym

Exchange Online programu PowerShell jest wymagany do wyświetlania i konfigurowania właściwości wielu lokalizacji Microsoft 365 danych. Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Aby wyświetlić właściwość **PreferredDataLocation** (Preferowana lokalizacjadanych) w obiektach użytkownika, potrzebny jest moduł programu [Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) w wersji 1.1.166.0 lub nowszej w wersji 1.x. Obiekty użytkowników synchronizowane za pośrednictwem AAD Połączenie z AAD nie mogą bezpośrednio zmodyfikować wartości **preferredDataLocation** za pośrednictwem AAD PowerShell. Obiekty użytkowników tylko w chmurze można modyfikować za pośrednictwem AAD PowerShell. Aby nawiązać połączenie z programem PowerShell usługi Azure AD, [Połączenie się z programem PowerShell](connect-to-microsoft-365-powershell.md).

W Exchange Online wielolokalizacji nie trzeba ręcznie dodawać lokalizacji geograficznych do dzierżawy. Po otrzymaniu wpisu w Centrum wiadomości z komunikatem Multi-geo is ready for Exchange Online, wszystkie dostępne lokalizacje geograficzne będą gotowe i skonfigurowane do użycia.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Połączenie bezpośrednio do lokalizacji geograficznej za pomocą programu Exchange Online PowerShell

Zazwyczaj program PowerShell Exchange Online się z centralną lokalizacją geograficzną. Możesz jednak również połączyć się bezpośrednio z lokalizacjami geolokalizacji satelitarnych. Ze względu na ulepszenia wydajności zalecamy nawiązywanie bezpośredniego połączenia z lokalizacją geolokalizacji satelitarnej, gdy zarządzasz tylko użytkownikami w tej lokalizacji.

Wymagania dotyczące instalowania i używania modułu V2 EXO opisano w tece Instalowanie i obsługa [modułu V2 funkcji EXO](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

Aby połączyć Exchange Online PowerShell z określoną lokalizacją geograficzną, parametr *ConnectionUri* różni się od zwykłych instrukcji dotyczących połączenia. Pozostałe polecenia i wartości są takie same.

W szczególności należy dodać wartość `?email=<emailaddress>` na końcu wartości _ConnectionUri_ . `<emailaddress>` to adres e-mail dowolnej **skrzynki** pocztowej w docelowej lokalizacji geograficznej. Twoje uprawnienia do tej skrzynki pocztowej lub relacji z poświadczeniami nie są czynnikiem; adres e-mail po prostu Exchange Online program PowerShell, gdzie się połączyć.

Microsoft 365 lub Microsoft 365 GCC zwykle nie muszą używać parametru _ConnectionUri_, aby połączyć się z programem Exchange Online PowerShell. Jednak aby połączyć się z określoną lokalizacją geograficzną, musisz użyć parametru _ConnectionUri_ , aby można było użyć wartości `?email=<emailaddress>` .

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>Połączenie lokalizacji geograficznej w programie Exchange Online PowerShell

Poniższe instrukcje dotyczące połączenia działają w przypadku kont, które są lub nie zostały skonfigurowane do uwierzytelniania wieloskładnikowego (MFA).

1. W Windows PowerShell exo V2 załaduj moduł EXO, uruchamiając następujące polecenie:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. W poniższym przykładzie admin@contoso.onmicrosoft.com kontem administratora, a docelowa lokalizacja geograficzna to miejsce, w którym olga@contoso.onmicrosoft.com się skrzynka pocztowa.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. Wprowadź hasło dostępu do admin@contoso.onmicrosoft.com w wyświetlonym monitie. Jeśli dla konta skonfigurowano uwierzytelniania MFA, musisz również wprowadzić kod zabezpieczeń.

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Wyświetlanie dostępnych lokalizacji geograficznych skonfigurowanych w Exchange Online organizacji

Aby wyświetlić listę skonfigurowanych lokalizacji geograficznych w programie Microsoft 365 Multi-Geo, uruchom następujące polecenie w programie Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Wyświetlanie centralnej lokalizacji geograficznej organizacji Exchange Online organizacji

Aby wyświetlić centralną lokalizację geograficzną dzierżawy, uruchom następujące polecenie w programie Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Znajdowanie lokalizacji geograficznej skrzynki pocztowej

Polecenie **cmdlet Get-Mailbox** w programie Exchange Online PowerShell wyświetla następujące właściwości dotyczące wielu lokalizacji geograficznych w skrzynkach pocztowych:

- **Database** (Baza danych): Pierwsze 3 litery nazwy bazy danych odpowiadają kodowi geograficznemu, który informuje o miejscu, w którym obecnie znajduje się skrzynka pocztowa. W przypadku skrzynek pocztowych archiwum online należy użyć właściwości **ArchiveDatabase** .

- **MailboxRegion**: Określa kod lokalizacji geograficznej ustawiony przez administratora (zsynchronizowany z **preferredDataLocation** w usłudze Azure AD).

- **MailboxRegionLastUpdateTime**: Wskazuje, kiedy ostatnia aktualizacja to MailboxRegion (automatycznie lub ręcznie).

Aby wyświetlić te właściwości skrzynki pocztowej, użyj następującej składni:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Aby na przykład wyświetlić informacje o lokalizacji geograficznej skrzynki chris@contoso.onmicrosoft.com pocztowej, uruchom następujące polecenie:

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Wynik polecenia wygląda następująco:

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> [!NOTE]
> Jeśli kod lokalizacji geograficznej w nazwie bazy danych jest niezgodny z wartością **MailboxRegion**, skrzynka pocztowa zostanie automatycznie przeniesiona do kolejki adresatów i przeniesiona do lokalizacji geograficznej określonej przez wartość **MailboxRegion** (program Exchange Online wyszukuje niezgodność między tymi wartościami właściwości).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Przenoszenie istniejącej skrzynki pocztowej dostępnej tylko w chmurze do określonej lokalizacji geograficznej

Użytkownik tylko w chmurze to użytkownik, który nie jest synchronizowany z dzierżawą za pośrednictwem AAD Połączenie. Tego użytkownika utworzono bezpośrednio w usłudze Azure AD. Użyj cmdlet **Get-MsolUser** i **Set-MsolUser** w module usługi Azure AD dla programu Windows PowerShell, aby wyświetlić lub określić lokalizację geograficzną, w której będzie przechowywana skrzynka pocztowa użytkownika przechowywana tylko w chmurze.

Aby wyświetlić wartość **PreferredDataLocation** (Preferowana lokalizacjadanych) dla użytkownika, użyj tej składni w programie PowerShell usługi Azure AD:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Aby na przykład wyświetlić wartość **PreferredDataLocation** (Preferowana lokalizacjadanych) dla michelle@contoso.onmicrosoft.com użytkownika, uruchom następujące polecenie:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Aby zmodyfikować wartość **PreferredDataLocation** (Preferowana lokalizacjadanych) obiektu użytkownika tylko w chmurze, użyj następującej składni w programie PowerShell usługi Azure AD:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

Aby na przykład ustawić dla użytkownika wartość **preferredDataLocation** (Preferowana lokalizacjadanych) na geolokalizację Unii Europejskiej (EUR) dla użytkownika michelle@contoso.onmicrosoft.com uruchom następujące polecenie:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - Jak wspomniano wcześniej, nie można użyć tej procedury dla synchronizowanych obiektów użytkowników z lokalnej usługi Active Directory. Należy zmienić wartość **PreferredDataLocation (Preferowana lokalizacjadanych**) w usłudze Active Directory i zsynchronizować ją przy użyciu AAD Połączenie. Aby uzyskać więcej informacji, [zobacz Azure Active Directory Połączenie: Konfigurowanie preferowanej lokalizacji danych dla Microsoft 365 zasobów](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - Czas przenoszenia skrzynki pocztowej do nowej lokalizacji geograficznej zależy od kilku czynników:
>
>   - Rozmiar i typ skrzynki pocztowej.
>   - Liczba przenoszonych skrzynek pocztowych.
>   - Dostępność zasobów do przeniesienia.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>Przenoszenie nieaktywnej skrzynki pocztowej do określonego geolokalizacji

Nie można przenosić nieaktywnych skrzynek pocztowych, które są zachowywane na potrzeby zachowania zgodności (na przykład w przypadku skrzynek pocztowych w związku z postępowaniem sądowym), zmieniając ich wartość **PreferredDataLocation** (Preferowana lokalizacjadanych). Aby przenieść nieaktywną skrzynkę pocztową do innej lokalizacji geograficznej, wykonaj następujące czynności:

1. Odzyskiwanie nieaktywnej skrzynki pocztowej. Aby uzyskać instrukcje, zobacz [Odzyskiwanie nieaktywnej skrzynki pocztowej](../compliance/recover-an-inactive-mailbox.md).

2. Uniemożliwiaj asystentowi \<MailboxIdentity\> folderów zarządzanych przetwarzanie odzyskanej skrzynki pocztowej, zastępując nim nazwę, alias, konto lub adres e-mail skrzynki pocztowej i uruchamiając następujące polecenie w programie [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. Przypisz **licencję Exchange Online Plan 2** do odzyskanej skrzynki pocztowej. Ten krok jest wymagany, aby umieścić skrzynkę pocztową z powrotem w związku z postępowaniem sądowym. Aby uzyskać instrukcje, [zobacz Przypisywanie licencji użytkownikom](../admin/manage/assign-licenses-to-users.md).

4. Skonfiguruj wartość **PreferredDataLocation (Preferowana lokalizacjadanych** ) w skrzynce pocztowej zgodnie z opisem w poprzedniej sekcji.

5. Po potwierdzeniu, że skrzynka pocztowa została przeniesiona do nowej lokalizacji geograficznej, umieść odzyskaną skrzynkę pocztową z powrotem w związku z postępowaniem sądowym. Aby uzyskać instrukcje, zobacz [Jak umieścić skrzynkę pocztową w związku z postępowaniem sądowym](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. Po sprawdzeniu, czy jest w nim sprawdzana ta zawieszenie w związku z postępowaniem sądowym, \<MailboxIdentity\> zezwomij asystentowi folderów zarządzanych na jej kolejne przetwarzanie, zastępując nazwą, aliasem, kontem lub adresem e-mail skrzynki pocztowej i uruchamiając następujące polecenie w programie [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. Ponownie zdezaktualij skrzynkę pocztową, usuwając konto użytkownika skojarzone ze skrzynką pocztową. Aby uzyskać instrukcje, [zobacz Usuwanie użytkownika z organizacji](../admin/add-users/delete-a-user.md). Ten krok zwalnia również licencję Exchange Online Plan 2 do innych zastosowań.

**Uwaga**: Przeniesienie nieaktywnej skrzynki pocztowej do innej lokalizacji geograficznej może mieć wpływ na wyniki wyszukiwania zawartości lub na możliwość przeszukiwania skrzynki pocztowej z poprzedniej lokalizacji geograficznej. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i eksportowanie zawartości w środowiskach wielowymiarowych](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Tworzenie nowych skrzynek pocztowych w chmurze w określonej lokalizacji geograficznej

Aby utworzyć nową skrzynkę pocztową w określonej lokalizacji geograficznej, wykonaj jedną z poniższych czynności:

- Skonfiguruj wartość **PreferredDataLocation** (Preferowana lokalizacjadanych [](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location)) zgodnie z opisem w poprzedniej sekcji Przenoszenie istniejącej skrzynki  pocztowej dostępnej tylko w chmurze do określonej sekcji lokalizacji geograficznej przed utworzeniem jej w Exchange Online. Na przykład skonfiguruj wartość **PreferredDataLocation** (Preferowana lokalizacjadanych) na użytkowniku przed przypisaniem licencji.

- Przypisz licencję w tym samym czasie, gdy ustawiasz wartość **PreferredDataLocation (Preferowana lokalizacjadanych** ).

Aby utworzyć nowego licencjonowanego użytkownika tylko w chmurze (AAD Połączenie zsynchronizowanego) w określonej lokalizacji geograficznej, użyj następującej składni w programie PowerShell usługi Azure AD:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

W tym przykładzie należy utworzyć nowe konto użytkownika Elżbiety B przed następującymi wartościami:

- Główna nazwa użytkownika: ebrunner@contoso.onmicrosoft.com
- Imię: Elizabeth
- Nazwisko: Brunner
- Nazwa wyświetlana: Elizabeth Brunner
- Hasło: losowo wygenerowane i wyświetlone w wynikach polecenia (ponieważ nie korzystamy z *parametru Password* )
- Licencja: `contoso:ENTERPRISEPREMIUM` (E5)
- Lokalizacja: Australia (Australia)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Aby uzyskać więcej informacji na temat tworzenia nowych kont użytkowników i znajdowania wartości licenseAssignment w programie PowerShell usługi Azure AD, zobacz Tworzenie kont użytkowników za pomocą programu [PowerShell](create-user-accounts-with-microsoft-365-powershell.md) i Wyświetlanie licencji i usług za pomocą programu [PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> Jeśli używasz programu Exchange Online PowerShell do włączania skrzynki pocztowej i potrzebujesz, aby została utworzona bezpośrednio w lokalizacji geograficznej określonej w **preferredDataLocation**, musisz użyć polecenia cmdlet programu Exchange Online, takiego jak **Enable-Mailbox** lub **New-Mailbox**, bezpośrednio w usłudze w chmurze. Jeśli użyjemy polecenia cmdlet **Enable-RemoteMailbox** w lokalnym programie Exchange PowerShell, skrzynka pocztowa zostanie utworzona w centralnej lokalizacji geograficznej.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Wdowe istniejące lokalne skrzynki pocztowe w określonej lokalizacji geograficznej

Za pomocą standardowych procesów i narzędzi dołączania można przeprowadzić migrację skrzynki pocztowej z lokalnej organizacji programu Exchange do programu Exchange Online, na przykład pulpitu nawigacyjnego migracji w Programie [EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) i polecenia cmdlet [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) w programie Exchange Online PowerShell.

Pierwszym krokiem jest sprawdzenie, czy dla każdej skrzynki pocztowej istnieje obiekt użytkownika, a także sprawdzenie, czy w usłudze Azure AD skonfigurowano prawidłową wartość **PreferredDataLocation** (Preferowana lokalizacjadanych). Narzędzia dołączające będą przestrzegać wartości **PreferredDataLocation** i będą migrować skrzynki pocztowe bezpośrednio do określonej lokalizacji geograficznej.

Możesz też wykonać poniższe czynności, aby wychować skrzynki pocztowe bezpośrednio w określonej lokalizacji geograficznej przy użyciu polecenia cmdlet [New-MoveRequest](/powershell/module/exchange/new-moverequest) w programie Exchange Online PowerShell.

1. Sprawdź, czy obiekt użytkownika istnieje dla każdej skrzynki pocztowej, która ma zostać  wniesiona, i czy dla preferowanej lokalizacji danych jest ustawiona żądana wartość w usłudze Azure AD. Wartość **preferredDataLocation (** Preferowana lokalizacjadanych) zostanie zsynchronizowana z atrybutem **MailboxRegion** odpowiedniego obiektu użytkownika poczty w programie Exchange Online.

2. Połączenie bezpośrednio do określonej lokalizacji geograficznej satelitarnej, korzystając z instrukcji dotyczących połączenia z wcześniejszej wersji tego tematu.

3. W Exchange Online PowerShell przechowuj poświadczenia administratora lokalnego, które są używane do przeprowadzania migracji skrzynki pocztowej w zmiennej, uruchamiając następujące polecenie:

   ```powershell
   $RC = Get-Credential
   ```

4. W Exchange Online PowerShell utwórz nowe **new-MoveRequest** podobne do następującego przykładu:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. Powtórz krok 4 dla każdej skrzynki pocztowej, z Exchange lokalnej do lokalizacji geograficznej satelitarnej, z którym obecnie masz połączenie.

6. Jeśli chcesz przeprowadzić migrację dodatkowych skrzynek pocztowych do różnych lokalizacji geograficznych satelitarnych, powtórz kroki od 2 do 4 dla każdej konkretnej lokalizacji.

## <a name="multi-geo-reporting"></a>Raportowanie wielu lokalizacji geograficznych

**Raporty użycia wielu lokalizacji geograficznych** w centrum administracyjne platformy Microsoft 365 liczbę użytkowników według lokalizacji geograficznej. Raport przedstawia rozkład użytkowników w bieżącym miesiącu oraz dane historyczne z ostatnich 6 miesięcy.

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)