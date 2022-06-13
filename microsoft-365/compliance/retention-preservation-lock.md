---
title: Używanie blokady zachowywania w celu ograniczenia zmian zasad przechowywania
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: Użyj blokady zachowania z zasadami przechowywania i zasadami etykiet przechowywania, aby pomóc w spełnieniu wymagań prawnych i ochronie przed nieautoryzowanymi administratorami.
ms.openlocfilehash: 228d4cd1a7778b5352df6d10d31b7e4c25af915f
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016289"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>Używanie blokady zachowania w celu ograniczenia zmian zasad przechowywania i zasad etykiet przechowywania

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!IMPORTANT]
> Obecnie [zakresy zasad adaptacyjnych](retention.md#adaptive-or-static-policy-scopes-for-retention) nie obsługują blokady zachowania.

Blokada zachowania blokuje zasady przechowywania lub zasady etykiet przechowywania, dzięki czemu nikt — w tym administrator globalny — nie może wyłączyć zasad, usunąć zasad ani uczynić ich mniej restrykcyjnym. Ta konfiguracja może być potrzebna do spełnienia wymagań prawnych i może pomóc w ochronie przed nieautoryzowanymi administratorami.

Gdy zasady przechowywania są zablokowane:

- Nikt nie może wyłączyć zasad ani je usunąć
- Lokalizacje można dodawać, ale nie usuwać
- Możesz przedłużyć okres przechowywania, ale nie zmniejszyć go

Gdy zasady etykiet przechowywania są zablokowane:

- Nikt nie może wyłączyć zasad ani je usunąć
- Lokalizacje można dodawać, ale nie usuwać
- Etykiety można dodawać, ale nie usuwać

Podsumowując, zablokowane zasady można zwiększyć lub rozszerzyć, ale nie można ich zmniejszyć ani wyłączyć.

> [!IMPORTANT]
> Przed zablokowaniem zasad przechowywania lub zasad etykiet przechowywania ważne jest zrozumienie wpływu i potwierdzenie, czy jest to wymagane w organizacji. Na przykład może być konieczne spełnienie wymagań prawnych. Administratorzy nie będą mogli wyłączać ani usuwać tych zasad po zastosowaniu blokady zachowania.

Skonfiguruj blokadę zachowania po utworzeniu [zasad przechowywania](create-retention-policies.md) lub publikowanych zasad etykiet [przechowywania i zawiera](create-apply-retention-labels.md) tylko etykiety [, które oznaczają elementy jako rekordy regulacyjne](records-management.md#records).

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>Jak zablokować zasady przechowywania lub zasady etykiet przechowywania

Jeśli musisz użyć blokady zachowania, musisz użyć programu PowerShell. Ponieważ administratorzy nie mogą wyłączyć ani usunąć zasad przechowywania po zastosowaniu tej blokady, włączenie tej funkcji nie jest dostępne w interfejsie użytkownika w celu ochrony przed przypadkową konfiguracją.

Wszystkie zasady przechowywania z dowolną konfiguracją obsługują blokadę zachowania. Aby zastosować blokadę zachowania dla zasad etykiet przechowywania, musi ona zawierać tylko etykiety, które oznaczają elementy jako rekordy regulacyjne.

1. [Połączenie do programu PowerShell zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell).

2. Znajdź nazwę zasad, które chcesz zablokować, uruchamiając polecenie [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy). Przykład:
    
   ![Lista zasad przechowywania w programie PowerShell.](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. Aby umieścić blokadę zachowania dla zasad, uruchom polecenie cmdlet [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) z nazwą zasad, a parametr *RestrictiveRetention* ma wartość true:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" -RestrictiveRetention $true
    ```
    
    Przykład:
    
    ![RestrictiveRetention parametr w programie PowerShell.](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     Po wyświetleniu monitu przeczytaj i potwierdź ograniczenia dotyczące tej konfiguracji, wprowadzając **wartość Y**:
    
   ![Monituj o potwierdzenie, że chcesz zablokować zasady przechowywania w programie PowerShell.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

Blokada zachowania jest teraz umieszczana w zasadach. Aby potwierdzić, uruchom `Get-RetentionCompliancePolicy` ponownie, ale określ nazwę zasad i wyświetl parametry zasad:

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

Powinna zostać **wyświetlona wartość RestrictiveRetention** ustawiona na **wartość True**. Przykład:

![Zablokowane zasady ze wszystkimi parametrami wyświetlanymi w programie PowerShell.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>Zobacz też

[Zasoby ułatwiające spełnienie wymagań prawnych dotyczących zarządzania cyklem życia danych i zarządzania rekordami](retention-regulatory-requirements.md)
