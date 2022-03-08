---
title: Połączenie rekordów DNS w witrynie IONOS o 1&1 do Microsoft 365
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w witrynie 1&1 IONOS dla firmy Microsoft.
ms.openlocfilehash: 54e18972fe2d5e2ccd8c3ab266b20241e67f68a9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313611"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>Połączenie rekordów DNS w witrynie IONOS o 1&1 do Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 

Jeśli obiekt IONOS by 1&1 jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online itp.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Dostępne są dwie opcje konfigurowania rekordów DNS dla domeny:

- [**Używanie usługi Domain Połączenie**](#use-domain-connect-to-verify-and-set-up-your-domain) Jeśli domena nie jest jeszcze ustawiona na inną usługę poczty e-mail usługodawca, skorzystaj z procedury Domain Połączenie (Domena Połączenie), aby automatycznie zweryfikować i skonfigurować nową domenę do używania z usługą Microsoft 365. 

    LUB

- [**Ręczne kroki**](#create-dns-records-with-manual-setup) Zweryfikuj domenę, korzystając z ręcznej procedury poniżej, i wybierz, kiedy i które rekordy dodać do rejestratora domen. Umożliwia to skonfigurowanie nowych rekordów MX (poczty), na przykład w dogodnym dla Ciebie momencie. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Weryfikowanie i konfigurowanie Połączenie przy użyciu usługi Domain Połączenie

Wykonaj poniższe czynności, aby automatycznie zweryfikować i skonfigurować domenę IONOS według 1&1 u rejestratora Microsoft 365:

1. W centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>, a następnie wybierz domenę, którą chcesz skonfigurować.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="Wybierz domenę w Microsoft 365.":::

1. Wybierz przycisk z trzema kropkami (więcej akcji), > pozycję **Rozpocznij konfigurowanie**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Na stronie Jak chcesz połączyć domenę? wybierz pozycję **Kontynuuj**.   

1. Na stronie Dodawanie rekordów DNS wybierz pozycję **Dodaj rekordy DNS**.

1. Na stronie logowania IONOS&1 zaloguj się do swojego konta, a następnie **Połączenie pozycję** **Zezwalaj**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="Wybierz Połączenie, a następnie pozycję Zezwalaj.":::

    Ukończy to konfigurację domeny dla Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>Tworzenie rekordów DNS przy użyciu konfiguracji ręcznej

Po dodaniu tych rekordów w u rejestratorze IONOS&1 Twoja domena będzie skonfigurować do współpracy z usługi firmy Microsoft.
  
> [!CAUTION]
> Pamiętaj, że funkcja IONOS&1 nie pozwala, aby domena miała zarówno rekord MX, jak i rekord CNAME Wykrywania automatycznego najwyższego poziomu. Ogranicza to sposoby konfigurowania usługi dla Exchange Online Microsoft. Istnieje obejście, ale zalecamy jego stosowanie tylko wtedy,  gdy masz już doświadczenie w tworzeniu poddomen w omówień IONOS do 1&1.
> Jeśli mimo tego [](../setup/domains-faq.yml) ograniczenia usług zdecydujesz się zarządzać swoimi rekordami DNS firmy Microsoft w usłudze IONOS do 1&1, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online itp.
  
> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
  
### <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziecie używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.
  
> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w menu IONOS do 1&1, używając [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Menu**, a następnie wybierz **pozycję Domeny i SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i SSL.":::
  
1. W **obszarze** Akcje dla domeny, którą chcesz zaktualizować wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję DNS.":::

1. Wybierz **pozycję Add record (Dodaj rekord**).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Wybierz **sekcję TXT** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="Wybierz sekcję TXT.":::

1. Na stronie Add a DNS record (Dodawanie rekordu DNS) w polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    |**Nazwa hosta** <br/> |**Wartość** <br/> | **TTL (Czas wygaśnięcia)**
    |:-----|:-----|:-----|
    |(Pozostaw to pole puste)  <br/> |MS=ms *XXXXXXXX*  <br/> UWAGA: To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)          | 1 godzina |

1. Wybierz **Zapisz**.
  
    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="Wybierz pozycję Zapisz.":::
  
    Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do usługi Microsoft 365 i zażądasz, aby Microsoft 365 go szukać. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w Microsoft 365:
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.

1. Na stronie Domeny wybierz weryfikowaną domenę, a następnie wybierz pozycję **Rozpocznij konfigurowanie**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Wybierz **pozycję Kontynuuj**.
  
1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
  
### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodawanie rekordu MX, aby poczta e-mail dla Twojej domeny trafiała do firmy Microsoft
  
> [!NOTE]
> Jeśli rejestracja zarejestrowałeś się w 1und1.de, [zaloguj się tutaj](https://go.microsoft.com/fwlink/?linkid=859152). 

1. Aby rozpocząć pracę, przejdź do swojej strony domen w menu IONOS do 1&1, używając [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Menu**, a następnie wybierz **pozycję Domeny i SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i SSL.":::
  
1. W **obszarze** Akcje dla domeny, którą chcesz zaktualizować wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję DNS.":::

1. Wybierz **pozycję Add record (Dodaj rekord**).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Wybierz **sekcję MX** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="Wybierz sekcję MX.":::
  
1. Na stronie Add a DNS record (Dodawanie rekordu DNS) w polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    | **Nazwa hosta**| **Wskazuje** |**Priority (Priorytet)**| **TTL (Czas wygaśnięcia)** |
    |:-----|:-----|:-----| :-----|
    |  @  | *\<domain-key\>*  mail.protection.outlook.com  <br/>  UWAGA: Pobierz ze \<domain-key\> swojego konta Microsoft. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) | 1 godzina |
  
1. Wybierz **Zapisz**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Jeśli na liście znajdują się już rekordy MX, usuń je, wybierając kosz **Delete record** (Usuń rekord) na **stronie Add record (Dodaj rekord** ).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="Wybierz pozycję Delete record (Usuń rekord).":::

### <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

> [!NOTE]
> Jeśli rejestracja zarejestrowałeś się w 1und1.de, [zaloguj się tutaj](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w menu IONOS do 1&1, używając [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Menu**, a następnie wybierz **pozycję Domeny i SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i SSL.":::
  
1. W **obszarze** Akcje dla domeny, którą chcesz zaktualizować wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję DNS.":::

    Teraz utworzysz dwie poddomeny i ustawisz wartość **lias** dla każdej z nich.<br/>(Jest to wymagane, ponieważ 1&1 IONOS obsługuje tylko jeden rekord CNAME najwyższego poziomu, ale firma Microsoft wymaga kilku rekordów CNAME.<br/>Najpierw utworzysz poddomenę Autodiscover.

1. Wybierz **pozycję Poddomeny**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Wybierz pozycję Subdomain (Poddomena).":::
  
1. Wybierz **pozycję Add subdomain (Dodaj poddomenę**).

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Wybierz pozycję Dodaj poddomeny.":::
  
1. W **polu Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość Dodaj **poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |**Dodaj poddomenę**| **Alias** |
    |:-----|:-----|
    |autodiscover  <br/> | autodiscover.outlook.com |

1. W **obszarze** Akcje dla **poddomeny** wykrywania automatycznego, która właśnie została utworzona, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej. <br/>

1. Wybierz **pozycję Add record (Dodaj** rekord), a następnie wybierz **sekcję CNAME** .

1. W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli. <br/>

    |**Dodaj poddomenę**| **Alias** |
    |:-----|:-----|
    |autodiscover  <br/> | autodiscover.outlook.com |
  
1. Wybierz **Zapisz**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy  *rekord SPF,*  który zawiera oba zestawy wartości. Potrzebujesz przykładów? Zapoznaj się z tymi [rekordami systemu nazw domen zewnętrznych dla firmy Microsoft](../../enterprise/external-domain-name-system-records.md). Do zweryfikowania rekordu SPF możesz użyć jednego z narzędzi do sprawdzania poprawności [platformy](../setup/domains-faq.yml) SPF. 
  
> [!NOTE]
> Jeśli rejestracja zarejestrowałeś się w 1und1.de, [zaloguj się tutaj](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w menu IONOS do 1&1, używając [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Menu**, a następnie wybierz **pozycję Domeny i SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i SSL.":::
  
1. W **obszarze** Akcje dla domeny, którą chcesz zaktualizować wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję DNS.":::

1. Wybierz **pozycję Add record (Dodaj rekord**).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Wybierz **sekcję SPF (TXT** ).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="Wybierz sekcję SPF (TXT).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. <br/>

    |**Type**|**Nazwa hosta**|**Wartość**| **TTL (Czas wygaśnięcia)** |
    |:-----|:-----|:-----|:-----|
    |SPF (TXT) (REKORD SPF (TXT)  <br/> |Pozostaw to pole puste.  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne. | 1 godzina |
  
1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="Wybierz pozycję Zapisz.":::

## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype 4 rekordy: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME do zalogowania się i połączenia użytkowników z usługą.

### <a name="add-two-additional-cname-records"></a>Dodawanie dwóch dodatkowych rekordów CNAME
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w menu IONOS do 1&1, używając [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Menu**, a następnie wybierz **pozycję Domeny i SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i SSL.":::
  
1. W **obszarze** Akcje dla domeny, którą chcesz zaktualizować wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję DNS.":::

    Teraz utworzysz dwie poddomeny i ustawisz wartość **lias** dla każdej z nich.<br/>(Jest to wymagane, ponieważ 1&1 IONOS obsługuje tylko jeden rekord CNAME najwyższego poziomu, ale firma Microsoft wymaga kilku rekordów CNAME.<br/>Najpierw utworzysz poddomenę lyncdiscover.

1. Wybierz **pozycję Poddomeny**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Wybierz pozycję Subdomain (Poddomena).":::
  
1. Wybierz **pozycję Add subdomain (Dodaj poddomenę**).

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Wybierz pozycję Dodaj poddomeny.":::

1. W **polu Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość Dodaj **poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).<br/> 

    |**Dodaj poddomenę**|**Alias**|
    |:-----|:-----|
    |lyncdiscover   |webdir.online.lync.com  |

1. W **obszarze** Akcje dla **poddomeny lyncdiscover** , która właśnie została utworzona, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej. <br/>

1. Wybierz **pozycję Add record (Dodaj** rekord), a następnie wybierz **sekcję CNAME** .

1. W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli. <br/>

    |**Create Subdomain (Utwórz poddomenę)**|**Alias**|
    |:-----|:-----|
    |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |

1. Utwórz inną poddomenę (SIP): <br/>Wybierz **pozycję Add subdomain (Dodaj poddomenę**).

1. W **polu Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość Dodaj **poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku). <br/>

    |**Dodaj poddomenę**|**Alias**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. W **obszarze** Akcje dla właśnie utworzonej poddomeny wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej. <br/>

1. Wybierz **pozycję Add record (Dodaj rekord**).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Wybierz **sekcję CNAME** .

1. w **polu Alias wpisz** lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli. 

    |**Create Subdomain (Utwórz poddomenę)**|**Alias**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. Zaznacz pole wyboru dla zastrzeżenia **I am aware (Rozumiem** ), a następnie wybierz pozycję **Save (Zapisz**).

## <a name="add-the-two-srv-records-required-for-microsoft"></a>Dodawanie dwóch rekordów SRV wymaganych dla firmy Microsoft
  
> [!NOTE]
> Jeśli rejestracja zarejestrowałeś się w 1und1.de, [zaloguj się tutaj](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w menu IONOS do 1&1, używając [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Menu**, a następnie wybierz **pozycję Domeny i SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i SSL.":::
  
1. W **obszarze** Akcje dla domeny, którą chcesz zaktualizować wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję DNS.":::

1. Wybierz **pozycję Add record (Dodaj rekord**).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Zaznacz **sekcję SRV** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="Zaznacz sekcję SRV.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. <br/>

    |**Type (Typ)**|**Service (Usługa)**|**Protocol (Protokół)**|**Nazwa hosta**|**Wskazuje**|**Priority (Priorytet)**|**Weight (Waga)**|**Port**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV  <br/> |_sip  <br/> |tls  <br/> |Pozostaw to pole puste.  <br/> |sipdir.online.lync.com  <br/> |100  <br/> |1  <br/> |443  <br/> |1 godzina  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |tcp  <br/> |Pozostaw to pole puste.  <br/> |sipfed.online.lync.com  <br/> |100  <br/> |1  <br/> |5061  <br/> |1 godzina <br/> |  
  
1. Wybierz **Zapisz**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj drugi rekord SRV.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: Intune i Zarządzanie urządzeniami przenośnymi dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Zarządzanie urządzeniami przenośnymi wymaga 2 rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

> [!IMPORTANT]
> Postępuj zgodnie z procedurą poddomeny uchwytną dla innych rekordów CNAME i podaj wartości z poniższej tabeli. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w menu IONOS do 1&1, używając [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Menu**, a następnie wybierz **pozycję Domeny i SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i SSL.":::
  
1. W **obszarze** Akcje dla domeny, którą chcesz zaktualizować wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Z listy rozwijanej wybierz pozycję DNS.":::

    Teraz utworzysz dwie poddomeny i ustawisz wartość **lias** dla każdej z nich.<br/>(Jest to wymagane, ponieważ 1&1 IONOS obsługuje tylko jeden rekord CNAME najwyższego poziomu, ale firma Microsoft wymaga kilku rekordów CNAME.<br/>Najpierw utworzysz poddomenę lyncdiscover.

1. Wybierz **pozycję Poddomeny**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Wybierz pozycję Subdomain (Poddomena).":::
  
1. Wybierz **pozycję Add subdomain (Dodaj poddomenę**).

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Wybierz pozycję Dodaj poddomeny.":::

1. W **polu Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość Dodaj **poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).<br/> 

    |**Dodaj poddomenę**|**Alias**|
    |:-----|:-----|
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |

1. W **obszarze** Akcje dla **poddomeny enterpriseregistration** , która właśnie została utworzona, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej. <br/>

1. Wybierz **pozycję Add record (Dodaj** rekord), a następnie wybierz **sekcję CNAME** .

1. W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli. <br/>

    |**Dodaj poddomenę**|**Alias**|
    |:-----|:-----|
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |

1. Utwórz inną poddomenę: <br/>Wybierz **pozycję Add subdomain (Dodaj poddomenę**).

1. W **polu Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość Dodaj **poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku). <br/>

    |**Dodaj poddomenę**|**Alias**|
    |:-----|:-----|
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

1. W **obszarze** Akcje dla **poddomeny enterpriseenrollment** , która właśnie została utworzona, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej. <br/>

1. Wybierz **pozycję Add record (Dodaj rekord**).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

1. Wybierz **sekcję CNAME** .

1. w **polu Alias wpisz** lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli. 

    |**Create Subdomain (Utwórz poddomenę)**|**Alias**|
    |:-----|:-----|
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

1. Zaznacz pole wyboru dla zastrzeżenia **I am aware (Rozumiem** ), a następnie wybierz pozycję **Save (Zapisz**).