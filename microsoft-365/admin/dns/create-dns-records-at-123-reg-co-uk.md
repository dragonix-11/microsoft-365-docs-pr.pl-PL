---
title: Połączenie rekordów DNS w 123-reg.co.uk Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w witrynie 123-reg.co.uk firmy Microsoft.
ms.openlocfilehash: 050aad4ca3e0e768b160a7ba210a93e163d72fe7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314941"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>Połączenie rekordów DNS w 123-reg.co.uk Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
Jeśli witryna 123-reg.co.uk jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online itp.
  
Po dodaniu tych rekordów w 123-reg.co.uk Twoja domena będzie skonfigurować do współpracy z usługi firmy Microsoft. 
  
> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziecie używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.
  
> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Wybierz **pozycję** Domeny, a następnie na stronie Domain name overview (Omówienie nazw domen) wybierz nazwę domeny, którą chcesz zweryfikować, lub przejdź do panelu sterowania.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz domenę, którą chcesz zweryfikować.":::

3. Na stronie Manage domain (Zarządzanie domeną) w obszarze **Advanced domain settings (Zaawansowane ustawienia domeny)** wybierz pozycję **Manage DNS (Zarządzaj systemem DNS**).
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::
  
4. Na stronie Manage your DNS (Zarządzanie systemem DNS) wybierz **kartę Advanced DNS (Zaawansowane ustawienia DNS** ). 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Advanced DNS (Zaawansowana karta DNS).":::
  
5. W polu **Typ** nowego rekordu wybierz z listy rozwijanej pozycję **TXT/SPF** , a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli. 

    ||||
    |:-----|:-----|:-----|
    |**Hostname (Nazwa hosta)** <br/> |**Type (Typ)** <br/> |**Destination TXT/SPF (TXT/SPF miejsca docelowego)** <br/> |
    |@  <br/> |TXT/SPF  <br/> |MS=ms *XXXXXXXX*  <br/> **Uwaga:** To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)          |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Z listy rozwijanej wybierz typ TXT/SPF i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Wybierz pozycję Dodaj.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz wyszukania tego rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.
  
Aby zweryfikować rekord w Microsoft 365:
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.

1. Na stronie Domeny wybierz weryfikowaną domenę, a następnie wybierz pozycję **Rozpocznij konfigurowanie**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Wybierz **pozycję Kontynuuj**.
  
1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodawanie rekordu MX, aby poczta e-mail dla Twojej domeny trafiała do firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

3. Na stronie Manage domain (Zarządzanie domeną) w obszarze **Advanced domain settings (Zaawansowane ustawienia domeny)** wybierz pozycję **Manage DNS (Zarządzaj systemem DNS**).
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::
  
4. Na stronie Manage your DNS (Zarządzanie systemem DNS) wybierz **kartę Advanced DNS (Zaawansowane ustawienia DNS** ). 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Advanced DNS (Zaawansowana karta DNS).":::

5. W polu **Typ** nowego rekordu wybierz pozycję **MX** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |**Hostname (Nazwa hosta)**|**Type (Typ)**|**Priority (Priorytet)**|**Destination MX (MX miejsca docelowego)**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |1  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) <br/> | *\<domain-key\>*  mail.protection.outlook.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> **Uwaga:** Pobierz ze \<domain-key\> swojego konta Microsoft. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)          |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="Wybierz z listy rozwijanej typ rekordu MX i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="Wybierz pozycję Dodaj.":::

7. Jeśli istnieją inne rekordy MX, usuń każdy z nich, wybierając dla tego rekordu ikonę **Delete (trash can) (Usuń (** kosz na śmieci).

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="Wybierz pozycję Usuń (kosz na śmieci).":::
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

3. Na stronie Manage domain (Zarządzanie domeną) w obszarze **Advanced domain settings (Zaawansowane ustawienia domeny)** wybierz pozycję **Manage DNS (Zarządzaj systemem DNS**).
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::
  
4. Na stronie Manage your DNS (Zarządzanie systemem DNS) wybierz **kartę Advanced DNS (Zaawansowane ustawienia DNS** ). 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Advanced DNS (Zaawansowana karta DNS).":::

5. Dodaj rekord CNAME.

    W polu **Typ** nowego rekordu wybierz z listy rozwijanej wartość **CNAME** , a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |**Hostname (Nazwa hosta)**|**Type (Typ)**|**Destination CNAME (CNAME miejsca docelowego)**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |autodiscover.outlook.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Wybierz typ CNAME z listy rozwijanej i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Wybierz pozycję Dodaj.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla aplikacji Microsfot. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy  *rekord SPF,*  który zawiera oba zestawy wartości. Potrzebujesz przykładów? Zapoznaj się z tymi [rekordami systemu nazw domen zewnętrznych dla firmy Microsoft](../../enterprise/external-domain-name-system-records.md). Do zweryfikowania rekordu SPF możesz użyć jednego z następujących [narzędzi do weryfikowania rekordu SPF](../setup/domains-faq.yml). 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

3. Na stronie Manage domain (Zarządzanie domeną) w obszarze **Advanced domain settings (Zaawansowane ustawienia domeny)** wybierz pozycję **Manage DNS (Zarządzaj systemem DNS**).
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::
  
4. Na stronie Manage your DNS (Zarządzanie systemem DNS) wybierz **kartę Advanced DNS (Zaawansowane ustawienia DNS** ). 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Advanced DNS (Zaawansowana karta DNS).":::

5. W polu **Typ** nowego rekordu wybierz z listy rozwijanej pozycję **TXT/SPF** , a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |**Hostname (Nazwa hosta)**|**Type (Typ)**|**Destination TXT/SPF (TXT/SPF miejsca docelowego)**|
    |:-----|:-----|:-----|
    |@  <br/> |TXT/SPF  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.           |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Z listy rozwijanej wybierz typ TXT/SPF i wypełnij wartości.":::
  
6. Wybierz opcję **Dodaj**.

## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype 4 rekordy: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME do zalogowania się i połączenia użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

3. Na stronie Manage domain (Zarządzanie domeną) w obszarze **Advanced domain settings (Zaawansowane ustawienia domeny)** wybierz pozycję **Manage DNS (Zarządzaj systemem DNS**).
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::
  
4. Na stronie Manage your DNS (Zarządzanie systemem DNS) wybierz **kartę Advanced DNS (Zaawansowane ustawienia DNS** ). 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Advanced DNS (Zaawansowana karta DNS).":::

5. Dodaj pierwszy z dwóch rekordów SRV:

   W polu **Typ** nowego rekordu wybierz pozycję **SRV** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    ||||||
    |:-----|:-----|:-----|:-----|:-----|
    |**Hostname (Nazwa hosta)**|**Type (Typ)**|**Priority (Priorytet)**|**TTL (Czas wygaśnięcia)**|**Destination SRV (SRV miejsca docelowego)**|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **Wartość ta MUSI mieć na końcu kropkę (.)**<br> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.           |
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **Wartość ta MUSI mieć na końcu kropkę (.)** <br> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.           |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Z listy rozwijanej wybierz typ TXT/SPF i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Wybierz pozycję Dodaj.":::

7. Dodaj drugi rekord SRV.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME 

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

1. Na stronie Manage domain (Zarządzanie domeną) w obszarze **Advanced domain settings (Zaawansowane ustawienia domeny)** wybierz pozycję **Manage DNS (Zarządzaj systemem DNS**).
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::
  
1. Na stronie Manage your DNS (Zarządzanie systemem DNS) wybierz **kartę Advanced DNS (Zaawansowane ustawienia DNS** ). 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Advanced DNS (Zaawansowana karta DNS).":::

1. Dodaj pierwszy rekord CNAME.

    W polu **Typ** nowego rekordu wybierz z listy rozwijanej wartość **CNAME** , a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    | **Hostname (Nazwa hosta)** |**Type (Typ)**|**Destination CNAME (CNAME miejsca docelowego)**|
    |:-----|:-----|:-----|
    |sip  <br/>|CNAME  <br/> |sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |
    |lyncdiscover  <br/>|CNAME  <br/> |webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Wybierz typ CNAME z listy rozwijanej i wypełnij wartości.":::

1. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Wybierz pozycję Dodaj.":::
  
1. Dodaj drugi rekord CNAME.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: Intune i Zarządzanie urządzeniami przenośnymi dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Zarządzanie urządzeniami przenośnymi wymaga dwóch rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

1. Na stronie Manage domain (Zarządzanie domeną) w obszarze **Advanced domain settings (Zaawansowane ustawienia domeny)** wybierz pozycję **Manage DNS (Zarządzaj systemem DNS**).
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::
  
1. Na stronie Manage your DNS (Zarządzanie systemem DNS) wybierz **kartę Advanced DNS (Zaawansowane ustawienia DNS** ). 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Advanced DNS (Zaawansowana karta DNS).":::

1. Dodaj pierwszy rekord CNAME.

    W polu **Typ** nowego rekordu wybierz z listy rozwijanej wartość **CNAME** , a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

   | **Hostname (Nazwa hosta)**|**Type (Typ)**|**Destination CNAME (CNAME miejsca docelowego)**|
   |:-----|:-----|:-----|
   | enterpriseregistration <br/> | CNAME  <br/> |enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |
   |enterpriseenrollment  <br/> | CNAME  <br/> |enterpriseenrollment.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Wybierz typ CNAME z listy rozwijanej i wypełnij wartości.":::

1. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Wybierz pozycję Dodaj.":::

1. Dodaj drugi rekord CNAME.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).