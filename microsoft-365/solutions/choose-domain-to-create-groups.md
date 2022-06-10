---
title: Wybieranie domeny do użycia podczas tworzenia grup Microsoft 365
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
description: Dowiedz się, jak wybrać domenę do użycia podczas tworzenia grup Microsoft 365, konfigurując zasady adresów e-mail przy użyciu programu PowerShell.
ms.openlocfilehash: c6eb1bbccf8745c88941f40d6fefeed29aec5620
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012543"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Wybieranie domeny do użycia podczas tworzenia grup Microsoft 365

Niektóre organizacje używają osobnych domen poczty e-mail w celu rozdzielenia różnych części swojej działalności. Możesz określić, która domena ma być używana podczas tworzenia grup Microsoft 365 przez użytkowników.
  
Jeśli Twoja organizacja potrzebuje użytkowników do tworzenia grup w domenach innych niż domyślna akceptowana domena firmy, możesz na to zezwolić, konfigurując zasady adresów e-mail (EAPs) przy użyciu programu PowerShell.

Przed uruchomieniem poleceń cmdlet programu PowerShell pobierz i zainstaluj moduł, który umożliwi ci rozmowę z organizacją. Zapoznaj się [z Połączenie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="example-scenarios"></a>Przykładowe scenariusze

Załóżmy, że główna domena Twojej firmy to Contoso.com. Jednak domyślna akceptowana domena organizacji to service.contoso.com. Oznacza to, że grupy zostaną utworzone w service.contoso.com (na przykład jimsteam@service.contoso.com).
  
Załóżmy, że masz również domeny podrzędne skonfigurowane w organizacji. Grupy mają być również tworzone w tych domenach:
  
- students.contoso.com dla studentów
    
- faculty.contoso.com dla wykładowców
    
W poniższych dwóch scenariuszach wyjaśniono, w jaki sposób można to osiągnąć.

> [!NOTE]
> Jeśli masz mulitple EAPs, są one oceniane w kolejności priorytetu. Wartość 1 oznacza najwyższy priorytet. Po dopasowaniu protokołu EAP nie jest oceniany żaden kolejny protokół EAP, a adresy, które są ostemplowane w grupie, są zgodne z dopasowanym protokółem EAP. > Jeśli żadne umowy EAPs nie spełniają określonych kryteriów, grupa zostanie aprowizowana w domyślnej akceptowanej domenie organizacji. Aby uzyskać szczegółowe informacje na temat dodawania akceptowanej domeny, zobacz [Zarządzanie zaakceptowanymi domenami w Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
  
### <a name="scenario-1"></a>Scenariusz 1

W poniższym przykładzie pokazano, jak aprowizować wszystkie grupy Microsoft 365 w organizacji w domenie groups.contoso.com.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Scenariusz 2

Załóżmy, że chcesz kontrolować, w których domenach podrzędnych są tworzone Microsoft 365 grupy. Chcesz:
  
- Grupy utworzone przez uczniów (użytkowników, dla których **dział** ma ustawioną pozycję **Studenci**) w domenie students.groups.contoso.com. Użyj tego polecenia:
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- Grupy utworzone przez członków wydziału (użytkownicy, **którzy mają dział** ustawiony na **Wydział lub adres e-mail zawiera faculty.contoso.com)**) w domenie faculty.groups.contoso.com. Użyj tego polecenia:
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Grupy utworzone przez inne osoby są tworzone w domenie groups.contoso.com. Użyj tego polecenia:
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>Zmienianie zasad adresów e-mail

Aby zmienić szablony priorytetów lub adresów e-mail dla istniejącego protokołu EAP, użyj polecenia cmdlet Set-EmailAddressPolicy.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

Zmiana protokołu EAP nie ma wpływu na grupy, które zostały już aprowizowane.
  
## <a name="delete-email-address-policies"></a>Usuwanie zasad adresów e-mail

Aby usunąć protokół EAP, użyj polecenia cmdlet Remove-EmailAddressPolicy.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

Zmiana protokołu EAP nie ma wpływu na grupy, które zostały już aprowizowane.
  
## <a name="hybrid-requirements"></a>Wymagania hybrydowe

Jeśli Twoja organizacja jest skonfigurowana w scenariuszu hybrydowym, zapoznaj się [z tematem Konfigurowanie grup Microsoft 365 przy użyciu lokalnego Exchange hybrydowego](/exchange/hybrid-deployment/set-up-microsoft-365-groups), aby upewnić się, że twoja organizacja spełnia wymagania dotyczące tworzenia grup Microsoft 365. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>Dodatkowe informacje na temat korzystania z grup zasad adresów e-mail:

Jest jeszcze kilka rzeczy do poznania:
  
- Szybkość tworzenia grup zależy od liczby adresów EAP skonfigurowanych w organizacji.
    
- Administratorzy i użytkownicy mogą również modyfikować domeny podczas tworzenia grup.
    
- Grupa użytkowników jest określana przy użyciu standardowych zapytań (właściwości użytkownika), które są już dostępne. Zapoznaj się z [właściwościami filtrowalnymi dla parametru -RecipientFilter](/powershell/exchange/recipientfilter-properties) , aby uzyskać obsługiwane właściwości z możliwością filtrowania. 
    
- Jeśli nie skonfigurujesz żadnych umów EAPs dla grup, domyślna zaakceptowana domena zostanie wybrana do utworzenia grupy.
    
- Jeśli usuniesz zaakceptowaną domenę, najpierw zaktualizuj umowy EAPs, w przeciwnym razie będzie to miało wpływ na aprowizację grup.
    
- Dla organizacji można skonfigurować maksymalny limit 100 zasad adresów e-mail.
    
## <a name="related-content"></a>Zawartość pokrewna

[Zalecenia dotyczące planowania ładu współpracy](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (artykuł)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md) (artykuł)

[Tworzenie grupy Microsoft 365 w centrum administracyjnym](../admin/create-groups/create-groups.md) (artykuł)