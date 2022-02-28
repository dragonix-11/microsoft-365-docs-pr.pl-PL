---
title: Używanie blokady zachowywania w celu ograniczenia zmian zasad przechowywania i zasad etykiet przechowywania
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
description: Blokady zachowywania można używać z zasadami przechowywania i zasadami etykiet przechowywania, aby ułatwić spełnienie wymagań prawnych i zabezpieczenie przed fałszywymi administratorami.
ms.openlocfilehash: 64c2bb8f2718ce0da9d638b5b8b6bd4f89d33668
ms.sourcegitcommit: f6fff04431d632db02e7bdbf12f691091a30efad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2021
ms.locfileid: "62988669"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>Używanie blokady zachowywania w celu ograniczenia zmian zasad przechowywania i zasad etykiet przechowywania

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!IMPORTANT]
> Obecnie [adaptacyjne zakresy zasad](retention.md#adaptive-or-static-policy-scopes-for-retention) nie obsługują blokady zachowywania.

Blokowanie zachowywania blokuje zasady przechowywania lub zasady etykiet przechowywania, aby nikt — w tym administrator globalny — nie może wyłączyć tych zasad, usunąć je lub sprawić, że będą mniej restrykcyjne. Taka konfiguracja może być potrzebna na potrzeby wymogów prawnych i może ułatwić zabezpieczenie przed administratorami zbędnych.

Gdy zasady przechowywania są zablokowane:

- Nikt nie może wyłączyć zasad ani je usunąć
- Lokalizacje można dodawać, ale nie można ich usuwać
- Możesz wydłużyć okres przechowywania, ale nie zmniejszać go

Gdy zasady etykiet przechowywania są zablokowane:

- Nikt nie może wyłączyć zasad ani je usunąć
- Lokalizacje można dodawać, ale nie można ich usuwać
- Etykiety można dodawać, ale nie można ich usuwać

Podsumowując, zablokowane zasady można zwiększyć lub wydłużyć, ale nie można ich zmniejszyć ani wyłączyć.

> [!IMPORTANT]
> Przed zablokowaniem zasad przechowywania lub zasad etykiet przechowywania należy zrozumieć skutki i potwierdzić, czy są wymagane dla Twojej organizacji. Może być na przykład konieczne spełnienie wymagań prawnych. Administratorzy nie będą mogli wyłączyć ani usunąć tych zasad po zastosowaniu blokady zachowywania.

Skonfiguruj blokadę zachowywania po utworzeniu zasad [](create-retention-policies.md)przechowywania lub zasad etykiet przechowywania publikowanych [lub](create-apply-retention-labels.md) [automatycznie stosowania](apply-retention-labels-automatically.md).

> [!NOTE]
> Zablokowanie zasad etykiet nie uniemożliwia administratorowi skrócenia okresu przechowywania na etykiecie zawartej w zablokowanych zasadach. To wymaganie, z innymi ograniczeniami, może być spełnione podczas konfigurowania etykiety w celu oznaczania elementów jako [rekordów prawnych](records-management.md#records).

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>Jak zablokować zasady przechowywania lub zasady etykiet przechowywania

Aby użyć blokady zachowania, należy użyć programu PowerShell. Administratorzy nie mogą wyłączać ani usuwać zasad przechowywania po zastosowaniu tej blokady, dlatego włączenie tej funkcji nie jest dostępne w interfejsie użytkownika w celu zabezpieczenia się przed przypadkową konfiguracją.

Wszystkie zasady przechowywania i z dowolną konfiguracją obsługują blokadę zachowywania.

1. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

2. Znajdź nazwę zasad, które chcesz zablokować, uruchamiając program [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy). Przykład:
    
   ![Lista zasad przechowywania w programie PowerShell.](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. Aby umieścić blokadę na zachowywaniu zasad, uruchom polecenie cmdlet [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) z nazwą zasad i *parametrem RestrictiveRetention* ustawionym na wartość True:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" –RestrictiveRetention $true
    ```
    
    Przykład:
    
    ![Parametr RestrictiveRetention w programie PowerShell.](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     Po wyświetleniu monitu przeczytaj ograniczenia związane z tą konfiguracją i potwierdzaj je, wprowadzając **Y**:
    
   ![Monit o potwierdzenie, że chcesz zablokować zasady przechowywania w programie PowerShell.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

Blokada zachowania zostanie umieszczona w zasadach. Aby potwierdzić, uruchom `Get-RetentionCompliancePolicy` ponownie, ale określ nazwę zasad i wyświetl parametry zasad:

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

Powinien zostać wyświetlony **temat RestrictiveRetention** ma ustawioną wartość **True (Prawda**). Przykład:

![Zasady blokowania ze wszystkimi parametrami wyświetlanymi w programie PowerShell.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>Zobacz też

[Zasoby pomocne w spełniania wymagań prawnych dotyczących zarządzania informacjami i zarządzania rekordami](retention-regulatory-requirements.md)