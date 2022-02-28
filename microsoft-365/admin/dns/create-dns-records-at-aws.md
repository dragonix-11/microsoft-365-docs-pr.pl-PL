---
title: Połączenie rekordów DNS w witrynie Amazon Web Services (AWS), aby Microsoft 365
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.assetid: 7a2efd75-0771-4897-ba7b-082fe5bfa9da
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w witrynie Amazon Web Services (AWS) dla firmy Microsoft.
ms.openlocfilehash: 27b1659a1a5e870a46a08786973ba857dc9ce939
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989495"
---
# <a name="connect-your-dns-records-at-amazon-web-services-aws-to-microsoft-365"></a>Połączenie rekordów DNS w witrynie Amazon Web Services (AWS), aby Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
Jeśli usługa AWS jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype Online dla Firm itp.
  
Po dodaniu tych rekordów w  rejestratorze domen AWS Twoja domena będzie skonfigurować do współpracy usługi firmy Microsoft.
  
> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziecie używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.
  
> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W **obszarze Domain Name** (Nazwa domeny) wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli twoja domena nie została jeszcze utworzona jako hostowana strefa, wybierz pozycję **Utwórz** hostowaną strefę i wykonaj kroki przed przejściem do następnego kroku. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz zweryfikować.":::

1. Wybierz **pozycję Manage DNS (Zarządzaj systemem DNS**). 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Domain name** (Nazwa domeny) wybierz nazwę domeny hostowanej wersji strefy domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny, którą chcesz zweryfikować.":::

1. Wybierz **pozycję Create record (Utwórz rekord**).

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Create record (Utwórz rekord).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    Z list **rozwijanych** wybierz wartości zasad **Typu** i Routing.

    > [!TIP]
    > Znaki cudzysłowu wymagane w instrukcjach wyświetlanych na ekranie zostaną wprowadzone automatycznie. Nie musisz wpisywać ich ręcznie. 
  
    ||||||
    |:-----|:-----|:-----|:-----|:-----|
    |**Nazwa rekordu** <br/> |**Typ rekordu** <br/> |**Wartość** <br/> |**TTL (Seconds) [Czas wygaśnięcia (w sekundach)]** <br/> |**Zasady routingu** <br/> |
    |Pozostaw to pole puste.  <br/> |TXT — służy do weryfikowania nadawców wiadomości e-mail  <br/> |MS=ms *XXXXXXXX*  <br/>**Uwaga:** To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli w Microsoft 365. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md) |300  <br/> |Simple (Proste)  <br/> |

1. Wybierz **pozycję Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz wyszukania tego rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w Microsoft 365:
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.

1. Na stronie Domeny wybierz weryfikowaną domenę, a następnie wybierz pozycję **Rozpocznij konfigurowanie**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Wybierz **pozycję Kontynuuj**.
  
1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>Dodaj rekord MX, aby poczta e-mail dla Twojej domeny trafiała do Microsoft 365

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W **obszarze Domain Name** (Nazwa domeny) wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli twoja domena nie została jeszcze utworzona jako hostowana strefa, wybierz pozycję **Utwórz** hostowaną strefę i wykonaj kroki przed przejściem do następnego kroku. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Manage DNS (Zarządzaj systemem DNS**). 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Domain name** (Nazwa domeny) wybierz nazwę domeny hostowanej wersji strefy domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Create record (Utwórz rekord**).

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Create record (Utwórz rekord)."::: 

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. 

    Z list **rozwijanych** wybierz wartości zasad **Typu** i Routing. 

    > [!TIP]
    > Znaki cudzysłowu wymagane w instrukcjach wyświetlanych na ekranie zostaną wprowadzone automatycznie. Nie musisz wpisywać ich ręcznie. 

    |**Nazwa rekordu**|**Typ rekordu**|**Wartość**|**TTL (Seconds) [Czas wygaśnięcia (w sekundach)]**|**Zasady routingu**|
    |:-----|:-----|:-----|:-----|:-----|
    |Pozostaw to pole puste.  <br/> |MX — określa serwery poczty  <br/> |0,mail.protection.outlook.com  *\<domain-key\>*  .  <br/> 0 to wartość priorytetu rekordu MX. Dodaj ją na początku wartości MX i oddziel ją od reszty wartości spacją.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> **Uwaga:** Pobierz ze \<*domain-key*\> swojego Microsoft 365 konta. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md) | 300  <br/> | Prosty routing <br/> |
  
1. Wybierz **pozycję Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-mx-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

1. Jeśli istnieją inne rekordy MX, usuń je, zaznaczając rekord, a następnie wybierając pozycję **Delete (Usuń**).
  
## <a name="add-the-cname-record-required-for-microsoft-365"></a>Dodawanie rekordu CNAME wymaganego dla Microsoft 365

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W **obszarze Domain Name** (Nazwa domeny) wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli twoja domena nie została jeszcze utworzona jako hostowana strefa, wybierz pozycję **Utwórz** hostowaną strefę i wykonaj kroki przed przejściem do następnego kroku. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Manage DNS (Zarządzaj systemem DNS**). 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Domain name** (Nazwa domeny) wybierz nazwę domeny hostowanej wersji strefy domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Create record (Utwórz rekord**).

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Create record (Utwórz rekord).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. 

    Z list **rozwijanych** wybierz wartości zasad **Typu** i Routing. 

    |**Nazwa rekordu**|**Typ rekordu**|**Wartość**| **TTL (Czas wygaśnięcia)** |**Zasady routingu**|
    |:-----|:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME — Kieruje ruch do innej nazwy domeny  <br/> | autodiscover.outlook.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> | 300  <br/> |Simple (Proste)  <br/> |
  
1. Wybierz **pozycję Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy  *rekord SPF,*  który zawiera oba zestawy wartości. Potrzebujesz przykładów? Zapoznaj się z tymi [rekordami systemu nazw domen zewnętrznych dla firmy Microsoft](../../enterprise/external-domain-name-system-records.md). Do zweryfikowania rekordu SPF możesz użyć jednego z narzędzi do sprawdzania poprawności [platformy](../setup/domains-faq.yml) SPF. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W **obszarze Domain Name** (Nazwa domeny) wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli twoja domena nie została jeszcze utworzona jako hostowana strefa, wybierz pozycję **Utwórz** hostowaną strefę i wykonaj kroki przed przejściem do następnego kroku. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Manage DNS (Zarządzaj systemem DNS**). 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Domain name** (Nazwa domeny) wybierz nazwę domeny hostowanej wersji strefy domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Create record (Utwórz rekord**).

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Create record (Utwórz rekord).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. 

    Z list **rozwijanych** wybierz wartość Type (Typ). 

    |**Typ rekordu** | **Wartość**|
    |:-----|:-----|
    |TXT — służy do weryfikowania nadawców wiadomości e-mail i do sprawdzania wartości specyficznych dla aplikacji |v=spf1 include:spf.protection.outlook.com -all  <br/> Znaki cudzysłowu wymagane w instrukcjach wyświetlanych na ekranie zostaną wprowadzone automatycznie. Nie musisz wpisywać ich ręcznie.  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.   |
  
1. Wybierz **pozycję Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype 4 rekordy: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME do zalogowania się i połączenia użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W **obszarze Domain Name** (Nazwa domeny) wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli twoja domena nie została jeszcze utworzona jako hostowana strefa, wybierz pozycję **Utwórz** hostowaną strefę i wykonaj kroki przed przejściem do następnego kroku. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Manage DNS (Zarządzaj systemem DNS**). 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Domain name** (Nazwa domeny) wybierz nazwę domeny hostowanej wersji strefy domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Create record (Utwórz rekord**).

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Create record (Utwórz rekord)."::: 

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. 

    Z list rozwijanych wybierz wartości **Type** (Typ) i **Routing Policy** (Zasady routingu). 

    |**Nazwa rekordu**|**Typ rekordu**|**Wartość**|**TTL (Seconds) [Czas wygaśnięcia (w sekundach)]**|**Zasady routingu**|
    |:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV — wartości serwerów identyfikatorów specyficzne dla aplikacji|100 1 443 sipdir.online.lync.com. **Ta wartość MUSI mieć na końcu okres (.)**><br> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne. | 300 |Simple (Proste)|
    |_sipfederationtls._tcp|SRV — wartości serwerów identyfikatorów specyficzne dla aplikacji|100 1 5061 sipfed.online.lync.com. **Wartość ta MUSI mieć na końcu kropkę (.)**<br> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.    | 300 |Simple (Proste)|
  
1. Aby dodać drugi rekord SRV, wybierz pozycję **Add another record** (Dodaj kolejny rekord), utwórz rekord, używając wartości z następnego wiersza w tabeli, a następnie ponownie wybierz pozycję **Create records (Utwórz rekordy**). 

   :::image type="content" source="../../media/dns-aws/aws-domians-srv-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME 

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W **obszarze Domain Name** (Nazwa domeny) wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli twoja domena nie została jeszcze utworzona jako hostowana strefa, wybierz pozycję **Utwórz** hostowaną strefę i wykonaj kroki przed przejściem do następnego kroku.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Manage DNS (Zarządzaj systemem DNS**). 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Domain name** (Nazwa domeny) wybierz nazwę domeny hostowanej wersji strefy domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Create record (Utwórz rekord**). 

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Create record (Utwórz rekord).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    Z list **rozwijanych** wybierz wartości zasad **Typu** i Routing.

     |**Nazwa rekordu**|**Typ rekordu**|**Wartość**| **TTL (Czas wygaśnięcia)** |**Zasady routingu**|
    |:-----|:-----|:-----|:-----|:-----|
    |sip  <br/> |CNAME  Canonical name (CNAME  Nazwa kanoniczna)  <br/> |sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |300  <br/> |Simple (Proste)  <br/> |
    |lyncdiscover  <br/> |CNAME  Canonical name (CNAME  Nazwa kanoniczna)  <br/> |webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/>  |300  <br/> ||Simple (Proste)  <br/> |
  
1. Aby dodać drugi rekord CNAME, wybierz pozycję **Add another record** (Dodaj kolejny rekord), utwórz rekord, używając wartości z następnego wiersza w tabeli. 

1. Wybierz **pozycję Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: Intune i Zarządzanie urządzeniami przenośnymi dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Zarządzanie urządzeniami przenośnymi wymaga dwóch rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W **obszarze Domain Name** (Nazwa domeny) wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli twoja domena nie została jeszcze utworzona jako hostowana strefa, wybierz pozycję **Utwórz** hostowaną strefę i wykonaj kroki przed przejściem do następnego kroku. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Manage DNS (Zarządzaj systemem DNS**).

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Domain name** (Nazwa domeny) wybierz nazwę domeny hostowanej wersji strefy domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz **pozycję Create record (Utwórz rekord**).

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Create record (Utwórz rekord).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    Z list **rozwijanych** wybierz wartości zasad **Typu** i Routing.

    |**Nazwa rekordu**|**Typ rekordu**|**Wartość**| **TTL (Czas wygaśnięcia)** |**Zasady routingu**|
    |:-----|:-----|:-----|:-----|:-----|
    |enterpriseregistration  <br/> |CNAME  Canonical name (CNAME  Nazwa kanoniczna)  <br/> |enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |300  <br/> |Simple (Proste)  <br/> |
    |enterpriseenrollment  <br/> |CNAME  Canonical name (CNAME  Nazwa kanoniczna)  <br/> | enterpriseenrollment-s.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/>|300  <br/> | |Simple (Proste)  <br/> |
  
1. Aby dodać drugi rekord CNAME, wybierz pozycję **Add another record** (Dodaj kolejny rekord), utwórz rekord, używając wartości z następnego wiersza w tabeli. 

1. Wybierz **pozycję Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
