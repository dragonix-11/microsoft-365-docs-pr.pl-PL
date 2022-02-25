---
title: Wyświetlanie stanu synchronizacji katalogów w programie Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule dowiesz się, jak sprawdzić stan synchronizacji katalogów w programie Office 365.
ms.openlocfilehash: 0cc5b5244c5809d3f1b13b15b200bd8cea585c7c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62959562"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Wyświetlanie stanu synchronizacji katalogów w programie Microsoft 365

Jeśli zintegrowano lokalną usługę Usługi domenowe w usłudze Active Directory (AD DS) z usługą Azure Active Directory (Azure AD), synchronizując środowisko lokalne z usługą Microsoft 365, możesz także sprawdzić stan synchronizacji.
  
## <a name="view-directory-synchronization-status"></a>Wyświetlanie stanu synchronizacji katalogów

- Zaloguj się do narzędzia [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) wybierz pozycję **Stan narzędzia DirSync** na stronie głównej.
- Możesz również przejść do strony  \> Aktywni **użytkownicy użytkownicy i** na stronie Aktywni  użytkownicy wybrać pozycję **Więcej synchronizacji** \> **katalogów**. W **okienku Synchronizacja** katalogów wybierz pozycję **Przejdź do zarządzania synchronizacją katalogów**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informacje na stronie Zarządzanie synchronizacją katalogów

W poniższej tabeli wymieniono funkcje, o których można uzyskać informacje na stronie.
  
Jeśli występuje problem z synchronizacją katalogu, na tej stronie są również wymienione błędy. Aby uzyskać więcej informacji o różnych błędach, które mogą wystąpić, zobacz Identyfikowanie błędów synchronizacji katalogów [w programie Microsoft 365](identify-directory-synchronization-errors.md).
  
|Element|Zastosowanie|
|:-----|:-----|
|**Domeny zweryfikowane** | Liczba domen w Twojej dzierżawie Microsoft 365, do których należysz. |
|**Domeny nie zostały zweryfikowane** | Domeny dodane, ale nie zweryfikowane. |
|**Włączono synchronizację katalogów** |Prawda lub fałsz. Określa, czy włączono synchronizację katalogów. |
|**Najnowsza synchronizacja katalogów** | Termin ostatniego uruchomiono synchronizację katalogów. Jeśli ostatnia synchronizacja została trwająca ponad 3 dni temu, zostanie wyświetlane ostrzeżenie i link do narzędzia do rozwiązywania problemów. |
|**Włączono synchronizację haseł** | Prawda lub fałsz. Określa, czy synchronizacja skrótów haseł między usługą lokalną a dzierżawą Microsoft 365 haseł. |
|**Ostatnia synchronizacja haseł** | Termin ostatniego uruchomiono synchronizację skrótów haseł. Jeśli ostatnia synchronizacja została trwająca ponad 3 dni temu, zostanie wyświetlane ostrzeżenie i link do narzędzia do rozwiązywania problemów. |
|**Wersja klienta synchronizacji katalogów** | Zawiera link pobierania, jeśli została wydana Połączenie usługi Azure AD. |
|**Konto usługi synchronizacji katalogów** | Wyświetla nazwę konta usługi Microsoft 365 synchronizacji katalogów. |
|||

## <a name="monitor-synchronization-health"></a>Monitorowanie kondycji synchronizacji

W tej sekcji zainstalujesz agenta usługi Azure AD Połączenie Health w każdym lokalnym kontrolerze domeny usługi AD DS, aby monitorować infrastrukturę tożsamości i usługi synchronizacji udostępniane przez usługę Azure AD Połączenie. Informacje dotyczące monitorowania są dostępne w portalu kondycji usługi Azure AD Połączenie, w którym można wyświetlać alerty, monitorowanie wydajności, analizy użycia i inne informacje.

Kluczowa decyzja co do projektu sposobu korzystania z usługi Azure AD Połączenie Health zależy od tego, jak korzystasz z usługi Azure AD Połączenie:

- Jeśli korzystasz z opcji uwierzytelniania  zarządzanego, zacznij od tematu Używanie usługi [Azure AD Połączenie Health](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) z synchronizacją, aby poznać i skonfigurować usługę Azure AD Połączenie Health.
- Jeśli synchronizuje się tylko nazwy kont i grup za pomocą uwierzytelniania **feder** sądowego z usługami federacyjną Active Directory (AD FS), zacznij od korzystania z usługi [Azure AD Połączenie Health](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) z usługami AD FS w celu zrozumienia i skonfigurowania usługi Azure AD Połączenie Health.

Po zakończeniu będziesz mieć:

- Agent usługi Azure AD Połączenie Health zainstalowany na twoich lokalnych serwerach dostawców tożsamości.
- Portal usługi Azure AD Połączenie Health z wyświetlonym bieżącym stanem infrastruktury lokalnej i działaniami synchronizacji z dzierżawą usługi Azure AD na Microsoft 365 subskrypcji usługi.