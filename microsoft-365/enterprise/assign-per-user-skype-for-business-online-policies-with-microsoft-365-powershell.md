---
title: Przypisywanie zasad usługi Skype dla firm online za pomocą programu PowerShell dla Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Podsumowanie: Użyj programu PowerShell do Microsoft 365, aby przypisać ustawienia komunikacji dla 1 użytkownika za pomocą Skype dla firm online.'
ms.openlocfilehash: c49d465ffe0a6f1379681be0ae4faaf9982b6ef0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985224"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>Przypisywanie zasad usługi Skype dla firm online za pomocą programu PowerShell dla Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Program PowerShell dla Microsoft 365 to skuteczny sposób przypisywania ustawień komunikacji dla 1 użytkownika za pomocą Skype dla firm online.
  
## <a name="prepare-to-run-the-powershell-commands"></a>Przygotowywanie do uruchamiania poleceń programu PowerShell

Skorzystaj z tych instrukcji, aby skonfigurować uruchamianie poleceń (pomiń czynności, które zostały już wykonane):
  
  > [!Note]
   > Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams PowerShell. Jeśli używasz najnowszej wersji programu Teams PowerShell, nie musisz instalować do łącznika usługi Skype dla firm Online.

1. Zainstaluj moduł [Teams PowerShell](/microsoftteams/teams-powershell-install).
    
2. Otwórz wiersz Windows PowerShell i uruchom następujące polecenia: 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   Po wyświetleniu monitu wprowadź nazwę Skype dla firm administratora usługi Online oraz hasło.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Aktualizowanie ustawień komunikacji zewnętrznej dla konta użytkownika

Załóżmy, że chcesz zmienić ustawienia komunikacji zewnętrznej na koncie użytkownika. Na przykład chcesz zezwolić Alexowi na komunikowanie się z użytkownikami federacyjną (wartość EnableFederationAccess jest równa True), ale nie z użytkownikami usługi Windows Live (EnablePublicCloudAccess równa się False). Aby to zrobić, musisz wykonać dwie czynności:
  
1. Znajdź zasady dostępu zewnętrznego, które spełniają nasze kryteria.
    
2. Przypisz te zasady dostępu zewnętrznego do Alexy.
    
Jak ustalić, do jakich zasad dostępu zewnętrznego ma przypisać Alexę? Poniższe polecenie zwraca wszystkie zasady dostępu zewnętrznego, w których dla ustawienia EnableFederationAccess jest ustawiona wartość True , a dla ustawienia EnablePublicCloudAccess jest ustawiona wartość False:
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Jeśli nie utworzono żadnych niestandardowych wystąpień właściwości ExternalAccessPolicy, to polecenie zwraca jedną zasady spełniające nasze kryteria (FederationOnly). Oto przykład:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

Gdy już wiesz, które zasady przypisać do Alexy, możemy je przypisać za pomocą polecenia cmdlet [Grant-CsExternalAccessPolicy](/powershell/module/skype/Get-CsExternalAccessPolicy) . Oto przykład:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Przypisywanie zasad jest dość proste: wystarczy określić Tożsamość użytkownika i nazwę zasad, które mają zostać przypisane. 
  
A jeśli chodzi o zasady i przypisania zasad, nie musisz ograniczać się do pracy z kontami użytkowników na raz. Załóżmy na przykład, że potrzebna jest lista wszystkich użytkowników, którzy mogą komunikować się z partnerami federacyjną i Windows użytkownikami na żywo. Wiemy już, że tym użytkownikom przypisano zasady dostępu zewnętrznego FederationAndPICDefault. Ponieważ wiemy o tym, możesz wyświetlić listę wszystkich tych użytkowników, uruchamiając jedno proste polecenie. Oto polecenie:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Innymi słowy pokaż nam wszystkich użytkowników, dla których właściwość ExternalAccessPolicy ma ustawioną wartość FederationAndPICDefault. (Aby ograniczyć ilość informacji wyświetlanych na ekranie, użyj polecenia cmdlet Select-Object, aby wyświetlić tylko nazwę wyświetlaną każdego użytkownika). 
  
Aby skonfigurować wszystkie konta użytkowników do używania tych samych zasad, użyj tego polecenia:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

To polecenie używa programu Get-CsOnlineUser w celu zwrócenia zbioru wszystkich użytkowników, dla których włączono obsługę programu Lync, a następnie wysyła wszystkie te informacje do firmy Grant-CsExternalAccessPolicy, która przypisuje zasady FederationAndPICDefault wszystkim użytkownikom w zbiorze.
  
Załóżmy na przykład, że wcześniej przypisano zasady Alex FederationAndPICDefault, a teraz zmienisz zdanie i chcesz, aby nim zarządzały globalne zasady dostępu zewnętrznego. Nie można jawnie przypisywać żadnych zasad globalnych. Jeśli nie przypisano żadnych zasad dla danego użytkownika, zasady globalne są używane dla danego użytkownika. Dlatego, jeśli chcemy, aby Alexą zarządzały zasady globalne, musisz usunąć przypisanie  do niego wszelkich wcześniej przypisanych zasad dla użytkowników. Oto przykładowe polecenie:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

To polecenie ustawia nazwę zasad dostępu zewnętrznego przypisanych do Alexa na wartość null ($Null). Wartość Null oznacza "nic". Innymi słowy, do Alexy nie są przypisywane żadne zasady dostępu zewnętrznego. Jeśli do użytkownika nie przypisano żadnych zasad dostępu zewnętrznego, wówczas ten użytkownik jest zarządzany przez zasady globalne.

## <a name="managing-large-numbers-of-users"></a>Zarządzanie dużą liczba użytkowników

Aby zarządzać dużą liczbę użytkowników (1000 lub więcej), należy wsadować polecenia za pośrednictwem bloku skryptu za pomocą polecenia cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .  W poprzednich przykładach po wykonaniu każdego polecenia cmdlet musi ono skonfigurować połączenie, a następnie poczekać na wynik, zanim zostanie ono ponownie wysłanie.  W przypadku używania bloku skryptu umożliwia to zdalne wykonywanie polecenia cmdlet, a po wykonaniu tych operacji — wysyłanie danych z powrotem.

```powershell
$s = Get-PSSession | Where-Object { ($.ComputerName -like '*.online.lync.com' -or $.Computername -eq 'api.interfaces.records.teams.microsoft.com') -and $.State -eq 'Opened' -and $.Availability -eq 'Available' }

$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

Spowoduje to znalezienie 500 użytkowników jednocześnie, którzy nie mają zasad klienta. Przyznają im zasady klienta "ClientPolicyNoIMURL" i zasady dostępu zewnętrznego "FederationAndPicDefault". Wyniki są grupowane w grupy po 50, a każda partia po 50 jest następnie wysyłana do komputera zdalnego.
  
## <a name="see-also"></a>Zobacz też

[Zarządzanie usługą Skype dla firm Online za pomocą programu PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
