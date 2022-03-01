---
title: Zarządzanie tym, kto może tworzyć Microsoft 365 grupy
f1.keywords: NOCSH
ms.author: mikeplum
ms.reviewer: arvaradh
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 4c46c8cb-17d0-44b5-9776-005fced8e618
recommendations: false
description: Dowiedz się, jak kontrolować, którzy użytkownicy mogą Microsoft 365 grupy.
ms.openlocfilehash: 4280b6859358580547302ccf9497e8cd1e7ed752
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032133"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>Zarządzanie tym, kto może tworzyć Microsoft 365 grupy

Domyślnie wszyscy użytkownicy mogą tworzyć Microsoft 365 grupy. Jest to zalecane podejście, ponieważ umożliwia użytkownikom rozpoczęcie współpracy bez konieczności pomocy ze strony it.

Jeśli Twoja firma wymaga ograniczenia możliwości tworzenia grup, możesz ograniczyć tworzenie grup Microsoft 365 tylko do członków określonej grupy Microsoft 365 lub grupy zabezpieczeń.

Jeśli martwi Cię tworzenie zespołów lub grup, które nie są zgodne ze standardami Twojej firmy, rozważ wymaganie od użytkowników ukończenia kursu szkoleniowego, a następnie dodania ich do grupy dozwolonych użytkowników.

Ograniczenie liczby osób, które mogą tworzyć grupę, ma wpływ na wszystkie usługi korzystające z grup w celu uzyskania dostępu, w tym:

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planner
- Power BI (klasyczny)
- Project sieci Web / Przewodnik

Czynności opisane w tym artykule nie uniemożliwią członkom pewnych ról tworzenia grup. Office 365 administratorzy globalni mogą tworzyć grupy za pośrednictwem usług centrum administracyjne platformy Microsoft 365, Planner, Exchange i SharePoint Online. Inne role mogą tworzyć grupy za pośrednictwem ograniczonych środków wymienionych poniżej.

- Exchange administrator: Exchange administracyjnego usługi Azure AD
- Pomoc techniczna dla partnerów (warstwa 1): centrum administracyjne platformy Microsoft 365, Exchange administracyjne, Usługa Azure AD
- Pomoc techniczna dla partnerów (warstwa 2): centrum administracyjne platformy Microsoft 365, Exchange administracyjne, Azure AD
- Autorzy katalogów: Usługa Azure AD
- SharePoint usługi Azure AD: centrum SharePoint administracyjnego usługi Azure AD
- Teams usługi: centrum administracyjne usługi Teams, Usługa Azure AD
- Administrator użytkownika: usługa centrum administracyjne platformy Microsoft 365, Azure AD

Jeśli jesteś członkiem jednej z tych ról, możesz utworzyć grupy Microsoft 365 dla użytkowników z ograniczeniami, a następnie przypisać tego użytkownika jako właściciela grupy.

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Aby zarządzać tym, kto tworzy grupy, następujące osoby Azure AD — wersja Premium do nich przypisane licencje:

- Administrator, który konfiguruje te ustawienia tworzenia grup
- Członkowie grupy, którzy mogą tworzyć grupy

> [!NOTE]
> Zobacz [Przypisywanie lub usuwanie licencji w portalu Azure Active Directory,](/azure/active-directory/fundamentals/license-users-groups) aby uzyskać więcej informacji na temat przypisywania licencji platformy Azure.

Następujące osoby nie potrzebują Azure AD — wersja Premium przypisanych do nich licencji:

- Osoby, które są członkami Microsoft 365 grup i nie mają możliwości tworzenia innych grup.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>Krok 1. Tworzenie grupy dla użytkowników, którzy muszą tworzyć Microsoft 365 grupy

Do kontrolowania, kto może tworzyć grupy, można użyć tylko jednej grupy w organizacji. Można jednak zagnieździć inne grupy jako członków tej grupy.

Administratorzy pełniący wymienione powyżej role nie muszą być członkami tej grupy: zachowują możliwość tworzenia grup.

1. W centrum administracyjnym przejdź do [strony Grupy](https://admin.microsoft.com/adminportal/home#/groups).

2. Kliknij pozycję **Dodaj grupę**.

3. Wybierz odpowiedni typ grupy. Zapamiętaj nazwę tej grupy! Będzie potrzebna później.

4. Zakończ konfigurowanie grupy, dodając osoby lub inne grupy, które chcesz mieć możliwość tworzenia grup w Twojej organizacji.

Aby uzyskać szczegółowe instrukcje, [zobacz Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń w centrum administracyjne platformy Microsoft 365](../admin/email/create-edit-or-delete-a-security-group.md).

## <a name="step-2-run-powershell-commands"></a>Krok 2. Uruchamianie poleceń programu PowerShell

Aby zmienić ustawienie dostępu gościa na poziomie grupy, należy użyć wersji Preview programu [Azure Active Directory PowerShell dla programu Graph (AzureAD) (](/powershell/azure/active-directory/install-adv2)nazwa modułu **AzureADPreview**):

- Jeśli wcześniej nie zainstalowano żadnej wersji modułu programu PowerShell usługi Azure AD, zobacz Instalowanie modułu [usługi Azure AD](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) i postępuj zgodnie z instrukcjami, aby zainstalować publiczną wersję Preview.

- Jeśli masz zainstalowaną wersję 2.0 modułu programu PowerShell usługi Azure AD (AzureAD), `Uninstall-Module AzureAD` musisz odinstalować go, uruchamiając w sesji programu PowerShell, a następnie zainstalować wersję Preview `Install-Module AzureADPreview`, uruchamiając program .

- Jeśli masz już zainstalowaną wersję Preview, `Install-Module AzureADPreview` uruchom program, aby upewnić się, że jest to najnowsza wersja tego modułu.

Skopiuj poniższy skrypt do edytora tekstów, takiego jak Notatnik, lub do Windows PowerShell [ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

Zamień *\<GroupName\>* na nazwę utworzonej grupy. Przykład:

`$GroupName = "Group Creators"`

Zapisz plik jako GroupCreators.ps1.

W oknie programu PowerShell przejdź do lokalizacji, w której został zapisany plik (wpisz "CD \<FileLocation\>").

Uruchom skrypt, wpisując:

`.\GroupCreators.ps1`

i [zaloguj się przy użyciu konta administratora po](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) wyświetleniu monitu.

```PowerShell
$GroupName = "<GroupName>"
$AllowGroupCreation = $False

Connect-AzureAD

$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
if(!$settingsObjectID)
{
    $template = Get-AzureADDirectorySettingTemplate | Where-object {$_.displayname -eq "group.unified"}
    $settingsCopy = $template.CreateDirectorySetting()
    New-AzureADDirectorySetting -DirectorySetting $settingsCopy
    $settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
}

$settingsCopy = Get-AzureADDirectorySetting -Id $settingsObjectID
$settingsCopy["EnableGroupCreation"] = $AllowGroupCreation

if($GroupName)
{
  $settingsCopy["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString $GroupName).objectid
} else {
$settingsCopy["GroupCreationAllowedGroupId"] = $GroupName
}
Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values
```

W ostatnim wierszu skryptu zostaną zaktualizowane ustawienia:

![Zrzut ekranu przedstawiający dane wyjściowe skryptów programu PowerShell.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

Jeśli w przyszłości chcesz zmienić używaną grupę, możesz ponownie uruchomić skrypt z nazwą nowej grupy.

Jeśli chcesz wyłączyć ograniczenie tworzenia grup i ponownie zezwolić wszystkim użytkownikom na tworzenie grup, ustaw dla $GroupName wartość "", a następnie $AllowGroupCreation wartość "True" (Prawda) i ponownie uruchomić skrypt.

## <a name="step-3-verify-that-it-works"></a>Krok 3. Sprawdzenie działania

Zmiana może potrwać co najmniej 30 minut. Nowe ustawienia możesz sprawdzić, wykonując następujące czynności:

1. Zaloguj się Microsoft 365 za pomocą konta użytkownika, który NIE powinien mieć możliwości tworzenia grup. Oznacza to, że nie jest członkiem utworzonej grupy ani administratorem.

2. Wybierz **kafelek Planner** .

3. W aplikacji Planner wybierz **pozycję Nowy plan** w lewym okienku nawigacji, aby utworzyć plan.

4. Powinien zostać wyświetlony komunikat informujący, że tworzenie planu i grupy jest wyłączone.

Spróbuj ponownie wykonać tę samą procedurę z członkiem grupy.

> [!NOTE]
> Jeśli członkowie grupy nie mogą tworzyć grup, sprawdź, czy nie są blokowani za pośrednictwem ich zasad skrzynki [pocztowej aplikacji OWA](/powershell/module/exchange/set-owamailboxpolicy).

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Rozpoczynanie pracy z programem Office 365 PowerShell](../enterprise/getting-started-with-microsoft-365-powershell.md)

[Konfigurowanie samoobsługowego zarządzania grupą w programie Azure Active Directory](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Azure Active Directory cmdlet do konfigurowania ustawień grupy](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
