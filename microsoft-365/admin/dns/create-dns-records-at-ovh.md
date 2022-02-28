---
title: Połączenie rekordy DNS w OVH, aby Microsoft 365
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
ms.assetid: 5176feef-36dc-4d84-842f-1f2b5a21ba96
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w OVH dla firmy Microsoft.
ms.openlocfilehash: 5bf6b052be9297f3d121897f8e8de5ec8fa2a9e4
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989684"
---
# <a name="connect-your-dns-records-at-ovh-to-microsoft-365"></a>Połączenie rekordy DNS w OVH, aby Microsoft 365

[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml), jeśli nie możesz znaleźć szukanych informacji.
  
Jeśli OVH jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, dla usługi Skype dla firm Online itp.

Po dodaniu tych rekordów w OVH Twoja domena będzie skonfigurować do współpracy z usługi firmy Microsoft.

> [!NOTE]
>  Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziecie używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.
  
> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w OVH, używając [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Na stronie startowej pulpitu nawigacyjnego w **obszarze Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.
  
1. Wybierz **strefę DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Wybierz **pozycję TXT**

    ![OVH wybierz wpis TXT.](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)
  
1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. Aby przypisać wartość TTL (Czas wygaśnięcia), z listy rozwijanej wybierz pozycję **Custom** (Niestandardowe), a następnie wpisz wartość w polu tekstowym. 

    |**Typ rekordu**|**Poddomena**|**TTL (Czas wygaśnięcia)**|**Wartość**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |(pozostaw puste)  <br/> |3600 (sekundy)  <br/> |MS=msxxxxxxxx  <br/> **Uwaga:** To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli.  [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)          |

1. Wybierz pozycję **Dalej**.

1. Wybierz **pozycję Potwierdź**.

    ![OVH potwierdź txt w celu weryfikacji.](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)
  
1. Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz tego rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w Microsoft 365:
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.

1. Na stronie Domeny wybierz weryfikowaną domenę, a następnie wybierz pozycję **Rozpocznij konfigurowanie**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Wybierz **pozycję Kontynuuj**.
  
1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
>  Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodawanie rekordu MX, aby poczta e-mail dla Twojej domeny trafiała do firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w OVH, używając [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Na stronie startowej pulpitu nawigacyjnego w **obszarze Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.
  
1. Wybierz **strefę DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Wybierz **pozycję MX**.

    ![Typ rekordu MX OVH.](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)
  
1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. Aby przypisać wartość TTL (Czas wygaśnięcia), z listy rozwijanej wybierz pozycję **Custom** (Niestandardowe), a następnie wpisz wartość w polu tekstowym. 

    > [!NOTE]
    > Domyślnie w OVH jest używana notacja względna wartości docelowej, która dodaje nazwę domeny na końcu rekordu docelowego. Aby zamiast tego użyć notacji bezwzględnej, dodaj kropkę do rekordu docelowego, jak pokazano w poniższej tabeli. 
  
    |**Poddomena**|**TTL (Czas wygaśnięcia)**|**Priority (Priorytet)**|**Target (Element docelowy)**|
    |:-----|:-----|:-----|:-----|
    |(pozostaw puste)  <br/> |3600 (sekundy)  <br/> |0  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) <br/> |\<domain-key\>mail.protection.outlook.com.  <br/> **Uwaga:** Pobierz ze  *\<domain-key\>*  swojego konta Microsoft.  [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)  |

    ![Rekord MX OVH dla poczty.](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)
  
1. Wybierz pozycję **Dalej**.

    ![Rekord MX OVH wybierz pozycję Next (Dalej).](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)
  
1. Wybierz **pozycję Potwierdź**.

    ![Rekord MX OVH wybierz pozycję Potwierdź.](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)

1. Usuń wszelkie inne rekordy MX z listy na stronie **strefy DNS** . Zaznacz każdy rekord i w kolumnie **Akcje** wybierz ikonę kosza na śmieci **Usuń** .

    ![OVH: usuwanie rekordu MX.](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)
  
1. Wybierz **pozycję Potwierdź**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w OVH, używając [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Na stronie startowej pulpitu nawigacyjnego w **obszarze Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.
  
1. Wybierz **strefę DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Wybierz **pozycję CNAME**.

    ![OVH Add CNAME record type (Dodaj typ rekordu CNAME).](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli. Aby przypisać wartość TTL (Czas wygaśnięcia), z listy rozwijanej wybierz pozycję **Custom** (Niestandardowe), a następnie wpisz wartość w polu tekstowym. 

    |**Poddomena**|**TTL (Czas wygaśnięcia)**|**Target (Element docelowy)**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |3600 (sekundy)  <br/> |autodiscover.outlook.com.  <br/> |

    ![Rekord OVH CNAME.](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)
  
1. Wybierz pozycję **Dalej**.

    ![OVH Dodaj wartości CNAME i wybierz pozycję Dalej.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Wybierz **pozycję Potwierdź**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy  *rekord SPF,*  który zawiera oba zestawy wartości. 
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w OVH, używając [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Na stronie startowej pulpitu nawigacyjnego w **obszarze Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.
  
1. Wybierz **strefę DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Wybierz **pozycję TXT**.

1. W polach nowego rekordu wpisz lub skopiuj i wklej następujące wartości. Aby przypisać wartość TTL (Czas wygaśnięcia), z listy rozwijanej wybierz pozycję **Custom** (Niestandardowe), a następnie wpisz wartość w polu tekstowym. 

    |**Poddomena**|**TTL (Czas wygaśnięcia)**|**Wartość**|
    |:-----|:-----|:-----|
    |(pozostaw puste)  <br/> |3600 (sekundy)  <br/> |v=spf1 include:spf.protection.outlook.com -all <br/**Note:** zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.           |

    ![OVH Add TXT record for SPF (Dodaj rekord TXT dla SPF).](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)
  
1. Wybierz pozycję **Dalej**.

    ![OVH Add TXT record for SPF (Dodaj rekord TXT dla SPF) i wybierz pozycję Next (Dalej).](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)
  
1. Wybierz **pozycję Potwierdź**.

    ![OVH Add TXT record for SPF and Confirm (Dodaj rekord TXT dla SPF) i Confirm (Potwierdź).](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)
  
## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype 4 rekordy: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME do zalogowania się i połączenia użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć pracę, przejdź do swojej strony domen w OVH, używając [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Na stronie startowej pulpitu nawigacyjnego w **obszarze Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.
  
1. Wybierz **strefę DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz **pozycję SRV**.

1. W polach nowego rekordu wpisz lub skopiuj i wklej następujące wartości. Aby przypisać wartość TTL (Czas wygaśnięcia), z listy rozwijanej wybierz pozycję **Custom** (Niestandardowe), a następnie wpisz wartość w polu tekstowym. 

    |**Poddomena**|**TTL (Seconds) [Czas wygaśnięcia (w sekundach)]**| **Priority (Priorytet)** | **Weight (Waga)** | **Port**|**Target (Element docelowy)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|3600 (s.) |100 |  1  | 443 |sipdir.online.lync.com. **Ta wartość MUSI mieć na końcu okres (.)**><br> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne. | 
    |_sipfederationtls._tcp| 3600 (s.)|100 | 1 | 5061 | sipfed.online.lync.com. **Wartość ta MUSI mieć na końcu kropkę (.)**<br> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.    | 
  
1. Aby dodać drugi rekord SRV, wybierz pozycję **Add another record** (Dodaj kolejny rekord), utwórz rekord, używając wartości z następnego wiersza w tabeli, a następnie wybierz pozycję **Create records (Utwórz rekordy**).

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME 

1. Aby rozpocząć pracę, przejdź do swojej strony domen w OVH, używając [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Na stronie startowej pulpitu nawigacyjnego w **obszarze Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.
  
1. Wybierz **strefę DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz **pozycję CNAME**.

    ![OVH Add CNAME record type (Dodaj typ rekordu CNAME).](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli. Aby przypisać wartość TTL (Czas wygaśnięcia), z listy rozwijanej wybierz pozycję **Custom** (Niestandardowe), a następnie wpisz wartość w polu tekstowym. 

    |**Poddomena**| **TTL (Czas wygaśnięcia)** | **Target (Element docelowy)** | 
    |:-----|:-----|:-----|
    |sip  <br/> | 3600 (s.)  <br/> |sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |
    |lyncdiscover  <br/> |3600 (s.) |webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/>  |
  
1. Wybierz pozycję **Dalej**.

    ![OVH Dodaj wartości CNAME i wybierz pozycję Dalej.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Wybierz **pozycję Potwierdź**.

1. Dodaj drugi rekord CNAME.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: Intune i Zarządzanie urządzeniami przenośnymi dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Zarządzanie urządzeniami przenośnymi wymaga dwóch rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Aby rozpocząć pracę, przejdź do swojej strony domen w OVH, używając [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Na stronie startowej pulpitu nawigacyjnego w **obszarze Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.
  
1. Wybierz **strefę DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Wybierz **pozycję CNAME**.

    ![OVH Add CNAME record type (Dodaj typ rekordu CNAME).](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli. Aby przypisać wartość TTL (Czas wygaśnięcia), z listy rozwijanej wybierz pozycję **Custom** (Niestandardowe), a następnie wpisz wartość w polu tekstowym. 
  
    |**Poddomena**| **TTL (Czas wygaśnięcia)** | **Target (Element docelowy)** | 
    |:-----|:-----|:-----|
    |enterpriseregistration  <br/>| 3600 (s.)  <br/> |enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |
    |enterpriseenrollment  <br/>  |3600 (s.) |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/>|

1. Wybierz pozycję **Dalej**.

    ![OVH Dodaj wartości CNAME i wybierz pozycję Dalej.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Wybierz **pozycję Potwierdź**.

1. Dodaj drugi rekord CNAME.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).