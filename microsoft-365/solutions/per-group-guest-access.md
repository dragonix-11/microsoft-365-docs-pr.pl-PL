---
title: Zapobieganie dodaniu gości do określonej grupy
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
description: Dowiedz się, jak uniemożliwić dodanie gości do określonej grupy
ms.openlocfilehash: 4b9ebc6366934db52c30d51091ac9991ff82d8c3
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570068"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>Zapobieganie dodaniu gości do określonej grupy Microsoft 365 lub zespołu Microsoft Teams zespołu

Jeśli chcesz zezwolić na dostęp gości do większości grup i zespołów, ale w niektórych miejscach, w których nie chcesz zezwalać na dostęp gości, możesz zablokować dostęp gościa dla poszczególnych grup i zespołów. (Zablokowanie dostępu gościa do zespołu jest wykonywane przez zablokowanie dostępu gościa do skojarzonej grupy). Zapobiega to dodawaniu nowych gości, ale nie powoduje usunięcia gości, którzy są już w grupie lub zespole.

Jeśli używasz etykiet wrażliwości w swojej organizacji, zalecamy używanie ich do kontrolowania dostępu gościa w zależności od grupy. Aby dowiedzieć się, jak to zrobić, zobacz Chroninie zawartości w witrynach sieci [Microsoft Teams, Microsoft 365 grup SharePoint zawartości](../compliance/sensitivity-labels-teams-groups-sites.md). Jest to zalecane podejście.

## <a name="change-group-settings-using-microsoft-powershell"></a>Zmienianie ustawień grupy przy użyciu programu Microsoft PowerShell

Możesz również zapobiec dodatku nowych gości do poszczególnych grup przy użyciu programu PowerShell. (Pamiętaj, że witryna zespołu skojarzona SharePoint ma [osobne mechanizmy udostępniania gościa](/sharepoint/change-external-sharing-site)).

Aby zmienić ustawienie dostępu gościa na poziomie grupy Azure Active Directory należy użyć wersji Preview programu [PowerShell dla programu Graph](/powershell/azure/active-directory/install-adv2) (nazwa modułu **AzureADPreview**):

- Jeśli nie zainstalowano jeszcze żadnej wersji modułu programu Azure AD PowerShell, zobacz [Instalowanie modułu usługi Azure AD](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) i postępuj zgodnie z instrukcjami, aby zainstalować publiczną wersję zapoznawczą.

- Jeśli masz zainstalowaną ogólnie dostępną wersję modułu Azure AD PowerShell (AzureAD) w wersji 2.0, musisz ją odinstalować, uruchamiając `Uninstall-Module AzureAD` w sesji programu PowerShell, a następnie zainstalować wersję zapoznawczą, uruchamiając `Install-Module AzureADPreview`.

- Jeśli masz już zainstalowaną wersję zapoznawczą, uruchom `Install-Module AzureADPreview` , aby upewnić się, że jest to najnowsza wersja tego modułu.

> [!NOTE]
> Aby uruchomić te polecenia, musisz mieć uprawnienia administratora globalnego. 

Uruchom poniższy skrypt, zmieniając *\<GroupName\>* nazwę grupy, w której chcesz zablokować dostęp gościa.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

Aby zweryfikować ustawienia, uruchom to polecenie:

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

Weryfikacja wygląda następująco:
    
![Zrzut ekranu przedstawiający okno programu PowerShell pokazujące, że dostęp do grupy gości został ustawiony na wartość False (Fałsz).](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

Jeśli chcesz ponownie włączyć ustawienie zezwalania na dostęp gościa do konkretnej grupy, uruchom poniższy skrypt, zmieniając nazwę grupy, ```<GroupName>``` w której chcesz zezwolić na dostęp gościa.

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

## <a name="allow-or-block-guest-access-based-on-their-domain"></a>Zezwalanie na dostęp gościa lub blokowanie go na podstawie jego domeny

Możesz zezwolić na gości korzystających z określonej domeny lub zablokować ich. Jeśli na przykład Twoja firma (Contoso) będzie partnerską firmą (Fabrikam), możesz dodać firmę Fabrikam do listy zezwalań, aby twoi użytkownicy dodali tych gości do swoich grup.

Aby uzyskać więcej informacji, zobacz [Zezwalanie na zaproszenia do B2B lub blokowanie zaproszeń do B2B użytkowników z określonych organizacji](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>Dodawanie gości do globalnej listy adresowej

Domyślnie goście nie są widoczni na globalnej Exchange adresowej. Aby wyświetlić gościa na globalnej liście adresowej, należy wykonać czynności wymienione poniżej.

Znajdź identyfikator ObjectID gościa, uruchamiając go:

```PowerShell
Get-AzureADUser -Filter "userType eq 'Guest'"
```

Następnie uruchom następujące czynności, używając odpowiednich wartości dla obiektów ObjectID, GivenName, Surname, DisplayName i TelephoneNumber.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Zarządzanie członkostwem w grupie w Centrum administracyjne platformy Microsoft 365](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[Azure Active Directory dostępu](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
