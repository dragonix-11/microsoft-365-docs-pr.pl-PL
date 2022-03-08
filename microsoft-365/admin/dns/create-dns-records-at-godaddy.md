---
title: Łączenie rekordów DNS w witrynie GoDaddy z usługą Microsoft 365
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
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i innych usług w witrynie GoDaddy dla firmy Microsoft.
ms.openlocfilehash: 728fd6cc34517213b338e3da07e6a275a1a727d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313555"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>Łączenie rekordów DNS w witrynie GoDaddy z usługą Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli witryna GoDaddy jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i tym podobne.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Dostępne są dwie opcje konfigurowania rekordów DNS dla domeny:

- [**Używanie funkcji Domain Connect**](#use-domain-connect-to-verify-and-set-up-your-domain) Jeśli twoja domena nie jest jeszcze ustawiona na inną usługę poczty e-mail usługodawca, skorzystaj z procedury domain Connect, aby automatycznie zweryfikować i skonfigurować nową domenę do używania z usługą Microsoft 365.

   LUB

- [**Ręczne kroki**](#create-dns-records-with-manual-setup) Zweryfikuj domenę, korzystając z ręcznej procedury poniżej, i wybierz, kiedy i które rekordy dodać do rejestratora domen. Umożliwia to skonfigurowanie nowych rekordów MX (poczty), na przykład w dogodnym dla Ciebie momencie.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Weryfikowanie i konfigurowanie domeny za pomocą funkcji Domain Connect

Wykonaj poniższe czynności, aby automatycznie zweryfikować i skonfigurować domenę GoDaddy na microsoft 365:

1. W centrum administracyjnym platformy Microsoft 365 wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**SettingsDomains**</a> > , a następnie wybierz domenę, którą chcesz skonfigurować.

1. Wybierz przycisk z trzema kropkami (więcej akcji), > pozycję **Rozpocznij konfigurowanie**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Na stronie Jak chcesz połączyć domenę? wybierz pozycję **Kontynuuj**.

1. Na stronie Dodawanie rekordów DNS wybierz pozycję **Dodaj rekordy DNS**.

1. Na stronie logowania do witryny GoDaddy zaloguj się do swojego konta i wybierz pozycję **Autoryzuj**.

    Ukończy to konfigurację domeny dla platformy Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Tworzenie rekordów DNS przy użyciu konfiguracji ręcznej

Po dodaniu tych rekordów w witrynie GoDaddy Twoja domena będzie skonfigurować do współpracy z usługami firmy Microsoft.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziecie używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj swoich poświadczeń logowania, wybierz swoją nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

1. W **obszarze Domeny** wybierz trzy kropki obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Rekordy** wybierz **pozycję DODAJ** (może być konieczne przewinięcie w dół).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

1. Z **listy** rozwijanej wybierz wartość TXT.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Z listy rozwijanej Type (Typ) wybierz wartość TXT.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z tabeli.

   |**Type (Typ)** |**Host**|**Wartość TXT**|**TTL (Czas wygaśnięcia)** |
   |:-----|:-----|:-----|:-----|
   |TXT |@|MS=ms *XXXXXXXX*<br>**Uwaga**: To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|1 godzina  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Wypełnij wartości z tabeli rekordu TXT.":::

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="Wybierz pozycję Zapisz.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz tego rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.
  
Aby zweryfikować rekord na platformy Microsoft 365:
  
1. W centrum administracyjnym przejdź do pozycji **Ustawienia Domeny**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. Na stronie Domeny wybierz weryfikowaną domenę, a następnie wybierz pozycję **Rozpocznij konfigurowanie**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurowanie.":::

1. Wybierz **pozycję Kontynuuj**.
  
1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodawanie rekordu MX, aby poczta e-mail dla Twojej domeny trafiała do firmy Microsoft

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj swoich poświadczeń logowania, wybierz swoją nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

2. W **obszarze Domeny** wybierz trzy kropki obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

3. W **obszarze Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

4. Z **listy** rozwijanej wybierz pozycję MX.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję MX.":::

5. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    Z listy **rozwijanej** wybierz wartości Type (Typ) i **TTL** (Czas wygaśnięcia).

    |**Type (Typ)**|**Host**|**Wskazuje**|**Priority (Priorytet)**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX  <br/> |@  <br/> | *\<domain-key\>*  mail.protection.outlook.com  <br/> **Uwaga:** Pobierz ze  *\<domain-key\>*  swojego konta Microsoft.           [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) <br/> |1 godzina  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wypełnij wartości z tabeli rekordu MX.":::

6. Wybierz **Zapisz**.

### <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj swoich poświadczeń logowania, wybierz swoją nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

2. W **obszarze Domeny** wybierz trzy kropki obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

3. W **obszarze Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

4. Z **listy rozwijanej wybierz pozycję CNAME** .

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję CNAME.":::

5. Utwórz rekord CNAME.

    W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli.

    Z listy **rozwijanej wybierz wartość TTL** (Czas wygaśnięcia).

    |**Type (Typ)**|**Host**|**Wskazuje**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover <br/> |autodiscover.outlook.com  <br/> |1 godzina  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Wypełnij wartości z tabeli rekordu CNAME.":::

6. Wybierz **Zapisz**.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy  *rekord SPF,*  który zawiera oba zestawy wartości.

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj swoich poświadczeń logowania, wybierz swoją nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

2. W **obszarze Domeny** wybierz trzy kropki obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

3. W **obszarze Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

4. Z **listy** rozwijanej wybierz wartość TXT.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Z listy rozwijanej Type (Typ) wybierz wartość TXT.":::

5. W polach nowego rekordu wpisz lub skopiuj i wklej następujące wartości.

    Z list **rozwijanych wybierz wartość TTL** (Czas wygaśnięcia).

    |**Type (Typ)**|**Host**|**Wartość TXT**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |TXT <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne. |1 godzina  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Wypełnij wartości z tabeli rekordu TXT.":::

6. Wybierz **Zapisz**.

## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype 4 rekordy: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME do zalogowania się i połączenia użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj swoich poświadczeń logowania, wybierz swoją nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

1. W **obszarze Domeny** wybierz trzy kropki obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

1. Z **listy rozwijanej wybierz pozycję SRV** .

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję SRV.":::

1. Utwórz pierwszy rekord SRV.

    W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli.

    Z list **rozwijanych** wybierz wartości Type (Typ) i **TTL** (Czas wygaśnięcia).

    |**Type (Typ)**|**Service (Usługa)**|**Protocol (Protokół)**| **Name (Nazwa)** | **Target (Element docelowy)**|**Priority (Priorytet)**|**Weight (Waga)**|**Port**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV   <br/> |_sip  <br/> |_tls  <br/> |@  <br/> |sipdir.online.lync.com  <br/> |100 <br/> | 1  <br/> |443  <br/> |1 godzina  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |_tcp  <br/> |@  <br/> | sipfed.online.lync.com  <br/> | 100  <br/> |1  <br/> |5061  <br/> |1 godzina  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="Wypełnij wartości z tabeli dla rekordu SRV.":::

1. Wybierz **Zapisz**.

1. Dodaj drugi rekord SRV, wybierając wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME
  
1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj swoich poświadczeń logowania, wybierz swoją nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

2. W **obszarze Domeny** wybierz trzy kropki obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

1. Z **listy rozwijanej wybierz pozycję CNAME** .

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję CNAME.":::

1. W pustych polach nowych rekordów wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli.

    |**Type (Typ)**|**Host**|**Wskazuje**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Wypełnij wartości z tabeli rekordu CNAME.":::
  
1. Wybierz **Zapisz**.
  
1. Dodaj drugi rekord CNAME, wybierając wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: Intune i Zarządzanie urządzeniami przenośnymi dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Zarządzanie urządzeniami przenośnymi wymaga 2 rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj swoich poświadczeń logowania, wybierz swoją nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

1. W **obszarze Domeny** wybierz trzy kropki obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Manage DNS (Zarządzaj systemem DNS).":::

1. W **obszarze Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

1. Z **listy rozwijanej wybierz pozycję CNAME** .

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję CNAME.":::

1. W pustych polach nowych rekordów wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli.

    |**Type (Typ)**|**Host**|**Wskazuje**|**TTL (Czas wygaśnięcia)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> |1 godzina  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Wypełnij wartości z tabeli rekordu CNAME.":::
  
1. Wybierz **Zapisz**.
  
1. Dodaj drugi rekord CNAME, wybierając wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
