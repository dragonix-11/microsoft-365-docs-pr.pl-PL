---
title: Nadaj uprawnienia do skrzynki pocztowej inowi użytkownikowi — Pomoc dla administratorów
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1dbcf12f-a9de-4d1d-b0b3-a227f8a736d8
description: Nadaj użytkownikowi prawo dostępu do skrzynki pocztowej innego użytkownika, co pozwoli użytkownikowi odczytywać i wysyłać wiadomości e-mail ze skrzynki pocztowej innego użytkownika.
ms.openlocfilehash: 82a254081eba2e9b6f4ef83f952b07c743dee2c1
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011330"
---
# <a name="give-mailbox-permissions-to-another-user---admin-help"></a>Nadaj uprawnienia do skrzynki pocztowej inowi użytkownikowi — Pomoc dla administratorów

Jako administrator możesz podlegać wymaganiom firmowym, aby umożliwić niektórym użytkownikom uzyskiwanie dostępu do skrzynki pocztowej innego użytkownika. Na przykład możesz zechcieć umożliwić asystentowi wysyłanie lub odczytywanie wiadomości e-mail ze skrzynki pocztowej jego kierownika lub umożliwić jednemu z użytkowników wysyłanie wiadomości e-mail w imieniu innego użytkownika. W tym temacie pokazano, jak to zrobić.
  
Jeśli szukasz informacji na temat tworzenia udostępnionych skrzynek pocztowych i zarządzania nimi, zobacz [Tworzenie udostępnionej skrzynki pocztowej](../email/create-a-shared-mailbox.md).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.
    
## <a name="looking-to-set-up-mailbox-permissions"></a>Chcesz skonfigurować uprawnienia do skrzynki pocztowej?

Uprawnienia do skrzynki pocztowej pozwalają nadawać innemu użytkownikowi dostęp do odczytu/zapisu w skrzynce pocztowej. Poniższe artykuły mogą udostępnić Ci pomoc potrzebną do skonfigurowania tej funkcji i korzystania z niej:
  
 **Konfigurowanie uprawnień:**
  
Pierwszym krokiem konfigurowania uprawnień jest ustalenie, na wykonywanie których akcji chcesz zezwolić innemu użytkownikowi w danej skrzynce pocztowej. Możesz zezwolić użytkownikowi na czytanie wiadomości e-mail ze skrzynki pocztowej, wysyłanie wiadomości e-mail w imieniu innego użytkownika i wysyłanie wiadomości e-mail, tak jakby były wysyłane z tej skrzynki pocztowej. Zobacz następujące artykuły dotyczące konfigurowania poszczególnych typów uprawnień:
  
- [Czytanie wiadomości e-mail ze skrzynki pocztowej innego użytkownika](give-mailbox-permissions-to-another-user.md#read-email-in-another-users-mailbox)
    
- [Wysyłanie wiadomości e-mail ze skrzynki pocztowej innego użytkownika](give-mailbox-permissions-to-another-user.md#send-email-from-another-users-mailbox)

- [Wysyłanie wiadomości e-mail w imieniu innego użytkownika](give-mailbox-permissions-to-another-user.md#send-email-on-behalf-of-another-user)
    
 **Zmienianie propagacji:**
  
Po skonfigurowaniu uprawnień może upłynąć do 60 minut, zanim zmiany zostaną rozpropagowane w systemie i zaczną obowiązywać.
  
 **Jak używać uprawnień po ich skonfigurowaniu:**
  
Istnieje kilka różnych sposobów uzyskiwania dostępu do skrzynki pocztowej po otrzymaniu do niej dostępu. Aby uzyskać pomoc na ten temat, zobacz ten artykuł: Uzyskiwanie dostępu do [skrzynki pocztowej innej osoby](https://support.microsoft.com/office/A909AD30-E413-40B5-A487-0EA70B763081).

> [!NOTE]
> Uprawnienia można skonfigurować tylko w ramach bieżącej dzierżawy organizacji. Nie można skonfigurować uprawnień skrzynki pocztowej u użytkowników  poza dzierżawą.
  
## <a name="send-email-from-another-users-mailbox"></a>Wysyłanie wiadomości e-mail ze skrzynki pocztowej innego użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.  
    
2. Zaznacz nazwę użytkownika (któremu zamierzasz nadać uprawnienia do wysyłania), aby otworzyć okienko właściwości.
    
3. Na karcie **Poczta** wybierz pozycję **Zarządzaj uprawnieniami skrzynek pocztowych**.

4. Obok pozycji **Wyślij jako** wybierz pozycję **Edytuj**. 

5. Wybierz pozycję **Dodaj uprawnienia**, a następnie wybierz imię i nazwisko osoby, w imieniu której ten użytkownik ma wysyłać wiadomości. 
    
6. Wybierz opcję **Dodaj**.
 
::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>. 

2. Wybierz odpowiedniego użytkownika, rozwiń pozycję **Ustawienia poczty**, a następnie wybierz pozycję **Edytuj** obok pozycji **Uprawnienia do skrzynki pocztowej**.

3. Obok pozycji **Wyślij jako** wybierz pozycję **Edytuj**. 

4. Wybierz pozycję **Dodaj uprawnienia**, a następnie wybierz imię i nazwisko osoby, w imieniu której ten użytkownik ma wysyłać wiadomości. 
    
5. Wybierz opcję **Dodaj**.

::: moniker-end
  
## <a name="read-email-in-another-users-mailbox"></a>Czytanie wiadomości e-mail w skrzynce pocztowej innego użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.  
    
2. Wybierz nazwę użytkownika (którego skrzynka pocztowa ma być dostępna do odczytu), aby otworzyć okienko właściwości.
    
3. Na karcie **Poczta** wybierz pozycję **Zarządzaj uprawnieniami skrzynek pocztowych**.
    
4. Obok pozycji **Odczyt i zarządzanie** wybierz pozycję **Edytuj**. 
    
5. Wybierz pozycję **Dodaj uprawnienia** i wybierz nazwę użytkownika lub użytkowników, którym chcesz zezwolić na odczytywanie wiadomości e-mail z tej skrzynki pocztowej.

6. Wybierz opcję **Dodaj**.


> [!NOTE]
> **Uprawnienia** do odczytu **i** zarządzania są nazywane **uprawnieniami Pełny** dostęp w przypadku ich Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">administracyjnego</a>. To uprawnienie umożliwia przypisanej skrzynce pocztowej użytkownika czytanie wiadomości e-mail oraz zarządzanie wiadomościami e-mail w skrzynce pocztowej użytkownika, do której przypisano uprawnienie. Uprawnienia Pełny dostęp nie przyznają **uprawnień Wyślij jako** ani **Wyślij w imieniu**  .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>. 
  
2. Wybierz odpowiedniego użytkownika, rozwiń pozycję **Ustawienia poczty**, a następnie wybierz pozycję **Edytuj** obok pozycji **Uprawnienia do skrzynki pocztowej**.
    
3. Obok pozycji **Odczyt i zarządzanie** wybierz pozycję **Edytuj**. 
    
4. Wybierz pozycję **Dodaj uprawnienia** i wybierz nazwę użytkownika lub użytkowników, którym chcesz zezwolić na odczytywanie wiadomości e-mail z tej skrzynki pocztowej.

5. Wybierz opcję **Dodaj**.

::: moniker-end


## <a name="send-email-on-behalf-of-another-user"></a>Wysyłanie wiadomości e-mail w imieniu innego użytkownika

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.  

2. Zaznacz nazwę użytkownika (któremu zamierzasz nadać uprawnienia **Wyślij w imieniu**), aby otworzyć okienko właściwości.
    
3. Na karcie **Poczta** wybierz pozycję **Zarządzaj uprawnieniami skrzynek pocztowych**.
    
4. Obok pozycji **Wyślij w imieniu** wybierz pozycję **Edytuj**.

5. Wybierz pozycję **Dodaj uprawnienia** i wybierz nazwę użytkownika lub użytkowników, którym chcesz zezwolić na wysyłanie wiadomości e-mail z tej skrzynki pocztowej.

6. Wybierz opcję **Dodaj**.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktywni użytkownicy</a>. 

2. Wybierz odpowiedniego użytkownika, rozwiń pozycję **Ustawienia poczty**, a następnie wybierz pozycję **Edytuj** obok pozycji **Uprawnienia do skrzynki pocztowej**.

3. Obok pozycji **Wyślij w imieniu** wybierz pozycję **Edytuj**.
    
4. Wybierz pozycję **Dodaj uprawnienia** i wybierz nazwę użytkownika lub użytkowników, którym chcesz zezwolić na wysyłanie wiadomości e-mail z tej skrzynki pocztowej.

5. Wybierz opcję **Dodaj**.

::: moniker-end


## <a name="related-content"></a>Zawartość pokrewna
  
[Zarządzanie elementami poczty i kalendarza innej osoby](https://support.microsoft.com/office/afb79d6b-2967-43b9-a944-a6b953190af5) (artykuł)\   
[Wysyłanie wiadomości e-mail od innej osoby lub grupy](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b) (artykuł)\
[Zmienianie nazwy użytkownika i adresu e-mail](../add-users/change-a-user-name-and-email-address.md) (klip wideo)

