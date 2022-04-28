---
title: Konfigurowanie synchronizacji katalogów dla Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Dowiedz się, jak skonfigurować synchronizację katalogów między Microsoft 365 a lokalna usługa Active Directory.
ms.openlocfilehash: 49240d056520a83c0828440e21c5cf26943bae8e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092894"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Konfigurowanie synchronizacji katalogów dla Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 używa dzierżawy Azure Active Directory (Azure AD) do przechowywania tożsamości i zarządzania nimi w celu uwierzytelniania i uprawnień dostępu do zasobów opartych na chmurze. 

Jeśli masz domenę lub las usług lokalna usługa Active Directory Domain Services (AD DS), możesz zsynchronizować konta użytkowników, grupy i kontakty usług AD Z dzierżawą usługi Azure AD subskrypcji Microsoft 365. Jest to tożsamość hybrydowa dla Microsoft 365. Oto jego składniki.

![Składniki synchronizacji katalogów dla Microsoft 365.](../media/about-microsoft-365-identity/hybrid-identity.png)

Usługa Azure AD Połączenie działa na serwerze lokalnym i synchronizuje usługi AD DS z dzierżawą usługi Azure AD. Oprócz synchronizacji katalogów można również określić następujące opcje uwierzytelniania:

- Synchronizacja skrótów haseł (PHS)

  Usługa Azure AD wykonuje samo uwierzytelnianie.

- Uwierzytelnianie przekazywane (PTA)

  Usługa Azure AD ma usług AD DS wykonać uwierzytelnianie.

- Uwierzytelnianie federacyjne

  Usługa Azure AD odwołuje się do komputera klienckiego żądającego uwierzytelniania do innego dostawcy tożsamości.

Aby uzyskać więcej informacji [, zobacz Tożsamości hybrydowe](plan-for-directory-synchronization.md) .
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Przejrzyj wymagania wstępne dotyczące usługi Azure AD Połączenie

Otrzymasz bezpłatną subskrypcję usługi Azure AD z subskrypcją Microsoft 365. Podczas konfigurowania synchronizacji katalogów zainstalujesz usługę Azure AD Połączenie na jednym z serwerów lokalnych.
  
W przypadku Microsoft 365 należy wykonać następujące czynności:
  
- Zweryfikuj domenę lokalną. Kreator Połączenie usługi Azure AD przeprowadzi Cię przez ten proces.
- Uzyskaj nazwy użytkowników i hasła dla kont administratorów dzierżawy Microsoft 365 i usług AD DS.

W przypadku serwera lokalnego, na którym instalujesz usługę Azure AD Połączenie, potrzebne są następujące elementy:
  
|**System operacyjny serwera**|**Inne oprogramowanie**|
|:-----|:-----|
|Windows Server 2012 R2 i nowsze | — Program PowerShell jest instalowany domyślnie, nie jest wymagana żadna akcja.  <br> — Wersje net 4.5.1 i nowsze są oferowane za pośrednictwem Windows Update. Upewnij się, że zainstalowano najnowsze aktualizacje programu Windows Server w Panel sterowania. |
|Windows Server 2008 R2 z dodatkiem Service Pack 1 (SP1)** lub Windows Server 2012 | — Najnowsza wersja programu PowerShell jest dostępna w wersji Windows Management Framework 4.0. Wyszukaj go w [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> — Wersje .Net 4.5.1 i nowsze są dostępne w [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | — Najnowsza obsługiwana wersja programu PowerShell jest dostępna w Windows Management Framework 3.0, dostępna w [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> — Wersje .Net 4.5.1 i nowsze są dostępne w [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Zobacz [Wymagania wstępne dotyczące Azure Active Directory Połączenie](/azure/active-directory/hybrid/how-to-connect-install-prerequisites), aby uzyskać szczegółowe informacje o wymaganiach dotyczących sprzętu, oprogramowania, konta i uprawnień, wymagań dotyczących certyfikatów SSL i limitów obiektów dla usługi Azure AD Połączenie.
  
Możesz również przejrzeć [historię wersji](/azure/active-directory/hybrid/reference-connect-version-history) usługi Azure AD Połączenie, aby zobaczyć, co jest uwzględnione i naprawione w każdej wersji.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Instalowanie usługi Azure AD Połączenie i konfigurowanie synchronizacji katalogów

Przed rozpoczęciem upewnij się, że masz następujące elementy:

- Nazwa użytkownika i hasło administratora globalnego Microsoft 365
- Nazwa użytkownika i hasło administratora domeny usług AD DS
- Która metoda uwierzytelniania (PHS, PTA, federacyjna)
- Czy chcesz używać [bezproblemowego logowania jednokrotnego w usłudze Azure AD](/azure/active-directory/hybrid/how-to-connect-sso)

Wykonaj następujące czynności:

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) i wybierz pozycję **Użytkownicy** \> **aktywni użytkownicy** na lewym pasku nawigacyjnym.
2. Na stronie **Aktywni użytkownicy** wybierz pozycję **Więcej** (trzy kropki) \> **Synchronizacja katalogu**.
  
3. Na stronie **przygotowywania Azure Active Directory** wybierz pozycję **Przejdź do centrum pobierania, aby uzyskać link do narzędzia Połączenie usługi Azure AD**, aby rozpocząć pracę. 
4. Wykonaj kroki opisane w temacie [Azure AD Połączenie and Azure AD Połączenie Health installation roadmap (Plan instalacji usługi Azure AD Połączenie Health](/azure/active-directory/hybrid/how-to-connect-install-roadmap)).

## <a name="3-finish-setting-up-domains"></a>3. Zakończ konfigurowanie domen

Wykonaj kroki opisane w [temacie Tworzenie rekordów DNS dla Microsoft 365 podczas zarządzania rekordami DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), aby zakończyć konfigurowanie domen.

## <a name="next-step"></a>Następny krok

[Przypisywanie licencji do kont użytkowników](assign-licenses-to-user-accounts.md)