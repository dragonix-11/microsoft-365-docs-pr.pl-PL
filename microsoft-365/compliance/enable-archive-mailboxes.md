---
title: Włączanie archiwalnych skrzynek pocztowych na Microsoft 365 zgodności
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 268a109e-7843-405b-bb3d-b9393b2342ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
description: Dowiedz się, jak włączyć lub wyłączyć archiwalne skrzynki pocztowe w celu obsługi wymagań organizacji w zakresie przechowywania wiadomości, zbierania elektronicznych materiałów dowodowych i archiwizacji.
ms.openlocfilehash: be7939f11c6aea0161f76c3796ca2ff8bd515ba0
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010623"
---
# <a name="enable-archive-mailboxes-in-the-compliance-center"></a>Włączanie archiwalnych skrzynek pocztowych w centrum zgodności

Archiwizacja w Microsoft 365 (nazywana również archiwizacją *miejscową) zapewnia* użytkownikom dodatkowe miejsce do magazynowania skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Informacje o archiwalnych skrzynkach pocztowych](archive-mailboxes.md).

Skorzystaj z informacji w tym artykule, aby włączyć lub wyłączyć archiwacyjną skrzynkę pocztową w Centrum zgodności platformy Microsoft 365 lub przy użyciu programu PowerShell. Dowiedz się także, jak uruchomić automatyczne sprawdzanie diagnostyczne archiwaowej skrzynki pocztowej użytkownika w celu zidentyfikowania problemów i sugerowanych rozwiązania.

## <a name="get-the-necessary-permissions"></a>Uzyskiwanie niezbędnych uprawnień

Aby włączyć lub wyłączyć archiwalne skrzynki pocztowe, musisz mieć przypisaną rolę Exchange Online adresatów poczty. Domyślnie ta rola jest przypisana do grup ról Zarządzanie adresatami i Zarządzanie organizacją na stronie Uprawnienia w  centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a>. 

Jeśli nie widzisz strony Archiwum **w** skoroszycie, Centrum zgodności platformy Microsoft 365 poproś administratora o przypisanie niezbędnych uprawnień.

## <a name="enable-an-archive-mailbox"></a>Włączanie archiwaowej skrzynki pocztowej

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się.

2. W lewym okienku okna Centrum zgodności platformy Microsoft 365 kliknij pozycję Zarządzanie **informacjami**, a następnie kliknij **kartę Archiwum**.

   Zostanie **wyświetlona** strona Archiwum. Kolumna **Archiwalne skrzynki** pocztowe wskazuje, czy archiwalne skrzynki pocztowe są włączone, czy wyłączone dla każdego użytkownika.

   > [!NOTE]
   > Strona **Archiwum** zawiera maksymalnie 500 użytkowników.

3. Na liście skrzynek pocztowych wybierz użytkownika, dla którego chcesz włączyć archiwalne skrzynki pocztowe.

   ![Kliknij pozycję Włącz w okienku szczegółów wybranego użytkownika, aby włączyć archiwalne skrzynki pocztowe.](../media/8b53cdec-d5c9-4c28-af11-611f95c37b34.png)

4. W okienku szczegółów dla wybranego użytkownika kliknij pozycję **Włącz**.

   Zostanie wyświetlone ostrzeżenie z informacją, że po włączeniu archiwalnej skrzynki pocztowej elementy w skrzynce pocztowej użytkownika, które są starsze niż zasady archiwizacji przypisane do skrzynki pocztowej, zostaną przeniesione do nowej archiwalnej skrzynki pocztowej. Domyślne zasady archiwizacji, które są częścią zasad przechowywania przypisanych do skrzynek pocztowych programu Exchange Online, przenosi elementy do archiwaowej skrzynki pocztowej dwa lata po tym, jak element został dostarczony do skrzynki pocztowej lub utworzony przez użytkownika. Aby uzyskać więcej informacji, zobacz **sekcję Więcej** informacji w tym artykule.

5. Kliknij **przycisk Tak,** aby włączyć archiwacyjną skrzynkę pocztową.

   Utworzenie archiwaowej skrzynki pocztowej może chwilę potrwać. Po utworzeniu archiwacyjna skrzynka **pocztowa: włączone** jest wyświetlana w okienku szczegółów dla wybranego użytkownika. Może być konieczne kliknięcie ikony **Odśwież**![.](../media/O365-MDM-Policy-RefreshIcon.gif) , aby zaktualizować informacje w okienku szczegółów.

> [!TIP]
> Możesz także włączyć zbiorczo archiwalne skrzynki pocztowe, zaznaczając wielu użytkowników z wyłączonymi archiwalnych skrzynek pocztowych (za pomocą klawiszy Shift i Ctrl). Po zaznaczeniu wielu skrzynek pocztowych kliknij pozycję **Włącz** w okienku szczegółów.

## <a name="disable-an-archive-mailbox"></a>Wyłączanie archiwaowej skrzynki pocztowej

Możesz również użyć strony **Archiwum** w Centrum zgodności platformy Microsoft 365, aby wyłączyć archiwacyjną skrzynkę pocztową użytkownika. Po wyłączeniu archiwazyjną skrzynkę pocztową możesz ponownie podłączyć ją do podstawowej skrzynki pocztowej użytkownika w ciągu 30 dni od jej wyłączenia. W takim przypadku zostanie przywrócona oryginalna zawartość archiwaowej skrzynki pocztowej. Po 30 dniach zawartość oryginalnej archiwaowej skrzynki pocztowej zostanie trwale usunięta i nie będzie można jej odzyskać. Jeśli więc ponownie włączysz archiwum po upływie 30 dni od wyłączenia go, zostanie utworzona nowa archiwalne skrzynka pocztowa.

Domyślne zasady archiwizacji przypisane do skrzynek pocztowych użytkowników przenosi elementy do archiwaowej skrzynki pocztowej dwa lata po ich dostarczaniu. Jeśli wyłączysz archiwacyjną skrzynkę pocztową użytkownika, elementy skrzynki pocztowej nie zostaną wykonane i pozostaną one w podstawowej skrzynce pocztowej użytkownika.

Aby wyłączyć archiwacyjną skrzynkę pocztową:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się.

2. W lewym okienku okna Centrum zgodności platformy Microsoft 365 kliknij pozycję Zarządzanie **informacjami**, a następnie kliknij **kartę Archiwum**.

   Zostanie **wyświetlona** strona Archiwum. Kolumna **Archiwalne skrzynki** pocztowe wskazuje, czy archiwalne skrzynki pocztowe są włączone, czy wyłączone dla każdego użytkownika.

   > [!NOTE]
   > Strona **Archiwum** zawiera maksymalnie 500 użytkowników.

3. Na liście skrzynek pocztowych wybierz użytkownika, dla którego chcesz wyłączyć archiwalne skrzynki pocztowe.

4. W okienku szczegółów kliknij pozycję **Wyłącz**.

   Zostanie wyświetlony komunikat ostrzegawczy z informacją, że na ponowne włączenie archiwatywnej skrzynki pocztowej będziesz mieć 30 dni, a po 30 dniach wszystkie informacje w archiwum zostaną trwale usunięte.

5. Kliknij **przycisk Tak,** aby wyłączyć archiwacyjną skrzynkę pocztową.

   Wyłączenie archiwacyjną skrzynki pocztowej może chwilę potrwać. Po wyłączeniu w okienku szczegółów wybranego użytkownika zostanie wyświetlona informacja Archiwizuj skrzynkę pocztową **:** wyłączona. Może być konieczne kliknięcie ikony **Odśwież**![.](../media/O365-MDM-Policy-RefreshIcon.gif) , aby zaktualizować informacje w okienku szczegółów.

> [!TIP]
> Archiwalne skrzynki pocztowe można również wyłączyć zbiorczo, zaznaczając wielu użytkowników z włączonymi archiwalnych skrzynek pocztowych (za pomocą klawiszy Shift i Ctrl). Po zaznaczeniu wielu skrzynek pocztowych kliknij pozycję **Wyłącz w** okienku szczegółów.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Włączanie Exchange Online archiwalnych skrzynek pocztowych przy użyciu programu PowerShell

Archiwalne skrzynki pocztowe można Exchange Online włączyć za pomocą programu PowerShell. Podstawowym powodem korzystania z programu PowerShell jest możliwość szybkiego włączenia archiwaowej skrzynki pocztowej dla wszystkich użytkowników w organizacji.

Pierwszym krokiem jest połączenie się z programem Exchange Online PowerShell. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Po na połączeniu z siecią Exchange Online można uruchomić polecenia z poniższych sekcji, aby włączyć lub wyłączyć archiwalne skrzynki pocztowe.

### <a name="enable-archive-mailboxes"></a>Włączanie archiwalnych skrzynek pocztowych

Uruchom następujące polecenie, aby włączyć archiwacyjną skrzynkę pocztową dla jednego użytkownika.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Uruchom następujące polecenie, aby włączyć archiwalne skrzynki pocztowe dla wszystkich użytkowników w organizacji (których archiwalne skrzynki pocztowe nie są obecnie włączone).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>Wyłączanie archiwalnych skrzynek pocztowych

Uruchom następujące polecenie, aby wyłączyć archiwacyjną skrzynkę pocztową dla jednego użytkownika.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Uruchom poniższe polecenie, aby wyłączyć archiwalne skrzynki pocztowe dla wszystkich użytkowników w organizacji (których archiwalne skrzynki pocztowe są obecnie włączone).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>Uruchamianie diagnostyki w archiwalnych skrzynkach pocztowych

W archiwaowej skrzynce pocztowej użytkownika możesz uruchomić automatyczne sprawdzanie diagnostyczne, aby zidentyfikować wszelkie problemy i sugerowane rozwiązania.

Aby uruchomić sprawdzanie diagnostyczne, kliknij przycisk poniżej. 

> [!div class="nextstepaction"]
> [Uruchom testy: archiwalne skrzynki pocztowe](https://aka.ms/PillarArchiveMailbox)

![Uruchamianie diagnostyki w archiwaowej skrzynce pocztowej.](../media/ArchiveMailboxDiagnostics.png)

W menu wysuwana zostanie centrum administracyjne platformy Microsoft 365. Wprowadź adres e-mail skrzynki pocztowej, którą chcesz sprawdzić, i kliknij pozycję **Uruchom testy**.

> [!NOTE]
> Musisz być administratorem globalnym usługi Microsoft 365 w celu korzystania z kontroli diagnostycznej archiwanych skrzynek pocztowych. Ponadto ta funkcja nie jest dostępna w chmurach Microsoft 365 Government, Microsoft 365 obsługiwane przez firmę 21Vianet lub Microsoft 365 Germany.

## <a name="next-steps"></a>Następne kroki

Rozważ włączenie [automatycznego rozszerzania archiwizacji w](autoexpanding-archiving.md) celu dodatkowego miejsca do magazynowania. Aby uzyskać instrukcje, [zobacz Włączanie automatycznego rozwijania archiwizacji](enable-autoexpanding-archiving.md).
