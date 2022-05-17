---
title: Przywracanie użytkownika
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c261e42-5dd1-48b0-845f-2a016d29cfc1
description: W ciągu 30 dni od usunięcia konta użytkownika można przywrócić konto i wszystkie dane, a użytkownik może zalogować się przy użyciu tego samego konta.
ms.openlocfilehash: 2f9a28e5000c1ba826b5458916f30c3e8a438253
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436212"
---
# <a name="restore-a-user-in-the-microsoft-365-admin-center"></a>Przywracanie użytkownika w Centrum administracyjne platformy Microsoft 365
   
Jeśli konto użytkownika zostanie przywrócone w ciągu 30 dni od jego usunięcia, konto i wszystkie skojarzone z nim dane zostaną przywrócone. Użytkownik może zalogować się, wykorzystując to samo konto służbowe. Skrzynka pocztowa zostanie w pełni przywrócona. Aby dowiedzieć się, ile czasu pozostało do momentu, w którym przywrócenie określonego konta użytkownika nie będzie już możliwe, [skontaktuj się z nami](../../business-video/get-help-support.md).
  
Oto kilka porad:
  
- Upewnij się, że licencje są dostępne do przypisania do konta.
    
- Jeśli Twoja firma korzysta z usługi Active Directory, aby uzyskać instrukcje dotyczące przywracania konta użytkownika, zobacz [Jak rozwiązywać problemy z usuniętymi kontami użytkowników w Office 365](/office365/troubleshoot/active-directory/restore-deleted-user-accounts). 
    
## <a name="restore-one-or-more-user-accounts"></a>Przywracanie jednego lub kilku kont użytkowników

Aby wykonać te kroki, musisz być administratorem globalnym Microsoft 365 lub administratorem zarządzania użytkownikami. 

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">usunięci użytkownicy</a> .

2. Na stronie **Usunięci użytkownicy** wybierz nazwy użytkowników, którzy chcesz przywrócić, a następnie wybierz pozycję **Przywróć**.
    
3. Postępuj zgodnie z monitami, aby ustawić hasło, a następnie wybierz pozycję **Przywróć**.
    
4. Jeśli użytkownik zostanie pomyślnie przywrócony, wybierz pozycję **Wyślij wiadomość e-mail i zamknij**. Jeśli wystąpi konflikt nazw lub konflikt adresów serwera proxy, zapoznaj się z poniższymi instrukcjami dotyczącymi sposobu przywracania tych kont.
    
Po przywróceniu użytkownika upewnij się, że powiadom go o zmianie hasła i postępuj zgodnie z jego instrukcjami.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Przywracanie użytkownika w przypadku konfliktu nazwy użytkownika

Konflikt nazwy użytkownika występuje, gdy usuniesz konto użytkownika, utworzysz nowe konto z tą samą nazwą użytkownika (dla tego samego lub innego użytkownika o podobnym nazwisku), a następnie spróbujesz przywrócić usunięte konto.
  
Aby to naprawić, zastąp aktywne konto tym, które chcesz przywrócić, lub przypisz inną nazwę użytkownika do przywracanego konta, tak aby nie było dwóch kont z tą samą nazwą użytkownika. Poniżej przedstawiono odpowiednią procedurę.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">usunięci użytkownicy</a> .
  
2. Na stronie **Usunięci użytkownicy** wybierz nazwy użytkowników, których chcesz przywrócić, a następnie wybierz pozycję **Przywróć**.
    
    > [!NOTE]
    > Jeśli nie uda się przywrócić dwóch lub większej liczby użytkowników, pojawi się komunikat o błędzie z informacją, że operacja przywracania niektórych użytkowników nie powiodła się. Wyświetl dziennik, aby zobaczyć, których użytkowników nie udało się przywrócić, a następnie przywróć konta pojedynczo. 
  
3. Postępuj zgodnie z monitami, aby ustawić hasło i wybierz pozycję **Przywróć**.
    
4. Zostanie wyświetlony komunikat informujący o wystąpieniu problemu z przywracaniem konta. Wykonaj jedną z następujących czynności:
    
     - Anuluj przywracanie i zmień nazwę bieżącego aktywnego użytkownika. Następnie ponów próbę przywrócenia.
    
     - LUB wpisz nowy podstawowy adres e-mail użytkownika i wybierz pozycję **Przywróć**.
    
5. Przejrzyj wyniki, a następnie wybierz pozycję **Zamknij**.
    
## <a name="restore-a-user-that-has-a-proxy-address-conflict"></a>Przywracanie użytkownika w przypadku konfliktu adresu serwera proxy

Konflikt adresu serwera proxy występuje, gdy usuniesz konto użytkownika zawierające adres serwera proxy, przypiszesz ten adres do innego konta, a następnie spróbujesz przywrócić usunięte konto. Aby naprawić ten problem, wykonaj poniższe czynności.
  
Aby to zrobić, musisz mieć [uprawnienia administratora](about-admin-roles.md) w Microsoft 365. 

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">usunięci użytkownicy</a> .

2. Na stronie **Usunięci użytkownicy** wybierz użytkownika, którego chcesz przywrócić, a następnie wybierz pozycję **Przywróć**. 
    
3. Na stronie **Przywracanie** postępuj zgodnie z instrukcjami, aby ustawić hasło i wybierz pozycję **Przywróć**. Adresy serwerów proxy powodujące konflikt są automatycznie usuwane z profilu przywracanego użytkownika.
    
4. Przejrzyj wyniki, a następnie wybierz pozycję **Zamknij**.

## <a name="related-content"></a>Zawartość pokrewna

[Usuwanie użytkownika](delete-a-user.md) (artykuł)\
[Przypisywanie ról administratora](assign-admin-roles.md) (wideo)\
[Przypisywanie licencji użytkownikom](../manage/assign-licenses-to-users.md) (artykuł)
