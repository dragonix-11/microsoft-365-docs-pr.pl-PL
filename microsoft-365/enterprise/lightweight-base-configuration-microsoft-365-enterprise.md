---
title: Konfiguracja podstawowa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/14/2019
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
- admindeeplinkMAC
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Skorzystaj z tego przewodnika laboratorium testowego, aby utworzyć uproszczone środowisko testowe do Microsoft 365 dla przedsiębiorstw.
ms.openlocfilehash: 742fc93b64d2e3c1d858931eb7dbc591ebcd8e9d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977634"
---
# <a name="the-lightweight-base-configuration"></a>Konfiguracja podstawowa (podstawowa)

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

W tym artykule opisano sposób tworzenia środowiska uproszczonego z subskrypcją usługi Microsoft 365 E5 i komputerem z systemem Windows 10 Enterprise.

![Uproszczone środowisko testowe platformy Microsoft 3656 Enterprise testowe.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Tworzenie uproszczonego środowiska testowego składa się z pięciu etapów:
- [Etap 1. Tworzenie subskrypcji Microsoft 365 E5 firmowej](#phase-1-create-your-microsoft-365-e5-subscription)
- [Etap 2. Konfigurowanie subskrypcji Office 365 próbnej](#phase-2-configure-your-office-365-trial-subscription)
- [Etap 3. Dodawanie subskrypcji Microsoft 365 E5 próbnej](#phase-3-add-a-microsoft-365-e5-trial-subscription)
- [Etap 4. Tworzenie Windows 10 Enterprise komputera](#phase-4-create-a-windows-10-enterprise-computer)
- [Etap 5. Dołączanie komputera Windows 10 do usługi Azure AD](#phase-5-join-your-windows-10-computer-to-azure-ad)

Skorzystaj z wynikowego środowiska, aby przetestować funkcje funkcji aplikacji dla Microsoft 365 [przedsiębiorstwa](https://www.microsoft.com/microsoft-365/enterprise).

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium Microsoft 365 dla przedsiębiorstw testowych, zobacz artykuł Microsoft 365 — przewodnik laboratorium testowego [w przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).

>[!NOTE]
>Warto wydrukować ten artykuł, aby zarejestrować konkretne informacje potrzebne w tym środowisku w ciągu 30 dni od Office 365 wersji próbnej. Możesz łatwo przedłużyć abonament na kolejne 30 dni. W przypadku stałego środowiska testowego utwórz nową płatną subskrypcję z osobną dzierżawą usługi Azure AD i niewielką liczbą licencji.

## <a name="phase-1-create-your-microsoft-365-e5-subscription"></a>Etap 1. Tworzenie subskrypcji Microsoft 365 E5 firmowej

Zaczynamy od subskrypcji Microsoft 365 E5 próbnej, a następnie Microsoft 365 E5 subskrypcję wersji próbnej.

>[!NOTE]
>Zalecamy utworzenie subskrypcji próbnej usługi Office 365 tak, aby środowisko testowe było osobną dzierżawą usługi Azure AD od wszystkich płatnych subskrypcji, które obecnie posiadasz. Dzięki temu wyciągowi można dodawać i usuwać użytkowników oraz grupy w dzierżawie testowej bez wpływu na subskrypcje produkcyjne.

Aby rozpocząć Microsoft 365 E5 wersji próbnej, musisz najpierw fikcyjną nazwę firmy i nowe konto Microsoft.
  
1. Jako nazwy firmy zalecamy używanie wariantu nazwy firmy Contoso, który jest fikcyjną firmą używaną w zawartości przykładowej firmy Microsoft, ale nie jest ona wymagana. Aby nagrać swoją fikcyjną nazwę firmy, kliknij tutaj: ![Liniowy.](../media/Common-Images/TableLine.png)
    
2. Aby utworzyć nowe konto Microsoft, przejdź do [https://outlook.com](https://outlook.com) nowego konta e-mail i utwórz je przy użyciu nowego konta e-mail oraz adresu. Będziesz używać tego konta do rejestracji w celu Office 365.
    
    - Tutaj możesz zarejestrować imię i nazwisko nowego konta: ![Liniowy.](../media/Common-Images/TableLine.png)
    
    - Tutaj możesz zarejestrować nowy adres e-mail: ![Liniowy.](../media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Zarejestruj się w celu subskryb Office 365 E5 próbnej

1. W przeglądarce przejdź do .[https://aka.ms/e5trial](https://aka.ms/e5trial)
    
2. W kroku 1 strony **Dziękujemy za wybranie Office 365 E5** wprowadź adres nowego konta e-mail.
3. W kroku 2 procesu subskrypcji trail wprowadź wymagane informacje, a następnie przekonwertuj tę weryfikację.
4. W kroku 3 wprowadź nazwę organizacji, a następnie nazwę konta, która będzie administratorem globalnym subskrypcji.
5. W kroku 4 zarejestruj tutaj stronę logowania (wybierz i skopiuj): ![Liniowy.](../media/Common-Images/TableLine.png)
6. Tutaj możesz zarejestrować identyfikator użytkownika: ![Wiersz](../media/Common-Images/TableLine.png). onmicrosoft.com  
   Zanotuj hasło wprowadzone w bezpiecznym miejscu.
   Ta wartość będzie określana jako nazwa administratora **globalnego**.
7. Wybierz **pozycję Przejdź do konfiguracji**.
8. W Office 365 E5 wybierz pozycję Kontynuuj korzystanie z usługi ***organization.onmicrosoft.com*** do korzystania z poczty e-mail i logowania, a następnie wybierz pozycję **Zakończ i kontynuuj później**.

Powinien zostać wyświetlony centrum administracyjne platformy Microsoft 365.
    
## <a name="phase-2-configure-your-office-365-trial-subscription"></a>Etap 2. Konfigurowanie subskrypcji Office 365 próbnej

Na tym etapie skonfigurujesz subskrypcję z dodatkowymi użytkownikami i przypiszesz im Office 365 E5 licencji.
  
Aby nawiązać połączenie z subskrypcją za pomocą Azure Active Directory PowerShell dla systemu Graph na komputerze, skorzystaj z instrukcji w Połączenie, aby Microsoft 365 [za pomocą programu PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
    
W **oknie Windows PowerShell żądanie** poświadczeń wprowadź nazwę administratora globalnego (na *przykład jdoe@contosotoycompany.onmicrosoft.com*) i hasło.
  
Wpisz nazwę organizacji (na przykład *contosotoycompany), dwukierunkowy* kod kraju swojej lokalizacji i hasło do wspólnego konta, a następnie uruchom następujące polecenia z monitu programu PowerShell:

```powershell
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License

for($i=2;$i -le 4; $i++) {
    $userUPN= "user$($i)@$($orgName).onmicrosoft.com"
    New-AzureADUser -DisplayName "User $($i)" -GivenName User -SurName $i -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user$($i)"
    $userObjectID = (Get-AzureADUser -SearchString $userupn).ObjectID
    Set-AzureADUserLicense -ObjectId $userObjectID -AssignedLicenses $LicensesToAssign
}
```
> [!NOTE]
> Użycie wspólnego hasła w tym miejscu ułatwia automatyzację i konfigurację środowiska testowego. Oczywiście jest to zdecydowanie zalecane w przypadku subskrypcji produkcyjnych. 

### <a name="record-key-information-for-future-reference"></a>Rejestrowanie kluczowych informacji do przyszłego odwołania

Jeśli te wartości nie zostały jeszcze zarejestrowane, zanotuj je teraz:
  
- Nazwa administratora globalnego: ![Liniowy.](../media/Common-Images/TableLine.png)onmicrosoft.com (od kroku 6 fazy 1)
    
    Ponadto zanotuj hasło do tego konta w bezpiecznym miejscu.
    
- Nazwa organizacji z subskrypcją wersji próbnej: ![Liniowy.](../media/Common-Images/TableLine.png) (od kroku 4. fazy 1)
    
- Aby wyświetlić listę kont dla użytkowników User 2, User 3, User 4 i User 5, uruchom następujące polecenie z modułu Windows Azure Active Directory dla Windows PowerShell monitu:
    
  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Tutaj możesz zarejestrować nazwy kont:
    
  - Nazwa konta użytkownika 2: użytkownik2 @![Liniowy.](../media/Common-Images/TableLine.png)onmicrosoft.com
    
  - Nazwa konta użytkownika 3: użytkownik3 @![Liniowy.](../media/Common-Images/TableLine.png)onmicrosoft.com
    
  - Nazwa konta użytkownika 4: użytkownik4 @![Liniowy.](../media/Common-Images/TableLine.png)onmicrosoft.com
    
  - Nazwa konta użytkownika 5: user5 @![Liniowy.](../media/Common-Images/TableLine.png)onmicrosoft.com
    
    Ponadto zanotuj hasło wspólne dla tych kont w bezpiecznym miejscu.
   
### <a name="using-an-office-365-test-environment"></a>Używanie Office 365 testowego

Jeśli potrzebujesz tylko Office 365 testowego, nie musisz czytać pozostałej części tego artykułu.

Aby uzyskać dodatkowe przewodniki laboratorium testowego dotyczące produktów Office 365 i Microsoft 365, zobacz Microsoft 365 laboratorium testowego [dla przedsiębiorstw](m365-enterprise-test-lab-guides.md).
  
## <a name="phase-3-add-a-microsoft-365-e5-trial-subscription"></a>Etap 3. Dodawanie subskrypcji Microsoft 365 E5 próbnej

W tym etapie załóższ konto subskrypcji próbnej usługi Microsoft 365 E5 i dodajesz ją do tej samej organizacji, w Office 365 E5 próbnej.
  
Najpierw dodaj subskrypcję wersji Microsoft 365 E5 próbnej i przypisz nową licencję usługi Microsoft 365 do konta administratora globalnego.
  
1. W oknie prywatnym przeglądarki internetowej użyj poświadczeń administratora globalnego, aby zalogować się w oknie centrum administracyjne platformy Microsoft 365 stronie [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. Na stronie **centrum administracyjne platformy Microsoft 365** nawigacji po lewej stronie wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**BillingPurchase**</a> >  services.
    
3. Na stronie **Zakup usług** wybierz **pozycję Microsoft 365 E5,** a następnie wybierz pozycję **Uzyskaj bezpłatną wersję próbną**.

4. Na stronie **Microsoft 365 E5** próbnych wybierz opcję odbierania wiadomości SMS lub połączenia telefonicznego, wprowadź swój numer telefonu, a następnie wybierz pozycję Wiadomość **SMS** lub **Zadzwoń do mnie**. Przekonwertuj tę weryfikację.

5. Na stronie **Potwierdzanie zamówienia** wybierz pozycję **Wypróbuj teraz**.

6. Na stronie **Potwierdzenie zamówienia** wybierz pozycję **Kontynuuj**.

7. W centrum administracyjne platformy Microsoft 365 wybierz pozycję **Użytkownicy** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktywuj użytkowników**</a>.

8. W **ustawieniach Aktywni** użytkownicy wybierz konto administratora.

9. Wybierz **pozycję Licencje i aplikacje**.

10. Wyłącz licencję dla Office 365 Enterprise E5 i włącz licencję dla Microsoft 365 E5.

11. Wybierz **pozycję Zapisz zmiany**, a następnie zamknij okienko informacji o koncie użytkownika.

Następnie powtórz kroki od 8 do 11 z poprzedniej procedury dla wszystkich innych kont (Użytkownik 2, Użytkownik 3, Użytkownik 4 i Użytkownik 5).
  
> [!NOTE]
> Długość subskrypcji usługi Microsoft 365 E5 próbnej wynosi 30 dni. W przypadku stałego środowiska testowego przekonwertuj tę subskrypcję wersji próbnej na płatną subskrypcję z niewielką liczbą licencji.
  
Twoje środowisko testowe oferuje teraz:
  
- Subskrypcja Microsoft 365 E5 próbna.
- Wszystkie odpowiednie konta użytkowników (tylko administrator globalny lub wszystkie pięć kont użytkowników) mogą korzystać z Microsoft 365 E5.
    
Wynikowa konfiguracja, która dodaje Microsoft 365 E5, wygląda tak:
  
![Etap 3 środowiska testowego platformy Microsoft 365 Enterprise 6.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase2.png)
  
## <a name="phase-4-create-a-windows-10-enterprise-computer"></a>Etap 4. Tworzenie Windows 10 Enterprise komputera

W tej fazie utworzysz autonomiczny komputer z uruchomionym Windows 10 Enterprise jako komputer fizyczny, maszynę wirtualną lub maszynę wirtualną platformy Azure.
  
### <a name="physical-computer"></a>Komputer fizyczny

Na komputerze osobistym zainstaluj program Windows 10 Enterprise. Możesz pobrać wersję próbną Windows 10 Enterprise [tutaj](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine"></a>Maszynę wirtualną

Użyj wybranego hipervisora, aby utworzyć maszynę wirtualną, a następnie Windows 10 Enterprise na nim. Możesz pobrać wersję próbną Windows 10 Enterprise [tutaj](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine-in-azure"></a>Maszyny wirtualne na platformie Azure

Aby utworzyć Windows 10 wirtualną w programie ***Microsoft Azure, musisz*** mieć subskrypcję opartą na Visual Studio, która ma dostęp do obrazu dla Windows 10 Enterprise. Inne typy subskrypcji platformy Azure, takie jak subskrypcje wersji próbnej i płatne, nie mają dostępu do tego obrazu. Aby uzyskać najnowsze informacje, zobacz Używanie [Windows na platformie Azure w scenariuszach deweloper/test.](/azure/virtual-machines/windows/client-images)
  
> [!NOTE]
> W poniższych zestawach poleceń jest dostępna najnowsza wersja Azure PowerShell. Zobacz [Wprowadzenie do Azure PowerShell cmdlet](/powershell/azureps-cmdlets-docs/). Te zestawy poleceń Windows 10 Enterprise maszynę wirtualną o nazwie WIN10 i całą jej wymaganą infrastrukturę, w tym grupę zasobów, konto magazynu i sieć wirtualną. Jeśli znasz już usługi infrastruktury platformy Azure, dostosuj te instrukcje do posiadanej obecnie wdrożonej infrastruktury.
  
Najpierw uruchom monit programu Microsoft PowerShell.
  
Zaloguj się do swojego konta Azure za pomocą tego polecenia.
  
```powershell
Connect-AzAccount
```

Uzyskaj nazwę subskrypcji za pomocą tego polecenia.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Ustaw subskrypcję platformy Azure. Zastąp wszystkie znaki cudzysłowu, łącznie ze \< and > znakami, poprawną nazwą.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Następnie utwórz nową grupę zasobów. Aby określić unikatową nazwę grupy zasobów, użyj tego polecenia, aby wyświetlić listę istniejących grup zasobów.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Za pomocą tych poleceń utwórz nową grupę zasobów. Zamień wszystkie znaki cudzysłowu, łącznie ze \< and > znakami, na poprawne nazwy.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Następnie utwórz nową sieć wirtualną i maszynę wirtualną WIN10, która będzie używać tych poleceń. Gdy zostanie wyświetlony monit, podaj nazwę i hasło konta administratora lokalnego dla systemu WIN10 i przechowuj je w bezpiecznym miejscu.
  
```powershell
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
$pip=New-AzPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName WIN10 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-5-join-your-windows-10-computer-to-azure-ad"></a>Etap 5. Dołączanie komputera Windows 10 do usługi Azure AD

Po utworzeniu fizycznej lub wirtualnej Windows 10 Enterprise, zaloguj się przy użyciu konta administratora lokalnego.
  
> [!NOTE]
> W przypadku maszyny wirtualnej na platformie Azure skorzystaj z  [tych](/azure/virtual-machines/windows/connect-logon) instrukcji, aby się z nim połączyć.
  
Następnie dołącz komputer WIN10 do dzierżawy usługi Azure AD swojej Microsoft 365 E5 subskrypcji usługi.
  
1. Na komputerze z systemem WIN10 wybierz pozycję Rozpocznij > Ustawienia > **Konta > uzyskaj** dostęp do konta służbowego > Połączenie.
    
2. W **oknie dialogowym Konfigurowanie konta służbowego** wybierz pozycję **Dołącz do tego urządzenia, aby Azure Active Directory**.
    
3. Na **koncie służbowym wprowadź** nazwę konta administratora globalnego subskrypcji usługi Microsoft 365 E5, a następnie wybierz pozycję **Dalej**.
    
4. W **polecej** Wprowadź hasło wprowadź hasło do konta administratora globalnego, a następnie wybierz **pozycję Zaloguj.**
    
5. Po wyświetleniu monitu o upewnienie się, że jest to Twoja organizacja, **wybierz pozycję Dołącz**, a następnie wybierz pozycję **Gotowe**.
    
6. Zamknij okno ustawień.
    
Następnie zainstaluj Aplikacje Microsoft 365 dla przedsiębiorstw na komputerze z systemem WIN10:
  
1. Otwórz przeglądarkę Microsoft Edge i zaloguj się do witryny [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) poświadczeniami administratora globalnego.
    
2. Na karcie **Microsoft Office Narzędzia główne** wybierz pozycję **Zainstaluj Office**.
    
3. Po wyświetleniu monitu z pytaniem, co należy zrobić, wybierz **pozycję Uruchom**, a następnie wybierz pozycję **Tak w** przypadku kontroli **konta użytkownika**.
    
4. Poczekaj, Office zakończyć instalację. Gdy zobaczysz **pozycję Wszystko jest już ustawione,** wybierz pozycję **Zamknij** dwa razy.
    
Środowisko wynikowe wygląda następująco:

![Etap 5 środowiska testowego platformy Microsoft 3656 Enterprise testowego.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Dotyczy to również komputera z systemem WIN10, który:

- Dołączyć do dzierżawy usługi Azure AD Twojej Microsoft 365 E5 subskrypcji usługi.
- Zarejestrowane jako urządzenie usługi Azure AD w programie Microsoft Intune (EMS).
- Aplikacje Microsoft 365 dla przedsiębiorstw zainstalowane.
  
Możesz teraz poeksperymentować z dodatkowymi funkcjami usługi [Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Następne kroki

Zapoznaj się z tymi dodatkowymi zestawami przewodników laboratorium testowego:
  
- [Tożsamości](m365-enterprise-test-lab-guides.md#identity)
- [Zarządzanie urządzeniami przenośnymi](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Ochrona informacji](m365-enterprise-test-lab-guides.md#information-protection)
   

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)
