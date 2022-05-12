---
title: Zarządzanie Grupy Microsoft 365 przy użyciu programu PowerShell
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
description: W tym artykule dowiesz się, jak wykonywać typowe zadania zarządzania dla grup Microsoft 365 w programie PowerShell.
ms.openlocfilehash: 407e242728bf37ebf8c11b8094bfa4931229e4ef
ms.sourcegitcommit: 3226bdf213b290ec5262670873c3a75f17b66ddd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2022
ms.locfileid: "65372208"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>Zarządzanie Grupy Microsoft 365 przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Ten artykuł zawiera kroki wykonywania typowych zadań zarządzania dla grup w programie Microsoft PowerShell. Zawiera również listę poleceń cmdlet programu PowerShell dla grup. Aby uzyskać informacje na temat zarządzania witrynami SharePoint, zobacz [Manage SharePoint Online sites using PowerShell (Zarządzanie witrynami SharePoint Online przy użyciu programu PowerShell](/sharepoint/manage-team-and-communication-sites-in-powershell)).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Link do wytycznych dotyczących użycia Grupy Microsoft 365

Gdy użytkownicy [tworzą lub edytują grupę w Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), możesz wyświetlić im link do wytycznych dotyczących użycia w organizacji. Jeśli na przykład chcesz dodać określony prefiks lub sufiks do nazwy grupy.

Użyj programu PowerShell Azure Active Directory (Azure AD), aby wskazać użytkownikom wytyczne dotyczące użycia Microsoft 365 grup w organizacji. Zapoznaj się [Azure Active Directory poleceń cmdlet do konfigurowania ustawień grupy](/azure/active-directory/enterprise-users/groups-settings-cmdlets) i wykonaj kroki opisane w artykule **Tworzenie ustawień na poziomie katalogu**, aby zdefiniować hiperłącze wytycznych dotyczących użycia. Po uruchomieniu polecenia cmdlet usługi AAD użytkownicy będą widzieć link do wytycznych podczas tworzenia lub edytowania grupy w Outlook.

![Utwórz nową grupę z linkiem wytycznych dotyczących użycia.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Kliknij pozycję Wytyczne dotyczące użycia grupy, aby wyświetlić wskazówki dotyczące grup Office 365 organizacji.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Zezwalaj użytkownikom na wysyłanie jako grupa Microsoft 365

Jeśli chcesz włączyć grupy Microsoft 365 na wartość "Wyślij jako", skonfiguruj to za pomocą poleceń cmdlet [Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) i [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission). Po włączeniu tego ustawienia użytkownicy grupy Microsoft 365 mogą używać Outlook lub Outlook w sieci Web do wysyłania wiadomości e-mail i odpowiadania na nie jako grupy Microsoft 365. Użytkownicy mogą przejść do grupy, utworzyć nową wiadomość e-mail i zmienić pole "Wyślij jako" na adres e-mail grupy.

([Można to również zrobić w centrum administracyjnym Exchange](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).

Użyj następującego skryptu, zastępując *\<GroupAlias\>* go aliasem grupy, którą chcesz zaktualizować, oraz *\<UserAlias\>* aliasem użytkownika, któremu chcesz udzielić uprawnień. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w celu uruchomienia tego skryptu.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Po wykonaniu polecenia cmdlet użytkownicy mogą przejść do Outlook lub Outlook w sieci Web, aby wysłać jako grupę, dodając adres e-mail grupy do pola **Od**.

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Tworzenie klasyfikacji dla Grupy Microsoft 365 w organizacji

Możesz utworzyć etykiety poufności, które użytkownicy w organizacji mogą ustawić podczas tworzenia grupy Microsoft 365. Jeśli chcesz klasyfikować grupy, zalecamy używanie etykiet poufności zamiast poprzedniej funkcji klasyfikacji grup. Aby uzyskać informacje na temat korzystania z etykiet poufności, zobacz [Używanie etykiet poufności do ochrony zawartości w witrynach Microsoft Teams, Microsoft 365 i SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> Jeśli obecnie używasz etykiet klasyfikacji, nie będą one już dostępne dla użytkowników, którzy tworzą grupy po włączeniu etykiet poufności.

Nadal można używać poprzedniej funkcji klasyfikacji grup. Można tworzyć klasyfikacje, które użytkownicy w organizacji mogą ustawić podczas tworzenia grupy Microsoft 365. Można na przykład zezwolić użytkownikom na ustawianie "Standardowa", "Tajne" i "Ściśle tajne" dla grup, które tworzą. Klasyfikacje grup nie są domyślnie ustawiane i należy je utworzyć, aby użytkownicy go ustawili. Użyj Azure Active Directory programu PowerShell, aby wskazać użytkownikom wytyczne dotyczące użycia Grupy Microsoft 365 w organizacji.

Zapoznaj się [Azure Active Directory poleceniami cmdlet do konfigurowania ustawień grupy](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) i wykonaj kroki opisane w temacie **Tworzenie ustawień na poziomie katalogu**, aby zdefiniować klasyfikację Grupy Microsoft 365.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Aby skojarzyć opis z każdą klasyfikacją, można zdefiniować atrybut ustawienia  *ClassificationDescriptions* .

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

Gdzie klasyfikacja jest zgodna z ciągami na liście klasyfikacji.

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

Zapoznaj się [z tematem Używanie programu PowerShell z programem Exchange Online](/powershell/exchange/exchange-online-powershell) i [Połączenie do Exchange Online programu PowerShell, aby](/powershell/exchange/connect-to-exchange-online-powershell) uzyskać więcej informacji na temat korzystania z programu Exchange Online Programu PowerShell.

Po włączeniu tych ustawień właściciel grupy będzie mógł wybrać klasyfikację z menu rozwijanego w Outlook w sieci Web i Outlook, a następnie zapisać ją na stronie **Edytowanie** grupy.

![Wybierz pozycję Microsoft 365 Klasyfikacja grupy.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Ukryj Grupy Microsoft 365 na globalnej liście adresów.

Możesz określić, czy grupa Microsoft 365 jest wyświetlana na globalnej liście adresowej (GAL) i innych listach w organizacji. Jeśli na przykład masz grupę działu prawnego, która nie ma być wyświetlana na liście adresów, możesz zatrzymać wyświetlanie tej grupy w gal. Uruchom polecenie cmdlet grupy Set-Unified, aby ukryć grupę na liście adresów w następujący sposób:

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>Zezwalaj tylko użytkownikom wewnętrznym na wysyłanie wiadomości do Grupy Microsoft 365

Jeśli nie chcesz, aby użytkownicy z innych organizacji wysyłali wiadomości e-mail do grupy Microsoft 365, możesz zmienić ustawienia tej grupy. Umożliwi to tylko użytkownikom wewnętrznym wysyłanie wiadomości e-mail do grupy. Jeśli użytkownik zewnętrzny spróbuje wysłać wiadomość do tej grupy, zostanie on odrzucony.

Uruchom polecenie cmdlet Set-UnifiedGroup, aby zaktualizować to ustawienie w następujący sposób:

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Dodawanie etykietek poczty do Grupy Microsoft 365

Za każdym razem, gdy nadawca próbuje wysłać wiadomość e-mail do grupy Microsoft 365, można wyświetlić mu etykietkę pocztową.

Uruchom polecenie cmdlet grupy Set-Unified, aby dodać etykietkę poczty do grupy:

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Oprócz opcji MailTip można również ustawić pozycję MailTipTranslations, która określa inne języki dla etykietki poczty. Załóżmy, że chcesz mieć tłumaczenie na język hiszpański, a następnie uruchom następujące polecenie:

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Zmienianie nazwy wyświetlanej grupy Microsoft 365

Nazwa wyświetlana określa nazwę grupy Microsoft 365. Ta nazwa jest widoczna w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a> lub <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">w Centrum administracyjne platformy Microsoft 365</a>. Możesz edytować nazwę wyświetlaną grupy lub przypisać nazwę wyświetlaną do istniejącej grupy Microsoft 365, uruchamiając polecenie Set-UnifiedGroup:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Zmień domyślne ustawienie Grupy Microsoft 365 dla Outlook na publiczne lub prywatne

Grupy Microsoft 365 w Outlook są domyślnie tworzone jako prywatne. Jeśli Twoja organizacja chce, aby Grupy Microsoft 365 była domyślnie tworzona jako publiczna (lub z powrotem do prywatnej), użyj tej składni polecenia cmdlet programu PowerShell:

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Public
 ```

Aby ustawić wartość Prywatna:

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Private
 ```

Aby zweryfikować to ustawienie:

 ```powershell
 Get-OrganizationConfig | ft DefaultGroupAccessType
 ```

Aby dowiedzieć się więcej, zobacz [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) i [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>polecenia cmdlet Grupy Microsoft 365

Z Grupy Microsoft 365 można używać następujących poleceń cmdlet.

|**Nazwa polecenia cmdlet**|**Opis**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |Użyj tego polecenia cmdlet, aby wyszukać istniejące Grupy Microsoft 365 i wyświetlić właściwości obiektu grupy  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |Aktualizowanie właściwości określonej grupy Microsoft 365  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |Utwórz nową grupę Microsoft 365. To polecenie cmdlet zapewnia minimalny zestaw parametrów. Aby ustawić wartości właściwości rozszerzonych, użyj Set-UnifiedGroup po utworzeniu nowej grupy  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |Usuwanie istniejącej grupy Microsoft 365  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |Pobieranie informacji o członkostwie i właścicielu dla grupy Microsoft 365  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |Dodawanie członków, właścicieli i subskrybentów do istniejącej grupy Microsoft 365 <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |Usuwanie właścicieli i członków z istniejącej grupy Microsoft 365  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |Służy do wyświetlania informacji o zdjęciu użytkownika skojarzonym z kontem. Zdjęcia użytkowników są przechowywane w usłudze Active Directory  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |Służy do kojarzenia zdjęcia użytkownika z kontem. Zdjęcia użytkowników są przechowywane w usłudze Active Directory  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |Usuń zdjęcie dla grupy Microsoft 365  <br/> |

## <a name="related-topics"></a>Tematy pokrewne

[Uaktualnianie list dystrybucyjnych do Grupy Microsoft 365](/office365/admin/manage/upgrade-distribution-lists)

[Zarządzanie tym, kto może tworzyć grupy platformy Microsoft 365](/office365/admin/create-groups/manage-creation-of-groups)

[Zarządzanie dostępem gościa do Grupy Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Zmień członkostwo w grupie statycznej na dynamiczne w](/azure/active-directory/users-groups-roles/groups-change-type)
