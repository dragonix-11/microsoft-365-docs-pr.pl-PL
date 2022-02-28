---
title: Tworzenie rekordów DNS dla firmy Microsoft przy Windows DNS
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9eec911d-5773-422c-9593-40e1147ffbde
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w witrynie Windows DNS dla firmy Microsoft.
ms.openlocfilehash: 43cc3679f33a929545ed3d9deec388126aec853c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983802"
---
# <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Tworzenie rekordów DNS dla firmy Microsoft przy Windows DNS

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
   
Jeśli samodzielnie hostujesz własne rekordy DNS za pomocą usługi DNS opartej na systemie Windows, wykonaj czynności opisane w tym artykule, aby skonfigurować rekordy dla poczty e-mail, usługi Skype dla firm Online i tak dalej.
  
Aby rozpocząć, musisz znaleźć rekordy [DNS w opartym Windows DNS](#find-your-dns-records-in-windows-based-dns), aby można je było zaktualizować. Ponadto, jeśli planujesz zsynchronizować lokalną usługę Active Directory z firmą Microsoft, zobacz Nie [routowalny adres e-mail używany jako upn](#non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory) w lokalnej usłudze Active Directory.
  
Problemy z przepływem poczty e-mail lub inne problemy po dodaniu rekordów DNS, zobacz Rozwiązywanie problemów po zmianie [nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="find-your-dns-records-in-windows-based-dns"></a>Znajdowanie rekordów DNS w systemie DNS bazującym na systemie Windows
<a name="BKMK_find_your_dns_1"> </a> Przejdź do strony, która zawiera rekordy DNS dla Twojej domeny. Jeśli pracujesz w programie Windows Server 2008, **przejdź do** **startrun** > . Jeśli pracujesz w programie Windows Server 2012, naciśnij klawisz Windows i **klawisz r**. Wpisz **dnsmgmnt.msc**, a następnie wybierz przycisk **OK**. W Menedżerze DNS **rozwiń obszar\<DNS server name\>\> Strefy odnośników.** Wybierz domenę. Możesz teraz przystąpić do tworzenia rekordów DNS.
   
## <a name="add-mx-record"></a>Dodawanie rekordu MX
<a name="BKMK_add_MX"> </a>

Dodaj rekord MX, aby poczta e-mail dla Twojej domeny trafiała do firmy Microsoft.
- Rekord MX, który dodasz, zawiera wartość ( **Points to address** value) wygląda następująco: \<MX token\>mail.protection.outlook.com, \<MX token\> gdzie jest wartością, taką jak MSxxxxxxx. 
- Z wiersza MX w sekcji Exchange Online strony Dodawanie rekordów DNS w firmie Microsoft skopiuj wartość wymienioną w obszarze Points to address (Wskazuje adres). Użyjesz tej wartości w rekordzie tworzonym w tym zadaniu. 
- Na stronie Menedżer DNS dla tej domeny przejdź do **actionMail** >  **Exchanger (MX) (Exchanger— usługa wymiany poczty dns).** Aby znaleźć tę stronę dla domeny, zobacz [Znajdowanie rekordów DNS w Windows DNS](#find-your-dns-records-in-windows-based-dns).  
- Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości: 
    - Nazwa hosta: 
    - @Address: Wklej w tym miejscu wartość pola Points to address (Punkty na adres), która właśnie skopiowała się od firmy Microsoft.  
    - Wstępne: 
- Wybierz opcję **Zapisz zmiany**.
- Usuwanie wszystkich przestarzałych rekordów MX. Jeśli masz jakiekolwiek stare rekordy MX dla tej domeny, które rozsyłają wiadomości e-mail gdzie indziej, zaznacz pole wyboru obok każdego starego rekordu, a następnie wybierz pozycję **DeleteOK** > . 
   
## <a name="add-cname-records"></a>Dodawanie rekordów CNAME
<a name="BKMK_add_CNAME"> </a>

Dodaj rekordy CNAME wymagane dla firmy Microsoft. Jeśli w firmie Microsoft są wymienione dodatkowe rekordy CNAME, dodaj je, zgodnie z instrukcjami ogólnymi przedstawionymi tutaj.
  
> [!IMPORTANT]
> Jeśli masz funkcję Zarządzanie urządzeniami przenośnymi dla firmy Microsoft, musisz utworzyć dwa dodatkowe rekordy CNAME. Postępuj zgodnie z procedurą użytą dla czterech pozostałych rekordów CNAME, ale podaj wartości z poniższej tabeli. (Jeśli nie masz aplikacji MDM, możesz pominąć ten krok). 

- Na stronie Menedżer DNS domeny przejdź do strony **ActionCNAME** >  **(CNAME) (ActionCNAME).**
- Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości:  
    - Nazwa hosta: autodiscover
    - Typ: 
    - CNAMEAddress: autodiscover.outlook.com
- Wybierz **pozycję OK**.

Dodaj rekord CNAME protokołu SIP. 
- Na stronie Menedżer DNS domeny przejdź do **action** \> **CNAME (CNAME) (Akcja CNAME**). 
- Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości:  
    - Nazwa hosta: sip
    - Typ: CNAME
    - Adres: sipdir.online.lync.com
- Wybierz przycisk **OK**.

Dodaj rekord CNAME usługi wykrywania automatycznego usługi Skype dla firm Online.  
- Na stronie Menedżer DNS domeny przejdź do **action** \> **CNAME (CNAME) (Akcja CNAME**). Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości:  
    - Nazwa hosta: lyncdiscover
    - Typ: CNAME
    - Adres: webdir.online.lync.com
- Wybierz przycisk **OK**.
   
### <a name="add-two-cname-records-for-mobile-device-management-mdm-for-microsoft"></a>Dodawanie dwóch rekordów CNAME dla usługi Zarządzanie urządzeniami przenośnymi dla firmy Microsoft

> [!IMPORTANT]
> Jeśli masz funkcję Zarządzanie urządzeniami przenośnymi dla firmy Microsoft, musisz utworzyć dwa dodatkowe rekordy CNAME. Postępuj zgodnie z procedurą użytą dla czterech pozostałych rekordów CNAME, ale podaj wartości z poniższej tabeli. >(Jeśli nie masz funkcji MDM, możesz pominąć ten krok). 
  

Dodaj rekord CNAME MDM Enterpriseregistration.  
- Na stronie Menedżer DNS domeny przejdź do **action** \> **CNAME (CNAME) (Akcja CNAME**). 
- Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości:  
- Nazwa hosta: enterpriseregistration
- Typ: CNAME
- Adres: enterpriseregistration.windows.net
- Wybierz przycisk **OK**. 

Dodaj rekord CNAME MDM Enterpriseenrollment. 
-  Na stronie Menedżer DNS domeny przejdź do **action** \> **CNAME (CNAME) (Akcja CNAME**). 
-  Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości:  
    - Nazwa hosta: enterpriseenrollment
    - Typ: CNAME
    - Adres: enterpriseenrollment-s.manage.microsoft.com
- Wybierz przycisk **OK**.
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy  *rekord SPF,*  który zawiera oba zestawy wartości. 
  
Dodaj rekord TXT SPF dla swojej domeny w celu zapobiegania spamowi w wiadomościach e-mail.
  
- Wartość TXT dla tego rekordu może już zawierać inne ciągi (na przykład ciągi marketingowych wiadomości e-mail), co nie stanowi problemu. Pozostaw te ciąg bez mian i dodaj następujący umieszczając podwójne cudzysłowy wokół każdego ciągu, aby je oddzielić. 
- Na stronie Menedżer DNS domeny przejdź do **strony Tekst** \> akcji **(TXT).** 
-  Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości. 
 > [!IMPORTANT]
> W niektórych wersjach menedżera DNS Windows domeny mógł zostać tak skonfigurować, że po utworzeniu rekordu txt nazwa główna domyślnie jest ustawiana jako domena nadrzędna. W takiej sytuacji podczas dodawania rekordu TXT ustaw nazwę hosta jako pustą (bez wartości) zamiast ustawiania wartości @ lub nazwy domeny. 

-  Typ hosta: @
-  Record Type (Typ rekordu): TXT
-  Adres: v=spf1 include:spf.protection.outlook.com -all 
         
-  Wybierz przycisk **OK**.
   
## <a name="add-srv-records"></a>Dodawanie rekordów SRV
<a name="BKMK_add_SRV"> </a>

Dodaj dwa rekordy SRV, które są wymagane dla firmy Microsoft.

Dodaj rekord SRV SIP na potrzeby funkcji konferencji w sieci Web usługi Skype dla firm Online.  <br/> 
-  Na stronie Menedżer DNS domeny przejdź do strony **Action** **Other New Records** (\>Działanie innych nowych rekordów). 
-   W **oknie Typ rekordu zasobu** wybierz pozycję Lokalizacja **usługi (SRV),** a następnie wybierz pozycję **Utwórz rekord**. 
-   Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości:  
    -  Usługa: _sip
    -  Protokół: _tls
    -  Priorytet: 100
    -  Waga: 1
    -  Port: 443
    -  Target (Hostname): sipdir.online.lync.com
-  Wybierz przycisk **OK**. 


Dodaj rekord SRV SIP na potrzeby federacji usługi Skype dla firm Online.  
-  Na stronie Menedżer DNS domeny przejdź do strony **Action** **Other New Records** (\>Działanie innych nowych rekordów).  
-  W **oknie Typ rekordu zasobu** wybierz pozycję Lokalizacja **usługi (SRV),** a następnie wybierz pozycję **Utwórz rekord**. 
-   Upewnij się, **że** w polach w oknie dialogowym Nowy rekord zasobu są ustawione dokładnie następujące wartości:  
    -  Usługa: _sipfederationtls
    -  Protokół: _tcp
    -  Priorytet: 100
    -  Waga: 1
    -  Port: 5061
    -  Target (Hostname): sipfed.online.lync.com
-  Wybierz przycisk **OK**. 
   
## <a name="add-a-record-to-verify-that-you-own-the-domain-if-you-havent-already"></a>Dodawanie rekordu w celu zweryfikowania własności domeny, jeśli nie zostało to jeszcze zrobione
<a name="BKMK_verify"> </a>

Zanim dodasz rekordy DNS w celu skonfigurowania konta usługi firmy Microsoft firma Microsoft musi potwierdzić, że dodasz własną domenę. W tym celu musisz dodać rekord, wykonując poniższe kroki.
  
> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. 
  

1. Zbieranie informacji od firmy Microsoft.  <br/> 
2. W Centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domeny</a>. 
3. Na stronie **Domains** (Domeny) w kolumnie **Actions** (Akcje) domeny, która jest weryfikowana, wybierz pozycję **Start setup (Rozpocznij konfigurowanie).** 
4. Na stronie **Dodawanie domeny do firmy Microsoft** wybierz pozycję **Rozpocznij krok 1**. 
5. Na stronie **Potwierdzanie, że** jesteś właścicielem domeny, z  listy rozwijanej Zobacz instrukcje dotyczące wykonywania tego kroku wybierz pozycję **Ogólne instrukcje**. 
6. Skopiuj z tabeli wartość Lokalizacja docelowa lub wskazywany adres. Będzie ona potrzebna w kolejnym kroku. Zalecamy skopiować i wkleić tę wartość, aby wszystkie odstępy pozostały poprawne.

Dodaj rekord TXT. 
-  Na stronie Menedżer DNS domeny przejdź do **strony Tekst** \> akcji **(TXT).** 
-   W **oknie dialogowym Nowy rekord** zasobu wybierz pozycję **Edytuj**.  
-  Upewnij **się,** że w obszarze Niestandardowe nazwy  hostów okna dialogowego Nowy rekord zasobu są ustawione dokładnie następujące wartości. 

> [!IMPORTANT] 
> W niektórych wersjach menedżera DNS Windows domeny mógł zostać tak skonfigurować, że po utworzeniu rekordu txt nazwa główna domyślnie jest ustawiana jako domena nadrzędna. W takiej sytuacji podczas dodawania rekordu TXT ustaw nazwę hosta jako pustą (bez wartości) zamiast ustawiania wartości @ lub nazwy domeny. 

- Nazwa hosta: @
- Typ: TXT
- Adres: wklej w tym miejscu wartość pola Miejsce docelowe lub wskazuje adres skopiowaną z firmy Microsoft.  
- Wybierz **pozycję** **OKDone** > .

Weryfikowanie domeny w firmie Microsoft.  
> [!IMPORTANT]
> Przed rozpoczęciem tej pracy poczekaj około 15 minut na zaktualizowanie właśnie utworzonego rekordu w Internecie.       

- Wróć do firmy Microsoft i wykonaj poniższe czynności, aby zażądać weryfikacji. Test wyszukuje rekord TXT dodany w poprzednim kroku. Po znalezieniu właściwego rekordu TXT domena zostaje zweryfikowana.  
1. W centrum administracyjnym przejdź do strony **Konfigurowanie** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domen</a> .
2. Na stronie **Domeny** w kolumnie Akcja domeny, która jest weryfikowana, wybierz pozycję **Rozpocznij konfigurowanie**. 
3. Na stronie **Potwierdzanie, że jesteś** właścicielem domeny wybierz pozycję **gotowe,** zweryfikuj teraz, a następnie w oknie dialogowym potwierdzenia wybierz pozycję **Zakończ**. 
   
> [!NOTE]
>  Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory"></a>Nierutowalny adres e-mail używany jako główna nazwa użytkownika w lokalnej usłudze Active Directory
<a name="BKMK_ADNote"> </a>

Jeśli planujesz zsynchronizowanie lokalnej usługi Active Directory z firmą Microsoft, upewnij się, że sufiks głównej nazwy użytkownika (UPN) usługi Active Directory jest prawidłowym sufiksem domeny, a nie nieobsługiwanym sufiksem domeny, takim jak @contoso.local. Jeśli chcesz zmienić sufiks upn, zobacz Jak przygotować domenę nie [routowatą do synchronizacji katalogów](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md).
  
> [!NOTE]
>  Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="related-content"></a>Zawartość pokrewna

[Przenoszenie domeny z usługi Micrsoft 365 do innego hosta](../get-help-with-domains/transfer-a-domain-from-microsoft-to-another-host.md) (artykuł)\
[Pilot Microsoft 365 z domeny niestandardowej](../misc/pilot-microsoft-365-from-my-custom-domain.md) (artykuł)\
[Domeny — często](../setup/domains-faq.yml) zadawane pytania (artykuł)