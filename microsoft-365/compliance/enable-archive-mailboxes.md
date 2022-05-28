---
title: Włączanie archiwalnych skrzynek pocztowych dla Microsoft 365
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
description: Dowiedz się, jak włączyć lub wyłączyć archiwalne skrzynki pocztowe, aby obsługiwać wymagania dotyczące przechowywania komunikatów, zbierania elektronicznych materiałów dowodowych i przechowywania wiadomości w organizacji.
ms.openlocfilehash: f95da36b48389bba2bd640825071dbff5c6ddb3d
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772429"
---
# <a name="enable-archive-mailboxes-in-the-microsoft-purview-compliance-portal"></a>Włączanie archiwalnych skrzynek pocztowych w portal zgodności Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Archiwizowanie w Microsoft 365 (nazywane również *archiwizowaniem w miejscu*) zapewnia użytkownikom więcej miejsca do magazynowania skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o archiwalnych skrzynkach pocztowych](archive-mailboxes.md).

Informacje zawarte w tym artykule umożliwiają włączanie lub wyłączanie archiwum skrzynki pocztowej w portal zgodności Microsoft Purview lub przy użyciu programu PowerShell. Dowiedz się również, jak uruchomić automatyczne sprawdzanie diagnostyczne w archiwum skrzynki pocztowej użytkownika w celu zidentyfikowania wszelkich problemów i sugerowanych rozwiązań.

## <a name="get-the-necessary-permissions"></a>Uzyskiwanie niezbędnych uprawnień

Musisz mieć przypisaną rolę Adresaci poczty w Exchange Online, aby włączyć lub wyłączyć archiwalne skrzynki pocztowe. Domyślnie ta rola jest przypisywana do grup ról Zarządzanie adresatami i Zarządzanie organizacją na stronie **Uprawnienia** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>. 

Jeśli nie widzisz strony **Archiwum** w portal zgodności Microsoft Purview, poproś administratora o przypisanie Ci niezbędnych uprawnień.

## <a name="enable-an-archive-mailbox"></a>Włączanie archiwum skrzynki pocztowej

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> i zaloguj się.

2. W lewym okienku portalu zgodności wybierz pozycję **Archiwum zarządzania cyklem** >  życia danych.

   Na stronie **Archiwum** kolumna  **Skrzynka pocztowa Archiwum** określa, czy skrzynka pocztowa archiwum jest włączona, czy wyłączona dla każdego użytkownika.

   > [!NOTE]
   > Strona **Archiwum** zawiera maksymalnie 500 użytkowników. Użyj pola wyszukiwania, jeśli nie możesz od razu wyświetlić żądanej nazwy użytkownika.

3. Na liście skrzynek pocztowych wybierz użytkownika, aby włączyć skrzynkę pocztową dla archiwum, a następnie wybierz opcję **Włącz archiwum** :
    
   ![Włącz opcję archiwum dla wybranego użytkownika.](../media/enable-archive-option.png)
    
   Zostanie wyświetlone ostrzeżenie informujące, że po włączeniu archiwum skrzynki pocztowej elementy w skrzynce pocztowej użytkownika starsze niż zasady archiwizacji przypisane do skrzynki pocztowej zostaną przeniesione do nowej skrzynki pocztowej archiwum. Domyślne zasady archiwum, które są częścią zasad przechowywania przypisanych do Exchange Online skrzynek pocztowych, przenosi elementy do archiwum skrzynki pocztowej dwa lata po dacie dostarczenia elementu do skrzynki pocztowej lub utworzenia przez użytkownika. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o archiwalnych skrzynkach pocztowych](archive-mailboxes.md).

5. Wybierz pozycję **Włącz** , aby potwierdzić.

   Utworzenie archiwum skrzynki pocztowej może potrwać kilka chwil. Po utworzeniu opcja **Włączone** jest wyświetlana w kolumnie **Archiwum skrzynki pocztowej** dla wybranego użytkownika, chociaż może być konieczne odświeżenie strony w celu wyświetlenia zmiany stanu.

## <a name="disable-an-archive-mailbox"></a>Wyłączanie archiwum skrzynki pocztowej

Podobnie jak w przypadku włączania archiwum skrzynki pocztowej, możesz użyć strony **Archiwum** w portal zgodności Microsoft Purview, aby wyłączyć skrzynkę pocztową archiwum użytkownika. Tym razem wybierz opcję **Wyłącz archiwum** po wybraniu użytkownika.

Po wyłączeniu archiwum skrzynki pocztowej można ponownie połączyć ją z podstawową skrzynką pocztową użytkownika w ciągu 30 dni od jej wyłączenia. W takim przypadku oryginalna zawartość archiwum skrzynki pocztowej są przywracane. Po 30 dniach zawartość oryginalnej skrzynki pocztowej archiwum zostanie trwale usunięta i nie będzie można jej odzyskać. Jeśli więc ponownie włączysz archiwum dłużej niż 30 dni po jego wyłączeniu, zostanie utworzona nowa skrzynka pocztowa archiwum.

Domyślne zasady archiwum przypisane do skrzynek pocztowych użytkowników przenosi elementy do archiwum skrzynki pocztowej dwa lata po dacie dostarczenia elementu. Jeśli wyłączysz archiwum skrzynki pocztowej użytkownika, nie zostaną podjęte żadne akcje dotyczące elementów skrzynki pocztowej i pozostaną one w podstawowej skrzynce pocztowej użytkownika.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Używanie Exchange Online programu PowerShell do włączania lub wyłączania archiwalnych skrzynek pocztowych

Do włączania archiwalnych skrzynek pocztowych można również użyć programu Exchange Online PowerShell. Głównym powodem korzystania z programu PowerShell jest szybkie włączenie archiwum skrzynki pocztowej dla wszystkich użytkowników w organizacji.

Pierwszym krokiem jest nawiązanie połączenia z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Po nawiązaniu połączenia z Exchange Online możesz uruchomić polecenia w poniższych sekcjach, aby włączyć lub wyłączyć archiwalne skrzynki pocztowe.

### <a name="enable-archive-mailboxes"></a>Włącz archiwalne skrzynki pocztowe

Uruchom następujące polecenie, aby włączyć skrzynkę pocztową archiwum dla jednego użytkownika.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Uruchom następujące polecenie, aby włączyć archiwum skrzynki pocztowej dla wszystkich użytkowników w organizacji (których skrzynka pocztowa archiwum nie jest obecnie włączona).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>Wyłączanie archiwalnych skrzynek pocztowych

Uruchom następujące polecenie, aby wyłączyć skrzynkę pocztową archiwum dla jednego użytkownika.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Uruchom następujące polecenie, aby wyłączyć skrzynkę pocztową archiwum dla wszystkich użytkowników w organizacji (których skrzynka pocztowa archiwum jest obecnie włączona).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>Uruchamianie diagnostyki w archiwalnych skrzynkach pocztowych

Możesz uruchomić automatyczne sprawdzanie diagnostyczne w skrzynce pocztowej archiwum użytkownika, aby zidentyfikować wszelkie problemy i sugerowane rozwiązania.

Aby uruchomić test diagnostyczny, kliknij przycisk poniżej. 

> [!div class="nextstepaction"]
> [Uruchamianie testów: archiwum skrzynki pocztowej](https://aka.ms/PillarArchiveMailbox)

![Uruchom diagnostykę w archiwum skrzynki pocztowej.](../media/ArchiveMailboxDiagnostics.png)

W Centrum administracyjne platformy Microsoft 365 zostanie otwarta strona wysuwana. Wprowadź adres e-mail skrzynki pocztowej, którą chcesz sprawdzić, i kliknij pozycję **Uruchom testy**.

> [!NOTE]
> Aby użyć sprawdzania diagnostycznego skrzynki pocztowej archiwum, musisz być administratorem globalnym Microsoft 365. Ponadto ta funkcja nie jest dostępna w chmurach Microsoft 365 government, Microsoft 365 obsługiwanych przez firmę 21Vianet lub Microsoft 365 Niemczech.

## <a name="instructions-for-end-users"></a>Instrukcje dla użytkowników końcowych

Wyjaśnij użytkownikom, jak działa ich archiwum skrzynki pocztowej i jak mogą z nią korzystać w Outlook na Windows, macOS i w Internecie. Najbardziej efektywna dokumentacja zostanie dostosowana dla Twojej organizacji. Aby uzyskać podstawowe instrukcje, zobacz [Zarządzanie magazynem poczty e-mail przy użyciu skrzynek pocztowych archiwum online](https://prod.support.services.microsoft.com/en-us/office/manage-email-storage-with-online-archive-mailboxes-1cae7d17-7813-4fe8-8ca2-9a5494e9a721).

## <a name="next-steps"></a>Następne kroki

Rozważ włączenie [automatycznego rozszerzania archiwizacji](autoexpanding-archiving.md) w celu uzyskania dodatkowego miejsca do magazynowania. Aby uzyskać instrukcje, zobacz [Włączanie automatycznego rozszerzania archiwizacji](enable-autoexpanding-archiving.md).
