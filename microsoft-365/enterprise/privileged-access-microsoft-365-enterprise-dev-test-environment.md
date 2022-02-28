---
title: Zarządzanie dostępem z uprawnieniami do Microsoft 365 w środowisku testowania przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: Skorzystaj z tego przewodnika po laboratorium testowym, aby włączyć funkcję zarządzania dostępem z Microsoft 365 w środowisku testowania przedsiębiorstwa.
ms.openlocfilehash: 424b7c09a89b20d134654293a1e9c9abd69d6ff2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988370"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Zarządzanie dostępem z uprawnieniami do Microsoft 365 w środowisku testowania przedsiębiorstwa

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

W tym artykule opisano sposób konfigurowania zarządzania dostępem z uprawnieniami w celu zwiększenia bezpieczeństwa Microsoft 365 w środowisku testowania przedsiębiorstwa.

Konfigurowanie zarządzania dostępem uprzywilejowanym obejmuje trzy fazy:

- [Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Etap 2. Konfigurowanie zarządzania dostępem z uprawnieniami](#phase-2-configure-privileged-access-management)
- [Etap 3. Sprawdzanie, czy zatwierdzanie jest wymagane w przypadku zadań o podwyższonym poziomie uprawnień](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz skonfigurować uproszczone zarządzanie dostępem z uprawnieniami przy minimalnym poziomie wymagań, postępuj zgodnie z instrukcjami w [tece Konfiguracja podstawowa.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Jeśli chcesz skonfigurować zarządzanie dostępem z uprawnieniami w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w tece uwierzytelnianie [pass-through](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>Testowanie zarządzania dostępem z uprawnieniami nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów na Usługi domenowe w usłudze Active Directory lasów. Jest ona dostępna jako opcja, która umożliwia testowanie zarządzania dostępem z uprawnieniami i eksperymentowanie z nim w środowisku reprezentującym typową organizację.

## <a name="phase-2-configure-privileged-access-management"></a>Etap 2. Konfigurowanie zarządzania dostępem z uprawnieniami

Na tym etapie skonfiguruj grupę osób zatwierdzających i włącz zarządzanie dostępem uprzywilejowanym na Microsoft 365 w środowisku testowania przedsiębiorstwa. Aby uzyskać dodatkowe informacje i omówienie zarządzania dostępem z uprawnieniami, zobacz [Zarządzanie dostępem z uprawnieniami](../compliance/privileged-access-management-overview.md).

Aby skonfigurować dostęp uprzywilejowany w organizacji i korzystać z niego, wykonaj następujące czynności.

#### <a name="step-1-create-an-approvers-group"></a>[Krok 1. Tworzenie grupy osoby zatwierdzającej](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

Przed rozpoczęciem korzystania z dostępu z uprawnieniami określ, kto będzie miał uprawnienia do zatwierdzania przychodzących żądań dostępu do podwyższonych i uprzywilejowanych zadań. Wszyscy użytkownicy, którzy są częścią grupy Osoby zatwierdzające, mogą zatwierdzać żądania dostępu. Aby korzystać z dostępu z uprawnieniami, musisz utworzyć grupę zabezpieczeń z obsługą poczty w programie Microsoft 365. W środowisku testowym nazwij nową grupę zabezpieczeń "Osoby zatwierdzające dostęp z uprawnieniami" i dodaj "Użytkownik 3" utworzony wcześniej w poprzednich krokach przewodnika laboratorium testowego.

#### <a name="step-2-enable-privileged-access"></a>[Krok 2. Włączanie dostępu z uprawnieniami](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

Dostęp z uprawnieniami musi być jawnie włączony w programie Microsoft 365 z domyślną grupą osób zatwierdzających i musi zawierać zestaw kont systemowych, które chcesz wykluczyć z kontroli dostępu do zarządzania dostępem uprzywilejowanym. Pamiętaj o włączeniu dostępu uprzywilejowanych w organizacji przed rozpoczęciem fazy 3 tego przewodnika.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Etap 3. Sprawdzanie, czy zatwierdzanie jest wymagane w przypadku zadań o podwyższonym poziomie uprawnień

W tej fazie sprawdź, czy zasady dostępu z uprawnieniami działają i czy użytkownicy wymagają zatwierdzenia w celu wykonania zdefiniowanych, podwyższonych i uprzywilejowanych zadań.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Testowanie możliwości wykonywania zadania NIE zdefiniowano w zasadach dostępu z uprawnieniami

Najpierw połącz się z programem PowerShell zarządzania Exchange przy użyciu poświadczeń użytkownika skonfigurowanego przy użyciu roli Zarządzanie rolami Exchange w środowisku testowym i spróbuj utworzyć nową regułę dziennika. Zadanie [New-JournalRule](/powershell/module/exchange/new-journalrule) nie jest obecnie zdefiniowane w zasadach dostępu z uprawnieniami dla organizacji.

1. Na komputerze lokalnym otwórz moduł zdalnej obsługi programu PowerShell usługi Exchange Online i zaloguj się do tego modułu w witrynie **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** przy użyciu poświadczeń z rolą zarządzanie rolami usługi Exchange dla środowiska testowego.
2. W Exchange PowerShell zarządzania utwórz nową regułę dziennika dla organizacji:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. Sprawdź, czy nowa reguła dziennika została pomyślnie utworzona w programie Exchange PowerShell zarządzania.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Tworzenie nowych zasad dostępu z uprawnieniami dla zadania New-JournalRule dostępu

>[!NOTE]
>Jeśli nie ukończono jeszcze kroków 1 i 2 z fazy 2 tego przewodnika, postępuj zgodnie z instrukcjami, aby utworzyć grupę osoby zatwierdzającej o nazwie "Osoby zatwierdzające dostęp uprawnień", aby włączyć dostęp uprzywilejowany w środowisku testowym.

1. Zaloguj się do bazy [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń za pomocą Exchange Zarządzanie rolami w środowisku testowym.
2. W Centrum administracyjnym przejdź **do Ustawienia** >  **Zabłędy &** **Privileged** >  access.
3. Wybierz **pozycję Zarządzaj zasadami dostępu i żądaniami dostępu**.
4. Wybierz **pozycję Konfiguruj zasady**, a następnie **wybierz pozycję Dodaj zasady**.
5. Z pola listy rozwijanej wybierz lub wprowadź następujące wartości:

    **Typ zasad**: Zakres **zasad zadań**: Exchange Nawiązy **administracyjne: Nowy** typ zatwierdzania reguły **dziennika: grupa** Zatwierdzanie **ręczne: Osoby** zatwierdzające dostęp z uprawnieniami  

6. Wybierz **pozycję Utwórz**, a następnie wybierz **pozycję Zamknij**. Pełne skonfigurowanie i włączeniu zasad może potrwać kilka minut. Przed przetestowaniem wymagania zatwierdzenia w następnym kroku należy zezwolić na pełne włączono zasady.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Test approval requirement for the New-JournalRule defined in a privileged access policy

1. Na komputerze lokalnym otwórz moduł zdalnej obsługi programu PowerShell usługi Exchange Online i zaloguj się do tego modułu w witrynie **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** przy użyciu poświadczeń z rolą zarządzanie rolami usługi Exchange dla środowiska testowego.

2. W Exchange PowerShell zarządzania utwórz nową regułę dziennika dla organizacji:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Wyświetlanie błędu "Za mało uprawnień" w programie PowerShell Exchange zarządzania:

   ```ExchangeManagementPowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Żądanie dostępu do utworzenia nowej reguły dziennika przy użyciu New-JournalRule dziennika

1. Zaloguj się do bazy [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń za pomocą Exchange Zarządzanie rolami w środowisku testowym.

2. W Centrum administracyjnym przejdź **do Ustawienia** >  **Zabłędy &** **Privileged** >  access.

3. Wybierz **pozycję Zarządzaj zasadami dostępu i żądaniami dostępu**.

4. Wybierz **pozycję Nowa prośba**. Z pól rozwijanych wybierz odpowiednie wartości dla organizacji:

    **Typ żądania**: Zakres **żądania zadania**: Exchange Określanie **o: Czas** trwania reguły dziennika **(godziny)**: 2 **Komentarze**: żądanie uprawnień do utworzenia nowej reguły dziennika  

5. Wybierz **pozycję Zapisz**, a następnie wybierz **pozycję Zamknij**. Twój wniosek zostanie wysłany do grupy osoby zatwierdzającej pocztą e-mail.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Zatwierdzanie żądania dostępu z uprawnieniami do utworzenia nowej reguły dziennika

1. Zaloguj się [do centrum administracyjne platformy Microsoft 365 przy](https://admin.microsoft.com) użyciu poświadczeń użytkownika 3 w środowisku testowym (członek grupy zabezpieczeń "Osoby zatwierdzające dostęp z uprawnieniami" w środowisku testowym).

2. W Centrum administracyjnym przejdź **do Ustawienia** >  **Zabłędy &** **Privileged** >  access.

3. Wybierz **pozycję Zarządzaj zasadami dostępu i żądaniami dostępu**.

4. Wybierz oczekujące żądanie, a następnie **wybierz pozycję** Zatwierdź, aby udzielić dostępu do konta użytkownika w celu utworzenia nowej reguły dziennika. Konto (użytkownik żądający) otrzyma wiadomość e-mail z potwierdzeniem, że zatwierdzenie zostało udzielone.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Testowanie tworzenia nowej reguły dziennika z dostępem z uprawnieniami zatwierdzonego dla New-JournalRule dziennika

1. Na komputerze lokalnym otwórz moduł zdalnej obsługi programu PowerShell usługi Exchange Online i zaloguj się do tego modułu w witrynie **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** przy użyciu poświadczeń z rolą zarządzanie rolami usługi Exchange dla środowiska testowego.

2. W Exchange PowerShell zarządzania utwórz nową regułę dziennika dla organizacji:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Sprawdź, czy nowa reguła dziennika została pomyślnie utworzona w programie Exchange PowerShell zarządzania.

## <a name="next-step"></a>Następny krok

Poznaj dodatkowe [funkcje i możliwości](m365-enterprise-test-lab-guides.md#information-protection) ochrony informacji w środowisku testowym.

## <a name="see-also"></a>Zobacz też

- [Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)
- [Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)
- [Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)
