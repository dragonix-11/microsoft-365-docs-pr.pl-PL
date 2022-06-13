---
title: Zwiększ limit przydziału elementów odzyskiwalnych dla archiwum skrzynek pocztowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Włącz skrzynkę pocztową archiwum i włącz automatyczne rozszerzanie archiwizacji, aby zwiększyć rozmiar folderu Elementy możliwe do odzyskania dla skrzynki pocztowej w Microsoft 365.
ms.openlocfilehash: bbeb72c6a055be42e06c450afccb35965d149dce
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015021"
---
# <a name="increase-the-recoverable-items-quota-for-mailboxes-on-hold"></a>Zwiększ limit przydziału elementów odzyskiwalnych dla archiwum skrzynek pocztowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Domyślne zasady przechowywania Exchange o nazwie *Domyślne zasady MRM*, które są automatycznie stosowane do nowych skrzynek pocztowych w Exchange Online zawiera tag przechowywania o nazwie Elementy do odzyskania 14 dni przenieść do archiwum. Ten tag przechowywania przenosi elementy z folderu Elementy możliwe do odzyskania w podstawowej skrzynce pocztowej użytkownika do folderu Elementy możliwe do odzyskania w skrzynce pocztowej archiwum użytkownika po upływie 14-dniowego okresu przechowywania elementu. Aby tak się stało, należy włączyć archiwum skrzynki pocztowej użytkownika. Jeśli skrzynka pocztowa archiwum nie jest włączona, nie jest podejmowana żadna akcja, co oznacza, że elementy w folderze Elementy możliwe do odzyskania dla skrzynki pocztowej wstrzymanej nie są przenoszone do skrzynki pocztowej archiwum po upływie 14-dniowego okresu przechowywania. Ponieważ nic nie jest usuwane ze skrzynki pocztowej wstrzymanej, możliwe jest przekroczenie limitu przydziału magazynu dla folderu Elementy możliwe do odzyskania, zwłaszcza jeśli skrzynka pocztowa archiwum użytkownika nie jest włączona.

Aby zmniejszyć prawdopodobieństwo przekroczenia tego limitu, limit przydziału magazynu dla folderu Elementy możliwe do odzyskania zostanie automatycznie zwiększony z 30 GB do 100 GB po umieszczeniu blokady w skrzynce pocztowej w Exchange Online. Jeśli skrzynka pocztowa archiwum jest włączona, limit przydziału magazynu dla folderu Elementy możliwe do odzyskania w skrzynce pocztowej archiwum również zostanie zwiększony z 30 GB do 100 GB. Jeśli funkcja automatycznego rozszerzania archiwizacji w Exchange Online jest włączona, łączny limit przydziału magazynu dla skrzynki pocztowej archiwum użytkownika, w tym folderu Elementy możliwe do odzyskania, wynosi 1,5 TB.

 Poniższa tabela zawiera podsumowanie limitu przydziału magazynu dla folderu Elementy możliwe do odzyskania.

| Lokalizacja folderu Elementy do odzyskania | Skrzynki pocztowe nie są wstrzymane | Skrzynki pocztowe wstrzymane |
|:-----|:-----|:-----|
|Podstawowa skrzynka pocztowa |30 GB |100 GB |
|Archiwizuj skrzynkę pocztową, w tym folder Elementy możliwe do odzyskania <sup>\*</sup> |1,5 TB |1,5 TB |

> [!NOTE]
> <sup>\*</sup>Początkowy limit przydziału magazynu dla archiwum skrzynki pocztowej wynosi 100 GB dla użytkowników z licencją Exchange Online (plan 2). Jednak po włączeniu automatycznego rozszerzania archiwizacji dla skrzynek pocztowych wstrzymanych limit przydziału magazynu dla skrzynki pocztowej archiwum i folderu Elementy możliwe do odzyskania zostanie zwiększony do 110 GB. W razie potrzeby zostanie aprowizowane dodatkowe miejsce do magazynowania archiwum (w tym folder Elementy możliwe do odzyskania) do 1,5 TB. Aby uzyskać więcej informacji na temat automatycznego rozszerzania archiwizacji, zobacz [Dowiedz się więcej na temat automatycznego rozszerzania archiwizacji](autoexpanding-archiving.md).

Gdy limit przydziału magazynu dla folderu Elementy możliwe do odzyskania w podstawowej skrzynce pocztowej skrzynki pocztowej jest bliski osiągnięcia limitu, możesz wykonać następujące czynności:

- **Włącz skrzynkę pocztową archiwum i włącz automatyczne rozszerzanie archiwizacji.** Możesz włączyć dodatkową pojemność magazynu dla folderu Elementy możliwe do odzyskania po prostu włączając skrzynkę pocztową archiwum, a następnie włączając funkcję automatycznego rozszerzania archiwizacji w Exchange Online. Spowoduje to utworzenie 110 GB folderu Elementy do odzyskania w podstawowej skrzynce pocztowej i maksymalnie 1,5 TB łącznej pojemności magazynu dla folderu archiwum i elementów możliwych do odzyskania. Aby uzyskać więcej informacji, zobacz [Włączanie archiwizowania skrzynek pocztowych](enable-archive-mailboxes.md) i [Włączanie automatycznego rozszerzania archiwizacji](enable-autoexpanding-archiving.md).

    > [!NOTE]
    > Po włączeniu archiwum dla skrzynki pocztowej, która jest bliska przekroczenia limitu przydziału magazynu dla folderu Elementy możliwe do odzyskania, możesz uruchomić Asystenta folderów zarządzanych, aby ręcznie wyzwolić asystenta w celu przetworzenia skrzynki pocztowej, aby wygasłe elementy zostały przeniesione do folderu Elementy możliwe do odzyskania w skrzynce pocztowej archiwum. Aby uzyskać instrukcje [, zobacz Krok 4](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings) . Należy pamiętać, że inne elementy w skrzynce pocztowej użytkownika mogą zostać przeniesione do nowej skrzynki pocztowej archiwum. Rozważ poinformowanie użytkownika, że może się to zdarzyć po włączeniu archiwum skrzynki pocztowej.

- **Utwórz niestandardowe zasady przechowywania Exchange dla skrzynek pocztowych zablokowanych.** Oprócz włączenia skrzynki pocztowej archiwum i automatycznego rozszerzania archiwizacji skrzynek pocztowych w blokadzie postępowania sądowego lub In-Place blokadzie, warto również utworzyć niestandardowe zasady przechowywania Exchange dla skrzynek pocztowych wstrzymanych. Dzięki temu można zastosować zasady przechowywania do skrzynek pocztowych w stanie wstrzymania, które różnią się od domyślnych zasad MRM stosowanych do skrzynek pocztowych, które nie są zawieszone, i umożliwia stosowanie tagów przechowywania przeznaczonych dla skrzynek pocztowych zablokowanych. Obejmuje to utworzenie nowego tagu przechowywania dla folderu Elementy możliwe do odzyskania.

W pozostałej części tego tematu opisano procedury krok po kroku umożliwiające utworzenie niestandardowych zasad przechowywania Exchange dla skrzynek pocztowych wstrzymanych.

[Krok 1. Tworzenie niestandardowego tagu przechowywania dla folderu Elementy możliwe do odzyskania](#step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder)

[Krok 2. Tworzenie nowych zasad przechowywania Exchange dla skrzynek pocztowych zablokowanych](#step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold)

[Krok 3. Stosowanie nowych zasad przechowywania Exchange do skrzynek pocztowych zablokowanych](#step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold)

[(Opcjonalnie) Krok 4. Uruchamianie asystenta folderów zarządzanych w celu zastosowania nowych ustawień przechowywania](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings)

## <a name="step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder"></a>Krok 1. Tworzenie niestandardowego tagu przechowywania dla folderu Elementy możliwe do odzyskania

Pierwszym krokiem jest utworzenie niestandardowego tagu przechowywania (nazywanego tagiem zasad przechowywania lub RPT) dla folderu Elementy możliwe do odzyskania. Jak wyjaśniono wcześniej, ten RPT przenosi elementy z folderu Elementy do odzyskania w podstawowej skrzynce pocztowej użytkownika do folderu Elementy możliwe do odzyskania w skrzynce pocztowej archiwum użytkownika. Aby utworzyć RPT dla folderu Elementy do odzyskania, należy użyć programu PowerShell. Nie można użyć centrum administracyjnego Exchange (EAC).

1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Uruchom następujące polecenie, aby utworzyć nowy RPT dla folderu Elementy możliwe do odzyskania:

    ```powershell
    New-RetentionPolicyTag -Name <Name of RPT> -Type RecoverableItems -AgeLimitForRetention <Number of days> -RetentionAction MoveToArchive
    ```

    Na przykład następujące polecenie tworzy RPT dla folderu Elementy możliwe do odzyskania o nazwie "Elementy do odzyskania 30 dni dla skrzynek pocztowych wstrzymanych" z okresem przechowywania wynoszącym 30 dni. Oznacza to, że gdy element będzie znajdować się w folderze Elementy możliwe do odzyskania przez 30 dni, zostanie on przeniesiony do folderu Elementy możliwe do odzyskania w skrzynce pocztowej archiwum użytkownika.

    ```powershell
    New-RetentionPolicyTag -Name "Recoverable Items 30 days for mailboxes on hold" -Type RecoverableItems -AgeLimitForRetention 30 -RetentionAction MoveToArchive
    ```

    > [!TIP]
    > Zalecamy, aby okres przechowywania (zdefiniowany przez parametr  _AgeLimitForRetention_ ) dla elementów możliwych do odzyskania RPT był taki sam jak usunięty okres przechowywania elementów dla skrzynek pocztowych, do których zostanie zastosowany RPT. Dzięki temu użytkownikowi cały usunięty okres przechowywania elementów może odzyskać usunięte elementy przed przeniesieniem ich do archiwum skrzynki pocztowej. W poprzednim przykładzie okres przechowywania został ustawiony na 30 dni na podstawie założenia, że okres przechowywania usuniętych elementów dla skrzynek pocztowych wynosi również 30 dni. Skrzynka pocztowa Exchange Online jest domyślnie skonfigurowana do przechowywania usuniętych elementów przez 14 dni. Można jednak zmienić to ustawienie na maksymalnie 30 dni. Aby uzyskać więcej informacji, zobacz [Zmienianie okresu przechowywania usuniętego elementu dla skrzynki pocztowej w Exchange Online](https://www.microsoft.com/?ref=go).

## <a name="step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold"></a>Krok 2. Tworzenie nowych zasad przechowywania Exchange dla skrzynek pocztowych zablokowanych

Następnym krokiem jest utworzenie nowych zasad przechowywania i dodanie do nich tagów przechowywania, w tym RPT elementów możliwych do odzyskania utworzonych w kroku 1. Te nowe zasady zostaną zastosowane do skrzynek pocztowych wstrzymanych w następnym kroku.

Przed utworzeniem nowych zasad przechowywania określ dodatkowe tagi przechowywania, które chcesz dodać. Aby uzyskać listę tagów przechowywania dodanych do domyślnych zasad MRM oraz informacje o tworzeniu nowych tagów przechowywania, zobacz następujące informacje:

- [Domyślne zasady przechowywania w Exchange Online](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- [Foldery domyślne obsługujące tagi zasad przechowywania](/exchange/security-and-compliance/messaging-records-management/default-folders)

- Sekcja "Tworzenie tagu przechowywania" w temacie [Tworzenie zasad przechowywania](/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy) .

Aby utworzyć zasady przechowywania, możesz użyć eac lub Exchange Online programu PowerShell.

### <a name="use-the-eac-to-create-a-retention-policy"></a>Tworzenie zasad przechowywania przy użyciu umowy EAC

1. W usłudze EAC przejdź do pozycji **Zasady przechowywania** **zarządzania zgodnością**\>, a następnie kliknij pozycję **Dodaj** ![ikonę.](../media/ITPro-EAC-AddIcon.gif).

2. Na stronie **Nowe zasady przechowywania** w obszarze **Nazwa** wpisz nazwę opisującą przeznaczenie zasad przechowywania; na przykład **zasady MRM dla skrzynek pocztowych w blokadzie**.

3. W obszarze **Tagi przechowywania** kliknij pozycję **Dodaj** ![ikonę.](../media/ITPro-EAC-AddIcon.gif).

4. Na liście tagów przechowywania wybierz elementy do odzyskania utworzone w kroku 1, a następnie kliknij przycisk **Dodaj**.

    ![Wybierz niestandardowy tag przechowywania elementów możliwych do odzyskania.](../media/eb49866b-bdef-4fcd-a6d9-01607c01249b.png)

5. Wybierz dodatkowe tagi przechowywania, aby dodać je do zasad przechowywania. Na przykład możesz dodać te same tagi, które są uwzględnione w domyślnych zasadach MRM.

6. Po zakończeniu dodawania tagów przechowywania kliknij przycisk **OK**.

7. Kliknij **przycisk Zapisz** , aby utworzyć nowe zasady przechowywania.

    Zwróć uwagę, że tagi przechowywania połączone z zasadami przechowywania są wyświetlane w okienku szczegółów.

    ![Tagi przechowywania połączone z zasadami przechowywania są wyświetlane w okienku szczegółów.](../media/dad1c8f4-9928-4d6d-991a-6f6c5194eceb.png)

### <a name="use-exchange-online-powershell-to-create-a-retention-policy"></a>Tworzenie zasad przechowywania przy użyciu Exchange Online programu PowerShell

Uruchom następujące polecenie, aby utworzyć nowe zasady przechowywania dla skrzynek pocztowych w stanie wstrzymania.

```powershell
New-RetentionPolicy <Name of retention policy>  -RetentionPolicyTagLinks <list of retention tags>
```

Na przykład następujące polecenie tworzy zasady przechowywania i połączone tagi przechowywania, które są wyświetlane na poprzedniej ilustracji.

```powershell
New-RetentionPolicy "MRM Policy for Mailboxes on Hold"  -RetentionPolicyTagLinks "Recoverable Items 30 days for mailboxes on hold","1 Month Delete","1 Week Delete","1 Year Delete","5 Year Delete","6 Month Delete","Default 2 year move to archive","Junk Email","Never Delete","Personal 1 year move to archive","Personal 5 year move to archive"
```

## <a name="step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold"></a>Krok 3. Stosowanie nowych zasad przechowywania Exchange do skrzynek pocztowych zablokowanych

Ostatnim krokiem jest zastosowanie nowych zasad przechowywania utworzonych w kroku 2 do skrzynek pocztowych zablokowanych w organizacji. Możesz użyć eac lub Exchange Online programu PowerShell, aby zastosować zasady przechowywania do jednej skrzynki pocztowej lub do wielu skrzynek pocztowych.

### <a name="use-the-eac-to-apply-the-new-retention-policy"></a>Stosowanie nowych zasad przechowywania przy użyciu umowy EAC

1. Przejdź do **obszaru Skrzynki pocztowe adresatów** > .

2. W widoku listy wybierz skrzynkę pocztową, do którą chcesz zastosować zasady przechowywania, a następnie kliknij pozycję **Edytuj ikonę Edytuj**![.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)

3. Na stronie **Skrzynka pocztowa użytkownika** kliknij pozycję **Funkcje skrzynki pocztowej**.

4. W obszarze **Zasady przechowywania** wybierz zasady przechowywania utworzone w kroku 2, a następnie kliknij przycisk **Zapisz**.

Możesz również użyć umowy EAC, aby zastosować zasady przechowywania do wielu skrzynek pocztowych.

1. Przejdź do **obszaru Skrzynki pocztowe adresatów** > .

2. W widoku listy użyj klawiszy Shift lub Ctrl, aby wybrać wiele skrzynek pocztowych.

3. W okienku szczegółów kliknij pozycję **Więcej opcji**.

4. W obszarze **Zasady przechowywania** kliknij pozycję **Aktualizuj**.

5. Na stronie **Zasady przechowywania przypisywania zbiorczego** wybierz zasady przechowywania utworzone w kroku 2, a następnie kliknij przycisk **Zapisz**.

### <a name="use-exchange-online-powershell-to-apply-the-new-retention-policy"></a>Stosowanie nowych zasad przechowywania przy użyciu Exchange Online programu PowerShell

Za pomocą programu Exchange Online programu PowerShell można zastosować nowe zasady przechowywania do pojedynczej skrzynki pocztowej. Ale prawdziwą siłą programu PowerShell jest to, że można go używać do szybkiego identyfikowania wszystkich skrzynek pocztowych w organizacji, które znajdują się w blokadzie postępowania sądowego lub In-Place blokadzie, a następnie zastosować nowe zasady przechowywania do wszystkich skrzynek pocztowych wstrzymanych w jednym poleceniu. Oto kilka przykładów użycia Exchange programu PowerShell do stosowania zasad przechowywania do co najmniej jednej skrzynki pocztowej. Wszystkie przykłady dotyczą zasad przechowywania utworzonych w kroku 2.

W tym przykładzie nowe zasady przechowywania są stosowane do skrzynki pocztowej firmy Pilar Pinilla.

```powershell
Set-Mailbox "Pilar Pinilla" -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

W tym przykładzie nowe zasady przechowywania są stosowane do wszystkich skrzynek pocztowych w organizacji, które znajdują się w blokadzie postępowania sądowego.

```powershell
$LitigationHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'}
```

```powershell
$LitigationHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

W tym przykładzie nowe zasady przechowywania są stosowane do wszystkich skrzynek pocztowych w organizacji, które znajdują się w In-Place Blokada.

```powershell
$InPlaceHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null}
```

```powershell
$InPlaceHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Aby sprawdzić, czy zostały zastosowane nowe zasady przechowywania, możesz użyć polecenia cmdlet **Get-Mailbox** .

Poniżej przedstawiono kilka przykładów sprawdzania, czy polecenia w poprzednich przykładach stosują zasady przechowywania "Zasady MRM dla skrzynek pocztowych wstrzymanych" do skrzynek pocztowych w blokadzie postępowania sądowego i skrzynek pocztowych w In-Place Blokada.

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

Po zastosowaniu nowych zasad przechowywania Exchange do skrzynek pocztowych w stanie wstrzymania może upłynąć do 7 dni w Exchange Online, aby asystent folderów zarządzanych przetworzyć te skrzynki pocztowe przy użyciu ustawień w nowych zasadach przechowywania. Zamiast czekać na uruchomienie Asystenta folderów zarządzanych, możesz użyć polecenia cmdlet **Start-ManagedFolderAssistant** , aby ręcznie wyzwolić asystenta w celu przetworzenia skrzynek pocztowych, do których zastosowano nowe zasady przechowywania.

Uruchom następujące polecenie, aby uruchomić asystenta folderów zarządzanych dla skrzynki pocztowej Pilar Pinilla.

```powershell
Start-ManagedFolderAssistant "Pilar Pinilla"
```

Uruchom następujące polecenia, aby uruchomić Asystenta folderów zarządzanych dla wszystkich skrzynek pocztowych wstrzymanych.

```powershell
$MailboxesOnHold = Get-Mailbox -ResultSize unlimited | Where-Object {($_.InPlaceHolds -ne $null) -or ($_.LitigationHoldEnabled -eq "True")}
```

```powershell
$MailboxesOnHold.DistinguishedName | Start-ManagedFolderAssistant
```

## <a name="more-information"></a>Więcej informacji

- Po włączeniu archiwum skrzynki pocztowej użytkownika rozważ poinformowanie użytkownika, że inne elementy w jego skrzynce pocztowej (nie tylko elementy w folderze Elementy możliwe do odzyskania) mogą zostać przeniesione do skrzynki pocztowej archiwum. Wynika to z faktu, że domyślne zasady MRM przypisane do Exchange Online skrzynek pocztowych zawierają tag przechowywania (o nazwie Domyślne 2 lata przenieść do archiwum), który przenosi elementy do skrzynki pocztowej archiwum dwa lata po dacie dostarczenia elementu do skrzynki pocztowej lub utworzonego przez użytkownika. Aby uzyskać więcej informacji, zobacz [Domyślne zasady przechowywania w Exchange Online](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- Po włączeniu archiwum skrzynki pocztowej użytkownika możesz również poinformować użytkownika, że może odzyskać usunięte elementy w folderze Elementy możliwe do odzyskania w skrzynce pocztowej archiwum. Mogą to zrobić w Outlook, wybierając folder **Elementy usunięte** w skrzynce pocztowej archiwum, a następnie klikając pozycję **Odzyskaj usunięte elementy z serwera** na karcie **Narzędzia** główne. Aby uzyskać więcej informacji na temat odzyskiwania usuniętych elementów, zobacz [Odzyskiwanie usuniętych elementów w Outlook, aby uzyskać Windows](https://go.microsoft.com/fwlink/p/?LinkId=624829).
