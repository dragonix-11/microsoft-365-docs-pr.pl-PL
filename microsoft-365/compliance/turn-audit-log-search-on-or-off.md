---
title: Włącz lub wyłącz inspekcję
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: e893b19a-660c-41f2-9074-d3631c95a014
ms.custom: seo-marvel-apr2020
description: Jak włączyć lub wyłączyć funkcję wyszukiwania dzienników inspekcji w portalu zgodności usługi Microsoft Purview, aby włączyć lub wyłączyć możliwość przeszukiwania dziennika inspekcji przez administratorów.
ms.openlocfilehash: e74effad1803b9a55167d1cd3bb5725bd042616a
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64991825"
---
# <a name="turn-auditing-on-or-off"></a>Włącz lub wyłącz inspekcję

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Rejestrowanie inspekcji zostanie domyślnie włączone dla organizacji Microsoft 365 i Office 365 przedsiębiorstw. Jednak podczas konfigurowania nowej organizacji Microsoft 365 lub Office 365 należy zweryfikować stan inspekcji organizacji. Aby uzyskać instrukcje, zobacz [sekcję Weryfikowanie stanu inspekcji organizacji](#verify-the-auditing-status-for-your-organization) w tym artykule. 

Gdy inspekcja w portalu zgodności usługi Microsoft Purview jest włączona, aktywność użytkownika i administratora w organizacji jest rejestrowana w dzienniku inspekcji i przechowywana przez 90 dni i do jednego roku w zależności od licencji przypisanej do użytkowników. Jednak organizacja może mieć powody, dla których nie chce rejestrować i zachowywać danych dziennika inspekcji. W takich przypadkach administrator globalny może zdecydować o wyłączeniu inspekcji w Microsoft 365.

> [!IMPORTANT]
> Jeśli wyłączysz inspekcję w Microsoft 365, nie możesz użyć interfejsu API działania zarządzania Office 365 ani usługi Microsoft Sentinel, aby uzyskać dostęp do danych inspekcji dla organizacji. Wyłączenie inspekcji przez wykonanie kroków opisanych w tym artykule oznacza, że żadne wyniki nie zostaną zwrócone podczas przeszukiwania dziennika inspekcji przy użyciu portalu zgodności lub po uruchomieniu polecenia cmdlet **Search-UnifiedAuditLog** w programie Exchange Online programu PowerShell. Oznacza to również, że dzienniki inspekcji nie będą dostępne za pośrednictwem interfejsu API działania zarządzania Office 365 ani usługi Microsoft Sentinel.
  
## <a name="before-you-turn-auditing-on-or-off"></a>Przed włączeniem lub wyłączeniem inspekcji

- Musisz mieć przypisaną rolę Dzienniki inspekcji w Exchange Online, aby włączyć lub wyłączyć inspekcję w organizacji Microsoft 365. Domyślnie ta rola jest przypisywana do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie **Uprawnienia** w centrum administracyjnym Exchange. Administratorzy globalni w Microsoft 365 są członkami grupy ról Zarządzanie organizacją w Exchange Online.

    > [!NOTE]
    > Użytkownicy muszą mieć przypisane uprawnienia w Exchange Online, aby włączyć lub wyłączyć inspekcję. Jeśli przypiszesz użytkownikom rolę Dzienniki inspekcji na stronie **Uprawnienia** w portalu zgodności, nie będą oni mogli włączać ani wyłączać inspekcji. Dzieje się tak, ponieważ podstawowe polecenie cmdlet jest Exchange Online poleceniem cmdlet programu PowerShell.

- Aby uzyskać instrukcje krok po kroku dotyczące przeszukiwania dziennika inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md). Aby uzyskać więcej informacji na temat interfejsu API działania zarządzania Microsoft 365, zobacz [Wprowadzenie z interfejsami API zarządzania Microsoft 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="verify-the-auditing-status-for-your-organization"></a>Weryfikowanie stanu inspekcji organizacji

Aby sprawdzić, czy inspekcja jest włączona dla organizacji, możesz uruchomić następujące polecenie w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

Wartość `True` właściwości  _UnifiedAuditLogIngestionEnabled_ wskazuje, że inspekcja jest włączona. Wartość `False` wskazuje, że inspekcja nie jest włączona.

> [!NOTE]
> Pamiętaj, aby uruchomić poprzednie polecenie w programie Exchange Online programu PowerShell. Do uruchomienia tego polecenia nie można użyć programu PowerShell security & Compliance.

## <a name="turn-on-auditing"></a>Włączanie inspekcji

Jeśli inspekcja nie jest włączona dla organizacji, możesz ją włączyć w portalu zgodności lub przy użyciu programu Exchange Online programu PowerShell. Może upłynąć kilka godzin po włączeniu inspekcji, zanim będzie można zwrócić wyniki podczas przeszukiwania dziennika inspekcji.
  
### <a name="use-the-compliance-center-to-turn-on-auditing"></a>Używanie centrum zgodności do włączania inspekcji

1. Przejdź do i <https://compliance.microsoft.com> zaloguj się.

2. W okienku nawigacji po lewej stronie portalu zgodności kliknij pozycję **Inspekcja**.

   Jeśli inspekcja nie jest włączona dla Organizacji, zostanie wyświetlony baner z monitem o rozpoczęcie rejestrowania aktywności użytkownika i administratora.

   ![Baner na stronie Inspekcja.](../media/AuditingBanner.png)

3. Kliknij baner **Start recording user and admin activity (Rozpocznij rejestrowanie użytkownika i działania administratora** ).

   Zmiana może potrwać do 60 minut.

### <a name="use-powershell-to-turn-on-auditing"></a>Włączanie inspekcji przy użyciu programu PowerShell

1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom następujące polecenie programu PowerShell, aby włączyć inspekcję.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    Zostanie wyświetlony komunikat informujący o tym, że może upłynąć do 60 minut, aż zmiana zostanie wprowadzona.
  
## <a name="turn-off-auditing"></a>Wyłączanie inspekcji

Aby wyłączyć inspekcję, należy użyć Exchange Online programu PowerShell.
  
1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom następujące polecenie programu PowerShell, aby wyłączyć inspekcję.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. Po chwili sprawdź, czy inspekcja jest wyłączona (wyłączona). Istnieją dwa sposoby wykonywania tej czynności:

    - W Exchange Online programu PowerShell uruchom następujące polecenie:

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      Wartość  `False` właściwości  _UnifiedAuditLogIngestionEnabled_ wskazuje, że inspekcja jest wyłączona.

    - Przejdź do strony **Inspekcja** w portalu zgodności.

      Jeśli inspekcja nie jest włączona dla Organizacji, zostanie wyświetlony baner z monitem o rozpoczęcie rejestrowania aktywności użytkownika i administratora.

## <a name="audit-records-when-auditing-status-is-changed"></a>Inspekcja rekordów po zmianie stanu inspekcji

Zmiany stanu inspekcji w organizacji są poddawane inspekcji. Oznacza to, że rekordy inspekcji są rejestrowane, gdy inspekcja jest włączona lub wyłączona. Możesz wyszukać te rekordy inspekcji w dzienniku inspekcji administratora Exchange.

Aby przeszukać dziennik inspekcji administratora Exchange w poszukiwaniu rekordów inspekcji generowanych podczas włączania lub wyłączania inspekcji, uruchom następujące polecenie w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Search-AdminAuditLog -Cmdlets Set-AdminAuditLogConfig -Parameters UnifiedAuditLogIngestionEnabled
```

Rekordy inspekcji dla tych zdarzeń zawierają informacje o tym, kiedy stan inspekcji został zmieniony, administrator, który go zmienił, oraz adres IP komputera, który został użyty do wprowadzenia zmiany. Na poniższych zrzutach ekranu przedstawiono rekordy inspekcji, które odpowiadają zmianie stanu inspekcji w organizacji.

### <a name="audit-record-for-turning-on-auditing"></a>Rekord inspekcji dotyczący włączania inspekcji

![Rekord inspekcji dotyczący włączania inspekcji](../media/AuditStatusAuditingEnabled.png)

Wartość `Confirm` właściwości *CmdletParameters* wskazuje, że ujednolicone rejestrowanie inspekcji zostało włączone w centrum zgodności lub poprzez uruchomienie polecenia cmdlet **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true.**

### <a name="audit-record-for-turning-off-auditing"></a>Rekord inspekcji umożliwiający wyłączenie inspekcji

![Rekord inspekcji umożliwiający wyłączenie inspekcji](../media/AuditStatusAuditingDisabled.png)

Wartość parametru `Confirm` nie jest uwzględniana we właściwości *CmdletParameters* . Oznacza to, że ujednolicone rejestrowanie inspekcji zostało wyłączone przez uruchomienie polecenia **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false** .

Aby uzyskać więcej informacji na temat przeszukiwania dziennika inspekcji Exchange administratora, zobacz [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog).
