---
title: Rozwiązywanie problemów z synchronizacją katalogów na Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: W tym artykule opisano typowe przyczyny problemów z synchronizacją katalogów w programie Office 365 oraz przedstawiono kilka metod pomocnych w rozwiązywaniu problemów i ich rozwiązywaniu.
ms.openlocfilehash: dba6626ead648928186f8fbeac646a2b52206bc0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988372"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Rozwiązywanie problemów z synchronizacją katalogów na Microsoft 365

Dzięki synchronizacji katalogów możesz zarządzać użytkownikami i grupami lokalnie, a także synchronizować zmiany (w tym dodawanie i usuwanie) oraz zmiany w chmurze. Jednak konfiguracja jest nieco skomplikowana i zidentyfikowanie źródła problemów może być czasami trudne. Mamy zasoby, które ułatwiają identyfikowanie potencjalnych problemów i ich rozwiązywanie.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Skąd wiadomo, że coś jest nie tak?

Pierwszym sygnałem, że coś jest nie tak, jest wskazanie problemu na kafelku stanu synchronizacji katalogów w centrum administracyjne platformy Microsoft 365, że występuje problem.
  
Otrzymasz również wiadomość (na alternatywny adres e-mail i adres e-mail administratora) od użytkownika Microsoft 365 z powiadomieniem, że w dzierżawie wystąpiły błędy synchronizacji katalogów. Aby uzyskać szczegółowe informacje[, zobacz Błędy synchronizacji katalogów tożsamości w programie Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Jak uzyskać narzędzie Azure Active Directory Połączenie?

W [centrum administracyjne platformy Microsoft 365 przejdź](https://admin.microsoft.com) do tematu **Aktywni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**użytkownicy**</a> użytkownicy. Kliknij menu **Więcej** (trzy kropki) i wybierz pozycję **Synchronizacja katalogów**. 
  
Postępuj zgodnie [z instrukcjami kreatora,](set-up-directory-synchronization.md) aby pobrać usługę Azure AD Połączenie. 
  
Jeśli nadal używasz narzędzia Azure Active Directory (Azure AD) Sync (DirSync), zobacz Jak rozwiązywać problemy z instalacją narzędzia do synchronizacji Azure Active Directory i komunikatami o błędach Kreatora [konfiguracji w programie Microsoft 365](/troubleshoot/azure/active-directory/installation-configuration-wizard-errors)  aby uzyskać informacje na temat wymagań systemowych dotyczących instalacji narzędzia dirsync, wymaganych uprawnień i sposobu rozwiązywania typowych błędów. 
  
Aby zaktualizować usługę Azure AD Sync do usługi Azure AD Połączenie, zobacz [instrukcje uaktualniania](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Rozwiązywanie typowych przyczyn problemów z synchronizacją katalogów w programie Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>Obiekty zsynchronizowane nie są wyświetlane lub aktualizowane w trybie online albo z usługi są wyświetlane raporty o błędach synchronizacji.

- [Synchronizacja tożsamości i zapobieganie duplikowaniu atrybutów](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>W centrum administracyjnym pojawia się alert lub otrzymuję automatyczne wiadomości e-mail z informacjami, że ostatnio nie było zdarzenia synchronizacji
- [Rozwiązywanie problemów z łącznością w narzędziu Azure AD Connect](/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect — konta i uprawnienia ](/azure/active-directory/hybrid/reference-connect-accounts-permissions)
- [Synchronizacja w narzędziu Azure AD Connect: jak zarządzać kontem usługi Azure AD](/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Synchronizacja katalogów z usługą Azure Active Directory zatrzymuje się lub jest wyświetlane ostrzeżenie, że synchronizacja nie zarejestrowała się przez więcej niż jeden dzień ](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>Skróty haseł nie są synchronizowane lub w centrum administracyjnym pojawia się alert o niedawnej synchronizacji skrótów haseł
- [Implementowanie synchronizacji skrótów haseł za pomocą synchronizacji w narzędziu Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>Widzę alert z przekroczeniem przydziału obiektu
- Wbudowany przydział obiektu pomaga chronić usługę. Jeśli masz za dużo obiektów w katalogu, które trzeba zsynchronizować z usługą Microsoft 365, musisz skontaktować się z pomocą techniczną dla [](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) produktów biznesowych, aby zwiększyć przydział.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>Chcę wiedzieć, które atrybuty są synchronizowane
- Tutaj możesz znaleźć listę wszystkich atrybutów synchronizowanych między środowiskiem lokalnym a [chmurą](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>Nie mogę zarządzać obiektami, które zostały zsynchronizowane z chmurą, ani ich usuwać
- Czy chcesz zarządzać obiektami tylko w chmurze? Czy może istnieje obiekt, który został usunięty lokalnie, ale nadal znajduje się w chmurze? Aby uzyskać wskazówki dotyczące rozwiązywania [tych problemów,](/azure/active-directory/hybrid/tshoot-connect-sync-errors) zobacz ten [](/troubleshoot/azure/active-directory/cannot-manage-objects) artykuł rozwiązywanie problemów podczas synchronizacji i artykuł pomocy technicznej.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>Został wyświetlony komunikat o błędzie informujący, że moja firma przekroczyła liczbę obiektów, które można synchronizować
- Więcej o tym problemie możesz przeczytać [tutaj](/troubleshoot/azure/active-directory/exceed-number-objects-synced).
   
## <a name="other-resources"></a>Inne zasoby

- [Skrypt umożliwiający naprawienie zduplikowanych głównych nazw użytkowników (UPN)](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Jak przygotować domenę nie routowaną (taką jak domena .local) do synchronizacji katalogów](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Skrypt do zliczania wszystkich zsynchronizowanych obiektów](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Rozwiązywanie problemów z usługami AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Rozwiązywanie problemów z pustymi atrybutami DisplayName dla grup z obsługą poczty przy użyciu programu PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Rozwiązywanie problemów ze zduplikowanymi sieciami UPN za pomocą programu PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Rozwiązywanie problemów ze zduplikowanymi adresami e-mail za pomocą programu PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396731)
