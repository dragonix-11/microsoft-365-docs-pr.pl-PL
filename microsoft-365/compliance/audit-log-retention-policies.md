---
title: Zarządzanie zasadami przechowywania dziennika inspekcji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Zasady przechowywania dziennika inspekcji są częścią nowych funkcji zaawansowanej inspekcji w programie Microsoft 365. Zasady przechowywania dziennika inspekcji pozwalają określić, jak długo mają być zachowywane dzienniki inspekcji w organizacji.
ms.openlocfilehash: f8c269aa4541c438942c69831857ed531681b742
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986426"
---
# <a name="manage-audit-log-retention-policies"></a>Zarządzanie zasadami przechowywania dziennika inspekcji

Zasady przechowywania dziennika inspekcji można tworzyć i zarządzać nimi w Centrum zgodności platformy Microsoft 365. Zasady przechowywania dziennika inspekcji są częścią nowych funkcji zaawansowanej inspekcji w programie Microsoft 365. Zasady przechowywania dziennika inspekcji pozwalają określić, jak długo mają być zachowywane dzienniki inspekcji w organizacji. Dzienniki inspekcji można przechowywać przez maksymalnie 10 lat. Zasady można tworzyć na podstawie następujących kryteriów:

- Wszystkie działania w jednej lub większej Microsoft 365 usługach
- Określone działania (w usłudze Microsoft 365) wykonane przez wszystkich lub określonych użytkowników
- Poziom priorytetu określający zasady, które mają pierwszeństwo w przypadku wielu zasad w organizacji

## <a name="default-audit-log-retention-policy"></a>Domyślne zasady przechowywania dziennika inspekcji

Advanced Audit in Microsoft 365 provides a default audit log retention policy for all organizations. Te zasady zachowują przez jeden Exchange Online, SharePoint online, OneDrive dla Firm i Azure Active Directory inspekcji. Te zasady domyślne zachowują rekordy inspekcji, które zawierają wartość właściwości **Exchange**, **SharePoint**, **OneDrive** i **AzureActiveDirectory** dla właściwości **Workload** (czyli usługi, w której wystąpiło działanie). Nie można modyfikować zasad domyślnych. Zobacz [sekcję Więcej informacji](#more-information) w tym artykule, aby uzyskać listę typów rekordów dla każdego obciążenia pracą uwzględnionego w zasadach domyślnych.

> [!NOTE]
> Domyślne zasady przechowywania dziennika inspekcji mają zastosowanie tylko do rekordów inspekcji działań wykonywanych przez użytkowników, którym przypisano licencję usługi Office 365 lub Microsoft 365 E5 albo którzy mają licencję na zbierania elektronicznych materiałów dowodowych w programie Zgodność platformy Microsoft 365 E5 lub E5 oraz licencję na dodatek Inspekcja. Jeśli w organizacji są użytkownicy niebędący użytkownikami E5 lub goście, odpowiadające im rekordy inspekcji są zachowywane przez 90 dni.

## <a name="before-you-create-an-audit-log-retention-policy"></a>Przed utworzeniem zasad przechowywania dziennika inspekcji

- Aby utworzyć lub zmodyfikować zasady przechowywania inspekcji, musisz mieć przypisaną rolę Konfiguracja organizacji Centrum zgodności platformy Microsoft 365 grupy.

- W organizacji można mieć maksymalnie 50 zasad przechowywania dziennika inspekcji.

- Aby dziennik inspekcji był zachowywany przez czas dłuższy niż 90 dni (i do 1 roku), użytkownik, który generuje dziennik inspekcji (przez wykonanie działań inspekcji), musi mieć przypisaną licencję usługi Office 365 E5 lub Microsoft 365 E5 albo licencję na usługę zbierania elektronicznych materiałów dowodowych w ramach usługi Zgodność platformy Microsoft 365 E5 lub E5 i licencję na dodatek inspekcja. Aby przechowywać dzienniki inspekcji przez 10 lat, oprócz licencji E5 użytkownik, który wygeneruje dziennik inspekcji, musi mieć przypisaną licencję dodatkową do przechowywania dziennika inspekcji na 10 lat.

- Wszystkie niestandardowe zasady przechowywania dziennika inspekcji (utworzone przez Twoją organizację) mają priorytet nad domyślnymi zasadami przechowywania. Jeśli na przykład utworzysz zasady przechowywania dziennika inspekcji dla działań w skrzynce pocztowej programu Exchange, który ma okres przechowywania krótszy niż rok, rekordy inspekcji dotyczące działań skrzynki pocztowej programu Exchange będą przechowywane przez krótszy czas określony w zasadach niestandardowych.

## <a name="create-an-audit-log-retention-policy"></a>Tworzenie zasad przechowywania dziennika inspekcji

1. Przejdź do <https://compliance.microsoft.com> konta użytkownika z przypisaną rolą Konfiguracja organizacji i zaloguj się do tego konta na stronie Uprawnienia w Centrum zgodności platformy Microsoft 365.

2. W lewym okienku okna Centrum zgodności platformy Microsoft 365 pozycję **Inspekcja**.

3. Kliknij **kartę Inspekcja zasad** przechowywania.

4. Kliknij **pozycję Utwórz zasady przechowywania inspekcji**, a następnie na wysuwanych stronie wypełnij następujące pola:

   ![Wysuwna strona nowych zasad przechowywania inspekcji.](../media/CreateAuditLogRetentionPolicy.png)

   1. **Nazwa zasad:** Nazwa zasad przechowywania dziennika inspekcji. Ta nazwa musi być unikatowa w Twojej organizacji i nie można jej zmienić po utworzeniu zasad.

   2. **Opis:** Opcjonalne, ale pomocne w dostarczaniu informacji o zasadach, takich jak typ rekordu lub obciążenie pracą, użytkownicy określone w zasadach i czas trwania.

   3. **Użytkownicy:** Wybierz co najmniej jednego użytkownika, do których chcesz zastosować zasady. Jeśli pozostawisz to pole puste, zasady zostaną stosowane do wszystkich użytkowników. Jeśli pole **Typ rekordu jest** puste, należy wybrać użytkownika.

   4. **Typ rekordu:** Typ rekordu inspekcji, do jakiego mają zastosowanie zasady. Jeśli pozostawisz tę właściwość pustą, musisz wybrać użytkownika w **polu Użytkownicy** . Możesz wybrać jeden typ rekordu lub wiele typów rekordów:
      - Jeśli wybierzesz jeden typ rekordu, pole **Działania** zostanie dynamicznie wyświetlone. Za pomocą listy rozwijanej możesz wybrać działania z wybranego typu rekordu w celu zastosowania zasad. Jeśli nie wybierzesz określonych działań, zasady zostaną stosowane do wszystkich działań wybranego typu rekordu.
      - Jeśli wybierzesz wiele typów rekordów, nie będziesz mieć możliwości zaznaczania działań. Zasady zostaną stosowane do wszystkich działań wybranych typów rekordów.

   5. **Czas trwania:** Czas przechowywania dzienników inspekcji spełniających kryteria zasad.

   6. **Priorytet:** Ta wartość określa kolejność przetwarzania zasad przechowywania dziennika inspekcji w organizacji. O niższej wartości informuje o wyższym priorytecie. Prawidłowe priorytety to wartości liczbowe od **1** **do 10000**. Wartość **1 jest** najwyższym priorytetem, a wartość **10000** ma najniższy priorytet. Na przykład zasady o wartości **5** mają pierwszeństwo przed zasadami o wartości **10**. Jak wyjaśniono wcześniej, wszystkie niestandardowe zasady przechowywania dziennika inspekcji mają pierwszeństwo przed domyślnymi zasadami organizacji.

5. Kliknij **pozycję Zapisz** , aby utworzyć nowe zasady przechowywania dziennika inspekcji.

Nowe zasady zostaną wyświetlone na liście na karcie **Inspekcja zasad** przechowywania.

## <a name="manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center"></a>Zarządzanie zasadami przechowywania dziennika inspekcji w Centrum zgodności platformy Microsoft 365

Zasady przechowywania dziennika inspekcji są wymienione na karcie **Zasady przechowywania inspekcji** (nazywanej również *pulpitem nawigacyjnym*). Za pomocą pulpitu nawigacyjnego można wyświetlać, edytować i usuwać zasady przechowywania inspekcji.

### <a name="view-policies-in-the-dashboard"></a>Wyświetlanie zasad na pulpicie nawigacyjnym

Zasady przechowywania dziennika inspekcji są wyświetlane na pulpicie nawigacyjnym. Jedną z zalet wyświetlania zasad na pulpicie nawigacyjnym jest możliwość kliknięcia  kolumny Priorytet w celu wyświetlenia listy zasad, w których mają one zastosowanie. Jak wyjaśniono wcześniej, mniejsza wartość wskazuje wyższy priorytet.

![Kolumna Priorytet na pulpicie nawigacyjnym Inspekcja zasad przechowywania.](../media/AuditLogRetentionDashboardPriority.png)

Możesz także wybrać zasady, aby wyświetlić ich ustawienia na stronie wysuwu.

> [!NOTE]
> Domyślne zasady przechowywania dziennika inspekcji dla organizacji nie są wyświetlane na pulpicie nawigacyjnym.

### <a name="edit-policies-in-the-dashboard"></a>Edytowanie zasad na pulpicie nawigacyjnym

Aby edytować zasady, zaznacz je w celu wyświetlenia strony wysuwu. Możesz zmodyfikować jedno lub więcej ustawień, a następnie zapisać zmiany.

> [!IMPORTANT]
>
> Jeśli używasz polecenia cmdlet **New-UnifiedAuditLogRetentionPolicy**, możesz utworzyć zasady przechowywania dziennika inspekcji dla typów rekordów lub działań, które nie są dostępne w narzędziu Do tworzenia zasad przechowywania inspekcji  na pulpicie nawigacyjnym. W takim przypadku nie będzie można edytować zasad (na przykład zmienić czasu trwania przechowywania lub dodać i usunąć działania) z pulpitu nawigacyjnego Inspekcja **zasad** przechowywania. Zasady będzie można tylko wyświetlać i usuwać w Centrum zgodności. Aby edytować zasady, musisz użyć polecenia cmdlet [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) w programie PowerShell w centrum zabezpieczeń & zgodności.>
>
> **Porada:** W górnej części wysuwanych stron zostanie wyświetlony komunikat z informacjami o zasadach, które trzeba edytować przy użyciu programu PowerShell.

### <a name="delete-policies-in-the-dashboard"></a>Usuwanie zasad z pulpitu nawigacyjnego

Aby usunąć zasady, kliknij **ikonę Usuń** ![usuń.](../media/92a9f8e0-d469-48da-addb-69365e7ffb6f.jpg) , a następnie potwierdź usunięcie zasad. Zasady zostaną usunięte z pulpitu nawigacyjnego, ale usunięcie zasad z organizacji może potrwać do 30 minut.

## <a name="create-and-manage-audit-log-retention-policies-in-powershell"></a>Tworzenie zasad przechowywania dziennika inspekcji i zarządzanie nimi w programie PowerShell

Do tworzenia zasad przechowywania dziennika inspekcji & zarządzania nimi możesz także użyć programu PowerShell w Centrum zabezpieczeń i zgodności. Jednym z powodów korzystania z programu PowerShell jest utworzenie zasad dla typu rekordu lub działania, które nie jest dostępne w interfejsie użytkownika.

### <a name="create-an-audit-log-retention-policy-in-powershell"></a>Tworzenie zasad przechowywania dziennika inspekcji w programie PowerShell

Wykonaj poniższe czynności, aby utworzyć zasady przechowywania dziennika inspekcji w programie PowerShell:

1. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom następujące polecenie, aby utworzyć zasady przechowywania dziennika inspekcji:

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
   ```

   W tym przykładzie są tworzy zasady przechowywania dziennika inspekcji o nazwie "Microsoft Teams inspekcji" z tymi ustawieniami:

   - Opis zasad.
   - Zachowuje wszystkie Microsoft Teams (zgodnie z definicją *parametru RecordType*).
   - Zachowuje Microsoft Teams inspekcji przez 10 lat.
   - Priorytet 100.

Oto kolejny przykład tworzenia zasad przechowywania dziennika inspekcji. Te zasady zachowują dzienniki inspekcji dla działania "Użytkownik zalogowany" przez sześć miesięcy dla użytkownika, który admin@contoso.onmicrosoft.com.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

Aby uzyskać więcej informacji, [zobacz New-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

### <a name="view-policies-in-powershell"></a>Wyświetlanie zasad w programie PowerShell

Aby wyświetlić zasady przechowywania dziennika inspekcji, użyj polecenia cmdlet [Get-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/get-unifiedauditlogretentionpolicy) w programie PowerShell & w Centrum zabezpieczeń i zgodności.

Oto przykładowe polecenie służące do wyświetlania ustawień dla wszystkich zasad przechowywania dziennika inspekcji w organizacji. To polecenie sortuje zasady od najwyższego do najniższego priorytetu.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> Polecenie **cmdlet Get-UnifiedAuditLogRetentionPolicy** nie zwraca domyślnych zasad przechowywania dziennika inspekcji dla organizacji.

### <a name="edit-policies-in-powershell"></a>Edytowanie zasad w programie PowerShell

Użyj polecenia [cmdlet Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) w programie PowerShell w & Security & Compliance Center, aby edytować istniejące zasady przechowywania dziennika inspekcji.

### <a name="delete-policies-in-powershell"></a>Usuwanie zasad w programie PowerShell

Aby usunąć zasady przechowywania dziennika inspekcji, użyj polecenia cmdlet [Remove-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/remove-unifiedauditlogretentionpolicy) w programie PowerShell w centrum & zabezpieczeń i zgodności. Usunięcie zasad z organizacji może potrwać do 30 minut.

## <a name="more-information"></a>Więcej informacji

Jak wspomniano wcześniej, rekordy inspekcji dotyczące operacji Azure Active Directory, Exchange Online, SharePoint Online i OneDrive dla Firm są domyślnie przechowywane przez jeden rok. W poniższej tabeli wymieniono wszystkie typy rekordów (dla każdej z tych usług) zawarte w domyślnych zasadach przechowywania dziennika inspekcji. Oznacza to, że dzienniki inspekcji dla każdej operacji z tym typem rekordu są przechowywane przez jeden rok, chyba że niestandardowe zasady przechowywania dziennika inspekcji mają pierwszeństwo przed określonym typem rekordu, operacją lub użytkownikiem. Wartość wsadowa (wyświetlana jako wartość właściwości RecordType (Typ Rekordu) dla każdego typu rekordu jest wyświetlana w nawiasach.

<br>

****

|AzureActiveDirectory|Exchange |SharePoint lub OneDrive|
|---|---|---|
|AzureActiveDirectory (8)|ExchangeAdmin (1)|ComplianceDLPSharePoint (11)|
|AzureActiveDirectoryAccountLogon (9)|ExchangeItem (2)|ComplianceDLPSharePointClassification (33)|
|AzureActiveDirectoryStsLogon (15)|Kampania (62)|Project (35)|
||ComplianceDLPExchange (13)|SharePoint (4)|
||ComplianceSupervisionExchange (68)|SharePointCommentOperation (37)|
||CustomerKeyServiceEncryption (69)|SharePointContentTypeOperation (55)|
||ExchangeAggregatedOperation (19)|SharePointFieldOperation (56)|
||ExchangeItemAggregated (50)|SharePointFileOperation (6)|
||ExchangeItemGroup (3)|SharePointListOperation (36)|
||InformationBarrierPolicyApplication (53)|SharePointSharingOperation (14)|
||||
