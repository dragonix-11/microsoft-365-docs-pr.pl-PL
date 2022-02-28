---
title: Tożsamość federowana w środowisku Microsoft 365 testowym
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 05/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 'Podsumowanie: Skonfiguruj uwierzytelnianie federowane w środowisku Microsoft 365 testowym.'
ms.openlocfilehash: 6553590c06df4caf099c7b4db47d253bd37b39fd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983437"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>Tożsamość federowana w środowisku Microsoft 365 testowym

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

Microsoft 365 obsługuje tożsamość federacyjną. Oznacza to, że zamiast sprawdzania poprawności poświadczeń samą Microsoft 365 odwołuje użytkownika łączącego się z serwerem uwierzytelniania federatora, który Microsoft 365 zaufany. Jeśli poświadczenia użytkownika są prawidłowe, federowany serwer uwierzytelniania wydaje token zabezpieczający, który klient wysyła do firmy Microsoft 365 jako dowód uwierzytelniania. Tożsamość federowana umożliwia ładowanie i skalowanie uwierzytelniania w ramach subskrypcji usługi Microsoft 365 oraz zaawansowanych scenariuszy uwierzytelniania i zabezpieczeń.
  
W tym artykule opisano, jak skonfigurować uwierzytelnianie federowane w środowisku testowym Microsoft 365, co spowoduje następujące działania:

![Uwierzytelnianie federowane w Microsoft 365 testowym.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
Ta konfiguracja składa się z:
  
- Subskrypcja Microsoft 365 E5 wersji próbnej lub produkcyjnej.
    
- Uproszczony intranet organizacji połączony z Internetem składający się z pięciu maszyn wirtualnych w podsieci sieci wirtualnej platformy Azure (DC1, APP1, CLIENT1, ADFS1 i PROXY1). Usługa Azure AD Połączenie działa w aplikacji APP1 w celu zsynchronizowania listy kont w domenie Usługi domenowe w usłudze Active Directory w celu Microsoft 365. Serwer PROXY1 odbiera przychodzące żądania uwierzytelnienia. Usługi ADFS1 sprawdza poświadczenia przy użyciu dc1 i wydaje problemy z tokenami zabezpieczającymi.
    
Konfigurowanie tego środowiska testowego składa się z pięciu etapów:
- [Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku testowania Microsoft 365 hasła](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Etap 2. Tworzenie serwera usług AD FS](#phase-2-create-the-ad-fs-server)
- [Etap 3. Tworzenie internetowego serwera proxy](#phase-3-create-the-web-proxy-server)
- [Etap 4. Tworzenie certyfikatu z podpisem własnym i konfigurowanie usług ADFS1 i PROXY1](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [Etap 5. Konfigurowanie Microsoft 365 tożsamości federowej](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> Nie możesz skonfigurować tego środowiska testowego przy użyciu subskrypcji wersji próbnej platformy Azure.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku testowania Microsoft 365 hasła

Postępuj zgodnie z instrukcjami [w te dotyczące synchronizacji skrótów haseł, aby uzyskać Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Wynikowa konfiguracja wygląda następująco:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowania skrótów haseł.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
Ta konfiguracja składa się z:
  
- Subskrypcja Microsoft 365 E5 próbna lub płatna.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure. Usługa Azure AD Połączenie działa w aplikacji APP1 w celu synchronizowania domeny TESTLAB Usługi domenowe w usłudze Active Directory (AD DS) z dzierżawą usługi Azure AD w ramach subskrypcji usługi Microsoft 365 okresowo.

## <a name="phase-2-create-the-ad-fs-server"></a>Etap 2. Tworzenie serwera usług AD FS

Serwer usług AD FS zapewnia uwierzytelnianie federowane między Microsoft 365 a kontami w domenie corp.contoso.com hostowanej w dc1.
  
Aby utworzyć maszynę wirtualną platformy Azure dla usług ADFS1, wprowadź nazwę subskrypcji, grupę zasobów i lokalizację platformy Azure w konfiguracji podstawowej, Azure PowerShell następnie uruchom te polecenia w wierszu polecenia programu Azure PowerShell na komputerze lokalnym.
  
```powershell
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Następnie za pomocą portalu [Azure Portal](https://portal.azure.com) połącz się z maszyną wirtualną ADFS1 przy użyciu nazwy i hasła konta administratora lokalnego ADFS1, a następnie otwórz wiersz Windows PowerShell polecenia.
  
Aby sprawdzić rozdzielczość nazw i komunikację sieciową między usługami ADFS1 i DC1, uruchom polecenie **ping dc1.corp.contoso.com** i sprawdź, czy są cztery odpowiedzi.
  
Następnie dołącz maszynę wirtualną USŁUGI ADFS1 do domeny CORP za pomocą tych poleceń w wierszu polecenia usługi WINDOWS POWERSHELL w umacie ADFS1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Wynikowa konfiguracja wygląda następująco:
  
![Serwer usług AD FS dodany do synchronizacji katalogów dla Microsoft 365 testowego.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>Etap 3. Tworzenie internetowego serwera proxy

Serwer PROXY1 zapewnia serwer proxy wiadomości uwierzytelniania między użytkownikami próbujących uwierzytelnić się a usługami ADFS1.
  
Aby utworzyć maszynę wirtualną platformy Azure dla serwera PROXY1, wpisz nazwę grupy zasobów i lokalizację platformy Azure, a następnie uruchom te polecenia w wierszu polecenia Azure PowerShell na komputerze lokalnym.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Serwer PROXY1 ma przypisany statyczny publiczny adres IP, ponieważ należy utworzyć publiczny rekord DNS, który na niego wskazuje i nie może się zmienić po ponownym uruchomieniu maszyny wirtualnej PROXY1.
  
Następnie dodaj regułę do grupy zabezpieczeń sieciowych w podsieci CorpNet, aby zezwolić na niechciany ruch przychodzący z Internetu do prywatnego adresu IP serwera PROXY1 i portu TCP 443. Uruchom te polecenia w wierszu Azure PowerShell polecenia na komputerze lokalnym.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

Następnie za pomocą portalu [Azure Portal](https://portal.azure.com) połącz się z maszyną wirtualną PROXY1 przy użyciu nazwy i hasła konta administratora lokalnego PROXY1, a następnie otwórz wiersz polecenia Windows PowerShell w serwerze PROXY1.
  
Aby sprawdzić rozdzielczość nazw i komunikację sieciową między serwerami PROXY1 i DC1, uruchom polecenie **ping dc1.corp.contoso.com** i sprawdź, czy są cztery odpowiedzi.
  
Następnie dołącz maszynę wirtualną PROXY1 do domeny CORP za pomocą tych poleceń w wierszu Windows PowerShell w proxy1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Wyświetl publiczny adres IP serwera PROXY1 przy użyciu tych Azure PowerShell na komputerze lokalnym.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Następnie należy współpracować z publicznym dostawcą DNS i utworzyć nowy publiczny rekord DNS A dla **domeny fs.testlab.**\<*your DNS domain name*> która rozwiązuje adres IP wyświetlany za pomocą **polecenia Write-Host** . **Fs.testlab.**\<*your DNS domain name*> jest określane jako  *FQDN usługi federrskiej*.
  
Następnie za pomocą portalu [Azure Portal](https://portal.azure.com) połącz się z maszyną wirtualną DC1 przy użyciu poświadczeń CORPUser1\\, a następnie uruchom następujące polecenia w wierszu polecenia Windows PowerShell administratora:
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
Te polecenia tworzą wewnętrzny rekord DNS A, dzięki czemu maszyny wirtualne w sieci wirtualnej platformy Azure mogą rozpoznać nazwę FQDN wewnętrznej usługi federniczej na prywatny adres IP usługi ADFS1.
  
Wynikowa konfiguracja wygląda następująco:
  
![Serwer proxy aplikacji sieci Web dodany do programu DirSync dla Microsoft 365 testowego.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Etap 4. Tworzenie certyfikatu z podpisem własnym i konfigurowanie usług ADFS1 i PROXY1

W tej fazie utworzysz certyfikat cyfrowy z podpisem własnym dla swojej domeny FQDN usługi federlnej i skonfigurujesz usługi ADFS1 i PROXY1 jako farmę usług AD FS.
  
Najpierw użyj portalu [Azure Portal](https://portal.azure.com), aby połączyć się z maszyną wirtualną DC1 przy użyciu poświadczeń CORPUser1\\, a następnie otwórz wiersz polecenia Windows PowerShell administratora.
  
Następnie utwórz konto usługi AD FS za pomocą tego polecenia w wierszu Windows PowerShell w dc1:
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
To polecenie monituje o podaniem hasła do konta. Wybierz silne hasło i zanotuj je w zabezpieczonej lokalizacji. Będzie ona potrzebna w tej fazie i w fazie 5.
  
Za pomocą [portalu Azure portal możesz](https://portal.azure.com) nawiązać połączenie z maszyną wirtualną ADFS1 przy użyciu poświadczeń CORPUser1\\. Otwórz wiersz polecenia polecenia Windows PowerShell na poziomie administratora w usłudze ADFS1, wpisz swoją federacyjną domenę FQDN, a następnie uruchom następujące polecenia, aby utworzyć certyfikat z podpisem własnym:
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

Następnie skorzystaj z poniższych kroków, aby zapisać nowy certyfikat z podpisem własnym jako plik.
  
1. Wybierz **przycisk Start**, **wprowadźmmc.exe**, a następnie naciśnij klawisz **Enter**.
    
2. Wybierz **pozycję FileAdd** > **/Remove Snap-in (Usuń przystawkę**).
    
3. W **menu Dodawanie** lub usuwanie przystawki kliknij dwukrotnie pozycję Certyfikaty  na liście dostępnych przystawki, wybierz pozycję **Konto** komputera, a następnie wybierz przycisk **Dalej**.
    
4. W **czacie Wybieranie** komputera wybierz **pozycję Zakończ**, a następnie wybierz przycisk **OK**.
    
5. W drzewie w okienku otwórz **pozycję Certyfikaty (komputer lokalny) > osobiste > certyfikaty**.
    
6. Wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy) certyfikat z twoją witrynie FQDN usługi federrskiej, **wybierz pozycję Wszystkie** zadania, a następnie wybierz pozycję **Eksportuj**.
    
7. Na stronie **powitałej** wybierz pozycję **Dalej**.
    
8. Na stronie **Eksportowanie klucza prywatnego** wybierz pozycję **Tak**, a następnie wybierz przycisk **Dalej**.
    
9. Na stronie **Eksportowanie formatu pliku** wybierz pozycję **Eksportuj wszystkie właściwości rozszerzone**, a następnie wybierz przycisk **Dalej**.
    
10. Na stronie **Zabezpieczenia** wybierz pozycję **Hasło** i wprowadź hasło w ustawieniach **Hasło** i **Potwierdź hasło.**
    
11. Na stronie **Plik do wyeksportowania** wybierz pozycję **Przeglądaj**.
    
12. Przejdź do folderu **C:\\Certs** , wprowadź **wartość SSL** w nazwie **pliku, a** następnie wybierz pozycję **Zapisz.**
    
13. Na stronie **Plik do wyeksportowania** wybierz pozycję **Dalej**.
    
14. Na stronie **Kończenie pracy z Kreatorem eksportu certyfikatów** wybierz pozycję **Zakończ**. Po wyświetleniu monitu wybierz przycisk **OK**.
    
Następnie zainstaluj usługę AD FS za pomocą tego polecenia w wierszu polecenia usługi Windows PowerShell w usłudze ADFS1:
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Poczekaj na ukończenie instalacji.
  
Następnie skonfiguruj usługę AD FS, wykonać następujące czynności:
  
1. Wybierz **przycisk Start**, a następnie wybierz **ikonę Menedżer** serwera.
    
2. W drzewie okna Menedżer serwera wybierz pozycję **AD FS**.
    
3. Na pasku narzędzi u góry wybierz pomarańczowy symbol przestrogi, a następnie wybierz pozycję **Konfiguruj usługę federacyjną na tym serwerze**.
    
4. Na stronie **powitał** Kreatora konfiguracji usług federacyjnych Active Directory wybierz pozycję **Dalej**.
    
5. Na Połączenie **do AD DS** wybierz pozycję **Dalej**.
    
6. Na stronie **Określanie właściwości** usługi:
    
  - W **przypadku certyfikatu SSL** wybierz strzałkę w dół, a następnie wybierz certyfikat z nazwą FQDN Twojej usługi federrskiej.
    
  - W **chmurze Nazwa wyświetlana** usługi federacyjne wprowadź nazwę organizacji fikcyjnej.
    
  - Wybierz pozycję **Dalej**.
    
7. Na stronie **Określanie konta usługi** wybierz pozycję **Wybierz** dla **nazwy klienta**.
    
8. W **chmurze Wybierz konto użytkownika lub usługi** wprowadź **adfs-service**, wybierz pozycję Sprawdź **nazwy**, a następnie wybierz przycisk **OK**.
    
9. W **polecej** Hasło konta wprowadź hasło do konta ADFS-Service, a następnie wybierz pozycję **Dalej**.
    
10. Na stronie **Określanie bazy danych konfiguracji** wybierz pozycję **Dalej**.
    
11. Na stronie **Opcje recenzji** wybierz pozycję **Dalej**.
    
12. Na stronie **Testy wstępne** wybierz pozycję **Konfiguruj**.

13. Na **stronie Wyniki** wybierz pozycję **Zamknij**.
    
14. Wybierz **przycisk Start**, wybierz ikonę zasilania, wybierz pozycję **Uruchom ponownie**, a następnie wybierz pozycję **Kontynuuj**.
    
W portalu [Azure połącz](https://portal.azure.com) się z serwerem PROXY1 za pomocą poświadczeń konta CORPUser1\\.
  
Następnie skorzystaj z poniższych kroków, aby zainstalować certyfikat z podpisem własnym zarówno w serwerze **PROXY1, jak i w aplikacji APP1**.
  
1. Wybierz **przycisk Start**, **wprowadźmmc.exe**, a następnie naciśnij klawisz **Enter**.
    
2. Wybierz **pozycję > dodaj/usuń przystawkę**.
    
3. W **menu Dodawanie** lub usuwanie przystawki kliknij dwukrotnie pozycję Certyfikaty  na liście dostępnych przystawki, wybierz pozycję **Konto** komputera, a następnie wybierz przycisk **Dalej**.
    
4. W **czacie Wybieranie** komputera wybierz **pozycję Zakończ**, a następnie wybierz przycisk **OK**.
    
5. W okienku drzewa otwórz **pozycję Certyfikaty (Komputer lokalny)** > **Certyfikaty** > **_osobiste**.
    
6. Wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy) **Osobiste**, wybierz pozycję **Wszystkie zadania**, a następnie wybierz **importuj**.
    
7. Na stronie **powitałej** wybierz pozycję **Dalej**.
    
8. Na stronie **Plik do importowania** wprowadź **\\\\adfs1certssl.pfx\\\\**, a następnie wybierz pozycję **Dalej**.
    
9. Na stronie **Ochrona klucza prywatnego** wprowadź hasło certyfikatu w opcji **Hasło**, a następnie wybierz pozycję **Dalej.**
    
10. Na stronie **Magazyn certyfikatów** wybierz pozycję **Dalej.**
    
11. Na stronie **Kończenie** wybierz pozycję **Zakończ**.
    
12. Na stronie **Magazyn certyfikatów** wybierz pozycję **Dalej**.
    
13. Po wyświetleniu monitu wybierz przycisk **OK**.
    
14. W drzewie okienka wybierz **pozycję Certyfikaty**.
    
15. Wybierz i przytrzymaj certyfikat (lub kliknij go prawym przyciskiem myszy), a następnie wybierz polecenie **Kopiuj**.
    
16. W okienku drzewa otwórz katalog **Trusted Root Certification** **AuthoritiesCertificates** > .
    
17. Przesuń wskaźnik myszy poniżej listy zainstalowanych certyfikatów, wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy), a następnie wybierz polecenie **Wklej**.
    
Otwórz wiersz polecenia programu PowerShell na poziomie administratora i uruchom następujące polecenie:
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Poczekaj na ukończenie instalacji.
  
Aby skonfigurować usługę serwera proxy aplikacji sieci Web do używania usług ADFS1 jako serwera federacji, skorzystaj z poniższych kroków:
  
1. Wybierz **przycisk Start**, a następnie wybierz **pozycję Menedżer serwera**.
    
2. W okienku drzewa wybierz pozycję **Dostęp zdalny**.
    
3. Na pasku narzędzi u góry wybierz pomarańczowy symbol przestrogi, a następnie wybierz **pozycję Otwórz Kreatora proxy aplikacji sieci Web**.
    
4. Na stronie **powitaowej** Kreatora konfiguracji serwera proxy aplikacji sieci Web wybierz pozycję **Dalej**.
    
5. Na stronie **Federation Server (Serwer federacji** ):
    
  - W polu **Nazwa usługi federejnej** wprowadź nazwę FQDN usługi federrskiej.
    
  - W **polu Nazwa użytkownika** wprowadź **tekst CORPUser1\\**.
    
  - W **polu** Hasło wprowadź hasło do konta użytkownika Użytkownik1.
    
  - Wybierz pozycję **Dalej**.
    
6. Na stronie **Certyfikat serwera proxy usług AD FS** wybierz strzałkę w dół, wybierz certyfikat z witrynie FQDN usługi federnej, a następnie wybierz pozycję **Dalej**.
    
7. Na stronie **Potwierdzenie** wybierz pozycję **Konfiguruj**.
    
8. Na **stronie Wyniki** wybierz pozycję **Zamknij**.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>Etap 5. Konfigurowanie Microsoft 365 tożsamości federowej

Za pomocą [portalu Azure portal](https://portal.azure.com) możesz nawiązać połączenie z maszyną wirtualną APP1 za pomocą poświadczeń konta CORPUser1\\.
  
Skorzystaj z tej procedury, aby skonfigurować usługę Azure AD Połączenie oraz subskrypcję usługi Microsoft 365 na Microsoft 365 uwierzytelnianie federowane:
  
1. Na komputerze stacjonarnym kliknij dwukrotnie pozycję **Azure AD Połączenie**.
    
2. Na stronie **Połączenie usługi Azure AD** wybierz pozycję **Konfiguruj**.
    
3. Na stronie **Dodatkowe zadania** wybierz pozycję **Zmień logowanie użytkownika**, a następnie wybierz pozycję **Dalej**.
    
4. Na stronie **Połączenie do usługi Azure AD** wprowadź nazwę i hasło konta administratora globalnego, a następnie wybierz pozycję **Dalej**.
    
5. Na stronie **Logowanie użytkownika wybierz** pozycję Federacja z usługami **AD FS**, a następnie wybierz pozycję **Dalej**.
    
6. Na stronie **farmy usług AD FS** wybierz pozycję Użyj istniejącej farmy usług **AD FS**, wprowadź **usługę ADFS1** w polu **Nazwa** serwera, a następnie wybierz pozycję **Dalej**.
    
7. Po wyświetleniu monitu o podanie poświadczeń serwera wprowadź poświadczenia konta CORPUser1\\, a następnie wybierz przycisk **OK**.
    
8. Na stronie **Poświadczenia administratora** domeny wprowadź **nazwę CORPUser1\\** w polu **Nazwa** użytkownika, wprowadź hasło do konta w polu Hasło,  a następnie wybierz przycisk **Dalej**.
    
9. Na stronie **Konto usługi AD FS** wprowadź **nazwę CORPADFS-Service\\** w polu **Nazwa** użytkownika domeny, wprowadź hasło do konta w polu **Hasło** użytkownika domeny, a następnie wybierz przycisk **Dalej**.
    
10. Na stronie **Domena usługi Azure AD** w witrynie **Domain** (Domena) wybierz nazwę domeny, która została utworzona wcześniej i dodana do subskrypcji w fazie 1, a następnie wybierz pozycję **Dalej**.
    
11. Na stronie **Wszystko gotowe do skonfigurowania** wybierz pozycję **Konfiguruj**.
    
12. Na stronie **Instalacja ukończona** wybierz pozycję **Weryfikuj**.
    
    Powinny być wyświetlane komunikaty informujące, że zweryfikowano zarówno konfigurację intranetu, jak i Internetu.
    
13. Na stronie **Instalacja ukończona** wybierz pozycję **Zakończ**.
    
Aby pokazać, że działa uwierzytelnianie federowane:
  
1. Otwórz nowe prywatne wystąpienie przeglądarki na komputerze lokalnym i przejdź do strony [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. Aby uzyskać poświadczenia logowania **, wprowadź user1@**\<*the domain created in Phase 1*>.
    
    Jeśli na przykład domena testowa **jest testlab.contoso.com,** należy wprowadzić tekst "user1@testlab.contoso.com". Naciśnij klawisz **Tab** lub zezwalaj na Microsoft 365 automatyczne przekierowywanie Cię.
    
    Powinien zostać wyświetlony temat **Twoje połączenie nie jest stroną prywatną** . Jest to spowodowane tym, że w usługach ADFS1 zainstalowano certyfikat z podpisem własnym, który nie może zostać zweryfikowany na komputerze stacjonarnym. We wdrożeniu produkcyjnym uwierzytelniania federyjnego użyj certyfikatu od zaufanego urzędu certyfikacji, a Twoi użytkownicy nie zobaczą tej strony.
    
3. Na stronie **Twoje połączenie nie jest prywatna** wybierz pozycję **Zaawansowane**, a następnie wybierz **pozycję Kontynuuj do \<*your federation service FQDN*>**. 
    
4. Na stronie z nazwą organizacji fikcyjnej zaloguj się przy użyciu następujących danych:
    
  - **CORP\\ Nazwa użytkownika1**
    
  - Hasło do konta użytkownika user1
    
    Powinna zostać wyświetlony Microsoft Office **strona główna**.
    
Ta procedura pokazuje, że subskrypcja wersji próbnej jest federowana z domeną AD DS corp.contoso.com hostowaną w DC1. Poniżej znajdują się podstawowe informacje o procesie uwierzytelniania:
  
1. Jeśli korzystasz z domeny federacji utworzonej w pierwszym etapie przy użyciu nazwy konta logowania, usługa Microsoft 365 przekierowuje Twoją przeglądarkę do twojej nazwy FQDN i serwera PROXY1 usługi federacji.
    
2. Serwer PROXY1 wysyła do komputera lokalnego fikcyjną stronę logowania firmy.
    
3. Po wysłaniu oprogramowania CORPUser1\\ i hasła do serwera PROXY1 są przekazywane do usługi ADFS1.
    
4. Usługi ADFS1 weryfikowają usługę CORPUser1\\ i hasło za pomocą dc1, a następnie wysyła na komputerze lokalnym token zabezpieczający.
    
5. Token zabezpieczający jest przesyłany na komputer lokalny do Microsoft 365.
    
6. Microsoft 365 sprawdza, czy token zabezpieczający został utworzony przez usługę ADFS1 i zezwala na dostęp.
    
Subskrypcja wersji próbnej jest teraz skonfigurowana z uwierzytelnianiem federacyjnym. Tego środowiska deweloper/testowego można używać na przykład w zaawansowanych scenariuszach uwierzytelniania.
  
## <a name="next-step"></a>Następny krok

Gdy wszystko będzie gotowe do wdrożenia produkcyjnego, gotowego do użycia uwierzytelniania federeracyjnie o wysokiej dostępności dla usługi Microsoft 365 na platformie Azure, zobacz Wdrażanie uwierzytelniania federacji o wysokiej dostępności dla usługi [Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
