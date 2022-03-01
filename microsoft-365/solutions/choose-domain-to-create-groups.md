---
title: Wybieranie domeny do użycia podczas tworzenia Microsoft 365 grup
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 7cf5655d-e523-4bc3-a93b-3ccebf44a01a
recommendations: false
description: Dowiedz się, jak wybrać domenę do użycia podczas tworzenia grup Microsoft 365, konfigurując zasady adresów e-mail za pomocą programu PowerShell.
ms.openlocfilehash: 31b84304643190f343ae9ee74a947ecf6741f135
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63004957"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Wybieranie domeny do użycia podczas tworzenia Microsoft 365 grup

Niektóre organizacje używają osobnych domen poczty e-mail w celu rozdzielenia różnych części swojej działalności. Możesz określić, która domena ma być używana, gdy użytkownicy tworzą Microsoft 365 grupy.
  
Jeśli użytkownicy w Twojej organizacji muszą tworzyć swoje grupy w domenach innych niż domyślna zaakceptowana domena Twojej firmy, możesz na to zezwolić, konfigurując zasady adresów e-mail (EPS) przy użyciu programu PowerShell.

Zanim będzie można uruchomić polecenia cmdlet programu PowerShell, pobierz i zainstaluj moduł, który pozwoli ci rozmawiać z Twoją organizacją. Zapoznaj się [Połączenie, aby Exchange Online przy użyciu zdalnej pracy z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="example-scenarios"></a>Przykładowe scenariusze

Załóżmy, że główna domena Twojej firmy to Contoso.com. Domyślna zaakceptowana domena organizacji jest jednak service.contoso.com. Oznacza to, że grupy będą tworzone w programie service.contoso.com (na przykład jimsteam@service.contoso.com).
  
Załóżmy, że w organizacji skonfigurowano również poddomeny. Chcesz również tworzyć grupy w tych domenach:
  
- students.contoso.com dla uczniów
    
- faculty.contoso.com dla wykładowców
    
W poniższych dwóch scenariuszach wyjaśniono, jak można to zrobić.

> [!NOTE]
> W przypadku wielu POP są one obliczane w kolejności priorytetu. Wartość 1 oznacza najwyższy priorytet. Po dopasowań JNW nie jest sprawdzana żadna dodatkowa wartość JAP, a adresy, które są oznaczane w grupie, są zgodne z dopasowaną wartością EAP. >, jeśli żaden z e-maili nie spełnia określonych kryteriów, to grupa będzie zapewniana w domyślnej zaakceptowaowej domenie organizacji. Aby uzyskać [szczegółowe informacje na temat](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dodawania zaakceptowanych Exchange Online, zobacz Zarządzanie zaakceptowanymi domenami w polsce.
  
### <a name="scenario-1"></a>Scenariusz 1

W poniższym przykładzie pokazano, jak aprowizować wszystkie Microsoft 365 grup w organizacji w domenie groups.contoso.com domeny.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Scenariusz 2

Załóżmy, że chcesz kontrolować, w jakich poddomenach Microsoft 365 są tworzone grupy. Chcesz:
  
- Grupy utworzone przez uczniów (użytkowników, dla **których dla ustawienia Dział** **na wartość** Uczniowie) w students.groups.contoso.com domenie. Użyj tego polecenia:
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- Grupy utworzone przez nauczycieli lub wykładowców (użytkownicy z ustawieniami działów o adresie wykładowcy lub adresie **e-mail faculty.contoso.com)**) w domenie faculty.groups.contoso.com nauczycieli. Użyj tego polecenia:
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Grupy utworzone przez inne osoby są tworzone w groups.contoso.com domeny. Użyj tego polecenia:
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>Zmienianie zasad adresu e-mail

Aby zmienić priorytet lub szablony adresów e-mail dla istniejącego EAP, użyj Set-EmailAddressPolicy cmdlet.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

Zmiana JNW nie ma wpływu na grupy, które już zostały inicjowanie obsługi administracyjnej.
  
## <a name="delete-email-address-policies"></a>Usuwanie zasad adresu e-mail

Aby usunąć program EAP, użyj Remove-EmailAddressPolicy cmdlet.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

Zmiana JNW nie ma wpływu na grupy, które już zostały inicjowanie obsługi administracyjnej.
  
## <a name="hybrid-requirements"></a>Wymagania dotyczące środowiska hybrydowego

Jeśli Twoja organizacja jest skonfigurowana w scenariuszu hybrydowym, zobacz Konfigurowanie grup usługi Microsoft 365 przy użyciu lokalnego środowiska hybrydowego usługi [Exchange](/exchange/hybrid-deployment/set-up-microsoft-365-groups), aby upewnić się, że Twoja organizacja spełnia wymagania dotyczące tworzenia grup Microsoft 365 grupy. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>Dodatkowe informacje na temat korzystania z grup zasad dotyczących adresów e-mail:

Należy wiedzieć jeszcze kilka rzeczy:
  
- Szybkość tworzenia grup zależy od liczby EAPS skonfigurowanych w organizacji.
    
- Administratorzy i użytkownicy mogą też modyfikować domeny podczas tworzenia grup.
    
- Grupa użytkowników jest określana przy użyciu już dostępnych zapytań standardowych (właściwości użytkownika). Zobacz Właściwości [z filtrowaniem dla parametru -RecipientFilter,](/powershell/exchange/recipientfilter-properties) aby uzyskać obsługiwane właściwości z filtrowaniem. 
    
- Jeśli nie skonfigurujesz żadnych EAPS dla grup, do tworzenia grup zostanie wybrana domyślna zaakceptowana domena.
    
- Jeśli usuniesz zaakceptowaną domenę, należy najpierw zaktualizować eaPs, w przeciwnym razie będzie to miało wpływ na inicjowanie obsługi grup.
    
- W organizacji można skonfigurować maksymalnie 100 zasad adresu e-mail.
    
## <a name="related-content"></a>Zawartość pokrewna

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (artykuł)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md) (artykuł)

[Tworzenie grupy Microsoft 365 w centrum administracyjnym](../admin/create-groups/create-groups.md) (artykuł)