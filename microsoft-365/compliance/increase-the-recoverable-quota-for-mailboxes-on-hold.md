---
title: Zwiększanie przydziału elementów odzyskiwalnych dla skrzynek pocztowych w  hold.
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a8bdcbdd-9298-462f-b889-df26037a990c
description: Włącz archiwalna skrzynkę pocztową i włącz automatyczne rozszerzanie archiwizacji, aby zwiększyć rozmiar folderu Elementy do odzyskania dla skrzynki pocztowej w programie Microsoft 365.
ms.openlocfilehash: 6465a86bfbf2d7f4eaf933786d15a4747b84dd5f
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010622"
---
# <a name="increase-the-recoverable-items-quota-for-mailboxes-on-hold"></a>Zwiększanie przydziału elementów odzyskiwalnych dla skrzynek pocztowych w  hold.

Domyślne zasady przechowywania Exchange, nazywane domyślnymi zasadami *MRM*, które są automatycznie stosowane do nowych skrzynek pocztowych w programie Exchange Online, zawierają tag przechowywania o nazwie Elementy odzyskiwalne, które są usuwane do archiwum przez 14 dni. Ten tag przechowywania przenosi elementy z folderu Elementy odzyskiwalne w podstawowej skrzynce pocztowej użytkownika do folderu Elementy odzyskiwalne w archiwanej skrzynce pocztowej użytkownika po upływie 14-dniowego okresu przechowywania dla elementu. Aby tak się stało, archiwalne skrzynki pocztowe użytkowników muszą być włączone. Jeśli archiwalna skrzynka pocztowa nie zostanie włączona, nie zostanie wykonane żadne działanie, co oznacza, że elementy w folderze Elementy do odzyskania w archiwum nie są przenoszone do archiwanej skrzynki pocztowej po upływie 14-dniowego okresu przechowywania. Ponieważ nic nie jest usuwane ze skrzynki pocztowej w archiwum, możliwe, że został przekroczony przydział magazynowania dla folderu Elementy do odzyskania, szczególnie jeśli archiwalna skrzynka pocztowa użytkownika nie jest włączona.

Aby zmniejszyć ryzyko przekroczenia tego limitu, przydział magazynowania dla folderu Elementy do odzyskania jest automatycznie zwiększany z 30 GB do 100 GB po umieszczeniu w skrzynce pocztowej w folderze Exchange Online. Jeśli archiwalna skrzynka pocztowa jest włączona, zwiększany jest również przydział miejsca do magazynowania w folderze Elementy do odzyskania w archiwanej skrzynce pocztowej z 30 GB do 100 GB. Jeśli funkcja automatycznego archiwizowania w programie Exchange Online jest włączona, całkowity przydział miejsca do magazynowania dla archiwalnej skrzynki pocztowej użytkownika, łącznie z folderem Elementy do odzyskania, wynosi 1,5 TB.

 W poniższej tabeli podsumowano przydział magazynowania dla folderu Elementy do odzyskania.

| Lokalizacja folderu Elementy do odzyskania | Skrzynki pocztowe, które nie są zawieszone | Skrzynki pocztowe zawieszone |
|:-----|:-----|:-----|
|Podstawowa skrzynka pocztowa |30 GB |100 GB |
|Archiwalna skrzynka pocztowa, w tym folder Elementy do odzyskania <sup>\*</sup> |1,5 TB |1,5 TB |

> [!NOTE]
> <sup>\*</sup>Początkowy przydział miejsca do magazynowania dla archiwaowej skrzynki pocztowej to 100 GB dla użytkowników z licencją Exchange Online (plan 2) skrzynki pocztowej. Jednak po włączeniu automatycznego archiwizowania dla skrzynek pocztowych w archiwum przydział magazynowania zarówno dla archiwalnej skrzynki pocztowej, jak i folderu Elementy do odzyskania zostanie zwiększony do 110 GB. W razie potrzeby zostanie udostępniona dodatkowa przestrzeń dyskowa archiwum (która obejmuje folder Elementy do odzyskania) o pojemności do 1,5 TB. Aby uzyskać więcej informacji na temat automatycznego rozszerzania archiwizacji, zobacz [Informacje na temat automatycznego rozwijania archiwizacji](autoexpanding-archiving.md).

Po osiągnięciu limitu przydziału magazynowania dla folderu Elementy do odzyskania w podstawowej skrzynce pocztowej skrzynki pocztowej zawieszonej możesz wykonać następujące czynności:

- **Włącz archiwalne skrzynki pocztowe i włącz automatyczne rozszerzanie archiwizacji.** Możesz włączyć dodatkową pojemność magazynowania dla folderu Elementy do odzyskania, po prostu włączając archiwalna skrzynkę pocztową, a następnie włączając funkcję automatycznego archiwizowania w programie Exchange Online. W wyniku tego 110 GB na folder Elementy do odzyskania w podstawowej skrzynce pocztowej i do 1,5 TB połączonej pojemności archiwum i folderu Elementy do odzyskania. Aby uzyskać więcej informacji, zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md) i [Włączanie automatycznego rozwijania archiwizacji](enable-autoexpanding-archiving.md).

    > [!NOTE]
    > Po włączeniu archiwum dla skrzynki pocztowej, która jest bliska przekroczeniu przydziału magazynowania folderu Elementy do odzyskania, można uruchomić asystenta folderów zarządzanych w celu ręcznego uruchomienia asystenta w celu przetwarzania skrzynki pocztowej w taki sposób, aby wygasłe elementy zostały przeniesione do folderu Elementy do odzyskania w archiwa pocztowej skrzynce pocztowej. Aby [uzyskać instrukcje, zobacz Krok 4](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings) . Pamiętaj, że inne elementy w skrzynce pocztowej użytkownika mogą zostać przeniesione do nowej archiwaowej skrzynki pocztowej. Rozważ możliwość poniania użytkownika, że może się tak zdarzyć po włączeniu archiwaowej skrzynki pocztowej.

- **Tworzenie niestandardowych Exchange przechowywania dla skrzynek pocztowych w  hold.** Oprócz włączenia archiwalnej skrzynki pocztowej i automatycznego rozszerzania archiwizacji dla skrzynek pocztowych w przypadku archiwizacji w związku z postępowaniem sądowym lub archiwum In-Place możesz także utworzyć niestandardowe zasady przechowywania Exchange dla skrzynek pocztowych w archiwum. Pozwala to zastosować zasady przechowywania do skrzynek pocztowych, które są zawieszone, które różnią się od domyślnych zasad MRM stosowanych do skrzynek pocztowych, które nie znajdują się w wstrzymaniu, i umożliwiają stosowanie tagów przechowywania, które są przeznaczone dla skrzynek pocztowych w  hold. Obejmuje to utworzenie nowego tagu przechowywania dla folderu Elementy do odzyskania.

W dalszej części tego tematu opisano procedury krok po kroku dotyczące tworzenia Exchange przechowywania dla skrzynek pocztowych w  hold.

[Krok 1. Tworzenie niestandardowego tagu przechowywania dla folderu Elementy do odzyskania](#step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder)

[Krok 2. Tworzenie nowych zasad przechowywania Exchange przechowywania dla skrzynek pocztowych wstrzymywanych](#step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold)

[Krok 3. Stosowanie nowych zasad przechowywania Exchange do skrzynek pocztowych wstrzymywanych](#step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold)

[(Opcjonalnie) Krok 4. Uruchamianie asystenta folderów zarządzanych w celu zastosowania nowych ustawień przechowywania](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings)

## <a name="step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder"></a>Krok 1. Tworzenie niestandardowego tagu przechowywania dla folderu Elementy do odzyskania

Pierwszym krokiem jest utworzenie niestandardowego tagu przechowywania (nazywanego tagiem zasad przechowywania lub zasad przechowywania) dla folderu Elementy do odzyskania. Jak wyjaśniono wcześniej, ten tag RPT przenosi elementy z folderu Elementy do odzyskania w podstawowej skrzynce pocztowej użytkownika do folderu Elementy do odzyskania w archiwanej skrzynce pocztowej użytkownika. Aby utworzyć rpt dla folderu Elementy do odzyskania, należy użyć programu PowerShell. Nie możesz korzystać z centrum administracyjnego usługi Exchange(EAC).

1. [Łączenie się z usługą Exchange Online przy użyciu zdalnej obsługi programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Uruchom następujące polecenie, aby utworzyć nowy kod RPT dla folderu Elementy do odzyskania:

    ```powershell
    New-RetentionPolicyTag -Name <Name of RPT> -Type RecoverableItems -AgeLimitForRetention <Number of days> -RetentionAction MoveToArchive
    ```

    Na przykład poniższe polecenie tworzy regułę zasad przechowywania dla folderu Elementy do odzyskania o nazwie "Elementy do odzyskania, 30 dni w przypadku skrzynek pocztowych w czasie przechowywania", z 30-dniowym okresem przechowywania. Oznacza to, że element, który znajduje się w folderze Elementy do odzyskania przez 30 dni, zostanie przeniesiony do folderu Elementy do odzyskania w archiwanej skrzynce pocztowej użytkownika.

    ```powershell
    New-RetentionPolicyTag -Name "Recoverable Items 30 days for mailboxes on hold" -Type RecoverableItems -AgeLimitForRetention 30 -RetentionAction MoveToArchive
    ```

    > [!TIP]
    > Zalecamy, aby okres przechowywania (zdefiniowany przez parametr  _AgeLimitForRetention_ ) dla reguły zasad grupy elementów odzyskiwalnych był taki sam jak okres przechowywania elementów usuniętych dla skrzynek pocztowych, do których będzie stosowany zasad grupy. Dzięki temu użytkownik będzie mieć możliwość odzyskania usuniętych elementów przez cały okres przechowywania usuniętych elementów przed ich przenoszeniem do archiwaowej skrzynki pocztowej. W poprzednim przykładzie ustawiono okres przechowywania na 30 dni przy założeniu, że okres przechowywania elementów usuniętych dla skrzynek pocztowych również wynosi 30 dni. Skrzynka Exchange Online jest domyślnie skonfigurowana do przechowywania usuniętych elementów przez 14 dni. Jednak możesz zmienić to ustawienie na maksymalnie 30 dni. Aby uzyskać więcej informacji, [zobacz Zmienianie okresu przechowywania elementów usuniętych dla skrzynki pocztowej w programie Exchange Online](https://www.microsoft.com/?ref=go).

## <a name="step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold"></a>Krok 2. Tworzenie nowych zasad przechowywania Exchange przechowywania dla skrzynek pocztowych wstrzymywanych

Następnym krokiem jest utworzenie nowych zasad przechowywania i dodanie do nich tagów przechowywania, w tym tagu zasad przechowywania Elementy odzyskiwalne utworzonego w kroku 1. Te nowe zasady zostaną zastosowane do skrzynek pocztowych wstrzymywanych w następnym kroku.

Przed utworzeniem nowych zasad przechowywania określ dodatkowe tagi przechowywania, które chcesz dodać. Aby uzyskać listę tagów przechowywania dodawanych do domyślnych zasad MRM oraz uzyskać informacje na temat tworzenia nowych tagów przechowywania, zobacz następujące informacje:

- [Domyślne zasady przechowywania w programie Exchange Online](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- [Foldery domyślne, które obsługują tagi zasad przechowywania](/exchange/security-and-compliance/messaging-records-management/default-folders)

- Sekcja "Tworzenie tagu przechowywania" w [temacie Tworzenie zasad przechowywania](/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy) .

Za pomocą SAC lub programu PowerShell Exchange Online tworzyć zasady przechowywania.

### <a name="use-the-eac-to-create-a-retention-policy"></a>Tworzenie zasad przechowywania przy użyciu SAC

1. W Aplikacji programu EAC przejdź do tematu **Zasady przechowywania zarządzania zgodnością** \> **, a** następnie kliknij pozycję **Dodaj** ![ikonę Dodaj](../media/ITPro-EAC-AddIcon.gif).

2. Na stronie **Nowe zasady przechowywania** w obszarze **Nazwa** wpisz nazwę opisującą przeznaczenie zasad przechowywania. Na przykład zasady **MRM dla skrzynek pocztowych w hold**.

3. W **obszarze Tagi przechowywania** kliknij **pozycję Dodaj** ![ikonę Dodaj](../media/ITPro-EAC-AddIcon.gif).

4. Na liście tagów przechowywania wybierz tag zasad przechowywania Elementy odzyskiwalne utworzony w kroku 1, a następnie kliknij przycisk **Dodaj**.

    ![Wybierz niestandardowy tag przechowywania Elementy odzyskiwalne.](../media/eb49866b-bdef-4fcd-a6d9-01607c01249b.png)

5. Wybierz dodatkowe tagi przechowywania, aby dodać je do zasad przechowywania. Możesz na przykład dodać te same tagi, które są zawarte w domyślnych zasadach MRM.

6. Po zakończeniu dodawania tagów przechowywania kliknij przycisk **OK**.

7. Kliknij **pozycję Zapisz** , aby utworzyć nowe zasady przechowywania.

    Zwróć uwagę, że tagi przechowywania połączone z zasadami przechowywania są wyświetlane w okienku szczegółów.

    ![Tagi przechowywania połączone z zasadami przechowywania są wyświetlane w okienku szczegółów.](../media/dad1c8f4-9928-4d6d-991a-6f6c5194eceb.png)

### <a name="use-exchange-online-powershell-to-create-a-retention-policy"></a>Tworzenie Exchange Online przechowywania przy użyciu programu PowerShell

Uruchom następujące polecenie, aby utworzyć nowe zasady przechowywania dla skrzynek pocztowych w  hold.

```powershell
New-RetentionPolicy <Name of retention policy>  -RetentionPolicyTagLinks <list of retention tags>
```

Na przykład poniższe polecenie tworzy zasady przechowywania i połączone tagi przechowywania, które są wyświetlane na poprzedniej ilustracji.

```powershell
New-RetentionPolicy "MRM Policy for Mailboxes on Hold"  -RetentionPolicyTagLinks "Recoverable Items 30 days for mailboxes on hold","1 Month Delete","1 Week Delete","1 Year Delete","5 Year Delete","6 Month Delete","Default 2 year move to archive","Junk Email","Never Delete","Personal 1 year move to archive","Personal 5 year move to archive"
```

## <a name="step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold"></a>Krok 3. Stosowanie nowych zasad przechowywania Exchange do skrzynek pocztowych wstrzymywanych

Ostatnim krokiem jest zastosowanie nowych zasad przechowywania utworzonych w kroku 2 do skrzynek pocztowych wstrzymywanych w organizacji. Za pomocą SAC lub programu PowerShell Exchange Online zasady przechowywania do jednej lub wielu skrzynek pocztowych.

### <a name="use-the-eac-to-apply-the-new-retention-policy"></a>Stosowanie nowych zasad przechowywania przy użyciu SAC

1. Przejdź do **pola AdresaciMailboxes** > .

2. W widoku listy zaznacz skrzynkę pocztową, do której chcesz zastosować zasady przechowywania, a następnie kliknij **ikonę Edytuj** ![Edytuj](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

3. Na stronie **Skrzynka pocztowa użytkownika** kliknij pozycję **Funkcje skrzynki pocztowej**.

4. W **obszarze Zasady** przechowywania wybierz zasady przechowywania utworzone w kroku 2, a następnie kliknij przycisk **Zapisz**.

Za pomocą Programu eAC możesz również zastosować zasady przechowywania do wielu skrzynek pocztowych.

1. Przejdź do **pola AdresaciMailboxes** > .

2. W widoku listy zaznacz wiele skrzynek pocztowych za pomocą klawiszy Shift i Ctrl.

3. W okienku szczegółów kliknij pozycję **Więcej opcji**.

4. W **obszarze Zasady przechowywania** kliknij pozycję **Aktualizuj**.

5. Na stronie **Zasady przechowywania zbiorczego** przypisywania wybierz zasady przechowywania utworzone w kroku 2, a następnie kliknij przycisk **Zapisz**.

### <a name="use-exchange-online-powershell-to-apply-the-new-retention-policy"></a>Stosowanie Exchange Online zasad przechowywania za pomocą programu PowerShell

Za pomocą programu Exchange Online PowerShell możesz zastosować nowe zasady przechowywania do jednej skrzynki pocztowej. Natomiast program Power In-Place Shell umożliwia szybkie identyfikowanie wszystkich skrzynek pocztowych w organizacji, które są w związku z postępowaniem sądowym lub zawieszeniem w związku z postępowaniem sądowym, a następnie zastosowanie nowych zasad przechowywania do wszystkich skrzynek pocztowych wstrzymywanych za pomocą jednego polecenia. Oto kilka przykładów użycia programu Exchange PowerShell w celu zastosowania zasad przechowywania do jednej lub większej liczby skrzynek pocztowych. Wszystkie przykłady dotyczą zasad przechowywania utworzonych w kroku 2.

W tym przykładzie nowe zasady przechowywania są stosowane do skrzynki pocztowej osoby Pilar Pinilla.

```powershell
Set-Mailbox "Pilar Pinilla" -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

W tym przykładzie nowe zasady przechowywania są stosowane do wszystkich skrzynek pocztowych w organizacji, które są w związku z postępowaniem sądowym.

```powershell
$LitigationHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'}
```

```powershell
$LitigationHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

W tym przykładzie nowe zasady przechowywania są stosowane do wszystkich skrzynek pocztowych w organizacji, które In-Place hold.

```powershell
$InPlaceHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null}
```

```powershell
$InPlaceHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Za pomocą polecenia cmdlet **Get-Mailbox** możesz sprawdzić, czy zastosowano nowe zasady przechowywania.

Oto kilka przykładów, aby sprawdzić, czy polecenia z poprzednich przykładów stosowane były do zasad przechowywania "Zasady MRM dla skrzynek pocztowych w miejscu przechowywania" do skrzynek pocztowych w przypadku stosowania funkcji Zawieszenie w procesów sądowych i skrzynek pocztowych w In-Place hold.

```powershell
Get-Mailbox "Pilar Pinilla" | Select RetentionPolicy
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'} | FT DisplayName,RetentionPolicy -Auto
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null} | FT DisplayName,RetentionPolicy -Auto
```

## <a name="optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings"></a>(Opcjonalnie) Krok 4. Uruchamianie asystenta folderów zarządzanych w celu zastosowania nowych ustawień przechowywania

Po zastosowaniu nowych zasad przechowywania usługi Exchange do skrzynek pocztowych w czasie przechowywania asystent folderów zarządzanych może upłynie do 7 dni Exchange Online aby przetworzyć te skrzynki pocztowe przy użyciu ustawień w nowych zasadach przechowywania. Zamiast czekać na uruchomienie asystenta folderów zarządzanych, możesz użyć polecenia cmdlet **Start-ManagedFolderAssistant** w celu ręcznego uruchomienia asystenta w celu przetwarzania skrzynek pocztowych, do których zastosowano nowe zasady przechowywania.

Uruchom następujące polecenie, aby uruchomić asystenta folderów zarządzanych dla skrzynki pocztowej Pilara Pinilla.

```powershell
Start-ManagedFolderAssistant "Pilar Pinilla"
```

Uruchom następujące polecenia, aby uruchomić asystenta folderów zarządzanych dla wszystkich skrzynek pocztowych, które są zawieszone.

```powershell
$MailboxesOnHold = Get-Mailbox -ResultSize unlimited | Where-Object {($_.InPlaceHolds -ne $null) -or ($_.LitigationHoldEnabled -eq "True")}
```

```powershell
$MailboxesOnHold.DistinguishedName | Start-ManagedFolderAssistant
```

## <a name="more-information"></a>Więcej informacji

- Po włączeniu archiwanej skrzynki pocztowej użytkownika rozważ pokłoń temu użytkownikowi, że inne elementy w jego skrzynce pocztowej (nie tylko elementy w folderze Elementy do odzyskania) mogły zostać przeniesione do archiwanej skrzynki pocztowej. Jest tak dlatego, że domyślne zasady MRM przypisane do skrzynek pocztowych programu Exchange Online zawierają tag przechowywania (o nazwie Domyślne 2 lata są przenoszone do archiwum), który przenosi elementy do archiwanej skrzynki pocztowej dwa lata po dostarczaniu elementu do skrzynki pocztowej lub utworzeniu go przez użytkownika. Aby uzyskać więcej informacji, zobacz [Domyślne zasady przechowywania w programie Exchange Online](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- Po włączeniu archiwaowej skrzynki pocztowej użytkownika możesz również poinformować użytkownika, że może on odzyskać usunięte elementy w folderze Elementy do odzyskania w jego archiwaowej skrzynce pocztowej. Mogą to zrobić w Outlook, **wybierając folder Elementy** usunięte w archiwaowej skrzynce pocztowej, a następnie klikając pozycję Odzyskaj elementy usunięte z serwera  na **karcie Narzędzia** główne. Aby uzyskać więcej informacji na temat odzyskiwania elementów usuniętych, zobacz Odzyskiwanie usuniętych elementów w [programie Outlook for Windows](https://go.microsoft.com/fwlink/p/?LinkId=624829).
