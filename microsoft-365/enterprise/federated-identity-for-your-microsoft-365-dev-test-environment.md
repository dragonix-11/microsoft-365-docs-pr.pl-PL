---
title: Tożsamość federacyjna dla środowiska testowego Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Skonfiguruj uwierzytelnianie federacyjne dla środowiska testowego Microsoft 365.'
ms.openlocfilehash: 0214c7778176641c6446106cf92ed173b81b71de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101034"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>Tożsamość federacyjna dla środowiska testowego Microsoft 365

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

Microsoft 365 obsługuje tożsamość federacyjną. Oznacza to, że zamiast walidacji poświadczeń, Microsoft 365 odwołuje się do użytkownika łączącego się z serwerem uwierzytelniania federacyjnego, który Microsoft 365 zaufania. Jeśli poświadczenia użytkownika są poprawne, serwer uwierzytelniania federacyjnego wystawia token zabezpieczający wysyłany przez klienta do Microsoft 365 jako dowód uwierzytelniania. Tożsamość federacyjna umożliwia odciążanie i skalowanie uwierzytelniania dla subskrypcji Microsoft 365 oraz zaawansowanych scenariuszy uwierzytelniania i zabezpieczeń.
  
W tym artykule opisano sposób konfigurowania uwierzytelniania federacyjnego dla środowiska testowego Microsoft 365, co daje następujące rezultaty:

![Uwierzytelnianie federacyjne dla środowiska testowego Microsoft 365.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
Ta konfiguracja składa się z następujących elementów:
  
- Subskrypcja Microsoft 365 E5 wersji próbnej lub produkcyjnej.
    
- Uproszczony intranet organizacji połączony z Internetem, składający się z pięciu maszyn wirtualnych w podsieci sieci wirtualnej platformy Azure (DC1, APP1, CLIENT1, ADFS1 i PROXY1). Usługa Azure AD Połączenie działa w usłudze APP1, aby zsynchronizować listę kont w domenie Active Directory Domain Services z Microsoft 365. Serwer PROXY1 odbiera przychodzące żądania uwierzytelniania. Usługa ADFS1 weryfikuje poświadczenia przy użyciu kontrolera DC1 i wystawia tokeny zabezpieczające.
    
Konfigurowanie tego środowiska testowego obejmuje pięć faz:
- [Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Faza 2. Tworzenie serwera usług AD FS](#phase-2-create-the-ad-fs-server)
- [Faza 3. Tworzenie internetowego serwera proxy](#phase-3-create-the-web-proxy-server)
- [Faza 4. Tworzenie certyfikatu z podpisem własnym i konfigurowanie usług ADFS1 i PROXY1](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [Faza 5. Konfigurowanie Microsoft 365 dla tożsamości federacyjnej](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> Nie można skonfigurować tego środowiska testowego przy użyciu subskrypcji usługi Azure Trial.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365

Postępuj zgodnie z instrukcjami [synchronizacji skrótów haseł dla Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Wynikowe konfiguracje wyglądają następująco:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowym synchronizacji skrótów haseł.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
Ta konfiguracja składa się z następujących elementów:
  
- Microsoft 365 E5 wersji próbnej lub płatnych subskrypcji.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure. Usługa Azure AD Połączenie działa w usłudze APP1, aby okresowo synchronizować domenę Active Directory Domain Services TESTLAB (AD DS) z dzierżawą usługi Azure AD subskrypcji Microsoft 365.

## <a name="phase-2-create-the-ad-fs-server"></a>Faza 2. Tworzenie serwera usług AD FS

Serwer usług AD FS zapewnia uwierzytelnianie federacyjne między Microsoft 365 a kontami w domenie corp.contoso.com hostowanej na serwerze DC1.
  
Aby utworzyć maszynę wirtualną platformy Azure dla usług ADFS1, podaj nazwę subskrypcji oraz grupę zasobów i lokalizację platformy Azure dla konfiguracji podstawowej, a następnie uruchom te polecenia w wierszu polecenia Azure PowerShell na komputerze lokalnym.
  
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

Następnie użyj [Azure Portal](https://portal.azure.com), aby nawiązać połączenie z maszyną wirtualną usługi ADFS1 przy użyciu nazwy konta administratora lokalnego usługi ADFS1 i hasła, a następnie otwórz wiersz polecenia Windows PowerShell.
  
Aby sprawdzić rozpoznawanie nazw i komunikację sieciową między usługami ADFS1 i DC1, uruchom polecenie **ping dc1.corp.contoso.com** i sprawdź, czy istnieją cztery odpowiedzi.
  
Następnie dołącz maszynę wirtualną usługi ADFS1 do domeny CORP za pomocą tych poleceń w wierszu Windows PowerShell w usłudze ADFS1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Wynikowe konfiguracje wyglądają następująco:
  
![Serwer usług AD FS dodany do narzędzia DirSync dla środowiska testowego Microsoft 365.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>Faza 3. Tworzenie internetowego serwera proxy

Serwer PROXY1 zapewnia serwer proxy komunikatów uwierzytelniania między użytkownikami próbującymi uwierzytelnić się i usługą ADFS1.
  
Aby utworzyć maszynę wirtualną platformy Azure dla serwera PROXY1, podaj nazwę grupy zasobów i lokalizacji platformy Azure, a następnie uruchom te polecenia w wierszu polecenia Azure PowerShell na komputerze lokalnym.
  
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
> Serwer PROXY1 ma przypisany statyczny publiczny adres IP, ponieważ utworzysz publiczny rekord DNS, który na niego wskazuje i nie może ulec zmianie po ponownym uruchomieniu maszyny wirtualnej PROXY1.
  
Następnie dodaj regułę do sieciowej grupy zabezpieczeń podsieci CorpNet, aby zezwolić na niechciany ruch przychodzący z Internetu do prywatnego adresu IP serwera PROXY1 i portu TCP 443. Uruchom te polecenia w wierszu polecenia Azure PowerShell na komputerze lokalnym.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

Następnie użyj [Azure Portal](https://portal.azure.com), aby nawiązać połączenie z maszyną wirtualną proxy1 przy użyciu nazwy konta administratora lokalnego proxy1 i hasła, a następnie otwórz wiersz polecenia Windows PowerShell na serwerze PROXY1.
  
Aby sprawdzić rozpoznawanie nazw i komunikację siecią między serwerem PROXY1 i kontrolerem DC1, uruchom polecenie **ping dc1.corp.contoso.com** i sprawdź, czy istnieją cztery odpowiedzi.
  
Następnie dołącz maszynę wirtualną PROXY1 do domeny CORP za pomocą tych poleceń w wierszu Windows PowerShell na serwerze PROXY1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Wyświetl publiczny adres IP serwera PROXY1 za pomocą tych poleceń Azure PowerShell na komputerze lokalnym.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Następnie skontaktuj się z publicznym dostawcą DNS i utwórz nowy publiczny rekord DNS A dla **pliku fs.testlab.**\<*your DNS domain name*> jest rozpoznawana jako adres IP wyświetlany przez polecenie **Write-Host** . **Fs.testlab.**\<*your DNS domain name*> jest dalej nazywana  *nazwą FQDN usługi federacyjnej*.
  
Następnie użyj [Azure Portal](https://portal.azure.com), aby nawiązać połączenie z maszyną wirtualną DC1 przy użyciu poświadczeń CORPUser1\\, a następnie uruchom następujące polecenia w wierszu polecenia Windows PowerShell na poziomie administratora:
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
Te polecenia tworzą wewnętrzny rekord DNS A, aby maszyny wirtualne w sieci wirtualnej platformy Azure mogły rozpoznawać wewnętrzną nazwę FQDN usługi federacyjnej na prywatny adres IP usługi ADFS1.
  
Wynikowe konfiguracje wyglądają następująco:
  
![Serwer proxy aplikacji internetowej został dodany do narzędzia DirSync w celu Microsoft 365 środowiska testowego.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Faza 4. Tworzenie certyfikatu z podpisem własnym i konfigurowanie usług ADFS1 i PROXY1

W tej fazie utworzysz certyfikat cyfrowy z podpisem własnym dla nazwy FQDN usługi federacyjnej i skonfigurujesz usługi ADFS1 i PROXY1 jako farmę usług AD FS.
  
Najpierw użyj [Azure Portal](https://portal.azure.com), aby nawiązać połączenie z maszyną wirtualną DC1 przy użyciu poświadczeń CORPUser1\\, a następnie otwórz wiersz polecenia Windows PowerShell na poziomie administratora.
  
Następnie utwórz konto usługi AD FS za pomocą tego polecenia w wierszu polecenia Windows PowerShell na kontrolerze DC1:
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
Należy pamiętać, że to polecenie monituje o podanie hasła konta. Wybierz silne hasło i zarejestruj je w zabezpieczonej lokalizacji. Będzie ona potrzebna dla tej fazy i fazy 5.
  
Użyj [Azure Portal](https://portal.azure.com), aby nawiązać połączenie z maszyną wirtualną usługi ADFS1 przy użyciu poświadczeń CORPUser1\\. Otwórz wiersz polecenia Windows PowerShell na poziomie administratora w usłudze ADFS1, wypełnij nazwę FQDN usługi federacyjnej, a następnie uruchom następujące polecenia, aby utworzyć certyfikat z podpisem własnym:
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

Następnie wykonaj następujące kroki, aby zapisać nowy certyfikat z podpisem własnym jako plik.
  
1. Wybierz pozycję **Start**, **wprowadźmmc.exe**, a następnie naciśnij **klawisz Enter**.
    
2. Wybierz pozycję **PlikDodaj** > **/Usuń przystawkę**.
    
3. W **obszarze Dodawanie lub usuwanie przystawek** kliknij **dwukrotnie pozycję Certyfikaty** na liście dostępnych przystawek, wybierz pozycję **Konto komputera**, a następnie wybierz pozycję **Dalej**.
    
4. W **obszarze Wybierz komputer** wybierz pozycję **Zakończ**, a następnie wybierz przycisk **OK**.
    
5. W okienku drzewa otwórz pozycję **Certyfikaty (komputer lokalny) > Certyfikaty osobiste >**.
    
6. Wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy) certyfikat przy użyciu nazwy FQDN usługi federacyjnej, wybierz pozycję **Wszystkie zadania**, a następnie wybierz pozycję **Eksportuj**.
    
7. Na stronie **Witamy** wybierz pozycję **Dalej**.
    
8. Na stronie **Eksportowanie klucza prywatnego** wybierz pozycję **Tak**, a następnie wybierz pozycję **Dalej**.
    
9. Na stronie **Eksportowanie formatu pliku** wybierz pozycję **Eksportuj wszystkie właściwości rozszerzone**, a następnie wybierz pozycję **Dalej**.
    
10. Na stronie **Zabezpieczenia** wybierz pozycję **Hasło** i wprowadź hasło w polach **Hasło** i **Potwierdź hasło.**
    
11. Na stronie **Plik do eksportu** wybierz pozycję **Przeglądaj**.
    
12. Przejdź do folderu **C:\\Certs** , wprowadź **ciąg SSL** w **polu Nazwa pliku**, a następnie wybierz pozycję **Zapisz.**
    
13. Na stronie **Plik do eksportu** wybierz pozycję **Dalej**.
    
14. Na **stronie Kończenie pracy z Kreatorem eksportu certyfikatów** wybierz pozycję **Zakończ**. Po wyświetleniu monitu wybierz przycisk **OK**.
    
Następnie zainstaluj usługę AD FS za pomocą tego polecenia w wierszu polecenia Windows PowerShell w usłudze ADFS1:
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Poczekaj na ukończenie instalacji.
  
Następnie skonfiguruj usługę AD FS, wykonując następujące kroki:
  
1. Wybierz pozycję **Start**, a następnie wybierz ikonę **Menedżer serwera**.
    
2. W okienku drzewa Menedżer serwera wybierz pozycję **AD FS**.
    
3. Na pasku narzędzi u góry wybierz pomarańczowy symbol ostrzeżenia, a następnie wybierz pozycję **Konfiguruj usługę federacyjną na tym serwerze**.
    
4. Na stronie **Powitalnej** Kreatora konfiguracji Active Directory Federation Services wybierz pozycję **Dalej**.
    
5. Na **stronie Połączenie do usług AD DS** wybierz pozycję **Dalej**.
    
6. Na stronie **Określanie właściwości usługi** :
    
  - W polu **Certyfikat SSL** wybierz strzałkę w dół, a następnie wybierz certyfikat o nazwie nazwy FQDN usługi federacyjnej.
    
  - W polu **Nazwa wyświetlana usługi federacyjnej** wprowadź nazwę fikcyjnej organizacji.
    
  - Wybierz pozycję **Dalej**.
    
7. Na stronie **Określanie konta usługi** wybierz pozycję **Wybierz** jako **nazwę konta**.
    
8. W **obszarze Wybierz konto użytkownika lub usługi** wprowadź **ADFS-Service**, wybierz pozycję **Sprawdź nazwy**, a następnie wybierz przycisk **OK**.
    
9. W **polu Hasło konta** wprowadź hasło dla konta ADFS-Service, a następnie wybierz pozycję **Dalej**.
    
10. Na stronie **Określanie bazy danych konfiguracji** wybierz pozycję **Dalej**.
    
11. Na stronie **Przeglądanie opcji** wybierz pozycję **Dalej**.
    
12. Na stronie **Sprawdzanie wymagań wstępnych** wybierz pozycję **Konfiguruj**.

13. Na stronie **Wyniki** wybierz pozycję **Zamknij**.
    
14. Wybierz pozycję **Start**, wybierz ikonę zasilania, wybierz pozycję **Uruchom ponownie**, a następnie wybierz pozycję **Kontynuuj**.
    
Z [poziomu Azure Portal](https://portal.azure.com) połącz się z serwerem PROXY1 przy użyciu poświadczeń konta CORPUser1\\.
  
Następnie wykonaj następujące kroki, aby zainstalować certyfikat z podpisem własnym zarówno na **serwerze PROXY1, jak i w aplikacji APP1**.
  
1. Wybierz pozycję **Start**, **wprowadźmmc.exe**, a następnie naciśnij **klawisz Enter**.
    
2. Wybierz pozycję **Plik > dodaj/usuń przystawkę**.
    
3. W **obszarze Dodawanie lub usuwanie przystawek** kliknij **dwukrotnie pozycję Certyfikaty** na liście dostępnych przystawek, wybierz pozycję **Konto komputera**, a następnie wybierz pozycję **Dalej**.
    
4. W **obszarze Wybierz komputer** wybierz pozycję **Zakończ**, a następnie wybierz przycisk **OK**.
    
5. W okienku drzewa otwórz pozycję **Certyfikaty (komputer lokalny)** > **OsobisteCertyfikaty** > .
    
6. Wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy) **pozycję Osobiste**, wybierz pozycję **Wszystkie zadania**, a następnie wybierz pozycję **Importuj**.
    
7. Na stronie **Witamy** wybierz pozycję **Dalej**.
    
8. Na stronie **Plik do importu** wprowadź **\\\\adfs1certsssl.pfx\\\\**, a następnie wybierz przycisk **Dalej**.
    
9. Na stronie **Ochrona klucza prywatnego** wprowadź hasło certyfikatu w polu **Hasło**, a następnie wybierz pozycję **Dalej.**
    
10. Na stronie **Magazyn certyfikatów** wybierz pozycję **Dalej.**
    
11. Na stronie **Kończenie** wybierz pozycję **Zakończ**.
    
12. Na stronie **Magazyn certyfikatów** wybierz pozycję **Dalej**.
    
13. Po wyświetleniu monitu wybierz przycisk **OK**.
    
14. W okienku drzewa wybierz pozycję **Certyfikaty**.
    
15. Wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy) certyfikat, a następnie wybierz pozycję **Kopiuj**.
    
16. W okienku drzewa otwórz pozycję **Zaufane główne urzędy** >  **certyfikacjiCertyfikaty**.
    
17. Przenieś wskaźnik myszy poniżej listy zainstalowanych certyfikatów, wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy), a następnie wybierz pozycję **Wklej**.
    
Otwórz wiersz polecenia programu PowerShell na poziomie administratora i uruchom następujące polecenie:
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Poczekaj na ukończenie instalacji.
  
Wykonaj następujące kroki, aby skonfigurować usługę serwera proxy aplikacji internetowej do używania usług ADFS1 jako serwera federacyjnego:
  
1. Wybierz pozycję **Start**, a następnie wybierz pozycję **Menedżer serwera**.
    
2. W okienku drzewa wybierz pozycję **Dostęp zdalny**.
    
3. Na pasku narzędzi u góry wybierz pomarańczowy symbol ostrzeżenia, a następnie wybierz pozycję **Otwórz Kreatora serwer proxy aplikacji sieci Web**.
    
4. Na stronie **Powitalnej** Kreatora konfiguracji serwer proxy aplikacji sieci Web wybierz pozycję **Dalej**.
    
5. Na stronie **Serwer federacyjny** :
    
  - W polu **Nazwa usługi federacyjnej** wprowadź nazwę FQDN usługi federacyjnej.
    
  - W polu **Nazwa użytkownika** wprowadź **corpuser1\\**.
    
  - W polu **Hasło** wprowadź hasło dla konta Użytkownika1.
    
  - Wybierz pozycję **Dalej**.
    
6. Na stronie **Certyfikat serwera proxy usług AD FS** wybierz strzałkę w dół, wybierz certyfikat z nazwą FQDN usługi federacyjnej, a następnie wybierz przycisk **Dalej**.
    
7. Na stronie **Potwierdzenie** wybierz pozycję **Konfiguruj**.
    
8. Na stronie **Wyniki** wybierz pozycję **Zamknij**.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>Faza 5. Konfigurowanie Microsoft 365 dla tożsamości federacyjnej

Użyj [Azure Portal](https://portal.azure.com), aby nawiązać połączenie z maszyną wirtualną APP1 przy użyciu poświadczeń konta CORPUser1\\.
  
Wykonaj następujące kroki, aby skonfigurować usługę Azure AD Połączenie i subskrypcję Microsoft 365 na potrzeby uwierzytelniania federacyjnego:
  
1. Na pulpicie kliknij dwukrotnie **usługę Azure AD Połączenie**.
    
2. Na stronie **Witamy w usłudze Azure AD Połączenie** wybierz pozycję **Konfiguruj**.
    
3. Na stronie **Dodatkowe zadania** wybierz pozycję **Zmień logowanie użytkownika**, a następnie wybierz pozycję **Dalej**.
    
4. Na stronie **Połączenie do usługi Azure AD** wprowadź nazwę konta administratora globalnego i hasło, a następnie wybierz pozycję **Dalej**.
    
5. Na stronie **Logowanie użytkownika** wybierz pozycję **Federacja z usługami AD FS**, a następnie wybierz pozycję **Dalej**.
    
6. Na stronie **farmy usług AD FS** wybierz pozycję **Użyj istniejącej farmy usług AD FS**, wprowadź **ADFS1** w polu **Nazwa serwera** , a następnie wybierz przycisk **Dalej**.
    
7. Po wyświetleniu monitu o podanie poświadczeń serwera wprowadź poświadczenia konta CORPUser1\\, a następnie wybierz przycisk **OK**.
    
8. Na stronie Poświadczenia **administratora domeny** wprowadź **corpuser1\\** w polu **Nazwa użytkownika**, wprowadź hasło konta w polu **Hasło**, a następnie wybierz przycisk **Dalej**.
    
9. Na stronie **Konto usługi AD FS** wprowadź **corpadfs-service\\** w polu **Nazwa użytkownika domeny**, wprowadź hasło konta w polu **Hasło użytkownika domeny**, a następnie wybierz przycisk **Dalej**.
    
10. Na stronie **Domena usługi Azure AD** w obszarze **Domena** wybierz nazwę domeny, która została wcześniej utworzona i dodana do subskrypcji w fazie 1, a następnie wybierz pozycję **Dalej**.
    
11. Na stronie **Gotowe do skonfigurowania** wybierz pozycję **Konfiguruj**.
    
12. Na stronie **Instalacja ukończona** wybierz pozycję **Weryfikuj**.
    
    Powinny zostać wyświetlone komunikaty wskazujące, że zweryfikowano konfigurację intranetu i Internetu.
    
13. Na stronie **Instalacja ukończona** wybierz pozycję **Zakończ**.
    
Aby pokazać, że uwierzytelnianie federacyjne działa:
  
1. Otwórz nowe prywatne wystąpienie przeglądarki na komputerze lokalnym i przejdź do pozycji [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. Aby uzyskać poświadczenia logowania, wprowadź **user1@**\<*the domain created in Phase 1*>.
    
    Jeśli na przykład domena testowa jest **testlab.contoso.com**, należy wprowadzić wartość "user1@testlab.contoso.com". Naciśnij klawisz **Tab** lub zezwalaj Microsoft 365 na automatyczne przekierowanie.
    
    Teraz powinna zostać wyświetlona strona **Twoje połączenie nie jest prywatna** . Jest to widoczne, ponieważ zainstalowano certyfikat z podpisem własnym w usługach ADFS1, których komputer stacjonarny nie może zweryfikować. W produkcyjnym wdrożeniu uwierzytelniania federacyjnego należy użyć certyfikatu z zaufanego urzędu certyfikacji, a użytkownicy nie będą widzieć tej strony.
    
3. Na stronie **Twoje połączenie nie jest prywatne** wybierz pozycję **Zaawansowane**, a następnie wybierz pozycję **Przejdź do \<*your federation service FQDN*>**. 
    
4. Na stronie o nazwie fikcyjnej organizacji zaloguj się przy użyciu następujących elementów:
    
  - **CORP\\ User1** — nazwa
    
  - Hasło dla konta Użytkownika1
    
    Powinna zostać wyświetlona strona **główna Microsoft Office**.
    
Ta procedura pokazuje, że subskrypcja wersji próbnej jest federowana z domeną corp.contoso.com usług AD DS hostowaną na serwerze DC1. Oto podstawy procesu uwierzytelniania:
  
1. W przypadku korzystania z domeny federacyjnej utworzonej w fazie 1 w ramach nazwy konta logowania Microsoft 365 przekierowuje przeglądarkę do nazwy FQDN i serwera PROXY1 usługi federacyjnej.
    
2. Serwer PROXY1 wysyła do komputera lokalnego fikcyjną stronę logowania firmowego.
    
3. Po wysłaniu aplikacji CORPUser1\\ i hasła do serwera PROXY1 przekazuje je do usługi ADFS1.
    
4. Usługa ADFS1 weryfikuje wartość CORPUser1\\ i hasło przy użyciu kontrolera DC1 i wysyła do komputera lokalnego token zabezpieczający.
    
5. Komputer lokalny wysyła token zabezpieczający do Microsoft 365.
    
6. Microsoft 365 sprawdza, czy token zabezpieczający został utworzony przez usługę ADFS1 i zezwala na dostęp.
    
Subskrypcja wersji próbnej jest teraz skonfigurowana przy użyciu uwierzytelniania federacyjnego. Tego środowiska deweloperskiego/testowego można użyć w przypadku zaawansowanych scenariuszy uwierzytelniania.
  
## <a name="next-step"></a>Następny krok

Gdy wszystko będzie gotowe do wdrożenia gotowego do produkcji uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure, zobacz [Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
