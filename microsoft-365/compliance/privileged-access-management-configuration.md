---
title: Wprowadzenie do zarządzania dostępem z uprawnieniami
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
description: Skorzystaj z tego artykułu, aby dowiedzieć się więcej o włączaniu i konfigurowaniu zarządzania dostępem z uprawnieniami w programie Office 365.
ms.openlocfilehash: fd7216b09b17f7f900a9aee98059918a1796fe19
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2022
ms.locfileid: "63009781"
---
# <a name="get-started-with-privileged-access-management"></a>Wprowadzenie do zarządzania dostępem z uprawnieniami

Ten temat przeprowadzi Cię przez proces włączania i konfigurowania funkcji zarządzania dostępem z uprawnieniami w organizacji. Do zarządzania dostępem centrum administracyjne platformy Microsoft 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank"></a> lub zarządzania Exchange PowerShell można użyć programu PowerShell zarządzania uprawnieniami.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem pracy z zarządzaniem dostępem z uprawnieniami należy potwierdzić subskrypcję usługi [Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) i wszelkie dodatki. Aby można było uzyskać dostęp do zarządzania dostępem z uprawnieniami i korzystać z niego, organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- Microsoft 365 E5 (płatna lub próbna)
- Microsoft 365 E3 (lub Office 365 E3 + Enterprise Mobility and Security E3) + Zgodność platformy Microsoft 365 E5
- Dowolna Microsoft 365, Office 365, Exchange, SharePoint lub OneDrive dla Firm subskrypcji + Microsoft 365 E5 zarządzanie ryzykiem w niejawnym programie testów
- Microsoft 365 A5 (płatna lub próbna)
- Microsoft 365 A3 (lub Office 365 A3 + Enterprise Mobility and Security A3) + dodatek microsoft A5 compliance
- Wszelkie Microsoft 365, Office 365, Exchange, SharePoint lub OneDrive dla edukacji + dodatek Microsoft 365 A5 Insider Risk Management
- Office 365 Enterprise E5 (płatna lub próbna)
- Office 365 Enterprise E3 + Office 365 Advanced Compliance (nie jest już dostępna dla nowych subskrypcji, zobacz uwagę)

Użytkownicy przesyłający żądania zarządzania dostępem z uprawnieniami i odpowiadający na nie muszą mieć przypisaną jedną z powyższych licencji.

> [!IMPORTANT]
> Office 365 Advanced Compliance jest już sprzedawana jako subskrypcja autonomiczna. Gdy wygasają bieżące subskrypcje, klienci powinni przejść do jednej z powyższych subskrypcji, która zawiera takie same lub dodatkowe funkcje zgodności.

Jeśli nie masz jeszcze planu Office 365 Enterprise E5 i chcesz wypróbować zarządzanie dostępem uprzywilejowanym, możesz dodać usługę [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) do istniejącej subskrypcji usługi Office 365 lub utworzyć konto w celu uzyskania wersji próbnej usługi Microsoft 365 Enterprise E5.[](https://www.microsoft.com/microsoft-365/enterprise)

## <a name="enable-and-configure-privileged-access-management"></a>Włączanie i konfigurowanie zarządzania dostępem z uprawnieniami

Wykonaj poniższe czynności, aby skonfigurować dostęp z uprawnieniami w organizacji i korzystać z niego:

- [Krok 1. Tworzenie grupy osoby zatwierdzającej](privileged-access-management-configuration.md#step1)

    Przed rozpoczęciem korzystania z dostępu uprawnień określ, kto potrzebuje uprawnień do zatwierdzania przychodzących żądań dostępu do podwyższonych i uprzywilejowanych zadań. Każdy użytkownik, który należy do grupy Osoby zatwierdzające, może zatwierdzać żądania dostępu. Tę grupę można włączyć, tworząc grupę zabezpieczeń z obsługą poczty w programie Office 365.

- [Krok 2. Włączanie dostępu z uprawnieniami](privileged-access-management-configuration.md#step2)

    Dostęp z uprawnieniami musi być jawnie włączony w programie Office 365 z domyślną grupą osób zatwierdzających, łącznie z zestawem kont systemowych, które mają zostać wykluczone z kontroli dostępu do zarządzania dostępem z uprawnieniami.

- [Krok 3. Tworzenie zasad dostępu](privileged-access-management-configuration.md#step3)

    Utworzenie zasad zatwierdzania umożliwia zdefiniowanie określonych wymagań zatwierdzania określonych dla poszczególnych zadań. Opcje typu zatwierdzenia to **Automatycznie lub** **Ręcznie**.

- [Krok 4. Przesyłanie/zatwierdzanie żądań dostępu z uprawnieniami](privileged-access-management-configuration.md#step4)

    Po włączeniu dostęp z uprawnieniami wymaga zatwierdzenia dla każdego zadania, które ma zdefiniowane skojarzone zasady zatwierdzania. W przypadku zadań zawartych w zasadach zatwierdzania użytkownicy muszą zażądać zatwierdzenia dostępu i uzyskać do niego uprawnienia niezbędne do wykonania zadania.

Po zatwierdzeniu użytkownik żądający może wykonać odpowiednie zadanie, a dostęp uprzywilejowany autoryzowa i wykonuje zadanie w jego imieniu. Zatwierdzenie jest ważne przez żądany czas trwania (domyślny czas trwania wynosi 4 godziny), podczas którego żądany może wykonywać zamierzony zadaniu wiele razy. Wszystkie takie wykonania są rejestrowane i udostępniane na inspekcję zabezpieczeń i zgodności.

> [!NOTE]
> Jeśli chcesz użyć programu PowerShell do zarządzania usługą Exchange w celu włączenia i skonfigurowania dostępu uprzywilejowanych, postępuj zgodnie z instrukcjami w programie Połączenie, aby program [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) przy użyciu uwierzytelniania wieloskładnikowego łączył się z programem Exchange Online PowerShell za pomocą poświadczeń Office 365. Nie musisz włączać uwierzytelniania wieloskładnikowego dla organizacji, aby umożliwić dostęp uprzywilejowany podczas nawiązywania połączenia z programem Exchange Online PowerShell. Nawiązanie połączenia za pomocą uwierzytelniania wieloskładnikowego powoduje utworzenie tokenu uwierzytelniania używanego przez uprawnienia dostępu do podpisywania Twoich żądań.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>Krok 1. Tworzenie grupy osoby zatwierdzającej

1. Zaloguj się do [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji.

2. W centrum administracyjnym przejdź do pozycji **GrupyDdowaj**<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a> >  grupę.

3. Wybierz **grupę zabezpieczeń z obsługą poczty**, a następnie wypełnij pola **Nazwa**, **Grupowy adres e-mail** i Opis dla nowej grupy.

4. Zapisz grupę. Może mi potrwać kilka minut, aby grupa była w pełni skonfigurowana i była wyświetlana w centrum administracyjne platformy Microsoft 365.

5. Wybierz grupę nowej osoby zatwierdzającej i wybierz **pozycję Edytuj,** aby dodać użytkowników do grupy.

6. Zapisz grupę.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>Krok 2. Włączanie dostępu z uprawnieniami

### <a name="in-the-microsoft-365-admin-center"></a>W Administracja Microsoft 365 klienta

1. Zaloguj się do [centrum Administracja Microsoft 365 przy](https://admin.microsoft.com) użyciu poświadczeń konta administratora w organizacji.

2. W centrum administracyjnym przejdź do strony **Ustawienia** >  **Org Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access.

3. Włącz **kontrolkę Wymagaj zatwierdzania dla zadań uprzywilejowanych** .

4. Przypisz grupę osoby zatwierdzającej utworzoną w kroku 1 jako **grupę Osoby** zatwierdzające domyślnie.

5. **Zapisz** i **zamknij**.

### <a name="in-exchange-management-powershell"></a>W Exchange PowerShell do zarządzania danymi

Aby włączyć dostęp uprzywilejowany i przypisać grupę osoby zatwierdzającej, uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

Przykład:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', 'sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Funkcja kont systemowych jest dostępna w celu zapewnienia, że pewne automatyzacje w Twojej organizacji mogą działać bez zależności od dostępu uprzywilejowanych, jednak zalecane jest, aby takie wykluczenia były wyjątkowe i dozwolone były regularnie zatwierdzane i sprawdzane.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>Krok 3. Tworzenie zasad dostępu

Możesz utworzyć i skonfigurować maksymalnie 30 zasad dostępu uprzywilejowanych dla organizacji.

### <a name="in-the-microsoft-365-admin-center"></a>W Administracja Microsoft 365 klienta

1. Zaloguj się do [centrum Administracja Microsoft 365 przy](https://admin.microsoft.com) użyciu poświadczeń konta administratora w organizacji.

2. W Centrum administracyjnym przejdź **do Ustawienia** >  **Org Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access.

3. Wybierz **pozycję Zarządzaj zasadami dostępu i żądaniami dostępu**.

4. Wybierz **pozycję Konfiguruj zasady** i **wybierz pozycję Dodaj zasady**.

5. Z pól rozwijanych wybierz odpowiednie wartości dla organizacji:

    **Typ zasad**: Zadanie, Rola lub Grupa ról

    **Zakres zasad**: Exchange

    **Nazwa zasad**: wybierz jedną z dostępnych zasad

    **Typ zatwierdzenia**: Ręcznie lub Automatycznie

    **Grupa Zatwierdzanie**: Wybierz grupę osób zatwierdzających utworzoną w kroku 1

6. Wybierz **pozycję Utwórz** , a następnie **pozycję Zamknij**. Pełne skonfigurowanie i włączeniu zasad może potrwać kilka minut.

### <a name="in-exchange-management-powershell"></a>W Exchange PowerShell do zarządzania danymi

Aby utworzyć i zdefiniować zasady zatwierdzania, uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

Przykład:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>Krok 4. Przesyłanie/zatwierdzanie żądań dostępu z uprawnieniami

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>Żądanie autoryzacji podwyższenia w celu wykonywania zadań uprzywilejowanych

Żądania dostępu z uprawnieniami są ważne do 24 godzin po przesłaniu żądania. Jeśli żądania nie zostały zatwierdzone lub odrzucone, wygasają i nie są zatwierdzane.

#### <a name="in-the-microsoft-365-admin-center"></a>W Administracja Microsoft 365 klienta

1. Zaloguj się do [centrum Administracja Microsoft 365 przy](https://admin.microsoft.com) użyciu poświadczeń.

2. W Centrum administracyjnym przejdź **do Ustawienia** >  **Org Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access.

3. Wybierz **pozycję Zarządzaj zasadami dostępu i żądaniami dostępu**.

4. Wybierz **pozycję Nowa prośba**. Z pól rozwijanych wybierz odpowiednie wartości dla organizacji:

    **Typ żądania**: Zadanie, Rola lub Grupa ról

    **Zakres żądania**: Exchange

    **Żądanie:** Wybierz jedną z dostępnych zasad

    **Czas trwania (godziny)**: liczba godzin żądanego dostępu. Nie ma ograniczenia liczby godzin, o które można poprosić.

    **Komentarze**: pole tekstowe na komentarze związane z twoim żądaniem dostępu

5. Wybierz **pozycję Zapisz,** a następnie **zamknij**. Twój wniosek zostanie wysłany do grupy osoby zatwierdzającej pocztą e-mail.

#### <a name="in-exchange-management-powershell"></a>W Exchange PowerShell do zarządzania danymi

Uruchom następujące polecenie w programie Exchange Online PowerShell, aby utworzyć i przesłać żądanie zatwierdzenia do grupy osoby zatwierdzającej:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

Przykład:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>Wyświetlanie stanu żądań podwyższenia

Po utworzeniu żądania zatwierdzenia stan żądania podwyższenia można sprawdzić w centrum administracyjnym lub w programie PowerShell zarządzania Exchange przy użyciu skojarzonego z identyfikatorem żądania.

#### <a name="in-the-microsoft-365-admin-center"></a>W centrum administracyjne platformy Microsoft 365

1. Zaloguj się do [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń.

2. W centrum administracyjnym przejdź do strony **Ustawienia** >  **Org Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access.

3. Wybierz **pozycję Zarządzaj zasadami dostępu i żądaniami dostępu**.

4. Wybierz **pozycję Wyświetl,** aby filtrować przesłane żądania według **stanu Oczekujące**, **Zatwierdzone**, **Odrzucone** lub **Skrytka klienta** .

#### <a name="in-exchange-management-powershell"></a>W Exchange PowerShell do zarządzania danymi

Uruchom następujące polecenie w programie Exchange Online PowerShell, aby wyświetlić stan żądania zatwierdzenia dla określonego identyfikatora żądania:

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

Przykład:

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Zatwierdzanie żądania autoryzacji podwyższenia

Po utworzeniu wniosku o zatwierdzenie członkowie odpowiedniej grupy osób zatwierdzających otrzymają powiadomienie e-mail i będą mieć możliwość zatwierdzenia wniosku skojarzonego z identyfikatorem wniosku. Żądające są powiadamiane o zatwierdzeniu żądania lub odmowę w wiadomości e-mail.

#### <a name="in-the-microsoft-365-admin-center"></a>W centrum administracyjne platformy Microsoft 365

1. Zaloguj się do [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń.

2. W centrum administracyjnym przejdź do strony **Ustawienia** >  **Org Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access.

3. Wybierz **pozycję Zarządzaj zasadami dostępu i żądaniami dostępu**.

4. Wybierz wymienione żądanie, aby wyświetlić szczegóły i podjąć działanie w związku z żądaniem.

5. Wybierz **pozycję Zatwierdź** , aby zatwierdzić wniosek, lub pozycję **Odmów** , aby odrzucić wniosek. Poprzednio zatwierdzone żądania mogą mieć cofnięty dostęp, wybierając pozycję **Odwołaj**.

#### <a name="in-exchange-management-powershell"></a>W Exchange PowerShell do zarządzania danymi

Aby zatwierdzić żądanie autoryzacji podwyższenia, uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

Przykład:

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

Aby odrzucić żądanie autoryzacji podwyższenia, uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

Przykład:

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>Usuwanie zasad dostępu z uprawnieniami w programie Office 365

Jeśli nie jest już potrzebny w organizacji, możesz usunąć zasady dostępu z uprawnieniami.

### <a name="in-the-microsoft-365-admin-center"></a>W centrum administracyjne platformy Microsoft 365

1. Zaloguj się do [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji.

2. W centrum administracyjnym przejdź do strony **Ustawienia** >  **Org Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access.

3. Wybierz **pozycję Zarządzaj zasadami dostępu i żądaniami dostępu**.

4. Wybierz **pozycję Konfiguruj zasady**.

5. Wybierz zasady, które chcesz usunąć, a następnie wybierz **pozycję Usuń zasady**.

6. Wybierz pozycję **Zamknij**.

### <a name="in-exchange-management-powershell"></a>W Exchange PowerShell do zarządzania danymi

Aby usunąć zasady dostępu z uprawnieniami, uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>Wyłączanie dostępu z uprawnieniami w programie Office 365

W razie potrzeby możesz wyłączyć zarządzanie dostępem uprzywilejowanym dla organizacji. Wyłączenie dostępu uprzywilejowanych nie powoduje usunięcia żadnych skojarzonych zasad zatwierdzania ani grup osób zatwierdzających.

### <a name="in-the-microsoft-365-admin-center"></a>W centrum administracyjne platformy Microsoft 365

1. Zaloguj się do [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji.

2. W Centrum administracyjnym przejdź **do Ustawienia** >  **Org Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access.

3. Włącz ustawienie **Wymagaj zatwierdzania dla kontroli dostępu z uprawnieniami** .

### <a name="in-exchange-management-powershell"></a>W Exchange PowerShell do zarządzania danymi

Aby wyłączyć dostęp z uprawnieniami, uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Disable-ElevatedAccessControl
```
