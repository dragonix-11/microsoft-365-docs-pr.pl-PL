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
ms.openlocfilehash: 3315c362a6e6ae1eb4fa9bf54d388a89dd667136
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988367"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Konfigurowanie harmonogramu dla Microsoft 365

Administratorzy dzierżawy muszą skonfigurować skrzynkę pocztową asystenta harmonogramu i uzyskać licencje programu Scheduler dla organizatorów spotkań, aby włączyć program Scheduler dla Microsoft 365 usługi. 

## <a name="licensing"></a>Licencjonowanie

Dowiedz się więcej: [Program Scheduler Microsoft 365 licencjonowania](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!Note]
> Uczestnicy spotkania nie potrzebują programu Scheduler Microsoft 365 licencji. <br>Skrzynka pocztowa asystenta harmonogramu nie wymaga Microsoft 365 ani licencji programu Scheduler.

## <a name="prerequisites"></a>Wymagania wstępne

| Wymagania wstępne | Opis |
|-------------------|-------------|
|Skrzynka pocztowa asystenta harmonogramu dla dzierżawy |Skrzynka Exchange zasobu typu sprzętu pełniąca rolę skrzynki pocztowej asystenta harmonogramu dla dzierżawy w celu wysyłania i odbierania wiadomości e-mail z i do Cortana. Wszystkie wiadomości e-mail Cortana są zachowywane w skrzynce Cortana dzierżawy na podstawie zasad przechowywania. Skrzynka pocztowa asystenta harmonogramu ma zazwyczaj nazwę "Cortana" lub "Cortana Scheduler", ponieważ wszystkie wiadomości e-mail od asystenta zostaną podpisane Cortana.<ul><li>Tworzenie typu sprzętu w skrzynce Exchange zasobów</li><li>Nazwij nazwę wyświetlaną skrzynki pocztowej oraz podstawowy adres SMTP lub `Cortana <cortana@yourdomain.com>` `Cortana Scheduler <cortana.scheduler@yourdomain.com>`.</li></ul>**Uwaga:** Skrzynka pocztowa asystenta harmonogramu nie wymaga Microsoft 365 ani licencji programu Scheduler.|
|Exchange Online skrzynki pocztowej |Organizatorzy spotkań muszą mieć skrzynkę Exchange Online pocztową i kalendarz zazwyczaj w ramach Microsoft 365 kalendarza. Ponadto organizatorzy spotkań muszą mieć licencję programu Scheduler. Licencja Scheduler umożliwia asystentowi programu Scheduler planowanie spotkań za pomocą skrzynki pocztowej i kalendarza organizatora spotkania.<br/><br/> Zobacz Scheduler, aby Microsoft 365 informacje o licencjach i cenach.  <br/><br/>**Uwaga:** Uczestnicy spotkania nie potrzebują programu Scheduler Microsoft 365 licencji. Uczestnicy spotkania mogą być wewnętrzni lub zewnętrzni w  urządzeniem dzierżawy. Uczestnicy spotkania potrzebują dostępu tylko do adresu e-mail.|


## <a name="setting-up-the-scheduler-assistant-mailbox"></a>Konfigurowanie skrzynki pocztowej asystenta harmonogramu

Skrzynka pocztowa asystenta harmonogramu Exchange skrzynką pocztową typu sprzętu, która nie wymaga dodatkowej Microsoft 365 ani licencji programu Scheduler. Nazwa wyświetlana i podstawowy adres SMTP skrzynki pocztowej powinny zawierać protokół Cortana, ponieważ wszystkie wiadomości e-mail za pomocą asystenta harmonogramu będą podpisane jako Cortana ( `Cortana <cortana@yourdomain.com>` np. lub `Cortana Scheduler <cortana.scheduler@yourdomain.com>`). Po utworzeniu skrzynki pocztowej asystenta harmonogramu należy wyznaczyć skrzynkę pocztową asystenta harmonogramu. Po wyznaczeniu skrzynki pocztowej asystenta harmonogramu Cortana dostępne do planowania spotkań w imieniu użytkowników.

- Użyj centrum administracyjne platformy Microsoft 365, aby utworzyć skrzynkę pocztową użytkownika. Zalecane są 30-dniowe zasady przechowywania. 
- Użyj nazwy Cortana podstawowym adresu SMTP skrzynki pocztowej. Nazwy, takie jak `Cortana@yourdomain.com`, `CortanaScheduler@contoso.com`lub są `Cortana.Scheduler@yourdomain.com` zalecane.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Wyznaczanie skrzynki pocztowej na asystenta harmonogramu

Po utworzeniu unikatowej skrzynki pocztowej Cortana Scheduler należy wyznaczyć skrzynkę pocztową do formalnego Microsoft 365. Po wyznaczeniu skrzynki Cortana Scheduler będzie ona dostępna do planowania spotkań w imieniu użytkowników.

#### <a name="connect-to-powershell"></a>Połączenie do programu PowerShell

Użyj centrum administracyjne platformy Microsoft 365, aby utworzyć skrzynkę pocztową użytkownika. Zalecane są 30-dniowe zasady przechowywania.
Użyj nazwy Cortana podstawowym adresu SMTP skrzynki pocztowej. Nazwy, takie jak `Cortana@yourdomain.com`, `CortanaScheduler@contoso.com`lub są `Cortana.Scheduler@yourdomain.com` zalecane.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

#### <a name="create-the-scheduler-assistant-mailbox"></a>Tworzenie skrzynki pocztowej asystenta harmonogramu

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```
    
#### <a name="designate-the-scheduler-assistant-mailbox"></a>Wyznaczanie skrzynki pocztowej asystenta harmonogramu

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

Po uruchomieniu tego polecenia "set" w skrzynce pocztowej asystenta programu Cortana Scheduler dla skrzynki pocztowej jest ustawiana nowa wartość "PersistedCapability", aby można było zauważyć, że ta skrzynka pocztowa to "SchedulerAssistant".

> [!Note]
> Aby dowiedzieć się, jak połączyć organizację z programem PowerShell, zobacz: Połączenie się z Microsoft 365 [programem PowerShell.](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>Weryfikowanie skrzynki pocztowej asystenta harmonogramu

Aby sprawdzić, czy została utworzona skrzynka pocztowa asystenta harmonogramu

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

Wynik powinien być "fałsz".

<br>

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

Wynik powinien być
- ResourceType: Equipment
- Remote RecipientType: None
- RecipientType (Typ adresata): UserMailbox
- RecipientTypeDetails: EquipmentMailbox

<br/>

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>Aby dowiedzieć się, która skrzynka pocztowa jest skrzynką pocztową asystenta harmonogramu

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!Important]
> Pełne inicjowanie obsługi administracyjnej w celu ustawienia funkcji SchedulerAssistant przez skrzynkę pocztową asystenta harmonogramu może potrwać kilka godzin.


## <a name="exchange-online-mailbox"></a>Exchange Online skrzynki pocztowej

Licencja programu Scheduler jest dodatku do programu Microsoft 365, który umożliwia organizatorowi spotkania delegowanie zadań planowania spotkania do asystenta harmonogramu. Oprócz wyznaczania skrzynki pocztowej jako skrzynki pocztowej asystenta harmonogramu organizatorzy spotkań muszą również mieć licencję programu Scheduler oraz skrzynkę pocztową i kalendarz programu Exchange Online, zazwyczaj za pośrednictwem programu Microsoft 365, aby program Scheduler działał. Uczestnicy spotkania nie potrzebują licencji programu Scheduler ani Microsoft 365 programu.

Aby kupić dodatek Scheduler, należy wymagać jednej z następujących licencji:

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, Business Premium
- Exchange Online Plan 1 lub Plan 2. 

> [!Note]
> Program Scheduler for Microsoft 365 jest dostępny w środowiskach wielodostępnych na całym świecie tylko w języku angielskim. **Harmonogram dla Microsoft 365** jest niedostępny dla użytkowników:
> 
> - Microsoft 365 obsługiwana przez firmę 21Vianet w Chinach
> - Microsoft 365 z niemiecką chmurą, która korzysta z powierni danych, niemiecki Telekom
> - Government cloud including GCC, Consumer, GCC High, or DoD
> 
> Program Scheduler obsługuje użytkowników w Niemczech, których lokalizacja danych nie jest niemieckim centrum danych.
