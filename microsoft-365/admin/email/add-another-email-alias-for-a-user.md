---
title: Dodawanie kolejnego aliasu e-mail użytkownika
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
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0b0bd900-68b1-4bf5-808b-5d240a7739f4
description: 'Dowiedz się, jak możesz mieć więcej niż jeden adres e-mail nazywany aliasem e-mail skojarzonym z Microsoft 365 dla firm. '
ms.openlocfilehash: f5adc9e48110aa1e2a2e6c87f2c2f7847986d741
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "62973885"
---
# <a name="add-another-email-alias-for-a-user"></a>Dodawanie kolejnego aliasu e-mail użytkownika
  
Ten artykuł jest Microsoft 365 administratorów, którzy mają subskrypcję dla firm. Nie dotyczy on użytkowników domowych.
  
Podstawowym adresem e-mail w Microsoft 365 zwykle jest adres e-mail przypisany użytkownikowi podczas jego tworzenia. Podstawowy adres e-mail jest zazwyczaj widoczny w polu  *Od*  w wysyłanych przez użytkownika wiadomościach e-mail w aplikacjach do obsługi poczty e-mail. Może mieć więcej niż jeden adres e-mail skojarzony z kontem Microsoft 365 dla firm. Takie dodatkowe adresy są nazywane aliasami. 
  
Załóżmy na przykład, że Joanna ma adres e-mail jenna@contosoco.com, ale chce też odbierać wiadomości e-mail w programie jen@contosoco.com, ponieważ niektóre osoby odwołują się do niej, korzystając z tego imienia i nazwiska. Możesz utworzyć aliasy dla niej, aby oba adresy e-mail trafiały do skrzynki odbiorczej Jana.
  
Można utworzyć do 400 aliasów dla jednego użytkownika. Nie są przy tym wymagane dodatkowe opłaty ani licencje.
  
> [!Tip]
> Jeśli chcesz, aby wiele osób zarządzało wiadomościami e-mail wysyłanymi na jeden adres e-mail, info@NodPublishers.com lub sales@NodPublishers.com, utwórz udostępnioną skrzynkę pocztową. Aby dowiedzieć się więcej, zobacz [Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.
  
## <a name="add-email-aliases-to-a-user"></a>Dodawanie aliasów e-mail użytkownika

Aby dodać aliasy e-mail do użytkownika, musisz mieć uprawnienia administratora globalnego.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

2. Na stronie **Aktywni użytkownicy** wybierz użytkownika, > **nazwę użytkownika i adres e-mail**. Nie zobaczysz tej opcji, jeśli ta osoba nie ma przypisanej do tej osoby licencji. 
    
3. Wybierz **pozycję + Dodaj alias** i wprowadź nowy alias dla użytkownika.   
    
    > [!Important] 
    > Jeśli zostanie wyświetlony komunikat o błędzie "Nie można odnaleźć parametru, który odpowiada nazwie parametru **"EmailAddresses**", oznacza to, że koństwo konfigurowania dzierżawy lub domeny niestandardowej, jeśli ostatnio ją dodano, trwa nieco dłużej. Proces konfigurowania może potrwać do 4 godzin. Poczekaj chwilę na ukończenie procesu konfigurowania, a następnie spróbuj ponownie. Jeśli problem nie ustąpi, zadzwoń do pomocy technicznej, która przeprowadzi pełną synchronizację dla Ciebie.
    
  
    > [!IMPORTANT]
    > Jeśli subskrypcja została kupiona od firmy GoDaddy lub od innego partnera, aby ustawić nowy alias jako podstawowy, należy przejść do konsoli zarządzania firmy GoDaddy/innego partnera. 


   > [!IMPORTANT]
   >  Jeśli zostanie wyświetlony komunikat o błędzie **Ten użytkownik jest synchronizowany z lokalną usługą Active Directory. Niektóre szczegóły można** edytować tylko za pośrednictwem lokalnej usługi Active Directory, oznacza to, że usługa Active Directory ma autorytatywny atrybut dla zsynchronizowanych użytkowników, musisz zmodyfikować atrybuty w lokalnej usłudze Active Directory.
  
    > [!TIP]
    > Alias adresu e-mail musi kończyć się domeną z listy rozwijanej. Aby dodać do listy inną nazwę domeny, zobacz [Dodawanie domeny](../setup/add-domain.md) do Microsoft 365. 
  
     
5. Gdy wszystko będzie gotowe, wybierz pozycję **Zapisz zmiany**.
    
6. Poczekaj 24 godziny, aż nowe aliasy zostaną wypełnione w ciągu Microsoft 365.
    
    Użytkownik będzie miał teraz adres podstawowy i alias. Na przykład cała poczta wysyłana na adres podstawowy Oraz Eliza@NodPublishers.com i jej alias (Sales@NodPublishers.com) zostanie wysłana do skrzynki odbiorczej Elizy.
    
  
7. **Gdy użytkownik odpowie, adres *Od* będzie zależny od Outlook klienta. Outlook w sieci Web będą używać aliasu, pod którym odebrano wiadomość e-mail (tę zasadę nazywamy zasadą ping-pong). Outlook będzie używać swojego podstawowego aliasu e-mail.** Załóżmy na przykład, że wiadomość została wysłana do Sales@NodPublishers.com i dotarła do skrzynki odbiorczej Elżbiety. Gdy Eliza odpowie na wiadomość przy użyciu komputera Outlook, jej podstawowy adres e-mail będzie wyświetlany jako Eliza@NodPublishers.com, a nie Sales@NodPublishers.com.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Czy został znaleziony "Nie można odnaleźć parametru, który pasuje do nazwy parametru EmailAddresses"?

Jeśli zostanie wyświetlony komunikat o błędzie "Nie można odnaleźć parametru, który odpowiada nazwie parametru **EmailAddresses**", oznacza to, że koństwo konfigurowania dzierżawy lub domeny niestandardowej, jeśli ostatnio ją dodano, trwa nieco dłużej. Proces konfigurowania może potrwać do 4 godzin. Poczekaj chwilę na ukończenie procesu konfigurowania, a następnie spróbuj ponownie. Jeśli problem nie ustąpi, zadzwoń do pomocy technicznej, która przeprowadzi pełną synchronizację dla Ciebie.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Czy subskrypcja została kupiona od firmy GoDaddy lub u innego partnera?


Jeśli subskrypcja została kupiona od firmy GoDaddy lub od innego partnera, aby ustawić nowy alias jako podstawowy, należy przejść do konsoli zarządzania firmy GoDaddy/innego partnera.

## <a name="sending-email-from-the-proxy-address-easily"></a>Łatwe wysyłanie wiadomości e-mail z adresu serwera proxy

W lipcu 2021 r. zostanie w wer. nowa funkcja, która umożliwia użytkownikom łatwe wysyłanie wiadomości ze swoich aliasów podczas korzystania z Outlook w sieci Web. `Set-OrganizationConfig -SendFromAliasEnabled $true` Po wejściu funkcji do dzierżawy, w której administrator dzierżawy używa polecenia cmdlet, użytkownicy w ramach dzierżawy uzyskają dostęp do listy pól wyboru, gdzie każdy wpis odpowiada aliasowi w ustawieniach usługi Outlook dzierżawy. Wybranie aliasu spowoduje, że będzie on wyświetlany na liście rozwijanej Od w formularzu redagowania.
  
## <a name="related-content"></a>Zawartość pokrewna

[Wysyłanie wiadomości e-mail z innego adresu](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (artykuł)

[Zmienianie nazwy użytkownika i adresu e-mail](../add-users/change-a-user-name-and-email-address.md) (artykuł)

[Konfigurowanie przesyłania dalej poczty e-mail Microsoft 365](configure-email-forwarding.md) (artykuł)
