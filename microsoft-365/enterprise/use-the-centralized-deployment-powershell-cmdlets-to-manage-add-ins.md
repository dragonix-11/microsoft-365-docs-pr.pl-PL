---
title: Zarządzanie dodatkami za pomocą poleceń cmdlet programu PowerShell scentralizowanego wdrażania
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/24/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
ms.custom:
- seo-marvel-apr2020
description: Polecenia cmdlet programu PowerShell scentralizowanego wdrażania ułatwiają wdrażanie dodatków Office i zarządzanie nimi dla organizacji Microsoft 365.
ms.openlocfilehash: 07e0f69cd95bc1553adea96242bf44eb9f1217f1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078463"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Zarządzanie dodatkami za pomocą poleceń cmdlet programu PowerShell scentralizowanego wdrażania

Jako administrator globalny Microsoft 365 możesz wdrażać dodatki Office dla użytkowników za pośrednictwem funkcji Scentralizowane wdrażanie (zobacz [Wdrażanie dodatków Office w centrum administracyjnym](../admin/manage/manage-deployment-of-add-ins.md). Oprócz wdrażania dodatków Office za pośrednictwem Centrum administracyjne platformy Microsoft 365 można również użyć programu Microsoft PowerShell. Zainstaluj [moduł wdrażania scentralizowanego Add-In usługi O365 dla Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).

Po pobraniu modułu otwórz regularne okno Windows PowerShell i uruchom następujące polecenie cmdlet:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```

## <a name="connect-using-your-admin-credentials"></a>Połączenie przy użyciu poświadczeń administratora

Aby można było używać poleceń cmdlet scentralizowanego wdrażania, musisz się zalogować.

1. Uruchom program PowerShell.

2. Połączenie do programu PowerShell przy użyciu poświadczeń administratora firmy. Uruchom następujące polecenie cmdlet.

  ```powershell
  Connect-OrganizationAddInService
  ```

3. Na stronie **Wprowadzanie poświadczeń** wprowadź Microsoft 365 **administratora użytkownika** lub poświadczenia **administratora globalnego**. Alternatywnie możesz wprowadzić swoje poświadczenia bezpośrednio do polecenia cmdlet.

    Uruchom następujące polecenie cmdlet określające poświadczenia administratora firmy jako obiekt PSCredential.

  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Aby uzyskać więcej informacji na temat korzystania z programu PowerShell, zobacz [Połączenie do Microsoft 365 za pomocą programu PowerShell](./connect-to-microsoft-365-powershell.md).

## <a name="upload-an-add-in-manifest"></a>Upload manifest dodatku

Uruchom polecenie cmdlet **New-OrganizationAdd-In** , aby przekazać manifest dodatku ze ścieżki, która może być lokalizacją pliku lub adresem URL. W poniższym przykładzie przedstawiono lokalizację pliku dla wartości parametru  _ManifestPath_ .

```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Możesz również uruchomić polecenie cmdlet **New-OrganizationAdd-In** , aby przekazać dodatek i przypisać go do użytkowników lub grup bezpośrednio przy użyciu parametru  _Członkowie_ , jak pokazano w poniższym przykładzie. Rozdziel adresy e-mail członków przecinkiem.

```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Upload dodatku ze Sklepu Office

Uruchom polecenie cmdlet **New-OrganizationAddIn**, aby przekazać manifest ze sklepu Office Store.

W poniższym przykładzie polecenie cmdlet **New-OrganizationAddIn** określa identyfikator assetid dla dodatku dla Stany Zjednoczone lokalizacji i rynku zawartości.

```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Aby określić wartość parametru _AssetId_, możesz skopiować ją z adresu URL strony internetowej sklepu Office Store dla dodatku. Identyfikatory assetId zawsze zaczynają się od "WA", po których następuje liczba. Na przykład w poprzednim przykładzie źródłem wartości AssetId WA104099688 jest adres URL strony internetowej sklepu Office Store dla dodatku: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).

Wartości parametru Ustawienia regionalne i _parametru ContentMarket_ są _identyczne_ i wskazują kraj/region, z których próbujesz zainstalować dodatek. Format to en-US, fr-FR. i tak dalej.

> [!NOTE]
> Dodatki przekazane ze sklepu Office Store zostaną automatycznie zaktualizowane w ciągu kilku dni od udostępnienia najnowszej aktualizacji w sklepie Office Store.

## <a name="get-details-of-an-add-in"></a>Uzyskiwanie szczegółów dodatku

Uruchom polecenie cmdlet **Get-OrganizationAddIn** , jak pokazano poniżej, aby uzyskać szczegółowe informacje o wszystkich dodatkach przekazanych do dzierżawy, w tym identyfikatora produktu dodatku.

```powershell
Get-OrganizationAddIn
```

Uruchom polecenie cmdlet **Get-OrganizationAddIn** z wartością parametru  _ProductId_ , aby określić dodatek, dla którego chcesz pobrać szczegóły.

```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Aby uzyskać pełne szczegóły wszystkich dodatków oraz przypisanych użytkowników i grup, przeprowadź potok danych wyjściowych polecenia cmdlet **Get-OrganizationAddIn** do polecenia cmdlet Format-List, jak pokazano w poniższym przykładzie.

```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Włączanie lub wyłączanie dodatku

Aby wyłączyć dodatek, aby przypisani do niego użytkownicy i grupy nie mieli już dostępu, uruchom polecenie cmdlet **Set-OrganizationAddIn** z parametrem  _ProductId_ i parametrem  _Enabled_ ustawionym na  `$false`, jak pokazano w poniższym przykładzie.

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Aby ponownie włączyć dodatek, uruchom to samo polecenie cmdlet z parametrem  _Enabled_ ustawionym na  `$true`wartość .

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Dodawanie lub usuwanie użytkowników z dodatku

Aby dodać użytkowników i grupy do określonego dodatku, uruchom polecenie **cmdlet Set-OrganizationAddInAssignments** z parametrami  _ProductId_,  _Add_ i  _Members_ . Rozdziel adresy e-mail członków przecinkiem.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Aby usunąć użytkowników i grupy, uruchom to samo polecenie cmdlet przy użyciu parametru  _Usuń_ .

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Aby przypisać dodatek do wszystkich użytkowników w dzierżawie, uruchom to samo polecenie cmdlet przy użyciu parametru  _AssignToEveryone_ z wartością ustawioną na  `$true`.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Aby nie przypisywać dodatku do wszystkich użytkowników i wrócić do poprzednio przypisanych użytkowników i grup, można uruchomić to samo polecenie cmdlet i wyłączyć parametr  _AssignToEveryone_ , ustawiając jego wartość na  `$false`.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Aktualizowanie dodatku

Aby zaktualizować dodatek z manifestu, uruchom polecenie cmdlet **Set-OrganizationAddIn** z parametrami  _ProductId_,  _ManifestPath_ i  _Locale_ , jak pokazano w poniższym przykładzie.

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Dodatki przekazane ze sklepu Office Store zostaną automatycznie zaktualizowane w ciągu kilku dni od udostępnienia najnowszej aktualizacji w sklepie Office Store.

## <a name="delete-an-add-in"></a>Usuwanie dodatku

Aby usunąć dodatek, uruchom polecenie cmdlet **Remove-OrganizationAddIn** z parametrem  _ProductId_ , jak pokazano w poniższym przykładzie.

```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<!--
## Customize Microsoft Store add-ins for your organization

You must customize the add-in before you deploy it to your organization. Add-ins older than version 1.1 are not supported by this feature.

We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.

Note also the following restrictions:
- All URLs must be absolute (include http or https) and valid.
- *DisplayName* must not exceed 125 characters
- *DisplayName*, *Resources* and *AppDomains* must not include the following characters:

    - \<
    -  \>
    -  ;
    -  =

If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.

To customize an add-in, run the **Set -OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg"
```
To customize multiple tags for an add-in, add those tags to the commandline:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg"
```

> [!IMPORTANT]
> You must apply multiple customized tags to one add-in as one command. If you customize tags one by one, only the last customization will be applied. Additionally, if you customize a tag by mistake, you must remove all customizations and start over.

### Tags you can customize

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| The URL of the image used as the add-in's icon (in admin center). |
| \<DisplayName>| The title of the add-in  (in admin center).|
| \<Hosts>| List of apps that will support the add-in.|
| \<SourceLocation> | The source URL that the add-in will connect to.|
| \<AppDomains> | A list of domains that the add-in can connect with. |
| \<SupportURL>| The URL users can use to access help and support. |
| \<Resources>  | This tag contains a number of elements including titles, tooltips, and icons of different sizes.|
|
### Customize Resources tag

Any element in the <Resources> tag of the manifest can be customized dynamically. You first need to check the manifest to find the element id to which you want to assign a new value. The <Resources> tag looks like this:

```
<Resources>
    <bt:Images>
          <bt:Image id="img16icon" DefaultValue="https://site.com/img.jpg"
    </bt:Images>
</Resources>
```
In this case, the element id for the image is "img16icon" and the value associated with it is "http:<i></i>//site.<i></i>com/img.jpg."

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{"ElementID" = "New Value"; "NextElementID" = "Next New Value"}
```

You can customize as many elements with the command as you need to.

### Remove customization from an add-in

The only option currently available for deleting customizations is to delete all of them at once:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391
```

### View add-in customizations

To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet. If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.

```powershell
Get-OrganizationAddInOverrides
```
If ProductId is specified, then a list of overrides applied to that add-in is returned.

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391
```

### Remove an add-in from local cache

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remove an add-in from cache:

1. Navigate to the "Users" folder in C:\
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a>Uzyskaj szczegółową pomoc dotyczącą każdego polecenia cmdlet

Aby zapoznać się ze szczegółową pomocą dla każdego polecenia cmdlet, użyj polecenia cmdlet Get-help. Na przykład następujące polecenie cmdlet zawiera szczegółowe informacje o poleceniu cmdlet Remove-OrganizationAddIn.

```powershell
Get-help Remove-OrganizationAddIn -Full
```
