---
title: Włącz załączniki Sejf załączników wiadomości SharePoint, OneDrive i Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: Administratorzy mogą dowiedzieć się, jak włączyć załączniki wiadomości Sejf dla plików SharePoint, OneDrive i Microsoft Teams, w tym jak ustawiać alerty dotyczące wykrytych plików.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6501097251f4001c58a651db7ddb34bc623e9b0a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021248"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Włącz załączniki Sejf załączników wiadomości SharePoint, OneDrive i Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Program Microsoft Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams chroni twoją organizację przed nieumyślnie udostępnieniem złośliwych plików. Aby uzyskać więcej informacji, [zobacz Sejf załączniki wiadomości SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Ten artykuł zawiera instrukcje dotyczące włączania i konfigurowania załączników Sejf załączników wiadomości SharePoint, OneDrive i Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

- Aby włączyć załączniki Sejf dla systemów SharePoint, OneDrive i Microsoft Teams, musisz być członkiem grup ról Zarządzanie organizacją lub **Administrator** zabezpieczeń w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).

- Aby zapobiec pobieraniu złośliwych plików za pomocą programu SharePoint Online PowerShell, musisz być członkiem roli [administratora](/azure/active-directory/roles/permissions-reference#global-administrator) globalnego lub administratora SharePoint [w](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) usłudze Azure AD.

- Sprawdź, czy dla organizacji włączono rejestrowanie inspekcji. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie wyszukiwania w dzienniku inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

- Może upłynieć do 30 minut, aby ustawienia obowiązywały.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Krok 1. Użyj portalu Microsoft 365 Defender, aby włączyć Sejf załączniki wiadomości SharePoint, OneDrive i Microsoft Teams

1. W portalu Microsoft 365 Defender przejdź <https://security.microsoft.com>do **artykułu Zasady i & zasady** \>  \> zagrożeń **Sejf załączników** w **sekcji** Zasady. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

2. Na stronie **Sejf załączników** kliknij pozycję **Ustawienia globalne**.

3. W **wyświetlonym wysuwam** menu Ustawienia globalne przejdź do sekcji Ochrona plików w folderach **SharePoint, OneDrive i Microsoft Teams** plikach.

   Przesuń przełącznik **Turn on Defender for Office 365 for SharePoint, OneDrive i Microsoft Teams** w ![prawo, aby włączyć przełącznik.](../../media/scc-toggle-on.png) , aby włączyć Sejf załączniki do SharePoint, OneDrive i Microsoft Teams.

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Włączanie Exchange Online PowerShell w celu Sejf załączników załączników wiadomości SharePoint, OneDrive i Microsoft Teams

Jeśli wolisz włączyć załączniki programu Sejf dla dodatków SharePoint, OneDrive i Microsoft Teams za pomocą programu PowerShell, połącz się z programem [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i uruchom następujące polecenie:

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>Krok 2. (Zalecane) Użyj programu SharePoint Online PowerShell, aby uniemożliwić użytkownikom pobieranie złośliwych plików

Domyślnie użytkownicy nie mogą otwierać, przenosić,<sup>\*</sup> kopiować ani udostępniać złośliwych plików wykrytych przez załączniki usługi Sejf dla komputerów SharePoint, OneDrive i Microsoft Teams. Mogą jednak usuwać i pobierać złośliwe pliki.

<sup>\*</sup> Jeśli użytkownicy przejdźą do **opcji Zarządzaj dostępem**, opcja **Udostępnij** będzie nadal dostępna.

Aby uniemożliwić użytkownikom pobieranie złośliwych plików, połącz się z [usługą SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) i uruchom następujące polecenie:

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Uwagi**:

- To ustawienie dotyczy zarówno użytkowników, jak i administratorów.
- Osoby te mogą nadal usuwać złośliwe pliki.

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>Krok 3 (zalecane) Tworzenie zasad alertów Microsoft 365 Defender dla wykrytych plików za pomocą portalu alertów

Możesz utworzyć zasady alertów, które powiadomią Ciebie i innych administratorów, gdy Sejf załączniki dla aplikacji SharePoint, OneDrive i Microsoft Teams wykryje złośliwy plik. Aby dowiedzieć się więcej o alertach, zobacz [Zasady alertów](../../compliance/alert-policies.md).

1. W portalu Microsoft 365 Defender przejdź <https://security.microsoft.com>do **tematu Zasady i & Zasady** \> **alertów**. Aby przejść bezpośrednio do strony **zasady alertu**, użyj .<https://security.microsoft.com/alertpolicies>

2. Na stronie **Zasady alertów** kliknij pozycję **Nowe zasady alertów**.

3. Zostanie **otwarty wysuwny** kreator nowych zasad alertów. Na stronie **Nadaj nazwę alertowi** skonfiguruj następujące ustawienia:
   - **Nazwa**: Wpisz unikatową i opisową nazwę. Na przykład złośliwe pliki w bibliotekach.
   - **Opis**. Wpisz opcjonalny opis. Na przykład powiadamia administratorów o wykryciu złośliwych plików w SharePoint Online, OneDrive lub Microsoft Teams.
   - **Ważność**: **Wybierz pozycję Niski**, **Średni** **lub Wysoki** z listy rozwijanej.
   - **Kategoria**: Wybierz **pozycję Zarządzanie zagrożeniami** z listy rozwijanej.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Tworzenie ustawień alertów** skonfiguruj następujące ustawienia:
   - **Czego chcesz ostrzegać?** sekcja \> **Aktywność to Wybierz** \> **wykryte złośliwe oprogramowanie w pliku** z listy rozwijanej.
   - **Jak chcesz wyzwolić alert?** section: Pozostaw wartość domyślną **Za każdym razem, gdy działanie będzie odpowiadać wybranej regułie** .

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Ustawianie adresatów** skonfiguruj następujące ustawienia:
   - Sprawdź, **czy jest zaznaczona opcja Wyślij powiadomienia e-mail** . W polu **Adresaci wiadomości** e-mail wybierz co najmniej jednego administratora globalnego, administratora zabezpieczeń lub czytnika zabezpieczeń, który powinien otrzymać powiadomienie po wykryciu złośliwego pliku.
   - **Dzienny limit powiadomień**: pozostaw wybraną wartość **domyślną Bez limitu** .

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na **stronie Przeglądanie ustawień** przejrzyj ustawienia. Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   W **sekcji Czy chcesz włączyć zasady od razu?** pozostaw wartość domyślną **Tak, włącz ją od razu.**

   Po zakończeniu kliknij przycisk **Zakończ**.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Tworzenie zasad & zabezpieczeń i zgodności w programie PowerShell w celu utworzenia zasad alertów dotyczących wykrytych plików

Jeśli wolisz użyć programu PowerShell do utworzenia tych samych zasad alertów, które opisano w poprzedniej sekcji, połącz się z programem [PowerShell](/powershell/exchange/connect-to-scc-powershell) w Centrum zabezpieczeń & zgodności i uruchom następujące polecenie:

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Uwaga**: Domyślna wartość _ważności_ to Niska. Aby określić średni lub wysoki, uwzględnij parametr _ważności_ i wartość w poleceniu.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiadomo, że te procedury działały?

- Aby sprawdzić, czy załączniki do załączników wiadomości Sejf SharePoint, OneDrive i Microsoft Teams zostały pomyślnie włączone, należy wykonać jedną z następujących czynności:

  - W portalu Microsoft 365 Defender przejdź do sekcji Zasady **&** \>  \>  \> zasady zagrożeń sekcja **Sejf** Załączniki, wybierz ustawienia globalne i sprawdź wartość włącz defender dla usługi Office 365 dla usługi **SharePoint, OneDrive i Microsoft Teams** ustawienia.

  - W Exchange Online programu PowerShell uruchom następujące polecenie, aby sprawdzić ustawienie właściwości:

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- Aby sprawdzić, czy pobieranie złośliwych plików zostało pomyślnie zablokowane przez inne osoby, otwórz program SharePoint Online PowerShell i uruchom następujące polecenie w celu zweryfikowania wartości właściwości:

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- Aby sprawdzić, czy zasady alertów dotyczące wykrytych plików zostały pomyślnie skonfigurowane, należy wykonać dowolną z następujących czynności:
  - W portalu Microsoft 365 Defender przejdź do **zasad i reguł &** \> **Wybierz** \> zasady alertów i sprawdź ustawienia.
  - W Microsoft 365 Defender PowerShell \<AlertPolicyName\> portalu zamień na nazwę zasad alertów, uruchom następujące polecenie i sprawdź wartości właściwości:

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- Raport o [stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report) umożliwia wyświetlanie informacji o wykrytych plikach w SharePoint, OneDrive i Microsoft Teams. W szczególności możesz użyć widoku **Wyświetl dane według: Złośliwe oprogramowanie dotyczące \>** zawartości.
