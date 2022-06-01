---
title: Alerty usługi wykorzystania skrzynki pocztowej
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Skorzystaj z porad dotyczących usługi wykorzystania skrzynek pocztowych, aby monitorować skrzynki pocztowe w stanie wstrzymania, które osiągają limit przydziału skrzynki pocztowej.
ms.openlocfilehash: 22583cbc6c6495d07caa3f920eeacb6bcd1d7536
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810555"
---
# <a name="service-advisories-for-mailbox-utilization-in-exchange-online-monitoring"></a>Porady dotyczące usługi dotyczące wykorzystania skrzynki pocztowej w monitorowaniu Exchange Online

Opublikowaliśmy nowe usługi Exchange Online, które informują o zablokowanych skrzynkach pocztowych, które są zagrożone osiągnięciem lub przekroczeniem limitu przydziału. Te porady dotyczące usług zapewniają wgląd w liczbę skrzynek pocztowych w organizacji, które mogą wymagać interwencji administratora.

Te porady dotyczące usług są wyświetlane w Centrum administracyjne platformy Microsoft 365. Aby wyświetlić te porady dotyczące usług, przejdź do pozycji **Kondycja** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Kondycja usługi**</a> >  **Exchange Online** a następnie kliknij kartę **Aktywne problemy**. Oto przykład porady dotyczącej usługi wykorzystania skrzynki pocztowej.

:::image type="content" alt-text="Alert usługi wykorzystania skrzynki pocztowej." source="../media/MailboxUtilizationServiceAlert.png" lightbox="../media/MailboxUtilizationServiceAlert.png":::

Aby wyświetlić listę skrzynek pocztowych, które zbliżają się do limitu przydziału magazynu (nazywanego *raportem użycia skrzynki pocztowej*), kliknij wyróżniony link na poniższym zrzucie ekranu. Ten link jest wyświetlany w poradniku usługi.

:::image type="content" alt-text="Link do raportu użycia skrzynki pocztowej." source="../media/LinkToMailboxUsageReport.png" lightbox="../media/LinkToMailboxUsageReport.png":::

Alternatywnie bezpośredni adres URL raportu użycia skrzynki pocztowej to <https://admin.microsoft.com/Adminportal/Home?source=applauncher#/reportsUsage/MailboxUsage>.

## <a name="what-do-these-service-advisories-indicate"></a>Co wskazują te porady dotyczące usług?

Porady dotyczące obsługi użycia skrzynek pocztowych informują administratorów o wstrzymanych skrzynkach pocztowych, które zbliżają się do limitu przydziału magazynu skrzynki pocztowej. Typ blokad, które można umieścić w skrzynkach pocztowych, obejmuje blokady sporów sądowych, blokadę zbierania elektronicznych materiałów dowodowych i zasady przechowywania Microsoft 365 (skonfigurowane do przechowywania danych). Gdy skrzynka pocztowa jest wstrzymana, użytkownicy (lub zautomatyzowane procesy) nie mogą trwale usuwać danych ze swojej skrzynki pocztowej. Zamiast tego administratorzy muszą skonfigurować zasady przechowywania mrm w Exchange Online (zgodnie z zasadami zgodności organizacji związanymi z przechowywaniem danych), aby przenieść dane z podstawowej skrzynki pocztowej użytkownika do jego skrzynki pocztowej archiwum. Jeśli nie, a skrzynka pocztowa w blokadzie osiągnie stan krytyczny lub ostrzegawczy, administratorzy muszą [włączyć archiwalne skrzynki pocztowe](../compliance/enable-archive-mailboxes.md) i [włączyć automatyczne rozszerzanie archiwizacji](../compliance/enable-autoexpanding-archiving.md) , a następnie upewnić się, że okres przechowywania zasad archiwum przypisanych do skrzynki pocztowej (która przenosi wiadomość e-mail z podstawowej skrzynki pocztowej do archiwum skrzynki pocztowej) jest wystarczająco krótki. Jeśli nic nie zostanie zrobione w celu rozwiązania problemów z limitem przydziału, które są identyfikowane przez poradę dotyczącą usługi wykorzystania skrzynki pocztowej, użytkownicy mogą nie być w stanie wysyłać ani odbierać wiadomości e-mail lub zaproszeń na spotkania.

Porada dotycząca obsługi użycia skrzynek pocztowych zawiera tabele dotyczące liczby skrzynek pocztowych, które zbliżają się do limitu przydziału. W poniższych sekcjach opisano informacje zawarte w tych tabelach oraz działania, które administratorzy mogą podjąć, aby zapewnić, że te skrzynki pocztowe nie przekroczą limitu przydziału.

> [!NOTE]
> Porady dotyczące usług zawierają opisy właściwości przydziału skrzynki pocztowej, które są wyświetlane w kolumnach w tabelach opisanych w poniższych sekcjach.

### <a name="mailboxes-on-hold-without-an-archive"></a>Skrzynki pocztowe wstrzymane bez archiwum

W poniższej tabeli wymieniono liczbę zablokowanych skrzynek pocztowych, które zbliżają się do limitu przydziału, ale nie mają włączonej archiwum skrzynki pocztowej. Każda kolumna w tabeli identyfikuje określony limit przydziału i liczbę skrzynek pocztowych zbliżających się do tego limitu przydziału.

| # Skrzynki pocztowe ProhibitSendReceiveQuota (ostrzeżenie)| # Skrzynki pocztowe ProhibitSendReceiveQuota (krytyczne)** |# Skrzynki pocztowe RecoverableItemsQuota (ostrzeżenie)|# Skrzynki pocztowe RecoverableItemsQuota (krytyczne)** |
|:--------------|:--------------|:------------------|:--------------- |
| 2             | 2             | 1                 | 0               |
||||

Administratorzy mogą wykonać akcję dla tych skrzynek pocztowych, aby włączyć skrzynkę pocztową archiwum i upewnić się, że zasady archiwum MRM (czyli zasady przechowywania mrm w Exchange Online, który przenosi elementy do skrzynki pocztowej archiwum) są stosowane do skrzynki pocztowej, tak aby elementy były przenoszone do skrzynki pocztowej archiwum. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad archiwum i usuwania dla skrzynek pocztowych](../compliance/set-up-an-archive-and-deletion-policy-for-mailboxes.md).

Po włączeniu archiwum skrzynki pocztowej zalecamy rozważenie zwiększenia limitu przydziału dla folderu Elementy możliwe do odzyskania. Zapobiega to przekroczeniu limitu przydziału dla folderu Elementy możliwe do odzyskania dla skrzynek pocztowych, które są wstrzymane. Aby uzyskać więcej informacji, zobacz [Zwiększanie limitu przydziału elementów możliwych do odzyskania dla skrzynek pocztowych wstrzymanych](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="mailboxes-on-hold-with-an-archive"></a>Skrzynki pocztowe wstrzymane z archiwum

W poniższej tabeli wymieniono liczbę zablokowanych skrzynek pocztowych, które zbliżają się do limitu przydziału i mają włączoną skrzynkę pocztową archiwum.

|# Skrzynki pocztowe ProhibitSendReceiveQuota (ostrzeżenie) |# Skrzynki pocztowe ProhibitSendReceiveQuota (krytyczne) |# Skrzynki pocztowe RecoverableItemsQuota (ostrzeżenie) |# Skrzynki pocztowe RecoverableItemsQuota (krytyczne)** |
|:--------------|:--------------|:------------------|:--------------- |
| 1             | 1             | 6                 | 0               |
||||

W przypadku tych skrzynek pocztowych administratorzy mogą podjąć działania w celu zwiększenia limitu przydziału dla folderu Elementy możliwe do odzyskania. Aby uzyskać więcej informacji, zobacz [Zwiększanie limitu przydziału elementów możliwych do odzyskania dla skrzynek pocztowych wstrzymanych](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

Administratorzy powinni również upewnić się, że zasady archiwum MRM, które przenosi elementy do skrzynki pocztowej archiwum, są również stosowane do skrzynek pocztowych, a okres przechowywania zasad archiwum jest wystarczająco krótki, aby elementy nie były zachowywane zbyt długo w podstawowej skrzynce pocztowej, zanim zostaną przeniesione do archiwum.

> [!NOTE]
> Zasady archiwum MRM przenoszą również elementy z folderu Elementy do odzyskania w podstawowej skrzynce pocztowej do folderu Elementy możliwe do odzyskania w odpowiedniej skrzynce pocztowej archiwum. Ta funkcja zapobiega przekroczeniu limitu przydziału dla przydziału elementów możliwych do odzyskania przez skrzynkę pocztową.

### <a name="mrm-retention-policies-in-your-organization"></a>Zasady przechowywania mrm w organizacji

Porady dotyczące obsługi użycia skrzynek pocztowych mogą również zawierać tabelę z informacjami o zasadach przechowywania mrm w organizacji oraz o tym, czy skrzynki pocztowe, które są zasadami przechowywania, mają skrzynkę pocztową archiwum. Aby uzyskać więcej informacji na temat zasad przechowywania, zobacz [Tagi przechowywania i zasady przechowywania w Exchange Online](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

| RetentionPolicyGuid | Typ skrzynki pocztowej | HasMoveDumpsterToArchiveTag | HasMovePrimaryToArchiveTag | HasPersonalArchiveTag |  Skrzynek pocztowych |
|:--------------|:--------------|:---------------|:---------------|:---------------|:--------------- |
| 6c041498-1611-5011-a058-1156ce60890c | PrimaryWithArchive | True | False | True | 398 |
| 6c041498-1611-5011-a058-1156ce60890c | Podstawowy | True | False | True | 10 |
| 749ceecc-d49d-4000-a9d5-594dbaea1e56 | PrimaryWithArchive | False | True | False | 7 |
| 269f6a85-1234-4648-8cde-59bbc7bc67d0 | PrimaryWithArchive | True | True | True | 1 |
| 13fb778d-e1cb-4c44-5768-ad4282906c1f | PrimaryWithArchive | True | True  | False | 1 |
|||||||

Na poniższej liście opisano każdą kolumnę w poprzedniej tabeli.

- **RetentionPolicyGuid**: identyfikator GUID zasad przechowywania przypisanych do skrzynek pocztowych w organizacji. W poprzednim przykładzie istnieją dwa oddzielne wiersze dla tych samych zasad przechowywania. Pierwszy wiersz wskazuje liczbę skrzynek pocztowych z archiwum, do których przypisano zasady. Drugi wiersz wskazuje liczbę skrzynek pocztowych bez archiwum, do których przypisano te same zasady.

   Aby uzyskać więcej informacji na temat zasad przechowywania wymienionych w tej kolumnie, uruchom następujące polecenie w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-RetentionPolicy <GUID> | FL
   ```

   Wartość właściwości **Nazwa** jest nazwą zasad przechowywania wyświetlanych na stronie **Zasady przechowywania** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>.

- **Typ skrzynki pocztowej**: określa typ skrzynek pocztowych, do których są przypisane zasady. Wartości obejmują *podstawowe* (skrzynki pocztowe bez archiwum) lub *PrimaryWithArchive* (skrzynki pocztowe z archiwum). Jeśli wartość w tej kolumnie to *Podstawowa*, należy włączyć archiwum dla skrzynek pocztowych (kolumna **Skrzynka pocztowa** wskazuje liczbę tych skrzynek pocztowych), do których przypisano zasady. W przeciwnym razie zasady archiwum lub osobisty tag archiwum nie będą działać, ponieważ nie ma archiwum do przenoszenia elementów.

- **HasMoveDumpsterToArchiveTag**: wskazuje, że zasady przechowywania zawierają tag przechowywania, który przenosi elementy w folderze Elementy możliwe do odzyskania (nazywanym również *śmietnikiem*) w podstawowej skrzynce pocztowej do folderu Elementy możliwe do odzyskania w archiwum. Ten typ tagu przechowywania jest ustawiany przez administratora. Jeśli okres przechowywania tagu elementów możliwych do odzyskania jest zbyt długi, skrócenie okresu przechowywania powinno zapobiec zbliżaniu się skrzynek pocztowych do limitu przydziału dla folderu Elementy możliwe do odzyskania. Jeśli na przykład okres przechowywania jest ustawiony na 30 dni, zmniejszenie go do trzech lub pięciu dni może pomóc.  Aby uzyskać więcej informacji, zobacz [Zwiększanie limitu przydziału elementów możliwych do odzyskania dla skrzynek pocztowych wstrzymanych](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

- **HasMovePrimaryToArchiveTag**: wskazuje, czy w zasadach przechowywania znajduje się domyślny tag przechowywania "przenieś do archiwum" (nazywany również *zasadami archiwum*). W takim przypadku wiadomości zostaną przeniesione ze zwykłych folderów w podstawowej skrzynce pocztowej do archiwum skrzynki pocztowej. Ten typ tagu przechowywania jest ustawiany przez administratora. Ponownie, jeśli okres przechowywania tego tagu jest zbyt krótki, użytkownicy mogą mieć problemy z ciągłym osiągnięciem limitu przydziału dla podstawowej skrzynki pocztowej. Skrócenie okresu przechowywania zasad archiwum może pomóc rozwiązać ten problem.

- **HasPersonalArchiveTag**: wskazuje, czy zasady przechowywania zawierają osobisty tag "przenieś do archiwum". Jeśli zasady przechowywania zawierają osobisty tag "Przenieś do archiwum", użytkownicy mogą zastosować ten tag do folderów i wiadomości w skrzynce pocztowej, aby przenieść elementy do archiwum. Użytkownicy mogą również skonfigurować regułę skrzynki odbiorczej, aby przenosić komunikaty do folderu z zastosowanym tagiem. W obu przypadkach może to pomóc w przeniesieniu elementów do archiwum, aby uniknąć osiągnięcia limitu przydziału dla podstawowej skrzynki pocztowej.

- **Skrzynki pocztowe**: wskazuje liczbę skrzynek pocztowych (z archiwum lub bez niego, co jest wskazane w kolumnie **MailboxType** ), do której są przypisane zasady przechowywania.

## <a name="how-often-will-i-see-these-service-advisories"></a>Jak często będą widoczne te porady dotyczące usług?

Jeśli nie podejmiesz działań w celu rozwiązania problemów z limitem przydziału, możesz spodziewać się tego typu porad dotyczących usług co siedem dni. Kolejne porady dotyczące usług mogą zawierać wyższe liczby skrzynek pocztowych dla innych skrzynek pocztowych, które zbliżają się do limitu przydziału. Jeśli podejmiesz działania w celu rozwiązania problemów z limitami przydziału, ta porada dotycząca usługi będzie miała miejsce tylko wtedy, gdy zostanie zidentyfikowana inna skrzynka pocztowa z problemami z limitem przydziału.

## <a name="more-information"></a>Więcej informacji

- Aby uzyskać informacje na temat rozwiązywania problemów ze skrzynką pocztową archiwum i rozwiązywania ich, zobacz [rozwiązywanie problemów z Microsoft Purview](/office365/troubleshoot/microsoft-365-compliance-welcome).

- Aby uzyskać wskazówki dotyczące identyfikowania blokad umieszczonych w skrzynce pocztowej, zobacz [How to identify the type of hold placed on a mailbox (Jak zidentyfikować typ blokady umieszczonej w skrzynce pocztowej](../compliance/identify-a-hold-on-an-exchange-online-mailbox.md)).
