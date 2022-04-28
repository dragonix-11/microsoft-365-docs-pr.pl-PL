---
title: Zarządzanie dostępem uprzywilejowanym dla Microsoft 365 dla środowiska testowego przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: Skorzystaj z tego przewodnika po laboratorium testowym, aby włączyć zarządzanie dostępem uprzywilejowanym Microsoft 365 dla środowiska testowego przedsiębiorstwa.
ms.openlocfilehash: 0c92cbd398e4c388fe3c5999c5e0aa9973c4ee06
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092100"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Zarządzanie dostępem uprzywilejowanym dla Microsoft 365 dla środowiska testowego przedsiębiorstwa

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

W tym artykule opisano sposób konfigurowania zarządzania dostępem uprzywilejowanym w celu zwiększenia zabezpieczeń w Microsoft 365 dla środowiska testowego przedsiębiorstwa.

Konfigurowanie uprzywilejowanego zarządzania dostępem obejmuje trzy fazy:

- [Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Faza 2. Konfigurowanie zarządzania dostępem uprzywilejowanym](#phase-2-configure-privileged-access-management)
- [Faza 3. Sprawdzanie, czy zatwierdzenie jest wymagane w przypadku zadań z podwyższonym poziomem uprawnień i uprzywilejowanych](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz skonfigurować zarządzanie dostępem uprzywilejowanym w sposób uproszczony z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz skonfigurować zarządzanie dostępem uprzywilejowanym w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>Testowanie zarządzania dostępem uprzywilejowanym nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services. Jest ona dostępna w tym miejscu jako opcja umożliwiająca testowanie uprzywilejowanego zarządzania dostępem i eksperymentowanie z nim w środowisku reprezentującym typową organizację.

## <a name="phase-2-configure-privileged-access-management"></a>Faza 2. Konfigurowanie zarządzania dostępem uprzywilejowanym

W tej fazie skonfiguruj grupę osób zatwierdzających i włącz zarządzanie dostępem uprzywilejowanym dla Microsoft 365 dla środowiska testowego przedsiębiorstwa. Aby uzyskać dodatkowe informacje i omówienie zarządzania dostępem uprzywilejowanym, zobacz [Privileged access management (Zarządzanie dostępem uprzywilejowanym](../compliance/privileged-access-management-overview.md)).

Aby skonfigurować dostęp uprzywilejowany i korzystać z niego w organizacji, wykonaj następujące kroki.

#### <a name="step-1-create-an-approvers-group"></a>[Krok 1. Tworzenie grupy osoby zatwierdzającą](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

Przed rozpoczęciem korzystania z dostępu uprzywilejowanego określ, kto będzie miał urząd zatwierdzania dla przychodzących żądań dostępu do zadań z podwyższonym poziomem uprawnień i uprzywilejowanych. Wszyscy użytkownicy należący do grupy Osoby zatwierdzające mogą zatwierdzać żądania dostępu. Aby korzystać z dostępu uprzywilejowanego, należy utworzyć grupę zabezpieczeń z obsługą poczty w Microsoft 365. W środowisku testowym nadaj nowej grupie zabezpieczeń nazwę "Osoby zatwierdzające dostęp uprzywilejowany" i dodaj ciąg "Użytkownik 3", który został wcześniej utworzony w poprzednich krokach przewodnika po laboratorium testowym.

#### <a name="step-2-enable-privileged-access"></a>[Krok 2. Włączanie dostępu uprzywilejowanego](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

Dostęp uprzywilejowany musi być jawnie włączony w Microsoft 365 z domyślną grupą osób zatwierdzającą i musi zawierać zestaw kont systemowych, które mają zostać wykluczone z kontroli dostępu do zarządzania dostępem uprzywilejowanym. Pamiętaj, aby włączyć uprzywilejowany dostęp w organizacji przed rozpoczęciem fazy 3 tego przewodnika.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Faza 3. Sprawdzanie, czy zatwierdzenie jest wymagane w przypadku zadań z podwyższonym poziomem uprawnień i uprzywilejowanych

W tej fazie sprawdź, czy zasady dostępu uprzywilejowanego działają i czy użytkownicy wymagają zatwierdzenia do wykonywania zdefiniowanych zadań z podwyższonym poziomem uprawnień i uprzywilejowanych.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Testowanie możliwości wykonania zadania NIE zdefiniowanego w zasadach dostępu uprzywilejowanego

Najpierw połącz się z programem PowerShell Exchange Management przy użyciu poświadczeń użytkownika skonfigurowanego przy użyciu roli Exchange Role Management w środowisku testowym i spróbuj utworzyć nową regułę dziennika. Zadanie [New-JournalRule](/powershell/module/exchange/new-journalrule) nie jest obecnie zdefiniowane w zasadach dostępu uprzywilejowanego dla organizacji.

1. Na komputerze lokalnym otwórz i zaloguj się do modułu Exchange Online Remote PowerShell w firmie **Microsoft Corporation** >  **Microsoft Exchange Online zdalnego modułu programu PowerShell** przy użyciu poświadczeń z rolą zarządzania rolami Exchange dla środowiska testowego.
2. W programie PowerShell zarządzania Exchange utwórz nową regułę dziennika dla swojej organizacji:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. Wyświetl, że nowa reguła dziennika została pomyślnie utworzona w programie PowerShell zarządzania Exchange.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Tworzenie nowych zasad dostępu uprzywilejowanego dla zadania New-JournalRule

>[!NOTE]
>Jeśli kroki 1 i 2 z fazy 2 tego przewodnika nie zostały jeszcze ukończone, wykonaj kroki, aby utworzyć grupę osoby zatwierdzającą o nazwie "Osoby zatwierdzające dostęp do uprawnień", aby włączyć uprzywilejowany dostęp w środowisku testowym.

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń z rolą Exchange Role Management dla środowiska testowego.
2. W Centrum administracyjnym przejdź do **obszaru Ustawienia** >  **Zabezpieczenia &** prywatnośćUprzywilejowany  > **dostęp**.
3. Wybierz pozycję **Zarządzaj zasadami dostępu i żądaniami**.
4. Wybierz pozycję **Konfiguruj zasady**, a następnie wybierz **pozycję Dodaj zasady**.
5. Z pól listy rozwijanej wybierz lub wprowadź następujące wartości:

    **Typ zasad**: **Zakres zasad** zadań: Exchange **Nazwa zasad**: **Nowy typ zatwierdzenia** reguły dziennika: **Grupa zatwierdzania** ręcznego: Osoby zatwierdzające dostęp uprzywilejowany  

6. Wybierz pozycję **Utwórz**, a następnie wybierz pozycję **Zamknij**. Pełne skonfigurowanie i włączenie zasad może potrwać kilka minut. Przed przetestowaniem wymagania dotyczącego zatwierdzania w następnym kroku należy pozostawić czas na pełne włączenie zasad.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Testowanie wymagań dotyczących zatwierdzania zadania New-JournalRule zdefiniowanego w zasadach dostępu uprzywilejowanego

1. Na komputerze lokalnym otwórz i zaloguj się do modułu Exchange Online Remote PowerShell w firmie **Microsoft Corporation** >  **Microsoft Exchange Online zdalnego modułu programu PowerShell** przy użyciu poświadczeń z rolą zarządzania rolami Exchange dla środowiska testowego.

2. W programie PowerShell zarządzania Exchange utwórz nową regułę dziennika dla swojej organizacji:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Wyświetl błąd "Niewystarczające uprawnienia" w programie PowerShell zarządzania Exchange:

   ```ExchangeManagementPowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Żądanie dostępu w celu utworzenia nowej reguły dziennika przy użyciu zadania New-JournalRule

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń z rolą Exchange Role Management dla środowiska testowego.

2. W Centrum administracyjnym przejdź do **obszaru Ustawienia** >  **Zabezpieczenia &** prywatnośćUprzywilejowany  > **dostęp**.

3. Wybierz pozycję **Zarządzaj zasadami dostępu i żądaniami**.

4. Wybierz pozycję **Nowe żądanie**. Z pól listy rozwijanej wybierz odpowiednie wartości dla swojej organizacji:

    **Typ żądania**: **Zakres żądania** zadania: Exchange **Request dla**: Czas trwania nowej reguły dziennika **(godziny):** 2 **Komentarze**: Żądanie uprawnień do utworzenia nowej reguły dziennika  

5. Wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Zamknij**. Żądanie zostanie wysłane do grupy osoby zatwierdzającą za pośrednictwem poczty e-mail.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Zatwierdzanie żądania dostępu uprzywilejowanego w celu utworzenia nowej reguły dziennika

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń użytkownika 3 w środowisku testowym (członek grupy zabezpieczeń "Osoby zatwierdzające dostęp uprzywilejowany" w środowisku testowym).

2. W Centrum administracyjnym przejdź do **obszaru Ustawienia** >  **Zabezpieczenia &** prywatnośćUprzywilejowany  > **dostęp**.

3. Wybierz pozycję **Zarządzaj zasadami dostępu i żądaniami**.

4. Wybierz oczekujące żądanie, a następnie wybierz pozycję **Zatwierdź** , aby udzielić dostępu do konta użytkownika w celu utworzenia nowej reguły dziennika. Konto (żądający użytkownik) otrzyma wiadomość e-mail z potwierdzeniem udzielenia zatwierdzenia.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Testowanie tworzenia nowej reguły dziennika z uprzywilejowanym dostępem zatwierdzonym dla zadania New-JournalRule

1. Na komputerze lokalnym otwórz i zaloguj się do modułu Exchange Online Remote PowerShell w firmie **Microsoft Corporation** >  **Microsoft Exchange Online zdalnego modułu programu PowerShell** przy użyciu poświadczeń z rolą zarządzania rolami Exchange dla środowiska testowego.

2. W programie PowerShell zarządzania Exchange utwórz nową regułę dziennika dla swojej organizacji:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Wyświetl, że nowa reguła dziennika została pomyślnie utworzona w programie PowerShell zarządzania Exchange.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [ochrony informacji](m365-enterprise-test-lab-guides.md#information-protection) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

- [Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)
- [Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)
- [Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)
