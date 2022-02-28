---
title: Połączenie rekordów DNS w witrynie Namecheap Microsoft 365
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
ms.assetid: 54ae2002-b38e-43a1-82fa-3e49d78fda56
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w witrynie Namecheap dla firmy Microsoft.
ms.openlocfilehash: 31938656e17104d1388b53c05b6ccf3af9afc30f
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2021
ms.locfileid: "62988695"
---
# <a name="connect-your-dns-records-at-namecheap-to-microsoft-365"></a>Połączenie rekordów DNS w witrynie Namecheap Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
Jeśli namecheap jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, dla usługi Skype dla firm Online itp.
  
Po dodaniu tych rekordów w czacie Namecheap Twoja domena będzie skonfigurować do współpracy z usługi firmy Microsoft.
  
> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziecie używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.
  
> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w czacie Namecheap, używając [tego linku](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Zostanie wyświetlony monit o zalogowanie się i kontynuowanie.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Zaloguj się do namecheap.":::

1. Na stronie docelowej w obszarze **Konto** wybierz z listy  rozwijanej pozycję Lista domen. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Z listy rozwijanej wybierz pozycję Domain List (Lista domen).":::

1. Na stronie Domain List (Lista domen) wybierz domenę, którą chcesz edytować, a następnie wybierz pozycję **Manage (Zarządzaj**).

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Wybierz pozycję Zarządzaj.":::

1. Wybierz **pozycję Advanced DNS (Zaawansowana usługa DNS**).

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Wybierz pozycję Advanced DNS (Zaawansowana usługa DNS).":::

1. W sekcji **HOST RECORDS (REKORDY HOSTÓW** ) wybierz pozycję **ADD NEW RECORD (DODAJ NOWY REKORD**).

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Wybierz pozycję ADD NEW RECORD (DODAJ NOWY REKORD).":::

1. Z listy **rozwijanej Type** (Typ) wybierz pozycję **TXT Record (Rekord TXT**).
    
    > [!NOTE]
    > Lista **rozwijana** Type (Typ) jest wyświetlana automatycznie po wybraniu opcji **ADD NEW RECORD (DODAJ NOWY REKORD**). 

     :::image type="content" source="../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png" alt-text="Wybierz pozycję TXT Record (Rekord TXT).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.
    
    Z listy **rozwijanej wybierz wartość TTL** (Czas wygaśnięcia). 
    
    |**Type (Typ)**|**Host**|**Wartość**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |MS=ms *XXXXXXXX*  <br/>**Uwaga:** To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli.  [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md) |30 min  <br/> |

     :::image type="content" source="../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png" alt-text="Skopiuj i wklej wartości z tabeli.":::

1. Zaznacz **kontrolkę Zapisz** zmiany (znacznik wyboru). 

     :::image type="content" source="../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png" alt-text="Zaznacz kontrolkę Save Changes (Zapisz zmiany).":::

1. Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.
    
Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz tego rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana. 

Aby zweryfikować rekord w Microsoft 365:
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.
    
1. Na stronie Domeny wybierz weryfikowaną domenę, a następnie wybierz pozycję **Rozpocznij konfigurowanie**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Wybierz **pozycję Kontynuuj**.
  
1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.
    
> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodawanie rekordu MX, aby poczta e-mail dla Twojej domeny trafiała do firmy Microsoft
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w czacie Namecheap, używając [tego linku](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Zostanie wyświetlony monit o zalogowanie się i kontynuowanie.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Zaloguj się do namecheap.":::

1. Na stronie docelowej w obszarze **Konto** wybierz z listy  rozwijanej pozycję Lista domen. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Z listy rozwijanej wybierz pozycję Domain List (Lista domen).":::

1. Na stronie **Domain List (Lista** domen) wybierz domenę, którą chcesz edytować, a następnie wybierz pozycję **Manage (Zarządzaj**).

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Wybierz pozycję Zarządzaj.":::

1. Wybierz **pozycję Advanced DNS (Zaawansowana usługa DNS**).

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Wybierz pozycję Advanced DNS (Zaawansowana usługa DNS).":::

1. W sekcji **MAIL SETTINGS (USTAWIENIA POCZTY** ) wybierz **pozycję Custom MX (Niestandardowy rekord MX** ) z listy rozwijanej **Email Forwarding** (Przesyłanie dalej poczty e-mail). 
    
    Może być konieczne przewinięcie strony w dół.

     :::image type="content" source="../../media/40199e2c-42cf-4c3f-9936-3cbe5d4e81a4.png" alt-text="Wybierz pozycję Custom MX (Niestandardowy rekord MX)."::: 

1. Wybierz **pozycję Add New Record (Dodaj nowy rekord**).

     :::image type="content" source="../../media/8d169b81-ba48-4d51-84ea-a08fa1616457.png" alt-text="DODAJ NOWY REKORD.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.
    
    (Pole **Priorytet** to pole bez nazwy po prawej stronie **pola Wartość** . Z **listy rozwijanej wybierz wartość TTL** (Czas wygaśnięcia). 
    
    |**Type (Typ)**|**Host**|**Wartość**|**Priority (Priorytet)**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|:-----|
    |Rekord MX  <br/> |@  <br/> |\<*domain-key*\>mail.protection.outlook.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> **Uwaga:** Pobierz ze  *\<domain-key\>*  swojego konta Microsoft.  [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)          |0  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) <br/> |30 min  <br/> |

     :::image type="content" source="../../media/f3b76d62-5022-48c1-901b-8615a8571309.png" alt-text="Skopiuj i wklej wartości z tabeli.":::

1. Zaznacz **kontrolkę Zapisz** zmiany (znacznik wyboru). 

     :::image type="content" source="../../media/ef4e3112-36d2-47c8-a478-136a565dd71d.png" alt-text="Zaznacz kontrolkę Save Changes (Zapisz zmiany).":::

1. Jeśli istnieją inne rekordy MX, usuń każdy z nich przy użyciu poniższej dwuetapowej procedury:
    
    Najpierw wybierz **pozycję Usuń** (kosz na śmieci) dla rekordu, który chcesz usunąć. 

     :::image type="content" source="../../media/7a7a751f-29c2-495f-8f55-98ca37ce555a.png" alt-text="Wybierz pozycję Usuń.":::

    Następnie wybierz pozycję **Tak,** aby potwierdzić usunięcie. 

     :::image type="content" source="../../media/85ebc0c7-8787-43ee-9e7b-647375b3345c.png" alt-text="Wybierz pozycję Tak.":::

    Usuń wszystkie rekordy MX z wyjątkiem tego dodanego wcześniej w tej procedurze.
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w czacie Namecheap, używając [tego linku](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Zostanie wyświetlony monit o zalogowanie się i kontynuowanie.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Zaloguj się do namecheap.":::

1. Na stronie docelowej w obszarze **Konto** wybierz z listy  rozwijanej pozycję Lista domen. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Wybierz pozycję Domain List (Lista domen).":::

1. Na stronie **Domain List (Lista** domen) wybierz domenę, którą chcesz edytować, a następnie wybierz pozycję **Manage (Zarządzaj**).

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Wybierz pozycję Zarządzaj.":::

1. Wybierz **pozycję Advanced DNS (Zaawansowana usługa DNS**).

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Wybierz pozycję Advanced DNS (Zaawansowana usługa DNS).":::

1. W sekcji **HOST RECORDS (REKORDY HOSTÓW** ) wybierz pozycję **ADD NEW RECORD (DODAJ NOWY REKORD**).

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Wybierz pozycję ADD NEW RECORD (DODAJ NOWY REKORD).":::

1. Z listy **rozwijanej Type** (Typ) wybierz pozycję **CNAME Record (Rekord CNAME**).
    
    > [!NOTE]
    > Lista **rozwijana** Type (Typ) jest wyświetlana automatycznie po wybraniu opcji **ADD NEW RECORD (DODAJ NOWY REKORD**). 

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Wybierz pozycję CNAME Record (Rekord CNAME).":::

1. W pustych polach nowego rekordu wybierz pozycję **CNAME** dla ustawienia **Record Type** (Typ rekordu), a następnie wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli.
    
    |**Type (Typ)**|**Host**|**Wartość**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover  <br/> |autodiscover.outlook.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |Automatyczne  <br/> |

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Skopiuj i wklej wartości z tabeli.":::

1. Zaznacz **kontrolkę Zapisz** zmiany (znacznik wyboru). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Zaznacz kontrolkę Save Changes (Zapisz zmiany).":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy *rekord SPF,*  który zawiera oba zestawy wartości. 

1. Aby rozpocząć pracę, przejdź do swojej strony domen w czacie Namecheap, używając [tego linku](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Zostanie wyświetlony monit o zalogowanie się i kontynuowanie.
    
1. Na stronie docelowej w obszarze **Konto** wybierz z listy  rozwijanej pozycję Lista domen. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Wybierz pozycję Domain List (Lista domen).":::

1. Na stronie **Domain List (Lista** domen) wybierz domenę, którą chcesz edytować, a następnie wybierz pozycję **Manage (Zarządzaj**).

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Wybierz pozycję Zarządzaj.":::

1. Wybierz **pozycję Advanced DNS (Zaawansowana usługa DNS**).

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Wybierz pozycję Advanced DNS (Zaawansowana usługa DNS).":::

1. W sekcji **HOST RECORDS (REKORDY HOSTÓW** ) wybierz pozycję **ADD NEW RECORD (DODAJ NOWY REKORD**).

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Wybierz pozycję ADD NEW RECORD (DODAJ NOWY REKORD).":::

1. Z listy **rozwijanej Type** (Typ) wybierz pozycję **TXT Record (Rekord TXT**).
    
    > [!NOTE]
    > Lista **rozwijana** Type (Typ) jest wyświetlana automatycznie po wybraniu opcji **ADD NEW RECORD (DODAJ NOWY REKORD**). 

     :::image type="content" source="../../media/c5d1fddb-28b5-48ec-91c9-3e5d3955ac80.png" alt-text="Wybierz pozycję TXT Record (Rekord TXT).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej następujące wartości z poniższej tabeli.
    
    Z listy **rozwijanej wybierz wartość TTL** (Czas wygaśnięcia). 
    
    |**Type (Typ)**|**Host**|**Wartość**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne. |30 min  <br/> |

     :::image type="content" source="../../media/ea0829f1-990b-424b-b26e-9859468318dd.png" alt-text="Skopiuj i wklej wartości z tabeli.":::

1. Zaznacz **kontrolkę Zapisz** zmiany (znacznik wyboru). 

     :::image type="content" source="../../media/f2846c36-ace3-43d8-be5d-a65e2c267619.png" alt-text="Zaznacz kontrolkę Save Changes (Zapisz zmiany).":::

## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype 4 rekordy: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME do zalogowania się i połączenia użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć pracę, przejdź do swojej strony domen w czacie Namecheap, używając [tego linku](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Zostanie wyświetlony monit o zalogowanie się.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Zaloguj się do namecheap.":::

1. Na stronie docelowej w obszarze **Konto** wybierz z listy  rozwijanej pozycję Lista domen. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Wybierz pozycję Domain List (Lista domen).":::

1. Na stronie **Domain List (Lista** domen) wybierz domenę, którą chcesz edytować, a następnie wybierz pozycję **Manage (Zarządzaj**).

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Wybierz pozycję Zarządzaj.":::

1. Wybierz **pozycję Advanced DNS (Zaawansowana usługa DNS**).

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Wybierz pozycję Advanced DNS (Zaawansowana usługa DNS).":::

1. W sekcji **HOST RECORDS (REKORDY HOSTÓW** ) wybierz pozycję **ADD NEW RECORD (DODAJ NOWY REKORD**).

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Wybierz pozycję ADD NEW RECORD (DODAJ NOWY REKORD).":::

1. Z listy **rozwijanej Type** (Typ) wybierz pozycję **SRV Record (Rekord SRV**).
    
    > [!NOTE]
    > Lista **rozwijana** Type (Typ) jest wyświetlana automatycznie po wybraniu opcji **ADD NEW RECORD (DODAJ NOWY REKORD**). 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Wybierz typ rekordu SRV.":::

1. W pustych polach nowych rekordów wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli.
    
    |**Service (Usługa)**|**Protocol (Protokół)**|**Priority (Priorytet)**|**Weight (Waga)**|**Port**|**Target (Element docelowy)**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |100  <br/> |1  <br/> |443  <br/> |sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |Automatyczne  <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |100  <br/> |1  <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |Automatyczne  <br/> |
       
     :::image type="content" source="../../media/ff9566ea-0096-4b7f-873c-027080a23b56.png" alt-text="Skopiuj i wklej wartości z tabeli.":::

1. Zaznacz **kontrolkę Zapisz** zmiany (znacznik wyboru). 

     :::image type="content" source="../../media/48a8dee4-c66d-449d-8759-9e9784c82b13.png" alt-text="Zaznacz kontrolkę Save Changes (Zapisz zmiany).":::

1. Dodaj drugi rekord SRV, wybierając wartości z drugiego wiersza tabeli.
    
> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME 
  
1. W sekcji **HOST RECORDS (REKORDY HOSTÓW** ) wybierz pozycję **ADD NEW RECORD (DODAJ NOWY REKORD**).
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Wybierz pozycję DODAJ NOWĄ NAZWĘ.":::

1. Z listy **rozwijanej Type** (Typ) wybierz pozycję **CNAME**.
    
    > [!NOTE]
    > Lista **rozwijana** Type (Typ) jest wyświetlana automatycznie po wybraniu opcji **ADD NEW RECORD (DODAJ NOWY REKORD**). 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Wybierz pozycję CNAME.":::

1. W pustych polach nowych rekordów wpisz lub skopiuj i wklej wartości z pierwszego wiersza w tabeli.
    
    |**Type (Typ)**|**Host**|**Wartość**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |Automatyczne  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |Automatyczne  <br/> |

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Skopiuj i wklej wartości CNAME z tabeli.":::

1. Zaznacz **kontrolkę Zapisz** zmiany (znacznik wyboru). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Zaznacz kontrolkę Save Changes (Zapisz zmiany).":::

1. Dodaj drugi rekord CNAME, wybierając wartości z drugiego wiersza tabeli.
    
> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: Intune i Zarządzanie urządzeniami przenośnymi dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Zarządzanie urządzeniami przenośnymi wymaga dwóch rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Aby rozpocząć pracę, przejdź do swojej strony domen w czacie Namecheap, używając [tego linku](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Zostanie wyświetlony monit o zalogowanie się.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Zaloguj się do namecheap.":::

1. Na stronie docelowej w obszarze **Konto** wybierz z listy  rozwijanej pozycję Lista domen. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Wybierz pozycję Domain List (Lista domen).":::

1. Na stronie **Domain List (Lista** domen) wybierz domenę, którą chcesz edytować, a następnie wybierz pozycję **Manage (Zarządzaj**).
    
     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Wybierz pozycję Zarządzaj.":::

1. Wybierz **pozycję Advanced DNS (Zaawansowana usługa DNS**).

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS Records (Zarządzaj rekordami DNS).":::

1. W sekcji **HOST RECORDS (REKORDY HOSTÓW** ) wybierz pozycję **ADD NEW RECORD (DODAJ NOWY REKORD**).
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Wybierz pozycję ADD NEW RECORD (DODAJ NOWY REKORD).":::

1. Z listy **rozwijanej Type** (Typ) wybierz pozycję **CNAME Record (Rekord CNAME**).
    
    > [!NOTE]
    > Lista **rozwijana** Type (Typ) jest wyświetlana automatycznie po wybraniu opcji **ADD NEW RECORD (DODAJ NOWY REKORD**). 
  
     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Wybierz pozycję CNAME Record (Rekord CNAME).":::

1. W pustych polach nowych rekordów wpisz lub skopiuj i wklej wartości z pierwszego wiersza w tabeli.
    
    |**Type (Typ)**|**Host**|**Wartość**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |Automatyczne  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |Automatyczne  <br/> |
       
     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Skopiuj i wklej wartości z tabeli.":::

1. Zaznacz **kontrolkę Save Changes (Zapisz** zmiany). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Zaznacz kontrolkę Save Changes (Zapisz zmiany).":::

1. Dodaj drugi rekord CNAME, wybierając wartości z drugiego wiersza tabeli.
    
> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 


