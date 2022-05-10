---
title: Zasady kwarantanny
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak używać zasad kwarantanny do kontrolowania, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2f24592460daa4f476e969069d0c1b7636f6a23e
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285549"
---
# <a name="quarantine-policies"></a>Zasady kwarantanny

Zasady kwarantanny (wcześniej nazywane _tagami kwarantanny_) w Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Microsoft Defender umożliwiają administratorom kontrolowanie, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie na podstawie przyczyn kwarantanny komunikatu.

Tradycyjnie użytkownicy mają dozwolone lub niedozwolone poziomy interakcyjności komunikatów kwarantanny w zależności od tego, dlaczego wiadomość została poddana kwarantannie. Na przykład użytkownicy mogą wyświetlać i wydawać wiadomości poddane kwarantannie przez filtrowanie antyspamowe jako spam lub zbiorcze, ale nie mogą wyświetlać ani wydawać wiadomości, które zostały poddane kwarantannie jako wyłudzanie informacji o wysokim poziomie zaufania lub złośliwe oprogramowanie.

W przypadku [obsługiwanych funkcji ochrony](#step-2-assign-a-quarantine-policy-to-supported-features) zasady kwarantanny określają, co użytkownicy mogą robić dla własnych komunikatów (wiadomości, w których są adresatami) w kwarantannie i w _powiadomieniach o kwarantannie_. [Powiadomienia o kwarantannie](use-spam-notifications-to-release-and-report-quarantined-messages.md) są zastępowane powiadomieniami o spamie użytkowników końcowych. Powiadomienia te są teraz kontrolowane przez zasady kwarantanny i zawierają informacje o komunikatach objętych kwarantanną dla wszystkich obsługiwanych funkcji ochrony (nie tylko zasad ochrony przed spamem i werdyktów dotyczących zasad ochrony przed wyłudzaniem informacji).

Domyślne zasady kwarantanny, które wymuszają historyczne możliwości użytkownika, są automatycznie przypisywane do akcji w obsługiwanych funkcjach ochrony, które poddają komunikaty kwarantannie. Możesz też utworzyć niestandardowe zasady kwarantanny i przypisać je do obsługiwanych funkcji ochrony, aby umożliwić użytkownikom wykonywanie określonych akcji dla tych typów komunikatów objętych kwarantanną lub uniemożliwić im wykonywanie określonych akcji.

Poszczególne uprawnienia zasad kwarantanny są łączone z następującymi wstępnie ustawionymi grupami uprawnień:

- Brak dostępu
- Ograniczony dostęp
- Pełny dostęp

Poszczególne uprawnienia zasad kwarantanny, które znajdują się w wstępnie ustawionych grupach uprawnień, są opisane w poniższej tabeli:

|Uprawnienia|Brak dostępu|Ograniczony dostęp|Pełny dostęp|
|---|:---:|:---:|:---:|
|**Blokuj nadawcę** (_PermissionToBlockSender_)||![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|**Usuń** (_PermissionToDelete_)||![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|**Wersja zapoznawcza** (_PermissionToPreview_)||![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|**Zezwalaj adresatom na zwolnienie komunikatu z kwarantanny** (_PermissionToRelease_)|||![Znacznik wyboru.](../../media/checkmark.png)|
|**Zezwalaj adresatom na żądanie zwolnienia komunikatu z kwarantanny** (_PermissionToRequestRelease_)||![Znacznik wyboru](../../media/checkmark.png)||

Domyślne zasady kwarantanny, skojarzone z nimi grupy uprawnień i to, czy powiadomienia o kwarantannie są włączone, są opisane w poniższej tabeli:

|Domyślne zasady kwarantanny|Używana grupa uprawnień|Powiadomienia o kwarantannie są włączone?|
|---|---|---|
|AdminOnlyAccessPolicy|Brak dostępu|Nie|
|DefaultFullAccessPolicy|Pełny dostęp|Nie|
|NotificationEnabledPolicy<sup>\*</sup>|Pełny dostęp|Tak|

Jeśli nie podobają Ci się domyślne uprawnienia w wstępnie ustawionych grupach uprawnień lub chcesz włączyć powiadomienia o kwarantannie, utwórz niestandardowe zasady kwarantanny i użyj ich. Aby uzyskać więcej informacji o tym, co robi każde uprawnienie, zobacz sekcję [Szczegóły uprawnień zasad kwarantanny](#quarantine-policy-permission-details) w dalszej części tego artykułu.

Zasady kwarantanny można tworzyć i przypisywać w portalu Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla organizacji Microsoft 365 z Exchange Online skrzynkami pocztowymi; autonomiczny program PowerShell EOP w organizacjach EOP bez Exchange Online skrzynki pocztowe).

> [!NOTE]
> Czas przechowywania wiadomości poddanych kwarantannie przed ich wygaśnięciem jest kontrolowany przez kwarantannę **Zachowaj spam w kwarantannie przez tyle dni** (_QuarantineRetentionPeriod_) w zasadach ochrony przed spamem. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md).
>
> Zmiana zasad kwarantanny przypisanych do obsługiwanej funkcji ochrony ma wpływ na komunikaty poddane kwarantannie _po_ wprowadzeniu zmiany. Ustawienia nowego przypisania zasad kwarantanny nie mają wpływu na komunikaty, które zostały wcześniej poddane kwarantannie przez tę funkcję ochrony.

## <a name="full-access-permissions-and-quarantine-notifications"></a>Uprawnienia pełnego dostępu i powiadomienia o kwarantannie

<sup>\*</sup> Zasady kwarantanny o nazwie NotificationEnabledPolicy nie są obecne we wszystkich środowiskach. Zasady kwarantanny NotificationEnabledPolicy będą mieć, jeśli organizacja spełnia oba poniższe wymagania:

- Twoja organizacja istniała przed włączeniem funkcji zasad kwarantanny (koniec lipca/początek sierpnia 2021 r.).
- Masz co najmniej jedną [zasadę ochrony przed spamem](configure-your-spam-filter-policies.md) (domyślne zasady ochrony przed spamem lub niestandardowe zasady ochrony przed spamem), w których włączono ustawienie **Włącz powiadomienia o spamie użytkowników końcowych** .

Zgodnie z wcześniejszym opisem powiadomienia o kwarantannie w zasadach kwarantanny zastępują powiadomienia o spamie użytkowników końcowych używane do włączania lub wyłączania zasad ochrony przed spamem. Wbudowane zasady kwarantanny o nazwie DefaultFullAccessPolicy duplikują _historyczne uprawnienia do komunikatów poddanych_ kwarantannie, ale _powiadomienia kwarantanny_ nie są włączone w zasadach kwarantanny. Ponieważ nie można zmodyfikować wbudowanych zasad, nie można włączyć powiadomień o kwarantannie w temacie DefaultFullAccessPolicy.

Aby zapewnić uprawnienia defaultFullAccessPolicy, ale z włączonymi powiadomieniami o kwarantannie, utworzyliśmy zasady o nazwie NotificationEnabledPolicy do użycia zamiast DefaultFullAccessPolicy dla organizacji, które tego potrzebowały (organizacje, w których włączono powiadomienia o spamie użytkowników końcowych).

W przypadku nowych organizacji lub starszych organizacji, w których nigdy nie włączono powiadomień o spamie użytkowników końcowych w zasadach ochrony przed spamem, nie będą dostępne zasady kwarantanny o nazwie NotificationEnabledPolicy. Sposobem włączania powiadomień o kwarantannie jest tworzenie niestandardowych zasad kwarantanny i korzystanie z nich, w których są włączone powiadomienia o kwarantannie.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zasady kwarantanny** , użyj polecenia <https://security.microsoft.com/quarantinePolicies>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby wyświetlać, tworzyć, modyfikować lub usuwać zasady kwarantanny, musisz być członkiem ról **Zarządzanie organizacją**, **Administrator zabezpieczeń** lub **Administrator kwarantanny** w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Krok 1. Tworzenie zasad kwarantanny w portalu Microsoft 365 Defender

1. W [portalu Microsoft 365 Defender przejdź do obszaru](https://security.microsoft.com) Zasady **współpracy** \> & poczty e-mail **& Zasady zasad** \> **zagrożeń** \> **Zasady kwarantanny** w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zasady kwarantanny** , użyj polecenia <https://security.microsoft.com/quarantinePolicies>.

2. Na stronie **Zasady kwarantanny** kliknij ikonę ![Dodaj zasady niestandardowe.](../../media/m365-cc-sc-create-icon.png) **Dodaj zasady niestandardowe**.

3. Zostanie otwarty Kreator **nowych zasad** . Na stronie **Nazwa zasad** wprowadź krótką, ale unikatową nazwę w polu **Nazwa zasad** . W nadchodzących krokach musisz zidentyfikować i wybrać zasady kwarantanny według nazwy. Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Dostęp do wiadomości adresata** wybierz jedną z następujących wartości:
   - **Ograniczony dostęp**: poszczególne uprawnienia, które są zawarte w tej grupie uprawnień, zostały opisane wcześniej w tym artykule.
   - **Ustaw określony dostęp (zaawansowane)**: użyj tej wartości, aby określić uprawnienia niestandardowe. Skonfiguruj następujące wyświetlane ustawienia:
     - **Wybierz preferencję akcji wydania**: wybierz jedną z następujących wartości:
       - Puste: jest to wartość domyślna.
       - **Zezwalaj adresatom na zwolnienie komunikatu z kwarantanny**
       - **Zezwalaj adresatom na żądanie zwolnienia komunikatu z kwarantanny**
     - **Wybierz dodatkowe akcje, które adresaci mogą wykonać w przypadku komunikatów poddanych kwarantannie**: wybierz niektóre, wszystkie lub żadną z następujących wartości:
       - **Usuń**
       - **Wersja zapoznawcza**
       - **Blokuj nadawcę**

   Te uprawnienia i ich wpływ na komunikaty poddane kwarantannie i powiadomienia o kwarantannie zostały opisane w sekcji [Szczegóły uprawnień zasad kwarantanny](#quarantine-policy-permission-details) w dalszej części tego artykułu.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Powiadomienie o spamie użytkownika końcowego** wybierz pozycję **Włącz** , aby włączyć powiadomienia o kwarantannie (wcześniej znane jako powiadomienia o spamie użytkowników końcowych). Po zakończeniu kliknij przycisk **Dalej**.

   > [!NOTE]
   > Jak wyjaśniono wcześniej, wbudowane zasady (AdminOnlyAccessPolicy lub DefaultFullAccessPolicy) nie mają włączonych powiadomień poddanych kwarantannie i nie można modyfikować zasad.

6. Na stronie **Przeglądanie zasad** przejrzyj ustawienia. W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

7. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

Teraz możesz przystąpić do przypisywania zasad kwarantanny do funkcji kwarantanny zgodnie z opisem w sekcji [Krok 2](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>Tworzenie zasad kwarantanny w programie PowerShell

Jeśli wolisz używać programu PowerShell do tworzenia zasad kwarantanny, połącz się z programem Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell i użyj polecenia cmdlet **New-QuarantinePolicy**.

> [!NOTE]
> Jeśli nie używasz parametru _ESNEnabled_ i wartości `$true`, powiadomienia kwarantanny są wyłączone.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>Użyj parametru EndUserQuarantinePermissionsValue

Aby utworzyć zasady kwarantanny przy użyciu _parametru EndUserQuarantinePermissionsValue_ , użyj następującej składni:

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

Parametr _EndUserQuarantinePermissionsValue_ używa wartości dziesiętnej, która jest konwertowana z wartości binarnej. Wartość binarna odpowiada dostępnym uprawnieniom kwarantanny użytkownika końcowego w określonej kolejności. Dla każdego uprawnienia wartość 1 jest równa True, a wartość 0 równa False.

Wymagana kolejność i wartości dla każdego indywidualnego uprawnienia są opisane w poniższej tabeli:

|Uprawnienia|Wartość dziesiętna|Wartość binarna|
|---|:---:|:---:|
|PermissionToViewHeader<sup>\*</sup>|128|10000000|
|PermissionToDownload<sup>\*\*</sup>|64|01000000|
|PermissionToAllowSender<sup>\*\*</sup>|32|00100000|
|PermissionToBlockSender|16|00010000|
|PermissionToRequestRelease<sup>\*\*\*</sup>|8|00001000|
|PermissionToRelease<sup>\*\*\*</sup>|4|00000100|
|PermissionToPreview|2|00000010|
|PermissionToDelete|1|00000001|

<sup>\*</sup> Wartość 0 nie ukrywa przycisku **Wyświetl nagłówek komunikatu** w szczegółach komunikatu poddanej kwarantannie (przycisk jest zawsze dostępny).

<sup>\*\*</sup> To ustawienie nie jest używane (wartość 0 lub 1 nic nie robi).

<sup>\*\*\*</sup> Nie ustawiaj obu tych wartości na 1. Ustaw jedną wartość na 1, a drugą na wartość 0 lub ustaw obie wartości na 0.

W przypadku ograniczonych uprawnień dostępu wymagane wartości to:

|Uprawnienia|Ograniczony dostęp|
|---|:--:|
|PermissionToViewHeader|0|
|PermissionToDownload|0|
|PermissionToAllowSender|0|
|PermissionToBlockSender|1|
|PermissionToRequestRelease|1|
|PermissionToRelease|0|
|PermissionToPreview|1|
|PermissionToDelete|1|
|Wartość binarna|00011011|
|Wartość dziesiętna do użycia|27|

Ten przykład tworzy nowe zasady kwarantanny o nazwie LimitedAccess z włączonymi powiadomieniami o kwarantannie, które przypisują uprawnienia ograniczony dostęp zgodnie z opisem w poprzedniej tabeli.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

W przypadku uprawnień niestandardowych użyj poprzedniej tabeli, aby uzyskać wartość binarną odpowiadającą żądanym uprawnieniom. Przekonwertuj wartość binarną na wartość dziesiętną i użyj wartości dziesiętnej dla _parametru EndUserQuarantinePermissionsValue_ . Nie używaj wartości binarnej dla wartości parametru.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>Krok 2. Przypisywanie zasad kwarantanny do obsługiwanych funkcji

W _obsługiwanych_ funkcjach ochrony, które poddają wiadomości e-mail kwarantannie, można przypisać zasady kwarantanny do dostępnych akcji kwarantanny. Funkcje, które umożliwiają kwarantannę komunikatów i dostępność zasad kwarantanny, opisano w poniższej tabeli:

|Funkcja|Obsługiwane zasady kwarantanny?|Używane domyślne zasady kwarantanny|
|---|:---:|---|
|[Zasady ochrony przed spamem](configure-your-spam-filter-policies.md): <ul><li>**Spam** (_SpamAction_)</li><li>**Spam o wysokim poziomie ufności** (_HighConfidenceSpamAction_)</li><li>**Wyłudzanie informacji** (_PhishSpamAction_)</li><li>**Wyłudzanie informacji o wysokim poziomie zaufania** (_HighConfidencePhishAction_)</li><li>**Zbiorczo** (_BulkSpamAction_)</li></ul>|Tak|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (pełny dostęp)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (pełny dostęp)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (pełny dostęp)</li><li>AdminOnlyAccessPolicy (brak dostępu)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (pełny dostęp)</li></ul>|
|Zasady ochrony przed wyłudzaniem informacji: <ul><li>[Ochrona przed fałszowaniem inteligencji](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Ochrona przed personifikacją w Ochrona usługi Office 365 w usłudze Defender](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<ul><li>**Jeśli komunikat zostanie wykryty jako personifikowany użytkownik** (_TargetedUserProtectionAction_)</li><li>**Jeśli komunikat zostanie wykryty jako domena personifikowana** (_TargetedDomainProtectionAction_)</li><li>**Jeśli analiza skrzynki pocztowej wykryje i personifikuje użytkownika** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|Tak|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (pełny dostęp)</li><li>Ochrona przed personifikacjami:<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (pełny dostęp)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (pełny dostęp)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (pełny dostęp)</li></ul></li></ul>|
|[Zasady ochrony przed złośliwym oprogramowaniem](configure-anti-malware-policies.md): wszystkie wykryte komunikaty są zawsze poddawane kwarantannie.|Tak|AdminOnlyAccessPolicy (brak dostępu)|
|[ochrona załączników Sejf](safe-attachments.md): <ul><li>Wiadomości e-mail z załącznikami, które zostały poddane kwarantannie jako złośliwe oprogramowanie przez zasady załączników Sejf (_Włączanie_ i _działanie_)</li><li>Pliki poddane kwarantannie jako złośliwe oprogramowanie przez [Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li></ul>|<ul><li>Tak</li><li>Nie</li></ul>|<ul><li>AdminOnlyAccessPolicy (brak dostępu)</li><li>nie dotyczy</li></ul>|
|[Reguły przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (nazywane również regułami transportu) z akcją: **Dostarczanie wiadomości do hostowanej kwarantanny** (_kwarantanna_).|Nie|nie dotyczy|

<sup>\*</sup> Jak [opisano wcześniej w tym artykule](#full-access-permissions-and-quarantine-notifications), Organizacja może używać notificationEnabledPolicy zamiast DefaultFullAccessPolicy. Jedyną różnicą między tymi dwoma zasadami kwarantanny jest włączenie powiadomień kwarantanny w obszarze NotificationEnabledPolicy i wyłączenie w obszarze DefaultFullAccessPolicy.

Domyślne zasady kwarantanny, wstępnie ustawione grupy uprawnień i uprawnienia są opisane na [początku tego artykułu](#quarantine-policies) i [w dalszej części tego artykułu](#preset-permissions-groups).

> [!NOTE]
> Jeśli masz domyślne uprawnienia użytkownika końcowego i powiadomienia o kwarantannie, które są udostępniane (lub nie są udostępniane) przez domyślne zasady kwarantanny, nie musisz nic robić. Jeśli chcesz dodać lub usunąć możliwości użytkownika końcowego (dostępne przyciski) dla komunikatów poddanych kwarantannie przez użytkownika lub włączyć powiadomienia o kwarantannie oraz dodać lub usunąć te same możliwości w powiadomieniach o kwarantannie, możesz przypisać inne zasady kwarantanny do akcji kwarantanny.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>Przypisywanie zasad kwarantanny w obsługiwanych zasadach w portalu Microsoft 365 Defender

### <a name="anti-spam-policies"></a>Zasady ochrony przed spamem

1. W [portalu Microsoft 365 Defender przejdź do obszaru](https://security.microsoft.com) Zasady **współpracy** \> & poczty e-mail **, & reguły** \> **Zasady** \> zagrożeń **— ochrona przed spamem** w sekcji **Zasady**.

   Lub, aby przejść bezpośrednio do strony **zasady ant-spam**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** wykonaj jedną z następujących czynności:
   - Znajdź i wybierz istniejące **przychodzące** zasady ochrony przed spamem.
   - Utwórz nowe zasady ochrony przed spamem **dla ruchu przychodzącego** .

3. Wykonaj jedną z następujących czynności:
   - **Edytuj istniejące**: wybierz zasady, klikając nazwę zasad. W wysuwanych szczegółach zasad przejdź do sekcji **Akcje** , a następnie kliknij pozycję **Edytuj akcje**.
   - **Utwórz nową**: w nowym kreatorze zasad przejdź do strony **Akcje** .

4. Na stronie **Akcje** każdy werdykt zawierający akcję **Komunikat kwarantanny** będzie miał również pole **Wyboru zasad kwarantanny** , aby wybrać odpowiednie zasady kwarantanny.

   **Uwaga**: Podczas tworzenia nowych zasad pusta wartość **zasad wybierz kwarantannę** wskazuje, że są używane domyślne zasady kwarantanny dla tego werdyktu. Podczas późniejszej edycji zasad puste wartości są zastępowane przez rzeczywiste domyślne nazwy zasad kwarantanny zgodnie z opisem w poprzedniej tabeli.

   :::image type="content" source="../../media/quarantine-tags-in-anti-spam-policies.png" alt-text="Wybór zasad kwarantanny w zasadach ochrony przed spamem" lightbox="../../media/quarantine-tags-in-anti-spam-policies.png":::

Pełne instrukcje dotyczące tworzenia i modyfikowania zasad ochrony przed spamem opisano w [temacie Konfigurowanie zasad ochrony przed spamem w usłudze EOP](configure-your-spam-filter-policies.md).

#### <a name="anti-spam-policies-in-powershell"></a>Zasady ochrony przed spamem w programie PowerShell

Jeśli wolisz używać programu PowerShell do przypisywania zasad kwarantanny w zasadach ochrony przed spamem, połącz się z programem Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell i użyj następującej składni:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Uwagi**:

- Wartością domyślną parametrów _PhishSpamAction_ i _HighConfidencePhishAction jest Kwarantanna_ , więc nie trzeba używać tych parametrów podczas tworzenia nowych zasad filtrowania spamu w programie PowerShell. W przypadku parametrów _SpamAction_, _HighConfidenceSpamAction_ i _BulkSpamAction_ w nowych lub istniejących zasadach ochrony przed spamem zasady kwarantanny są skuteczne tylko wtedy, gdy wartość to Kwarantanna.

  Aby wyświetlić ważne wartości parametrów w istniejących zasadach ochrony przed spamem, uruchom następujące polecenie:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  Aby uzyskać informacje o domyślnych wartościach akcji i zalecanych wartościach akcji dla standardowych i ścisłych, zobacz [Ustawienia zasad ochrony przed spamem w usłudze EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Podczas tworzenia nowych zasad ochrony przed spamem werdykt filtrowania spamu bez odpowiedniego parametru zasad kwarantanny oznacza, że są używane [domyślne zasady kwarantanny](#step-2-assign-a-quarantine-policy-to-supported-features) dla tego werdyktu.

  Domyślne zasady kwarantanny należy zastąpić niestandardowymi zasadami kwarantanny tylko wtedy, gdy chcesz zmienić domyślne możliwości użytkowników końcowych w komunikatach poddanych kwarantannie dla danego werdyktu filtrowania spamu.

- Nowe zasady ochrony przed spamem w programie PowerShell wymagają zasad filtrowania spamu (ustawień) przy użyciu polecenia cmdlet **New-HostedContentFilterPolicy** i wyłącznej reguły filtru spamu (filtry adresatów) przy użyciu polecenia cmdlet **New-HostedContentFilterRule** . Aby uzyskać instrukcje, zobacz [Tworzenie zasad ochrony przed spamem za pomocą programu PowerShell](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

Ten przykład tworzy nowe zasady filtru spamu o nazwie Dział badań z następującymi ustawieniami:

- Akcja dla wszystkich werdyktów filtrowania spamu jest ustawiona na Kwarantanna.
- Niestandardowe zasady kwarantanny o nazwie NoAccess, które przypisują uprawnienia **Brak dostępu** , zastępują domyślne zasady kwarantanny, które domyślnie nie przypisują żadnych uprawnień **dostępu** .

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

Ten przykład modyfikuje istniejące zasady filtrowania spamu o nazwie Human Resources. Akcja werdyktu dotyczącego kwarantanny spamu jest ustawiona na Kwarantanna, a niestandardowe zasady kwarantanny o nazwie NoAccess są przypisywane.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>Zasady ochrony przed wyłudzaniem informacji

Analiza fałszowania jest dostępna w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Defender. Ochrona przed personifikacją użytkowników, ochrona przed personifikacją domeny i analiza skrzynki pocztowej są dostępne tylko w Ochrona usługi Office 365 w usłudze Defender. Aby uzyskać więcej informacji, zobacz [Zasady ochrony przed wyłudzaniem informacji w Microsoft 365](set-up-anti-phishing-policies.md).

1. W [portalu Microsoft 365 Defender przejdź do obszaru](https://security.microsoft.com) Zasady **współpracy** \> & poczty e-mail **& reguły** \> **Zasady** \> zagrożeń **— ochrona przed wyłudzaniem informacji** w sekcji **Zasady**.

   Lub, aby przejść bezpośrednio do strony **zasady ant-spam**, użyj .<https://security.microsoft.com/antiphishing>

2. Na stronie **Ochrona przed wyłudzaniem informacji** wykonaj jedną z następujących czynności:
   - Znajdź i wybierz istniejące zasady ochrony przed wyłudzaniem informacji.
   - Utwórz nowe zasady ochrony przed wyłudzaniem informacji.

3. Wykonaj jedną z następujących czynności:
   - **Edytuj istniejące**: wybierz zasady, klikając nazwę zasad. W wysuwanych szczegółach zasad przejdź do sekcji **Ustawienia ochrony** , a następnie kliknij pozycję **Edytuj ustawienia ochrony**.
   - **Utwórz nową**: w nowym kreatorze zasad przejdź do strony **Akcje** .

4. Na stronie **Ustawienia ochrony** sprawdź, czy następujące ustawienia są włączone i skonfigurowane zgodnie z wymaganiami:
   - **Włączono ochronę użytkowników**: określ użytkowników.
   - **Włączone domeny do ochrony**: wybierz pozycję **Dołącz domeny, których jestem właścicielem** i/lub **Dołącz domeny niestandardowe** , i określ domeny.
   - **Włączanie analizy skrzynki pocztowej**
   - **Włączanie analizy w celu ochrony przed personifikacją**
   - **Włączanie analizy fałszowania**

5. Wykonaj jedną z następujących czynności:
   - **Edytuj istniejące**: w wysuwanych szczegółach zasad przejdź do sekcji **Akcje** , a następnie kliknij pozycję **Edytuj akcje**.
   - **Utwórz nową**: w nowym kreatorze zasad przejdź do strony **Akcje** .

6. Na stronie **Akcje** każdy werdykt zawierający **akcję Kwarantanna komunikatu** będzie miał również pole **Zastosuj zasady kwarantanny** , aby wybrać odpowiednie zasady kwarantanny.

   **Uwaga**: podczas tworzenia nowych zasad pusta wartość **zasad kwarantanny Zastosuj** wskazuje domyślne zasady kwarantanny dla tej akcji. Podczas późniejszej edycji zasad puste wartości są zastępowane przez rzeczywiste domyślne nazwy zasad kwarantanny zgodnie z opisem w poprzedniej tabeli.

   :::image type="content" source="../../media/quarantine-tags-in-anti-phishing-policies.png" alt-text="Wybór zasad kwarantanny w zasadach ochrony przed wyłudzaniem informacji" lightbox="../../media/quarantine-tags-in-anti-phishing-policies.png":::

Pełne instrukcje dotyczące tworzenia i modyfikowania zasad ochrony przed wyłudzaniem informacji są dostępne w następujących tematach:

- [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w usłudze EOP](configure-anti-phishing-policies-eop.md)
- [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>Zasady ochrony przed wyłudzaniem informacji w programie PowerShell

Jeśli wolisz używać programu PowerShell do przypisywania zasad kwarantanny w zasadach ochrony przed wyłudzaniem informacji, połącz się z programem Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell i użyj następującej składni:

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**Uwagi**:

- Parametry _Włącz\*_ są wymagane do włączenia określonych funkcji ochrony. Wartość domyślna parametrów _EnableMailboxIntelligence_ i _EnableSpoofIntelligence_ jest $true, więc nie trzeba używać tych parametrów podczas tworzenia nowych zasad anty-phish w programie PowerShell. Wszystkie inne parametry _Włącz\*_ muszą mieć wartość $true, aby można było ustawić wartość Kwarantanna w odpowiednich _\*_ parametrach akcji, aby następnie przypisać zasady kwarantanny. Żaden z parametrów _*\Action_ nie ma wartości domyślnej Kwarantanna.

  Aby wyświetlić ważne wartości parametrów w istniejących zasadach anty-phish, uruchom następujące polecenie:

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  Aby uzyskać informacje o domyślnych wartościach akcji i zalecanych wartościach akcji dla standardowych i ścisłych, zobacz [Ustawienia zasad ochrony przed wyłudzaniem informacji EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) i [Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- Podczas tworzenia zasad ochrony przed wyłudzaniem informacji akcja chroniąca przed wyłudzaniem informacji bez odpowiedniego parametru zasad kwarantanny oznacza, że są używane [domyślne zasady kwarantanny](#step-2-assign-a-quarantine-policy-to-supported-features) dla tego werdyktu.

  Domyślne zasady kwarantanny należy zastąpić niestandardowymi zasadami kwarantanny tylko wtedy, gdy chcesz zmienić domyślne możliwości użytkowników końcowych w komunikatach poddanych kwarantannie dla danego werdyktu.

- Nowe zasady ochrony przed wyłudzaniem informacji w programie PowerShell wymagają zasad anty-phish (ustawień) przy użyciu polecenia cmdlet **New-AntiPhishPolicy** i wyłącznej reguły anty-phish (filtry adresatów) przy użyciu polecenia cmdlet **New-AntiPhishRule** . Aby uzyskać instrukcje, zobacz następujące tematy:
  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP przy użyciu programu PowerShell](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji przy użyciu programu Exchange Online PowerShell](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

W tym przykładzie utworzono nowe zasady anty-phish o nazwie Dział badań z następującymi ustawieniami:

- Akcja dla wszystkich werdyktów filtrowania spamu jest ustawiona na Kwarantanna.
- Niestandardowe zasady kwarantanny o nazwie NoAccess, które przypisują uprawnienia **Brak dostępu** , zastępują domyślne zasady kwarantanny, które domyślnie nie przypisują żadnych uprawnień **dostępu** .

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

Ten przykład modyfikuje istniejące zasady anty-phish o nazwie Human Resources. Akcja dla komunikatów wykrytych przez personifikację użytkownika i personifikację domeny jest ustawiona na Kwarantanna, a niestandardowe zasady kwarantanny o nazwie NoAccess są przypisywane.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-AntiPhishPolicy](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>Zasady ochrony przed złośliwym oprogramowaniem

1. W [portalu Microsoft 365 Defender przejdź do obszaru](https://security.microsoft.com) Zasady **współpracy** \> & poczty e-mail **& reguły** \> **Zasady** \> zagrożeń **Chroniące przed złośliwym oprogramowaniem** w sekcji **Zasady**.

   Aby przejść bezpośrednio do strony **Ochrona przed złośliwym oprogramowaniem** , użyj polecenia <https://security.microsoft.com/antimalwarev2>.

2. Na stronie **Ochrona przed złośliwym oprogramowaniem** wykonaj jedną z następujących czynności:
   - Znajdź i wybierz istniejące zasady ochrony przed złośliwym oprogramowaniem.
   - Utwórz nowe zasady ochrony przed złośliwym oprogramowaniem.

3. Wykonaj jedną z następujących czynności:
   - **Edytuj istniejące**: wybierz zasady, klikając nazwę zasad. W wysuwanych szczegółach zasad przejdź do sekcji **Ustawienia ochrony** , a następnie kliknij pozycję **Edytuj ustawienia ochrony**.
   - **Utwórz nową**: w nowym kreatorze zasad przejdź do strony **Akcje** .

4. Na stronie **Ustawienia ochrony** wybierz zasady kwarantanny w polu **Zasady kwarantanny** .

   **Uwaga**: podczas tworzenia nowych zasad pusta wartość **zasad kwarantanny** wskazuje domyślne zasady kwarantanny, dla których są używane. Podczas późniejszej edycji zasad pusta wartość jest zastępowana rzeczywistą domyślną nazwą zasad kwarantanny zgodnie z opisem w poprzedniej tabeli.

#### <a name="anti-malware-policies-in-powershell"></a>Zasady ochrony przed złośliwym oprogramowaniem w programie PowerShell

Jeśli wolisz używać programu PowerShell do przypisywania zasad kwarantanny w zasadach ochrony przed złośliwym oprogramowaniem, połącz się z programem Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell i użyj następującej składni:

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**Uwagi**:

- Podczas tworzenia nowych zasad ochrony przed złośliwym oprogramowaniem bez używania parametru QuarantineTag podczas tworzenia nowych zasad ochrony przed złośliwym oprogramowaniem są używane domyślne zasady kwarantanny wykrywania złośliwego oprogramowania (AdminOnlyAccessPolicy).

  Domyślne zasady kwarantanny należy zastąpić niestandardowymi zasadami kwarantanny tylko wtedy, gdy chcesz zmienić domyślne możliwości użytkowników końcowych w komunikatach, które zostały poddane kwarantannie jako złośliwe oprogramowanie.

  Aby wyświetlić ważne wartości parametrów w istniejących zasadach anty-phish, uruchom następujące polecenie:

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- Nowe zasady ochrony przed złośliwym oprogramowaniem w programie PowerShell wymagają zasad filtrowania złośliwego oprogramowania (ustawień) przy użyciu polecenia cmdlet **New-MalwareFilterPolicy** i wyłącznej reguły filtru złośliwego oprogramowania (filtry adresatów) przy użyciu polecenia cmdlet **New-MalwareFilterRule** . Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem za pomocą Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies).

W tym przykładzie tworzone są zasady filtrowania złośliwego oprogramowania o nazwie Dział badań, które używają niestandardowych zasad kwarantanny o nazwie NoAccess, które przypisują do komunikatów w kwarantannie uprawnienia **Nie ma dostępu** .

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

W tym przykładzie modyfikuje istniejące zasady filtrowania złośliwego oprogramowania o nazwie Human Resources, przypisując niestandardowe zasady kwarantanny o nazwie NoAccess, które przypisują komunikatom z kwarantanną brak uprawnień **dostępu** .

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>zasady załączników Sejf w Ochrona usługi Office 365 w usłudze Defender

1. W [portalu Microsoft 365 Defender przejdź do obszaru](https://security.microsoft.com) Zasady **współpracy** \> & poczty e-mail **& reguły** \> **zasad** \> zagrożeń **Sejf załączników** w sekcji **Zasady**.

   Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **załączników Sejf** wykonaj jedną z następujących czynności:
   - Znajdź i wybierz istniejące zasady Sejf Załączniki.
   - Utwórz nowe zasady Sejf Załączniki.

3. Wykonaj jedną z następujących czynności:
   - **Edytuj istniejące**: wybierz zasady, klikając nazwę zasad. W wysuwanych szczegółach zasad przejdź do sekcji **Ustawienia**, a następnie kliknij pozycję **Edytuj ustawienia**.
   - **Utwórz nową**: w nowym kreatorze zasad przejdź do strony **Ustawienia**.

4. Na stronie **Ustawienia** wykonaj następujące czynności:
   1. **Sejf Odpowiedzi na nieznane złośliwe oprogramowanie załączników**: wybierz pozycję **Blokuj**, **Zastąp** lub **Dynamiczne dostarczanie**.
   2. Wybierz zasady kwarantanny w polu **Zasady kwarantanny** .

   **Uwaga**: podczas tworzenia nowych zasad pusta wartość **zasad kwarantanny** wskazuje, że są używane domyślne zasady kwarantanny. Podczas późniejszej edycji zasad pusta wartość jest zastępowana rzeczywistą domyślną nazwą zasad kwarantanny zgodnie z opisem w poprzedniej tabeli.

Pełne instrukcje dotyczące tworzenia i modyfikowania zasad załączników Sejf opisano w temacie [Konfigurowanie zasad załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-safe-attachments-policies.md).

#### <a name="safe-attachments-policies-in-powershell"></a>zasady załączników Sejf w programie PowerShell

Jeśli wolisz używać programu PowerShell do przypisywania zasad kwarantanny w zasadach Sejf Załączniki, połącz się z programem Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell i użyj następującej składni:

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**Uwagi**:

- Wartości parametrów _Akcja_ Blokuj, Zastąp lub DynamicDelivery mogą powodować komunikaty poddane kwarantannie (wartość Zezwalaj nie powoduje kwarantanny komunikatów). Wartość parametru _Action (Akcja_ ) ma znaczenie tylko wtedy, gdy wartość parametru _Enable_ to `$true`.

- Podczas tworzenia nowych zasad załączników Sejf bez użycia parametru QuarantineTag są używane domyślne zasady kwarantanny dla wykrywania załączników Sejf w wiadomości e-mail (AdminOnlyAccessPolicy).

  Domyślne zasady kwarantanny należy zastąpić niestandardowymi zasadami kwarantanny tylko wtedy, gdy chcesz zmienić domyślne możliwości użytkowników końcowych w wiadomościach e-mail poddawanych kwarantannie przez zasady Sejf Załączniki.

  Aby wyświetlić ważne wartości parametrów, uruchom następujące polecenie:

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- Nowe zasady załączników Sejf w programie PowerShell wymagają zasad bezpiecznego załącznika (ustawień) przy użyciu polecenia cmdlet **New-SafeAttachmentPolicy** i wyłącznej reguły bezpiecznego załącznika (filtry adresatów) przy użyciu polecenia cmdlet **New-SafeAttachmentRule**. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad Sejf załączników za pomocą programu Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies).

W tym przykładzie utworzono zasady bezpiecznego załącznika o nazwie Dział badań, które blokują wykryte komunikaty i używają niestandardowych zasad kwarantanny o nazwie NoAccess, które przypisują do komunikatów z kwarantanną brak uprawnień **dostępu** .

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Ten przykład modyfikuje istniejące zasady bezpiecznego załącznika o nazwie Human Resources, przypisując niestandardowe zasady kwarantanny o nazwie NoAccess, które przypisują **brak uprawnień dostępu** .

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>Konfigurowanie ustawień powiadomień globalnej kwarantanny w portalu Microsoft 365 Defender

Globalne ustawienia zasad kwarantanny umożliwiają dostosowywanie powiadomień kwarantanny wysyłanych do adresatów komunikatów objętych kwarantanną, jeśli powiadomienia o kwarantannie są włączone w zasadach kwarantanny. Aby uzyskać więcej informacji na temat tych powiadomień, zobacz [Powiadomienia o kwarantannie](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. W portalu Microsoft 365 Defender przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> zasad **kwarantanny** zasad \> **zagrożeń** w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zasady kwarantanny** , użyj polecenia <https://security.microsoft.com/quarantinePolicies>.

2. Na stronie **Zasady kwarantanny** wybierz pozycję **Ustawienia globalne**.

3. W wyświetlonym wysuwaniu **ustawień powiadomień kwarantanny** skonfiguruj następujące ustawienia:

   - Dostosuj powiadomienia o kwarantannie na podstawie języka adresata:

     - **Nazwa wyświetlana** nadawcy używanego w powiadomieniach o kwarantannie, jak pokazano na poniższym zrzucie ekranu.

       :::image type="content" source="../../media/quarantine-tags-esn-customization-display-name.png" alt-text="Niestandardowa nazwa wyświetlana nadawcy w powiadomieniu o kwarantannie." lightbox="../../media/quarantine-tags-esn-customization-display-name.png":::

     - Tekst **zastrzeżenia** dodany do dolnej części powiadomień o kwarantannie. Zlokalizowany tekst **A disclaimer from your organization:** is always included first (Zrzeczenie się odpowiedzialności w organizacji): jest zawsze uwzględniany jako pierwszy, a następnie tekst określony jako wyświetlany na poniższym zrzucie ekranu:

       :::image type="content" source="../../media/quarantine-tags-esn-customization-disclaimer.png" alt-text="Niestandardowe zastrzeżenie w dolnej części powiadomienia o kwarantannie." lightbox="../../media/quarantine-tags-esn-customization-disclaimer.png":::

     - Identyfikator języka dla **wartości Nazwa wyświetlana** i **Zastrzeżenie** . Powiadomienia o kwarantannie są już zlokalizowane na podstawie ustawień języka adresata. Wartości **Nazwa wyświetlana** i **Zastrzeżenie** są używane w powiadomieniach kwarantanny, które mają zastosowanie do języka adresata.

       Przed wprowadzeniem wartości _w polach_ **Nazwa wyświetlana** i **Zastrzeżenie** wybierz język w polu **Wybierz język**. Po zmianie wartości w polu **Wybierz język** wartości w polach **Nazwa wyświetlana** i **Zastrzeżenie** zostaną opróżnione.

     Wykonaj następujące kroki, aby dostosować powiadomienia o kwarantannie na podstawie języka adresata:

     1. Wybierz język w polu **Wybierz język** . Wartość domyślna to **Wartość domyślna**, co oznacza angielski.
     2. Wprowadź wartości w polach **Nazwa wyświetlana** i **Zastrzeżenie**. Wartości muszą być unikatowe dla każdego języka. Jeśli spróbujesz ponownie użyć **nazwy wyświetlanej** lub wartości **zastrzeżenia** dla wielu języków, po kliknięciu przycisku **Zapisz** zostanie wyświetlony błąd.
     3. Kliknij przycisk **Dodaj** .
     4. Powtórz poprzednie kroki, aby utworzyć maksymalnie trzy dostosowane powiadomienia o kwarantannie na podstawie języka adresata. Nieoznaczone pole zawiera skonfigurowane języki:

        :::image type="content" source="../../media/quarantine-tags-esn-customization-selected-languages.png" alt-text="Wybrane języki w globalnych ustawieniach powiadomień kwarantanny zasad kwarantanny." lightbox="../../media/quarantine-tags-esn-customization-selected-languages.png":::

   - **Użyj logo mojej firmy**: wybierz tę opcję, aby zastąpić domyślne logo firmy Microsoft używane w górnej części powiadomień o kwarantannie. Przed wykonaniem tego kroku należy postępować zgodnie z instrukcjami w [temacie Dostosowywanie motywu Microsoft 365 dla organizacji](../../admin/setup/customize-your-organization-theme.md) w celu przekazania niestandardowego logo.

     Poniższy zrzut ekranu przedstawia niestandardowe logo w powiadomieniu o kwarantannie:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-logo.png" alt-text="Niestandardowe logo w powiadomieniu o kwarantannie" lightbox="../../media/quarantine-tags-esn-customization-logo.png":::

   - **Wysyłaj powiadomienia o spamie użytkowników końcowych co (dni)**: wybierz częstotliwość powiadomień o kwarantannie. Wartość domyślna to 3 dni, ale możesz wybrać od 1 do 15 dni.

4. Po zakończeniu kliknij przycisk **Zapisz**.

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Wyświetlanie zasad kwarantanny w portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> zasad **kwarantanny** zasad \> **zagrożeń** w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zasady kwarantanny** , użyj polecenia <https://security.microsoft.com/quarantinePolicies>.

2. Strona **Zasady kwarantanny** zawiera listę zasad według **nazwy** i daty **ostatniej aktualizacji** .

3. Aby wyświetlić ustawienia wbudowanych lub niestandardowych zasad kwarantanny, wybierz zasady kwarantanny z listy, klikając nazwę.

4. Aby wyświetlić ustawienia globalne, kliknij pozycję **Ustawienia globalne**

### <a name="view-quarantine-policies-in-powershell"></a>Wyświetlanie zasad kwarantanny w programie PowerShell

Jeśli wolisz używać programu PowerShell do wyświetlania zasad kwarantanny, wykonaj dowolne z następujących kroków:

- Aby wyświetlić listę podsumowań wszystkich wbudowanych lub niestandardowych zasad, uruchom następujące polecenie:

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- Aby wyświetlić ustawienia wbudowanych lub niestandardowych zasad kwarantanny, zastąp \<QuarantinePolicyName\> ciąg nazwą zasad kwarantanny i uruchom następujące polecenie:

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- Aby wyświetlić ustawienia globalne powiadomień o kwarantannie, uruchom następujące polecenie:

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Modyfikowanie zasad kwarantanny w portalu Microsoft 365 Defender

Nie można modyfikować wbudowanych zasad kwarantanny o nazwie AdminOnlyAccessPolicy lub DefaultFullAccessPolicy. Możesz zmodyfikować wbudowane zasady o nazwie NotificationEnabledPolicy ([jeśli je masz](#full-access-permissions-and-quarantine-notifications)) i niestandardowe zasady kwarantanny.

1. W portalu Microsoft 365 Defender przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> zasad **kwarantanny** zasad \> **zagrożeń** w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zasady kwarantanny** , użyj polecenia <https://security.microsoft.com/quarantinePolicies>.

2. Na stronie **Zasady kwarantanny** wybierz zasady, klikając nazwę.

3. Po wybraniu zasad kliknij ikonę Edytuj ![zasady.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** wyświetloną ikonę zasad.

4. Kreator **edytowania zasad**, który zostanie otwarty, jest praktycznie identyczny z Kreatorem **nowych zasad**, jak opisano w sekcji [Tworzenie zasad kwarantanny w portalu Microsoft 365 Defender](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) we wcześniejszej części tego artykułu.

   Główna różnica polega na tym, że nie można zmienić nazwy istniejących zasad.

5. Po zakończeniu modyfikowania zasad przejdź do strony **Podsumowanie** i kliknij pozycję **Prześlij**.

### <a name="modify-quarantine-policies-in-powershell"></a>Modyfikowanie zasad kwarantanny w programie PowerShell

Jeśli wolisz użyć programu PowerShell do zmodyfikowania niestandardowych zasad kwarantanny, zastąp \<QuarantinePolicyName\> ciąg nazwą zasad kwarantanny i użyj następującej składni:

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

Dostępne ustawienia są takie same, jak opisano w przypadku tworzenia zasad kwarantanny we wcześniejszej części tego artykułu.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Usuwanie zasad kwarantanny w portalu Microsoft 365 Defender

**Uwagi**:

- Nie można usunąć wbudowanych zasad kwarantanny o nazwie AdminOnlyAccessPolicy lub DefaultFullAccessPolicy. Możesz usunąć wbudowane zasady o nazwie NotificationEnabledPolicy ([jeśli je masz](#full-access-permissions-and-quarantine-notifications)) i niestandardowe zasady kwarantanny.
- Przed usunięciem zasad kwarantanny sprawdź, czy nie są one używane. Na przykład uruchom następujące polecenie w programie PowerShell:

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  Jeśli zasady kwarantanny są używane, [przed jej usunięciem zastąp przypisane zasady kwarantanny](#step-2-assign-a-quarantine-policy-to-supported-features) .

1. W portalu Microsoft 365 Defender przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> zasad **kwarantanny** zasad \> **zagrożeń** w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zasady kwarantanny** , użyj polecenia <https://security.microsoft.com/quarantinePolicies>.

2. Na stronie **Zasady kwarantanny** wybierz niestandardowe zasady kwarantanny, które chcesz usunąć, klikając nazwę.

3. Po wybraniu zasad kliknij ikonę ![Usuń zasady.](../../media/m365-cc-sc-delete-icon.png) **Ikona usuwania zasad** , która zostanie wyświetlona.

4. Kliknij pozycję **Usuń zasady** w wyświetlonym oknie dialogowym potwierdzenia.

### <a name="remove-quarantine-policies-in-powershell"></a>Usuwanie zasad kwarantanny w programie PowerShell

Jeśli wolisz użyć programu PowerShell do usunięcia niestandardowych zasad kwarantanny, zastąp \<QuarantinePolicyName\> ciąg nazwą zasad kwarantanny i uruchom następujące polecenie:

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>Alerty systemowe dotyczące żądań wydania kwarantanny

Domyślnie domyślne zasady alertów o nazwie **Użytkownik zażądał wydania komunikatu poddanego kwarantannie** automatycznie generują alert informacyjny i wysyłają komunikaty powiadomień do członków następujących grup ról za każdym razem, gdy użytkownik zażąda wydania komunikatu poddanego kwarantannie:

- Administrator kwarantanny
- Administrator zabezpieczeń
- Zarządzanie organizacją (administrator globalny)

Administratorzy mogą dostosować adresatów powiadomień e-mail lub utworzyć niestandardowe zasady alertów, aby uzyskać więcej opcji.

Aby uzyskać więcej informacji na temat zasad alertów, zobacz [Zasady alertów w Microsoft 365](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>Szczegóły uprawnień zasad kwarantanny

W poniższych sekcjach opisano skutki wstępnie ustawionych grup uprawnień i poszczególnych uprawnień w szczegółach komunikatów poddanych kwarantannie i powiadomień o kwarantannie.

### <a name="preset-permissions-groups"></a>Wstępnie ustawione grupy uprawnień

Poszczególne uprawnienia dołączone do wstępnie ustawionych grup uprawnień są wymienione w tabeli na początku tego artykułu.

#### <a name="no-access"></a>Brak dostępu

Jeśli zasady kwarantanny przypisują uprawnienia **Brak dostępu** (tylko administrator), użytkownicy nie będą mogli zobaczyć tych komunikatów, które zostały poddane kwarantannie:

- **Szczegóły komunikatu poddanej kwarantannie**: żadne komunikaty nie będą wyświetlane w widoku użytkownika końcowego.
- **Powiadomienia o kwarantannie**: dla tych komunikatów nie będą wysyłane żadne powiadomienia.

#### <a name="limited-access"></a>Ograniczony dostęp

Jeśli zasady kwarantanny przypisują uprawnienia **ograniczony dostęp** , użytkownicy otrzymają następujące możliwości:

- **Szczegóły komunikatu poddanej kwarantannie**: Dostępne są następujące przyciski:
  - **Żądanie wydania**
  - **Wyświetlanie nagłówków komunikatów**
  - **Komunikat w wersji zapoznawczej**
  - **Usuwanie z kwarantanny**
  - **Blokuj nadawcę**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-limited-access.png" alt-text="Dostępne przyciski w wiadomości poddanej kwarantannie zawierają szczegółowe informacje, jeśli zasady kwarantanny dają użytkownikowi ograniczone uprawnienia dostępu" lightbox="../../media/quarantine-tags-quarantined-message-details-limited-access.png":::

- **Powiadomienia o kwarantannie**: Dostępne są następujące przyciski:
  - **Blokuj nadawcę**
  - **Żądanie wydania**
  - **Przegląd**

  :::image type="content" source="../../media/quarantine-tags-esn-limited-access.png" alt-text="Dostępne przyciski w powiadomieniu o kwarantannie, jeśli zasady kwarantanny dają użytkownikowi ograniczone uprawnienia dostępu" lightbox="../../media/quarantine-tags-esn-limited-access.png":::

#### <a name="full-access"></a>Pełny dostęp

Jeśli zasady kwarantanny przypisują uprawnienia **pełnego dostępu** (wszystkie dostępne uprawnienia), użytkownicy otrzymają następujące możliwości:

- **Szczegóły komunikatu poddanej kwarantannie**: Dostępne są następujące przyciski:
  - **Komunikat o wersji**
  - **Wyświetlanie nagłówków komunikatów**
  - **Komunikat w wersji zapoznawczej**
  - **Usuwanie z kwarantanny**
  - **Blokuj nadawcę**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-full-access.png" alt-text="Dostępne przyciski w wiadomości poddanej kwarantannie zawierają szczegółowe informacje, jeśli zasady kwarantanny dają użytkownikowi pełne uprawnienia dostępu" lightbox="../../media/quarantine-tags-quarantined-message-details-full-access.png":::

- **Powiadomienia o kwarantannie**: Dostępne są następujące przyciski:
  - **Blokuj nadawcę**
  - **Wydanie**
  - **Przegląd**

  :::image type="content" source="../../media/quarantine-tags-esn-full-access.png" alt-text="Dostępne przyciski w powiadomieniu o kwarantannie, jeśli zasady kwarantanny dają użytkownikowi pełne uprawnienia dostępu" lightbox="../../media/quarantine-tags-esn-full-access.png":::

### <a name="individual-permissions"></a>Uprawnienia indywidualne

#### <a name="block-sender-permission"></a>Blokuj uprawnienie nadawcy

Uprawnienie **blokuj nadawcę** (_PermissionToBlockSender_) steruje dostępem do przycisku, który umożliwia użytkownikom wygodne dodawanie nadawcy wiadomości poddanego kwarantannie do listy zablokowanych nadawców.

- **Szczegóły komunikatu poddanej kwarantannie**:
  - Włączone uprawnienie **blokuj nadawcę**: przycisk **Blokuj nadawcę** jest dostępny.
  - **Zablokowane uprawnienie nadawcy** : przycisk **Blokuj nadawcę** jest niedostępny.

- **Powiadomienia o kwarantannie**:
  - Włączone uprawnienie **blokuj nadawcę**: przycisk **Blokuj nadawcę** jest dostępny.
  - **Zablokowane uprawnienie nadawcy** : przycisk **Blokuj nadawcę** jest niedostępny.

Aby uzyskać więcej informacji na temat listy Zablokowanych nadawców, zobacz [Blokuj wiadomości od kogoś](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) i [Użyj Exchange Online programu PowerShell do skonfigurowania kolekcji listy bezpiecznej w skrzynce pocztowej](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="delete-permission"></a>Uprawnienie do usuwania

Uprawnienie **Usuwania** (_PermissionToDelete_) umożliwia użytkownikom usuwanie ich komunikatów (komunikatów, w których użytkownik jest adresatem) z kwarantanny.

- **Szczegóły komunikatu poddanej kwarantannie**:
  - Włączone uprawnienie **usuwania**: dostępny jest przycisk **Usuń z kwarantanny**.
  - **Wyłączone** uprawnienie usuwania: przycisk **Usuń z kwarantanny** jest niedostępny.

- **Powiadomienia o kwarantannie**: Brak efektu.

#### <a name="preview-permission"></a>Uprawnienie podglądu

Uprawnienie **podglądu** (_PermissionToPreview_) steruje możliwością wyświetlania podglądu komunikatów w kwarantannie przez użytkowników.

- **Szczegóły komunikatu poddanej kwarantannie**:
  - Włączone uprawnienie **w wersji zapoznawczej**: przycisk **komunikatu w wersji zapoznawczej** jest dostępny.
  - Wyłączone uprawnienie **podglądu**: przycisk **komunikatu w wersji zapoznawczej** jest niedostępny.

- **Powiadomienia o kwarantannie**: Brak efektu.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Zezwalaj adresatom na zwolnienie komunikatu z uprawnienia kwarantanny

Pozycja **Zezwalaj adresatom na zwolnienie komunikatu z uprawnienia do kwarantanny** (_PermissionToRelease_) umożliwia użytkownikom bezpośrednie i bez zgody administratora wydawanie komunikatów objętych kwarantanną.

- **Szczegóły komunikatu poddanej kwarantannie**:
  - Włączone uprawnienie: przycisk **Komunikat o wersji** jest dostępny.
  - Wyłączone uprawnienie: przycisk **Komunikat o wersji** jest niedostępny.

- **Powiadomienia o kwarantannie**:
  - Włączone uprawnienie: przycisk **Zwolnij** jest dostępny.
  - Uprawnienie wyłączone: przycisk **Zwolnij** jest niedostępny.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Zezwalaj adresatom na żądanie zwolnienia wiadomości z uprawnienia kwarantanny

Pozycja **Zezwalaj adresatom na żądanie zwolnienia komunikatu z uprawnienia kwarantanny** (_PermissionToRequestRelease_) umożliwia użytkownikom _żądanie_ wydania komunikatów poddanych kwarantannie. Komunikat jest zwalniany dopiero po zatwierdzeniu żądania przez administratora.

- **Szczegóły komunikatu poddanej kwarantannie**:
  - Włączone uprawnienie: przycisk **Żądanie wydania** jest dostępny.
  - Uprawnienie wyłączone: przycisk **Żądanie wydania** jest niedostępny.

- **Powiadomienia o kwarantannie**:
  - Włączone uprawnienie: przycisk **Żądanie wydania** jest dostępny.
  - Uprawnienie wyłączone: przycisk **Żądanie wydania** jest niedostępny.
