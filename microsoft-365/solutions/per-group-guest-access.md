---
title: Uniemożliwianie dodawania gości do określonej grupy
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się, jak uniemożliwić dodawanie gości do określonej grupy
ms.openlocfilehash: f050011427ceeeff8347c2acd5b6d3fbbcf11bec
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285319"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>Uniemożliwianie dodawania gości do określonej grupy Microsoft 365 lub zespołu Microsoft Teams

Jeśli chcesz zezwolić na dostęp gościa do większości grup i zespołów, ale masz gdzieś, gdzie chcesz uniemożliwić dostęp gościowi, możesz zablokować dostęp gościa dla poszczególnych grup i zespołów. (Blokowanie dostępu gościa do zespołu odbywa się przez zablokowanie dostępu gościa do skojarzonej grupy). Zapobiega to dodawaniu nowych gości, ale nie usuwa gości, którzy są już w grupie lub zespole.

Jeśli używasz etykiet poufności w organizacji, zalecamy używanie ich do kontrolowania dostępu gościa dla grupy. Aby uzyskać informacje o tym, jak to zrobić, [użyj etykiet poufności, aby chronić zawartość w witrynach Microsoft Teams, Microsoft 365 i SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md). Jest to zalecane podejście.

## <a name="change-group-settings-using-microsoft-powershell"></a>Zmienianie ustawień grupy przy użyciu programu Microsoft PowerShell

Możesz również uniemożliwić dodawanie nowych gości do poszczególnych grup przy użyciu programu PowerShell. (Pamiętaj, że skojarzona witryna SharePoint zespołu ma [oddzielne kontrolki udostępniania gościa](/sharepoint/change-external-sharing-site)).

Aby zmienić ustawienie dostępu gościa na poziomie grupy, należy użyć wersji zapoznawczej [programu Azure Active Directory programu PowerShell dla Graph](/powershell/azure/active-directory/install-adv2) (nazwa modułu **AzureADPreview**):

- Jeśli nie zainstalowano jeszcze żadnej wersji modułu programu Azure AD PowerShell, zobacz [Instalowanie modułu usługi Azure AD](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) i postępuj zgodnie z instrukcjami, aby zainstalować publiczną wersję zapoznawczą.

- Jeśli masz zainstalowaną ogólnie dostępną wersję modułu Azure AD PowerShell (AzureAD) w wersji 2.0, musisz ją odinstalować, uruchamiając `Uninstall-Module AzureAD` w sesji programu PowerShell, a następnie zainstalować wersję zapoznawczą, uruchamiając `Install-Module AzureADPreview`.

- Jeśli masz już zainstalowaną wersję zapoznawczą, uruchom `Install-Module AzureADPreview` , aby upewnić się, że jest to najnowsza wersja tego modułu.

> [!NOTE]
> Aby uruchamiać te polecenia, musisz mieć uprawnienia administratora globalnego. 

Uruchom następujący skrypt, zmieniając *\<GroupName\>* nazwę grupy, w której chcesz zablokować dostęp gościa.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

Aby zweryfikować ustawienia, uruchom następujące polecenie:

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

Weryfikacja wygląda następująco:
    
![Zrzut ekranu okna programu PowerShell pokazujący, że dostęp do grupy gości został ustawiony na wartość false.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

Jeśli chcesz ponownie przełączyć ustawienie, aby zezwolić na dostęp gościa do określonej grupy, uruchom następujący skrypt, zmieniając ```<GroupName>``` nazwę grupy, w której chcesz zezwolić na dostęp gościa.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$True
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
$id = (get-AzureADObjectSetting -TargetType groups -TargetObjectId $groupID).id
Set-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy -id $id
```

## <a name="allow-or-block-guest-access-based-on-their-domain"></a>Zezwalanie na dostęp gościa lub blokowanie go na podstawie ich domeny

Możesz zezwolić lub zablokować gości korzystających z określonej domeny. Jeśli na przykład Firma (Contoso) współpracuje z inną firmą (Fabrikam), możesz dodać firmę Fabrikam do listy dozwolonych, aby użytkownicy mogli dodawać tych gości do swoich grup.

Aby uzyskać więcej informacji, zobacz [Zezwalanie lub blokowanie zaproszeń do użytkowników B2B z określonych organizacji](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>Dodawanie gości do globalnej listy adresów

Domyślnie goście nie są widoczni na Exchange globalnej liście adresów. Wykonaj poniższe kroki, aby wyświetlić gościa na globalnej liście adresów.

Znajdź identyfikator ObjectID gościa, uruchamiając polecenie:

```PowerShell
get-AzureADUser -all $true | ?{$_.CreationType -eq "Invitation"}
```

Następnie uruchom następujące polecenie, używając odpowiednich wartości dla wartości ObjectID, GivenName, Surname, DisplayName i TelephoneNumber.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Zarządzanie członkostwem w grupie w Centrum administracyjne platformy Microsoft 365](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[przeglądy dostępu Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
