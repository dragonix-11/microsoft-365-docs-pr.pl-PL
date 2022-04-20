---
title: Konfigurowanie harmonogramu dla Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Konfigurowanie harmonogramu dla Microsoft 365.
ms.openlocfilehash: ef377393134e4d8028ab0e6e40ddcc3647f60695
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953853"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Konfigurowanie harmonogramu dla platformy Microsoft 365

Administratorzy dzierżawy muszą skonfigurować skrzynkę pocztową asystenta harmonogramu i uzyskać licencje harmonogramu dla organizatorów spotkań, aby włączyć usługę Scheduler dla usługi Microsoft 365. 

## <a name="licensing"></a>Licencjonowanie

Dowiedz się więcej: [Harmonogram licencjonowania Microsoft 365](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!NOTE]
> Uczestnicy spotkania nie potrzebują licencji harmonogramu ani licencji Microsoft 365.
>
> Skrzynka pocztowa asystenta harmonogramu nie wymaga licencji Microsoft 365 ani harmonogramu.

## <a name="prerequisites"></a>Wymagania wstępne

|Wymagania wstępne|Opis|
|---|---|
|Skrzynka pocztowa asystenta harmonogramu dla dzierżawy |Skrzynka pocztowa zasobu typu sprzętu Exchange, która działa jako skrzynka pocztowa asystenta harmonogramu dla dzierżawy do wysyłania i odbierania wiadomości e-mail do i z Cortana. Wszystkie wiadomości e-mail wysyłane do Cortana są przechowywane w skrzynce pocztowej Cortana dzierżawy na podstawie zasad przechowywania. Skrzynka pocztowa asystenta harmonogramu jest zwykle nazywana "Cortana" lub "Cortana Scheduler", ponieważ wszystkie wiadomości e-mail od asystenta zostaną podpisane Cortana. <ul><li>Tworzenie skrzynki pocztowej zasobu typu sprzętu Exchange</li><li>Nadaj skrzynce pocztowej nazwę wyświetlaną i podstawowy adres `Cortana <cortana@yourdomain.com>` SMTP lub `Cortana Scheduler <cortana.scheduler@yourdomain.com>`.</li></ul> <br/> **Uwaga:** Skrzynka pocztowa asystenta harmonogramu nie wymaga licencji Microsoft 365 ani harmonogramu.|
|skrzynka pocztowa Exchange Online |Organizatorzy spotkań muszą mieć Exchange Online skrzynkę pocztową i kalendarz zazwyczaj w ramach licencji Microsoft 365. Ponadto organizatorzy spotkań muszą mieć licencję harmonogramu. Licencja harmonogramu umożliwia asystentowi harmonogramu korzystanie ze skrzynki pocztowej i kalendarza organizatora spotkania w celu zaplanowania dla nich spotkań. <br/><br/> Zobacz Harmonogram, aby uzyskać Microsoft 365, aby uzyskać informacje o licencjonowaniu i cenach. <br/><br/> **Uwaga:** Uczestnicy spotkania nie potrzebują licencji harmonogramu ani licencji Microsoft 365. Uczestnicy spotkania mogą być wewnętrzni lub zewnętrzni dla dzierżawy. Uczestnicy spotkania potrzebują tylko dostępu do adresu e-mail.|

## <a name="setting-up-the-scheduler-assistant-mailbox"></a>Konfigurowanie skrzynki pocztowej asystenta harmonogramu

Skrzynka pocztowa asystenta harmonogramu to skrzynka pocztowa typu sprzętu Exchange, która nie wymaga dodatkowej licencji Microsoft 365 ani harmonogramu. Nazwa wyświetlana i podstawowy adres SMTP skrzynki pocztowej powinny zawierać Cortana, ponieważ wszystkie wiadomości e-mail z asystenta harmonogramu zostaną podpisane Cortana (tj. `Cortana <cortana@yourdomain.com>` lub `Cortana Scheduler <cortana.scheduler@yourdomain.com>`). Po utworzeniu skrzynki pocztowej asystenta harmonogramu należy wyznaczyć skrzynkę pocztową jako skrzynkę pocztową asystenta harmonogramu. Po wyznaczeniu skrzynki pocztowej asystenta harmonogramu Cortana będą dostępne do planowania spotkań w imieniu użytkowników.

- Użyj Centrum administracyjne platformy Microsoft 365, aby utworzyć skrzynkę pocztową użytkownika. Zalecane są 30-dniowe zasady przechowywania. 
- Użyj nazwy Cortana w podstawowym adresie SMTP skrzynki pocztowej. Zalecane są nazwy, takie jak `Cortana@yourdomain.com`, `CortanaScheduler@contoso.com`lub `Cortana.Scheduler@yourdomain.com` .

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Wyznaczanie skrzynki pocztowej jako Asystenta harmonogramu

Po utworzeniu unikatowej skrzynki pocztowej dla usługi Cortana Scheduler należy wyznaczyć skrzynkę pocztową do Microsoft 365 formalnie. Po wyznaczeniu skrzynki pocztowej usługi Cortana Scheduler będzie ona dostępna do planowania spotkań w imieniu użytkowników.

### <a name="connect-to-powershell"></a>Połączenie do programu PowerShell

Użyj Centrum administracyjne platformy Microsoft 365, aby utworzyć skrzynkę pocztową użytkownika. Zalecane są 30-dniowe zasady przechowywania.
Użyj nazwy Cortana w podstawowym adresie SMTP skrzynki pocztowej. Zalecane są nazwy, takie jak `Cortana@yourdomain.com`, `CortanaScheduler@contoso.com`lub `Cortana.Scheduler@yourdomain.com` .

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

### <a name="create-the-scheduler-assistant-mailbox"></a>Tworzenie skrzynki pocztowej Asystenta harmonogramu

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```

### <a name="designate-the-scheduler-assistant-mailbox"></a>Wyznaczanie skrzynki pocztowej asystenta harmonogramu

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

Po uruchomieniu tego polecenia "set" w skrzynce pocztowej asystenta harmonogramu Cortana w skrzynce pocztowej ustawiono nową wartość "PersistedCapability", aby pamiętać, że ta skrzynka pocztowa to "SchedulerAssistant".

> [!NOTE]
> Aby dowiedzieć się, jak połączyć organizację z programem PowerShell, zobacz: [Połączenie do Microsoft 365 za pomocą programu PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>Weryfikowanie skrzynki pocztowej asystenta harmonogramu

Aby sprawdzić, czy została utworzona skrzynka pocztowa asystenta harmonogramu

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

Wynik powinien mieć wartość "false".

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

Wynik powinien być

- ResourceType: Sprzęt
- Typ adresata zdalnego: brak
- Typ odbiorcy: UserMailbox
- RecipientTypeDetails: EquipmentMailbox

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>Aby dowiedzieć się, która skrzynka pocztowa jest skrzynką pocztową asystenta harmonogramu

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!IMPORTANT]
> Pełne aprowizowanie w skrzynce pocztowej asystenta harmonogramu może potrwać kilka godzin, aby ustawić funkcję SchedulerAssistant.

## <a name="exchange-online-mailbox"></a>skrzynka pocztowa Exchange Online

Licencja harmonogramu to dodatek do Microsoft 365, który umożliwia organizatorowi spotkania delegowanie zadań planowania spotkań do asystenta harmonogramu. Oprócz wyznaczenia skrzynki pocztowej jako skrzynki pocztowej asystenta harmonogramu, organizatorzy spotkań będą również potrzebować licencji harmonogramu i Exchange Online skrzynki pocztowej i kalendarza, zazwyczaj za pośrednictwem licencji Microsoft 365, aby harmonogram działał. Uczestnicy spotkania nie potrzebują licencji harmonogramu ani licencji Microsoft 365.

Aby kupić dodatek Scheduler, potrzebujesz jednej z następujących licencji:

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, business Premium
- licencja Exchange Online plan 1 lub plan 2.

> [!NOTE]
> Harmonogram Microsoft 365 jest dostępny tylko w środowiskach wielodostępnych na całym świecie w języku angielskim. **Harmonogram Microsoft 365** nie jest dostępny dla użytkowników:
>
> - Microsoft 365 obsługiwany przez firmę 21Vianet w Chinach
> - Microsoft 365 z chmurą niemiecką korzystającą z niemieckiego telekomu będącego powiernikiem danych
> - Chmura dla instytucji rządowych, w tym GCC, consumer, GCC High lub DoD
>
> Usługa Scheduler obsługuje użytkowników w Niemczech, których lokalizacja danych nie jest niemieckim centrum danych.
