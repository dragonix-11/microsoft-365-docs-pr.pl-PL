---
title: Administrowanie skrzynkami pocztowymi Exchange Online w środowisku z wieloma lokalizacjami geograficznymi
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
description: Dowiedz się, jak administrować Exchange Online ustawieniami wielu obszarów geograficznych w środowisku Microsoft 365 przy użyciu programu PowerShell.
ms.openlocfilehash: 4b0b02fa9ea974784ec93efe83520faed5fd05bd
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130872"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administrowanie skrzynkami pocztowymi Exchange Online w środowisku z wieloma lokalizacjami geograficznymi

Exchange Online program PowerShell jest wymagany do wyświetlania i konfigurowania właściwości wielu obszarów geograficznych w środowisku Microsoft 365. Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Aby wyświetlić właściwość **PreferredDataLocation** dla obiektów użytkowników, potrzebujesz [modułu Microsoft Azure Active Directory programu PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) w wersji 1.1.166.0 lub nowszej w wersji 1.x. Obiekty użytkownika zsynchronizowane za pośrednictwem AAD Połączenie do AAD nie mogą bezpośrednio modyfikować wartości **PreferredDataLocation** za pośrednictwem programu AAD programu PowerShell. Obiekty użytkowników tylko w chmurze można modyfikować za pośrednictwem AAD programu PowerShell. Aby nawiązać połączenie z programem Azure AD programu PowerShell, zobacz [Połączenie z programem PowerShell](connect-to-microsoft-365-powershell.md).

W Exchange Online środowiskach z wieloma lokalizacjami geograficznymi nie trzeba wykonywać żadnych ręcznych kroków w celu dodania obszarów geograficznych do dzierżawy. Po otrzymaniu wpisu centrum komunikatów z informacją, że wiele obszarów geograficznych jest gotowe do Exchange Online, wszystkie dostępne obszary geograficzne będą gotowe i skonfigurowane do użycia.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Połączenie bezpośrednio do lokalizacji geograficznej przy użyciu programu Exchange Online PowerShell

Zazwyczaj Exchange Online program PowerShell połączy się z centralną lokalizacją geograficzną. Można jednak również połączyć się bezpośrednio z lokalizacjami geograficznymi satelitów. Ze względu na poprawę wydajności zalecamy bezpośrednie połączenie z lokalizacją geograficzną satelity, gdy zarządzasz tylko użytkownikami w tej lokalizacji.

Wymagania dotyczące instalowania i używania modułu EXO V2 zostały opisane w temacie [Instalowanie i obsługa modułu EXO V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

Aby nawiązać połączenie Exchange Online programu PowerShell z określoną lokalizacją geograficzną, parametr *ConnectionUri* różni się od zwykłych instrukcji połączenia. Pozostałe polecenia i wartości są takie same.

W szczególności należy dodać `?email=<emailaddress>` wartość na końcu wartości _ConnectionUri_ . `<emailaddress>` to adres e-mail **dowolnej** skrzynki pocztowej w docelowej lokalizacji geograficznej. Twoje uprawnienia do tej skrzynki pocztowej lub relacja z poświadczeniami nie są czynnikiem; Adres e-mail po prostu informuje Exchange Online programu PowerShell, gdzie nawiązać połączenie.

Microsoft 365 lub Microsoft 365 GCC klienci zazwyczaj nie muszą używać parametru _ConnectionUri_, aby nawiązać połączenie z programem Exchange Online programu PowerShell. Aby jednak nawiązać połączenie z określoną lokalizacją geograficzną, należy użyć _parametru ConnectionUri_ , aby można było użyć wartości `?email=<emailaddress>` .

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>Połączenie do lokalizacji geograficznej w programie Exchange Online PowerShell

Poniższe instrukcje połączenia działają w przypadku kont, które są lub nie są skonfigurowane do uwierzytelniania wieloskładnikowego (MFA).

1. W oknie Windows PowerShell załaduj moduł EXO V2, uruchamiając następujące polecenie:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. W poniższym przykładzie admin@contoso.onmicrosoft.com jest kontem administratora, a docelowa lokalizacja geograficzna to miejsce, w którym znajduje się skrzynka pocztowa olga@contoso.onmicrosoft.com.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. Wprowadź hasło dla admin@contoso.onmicrosoft.com w wyświetlonym monitie. Jeśli konto jest skonfigurowane dla uwierzytelniania wieloskładnikowego, należy również wprowadzić kod zabezpieczeń.

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Wyświetlanie dostępnych lokalizacji geograficznych skonfigurowanych w organizacji Exchange Online

Aby wyświetlić listę skonfigurowanych lokalizacji geograficznych w Microsoft 365 Multi-Geo, uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Wyświetlanie centralnej lokalizacji geograficznej organizacji Exchange Online

Aby wyświetlić centralną lokalizację geograficzną dzierżawy, uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Znajdowanie lokalizacji geograficznej skrzynki pocztowej

Polecenie cmdlet **Get-Mailbox** w programie Exchange Online programu PowerShell wyświetla następujące właściwości związane z wieloma obszarami geograficznymi w skrzynkach pocztowych:

- **Baza danych**: pierwsze 3 litery nazwy bazy danych odpowiadają kodowi geograficznemu, który informuje o tym, gdzie obecnie znajduje się skrzynka pocztowa. W przypadku skrzynek pocztowych archiwum online należy użyć właściwości **ArchiveDatabase** .

- **MailboxRegion**: określa kod lokalizacji geograficznej, który został ustawiony przez administratora (zsynchronizowane z **PreferredDataLocation** w Azure AD).

- **MailboxRegionLastUpdateTime**: wskazuje, kiedy mailboxRegion został ostatnio zaktualizowany (automatycznie lub ręcznie).

Aby wyświetlić te właściwości skrzynki pocztowej, użyj następującej składni:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Aby na przykład wyświetlić informacje o lokalizacji geograficznej skrzynki pocztowej chris@contoso.onmicrosoft.com, uruchom następujące polecenie:

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Dane wyjściowe polecenia wyglądają następująco:

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> [!NOTE]
> Jeśli kod lokalizacji geograficznej w nazwie bazy danych nie jest zgodny z wartością **MailboxRegion**, skrzynka pocztowa zostanie automatycznie umieszczona w kolejce relokacji i przeniesiona do lokalizacji geograficznej określonej przez wartość **MailboxRegion** (Exchange Online wyszuka niezgodności między tymi wartościami właściwości).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Przenoszenie istniejącej skrzynki pocztowej tylko w chmurze do określonej lokalizacji geograficznej

Użytkownik tylko w chmurze jest użytkownikiem, który nie jest synchronizowany z dzierżawą za pośrednictwem AAD Połączenie. Ten użytkownik został utworzony bezpośrednio w Azure AD. Użyj poleceń cmdlet **Get-MsolUser** i **Set-MsolUser** w module Azure AD, aby Windows PowerShell wyświetlić lub określić lokalizację geograficzną, w której będzie przechowywana skrzynka pocztowa użytkownika tylko w chmurze.

Aby wyświetlić wartość **PreferredDataLocation** dla użytkownika, użyj tej składni w programie Azure AD programu PowerShell:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Aby na przykład wyświetlić wartość **PreferredDataLocation** dla użytkownika michelle@contoso.onmicrosoft.com, uruchom następujące polecenie:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Aby zmodyfikować wartość **PreferredDataLocation** dla obiektu użytkownika tylko w chmurze, użyj następującej składni w programie Azure AD programu PowerShell:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

Aby na przykład ustawić wartość **PreferredDataLocation** na obszar geograficzny Unii Europejskiej (EUR) dla użytkownika michelle@contoso.onmicrosoft.com, uruchom następujące polecenie:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - Jak wspomniano wcześniej, nie można użyć tej procedury dla zsynchronizowanych obiektów użytkownika z lokalna usługa Active Directory. Musisz zmienić wartość **PreferredDataLocation** w usłudze Active Directory i zsynchronizować ją przy użyciu AAD Połączenie. Aby uzyskać więcej informacji, zobacz [Azure Active Directory Połączenie sync: Configure preferred data location for Microsoft 365 resources (Konfigurowanie preferowanej lokalizacji danych dla zasobów Microsoft 365](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)).
>
> - Czas przenoszenia skrzynki pocztowej do nowej lokalizacji geograficznej zależy od kilku czynników:
>
>   - Rozmiar i typ skrzynki pocztowej.
>   - Liczba przenoszonych skrzynek pocztowych.
>   - Dostępność zasobów przenoszenia.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>Przenoszenie nieaktywnej skrzynki pocztowej do określonego obszaru geograficznego

Nie można przenosić nieaktywnych skrzynek pocztowych, które są zachowywane do celów zgodności (na przykład skrzynek pocztowych w blokadzie postępowania sądowego), zmieniając ich wartość **PreferredDataLocation** . Aby przenieść nieaktywną skrzynkę pocztową do innego obszaru geograficznego, wykonaj następujące kroki:

1. Odzyskaj nieaktywną skrzynkę pocztową. Aby uzyskać instrukcje, zobacz [Odzyskiwanie nieaktywnej skrzynki pocztowej](../compliance/recover-an-inactive-mailbox.md).

2. Uniemożliwia asystentowi folderów zarządzanych przetwarzanie odzyskanej skrzynki pocztowej przez zastąpienie \<MailboxIdentity\> nazwą, aliasem, kontem lub adresem e-mail skrzynki pocztowej i uruchomienie następującego polecenia w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. Przypisz licencję **Exchange Online Plan 2** do odzyskanej skrzynki pocztowej. Ten krok jest wymagany do umieszczenia skrzynki pocztowej z powrotem w blokadzie postępowania sądowego. Aby uzyskać instrukcje, zobacz [Przypisywanie licencji użytkownikom](../admin/manage/assign-licenses-to-users.md).

4. Skonfiguruj wartość **PreferredDataLocation** w skrzynce pocztowej zgodnie z opisem w poprzedniej sekcji.

5. Po potwierdzeniu, że skrzynka pocztowa została przeniesiona do nowej lokalizacji geograficznej, umieść odzyskaną skrzynkę pocztową z powrotem w blokadzie postępowania sądowego. Aby uzyskać instrukcje, zobacz [Umieszczanie skrzynki pocztowej w blokadzie postępowania sądowego](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. Po sprawdzeniu, czy blokada postępowania sądowego jest włączona, zezwól asystentowi folderów zarządzanych na ponowne przetworzenie skrzynki pocztowej, zastępując \<MailboxIdentity\> ją nazwą, aliasem, kontem lub adresem e-mail skrzynki pocztowej i uruchamiając następujące polecenie w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. Ponownie ustaw nieaktywność skrzynki pocztowej, usuwając konto użytkownika skojarzone ze skrzynką pocztową. Aby uzyskać instrukcje, zobacz [Usuwanie użytkownika z organizacji](../admin/add-users/delete-a-user.md). Ten krok zwalnia również licencję Exchange Online plan 2 do innych zastosowań.

**Uwaga**: przeniesienie nieaktywnej skrzynki pocztowej do innej lokalizacji geograficznej może mieć wpływ na wyniki wyszukiwania zawartości lub na możliwość przeszukiwania skrzynki pocztowej z poprzedniej lokalizacji geograficznej. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i eksportowanie zawartości w środowiskach z wieloma lokalizacjami geograficznymi](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Tworzenie nowych skrzynek pocztowych w chmurze w określonej lokalizacji geograficznej

Aby utworzyć nową skrzynkę pocztową w określonej lokalizacji geograficznej, należy wykonać jedną z następujących czynności:

- Skonfiguruj wartość **PreferredDataLocation** zgodnie z *opisem* w poprzedniej sekcji [Przenoszenie istniejącej skrzynki pocztowej tylko w chmurze do określonej lokalizacji geograficznej](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location) przed utworzeniem skrzynki pocztowej w Exchange Online. Na przykład przed przypisaniem licencji skonfiguruj wartość **PreferredDataLocation** dla użytkownika.

- Przypisz licencję w tym samym czasie, gdy ustawisz wartość **PreferredDataLocation** .

Aby utworzyć nowego użytkownika licencjonowanego tylko w chmurze (nie AAD Połączenie zsynchronizowane) w określonej lokalizacji geograficznej, użyj następującej składni w programie Azure AD programu PowerShell:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

W tym przykładzie utwórz nowe konto użytkownika elizabeth Brunner z następującymi wartościami:

- Główna nazwa użytkownika: ebrunner@contoso.onmicrosoft.com
- Imię: Elizabeth
- Nazwisko: Brunner
- Nazwa wyświetlana: Elizabeth Brunner
- Hasło: generowane losowo i wyświetlane w wynikach polecenia (ponieważ nie używamy parametru *Hasło* )
- Licencja: `contoso:ENTERPRISEPREMIUM` (E5)
- Lokalizacja: Australia (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Aby uzyskać więcej informacji na temat tworzenia nowych kont użytkowników i znajdowania wartości LicenseAssignment w programie Azure AD programu PowerShell, zobacz [Tworzenie kont użytkowników przy użyciu programu PowerShell](create-user-accounts-with-microsoft-365-powershell.md) oraz [Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> Jeśli używasz Exchange Online programu PowerShell, aby włączyć skrzynkę pocztową i potrzebujesz, aby skrzynka pocztowa została utworzona bezpośrednio w lokalizacji geograficznej określonej w **obszarze PreferredDataLocation**, musisz użyć polecenia cmdlet Exchange Online, takiego jak **Enable-Mailbox** lub **New-Mailbox** bezpośrednio w usłudze w chmurze. Jeśli używasz polecenia cmdlet **Enable-RemoteMailbox** w lokalnej Exchange programu PowerShell, skrzynka pocztowa zostanie utworzona w centralnej lokalizacji geograficznej.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Dołączanie istniejących lokalnych skrzynek pocztowych w określonej lokalizacji geograficznej

Standardowe narzędzia i procesy dołączania umożliwiają migrowanie skrzynki pocztowej z lokalnej organizacji Exchange do Exchange Online, [w tym pulpitu nawigacyjnego migracji w usłudze EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) oraz polecenia cmdlet [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) w programie Exchange Online programu PowerShell.

Pierwszym krokiem jest sprawdzenie, czy obiekt użytkownika istnieje dla każdej skrzynki pocztowej, która ma zostać dołączona, i sprawdzenie, czy w Azure AD skonfigurowano poprawną wartość **PreferredDataLocation**. Narzędzia dołączania będą **uwzględniać wartość PreferredDataLocation** i będą migrować skrzynki pocztowe bezpośrednio do określonej lokalizacji geograficznej.

Możesz też użyć poniższych kroków, aby dołączyć skrzynki pocztowe bezpośrednio w określonej lokalizacji geograficznej przy użyciu polecenia cmdlet [New-MoveRequest](/powershell/module/exchange/new-moverequest) w programie Exchange Online programu PowerShell.

1. Sprawdź, czy obiekt użytkownika istnieje dla każdej skrzynki pocztowej, która ma zostać dołączona, i czy **parametr PreferredDataLocation** jest ustawiony na żądaną wartość w Azure AD. Wartość **preferredDataLocation** zostanie zsynchronizowana z atrybutem **MailboxRegion** odpowiedniego obiektu użytkownika poczty w Exchange Online.

2. Połącz się bezpośrednio z określoną lokalizacją geograficzną satelity, korzystając z instrukcji połączenia z wcześniejszej części tego tematu.

3. W programie PowerShell usługi Exchange Online zapisz poświadczenia administratora lokalnego, które są używane do przeprowadzania migracji skrzynki pocztowej w zmiennej, uruchamiając następujące polecenie:

   ```powershell
   $RC = Get-Credential
   ```

4. W programie Exchange Online PowerShell utwórz nowy element **New-MoveRequest** podobny do następującego przykładu:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. Powtórz krok nr 4 dla każdej skrzynki pocztowej, z której chcesz przeprowadzić migrację z lokalnego programu Exchange do satelitarnej lokalizacji geograficznej, z którą aktualnie masz połączenie.

6. Jeśli musisz przeprowadzić migrację dodatkowych skrzynek pocztowych do różnych satelitarnych lokalizacji geograficznych, powtórz kroki od 2 do 4 dla każdej określonej lokalizacji.

## <a name="multi-geo-reporting"></a>Raportowanie z wieloma lokalizacjami geograficznymi

> [!NOTE]
> Funkcja raportowania wielu obszarów geograficznych jest obecnie dostępna w wersji zapoznawczej, nie jest dostępna we wszystkich organizacjach i może ulec zmianie.

**Raporty użycia wielu obszarów geograficznych** w centrum administracyjnym platformy Microsoft 365 wyświetlają liczbę użytkowników według lokalizacji geograficznej. Raport wyświetla rozkład użytkowników dla bieżącego miesiąca i zawiera dane historyczne z ostatnich 6 miesięcy.

## <a name="see-also"></a>Zobacz też

[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
