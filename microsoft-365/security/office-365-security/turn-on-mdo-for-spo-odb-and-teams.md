---
title: Włączanie bezpiecznych załączników dla programu SharePoint, usługi OneDrive i aplikacji Microsoft Teams
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
description: Administratorzy mogą dowiedzieć się, jak włączyć Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams, w tym jak ustawić alerty dla wykrytych plików.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 55923b13cf47e0309a7246ba43dcb9adaf3c58ff
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016015"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Włączanie bezpiecznych załączników dla programu SharePoint, usługi OneDrive i aplikacji Microsoft Teams

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Ochrona usługi Office 365 w usłudze Microsoft Defender SharePoint, OneDrive i Microsoft Teams chroni organizację przed nieumyślnym udostępnianiem złośliwych plików. Aby uzyskać więcej informacji, zobacz [Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Ten artykuł zawiera kroki włączania i konfigurowania załączników Sejf dla SharePoint, OneDrive i Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

- Aby włączyć Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Aby uniemożliwić użytkownikom pobieranie złośliwych plików za pomocą programu PowerShell SharePoint Online, musisz być członkiem ról [administratora globalnego](/azure/active-directory/roles/permissions-reference#global-administrator) lub [administratora SharePoint](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) w Azure AD.

- Sprawdź, czy rejestrowanie inspekcji jest włączone dla Twojej organizacji. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

- Zaczekaj do 30 minut na zastosowanie ustawień.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Krok 1. Używanie portalu Microsoft 365 Defender do włączania załączników Sejf dla SharePoint, OneDrive i Microsoft Teams

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do sekcji **Zasady & reguły** \> **zagrożeń** \> **Sejf załączniki** w sekcji **Zasady**. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** kliknij pozycję **Ustawienia globalne**.

3. W wyświetlonym **obszarze Ustawienia globalne** przejdź do sekcji **Ochrona plików w sekcji SharePoint, OneDrive i Microsoft Teams**.

   Przenieś przełącznik **Włącz Ochrona usługi Office 365 w usłudze Defender dla SharePoint, OneDrive i Microsoft Teams** do prawego ![przełącznika.](../../media/scc-toggle-on.png) aby włączyć załączniki Sejf dla SharePoint, OneDrive i Microsoft Teams.

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Użyj programu Exchange Online PowerShell, aby włączyć załączniki Sejf dla SharePoint, OneDrive i Microsoft Teams

Jeśli wolisz użyć programu PowerShell, aby włączyć Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams, [połącz się z Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i uruchom następujące polecenie:

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>Krok 2. (Zalecane) Używanie programu PowerShell SharePoint Online, aby uniemożliwić użytkownikom pobieranie złośliwych plików

Domyślnie użytkownicy nie mogą otwierać, przenosić, kopiować ani udostępniać<sup>\*</sup> złośliwych plików wykrytych przez Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams. Mogą jednak usuwać i pobierać złośliwe pliki.

<sup>\*</sup> Jeśli użytkownicy przejdą do pozycji **Zarządzaj dostępem**, opcja **Udostępnij** jest nadal dostępna.

Aby uniemożliwić użytkownikom pobieranie złośliwych plików, [połącz się z programem SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) i uruchom następujące polecenie:

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Uwagi**:

- To ustawienie dotyczy zarówno użytkowników, jak i administratorów.
- Użytkownicy nadal mogą usuwać złośliwe pliki.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>Krok 3 (Zalecane) Tworzenie zasad alertów dla wykrytych plików za pomocą portalu Microsoft 365 Defender

Możesz utworzyć zasady alertów, które powiadamiają Ciebie i innych administratorów, gdy Sejf załączniki dla SharePoint, OneDrive i Microsoft Teams wykrywa złośliwy plik. Aby dowiedzieć się więcej o alertach, zobacz [Zasady alertów](../../compliance/alert-policies.md).

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Zasady & reguł alertów**\>. Aby przejść bezpośrednio do strony **zasad alertów** , użyj polecenia <https://security.microsoft.com/alertpolicies>.

2. Na stronie **Zasady alertów** kliknij pozycję **Nowe zasady alertów**.

3. Kreator **nowych zasad alertów** zostanie otwarty w oknie wysuwanym. Na stronie **Nazwa alertu** skonfiguruj następujące ustawienia:
   - **Nazwa**: wpisz unikatową i opisową nazwę. Na przykład złośliwe pliki w bibliotekach.
   - **Opis**: wpisz opcjonalny opis. Na przykład powiadamia administratorów o wykryciu złośliwych plików w usłudze SharePoint Online, OneDrive lub Microsoft Teams.
   - **Ważność**: wybierz pozycję **Niski**, **Średni** lub **Wysoki** z listy rozwijanej.
   - **Kategoria**: wybierz pozycję **Zarządzanie zagrożeniami** z listy rozwijanej.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Tworzenie ustawień alertu** skonfiguruj następujące ustawienia:
   - **Na czym chcesz otrzymywać alerty?** Działanie sekcji \> **to** \> Wybierz **wykryte złośliwe oprogramowanie w pliku** z listy rozwijanej.
   - **Jak chcesz wyzwolić alert?** sekcja: Pozostaw wartość **domyślną Za każdym razem, gdy działanie jest zgodne z wybraną regułą** .

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Ustawianie adresatów** skonfiguruj następujące ustawienia:
   - Sprawdź **, czy wybrano opcję Wyślij powiadomienia e-mail** . W polu **Adresaci poczty e-mail** wybierz co najmniej jednego administratora globalnego, administratora zabezpieczeń lub czytelników zabezpieczeń, którzy powinni otrzymywać powiadomienia po wykryciu złośliwego pliku.
   - **Dzienny limit powiadomień**: pozostaw wartość domyślną **Nie wybrano limitu** .

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na stronie **Przeglądanie ustawień** przejrzyj ustawienia. W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   W sekcji **Czy chcesz od razu włączyć zasady?** pozostaw wartość domyślną **Tak, włącz ją od razu** .

   Po zakończeniu kliknij przycisk **Zakończ**.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Tworzenie zasad alertów dla wykrytych plików przy użyciu programu PowerShell zgodności & zabezpieczeń

Jeśli wolisz użyć programu PowerShell do utworzenia tych samych zasad alertów, co opisano w poprzedniej sekcji, [połącz się z programem PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell) i uruchom następujące polecenie:

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Uwaga**: domyślna wartość _ważności_ to Niska. Aby określić wartość średnią lub wysoką, dołącz parametr _ważności_ i wartość w poleceniu .

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

- Aby sprawdzić, czy pomyślnie włączono Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams, wykonaj jedną z następujących czynności:

  - W portalu Microsoft 365 Defender przejdź **do sekcji** \> **Zasady & reguły** \> zasad \> **zagrożeń** **Sejf Załączniki**, wybierz pozycję **Ustawienia globalne** i sprawdź wartość **Ochrona usługi Office 365 w usłudze Defender Włączanie dla ustawienie SharePoint, OneDrive i Microsoft Teams**.

  - W Exchange Online programu PowerShell uruchom następujące polecenie, aby zweryfikować ustawienie właściwości:

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- Aby sprawdzić, czy pomyślnie zablokowano użytkownikom możliwość pobierania złośliwych plików, otwórz SharePoint Programu PowerShell online i uruchom następujące polecenie, aby zweryfikować wartość właściwości:

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- Aby sprawdzić, czy zasady alertów dla wykrytych plików zostały pomyślnie skonfigurowane, wykonaj dowolne z następujących kroków:
  - W portalu Microsoft 365 Defender przejdź do obszaru **Zasady & reguły** \> **alertów** \> Wybierz zasady alertów i sprawdź ustawienia.
  - W Microsoft 365 Defender portalu programu PowerShell zastąp \<AlertPolicyName\> ciąg nazwą zasad alertu, uruchom następujące polecenie i sprawdź wartości właściwości:

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- Raport o [stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report) umożliwia wyświetlanie informacji o wykrytych plikach w SharePoint, OneDrive i Microsoft Teams. W szczególności możesz użyć widoku **Wyświetl dane według: Widok złośliwego oprogramowania zawartości\>**.
