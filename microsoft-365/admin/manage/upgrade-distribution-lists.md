---
title: Uaktualnianie list dystrybucyjnych do grup platformy Microsoft 365 w usłudze Exchange Online
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 787d7a75-e201-46f3-a242-f698162ff09f
description: Dowiedz się, jak uaktualnić jedną lub wiele list dystrybucyjnych do grup platformy Microsoft 365 w usłudze Exchange Online oraz jak uaktualnić kilka list dystrybucyjnych jednocześnie za pomocą programu PowerShell.
ms.openlocfilehash: 6f27c4a7df345a25f4b5ca7d2a9f2979a97e7c6a
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922180"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-exchange-online"></a>Uaktualnianie list dystrybucyjnych do grup platformy Microsoft 365 w usłudze Exchange Online

Uaktualnienie listy dystrybucyjnej do grupy platformy Microsoft 365 to doskonały sposób na ulepszenie funkcji i możliwości grup w organizacji. Aby uzyskać więcej informacji, zobacz [Dlaczego należy uaktualnić listy dystrybucyjne do grup w programie Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

Listy dystrybucyjne można uaktualniać pojedynczo lub kilka jednocześnie. Możesz użyć centrum administracyjnego programu Exchange (EAC) lub programu PowerShell usługi Exchange Online.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups"></a>Uaktualnianie jednej lub wielu grup listy dystrybucyjnej do grup platformy Microsoft 365

Aby uaktualnić listę dystrybucyjną, musisz być administratorem globalnym lub administratorem programu Exchange. Aby przeprowadzić uaktualnienie do grup platformy Microsoft 365, lista dystrybucyjna musi mieć wyznaczonego właściciela, a ten właściciel musi być skrzynką pocztową.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Uaktualnianie jednej lub wielu grup listy dystrybucyjnej do grup platformy Microsoft 365 w programie Outlook przy użyciu klasycznej usługi EAC

> [!NOTE]
> Procedury opisane w tej sekcji nie są dostępne w nowej usłudze EAC.

1. Przejdź do centrum administracyjnego programu Exchange > <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**grupy**</a> **adresatów**\>.

   Zostanie wyświetlone powiadomienie wskazujące, że masz listy dystrybucyjne (nazywane również **grupami dystrybucji**), które kwalifikują się do uaktualnienia do grup platformy Microsoft 365.
   
   ![Wybierz przycisk Rozpocznij.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. Wybierz co najmniej jedną listę dystrybucyjną (nazywaną również **grupami dystrybucji**) na stronie **grup** .

   ![Wybierz grupę dystrybucyjną.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Wybierz ikonę uaktualnienia.

   ![Uaktualnij do ikony Grupy platformy Microsoft 365.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. W oknie dialogowym informacji wybierz pozycję **Tak** , aby potwierdzić uaktualnienie. Proces rozpoczyna się natychmiast. W zależności od rozmiaru i liczby uaktualnianych rozłożeń proces może potrwać kilka minut lub godzin.

   Jeśli nie można uaktualnić listy dystrybucyjnej, zostanie wyświetlone okno dialogowe. Zobacz [Które listy dystrybucyjne nie mogą być uaktualnione?](#which-distribution-lists-cant-be-upgraded).

1. Jeśli uaktualniasz wiele list dystrybucyjnych, użyj listy rozwijanej, aby filtrować listy dystrybucyjne, które zostały uaktualnione. Jeśli lista nie została ukończona, poczekaj chwilę dłużej, a następnie wybierz pozycję **Odśwież** , aby zobaczyć, co zostało pomyślnie uaktualnione.

**Uwagi**:

- Po zakończeniu uaktualnień nie zostanie wyświetlone powiadomienie. Zamiast tego zobacz, co jest wymienione w obszarze **Dostępne do uaktualnienia** lub **Uaktualnione listy DLs**.

- Jeśli wybrano listę dystrybucyjną do uaktualnienia, ale nadal jest ona wyświetlana na stronie **jako Dostępna do uaktualnienia**, uaktualnienie nie powiodło się. Zobacz [Co zrobić, jeśli uaktualnienie nie działa](#what-to-do-if-the-upgrade-doesnt-work).

- Szyfrowane wiadomości e-mail grupy mogą oferować możliwość uaktualnienia wszystkich kwalifikujących się list dystrybucyjnych, których jesteś właścicielem. Aby uzyskać więcej informacji na temat wiadomości e-mail szyfrowane, zobacz [Temat Prowadzenie konwersacji grupowej w programie Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22).

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Co zrobić, jeśli uaktualnienie nie działa

Listy dystrybucyjne, które nie mogą zostać uaktualnione, pozostają niezmienione.

Jeśli nie można uaktualnić co najmniej jednej **kwalifikującej się** listy dystrybucyjnej, wykonaj następujące kroki:

1. Ten [skrypt](https://aka.ms/DLToM365Group) służy do skanowania pod kątem możliwych problemów. Rozwiąż wszelkie problemy zgłaszane przez skrypt i spróbuj uaktualnić listę dystrybucyjną jeszcze raz. 

2. Jeśli skrypt nie pomoże, otwórz [bilet pomocy technicznej](../../business-video/get-help-support.md). Problem będzie musiał zostać przekazany zespołowi inżynierów grup.

## <a name="how-to-use-exchange-online-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Jak używać programu PowerShell usługi Exchange Online do uaktualniania kilku list dystrybucyjnych w tym samym czasie

Aby nawiązać połączenie z programem PowerShell usługi Exchange Online, zobacz [Łączenie z programem PowerShell usługi Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="upgrade-a-single-distribution-list"></a>Uaktualnianie pojedynczej listy dystrybucyjnej

Aby uaktualnić pojedynczą listę dystrybucyjną, użyj następującej składni:

```PowerShell
Upgrade-DistributionGroup -DLIdentities <EmailAddress>
```

W tym przykładzie uaktualnij listę dystrybucyjną marketing@contoso.com:

```PowerShell
Upgrade-DistributionGroup -DLIdentities marketing@contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Upgrade-DistributionGroup](/powershell/module/exchange/upgrade-distributiongroup).

> [!NOTE]
> Możesz również uaktualnić pojedynczą listę dystrybucyjną do grupy platformy Microsoft 365 przy użyciu polecenia cmdlet [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) .

### <a name="upgrade-multiple-distribution-lists-at-the-same-time"></a>Uaktualnianie wielu list dystrybucyjnych w tym samym czasie

Aby uaktualnić wiele list dystrybucyjnych w tym samym czasie, użyj następującej składni:

```PowerShell
Upgrade-DistributionGroup -DLIdentities <EmailAddress1>,<EmailAddress2>,...
```

W tym przykładzie określona lista dystrybucyjna jest uaktualniana do grup platformy Microsoft 365.

```powershell
Upgrade-DistributionGroup -DLIdentities marketing@contoso.com,finanace@contoso.com,hr@contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Upgrade-DistributionGroup](/powershell/module/exchange/upgrade-distributiongroup).

### <a name="upgrade-all-eligible-distribution-lists"></a>Uaktualnianie wszystkich kwalifikujących się list dystrybucyjnych

Użyj jednej z następujących metod, aby uaktualnić wszystkie kwalifikujące się listy dystrybucyjne do grup platformy Microsoft 365:

- Uaktualnij wszystkie kwalifikujące się listy dystrybucyjne:

   ```PowerShell
   $All = Get-EligibleDistributionGroupForMigration -ResultSize unlimited
   $All | Foreach-Object {Upgrade-DistributionGroup -DLIdentities $_.PrimarySMTPAddress}
   ```

- Spróbuj uaktualnić wszystkie listy dystrybucyjne, niezależnie od tego, czy są one uprawnione, czy nie:

   ```PowerShell
   $All Get-DistributionGroup -RecipientTypeDetails MailUniversalDistributionGroup -ResultSize unlimited
   $All | Foreach-Object {Upgrade-DistributionGroup -DLIdentities $_.PrimarySMTPAddress}
   ```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Często zadawane pytania dotyczące uaktualniania list dystrybucyjnych do grup platformy Microsoft 365 w programie Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>Których list dystrybucyjnych nie można uaktualnić?

Można uaktualnić tylko zarządzane w chmurze, proste, niegnieżdżone listy dystrybucyjne. W poniższej tabeli wymieniono listy dystrybucyjne, których **nie można** uaktualnić.

|Właściwość|Kwalifikujących się?|
|---|:---:|
|Lokalna zarządzana lista dystrybucyjna.|Nie|
|Zagnieżdżone listy dystrybucyjne. Lista dystrybucyjna zawiera grupy podrzędne lub jest członkiem innej grupy.|Nie|
|Listy dystrybucyjne, w których co najmniej jeden członek jest inny niż skrzynka pocztowa użytkownika, udostępniona skrzynka pocztowa, skrzynka pocztowa zespołu lub użytkownik poczty. Innymi słowy, wartość **RecipientTypeDetails** dowolnego członka listy dystrybucyjnej nie jest **UserMailbox**, **SharedMailbox**, **TeamMailbox** lub **MailUser**.|Nie|
|Lista dystrybucyjna zawierająca ponad 100 właścicieli.|Nie|
|Lista dystrybucyjna zawierająca tylko elementy członkowskie, ale bez właściciela.|Nie|
|Lista dystrybucyjna zawierająca alias zawierający znaki specjalne.|Nie|
|Lista dystrybucyjna jest skonfigurowana jako adres przesyłania dalej dla udostępnionej skrzynki pocztowej.|Nie|
|Lista dystrybucyjna jest częścią **ograniczenia nadawcy** na innej liście dystrybucyjnej.|Nie|
|Grupy zabezpieczeń z obsługą poczty.|Nie|
|Dynamiczne grupy dystrybucyjne.|Nie|
|Listy dystrybucyjne, które zostały przekonwertowane na **listy pokojów**.|Nie|

### <a name="check-which-distribution-lists-are-eligible-for-upgrade"></a>Sprawdzanie, które listy dystrybucyjne kwalifikują się do uaktualnienia

Aby sprawdzić, czy określona lista dystrybucyjna kwalifikuje się do uaktualnienia, uruchom następujące polecenie:

```PowerShell
Get-DistributionGroup <EmailAddress> | Get-EligibleDistributionGroupForMigration
```

Aby wyświetlić wszystkie grupy dystrybucyjne kwalifikujące się do uaktualnienia, uruchom następujące polecenie:

```PowerShell
Get-EligibleDistributionGroupForMigration
```

### <a name="who-can-run-the-upgrade-scripts"></a>Kto może uruchamiać skrypty uaktualniania?

Osoby z uprawnieniami administratora globalnego lub administratora programu Exchange.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Dlaczego karta kontaktu nadal wyświetla listę dystrybucyjną? Co należy zrobić, aby zapobiec wyświetlaniu uaktualnianej listy dystrybucyjnej na liście autosugerów?

- **Outlook**: Po uaktualnieniu listy ditribution do grupy platformy Microsoft 365 lokalna pamięć podręczna adresatów użytkownika (znana również jako pamięć podręczna nazw nicków) nie jest świadoma zmiany. Wykonaj kroki opisane w poniższym artykule, aby zresetować lokalną pamięć podręczną adresatów użytkownika: [informacje o liście autouzupełniania programu Outlook](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list). 

  Jeśli nie zaktualizujesz pamięci podręcznej adresata, wszelkie wiadomości e-mail wysłane do grupy platformy Microsoft 365 zostaną dostarczone pomyślnie, ale nadal będą występować następujące problemy:
  
  - Adresat grupy zostanie rozpoznany jako lista dystrybucyjna zamiast grupy platformy Microsoft 365.
  - Wizytówka będzie kontaktem z listą dystrybucyjną, a nie grupą platformy Microsoft 365.

- **Outlook w internecie**: podobnie jak program Outlook, lista dystrybucyjna pozostanie w pamięci podręcznej adresata. Wykonaj kroki opisane w tym artykule, aby odświeżyć pamięć podręczną, aby wyświetlić kartę kontaktową grupy: [Usuń sugerowaną nazwę lub adres e-mail z listy autouzupełniania](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58).

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Czy nowi członkowie grupy otrzymują powitalną wiadomość e-mail w skrzynce odbiorczej?

Nie. Ustawienie włączania komunikatów powitalnych jest domyślnie ustawione na wartość false. To ustawienie dotyczy zarówno istniejących, jak i nowych członków grupy, którzy mogą dołączyć po zakończeniu migracji. Jeśli właściciel grupy później zezwoli użytkownikom-gościom, użytkownicy-goście nie otrzymają powitalnej wiadomości e-mail w skrzynce odbiorczej. Członkowie-goście mogą kontynuować pracę z grupą.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Co zrobić, jeśli jeden lub niektóre listy DLS nie zostaną uaktualnione?

W niektórych przypadkach nie można uaktualnić kwalifikujących się list dystrybucyjnych. Przykład:

- Administrator zastosował **zasady adresów e-mail grupy**, a lista dystrybucyjna nie spełnia wymagań zasad.

- Lista dystrybucyjna ma wartość **MemberJoinRestriction** lub **MemberDepartRestriction** ustawioną na wartość **Zamknięte**.

- Tworzenie grupy platformy Microsoft 365 jest ograniczone zgodnie z opisem w tym artykule: [ten artykuł](/microsoft-365/solutions/manage-creation-of-groups).

  Użyj jednego z następujących obejść tego konkretnego problemu:

  - Upewnij się, że wszyscy właściciele listy dystrybucyjnej mogą tworzyć grupy platformy Microsoft 365 (tj. właściciele są członkami grupy zabezpieczeń, która może tworzyć grupy platformy Microsoft 365).

  - Tymczasowo zastąp właściciela listy dystrybucyjnej użytkownikiem, który może tworzyć grupy platformy Microsoft 365.

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>Co się stanie z biblioteką DL, jeśli uaktualnienie z eac zakończy się niepowodzeniem?

Uaktualnienie nastąpi tylko wtedy, gdy wywołanie zostanie przesłane do serwera. Jeśli uaktualnienie zakończy się niepowodzeniem, listy dystrybucyjne pozostaną i będą działać tak, jak kiedyś.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>Co się stanie z ustawieniami zatwierdzania komunikatów (moderowania) w grupach dystrybucyjnych po uaktualnieniu?

Ustawienia zatwierdzania komunikatów (moderowania) są zachowywane i nadal działają prawidłowo po uaktualnieniu grupy dystrybucyjnej do grupy platformy Microsoft 365.

## <a name="related-content"></a>Zawartość pokrewna

[Porównanie grup](../create-groups/compare-groups.md) (artykuł)\
[Objaśnienie grup platformy Microsoft 365 użytkownikom](../create-groups/explain-groups-knowledge-worker.md) (artykuł)\
[Dodawanie lub usuwanie członków z grup platformy Microsoft 365 przy użyciu centrum administracyjnego](../create-groups/add-or-remove-members-from-groups.md)
