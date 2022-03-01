---
title: Alerty usługi użycia skrzynki pocztowej
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
description: Alerty usługi użycia skrzynki pocztowej są służące do monitorowania skrzynek pocztowych w chmurze, które osiągają swój przydział skrzynki pocztowej.
ms.openlocfilehash: 311be4159d45b19ce1123baa840eebdf844840ec
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63012523"
---
# <a name="service-alerts-for-mailbox-utilization-in-exchange-online-monitoring"></a>Alerty usługi dotyczące użycia skrzynek pocztowych Exchange Online monitorowanie

Opublikowano nowy alert usługi Exchange Online, który informuje o skrzynkach pocztowych, które znajdują się w holdie, które mogą przekroczyć limit przydziału. Te alerty usługi zapewniają widoczność liczby skrzynek pocztowych w organizacji, które mogą wymagać interwencji administratora.

Alerty usługi są wyświetlane w centrum administracyjne platformy Microsoft 365. Aby wyświetlić te alerty usługi, przejdź do strony Kondycja usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**HealthService**</a> >  >  **Exchange Online** a następnie kliknij **kartę Aktywne** problemy. Oto przykład alertu użycia skrzynki pocztowej w usłudze.

:::image type="content" alt-text="Alert usługi użycia skrzynki pocztowej." source="../media/MailboxUtilizationServiceAlert.png" lightbox="../media/MailboxUtilizationServiceAlert.png":::

Aby wyświetlić listę skrzynek pocztowych, które zbliżają się do limitu przydziału magazynowania (nazywany raportem użycia skrzynki *pocztowej), kliknij* wyróżniony link na poniższym zrzucie ekranu. Ten link jest wyświetlany w alercie usługi.

:::image type="content" alt-text="Link do raportu o użyciu skrzynki pocztowej." source="../media/LinkToMailboxUsageReport.png" lightbox="../media/LinkToMailboxUsageReport.png":::

Bezpośredni adres URL raportu o użyciu skrzynki pocztowej to .<https://admin.microsoft.com/Adminportal/Home?source=applauncher#/reportsUsage/MailboxUsage>

## <a name="what-do-these-service-alerts-indicate"></a>Co oznaczają te alerty usługi?

Alerty usługi dotyczące użycia skrzynki pocztowej informują administratorów o skrzynkach pocztowych w chmurze, które zbliża się do limitu przydziału magazynowania skrzynki pocztowej. Do typów blokady, które mogą być umieszczane w skrzynkach pocztowych, należą: blokady w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych i zasady przechowywania Microsoft 365 (skonfigurowane tak, aby zachowywały dane). Gdy skrzynka pocztowa znajduje się w stanie przechowywania, użytkownicy (lub zautomatyzowane procesy) nie mogą trwale usuwać danych ze swoich skrzynek pocztowych. Zamiast tego administratorzy muszą skonfigurować zasady przechowywania MRM w programie Exchange Online (wbudowane w zasady zgodności organizacji dotyczące przechowywania danych) w celu przenoszenia danych z podstawowej skrzynki pocztowej użytkownika do jego archiwaowej skrzynki pocztowej. Jeśli nie, a skrzynka pocztowa w archiwum osiągnie stan krytyczny lub ostrzegawczy, administratorzy muszą włączyć archiwalne skrzynki pocztowe i włączyć automatyczne rozszerzanie archiwizacji, a następnie upewnić się, że okres przechowywania zasad archiwizacji przypisanych do skrzynki pocztowej (która przenosi wiadomości [e-mail](../compliance/enable-autoexpanding-archiving.md) z podstawowej skrzynki pocztowej do archiwalnej skrzynki pocztowej) jest wystarczająco krótki.[](../compliance/enable-archive-mailboxes.md) Jeśli nic nie zostanie wykonane w celu rozwiązania problemów z przydziałem zidentyfikowanych przez alerty usługi użycia skrzynki pocztowej, użytkownicy mogą nie być w stanie wysyłać ani odbierać wiadomości e-mail ani zaproszeń na spotkania.

Alert usługi dla użycia skrzynki pocztowej zawiera tabele dotyczące liczby skrzynek pocztowych, które zbliżają się do limitu przydziału. W poniższych sekcjach opisano informacje zawarte w tych tabelach oraz działania, które administratorzy mogą podjąć, aby upewnić się, że skrzynki pocztowe nie przekraczają ich przydziału.

> [!NOTE]
> Alerty usługi zawierają opisy właściwości przydziału skrzynki pocztowej wyświetlane w kolumnach w tabelach opisanych w poniższych sekcjach.

### <a name="mailboxes-on-hold-without-an-archive"></a>Skrzynki pocztowe w archiwum

W poniższej tabeli wymieniono liczbę skrzynek pocztowych w archiwum, które zbliżają się do limitu przydziału, ale nie mają włączonej archiwaowej skrzynki pocztowej. Każda kolumna w tabeli określa określony przydział i liczbę skrzynek pocztowych zbliżających się do tego przydziału.

| # Mailboxes ProhibitSendReceiveQuota (warning)| # Mailboxes ProhibitSendReceiveQuota (Critical)** |# Mailboxes RecoverableItemsQuota (Ostrzeżenie)|# Mailboxes RecoverableItemsQuota (Critical)** |
|:--------------|:--------------|:------------------|:--------------- |
| 2             | 2             | 1                 | 0               |
||||

Administratorzy akcji mogą włączyć archiwacyjną skrzynkę pocztową i upewnić się, że zasady archiwizacji MRM (czyli zasady przechowywania MRM w programie Exchange Online, które przeniosą elementy do archiwaowej skrzynki pocztowej) są stosowane do skrzynki pocztowej w celu przenoszenia elementów do archiwaowej skrzynki pocztowej. Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad archiwizacji i usuwania dla skrzynek pocztowych](../compliance/set-up-an-archive-and-deletion-policy-for-mailboxes.md).

Po włączeniu archiwazyjnej skrzynki pocztowej zalecamy zwiększenie przydziału dla folderu Elementy do odzyskania. Pomaga to zapobiec przekroczeniu przydziału dla folderu Elementy odzyskiwalne dla skrzynek pocztowych umieszczonych w hold. Aby uzyskać więcej informacji, zobacz Zwiększanie przydziału elementów [odzyskiwalnych dla skrzynek pocztowych w hold.](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md)

### <a name="mailboxes-on-hold-with-an-archive"></a>Skrzynki pocztowe w archiwum

W poniższej tabeli wymieniono liczbę skrzynek pocztowych w archiwum, które zbliżają się do ich przydziału i mają włączoną archiwacyjną skrzynkę pocztową.

|# Mailboxes ProhibitSendReceiveQuota (warning) |# Mailboxes ProhibitSendReceiveQuota (Critical) |# Mailboxes RecoverableItemsQuota (Ostrzeżenie) |# Mailboxes RecoverableItemsQuota (Critical)** |
|:--------------|:--------------|:------------------|:--------------- |
| 1             | 1             | 6                 | 0               |
||||

Czynności, które administratorzy mogą podjąć w przypadku tych skrzynek pocztowych, to zwiększenie przydziału folderu Elementy do odzyskania. Aby uzyskać więcej informacji, zobacz Zwiększanie przydziału elementów [odzyskiwalnych dla skrzynek pocztowych w hold.](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md)

Administratorzy powinni również upewnić się, że zasady archiwizacji MRM, które przenosi elementy do archiwaowej skrzynki pocztowej, są również stosowane do skrzynek pocztowych, a okres przechowywania zasad archiwizacji jest na tyle krótki, że elementy nie są zachowywane zbyt długo w podstawowej skrzynce pocztowej, zanim zostaną przeniesione do archiwum.

> [!NOTE]
> Zasady archiwizacji MRM przenoszenie elementów z folderu Elementy do odzyskania w podstawowej skrzynce pocztowej do folderu Elementy do odzyskania w odpowiedniej archiwanej skrzynce pocztowej. Funkcja ta pomaga zapobiec przekroczeniu limitu przydziału dla skrzynki pocztowej dla przydziału Elementy odzyskiwalne.

### <a name="mrm-retention-policies-in-your-organization"></a>Zasady przechowywania MRM w organizacji

Alerty usługi dla użycia skrzynek pocztowych mogą również zawierać tabelę z informacjami na temat zasad przechowywania MRM w organizacji i tego, czy skrzynki pocztowe, które są zasadami przechowywania, mają archiwalne skrzynki pocztowe. Aby uzyskać więcej informacji na temat zasad przechowywania, zobacz [Tagi przechowywania i zasady przechowywania w programie Exchange Online](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

| RetentionPolicyGuid | MailboxType (Typ skrzynki pocztowej) | HasMoveDumpsterToArchiveTag | HasMovePrimaryToArchiveTag | HasPersonalArchiveTag |  Skrzynki pocztowe |
|:--------------|:--------------|:---------------|:---------------|:---------------|:--------------- |
| 6c041498-1611-5011-a058-1156ce60890c | PrimaryWithArchive | True (Prawda) | False (Fałsz | True (Prawda) | 398 |
| 6c041498-1611-5011-a058-1156ce60890c | Podstawowa | True (Prawda) | False (Fałsz | True (Prawda) | 10 |
| 749ceecc-d49d-4000-a9d5-594dbaea1e56 | PrimaryWithArchive | False (Fałsz | True (Prawda) | False (Fałsz | 7 |
| 269f6a85-1234-4648-8cde-59bbc7bc67d0 | PrimaryWithArchive | True (Prawda) | True (Prawda) | True (Prawda) | 1 |
| 13fb778d-e1cb-4c44-5768-ad4282906c1f | PrimaryWithArchive | True (Prawda) | True (Prawda)  | False (Fałsz | 1 |
|||||||

Na poniższej liście opisano każdą kolumnę w poprzedniej tabeli.

- **RetentionPolicyGuid**: Identyfikator GUID zasad przechowywania przypisanych do skrzynek pocztowych w organizacji. W poprzednim przykładzie istnieją dwa oddzielne wiersze dla tych samych zasad przechowywania. Pierwszy wiersz wskazuje liczbę skrzynek pocztowych z archiwum, do których przypisano zasady. Drugi wiersz wskazuje liczbę skrzynek pocztowych bez archiwum, do których przypisano te same zasady.

   Aby uzyskać więcej informacji na temat zasad przechowywania wymienionych w tej kolumnie, uruchom następujące polecenie w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-RetentionPolicy <GUID> | FL
   ```

   Wartość właściwości **Name** (Nazwa) to nazwa zasad przechowywania wyświetlanych na stronie Zasady przechowywania w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a>.

- **MailboxType**( Typ skrzynki pocztowej): określa typ skrzynek pocztowych, do których przypisano zasady. Wartości to *Podstawowe* (skrzynki pocztowe bez archiwum) lub *PrimaryWithArchive* (skrzynki pocztowe z archiwum). Jeśli ta kolumna ma wartość Podstawowa *, należy* włączyć archiwum dla skrzynek pocztowych (kolumna Skrzynka  pocztowa wskazuje liczbę tych skrzynek pocztowych), do których przypisano zasady. W przeciwnym razie tag zasad archiwizacji lub archiwum osobistego nie będzie działać, ponieważ nie ma archiwum służącego do przenoszenia elementów.

- **HasMoveDumpsterToArchiveTag**: wskazuje, że zasady przechowywania zawierają tag przechowywania, który przenosi elementy z folderu Elementy do odzyskania (nazywanego również magazynem *) w* podstawowej skrzynce pocztowej do folderu Elementy do odzyskania w archiwum. Ten typ tagu przechowywania jest ustawiany przez administratora. Jeśli okres przechowywania tagu elementów odzyskiwalnych jest zbyt długi, skrócenie okresu przechowywania powinno zapobiec zbliżaniu się przydziału folderu Elementy do odzyskania dla skrzynek pocztowych. Jeśli na przykład ustawiono okres przechowywania na 30 dni, może to być pomocne po jego ograniczeniu do trzech lub pięciu dni.  Aby uzyskać więcej informacji, zobacz Zwiększanie przydziału elementów [odzyskiwalnych dla skrzynek pocztowych w hold.](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md)

- **HasMovePrimaryToArchiveTag**: Wskazuje, czy w zasadach przechowywania jest domyślny tag przechowywania "przenieś do archiwum" (nazywany również zasadami archiwizacji). W takim przypadku wiadomości zostaną przeniesione ze zwykłych folderów podstawowej skrzynki pocztowej do archiwaowej skrzynki pocztowej. Ten typ tagu przechowywania jest ustawiany przez administratora. Również wtedy, gdy okres przechowywania dla tego tagu jest zbyt krótki, użytkownicy mogą mieć problemy z ciągłym osiągnięciem przydziału dla podstawowej skrzynki pocztowej. Skrócenie okresu przechowywania zasad archiwizacji może pomóc rozwiązać ten problem.

- **HasPersonalArchiveTag**: Wskazuje, czy zasady przechowywania zawierają osobisty tag "przenieś do archiwum". Jeśli zasady przechowywania zawierają osobisty tag "przenieś do archiwum", użytkownicy mogą zastosować ten tag do folderów i wiadomości w swoich skrzynkach pocztowych, aby przenosić elementy do archiwum. Użytkownicy mogą również skonfigurować regułę skrzynki odbiorczej w celu przenoszenia wiadomości do folderu, do którym zastosowano to otagowanie. W obu przypadkach może to ułatwić przenoszenie elementów do archiwum w celu uniknięcia osiągnięcia limitu przydziału dla podstawowej skrzynki pocztowej.

- **Skrzynki** pocztowe. Wskazuje liczbę skrzynek pocztowych (z archiwum lub bez niego, co wskazuje kolumna **Typ** Skrzynki pocztowej), do których przypisano zasady przechowywania.

## <a name="how-often-will-i-see-these-service-alerts"></a>Jak często będą pojawiać się te alerty usługi?

Jeśli nie podejmiesz działań w celu rozwiązania problemów z przydziałem, możesz się spodziewać tego typu alertu usługi co cztery dni. Kolejne alerty usługi mogą zawierać większą liczbę skrzynek pocztowych dla innych skrzynek pocztowych, które zbliżają się do limitu przydziału. Jeśli podejmiesz działania w celu rozwiązania problemów z przydziałem, ten alert usługi wystąpi tylko wtedy, gdy zostanie zidentyfikowana inna skrzynka pocztowa z problemami z przydziałem.

## <a name="more-information"></a>Więcej informacji

- Aby uzyskać informacje na temat rozwiązywania problemów z archiwaną skrzynką pocztową i rozwiązywania tych problemów, [Microsoft 365 rozwiązywanie problemów ze zgodnością](/office365/troubleshoot/microsoft-365-compliance-welcome).

- Aby uzyskać wskazówki dotyczące identyfikowania blokady umieszczonej w skrzynce pocztowej, zobacz Jak zidentyfikować typ blokady [umieszczany w skrzynce pocztowej](../compliance/identify-a-hold-on-an-exchange-online-mailbox.md).
