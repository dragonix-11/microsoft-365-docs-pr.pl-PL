---
title: Zarządzanie zasadami usługi Skype dla firm Online przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Podsumowanie: Zarządzanie właściwościami konta użytkownika usługi Skype dla firm Online przy użyciu programu PowerShell przy użyciu zasad.'
ms.openlocfilehash: 71ced77947efda0f587fe7a20af85a73dea73f6c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094355"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>Zarządzanie zasadami usługi Skype dla firm Online przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Aby zarządzać wieloma właściwościami konta użytkownika dla usługi Skype dla firm Online, należy określić je jako właściwości zasad w programie PowerShell dla Microsoft 365.
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

Skorzystaj z tych instrukcji, aby skonfigurować uruchamianie poleceń (pomiń kroki, które zostały już wykonane):

  > [!Note]
  > Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams programu PowerShell. Jeśli używasz najnowszej Teams publicznej wersji programu PowerShell, nie musisz instalować łącznika usługi Skype dla firm Online.

1. Zainstaluj [moduł Teams programu PowerShell](/microsoftteams/teams-powershell-install).
    
2. Otwórz wiersz polecenia Windows PowerShell i uruchom następujące polecenia: 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   Po wyświetleniu monitu wprowadź nazwę i hasło konta administratora usługi Skype dla firm Online.
    
## <a name="manage-user-account-policies"></a>Zarządzanie zasadami konta użytkownika

Wiele właściwości konta użytkownika usługi Skype dla firm Online jest konfigurowanych przy użyciu zasad. Zasady to po prostu kolekcje ustawień, które można zastosować do co najmniej jednego użytkownika. Aby przyjrzeć się sposobowi konfigurowania zasad, możesz uruchomić to przykładowe polecenie dla zasad FederationAndPICDefault:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Z kolei należy wrócić do czegoś podobnego do następującego:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

W tym przykładzie wartości w tych zasadach określają, co użycie może lub nie może zrobić, jeśli chodzi o komunikację z użytkownikami federacyjnymi. Na przykład właściwość EnableOutsideAccess musi być ustawiona na wartość True, aby użytkownik mógł komunikować się z osobami spoza organizacji. Należy pamiętać, że ta właściwość nie jest wyświetlana w Centrum administracyjne platformy Microsoft 365. Zamiast tego właściwość jest automatycznie ustawiana na wartość True lub False na podstawie innych wybranych opcji. Pozostałe dwie właściwości są interesujące:
  
- **EnableFederationAccess** wskazuje, czy użytkownik może komunikować się z osobami z domen federacyjnych.
    
- **EnablePublicCloudAccess** wskazuje, czy użytkownik może komunikować się z Windows użytkownikami na żywo.
    
W związku z tym nie zmieniasz bezpośrednio właściwości związanych z federacją na kontach użytkowników (na przykład **Set-CsUser -EnableFederationAccess $True**). Zamiast tego przypisujesz kontu zasady dostępu zewnętrznego, które mają wstępnie skonfigurowane żądane wartości właściwości. Jeśli chcemy, aby użytkownik mógł komunikować się z użytkownikami federacyjnymi i z użytkownikami Windows Live, to konto użytkownika musi mieć przypisane zasady, które zezwalają na tego typu komunikację.
  
Jeśli chcesz wiedzieć, czy ktoś może komunikować się z użytkownikami spoza organizacji, musisz:
  
- Określ, które zasady dostępu zewnętrznego zostały przypisane do tego użytkownika.
    
- Określ, które możliwości są lub nie są dozwolone przez te zasady.
    
Można to zrobić na przykład za pomocą następującego polecenia:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

To polecenie znajduje zasady przypisane do użytkownika, a następnie znajduje możliwości włączone lub wyłączone w ramach tych zasad.
  
Aby zarządzać zasadami usługi Skype dla firm Online za pomocą programu PowerShell, zobacz polecenia cmdlet dla następujących elementów:

- [Zasady klienta](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Zasady konferencji](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Zasady dotyczące urządzeń przenośnych](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Zasady poczty głosowej online](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Zasady routingu głosów](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Plan wybierania numerów Skype dla firm Online to zasady pod każdym względem, z wyjątkiem nazwy. Nazwa "plan wybierania numerów" została wybrana zamiast na przykład "zasady wybierania numerów", aby zapewnić zgodność z poprzednimi wersjami z serwerem Office Communications Server i Exchange. 
  
Aby na przykład przyjrzeć się wszystkim zasadom głosowym dostępnym do użycia, uruchom następujące polecenie:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> Spowoduje to zwrócenie listy wszystkich dostępnych zasad głosu. Należy jednak pamiętać, że nie wszystkie zasady mogą być przypisane do wszystkich użytkowników. Wynika to z różnych ograniczeń dotyczących licencjonowania i lokalizacji geograficznej. (Tak zwana "[lokalizacja użycia](/previous-versions/azure/dn194136(v=azure.100))")." Jeśli chcesz poznać zasady dostępu zewnętrznego i zasady konferencji, które można przypisać do określonego użytkownika, użyj poleceń podobnych do następujących: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

Parametr ApplicableTo ogranicza zwrócone dane do zasad, które mogą być przypisane do określonego użytkownika (na przykład Alex Darrow). W zależności od ograniczeń dotyczących licencjonowania i lokalizacji użycia mogą one reprezentować podzbiór wszystkich dostępnych zasad. 
  
W niektórych przypadkach właściwości zasad nie są używane z Microsoft 365, podczas gdy inne mogą być zarządzane tylko przez personel pomocy technicznej firmy Microsoft. 
  
W przypadku Skype dla firm Online użytkownicy muszą być zarządzane przez zasady pewnego rodzaju. Jeśli prawidłowa właściwość związana z zasadami jest pusta, oznacza to, że dany użytkownik jest zarządzany przez zasady globalne, czyli zasady, które są automatycznie stosowane do użytkownika, chyba że przypisano mu zasady dla poszczególnych użytkowników. Ponieważ nie widzimy zasad klienta na liście dla konta użytkownika, są one zarządzane przez zasady globalne. Globalne zasady klienta można określić za pomocą następującego polecenia:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Skype dla firm Online przy użyciu programu PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)