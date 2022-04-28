---
title: Symulowana konfiguracja podstawowa przedsiębiorstwa dla Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Skorzystaj z tego przewodnika po laboratorium testowym, aby utworzyć symulowane środowisko testowe przedsiębiorstwa dla Microsoft 365 dla przedsiębiorstw.
ms.openlocfilehash: 9c52bf657e91ceca9ef6e43f20a523a57a7b5042
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078718"
---
# <a name="the-simulated-enterprise-base-configuration"></a>Symulowana konfiguracja podstawowa przedsiębiorstwa

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

W tym artykule opisano sposób tworzenia uproszczonego środowiska dla Microsoft 365 dla przedsiębiorstw, które obejmuje:

- Subskrypcja Microsoft 365 E5 wersji próbnej lub płatnej.
- Uproszczony intranet organizacji połączony z Internetem, składający się z trzech maszyn wirtualnych w sieci wirtualnej platformy Azure (DC1, APP1 i CLIENT1).
 
![Symulowana konfiguracja podstawowa przedsiębiorstwa.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

Tworzenie uproszczonego środowiska testowego obejmuje dwie fazy:
- [Faza 1. Tworzenie symulowanego intranetu](#phase-1-create-a-simulated-intranet)
- [Faza 2. Tworzenie subskrypcji Microsoft 365 E5](#phase-2-create-your-microsoft-365-e5-subscription)

Środowisko wynikowe umożliwia testowanie funkcji i funkcji [Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/microsoft-365/enterprise) przy użyciu dodatkowych [przewodników laboratorium testowego](m365-enterprise-test-lab-guides.md) lub samodzielnie.

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-create-a-simulated-intranet"></a>Faza 1. Tworzenie symulowanego intranetu

W tej fazie skompiluj symulowany intranet w usługach infrastruktury platformy Azure, który obejmuje kontroler domeny Active Directory Domain Services (AD DS), serwer aplikacji i komputer kliencki.

Te komputery będą używane w dodatkowych [Microsoft 365 dla przewodników laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md), aby skonfigurować i zademonstrować tożsamość hybrydową i inne możliwości.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>Metoda 1. Tworzenie symulowanego intranetu przy użyciu szablonu usługi Azure Resource Manager

W tej metodzie użyjesz szablonu usługi Azure Resource Manager do utworzenia symulowanego intranetu. Szablony usługi Azure Resource Manager zawierają wszystkie instrukcje dotyczące tworzenia infrastruktury sieciowej platformy Azure, maszyn wirtualnych i ich konfiguracji.

Przed wdrożeniem szablonu przeczytaj [stronę README szablonu](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) i przygotuj następujące informacje:

- Publiczna nazwa domeny DNS środowiska testowego (testlab.\<*your public domain*>). Wprowadź tę nazwę w polu **Nazwa domeny** na stronie **Wdrożenie niestandardowe** .
- Prefiks etykiety DNS dla adresów URL publicznych adresów IP maszyn wirtualnych. Musisz wprowadzić tę etykietę w polu **Prefiks etykiety DNS** na stronie **Wdrożenie niestandardowe** .

Po zapoznaniu się z instrukcjami wybierz pozycję **Wdróż na platformie Azure** na [stronie README szablonu](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) , aby rozpocząć pracę.

>[!Note]
>Symulowany intranet utworzony za pomocą szablonu usługi Azure Resource Manager wymaga płatnej subskrypcji platformy Azure.

Po ukończeniu szablonu konfiguracja wygląda następująco:

![Symulowany intranet w usługach infrastruktury platformy Azure.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>Metoda 2. Tworzenie symulowanego intranetu przy użyciu Azure PowerShell

W tej metodzie użyjesz Windows PowerShell i modułu Azure PowerShell, aby utworzyć infrastrukturę sieciową, maszyny wirtualne i ich konfigurację.

Użyj tej metody, jeśli chcesz uzyskać doświadczenie w tworzeniu elementów infrastruktury platformy Azure krok po kroku za pomocą programu PowerShell. Następnie możesz dostosować bloki poleceń programu PowerShell do własnego wdrożenia innych maszyn wirtualnych na platformie Azure.

#### <a name="step-1-create-dc1"></a>Krok 1. Tworzenie kontrolera DC1

W tym kroku utworzysz sieć wirtualną platformy Azure i dodasz dc1, maszynę wirtualną będącą kontrolerem domeny dla domeny usług AD DS.

Najpierw uruchom wiersz polecenia Windows PowerShell na komputerze lokalnym.
  
> [!NOTE]
> Poniższe zestawy poleceń używają najnowszej wersji Azure PowerShell. Zobacz [Wprowadzenie z poleceniami cmdlet Azure PowerShell](/powershell/azureps-cmdlets-docs/). 
  
Zaloguj się do konta platformy Azure za pomocą następującego polecenia.
  
```powershell
Connect-AzAccount
```

Pobierz nazwę subskrypcji przy użyciu następującego polecenia.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Ustaw subskrypcję platformy Azure. Zastąp wszystkie elementy cudzysłowu, w tym nawiasy kątowe ("<" i ">"), poprawną nazwą.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Następnie utwórz nową grupę zasobów dla symulowanego laboratorium testowego przedsiębiorstwa. Aby określić unikatową nazwę grupy zasobów, użyj tego polecenia, aby wyświetlić listę istniejących grup zasobów.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Utwórz nową grupę zasobów przy użyciu tych poleceń. Zastąp wszystkie elementy cudzysłowu, w tym nawiasy kątowe, prawidłowymi nazwami.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Następnie utwórz sieć wirtualną TestLab, która będzie hostować podsieć sieci firmowej symulowanego środowiska przedsiębiorstwa i chronić ją za pomocą sieciowej grupy zabezpieczeń. Podaj nazwę grupy zasobów i uruchom te polecenia w wierszu polecenia programu PowerShell na komputerze lokalnym.
  
```powershell
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Następnie utworzysz maszynę wirtualną DC1 i skonfigurujesz ją jako kontroler domeny dla **płyty testowej.**\<your public domain> Domena usług AD DS i serwer DNS dla maszyn wirtualnych sieci wirtualnej TestLab. Jeśli na przykład nazwa domeny publicznej to **<span>contoso.com</span>**, maszyna wirtualna DC1 będzie kontrolerem domeny dla domeny **<span>testlab.contoso.com</span>**.
  
Aby utworzyć maszynę wirtualną platformy Azure dla kontrolera DC1, podaj nazwę grupy zasobów i uruchom te polecenia w wierszu polecenia programu PowerShell na komputerze lokalnym.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Zostanie wyświetlony monit o podanie nazwy użytkownika i hasła dla konta administratora lokalnego na serwerze DC1. Użyj silnego hasła i zarejestruj zarówno nazwę, jak i hasło w bezpiecznej lokalizacji.
  
Następnie połącz się z maszyną wirtualną DC1:
  
1. W [Azure Portal](https://portal.azure.com) wybierz pozycję **Grupy zasobów** > <**_nazwę nowej grupy zasobów_*_> > _* DC1** >  **Połączenie**.
    
2. W otwartym okienku wybierz pozycję **Pobierz plik RDP**. Otwórz pobrany plik DC1.rdp, a następnie wybierz pozycję **Połączenie**.
    
3. Określ nazwę konta administratora lokalnego DC1:
    
   - W przypadku Windows 7:
    
     W oknie dialogowym **Zabezpieczenia Windows** wybierz pozycję **Użyj innego konta**. W **polu Nazwa użytkownika** wprowadź *nazwę konta administratora* **DC1local\\**<>.
    
   - W przypadku Windows 8 lub Windows 10:
    
     W oknie dialogowym **Zabezpieczenia Windows** wybierz pozycję **Więcej opcji**, a następnie wybierz pozycję **Użyj innego konta**. W **polu Nazwa użytkownika** wprowadź *nazwę konta administratora* **DC1local\\**<>.
    
4. W **polu Hasło** wprowadź hasło konta administratora lokalnego, a następnie wybierz przycisk **OK**.
    
5. Po wyświetleniu monitu wybierz pozycję **Tak**.
    
Następnie dodaj dodatkowy dysk danych jako nowy wolumin z literą dysku F: za pomocą tego polecenia na poziomie administratora Windows PowerShell wiersza polecenia na kontrolerze DC1.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Następnie skonfiguruj kontroler DOMENY DC1 jako kontroler domeny i serwer DNS dla **narzędzia testlab.**\<*your public domain*> Domeny. Określ nazwę domeny publicznej, usuń nawiasy kątowe, a następnie uruchom te polecenia w wierszu polecenia na poziomie administratora Windows PowerShell dc1.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
Należy określić hasło administratora trybu awaryjnego. Zapisz to hasło w bezpiecznej lokalizacji.
  
Należy pamiętać, że wykonanie tych poleceń może potrwać kilka minut.
  
Po ponownym uruchomieniu kontrolera DC1 ponownie połącz się z maszyną wirtualną DC1.
  
1. W [Azure Portal](https://portal.azure.com) wybierz pozycję **Grupy zasobów** > <*nazwę grupy zasobów*> > **DC1** >  **Połączenie**.
    
2. Uruchom pobrany plik DC1.rdp, a następnie wybierz pozycję **Połączenie**.
    
3. W **Zabezpieczenia Windows** wybierz pozycję **Użyj innego konta**. W **polu Nazwa użytkownika** wprowadź *nazwę konta administratora* **TESTLABlocal\\**<>.
    
4. W polu **Hasło** wprowadź hasło konta administratora lokalnego, a następnie wybierz przycisk **OK**.
    
5. Po wyświetleniu monitu wybierz pozycję **Tak**.
    
Następnie utwórz konto użytkownika w usłudze Active Directory, które będzie używane podczas logowania się do komputerów należących do domeny TESTLAB. Uruchom to polecenie w wierszu polecenia Windows PowerShell na poziomie administratora.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Należy pamiętać, że to polecenie monituje o podanie hasła konta Użytkownika1. To konto będzie używane do połączeń pulpitu zdalnego dla wszystkich komputerów należących do domeny TESTLAB, więc wybierz silne hasło. Zarejestruj hasło konta Użytkownika1 i zapisz je w zabezpieczonej lokalizacji.
  
Następnie skonfiguruj nowe konto Użytkownika1 jako domenę, przedsiębiorstwo i administrator schematu. Uruchom to polecenie w wierszu polecenia Windows PowerShell na poziomie administratora.
  
```powershell
$yourDomain="<your public domain>"
$domainName = "testlab."+$yourDomain
$userName="user1@" + $domainName
$userSID=(New-Object System.Security.Principal.NTAccount($userName)).Translate([System.Security.Principal.SecurityIdentifier]).Value
$groupNames=@("Domain Admins","Enterprise Admins","Schema Admins")
ForEach ($name in $groupNames) {Add-ADPrincipalGroupMembership -Identity $userSID -MemberOf (Get-ADGroup -Identity $name).SID.Value}
```

Zamknij sesję pulpitu zdalnego z kontrolerem DC1, a następnie ponownie połącz się przy użyciu konta TESTLABUser1\\.
  
Następnie, aby zezwolić na ruch dla narzędzia ping, uruchom to polecenie w wierszu polecenia Windows PowerShell na poziomie administratora.
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Bieżąca konfiguracja wygląda następująco:
  
![Krok 1 symulowanej konfiguracji podstawowej przedsiębiorstwa.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
#### <a name="step-2-configure-app1"></a>Krok 2. Konfigurowanie aplikacji APP1

W tym kroku utworzysz i skonfigurujesz aplikację APP1, która jest serwerem aplikacji, który początkowo udostępnia usługi udostępniania plików i sieci Web.

Aby utworzyć maszynę wirtualną platformy Azure dla aplikacji APP1, podaj nazwę grupy zasobów i uruchom te polecenia w wierszu polecenia na komputerze lokalnym.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Następnie połącz się z maszyną wirtualną APP1 przy użyciu nazwy konta administratora lokalnego app1 i hasła, a następnie otwórz wiersz polecenia Windows PowerShell.
  
Aby sprawdzić rozpoznawanie nazw i komunikację siecią między aplikacjami APP1 i DC1, uruchom **polecenie ping dc1.testlab.**\<*your public domain name*> polecenie i sprawdź, czy istnieją cztery odpowiedzi.
  
Następnie dołącz maszynę wirtualną APP1 do domeny TESTLAB za pomocą tych poleceń w wierszu Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Należy pamiętać, że po uruchomieniu polecenia **Add-Computer** należy podać poświadczenia konta domeny TESTLABUser1\\.
  
Po ponownym uruchomieniu aplikacji APP1 połącz się z nią przy użyciu konta TESTLABUser1\\, a następnie otwórz wiersz polecenia Windows PowerShell na poziomie administratora.
  
Następnie ustaw aplikację APP1 jako serwer internetowy za pomocą tego polecenia w wierszu polecenia Windows PowerShell na poziomie administratora w aplikacji APP1.
  
```powershell
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Następnie utwórz folder udostępniony i plik tekstowy w folderze w aplikacji APP1 za pomocą tych poleceń programu PowerShell.
  
```powershell
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess TESTLAB\User1
```

Bieżąca konfiguracja wygląda następująco:
  
![Krok 2 symulowanej konfiguracji podstawowej przedsiębiorstwa.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>Krok 3. Konfigurowanie klienta CLIENT1

W tym kroku utworzysz i skonfigurujesz klienta CLIENT1, który działa jako typowy laptop, tablet lub komputer stacjonarny w intranecie.

> [!NOTE]  
> Poniższy zestaw poleceń tworzy klienta CLIENT1 z systemem Windows Server 2016 Datacenter, który można wykonać dla wszystkich typów subskrypcji platformy Azure. Jeśli masz subskrypcję platformy Azure opartą na Visual Studio, możesz utworzyć Windows 10 z systemem CLIENT1 przy [użyciu Azure Portal](https://portal.azure.com).
  
Aby utworzyć maszynę wirtualną platformy Azure dla klienta CLIENT1, podaj nazwę grupy zasobów i uruchom te polecenia w wierszu polecenia na komputerze lokalnym.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Następnie połącz się z maszyną wirtualną CLIENT1 przy użyciu nazwy konta administratora lokalnego CLIENT1 i hasła, a następnie otwórz wiersz polecenia Windows PowerShell na poziomie administratora.
  
Aby sprawdzić rozpoznawanie nazw i komunikację siecią między client1 i DC1, uruchom **polecenie ping dc1.testlab.**\<*your public domain name*> polecenie w wierszu polecenia Windows PowerShell i sprawdź, czy istnieją cztery odpowiedzi.
  
Następnie dołącz maszynę wirtualną CLIENT1 do domeny TESTLAB za pomocą tych poleceń w wierszu Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Należy pamiętać, że po uruchomieniu polecenia **Dodaj komputer** należy podać poświadczenia konta domeny TESTLABUser1\\.
  
Po ponownym uruchomieniu klienta CLIENT1 połącz się z nim przy użyciu nazwy konta TESTLABUser1\\ i hasła, a następnie otwórz wiersz polecenia Windows PowerShell na poziomie administratora.
  
Następnie sprawdź, czy możesz uzyskać dostęp do zasobów sieci Web i udziału plików w aplikacji APP1 z poziomu klienta CLIENT1.
  
1. W Menedżer serwera w okienku drzewa wybierz pozycję **Serwer lokalny**.
    
2. W **obszarze Właściwości klienta CLIENT1** wybierz pozycję **Włączone** obok pozycji **Konfiguracja zwiększonych zabezpieczeń programu IE**.
    
3. W obszarze **Konfiguracja zwiększonych zabezpieczeń programu Internet Explorer** wybierz pozycję **Wyłączone** dla **administratorów** i **użytkowników**, a następnie wybierz przycisk **OK**.
    
4. Na ekranie Start wybierz pozycję **Internet Explorer**, a następnie wybierz przycisk **OK**.
    
5. Na pasku adresu wprowadź **ciąg http <span>://</span>app1.testab.**\<*your public domain name*>**/**, a następnie naciśnij **klawisz Enter**. Powinna zostać wyświetlona domyślna strona internetowa Internet Information Services dla aplikacji APP1.
    
6. Na pasku zadań pulpitu wybierz ikonę Eksplorator plików.
    
7. Na pasku adresu wprowadź **ciąg\\\\ app1Files\\**, a następnie naciśnij **klawisz Enter**. Powinno zostać wyświetlone okno folderu z zawartością folderu udostępnionego Pliki.
    
8. W oknie **Folder udostępniony Pliki** kliknij dwukrotnie plik **Example.txt** . Powinna zostać wyświetlona zawartość pliku Example.txt.
    
9. Zamknij **okna folderuexample.txt — Notatnik** i **folderu** udostępnionego Pliki.
    
Bieżąca konfiguracja wygląda następująco:
  
![Krok 3 symulowanej konfiguracji podstawowej przedsiębiorstwa.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>Faza 2. Tworzenie subskrypcji Microsoft 365 E5

W tej fazie utworzysz nową subskrypcję Microsoft 365 E5, która korzysta z nowej dzierżawy usługi Azure AD, która jest oddzielona od subskrypcji produkcyjnej. Można to zrobić na dwa sposoby:

- Użyj subskrypcji wersji próbnej Microsoft 365 E5.

  Subskrypcja wersji próbnej Microsoft 365 E5 wynosi 30 dni, co można łatwo przedłużyć do 60 dni. Po wygaśnięciu subskrypcji próbnej musisz przekonwertować ją na płatną subskrypcję lub utworzyć nową subskrypcję próbną. Tworzenie nowych subskrypcji wersji próbnych oznacza pozostawienie konfiguracji, która może obejmować złożone scenariusze.  

- Użyj oddzielnej subskrypcji produkcyjnej Microsoft 365 E5 z niewielką liczbą licencji.

  Jest to dodatkowy koszt, ale gwarantuje, że środowisko testowe pracy nie wygaśnie. Możesz w nim wypróbować funkcje, konfiguracje i scenariusze. W dłuższej perspektywie możesz użyć tego samego środowiska testowego do weryfikacji koncepcji, demonstracji dla elementów równorzędnych i zarządzania oraz tworzenia i testowania aplikacji. Jest to zalecana metoda.

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Tworzenie konta w celu Office 365 E5 subskrypcji wersji próbnej

Z Azure Portal połącz się z klientem CLIENT1 przy użyciu konta CORP\User1.

Aby utworzyć nową subskrypcję wersji próbnej Office 365 E5, wykonaj instrukcje opisane w [sekcji Faza 1](lightweight-base-configuration-microsoft-365-enterprise.md#phase-1-create-your-microsoft-365-e5-subscription) przewodnika laboratorium testowego uproszczonej konfiguracji podstawowej.

Aby skonfigurować nową subskrypcję wersji próbnej Office 365 E5, wykonaj instrukcje opisane w [sekcji Faza 2](lightweight-base-configuration-microsoft-365-enterprise.md#phase-2-configure-your-office-365-trial-subscription) przewodnika laboratorium testowego uproszczonej konfiguracji podstawowej.

#### <a name="using-an-office-365-e5-test-environment"></a>Korzystanie ze środowiska testowego Office 365 E5

Jeśli potrzebujesz tylko środowiska testowego Office 365, nie musisz czytać pozostałej części tego artykułu.

Aby uzyskać dodatkowe przewodniki laboratorium testowego, które dotyczą zarówno Microsoft 365, jak i Office 365, zobacz [przewodniki Microsoft 365 dla laboratoriów testowych w przedsiębiorstwie](m365-enterprise-test-lab-guides.md).

### <a name="add-a-microsoft-365-e5-trial-subscription"></a>Dodawanie subskrypcji wersji próbnej Microsoft 365 E5

Aby dodać subskrypcję wersji próbnej Microsoft 365 E5 i skonfigurować konta użytkowników z licencjami, wykonaj instrukcje opisane w [sekcji Faza 3](lightweight-base-configuration-microsoft-365-enterprise.md#phase-3-add-a-microsoft-365-e5-trial-subscription) przewodnika laboratorium testowego uproszczonej konfiguracji podstawowej.

  
## <a name="results"></a>Wyniki

Środowisko testowe ma teraz:
  
- Microsoft 365 E5 subskrypcji wersji próbnej.
- Wszystkie odpowiednie konta użytkowników mogą korzystać z Microsoft 365 E5.
- Symulowany i uproszczony intranet.
    
Ostateczna konfiguracja wygląda następująco:
  
![Faza 2 symulowanej konfiguracji podstawowej przedsiębiorstwa.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
Teraz możesz eksperymentować z dodatkowymi funkcjami [Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Następne kroki

Zapoznaj się z tymi dodatkowymi zestawami przewodników laboratorium testowego:
  
- [Tożsamości](m365-enterprise-test-lab-guides.md#identity)
- [Zarządzanie urządzeniami przenośnymi](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Ochrona informacji](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)