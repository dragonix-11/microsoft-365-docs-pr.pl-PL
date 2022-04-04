---
title: Migracja skrzynki pocztowej między dzierżawami
description: Jak przenosić skrzynki pocztowe między Microsoft 365 lub Office 365 dzierżawami.
ms.author: kvice
author: kelleyvice-msft
manager: Laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: 09/21/2020
ms.reviewer: georgiah
ms.custom:
- it-pro
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.collection:
- M365-subscription-management
ms.openlocfilehash: e9ec5c27f5dabfa2df0f12ca6daecfcef860547c
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499380"
---
# <a name="cross-tenant-mailbox-migration-preview"></a>Migracja skrzynek pocztowych między dzierżawami (wersja Preview)

Zazwyczaj podczas fuzji lub rozchodów potrzebujesz możliwości przeniesienia skrzynki Exchange Online pocztowej użytkownika do nowej dzierżawy. Migracja skrzynek pocztowych między dzierżawami umożliwia administratorom dzierżawy korzystanie z dobrze znanych interfejsów, takich jak zdalny program PowerShell i mrs, do przenoszenia użytkowników do nowej organizacji.

Administratorzy mogą używać New-MigrationBatch cmdlet dostępnego za pośrednictwem roli zarządzania Przenoszenie skrzynek pocztowych, aby przeprowadzać przeniesienia między dzierżawami.

Użytkownicy migrujący muszą znajdować się w dzierżawie Exchange Online system jako użytkownicy poczty, oznaczenie określonymi atrybutami w celu umożliwienia migracji między dzierżawami. System nie zostanie przeniesiony w przypadku użytkowników, którzy nie są poprawnie skonfigurowani w dzierżawie docelowej.

Po zakończeniu przenoszenia źródłowa skrzynka pocztowa użytkownika jest konwertowana na użytkownika poczty, a wartość targetAddress (wyświetlana jako ExternalEmailAddress w programie Exchange) jest znakowana adresem routingu do dzierżawy docelowej. Ten proces pozostawia starszego użytkownika poczty w dzierżawie źródłowej i umożliwia współistnienie oraz routing poczty. Gdy zezwalają na to procesy biznesowe, dzierżawa źródłowa może usunąć źródłowego użytkownika poczty lub przekonwertować go na kontakt pocztowy.

Migracje skrzynek Exchange między dzierżawami są obsługiwane tylko w trybie hybrydowym lub w chmurze albo dowolną kombinację tych dwóch dzierżaw.

W tym artykule opisano proces przenoszenia skrzynek pocztowych między dzierżawami i przedstawiono wskazówki dotyczące sposobu przygotowywania dzierżaw źródłowych i docelowych dla przenoszenia zawartości skrzynki Exchange Online pocztowej.

   > [!NOTE]
   > Ostatnio zaktualizowaliśmy nasze kroki konfiguracji dotyczące włączania migracji skrzynek pocztowych między dzierżawami, aby nie wymagały już usługi Azure Key Vault! Jeśli dołączasz do tej wersji Preview po raz pierwszy, nie musisz nic więcej zrobić i możesz wykonać kroki opisane w tym dokumencie. Jeśli rozpoczęto konfigurowanie dzierżaw przy użyciu poprzedniej metody akv, zdecydowanie zalecamy zatrzymanie lub usunięcie tej konfiguracji, aby rozpocząć korzystanie z tej nowej metody. Jeśli migracja skrzynek pocztowych jest w toku przy użyciu poprzedniej metody akv, poczekaj na ukończenie istniejących migracji i wykonaj poniższe czynności, aby włączyć nową uproszczoną metodę. Kroki Key Vault wymaganej konfiguracji usługi Azure są archiwizowane, ale można je **[znaleźć tutaj,](https://github.com/microsoft/cross-tenant/wiki/V1-Content#cross-tenant-mailbox-migration-preview)** w celu ich odwołania.

## <a name="preparing-source-and-target-tenants"></a>Przygotowywanie dzierżawy źródłowej i docelowej

### <a name="prerequisites-for-source-and-target-tenants"></a>Wymagania wstępne dzierżawy źródłowej i docelowej

Przed rozpoczęciem upewnij się, że masz niezbędne uprawnienia do skonfigurowania aplikacji Przenieś skrzynkę pocztową na platformie Azure, punktu końcowego migracji EXO i relacji organizacji EXO.

Ponadto wymagana jest co najmniej jedna grupa zabezpieczeń z obsługą poczty w dzierżawie źródłowej. Te grupy służą do zakresu listy skrzynek pocztowych, które można przenosić z dzierżawy źródłowej (lub czasami nazywanej zasobem) do dzierżawy docelowej. Dzięki temu administrator dzierżawy źródłowej może ograniczyć lub zawężać określony zestaw skrzynek pocztowych do przeniesienia, aby zapobiec migracji niezamierzonych użytkowników. Grupy zagnieżdżone nie są obsługiwane.

W celu uzyskania identyfikatora Microsoft 365 musisz również komunikować się z zaufaną firmą partnerską (z którą chcesz przenosić skrzynki pocztowe). Ten identyfikator dzierżawy jest używany w polu Nazwa_domeny relacji organizacji.

Aby uzyskać identyfikator dzierżawy subskrypcji, zaloguj się do [Centrum administracyjne platformy Microsoft 365 i przejdź](https://go.microsoft.com/fwlink/p/?linkid=2024339) do strony [https://aad.portal.azure.com/\#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Kliknij ikonę kopiowania dla właściwości Identyfikator dzierżawy, aby skopiować ją do schowka.

### <a name="configuration-steps-to-enable-your-tenants-for-cross-tenant-mailbox-migrations"></a>Czynności konfiguracyjne umożliwiające dzierżawie migrowanie skrzynek pocztowych między dzierżawami

   > [!NOTE]
   > Najpierw musisz skonfigurować element docelowy (miejsce docelowe). Aby wykonać te czynności, nie musisz posiadać ani znać poświadczeń administratora dzierżawy zarówno dla dzierżawy źródłowej, jak i docelowej. Poszczególne kroki mogą zostać wykonane przez różnych administratorów dla każdej dzierżawy.

### <a name="prepare-the-target-destination-tenant-by-creating-the-migration-application-and-secret"></a>Przygotowywanie dzierżawy docelowej (docelowej) przez utworzenie aplikacji do migracji i stanu tajnego

1. Logowanie się do portalu usługi Azure AD (<https://portal.azure.com>) przy użyciu poświadczeń administratora dzierżawy docelowej

   ![Azure Logon](../media/tenant-to-tenant-mailbox-move/74f26681e12df3308c7823ee7d527587.png)

2. Kliknij widok w obszarze Zarządzaj Azure Active Directory.

   ![Azure Active Directory przycisku](../media/tenant-to-tenant-mailbox-move/109ac3dfbac2403fb288f085767f393b.png)

3. Na lewym pasku nawigacyjnym wybierz pozycję Rejestracje aplikacji.

4. Wybierz pozycję Nowa rejestracja

   ![Nowa aplikacja](../media/tenant-to-tenant-mailbox-move/b36698df128e705eacff4bff7231056a.png)

5. Na stronie Rejestrowanie aplikacji w obszarze Obsługiwane typy kont wybierz pozycję Konta w dowolnym katalogu organizacyjnym (Dowolny katalog usługi Azure AD — usługa multitenant). Następnie w obszarze Redirect URI (optional) (Opcjonalnie) wybierz pozycję Web and enter .<https://office.com> Na koniec wybierz pozycję Zarejestruj.

   ![Rejestracja aplikacji](../media/tenant-to-tenant-mailbox-move/edcdf18b9f504c47284fe4afb982c433.png)

6. W prawym górnym rogu strony pojawi się okno podręczne z powiadomieniem z powiadomieniem o pomyślnym utworzeniu aplikacji.

7. Wstecz do ekranu Azure Active Directory i kliknij przycisk Rejestracje aplikacji.

8. W obszarze Posiadane aplikacje znajdź utworzoną aplikację i kliknij ją.

9. W obszarze ^Essentials musisz skopiować identyfikator aplikacji (klienta), ponieważ będzie potrzebny później do utworzenia adresu URL dzierżawy docelowej.

10. Teraz na lewym pasku nawigacyjnym kliknij pozycję Uprawnienia interfejsu API, aby wyświetlić uprawnienia przypisane do aplikacji.

11. Domyślnie użytkownik. Uprawnienia do odczytu są przypisywane do utworzonej przez Ciebie aplikacji, ale nie wymagamy ich w przypadku migracji skrzynek pocztowych, możesz usunąć to uprawnienie.

    ![Uprawnienia aplikacji](../media/tenant-to-tenant-mailbox-move/6a8c13a36cb3e10964a6920b8138e12b.png)

12. Teraz musimy dodać uprawnienia do migracji skrzynek pocztowych, wybierz pozycję Dodaj uprawnienie

13. W oknach Zażądaj uprawnień interfejsu API wybierz pozycję Interfejsy API używane przez moją organizację, wyszukaj Office 365 Exchange Online i wybierz je.

    ![Wybieranie interfejsu API](../media/tenant-to-tenant-mailbox-move/0b4dc1eea3910e9c475724d9473aca58.png)

14. Następnie wybierz pozycję Uprawnienia aplikacji

15. Następnie w obszarze Wybierz uprawnienia rozwiń pozycję Skrzynka pocztowa i zaznacz pola wyboru Mailbox.Migration i Dodaj uprawnienia u dołu ekranu.

    ![Ustaw interfejs API](../media/tenant-to-tenant-mailbox-move/0038a4cf74bb13de0feb51800e078803.png)

16. Teraz wybierz pozycję Certyfikaty & sekrety na lewym pasku nawigacyjnym aplikacji.

17. W obszarze Tajemnice klienta wybierz klucz tajny nowego klienta.

    ![Tajemnice klientów](../media/tenant-to-tenant-mailbox-move/273dafd5e6c6455695f9baf35ef9977a.png)

18. W oknie Dodawanie klienta jako tajnego wprowadź opis i skonfiguruj odpowiednie ustawienia wygasania.

      > [!NOTE]
      > Jest to hasło, które będzie używane podczas tworzenia punktu końcowego migracji. Bardzo ważne jest, aby skopiować to hasło do Schowka i skopiować to hasło do bezpiecznej/tajnej lokalizacji. To jest jedyny taki czas, w których będzie można zobaczyć to hasło. Jeśli w jakiś sposób go utracisz lub chcesz go zresetować, możesz zalogować się ponownie do naszej usługi Azure Portal, przejść do usługi Rejestracje aplikacji, znaleźć aplikację do migracji, wybrać pozycję Tajemnice & certyfikatów i utworzyć nową tajemnicę dla swojej aplikacji.

19. Teraz, gdy pomyślnie utworzono aplikację do migracji i klucz tajny, należy wyrazić zgodę na aplikację. Aby wyrazić zgodę na aplikację, wróć do strony Azure Active Directory, kliknij pozycję aplikacje Enterprise w lewym okienku nawigacji, znajdź utworzoną aplikację do migracji, zaznacz ją i wybierz pozycję Uprawnienia w lewym okienku nawigacji.

20. Kliknij przycisk Udostępniaj zgodę administratora dla [Twojej dzierżawy].

21. Zostanie otwarte nowe okno przeglądarki i wybierz pozycję Zaakceptuj.

22. Możesz wrócić do okna portalu i wybrać pozycję Odśwież, aby potwierdzić akceptację.

23. Formułuj adres URL, aby był wysyłany do zaufanego partnera (administratora dzierżawy źródłowej), aby on również akceptował aplikację w celu włączenia migracji skrzynek pocztowych. Oto przykładowy adres URL do ich podania, będzie potrzebny identyfikator aplikacji utworzonej przez Ciebie:

    ```powershell
    https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
    ```

    > [!NOTE]
    > Będzie potrzebny identyfikator aplikacji do migracji skrzynek pocztowych, która właśnie została utworzona.
    >
    > W powyższym przykładzie należy zastąpić sourcetenant.onmicrosoft.com poprawną nazwą domeny dzierżawy onmicrosoft.com źródłowej.
    >
    > Konieczne będzie też zastąpienie ciągu [application_id_of_the_app_you_just_created] identyfikatorem aplikacji do migracji skrzynek pocztowych, która właśnie została utworzona.

### <a name="prepare-the-target-tenant-by-creating-the-exchange-online-migration-endpoint-and-organization-relationship"></a>Przygotowywanie dzierżawy docelowej przez utworzenie punktu końcowego Exchange Online i relacji organizacji

1. Utwórz zdalne połączenie programu PowerShell z docelową Exchange Online dzierżawą.

2. Tworzenie nowego punktu końcowego migracji dla przenoszenia skrzynek pocztowych między dzierżawami

   > [!NOTE]
   > Będzie potrzebny identyfikator aplikacji do migrowania skrzynek pocztowych, który właśnie został utworzony, oraz hasło (tajny), które skonfigurowano podczas tego procesu. Także w zależności od tego, Microsoft 365 Cloud Instance, z których korzystasz, może się różnić. Zapoznaj się ze stroną [Microsoft 365 punktami](/microsoft-365/enterprise/microsoft-365-endpoints) końcowymi i wybierz odpowiednie wystąpienie dla twojej dzierżawy, a następnie przejrzyj adres w Exchange Online Optimize Required (Optymalizuj wymagane) i odpowiednio zamień.

   ```powershell
   
   # Enable customization if tenant is dehydrated
     $dehydrated=Get-OrganizationConfig | fl isdehydrated
     if ($dehydrated -eq $true) {Enable-OrganizationCustomization}
     
   $AppId = "[guid copied from the migrations app]"

   $Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $AppId, (ConvertTo-SecureString -String "[this is your secret password you saved in the previous steps]" -AsPlainText -Force)

   New-MigrationEndpoint -RemoteServer outlook.office.com -RemoteTenant "sourcetenant.onmicrosoft.com" -Credentials $Credential -ExchangeRemoteMove:$true -Name "[the name of your migration endpoint]" -ApplicationId $AppId
   ```

3. Utwórz nowy obiekt lub edytuj istniejący obiekt relacji organizacji z dzierżawą źródłową.

   ```powershell
   $sourceTenantId="[tenant id of your trusted partner, where the source mailboxes are]"
   $orgrels=Get-OrganizationRelationship
   $existingOrgRel = $orgrels | ?{$_.DomainNames -like $sourceTenantId}
   If ($null -ne $existingOrgRel)
   {
       Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound
   }
   If ($null -eq $existingOrgRel)
   {
       New-OrganizationRelationship "[name of the new organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound -DomainNames $sourceTenantId
   }
   ```

### <a name="prepare-the-source-current-mailbox-location-tenant-by-accepting-the-migration-application-and-configuring-the-organization-relationship"></a>Przygotowywanie dzierżawy źródłowej (bieżącej lokalizacji skrzynki pocztowej) przez zaakceptowanie aplikacji do migracji i skonfigurowanie relacji między organizacjami

1. Z przeglądarki przejdź do linku adresu URL podanego przez zaufanego partnera, aby wyrazić zgodę na aplikację do migracji skrzynek pocztowych. Adres URL będzie wyglądać tak:

   ```powershell
   https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
   ```

   > [!NOTE]
   > Będzie potrzebny identyfikator aplikacji do migracji skrzynek pocztowych, która właśnie została utworzona.
   > W powyższym przykładzie należy zastąpić sourcetenant.onmicrosoft.com poprawną nazwą domeny dzierżawy onmicrosoft.com źródłowej.
   > Konieczne będzie też zastąpienie ciągu [application_id_of_the_app_you_just_created] identyfikatorem aplikacji do migracji skrzynek pocztowych, która właśnie została utworzona.

2. Gdy pojawi się okno podręczne, zaakceptuj aplikację. Możesz również zalogować się do swojego Azure Active Directory i znaleźć aplikację w obszarze Enterprise aplikacji.

3. Utwórz nowy lub edytuj istniejący obiekt relacji organizacji z dzierżawą docelową (miejsca docelowego) za pomocą Exchange Online zdalnej obsługi programu PowerShell.

   ```powershell
   $targetTenantId="[tenant id of your trusted partner, where the mailboxes are being moved to]"
   $appId="[application id of the mailbox migration app you consented to]"
   $scope="[name of the mail enabled security group that contains the list of users who are allowed to migrate]"
   $orgrels=Get-OrganizationRelationship
   $existingOrgRel = $orgrels | ?{$_.DomainNames -like $targetTenantId}
   If ($null -ne $existingOrgRel)
   {
       Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
   }
   If ($null -eq $existingOrgRel)
   {
       New-OrganizationRelationship "[name of your organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -DomainNames $targetTenantId -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
   }
   ```
   
> [!NOTE]
> Identyfikator dzierżawy wprowadzany jako identyfikator $sourceTenantId i $targetTenantId to identyfikator GUID, a nie nazwa domeny dzierżawy. Aby uzyskać przykład identyfikatora dzierżawy i informacje o znajdowaniu identyfikatora dzierżawy, zobacz Znajdowanie identyfikatora Microsoft 365 [dzierżawy](/onedrive/find-your-office-365-tenant-id).
   
### <a name="how-do-i-know-this-worked"></a>Jak mogę, że to zadziałało?

Konfigurację migracji skrzynek pocztowych między dzierżawami możesz sprawdzić, uruchamiając polecenie cmdlet [Test-MigrationServerAvailability](/powershell/module/exchange/Test-MigrationServerAvailability) względem punktu końcowego migracji między dzierżawami utworzonego w dzierżawie docelowej.

   > [!NOTE]
   >
   > - Dzierżawa docelowa:
   > 
   > Test-MigrationServerAvailability -Endpoint "[nazwa punktu końcowego migracji między dzierżawami]"
   >
   > Get-OrganizationRelationship | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability
   >
   > - Dzierżawa źródłowa:
   > 
   > Get-OrganizationRelationship | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability 

### <a name="move-mailboxes-back-to-the-original-source"></a>Przenoszenie skrzynek pocztowych z powrotem do oryginalnego źródła

Jeśli w celu powrotu do pierwotnej dzierżawy źródłowej jest wymagana skrzynka pocztowa, należy uruchomić ten sam zestaw czynności i skryptów zarówno w nowej dzierżawie źródłowej, jak i w nowej dzierżawie docelowej. Istniejący obiekt Organization Relationship (Relacja między organizacjami) zostanie zaktualizowany lub dodany, a nie utworzony ponownie

## <a name="prepare-target-user-objects-for-migration"></a>Przygotowywanie docelowych obiektów użytkowników do migracji

Migrowanie użytkowników musi być obecne w dzierżawie docelowej, a system Exchange Online (jako użytkownicy poczty) oznaczony określonymi atrybutami, aby umożliwić migrowanie między dzierżawami. System nie zostanie przeniesiony w przypadku użytkowników, którzy nie są poprawnie skonfigurowani w dzierżawie docelowej. W poniższej sekcji przedstawiono wymagania dotyczące obiektu MailUser dla dzierżawy docelowej.

### <a name="prerequisites-for-target-user-objects"></a>Wymagania wstępne obiektów użytkowników docelowych

Upewnij się, że w organizacji docelowej są ustawione następujące obiekty i atrybuty.

1. W przypadku każdej skrzynki pocztowej przenoszącej się z organizacji źródłowej należy aprowiz z obiektu MailUser w organizacji docelowej:

   - Docelowy użytkownik poczty musi mieć następujące atrybuty ze źródłowej skrzynki pocztowej lub musi mieć przypisany nowy obiekt User:
      - Identyfikator EXCHANGEGUID (bezpośredni przepływ ze źródła do celu): Identyfikator GUID skrzynki pocztowej musi być zgodne. Proces przenoszenia nie będzie kontynuowany, jeśli nie występuje w obiekcie docelowym.
      - ArchiveGUID (bezpośredni przepływ ze źródła do docelowego): archiwalny identyfikator GUID musi być zgodne. Proces przenoszenia nie będzie kontynuowany, jeśli nie występuje w obiekcie docelowym. (Ta opcja jest wymagana tylko wtedy, gdy dla źródłowej skrzynki pocztowej włączono archiwum).
      - LegacyExchangeDN (flow as proxyAddress, "x500:\<LegacyExchangeDN>"): LegacyExchangeDN musi być obecna w docelowej witrynie MailUser jako x500: proxyAddress. Ponadto musisz również skopiować wszystkie adresy x500 ze źródłowej skrzynki pocztowej do użytkownika poczty docelowej. Procesy przenoszenia nie będą kontynuowane, jeśli nie są obecne w obiekcie docelowym.
      - UserPrincipalName( Głównej nazwy użytkownika): zostanie wyrównana do nowej tożsamości lub firmy docelowej użytkownika (na przykład user@northwindtraders.onmicrosoft.com).
      - Primary SMTPAddress (Podstawowy adres SMTP): podstawowy adres SMTP będzie wyrównany do nowej firmy użytkownika (na przykład dla user@northwind.com).
      - TargetAddress/ExternalEmailAddress: Użytkownik poczty odwołuje się do bieżącej skrzynki pocztowej użytkownika hostowanej w dzierżawie źródłowej (na przykład user@contoso.onmicrosoft.com). Przypisując tę wartość, upewnij się, że masz/również przypisywany jest adres PrimarySMTPAddress lub ta wartość powoduje ustawienie wartości PrimarySMTPAddress, co spowoduje błędy przenoszenia.
      - Nie można dodać starszych adresów serwera proxy SMTP ze źródłowej skrzynki pocztowej do docelowych użytkowników poczty. Nie można na przykład zachować danych contoso.com z użytkownikami z grupy fabrikam.onmicrosoft.com obiektach dzierżawy). Domeny są skojarzone tylko z jedną dzierżawą usługi Azure AD Exchange Online usługi Azure AD.

     Przykład **docelowy obiekt** MailUser:

     | Atrybut            | Value                                                                                                                   |
     | -------------------- | ----------------------------------------------------------------------------------------------------------------------- |
     | Alias                | LaraN                                                                                                                   |
     | RecipientType (Typ adresata)        | MailUser                                                                                                                |
     | RecipientTypeDetails | MailUser                                                                                                                |
     | UserPrincipalName (Nazwa użytkownika)    | LaraN@northwintraders.onmicrosoft.com                                                                                   |
     | PrimarySmtpAddress   | Lara.Newton@northwind.com                                                                                               |
     | ExternalEmailAddress | SMTP:LaraN@contoso.onmicrosoft.com                                                                                      |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                                                                    |
     | LegacyExchangeDN     | /o=Pierwsza organizacja/ou=Exchange administracyjnej                                                                  |
     |                      | (FYDIBOLAF23SPDLT)/cn=Recipients/cn=74e5385fce4b46d19006876949855035Lara                                                 |
     | EmailAddresses       | x500:/o=Pierwsza organizacja/ou=Exchange Administrative Group (FYDIBIBF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c8190 |
     |                      | 7273f1f9-Lara                                                                                                           |
     |                      | smtp:LaraN@northwindtraders.onmicrosoft.com                                                                             |
     |                      | SMTP:Lara.Newton@northwind.com                                                                                          |
     |                      |                                                                                                                         |

     **Przykładowy obiekt źródłowy** skrzynki pocztowej:

     | Atrybut            | Value                                                                   |
     | -------------------- | ----------------------------------------------------------------------- |
     | Alias                | LaraN                                                                   |
     | RecipientType (Typ adresata)        | UserMailbox                                                             |
     | RecipientTypeDetails | UserMailbox                                                             |
     | UserPrincipalName (Nazwa użytkownika)    | LaraN@contoso.onmicrosoft.com                                           |
     | PrimarySmtpAddress   | Lara.Newton@contoso.com                                                 |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                    |
     | LegacyExchangeDN     | /o=Pierwsza organizacja/ou=Exchange administracyjnej                  |
     |                      | (FYDIBOLAF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara |
     | EmailAddresses       | smtp:LaraN@contoso.onmicrosoft.com                                      |
     |                      | SMTP:Lara.Newton@contoso.com                                            |
     |                      |                                                                         |

   - Dodatkowe atrybuty mogą być już zawarte w Exchange zapisu hybrydowego. Jeśli nie, powinny być uwzględniane.
   - msExchBlockedSendersHash — zapisuje z powrotem dane bezpiecznych i zablokowanych nadawców w trybie online z klientów do lokalna usługa Active Directory.
   - msExchSafeRecipientsHash — zapisuje z powrotem dane bezpiecznych i zablokowanych nadawców w trybie online z klientów do lokalna usługa Active Directory.
   - msExchSafeSendersHash — zapisuje z powrotem dane bezpiecznych i zablokowanych nadawców w trybie online z klientów do lokalna usługa Active Directory.

2. Jeśli źródłową skrzynkę pocztową jest w  obiektu LitigationHold, a rozmiar elementów odzyskiwalnych skrzynki pocztowej źródłowych jest większy niż domyślny rozmiar naszej bazy danych (30 GB), przeniesienie nie będzie kontynuowane, ponieważ docelowy przydział jest mniejszy niż rozmiar źródłowej skrzynki pocztowej. Możesz zaktualizować docelowy obiekt MailUser, aby przenieść flagi skrzynki pocztowej ELC ze środowiska źródłowego do docelowego, co wyzwala system docelowy w celu rozszerzenia przydziału użytkownika poczty do 100 GB, umożliwiając tym samym przeniesienie do miejsca docelowego. Poniższe instrukcje działają tylko w przypadku tożsamości hybrydowej z uruchomionym usługą Azure AD Połączenie, ponieważ polecenia do oznaczania flag ELC nie są widoczne dla administratorów dzierżawy.

    > [!NOTE]
    > PRZYKŁADOWY — BEZ GWARANCJI
    >
    > W tym skrypcie założono połączenie zarówno ze źródłową skrzynką pocztową (w celu uzyskania wartości źródłowych), jak i z obiektem docelowym lokalna usługa Active Directory (sygnaturą obiektu ADUser). Jeśli w źródle jest włączony proces sądowy lub odzyskiwanie pojedynczych elementów, ustaw je na koncie docelowym.  Spowoduje to zwiększenie rozmiaru magazynu w koncie docelowym do 100 GB.

    ```powershell
    $ELCValue = 0
    if ($source.LitigationHoldEnabled) {$ELCValue = $ELCValue + 8} if ($source.SingleItemRecoveryEnabled) {$ELCValue = $ELCValue + 16} if ($ELCValue -gt 0) {Set-ADUser -Server $domainController -Identity $destination.SamAccountName -Replace @{msExchELCMailboxFlags=$ELCValue}}
    ```

3. Dzierżawy docelowe niebędące elementami hybrydowymi mogą przed rozpoczęciem migracji zmodyfikować przydział dla użytkowników poczty w folderze Elementy do odzyskania, uruchamiając następujące polecenie w celu włączenia funkcji Zawieszenie w związku z postępowaniem sądowym w obiekcie MailUser i zwiększając przydział do 100 GB: `Set-MailUser -EnableLitigationHoldForMigration`. Zwróć uwagę, że nie będzie to działać w przypadku dzierżaw w trybie hybrydowym.

4. Użytkownicy w organizacji docelowej muszą mieć licencję na odpowiednie Exchange Online mających zastosowanie dla organizacji. Możesz zastosować licencję przed przeniesieniem skrzynki pocztowej, ale TYLKO wtedy, gdy docelowy użytkownik poczty zostanie poprawnie skonfigurowany z adresami serwerów proxy iid usługi ExchangeGUID. Zastosowanie licencji przed zastosowaniem wartości ExchangeGUID spowoduje, że w organizacji docelowej zostanie zastosowana nowa skrzynka pocztowa.

    > [!NOTE]
    > Po zastosowaniu licencji na obiekt Mailbox lub MailUser wszystkie adresy proxyAddresses typu SMTP są przesuwane w celu zapewnienia, że tablica Exchange EmailAddresses zawiera tylko zweryfikowane domeny.

5. Musisz upewnić się, że docelowy użytkownik poczty nie ma poprzedniego argumentu ExchangeGuid, który nie jest zgodne ze źródłowym argumentem ExchangeGuid. Może się to zdarzyć, jeśli docelowy użytkownik z licencją użytkownika z dostępem do poczty Exchange Online i obsługi administracyjnej skrzynki pocztowej. Jeśli docelowy użytkownik poczty miał wcześniej licencję na usługę ExchangeGuid lub miał dla niej wartość, która nie jest taka jak wartość source ExchangeGuid, należy wyczyścić użytkownika z obsługą poczty w chmurze. W przypadku tych osób z mem chmury możesz uruchomić `Set-User <identity> -PermanentlyClearPreviousMailboxInfo`.

    > [!CAUTION]
    > Ten proces jest nieodwracalny. Jeśli obiekt zawiera "softDeleted skrzynkę pocztową", po tym momencie nie będzie można go przywrócić. Jednak po wyczyszczeniu możesz zsynchronizować prawidłowy identyfikator ExchangeGuid z obiektem docelowym, a mrs połączy źródłową skrzynkę pocztową z nowo utworzoną docelową skrzynką pocztową. (Odwołanie do blogu EHLO na temat nowego parametru).

    Znajdowanie obiektów, które były wcześniej skrzynkami pocztowymi, przy użyciu tego polecenia.

    ```powershell
    Get-User <identity> | select Name, *recipient* | Format-Table -AutoSize
    ```

    Oto przykład.

    ```powershell
    Get-User John@northwindtraders.com |select name, *recipient*| Format-Table -AutoSize

    Name       PreviousRecipientTypeDetails     RecipientType RecipientTypeDetails
    ----       ---------------------------- ------------- --------------------
    John       UserMailbox                  MailUser      MailUser
    ```

    Wyczyść miękko usuniętą skrzynkę pocztową za pomocą tego polecenia.

    ```powershell
    Set-User <identity> -PermanentlyClearPreviousMailboxInfo
    ```

    Oto przykład.

    ```powershell
    Set-User John@northwindtraders.com -PermanentlyClearPreviousMailboxInfo -Confirm
    
    Are you sure you want to perform this action?
    Delete all existing information about user "John@northwindtraders.com"?. This operation will clear existing values from Previous home MDB and Previous Mailbox GUID of the user. After deletion, reconnecting to the previous mailbox that existed in the cloud will not be possible and any content it had will be unrecoverable PERMANENTLY.
    Do you want to continue?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"): Y
    ```

### <a name="perform-mailbox-migrations"></a>Przeprowadzanie migracji skrzynek pocztowych

Migracje skrzynek Exchange między dzierżawami są inicjowane z dzierżawy docelowej jako partie migracji. Jest to sposób działania partii migracji w miejscu podczas migracji z Exchange do Microsoft 365.

### <a name="create-migration-batches"></a>Tworzenie partii migracji

Oto przykładowe polecenie cmdlet partii migracji służące do rozpoczynania przenoszek.

```powershell
New-MigrationBatch -Name T2Tbatch -SourceEndpoint target_source_7977 -CSVData ([System.IO.File]::ReadAllBytes('users.csv')) -Autostart -TargetDeliveryDomain target.onmicrosoft.com

Identity                   Status  Type               TotalCount
--------                   ------  ----               ----------
T2Tbatch                   Syncing ExchangeRemoteMove 1
```

> [!NOTE]
> Adres e-mail w pliku CSV musi być określony w dzierżawie docelowej, a nie w dzierżawie źródłowej.
>
> [Aby uzyskać więcej informacji na temat polecenia cmdlet, kliknij tutaj](/powershell/module/exchange/new-migrationbatch)
>
> [W przypadku przykładowego pliku CSV kliknij tutaj](/exchange/csv-files-for-mailbox-migration-exchange-2013-help)

Przesyłanie partii migracji jest również obsługiwane z nowego centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a> po wybraniu opcji między dzierżawami.

### <a name="update-on-premises-mailusers"></a>Aktualizowanie lokalnych użytkowników poczty

Gdy skrzynka pocztowa zostanie przeniesiony z źródłowego do docelowego, upewnij się, że lokalni użytkownicy poczty zarówno w źródłowym, jak i docelowym, są aktualizowani przy użyciu nowego adresu targetAddress. W przykładach wartość targetDeliveryDomain użyta podczas **przenoszenia to contoso.onmicrosoft.com**. Zaktualizuj adres docelowy użytkowników poczty.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Czy po zakończeniu przenoszenia musimy zaktualizować lokalne skrzynki poczty zdalnej w źródłowym środowisku?**

Tak, podczas przenoszenia źródłowej skrzynki pocztowej dzierżawy źródłowej do dzierżawy docelowej należy zaktualizować wartość targetAddress (RemoteRoutingAddress/ExternalEmailAddress) źródłowej skrzynki pocztowej dzierżawy lokalnej.  Rozsyłanie poczty może być zgodne z odwołaniami wielu użytkowników poczty o różnych adresach targetAddresses, natomiast wyszukiwania wolny/zajęty dla użytkowników poczty MUSZĄ być kierowane do lokalizacji użytkownika skrzynki pocztowej. Odnośniki wolny/zajęty nie będą owijać wielu przekierowań.

**Czy Teams migrują spotkania między dzierżawami?**

Spotkania zostaną przeniesione, jednak adres URL spotkania Teams się nie zaktualizuje w przypadku migrowania elementów między dzierżawami. Ponieważ adres URL będzie nieprawidłowy w dzierżawie docelowej, należy usunąć i ponownie utworzyć Teams spotkania.

**Czy zawartość Teams czatu jest migrowana między dzierżawami?**

Nie, zawartość Teams czatu nie jest migrowana między dzierżawami.

**Jak mogę zobaczyć tylko ruchy, które są przenosine między dzierżawami, a nie moje przeniesienie na wychodzie i wyniesienie z domu?**

Użyj _parametru Flags_ . Oto przykład.

```powershell
Get-MoveRequest -Flags "CrossTenant"
```

**Czy możesz podać przykładowe skrypty do kopiowania atrybutów używanych podczas testowania?**

> [!NOTE]
> PRZYKŁAD — BEZ GWARANCJI Ten skrypt zakłada połączenie zarówno ze źródłową skrzynką pocztową (w celu uzyskania wartości źródłowych), jak i z docelowymi usługami domenowych lokalna usługa Active Directory (w celu sygnatury obiektu ADUser). Jeśli w źródle jest włączony proces sądowy lub odzyskiwanie pojedynczych elementów, ustaw je na koncie docelowym.  Spowoduje to zwiększenie rozmiaru magazynu w koncie docelowym do 100 GB.



   ```powershell
   # This will export users from the source tenant with the CustomAttribute1 = "Cross-Tenant-Project"
   # These are the 'target' users to be moved to the Northwind org tenant
   $outFileUsers = "$home\desktop\UsersToMigrate.txt"
   $outFileUsersXML = "$home\desktop\UsersToMigrate.xml"
   Get-Mailbox -Filter "CustomAttribute1 -like 'Cross-Tenant-Project'" -ResultSize Unlimited | Select-Object -ExpandProperty  Alias | Out-File $outFileUsers
   $mailboxes = Get-Content $outFileUsers
   $mailboxes | ForEach-Object {Get-Mailbox $_} | Select-Object PrimarySMTPAddress,Alias,SamAccountName,FirstName,LastName,DisplayName,Name,ExchangeGuid,ArchiveGuid,LegacyExchangeDn,EmailAddresses | Export-Clixml $outFileUsersXML
   ```

   ```powershell
   # Copy the file $outfile to the desktop of the target on-premises then run the below to create MEU in Target
   $mailboxes = Import-Clixml $home\desktop\UsersToMigrate.xml
   add-type -AssemblyName System.Web
   foreach ($m in $mailboxes) {
       $organization = "@contoso.onmicrosoft.com"
       $mosi = $m.Alias+$organization
       $Password = [System.Web.Security.Membership]::GeneratePassword(16,4) | ConvertTo-SecureString -AsPlainText -Force
       $x500 = "x500:" +$m.LegacyExchangeDn
       $tmpUser = New-MailUser -MicrosoftOnlineServicesID $mosi -PrimarySmtpAddress $mosi -ExternalEmailAddress $m.PrimarySmtpAddress -FirstName $m.FirstName -LastName $m.LastName -Name $m.Name -DisplayName $m.DisplayName -Alias $m.Alias -Password $Password
       $tmpUser | Set-MailUser -EmailAddresses @{add=$x500} -ExchangeGuid $m.ExchangeGuid -ArchiveGuid $m.ArchiveGuid -CustomAttribute1 "Cross-Tenant-Project"
       $tmpx500 = $m.EmailAddresses | ?{$_ -match "x500"}
       $tmpx500 | %{Set-MailUser $m.Alias -EmailAddresses @{add="$_"}}
       }
   ```

   ```powershell
   # Now sync the changes from On-Premises to Azure and Exchange Online in the Target tenant
   # This action should create the target mail enabled users (MEUs) in the Target tenant
   Start-ADSyncCycle
   ```

**Jak uzyskać dostęp do Outlook dnia 1 po tym, jak skrzynka pocztowa zostanie przeniesiona?**

Ponieważ tylko jedna dzierżawa może być właścicielem domeny, poprzedni podstawowy adres SMTPAddress nie zostanie skojarzony z użytkownikiem w dzierżawie docelowej po zakończeniu przenoszenia skrzynki pocztowej. tylko te domeny skojarzone z nową dzierżawą. Outlook używa nowej głównej sieci użytkowników do uwierzytelniania w usłudze, Outlook profil oczekuje, że starsza główna nazwa SMTPAddress będzie odpowiadać skrzynce pocztowej w systemie docelowym. Ponieważ starszy adres nie znajduje się w systemie docelowym, profil programu Outlook nie będzie łączyć się ze znalezieniem nowo przeniesionej skrzynki pocztowej.

W tym wdrożenie wstępne użytkownicy będą musieli odbudować swój profil przy użyciu nowej głównej sieci, podstawowego adresu SMTP i ponownie zsynchronizować zawartość OST.

> [!NOTE]
> Zaplanuj odpowiednie planowanie wsadu użytkowników do wykonania. Podczas tworzenia profilów klientów należy uwzględnić wykorzystanie sieci i wydajność, Outlook następnie do klientów są pobierane kolejne pliki OST i OAB.

**Do Exchange ról RBAC muszę być członkiem, aby skonfigurować lub ukończyć przenoszenie między dzierżawami?**

Istnieje macierz ról oparta na założeniach dotyczących obowiązków delegowanych podczas wykonywania przenoszenia skrzynki pocztowej. Obecnie wymagane są dwie role:

- Pierwsza rola jest w przypadku zadania konfiguracji etapowej, które określa autoryzację przenoszenia zawartości do granicy dzierżawy/organizacji lub poza nie. Przenoszenie danych z kontroli organizacji jest kluczowym problemem dla wszystkich firm, dlatego zdecydowaliśmy się na najwyższą przypisaną rolę administratora organizacji (OrgAdmin). Ta rola musi zmienić lub skonfigurować nowy program OrganizationRelationship, który definiuje funkcję -MailboxMoveCapability w organizacji zdalnej. Tylko administrator organizacji może zmienić ustawienie MailboxMoveCapability, natomiast innymi atrybutami w programie OrganizationRelationship może zarządzać administrator udostępniania federckiego.

- Rolę wykonywania rzeczywistych poleceń przenoszenia można delegować na funkcję niższego poziomu. Rola Przenoszenia skrzynek pocztowych jest przypisana do funkcji przenoszenia skrzynek pocztowych do organizacji i poza nią.

**Jak wybrać adres SMTP dla wartości targetAddress (TargetDeliveryDomain) dla przekonwertowanych skrzynek pocztowych (konwersja na konwersję z użytkownika MailUser)?**

Exchange jest przenosłana przy użyciu funkcji MRS twórz wartość targetAddress w oryginalnej źródłowej skrzynce pocztowej podczas konwertowania na użytkownika poczty, dopasowując adres e-mail (adres proxyAddress) do obiektu docelowego. Ten proces przenosi wartość -TargetDeliveryDomain przekazaną do polecenia move, a następnie sprawdza pasujący serwer proxy dla tej domeny po stronie docelowej. Gdy znajdziemy dopasowanie, zgodny adres proxyAddress jest używany do ustawienia wartości ExternalEmailAddress (targetAddress) dla przekonwertowanego obiektu skrzynki pocztowej (obecnie MailUser).

**Jak przejść uprawnień do skrzynki pocztowej?**

Do uprawnień skrzynki pocztowej należą: Wyślij w imieniu i Dostęp do skrzynki pocztowej:

- W imieniu nadawcy (AD:publicDelegates) jest przechowywane wartości DN adresatów z dostępem do skrzynki pocztowej użytkownika jako pełnomocnik. Ta wartość jest przechowywana w usłudze Active Directory i obecnie nie jest prze zapisywana jako część przejścia skrzynki pocztowej. Jeśli dla źródłowej skrzynki pocztowej ustawiono ustawienia publicDelegates, po zakończeniu konwersji użytkownika z użytkownikami z grupy z użytkownikami z użytkownikami z dostępem do skrzynki pocztowej w środowisku docelowym należy ponownie przećwic ustawienia publicDelegates w docelowej skrzynce pocztowej, uruchamiając usługę `Set-Mailbox <principle> -GrantSendOnBehalfTo <delegate>`.

- Uprawnienia skrzynki pocztowej przechowywane w skrzynce pocztowej są przenoszone do skrzynki pocztowej po przenoszeniu zarówno głównego użytkownika, jak i pełnomocnika do systemu docelowego. Na przykład użytkownikowi, TestUser_7 do skrzynki pocztowej, która TestUser_8 w dzierżawie usługi SourceCompany.onmicrosoft.com. Po zakończeniu przenoszenia skrzynki TargetCompany.onmicrosoft.com w katalogu docelowym są ustawione te same uprawnienia. Poniżej przedstawiono *przykłady użycia funkcji Get-MailboxPermission* TestUser_7 zarówno w dzierżawie źródłowej, jak i docelowej. Exchange cmdlet są odpowiednio poprzedzone prefiksem źródłowym i docelowym.

Oto przykład wyniku uprawnienia skrzynki pocztowej przed przeniesieniem.

```powershell
Get-SourceMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@SourceCompany.onmicrosoft.com         {FullAccess}                         False       False
```

Oto przykład wyniku przeniesienia uprawnień skrzynki pocztowej.

```powershell
Get-TargetMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@TargetCompany.onmicrosoft.com         {FullAccess}                         False       False
```

> [!NOTE]
> Uprawnienia do skrzynek pocztowych i kalendarzy w wielu dzierżawach NIE są obsługiwane. Głównych użytkowników i pełnomocników należy zorganizować w skonsolidowane partie przenoszenia, tak aby połączone skrzynki pocztowe zostały jednocześnie połączone z dzierżawą źródłową.

**Jaki serwer proxy X500 powinien zostać dodany do docelowych adresów proxy użytkownika poczty, aby włączyć migrację?**

Migracja skrzynek pocztowych między dzierżawami wymaga, aby wartość LegacyExchangeDN obiektu źródłowej skrzynki pocztowej miała sygnaturę jako 500-znakowy adres e-mail w docelowym obiekcie MailUser.

Przykład:

```powershell
LegacyExchangeDN value on source mailbox is:
/o=First Organization/ou=Exchange Administrative Group(FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara

so, the x500 email address to be added to target MailUser object would be:
x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9-Lara
```

> [!NOTE]
> Oprócz tego serwera proxy X500 musisz skopiować wszystkie serwery proxy X500 ze skrzynki pocztowej w źródle do skrzynki pocztowej w docelowej skrzynce pocztowej.

**Czy dzierżawa źródłowa i docelowa może korzystać z tej samej nazwy domeny?**

L.p. Nazwy domen dzierżawy źródłowej i docelowej muszą być unikatowe. Na przykład domena źródłowa domeny contoso.com i docelowa domena domeny fourthcoffee.com.

**Czy udostępnione skrzynki pocztowe zostaną przenieść i nadal będą działać?**

Tak, jednak uprawnienia do magazynu są przechowywane tylko w sposób opisany w tych artykułach:

- [Microsoft Docs | Zarządzanie uprawnieniami adresatów w aplikacji Exchange Online](/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)

- [pomoc techniczna firmy Microsoft | Jak przyznać uprawnienia do Exchange skrzynki Outlook pocztowej w Office 365 dedykowanych](https://support.microsoft.com/topic/how-to-grant-exchange-and-outlook-mailbox-permissions-in-office-365-dedicated-bac01b2c-08ff-2eac-e1c8-6dd01cf77287)

**Masz jakieś zalecenia dotyczące partii?**

Nie przekraczaj 2000 skrzynek pocztowych na partię. Zdecydowanie zalecamy przesyłanie partii na dwa tygodnie przed datą wycięcia, ponieważ nie ma żadnego wpływu na użytkowników końcowych podczas synchronizacji. Jeśli potrzebujesz wskazówek dotyczących skrzynek pocztowych powyżej 50 000, możesz przejść do listy dystrybucyjnej opinii inżynierskich w crosstenantmigrationpreview@service.microsoft.com.

**Co zrobić, jeśli używam szyfrowania usługi z kluczem klienta?**

Skrzynka pocztowa zostanie odszyfrowana przed przeniesieniem. Jeśli klucz klienta nadal jest wymagany, upewnij się, że w dzierżawie docelowej jest skonfigurowany klucz klienta. Aby [uzyskać więcej informacji](/microsoft-365/compliance/customer-key-overview) , zobacz tutaj.

**Jaki jest szacowany czas migracji?**

W poniższej tabeli przedstawiono wskazówki dotyczące tego, kiedy [](/exchange/mailbox-migration/office-365-migration-best-practices#estimated-migration-times) należy oczekiwać zbiorczej migracji skrzynek pocztowych lub poszczególnych migracji. Te oszacowania są oparte na analizie danych poprzednich migracji klientów. Ponieważ każde środowisko jest unikatowe, twoja dokładna szybkość migracji może się różnić.

Należy pamiętać, że ta funkcja jest obecnie w wersji zapoznawczej i na poziomie umowy SLA, a żadne mające zastosowanie poziomy usług nie mają zastosowania do żadnych problemów z wydajnością i dostępnością podczas stanu wersji Preview tej funkcji.

**Ochrona dokumentów w dzierżawie źródłowej zużywanych przez użytkowników w dzierżawie docelowej.**

Migracja między dzierżawami migruje tylko dane skrzynek pocztowych i nic innego. Istnieje wiele innych opcji, które o dokumencie podano w następującym wpisie w blogu, które mogą okazać się pomocne: <https://techcommunity.microsoft.com/t5/security-compliance-and-identity/mergers-and-spinoffs/ba-p/910455>

**Czy w dzierżawie docelowej mogę mieć takie same etykiety, jak w dzierżawie źródłowej, jako jedyny zestaw etykiet lub dodatkowy zestaw etykiet dla migrowanych użytkowników w zależności od wyrównania między organizacjami.**

Ponieważ migracje między dzierżawami nie eksportują etykiet i nie ma możliwości udostępniania etykiet między dzierżawami, można to osiągnąć tylko przez ponowne utworzyć etykiety w dzierżawie docelowej.

**Czy obsługujesz przenoszenie Grupy Microsoft 365?**

Obecnie funkcja migracji skrzynek pocztowych między dzierżawami nie obsługuje migracji Grupy Microsoft 365.

**Czy administrator dzierżawy źródłowej może przeprowadzać wyszukiwanie zbierania elektronicznych materiałów dowodowych w skrzynce pocztowej po migracji skrzynki pocztowej do nowej/docelowej dzierżawy?**

Nie, po migracji skrzynek pocztowych między dzierżawami nie działa zbierania elektronicznych materiałów dowodowych dla skrzynki pocztowej migrowanych użytkowników w źródle. Jest to spowodowane tym, że w źródle nie ma już skrzynki pocztowej, w której będzie można wyszukiwać, ponieważ została już zmigrowana do dzierżawy docelowej i należy do dzierżawy docelowej. Zbierania elektronicznych materiałów dowodowych po migracji skrzynek pocztowych można wykonać tylko w dzierżawie docelowej (gdzie teraz istnieje skrzynka pocztowa). Jeśli po migracji kopia źródłowej skrzynki pocztowej musi zostać utrwalona w dzierżawie źródłowej, administrator w źródle może skopiować zawartość do alternatywnej skrzynki pocztowej przed migracją na potrzeby przyszłych operacji zbierania elektronicznych materiałów dowodowych dotyczących danych.

## <a name="known-issues"></a>Znane problemy

- **Problem: Po migracji Teams funkcje dzierżawy źródłowej będą ograniczone.** Po zakończeniu migracji skrzynki pocztowej do dzierżawy docelowej Teams dzierżawy źródłowej nie będzie już mieć dostępu do skrzynki pocztowej użytkownika. Jeśli więc użytkownik zaloguje się do usługi Teams przy użyciu poświadczeń dzierżawy źródłowej, może dołączyć do nich utrata funkcjonalności, taka jak brak możliwości zaktualizowania obrazu profilu, brak aplikacji kalendarza oraz brak możliwości wyszukiwania zespołów publicznych i dołączania do nich.

- **Problem: Nie można migrować automatycznie rozwiniętych archiwów.** Funkcja migracji między dzierżawami obsługuje migracje podstawowej skrzynki pocztowej i archiwazyjnej skrzynki pocztowej dla określonego użytkownika. Jeśli jednak użytkownik w źródle ma automatycznie rozwinięte archiwum — co oznacza więcej niż jedną archiwacyjną skrzynkę pocztową, funkcja nie może przeprowadzić migracji dodatkowych archiwów i powinna się nie powieść.

- **Problem: W tle przenosi się użytkowników poczty w chmurze z niebędący właścicielem smtp proxyAddress bloku MRS.** Podczas tworzenia obiektów użytkownika poczty w dzierżawie docelowej należy się upewnić, że wszystkie adresy serwerów proxy SMTP należą do organizacji dzierżawy docelowej. Jeśli dla użytkownika poczty docelowej istnieje adres proxyAddress SMTP, który nie należy do dzierżawy lokalnej, nie będzie można konwersji użytkownika poczty na skrzynkę pocztową. Wynika to z naszego zapewniania, że obiekty skrzynek pocztowych mogą wysyłać pocztę tylko z domen, dla których dzierżawa ma autorytatywny adres (domeny, których dotyczy dzierżawa):

  - Podczas synchronizowania użytkowników z lokalnego przy użyciu usługi Azure AD Połączenie inicjowanie obsługi administracyjnej lokalnych obiektów użytkownika poczty za pomocą adresu ExternalEmailAddress, który wskaże dzierżawę źródłową, w której znajduje się skrzynka pocztowa (LaraN@contoso.onmicrosoft.com), oraz sygnaturę PrimarySMTPAddress jako domenę, która znajduje się w dzierżawie docelowej (Lara.Newton@northwind.com). Te wartości są synchronizowane z dzierżawą, a odpowiedni użytkownik poczty jest aprowowany i gotowy do migracji. W tym miejscu jest pokazany obiekt przykładowy.

    ```powershell
    Get-MailUser LaraN | select ExternalEmailAddress, EmailAddresses

    ExternalEmailAddress               EmailAddresses
    --------------------               --------------
    SMTP:LaraN@contoso.onmicrosoft.com {SMTP:lara.newton@northwind.com}
    ```

   > [!NOTE]
   > Adres *contoso.onmicrosoft.com* nie *występuje* w tablicy EmailAddresses/proxyAddresses.

- **Problem: obiekty użytkowników poczty z podstawowymi adresami SMTP "zewnętrznymi" są modyfikowane /resetowane do "wewnętrznych" domen firmy, do których odebrano domeny**

  Obiekty użytkownika poczty są wskaźnikami do nie localowych skrzynek pocztowych. W przypadku migracji skrzynek pocztowych między dzierżawami obiekty mailUser reprezentują źródłową skrzynkę pocztową (z perspektywy organizacji docelowej) lub docelową skrzynkę pocztową (z perspektywy organizacji źródłowej). Wartość MailUsers (Adres_użytkownika poczty) będzie mieć wartość ExternalEmailAddress (targetAddress), która wskazuje adres SMTP rzeczywistej skrzynki pocztowej (ProxyTest@fabrikam.onmicrosoft.com) i podstawowy adres SMTP reprezentujący wyświetlany adres SMTP użytkownika skrzynki pocztowej w katalogu. Niektóre organizacje wybierają wyświetlanie podstawowego adresu SMTP jako zewnętrznego adresu SMTP, a nie jako adresu będącego własnością/zweryfikowanego przez dzierżawę lokalną (na przykład fabrikam.com zamiast jako contoso.com).  Jednak po zastosowaniu obiektu planu usługi Exchange do użytkownika poczty w ramach operacji licencjonowania podstawowy adres SMTP jest modyfikowany w celu pokazania go jako domena zweryfikowana przez organizację lokalną (contoso.com). Istnieją dwie potencjalne przyczyny:

  - Gdy do użytkownika poczty zostanie zastosowany dowolny plan usługi usługi Exchange, proces usługi Azure AD zacznie wymuszać czyszczenie serwera proxy, aby upewnić się, że lokalna organizacja nie może wysyłać poczty e-mail, fałszowania ani poczty z innej dzierżawy. Każdy adres SMTP obiektu adresata z tymi planami usług zostanie usunięty, jeśli ten adres nie został zweryfikowany przez organizację lokalną. Tak jak w tym przykładzie domena domeny Fabikam.com NIE została zweryfikowana przez dzierżawę usługi contoso.onmicrosoft.com, więc usunięcie jej powoduje usunięcie jej fabrikam.com domeny. Jeśli chcesz utrzymać te domeny zewnętrzne w użytą dla użytkownika poczty przed migracją lub po migracji, musisz zmienić procesy migracji w celu usuwania licencji po zakończeniu procesu przenoszenia lub przed przeniesieniem w celu zapewnienia, że zastosowano oczekiwane znakowanie zewnętrzne. Aby nie miało to wpływu na usługę poczty, należy się upewnić, że obiekt skrzynki pocztowej ma poprawnie licencjonowaną licencję.
  - Przykładowy skrypt usuwania planów usługi dla użytkownika poczty w contoso.onmicrosoft.com dzierżawie poczty.

    ```powershell
    $LO = New-MsolLicenseOptions -AccountSkuId "contoso:ENTERPRISEPREMIUM" DisabledPlans "LOCKBOX_ENTERPRISE","EXCHANGE_S_ENTERPRISE","INFORMATION_BARRIERS","MIP_S_CLP2","MIP_S_CLP1","MYANALYTICS_P2","EXCHANGE_ANALYTICS","EQUIVIO_ANALYTICS","THREAT_INTELLIGENCE","PAM_ENTERPRISE","PREMIUM_ENCRYPTION"
    Set-MsolUserLicense -UserPrincipalName ProxyTest@contoso.com LicenseOptions $lo
    ```

       Tutaj są wyświetlane wyniki w zestawie przypisanych planów usługi.

    ```powershell
    (Get-MsolUser -UserPrincipalName ProxyTest@contoso.com).licenses | Select-Object -ExpandProperty ServiceStatus |sort ProvisioningStatus -Descending

    ServicePlan           ProvisioningStatus
    -----------           ------------------
    ATP_ENTERPRISE        PendingProvisioning
    MICROSOFT_SEARCH      PendingProvisioning
    INTUNE_O365           PendingActivation
    PAM_ENTERPRISE        Disabled
    EXCHANGE_ANALYTICS    Disabled
    EQUIVIO_ANALYTICS     Disabled
    THREAT_INTELLIGENCE   Disabled
    LOCKBOX_ENTERPRISE    Disabled
    PREMIUM_ENCRYPTION    Disabled
    EXCHANGE_S_ENTERPRISE Disabled
    INFORMATION_BARRIERS  Disabled
    MYANALYTICS_P2        Disabled
    MIP_S_CLP1            Disabled
    MIP_S_CLP2            Disabled
    ADALLOM_S_O365        PendingInput
    RMS_S_ENTERPRISE      Success
    YAMMER_ENTERPRISE     Success
    PROJECTWORKMANAGEMENT Success
    BI_AZURE_P2           Success
    WHITEBOARD_PLAN3      Success
    SHAREPOINTENTERPRISE  Success
    SHAREPOINTWAC         Success
    KAIZALA_STANDALONE    Success
    OFFICESUBSCRIPTION    Success
    MCOSTANDARD           Success
    Deskless              Success
    STREAM_O365_E5        Success
    FLOW_O365_P3          Success
    POWERAPPS_O365_P3     Success
    TEAMS1                Success
    MCOEV                 Success
    MCOMEETADV            Success
    BPOS_S_TODO_3         Success
    FORMS_PLAN_E5         Success
    SWAY                  Success
    ```

    Adres PrimarySMTPAddress użytkownika nie jest już przesuwany. Domena fabrikam.com jest własnością dzierżawy usługi contoso.onmicrosoft.com i będzie utrwalona jako podstawowy adres SMTP widoczny w katalogu.

    Oto przykład.

    ```powershell
    Get-Recipient ProxyTest | Format-Table -AutoSize UserPrincipalName, PrimarySmtpAddress, ExternalEmailAddress, ExternalDirectoryObjectId
    UserPrincipalName               PrimarySmtpAddress              ExternalEmailAddress                 ExternalDirectoryObjectId
    -----------------               ------------------              --------------------                 -------------------------
    ProxyTest@fabrikam.com          ProxyTest@fabrikam.com          SMTP:ProxyTest@fabrikam.com          e2513482-1d5b-4066-936a-cbc7f8f6f817
    ```

    - Jeśli dla ustawienia msExchRemoteRecipientType jest ustawiona wartość 8 (DeprovisionMailbox), w przypadku lokalnych użytkowników poczty migrowanych do dzierżawy docelowej logika oczyszczania serwera proxy na platformie Azure usunie domeny będące własnością i zresetuje portal primarySMTP do należącej domeny. Wyczyszczenie ustawienia msExchRemoteRecipientType w lokalnym czacie użytkownika poczty powoduje, że logika czyszczenia serwera proxy nie ma już zastosowanie.

      Poniżej znajduje się pełny zestaw bieżących planów usług, które zawierają Exchange Online.

      | Name (Nazwa)                                             |
      | ------------------------------------------------ |
      | Advanced eDiscovery Storage (500 GB)              |
      | Skrytka klienta                                 |
      | Ochrona przed utratą danych                             |
      | Exchange Enterprise CAL Services (EOP, DLP)      |
      | Exchange Essentials                              |
      | Exchange Foundation                              |
      | Exchange Online (P1)                             |
      | Exchange Online (plan 1)                         |
      | Exchange Online (plan 2)                         |
      | Exchange Online — archiwum dla usługi Exchange Online    |
      | Exchange Online — archiwum dla serwera Exchange Server    |
      | Exchange Online nieaktywny dodatek użytkownika             |
      | Exchange Online Kiosk                            |
      | Exchange Online Multi-Geo                        |
      | Exchange Online Plan 1                           |
      | Exchange Online — POP                              |
      | Exchange Online Protection                       |
      | Bariery informacyjne                             |
      | Information Protection dla Office 365 — Premium  |
      | Information Protection dla Office 365 — Standardowe |
      | Szczegółowe informacje przez MyAnalytics                          |
      | Microsoft 365 zaawansowanej inspekcji                  |
      | Microsoft Bookings                               |
      | Microsoft Business Center                        |
      | Microsoft MyAnalytics (Pełne)                     |
      | Office 365 Advanced eDiscovery                   |
      | Ochrona usługi Office 365 w usłudze Microsoft Defender (Plan 1)       |
      | Ochrona usługi Office 365 w usłudze Microsoft Defender (Plan 2)       |
      | Office 365 zarządzanie dostępem z uprawnieniami          |
      | Premium szyfrowania w Office 365                 |
      |                                                  |
