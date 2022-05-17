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
description: 'Dowiedz się, jak możesz mieć więcej niż jeden adres e-mail, nazywany aliasem wiadomości e-mail, skojarzony z kontem Microsoft 365 dla firm. '
ms.openlocfilehash: 2951b5eef21748ace22bee50afb24f86123fa46a
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437464"
---
# <a name="add-another-email-alias-for-a-microsoft-365-business-subscription-user"></a>Dodawanie kolejnego aliasu wiadomości e-mail dla Microsoft 365 użytkownika subskrypcji biznesowej
  
Ten artykuł dotyczy administratorów Microsoft 365, którzy mają subskrypcje biznesowe. Nie dotyczy on użytkowników domowych.
  
Podstawowym adresem e-mail w Microsoft 365 jest zwykle adres e-mail, który użytkownik został przypisany podczas tworzenia konta. Podstawowy adres e-mail jest zazwyczaj widoczny w polu  *Od*  w wysyłanych przez użytkownika wiadomościach e-mail w aplikacjach do obsługi poczty e-mail. Mogą również mieć więcej niż jeden adres e-mail skojarzony ze swoim kontem Microsoft 365 dla firm. Takie dodatkowe adresy są nazywane aliasami. 
  
Załóżmy na przykład, że Jenna ma adres e-mail jenna@contosoco.com, ale chce również otrzymywać wiadomości e-mail na jen@contosoco.com, ponieważ niektóre osoby odwołują się do niej pod tą nazwą. Możesz utworzyć dla niej aliasy, aby oba adresy e-mail przechodzić do skrzynki odbiorczej Jenny.
  
Można utworzyć do 400 aliasów dla jednego użytkownika. Nie są przy tym wymagane dodatkowe opłaty ani licencje.
  
> [!Tip]
> Jeśli chcesz, aby wiele osób zarządzało wiadomościami e-mail wysyłanych na jeden adres e-mail, taki jak info@NodPublishers.com lub sales@NodPublishers.com, utwórz udostępnioną skrzynkę pocztową. Aby dowiedzieć się więcej, zobacz [Tworzenie udostępnionej skrzynki pocztowej](create-a-shared-mailbox.md).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą ds. małych firm firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy uzyskujecie całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm w miarę rozwoju firmy — od dołączania do codziennego użytku.
  
## <a name="add-email-aliases-to-a-user"></a>Dodawanie aliasów e-mail użytkownika

Aby dodać aliasy wiadomości e-mail do użytkownika, musisz mieć uprawnienia administratora globalnego.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.

2. Na stronie **Aktywni użytkownicy** wybierz użytkownika, > **Zarządzaj nazwą użytkownika i wiadomością e-mail**. Ta opcja nie zostanie wyświetlona, jeśli dana osoba nie ma przypisanej licencji. 
    
3. Wybierz **pozycję + Dodaj alias** i wprowadź nowy alias użytkownika.   
    
    > [!Important] 
    > Jeśli zostanie wyświetlony komunikat o błędzie "**Nie można odnaleźć parametru zgodnego z nazwą parametru "EmailAddresses**", oznacza to, że ukończenie konfigurowania dzierżawy lub domeny niestandardowej trwa nieco dłużej, jeśli została ostatnio dodana. Proces konfigurowania może potrwać do 4 godzin. Poczekaj chwilę na ukończenie procesu konfigurowania, a następnie spróbuj ponownie. Jeśli problem nie ustąpi, zadzwoń do pomocy technicznej, która przeprowadzi pełną synchronizację dla Ciebie.
    
  
    > [!IMPORTANT]
    > Jeśli subskrypcja została kupiona od firmy GoDaddy lub od innego partnera, aby ustawić nowy alias jako podstawowy, należy przejść do konsoli zarządzania firmy GoDaddy/innego partnera. 


   > [!IMPORTANT]
   >  Jeśli zostanie wyświetlony komunikat o błędzie **Ten użytkownik jest synchronizowany z lokalną usługą Active Directory. Niektóre szczegóły można edytować tylko za pośrednictwem lokalnej usługi Active Directory**. Oznacza to, że usługa Active Directory jest autorytatywna dla atrybutów synchronizowanych użytkowników. Należy zmodyfikować atrybuty w lokalna usługa Active Directory.
  
    > [!TIP]
    > Alias adresu e-mail musi kończyć się domeną z listy rozwijanej. Aby dodać inną nazwę domeny do listy, zobacz [Dodawanie domeny do Microsoft 365](../setup/add-domain.md). 
  
     
5. Po zakończeniu wybierz pozycję **Zapisz zmiany**.
    
6. Poczekaj 24 godziny na wypełnienie nowych aliasów w Microsoft 365.
    
    Użytkownik będzie teraz miał adres podstawowy i alias. Na przykład wszystkie wiadomości wysłane na podstawowy adres Elizy Hoffman, Eliza@NodPublishers.com i jej alias, Sales@NodPublishers.com, trafią do skrzynki odbiorczej Elizy.
    
  
7. **Gdy użytkownik odpowie, adres Od będzie zależeć *od* jej klienta Outlook. Outlook w sieci Web użyje aliasu, w którym odebrano wiadomość e-mail (będziemy nazywać to zasadą ping-ponga). Outlook desktop użyje swojego podstawowego aliasu poczty e-mail.** Załóżmy na przykład, że wiadomość jest wysyłana do Sales@NodPublishers.com i dociera do skrzynki odbiorczej Elizy. Gdy Eliza odpowie na wiadomość przy użyciu Outlook desktop, jej podstawowy adres e-mail będzie wyświetlany jako Eliza@NodPublishers.com, a nie Sales@NodPublishers.com.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Czy został wyświetlony komunikat "Nie można odnaleźć parametru zgodnego z nazwą parametru EmailAddresses"?

Jeśli zostanie wyświetlony komunikat o błędzie "**Nie można odnaleźć parametru zgodnego z nazwą parametru EmailAddresses**", oznacza to, że ukończenie konfigurowania dzierżawy lub domeny niestandardowej trwa nieco dłużej, jeśli została ostatnio dodana. Proces konfigurowania może potrwać do 4 godzin. Poczekaj chwilę na ukończenie procesu konfigurowania, a następnie spróbuj ponownie. Jeśli problem nie ustąpi, zadzwoń do pomocy technicznej, która przeprowadzi pełną synchronizację dla Ciebie.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Czy subskrypcja została kupiona od firmy GoDaddy lub u innego partnera?


Jeśli subskrypcja została kupiona od firmy GoDaddy lub od innego partnera, aby ustawić nowy alias jako podstawowy, należy przejść do konsoli zarządzania firmy GoDaddy/innego partnera.

## <a name="sending-email-from-the-proxy-address-easily"></a>Łatwe wysyłanie wiadomości e-mail z adresu proxy

W lipcu 2021 r. wdrażana jest nowa funkcja, która umożliwia użytkownikom łatwe wysyłanie aliasów podczas korzystania z Outlook w sieci Web. Gdy funkcja jest wdrażana w dzierżawie, w której administrator dzierżawy używa `Set-OrganizationConfig -SendFromAliasEnabled $true` polecenia cmdlet, użytkownicy w dzierżawie otrzymają dostęp do listy pól wyboru, w których każdy wpis odpowiada aliasowi w ustawieniach Outlook. Wybranie aliasu spowoduje wyświetlenie go na liście rozwijanej Od w formularzu Compose.
  
## <a name="related-content"></a>Zawartość pokrewna

[Wysyłanie wiadomości e-mail z innego adresu](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (artykuł)

[Zmienianie nazwy użytkownika i adresu e-mail](../add-users/change-a-user-name-and-email-address.md) (artykuł)

[Konfigurowanie przekazywania wiadomości e-mail w Microsoft 365](configure-email-forwarding.md) (artykuł)
