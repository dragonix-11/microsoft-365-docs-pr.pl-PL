---
title: Rozwiązywanie problemów z synchronizacją katalogów dla Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Opisuje typowe przyczyny problemów z synchronizacją katalogów w Office 365 i udostępnia kilka metod ułatwiających ich rozwiązywanie.
ms.openlocfilehash: 248ccc888f047a57f474dfc55b501f4450cb116e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101012"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Rozwiązywanie problemów z synchronizacją katalogów dla Microsoft 365

Dzięki synchronizacji katalogów można nadal zarządzać użytkownikami i grupami lokalnie oraz synchronizować dodatki, usunięcia i zmiany w chmurze. Jednak konfiguracja jest nieco skomplikowana i czasami może być trudno zidentyfikować źródło problemów. Dysponujemy zasobami, które pomogą Ci zidentyfikować potencjalne problemy i je rozwiązać.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Jak mogę wiedzieć, czy coś jest nie tak?

Pierwszym wskazaniem, że coś jest nie tak, jest to, że kafelek Stan DirSync w Centrum administracyjne platformy Microsoft 365 wskazuje, że wystąpił problem.
  
Otrzymasz również wiadomość e-mail (na alternatywną wiadomość e-mail i na adres e-mail administratora) z Microsoft 365 wskazującą, że dzierżawa napotkała błędy synchronizacji katalogów. Aby uzyskać szczegółowe informacje, zobacz [Identyfikowanie błędów synchronizacji katalogów w Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Jak mogę uzyskać narzędzie Azure Active Directory Połączenie?

W [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przejdź do pozycji **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**aktywni użytkownicy**</a>. Kliknij menu **Więcej** (trzy kropki) i wybierz pozycję **Synchronizacja katalogów**. 
  
Postępuj zgodnie z [instrukcjami w kreatorze,](set-up-directory-synchronization.md) aby pobrać Połączenie usługi Azure AD. 
  
Jeśli nadal używasz synchronizacji Azure Active Directory (Azure AD) (DirSync), zapoznaj się z artykułem [Jak rozwiązywać problemy z instalacją narzędzia synchronizacji Azure Active Directory i komunikatami o błędach Kreatora konfiguracji w Microsoft 365](/troubleshoot/azure/active-directory/installation-configuration-wizard-errors)  aby uzyskać informacje o wymaganiach systemowych dotyczących instalowania dirsync, potrzebnych uprawnień i sposobu rozwiązywania typowych błędów. 
  
Aby zaktualizować Azure AD Sync do usługi Azure AD Połączenie, zobacz [instrukcje uaktualniania](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Rozwiązywanie typowych przyczyn problemów z synchronizacją katalogów w Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>Zsynchronizowane obiekty nie są wyświetlane ani aktualizowane w trybie online lub ochodzę raporty o błędach synchronizacji z usługi.

- [Synchronizacja tożsamości i zapobieganie duplikowaniu atrybutów](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>Mam alert w centrum administracyjnym lub otrzymuję automatyczne wiadomości e-mail z informacją, że nie było ostatnio zdarzenia synchronizacji
- [Rozwiązywanie problemów z łącznością w narzędziu Azure AD Connect](/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect — konta i uprawnienia ](/azure/active-directory/hybrid/reference-connect-accounts-permissions)
- [Synchronizacja w narzędziu Azure AD Connect: jak zarządzać kontem usługi Azure AD](/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Synchronizacja katalogów z usługą Azure Active Directory zatrzymuje się lub jest wyświetlane ostrzeżenie, że synchronizacja nie zarejestrowała się przez więcej niż jeden dzień ](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>Skróty haseł nie są synchronizowane lub w centrum administracyjnym jest wyświetlany alert informujący, że ostatnio nie było synchronizacji skrótów haseł
- [Implementowanie synchronizacji skrótów haseł za pomocą synchronizacji w narzędziu Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>Widzę alert informujący o przekroczeniu limitu przydziału obiektu
- Mamy wbudowany limit przydziału obiektów, który pomaga chronić usługę. Jeśli w katalogu jest zbyt wiele obiektów, które muszą zostać zsynchronizowane z Microsoft 365, musisz [skontaktować się z pomocą techniczną dla produktów biznesowych](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b), aby zwiększyć limit przydziału.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>Muszę wiedzieć, które atrybuty są synchronizowane
- Listę wszystkich atrybutów synchronizowanych między środowiskiem lokalnym a chmurą można znaleźć [tutaj](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>Nie mogę zarządzać obiektami synchronizowanymi z chmurą ani usuwać ich
- Czy wszystko jest gotowe do zarządzania obiektami tylko w chmurze? A może istnieje obiekt, który został usunięty lokalnie, ale jest zablokowany w chmurze? Zapoznaj się z tym artykułem [Rozwiązywanie problemów z błędami podczas synchronizacji](/azure/active-directory/hybrid/tshoot-connect-sync-errors) i [pomocy technicznej](/troubleshoot/azure/active-directory/cannot-manage-objects) , aby uzyskać wskazówki dotyczące rozwiązywania tych problemów.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>Został wyświetlony komunikat o błędzie informujący o przekroczeniu liczby obiektów, które można zsynchronizować
- Więcej informacji na temat tego problemu można znaleźć [tutaj](/troubleshoot/azure/active-directory/exceed-number-objects-synced).
   
## <a name="other-resources"></a>Inne zasoby

- [Skrypt umożliwiający naprawienie zduplikowanych głównych nazw użytkowników (UPN)](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Jak przygotować domenę bez routingu (taką jak domena lokalna) do synchronizacji katalogów](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Skrypt do zliczania łącznej liczby zsynchronizowanych obiektów](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Rozwiązywanie problemów z usługami AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Naprawianie pustych atrybutów DisplayName dla grup obsługujących pocztę przy użyciu programu PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Naprawianie zduplikowanej nazwy UPN przy użyciu programu PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Naprawianie zduplikowanych adresów e-mail przy użyciu programu PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396731)
