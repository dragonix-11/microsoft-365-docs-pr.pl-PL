---
title: Połączenie rekordy DNS w witrynie Wix to Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w witrynie Wix dla Microsoft.
ms.openlocfilehash: 9a9e230a46967ab6c012199e7f4fc6426fdc67bf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314857"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Połączenie rekordy DNS w witrynie Wix to Microsoft 365

**[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
Jeśli usługa Wix jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online itp.

Po dodaniu tych rekordów Wix Twoja domena będzie skonfigurować do współpracy z usługi firmy Microsoft.
  
> [!NOTE]
>  Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziesz używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.
  
> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć. 

> [!NOTE]
> Usługa WIX nie obsługuje wpisów DNS dla poddomen.
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w usługi Wix, używając [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

2. Wybierz **pozycję Domeny** > **, a** następnie z listy rozwijanej wybierz pozycję **Manage DNS Records** (Zarządzaj rekordami DNS).

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS Records (Zarządzaj rekordami DNS).":::

3. Wybierz **pozycję + Add Record** (Dodaj rekord **) w wierszu TXT (Text) (Tekst)** edytora DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Wybierz pozycję Add record (Dodaj rekord).":::

4. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

   ||||
   |:-----|:-----|:-----|
   | **Nazwa hosta **<br/> | **Wartość TXT** <br/> | **Czas wygaśnięcia** <br/> |
   |Automatycznie wypełniane (pozostaw puste)  <br/> |MS=ms *XXXXXXXX*  <br/> **Uwaga:** To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli.  [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|1 godzina <br/> |          |

5. Wybierz **pozycjęZazadaj**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Wybierz pozycję Zapisz.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.


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

1. Aby rozpocząć pracę, przejdź do swojej strony domen w usługi Wix, używając [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Domeny** > **, a** następnie z listy rozwijanej wybierz pozycję **Manage DNS Records** (Zarządzaj rekordami DNS).

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS Records (Zarządzaj rekordami DNS).":::

1. W **obszarze MX (Mail exchange)** wybierz **pozycję Edit MX Records (Edytuj rekordy MX**). 

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="Wybierz pozycję Edit MX Records (Edytuj rekordy MX).":::

1. Z **listy** rozwijanej wybierz pozycję Inne, a następnie wybierz **pozycję + Add record (Dodaj rekord**).

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="Z listy rozwijanej wybierz pozycję Inne.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli:

   | **Host Name (Nazwa hosta)** | **Wskazuje** | **Priority (Priorytet)** | **TTL (Czas wygaśnięcia)** |
   |:-----|:-----|:-----|:-----|
   |Automatycznie wypełniane <br/> | *\<domain-key\>*  mail.protection.outlook.com  <br/> **Uwaga:** Pobierz ze  *\<domain-key\>*  swojego konta Microsoft.   [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md) |0  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) | 1 godzina|

1. Jeśli na liście znajdują się inne rekordy MX, usuń je wszystkie.

   :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="Wybierz pozycję Usuń.":::

1. Wybierz **Zapisz**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w usługi Wix, używając [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

2. Wybierz **pozycję Domeny** > **, a** następnie z listy rozwijanej wybierz pozycję **Manage DNS Records** (Zarządzaj rekordami DNS). 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS Records (Zarządzaj rekordami DNS).":::

3. Wybierz **pozycję + Add Record (** Dodaj rekord) w wierszu **CNAME (Aliases)** edytora DNS rekordu CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Wybierz pozycję + Add Record (Dodaj rekord).":::

4. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli:

   | **Host Name (Nazwa hosta)** | **Value (Wartość)** | **TTL (Czas wygaśnięcia)** |
   |:-----|:-----|:-----|
   |autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 godzina  <br/> |

5. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy  *rekord SPF,*  który zawiera oba zestawy wartości.  
  
1. Aby rozpocząć pracę, przejdź do swojej strony domen w usługi Wix, używając [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

2. Wybierz **pozycję Domeny** > **, a** następnie z listy rozwijanej wybierz pozycję **Manage DNS Records** (Zarządzaj rekordami DNS). 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS Records (Zarządzaj rekordami DNS).":::

3. Wybierz **pozycję + Add Record** (Dodaj rekord **) w wierszu TXT (Text) (Tekst)** edytora DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Wybierz pozycję + Add record (Dodaj rekord).":::

   **Uwaga**: Usługa Wix udostępnia wiersz SPF w edytorze DNS. Zignoruj ten wiersz i wprowadź poniższe wartości **SPF przy użyciu wiersza TXT (Text)** (Tekst). 

4. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli:

   | **Host Name (Nazwa hosta)** | **Value (Wartość)** | **TTL (Czas wygaśnięcia)** |
   |:-----|:-----|:-----|
   |[pozostaw to pole puste]  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.<br/> | 1 godzina |

5. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Wybierz pozycję Zapisz.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype do zalogowania się i połączenia użytkowników z usługą potrzebne są cztery rekordy: dwa rekordy SRV do komunikacji między użytkownikami i dwa rekordy CNAME.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć pracę, przejdź do swojej strony domen w usługi Wix, używając [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Domeny** > **, a** następnie z listy rozwijanej wybierz pozycję **Manage DNS Records** (Zarządzaj rekordami DNS).

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS Records (Zarządzaj rekordami DNS).":::

1. Wybierz **pozycję + Add Record (Dodaj** rekord) **w wierszu SRV** edytora DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="Wybierz pozycję + Add Record (Dodaj rekord).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza w tabeli:

   | **Service (Usługa)** | **Protocol (Protokół)** | **Nazwa hosta** | **Weight (Waga)** | **Port** | **Target (Element docelowy)** | **Priority (Priorytet)** | **TTL (Czas wygaśnięcia)** |
   |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
   |sip  |tls  |Automatycznie wypełniane |1  |443   |sipdir.online.lync.com |100 |1 godzina |
   |sipfed|tcp |Automatycznie wypełniane|1 |5061 |sipfed.online.lync.com|100 | 1 godzina |

1. Wybierz **Zapisz**.
  
   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj drugi rekord SRV, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Wybierz **pozycję + Dodaj kolejną** pozycję w wierszu **CNAME (Aliasy)** edytora DNS i wprowadź wartości z pierwszego wiersza poniższej tabeli.

   |**Type (Typ)**|**Host**|**Wartość**|**TTL (Czas wygaśnięcia)**|
   |:-----|:-----|:-----|:-----|
   |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
   |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
  
1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::
  
1. Dodaj drugi rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: Intune i Zarządzanie urządzeniami przenośnymi dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Zarządzanie urządzeniami przenośnymi wymaga dwóch rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Aby rozpocząć pracę, przejdź do swojej strony domen w usługi Wix, używając [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz **pozycję Domeny** > **, a** następnie z listy rozwijanej wybierz pozycję **Manage DNS Records** (Zarządzaj rekordami DNS).

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS Records (Zarządzaj rekordami DNS).":::

1. Wybierz **pozycję + Add Record (** Dodaj rekord) w wierszu **CNAME (Aliases)** edytora DNS rekordu CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Wybierz pozycję + Add Record (Dodaj rekord).":::

1. Wprowadź wartości z pierwszego wiersza poniższej tabeli.

    |**Type (Typ)**|**Host**|**Wartość**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration <br/> |enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
  
1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::
  
1. Dodaj drugi rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).