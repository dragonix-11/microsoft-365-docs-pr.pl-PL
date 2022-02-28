---
title: Zarządzanie Skype dla firm online za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Podsumowanie: Za pomocą programu PowerShell możesz zarządzać właściwościami konta Skype dla firm online za pomocą zasad.'
ms.openlocfilehash: 674ea6daba498279537f7c302f4bf4d791ee00f5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985086"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>Zarządzanie Skype dla firm online za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Aby zarządzać wieloma właściwościami konta użytkownika dla usługi Skype dla firm Online, musisz określić je jako właściwości zasad w programie PowerShell dla systemu Microsoft 365.
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

Skorzystaj z tych instrukcji, aby skonfigurować uruchamianie poleceń (pomiń czynności, które zostały już wykonane):

  > [!Note]
  > Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams PowerShell. Jeśli używasz najnowszej wersji programu Teams PowerShell, nie musisz instalować do łącznika usługi Skype dla firm Online.

1. Zainstaluj moduł [Teams PowerShell](/microsoftteams/teams-powershell-install).
    
2. Otwórz wiersz Windows PowerShell i uruchom następujące polecenia: 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   Po wyświetleniu monitu wprowadź nazwę Skype dla firm administratora usługi Online oraz hasło.
    
## <a name="manage-user-account-policies"></a>Zarządzanie zasadami kont użytkowników

Wiele Skype dla firm konta użytkownika w trybie online jest konfigurowane przy użyciu zasad. Zasady są po prostu kolekcjami ustawień, które można zastosować do jednego lub większej liczby użytkowników. Aby sprawdzić, jak skonfigurowano zasady, możesz uruchomić to przykładowe polecenie dla zasad FederationAndPICDefault:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Z kolei w takiej sytuacji należy wrócić do nas w podobny sposób:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

W tym przykładzie wartości w tych zasadach określają, jakie zastosowania mogą, a czego nie mogą robić w komunikacji z użytkownikami federacyjną. Na przykład właściwość EnableOutsideAccess musi mieć ustawioną wartość True (Prawda), aby użytkownik mógł komunikować się z osobami spoza organizacji. Ta właściwość nie jest wyświetlana w centrum administracyjne platformy Microsoft 365. Zamiast tego właściwość jest automatycznie ustawiana na wartość True (Prawda) lub False (Fałsz) na podstawie innych wybranych opcji. Pozostałe dwie interesujące cię właściwości to:
  
- **EnableFederationAccess** wskazuje, czy użytkownik może komunikować się z osobami z domen federowanych.
    
- **Ustawienie EnablePublicCloudAccess** wskazuje, czy użytkownik może komunikować się z Windows użytkownikami usługi Live.
    
Dlatego nie można bezpośrednio zmieniać właściwości powiązanych z federacją kont użytkowników (na przykład **Set-CsUser -EnableFederationAccess $True**). Zamiast tego należy przypisać do konta zasady dostępu zewnętrznego, które wstępnie skonfigurowano odpowiednie wartości właściwości. Jeśli chcemy, aby użytkownik mógł komunikować się z użytkownikami federacyjną i użytkownikami usługi Windows Live, temu kontu użytkownika musi zostać przypisana zasada umożliwiająca komunikację tych typów.
  
Aby dowiedzieć się, czy ktoś może komunikować się z użytkownikami spoza organizacji, musisz:
  
- Określ, które zasady dostępu zewnętrznego zostały przypisane do tego użytkownika.
    
- Określanie możliwości, które są lub nie są dozwolone przez te zasady.
    
Można to zrobić na przykład za pomocą tego polecenia:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

To polecenie znajduje zasady przypisane do użytkownika, a następnie znajduje funkcje włączone lub wyłączone w ramach tych zasad.
  
Aby zarządzać Skype dla firm online za pomocą programu PowerShell, zobacz polecenia cmdlet:

- [Zasady klienta](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Zasady dotyczące konferencji](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Zasady dotyczące urządzeń przenośnych](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Zasady poczty głosowej online](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Zasady routingu połączeń głosowych](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Plan Skype dla firm wybierania numerów w trybie online to zasady pod każdym względem z wyjątkiem nazwy. W celu zapewnienia zgodności z poprzednimi wersjami programu Office Communications Server i programem Exchange wybrano nazwę "plan wybierania numerów", zamiast na przykład "zasady wybierania numerów". 
  
Aby na przykład sprawdzić wszystkie zasady komunikacji głosowej dostępne do użycia, uruchom to polecenie:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> Zostanie wyświetlona lista wszystkich dostępnych zasad głosowych. Pamiętaj jednak, że nie wszystkie zasady można przypisać wszystkim użytkownikom. Wynika to z różnych ograniczeń dotyczących licencjonowania i lokalizacji geograficznej. (Tak zwana "[lokalizacja użytkowania](/previous-versions/azure/dn194136(v=azure.100))"). Aby poznać zasady dostępu zewnętrznego i zasady konferencji, które można przypisać do określonego użytkownika, użyj poleceń podobnych do tych: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

Parametr ApplicableTo ogranicza zwracane dane do zasad, które można przypisać do określonego użytkownika (na przykład Alex Darrow). W zależności od ograniczeń licencjonowania i lokalizacji użytkowania może to oznaczać podzbiór wszystkich dostępnych zasad. 
  
W niektórych przypadkach właściwości zasad nie są używane razem z Microsoft 365, natomiast inne mogą być zarządzane tylko przez pracowników pomocy technicznej firmy Microsoft. 
  
W Skype dla firm Online użytkownicy muszą być zarządzani przez pewien rodzaj zasad. Jeśli prawidłowa właściwość związana z zasadami jest pusta, oznacza to, że użytkownikiem zarządza się przy pomocy zasad globalnych, czyli zasad, które są automatycznie stosowane do użytkownika, chyba że mu specjalnie przypisano zasady dla  użytkownika. Ponieważ dla konta użytkownika nie są wymienione zasady klienta, są zarządzane przez zasady globalne. Przy użyciu tego polecenia możesz określić globalne zasady klienta:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie usługą Skype dla firm Online za pomocą programu PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)