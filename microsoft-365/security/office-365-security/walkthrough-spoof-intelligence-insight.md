---
title: Zarządzanie fałszywymi nadawcami przy użyciu zasad analizy fałszowania i fałszowania szczegółowych informacji wywiadowczych
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak używać zasad analizy fałszowania i analizy fałszowania, aby zezwalać na wykryte sfałszowane nadawcy lub blokować ich blokowanie.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: f827046dc9a103e73eb6fb79ba161e523e2b2690
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649358"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>Zarządzanie sfałszowanymi nadawcami przy użyciu zasad analizy fałszowania i fałszowania analizy w ramach EOP

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Sfałszowane zarządzanie nadawcą w portalu Microsoft 365 Defender jest teraz dostępne tylko na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżaw. Aby zapoznać się z bieżącymi procedurami w portalu Microsoft 365 Defender, zobacz [Spoof intelligence insight in EOP (Fałszowanie analizy w ramach EOP](learn-about-spoof-intelligence.md)).
>
> Sfałszowane zarządzanie nadawcą w programie Exchange Online programie PowerShell lub autonomicznym programie PowerShell EOP jest w trakcie migracji wyłącznie do powiązanych **\*poleceń cmdlet -TenantAllowBlockListSpoofItems**, **Get-SpoofIntelligenceInsight** i **Get-SpoofMailReport**. Procedury korzystające z tych poleceń cmdlet można znaleźć w następujących artykułach:
>
> - [Wyświetlanie fałszywych wpisów nadawcy przy użyciu programu PowerShell](tenant-allow-block-list.md#view-spoofed-sender-entries)
> - [Dodawanie fałszywych wpisów zezwalania nadawcy przy użyciu programu PowerShell](manage-tenant-allows.md#add-spoofed-sender-allow-entries-using-powershell)
> - [Dodawanie fałszywych wpisów bloku nadawcy przy użyciu programu PowerShell](manage-tenant-blocks.md#add-spoofed-sender-block-entries)
> - [Modyfikowanie fałszywych wpisów nadawcy przy użyciu programu PowerShell](modify-remove-entries-tenant-allow-block.md#modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
> - [Usuwanie fałszywych wpisów nadawcy przy użyciu programu PowerShell](modify-remove-entries-tenant-allow-block.md#remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
>
> Starsze sfałszowane środowisko zarządzania nadawcą przy użyciu poleceń cmdlet **Get-PhishFilterPolicy** i **Set-PhishFilterPolicy** jest w trakcie wycofywania, ale nadal jest prezentowane w tym artykule w celu uzyskania kompletności, dopóki polecenia cmdlet nie zostaną usunięte wszędzie.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby zmodyfikować zasady analizy fałszowania lub włączyć lub wyłączyć analizę fałszowania, musisz być członkiem następujących elementów:
    - **Zarządzanie organizacją**
    - **Administrator zabezpieczeń** <u>i</u> **konfiguracja tylko do wyświetlania** lub **zarządzanie organizacją tylko do wyświetlania**.
  - Aby uzyskać dostęp tylko do odczytu do zasad analizy fałszowania, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Opcje analizy fałszowania zostały opisane w temacie [Spoof settings in anti-phishing policies (Ustawienia fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings)).

- Ustawienia analizy fałszowania można włączać, wyłączać i konfigurować w zasadach ochrony przed wyłudzaniem informacji. Aby uzyskać instrukcje oparte na subskrypcji, zobacz jeden z następujących tematów:

  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP](configure-anti-phishing-policies-eop.md).
  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md).

- Aby zapoznać się z naszymi zalecanymi ustawieniami analizy podróbek, zobacz [Ustawienia zasad ochrony przed wyłudzaniem informacji](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) w usłudze EOP.

## <a name="use-powershell-to-manage-spoofed-senders"></a>Zarządzanie fałszowaniem nadawców przy użyciu programu PowerShell

Aby wyświetlić dozwolonych i zablokowanych nadawców w analizie fałszowania, użyj następującej składni:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Ten przykład zwraca szczegółowe informacje o wszystkich nadawcach, którzy mogą podszywać się pod użytkowników w domenach.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Aby skonfigurować dozwolonych i zablokowanych nadawców w analizie fałszowania, wykonaj następujące kroki:

1. Przechwyć bieżącą listę wykrytych sfałszowanych nadawców, zapisując dane wyjściowe polecenia cmdlet **Get-PhishFilterPolicy** w pliku CSV, uruchamiając następujące polecenie:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Edytuj plik CSV, aby dodać lub zmodyfikować następujące wartości:
   - **Nadawca** (domena w rekordzie PTR serwera źródłowego lub adres IP/24)
   - **SpoofedUser**: jedna z następujących wartości:
     - Wewnętrzny adres e-mail użytkownika.
     - Domena poczty e-mail użytkownika zewnętrznego.
     - Pusta wartość wskazująca, że chcesz zablokować lub zezwolić na wszystkie sfałszowane wiadomości od określonego **nadawcy**, niezależnie od sfałszowanego adresu e-mail.
   - **AllowedToSpoof** (Tak lub Nie)
   - **SpoofType** (wewnętrzny lub zewnętrzny)

   Zapisz plik, odczytaj plik i zapisz zawartość jako zmienną o nazwie `$UpdateSpoofedSenders` , uruchamiając następujące polecenie:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Użyj zmiennej `$UpdateSpoofedSenders` , aby skonfigurować zasady analizy fałszowania, uruchamiając następujące polecenie:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

Aby sprawdzić, czy skonfigurowano analizę fałszowania z nadawcami, którzy są dozwoloni i nie mogą podszywać się, uruchom następujące polecenia w programie PowerShell, aby wyświetlić nadawców, którzy są dozwoloni i nie mogą podszywać się:

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- W programie PowerShell uruchom następujące polecenie, aby wyeksportować listę wszystkich sfałszowanych nadawców do pliku CSV:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
