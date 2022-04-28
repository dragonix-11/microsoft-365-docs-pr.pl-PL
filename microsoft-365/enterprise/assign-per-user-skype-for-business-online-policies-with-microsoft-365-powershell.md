---
title: Przypisywanie zasad Skype dla firm Online dla poszczególnych użytkowników za pomocą programu PowerShell dla Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Używanie programu PowerShell do Microsoft 365 w celu przypisania ustawień komunikacji między użytkownikami przy użyciu zasad usługi Skype dla firm Online.'
ms.openlocfilehash: 70120f6d296f958f44906a3526a7dcaa36b7eb04
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091396"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>Przypisywanie zasad Skype dla firm Online dla poszczególnych użytkowników za pomocą programu PowerShell dla Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Korzystanie z programu PowerShell dla Microsoft 365 jest skutecznym sposobem przypisywania ustawień komunikacji na użytkownika przy użyciu zasad usługi Skype dla firm Online.
  
## <a name="prepare-to-run-the-powershell-commands"></a>Przygotowanie do uruchomienia poleceń programu PowerShell

Skorzystaj z tych instrukcji, aby skonfigurować uruchamianie poleceń (pomiń kroki, które zostały już wykonane):
  
  > [!Note]
   > Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams programu PowerShell. Jeśli używasz najnowszej Teams publicznej wersji programu PowerShell, nie musisz instalować łącznika usługi Skype dla firm Online.

1. Zainstaluj [moduł Teams programu PowerShell](/microsoftteams/teams-powershell-install).
    
2. Otwórz wiersz polecenia Windows PowerShell i uruchom następujące polecenia: 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   Po wyświetleniu monitu wprowadź nazwę i hasło konta administratora usługi Skype dla firm Online.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Aktualizowanie ustawień komunikacji zewnętrznej dla konta użytkownika

Załóżmy, że chcesz zmienić ustawienia komunikacji zewnętrznej na koncie użytkownika. Na przykład chcesz zezwolić Alexowi na komunikowanie się z użytkownikami federacyjnymi (enableFederationAccess jest równa True), ale nie z użytkownikami Windows Live (EnablePublicCloudAccess to False). W tym celu należy wykonać dwie czynności:
  
1. Znajdź zasady dostępu zewnętrznego spełniające nasze kryteria.
    
2. Przypisz te zasady dostępu zewnętrznego do usługi Alex.
    
Jak określić, które zasady dostępu zewnętrznego mają zostać przypisane alexowi? Następujące polecenie zwraca wszystkie zasady dostępu zewnętrznego, w których właściwość EnableFederationAccess jest ustawiona na wartość True, a wartość EnablePublicCloudAccess ma wartość False:
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Jeśli nie utworzono żadnych niestandardowych wystąpień funkcji ExternalAccessPolicy, to polecenie zwraca jedną zasadę spełniającą nasze kryteria (FederationOnly). Oto przykład:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

Teraz, gdy już wiesz, które zasady należy przypisać alexowi, możemy przypisać te zasady za pomocą polecenia cmdlet [Grant-CsExternalAccessPolicy](/powershell/module/skype/Get-CsExternalAccessPolicy) . Oto przykład:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Przypisywanie zasad jest dość proste: wystarczy określić tożsamość użytkownika i nazwę zasad, które mają zostać przypisane. 
  
A jeśli chodzi o zasady i przypisania zasad, nie ograniczasz się do pracy z kontami użytkowników pojedynczo. Załóżmy na przykład, że potrzebujesz listy wszystkich użytkowników, którzy mogą komunikować się z partnerami federacyjnymi i z użytkownikami Windows Live. Wiemy już, że do tych użytkowników przypisano zasady dostępu użytkowników zewnętrznych FederationAndPICDefault. Ponieważ wiemy o tym, możesz wyświetlić listę wszystkich tych użytkowników, uruchamiając jedno proste polecenie. Oto polecenie:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Innymi słowy, pokaż wszystkim użytkownikom, dla których właściwość ExternalAccessPolicy jest ustawiona na wartość FederationAndPICDefault. (Aby ograniczyć ilość informacji wyświetlanych na ekranie, użyj polecenia cmdlet Select-Object, aby wyświetlić tylko nazwę wyświetlaną każdego użytkownika). 
  
Aby skonfigurować wszystkie nasze konta użytkowników do korzystania z tych samych zasad, użyj tego polecenia:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

To polecenie używa Get-CsOnlineUser do zwrócenia kolekcji wszystkich użytkowników, którzy włączyli program Lync, a następnie wysyła wszystkie te informacje do polecenia Grant-CsExternalAccessPolicy, która przypisuje zasady FederationAndPICDefault do każdego użytkownika w kolekcji.
  
Jako dodatkowy przykład załóżmy, że wcześniej przypisano Alexowi zasady FederationAndPICDefault, a teraz zmieniono zdanie i chcesz, aby był on zarządzany przez globalne zasady dostępu zewnętrznego. Nie można jawnie przypisać zasad globalnych do nikogo. Zamiast tego zasady globalne są używane dla danego użytkownika, jeśli żadne zasady dla użytkownika nie są przypisane do tego użytkownika. W związku z tym, jeśli chcemy, aby Alex był zarządzany przez zasady globalne, musisz  *anulować przypisanie*  wszelkich przypisanych wcześniej zasad dla poszczególnych użytkowników. Oto przykładowe polecenie:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

To polecenie ustawia nazwę zasad dostępu zewnętrznego przypisanych alexowi na wartość null ($Null). Wartość null oznacza "nic". Innymi słowy, do Alexa nie są przypisane żadne zasady dostępu zewnętrznego. Jeśli do użytkownika nie przypisano żadnych zasad dostępu zewnętrznego, ten użytkownik będzie zarządzany przez zasady globalne.

## <a name="managing-large-numbers-of-users"></a>Zarządzanie dużą liczbą użytkowników

Aby zarządzać dużą liczbą użytkowników (1000 lub więcej), należy wsadowo wykonywać polecenia za pomocą bloku skryptu przy użyciu polecenia cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .  W poprzednich przykładach za każdym razem, gdy polecenie cmdlet jest wykonywane, musi skonfigurować wywołanie, a następnie poczekać na wynik przed wysłaniem go z powrotem.  W przypadku korzystania z bloku skryptu umożliwia to zdalne wykonywanie poleceń cmdlet, a po zakończeniu wysyłanie danych z powrotem.

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

Spowoduje to znalezienie 500 użytkowników jednocześnie, którzy nie mają zasad klienta. Przyzna im zasady klienta "ClientPolicyNoIMURL" i zasady dostępu zewnętrznego "FederationAndPicDefault". Wyniki są podzielone na partie w grupy po 50, a każda partia po 50 jest następnie wysyłana do maszyny zdalnej.
  
## <a name="see-also"></a>Zobacz też

[Zarządzanie Skype dla firm Online przy użyciu programu PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
