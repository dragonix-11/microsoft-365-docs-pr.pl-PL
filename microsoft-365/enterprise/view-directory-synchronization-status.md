---
title: Wyświetl stan synchronizacji katalogów w Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: W tym artykule dowiesz się, jak sprawdzić stan synchronizacji katalogów w Office 365.
ms.openlocfilehash: 8f21985f8db3539e8dd1a839cc6cb499a425feeb
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095559"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Wyświetl stan synchronizacji katalogów w Microsoft 365

Jeśli zintegrowano usługi lokalna usługa Active Directory Domain Services (AD DS) z usługą Azure Active Directory (Azure AD), synchronizując środowisko lokalne z Microsoft 365, możesz również sprawdzić stan synchronizacji.
  
## <a name="view-directory-synchronization-status"></a>Wyświetlanie stanu synchronizacji katalogów

- Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) i wybierz pozycję **Stan narzędzia DirSync** na stronie głównej.
- Alternatywnie możesz przejść do pozycji **Użytkownicy** \> **aktywni użytkownicy**, a następnie na stronie **Użytkownicy aktywni** wybierz pozycję **Więcej** \> **synchronizacji katalogów**. W okienku **Synchronizacja katalogów** wybierz pozycję **Przejdź do zarządzania DirSync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informacje na stronie Zarządzanie synchronizacją katalogów

Poniższa tabela zawiera listę funkcji, o których można uzyskać informacje na stronie.
  
Jeśli wystąpił problem z synchronizacją katalogów, błędy są również wyświetlane na tej stronie. Aby uzyskać więcej informacji o różnych błędach, które mogą wystąpić, zobacz [Identyfikowanie błędów synchronizacji katalogów w Microsoft 365](identify-directory-synchronization-errors.md).
  
|Element|Zastosowanie|
|:-----|:-----|
|**Domeny zweryfikowane** | Liczba domen w dzierżawie Microsoft 365 zweryfikowanej przez Ciebie. |
|**Domeny nie zostały zweryfikowane** | Dodane domeny, ale nie zostały zweryfikowane. |
|**Włączono synchronizację katalogów** |Prawda lub Fałsz. Określa, czy włączono synchronizację katalogów. |
|**Najnowsza synchronizacja katalogów** | Ostatnia synchronizacja katalogów została uruchomiona. Wyświetli ostrzeżenie i link do narzędzia do rozwiązywania problemów, jeśli ostatnia synchronizacja była większa niż trzy dni temu. |
|**Włączono synchronizację haseł** | Prawda lub Fałsz. Określa, czy masz synchronizację skrótów haseł między naszą lokalną i dzierżawą Microsoft 365. |
|**Ostatnia synchronizacja haseł** | Ostatnia synchronizacja skrótów haseł została uruchomiona. Wyświetli ostrzeżenie i link do narzędzia do rozwiązywania problemów, jeśli ostatnia synchronizacja była większa niż trzy dni temu. |
|**Wersja klienta synchronizacji katalogów** | Zawiera link pobierania, jeśli została wydana nowa wersja usługi Azure AD Połączenie. |
|**Konto usługi synchronizacji katalogów** | Wyświetla nazwę konta usługi synchronizacji katalogów Microsoft 365. |
|||

## <a name="monitor-synchronization-health"></a>Monitorowanie kondycji synchronizacji

W tej sekcji zainstalujesz agenta usługi Azure AD Połączenie Health na każdym z lokalnych kontrolerów domeny usług AD DS w celu monitorowania infrastruktury tożsamości i usług synchronizacji udostępnianych przez usługę Azure AD Połączenie. Informacje o monitorowaniu są udostępniane w portalu usługi Azure AD Połączenie Health, w którym można wyświetlać alerty, monitorowanie wydajności, analizę użycia i inne informacje.

Kluczowa decyzja dotycząca projektowania sposobu korzystania z usługi Azure AD Połączenie Health zależy od sposobu korzystania z usługi Azure AD Połączenie:

- Jeśli używasz opcji **uwierzytelniania zarządzanego**, zacznij od [korzystania z usługi Azure AD Połączenie Health z synchronizacją](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync), aby zrozumieć i skonfigurować usługę Azure AD Połączenie Health.
- Jeśli synchronizujesz tylko nazwy kont i grup przy użyciu **uwierzytelniania federacyjnego** z usługą Active Directory Federation Services (AD FS), zacznij od [korzystania z usługi Azure AD Połączenie Health z usługami AD FS](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) w celu zrozumienia i skonfigurowania usługi Azure AD Połączenie Health.

Po zakończeniu będziesz mieć następujące elementy:

- Agent usługi Azure AD Połączenie Health zainstalowany na lokalnych serwerach dostawcy tożsamości.
- W portalu usługi Azure AD Połączenie Health wyświetlany jest bieżący stan infrastruktury lokalnej i działania synchronizacji z dzierżawą usługi Azure AD dla subskrypcji Microsoft 365.