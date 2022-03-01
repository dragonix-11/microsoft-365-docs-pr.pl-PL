---
title: Zarządzanie grupami Microsoft 365 za pomocą programu PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Z tego artykułu dowiesz się, jak wykonywać typowe zadania zarządzania dla grup Microsoft 365 w programie PowerShell.
ms.openlocfilehash: 460444e1cb2f862f4d96ed6aad0178a146864658
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019354"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>Zarządzanie grupami Microsoft 365 za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W tym artykule przedstawiono procedury wykonywania typowych zadań zarządzania dla grup w programie Microsoft PowerShell. Zawiera również polecenia cmdlet programu PowerShell dla grup. Aby uzyskać informacje na temat SharePoint witryn internetowych, zobacz [Zarządzanie witrynami usługi SharePoint Online za pomocą programu PowerShell](/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Link do wytycznych dotyczących Microsoft 365 grupy użytkowników

Gdy użytkownicy [tworzą lub edytują](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx) grupę w Outlook sieci, możesz im pokazać link do wytycznych dotyczących użycia w Twojej organizacji. Na przykład jeśli wymagane jest dodanie określonego prefiksu lub sufiksu do nazwy grupy.

Użyj programu Azure Active Directory (Azure AD) PowerShell, aby wskazać użytkownikom wytyczne dotyczące korzystania z grup Microsoft 365 organizacji. Zapoznaj się [Azure Active Directory poleceniami cmdlet](/azure/active-directory/enterprise-users/groups-settings-cmdlets) do konfigurowania ustawień grupy i wykonaj czynności opisane w tece  Tworzenie ustawień na poziomie katalogu, aby zdefiniować hiperlink do wytycznych dotyczących użycia. Po uruchomieniu polecenia cmdlet AAD użytkownicy zobaczą link do wytycznych podczas tworzenia lub edytowania grupy w Outlook.

![Utwórz nową grupę z linkiem do wytycznych dotyczących użycia.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Kliknij pozycję Wskazówki dotyczące korzystania z grup, aby wyświetlić wskazówki Office 365 grupy.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Zezwalaj użytkownikom na wysyłanie jako Microsoft 365 grupy

Jeśli chcesz włączyć dla grup Microsoft 365 opcję "Wyślij jako", skonfiguruj to ustawienie za pomocą polecenia [cmdlet Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) i [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission). Po włączeniu tego ustawienia użytkownicy grup Microsoft 365 grupy będą Outlook lub Outlook w sieci Web wysyłać wiadomości e-mail i odpowiadać na nie jako Microsoft 365 grupy. Użytkownicy mogą przejść do grupy, utworzyć nową wiadomość e-mail i zmienić pole "Wyślij jako" na adres e-mail grupy.

([Możesz to również zrobić w centrum Exchange administracyjnego](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).

Użyj poniższego skryptu, zastępując *\<GroupAlias\>* aliasem grupy, którą chcesz zaktualizować, *\<UserAlias\>* oraz aliasem użytkownika, któremu chcesz przyznać uprawnienia. [Połączenie uruchomić Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Po wykonaniu polecenia cmdlet użytkownicy mogą przejść do Outlook lub Outlook w sieci Web, aby wysłać jako grupę, dodając adres e-mail grupy do **pola Od.**

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Tworzenie klasyfikacji dla Microsoft 365 grupy w organizacji

Możesz utworzyć etykiety wrażliwości, które mogą być ustawiane przez użytkowników podczas tworzenia grupy Microsoft 365 grupy. Jeśli chcesz sklasyfikować grupy, zalecamy użycie etykiet wrażliwości zamiast poprzedniej funkcji klasyfikacji grup. Aby uzyskać informacje na temat korzystania z etykiet wrażliwości, zobacz Używanie etykiet wrażliwości do ochrony zawartości w Microsoft Teams[, Microsoft 365 grupach i SharePoint witrynach](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> Jeśli obecnie używasz etykiet klasyfikacji, nie będą one już dostępne dla użytkowników, którzy tworzą grupy po włączeniu etykiet wrażliwości.

Nadal możesz używać poprzedniej funkcji klasyfikacji grup. Możesz utworzyć klasyfikacje, które mogą być ustawiane przez użytkowników podczas tworzenia grupy Microsoft 365 grupy. Na przykład możesz zezwolić użytkownikom na ustawienie "Standardowa", "Tajna" i "Ściśle tajna" dla tworzyć grupy. Klasyfikacje grup nie są ustawiane domyślnie i należy je utworzyć, aby klasyfikacja była ustawiana przez użytkowników. Użyj Azure Active Directory PowerShell, aby wskazać użytkownikom wytyczne dotyczące korzystania z grup Microsoft 365 użytkowników.

Zobacz Azure Active Directory [cmdlet](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) dotyczące konfigurowania ustawień grupy i wykonaj czynności opisane w tece Tworzenie ustawień  na poziomie katalogu, aby zdefiniować klasyfikację dla grup Microsoft 365 grupy.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Aby skojarzyć opis z każdą klasyfikacją, możesz zdefiniować atrybut ustawień  *ClassificationDescriptions* .

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

Gdzie Klasyfikacja odpowiada ciągom na liście ClassificationList.

Przykład:

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Po uruchomieniu powyższego polecenia cmdlet Azure Active Directory w celu ustawienia klasyfikacji uruchom polecenie cmdlet [Set-UnifiedGroup](/powershell/module/exchange/Set-UnifiedGroup), jeśli chcesz ustawić klasyfikację dla określonej grupy.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

Możesz też utworzyć nową grupę z klasyfikacją.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

Aby uzyskać [więcej szczegółowych informacji na temat](/powershell/exchange/exchange-online-powershell) Exchange Online PowerShell, zobacz Używanie programu PowerShell z Exchange Online Połączenie [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Po włączeniu tych ustawień właściciel grupy będzie mógł wybrać klasyfikację z menu rozwijanego w aplikacji Outlook w sieci Web i aplikacji Outlook i zapisać ją na stronie Edytowanie grupy.

![Wybierz Microsoft 365 klasyfikacji grupy.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Ukryj Microsoft 365 grupy na globalnej liście adresowej.

Możesz określić, czy grupa Microsoft 365 ma być wyświetlana na globalnej liście adresowej i innych listach w organizacji. Jeśli na przykład grupa działu prawnego nie ma być wyświetlana na liście adresów, możesz zatrzymać jej wyświetlanie na liście adresowej. Uruchom polecenie cmdlet Set-Unified Group, aby ukryć grupę na liście adresów w ten sposób:

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>Zezwalaj tylko użytkownikom wewnętrznym na wysyłanie wiadomości do Microsoft 365 grupy

Jeśli nie chcesz, aby użytkownicy z innych organizacji wysyłali wiadomości e-mail do grupy Microsoft 365, możesz zmienić ustawienia tej grupy. Tylko użytkownicy wewnętrzni mogą wysyłać wiadomości e-mail do grupy. Jeśli użytkownik zewnętrzny spróbuje wysłać wiadomość do tej grupy, zostanie ona odrzucona.

Uruchom polecenie cmdlet Set-UnifiedGroup, aby zaktualizować to ustawienie, w ten sposób:

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Dodawanie porad dotyczących poczty do Microsoft 365 poczty

Za każdym razem, gdy nadawca spróbuje wysłać wiadomość e-mail do grupy Microsoft 365, może zostać do nich pokazana porada w sprawie poczty.

Uruchom polecenie cmdlet Set-Unified Grupy w celu dodania do grupy porad dotyczących poczty:

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Wraz z poradą o poczty można także ustawić tłumaczenia tej etykietki, która określa inne języki tej etykietki. Załóżmy, że chcesz mieć hiszpańskie tłumaczenie, a następnie uruchom następujące polecenie:

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Zmienianie nazwy wyświetlanej grupy Microsoft 365.

Nazwa wyświetlana określa nazwę grupy Microsoft 365 grupy. Możesz zobaczyć tę nazwę w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">administracyjnym Exchange lub w</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a>. Możesz edytować nazwę wyświetlaną grupy lub przypisać nazwę wyświetlaną do istniejącej grupy Microsoft 365, uruchamiając Set-UnifiedGroup polecenie:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Zmienianie domyślnego ustawienia grup Microsoft 365 grup na publiczne Outlook prywatne

Microsoft 365 grupy w Outlook są domyślnie tworzone jako prywatne. Jeśli Twoja organizacja chce, Microsoft 365 grupy jako publiczne domyślnie (lub ponownie jako prywatne), użyj tej składni polecenia cmdlet programu PowerShell:

 `Set-OrganizationConfig -DefaultGroupAccessType Public`

Aby ustawić wartość Prywatna:

 `Set-OrganizationConfig -DefaultGroupAccessType Private`

Aby sprawdzić ustawienie:

 `Get-OrganizationConfig | ft DefaultGroupAccessType`

Aby dowiedzieć się więcej, [zobacz Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) i [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>Microsoft 365 cmdlet grup

Poniższe polecenia cmdlet mogą być używane z grupami Microsoft 365 grupy.

|**Nazwa polecenia cmdlet**|**Opis**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |To polecenie cmdlet umożliwia przeglądanie istniejących grup Microsoft 365 grupy oraz wyświetlanie właściwości obiektu grupy  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |Aktualizowanie właściwości określonej grupy Microsoft 365 grupy  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |Tworzenie nowej grupy Microsoft 365 grupy. To polecenie cmdlet zapewnia minimalny zestaw parametrów. Aby ustawić wartości dla właściwości rozszerzonych, użyj Set-UnifiedGroup po utworzeniu nowej grupy.  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |Usuwanie istniejącej grupy Microsoft 365 grupy  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |Pobieranie informacji o członkostwie i właścicielu grupy Microsoft 365 grupy  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |Dodawanie członków, właścicieli i subskrybentów do istniejącej grupy Microsoft 365 grupy <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |Usuwanie właścicieli i członków z istniejącej Microsoft 365 grupy  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |Umożliwia wyświetlanie informacji o zdjęciu użytkownika skojarzonego z kontem. Zdjęcia użytkowników są przechowywane w usłudze Active Directory  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |Służy do kojarzenia zdjęcia użytkownika z kontem. Zdjęcia użytkowników są przechowywane w usłudze Active Directory  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |Usuwanie zdjęcia dla grupy Microsoft 365 grupy  <br/> |

## <a name="related-topics"></a>Tematy pokrewne

[Uaktualnianie list dystrybucyjnych do Microsoft 365 grup](/office365/admin/manage/upgrade-distribution-lists)

[Zarządzanie tym, kto może tworzyć Microsoft 365 grupy](/office365/admin/create-groups/manage-creation-of-groups)

[Zarządzanie dostępem gości do grup Microsoft 365 grupy](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Zmienianie statycznego członkostwa w grupach na dynamiczne w](/azure/active-directory/users-groups-roles/groups-change-type)
