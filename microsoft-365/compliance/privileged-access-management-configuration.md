---
title: Wprowadzenie do usługi Privileged Access Management
description: Skorzystaj z tego artykułu, aby dowiedzieć się więcej na temat włączania i konfigurowania zarządzania dostępem uprzywilejowanym w usłudze Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, zgodność, uprzywilejowane zarządzanie dostępem
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: ''
ms.openlocfilehash: d53058e89fc1830b6f35eef270d84b99f2cc9f74
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626342"
---
# <a name="get-started-with-privileged-access-management"></a>Wprowadzenie do usługi Privileged Access Management

W tym artykule opisano włączanie i konfigurowanie zarządzania dostępem uprzywilejowanym w organizacji. Do zarządzania dostępem uprzywilejowanym i korzystania z niego można użyć <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">programu PowerShell Centrum administracyjne platformy Microsoft 365</a> lub programu Exchange Management.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem zarządzania dostępem uprzywilejowanym należy potwierdzić [subskrypcję platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) i wszelkie dodatki. Aby uzyskać dostęp do zarządzania dostępem uprzywilejowanym i korzystać z niego, organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- subskrypcja Microsoft 365 E5 (wersja płatna lub próbna)
- subskrypcja Microsoft 365 E3 (lub subskrypcja Office 365 E3 + subskrypcja Enterprise Mobility and Security E3) + dodatek Zgodność platformy Microsoft 365 E5
- Dowolna subskrypcja platformy Microsoft 365, Office 365, Exchange, SharePoint lub OneDrive dla Firm + dodatek Microsoft 365 E5 Insider Risk Management
- subskrypcja Microsoft 365 A5 (wersja płatna lub próbna)
- subskrypcja Microsoft 365 A3 (lub subskrypcja Office 365 A3 + subskrypcja Enterprise Mobility and Security A3) + dodatek Zgodności z usługą Microsoft A5
- Dowolna subskrypcja platformy Microsoft 365, Office 365, Exchange, SharePoint lub OneDrive dla Edukacji + dodatek Microsoft 365 A5 Insider Risk Management
- subskrypcja Office 365 Enterprise E5 (wersja płatna lub próbna)
- Office 365 Enterprise subskrypcję E3 + dodatek Office 365 Advanced Compliance (nie jest już dostępny dla nowych subskrypcji, zobacz uwaga)

Użytkownicy przesyłający żądania zarządzania dostępem uprzywilejowanym i odpowiadający na nie muszą mieć przypisaną jedną z powyższych licencji.

> [!IMPORTANT]
> Office 365 Advanced Compliance nie jest już sprzedawana jako subskrypcja autonomiczna. Po wygaśnięciu bieżących subskrypcji klienci powinni przejść do jednej z powyższych subskrypcji, która zawiera te same lub dodatkowe funkcje zgodności.

Jeśli nie masz istniejącego planu Office 365 Enterprise E5 i chcesz wypróbować zarządzanie dostępem uprzywilejowanym, możesz dodać usługę [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) do istniejącej subskrypcji Office 365 lub [utworzyć konto próbne](https://www.microsoft.com/microsoft-365/enterprise) Microsoft 365 Enterprise E5.

## <a name="enable-and-configure-privileged-access-management"></a>Włączanie i konfigurowanie zarządzania dostępem uprzywilejowanym

Wykonaj następujące kroki, aby skonfigurować dostęp uprzywilejowany i korzystać z niego w organizacji:

- [Krok 1. Tworzenie grupy osoby zatwierdzającą](privileged-access-management-configuration.md#step1)

    Przed rozpoczęciem korzystania z dostępu do uprawnień określ, kto potrzebuje urzędu zatwierdzania dla przychodzących żądań dostępu do zadań z podwyższonym poziomem uprawnień i uprzywilejowanych. Każdy użytkownik należący do grupy Osoby zatwierdzające może zatwierdzać żądania dostępu. Ta grupa jest włączona przez utworzenie grupy zabezpieczeń z obsługą poczty w Office 365.

- [Krok 2. Włączanie dostępu uprzywilejowanego](privileged-access-management-configuration.md#step2)

    Dostęp uprzywilejowany musi być jawnie włączony w Office 365 z domyślną grupą osoby zatwierdzającą, w tym zestawem kont systemowych, które mają zostać wykluczone z kontroli dostępu do zarządzania dostępem uprzywilejowanym.

- [Krok 3. Tworzenie zasad dostępu](privileged-access-management-configuration.md#step3)

    Utworzenie zasad zatwierdzania umożliwia zdefiniowanie konkretnych wymagań dotyczących zatwierdzania określonych w poszczególnych zadaniach. Opcje typu zatwierdzenia są **automatyczne** lub **ręczne**.

- [Krok 4. Przesyłanie/zatwierdzanie żądań dostępu uprzywilejowanego](privileged-access-management-configuration.md#step4)

    Po włączeniu dostępu uprzywilejowanego wymaga zatwierdzeń dla każdego zadania, które ma zdefiniowane skojarzone zasady zatwierdzania. W przypadku zadań uwzględnionych w zasadach zatwierdzania użytkownicy muszą zażądać zatwierdzenia dostępu i otrzymać je, aby mieć uprawnienia niezbędne do wykonania zadania.

Po udzieleniu zatwierdzenia żądający użytkownik może wykonać zamierzone zadanie, a uprzywilejowany dostęp autoryzuje i wykonuje zadanie w imieniu użytkownika. Zatwierdzenie pozostaje ważne przez żądany czas trwania (domyślny czas trwania to 4 godziny), podczas którego żądająca może wykonać zamierzone zadanie wiele razy. Wszystkie takie wykonania są rejestrowane i udostępniane na potrzeby inspekcji zabezpieczeń i zgodności.

> [!NOTE]
> Jeśli chcesz włączyć i skonfigurować uprzywilejowany dostęp za pomocą programu Exchange Management PowerShell, wykonaj kroki opisane w temacie [Nawiązywanie połączenia z programem PowerShell Exchange Online przy użyciu uwierzytelniania wieloskładnikowego w celu nawiązania](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) połączenia z programem Exchange Online programu PowerShell przy użyciu poświadczeń Office 365. Nie musisz włączać uwierzytelniania wieloskładnikowego w organizacji, aby móc włączyć dostęp uprzywilejowany podczas nawiązywania połączenia z programem Exchange Online programu PowerShell. Nawiązywanie połączenia z uwierzytelnianiem wieloskładnikowym powoduje utworzenie tokenu uwierzytelniania używanego przez uprzywilejowany dostęp do podpisywania żądań.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>Krok 1. Tworzenie grupy osoby zatwierdzającą

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji.

2. W centrum administracyjnym przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a> > **Dodaj grupę**.

3. Wybierz **grupę zabezpieczeń obsługującą pocztę** , a następnie wypełnij pola **Nazwa**, **Adres e-mail grupy** i **Opis** dla nowej grupy.

4. Zapisz grupę. Pełne skonfigurowanie grupy i wyświetlenie jej w Centrum administracyjne platformy Microsoft 365 może potrwać kilka minut.

5. Wybierz grupę nowego osoby zatwierdzającą i wybierz pozycję **Edytuj** , aby dodać użytkowników do grupy.

6. Zapisz grupę.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>Krok 2. Włączanie dostępu uprzywilejowanego

### <a name="in-the-microsoft-365-admin-center"></a>W centrum Administracja Microsoft 365

1. Zaloguj się do [centrum Administracja Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń dla konta administratora w organizacji.

2. W centrum administracyjnym przejdź do pozycji **Ustawienia** > **Ustawienia organizacji Zabezpieczenia** >  &**dostęp uprzywilejowany** <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**prywatności**</a> > .

3. Włącz kontrolkę **Wymagaj zatwierdzeń dla zadań uprzywilejowanych** .

4. Przypisz grupę osoby zatwierdzającą utworzoną w kroku 1 jako **domyślną grupę osób zatwierdzających**.

5. **Zapisz** i **zamknij**.

### <a name="in-exchange-management-powershell"></a>W programie PowerShell zarządzania programem Exchange

Aby włączyć dostęp uprzywilejowany i przypisać grupę osoby zatwierdzającą, uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

Przykład:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', 'sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Funkcja kont systemowych jest udostępniana w celu zapewnienia, że niektóre automatyzacje w organizacji mogą działać bez zależności od uprzywilejowanego dostępu, jednak zaleca się, aby takie wykluczenia były wyjątkowe, a dozwolone powinny być regularnie zatwierdzane i poddawane inspekcji.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>Krok 3. Tworzenie zasad dostępu

Możesz utworzyć i skonfigurować maksymalnie 30 zasad dostępu uprzywilejowanego dla organizacji.

### <a name="in-the-microsoft-365-admin-center"></a>W centrum Administracja Microsoft 365

1. Zaloguj się do [centrum Administracja Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń dla konta administratora w organizacji.

2. W centrum Administracja przejdź do pozycji **Ustawienia** >  ustawienia  > **organizacji**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Zabezpieczenia & dostęp**</a>**uprzywilejowany** prywatności > .

3. Wybierz pozycję **Zarządzaj zasadami dostępu i żądaniami**.

4. Wybierz pozycję **Konfiguruj zasady** i wybierz **pozycję Dodaj zasady**.

5. Z pól listy rozwijanej wybierz odpowiednie wartości dla swojej organizacji:

    **Typ zasad**: Zadanie, Rola lub Grupa ról

    **Zakres zasad**: Exchange

    **Nazwa zasad**: wybierz spośród dostępnych zasad

    **Typ zatwierdzenia**: Ręczne lub Automatyczne

    **Grupa zatwierdzania**: wybierz grupę osób zatwierdzających utworzoną w kroku 1

6. Wybierz pozycję **Utwórz,** a następnie **zamknij**. Pełne skonfigurowanie i włączenie zasad może potrwać kilka minut.

### <a name="in-exchange-management-powershell"></a>W programie PowerShell zarządzania programem Exchange

Aby utworzyć i zdefiniować zasady zatwierdzania, uruchom następujące polecenie w Exchange Online programu PowerShell:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

Przykład:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>Krok 4. Przesyłanie/zatwierdzanie żądań dostępu uprzywilejowanego

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>Żądanie autoryzacji podniesienia uprawnień w celu wykonywania zadań uprzywilejowanych

Żądania dostępu uprzywilejowanego są ważne przez maksymalnie 24 godziny po przesłaniu żądania. Jeśli żądania nie zostaną zatwierdzone lub odmówione, żądania wygasną, a dostęp nie zostanie zatwierdzony.

#### <a name="in-the-microsoft-365-admin-center"></a>W centrum Administracja Microsoft 365

1. Zaloguj się do [centrum Administracja Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń.

2. W centrum Administracja przejdź do pozycji **Ustawienia** >  ustawienia  > **organizacji**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Zabezpieczenia & dostęp**</a>**uprzywilejowany** prywatności > .

3. Wybierz pozycję **Zarządzaj zasadami dostępu i żądaniami**.

4. Wybierz pozycję **Nowe żądanie**. Z pól listy rozwijanej wybierz odpowiednie wartości dla swojej organizacji:

    **Typ żądania**: Zadanie, Rola lub Grupa ról

    **Zakres żądania**: Exchange

    **Żądanie**: wybierz spośród dostępnych zasad

    **Czas trwania (godziny)**: liczba godzin żądanego dostępu. Nie ma limitu liczby godzin, które można zażądać.

    **Komentarze**: pole tekstowe dla komentarzy związanych z żądaniem dostępu

5. Wybierz pozycję **Zapisz** , a następnie **zamknij**. Żądanie zostanie wysłane do grupy osoby zatwierdzającą za pośrednictwem poczty e-mail.

#### <a name="in-exchange-management-powershell"></a>W programie PowerShell zarządzania programem Exchange

Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby utworzyć i przesłać żądanie zatwierdzenia do grupy osoby zatwierdzającą:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

Przykład:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>Wyświetlanie stanu żądań podniesienia uprawnień

Po utworzeniu żądania zatwierdzenia stan żądania podniesienia uprawnień można przejrzeć w centrum administracyjnym lub w programie Exchange Management PowerShell przy użyciu skojarzonego z identyfikatorem żądania.

#### <a name="in-the-microsoft-365-admin-center"></a>W Centrum administracyjne platformy Microsoft 365

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń.

2. W centrum administracyjnym przejdź do pozycji **Ustawienia** > **Ustawienia organizacji Zabezpieczenia** >  &**dostęp uprzywilejowany** <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**prywatności**</a> > .

3. Wybierz pozycję **Zarządzaj zasadami dostępu i żądaniami**.

4. Wybierz pozycję **Widok** , aby filtrować przesłane żądania według **stanu Oczekujące**, **Zatwierdzone**, **Odrzucone** lub **Skrytka klienta** .

#### <a name="in-exchange-management-powershell"></a>W programie PowerShell zarządzania programem Exchange

Uruchom następujące polecenie w programie Exchange Online programu PowerShell, aby wyświetlić stan żądania zatwierdzenia dla określonego identyfikatora żądania:

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

Przykład:

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Zatwierdzanie żądania autoryzacji podniesienia uprawnień

Po utworzeniu żądania zatwierdzenia członkowie odpowiedniej grupy osoby zatwierdzającą otrzymują powiadomienie e-mail i mogą zatwierdzić żądanie skojarzone z identyfikatorem żądania. Żądanie jest powiadamiane o zatwierdzeniu lub odmowie żądania za pośrednictwem wiadomości e-mail.

#### <a name="in-the-microsoft-365-admin-center"></a>W Centrum administracyjne platformy Microsoft 365

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń.

2. W centrum administracyjnym przejdź do pozycji **Ustawienia** > **Ustawienia organizacji Zabezpieczenia** >  &**dostęp uprzywilejowany** <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**prywatności**</a> > .

3. Wybierz pozycję **Zarządzaj zasadami dostępu i żądaniami**.

4. Wybierz wymienione żądanie, aby wyświetlić szczegóły i podjąć działania w żądaniu.

5. Wybierz pozycję **Zatwierdź** , aby zatwierdzić żądanie, lub wybierz pozycję **Odmów** , aby odrzucić żądanie. Wcześniej zatwierdzone żądania mogą mieć dostęp odwołany, wybierając pozycję **Odwołaj**.

#### <a name="in-exchange-management-powershell"></a>W programie PowerShell zarządzania programem Exchange

Aby zatwierdzić żądanie autoryzacji podniesienia uprawnień, uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

Przykład:

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

Aby odrzucić żądanie autoryzacji podniesienia uprawnień, uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

Przykład:

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>Usuwanie zasad dostępu uprzywilejowanego w Office 365

Jeśli nie jest ona już potrzebna w organizacji, możesz usunąć zasady dostępu uprzywilejowanego.

### <a name="in-the-microsoft-365-admin-center"></a>W Centrum administracyjne platformy Microsoft 365

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji.

2. W centrum administracyjnym przejdź do pozycji **Ustawienia** > **Ustawienia organizacji Zabezpieczenia** >  &**dostęp uprzywilejowany** <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**prywatności**</a> > .

3. Wybierz pozycję **Zarządzaj zasadami dostępu i żądaniami**.

4. Wybierz pozycję **Konfiguruj zasady**.

5. Wybierz zasady, które chcesz usunąć, a następnie wybierz pozycję **Usuń zasady**.

6. Wybierz pozycję **Zamknij**.

### <a name="in-exchange-management-powershell"></a>W programie PowerShell zarządzania programem Exchange

Aby usunąć zasady dostępu uprzywilejowanego, uruchom następujące polecenie w programie Exchange Online powershell:

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>Wyłączanie dostępu uprzywilejowanego w Office 365

W razie potrzeby można wyłączyć zarządzanie dostępem uprzywilejowanym dla organizacji. Wyłączenie dostępu uprzywilejowanego nie powoduje usunięcia żadnych skojarzonych zasad zatwierdzania ani grup osób zatwierdzające.

### <a name="in-the-microsoft-365-admin-center"></a>W Centrum administracyjne platformy Microsoft 365

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji.

2. W centrum Administracja przejdź do pozycji **Ustawienia** >  ustawienia  > **organizacji**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Zabezpieczenia & dostęp**</a>**uprzywilejowany** prywatności > .

3. Włącz **opcję Wymagaj zatwierdzeń dla kontroli dostępu uprzywilejowanego** .

### <a name="in-exchange-management-powershell"></a>W programie PowerShell zarządzania programem Exchange

Aby wyłączyć dostęp uprzywilejowany, uruchom następujące polecenie w programie Exchange Online powershell:

```PowerShell
Disable-ElevatedAccessControl
```
