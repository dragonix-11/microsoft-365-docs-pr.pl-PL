---
title: Połączenie rekordów DNS w witrynie Cloudflare to Microsoft 365
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
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w witrynie Cloudflare firmy Microsoft.
ms.openlocfilehash: 5cf6483c7f560f5ab3ed2074dbaebf6c893dca3e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314927"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>Połączenie rekordów DNS w witrynie Cloudflare to Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 

Jeśli Cloudflare jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online itp.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Dostępne są dwie opcje konfigurowania rekordów DNS dla domeny:

- [**Używanie usługi Domain Połączenie**](#use-domain-connect-to-verify-and-set-up-your-domain) Jeśli domena nie jest jeszcze ustawiona na inną usługę poczty e-mail usługodawca, skorzystaj z procedury Domain Połączenie (Domena Połączenie), aby automatycznie zweryfikować i skonfigurować nową domenę do używania z usługą Microsoft 365. 

    LUB

- [**Ręczne kroki**](#create-dns-records-with-manual-setup) Zweryfikuj domenę, korzystając z ręcznej procedury poniżej, i wybierz, kiedy i które rekordy dodać do rejestratora domen. Umożliwia to skonfigurowanie nowych rekordów MX (poczty), na przykład w dogodnym dla Ciebie momencie. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Weryfikowanie i konfigurowanie Połączenie przy użyciu usługi Domain Połączenie

Wykonaj poniższe czynności, aby automatycznie zweryfikować i skonfigurować domenę Cloudflare u Microsoft 365:

1. W centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>, a następnie wybierz domenę, którą chcesz skonfigurować.

1. Wybierz przycisk z trzema kropkami (więcej akcji), > pozycję **Rozpocznij konfigurowanie**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Na stronie Jak chcesz połączyć domenę? wybierz pozycję **Kontynuuj**.

1. Na stronie Dodawanie rekordów DNS wybierz pozycję **Dodaj rekordy DNS**.

1. Na stronie logowania Cloudflare zaloguj się do swojego konta i wybierz pozycję **Autoryzuj**.

    Ukończy to konfigurację domeny dla Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>Tworzenie rekordów DNS przy użyciu konfiguracji ręcznej

Po dodaniu tych rekordów w chmurze Cloudflare Twoja domena będzie skonfigurować do współpracy z Microsoft 365 usługami.

> [!NOTE]
>  Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
### <a name="change-your-domains-nameserver-ns-records"></a>Zmienianie rekordów serwerów nazw domeny (SN)

> [!IMPORTANT]
> Tę procedurę należy wykonać w witrynie rejestratora domen, u którego kupiono i zarejestrowano domenę. 
  
Po rejestracji w usłudze Cloudflare dodano domenę przy użyciu procesu konfiguracji Cloudflare. 
  
Dodana domena została zakupiona u Cloudflare lub u oddzielnego rejestratora domen. Aby zweryfikować i utworzyć rekordy DNS dla twojej domeny w usłudze Microsoft 365, musisz najpierw zmienić serwery nazw u rejestratora domen, aby używały serwerów nazw Cloudflare.
  
Aby samodzielnie zmienić serwery nazw domen w witrynie sieci Web rejestratora domen, wykonaj poniższe czynności.
  
1. Znajdź obszar w witrynie sieci Web rejestratora domen, w którym można edytować serwery nazw dla Twojej domeny.

2. Utwórz dwa rekordy serwera nazw, używając wartości z poniższej tabeli, lub edytuj istniejące rekordy serwera nazw tak, aby były zgodne z tymi wartościami.

    ||
    |:-----|:-----|
    |Pierwszy serwer nazw  <br/> |Użyj wartości serwera nazw udostępnianej przez Cloudflare.  <br/> |
    |Drugi serwer nazw  <br/> |Użyj wartości serwera nazw udostępnianej przez Cloudflare.  <br/> |

    > [!TIP]
    > Należy użyć co najmniej dwóch rekordów serwera nazw. Jeśli na liście znajdują się jakiekolwiek inne serwery nazw, należy je usunąć. 
  
3. Zapisz zmiany.

> [!NOTE]
> Aktualizowanie rekordu serwera nazw w internetowym systemie DNS może potrwać nawet kilka godzin. Wtedy poczta e-mail Firmy Microsoft i inne usługi będą ustawione do współpracy z Twoją domeną. 
  
### <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziecie używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.
  
> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w chmurze Cloudflare, używając [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.
  
1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Omówienie domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::
  
1. Na stronie zarządzania systemem DNS wybierz pozycję **+Dodaj rekord**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Wybierz z listy rozwijanej typ TXT, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli. 

    | **Type** | **Name (Nazwa)** | **TTL (Czas wygaśnięcia)** | **Zawartość** |
    |:-----|:-----|:-----|:----|
    |TXT  <br/> |@  <br/> |30 minut  <br/> |MS=ms *XXXXXXXX*  <br/> **Uwaga:** To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)    |

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i wyszukasz ten rekord. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.
  
Aby zweryfikować rekord w Microsoft 365:
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.

1. Na stronie Domeny wybierz weryfikowaną domenę, a następnie wybierz pozycję **Rozpocznij konfigurowanie**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Wybierz **pozycję Kontynuuj**.
  
1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodawanie rekordu MX, aby poczta e-mail dla Twojej domeny trafiała do firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w chmurze Cloudflare, używając [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.
  
1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Omówienie domeny wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania systemem DNS wybierz pozycję **+Dodaj rekord**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Wybierz z listy rozwijanej typ rekordu MX, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli. 

   | **Type** | **Nazwa** | **Mail server (Serwer poczty)** |  **TTL (Czas wygaśnięcia)** | **Priority (Priorytet)** |
   |:-----|:-----|:-----|:-----|:-----|
   |MX  <br/> |@  <br/> |*\<domain-key\>*  mail.protection.outlook.com  <br/> **Uwaga:** Pobierz ze *\<domain-key\>* swojego Microsoft 365 konta.   [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md) |30 minut  <br/> | 1  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) <br/>|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="Wybierz pozycję Add record (Dodaj rekord)."::: 

1. Jeśli na liście w sekcji MX Records (Rekordy MX) znajdują się jakiekolwiek inne rekordy **MX** , usuń je, wybierając pozycję **Edit** (Edytuj), a następnie wybierz pozycję **Delete (Usuń**). 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="Wybierz pozycję Usuń.":::  

1. W oknie dialogowym potwierdzenia wybierz pozycję **Usuń** , aby potwierdzić zmiany. 

### <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w chmurze Cloudflare, używając [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Omówienie domeny wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie **zarządzania systemem DNS** wybierz pozycję **+Dodaj rekord**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Z listy rozwijanej wybierz typ CNAME, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli. 

    | Wpisać | Name (Nazwa) | Target (Element docelowy) | Czas wygaśnięcia |
    |:-----|:-----|:-----|:-----|
    | CNAME  <br/> | autodiscover  <br/> | autodiscover.outlook.com  <br/> | Automatycznie <br/> |
  
1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz."::: 

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla Microsoft 365. Zamiast tego dodaj wymagane Microsoft 365 do bieżącego rekordu, aby mieć pojedynczy *rekord SPF,* który zawiera oba zestawy wartości. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w chmurze Cloudflare, używając [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.  
  
1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Omówienie domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania systemem DNS wybierz pozycję **+Dodaj rekord**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Wybierz z listy rozwijanej typ TXT, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli. 

    | Wpisać | Name (Nazwa) | Czas wygaśnięcia | Zawartość |
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |30 minut  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.   |

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Wybierz pozycję Zapisz."::: 

## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype 4 rekordy: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME do zalogowania się i połączenia użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

> [!IMPORTANT]
> Pamiętaj, że za dostęp do tej funkcji odpowiada Cloudflare. W przypadku rozbieżności między czynnościami poniżej a bieżącym interfejsem użytkownika Cloudflare (Graphical User Interface) skorzystaj z interfejsu użytkownika [Cloudflare Community](https://community.cloudflare.com/). 

1. Aby rozpocząć pracę, przejdź do swojej strony domen w chmurze Cloudflare, używając [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::
  
1. Na stronie Omówienie domeny wybierz pozycję **DNS**.
  
    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania systemem DNS wybierz pozycję **+Dodaj rekord**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Z listy rozwijanej wybierz typ SRV, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    | **Type** | **Nazwa** | **Service (Usługa)** | **Protocol (Protokół)** |  **TTL (Czas wygaśnięcia)** | **Priority (Priorytet)** | **Weight (Waga)** | **Port** | **Target (Element docelowy)** |
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV| Użyj swojego *domain_name*; na przykład: contoso.com | _sip |TLS |30 minut | 100|1 |443 |sipfed.online.lync.com  |
    |SRV|_sipfederationtls | TCP|Użyj swojego *domain_name*; na przykład: contoso.com   |30 minut |100 |1 |5061 | sipfed.online.lync.com |
  
1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="Wybierz pozycję Zapisz."::: 

1. Dodaj drugi rekord SRV, kopiując wartości z drugiego wiersza tabeli. 

> [!NOTE]
>  Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w chmurze Cloudflare, używając [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Omówienie domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania systemem DNS wybierz pozycję **+Dodaj rekord**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Z listy rozwijanej wybierz typ CNAME, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    |**Type**|**Nazwa**|**Target (Element docelowy)**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
  
1. Wybierz pozycję **Zapisz**. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::  

1. Dodaj drugi rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: Intune i Zarządzanie urządzeniami przenośnymi dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Zarządzanie urządzeniami przenośnymi wymaga 2 rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Aby rozpocząć pracę, przejdź do swojej strony domen w chmurze Cloudflare, używając [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Omówienie domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania systemem DNS wybierz pozycję **+Dodaj rekord**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Z listy rozwijanej wybierz typ CNAME, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    |**Type**|**Nazwa**|**Target (Element docelowy)**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
  
1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz."::: 

1. Dodaj drugi rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).